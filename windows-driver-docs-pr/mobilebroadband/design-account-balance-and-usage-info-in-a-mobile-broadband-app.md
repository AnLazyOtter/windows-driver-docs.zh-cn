---
title: 设计移动宽带应用中的帐户余额和使用情况信息
description: 设计移动宽带应用中的帐户余额和使用情况信息
ms.assetid: aec4e4b3-d207-4319-a134-29b4a773c3a6
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0b637f489d35a4e62032a6150fcffe358fac2cc2
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56564276"
---
# <a name="design-account-balance-and-usage-info-in-a-mobile-broadband-app"></a>设计移动宽带应用中的帐户余额和使用情况信息


用户主要使用移动宽带应用以查看帐户余额和使用情况信息。 此数据应该是应用程序的主屏幕上清晰可见。

![后付费的计划摘要](images/mb-fig1-postpaidplansummary.png)

后付费帐户相关的帐户信息包括：

-   帐户的移动电话号码

-   剩余的帐户余额

-   数据使用，漫游数据使用和剩余的使用情况

-   计费期或计划到期日期

一眼，用户可以清楚地了解多少已使用数据、 以及剩余多少数据，并在计费周期结束 （对于每月帐户）。

![預付的计划摘要](images/mb-fig2-prepaidplansummary.png)

预付帐户相关的帐户信息包括：

-   帐户的移动电话号码

-   剩余的帐户余额

-   重新充电现在按钮，可将付款页面的链接

-   使用数据磁盘大小和剩余

-   计划到期日期 （如果存在）

## <a name="span-idquicksummaryspanspan-idquicksummaryspanspan-idquicksummaryspanquick-summary"></a><span id="Quick_summary"></span><span id="quick_summary"></span><span id="QUICK_SUMMARY"></span>快速摘要


用于显示帐户信息的相应设计：

-   显示相关的帐户信息

-   显示上次更新数据时

-   使用说明，如图表和图形，以实现数据可视化效果

    **提示**  中所述，可以通过使用确定性进度栏控件，实现条形图[添加进度控件](https://msdn.microsoft.com/library/windows/apps/hh465428)。

     

-   当剩余的使用率较低时，显示链接到计划页后，可以升级计划

用于显示帐户信息的设计不完善：

-   不再显示较长的段落的旁边数据使用情况的法律免责声明。 这可以使用户从帐户使用情况部分的重点变得混乱。 相反，显示的应用程序具有完整法律免责声明的单独部分的链接。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关主题


[设计用户体验的移动宽带应用程序](designing-the-user-experience-of-a-mobile-broadband-app.md)

 

 





