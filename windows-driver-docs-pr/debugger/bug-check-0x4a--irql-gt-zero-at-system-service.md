---
title: Bug Check 0x4A IRQL_GT_ZERO_AT_SYSTEM_SERVICE
description: IRQL_GT_ZERO_AT_SYSTEM_SERVICE bug 检查具有 0x0000004A 值。 这表示的线程将返回给用户模式下从系统调用时其 IRQL 仍高于 passive_level 调用。
ms.assetid: 0da64630-d446-426a-a51f-34117fe9daa7
keywords:
- Bug Check 0x4A IRQL_GT_ZERO_AT_SYSTEM_SERVICE
- IRQL_GT_ZERO_AT_SYSTEM_SERVICE
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- IRQL_GT_ZERO_AT_SYSTEM_SERVICE
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 141c75154110429660bc5f1a2a24c6ddd0785bb7
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519414"
---
# <a name="bug-check-0x4a-irqlgtzeroatsystemservice"></a>Bug 检查 0x4A：IRQL\_GT\_ZERO\_AT\_SYSTEM\_SERVICE


IRQL\_GT\_零\_处\_系统\_服务错误检查的值为 0x0000004A。 这表示的线程将返回给用户模式下从系统调用时其 IRQL 仍高于被动\_级别。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="irqlgtzeroatsystemservice-parameters"></a>IRQL\_GT\_零\_处\_系统\_服务参数


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
<td align="left"><p>1</p></td>
<td align="left"><p>系统函数 （系统调用例程） 的地址</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p>当前 IRQL</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>0</p></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>0</p></td>
</tr>
</tbody>
</table>


## <a name="resolution"></a>分辨率 
[ **！ 分析**](https://docs.microsoft.com/windows-hardware/drivers/debugger/-analyze)调试扩展显示有关错误检查的信息，有助于在确定根本原因。
 

 




