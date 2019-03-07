---
title: WS 发现移动打印支持
description: WS 发现移动打印支持
ms.assetid: 788E2A1C-FBE9-40CD-A3EB-14A2DE266A2C
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 70089971f168209eedfa79a3fd4507ebfe0154a4
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56540757"
---
# <a name="ws-discovery-mobile-printing-support"></a>WS 发现移动打印支持


支持从 Windows 10 移动版的打印设备必须将 MobilePrinter 类别添加到其 Ws-discovery ThisModel 响应，如下面的示例中所示：

```xml
<soap:Envelope
    xmlns:soap="http://www.w3.org/2003/05/soap-envelope"
    xmlns:wsa="http://schemas.xmlsoap.org/ws/2004/08/addressing"
    xmlns:wsdisco="http://schemas.xmlsoap.org/ws/2005/04/discovery"
    xmlns:wsx="http://schemas.xmlsoap.org/ws/2004/09/mex"
    xmlns:wsd="http://schemas.xmlsoap.org/ws/2006/02/devprof"
    xmlns:pnpx="http://schemas.microsoft.com/windows/pnpx/2005/10"> 

    <soap:Header>
        <!-- Place SOAP header information here.-->
    </soap:Header>   

    <soap:Body>
        <wsx:Metadata>
            <wsx:MetadataSection
                Dialect="http://schemas.xmlsoap.org/ws/2005/05/devprof/ThisDevice">
                <wsd:ThisDevice>
                    <!-- Place ThisDevice metadata here.-->
                </wsd:ThisDevice>
            </wsx:MetadataSection>
                
           <wsx:MetadataSection
                Dialect="http://schemas.xmlsoap.org/ws/2005/05/devprof/ThisModel">
                <wsd:ThisModel>
                    <!-- Place ThisModel metadata here.-->              
                    <pnpx:DeviceCategory>
                        <!-- This device is in the Printers category -->
                        Printers Scanners MobilePrinter
                   </pnpx:DeviceCategory>   
                </wsd:ThisModel>
            </wsx:MetadataSection>  

            <wsx:MetadataSection
                Dialect="http://schemas.xmlsoap.org/ws/2005/05/devprof/Relationship">
                <wsd:Relationship
                    Type="http://schemas.xmlsoap.org/ws/2005/05/devprof/host">

                    <wsd:Hosted>
                        <!-- Place Hosted metadata for the 
                             first service here.-->
                        <pnpx:HardwareId>
                            <!-- Place the Hardware ID for the first service here.-->
                            PnPX_SampleService1_HWID    
                        </pnpx:HardwareId>
                        <pnpx:CompatibleId>
                            <!-- Place the Compatible ID for the first service here.-->
                            PnPX_SampleService1_CPID    
                        </pnpx:CompatibleId>
                    </wsd:Hosted>
                                                
                </wsd:Relationship>
            </wsx:MetadataSection>

        </wsx:Metadata>
    </soap:Body>
</soap:Envelope>
```

下表提供了有关 MobilePrinter 类别关键字的其他信息：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>常量/值</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PNPX_DEVICECATEGORY_PRINTER_MOBILE</p>
<p>L&quot;MobilePrinter&quot;</p></td>
<td><p>MobilePrinter 类别</p>
<p>关键字：打印机</p></td>
</tr>
</tbody>
</table>

 

有关如何将设备类别添加到 WS 发现元数据交换的详细信息，请参阅[PNP-X 的规范](https://go.microsoft.com/fwlink/p/?linkid=509797)。

 

 



