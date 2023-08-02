---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.prod: hololens
ms.sitesec: library
author: lolambean
ms.author: lolab
manager: nazara
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
|[Scratch Spaces are now available](#scratch-spaces-now-available)|Insert notes here. | All| 10.0.22621.xxxx ||[Start Menu gesture settings now controlled via MDM](#start-menu-gesture-settings-in-mdm)|It is now possible to control start menu gesture settings via MDM. | All| 10.0.22621.xxxx |
|[USB Peripherals can now be blocked via MDM policy](#usb-peripherals-now-blocked-via-MDM-policy)|Insert note here. | All| 10.0.22621.xxxx |
|[Domain name suggested during sign-in](#domain-suggested-during-signin)|Insert note here.|All| 10.0.22621.xxxx |
|[Support added for RequireUpdateApproval policy](#support-added-for-requireupdateapproval-policy) | Insert note here. | All | 10.0.22621.xxxx |
|[New policy for Windows Hello Provisioning behavior](#windows-hello-behavior-with-fido2-policy) | This new policy can be used to control Windows Hello provisioning behavior for users signed in with FIDO2 security keys.| All | 10.0.22621.1212 |
|[New policy for Sign-in app launch](#signin-app-launch-policy) | This new policy can be used to control the behavior of the sign-in app when it launches.| All | 10.0.22621.1212 |
|[Hand tracking improvements](#hand-tracking-improvements) | Hand tracking is now more reliable when aiming at the floor. | All | 10.0.22621.1205 |
|[Font and IME improvements](#font-and-ime-improvements) | Several simplified Chinese fonts and the Microsoft Pinyin Input Method Editor (IME) now support GB18030-2022. | All | 10.0.22621.1205 |
|[Support for NFC readers](#support-for-nfc-readers) | Users can now login to their devices using their security badge with an NFC reader. | All | 10.0.22621.1205 |
|[Fixes improvements](#fixes-and-improvements)  | Fixes and improvements for HoloLens. | All   | 10.0.22621.1205 |

### Start menu gesture settings in MDM

### USB peripherals now blocked via MDM policy

### Domain suggested during signin

### Support added for RequireUpdateApproval policy

### Windows Hello behavior with FIDO2 policy

A new policy, EnableWindowsHelloProvisioningForSecurityKeys, has been added to the PassportForWork CSP to control Windows Hello Provisioning behavior for users signed in with FIDO2 security keys. If this policy is enabled on HoloLens 2, the device will start Iris and PIN enrollments after new users sign-in to their devices with FIDO2 security keys. By default, this policy is disabled and new users won’t go through Iris and PIN enrollments if they sign-in with FIDO2 security keys.  The device policy path is:

./Device/Vendor/MSFT/PassportForWork/{TenantId}/Policies/EnableWindowsHelloProvisioningForSecurityKeys

### Signin app launch policy

There is a new MDM policy, PreferLogonAsOtherUser.  This policy controls if the HoloLens Sign-In App will show Other User screen to user when the app starts. When this policy is enabled, users will see the screen to sign in as an "Other user" when the sign-in app launches.  The Device policy path is:

./Device/Vendor/MSFT/Policy/Config/MixedReality/PreferLogonAsOtherUser

### Hand tracking improvements 

Hand tracking system has been improved so that tracking is more reliable when aiming down at objects on the floor.

### Font and IME improvements

This update improves several simplified Chinese fonts and the Microsoft Pinyin Input Method Editor (IME) to support GB18030-2022. You can enter and display characters from conformance level 1 or 2 using the additions to Microsoft Yahei, Simsun, and Dengxian. This update now supports Unicode Extensions E and F in the Simsun Ext-B font. This meets the requirements for level 3.  These improvements are in-line with what has been released to the Windows 11 Build Release Preview Channel.  More details can be found on the [Windows Insiders blog](https://blogs.windows.com/windows-insider/2023/06/20/releasing-windows-11-build-22621-1926-to-the-release-preview-channel/).

### Support for NFC readers

The next Insider Preview flight for HoloLens will include the ability for users to take advantage of NFC Readers.  Using a USB-C NFC reader, the HoloLens 2 device can be integrated with NFC FIDO2 cards as supported by Azure AD. For users in clean room environments, or where ID Badges contain FIDO technology, this can enable a “Tap & PIN” experience for HoloLens Sign on.  This feature enables a faster sign-in experience for users.

#### USB NFC reader support

USB-CCID (Chip Card Interface Device) compatible NFC FIDO2 readers with USB base class ‘0B’ and subclass ‘00’ are supported. Please refer to [Microsoft Class Drivers for USB CCID Smart Cards](/previous-versions/windows/hardware/design/dn653571(v=vs.85)) for details on Microsoft class driver for USB CCID devices.  To determine if your NFC reader is compatible with HoloLens, you may either refer to the documentation provided by the reader's manufacturer, or use the Device Manager on your PC, as follows:

1.	Plug in the USB NFC reader to a Windows PC.
2.	In Device Manager, locate the reader device and right click on it and select Properties.
3.	In Details tab, select "Compatible Ids" properties and check if "USB\Class_0b&SubClass_00" is in the list.


![smartcard reader properties](media/hololens-insider/smartcard-reader-properties.png)

Whether you sign into a device you have used before or a new device, please follow these steps to sign in with an NFC reader:

1.	From the “Other User” screen, enter the FIDO Key / Tap the NFC Key against the reader.
2.	Enter the FIDO PIN.
3.	Press the button on the FIDO Key / Tap the NFC Key against the reader again.
4.	The Device logs in.

      a.	Note:  if the user is new to the device, the Single Biometric Disclosure Screen will be displayed.
5.	Start Menu then appears.

### Fixes and improvements

- Fixed an issue where specific pages were not showing / hiding correctly in PageVisibility MDM policy (Windows 11 builds only).
- Fixed an issue where swipe to type on the virtual keyboard was not working correctly (Windows 11 builds only).
- Fixed an issue where the "Reset" button was not showing in the case of an Autopilot failure that occurred before reading the ESP configuration.
- Minor updates were made to the virtual keyboard, including optimization of the keyboard suggestions that are presented to users and improved audio feedback while typing.
- Prior to this update, users were often unclear when dictation from the virtual keyboard was available.  Users now see a spinning icon while dictation is being initiated and the dictation tip to begin speaking is only displayed once dictation is available.

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






