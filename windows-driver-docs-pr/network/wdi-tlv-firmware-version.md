---
title: WDI_TLV_FIRMWARE_VERSION
description: WDI_TLV_FIRMWARE_VERSION 是 TLV 包含固件版本。
ms.assetid: 31E61ACA-AF2F-4E5D-9448-363630A27E39
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 WDI_TLV_FIRMWARE_VERSION 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: a9d6bfbf23252c6c73afa8a9f93c4dfef7d068ba
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63329631"
---
# <a name="wditlvfirmwareversion"></a>WDI\_TLV\_FIRMWARE\_VERSION


WDI\_TLV\_固件\_版本是包含固件版本 TLV。

## <a name="tlv-type"></a>TLV 类型


0xF4

## <a name="length"></a>长度


Char 元素的数组大小 （以字节为单位）。 该数组必须包含一个或多个元素。

## <a name="values"></a>值


| 在任务栏的搜索框中键入     | 描述                                                     |
|----------|-----------------------------------------------------------------|
| char\[\] | 作为以 null 结尾的 ASCII 字符串存储的固件版本。 |

 

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低受支持的客户端</p></td>
<td><p>Windows 10</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2016</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wditypes.hpp</td>
</tr>
</tbody>
</table>

 

 




