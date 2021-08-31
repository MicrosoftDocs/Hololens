---
title: Microsoft Store for Business
description: Learn how to work with the Microsoft Store for Business to publish your mixed reality applications to your business. 
keywords: Microsoft Store for Business, msfb, app deployment, store
author: evmill
ms.author: v-evmill
ms.date: 10/13/2021
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: HoloLens
manager: yannisle

---

# Microsoft Store for Business

The Microsoft Store for Business is designed primarily for IT decision-makers and administrators in businesses or organizations with a flexible way to find, acquire, manage, and distribute free and paid apps in select markets to Windows 10 devices in volume.

You can manage Microsoft Store apps and private line-of-business apps in one inventory, and assign and re-use licenses as needed. You can also choose the best distribution method for your organization: directly assign apps to individuals and teams, publish apps to private pages in Microsoft Store, or connect with management solutions for more options.

When Microsoft Store for Business is used by an end user they will launch the Microsoft Store app. Once launched the user will be able to select the tab with their organizations name, they will then be presented with the apps available to them or that device.

> [!Note]
> Microsoft Store for Business does not automatically download (push) apps to devices. However, apps from the Microsoft Store for Business can be associated with your device management (MDM) server to target and sync apps to devices.

Visit the following pages to learn more about how to use the Microsoft Store for Business:

* [Levels of permissions used for installing applications](/mem/intune/configuration/device-restrictions-windows-holographic#app-store)
* [How to add an app to your Store for Business](/mem/intune/apps/store-apps-windows)
* [How to assign apps to groups of employees](/mem/intune/apps/windows-store-for-business)

To associate your Microsoft Store for Business, visit [Associate your Microsoft Store for Business with Intune](/mem/intune/apps/windows-store-for-business#associate-your-microsoft-store-for-business-account-with-intune).

> [!Tip]
> Learn more about [distributing offline apps](/microsoft-store/distribute-offline-apps) when using apps like Advanced Recovery Companion (ARC) and Windows Configuration Designer (WCD).

## Use only private store apps for Microsoft Store

- Introduced in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2).

The RequirePrivateStoreOnly  policy has been enabled for HoloLens. This policy enables the Microsoft Store app to be configured to only show the private store configured for your organization. Limiting access to only the apps you’ve made available.

Learn more about [ApplicationManagement/RequirePrivateStoreOnly](http://windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-requireprivatestoreonly)

## Smart Retry for app updates

- Introduced in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2).

Now enabled for HoloLens is a new policy that allows IT Admins to set a recurring or one time date to restart apps whose update failed due to the app being in use allowing the update to be applied. These can be set based on a few different triggers such as a scheduled time or sign-in. To learn more about how to use this policy please view [ApplicationManagement/ScheduleForceRestartForUpdateFailures](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures).