---
title: 将筛选器驱动程序移植到 NDIS 6.20 所要做出的更改摘要
description: 将筛选器驱动程序移植到 NDIS 6.20 所要做出的更改摘要
ms.assetid: faf83399-b9ac-41b3-a891-0142ded422b3
keywords:
- NDIS 6.20 WDK，移植筛选器驱动程序
- 将筛选器驱动程序移植到 NDIS 6.20 WDK
- 筛选器驱动程序 WDK
- 筛选器驱动程序 WDK，移植到 NDIS 6.20
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e9b5bea66179d54a7037059660b79141877b5dbe
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72841813"
---
# <a name="summary-of-changes-required-to-port-a-filter-driver-to-ndis-620"></a>将筛选器驱动程序移植到 NDIS 6.20 所要做出的更改摘要





本主题概述了移植 NDIS 6 所需的更改。*x*筛选器驱动程序到 NDIS 6.20。

NDIS 6.20 保持与早期的 NDIS 版本的向后兼容性。 有关向后兼容性的详细信息，请参阅[NDIS 6.20 向后兼容性](ndis-6-20-backward-compatibility.md)。

若要更新筛选器驱动程序以支持 NDIS 6.20 环境，必须修改 NDIS 1.x 筛选器驱动程序，如下所示：

<a href="" id="build-environment"></a>**生成环境**  
将预处理器定义 NDIS61 或 NDIS60 替换为 NDIS620。

<a href="" id="general-porting-requirements"></a>**一般移植要求**  
-   将过时的接口替换为 NDIS 6.20 版本。 有关过时接口的详细信息，请参阅[NDIS 6.20 中的过时接口](obsolete-interfaces-in-ndis-6-20.md)。

-   更新以下接口以支持超过64个处理器：

    -   接收方缩放（RSS）
    -   处理器信息设备驱动程序接口
    -   资源分配
    -   读取和写入锁

    有关支持超过64个处理器的详细信息，请参阅[NDIS 6.20 中对超过64个处理器的支持](support-for-more-than-64-processors-in-ndis-6-20.md)。

<a href="" id="driver-initialization"></a>**驱动程序初始化**  
-   在 Ndis\_筛选器的**MajorNdisVersion**和**MinorNdisVersion**成员中，将 ndis 版本设置为6.20，并将[ **\_驱动程序\_特性**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_filter_driver_characteristics)结构传递到[**NdisFRegisterFilterDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfregisterfilterdriver)才能.

-   在 NDIS\_筛选器的**MajorDriverVersion**和**MinorDriverVersion**成员中设置筛选器驱动程序版本，将\_驱动程序\_特征结构设置为合适的特定于驱动程序值。

<a href="" id="filter-module-attach-and-detach-operations"></a>**筛选模块附加和分离操作**  
-   使用最新版本的微型端口适配器功能播发接口。 以下接口具有更新的功能：
    -   电源管理
    -   接收方缩放（RSS）
    -   硬件协助（VMQ）
-   使用这些结构的更新版本：

    -   [ **\_附加\_参数的 NDIS\_筛选器**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_filter_attach_parameters)
    -   [**NDIS\_卸载\_参数**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload_parameters)

    有关 NDIS 结构版本信息的信息，请参阅[指定 Ndis 版本信息](specifying-ndis-version-information.md)。

<a href="" id="send-and-receive-data-paths"></a>**发送和接收数据路径**  
-   使用[**NET\_缓冲区**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer)结构的更新版本。

-   （可选）支持虚拟机队列（VMQ）接口。 有关 VMQ 的详细信息，请参阅[NDIS 6.20 中的虚拟机队列（VMQ）](virtual-machine-queue--vmq--in-ndis-6-20.md)。

 

 





