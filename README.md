# angular-instagram
Angular instagram page

Why were client-side frameworks like Angular introduced?

Back in the day, web developers used VanillaJS and jQuery to develop dynamic websites but, as the logic of one's website grew, the code became more and more tedious to maintain. For applications that use complex logic, developers had to put in extra effort to maintain separation of concerns for the app. Also, jQuery did not provide facilities for data handling across views.
For tackling the above problems, client-side frameworks like Angular came into the picture, which made life easier for the developers by handling separation of concerns and dividing code into smaller bits of information (In the case of Angular, called Components).
Client-side frameworks allow one to develop advanced web applications like Single-Page-Application. Not that we cannot develop SPAs using VanillaJS, but by doing so, the development process becomes slower

How does an Angular application work?

Every Angular app consists of a file named angular.json. This file will contain all the configurations of the app. While building the app, the builder looks at this file to find the entry point of the application.

Inside the build section, the main property of the options object defines the entry point of the application which in this case is main.ts.
The main.ts file creates a browser environment for the application to run, and, along with this, it also calls a function called bootstrapModule, which bootstraps the application. These two steps are performed in the following order inside the main.ts file:
import { platformBrowserDynamic } from '@angular/platform
platformBrowserDynamic().bootstrapModule(AppModule)


In the above line of code, AppModule is getting bootstrapped.
The AppModule is declared in the app.module.ts file. This module contains declarations of all the components.
Below is an example of app.module.ts file:
    
      import { BrowserModule } from '@angular/platform-browser';
      import { NgModule } from '@angular/core';
      import { AppComponent } from './app.component';

      @NgModule({
        declarations: [
          AppComponent
        ],
        imports: [
          BrowserModule
        ],
        providers: [],
        entryComponents: [],
        bootstrap: [AppComponent]
      })
      export class AppModule { }

As one can see in the above file, AppComponent is getting bootstrapped.
This component is defined in app.component.ts file. This file interacts with the webpage and serves data to it.
Below is an example of app.component.ts file:
    
      import { Component } from '@angular/core';

      @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css']
      })
      export class AppComponent {
        title = 'angular';
      }

Each component is declared with three properties:
1. Selector - used for accessing the component
2. Template/TemplateURL - contains HTML of the component
3. StylesURL - contains component-specific stylesheets


After this, Angular calls the index.html file. This file consequently calls the root component that is app-root. The root component is defined in app.component.ts.
This is how the index.html file looks:
    
      <!doctype html>
      <html lang="en">
      <head>
        <meta charset="utf-8">
        <title>Angular</title>
        <base href="/">
        <meta name="viewport" content="width=device-width, initial-scale=1">
      </head>
      <body>
        <app-root></app-root>
      </body>
      </html>
    
  


The HTML template of the root component is displayed inside the <app-root> tags.

This is how every angular application works.

What are some of the advantages of Angular over other frameworks?

•  Features that are provided out of the box - Angular provides a number of built-in features like,routing, state management, rxjs library and http servicesstraight out of the box. This means that one does not need tolook for the above stated features separately. They are allprovided with angular.
•  Declarative UI - Angular uses HTML to render the UI of an application. HTML isa declarative language and is much easier to use than JavaScript.

•  Long-term Google support - Google announced Long-term support for Angular. This means that Google plans to stick with Angular and further scale up its ecosystem.

4. List out differences between AngularJS and Angular
Architecture
AngularJS uses MVC or Model-View-Controller architecture, where the Model contains the business logic, Controller processes information and View shows the information present in the Model.
Angular replaces controllers with Components. Components are nothing but directives with a predefined template.
Language
AngularJS uses JavaScript language, which is a dynamically typed language.
Angular uses TypeScript language, which is a statically typed language and is a superset of JavaScript. By using statically typed language, Angular provides better performance while developing larger applications.
Mobile Support
AngularJS does not provide mobile support.
Angular is supported by all popular mobile browsers.
Structure
While developing larger applications, the process of maintaining code becomes tedious in the case of AngularJS.
In the case of Angular, it is easier to maintain code for larger applications as it provides a better structure.
Expression Syntax
While developing an AngularJS application, a developer needs to remember the correct ng-directive for binding an event, or a property. Whereas in Angular, property binding is done using "[ ]" attribute and event binding is done using "( )" attribute.

What is AOT compilation? What are the advantages of AOT?

Every Angular application consists of components and templates which the browser cannot understand. Therefore, all the Angular applications need to be compiled first before running inside the browser.

Angular provides two types of compilation:
•  JIT(Just-in-Time) compilation
•  AOT(Ahead-of-Time) compilation

In JIT compilation, the application compiles inside the browser during runtime.
Whereas in the AOT compilation, the application compiles during the build time.

The advantages of using AOT compilation are:

•  Since the application compiles before running inside the browser, the browser loads the executable code and renders the application immediately, which leads to faster rendering.
•  In AOT compilation, the compiler sends the external HTML and CSS files along with the application, eliminating separate AJAX requests for those source files, which leads to fewer ajax requests.
•  Developers can detect and handle errors during the building phase, which helps in minimizing errors.
•  The AOT compiler adds HTML and templates into the JS files before they run inside the browser. Due to this, there are no extra HTML files to be read, which provide better security to the application.

By default, angular builds and serves the application using JIT compiler:
ng build
ng serve
For using AOT compiler following changes should be made:
ng build --aot
ng serve --aot


6. Explain Components, Modules and Services in Angular

For better understanding, I would like you to create an Angular application by running the following inside the command terminal:
ng new angularApp


The above command will create an angular application in the directory.
Next, let's move on to understand Components, Modules, and Services.

Components
In Angular, components are the basic building blocks, which control a part of the UI for any application.
A component is defined using the @Component decorator. Every component consists of three parts, the template which loads the view for the component, a stylesheet which defines the look and feel for the component, and a class that contains the business logic for the component.
For creating a component, inside the command terminal, navigate to the directory of the application created, and run the following command:
ng generate component test


Or
ng g c test


One can see the generated component inside src/app/test folder. The component will be defined inside test.component.ts and this is how it looks:


    
      import { Component, OnInit } from '@angular/core';

      @Component({
        selector: 'app-test',
        templateUrl: './test.component.html',
        styleUrls: ['./test.component.css']
      })
      export lass TestComponent implements OnInit {

        constructor() {}

        ngOnInit() {
        }
      }
    
  
As we can see in the above image, our component is defined with @Component decorator.

Modules
A module is a place where we can group components, directives, services, and pipes. Module decides whether the components, directives, etc can be used by other modules, by exporting or hiding these elements. Every module is defined with a @NgModule decorator.
By default, modules are of two types:
•  Root Module
•  Feature Module Every application can have only one root module whereas, it can have one or more feature modules.
A root module imports BrowserModule, whereas a feature module imports CommonModule.

In the application that we created before, one can see that the root module is defined inside app.module.ts and this is how it looks:
    
      import { BrowserModule } from '@angular/platform-browser';
      import { NgModule } from '@angular/core';

      import { AppComponent } from './app.component';
      import { TestComponent } from './test/text.component';

      @NgModule({
        declarations: [
          AppComponent,
          TestComponent
        ],
        imports: [
          BrowserModule
        ],
        providers: [],
        bootstrap: [AppComponent]
      })
      export class AppModule { }
    
  
We can see in the above image that the component we created earlier is already imported in the declarations array.

To create a feature module, run the following command:
ng g m test-module
The module is created inside the src/app/test-module/test-module.module.ts file:
    
      import { NgModule } from '@angular/core';
      import { CommonModule } from '@angular/common';

      @NgModule({
        declarations: [],
        imports: [
          CommonModule
        ]
      })
      export class TestModuleModule { }
    
  
As one can see, CommonModule is imported since this is a feature module.
Services Services are objects which get instantiated only once during the lifetime of an application. The main objective of a service is to share data, functions with different components of an Angular application.
A service is defined using a @Injectable decorator. A function defined inside a service can be invoked from any component or directive.

To create a service, run the following command:
ng g s test-service


The service will be created inside src/app/test-service.service.ts:
    
      import { Injectable } from '@angular/core';

      @Injectable({
        providedIn: 'root'
      })
      export class TestServiceService {

        constructor() { }

      }
    
  
Any method/function defined inside the TestServiceService class can be directly used inside any component by just importing the service.
7. What are lifecycle hooks in Angular? Explain a few lifecycle hooks.
Every component in Angular has a lifecycle, different phases it goes through from the time of creation to the time it's destroyed. Angular provides hooks to tap into these phases and trigger changes at specific phases in a lifecycle.

 

ngOnChanges( ) This hook/method is called before ngOnInit and whenever one or more input properties of the component changes.
This method/hook receives a SimpleChanges object which contains the previous and current values of the property.

ngOnInit( ) This hook gets called once, after the ngOnChanges hook.
It initializes the component and sets the input properties of the component.

ngDoCheck( ) It gets called after ngOnChanges and ngOnInit and is used to detect and act on changes that cannot be detected by Angular.
We can implement our change detection algorithm in this hook. ngAfterContentInit( ) It gets called after the first ngDoCheck hook. This hook responds after the content gets projected inside the component.

ngAfterContentChecked( ) It gets called after ngAfterContentInit and every subsequent ngDoCheck. It responds after the projected content is checked.

ngAfterViewInit( ) It responds after a component's view, or a child component's view is initialized.

ngAfterViewChecked( ) It gets called after ngAfterViewInit, and it responds after the component's view, or the child component's view is checked.

ngOnDestroy( ) It gets called just before Angular destroys the component. This hook can be used to clean up the code and detach event handlers.

Let’s understand how to use ngOnInit hook, since it’s the most oftenly used hook. If one has to process lot of data during component creation, it’s better to do it inside ngOnInit hook rather than the constructor:
    
      import { Component, OnInit } from '@angular/core';

      @Component({
        selector: 'app-test',
        templateUrl: './test.component.html',
        styleUrls: ['./test.component.css']
      })
      export class TestComponent implements OnInit {
        constructor() { }

        ngOnInit() {
          this.processData();
        }

        processData(){
          // Do something..
        }

      }
    
  
As you can see we have imported OnInit but we have used ngOnInit function. This principle should be used with the rest of the hooks as well.


7. What are lifecycle hooks in Angular? Explain a few lifecycle hooks.
Every component in Angular has a lifecycle, different phases it goes through from the time of creation to the time it's destroyed. Angular provides hooks to tap into these phases and trigger changes at specific phases in a lifecycle.
 

ngOnChanges( ) This hook/method is called before ngOnInit and whenever one or more input properties of the component changes.
This method/hook receives a SimpleChanges object which contains the previous and current values of the property.

ngOnInit( ) This hook gets called once, after the ngOnChanges hook.
It initializes the component and sets the input properties of the component.

ngDoCheck( ) It gets called after ngOnChanges and ngOnInit and is used to detect and act on changes that cannot be detected by Angular.
We can implement our change detection algorithm in this hook. ngAfterContentInit( ) It gets called after the first ngDoCheck hook. This hook responds after the content gets projected inside the component.

ngAfterContentChecked( ) It gets called after ngAfterContentInit and every subsequent ngDoCheck. It responds after the projected content is checked.

ngAfterViewInit( ) It responds after a component's view, or a child component's view is initialized.

ngAfterViewChecked( ) It gets called after ngAfterViewInit, and it responds after the component's view, or the child component's view is checked.

ngOnDestroy( ) It gets called just before Angular destroys the component. This hook can be used to clean up the code and detach event handlers.

Let’s understand how to use ngOnInit hook, since it’s the most oftenly used hook. If one has to process lot of data during component creation, it’s better to do it inside ngOnInit hook rather than the constructor:

    
      import { Component, OnInit } from '@angular/core';

      @Component({
        selector: 'app-test',
        templateUrl: './test.component.html',
        styleUrls: ['./test.component.css']
      })
      export class TestComponent implements OnInit {
        constructor() { }

        ngOnInit() {
          this.processData();
        }

        processData(){
          // Do something..
        }

      }
As you can see we have imported OnInit but we have used ngOnInit function. This principle should be used with the rest of the hooks as well.
8. Explain string interpolation and property binding in Angular.
String interpolation and property binding are parts of data-binding in Angular.
Data-binding is a feature in angular, which provides a way to communicate between the component(Model) and its view(HTML template).
Data-binding can be done in two ways, one-way binding and two-way binding.
In Angular, data from the component can be inserted inside the HTML template. In one-way binding, any changes in the component will directly reflect inside the HTML template but, vice-versa is not possible. Whereas, it is possible in two-way binding.

String interpolation and property binding allow only one-way data binding.
String interpolation uses the double curly braces {{ }} to display data from the component. Angular automatically runs the expression written inside the curly braces, for example, {{ 2 + 2 }} will be evaluated by Angular and the output 4, will be displayed inside the HTML template. Using property binding, we can bind the DOM properties of an HTML element to a component's property. Property binding uses the square brackets [ ] syntax.
9. How are Angular expressions different from JavaScript expressions?
The first and perhaps, the biggest difference is that Angular expressions allow us to write JavaScript in HTML which is not the case when it comes to JavaScript expressions.
Next, Angular expressions are evaluated against a local scope object whereas JavaScript expressions against global window object. Let's understand that better with an example :

Consider the following component named test:
    
      import { Component, OnInit } from '@angular/core';

      @Component({
        selector: 'app-test',
        template: `
            <h4>{{message}}</h4>
        `,
        styleUrls: ['./test.component.css']
      })
      export class TestComponent implements OnInit {
        message:string = “Hello world”;
        constructor() { }

        ngOnInit() {
        }
      }
    
  
As one can see that Angular expression is used to display message property of a component. Since we are using Angular expressions, in the present template, we cannot access a property outside of its local scope, which in this case is TestComponent.
This proves that Angular expressions are always evaluated based on scope object rather than the global object.

Next difference is how Angular expressions handle null and undefined.
Consider the following JavaScript example:
    
      <!DOCTYPE html>
      <html lang="en">
      <head>
          <meta charset="UTF-8">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>JavaScript Test</title>
      </head>
      <body>
          <div id="foo"><div>
      </body>
      <script>
          'use strict';
          let bar = {};
          document.getElementById('foo').innerHTML = bar.x;
      </script>
      </html>
    
  
If you run the above code, you will see undefined displayed on the screen. Although it’s not ideal to leave any property undefined, the user does not need to see this.
Now consider the following Angular example:
    
      import { Component, OnInit } from '@angular/core';

      @Component({
        selector: 'app-new',
        template: `
            <h4>{{message}}</h4>
        `,
        styleUrls: ['./new.component.css']
      })
      export class NewComponent implements OnInit {
        message:object = {};
        constructor() { }

        ngOnInit() {
        }

      }
    
  
If you render the above component, you will not see undefined being displayed on the screen.

Next, in Angular expressions one cannot use loops, conditionals and exceptions.

The difference which makes Angular expressions quite beneficial is the use of pipes. Angular uses pipes(called filters in AngularJS), which can be used to format data before displaying it. Let’s see one predefined pipe in action:
    
      import { Component, OnInit } from '@angular/core';

      @Component({
        selector: 'app-new',
        template: `
            <h4>{{message | lowercase}}</h4>
        `,
        styleUrls: ['./new.component.css']
      })
      export class NewComponent implements OnInit {
        message:string = "HELLO WORLD";
        constructor() { }

        ngOnInit() {
        }

      }
    
  
In the above code we have used a predefined pipe called lowercase, which transforms all the letters in lowercase. Therefore, if you render the above component, you will see “hello world” being displayed.

In contrast, JavaScript does not have the concept of pipes.
