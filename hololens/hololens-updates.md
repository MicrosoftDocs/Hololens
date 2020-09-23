---
title: Manage HoloLens updates
description: Administrators can use mobile device management to manage updates to HoloLens devices.
ms.prod: hololens
ms.sitesec: library
author: Teresa-Motiv
ms.author: v-tea
audience: ITPro
ms.topic: article
ms.localizationpriority: high
ms.date: 10/13/2020
ms.reviewer: jarrettr
manager: jarrettr
ms.custom: 
- CI 116337
- CI 115825
- CI 111456
- CSSTroubleshooting

---

# Manage HoloLens updates

HoloLens uses Windows Update in the same manner as other Windows 10 devices. When an update is available, it is automatically downloaded and installed the next time that your device is plugged in and connected to the internet. This article describes how to manage updates in an enterprise or other managed environment. For information about how to manage updates to individual HoloLens devices, see [Update HoloLens](hololens-update-hololens.md).

## Manage updates automatically

### Managing updates by using Windows Update for Business

Windows Holographic for Business can use [Windows Update for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb) to manage updates. All HoloLens 2 devices can use Windows Holographic for Business. Make sure that they use Windows Holographic for Business build 10.0.18362.1042 or a later build. If you have HoloLens (1st gen) devices, you have to [upgrade them to Windows Holographic for Business](hololens1-upgrade-enterprise.md) in order to manage their updates.

Windows Update for Business connects HoloLens devices directly to the Windows Update service. By using Windows Update for Business, you can control multiple aspects of the update process&mdash;that is, which devices get which updates at what time. For example, you can roll out updates to a subset of devices for testing, then later roll out updates to the remaining devices. Or, you can define different update schedules for different types of updates.

> [!NOTE]  
> For HoloLens devices, you can automatically manage feature updates (released two times a year) and quality updates (released monthly or as required, including critical security updates). For more information about update types, see [Types of updates managed by Windows Update for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb#types-of-updates-managed-by-windows-update-for-business).

You can configure Windows Update for Business settings for HoloLens by using policies in a Mobile Device Management (MDM) solution such as Microsoft Intune.

### Managing Windows Update for Business by using Microsoft Intune

For a detailed discussion about how to use Intune to configure Windows Update for Business, see [Manage Windows 10 software updates in Intune](https://docs.microsoft.com/intune/protect/windows-update-for-business-configure). For more information about the specific Intune functionality that HoloLens supports, see [Intune update management functions that HoloLens supports](#intune-update-management-functions-that-hololens-supports).

> [!IMPORTANT]  
> Intune provides two policy types for managing updates: *Windows 10 update ring* and *Windows 10 feature update*. The Windows 10 feature update policy type is in public preview at this time and is not supported for HoloLens.
>  
> You can use Windows 10 update ring policies to manage HoloLens 2 updates.

### Configure update policies for HoloLens 2 or HoloLens (1st gen)

This section describes the policies that you can use to manage updates for either HoloLens 2 or HoloLens (1st gen). For more information about the functionality that is available for HoloLens 2, see [Plan and configure update rollouts for HoloLens 2](#plan-and-configure-update-rollouts-for-hololens-2).

[Policy CSP - Update](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update) defines the policies that configure Windows Update for Business.

> [!NOTE]  
> For a list of specific policy configuration service providers (CSPs) that are supported by specific editions of HoloLens, see [Policy CSPs supported by HoloLens devices](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policy-csps-supported-by-hololens-devices).

#### Configure automatic checks for updates

You can use the **Update/AllowAutoUpdate** policy to manage automatic update behavior, such as scanning, downloading, and installing updates. For more information about the available settings for this policy, see [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate).

> [!NOTE]  
> In Microsoft Intune, you can use **Automatic Update Behavior** to change this policy. For more information, see [Manage Windows 10 software updates in Intune](https://docs.microsoft.com/intune/windows-update-for-business-configure).

#### Configure an update schedule

To configure how and when updates are applied, use the following policies:

- [Update/ScheduledInstallDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstallday)  
  - Values: **0**–**7** (0 = every day, 1 = Sunday, 7 = Saturday)
  - Default value: **0** (every day)
- [Update/ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)
  - Values: 0–23 (0 = midnight, 23 = 11 PM)
  - Default value: 3 PM

#### Configure active hours
Starting with [Windows Holographic, verison 2010](hololens-release-notes.md#windows-holographic-version-2010) an IT Admin can specify the active hours range for HoloLens 2 devices.

Active hours identify the period of time when you expect the device to be in use. Automatic restarts after an update will occur outside of the active hours. The specified range will be counted from the active hours start time. You can use MDM, as described in [Configuring active hours with MDM](https://docs.microsoft.com/windows/deployment/update/waas-restart#configuring-active-hours-with-mdm). MDM uses the Update/ActiveHoursStart and Update/ActiveHoursEnd and Update/ActiveHoursMaxRange settings in the Policy CSP to configure active hours.

-	[Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend) - This value sets the end time. There is a 12 hour maximum from start time.
    -	Supported values are 0-23, where 0 is 12 AM, 1 is 1 AM, etc.
    -	The default is 17 (5 PM).
-	[Update/ActiveHoursMaxRange](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursmaxrange) - This value sets max number of active hours from start time.
    -	Supported values are 8-18.
    -	The default value is 18 (hours).
-	[Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart) - This value sets the start time. There is a 12 hour maximum from end time.
    -	Supported values are 0-23, where 0 is 12 AM, 1 is 1 AM, etc.
    -	The default value is 8 (8 AM).

#### For devices that run Windows 10, version 1607 only

You can use the following update policies to configure devices to get updates from Windows Server Update Service (WSUS), instead of from Windows Update:

- [Update/AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)
- [Update/RequireUpdateApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)
- [Update/UpdateServiceUrl](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

### Plan and configure update rollouts for HoloLens 2

HoloLens 2 supports more update automation features than HoloLens (1st gen) does. This is especially true if you use Microsoft Intune to manage Windows Update for Business policies. These features make it easier for you to plan and implement update rollouts across your organization.

#### Plan the update strategy

Windows Updates for Business supports deferral policies. After Microsoft releases an update, you can use a deferral policy to define how long to wait before installing that update on devices. By associating subsets of your devices (also known as *update rings*) with different deferral policies, you can coordinate an update rollout strategy for your organization.

For example, consider an organization that has 1,000 devices, and has to update the devices in five waves. The organization can create five update rings, as shown in the following table.

|Group |Number of devices |Deferral (days) |
| ---| :---: | :---: |
|Grp 1 (IT staff) |5 |0 |
|Grp 2 (early adopters) |50 |60 |
|Grp 3 (main 1) |250 |120 |
|Grp 4 (main 2) |300 |150 |
|Grp 5 (main 3) |395 |180 |

Here's how the rollout progresses over time to the whole organization.

![Timeline for deploying updates](./images/hololens-updates-timeline.png)

#### Configure an update deferral policy

A deferral policy specifies the number of days between the date on which an update becomes available and the date on which the update is offered to a device.

You can configure different deferrals for feature updates and quality updates. The following table lists the specific policies to use for each type, and the maximum deferral for each.

|Category |Policy |Maximum deferral |
| --- | --- | --- |
|Feature updates |DeferFeatureUpdatesPeriodInDays |365 days |
|Quality updates |DeferQualityUpdatesPeriodInDays |30 days |

#### Pause Updates via Device

If a user does not have access to MDM they can indivually Pause updates for up to 35 days manually on a HoloLens 2 device on build [Windows Holographic, version 2004](hololens-release-notes#windows-holographic-version-2004) or later. Users can reach this setting by navigating to **Settings -> Update & Security -> Advanced options** scroll down to **Pause updates** and select the date until which they will pause updates. Once a user reached the pause limit, the device will need to get new updates because they can pause again. 

Starting with [Windows Holographic, verison 2010](hololens-release-notes.md#windows-holographic-version-2010), this pause updates fuction can be managed for HoloLens 2 devices. 
- [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess).
    - 0 (default) – Enabled
    - 1 – Disabled

#### Intune update management functions that HoloLens supports

You can use the following Intune update management functions to manage updates for HoloLens.

- **Create** and **Assign**: These functions add a Windows 10 update ring to the list of update rings. For more information, see [Create and assign update rings](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure#create-and-assign-update-rings).

- **Pause**: If you encounter a problem when you deploy a feature or quality update, you can pause the update for 35 days (starting from a specified date). This pause prevents other devices from installing the update until you resolve or mitigate the problem. If you pause a feature update, quality updates are still offered to devices to make sure that they stay secure. When an update type is paused, the Overview pane for that ring displays how many days remain before that update type resumes. After the specified time has passed, the pause automatically expires, and the update process resumes.

  While the update ring is paused, you can select either of the following options:

  - **Extend**: Extend the pause period for an update type for 35 days.
  - **Resume**: Restore updates for that ring to active operation. You can pause the update ring again, if it is necessary.

  > [!NOTE]  
  > The **Uninstall** operation for update rings is not supported for HoloLens 2 devices.

## Manually check for updates

Although HoloLens periodically checks for system updates, there may be circumstances in which you want to manually check.

To manually check for updates, go to **Settings** > **Update & Security** > **Check for updates**. If the Settings app indicates that your device is up to date, you have all the updates that are currently available.

## Manually roll back an update

In some cases, you might want to revert to a previous version of the HoloLens software. The process for doing this depends on whether you are using HoloLens 2 or HoloLens (1st gen).

### Revert to a previous version (HoloLens 2)

You can roll back updates and return to a previous version of HoloLens 2 by using the [Advanced Recovery Companion](https://www.microsoft.com/p/advanced-recovery-companion/9p74z35sfrs8?activetab=pivot:overviewtab) to reset your HoloLens to the earlier version.

> [!NOTE]
> Reverting to an earlier version deletes your personal files and settings.

To revert to a previous version of HoloLens 2, follow these steps:

1. Make sure that you don't have any phones or Windows devices plugged in to your computer.
1. On your computer, download the [Advanced Recovery Companion](https://www.microsoft.com/p/advanced-recovery-companion/9p74z35sfrs8?activetab=pivot:overviewtab) from the Microsoft Store.
1. Download the [most recent HoloLens 2 release](https://aka.ms/hololens2download).
1. After these downloads finish, open **File explorer** > **Downloads**, right-click the compressed (.zip) folder that you just downloaded, and then select **Extract all** > **Extract** to expand the file.
1. Use a USB-A to USB-C cable to connect your HoloLens device to your computer. Even if you've been using other cables to connect your HoloLens, this kind of cable works best.
1. The Advanced Recovery Companion automatically detects your HoloLens device. Select the **Microsoft HoloLens** tile.
1. On the next screen, select **Manual package selection**, and then open the folder that you previously expanded.
1. Select the installation (.ffu) file.
1. Select **Install software**, and then follow the instructions.

### Revert to a previous version (HoloLens (1st gen))

You can roll back updates and return to a previous version of HoloLens (1st gen) by using the [Windows Device Recovery Tool (WDRT)](https://support.microsoft.com/help/12379) to reset your HoloLens to the earlier version.

> [!NOTE]
> Reverting to an earlier HoloLens version deletes your personal files and settings.

To revert to a previous version of HoloLens (1st gen), follow these steps:

1. Make sure that you don't have any phones or Windows devices plugged into your computer.
1. On your computer, download the [Windows Device Recovery Tool (WDRT)](https://support.microsoft.com/help/12379).
1. Download the [HoloLens Anniversary Update recovery package](https://aka.ms/hololensrecovery).
1. After the downloads finish, open **File explorer** > **Downloads**, right-click the compressed (.zip) folder that you just downloaded, and then select **Extract all** > **Extract** to expand the file.
1. Use the micro-USB cable that was provided together with your HoloLens device to connect your HoloLens device to your computer. Even if you've been using other cables to connect your HoloLens device, this one works best.
1. The WDRT automatically detects your HoloLens device. Select the **Microsoft HoloLens** tile.
1. On the next screen, select **Manual package selection**, and then open the folder that you previously expanded.
1. Select the installation (.ffu) file.
1. Select **Install software**, and then follow the instructions.

**If WDRT doesn't detect your device**

If WDRT doesn't detect your HoloLens device, try restarting your computer. If that doesn't work, select **My device was not detected**, select **Microsoft HoloLens**, and then follow the instructions.

## Related articles

- [HoloLens 2 release notes](https://docs.microsoft.com/hololens/hololens-release-notes)
- [What is Windows Update for Business?](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb)
- [Assign devices to servicing channels for Windows 10 updates](https://docs.microsoft.com/windows/deployment/update/waas-servicing-channels-windows-10-updates)
- [Manage Windows 10 software updates in Intune](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure)
