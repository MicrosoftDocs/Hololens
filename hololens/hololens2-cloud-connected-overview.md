---
title: Overview of Cloud connected HoloLens 2 with Remote Assist 
description: Learn how to enroll HoloLens 2 devices over a Cloud Connected network using Dynamics 365 Remote Assist.
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

# Deployment Guide – Cloud connected HoloLens 2 with Remote Assist – Overview

This guide will help IT professionals plan for and deploy Microsoft HoloLens 2 devices with Remote Assist to their organization. This will serve as a model for proof-of-concept deployments to your organization across a variety of HoloLens 2 use cases. The setup is similar to [Scenario A: Deploy to cloud connect devices](https://docs.microsoft.com/hololens/common-scenarios#scenario-a). 

During the guide, we will cover how to enroll your devices into your device management, apply licenses as needed, and validate that your end users are able to immediately use Remote Assist upon device setup. To do this, we will go over the important pieces of infrastructure needed to get set up and running – achieving deployment at scale with HoloLens 2. No other device restrictions or configurations will be applied in this guide, however, we encourage you to explore those options after finishing.

## Prerequisites

The following infrastructure should already be in place. (If not, setting up Azure and Intune is included in this guide):

- Wi-Fi
    - Networks are typically open to the Internet and Cloud services
- Azure Active Directory (Azure AD) Join with MDM Auto Enrollment ([Azure AD P1 subscription](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) needed)
- MDM (Intune) Managed
    - One or more applications are deployed via MDM.
- Users sign in with their own corporate account (Azure AD)
    - Single or multiple users per device is supported.

[ ![Cloud connected scenario](./images/deployment-guides-revised-scenario-a.png) ](./images/deployment-guides-revised-scenario-a.png#lightbox)

## Learn about Remote Assist

Remote Assist allows for collaborative maintenance and repair, remote inspection, as well as knowledge sharing and training. By connecting people in different roles and locations a technician using Remote Assist can connect with a remote collaborator on Microsoft Teams. They can combine video, screenshots, and annotations to solve problems in real time even when they aren&#39;t in the same location. Remote collaborators can insert reference images, schematics, and other helpful information the technician&#39;s physical space so they can refer to the schematic while working heads-up and hands-free on HoloLens.

<iframe width="560" height="315" src="https://www.youtube.com/embed/d3YT8j0yYl0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Remote Assist Licensing and Requirements

- Azure AD account (required for purchasing the subscription and assigning licenses)
- [Remote Assist subscription](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/buy-and-deploy-remote-assist[) (or [Remote Assist Trial](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/try-remote-assist))
    
#### Dynamics 365 Remote Assist user

- Remote Assist license
- Network Connectivity

#### Microsoft Teams user

- Microsoft Teams or [Teams Freemium](https://products.office.com/microsoft-teams/free).
- Network connectivity

If you plan on implementing this [cross-tenant scenario](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/cross-tenant-overview#scenario-2-leasing-services-to-other-tenants), you may need an Information Barriers license. See [this article](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/cross-tenant-licensing-implementation#step-1-determine-if-information-barriers-are-necessary) to determine if an Information Barrier License is required.

## In this guide you will:

Prepare:

> [!div class="checklist"]
> - [Learn about the infrastructure essentials for HoloLens 2 devices.](hololens2-cloud-connected-prepare.md#infrastructure-essentials)
> - [Learn more about Azure AD and set up one if you don&#39;t have it.](hololens2-cloud-connected-prepare.md#azure-active-directory)
> - [Learn about Identity management and how to best set up Azure AD accounts.](hololens2-cloud-connected-prepare.md#identity-management)
> - [Learn more about MDM, and set up with Intune if you don&#39;t already have one ready.](hololens2-cloud-connected-prepare.md#mobile-device-management)
> - [Learn about the networking requirements of Remote Assist.](hololens2-cloud-connected-prepare.md#network)
> - [Optionally: VPN to connect to organizational resources](/hololens2-cloud-connected-prepare.md#optional-connect-your-hololens-to-vpn)

Configure:

> [!div class="checklist"]
> - [How to create Users and Groups.](hololens2-cloud-connected-configure.md#azure-users-and-groups)
> - [How to set up Auto-enrollment within Azure AD.](hololens2-cloud-connected-configure.md#auto-enrollment-on-hololens-2)
> - [How to assign your Application licenses.](hololens2-cloud-connected-configure.md#application-licenses)

Deploy:

> [!div class="checklist"]
> - [Set up your HoloLens 2 and validate enrollment.](hololens2-cloud-connected-deploy.md#enrollment-validation)
> - [Validate you can make a Remote Assist call.](hololens2-cloud-connected-deploy.md#remote-assist-call-validation)

Maintain:

> [!div class="checklist"]
> - [How to update Remote Assist using the Microsoft Store app.](hololens2-cloud-connected-maintain.md#updates)
> - [Making a support plan.](hololens2-cloud-connected-maintain.md#support-plan)
> - [Development plan.](hololens2-cloud-connected-maintain.md#development-plan)

## Next step

> [!div class="nextstepaction"]
> [Cloud connected deployment - Prepare](hololens2-cloud-connected-prepare.md)

