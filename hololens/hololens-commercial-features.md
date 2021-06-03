---
title: HoloLens solutions in your environment
description: Learn about the Microsoft HoloLens Commercial features that make it easier for businesses to manage HoloLens devices. 
author: scooley
ms.author: scooley
ms.date: 08/26/2019
ms.custom: 
- CI 111456
- CSSTroubleshooting
ms.topic: article
audience: ITPro
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
manager: jarrettr
appliesto:
- HoloLens 2
keywords: HoloLens, commercial, features, mdm, mobile device management, kiosk mode
---

# What can HoloLens do for you?



## Solutions
| I want to... | Solution | Description |  
|---------| ------------|------------|
| Collaborate in real time with remote employees | [**Dynamics 365 Remote Assist**](https://dynamics.microsoft.com/mixed-reality/remote-assist/) | Share your real-time view with experts remotely to get the help you need, and stay hands-free on HoloLens. | 
| Create step-by-step visual work instructions | [**Dynamics 365 Guides**](https://dynamics.microsoft.com/mixed-reality/guides/capabilities/) | Show remote employees how to use their tools and parts in real work situations using HoloLens 2. |
| Develop for HoloLens | [**Get Started**](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials) | Build and manage apps and solutions for the HoloLens 2. |
| Collaborate digitally in realtime through mixed reality | [**Microsoft Mesh**](https://www.microsoft.com/mesh) | Connect with presence, share across space, and collaborate in an immersive way as if you are in person regardless of physical location.
| Use third party apps for HoloLens 2 | [**Microsoft Store**](https://www.microsoft.com/store/collections/hlgettingstarted/hololens) | Explore the ever expanding number of apps available for the HoloLens 2.

## Managing HoloLens in your business
HoloLens includes features that make it easier for businesses to manage and use HoloLens devices. Some features are included with the device while others can be enabled by [Mobile Device Management (MDM) for HoloLens](hololens-mdm-configure.md)  or through [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) using [Windows Configuration Designer](https://www.microsoft.com/store/productId/9NBLGGH4TX22).

| I want to... | Solution | Description |  
|---------| ------------|------------|
Manage how my end users sign in | [**Identity**](hololens-identity.md) | HoloLens supports several kinds of user identities - Azure Active Directory (AAD), Microsoft Account (MSA), and local accounts.  |
| Encrypt user data | [**Data security**](security-encryption-data-protection.md) | BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device. | 
Deploy at scale | [**Mobile Device Managment**](hololens-mdm-configure.md) | Manage settings, select apps to install and set security configurations tailored to your organization's need on multiple devices. | 
|Minimize setup time for new users and devices | [**Autopilot**](hololens2-autopilot.md) | Configure the out-of-box experience (OOBE) in Microsoft Endpoint Manager and enable end users to prepare devices for business use with little to no interaction. |  
| Control OS updates for my devices | [**Windows Update for Business**](hololens-updates.md#managing-updates-by-using-windows-update-for-business) | Windows Update for Business provides controlled operating system updates to devices and support for the long-term servicing channel. |  
| Allow specific and LOB apps to be downloaded |[**Microsoft Store for Business**](app-deploy-overview.md) | Set up an enterprise private store containing only your company's apps for your specific HoloLens usage. Securely distribute your enterprise software to selected group of enterprise users. | 
| Control what apps are shown on start menus |[**Kiosk mode**](hololens-kiosk.md) |You can use HoloLens in demo or showcase experiences by using kiosk mode, to limit which apps can run.  
| Manage device security with rules for apps and processes | [**Policies (CSPs)**](hololens-csp-policy-overview.md) | IT Admins can define and implement policy settings on HoloLens 2. |  
| Manage how a device connects to the internet | [**Network and Connectivity**](hololens-certificates-network.md) |Anyone in your organization can remotely connect to the corporate network through virtual private network (VPN) on a HoloLens. HoloLens can also access Wi-Fi networks that require credentials. 


  
## Enable your environment

Your organization's IT admin can set up commercial features, such as Microsoft Store for Business, kiosk mode, and enterprise Wi-Fi access. 

1. Identity - [Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) 
1. MDM
1. 

[Planning HoloLens 2 deployment in a commercial environment](hololens-core-components.md) documentation provides step-by-step instructions for enrolling devices and installing apps from Microsoft Store for Business.

## Recommended Content

- [CSPs supported in HoloLens 2 devices](https://docs.microsoft.com/windows/client-management/mdm/policies-in-policy-csp-supported-by-hololens2)
- [Microsoft Store For Business and line of business applications](https://docs.microsoft.com/hololens/app-deploy-overview)
- [Working with line-of-business apps](/microsoft-store/working-with-line-of-business-apps)
