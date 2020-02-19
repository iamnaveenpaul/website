---
title: Answers on StackOverflow to the most popular Angular questions (Part 3)
image: "/assets/default-social-image.png"
categories: Angular
---

**48 answers on StackOverflow to the most popular Angular questions (Part 3/4)**

This gathered list is the most common questions and answers from **Stackoverflow**. These questions were chosen by the highest score received. Whether you are an expert or a beginner, you can learn from others’ experiences.

**Table of Contents**

#25. Angular — What is the meanings of module.id in component?

#26. How can I get new selection in “select” in Angular 2?

#27. Angular exception: Can’t bind to ‘ngForIn’ since it isn’t a known native property

#28. `*ngIf` and `*ngFor` on same element causing error

#29. What is the Angular equivalent to an AngularJS $watch?

#30. Importing lodash into angular2 + typescript application

#31. How to detect a route change in Angular?

#32. Global Events in Angular

#33. What are differences between SystemJS and Webpack?

#34. Angular: Can’t find Promise, Map, Set and Iterator

#35. How to detect when an @Input() value changes in Angular?

#36. How to pass url arguments (query string) to a HTTP request on Angular

**Enjoy!**

**#25. Angular — What is the meanings of module.id in component?**

**[Nishchit Dhanani](https://stackoverflow.com/users/2837412/nishchit-dhanani) asked,**

In an Angular app, I have seen that `@Component` has property `moduleId`. What does it mean?

And when `module.id` is not defined anywhere, the app still works. How can it still work?

```
@Component({
  moduleId: module.id,
  selector: 'ng-app',
  templateUrl: 'app.component.html',
  styleUrls: ['app.component.css'],
  directives: [AppComponent]
});
```

**[Nishchit Dhanani](https://stackoverflow.com/users/2837412) answered,**

The beta release of Angular (since vesion 2-alpha.51) supports relative assets for components, like **templateUrl** and **styleUrls** in the `@Component` decorator.

`module.id` works when using CommonJS. You don't need to worry about how it works.

`Remember: setting moduleId: module.id in the @Component decorator is the key here. If you don't have that then Angular 2 will be looking for your files at the root level.`

Source from [Justin Schwartzenberger’s post](http://schwarty.com/2015/12/22/angular2-relative-paths-for-templateurl-and-styleurls/), thanks to [@Pradeep Jain](https://stackoverflow.com/users/5043867/pardeep-jain)

**Update on 16 Sep 2016:**

`If you are using webpack for bundling then you don't need module.id in decorator. Webpack plugins auto handle (add it) module.id in final bundle`

**[Source](https://stackoverflow.com/questions/37178192)**

**#26. How can I get new selection in “select” in Angular 2?**

**[Hongbo Miao](https://stackoverflow.com/users/2000548/hongbo-miao) asked,**

I am using Angular 2 (TypeScript).

I want to do something for new selection, but what I got in onChange() is always last selection. How can I get new selection?

```
<select [(ngModel)]="selectedDevice" (change)="onChange($event)">
    <option *ngFor="#i of devices">{{i}}</option>
</select>

onChange($event) {
    console.log(this.selectedDevice);
    // I want to do something here for new selectedDevice, but what I
    // got here is always last selection, not the one I just select.
}
```

**[Mark Rajcok](https://stackoverflow.com/users/215945) answered,**

If you don’t need two-way data-binding:

```
<select (change)="onChange($event.target.value)">
    <option *ngFor="let i of devices">{{i}}</option>
</select>

onChange(deviceValue) {
    console.log(deviceValue);
}
```

For two-way data-binding, separate the event and property bindings:

```
<select [ngModel]="selectedDevice" (ngModelChange)="onChange($event)" name="sel2">
    <option [value]="i" *ngFor="let i of devices">{{i}}</option>
</select>

export class AppComponent {
  devices = 'one two three'.split(' ');
  selectedDevice = 'two';
  onChange(newValue) {
    console.log(newValue);
    this.selectedDevice = newValue;
    // ... do other stuff here ...
}
```

If `devices` is array of objects, bind to `ngValue` instead of `value`:

```
<select [ngModel]="selectedDeviceObj" (ngModelChange)="onChangeObj($event)" name="sel3">
  <option [ngValue]="i" *ngFor="let i of deviceObjects">{{i.name}}</option>
</select>
{{selectedDeviceObj | json}}

export class AppComponent {
  deviceObjects = [{name: 1}, {name: 2}, {name: 3}];
  selectedDeviceObj = this.deviceObjects[1];
  onChangeObj(newObj) {
    console.log(newObj);
    this.selectedDeviceObj = newObj;
    // ... do other stuff here ...
  }
}
```

[Plunker](http://plnkr.co/edit/VbJUBkqAlS8UPVgh4bqV?p=preview) — does not use `<form>`

[Plunker](http://plnkr.co/edit/pv5j4b1NFyTGFkxHUSga?p=preview) - uses `<form>` and uses the new forms API

**[Source](https://stackoverflow.com/questions/33700266)**

**#27. Angular exception: Can’t bind to ‘ngForIn’ since it isn’t a known native property**

**[Mark Rajcok](https://stackoverflow.com/users/215945/mark-rajcok) asked,**

What am I doing wrong?

```
import {bootstrap, Component} from 'angular2/angular2'

@Component({
  selector: 'conf-talks',
  template: `<div *ngFor="let talk in talks">
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
Can't bind to 'ngForIn' since it isn't a known native property
("<div [ERROR ->]*ngFor="let talk in talks">
```

**[Mark Rajcok](https://stackoverflow.com/users/215945) answered,**

Since this is at least the third time I’ve wasted more than 5 min on this problem I figured I’d post the Q & A. I hope it helps someone else down the road… probably me!

I typed `in` instead of `of` in the ngFor expression.

**Befor 2-beta.17**, it should be:

`<div *ngFor="#talk of talks">`

As of beta.17, use the `let` syntax instead of `#`. See the UPDATE further down for more info.

Note that the ngFor syntax “desugars” into the following:

```
<template ngFor #talk [ngForOf]="talks">
  <div>...</div>
</template>
```

If we use `in` instead, it turns into

```
<template ngFor #talk [ngForIn]="talks">
  <div>...</div>
</template>
```

Since `ngForIn` isn't an attribute directive with an input property of the same name (like `ngIf`), Angular then tries to see if it is a (known native) property of the `template` element, and it isn't, hence the error.

**UPDATE** — as of 2-beta.17, use the `let` syntax instead of `#`. This updates to the following:

`<div *ngFor="let talk of talks">`

Note that the ngFor syntax “desugars” into the following:

```
<template ngFor let-talk [ngForOf]="talks">
  <div>...</div>
</template>
```

If we use `in` instead, it turns into

```
<template ngFor let-talk [ngForIn]="talks">
  <div>...</div>
</template>
```

**[Source](https://stackoverflow.com/questions/34561168)**

**#28. `*ngIf` and `*ngFor` on same element causing error**

**[garethdn](https://stackoverflow.com/users/1128290/garethdn) asked,**

I’m having a problem with trying to use Angular’s `*ngFor` and `*ngIf` on the same element.

When trying to loop through the collection in the `*ngFor`, the collection is seen as `null` and consequently fails when trying to access its properties in the template.

```
@Component({
  selector: 'shell',
  template: `
    <h3>Shell</h3><button (click)="toggle()">Toggle!</button>
    
    <div *ngIf="show" *ngFor="let thing of stuff">
      <span>{{thing.name}}</span>
    </div>
  `
})

export class ShellComponent implements OnInit {

  public stuff:any[] = [];
  public show:boolean = false;
  
  constructor() {}
  
  ngOnInit() {
    this.stuff = [
      { name: 'abc', id: 1 },
      { name: 'huo', id: 2 },
      { name: 'bar', id: 3 },
      { name: 'foo', id: 4 },
      { name: 'thing', id: 5 },
      { name: 'other', id: 6 },
    ]
  }
  
  toggle() {
    this.show = !this.show;
  }
  
  log(thing) {
    console.log(thing);
  }
  
}
```

I know the easy solution is to move the `*ngIf` up a level but for scenarios like looping over list items in a `ul`, I'd end up with either an empty `li` if the collection is empty, or my `li`s wrapped in redundant container elements.

Example at this [plnkr](http://plnkr.co/edit/C5tZ8mD3iWczVvWkWycH?p=preview).

Note the console error:

`EXCEPTION: TypeError: Cannot read property 'name' of null in [{{thing.name}} in ShellComponent@5:12]`

Am I doing something wrong or is this a bug?

**[Günter Zöchbauer](https://stackoverflow.com/users/217408) answered,**

Angular2 doesn’t support more than one structural directive on the same element.

As a workaround use the `<ng-container>` element that allows you to use separate elements for each structural directive, but **it is not stamped to the DOM**.

```
<ng-container *ngIf="show">
  <div *ngFor="let thing of stuff">
    <span>{{thing.name}}</span>
  </div>
</ng-container>
```

`<ng-template>` (`<template>` before Angular4) allows to do the same but with a different syntax which is confusing and no longer recommended

```
<ng-template [ngIf]="show">
  <div *ngFor="let thing of stuff">
    <span>{{thing.name}}</span>
  </div>
</ng-template>
```

**[Source](https://stackoverflow.com/questions/34657821)**

**#29. What is the Angular equivalent to an AngularJS $watch?**

**[Erwin](https://stackoverflow.com/users/1716567/erwin) asked,**

In AngularJS you were able to specify watchers to observe changes in scope variables using the `$watch` function of the `$scope`. What is the equivalent of watching for variable changes (in, for example, component variables) in Angular?

**[Mark Rajcok](https://stackoverflow.com/users/215945) answered,**

In Angular 2, change detection is automatic… `$scope.$watch()` and `$scope.$digest()` R.I.P.

Unfortunately, the Change Detection section of the dev guide is not written yet (there is a placeholder near the bottom of the [Architecture Overview](https://angular.io/docs/ts/latest/guide/architecture.html) page, in section “The Other Stuff”).

Here’s my understanding of how change detection works:

* Zone.js “monkey patches the world” — it intercepts all of the asynchronous APIs in the browser (when Angular runs). This is why we can use `setTimeout()` inside our components rather than something like `$timeout`... because `setTimeout()` is monkey patched.
* Angular builds and maintains a tree of “change detectors”. There is one such change detector (class) per component/directive. (You can get access to this object by injecting [`ChangeDetectorRef`](https://angular.io/docs/ts/latest/api/core/index/ChangeDetectorRef-class.html).) These change detectors are created when Angular creates components. They keep track of the state of all of your bindings, for dirty checking. These are, in a sense, similar to the automatic `$watches()` that Angular 1 would set up for {{}} template bindings. Unlike Angular 1, the change detection graph is a directed tree and cannot have cycles (this makes Angular 2 much more performant, as we'll see below).
* When an event fires (inside the Angular zone), the code we wrote (the event handler callback) runs. It can update whatever data it wants to — the shared application model/state and/or the component’s view state.
* After that, because of the hooks Zone.js added, it then runs Angular’s change detection algorithm. By default (i.e., if you are not using the `onPush` change detection strategy on any of your components), every component in the tree is examined once (TTL=1)... from the top, in depth-first order. (Well, if you're in dev mode, change detection runs twice (TTL=2). See [`ApplicationRef.tick()`](https://angular.io/docs/ts/latest/api/core/index/ApplicationRef-class.html#!#tick-anchor) for more about this.) It performs dirty checking on all of your bindings, using those change detector objects.
* Lifecycle hooks are called as part of change detection. If the component data you want to watch is a primitive input property (String, boolean, number), you can implement `ngOnChanges()` to be notified of changes. If the input property is a reference type (object, array, etc.), but the reference didn't change (e.g., you added an item to an existing array), you'll need to implement `ngDoCheck()` (see [this SO answer](https://stackoverflow.com/a/34298708/215945) for more on this). You should only change the component's properties and/or properties of descendant components (because of the single tree walk implementation -- i.e., unidirectional data flow). Here's a [plunker](http://plnkr.co/edit/XWBSvE0NoQlRuOsXuOm0?p=preview) that violates that. Stateful pipes can also [trip you up](https://stackoverflow.com/questions/34456430/ngfor-doesnt-update-data-with-pipe-in-angular2/34497504#34497504) here.
* For any binding changes that are found, the Components are updated, and then the DOM is updated. Change detection is now finished.
* The browser notices the DOM changes and updates the screen.

Other references to learn more:

* [Angular’s $digest is reborn in the newer version of Angular](https://blog.angularindepth.com/angulars-digest-is-reborn-in-the-newer-version-of-angular-718a961ebd3e) — explains how the ideas from AngularJS are mapped to Angular
* [Everything you need to know about change detection in Angular](https://blog.angularindepth.com/everything-you-need-to-know-about-change-detection-in-angular-8006c51d206f) — explains in great detail how change detection works under the hood
* [Change Detection Explained](http://blog.thoughtram.io/angular/2016/02/22/angular-2-change-detection-explained.html) — Thoughtram blog Feb 22, 2016 — probably the best reference out there
* Savkin’s [Change Detection Reinvented](https://www.youtube.com/watch?v=jvKGQSFQf10) video — definitely watch this one
* [How does Angular 2 Change Detection Really Work?](http://blog.jhades.org/how-does-angular-2-change-detection-really-work/)- jhade’s blog Feb 24, 2016
* [Brian’s video](https://www.youtube.com/watch?v=3IqtmUscE_U) and [Miško’s video](https://www.youtube.com/watch?v=V9Bbp6Hh2YE) about Zone.js. Brian’s is about Zone.js. Miško’s is about how Angular 2 uses Zone.js to implement change detection. He also talks about change detection in general, and a little bit about `onPush`.
* Victor Savkins blog posts: [Change Detection in Angular 2](http://victorsavkin.com/post/110170125256/change-detection-in-angular-2), [Two phases of Angular 2 applications](http://victorsavkin.com/post/114168430846/two-phases-of-angular-2-applications), [Angular, Immutability and Encapsulation](http://victorsavkin.com/post/110170125256/change-detection-in-angular-2). He covers a lot of ground quickly, but he can be terse at times, and you’re left scratching your head, wondering about the missing pieces.
* [Ultra Fast Change Detection](https://docs.google.com/document/d/1QKTbyVNPyRW-otJJVauON4TFMHpl0zNBPkJcTcfPJWg/edit) (Google doc) — very technical, very terse, but it describes/sketches the ChangeDetection classes that get built as part of the tree

**[Source](https://stackoverflow.com/questions/34569094)**

**#30. Importing lodash into angular2 + typescript application**


**[Davy](https://stackoverflow.com/users/1854793/davy) asked,**

I am having a hard time trying to get the lodash modules imported. I’ve setup my project using npm+gulp, and keep hitting the same wall. I’ve tried the regular lodash, but also lodash-es.

The lodash npm package: (has an index.js file in the package root folder)

`import * as _ from 'lodash';`

Results in:

`error TS2307: Cannot find module 'lodash'.`

The lodash-es npm package: (has a defaut export in lodash.js i the package root folder)

`import * as _ from 'lodash-es/lodash';`

Results in:

`error TS2307: Cannot find module 'lodash-es'.`

Both the gulp task and webstorm report the same issue.

Funny fact, this returns no error:

`import 'lodash-es/lodash';`

… but of course there is no “_” …

My tsconfig.json file:

```
{
  "compilerOptions": {
    "target": "es5",
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
```

My gulpfile.js:

```
var gulp = require('gulp'),
    ts = require('gulp-typescript'),
    uglify = require('gulp-uglify'),
    sourcemaps = require('gulp-sourcemaps'),
    tsPath = 'app/**/*.ts';
    
gulp.task('ts', function () {
    var tscConfig = require('./tsconfig.json');
    
    gulp.src([tsPath])
        .pipe(sourcemaps.init())
        .pipe(ts(tscConfig.compilerOptions))
        .pipe(sourcemaps.write('./../js'));
});

gulp.task('watch', function() {
    gulp.watch([tsPath], ['ts']);
});

gulp.task('default', ['ts', 'watch']);
```

If i understand correctly, moduleResolution:’node’ in my tsconfig should point the import statements to the node_modules folder, where lodash and lodash-es are installed. I’ve also tried lots of different ways to import: absolute paths, relative paths, but nothing seems to work. Any ideas?

If necessary i can provide a small zip file to illustrate the problem.

**[Taytay](https://stackoverflow.com/users/544130) answered,**

Here is how to do this as of Typescript 2.0: (tsd and typings are being deprecated in favor of the following):

```
$ npm install --save lodash

# This is the new bit here: 
$ npm install --save @types/lodash
```

Then, in your .ts file:

Either:

`import * as _ from "lodash";`

Or (as suggested by @Naitik):

`import _ from "lodash";`

I’m not positive what the difference is. We use and prefer the first syntax. However, some report that the first syntax doesn’t work for them, and someone else has commented that the latter syntax is incompatible with lazy loaded webpack modules. YMMV.

Edit on Feb 27th, 2017:

According to @Koert below, `import * as _ from "lodash";` is the only working syntax as of Typescript 2.2.1, lodash 4.17.4, and @types/lodash 4.14.53. He says that the other suggested import syntax gives the error "has no default export".

**[Source](https://stackoverflow.com/questions/34660265)**

**#31. How to detect a route change in Angular?**

**[AngularM](https://stackoverflow.com/users/1590389/angularm) asked,**

I am looking to detect a route change in my `AppComponent`.

Thereafter I will check the global user token to see if he is logged in. Then I can redirect the user if he is not logged in.

**[Ludohen](https://stackoverflow.com/users/1048274) answered,**

In Angular 2 you can `subscribe` (Rx event) to a Router instance. So you can do things like

```
class MyClass {
  constructor(private router: Router) {
    router.subscribe((val) => /*whatever*/)
  }
}
```

**Edit** (since rc.1)

```
class MyClass {
  constructor(private router: Router) {
    router.changes.subscribe((val) => /*whatever*/)
  }
}
```

**Edit 2** (since 2.0.0)

see also : [Router.events doc](https://angular.io/api/router/RouterEvent)

```
class MyClass {
  constructor(private router: Router) {
    router.events.subscribe((val) => {
        // see also 
        console.log(val instanceof NavigationEnd) 
    });
  }
}
```

**[Source](https://stackoverflow.com/questions/33520043)**

**#32. Global Events in Angular**

**[skovmand](https://stackoverflow.com/users/3368477/skovmand) asked,**

Is there no equivalent to `$scope.emit()` or `$scope.broadcast()` in Angular?

I know the `EventEmitter` functionality, but as far as I understand that will just emit an event to the parent HTML element.

What if I need to communicate between fx. siblings or between a component in the root of the DOM and an element nested several levels deep?

**[pixelbits](http://) answered,**

There is no equivalent to `$scope.emit()` or `$scope.broadcast()` from AngularJS. EventEmitter inside of a component comes close, but as you mentioned, it will only emit an event to the immediate parent component.

In Angular, there are other alternatives which I’ll try to explain below.

@Input() bindings allows the application model to be connected in a directed object graph (root to leaves). The default behavior of a component’s change detector strategy is to propagate all changes to an application model for all bindings from any connected component.

Aside: There are two types of models: View Models and Application Models. An application model is connected through @Input() bindings. A view model is a just a component property (not decorated with @Input()) which is bound in the component’s template.

To answer your questions:

What if I need to communicate between sibling components?

* **Shared Application Model:** Siblings can communicate through a shared application model (just like angular 1). For example, when one sibling makes a change to a model, the other sibling that has bindings to the same model is automatically updated.
* **Component Events:** Child components can emit an event to the parent component using @Output() bindings. The parent component can handle the event, and manipulate the application model or it’s own view model. Changes to the Application Model are automatically propagated to all components that directly or indirectly bind to the same model.
* **Service Events:** Components can subscribe to service events. For example, two sibling components can subscribe to the same service event and respond by modifying their respective models. More on this below.

How can I communicate between a Root component and a component nested several levels deep?

* **Shared Application Model:** The application model can be passed from the Root component down to deeply nested sub-components through @Input() bindings. Changes to a model from any component will automatically propagate to all components that share the same model.
* **Service Events:** You can also move the EventEmitter to a shared service, which allows any component to inject the service and subscribe to the event. That way, a Root component can call a service method (typically mutating the model), which in turn emits an event. Several layers down, a grand-child component which has also injected the service and subscribed to the same event, can handle it. Any event handler that changes a shared Application Model, will automatically propagate to all components that depend on it. This is probably the closest equivalent to `$scope.broadcast()` from Angular 1. The next section describes this idea in more detail.

**Example of an Observable Service that uses Service Events to Propagate Changes**

Here is an example of an observable service that uses service events to propagate changes. When a TodoItem is added, the service emits an event notifying its component subscribers.

```
export class TodoItem {
    constructor(public name: string, public done: boolean) {
    }
}
export class TodoService {
    public itemAdded$: EventEmitter<TodoItem>;
    private todoList: TodoItem[] = [];
    
    constructor() {
        this.itemAdded$ = new EventEmitter();
    }
    
    public list(): TodoItem[] {
        return this.todoList;
    }
    
    public add(item: TodoItem): void {
        this.todoList.push(item);
        this.itemAdded$.emit(item);
    }
}
```

Here is how a root component would subscribe to the event:

```
export class RootComponent {
    private addedItem: TodoItem;
    constructor(todoService: TodoService) {
        todoService.itemAdded$.subscribe(item => this.onItemAdded(item));
    }
    
    private onItemAdded(item: TodoItem): void {
        // do something with added item
        this.addedItem = item;
    }
}
```

A child component nested several levels deep would subscribe to the event in the same way:

```
export class GrandChildComponent {
    private addedItem: TodoItem;
    constructor(todoService: TodoService) {
        todoService.itemAdded$.subscribe(item => this.onItemAdded(item));
    }
    
    private onItemAdded(item: TodoItem): void {
        // do something with added item
        this.addedItem = item;
    }
}
```

Here is the component that calls the service to trigger the event (it can reside anywhere in the component tree):

```
@Component({
    selector: 'todo-list',
    template: `
         <ul>
            <li *ngFor="#item of model"> {{ item.name }}
            </li>
         </ul>
        <br />
        Add Item <input type="text" #txt /> <button (click)="add(txt.value); txt.value='';">Add</button>
    `
})
export class TriggeringComponent{
    private model: TodoItem[];
    
    constructor(private todoService: TodoService) {
        this.model = todoService.list();
    }
    
    add(value: string) {
        this.todoService.add(new TodoItem(value, false));
    }
}
```

Reference: [Change Detection in Angular](http://victorsavkin.com/post/110170125256/change-detection-in-angular-2)

**[Source](https://stackoverflow.com/questions/34700438)**

**#33. What are differences between SystemJS and Webpack?**

**[smartmouse](https://stackoverflow.com/users/2516399/smartmouse) asked,**

I’m creating my first Angular application and I would figure out what is the role of the module loaders. Why we need them? I tried to search and search on Google and I can’t understand why we need to install one of them to run our application?

Couldn’t it be enough to just use `import` to load stuff from node modules?

I have followed [this tutorial](https://angular.io/docs/ts/latest/quickstart.html#!#systemjs) (that uses SystemJS) and it makes me to use `systemjs.config.js` file:

```
/**
 * System configuration for Angular samples
 * Adjust as necessary for your application needs.
 */
(function(global) {
  // map tells the System loader where to look for things
  var map = {
    'app':                        'transpiled', // 'dist',
    '@angular':                   'node_modules/@angular',
    'angular2-in-memory-web-api': 'node_modules/angular2-in-memory-web-api',
    'rxjs':                       'node_modules/rxjs'
  };
  // packages tells the System loader how to load when no filename and/or no extension
  var packages = {
    'app':                        { main: 'main.js',  defaultExtension: 'js' },
    'rxjs':                       { defaultExtension: 'js' },
    'angular2-in-memory-web-api': { main: 'index.js', defaultExtension: 'js' },
  };
  var ngPackageNames = [
    'common',
    'compiler',
    'core',
    'forms',
    'http',
    'platform-browser',
    'platform-browser-dynamic',
    'router',
    'router-deprecated',
    'upgrade',
  ];
  // Individual files (~300 requests):
  function packIndex(pkgName) {
    packages['@angular/'+pkgName] = { main: 'index.js', defaultExtension: 'js' };
  }
  // Bundled (~40 requests):
  function packUmd(pkgName) {
    packages['@angular/'+pkgName] = { main: '/bundles/' + pkgName + '.umd.js', defaultExtension: 'js' };
  }
  // Most environments should use UMD; some (Karma) need the individual index files
  var setPackageConfig = System.packageWithIndex ? packIndex : packUmd;
  // Add package entries for angular packages
  ngPackageNames.forEach(setPackageConfig);
  var config = {
    map: map,
    packages: packages
  };
  System.config(config);
})(this);
```

Why we need this configuration file?

Why we need SystemJS (or WebPack or others)?

Finally, in your opinion what is the better?

**[Thierry Templier](https://stackoverflow.com/users/1873365) answered,**

If you go to the SystemJS Github page, you will see the description of the tool:

`Universal dynamic module loader - loads ES6 modules, AMD, CommonJS and global scripts in the browser and NodeJS.`

Because you use modules in TypeScript or ES6, you need a module loader. In the case of SystemJS, the `systemjs.config.js` allows us to configure the way in which module names are matched with their corresponding files.

This configuration file (and SystemJS) is necessary if you explicitly use it to import the main module of your application:

```
<script>
  System.import('app').catch(function(err){ console.error(err); });
</script>
```

When using TypeScript, and configuring the compiler to the `commonjs` module, the compiler creates code that is no longer based on SystemJS. In this example, the typescript compiler config file would appear like this:

```
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs", // <------
    "moduleResolution": "node",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "removeComments": false,
    "noImplicitAny": false
  }
}
```

Webpack is a flexible module bundler. This means that it goes further and doesn’t only handle modules but also provides a way to package your application (concat files, uglify files, …). It also provides a dev server with load reload for development

SystemJS and Webpack are different but with SystemJS, you still have work to do (with [Gulp](http://gulpjs.com/) or [SystemJS builder](https://github.com/systemjs/builder) for example) to package your Angular2 application for production.

[Source](https://stackoverflow.com/questions/38263406)

**#34. Angular: Can’t find Promise, Map, Set and Iterator**

**[Stav Alfi](https://stackoverflow.com/users/806963/stav-alfi) asked,**

After installing Angular, the Typescript compiler keep getting some errors about not finding `Promise`, `Map`, `Set` and `Iterator`.

Until now I ignored them but now I need `Promise` so my code can work.

```
import {Component} from 'angular2/core';
@Component({
    selector: 'greeting-cmp',
    template: `<div>{{ asyncGreeting | async}}</div>`
})
export class GreetingCmp {
    asyncGreeting: Promise<string> = new Promise(resolve => {
// after 1 second, the promise will resolve
        window.setTimeout(() => resolve('hello'), 1000);
    });
}

Additional information:
npm -v is 2.14.12
node -v is v4.3.1
typescript v is 1.6
```

The errors:

```
................ERROS OF MY CODE.................
    C:\Users\armyTik\Desktop\angular2\greeting_cmp.ts
    Error:(7, 20) TS2304: Cannot find name 'Promise'.
    Error:(7, 42) TS2304: Cannot find name 'Promise'.
    .........................................
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\platform\browser.d.ts
    Error:(77, 90) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\core\application_ref.d.ts
    Error:(83, 60) TS2304: Cannot find name 'Promise'.
    Error:(83, 146) TS2304: Cannot find name 'Promise'.
    Error:(96, 51) TS2304: Cannot find name 'Promise'.
    Error:(96, 147) TS2304: Cannot find name 'Promise'.
    Error:(133, 90) TS2304: Cannot find name 'Promise'.
    Error:(171, 81) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\core\change_detection\parser\locals.d.ts
    Error:(3, 14) TS2304: Cannot find name 'Map'.
    Error:(4, 42) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\core\debug\debug_node.d.ts
    Error:(14, 13) TS2304: Cannot find name 'Map'.
    Error:(24, 17) TS2304: Cannot find name 'Map'.
    Error:(25, 17) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\core\di\provider.d.ts
    Error:(436, 103) TS2304: Cannot find name 'Map'.
    Error:(436, 135) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\core\linker\compiler.d.ts
    Error:(12, 50) TS2304: Cannot find name 'Promise'.
    Error:(16, 41) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\core\linker\dynamic_component_loader.d.ts
    Error:(108, 136) TS2304: Cannot find name 'Promise'.
    Error:(156, 150) TS2304: Cannot find name 'Promise'.
    Error:(197, 128) TS2304: Cannot find name 'Promise'.
    Error:(203, 127) TS2304: Cannot find name 'Promise'.
    Error:(204, 141) TS2304: Cannot find name 'Promise'.
    Error:(205, 119) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\core\render\api.d.ts
    Error:(13, 13) TS2304: Cannot find name 'Map'.
    Error:(14, 84) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\facade\async.d.ts
    Error:(27, 33) TS2304: Cannot find name 'Promise'.
    Error:(28, 45) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\facade\collection.d.ts
    Error:(1, 25) TS2304: Cannot find name 'MapConstructor'.
    Error:(2, 25) TS2304: Cannot find name 'SetConstructor'.
    Error:(4, 27) TS2304: Cannot find name 'Map'.
    Error:(4, 39) TS2304: Cannot find name 'Map'.
    Error:(7, 9) TS2304: Cannot find name 'Map'.
    Error:(8, 30) TS2304: Cannot find name 'Map'.
    Error:(11, 43) TS2304: Cannot find name 'Map'.
    Error:(12, 27) TS2304: Cannot find name 'Map'.
    Error:(14, 23) TS2304: Cannot find name 'Map'.
    Error:(15, 25) TS2304: Cannot find name 'Map'.
    Error:(95, 41) TS2304: Cannot find name 'Set'.
    Error:(96, 22) TS2304: Cannot find name 'Set'.
    Error:(97, 25) TS2304: Cannot find name 'Set'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\facade\lang.d.ts
    Error:(13, 17) TS2304: Cannot find name 'Map'.
    Error:(14, 17) TS2304: Cannot find name 'Set'.
    Error:(78, 59) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\facade\promise.d.ts
    Error:(2, 14) TS2304: Cannot find name 'Promise'.
    Error:(7, 32) TS2304: Cannot find name 'Promise'.
    Error:(8, 38) TS2304: Cannot find name 'Promise'.
    Error:(9, 35) TS2304: Cannot find name 'Promise'.
    Error:(9, 93) TS2304: Cannot find name 'Promise'.
    Error:(10, 34) TS2304: Cannot find name 'Promise'.
    Error:(11, 32) TS2304: Cannot find name 'Promise'.
    Error:(11, 149) TS2304: Cannot find name 'Promise'.
    Error:(12, 43) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\http\headers.d.ts
    Error:(43, 59) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\http\url_search_params.d.ts
    Error:(11, 16) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\platform\browser\browser_adapter.d.ts
    Error:(75, 33) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\angular2\src\platform\dom\dom_adapter.d.ts
    Error:(85, 42) TS2304: Cannot find name 'Map'.
    C:\Users\armyTik\Desktop\angular2\node_modules\rxjs\CoreOperators.d.ts
    Error:(35, 67) TS2304: Cannot find name 'Promise'.
    Error:(50, 66) TS2304: Cannot find name 'Promise'.
    Error:(89, 67) TS2304: Cannot find name 'Promise'.
    Error:(94, 38) TS2304: Cannot find name 'Promise'.
    Error:(94, 50) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\rxjs\Observable.d.ts
    Error:(46, 62) TS2304: Cannot find name 'Promise'.
    Error:(47, 42) TS2304: Cannot find name 'Iterator'.
    Error:(103, 74) TS2304: Cannot find name 'Promise'.
    Error:(103, 84) TS2304: Cannot find name 'Promise'.
    Error:(143, 66) TS2304: Cannot find name 'Promise'.
    Error:(158, 65) TS2304: Cannot find name 'Promise'.
    Error:(201, 66) TS2304: Cannot find name 'Promise'.
    Error:(206, 38) TS2304: Cannot find name 'Promise'.
    Error:(206, 50) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\rxjs\observable\ForkJoinObservable.d.ts
    Error:(6, 50) TS2304: Cannot find name 'Promise'.
    Error:(7, 58) TS2304: Cannot find name 'Promise'.
    C:\Users\armyTik\Desktop\angular2\node_modules\rxjs\observable\FromObservable.d.ts
    Error:(7, 38) TS2304: Cannot find name 'Promise'.
    Error:(7, 51) TS2304: Cannot find name 'Iterator'.
    C:\Users\armyTik\Desktop\angular2\node_modules\rxjs\observable\PromiseObservable.d.ts
    Error:(9, 31) TS2304: Cannot find name 'Promise'.
    Error:(10, 26) TS2304: Cannot find name 'Promise'.
```

**[Kris Hollenbeck](https://stackoverflow.com/users/1949099) answered,**

**Angular RC4 — Angular ^2.0.0 with Typescript 2.0.0**

Updated 9/19/2016

To get this to work with typescript 2.0.0, I did the following.

`npm install --save-dev @types/core-js`

**tsconfig.json**

```
"compilerOptions": {
    "declaration": false,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "mapRoot": "./",
    "module": "es6",
    "moduleResolution": "node",
    "noEmitOnError": true,
    "noImplicitAny": false,
    "outDir": "../dist/out-tsc",
    "sourceMap": true,
    "target": "es5",
    "typeRoots": [
      "../node_modules/@types"
    ],
    "types": [
      "core-js"
    ]
  }
```

More about @types with typescript 2.0.0.

1. [https://blogs.msdn.microsoft.com/typescript/2016/06/15/the-future-of-declaration-files/](https://blogs.msdn.microsoft.com/typescript/2016/06/15/the-future-of-declaration-files/)
2. [https://www.npmjs.com/~types](https://www.npmjs.com/~types)

Install Example:

`npm install --save-dev @types/core-js`

**Duplicate Identifier errors**

This is most likely because duplicate ecmascript 6 typings are already being imported from somewhere else most likely an old es6-shim.

Double check `typings.d.ts` make sure there are no references to `es6`. Remove any reference to `es6` from your typings directory if you have one.

**For Example:**

This will conflict with `types:['core-js']` in typings.json.

```
{
  "globalDependencies": {
    "core-js": "registry:dt/core-js#0.0.0+20160602141332" 
    // es6-shim will also conflict
  }
}
```

Including `core-js` in the types array in `tsconfig.json` should be the only place it is imported from.

**Angular CLI 1.0.0-beta.30**

If you are using the Angular-CLI, remove the lib array in `typings.json`. This seems to conflict with declaring core-js in types.

```
"compilerOptions" : {
  ...
  // removed "lib": ["es6", dom"],
  ...
},
"types" : ["core-js"]
```

**Webstorm/Intellij Users using the Angular CLI**

Make sure the built in typescript compiler is disabled. This will conflict with the CLI. To compile your typescript with the CLI you can setup a `ng serve` configuration.

**Tsconfig compilerOptions lib vs types**

If you prefer not to install core js type definitions there are some es6 libraries that come included with typescript. Those are used via the `lib: []` property in tsconfig.

See here for example: [https://www.typescriptlang.org/docs/handbook/compiler-options.html](https://www.typescriptlang.org/docs/handbook/compiler-options.html)

`Note: If --lib is not specified a default library is injected. The default library injected is: ? For --target ES5: DOM,ES5,ScriptHost ? For --target ES6: DOM,ES6,DOM.Iterable,ScriptHost`

**tl;dr**

Short answer either `"lib": [ "es6", "dom" ]` or `"types": ["core-js"]` can be used to resolve `can't find Promise,Map, Set and Iterator`. Using both however will cause duplicate identifier errors.

**[Source](https://stackoverflow.com/questions/35660498)**

**#35. How to detect when an @Input() value changes in Angular?**

**[Jon Catmull](https://stackoverflow.com/users/3604283/jon-catmull) asked,**

I have a parent component (**CategoryComponent**), a child component (**videoListComponent**) and an ApiService.

I have most of this working fine i.e. each component can access the json api and get its relevant data via observables.

Currently video list component just gets all videos, I would like to filter this to just videos in a particular category, I achieved this by passing the categoryId to the child via `@Input()`.

CategoryComponent.html

`<video-list *ngIf="category" [categoryId]="category.id"></video-list>`

This works and when the parent CategoryComponent category changes then the categoryId value gets passed through via `@Input()` but I then need to detect this in VideoListComponent and re-request the videos array via APIService (with the new categoryId).

In AngularJS I would have done a `$watch` on the variable. What is the best way to handle this?

**[Alan C. S](https://stackoverflow.com/users/2107767). answered,**

**Actually, there are two ways of detecting and acting up on when an input changes in the child component in angular2+ :**

1. You can use the **ngOnChanges() lifecycle method** as also mentioned in older answers: `@Input() categoryId: string; ngOnChanges(changes: SimpleChanges) { this.doSomething(changes.categoryId.currentValue); // You can also use categoryId.previousValue and // categoryId.firstChange for comparing old and new values }`
2. Documentation Links: [ngOnChanges](https://angular.io/api/core/OnChanges), [SimpleChanges](https://angular.io/api/core/SimpleChanges), [SimpleChange](https://angular.io/api/core/SimpleChange) Demo Example: Look at [this plunker](https://plnkr.co/edit/LUr2bMQRhhAeuLN3R5B6?p=preview)
3. Alternately, you can also use an **input property setter** as follows: `private _categoryId: string; @Input() set categoryId(value: string) { this._categoryId = value; this.doSomething(this._categoryId); } get categoryId(): string { return this._categoryId; }`
4. Documentation Link: Look [here](https://angular.io/guide/component-interaction#intercept-input-property-changes-with-a-setter).
5. Demo Example: Look at [this plunker](https://plnkr.co/edit/EsolgwJVuvOUx6rKk8d4?p=preview).

**WHICH APPROACH SHOULD YOU USE?**

If your component has several inputs, then, if you use ngOnChanges(), you will get all changes for all the inputs at once within ngOnChanges(). Using this approach, you can also compare current and previous values of the input that has changed and take actions accordingly.

However, if you want to do something when only a particular single input changes (and you don’t care about the other inputs), then it might be simpler to use an input property setter. However, this approach does not provide a built in way to compare previous and current values of the changed input (which you can do easily with the ngOnChanges lifecycle method).

**EDIT 2017–07–25: ANGULAR CHANGE DETECTION MAY STILL NOT FIRE UNDER SOME CIRCUMSTANCES**

Normally, change detection for both setter and ngOnChanges will fire whenever the parent component changes the data it passes to the child, **provided that the data is a JS primitive datatype(string, number, boolean)**. However, in the following scenarios, it will not fire and you have to take extra actions in order to make it work.

1. If you are using a nested object or array (instead of a JS primitive data type) to pass data from Parent to Child, change detection (using either setter or ngchanges) might not fire, as also mentioned in the answer by user: muetzerich. For solutions look here.
2. If you are mutating data outside of the angular context (i.e., externally), then angular will not know of the changes. You may have to use ChangeDetectorRef or NgZone in your component for making angular aware of external changes and thereby triggering change detection. Refer to this.

**[Source](https://stackoverflow.com/questions/38571812)**

**#36. How to pass URL arguments (query string) to a HTTP request on Angular**

**[Miguel Lattuada](https://stackoverflow.com/users/3276721/miguel-lattuada) asked,**

Hi guys I’m creating a HTTP request on Angular, but I do not know how to add URL arguments (query string) to it.

```
this.http.get(StaticSettings.BASE_URL).subscribe(
  (response) => this.onGetForecastResult(response.json()),
  (error) => this.onGetForecastError(error.json()),
  () => this.onGetForecastComplete()
);
```

Now my StaticSettings.BASE_URL is something like a url with no query string like: [http://atsomeplace.com/](http://atsomeplace.com/) but I want it to be [http://atsomeplace.com/?var1=val1&var2=val2](http://atsomeplace.com/?var1=val1&var2=val2)

Where var1, and var2 fit on my Http request object? I want to add them like an object.

```
{
  query: {
    var1: val1,
    var2: val2
  }
}
```

and then just the Http module do the job to parse it into URL query string.

**[toskv](https://stackoverflow.com/users/5152732) answered,**

The **[HttpClient](https://angular.io/api/common/http/HttpClient)** methods allow you to set the **params** in it’s options.

You can configure it by importing the **[HttpClientModule](https://angular.io/api/common/http)** from the @angular/common/http package.

```
import {HttpClientModule} from '@angular/common/http';

@NgModule({
  imports: [ BrowserModule, HttpClientModule ],
  declarations: [ App ],
  bootstrap: [ App ]
})
export class AppModule {}
```

After that you can inject the **HttpClient** and use it to do the request.

`import {HttpClient} from '@angular/common/http'`

```
import {HttpClient} from '@angular/common/http'

@Component({
  selector: 'my-app',
  template: `
    <div>
      <h2>Hello {{name}}</h2>
    </div>
  `,
})
export class App {
  name:string;
  constructor(private httpClient: HttpClient) {
    this.httpClient.get('/url', {
      params: {
        appid: 'id1234',
        cnt: '5'
      },
      observe: 'response'
    })
    .toPromise()
    .then(response => {
      console.log(response);
    })
    .catch(console.log);
  }
}
```

You can find a working example [here](https://plnkr.co/edit/G4mczOLOHfVYKpuaWee3?p=preview).

For angular versions prior to version 4 you can do the same using the **Http** service.

The **Http.get** method takes an object that implements [RequestOptionsArgs](https://angular.io/docs/ts/latest/api/http/index/RequestOptionsArgs-interface.html) as a second parameter.

The **search** field of that object can be used to set a string or a [URLSearchParams](https://angular.io/docs/ts/latest/api/http/index/URLSearchParams-class.html) object.

An example:

```
// Parameters obj-
 let params: URLSearchParams = new URLSearchParams();
 params.set('appid', StaticSettings.API_KEY);
 params.set('cnt', days.toString());
 
 //Http request-
 return this.http.get(StaticSettings.BASE_URL, {
   search: params
 }).subscribe(
   (response) => this.onGetForecastResult(response.json()), 
   (error) => this.onGetForecastError(error.json()), 
   () => this.onGetForecastComplete()
 );
```

The documentation for the **Http** class has more details. It can be found [here](https://angular.io/docs/ts/latest/api/http/index/Http-class.html) and an working example [here](https://plnkr.co/edit/pKdztZBHr0wr1YLmmI8P?p=preview).

**[Source](https://stackoverflow.com/questions/34475523)**