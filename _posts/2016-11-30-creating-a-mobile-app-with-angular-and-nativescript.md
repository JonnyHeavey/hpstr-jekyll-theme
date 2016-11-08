---
layout: post
title: Creating a mobile app with Angular 2 and Nativescript
description: "How to create a mobile application with Angular 2 and Nativescript."
modified: 2016-11-30
tags: [Angular, Nativescript, Mobile, Development]
image:
  feature: angular.png
  credit:
  creditlink:
---

Mobile app development has come a long way

No longer stark choice between truly native (writing objective-c or Android friendly Java) or phonegap / cordova web-view based things.

For a long time us web developers opted for the latter, as they promised use to reuse skills

Unfortunately many of us found that performance was lacking

lines have now been blurred somewhat - several technologies, one of which is nativescript, which allows us to write out business logic in Javascript (even in a framework we like such as Angular), something we're familiar with,

but the views are written and use truly native UI components, resulting in a much more improved performance and better experience for users



Install TNS

`npm install -g nativescript`

EASY

`tns` is the CLI command

`tns create my-project --ng`

--ng flag tells the CLI to create an angular 2 based skeleton app
which I'll be using here
template

NS doesn't need angular, the 'vanilla' version works fine using the code-behind model,
but as an Angular developer I'd like to transfer my skills and appreciate the familiar structure that NG offers

Next we need to add a platforms.

I'll focus on ios today, but much the same process for android (slight differences in simulation vs emulation etc that you'll be familiar with if you've built a cross platform app in the past)

`tns platform add ios`

sets up the relevant platform's project (creates an actual ios xcode project for example)

To test we're up and running

once run, we don't need to worry about xcode again, which gets my vote!

painless.

`tns run ios --emulator`

Should see something like this:

<img here>

Now we're ready to create our app

significant directories:
`app` directory contains our source for app
`App_Resources` contains the platform specific resources (icons, splash screens etc)

code business logic in app

If you look at app.component.ts jsut an angular component that you're probably used to, written in typescript

worth noting that views need to use NS specific XML, importantly NOT HTML (despite templates still using this extension...), no divs here... as there is no DOM!
Bit of a transition.

`app.component.html`

```
<Label text="Tap the button" class="title"></Label>
```

to

```
<Label text="Please tap the button" class="title"></Label>
```

Manners go a long way

If we now invoke `tns run ios --emulator` again you should see our new label.

Workflow perspective constantly rebuilding can be a pain

livewatch

from where you're good to go with building your mobile application using Angular as you know (and maybe love?) and the Nativescript View layer.
