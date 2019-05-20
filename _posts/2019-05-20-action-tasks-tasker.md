---
layout: post
title: "Action tasks: Tasker"
description: Work with Action tasks over Tasker application is easy. With existing add-on it is very easy.
comments: true
tags: 
 - locus-map
 - tasker
 - api
---

# Basics

In the [previous post]({{ site.baseurl }}{% post_url 2019-05-17-action-tasks %}) we talked about quite a new system of Action tasks, so suggest to read basics and why it may be useful for you.

In this post, let's look on how to use them even if you are not Android developer. Today with the help of the Tasker application.

# How to: Tasker

## 1. Preparation

* install [Locus Map](https://play.google.com/store/apps/details?id=menion.android.locus) (you may use [Locus Classic](https://play.google.com/store/apps/details?id=menion.android.locus.pro) as well)
* install [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm) application
* install [Locus Map Tasker Plugin](https://play.google.com/store/apps/details?id=falcosc.locus.addon.tasker) as an optional step for much easier setup of the task (method 3b)
* validate both apps works correctly and start Tasker

## 2. Create a Tasker task

* open `Tasker` > tab `TASKS`
* FAB (floating action button) `+` button > name your new task. I created `Start bike ride` > `OK`
* we are in our new task

![img]({{ '/assets/images/post_action_tasks_02.png' | relative_url }}){: .center-image }

## 3a. Define Locus action (the hard way)
* `+` to add new action, filter `intent` and select `Send intent`

![img]({{ '/assets/images/post_action_tasks_01.png' | relative_url }}){: .center-image }

* now we need to specify parameters for new action. Following fields have to be filled:

  * **Action**: `com.asamm.locus.ACTION_TASK`
  * **Extra**: `tasks: { preset: { action: "start", name: "Bike" }, track_record: { action: "start", name: "Biking" } }`
  * **Package**: `menion.android.locus` (or `menion.android.locus.pro` for Locus Classic)

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
