---
title: Top 10 Features Of Angular 8
image: "/assets/default-social-image.png"
categories: Angular-8.0
---

One of Javascript's most common frameworks-Angular finally released the latest version of Angular 8 on May 23, 2019. The latest release of the Angular Project of Google has purchased some enticing features that make Angular 8 special relative to its earlier versions. We're going to talk about the top 10 Angular 8 features & updates in this blog.

**History of previous versions of the angular**

Please skip this part and move on to the next–Angular 8 features if you know the history of Angular versions & features before, or if you just want to focus on Angular 8 features.

Angular is one of the most common JavaScript front-end application for web app creation contrasting React & Vue.js. Its first version was released in 2009 and has been around since the last decade, carrying an amazing list of changes and enhancements since then.

The first edition of the application related as AngularJS was released in 2009. While it was not a perfect system at that time, mostly because of its broad package volume, difficult debugging problem, dependency injection stops functioning after code minification, performance issues, and other technical issues.

The competition was tough, so Google's engineering team made many changes to their framework that added really powerful libraries and new features like AOT, tree-shaking for every [AngularJS Development Company](https://www.angularminds.com/angularjs-development-company.html) to do better.

It is not an upgrade of version 1, where Angular 2 has been completely rewritten. It was released with Typescript, a JavaScript superset introduced by Microsoft and selected for development by the Angular team. Typescript is a fantastic javascript writing tool. Angular 2 implemented the hierarchical injection system of dependence as everything is a group in angular, so DI is accomplished through a constructor. The compiler has been modified to optimize template rendering performance, which makes the software run at the maximum speed in JVMs.

The main reason for missing version 3 was to avoid confusion as the core Angular modules are released live on a common GitHub database at @angular/angular with the same version but as separate NPM packages creating misalignment of the version of the router module that was already distributed as version 3.3.0, so team decided to skip version 3 and move forward with [v4](https://www.angularminds.com/blog/article/10-major-features-introduced-in-angular-4.html), aligning all the core packages and helping to avoid any possible confusion in the future.

Apps used fewer space with view-engine improvements and software creation cuts in Angular 4 and run faster than their previous versions. Angular Universal has been launched as the core Angular Module which allows importing functions from the library quickly.

Angular team launched progressive web applications support to their Angular v5 to get the functionality of native mobile apps for mobile web apps along with changes & upgrades in Material Design & integrated construct optimizer to render the software lightweight and quicker by removing unnecessary runtime code.

ng update, Bazel Compiler, Service Worker Support, Angular elements, CLI Workspaces, Animations Performance Improvements, ng add, and Angular Material + CDK components were the major changes in v6.

The Angular 7 version focuses primarily on the Ivy project, but they have not introduced ivy in their version and talking about other major changes such as new CLI, ScrollingModule, DragDropModule, major performance tweak by removing reflect-metadata polyfill that is automatically included in the production and adding by default budget bundles that will notify you when your application reaches size limits. Angular 7 has been upgraded to 3.1, RxjS 6.3 and introduced support for Node 10.


Check [this](https://www.angularminds.com/blog/article/top-10-features-of-angular-7.html) blog on Angular 7

**What’s New in Angular 8**

Angular 8 released with a bunch of functionality and a new set of powerful features that Angular developers can enjoy such as the core module, the Angular Material Library, and the Command Line Interface. As an Angular Console, they enabled major launch partner to run Angular projects, #angular/fire to integrate Firebase with Angular, StackBlitz integrated IDE and NativeScript to build native mobile apps with Angular. Let's summarize what's new in Angular 8 and how to upgrade your Angular 7 apps to v8.

**List of Top 10 Angular 8 Features**

**Preview of Ivy**

When you adopted Angular, you therefore found the word "Ivy." Ivy is a major change to Angular past, an angular renderer that varies significantly from anything because it utilizes gradual DOM. It affects how the code operates dynamically, without our Angular programs having updated. Basically, the Ivy project rewrites the Angular compiler and runtime code in order for better build times, (incremental approach), sizes more compatible with tree-shaking and new potential features like lazy component loading instead of modules.

**How Angular Ivy works on Incremental DOM**

The key idea behind Incremental DOM is to compile a series of instructions for each variable. Such instructions build DOM trees, and when the information shifts, they refresh them in order.

```
@Component({
  selector: 'todos-cmp',
  template: `
    <div *ngFor="let t of todos|async">
        {{t.description}}
    </div>
  `
})
class TodosComponent {
  todos: Observable<Todo[]> = this.store.pipe(select('todos'));
  constructor(private store: Store<AppState>) {}
}
```

Will be compiled into:

```
var TodosComponent = /** @class */ (function () {
  function TodosComponent(store) {
    this.store = store;
    this.todos = this.store.pipe(select('todos'));
  }
  TodosComponent.ngComponentDef = defineComponent({
    type: TodosComponent,
    selectors: [["todos-cmp"]],
    factory: function TodosComponent_Factory(t) {
      return new (t || TodosComponent)(directiveInject(Store));
    },
    consts: 2,
    vars: 3,
    template: function TodosComponent_Template(rf, ctx) {
      if (rf & 1) { /** create dom*/ 
        pipe(1, "async");
        template(0, TodosComponent_div_Template_0, 2, 1, null, _c0);
      } if (rf & 2) { /** create dom*/ 
        elementProperty(0, "ngForOf", bind(pipeBind1(1, 1, ctx.todos)));
      }
    },
    encapsulation: 2
  });
  
  return TodosComponent;
}());
```

The template function contains the instructions rendering and updating the DOM as they are rendering engine.

**Two main concepts of IVY**

Tree shakable: This means removing redundant parts of your code, the component is not understood by the framework. Instead, the instructions are referenced by the component. If it does not apply to a specific instruction, it will never be used in order to remove the missing instruction from the output of the package in smaller packages and shorter load times.

Low Memory Footprint: Incremental DOM does not need any space to make the view if it does not alter the DOM, so when the DOM nodes are inserted or deleted, it allocates the storage. Since most render/template calls do not alter something, they save huge amounts of space.

**Differential loading**

Thanks to Differential Loading of Modern JavaScript, Angular 8 apps will now be more efficient. New Angular CLI generated apps will now have separate bundles for legacy JavaScript (ES5) and modern JavaScript (ES2015+) with differential loading.

The browser will automatically load the correct bundle and will be able to download smaller, more efficient app bundles that load and render faster.



**Angular Router Backwards Compatibility**

Angular 8 feature added Angular router backward compatibility mode to help upgrade the path for large projects and make it easier to move to Angular by allowing lazy loading parts of Angular v1.x apps using $route APIs. In a simple word, we'll be able to upgrade our Angular 1.x apps to Angular 2 + immediately.

**Improved Web Worker Bundling**

Thanks to Angular CLI 8, web workers are included while building the bundles of production that are essential to enhance parallelizability and help increase performance. Therefore, Angular 8.0 adds support for building CLI that provides one bundle for each web worker.

`ng g webWorker <name>`

**Bazel Support**

One of Angular 8's new features is the option of using Bazel to construct the CLI software. Bazel constructed the Angular Project itself.

It is eligible as an opt-in, it should be included in version 9 of @angular / cli.

Bazel key advantages are:

* With the same tool, we can create our backends and frontends.
* Quicker build time The first build will be incredibly slow because Bazel looks for precisely reproducible builds, but concurrent builds will be much quicker and it will be helpful if your device requires several modules and libraries.
* Incremental Build: Codebase will only trigger the smallest possible reconstruction assistance in building and deploying only what has changed rather than the entire App.
* Bazel files can be ejected , they are hidden by default.
* The probability of constructing mobile builds on a project farm (with cache).

**Lazy Loading**

Lazy loading is based on Angular Routing principles because it helps to reduce the size of large files by lazily loading the necessary data. The route configuration uses the @loadChildren property that accepts a string in previous angular versions, and if there was a wrong module name or typo while the code was being written, Angular would not consider it wrong and accept any value as a string until we try to build it.

To overcome that they have added router configuration support for dynamic imports in the latest Angular 8, which allows the use of import statements for lazy loading of the module and this will be understood by the IDEs, webpack, etc.

So Editor can grasp what this syntax is and will know if a mistake happens so we won't have to wait before we create time to realize an error.

**Opt-In Usage Sharing**

Angular CLI should add another new feature I e opt-in application sharing to hold their activities in sync with the needs of the community. That functionality would allow opt-in to exchange telemetry with the Angular team about your Angular CLI use, and now Angular 8 will collect data such as commands used and construct speed if users want it to support developers improve it in the future.

**CLI workflow improvements**

The Angular CLI is constantly improving, and the ng-build, ng-test and ng-run are now equipped to be extended by third-party libraries and tools. The AngularFire, as an example

**Builders API**

The new version allows us to use Builders API. Major operations such as: serve, build, test, lint, and e2e are used by builders. The builder Builders are basically functions that implement the logic and behavior for a task that can replace a command that you pass from the @angular-devkit/architect package to createBuilder() method and now we can also create our custom builders.

```
import { BuilderOutput, createBuilder } from '@angular-devkit/architect';
export default createBuilder((options, context) => {
  return new Promise<BuilderOutput>(resolve => {
    resolve({ success: true });
  });
});
```

**AngularJS API Migration Improvements with $location service**

The Angular Team wants to support all developers who use AngularJS to upgrade them with the latest Angular so that some improvements have been made to better integrate with the AngularJS $location service in hybrid (AngularJS <=> Angular) applications. A new `angular/common/upgrade` package will be added to help you

The Angular Team wants to provide support for all developers using AngularJS to upgrade them with latest Angular so some enhancements have been made to provide better integration with the AngularJS $location service in hybrid (AngularJS <=> Angular) apps. A new package angular/common/upgrade is added help you

* To retrieve the state from the service of the location.
* To track any changes to the location.
* Help you to retrieve search properties pof the hostname protocol port which were available in AngularJS.
* To test the location service, MockPlatformLocation API has been added.

**Service Worker**

Starting with version 5, Angular ships with the implementation of a service worker. With the Angular Service Worker and the Angular CLI built-in PWA support, angular developers can take advantage of this service worker and without code for low-level APIs, benefit from the increased reliability and performance it provides and can achieve native-like download and installation of applications.

**Updated Typescript to 3.4.x**

They have updated Angular's dependencies in the latest version of Angular 8, which include tools like RxJS and TypeScript to v3.4 (Angular 7 uses v3.2). New apps generated via the Angular CLI will also use TypeScript's latest version by default.

**Angular Firebase**

Angular has officially added firebase support and now we can use the Angular CLI to deploy our application.

`ng run [PROJECT_NAME]:deploy`

**Deprecated APIs and Features**

Angular aims to balance innovation and stability within their framework and to do that they have removed or replaced some features & API 'S so that Angular can stay up-to-date with the latest practices, changing dependencies, or platform changes themselves.

To render these changes smoother, they deprecate APIs and functionality for a period of time before they are disabled, and allow users time to update their applications to the new APIs and best practices.

* Web Tracing Framework integration
* Both `@angular/platform-webworker` and `@angular/platform-webworker-dynamic` are deprecated packages
* Usage for any in TesBed.get
* Removed deprecated DOCUMENT from `@angular/platform-browser`
* `@angular/http` removed from the list of packages
* ngForm element selector
* Service worker versionedFiles

**Angular Performance & Upgradtion from Angular 7 to Angular 8**

Angular 8 new features are nice, but a performance boost is the main reason many of us need to upgrade to new versions of Angular 8. It's simple to upgrade an app from version 7 to Angular 8 if you've worked with previous angular versions.

The following update should be handled by one command for most developers:

`ng update @angular/cli @angular/core <name>`

**Final Thoughts:**

To sum up all of the above features, the Angular team certainly did a great job with the framework that made developers much easier and simpler to work with. With Angular version 8 added features like Ivy, route configurations use dynamic imports, new builder API in CLI, web worker support and Unified Angular Location Service, it looks like a much more accessible solution focused on modern technological trends and with every new release. To improve the Angular platform, the frame becomes smoother and smoother.