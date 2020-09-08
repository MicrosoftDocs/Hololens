---
title: Windows Defender Application Control - WDAC
description: Overview on what WDAC is and how to use to manage HoloLens devices.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 09/8/2020
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens 2
---

# Windows Defender Application Control - WDAC

WDAC allows an IT Admin to configure their devices to block the launch of apps on devices. This is different than methods of device restriction such as Kiosk mode, where  the user is presented with a UI that hides the apps on the device but they can still be launched. While WDAC is implemented, the apps are still visible in the All Apps list but WDAC stops those apps and processes from being able to be launched by the device user.

>	[!NOTE]
>	When end users attempt to launch an app that is blocked by WDAC, on HoloLens they will not receive a notification about not being able to launch that app.

The following is a guide for users to learn how to [use WDAC and Windows PowerShell to allow or block apps on HoloLens 2 devices with Microsoft Intune](https://docs.microsoft.com/mem/intune/configuration/custom-profile-hololens).
