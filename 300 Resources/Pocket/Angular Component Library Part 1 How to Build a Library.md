---
url: https://www.telerik.com/blogs/angular-component-library-part-1-how-to-build
readlater:
  id: "3954495360"
  provider: pocket
  synchtime: 1699293690850
---
[skip navigation](#skip-to-content)[](/)

- Kendo UI for Angular
    
    ##### Product Bundles
    
    [
    
    #### DevCraft
    
    All Telerik .NET tools and Kendo UI JavaScript components in one package. Now enhanced with:
    
    - **NEW**: Design Kits for Figma
    - Online Training
    - Document Processing Library
    - Embedded Reporting for web and desktop
    
    ](/devcraft)
    
    ##### Web
    
    [Kendo UI](/kendo-ui) [UI for jQuery](/kendo-jquery-ui) [UI for Angular](/kendo-angular-ui) [UI for React](/kendo-react-ui) [UI for Vue](/kendo-vue-ui) [UI for Blazor](/blazor-ui) [UI for ASP.NET Core](/aspnet-core-ui) [UI for ASP.NET MVC](/aspnet-mvc) [UI for ASP.NET AJAX](/products/aspnet-ajax.aspx) [UI for Silverlight](/products/silverlight/overview.aspx) [UI for PHP](/php-ui) [UI for JSP](/jsp-ui)
    
    ##### Mobile
    
    [UI for .NET MAUI](/maui-ui) [UI for Xamarin](/xamarin-ui)
    
    ##### Document Management
    
    [Telerik Document Processing](/document-processing-libraries)
    
    ##### Desktop
    
    [UI for .NET MAUI](/maui-ui) [UI for WinUI](/winui) [UI for WinForms](/products/winforms.aspx) [UI for WPF](/products/wpf/overview.aspx) [UI for UWP](/universal-windows-platform-ui)
    
    ##### Reporting & Mocking
    
    [Telerik Reporting](/products/reporting.aspx) [Telerik Report Server](/report-server) [Telerik JustMock](/products/mocking.aspx)
    
    ##### Automated Testing
    
    [Test Studio](/teststudio) [Test Studio Dev Edition](/teststudio-dev)
    
    ##### CMS
    
    [Sitefinity](https://www.progress.com/sitefinity-cms)
    
    ##### UI/UX Tools
    
    [ThemeBuilder](/themebuilder) [Design System Kit](/design-system)
    
    ##### Debugging
    
    [Fiddler](/fiddler) [Fiddler Everywhere](/fiddler/fiddler-everywhere) [Fiddler Classic](/fiddler/fiddler-classic) [Fiddler Jam](/fiddler-jam) [FiddlerCap](/fiddler/fiddlercap) [FiddlerCore](/fiddlercore)
    
    ##### Extended Reality
    
    [UI for Unity XR](/unity-xr-ui)
    
    ##### Free Tools
    
    [JustAssembly](/justassembly) [JustDecompile](/products/decompiler.aspx) [VB.NET to C# Converter](https://converter.telerik.com) [Testing Framework](/teststudio/testing-framework)
    
    [View all products](/all-products)
    

- [Overview](/kendo-angular-ui)
- Frameworks
    - [jQuery](/kendo-jquery-ui)
    - [Angular](/kendo-angular-ui)
    - [React](/kendo-react-ui)
    - [Vue](/kendo-vue-ui)
- [Docs & Demos](/kendo-angular-ui/components/)
- [Get Started](/kendo-angular-ui/components/getting-started/)
- Resources
    
    #### Support and Learning
    
    - [Support and Learning Hub](/support/kendo-ui-for-angular)
    - [First Steps](/kendo-angular-ui/components/getting-started/)
    - [Angular Tutorials and Learning](/kendo-angular-ui/resources)
    - [Virtual Classroom](https://learn.telerik.com/learn/course/external/view/elearning/55/kendo-ui-for-angular)
    - [Forums](/forums/kendo-angular-ui)
    - [Submit a Ticket](/account/support-center)
    
    #### Resources
    
    - [Docs & Demos](/kendo-angular-ui/components/)
    - [Videos](/videos/product/kendo-angular-ui)
    - [Blogs](/blogs/web-angular)
    - [What’s New](/support/whats-new/kendo-angular-ui)
    - [Roadmap](/kendo-angular-ui/components/roadmap/)
    - [Release History](/kendo-angular-ui/components/changelogs/kendo-angular-ui/)
    
    #### Productivity and Design Tools
    
    - [ThemeBuilder](/themebuilder)
    - [Design System Documentation](/design-system/docs/)
    - [Visual Studio Code Extensions](/kendo-angular-ui/components/installation/vscode-extension/)
    - [Embedded Reporting](/products/reporting.aspx)
    
- [Pricing](/purchase/kendo-ui)

- [Search](/search "Search")
- [Shopping cart](https://store.progress.com/shopping-cart "Shopping cart")
- [Login](/account/ "Your Account")
- [Contact Us](/contact?preselect=ui-for-angular "Contact Us")
- [Try now](/try/kendo-angular-ui)

close mobile menu

[![Telerik blogs](https://d585tldpucybw.cloudfront.net/sfimages/default-source/svg/blogs-ninjasa0020c9284b44432a37b7f0f41d28d1d.svg "Telerik blogs")](/blogs)

# Angular Component Library Part 1: How to Build a Component Library with Angular

 ![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/author-images/dany-paredes-google-expert-angular.png?sfvrsn=c8ecca3f_3 "dany-paredes-google-expert-angular") by [Dany Paredes](/blogs/author/dany-paredes)October 23, 2023 [Web](/blogs/web), [Angular](/blogs/web-angular) [0 Comments](#disqus_thread)

![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/templates/angulart2-light-1200x303.png?sfvrsn=4af99b70_4 "AngularT2-light-1200x303")

[](# "Facebook Share Icon")[](# "Twitter Share Icon")  
[](# "Linkedin Share Icon")[](https://www.reddit.com/submit?url=http://www.telerik.com/blogs/angular-component-library-part-1-how-to-build "Reddit Share Icon")  
[](https://feeds.telerik.com/blogs "Feed Share Icon")

Using a component library accelerates your development because you can skip redesigning and re-coding the same components. Here’s how to start your own shared component library in Angular.

As developers working in a company with a variety of products, we find that reusing the same components and styles between applications can be challenging. Building our own library helps us cut down on code duplication and offers a smooth, cohesive interface, which can significantly boost our team’s productivity. Moreover, it ensures consistent functionality across all applications, saving valuable time and resources—no more dealing with the same issues in different apps!

The ideal solution for this issue is to create a shared library that allows for effortless distribution of code among projects. Fortunately, Angular offers a straightforward method to develop a library for sharing components, services and utilities.

But the best way to understand how a library helps us speed up our team and deliver fast, consistent projects is to show a real scenario.

## Scenario

We work for a large accounting software company that needs to release two new applications for banking and registration. Both applications require a set of buttons.

What can we do?

- Create identical buttons for both the banking and registration applications.
- Share the CSS between both applications and duplicate the button component.
- Make sure we think long term: What would happen if the company changed its brand color? This should be something we ought to be able to update in the future without too much hassle.

We can resolve this issue by creating a shared button library for both applications. Let’s proceed with this solution.

## Create the Library

Before creating the library, we need to set up a workspace to serve as the location for our library and apps. To do this, we can use the Angular CLI and run the following command to set up the workspace:

```bash
ng new my-company --create-application=false
```

> This will create a new Angular workspace without creating an initial application.

```bash
C:\Users\dany.paredes\Desktop>ng new my-company --create-application=false
CREATE my-company/angular.json (139 bytes)
CREATE my-company/package.json (993 bytes)
CREATE my-company/README.md (1063 bytes)
CREATE my-company/tsconfig.json (901 bytes)
CREATE my-company/.editorconfig (274 bytes)
CREATE my-company/.gitignore (548 bytes)
CREATE my-company/.vscode/extensions.json (130 bytes)
CREATE my-company/.vscode/launch.json (474 bytes)
CREATE my-company/.vscode/tasks.json (938 bytes)
√ Packages installed successfully.
```

Once the setup is generated inside the my-company directory, we will generate the library. The name of your library is important, especially if you plan to publish it later in a public package registry like npm.

> Avoid using names that start with “ng-” as it is a reserved keyword used by the Angular framework and its libraries. Use the prefix “ngx-” to denote that the library is suitable for use with Angular.

After picking the name `ngx-banana-ui`, use the command `ng generate library ngx-banana-ui --prefix=banana`.

> The [–prefix=banana](https://angular.io/guide/creating-libraries#getting-started): changes your component prefix from `<app-my-lib>` to `<banana-my-component>`, by default.

```bash
cd my-company
ng g library ngx-banana-ui --prefix=banana
```

```typescript
C:\Users\dany.paredes\Desktop\my-company>ng g library ngx-banana-ui --prefix=banana
CREATE projects/ngx-banana-ui/ng-package.json (162 bytes)
CREATE projects/ngx-banana-ui/package.json (217 bytes)
CREATE projects/ngx-banana-ui/README.md (1033 bytes)
CREATE projects/ngx-banana-ui/tsconfig.lib.json (314 bytes)
CREATE projects/ngx-banana-ui/tsconfig.lib.prod.json (240 bytes)
CREATE projects/ngx-banana-ui/tsconfig.spec.json (273 bytes)
CREATE projects/ngx-banana-ui/src/public-api.ts (183 bytes)
CREATE projects/ngx-banana-ui/src/lib/ngx-banana-ui.module.ts (269 bytes)
CREATE projects/ngx-banana-ui/src/lib/ngx-banana-ui.component.spec.ts (636 bytes)
CREATE projects/ngx-banana-ui/src/lib/ngx-banana-ui.component.ts (214 bytes)
CREATE projects/ngx-banana-ui/src/lib/ngx-banana-ui.service.spec.ts (384 bytes)
CREATE projects/ngx-banana-ui/src/lib/ngx-banana-ui.service.ts (140 bytes)
UPDATE angular.json (1149 bytes)
UPDATE package.json (1070 bytes)
UPDATE tsconfig.json (985 bytes)
```

![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/2023/2023-10/angular-project.png?sfvrsn=5d1ea025_3)

> Read more about projects in [Angular](https://angular.io/guide/file-structure#library-project-files).

The “ng generate” command creates the “projects/my-lib” folder in your workspace, which contains a component and a service inside an `NgModule` with the `public-api.ts` to export the library API for it.

The CLI generates a public-api.ts file in your library folder. This is an essential file because anything exported from this file is made public when your library is imported into an application by using the ngx-banana-ui.module to expose services and components.

![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/2023/2023-10/angular-public-api-ts.png?sfvrsn=a0f12124_3)

## The Buttons

With the setup in place, we can generate the button component using the Angular/CLI by running `ng g c components/button` command.

```typescript
PS C:\Users\dany.paredes\Desktop\my-company\projects\ngx-banana-ui\src\lib> ng g c components/button       
CREATE projects/ngx-banana-ui/src/lib/components/button/button.component.html (21 bytes)
CREATE projects/ngx-banana-ui/src/lib/components/button/button.component.spec.ts (599 bytes)
CREATE projects/ngx-banana-ui/src/lib/components/button/button.component.ts (205 bytes)
CREATE projects/ngx-banana-ui/src/lib/components/button/button.component.css (0 bytes)
UPDATE projects/ngx-banana-ui/src/lib/ngx-banana-ui.module.ts (481 bytes)
```

Just like any other Angular component, we can add properties and styles. Open the button.component.css file and add the following style:

```css
.button {
  background-color:#0a0a23;
  color: #fff;
box-sizing: border-box;
display: inline-block;
border: 0;
border-radius: 10px;
padding: 15px;
min-height: 30px;
min-width: 120px;
opacity: 0.8;


cursor: pointer;
text-align: center;
font-size: 1rem;
line-height: 1.2;
transition: opacity 0.3s ease;
}

.button:hover {
  opacity: 1;
}
```

Since we aim to create a customizable label button, add an input property to the component:

```typescript
import {Component, Input} from '@angular/core';

@Component({
  selector: 'banana-button',
  templateUrl: './button.component.html',
  styleUrls: ['./button.component.css']
})
export class ButtonComponent {
  @Input() label = 'Accept';
}
```

Finally, add the HTML markup:

```html
<button class="button">{{label}}</button>
```

Perfect, we have already set up the button. Next, we need to export the button component into the public-api.ts.

![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/2023/2023-10/angular-button.png?sfvrsn=7b0c7b2c_3)

## Build the Library

We’ll first create a bundle in the dist folder to build our Angular library by running the command `ng build ngx-banana-ui`.

```typescript
PS C:\Users\dany.paredes\Desktop\my-company\projects> ng build ngx-banana-ui
Building Angular Package

------------------------------------------------------------------------------
Building entry point 'ngx-banana-ui'
------------------------------------------------------------------------------
√ Compiling with Angular sources in Ivy partial compilation mode.
√ Generating FESM2020
√ Generating FESM2015
√ Copying assets
√ Writing package manifest
√ Built ngx-banana-ui

------------------------------------------------------------------------------
Built Angular Package
 - from: C:\Users\dany.paredes\Desktop\my-company\projects\ngx-banana-ui
 - to:   C:\Users\dany.paredes\Desktop\my-company\dist\ngx-banana-ui
------------------------------------------------------------------------------

Build at: 2023-04-23T15:36:34.716Z - Time: 2888ms
```

This command will create a dist folder; inside this folder, our compiled library is stored.

## Publish as Local Package

As we have already built the library, we now need to build it as an npm package for the npm package manager. Once that is done, we can publish it to the local node package manager’s registry.

So we will go to our `dist/ngx-banana-ui/` folder and run the command `npm pack`:

```typescript
C:\Users\dany.paredes\Desktop\my-company\dist\ngx-banana-ui>npm pack
npm notice
npm notice package: ngx-banana-ui@1.2.3
npm notice === Tarball Contents ===
npm notice 1.0kB README.md
npm notice 2.4kB esm2020/lib/components/button/button.component.mjs
npm notice 1.7kB esm2020/lib/ngx-banana-ui.component.mjs
npm notice 2.8kB esm2020/lib/ngx-banana-ui.module.mjs
npm notice 1.5kB esm2020/lib/ngx-banana-ui.service.mjs
npm notice 512B  esm2020/ngx-banana-ui.mjs
npm notice 981B  esm2020/public-api.mjs
npm notice 4.2kB fesm2015/ngx-banana-ui.mjs
npm notice 4.0kB fesm2015/ngx-banana-ui.mjs.map
npm notice 4.2kB fesm2020/ngx-banana-ui.mjs
npm notice 4.0kB fesm2020/ngx-banana-ui.mjs.map
npm notice 123B  index.d.ts
npm notice 315B  lib/components/button/button.component.d.ts
npm notice 298B  lib/ngx-banana-ui.component.d.ts
npm notice 527B  lib/ngx-banana-ui.module.d.ts
npm notice 247B  lib/ngx-banana-ui.service.d.ts
npm notice 828B  package.json
npm notice 198B  public-api.d.ts
npm notice === Tarball Details ===
npm notice name:          ngx-banana-ui
npm notice version:       1.2.3
npm notice filename:      ngx-banana-ui-1.2.3.tgz
npm notice package size:  5.7 kB
npm notice unpacked size: 29.8 kB
npm notice shasum:        93acb4890e0523a754e17ca02bb917a0046324a7
npm notice integrity:     sha512-Le0XCo3OuXbEj[...]CmfAMUJyMO+xQ==
npm notice total files:   18
npm notice
ngx-banana-ui-1.2.3.tgz
```

This will create the package ngx-banana-ui-1.2.3.tgz, and local publishing will be completed! Now, we can use this library in any Angular application. Let’s quickly attempt to install the library into another Angular application.

## Installing and Registering the Library

Now it’s a fun moment, consume the library, but first, create a new application using the Angular CLI.

```bash
ng new bank
```

Next, copy the ngx-banana-ui-1.2.3.tgz file to the root of the bank application.

![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/2023/2023-10/angular-tgz-to-root.png?sfvrsn=f044b824_3)

Next, install the library by running `npm i ngx-banana-ui-1.2.3.tgz`.

```typescript
C:\Users\dany.paredes\Desktop\bank>npm i ngx-banana-ui-1.2.3.tgz

added 1 package, removed 1 package, and audited 910 packages in 2s

95 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

Import the NgxBananaUiModule into the AppModule in the app.module.ts file.

![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/2023/2023-10/import-to-appmodule.png?sfvrsn=f9d32a9e_3)

Replace the default HTML and utilize the components.

```html
<div class="container">

  <div class="example">
    Button with a custom message<banana-button label="Amazing Button Library" />

    The default message button: <banana-button />
  </div>
</div>
```

Done!! Our app uses our library with amazing buttons!

![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/2023/2023-10/angular-amazing-button-library.png?sfvrsn=e3e2f237_3)

- [https://github.com/danywalls/ngx-banana](https://github.com/danywalls/ngx-banana)

## What’s Next?

This example demonstrates how to create a library with a single button. However, a library is more than just a button; it must offer a range of components. Beyond simply providing components, there are several crucial aspects to consider when constructing a robust, flexible library for our organization.

To build your own library, you need to take care of other points like:

- **Distribution:** In our scenario, we are using a local build, but we might want to allow our company to install using an npm package from the internet.
- **Theme:** Allow our consumers to alter the colors of our buttons, alerts or components. We should provide a method for them to modify these colors easily.
- **Organization:** We must organize how to install and import the components. For example, we must use components without forcing our consumers to install numerous components if they only need one. Therefore, we should divide our components into smaller packages to install.

Yeah, it’s a nice adventure and it’s just the beginning. You can save time by using a pre-built library like [Kendo UI for Angular](/kendo-angular-ui).

## Conclusion

We’ve learned a ton about creating a workspace, developing a library, exposing the API and integrating it into an application. It has been a truly rewarding adventure.

In the [next article, we learn about how to theme and publish our library to npm](https://www.telerik.com/blogs/angular-component-library-part-2-how-to-theme-publish-npm).

---

[Angular](/blogs/tag/angular)

![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/author-images/dany-paredes-google-expert-angular.png?sfvrsn=c8ecca3f_3 "dany-paredes-google-expert-angular")

About the Author

### Dany Paredes

Dany Paredes is a Google Developer Expert on Angular and loves sharing content and writing articles about Angular, TypeScript and testing in [his blog](http://dev.to/danywalls) and on Twitter ([@danywalls](https://twitter.com/danywalls)).

### Related Posts

[Web](/blogs/web) [Angular](/blogs/web-angular)

#### [Angular Component Library Part 2: How to Theme and Publish Your Library to npm](/blogs/angular-component-library-part-2-how-to-theme-publish-npm)

[Web](/blogs/web) [Angular](/blogs/web-angular)

#### [Sorting, Filtering, Grouping and Aggregating Data in Angular](/blogs/sorting-filtering-grouping-aggregating-data-angular)

[Web](/blogs/web) [Angular](/blogs/web-angular)

#### [Manipulating Data in Angular with Kendo UI Data Query](/blogs/manipulating-data-angular-kendo-ui-data-query)

[Web](/blogs/web) [Angular](/blogs/web-angular)

#### [Effortlessly Create Rich Text Content with Angular Kendo UI Editor](/blogs/effortlessly-create-rich-text-content-angular-kendo-ui-editor)

---

### Comments

Comments are disabled in preview mode.

Please enable JavaScript to view the [comments powered by Disqus.](https://disqus.com/?ref_noscript)

 

#### [All articles](/blogs)

##### Topics

[Web](/blogs/web)

- [Blazor](/blogs/web-blazor)
- [ASP.NET Core](/blogs/web-aspnet-core)
- [ASP.NET MVC](/blogs/web-aspnet-mvc)
- [ASP.NET AJAX](/blogs/web-aspnet-ajax)
- [Angular](/blogs/web-angular)
- [React](/blogs/web-react)
- [jQuery](/blogs/web-jquery)
- [Vue](/blogs/web-vue)

[Mobile](/blogs/mobile)

- [.NET MAUI](/blogs/mobile-net-maui)
- [Xamarin](/blogs/mobile-xamarin)

[Desktop](/blogs/desktop)

- [Blazor Desktop/.NET MAUI](/blogs/desktop-blazor-net-maui)
- [WPF](/blogs/desktop-wpf)
- [WinForms](/blogs/desktop-winforms)
- [WinUI](/blogs/desktop-winui)
- [UWP](/blogs/desktop-uwp)

[Design](/blogs/design)

- [UX](/blogs/design-ux)
- [Design Systems](/blogs/design-systems)

[Productivity](/blogs/productivity)

- [Reporting](/blogs/productivity-reporting)
- [Testing](/blogs/productivity-testing)
- [Debugging](/blogs/productivity-debugging)
- [Document Processing](/blogs/productivity-document-processing)

[People](/blogs/people)

- [Accessibility](/blogs/people-accessibility)
- [Humanity](/blogs/people-humanity)

[Release](/blogs/release)

[![](https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/banners/kendo-ui-for-angularb_the-component-library-developers-trust-250x250.png?sfvrsn=49575b4d_6 "Kendo UI for AngularB_The Component Library Developers Trust-250x250")](https://www.telerik.com/kendo-angular-ui?utm_medium=cpm&utm_source=kendoblog&utm_campaign=kendo-ui-angular-awareness-general&utm_content=250x250)

##### Latest Stories  
in Your Inbox

Subscribe to be the first to get our expert-written articles and tutorials for developers!

All fields are required

  

![Loading animation](/WebResource.axd?d=kLXF93zSE8rrtGGHz2_yEHKUQ3nCpsv2U-3cILbSEvOdQzH3J0ni8TPzdVKJpmRz6UDfLTLRqP6pohNdgx3_V5KOAZNjOAsMljY880d5NBvUKG0lKct-_ZXtbJ8_lNNdxm_Cl3AnJGWoNyFyOJlI5tvVRaJvk8hapGLJ9ZSm5Djl7Q9jx4GGMISsk8cmKusSuwNnMw2&t=638333075480000000)

  Email 

 Country/Territory  Select country/territory United States Afghanistan Albania Algeria American Samoa Andorra Angola Anguilla Antarctica Antigua and Barbuda Argentina Armenia Aruba Australia Austria Azerbaijan Bahamas Bahrain Bangladesh Barbados Belgium Belize Benin Bermuda Bhutan Bolivia Bosnia and Herzegovina Botswana Bouvet Island Brazil British Indian Ocean Terr. Brunei Darussalam Bulgaria Burkina Faso Burundi Cambodia Cameroon Canada Cape Verde Cayman Islands Central African Republic Chad Chile China Christmas Island Cocos (Keeling) Islands Colombia Comoros Congo (Brazzaville) Congo, the democratic republic of the Cook Islands Costa Rica Cote d'Ivoire Croatia (Hrvatska) Curacao Cyprus Czech Republic Denmark Djibouti Dominica Dominican Republic Ecuador Egypt El Salvador Equatorial Guinea Eritrea Estonia Eswatini Ethiopia Falkland Islands Faroe Islands Fiji Finland France French Guiana French Polynesia French Southern Terr. Gabon Gambia Georgia Germany Ghana Gibraltar Greece Greenland Grenada Guadeloupe Guam Guatemala Guernsey Guinea Guinea-Bissau Guyana Haiti Heard and McDonald Is. Honduras Hong Kong Hungary Iceland India Indonesia Iraq Ireland Israel Italy Jamaica Japan Jersey Jordan Kazakhstan Kenya Kiribati Kuwait Kyrgyzstan Lao People's Dem. Rep. Latvia Lebanon Lesotho Liberia Libya Liechtenstein Lithuania Luxembourg Macao Madagascar Malawi Malaysia Maldives Mali Malta Man, Isle of Marshall Islands Martinique Mauritania Mauritius Mayotte Mexico Micronesia Moldova Monaco Mongolia Montenegro Montserrat Morocco Mozambique Myanmar Namibia Nauru Nepal Netherlands New Caledonia New Zealand Nicaragua Niger Nigeria Niue Norfolk Island North Macedonia Northern Mariana Is. Norway Oman Pakistan Palau Palestine, State Of Panama Papua New Guinea Paraguay Peru Philippines Pitcairn Poland Portugal Puerto Rico Qatar Republic of Korea (South Korea) Reunion Romania Rwanda S.Georgia and S.Sandwich Is. Saint Kitts and Nevis Saint Lucia Samoa San Marino Sao Tome and Principe Saudi Arabia Senegal Serbia Seychelles Sierra Leone Singapore Slovakia Slovenia Solomon Islands Somalia South Africa South Sudan Spain Sri Lanka St. Helena St. Pierre and Miquelon St. Vincent and Grenadines Sudan Suriname Svalbard and Jan Mayen Is. Sweden Switzerland Taiwan Tajikistan Tanzania Thailand Timor-Leste Togo Tokelau Tonga Trinidad and Tobago Tunisia Turkey Turkmenistan Turks and Caicos Islands Tuvalu U.S. Minor Outlying Is. Uganda Ukraine United Arab Emirates United Kingdom Uruguay Uzbekistan Vanuatu Vatican (Holy See) Venezuela Viet Nam Virgin Islands (British) Virgin Islands (U.S.) Wallis and Futuna Is. Western Sahara Yemen Zambia Zimbabwe

   State/Province Select

Progress collects the Personal Information set out in our [Privacy Policy](https://www.progress.com/legal/privacy-policy) and [the Supplemental Privacy notice for residents of California and other US States](https://www.progress.com/legal/california-resident-privacy-notice) and uses it for the purposes stated in that policy.

You can also ask us not to share your Personal Information to third parties here: [Do Not Sell or Share My Info](https://forms.progress.com/ccpa-subscription)

  Blog 

   

By submitting this form, I understand and acknowledge my data will be processed in accordance with Progress' [Privacy Policy](https://www.progress.com/legal/privacy-policy).

I agree to receive email communications from Progress Software or its [Partners](https://www.progress.com/partners/partner-directory), containing information about Progress Software’s products. I understand I may opt out from marketing communication at any time [here](https://forms.progress.com/emailoptin) or through the opt out option placed in the e-mail communication received.

By submitting this form, you understand and agree that your personal data will be processed by Progress Software or its [Partners](https://www.progress.com/partners/partner-directory) as described in our [Privacy Policy](https://www.progress.com/legal/privacy-policy). You may opt out from marketing communication at any time [here](https://forms.progress.com/emailoptin) or through the opt out option placed in the e-mail communication sent by us or our Partners.

We see that you have already chosen to receive marketing materials from us. If you wish to change this at any time you may do so by clicking [here](https://forms.progress.com/emailoptin).

Thank you for your continued interest in Progress. Based on either your previous activity on our websites or our ongoing relationship, we will keep you updated on our products, solutions, services, company news and events. If you decide that you want to be removed from our mailing lists at any time, you can change your contact preferences by clicking [here](https://forms.progress.com/emailoptin).

 

Subscribe

   

Complete .NET Toolbox

[Telerik DevCraft](/devcraft)

Complete JavaScript Toolbox

[Kendo UI](/kendo-ui)

Get Products

- [Free Trials](/download)
- [Pricing](/purchase.aspx)

Resources

- [Demos](/support/demos)
- [Documentation](/documentation)
- [Release History](/support/whats-new/release-history)
- [Forums](/forums)
- [Blogs](/blogs)
- [Webinars](/webinars)
- [Videos](/videos)
- [Professional Services](/services)
- [Partners](https://www.progress.com/partners/partner-locator?Products=KendoUI+and+Telerik)
- [Virtual Classroom](/support/virtual-classroom)
- [Events](https://www.progress.com/events)

Recognition

- [Success Stories](/about/success-stories)
- [Testimonials](/about/testimonials)

Get in touch

- [Contact Us](/contact)
- - [USA: +1 800 213 3407](tel:+18002133407)
    - [UK: +44 13 4483 8186](tel:+441344838186)
    - [India: +91 406 9019447](tel:+914069019447)
    - [Bulgaria: +359 2 8099850](tel:+35928099850)
    - [Australia: +61 3 7068 8610](tel:+61370688610)
- - [165k+](https://www.facebook.com/telerik "Facebook")
    - [50k+](https://twitter.com/telerik "Twitter")
    - [17k+](https://www.linkedin.com/company/telerik "LinkedIn")
    - [4k+](https://www.twitch.tv/codeitlive "Twitch")
    - [14k+](https://www.youtube.com/c/telerik "YouTube")
    - [](https://github.com/telerik "GitHub")

- [Contact Us](/contact)
- - [165k+](https://www.facebook.com/telerik "Facebook")
    - [50k+](https://twitter.com/telerik "Twitter")
    - [17k+](https://www.linkedin.com/company/telerik "LinkedIn")
    - [4k+](https://www.twitch.tv/codeitlive "Twitch")
    - [14k+](https://www.youtube.com/c/telerik "YouTube")
    - [](https://github.com/telerik "GitHub")

[](https://www.progress.com)

Telerik and Kendo UI are part of Progress product portfolio. Progress is the leading provider of application development and digital experience technologies.

- [Company](https://www.progress.com/company)
- [Technology](https://www.progress.com/products)
- [Awards](https://www.progress.com/company/awards)
- [Press Releases](http://investors.progress.com/releases.cfm)
- [Media Coverage](https://www.progress.com/company/press-coverage)
- [Careers](https://www.progress.com/company/careers)
- [Offices](https://www.progress.com/company/offices)

- [Company](https://www.progress.com/company)
- [Technology](https://www.progress.com/products)
- [Awards](https://www.progress.com/company/awards)
- [Press Releases](http://investors.progress.com/releases.cfm)
- [Media Coverage](https://www.progress.com/company/press-coverage)
- [Careers](https://www.progress.com/company/careers)
- [Offices](https://www.progress.com/company/offices)

Copyright © 2023 Progress Software Corporation and/or its subsidiaries or affiliates. All Rights Reserved.

Progress, Telerik, Ipswitch, Chef, Kemp, Flowmon, MarkLogic, Semaphore and certain product names used herein are trademarks or registered trademarks of Progress Software Corporation and/or one of its subsidiaries or affiliates in the U.S. and/or other countries. See [Trademarks](https://www.progress.com/legal/trademarks) for appropriate markings.

- [Terms of Use](/about/terms-of-use)
- [Site Feedback](/feedback)
- [Privacy Center](https://www.progress.com/legal/privacy-center)
- [Security Center](https://www.progress.com/security)

[Do Not Sell or Share My Personal Information](https://forms.progress.com/ccpa-subscription)

Powered by [Progress Sitefinity](https://www.progress.com/sitefinity-cms)