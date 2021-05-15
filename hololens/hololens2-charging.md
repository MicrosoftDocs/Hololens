---
title: Battery and Charging
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

# Battery and Charging

This page offers details about charging HoloLens 2 and leveraging external battery packs.

## Included Charger

The charger included with HoloLens 2 provides up to 9V @ 2A (18W). When possible, it's highly recommended to charge using the included charger.  

## Specifications

HoloLens 2 can be charged by [USB Power Delivery](https://www.usb.org/usb-charger-pd) sources up to 27 Watts. If the source is able supply at least 10 Watts, HoloLens operating time can be extended (potentially indefinitely for some workloads). 

> [!NOTE]
> Using a USB-A to USB-C charging cable will limit the charge to 7.5 Watts. Operating time will still be extended, but not as long as using USB-C to C.

When HoloLens is in standby mode, 18 Watts is sufficient to reach the maximum charge rate for the internal battery. When HoloLens is in use, the charge rate may be reduced since HoloLens prioritizes operating over charging.

> [!TIP]
> HoloLens 2 charge ports support 5V/1.5A minimum and will not be damaged when using a lessor charge port. The charge port may overheat if it does not implement the BC1.2 DCP specification correctly

## External Battery Packs

Battery packs that meet the specifications above can be used with HoloLens 2. However, note that some USB-C battery packs recharge and provide power through the same USB-C port. It's important that these battery packs implement [TRY.SRC](https://www.usb.org/sites/default/files/USB%20Type%20C%20Functional%20Test%20Specification%202019%2007%2025.pdf) to ensure they charge HoloLens rather than charge from it. 

## Managing Heat

As with any device, charging HoloLens generates heat. The more rapid the charge, the more heat is generated. Also, starting a charge at a lower battery level will generate more heat than starting a charge when the battery is mostly full. Customers who need to operate HoloLens for extended periods of time in hot environments can leverage the following techniques:

- It's OK to connect HoloLens 2 to an external power source even when the internal battery is fully charged.
- When an external battery is depleted, HoloLens will continue operating on its internal battery.    
- If heat is still an issue after following steps above, consider using a charger or battery pack that limits charging to 1.5A. Note that this option won't provide as much operating time since the internal battery will still slowly deplete.

## Troubleshooting

### General
Try charging with a USB-A to USB-C cable.

### HoloLens Charges External Battery
If HoloLens 2 charges an external battery rather than being charged by it, this indicates that the battery doesn't implement [TRY.SRC](https://usb.org/document-library/usb-type-cr-cable-and-connector-specification-revision-20). Try switching to a newer battery pack to resolve the issue.
