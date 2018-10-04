---
title: CA1501： 避免过度继承 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: febffd0b9e2fb0275cab1a8055515c83fade5a12
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587643"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501：避免过度继承
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[CA1501： 避免过度继承](https://docs.microsoft.com/visualstudio/code-quality/ca1501-avoid-excessive-inheritance)。

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|类别|Microsoft.Maintainability|
|是否重大更改|重大|

## <a name="cause"></a>原因
 类型在继承层次结构中的深度超过四级。

## <a name="rule-description"></a>规则说明
 深度嵌套的类型层次结构可能很难遵循、理解和维护。 此规则将分析限制的同一模块中的层次结构。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请从继承层次结构中较浅的基类型派生类型或消除一些中间的基类型。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 它可以安全地禁止显示此规则的警告。 但是，代码可能更难以维护。 请注意，具体取决于基类型的可见性，解决此规则冲突的情况可能会造成重大更改。 例如，删除公共基类型是一项重大更改。

## <a name="example"></a>示例
 下面的示例显示了违反了此规则的类型。

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]


