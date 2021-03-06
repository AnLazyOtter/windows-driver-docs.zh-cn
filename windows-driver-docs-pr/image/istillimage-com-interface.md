---
title: IStillImage COM 接口
description: IStillImage COM 接口
ms.assetid: eb60a3fd-e7e2-4d3c-973e-af8cb3c3c511
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 8cbb8c9c24c9f92c0cbde20dcefc45e56ccdda65
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67378905"
---
# <a name="istillimage-com-interface"></a>IStillImage COM 接口





**IStillImage** COM 接口提供对访问[静止图像事件监控程序](overview-of-sti-components.md#ddk-still-image-event-monitor-si)使应用程序可以将自身注册为"推送模型注意"。 应用程序可以使用此接口来获取有关系统的静止图像设备信息。

该接口提供某些应用程序管理功能，例如启用事件通知和启动应用程序，以供自定义应用程序管理软件。

此外， **IStillImage**接口提供对访问[IStiDevice COM 接口](istidevice-com-interface.md)，它允许应用程序执行静止图像设备上的 I/O 操作。

下表列出并描述的所有**IStillImage**接口的方法。 此表指示通常必须调用每个方法的客户端的类型。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
<th>典型的调用方</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543778(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::CreateDevice&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543778(v=vs.85))"><strong>IStillImage::CreateDevice</strong></a></p></td>
<td><p>创建定义的 COM 对象的实例<strong>IStiDevice</strong>接口，并返回指向该接口的指针。</p></td>
<td><p>图像采集 Api</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543780(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::EnableHwNotifications&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543780(v=vs.85))"><strong>IStillImage::EnableHwNotifications</strong></a></p></td>
<td><p>启用或禁用通知的应用程序时<a href="still-image-device-events.md" data-raw-source="[Still Image Device Events](still-image-device-events.md)">仍映像设备事件</a>发生指定的设备。</p></td>
<td><p>静止图像事件监视器</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543782(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::GetDeviceInfo&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543782(v=vs.85))"><strong>IStillImage::GetDeviceInfo</strong></a></p></td>
<td><p>返回指定静止图像设备的硬件特征。</p></td>
<td><p>图像采集 Api</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543784(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::GetDeviceList&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543784(v=vs.85))"><strong>IStillImage::GetDeviceList</strong></a></p></td>
<td><p>返回所有的硬件特征仍安装映像的设备。</p></td>
<td><p>扫描仪和照相机控件面板中，图像采集 Api</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543786(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::GetDeviceValue&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543786(v=vs.85))"><strong>IStillImage::GetDeviceValue</strong></a></p></td>
<td><p>返回与指定的静止图像设备相关联的注册表信息。</p></td>
<td><p>图像采集 Api、 扫描仪和照相机控件面板</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543788(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::GetHwNotificationState&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543788(v=vs.85))"><strong>IStillImage::GetHwNotificationState</strong></a></p></td>
<td><p>指示映像设备事件仍在指定的设备上发生时是否会通知应用程序。</p></td>
<td><p>静止图像事件监视器</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543790(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::GetSTILaunchInformation&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543790(v=vs.85))"><strong>IStillImage::GetSTILaunchInformation</strong></a></p></td>
<td><p>返回已启动调用静止图像的应用程序的原因，如果静止图像事件监视器启动它。</p></td>
<td><p>推送模型识别应用程序</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543793(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::Initialize&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543793(v=vs.85))"><strong>IStillImage::Initialize</strong></a></p></td>
<td><p>初始化的对象实例。</p></td>
<td><p>不直接调用</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543796(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::LaunchApplicationForDevice&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543796(v=vs.85))"><strong>IStillImage::LaunchApplicationForDevice</strong></a></p></td>
<td><p>启动指定的静止图像设备指定的应用程序。</p></td>
<td><p>静止图像事件监视器</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543798(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::RegisterLaunchApplication&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543798(v=vs.85))"><strong>IStillImage::RegisterLaunchApplication</strong></a></p></td>
<td><p>将添加到静止图像事件监视器的列表的推送模型识别应用程序的应用程序。</p></td>
<td><p>推送模型识别应用程序或它们的安装程序</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543799(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::Release&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543799(v=vs.85))"><strong>IStillImage::Release</strong></a></p></td>
<td><p>关闭对象实例，并删除对访问权限<strong>IStillImage</strong>接口。</p></td>
<td><p>所有<strong>IStillImage</strong>接口客户端</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543801(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::SetDeviceValue&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543801(v=vs.85))"><strong>IStillImage::SetDeviceValue</strong></a></p></td>
<td><p>设置指定静止图像设备的注册表信息。</p></td>
<td><p>扫描仪和照相机控件面板</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543803(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::SetupDeviceParameters&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543803(v=vs.85))"><strong>IStillImage::SetupDeviceParameters</strong></a></p></td>
<td><p>允许的客户端<strong>IStillImage</strong>界面，用于修改静态图像设备存储特征。</p></td>
<td><p>扫描仪和照相机控件面板</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543804(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::StiCreateInstance&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543804(v=vs.85))"><strong>IStillImage::StiCreateInstance</strong></a></p></td>
<td><p>创建定义的 COM 对象的实例<strong>IStillImage</strong>接口，并返回指向该接口的指针。</p></td>
<td><p>所有<strong>IStillImage</strong>接口客户端</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543806(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::UnregisterLaunchApplication&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543806(v=vs.85))"><strong>IStillImage::UnregisterLaunchApplication</strong></a></p></td>
<td><p>推送模型识别应用程序静止图像事件监视器的列表中移除应用程序。</p></td>
<td><p>推送模型识别应用程序或它们的安装程序</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543807(v=vs.85)" data-raw-source="[&lt;strong&gt;IStillImage::WriteToErrorLog&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff543807(v=vs.85))"><strong>IStillImage::WriteToErrorLog</strong></a></p></td>
<td><p>静止图像错误日志中写入一条消息。</p></td>
<td><p>所有<strong>IStillImage</strong>接口客户端</p></td>
</tr>
</tbody>
</table>

 

 

 




