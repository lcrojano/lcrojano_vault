---
url: https://itnext.io/elevating-user-experience-with-light-and-dark-mode-in-angular-apps-a-bootstrap-and-angular-5047b4d8f2f6
readlater:
  id: "3963205841"
  provider: pocket
  synchtime: 1699813107283
---
# Elevating User Experience with Light and Dark Mode in Angular Apps: A Bootstrap and Angular Material Guide

[

![Astrit Shuli](https://miro.medium.com/v2/resize:fill:88:88/1*6LE4DCjTIgvrMAOPRdp_4Q.png)









](https://astritshuli.medium.com/?source=post_page-----5047b4d8f2f6--------------------------------)[

![ITNEXT](https://miro.medium.com/v2/resize:fill:48:48/1*yAqDFIFA5F_NXalOJKz4TA.png)











](https://itnext.io/?source=post_page-----5047b4d8f2f6--------------------------------)

[Astrit Shuli](https://astritshuli.medium.com/?source=post_page-----5047b4d8f2f6--------------------------------)

·

[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fuser%2Fcfc4465f97fe&operation=register&redirect=https%3A%2F%2Fitnext.io%2Felevating-user-experience-with-light-and-dark-mode-in-angular-apps-a-bootstrap-and-angular-5047b4d8f2f6&user=Astrit+Shuli&userId=cfc4465f97fe&source=post_page-cfc4465f97fe----5047b4d8f2f6---------------------post_header-----------)

Published in

[

ITNEXT

](https://itnext.io/?source=post_page-----5047b4d8f2f6--------------------------------)

·

3 min read

·

3 days ago

[

](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fvote%2Fitnext%2F5047b4d8f2f6&operation=register&redirect=https%3A%2F%2Fitnext.io%2Felevating-user-experience-with-light-and-dark-mode-in-angular-apps-a-bootstrap-and-angular-5047b4d8f2f6&user=Astrit+Shuli&userId=cfc4465f97fe&source=-----5047b4d8f2f6---------------------clap_footer-----------)

--

[](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fbookmark%2Fp%2F5047b4d8f2f6&operation=register&redirect=https%3A%2F%2Fitnext.io%2Felevating-user-experience-with-light-and-dark-mode-in-angular-apps-a-bootstrap-and-angular-5047b4d8f2f6&source=-----5047b4d8f2f6---------------------bookmark_footer-----------)

Listen

Share

Elevating User Experience with Light and Dark Mode in Angular Apps: A Bootstrap and Angular Material Guide. Photo by: [Astrit Shuli](https://medium.com/u/cfc4465f97fe?source=post_page-----5047b4d8f2f6--------------------------------)

In the realm of Angular development, enhancing user experience is a constant pursuit. One effective way to achieve this is by implementing light and dark mode features. In this article, we’ll explore the integration of these modes using both Bootstrap and Angular Material, along with practical examples and the incorporation of a service for seamless theming.

# Part 1: Implementing Light and Dark Mode with Bootstrap

## 1. Setting Up Bootstrap:

Begin by installing Bootstrap in your Angular project:

ng add ngx-bootstrap

## 2. Creating Theme Files:

Bootstrap uses SCSS for theming. Create separate SCSS files for light and dark themes:

// styles-light.scss  
$body-bg: #fff;  
$body-color: #000;  
  
// Add other Bootstrap variables as needed  
  
@import "~bootstrap/scss/bootstrap";

// styles-dark.scss  
$body-bg: #333;  
$body-color: #fff;  
  
// Add other Bootstrap variables as needed  
  
@import "~bootstrap/scss/bootstrap";

## 3. Toggling Themes:

Use a service to toggle between the light and dark themes. Create a `ThemeService` with methods to set and get the current theme.

// theme.service.ts  
import { Injectable } from '@angular/core';  
import { BehaviorSubject } from 'rxjs';  
  
@Injectable({  
  providedIn: 'root'  
})  
export class ThemeService {  
  private _theme = new BehaviorSubject<string>('light');  
  theme$ = this._theme.asObservable();  
  
  setTheme(theme: string): void {  
    this._theme.next(theme);  
  }  
  
  getTheme(): string {  
    return this._theme.value;  
  }  
}

## 4. Applying Theme in Components:

In your components, dynamically load the appropriate theme based on the service’s current theme.

// app.component.ts  
import { Component, OnInit } from '@angular/core';  
import { ThemeService } from './theme.service';  
  
@Component({  
  selector: 'app-root',  
  templateUrl: './app.component.html',  
  styleUrls: ['./app.component.scss']  
})  
export class AppComponent implements OnInit {  
  constructor(private themeService: ThemeService) {}  
  
  ngOnInit(): void {  
    this.themeService.theme$.subscribe(theme => {  
      document.body.classList.toggle('dark-theme', theme === 'dark');  
    });  
  }  
}

## 5. Toggle Button in UI:

Provide a UI element to allow users to switch between light and dark modes.

<!-- app.component.html -->  
<button (click)="toggleTheme()">Toggle Theme</button>

// app.component.ts  
// ...  
toggleTheme(): void {  
  const newTheme = this.themeService.getTheme() === 'light' ? 'dark' : 'light';  
  this.themeService.setTheme(newTheme);  
}

# Part 2: Angular Material Integration

## 1. Setting Up Angular Material:

If not already done, install Angular Material in your project:

ng add @angular/material

## 2. Creating Theme Files:

Follow the same steps as in the previous example to create separate SCSS files for light and dark modes.

// styles-light.scss  
@import '~@angular/material/theming';  
  
$light-theme-primary: mat-palette($mat-indigo);  
$light-theme-accent: mat-palette($mat-pink, A200, A100, A400);  
$light-theme-warn: mat-palette($mat-red);  
  
$light-theme: mat-light-theme(  
  $light-theme-primary,  
  $light-theme-accent,  
  $light-theme-warn  
);  
  
@include angular-material-theme($light-theme);

// styles-dark.scss  
@import '~@angular/material/theming';  
  
$dark-theme-primary: mat-palette($mat-indigo);  
$dark-theme-accent: mat-palette($mat-pink, A200, A100, A400);  
$dark-theme-warn: mat-palette($mat-red);  
  
$dark-theme: mat-dark-theme(  
  $dark-theme-primary,  
  $dark-theme-accent,  
  $dark-theme-warn  
);  
  
@include angular-material-theme($dark-theme);

## 3. Toggling Themes:

Reuse the `ThemeService` created earlier to handle theme toggling.

## 4. Applying Theme in Components:

Subscribe to the `theme$` observable and apply the Angular Material theme dynamically.

// app.component.ts  
import { Component, OnInit } from '@angular/core';  
import { ThemeService } from './theme.service';  
  
@Component({  
  selector: 'app-root',  
  templateUrl: './app.component.html',  
  styleUrls: ['./app.component.scss']  
})  
export class AppComponent implements OnInit {  
  constructor(private themeService: ThemeService) {}  
  
  ngOnInit(): void {  
    this.themeService.theme$.subscribe(theme => {  
      document.body.classList.toggle('dark-theme', theme === 'dark');  
    });  
  }  
}

## 5. Toggle Button in UI:

Provide a UI element to allow users to switch between light and dark modes.

<!-- app.component.html -->  
<button (click)="toggleTheme()">Toggle Theme</button>

// app.component.ts  
// ...  
toggleTheme(): void {  
  const newTheme = this.themeService.getTheme() === 'light' ? 'dark' : 'light';  
  this.themeService.setTheme(newTheme);  
}

# Conclusion

By incorporating both Bootstrap and Angular Material, you can offer users a choice between two widely used styling frameworks while ensuring a seamless transition between light and dark modes. The provided examples and services demonstrate the versatility of Angular in creating a customizable and visually appealing user experience. Experiment with different themes, and empower your users to tailor the application to their preferences. Happy theming!