---
title: 方向传感器数据字段
description: 本主题提供有关特定于方向传感器的数据字段的信息。
ms.assetid: 4B1FA56E-6956-4BC9-B929-3D78EF933057
ms.date: 07/20/2018
ms.localizationpriority: medium
ms.openlocfilehash: 287a1a5fbaad25c572c9f54fdbc3999abbc26164
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72841693"
---
# <a name="orientation-sensor-data-fields"></a>方向传感器数据字段


本主题提供有关特定于方向传感器的数据字段的信息。

下表显示了数据字段。 有关 "类型" 列中显示的类型的详细信息，请参阅[PROPVARIANT 结构](https://go.microsoft.com/fwlink/p/?linkid=313395)。

|属性键|在任务栏的搜索框中键入|必需/可选|说明/注释|
|---|---|---|---|
|PKEY_SensorData_QuaternionW|VT_R4|必需|旋转轴向量的实系数（相对于复数的虚部）。|
|PKEY_SensorData_QuaternionX|VT_R4|必需|旋转轴向量的 X 分量。|
|PKEY_SensorData_QuaternionY|VT_R4|必需|旋转轴向量的 Y 分量。|
|PKEY_SensorData_QuaternionZ|VT_R4|必需|旋转轴向量的 Z 分量。|
|PKEY_SensorData_MagnetometerAccuracy|VT_UI4|必需|磁力仪传感器的准确性。 有关有效值的详细信息，请参阅[MAGNETOMETER_ACCURACY](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorsdef/ne-sensorsdef-magnetometer_accuracy)。|
|PKEY_SensorData_DeclinationAngle_Degrees|VT_R4|可选|用于从地球上北部的赤纬中推断出 true 的磁性。 如果不支持，类扩展将计算此值。|
|PKEY_SensorData_LinearAccelerationX_Gs|VT_R4|可选|G 中的 X 轴线性加速度|
|PKEY_SensorData_LinearAccelerationY_Gs|VT_R4|可选|G 中的 Y 轴线性加速度|
|PKEY_SensorData_LinearAccelerationZ_Gs|VT_R4|可选|G 的 Z 轴线性加速度|
|PKEY_SensorData_CorrectedAngularVelocityX_DegreesPerSecond|VT_R4|可选|Gyrometric X 轴速度，以度/秒为单位。|
|PKEY_SensorData_CorrectedAngularVelocityY_DegreesPerSecond|VT_R4|可选|Gyrometric Y 轴速度，以度/秒为单位。|
|PKEY_SensorData_CorrectedAngularVelocityZ_DegreesPerSecond|VT_R4|可选|Gyrometric Z 轴速度，以度/秒为单位。|


## <a name="related-topics"></a>相关主题


[MSDN PROPVARIANT 结构](https://go.microsoft.com/fwlink/p/?linkid=313395)






