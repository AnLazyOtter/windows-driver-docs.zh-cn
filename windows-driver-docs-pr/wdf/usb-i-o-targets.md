---
title: USB I/O 目标
description: 本部分介绍了 KMDF 和 UMDF 2 驱动程序如何与通用串行总线（USB）设备交互。
ms.assetid: 195c0f4b-7f33-428a-8de7-32643ad854c6
keywords:
- I/o 目标 WDK KMDF，USB
- USB i/o 目标 WDK KMDF
- USB 请求块 WDK KMDF
- URBs WDK KMDF
- USB i/o 目标 WDK KMDF，关于 USB i/o 目标
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 163ba4f1a1766b378dc86397322df0b7c7a62ab2
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843112"
---
# <a name="usb-io-targets"></a>USB I/O 目标


本部分介绍从版本2开始的内核模式驱动程序框架（KMDF）和用户模式驱动程序框架（UMDF）驱动程序如何与通用串行总线（USB）设备交互。




每个 USB 设备以及 USB 设备接口支持的每个管道都具有单独的 i/o 目标。 将 USB 设备处理的控制传输发送到设备的 i/o 目标。 I/o 会传输特定管道句柄发送到该管道的 i/o 目标。

此框架通过发送 USB 请求块（[**URBs**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usb/ns-usb-_urb)）与 usb 设备的 i/o 目标通信。 该框架提供了对象方法，这些方法可隐藏驱动程序中的 URBs，以便驱动程序无需生成并发送自身。 如果希望驱动程序生成 URBs，KMDF 驱动程序可以使用一组额外的对象方法来生成和发送 URBs。

有关如何确定 USB 设备所需的驱动程序类型的信息，请参阅[选择用于开发 usb 客户端驱动](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)程序的驱动程序模型。

本部分包括：

-   [使用 USB 设备](working-with-usb-devices.md)

-   [使用 USB 接口](working-with-usb-interfaces.md)

-   [使用 USB 管道](working-with-usb-pipes.md)

 

 





