---
layout: toc-page
title: Getting Started
id: getting_started
lang: en
---

* Table of contents. This line is required to start the list.
{:toc}

# Getting Started

Nebula is a collection of plugins built on top of Gradle. You will need to understand how Gradle works to understand how to integrate Nebula. The team at Gradle maintains a [getting started page for Java projects](http://gradle.org/getting-started-gradle-java/), if you are new to the subject.  

We publish all Nebula plugins to [Bintray](https://bintray.com/nebula/gradle-plugins), as well as to the [Gradle Plugin portal](https://plugins.gradle.org/). Since we publish to the Gradle Plugin portal, including a Nebula plugin in your Gradle build is as easy as adding a single line to your `build.gradle` file:

~~~output
apply plugin: 'nebula.dependency-lock'
~~~

After including this plugin in your `build.gradle`, you will be able to take advantage of all the features it has to offer. 

# What can Nebula do for you?

To help explain how Nebula can make your builds better, we describe some use cases below for organizations and for individual projects. This should help you understand which plugins might be most useful to you.  

## For organizations

Many of the Nebula plugins are useful for targeting problems that plague an organization or enterprise.

#### I want to make sure nobody in my organization builds with a particular dependency

Occasionally, Netflix engineers encounter a dependency that is considered harmful (for a variety of reasons) and needs to be removed from the overall dependency graph. We built the [gradle-resolution-rules-plugin](https://github.com/nebula-plugins/gradle-resolution-rules-plugin) as a simple approach to ensuring that we can quickly fix or fail builds based on the presence of the harmful dependency.   

Check out the [gradle-resolution-rules-plugin GitHub page](https://github.com/nebula-plugins/gradle-resolution-rules-plugin) for details on how to use it.

#### I want to make sure my library/version is always consumed with a fixed set of other library/versions

It is not uncommon for multiple libraries to be consumed as a dependency/version set in order to work properly. For instance, imagine there are three libraries: platform-core, platform-ipc and platform-cache. Consumers of the libraries should consume the same version of all three or unknown issues may arise. We built the [nebula-dependency-recommender-plugin](https://github.com/nebula-plugins/nebula-dependency-recommender-plugin) to make it easier to produce and consume [Maven BOM files](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html) to accomplish this task.

Check out the [nebula-dependency-recommender-plugin GitHub page](https://github.com/nebula-plugins/nebula-dependency-recommender-plugin) for details on how to use it.

#### I want to make sure engineers provide a mechanism to install or deploy their application

A common challenge in any organization is finding a simple, consistent way by which application developers can package and install their application for deployment. Chef, Puppet and a few other tools offer solutions to this problem. At Netflix, we decided to have application owners build OS specific packages. In order to simplify this process, we have built the [gradle-ospackage-plugin](https://github.com/nebula-plugins/gradle-ospackage-plugin).

Check out the [gradle-ospackage-plugin](https://github.com/nebula-plugins/gradle-ospackage-plugin) and [nebula-ospackage-plugin](https://github.com/nebula-plugins/nebula-ospackage-plugin) GitHub pages for details on how to use it.

#### I want to gather metrics and data about all builds within my organization

As tools teams scale the usage of an enterprise build solution, gathering metrics about the state of builds, both local and on a CI server becomes increasingly important. To accomplish this, we built the [gradle-metrics-plugin](https://github.com/nebula-plugins/gradle-metrics-plugin). This plugin will collect information about each build, and publish this data to [ElasticSearch](https://www.elastic.co/products/elasticsearch).

Check out the [gradle-metrics-plugin GitHub page](https://github.com/nebula-plugins/gradle-metrics-plugin) for details on how to use it.

#### I want to make sure all projects in my organization provide contact information

Maven provides a solution to this problem in their pom file schema, but Gradle does not. We built the [gradle-contacts-plugin]({{ site.baseurl }}/plugins/gradle_contacts.html) to allow this information to be captured inside a `build.gradle` file. 

Check out the [gradle-contacts-plugin GitHub page](https://github.com/nebula-plugins/gradle-contacts-plugin) for details on how to use it.

## For individual projects

While Nebula was built to tackle build issues at Netflix, many of the plugins are useful to standalone Java projects.

#### I want to ensure that previous versions of my code build with the exact same dependencies

In order to ensure that previous versions of your application have repeatable builds, you need to ensure that your transitive dependency graph is exactly the same. In order to do this, we created the [gradle-dependency-lock-plugin](https://github.com/nebula-plugins/gradle-dependency-lock-plugin), that will generate a `dependencies.lock` file and check that into version control. The plugin will also ensure that the locked versions are forced during a build.

Check out the [gradle-dependency-lock-plugin GitHub page](https://github.com/nebula-plugins/gradle-dependency-lock-plugin) for details on how to use it.

#### I want to use semantic versioning for my Java project

Gradle allows you to define a version number, but doesn't provide intelligence around how to easily manage a project's version. We built the [nebula-release-plugin](https://github.com/nebula-plugins/nebula-release-plugin) to allow us to manage releases of our software, using [Semantic Versioning](http://semver.org/).

Check out the [nebula-release-plugin GitHub page](https://github.com/nebula-plugins/nebula-release-plugin) for details on how to use it.

#### I want to publish my Java library to a Maven (or Ivy) repository

Recent versions of Gradle allow you to publish to a Maven or Ivy repository. Unfortunately, there is a fair amount of boilerplate required to do a simple publish. We created the [nebula-publishing-plugin](https://github.com/nebula-plugins/nebula-publishing-plugin) to address much of this boilerplate and make it easy to publish a Java library.

Check out the [nebula-publishing-plugin GitHub page](https://github.com/nebula-plugins/nebula-publishing-plugin) for details on how to use it.

#### I want to manage my Atlassian Stash project during a build

Being able to manage pull requests, branches or build statuses within Atlassian Stash is very useful. In order to simplify these tasks within a Gradle build, we built the [gradle-stash-plugin](https://github.com/nebula-plugins/gradle-stash-plugin). 

Check out the [gradle-stash-plugin GitHub page](https://github.com/nebula-plugins/gradle-stash-plugin) for details on how to use it.

#### I want all the Javadocs from my multi-module project to be aggregated

If you have a multi-module project and you would like to publish all of the javadocs as a single site or zip, then you can use the [gradle-aggregate-javadoc-plugin](https://github.com/nebula-plugins/gradle-aggregate-javadocs-plugin). 

Check out the [gradle-aggregate-javadoc-plugin GitHub page](https://github.com/nebula-plugins/gradle-aggregate-javadocs-plugin) for details on how to use it.

#### I want to override certain build properties from the command-line

Every once in a while, the need arises to set a value inside a Gradle build from the command line. Gradle currently does not allow you to do this. We built the [gradle-override-plugin](https://github.com/nebula-plugins/gradle-override-plugin) that will allow you to set any property in the Gradle build.

Check out the [gradle-override-plugin GitHub page](https://github.com/nebula-plugins/gradle-override-plugin) for details on how to use it.