---
# required metadata

title: Discovered apps
titleSuffix: Microsoft Intune
description: Understand details about the detected apps that Intune found on a device.
keywords:
author: nicholasswhite
ms.author: nwhite
manager: laurawi
ms.date: 07/30/2025
ms.topic: how-to
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: arnab
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: 
ms.collection:
- tier1
- M365-identity-device-management
---

# Intune discovered apps

Intune **discovered apps** is a list of detected apps on the Intune enrolled devices in your tenant. It acts as a software inventory for your tenant. **Discovered apps** is a separate report from the [app installation](apps-monitor.md) reports. For personal devices, Intune never collects information on applications that are unmanaged. On corporate devices, any app whether it's a managed app or not is collected for this report. The following table shows the expected behavior. In general, the report refreshes every seven days for each device, starting from its enrollment date. This refresh isn't performed weekly for the entire tenant. The only exception to this refresh cycle for the **Discovered apps** report is application information that the Intune Management Extension for Win32 Apps collects every 24 hours.

## Monitor discovered apps with Intune

Intune provides an aggregated list of detected apps on the Intune enrolled devices in your tenant.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Monitor** > **Discovered apps**.

>[!NOTE]
>You can export the list of discovered apps to a *.csv* file by selecting **Export** from the **Discovered apps** pane.

The **Discovered apps** report provides the following details:

- Application name
- Platform
- Application version
- Device count
- Application publisher

Intune also provides the list of discovered apps for the individual device in your tenant.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **All Devices**.
3. Select a device.
4. To view detected apps for this device, select **Discovered Apps** in the **Monitor** section.

## Details of discovered apps

The following list shows the app platform type. It also shows which apps are monitored for personal devices and for company-owned devices. The refresh cycle is included as well. For more information about app types supported by Intune, see [App types in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Platform | For personally owned devices | For company-owned devices | Refresh cycle |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10/11 (Win32 Apps) NOTE: [Requires Intune Management Extension](intune-management-extension.md) on device | Not Applicable | Windows Installer apps on the device that appear in add/remove programs | Every 24 hours from device enrollment |
| Windows 10/11 (Modern Apps) | Only managed modern apps | All modern apps installed on the device | Every seven days from device enrollment |
| Windows 8.1 | Only managed apps | Only managed apps | Every seven days from device enrollment |
| Windows RT | Only managed apps | Only managed apps | Every seven days from device enrollment |
| iOS/iPadOS | Only managed apps | All apps installed on the device except system apps | Every seven days from device enrollment |
| macOS | Only managed apps | All apps installed on the device | Every seven days from device enrollment |
| Android device administrator | Only managed apps | All apps installed on the device | Every seven days from device enrollment |
| Android Enterprise personally owned enrollment | Managed apps in the work profile and system apps | Not applicable | Every seven days from device enrollment |
| Android Enterprise corporate-owned enrollments | Not applicable| Apps installed in the work profile| Every seven days from device enrollment |
| AOSP enrollments | Not applicable | Not yet supported | Not applicable |

> [!NOTE]
> - Windows 10/11 co-managed devices, as shown in the [client apps](../../configmgr/comanage/workloads.md#client-apps) workload in Configuration Manager, don't currently collect app inventory through the Intune Management Extension (IME) according to the schedule described earlier. To mitigate this issue, the [client apps](../../configmgr/comanage/workloads.md#client-apps) workload in Configuration Manager should be switched to Intune for the IME to be installed on the device (IME is required for Win32 inventory and PowerShell deployment). Any changes or updates on this behavior are announced in [in development](../fundamentals/in-development.md) and/or [what's new](../fundamentals/whats-new.md).
> - Software inventory collection for Discovered apps on Windows requires a Microsoft Entra ID user signed in to the device. For devices without a Microsoft Entra ID user signed in, Discovered apps data isn't updated.
> - Personally owned macOS devices enrolled before November 2019 might continue to show all apps installed on the device until the devices are enrolled again.
> - Android Open Source Project (AOSP) enrollments don't display discovered apps.
> - On Android Enterprise personally owned work profile devices, system apps are automatically associated with the work profile. System apps are apps that the Android operating system or device manufacturer consider essential for correct operation of the device. These apps are included in the Discovered Apps report, even if they aren't visible to the end user in the "Work" tab. To view the list of system apps that might be reported, go to **Settings** > **Apps** > **Show system apps** on the device. For more information, see [Google's Android Enterprise documentation (opens in a new page)](https://source.android.com/docs/devices/admin/implement#default-work-apps).
> - If you use a Mobile Threat Defense partner with Intune, [App Sync data](../protect/mtd-connector-enable.md) is sent to the partner based on the device check-in interval. Don't confuse this interval with the refresh interval for the Discovered Apps report.

The number of discovered apps might not match the app install status count. Possibilities for inconsistencies include:

- Changing the targeting of an installed managed app can cause the install count in the status pane to decrement, but the app remains in detected apps.
- Targeting multiple instances of the same app in a tenant results in different counts due to potential overlap of users or devices. Each instance of the app counts overlapping users, but discovered apps show duplicated counts.
- Discovered apps and app status are collected at different time intervals, which could cause a discrepancy in the app counts.

## Next steps

- [App types in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Monitor app information and assignments with Microsoft Intune](apps-monitor.md)

