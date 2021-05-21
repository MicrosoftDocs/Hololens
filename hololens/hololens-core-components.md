---
title: Planning HoloLens 2 deployment in a commercial environment
description: Learn about the core needs for deploying and managing HoloLens in enterprise environments, including infrastructure, azure active directory, and mobile device management.
ms.prod: hololens
ms.sitesec: library
ms.assetid: 88bf50aa-0bac-4142-afa4-20b37c013001
author: joyjaz
ms.author: v-jjaswinski
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.date: 05/21/2021
appliesto:
- HoloLens 2
---
# Planning HoloLens 2 deployment in a commercial environment

## Overview
> [!NOTE]
> This overview is intended to help IT professionals understand considerations for deploying and managing Microsoft HoloLens 2 devices within an organization. For device end users, see [The Basics](hololens2-setup.md) to get started.

HoloLens 2 runs on Windows 10 Holographic which provides organizations with robust, flexible, built-in mobile device and app management technologies. Windows 10 Holographic supports end-to-end device lifecycle management to give companies control over their devices, data, and apps. The HoloLens 2 can easily be incorporated into standard lifecycle practices, from device enrollment, configuration, and application management to maintenance and retirement using a comprehensive mobile device management solution.

The following steps can help guide you through the process of HoloLens 2 adoption within your organization.

| | |
|--|--|
| ![Step 1](images/1green.png)| <br/> **[Common Deployment Scenarios](hololens-requirements.md)**: Understand deployment scenarios and explore the core components needed to deploy HoloLens 2 devices. |
| ![Step 2](images/2green.png)| <br/> **[Prepare](#prepare)**: Become familiar with and setup the infrastructure essentials. |
| ![Step 3](images/3green.png) | <br/> **[Configure](#configure)**: Configure your essential components for a cloud-based deployment. |
| ![Step 4](images/4green.png) | <br/> **[Deploy](#deploy)**: Deploy your devices and distribute your applications securely and efficiently. |
| ![Step 5](images/5green.png) | <br/> **[Maintain](#maintain)**: Find out what's needed to properly maintain the state of your HoloLens 2 devices and ensure compliance with corporate policy. |

## Prepare

As you prepare to deploy HoloLens 2 to your corporate enterprise environment, there are certain essential infrastructure services required to support the full set of capabilities. 

| Component | Description |
|-----------|------------|
| [Azure AD](hololens-identity.md) | Provides identity and access management for the HoloLens 2  |
| [Mobile Device Management](hololens-mdm-configure.md)| Manages HoloLens 2 devices connected to your tenant  |
| [Wi-Fi Network](hololens-commercial-infrastructure.md)| Wi-Fi is available and devices can be connected to the Internet  |

## Configure

| Component | Description |
|-----------|------------|
| [Auto Enrollment](hololens-enroll-mdm.md#auto-enrollment-in-mdm) | After initial login, devices automatically register with Azure AD and enroll into MDM  |
| [Application Licenses](app-deploy-overview.md)| Can be applied to either users, user groups, or device groups  |
| [Azure Users and Groups](hololens2-corp-connected-configure.md#azure-users-and-groups) | Helps assign configurations and licenses for the HoloLens 2  |

## Deploy

Now that you have everything configured you should be ready to distribute devices. 

| Component | Description |
|-----------|------------|
| [Enrollment Validation](hololens2-corp-connected-deploy.md#enrollment-validation) | Validate the device has Azure AD Joined from Settings or the Azure Portal |
 [Certificate Validation](hololens2-corp-connected-deploy.md#wi-fi-certificate-validation) | Check settings and validate they have been distributed correctly |
| [Validate app installs](hololens2-corp-connected-deploy.md#validate-lob-app-install) | Confirm the app is present and working on your HoloLens 2 |

## Maintain

In enterprise IT environments, the need for security and cost control must be balanced against the desire to provide users with the latest technologies. Since cyberattacks have become an everyday occurrence, it is important to properly maintain the state of your Windows 10 devices. IT needs to control configuration settings, keeping them from drifting out of compliance, as well as enforce which devices can access internal applications. HoloLens 2 delivers the mobile operations management capabilities necessary to ensure that devices are in compliance with corporate policy.

| Component | Description |
|-----------|------------|
| [Update HoloLens 2](hololens-updates.md) | Configure updates as needed through Windows Updates for Business |
| [Update apps](app-deploy-overview.md) | Configure through your MDM system or the Microsoft Store

