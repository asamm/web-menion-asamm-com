---
layout: post
title: "Control of Locus Map over NFC"
description: Interested in quick control of Locus Map application over NFC tags? You're on the correct place.
tags: 
 - locus-map
 - nfc
---

# History

[NFC](https://en.wikipedia.org/wiki/Near-field_communication) system started it's a bigger boom in ~2014, when Google and Apple added bigger support for NFC payments and all this stuff around. It was the same year when I've added basic support for NFC into Locus Map application.

The main idea was to automatize and simplify repeatable situations like set something, enable/disable something, etc.Configured NFC tag on the bike was one possible solution.

Unfortunately capacity of these tags was really low and together with its price, NFC usage in Locus Map was always one of the less used functions. Well, this won't any longer be true as we decided to remove it from Locus Map completely.

What?

# NFC support

We may use alternative approach. Tasker application allows us to create and control Locus Map over so called `Action tasks` as I described in the [previous post]({{ site.baseurl }}{% post_url 2019-05-17-action-tasks %}). What if we should start certain task over NFC tag?

## 1. Preparation

* define task by method described in previous post
* prepare your nice new NFC tag, best some waterproof sticker that may be placed on bike
* rather validate once more that your device is NFC capable

## 2. Prepare event

* open `Tasker` > tab `PROFILES`
* FAB (floating action button) `+` button > `Event` > `Net` > `NFC Tag`

![img]({{ '/assets/images/post_nfc_01.png' | relative_url }}){: .center-image }

* tap magnifier icon in ID title and scan your tag. ID field should be filled.

![img]({{ '/assets/images/post_nfc_02.png' | relative_url }}){: .center-image }

* press back
* `Tasker` now offer available tasks, so choose your Start bike ride

And we are done!
