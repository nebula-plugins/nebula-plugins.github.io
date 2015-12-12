---
layout: video-page
title: Guiding to Building Gradle Plugins
id: gradle_summit_2015_rspieldenner   
youtube_id: "H1XNEixAbeU"
---                     
                        
## Guide to Building Gradle Plugins (Rob Spieldenner)

Netflix has had deep experience building plugins over the past few years. This talk focuses on techniques learned during this process.

This talk will go into how we plan and develop configurable, tested gradle plugins for https://github.com/nebula-plugins. We’ll go through the lessons we have learned developing plugins over the last few years. Techniques will be demonstrated for how to respond to the presence of other plugins and how to allow configuration of tasks and other parts of the plugin via extensions and command line properties. Strategies and code samples of what features should be unit vs integration tested will be shown using the base spock specs and helpers from nebula-test.