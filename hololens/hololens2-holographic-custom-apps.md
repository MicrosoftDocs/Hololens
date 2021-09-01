---
title: Manage custom apps for HoloLens 2
description: Learn how to install, uninstall, and side load custom holographic apps on HoloLens 2 devices using the Device Portal and Visual Studio.
ms.assetid: 6bd124c4-731c-4bcc-86c7-23f9b67ff616
ms.date: 9/1/2021
manager: sekerawa
keywords: hololens, hololens 2, sideload, side load, side-load, store, uwp, app, install
ms.prod: hololens
ms.sitesec: library
author: qianw211
ms.author: v-qianwen
ms.topic: article
ms.localizationpriority: medium
ms.custom: 
- CI 111456
- CSSTroubleshooting
appliesto:
- HoloLens 2
---

# Manage custom apps for HoloLens 2

HoloLens supports many existing applications from the Microsoft Store, and new apps built specifically for HoloLens. 

For more information about store apps, see [Manage apps with the store](holographic-store-apps.md).

> [!IMPORTANT]
> For enterprise deployments, we don't recommend enabling Developer Mode, which both of these methods use. If you're interested in a secure app deployment method, please review our [App Management: Overview](app-deploy-overview.md).

If you're looking for either developer method of app installation for HoloLens 2 devices, refer to:

- [Device Portal: Installing an App](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#installing-an-app)
- [Using Visual Studio to deploy and debug Apps](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio)

See our [guide](holographic-custom-apps.md) if you'd like to deploy custom apps on HoloLens (1st gen).

## Manage line of business (LOB) apps

What is a line of business (LOB) app?

Line of business, or LOB for short, means a product or products that serve a particular customer transaction or business need. 

You’ll find LOB apps in a wide range of organizations. LOB apps are valued because they solve problems unique to each business. 

When you sideload an app, you deploy an app package to HoloLens.

A provisioning package – also known by the abbreviation “.ppkg” – is a container for a collection of configuration settings. 

With Windows 10, you can create provisioning packages that let you quickly and efficiently configure a device without having to install a new image.

