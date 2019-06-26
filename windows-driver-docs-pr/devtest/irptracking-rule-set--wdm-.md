---
title: IrpTracking 规则集 (WDM)
description: 使用这些规则来验证您的驱动程序正确跟踪 I/O 请求数据包 (IRP)，这样，Irp 未完成而不删除该设备。
ms.assetid: 9AD62397-6840-42FF-ADEC-6836EDD16647
ms.date: 05/21/2018
ms.localizationpriority: medium
ms.openlocfilehash: 792994e2a6071a8a94626b67611bd45649113693
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63350515"
---
# <a name="irptracking-rule-set-wdm"></a>IrpTracking 规则集 (WDM)


使用这些规则来验证您的驱动程序正确跟踪 I/O 请求数据包 (IRP)，这样，Irp 未完成而不删除该设备。

## <a name="in-this-section"></a>本节内容


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">主题</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="wdm-ioreleaseremovelockandwaitoutsideremovedevice.md" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLockAndWaitOutsideRemoveDevice&lt;/strong&gt;](wdm-ioreleaseremovelockandwaitoutsideremovedevice.md)"><strong>IoReleaseRemoveLockAndWaitOutsideRemoveDevice</strong></a></p></td>
<td align="left"><p><a href="wdm-ioreleaseremovelockandwaitoutsideremovedevice.md" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLockAndWaitOutsideRemoveDevice&lt;/strong&gt;](wdm-ioreleaseremovelockandwaitoutsideremovedevice.md)"> <strong>IoReleaseRemoveLockAndWaitOutsideRemoveDevice</strong> </a>规则指定<a href="https://msdn.microsoft.com/library/windows/hardware/ff549567" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLockAndWait&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549567)"> <strong>IoReleaseRemoveLockAndWait</strong> </a>不应为在使用 IRP_MN_REMOVE_DEVICE IRP_MJ_PNP 外部调用即插即用驱动程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-nsremovelockmnremove.md" data-raw-source="[&lt;strong&gt;NsRemoveLockMnRemove&lt;/strong&gt;](wdm-nsremovelockmnremove.md)"><strong>NsRemoveLockMnRemove</strong></a></p></td>
<td align="left"><p><a href="wdm-nsremovelockmnremove.md" data-raw-source="[&lt;strong&gt;NsRemoveLockMnRemove&lt;/strong&gt;](wdm-nsremovelockmnremove.md)"> <strong>NsRemoveLockMnRemove</strong> </a>规则验证驱动程序不会返回 STATUS_NOT_SUPPORTED 处理与 MinorFunction IRP_MN_REMOVE_DEVICE IRP_MJ_PNP 时。 此规则仅适用于 FDO 和 FIDO 驱动程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-nsremovelockmnsurpriseremove.md" data-raw-source="[&lt;strong&gt;NsRemoveLockMnSurpriseRemove&lt;/strong&gt;](wdm-nsremovelockmnsurpriseremove.md)"><strong>NsRemoveLockMnSurpriseRemove</strong></a></p></td>
<td align="left"><p><a href="wdm-nsremovelockmnsurpriseremove.md" data-raw-source="[&lt;strong&gt;NsRemoveLockMnSurpriseRemove&lt;/strong&gt;](wdm-nsremovelockmnsurpriseremove.md)"> <strong>NsRemoveLockMnSurpriseRemove</strong> </a>规则验证驱动程序不会处理与 minorFunction IRP_MN_SUPRISE_REMOVAL IRP_MJ_PNP 请求时返回 STATUS_NOT_SUPPORTED。 此规则仅适用于 FDO 和 FIDO 驱动程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-nsremovelockquerymnremove.md" data-raw-source="[&lt;strong&gt;NsRemoveLockQueryMnRemove&lt;/strong&gt;](wdm-nsremovelockquerymnremove.md)"><strong>NsRemoveLockQueryMnRemove</strong></a></p></td>
<td align="left"><p><a href="wdm-nsremovelockquerymnremove.md" data-raw-source="[&lt;strong&gt;NsRemoveLockQueryMnRemove&lt;/strong&gt;](wdm-nsremovelockquerymnremove.md)"> <strong>NsRemoveLockQueryMnRemove</strong> </a>规则验证驱动程序不会返回 STATUS_NOT_SUPPORTED 处理与 MinorFunction IRP_MN_QUERY_REMOVE IRP_MJ_PNP 时。 此规则仅适用于 FDO 和 FIDO 驱动程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelock.md" data-raw-source="[&lt;strong&gt;RemoveLock&lt;/strong&gt;](wdm-removelock.md)"><strong>RemoveLock</strong></a></p></td>
<td align="left"><p><a href="wdm-removelock.md" data-raw-source="[&lt;strong&gt;RemoveLock&lt;/strong&gt;](wdm-removelock.md)"> <strong>RemoveLock</strong> </a>规则指定的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>正确使用。 此外，在 IRP_MJ_PNP 或 IRP_MJ_POWER 例程结束时，该驱动程序不应阻止<strong>RemoveLock</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockcheck.md" data-raw-source="[&lt;strong&gt;RemoveLockCheck&lt;/strong&gt;](wdm-removelockcheck.md)"><strong>RemoveLockCheck</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockcheck.md" data-raw-source="[&lt;strong&gt;RemoveLockCheck&lt;/strong&gt;](wdm-removelockcheck.md)"> <strong>RemoveLockCheck</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549567" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLockAndWait&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549567)"> <strong>IoReleaseRemoveLockAndWait</strong> </a>处理与 MinorFunction IRP_MN_REMOVE_DEVICE IRP_MJ_PNP 时正确使用。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockforward.md" data-raw-source="[&lt;strong&gt;RemoveLockForward&lt;/strong&gt;](wdm-removelockforward.md)"><strong>RemoveLockForward</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforward.md" data-raw-source="[&lt;strong&gt;RemoveLockForward&lt;/strong&gt;](wdm-removelockforward.md)"> <strong>RemoveLockForward</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>转发到另一个设备 IRP 时正确使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockforward2.md" data-raw-source="[&lt;strong&gt;RemoveLockForward2&lt;/strong&gt;](wdm-removelockforward2.md)"><strong>RemoveLockForward2</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforward2.md" data-raw-source="[&lt;strong&gt;RemoveLockForward2&lt;/strong&gt;](wdm-removelockforward2.md)"> <strong>RemoveLockForward2</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>转发到另一个设备 IRP 时正确使用。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockforwarddevicecontrol.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardDeviceControl&lt;/strong&gt;](wdm-removelockforwarddevicecontrol.md)"><strong>RemoveLockForwardDeviceControl</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforwarddevicecontrol.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardDeviceControl&lt;/strong&gt;](wdm-removelockforwarddevicecontrol.md)"> <strong>RemoveLockForwardDeviceControl</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>驱动程序使用时正确使用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548336" data-raw-source="[&lt;strong&gt;IoCallDriver&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548336)"> <strong>IoCallDriver</strong> </a>转发到另一个设备 IRP。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockforwarddevicecontrol2.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardDeviceControl2&lt;/strong&gt;](wdm-removelockforwarddevicecontrol2.md)"><strong>RemoveLockForwardDeviceControl2</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforwarddevicecontrol2.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardDeviceControl2&lt;/strong&gt;](wdm-removelockforwarddevicecontrol2.md)"> <strong>RemoveLockForwardDeviceControl2</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>驱动程序使用时正确使用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548336" data-raw-source="[&lt;strong&gt;IoCallDriver&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548336)"> <strong>IoCallDriver</strong> </a>转发到另一个设备 IRP。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockforwarddevicecontrolinternal.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardDeviceControlInternal&lt;/strong&gt;](wdm-removelockforwarddevicecontrolinternal.md)"><strong>RemoveLockForwardDeviceControlInternal</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforwarddevicecontrolinternal.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardDeviceControlInternal&lt;/strong&gt;](wdm-removelockforwarddevicecontrolinternal.md)"> <strong>RemoveLockForwardDeviceControlInternal</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"><strong>IoReleaseRemoveLock</strong> </a>中使用正确转发 IRP 使用时<a href="https://msdn.microsoft.com/library/windows/hardware/ff548336" data-raw-source="[&lt;strong&gt;IoCallDriver&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548336)"> <strong>IoCallDriver</strong> </a>到另一台设备。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockforwarddevicecontrolinternal2.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardDeviceControlInternal2&lt;/strong&gt;](wdm-removelockforwarddevicecontrolinternal2.md)"><strong>RemoveLockForwardDeviceControlInternal2</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforwarddevicecontrolinternal2.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardDeviceControlInternal2&lt;/strong&gt;](wdm-removelockforwarddevicecontrolinternal2.md)"> <strong>RemoveLockForwardDeviceControlInternal2</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"><strong>IoReleaseRemoveLock</strong> </a>中使用正确转发 IRP 使用时<a href="https://msdn.microsoft.com/library/windows/hardware/ff548336" data-raw-source="[&lt;strong&gt;IoCallDriver&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548336)"> <strong>IoCallDriver</strong> </a>到另一台设备。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockforwardread.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardRead&lt;/strong&gt;](wdm-removelockforwardread.md)"><strong>RemoveLockForwardRead</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforwardread.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardRead&lt;/strong&gt;](wdm-removelockforwardread.md)"> <strong>RemoveLockForwardRead</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>中正确使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockforwardread2.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardRead2&lt;/strong&gt;](wdm-removelockforwardread2.md)"><strong>RemoveLockForwardRead2</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforwardread2.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardRead2&lt;/strong&gt;](wdm-removelockforwardread2.md)"> <strong>RemoveLockForwardRead2</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a> IRP 使用转发时正确使用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548336" data-raw-source="[&lt;strong&gt;IoCallDriver&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548336)"> <strong>IoCallDriver</strong> </a>到另一台设备。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockforwardwrite.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardWrite&lt;/strong&gt;](wdm-removelockforwardwrite.md)"><strong>RemoveLockForwardWrite</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforwardwrite.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardWrite&lt;/strong&gt;](wdm-removelockforwardwrite.md)"> <strong>RemoveLockForwardWrite</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a> IRP 使用转发时正确使用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548336" data-raw-source="[&lt;strong&gt;IoCallDriver&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548336)"> <strong>IoCallDriver</strong> </a>到另一台设备。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockforwardwrite2.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardWrite2&lt;/strong&gt;](wdm-removelockforwardwrite2.md)"><strong>RemoveLockForwardWrite2</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockforwardwrite2.md" data-raw-source="[&lt;strong&gt;RemoveLockForwardWrite2&lt;/strong&gt;](wdm-removelockforwardwrite2.md)"> <strong>RemoveLockForwardWrite2</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>转发 IRP 使用时正确使用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548336" data-raw-source="[&lt;strong&gt;IoCallDriver&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548336)"> <strong>IoCallDriver</strong> </a>到另一台设备。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockmnremove.md" data-raw-source="[&lt;strong&gt;RemoveLockMnRemove&lt;/strong&gt;](wdm-removelockmnremove.md)"><strong>RemoveLockMnRemove</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockmnremove.md" data-raw-source="[&lt;strong&gt;RemoveLockMnRemove&lt;/strong&gt;](wdm-removelockmnremove.md)"> <strong>RemoveLockMnRemove</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549567" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLockAndWait&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549567)"> <strong>IoReleaseRemoveLockAndWait</strong> </a>处理与 MinorFunction IRP_MN_REMOVE_DEVICE IRP_MJ_PNP 时正确使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockmnremove2.md" data-raw-source="[&lt;strong&gt;RemoveLockMnRemove2&lt;/strong&gt;](wdm-removelockmnremove2.md)"><strong>RemoveLockMnRemove2</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockmnremove2.md" data-raw-source="[&lt;strong&gt;RemoveLockMnRemove2&lt;/strong&gt;](wdm-removelockmnremove2.md)"> <strong>RemoveLockMnRemove2</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549567" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLockAndWait&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549567)"> <strong>IoReleaseRemoveLockAndWait</strong> </a>处理 IRP 之前 IRP_MN_REMOVE_DEVICE 请求转发到低级驱动程序时正确使用。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockmnsurpriseremove.md" data-raw-source="[&lt;strong&gt;RemoveLockMnSurpriseRemove&lt;/strong&gt;](wdm-removelockmnsurpriseremove.md)"><strong>RemoveLockMnSurpriseRemove</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockmnsurpriseremove.md" data-raw-source="[&lt;strong&gt;RemoveLockMnSurpriseRemove&lt;/strong&gt;](wdm-removelockmnsurpriseremove.md)"> <strong>RemoveLockMnSurpriseRemove</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549567" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLockAndWait&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549567)"> <strong>IoReleaseRemoveLockAndWait</strong> </a>处理与 MinorFunction IRP_MN_SUPRISE_REMOVAL IRP_MJ_PNP 时正确使用。 该驱动程序应转发堆栈的下层 IRP 之前获取的删除锁定。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockquerymnremove.md" data-raw-source="[&lt;strong&gt;RemoveLockQueryMnRemove&lt;/strong&gt;](wdm-removelockquerymnremove.md)"><strong>RemoveLockQueryMnRemove</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockquerymnremove.md" data-raw-source="[&lt;strong&gt;RemoveLockQueryMnRemove&lt;/strong&gt;](wdm-removelockquerymnremove.md)"> <strong>RemoveLockQueryMnRemove</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>处理与 MinorFunction IRP_MN_QUERY_REMOVE_DEVICE IRP_MJ_PNP 时正确使用。 该驱动程序应转发堆栈的下层 IRP 之前获取的删除锁定。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockrelease2.md" data-raw-source="[&lt;strong&gt;RemoveLockRelease2&lt;/strong&gt;](wdm-removelockrelease2.md)"><strong>RemoveLockRelease2</strong></a></p></td>
<td align="left"><p>该规则<a href="wdm-removelockrelease2.md" data-raw-source="[&lt;strong&gt;RemoveLockRelease2&lt;/strong&gt;](wdm-removelockrelease2.md)"> <strong>RemoveLockRelease2</strong> </a>验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockreleasecleanup.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseCleanup&lt;/strong&gt;](wdm-removelockreleasecleanup.md)"><strong>RemoveLockReleaseCleanup</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleasecleanup.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseCleanup&lt;/strong&gt;](wdm-removelockreleasecleanup.md)"> <strong>RemoveLockReleaseCleanup</strong> </a>规则指定的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 每次调用<strong>IoAcquireRemoveLock</strong>必须具有匹配调用<strong>IoReleaseRemoveLock</strong>。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockreleaseclose.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseClose&lt;/strong&gt;](wdm-removelockreleaseclose.md)"><strong>RemoveLockReleaseClose</strong></a></p></td>
<td align="left"><p>该规则<a href="wdm-removelockreleaseclose.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseClose&lt;/strong&gt;](wdm-removelockreleaseclose.md)"> <strong>RemoveLockReleaseClose</strong> </a>验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockreleasecreate.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseCreate&lt;/strong&gt;](wdm-removelockreleasecreate.md)"><strong>RemoveLockReleaseCreate</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleasecreate.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseCreate&lt;/strong&gt;](wdm-removelockreleasecreate.md)"> <strong>RemoveLockReleaseCreate</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockreleasedevicecontrol.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseDeviceControl&lt;/strong&gt;](wdm-removelockreleasedevicecontrol.md)"><strong>RemoveLockReleaseDeviceControl</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleasedevicecontrol.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseDeviceControl&lt;/strong&gt;](wdm-removelockreleasedevicecontrol.md)"> <strong>RemoveLockReleaseDeviceControl</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockreleaseinternaldevicecontrol.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseInternalDeviceControl&lt;/strong&gt;](wdm-removelockreleaseinternaldevicecontrol.md)"><strong>RemoveLockReleaseInternalDeviceControl</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleaseinternaldevicecontrol.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseInternalDeviceControl&lt;/strong&gt;](wdm-removelockreleaseinternaldevicecontrol.md)"> <strong>RemoveLockReleaseInternalDeviceControl</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"><strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockreleasepnp.md" data-raw-source="[&lt;strong&gt;RemoveLockReleasePnp&lt;/strong&gt;](wdm-removelockreleasepnp.md)"><strong>RemoveLockReleasePnp</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleasepnp.md" data-raw-source="[&lt;strong&gt;RemoveLockReleasePnp&lt;/strong&gt;](wdm-removelockreleasepnp.md)"> <strong>RemoveLockReleasePnp</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockreleasepower.md" data-raw-source="[&lt;strong&gt;RemoveLockReleasePower&lt;/strong&gt;](wdm-removelockreleasepower.md)"><strong>RemoveLockReleasePower</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleasepower.md" data-raw-source="[&lt;strong&gt;RemoveLockReleasePower&lt;/strong&gt;](wdm-removelockreleasepower.md)"> <strong>RemoveLockReleasePower</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockreleaseread.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseRead&lt;/strong&gt;](wdm-removelockreleaseread.md)"><strong>RemoveLockReleaseRead</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleaseread.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseRead&lt;/strong&gt;](wdm-removelockreleaseread.md)"> <strong>RemoveLockReleaseRead</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockreleaseshutdown.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseShutdown&lt;/strong&gt;](wdm-removelockreleaseshutdown.md)"><strong>RemoveLockReleaseShutdown</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleaseshutdown.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseShutdown&lt;/strong&gt;](wdm-removelockreleaseshutdown.md)"> <strong>RemoveLockReleaseShutdown</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="wdm-removelockreleasesystemcontrol.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseSystemControl&lt;/strong&gt;](wdm-removelockreleasesystemcontrol.md)"><strong>RemoveLockReleaseSystemControl</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleasesystemcontrol.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseSystemControl&lt;/strong&gt;](wdm-removelockreleasesystemcontrol.md)"> <strong>RemoveLockReleaseSystemControl</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>和<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="wdm-removelockreleasewrite.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseWrite&lt;/strong&gt;](wdm-removelockreleasewrite.md)"><strong>RemoveLockReleaseWrite</strong></a></p></td>
<td align="left"><p><a href="wdm-removelockreleasewrite.md" data-raw-source="[&lt;strong&gt;RemoveLockReleaseWrite&lt;/strong&gt;](wdm-removelockreleasewrite.md)"> <strong>RemoveLockReleaseWrite</strong> </a>规则验证的调用<a href="https://msdn.microsoft.com/library/windows/hardware/ff548204" data-raw-source="[&lt;strong&gt;IoAcquireRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff548204)"> <strong>IoAcquireRemoveLock</strong> </a>并<a href="https://msdn.microsoft.com/library/windows/hardware/ff549560" data-raw-source="[&lt;strong&gt;IoReleaseRemoveLock&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549560)"> <strong>IoReleaseRemoveLock</strong> </a>严格的分支结构中使用。 此外，在调度例程末尾驱动程序不应阻止删除锁。</p></td>
</tr>
</tbody>
</table>

 

**若要选择 IrpTracking 规则集**

1.  Microsoft Visual Studio 中选择您的驱动程序项目 (.vcxProj)。 从**驱动程序**菜单上，单击**启动 Static Driver Verifier...**.

2.  单击**规则**选项卡。下**规则集**，选择**IrpTracking**。

    若要选择的默认规则集从 Visual Studio 开发人员命令提示符窗口，请指定**IrpTracking.sdv**与 **/check**选项。 例如：

    ```
    msbuild /t:sdv /p:Inputs="/check:IrpTracking.sdv" mydriver.VcxProj /p:Configuration="Win8 Release" /p:Platform=Win32
    ```

    有关详细信息，请参阅[以找到缺陷驱动程序中使用 Static Driver Verifier](https://msdn.microsoft.com/library/windows/hardware/hh454281)并[Static Driver Verifier 命令 (MSBuild)](https://msdn.microsoft.com/library/windows/hardware/hh466459)。

 

 




