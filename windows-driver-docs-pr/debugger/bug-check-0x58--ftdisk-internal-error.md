---
title: Bug Check 0x58 FTDISK_INTERNAL_ERROR
description: FTDISK_INTERNAL_ERROR bug 检查具有 0x00000058 值。 在系统启动从镜像分区的副本中错误时发出此操作。
ms.assetid: c8de6a04-740d-415e-bf23-b28da066a225
keywords:
- Bug Check 0x58 FTDISK_INTERNAL_ERROR
- FTDISK_INTERNAL_ERROR
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- FTDISK_INTERNAL_ERROR
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 72d593051e396998d7c71bf73e5f9a0391dfdc39
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519354"
---
# <a name="bug-check-0x58-ftdiskinternalerror"></a>Bug 检查 0x58：FTDISK\_INTERNAL\_ERROR


FTDISK\_内部\_错误 bug 检查的值为 0x00000058。 在系统启动从镜像分区的副本中错误时发出此操作。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="ftdiskinternalerror-parameters"></a>FTDISK\_内部\_错误参数


无

<a name="cause"></a>原因
-----

镜像有效，但它不是，要指出配置单元。 配置单元实际上应指向的卷影分区。

这几乎总是引起正在恢复的主分区。

<a name="resolution"></a>分辨率
----------

重新启动系统的卷影分区。

 

 




