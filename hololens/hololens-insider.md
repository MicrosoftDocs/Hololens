---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.custom:
- CI 111456
- CSSTroubleshooting
audience: ITPro
ms.date: 2/22/2022
ms.localizationpriority:
ms.reviewer: 
manager: ranjibb
appliesto:
- HoloLens 2
---

# Insider preview for Microsoft HoloLens

Welcome to the latest Insider Preview builds for HoloLens! It's simple to [get started](hololens-insider.md#start-receiving-insider-builds) and provide valuable feedback for our next major operating system update for HoloLens.

## Windows Insider Release Notes

What's new and on the horizon for HoloLens? Check out these new updates coming to HoloLens!

| Feature | Description | Target Audience | Available in Build |
|---------|-------------|-----------------|--------------------|
| [Color-blind mode](#color-blind-mode)        | Applies filters that adjust the displayed colors for Color-blind users.      | End users        | 20348.1463       |
| [Single app kiosk policy for launching other apps](#single-app-kiosk-policy-for-launching-other-apps) | Allows for app launch of secondary app. | IT Admins | 20348.1470 |
| [Power and Thermal SDK for apps](#power-and-thermal-sdk-for-apps) | Allows apps to adapt to reduce the thermal impact. | Developers | 20348.1479 |

Looking for a new feature but don't see it? Check out the [release notes](hololens-release-notes.md) as many of our new features have been released as part of the main builds. The following features have recently moved to the release notes since their release:

- [Moving Platform Mode Settings](hololens-release-notes.md#moving-platform-mode-settings)
- [Moving Platform Mode MDM policies](hololens-release-notes.md#moving-platform-mode-mdm-policies)
- [Start gestures settings](hololens-release-notes.md#start-gestures-settings)

### IT Admin Feature Checklist - Insider

✔️ If you'd like to allow launching another app from a single app Kiosk (such as settings) check out the new [single app kiosk policy for launching other apps](#single-app-kiosk-policy-for-launching-other-apps).

### Color-blind mode

Added in Insider build 20348.1463

Color-blind mode is useful a great feature that makes HoloLens more accessible. The new color-blind mode can be found in the Settings app under **Settings** -> **Ease of Access** -> **Color filters**. Several new filters are available. Here's a visual example of some of the available filters.

| Off | Grey scale | Tritanopia |
|-----|-----------|------------|
| ![Color filter off](images/colorblind-off.png)   | ![Color filter grey scale](images/colorblind-greyscale.png)         | ![Color filter tritanopia](images/colorblind-tritanopia.png)          |

### Single app kiosk policy for launching other apps

Introduced a new MDM policy MixedReality\AllowLaunchUriInSingleAppKiosk. This can be enabled to allow for other apps to be launched with in a single app Kiosk, which may be useful, for example,  if you want to launch the Settings app to calibrate your device or change your Wi-fi.

By default, launching applications via [Launcher API (Launcher Class (Windows.System) - Windows UWP applications)](/uwp/api/Windows.System.Launcher?view=winrt-22000&preserve-view=true) is disabled in single app kiosk mode. To enable applications to launch in single app kiosk mode on HoloLens devices, set the policy value to true.

The OMA-URI of new policy: `./Device/Vendor/MSFT/Policy/Config/MixedReality/AllowLaunchUriInSingleAppKiosk`

- Bool value

### Power and Thermal SDK for apps

When the HoloLens 2 is running in warm environments or with heavy performance requirements (CPU/GPU usage, peripheral usage, etc.), it might get hot enough that it takes actions automatically to keep itself from overheating. If your app demands high peripheral performance, consider using the [PowerThermalNotification Software Development Kit (SDK)](/windows/mixed-reality/develop/unity/managing-power-and-thermals) to subscribe to notification events and implement your own custom actions.

Using this new SDK can allow the device to operate longer in situations where the app may be closed by the system.

### Fixes and improvements

- Improvements to Moving Platform Mode when detecting the down direction.
- Fixed an issue around update dialogs.
- Updated inbox Microsoft Edge browser version.
- Fixed an issue where toggling optional diagnostic data didn't persist the chosen setting in telemetry settings page after a reboot.
- Fixed an issue where MDM enrollment was stuck when applied with runtime provisioning for local accounts.
- Fixed an issue where kiosk mode wasn’t falling back to global kiosk (if configured) on encountering failures for AAD group-based kiosk configuration.
- Fixed an issue where graphics memory is leaked during some camera usage scenarios.

### Known Issue - Some users may encounter an update failure with Insider build 20346.1466

If a user has taken an update to the Insider flight, 20346.1466, and it doesn’t appear to be finishing the boot, a clean reflash may be required to move forward again. To see if you’ve encountered this:

1. Reboot – Hold down the power until the LED’s step down.
1. Power up.
1. Confirm you see the Windows flag at the beginning of the boot and it goes black shortly after that.
1. Connect your HoloLens2 to your PC with USB and run Advanced Recovery companion.
1. Select the HoloLens.
1. If the version says you’re running the 20346.1466 build, you likely hit this issue.

#### Who does this tend to affect

Users who have been using their device without flashing it since [Windows Holographic, version 2004](hololens-release-notes-2004.md#windows-holographic-version-2004).

#### Users who are typically unaffected

Users who have flashed their device, or unboxed their device, and started using it since [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1).

#### Workaround

- [Reflash your device.](hololens-recovery.md#clean-reflash-the-device)

## Start receiving Insider builds

> [!NOTE]
> If you haven’t updated recently, please reboot your device to update state and get the latest build.
>
> - The “Reboot device” voice command works well.
> - You can also choose the restart button in Settings/Windows Insider Program.
>
> We had a bug on the back-end that you may have encountered and this will get you back on track.

On a HoloLens 2 device go to **Settings** > **Update & Security** > **Windows Insider Program** and select **Get started**. Link the account you used to register as a Windows Insider.

> [!NOTE]
> In order to enroll your device in Insider builds, you'll need to enable optional telemetry. If you have not done this already, open the Settings app and select **Privacy** > **Diagnostics & feedback** and then select **Optional diagnostics data**.

Windows insider is now moving to Channels. The **Fast** ring will become the **Dev Channel**, the **Slow** ring will become the **Beta Channel**, and the **Release Preview** ring will become the **Release Preview Channel**. Here’s what that mapping looks like:

![Windows Insider Channels explanation.](images/WindowsInsiderChannels.png)

For more information, see [Introducing Windows Insider Channels](https://blogs.windows.com/windowsexperience/2020/06/15/introducing-windows-insider-channels) on Windows Blogs.
Then, select **Active development of Windows**, choose whether you'd like to receive **Dev Channel** or **Beta Channel** builds, and review the program terms.
Select **Confirm > Restart Now** to finish up. After your device has rebooted, go to **Settings > Update & Security > Check for updates** to get the latest build.

### Update error 0x80070490 work-around

If you encounter an update error 0x80070490 when updating on the Dev or Beta channel, try the following short-term work-around. It involves moving your insider channel, picking up the update and then moving your Insider channel back.

#### Stage one - Release Preview

1. Settings, Update & Security, Windows Insider Program, select **Release Preview Channel**.

2. Settings, Update & Security, Windows Update, **Check for updates**. After the update, continue on to Stage two.

#### Stage two - Dev Channel

1. Settings, Update & Security, Windows Insider Program, select **Dev Channel**.

2. Settings, Update & Security, Windows Update, **Check for updates**.

## FFU download and flash directions

To test with a flight signed ffu, you first have to flight unlock your device prior to flashing the flight signed ffu.

1. On PC:
    1. Download ffu to your PC from [https://aka.ms/hololenspreviewdownload](https://aka.ms/hololenspreviewdownload).

    1. Install ARC (Advanced Recovery Companion) from the Microsoft Store: [https://www.microsoft.com/store/productId/9P74Z35SFRS8](https://www.microsoft.com/store/productId/9P74Z35SFRS8).

1. On HoloLens - Flight Unlock: Open **Settings** > **Update & Security** > **Windows Insider Program** then sign up, reboot device.

1. Flash FFU - Now you can flash the flight signed FFU using ARC.

### Provide feedback and report issues

Please use [the Feedback Hub app](hololens-feedback.md) on your HoloLens to provide feedback and report issues. Using Feedback Hub ensures that all necessary diagnostics information is included to help our engineers quickly debug and resolve the problem.  Issues with the Chinese and Japanese version of HoloLens should be reported the same way.

> [!NOTE]
> Be sure to accept the prompt that asks whether you'd like Feedback Hub to access your Documents folder (select **Yes** when prompted).

## Note for developers

You are welcome and encouraged to try developing your applications using Insider builds of HoloLens.  Check out the [HoloLens Developer Documentation](https://developer.microsoft.com/windows/mixed-reality/development) to get started. Those same instructions work with Insider builds of HoloLens.  You can use the same builds of Unity and Visual Studio that you're already using for HoloLens development.

## Stop receiving Insider builds

If you no longer want to receive Insider builds of Windows Holographic, you can opt out when your HoloLens is running a production build, or you can [recover your device](hololens-recovery.md) using the Advanced Recovery Companion to recover your device to a non-Insider version of Windows Holographic.

> [!CAUTION]
> There is a known issue in which users who un-enroll from Insider Preview builds after manually reinstalling a fresh preview build would experience a blue screen. Afterwards they must manually recover their device. For full details on if you would be impacted or not, please view more on this [Known Issue](hololens-troubleshooting.md#blue-screen-after-unenrolling-from-insider-preview-on-a-device-flashed-with-an-insider-build).

To verify that your HoloLens is running a production build:

1. Go to **Settings > System > About**, and find the build number.

1. [See the release notes for production build numbers](hololens-release-notes.md).

To opt out of Insider builds:

1. On a HoloLens running a production build, go to **Settings > Update & Security > Windows Insider Program**, and select **Stop Insider builds**.

1. Follow the instructions to opt out your device.
