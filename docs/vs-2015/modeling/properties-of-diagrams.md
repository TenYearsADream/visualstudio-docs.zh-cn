---
title: 图表属性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 287e9362162c00a5292815ebacfb8047b2a0bb7b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58937492"
---
# <a name="properties-of-diagrams"></a>图表属性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可以设置指定关系图将在生成的设计器中的显示方式的属性。 例如，您可以在关系图中指定文本的默认颜色。  
  
 有关详细信息，请参阅[如何定义特定于域的语言](../modeling/how-to-define-a-domain-specific-language.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 下表列出了关系图的属性。  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|填充颜色|关系图的填充颜色。|白色|  
|文本颜色|在关系图显示的文本的颜色。|黑色|  
|访问修饰符|类 （公共或内部） 的访问修饰符。|Public|  
|自定义特性|用于将属性添加到生成的代码类。|\<none>|  
|生成双派生|如果`True`，将生成的基类和一个分部类 （以支持通过重写自定义）。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义构造函数|如果`True`，将在源代码中提供自定义构造函数。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|继承修饰符|描述的关系图生成源代码类的继承的类型 (`none`，`abstract`或`sealed`)。|None|  
|基本关系图|此关系图的基类。|(无)|  
|名称|此关系图的名称。|当前名称|  
|命名空间|隶属于此关系图命名空间。|当前命名空间|  
|表示类|此关系图表示的根域类。|如果适用的当前根类|  
|说明|与此元素相关联的非正式说明。|\<none>|  
|公开为属性的填充颜色|如果`True`，用户可以设置生成的设计器关系图的填充颜色。 若要将此项设置，请右键单击关系图形状，然后单击**添加 Explosed**。|False|  
|作为属性公开文本颜色|如果`True`，用户可以在生成的设计器中设置关系图的文本颜色。 若要将此项设置，请右键单击关系图形状，然后单击**添加 Explosed**。|False|  
|描述|用于记录生成的设计器中的说明。|\<none>|  
|显示名称|将在生成的设计器为此关系图中显示的名称。|\<none>|  
|帮助关键字|用于索引为此关系图 F1 帮助关键字。|\<none>|  
  
## <a name="see-also"></a>请参阅  
 [域特定语言工具术语表](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
