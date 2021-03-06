---
title: Probing with Gradle
date: 2014-10-07T23:12:03+00:00
layout: post
permalink: /2014/10/07/probing-with-gradle/
image: /wp-content/uploads/2014/10/probe-gradle.png
categories:
  - Android
  - Free Software
  - General
  - Software
tags:
  - androiddev
  - build
  - gradle
  - layout
  - mozilla
  - planet
  - probe
  - proxy
  - view
---
Up until now, [Probe](https://github.com/lucasr/probe/) relied on dynamic view
proxies generated at runtime to intercept View calls. Although very convenient,
this approach greatly affects the time to inflate your layouts—which
limits the number of use cases for the library, especially in more
complex apps.

This is all changing now with Probe's brand new Gradle plugin which seamlessly
generates build-time proxies for your app. This means virtually no overhead at
runtime!

Using Probe's Gradle plugin is very simple. First, add the Gradle plugin as a
dependency in your build script.

```groovy
buildscript {
    ...
    dependencies {
        ...
        classpath 'org.lucasr.probe:gradle-plugin:0.1.3'
    }
}
```

Then apply the plugin to your app's _build.gradle_.

```groovy
apply plugin: 'org.lucasr.probe'
```

Probe's proxy generation is disabled by default and needs to be explicitly
enabled on specific build variants (build type + product flavour). For example,
this is how you enable Probe proxies in debug builds.

```groovy
probe {
    buildVariants {
        debug {
            enabled = true
        }
    }
}
```

And that's all! You should now be able to deploy interceptors on any part of
your UI. Here's how you could deploy an _OvermeasureInterceptor_ in an
activity.

```java
public final class MainActivity extends Activity {
   @Override
   protected void onCreate(Bundle savedInstanceState) {
       Probe.deploy(this, new OvermeasureInterceptor());
       super.onCreate(savedInstanceState);
       setContentView(R.id.main_activity);
   }
}
```

While working on this feature, I have changed _DexMaker_ to be an optional
dependency i.e. you have to explicitly add _DexMaker_ as a build dependency in
your app in order to use it.

This is my first Gradle plugin. There's definitely a lot of room for
improvement here. These features are available in the 0.1.3 release in Maven
Central.

As usual, feedback, bug reports, and fixes are [very
welcome](https://github.com/lucasr/probe/). Enjoy!
