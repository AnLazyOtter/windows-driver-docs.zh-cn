---
title: 定义反交错容器设备类
description: 定义反交错容器设备类
ms.assetid: 683c8d89-33d5-4b2a-b24a-4e316c3fa64b
keywords:
- 取消隔行扫描容器设备 WDK DirectX VA
- 容器设备 WDK DirectX VA
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: cd8b8c0eb8f9617132fbdc072244ba8be17564ba
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63367925"
---
# <a name="defining-the-deinterlace-container-device-class"></a>定义反交错容器设备类


## <span id="ddk_defining_the_deinterlace_container_device_class_gg"></span><span id="DDK_DEFINING_THE_DEINTERLACE_CONTAINER_DEVICE_CLASS_GG"></span>


使用下面的示例代码来定义取消隔行扫描容器设备类：

```cpp
// Deinterlace container device class.
struct DXVA_DeinterlaceContainerDeviceClass : public DXVA_DeviceBaseClass
{
    // Uses the base class's constructor.
    DXVA_DeinterlaceContainerDeviceClass(const GUID& guid, DXVA_DeviceType Type) :
        DXVA_DeviceBaseClass(guid, Type)
    {}
     // Part of the Deinterlace DDI.
    HRESULT DeinterlaceQueryAvailableModes(
        LPDXVA_VideoDesc lpVideoDescription,
        LPDWORD lpdwNumModesSupported,
        LPGUID pGuidsDeinterlaceModes
        );
    // Part of the Deinterlace DDI.
    HRESULT DeinterlaceQueryModeCaps(
        LPGUID pGuidDeinterlaceMode,
        LPDXVA_VideoDesc lpVideoDescription,
        LPDXVA_DeinterlaceCaps lpDeinterlaceCaps
        );
     // Part of the ProcAmp Control DDI.
    HRESULT ProcAmpControlQueryCaps(
        LPDXVA_VideoDesc lpVideoDescription,
        LPDXVA_ProcAmpControlCaps lpProcAmpControlCaps
        );
    // Part of the ProcAmp Control DDI.
    HRESULT ProcAmpControlQueryRange(
        DWORD VideoProperty,
        LPDXVA_VideoDesc lpVideoDescription,
        LPDXVA_VideoPropertyRange lpProcAmpControlRange
        );
};
```

 

 





