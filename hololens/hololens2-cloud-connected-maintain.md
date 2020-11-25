---
title: Deployment Guide – Cloud connected HoloLens 2 deployment at scale with Remote Assist - Maintain
description: Enroll HoloLens devices over a Cloud Connected network
keywords: HoloLens, management, cloud connected, Remote Assist, AAD, Azure AD, MDM, Mobile Device Management
author: evmill
ms.author: v-evmill
ms.reviewer: aboeger
ms.date: 12/04/2020
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: HoloLens
manager: yannisle
appliesto:
- HoloLens 2
---

# Maintain - Cloud connected Guide

## Updates

Microsoft designed Windows Update for Business to provide IT administrators with additional Windows Update-centric management capabilities, such as the ability to deploy updates to groups of devices and to define maintenance windows for installing updates.

Learn how to [manage HoloLens updates](https://docs.microsoft.com/hololens/hololens-updates) including scheduled days, scheduled time, and setting active hours on the device so it will update outside of working hours.

Remote Assist is a In-Box app, and can be update through the Microsoft Store app. For all apps that are downloaded through the Microsoft Store they can be [updated through the Microsoft Store](https://docs.microsoft.com/en-us/hololens/holographic-store-apps#update-apps) app itself manually.

## Support Plan

A support plan is an excellent thing to have in place. Having someone, or a group trained up on troubleshooting the enrollment process on HoloLens devices and also general use of the HoloLens device within your organization is useful. In order to allow your users to have the faster resolution of their issues we suggest that your escalation process is handled in a similar to this:

1. Your Support desk.
2. Your HoloLens Expert team
3. [HoloLens Docs](https://docs.microsoft.com/en-us/hololens/) / [HoloLens Troubleshooting Docs](https://docs.microsoft.com/hololens/hololens-troubleshooting)
4. [Contact Support](https://support.serviceshub.microsoft.com/supportforbusiness/create?sapId=e9391227-fa6d-927b-0fff-f96288631b8f)

## Development Plan

With your device successfully enrolled you are now prepared to deploy Line of Business apps (LOB apps) to your devices. These are custom apps built for your organization&#39;s needs.

If you already have a line of business app then you&#39;re ready to [deploy your app through MDM](https://docs.microsoft.com/hololens/app-deploy-intune). If you&#39;d prefer a different method then review the [application deployment overview for HoloLens 2](https://docs.microsoft.com/hololens/app-deploy-overview) to learn more methods of deploying your LOB app to your devices.

If you&#39;ve yet to create your own LOB app or are still in the process of creation then review our mixed reality development docs to [start designing and prototyping](https://docs.microsoft.com/windows/mixed-reality/design/design) or learn the core concepts to [get started with mixed reality development.](https://docs.microsoft.com/en-us/windows/mixed-reality/discover/get-started-with-mr)