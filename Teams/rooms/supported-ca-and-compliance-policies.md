---
title: Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: dimehta
ms.date: 05/16/2025
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords:
  - NOCSH
description: Learn about supported and recommended Conditional Access and Intune device compliance policies for Microsoft Teams Rooms.
---

# Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms and Teams Android Devices

This article provides supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms. For best practices and example policies, see [Conditional Access and Intune compliance best practices for Microsoft Teams Rooms](conditional-access-and-compliance-for-devices.md).

## Supported Conditional Access policies  

The following list includes the supported Conditional Access policies for Teams Rooms on Windows and Android as well as Teams panels and phones. 

> [!IMPORTANT]
> While configuring certain policies might be supported, they may lead to less than desired experiences on your devices, test, and confirm configurations function as intended before deploying at scale. For instance, using the sign-in frequency policy causes devices to periodically sign out and may not be desired. Likewise, configuring sign-in frequency on individual Microsoft 365 services can interrupt or stop the Teams Device sign in flow and isn't supported. Also, blocking Device Code Flow prevents using microsoft.com/devicelogin to remotely sign-in a Teams Android device.


| Assignment | Teams Rooms on Windows | Teams Rooms on Android / Teams phone / Teams Panels |
|--------|----------|---------|
| Users            | Supported | Supported |
| Target Resources | Supported <br><br> (For functionality, don't block access to: Office 365, Office 365 SharePoint Online, Microsoft Teams Services, & Device Registration Service) |Supported <br><br> (For functionality, don't block access to: Office 365, Office 365 SharePoint Online, Microsoft Teams Services, & Device Registration Service) |
| Network          | Supported| Supported |
| **Conditions**   | &nbsp; | &nbsp; |
| User risk        | Supported | Supported |
| Sign-in risk     | Supported | Supported |
| Insider risk     | Not supported | Not supported |
| Device platforms | Supported | Supported |
| Locations        | Supported | Supported |
| Client apps      | Supported | Supported |
| Filter for devices    | Supported | Supported | 
| Authentication flows  | Supported | Supported <br><br>*To use remote sign-in, don't block Device code flow.* |
| **Grant**        | &nbsp; | &nbsp; |
| Block access     | Supported | Supported |
| Grant access     | Supported | Supported |
| Require multifactor authentication | Not supported | Supported <br><br> *To enable seamless sign-on, don't enforce this policy, use a different secondary authentication factor.* |
| Require authentication strength     | Not supported | Not supported |
| Require device to be marked as compliant | Supported | Supported |
| Require Microsoft Entra hybrid joined device | Not supported | Not supported |
| Require approved client app         | Not supported | Not supported |
| Require app protection policy       | Not supported | Not supported |
| Require password change             | Not supported | Not supported |
| **Sessions**      | &nbsp; | &nbsp; |
| Use app enforced restrictions       | Not supported | Not supported |
| Use Conditional Access App Control  | Not supported | Not supported |
| Sign-in frequency                   | Supported | Supported |
| Persistent browser session          | Not supported | Not supported |
| Customize continuous access evaluation | Not supported <br><br>*If you check the box, it must be set to Disable or you'll experience instability* | Not supported <br><br>*If you check the box, it must be set to Disable or you'll experience instability* |
| Disable resiliency defaults | Not supported | Not supported | 
| Require token protection for sign-in sessions (Preview)     | Not supported | Not supported |

> [!NOTE]
> Authentication strength including but not limited to, FIDO2 Security keys, isn't supported for use with Conditional Access policies that affect all Teams Devices.

## Supported device compliance policies 

Microsoft Teams Rooms on Windows and Teams Rooms on Android support different device compliance policies.

#### [Teams Rooms on Windows](#tab/mtr-w)

Supported device compliance settings and recommendations for their use with Teams Rooms on Windows.  

| Policy | Availability | Notes |
|--------------|---------------|----------------|
| [**Device health**](/mem/intune/protect/compliance-policy-create-windows#device-health)                                     | --             | --                                                                                                                                          |
| Require BitLocker                                                                                                           | Supported      | Only use if BitLocker is enabled first.                                                                                                     |
| Require Secure Boot to be enabled on the device                                                                             | Supported      | Secure Boot is a requirement for Teams Rooms.                                                                                               |
| Require code integrity                                                                                                      | Supported      | Code integrity is already a requirement for Teams Rooms.                                                                                    |
| [**Device Properties**](/mem/intune/protect/compliance-policy-create-windows#device-properties)  --  |                                                                                                                                       |
| Operating System Version (minimum, maximum)                                                                                 | Not supported  | Teams Rooms automatically will update to newer versions of Windows and setting values here could prevent successful sign-in after an OS update. |
| OS version for mobile devices (minimum, maximum)                                                                            | Not supported. |                                                                                                                                             |
| Valid operating system builds                                                                                               | Not supported  |                                                                                                                                             |
| [**Configuration Manager Compliance**](/mem/intune/protect/compliance-policy-create-windows#device-properties)              | --             | --                                                                                                                                          |
| Require device compliance from Configuration Manager                                                                        | Supported      |                                                                                                                                             |
| [**System security**](/mem/intune/protect/compliance-policy-create-windows#system-security)                                 | --             | --                                                                                                                                          |
| All password policies                                                                                                       | Not supported  | Password policies can prevent the local Skype account from automatically signing in.                                                        |
| Require encryption of data storage on device.                                                                               | Supported      | Only use if BitLocker is enabled first.                                                                                                     |
| Firewall                                                                                                                    | Supported      | Firewall is already a requirement for Teams Rooms                                                                                           |
| Trusted Platform Module (TPM)                                                                                               | Supported      | Trusted Platform Module (TPM) is already a requirement for Teams Rooms.                                                                     |
| Antivirus                                                                                                                   | Supported      | Antivirus (Windows Defender) is already a requirement for Teams Rooms.                                                                      |
| Antispyware                                                                                                                 | Supported      | Antispyware (Windows Defender) is already a requirement for Teams Rooms.                                                                    |
| Microsoft Defender Anti-malware                                                                                              | Supported      | Microsoft Defender Anti-malware is already a requirement for Teams Rooms.                                                                    |
| Microsoft Defender Anti-malware minimum version                                                                              | Not supported. | Teams Rooms will automatically update this component so there's no need to set compliance policies.                                         |
| Microsoft Defender Anti-malware security intelligence up-to-date                                                             | Supported      | Validate that Microsoft Defender Anti-malware is already a requirement for Teams Rooms.                                                      |
| Real-time protection                                                                                                        | Supported      | Real-time protections are already a requirement for Teams Rooms.                                                                            |
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-windows#microsoft-defender-for-endpoint) | --             | --                                                                                                                                          |
| Require the device to be at or under the machine risk score.                                                                | Supported      |                                                                                                                                             |

#### [Teams Rooms on Android (AOSP DM)](#tab/mtr-a)

Supported device compliance settings for Teams Rooms on Andorid devices enrolled with AOSP Device Management (AOSP DM).  

| Policy | Availability | Notes |
|--------------|---------------|----------------|
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android-aosp#device-health)                                            | --            | --                                                                            |
| Rooted devices                                                                                                                          | Supported     |                                                                               |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android-aosp#device-properties)                                    | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| Minimum security patch level                                                                                                            | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android-aosp#system-security)                                        | --            | --                                                                            |
| Require a password to unlock mobile devices                                                                                             | Not supported | Teams Devices don't support a password unlock.                               |
| Required password type                                                                                                                  | Not supported | Teams Devices don't support a password unlock.                               |
| Maximum minutes of inactivity before password is required                                                                               | Not supported | Teams Devices don't support a password unlock.                               |
| Require encryption of data storage on device.                                                                                           | Supported     |                                                                               |

#### [Teams phones and displays (AOSP DM)](#tab/phones)

Supported device compliance settings for Teams phone and displays enrolled with AOSP Device Management (AOSP DM).  

| Policy | Availability | Notes |
|--------------|---------------|----------------|
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android-aosp#device-health)                                            | --            | --                                                                            |
| Rooted devices                                                                                                                          | Supported     |                                                                               |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android-aosp#device-properties)                                    | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| Minimum security patch level                                                                                                            | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android-aosp#system-security)                                        | --            | --                                                                            |
| Require a password to unlock mobile devices                                                                                             | Not supported | Teams Devices don't support a password unlock.                               |
| Required password type                                                                                                                  | Not supported | Teams Devices don't support a password unlock.                               |
| Maximum minutes of inactivity before password is required                                                                               | Not supported | Teams Devices don't support a password unlock.                               |
| Require encryption of data storage on device.                                                                                           | Supported     |                                                                               |

#### [Teams panels (AOSP DM)](#tab/panels)

Supported device compliance settings for Teams panels enrolled with AOSP Device Management (AOSP DM).  

| Policy | Availability | Notes |
|--------------|---------------|----------------|
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android-aosp#device-health)                                            | --            | --                                                                            |
| Rooted devices                                                                                                                          | Supported     |                                                                               |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android-aosp#device-properties)                                    | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| Minimum security patch level                                                                                                            | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android-aosp#system-security)                                        | --            | --                                                                            |
| Require a password to unlock mobile devices                                                                                             | Not supported | Teams Devices don't support a password unlock.                               |
| Required password type                                                                                                                  | Not supported | Teams Devices don't support a password unlock.                               |
| Maximum minutes of inactivity before password is required                                                                               | Not supported | Teams Devices don't support a password unlock.                               |
| Require encryption of data storage on device.                                                                                           | Supported     |                                                                               |


#### [Teams Rooms on Android (ADA)](#tab/mtr-a-da)

Device compliance settings and recommendations for their use with Teams Rooms on Android devices enrolled using Android Device Administrator (ADA).  

| Policy | Availability | Notes |
|--------------|---------------|----------------|
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-android#microsoft-defender-for-endpoint)             | --            | --                                                                            |
| Require the device to be at or under the machine risk score                                                                             | Not supported |                                                                               |
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android#device-health)                                                 | --            | --                                                                            |
| Device managed with device administrator                                                                                                | Required      | Teams Android devices management requires device administrator to be enabled. |
| Rooted devices                                                                                                                          | Supported     |                                                                               |
| Require the device to be at or under the device threat level                                                                            | Not supported |                                                                               |
| [**Google Play Protect**](/mem/intune/protect/compliance-policy-create-android#device-health)                                           | --            | --                                                                            |
| Google Play Services is configured                                                                                                      | Not supported | Google play isn't installed on Teams Android devices.                         |
| Up-to-date security provider                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| Threat scan on apps                                                                                                                     | Not supported | Google play isn't installed on Teams Android devices.                         |
| SafetyNet device attestation                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android#device-properties)                                         | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android#system-security)                                             | --            | --                                                                            |
| Require encryption of data storage on device.                                                                                           | Supported     |                                                                               |
| [**Device security**](/mem/intune/protect/compliance-policy-create-android#device-security)                                             | --            | --                                                                            |
| Block apps from unknown sources                                                                                                         | Not supported | Only Teams admins install apps or OEM tools                                   |
| Company Portal app runtime integrity                                                                                                    | Supported     |                                                                               |
| Restricted apps                                                                                                                         | Not supported |                                                                               |
| Block USB debugging on device                                                                                                           | Not Supported | Not Applicable. ADB enablement isn't allowed on production devices.  |
| [**All Android devices*](/mem/intune/protect/compliance-policy-create-android#all-android-devices)                                      | --            | --                                                                            |
| Maximum minutes of inactivity before password are required   | Not supported |
| Require a password to unlock mobile devices                                                                                             | Not supported |                                                                               |
| [**Android 10 and later**](/mem/intune/protect/compliance-policy-create-android#android-10-and-later)                                   | --            | --                                                                            |
| [**Android 9 and earlier or Samsung Knox**](/mem/intune/protect/compliance-policy-create-android#android-9-and-earlier-or-samsung-knox) | --            | --                                                                            |
| Required password type                                                                                                                  | Not supported |                                                                               |

#### [Teams phones and displays (ADA)](#tab/phones-da)

Device compliance settings and recommendations for their use with Teams phones and displays enrolled using Android Device Administrator (ADA).  

| Policy | Availability | Notes |
|--------------|---------------|----------------|
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-android#microsoft-defender-for-endpoint)             | --            | --                                                                            |
| Require the device to be at or under the machine risk score                                                                             | Not supported |                                                                               |
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android#device-health)                                                 | --            | --                                                                            |
| Device managed with device administrator                                                                                                | Required      | Teams Android devices management requires device administrator to be enabled. |
| Rooted devices                                                                                                                          | Supported     |                                                                               |
| Require the device to be at or under the device threat level                                                                            | Not supported |                                                                               |
| [**Google Play Protect**](/mem/intune/protect/compliance-policy-create-android#device-health)                                           | --            | --                                                                            |
| Google Play Services is configured                                                                                                      | Not supported | Google play isn't installed on Teams Android devices.                         |
| Up-to-date security provider                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| Threat scan on apps                                                                                                                     | Not supported | Google play isn't installed on Teams Android devices.                         |
| SafetyNet device attestation                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android#device-properties)                                         | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android#system-security)                                             | --            | --                                                                            |
| Require encryption of data storage on device.                                                                                           | Supported     |                                                                               |
| [**Device security**](/mem/intune/protect/compliance-policy-create-android#device-security)                                             | --            | --                                                                            |
| Block apps from unknown sources                                                                                                         | Not supported | Only Teams admins install apps or OEM tools                                   |
| Company Portal app runtime integrity                                                                                                    | Supported     |                                                                               |
| Restricted apps                                                                                                                         | Not supported |                                                                               |
| Block USB debugging on device                                                                                                           | Not Supported | Not Applicable. ADB enablement isn't allowed on production devices.  |
| [**All Android devices*](/mem/intune/protect/compliance-policy-create-android#all-android-devices)                                      | --            | --                                                                            |
| Maximum minutes of inactivity before password are required                                                                              | Not supported |                                                                               |
| Require a password to unlock mobile devices                                                                                             | Not supported |                                                                               |
| [**Android 10 and later**](/mem/intune/protect/compliance-policy-create-android#android-10-and-later)                                   | --            | --                                                                            |
| [**Android 9 and earlier or Samsung Knox**](/mem/intune/protect/compliance-policy-create-android#android-9-and-earlier-or-samsung-knox) | --            | --                                                                            |
| Required password type                                                                                                                  | Not supported |                                                                               |

#### [Teams panels (ADA)](#tab/panels-da)

Device compliance settings and recommendations for their use with Teams panels enrolled using Android Device Administrator (ADA).  

| Policy | Availability | Notes |
|--------------|---------------|----------------|
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-android#microsoft-defender-for-endpoint)  | --            | --                                                                            |
| Require the device to be at or under the machine risk score    | Not supported |                    |
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android#device-health)                                                 | --            | --                       |
| Device managed with device administrator       | Required   | Teams Android devices management requires device administrator to be enabled. |
| Rooted devices    | Supported     |            |
| Require the device to be at or under the device threat level  | Not supported |              |
| [**Google Play Protect**](/mem/intune/protect/compliance-policy-create-android#device-health)                                           | --            | --                                                                            |
| Google Play Services is configured                                                                                                      | Not supported | Google play isn't installed on Teams Android devices.                         |
| Up-to-date security provider                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| Threat scan on apps                                                                                                                     | Not supported | Google play isn't installed on Teams Android devices.                         |
| SafetyNet device attestation                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android#device-properties)                                         | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android#system-security)                                             | --            | --                                                                            |
| Require encryption of data storage on device.                                                                                           | Supported     |                                                                               |
| [**Device security**](/mem/intune/protect/compliance-policy-create-android#device-security)                                             | --            | --                                                                            |
| Block apps from unknown sources                                                                                                         | Not supported | Only Teams admins install apps or OEM tools                                   |
| Company Portal app runtime integrity                                                                                                    | Supported     |                                                                               |
| Restricted apps                                                                                                                         | Not supported |                                                                               |
| Block USB debugging on device                                                                                                           | Not Supported | Not Applicable. ADB enablement isn't allowed on production devices.  |
| [**All Android devices*](/mem/intune/protect/compliance-policy-create-android#all-android-devices)                                      | --            | --                                                                            |
| Maximum minutes of inactivity before password are required                                                                              | Not supported |                                                                               |
| Require a password to unlock mobile devices                                                                                             | Not supported |                                                                               |
| [**Android 10 and later**](/mem/intune/protect/compliance-policy-create-android#android-10-and-later)                                   | --            | --                                                                            |
| [**Android 9 and earlier or Samsung Knox**](/mem/intune/protect/compliance-policy-create-android#android-9-and-earlier-or-samsung-knox) | --            | --                                                                            |
| Required password type                                                                                                                  | Not supported |                                                                               |

