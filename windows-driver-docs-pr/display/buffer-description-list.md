---
title: 缓冲区说明列表
description: 缓冲区说明列表
ms.assetid: 7d820491-2df2-4036-8f3d-e6bcff4cd1f6
keywords:
- 视频解码 WDK DirectX VA，缓冲区说明列表
- 解码视频 WDK DirectX VA，缓冲区说明列表
- 解码 WDK DirectX VA，缓冲区描述列表的图片
- 缓冲 WDK DirectX VA
- 缓冲说明列表 WDK DirectX VA
- DXVA_BufferDescription
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 8aaea7ebea615fceac2d37bfc4af5a7fb2bc79ab
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63341567"
---
# <a name="buffer-description-list"></a>缓冲区说明列表


## <span id="ddk_buffer_description_list_gg"></span><span id="DDK_BUFFER_DESCRIPTION_LIST_GG"></span>


DirectX VA 操作主要是通过将从主机解码器的数据的缓冲区传递给硬件加速器。 当一组缓冲区传递从主机到加速器时，发送缓冲区描述列表来描述缓冲区。 缓冲区描述列表是一个数组[ **DXVA\_BufferDescription** ](https://msdn.microsoft.com/library/windows/hardware/ff563122)结构。 缓冲区描述列表包含一个 DXVA\_BufferDescription 结构中的一组缓冲区发送每个缓冲区。 缓冲区描述列表起初只具有一个或多个 DXVA\_BufferDescription 发送缓冲区的第一种类型的结构。 这一切后跟一个或多个 DXVA\_BufferDescription 结构下一步要发送的缓冲区和等等的类型。

值**dwTypeIndex**的成员[ **DXVA\_BufferDescription** ](https://msdn.microsoft.com/library/windows/hardware/ff563122)结构指定哪种类型的缓冲区传递到主机中加速器。

 

 




