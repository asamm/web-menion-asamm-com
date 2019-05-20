---
layout: post
title: "Action tasks: MacroDroid"
description: Work with Action tasks over MacroDroid application is easy, when you know how to do it.
comments: true
tags: 
 - locus-map
 - api
---

# Basics

We already covered Locus Actions in the [previous post]({{ site.baseurl }}{% post_url 2019-05-17-action-tasks %}), also it's usage with [Tasker application]({{ site.baseurl }}{% post_url 2019-05-20-action-tasks-tasker %}). This post will try to bring some light to the usage of this nice feature with the cooperation with MacroDroid application.

# How to: MacroDroid

## 1. Preparation

* install [Locus Map](https://play.google.com/store/apps/details?id=menion.android.locus) (you may use [Locus Classic](https://play.google.com/store/apps/details?id=menion.android.locus.pro) as well)
* install [MacroDroid](https://play.google.com/store/apps/details?id=com.arlosoft.macrodroid) application
* validate both apps works correctly and start MacroDroid

## 2. Create a MacroDroid macro

* open `MacroDroid` > tap `Add Macro`

* tab Triggers
* MacroDroid Specific > Empty Trigger

* tab Actions
* Connectivity > Send Intent
* specify necessary parameters

  * **Target**: `Broadcast`
  * **Action**: `com.asamm.locus.ACTION_TASK`
  * **Package**: `menion.android.locus` (or `menion.android.locus.pro` for Locus Classic)
  * **Extra1**
    * **name**: `tasks`
    * **value**: `{ preset: { action: "start", name: "Bike" }, track_record: { action: "start", name: "Biking" } }`

![img]({{ '/assets/images/post_action_tasks_03.png' | relative_url }}){: .center-image }

* **Ok** to confirm defined action

* bottom "+" fab button to confirm macro
* set metadata and confirm your new macro

## 3. Usage
There exist many methods of how to use defined action.

* simple test: long click on an action in the list > **Test actions**.
* profi usage: modify macro and define own specific **Trigger**.
