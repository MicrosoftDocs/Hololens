---
title: Network security
description: network security
author: evmill
ms.author: v-evmill
ms.date: 6/30/2020
ms.topic: article
keywords: security, hololens, network, network security
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens 2
---

# Network security

## Network protocols

The outdated NetBIOS (Network Basic Input/Output System) was widely used in the past in LAN scenarios – often for providing name resolution to a computer and shared folders. But over time, NetBIOS proved to be susceptible to multiple attacks, and its relevance decreased in favor of other more secure protocols. To remove this vulnerability issue, HoloLens 2 has eliminated the NetBIOS-related code from the operating system.

TLS (Transport Layer Security) protocols are constantly evolving. To keep up with the various security exploits that have been uncovered in this area, the computing industry has graduated to newer and more effective versions. Due to the time required for all server deployments to adopt the new TLS protocol versions, a fallback mechanism can be implemented that permits the client and servers on different default protocol versions to still be able to communicate during the transition period.

## Secure connectivity 

The Windows Defender Firewall delivers critical functionality to secure device connectivity. With HoloLens 2, the firewall is always enabled and there are no ways to disable it programmatically or through the UI.

Remote access and connection privacy for mobile clients can be assured through the [UWP VPN plug-in platform](https://docs.microsoft.com/uwp/api/Windows.Networking.Vpn?view=winrt-19041). Third-party VPN providers can create their own plug-ins using WinRT APIs which will run within the AppContainer sandbox, eliminating the complexity and issues often associated with writing system-level drivers.
