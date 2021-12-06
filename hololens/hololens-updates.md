---
title: Manage HoloLens updates
description: Learn how your administrators can use mobile device management to manage updates to HoloLens devices.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
audience: ITPro
ms.topic: article
ms.localizationpriority: high
ms.date: 11/1/2021
ms.reviewer: shriyen
manager: ranjibb
appliesto:
- HoloLens (1st gen)
- HoloLens 2
ms.custom: 
- CI 116337
- CI 115825
- CI 111456
- CSSTroubleshooting
---

# Manage HoloLens updates

HoloLens uses Windows Update in the same manner as other Windows 10 devices. When an update is available, it is automatically downloaded and installed the next time that your device is plugged in and connected to the internet. This article describes how to manage updates in an enterprise or other managed environment. For information about how to manage updates to individual HoloLens devices, see [Update HoloLens](hololens-update-hololens.md).

## How to optimize HoloLens updates

While the process of applying updates to HoloLens devices is similar to other Windows 10 devices, the device itself is different in subtle ways. For example, just like a PC, HoloLens performs updates in 3 steps: find eligible updates (**scan**), fetch the latest eligible update (**download & install**), and apply that update (**reboot**). However, each of those steps can be optimized further specifically for HoloLens devices to ensure that updates occur seamlessly and as soon as possible.

**Overall summary of best practices:** The device should be plugged in and connected to the internet outside of configured Active Hours, usually overnight, to ensure an update can be applied. Go to **Settings** -> **Update & Security** -> **Windows Update** to see current Active Hour settings.

### 1. Scan

#### What happens during Scan

This is the first step of the update process where the device will query Windows Update for any applicable updates. An update scan automatically occurs in the background once every 22 hours and requires that the device is either actively in use or on standby but plugged in to ensure internet connectivity. In order for the update scan to succeed the device must have internet connectivity. This scan happens automatically, although a user can manually start a scan from the Settings app. If the device was turned off during the last scheduled scan then it will initiate a scan the next time it is plugged in.

#### Best practices for Scan

The two critical pieces for scan to succeed are power and internet connectivity. We suggest that when users end their session with HoloLens they return it to an area where it is plugged in overnight and that it still has internet connectivity in that area.

If your device is having issues scanning for updates please review the [troubleshooting scanning section](#issue---my-device-didnt-find-an-update-when-scanning) and ensure you don't have any hindering configurations.

### 2. Download & Install

#### What happens during Download & Install

Once the device has scanned and found an applicable update, it can begin downloading the update. Like scanning, a user can manually choose to start the download.

#### Best practices for Download & Install

If the best practices for scanning are followed, then the device should be plugged into power and have internet connectivity. These best practices are the same, and after the scan, if an update is found it will start the download.

### 3. Restart

#### What happens during Restart

This is the final stage of the update process, and the device has already found, downloaded and staged the update. The remaining step is a device restart to complete installation and boot into the updated operating system. It needs to restart to start the install process, [which as a benefit of state separation, is an atomic step](security-state-separation-isolation.md#state-separation-benefits). By default, the device won't restart during [active hours](#configure-active-hours). When it is finished the device will boot into the sign-in screen and be finished updating!

#### Best practices for Restart

If the device is left plugged in overnight, it will automatically completely installing the update and restart during the [maintenance window](/windows/win32/taskschd/task-maintenence). Once the download has been installed and staged for a restart internet connectivity isn't a requirement.

Restarting the device is necessary for successfully applying the update but it also breaks into user behavior. HoloLens offers IT administrators the following levels of control over when and how the device should be restarted:

1. Configure different default [active hours](#configure-active-hours). If your devices are used at different times of day, or you'd like to change your active hours so the update process is started at a different time of day.
1. Consider configuring an [update schedule.](#configure-an-update-schedule)
1. Set Deadlines. If you want to ensure that a download update isn't delayed by a user either directly or indirectly, you can set a deadline to force the device to update. Check out [the new deadline policies added in 21H2.](#improved-update-restart-detection-and-notifications)

## Manage updates automatically

### Managing updates by using Windows Update for Business

Windows Holographic for Business can use [Windows Update for Business](/windows/deployment/update/waas-manage-updates-wufb) to manage updates. All HoloLens 2 devices can use Windows Holographic for Business. Make sure that they use Windows Holographic for Business build 10.0.18362.1042 or a later build. If you have HoloLens (1st gen) devices, you have to [upgrade them to Windows Holographic for Business](hololens1-upgrade-enterprise.md) in order to manage their updates.

Windows Update for Business connects HoloLens devices directly to the Windows Update service. By using Windows Update for Business, you can control multiple aspects of the update process&mdash;that is, which devices get which updates at what time. For example, you can roll out updates to a subset of devices for testing, then later roll out updates to the remaining devices. Or, you can define different update schedules for different types of updates.

> [!NOTE]  
> For HoloLens devices, you can automatically manage feature updates (released two times a year) and quality updates (released monthly or as required, including critical security updates). For more information about update types, see [Types of updates managed by Windows Update for Business](/windows/deployment/update/waas-manage-updates-wufb#types-of-updates-managed-by-windows-update-for-business).

You can configure Windows Update for Business settings for HoloLens by using policies in a Mobile Device Management (MDM) solution such as Microsoft Intune.

### Managing Windows Update for Business by using Microsoft Intune

For a detailed discussion about how to use Intune to configure Windows Update for Business, see [Manage Windows 10 software updates in Intune](/intune/protect/windows-update-for-business-configure). For more information about the specific Intune functionality that HoloLens supports, see [Intune update management functions that HoloLens supports](#intune-update-management-functions-that-hololens-supports).

> [!IMPORTANT]  
> Intune provides two policy types for managing updates: *Windows 10 update ring* and *Windows 10 feature update*. The Windows 10 feature update policy type is in public preview at this time and is not supported for HoloLens.
>  
> You can use Windows 10 update ring policies to manage HoloLens 2 updates.

### Configure update policies for HoloLens 2 or HoloLens (1st gen)

This section describes the policies that you can use to manage updates for either HoloLens 2 or HoloLens (1st gen). For more information about the functionality that is available for HoloLens 2, see [Plan and configure update rollouts for HoloLens 2](#plan-and-configure-update-rollouts-for-hololens-2).

[Policy CSP - Update](/windows/client-management/mdm/policy-csp-update) defines the policies that configure Windows Update for Business.

> [!NOTE]  
> For a list of specific policy configuration service providers (CSPs) that are supported by specific editions of HoloLens, see [Policy CSPs supported by HoloLens devices](/windows/client-management/mdm/policy-configuration-service-provider#policy-csps-supported-by-hololens-devices).

#### Configure automatic checks for updates

You can use the **Update/AllowAutoUpdate** policy to manage automatic update behavior, such as scanning, downloading, and installing updates. For more information about the available settings for this policy, see [Update/AllowAutoUpdate](/windows/client-management/mdm/policy-csp-update#update-allowautoupdate).

> [!NOTE]  
> In Microsoft Intune, you can use **Automatic Update Behavior** to change this policy. For more information, see [Manage Windows 10 software updates in Intune](/intune/windows-update-for-business-configure).

#### Configure an update schedule

To configure how and when updates are applied, use the following policies:

- [Update/ScheduledInstallDay](/windows/client-management/mdm/policy-csp-update#update-scheduledinstallday)  
  - Values: **0**–**7** (0 = every day, 1 = Sunday, 7 = Saturday)
  - Default value: **0** (every day)
- [Update/ScheduledInstallTime](/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)
  - Values: 0–23 (0 = midnight, 23 = 11 PM)
  - Default value: 3 AM

#### Configure active hours

Starting with [Windows Holographic, version 20H2](hololens-release-notes-2004.md#windows-holographic-version-20h2) an IT Admin can specify the active hours range for HoloLens 2 devices.

Active hours identify the period of time when you expect the device to be in use. Automatic restarts after an update will occur outside of the active hours. The specified range will be counted from the active hours start time. You can use MDM, as described in [Configuring active hours with MDM](/windows/deployment/update/waas-restart#configuring-active-hours-with-mdm). MDM uses the Update/ActiveHoursStart and Update/ActiveHoursEnd and Update/ActiveHoursMaxRange settings in the Policy CSP to configure active hours.

- [Update/ActiveHoursEnd](/windows/client-management/mdm/policy-csp-update#update-activehoursend) - This value sets the end time. There is a 12-hour maximum from start time.
  - Supported values are 0-23, where 0 is 12 AM, 1 is 1 AM, etc.
  - The default is 17 (5 PM).
- [Update/ActiveHoursMaxRange](/windows/client-management/mdm/policy-csp-update#update-activehoursmaxrange) - This value sets max number of active hours from start time.
  - Supported values are 8-18.
  - The default value is 18 (hours).
- [Update/ActiveHoursStart](/windows/client-management/mdm/policy-csp-update#update-activehoursstart) - This value sets the start time. There is a 12-hour maximum from end time.
  - Supported values are 0-23, where 0 is 12 AM, 1 is 1 AM, etc.
  - The default value is 8 (8 AM).

#### For devices that run Windows 10, version 1607 only

You can use the following update policies to configure devices to get updates from Windows Server Update Service (WSUS), instead of from Windows Update:

- [Update/AllowUpdateService](/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)
- [Update/RequireUpdateApproval](/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)
- [Update/UpdateServiceUrl](/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

#### Improved update restart detection and notifications

- Introduced in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2).

Between active hours and install time policies, it is possible to avoid rebooting HoloLens devices when they are in use. However, it would also delay the adoption of updates if reboots don’t occur to complete the installation of a required update. We’ve now added policies to allow IT to enforce deadlines and required reboots and ensure that the installation of an update is completed in a timely manner. Users can be notified prior the reboot being initiated and they can delay the reboot in accordance with IT policy.

The following update policies were be added:

- [Update/AutoRestartNotificationSchedule](/windows/client-management/mdm/policy-csp-update#update-autorestartnotificationschedule)
- [Update/AutoRestartRequiredNotificationDismissal](/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
- [Update/ConfigureDeadlineForFeatureUpdates](/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)
- [Update/ConfigureDeadlineForQualityUpdates](/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)
- [Update/ConfigureDeadlineGracePeriod](/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)
- [Update/ConfigureDeadlineNoAutoReboot](/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)
- [Update/ScheduleImminentRestartWarning](/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)
- [Update/ScheduleRestartWarning](/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)
- [Update/UpdateNotificationLevel](/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)

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

![Timeline for deploying updates.](./images/hololens-updates-timeline.png)

#### Configure an update deferral policy

A deferral policy specifies the number of days between the date on which an update becomes available and the date on which the update is offered to a device.

You can configure different deferrals for feature updates and quality updates. The following table lists the specific policies to use for each type, and the maximum deferral for each.

|Category |Policy |Maximum deferral |
| --- | --- | --- |
|Feature updates |DeferFeatureUpdatesPeriodInDays |365 days |
|Quality updates |DeferQualityUpdatesPeriodInDays |30 days |

#### Pause Updates via Device

If a user does not have access to MDM they can individually Pause updates for up to 35 days manually on a HoloLens 2 device on build [Windows Holographic, version 2004](hololens-release-notes-2004.md#windows-holographic-version-2004) or later. Users can reach this setting by navigating to **Settings > Update & Security > Advanced options** scroll down to **Pause updates** and select the date until which they will pause updates. Once a user reached the pause limit, the device will need to get new updates before they can pause again.

Starting with [Windows Holographic, version 20H2](hololens-release-notes-2004.md#windows-holographic-version-20h2), this pause updates function can be managed for HoloLens 2 devices:

- [Update/SetDisablePauseUXAccess](/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess).
  - 0 (default) – Enabled
  - 1 – Disabled

#### Intune update management functions that HoloLens supports

You can use the following Intune update management functions to manage updates for HoloLens.

- **Create** and **Assign**: These functions add a Windows 10 update ring to the list of update rings. For more information, see [Create and assign update rings](/mem/intune/protect/windows-update-for-business-configure#create-and-assign-update-rings).

- **Pause**: If you encounter a problem when you deploy a feature or quality update, you can pause the update for 35 days (starting from a specified date). This pause prevents other devices from installing the update until you resolve or mitigate the problem. If you pause a feature update, quality updates are still offered to devices to make sure that they stay secure. When an update type is paused, the Overview pane for that ring displays how many days remain before that update type resumes. After the specified time has passed, the pause automatically expires, and the update process resumes.

  While the update ring is paused, you can select either of the following options:

  - **Extend**: Extend the pause period for an update type for 35 days.
  - **Resume**: Restore updates for that ring to active operation. You can pause the update ring again, if it is necessary.

  > [!NOTE]  
  > The **Uninstall** operation for update rings is not supported for HoloLens 2 devices.

### Delivery Optimization Preview

[Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1) has enabled an early preview for delivery optimization settings to reduce bandwidth consumption for downloads from multiple HoloLens devices. A fuller description of this functionality along with the recommended network configuration is available here: [Delivery Optimization for Windows 10 updates](/windows/deployment/update/waas-delivery-optimization).

The following settings are enabled as part of the management surface and [can be configured from Intune](/mem/intune/configuration/delivery-optimization-settings):

- [DOCacheHost](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-docachehost)
- [DOCacheHostSource](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-docachehostsource)
- [DODelayCacheServerFallbackBackground](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaycacheserverfallbackbackground)
- [DODelayCacheServerFallbackForeground](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaycacheserverfallbackforeground)
- [DODownloadMode](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)
- [DOMaxBackgroundDownloadBandwidth](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxbackgrounddownloadbandwidth)
- [DOMaxForegroundDownloadBandwidth](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxforegrounddownloadbandwidth)
- [DOPercentageMaxBackgroundBandwidth](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)
- [DOPercentageMaxForegroundBandwidth](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth)
- [DOSetHoursToLimitForegroundDownloadBandwidth](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)
- [DOSetHoursToLimitBackgroundDownloadBandwidth](/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth)

A few caveats about this preview offering:

- HoloLens support is limited in this preview to OS updates only.
- Windows Holographic for Business only supports HTTP download modes and downloads from a [Microsoft Connected Cache endpoint](/mem/configmgr/core/plan-design/hierarchy/microsoft-connected-cache); peer-to-peer download modes and group assignments are not supported for HoloLens devices at this time.
- HoloLens does not support deployment or delivery optimization for Windows Server Update Services endpoints.
- Troubleshooting will require either diagnostics on the Connected Cache server or collecting a trace on HoloLens on HoloLens via **Settings** > **Update & Security** >  **Troubleshooting** >  **Windows Update**.

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

#### If WDRT doesn't detect your device

If WDRT doesn't detect your HoloLens device, try restarting your computer. If that doesn't work, select **My device was not detected**, select **Microsoft HoloLens**, and then follow the instructions.

## Troubleshooting updates

### Issue - My device didn't find an update when scanning

If your devices are having issues successfully scanning for updates entirely (verify using a manual scan when you know an update is pending) then check the following configurations.

1. That you if you have a restrictive network in your organization, that you have allowed the [endpoints for Windows Update](hololens-offline.md).
1. Your device has received a [deferral policy](#configure-an-update-deferral-policy),and is already on the latest eligible update as determined by policy.
1. Your device has received a [pause policy](/mem/intune/protect/windows-10-update-rings#pause) which will prevent scans from occurring while the policy is in effect.
1. If your device at Intune uses _Feature Updates for Windows 10_ or _Quality Updates for Windows 10_, please remove devices from being opted in these rings. These are not supported for HoloLens devices.

### Issue - My device has downloaded an update, but won't install it

Many of the [troubleshooting steps for scanning](#issue---my-device-didnt-find-an-update-when-scanning) also apply here. If you've already reviewed those you may have an OS install issue. If this is the case, please [file an issue through feedback hub](hololens-feedback.md) using the **Enterprise Management -> Device category**.

## Related articles

- [HoloLens 2 release notes](hololens-release-notes.md)
- [What is Windows Update for Business?](/windows/deployment/update/waas-manage-updates-wufb)
- [Assign devices to servicing channels for Windows 10 updates](/windows/deployment/update/waas-servicing-channels-windows-10-updates)
- [Manage Windows 10 software updates in Intune](/mem/intune/protect/windows-update-for-business-configure)
