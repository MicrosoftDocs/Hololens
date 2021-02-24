---
title: Collect and use diagnostic information from HoloLens devices
description: Learn how to collect, use, and retain diagnostic information from HoloLens devices.
author: Teresa-Motiv
ms.author: v-tea
ms.date: 10/15/2020
ms.prod: hololens
ms.mktglfcycl: manage
ms.sitesec: library
ms.topic: article
ms.custom: 
- CI 115131
- CSSTroubleshooting
audience: ITPro
ms.localizationpriority: medium
keywords: 
manager: jarrettr
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Collect and use diagnostic information from HoloLens devices

HoloLens users and administrators can choose from among four different methods to collect diagnostic information from HoloLens:

- Feedback Hub app
- DiagnosticLog CSP
- Settings app

> [!IMPORTANT]  
> Device diagnostic logs contain personally identifiable information (PII), such as about what processes or applications the user starts during typical operations. When multiple users share a HoloLens device (for example, users sign in to the same device by using different Microsoft Azure Active Directory (Azure AD) accounts) the diagnostic logs may contain PII information that applies to multiple users. For more information, see [Microsoft Privacy statement](https://privacy.microsoft.com/privacystatement).

The following table compares the three collection methods. The method names link to more detailed information in the sections that follow the table.

|Method |Prerequisites |Data locations |Data access and use |Data retention |
| --- | --- | --- | --- | --- |
|[Feedback Hub](#feedback-hub) |Network and internet connection<br /><br />Feedback Hub app<br /><br />Permission to upload files to the Microsoft cloud |Microsoft cloud<br /><br />HoloLens device (optional) |User requests assistance, agrees to the terms of use, and uploads the data<br /><br />Microsoft employees view the data, as consistent with the terms of use |Data in the cloud is retained for the period that is defined by Next Generation Privacy (NGP). Then the data is deleted automatically.<br /><br />Data on the device can be deleted at any time by a user who has **Device owner** or **Admin** permissions. |
|[Settings Troubleshooter](#settings-troubleshooter) |Settings app |HoloLens device<br /><br />Connected computer (optional) |The user stores the data, and only the user accesses the data (unless the user specifically shares the data with another user). |The data is retained until the user deletes it.* |
|[DiagnosticLog CSP](#diagnosticlog-csp) |Network connection<br /><br />MDM environment that supports the DiagnosticLog CSP |Administrator configures storage locations |In the managed environment, the user implicitly consents to administrator access to the data.<br /><br />Administrator configures access roles and permissions. | Administrator configures retention policy. |
|[Offline diagnostics](#offline-diagnostics) |Device configuration:<ul><li>Powered on and connected to computer</li><li>Power and Volume buttons functioning</li></ul> |HoloLens device<br /><br />Connected computer |The user stores the data, and only the user accesses the data (unless the user specifically shares the data with another user). |The data is retained until the user deletes it. | 


-	End-user is responsible for sharing the logs responsibly with someone else. These files are primarily useful when contacting customer service and support.  

## Feedback Hub

A HoloLens user can use the Microsoft Feedback Hub desktop app to send diagnostic information to Microsoft Support. For details and complete instructions, see [Give us feedback](hololens-feedback.md).  

> [!NOTE]  
> **Commercial or enterprise users:** If you use the Feedback Hub app to report a problem that relates to MDM, provisioning, or any other device management aspect, change the app category to **Enterprise Management** > **Device category**.

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

A HoloLens user can use the Settings app on the device to troubleshoot problems and collect diagnostic information. To do this, follow these steps:

1. Open the Settings app and select **Update & Security** > **Troubleshoot** page.
1. Select the appropriate area, and select **Start**.
1. Reproduce the issue.
1. After you reproduce the issue, return to Settings and then select **Stop**.

### Prerequisites

- The Settings app is installed on the device and is available to the user.

### Data locations, access, and retention

Because the user starts the data collection, the user implicitly consents to the storage of the diagnostic information. Only the user, or anyone with whom that the user shares the data, can access the data.

The diagnostic information is stored on the device. If the device is connected to the user's computer, the information also resides on the computer in the following file:

> This PC\\\<*HoloLens device name*>\\Internal Storage\\Documents\\Trace\<*ddmmyyhhmmss*>.etl

> [!NOTE]  
> In this file path and name, \<*HoloLens device name*> represents the name of the HoloLens device, and \<*ddmmyyhhmmss*> represents the date and time that the file was created.

The diagnostic information remains in these locations until the user deletes it.

## DiagnosticLog CSP

In a Mobile Device Management (MDM) environment, the IT administrator can use the the [DiagnosticLog configuration service provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/diagnosticlog-csp) to configure diagnostic settings on enrolled HoloLens devices. The IT administrator can configure these settings to collect logs from enrolled devices.

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
In situations where the device is not able to collect diagnostics via Feedback Hub or the Setting Troubleshooter, you can collect diagnostics manually. One scenario where this is necessary is when the device cannot connect to Wi-Fi. The diagnostics collect crash dumps and logs from the device that help a Microsoft support engineer isolate issues.

This works when the device shows up in File Explorer after connecting it to a PC via a USB cable. 

> [!NOTE]
> Offline Diagnostics generation and management is controlled differently depending on your OS version. Previously it was controlled by the telemetry setting, but is now directly controlled via policy. 

Behavior Prior to [Windows Holographic, verison 20H2](hololens-release-notes.md#windows-holographic-version-20h2):
 - Offline diagnostics is only enabled when user is either going through OOBE or [System\AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) policy value is set to Full (Basic is default value on HoloLens). 
- To disable Offline diagnostics, go to **Settings App > Privacy** page and select **Basic** in **Diagnostic Data**. On builds where offline diagnostics depends on telemetry setting, it only impacts whether any logs are collected or not. It does not impact what files are collected.
- If device is locked then logs won't appear.

On builds [Windows Holographic, verison 20H2](hololens-release-notes.md#windows-holographic-version-20h2) and onwards:
- When Fallback Diagnostics is enabled will be controlled by specific MDM policy with corresponding setting [MixedReality/FallbackDiagnostics](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mixedreality#mixedreality-fallbackdiagnostics)
- If device is locked then logs won't appear.


Watch this video to learn more. 

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Gathering-Diagnostic-Files-on-HoloLens2/player]

Follow these steps to collect diagnostics:
1.	Connect the device with a USB cable to your PC.
2.	In File Explorer on your PC, navigate to **'This PC\<hololens-device>\Internal Storage'**.
3.	If the **Internal Storage** folder does not show up, the device is waiting for a user to sign in. Either sign-in or power cycle the device by holding the POWER button down for 10 seconds.
4.	Press and immediately release the **POWER + VOLUME DOWN** buttons together.
5.	Wait a minute for the device to prepare the zip archives. (A temporary file named HololensDiagnostics.temp may become visible while the device generates the zip archives. Do not access or save that file. When the process finishes it will be replaced by the zip archives.)
6.	Refresh file explorer, and navigate to the **'\Documents'** folder.
7.	Copy the diagnostics ZIP files and share them with the Microsoft support team.

> [!NOTE]
> Some of the diagnostics ZIP files may contain personally identifiable information.



