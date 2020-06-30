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

Windows Holographic for Business Wireless LAN connectivity supports an impressive range of the latest Wi-Fi security standards, such as:
  * WPA2 (Wi-Fi Protected Access 2)  
  * TEAP (Tunnel Extensible Authentication Protocol)  
  * OWE (Opportunistic Wireless Encryption)

WPA3 is a step forward from the older WPA2 standard, with protection against brute force password attacks, and protected management frames enforcement. WPA3-Personal prevents a known WPA2 Pre-Shared Key weakness that allowed attackers to decrypt traffic if they gained access to the Wi-Fi password. Now enterprises can have the benefits of WPA3-personal, with the addition of stronger 192-bit encryption to help secure their wireless networks.

TEAP, the next generation of enterprise network authentication, provides the ability to securely chain multiple credentials into a single transaction.  This allows administrators to enforce a stronger security stance – one that requires valid identities for both machine and user during the same authentication transaction.

Windows Holographic for Business further hardens the security of the guest operating system by restricting the ability to call into the Wi-Fi APIs. Apps running in containers can only access the query functionality, while the set options cannot be accessed.  Consequently, the threats of random applications modifying the Wi-Fi configuration are mitigated.

HoloLens 2 has modern wireless and Wi-Fi protocols that enable customers with maximum support. The HoloLens 2 radio is a Qualcomm WCN3990 solution delivering a premium radio experience. The Wi-Fi supported is 802.11 ac/n. The frequency range is not user configurable and depends on the country of use. In the United States, Wi-Fi uses both 2.4GHz (1-11) channels and 5GHz (36-64, 100-165) channels. Neither user nor device can make allow/deny lists for specific frequencies. Bluetooth SIC Core 5.0 has a dedicated 2.4GHz antenna for Bluetooth which is not shared with Wi-Fi. HoloLens 2’s software stack supports several protocols and profiles including HID, HOGP, A2DP, and GATT. 

IT admins can: 
  * enable or restrict  [Bluetooth access](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowbluetooth)
  * set [local Bluetooth device names](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#bluetooth-localdevicename)
  * allow [devices to be discoverable](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#bluetooth-allowdiscoverablemode)
  * allow/disallow [Wi-Fi connections](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi#wifi-allowwifi) 
  * allow or disallow [connecting to Wi-Fi outside of MDM server-installed networks](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi#wifi-allowmanualwificonfiguration)
