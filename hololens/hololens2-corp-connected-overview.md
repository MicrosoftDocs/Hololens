---
title: Deployment Guide – Corporate connected HoloLens 2 with Dynamics 365 Guides - Overview
description: Learn how to enroll HoloLens 2 devices with Dynamics 365 Guides over a corporate Connected network.
keywords: HoloLens, management, corporate connected, Dynamics 365 Guides, AAD, Azure AD, MDM, Mobile Device Management
author: joyjaz
ms.author: v-jjaswinski
ms.reviewer: aboeger
ms.date: 03/24/2021
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: HoloLens
manager: yannisle
appliesto:
- HoloLens 2
---

# Deployment Guide - Corporate Connected HoloLens 2 with Dynamics 365 Guides - Overview

This guide will help IT professionals plan for and deploy Microsoft HoloLens 2 devices with Dynamics 365 Guides (Guides) to their organization. This guide is great for pilots as well as production deployments and is similar to the [Scenario B: Deploy inside your organization's network](https://docs.microsoft.com/hololens/common-scenarios#scenario-b-deploy-inside-your-organizations-network) guide. After testing your proof-of-concept, use this guide to move forward with integrating HoloLens into your organization.

In this guide, we will cover how to enroll your devices into your existing device management, apply licenses as needed, and validate that your end users are able to operate a Dynamics 365 Guide, as well as use custom line of business apps, after device set up. 

## Prerequisites

The following infrastructure should already be in place:
- Wi-Fi
    - Internal corporate network with access to internal resources and limited access to the internet or Cloud services
    - Device-based certificate authentication.
- Azure Active Directory (Azure AD) Join with MDM Auto Enrollment ([Azure AD P1 subscription](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) needed)
- MDM (Intune) Managed
    - One or more applications are deployed via MDM.
- Network 
    - Certificates (SCEP or PKCS)
    - Proxy configuration
- Users sign in with their own corporate account (Azure AD)
    - Single or multiple users per device is supported.
- Varying levels of device lockdown configurations applied based on specific use cases, from Fully Open to Single App Kiosk.

## [Guides Licensing and Requirements](https://docs.microsoft.com/dynamics365/mixed-reality/guides/requirements#licensing-and-product-requirements)
- Azure AD account
- Dynamics 365 Guides applications PC and HoloLens
- Dynamics 365 Guides subscription
    - Microsoft Dataverse (included)
    - Power Apps (included)
- Power BI Desktop
- Network Connectivity

[ ![Corp connected network diagram, stage 1](./images/deployment-guides-revised-scenario-b-01-1.png) ](./images/deployment-guides-revised-scenario-b-01-1.png#lightbox)

[ ![Corp connected network diagram, stage 2](./images/deployment-guides-revised-scenario-b-02-1.png) ](./images/deployment-guides-revised-scenario-b-02-1.png#lightbox)

## In this guide you will:
### Prepare
> [!div class="checklist"]
>- [Learn about the infrastructure essentials for HoloLens 2 devices.](hololens2-corp-connected-prepare.md#infrastructure-essentials)
>- [Learn more about Azure AD and set up one if you don't have it.](hololens2-corp-connected-prepare.md#azure-active-directory)
>- [Learn about Identity management and how to best set up Azure AD accounts.](hololens2-corp-connected-prepare.md#identity-management)
>- [Learn more about MDM and set up with Intune if you don't already have one ready.](hololens2-corp-connected-prepare.md#mobile-device-management)
>- [Familiarize yourself with certificate-based Wi-Fi.](hololens2-corp-connected-prepare.md#certificates)
>- [Familiarize yourself with Proxy.](hololens2-corp-connected-prepare.md#proxy)
>- [Understand how you can use Line of Business Apps.](hololens2-corp-connected-prepare.md#line-of-business-apps)
>- [Learn more about the way you can use Guides for your organization.](hololens2-corp-connected-prepare.md#guides-playbook)
### Configure
> [!div class="checklist"]
>- [How to create users and groups.](hololens2-corp-connected-configure.md#azure-users-and-groups)
>- [How to set up Auto Enrollment.](hololens2-corp-connected-configure.md#auto-enrollment-on-hololens-2)
>- [How to set up Wi-Fi certificates and profiles for Corporate Wi-Fi Connectivity.](hololens2-corp-connected-configure.md#corporate-wi-fi-connectivity)
>- [Upload and Assign Line of Business (LOB) App packages.](hololens2-corp-connected-configure.md#app-deployment)
>- [Setup Dynamics 365 Guides.](hololens2-corp-connected-configure.md#setup-guides-application-licenses-dataverse-and-authoring)
>- [How to configure Kiosk Mode (optional).](hololens2-corp-connected-configure.md#optional-kiosk-mode)
>- [How to configure WDAC (optional).](hololens2-corp-connected-configure.md#optional-wdac)
### Deploy
> [!div class="checklist"]
>-	[Validate enrollment via device and MDM.](hololens2-corp-connected-deploy.md#enrollment-validation)
>-	[Validate Wi-Fi certificates.](hololens2-corp-connected-deploy.md#wi-fi-certificate-validation)
>-	[Validate LOB app install.](hololens2-corp-connected-deploy.md#validate-lob-app-install)
>-	[Validate Guides via authoring and operating.](hololens2-corp-connected-deploy.md#validate-dynamics-365-guides)
### Maintain
> [!div class="checklist"]
>- [Update HoloLens 2.](hololens2-corp-connected-maintain.md#update-hololens)
>- [How to update Guides (store apps).](hololens2-corp-connected-maintain.md#how-to-update-dynamics-365-guides-and-other-store-apps)
>- [How to update LOB apps.](hololens2-corp-connected-maintain.md#how-to-update-lob-apps) 
>- [Development plan.](hololens2-corp-connected-maintain.md#development-plan) 
>- [Making a support plan.](hololens2-corp-connected-maintain.md#support-plan)
>- [Device management options.](hololens2-corp-connected-maintain.md#device-management)

## Next step 
> [!div class="nextstepaction"]
> [Corporate connected deployment - Prepare](hololens2-corp-connected-prepare.md)
