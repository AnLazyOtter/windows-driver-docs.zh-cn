---
title: 修改可处理已完成请求的代码
description: 修改可处理已完成请求的代码
ms.assetid: 0DD48424-A728-4887-9F26-46B7004CB12C
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f73fadbd243ff0361b558d66ceab1176220cb4c5
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63325167"
---
# <a name="revise-code-that-handles-completed-requests"></a>修改可处理已完成请求的代码


Windows 驱动程序框架 (WDF) 提供了完成 I/O 请求的三个方法：

-   [**WdfRequestComplete**](https://msdn.microsoft.com/library/windows/hardware/ff549945)
-   [**WdfRequestCompleteWithInformation**](https://msdn.microsoft.com/library/windows/hardware/ff549948)
-   [**WdfRequestCompleteWithPriorityBoost** ](https://msdn.microsoft.com/library/windows/hardware/ff549949) (仅适用于 KMDF)

有关使用这些方法的信息，请参阅[完成 I/O 请求](completing-i-o-requests.md)。

 

 




