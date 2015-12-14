---
layout: toc-page
title: Getting Started
id: getting_started
lang: en
---

* Table of contents. This line is required to start the list.
{:toc}

# Getting Started

Nebula is a collection of plugins built on top of Gradle. You will need to understand how Gradle works to understand how to integrate Nebula. The team at Gradle maintains a [getting started page for Java projects](http://gradle.org/getting-started-gradle-java/).  

We publish all Nebula plugins to [Bintray](https://bintray.com/nebula/gradle-plugins), as well as the [Gradle Plugin portal](https://plugins.gradle.org/). Since we publish to the Gradle Plugin portal, including a Nebula plugin into your Gradle build is as easy as adding a single line to your `build.gradle` file:

~~~groovy
apply plugin: 'nebula.dependency-lock'
~~~

After including this plugin in your `build.gradle`, you will be able to take advantage of all the features it has to offer. 

# What can Nebula do for you?

To understand how Nebula can make your builds better, we have tried to categorize the Nebula plugins. To help you better understand which plugins might be useful, we've put together some common use cases.

## For organizations

Many of the Nebula plugins are useful for targeting problems that plague an organization or enterprise.

#### I want to make sure nobody in my organization builds with a particular dependency

Occasionally, Netflix engineers encounter a dependency that is considered harmful (for a variety of reasons) and needs to be removed from the overall dependency graph. We built the [gradle-resolution-rules-plugin]({{ site.baseurl }}/plugins/gradle_resolution_rules.html) as a simple approach to ensuring that we can quickly fix or fail builds based on the presence of the harmful dependency.   

Check out the [gradle-resolution-rules-plugin page]({{ site.baseurl }}/plugins/gradle_resolution_rules.html) for details on how to use it.

#### I want to make sure my library/version is always consumed with a fixed set of other library/versions

It is not uncommon for multiple libraries to be consumed as a dependency/version set in order to work properly. For instance, imagine there are three libraries: platform-core, platform-ipc and platform-cache. Consumers of the libraries should consume the same version of all three or unknown issues may arise. We built the [nebula-dependency-recommender-plugin]({{ site.baseurl }}/plugins/nebula_dependency_recommender.html) to make it easier to produce and consume [Maven BOM files](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html) to accomplish this task.

Check out the [nebula-dependency-recommender-plugin page]({{ site.baseurl }}/plugins/nebula_dependency_recommender.html) for details on how to use it.

#### I want to make sure engineers provide a mechanism to install or deploy their application

A common challenge in any organization is finding a simple, consistent way by which application developers can package and install their application for deployment. Chef, Puppet and a few other tools offer solutions to this problem. At Netflix, we decided to have application owners build OS specific packages. In order to simplify this process, we have built the [gradle-ospackage-plugin]({{ site.baseurl }}/plugins/gradle_ospackage.html).

Check out the [gradle-ospackage-plugin page]({{ site.baseurl }}/plugins/gradle_ospackage.html) for details on how to use it.

#### I want to gather metrics and data about all builds within my organization

As tools team scale the usage of an enterprise build solution, gathering metrics about the state of builds, both local and on a CI server. To accomplish this, we built the [gradle-metrics-plugin]({{ site.baseurl }}/plugins/gradle_metrics.html). This plugin will collect information about each build, and publish this data to [ElasticSearch](https://www.elastic.co/products/elasticsearch).

Check out the [gradle-metrics-plugin page]({{ site.baseurl }}/plugins/gradle_metrics.html) for details on how to use it.

#### I want to make sure all projects in my organization provide contact information

Maven provides a solution to this problem in their pom file schema, but Gradle does not. We built the [gradle-contacts-plugin]({{ site.baseurl }}/plugins/gradle_contacts.html) to allow this information to be captured inside a `build.gradle` file. 

Check out the [gradle-contacts-plugin page]({{ site.baseurl }}/plugins/gradle_contacts.html) for details on how to use it.

## For individual projects

While Nebula was built to tackle enterprise scale dependency issues at Netflix, many of the plugins are useful to standalone Java projects.

#### I want to ensure that previous versions of my code build with the exact same dependencies

dependency-lock

#### I want to use semantic versioning for my Java project

nebula-release

#### I want to publish my Java library to a Maven (or Ivy) repository

nebula-publishing

#### I want to publish my Java library to Bintray

nebula-bintray

#### I want to manage my Atlassian Stash project during a build

gradle-stash

#### I want all the Javadocs from my multi-module project to be aggregated

aggregate-javadoc

#### I want to override certain build properties from the command-line

override-plugin