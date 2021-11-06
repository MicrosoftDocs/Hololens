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
ms.date: 11/01/2021
appliesto:
- HoloLens 2
---
# Planning HoloLens 2 deployment in a commercial environment

## Overview

> This overview is intended to help IT professionals understand considerations for deploying and managing Microsoft HoloLens 2 devices within an organization. For device end users, see [Get your HoloLens 2 ready to use](hololens2-setup.md) to get started.

HoloLens 2 runs on Windows 10 Holographic, which provides organizations with robust, flexible, built-in mobile device and app management technologies. Windows 10 Holographic supports end-to-end device lifecycle management to give companies control over their devices, data, and apps. The HoloLens 2 can easily be incorporated into standard lifecycle practices, from device enrollment, configuration, and application management to maintenance and retirement using a comprehensive mobile device management solution.

The following steps and video can help guide you through the process of HoloLens 2 adoption within your organization.

<br/>

> [!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

The following steps contain links that will help you learn the process of deploying HoloLens 2.

![Step 1.](images/1green.png)

## Prepare for deployment

If you already know the basics of HoloLens, you can skip this step. Otherwise, start by finding out [where to buy HoloLens 2](hololens2-purchase.md), how to get [support](hololens2-support.md), and how to [give Feedback](hololens-feedback.md). You might also want to get familiar with [licensing requirements](hololens-licenses-requirements.md) at this time.

Before you put on your HoloLens2 and start using it, learn about how it [redefines your environment](hololens-environment-considerations.md) so you can optimize your experience. Then dive into learning how to set it up and [use it for the first time](hololens2-setup.md). 

After you've mastered the basics, you can get down to learning the language of HoloLens by reviewing the [Daily Usage](holographic-home.md) topics. Once you have learned the HoloLens voice and gesture commands, you're ready to move on to planning your deployment.  

![Step 2.](images/2green.png)

## Plan your deployment

Plan your deployment by learning about deployment scenarios, requirements, and essential services. Your deployment method will depend on your use case.

|Use case | Notes |
| --- | --- |
|Remote Assistance  |Enable your employees to remote in an expert anytime they need it. |
|Guides & Task Management  |Walk employees step-by-step through guided experiences to help them complete tasks faster and more accurately than ever before. |
| Restricted offline installation | Lock down HoloLens 2 for use in secure environments |
|Training & Simulation |Train and onboard new employees faster than ever using a "learning by doing" approach. |
|Design & Prototyping  |Convert your CAD and BIM files to 3D digital twins to quickly iterate and collaborate on new product designs. |
|Sales Assistance  |Carry less inventory and close large ticket sales faster by using mixed reality to showcase any configuration or customization to your customer. |
|Contextual Data Overlays  |Make pertinent and real-time data available when and where it is needed, enabling your employees to make better, faster, more informed decisions. |

Your first task will be to determine which of the [Common Deployment Scenarios](hololens-requirements.md) fit your organization's requirements. If you're planning a [Remote Assist](hololens2-cloud-connected-overview.md), [Dynamics 365](hololens2-corp-connected-overview.md), or [restricted offline](hololens-common-scenarios-offline-secure.md) installation, you can use the existing Deployment Guides. 

If your use case requires an alternate approach, you will have to use Microsoft tools and processes to [configure your commercial infrastructure for HoloLens](hololens-commercial-infrastructure.md). HoloLens is a Windows device, so you'll want to become familiar with mobile device management, Azure Active Directory, and Windows Device Configuration Manager. You'll learn about using [Modern Mobile Device Management](hololens-enroll-mdm.md) to manage your HoloLens devices and apps using [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) and [Endpoint Manager](hololens-mdm-configure.md) .

HoloLens deployments need wireless network availability and access to Microsoft services, so you'll have to learn [how to connect HoloLens to a network](hololens-network.md). Throughout the process, you'll be using Microsoft tools like Intune, Autopilot, and Endpoint Manager to get your network set up. 

![Step 3.](images/3green.png)

## Configure your network, users, and devices

### Network

After you've confirmed your use case, you'll need to plan your network infrastructure and [review the network requirements ](hololens-network.md) for the HoloLens devices and applications. Inspect your physical location to determine if your corporate WiFi network and its security components will work for a HoloLens deployment, and consider [preparing certificates and network profiles to meet company requirements](hololens-certificates-network.md). 

### Identity

[Microsoft Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) provides the basic framework for user groups, identities, and logins. Within that framework, you'll learn to create your users' identities, authenticate them, and manage their access so they can login easily and connect to their work resources.

### Devices

Once your organization is set up with Azure AD, you can [register your HoloLens devices with Windows Autopilot](hololens2-autopilot-registration-support.md) and set them up to [enroll automatically into Mobile Device Management](hololens-enroll-mdm.md#auto-enrollment-in-mdm). You can also use Autopilot to [validate their enrollment](hololens2-corp-connected-deploy.md#enrollment-validation) and [certificates](hololens2-corp-connected-deploy.md#wi-fi-certificate-validation). 

If you have a large installation planned, [Windows Autopilot](hololens2-autopilot.md) will do all of that for you. Once you have your HoloLens devices registered and enrolled, you can use [Microsoft Endpoint Manager](hololens-mdm-configure.md) to manage them.

> [!NOTE]
> Mobile device management (MDM), including the VPN, Bitlocker, and kiosk mode features, is only available when you upgrade to Windows Holographic for Business.

![Step 4.](images/4green.png)

## Start Deploying

After you've learned to [manage HoloLens user identities and logins](hololens-identity.md) and [limit their password use](security-limiting-password-use.md) to secure your installation, you'll use [Azure Users and Groups](hololens2-cloud-connected-configure.md#azure-users-and-groups) to apply [application licenses](hololens2-cloud-connected-configure.md#application-licenses) to your user or device groups.

You'll also be using Azure Active Directory to [create the tenant that represents your organization](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant), and you'll build your services on top of that tenant.

Before proceeding, you'll need to make sure your device enrollment and certificates are validated. Devices must have [Azure joined from Settings or the Azure portal](hololens2-cloud-connected-configure.md), and certificate settings must be checked to make sure they have been correctly distributed. 

You should also consider [how apps will be deployed](app-deploy-overview.md) on HoloLens through your MDM system or the Microsoft Store, and validate that [apps are operating effectively on the device](hololens2-corp-connected-deploy). 

![Step 5.](images/5green.png)

## Maintain your installation

### Updates

Use [Windows Update for Business](hololens-updates.md) to keep your group of HoloLens 2 devices and apps updated. Keep devices plugged in and set active hours so updates will occur outside of working hours.

Review [HoloLens 2 release notes](hololens-release-notes.md) and [insider preview updates](hololens-insider.md), and consider creating update rings for different user groups.

### Support Plan

Get support from [Microsoft](hololens2-support.md), the [HoloLens Community](hololens2-support.md#community-help-options), or [Stack Overflow](hololens2-support#post-a-question-on-stack-overflow). 

You might also consider asking for deployment assistance from a Microsoft Consulting Services/Partner.

### Device Management

Find out what's needed to properly maintain the state of your HoloLens 2 devices and ensure compliance with corporate policy. Start with the [HoloLens 2 Cleaning FAQ](hololens2-maintenance).

If the headset seems to need service or repair, start with a [restart, reset, or recover](hololens-recovery.md) process. Do some [troubleshooting](hololens-troubleshooting) if you have any questions or concerns about the state of the device or its maintenance.