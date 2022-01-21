---
title: Set up users on HoloLens 2 quickly
description: Learn how to set up your HoloLens 2 for users quickly, and what can happen that affects set up. 
ms.date: 1/19/2022
keywords: hololens
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: high
appliesto:
- HoloLens 2
---

# HoloLens 2 new user best practices

Often times organizations have many devices and lots of different people who use those devices. When people are looking to use a HoloLens 2 device they often want to get straight to their app. This can sometimes be hindered by having to do additional set up. In this article we'll cover the best ways to reduce set up time, best practices, and cover variations in logging into a device.

## Best practices

The following are the average times for each scenario. Time was started from the moment the user interacted with the device after it was booted, and stopped when they were in the Remote Assist app.

| Scenario start to app launch                                                    | Average time in minutes |
|---------------------------------------------------------------------------------|-------------------------|
| User exists on device, sign in                                                  | 0:30                    |
| New user on device with first experience policies <sup>1</sup>                  | 3:15                    |
| New user on device                                                              | 5:00                    |
| Device needs to go through first time set up (OOBE)                             | 6:00                    |
| Device needs to go through first time set up (OOBE) using provisioning packages |                         |
| Device needs to go through first time set up (OOBE) and Autopilot               | 9:30                    |

<sup>1</sup> - These can be from either a provisioning package previously applied or from MDM, possibly applied during Autopilot.

### Use a device you've already used to get to your app fastest

The key take away from this chart, is if you can use a device you've used before then you can sign in and use the app in less than a minute. If you have to go through set up then you will go over the minute mark.

Physically label your devices. Placing label either on the rear outer cover, or the outer arms closer to the front so they do not go into the rear outer cover. See [this diagram](images/hololens2-exploded-view-diagram.png) to see the names of parts.

### Use policies to speed up your set up

If you want to speed up both Out of Box Experience (OOBE) set up or for each new user on devices, then you want to set first experience policy.

If you are using Windows Configuration Designer to create provisioning packages, you can use the wizard to **Provision HoloLens devices** -> **Provision HoloLens 2 devices** and ensure you properly configure everything in the Set up device page to help streamline OOBE.

<br>
<img src="images/WCD-OOBE-skip.jpg" width="500px" alt="WCD OOBE First Experience">

[FirstExperience (Windows Configuration Designer reference)](/windows/configuration/wcd/wcd-firstexperience)

There are three other policies that affect the set up experience, by configuring them as well you reduce the number of screens in the set up experience.

- Telemetry : Policy/System/AllowTelemetry
- Speech :  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! AllowCORTANA?
- Location : Policy/System/AllowLocation

## Set up conditions

In general there are a few scenarios when you pick up a device. In those scenarios there can also be some variations that can speed up (or slow down) your set up. The general states you can find a device in when picking it up to use it are:

- You've signed into this device already
- You haven't signed into this device yet
- No one has set up this device yet

The modifiers that can increase or decrease the time to set up are typically:

- You use a provisioning package to apply settings all at once, instead of manually during set up
- You your device already has helpful set up policies, due to someone else applying them via provisioning or from going through Autopilot set up
- Your device needs to go through autopilot, which takes some time
- Your device was connected to the Internet and went through autopilot already, saving time
- Your device's battery is low which may pause Autopilot if it occurs

## Set up flows

Let's walk through different scenarios in which your device needs to be set up. This excludes signing back into a device that already has your account on it:

**Instructions:** *Click the link matching what you see, your selection will determine the tabs you see in the next section.*
<br> When you first boot on the device what do you see?


