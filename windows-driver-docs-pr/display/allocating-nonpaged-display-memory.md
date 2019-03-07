---
title: 分配非分页的显示内存
description: 分配非分页的显示内存
ms.assetid: 6a8523e7-3955-4289-b131-52556ba3e631
keywords:
- 非分页的显示内存 WDK DirectX 9.0
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 95ec52f08d2c2adb49bc2adb84fe4b9d43c27be3
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56533663"
---
# <a name="allocating-nonpaged-display-memory"></a>分配非分页的显示内存


## <span id="ddk_allocating_nonpaged_display_memory_gg"></span><span id="DDK_ALLOCATING_NONPAGED_DISPLAY_MEMORY_GG"></span>


**本主题仅适用于 Microsoft Windows XP 和更高版本。**

DirectX 9.0 版本显示驱动程序可以调用[ **EngAllocMem** ](https://msdn.microsoft.com/library/windows/hardware/ff564176)图形设备接口 (GDI) 函数不仅从系统分配的内存分页池还从非分页缓冲池。 若要分配非分页的内存，该驱动程序必须指定 FL\_未分页\_中的内存标志*标志*参数**EngAllocMem**调用。 如果未指定此标志，从系统的页面缓冲池分配内存。

Windows 2000 和前面仅允许从分配的系统页面缓冲池。

虽然从非分页缓冲池分配的这一功能已推出 WindowsXP 及更高版本，它是未记录在 Windows XP 和 Windows XP Service Pack 1 (SP1) Ddk 中。

 

 




