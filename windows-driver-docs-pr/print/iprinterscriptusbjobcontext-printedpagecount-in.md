---
title: IPrinterScriptUsbJobContext PrintedPageCount 方法
description: 设置由当前的作业中的打印设备打印的页数。
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3C1DAE22-F1DF-48AE-A6F6-CCB8A97EB424
keywords:
- PrintedPageCount 方法打印设备
- PrintedPageCount 方法打印设备，IPrinterScriptUsbJobContext 接口
- IPrinterScriptUsbJobContext 接口打印设备，PrintedPageCount 方法
topic_type:
- apiref
api_name:
- IPrinterScriptUsbJobContext.PrintedPageCount
api_type:
- COM
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3d57fc1464cc39e4137bcd5665df41b903476ec6
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63349242"
---
# <a name="iprinterscriptusbjobcontextprintedpagecount-method"></a>IPrinterScriptUsbJobContext::PrintedPageCount method

设置由当前的作业中的打印设备打印的页数。

<a name="syntax"></a>语法
------

```cpp
HRESULT PrintedPageCount(
  [in] UINT32 value
);
```

<a name="parameters"></a>Parameters
----------

*value* \[in\]  
由当前的作业中的打印设备打印的页数。

<a name="return-value"></a>返回值
------------

此方法返回**HRESULT**值。

<a name="remarks"></a>备注
-------

**PrintedPageCount**是读/写方法。 IHV JavaScript **writeData**函数应保留打印的页计数保持最新状态，以允许 USBMon 来对作业设置正确的进度。

如果 IHV JavaScript 代码永远不会调用**PrintedPageCount**若要设置打印的页计数，假定是不可能准确的页计数和 USBMon 将允许后台处理程序以继续估计进度。

璝惠 USBMon 和基于 USB 的双向通信与打印设备，请参阅[USB Bidi 扩展器](https://docs.microsoft.com/windows-hardware/drivers/print/usb-bidi-extender)。

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
<td><p>Windows 8.1</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2012 R2</p></td>
</tr>
<tr class="odd">
<td><p>目标平台</p></td>
<td>桌面设备</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅

[**IPrinterScriptUsbJobContext**](iprinterscriptusbjobcontext.md)

[USB Bidi 扩展程序](https://docs.microsoft.com/windows-hardware/drivers/print/usb-bidi-extender)
