---
title: State separation and isolation
description: State separation and isolation
author: jbennett
ms.author: v-evmill
ms.date: 6/30/2020
ms.topic: article
keywords: security, hololens, State separation, State separation and isolation, hololens 2, hololens2 security, security overview, security architecture, architecture, hololens 2 architecture
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
manager: yannisl
appliesto:
- HoloLens 2
---

# State separation and isolation

State separation and isolation protects critical portions of the Hololens 2 operating system from change – such as those required for the operating system to boot into a trusted state. With isolation technology, untrusted apps are moved to an isolated sandbox environment, to ensure that they do not affect system security.

## State separation

State separation on HoloLens 2 vastly improves security and serviceability (updating) and helps protect your application data.  State separation works as follows:
  * The core operating system is stored in the core operating system volume (trusted or verified Microsoft OS updating the operating system).
  * The portions of the operating system that can be changed at run time (such as downloadable drivers and configurations), use further state separation to partition the data, and to store it in secure, separate storage locations.
  * Each secure storage location has distinct security policies associated with it, offering varied security advantages as detailed in the following section.

## State separation benefits

  * Security: The state separation featured in HoloLens 2 significantly improves platform integrity, malware resistance and user data protection. By separating the unalterable part of the operating system and making it read-only or integrity protected, state separation makes it extremely difficult for malware to persist across a cold reboot. 
  * Updates: With HoloLens 2, once the core operating system is unmodifiable and has been cleanly separated from the rest of the data on the device, updates become simple and reliable.  In addition, state separation lays the vital groundwork for dramatically faster updates, which permits the operating system to be replaced in a single step (atomic unit).
  * Device reset: HoloLens 2 reset clears user generated data and user app data on the device – including internal and external storage locations. It preserves the current OS apps and security critical apps, and the current Microsoft and OEM customized apps (Preinstalled). These Preinstalled apps can be rehydrated on the device after reset completes

### State separation states

State separation ensures the operating system can only be changed by Microsoft trusted device components and only high-value state is allowed to persist across reboots; other system state exists only for the duration of the boot session and is discarded after a reboot. Having state separation rapidly returns the device back to factory state. Windows Holographic for Business states can be divided into these distinct categories:
  * Core operating system – Unalterable state
  * Operating System Data – Alterable state 
  * User Data – Alterable state

Each of these HoloLens 2 operating states is described in the following section.

#### Core operating system

An immutable state is comprised of executable files and data that are unalterable and can only be changed by Microsoft during the installation of updates. During such an update of the core operating system, a new image containing the latest desired operating state is enabled.
The unalterable state is marked as read-only (or is otherwise integrity-protected), preventing persistence of any malware with elevated privileges. The following executable files and data are protected in the immutable state:
  * Windows Holographic inbox drivers
  * Operating system binaries
  * Windows inbox drivers
  * Static Windows Holographic settings stored in Windows registry hive (HKLM)
    * Example: HKLM stores the configuration information for the apps installed on a machine. It also stores information to detect hardware and the corresponding drivers.
By protecting these in the immutable (integrity and read-only protected) state, we ensure that the core operating system always boots into a trusted state. Additionally, when a device is reset, we can ensure that the device boots only into the components that are on this immutable section. 

#### Operating system data 

It is important to note that executable files and data that are changeable at runtime (and are not critical to the operating system function), can be discarded and re-created when the data is corrupted or compromised. 
A high-value alterable state is either functionally required to persist by the operating system, or expected to persist across operating system shutdown, and/or across reboots by supported Windows operating system and device scenarios. Examples of high-value mutable state are:
  * IT Admin-configured global device settings, such as disabling the location for all users.
  * Wi-fi network connection access data-device-remembered networks and associated connection passwords.
  * Crash dumps including settings, logs.
  * Drivers downloaded on-demand for newly discovered devices.
A high-value alterable state on HoloLens 2 resides on the operating system Data security location, either as a saved file on disk or in a persisted registry hive.

#### User data

The last category of state represents user data produced or persisted by UWP applications or the operating system. All known user folders such as Downloads, Documents, Videos, user profiles and HKEY_CURRENT_USER hive are also stored in this location. This data cannot be extracted without proper credentials; to learn more about how your data is protected, see [Encryption and Data Protection](security-encryption-data-protection.md).

##	Isolation

To achieve this balance, HoloLens 2 has a core operating system that is used for primary functions such as booting up, hardware control, logging in etc. There are only two sets of applications that run on the core operating system – pre-installed applications and UWP apps.

## Code signing

Digitally signing code allows substantiation that executables and scripts have not been modified since they were signed by a trusted source therefore providing authenticity and integrity. The authorities that HoloLens 2 trusts by default are Microsoft and Microsoft Store. IT administrators can add new certificates to the device through the [ClientCertificateInstall](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp) and [RootCATrustedCertificates](https://docs.microsoft.com/windows/client-management/mdm/rootcacertificates-csp) CSPs. They can also use the [AllowAllTrustedApps policy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowalltrustedapps) to trust additional sideloaded or [Line-of-business apps](https://docs.microsoft.com/intune/apps/lob-apps-windows). Certificates reside in the local machine certificate store which is stored in HKLM/Root if using “Device” or in HKCU if using “User”.

## Defender protections
HoloLens 2 uses Microsoft services to give users an advanced level of security:

* [Defender SmartScreen](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) is automatically enabled on Windows Holographic by the OS and protects against phishing and malware, as well as the downloading of potentially malicious files, on Edge. It cannot be turned off by the user but can be disabled through policy.

* [Defender Firewall](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) blocks unauthorized network traffic from flowing to and from your device. It is enabled by default and not configurable by the customer through local actions or policy. 

* [Windows Defender Application Control](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/wdac-and-applocker-overview):  HoloLens 2 supports WDAC which allows IT admin to push application control policies onto the device. More info can be found in [Use WDAC on HoloLens 2 devices with MSFT Intune](https://docs.microsoft.com/mem/intune/configuration/custom-profile-hololens). 

IT admins can manage SmartScreen behavior through [AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) and browser behavior through [these policies](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-hololens2). 

