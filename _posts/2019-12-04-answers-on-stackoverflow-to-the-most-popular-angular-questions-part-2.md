---
title: Answers on StackOverflow to the most popular Angular questions (Part 2)
image: "/assets/default-social-image.png"
categories: Angular
---

**48 answers on StackOverflow to the most popular Angular questions (Part 2/4)**

This gathered list is the most common questions and answers from **Stackoverflow**. These questions were chosen by the highest score received. Whether you are an expert or a beginner, you can learn from others’ experiences.

**Table of Contents**

#13. Angular EXCEPTION: No provider for Http

#14. Can’t bind to ‘formGroup’ since it isn’t a known property of ‘form’

#15. Angular DI Error — EXCEPTION: Can’t resolve all parameters

#16. Angular — Set headers for every request

#17. How to use `*ngIf` else in Angular?

#18. Angular no provider for NameService

#19. Binding select element to object in Angular

#20. What is difference between declarations, providers and import in NgModule

#21. In Angular, how do you determine the active route?

#22. Angular CLI SASS options

#23. Triggering change detection manually in Angular

#24. Angular and Typescript: Can’t find names

**Enjoy!**

**# 13. Angular EXCEPTION: No provider for Http**

**[daniel](https://stackoverflow.com/users/516389/daniel) asked,**

I am getting the `EXCEPTION: No provider for Http!` in my Angular app. What am I doing wrong?

```
import {Http, Headers} from 'angular2/http';
import {Injectable} from 'angular2/core'

@Component({
    selector: 'greetings-ac-app2',
    providers: [],
    templateUrl: 'app/greetings-ac2.html',
    directives: [NgFor, NgModel, NgIf, FORM_DIRECTIVES],
    pipes: []
})
export class GreetingsAcApp2 {
    private str:any;
    
    constructor(http: Http) {
    
        this.str = {str:'test'};
        http.post('http://localhost:18937/account/registeruiduser/',
            JSON.stringify(this.str),
            {
                headers: new Headers({
                    'Content-Type': 'application/json'
                })
            });
```

**[Philip Miglinci](https://stackoverflow.com/users/2083492) answered,**

Import the HttpModule

```
import { HttpModule } from '@angular/http';

@NgModule({
    imports: [ BrowserModule, HttpModule ],
    providers: [],
    declarations: [ AppComponent ],
    bootstrap: [ AppComponent ]
})
export default class AppModule { }

platformBrowserDynamic().bootstrapModule(AppModule);
```

Ideally you split up this code in two separate files. For further information read:

* [https://angular.io/docs/ts/latest/cookbook/rc4-to-rc5.html](https://angular.io/docs/ts/latest/cookbook/rc4-to-rc5.html)
* [https://angular.io/docs/ts/latest/guide/ngmodule.html](https://angular.io/docs/ts/latest/guide/ngmodule.html)

[Source](https://stackoverflow.com/questions/33721276)

**#14. Can’t bind to ‘formGroup’ since it isn’t a known property of ‘form’**

**[johnnyfittizio](https://stackoverflow.com/users/2433664/francescomussi) asked,**

**THE SITUATION:**

Please help! I am trying to make what should be a very simple form in my Angular2 app but no matter what it never works.

**ANGULAR VERSION:**

Angular 2.0.0 Rc5

**THE ERROR:**

`Can't bind to 'formGroup' since it isn't a known property of 'form'`

**THE CODE:**

The view:

```
<form [formGroup]="newTaskForm" (submit)="createNewTask()">
    <div class="form-group">
        <label for="name">Name</label>
        <input type="text" name="name" required>
    </div>
     <button type="submit" class="btn btn-default">Submit</button>
</form>
```

The controller:

```
import { Component } from '@angular/core';
import { FormGroup, FormControl, Validators, FormBuilder }  from '@angular/forms';
import {FormsModule,ReactiveFormsModule} from '@angular/forms';
import { Task } from './task';

@Component({
    selector: 'task-add',
    templateUrl: 'app/task-add.component.html'
    
})

export class TaskAddComponent {

    newTaskForm: FormGroup;
    
    constructor(fb: FormBuilder) 
    {
        this.newTaskForm = fb.group({
            name: ["", Validators.required]
        });
    }
    
    createNewTask()
    {
        console.log(this.newTaskForm.value)
    }
    
}
```

The ngModule:

```
import { NgModule }      from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule }   from '@angular/forms';

import { routing }        from './app.routing';
import { AppComponent }  from './app.component';
import { TaskService } from './task.service'

@NgModule({
    imports: [ 
        BrowserModule,
        routing,
        FormsModule
    ],
    declarations: [ AppComponent ],
    providers: [
        TaskService
    ],
    bootstrap: [ AppComponent ]
})

export class AppModule { }
```

**THE QUESTION:**

Why am I getting that error?

Am I missing something?

**[Stefan Svrkota](https://stackoverflow.com/users/6677986) answered,**

**RC5 FIX**

You need to `import { REACTIVE_FORM_DIRECTIVES } from '@angular/forms'` in your controller and add it to `directives` in `@Component`. That will fix the problem.

After you fix that, you will probably get another error because you didn’t add `formControlName="name"` to your input in form.

**RC6/RC7/Final release FIX**

To fix this error, you just need to import `ReactiveFormsModule` from `@angular/forms` in your module. Here's the example of a basic module with `ReactiveFormsModule` import:

```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule, ReactiveFormsModule } from '@angular/forms';
import { AppComponent }  from './app.component';

@NgModule({
    imports: [
        BrowserModule,
        FormsModule,
        ReactiveFormsModule
    ],
    declarations: [
        AppComponent
    ],
    bootstrap: [AppComponent]
})

export class AppModule { }
```

To explain further, `formGroup` is a selector for directive named `FormGroupDirective` that is a part of `ReactiveFormsModule`, hence the need to import it. It is used to bind an existing `FormGroup` to a DOM element. You can read more about it on [Angular's official docs page](https://angular.io/docs/ts/latest/api/forms/index/FormGroupDirective-directive.html).

**[Source](https://stackoverflow.com/questions/39152071)**

**#15. Angular DI Error — EXCEPTION: Can’t resolve all parameters**

**[Keith Otto](https://stackoverflow.com/users/4321757/keith-otto) asked,**

I’ve built a basic app in Angular, but I have encountered a strange issue where I cannot inject a service into one of my components. It injects fine into any of the three other components I have created however.

For starters, this is the service:

```
import { Injectable } from '@angular/core';

@Injectable()
export class MobileService {
  screenWidth: number;
  screenHeight: number;
  
  constructor() {
    this.screenWidth = window.outerWidth;
    this.screenHeight = window.outerHeight;
    
    window.addEventListener("resize", this.onWindowResize.bind(this) )
  }
  
  onWindowResize(ev: Event) {
    var win = (ev.currentTarget as Window);
    this.screenWidth = win.outerWidth;
    this.screenHeight = win.outerHeight;
  }
  
}
```

And the component that it refuses to work with:

```
import { Component, } from '@angular/core';
import { NgClass } from '@angular/common';
import { ROUTER_DIRECTIVES } from '@angular/router';

import {MobileService} from '../';

@Component({
  moduleId: module.id,
  selector: 'pm-header',
  templateUrl: 'header.component.html',
  styleUrls: ['header.component.css'],
  directives: [ROUTER_DIRECTIVES, NgClass],
})
export class HeaderComponent {
  mobileNav: boolean = false;
  
  constructor(public ms: MobileService) {
    console.log(ms);
  }
  
}
```

The error I get in the browser console is this:

`EXCEPTION: Can't resolve all parameters for HeaderComponent: (?).`

I have the service in the bootstrap function so it has a provider. And I seem to be able to inject it into the constructor of any of my other components without issue.

**[Günter Zöchbauer](https://stackoverflow.com/users/217408) answered,**

Import it from the file where it is declared directly instead of the barrel.

I don’t know what exactly causes the issue but I saw it mentioned several times (probably some kind of circular dependency).

It should also be fixable by changing the order of the exports in the barrel (don’t know details, but was mentioned as well)

**[Source](https://stackoverflow.com/questions/37997824)**

**#16. Angular — Set headers for every request**

**[Avijit Gupta](https://stackoverflow.com/users/4135178/avijit-gupta) asked,**

I need to set some Authorization headers after the user has logged in, for every subsequent request.

To set headers for a particular request,

```
import {Headers} from 'angular2/http';
var headers = new Headers();
headers.append(headerName, value);

// HTTP POST using these headers
this.http.post(url, data, {
  headers: headers
})
// do something with the response
```

[Reference](https://auth0.com/blog/2015/10/15/angular-2-series-part-3-using-http/)

But it would be not be feasible to manually set request headers for every request in this way.

How do I set the headers set once the user has logged in, and also remove those headers on logout?

**[Thierry Templier](https://stackoverflow.com/users/1873365) answered,**

To answer, you question you could provide a service that wraps the original `Http` object from Angular. Something like described below.

```
import {Injectable} from '@angular/core';
import {Http, Headers} from '@angular/http';

@Injectable()
export class HttpClient {

  constructor(private http: Http) {}
  
  createAuthorizationHeader(headers: Headers) {
    headers.append('Authorization', 'Basic ' +
      btoa('username:password')); 
  }
  
  get(url) {
    let headers = new Headers();
    this.createAuthorizationHeader(headers);
    return this.http.get(url, {
      headers: headers
    });
  }
  
  post(url, data) {
    let headers = new Headers();
    this.createAuthorizationHeader(headers);
    return this.http.post(url, data, {
      headers: headers
    });
  }
}
```

And instead of injecting the `Http` object you could inject this one (`HttpClient`).

```
import { HttpClient } from './http-client';

export class MyComponent {
  // Notice we inject "our" HttpClient here, naming it Http so it's easier
  constructor(http: HttpClient) {
    this.http = httpClient;
  }
  
  handleSomething() {
    this.http.post(url, data).subscribe(result => {
        // console.log( result );
    });
  }
}
```

I also think that something could be done using multi providers for the `Http` class by providing your own class extending the `Http` one... See this link: [http://blog.thoughtram.io/angular2/2015/11/23/multi-providers-in-angular-2.html](http://blog.thoughtram.io/angular2/2015/11/23/multi-providers-in-angular-2.html).

[Source](https://stackoverflow.com/questions/34464108)

**#17. How to use `*ngIf else` in Angular?**

**[kawli norman](https://stackoverflow.com/users/5486494/kawli-norman) asked,**

I’m using Angular and I want to use `*ngIf else` (available since version 4) in this example:

```
<div *ngIf="isValid">
  content here ...
</div>

<div *ngIf="!isValid">
 other content here...
</div>
```

How can I acheive the same behavior with `ngIf else` ?

**[Bougarfaoui El houcine](https://stackoverflow.com/users/7273246) answered,**

Angular 4 and 5:

using `else` :

```
<div *ngIf="isValid;else other_content">
    content here ...
</div>

<ng-template #other_content>other content here...</ng-template>
```

you can also use `then else` :

```
<div *ngIf="isValid;then content else other_content">here is ignored</div>

<ng-template #content>content here...</ng-template>
<ng-template #other_content>other content here...</ng-template>
```

or `then` alone :

```
<div *ngIf="isValid;then content"></div>

<ng-template #content>content here...</ng-template>
```

**Demo :**

**[Plunker](https://plnkr.co/edit/XD5vLvmwTApcaHJ66Is1)**

Details:

`<ng-template>` : is Angular’s own implementation of the `<template>` tag which is according to MDN :

`The HTML <template> element is a mechanism for holding client-side content that is not to be rendered when a page is loaded but may subsequently be instantiated during runtime using JavaScript.`

**[Source](https://stackoverflow.com/questions/43006550)**

**#18. Angular no provider for NameService**

**[M.Svrcek](https://stackoverflow.com/users/2667885/m-svrcek) asked,**

I’ve got problem with loading class into Angular component. I’m trying to solve for long time, even tried to add it to single file. What I have is:

**Application.ts**

```
/// <reference path="../typings/angular2/angular2.d.ts" />

import {Component,View,bootstrap,NgFor} from "angular2/angular2";
import {NameService} from "./services/NameService";

@Component({
    selector:'my-app',
    injectables: [NameService]
})
@View({
    template:'<h1>Hi {{name}}</h1>' +
    '<p>Friends</p>' +
    '<ul>' +
    '   <li *ng-for="#name of names">{{name}}</li>' +
    '</ul>',
    directives:[NgFor]
})

class MyAppComponent
{
    name:string;
    names:Array<string>;
    
    constructor(nameService:NameService)
    {
        this.name = 'Michal';
        this.names = nameService.getNames();
    }
}
bootstrap(MyAppComponent);
```

**services/NameService.ts**

```
export class NameService {
    names: Array<string>;
    constructor() {
        this.names = ["Alice", "Aarav", "Martín", "Shannon", "Ariana", "Kai"];
    }
    getNames()
    {
        return this.names;
    }
}
```

All the time I’m getting error message saying “No provider for NameService” …

Can someone help me spot that small issue with my code?

**[Klas Mellbourn](https://stackoverflow.com/users/46194) answered,**

You have to use `providers` instead of `injectables`

```
@Component({
    selector: 'my-app',
    providers: [NameService]
})
```

[Complete code sample here.](https://github.com/Mellbourn/angular2-step-by-step-guide)

[Source](https://stackoverflow.com/questions/30580083)

**#19. Binding select element to object in Angular**

**[RHarris](https://stackoverflow.com/users/372296/rharris) asked,**

I’m new to Angular and trying to get up to speed with the new way of doing things.

I’d like to bind a select element to a list of objects — which is easy enough:

```
@Component({
   selector: 'myApp',
   template: `<h1>My Application</h1>
              <select [(ngModel)]="selectedValue">
                 <option *ngFor="#c of countries" value="c.id">{{c.name}}</option>
              </select>`
})
export class AppComponent{
    countries = [
       {id: 1, name: "United States"},
       {id: 2, name: "Australia"}
       {id: 3, name: "Canada"}
       {id: 4, name: "Brazil"}
       {id: 5, name: "England"}
     ];
    selectedValue = null;
}
```

In this case, it appears that selectedValue would be a number — the id of the selected item.

However, I’d actually like to bind to the country object itself so that selectedValue is the object rather than just the id. I tried changing the value of the option like so:

`<option *ngFor="#c of countries" value="c">{{c.name}}<;/option>`

but this does not seem to work. It seems to place an object in my selectedValue — but not the object that I’m expecting. You can [see this in my Plunker example](http://plnkr.co/edit/HGRGv33EFwxDsSnELofk?p=preview).

I also tried binding to the change event so that I could set the object myself based on the selected id; however, it appears that the change event fires before the bound ngModel is updated — meaning I don’t have access to the newly selected value at that point.

Is there a clean way to bind a select element to an object with Angular 2?

**[Günter Zöchbauer](https://stackoverflow.com/users/217408) answered,**

```
<h1>My Application</h1>
<select [(ngModel)]="selectedValue">
  <option *ngFor="let c of countries" [ngValue]="c">{{c.name}}</option>
</select>
```

**[Plunker example](https://plnkr.co/edit/njGlIV?p=preview)**

NOTE: you can use `[ngValue]="c"` instead of `[ngValue]="c.id"` where c is the complete country object.

`[value]="..."` only supports string values
`[ngValue]="..."` supports any type

**update**

If the `value` is an object, the preselected instance needs to be identical with one of the values.

See also the recently added custom comparison [https://github.com/angular/angular/issues/13268](https://github.com/angular/angular/issues/13268) available since 4.0.0-beta.7

`<select [compareWith]="compareFn" ...`

Take care of if you want to access `this` within `compareFn`.

```
compareFn = this._compareFn.bind(this);

// or 
// compareFn = (a, b) => this._compareFn(a, b);

_comareFn((a, b) {
   if(this.x ...) {
     ...
}
```

[Source](https://stackoverflow.com/questions/35945001)

**#20. What is difference between declarations, providers and import in NgModule**

**[Ramesh Papaganti](https://stackoverflow.com/users/2822252/ramesh-papaganti) asked,**

I am trying to understand Angular (sometimes called Angular2+), then I came across @Module

1. Imports
2. Declarations
3. Providers

Following [Angularjs-2 quick start](https://angular.io/guide/quickstart)

**[Günter Zöchbauer](https://stackoverflow.com/users/217408) answered,**

**Angular Concepts**

* `imports` makes the exported declarations of other modules available in the current module
* `declarations` are to make directives (including components and pipes) from the current module available to other directives in the current module. Selectors of directives, components or pipes are only matched against the HTML if they are declared or imported.
* `providers` are to make services and values known to DI. They are added to the root scope and they are injected to other services or directives that have them as dependency.

A special case for `providers` are lazy loaded modules that get their own child injector. `providers` of a lazy loaded module are only provided to this lazy loaded module by default (not the whole application as it is with other modules).

For more details about modules see also [https://angular.io/docs/ts/latest/guide/ngmodule.html](https://angular.io/docs/ts/latest/guide/ngmodule.html)

* `exports` makes the components, directives, and pipes available in modules that add this module to `imports`. `exports` can also be used to re-export modules such as CommonModule and FormsModule, which is often done in shared modules.
* `entryComponents` registers components for offline compilation so that they can be used with `ViewContainerRef.createComponent()`. Components used in router configurations are added implicitly.

**TypeScript (ES2015) imports**

`import ... from 'foo/bar'` (which [may resolve to an `index.ts`](https://stackoverflow.com/a/38158884/1175496)) are for TypeScript imports. You need these whenever you use an identifier in a typescript file that is declared in another typescript file.

Angular’s `@NgModule()` `imports` and TypeScript `import` are entirely different concepts.

See also [jDriven — TypeScript and ES6 import syntax](https://blog.jdriven.com/2017/06/typescript-and-es6-import-syntax/)

`Most of them are actually plain ECMAScript 2015 (ES6) module syntax that TypeScript uses as well.`

**[Source](https://stackoverflow.com/questions/39062930)**

**#21. In Angular, how do you determine the active route?**

**[Michael Oryl](https://stackoverflow.com/users/1480995/michael-oryl) asked,**

**NOTE:** There are many different answers here, and most have been valid at one time or another. The fact is that what works has changed a number of times as the Angular team has changed its Router. The Router 3.0 version that will eventually be **the** router in Angular breaks many of these solutions, but offers a very simple solution of its own. As of RC.3, the preferred solution is to use `[routerLinkActive]` as shown in [this answer](https://stackoverflow.com/a/37947435/1480995).

In an Angular application (current in the 2.0.0-beta.0 release as I write this), how do you determine what the currently active route is?

I’m working on an app that uses Bootstrap 4 and I need a way to mark navigation links/buttons as active when their associated component is being shown in a `<router-output>` tag.

I realize that I could maintain the state myself when one of the buttons is clicked upon, but that wouldn’t cover the case of having multiple paths into the same route (say a main navigation menu as well as a local menu in the main component).

Any suggestions or links would be appreciated. Thanks.

**[jessepinho](https://stackoverflow.com/users/974981) answered,**

With the new [Angular router](https://github.com/angular/vladivostok), you can add a `[routerLinkActive]="['your-class-name']"` attribute to all your links:

`<a [routerLink]="['/home']" [routerLinkActive]="['is-active']">Home</a>`

Or the simplified non-array format if only one class is needed:

`<a [routerLink]="['/home']" [routerLinkActive]="'is-active'">Home</a>`

See the [poorly documented `routerLinkActive` directive](https://github.com/angular/angular/blob/ae75e3640a2d9eb1e897a0771d92b976c5a42c75/modules/%40angular/router/src/directives/router_link_active.ts) for more info. (I mostly figured this out via trial-and-error.)

UPDATE: Better documentation for the `routerLinkActive` directive can now be found [here](https://angular.io/docs/ts/latest/api/router/index/RouterLinkActive-directive.html). (Thanks to @Victor Hugo Arango A. in the comments below.)

**[Source](https://stackoverflow.com/questions/34323480)**

**#22. Angular CLI SASS options**

**[JDillon522](https://stackoverflow.com/users/2109585/jdillon522) asked,**

I’m new to Angular and I’m coming from the Ember community. Trying to use the new Angular-CLI based off of Ember-CLI.

I need to know the best way to handle SASS in a new Angular project. I tried using the `ember-cli-sass` repo to see if it would play along since a number of core components of the Angular-CLI are run off of Ember-CLI modules.

It didnt work but than again not sure if I just misconfigured something.

Also, what is the best way to organize styles in a new Angular project? It would be nice to have the sass file in the same folder as the component.

**[Mertcan Diken](https://stackoverflow.com/users/6265549) answered,**

When you are creating your project with angular cli try this:

`ng new My_New_Project --style=sass`

This generating all your components with predifined sass files.

If you want scss syntax create your project with :

`ng new My_New_Project --style=scss`

If you are changing your existing style in your project

`ng set defaults.styleExt scss`

Cli handles the rest of it.

**[Source](https://stackoverflow.com/questions/36220256)**

**#23. Triggering change detection manually in Angular**

**[jz87](https://stackoverflow.com/users/515279/jz87) asked,**

I’m writing an Angular component that has a property `Mode(): string`. I would like to be able to set this property programmatically not in response to any event. The problem is that in the absence of a browser event, a template binding `{{Mode}}` doesn't update. Is there a way to trigger this change detection manually?

**[Mark Rajcok](https://stackoverflow.com/users/215945) answered,**

Try one of these:

* `[ApplicationRef.tick()](https://angular.io/docs/ts/latest/api/core/index/ApplicationRef-class.html#!#tick-anchor)` - similar to AngularJS's `$rootScope.$digest()` -- i.e., check the full component tree
* `[NgZone.run(callback)](https://angular.io/docs/ts/latest/api/core/index/NgZone-class.html#!#run-anchor)` - similar to `$rootScope.$apply(callback)` -- i.e., evaluate the callback function inside the Angular zone. I think, but I'm not sure, that this ends up checking the full component tree after executing the callback function.
* `[ChangeDetectorRef.detectChanges()](https://angular.io/docs/ts/latest/api/core/index/ChangeDetectorRef-class.html#!#detectChanges-anchor)` - similar to `$scope.$digest()` -- i.e., check only this component and its children

You can inject `ApplicationRef`, `NgZone`, or `ChangeDetectorRef` into your component.

**[Source](https://stackoverflow.com/questions/34827334)**

**#24. Angular and Typescript: Can’t find names**

**[user233232](https://stackoverflow.com/users/4997649/user233232) asked,**

I am using Angular (version 2) with TypeScript (version 1.6) and when I compile the code I get these errors:

```
Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/change_detection/parser/locals.d.ts(4,42): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(1,25): Error TS2304: Cannot find name 'MapConstructor'.
    node_modules/angular2/src/core/facade/collection.d.ts(2,25): Error TS2304: Cannot find name 'SetConstructor'.
    node_modules/angular2/src/core/facade/collection.d.ts(4,27): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(4,39): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(7,9): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(8,30): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(11,43): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(12,27): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(14,23): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(15,25): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/collection.d.ts(94,41): Error TS2304: Cannot find name 'Set'.
    node_modules/angular2/src/core/facade/collection.d.ts(95,22): Error TS2304: Cannot find name 'Set'.
    node_modules/angular2/src/core/facade/collection.d.ts(96,25): Error TS2304: Cannot find name 'Set'.
    node_modules/angular2/src/core/facade/lang.d.ts(1,22): Error TS2304: Cannot find name 'BrowserNodeGlobal'.
    node_modules/angular2/src/core/facade/lang.d.ts(33,59): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/facade/promise.d.ts(1,10): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(3,14): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(8,32): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(9,38): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(10,35): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(10,93): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(11,34): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(12,32): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(12,149): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/facade/promise.d.ts(13,43): Error TS2304: Cannot find name 'Promise'.
    node_modules/angular2/src/core/linker/element_injector.d.ts(72,32): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/element_injector.d.ts(74,17): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/element_injector.d.ts(78,184): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/element_injector.d.ts(83,182): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/element_injector.d.ts(107,37): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/proto_view_factory.d.ts(27,146): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/view.d.ts(52,144): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/view.d.ts(76,79): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/view.d.ts(77,73): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/view.d.ts(94,31): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/view.d.ts(97,18): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/view.d.ts(100,24): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/view.d.ts(103,142): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/linker/view.d.ts(104,160): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/render/api.d.ts(281,74): Error TS2304: Cannot find name 'Map'.
    node_modules/angular2/src/core/zone/ng_zone.d.ts(1,37): Error TS2304: Cannot find name 'Zone'.
```

This is the code:

```
import 'reflect-metadata';
import {bootstrap, Component, CORE_DIRECTIVES, FORM_DIRECTIVES} from 'angular2/core';
@Component({
  selector: 'my-app',
  template: '<input type="text" [(ng-model)]="title" /><h1>{{title}}</h1>',
  directives: [ CORE_DIRECTIVES ]
})
class AppComponent {
  title :string;
  
  constructor() {
    this.title = 'hello angular 2';
  }
}
bootstrap(AppComponent);
```

**[basarat](https://stackoverflow.com/users/390330) answered,**

A known issue: [https://github.com/angular/angular/issues/4902](https://github.com/angular/angular/issues/4902)

Core reason: the `.d.ts` file implicitly included by TypeScript varies with the compile target, so one needs to have more ambient declarations when targeting `es5` even if things are actually present in the runtimes (e.g. chrome). More on `lib.d.ts`

**[Source](https://stackoverflow.com/questions/33332394)**