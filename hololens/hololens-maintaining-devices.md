---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: millerevan
manager: lolab
ms.reviewer: lavinds
ms.topic: article
audience: ITPro
ms.date: 7/15/2022
ms.localizationpriority:
appliesto:
- HoloLens 2
---

# Maintaining devices

There are several maintenance tasks that are commonly run or run on a schedule. Here we&#39;ll cover some of the most common ones that are run and define when they run and their behaviors.

- MDM Sync
- OS Updates
- App updates from the Store
- App updates from MDM
- Collect logs via MDM

While looking at the devices we want to perform these maintenance tasks they can be put into 3 categories.

**Active Use:** The device is awake, and the display is on. The device is likely being used by someone and on battery. Although as long as the device is awake it doesn&#39;t matter if it&#39;s plugged into a power source or has been temporarily set down.

**Modern Standby - with AC power:** The device is put away and plugged into power. This could be a AC adapter for one device, or a charging cabinet. This state, combined with Wi-Fi connectivity, is the recommended state for maintenance.

**Modern Standby - Battery only:** The device has been left somewhere, but without power. In this state the device will not sync with MDM or perform updates of any kind. This is the least useful state to leave the device in. It is advised that you take best efforts to put your devices away with power. Because these devices don&#39;t perform any of these maintenance tasks while in this state, we will exclude this state from the rest of the article.

NOTE: Plugging in a device that is off will turn the device on, placing it in active use temporarily, and then it will fall asleep into Modern Standby on AC power. If a device is currently in Modern Standby plugging it into an AC power source won&#39;t wake it up into Active Use.

## MDM Sync

An MDM sync is when a device communicates with the MDM provider. Looking for updated policies, confirming compliance, and reports information from the device to MEM.

When do MDM syncs trigger?

- Enrolled devices will sync every 8 hours.
- [Newly enrolled devices sync frequently, increasing the interval until it reaches 8 hours by the end of the first day](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).
- Can be manually triggered on device via the Settings app.
- Can be manually triggered via IT Admin via MEM Admin portal.

MDM sync Behavior:

| Active Use | Modern Standby - with AC power |
| --- | --- |
| Yes it will sync. | Yes it will sync. |

## OS Updates

An OS Update is when the operating system updates. Sometimes these updates are minor and are quality of life updates or security fixes, and sometimes they add brand new features to the device. As such it&#39;s best to keep your devices up to date so they are all on the latest version.

When do OS updates trigger?

- Scans are automatic roughly every 22 hours.
- If a scan was missed, the device will scan on the next boot.
- Can be manually triggered on device via the Settings app.

MDM sync Behavior:

| Active Use | Modern Standby - with AC power |
| --- | --- |
| Scans for OS updates.Downloads OS updates. <br>  - Will not install automatically while in use. <br>  - Will not install and restart until connected to power. | Can scan, download, and update the OS outside of active hours. |

Due to the behaviors of OS updates, where the device can be scanned for and downloaded while in use, but won&#39;t actually install and update until the device is out of active hours and on power, we highly recommend that when the devices done being used, they are placed on AC power when put away.

Information on current releases can be found in our [release notes](hololens-release-notes.md).

For more information on how to restrict updates read about how to [manage HoloLens updates](hololens-updates.md).

## App updates from the Store

Keeping your apps up to date is something that most people want. If you apps are coming from the store then they should auto update, but there is some complexity to it. It&#39;s also important to know that the following information is relevant for apps that are hosted on the Microsoft Store app. This means that inbox apps (such as Remote Assist, Guides or the Store app itself), apps downloaded from the store, or from your private store via Windows Store for Business will all receive updates via the store. Apps not installed via these means will need to be updates in the same way they were installed.

When do app updates from the store trigger?

- Scans are automatic roughly every 24 hours for updates.
  - If an update is found, it will have low priority state for 2 days and will defer install if:
    - The user is present
    - The user is predicted to come back to the machine in 90 minutes
    - The machine is on battery
  - After 2 days, the installation goes to a higher priority and will install within 24 hours
- Can be [manually triggered](holographic-store-apps#update-apps.md) on device via the Store app
  - This does not have the same restrictions as automatic updates and will be installed right away
- Cannot be triggered remotely by IT Admin

Store app update Behavior:

| Active Use | Modern Standby - with AC power |
| --- | --- |
| Can download an app but won&#39;t update while app itself is in use. | The app will download and update, outside of active hours. |

See more about [deploying apps via the store](app-deploy-store-business.md).

## App update from MDM

You may be hosting your apps via MDM, such as MEM (Microsoft Endpoint Manager, formerly known as Microsoft Intune). If your apps are LOB apps (Line of Business apps) hosted on MEM, and you&#39;ve updated them, then anyone who has those apps installed on their devices will also receive an update. However, these updates don&#39;t occur at the same time as the more frequent MDM syncs.

When do LOB app updates from MDM trigger?

- Enrolled devices will download all required apps after enrolling
- Device will scan automatically roughly every 24 hours for updates to LOB apps
- Process is not manually initiated

LOB app update from MDM Behavior:

| Active Use | Modern Standby - with AC power |
| --- | --- |
| Can download and update an app, will close app if it&#39;s being used. | Can download and update an app. |

## Collect logs via MDM

Log collection is unique to this list, as it does not run automatically. However, log collection in this method is useful because it can be initiated remotely to investigate a device. This will allow you to diagnose a device after collecting logs.

What triggers MDM log collection:

- Log collection is triggered manually by IT Admin
- Process is not run automatically

Log collection via MDM Behavior:

| Active Use | Modern Standby - with AC power |
| --- | --- |
| Can download and update an app, will close app if it&#39;s being used. | Can download and update an app. |

Read more about [log collection on HoloLens](hololens-diagnostic-logs#diagnosticlog-csp.md).

Read about how to [collect logs via MDM](/mem/intune/remote-actions/collect-diagnostics).
