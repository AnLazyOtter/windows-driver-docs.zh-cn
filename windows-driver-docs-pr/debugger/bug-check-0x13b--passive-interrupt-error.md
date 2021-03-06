---
title: Bug 检查 0x13B PASSIVE_INTERRUPT_ERROR
description: PASSIVE_INTERRUPT_ERROR bug 检查具有 0x0000013B 值。 这表示内核已检测到被动级别中断问题。
ms.assetid: 6C921FCB-B945-4909-BAD3-1DBD6E3CAA54
keywords:
- Bug 检查 0x13B PASSIVE_INTERRUPT_ERROR
- PASSIVE_INTERRUPT_ERROR
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- PASSIVE_INTERRUPT_ERROR
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 3795a076eb9ad0864ac80d86a7693778a4455e3c
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67520225"
---
# <a name="bug-check-0x13b-passiveinterrupterror"></a>Bug 检查 0x13B：被动\_中断\_错误


被动\_中断\_错误 bug 检查的值为 0x0000013B。 这表示内核已检测到被动级别中断问题。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="passiveinterrupterror-parameters"></a>被动\_中断\_错误参数


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">参数</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left"><p>检测到错误的类型</p>
0x1:驱动程序尝试获取中断旋转锁，但在被动级别中断对象中传递。</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">被动级别中断 KINTERRUPT 对象的地址。</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left">保留</td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left">保留</td>
</tr>
</tbody>
</table>

 

 

 




