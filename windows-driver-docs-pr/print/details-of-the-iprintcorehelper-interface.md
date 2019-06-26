---
title: IPrintCoreHelper 接口详细信息
description: IPrintCoreHelper 接口详细信息
ms.assetid: df736ca2-425e-4fc8-bdcb-bdbd5caa3e22
keywords:
- IPrintCoreHelper
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e8d4904bb4c27f071dd8290bf4c9fd6b2bc83aec
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63352989"
---
# <a name="details-of-the-iprintcorehelper-interface"></a>IPrintCoreHelper 接口详细信息


**IPrintCoreHelper** Pscript5 UI 替换接口上大致基于接口。 但是，有两种方法在其中**IPrintCoreHelper**接口是本质上不同于原始 Pscript5 帮助程序接口。

-   **IPrintCoreHelper**接口没有**QuerySimulatedCapabilities**方法。 相反， **IPrintCoreHelper**接口定义完善且可识别的方式将模拟的功能映射到常规功能和选项的列表。

-   在中**IPrintCoreHelper**接口，调用方要求传入[ **DEVMODEW** ](https://msdn.microsoft.com/library/windows/hardware/ff552837)结构，而不是[ **OEMUIOBJ**](https://msdn.microsoft.com/library/windows/hardware/ff559571)结构。

如果您使用**IPrintCoreHelper**接口或从其继承的接口，应考虑以下几点：

-   有关**IPrintCoreHelper**接口，用于字符串**GetOption**或**SetOptions**方法都是 GPD 字符串不 GDL 字符串，因此功能和在中定义的选项\#ifdef GDL 块不是可用于帮助程序接口方法。

-   如果上一个方法**IPrintCoreHelper**接口 （和其子接口） 具有一个输出参数和 OUT 参数如果该方法将失败，将保留时调用该方法的值。

-   内存模型**IPrintCoreHelper**接口是略有不同于以前 Pscript5 接口。 调用方不负责清理返回从帮助器接口，传递的参数，调用方不需要分配缓冲区中传递。 核心驱动程序处理这些类型的内存管理。

本部分提供了以下主题：

[IPrintCoreHelperUni 接口的详细信息](details-of-the-iprintcorehelperuni-interface.md)

[IPrintCoreHelperPS 接口的详细信息](details-of-the-iprintcorehelperps-interface.md)

 

 



