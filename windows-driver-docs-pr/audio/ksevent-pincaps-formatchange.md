---
title: KSEVENT\_PINCAPS\_格式
description: KSEVENT\_PINCAPS\_格式事件指示音频堆栈为音频设备的音频数据格式已更改。
ms.assetid: ca9ee246-7fca-42df-89e0-7ace6b1f808a
keywords:
- KSEVENT_PINCAPS_FORMATCHANGE 音频设备
topic_type:
- apiref
api_name:
- KSEVENT_PINCAPS_FORMATCHANGE
api_location:
- Ks.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 702aff43ce9fd6b4da8eb939501d9299a85d0028
ms.sourcegitcommit: 6dff49ca5880466c396be5b889c44481dfed44ec
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "67161375"
---
# <a name="kseventpincapsformatchange"></a>KSEVENT\_PINCAPS\_格式


`KSEVENT_PINCAPS_FORMATCHANGE`事件指示音频堆栈为音频设备的音频数据格式已更改。

### <a name="span-idusagesummarytablespanspan-idusagesummarytablespan-usage-summary-table"></a><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span> 使用率摘要表

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">目标</th>
<th align="left">事件描述符类型</th>
<th align="left">事件值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Pin</p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/hardware/ff561744" data-raw-source="[&lt;strong&gt;KSEVENT&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff561744)"><strong>KSEVENT</strong></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/hardware/ff561750" data-raw-source="[&lt;strong&gt;KSEVENTDATA&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff561750)"><strong>KSEVENTDATA</strong></a></p></td>
</tr>
</tbody>
</table>

 

事件值类型 （操作数据） 是**KSEVENTDATA**结构，它指定要使用此事件的通知方法。

<a name="remarks"></a>备注
-------

当音频端口驱动程序调用[ **EventHandler** ](https://msdn.microsoft.com/library/windows/hardware/ff536374)例程对于其微型端口驱动程序，它将传递[ **PCEVENT\_请求**](https://msdn.microsoft.com/library/windows/hardware/ff537693)结构。 此结构包含一个指向[ **PCEVENT\_项**](https://msdn.microsoft.com/library/windows/hardware/ff537692)结构，用于描述支持的筛选器、 pin 或节点的事件。

因此，例如，驱动程序的支持`KSEVENT_PINCAPS_FORMATCHANGE`事件必须填充**PCEVENT\_项**结构，如下所示：

```cpp
static PCEVENT_ITEM FormatChangePinEvent[] = {
  {
    &KSEVENTSETID_PinCapsChange,
    KSEVENT_PINCAPS_FORMATCHANGE,
    KSEVENT_TYPE_ENABLE | KSEVENT_TYPE_BASICSUPPORT,
    MyEventHandler
  }
};
```

在前面的代码示例中，MyEventHandler 的自定义事件处理程序必须监视`KSEVENT_PINCAPS_FORMATCHANGE`事件并将其注册到 Portcls 时 KSEVENT\_PINCAPS\_触发格式。 微型端口驱动程序必须调用[ **IPortEvents::AddEventToEventList** ](https://msdn.microsoft.com/library/windows/hardware/ff536886)方法来注册该事件。

若要获取 pin、 节点、 连接和支持的微型端口驱动程序属性的说明，端口驱动程序调用[ **IMiniport::GetDescription** ](https://msdn.microsoft.com/library/windows/hardware/ff536765)方法。 此方法调用返回[ **PCFILTER\_描述符**](https://msdn.microsoft.com/library/windows/hardware/ff537694)指向自动化表的结构 ([**PCAUTOMATION\_表**](https://msdn.microsoft.com/library/windows/hardware/ff537685)). **PCAUTOMATION\_表**结构具有**事件**成员。 此成员将指向与微型端口驱动程序支持的筛选器相关联的事件的数组。 因此，你必须设置**事件**成员以指向包含事件数组**PCEVENT\_项**结构`KSEVENT_PINCAPS_FORMATCHANGE`事件。

当微型端口驱动程序检测到动态格式更改时，它必须调用[ **IPortEvents::GenerateEventList** ](https://msdn.microsoft.com/library/windows/hardware/ff536889)方法用信号通知`KSEVENT_PINCAPS_FORMATCHANGE`事件。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Version</p></td>
<td align="left"><p>在 Windows 7 和更高版本的 Windows 操作系统中可用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Header</p></td>
<td align="left">Ks.h （包括 Ks.h）</td>
</tr>
</tbody>
</table>

## <a name="span-idseealsospansee-also"></a><span id="see_also"></span>另请参阅


[**EventHandler**](https://msdn.microsoft.com/library/windows/hardware/ff536374)

[**IMiniport::GetDescription**](https://msdn.microsoft.com/library/windows/hardware/ff536765)

[**IPortEvents::AddEventToEventList**](https://msdn.microsoft.com/library/windows/hardware/ff536886)

[**IPortEvents::GenerateEventList**](https://msdn.microsoft.com/library/windows/hardware/ff536889)

[**KSEVENT**](https://msdn.microsoft.com/library/windows/hardware/ff561744)

[**KSEVENTDATA**](https://msdn.microsoft.com/library/windows/hardware/ff561750)

[**PCAUTOMATION\_表**](https://msdn.microsoft.com/library/windows/hardware/ff537685)

[**PCEVENT\_项**](https://msdn.microsoft.com/library/windows/hardware/ff537692)

[**PCEVENT\_REQUEST**](https://msdn.microsoft.com/library/windows/hardware/ff537693)

[**PCFILTER\_DESCRIPTOR**](https://msdn.microsoft.com/library/windows/hardware/ff537694)

 

 





