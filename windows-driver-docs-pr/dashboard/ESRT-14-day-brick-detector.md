---
title: 已成功安装固件但 14 天内未报告任何遥测数据的计算机的百分比
description: 该度量将 28 天滑动窗口中的遥测数据聚合为在 14 天内未报告任何遥测数据的计算机数与成功安装固件的计算机数的比率
ms.topic: article
ms.date: 10/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: 09120b2e914c95f7c0d563378804b9833e3d6494
ms.sourcegitcommit: 07b2926c15f4782e1914e8d3cf6c5c511a3a6111
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2019
ms.locfileid: "74097501"
---
# <a name="percent-of-machines-that-successfully-installed-firmware-and-not-heartbeat-within-14-days"></a>已成功安装固件但 14 天内未报告任何遥测数据的计算机的百分比

## <a name="description"></a>描述

已成功安装固件但 14 天未报告任何遥测数据的计算机的百分比。   

该度量将 28 天滑动窗口中的遥测数据聚合为在 14 天内未报告任何遥测数据的计算机数与成功安装固件的计算机数的比率

这用于检测可能受限的计算机。 

## <a name="measure-attributes"></a>度量属性

|属性|值|
|----|----|
|受众 |零售和预览体验成员|
|时间段 |28 天滑动窗口|
|度量标准 |计算机的聚合|
|最小实例数 |250|
|通过标准 |> 50%|
|度量 ID |23095170|

## <a name="calculation"></a>计算

在 14 天内未报告任何遥测数据的计算机数/

成功安装固件的计算机数（以度量 20116729 为标准）

