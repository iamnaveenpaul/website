---
title: Answers on StackOverflow to the most popular Angular questions (Part 4)
image: "/assets/default-social-image.png"
categories: Angular
---

**48 answers on StackOverflow to the most popular Angular questions (Part 4/4)**

This gathered list is the most common questions and answers from **Stackoverflow**. These questions were chosen by the highest score received. Whether you are an expert or a beginner, you can learn from others’ experiences.

**Table of Contents**

#37. How do you deploy Angular apps?

#38. ngFor with index as value in attribute

#39. Define global constants in Angular 2

#40. Angular — Use pipes in services and components

#41. Angular2 Exception: Can’t bind to ‘routerLink’ since it isn’t a known native property

#42. Angular 2 dynamic tabs with user-click chosen components

#43. Delegation: EventEmitter or Observable in Angular

#44. How to add bootstrap to an angular-cli project

#45. access key and value of object using `*ngFor`

#46. Angular exception: Can’t bind to ‘ngFor’ since it isn’t a known native property

#47. How to add font-awesome to Angular 2 + CLI project

#48. Difference between HTTP and HTTPClient in angular 4?

**Enjoy!**

**#37. How do you deploy Angular apps?**

**[Joseph Assem Sobhy](https://stackoverflow.com/users/1362355/joseph-girgis) asked,**

How do you deploy Angular apps once they reach the production phase?

All the guides I’ve seen so far (even on [angular.io](https://angular.io/)) are counting on a lite-server for serving and browserSync to reflect changes — but when you finish with development, how can you publish the app?

Do I import all the compiled `.js` files on the `index.html` page or do I minify them using gulp? Will they work? Do I need SystemJS at all in the production version?

**[Amid](https://stackoverflow.com/users/1035889) answered,**

You are actually here touching two questions in one. First one is how to host your application. And as @toskv mentioned its really too broad question to be answered and depends on numerous different things. Second one is more specific — how do you prepare the deployment version of the application. You have several options here:

1. Deploy as it is. Just that — no minification, concatenation, name mangling etc. Transpile all your ts project, copy all your resulting js/css/… sources + dependencies to the hosting server and your are good to go.
2. Deploy using special bundling tools. Like webpack or systemjs builder. They come with all possibilities that are lacking in #1. You can pack all your app code into just couple of js/css/… files that you reference in your html. Systemjs buider even allows you to get rid of need to include systemjs as part of your deployment package.

Yes you will most likely need to deploy systemjs and bunch of other external libraries as part of your package. And yes you will be able to bundle them into just couple of js files you reference from your html page. You do not have to reference all your compiled js files from the page though — systemjs as a module loader will take care of that.

I know it sounds muddy — to help get you started with the #2 here are two really good sample applications:

SystemJS builder: [angular2 seed](https://github.com/mgechev/angular2-seed)

WebPack: [angular2 webpack starter](https://github.com/AngularClass/angular2-webpack-starter)

Look how they do it — and hopefully this will help you to find your way of bundling apps you make.

**[Source](https://stackoverflow.com/questions/35539622)**

**#38. ngFor with index as value in attribute**

**[Vivendi](https://stackoverflow.com/users/1175327/vivendi) asked,**

I have a simple `ngFor` loop which also keeps track of the current `index`. I want to store that `index` value in an attribute so I can print it. But I can't figure out how this works.

I basically have this:

```
<ul *ngFor="#item of items; #i = index" data-index="#i">
    <li>{{item}}</li>
</ul>
```

I want to store the value of `#i` in the attribute `data-index`. I tried several methods but none of them worked.

I have a demo here: [http://plnkr.co/edit/EXpOKAEIFlI9QwuRcZqp?p=preview](http://plnkr.co/edit/EXpOKAEIFlI9QwuRcZqp?p=preview)

How can I store the `index` value in the `data-index` attribute?

**[Thierry Templier](https://stackoverflow.com/users/1873365) answered,**

I would use this syntax to set the index value into an attribute of the HTML element:

```
<ul>
    <li *ngFor="#item of items; #i = index" [attr.data-index]="i">
        {{item}}
    </li>
</ul>
```

Here is the updated plunkr: [http://plnkr.co/edit/LiCeyKGUapS5JKkRWnUJ?p=preview](http://plnkr.co/edit/LiCeyKGUapS5JKkRWnUJ?p=preview).

**Update for recent angular 2 releases** You have to use `let` to declare the value rather than `#`.

```
<ul>
    <li *ngFor="let item of items; let i = index" [attr.data-index]="i">
        {{item}}
    </li>
</ul>
```

**[Source](https://stackoverflow.com/questions/35405618)**

**#39. Define global constants in Angular 2**

**[AndreFeijo](https://stackoverflow.com/users/2946773/andrefeijo) asked,**

In Angular 1.x you can define constants like this:

```
angular.module('mainApp.config', [])
.constant('API_ENDPOINT', 'http://127.0.0.1:6666/api/')
```

What would be the equivalent in Angular2 (with Typescript)? I just don’t want to repeat the API base url over and over again in all my services.

**[AndreFeijo](https://stackoverflow.com/users/2946773) answered,**

**Below changes works for me on Angular 2 final version:**

```
export class AppSettings {
   public static API_ENDPOINT='http://127.0.0.1:6666/api/';
}
```

**And then in the service:**

```
import {Http} from 'angular2/http';
import {Message} from '../models/message';
import {Injectable} from 'angular2/core';
import {Observable} from 'rxjs/Observable';
import {AppSettings} from '../appSettings';
import 'rxjs/add/operator/map';

@Injectable()
export class MessageService {

    constructor(private http: Http) { }
    
    getMessages(): Observable<Message[]> {
        return this.http.get(AppSettings.API_ENDPOINT+'/messages')
            .map(response => response.json())
            .map((messages: Object[]) => {
                return messages.map(message => this.parseData(message));
            });
    }
    
    private parseData(data): Message {
        return new Message(data);
    }
}
```

**[Source](https://stackoverflow.com/questions/34986922)**

**#40. Angular — Use pipes in services and components**

**[POSIX-compliant](https://stackoverflow.com/users/4602586/posix-compliant) asked,**

In AngularJS, I am able to use filters (pipes) inside of services and controllers using syntax similar to this:

`$filter('date')(myDate, 'yyyy-MM-dd');`

Is it possible to use pipes in services/components like this in Angular?

**[cexbrayat](https://stackoverflow.com/users/971121) answered,**

As usual in Angular, you can rely on dependency injection:

```
import { DatePipe } from '@angular/common';
class MyService {

  constructor(private datePipe: DatePipe) {}
  
  transformDate(date) {
    this.datePipe.transform(myDate, 'yyyy-MM-dd');
  }
}
```

Add `DatePipe` to your providers list in your module; if you forget to do this you'll get an error `no provider for DatePipe`:

`providers: [DatePipe,...]`

Be warned though that the `DatePipe` was relying on the Intl API until version 5, which is not supported by all browsers (check the [compatibility table](http://kangax.github.io/compat-table/esintl/)).

If you’re using older Angular versions, you should add the `Intl` polyfill to your project to avoid any problem. See this [related question](https://stackoverflow.com/questions/35017800/ionic-2-using-angular-2-pipe-breaks-on-ios-cant-find-variable-intl/35018352#35018352) for a more detailed answer.

**[Source](https://stackoverflow.com/questions/35144821)**

**#41. Angular2 Exception: Can’t bind to ‘routerLink’ since it isn’t a known native property**

**[Lester Burnham](https://stackoverflow.com/users/1798547/lester-burnham) asked,**

Obviously the beta for Angular2 is newer than new, so there’s not much information out there, but I am trying to do what I think is some fairly basic routing.

Hacking about with the quick-start code and other snippets from the [https://angular.io](https://angular.io/) website has resulted in the following file structure:

```
angular-testapp/
    app/
        app.component.ts
        boot.ts
        routing-test.component.ts
    index.html
```

With the files being populated as follows:

**index.html**

```
<html>

  <head>
    <base href="/">
    <title>Angular 2 QuickStart</title>
    <link href="../css/bootstrap.css" rel="stylesheet">
    
    <!-- 1. Load libraries -->
    <script src="node_modules/angular2/bundles/angular2-polyfills.js"></script>
    <script src="node_modules/systemjs/dist/system.src.js"></script>
    <script src="node_modules/rxjs/bundles/Rx.js"></script>
    <script src="node_modules/angular2/bundles/angular2.dev.js"></script>
    <script src="node_modules/angular2/bundles/router.dev.js"></script>
    
    <!-- 2. Configure SystemJS -->
    <script>
      System.config({
        packages: {        
          app: {
            format: 'register',
            defaultExtension: 'js'
          }
        }
      });
      System.import('app/boot')
            .then(null, console.error.bind(console));
    </script>
    
  </head>
  
  <!-- 3. Display the application -->
  <body>
    <my-app>Loading...</my-app>
  </body>
  
</html>
```

**boot.ts**

```
import {bootstrap}    from 'angular2/platform/browser'
import {ROUTER_PROVIDERS} from 'angular2/router';

import {AppComponent} from './app.component'

bootstrap(AppComponent, [
    ROUTER_PROVIDERS
]);
```

**app.component.ts**

```
import {Component} from 'angular2/core';
import {RouteConfig, ROUTER_DIRECTIVES, ROUTER_PROVIDERS, LocationStrategy, HashLocationStrategy} from 'angular2/router';

import {RoutingTestComponent} from './routing-test.component';

@Component({
    selector: 'my-app',
    template: `
        <h1>Component Router</h1>
        <a [routerLink]="['RoutingTest']">Routing Test</a>
        <router-outlet></router-outlet>
        `
})

@RouteConfig([
    {path:'/routing-test', name: 'RoutingTest', component: RoutingTestComponent, useAsDefault: true},
])

export class AppComponent { }
```

**routing-test.component.ts**

```
import {Component} from 'angular2/core';
import {Router} from 'angular2/router';

@Component({
    template: `
        <h2>Routing Test</h2>
        <p>Interesting stuff goes here!</p>
        `
})
export class RoutingTestComponent { }
```

Attempting to run this code produces the error:
```

EXCEPTION: Template parse errors:
Can't bind to 'routerLink' since it isn't a known native property ("
        <h1>Component Router</h1>
        <a [ERROR ->][routerLink]="['RoutingTest']">Routing Test</a>
        <router-outlet></router-outlet>
        "): AppComponent@2:11
```

I found a vaguely related issue here; [router-link directives broken after upgrading to angular2.0.0-beta.0](https://stackoverflow.com/questions/34304115/router-link-directives-broken-after-upgrading-to-angular2-0-0-beta-0). However, the “working example” in one of the answers is based on pre-beta code — which may well still work, but I would like to know why the code I have created is not working.

Any pointers would be gratefully received!

**[Günter Zöchbauer](https://stackoverflow.com/users/217408) answered,**

**>=RC.5**

import the `RouterModule` See also [https://angular.io/docs/ts/latest/guide/router.html](https://angular.io/docs/ts/latest/guide/router.html)

```
@NgModule({ 
  imports: [RouterModule],
  ...
})
```

**>=RC.2**

**app.routes.ts**

```
import { provideRouter, RouterConfig } from '@angular/router';

export const routes: RouterConfig = [
  ...
];

export const APP_ROUTER_PROVIDERS = [provideRouter(routes)];
```

**main.ts**

```
import { bootstrap } from '@angular/platform-browser-dynamic';
import { APP_ROUTER_PROVIDERS } from './app.routes';

bootstrap(AppComponent, [APP_ROUTER_PROVIDERS]);
```

**<=RC.1**

Your code is missing

```
@Component({
    ...
    directives: [ROUTER_DIRECTIVES],
    ...)}
```

You can’t use directives like `routerLink` or `router-outlet` without making them known to your component.

While directive names were changed to be case-sensitive in Angular2, elements still use `-` in the name like `<router-outlet>` to be compatible with the web-components spec which requ`i`re a - in the name of custom elements.

**register globally**

To make `ROUTER_DIRECTIVES` globally available, add this provider to `bootstrap(...)`:

`provide(PLATFORM_DIRECTIVES, {useValue: [ROUTER_DIRECTIVES], multi: true})`

then it’s no longer necessary to add `ROUTER_DIRECTIVES` to each component.

**[Source](https://stackoverflow.com/questions/34317044)**

**#42. Angular 2 dynamic tabs with user-click chosen components**

**[Cuel](https://stackoverflow.com/users/2951897/cuel) asked,**

I’m trying to setup a tab system that allows for components to register themselves (with a title). The first tab is like an inbox, there’s plenty of actions/link items to choose from for the users, and each of these clicks should be able to instantiate a new component, on click. The actions / links comes in from JSON.

The instantiated component will then register itself as a new tab.

I’m not sure if this is the ‘best’ approach? Sofar the only guides I’ve seen are for static tabs, which doesn’t help.

So far I’ve only got the tabs service which is bootstrapped in main to persist throughout the app, looks ~something like this.

```
export interface ITab { title: string; }

@Injectable()
export class TabsService {
    private tabs = new Set<ITab>();
    
    addTab(title: string): ITab {
        let tab: ITab = { title };
        this.tabs.add(tab);
        return tab;
    }
    
    removeTab(tab: ITab) {
        this.tabs.delete(tab);
    }
}
```

Questions:

1) How can I have a dynamic list in the inbox that creates new (different) tabs? I am sort of guessing the DynamicComponentBuilder would be used?

2) How can the components created from the inbox (on click) register themselves as tabs and also be shown? I’m guessing ng-content but I can’t find much info on how to use it

Edit: Try to clarify

Think of the inbox as a mail inbox, items are fetched as JSON and displays several items. Once one of the items is clicked, a new tab is created with that items action ‘type’. The type is then a component

Edit2: Image

[http://i.imgur.com/yzfMOXJ.png](http://i.imgur.com/yzfMOXJ.png)

**[Günter Zöchbauer](https://stackoverflow.com/users/217408) answered,**

**update**

**[Angular 5 StackBlitz example](https://stackblitz.com/edit/angular-ygz3jg)**

**update**

`ngComponentOutlet` was added to 4.0.0-beta.3

**update**

There is a `NgComponentOutlet` work in progress that does something similar [https://github.com/angular/angular/pull/11235](https://github.com/angular/angular/pull/11235)

**RC.7**

**[Plunker example RC.7](http://plnkr.co/edit/UGzoPTCHlXKWrn4p8gd1?p=preview)**

```
// Helper component to add dynamic components
@Component({
  selector: 'dcl-wrapper',
  template: `<div #target></div>`
})
export class DclWrapper {
  @ViewChild('target', {read: ViewContainerRef}) target: ViewContainerRef;
  @Input() type: Type<Component>;
  cmpRef: ComponentRef<Component>;
  private isViewInitialized:boolean = false;
  
  constructor(private componentFactoryResolver: ComponentFactoryResolver, private compiler: Compiler) {}
  
  updateComponent() {
    if(!this.isViewInitialized) {
      return;
    }
    if(this.cmpRef) {
      // when the `type` input changes we destroy a previously 
      // created component before creating the new one
      this.cmpRef.destroy();
    }
    
    let factory = this.componentFactoryResolver.resolveComponentFactory(this.type);
    this.cmpRef = this.target.createComponent(factory)
    // to access the created instance use
    // this.compRef.instance.someProperty = 'someValue';
    // this.compRef.instance.someOutput.subscribe(val => doSomething());
  }
  
  ngOnChanges() {
    this.updateComponent();
  }
  
  ngAfterViewInit() {
    this.isViewInitialized = true;
    this.updateComponent();  
  }
  
  ngOnDestroy() {
    if(this.cmpRef) {
      this.cmpRef.destroy();
    }    
  }
}
```

Usage example

```
// Use dcl-wrapper component
@Component({
  selector: 'my-tabs',
  template: `
  <h2>Tabs</h2>
  <div *ngFor="let tab of tabs">
    <dcl-wrapper [type]="tab"></dcl-wrapper>
  </div>
`
})
export class Tabs {
  @Input() tabs;
}

@Component({
  selector: 'my-app',
  template: `
  <h2>Hello {{name}}</h2>
  <my-tabs [tabs]="types"></my-tabs>
`
})
export class App {
  // The list of components to create tabs from
  types = [C3, C1, C2, C3, C3, C1, C1];
}

@NgModule({
  imports: [ BrowserModule ],
  declarations: [ App, DclWrapper, Tabs, C1, C2, C3],
  entryComponents: [C1, C2, C3],
  bootstrap: [ App ]
})
export class AppModule {}
```

See also [angular.io DYNAMIC COMPONENT LOADER](https://angular.io/docs/ts/latest/cookbook/dynamic-component-loader.html)

**older versions xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx**

This changed again in Angular2 RC.5

I will update the example below but it’s the last day before vacation.

This [Plunker example](http://plnkr.co/edit/3dzkMVXe4AGSRhk11TXG?p=preview) demonstrates how to dynamically create components in RC.5

**Update — use [ViewContainerRef](https://angular.io/docs/ts/latest/api/core/index/ViewContainerRef-class.html).createComponent()**

Because `DynamicComponentLoader` is deprecated, the approach needs to be update again.

```
@Component({
  selector: 'dcl-wrapper',
  template: `<div #target></div>`
})
export class DclWrapper {
  @ViewChild('target', {read: ViewContainerRef}) target;
  @Input() type;
  cmpRef:ComponentRef;
  private isViewInitialized:boolean = false;
  
  constructor(private resolver: ComponentResolver) {}
  
  updateComponent() {
    if(!this.isViewInitialized) {
      return;
    }
    if(this.cmpRef) {
      this.cmpRef.destroy();
    }
   this.resolver.resolveComponent(this.type).then((factory:ComponentFactory<any>) => {
      this.cmpRef = this.target.createComponent(factory)
      // to access the created instance use
      // this.compRef.instance.someProperty = 'someValue';
      // this.compRef.instance.someOutput.subscribe(val => doSomething());
    });
  }
  
  ngOnChanges() {
    this.updateComponent();
  }
  
  ngAfterViewInit() {
    this.isViewInitialized = true;
    this.updateComponent();  
  }
  ngOnDestroy() {
    if(this.cmpRef) {
      this.cmpRef.destroy();
    }    
  }
}
```

**[Plunker example RC.4](http://plnkr.co/edit/GJTLrnQdRDBvZenX59PZ?p=preview)**
**[Plunker example beta.17](https://plnkr.co/edit/PpgMvS?p=preview)**

**Update — use loadNextToLocation**

```
export class DclWrapper {
  @ViewChild('target', {read: ViewContainerRef}) target;
  @Input() type;
  cmpRef:ComponentRef;
  private isViewInitialized:boolean = false;
  
  constructor(private dcl:DynamicComponentLoader) {}
  
  updateComponent() {
    // should be executed every time `type` changes but not before `ngAfterViewInit()` was called 
    // to have `target` initialized
    if(!this.isViewInitialized) {
      return;
    }
    if(this.cmpRef) {
      this.cmpRef.destroy();
    }
    this.dcl.loadNextToLocation(this.type, this.target).then((cmpRef) => {
      this.cmpRef = cmpRef;
    });
  }
  
  ngOnChanges() {
    this.updateComponent();
  }
  
  ngAfterViewInit() {
    this.isViewInitialized = true;
    this.updateComponent();  
  }
  
  ngOnDestroy() {
    if(this.cmpRef) {
      this.cmpRef.destroy();
    }    
  }
}
```

**[Plunker example beta.17](https://plnkr.co/edit/kc2Bgg?p=preview)**

**original**

Not entirely sure from your question what your requirements are but I think this should do what you want.

The `Tabs` component gets an array of types passed and it creates "tabs" for each item in the array.

```
@Component({
  selector: 'dcl-wrapper',
  template: `<div #target></div>`
})
export class DclWrapper {
  constructor(private elRef:ElementRef, private dcl:DynamicComponentLoader) {}
  @Input() type;
  
  ngOnChanges() {
    if(this.cmpRef) {
      this.cmpRef.dispose();
    }
    this.dcl.loadIntoLocation(this.type, this.elRef, 'target').then((cmpRef) => {
      this.cmpRef = cmpRef;
    });
  }
}

@Component({
  selector: 'c1',
  template: `<h2>c1</h2>`
  
})
export class C1 {
}

@Component({
  selector: 'c2',
  template: `<h2>c2</h2>`
})
export class C2 {
}
@Component({
  selector: 'c3',
  template: `<h2>c3</h2>`
  
})
export class C3 {
}

@Component({
  selector: 'my-tabs',
  directives: [DclWrapper],
  template: `
  <h2>Tabs</h2>
  <div *ngFor="let tab of tabs">
    <dcl-wrapper [type]="tab"></dcl-wrapper>
  </div>
`
})
export class Tabs {
  @Input() tabs;
}

@Component({
  selector: 'my-app',
  directives: [Tabs]
  template: `
  <h2>Hello {{name}}</h2>
  <my-tabs [tabs]="types"></my-tabs>
`
})
export class App {
  types = [C3, C1, C2, C3, C3, C1, C1];
}
```

**[Plunker example beta.15](https://plnkr.co/edit/kc2Bgg?p=preview)** (not based on your Plunker)

There is also a way to pass data along that can be passed to the dynamically created component like (`someData` would need to be passed like `type`)

```
this.dcl.loadIntoLocation(this.type, this.elRef, 'target').then((cmpRef) => {
  cmpRef.instance.someProperty = someData;
  this.cmpRef = cmpRef;
});
```

There is also some support to use dependency injection with shared services.

For more details see [https://angular.io/docs/ts/latest/cookbook/dynamic-component-loader.html](https://angular.io/docs/ts/latest/cookbook/dynamic-component-loader.html)

**[Source](https://stackoverflow.com/questions/36325212)**

**#43. Delegation: EventEmitter or Observable in Angular**

**[the_critic](https://stackoverflow.com/users/1066899/the-critic) asked,**

I am trying to implement something like a delegation pattern in Angular. When the user clicks on a `nav-item`, I would like to call a function which then emits an event which should in turn be handled by some other component listening for the event.

Here is the scenario: I have a `Navigation` component:

```
import {Component, Output, EventEmitter} from 'angular2/core';

@Component({
    // other properties left out for brevity
    events : ['navchange'], 
    template:`
      <div class="nav-item" (click)="selectedNavItem(1)"></div>
    `
})

export class Navigation {

    @Output() navchange: EventEmitter<number> = new EventEmitter();
    
    selectedNavItem(item: number) {
        console.log('selected nav item ' + item);
        this.navchange.emit(item)
    }
    
}
```

Here is the observing component:

```
export class ObservingComponent {

  // How do I observe the event ? 
  // <----------Observe/Register Event ?-------->
  
  public selectedNavItem(item: number) {
    console.log('item index changed!');
  }
  
}
```

The key question is, how do I make the observing component observe the event in question ?

**[Mark Rajcok](https://stackoverflow.com/users/215945) answered,**

**Update 2016–06–27:** instead of using Observables, use either

* a BehaviorSubject, as recommended by @Abdulrahman in a comment, or
* a ReplaySubject, as recommended by @Jason Goemaat in a comment

A [Subject](http://reactivex.io/rxjs/manual/overview.html#subject) is both an Observable (so we can `subscribe()` to it) and an Observer (so we can call `next()` on it to emit a new value). We exploit this feature. A Subject allows values to be multicast to many Observers. We don't exploit this feature (we only have one Observer).

[BehaviorSubject](http://reactivex.io/rxjs/manual/overview.html#behaviorsubject) is a variant of Subject. It has the notion of “the current value”. We exploit this: whenever we create an ObservingComponent, it gets the current navigation item value from the BehaviorSubject automatically.

The code below and the [plunker](http://plnkr.co/edit/XqwwUM44NQEpxQVFFxNW?p=preview) use BehaviorSubject.

[ReplaySubject](http://reactivex.io/rxjs/manual/overview.html#replaysubject) is another variant of Subject. If you want to wait until a value is actually produced, use `ReplaySubject(1)`. Whereas a BehaviorSubject requires an initial value (which will be provided immediately), ReplaySubject does not. ReplaySubject will always provide the most recent value, but since it does not have a required initial value, the service can do some async operation before returning it's first value. It will still fire immediately on subsequent calls with the most recent value. If you just want one value, use `first()` on the subscription. You do not have to unsubscribe if you use `first()`.

```
import {Injectable}      from '@angular/core'
import {BehaviorSubject} from 'rxjs/BehaviorSubject';

@Injectable()
export class NavService {
  // Observable navItem source
  private _navItemSource = new BehaviorSubject<number>(0);
  // Observable navItem stream
  navItem$ = this._navItemSource.asObservable();
  // service command
  changeNav(number) {
    this._navItemSource.next(number);
  }
}

import {Component}    from '@angular/core';
import {NavService}   from './nav.service';
import {Subscription} from 'rxjs/Subscription';

@Component({
  selector: 'obs-comp',
  template: `obs component, item: {{item}}`
})
export class ObservingComponent {
  item: number;
  subscription:Subscription;
  constructor(private _navService:NavService) {}
  ngOnInit() {
    this.subscription = this._navService.navItem$
       .subscribe(item => this.item = item)
  }
  ngOnDestroy() {
    // prevent memory leak when component is destroyed
    this.subscription.unsubscribe();
  }
}

@Component({
  selector: 'my-nav',
  template:`
    <div class="nav-item" (click)="selectedNavItem(1)">nav 1 (click me)</div>
    <div class="nav-item" (click)="selectedNavItem(2)">nav 2 (click me)</div>`
})
export class Navigation {
  item = 1;
  constructor(private _navService:NavService) {}
  selectedNavItem(item: number) {
    console.log('selected nav item ' + item);
    this._navService.changeNav(item);
  }
}
```

[Plunker](http://plnkr.co/edit/XqwwUM44NQEpxQVFFxNW?p=preview)

**Original answer that uses an Observable:** (it requires more code and logic than using a BehaviorSubject, so I don’t recommend it, but it may be instructive)

So, here’s an implementation that uses an Observable instead of an EventEmitter. Unlike my EventEmitter implementation, this implementation also stores the currently selected `navItem` in the service, so that when an observing component is created, it can retrieve the current value via API call `navItem()`, and then be notified of changes via the `navChange$` Observable.

```
import {Observable} from 'rxjs/Observable';
import 'rxjs/add/operator/share';
import {Observer} from 'rxjs/Observer';

export class NavService {
  private _navItem = 0;
  navChange$: Observable<number>;
  private _observer: Observer;
  constructor() {
    this.navChange$ = new Observable(observer =>
      this._observer = observer).share();
    // share() allows multiple subscribers
  }
  changeNav(number) {
    this._navItem = number;
    this._observer.next(number);
  }
  navItem() {
    return this._navItem;
  }
}

@Component({
  selector: 'obs-comp',
  template: `obs component, item: {{item}}`
})
export class ObservingComponent {
  item: number;
  subscription: any;
  constructor(private _navService:NavService) {}
  ngOnInit() {
    this.item = this._navService.navItem();
    this.subscription = this._navService.navChange$.subscribe(
      item => this.selectedNavItem(item));
  }
  selectedNavItem(item: number) {
    this.item = item;
  }
  ngOnDestroy() {
    this.subscription.unsubscribe();
  }
}

@Component({
  selector: 'my-nav',
  template:`
    <div class="nav-item" (click)="selectedNavItem(1)">nav 1 (click me)</div>
    <div class="nav-item" (click)="selectedNavItem(2)">nav 2 (click me)</div>
  `,
})
export class Navigation {
  item:number;
  constructor(private _navService:NavService) {}
  selectedNavItem(item: number) {
    console.log('selected nav item ' + item);
    this._navService.changeNav(item);
  }
}
```

[Plunker](http://plnkr.co/edit/vL76b0UjrAav3Ao7kF4W?p=preview)

See also the [Component Interaction Cookbook example](https://angular.io/docs/ts/latest/cookbook/component-communication.html#!#bidirectional-service), which uses a `Subject` in addition to observables. Although the example is "parent and children communication," the same technique is applicable for unrelated components.

**[Source](https://stackoverflow.com/questions/34376854)**

**#44. How to add bootstrap to an angular-cli project**

**[Jerome](https://stackoverflow.com/users/811865/jerome) asked,**

We want to use bootstrap 4 (4.0.0-alpha.2) in our app generated with angular-cli 1.0.0-beta.5 (w/ node v6.1.0).

After getting bootstrap and its dependencies with npm, our first approach consisted in adding them in `angular-cli-build.js`:

```
'bootstrap/dist/**/*.min.+(js|css)',  
  'jquery/dist/jquery.min.+(js|map)',  
  'tether/dist/**/*.min.+(js|css)',
```

and import them in our `index.html`

```
<script src="vendor/jquery/dist/jquery.min.js"></script>
  <script src="vendor/tether/dist/js/tether.min.js"></script>
  <link rel="stylesheet" type="text/css" href="vendor/bootstrap/dist/css/bootstrap.min.css">
  <script src="vendor/bootstrap/dist/js/bootstrap.min.js"></script>
```

This worked fine with `ng serve` but as soon as we produced a build with `-prod` flag all these dependencies disappeared from `dist/vendor` (surprise !).

**How we are intended to handle such scenario (i.e. loading bootstrap scripts) in a project generated with angular-cli ?**

We had the following thoughts but we don’t really know which way to go…

* use a CDN ? but we would rather serve these files to guarantee that they will be available
* copy dependencies to `dist/vendor` after our `ng build -prod` ? But that seems like something angular-cli should provide since it 'takes care' of the build part ?
* adding jquery, bootstrap and tether in src/system-config.ts and somehow pull them into our bundle in main.ts ? But that seemed wrong considering that we are not going to explicitly use them in our application’s code (unlike moment.js or something like lodash, for example)

**[pd farhad](https://stackoverflow.com/users/1417742) answered,**

**IMPORTANT UPDATE: ng2-bootstrap is now replaced by [ngx-bootstrap](https://github.com/valor-software/ngx-bootstrap) **

ngx-bootstrap supports both angular 3 and 4.

**Update : `1.0.0-beta.11-webpack` or above versions**

First of all check your angular-cli version with the following command in the terminal: `ng -v`

If your angular-cli version is greater than `1.0.0-beta.11-webpack` then you should follow these steps:

1) install ngx-bootstrap and bootstrap:

`npm install ngx-bootstrap bootstrap --save`

This line installs bootstrap 3 nowadays, but can install bootstrap 4 in future. Keep in mind ngx-bootstrap supports both versions.

1) open src/app/app.module.ts and add
```
import { AlertModule } from 'ngx-bootstrap'; ... @NgModule({ ... 
imports: [AlertModule.forRoot(), ... ], ... })
```
2)open angular-cli.json and insert a new entry into the styles array
```
"styles": [ "styles.css",
"../node_modules/bootstrap/dist/css/bootstrap.min.css" ],
```
3)open src/app/app.component.html and add

`<alert type="success">hello&l`t;/alert>

**1.0.0-beta.10 or below versions:**

And, if your angular-cli version is 1.0.0-beta.10 or below versions then you can use below steps.

First go to the project directory and type

`npm install ngx-bootstrap --save`

then open your **angular-cli-build.js** and add this line

```
vendorNpmFiles: [
   ..................
   'ngx-bootstrap/**/*.js',
    ....................
  ]
```

now open your **src/system-config.ts**, write

```
const map:any = {
     ..................
   'ngx-bootstrap': 'vendor/ngx-bootstrap',
    ....................
}
```

and

```
const packages: any = {
  'ngx-bootstrap': {
    format: 'cjs',
    defaultExtension: 'js',
    main: 'ngx-bootstrap.js'
  }
};
```

**[Source](https://stackoverflow.com/questions/37649164)**

**#45. access key and value of object using `*ngFor`**

**[Pardeep Jain](https://stackoverflow.com/users/5043867/pardeep-jain) asked,**

Bit confused about how to get `Key and Value` of object in angular2 while usng `*ngFor` for iteration over object. i know in angular 1.x there is syntax like

`ng-repeat="(key, value) in demo"`

but in angular2 i don’t know i tired the same but did’t get successful. i have tried the below code but did’t run please tell me where i am doing wrong.

```
<ul>
  <li *ngFor='#key of demo'>{{key}}</li>
</ul>

demo = {
    'key1': [{'key11':'value11'}, {'key12':'value12'}],
    'key2': [{'key21':'value21'}, {'key22':'value22'}],
  }
```

here is plnkr where i have tried the same : [http://plnkr.co/edit/mIj619FncOpfdwrR0KeG?p=preview](http://plnkr.co/edit/mIj619FncOpfdwrR0KeG?p=preview)

I want to get `key1` and `key2` dynamically using `*ngFor`. How to get it? i searched a lot found idea of using pipe but how to use i dont know. is there any inbuild pipe for doing same in angular2 ?

**[Thierry Templier](https://stackoverflow.com/users/1873365) answered,**

You could create a custom pipe to return the list of key for each element. Something like that:

```
import { PipeTransform, Pipe } from '@angular/core';

@Pipe({name: 'keys'})
export class KeysPipe implements PipeTransform {
  transform(value, args:string[]) : any {
    let keys = [];
    for (let key in value) {
      keys.push(key);
    }
    return keys;
  }
}
```

and use it like that:

```
<tr *ngFor="let c of content">           
  <td *ngFor="let key of c | keys">{{key}}: {{c[key]}}</td>
</tr>
```

**Edit**

You could also return an entry containing both key and value:

```
@Pipe({name: 'keys'})
export class KeysPipe implements PipeTransform {
  transform(value, args:string[]) : any {
    let keys = [];
    for (let key in value) {
      keys.push({key: key, value: value[key]});
    }
    return keys;
  }
}
```

and use it like that:

```
<span *ngFor="let entry of content | keys">           
  Key: {{entry.key}}, value: {{entry.value}}
</span>
```

**[Source](https://stackoverflow.com/questions/35534959)**

**#46. Angular exception: Can’t bind to ‘ngFor’ since it isn’t a known native property**

**[Mark Rajcok](https://stackoverflow.com/users/215945/mark-rajcok) asked,**

What am I doing wrong?

```
import {bootstrap, Component} from 'angular2/angular2'

@Component({
  selector: 'conf-talks',
  template: `<div *ngFor="talk of talks">
     {{talk.title}} by {{talk.speaker}}
     <p>{{talk.description}}
   </div>`
})
class ConfTalks {
  talks = [ {title: 't1', speaker: 'Brian', description: 'talk 1'},
            {title: 't2', speaker: 'Julie', description: 'talk 2'}];
}
@Component({
  selector: 'my-app',
  directives: [ConfTalks],
  template: '<conf-talks></conf-talks>'
})
class App {}
bootstrap(App, [])
```

The error is

```
EXCEPTION: Template parse errors:
Can't bind to 'ngFor' since it isn't a known native property
("<div [ERROR ->]*ngFor="talk of talks">
```

**[Mark Rajcok](https://stackoverflow.com/users/215945) answered,**

I missed `let` in front of `talk`:

`<div *ngFor="let talk of talks">`

Note that [as of beta.17](https://github.com/angular/angular/blob/master/CHANGELOG.md#200-beta17-2016-04-28) usage of `#...` to declare local variables inside of structural directives like NgFor is deprecated. Use `let` instead.

`<div *ngFor="#talk of talk`s"> now becomes `<div *ngFor="let talk o`f talks">

Original answer:

I missed `#` in front of `talk`:

`<div *ngFor="#talk of talks">`

It is so easy to forget that `#`. I wish the Angular exception error message would instead say:

`you forgot that # again.`

**[Source](https://stackoverflow.com/questions/34012291)**

**#47. How to add font-awesome to Angular 2 + CLI project**

**[Nik](https://stackoverflow.com/users/1394625/nik) asked,**

I’m using Angular 2+ and Angular CLI.

How do I add font-awesome to my project?

**[AIon](https://stackoverflow.com/users/5904566) answered,**

After Angular 2.0 final release, **the structure of the Angular2 CLI project has been changed** — you don’t need any vendor files, no system.js — only webpack. So you do:

1. `npm install font-awesome --save`
2. In the angular-cli.json file locate the `styles[]` array and add font-awesome references directory here, like below: `“apps”: [ { “root”: “src”, “outDir”: “dist”, …. “styles”: [ “styles.css”, “../node_modules/bootstrap/dist/css/bootstrap.css”, “../node_modules/font-awesome/css/font-awesome.css” // -here webpack will automatically build a link css element out of this!? ], … } ] ]`
3. Place some font-awesome icons in any html file you want: `<i class=”fa fa-american-sign-language-interpreting fa-5x” aria-hidden=”true”> </i>`
4. Run `ng build` and `ng serve` again - because the watchers are only for the src folder and angular-cli.json is not observed for changes.
5. Enjoy your awesome icons!

**[Source](https://stackoverflow.com/questions/38796541)**

**#48. Difference between HTTP and HTTPClient in angular 4?**

**[Aioub Amini](https://stackoverflow.com/users/3551590/aiyoub-amini) asked,**

I want to know which one to use to build a mock web service to test the Angular program?

**[AngularInDepth.com](https://stackoverflow.com/users/2545680) answered,**

Use the `HttpClient` class from `HttpClientModule` if you're using Angular 4.3.x and above:

```
import { HttpClientModule } from '@angular/common/http';

@NgModule({
 imports: [
   BrowserModule,
   HttpClientModule
 ],
 ...
 
 class MyService() {
    constructor(http: HttpClient) {...}
```

It’s an upgraded version of `http` from `@angular/http` module with the following improvements:

* Interceptors allow middleware logic to be inserted into the pipeline
* Immutable request/response objects
* Progress events for both request upload and response download

You can read about how it works in [Insider’s guide into interceptors and HttpClient mechanics in Angular.](https://blog.angularindepth.com/insiders-guide-into-interceptors-and-httpclient-mechanics-in-angular-103fbdb397bf)

* Typed, synchronous response body access, including support for JSON body types
* JSON is an assumed default and no longer needs to be explicitly parsed
* Post-request verification & flush based testing framework

Going forward the old http client will be deprecated. Here are the links to the [commit message](https://github.com/angular/angular/commit/37797e2) and the [official docs](https://angular.io/guide/http).

Also pay attention that old http was injected using `Http` class token instead of the new `HttpClient`:

```
import { HttpModule } from '@angular/http';

@NgModule({
 imports: [
   BrowserModule,
   HttpModule
 ],
 ...
 
 class MyService() {
    constructor(http: Http) {...}
```

Also, new `HttpClient` seem to require `tslib` in runtime, so you have to install it `npm i tslib` and update `system.config.js` if you're using `SystemJS`:

```
map: {
     ...
    'tslib': 'npm:tslib/tslib.js',
```

And you need to add another mapping if you use SystemJS:

`'@angular/common/http': 'npm:@angular/common/bundles/common-http.umd.js',`

**[Source](https://stackoverflow.com/questions/45129790)**