---
title: 使用 16550 UART 兼容接口安装串行设备
description: 安装使用 16550 UART 兼容接口的串行设备
ms.assetid: d80db651-b890-44dc-98ad-32e72e244d8c
keywords:
- 串行驱动程序 WDK，16550 UART 兼容接口
- 通用的异步接收方发射机 WDK 串行设备
- UART WDK 串行设备
- 16550 UART 兼容接口 WDK 串行设备
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e335fb41be0169cd752d0fb924dc2cab3741c1bc
ms.sourcegitcommit: 6a0636c33e28ce2a9a742bae20610f0f3435262c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65836361"
---
# <a name="installing-serial-devices-that-use-a-16550-uart-compatible-interface"></a>安装使用 16550 UART 兼容接口的串行设备

若要安装即插即用设备使用序列作为较低级别设备筛选器驱动程序，请执行以下操作：

- 指定序列作为设备的 INF 文件中的较低级别设备筛选器驱动程序--请参阅[安装筛选器驱动程序](https://msdn.microsoft.com/library/windows/hardware/ff547595)。

- 设置**SerialSkipExternalNaming**条目值，该设备为非零值-请参阅[即插即用和播放串行设备的注册表设置](registry-settings-for-a-plug-and-play-serial-device.md)。