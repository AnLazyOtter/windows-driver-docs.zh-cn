---
title: Bug 检查 0x1CF HARDWARE_WATCHDOG_TIMEOUT
description: HARDWARE_WATCHDOG_TIMEOUT bug 检查具有 0x000001CF 值。
keywords:
- Bug 检查 0x1CF HARDWARE_WATCHDOG_TIMEOUT
- HARDWARE_WATCHDOG_TIMEOUT
ms.date: 05/23/2018
topic_type:
- apiref
api_name:
- HARDWARE_WATCHDOG_TIMEOUT
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 4fd2513c1ddbf0522d80dfdb93a585f3e820c289
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519679"
---
# <a name="bug-check-bug-check-0x1cf-hardwarewatchdogtimeout"></a>Bug 检查 Bug 检查 0x1CF:硬件\_监视器\_超时 

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


HARDWARE_WATCHDOG_TIMEOUT bug 检查具有 0x000001CF 值。 这表明系统已挂起和未处理计时器时钟周期。


## <a name="hardwarewatchdogtimeout-parameters"></a>硬件\_监视器\_超时参数
 
参数 | 描述 
|---------|--------------|
1 | 自监视器上次重置，在中断时间以来的时间。
2 | 当前的中断时间。
3 | 当前 QPC 时间戳。
4 | 时钟处理器的索引。


 

 




