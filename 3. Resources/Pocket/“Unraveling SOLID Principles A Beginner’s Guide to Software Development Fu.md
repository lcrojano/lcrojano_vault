---
url: https://systemweakness.com/unraveling-solid-principles-a-beginners-guide-to-software-development-fundamentals-03c891c5309e
readlater:
  id: "3961354885"
  provider: pocket
  synchtime: 1699813107670
---
# “Unraveling SOLID Principles: A Beginner’s Guide to Software Development Fundamentals”

[

![Rishabh Gaud](https://miro.medium.com/v2/resize:fill:88:88/1*x5pPz45mX-jJa0b6lvXw1A.jpeg)









](https://gaudrishabh.medium.com/?source=post_page-----03c891c5309e--------------------------------)[

![System Weakness](https://miro.medium.com/v2/resize:fill:48:48/1*gncXIKhx5QOIX0K9MGcVkg.jpeg)











](https://systemweakness.com/?source=post_page-----03c891c5309e--------------------------------)

[Rishabh Gaud](https://gaudrishabh.medium.com/?source=post_page-----03c891c5309e--------------------------------)

·

[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fuser%2F2d562fc577ed&operation=register&redirect=https%3A%2F%2Fsystemweakness.com%2Funraveling-solid-principles-a-beginners-guide-to-software-development-fundamentals-03c891c5309e&user=Rishabh+Gaud&userId=2d562fc577ed&source=post_page-2d562fc577ed----03c891c5309e---------------------post_header-----------)

Published in

[

System Weakness

](https://systemweakness.com/?source=post_page-----03c891c5309e--------------------------------)

·

4 min read

·

Nov 1

[

](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fvote%2Fsystem-weakness%2F03c891c5309e&operation=register&redirect=https%3A%2F%2Fsystemweakness.com%2Funraveling-solid-principles-a-beginners-guide-to-software-development-fundamentals-03c891c5309e&user=Rishabh+Gaud&userId=2d562fc577ed&source=-----03c891c5309e---------------------clap_footer-----------)

--

[](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fbookmark%2Fp%2F03c891c5309e&operation=register&redirect=https%3A%2F%2Fsystemweakness.com%2Funraveling-solid-principles-a-beginners-guide-to-software-development-fundamentals-03c891c5309e&source=-----03c891c5309e---------------------bookmark_footer-----------)

Listen

Share

image src: [https://blog.knoldus.com/all-you-need-to-know-about-solid-principles/](https://blog.knoldus.com/all-you-need-to-know-about-solid-principles/)

Hey everyone! Today, let’s dive into the fundamental concepts of S.O.L.I.D principles in programming. The SOLID Principles represent a crucial set of guidelines for designing object-oriented classes. These five principles establish essential rules and best practices for structuring classes, aiding in understanding the necessity for specific design patterns and overall software architecture. These principles might sound complex, but trust me, they’re like the secret sauce that makes your code stand out among the rest. Let’s break it down.

S — **S**ingle Responsibility Principle

O — **O**pen Closed Principle

L — **L**iskov Substitution Principle

I — **I**nterface Segmented Principle

D — **D**ependency Inversion Principle

Let’s try to gives shot to each one by one.

# **S — Single Responsibility Principle**

Single responsibility principle said that a class have only single reason to change. If we use this principle, our code will be easy to understands and maintains.

Let’s take an example to understand. Picture your favorite gaming character. In coding terms, this principle says that each class should be like that character, doing just one thing excellently. Check this out:

class Player {  
public:  
    void move() {  
        // Code to move the player  
    }  
  
    void attack() {  
        // Code to make the player attack  
    }  
};

But let’s say we split these responsibilities into different classes — one for moving and one for attacking. That’s the Single Responsibility Principle in action!

# O — Open Closed Principle

Open for extension but closed for modification.

If the classes are already written then according to this principle, we can extend but we are not allowed to modify the existing class.

Think of your favorite app on your phone. When developers add new features to it without breaking the existing ones, that’s the Open Closed Principle. Check it out in code:

class Device {  
public:  
    virtual void unlock() const = 0; // Abstract method  
};  
  
// Subclasses can be added without modifying existing classes.  
class FaceRecognition : public Device {  
public:  
    void unlock() const override {  
        // Code for face recognition unlock  
    }  
};  
  
class Passcode : public Device {  
public:  
    void unlock() const override {  
        // Code for passcode unlock  
    }  
};

We can add new unlocking methods without changing the existing code, just like updating your app with new features!

# L — Liskov Substitution Principle

If class B is sub type of class A, then we should be able to replace object of A with B without breaking the behavior of the program.

Subclass should extend the capability of parent class not narrow it down.

Ever heard the saying “_If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck_”? That’s Liskov Substitution Principle in action:

class Animal {  
public:  
    virtual void makeSound() const {  
        // Generic animal sound  
    }  
};  
  
class Duck : public Animal {  
public:  
    void makeSound() const override {  
        // Code for duck's quacking  
    }  
};

When a `Duck` class behaves like an `Animal` class, it’s a smooth substitution without changing the behavior.

# I — Interface Segmented Principle

Interface should be such that client should not implement unnecessary functions they do not need.

Think of your favorite game controller. You don’t want unnecessary buttons, right? That’s the Interface Segregation Principle — classes should have what they need.

class GamePad {  
public:  
    virtual void move() = 0;  
    virtual void attack() = 0;  
};  
  
class XboxController : public GamePad {  
public:  
    void move() override {  
        // Code to move with an Xbox controller  
    }  
  
    void attack() override {  
        // Code to attack with an Xbox controller  
    }  
};

The `XboxController` only implements the needed functions, following the Interface Segregation Principle.

# D — Dependency Inversion Principle

Class should depend on interfaces rather than concrete classes. In other word we can say that high-level of class does not directly depends on low-level class, instead we used interface to provide independently between the classes.

Imagine a game with interchangeable weapons. The Dependency Inversion Principle suggests high-level classes should depend on abstractions, not specifics (or low-level classes):

class Weapon {  
public:  
    virtual void attack() = 0;  
};  
  
class Player {  
private:  
    Weapon* playerWeapon;  
  
public:  
    Player(Weapon* weapon) : playerWeapon(weapon) {}  
  
    void useWeapon() {  
        playerWeapon->attack();  
    }  
};  
  
class Sword : public Weapon {  
public:  
    void attack() override {  
        // Code for sword attack  
    }  
};

The Player class depends on the Weapon abstraction, allowing it to use different weapons without changing its code.

# Conclusion

Implementing these principles isn’t just about writing code; it’s about creating a mindset and approach to software development that emphasizes clarity, adaptability, and maintainability.

By adhering to SOLID principles, tech professionals not only produce better code but also build a solid foundation for long-term software evolution. It’s like mastering a set of superpowers that transform code into a dynamic, scalable, and sustainable solution.

> I am Rishabh Gaud, I work as a Software Developer, and really enjoy building Distributed Systems. Feel free to reach out to me on [Linkedin](https://www.linkedin.com/in/rishabhgaud7800/) or [Portfolio](https://rishabhgaud.vercel.app/) for anything related to tech.
> 
> Happy learning 😃

Thank you for reading!.

Let me know if you have any feedback or comments.