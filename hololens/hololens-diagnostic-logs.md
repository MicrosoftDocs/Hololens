---
title: Collect and use diagnostic information from HoloLens devices
description: Learn how to collect, use, and retain diagnostic information from HoloLens devices.
author: evmill
ms.author: v-evmill
manager: ranjibb
ms.reviewer: lavinds
ms.date: 9/12/2021
ms.prod: hololens
ms.mktglfcycl: manage
ms.sitesec: library
ms.topic: article
ms.custom: 
- CI 115131
- CSSTroubleshooting
audience: ITPro
ms.localizationpriority:
keywords: 
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Collect and use diagnostic information from HoloLens devices

HoloLens users and administrators can choose from among four different methods to collect diagnostic information from HoloLens:

- Feedback Hub app
- DiagnosticLog CSP
- Settings app
- Offline Diagnostics

> [!IMPORTANT]  
> Device diagnostic logs contain personally identifiable information (PII), such as about what processes or applications the user starts during typical operations. When multiple users share a HoloLens device (for example, users sign in to the same device by using different Microsoft Azure Active Directory (Azure AD) accounts) the diagnostic logs may contain PII information that applies to multiple users. For more information, see [Microsoft Privacy statement](https://privacy.microsoft.com/privacystatement).

The following table compares different collection methods. The method names link to more detailed information in the sections that follow the table.

|Method |Prerequisites |Data locations |Data access and use |Data retention |
| --- | --- | --- | --- | --- |
|[Feedback Hub](#feedback-hub) |Network and internet connection<br /><br />Feedback Hub app<br /><br />Permission to upload files to the Microsoft cloud |Microsoft cloud<br /><br />HoloLens device (optional) |User requests assistance, agrees to the terms of use, and uploads the data<br /><br />Microsoft employees view the data, as consistent with the terms of use |Data in the cloud is retained for the period that is defined by Next Generation Privacy (NGP). Then the data is deleted automatically.<br /><br />Data on the device can be deleted at any time by a user who has **Device owner** or **Admin** permissions. |
|[Settings Troubleshooter](#settings-troubleshooter) |Settings app |HoloLens device<br /><br />Connected computer (optional) |The user stores the data, and only the user accesses the data (unless the user specifically shares the data with another user). |The data is retained on device until the user deletes it.* |
|[DiagnosticLog CSP](#diagnosticlog-csp) |Network connection<br /><br />MDM environment that supports the DiagnosticLog CSP |Administrator configures storage locations |In the managed environment, the user implicitly consents to administrator access to the data.<br /><br />Administrator configures access roles and permissions. | Data is retained in the cloud storage and Administrator configures retention policy. |
|[Offline diagnostics](#offline-diagnostics) |Device configuration:<ul><li>Powered on and connected to computer</li><li>Power and Volume buttons functioning</li></ul> |HoloLens device<br /><br />Connected computer |The user stores the data, and only the user accesses the data (unless the user specifically shares the data with another user). |The data is retained on device until the user deletes it. |

- The end user is responsible for sharing the logs responsibly with someone else. These files are primarily useful when contacting customer service and support.  

## Feedback Hub

A HoloLens user can use the Microsoft Feedback Hub desktop app to send diagnostic information to Microsoft Support. For details and complete instructions, see [Give us feedback](hololens-feedback.md).  

> [!NOTE]  
> **Commercial or enterprise users:** If you use the Feedback Hub app to report a problem that relates to MDM, provisioning, or any other device management aspect, change the app category to **Enterprise Management** > **Device category**.

>[!IMPORTANT]
> To provide the best possible data for fixing issues, we highly recommend that you set your device telemetry to **Optional**. You can set this value during the Out-of-Box-Experience (OOBE), or by using the **Settings** app. To do this by using Settings, select **Start > Settings > Privacy > App Diagnostics > On**.

### Prerequisites

- The device is connected to a network.
- The Feedback Hub app is available on the user's desktop computer, and the user can upload files to the Microsoft cloud.

### Data locations, access, and retention

By agreeing to the terms-of-use of the Feedback Hub, the user explicitly consents to the storage and usage of the data (as defined by that agreement).

The Feedback Hub provides two places for the user to store diagnostic information:

- **The Microsoft cloud**. Data that the user uploads by using the Feedback Hub app is stored for the number of days that is consistent with Next Generation Privacy (NGP) requirements. Microsoft employees can use an NGP-compliant viewer to access the information during this period.

   > [!NOTE]  
   > These requirements apply to data in all Feedback Hub categories.

- **The HoloLens device**. While filing a report in Feedback Hub, the user can select **Save a local copy of diagnostics and attachments created when giving feedback**. If the user selects this option, the Feedback Hub stores a copy of the diagnostic information on the HoloLens device. This information remains accessible to the user (or anyone that uses that account to sign in to HoloLens). To delete this information, a user must have **Device owner** or **Admin** permissions on the device. A user who has the appropriate permissions can sign in to the Feedback Hub, select **Settings** > **View diagnostics logs**, and delete the information.

## Settings Troubleshooter

A HoloLens user can use the **Settings** app on the device to troubleshoot problems and collect diagnostic information. To do this, follow these steps:

1. Open the Settings app and select **Update & Security** > **Troubleshoot** page.
1. Select the appropriate area, and select **Start**.
1. Reproduce the issue.
1. After you reproduce the issue, return to Settings and then select **Stop**.

A user can also configure the behavior of Fallback Diagnostics from the **Settings** app. Navigate to **Privacy -> Troubleshooting** page to configure this setting.
> [!NOTE]
> If there is MDM policy configured for the device, user will not be able to override that behavior.

### OS Update Troubleshooter

On builds [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1) and onwards:

- In addition to the previous troubleshooters within the Settings app, a new troubleshooter has been added with the addition of the new Settings app for OS Updates. Navigate to **Settings -> Update & Security -> Troubleshoot -> Windows Update** and select **Start**. This allows you to collect traces while reproducing your issue with OS Updates to assist better in troubleshooting with your IT or support.

### Prerequisites

- The **Settings** app is installed on the device and is available to the user.

### Data locations, access, and retention

Because the user starts the data collection, the user implicitly consents to the storage of the diagnostic information. Only the user, or anyone with whom that the user shares the data, can access the data.

The diagnostic information is stored on the device. If the device is connected to the user's computer, the information also resides on the computer in the following file:

> This PC\\\<*HoloLens device name*>\\Internal Storage\\Documents\\Trace\<*ddmmyyhhmmss*>.etl

> [!NOTE]  
> In this file path and name, \<*HoloLens device name*> represents the name of the HoloLens device, and \<*ddmmyyhhmmss*> represents the date and time that the file was created.

The diagnostic information remains in these locations until the user deletes it.

### View diagnostic report

To view the MDM Diagnostics on HoloLens 2, select your WiFi icon, then navigate to **Settings** -> **Accounts** > **Access work or school** and select **Export your management logs**. HoloLens sends the log files to your account and displays their location on your desktop PC.

## DiagnosticLog CSP

In a Mobile Device Management (MDM) environment, the IT administrator can use the [DiagnosticLog configuration service provider (CSP)](/windows/client-management/mdm/diagnosticlog-csp) to configure diagnostic settings on enrolled HoloLens devices. The IT administrator can configure these settings to collect logs from enrolled devices.

See more:

- [Collect diagnostics from a Windows device](/mem/intune/remote-actions/collect-diagnostics)
- [Intune Public Preview - Windows 10 Device diagnostics](https://techcommunity.microsoft.com/t5/intune-customer-success/intune-public-preview-windows-10-device-diagnostics/ba-p/2179712#:~:text=This%20first%20release%20of%20device%20diagnostics%20utilizes%20the,taking%20about%205%20minutes%20from%20start%20to%20finish.)

### Prerequisites

- The device is connected to a network.
- The device is enrolled in an MDM environment that supports the DiagnosticLog CSP.

### Data locations, access, and retention

Because the device is part of the managed environment, the user implicitly consents to administrative access to diagnostic information.

The IT administrator uses the DiagnosticLog CSP to configure the data storage, retention, and access policies, including the policies that govern the following:

- The cloud infrastructure that stores the diagnostic information.
- The retention period for the diagnostic information.
- Permissions that control access to the diagnostic information.

## Offline diagnostics

In situations where the device is not able to collect diagnostics via Feedback Hub or the Settings Troubleshooter, you can collect diagnostics manually. One scenario where this is necessary is when the device cannot connect to Wi-Fi or you can't access other methods mentioned above. The diagnostics collect crash dumps and logs from the device that help a Microsoft support engineer isolate issues.

This works when the device shows up in File Explorer after connecting it to a PC via a USB cable.

> [!NOTE]
> Offline Diagnostics generation and management is controlled differently depending on your OS version. Previously it was controlled by the telemetry setting, but is now directly controlled via MDM policy. If disabled via either setting or MDM policy, then diagnostic logs cannot be collected using this mechanism.

Behavior prior to [Windows Holographic, version 20H2](hololens-release-notes-2004.md#windows-holographic-version-20h2):

- Offline diagnostics is only enabled when user is either going through OOBE or [System\AllowTelemetry](/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) policy value is set to Full (Basic is default value on HoloLens).
- To disable Offline diagnostics, go to **Settings App > Privacy** page and select **Basic** in **Diagnostic Data**. On builds where offline diagnostics depends on telemetry setting, it only impacts whether any logs are collected or not. It does not impact what files are collected.
- If device is locked then logs won't appear.

On builds [Windows Holographic, version 20H2](hololens-release-notes-2004.md#windows-holographic-version-20h2) and onwards:

- When Fallback Diagnostics is enabled will be controlled by specific MDM policy with corresponding setting [MixedReality/FallbackDiagnostics](/windows/client-management/mdm/policy-csp-mixedreality#mixedreality-fallbackdiagnostics)
- If device is locked then logs won't appear.

Watch this video to learn more.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Gathering-Diagnostic-Files-on-HoloLens2/player]

Follow these steps to collect diagnostics:

1. Connect the device with a USB cable to your PC.

2. In File Explorer on your PC, navigate to **'This PC\<hololens-device>\Internal Storage'**.

3. If the **Internal Storage** folder does not show up, the device is waiting for a user to sign in. Either sign-in or power cycle the device by holding the POWER button down for 10 seconds.

4. Press and immediately release the **Power + Volume Down** buttons together.

5. Wait a minute for the device to prepare the zip archives. (A temporary file named HololensDiagnostics.temp may become visible while the device generates the zip archives. Do not access or save that file. When the process finishes it will be replaced by the zip archives.)

6. Refresh file explorer, and navigate to the **'\Documents'** folder.

7. Copy the diagnostics ZIP files and share them with the Microsoft support team.

> [!NOTE]
> Some of the diagnostics ZIP files may contain PII.

### Offline Diagnostics notifications

- Introduced in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2).

This an update for an existing feature called [Offline Diagnostics](hololens-diagnostic-logs.md#offline-diagnostics). Previously, there was no clear indicator to users that they had triggered diagnostic collection or it had completed.
Now added in Windows Insider builds, there are two forms of audiovisual feedback for Offline Diagnostics. The first being toasts notifications displayed for both when collection starts and completes. These will be displayed when the user is logged in and has visuals.

![Toast for collecting logs.](./images/logcollection1.jpg)

![Toast when log collection is complete.](./images/logcollection2.jpg)

Because users often use Offline Diagnostics as a fallback log gathering mechanism for when they don’t have access to a display, can’t log-in or are still in OOBE there will also be an audio cue played when logs are gathered. This sound will be played in addition to the toast notification.

This new feature will be enabled when your device updates, and doesn’t need to be enabled or managed. In any event that this new feedback cannot be displayed or heard, Offline Diagnostics will still be generated.

We hope with this newer addition of audiovisual feedback it is easier to gather diagnostic data, and more quickly be able to troubleshoot your problems.

### Low storage log collection improvements

- Introduced in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2).

In scenarios where a device seems to be low on disk space when diagnostic logs are collected, an additional report named **StorageDiagnostics.zip** will be created. The threshold of low storage is determined automatically by Windows [storage sense](https://support.microsoft.com/office/use-onedrive-and-storage-sense-in-windows-10-to-manage-disk-space-de5faa9a-6108-4be1-87a6-d90688d08a48).

## View advanced diagnostic report in Settings on HoloLens

- Introduced in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2).

For managed devices when troubleshooting behavior, confirming that an expected policy configuration is applied is an important step. Previously to this new feature, this had to be done off device via MDM or near the device after exporting MDM diagnostic logs gathered via **Settings** -> **Accounts** > **Access work or school**, and select **Export your management logs** and viewed on a nearby PC.

Now the MDM Diagnostics can be viewed on device using the Edge browser. To more easily view the MDM Diagnostic report navigate to the Access work or school page, and select **View advanced diagnostic report**. This will generate and open the report in a new Edge window.

![View advanced diagnostic report in Settings app.](./images/view-advanced-diagnostic-report.jpg)
