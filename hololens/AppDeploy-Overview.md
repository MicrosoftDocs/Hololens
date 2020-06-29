---
title: Overview - App Management
description: app, management, app management
keywords: HoloLens, user, account, app, application management,
author: v-jodben
ms.date: 6/22/2020
ms.prod: hololens
ms.topic: article 
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
manager: yannisl
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# App Management: Overview

You can deploy apps on four different paths: **Mobile Device Management (MDM)**, **Microsoft Store for Business**, **Microsoft Store**, or by installing them via **Provisioning**. 

## Mobile Device Management (MDM)

The [MDM](AppDeploy-Intune.md) provides IT decision-makers and administrators to privately auto-install (push) their in-house, line-of-business apps, or purchase apps through the store for a group of users. HoloLens devices work best with Microsoft Intune. The **Company Portal** is a downloadable experience only offered by Intune to give users finer-grained control over IT-managed apps.

> [!NOTE] 
> The following instructions are for users who want to manage their applications with Intune. Microsoft recommends using Intune for application and device management.
	
Mobile Device Management (MDM) is applicable for: 
* MDM deployed + Company Portal 
* Line of Buisness (non-public) apps
* Manual installation of available applications through Company Portal
* Admin push through MDM policy
* Auto update through MDM

## Microsoft Store for Business

The [Microsoft Store for Business](AppDeploy-StoreforBusiness.md) provides IT decision-makers and administrators in businesses to find, acquire, manage, and distribute free and paid apps. IT administrators can manage Microsoft Store apps and private line-of-business apps in one inventory, plus assign and re-use licenses as needed. For more information, visit [Prerequisites for using the Microsoft Store for Business](https://docs.microsoft.com/microsoft-store/prerequisites-microsoft-store-for-business).
	
The Microsoft Store for Business is applicable for: 
* Public or Line of Business apps
* Automatic installation of required applications through MDM association
* User manually downloads apps
* Auto Update

## Microsoft Store apps

The Microsoft Store provides IT decision-makers and administrators in businesses to find, acquire, manage, and distribute public apps.
	
This Microsoft Store is applicable for: 
* Public apps only
* User manually downloads apps
* Auto update if connected to Internet

For more information, visit [Holographic Store Apps](https://docs.microsoft.com/hololens/holographic-store-apps).

## Install via Provisioning Packages

[Provisioning Packages](AppDeploy-ProvisioningPackage.md) allow you to install custom or Line of Business apps, allowing IT pros and administrators to quickly install apps to a local device(s) via USB. This can be done without an internet connection and for any identity type.
	
Installing via Provisioning Packages is applicable for: 
* Line of Buisness (non-public) apps
* Public apps (if offline installer is available)
* USB side-load only
* No auto update (requires manual updates via Provisioning Package)
