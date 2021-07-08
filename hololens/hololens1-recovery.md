---
title: Restart, reset, or recover HoloLens 1
ms.reviewer: Keep up to date on the basic and advanced instructions for rebooting or resetting your HoloLens mixed reality device.
description: How to use Windows Device Recovery Tool to flash an image to HoloLens 1st Gen.
keywords: how-to, reboot, reset, recover, hard reset, soft reset, power cycle, HoloLens, shut down, wdrt, windows device recovery tool
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.date: 06/01/2020
ms.custom: 
- CI 111456
- CSSTroubleshooting
ms.topic: article
ms.localizationpriority: medium
manager: yannisle
appliesto:
- HoloLens (1st gen)
---

# Restart, reset, or recover HoloLens (1st Gen)

If you're experiencing problems with your HoloLens, you may want to try a restart or reset, or even reflash the device by using device recovery. This article guides you through the recommended recovery steps in order.

If you're looking to recover a HoloLens 2, see [Recovering a HoloLens 2](hololens-recovery.md), as that process differs.

> [!NOTE]
> This article focuses on the HoloLens device and software. If your holograms don't look right, see **[HoloLens environment considerations](hololens-environment-considerations.md)** for information about factors that improve hologram quality.

## Restart

### Do a safe restart by using Cortana

The safest way to restart the HoloLens is by using Cortana, which is generally the first thing to try when you experience an issue with HoloLens.

> [!NOTE] 
> Cortana is not available on all devices.
> - Cortana is available on all HoloLens (1st Gen) devices. 
> - Cortana is available on HoloLens 2 devices on builds prior to the Windows Holograpic, Version 2004 update.

1. Turn on your HoloLens.
1. Make sure that a user is logged in and the device isn't waiting for a password to unlock it.
2. Say "Hey Cortana, reboot" or "Hey Cortana, restart."
3. Cortana will respond and prompt you to confirm. Wait for a sound to play after the question, and then say "Yes." The device will restart.

### Use the power button to do a safe restart

If you still can't restart your device, try to restart it by using the **power** button:

1. Press and hold the **power** button for 5 seconds. After 1 second, all five LEDs will illuminate and then slowly turn off one by one from right to left. After 5 seconds, all LEDs will be off, indicating successful shutdown.
      
   > [!IMPORTANT]
   > Stop pressing the button immediately after all the LEDs have turned off.
1. Wait 1 minute for the shutdown to complete. The shutdown may still be in progress even after the displays are turned off.
2. Turn on the device again by pressing and holding the **power** button for 1 second.

### Do a safe restart by using Windows Device Portal

> [!NOTE]
> For this process, HoloLens has to be configured as a developer device. Learn more at [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal).

If the previous procedure didn't work, try to restart the device by using [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal). In the upper-right corner, find the option to restart or shut down the device.

### Do an unsafe forced restart

If the previous methods didn't restart your HoloLens, force a restart. This method is equivalent to removing and reinstalling the battery. It's dangerous because it might leave your device in a corrupted state. If that happens, you'll have to flash your HoloLens.  

> [!WARNING]
> This is a potentially harmful method and should only be used if the previously cited methods didn't work.

1. Press and hold the **power** button for at least 10 seconds.
   - It's okay to hold the button for longer than 10 seconds.
   - It's safe to ignore any LED activity.
1. Release the button and wait for 2-3 seconds.
1. Press and hold the **power** button for 1  second.
1. If you still have problems, press the **power** button for 4 seconds, until all the battery indicators fade out and the screen stops displaying holograms. Wait 1 minute, and then press the **power** button again to turn on the device.

## Go back to a previous version - HoloLens (1st Gen)

In some cases, you might want to go back to a previous version of the HoloLens software. You can do this by using the Windows Device Recovery Tool to reset your HoloLens to the earlier version.

> [!NOTE]
> Going back to an earlier version deletes your personal files and settings.

To go back to a previous version of HoloLens 1, follow these steps:

1. Make sure that you don't have any phones or Windows devices plugged in to your PC.
1. On your PC, download the [Windows Device Recovery Tool (WDRT)](https://support.microsoft.com/help/12379).
1. Download the [HoloLens Anniversary Update recovery package](https://aka.ms/hololensrecovery).
1. When the downloads finish, open **File explorer** > **Downloads**. Right-click the zipped folder you just downloaded, and select **Extract all** > **Extract** to unzip it.
1. Connect your HoloLens to your PC using the micro-USB cable that it came with. (Even if you've been using other cables to connect your HoloLens, this one works best.)
1. The WDRT will automatically detect your HoloLens. Select the **Microsoft HoloLens** tile.
1. On the next screen, select **Manual package selection** and choose the installation file contained in the folder you unzipped in step 4. (Look for a file with the .ffu extension.)
1. Select **Install software**, and follow the instructions.

> [!NOTE]
> If the WDRT doesn't detect your HoloLens, try restarting your PC. If that doesn't work, select **My device was not detected**, select **Microsoft HoloLens**, and then follow the instructions.

## Reset to factory settings

> [!NOTE]
> The battery needs at least a 40-percent charge to reset.

If your HoloLens still has a problem, try resetting it to factory state. This step keeps the version of the Windows Holographic software that's installed on it and returns everything else to factory settings.

>[!WARNING]
> If you reset your device, all your personal data, apps, and settings will be erased, including TPM reset information. Resetting will only install the latest installed version of Windows Holographic. You'll have to redo all the initialization steps (calibrate, connect to Wi-Fi, create a user account, download apps, and so on).

1. Open the Settings app, and then select **Update** > **Recovery**.
1. Select the **Reset device** option and read the confirmation message.
1. Confirm the reset. The device will restart and display a set of spinning gears and a progress bar.
1. Wait about 30 minutes for this process to complete. When it's done, the device will restart into the "out-of-the-box" experience.

## Reinstall the operating system

If the device is still having a problem after restart and reset, you can use a recovery tool on your computer to reinstall the HoloLens operating system and firmware.  

The data that HoloLens needs for the reset is packaged in a Full Flash Update (FFU), which is similar to an .iso, .wim, or .vhd file. [Learn about FFU image file formats.](/windows-hardware/manufacture/desktop/wim-vs-ffu-image-file-formats)

You can install a new operating system on your HoloLens (1st gen) by using the Windows Device Recovery Tool. Before you use that tool, see if restarting or resetting your HoloLens fixes the problem.

The recovery process may take a while. When it's done, the latest version of the Windows Holographic software will be installed.

To use the tool, you need a computer running Windows 10 or later with at least 4 GB of free storage space. You can't run this tool on a virtual machine.

### Recover your HoloLens

1. Download and install the [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) on your computer.
1. Connect the HoloLens (1st gen) to your computer by using the Micro USB cable that came with your HoloLens.
1. Open the Windows Device Recovery Tool and follow the instructions.

If the HoloLens (1st gen) isn't automatically detected, select **My device was not detected**. Then follow the instructions to put the device into recovery mode.

### Manual flashing mode

If your device isn't detected, follow these steps to put it into flashing mode:

1. Unplug the device from any power source.
1. If the device is on, hold down the **power** button until it completely turns off.
2. Hold the **volume up** button, and briefly tap the **power** button. The device should start and display only the middle LED.
3. Plug the device into your PC.
4. Open the Windows Device Recovery Tool.
5. Select **My device was not detected** and then **HoloLens**. 
6. Follow the instructions to recover your device.
