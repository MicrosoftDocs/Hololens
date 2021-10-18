---
title: HoloLens 2 Battery and Charging
description: How to charge your HoloLens and use external battery packs.
ms.assetid: E0AB903E-454E-46F6-AB25-4DFA0A475B0C
ms.prod: hololens
ms.sitesec: library
author: jbienzms
ms.author: jbienz
ms.topic: article
ms.localizationpriority: high
ms.date: 05/14/2021
manager: evmill
appliesto:
- HoloLens 2
---

# HoloLens 2 Battery and Charging

This page offers details about charging HoloLens 2 and using external battery packs.

## Charging the device

Use the [charger and the USB Type-C cable](https://www.microsoft.com/en-us/p/microsoft-hololens-2-usb-c-charger-cable/8vj21f2z8pk5?rtc=1) that came with the HoloLens 2 as that is the best way to charge your device. The charger included with HoloLens 2 provides up to 9V @ 2A (18W). Along with the supplied wall charger, HoloLens 2 devices can charge the battery to full in less than 65 minutes when the device is in standby. If those accessories aren't available, make sure the charger that's available can support at least 15W of power.

> [!NOTE]
> If possible, avoid using a PC to charge the device over USB, which is slow.

## Checking the battery charge level
If the device is correctly booted and running, there are three ways to check the battery charge level:

- From the main menu of the HoloLens device UI.
- View the LED close to the power button (for a 40-percent charge, you should see at least two solid LEDs).
    - When the device is charging, the battery indicator lights up to indicate the current level of charge.  The last light will fade in and out to indicate active charging.
    - When your HoloLens is on, the battery indicator displays the battery level in five increments.
    - When only one of the five lights is on, the battery level is below 20 percent.
    - If the battery level is critically low and you try to turn on the device, one light will blink briefly, then go out.
- On your host PC, open **File Explorer** and look for your HoloLens 2 device on left side under **This PC**. Right-click the device, and select **Properties**. A dialog box will show the battery charge level.

   ![A HoloLens 2 properties screen shows battery change level.](images/ResetRecovery2.png)

## Alternative charging specifications

HoloLens 2 can be charged by [USB Power Delivery](https://www.usb.org/usb-charger-pd) sources up to 27 Watts. If the source is able to supply at least 10 Watts, HoloLens operating time can be extended (potentially indefinitely for some workloads). 

> [!NOTE]
> Using a USB-A to USB-C charging cable will limit the charge to 7.5 Watts. Operating time will still be extended, but not as long as using USB-C to C.

When HoloLens is in standby mode, 18 Watts is sufficient to reach the maximum charge rate for the internal battery. When HoloLens is in use, the charge rate may be reduced since HoloLens prioritizes operating over charging.

> [!IMPORTANT]
> It's recommended that HoloLens 2 be charged at 5V/1.5A minimum. Chargers that can't supply at least 5V/1.5A should not be used. 

### External Battery Packs

Battery packs that meet the specifications above can be used with HoloLens 2. However, note that some USB-C battery packs recharge and provide power through the same USB-C port. It's important that these battery packs implement [TRY.SRC](https://usb.org/document-library/usb-type-cr-cable-and-connector-specification-revision-20) to ensure they charge HoloLens rather than charge from it. 

### Managing Heat

As with any device, charging HoloLens generates heat. The more rapid the charge, the more heat is generated. Also, starting a charge at a lower battery level will generate more heat than starting a charge when the battery is mostly full. Customers who need to operate HoloLens for extended periods of time in hot environments can use the following techniques:

- It's OK to connect HoloLens 2 to an external power source even when the internal battery is fully charged.
- When an external battery is depleted, HoloLens will continue operating on its internal battery.    
- If heat is still an issue after following steps above, consider using a charger or battery pack that limits charging to 1.5A. Note that this option won't provide as much operating time since the internal battery will still slowly deplete.

## Troubleshooting


### HoloLens Charges External Battery
If HoloLens 2 charges an external battery rather than being charged by it, this indicates that the battery doesn't implement [TRY.SRC](https://usb.org/document-library/usb-type-cr-cable-and-connector-specification-revision-20). Switching to a newer battery pack is the recommended way to solve this issue, but alternatively you can try switching to a USB-A to USB-C cable. Keep in mind this will limit the charging rate to 7.5 watts.
