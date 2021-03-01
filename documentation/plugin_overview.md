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
- Deprecated / Maintenance mode

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

## Release management

There are a number of Nebula plugins that assist in the publishing and releasing of software, based on the needs of Netflix services.

### nebula-publishing-plugin
The goal of this plugin is to make it dirt simple to publish your Java library to a Maven or Ivy repository without all of the boilerplate Gradle DSL.

Check out the [nebula-publishing-plugin GitHub page](https://github.com/nebula-plugins/nebula-publishing-plugin) for details on how to use it.

### nebula-release-plugin
The goal of this plugin is to simplify a [Semantic Versioning](http://semver.org/) approach to releasing Gradle based builds.    

Check out the [nebula-release-plugin GitHub page](https://github.com/nebula-plugins/nebula-release-plugin) for details on how to use it.

### nebula-bintray-plugin
The goal of this plugin is to remove much of the boilerplate required in using the existing [gradle-bintray-plugin](https://github.com/bintray/gradle-bintray-plugin). The goal is allow users to apply the plugin and publish to [Bintray](https://bintray.com/) with very little ceremony.

Check out the [nebula-bintray-plugin page](https://github.com/nebula-plugins/nebula-bintray-plugin) for details on how to use it.

### gradle-git-scm-plugin
The goal of this plugin is to allow for the execution of [Git](https://git-scm.com/) commands from a Gradle build.

Check out the [gradle-git-scm-plugin page](https://github.com/nebula-plugins/gradle-git-scm-plugin) for details on how to use it.

### gradle-stash-plugin
The goal of this plugin is to provide tasks that allow the management of a Git repository in a [Bitbucket server (formerly Stash)](https://www.atlassian.com/software/bitbucket/server).

Check out the [gradle-stash-plugin GitHub page](https://github.com/nebula-plugins/gradle-stash-plugin) for details on how to use it.

## Miscellaneous
The Nebula team has built a variety of additional miscellaneous plugins over time, each with a unique purpose.

### gradle-lint-plugin

The [Gradle Lint](https://github.com/nebula-plugins/gradle-lint-plugin) plugin is a pluggable and configurable linter tool for identifying and reporting on patterns of misuse or deprecations in Gradle scripts and related files.  It is inspired by the excellent ESLint tool for Javascript and by the formatting in NPM's [eslint-friendly-formatter](https://www.npmjs.com/package/eslint-friendly-formatter) package.

It assists a centralized build tools team in gently introducing and maintaining a standard build script style across their organization.

### gradle-java-cross-compile-plugin

The [gradle-java-cross-compile](https://github.com/nebula-plugins/gradle-java-cross-compile-plugin) plugin automatically configures the bootstrap classpath when the requested `targetCompatibility` is less than the current Java version, avoiding:

```
warning: [options] bootstrap class path not set in conjunction with -source 1.7
```

The plugin supports Java, Groovy joint compilation, and Kotlin. The plugin locates JDKs via either:

* Environment variables
   * In the form JDK1x where x is the major version, for instance JDK18 for Java 8
* Default installation locations for MacOS, Ubuntu and Windows
   * Where more than one version of the JDK is available for a given version is available, the highest is used
   * The lookup prefers Oracle JDKs, but falls back to OpenJDK (Zulu) where possible
* [SDKMAN!](http://sdkman.io/) JDK candidates
   * The lookup prefers JDKs with no suffix, then Oracle JDKs then OpenJDK (Zulu)

### nebula-project-plugin
The goal of this project is to make it easy to set up a Java project the Netflix way. While it is tailored to Netflix's view of project setup, the defaults are sane enough for most projects. Applying this plugin:

- adds a `*-javadoc.jar` and a `*-sources.jar` as build outputs
- applies the [gradle-info-plugin](https://github.com/nebula-plugins/gradle-info-plugin)
- applies the [gradle-contacts-plugin](https://github.com/nebula-plugins/gradle-contacts-plugin)

Check out the [nebula-project-plugin page](https://github.com/nebula-plugins/nebula-project-plugin) for details on how to use it.

### gradle-contacts-plugin
A feature provided by Maven that is missing from Gradle is the `<developers/>` section, which denotes the contact information for the owners of the project. The purpose of the  [gradle-contacts-plugin](https://github.com/nebula-plugins/gradle-contacts-plugin) is to provide comparable features to Gradle.  

Check out the [gradle-contacts-plugin GitHub page](https://github.com/nebula-plugins/gradle-contacts-plugin) for details on how to use it.

### gradle-extra-configurations-plugin
The goal of this plugin is to make it easier to add either an `optional` or `provided` configuration to an existing Gradle project.  

Check out the [gradle-extra-configurations-plugin page](https://github.com/nebula-plugins/gradle-extra-configurations-plugin) for details on how to use it.

### gradle-override-plugin
This plugin allows you to override arbitrary Gradle properties via command line args. Convenient if you want to quickly change values that are normally static for one off builds.

Check out the [gradle-override-plugin page](https://github.com/nebula-plugins/gradle-override-plugin) for details on how to use it.

### nebula-clojure-plugin
An opinionated plugin that wraps the [clojuresque](https://bitbucket.org/clojuresque/clojuresque) gradle plugin, removing the [Clojars](https://clojars.org/) logic.

Check out the [nebula-clojure-plugin page](https://github.com/nebula-plugins/nebula-clojure-plugin) for details on how to use it.

### gradle-netflixoss-project-plugin

Gradle plugin to setup common needs for Netflix OSS projects

This plugin is to support projects in the NetflixOSS org (and it isn't meant to be used elsewhere). It is at its essence just a combination of other plugins that are common to all NetflixOSS projects, with some additional configuration. The primary responsibilities is to:

* Provide release process
* Configure publishing
* Recommend license headers

This project could be used as an example of how a "project plugin" could work. A "project plugin" is a Gradle plugin that provides consistency across many projects, e.g. in a Github org or an enterprise.

## Core Plugins
These plugins don't provide any significant value by themselves, but generally are used with some other plugin or infrastructure component.

### gradle-info-plugin
The goal of this plugin is to collect metadata about the environment where the Gradle build is being executed.

Check out the [gradle-info-plugin GitHub page](https://github.com/nebula-plugins/gradle-info-plugin) for details on how to use it.

### gradle-scm-plugin
This plugin is the foundation of the [gradle-git-scm-plugin]() and can be used to build other scm related Gradle plugins.

Check out the [gradle-scm-plugin GitHub page](https://github.com/nebula-plugins/gradle-scm-plugin) for details on how to use it.

### nebula-gradle-interop

Kotlin library providing extensions to assist with Gradle iterop and backwards compatibility.

Check out the [nebula-gradle-interop GitHub page](https://github.com/nebula-plugins/nebula-gradle-interop).

## Deprecated / Maintenance mode

### gradle-metrics-plugin
The goal of this plugin was to capture and publish metadata and build performance metrics to a centralized location so the Netflix Build Tools team could analyze build trends. The [gradle-metrics-plugin](https://github.com/nebula-plugins/gradle-metrics-plugin) publishes a json document to an [ElasticSearch](https://www.elastic.co/products/elasticsearch) cluster by default.

Check out the [gradle-metrics-plugin GitHub page](https://github.com/nebula-plugins/gradle-metrics-plugin) for details on how to use it.

### nebula-test

The [nebula-test](https://github.com/nebula-plugins/nebula-test) plugin was extremely useful in ensuring we can easily test our plugins. However, Gradle has begun to integrate these concepts into Gradle core. As a result, we recommend using [Gradle TestKit](https://docs.gradle.org/current/userguide/test_kit.html) instead of nebula-test.

### nebula-kotlin-plugin

The [nebula-kotlin](https://github.com/nebula-plugins/nebula-kotlin-plugin) plugin was extremely useful in providing the Kotlin plugin via the Gradle plugin portal, and added ergonomic improvements over the default plugin:

* Allows Kotlin library versions to be omitted, inferring them automatically from the plugin version
* For Kotlin 1.1 and later, sets the -jvm-target and uses the jre standard library based on the sourceCompatibility
* Use the [gradle-java-cross-compile-plugin](https://github.com/nebula-plugins/gradle-java-cross-compile-plugin) to set the `targetJdk` if desired
* Bundles the `kotlin-allopen` and `kotlin-noarg` plugins to allow them to be applied without adding them manually to the classpath

However, this plugin is in maintenance mode but will continue to receive 1.2 and 1.3 Kotlin releases. JetBrains has deprecated the existing `jvm` plugin and replaced it with the `multiplatform` plugin.

The multiplatform plugin is a complete migration from the legacy plugin and provides many of the ergonomic features, such as JVM target configuration and Kotlin library version management that this plugin provided. If you have a project that will move to 1.4 once it's released you should migrate to `multiplatform`.

### nebula-core
Common classes shared by Nebula plugins. Adds useful Gradle tasks such as Download, Unzip and Untar.

Check out the [nebula-core-plugin GitHub page](https://github.com/nebula-plugins/nebula-core-plugin) for details on how to use it.
