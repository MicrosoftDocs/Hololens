---
title: HoloLens 2 Moving Platform
description: How to use HoloLens on moving platforms
keywords: moving platforms, dynamic motion, hololens, moving platform mode
author: evmill
ms.author: v-evmill
ms.reviewer: yabahman
ms.date: 8/10/2021
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: high
audience: HoloLens
manager: yannisle
appliesto:
- HoloLens 2
---

# Moving Platform Mode on Low Dynamic Motion Moving Platforms

As of **Insider build 20348.1411** we have added beta support for tracking on low-dynamic motion moving platforms on HoloLens 2. After installing the build and enabling Moving Platform Mode, you'll be able to use your HoloLens 2 in previously inaccessible environments like large ships and large marine vessels. Currently, the feature is targeted at enabling these specific moving platforms only. While nothing prevents you from attempting to use the feature in other environments, the feature is focused on adding support for these environments first.

> [!NOTE]
> This feature is currently only available via Windows [Insiders](hololens-insider.md).

## Why Moving Platform Mode is Necessary

HoloLens needs to be able to track your head position with [6 degrees of freedom](https://en.wikipedia.org/wiki/Six_degrees_of_freedom) (X, Y, Z translation and roll, pitch, yaw rotation) in order to show stable holograms. To do that, HoloLens tracks two similar pieces of information from two separate sources:

1. Visible light cameras – which track the environment, for example, the physical room in which you are using the HoloLens
1. Inertial Measurement Unit (IMU), – which consists of an accelerometer, gyroscope, and magnetometer that tracks your head motion and orientation relative to Earth

Information from these two sources is compounded to track your head position at a low latency and high enough frequency in order to render smooth holograms.

However, this approach relies on a critical assumption; the environment (tracked by the cameras) remains stationary relative to Earth (against which the IMU can make measurements). When that is not the case, like on a boat in the water, the information from both sources can conflict with one another and cause the tracker to get lost. This conflict produces incorrect position information and results in swimmy holograms or even tracking loss.

Moving Platform Mode remedies this issue. When you enable Moving Platform Mode, that is a hint to our tracker that we cannot rely on our sensor inputs to completely agree with each other at all times. Instead, we need to rely more heavily on visual tracking and quickly identify incongruous inertial motion data and filter it out accordingly before we&#39;re able to use the IMU input.

## Supported Environments and Known Limitations

While Moving Platform Mode was developed to intelligently handle cases of inertial and visual data conflict, it is currently scoped to large marine vessels experiencing low-dynamic motion. Meaning there are certainly limitations and unsupported scenarios.

### Known Limitations

- The only supported environments for Moving Platform Mode (MPM) are large marine vessels experiencing low-dynamic motion. In other words, many common environments/situations are **not** yet supported (for example: planes, trains, cars, bikes, buses, small boats, elevators, etc.) due to their high frequency motion and high levels of acceleration and [jerk](https://en.wikipedia.org/wiki/Jerk_(physics)).
- Holograms may not be as stable when MPM is enabled, especially when on choppy water.
- Nothing prevents users from attempting to use MPM in unsupported environments, however, users may experience undesirable side-effects if the device is able to maintain tracking in the unsupported space. For example, with MPM, users may find it&#39;s possible to use in an elevator while changing floors, whereas that was previously impossible. Unfortunately, while MPM allows the device to maintain tracking, it does not handle map management. So users will find that changing floors in an elevator will cause the device to confuse the upper and lower floors and create a map prone to worm holing.

## Prerequisites

Beta support for Moving Platform Mode requires only a few prerequisites:

1. Install build 20348.1411 or newer [by flashing the latest Insiders build via ARC](hololens-insider.md#ffu-download-and-flash-directions) or [enrolling and updating your device](hololens-insider.md#start-receiving-insider-builds).
   - Note: This build is currently only available on the [Insider Dev Channel](hololens-insider.md#start-receiving-insider-builds).
2. Enable [Developer Mode and Device Portal](/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)

## Enabling Moving Platform Mode

To enable Moving Platform mode, first [enable Device Portal](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).

1. Click on the **System** accordion on the Left-hand menu
2. Click on the **Moving Platform Mode** page and check the **Moving Platform Mode** checkbox

![First image](.\images\moving-platform-1.png) ![Second image](.\images\moving-platform-2.png)

3. When prompted with a warning, click **OK**

![Third image](.\images\moving-platform-3.png)

4. Reboot your device, which can be done either via the Device Portal **Power** menu at the top right or by issuing the following voice command &quot;Reboot the device&quot; and clicking &quot;Yes&quot;.

![Fourth image](.\images\moving-platform-4.png)

If you are unable to see the Moving Platform Mode option in Device Portal, then it likely means you are not yet on the proper build. See the [Prerequisites](#prerequisites) section.