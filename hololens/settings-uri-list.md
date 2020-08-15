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
| Settings page           | URI                                            |
|-------------------------|------------------------------------------------|
| Sign In Options         | ms-settings:signinoptions                      |
| Iris Enrollment       | ms-settings:signinoptions-launchirisenrollment |
| Access work or school | ms-settings:workplace                          |

## Devices
| Settings page | URI                          |
|---------------|------------------------------|
| Bluetooth     | ms-settings:bluetooth <br> ms-settings:connecteddevices |

## Privacy
| Settings page            | URI                                             |
|--------------------------|-------------------------------------------------|
| Account Info             | ms-settings:privacy-accountinfo                 |
| App Diagnostics        | ms-settings:privacy-appdiagnostics              |
| Background Apps        | ms-settings:privacy-backgroundapps              |
| User movements           | ms-settings:privacy-backgroundspatialperception |
| File system              | ms-settings:privacy-broadfilesystemaccess       |
| Calendar                 | ms-settings:privacy-calendar                    |
| Call History             | ms-settings:privacy-callhistory                 |
| Contacts                 | ms-settings:privacy-contacts                    |
| Other devices            | ms-settings:privacy-customdevices               |
| Documents                | ms-settings:privacy-documents                   |
| Email                    | ms-settings:privacy-email                       |
| Diagnostics & Feedback | ms-settings:privacy-feedback                    |
| Location                 | ms-settings:privacy-location                    |
| Messaging                | ms-settings:privacy-messaging                   |
| Microphone               | ms-settings:privacy-microphone                  |
| Notifications            | ms-settings:privacy-notifications               |
| Pictures                 | ms-settings:privacy-pictures                    |
| Radios                   | ms-settings:privacy-radios                      |
| Speech                   | ms-settings:privacy-speech                      |
| Tasks                    | ms-settings:privacy-tasks                       |
| Videos                   | ms-settings:privacy-videos                      |
| Voice Activation       | ms-settings:privacy-voiceactivation             |
| Camera                   | ms-settings:privacy-webcam                      |

## Network & Internet
| Settings page | URI                              |
|---------------|----------------------------------|
| Wi-Fi  | ms-settings:network-wifi<br>ms-settings:network-wifisettings<br>ms-settings:network-status<br>ms-settings:wifi-provisioning    |
| VPN   | ms-settings:network-vpn          |
| Proxy | ms-settings:network-proxy        |

## System
| Settings page      | URI                                |
|--------------------|------------------------------------|
| Shared Experiences | ms-settings:crossdevice            |
| Colors             | ms-settings:colors<br>ms-settings:personalization-colors |
| AppsNotifications  | ms-settings:notifications          |
| Storage            | ms-settings:storagesense           |

## Time & Language
| Settings page | URI                                           |
|---------------|-----------------------------------------------|
| Region        | ms-settings:regionformatting                  |
| Language      | ms-settings:regionlanguage<br>ms-settings:regionlanguage-adddisplaylanguage<br>ms-settings:regionlanguage-setdisplaylanguage |

## Update & Security
| Settings page                         | URI                                       |
|---------------------------------------|-------------------------------------------|
| Windows Insider Program               | ms-settings:windowsinsider <br>ms-settings:windowsinsider-optin          |
| Windows Update                        | ms-settings:windowsupdate<br> ms-settings:windowsupdate-activehours  <br> ms-settings:windowsupdate-history <br> ms-settings:windowsupdate-optionalupdates <br><sup>1</sup>ms-settings:windowsupdate-options<br><sup>1</sup>ms-settings:windowsupdate-restartoptions |
| Windows Update - Checks for updates | ms-settings:windowsupdate-action          |
| Advanced Options                    | ms-settings:windowsupdate-options         |

> [!NOTE]
>  1 The following two URI do not actually take you to the Advanced options or Options page page, it will only block / show the main Windows Update page. 
> - ms-settings:windowsupdate-options
> - ms-settings:windowsupdate-restartoptions 

For a full list of Windows 10 Settings URIs, please visit [here](https://docs.microsoft.com/windows/uwp/launch-resume/launch-settings-app#ms-settings-uri-scheme-reference). 
