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

## Specifications

HoloLens 2 can be charged by [USB Power Delivery](https://www.usb.org/usb-charger-pd) sources at up to 3A @ 5V or 2A @ 9V. If the source is able supply at least 10 Watts, HoloLens operating time can be greatly extended (up to indefinite for some workloads).

Note that using a USB-A to USB-C charging cable will limit current to 7.5 Watts. Operating time will still be extended, but not as long as using USB-C to C.

HoloLens 2 can charge with as little as 1.5A, but charging below 1.5A is not supported. Attempting to charge HoloLens 2 with less than 1.5A can damage the HoloLens, the charger, or both.

## Included Charger

The charger included with HoloLens 2 provides up to 9V @ 2A (18W). When possible, it's highly recommended to charge using the included charger.  

## External Battery Packs

Battery packs that meet the specifications above can be used with HoloLens 2. However, note that some USB-C battery packs recharge and provide power through the same USB-C port. It's important that these battery packs implement [TRY.SRC](https://www.usb.org/sites/default/files/USB%20Type%20C%20Functional%20Test%20Specification%202019%2007%2025.pdf) to indicate they will provide a charge to HoloLens rather than receive it. Most battery packs produced in 2019 and later implement this feature.

## Managing Heat

As with any device, charging HoloLens generates heat. The more rapid the charge, the more heat is generated. Also, starting a charge at a lower battery level will generate more heat than starting a charge when the battery is mostly full. Customers who need to operate HoloLens for extended periods of time in hot environments can leverage the following techniques:

- Begin charging HoloLens 2 when the internal battery is at 80% charge or higher. When the internal battery has at least 80% charge, it will trickle charge and generate much less heat.
- It's OK to connect HoloLens 2 to an external power source even when the internal battery is fully charged.
- When an external battery is depleted, HoloLens will continue operating on its internal battery.    
- After following the steps above, if heat is still an issue consider using a charger or battery pack that limits charging to 1.5A. Operating time may be reduced (since the internal battery will slowly deplete), but less heat will also be generated in the process.   

## Troubleshooting

### HoloLens Charges External Battery
If HoloLens 2 charges an external battery rather than being charged by it, this indicates that the battery doesn't implement [TRY.SRC](https://www.usb.org/sites/default/files/USB%20Type%20C%20Functional%20Test%20Specification%202019%2007%2025.pdf). Try switching to a newer battery pack to resolve the issue.