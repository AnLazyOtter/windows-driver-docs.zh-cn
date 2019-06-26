---
title: 在总线驱动程序中创建设备对象
description: 在总线驱动程序中创建设备对象
ms.assetid: 36b4d24c-9f5e-4853-bf70-c94613e01f2b
keywords:
- 即插即用 WDK KMDF，总线驱动程序
- 插 WDK KMDF，总线驱动程序
- 电源管理 WDK KMDF，总线驱动程序
- 总线驱动程序 WDK KMDF
- 物理设备对象 WDK KMDF
- PDOs WDK KMDF
- 总线枚举 WDK KMDF
- 枚举 WDK KMDF
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2093659341a6092b5472d4d61cb3b9dfb103d1d9
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63358699"
---
# <a name="creating-device-objects-in-a-bus-driver"></a>在总线驱动程序中创建设备对象


每个[总线驱动程序](https://msdn.microsoft.com/library/windows/hardware/ff540704)发现子设备连接到父设备时，必须创建 framework 设备对象。 父设备通常是总线，但它还可为其每个函数需要一组单独的驱动程序 （例如声卡支持数字音频和 MIDI） 的多功能设备。 总线驱动程序创建的设备对象称为物理设备对象 (PDOs)，因为每个代表一套硬件 （子级） 的实际连接到另一个 （父级）。

标识和报告连接到总线的设备的过程称为*总线枚举*。

-   如果总线驱动程序执行[动态总线枚举](dynamic-enumeration.md)，将其[ *EvtChildListCreateDevice* ](https://msdn.microsoft.com/library/windows/hardware/ff540828)回调函数接收的句柄[ **WDFDEVICE\_INIT** ](https://msdn.microsoft.com/library/windows/hardware/ff546951)结构。

-   如果总线驱动程序执行[静态总线枚举](static-enumeration.md)，它必须调用[ **WdfPdoInitAllocate** ](https://msdn.microsoft.com/library/windows/hardware/ff548786)若要获取的句柄 WDFDEVICE\_INIT 结构。

有关总线枚举的详细信息，请参阅[枚举的总线上设备](enumerating-the-devices-on-a-bus.md)。

总线驱动程序可以调用一系列[framework 设备对象初始化方法](https://msdn.microsoft.com/library/windows/hardware/dn265631#device-init-methods)，这将存储中的信息[ **WDFDEVICE\_INIT** ](https://msdn.microsoft.com/library/windows/hardware/ff546951)结构。 此外，总线驱动程序可以调用[framework PDO 初始化方法](https://msdn.microsoft.com/library/windows/hardware/dn265631#pdo-init-methods)。

创建枚举的子设备是 framework 的设备对象通常包括以下步骤：

-   正在注册总线驱动程序特定的回调函数。

    大多数总线驱动程序调用[ **WdfPdoInitSetEventCallbacks**](https://msdn.microsoft.com/library/windows/hardware/ff548805)，因为它们必须指定设备需要的系统硬件资源。 有关指定硬件资源的详细信息，请参阅[基于框架的驱动程序的硬件资源](hardware-resources-for-kmdf-drivers.md)。 如果设备和驱动程序支持弹出，则可以注册其他回调函数。

-   Reporting[设备标识字符串](https://msdn.microsoft.com/library/windows/hardware/ff541224)。

    总线驱动程序必须通过调用报告设备的标识字符串[ **WdfPdoInitAssignDeviceID**](https://msdn.microsoft.com/library/windows/hardware/ff548797)， [ **WdfPdoInitAssignInstanceID** ](https://msdn.microsoft.com/library/windows/hardware/ff548799)， [ **WdfPdoInitAddCompatibleID**](https://msdn.microsoft.com/library/windows/hardware/ff548776)，并且[ **WdfPdoInitAddHardwareID** ](https://msdn.microsoft.com/library/windows/hardware/ff548784)每种类型的字符串，设备支持。 此外，使用版本 1.9 或更高版本的 framework 的总线驱动程序可以调用[ **WdfPdoInitAssignContainerID**](https://msdn.microsoft.com/library/windows/hardware/ff548792)。

-   报告总线驱动程序是否可以在 raw 模式中支持的设备。

    如果总线驱动程序支持的设备的 raw 模式，它必须调用[ **WdfPdoInitAssignRawDevice**](https://msdn.microsoft.com/library/windows/hardware/ff548802)。

-   提供可显示的文本描述的设备。

    总线驱动程序调用[ **WdfPdoInitAddDeviceText** ](https://msdn.microsoft.com/library/windows/hardware/ff548780)并[ **WdfPdoInitSetDefaultLocale** ](https://msdn.microsoft.com/library/windows/hardware/ff548803)提供描述到设备的文本多种语言中的用户。

-   创建设备对象。

    创建设备对象的最后一步是调用[ **WdfDeviceCreate**](https://msdn.microsoft.com/library/windows/hardware/ff545926)。

如果该驱动程序时遇到错误时初始化 WDFDEVICE\_INIT 结构，它从其获取[ **WdfPdoInitAllocate**](https://msdn.microsoft.com/library/windows/hardware/ff548786)，该驱动程序必须调用[ **WdfDeviceInitFree** ](https://msdn.microsoft.com/library/windows/hardware/ff546050)而不是[ **WdfDeviceCreate**](https://msdn.microsoft.com/library/windows/hardware/ff545926)。

总线驱动程序已创建的设备对象后，它通常会调用[ **WdfDeviceSetPnpCapabilities** ](https://msdn.microsoft.com/library/windows/hardware/ff546898)并[ **WdfDeviceSetPowerCapabilities**](https://msdn.microsoft.com/library/windows/hardware/ff546901)报告设备的即插和电源功能。

每个总线驱动程序也是总线适配器的功能驱动程序。 因此，该驱动程序还必须提供[ *EvtDriverDeviceAdd* ](https://msdn.microsoft.com/library/windows/hardware/ff541693)回调函数。 此回调函数为每个系统上的总线适配器创建的功能的设备对象 (FDO)。 有关创建 FDOs 的详细信息，请参阅[功能驱动程序中创建设备对象](creating-device-objects-in-a-function-driver.md)。

 

 




