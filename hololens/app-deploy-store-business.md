---
title: Microsoft Store & Intune
description: Learn how to work with the Microsoft Store & Intune to publish your mixed reality applications to your business. 
keywords: Microsoft Store, Intune, app deployment, store
author: lolab
ms.author: lolab
ms.date: 10/13/2021
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority:
audience: HoloLens
manager: lolab
---

# Microsoft Store & Intune

With the [retirement](https://techcommunity.microsoft.com/t5/intune-customer-success/adding-your-microsoft-store-for-business-and-education-apps-to/ba-p/3788506) of the [Microsoft Store for Business](/microsoft-store/microsoft-store-for-business-overview), a new and improved Microsoft Store app management experience is available in Intune, leveraging Windows Package Manager and other improvements.  For more details, read [Update to Intune integration with the Microsoft Store on Windows](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/update-to-intune-integration-with-the-microsoft-store-on-windows/ba-p/3585077)

A Mobile Device Management (MDM) solution enables IT administrators to distribute and auto-install apps to the managed HoloLens 2 devices in their organization. HoloLens 2 devices work best with Microsoft __Intune__ as the MDM solution.

The following instructions describe how to download HoloLens 2 apps from the __Microsoft Store for Business__, and then to distribute those apps to your managed HoloLens 2 devices using Intune.

> [!Note]
> Microsoft has [announced plans to retire](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/support-tip-microsoft-store-for-business-retirement-and-windows/ba-p/3662691) the Microsoft Store for Business.   However, the original retirement date, March 31<sup>st</sup> 2023, has been postponed, with a new retirement date yet to be announced. The instructions below can be used until the Microsoft Store for Business is retired. 
> When the Microsoft Store for Business is retired, Microsoft plans to enable an alternative process for downloading an app package.  The step to distribute an app package to HoloLens 2 devices will not change.

__Step 1: Download an app package__

To prepare for distributing an app to HoloLens 2 devices using Intune, you first need to download the app package file from the Microsoft Store for Business (or obtain the app package file directly from the app vendor).

1. __Configure the Microsoft Store for Business website to display offline apps__:

   a.   Using a web browser on a PC, sign in to the [Microsoft Store for Business](https://businessstore.microsoft.com/).

   b.   Click __Manage__ (on the top navigation).

   c.   Click __Settings__ (on the left navigation).

   d.   Click __Shop.__

   e.   Under __Shopping experience__, ensure that __Show offline apps__ is enabled.

2. __Shop for the app and add it into your group inventory__:

   a.   Using a web browser on a PC, sign in to the [Microsoft Store for Business](https://businessstore.microsoft.com/).

   b.   In the top navigation bar, click __Shop for my group__.

   c.    Using the search box on the top navigation bar, __search__ for the name of the app that you're looking for. When you find the app, click on it.

   d.   On the app page, for __License type__ select __Offline.__

   e.   Click __Get the app__. This will add the app to your group inventory in the Microsoft Store for Business website.

> [!NOTE]
> If you do not see the **Get the app** button next to the app, the app may already be in your group inventory.
> To be able to add apps into the group inventory, you must have one of the following [security roles in the Microsoft Store for Business](/microsoft-store/roles-and-permissions-microsoft-store-for-business): **Admin**, and/or **Purchaser**. If you do not have one of these roles, then when you shop for apps, you may see the option to [request apps](/microsoft-store/acquire-apps-microsoft-store-for-business). Submitting a request for an app will send an automated email with the request to the relevant administrator(s) in your organization, who will then need to decide whether to add the app.
> If the app you are looking for is not available for offline download from the Microsoft Store for Business, you will need to contact the app vendor to request the offline app package (appx file).

__3.     Download the offline app package and required frameworks (if any)__:

   a.   Using a web browser on a PC, sign in to the [Microsoft Store for Business](https://businessstore.microsoft.com/).

   b.   On the top navigation bar, click __Manage__.

   c.    Under __Products & services__, select __Manage apps__.

   d.   Find the app that you are looking for in the list. Click the app name.

   e.   Under __Download package for offline use__, set __Platform__ to __Windows 10 HoloLens__.

   f.     Click __Download__ to download the app package (appx file).

   g.   Scroll down to the __Required frameworks.__ If any required frameworks are listed, click the __Download__ button next to each to download them all. (Some apps may not have any required frameworks)

> [!NOTE]
> Dynamics 365 Guides and Dynamics 365 Remote Assist are pre-installed on HoloLens 2 devices. If you use Windows Autopilot for managed device setup, these apps will automatically be updated to the latest versions during device setup.

 

__Step 2: Distribute an app package to HoloLens 2 devices__

Once you have downloaded an app package file (see above), you can use Intune to [distribute it as a line-of-business app](/mem/intune/apps/lob-apps-windows) to auto-install on HoloLens 2 devices.

__1.     Select the app type:__

   a.   Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).

   b.   Select __Apps__ > __All apps__ > __Add__.

   c.    In the __Select app type__ pane, under the __Other__ app types, select __Line-of-business app__.

   d.   Click __Select__. The __Add app__ steps are displayed.

__2.     Select the app package file:__

   a.   In the __Add app__ pane, click __Select app package file__.

   b.   In the __App package file__ pane, select the browse button. Then, select an app package file with the extension __.appx__. The app details will be displayed.

   c.    When you're finished, select __OK__ on the __App package file__ pane to add the app.

__3.     Set app information:__

   a.   In the __App information__ page, add the details for your app. Depending on the app that you chose, some of the values in this pane might be automatically filled in.

   - __Name__: Enter the name of the app as it appears in the company portal. Make sure all app names that you use are unique. If the same app name exists twice, only one of the apps appears in the company portal.
   - __Description__: Enter the description of the app. The description appears in the company portal.
   - __Publisher__: Enter the name of the publisher of the app.
   - __App Install Context__: Select the install context to be associated with this app. For dual mode apps, select the desired context for this app. For all other apps, this is pre-selected based on the package and cannot be modified.
   - __Category__: Select one or more of the built-in app categories, or select a category that you created. Categories make it easier for users to find the app when they browse through the company portal.
   - __Show this as a featured app in the Company Portal__: Display the app prominently on the main page of the company portal when users browse for apps.
   - __Information URL__: Optionally, enter the URL of a website that contains information about this app. The URL appears in the company portal.
   - __Privacy URL__: Optionally, enter the URL of a website that contains privacy information for this app. The URL appears in the company portal.
   - __Developer__: Optionally, enter the name of the app developer.
   - __Owner__: Optionally, enter a name for the owner of this app. An example is HR department.
   - __Notes__: Enter any notes that you want to associate with this app.
   - __Logo__: Upload an icon that is associated with the app. This icon is displayed with the app when users browse through the company portal.

   b.   Click __Next__ to display the __Scope tags__ page.

__4.     Select scope tags (optional):__

You can use scope tags to determine who can see client app information in Intune. For full details about scope tags, see [Use role-based access control and scope tags for distributed IT](/mem/intune/fundamentals/scope-tags).

   a.   Click __Select scope tags__ to optionally add scope tags for the app.

   b.   Click __Next__ to display the __Assignments__ page.

__5.     Assignments:__

   a.   Select the __Required__ group assignment for the app. For more information, see [Add groups to organize users and devices](/mem/intune/fundamentals/groups-add) and [Assign apps to groups with Microsoft Intune](/mem/intune/apps/apps-deploy).

   b.   Click __Next__ to display the __Review + create__ page.

__6.     Review + create:__

   a.   Review the values and settings you entered for the app.

   b.   When you are done, click __Create__ to add the app to Intune.

The __Overview__ blade for the line-of-business app is displayed.


__Next steps:__

The app that you created now appears in the list of apps. From the list, you can assign the apps to groups that you choose. For help, see [How to assign apps to groups](/mem/intune/apps/apps-deploy).

> [!Tip]
> Learn more about [distributing offline apps](/microsoft-store/distribute-offline-apps) when using apps like Advanced Recovery Companion (ARC) and Windows Configuration Designer (WCD).

## Smart Retry for app updates

- Introduced in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2).

Now enabled for HoloLens is a new policy that allows IT Admins to set a recurring or one time date to restart apps whose update failed due to the app being in use allowing the update to be applied. These can be set based on a few different triggers such as a scheduled time or sign-in. To learn more about how to use this policy please view [ApplicationManagement/ScheduleForceRestartForUpdateFailures](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures).