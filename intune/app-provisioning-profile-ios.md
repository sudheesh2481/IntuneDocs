---
# required metadata

title: iOS app provisioning profiles in Microsoft Intune
titlesuffix:
description: Intune gives you the tools to proactively assign a new provisioning profile to devices that have apps that are nearing expiry.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# Use iOS app provisioning profiles to prevent your apps from expiring

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## Introduction

Apple iOS line-of-business apps that are assigned to iPhones and iPads are built with an included provisioning profile and code that is signed with a certificate. When the app is run, iOS confirms the integrity of the iOS app and enforces policies that are defined by the provisioning profile. The following validations happen:

- **Installation file integrity** - iOS compares the app's details with the enterprise signing certificate's public key. If they differ, the app's content might have changed, and the app is not allowed to run.
- **Capabilities enforcement** - iOS attempts to enforce the app's capabilities from the enterprise provisioning profile (not individual developer provisioning profiles) that are in the app installation (.ipa) file.


The enterprise signing certificate that you use to sign apps typically lasts for three years. However, the provisioning profile expires after a year. While the certificate is still valid, Intune gives you the tools to proactively assign a new provisioning profile to devices that have apps that are nearing expiry.
After the certificate expires, you must sign the app again with a new certificate and embed a new provisioning profile with the key of the new certificate.

As the admin, you can include and exclude security groups to assign iOS app provisioning configuration. For example, you can assign an iOS app provisioning configuration to All Users, but exclude an executive group.

## How to create an iOS mobile app provisioning profile

1. Sign into the [Azure portal](https://portal.azure.com).
2. Choose **All services** > **Intune**. Intune is located in the **Monitoring + Management** section.
3. On the **Intune** pane, choose **Mobile apps**.
1.  In the **Mobile apps** workload, choose **Manage** > **iOS app provisioning profiles**.
2.  In the list of profiles pane, choose **Create profile**.
3. In the **Create profile** pane, configure the following values:
	- **Name** - Provide a name for this mobile provisioning profile.
	- **Description** - Optionally, provide a description for the policy.
	- **Upload profile file** - Choose **Import**, and then choose an Apple Mobile Configuration Profile file (with the extension **.mobileprovision**) that you downloaded from the Apple Developer website.
4. When you are done, choose **Create**.

## Next steps

Assign the profile to the required iOS devices. For more information, use the steps in [How to assign device profiles](device-profile-assign.md).
