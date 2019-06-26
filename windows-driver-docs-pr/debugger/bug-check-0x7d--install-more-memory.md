---
title: Bug 检查 0x7D INSTALL_MORE_MEMORY
description: INSTALL_MORE_MEMORY bug 检查具有 0x0000007D 值。 此 bug 对勾指示是不足够的内存来启动 Microsoft Windows 操作系统。
ms.assetid: 560cfa2b-f000-4dc9-8505-f539f3f56fd6
keywords:
- Bug 检查 0x7D INSTALL_MORE_MEMORY
- INSTALL_MORE_MEMORY
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- INSTALL_MORE_MEMORY
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: ac142192bcb73fc4cb39f01e1cc9d31fe5fdfb7e
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63367323"
---
# <a name="bug-check-0x7d-installmorememory"></a>Bug 检查 0x7D：安装\_详细\_内存


在安装\_详细\_内存错误检查的值为 0x0000007D。 此 bug 对勾指示是不足够的内存来启动 Microsoft Windows 操作系统。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://windows.microsoft.com/windows-10/troubleshoot-blue-screen-errors)。


## <a name="installmorememory-parameters"></a>安装\_详细\_内存参数


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
<td align="left"><p>找到的物理页面数</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p>最低的物理页</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>最高的物理页</p></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>0</p></td>
</tr>
</tbody>
</table>

 

<a name="cause"></a>原因
-----

Windows 操作系统不具有足够的内存来完成启动过程。

<a name="resolution"></a>分辨率
----------

安装更多内存。

 

 



