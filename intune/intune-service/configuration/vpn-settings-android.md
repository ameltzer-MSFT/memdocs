---
# required metadata

title: Use VPN settings for Android DA devices in Microsoft Intune
description: See all the settings to create VPN connections on Android device administrator devices in Microsoft Intune. Enter the connection name, IP address, or FQDN of the VPN server. Choose how users authenticate, and choose Citrix, SonicWall, Check Point Capsule, and Pulse Secure connection types.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: laurawi
ms.date: 06/09/2025
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: abalwan
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection:
- tier3
- M365-identity-device-management
---

# Android device administrator settings that configure VPN in Intune

This article describes the different VPN connection settings you can control on Android devices. As part of your mobile device management (MDM) solution, use these settings to create a VPN connection, choose how the VPN authenticates, select a VPN server type, and more.

This feature applies to:

- Android device administrator (DA)

As an Intune administrator, you can create and assign VPN settings to Android devices. To learn more about VPN profiles in Intune, go to [VPN profiles](vpn-settings-configure.md).

[!INCLUDE [android_device_administrator_support](../includes/android-device-administrator-support.md)]

## Before you begin

- Create an [Android device administrator VPN device configuration profile](vpn-settings-configure.md).

- [!INCLUDE [partner-vpns](../includes/partner-vpns.md)]

## Base VPN

- **Connection name**: Enter a name for this connection. End users see this name when they browse their device for the available VPN connections. For example, enter `Contoso VPN`.
- **VPN server address**: Enter the IP address or fully qualified domain name (FQDN) of the VPN server that devices connect. For example, enter `192.168.1.1` or `vpn.contoso.com`.
- **Authentication method**: Select how devices authenticate to the VPN server. Your options:

  - **Certificates**: Select an existing SCEP or PKCS certificate profile to authenticate the connection. [Configure certificates](../protect/certificates-configure.md) lists the steps to create a certificate profile.
  - **Username and password**: When users sign into the VPN server, they're prompted to enter their user name and password.

    For more information, go to [Use derived credentials in Intune](../protect/derived-credentials.md).

- **Connection type**: Select the VPN connection type. Your options:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **Fingerprint** (Check Point Capsule VPN only): Enter the fingerprint string given to you by the VPN vendor, like `Contoso Fingerprint Code`. This fingerprint verifies that the VPN server can be trusted.

  When authenticating, a fingerprint is sent to the client so the client knows to trust any server that has the same fingerprint. If the device doesn't have the fingerprint, it prompts the user to trust the VPN server while showing the fingerprint. The user manually verifies the fingerprint, and chooses to trust to connect.

## Related articles

- [Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).

- Create VPN profiles for [Android Enterprise](vpn-settings-android-enterprise.md), [iOS/iPadOS](vpn-settings-ios.md), [macOS](vpn-settings-macos.md), and [Windows](vpn-settings-windows-10.md).
