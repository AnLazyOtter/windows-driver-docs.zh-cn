---
title: Bug 检查 0x195 SMB_SERVER_LIVEDUMP
description: SMB_SERVER_LIVEDUMP bug 检查具有 0x00000195 值。 这表示在 SMB 服务器检测到问题，已捕获核心转储收集调试信息。
ms.assetid: 302BA6E0-DC7C-4AE7-BD4D-C6F6A74D82D9
keywords:
- Bug 检查 0x195 SMB_SERVER_LIVEDUMP
- SMB_SERVER_LIVEDUMP
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- SMB_SERVER_LIVEDUMP
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: a68ecca5dc04da13be043a8cd99a8920ae498080
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519810"
---
# <a name="bug-check-0x195-smbserverlivedump"></a>Bug 检查 0x195：SMB\_SERVER\_LIVEDUMP


SMB\_SERVER\_LIVEDUMP bug 检查的值为 0x00000195。 这表示在 SMB 服务器检测到问题，已捕获核心转储收集调试信息。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="smbserverlivedump-parameters"></a>SMB\_SERVER\_LIVEDUMP 参数


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
<td align="left"><p>0x1:无法在合理的时间内完成 I/O。</p>
2-指针到 I / O 的 SRV2_WORK_ITEM</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">请参阅参数 1</td>
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

 

 

 




