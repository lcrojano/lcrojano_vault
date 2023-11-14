[[ReadItLater]] [[Article]]

# [Applying the Onion Architecture to Angular Projects](https://medium.com/@navez.jerome/applying-the-onion-architecture-to-angular-projects-b37736d2c996)

[

![Jérôme Navez](Jérôme%20Navez.jpeg)



](https://medium.com/@navez.jerome?source=post_page-----b37736d2c996--------------------------------)

Investing time to design a well-structured software programs is always time well spent. **Making the extra effort to have a clean and well-ordered code is worth the pain in the long run.**

In this article, we will push our [SCA Architecture](https://medium.com/@navez.jerome/a-simple-and-clean-architecture-for-your-angular-projects-f1a68040c09a) a bit further and implement the **Onion architecture** (a.k.a. Hexagonal architecture).

Remember, the goal of the SCA Architecture was to enforce the separation of concern and to keep the Domain logic isolated. The most critical parts of an Angular project are:

-   Having nice and **clean Components**;
-   The **state management**;
-   And **avoiding having logic code spread** across Components and services.

This is where the **Onion architecture** can help us. Let’s dig into its core principle.

## Onion architecture, the theory

The Onion Architecture was theorized by Jeffrey Palermo. [Following his article written in 2008](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/), there was a trend to **isolate the core logic** of specific applications from the presentation code, persistence code, and other infra-related code by reversing some dependencies. All thanks to a pattern named **Dependency Inversion**.

This trend was born in opposition to the layered architecture where the dependencies lead to the persistence layer. The goal was for the core logic to be agnostic from the persistence layer.

But wait… Doesn’t this kind of architecture belong to the backend!?

**Not at all!** Dependency Inversion opens the gate to lots of architectures, and we can apply the pattern in **NodeJS** projects. Hexagonal, Clean Architecture,… you name it! The kind of architecture usually reserved for backends.

Angular and other modern frameworks embrace the asynchronous code. **Making those architectures even more interesting to implement!**

## The Angular Onion Architecture

Now that you have the general theory of this architecture, we need to define what is our Domain and what needs to be isolated from it. We can define **four big parts** in Frontend projects:

-   The **Views** displayed to the user, i.e, the Components;
-   The **Clients** used to communicate with APIs;
-   The **State**, our single source of truth;
-   Our **Domain** that contains our logic.

Client and State modules are part of the **Infrastructure** layer.

From now on, those four parts will be called **modules** in the rest of the article. Module in the sense that they are **Node modules/packages** (not Angular `@NgModule`)

## Domain module

The center of the architecture is the Domain module: the **orchestration logic** and our **business logic**. This module also contains the **model** of our application. Most of the time, this model is defined by interfaces.

The Domain module

The **orchestration logic** is the instructions that **synchronize the calls to the Clients and the Application State**.

Let us suppose a list of items available for the user. When the user deletes an item, the orchestration logic executes a delete operation through a **Client Gateway** and then remove the item from the State through a **Store Gateway**. This orchestration is hidden behind a **Facade** method.

In the Domain, those **Gateways** are abstract classes containing only unimplemented methods. It’s the way for the Domain to tell that it needs other modules to implement those methods. This way, the **Domain stays away from the implementation complexity** of those dependencies while defining the way to use those dependencies.

> Conceptually, this could have been achieved with interfaces as well, it seems even more right. The reason we use abstract classes is that the **interface concept does not exist in JavaScript**. Thus, we would not be able to inject interfaces in Angular services.

The **business logic** is any logic unrelated to View, Client, and Store modules. Sensitive logic is usually handled in the backend. In case an application needs to perform business logic in the frontend, this logic takes place in the Domain.

*Example of Facade:*

//hello-world.facade.ts  
@Injectable()  
export class HelloWorldFacade {  
    readonly currentMessage$ = this.storeGateway.message$;

    constructor(private clientGateway: HelloWorldClientGateway,  
                private storeGateway: HelloWorldStoreGateway) {  
        this.clientGateway.getMessage()  
            .subscribe(message => this.storeGateway.updateMessage(message));  
    }

    updateMessage(message: string): void {  
        this.clientGateway.saveMessage({ info: message.trim() })  
            .subscribe(saved => this.storeGateway.updateMessage(saved))  
    }  
}

In the example, the Facade provides:

-   `currentMessage[[ReadItLater]] [[Article]]

# [Applying the Onion Architecture to Angular Projects](https://medium.com/@navez.jerome/applying-the-onion-architecture-to-angular-projects-b37736d2c996)

: an updated value of the current message through an Observable;
-   `updateMessage()`: a void method to update this value.

*The Gateways are the following:*

//hello-world.client.gateway.ts  
export abstract class HelloWorldClientGateway {  
    abstract getMessage(): Observable<Message>;  
    abstract saveMessage(message: Message): Observable<Message>;  
}

//hello-world.store.gateway.ts  
export abstract class HelloWorldStoreGateway {  
    abstract message$: Observable<Message>;  
    abstract updateMessage(message: Message): void;  
}

## View module

The View module takes care of defining the **Components**. The goal is to keep the logic of your business out of those Components. Components need to be **as dummy as possible**: they execute actions using the Domain Facades and get business data from it. The only logic that could be present in a Component is display logic or Form logic.

The View Module

In addition, besides providing the Components, you can write your **Directives** and your **Pipes** in the View module. These are strongly related to the display of the application. But keep in mind that Directives and Pipes have no choice but to use a service from the Domain if they are based on business logic.

*Example of Component:*

@Component({  
    selector: 'app-root',  
    template: \`  
    Message:   
    <br/>  
    <label> New message:  
      <input \[(ngModel)\]="input" type="text"/>  
    </label>  
    <button (click)="updateMessage()">Submit message</button>  
  \`  
})  
export class AppComponent {

    input: string = '';

    message: Signal<Message | undefined> = toSignal(this.helloWorldFacade.currentMessage$);

    constructor(private helloWorldFacade: HelloWorldFacade) {}

    public updateMessage() {  
        this.helloWorldFacade.updateMessage(this.input);  
    }  
}

## Client module (Infrastructure)

The Client module belongs to the Infrastructure layer. This is **our gate to the backend**, the connection of our API. The Clients are the services that use HttpClients to contact APIs. They only return asynchronous values, thus finite Observables emitting once.

The Client Module

One of the biggest mistakes we see: calling the Clients directly from the Components. [No, no, no, please no!](https://www.youtube.com/watch?v=umDr0mPuyQc) Why would you do that? The day you need to extend your features, attach a store to those data, or reuse is somewhere else in your application, you are good to refactor your whole Components.

To avoid making this mistake, let **the Client adapt itself to the Domain Model**.

What does ***adapt itself*** mean?

The Domain provides an abstract class that is meant to be implemented by the Client module. But the Domain uses Domain Models while Clients use DTOs. To ensure that your Domain is not impacted by DTO changes, we need to **map the DTOs to Domain Models and vice versa** when implementing a Client Gateway.

The Client can implement methods the way we like. Using Web-sockets, HTTP calls, as we want. As long as the contract is respected.

*Example of Client:*

//hello-world.client.ts  
export class HelloWorldClient extends HelloWorldClientGateway {

    private httpClient = inject(HttpClient);

    getMessage(): Observable<Message> {  
        return this.httpClient.get<MessageDto>('/api/message').pipe(  
            map(dto => ({ info: dto.content }))  
        )  
    }

    public saveMessage(message: Message): Observable<Message> {  
        return this.httpClient.put<MessageDto>('/api/message', { content: message.info }).pipe(  
            map(dto => ({ info: dto.content }))  
        );  
    }  
}

Imagine that in early stage development, the backend is not yet ready. But still, you want to integrate your Clients and have a working frontend. You could implement those Clients by using the local storage of the browser. Later, you simply need to implement the HttpClient version to be “backend-ready”. That’s the way to **keep your Domain safe from any change on the Client side**.

## State module (Infrastructure)

The State module also belongs to the Infrastructure layer. It has to be built as **the single source of truth of your application**. The state of our application only relies on this module.

The State Module

The State module provide a way for the Domain to store data locally in-memory. Once again, **the Domain defines** the way he wants to store/retrieve data and **the State module provides** the way to do it.

Whether it uses NgRx, Redux, or any other fancy store library, it’s up to the State module to manage that.

> **Side note:** a state management can simply be built around a simple `BehaviorSubject`. No need to bring complex libraries. **RxJs** natively provides great mechanisms. For more information, I invite you to read [this section](https://medium.com/@navez.jerome/a-simple-and-clean-architecture-for-your-angular-projects-f1a68040c09a#6e32) of a previous article.

*Example of Store:*

//hello-world.store.ts  
export class HelloWorldStore extends HelloWorldStoreGateway {  
    private store = new Store<MessageState>(initialState)

    public message$: Observable<Message>  
        = this.store.select((state) => ({info: state.currentMessage}));

    public updateMessage(message: Message): void {  
        this.store.update((state) => ({ ...state, currentMessage: message.info }))  
    }  
}

More generally, **Infrastructure modules** are there to provide the Domain with everything it needs to run correctly so that the Domain can focus on Business logic. In regular Web applications, we mostly meet the State and the Clients. But it could also be local DB, Session/Local storage, file system, etc.

## App module

The application module is **the oil of all of this**. It takes care of every nasty thing needed to run an Angular project. Configuration files, external dependencies, and root `NgModule`. It also makes sure that the modules run all together.

The App Module

On top of that, the routing is tackled there, meaning that this is also the place for `Guards` and `Resolvers`.

Depending on the size of the application, **Angular feature modules** are defined in the App module.

## All together

Bring all together the Onion Architecture on Angular projects results in the following structure:

We notice that the **dependencies lead to the Domain**. This is the crucial point of this architecture. Instead of having the Domain depending on the Clients or a state management library, we have the Clients and the State that depend on the Domain. You cannot be more **Domain Driven Development** oriented than that.

> **Side note:** A strong effort needs to be put into the naming conventions. Using `*.service.ts` file names and `*Service` class names is not enough to clearly define the purpose of a service. `*.facade.ts`, `*.client.ts`, and `*.store.ts` are filenames that better help the understanding of the class purpose.