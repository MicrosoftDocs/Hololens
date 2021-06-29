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


## Examples
Pages are identified by a shortened version of the published URIs, which is the URI minus the "ms-settings:" prefix.

The following example illustrates a policy that would allow access only to the about and bluetooth pages, which have URI "network-wifi" and "bluetooth" respectively:
- `showonly:network-wifi;network-proxy;bluetooth`

The following example illustrates a policy that would hide the OS Reset page:
- `hide:reset`


## Deploying this policy via Intune

These are the configuration values that will be supplied to Intune:

**Name:** An admin preferred display name for the profile
**OMA-URI:** The fully qualified URI of the setting page including its [scope](/windows/client-management/mdm/policy-configuration-service-provider). This examples on this page are using the `./Device` scope.
**Value:** A string value that indicates whether to hide or show *only* the specified pages. Possible values are `hide:<pagename>` and `showonly:<pagename>`. Multiple pages can be specified by separating them with a semicolon, and a listing of common pages can be found below.

1. Create a **Custom policy**.
1. When setting the **OMA-URI** enter the fully scoped URI. For example: **`./Device/Vendor/MSFT/Policy/Config/Settings/PageVisibilityList`**
1. When selecting the data pick choose: **String**
1. When specifying **Value** use the guidance above. For example: **`showonly:network-wifi;network-proxy;bluetooth`** or **`hide:reset`** 
> [!IMPORTANT]
> Make sure to assign the custom device configuration to a group the device is intended to be in. If this step is not performed, the policy will be pushed but won't be applied.

See [HoloLens MDM configuration](hololens-mdm-configure.md) for more information on Intune groups and device configurations.


## Deploying this policy via a Provisioning Package

These are the configuration values that will be specified in Windows Configuration Designer:

**Value:** A string value that indicates whether to hide or show *only* the specified pages. Possible values are `hide:<pagename>` and `showonly:<pagename>`. Multiple pages can be specified by separating them with a semicolon, and a listing of common pages can be found below.


1. While creating your package in Windows Configuration Designer navigate to **Policies > Settings > PageVisibilityList**
1. Enter the string: **`showonly:network-wifi;network-proxy;bluetooth`**
1. Export your Provisioning Package.
1. Apply the package to your device.
For full details on how to create and apply a provisioning package visit [the HoloLens provisioning page](hololens-provisioning.md).


Regardless of method chosen your device should now receive the changes and users will be presented with the following Settings App.

![Screenshot of active hours being modified in the Settings app](images/hololens-page-visibility-list.jpg)

To configure the Settings app pages to show or hide your own selection of pages, take a look at the Settings URIs available on HoloLens.

## Settings URIs

HoloLens devices and Windows 10 devices have a different selection of pages within the Settings app. On this page, you will find only the settings that exist on HoloLens.

### Accounts
| Settings page           | URI                                            |
|-------------------------|------------------------------------------------|
| Access work or school | `workplace`                         |
| Iris Enrollment       | `signinoptions-launchirisenrollment` |
| Sign In Options         | ` signinoptions `                   |

### Apps
| Settings page | URI                          |
|---------------|------------------------------|
| Apps & features <sup>2</sup>     | `appsfeatures` <br> |
| Apps & features > Advanced Options <sup>2</sup>     | `appsfeatures-app` <br> |
| Apps & features > Offline Maps <sup>2</sup>     | `maps-maps` <br> |
| Apps & features > Offline Maps > Download maps <sup>2</sup>     | `maps-downloadmaps` <br> |

### Devices
| Settings page | URI                          |
|---------------|------------------------------|
| Bluetooth     | `bluetooth` <br> `connecteddevices` |
| Mouse <sup>2</sup>      | `mouse` <br>  |
| USB <sup>2</sup>      | `usb` <br>  |

### Privacy
| Settings page            | URI                                             |
|--------------------------|-------------------------------------------------|
| Account Info             | `privacy-accountinfo`              |
| App Diagnostics        | `privacy-appdiagnostics`              |
| Background Apps        | `privacy-backgroundapps`              |
| Calendar                 | `privacy-calendar`                    |
| Call History             | `privacy-callhistory`                 |
| Camera                   | `privacy-webcam`                      |
| Contacts                 | `privacy-contacts`                    |
| Diagnostics & Feedback | `privacy-feedback`                    |
| Documents                | `privacy-documents`                   |
| Email                    | `privacy-email`                       |
| File system              | `privacy-broadfilesystemaccess`       |
| General <sup>2</sup>             | `privacy-general`       |
| Ink & typing personalization <sup>2</sup>             | `privacy-speechtyping`       |
| Location                 | `privacy-location`                    |
| Messaging                | `privacy-messaging`                   |
| Microphone               | `privacy-microphone`                  |
| Motion <sup>2</sup>               | `privacy-motion`                  |
| Notifications            | `privacy-notifications`               |
| Other devices            | `privacy-customdevices`               |
| Pictures                 | `privacy-pictures`                    |
| Radios                   | `privacy-radios`                      |
| Screenshot borders <sup>2</sup>             | `privacy-graphicsCaptureWithoutBorder`       |
| Screenshots and apps <sup>2</sup>             | `privacy-graphicsCaptureProgrammatic`       |
| Speech                   | `privacy-speech`                      |
| Tasks                    | `privacy-tasks`                       |
| User movements           | `privacy-backgroundspatialperception` |
| Videos                   | `privacy-videos`                      |
| Voice Activation       | `privacy-voiceactivation`             |

### Network & Internet
| Settings page | URI                              |
|---------------|----------------------------------|
| Airplane Mode <sup>2</sup> | `network-airplanemode`        |
| Proxy | `network-proxy`        |
| VPN   | `network-vpn`          |
| Wi-Fi  | `network-wifi`<br>`network-wifisettings`<br>`network-status`<br>`wifi-provisioning`    |



### System
| Settings page      | URI                                |
|--------------------|------------------------------------|
| Battery <sup>2</sup>           | `batterysaver`<br>|
| Battery <sup>2</sup>           | `batterysaver-settings`<br>|
| Colors             | `colors`<br>`personalization-colors` |
| Holograms <sup>2</sup>  |  `holograms`  |
| Calibration <sup>2</sup> |  `calibration` |
| Notifications & actions  | `notifications`          |
| Shared Experiences | `crossdevice` 
| Sound <sup>2</sup>           | `sound`<br>|
| Sound > App volume and device preference <sup>2</sup>           | `apps-volume`<br>|
| Sound > Manage sound devices <sup>2</sup>           | `sound-devices`<br>|
| Storage            | `storagesense`           |
| Storage > Configure Storage Sense <sup>2</sup>           | `storagepolicies`<br>|

### Time & Language
| Settings page | URI                                           |
|---------------|-----------------------------------------------|
| Date & time <sup>2</sup> | `dateandtime`                  |
| Keyboard <sup>2</sup> | `keyboard`                  |
| Language <sup>2</sup> | `language`                  |
| Language <sup>2</sup> | `regionlanguage-languageoptions`                  |
| Language      | `regionlanguage`<br>`regionlanguage-adddisplaylanguage`<br>`regionlanguage-setdisplaylanguage` |
| Region        | `regionformatting`                  |

### Update & Security
| Settings page                         | URI                                       |
|---------------------------------------|-------------------------------------------|
| Advanced Options                    | `windowsupdate-options`         |
| Reset & Recovery <sup>2</sup>      | `reset`         |
| Windows Insider Program               | `windowsinsider` <br>`windowsinsider-optin`          |
| Windows Update                        | `windowsupdate`<br> `windowsupdate-activehours`  <br> `windowsupdate-history` <br> `windowsupdate-optionalupdates` <br><sup>1</sup>`windowsupdate-options`<br><sup>1</sup>`windowsupdate-restartoptions` |
| Windows Update - Checks for updates | `windowsupdate-action`          |


- <sup>1</sup> - For versions prior to Windows Holographic, version 21H1, the following two URIs do not actually take you to the **Advanced options** or **Options** pages; they will only block or show the main Windows Update page.
  -  windowsupdate-options
  -  windowsupdate-restartoptions

- <sup>2</sup> - Available in Windows Holographic 21H1 or higher.


For a full list of Windows 10 Settings URIs, please visit the [launch settings](https://docs.microsoft.com/windows/uwp/launch-resume/launch-settings-app#ms-settings-uri-scheme-reference) documentation.
