---
title: Answers on StackOverflow to the most popular Angular questions (Part 1)
image: "/assets/default-social-image.png"
categories: Angular
---

**48 answers on StackOverflow to the most popular Angular questions (Part 1/4)**

This gathered list is the most common questions and answers from **Stackoverflow**. These questions were chosen by the highest score received. Whether you are an expert or a beginner, you can learn from others’ experiences.

**Table of Contents**

#1. Angular — Promise vs Observable

#2. Difference between Constructor and ngOnInit

#3. Can’t bind to ‘ngModel’ since it isn’t a known property of ‘input’

#4. Angular HTML binding

#5. Angular/RxJs When should I unsubscribe from 'Subscription'

#6. How can I select an element in a component template?

#7. What is the equivalent of ngShow and ngHide in Angular?

#8. How to bundle an Angular app for production

#9. BehaviorSubject vs Observable?

#10. @Directive v/s @Component in Angular

#11. Angular HTTP GET with TypeScript error http.get(…).map is not a function in [null]

#12. How to use jQuery with Angular?

**Enjoy!**

**#1. Angular — Promise vs Observable**

**[Rohit](https://stackoverflow.com/users/6364715/rohit) asked,**

Can someone please explain the difference between `Promise` and `Observable` in Angular?

An example on each would be helpful in understanding both the cases. In what scenario can we use each case?

**[Günter Zöchbauer](https://stackoverflow.com/users/217408) answered,**

**Promise**

A `Promise` handles a single event when an async operation completes or fails.

Note: There are `Promise` libraries out there that support cancellation, but ES6 `Promise` doesn't so far.

**Observable**

An `Observable` is like a **`Stream`** (in many languages) and allows to pass zero or more events where the callback is called for each event.

Often `Observable` is preferred over `Promise` because it provides the features of `Promise` and more. With `Observable` it doesn't matter if you want to handle 0, 1, or multiple events. You can utilize the same API in each case.

`Observable` also has the advantage over `Promise` to be **cancelable**. If the result of an HTTP request to a server or some other expensive async operation isn't needed anymore, the `Subscription` of an `Observable` allows to cancel the subscription, while a `Promise` will eventually call the success or failed callback even when you don't need the notification or the result it provides anymore.

Observable provides **operators** like `map`, `forEach`, `reduce`, ... similar to an array

There are also powerful operators like `retry()`, or `replay()`, ... that are often quite handy.

**[Source](https://stackoverflow.com/questions/37364973)**

**#2. Difference between Constructor and ngOnInit**

**[Haseena P A](https://stackoverflow.com/users/4029338) asked,**

Angular provides lifecycle hook `ngOnInit` by default.

Why should `ngOnInit` be used, if we already have a `constructor`?

**[Pardeep Jain](https://stackoverflow.com/users/5043867) answered,**

The `Constructor` is a default method of the class that is executed when the class is instantiated and ensures proper initialization of fields in the class and its subclasses. Angular or better Dependency Injector (DI) analyzes the constructor parameters and when it creates a new instance by calling `new MyClass()` it tries to find providers that match the types of the constructor parameters, resolves them and passes them to the constructor like

`new MyClass(someArg);`

`ngOnInit` is a lifecycle hook called by Angular2 to indicate that Angular is done creating the component.

We have to import `OnInit` in order to use like this (actually implementing OnInit is not mandatory but considered good practice):

`import {Component, OnInit} from '@angular/core';`

then to use the method of OnInit we have to implement in the class like this.

```
export class App implements OnInit{
  constructor(){
     //called first time before the ngOnInit()
  }
  
  ngOnInit(){
     //called after the constructor and called  after the first ngOnChanges() 
  }
}
```

`Implement this interface to execute custom initialization logic after your directive's data-bound properties have been initialized. ngOnInit is called right after the directive's data-bound properties have been checked for the first time, and before any of its children have been checked. It is invoked only once when the directive is instantiated.`

Mostly we use `ngOnInit` for all the initialization/declaration and avoid stuff to work in the constructor. The constructor should only be used to initialize class members but shouldn't do actual "work".

So you should use `constructor()` to setup Dependency Injection and not much else. ngOnInit() is better place to "start" - it's where/when components' bindings are resolved.

For more information refer here:

* [https://angular.io/api/core/OnInit](https://angular.io/api/core/OnInit)
* [Angular 2 Component Constructor Vs OnInit](https://stackoverflow.com/a/35846307/5043867)

**[Source](https://stackoverflow.com/questions/35763730)**

**#3. Can’t bind to ‘ngModel’ since it isn’t a known property of ‘input’**

**[abreneliere](https://stackoverflow.com/users/3433751/anthony-breneli%C3%A8re) asked,**

I’ve got the following error when launching my Angular app, even if the component is not displayed.

I have to comment out the so that my app works.

```
zone.js:461 Unhandled Promise rejection: Template parse errors:
Can't bind to 'ngModel' since it isn't a known property of 'input'. ("
    <div>
        <label>Created:</label>
        <input  type="text" [ERROR ->][(ngModel)]="test" placeholder="foo" />
    </div>
</div>"): InterventionDetails@4:28 ; Zone: <root> ; Task: Promise.then ; Value:
```

I’m looking at the Hero plucker but I don’t see any difference.

Here is the component file:

```
import { Component, EventEmitter, Input, OnInit, Output } from '@angular/core';
import { Intervention } from '../../model/intervention';

@Component({
    selector: 'intervention-details',
    templateUrl: 'app/intervention/details/intervention.details.html',
    styleUrls: ['app/intervention/details/intervention.details.css']
})

export class InterventionDetails
{
    @Input() intervention: Intervention;
    public test : string = "toto";
}
```

**[abreneliere](https://stackoverflow.com/users/3433751) answered,**

Yes that’s it, in the app.module.ts, I just added :

```
import { FormsModule } from '@angular/forms';

[...]

@NgModule({
  imports: [
    [...]
    FormsModule
  ],
  [...]
})
```

**[Source](https://stackoverflow.com/questions/38892771)**

**#4. Angular HTML binding**

**[Aviad P.](https://stackoverflow.com/users/3433751/anthony-breneli%C3%A8re) asked,**

I am writing an Angular application, and I have an HTML response I want to display. How do I do that? If I simply use the binding syntax `{{myVal}}` it encodes all HTML characters (of course).

I need somehow to bind the inner html of a div to the variable value.

**[prolink007](https://stackoverflow.com/users/427763) answered,**

The correct syntax is now the following:

`<div [innerHTML]="theHtmlString"></div>`

Working in `5.2.6`

[Documentation Reference](https://angular.io/docs/ts/latest/guide/template-syntax.html#!#property-binding-or-interpolation-)

[Source](https://stackoverflow.com/questions/31548311)

**#5. Angular/RxJs When should I unsubscribe from 'Subscription'**

**[Sergey Tihon](https://stackoverflow.com/users/1429493) asked,**

When should I store the `Subscription` instances and invoke `unsubscribe()` during the NgOnDestroy lifecycle and when can I simply ignore them?

Saving all subscriptions introduces a lot of mess into component code.

[HTTP Client Guide](https://angular.io/docs/ts/latest/guide/server-communication.html) ignore subscriptions like this:

```
getHeroes() {
  this.heroService.getHeroes()
                   .subscribe(
                     heroes => this.heroes = heroes,
                     error =>  this.errorMessage = <any>error);
}
```

In the same time Route & Navigation Guide says that:

```
Eventually, we'll navigate somewhere else. The router will remove this component from the DOM and destroy it. We need to clean up after ourselves before that happens. Specifically, we must unsubscribe before Angular destroys the component. Failure to do so could create a memory leak.

We unsubscribe from our Observable in the ngOnDestroy method.
```

```
private sub: any;

ngOnInit() {
  this.sub = this.route.params.subscribe(params => {
     let id = +params['id']; // (+) converts string 'id' to a number
     this.service.getHero(id).then(hero => this.hero = hero);
   });
}

ngOnDestroy() {
  this.sub.unsubscribe();
}
```

**[seangwright](https://stackoverflow.com/users/939634) answered,**

**— — Edit 3 — The ‘Official’ Solution (2017/04/09)**

I spoke with Ward Bell about this question at NGConf (I even showed him this answer which he said was correct) but he told me the docs team for Angular had a solution to this question that is unpublished (though they are working on getting it approved). He also told me I could update my SO answer with the forthcoming official recommendation.

The solution we should all use going forward is to add a `private ngUnsubscribe: Subject = new Subject();` field to all components that have `.subscribe()` calls to `Observable`s within their class code.

We then call `this.ngUnsubscribe.next(); this.ngUnsubscribe.complete();` in our `ngOnDestroy()` methods.

The secret sauce (as noted already by @metamaker) is to call `.takeUntil(this.ngUnsubscribe)` before each of our `.subscribe()` calls which will guarantee all subscriptions will be cleaned up when the component is destroyed.

Example:

```
import { Component, OnDestroy, OnInit } from '@angular/core';
import 'rxjs/add/operator/takeUntil';
// import { takeUntil } from 'rxjs/operators'; // for rxjs ^5.5.0 lettable operators
import { Subject } from 'rxjs/Subject';

import { MyThingService } from '../my-thing.service';

@Component({
    selector: 'my-thing',
    templateUrl: './my-thing.component.html'
})
export class MyThingComponent implements OnDestroy, OnInit {
    private ngUnsubscribe: Subject = new Subject();
    
    constructor(
        private myThingService: MyThingService,
    ) { }
    
    ngOnInit() {
        this.myThingService.getThings()
            .takeUntil(this.ngUnsubscribe)
            .subscribe(things => console.log(things));
            
        /* if using lettable operators in rxjs ^5.5.0
        this.myThingService.getThings()
            .pipe(takeUntil(this.ngUnsubscribe))
            .subscribe(things => console.log(things));
        */
        
        this.myThingService.getOtherThings()
            .takeUntil(this.ngUnsubscribe)
            .subscribe(things => console.log(things));
            
    }
    
    ngOnDestroy() {
        this.ngUnsubscribe.next();
        this.ngUnsubscribe.complete();
    }
}
```

**— — Edit 2 (2016/12/28)**

**Source 5**

The Angular tutorial, the Routing chapter now states the following: “The Router manages the observables it provides and localizes the subscriptions. The subscriptions are cleaned up when the component is destroyed, protecting against memory leaks, so we don’t need to unsubscribe from the route params Observable.” — [Mark Rajcok](https://stackoverflow.com/questions/38008334/angular2-rxjs-when-should-i-unsubscribe-from-subscription/41177163?noredirect=1#comment69909721_41177163)

Here’s a [discussion](https://github.com/angular/angular.io/issues/3003#issuecomment-268429065) on the Github issues for the Angular docs regarding Router Observables where Ward Bell mentions that clarification for all of this is in the works.

**— — Edit 1**

**Source 4**

In this [video from NgEurope](https://youtu.be/WWR9nxVx1ec?t=20m32s) Rob Wormald also says you do not need to unsubscribe from Router Observables. He also mentions the `http` service and `ActivatedRoute.params` in this [video from November 2016](https://youtu.be/VLGCCpOWFFw?t=33m37s).

**— — Original Answer**

**TLDR:**

For this question there are (2) kinds of `Observables` - **finite** value and **infinite** value.

`http` `Observables` produce **finite** (1) values and something like a DOM `event listener Observables` produce `infinite` values.

If you manually call `subscribe` (not using async pipe), then `unsubscribe` from **infinite** `Observables`.

Don’t worry about **finite** ones, `RxJs` will take care of them.

**Source 1**

I tracked down an answer from Rob Wormald in Angular’s Gitter here.

He states (i reorganized for clarity and emphasis is mine)

`if it's a **single-value-sequence** (like an http request) the **manual cleanup is unnecessary** (assuming you subscribe in the controller manually)`

`i should say "if it's a **sequence that completes**" (of which single value sequences, a la http, are one)`

`**if it's an infinite sequence, you should unsubscribe** which the async pipe does for you`

Also he mentions in this [youtube video](https://youtu.be/UHI0AzD_WfY?t=26m42s) on Observables that `they clean up after themselves`... in the context of Observables that `complete` (like Promises, which always complete because they are always producing 1 value and ending - we never worried about unsubscribing from Promises to make sure they clean up `xhr` event listeners, right?).

**Source 2**

Also in the [Rangle guide to Angular 2 ](https://angular-2-training-book.rangle.io/handout/observables/disposing_subscriptions_and_releasing_resources.html)it reads

`In most cases we will not need to explicitly call the unsubscribe method unless we want to cancel early or our Observable has a longer lifespan than our subscription. The default behavior of Observable operators is to dispose of the subscription as soon as .complete() or .error() messages are published. Keep in mind that RxJS was designed to be used in a "fire and forget" fashion most of the time.`

When does the phrase `our Observable has a longer lifespan than our subscription` apply?

It applies when a subscription is created inside a component which is destroyed before (or not ‘long’ before) the `Observable` completes.

I read this as meaning if we subscribe to an `http` request or an observable that emits 10 values and our component is destroyed before that `http` request returns or the 10 values have been emitted, we are still ok!

When the request does return or the 10th value is finally emitted the `Observable` will complete and all resources will be cleaned up.

**Source 3**

If we look at [this example](https://angular-2-training-book.rangle.io/handout/routing/routeparams.html) from the same Rangle guide we can see that the `Subscription` to `route.params` does require an `unsubscribe()` because we don't know when those `params` will stop changing (emitting new values).

The component could be destroyed by navigating away in which case the route params will likely still be changing (they could technically change until the app ends) and the resources allocated in subscription would still be allocated because there hasn’t been a `completion`.

**[Source](https://stackoverflow.com/questions/38008334)**

**#6. How can I select an element in a component template?**

**[Aman Gupta](https://stackoverflow.com/users/2748475/aman-gupta) asked,**

Does anybody know how to get hold of an element defined in a component template? Polymer makes it really easy with the `$` and `$$`.

I was just wondering how to go about it in Angular.

Take the example from the tutorial:

```
import {Component} from '@angular/core'

@Component({
    selector:'display'
    template:`
     <input #myname(input)="updateName(myname.value)"/>
     <p>My name : {{myName}}</p>
    `
    
})
export class DisplayComponent {
    myName: string = "Aman";
    updateName(input: String) {
        this.myName = input;
    }
}
```

How do I catch hold of a reference of the `p` or `input` element from within the class definition?

**[Brocco](https://stackoverflow.com/users/1413538) answered,**

You can get a handle to the DOM element via `ElementRef` by injecting it into your component's constructor:

`constructor(myElement: ElementRef) { ... }`
Docs: https://angular.io/docs/ts/latest/api/core/index/ElementRef-class.html

**[Source](https://stackoverflow.com/questions/32693061)**

**#7. What is the equivalent of ngShow and ngHide in Angular?**

**[Mihai Răducanu](https://stackoverflow.com/users/2870735/mihai-r%C4%83ducanu) asked,**

I have a number of elements that I want to be visible under certain conditions.

In AngularJS I would write

`<div ng-show="myVar">stuff</div>`

How can I do this in Angular?

**[Günter Zöchbauer](https://stackoverflow.com/users/217408) answered,**

Just bind to the `hidden` property

`[hidden]="!myVar"`

See also

[https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/hidden](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/hidden)

**issues**

`hidden` has some issues though because it can conflict with CSS for the `display` property.

See how `some` in **[Plunker example](https://plnkr.co/edit/SO3c3UUT3LBvhNAeriCz?p=preview)** doesn't get hidden because it has a style

`:host {display: block;}`

set. (This might behave differently in other browsers — I tested with Chrome 50)

**workaround**

You can fix it by adding

`[hidden] { display: none !important;}`

To a global style in `index.html`.

**another pitfall**

```
hidden="false"
hidden="{{false}}"
hidden="{{isHidden}}" // isHidden = false;
```
are the same as

`hidden="true"`

and will not show the element.

`hidden="false"` will assign the string `"false"` which is considered truthy.

Only the value `false` or removing the attribute will actually make the element visible.

Using `{{}}` also converts the expression to a string and won't work as expected.

Only binding with `[]` will work as expected because this `false` is assigned as false instead of `"false"`.

**`*ngIf`** vs **`[hidden]`**

`*ngIf` effectively removes its content from the DOM while `[hidden]` modifies the `display` property and only instructs the browser to not show the content but the DOM still contains it.

**[Source](https://stackoverflow.com/questions/35578083)**

**#8. How to bundle an Angular app for production**

**[Pat M](https://stackoverflow.com/users/4155124) asked,**

I would like to track and update in this thread the latest best (and hopefully the simplest) method to bundle Angular (version 2, 4, …) for production on a live web server.

Please include the Angular version within answers so we can track better when it moves to later releases.

**[Nicolas Henneaux](https://stackoverflow.com/users/1630604) answered,**

`2.x, 4.x, 5.x` **(TypeScript) with Angular CLI**

**OneTime Setup**

* `npm install -g @angular/cli`
* `ng new projectFolder` creates a new application

**Bundling Step**

* `ng build --prod` (run in command line when directory is `projectFolder`)
* flag `prod` bundle for production (see the [Angular documentation](https://github.com/angular/angular-cli/wiki/build#--dev-vs---prod-builds) for the list of option included with the production flag).
* Compress using [Brotli compression](https://en.wikipedia.org/wiki/Brotli) the resources using the following command `for i in dist/*; do brotli $i; done`

bundles are generated by default to projectFolder/dist/

**Output**

Sizes with Angular `5.2.8` with CLI `1.7.2`

* `dist/main.[hash].bundle.js` Your application bundled [ size: 151 KB for new Angular CLI application empty, **36 KB** compressed].
* `dist/polyfill.[hash].bundle.js` the polyfill dependencies (@angular, RxJS...) bundled [ size: 58 KB for new Angular CLI application empty, **17 KB** compressed].
* `dist/index.html` entry point of your application.
* `dist/inline.[hash].bundle.js` webpack loader
* `dist/style.[hash].bundle.css` the style definitions
* `dist/assets` resources copied from the Angular CLI assets configuration

**Deployment**

You can get a preview of your application using the `ng serve --prod` command that starts a local HTTP server such that the application with production files is accessible using [http://localhost:4200](http://localhost:4200/).

For a production usage, you have to deploy all the files from the `dist` folder in the HTTP server of your choice.

**[Source](https://stackoverflow.com/questions/37631098)**

**#9. BehaviorSubject vs Observable?**

**[Kevin Mark](https://stackoverflow.com/users/6620551/kevin-mark) asked,**

I’m looking into Angular RxJs patterns and I don’t understand the difference between a BehaviorSubject and an Observable.

From my understanding, a BehaviorSubject is a value that can change over time (can be subscribed to and subscribers can receive updated results). This seems to be the exact same purpose of an Observable.

When would you use an Observable vs a BehaviorSubject? Are there benefits to using a BehaviorSubject over an Observable or vice versa?

**[Shantanu Bhadoria](https://stackoverflow.com/users/3070452) answered,**

BehaviorSubject is a type of subject, a subject is a special type of observable so you can subscribe to messages like any other observable. The unique features of BehaviorSubject are:

* It needs an initial value as it must always return a value on subscription even if it hasn’t received a `next()`
* Upon subscription it returns the last value of the subject. A regular observable only triggers when it receives an `onnext`
* at any point you can retrieve the last value of the subject in a non-observable code using the `getValue()` method.

Unique features of a subject compared to an observable are:

* It is an observer in addition to being an observable so you can also send values to a subject in addition to subscribing to it.

In addition you can get an observable from behavior subject using the `asobservable()` method on BehaviorSubject.

Observable is a Generic, and BehaviorSubject is technically a sub-type of Observable because BehaviorSubject is an observable with specific qualities.

Example with BehaviorSubject:

```
// Behavior Subject

// a is an initial value. if there is a subscription 
// after this, it would get "a" value immediately
let bSubject = new BehaviorSubject("a"); 

bSubject.next("b");

bSubject.subscribe((value) => {
  console.log("Subscription got", value); // Subscription got b, 
                                          // ^ This would not happen 
                                          // for a generic observable 
                                          // or generic subject by default
});

bSubject.next("c"); // Subscription got c
bSubject.next("d"); // Subscription got d
```

Example 2 with regular subject:

```
// Regular Subject

let subject = new Subject(); 

subject.next("b");

subject.subscribe((value) => {
  console.log("Subscription got", value); // Subscription wont get 
                                          // anything at this point
});

subject.next("c"); // Subscription got c
subject.next("d"); // Subscription got d
```

An observable can be created from both Subject and BehaviorSubject using `subject.asobservable()`. Only difference being you can't send values to an observable using `next()` method.

In Angular services, I would use BehaviorSubject for a data service as a angular service often initializes before component and behavior subject ensures that the component consuming the service receives the last updated data even if there are no new updates since the component’s subscription to this data.

**[Source](https://stackoverflow.com/questions/39494058)**

**#10. @Directive v/s @Component in Angular**

**[Prasanjit Dey](https://stackoverflow.com/users/4917853/prasanjit-dey) asked,**

What is the difference between `@Component` and `@Directive` in Angular? Both of them seem to do the same task and have the same attributes.

What are the use cases and when to prefer one over another?

**[jaker](https://stackoverflow.com/users/1771017) answered,**

A @Component requires a view whereas a @Directive does not.

**Directives**

I liken a @Directive to an Angular 1.0 directive with the option `restrict: 'A'` (Directives aren't limited to attribute usage.) Directives add behaviour to an existing DOM element or an existing component instance. One example use case for a directive would be to log a click on an element.

```
import {Directive} from '@angular/core';

@Directive({
    selector: "[logOnClick]",
    hostListeners: {
        'click': 'onClick()',
    },
})

class LogOnClick {
    constructor() {}
    onClick() { console.log('Element clicked!'); }
}
```

Which would be used like so:

`<button logOnClick>I log when clicked!<;/button>`

**Components**

A component, rather than adding/modifying behaviour, actually creates its own view (hierarchy of DOM elements) with attached behaviour. An example use case for this might be a contact card component:

```
import {Component, View} from '@angular/core';

@Component({
  selector: 'contact-card',
  template: `
    <div>
      <h1>{{name}}</h1>
      <p>{{city}}</p>
    </div>
  `
})
class ContactCard {
  @Input() name: string
  @Input() city: string
  constructor() {}
}
```

Which would be used like so:

`<contact-card [name]="'foo'" [city]="'bar'"></contact-card>`

`ContactCard` is a reusable UI component that we could use anywhere in our application, even within other components. These basically make up the UI building blocks of our applications.

**In summary**

Write a component when you want to create a reusable set of DOM elements of UI with custom behaviour. Write a directive when you want to write reusable behaviour to supplement existing DOM elements.

Sources:

* [@Directive documentation](https://angular.io/api/core/Directive)
* [@Component documentation](https://angular.io/api/core/Component)
* [Helpful blog post](http://blog.codeleak.pl/2015/06/angular2hello-world.html)

[Source](https://stackoverflow.com/questions/32680244)

**#11. Angular HTTP GET with TypeScript error http.get(…).map is not a function in [null]**

**[Claudiu](https://stackoverflow.com/users/4834129/claudiu) asked,**

I have a problem with HTTP in Angular.

I just want to `GET` a `JSON` list and show it in the view.

**Service class**

```
import {Injectable} from "angular2/core";
import {Hall} from "./hall";
import {Http} from "angular2/http";
@Injectable()
export class HallService {
    public http:Http;
    public static PATH:string = 'app/backend/' 
    
    constructor(http:Http) {
        this.http=http;
    }
    
    getHalls() {
           return this.http.get(HallService.PATH + 'hall.json').map((res:Response) => res.json());
    }
}
```

And in the `HallListComponent` I call the `getHalls` method from the service:

```
export class HallListComponent implements OnInit {
    public halls:Hall[];
    public _selectedId:number;
    
    constructor(private _router:Router,
                private _routeParams:RouteParams,
                private _service:HallService) {
        this._selectedId = +_routeParams.get('id');
    }
    
    ngOnInit() {
        this._service.getHalls().subscribe((halls:Hall[])=>{ 
            this.halls=halls;
        });
    }
}
```

However, I got an exception:

`TypeError: this.http.get(...).map is not a function in [null]`

**hall-center.component**

```
import {Component} from "angular2/core";
import {RouterOutlet} from "angular2/router";
import {HallService} from "./hall.service";
import {RouteConfig} from "angular2/router";
import {HallListComponent} from "./hall-list.component";
import {HallDetailComponent} from "./hall-detail.component";
@Component({
    template:`
        <h2>my app</h2>
        <router-outlet></router-outlet>
    `,
    directives: [RouterOutlet],
    providers: [HallService]
})

@RouteConfig([
    {path: '/',         name: 'HallCenter', component:HallListComponent, useAsDefault:true},
    {path: '/hall-list', name: 'HallList', component:HallListComponent}
])

export class HallCenterComponent{}
```

**app.component**

```
import {Component} from 'angular2/core';
import {ROUTER_DIRECTIVES} from "angular2/router";
import {RouteConfig} from "angular2/router";
import {HallCenterComponent} from "./hall/hall-center.component";
@Component({
    selector: 'my-app',
    template: `
        <h1>Examenopdracht Factory</h1>
        <a [routerLink]="['HallCenter']">Hall overview</a>
        <router-outlet></router-outlet>
    `,
    directives: [ROUTER_DIRECTIVES]
})

@RouteConfig([
    {path: '/hall-center/...', name:'HallCenter',component:HallCenterComponent,useAsDefault:true}
])
export class AppComponent { }
```

**tsconfig.json**

{
  "compilerOptions": {
    "target": "ES5",
    "module": "system",
    "moduleResolution": "node",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "removeComments": false,
    "noImplicitAny": false
  },
  "exclude": [
    "node_modules"
  ]
}

**[Thierry Templier](https://stackoverflow.com/users/1873365) answered,**

I think that you need to import this:

`import 'rxjs/add/operator/map'`

Or more generally this if you want to have more methods for observables. **WARNING: This will import all 50+ operators and add them to your application, thus affecting your bundle size and load times.**

`import 'rxjs/Rx';`

See [this issue](https://github.com/angular/angular/issues/5632#issuecomment-167026172) for more details.

**[Source](https://stackoverflow.com/questions/34515173)**

**#12. How to use jQuery with Angular?**

**[Waog](https://stackoverflow.com/users/2398523/waog) asked,**

Can anyone tell me, how to use **jQuery** with **Angular**?

```
class MyComponent {
    constructor() {
        // how to query the DOM element from here?
    }
}
```

I’m aware there are workarounds like manipulating the class or id of the DOM element upfront, but I’m hoping for a cleaner way of doing it.

**[werenskjold](https://stackoverflow.com/users/2881743) answered,**

Using jQuery from Angular2 is a breeze compared to ng1. If you are using TypeScript you could first reference jQuery typescript definition.

```
tsd install jquery --save
or
typings install dt~jquery --global --save
```

TypescriptDefinitions are not required since you could just use `any` as the type for `$` or `jQuery`

In your angular component you should reference a DOM element from the template using `@ViewChild()` After the view has been initialized you can use the `nativeElement` property of this object and pass to jQuery.

Declaring `$` (or `jQuery`) as JQueryStatic will give you a typed reference to jQuery.

```
import {bootstrap}    from '@angular/platform-browser-dynamic';
import {Component, ViewChild, ElementRef, AfterViewInit} from '@angular/core';
declare var $:JQueryStatic;

@Component({
    selector: 'ng-chosen',
    template: `<select #selectElem>
        <option *ngFor="#item of items" [value]="item" [selected]="item === selectedValue">{{item}} option</option>
        </select>
        <h4> {{selectedValue}}</h4>`
})
export class NgChosenComponent implements AfterViewInit {
    @ViewChild('selectElem') el:ElementRef;
    items = ['First', 'Second', 'Third'];
    selectedValue = 'Second';
    
    ngAfterViewInit() {
        $(this.el.nativeElement)
            .chosen()
            .on('change', (e, args) => {
                this.selectedValue = args.selected;
            });
    }
}

bootstrap(NgChosenComponent);
```

This example is available on plunker: [http://plnkr.co/edit/Nq9LnK?p=preview](http://plnkr.co/edit/Nq9LnK?p=preview)

tslint will complain about `chosen` not being a property on $, to fix this you can add a definition to the JQuery interface in your custom *.d.ts file

```
interface JQuery {
    chosen(options?:any):JQuery;
}
```

**[Source](https://stackoverflow.com/questions/30623825)**