---
title: "范围标记 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: e476a1d0f3af8a0a0c9b9159d710fc7c5680a00d
ms.contentlocale: zh-cn
ms.lasthandoff: 05/13/2017

---
# <a name="span-markers"></a>范围标记
范围标记表示应用程序一个有意义的阶段。 例如，可以用范围表示正在处理某特定工作项的时间间隔。 范围的长度表示相应的应用程序阶段的持续时间。 下图显示并发可视化工具中的一个范围：  
  
 ![并发可视化工具中的范围标记](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
并发可视化工具中的范围标记  
  
## <a name="span-category"></a>范围类别  
 范围标记可用 5 种不同的颜色显示，具体取决于其类别。 如果类别超过 5 个，则颜色将会重复。 类别可以是任意整数。 此图显示 5 种可能的颜色：  
  
 ![不同类别中的 5 个范围](~/profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
前 5 个范围类别的颜色  
  
## <a name="span-aggregation-markers"></a>范围聚合标记  
 有时，并发可视化工具中范围标记发生时间过于接近，导致无法单独绘制。 发生这种情况时，将会显示代表基础范围的灰色范围聚合标记。 当将鼠标指针放在这些图标上时，工具提示将显示所代表的基础范围数量。 若要查看范围，请放大。 如果一直放大但仍显示范围聚合标记，则可以在[标记报告](../profiling/markers-report.md)中查看基础范围标记。 此图显示范围聚合标记：  
  
 ![并发可视化工具中的聚合范围](~/profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
范围聚合标记  
  
## <a name="see-also"></a>另请参阅  
 [并发可视化工具标记](../profiling/concurrency-visualizer-markers.md)   
 [并发可视化工具 SDK](../profiling/concurrency-visualizer-sdk.md)