---
title: Set up users on HoloLens 2 quickly
description: Learn how to set up your HoloLens 2 for users quickly, and what can happen that affects set up. 
ms.date: 12/1/2022
keywords: hololens
ms.service: hololens
ms.sitesec: library

ms.topic: article
ms.localizationpriority: high
appliesto:
- HoloLens 2
---

# Set up more users on your HoloLens 2

Often organizations have many devices and lots of different people who use those devices. When people are looking to use a HoloLens 2 device, they often want to get straight to their app. This can sometimes be hindered by having to do additional setup. In this article we cover the best ways to reduce set up time, best practices, and cover variations in logging into a device.

> [!NOTE]
> In all these scenarios we’re talking about scenarios in which a second user can use the device, so all these scenarios use Microsoft Entra identities.

## Best practices

The following are the average lengths for each scenario.

| Scenario start to app launch                                                    | Average time in minutes | Best practices |
|---------------------------------------------------------------------------------|-------------------------|---|
| User exists on device, sign in existing account                                                 | Under a minute                    | - [Use a device you've used before](#use-a-device-you-have-already-used-to-get-to-your-app-fastest) <br> - [Use labels](#physically-label-your-devices) <br> - [Fast logins](#fastest-to-log-in-to-an-existing-account)    |
| New user on device                                                              | Short                                             | - [Quick add user](#adding-your-user-to-an-existing-device) <br> - [Set up flows](#set-up-flows)   |
| Device needs to go through first-time setup or the Out of Box Experience (OOBE)                             | Moderate              | - [Fast first set up](#setting-up-a-device-for-the-first-time) <br> - [Pre set up person](#have-a-designated-setup-person) <br> - [Use policies](#use-policies-to-speed-up-your-setup) <br> - [Set up flows](#set-up-flows)    |

### Use a device you have already used to get to your app fastest

The key take away from this chart, is if you can use a device you’ve used before then you can sign in and use the app in less than a minute. If you have to go through setup, then it takes a few minutes. We highly suggest you [physically label your devices](#physically-label-your-devices).

### Have a designated setup person

Have someone at your location who sets up your devices. By setting up devices in advance, you can ensure that when the HoloLens reaches the end user that the device is configured with any policies and apps they need. It also helps shorten the amount of time it takes for them to set up.

#### Pre setup Autopilot

If your devices are set up to go through [Autopilot](hololens2-autopilot.md), then take those devices through Autopilot. It happens regardless, but by doing it now you save your end-user several minutes of time. Autopilot can apply helpful settings to speed up the new user process, as well as deploy your apps to the device.

- If you have an Ethernet to USB-C adapter, you can plug in your devices the moment OOBE starts to begin autopilot without having to wear the devices.
- You can also create a USB-C flash drive with a [provisioning package](hololens-provisioning.md) that contains your Wi-Fi info. Plug it in when OOBE starts, and confirm applying the provisioning package. Wi-fi is detected and you can start Autopilot.
- If you don't have those options available, then manually proceed through OOBE until Autopilot starts.

#### Provision the device in advance

You can use a [provisioning package](hololens-provisioning.md) to apply both helpful settings to speed up the new user process, as well as deploy your apps to the device. Take a look at [use policies to speed up your setup](#use-policies-to-speed-up-your-setup) to see which policies speed up device set up for the first user, and for each new user.

If you complete OOBE and set yourself up as a user then when your end users pick up the device they have a scenario of adding themselves as a new user.

#### Physically label your devices

Place a label either on the rear outer cover, or the outer arms closer to the front so they don’t go into the rear outer cover. See [about HoloLens 2](hololens2-hardware.md) to see the names of hardware parts.

By having a labeled device users can quickly pick up a device, they've used before. It can also help recognize other things such as a device that's known not to be working, or which ones were just used and still need charging.

### Fastest to log in to an existing account

When signing back into a device, there are several methods you can use. We cover the fastest three.

- **Iris** : Once Iris is set up, either during OOBE or in Settings, a user can sign back in with Iris. This takes no input on behalf of the user and they’re instantly signed in when recognized.
- **PIN** : A PIN has a minimum requirement of six numbers, this is much faster than typing in a lengthy password with multiple requirements.
- **FIDO2 Security key** : A security key allows someone to login with a PIN (for the key) and a touch, this is quite fast. Also when setting up a new user on a device using a FIDO2 security key won't require them to using their phone for Multi-factor authentication.

### Fastest ways to set up account on new device

When you are getting your account on a new device for the first time you don't want to be typing out your full username and password using the holographic keyboard. Depending on the scenario you're in there's two faster ways.

#### Adding your user to an existing device

Use a FIDO2 Security key. Why? By using a FIDO2 security key you don't have to type in your user name and password, or even use multi factor authentication. You can add your user to the device quickly in this way.

#### Setting up a device for the first time

When in the EULA after confirming it's a work device, don't start typing your username. Instead select **sign in from another device**. This practice lets you go to [aka.ms/devicelogin](https://aka.ms/devicelogin) on another device, type in the 9 character code, and proceed to sign in. If you've already logged into your account on that device, then you are able to select your account. If you haven't, then you are able to use a keyboard you are more familiar with.

### Use policies to speed up your setup

#### First experience policies

If you want to speed up both Out of Box Experience (OOBE) set up or for each new user on devices, then you want to set first experience policy.

If you're using Windows Configuration Designer to create provisioning packages, you can use the wizard to **Provision HoloLens devices** -> **Provision HoloLens 2 devices** and ensure you properly configure everything in the Set-up device page to help streamline OOBE.

<br>
<img src="images/WCD-OOBE-skip.jpg" width="500px" alt="WCD OOBE First Experience">

[FirstExperience (Windows Configuration Designer reference)](/windows/configuration/wcd/wcd-firstexperience)

#### Additional policies

There are many other policies that affect the setup experience, by configuring them as well you reduce the number of screens in the setup experience. When setting up additional users, you also see screens for speech and location. By configuring the setting for the device, no additional users see those confirmations.

> [!NOTE]
> For Speech, the consent screen is not be shown if the feature is disabled. If it is left as default (user choice) or set to on, the user is still presented with the consent screen.
| What's skipped          | Details                                                                    |  Screenshot of screen skipped |
|------------------|-----------------------------------------------------------------------------------|---|
| Telemetry | The page asking users to help improve HoloLens, by reporting additional data which helps us fix bugs. <br> Using [Policies/System/AllowTelemetry](/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)      | <img src="images/24-telemetry.png" width="200px" alt="Telemetry level"> |
| Speech | The page which asks the user if they'd like to use voice commands on the device. <br> Using [Policies/Privacy/AllowInputPersonalization](hololens-cortana.md#managing-speech-on-hololens) | <img src="images/22-do-more-with-voice.png" width="200px" alt="Enable Cortana">
| Location | The page which asks the user to enable their location to improve in app experiences. <br> Using [Policies/System/AllowLocation](/windows/client-management/mdm/policy-csp-system#system-allowlocation) | <img src="images/setup-location-services.png" width="200px" alt="Enable location services"> |
| Iris | The page asking a user to enroll in Iris authentication and the process of enrolling. <br> Using [Passportforwork CSP](/windows/client-management/mdm/passportforwork-csp) <br> ./Device/Vendor/MSFT/PassportForWork/Biometrics/UseBiometrics | <img src="images/setup-iris.png" width="200px" alt="Iris setup"> |
| Skip Calibration | The calibration run during OOBE, which can later be run via the Settings app, or when an app that uses eye tracking prompts the user to calibrate. <br> Using: [SkipCalibrationDuringSetup](/windows/client-management/mdm/policy-csp-mixedreality#mixedreality-skipcalibrationduringsetup) <br> This policy requires [Windows Holographic, version 22H2](hololens-release-notes.md#windows-holographic-version-22h2) or newer.     | <img src="images/07-adjust-eyes.png" width="200px" alt="Adjust for your eyes"> |
| Skip Training    | How to open and close the Start menu, which can later be learned via the Tips app. <br> Using: [SkipTrainingDuringSetup](/windows/client-management/mdm/policy-csp-mixedreality#mixedreality-skiptrainingduringsetup) <br> This policy requires [Windows Holographic, version 22H2](hololens-release-notes.md#windows-holographic-version-22h2) or newer.  | <img src="images/26-02-startmenu-learning.png" width="200px" alt="Learn how to use the start gesture, image 2"> |

## Set up conditions

In general there are a few scenarios when you pick up a device. In those scenarios there can also be some variations that can speed up (or slow down) your setup. The general states you can find a device in when picking it up to use it are:

- You’ve signed into this device already
- You haven’t signed into this device yet
- No one has set up this device yet

The modifiers that can increase or decrease the time to set up are typically:

- You use a provisioning package to apply settings all at once, instead of manually during setup
- Your device already has helpful setup policies, due to someone else applying them via provisioning or from going through Autopilot set up
- Your device needs to go through autopilot, which takes some time
- Your device was connected to the Internet and went through autopilot already, saving time
- Your device's battery is low, which may pause Autopilot if it occurs

## Set up flows

Let us walk through different scenarios in which your device needs to be set up. This excludes signing back into a device that already has your account on it:

**Instructions:** *Select the link matching what you see, your selection determines the tabs you see in the next section.*
<br> When you first boot on the device what do you see?

- **A.** [A swirl of colors](/hololens/hololens2-new-user-optimize?tabs=OOBEswirl%2CsecondBlank#a-swirl-of-colors-1)
- **B.** [A previously signed in user or list of users](/hololens/hololens2-new-user-optimize?tabs=Users#a-previously-signed-in-user-or-list-of-users)

[!INCLUDE[](includes/hololens-new-user.md)]

[!INCLUDE[](includes/hololens-oobe-screens.md)]

1. You may be asked to set up multi-factor authentication if it hasn’t already been set up on this account.
1. Calibration starts. Run through the calibration process following the gems with your eyes.
1. Your device prompts you to set up Iris sign in. Go ahead and register following the dots with your eyes.
1. You are asked to set up a PIN for your login. This is for this device only.
1. You are shown prompts for voice, location, and telemetry. (Please enable telemetry as it helps us identify and fix issues.) <sup>1</sup>
1. You are shown how to open the start menu. Hold your palm facing you and tap your wrist. Do it again and finish the training. <sup>1</sup>

<sup>1</sup> - These screens can be skipped if these settings were previously configured by policy.

You have completed set up. Congrats!

#### After OOBE - Paths to your app

We’re still a few steps away from being able to make that Remote Assist call. Using the following flow chart we can determine the environment you're in and how to use Remote Assist.
<br>

<img src="images/hololens2-kiosk-remote-assist-flowchart.png" alt="Post OOBE flowchart">

> [!NOTE]
> After device set up the Microsoft Store app checks for updates for Remote Assist [and other in-box apps](hololens2-hardware.md#pre-installed-software) approx every 24 hours.
