---
title: Planning HoloLens 2 deployment in a commercial environment
description: Learn about the core needs for deploying and managing HoloLens in enterprise environments, including infrastructure, azure active directory, and mobile device management.
ms.prod: hololens
ms.sitesec: library
ms.assetid: 88bf50aa-0bac-4142-afa4-20b37c013001
author: evmill
ms.author: v-beehanson
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.date: 10/20/2021
appliesto:
- HoloLens 2
---
# Planning HoloLens 2 deployment in a commercial environment

## Overview

> [!NOTE]
> This overview is intended to help IT professionals understand considerations for deploying and managing Microsoft HoloLens 2 devices within an organization. For device end users, see [Get your HoloLens 2 ready to use](hololens2-setup.md) to get started.

HoloLens 2 runs on Windows 10 Holographic, which provides organizations with robust, flexible, built-in mobile device and app management technologies. Windows 10 Holographic supports end-to-end device lifecycle management to give companies control over their devices, data, and apps.

HoloLens 2 can easily be incorporated into standard lifecycle practices -- from device enrollment, configuration, and application management to maintenance and retirement -- by using a comprehensive mobile device management solution.

The following steps and video can help guide you through the process of HoloLens 2 adoption within your organization.

| &nbsp; | &nbsp; |
|--|--|
| ![Step 1.](images/1green.png)| <br/> **[Common Deployment Scenarios](hololens-requirements.md)**: Understand deployment scenarios and explore the core components needed to deploy HoloLens 2 devices. |
| ![Step 2.](images/2green.png)| <br/> **[Prepare](#prepare)**: Become familiar with the infrastructure essentials needed for HoloLens 2. |
| ![Step 3.](images/3green.png) | <br/> **[Configure](#configure)**: Learn how to configure your essential components for a cloud-based deployment. |
| ![Step 4.](images/4green.png) | <br/> **[Deploy](#deploy)**: Discover how to deploy your devices and distribute your applications securely and efficiently. |
| ![Step 5.](images/5green.png) | <br/> **[Maintain](#maintain)**: Find out what's needed to properly maintain the state of your HoloLens 2 devices and ensure compliance with corporate policy. |

<br/>

> [!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

## Prerequisites

Provide new users with basic information.

*   [Where to buy HoloLens 2](hololens2-purchase.md)
*   [HoloLens 2 support](hololens2-support.md)
*   [Common Deployment Scenarios](hololens-requirements.md)

## Prepare

Learn about essential infrastructure services required to support the full set of HoloLens 2 capabilities.

| Component | Description |
|-----------|------------|
| [Azure AD](hololens-identity.md) | Provides identity and access management for the HoloLens 2  |
| [Mobile Device Management](hololens-mdm-configure.md)| Manages HoloLens 2 devices connected to your tenant  |
| [Wi-Fi Network](hololens-commercial-infrastructure.md)| Wi-Fi is available and devices can be connected to the Internet  |

## Configure

Use Intune and Autopilot as low-touch solutions for enrolling and configuring HoloLens 2 to your organization’s Azure AD tenant and MDM.

| Component | Description |
|-----------|------------|
| [Auto Enrollment](hololens-enroll-mdm.md#auto-enrollment-in-mdm) | After initial login, devices automatically register with Azure AD and enroll into MDM  |
| [Application Licenses](hololens2-cloud-connected-configure.md#application-licenses)| Can be applied to either users, user groups, or device groups  |
| [Azure Users and Groups](hololens2-cloud-connected-configure.md#azure-users-and-groups) | Helps assign configurations and licenses for the HoloLens 2  |

## Deploy

Distribute your HoloLens 2 devices and validate their configuration. 

| Component | Description |
|-----------|------------|
| Deployment Considerations - add link | Determine deployment requirements |
| [Enroll HoloLens](hololens-enroll-mdm.md) | Enroll HoloLens in Modern Mobile Device Management |
| [Enrollment Validation](hololens2-corp-connected-deploy.md#enrollment-validation) | Validate the device has Azure AD Joined from Settings or the Azure Portal |
| [Certificate Validation](hololens2-corp-connected-deploy.md#wi-fi-certificate-validation) | Check settings and validate they have been distributed correctly |
| [Validate app installs](hololens2-corp-connected-deploy.md#validate-lob-app-install) | Confirm the app is present and working on your HoloLens 2 |
| [Manage users](hololens-identity.md) | Set up and manage users |
| [Create users and groups](hololens2-corp-connected-configure.md#azure-users-and-groups)
| [Manage HoloLens devices with Microsoft Endpoint Manager](hololens-endpoint-configure.md)

## Maintain

Use Windows Update for Business along with your MDM system or the Microsoft Store to keep your fleet of HoloLens 2 and apps updated.

| Component | Description |
|-----------|------------|
| [Update HoloLens 2](hololens-updates.md) | Configure updates as needed through Windows Updates for Business |
| [Update apps](app-deploy-overview.md) | Configure through your MDM system or the Microsoft Store
