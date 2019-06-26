---
title: VMQ 接收筛选器
description: VMQ 接收筛选器
ms.assetid: b5dbd716-1d92-400c-b612-a70de690baef
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: d67f80ac629d8d8a468f6194a823edce065e23d6
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63327582"
---
# <a name="vmq-receive-filters"></a>VMQ 接收筛选器





网络虚拟服务提供程序 (VSP) 设置 VMQ 接收 VMQ 的筛选器接收队列。 这样的筛选器包括一组网络标头字段测试。 网络适配器硬件上的传入数据包以确定数据包的接收队列分配中的标头字段中执行这些测试。 在队列设置每个筛选器具有唯一的筛选器标识符为网络适配器。 也就是说，筛选器标识符未在不同的队列，用于管理网络适配器上复制。

VMQ 接口使用筛选器测试中的媒体访问控制 (MAC) 标头中的字段。 在 MAC 标头，VMQ 筛选器测试使用虚拟局域网 (VLAN) 标识符和目标 MAC 地址字段。

接收筛选器中，可以指定多个字段测试。 所有测试必须通过的筛选器的条件匹配并将数据包分配给接收队列。 VMQ 筛选器测试指定的值相等的字段。 例如，目标 MAC 地址等于指定的地址。

可以在接收队列上设置多个筛选器。 如果任何队列匹配的筛选器 （即，该筛选器的测试的所有传递），网络适配器分配到的数据包接收队列。

此下图显示了如何执行测试筛选器和筛选器如何确定队列分配。

![说明如何执行测试筛选器和筛选器如何确定队列分配的关系图](images/vmqfilter.png)

在上图中，测试目标地址 (DA) (相比 A 和 B)。 此外，VLAN 标识符，则测试 （相对于 2 和 3）。 与运算说明了 DA 和 VLAN 标识符必须等于指定的值可使筛选器匹配。 或运算说明了与网络数据包到该队列的分配中的结果相匹配的队列上的任何筛选。

此下图显示了筛选器和队列会接收数据流的影响。

![说明如何筛选器和队列影响接收数据流关系图](images/vmqfilterpaths.png)

如果传入数据包与队列中的筛选器相匹配，则将它分配到该队列。 否则，数据包是针对测试的下一个队列上的筛选器，等等。 如果不存在任何队列上的筛选器匹配，网络适配器会将数据包分配给默认队列。

 

 




