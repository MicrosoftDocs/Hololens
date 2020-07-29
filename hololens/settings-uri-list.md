---
title: Settings URIs
description: List of HoloLens supported URIs for PageVisibilityList
author: evmill
ms.author: v-evmill
ms.date: 8/1/2020
ms.topic: article
keywords: hololens, hololens 2, assigned access, kiosk
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: widuff
manager: yannisle
appliesto:
- HoloLens 2
---

# Settings URIs

One of the manageable features for HoloLens devices is using the [Settings/PageVisibilityList policiy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-pagevisibilitylist) to restrict the pages seen within the Settings app. HoloLens devices and Windows 10 devices have a different selection of pages within the Settings app. On this page you will find only the settings that exist on HoloLens. 

## Accounts

|Settings page| URI |
|-------------|-----|
| Access work or school | ms-settings:workplace |
| Email & app accounts  | ms-settings:emailandaccounts |
| Sign-in options | ms-settings:signinoptions<br>ms-settings:signinoptions-dynamiclock |
| Other users | ms-settings:otherusers |

## Devices

|Settings page| URI |
|-------------|-----|
| Devices | ms-settings:bluetooth |

## Ease of Access

|Settings page| URI |
|-------------|-----|
| Ease of Access | ms-settings:easeofaccess-audio |

## Network & internet

|Settings page| URI |
|-------------|-----|
| Proxy | ms-settings:network-proxy |
| VPN | ms-settings:network-vpn |
| Wi-Fi | ms-settings:network-wifi |

## Privacy

|Settings page| URI |
|-------------|-----|
| General | ms-settings:privacy or ms-settings:privacy-general |
| Speech | ms-settings:privacy-speech |
| Diagnostics & feedback | ms-settings:privacy-feedback |
| Location | ms-settings:privacy-location |
| Camera | ms-settings:privacy-webcam |
| Eye tracker | ms-settings:privacy-eyetracker |
| Microphone | ms-settings:privacy-microphone |
| Voice activation | ms-settings:privacy-voiceactivation |
| Notifications | ms-settings:privacy-notifications |
| Account info | ms-settings:privacy-accountinfo |
| Contacts | ms-settings:privacy-contacts |
| Calendar | ms-settings:privacy-calendar |
| Call history | ms-settings:privacy-callhistory |
| Email | ms-settings:privacy-email |
| Tasks | ms-settings:privacy-tasks |
| Messaging | ms-settings:privacy-messaging |
| Radios | ms-settings:privacy-radios |
| Other devices | ms-settings:privacy-customdevices |
| Background Apps | ms-settings:privacy-backgroundapps |
| App diagnostics | ms-settings:privacy-appdiagnostics |
| Advertising ID | ms-settings:privacy-advertisingid |
| Documents | ms-settings:privacy-documents |
| Pictures | ms-settings:privacy-pictures |
| Videos | ms-settings:privacy-videos |
| File system | ms-settings:privacy-broadfilesystemaccess |
| Enviorment | ???????????????????????????????????? |
| User movements | ms-settings:privacy-backgroundspatialperception |

??? might be ms-settings:privacy-webcam

## System

|Settings page| URI |
|-------------|-----|
| About | ms-settings:about |
| Notifications & actions |	ms-settings:notifications |
| Storage | ms-settings:storagesense |
| Holograms | ???????????????????? |
| Calibration | ???????????????? |
| Shared experiences | ms-settings:crossdevice |
| Colors | ms-settings:colors |

Holograms page?
Calibration page?

## Time and language

|Settings page| URI |
|-------------|-----|
| Date & time | ms-settings:dateandtime |
| Region | ms-settings:regionformatting |
| Language | ms-settings:regionlanguage<br/>ms-settings:regionlanguage-adddisplaylanguage<br/>ms-settings:regionlanguage-setdisplaylanguage |
| Keyboard | ms-settings:keyboard |

Will need to ask about language 

## Update & security

|Settings page| URI |
|-------------|-----|
| Windows Update | ms-settings:windowsupdate<br>ms-settings:windowsupdate-action |
| Windows Update-Advanced options | ms-settings:windowsupdate-options |
| Windows Update-Restart options | ms-settings:windowsupdate-restartoptions |
| Change active hours | ?????????????????????? |
| Recovery | ms-settings:recovery |
| Certificates | ??????????????? |
| Troubleshoot | ms-settings:troubleshoot |
| For developers | ms-settings:developers |
| Windows Insider Program | ms-settings:windowsinsider (only present if user is enrolled in WIP)<br/>ms-settings:windowsinsider-optin |

Will need to verify change active hours with Shrivaths.
Will need to verify certificates with Ezeugo.


