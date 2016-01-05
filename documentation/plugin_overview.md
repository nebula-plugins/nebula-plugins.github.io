---
layout: toc-page
title: Plugin Overview
id: plugin_overview
lang: en
---

* Table of contents. This line is required to start the list.
{:toc}

# Nebula Plugin Overview

As was stated earlier, Nebula is composed of a number of Gradle plugins, each serving a unique purpose. There are however logical groupings to some of the plugins. The categories 

- Java dependency management
- OS packaging
- Release management
- Miscellaneous
- Core plugins
- Deprecated

## Java dependency management
Gradle provides a substantial [dependency management facility](https://docs.gradle.org/current/userguide/artifact_dependencies_tutorial.html), but we have found these capabilities insufficient for the needs of Netflix engineers. As we result, we have built a few plugins that extend Gradle dependency management capabilities.

### gradle-dependency-lock-plugin
The goal of the [gradle-dependency-lock-plugin](https://github.com/nebula-plugins/gradle-dependency-lock-plugin) is to ensure builds are repeatable over time, by locking the complete transitive dependency graph into a single source file. This particular plugin is useful for:

- allowing repeatable builds of old versions of the code
- controlling dependency updates when volatile libraries

Check out the [gradle-dependency-lock-plugin GitHub page](https://github.com/nebula-plugins/gradle-dependency-lock-plugin) for details on how to use it.

### nebula-dependency-recommender-plugin
The goal of the [nebula-dependency-recommender-plugin](https://github.com/nebula-plugins/nebula-dependency-recommender-plugin) is to make it easier to produce and consume a [Maven BOM file](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html). This plugin allows library producers to publish a single BOM file that defines a graph of dependency versions that all work together. This plugin also allows library consumers to defer the specification of specific dependency versions to an authoritative BOM producer.

Check out the [nebula-dependency-recommender-plugin GitHub page](https://github.com/nebula-plugins/nebula-dependency-recommender-plugin) for details on how to use it.

### gradle-resolution-rules-plugin
The goal of the gradle-resolution-rules-plugin is provide a mechanism to share dependency rules for all Gradle builds within an entire organization. The rules can be packaged and published using the `nebula.resolution-rules-producer` sub-plugin. The rules can be consumed and applied using the `nebula.resolution-rules` sub-plugin.

Check out the [gradle-resolution-rules-plugin GitHub page](https://github.com/nebula-plugins/gradle-resolution-rules-plugin) for details on how to use it.

## OS Packaging

All deployments at Netflix are conducted via what we call a "bake". A bake is the process of taking a base Amazon Machine Image (BaseAMI) and installing the application via its Debian package. This enables us to easily conform to the [Immutable Server pattern](http://martinfowler.com/bliki/ImmutableServer.html). Nebula provides a few plugins to help with this process. 

### gradle-ospackage-plugin
The goal of this plugin is to produce a system package, typically an RPM or Debian package. 

Check out the [gradle-ospackage-plugin GitHub page](https://github.com/nebula-plugins/gradle-ospackage-plugin) for details on how to use it.

### nebula-ospackage-plugin
The [nebula-ospackage-plugin page](https://github.com/nebula-plugins/nebula-ospackage-plugin) is an opinionated implementation of the gradle-ospackage-plugin. With the nebula-ospackage-plugin, you can easily package your Gradle application into a RPM or Debian that will set up a daemon process on Tomcat.  

Check out the [nebula-ospackage-plugin GitHub page](https://github.com/nebula-plugins/nebula-ospackage-plugin) for details on how to use it.

## Release management

There are a number of Nebula plugins that assist in the publishing and releasing of software, based on the needs of Netflix services. 

### nebula-publishing-plugin
The goal of this plugin is to make it dirt simple to publish your Java library to a Maven or Ivy repository without all of the boilerplate Gradle DSL.

Check out the [nebula-publishing-plugin GitHub page](https://github.com/nebula-plugins/nebula-publishing-plugin) for details on how to use it.

### nebula-release-plugin 
The goal of this plugin is to simplify a [Semantic Versioning](http://semver.org/) approach to releasing Gradle based builds.    

Check out the [nebula-release-plugin GitHub page](https://github.com/nebula-plugins/nebula-release-plugin) for details on how to use it.

### gradle-git-scm-plugin
The goal of this plugin is to allow for the execution of [Git](https://git-scm.com/) commands from a Gradle build.

Check out the [gradle-git-scm-plugin page](https://github.com/nebula-plugins/gradle-git-scm-plugin) for details on how to use it.

### gradle-stash-plugin
The goal of this plugin is to provide tasks that allow the management of a Git repository in a [Bitbucket server (formerly Stash)](https://www.atlassian.com/software/bitbucket/server).

Check out the [gradle-stash-plugin GitHub page](https://github.com/nebula-plugins/gradle-stash-plugin) for details on how to use it.

### nebula-bintray-plugin
The goal of this plugin is to remove much of the boilerplate required in using the existing [gradle-bintray-plugin](https://github.com/bintray/gradle-bintray-plugin). The goal is allow users to apply the plugin and publish to [Bintray](https://bintray.com/) with very little ceremony.

Check out the [nebula-bintray-plugin page](https://github.com/nebula-plugins/nebula-bintray-plugin) for details on how to use it.

## Miscellaneous
The Nebula team has built a variety of additional miscellaneous plugins over time, each with a unique purpose. 

### gradle-metrics-plugin
The goal of this plugin was to capture and publish metadata and build performance metrics to a centralized location so the Netflix Build Tools team could analyze build trends. The [gradle-metrics-plugin](https://github.com/nebula-plugins/gradle-metrics-plugin) publishes a json document to an [ElasticSearch](https://www.elastic.co/products/elasticsearch) cluster by default.

Check out the [gradle-metrics-plugin GitHub page](https://github.com/nebula-plugins/gradle-metrics-plugin) for details on how to use it.

### nebula-project-plugin
The goal of this project is to make it easy to set up a Java project the Netflix way. While it is tailored to Netflix's view of project setup, the defaults are sane enough for most projects. Applying this plugin:

- adds a `*-javadoc.jar` and a `*-sources.jar` as build outputs
- applies the [gradle-info-plugin](https://github.com/nebula-plugins/gradle-info-plugin)
- applies the [gradle-contacts-plugin](https://github.com/nebula-plugins/gradle-contacts-plugin)

Check out the [nebula-project-plugin page](https://github.com/nebula-plugins/nebula-project-plugin) for details on how to use it.

### gradle-contacts-plugin
A feature provided by Maven that is missing from Gradle is the `<developers/>` section, which denotes the contact information for the owners of the project. The purpose of the  [gradle-contacts-plugin](https://github.com/nebula-plugins/gradle-contacts-plugin) is to provide comparable features to Gradle.  

Check out the [gradle-contacts-plugin GitHub page](https://github.com/nebula-plugins/gradle-contacts-plugin) for details on how to use it.

### gradle-aggregate-javadocs-plugin
If you are building a multi-module project and would like to publish a single Javadoc site for all modules, we recommend using the [gradle-aggregate-javadocs-plugin](https://github.com/nebula-plugins/gradle-aggregate-javadocs-plugin).

Check out the [gradle-aggregate-javadoc-plugin GitHub page](https://github.com/nebula-plugins/gradle-aggregate-javadocs-plugin) for details on how to use it.

### gradle-extra-configurations-plugin
The goal of this plugin is to make it easier to add either an `optional` or `provided` configuration to an existing Gradle project.  

Check out the [gradle-extra-configurations-plugin page](https://github.com/nebula-plugins/gradle-extra-configurations-plugin) for details on how to use it.

### gradle-override-plugin
This plugin allows you to override arbitrary Gradle properties via command line args. Convenient if you want to quickly change values that are normally static for one off builds. 

Check out the [gradle-override-plugin page](https://github.com/nebula-plugins/gradle-override-plugin) for details on how to use it.

### nebula-clojure-plugin
An opinionated plugin that wraps the [clojuresque](https://bitbucket.org/clojuresque/clojuresque) gradle plugin, removing the [Clojars](https://clojars.org/) logic.

Check out the [nebula-clojure-plugin page](https://github.com/nebula-plugins/nebula-clojure-plugin) for details on how to use it.

## Core Plugins
These plugins don't provide any significant value by themselves, but generally are used with some other plugin or infrastructure component.

### gradle-info-plugin
The goal of this plugin is to collect metadata about the environment where the Gradle build is being executed. 

Check out the [gradle-info-plugin GitHub page](https://github.com/nebula-plugins/gradle-info-plugin) for details on how to use it.

### gradle-scm-plugin
This plugin is the foundation of the [gradle-git-scm-plugin]() and can be used to build other scm related Gradle plugins.

Check out the [gradle-contacts-plugin GitHub page](https://github.com/nebula-plugins/gradle-scm-plugin) for details on how to use it.

### gradle-warnings-plugin
A plugin that makes it easier for Gradle plugin developers to send warning messages to the user that will be emitted at the end of the build. 

Check out the [gradle-warnings-plugin GitHub page](https://github.com/nebula-plugins/gradle-warnings-plugin) for details on how to use it.

### nebula-core
Common classes shared by Nebula plugins. Adds useful Gradle tasks such as Download, Unzip and Untar.

Check out the [nebula-core-plugin GitHub page](https://github.com/nebula-plugins/nebula-core-plugin) for details on how to use it.

## Deprecated

### nebula-test

The [nebula-test](https://github.com/nebula-plugins/nebula-test) plugin was extremely useful in ensuring we can easily test our plugins. However, Gradle has begun to integrate these concepts into Gradle core. As a result, we recommend using [Gradle TestKit](https://docs.gradle.org/current/userguide/test_kit.html) instead of nebula-test.

### gradle-webpack-plugin

The [gradle-webpack-plugin](https://github.com/nebula-plugins/gradle-webpack-plugin) was a short lived experiment in executing [webpack](https://webpack.github.io/) from Gradle. We never invested in this project and as a result do not consider this plugin production ready or supported.

### gradle-blacklist-plugin

The [gradle-blacklist-plugin](https://github.com/nebula-plugins/gradle-blacklist-plugin) was the predecessor to the [gradle-resolution-rules-plugin](https://github.com/nebula-plugins/gradle-resolution-rules-plugin). Since the gradle-blacklist-plugin was only able to impact a single project at a time, it's value was limited. We recommend using the [gradle-resolution-rules-plugin](https://github.com/nebula-plugins/gradle-resolution-rules-plugin) instead. 

### nebula-blob-plugin
The [nebula-blob-plugin](https://github.com/nebula-plugins/nebula-blob-plugin) was a small experimental plugin of limited value we no longer plan to support it. 
