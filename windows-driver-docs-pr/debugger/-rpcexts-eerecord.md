---
title: rpcexts.eerecord
description: Rpcexts.eerecord 扩展显示扩展的错误的信息记录的内容。
ms.assetid: 3c861842-d3ac-4c7d-88e3-d00233189b74
keywords:
- rpcexts.eerecord Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- rpcexts.eerecord
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 10d9e9034609d1eb91f39b85422365ba9c9e6046
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63335734"
---
# <a name="rpcextseerecord"></a>!rpcexts.eerecord


**！ Rpcexts.eerecord**扩展显示的扩展的错误的信息记录的内容。

```dbgcmd
!rpcexts.eerecord EERecordAddress
```

## <a name="span-idddkrpcextseerecorddbgspanspan-idddkrpcextseerecorddbgspanparameters"></a><span id="ddk__rpcexts_eerecord_dbg"></span><span id="DDK__RPCEXTS_EERECORD_DBG"></span>参数


<span id="_______EERecordAddress______"></span><span id="_______eerecordaddress______"></span><span id="_______EERECORDADDRESS______"></span> *EERecordAddress*   
指定扩展的错误记录的地址。

### <a name="span-iddllspanspan-iddllspandll"></a><span id="DLL"></span><span id="dll"></span>DLL

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Windows 2000</strong></p></td>
<td align="left"><p>不可用</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Windows XP 及更高版本</strong></p></td>
<td align="left"><p>Rpcexts.dll</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idadditionalinformationspanspan-idadditionalinformationspanspan-idadditionalinformationspanadditional-information"></a><span id="Additional_Information"></span><span id="additional_information"></span><span id="ADDITIONAL_INFORMATION"></span>其他信息

有关调试 Microsoft 远程过程调用 (RPC) 的详细信息，请参阅[RPC 调试](rpc-debugging.md)。

<a name="remarks"></a>备注
-------

此扩展插件在调试器中显示一个扩展的错误的信息记录的内容。 在大多数情况下，它是更轻松地使用[ **！ rpcexts.eeinfo**](-rpcexts-eeinfo.md)，后者将显示整个链。 如果链是很长，并且你想要看到只有一个记录，使用 **！ eerecord**相反。

下面是一个示例：

```dbgcmd
0:001> !rpcexts.eerecord 0xb015f0
Computer Name: (null)
ProcessID: 708 (0x2C4)
System Time is: 3/21/2000 4:3:0:264
Generating component: 8
Status: 14
Detection Location: 311
Flags:
Parameter 0:(Long value) : -30976 (0xFFFF8700)
Parameter 1:(Long value) : 16777343 (0x100007F)
```

 

 





