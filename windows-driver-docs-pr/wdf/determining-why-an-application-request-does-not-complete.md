---
title: 确定应用程序请求无法完成的原因
description: 本主题介绍如何结合使用用户模式驱动程序框架 (UMDF) 版本 1 或 2 驱动程序中使用 Wudfext.dll 调试器扩展来确定应用程序请求无法完成。
ms.assetid: 33a09277-1e00-4f91-b2ab-b2541091628f
keywords:
- UMDF WDK，未完成的应用程序请求
- 调试方案 WDK UMDF，未完成的应用程序请求
- UMDF WDK，调试方案中，未完成的应用程序请求
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 1238b504155757319b5f3a67d925f74b6f445f9c
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67377429"
---
# <a name="determining-why-an-application-request-does-not-complete"></a>确定应用程序请求无法完成的原因


本主题介绍如何结合使用用户模式驱动程序框架 (UMDF) 版本 1 或 2 驱动程序中使用 Wudfext.dll 调试器扩展来确定应用程序请求无法完成。

对于 UMDF 版本 1，将使用在 wudfext.dll 中实现的扩展命令。 从 UMDF 版本 2 开始，将使用在 wdfkd.dll 中实现的扩展命令。

您可以执行以下步骤来确定应用程序请求无法完成：

1.  使用[ **！ wudfext.umirps** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wudfext-umirps) (UMDF 1) 或[ **！ wdfkd.wdfumirps** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumirps) (UMDF 2) 若要显示所有用户模式下未完成 I/O 请求数据包 （Irp) 在主机进程。 每个用户模式下 IRP 的信息包括原始的内核模式 IRP 为其创建用户模式下 IRP。

    确定对应于内核模式 IRP 应用程序发起的用户模式下 IRP。

2.  使用[ **！ wudfext.umirp** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wudfext-umirp) (UMDF 1) 或[ **！ wdfkd.wdfumirp** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumirp) (UMDF 2) 若要获取有关特定的用户模式下 IRP 的信息。

    用于用户模式下 IRP 信息包括的堆栈位置。 如果您知道的堆栈位置，您可以确定处理 IRP 所在的位置。 堆栈位置 0 表示 UMDF （即，内核模式堆栈或某些其他子系统，如 Microsoft Win32 或 Winsock） 下的堆栈。

3.  如果 IRP 位于驱动程序的层 （即，层在其中您的驱动程序处理 IRP），请执行以下步骤：
    1.  查看在您的驱动程序的层上设置的 I/O 队列。 可以使用[ **！ wudfext.wudfdevicequeues** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wudfext-wudfdevicequeues) (UMDF 1) 或[ **！ wdfkd.wdfdevicequeues** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdevicequeues) (UMDF 2) 若要查看所有设置的 I/O 队列最多在驱动程序的层。 此外可以使用[ **！ wudfext.wudfqueue** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wudfext-wudfqueue) (UMDF 1) 或[ **！ wdfkd.wdfqueue** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfqueue) (UMDF 2) 若要获取有关特定队列的信息。

    2.  如果有多个请求未完成，则可以使用[ **！ wudfext.wudfrequest** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wudfext-wudfrequest) (UMDF 1) 或[ **！ wdfkd.wdfrequest** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfrequest) (UMDF 2) 到获取有关请求，其中包括基础的用户模式下 IRP 的信息。 从用户模式下 IRP 信息，您可以确定你感兴趣的请求。
    3.  验证由队列或驱动程序是否拥有该请求。 此信息显示为从输出的一部分[ **！ wudfext.wudfqueue** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wudfext-wudfqueue)或[ **！ wdfkd.wdfqueue**](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfqueue)。 执行以下验证，具体取决于队列或驱动程序是否拥有该请求之一：
        -   如果请求所有队列中，检查要确定队列不到驱动程序传送该请求的原因的队列的状态。
        -   如果请求所有驱动程序，请在主机进程来确定线程是否变得停滞或处理请求时出现死锁的线程。

4.  如果在另一个 UMDF 驱动程序层 IRP，您可以为该层重复上述步骤。 请记住，您可以使用[ **！ wudfext.umdevstack** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wudfext-umdevstack) (UMDF 1) 或[ **！ wdfkd.wdfumdevstack** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumdevstack) (UMDF 2) 若要查看有关所有信息堆栈层。

5.  如果不在 IRP UMDF 堆栈 （例如，如果堆栈位置 0 是当前正在处理 IRP），确定相应的内核模式 IRP 未完成。

 

 





