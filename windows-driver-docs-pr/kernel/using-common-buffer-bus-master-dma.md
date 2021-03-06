---
title: 使用公用缓冲区总线主控 DMA
description: 使用公用缓冲区总线主控 DMA
ms.assetid: 55b5d819-e257-4863-b02a-5eeb83f72c65
keywords:
- 连续 DMA WDK 内核
- 常见缓冲区 DMA WDK 内核
- DMA 传输 WDK 内核，公共缓冲区
- 总线主控 DMA WDK 内核
- DMA 传输 WDK 内核，总线主机 DMA
- 适配器对象 WDK 内核，主线-主 DMA
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2c6948218e9cfc32d57d2c34543b8ee2a2abe5cf
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72836018"
---
# <a name="using-common-buffer-bus-master-dma"></a>使用公用缓冲区总线主控 DMA





如[使用总线主机 dma](using-bus-master-dma.md)中所述，某些用于总线主机 dma 设备的驱动程序以独占方式使用通用缓冲区 dma，一些使用常见缓冲区 dma 与基于数据包的 dma 结合使用。

经济实惠地使用公用缓冲区 DMA。 设置公用缓冲区可能会绑定与表示 bus-主适配器的适配器对象关联的映射寄存器的某些（或全部，具体取决于所请求缓冲区的大小）。

若要以经济实惠的方式设置公用缓冲区区域（例如通过使用**页面\_大小**的区块或单个分配），可为基于数据包的 DMA 操作提供更多映射寄存器。 它还会使更多系统内存可用于其他目的，从而提高整体驱动程序和系统性能。

若要为 bus master DMA 设置公用缓冲区，则总线主控 DMA 设备驱动程序必须与[**IoGetDmaAdapter**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetdmaadapter)返回的适配器对象指针一起调用[**AllocateCommonBuffer**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-pallocate_common_buffer) 。 通常，驱动程序从其[*DispatchPnP*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_dispatch)例程对 IRP\_MN 进行此调用， [ **\_启动\_设备**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-start-device)请求。 仅当驱动程序仍在加载时，驱动程序才应分配一个通用缓冲区来为其 DMA 操作重复使用该缓冲区。 下图演示了对**AllocateCommonBuffer**的调用。

![说明如何为主线主机 dma 分配公共缓冲区的关系图](images/3halcbff.png)

缓冲区的请求大小（如上图所示为 LengthForBuffer）确定必须使用多少个映射寄存器来提供公共缓冲区的虚拟到逻辑映射。 使用[ **\_\_pages**](https://docs.microsoft.com/windows-hardware/drivers/kernel/mm-bad-pointer)宏来确定所需的最大页数（ **\_到\_页面的字节**数（*LengthForBuffer*））。 此值不能大于[**IoGetDmaAdapter**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetdmaadapter)返回的*NumberOfMapRegisters* 。

此外，调用方必须提供以下内容：

-   指示是否应启用缓存的布尔值

    **注意**   此值将被忽略。 操作系统确定是否在要分配的公用缓冲区中启用缓存的内存。 该决策基于处理器体系结构和设备总线。 

    在具有基于 x64、基于 x64 和基于 Itanium 的处理器的计算机上，已启用缓存内存。 

    在基于 ARM 或 ARM 64 处理器的计算机上，操作系统不会自动为所有设备启用缓存的内存。 系统依赖于每个设备的 ACPI_CCA 方法来确定设备是否是缓存相关的。 

-   指向驱动程序定义的变量的指针，该变量将包含从**AllocateCommonBuffer**返回的缓冲区（上图中的 BufferLogicalAddress）的设备可访问基本*逻辑地址*

如果调用成功， **AllocateCommonBuffer**将为缓冲区（上图中的 BufferVirtualAddress）返回驱动程序可访问的基虚拟地址，驱动程序必须将其保存在其设备扩展、控制器扩展或其他驱动程序可访问的常驻存储区域（驱动程序分配的非分页池）。

如果**AllocateCommonBuffer**不能为缓冲区分配内存，则返回**NULL** 。 如果返回的基本虚拟地址为**NULL**，则驱动程序必须独占使用系统的基于数据包的 DMA 支持，否则，该驱动程序必须失败**IRP\_MN\_开始\_设备**请求，返回状态\_\_资源不足。

否则，驱动程序可以使用分配的公用缓冲区作为 DMA 传输的驱动程序和适配器可访问的存储区域。

当 PnP 管理器发送停止或删除设备的 IRP 时，驱动程序必须调用[**FreeCommonBuffer**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-pfree_common_buffer)来释放已分配的每个通用缓冲区。

 

 




