---
title: 编写网络迁移 DLL
description: 编写网络迁移 DLL
ms.assetid: a6a9e57a-cc39-4cdf-a374-4791ddd4a5da
keywords:
- 网络迁移 DLL WDK
- 网络组件升级，WDK，网络迁移 DLL
- 升级网络组件 WDK，DLL 的网络迁移
- 迁移 DLL WDK 网络
- 编写网络迁移 DLL
- Dll WDK 网络迁移
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0d42efa3a8713534c008ac27c81ec0b69449476f
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67378612"
---
# <a name="writing-a-network-migration-dll"></a>编写网络迁移 DLL





**请注意**  供应商提供网络升级不支持在 Microsoft Windows XP (SP1 和更高版本)，Microsoft Windows Server 2003 和更高版本操作系统。

 

网络迁移 DLL 将从 Microsoft Windows NT 3.51 或 Windows NT 4.0 到 Windows 2000 或更高版本迁移一个或多个网络组件的参数值。

网络迁移 DLL 必须：

-   **加载在升级前操作系统 （Windows NT 3.51 或 Windows 4.0）**

    DLL 不能调用任何函数特定于 Windows 2000 或更高版本，或使用特定于 Windows 2000 或更高版本的任何功能。 如果在 postupgrade （GUI 模式） 阶段中运行该 DLL，必须还将其加载在 Windows 2000 和更高版本操作系统中。

-   **导出** [ **PreUpgradeInitialize**](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff562439(v=vs.85))**并**[**DoPreUpgradeProcessing** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff545634(v=vs.85))**函数**

    如果在 GUI 模式阶段中运行该 DLL，必须将导出[ **PostUpgradeInitialize** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff562410(v=vs.85))并[ **DoPostUpgradeProcessing** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff545629(v=vs.85))函数，为嗯。

-   **Winnt32 阶段做出任何不可逆更改**

    DLL 必须不进行任何不可逆更改，如删除文件或修改注册表项，在此阶段中，因为用户可以取消的网络组件或操作系统升级。 但是，该 DLL 可以修改 NetSetup 对的调用中指定其临时工作目录中的文件**PreUpgradeInitialize**。

 

 





