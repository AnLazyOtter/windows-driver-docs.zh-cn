---
title: 修改资源要求列表
description: 修改资源要求列表
ms.assetid: 75391dd2-5ae1-4562-97a0-4de21a08b61c
keywords:
- 硬件资源 WDK KMDF，修改资源需求列表
- 资源要求列出了 WDK KMDF，修改
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: c9439d9b28b6553bc2f8deaeb2aa7da3b463672c
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843142"
---
# <a name="modifying-a-resource-requirements-list"></a>修改资源要求列表


在 PnP 管理器确保已加载所有新连接设备的驱动程序后，它会将设备的硬件要求列表发送到设备的驱动程序堆栈。

当列表沿堆栈向下传递时，框架将调用每个函数和筛选器驱动程序的[*EvtDeviceFilterRemoveResourceRequirements*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nc-wdffdo-evt_wdf_device_filter_resource_requirements)回调函数，并将硬件需求列表作为输入参数传递。 此回调函数可以从总线驱动程序已指定的硬件要求列表中删除硬件资源，但不需要对设备进行操作来确定。

例如，PCI 总线驱动程序可能会根据 PCI 规范在内存空间中复制 i/o 空间资源。 如果你的设备可以在不使用 i/o 空间资源的情况下运行，则设备的函数驱动程序可以从硬件要求列表中删除 i/o 空间资源。

若要从要求列表中删除项，驱动程序可以执行以下操作：

-   调用以下方法来修改资源需求列表中的逻辑配置：
    -   [**WdfIoResourceRequirementsListGetCount**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcerequirementslistgetcount)，用于获取逻辑配置的数量。
    -   [**WdfIoResourceRequirementsListGetIoResList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcerequirementslistgetioreslist)，用于获取对逻辑配置的访问权限。
    -   [**WdfIoResourceRequirementsListRemove**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcerequirementslistremove)和[**WdfIoResourceRequirementsListRemoveByIoResList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcerequirementslistremovebyioreslist)，用于删除逻辑配置。
-   调用以下方法来修改逻辑配置中的资源描述符：
    -   [**WdfIoResourceListGetCount**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistgetcount)，用于获取资源说明符的数目。
    -   [**WdfIoResourceListGetDescriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistgetdescriptor)，用于获取对资源描述符的访问权限。
    -   [**WdfIoResourceListRemove**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistremove)和[**WdfIoResourceListRemoveByDescriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistremovebydescriptor)，用于删除资源描述符。

当列表沿驱动程序堆栈向上移动时，框架将调用每个函数和筛选器驱动程序的[*EvtDeviceFilterAddResourceRequirements*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nc-wdffdo-evt_wdf_device_filter_resource_requirements)回调函数，并将硬件需求列表作为输入参数传递。 此回调函数可以添加功能驱动程序所需的其他硬件资源，以使设备正常运行。

若要将项添加到硬件要求列表，驱动程序可以执行以下操作：

-   调用以下方法来修改资源需求列表中的逻辑配置：
    -   [**WdfIoResourceRequirementsListGetCount**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcerequirementslistgetcount)，用于获取逻辑配置的数量。
    -   [**WdfIoResourceRequirementsListGetIoResList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcerequirementslistgetioreslist)，用于获取对逻辑配置的访问权限。
    -   [**WdfIoResourceListCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistcreate)，用于创建新的逻辑配置。
    -   [**WdfIoResourceRequirementsListAppendIoResList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcerequirementslistappendioreslist)或[**WdfIoResourceRequirementsListInsertIoResList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcerequirementslistinsertioreslist)，用于添加新的逻辑配置。
-   调用以下方法来修改逻辑配置中的资源描述符：
    -   [**WdfIoResourceListGetCount**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistgetcount)，用于获取资源说明符的数目。
    -   [**WdfIoResourceListGetDescriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistgetdescriptor)，用于获取对资源描述符的访问权限。
    -   [**WdfIoResourceListAppendDescriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistappenddescriptor)或[**WdfIoResourceListInsertDescriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfioresourcelistinsertdescriptor)，用于添加资源描述符。

 

 





