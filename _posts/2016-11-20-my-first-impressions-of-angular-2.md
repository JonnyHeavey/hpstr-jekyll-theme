---
layout: post
title: My first impressions of Angular 2
description: "My first impressions of Angular 2."
modified: 2016-11-20
tags: [Angular, Development]
image:
  feature: angular.png
  credit:
  creditlink:
---

It is only recently that I have turned my attention to angular 2, with my [recent trip to AngularConnect](TBC) being the trigger for me to get up to speed.

I steered clear of the alpha/beta period completely, partly because it was clear from afar that it was very much a work-in-progress in terms of design and direction, but mostly because my recent workload hasn't offered the opportunity to pick up a new framework, which appears to have saved me quite a bit of pain. However, 2.0 final has now been released and with it comes some badly needed stability. It's worth noting that I was also quite late to the Angular 1 party - so for much of this period I was still very content with Ng1's feature set as it was still quite new to me, and hadn't quite felt the thirst for change.

As mentioned, Angular Connect was my kick start to getting back up to speed with the latest and greatest in the Angular world. I've been playing with Angular for around six weeks now, and I thought I'd summarise my initial thoughts, still very much as a newcomer. As a side note, I'm yet to use Angular 2 in a 'proper' project that is heading for production, only dummy proof-of-concepts, but I expect this to change in the near future.



The first thing that has struck me is the overall API simplification. The notion of components being the building blocks of an application is intuitive, and whilst this may have been the intent behind directives in NG1, this seems much simpler to comprehend.

Furthermore, the simplification of providers to Pipes is very welcome indeed. Compared to the NG1 counterparts of factories, services, providers

 caused many headaches.

Components, pipes and modules


Compared to its 1.x counterpart, this is remarkably straightforward

    no need to dig into factories, services, providers and the like


Events a bit more complex, but too much freedom in 1 meant loads of weird setups


Hard to predict how directives were communicating from one project to next


Sure there's still a DSL in templates, but I think it's fairly straight forward


Docs really good


So many how to videos / courses available for free!


Typescript bit of a hurdle / learning curve which doesn't help at the beginning, but as with most things, once clicks it's fine


Really enjoying the intelligence in ide

and I have to say that I've been really impressed with how much effort both the core team and the community have put into making Angular 2 easy to learn.

plenty more to learn

The reactive side with RXJS is something I need to dig into further

So, when I am next tasked with creating a front-end application I won't hesitate in considering Angular 2 and trying it out in anger.
