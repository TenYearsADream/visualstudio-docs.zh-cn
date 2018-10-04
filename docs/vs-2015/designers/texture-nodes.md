---
title: 纹理节点 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05bf4ecfcdd41815345c9f8ed6a5293723af799d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47481978"
---
# <a name="texture-nodes"></a>纹理节点
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[纹理节点](https://docs.microsoft.com/visualstudio/designers/texture-nodes)。  
  
在着色器设计器中，纹理节点采集不同的纹理类型和几何图形样本，并生成或转换纹理坐标。 纹理提供对象的颜色和照明细节。  
  
## <a name="texture-node-reference"></a>纹理节点引用  
  
|节点|详细信息|属性|  
|----------|-------------|----------------|  
|**立方体贴图样本**|从立方体贴图中采集指定坐标处的颜色样本。<br /><br /> 可使用立方体贴图提供反射效果的颜色细节，或应用到其纹理失真程度低于 2-D 纹理的球形对象。<br /><br /> **输入：**<br /><br /> `UVW`: `float3`<br /> 一个矢量，指定在纹理立方体上采样的位置。 在采样位置处，此矢量与该立方体相交。<br /><br /> **输出：**<br /><br /> `Output`: `float4`<br /> 颜色样本。|**纹理**<br /> 与采样器关联的纹理寄存器。|  
|**法线贴图样本**|从 2-D 法线贴图中采集指定坐标处的法线样本<br /><br /> 可使用法线贴图模拟对象图面上其他几何细节的外观。 法线贴图包含表示单位矢量的打包数据，而不包含颜色数据<br /><br /> **输入：**<br /><br /> `UV`: `float2`<br /> 采样位置的坐标。<br /><br /> **输出：**<br /><br /> `Output`: `float3`<br /> 法线样本。|**坐标轴调整**<br /> 用于调整法线贴图样本旋向性的系数。<br /><br /> **纹理**<br /> 与采样器关联的纹理寄存器。|  
|**平移 UV**|根据时间平移指定的纹理坐标。<br /><br /> 可以将此用于在对象图面间移动纹理或法线贴图。<br /><br /> **输入：**<br /><br /> `UV`: `float2`<br /> 要平移的坐标。<br /><br /> `Time`: `float`<br /> 要进行平移的时长，以秒为单位。<br /><br /> **输出：**<br /><br /> `Output`: `float2`<br /> 平移后的坐标。|**速度 X**<br /> 每秒沿 x 轴平移的纹素数。<br /><br /> **速度 Y**<br /> 每秒沿 y 轴平移的纹素数。|  
|**视差 UV**|根据高度和视角将指定纹理坐标移位。<br /><br /> 这样创建的效果被称为*视差映射*，或者虚拟的偏移量映射。 可将此用于在平面图面上创建深度错觉。<br /><br /> **输入：**<br /><br /> `UV`: `float2`<br /> 要移位的坐标。<br /><br /> `Height`: `float`<br /> 与 `UV` 坐标关联的 heightmap 值。<br /><br /> **输出：**<br /><br /> `Output`: `float2`<br /> 移位后的坐标。|**深度平面**<br /> 视差效果的参考深度。 默认情况下，该值为 0.5。 减小此值会提升纹理；增加此值会将纹理降到平面。<br /><br /> **深度数值范围**<br /> 视差效果的数值范围。 这在一定程度上断言视深。 典型值介于 0.02 到 0.1 之间。|  
|**旋转 UV**|根据时间，围绕中心点旋转指定的纹理坐标。<br /><br /> 可以将此用于在对象图面上旋转纹理或法线贴图。<br /><br /> **输入：**<br /><br /> `UV`: `float2`<br /> 要旋转的坐标。<br /><br /> `Time`: `float`<br /> 要进行平移的时长，以秒为单位。<br /><br /> **输出：**<br /><br /> `Output`: `float2`<br /> 旋转后的坐标。|**中心点 X**<br /> 定义旋转中心的 x 坐标。<br /><br /> **中心点 Y**<br /> 定义旋转中心的 y 坐标。<br /><br /> **速度**<br /> 纹理每秒旋转的角度(弧度形式)。|  
|**纹理坐标**|当前像素的纹理坐标。<br /><br /> 通过在附近顶点的纹理坐标属性之间插值，决定纹理坐标。 可以将此视为当前像素在纹理空间中的位置。<br /><br /> **输出：**<br /><br /> `Output`: `float2`<br /> 纹理坐标。|无|  
|**纹理维度**|输出 2-D 纹理贴图的宽度和高度。<br /><br /> 可以使用纹理维度考虑着色器中纹理的宽度和高度。<br /><br /> **输出：**<br /><br /> `Output`: `float2`<br /> 纹理的宽度和高度，表示为一个矢量。 宽度存储在矢量的第一个元素中。 高度存储在第二个元素中。|**纹理**<br /> 与纹理维度关联的纹理寄存器。|  
|**纹素增量**|输出 2-D 纹理贴图纹素之间的增量（距离）。<br /><br /> 可以使用纹素增量对着色器中的相邻纹素值进行采样。<br /><br /> **输出：**<br /><br /> `Output`: `float2`<br /> （沿对角线正方向移动的）从某纹素到下一纹素的增量（距离），表示为标准化纹理空间中的矢量。 可以通过有选择地忽略或否定增量的 U 或 V 坐标，获取所有相邻纹素的位置。|**纹理**<br /> 与纹素增量关联的纹理寄存器。|  
|**纹理样本**|从 2-D 纹理贴图中采集指定坐标处的颜色样本。<br /><br /> 可使用纹理贴图提供对象图面的颜色细节。<br /><br /> **输入：**<br /><br /> `UV`: `float2`<br /> 采样位置的坐标。<br /><br /> **输出：**<br /><br /> `Output`: `float4`<br /> 颜色样本。|**纹理**<br /> 与采样器关联的纹理寄存器。|


