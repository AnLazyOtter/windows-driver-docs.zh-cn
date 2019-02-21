---
title: KSPROPERTY\_EXTXPORT\_ATN\_SEARCH
description: KSPROPERTY\_EXTXPORT\_ATN\_搜索属性搜索为特定的绝对轨道数 (ATN) 在磁带上。
ms.assetid: e5bc7552-64a8-4567-9dc3-3f2b50411cc6
keywords:
- KSPROPERTY_EXTXPORT_ATN_SEARCH 流式处理媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_EXTXPORT_ATN_SEARCH
api_location:
- ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 5c7e430e85cd17afc0315aa64092399418f5e333
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56519381"
---
# <a name="kspropertyextxportatnsearch"></a>KSPROPERTY\_EXTXPORT\_ATN\_SEARCH


KSPROPERTY\_EXTXPORT\_ATN\_搜索属性搜索为特定的绝对轨道数 (ATN) 在磁带上。

## <span id="ddk_ksproperty_extxport_atn_search_ks"></span><span id="DDK_KSPROPERTY_EXTXPORT_ATN_SEARCH_KS"></span>


### <a name="usage-summary-table"></a>使用率摘要表

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Get</th>
<th>设置</th>
<th>目标</th>
<th>属性描述符类型</th>
<th>属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>否</p></td>
<td><p>是</p></td>
<td><p>设备</p></td>
<td><p><a href="https://msdn.microsoft.com/library/windows/hardware/ff565167" data-raw-source="[&lt;strong&gt;KSPROPERTY_EXTXPORT_S&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff565167)"><strong>KSPROPERTY_EXTXPORT_S</strong></a></p></td>
<td><p>DWORD</p></td>
</tr>
</tbody>
</table>

 

（操作数据） 的属性值为 dword 值，可以指定绝对跟踪号。

<a name="remarks"></a>备注
-------

**DwAbsTrackNumber** KSPROPERTY 成员\_EXTXPORT\_S 结构指定要搜索到的绝对跟踪号。

此方法是定义，但不是受支持。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>标头</p></td>
<td>Ksmedia.h （包括 Ksmedia.h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**KSPROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ks/ns-ks-ksidentifier)

[**KSPROPERTY\_EXTXPORT\_S**](https://msdn.microsoft.com/library/windows/hardware/ff565167)

 

 





