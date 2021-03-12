# Prepare - Corporate Connected Guide
## Infrastructure Essentials
For both personal and corporate deployment scenarios, an MDM system is the essential infrastructure required to deploy and manage Windows 10 Holographic devices. An [Azure AD Premium subscription](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-get-started-premium) is recommended as an identity provider and required to support certain capabilities.

## Azure Active Directory
Azure AD is a cloud-based directory service that provides identity and access management. Organizations that use Microsoft Office 365 or Intune are already using Azure AD, which has three editions: Free, Premium P1, and Premium P2 (see [Azure Active Directory editions](https://azure.microsoft.com/documentation/articles/active-directory-editions)). All editions support Azure AD device registration, but Premium P1 is required to enable MDM auto-enrollment which we will be using in this guide later.
> !Important - It is essential to have an Azure Active Directory as HoloLens devices do not support on-premises AD join. If you don't already have an Azure Active Directory set up, follow the instructions in this link to get started and [Create a new tenant in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).

## Identity Management
In this guide we have chosen that for the Identity used, we will use Azure AD accounts, or Azure Active Directory accounts. There are several benefits to Azure AD accounts we would like to use, such as:
- Employees use their Azure AD account to register the device in Azure AD and can automatically enroll it with the organization's MDM solution (Azure AD+MDM – requires Azure AD Premium subscription).
- Azure AD accounts support Single Sign On. When a user signs into Guides, their Identity from the signed in Azure AD user will be recognized and the user will be signed into the app for a streamlined experience.
- Azure AD accounts have additional authentication options via Windows Hello for Business. In addition to Iris log-in, users can sign in from another device or use FIDO security keys.

> [!Note] 
> Employees can use only one account to initialize a device so it's imperative that your organization controls which account is enabled first. The account chosen will determine who controls the device and influence your management capabilities.

## Mobile Device Management
Microsoft Intune, part of the Enterprise Mobility + Security, is a cloud-based MDM system that manages devices connected to your tenant. Like Office 365, Intune uses Azure AD for identity management, so employees use the same credentials to enroll devices in Intune that they use to sign into Office 365. Intune also supports devices that run other operating systems, such as iOS and Android, to provide a complete MDM solution. For the purposes of this guide, we'll be focusing on using Intune for enabling a deployment to your internal network with HoloLens 2.
> [!Important] 
> It is essential to have Mobile Device Management. If you don't already have it set up, follow this guide and Get started with Intune.

> [!Important]
> In order to use Guides an Azure AD account is required.

> [!Note] 
> Multiple MDM systems support Windows 10 and most support personal and corporate device deployment scenarios. MDM providers that support Windows 10 Holographic currently include: AirWatch, MobileIron, and others. Most industry-leading MDM vendors already support integration with Azure AD. You can find the MDM vendors that support Azure AD in Azure Marketplace.

## Certificates
Certificates help improve security by providing account authentication, Wi-Fi authentication, VPN encryption, and SSL encryption of web content. Although administrators can manage certificates on devices manually through provisioning packages, it’s a best practice to use your MDM system to manage those certificates throughout their entire lifecycle – from enrollment through renewal and revocation. 

Your MDM system can automatically deploy these certificates to the devices’ certificate stores after you enroll the device (as long as your MDM system supports the **Simple Certificate Enrollment Protocol (SCEP)** or **Public Key Cryptography Standards #12 (PKCS#12)**). [Learn about certificate types and profiles you use with Microsoft Intune](https://docs.microsoft.com/mem/intune/protect/certificates-configure). MDM can also query and delete enrolled client certificates or trigger a new enrollment request before the current certificate is expired.
 
If your MDM systems is already configured for certificates, reference [Prepare certificates and network profiles for HoloLens 2](https://docs.microsoft.com/hololens/hololens-certificates-network) to start deploying certificates and profiles for your HoloLens 2 devices.

## SCEP
### Requirements
The following services are required for SCEP deployment, with the exception of the Web Application Proxy Server.
- Certification Authority
- NDES Server role
- Microsoft Intune Connector

You must also publish your NDES URL external to your corporate network using [Azure AD application proxy or Web Access Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application). You can also use another reverse proxy of your choice.

If your network does not already support SCEP, or you are unsure if your network is correctly set up for SCEP with Intune, reference  [Configure infrastructure to support SCEP with Intune](https://docs.microsoft.com/mem/intune/protect/certificates-scep-configure).

If your infrastructure already supports SCEP, you will need to create a [profile](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/create-certificate-profiles) for each SCEP certificate that the HoloLens 2 will use. Reference [Create and assign SCEP certificate profiles in Intune](https://docs.microsoft.com/en-us/mem/intune/protect/certificates-profile-scep). If you are having issues with SCEP, reference [Troubleshoot use of SCEP certificate profiles to provision certificates with Microsoft Intune](https://docs.microsoft.com/troubleshoot/mem/intune/troubleshoot-scep-certificate-profiles).

## PKCS
Intune also supports the use of private and public key pair (PKCS) certificates. Reference [Use private and public key certificates in Microsoft Intune](https://docs.microsoft.com/mem/intune/protect/certificates-pfx-configure) for more information.

## Proxy
Most corporate intranet networks leverage a proxy to manage external traffic. With HoloLens 2 you can configure a proxy server for ethernet, Wi-Fi and VPN connections.

There are a few different types of proxy and ways to configure proxy. For the purposes of this guide, we are opting to choose Wi-Fi proxy, set via PAC URL, and deployed via MDM. This comes with the advantages of being deployed via MDM automatically, being able to update the PAC file instead of using a server:port configuration, and finally using Wi-Fi proxy to configure proxy to only apply to a single Wi-Fi connection allowing the devices to be used still if connected in another location. 

For more details on proxy settings for Windows 10, see [Create a Wi-Fi profile for devices in Microsoft Intune - Azure | Microsoft Docs](https://docs.microsoft.com/mem/intune/configuration/wi-fi-settings-configure).
## Line of Business Apps 
While several apps can be installed via the Microsoft Store, it is likely you have your own custom app that you have created specifically to use in mixed reality. These custom apps distributed throughout your organization for your business are called Line of Business (LOB) apps.
  
There are multiple ways to deploy applications to HoloLens 2 devices. Apps can be deployed directly through MDM, the Microsoft Store for Business, or sideloaded through a Provisioning Package. For the sake of this guide we will be deploying apps via, MDM, through the use of require app install. This will allow for your line of business apps to be automatically downloaded to your HoloLens devices once they finish enrollment.

For those of you who do not have your own LOB, we will provide a sample app to test this deployment flow. This app will be the MRTK Examples app, and has already been prebuilt and packaged to test for proof of concept.
 
More details regarding app deployment can be found [here](https://docs.microsoft.com/hololens/app-deploy-overview).

> [!NOTE]
> HoloLens 2 supports running of UWP ARM64 apps only.

## Guides Playbook
Dynamics 365 Guides uses a Microsoft Dataverse environment to provide control over deployments. It’s important to understand the bigger picture of how your Dataverse environment interacts with your Guides apps and your tenant. We won’t be covering how to manage your dataverse in this guide, but please review the following information - [Basic concepts for deploying Dynamics 365 Guides - Dynamics 365 Mixed Reality | Microsoft Docs](https://docs.microsoft.com/dynamics365/mixed-reality/guides/admin-deployment-playbook).
