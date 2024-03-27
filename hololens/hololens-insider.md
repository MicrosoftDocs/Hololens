---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.service: hololens
ms.sitesec: library
ms.reviewer: bryanth
ms.topic: article
ms.custom:
- CI 111456
- CSSTroubleshooting
audience: ITPro
ms.date: 2/1/2023
ms.localizationpriority: high
appliesto:
- HoloLens 2
---

# Insider preview for Microsoft HoloLens

Welcome to the latest Insider Preview builds for HoloLens! [Get started](#start-receiving-insider-builds) and provide valuable feedback on HoloLens for our next major operating system update.

> [!TIP]
>
> Organizations that have moved, or are moving toward, production deployment at scale should keep a subset of test devices on Insider builds to validate new features and builds.

## Windows Insider release notes

Looking for a new feature but don't see it? We released many new features as part of the main builds. Check out the [release notes](hololens-release-notes.md) if you think a feature might be missing.

> [!NOTE]
> Only devices in the [Dev channel](#start-receiving-insider-builds) receive these Insider build features.

> [!IMPORTANT]
>
> This next update is on a newer codebase than what currently is available in the main builds. After you update a device to this build, your device won't update to our monthly releases until those releases catch up to the newer codebase. If necessary, you can still flash your device to go back to the general release.

| Feature   | Description  | User or scenario | Available in build |
|-----------|--------------|---|---|
|[Shared Microsoft Entra accounts](#shared-microsoft-entra-accounts)|Shared Microsoft Entra (formerly Azure Active Directory) accounts on HoloLens are regular Microsoft Entra user accounts that can sign-in to the HoloLens without requiring any credentials. | IT Admin | 10.0.22621.1303|
|[Policy to enable auto unlock](#policy-to-enable-auto-unlock)|Policy to control whether a user is prompted for credentials when returning to the device in suspended state. | IT Admin | 10.0.22621.1303|
|[Collect and view network connectivity report](#collect-and-view-network-connectivity-report)|Network connectivity report is added to Offline Diagnostics to help users investigate network connectivity issues on HoloLens 2 devices. | All | 10.0.22621.1303|
|[Enforce time sync during OOBE](#enforce-time-sync-during-oobe)| When the HoloLens connects to Wi-Fi, the device attempts to sync with the time server. | All | 10.0.22621.1303|
|[Improve Intune app update experience](#improve-intune-app-update-experience)|The Intune LOB App update waits for App exit instead of forcing App shutdown. | All | 10.0.22621.1296|
|[Update to eye tracking calibration](#update-to-eye-tracking-calibration)|The option to perform eye tracking calibration is shown on the device even if it has been deployed via Autopilot. | All | 10.0.22621.1296|
|[Policies to set device standby action](#policies-to-set-device-standby-action)|Policies allow the admin to execute supported actions in modern standby. | IT Admin | 10.0.22621.1286|
|[Fixes and improvements](#fixes-and-improvements)  | Additional fixes and improvements for HoloLens. | All   | 10.0.22621.1205 |

### Shared Microsoft Entra accounts

Using a shared Microsoft Entra account on your HoloLens results in the quickest login experience, since it does not require any credentials. This setup is ideal for scenarios where the following conditions are true:

- Multiple people share the same set of HoloLens devices.
- Access to Microsoft Entra resources, such as Dynamics 365 Guides content, is required.
- Tracking who has used the device isn't required.

More details, including specific steps on how to configure these accounts, can be found in the [Shared Microsoft Entra accounts in HoloLens](shared-aad-accounts.md) article.

> [!TIP]
> **Validation Tip:**
> Try this in your shared environments, utilizing your apps, to ensure that shared Microsoft Entra accounts work without any credentials.

### Improve Intune app update experience

The Intune LOB App update does not enforce App shutdown if the App is still running on the device. Instead, the new version of the LOB App is installed and replaces the old App, once the old App is fully exited via user action, sign out or device reboot. 

Refer to [Consistent LOB App deployment and update](/hololens/hololens-best-practices-experiences#consistent-lob-app-deployment-and-update) for best practices on getting a consistent LOB App update experience for HoloLens devices.

> [!TIP]
> **Validation Tip:**
> Try this in your own environment and utilizing your own app to ensure that your app doesn't shut down when an update is waiting to load.

### Policy to enable auto-unlock

New policy to enable auto unlock [MixedReality/AutoUnlock](/windows/client-management/mdm/policy-csp-mixedreality#autounlock). When enabled, this policy allows a signed-in user to resume using the device without having to enter credentials. 

> [!TIP]
> **Validation Tip:**
> Try to modify this policy and ensure that auto unlock works in your specific environments and use cases.

### Collect and view network connectivity report

Network connectivity report is added to Offline Diagnostics to help users investigate network connectivity issues on HoloLens 2 devices. After user triggers Offline Diagnostics, device IP addresses, Wi-Fi information, proxy settings and device’s connectivity to known cloud service endpoints are collected.

The report file NetworkConnectivityReport.txt will be included in the diagnostics ZIP file under Documents folder. Users can also view the report on device through Settings > Update & Security > Troubleshoot > View network connectivity report.

> [!TIP]
> **Validation Tip:**
> If you use various network configurations, ensure it works with each configuration.

### Enforce time sync during OOBE

During OOBE, the HoloLens device attempts to sync the device time with the time server after the device has connected to Wi-Fi.

> [!TIP]
> **Validation Tip:**
> This will help you if you've flashed the build and then don't touch your device for a long time.

### Update to eye tracking calibration

The option to perform eye tracking calibration is now shown on the device even if it has been deployed via Autopilot. Customers still have the option to disable this behavior via the existing [MixedReality/SkipCalibrationDuringSetup](/windows/client-management/mdm/policy-csp-mixedreality#skipcalibrationduringsetup) policy.

Any user on the device can still choose to run eye calibration at any time to improve their experience.

> [!TIP]
> **Validation Tip:**
> Try this on a shared device and ensure that eye tracking calibration occurs.

### Policies to set device standby action

[MixedReality/ConfigureDeviceStandbyAction](/windows/client-management/mdm/policy-csp-mixedreality#configuredevicestandbyaction) and [MixedReality/ConfigureDeviceStandbyActionTimeout](/windows/client-management/mdm/policy-csp-mixedreality#configuredevicestandbyactiontimeout) policies enable configuring HoloLens 2 to execute certain action, when device is in modern standby after certain period of time. See policy documentation for supported actions.

> [!TIP]
> **Validation Tip:**
> Modify these settings and ensure their functionality in your usage models and environments.

### Fixes and improvements

- Fixed an issue where the user picture displayed does not match the selected user on the sign in screen if [MixedReality/PreferLogonAsOtherUser](/windows/client-management/mdm/policy-csp-mixedreality?branch=main#preferlogonasotheruser) policy is enabled.

- Fixed an issue where the user list cannot be dismissed by clicking on the "Add User" or the "Other User" buttons on the sign in screen if [MixedReality/PreferLogonAsOtherUser](/windows/client-management/mdm/policy-csp-mixedreality?branch=main#preferlogonasotheruser) policy is enabled.

- Improved error handling when the device has reached the max number of supported users on device. See [Remove users on a device](https://aka.ms/hlmaxusers) for recommendations if your device is used by more than 63 Microsoft Entra accounts.

- Improved error handling when the wrong user credentials are supplied when using web sign in.

- Fixed an issue in Device Portal that would sometimes prevent the export of the spatial mapping database.

## Start receiving Insider builds

This section explains the steps to prepare devices and then the steps to receive Insider builds.
> [!TIP]
>
> Once you enroll a device into Insider builds, we strongly recommend that your organization keeps a set of test devices enrolled, too. With a set of test devices, your organization can validate builds more easily as they come out. Timely and efficient validation creates an easier experience and helps if your normal production devices are blocked from Insider builds.

> [!NOTE]
>
> Windows Insider is moving to Channels. The **Fast** ring will become the **Dev Channel**, the **Slow** ring will become the **Beta Channel**, and the **Release Preview** ring will become the **Release Preview Channel**. Here’s how that mapping looks:
>
> :::image type="content" alt-text="Screenshot of the Windows Insider Channels explanation." source="./images/WindowsInsiderChannels.png":::
>
> For more information, see [Introducing Windows Insider Channels](https://blogs.windows.com/windowsexperience/2020/06/15/introducing-windows-insider-channels) on[ Windows Blogs](https://blogs.windows.com/).

### Prerequisites

These steps explain what to do before you sign up for Insider builds. 

1. Enable telemetry. Normally optional, telemetry is required to enroll your device in Insider builds.

   1. In the **Settings app** > **Privacy** > **Diagnostics & feedback** > **Optional diagnostics data**.

   1. **Enable** telemetry.

1. Get the latest build. Reboot your device using one of two methods:
     - Use the voice command "Reboot device."
     - Choose the restart button in Settings.

### Access the Windows Insider Program and check for updates

1. On a HoloLens 2 device, go to **Settings** > **Update & Security** > **Windows Insider Program** > **Get started**.

1. Link to the account you used to register as a Windows Insider.

1. Select **Active development of Windows**.

1. Choose whether you'd like to receive **Dev Channel** or **Beta Channel** builds.

1. Review and accept the program terms.

1. Select **Confirm** > **Restart Now**. Your device will reboot.

1. Go to **Settings** > **Update & Security** > **Check for updates** to get the latest build.

### Update error 0x80070490 workaround

If you encounter update error 0x80070490 when updating on the Dev or Beta channel, try the following short-term workaround. It involves moving your Insider channel, picking up the update, and then moving your Insider channel back.

#### Stage one - Release Preview

1. Select **Settings** > **Update & Security** > **Windows Insider Program** > **Release Preview Channel**.

1. Select **Settings** > **Update & Security** > **Windows Update** > **Check for updates**.

1. Accept any available update. After the update, continue to Stage two.

#### Stage two - Dev Channel

1. Select **Settings** > **Update & Security** > **Windows Insider Program** > **Dev Channel**.

1. Select **Settings** > **Update & Security** > **Windows Update** > **Check for updates**.

1. Accept any available update.

## FFU download and flash directions

1. To test with a flight signed `.ffu`, flight unlock your device prior to flashing the flight signed FFU:

   - On a PC:
      1. Download `.ffu` to your PC from [https://aka.ms/hololenspreviewdownload](https://aka.ms/hololenspreviewdownload).
      1. Install [ARC (Advanced Recovery Companion) from the Microsoft Store](https://www.microsoft.com/store/productId/9P74Z35SFRS8): [https://www.microsoft.com/store/productId/9P74Z35SFRS8](https://www.microsoft.com/store/productId/9P74Z35SFRS8).

   - On HoloLens:
      1. Open **Settings** > **Update & Security** > **Windows Insider Program**.
      1. Sign up.
      1. Reboot the device.

1. Flash FFU. Now you can flash the flight signed FFU using ARC.

## Provide feedback and report issues

Use [the Feedback Hub app](hololens-feedback.md) on your HoloLens to provide feedback and report issues. Feedback Hub helps you include the necessary diagnostics information to help our engineers quickly debug and resolve any problem. Report issues with the Chinese and Japanese versions of HoloLens the same way.

> [!NOTE]
>
> Be sure to select **Yes** when a prompt asks whether you'd like Feedback Hub to access your documents folder.

## Note for developers

You're welcome and encouraged to try developing your applications using Insider builds of HoloLens. Check out the [HoloLens Developer Documentation](https://developer.microsoft.com/windows/mixed-reality/development) to get started. Those instructions also work with Insider builds for HoloLens. Use the same builds for Unity and Visual Studio that you're already using for HoloLens development.

## Stop receiving Insider builds

If you no longer want to receive Insider builds of Windows Holographic, you have two options:

- Opt out on a HoloLens running a production build:
   1. Go to **Settings** > **Update & Security** > **Windows Insider Program** > **Stop Insider builds**.
   1. Follow the instructions to opt out your device.

- Use the ARC to [recover your device](hololens-recovery.md) to a non-Insider version of Windows Holographic.

> [!CAUTION]
>
> A known issue causes users who un-enroll from the Windows Insider program, and then manually install a fresh Insider preview build, to experience a blue screen. Afterward, the user must recover the device manually. Learn more about this [Known Issue](hololens-troubleshooting.md#blue-screen-after-unenrolling-from-insider-preview-on-a-device-flashed-with-an-insider-build).
>
> To verify that your HoloLens is running a production build:
>
> 1. Locate the build number through **Settings** > **System** > **About**.
> 1. [Check the build number against the release notes for production build numbers](hololens-release-notes.md).
