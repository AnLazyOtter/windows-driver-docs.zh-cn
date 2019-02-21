---
title: OID_TCP_TASK_IPSEC_DELETE_SA
description: 本主题介绍 OID_TCP_TASK_IPSEC_DELETE_SA 对象标识符 (OID)。
ms.assetid: 5f3b1f30-ab44-4d1c-96ff-b70ae6cfe324
keywords:
- OID_TCP_TASK_IPSEC_DELETE_SA
ms.date: 11/06/2017
ms.localizationpriority: medium
ms.openlocfilehash: 6f6c61150fd7976f2fb6b9b0c590bf524afadf94
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56523492"
---
# <a name="oidtcptaskipsecdeletesa"></a>OID_TCP_TASK_IPSEC_DELETE_SA

传输协议设置 OID_TCP_TASK_IPSEC_DELETE_SA OID 以请求微型端口驱动程序从 NIC 中删除安全关联 (SA) SA 信息的格式为[OFFLOAD_IPSEC_DELETE_SA](https://msdn.microsoft.com/library/windows/hardware/ff569058)结构。

在接收到此请求，微型端口驱动程序应删除任何系统资源分配给 SA 指定的 SA 从 NIC 和免费。

## <a name="requirements"></a>要求

| | |
| --- | --- |
| 版本 | Windows Vista 及更高版本 |
| 标头 | Ntddndis.h （包括 Ndis.h） |
