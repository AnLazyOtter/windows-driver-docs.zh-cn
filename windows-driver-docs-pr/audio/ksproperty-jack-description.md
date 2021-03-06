---
title: KSPROPERTY\_插孔\_说明
description: KSPROPERTY\_插孔\_DESCRIPTION 属性实现为通过筛选器句柄访问的多项、按位固定的属性。
ms.assetid: 005c7edc-8eb2-4387-b818-edef9b9dd4ee
keywords:
- KSPROPERTY_JACK_DESCRIPTION 音频设备
topic_type:
- apiref
api_name:
- KSPROPERTY_JACK_DESCRIPTION
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: b3504ca472b418a5887be965bcd26bf909458e59
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72830705"
---
# <a name="ksproperty_jack_description"></a>KSPROPERTY\_插孔\_说明


KSPROPERTY\_插孔\_DESCRIPTION 属性实现为通过筛选器句柄访问的多项、按位固定的属性。

在 Windows Vista 和更高版本中，此属性可在与一个或多个物理插孔关联的任何桥插针上受到支持。 它用于获取特定插孔的物理特性和使用情况的说明。

### <a name="span-idusage_summary_tablespanspan-idusage_summary_tablespanspan-idusage_summary_tablespanusage-summary-table"></a><span id="Usage_Summary_Table"></span><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span>使用情况摘要表

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
<th align="left">“获取”</th>
<th align="left">设置</th>
<th align="left">目标</th>
<th align="left">属性描述符类型</th>
<th align="left">属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>“是”</p></td>
<td align="left"><p>无</p></td>
<td align="left"><p>固定工厂（通过筛选器句柄）</p></td>
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksp_pin" data-raw-source="[&lt;strong&gt;KSP_PIN&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksp_pin)"><strong>KSP_PIN</strong></a></p></td>
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksmultiple_item" data-raw-source="[&lt;strong&gt;KSMULTIPLE_ITEM&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksmultiple_item)"><strong>KSMULTIPLE_ITEM</strong></a>后跟<a href="ksjack-description.md" data-raw-source="[&lt;strong&gt;KSJACK_DESCRIPTION&lt;/strong&gt;](ksjack-description.md)"><strong>KSJACK_DESCRIPTION</strong></a>结构的数组</p></td>
</tr>
</tbody>
</table>

 

属性值（实例数据）是 KSMULTIPLE\_项，后跟 KSJACK\_说明结构的数组。

### <a name="span-idreturn_valuespanspan-idreturn_valuespanspan-idreturn_valuespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值

KSPROPERTY\_插孔\_DESCRIPTION 属性请求返回一个 KSMULTIPLE\_项，后跟一个包含*N* KSJACK\_说明结构的数组，其中*n* = 与指定桥接器关联的插孔的数目。 因此，属性请求返回的成员将为：

KSMULTIPLE\_项。Size = sizeof （KSMULTIPLE\_ITEM） + N \* sizeof （KSJACK\_说明）

KSMULTIPLE\_项。计数 = N

KSJACK\_说明\[0\]

...

KSJACK\_说明\[N-1\]

<a name="remarks"></a>备注
-------

每个 KSJACK\_说明结构都必须包含有关一个插座的信息。 例如，支持三个立体声插孔的5.1 音频的输出桥插针需要大小为的数据缓冲区

sizeof （KSMULTIPLE\_ITEM） + 3 \* sizeof （KSJACK\_说明）

每个 KSJACK\_说明结构都有一个2位 ChannelMapping 值。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>最低受支持的客户端</p></td>
<td align="left"><p>Windows Vista</p></td>
</tr>
<tr class="even">
<td align="left"><p>最低受支持的服务器</p></td>
<td align="left"><p>Windows Server 2003</p></td>
</tr>
<tr class="odd">
<td align="left"><p>标头</p></td>
<td align="left">Ksmedia.h</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[**KSJACK\_说明**](ksjack-description.md)

[KSMULTIPLE\_项](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksmultiple_item)

[KSPROPERTY](https://docs.microsoft.com/previous-versions/ff564262(v=vs.85))

 

 






