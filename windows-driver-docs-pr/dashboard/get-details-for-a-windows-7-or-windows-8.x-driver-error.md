---
ms.assetid: 2FBA0B73-17C6-4F25-A79D-63F2F262491A
description: 在 Microsoft Store 分析 API 中使用此方法，可获取 Windows 7 或 Windows 8.x 驱动程序错误的详细数据。 此方法仅适用于 IHV。
title: 获取 Windows 7 或 Windows 8.x 驱动程序错误的详细信息
ms.topic: article
ms.date: 08/28/2018
keywords: windows 10, uwp, Store 服务, Microsoft Store 分析 API, 错误, 详细信息
ms.localizationpriority: medium
ms.openlocfilehash: 5adb0a9c729c45d898c6491d82e20d28cd949eeb
ms.sourcegitcommit: dabd74b55ce26f2e1c99c440cea2da9ea7d8b62c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "63335072"
---
# <a name="get-details-for-a-windows-7-or-windows-8x-driver-error"></a>获取 Windows 7 或 Windows 8.x 驱动程序错误的详细信息

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

在 Microsoft Store 分析 API 中使用此方法，可以 JSON 格式获取特定 Windows 7/Windows 8.x 驱动程序错误的详细数据。 可以使用此方法之前，必须先使用[获取 Windows 7 和 Windows 8.x 驱动程序的错误报告数据](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md)方法来检索想要获取其详细信息的错误的 ID。

> [!NOTE]
> 此方法仅可供属于 [Windows 硬件开发人员中心计划](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard)的开发者帐户使用。

## <a name="prerequisites"></a>必备条件


若要使用此方法，首先需要执行以下操作：

* 完成 Microsoft Store 分析 API 的所有[先决条件](https://docs.microsoft.com/windows/uwp/monetize/access-analytics-data-using-windows-store-services#prerequisites)（如果尚未这样做）。
* [获取 Azure AD 访问令牌](https://docs.microsoft.com/windows/uwp/monetize/access-analytics-data-using-windows-store-services#obtain-an-azure-ad-access-token)，以供在此方法的请求标头中使用。 获取访问令牌后，在它到期前，你有 60 分钟的使用时间。 该令牌到期后，可以获取新的令牌。
* 获取希望获取详细信息的错误的 ID。 若要获取此 ID，请使用[获取 Windows 7 和 Windows 8.x 驱动程序的错误报告数据](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md)方法，并使用该方法的响应正文中的 **failureHash** 值。

## <a name="request"></a>请求


### <a name="request-syntax"></a>请求语法

| 方法 | 请求 URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | `https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/failuredetails` |


### <a name="request-header"></a>请求头

| 标头        | 在任务栏的搜索框中键入   | 描述                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| 授权 | 字符串 | 必需。 Azure AD 访问令牌的格式为 **Bearer** *token*&lt;&gt;。 |


### <a name="request-parameters"></a>请求参数

| 参数        | 在任务栏的搜索框中键入   |  描述      |  必需  
|---------------|--------|---------------|------|
| failureHash | 字符串 | 你希望获取详细信息的错误的唯一 ID。 若要获取感兴趣的错误的此值，请使用[获取 OEM 硬件错误报告数据](get-oem-hardware-error-reporting-data.md)方法，并使用该方法的响应正文中的 **failureHash** 值。 |  是  |
| startDate | 日期 | 要检索的详细错误数据日期范围中的开始日期。 默认值为当前日期之前 30 天。 |  否  |
| endDate | 日期 | 要检索的详细错误数据日期范围中的结束日期。 默认值为当前日期。 |  否  |
| top | int | 要在请求中返回的数据行数。 如果未指定，最大值和默认值为 10000。 当查询中存在多行数据时，响应正文中包含的下一个链接可用于请求下一页数据。 |  否  |
| skip | int | 要在查询中跳过的行数。 使用此参数可以浏览较大的数据集。 例如，top=10 和 skip=0，将检索前 10 行数据；top=10 和 skip=10，将检索之后的 10 行数据，依此类推。 |  否  |
| filter | 字符串  | 在响应中筛选行的一条或多条语句。 每条语句包含的响应正文中的字段名称和值使用 **eq** 或 **ne** 运算符进行关联，并且语句可以使用 **and** 或 **or** 进行组合。 *filter* 参数中的字符串值必须使用单引号括起来。 可以指定响应正文中的以下字段：<p/><ul><li><strong>date</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>osName</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>driverName</strong></li><li><strong>driverVersion</strong></li><li><strong>oemName</strong></li><li><strong>oemModel</strong></li><li><strong>flightRing</strong></li><li><strong>architecture</strong></li><li><strong>cabType</strong></li><li><strong>cabExpirationTime</strong></li></ul> | 否   |
| orderby | 字符串 | 对结果数据值进行排序的语句。 语法是 <em>orderby=field [order],field [order],...</em>。可以指定响应正文中的以下字段：<p/><ul><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>cabType</strong></li><li><strong>cabExpirationTime</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>osName</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>driverName</strong></li><li><strong>driverVersion</strong></li><li><strong>oemName</strong></li><li><strong>oemModel</strong></li><li><strong>flightRing</strong></li><li><strong>architecture</strong></li></ul><p><em>order</em> 参数是可选的，可以是 <strong>asc</strong> 或 <strong>desc</strong>，用于指定每个字段的升序或降序排列。 默认值为 <strong>asc</strong>。</p><p>下面是一个 <em>orderby</em> 字符串的示例：<em>orderby=date,market</em></p> |  否  |


### <a name="request-example"></a>请求示例

以下示例演示用于获取详细错误数据的多个请求。

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/failuredetails?failureHash=012e33e3-dbc9-b12f-c124-9d9810f05d8b&startDate=2016-11-05&endDate=2016-11-06&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/failuredetails?failureHash=012e33e3-dbc9-b12f-c124-9d9810f05d8b&startDate=2016-11-05&endDate=2016-11-06&top=10&skip=0&filter=market eq 'US' and deviceType eq 'PC' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>响应


### <a name="response-body"></a>响应正文

| 值      | 在任务栏的搜索框中键入    | 描述    |
|------------|---------|------------|
| 值      | 数组   | 包含详细错误数据的对象数组。 有关每个对象中的数据的详细信息，请参阅下表。          |
| @nextLink  | 字符串  | 如果存在数据的其他页，此字符串中包含的 URI 可用于请求下一页数据。 例如，当请求的 **top** 参数设置为 10，但查询的错误超过 10 行时，就会返回此值。 |
| TotalCount | 整数 | 查询的数据结果中的行总数。        |


*Value* 数组中的元素包含以下值。

| 值           | 在任务栏的搜索框中键入    | 描述     |
|-----------------|---------|----------------------------|
| 日期            | 字符串  | 错误数据的日期范围内的第一个日期。 如果请求指定了某一天，此值就是该日期。 如果请求指定了一周、月或其他日期范围，此值是该日期范围内的第一个日期。 |
| sellerId   | 字符串  | 与此开发者帐户关联的经销商 ID 值（此值与开发人员中心帐户设置中的**经销商 ID** 值匹配）。 |
| failureName     | 字符串  | 故障的名称，它由四个部分组成：一个或多个问题类、异常/bug 检查代码、发生故障的驱动程序的名称和相关的函数名称。           |
| failureHash     | 字符串  | 错误的唯一标识符。     |
| symbol     | 字符串  | 分配给该错误的符号。     |
| osVersion       | 字符串  | 发生错误的操作系统的四部分内部版本。    |
| osName       | 字符串  | 发生错误的操作系统的名称。  |
| eventType       | 字符串  | 发生的错误的类型。      |
| market          | 字符串  | 设备市场的 ISO 3166 国家/地区代码。     |
| deviceType      | 字符串  | 出现错误的设备的类型。     |
| driverName     | 字符串  | 与此错误关联的驱动程序的唯一名称。      |
| driverVersion  | 字符串  | 与此错误关联的驱动程序的版本。   |
| architecture | 字符串 |  发生错误的设备的体系结构。  |
| oemName | 字符串 | 发生错误的设备的 OEM 名称。 |
| oemModel | 字符串 | 发生错误的设备型号的名称。 |
| flightRing | 字符串 | 发生错误的操作系统外部测试版的名称。 |
| clientDeviceId | 字符串 | 出现错误的设备的 ID。 |
| cabIdHash         | 字符串  | 与此错误相关联的 CAB 文件的唯一 ID。   |
| cabType         | 字符串  | CAB 文件的类型。   |
| cabExpirationTime  | 字符串  | CAB 文件已过期且不能再下载时的日期和时间，以 ISO 8601 格式表示。   |


### <a name="response-example"></a>响应示例

以下示例举例说明此请求的 JSON 响应正文。

```json
{
  "Value": [
    {
      "sellerId": "14313740",
      "architecture": "x64",
      "cabExpirationTime": "2017-06-12 23:51:11",
      "cabIdHash": "cc1797f9-b783-44d4-b0e5-46ae7ca668bc",
      "cabType": "MINI",
      "clientDeviceId": null,
      "date": "2017-03-14 23:51:11",
      "deviceType": "PC",
      "driverName": "fastboot.sys",
      "driverVersion": "2.1.1.0",
      "failureHash": "f060c0b6-fbe6-463f-a9f1-b7ebc1cc722f",
      "failureName": "0x109_18_2_LoadImageNotify",
      "market": "US",
      "oemModel": "C-122",
      "oemName": "Contoso",
      "osName": "Windows 8.1",
      "osVersion": "6.3.9600.9600"
    }]
}
```

## <a name="related-topics"></a>相关主题

- [获取 Windows 7 和 Windows 8.x 驱动程序的错误报告数据](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md)

- [下载 Windows 7 或 Windows 8.x 驱动程序错误的 CAB 文件](download-the-cab-file-for-a-windows-7-or-windows-8.x-driver-error.md)