---
title: Bug 检查 0x144 BUGCODE_USB3_DRIVER
description: BUGCODE_USB3_DRIVER bug 检查的值为0x00000144。 这是用于所有 USB 3 bug 检查的代码。
ms.assetid: 39414287-3E20-405B-846A-B7F9F8AEE078
keywords:
- Bug 检查 0x144 BUGCODE_USB3_DRIVER
- BUGCODE_USB3_DRIVER
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- BUGCODE_USB3_DRIVER
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 74c25bd7361e531d0fdf0fa1316267cbe733edf5
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72837636"
---
# <a name="bug-check-0x144-bugcode_usb3_driver"></a>Bug 检查0x144： BUGCODE\_USB3\_驱动程序


**BUGCODE\_USB3\_驱动程序**bug 检查的值为0x00000144。 这是用于所有 USB 3 bug 检查的代码。 参数1指定 USB 3 bug 检查的类型，其他参数的含义依赖于参数1。

> [!IMPORTANT]
> 本主题面向程序员。 如果你是在使用计算机时收到蓝屏错误代码的客户，请参阅[排查蓝屏错误](https://www.windows.com/stopcode)。


## <a name="bugcode_usb3_driver-parameters"></a>BUGCODE\_USB3\_驱动程序参数


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
<th align="left">参数 1</th>
<th align="left">参数2</th>
<th align="left">参数3</th>
<th align="left">参数4</th>
<th align="left">错误的原因</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x1</p></td>
<td align="left"><p>可选。 指向用于重新发送 URB 的 IRP 的指针</p></td>
<td align="left"><p>指向 URB 的指针</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针</p></td>
<td align="left"><p>客户端驱动程序使用以前发送到核心堆栈的 URB。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x2</p></td>
<td align="left"><p>指向启动设备的物理设备对象（PDO）的指针</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>启动或寻呼设备重新枚举失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x3</p></td>
<td align="left"><p>可选。 指向用于发送 URB 的 IRP 的指针</p></td>
<td align="left"><p>指向损坏的 URB 的指针</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针</p></td>
<td align="left"><p>客户端驱动程序向核心堆栈发送了损坏的 URB。 出现这种情况的原因可能是客户端驱动程序未使用<strong>USBD_<em>xxx</em>UrbAllocate</strong>分配 URB，或者因为客户端驱动程序对 URB 执行了缓冲区不足。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x800</p></td>
<td align="left"><p>发送打开的静态流请求的 IRQL</p></td>
<td align="left"><p>指向打开的静态流 IRP 的指针</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针</p></td>
<td align="left"><p>在被动级别 &gt; 以 IRQL 发送打开的静态流请求。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x801</p></td>
<td align="left"><p>指向打开的静态流 IRP 的指针</p></td>
<td align="left"><p>指向打开的静态流的指针 URB</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针</p></td>
<td align="left"><p>在查询流功能之前，客户端驱动程序尝试打开静态流。 客户端驱动程序在成功查询流功能之前，无法打开静态流。 有关详细信息，请参阅 "备注"。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x802</p></td>
<td align="left"><p>客户端驱动程序尝试打开的静态流数</p></td>
<td align="left"><p>已授予客户端驱动程序的静态流数</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针</p></td>
<td align="left"><p>客户端驱动程序尝试打开的静态流数量无效。 流的数目不能为0，并且不能大于返回到 query USB 功能调用中的客户端驱动程序的值。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x803</p></td>
<td align="left"><p>指向打开的静态流 IRP 的指针</p></td>
<td align="left"><p>指向打开的静态流的指针 URB</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针</p></td>
<td align="left"><p>对于已经打开了静态流的终结点，客户端驱动程序尝试打开静态流。 在打开静态流之前，客户端驱动程序必须关闭先前打开的静态流。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x804</p></td>
<td align="left"><p>泄漏的句柄上下文。 运行<strong>！ usbanalyze-v</strong>以获取有关泄漏的句柄和 URBs 的信息。 您必须为客户端驱动程序启用驱动程序验证程序。</p></td>
<td align="left"><p>传递给<strong><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/usbdlib/nf-usbdlib-usbd_createhandle" data-raw-source="[USBD_CreateHandle](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbdlib/nf-usbdlib-usbd_createhandle)">USBD_CreateHandle</a></strong>的设备对象。</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>客户端驱动程序忘记关闭使用<strong><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/usbdlib/nf-usbdlib-usbd_createhandle" data-raw-source="[USBD_CreateHandle](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbdlib/nf-usbdlib-usbd_createhandle)">USBD_CreateHandle</a></strong>之前创建的句柄，或忘记释放已分配的 URB。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x805</p></td>
<td align="left"><p>Close 静态流的<a href="https://docs.microsoft.com/windows-hardware/drivers/wdf/framework-request-objects" data-raw-source="[WDFREQUEST](https://docs.microsoft.com/windows-hardware/drivers/wdf/framework-request-objects)">WDFREQUEST</a>句柄 URB</p></td>
<td align="left"><p>指向 Close 静态流的指针 URB</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针</p></td>
<td align="left"><p>客户端驱动程序发送了处于无效状态的关闭静态流 URB （例如，在处理 D0 Exit 后）。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x806</p></td>
<td align="left"><p>指向 IRP 的指针</p></td>
<td align="left"><p>指向 URB 的指针</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针</p></td>
<td align="left"><p>客户端驱动程序尝试在查询链式<strong>mdl</strong>功能之前发送链式<strong><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_mdl" data-raw-source="[MDL](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_mdl)">mdl</a></strong> 。 如果客户端驱动程序成功查询链式<strong>mdl</strong>功能，则客户端驱动程序无法发送链式<strong>mdl</strong> 。 有关详细信息，请参阅 "备注"。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x807</p></td>
<td align="left"><p>指向链接 <strong><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_mdl" data-raw-source="[MDL](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_mdl)">MDL</a>的指针</strong></p></td>
<td align="left"><p>指向 URB 的指针</p></td>
<td align="left"><p>指向客户端驱动程序的设备对象的指针（如果可用）</p></td>
<td align="left"><p>客户端驱动程序将 URB 发送到核心堆栈，其传输缓冲区长度超过传入的<strong><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_mdl" data-raw-source="[MDL](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_mdl)">MDL</a></strong>的字节数（由<strong><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-mmgetmdlbytecount" data-raw-source="[MmGetMdlByteCount](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-mmgetmdlbytecount)">MmGetMdlByteCount</a></strong>返回）。 有关详细信息，请参阅 "备注"。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1001</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>XHCI 控制器已断言 HSE 位，指示主机系统错误。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1002</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>XHCI 控制器已断言 HCE 位，这表示发生了主机控制器错误。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1003</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>XHCI stop endpoint 命令返回了一个未处理的完成代码。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1004</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>发出 xHCI 终结点停止命令后，xHCI 终结点状态收到上下文状态错误。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1005</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>在尝试清除控制终结点上的延迟时设置取消排队指针失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1006</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>尝试在控制终结点上清除延迟时重置 EP 失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1007</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>重置恢复期间，xHCI 控制器重置失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1008 相关联</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>重启 xHCI 控制器在重置恢复过程中失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1009</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>命令超时中止后，xHCI 控制器命令无法完成。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x100A</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>在终结点停止完成后尝试设置取消排队指针的过程中，设置取消排队指针失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x100B</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>重置恢复期间，xHCI 控制器停止失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x100C</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>不支持 xHCI 控制器中的固件。 除非更新固件，否则不会在此控制器上加载 xHCI 驱动程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x100D</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>检测到控制器已被物理删除。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x100E</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>驱动程序在启用流的终结点上检测到错误。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x100F</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>XHCI 控制器中的固件已过时。 XHCI 驱动程序将继续使用此控制器，但可能会遇到一些问题。 建议更新固件。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1010</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>传输事件 TRB 已完成，但未处理完成代码。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1011</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器报告事件环已满。 此事件发生时，控制器也被称为删除事件。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1012</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器未按顺序完成命令。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1013</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>命令中止完成后，控制器报告的命令环取消排队指针不正确。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1014</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>启用槽完成后，控制器为我们提供了错误的插槽 id。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1015</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器未能使用 BSR1 的 SetAddress 命令。 这不是预期的。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1016</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器在 usbdevice 重置过程中无法启用槽。 这是意外情况。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1017</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器无法通过终结点配置命令来 deconfiguring 终结点。 这不是预期的。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1018</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器无法禁用槽命令。 这不是预期的。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1019</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器未通过 USB 设备重置命令。 这不是预期的。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x101A</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>终结点重置后，设置取消排队指针命令失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x101B</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>XHCI reset endpoint 命令返回了一个未处理的完成代码。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x101C</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>XHCI 的 D0Entry 失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x101D</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>在请求取消期间使用 "配置终结点" 命令而不是 "设置取消排队" 指针时，临时删除并添加流终结点（作为两个命令）失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x101E</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器指示控制器未等待传输完成。 EventData = = 1 （取消引用传输事件 TRB 的指针是否会导致错误检查）</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x101F</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器指示控制器未等待传输完成。 EventData = = 0 （传输事件 TRB 中的逻辑地址不匹配）</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1020</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>控制器指示控制器未等待传输完成。 EventData = = 0 （传输事件 TRB 中的逻辑地址不匹配）传输事件 TRB 可能是冗余的（指向最近完成的请求附近的某个地方）。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x1021</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>使用 "配置终结点" 命令作为重置未暂停终结点的一部分时，临时删除并添加流终结点（作为两个命令）失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x1022</p></td>
<td align="left"><p>XHCI_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>删除并添加同一终结点（作为一个命令）失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x3000</p></td>
<td align="left"><p>USBHUB3_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>集线器驱动程序已成功重置了行为不足的中心。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x3001</p></td>
<td align="left"><p>USBHUB3_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>集线器驱动程序无法成功重置有行为的中心。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x3002</p></td>
<td align="left"><p>USBHUB3_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>集线器驱动程序禁用了非函数 SuperSpeed 中心。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x3003</p></td>
<td align="left"><p>USBHUB3_LIVEDUMP_CONTEXT</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>USB 设备枚举失败。</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

若要查询 USB 功能，客户端驱动程序必须调用[**WdfUsbTargetDeviceQueryUsbCapability**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetdevicequeryusbcapability)或[**USBD\_QueryUsbCapability**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/hh406230(v=vs.85))

若要发送链式[**MDL**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_mdl)，客户端驱动程序必须调用[**USBD\_QueryUsbCapability**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/hh406230(v=vs.85)) ，并使用**URB\_函数\_大容量\_或\_中断\_使用\_链接\_MDL 传输\_** 或**URB\_函数\_ISOCH\_传输\_使用\_链接\_MDL**。

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[通用串行总线 (USB)](https://docs.microsoft.com/windows-hardware/drivers/)

 

 




