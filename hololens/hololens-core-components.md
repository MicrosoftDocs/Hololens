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

HoloLens 2 runs on Windows 10 Holographic, which includes a comprehensive mobile device management solution that gives companies control over device enrollment, configuration, and application management to maintenance and retirement. 

This overview will help IT professionals plan for deploying and managing HoloLens 2 devices in a commercial environment. To get started, view this quick summary of the process.

<br/>

> [!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

The following steps contain links that will help you learn the process of deploying HoloLens 2.

## Prepare

If you already know the basics of HoloLens and its use, you can skip this step. Otherwise, start by finding out [where to buy HoloLens 2](hololens2-purchase.md), how to get [support](hololens2-support.md), and how to [give Feedback](hololens-feedback.md).

Before you put on your HoloLens2 and start using it, learn about how it [redefines your environment](hololens-environment-considerations.md) so you can optimize your experience. Then dive into learning how to set it up and use it for the [first time](hololens2-setup.md). 

After you've mastered the basics, you can get down to learning the language of HoloLens by reviewing the [Daily Usage](holographic-home.md) files. Once you have internalized the HoloLens voice and gesture commands, you're ready to move on to planning your deployment.  

## Plan

Plan your deployment by learning about the scenarios, requirements, and essential services. Your first task will be do determine which of the [Common Deployment Scenarios](hololens-requirements.md) will fit your organization's requirements.

Then start planning your infrastructure by figuring out how to [configure your network for HolLens](hololens-commercial-infrastructure.md). 
If you're building a Remote Assist deployment, you'll want to learn about the [technical requirements](/dynamics365/mixed-reality/remote-assist/requirements.md#d/dynamics365/mixed-reality/remote-assist/requirements.md) for deploying and using Dynamics 365 Remote Assist. For example, you might have to learn about the [URLs and ports](/dynamics365/mixed-reality/remote-assist/requirements.md#urls-and-+ports) Remote Assist installations require.

Next you should learn about the Microsoft procedures and services that underlie HoloLens deployments. [Azure users and groups](hololens2-corp-connected-configure.md#azure-users-and-groups) are provide the basic framework for HoloLens user groups, identities, and logins. Within that framework, you'll learn to [manage user identity and login](hololens-identity.md) and [limiting password use](security-limiting-password-use.md) to secure your installation. 

Finally, you'll learn about Modern Mobile Device Management, which includes learning to manage your HoloLens devices and apps with [Microsoft Intune](tps://docs.microsoft.com/en-us/mem/intune/fundamentals/what-is-intune).

## Configure

Learn how to configure your essential components. 

Use Microsoft Intune and Windows Autopilot to automatically register devices into your organization's Azure AD. After initial login, devices automatically register with Azure AD and enroll into Mobile Device Management.
*   Use [Automatically enroll HoloLens 2 into MDM](hololens-enroll-mdm.md#auto-enrollment-in-mdm)
*   Use [Windows Autopilot](hololens2-autopilot.md) to deploy at scale with ease.
*   Use [Windows Autopilot](hololens2-autopilot-registration-support.md) to register your devices.
*   Use [Microsoft Endpoint Manager](hololens-mdm-configure.md) to manage your HoloLens devices.
*   [Application Licenses](hololens2-cloud-connected-configure.md#application-licenses) can be applied to either users, user groups, or device groups  
*   [Azure Users and Groups](hololens2-cloud-connected-configure.md#azure-users-and-groups) help assign configurations and licenses for the HoloLens 2 

## Deploy

Discover how to deploy your devices and distribute your applications securely and efficiently.

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

Find out what's needed to properly maintain the state of your HoloLens 2 devices and ensure compliance with corporate policy.

Use Windows Update for Business along with your MDM system or the Microsoft Store to keep your fleet of HoloLens 2 and apps updated.

Configure updates as needed through Windows Updates for Business
*   [Update HoloLens 2](hololens-updates.md)
Configure through your MDM system or the Microsoft Store
*   [Update apps](app-deploy-overview.md)
