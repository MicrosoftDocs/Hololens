---
title: Deployment Guide – Corporate connected HoloLens 2 with Dynamics 365 Guides - Overview
description: Learn how to enroll HoloLens 2 devices over a corporate Connected network with Dynamics 365 Guides.
keywords: HoloLens, management, corporate connected, Dynamics 365 Guides, AAD, Azure AD, MDM, Mobile Device Management
author: joyjaz
ms.author: v-jjaswinski
ms.reviewer: aboeger
ms.date: 03/16/2021
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

In this guide, we will cover how to enroll your devices into your existing device management, applying licenses as needed, and validating that your end users are able to operate a Dynamics 365 Guide, as well as using a custom line of business apps, after device set up. 

## Prerequisite Infrastructure

The following infrastructure should already be in place:
- Wi-Fi
    - Internal corporate network with access to internal resources and limited access to the internet or Cloud services
    - Device-based certificate authentication.
- Azure AD Join with MDM Auto Enrollment ([Azure Active Directory P1 subscription](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) needed)
- MDM (Intune) Managed
    - One or more applications are deployed via MDM.
- Users sign in with their own corporate account (AAD)
    - Single or multiple users per device supported.
- Varying levels of device lockdown configurations are applied based on specific use cases, from Fully Open to Single App Kiosk.

## New Infrastructure

- Network 
    - Certificates
    - Proxy configuration
- Custom apps deployment
    - uploading, 
    - assigning, and 
    - setting your app to automatically download to specific devices

## Guides Licensing and Requirements
- Azure Active Directory account
- Dynamics 365 Guides subscription
    - Microsoft Dataverse (included)
    - Power Apps (included)
- Power BI Desktop
- Network Connectivity

## Stages of Deployment
### Prepare
> [!div class="checklist"]
>- [Learn about the infrastructure essentials for HoloLens 2 devices.](hololens2-corp-connected-prepare.md#infrastructure-essentials)
>- [Learn more about Azure AD and set up one if you don't have it.](hololens2-corp-connected-prepare.md#Azure-Active-Directory)
>- [Learn about Identity management and how to best set up Azure AD accounts.](hololens2-corp-connected-prepare.md#Identity-Management)
>- [Learn more about MDM and set up with Intune if you don't already have one ready.](hololens2-corp-connected-prepare.md#Mobile-Device-Management)
>- [Familiarize yourself with certificate-based Wi-Fi](hololens2-corp-connected-prepare.md#Certificates)
>- [Familiarize yourself with Proxy](hololens2-corp-connected-prepare.md#Proxy)
>- [Understand how you can use Line of Business Apps](hololens2-corp-connected-prepare.md#Line-of-Business-Apps)
>- [Learn more about the way you can use Guides for your organization](hololens2-corp-connected-prepare.md#Guides-Playbook)
### Configure
> [!div class="checklist"]
>- [How to create users and groups](hololens2-corp-connected-configure.md#Azure-Users-and-Groups)
>- [How to set up Auto Enrollment](hololens2-corp-connected-configure.md#Auto-Enrollment-on-HoloLens-2)
>- [Wi-Fi Certificates Set up](hololens2-corp-connected-configure.md#Wi-Fi-and-Certificates-and-Wi-Fi-Set-up)
>- [Configure Proxy](hololens2-corp-connected-configure.md#Proxy-Set-up)
>- [Upload and Assign Line of Business (LOB) App packages](hololens2-corp-connected-configure.md#App-Deployment)
>- [Setup Dynamics 365 Guides](hololens2-corp-connected-configure.md#Setup-Guides:-Application-licenses,-dataverse,-and-authoring)
>- [Optional: Kiosk](hololens2-corp-connected-configure.md#Optional:-Kiosk-mode)
>- [Optional: WDAC](hololens2-corp-connected-configure.md#Optional:-WDAC)
### Deploy
> [!div class="checklist"]
>-	[Validate enrollment via device and MDM](hololens2-corp-connected-deploy.md#Enrollment-Validation)
>-	[Wi-Fi certificate validation](hololens2-corp-connected-deploy.md#Wi-Fi-certificate-validation)
>-	[Validate LOB app install](hololens2-corp-connected-deploy.md#Validate-Line-of-Business-(LOB)-app-install)
>-	[Validate Guides via authoring and operating](hololens2-corp-connected-deploy.md#Validate-Dynamics-365-Guides)
### Maintain
> [!div class="checklist"]
>- [Update HoloLens 2.](hololens2-corp-connected-maintain.md#Update-HoloLens)
>- [How to update Guides (store apps).](hololens2-corp-connected-maintain.md#How-to-update-Dynamics-365-Guides-(and-other-store-apps))
>- [How to update LOB apps.](hololens2-corp-connected-maintain.md#How-to-update-Line-of-Business-(LOB)-apps) 
>- [How to manage HoloLens Updates.](hololens2-corp-connected-maintain.md#Update-HoloLens)
>- [Development plan.](hololens2-corp-connected-maintain.md#Development-Plan) 
>- [Making a support plan.](hololens2-corp-connected-maintain.md#Support-Plan)
>- [Device management options](hololens2-corp-connected-maintain.md#Device-Management)

# Next step 
> [!div class="nextstepaction"]
> [Corporate connected deployment - Prepare](hololens2-corp-connected-prepare.md)
