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

HoloLens 2 runs on Windows 10 Holographic, which uses a comprehensive mobile device management solution that gives companies control over device enrollment, configuration, and application management through maintenance and retirement. 

This overview will help IT professionals plan for deploying and managing HoloLens 2 devices in a commercial environment. To get started, view this quick summary of the process.

<br/>

> [!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

The following steps contain links that will help you learn the process of deploying HoloLens 2.


![Step 1.](images/1green.png)

## Prepare 

If you already know the basics of HoloLens, you can skip this step. Otherwise, start by finding out [where to buy HoloLens 2](hololens2-purchase.md), how to get [support](hololens2-support.md), and how to [give Feedback](hololens-feedback.md).

Before you put on your HoloLens2 and start using it, learn about how it [redefines your environment](hololens-environment-considerations.md) so you can optimize your experience. Then dive into learning how to set it up and [use it for the first time](hololens2-setup.md). 

After you've mastered the basics, you can get down to learning the language of HoloLens by reviewing the [Daily Usage](holographic-home.md) topics. 

Once you have learned the HoloLens voice and gesture commands, you're ready to move on to planning your deployment.  

![Step 1.](images/2green.png)

## Plan

Plan your deployment by learning about deployment scenarios, requirements, and essential services. Your first task will be to determine which of the [Common Deployment Scenarios](hololens-requirements.md) fit your organization's requirements.

After making your determination, learn about [configuring your commercial infrastructure for HoloLens](hololens-commercial-infrastructure.md). HoloLens deployments need wireless network availability and access to Microsoft services. Your deployment depends on your [use case](/hololens/hololens-deployment-considerations).

For example, if you're planning a Remote Assist deployment, you'll have to learn about the [technical requirements](/dynamics365/mixed-reality/remote-assist/requirements.md), including the [network requirements](/dynamics365/mixed-reality/remote-assist/requirements#network-requirements) and [URL end points and TCP/UDP ports](/dynamics365/mixed-reality/remote-assist/requirements.md#urls-and-+ports) that Dynamics 365 Remote Assist must be able to reach. You should also authenticate your installation by [preparing the required certificates and network profiles](/hololens/hololens-certificates-network).

[Azure users and groups](hololens2-corp-connected-configure.md#azure-users-and-groups)  provide the basic framework for HoloLens user groups, identities, and logins. Within that framework, you'll learn to [manage user identity and login](hololens-identity.md) and [limit password use](security-limiting-password-use.md) to secure your installation. 

Finally, you'll learn about Modern Mobile Device Management, which includes learning to manage your HoloLens devices and apps with [Microsoft Intune](/mem/intune/fundamentals/what-is-intune).

![Step 1.](images/3green.png)

## Configure

You'll use Microsoft Intune and Windows Autopilot to configure your HoloLens devices. 

If your organization already uses Azure AD, you can [register](hololens2-autopilot-registration-support.md) and [enroll HoloLens devices into Mobile Device Management automatically](hololens-enroll-mdm.md#auto-enrollment-in-mdm). If you have a large installation planned, you can use [Windows Autopilot](hololens2-autopilot.md) to deploy at scale with ease.

Once you have your HoloLens devices registered and enrolled, you can use [Microsoft Endpoint Manager](hololens-mdm-configure.md) to manage them. For example, you can use [Azure Users and Groups](hololens2-cloud-connected-configure.md#azure-users-and-groups) to apply [application Licenses](hololens2-cloud-connected-configure.md#application-licenses) to users, user groups, or device groups quickly and efficiently.

![Step 1.](images/4green.png)

## Deploy

Next you'll deploy your HoloLens devices, validate their configuration, and distribute your applications securely and efficiently.

Determine deployment requirements 
*   Deployment Considerations - add link

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

![Step 1.](images/5green.png)

## Maintain

Find out what's needed to properly maintain the state of your HoloLens 2 devices and ensure compliance with corporate policy.

Use Windows Update for Business along with your MDM system or the Microsoft Store to keep your fleet of HoloLens 2 and apps updated.

Configure updates as needed through Windows Updates for Business
*   [Update HoloLens 2](hololens-updates.md)
Configure through your MDM system or the Microsoft Store
*   [Update apps](app-deploy-overview.md)
