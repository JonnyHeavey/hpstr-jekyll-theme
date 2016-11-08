---
layout: post
title: Javascript quality analysis with SonarQube
description: "Javascript quality analysis with SonarQube."
modified: 2016-11-08
tags: [Javascript, SonarQube, Development]
image:
  feature: jssq.png
  credit:
  creditlink:
---

At Surevine [SonarQube](http://www.sonarqube.org/) plays an important part in ensuring our development teams produce software of good quality. We use SonarQube as part of our continuous integration setup, ensuring that we automatically get the latest view of the quality of our projects, accessible via an easy-to-read web interface at a well-known URL. SonarQube also centralises our quality profile / rule configuration which is really handy when working across multiple projects. Overall, we're fans of the system and I'd thoroughly recommend checking it out if you haven't already.

Historically, we've used SonarQube analysis primarily for backend components based in Java and PHP. More recently, we've wanted to apply the same quality checks to our front-end components, as they too should meet our expectations of quality. Here's how I added Javascript analysis to our SonarQube setup.

## Prerequisites

* SonarQube installation
* Javascript based project to analyse

## SonarQube Javascript plugin

The first step is to install SonarQube's [Javascript plugin](http://docs.sonarqube.org/display/PLUG/JavaScript+Plugin), which essentially informs the system about the Javascript language and provides a set of rules to enforce.

Follow SonarQube's official instructions on how to [install a plugin](http://docs.sonarqube.org/display/SONAR/Installing+a+Plugin).

## Sonar Scanner

The next step is to configure your software project to invoke Sonar Scanner (the SonarQube component which performs the code analysis).

There are various ways to do this depending on your technology stack.

The most tech-agnostic way of doing this is to directly download the scanner, create a properties file and invoke the binary manually (as described [here](http://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner)).

Alternatively, there are wrappers available for most of the popular task runners / build systems, which will be much more convenient to setup and use if you already have a runner in place. The project I was using to test the setup used grunt for task management, so I opted to use the grunt wrapper. The instructions below reflect this, but the process will be much the same if using another wrapper.

## Grunt Wrapper

To install the (grunt wrapper)[https://www.npmjs.com/package/grunt-sonar-runner] of the scanner, invoke the following command from within the project's root directory:

```
npm install grunt-sonar-runner --save-dev
```

Next we need to load the plugin by adding the following line into our `Gruntfile.js`:

```
grunt.loadNpmTasks('grunt-sonar-runner');
```

Finally, we need to configure the scanner, providing details on the location of SonarQube, as well as the source files we want it to analyse. To do so, we need to add a `sonarRunner` configuration object following options to our `Gruntfile.js`.

```
sonarRunner: {
    analysis: {
        options: {
            sonar: {
                host: {
                    url: 'https://sonar.url.here/'
                },
                login: 'sonar-user-name',
                password: 'sonar-user-password',
                projectKey: 'project-key',
                projectName: 'project-name',
                projectVersion: '1.0.0',
                sources: ['src'].join(','),
                language: 'js',
                sourceEncoding: 'UTF-8'
            }
        }
    }
}
```

Of course you will need to adjust the values you use to reflect your SonarQube installation and project.

Its worth noting the documentation for the wrapper is missing some important details around authentication. In order to populate SonarQube you will need to provide `login` & `password` properties using the username and password of a valid SonarQube user (as shown above). Alternatively, you can use a `login` property alone, and provide a SonarQube auth token as the value (in which case no password required).

## Execution

Once configured, you can invoke the analysis by performing the following command from the root directory of your project:

```
grunt sonarRunner:analysis
```

Once Sonar Scanner was configured, all that remained was for me was to hook this up to our CI server. We use Jenkins for our CI, so a quick modification of the project's JenkinsFile (groovy script) to invoke the new grunt task (shown above) was all that was needed. We now have static analysis of the Javascript in our front-end component being performed on every commit.

The next steps for us will be to add code coverage reporting into this setup, which I will follow up on in another post.
