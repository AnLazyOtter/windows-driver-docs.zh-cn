---
title: PnPUtil 示例
description: PnPUtil 示例
ms.assetid: 4805edb9-e4f8-441d-a7f4-0c962ddeae4e
ms.date: 01/31/2018
ms.localizationpriority: medium
ms.openlocfilehash: 3d9d401ff31e804b33a9abc300897e5179c4fc61
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63345804"
---
# <a name="pnputil-examples"></a>PnPUtil 示例

本主题提供了有关如何使用 PnPUtil 工具的示例。

```
  pnputil /add-driver x:\driver.inf       <- Add driver package
  pnputil /add-driver c:\oem\*.inf        <- Add multiple driver packages
  pnputil /add-driver device.inf /install <- Add and install driver package
  pnputil /enum-drivers                   <- Enumerate OEM driver packages
  pnputil /delete-driver oem0.inf         <- Delete driver package
  pnputil /delete-driver oem1.inf /force  <- Force delete driver package
  pnputil /export-driver oem6.inf .       <- Export driver package
  pnputil /export-driver * c:\backup      <- Export all driver packages
```

 

 





