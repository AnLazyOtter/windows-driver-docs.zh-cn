---
title: DEVPKEY_Device_RemovalPolicyDefault
description: DEVPKEY_Device_RemovalPolicyDefault
ms.assetid: e51fb2d2-5bc7-440c-8fc8-9e3f461350ea
keywords:
- DEVPKEY_Device_RemovalPolicyDefault 设备和驱动程序安装
topic_type:
- apiref
api_name:
- DEVPKEY_Device_RemovalPolicyDefault
api_location:
- Devpkey.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 7de23a746a7849c07bfd69386628f5cd4e8a6d87
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56562029"
---
# <a name="devpkeydeviceremovalpolicydefault"></a>DEVPKEY_Device_RemovalPolicyDefault


DEVPKEY_Device_RemovalPolicyDefault 设备属性表示设备实例的默认删除的策略。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>属性键</strong></p></td>
<td align="left"><p>DEVPKEY_Device_RemovalPolicyDefault</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>属性数据类型标识符</strong></p></td>
<td align="left"><p><a href="devprop-type-int32.md" data-raw-source="[&lt;strong&gt;DEVPROP_TYPE_INT32&lt;/strong&gt;](devprop-type-int32.md)"><strong>DEVPROP_TYPE_INT32</strong></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>属性访问</strong></p></td>
<td align="left"><p>通过安装应用程序和安装程序的只读访问权限</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>相应 SPDRP_</strong><em>Xxx</em> <strong>标识符</strong></p></td>
<td align="left"><p>SPDRP_REMOVAL_POLICY_HW_DEFAULT</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>本地化？</strong></p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

Windows 将 DEVPKEY_Device_RemovalPolicyDefault 的值设置为一 CM_REMOVAL_POLICY_*Xxx* Cfgmgr32.h 中定义的值。

您可以调用[ **SetupDiGetDeviceProperty** ](https://msdn.microsoft.com/library/windows/hardware/ff551963)检索 DEVPKEY_Device_RemovalPolicyDefault 值。

Windows Server 2003 和 Windows XP 支持此属性，但不是支持 DEVPKEY_Device_RemovalPolicyDefault 属性键。 相反，相应的 SPDRP_REMOVAL_POLICY_HW_DEFAULT 标识符可用于访问这些早期版本的 Windows 上的属性的值。 有关如何访问这些早期版本的 Windows 上此属性的值的信息，请参阅[访问设备实例 SPDRP_Xxx 属性](https://msdn.microsoft.com/library/windows/hardware/ff537737)。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>版本</p></td>
<td align="left"><p>在 Windows Vista 和更高版本的 Windows 中可用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Header</p></td>
<td align="left">Devpkey.h （包括 Devpkey.h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**SetupDiGetDeviceProperty**](https://msdn.microsoft.com/library/windows/hardware/ff551963)

 

 





