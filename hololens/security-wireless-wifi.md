---
title: Wireless and Wi-Fi
description: Wireless and Wi-Fi
author: jbennett
ms.date: 6/30/2020
ms.topic: article
keywords: security, hololens, Wireless, Wi-Fi
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
manager: yannisl
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Wireless and Wi-Fi

HoloLens 2 Wireless LAN connectivity supports an impressive range of the latest Wi-Fi security standards, such as:
  * WPA2 (Wi-Fi Protected Access 2)  
  * TEAP (Tunnel Extensible Authentication Protocol)  
  * OWE (Opportunistic Wireless Encryption)

TEAP, the next generation of enterprise network authentication, provides the ability to securely chain multiple credentials into a single transaction.  This allows administrators to enforce a stronger security stance – one that requires valid identities for both machine and user during the same authentication transaction.

HoloLens 2 has modern wireless and Wi-Fi protocols that enable customers with maximum support. The HoloLens 2 radio is a Qualcomm WCN3990 solution delivering a premium radio experience. The Wi-Fi supported is 802.11 ac/n. The frequency range is not user configurable and depends on the country of use. In the United States, Wi-Fi uses both 2.4GHz (1-11) channels and 5GHz (36-64, 100-165) channels. Neither user nor device can make allow/deny lists for specific frequencies. Bluetooth SIC Core 5.0 has a dedicated 2.4GHz antenna for Bluetooth which is not shared with Wi-Fi. HoloLens 2’s software stack supports several protocols and profiles including HID, HOGP, A2DP, and GATT. 

IT admins can: 
  * Enable or restrict  [Bluetooth access](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowbluetooth)
  * Set [local Bluetooth device names](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#bluetooth-localdevicename)
  * Allow [devices to be discoverable](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#bluetooth-allowdiscoverablemode)
  * Allow/disallow [Wi-Fi connections](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi#wifi-allowwifi) 
  * Allow or disallow [connecting to Wi-Fi outside of MDM server-installed networks](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi#wifi-allowmanualwificonfiguration)
