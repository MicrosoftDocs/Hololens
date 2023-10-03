---
title: Set up your HoloLens 2
description: Learn how to set up your HoloLens 2 for the first time over Wi-Fi network with either a Microsoft (MSA) or Azure Active Directory (AAD) account.
ms.assetid: 507305f4-e85a-47c5-a055-a3400ae8a10e
ms.date: 6/09/2021
keywords: hololens
ms.prod: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: high
appliesto:
- HoloLens 2
---

# Add the first user to your HoloLens 2

The first time you turn on your HoloLens, you are guided through setting up your device, signing in with a user account, and calibrating the HoloLens to your eyes.  This section walks through the HoloLens 2 initial setup experience.

In the next section, you learn how to work with HoloLens and interact with holograms. To skip ahead to that article, see [Getting around HoloLens 2](hololens2-basic-usage.md).

## Before you start

Before you get started, make sure you have the following available:

**A network connection**. You need to connect your HoloLens to a network to set it up. With HoloLens 2, you can connect with Wi-Fi or by using ethernet (you need a USB-C-to-Ethernet adapter). The first time you connect, you need an open or password-protected network that doesn't require navigating to a website or using certificates to connect. [Learn more about the websites that HoloLens uses](hololens-offline.md).

**Azure AD account**. You also need to sign in to HoloLens with an Azure AD account, if your organization owns the device (or with your Microsoft account, if you own the device). (You can set up a Microsoft account for free at [account.microsoft.com](https://account.microsoft.com).)  Ensure you have configured a Multi-Factor Authentication (MFA) method on your account. Go to [What is Microsoft Entra authentication](/azure/active-directory/authentication/overview-authentication) to learn more about MFA.

**A safe, well-lit space with no tripping hazards**. [Health and safety info](https://go.microsoft.com/fwlink/p/?LinkId=746661).

**The optional comfort accessories** that came with your HoloLens, to help you get the most comfortable fit. [More on fit and comfort](hololens2-setup.md#adjust-fit).

## Set up Windows

The first time you start your HoloLens 2, your first task is to set up Windows Holographic.  When you start your HoloLens, you hear music and see a Microsoft logo.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGGGk]

<br/>
<img src="images/01-magic-moment.png" width="500px" alt="First screen during first boot">





You see a hummingbird flying around.

<img src="images/hummingbird-1.png" width="500px" alt="Hummingbird flying">

It follows your hand.

<img src="images/hummingbird-2.png" width="500px" alt="Hummingbird flying close up">

A button with a Microsoft logo shows up. Press the button, and HoloLens 2 walks you through the following steps:

1. Select your language.
 <img src="images/04-language.png" width="500px" alt="Select language">


1. Select your region.
1.  <img src="images/05-region.png" width="500px" alt="Select region">

1. View consent to collect biometric data for device calibration and improved reliability.  

![Biometric data is collected to improve the user experience.](media/hololens2-start/microsoftteams-image-(5).png)

1. Calibrate HoloLens to your eyes.  First, you'll adjust your visor to enable eye calibration to take place.

![Please adjust the HoloLens for your eyes so that calibration may continue.](media/hololens2-start/oobe-combinedcalibration.png)

1. To calibrate, you look at a set of targets (referred to as gems). It's fine if you blink or close your eyes during calibration, but try not to stare at other objects in the room or physical space. HoloLens uses this process to learn about your eye position so that it can better render your holographic world. 

After calibration, holograms appear correctly even as the visor shifts on your head. Calibration information is stored locally on the device and is not associated with any account information. For more information, see [Calibration data and security](hololens-calibration.md#calibration-data-and-security).

<img src="images/calibration-complete.png" width="500px" alt="Calibration is complete">

1. Connect to the internet (select Wi-Fi or your ethernet connection).

     HoloLens sets your time zone automatically based on information obtained from the Wi-Fi network. After setup finishes, you can change the time zone by using the Settings app.

    ![Connect to Wi-Fi.](images/11-network.png)

    > [!NOTE] 
    > If you progress past the Wi-Fi step and later need to switch to a different network while still in setup, you can press the **Volume Down** and **Power** buttons simultaneously to return to this step if you are running an OS version from October 2019 or later. For earlier versions, you may need to [reset the device](hololens-recovery.md) or restart it in a location where the Wi-Fi network is not available to prevent it from automatically connecting.
    > 
    > Also note that during HoloLens Setup, there is a credential timeout of two minutes. The username/password needs to be entered within two minutes otherwise the username field will be automatically cleared.

1. HoloLens 2 searches for, and applies, an Autopilot profile if one exists. If your organization has configured an Autopilot profile, it automatically configures and takes you to the sign in screen. So, no action is needed on this screen.
    ![Autopilot profile search.](images/autopilot-profile-search.png) 

1. Click **Accept** on the licensing screen.

    ![Windows license agreement.](images/windows-license-agreement.png)

1. Sign in to your user account. You choose between **My work or school owns it** and **I own it**.

    ![Set user.](images/13-device-owner.png)
    - When you choose **My work or school owns it**, you sign in with an Azure AD account. If your organization uses Azure AD Premium and has configured automatic MDM enrollment, HoloLens automatically enrolls in MDM. If your organization does not use Azure AD Premium, automatic MDM enrollment isn't available. In that case, you need to [manually enroll HoloLens in device management](hololens-enroll-mdm.md#different-ways-to-enroll).

        1. Enter your organizational account information.
        1. Accept the privacy statement and the end user license agreement.
        1. Sign in by using your Azure AD credentials. This may redirect to your organization's sign-in page.
        1. Continue setting up the device.

    - When you choose **I own it**, you sign in with a Microsoft account. After setup is complete, you can [manually enroll HoloLens in device management](hololens-enroll-mdm.md#different-ways-to-enroll).

        1. Enter your Microsoft account information.  You can set up a Microsoft account for free at [account.microsoft.com](https://account.microsoft.com).
        2. Enter your password. If your Microsoft account requires [two-step verification (2FA)](https://blogs.technet.microsoft.com/microsoft_blog/2013/04/17/microsoft-account-gets-more-secure/), complete the verification process.

        
1. Setup Iris sign-in by selecting **Next**. You go through a similar experience to the eye calibration. Select **Done** when the scan is complete. You may also select **Skip** to bypass this step.

 <img src="images/setup-iris.png" width="500px" alt="Iris setup">

 <img src="images/iris-setup-complete.png" width="500px" alt="Iris setup completion">





1. You setup a PIN to log into the device. This PIN is device specific. 

    ![Setup Windows Hello.](images/setup-windows-hello.png)

    ![Setup Windows Hello PIN.](images/windows-hello-pin.png)

    ![Windows Hello Setup successful.](images/windows-hello-successful.png) 

    
1. Select whether to enable speech on HoloLens 2.

    <img src="images/22-do-more-with-voice.png" width="500px" alt="Enable Cortana">

1. Select whether to enable location on HoloLens 2.
    
    <img src="images/setup-location-services.png" width="500px" alt="Enable location services">

1. Select your telemetry level. If you can, please enable Optional telemetry. This information really helps the HoloLens engineering team.

    <img src="images/24-telemetry.png" width="500px" alt="Telemetry level">


1. Learn how to use the start gesture on HoloLens 2.

    <img src="images/26-01-startmenu-learning.png" width="500px" alt="Learn how to use the start gesture, image 1">

    <img src="images/26-02-startmenu-learning.png" width="500px" alt="Learn how to use the start gesture, image 2">
    
    > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3Wxng]
    
    Congratulations!  Setup is complete and you're ready to use HoloLens!

## Next steps

1. Start interacting right away with Mixed Reality and navigating Windows 10 on your HoloLens - check out the **Tips** app for hands-on tutorials for hand interactions. Use the start gesture to go to Start or say "Go to Start" and select Tips.
1. Click below to continue reading about getting around HoloLens 2.

> [!div class="nextstepaction"]
> [Getting around HoloLens 2](hololens2-basic-usage.md)



