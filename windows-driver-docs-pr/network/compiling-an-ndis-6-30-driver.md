---
title: 编译 NDIS 6.30 驱动程序
description: 本部分介绍如何编译 NDIS 6.30 驱动程序
ms.assetid: 6CBAFAA2-7DA3-4184-B82B-AEFF61F7072C
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f286af8e981b57abb6175b5599c5ed1634a6ae92
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67379280"
---
# <a name="compiling-an-ndis-630-driver"></a>编译 NDIS 6.30 驱动程序


在 Windows 8 版本的 Windows Driver Kit (WDK) 中，驱动程序开发环境集成到 Visual Studio。 在 Visual Studio 用户界面中提供了大部分所需的编码、 构建、 测试、 调试、 部署和发布一个驱动程序的工具。 这是从早期版本的 WDK 驱动程序生命周期的各个阶段视为不同的独立工具的任务已执行的位置不同。

Windows 8 的 WDK 支持标头版本控制。 标头版本控制可确保 NDIS 6.30 驱动程序在编译时使用的合适的 NDIS 6.30 数据结构。 将以下编译器设置添加到您的驱动程序的 Visual Studio 项目：

-   微型端口驱动程序，将添加 NDIS630\_微型端口 = 1。

-   筛选器或协议驱动程序，将添加 NDIS630 = 1。

有关构建与 Windows 8 版本的 WDK 的驱动程序的信息，请参阅[构建一个驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/building-a-driver)。

有关将驱动程序的生成文件转换为 Visual Studio 项目的信息，请参阅[创建驱动程序从现有源文件](https://docs.microsoft.com/windows-hardware/drivers)。

 

 





