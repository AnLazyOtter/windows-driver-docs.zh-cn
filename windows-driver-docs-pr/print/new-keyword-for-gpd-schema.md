---
title: GPD 架构的新关键字
description: GPD 架构的新关键字
ms.assetid: 4814d019-0556-4e5a-8c55-c05454bafbd3
keywords:
- 根级别的关键字 WDK 打印机自动配置
- GPD 文件 WDK GDL 扩展，关键字
- 关键字 WDK 打印机自动配置
- 框中自动配置支持 WDK 打印机，关键字
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3e10528d9b1ace6b2eb3d728973a12c823f6a05f
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63324279"
---
# <a name="new-keyword-for-gpd-schema"></a>GPD 架构的新关键字


从 Windows Vista 开始，你应将添加一个新的根级别关键字到 GPD 文件指向中 GPD GDL 文件\* **BidiQueryFile**，这将标识包含 bidi 映射信息的 GDL 文件，是必需的自动配置。 如果缺少关键字，则自动配置不需要调用 GDL 分析器或达到文件系统中再次以搜索 GDL 文件。

如果你正在编写基于 Unidrv 的驱动程序，必须使用单独 GDL 引用的文件，驱动程序的主 GPD 文件直接通过\* **BidiQueryFile**关键字。

 

 




