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

> [!NOTE]
> This overview is intended to help IT professionals understand considerations for deploying and managing Microsoft HoloLens 2 devices within an organization. If you are just getting started with HoloLens, [get your device ready to use](hololens2-setup.md).

HoloLens 2 is a Windows device. It runs on Windows 10 Holographic, which provides organizations with robust, flexible, built-in mobile device and app management technologies. 

Windows 10 Holographic supports end-to-end device lifecycle management, giving you control over your devices, data, and apps. HoloLens 2 uses a comprehensive mobile device management solution that enables it to be incorporated into standard lifecycle practices, -- from device enrollment, configuration, and application management up through maintenance and retirement. 

The following steps and video will help guide you through the process of deploying HoloLens 2 within your organization.

<br/>

> [!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

| &nbsp; | &nbsp; |
|--|--|
| ![Step 1.](images/1green.png) | <br/> **[Prepare](#prepare)**: &nbsp; Get familiar with the basics and learn to use HoloLens 2.    |
| ![Step 2.](images/2green.png) | <br/> **[Plan](#configure)**: &nbsp; Plan your deployment by learning about Microsoft tools and services. |
| ![Step 3.](images/3green.png) | <br/> **[Configure](#configure)**: &nbsp; Learn to configure the  essential components of your installation. |
| ![Step 4.](images/4green.png) | <br/> **[Deploy](#deploy)**: &nbsp; Get your devices and applications deployed securely. |
| ![Step 5.](images/5green.png) | <br/> **[Maintain](#maintain)**: &nbsp; Learn to  update, support, and maintain your deployment.

## Prepare

If you already know the basics of HoloLens, you can skip this step.  If not, find out:

*   [what HoloLens can do for you](hololens-commercial-features)
*   [where to buy HoloLens 2](hololens2-purchase.md)
*   [how to get support](hololens2-support.md)
*   [how to give Feedback](hololens-feedback.md)
*   [about licensing requirements](hololens-licenses-requirements.md)

Then start learning to use HoloLens 2 by:

*   [understanding how it works in your environment](hololens-environment-considerations.md)
*   [setting up HoloLens2 for the first time](hololens2-setup.md)
*   [learning to navigate, manage, and manipulate holograms](holographic-home.md)

## Plan

The deployment method for your commercial installation will depend on your use case.

|Use case | What it will do |
| --- | --- |
|Remote Assistance  |Enable your employees to remote in an expert anytime they need it. |
|Guides & Task Management  |Walk employees step-by-step through guided experiences to help them complete tasks faster and more accurately than ever before. |
| Restricted offline installation | Lock down HoloLens 2 for use in secure environments |
|Training & Simulation |Train and onboard new employees faster than ever using a "learning by doing" approach. |
|Design & Prototyping  |Convert your CAD and BIM files to 3D digital twins to quickly iterate and collaborate on new product designs. |
|Sales Assistance  |Carry less inventory and close large ticket sales faster by using mixed reality to showcase any configuration or customization to your customer. |
|Contextual Data Overlays  |Make pertinent and real-time data available when and where it is needed, enabling your employees to make better, faster, more informed decisions. |

*   Learn about the [Common Deployment Scenarios](hololens-requirements.md):
    *   Start a [Remote Assist](hololens2-cloud-connected-overview.md) installation
    *   Start a [Dynamics 365](hololens2-corp-connected-overview.md) installation
    *   Start a [restricted offline](hololens-common-scenarios-offline-secure.md) installation

*   If you have another use case and are planning a [customized commercial scenario](hololens-commercial-infrastructure.md), start by learning about Microsoft tools and services:

    *   [What is the Microsoft Store for Business?](app-deploy-store-business.md)
    *   [What is Azure Active Directory?](/azure/active-directory/fundamentals/active-directory-whatis.md)
    *   [What is Windows Autopilot?](/mem/autopilot/windows-autopilot.md)
    *   [What is Microsoft Intune?](/mem/intune/fundamentals/what-is-intune)
    *   [What is Microsoft Endpoint Manager?](/mem/endpoint-manager-overview.md)
    
*   If you're already familiar with Microsoft tools and services, read about how they are used with HoloLens 2:

    *   
 HoloLens is a Windows device, so you'll want to become familiar with mobile device management, Azure Active Directory, and Windows Device Configuration Manager. You'll learn about using [Modern Mobile Device Management](hololens-enroll-mdm.md) to manage your HoloLens devices and apps using  and 
HoloLens deployments need wireless network availability and access to Microsoft services, so you'll have to learn [how to connect HoloLens to a network](hololens-network.md). 
        *   Learn about deploying with [Microsoft Intune](app-deploy-intune.md)
 


## Configure

       *   [Windows Autopilot](hololens2-autopilot.md)
           *   [Microsoft [Modern Mobile Device Management](hololens-enroll-mdm.md)
           endpoint manager     (hololens-mdm-configure.md) .
        *   Learn about deploying with [Microsoft Intune](app-deploy-intune.md)

### Network

After you've confirmed your use case, you'll need to plan your network infrastructure and [review the network requirements ](hololens-network.md) for the HoloLens devices and applications. Inspect your physical location to determine if your corporate WiFi network and its security components will work for a HoloLens deployment, and consider [preparing certificates and network profiles to meet company requirements](hololens-certificates-network.md). 

### Identity

[Microsoft Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) provides the basic framework for user groups, identities, and logins. Within that framework, you'll learn to create your users' identities, authenticate them, and manage their access so they can login easily and connect to their work resources.

### Devices

Once your organization is set up with Azure AD, you can [register your HoloLens devices with Windows Autopilot](hololens2-autopilot-registration-support.md) and set them up to [enroll automatically into Mobile Device Management](hololens-enroll-mdm.md#auto-enrollment-in-mdm). You can also use Autopilot to [validate their enrollment](hololens2-corp-connected-deploy.md#enrollment-validation) and [certificates](hololens2-corp-connected-deploy.md#wi-fi-certificate-validation). 

If you have a large installation planned, [Windows Autopilot](hololens2-autopilot.md) will do all of that for you. Once you have your HoloLens devices registered and enrolled, you can use [Microsoft Endpoint Manager](hololens-mdm-configure.md) to manage them.

> [!NOTE]
> Mobile device management (MDM), including the VPN, Bitlocker, and kiosk mode features, is only available when you upgrade to Windows Holographic for Business.

## Deploy

After you've learned to [manage HoloLens user identities and logins](hololens-identity.md) and [limit their password use](security-limiting-password-use.md) to secure your installation, you'll use [Azure Users and Groups](hololens2-cloud-connected-configure.md#azure-users-and-groups) to apply [application licenses](hololens2-cloud-connected-configure.md#application-licenses) to your user or device groups.

You'll also be using Azure Active Directory to [create the tenant that represents your organization](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant), and you'll build your services on top of that tenant.

Before proceeding, you'll need to make sure your device enrollment and certificates are validated. Devices must have [Azure joined from Settings or the Azure portal](hololens2-cloud-connected-configure.md), and certificate settings must be checked to make sure they have been correctly distributed. 

You should also consider [how apps will be deployed](app-deploy-overview.md) on HoloLens through your MDM system or the Microsoft Store, and validate that [apps are operating effectively on the device](hololens2-corp-connected-deploy). 

## Maintain

### Updates

Use [Windows Update for Business](hololens-updates.md) to keep your group of HoloLens 2 devices and apps updated. Keep devices plugged in and set active hours so updates will occur outside of working hours.

Review [HoloLens 2 release notes](hololens-release-notes.md) and [insider preview updates](hololens-insider.md), and consider creating update rings for different user groups.

### Support Plan

Get support from [Microsoft](hololens2-support.md), the [HoloLens Community](hololens2-support.md#community-help-options), or [Stack Overflow](hololens2-support#post-a-question-on-stack-overflow). 

You might also consider asking for deployment assistance from a Microsoft Consulting Services/Partner.

### Device Management

Find out what's needed to properly maintain the state of your HoloLens 2 devices and ensure compliance with corporate policy. Start with the [HoloLens 2 Cleaning FAQ](hololens2-maintenance).

If the headset seems to need service or repair, start with a [restart, reset, or recover](hololens-recovery.md) process. Do some [troubleshooting](hololens-troubleshooting) if you have any questions or concerns about the state of the device or its maintenance.