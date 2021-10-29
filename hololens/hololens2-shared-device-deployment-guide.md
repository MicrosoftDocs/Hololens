---
title: Deploying Remote Assist using a shared identity across multiple users
description: This article contains high level steps involved in deploying Remote Assist using shared Azure AD identity across multiple users. The guidance provided in this document focuses on provisioning Azure AD user accounts, assigning required licenses and HoloLens 2 device configuration for a shared device environment. For more detailed scenario-based deployment guidance please refer to [Common Deployment Scenarios](https://docs.microsoft.com/en-us/hololens/hololens-requirements).
author: MuruganandamDevarajan
ms.author: murugand
ms.date: 10/15/2021
ms.topic: article
ms.localizationpriority: high
audience: HoloLens 2
keywords: HoloLens, shared device, deployment
appliesto:
- HoloLens 2
---

# Deploying Remote Assist using a shared identity across multiple users - Overview
This article contains high level steps involved in deploying Remote Assist using shared Azure AD identity across multiple users. The guidance provided in this document focuses on provisioning Azure AD user accounts, assigning required licenses and HoloLens 2 device configuration for a shared device environment. For more detailed scenario-based deployment guidance please refer to [Common Deployment Scenarios](https://docs.microsoft.com/en-us/hololens/hololens-requirements).

## Deployment Tasks

### 1. Azure AD Accounts
Create Azure AD security groups and shared Azure AD user accounts to be used to login to HoloLens 2 devices.
1. Login to [Azure AD admin center](https://aad.portal.azure.com/) as Azure AD Global Administrator.
2. Navigate to [New Group - Azure Active Directory admin center](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/AddGroupBlade) blade and create a Azure AD **Security** Group to manage the HoloLens 2 shared user accounts. See [Create a basic group and add members - Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal#create-a-basic-group-and-add-members) for step by step instructions.
3. Navigate to [New user - Azure Active Directory admin center](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/MsGraphUsers) blade and create new user accounts to be shared by multiple people to login to the HoloLens 2 device. One Azure AD user account per HoloLens 2 device is recommended. See [Add or delete users - Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/add-users-azure-active-directory) for step by step instructions.
4. Navigate to [Groups - Azure Active Directory admin center](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups), select the ***Azure AD security group name* > Members > + Add members** and add the above user accounts to the security group. See [Add or remove group members - Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal) for step by step instructions.

### 2. License Assignments
Assign required licenses to the Azure AD user accounts.
1. You can assign licenses required to use Dynamics 365 Remote Assist on HoloLens 2 to a user or user group. To assign licenses to a user group follow [Assign licenses to a group - Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-groups-assign) step by step guide to assign the following licenses. To assign licenses to a user follow [Assign licenses to users - Microsoft 365 admin](https://docs.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide) step by step guide to assign the following licenses.
	- Dynamics 365 Remote Assist
	- Microsoft Teams
	- Common Data Service for Remote Assist
   
	See [Requirements for Dynamics 365 Remote Assist - Dynamics 365 Mixed Reality](https://docs.microsoft.com/en-us/dynamics365/mixed-reality/remote-assist/requirements#dynamics-365-remote-assist-app-user) for more details.
2. To manage HoloLens 2 using Microsoft Endpoint Manager (Intune), follow [Assign Microsoft Intune licenses](https://docs.microsoft.com/en-us/mem/intune/fundamentals/licenses-assign) step by step guide to assign the following licenses.
	- Microsoft Intune
3. To use advanced capabilities of Remote Assist, like accessing OneDrive files, scheduling one-time call, and integrating with Dynamics 365 Field Service you must assign additional licenses to the HoloLens 2 user accounts. See [Requirements for Dynamics 365 Remote Assist - Dynamics 365 Mixed Reality](https://docs.microsoft.com/en-us/dynamics365/mixed-reality/remote-assist/requirements#dynamics-365-remote-assist-app-user) for more details.

> [!NOTE]
> See [Scenarios, limitations, and known issues using groups to manage licensing in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-group-advanced) for more details.

### 3. Device Configuration
To share HoloLens 2 devices with multiple people using shared Azure AD user accounts, configure the following to secure user credentials and restrict apps to be used by the HoloLens 2 users. Follow [Set up your HoloLens 2](https://docs.microsoft.com/en-us/hololens/hololens2-start) to setup the HoloLens 2 devices for first time, using the shared Azure AD user accounts created in Azure AD Accounts section above. Use one Azure AD user account per HoloLens 2 device. During HoloLens 2 initial setup skip IRIS login configuration and configure Windows Hello PIN to login into the device (see more details below). 

#### Login PIN
Use Windows Hello PIN to login to HoloLens 2 devices. Do not share shared account passwords with end users. Configuring Windows Hello PIN allows you to not to share the user account password with end users and allows end users to login to HoloLens 2 devices using Windows Hello PIN configured for the user account on a specific HoloLens 2 device. The configured Windows Hello PIN is cryptographically tied to the HoloLens 2 device and cannot be used to login to the user account using a browser on a PC or on a different HoloLens 2 device. 
See [Share your HoloLens with multiple people](https://docs.microsoft.com/en-us/hololens/hololens-multiple-users) for more details.

#### Auto Login
You can also use AutoLogonUser policy to automatically login to the device with an identity tied to that device. This bypasses the HoloLens 2 login experience, and the user will be able to pick up the device and start using the device straight away. 
See [Auto login policy controlled by CSP](https://docs.microsoft.com/en-us/hololens/hololens-release-notes#auto-login-policy-controlled-by-csp) for more details.

#### Kiosk Mode
For shared HoloLens 2 devices, Kiosk mode is strongly recommended to control which applications are shown in Start menu when a user signs-in to HoloLens. By just allowing only required apps like Remote Assist, you can restrict users signing into the user account settings page using Edge browser by SSO and access user account details inside HoloLens 2 device.

##### A. If you use Microsoft Endpoint Manager (Intune) to manage the devices:
Navigate to [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/), and create single or multiple app kiosk mode configuration in [Devices | Configuration profiles](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles) blade. 

##### B. If you use Provisioning Packages to manage the devices:
Use Windows Configuration Designer to configure and deploy single or multiple app kiosk mode provisioning packages.
See [Set up HoloLens as a kiosk](https://docs.microsoft.com/en-us/hololens/hololens-kiosk?tabs=intunecustom%2Cnonaadlogon#steps-in-configuring-kiosk-mode-for-hololens) for more details.

#### Windows Defender Application Control (WDAC)
WDAC allows you to configure HoloLens to block the launch of apps. It is different from the Kiosk mode, where the UI hides the apps but they can still be launched. With WDAC, you can see the apps tile but they cannot be launched.
See [Windows Defender Application Control (WDAC)](https://docs.microsoft.com/en-us/hololens/windows-defender-application-control-wdac) for more details.

### 4. Limitations
Using shared Azure AD account has the following limitations (including but not limited to):
1. Identity – Users cannot use IRIS to sign in on the HoloLens 2 device and are unable to access their work account related content in Microsoft 365. 
2. Caller ID / Contacts – Accessing a user’s personal contacts list / most recently called contacts is not possible, and caller ID will show the shared account name rather than the user’s name. 
3. User Based Workflows – It is not possible to use the advanced integrations with field service, as the user being “assigned” work items, is not the user signed into Remote Assist. 
4. PIN Sharing – As IRIS sign in is not possible, Windows Hello PIN number must be shared between the users. 

### 5. Issues
Using shared Azure AD account poses the following issues to be addressed (including but not limited to):
1. Lack of accountability – With a shared account, there is no way to prove who has used the device, and what was done with the device. 
2. Lack of auditing – Audit records will be incomplete, and in the event of an incident, it could be impossible to identify the user. 
3. Lacks individual tracking / analytics. 
4. Permissions – Advanced permissions cannot be done on a shared account basis. 
5. MFA ownership – Multi-factor authentication (MFA) should be owned by a central authority for shared accounts.
6. PIN reset – When PIN needs to be reset and knowledge as to who owns the MFA on the devices is challenging.

### 6. Considerations
You must review and make changes to the following Azure AD settings (including but not limited to) when you want to use shared Azure AD user accounts. When enabling and disabling the following Azure AD settings extreme care should be taken to make sure that changing theses settings does not cause any issues for existing and new user accounts.
1. Review Administrator Portal access setting in [Users | User Settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/UserSettings) blade.
2. Review App Registrations setting in [Users | User Settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/UserSettings) blade.
3. Review Linked account connections setting in [Users | User Settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/UserSettings) blade.
4. Review User features setting in [Users | User features](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/FeatureSettingsBlade) blade.
5. Review Self-service password reset setting in [Password reset | Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/PasswordResetMenuBlade/Properties) blade.
6. Review Join devices to Azure AD setting in [Devices | Device settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/DeviceSettings/menuId/) blade.
7. Review Enterprise State Roming setting in [Devices | Enterprise State Roaming](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/RoamingSettings/menuId/) blade.

> [!WARNING]
> Do NOT share, shared account passwords with end users. End users should always use Azure AD account name and associated Windows Hello PIN or use auto login feature to login to HoloLens 2 devices in a shared environment.
