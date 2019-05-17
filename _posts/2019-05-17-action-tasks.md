---
layout: post
title: "Action tasks in action"
description: Control Locus Map over any other application may be useful, let's try it.
comments: true
tags: 
 - locus-map
 - intent
---

# Basics

Let's start with the hypotetical situation. You sit on the bike and now wants to enable certain recording profile, start map rotation, start GPS itself and so on. How to do it quickly without wasting a few minutes of changing old settings when I planned a trip at home?

There are solutions. One of the best is to use [Presets](https://docs.locusmap.eu/doku.php?id=manual:user_guide:settings:presets). Anyway, if you want interesting kind of flexibility and feel little "geeky", continue reading.

# Action tasks

In 2018, we have introduced a very interesting concept of controlling Locus Map over Broadcast intents, we internally call it `Action tasks`. Its possibilities are documented in our [Locus API repository](https://github.com/asamm/locus-api/wiki/Action-tasks-(Broadcasts)), but let's try to use it practically for example for our task above.

Among Locus Map application, you will also need a tool that is able to send configured intents to any other application. Tasker or MacroDroid are good examples. Anyway you may use this system also from own Android application.

## Main posibilities

* control map like zooming, centering, directly move with map
* control Track recording system
* control Live tracking
* enable certain Preset
* open certain app screens

## 1. Preparation

* install [Locus Map](https://play.google.com/store/apps/details?id=menion.android.locus) (you may use [Locus Classic](https://play.google.com/store/apps/details?id=menion.android.locus.pro) as well)
* install [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm) application
* install [Locus Map Tasker Plugin](https://play.google.com/store/apps/details?id=falcosc.locus.addon.tasker) as an optional step for much easier setup of the task (method 3b)
* validate both apps works correctly and start Tasker

## 2. Create a Tasker task

* open `Tasker` > tab `TASKS`
* FAB (floating action button) `+` button > name your new task. I created `Start bike ride` > `OK`
* we are in our new task

## 3a. Define Locus action (the hard way)
* `+` to add new action, filter `intent` and select `Send intent`

![img]({{ '/assets/images/post_action_tasks_01.png' | relative_url }}){: .center-image }

* now we need to specify parameters for new action. Following fields have to be filled:

  * `Action`: `com.asamm.locus.ACTION_TASK`
  * `Extra`: `tasks: { preset: { action: "start", name: "Bike" }, track_record: { action: "start", name: "Biking" } }`
  * `Package`: `menion.android.locus` (or `menion.android.locus.pro` for Locus Classic)

## 3b. Define Locus action (the easy way)

This step require installed Locus Map Tasker Plugin.

* `+` to add new action > Plugin > Locus Map Addon Tasker Plugin > Execute Action Task
* in Configuration section tap on the pencil on the right side

Now you see all supported actions you may define. Let's set the same system as for the hard way before.

* check `Preset apply` > insert `Bike`
* check `Track record` > `start` and insert `Biking`
* confirm by `OK`

Addon completely generates complicated JSON text we had to define before, nice right?

## 4. Usage

Now it is completely on you, how you execute the defined task.

<hr />

## Explanation of `extra tag

In section 3a. we defined `extra` tag for Tasker. What are parameters in this special definition?

  * `Action` is constant that will be handled by Locus Map itself (only)
  * `Extra`: define task itself "Biking"`
    * `preset` as identification of "work with Presets". Mode precisely `start`s preset named `Bike`.
    * `track_record` as identification of "work with track recording system".  Mode precisely `start` track-recording with profile names `Biking`.

{% highlight java %}
{ 
  preset: { 
    action: "start", 
    name: "Bike" 
  },
  track_record: {
    action: "start",
    name: "Biking"
  }
}
{% endhighlight %}

  * `Package`: reguired identification of target application (restrictions since Android 8.0
