---
title: Overview - App Management
description: Get started with an overview of mixed reality app management with mobile device management, Microsoft store for business, provisioning package, and App Installer.
keywords: HoloLens, user, account, app, application management,
ms.date: 6/22/2020
ms.service: hololens
ms.topic: article 
ms.sitesec: library
ms.localizationpriority:
audience: ITPro
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# App Management: Overview

You can deploy apps on four different paths: **Mobile Device Management (MDM)**, **Microsoft Store**, **Provisioning**, or by installing them via App Installer.

## Mobile Device Management (MDM)

An MDM solution enables IT decision-makers and administrators to privately auto install (push) their in-house, line-of-business apps, or purchase apps through the store for a group of users. HoloLens devices work best with Microsoft Intune for [application management](app-deploy-intune.md). Intune also offers users finer-grained control over IT-managed apps through the Company Portal downloadable experience.

> [!NOTE]
> The following instructions are for users who want to manage their applications with Intune. Microsoft recommends using Intune for application and device management.

Mobile Device Management (MDM) is applicable for:

* MDM deployed + Company Portal
* Line of Business (non public) apps
* Manual installation of available applications through Company Portal
* Admin push through MDM policy
* Auto update through MDM

## Microsoft Store 

The Microsoft Store provides IT decision-makers and administrators in businesses to find, acquire, manage, and distribute public apps.

This Microsoft Store is applicable for:

* Public apps only
* User manually downloads apps
* Auto update if connected to Internet

For more information, visit [Holographic Store Apps](/hololens/holographic-store-apps).

> [!NOTE]
> With the [retirement](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/update-to-intune-integration-with-the-microsoft-store-on-windows/ba-p/3585077) of the Microsoft Store for Business, how to deploy apps has changed.  See [Microsoft Store for Business & Intune](/hololens/app-deploy-store-business) for more information.

## Install via Provisioning Packages

[Provisioning Packages](app-deploy-provisioning-package.md) allow you to install custom or Line of Business apps, allowing IT pros and administrators to install apps quickly to a local device(s) via USB. This installation can be done without an internet connection and for any identity type.

Installing via Provisioning Packages is applicable for:

* Line of Business / Self-developed (non public) apps
* Public apps (if offline installer is available)
* USB side-loading only
* No auto update (requires manual updates via Provisioning Package)

## Install Apps on HoloLens 2 via App Installer

With the [App Installer](app-deploy-app-installer.md), users can have an experience that is simple for either installing Apps on local devices or sharing an app with someone else who is unfamiliar with other app install methods on HoloLens. This method does not need to enable Developer Mode or use Device Portal. It is a simple method of distributing a built app. It also works easily, whether you'd like to deploy your app or you simply want to demo your app to another user with a HoloLens.

Installing via App Installer is applicable for:

* Line of Business / Self-developed (non public) apps
* Side-load only
* Doesn't require Developer mode or Device portal
* Easy for end user to install







