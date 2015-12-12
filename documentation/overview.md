---
layout: toc-page
title: Overview
id: overview
lang: en
---

* Table of contents. This line is required to start the list.
{:toc}

# Overview

Provide an overview of Nebula


# Nebula Plugins

Nebula is not a singular product, but a collection of [Gradle](http://www.gradle.org) plugins that can be 
used together or individually. We have divided up the Nebula plugins into categories 

## Java dependency management
Gradle provides a substantial dependency management facility, but we have found these capabilities insufficient for the
needs of Netflix engineers. As we result, we have built a few plugins that e

### gradle-dependency-lock-plugin
Enables teams to shrink wrap their transitive dependency graph, while still maintaining dynamic dependency declarations 
in their build file. 

Useful for ensuring repeatable builds over time. It creates a `dependency.lock` file containing 
the complete dependency graph for the application.

### nebula-dependency-recommender-plugin
Provides facilities to produce and consume a Maven BOM. Producers can provide a single file that defines a graph of 
dependency versions that all work together. Consumers can defer specific versions to an authoritative source, via a BOM.

Useful for teams that consume a collection of libraries from another team that all need to be updated in lockstep

### gradle-resolution-rules-plugin
Centralize organization wide dependency rules enabling the fine grain control across all projects.

Useful for an organization that wants to rapidly eliminate dependencies or versions from the dependency graph.
OS Packaging

### gradle-ospackage-plugin
Provides a simple DSL to create RPM or Debian packages.

### nebula-ospackage-plugin
Opinionated version of the gradle-ospackage-plugin, such as an understanding of the Gradle Application plugin and the 
creation of daemon processes.

## Release management

### nebula-publishing-plugin
Provides sane defaults for publishing Maven or Ivy style artifacts, eliminating the boilerplate required by Gradle’s 
publishing block.

### nebula-release-plugin 
Release management plugin based on semantic versioning and git.

### gradle-scm-plugin
An interface plugin that defines a set of scm related functions, should not be implemented by itself.

### gradle-git-scm-plugin
A git implement implementation of the gradle-scm-plugin.

### gradle-stash-plugin
Provides methods to interact with Stash during a build.

### nebula-bintray-plugin
Provides sane defaults for publishing artifacts to Bintray, eliminating the boilerplate required by the existing 
gradle-bintray-plugin.

## Plumbing

### nebula-project-plugin
Add some healthy defaults to a Gradle project, eliminating boilerplate. Currently the plugin:

- adds Javadoc and Sources jar records information about the build and stores that in jar (using the gradle-info-plugin)
- applies the gradle-contacts-plugin

### gradle-metrics-plugin
Capture and publish a snapshot of every build to ElasticSearch.

### gradle-contacts-plugin
Adds contact information to a Gradle build definition, similar to a Maven POM.

### gradle-info-plugin
Exposes project information and writes it to the META-INF/manifest.mf.

### nebula-core
Common classes shared by Nebula plugins. Adds useful Gradle tasks such as Download, Unzip and Untar.

## Miscellaneous

### gradle-aggregate-javadocs-plugin

### gradle-extra-configurations-plugin

### gradle-override-plugin

### nebula-clojure-plugin
Smaller wrapper around clojuresque.

## Deprecated (or soon will be)

### nebula-test

### gradle-webpack-plugin

### gradle-blacklist-plugin

### gradle-warnings-plugin

### nebula-blob-plugin
