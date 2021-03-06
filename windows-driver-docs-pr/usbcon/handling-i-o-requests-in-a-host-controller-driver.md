---
Description: 用于处理由 UCX 发送的 i/o 请求的主机控制器驱动程序的最佳实践。
title: 处理 USB 主控制器驱动程序中的 I/O 请求
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: eaceb81d948704c0ab0df6b9ff872f043f99d739
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72845000"
---
# <a name="handle-io-requests-in-a-usb-host-controller-driver"></a>处理 USB 主控制器驱动程序中的 I/O 请求


用于处理由 UCX 发送的 i/o 请求的主机控制器驱动程序的最佳实践。

UCX 跟踪 USB 总线上设备的主机控制器驱动程序所创建的所有终结点。 集线器驱动程序发送的任何数据传输请求，或由 USB 设备堆栈中较高级别的驱动程序发送的任何数据都首先由 UCX 处理。 UCX 负责将框架请求对象转发到正确的终结点队列。 请求中包含的 USB 请求块（URB）可以指定终结点句柄。 如果指定了终结点句柄，UCX 将在设备的终结点中检查相应的终结点。 如果指定的终结点句柄存在，则会将请求转发到终结点的队列。 如果找不到指定的终结点句柄，则请求失败。 如果未指定句柄，则请求为默认终结点，UCX 将请求转发到该设备的主机控制器驱动程序的默认终结点队列。

若要确保与现有 USB 驱动程序兼容，在完成 URB 请求时，主机控制器必须符合以下要求：

-  在调度\_级别，必须调用[**WdfRequestComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcomplete) 。
-   如果 URB 已传递到其框架队列，并且驱动程序开始在调用驱动程序的线程或 DPC 上同步处理它，则请求也不应同步完成。 该请求必须在单独的 DPC 上完成，可以通过调用[**WdfDpcEnqueue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdpc/nf-wdfdpc-wdfdpcenqueue)来安排。
-   类似于前述要求，在接收[**EVT_WDF_IO_QUEUE_IO_CANCELED_ON_QUEUE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfio/nc-wdfio-evt_wdf_io_queue_io_canceled_on_queue)或[**EVT_WDF_REQUEST_CANCEL**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nc-wdfrequest-evt_wdf_request_cancel)时，主机控制器驱动程序必须通过调用线程或 DPC 在单独的 DPC 上完成 URB 请求。 默认情况下，WDF 以同步方式在队列上完成取消的请求。 此行为可能会导致 URB 请求出现问题。 出于此原因，驱动程序必须为其 URB 队列提供*EvtIoCanceledOnQueue*回调。

[**IOCTL\_内部\_USB\_提交\_URB**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbioctl/ni-usbioctl-ioctl_internal_usb_submit_urb)的 framework 请求对象包含位于**参数. 其他.** 请求的 URB。 请求完成后，URB 状态必须设置为 USBD\_状态\_成功，或设置为指示故障性质的失败状态。 故障状态值在 usb .h 头文件中定义。

## <a name="related-topics"></a>相关主题
[为 USB 主控制器开发 Windows 驱动程序](developing-windows-drivers-for-usb-host-controllers.md)  



