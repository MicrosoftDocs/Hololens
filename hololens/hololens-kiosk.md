---
title: Set up HoloLens as a kiosk
description: Learn how to set up and use a kiosk configuration to lock down the apps on HoloLens devices. 
ms.prod: hololens
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.date: 8/24/2021
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

1. **Single app kiosk mode** – No start menu is displayed, and a single app is launched automatically, when user signs in.

    *Example uses*: A device that runs only Dynamics 365 Guides app.

2. **Multiple app kiosk mode** – Start menu shows only those applications, which were specified in kiosk configuration when a user signs in. An app can be chosen to automatically launch if desired.

    *Example uses*: A device that shows only the Store app, Feedback Hub and Settings app in start menu.

    <br/><img alt="Multi app kiosk example" src=".\images\multi-app-kiosk.jpg" width="411" height="500" />

## Description of kiosk mode experience when a user signs-in

The following table lists the feature capabilities in the different kiosk modes.

||**Start menu**|**Quick Actions menu**|**Camera and video**|**Miracast**|**Cortana**|**Built-in voice commands**|
| --- | --- | --- | --- | --- | --- | --- |
|**Single-app kiosk**|Disabled |Disabled |Disabled |Disabled   |Disabled |Enabled* |
|**Multi-app kiosk**|Enabled |Enabled*  |Available*  |Available* |Available*   |Enabled*  |

\* For more information about how to enable disabled features, or how voice commands interact with disabled features and Cortana see [HoloLens AUMIDs for apps](hololens-kiosk-reference.md#hololens-application-user-model-ids-aumids).

## Key general considerations before configuring kiosk mode

1. Determine the kind of user account signing into HoloLens in your environment - HoloLens supports Azure Active Directory (AAD) accounts, Microsoft Accounts (MSA) and Local accounts. Additionally, temporarily created accounts called guests / visitors are also supported (only for AAD join devices). Learn more at [Manage user identity and sign-in for HoloLens](hololens-identity.md).

2. Determine the targets of kiosk mode experience – Whether it is everyone, a single user, certain users, or users who are member of AAD group(s), etc.

3. For multiple app kiosk mode, determine application(s) to show on start menu. For each application, its [Application User Model ID (AUMID)](hololens-kiosk-reference.md#hololens-application-user-model-ids-aumids) will be needed.

4. Determine if kiosk mode will be applied to HoloLens via either runtime provisioning packages or Mobile Device Management (MDM) server.

## Security considerations

Kiosk mode should not be considered as a security method but as a means to control start up experience on user sign-in. You may combine kiosk mode experience with options mentioned below if there are specific security related needs:

- When Settings app is configured to show in kiosk mode and you want to control which pages are shown in Settings app, refer to [Page Settings Visibility](settings-uri-list.md).

- When you want to control access to certain hardware capabilities, for example, camera, Bluetooth, etc. for certain apps, etc. refer to [Policies in Policy CSP supported by HoloLens 2 - Windows Client Management](/windows/client-management/mdm/policies-in-policy-csp-supported-by-hololens2). You can review our [Common device restrictions](hololens-common-device-restrictions.md) for ideas.

- Kiosk mode does not block an app (configured as part of kiosk experience) from launching other apps. When you want to completely block launching of certain apps / processes on HoloLens, refer to [Use Windows Defender Application Control on HoloLens 2 devices in Microsoft Intune - Azure](/mem/intune/configuration/custom-profile-hololens).

## Key technical considerations for Kiosk mode for HoloLens

Applies only if you are planning to use runtime provisioning packages or creating kiosk configurations manually yourself. Kiosk mode configuration uses a hierarchical structure based on XML:

- An assigned access profile defines which applications are displayed in start menu in kiosk mode. You can define multiple profiles in same XML structure, which can be referenced later.

- An assigned access configuration references a profile and target user(s) of that profile, for example, a specific user, or AAD group or visitor, etc. You can define multiple configurations in same XML structure depending on complexity of your usage scenarios (see supported scenarios section below).

- To learn more, refer to [AssignedAccess CSP](/windows/client-management/mdm/assignedaccess-csp).

## Supported scenarios for kiosk mode based on identity type

See [reference links](hololens-kiosk-reference.md#kiosk-xml-code-samples) for examples based on your scenario and update as needed before copy-pasting.

> [!NOTE]
> Use XML only if not using Intune's UI to create kiosk configuration.

### For users who sign-in as either Local account or MSA

| Desired kiosk experience | Recommended kiosk configuration | Ways to configure | Remarks |
| --- | --- | --- | --- |
| Every user who signs in gets kiosk experience. | [Configure multiple app Global Assigned Access profile](hololens-kiosk-reference.md#multiple-app-global-assigned-access-profile) | • [Microsoft Intune custom template](hololens-kiosk.md?tabs=intunecustom#steps-in-configuring-kiosk-mode-for-hololens) <br> • [Runtime provisioning - Multi app](hololens-kiosk.md?tabs=ppkgmak#steps-in-configuring-kiosk-mode-for-hololens) | Global assigned access requires [20H2 and newer builds](hololens-release-notes.md#windows-holographic-version-20h2) |
| Specific user who signs in gets kiosk experience.  | [Configure single or multiple app assigned access profile (as required) specifying name of specific user.](hololens-kiosk-reference.md#multiple-app-assigned-access-profile-for-a-local-account-or-aad-user-account) | [See supported options below.](#steps-in-configuring-kiosk-mode-for-hololens) | For single app kiosk mode, only local user account or MSA account is supported on HoloLens. <br><br/>For multiple app kiosk mode, only MSA account or AAD account is supported on HoloLens. |

### For users who sign-in as AAD account

| Desired kiosk experience | Recommended kiosk configuration | Ways to configure | Remarks |
| --- | --- | --- | --- |
| Every user who signs in gets kiosk experience. | [Configure multiple app Global Assigned Access profile](hololens-kiosk-reference.md#multiple-app-global-assigned-access-profile) | • [Microsoft Intune custom template](hololens-kiosk.md?tabs=intunecustom#steps-in-configuring-kiosk-mode-for-hololens) <br> • [Runtime provisioning - Multi app](hololens-kiosk.md?tabs=ppkgmak#steps-in-configuring-kiosk-mode-for-hololens) | Global assigned access requires [20H2 and newer builds](hololens-release-notes.md#windows-holographic-version-20h2) |
| Every user who signs in gets kiosk experience except certain users. | [Configure multiple app Global Assigned Access profile by excluding certain users (who must be device owners)](hololens-kiosk-reference.md#multiple-app-global-assigned-access-profile-excluding-device-owners). | • [Microsoft Intune custom template](hololens-kiosk.md?tabs=intunecustom#steps-in-configuring-kiosk-mode-for-hololens) <br> • [Runtime provisioning - Multi app](hololens-kiosk.md?tabs=ppkgmak#steps-in-configuring-kiosk-mode-for-hololens) | Global assigned access requires [20H2 and newer builds](hololens-release-notes.md#windows-holographic-version-20h2) |
| Every AAD user gets separate kiosk experience specific for that user. | [Configure assigned access configuration for each user specifying their AAD account name.](hololens-kiosk-reference.md#multiple-app-assigned-access-profiles-for-two-aad-users-or-more) | • [Microsoft Intune custom template](hololens-kiosk.md?tabs=intunecustom#steps-in-configuring-kiosk-mode-for-hololens) <br> • [Runtime provisioning - Multi app](hololens-kiosk.md?tabs=ppkgmak#steps-in-configuring-kiosk-mode-for-hololens) | &nbsp; |
| Users in different AAD groups experience kiosk mode that is for their group only. | [Configure assigned access configuration for each desired AAD group.](hololens-kiosk-reference.md#multiple-app-assigned-access-profile-for-two-aad-groups-or-more) | • [Microsoft Intune custom template](hololens-kiosk.md?tabs=intunecustom#steps-in-configuring-kiosk-mode-for-hololens) <br> • [Runtime provisioning - Multi app](hololens-kiosk.md?tabs=ppkgmak#steps-in-configuring-kiosk-mode-for-hololens) | • When a user signs-in and HoloLens is connected with Internet, if that user is found to be a member of AAD group for which kiosk configuration exists, user gets to experience kiosk for that AAD group. <br> • [If there is no internet available when user sign-in, then user will experience HoloLens failure mode behavior.](#issue---no-apps-are-shown-in-start-menu-in-kiosk-mode) <br> • If internet availability is not guaranteed when user signs-in and AAD group based kiosk needs to be used, [consider using AADGroupMembershipCacheValidityInDayspolicy](hololens-release-notes.md#cache-azure-ad-group-membership-for-offline-kiosk). <br> •  For optimal experience with AAD groups during sign-in, recommendation is to use [AADGroupMembershipCacheValidityInDayspolicy](/hololens/hololens-release-notes#cache-azure-ad-group-membership-for-offline-kiosk) |
| Users who need to use HoloLens for temporary purposes get kiosk experience. | [Configure assigned access configuration for visitors](hololens-kiosk-reference.md#multiple-app-assigned-access-profile-for-visitors) | • [Microsoft Intune custom template](hololens-kiosk.md?tabs=intunecustom#steps-in-configuring-kiosk-mode-for-hololens) <br> • [Runtime provisioning - Single app](hololens-kiosk.md?tabs=ppkgsak#steps-in-configuring-kiosk-mode-for-hololens) | • Temporary user account is automatically created by HoloLens on sign-in and is removed when temporary user signs out. <br> • Consider enabling [visitor auto-login policy](#how-can-visitor-accounts-automatically-logon-to-kiosk-experience). |

## Steps in configuring kiosk mode for HoloLens

Kiosk configurations can be created and applied in following ways:

1. With MDM server's UI, e.g., Intune's kiosk templates or it custom OMA-URI configurations, which are then remotely applied to HoloLens.
2. With runtime provisioning packages, which are then directly applied to HoloLens.

Here are the following ways to configure, select the tab matching the process you'd like to use.

1. [Microsoft Intune single app kiosk template](hololens-kiosk.md?tabs=uisak#steps-in-configuring-kiosk-mode-for-hololens)
2. [Microsoft Intune multi app kiosk template](hololens-kiosk.md?tabs=uimak#steps-in-configuring-kiosk-mode-for-hololens)
1. [Microsoft Intune custom template](hololens-kiosk.md?tabs=intunecustom#steps-in-configuring-kiosk-mode-for-hololens)
1. [Runtime provisioning - Multi app](hololens-kiosk.md?tabs=ppkgmak#steps-in-configuring-kiosk-mode-for-hololens)
1. [Runtime provisioning - Single app](hololens-kiosk.md?tabs=ppkgsak#steps-in-configuring-kiosk-mode-for-hololens)

[!INCLUDE[](includes/kiosk-configure-steps.md)]

## Frequently Asked Questions

### How can visitor accounts automatically logon to kiosk experience?

On builds [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1) and onwards:

- AAD and Non-ADD configurations both support visitor accounts being autologon enabled for Kiosk modes.

[!INCLUDE[](includes/kiosk-autologin.md)]

### Is kiosk experience supported on HoloLens (1st gen)?

Kiosk mode is available only if the device has Windows Holographic for Business. All HoloLens 2 devices ship with Windows Holographic for Business and there are no other editions. Every HoloLens 2 device is able to run Kiosk mode out of the box.

HoloLens (1st gen) devices need to be upgraded both in terms of OS build and OS edition. Here is more information on updating a HoloLens (1st gen) to [Windows Holographic for Business](hololens1-upgrade-enterprise.md) edition. To update a HoloLens (1st gen) device to use kiosk mode, you must first make sure that the device runs Windows 10, version 1803, or a later version. If you have used the Windows Device Recovery Tool to recover your HoloLens (1st gen) device to its default build, or if you have installed the most recent updates, your device is ready to configure.

### How to use device portal to configure kiosk in non-production environments?

Set up the [HoloLens device to use the Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal). The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.

 > [!CAUTION]
 > When you set up HoloLens to use the Device Portal, you have to enable Developer Mode on the device. Developer Mode on a device that has Windows Holographic for Business enables you to side-load apps. However, this setting creates a risk that a user can install apps that have not been certified by the Microsoft Store. Administrators can block the ability to enable Developer Mode by using the **ApplicationManagement/AllowDeveloper Unlock** setting in the [Policy CSP](/windows/client-management/mdm/policy-configuration-service-provider). [Learn more about Developer Mode.](/windows/uwp/get-started/enable-your-device-for-development#developer-mode)

Kiosk Mode can be set via Device Portal’s REST API by doing a POST to /api/holographic/kioskmode/settings with one required query string parameter (“kioskModeEnabled” with a value of “true” or “false”) and one optional parameter (“startupApp” with a value of a package name). Keep in mind that Device Portal is intended for developers only and should not be enabled on non-developer devices. The REST API is subject to change in future updates/releases.

## Troubleshooting

### Issue - No apps are shown in start menu in kiosk mode

**Symptoms**

When encountering failures in applying kiosk mode, the following behavior appears:

- Prior to Windows Holographic, version 20H2 - HoloLens will show all applications in the Start menu.
- Windows Holographic, version 20H2 - if a device has a kiosk configuration, which is a combination of both global assigned access and AAD group member assigned access, if determining AAD group membership fails, the user will see “nothing shown in start” menu.

  ![Image of what Kiosk mode now looks when it fails.](images/hololens-kiosk-failure-behavior.png )

- Starting with [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1), Kiosk mode looks for Global Assigned Access before showing an empty start menu. The kiosk experience will fall back to a global kiosk configuration (if present) if there are failures during AAD group kiosk mode.

**Troubleshooting steps**

- Verify that AUMID of app is correctly specified and it does not contain versions. Refer to [HoloLens AUMIDs](hololens-kiosk-reference.md#hololens-application-user-model-ids-aumids) for inbox apps for examples.

- Ensure that application is installed on the device for that user.

- If kiosk configuration is based on AAD groups please ensure internet connectivity is present when the AAD user signs in. If desired configure [MixedReality/AADGroupMembershipCacheValidityInDays](/windows/client-management/mdm/policy-csp-mixedreality#mixedreality-aadgroupmembershipcachevalidityindays) policy so this can function without internet as well.

If XML was used to create assigned access configuration (either via runtime provisioning or Intune custom-OMA URI), please ensure that XML is well-formed by opening it in any web browser or XML editor. Refer to [Kiosk XML code samples](hololens-kiosk-reference.md#kiosk-xml-code-samples) for well-formed and valid templates.

### Issue - Building a package with kiosk mode failed

**Symptoms**

A dialog like below is shown.

:::image type="content" alt-text="Kiosk failure to build." source="./images/kiosk-steps/kiosk-ppkg-failure.png":::


**Troubleshooting steps**

1. Click on the hyper-link shown as in the dialog above.
1. Open ICD.log in a text editor and its contents should indicate the error.

> [!NOTE]
> If you have made several attempts, check the time stamps in the log. This will help you check only the current issues.

### Issue – Provisioning package built successfully but failed to apply.

**Symptoms**

Error is shown when applying the provisioning package on HoloLens.

**Troubleshooting steps**

1. Browse to the folder where Windows Configuration Designer project for runtime provisioning package exists.
1. Open ICD.log and ensure that there are no errors in the log while building the provisioning package. Some errors are not showing during build but are still logged in ICD.log

### Issue – Multiple app assigned access to AAD group does not work

**Symptoms**

On AAD user sign-in, device does not go into expected kiosk mode.

**Troubleshooting steps**

- Confirm in Assigned Access configuration XML that GUID of AAD group of which signed-in user is a member of is used and not the GUID of the AAD user.
- Confirm that in Intune portal that AAD user is indeed shown as member of targeted AAD group.
- For Intune only, confirm that device is showing as compliant. Refer to [device compliance reference](/mem/intune/protect/device-compliance-get-started) for more information.
