---
title: Deployment Guide – Corporate connected HoloLens 2 with Dynamics 365 Guides - Maintain
description: Learn how to maintain HoloLens 2 devices over a corporate Connected network with Dynamics 365 Guides.
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

# Maintain - Corporate Connected Guide

## Update HoloLens

Microsoft designed Windows Update for Business to provide IT administrators with additional Windows Update-centric management capabilities, such as the ability to deploy updates to groups of devices and to define maintenance windows for installing updates.

One popular method of managing updates is to do a feature deferral of 30 days. This allows Admins to update and preview new features, gaining first hand knowledge and informing your support desk of any new changes.

Learn how to [manage HoloLens updates](/hololens/hololens-updates), including scheduled days, scheduled time, and setting active hours on the device, so it will update outside of working hours.

## How to update Dynamics 365 Guides (and other store apps)

Dynamics 365 Guides is an In-Box app, and can be updated through the Microsoft Store app. For all apps that are downloaded through the Microsoft Store, they can be [updated through the Microsoft Store](/hololens/holographic-store-apps#update-apps) app itself manually.

## How to update LOB apps

LOB apps can be updated in the same way they were added to Intune. Apps can be updated in Intune by uploading the new app with a higher version number to the existing App configuration. When the device syncs to Intune, it will observe that there is a newer app version and the newer app will be downloaded and replace the old app.

1. To upload the newer app, navigate to the [MEM portal](https://endpoint.microsoft.com/#home) -> **Apps** -> All **apps** -> *TheNameOfYourApp* -> **Properties.**
2. Next to App information, select **Edit.**
3. For the value of &quot;Select file to update&quot;, select your file.
4. From here, use the context menu to open your file explorer and upload the newer version of the LOB app. Ensure to include dependencies as needed.

See more: [Intune App Deployment for HoloLens](/hololens/app-deploy-intune)

## Development Plan

With your device successfully enrolled, you are now prepared to deploy more LOB apps to your devices. For the duration of this Guide, we're using a sample app, but it's more likely that you will want to use custom apps built for your organization's needs.

If you already have a LOB app, then you're ready to [deploy your app through MDM](/hololens/app-deploy-intune). If you'd prefer a different method, then review the [application deployment overview for HoloLens 2](/hololens/app-deploy-overview) to learn more methods of deploying your LOB app to your devices.

If you've yet to create your own LOB app or are still in the process of creation, then review our mixed reality development docs to [start designing and prototyping](/windows/mixed-reality/design/design) or learn the core concepts to [get started with mixed reality development.](/windows/mixed-reality/discover/get-started-with-mr)

## Support Plan

A support plan is an excellent thing to have in place. Having someone, or a group, trained up on troubleshooting the enrollment process on HoloLens devices and also general use of the HoloLens device within your organization is useful. In order to allow your users to have the faster resolution of their issues, we suggest that your escalation process is handled in a similar manner to this order:

1. Your Support desk.
2. Your HoloLens Expert team
3. [HoloLens Docs](/hololens/) / [HoloLens Troubleshooting Docs](/hololens/hololens-troubleshooting)
4. [Contact Support](https://support.serviceshub.microsoft.com/supportforbusiness/create?sapId=e9391227-fa6d-927b-0fff-f96288631b8f)

## Device Management

This guide talked about setting up Mobile Device Management (MDM) and used it to set up some device configurations and apply settings to allow access in terms of Wi-Fi certificates and proxy. However, MDM can also be used to apply device restrictions via CSPs and Policies.

In many cases, devices can have connectivity restrictions, such as Bluetooth, VPN, USB or even turning off access to the camera or microphone. If any of these interests you, then we encourage you to read our [common device restrictions page](/hololens/hololens-common-device-restrictions).

There are other more complex device restrictions you can use. Such as:

- Limiting the pages that can be viewed in the Settings app by using [SettingsPageVisibility](/hololens/settings-uri-list), allowing users to only access the settings they need to adjust, such as changing their Wi-Fi connection.
- Use [Kiosk mode](/hololens/hololens-kiosk) to limit the UI presented to users on a device. You can set Kiosks to show a single app, or multiple apps with a custom start page. Kiosks can also present different experiences to different users.
- [Windows Application Control (WDAC)](/hololens/windows-defender-application-control-wdac) to keep specific apps or processes from launching entirely.

If you'd like to learn about additional methods of device management or device restrictions, then take the next step and read our [Device Management Overview](/hololens/hololens-csp-policy-overview).





