---
layout: post
title: Getting Started With Yarn
description: "How to use the Yarn package manager."
modified: 2016-10-21
tags: [web, yarn, package management]
image:
  feature: yarn.png
  credit:
  creditlink:
---

A couple of weeks ago Facebook released Yarn, and alternate package manager for the web that is compatible with npm repositories.

When I first heard about it, my initial reaction was along the lines of "is this really necessary?", npm works ok and is now commonplace. Do we really need another component in an already complex Javascript ecosystem? However, I believe that there is always room for improvement, and anything that aims to make a developer's life better is worth looking at.

Yarn is a drop-in replacement for the npm client, and supposedly improvement upon it in various areas including:

- Performance
- Security
- Reporting

For more details on Yarn's features and advantages, please read the [official documentation](https://yarnpkg.com/) or [this comparison post](https://www.sitepoint.com/yarn-vs-npm/).

## Installation

For OSX/MacOS, the recommended method is to install using homebrew:

```
brew install yarn
```

Its also possible to install with npm, but this feels somewhat wrong.

```
npm install -g yarn
```

## Usage

Once installed, you're able to use yarn for both new projects, and existing ones that currently use npm for package management. For the latter, (where you already have a `package.json`), you simply need to invoke the following command from your project's root directory.

```
yarn install
```

It's as easy as that. This will instruct yarn to fetch all of the required dependencies for your project. If the process was successful, you should find a `yarn.lock` file in your project's root directory. This is the equivalent of the `package.json` from npm that you're probably familiar with.

For a new project, you'll need to initialise Yarn in much the same way you would with npm, by executing the following command from the root of your project:

```
yarn init
```

Once Yarn has been initialised, it is ready to manage your project's dependencies. The CLI commands differ slightly in places to their npm counterparts, but they remain intuitive and easy to remember. I won't duplicate the entire [API](https://yarnpkg.com/en/docs/usage) in this post, but the core commands are as follows:

```
yarn add <package> // adds a new package dependency
yarn update <package> // updates an existing package dependency
yarn remove <package> // removes a package dependency
```

No suprises there, which should make the transition from npm to yarn a smooth one.

## First Impressions

It's early days for Yarn, and I haven't really had enough time to cast too much of judgement on it yet, but so far it seems pretty good. It's quick to set up and transition to for an npm-based project (as you can hopefully see from above).

I'm particularly fond of the improved output/reporting, especially during a `yarn install`. I think it's much more readable, and provides a better picture of what it is currently doing / how much it has remaining.

Whilst some of the security improvements are less headline-grabbing to most of us, they are essential and we would feel the pain badly if they weren't in place.

I believe that performance will ultimately be where this battle is won or lost. Lengthy `npm install`'s have become notorious, and if Yarn can make a serious dent in them then I can see it being very popular.

It will be interesting to see how this influences the npm client moving forward. I for one really hope that the npm compatibility is retained. If this is lost, it will be more effort for developers when publishing or retrieving packages to/from multiple repositories, which would be a backwards step in my view.

For the latest updates on Yarn, follow [@yarnpkg](https://twitter.com/yarnpkg) on Twitter.
