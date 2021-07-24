---
title: Manage user identity and sign-in for HoloLens
description: Learn how to manage user identity, multi-user support, security, enterprise authentication, and sign-in for HoloLens devices.
keywords: HoloLens, user, account, AAD, Azure AD, adfs, microsoft account, msa, credentials, reference
ms.assetid: 728cfff2-81ce-4eb8-9aaa-0a3c3304660e
author: scooley
ms.author: scooley
ms.date: 10/6/2020
ms.prod: hololens
ms.custom: 
- CI 111456
- CSSTroubleshooting
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
manager: jarrettr
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Manage user identity and sign-in for HoloLens

> [!NOTE]
> This article is a technical reference for IT Pros and tech enthusiasts. If you're looking for HoloLens set up instructions, read "[Setting up your HoloLens (1st gen)](hololens1-start.md)" or "[Setting up your HoloLens 2](hololens2-start.md)".

Like other Windows devices, HoloLens always operates under a user context. There is always a user identity. HoloLens treats identity in almost the same manner as other Windows 10 devices do. This article is a deep-dive reference for identity on HoloLens, and focuses on how HoloLens differs from other Windows 10 devices.

HoloLens supports several kinds of user identities. You can use one or more user accounts to sign in. Here's an overview of the identity types and authentication options on HoloLens:

| Identity type | Accounts per device | Authentication options |
| --- | --- | --- |
| [Azure Active Directory](/azure/active-directory/)<sup>1</sup>  | 64 | <ul><li>Azure web credential provider</li><li>Azure Authenticator App</li><li>Biometric (Iris) &ndash; HoloLens 2 only<sup>2</sup> </li><li>PIN &ndash; Optional for HoloLens (1st gen), required for HoloLens 2</li><li>Password</li></ul> |
| [Microsoft Account (MSA)](/windows/security/identity-protection/access-control/microsoft-accounts) | 1 | <ul><li>Biometric (Iris) &ndash; HoloLens 2 only</li><li>PIN &ndash; Optional for HoloLens (1st gen), required for HoloLens 2</li><li>Password</li></ul> |
| [Local account](/windows/security/identity-protection/access-control/local-accounts) | 1 | Password |

Cloud-connected accounts (Azure AD and MSA) offer more features because they can use Azure services.  
> [!IMPORTANT]
> 1 - Azure AD Premium is not required to sign into the device. However, it is required for other features of a low touch cloud-based deployment, like Auto-enrollment and Autopilot.

> [!NOTE]
> 2 - While a HoloLens 2 device can support up to 64 Azure AD accounts, only 31 of those accounts may enroll in Iris Authentication. This is aligned with other [Biometric authentication options for Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-faq#how-many-users-can-enroll-for-windows-hello-for-business-on-a-single-windows-10-computer).

## Setting up users

There are two ways to set up a new user on the HoloLens. The most common way is during the HoloLens out-of-box experience (OOBE). If using Azure Active Directory, [other users can log in](#setting-up-multi-user-support-(azure-ad-only)) after OOBE using their Azure AD credentials. HoloLens devices that are initially logged onto using a MSA or local account do not support multiple users. See Setting up your [HoloLens (1st gen)](hololens1-start.md) or [HoloLens 2](hololens2-start.md).

If you use an enterprise or organizational account to sign in to HoloLens, HoloLens enrolls in the organization's IT infrastructure. This enrollment allows your IT Admin to configure Mobile Device Management (MDM) to send group policies to your HoloLens.

Like Windows on other devices, signing in during setup creates a user profile on the device. The user profile stores apps and data. The same account also provides Single Sign-on for apps, such as Edge or the Microsoft Store, by using the Windows Account Manager APIs. 

By default, as for other Windows 10 devices, you'll have to sign in again when HoloLens restarts or resumes from standby. You can use the Settings app to change this behavior, or the behavior can be controlled by group policy.

### Linked accounts

As in the Desktop version of Windows, you can link additional web account credentials to your HoloLens account. Such linking makes it easier to access resources across or within apps (such as the Store) or to combine access to personal and work resources. After you connect an account to the device, you can grant permission to use the device to apps so that you don't have to sign in to each app individually.

Linking accounts does not separate the user data created on the device, such as images or downloads.  

### Setting up multi-user support (Azure AD only)

HoloLens supports multiple users from the same Azure AD tenant. To use this feature, you must use an account that belongs to your organization to set up the device. Subsequently, other users from the same tenant can sign in to the device from the sign-in screen or by tapping the user tile on the Start panel. Only one user can be signed in at a time. When a user signs in, HoloLens signs out the previous user. 

>[!IMPORTANT]
The first user on the device is considered the device owner, except in the case of Azure AD Join, [learn more about device owners](security-adminless-os.md#device-owner).

All users can use the apps installed on the device. However, each user has their own app data and preferences. Removing an app from the device removes it for all users.  

Devices set up with Azure AD accounts will not allow signing in to the device with a Microsoft Account. All subsequent accounts used must be Azure AD accounts from the same tenant as the device. You may still [sign in using a Microsoft Account to apps](hololens-identity.md#setting-up-multi-user-support-azure-ad-only) that support it (such as the Microsoft Store). To change from using Azure AD accounts to Microsoft Accounts for signing in to the device, you must [reflash the device](hololens-recovery.md#clean-reflash-the-device).

> [!NOTE]
> **HoloLens (1st gen)** began supporting multiple Azure AD users in the [Windows 10 April 2018 Update](/windows/mixed-reality/release-notes-april-2018) as part of [Windows Holographic for Business](hololens-upgrade-enterprise.md).

### Multiple users listed on Sign in screen

Previously the Sign In screen showed only the most recently signed in user, as well as an 'Other user' entry point. We have received customer feedback that this not sufficient if multiple users have signed into the device. They were still required to retype their username etc.

Introduced in [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1), when selecting **Other user** which is located to the right of the PIN entry field, the Sign in screen will display multiple users with have previously signed into the device. This allows users to select their user profile and then sign-in using their Windows Hello credentials. A new user can also be added to the device from this Other users page via the **Add account** button.

When in the Other users menu, the Other users button will display the last user signed into the device. Select this button to return to the Sign in screen for this user.

![Sign-in screen default](./images/multiusers1.jpg)

<br>

![Sign-in screen other users](./images/multiusers2.jpg)

## Removing users

You can remove a user from the device by going to **Settings** > **Accounts** > **Other people**. This action also reclaims space by removing all of that user's app data from the device.  

## Using single sign-on within an app

As an app developer, you can take advantage of linked identities on HoloLens by using the [Windows Account Manager APIs](/uwp/api/Windows.Security.Authentication.Web.Core), just as you would on other Windows devices. Some code samples for these APIs are available on GitHub: [Web account management sample](https://go.microsoft.com/fwlink/p/?LinkId=620621).

Any account interrupts that might occur, such as requesting user consent for account information, two-factor authentication, and so forth, must be handled when the app requests an authentication token.

If your app requires a specific account type that hasn't been linked previously, your app can ask the system to prompt the user to add one. This request triggers the account settings pane to launch as a modal child of your app. For 2D apps, this window renders directly over the center of your app. For Unity apps, this request briefly takes the user out of your holographic app to render the child window. For information about customizing the commands and actions on this pane, see [WebAccountCommand Class](/uwp/api/Windows.UI.ApplicationSettings.WebAccountCommand).

## Enterprise and other authentication

If your app uses other types of authentication, such as NTLM, Basic, or Kerberos, you can use [Windows Credential UI](/uwp/api/Windows.Security.Credentials.UI) to collect, process, and store the user's credentials. The user experience for collecting these credentials is very similar to other cloud-driven account interrupts, and appears as a child app on top of your 2D app or briefly suspends a Unity app to show the UI.

## Deprecated APIs

One way in which developing for HoloLens differs from developing for Desktop is that the [OnlineIDAuthenticator](/uwp/api/Windows.Security.Authentication.OnlineId.OnlineIdAuthenticator) API is not fully supported. Although the API returns a token if the primary account is in good-standing, interrupts such as those described in this article do not display any UI for the user and fail to correctly authenticate the account.

## Frequently asked questions

### Is Windows Hello for Business supported on HoloLens (1st Gen)?

Windows Hello for Business (which supports using a PIN to sign in) is supported for HoloLens (1st Gen). To allow Windows Hello for Business PIN sign-in on HoloLens:

1. The HoloLens device must be [managed by MDM](hololens-enroll-mdm.md).
1. You must enable Windows Hello for Business for the device. ([See instructions for Microsoft Intune.](/intune/windows-hello))
1. On HoloLens, the user can then use **Settings** > **Sign-in Options** > **Add PIN** to set up a PIN.

> [!NOTE]
> Users who sign in by using a Microsoft account can also set up a PIN in **Settings** > **Sign-in Options** > **Add PIN**. This PIN is associated with [Windows Hello](https://support.microsoft.com/help/17215/windows-10-what-is-hello), rather than [Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-overview).

### How is Iris biometric authentication implemented on HoloLens 2?

HoloLens 2 supports Iris authentication. Iris is based on Windows Hello technology and is supported for use by both Azure Active Directory and Microsoft Accounts. Iris is implemented the same way as other Windows Hello technologies, and achieves biometrics security FAR of 1/100K.

See the [biometric requirements and specifications for Windows Hello](/windows-hardware/design/device-experiences/windows-hello-biometric-requirements) for more information. Learn more about [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) and [Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-identity-verification). 

### How does the type of account affect sign-in behavior?

If you apply policies for sign-in, the policy is always respected. If no policy for sign-in is applied, these are the default behaviors for each account type:

- **Azure AD**: asks for authentication by default, and configurable by **Settings** to no longer ask for authentication.
- **Microsoft account**: lock behavior is different allowing automatic unlock, however sign in authentication is still required on reboot.
- **Local account**: always asks for authentication in the form of a password, not configurable in **Settings**

> [!NOTE]
> Inactivity timers are currently not supported, which means that the **AllowIdleReturnWithoutPassword** policy is only respected when the device goes into StandBy.

## Additional resources

Read much more about user identity protection and authentication on [the Windows 10 security and identity documentation](/windows/security/identity-protection/).

Learn more about setting up hybrid identity infrastructure thorough the [Azure Hybrid identity documentation](/azure/active-directory/hybrid/).
