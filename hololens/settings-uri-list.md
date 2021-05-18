---
title: Page Settings Visibility
description: Keep up to date with our list of supported URIs for PageVisibilityList and Guide on HoloLens mixed reality devices.
author: evmill
ms.author: v-evmill
ms.date: 10/13/2020
ms.topic: article
keywords: hololens, hololens 2, assigned access, kiosk, settings page
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: widuff
manager: yannisle
appliesto:
- HoloLens 2
---

# Page Settings Visibility

One of the manageable features for HoloLens devices is using the [Settings/PageVisibilityList policy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-pagevisibilitylist) to restrict the pages seen within the Settings app. PageVisibilityList is a policy that allows IT Admins to either prevent specific pages in the System Settings app from being visible or accessible, or to do so for all pages except those specified.

> [!NOTE]
> This feature is only avalible in [Windows Holographic, version 20H2](hololens-release-notes.md#windows-holographic-version-20h2) or higher for HoloLens 2 devices. Please ensure devices you intend to use this for are updated.

The following example illustrates a policy that would allow access only to the about and bluetooth pages, which have URI "ms-settings:network-wifi" and "ms-settings:bluetooth" respectively:
- `showonly:network-wifi;network-proxy;bluetooth`

To set this via a Provisioning Package:

1. While creating your package in Windows Configuration Designer navigate to **Policies > Settings > PageVisibilityList**
1. Enter the string: **`showonly:network-wifi;network-proxy;bluetooth`**
1. Export your Provisioning Package.
1. Apply the package to your device.
For full details on how to create and apply a provisioning package visit [this page](hololens-provisioning.md).

This can be done via Intune using OMA-URI:

1. Create a **Custom policy**.
1. When setting the OMA-URI use the string: **`./Device/Vendor/MSFT/Policy/Config/Settings/PageVisibilityList`**
1. When selecting the data pick choose: **String**
1. When typing the value use: **`showonly:network-wifi;network-proxy;bluetooth`**
1. Make sure to assign the custom device configuration to a group the device is intended to be in.

See [HoloLens MDM configuration](hololens-mdm-configure.md) for more information on Intune groups and device configurations.

Regardless of method chosen your device should now receive the changes and users will be presented with the following Settings App.

![Screenshot of active hours being modified in the Settings app](images/hololens-page-visibility-list.jpg)

To configure the Settings app pages to show or hide your own selection of pages, take a look at the Settings URIs available on HoloLens.

## Settings URIs

HoloLens devices and Windows 10 devices have a different selection of pages within the Settings app. On this page, you will find only the settings that exist on HoloLens.

### Accounts
| Settings page           | URI                                            |
|-------------------------|------------------------------------------------|
| Access work or school | `ms-settings:workplace`                         |
| Iris Enrollment       | `ms-settings:signinoptions-launchirisenrollment` |
| Sign In Options         | ` ms-settings:signinoptions `                   |

### Apps
| Settings page | URI                          |
|---------------|------------------------------|
| Apps & features<sup>2</sup>     | `ms-settings:appsfeatures` <br> |
| Apps & features > Advanced Options <sup>2</sup>     | `ms-settings::appsfeatures-app` <br> |
| Apps & features > Offline Maps <sup>2</sup>     | `ms-settings:maps-maps` <br> |
| Apps & features > Offline Maps > Download maps <sup>2</sup>     | `ms-settings:maps-downloadmaps` <br> |

### Devices
| Settings page | URI                          |
|---------------|------------------------------|
| Bluetooth     | `ms-settings:bluetooth` <br> `ms-settings:connecteddevices` |
| Mouse <sup>2</sup>      | `ms-settings:mouse` <br>  |
| USB <sup>2</sup>      | `ms-settings:usb` <br>  |

### Privacy
| Settings page            | URI                                             |
|--------------------------|-------------------------------------------------|
| Account Info             | `ms-settings:privacy-accountinfo`              |
| App Diagnostics        | `ms-settings:privacy-appdiagnostics`              |
| Background Apps        | `ms-settings:privacy-backgroundapps`              |
| Calendar                 | `ms-settings:privacy-calendar`                    |
| Call History             | `ms-settings:privacy-callhistory`                 |
| Camera                   | `ms-settings:privacy-webcam`                      |
| Contacts                 | `ms-settings:privacy-contacts`                    |
| Diagnostics & Feedback | `ms-settings:privacy-feedback`                    |
| Documents                | `ms-settings:privacy-documents`                   |
| Email                    | `ms-settings:privacy-email`                       |
| File system              | `ms-settings:privacy-broadfilesystemaccess`       |
| General <sup>2</sup>             | `ms-settings:privacy-general`       |
| Ink & typing personalization <sup>2</sup>             | `ms-settings:privacy-speechtyping`       |
| Location                 | `ms-settings:privacy-location`                    |
| Messaging                | `ms-settings:privacy-messaging`                   |
| Microphone               | `ms-settings:privacy-microphone`                  |
| Motion <sup>2</sup>               | `ms-settings:privacy-motion`                  |
| Notifications            | `ms-settings:privacy-notifications`               |
| Other devices            | `ms-settings:privacy-customdevices`               |
| Pictures                 | `ms-settings:privacy-pictures`                    |
| Radios                   | `ms-settings:privacy-radios`                      |
| Screenshot borders <sup>2</sup>             | `ms-settings:privacy-graphicsCaptureWithoutBorder`       |
| Screenshots and apps <sup>2</sup>             | `ms-settings:privacy-graphicsCaptureProgrammatic`       |
| Speech                   | `ms-settings:privacy-speech`                      |
| Tasks                    | `ms-settings:privacy-tasks`                       |
| User movements           | `ms-settings:privacy-backgroundspatialperception` |
| Videos                   | `ms-settings:privacy-videos`                      |
| Voice Activation       | `ms-settings:privacy-voiceactivation`             |

### Network & Internet
| Settings page | URI                              |
|---------------|----------------------------------|
| Airplane Mode <sup>2</sup> | `ms-settings:network-airplanemode`        |
| Proxy | `ms-settings:network-proxy`        |
| VPN   | `ms-settings:network-vpn`          |
| Wi-Fi  | `ms-settings:network-wifi`<br>`ms-settings:network-wifisettings`<br>`ms-settings:network-status`<br>`ms-settings:wifi-provisioning`    |



### System
| Settings page      | URI                                |
|--------------------|------------------------------------|
| Battery <sup>2</sup>           | `ms-settings:batterysaver`<br>|
| Battery <sup>2</sup>           | `ms-settings:batterysaver-settings`<br>|
| Colors             | `ms-settings:colors`<br>`ms-settings:personalization-colors` |
| Holograms <sup>2</sup>  |  `ms-settings:holograms`  |
| Calibration <sup>2</sup> |  `ms-settings:calibration` |
| Notifications & actions  | `ms-settings:notifications`          |
| Shared Experiences | `ms-settings:crossdevice` 
| Sound <sup>2</sup>           | `ms-settings:sound`<br>|
| Sound > App volume and device preference <sup>2</sup>           | `ms-settings:apps-volume`<br>|
| Sound > Manage sound devices <sup>2</sup>           | `ms-settings:sound-devices`<br>|
| Storage            | `ms-settings:storagesense`           |
| Storage > Configue Storage Sense <sup>2</sup>           | `ms-settings:storagepolicies`<br>|

### Time & Language
| Settings page | URI                                           |
|---------------|-----------------------------------------------|
| Date & time <sup>2</sup> | `ms-settings:dateandtime`                  |
| Keyboard <sup>2</sup> | `ms-settings:keyboard`                  |
| Language <sup>2</sup> | `ms-settings:language`                  |
| Language <sup>2</sup> | `ms-settings:regionlanguage-languageoptions`                  |
| Language      | `ms-settings:regionlanguage`<br>`ms-settings:regionlanguage-adddisplaylanguage`<br>`ms-settings:regionlanguage-setdisplaylanguage` |
| Region        | `ms-settings:regionformatting`                  |

### Update & Security
| Settings page                         | URI                                       |
|---------------------------------------|-------------------------------------------|
| Advanced Options                    | `ms-settings:windowsupdate-options`         |
| Reset & Recovery <sup>2</sup>      | `ms-settings:reset`         |
| Windows Insider Program               | `ms-settings:windowsinsider` <br>`ms-settings:windowsinsider-optin`          |
| Windows Update                        | `ms-settings:windowsupdate`<br> `ms-settings:windowsupdate-activehours`  <br> `ms-settings:windowsupdate-history` <br> `ms-settings:windowsupdate-optionalupdates` <br><sup>1</sup>`ms-settings:windowsupdate-options`<br><sup>1</sup>`ms-settings:windowsupdate-restartoptions` |
| Windows Update - Checks for updates | `ms-settings:windowsupdate-action`          |


>  <sup>1</sup> For versions prior to Windows Holographic, version 21H1, the following two URIs do not actually take you to the **Advanced options** or **Options** pages; they will only block or show the main Windows Update page.
> - ms-settings:windowsupdate-options
> - ms-settings:windowsupdate-restartoptions
 
> <sup>2</sup> - Available in Windows Holographic 21H1 or higher.


For a full list of Windows 10 Settings URIs, please visit the [launch settings](https://docs.microsoft.com/windows/uwp/launch-resume/launch-settings-app#ms-settings-uri-scheme-reference) documentation.
