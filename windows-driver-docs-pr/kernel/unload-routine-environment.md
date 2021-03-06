---
title: Unload 例程环境
description: Unload 例程环境
ms.assetid: 4acf66f1-7b97-494e-9f84-14292e971542
keywords:
- 卸载例程，WDK 内核，环境
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: 17d56760466fa4ab827ff326029f14094544d246
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72836093"
---
# <a name="unload-routine-environment"></a>Unload 例程环境





当替换驱动程序时，或在删除驱动程序服务的所有设备时，操作系统将卸载驱动程序。 如果驱动程序在处理[**IRP\_MN\_删除\_设备**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-remove-device)请求后，该驱动程序没有更多设备对象，则 pnp 管理器会调用 pnp 驱动程序的[*Unload*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_unload)例程。

卸载序列开始时，i/o 管理器或 PnP 管理器将驱动程序对象及其设备对象标记为 "卸载挂起"。 将驱动程序标记为 "卸载挂起" 后，没有其他驱动程序可以附加到该驱动程序，也不能对驱动程序的设备对象进行任何其他引用。 驱动程序可以完成未完成的 Irp，但系统不会将任何新的 Irp 发送到该驱动程序。

当满足以下所有条件时，i/o 管理器会调用驱动程序的*Unload*例程：

-   任何引用都不会保留到驱动程序已创建的任何设备对象。 换句话说，不能打开与基础设备关联的任何文件，也不能为驱动程序的任何设备对象完成任何 Irp。

-   此驱动程序不会再附加任何驱动程序。

-   驱动程序调用了[**IoUnregisterPlugPlayNotification**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iounregisterplugplaynotification)来注销之前注册的所有 PnP 通知。

请注意，如果驱动程序的[**DriverEntry**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_initialize)例程返回失败状态，则不会调用*Unload*例程。 在这种情况下，i/o 管理器只释放驱动程序占用的内存空间。

PnP 管理器和 i/o 管理器都不会在系统关闭时调用*卸载*例程。 必须执行关闭处理的驱动程序应注册[*DispatchShutdown*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_dispatch)例程。

 

 




