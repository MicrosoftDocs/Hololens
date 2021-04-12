---
title: Connect to Bluetooth and USB-C devices
description: Get started connecting to Bluetooth and USB-C devices and accessories from your HoloLens mixed reality devices.
ms.assetid: 01af0848-3b36-4c13-b797-f38ad3977e30
ms.prod: hololens
ms.sitesec: library
author: Teresa-Motiv
ms.author: v-tea
ms.topic: article
ms.localizationpriority: high
ms.date: 03/11/2020
manager: jarrettr
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Connect to Bluetooth and USB-C devices

> [!NOTE]
> External microphones cannot be used. HoloLens 2 uses its built-in [microphone array](hololens2-hardware.md#audio-and-speech).

## Pair Bluetooth devices

HoloLens 2 supports the following classes of Bluetooth devices:

- [HID](https://docs.microsoft.com/windows-hardware/drivers/hid/):
    - Mouse
    - Keyboard
- Audio output (A2DP) devices

HoloLens 2 supports the following Bluetooth APIs:
- GATT [Server](https://docs.microsoft.com/windows/uwp/devices-sensors/gatt-server) and [Client](https://docs.microsoft.com/windows/uwp/devices-sensors/gatt-client)
- [RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm)
>[!IMPORTANT]
> You may have to install corresponding companion apps from Microsoft Store to actually use the HID and GATT devices.

HoloLens (1st gen) supports the following classes of Bluetooth devices:

- Mouse
- Keyboard
- [HoloLens (1st gen) clicker](https://docs.microsoft.com/hololens/hololens1-clicker)

> [!NOTE]
> Other types of Bluetooth devices, such as speakers, headsets, smartphones, and game pads, may be listed as available in HoloLens settings. However, these devices aren't supported on HoloLens (1st gen). For more information, see [HoloLens Settings lists devices as available, but the devices don't work](hololens-FAQ.md#hololens-settings-lists-devices-as-available-but-the-devices-dont-work).

### Pair a Bluetooth keyboard or mouse

1. Turn on your keyboard or mouse, and make it discoverable. To learn how to make the device discoverable, look for information on the device (or its documentation) or visit the manufacturer's website.

1. Use the bloom gesture (HoloLens (1st gen)) or the start gesture (HoloLens 2) to go to **Start**, and then select **Settings**.

1. Select **Devices**, and make sure that Bluetooth is on.  

1. When you see the device name, select **Pair**, and then follow the instructions.

## Disable Bluetooth

This procedure turns off the RF components of the Bluetooth radio and disables all Bluetooth functionality on Microsoft HoloLens.

1. Use the bloom gesture (HoloLens (1st gen)) or the start gesture (HoloLens 2) to go to **Start**, and then select **Settings** > **Devices**.

1. Move the slider switch for **Bluetooth** to the **Off** position.

## HoloLens 2: Connect USB-C devices

HoloLens 2 supports the following classes of USB-C devices:

- Mass storage devices (such as thumb drives)
- Ethernet adapters (including ethernet plus charging)
- USB-C-to-3.5mm digital audio adapters
- USB-C digital audio headsets (including headset adapters plus charging)
- Wired mouse
- Wired keyboard
- Combination PD hubs (USB A plus PD charging)

> [!NOTE]
> In response to customer feedback we have enabled limited support for cellular connectivity tethered directly to the HoloLens via USB-C. See [Connect to Cellular and 5G](hololens-cellular.md) for more information.

### USB-C Hubs

Some users may need to connect multiple devices at once. For users who would like to preview an Insider feature and [use a USB-C microphone](hololens-insider.md#usb-c-external-microphone-support) along with another connected device, USB-C hubs may fit the customer's need. Microsoft has not tested these devices, nor can we recommend any specific brands.

**Requirements for USB-C hub and connected devices:**

- Connected devices must not require a driver to be installed.
- The total power draw of all connected devices must be below 4.5 Watts.

## Connect to Miracast

To use Miracast, follow these steps:

1. Do one of the following:  

   - Open the **Start** menu, and select the display icon.
   - Say "Connect" while you gaze at the **Start** menu.  

1. On the list of devices that appears, select an available device.

1. Complete the pairing to begin projecting.
