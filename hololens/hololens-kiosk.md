---
title: Set up HoloLens as a kiosk
description: Learn how to setup and use a kiosk configuration to lock down the apps on HoloLens devices. 
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
2. **Multiple app kiosk mode** – Start menu shows only those applications which were set in kiosk configuration for that user, when that user signs in. An app can be chosen to automatically launch if desired. <br> *Example uses*: A device that runs both Guides and Remote Assistance for a range of employees. A device that runs a custom app, and allows the Settings app to change Wi-fi and settings per environment changes.

> [!IMPORTANT]  
> Kiosk mode determines which apps are available when a user signs in to the device. However, kiosk mode is not a security method. It does not stop an "allowed" app from opening another app that is not allowed. In order to block apps or processes from opening, use [Windows Defender Application Control (WDAC) CSP](/windows/client-management/mdm/applicationcontrol-csp) to create appropriate policies.
>
> Learn more about the Microsoft services to give users an advanced level of security that HoloLens 2 uses, read more about [State separation and isolation - Defender protections](security-state-separation-isolation.md#defender-protections). Or learn how to [use WDAC and Windows PowerShell to allow or block apps on HoloLens 2 devices with Microsoft Intune](/mem/intune/configuration/custom-profile-hololens).

## Description of kiosk mode experience when a user signs-in

![Multi app kiosk example](.\images\multi-app-kiosk.jpg)

The following table lists the feature capabilities in the different kiosk modes **(TBD: just specify what is disabled and if there is any way to enable them; and if there something is enabled if there is any way to disable them. If something is not supported, explicitly state).**

| &nbsp; |Start menu |Quick Actions menu |Camera and video |Miracast |Cortana |Built-in voice commands |
| --- | --- | --- | --- | --- | --- | --- |
|Single-app kiosk |Disabled |Disabled |Disabled |Disabled   |Disabled |Enabled<sup>1</sup> |
|Multi-app kiosk |Enabled |Enabled<sup>2</sup> |Available<sup>2</sup> |Available<sup>2</sup> |Available<sup>2, 3</sup>  |Enabled<sup>1</sup> |

> <sup>1</sup> Voice commands that relate to disabled features do not function.  
> <sup>2</sup> For more information about how to configure these features, see [HoloLens AUMIDs for apps](hololens-kiosk-reference.md#hololens-aumids).  
> <sup>3</sup> Even if Cortana is disabled, the built-in voice commands are enabled.

## Key general considerations before configuring kiosk mode

1. Kind of user account - HoloLens supports Azure Active Directory (AAD) accounts, Microsoft Accounts (MSA), Local accounts. Additionally, temporarily created accounts called guests / visitors are also supported (only for kiosk mode). Learn more at [Manage user identity and sign-in for HoloLens](hololens-identity.md).
2. Target users of kiosk mode – Whether it is everyone, a single user, certain users, or users who are member of AAD group(s), etc.
3. For multiple app kiosk mode, determining application(s) to show on start menu. For each application, its Application User Model ID (AUMID) will be needed. Link to reference section.
4. Whether kiosk mode will be applied to HoloLens via either runtime provisioning packages or Mobile Device Management (MDM) server.

## Key technical considerations for Kiosk mode for HoloLens

Applies only if you are planning to use runtime provisioning packages or creating kiosk configurations manually yourself. Kiosk mode configuration uses a hierarchical structure based on XML:

- An assigned access profile defines which applications are displayed in start menu in kiosk mode. You can define multiple profiles in same XML structure which can be referenced later.
- An assigned access configuration references a profile and target user(s) of that profile, e.g., a specific user, or AAD group or visitor, etc. You can define multiple configurations in same XML structure depending on complexity of your usage scenarios (see supported scenarios section below).
- To learn more, refer to [AssignedAccess CSP - Windows Client Management](/windows/client-management/mdm/assignedaccess-csp).

Kiosk mode only controls what applications are shown on start menu or are automatically launched on user sign-in. You can combine kiosk mode with options mentioned below if there are specific security related needs:

- When Settings app is configured to show in kiosk mode and you want to control which pages are shown in Settings app, refer to [Page Settings Visibility](settings-uri-list.md)
- When you want to control access to certain hardware capabilities, e.g. camera, Bluetooth, etc. for certain apps, etc. refer to [Policies in Policy CSP supported by HoloLens 2 - Windows Client Management](/windows/client-management/mdm/policies-in-policy-csp-supported-by-hololens2)
- When you want to completely block launching of certain apps / processes on HoloLens, refer to [Use Windows Defender Application Control on HoloLens 2 devices in Microsoft Intune - Azure](/mem/intune/configuration/custom-profile-hololens)

## Supported scenarios for kiosk mode based on identity type

### For users who sign-in to HoloLens are either Local accounts or MSA:

| **Desired kiosk experience** | **Recommended solution** | **Remarks** |
| --- | --- | --- |
| Every user who signs in gets kiosk experience. | Configure Global Assigned Access profile |
| Specific user who signs in gets kiosk experience. | Configure single or multiple app assigned access profile (as required) specifying name of specific user. | For single app kiosk mode, only local user account or MSA account is supported on HoloLens.For multiple app kiosk mode, only MSA account or AAD account is supported on HoloLens. |

### For users who sign-in to HoloLens using AAD accounts:

| **Desired kiosk experience** | **Recommended solution** | **Remarks** |
| --- | --- | --- |
| Every user who signs in gets kiosk experience. | Configure Global Assigned Access profile |
| Every user who signs in gets kiosk experience except certain users. | Configure Global Assigned Access profile by excluding certain users (who must be device owners). |
| Every AAD user gets separate kiosk experience specific for that user. | Configure assigned access configuration for each user specifying their AAD account name. |
| Users in different AAD groups experience kiosk mode which is for their group only. | Configure assigned access configuration for each desired AAD group. | • When a user signs-in and HoloLens is connected with Internet, if that user is found to be a member of AAD group for which kiosk configuration exists, user gets to experience kiosk for that AAD group. <br> • If there is no internet available when user sign-in, then user will experience HoloLens failure mode behavior. <br> • If internet availability is not guaranteed when user signs-in and AAD group based kiosk needs to be used, consider using AADGroupMembershipCacheValidityInDayspolicy. |
| Users in different AAD groups experience kiosk mode which is for their group only. | Configure assigned access configuration for each desired AAD group except users (designed as device Owners) and ensure they are not members of those AAD groups. | Same behavior as mentioned above.  |
| Users who need to use HoloLens for temporary purposes get kiosk experience. | Configure assigned access configuration for visitors | Temporary user account is automatically created by HoloLens on sign-in and is removed when temporary user signs out. |







## Steps in configuring kiosk mode for HoloLens

Kiosk mode can be deployed for your organization's device via two methods. Kiosks deployed through Intune can be automatically deployed to the device, and provisioning packages can be applied to devices manually.

### Using a MDM solution like Intune

1. Create or update kiosk configuration
When deploying a Kiosk from MDM it is important that each device may only receive one Kiosk profile, otherwise it will create a conflict and receive no Kiosk configurations at all. Other kinds of profiles and policies, such as device restrictions that are not related to the kiosk configuration profile, do not conflict with the kiosk configuration profile.
  
**A. Create a Kiosk [Using the user interface](/mem/intune/configuration/kiosk-settings#create-the-profile)**
  
When setting a Kiosk via Intune's UI take into consideration both the **User logon type** , and how the Kiosk profile configuration will be assigned. The assignment determines which devices receive the configuration, same as other policies. Once a device has that policy, the User logon type determines if the user who logs in is presented with the Kiosk on the device.
  
To add apps to your app, add them using their AUMID. You can use [the AUMIDs of in-box HoloLens apps](hololens-kiosk-reference.md#hololens-aumids).

**B. Using XML structure to create configurations for which there is no UX available**
  
You can use a [sample XML](hololens-kiosk-reference.md#kiosk-xml-code-samples).You many create multiple Kiosk profiles in one XML file, and assign each to different users/groups. Your kiosk configuration will be called a **Profile Id** and have a GUID. You will assign that Profile in the configs section by specifying the user type and using the same GUID for the **DefaultProfile Id**.
  
When setting a Kiosk through both MDM and with XML, keep in mind the Assignment, and the user, user group, or user type being set in the Config section of the XML file. The assignment of the policy will determine to which devices receive the configuration, same as other policies. The configurations in the Config section will determine if the user who logs in is presented with the Kiosk on the device.
  
To add apps to your app, add them using their AUMID. You can use [the AUMIDs of in-box HoloLens apps](hololens-kiosk-reference.md#hololens-aumids).

2. Apply kiosk configuration on HoloLens
Once the Kiosk is Assigned to a group, confirm it's deployment status. In Intune, while you're viewing the device configuration select **Device status** to view the deployment. Once the profile is assigned you'll be able to see the devices that will receive the profile. If you don't see the devices expected, ensure that your kiosk is properly assigned.

> [!TIP]
> If you are planning on using a user or user group to assign the kiosk profile, then consider the account that will [Enroll HoloLens in MDM](hololens-enroll-mdm.md). By using the same account for both enrollment and assignment the profile, you can guarantee the deployment.






3. Experience kiosk mode on HoloLens when user signs in
To validate the kiosk is assigned, it's time to sign into the device with a user to experience the kiosk. Be aware that unlocking the device and signing in are different and a fresh sign-in is required, users can sign out from the start menu. Once a user who is receiving the kiosk profile signs into the device they should be presented with the UI experience that you have configured.

If you do not see the kiosk experience then [check your MDM for it's assignment and deployment status](/intune/configuration/device-profile-monitor) and sync the device as needed, or review the XML file (if used) and ensure that the profiles are properly associated with the correct user, user group, or user type.

4. Remove kiosk configuration from HoloLens (if needed)

Remove the assignment of the Kiosk to the user, user group, or user type. Sync the device as needed. Sign out, and back into the device. The kiosk experience should no longer be present.

### Using runtime provisioning package

1. Create or update kiosk configuration

**For single app Kiosk**

In Windows Configuration Designer, you'll need to fill out the AssignedAccess/AssignedAccessSettings section with the account and app AUMID you want to use. You can use [the AUMIDs of in-box HoloLens apps](hololens-kiosk-reference.md#hololens-aumids).

For example a local account named &quot;LocalAccount&quot; using the Settings app would have the following entry:

`{"Account":"LocalAccount","AUMID":"HolographicSystemSettings_cw5n1h2txyewy!App"}`

**For multiple app Kiosk**

  In Windows Configuration Designer, you'll need to fill out the AssignedAccess/MultiAppAssignedAccessSettings, and upload the xml file you'll create that defines your kiosk.

You can use a [sample XML](hololens-kiosk-reference.md#kiosk-xml-code-samples). You many create multiple Kiosk profiles in one XML file, and assign each to different users/groups. Your kiosk configuration will be called a **Profile Id** and have a GUID. You will assign that Profile in the configs section by specifying the user type and using the same GUID for the **DefaultProfile Id**.

To add apps to your app, add them using their AUMID. You can use [the AUMIDs of in-box HoloLens apps](hololens-kiosk-reference.md#hololens-aumids).

2. Apply configuration on HoloLens

You can apply a provision package either [during OOBE during first time set up](hololens-provisioning.md#apply-a-provisioning-package-to-hololens-during-setup), or later [from the Settings app](hololens-provisioning.md#applyremove-a-provisioning-package-to-hololens-after-setup).

3. Experience kiosk mode on HoloLens when user signs in

To validate the kiosk is assigned, it's time to sign into the device with a user to experience the kiosk. Be aware that unlocking the device and signing in are different and a fresh sign-in is required, users can sign out from the start menu. Once a user who is receiving the kiosk profile signs into the device they should be presented with the UI experience that you have configured.

If you do not see the kiosk experience then review the XML file and ensure that the profiles are properly associated with the correct user, user group, or user type.

4. Remove kiosk configuration from HoloLens (if needed)

To remove the Kiosk configuration, [remove the provisioning package via the Settings app](hololens-provisioning.md#applyremove-a-provisioning-package-to-hololens-after-setup). This may involve having the Settings app in your kiosk, or using an account that isn't presented with the Kiosk.

> [!NOTE]
> If you would like your end users to be unable to remove the provisioning package, and you have the Settings app in your Kiosk then you can disable the removal of providing packages via policy. Use the [Security/AllowRemoveProvisioningPackage](/windows/client-management/mdm/policy-csp-security#security-allowremoveprovisioningpackage) and set it to not allow users to remove packages. This can be set in the same provisioning package that applies the Kiosk.
