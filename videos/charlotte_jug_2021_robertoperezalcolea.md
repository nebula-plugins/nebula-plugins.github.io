---
layout: video-page
title: Dependency Management at Scale
id: charlotte_jug_2021_robertoperezalcolea   
youtube_id: "jkCKjrWDMSg"
---                     

## Dependency Management at Scale (Roberto Perez Alcolea)

In an environment where software is constantly changing and new versions of a library should be distributed across thousands of projects, how can you know that your projects are using the right version of a given dependency? What if a OSS library introduces a security vulnerability and you need to make sure that no one is using it in your company? What if an internal library introduces a bad change and you need everyone to upgrade/downgrade? Automating these for hundreds or thousands of engineers is crucial.

At Netflix, engineers are not immune to the cost of dependency updates. Library owners publish new versions of their code without a comprehensive understanding of the organizational impact. Application owners ingest new library versions that can fail in obvious or subtle ways, leading to decreased confidence and slower organizational velocity. But these are problems we understand, and tooling can help.

After years of evolving our build, we've developed a few conceptual models of dependency management. Dependency management is hard, and in all cases there are compromises, and you the build owner should be conscious of which choices you're making and what else is available.

On this session, we'll introduce some tools we've developed at Netflix which attack dependency issues on a large scale to make it easier for every JVM engineer at Netflix and how we react to the scenarios mentioned above.
