---
layout: toc-page
title: Introduction to Nebula
id: introduction_to_nebula
lang: en
---

* Table of contents. This line is required to start the list.
{:toc}

## What is Nebula?

Nebula is a collection of [Gradle](http://gradle.org/) plugins built for engineers at [Netflix](http://jobs.netflix.com). The goal of Nebula is to simplify common build, release, testing and packaging tasks needed for projects at Netflix. In building Nebula, we realized that many of these tasks were common needs in the industry, and it was worth open sourcing them.

## A brief history of Nebula

Prior to Nebula, Netflix software was built using an [Ant](http://ant.apache.org/) and [Ivy](http://ant.apache.org/ivy/) based solution we called CBF (Common Build Framework). All Java software at Netflix was built using CBF. The Engineering Tools team at Netflix built and supported CBF. As CBF usage grew, the team felt the increasing challenges of supporting a large Ant/Ivy-based build system.

We began looking for a build tool that:

- enabled testability
- provided first class support for Java applications
- had a rich community and ecosystem
- allowed us to vastly simplify build files

The team began to look around the industry for alternative build systems and decided that Gradle was the best solution for Netflix. The results of our conversion to Gradle is Nebula.

Nebula was created by [Justin Ryan](https://twitter.com/quidryan) at Netflix. You can [watch this video](https://www.youtube.com/watch?v=iRwJrvj_hKw) from the [2013 Gradle Summit](http://gradlesummit.com/conference/santa_clara/2013/06/home) that talks about Nebula's humble beginnings.

## How Netflix builds software

To best understand the origins of Nebula, we should start with Netflix's build needs. Netflix migrated to the AWS a few years ago, and converted our previously monolithic Java application into microservices. Much of Netflix OSS represents the byproduct of our cloud, microservice migration.

### How deployments affects builds

Early in our migration to the cloud, we decided to lean heavily on the [Immutable Server pattern](http://martinfowler.com/bliki/ImmutableServer.html). Every deployment we make to our services means that we "bake" a new Amazon Machine Image, or AMI. We built and open sourced [Aminator](https://github.com/Netflix/aminator), a Python library that can take an RPM or DEB and create an AMI.

In order to make it easy for engineering teams at Netflix to turn their services into DEBs, we created the [gradle-ospackage-plugin](https://github.com/nebula-plugins/gradle-ospackage-plugin).

### How IPC affects builds

Netflix has developed a number of Java libraries designed to handle the complexities of communicating at scale in the cloud. Netflix engineers who wish to write code to call another microservice do so by consuming that service's client jar file. This client jar contains Java API's that abstract the complexities involved with scaling that service.Providing a far client jar makes it easy for consumers of the service to get up and running. The API is defined through a Java interface, making it easy to understand and use.

There are however a wealth of challenges that this approach creates:

- a client's transitive dependency graph can upgrade dependencies on the consuming service unintentionally
- if a bad client jar is published, all consumers need to pin back to a known good version

Most of these issues are can be classified as Java dependency management issues. We have written a number of plugins to help improve this story for engineers, including the [gradle-dependencylock-plugin](https://github.com/nebula-plugins/gradle-dependency-lock-plugin), [nebula-dependency-recommender-plugin](https://github.com/nebula-plugins/nebula-dependency-recommender-plugin) and the [gradle-resolution-rules-plugin](https://github.com/nebula-plugins/gradle-resolution-rules-plugin).

## The Nebula Team

Nebula is actively developed and maintained by the Netflix Build Tools team, which is a part of Engineering Tools & Services. Feel free to reach out if you have any questions.

- Erin Kidwell (Director, Engineering Tools & Services)
- [Roberto Perez Alcolea](https://twitter.com/rpalcolea) (Senior Software Engineer)
- Aubrey Chipman (Senior Software Engineer)
- Martin Chalupa (Senior Software Engineer)

## Previous team members

- [Mike McGarr](https://twitter.com/SonOfGarr) (Engineering Manager)
- [Rob Spieldenner](https://twitter.com/robspieldenner) (Senior Software Engineer)
- Steve Hill (Senior Software Engineer)
- [Jon Schneider](https://twitter.com/jon_k_schneider) (Senior Software Engineer)
- [Danny Thomas](https://twitter.com/dannythomas) (Senior Software Engineer)
- [Nadav Cohen](https://twitter.com/nadavc) (Senior Software Engineer)
