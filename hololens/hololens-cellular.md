---
title: Connect to Cellular and 5G
description: Connecting to cellular networks from your HoloLens mixed reality devices.
ms.assetid: f1aaadce-8762-41f8-bfeb-3b6067a2ec78
ms.prod: hololens
ms.sitesec: library
author: jbienzms
ms.author: jbienz
ms.topic: article
ms.localizationpriority: high
ms.date: 02/24/2021
manager: evmill
appliesto:
- HoloLens 2
---

# Connect to Cellular and 5G

HoloLens 2 supports two methods for connecting to cellular and 5G networks:

- An ad hoc WiFi network provided by the cellular device, commonly referred to as a "Hotspot"
- Limited support for USB-C tethered devices

## Hotspot (WiFi)

Most cellular connectivity needs can be met with a hotspot. HoloLens 2 WiFi supports 802.11ac, which can provide the bandwidth and latency requirements necessary for most common use cases. WiFi is also cable-free and offers compatibility with the largest number of cellular devices.

### Connecting to a Hotspot

1. Consult your device's manual on how to enable its hotspot mode.
1. Enable hotspot mode, supplying a name for the network as well as a known password.
1. In HoloLens 2 Network settings, locate the WiFi network created in step 2 and join it.

## USB-C Tethering

USB-C tethering can provide lower latency for advanced workloads that need it. [Azure Remote Rendering](https://azure.microsoft.com/services/remote-rendering), for example, can benefit from tethering. Note that tethering requires a cable between the cellular device and HoloLens, and tethering is supported by a limited number of devices.

### USB-C compatibility

Devices that present themselves as an ethernet adaptor can be used with Windows Holographic version 2004 and later.

Devices that do not present themselves as an ethernet adapter must support the generic Microsoft [RNDIS](https://docs.microsoft.com/windows-hardware/drivers/network/overview-of-remote-ndis--rndis-) driver. Please consult your device's manufacturer for details on whether it supports the generic Microsoft RNDIS driver.

Devices that are not RNDIS compatible, or require a driver or application to be installed, are not supported.

While Microsoft does not maintain a list of compatible devices, there is a community discussion on the topic [here](https://aka.ms/HLCommunityCell).

### Connecting to a tethered device

1. Consult your device's manual on how to enable data sharing over USB. This setting is often referred to as "USB Tethering", "Data Sharing" or "USB Modem".
1. Enable data sharing over USB.
1. Connect your device to the HoloLens USB-C port.
1. In HoloLens 2 Network settings, the device will automatically appear as an Ethernet connection.
