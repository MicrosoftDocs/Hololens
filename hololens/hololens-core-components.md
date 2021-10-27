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

HoloLens 2 runs on Windows 10 Holographic, which provides organizations with robust, flexible, built-in mobile device and app management technologies. Windows 10 Holographic supports end-to-end device lifecycle management to give companies control over their devices, data, and apps.

> [!NOTE]
> This overview is intended to help IT professionals understand considerations for deploying and managing Microsoft HoloLens 2 devices within an organization. For device end users, see [Get your HoloLens 2 ready to use](hololens2-setup.md) to get started.

HoloLens 2 can easily be incorporated into standard lifecycle practices -- from device enrollment, configuration, and application management to maintenance and retirement -- by using a comprehensive mobile device management solution. Here is a summary of the process.

> [!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

The following steps and video can help guide you through the process of deploying HoloLens 2.

| &nbsp; | &nbsp; |
|--|--|
| ![Step 1.](images/1green.png)| <br/> **[Prepare](#prepare)**: Get familiar with the basic information needed to get and learn to use HoloLens 2. |
| ![Step 2.](images/2green.png)| <br/> **[Plan](#configure)**: Plan your deployment by learning about the scenarios, requirements, and essential services. |
| ![Step 3.](images/3green.png) | <br/> **[Configure](#configure)**: Learn how to configure your essential components. |
| ![Step 4.](images/4green.png) | <br/> **[Deploy](#deploy)**: Discover how to deploy your devices and distribute your applications securely and efficiently. |
| ![Step 5.](images/5green.png) | <br/> **[Maintain](#maintain)**: Find out what's needed to properly maintain the state of your HoloLens 2 devices and ensure compliance with corporate policy. |

## Prepare

Get basic information about HoloLens:

*   [Where to buy HoloLens 2](hololens2-purchase.md)
*   [HoloLens 2 support](hololens2-support.md)
    *   [Give Feedback](hololens/hololens-feedback)

Start learning to use the device.

*   [HoloLens environment considerations](hololens/hololens-environment-considerations)
*   [First Time Usage](hololens/hololens2-setup)
*   [Daily Usage](hololens/holographic-home)

## Plan

Determine which deployment scenario aligns best to your organization by reviewing the [Common Deployment Scenarios](hololens-requirements.md). Plan your infrastructure by reviewing the requirements for deploying HoloLens devices and applications.
*   [Review infrastructure requirements](hololens/hololens-commercial-infrastructure)
*   [Review network requirements for Remote Assist](dynamics365/mixed-reality/remote-assist/requirements#dynamics-365-remote-assist-hololens)]
*   [Open ports for services](/dynamics365/mixed-reality/remote-assist/requirements#urls-and-+ports)

*	HoloLens 2 requires Modern Mobile Device Management.
    *   [What is Microsoft Intune?](/mem/intune/fundamentals/what-is-intune)  
        *   [Understand device categories, groups, profiles, and configurations](hololens/hololens-mdm-configure)

Plan your HoloLens 2 users by learning about user groups, identities, and logins.
*   [Azure users and groups](hololens/hololens2-corp-connected-configure#azure-users-and-groups)
*   [Manage user identity and login](hololens/hololens-identity)
*   [Limiting password use](hololens/security-limiting-password-use)

## Configure

Use Microsoft Intune and Windows Autopilot to automatically register devices into your organization's Azure AD. After initial login, devices automatically register with Azure AD and enroll into Mobile Device Management.
*   Use [Automatically enroll HoloLens 2 into MDM](hololens-enroll-mdm.md#auto-enrollment-in-mdm)
*   Use [Windows Autopilot](hololens2-autopilot) to deploy at scale with ease.
*   Use [Windows Autopilot](hololens2-autopilot-registration-support) to register your devices.
*   Use [Microsoft Endpoint Manager](hololens-mdm-configure) to manage your HoloLens devices.
*   [Application Licenses](hololens2-cloud-connected-configure.md#application-licenses) can be applied to either users, user groups, or device groups  
*   [Azure Users and Groups](hololens2-cloud-connected-configure.md#azure-users-and-groups) help assign configurations and licenses for the HoloLens 2 

## Deploy

Distribute your HoloLens 2 devices and validate their configuration. 

Determine deployment requirements 
*   Deployment Considerations - add link
Enroll HoloLens in Modern Mobile Device Management
*   [Enroll HoloLens](hololens-enroll-mdm.md) 
Validate the device has Azure AD - Joined from Settings or the Azure Portal
*   [Enrollment Validation](hololens2-corp-connected-deploy.md#enrollment-validation) 
Check settings and validate they have been distributed correctly
*   [Certificate Validation](hololens2-corp-connected-deploy.md#wi-fi-certificate-validation) 
Confirm the app is present and working on your HoloLens 2
*   [Validate app installs](hololens2-corp-connected-deploy.md#validate-lob-app-install)
Set up and manage users
*   [Manage users](hololens-identity.md)
*   [Create users and groups](hololens2-corp-connected-configure.md#azure-users-and-groups)
*   [Manage HoloLens devices with Microsoft Endpoint Manager](hololens-mdm-configure.md)

## Maintain

Use Windows Update for Business along with your MDM system or the Microsoft Store to keep your fleet of HoloLens 2 and apps updated.

Configure updates as needed through Windows Updates for Business
*   [Update HoloLens 2](hololens-updates.md)
Configure through your MDM system or the Microsoft Store
*   [Update apps](app-deploy-overview.md)
