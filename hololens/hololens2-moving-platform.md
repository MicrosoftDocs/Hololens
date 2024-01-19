---
title: HoloLens 2 Moving Platform Mode
description: How to use HoloLens on moving platforms
keywords: moving platforms, dynamic motion, hololens, moving platform mode

ms.reviewer: JoshuaElsdon
ms.date: 2/15/2021
ms.service: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: high
audience: HoloLens

appliesto:
- HoloLens 2
---

# Moving Platform Mode on Low Dynamic Motion Moving Platforms

In [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2) has newly added support for tracking on low-dynamic motion moving platforms on HoloLens 2. After installing the build and enabling Moving Platform Mode, you'll be able to use your HoloLens 2 in previously inaccessible environments like large ships and large marine vessels. Currently, the feature is targeted at enabling these specific moving platforms only. While nothing prevents you from attempting to use the feature in other environments, the feature is focused on adding support for these environments first.

![Moving platform example.](./images/mpm-compare.gif)

This article covers:

1. [Why Moving Platform is Necessary](#why-moving-platform-mode-is-necessary)
1. [Enabling Moving Platform Mode](#enabling-moving-platform-mode)

## Why Moving Platform Mode is Necessary

HoloLens needs to be able to track your head position with [6 degrees of freedom](https://en.wikipedia.org/wiki/Six_degrees_of_freedom) (X, Y, Z, translation, and roll, pitch, yaw rotation) in order to show stable holograms. To do that, HoloLens tracks two similar pieces of information from two separate sources:

1. **Visible light cameras.** These cameras track the environment, for example, the physical room in which you’re using the HoloLens
1. **Inertial Measurement Unit (IMU).** The IMU consists of an accelerometer, gyroscope, and magnetometer that tracks your head motion and orientation relative to Earth

Information from these two sources is compounded to track your head position at a low latency and high enough frequency in order to render smooth holograms.

However, this approach relies on a critical assumption; the environment (tracked by the cameras) remains stationary relative to Earth (against which the IMU can make measurements). When that isn’t the case, like on a boat in the water, the information from both sources can conflict with one another and cause the tracker to get lost. This conflict produces incorrect position information and results in swimmy holograms or even tracking loss.

Moving Platform Mode remedies this issue. When you enable Moving Platform Mode, that is a hint to the tracker that it can’t rely on our sensor inputs to completely agree with each other at all times. Instead, HoloLens needs to rely more heavily on visual tracking and quickly identify incongruous inertial motion data and filter it out accordingly before it's able to use the IMU input.

## Supported Environments and Known Limitations

While Moving Platform Mode was developed to intelligently handle cases of inertial and visual data conflict, it’s currently scoped to large marine vessels experiencing low-dynamic motion. Meaning there are certainly limitations and unsupported scenarios.

### Known Limitations

- The only supported environments for Moving Platform Mode (MPM) are large marine vessels experiencing low-dynamic motion. In other words, many common environments/situations are **not** yet supported due to their high frequency motion and high levels of acceleration and [jerk](https://en.wikipedia.org/wiki/Jerk_(physics)). For example: planes, trains, cars, bikes, buses, small boats, elevators, etc.
- Holograms might wobble slightly when MPM is enabled, especially when on choppy water.
- Nothing prevents users from attempting to use MPM in unsupported environments, however, you might experience undesirable side-effects if the device is able to maintain tracking in the unsupported space. For example, with MPM, you might find it's possible to use in an elevator while changing floors, whereas that was previously impossible. Unfortunately, while MPM allows the device to maintain tracking, it doesn’t handle map management at this time. You could find that changing floors in an elevator causes the device to confuse the upper and lower floors and negatively affect map quality.

## Prerequisites

Support for Moving Platform Mode requires the following prerequisites:

Install [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2) or newer by updating or flash to the [latest build](https://aka.ms/hololens2download) [via ARC](hololens-recovery.md#clean-reflash-the-device).

> [!NOTE]
> While Moving Platform Mode was introduced in 21H2, it's suggested using the [latest build](hololens-release-notes.md) to use the full range of features and updates.

## Enabling Moving Platform Mode

### How should I activate Moving Platform Mode?

There are four ways that you can enable Moving Platform Mode:

- [Via the on-device settings app](#on-device-settings)
- [Via Mobile Device Management (MDM) policies](#via-mobile-device-management-mdm)
- [Via API](/windows/mixed-reality/develop/unity/moving-platform-unity), the API will be released via Mixed Reality Feature tool in Unity and via Nuget.org
- [Via the device portal](#enable-via-developer-mode-and-device-portal)

In order to enable a range of use cases, various methods have been provided to activate Moving Platform Mode. It's important that you carefully consider which method to choose. A key question to ask is: Who knows whether the HoloLens 2 is currently within a moving platform? See the following table for an example:

| Who knows if HL2 is in a moving platform | Best method of setting Moving Platform Mode | Benefits | Costs |
|--------------|------------------------|-----|---- |
|System Administrator| [Mobile Device Management](#via-mobile-device-management-mdm)|  The user doesn't need to be involved. Any app will work without modification. Device can be protected from entering the incorrect mode.| User and apps can't change the mode. |
|End User            | [The Settings App](#on-device-settings)| The user is often the most knowledgeable about when and where they're using the device. Any app will work without modification.| The user may not know the mode exists. |
|The Application     | [Use the SDK](/windows/mixed-reality/develop/unity/moving-platform-unity)| Use case specific cues can be used to swap the mode when the environment can't be known ahead of time. Removes the requirement that a user has to make this decision and change the mode in settings.| A poorly designed app can give a very bad experience, and leave the device in an unexpected mode. |

### On Device Settings

- Requires build [20348.1447](hololens-release-notes.md#windows-holographic-version-21h2---february-2022-update) or newer.

1. Open the Start menu
1. Open the Settings app
1. Select **System**
1. Open **Holograms**
1. In the Moving Platform Mode section, select **Setup moving platform mode**

    ![How to reach the Moving Platform Mode page](images/mpm-from-holograms-settings.jpg)

1. Toggle Moving Platform Mode to **On**

    ![Moving Platform Mode page](images/moving-platform-mode-settings.jpg)

### Via Mobile Device Management (MDM)

- Requires build [20348.1447](hololens-release-notes.md#windows-holographic-version-21h2---february-2022-update) or newer.

MDM is a tool for system administrators to set certain settings on devices owned by the organization. See [Using Microsoft’s Endpoint Manager Intune to manage HoloLens devices](hololens-mdm-configure.md) for more details. System administrators can choose from three options:

1. Force Moving Platform Mode on for device.
1. Force Moving Platform Mode off for device.
1. Allow users to select via the settings app / device portal.

#### MixedReality/ConfigureMovingPlatform

This policy controls the behavior of moving platform feature on HoloLens 2. Specifically whether it’s turned off / on or it can be toggled by a user. It should only be used by customers who intend to use HoloLens 2 in moving environments with low dynamic motion. Refer to [HoloLens 2 Moving Platform Mode](hololens2-moving-platform.md) for background information.

The OMA-URI of new policy: `./Device/Vendor/MSFT/Policy/Config/MixedReality/ConfigureMovingPlatform`

Supported values:

- `0` *(Default)* : The value is the user's preference. Initial state is OFF and after that user's preference is persisted across reboots and is used to initialize the system.
- `1` *Force off* : Moving platform is disabled and cannot be changed by user.
- `2` *Force on* : Moving platform is enabled and cannot be changed by user.

#### MixedReality/ManualDownDirectionDisabled

This policy controls whether the user can change down direction manually or not. If no down direction is set by the user, then an automatically calculated down direction is used by the system. This policy has no dependency on ConfigureMovingPlatform policy and they can be set independently.

The OMA-URI of new policy: `./Device/Vendor/MSFT/Policy/Config/MixedReality/ManualDownDirectionDisabled`

Supported values:

- `False` *(Default)* : User can manually change down direction if desired, otherwise down direction is determined automatically based on the measured gravity vector.
- `True` : User can’t manually change down direction and down direction will be always determined automatically based on the measured gravity vector.

### Enable via SDK

- Requires build [20348.1447](hololens-release-notes.md#windows-holographic-version-21h2---february-2022-update) or newer.

Sometimes you may want the decision on if to use Moving Platform Mode to be dependent on your situation, you may only need it enabled when using your app, or only a specific app. In these cases you may wish to [enable Moving Platform Mode from your app using the SDK](/windows/mixed-reality/develop/unity/moving-platform-unity).

### Enable via [Developer Mode and Device Portal](/windows/mixed-reality/develop/advanced-concepts/using-the-windows-device-portal)

To enable Moving Platform mode this way, first [enable Device Portal](/windows/mixed-reality/develop/advanced-concepts/using-the-windows-device-portal).

1. Select the **System** accordion on the Left-hand menu

   ![First image.](.\images\mpm-01.png)

2. Select the **Moving Platform Mode** page and check the **Moving Platform Mode** checkbox

    ![Second image.](.\images\mpm-02.png)

3. When prompted with a warning, select **OK**

   ![Third image.](.\images\mpm-03.png)

4. The mode will change immediately, there is no need to restart the device.

If you’re unable to see the Moving Platform Mode option in Device Portal, then it likely means you aren’t yet on the proper build. See the [Prerequisites](#prerequisites) section.

## When to change to/from Moving Platform Mode

When using any of these methods tracking of the headset will be lost temporarily, and the displays show “looking for your space”. Therefore, it isn’t recommended to change the mode actively during use of the device.

If your use case moves between stationary environments and moving ones, it’s recommended to leave the device in Moving Platform Mode. The tracking quality when in stationary environments will be reduced slightly. Though most would consider this better than the loss of tracking incurred by swapping the moving platform mode frequently, or losing tracking on the moving platform due to forgetting to activate the mode.

### Down Direction

Normally the direction that is considered “down” by the system is the direction of gravity. This down direction is used for alignment of some user interfaces. However within a moving platform “down” and gravity aren’t always the same thing. Moving Platform Mode provides two solutions to this problem:

#### Automatic Down Calculation

This calculates the down direction based on an average of the measured gravity directions. For example, as a ship rolls in the sea, the actual gravity vector rotates relative to the structure of the ship. The average of the gravity vectors over a short time will point towards the floor of the ship’s cabin due to the oscillations of the gravity vector will cancel out.

Automatic down calculation is the default when in Moving Platform Mode, you do not need to do anything for it to work correctly. It is overridden if a manual down direction is set. The particular down direction will not be persisted to the device, but will be recalculated when necessary.

#### Manually Set Down Direction

For a use case where the orientation of the platform is not aligned with gravity, even when averaged over a short period of time, you can set the down direction manually. To set down direction manually:

1. Open the Start menu
1. Open the **Settings** app
1. Select **System**
1. Select **Holograms**
1. In the Moving Platform Mode section, select **Setup moving platform mode**
1. Align your head with the floor, such that you are looking at the horizon
1. Select the **set Down** button

When the Set Down button is pressed the current head orientation will be used to set the down direction. When down direction is set manually, it is stored persistently on the device and will be recalled after reboot or tracking loss.

To clear the down direction stored on the system, select the **Clear Down** button on the *Setup Moving Platform Mode* page. This clears the stored down direction and makes the system use the automatically calculated down direction. The particular manually set down direction cannot be recovered after this operation, you must set it again using the above process.

## Reporting Issues

You might hit issues, if that happens please report issues so they can be investigated and improve the product:

1. Report the issue via [Feedback Hub](hololens-feedback.md) under the **Hologram accuracy, stability, and reliability** category and include:
    1. A description of problem, including the expected behavior and experienced behavior
    1. A Mixed Reality [video capture](holographic-photos-and-videos.md#capture-a-mixed-reality-video) of the issue
2. Open a support case at [https://aka.ms/hlsupport](https://aka.ms/hlsupport) and share the Feedback Hub URL, so we can reach out in case we have follow-up questions.
