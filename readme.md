# Angular Basic Notes

- Angular is a client side framework developed by Google company

- Angular framework is developed using TypeScript

- Angular is mainley used for Single Page Applications Development

- Angular supports multiple devices ( Mobiles & Desktops )

- Angular supports multiple browsers

- Angular is free and open source framework

- Angular JS and Angular both are not same

- From Angular 2 version onwards it is called as Angular Framework

	``` Note: The current version of Angular is 15 ```

## Angular Building Blocks

  1) Components
  2) Metadata
  3) Template
  4) Data Binding
  5) Module
  6) Service
  7) Dependency Injection
  8) Directives
  9) Pipes

### Basics

- **Angular application is collection of components**. In **components** we will write logic to send data to template and capture data from template. Components are TypeScript classes.

- **Metadata** nothing but data about the data. It provides information about components and templates.

- **Template** is a view where we will write our presentation logic. In Angular application template is a HTML file. Every Component contains its own Template.

- **Data Binding** is the process of binding data between component property and view element in template file.

- **Module** is a collection of components, directives and pipes

- **Service** means it contains re-usable business logic. Service classes we will inject into Components using Depdency Injection.

- **Dependency Injection** is the process of injecting dependent object into target object. In Angular applications services will be injected into components using DI.

- **Directives** are used to manipulate DOM elements in the Template. 
(We can execute presentation logic based on conditions like if-else , loops etc... using directives)

- **Pipes** are used to transform the data before displaying 
  (lower case to upper case, INR to USD, dd/mm/yyyy to DD-MMM-YYYY)



### Environment Setup For Angular Applications

  1) Install Node JS
  2) Install TypeScript
  3) Install Angular CLI
  4) Install Visual Studio Code IDE

- Angular 2+ framework is available as a collection of packages, those packages are available in "Node". To use those packages "npm" (Node Package Manager) is must and should..

	```URL : https://nodejs.org/en/```

- After installing node software, open cmd and type node -v. It should display node version number then installation is successfull.

- Angular framework itself is developed based on TypeScript. In Angular applications we will write code using TypeScript only.

- We can install Typescript using Node Package Manager (npm). Open command prompt and execute below command to install TS.

	      npm install -g typescript

- After TypeScript installation got completed we can verify version number using below command in cmd. If it displays version number then installtion is successfull.

	      tsc

- Install Angular CLI software using below command in TypeScript.

        npm install @angular/cli -g

- Check angular installation using below command

	      ng v

- Download and install VS code IDE

	``` URL : https://code.visualstudio.com/download ```


``` Note: We are done with angular setup... lets start building angular applications ```

## Creating new angular project

- Create workspace folder in your file system

- Open command prompt from your workspace folder then type 'code .' then it will open VS CODE IDE from that folder

- Open terminal in VS CODE IDE to execute our commands ...

- To create angular application execute below command in command prompt

		 ng new <app-name>

- Once application got created, navigate into that application folder and execute below command to run angular application.

		 ng serve

- Angular applications will be deployed into live server which runs on port number 4200. Once application is deployed we can access that using below URL

		URL : http://localhost:4200/

- We can modify default response in app.component.html file

			Goto -> Project folder -> src -> app > app.component.html  (edit this file)


## Angular packages

- **@angular/core :** This pkg provides classes and interfaces that are related to decorators, components and DI. These are mandatory in every Angular 2+ application.

- **@angular/common :** This package provides common directives and pipes which are used in most of the angular applications.

- **@angular/compiler :** This package is used to compile "template" into "java script" code. We never invoke angular compiler directley. We will invoke that indirectly using below 2 packages

		  @angular/platform-browser
		  @angular/platform-browser-dynamic

- **@angular/platform-browser :** This package provides runtime services which are required to run our application in browser.

- **@angular/platform-browser-dynamic :** An angular application can have any no.of modules. This package is used to bootstrap (start) a module, which execution should be started automatically when application started.


- **@angular/forms :** This package is used to create "two way data bindings" , "validations" in angular 2+ applications. This package works based on another package called "zone.js". This package contains below two modules

	    a) Forms Module
	    b) Reactive Forms Module

- **@angular/router** : This package is used to create routings (page navigations) in Angular 2+ applications.


- **@angular/http :** This package is used to send Ajax request to server and get Ajax response from server.

- **@angular/animations :** This package is used to create animations in angular application.

- **@angular/material :** This package is used for "angular material design" in angular applications.

- **@angular/cdk :** Based on this package only "angular material design" components are developed. So this package must be used while using "@angular/material" package.

- **@angular/cli :** This package provides set of commands to create new angular application, components, pipes, directives, services etc.


### Common steps
* In angular application we can have any no.of modules

* When we run angular application, it starts execution from startup module i.e app-module

* Angular application boot strapping will begin from app module

* AppModule will bootstrap AppComponent

* AppComponent is the default component in Angular application


### We can see below files in app module

 	 src/app/app.module.ts
	 src/app/app.component.ts
	 src/app/app.component.html
 	 src/app/app.component.css
 	 src/app/app.component.spec.ts

src/app/app.module.ts
------------------
  	
- This file contains definition of app module

- Angular app can have any no.of modules. It should at least one module i.e called as "AppModule"

- This file imports "AppComponent" from app.component.ts file and bootstraps the same in "AppModule"

### app.component

```angular
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
  bootstrap: [AppComponent]
})
export class AppModule { }
```
### src/app/app.component.ts

- This file contains defintion of "AppComponent"

- In Angular application we can have many components. It should contain atleast one component that is called as "AppComponent"

```angular
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'app1';
}
```

- selector is used to invoke the component

- templateUrl represents presentation logic file (html)

- styleUrls represents css file(s)

 ### src/app/app.component.html
- This file contains presentation logic of component

- Every component will have its own template

- This template file content will be rendered into 
   <app-root></app-root> selector tag at index.html
  
### src/app/app.component.css

- This file contains css syles of "AppComponent"

- By default this file is empty

### src/app/app.component.spec.ts

- This file contains test cases for "AppComponent"

- The test case files should have "spec.ts" file extension

## Excution FLow

- In Angular application **"index.html"** file will act as wecome file

- When we access Angular application URL in Browser it will load index.html file

- In **index.html** file we are using AppComponent selector to invoke AppComponent.

             <app-root></app-root>
### Commanads

- We can create Component in the Angular using below command

	    $ ng generate component <component-name>

- When we create new component it will generate 4 files like below

 	 CREATE src/app/greet/greet.component.html (20 bytes)
	 CREATE src/app/greet/greet.component.spec.ts (619 bytes)
	 CREATE src/app/greet/greet.component.ts (271 bytes)     
	 CREATE src/app/greet/greet.component.css (0 bytes)      
	 UPDATE src/app/app.module.ts (478 bytes)

## Components   	
- The component class represents certain section of web page. For example, "login form" is represented as login component.

- The component class includes "properties" to store the data, "methods" to manipulate the data.

- Every Angular 2+ application contains at-least one component which is called as "app component". We can create any no.of components in angular application.

- A component is invoked through a custom tag called as selector. "app component" selector is "<app-root></app-root>".

- The Component class should have a decorator called "@Component" to define that class as Component class.

### Component Class
```
import {Component} from "@angular/core"

@Component (meta-data)
class ClassName{

    property:dataType = value; 

    method(args) : returnType {
         //logic
    }
}

```

### Metadata properties of @Component
```
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})

```


- **selector** : represents tag which is used to invoke the component

- **templateUrl** : represents the html file that has to be rendered when the component is invoked

- **template** represents content of content

- **styleUrls** : Represents the list of styles (css) that have to be loaded for the component.

- **providers** : Represents list of services to be imported into the component
 
- **animations** : Represents list of animations to be performed in the component.


- **animations** : Represents list of animations to be performed in the component.

> Note: The components which we are creating will act as child components for AppComponent.

- Child Components we will access from AppComponent using Selector.

- Create Welcome Component & Greet Component

- Invoke Welcome Component & Greet Component in AppComponent like below

### app.component.html

```html
<h1> This message from AppComponent</h1>
<app-welcome></app-welcome>
<app-greet></app-greet>
```

> Note: Every Component having its own CSS file to apply styles for that component related template logic.

## Data Bindings

- The "data binding" is used to establish relation between "component" and "template".

- When the value of "component" is changed, then template will be changed automatically. When the value of "template" is changed, then the "component" will be changed automatically.

- Data Bindings are four Types

      1) Interpolation
      2) Property Binding
      3) Event Binding
      4) Two Way Binding

### Interpolation
- It is used to display the value of variable /  property in template file

- If the property value is changed then automatically it will be updated in template

		syntax :  {{propertyName}}
  
### Property Binding

- Property Binding is used to send the data from component to template and assign the same into an attribute of tag.

- If the property value is changed then automatically it will be updated in template

		Syntax: [attribute]=*property

### Event Binding

- It is used to pass event notifications from template to component

		Syntax :  <tag (event) = "method()" > </tag>

### Two Way Binding

- Two-way data binding is the combination of both property binding and event binding

- When we change the value of the property then automatically it will be updated in HTML element.

- When we change the value of HTML element then automatically it will updated in property.

- "ngModel" is the pre-defined directive which is used to achieve two-way data binding.

- Two way data binding is applicable only for <input/> and <select/> tags.

- "FormsModule" must be imported in order to use Two Way Data Binding
