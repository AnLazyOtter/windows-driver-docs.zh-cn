---
title: Bug 检查 0xB4 VIDEO_DRIVER_INIT_FAILURE
description: VIDEO_DRIVER_INIT_FAILURE bug 检查具有 0x000000B4 值。 这表示 Windows 无法进入图形模式。
ms.assetid: 37c2d07d-f351-42d0-ba88-9b9a2a3d19f8
keywords:
- Bug 检查 0xB4 VIDEO_DRIVER_INIT_FAILURE
- VIDEO_DRIVER_INIT_FAILURE
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- VIDEO_DRIVER_INIT_FAILURE
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 20ea652b025a52b4049c0a64bdafb1a728cbc9d1
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519013"
---
# <a name="bug-check-0xb4-videodriverinitfailure"></a>Bug 检查 0xB4：视频\_驱动程序\_INIT\_失败


视频\_驱动程序\_INIT\_故障错误检查的值为 0x000000B4。 这表示 Windows 无法进入图形模式。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="videodriverinitfailure-parameters"></a>视频\_驱动程序\_INIT\_失败参数


无

<a name="cause"></a>原因
-----

系统无法进入图形模式，因为没有显示器驱动程序已启动。

这通常发生在任何微型端口驱动程序不都能够成功加载。

 

 




