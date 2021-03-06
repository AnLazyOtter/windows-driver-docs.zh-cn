---
title: OID_TCP_OFFLOAD_PARAMETERS
description: 本主题介绍 OID_TCP_OFFLOAD_PARAMETERS 对象标识符（OID）。
ms.assetid: 5D9B5F62-E506-4983-B247-A93B81E70A43
keywords:
- OID_TCP_OFFLOAD_PARAMETERS，WDK Oid，WDK 网络对象标识符，WDK 网络 Oid
ms.date: 11/01/2017
ms.localizationpriority: medium
ms.openlocfilehash: 8d3b2d590dcb920d49eb9436fc2e0eaf1cd48f6a
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843902"
---
# <a name="oid_tcp_offload_parameters"></a>OID_TCP_OFFLOAD_PARAMETERS

不支持查询请求。

作为一个集请求，OID_TCP_OFFLOAD_PARAMETERS OID 设置微型端口适配器的当前 TCP 卸载配置。 协议驱动程序或用户模式应用程序可以设置此 OID 以更改当前的 TCP 卸载配置。 系统管理员可以通过 Microsoft Windows Management Instrumentation （WMI）接口使用此 OID。

## <a name="remarks"></a>备注

对于支持 TCP 卸载的微型端口驱动程序和其他微型端口驱动程序的可选参数，OID_TCP_OFFLOAD_PARAMETERS 是必需的。 如果微型端口驱动程序不支持此 OID，则驱动程序将返回 NDIS_STATUS_NOT_SUPPORTED。

[NDIS_OID_REQUEST](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request)结构的**InformationBuffer**成员包含[NDIS_OFFLOAD_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload_parameters)结构。 如果**InformationBuffer**的内容无效，微型端口驱动程序应返回 NDIS_STATUS_INVALID_DATA 以响应此 OID。

当 NDIS 处理此 OID，并在将 OID 传递到微型端口驱动程序之前，NDIS 将用新设置更新微型端口适配器的卸载标准化关键字。

微型端口驱动程序必须使用[NDIS_OFFLOAD_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload_parameters)结构的内容来更新当前报告的 TCP 卸载功能。 更新后，微型端口驱动程序必须报告当前的任务卸载功能， [NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG](ndis-status-task-offload-current-config.md)状态指示。 此状态指示可确保所有的过量协议驱动程序都用新功能信息进行更新。

此 OID 是一个更全面的 OID，指示微型端口驱动程序启用或禁用某些卸载。 大多数 TCP/IP 任务卸载均可通过此 OID 进行配置和激活。 对于某些卸载，如 Rx 校验和或 Rx IPSec，此 OID 作为配置更改，并不意味着卸载将立即操作。 若要激活这些卸载，微型端口驱动程序必须等待，直到它收到[OID_OFFLOAD_ENCAPSULATION](oid-offload-encapsulation.md)设置请求。

设置 OID_TCP_OFFLOAD_PARAMETERS 之前，上层应用程序或驱动程序可以使用[OID_TCP_OFFLOAD_HARDWARE_CAPABILITIES](oid-tcp-offload-hardware-capabilities.md) OID 来确定微型端口适配器的硬件可以支持哪些功能。 使用 OID_TCP_OFFLOAD_PARAMETERS 启用[OID_TCP_OFFLOAD_CURRENT_CONFIG](oid-tcp-offload-current-config.md) OID 报告为未启用的功能。

### <a name="see-also"></a>另请参阅

[NDIS_OFFLOAD_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload_parameters)  
[NDIS_OID_REQUEST](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request)  
[NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG](ndis-status-task-offload-current-config.md)  
[OID_TCP_OFFLOAD_CURRENT_CONFIG](oid-tcp-offload-current-config.md)  
[OID_TCP_OFFLOAD_HARDWARE_CAPABILITIES](oid-tcp-offload-hardware-capabilities.md)

## <a name="requirements"></a>要求

| | |
| --- | --- |
| 版本 | Windows Vista 及更高版本 |
| 标头 | Ntddndis （包括 Ndis .h） |

