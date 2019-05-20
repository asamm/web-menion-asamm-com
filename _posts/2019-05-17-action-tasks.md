---
layout: post
title: "Action tasks in action"
description: Control Locus Map over any other application may be useful, let's try it.
comments: true
tags: 
 - locus-map
 - api
---

# Basics

Let's start with the hypotetical situation. You sit on the bike and now wants to enable certain recording profile, start map rotation, start GPS itself and so on. How to do it quickly without wasting a few minutes of changing old, not anymore used, settings?

There are solutions. One of the best is to use [Presets](https://docs.locusmap.eu/doku.php?id=manual:user_guide:settings:presets). Anyway, if you want interesting kind of flexibility and feel little "geeky", continue reading.

# Action tasks

In 2018, we introduced a very interesting concept of controlling Locus Map over Broadcast intents, internally called `Action tasks`. Its possibilities are documented in our [Locus API repository](https://github.com/asamm/locus-api/wiki/Action-tasks-(Broadcasts)), but let's try to use it practically for example for our task above.

Among Locus Map application, you will also need a tool that is able to send configured intents to any other application. Tasker or MacroDroid are good examples. You may use this system also from own Android application.

Related posts that may help with the practical part:
* [Action tasks: Tasker]({{ site.baseurl }}{% post_url 2019-05-20-action-tasks-tasker %})
* [Action tasks: MacroDroid]({{ site.baseurl }}{% post_url 2019-05-20-action-tasks-macrodroid %})

## Main possibilities

* control map like zooming, centering, directly move with the map
* control Track recording system
* control Live tracking
* enable certain Preset
* open certain app screens

## Principle

The feature is based on the core Android system called [Broadcast intent](https://developer.android.com/guide/components/broadcasts). With this method, one application is able to send predefined data (text, numbers, ...) to the second application. Values are usually stored in the internal container as key/value pairs.

Locus Map is able to catch defined intent and execute actions that another application send.

Actions are defined as JSON object. `Key` value is tasks. The `value` itself is defined as JSON object.

Sample of how parameters of `intent`, together with JSON object may look like is below. Some more samples may be found on the [API documentation](https://github.com/asamm/locus-api/wiki/Action-tasks-(Broadcasts)#samples) page.

## Example of Action

  * `Action` is constant that will be handled by Locus Map itself (only)
  * `Package`: reguired identification of target application (restrictions since Android 8.0
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

