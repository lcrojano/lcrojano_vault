---
url: https://javascript.plainenglish.io/deep-dive-into-angulars-attribute-decorator-real-world-applications-and-tips-7cc4fabf284f
readlater:
  id: "3959755877"
  provider: pocket
  synchtime: 1699401381878
---
# Deep Dive into Angular’s @Attribute Decorator: Real-World Applications and Tips

[

![Astrit Shuli](https://miro.medium.com/v2/resize:fill:88:88/1*6LE4DCjTIgvrMAOPRdp_4Q.png)









](https://astritshuli.medium.com/?source=post_page-----7cc4fabf284f--------------------------------)[

![JavaScript in Plain English](https://miro.medium.com/v2/resize:fill:48:48/1*yUNfohs9jA6GCDmyCYJTvA@2x.png)











](https://javascript.plainenglish.io/?source=post_page-----7cc4fabf284f--------------------------------)

[Astrit Shuli](https://astritshuli.medium.com/?source=post_page-----7cc4fabf284f--------------------------------)

·

[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fuser%2Fcfc4465f97fe&operation=register&redirect=https%3A%2F%2Fjavascript.plainenglish.io%2Fdeep-dive-into-angulars-attribute-decorator-real-world-applications-and-tips-7cc4fabf284f&user=Astrit+Shuli&userId=cfc4465f97fe&source=post_page-cfc4465f97fe----7cc4fabf284f---------------------post_header-----------)

Published in

[

JavaScript in Plain English

](https://javascript.plainenglish.io/?source=post_page-----7cc4fabf284f--------------------------------)

·

6 min read

·

5 days ago

[

](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fvote%2Fjavascript-in-plain-english%2F7cc4fabf284f&operation=register&redirect=https%3A%2F%2Fjavascript.plainenglish.io%2Fdeep-dive-into-angulars-attribute-decorator-real-world-applications-and-tips-7cc4fabf284f&user=Astrit+Shuli&userId=cfc4465f97fe&source=-----7cc4fabf284f---------------------clap_footer-----------)

--

1

[](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fbookmark%2Fp%2F7cc4fabf284f&operation=register&redirect=https%3A%2F%2Fjavascript.plainenglish.io%2Fdeep-dive-into-angulars-attribute-decorator-real-world-applications-and-tips-7cc4fabf284f&source=-----7cc4fabf284f---------------------bookmark_footer-----------)

Listen

Share

Deep Dive into Angular’s Attribute Decorator: Real-World Applications and Tips. Photo Credits: [Astrit Shuli](https://twitter.com/itsastritshuli). Image by [upklyak](https://www.freepik.com/free-vector/tiki-masks-tribal-wooden-totems-hawaiian-polynesian-style-attributes-scary-faces-with-toothy-mouth_12682481.htm) on Freepik

Angular is a powerful framework that simplifies building dynamic web applications. To harness its full potential, it’s essential to understand its various features and decorators. One such decorator, the `@Attribute` decorator, is a fundamental tool in the Angular developer's toolkit.

In this article, we’ll explore the `@Attribute` decorator in Angular and provide real-world usage examples to help you grasp its significance in your projects.

## Understanding the @Attribute Decorator

The `@Attribute` decorator is primarily used to access and manipulate HTML attributes within Angular components. It enables you to extract attribute values, which can be especially useful when you need to configure or customize your components based on these values.

## Syntax

@Attribute('attributeName') attributeValue: string;

- `attributeName`: The name of the HTML attribute you want to access.
- `attributeValue`: The variable in which the attribute value will be stored

# Real-World Usage Examples

Now, let’s dive into some practical use cases of the `@Attribute` decorator in Angular.

# 1. Accessing Custom HTML Attributes

Suppose you have a custom HTML element with a `data-` attribute, and you want to retrieve its value within your Angular component. Here's how you can do it using the `@Attribute` decorator:

<!-- Custom HTML element with a data attribute -->  
<app-custom-element data-title="My Custom Element"></app-custom-element>

import { Component, Attribute } from '@angular/core';  
  
@Component({  
  selector: 'app-custom-element',  
  template: '<p>{{ customTitle }}</p>'  
})  
export class CustomElementComponent {  
  constructor(@Attribute('data-title') public customTitle: string) {}  
}

In this example, we use the `@Attribute` decorator to access the `data-title` attribute and display its value in the `customTitle` property of our component.

# 2. Conditional Styling Based on Attributes

You can also use the `@Attribute` decorator to conditionally style elements based on their attributes. Consider a scenario where you want to change the background color of a button based on an `enabled` attribute:

<button appColorChange [enabled]="true">Change Color</button>

import { Directive, ElementRef, Input, Renderer2, HostListener } from '@angular/core';  
  
@Directive({  
  selector: '[appColorChange]'  
})  
export class ColorChangeDirective {  
  constructor(private el: ElementRef, private renderer: Renderer2) {}  
  
  @Input('enabled') set enabled(enabled: boolean) {  
    if (enabled) {  
      this.renderer.setStyle(this.el.nativeElement, 'background-color', 'green');  
    } else {  
      this.renderer.setStyle(this.el.nativeElement, 'background-color', 'red');  
    }  
  }  
}

In this example, the `@Attribute` decorator is used to set the button's background color to green or red based on the `enabled` attribute.

# 3. Dynamic Component Configuration

You can dynamically configure components based on attribute values. For instance, let’s say you want to create a tooltip component with customizable text:

<app-tooltip text="Hover me for a tooltip!"></app-tooltip>

import { Component, Attribute } from '@angular/core';  
  
@Component({  
  selector: 'app-tooltip',  
  template: '<div class="tooltip">{{ tooltipText }}</div>',  
  styles: [`  
    .tooltip {  
      position: relative;  
    }  
  `]  
})  
export class TooltipComponent {  
  constructor(@Attribute('text') public tooltipText: string) {}  
}

In this example, the `@Attribute` decorator allows you to customize the tooltip's text by providing an attribute value.

# 4. Dynamic Image Loading

Suppose you have an Angular component responsible for displaying images, and you want to load a specific image based on an attribute. Here’s how you can achieve this using the `@Attribute` decorator:

<app-image-loader src="assets/image1.jpg"></app-image-loader>

import { Component, Attribute, OnInit } from '@angular/core';  
  
@Component({  
  selector: 'app-image-loader',  
  template: '<img [src]="imageUrl" alt="Dynamic Image">'  
})  
export class ImageLoaderComponent implements OnInit {  
  constructor(@Attribute('src') private imageSrc: string) {}  
  
  imageUrl: string;  
  
  ngOnInit() {  
    this.imageUrl = this.imageSrc;  
  }  
}

In this example, the `@Attribute` decorator is used to extract the `src` attribute value, and the component dynamically loads the specified image.

# 5. Language Localization

If you’re working on a multilingual application, you can use the `@Attribute` decorator to set the language for a specific component:

<app-localized-text lang="fr">Bonjour le monde</app-localized-text>

import { Component, Attribute } from '@angular/core';  
  
@Component({  
  selector: 'app-localized-text',  
  template: '<p>{{ localizedText }}</p>'  
})  
export class LocalizedTextComponent {  
  constructor(@Attribute('lang') private language: string) {}  
  
  localizedText: string;  
  
  ngOnInit() {  
    if (this.language === 'fr') {  
      this.localizedText = 'Bonjour le monde';  
    } else {  
      this.localizedText = 'Hello, world';  
    }  
  }  
}

Here, the `@Attribute` decorator is used to specify the language, and the component displays the appropriate text based on the `lang` attribute.

# 6. Custom Form Fields

If you’re building custom form components, you can use the `@Attribute` decorator to configure the behavior of the form field based on attributes:

<app-custom-input type="text" placeholder="Enter your name"></app-custom-input>

import { Component, Attribute } from '@angular/core';  
  
@Component({  
  selector: 'app-custom-input',  
  template: '<input [type]="inputType" [placeholder]="inputPlaceholder">'  
})  
export class CustomInputComponent {  
  constructor(@Attribute('type') private inputType: string, @Attribute('placeholder') private inputPlaceholder: string) {}  
}

In this example, the `@Attribute` decorator is used to specify the `type` and `placeholder` attributes for a custom input field.

# 7. Responsive Components

Imagine you have a component that needs to adapt its behavior based on the screen size. You can use the `@Attribute` decorator to specify breakpoints:

<app-responsive-component breakpoint="tablet">Content for Tablets</app-responsive-component>

import { Component, Attribute } from '@angular/core';  
  
@Component({  
  selector: 'app-responsive-component',  
  template: '<div *ngIf="isTablet">{{ content }}</div>'  
})  
export class ResponsiveComponent {  
  constructor(@Attribute('breakpoint') private breakpoint: string) {}  
  
  content: string;  
  isTablet: boolean = false;  
  
  ngOnInit() {  
    this.content = this.nativeElement.innerHTML;  
    if (this.breakpoint === 'tablet') {  
      // Determine if the current viewport matches the tablet breakpoint  
      // Set the 'isTablet' property accordingly  
    }  
  }  
}

In this example, the `@Attribute` decorator is used to specify the desired breakpoint, allowing the component to respond dynamically to different screen sizes.

# 8. Theme Switcher

To create a theme switcher in your Angular application, you can use the `@Attribute` decorator to select a theme:

<app-theme-switcher theme="dark">Dark Theme</app-theme-switcher>

import { Component, Attribute } from '@angular/core';  
  
@Component({  
  selector: 'app-theme-switcher',  
  template: '<div [class]="themeClass">{{ content }}</div>'  
})  
export class ThemeSwitcherComponent {  
  constructor(@Attribute('theme') private selectedTheme: string) {}  
  
  content: string;  
  themeClass: string;  
  
  ngOnInit() {  
    this.content = this.nativeElement.innerHTML;  
    this.themeClass = this.selectedTheme === 'dark' ? 'dark-theme' : 'light-theme';  
  }  
}

In this example, the `@Attribute` decorator is used to specify the theme, and the component dynamically applies the corresponding CSS class.

# 9. Authentication and Authorization

You can use the `@Attribute` decorator to control access to certain parts of your application based on user roles:

<app-protected-section role="admin">Admin-Only Content</app-protected-section>

import { Component, Attribute } from '@angular/core';  
  
@Component({  
  selector: 'app-protected-section',  
  template: '<div *ngIf="isAuthorized">{{ content }}</div>'  
})  
export class ProtectedSectionComponent {  
  constructor(@Attribute('role') private requiredRole: string) {}  
  
  content: string;  
  isAuthorized: boolean = false;  
  
  ngOnInit() {  
    this.content = this.nativeElement.innerHTML;  
    // Check user role and determine if access is granted based on 'requiredRole'  
  }  
}

In this example, the `@Attribute` decorator is used to specify the required user role, allowing the component to conditionally display content based on user permissions.

# 10. Custom CSS Styling

You can use the `@Attribute` decorator to apply custom CSS styles to a component:

<app-custom-styled-div custom-style="color: blue; font-size: 16px;">Styled Content</app-custom-styled-div>

import { Component, Attribute } from '@angular/core';  
  
@Component({  
  selector: 'app-custom-styled-div',  
  template: '<div [style]="customStyle">{{ content }}</div>'  
})  
export class CustomStyledDivComponent {  
  constructor(@Attribute('custom-style') private customStyle: string) {}  
  
  content: string;  
  
  ngOnInit() {  
    this.content = this.nativeElement.innerHTML;  
  }  
}

In this example, the `@Attribute` decorator is used to specify custom CSS styles, allowing the component to apply them dynamically.

# Conclusion

The `@Attribute` decorator in Angular is a powerful tool for working with HTML attributes in your components. It enables you to extract and manipulate attribute values, leading to more dynamic and interactive web applications. By mastering this decorator, you can enhance your Angular development skills and build feature-rich web applications with ease.

We’ve explored various use cases of the `@Attribute` decorator, such as accessing custom HTML attributes, conditional styling, and dynamic component configuration. With this knowledge, you can leverage the decorator in your Angular projects to create more flexible and customizable components.

Angular’s `@Attribute` decorator is a valuable addition to your developer toolkit, and it's worth exploring further to unlock its full potential in your applications. Happy coding!

# In Plain English

_Thank you for being a part of our community! Before you go:_

- _Be sure to_ **_clap_** _and_ **_follow_** _the writer! 👏_
- _You can find even more content at_ [**_PlainEnglish.io_**](https://plainenglish.io/) **_🚀_**
- _Sign up for our_ [**_free weekly newsletter_**](http://newsletter.plainenglish.io/)_. 🗞️_
- _Follow us:_ [**_Twitter_**](https://twitter.com/inPlainEngHQ)**_(X_**), [**_LinkedIn_**](https://www.linkedin.com/company/inplainenglish/), [**_YouTube_**](https://www.youtube.com/channel/UCtipWUghju290NWcn8jhyAw), [**_Discord_**](https://discord.gg/in-plain-english-709094664682340443)**_._**
- _Check out our other platforms:_ [**_Stackademic_**](https://stackademic.com/), [**_CoFeed_**](https://cofeed.app/), [**_Venture_**](https://venturemagazine.net/).