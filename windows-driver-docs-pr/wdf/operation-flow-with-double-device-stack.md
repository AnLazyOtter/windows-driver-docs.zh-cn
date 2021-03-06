---
title: 使用双设备堆栈的操作流
description: 使用双设备堆栈的操作流
ms.assetid: a717b9c0-b24a-4347-8b0a-254a17238b5f
keywords:
- 操作流 WDK UMDF
- I/o 请求 WDK UMDF，操作流
- 请求处理 WDK UMDF，操作流
- 双设备堆栈流 WDK UMDF
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: aaa439033553356082f5b8bf4f670151e6c56988
ms.sourcegitcommit: d30691c8276f7dddd3f8333e84744ddeea1e1020
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75210877"
---
# <a name="operation-flow-with-double-device-stack"></a>使用双设备堆栈的操作流


[!include[UMDF 1 Deprecation](../includes/umdf-1-deprecation.md)]

下图显示了与一个双设备堆栈中的 UMDF 筛选器和功能驱动程序之间发生的操作流。

![umdf 筛选器驱动程序和 umdf 函数驱动程序的 umdf i/o 调用顺序](images/umdfflow2.gif)

  **请注意**，应用程序启动的所有 i/o 都将通过内核模式路由，如 UMDF 部分的[体系结构](https://docs.microsoft.com/previous-versions/ff554461(v=vs.85))中所示，即使上图中没有显示这种情况，也是如此。

 

如果 UMDF 筛选器和函数驱动程序需要有关与读取请求关联的文件的信息，则该方法还可以调用[**IWDFIoRequest：： GetCreateParameters**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfddi/nf-wudfddi-iwdfiorequest-getcreateparameters)方法。 如果 UMDF 筛选器和函数驱动程序需要有关读取请求的详细信息，还可以调用[**IWDFIoRequest：： GetReadParameters**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfddi/nf-wudfddi-iwdfiorequest-getreadparameters)方法。

UMDF 功能驱动程序调用[**IWDFIoRequest：： Complete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfddi/nf-wudfddi-iwdfiorequest-complete)或[**IWDFIoRequest：： CompleteWithInformation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfddi/nf-wudfddi-iwdfiorequest-completewithinformation)方法来向筛选器驱动程序发出信号，指示该驱动程序已通过读取操作完成。 如果 UMDF 筛选器驱动程序需要更多的信息来完成读取请求，则该驱动程序还可以调用[IWDFIoRequestCompletionParams](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfddi/nn-wudfddi-iwdfiorequestcompletionparams)接口的方法。 UMDF 筛选器驱动程序调用**complete**或**CompleteWithInformation**以指示读取操作完成;然后，应用程序可以访问读取数据。

 

 





