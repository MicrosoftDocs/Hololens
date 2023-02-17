---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: millerevan
manager: lolab
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
>
> Only devices in the [Dev channel](#start-receiving-insider-builds) will receive these Insider build features.

> [!IMPORTANT]
>
> This next update is on a newer codebase than what currently is available generally. After you update a device to this build, your device won't update to our monthly releases until those releases catch up to the newer codebase. If necessary, you can still flash your device to go back to the general release.

| Feature   | Description  | User or scenario | Available in build |
|-----------|--------------|------------------|---|
| [Reboot CSP enabled and related changes](#reboot-csp-enabled-and-related-changes-in-intune) | Hololens now supports weekly scheduled reboots and other options. | IT Admin | 10.0.22621.1051 |
| [Update available notification](#update-available-notification) | Shows user that update is available when looking at the start menu. | End User | 10.0.22621.1051 |
| [Autopilot reset experience](#autopilot-reset-experience) | Improvements in Autopilot reset experience to enable users to reset HoloLens 2 and restart Autopilot without requiring manual flashing.| IT Admin  | 10.0.22621.1008 |
| [Biometrics disclosure screen](#biometrics-disclosure-screen) | Displays information to all new users on what biometrics the device uses. | All | 10.0.22621.1008 |
| [Remove users on device](#remove-users-on-a-device) | New policies to manage when to remove users from the device to prevent hitting the maximum limit. | IT Admin  | 10.0.22621.1008 |
| [Fixes improvements](#fixes-and-improvements)  | Fixes and improvements for HoloLens. | All   | 10.0.22621.1006 |

✔️ If you need to delete users from your HoloLens automatically, then see [Remove users on a device](#remove-users-on-a-device).

✔️ If you'd like to set a policy for your HoloLens devices to automatically [reboot on a schedule](#reboot-csp-enabled-and-related-changes-in-intune), then read on.

### Reboot CSP enabled and related changes in Intune

In addition to supporting scheduled single daily reboots, [Reboot CSP](/windows/client-management/mdm/reboot-csp) now supports scheduled weekly reboots.

Create a custom OMA-URI device configuration profile as follows and apply it to a HoloLens device group:

 :::image type="content" alt-text ="This screenshot shows using OMA URI to configure the weekly reboot." source="./images/weekly-reboot-oma-uri.png":::

> [!NOTE]
>
> Setting Reboot CSP through the “Settings catalog” will be supported soon. Until then, use OMA-URI.

1. For the OMA-URI field, specify any of these three options:

   - `./Device/Vendor/MSFT/Reboot/Schedule/Single`
   - `./Device/Vendor/MSFT/Reboot/Schedule/DailyRecurrent`
   - `./Device/Vendor/MSFT/Reboot/Schedule/WeeklyRecurrent`

   > [!NOTE]
   >
   > Setting both DailyRecurrent and WeeklyRecurrent configurations on the same device is not supported.

1. For the **data type** field, choose **String**.

1. For the **value** field, enter a date value for a starting date and time, such as *2023-01-06T10:35:00* to set DailyRecurrent reboots starting on the given date and *two minutes after* the set starting time daily. Similarly, setting WeeklyRecurrent reboots starting at the given date and *two minutes after* the starting time every seven days. For example, if you specify 10:00, the reboot will occur at 10:02.

   > [!NOTE]
   >
   > The actual time of recurrent schedule reboots is about 2 minutes after the configured time. This delay is expected and intentional to preserve the operations and communication states.

### Update available notification

Having up-to-date devices is important. A previous feature improvement lets you see when updates are ready to *install*. With this new update, your device displays when an update is available to *download*. As with desktop devices, when an update is available, your Hololens displays a blue update circle icon. This icon is near your user icon.

1. Select your user icon. The user context menu will open.
1. Select **Download update** to launch the Settings app updates page that shows the update available to download.

   :::image type="content" alt-text="This screenshot shows the start menu context for OS updates." source="images/hl2-update-context-menu-crop-6in.png":::

### Autopilot reset experience

We've added a new setting to improve the Autopilot reset experience if Hololens 2 fails in certain installation scenarios. This setting lets users begin the Autopilot experience again without requiring a manual flash of HoloLens 2 devices. In the ESP configuration, set **Allow users to reset device if installation error occurs** to **Yes** and the device will display a "Reset device" button. If the user selects **Reset device**, after a delay of about 1 minute, HoloLens 2 will reset the operating system and OOBE experience.

### Biometrics disclosure screen

We've changed one of our OOBE screens before the device calibrates to show information on device usage for head, hand, and eye movements. Devices configured to skip calibration won't skip this biometrics disclosure screen, so all new users on a device will see device biometrics usage.

:::image type="content" alt-text="This screenshot shows the Biometrics OOBE window." source="images/biometrics-oobe-notification.jpg":::

### Remove users on a device

Organizations with scaled deployments of HoloLens 2 devices might encounter the 64-user limit per device that prevents adding users. To address this situation, we've added controls that delete the least recent users from the device at controlled intervals, which is a feature you might have used on the Desktop version. Deleting users in a controlled way is useful for other reasons, too. Removing the least recently used accounts increases security and speeds up the process of iris scanning on the sign-in screen because fewer users reduce the number of comparisons. The three methods to control when to remove least recent users are as follows:

- On a regular schedule determined by you
- At storage threshold percentage determined by you
- When you add more than your custom maximum number of users

Here's how to get started:

1. Set the boolean value for **UserProfileManagement/EnableProfileManager** to **true**.

1. Set the numerical **UserProfileManagement/ProfileInactivityThreshold**, which is the number of days until a user is deleted. The default value is **30**.

1. Set **UserProfileManagement/StorageCapacityStartDeletion**, a numerical value representing the percentage of free space left when the device begins deleting the least recent users. The Default value is **25%**.

1. Pair **UserProfileManagement/StorageCapacityStartDeletion** with **StorageCapacityStopDeletion** to determine when, based on the free storage percent, to stop deleting profiles.

1. Turn on the deletion policy **UserProfileManagement/DeletionPolicy**, and set it to **2**, which deletes both threshold and inactive users.

   If the **UserProfileManagement/DeletionPolicy** is on, when the device reaches the maximum number of users and is trying to add another, the device deletes the oldest user automatically.

To learn more about these policies, visit [AccountManagement CSP](/windows/client-management/mdm/accountmanagement-csp).

### Fixes and improvements

- Use EnterpriseModernAppManagement CSP to issue an app uninstall command in the device context.
- Uninstall apps in the device context.

## Start receiving Insider builds

> [!TIP]
>
> Once you enroll a device into Insider builds, we strongly recommend that your organization keeps a set of test devices enrolled, too. With a set of test devices, your organization can validate builds more easily as they come out. Timely and efficient validation creates an easier experience and helps if your normal production devices are blocked from Insider builds.

> [!NOTE]
>
> Windows Insider is moving to Channels. The **Fast** ring will become the **Dev Channel**, the **Slow** ring will become the **Beta Channel**, and the **Release Preview** ring will become the **Release Preview Channel**. Here’s how that mapping looks:
>
> :::image type="content" alt-text="Screenshot of the Windows Insider Channels explanation." source="./images/WindowsInsiderChannels.png":::
>
> For more information, see [Introducing Windows Insider Channels](https://blogs.windows.com/windowsexperience/2020/06/15/introducing-windows-insider-channels) on Windows Blogs.

### Prerequisites

If you haven't already, enable telemetry, get the latest build, and then access the Windows Insider Program.

1. Enable telemetry. Normally optional, telemetry is required to enroll your device in Insider builds.

   1. In the **Settings app** > **Privacy** > **Diagnostics & feedback** > **Optional diagnostics data**.

   1. **Enable** telemetry.

1. Get the latest build. Reboot your device using one of two methods:
     - Use the voice command "Reboot device."
     - Choose the restart button in Settings.

### Access the Windows Insider Program

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
