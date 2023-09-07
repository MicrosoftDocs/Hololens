---
title: Shared AAD accounts in HoloLens
description: Learn about how to use Shared AAD accounts in HoloLens
author: lolab
ms.author: lolab
keywords: HoloLens, shared accounts, AAD
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: qizho
manager: nazara
ms.date: 09/06/2023

---

# Shared AAD accounts in HoloLens

Shared Azure Active Directory (AAD) accounts on HoloLens are AAD user accounts that are assigned to a specific device. These accounts are only accessed on those devices and can be accessed without having to enter credentials. This setup is ideal for scenarios where the following conditions are true:

•	Multiple people share the same set of HoloLens devices

•	Access to AAD resources, such as Dynamics 365 Guides content is required

•	Tracking who has used the device is not required.

Before shared AAD account support on HoloLens, customers wishing to deploy shared accounts were either restricted to local accounts (via Guest/Visitor accounts) or manual AAD account setup. Local accounts do not provide the user easy access to apps that depend on AAD resources, such as Remote Assist. Manual AAD account setup is a slow process that is difficult to deploy. Shared AAD account support on HoloLens allows you to address both problems by providing easy access to AAD resources on your HoloLens devices, and can be deployed without requiring manual setup for each device.

> [!IMPORTANT]
> Since shared AAD accounts can be accessed on the HoloLens device without entering credentials, you should physically secure these HoloLens devices so that only authorized personnel have access. You may also want to lock down these accounts by applying conditional access policies, disabling self-service password reset, and configuring assigned access profiles to the devices where these accounts are used.

> [!NOTE]
>  Since these are shared accounts, users using these accounts are not shown the typical first sign-in setup screens, including PIN and iris enrollments, biometric data collection notice, and various consent screens. You should ensure that the appropriate defaults are configured for these accounts via policy (see [Set up users on HoloLens 2 quickly](/hololens2-new-user-optimize?tabs=firstBlank%2CsecondBlank#additional-policies)) and that your users are aware of these defaults.

At a high level, shared AAD accounts on HoloLens are implemented as regular AAD user accounts that are configured for AAD certificate-based authentication (CBA). The HoloLens devices are then configured so that they receive the necessary client certificates to perform CBA and the instructions about which certificates are valid for CBA. Once properly configured, the HoloLens device offers the shared AAD account as an option on the sign-in screen.

This document guides you to:

1.	Configure your AAD tenant to enable AAD CBA for a select group of accounts.

2.	Configure Microsoft Intune to apply device configurations to a select group of devices that:

    a.	Deploys client certificates used for AAD CBA onto the devices via Intune’s SCEP certificate profiles.
   
    b.	Deploys shared account configuration instructing the device which certificates are valid for AAD CBA.

4.	Prepares individual devices for shared AAD accounts.

## Prerequisites

Shared AAD account support is available starting in [Insider preview for Microsoft HoloLens](/hololens/hololens-insider) build 10.0.22621.1217.

In addition to having the required operating system build on your HoloLens, you also need to satisfy the prerequisites for AAD CBA ([How to configure Azure AD certificate-based authentication](/azure/active-directory/authentication/how-to-certificate-based-authentication#prerequisites)).

Finally, you need access to Microsoft Intune in order to deploy device configurations and client certificates. For required infrastructure to deploy client certificates via Intune, see [Learn about the types of certificate that are supported by Microsoft Intune](/mem/intune/protect/certificates-configure#whats-required-to-use-certificates).

## AAD Tenant configuration

Your AAD tenant must be configured to enable AAD CBA for a select group of users.  

1.	Create an AAD group that contains the shared AAD accounts. As an example, we use the name “SharedAccounts” for this group.

2.	Create an AAD group that contains the shared HoloLens devices. As an example, we use the name “SharedDevices” for this group.

3.	Enable AAD certificate-based authentication (CBA) for the SharedAccounts group For a complete step-by-step guide, refer to [How to configure Azure AD certificate-based authentication](/azure/active-directory/authentication/how-to-certificate-based-authentication#prerequisites). The following high-level steps are needed to set this up:

    a.	Add your (Certificate Authority) CA certificate to AAD. AAD allows client certificates issued by this CA to perform CBA.
  	
    b.	Enable CBA for the “SharedAccounts” group.
  	
    c.	Configure CBA such that the certificate issued by your CA uses MFA to ensure that users can access resources that require MFA without setting up another factor.
  	
    d.	Enable certificate binding via UserPrincipalName.

## Intune configuration

Intune must be configured to deploy the certificates necessary for AAD CBA.  These instructions also address which certificates are valid for AAD CBA.  Certificates are managed via [custom OMA-URI](/mem/intune/configuration/custom-settings-windows-10) policy.

1.	Create a custom device configuration policy and assign it to “SharedDevices”:

    - URI value: ./Vendor/MSFT/Policy/Config/MixedReality/ConfigureSharedAccount

| Policy | Data Type| 
| -------- | -------- |
| ./Vendor/MSFT/Policy/Config/MixedReality/ConfigureSharedAccount | String or String (XML file) |

You may customize the restrictions for which certificates are displayed for CBA. The above example requires that the issuer’s certificate thumbprint matches the provided value. It’s also possible to apply the restriction based on the issuer’s name, or apply more restrictions based on Extended Key Usages (EKUs) on the certificate. See Appendix B – ConfigureSharedAccount XML Examples for examples on how to configure the XML. 

Before saving this device configuration, ensure that you’ve validated the XML against the schema specified in Appendix A to ensure it’s well-formed.

2.	Create a SCEP configuration and assign it to “SharedDevices”:

    a.	Certificate type: Device

    b.	Add a User principal name (UPN) Subject alternative name (SAN) where the value is the UPN of the shared account assigned to the device. The UPN must contain the device serial number. You can use the Intune variable {{Device_Serial}} to refer to the device serial number. For example, enter a value of HL-{{Device_Serial}}@contoso.com if the shared accounts have a name format of HL-123456789@contoso.com.

   c.	Key storage provider (KSP): Require TPM, otherwise fail.
   
   d.	Ensure that the certificate has at least the following Extended key usages (EKUs):
   
    i.	Smartcard Logon – 1.3.6.1.4.1.311.20.2.2
      
    ii.	Client Authentication – 1.3.6.1.5.5.7.3.2
      
You may add EKUs to this list if you’ve configured other EKU requirements in step 1.

Full documentation for configuring SCEP in Intune: [Use SCEP certificate profiles with Microsoft Intune](/mem/intune/protect/certificates-profile-scep).

3.	Create a trusted certificate configuration and assign it to “SharedDevices” group. This assignment deploys your CA certificate to the devices. See documentation: [Create trusted certificate profiles in Microsoft Intune](/mem/intune/protect/certificates-trusted-root).

## Individual device configuration

For each HoloLens device that you want to configure for shared AAD accounts, perform the following steps:

1.	Create an AAD user in the format specified in section 2.b of the Intune configuration already described.

2.	Add that user to the “SharedAccounts” group.

3.	Add the AAD device to the “SharedDevices” group. Note this is simpler if you first configure these devices for Autopilot so that they are present in AAD without requiring the devices to be joined to AAD first.  See Appendix C for an example of a powershell script that can be used to automate this process.

## Testing your configuration

Once you’ve completed the above configuration, you’re ready to try out shared AAD accounts on HoloLens!

If your device is configured for Autopilot already, simply take the device through its normal Autopilot flow. The necessary device configurations are applied during Autopilot. Once the Autopilot flow is completed, you see the following screen:


Now click on the “Sign in” button to start using the shared AAD account; no credentials are necessary!

It’s highly recommended to configure these shared devices with Autopilot to simplify the device setup process.

## Troubleshooting

**Problem: The shared AAD account isn’t showing on the sign-in screen!**

**Solution:** First, check that the device is receiving the correct certificates. Open the certificate manager ([Certificate Manager](/hololens/certificate-manager)) and make sure that both the client certificate and the CA certificates are successfully deployed to the device. 

For the client certificate, ensure that it is installed to the “My” store on “Local Machine.”

Also ensure that the certificate is within the validity dates has the expected issuer and EKUs:

Next, ensure that the XML policy value you’ve applied to MixedReality/ConfigureSharedAccount is well-formed. You can use one of the many XML schema (XSD) validators online to check that your XML conforms to the schema described in Appendix A.

**Problem:  The sign in attempt fails!**

**Solution:**  Check that you’ve properly configured CBA following the instructions on [How to configure Azure AD certificate-based authentication](/azure/active-directory/authentication/how-to-certificate-based-authentication). Also, check out the [FAQ on Azure AD certificate-based authentication (CBA) FAQ](/azure/active-directory/authentication/certificate-based-authentication-faq). Sometimes it may be helpful to try these debug steps on a Windows desktop device first: [Windows smart card sign-in using Azure Active Directory certificate-based authentication](/azure/active-directory/authentication/concept-certificate-based-authentication-smartcard).

## Appendix A--ConfigureSharedAccount XML Schema

## Appendix B--ConfigureSharedAccount XML Examples

Require that the issuer certificate has a subject of CN=yourCA, DC=Test:

Require that the issuer certificate has a specified thumbprint:

Require that the issuer certificate has a specified thumbprint and that the client certificate has EKUs with OIDs 1.2.3.4.5.6 and 1.2.3.4.5.7:

Note that EKUs 1.3.6.1.4.1.311.20.2.2 (Smartcard Logon) and 1.3.6.1.5.5.7.3.2 (Client Authentication) are always required regardless of whether they’re in this list.

## Appendix C--Example device setup script


