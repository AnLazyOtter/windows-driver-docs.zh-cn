---
title: 捕获、预览和静态类别
description: 捕获、预览和静态类别
ms.assetid: b82cc3b6-1cea-4864-9501-95919f05455f
keywords:
- 流类别 WDK 视频捕获、捕获视频流
- 流类别 WDK 视频捕获，预览视频流
- 流类别 WDK 视频捕获、捕获静态图像
- 捕获视频流类别 WDK 视频捕获
- 预览视频流类别 WDK 视频捕获
- 捕获静止映像类别 WDK 视频捕获
- PINNAME_VIDEO_CAPTURE
- NAME_VIDEO_PREVIEW
- PINNAME_VIDEO_STILL
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 442932b257ed01e8a8677684afe511bab505881b
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72844742"
---
# <a name="capture-preview-and-still-category"></a>捕获、预览和静态类别


以下 Guid 对应于捕获视频流、预览视频流和捕获静态图像的类别（如果硬件支持）：

-   **PINNAME\_视频\_捕获**

    捕获类别输出插针提供压缩或未压缩数字视频流。 此流类别用于将电影写入磁盘、视频会议和图像分析。

-   **PINNAME\_视频\_预览版**

    预览类别输出插针提供未压缩数字视频流。 使用此流类别可以通过 DirectDraw 直接显示的 RGB 或 YUV 格式查看本地监视器上的视频流。 在资源有限的情况下，捕获微型驱动程序应将预览流 pin 的优先级设置为低于捕获流 pin。

-   **PINNAME\_视频\_**

    静止类别输出插针用于双模式相机，它们能够同时生成捕获流和静止图像流（这通常比捕获流更高）。 静止图像流包括外部或以编程方式触发图像获取功能的功能。

"捕获"、"预览" 和 "静止流" pin 类别在数据格式和流特征方面几乎完全相同。

**请注意**  ：由于很多照相机仅生成一个输出流，因此 Microsoft DirectShow 包含一个智能 t 筛选器，可将单个流拆分到捕获和预览流中。 因此，仅生成一个流的照相机微型驱动程序不应在内部复制其数据流以生成预览流。

 

指定**PINNAME\_视频\_捕获**或**PINNAME\_视频\_预览**，或**PINNAME\_视频\_仍**为 pin 时，请使用下表中列出的信息。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DataRange 结构</strong></p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_video" data-raw-source="[&lt;strong&gt;KS_DATARANGE_VIDEO&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_video)"><strong>KS_DATARANGE_VIDEO</strong></a> （仅限帧）</p>
<p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_video2" data-raw-source="[&lt;strong&gt;KS_DATARANGE_VIDEO2&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_video2)"><strong>KS_DATARANGE_VIDEO2</strong></a> （字段或框架、bob 或编织设置）</p>
<p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_mpeg1_video" data-raw-source="[&lt;strong&gt;KS_DATARANGE_MPEG1_VIDEO&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_mpeg1_video)"><strong>KS_DATARANGE_MPEG1_VIDEO</strong></a></p>
<p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_mpeg2_video" data-raw-source="[&lt;strong&gt;KS_DATARANGE_MPEG2_VIDEO&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_mpeg2_video)"><strong>KS_DATARANGE_MPEG2_VIDEO</strong></a></p></td>
</tr>
<tr class="even">
<td><p><strong>DataFormat 结构</strong></p></td>
<td><p>KS_DATAFORMAT_VIDEO （仅限帧）</p>
<p>KS_DATAFORMAT_VIDEO2 （字段或框架、bob 或编织设置）</p>
<p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_mpeg1videoinfo" data-raw-source="[&lt;strong&gt;KS_MPEG1VIDEOINFO&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_mpeg1videoinfo)"><strong>KS_MPEG1VIDEOINFO</strong></a> （适用于 MPEG1）</p>
<p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_mpegvideoinfo2" data-raw-source="[&lt;strong&gt;KS_MPEGVIDEOINFO2&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_mpegvideoinfo2)"><strong>KS_MPEGVIDEOINFO2</strong></a> （适用于 MPEG2）</p></td>
</tr>
<tr class="odd">
<td><p><strong>主要格式 GUID</strong></p></td>
<td><p>KSDATAFORMAT_TYPE_VIDEO</p></td>
</tr>
<tr class="even">
<td><p><strong>子格式 GUID</strong></p></td>
<td><p>RGB16、RGB24、UYVY、JPEG</p></td>
</tr>
<tr class="odd">
<td><p><strong>说明符 GUID</strong></p></td>
<td><p>KSDATAFORMAT_SPECIFIER_VIDEOINFO （仅限帧）</p>
<p>KSDATAFORMAT_SPECIFIER_VIDEOINFO2 （字段或框架）</p></td>
</tr>
<tr class="even">
<td><p><strong>扩展的标头大小</strong></p></td>
<td><p>如果不是 MPEG 格式，则<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_frame_info" data-raw-source="[&lt;strong&gt;KS_FRAME_INFO&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_frame_info)"><strong>KS_FRAME_INFO</strong></a> 。 如果为 MPEG 格式，则为零。</p></td>
</tr>
<tr class="odd">
<td><p><strong>必需的属性集</strong></p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/stream/kspropsetid-connection" data-raw-source="[KSPROPSETID_Connection](https://docs.microsoft.com/windows-hardware/drivers/stream/kspropsetid-connection)">KSPROPSETID_Connection</a></p>
<p><a href="https://docs.microsoft.com/windows-hardware/drivers/stream/propsetid-vidcap-droppedframes" data-raw-source="[PROPSETID_VIDCAP_DROPPEDFRAMES](https://docs.microsoft.com/windows-hardware/drivers/stream/propsetid-vidcap-droppedframes)">PROPSETID_VIDCAP_DROPPEDFRAMES</a></p></td>
</tr>
<tr class="even">
<td><p><strong>必需的事件集</strong></p></td>
<td><p>无</p></td>
</tr>
<tr class="odd">
<td><p><strong>DirectShow majortype</strong></p></td>
<td><p>MEDIATYPE_Video</p></td>
</tr>
<tr class="even">
<td><p><strong>DirectShow formattype</strong></p></td>
<td><p>FORMAT_VideoInfo （仅限帧）</p>
<p>FORMAT_VideoInfo2 （字段或框架）</p></td>
</tr>
</tbody>
</table>

 

 

 




