---
title: Set up users on HoloLens 2 quickly
description: Learn how to set up your HoloLens 2 for users quickly, and what can happen that affects set up. 
ms.date: 12/1/2022
keywords: hololens
ms.prod: hololens
ms.sitesec: library

ms.topic: article
ms.localizationpriority: high
appliesto:
- HoloLens 2
---

# Add more users to your HoloLens 2

HoloLens 2 can support a wide range of use cases and opportunities for customers. We know that time is money, and customers want to get to work as quickly as possible with their HoloLens devices.  To that end, we have created this set of best practices to guide customers towards a login experience based on their requirements that takes one minute or less.  This guidance assumes that the initial OOBE and AAD Domain Join / Autopilot process have already been completed.

> [!NOTE]
> In this section, we’re talking about scenarios in which additional users can use the device, so all these scenarios use Azure AD identities.

> [!TIP]
> If you need to set up more than five additional users, see [Deploying HL2](/hololens-core-components) for best practices on HoloLens deployments for the enterprise.

## Three best practices to reduce time to login

Follow these steps to reduce the time it takes to add more users to a HoloLens 2 device.

### Configure user settings and preferences in advance

There are many other policies that affect the setup experience, by configuring them as well you reduce the number of screens in the setup experience. When setting up more users, you also see screens for speech and location. By configuring the setting for the device, no additional users see those confirmations, saving time during the login process.

If you prefer each user to set these preferences individually, this step adds several minutes to the total login time duration.

> [!NOTE]
> For Speech, the consent screen is not shown if the feature is disabled. If it is left as default (user choice) or set to on, the user is still presented with the consent screen.
|What's skipped          | Details                                                                    |Screenshot of screen skipped |
|------------------|-----------------------------------------------------------------------------------|---|
| Telemetry | During sign in, the HoloLens asks for consent to share telemetry data with Microsoft. To save time during the login process, this setting can be applied via policy, which prevents this screen from appearing.  We recommend setting it to Full. <br> Using [Policies/System/AllowTelemetry](/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)      | <img src="images/24-telemetry.png" width="200px" alt="Telemetry level"> |
| Speech | HoloLens supports two key kinds of speech interaction. One method is called “See it Say it,” which is processed on device, and allows for navigation of the menu options and applications. Another methos is dictation support, where voice data is sent to the cloud to enable experiences involving full speech to text.  HoloLens does not support automatic consent for the Dictation services, and requires explicit user opt in. However, disabling the dictation services removes the prompt, whilst leaving “See it Say it” navigation enabled. If your organization and applications do not use the dictation services, they can be disabled through policy to enable a faster sign in experience. <br> Using [Policies/Privacy/AllowInputPersonalization](hololens-cortana.md#managing-speech-on-hololens) | <img src="images/22-do-more-with-voice.png" width="200px" alt="Enable Cortana">|
| Location | During sign in, the HoloLens asks for consent to share the users location with applications. This setting is often used in D365 Guides and Remote Assist to track the location the user is calling from (city level). To save time during the login process, this setting can be applied via policy, which prevents this screen from appearing. <br> Using [Policies/System/AllowLocation](/windows/client-management/mdm/policy-csp-system#system-allowlocation) | <img src="images/setup-location-services.png" width="200px" alt="Enable location services"> |
| Iris | The page that asks a user to enroll in Iris authentication and the process of enrolling. <br> Using [Passportforwork CSP](/windows/client-management/mdm/passportforwork-csp) <br> ./Device/Vendor/MSFT/PassportForWork/Biometrics/UseBiometrics | <img src="images/setup-iris.png" width="200px" alt="Iris setup"> |
| Skip Calibration | The calibration runs during OOBE, and can also run later via the Settings app, or when an app that uses eye tracking prompts the user to calibrate.  <br> Using: [SkipCalibrationDuringSetup](/windows/client-management/mdm/policy-csp-mixedreality#mixedreality-skipcalibrationduringsetup) <br> This policy requires [Windows Holographic, version 22H2](hololens-release-notes.md#windows-holographic-version-22h2) or newer.  If you prefer a faster login, you can choose to perform Eye Calibration at a later point when required.   | <img src="images/07-adjust-eyes.png" width="200px" alt="Adjust for your eyes"> |
| Skip Training    | When a new user logs in to the HoloLens device, a short training session, taking approx. 45 seconds, is shown to demonstrate how to open and close the Start menu. Many customers provide training on how to use HoloLens devices for their employees, so you can save time by skipping this training session.  The Tips app can be used on-demand to view this training session. <br> Using: [SkipTrainingDuringSetup](/windows/client-management/mdm/policy-csp-mixedreality#mixedreality-skiptrainingduringsetup) <br> This policy requires [Windows Holographic, version 22H2](hololens-release-notes.md#windows-holographic-version-22h2) or newer.  | <img src="images/26-02-startmenu-learning.png" width="200px" alt="Learn how to use the start gesture, image 2"> |

### Choose the right user identity for your scenario

Many companies want users to have access to corporate resources when using a HoloLens device, which requires that an Azure AD account is used.  There are two types of Azure AD accounts available on the HoloLens:

- Named user account
- Shared account

If it is important to know the identity of the user using the HoloLens device, then a Named user account should be used.  There are several scenarios where knowing the user's identity may be required, especially if the company is part of a regulated industry, but also if different content is provided to different users based on their training or seniority.  In these scenarios, it is important to follow these best practices to optimize and reduce the time to login.

For scenarios such as general training, it may not be necessary to track the identity of the person using the device. In this case, a Shared user account on the device allows you to have a single-click sign in, minimizing the time to log in. 

> [!NOTE] 
> Care should be taken to ensure that the permissions assigned to the shared account only allow access to “open” data that can be accessed by anyone in the organization, and physical security on the HoloLens device is set to ensure that it cannot be accessed without authorization.

For full details on setting up a “Shared” account with HoloLens 2, refer to [Shared Azure AD accounts in HoloLens](/hololens/shared-aad-accounts).

### Choose the right login method for your user identity

The HoloLens 2 is by design, a heads-up hands-free device, and is optimized for input using voice and hand interaction. However, logging onto an Active Directory account requires the use of a username and password, and the setup of a Windows Hello for Business credential, requires the use of Multi Factor Authentication.

The fastest login method for your users varies based on whether you use named user or shared accounts.

Named user accounts experience the fastest login experience when using these login methods:

- Iris authentication
- FIDO key-based authentication, both with and without the NFC reader
- Sign in from another device, using Authenticator App

Shared accounts experience the fastest login experience when using these login methods:

- FIDO key-based authentication, both with and without the NFC reader
- Sign in from another device, using Authenticator App
- PIN

## More tips for managing your HoloLens 2 devices

This table helps to illustrate how long it takes to get to app launch for the most common scenarios.

| Scenario start to app launch                                                 | Average time in minutes | Best practices |
|------------------------------------------------------------------------------|----------------------|---------|
| User exists on device, sign in with existing account                                                 | Under a minute                    | - [Use a device you've used before](#physically-label-your-devices-so-users-can-select-a-device-theyve-already-used) <br> - [Use labels](#physically-label-your-devices-so-users-can-select-a-device-theyve-already-used) <br> - [Fast logins](#let-your-users-know-the-fastest-ways-to-log-in-to-an-existing-account)    |
| New user on device, where at least one person has already signed in                                                     | Short                                             | - [Quick add user](#adding-your-user-to-an-existing-device) <br> - [Set up flows](#set-up-flows)   |
| New device, which needs to go through first-time setup or the Out of Box Experience (OOBE)                             | Moderate              | - [Fast first set up](#setting-up-a-device-for-the-first-time) <br> - [Pre set up person](#have-a-designated-setup-person) <br> - [Use policies](#use-policies-to-speed-up-your-setup) <br> - [Set up flows](#set-up-flows)    |

To help you optimize device management, here are some more tips recommended to further reduce the time it takes to get up and running on the device.

### Physically label your devices so users can select a device they've already used

Place a label either on the rear outer cover, or the outer arms closer to the front so they don’t go into the rear outer cover. See [about HoloLens 2](hololens2-hardware.md) to see the names of hardware parts.  By having a labeled device, users can quickly pick up a device they've used before. It can also help recognize other things such as a device that's known not to be working, or which ones were recently used and still need charging.

The key takeaway from this table is, if you can use a device you’ve used before, then you can sign in and use the app in less than a minute. If you have to go through setup, then it takes a few more minutes.

### Set up all devices in advance

By setting up devices in advance, you can ensure that when the HoloLens reaches the end user that the device is configured with any policies and apps they need. It also helps shorten the amount of time it takes for them to set up.

#### Have a designated setup person

Have one or two people at your location who set up your devices. This consistency ensures that all devices are set up most efficiently and in a way that meets your organization's requirements.

#### Setup Autopilot in advance

If your devices are set up to go through [Autopilot](hololens2-autopilot.md), then take those devices through Autopilot. It happens eventually, but doing it in advance can the end-user several minutes of time. Autopilot can apply helpful settings to speed up the new user process, and also deploy your apps to the device.  With the 23H2 release, Autopilot can also deploy a shared Azure AD account to the device.  For more information, see [Shared Azure AD accounts in HoloLens](/hololens/shared-aad-accounts) for more details.

- If you have an Ethernet to USB-C adapter, you can plug in your devices the moment OOBE starts to begin autopilot without having to wear the devices.
- You can also create a USB-C flash drive with a [provisioning package](hololens-provisioning.md) that contains your Wi-Fi info. Plug it in when OOBE starts, and confirm applying the provisioning package. Wi-fi is detected and you can start Autopilot.
- If you don't have those options available, then manually proceed through OOBE until Autopilot starts.

#### Provision the device in advance

You can use a [provisioning package](hololens-provisioning.md) to apply both helpful settings to speed up the new user process, and deploy your apps to the device. Take a look at [use policies to speed up your setup](#use-policies-to-speed-up-your-setup) to see which policies speed up device set up for the first user, and for each new user.

If you complete OOBE and set yourself up as a user, then when your end users pick up the device they have the option of adding themselves as a new user.

### Let your users know the fastest ways to log in to an existing account

When signing back into a device, there are several methods you can use. We cover the fastest three here.  Ensure your users can use one of these three login methods.

- **Iris** : Once Iris is set up, either during OOBE or in Settings, a user can sign back in with Iris. No input is required from the user and they’re instantly signed in when recognized.
- **FIDO2 Security key with an NFC reader** : A security key used with an NFC reader (supported with the 23H2 release) allows the user to login with two taps, which is fast. Also, when setting up a new user on a device using a FIDO2 security key, the user isn't required to use a phone for Multi-factor authentication.  
- **PIN** : A PIN has a minimum requirement of six numbers and is faster than typing in a lengthy password with multiple requirements.

#### More policies

For a list of more policies that can be set in advance, see [Configure user settings and preferences in advance](/hololens2-new-user-optimize?tabs=firstBlank%2CsecondBlank#Configure-user-settings-and-preferences-in-advance/).

You have now completed set up. Congrats!

#### After OOBE - Paths to your app

We’re still a few steps away from being able to use an app, such as Guides, to make a call. Using the following flow chart, we can determine the environment you're in and how to use Guides, as an example.
<br>

<img src="images/hololens2-kiosk-remote-assist-flowchart.png" alt="Post OOBE flowchart">

> [!NOTE]
> After device set up the Microsoft Store app checks for updates for Guides [and other in-box apps](hololens2-hardware.md#pre-installed-software) approximately every 24 hours.

