---
title: Top 10 Features of Angular 6.0
image: "/assets/default-social-image.png"
categories: Angular-6.0
---

**Top 10 Features of Angular 6.0**

Angular is one amongst the most popular frameworks available for web development. With the release of its latest version, web developers have been given even more features.

As we all know, the new version of Angular was released by Google in April. It was Google's first major release in 2018 that focused primarily on the toolchain and also made it easier for the user to create various types of applications. There are also some new features and enhancements in this big edition. This release confirms at the final stage that the new version of Angular is much lighter, faster, and easier. Obviously, developers will prefer it more as it facilitates their development. Angular 6 now supports version 2.7 of TypeScript. Therefore, the latest TypeScript release makes it much easier to program with declarations of default as well as conditional type and strict class initialization.


Now it's time to discuss Angular 6's major changes.

**1. Angular Elements**

Angular is a great platform for single-page applications creation. In earlier versions of Angular, creating a widget or component that can be included in any existing web page was not a simple task. But with the help of Angular Elements, it can be done in Angular 6. In addition, the first Angular launch that fully supports Angular Elements is Angular 6. Angular Elements was Angular's Rob Wormald's brainchild. The Angular Elements package will give us the ability to create an Angular component and then publish it as a web component that can be used in any other environment on any HTML page (even if that page does not use the Angular framework). It actually takes an Angular component and then wraps it into a custom element like a DOM element, so we can use our favorite Angular component in other projects that don't use Angular.


**2. Service Worker Support**

Service workers are essentially web browser scripts that manage to cache an application. In Angular 5, service workers were introduced for the first time. Service workers come up with some bug fixes in Angular 6, including some new features. So when we launch the new software update, the current networkworker(s) may need to be deactivated or uninstalled. There is no clear choice in Angular 5 to do this, but Angular 6 introduces this function with the new script file called safety-worker.js, which is basically part of the production package which lets us unregister the existing serviceworker(s).

Angular 6 now supports the Service Workers configuration of navigation URLs. The service worker must navigate to the defined index file navigation requests that suit no origin or information class. Now, in ngsw-config.json data, we may discuss an additional navigationUrls list that includes the required URLs. Of eg, if the URLs of a query suit any of the optimistic trends and none of the negative patterns, then a navigation application will be deemed and the service worker will treat the correct way. Unless the database is reconnected and upgrades the job, the service worker stays in the current mode in Angular 6.


**3. Bye, Bye Template Element**

Once Angular 4 was introduced, the `<template>` element was depreciated a year later. Now it's time to say goodbye to `<template>` as it's gone from the Angular 6  framework. We now need to use `<ng-tempalate>` instead of using `<template>`.

**4. i18n**

The internationalization or i18n is one of the major changes in Angular 6. In Angular 6, i18n comes with runtime rendering so that one request per locale is not needed. Within Angular 6, the currency pipe has been changed in such a way that it makes a lot of sense, for instance, with 2 digits it will no longer round every currency value. It will then round the currency to the correct numbers (like Arabic Dinar's 3-digit roundup or Chilean Pesos 0 roundup). If we want to programmatically extract these numbers, we must use the feature `getNumberOfCurrencyDigits()`of the i18n. There are some other formatting features that are also publicly exposed such as `formatDate`, `formatCurrency`, `formatPercent`, and `formatNumber`.

**5. Ivy: New Rendering Engine**

In Angular 6, a third rendering engine named Ivy was released by the Angular group. Ivy is the Angular rendering engine of the next generation. Angular used a display engine for rendering purposes in some of the previous versions of Angular (i.e. Angular 2 to Angular 4). The implementation of this interaction with the rendering engine increases the speed and decreases the software size. With the new rendering engine, the Angular team expects the same type of experience.

Angular compiles our templates into identical TypeScript code, then compiles TypeScript code into JavaScript, and then ships the output to our clients.  Ivy renderer is the latest rendering engine, initially designed to support backward compatibility with current renderers and then focused on improving rendering speed and optimizing the final pack size. In Angular, it won't be the default renderer, but the compiler options can be used to manually allow it. This essential function is not fully released in Angular 6 as it is in beta form, with the exception of the full version in the next launch of Angular.

**6. ngModelChange**

The `ngModelChange` event was emitted before the updating of the said form control, before Angular 6. If we have an event handler that verified the value through the control for the `ngModelChange` function, the old value will be returned instead of the modified value. `ngModelChange` has now emitted the value in Angular 6 after modifying the value in the form control.

**7. `ElementRef` `<T>`**

If we want to build an element link in the template in previous versions of Angular, we can use `@ViewChild` or `@ViewChildren` or explicitly insert the host using `ElementRef`. But the issue is that, like any other element, `ElementRef` had its `nativeElement` property typed. But now we can use the `ElementRef` type more specifically in Angular 6 if we want to.

```
@ViewChild('login') login: ElementRef<HTMLInputElement>;
ngAfterViewInit() {
  this.loginInput.nativeElement.focus();
}
```

**8. Bazel Compiler**

In fact, Bazel Compiler is a build system or mechanism that is used by Google to build almost all software. Only rebuild what is needed to build this compiler. Since source code varies very often, restoring the entire application for every small change makes no sense. Instead of reconstructing the entire application, we only create the code that actually changes, and also the code that depends on those changes. Therefore, we can achieve quick and gradual builds with the aid of advanced local and distributed caching, automated dependency analysis and concurrent execution. We'll have this compiler support with Angular 6.

**9. RxJS 6.0**

Angular 6 has now been locally utilizing RxJS 6. Thus, we need to review the software accordingly. Such updates make it easier for programmers to test AJAX request stacks and also boost modularity, rendering it as backward compatible as possible and increased performance for developers. Yet RxJS has changed the way items are being imported.

The usual code in RxJS 5 is:

```
import { Observable } from 'rxjs/Observable';
import 'rxjs/add/observable/of';
import 'rxjs/add/operator/map';
const squares$: Observable<number> = Observable.of(1, 2).map(n => n * n);
```

The pipeable operators was introduced by RxJS 5.5:

```
import { Observable } from 'rxjs/Observable';
import { of } from 'rxjs/observable/of';
import { map } from 'rxjs/operators';
const squares$: Observable<number> = of(1, 2).pipe( map(n => n * n));
```

The imports were changed in RxJS 6.0 to:

```
import { Observable, of } from 'rxjs';
import { map } from 'rxjs/operators';
const squares$: Observable<number> = of(1, 2).pipe(map(n => n * n));
```

So, as shown by the above code, we need to change the import of RxJS throughout our Angular 6 application. But I'm going to say right now we don't need to change this. Since RxJS provided a module named rxjs-compat enabling us to use RxJS version 6.0 with the syntaxes of the old version.

**10. Tree Shaking**

Angular 6 switched from modules that referenced resources to modules that referenced services to minimize size of the Angular device. Tree shaking is a step of build optimization that attempts to ensure that any unused code in our final bundle is not used. Rather than rendering template data and passing it directly to the interpreter which knows how to do everything, the new renderer will directly generate the instructions of template, which leads to much smaller bundles and a quicker startup time.

In Angular 6, there is a new way of defining an injectable service. By using the new `providedIn` attribute, we can register a provider directly within the `@Injectable()` decorator. It recognizes 'root' from our application as a value or any name of the module. When we use root, this means that this injectable will be registered in the application as a singleton object, and we don't need to add it to the root modules providers. Likewise, if we use `providIdIn:LoginModule`, injectable will then be listed as a `LoginModules` provider without applying it to the modules providers.

```
@Injectable({
  providedIn: 'root'
})
export class UserService {}
```

So, in the above section, we discuss most important features of the Angular 6. Apart for these, there are also several features, like:

* While a path is being built, the router often enters a race situation and a fresh application for navigation arrives. In Angular 6, this problem has been fixed.
* Avoid overriding the `ngInjectableDef` on the type in the decorator.
* Angular Material Library uses the Dev Kit (CDK) component that provided 30 + components for the UI. CDK also allows us to use Angular Material to build our own library of UI components.
* Angular CLI uses technology called Schematics to generate angular artifacts. If you decide to create your own template, the Angular team has added the command `ng-add` in Angular-CLI that allows users to download and install new packages in an Angular app.
* If the user wants to upgrade their Angular app from v5 to v6, Angular team has added `ng-update` support to their Angular-CLI that allows the user to upgrade and upgrade packages.
* The 2.6 version of the `resolveModuleName` of Typescript started requiring passed-in paths to be separated by `/` rather than handling `\`.
* Improved messages for the decorator error.
* Enable minimal CLI render3 application size tracking.
* The Angular team decided to extend long-term support (LTE) to all major releases from v4.
* Bundlers for web pack module have been updated to version 4 and are supported by Angular CLI.

Check out [this](https://dzone.com/articles/angular-tutorials-and-articles) if you enjoyed this article and would like to learn more about Angular.