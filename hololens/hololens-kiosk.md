---
title: Set up HoloLens as a kiosk
description: Learn how to set up and use a kiosk configuration to lock down the apps on HoloLens devices. 
ms.prod: hololens
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.date: 8/1/2021
ms.custom: 
- CI 115262
- CI 111456
- CSSTroubleshooting
ms.reviewer: 
manager: laurawi
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Set up HoloLens as a kiosk

## What is Kiosk mode?

Kiosk mode is a feature where you can control which applications are shown in start menu when a user signs-in to HoloLens. There are 2 supported scenarios:

1. **Single app kiosk mode** – No start menu is displayed, and a single app is launched automatically, when user signs in. <br> *Example uses*: A device that runs only a Dynamics 365 Guide for new employees. A device that runs only a custom app.
2. **Multiple app kiosk mode** – Start menu shows only those applications, which were set in kiosk configuration for that user, when that user signs in. An app can be chosen to automatically launch if desired. <br> *Example uses*: A device that runs both Guides and Remote Assistance for a range of employees. A device that runs a custom app, and allows the Settings app to change Wi-fi and settings per environment changes.

    <img alt="Multi app kiosk example" src=".\images\multi-app-kiosk.jpg" width="411" height="500" />

## Description of kiosk mode experience when a user signs-in

The following table lists the feature capabilities in the different kiosk modes.

| &nbsp; |Start menu |Quick Actions menu |Camera and video |Miracast |Cortana |Built-in voice commands |
| --- | --- | --- | --- | --- | --- | --- |
|Single-app kiosk |Disabled |Disabled |Disabled |Disabled   |Disabled |Enabled<sup>1</sup> |
|Multi-app kiosk |Enabled |Enabled<sup>2</sup> |Available<sup>2</sup> |Available<sup>2</sup> |Available<sup>2, 3</sup>  |Enabled<sup>1</sup> |

> <sup>1</sup> Voice commands that relate to disabled features do not function.  
> <sup>2</sup> For more information about how to configure these features, see [HoloLens AUMIDs for apps](hololens-kiosk-reference.md#hololens-aumids).  
> <sup>3</sup> Even if Cortana is disabled, the built-in voice commands are enabled.

## Key general considerations before configuring kiosk mode

1. Kind of user account - HoloLens supports Azure Active Directory (AAD) accounts, Microsoft Accounts (MSA) and Local accounts. Additionally, temporarily created accounts called guests / visitors are also supported (only for AAD join devices). Learn more at [Manage user identity and sign-in for HoloLens](hololens-identity.md).
2. Target users of kiosk mode – Whether it is everyone, a single user, certain users, or users who are member of AAD group(s), etc.
3. For multiple app kiosk mode, determining application(s) to show on start menu. For each application, its [Application User Model ID (AUMID)](hololens-kiosk-reference.md#hololens-aumids) will be needed.
4. Whether kiosk mode will be applied to HoloLens via either runtime provisioning packages or Mobile Device Management (MDM) server.

## Key technical considerations for Kiosk mode for HoloLens

Applies only if you are planning to use runtime provisioning packages or creating kiosk configurations manually yourself. Kiosk mode configuration uses a hierarchical structure based on XML:

- An assigned access profile defines which applications are displayed in start menu in kiosk mode. You can define multiple profiles in same XML structure, which can be referenced later.
- An assigned access configuration references a profile and target user(s) of that profile, for example, a specific user, or AAD group or visitor, etc. You can define multiple configurations in same XML structure depending on complexity of your usage scenarios (see supported scenarios section below).
- To learn more, refer to [AssignedAccess CSP](/windows/client-management/mdm/assignedaccess-csp).
- [XML Sample HoloLens Kiosks](hololens-kiosk-reference.md#kiosk-xml-code-samples)

## Security considerations

Kiosk mode determines which apps are available when a user signs in to the device. However, kiosk mode is not a security method. Kiosk mode only controls what applications are shown on start menu or are automatically launched on user sign-in. You can combine kiosk mode with options mentioned below if there are specific security related needs:

- When Settings app is configured to show in kiosk mode and you want to control which pages are shown in Settings app, refer to [Page Settings Visibility](settings-uri-list.md)
- When you want to control access to certain hardware capabilities, for example, camera, Bluetooth, etc. for certain apps, etc. refer to [Policies in Policy CSP supported by HoloLens 2 - Windows Client Management](/windows/client-management/mdm/policies-in-policy-csp-supported-by-hololens2). You can review our [Common device restrictions](hololens-common-device-restrictions.md) for ideas.
- Kiosk does not stop an "allowed" app from opening another app that is not allowed. In order to block apps or processes from opening, use [Windows Defender Application Control (WDAC) CSP](/windows/client-management/mdm/applicationcontrol-csp) to create appropriate policies. When you want to completely block launching of certain apps / processes on HoloLens, refer to [Use Windows Defender Application Control on HoloLens 2 devices in Microsoft Intune - Azure](/mem/intune/configuration/custom-profile-hololens)

## Supported scenarios for kiosk mode based on identity type

### For users who sign-in as either Local account or MSA

| **Desired kiosk experience** | **Recommended solution** | **Remarks** |
| --- | --- | --- |
| Every user who signs in gets kiosk experience. | [Configure multiple app Global Assigned Access profile](hololens-kiosk-reference.md#multiple-app-global-assigned-access-profile) | &nbsp; |
| Specific user who signs in gets kiosk experience. | [Configure single or multiple app assigned access profile (as required) specifying name of specific user.](hololens-kiosk-reference.md#multiple-app-assigned-access-profile-for-a-local-account-or-aad-user-account) | For single app kiosk mode, only local user account or MSA account is supported on HoloLens. <br> For multiple app kiosk mode, only MSA account or AAD account is supported on HoloLens. |

### For users who sign-in as AAD account

| **Desired kiosk experience** | **Recommended solution** | **Remarks** |
| --- | --- | --- |
| Every user who signs in gets kiosk experience. | [Configure multiple app Global Assigned Access profile](hololens-kiosk-reference.md#multiple-app-global-assigned-access-profile) | &nbsp; |
| Every user who signs in gets kiosk experience except certain users. | [Configure multiple app Global Assigned Access profile by excluding certain users (who must be device owners)](hololens-kiosk-reference.md#multiple-app-global-assigned-access-profile-excluding-device-owners). | &nbsp; |
| Every AAD user gets separate kiosk experience specific for that user. | [Configure assigned access configuration for each user specifying their AAD account name.](hololens-kiosk-reference.md#multiple-app-assigned-access-profiles-for-2-aad-users-or-more) | &nbsp; |
| Users in different AAD groups experience kiosk mode that is for their group only. | [Configure assigned access configuration for each desired AAD group.](hololens-kiosk-reference.md#multiple-app-assigned-access-profile-for-2-aad-groups-or-more) | • When a user signs-in and HoloLens is connected with Internet, if that user is found to be a member of AAD group for which kiosk configuration exists, user gets to experience kiosk for that AAD group. <br> • [If there is no internet available when user sign-in, then user will experience HoloLens failure mode behavior.](hololens-kiosk-reference.md#kiosk-mode-behavior-changes-for-handling-of-failures) <br> • If internet availability is not guaranteed when user signs-in and AAD group based kiosk needs to be used, [consider using AADGroupMembershipCacheValidityInDayspolicy](hololens-release-notes.md#cache-azure-ad-group-membership-for-offline-kiosk). |
| Users who need to use HoloLens for temporary purposes get kiosk experience. | [Configure assigned access configuration for visitors](hololens-kiosk-reference.md#multiple-app-assigned-access-profile-for-visitors) | • Temporary user account is automatically created by HoloLens on sign-in and is removed when temporary user signs out. <br> • Consider enabling [visitor auto-login policy](hololens-kiosk-reference.md#enable-visitor-autologon). |

## Steps in configuring kiosk mode for HoloLens

Kiosk mode can be deployed for your organization's device via two methods. Kiosks configured through Microsoft Intune can be automatically deployed to the device, and provisioning packages can be applied to devices manually.

Here are the following ways to configure, select the tab matching the process you'd like to use.

1. Microsoft Intune kiosk template
1. Microsoft Intune custom template
1. Runtime provisioning

[!INCLUDE[](includes/kiosk-configure-steps.md)]
