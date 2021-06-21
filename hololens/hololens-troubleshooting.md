---
title: HoloLens Device Troubleshooting
description: Stay up to date on the most common solutions to HoloLens device issues and troubleshooting techniques.
author: mattzmsft
ms.author: mazeller
ms.date: 12/02/2019
ms.prod: hololens
ms.topic: article
audience: HoloLens
ms.localizationpriority: medium
manager: jarrettr
ms.custom: 
- CI 111456
- CSSTroubleshooting
keywords: issues, bug, troubleshoot, fix, help, support, HoloLens, emulator
---

# Device Troubleshooting

This article describes how to resolve several common HoloLens issues.

>[!IMPORTANT]
> Before you start any troubleshooting procedure, make sure that your device is charged to **20 to 40 percent** of battery capacity, if possible. The [battery indicator lights](hololens2-setup.md#lights-that-indicate-the-battery-level) located under the power button are a quick way to verify the battery capacity without logging into the device.

If the device can't boot to the startup menu, note the LED appearance and device enumeration on the host PC. If the state of the device doesn't match any of the states listed in the troubleshooting guide, perform the [hard reset procedure](hololens-recovery.md#hard-reset-procedure) with the device connected to the power supply, not to your host PC. 

<a id="list"></a>
- [HoloLens is unresponsive or won't start](#holoLens-is-unresponsive-or-won't-start)
- [Voice commands are not working](#voice-commands-are-not-working)
- [Hand input is not working](#hand-input-is-not-working)
- ["Low Disk Space" error](#"low-disk-space"-error)
- [Calibration Fails](#calibration-fails)
- [Auto-login asks for log-in](#auto-login-asks-for-log-in)
- [Microsoft Edge fails to launch](#microsoft-edge-fails-to-launch)
- [Keyboard does not switch to special characters](#keyboard-does-not-switch-to-special-characters)
- [Bluetooth devices are not pairing](#bluetooth-devices-are-not-pairing)
- [Devices that are listed as available in Settings don't work](#devices-that-are-listed-as-available-in-settings-don't-work)
- [Blue screen after unenrolling from Insider preview on a device flashed with an Insider build](#blue-screen-after-unenrolling-from-insider-preview-on-a-device-flashed-with-an-insider-build)
- [Can't connect to Wi-Fi](#can't-connect-to-wi-Fi)
- [Can't sign in because my HoloLens was previously set up for someone else](#can't-sign-in-because-my-HoloLens-was-previously-set-up-for-someone-else)
- [The HoloLens emulator isn't working](#the-holoLens-emulator-isn't-working)

## HoloLens is unresponsive or won't start

If your HoloLens won't start:

- If the LEDs next to the power button don't light up, or only one LED briefly blinks, you may need to [charge your HoloLens.](hololens2-charging.md#charge-the-device)
- If the LEDs light up when you press the power button but you can't see anything on the displays, [preform a hard reset of the device](hololens-recovery.md#hard-reset-procedure).

If your HoloLens becomes frozen or unresponsive:

- Turn off your HoloLens by pressing the power button until all five of the LEDs turn themselves off, or for 15 seconds if the LEDs are unresponsive. To start your HoloLens, press the power button again.

If these steps don't work, you can try [recovering your HoloLens 2 device](hololens-recovery.md) or [HoloLens (1st gen) device.](hololens1-recovery.md)

[Back to list](#list)

## Voice commands are not working

If Cortana isn't responding to your voice commands, make sure Cortana is turned on. On the All apps list, select **Cortana** > **Menu** > **Notebook** > **Settings** to make changes. To learn more about what you can say, see [Use your voice with HoloLens](hololens-cortana.md).

On HoloLens (1st gen), built-in speech recognition is not configurable. It is always turned on. On HoloLens 2, you can choose whether to turn on both speech recognition and Cortana during device setup.

If your HoloLens 2 is not responding to your voice, make sure Speech recognition is turned on. Go to **Start** > **Settings** > **Privacy** > **Speech** and turn on **Speech recognition**.

[Back to list](#list)

## Hand input is not working

To ensure that HoloLens can see your hands, you need to keep them in the gesture frame.  The Mixed Reality Home provides feedback that lets you know when your hands are tracked.  The feedback is different on different versions of HoloLens:
- On HoloLens (1st gen), the gaze cursor changes from a dot to a ring
- On HoloLens 2, a fingertip cursor appears when your hand is close to a slate, and a hand ray appears when slates are further away

Many immersive apps follow input patterns that are similar to Mixed Reality Home.  Learn more about using hand input on [HoloLens (1st gen)](hololens1-basic-usage.md#use-hololens-with-your-hands) and [HoloLens 2](hololens2-basic-usage.md#the-hand-tracking-frame).

If you are wearing gloves, note that some types of gloves do not work with hand tracking.  A common example is black rubber gloves, which tend to absorb infrared light and are not picked up by the depth camera.  If your work involves rubber gloves, we recommend trying a lighter color such as blue or gray.  Another example is large baggy gloves, which tend to obscure the shape of your hand. We recommend using gloves that are as form-fitting as possible for best results.

If your visor has fingerprints or smudges, use the microfiber cleaning cloth that came with the HoloLens to clean your visor gently.

[Back to list](#list)

## "Low Disk Space" error

You'll need to free up some storage space by doing one or more of the following:

- Delete some unused spaces. Go to **Settings** > **System** > **Spaces**, select a space that you no longer need, and then select **Remove**.
- Remove some of the holograms that you've placed.
- Delete some pictures and videos from the Photos app.
- Uninstall some apps from your HoloLens. In the **All apps** list, tap and hold the app you want to uninstall, and then select **Uninstall**.

[Back to list](#list)

## Calibration fails

Calibration should work for most people, but there are cases where calibration fails.
  
Some potential reasons for calibration failure include:

- Getting distracted and not following the calibration targets
- Dirty or scratched device visor or device visor not positioned properly
- Dirty or scratched glasses
- Certain types of contact lenses and glasses (colored contact lenses, some toric contact lenses, IR blocking glasses, some high prescription glasses, sunglasses, or similar)
- More-pronounced makeup and some eyelash extensions
- Hair or thick eyeglass frames if they're blocking the device from seeing your eyes
- Certain eye physiology, eye conditions, or eye surgery such as narrow eyes, long eyelashes, amblyopia, nystagmus, some cases of LASIK or other eye surgeries

If calibration is unsuccessful try:

- Cleaning your device visor
- Cleaning your glasses
- Pushing your device visor as close to your eyes as possible
- Moving objects in your visor out of the way (such as hair)
- Turning on a light in your room or moving out of direct sunlight

If you followed all guidelines and calibration is still failing, you can disable the calibration prompt in Settings. Also let us know by filing feedback in [Feedback Hub](hololens-feedback.md).

Also see related information for [image color or brightness troubleshooting.](hololens2-fit-comfort-faq.md#hologram-image-color-or-brightness-does-not-look-right)

Setting IPD is not applicable for HoloLens 2, since eye positions are computed by the system. 

[Back to list](#list)

## Auto-login asks for log-in

A HoloLens 2 device can be configured to automatically login in via **Settings** -> **Accounts** -> **Sign-in Options** -> and under **Required** setting the value to **Never**. Some users may be required to log-in to the device again when updating a device with a substantially large update, such as a feature update.

Example of when this could occur:

- Updating a device from Windows Holographic, version 2004 (Build 19041.xxxx) to Windows Holographic, version 21H1 (Build 20346.xxxx)
- Updating a device to take a large update on the same major build, e.g. Windows Holographic, version 2004 to Windows Holographic, version 20H2
- Updating a device from a factory image to the latest image

This should not occur during:

- Devices taking a monthly servicing update

Work around methods:

- Sign-in methods such as PIN, Password, Iris, Web Authentication, or FIDO2 keys.
- If device PIN cannot be remembered, and other authentication methods are not available, then a user can use [manual reflashing mode](hololens-recovery.md#manual-procedure).

[Back to list](#list)

## Microsoft Edge fails to launch

> [!NOTE]
> This issue was originally created with the shipping version of Microsoft Edge in-mind. This issue may be resolved in the [new Microsoft Edge](hololens-new-edge.md). If it is not, please file feedback.

A few customers have reported an issue where Microsoft Edge fails to launch. For these customers, the issue persists through reboot and is not resolved with Windows or application updates. If you're experiencing this issue and you've confirmed [Windows is up-to-date](hololens-updates.md#manually-check-for-updates), please file a bug from the [Feedback Hub app](hololens-feedback.md) with the following category and sub-category: Install and Update > Downloading, installing, and configuring Windows Update.

There are no known workarounds as we've been unable to root cause the issue so far. Filing a bug via Feedback Hub will help our investigation!

[Back to list](#list)

## Keyboard does not switch to special characters

There is an issue during OOBE, where once the user has chosen a work or school account and is entering their password, trying to switch to the special characters on the keyboard by tapping the &123 button does not change to special characters.

Work-arounds:
-	Close the keyboard and reopen it by tapping the text field.
-	Incorrectly enter your password. When the keyboard is relaunched next time it will then work as expected.
- Web Authentication, close the keyboard and select **Sign in from another device**.
-	If entering only numbers, a user may press and hold certain keys to open an expanded menu.
-	Using a USB keyboard.

This does not affect:
- Users who choose to use a personal account.

[Back to list](#list)

## Bluetooth devices are not pairing

If you're having problems [pairing a Bluetooth device](hololens-connect-devices.md), try the following:

- Go to **Settings** > **Devices**, and make sure that Bluetooth is turned on. If it is, turn it off and on again.
- Make sure that your Bluetooth device is fully charged or has fresh batteries.
- If you still can't connect, [restart the HoloLens](hololens-recovery.md).

[Back to list](#list)

## Devices that are listed as available in Settings don't work

HoloLens (1st gen) doesn't support Bluetooth audio profiles. Bluetooth audio devices, such as speakers and headsets, may appear as available in HoloLens settings, but they aren't supported.

HoloLens 2 supports the Bluetooth A2DP audio profile for stereo playback. The Bluetooth Hands Free profile which enables microphone capture from a Bluetooth peripheral is not supported on HoloLens 2.

If you're having trouble using a Bluetooth device, make sure that it's a supported device. Supported devices include the following:

- English-language QWERTY Bluetooth keyboards (you can use these anywhere that you use the holographic keyboard).
- Bluetooth mice.
- The [HoloLens clicker](hololens1-clicker.md).

You can pair other Bluetooth HID and GATT devices together with your HoloLens. However, you may have to install corresponding companion apps from Microsoft Store to actually use the devices.

[Back to list](#list)

## Blue screen after unenrolling from Insider preview on a device flashed with an Insider build

This is an issue affecting that affects users who are were on an Insider preview build, reflashed their HoloLens 2 with a new insider preview build, and then unenrolled from the Insider program.

This does not affect:
- Users who are not enrolled in Windows Insider 
- Insiders:
    - If a device has been enrolled since Insider builds were version 18362.x
    - If they flashed an Insider signed 19041.x build AND stay enrolled in the Insider program

Work-around: 
- Avoid the issue 
    - Flash a non-insider build. One of the regular monthly updates.
    - Stay on Insider Preview
- Reflash the device

    1. Put the [HoloLens 2 into flashing mode](https://review.docs.microsoft.com/hololens/hololens-recovery?branch=master#hololens-2) manually by fully powering down while not connect. Then while holding Volume up, tap the Power button.
    
    1. Connect to the PC and open Advanced Recovery Companion.
    
    1. Flash the HoloLens 2 to the default build.

[Back to list](#list)

## Can't connect to Wi-Fi

Here are some things to try if you can't connect your HoloLens to a Wi-Fi network:

- Make sure that Wi-Fi is turned on. To check, use the Start gesture, then select **Settings** > **Network &amp; Internet** > **Wi-Fi**. If Wi-Fi is on, try turning it off and then on again.
- Move closer to the router or access point.
- Restart your Wi-Fi router, then [restart HoloLens](hololens-recovery.md). Try connecting again.
- If none of these things work, check to make sure that your router is using the latest firmware. You can find this information on the manufacturer website.

[Back to list](#list)

## Can't sign in because my HoloLens was previously set up for someone else

You can [put the device into **Flashing Mode** and use Advanced Recovery Companion](hololens-recovery.md#clean-reflash-the-device) to recover the device.

[Back to list](#list)

## Emulator
### The HoloLens emulator isn't working

Information about the HoloLens emulator is located in our developer documentation.  Read more about [troubleshooting the HoloLens emulator](/windows/mixed-reality/using-the-hololens-emulator#troubleshooting).
