---
ms.assetid: AE3E003F-BDEC-438B-A80A-3CE1675B369C
description: 使用 Microsoft Store 分析 API 中的此方法，可获取给定日期范围和其他可选筛选器的聚合硬件错误报告数据。 此方法仅适用于 OEM。
title: 获取 OEM 硬件错误报告数据
ms.date: 06/04/2018
ms.topic: article
keywords: windows 10, uwp, Microsoft Store 服务, Microsoft Store 分析 API, 错误
ms.localizationpriority: medium
ms.openlocfilehash: 1dfc92087338ba6c94fb37d26bbda460e4568eed
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56518421"
---
# <a name="get-oem-hardware-error-reporting-data"></a>获取 OEM 硬件错误报告数据

> [!IMPORTANT]
> 本主题包含已弃用的材料。 它介绍了用于收集驱动程序提交失败相关数据的旧方法。 它仅为支持旧版提供。
>
> 请改为参考这些更新的主题：
>
> - [计划自定义报告以获取驱动程序失败详细信息](schedule-custom-reports-for-driver-failure-details.md)
> - [创建新的报告模板](create-a-new-report-template.md)
> - [计划新报告](schedule-a-new-report.md)
> - [获取报告数据](get-report-data.md)
> - [下载失败的 Cab](download-failure-cabs.md)

使用 Microsoft Store 分析 API 中的此方法，可获取给定日期范围和其他可选筛选器的 OEM 硬件错误聚合报告数据。 可以使用[获取 OEM 硬件错误的详细信息](get-details-for-an-oem-hardware-error.md)方法检索其他错误信息。

> [!NOTE]
> 此方法仅可供属于 [Windows 硬件开发人员中心计划](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard)的开发者帐户使用。

## <a name="prerequisites"></a>必备条件

若要使用此方法，首先需要执行以下操作：

* 如果尚未开始操作，请先完成 Microsoft Store 分析 API 的所有[先决条件](https://docs.microsoft.com/windows/uwp/monetize/access-analytics-data-using-windows-store-services#prerequisites)。
* [获取 Azure AD 访问令牌](https://docs.microsoft.com/windows/uwp/monetize/access-analytics-data-using-windows-store-services#obtain-an-azure-ad-access-token)，以供在此方法的请求标头中使用。 获取访问令牌后，在它到期前，你有 60 分钟的使用时间。 该令牌到期后，可以获取新的令牌。

## <a name="request"></a>请求


### <a name="request-syntax"></a>请求语法

| 方法 | 请求 URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | `https://manage.devcenter.microsoft.com/v1.0/my/analytics/hardware/failurehits` |

<span/> 

### <a name="request-header"></a>请求头

| 标头        | 在任务栏的搜索框中键入   | 描述                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| 授权 | 字符串 | 必需。 Azure AD 访问令牌的格式为 **Bearer** &lt;token&gt;。 |

<span/> 

### <a name="request-parameters"></a>请求参数

| 参数        | 在任务栏的搜索框中键入   |  描述      |  必需  
|---------------|--------|---------------|------|
| startDate | 日期 | 要检索的错误报告数据日期范围中的开始日期。 默认值为当前日期。 |  否  |
| endDate | 日期 | 要检索的错误报告数据日期范围中的结束日期。 默认值为当前日期。 |  否  |
| top | int | 要在请求中返回的数据行数。 如果未指定，最大值和默认值为 10000。 当查询中存在多行数据时，响应正文中包含的下一个链接可用于请求下一页数据。 |  否  |
| skip | int | 要在查询中跳过的行数。 使用此参数可以浏览较大的数据集。 例如，top=10000 和 skip=0，将检索前 10000 行数据；top=10000 和 skip=10000，将检索之后的 10000 行数据，依此类推。 |  否  |
| filter |字符串  | 在响应中筛选行的一条或多条语句。 每条语句包含的响应正文中的字段名称和值使用 **eq** 或 **ne** 运算符进行关联，并且语句可以使用 **and** 或 **or** 进行组合。 *filter* 参数中的字符串值必须使用单引号括起来。 可以指定的字段如下所示：<p/><ul><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>moduleName</strong></li><li><strong>moduleVersion</strong></li><li><strong>mode</strong></li><li><strong>architecture</strong></li><li><strong>model</strong></li><li><strong>baseboard</strong></li><li><strong>modelFamily</strong></li><li><strong>flightRing</strong></li></ul> | 否   |
| aggregationLevel | 字符串 | 指定用于检索聚合数据的时间范围。 可以是以下字符串之一：<strong>day</strong>、<strong>week</strong> 或 <strong>month</strong>。 如果未指定，默认值为 <strong>day</strong>。 如果指定 <strong>week</strong> 或 <strong>month</strong>，则 <em>failureName</em> 和 <em>failureHash</em> 值限制为 1000 个存储桶。 | 否 |
| orderby | 字符串 | 对结果数据值进行排序的语句。 语法是 <em>orderby=field [order],field [order],...</em>。可以指定响应正文中的以下字段：<p/><ul><li><strong>date</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>moduleName</strong></li><li><strong>moduleVersion</strong></li><li><strong>mode</strong></li><li><strong>architecture</strong></li><li><strong>model</strong></li><li><strong>baseboard</strong></li><li><strong>modelFamily</strong></li><li><strong>flightRing</strong></li></ul><p><em>order</em> 参数是可选的，可以是 <strong>asc</strong> 或 <strong>desc</strong>，用于指定每个字段的升序或降序排列。 默认值为 <strong>asc</strong>。</p><p>下面是一个 <em>orderby</em> 字符串的示例：<em>orderby=date,market</em></p> |  否  |
| groupby | 字符串 | 仅将数据聚合应用于指定字段的语句。 可以指定响应正文中的以下字段：<p/><ul><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>moduleName</strong></li><li><strong>moduleVersion</strong></li><li><strong>mode</strong></li><li><strong>architecture</strong></li><li><strong>model</strong></li><li><strong>baseboard</strong></li><li><strong>modelFamily</strong></li><li><strong>flightRing</strong></li></ul><p>返回的数据行会包含 <em>groupby</em> 参数中指定的字段，以及以下字段：</p><ul><li><strong>date</strong></li><li><strong>eventCount</strong></li></ul><p><em>groupby</em> 参数可以与 <em>aggregationLevel</em> 参数结合使用。 例如：<em>&amp;groupby=failureName,market&amp;aggregationLevel=week</em></p></p> |  否  |

<span/>


### <a name="request-example"></a>请求示例

以下示例演示用于获取 OEM 硬件错误报告数据的多个请求。

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/hardware/failurehits?startDate=1/1/2015&endDate=2/1/2015&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/hardware/failurehits?startDate=8/1/2015&endDate=8/31/2015&skip=0&filter=market eq 'US' and deviceType eq 'PC' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>响应


### <a name="response-body"></a>响应正文

| 值      | 在任务栏的搜索框中键入    | 描述     |
|------------|---------|--------------|
| 值      | 数组   | 包含聚合错误报告数据的对象数组。 有关每个对象中的数据的详细信息，请参阅下表。     |
| @nextLink  | 字符串  | 如果存在数据的其他页，此字符串中包含的 URI 可用于请求下一页数据。 例如，当请求的 **top** 参数设置为 10000，但查询的错误超过 10000 行时，就会返回此值。 |
| TotalCount | 整数 | 查询的数据结果中的行总数。     |

<span/>

*Value* 数组中的元素包含以下值。

| 值           | 在任务栏的搜索框中键入    | 描述        |
|-----------------|---------|---------------------|
| 日期            | 字符串  | 错误数据的日期范围内的第一个日期。 如果请求指定了某一天，此值就是该日期。 如果请求指定了一周、月或其他日期范围，此值是该日期范围内的第一个日期。 |
| sellerId   | 字符串  | 与此开发者帐户关联的经销商 ID 值（此值与开发人员中心帐户设置中的**经销商 ID** 值匹配）。 |
| failureName     | 字符串  | 故障的名称，它由四个部分组成：一个或多个问题类、异常/bug 检查代码、发生故障的映像/驱动程序的名称和相关的函数名称。  |
| failureHash     | 字符串  | 错误的唯一标识符。   |
| symbol          | 字符串  | 分配给该错误的符号。 |
| osVersion       | 字符串  | 发生错误的操作系统的四部分内部版本。  |
| eventType       | 字符串  | 发生的错误的类型。       |
| market          | 字符串  | 设备市场的 ISO 3166 国家/地区代码。   |
| deviceType      | 字符串  | 以下字符串之一，用于指定发生错误的设备的类型：<p/><ul><li><strong>PC</strong></li><li><strong>Phone</strong></li><li><strong>Console</strong></li><li><strong>IoT</strong></li><li><strong>Holographic</strong></li><li><strong>Unknown</strong></li></ul>    |
| moduleName     | 字符串  | 与此错误相关联的模块的唯一名称。      |
| moduleVersion  | 字符串  | 与此错误相关联的模块的版本。   |
| architecture | 字符串 |  发生错误的设备的体系结构。  |
| 模型 | 字符串 | 发生错误的设备型号的名称。 |
| baseboard | 字符串 | 发生错误的设备主板的名称。 |
| modelFamily | 字符串 | 发生错误的设备型号系列的名称。 |
| flightRing | 字符串 | 发生错误的操作系统外部测试版的名称。 |
| mode | 字符串 | 此值始终是 *kernel*。 |
| eventCount      | 整数 | 归因于指定聚合级别的该错误的事件数目。      |

<span/> 

### <a name="response-example"></a>响应示例

以下示例举例说明此请求的 JSON 响应正文。

```json
{
  "Value": [
    {
      "date": "2017-02-18",
      "sellerId": "14313740",
      "mode": "Kernel",
      "failureName": "AV_wfplwfs!L2802_3ParseMacHeader",
      "failureHash": "f060c0b6-fbe6-463f-a9f1-b7ebc1cc722f",
      "symbol": "wfplwfs!L2802_3ParseMacHeader",
      "osVersion": "10.0.14393.0",
      "eventType": "System crash",
      "market": "US",
      "deviceType": "PC",
      "moduleName": "wfplwfs.sys",
      "moduleVersion": "10.0.14393.0",
      "architecture": "x64",
      "model": "Unknown",
      "baseboard": "Unknown",
      "modelFamily": "ContosoPad",
      "flightRing": "Windows 10 Retail",
      "eventCount": 2.0
    }]
}
```

## <a name="related-topics"></a>相关主题

- [获取 OEM 硬件错误的详细信息](get-details-for-an-oem-hardware-error.md)

- [下载 OEM 硬件错误的 CAB 文件](download-the-cab-file-for-an-oem-hardware-error.md)
