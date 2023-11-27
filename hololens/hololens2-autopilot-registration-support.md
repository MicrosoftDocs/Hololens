---
title: Windows Autopilot Registration Support for HoloLens 2
description: Learn how to get registration support for Autopilot on HoloLens 2 devices.
ms.date: 8/1/2022
ms.prod: hololens
ms.topic: article
ms.custom: 
- CI 116283
- CSSTroubleshooting
audience: ITPro
ms.localizationpriority: high
keywords: autopilot
---
# HoloLens 2 Registration Support for Autopilot

Customers and Microsoft Cloud Solution Providers (CSPs) can now register HoloLens 2 devices by directly submitting requests to Microsoft Support. This page outlines the requirements for the following supported Autopilot registration scenarios:

- **HoloLens 2 Device Autopilot Registration**. Submits request to register HoloLens 2 devices into Windows Autopilot.
- **HoloLens 2 Device Hardware Hash Request**. Submits request to Microsoft Support to provide you with hardware hashes that customers or CSPs can use to self-register devices via Microsoft Intune or the Microsoft Partner Center.
- **HoloLens 2 Device Autopilot Deregistration**. Submits request to delete devices from Windows Autopilot, typically used in device end of life scenarios.

The following table details the information you will need to collect *prior* to submitting registration requests to Microsoft Support.

| Required Information | Description | Autopilot Registration  | Hardware Hash Request | Autopilot Deregistration |
------------|-------------------------------|--------------------------------------------------|------------------------------|--------------------------------|
|  Microsoft Entra tenant ID    |    Your Microsoft Entra tenant ID is a globally unique identifier (GUID) that is different than your organization name or domain.    To find your Tenant ID sign into the [Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).    |     ✔️                         |                              |                         ✔️                        |
|  Microsoft Entra Domain Name    |   Your top-level domain name; for example, contoso.com.    |     ✔️                         |                              |                         ✔️                        |
|  Proof of Ownership    |   Verify proof of ownership by uploading the original bill of sale or invoice in PDF format. Screenshots are not accepted. The bill of sale or invoice must include the following: Device serial numbers. Company name.     |     ✔️                         |              ✔️                |                         ✔️                        |
|  Device serial numbers    |   Upload Excel file in CSV format with each device serial number in a new line.     |     ✔️                         |              ✔️                |                         ✔️                        |

## Submit support requests

> [!div class="nextstepaction"]
> [Submit Autopilot Registration Support for HoloLens 2](https://support.serviceshub.microsoft.com/supportforbusiness/create?sapId=366a90e9-f67f-d352-8143-a3be7d5514f0)
