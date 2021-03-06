---
title: 创建和使用 DirectX VA 2.0 扩展设备
description: 创建和使用 DirectX VA 2.0 扩展设备
ms.assetid: 650a77a5-67c3-4b11-93c8-24232905eb43
keywords:
- DirectX 视频加速 WDK 显示，扩展支持
- 视频加速 WDK DirectX，扩展支持
- VA WDK DirectX，扩展支持
- 扩展设备 WDK DirectX VA
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: a26e8c0e09b86d5c6dd62d9f36d2d757468b3381
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72839026"
---
# <a name="creating-and-using-a-directx-va-20-extension-device"></a>创建和使用 DirectX VA 2.0 扩展设备


Microsoft Direct3D runtime 调用用户模式显示驱动程序的[**CreateExtensionDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dumddi/nc-d3dumddi-pfnd3dddi_createextensiondevice)函数来创建用于 DirectX VA 2.0 的扩展设备。 当 Direct3D 运行时完成设备后，它将调用用户模式显示驱动程序的[**DestroyExtensionDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dumddi/nc-d3dumddi-pfnd3dddi_destroyextensiondevice)函数。

Direct3D 运行时调用用户模式显示驱动程序的[**DecodeExtensionExecute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dumddi/nc-d3dumddi-pfnd3dddi_decodeextensionexecute)函数，以便在开始框架和结束帧时间段之间以及特定呈现目标图面上的非标准解码设备上解码视频。 有关解码视频的一般讨论，请参阅[解码视频](decoding-video.md)。

Direct3D 运行时调用用户模式显示驱动程序的[**ExtensionExecute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dumddi/nc-d3dumddi-pfnd3dddi_extensionexecute)函数，在扩展设备上执行非标准 DirectX VA 2.0 操作。

 

 





