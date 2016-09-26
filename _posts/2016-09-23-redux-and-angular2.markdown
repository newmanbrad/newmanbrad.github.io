---
layout: post
title:  "What Redux can do for your Angular 2 application"
date:   2016-09-23 12:35:05 -0400
categories: Redux, Angular, Javascript
---

![Brad Newman]({{ site.url }}/assets/angular_logo.png){: .center-image }

Pairing Redux with your Angular 2 application may bring more to the table than you have considered. Providing a rich feature set and predictable application behavior, adding Redux to your application will provide the insights and workflow you have been looking for.

## What is Redux

“Redux is a predictable state container for JavaScript apps. It helps you write applications that behave consistently, run in different environments (client, server, and native), and are easy to test.” (http://redux.js.org/)

This topic is broad and cannot be covered in it’s entirety here. However, the general idea is to save the state of your entire application in an object tree. The object tree is saved in a container object called the store. State is captured with Redux when an action is taken via an Angular component. The lifecycle pattern shown below offers predictable behavior throughout the entire application regardless of size.

![Data Flow]({{ site.url }}/assets/NG2-Redux-data-flow.png){: .center-image }

Every change to the application state is captured as an action and sent to the store to be recorded. You can learn more about each piece and what specifically it does here.
Capturing state changes in your application can provide the ability to review and refine many aspects of your application from UX to logic efficiencies. The application state can be used to quickly identify bottlenecks, allowing poor user interaction to be caught early in the development process. This means that once your application rolls out for testing, you can spend more time on the shiny new feature set that has suddenly become a new project requirement. Here are some examples of what Redux can offer.

## UX Insight

As a user moves through an application that is using Redux, we can capture router state change. This will allow us to visualize user navigation. We can identify specific workflows that could be defined in a clearer way. New tools like Redux VCR allow the ability to monitor / record a user session using Redux store interactions in real time. From a UX perspective, having the ability to monitor a user and watch them walk through complicated application interactions can be invaluable.

![Data Flow]({{ site.url }}/assets/Sep-22-2016.gif){: .center-image }

Above, you can see application state changes played like a movie with the use of time travel debugging. Also, take note that each action that is taken by the user is being displayed in the console visible in the bottom right corner.

![Data Flow]({{ site.url }}/assets/tree.png){: .center-image }

The image above is of an application state tree displayed using the Redux debugging tool. It was used for an example Angular 2 / NG2-Redux application that I put together. You quickly get an overview of my example application structure without browsing through the app. My state contains only a couple of modules at this point, clients, router and session. With a couple of clicks, I can drill into different modules and see data structures and associations.

## Debugging Insight

Using the Redux development tools package, you can see actions that have been performed on the application state in sequential order. When an action is dispatched, Redux captures and displays the previous application state, the action taken and the next application state. Working your way backward or forward through the state assures that your action is having the correct effect on the UI. This makes debugging a breeze. Saving the developer from filling out forms thousands of times to assure that the correct state transition has been a success.

![Data Flow]({{ site.url }}/assets/insight.png){: .center-image }

## What integration would look in your Angular 2 application

<script src="https://gist.github.com/newmanbrad/2e9129e593afd66251ba51eb4fcb5244.js"></script>

If you would like to see a full example, you can check out the project used for this article via a link in the resources section below.

## Is Redux Necessary

If you are building a small application, integrating Redux into your Angular 2 application might not make sense. Reasons to not use Redux are best explained by the Redux author himself Dan Abramov. A useful article on this subject can be found here.
If you are building a large data intensive application. I highly recommend reviewing what Redux can bring to your application.

## Getting Started

Here are some great resources you can use.

[https://github.com/angular-redux/ng2-redux]() — Ng2Redux lets you easily connect your Angular 2 components with Redux, while still respecting the Angular 2 idiom.

[https://github.com/newmanbrad/ng2-redux-example ]() — Example application build using Ng2Redux and shown in the images above.

[https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=en]() — Redux dev tools for Chrome.