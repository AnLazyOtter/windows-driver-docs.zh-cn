---
title: 电源管理
description: 电源管理
ms.assetid: b47ed463-2292-419a-af16-196382dbd3f1
keywords:
- 电源管理 WDK 打印机
- 紧急关机 WDK 打印机
- 关闭电源管理 WDK 打印机
- 备用测试 WDK 打印机
- 休眠测试 WDK 打印机
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: fc29214273eb14b21fd07c044a445cecccf427f9
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56533925"
---
# <a name="power-management"></a>电源管理


一些最常见的端口连接的设备故障发生时通过各种睡眠状态并重新打开系统和设备无法正确设置设备的电源状态，或从各种设备的电源状态返回。 系统应始终其行为就好像它已启动从完全电源已关闭状态 （"冷启动"）。 是唯一的输入或从休眠状态唤醒的特殊行为很可能是一个 bug。

遵循这些基本规则，以确保你的设备正常工作。

1.  设备、 端口和其驱动程序不应阻止或防止系统进入睡眠状态。

2.  进行中的打印作业不应阻止的请求进入低功率状态。

3.  当系统从睡眠状态中唤醒时，低功率状态启动时已在进行任何打印作业应正常恢复。

4.  紧急关机请求将重写任何尝试都能阻止电源状态的更改。

有关详细信息，请参阅[系统的电源状态](https://msdn.microsoft.com/library/windows/hardware/ff564571)WDK 文档中并[系统电源状态](https://go.microsoft.com/fwlink/p/?linkid=51899)Microsoft Windows SDK 文档中。

### <a name="testing-port-connected-devices-across-various-power-states"></a>跨不同的电源状态，测试端口连接的设备

若要开始测试设备之前和之后各种电源状态，请首先验证设备的基线[插](https://msdn.microsoft.com/library/windows/hardware/ff547125)(PnP) 功能。 接下来，验证你的测试环境，可以输入并从所有的电源状态唤醒。

使用一个在设备连接并已正确安装，测试，其行为之前和之后到 S5 每个电源状态 S0，如下所示：

-   **备用测试 (S1-S3)**
    1.  输入和从随附的设备待机状态和正在进行中的作业唤醒。 系统应正常进入每种睡眠和唤醒状态。
    2.  验证在设备正常同时在和后进入睡眠状态。 重复相同的测试，而无需安装的设备。
    3.  请尝试从待机状态唤醒后安装设备。 设备应已成功安装。
    4.  验证输入，以及与正在进行中的打印作业从待机状态唤醒。 正在进行中的作业应恢复时唤醒。
    5.  验证，可以取消、 恢复，并输入并从待机状态唤醒后重新启动该作业。
    6.  将设备置于每个错误状态中所述[设备的错误状态](device-error-states.md)。 验证，可以取消、 恢复，并输入并从待机状态唤醒后重新启动该作业。
-   **休眠测试 (S4)**
    1.  输入并唤醒从休眠状态中随附的设备和正在进行中的作业。 系统应正常进入每种睡眠和唤醒状态。
    2.  验证在设备正常同时在和后进入睡眠状态。 重复相同的测试，而无需安装的设备。
    3.  请尝试从休眠状态唤醒后安装设备。 设备应已成功安装。
    4.  验证输入并唤醒从休眠状态与正在进行中的打印作业。 正在进行中的作业应恢复时唤醒。
    5.  将设备置于每个错误状态中所述[设备的错误状态](device-error-states.md)。 验证可以取消、 恢复，并且在输入，然后从休眠状态唤醒后重新启动作业。
-   **Shutdown/Restart (S5)**
    1.  连接设备和任何作业正在进行时关闭系统。 系统应正常关闭。
    2.  验证是否在设备正常同时之前和之后的系统关闭。 重复相同的测试，而无需安装的设备。
    3.  请尝试安装设备后关闭的情况下，然后重新启动系统。
    4.  关闭并重新启动打印作业的系统，正在进行中。 正在进行中的作业应在重新启动时恢复。
    5.  将设备置于每个错误状态中所述[设备的错误状态](device-error-states.md)。 验证，可以取消、 恢复，并返回从系统关闭或重新启动后重新启动该作业。 处于错误状态的打印作业应保留在队列中通过关闭或重新启动，并关闭或重新启动后清除错误状态后，应继续打印作业。
-   **紧急关机**
    1.  计算机可以是电源的任何上述活动状态 (S0-S4) 紧急关机事件时可以请求 （例如，如果已达到电池电量严重短缺级别） 中。 验证是否在设备正常同时之前和之后的紧急关机事件。 重复相同的测试，而无需安装的设备。
    2.  请尝试在紧急关机事件之后安装设备。
    3.  测试中的设备正在使用紧急关机事件启动的电源管理器，且设备驱动程序不能阻止睡眠状态的条件。
    4.  与打印作业正在进行中，启动紧急关机事件。 系统唤醒时，应重新启动打印作业并将其恢复正常。
    5.  将设备置于每个错误状态中所述[设备的错误状态](device-error-states.md)。 验证，可以取消、 恢复，并返回从紧急关机事件后重新启动该作业。 处于错误状态的打印作业应保留在队列中通过关闭或重新启动，并关闭或重新启动后清除错误状态后，应继续打印作业。
    6.  使用设备安装和空闲**电源选项**启动应用程序，从控制面板中，获取系统睡眠状态。 验证系统在给定时间进入相应的睡眠状态。 重复此测试，而无需设备安装，并验证系统唤醒后，可以安装设备。

 

 



