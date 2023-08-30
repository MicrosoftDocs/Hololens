---
title: Diagnose HoloLens 2 network issues with Fiddler and Wireshark
description: If network issues are an obstacle to successfully deploying and using HoloLens 2 in your organization, learn how two well-known network diagnostic tools, Fiddler and Wireshark can help you scan, diagnose, and identify problems.
ms.reviewer: robertvs
ms.date: 9/15/2022
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
- HoloLens 2
---

# Diagnose HoloLens 2 network issues with Fiddler and Wireshark

If network issues are an obstacle to successfully deploying and using HoloLens 2 in your organization, learn how two well-known network diagnostic tools, Fiddler and Wireshark can help you scan, diagnose, and identify problems.

* [Fiddler Everywhere](https://www.telerik.com/fiddler) is a third party web debugging proxy and is used primarily to troubleshoot HTTP(S) issues. It captures every HTTP request the computer makes and records everything associated with it, making it easy to uncover end-user authentication issues for the HTTPS apps used in your organization.

    >[!Note]
    >There is also a free version of Fiddler called [Fiddler Classic](https://www.telerik.com/fiddler/fiddler-classic) that can be used for the diagnostics.   Although the interface is slightly different than what is shown here, the functionality between the two tools is similar

* [Wireshark](https://www.wireshark.org/) is a third party network protocol analyzer primarily used to inspect TCP/UDP traffic to and from your HoloLens 2 devices. This makes it easy to inspect all the network traffic that is crossing to your HoloLens 2.   This also allows for you to do some deeper inspection of the traffic by looking at much of it there is, how much latency there is between certain hops, etc.

## Network diagnostic tools

We’ll go over some examples of when to use these tools, along with installing and configurations with your HoloLens 2.

[!INCLUDE[](includes/tools-network-diagnostics.md)]

## Conclusion

After deploying HoloLens 2 to your organization, you may need to capture network traffic for troubleshooting purposes. Both Fiddler and Wireshark will work with the HoloLens 2 to identify and diagnose problems in the HTTP(S) and TCP/UDP levels.

## Feedback Hub and troubleshooting tips

HoloLens 2 provides a few methods for users to provide diagnostic logs to Microsoft for investigation. You can use Feedback Hub to submit logs for generic network connectivity issues by submitting your feedback through the “Network & Internet” category. In addition, the built-in Settings Troubleshooter can collect detailed network traces for more complex issues. For more information, see [Collect and use diagnostic information from HoloLens devices](hololens-diagnostic-logs.md) for instructions.
