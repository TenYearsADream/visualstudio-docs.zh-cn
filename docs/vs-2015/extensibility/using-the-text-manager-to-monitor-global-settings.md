---
title: 使用文本管理器监视全局设置 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d7f93d0b736548f9ee815e0870a89dbd30ea21d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47481266"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>使用文本管理器监视全局设置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[使用文本管理器监视器全局设置](https://docs.microsoft.com/visualstudio/extensibility/using-the-text-manager-to-monitor-global-settings)。  
  
如果你实现核心编辑器，您必须监视到全局设置，所做的更改，因为这些更改可能会影响你的编辑器实例。 可以通过侦听由文本管理器引发的事件跟踪所做的更改。 例如，核心编辑器，如其文档数据对象中指定的外观或行为的一个组件的全局首选项时文本管理器存储此信息，并将其传递给所有受影响的客户端。  
  
## <a name="text-manager-functions"></a>文本管理器函数  
 文本管理器会引发多个设置，包括以下事件：  
  
-   缓冲区是否是受源代码管理  
  
-   如何注册文件更改通知  
  
-   如何跟踪哪些视图是与某些缓冲区相关联的  
  
-   文本颜色设置首选项  
  
-   空间首选项与选项卡  
  
 是唯一的给定语言的首选项不受文本管理器。 必须由每个语言服务管理这些设置。  
  
 提供文本管理器的事件通知<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>接口。 实现此接口上您的客户端对象来处理事件引发文本管理器。 通过使用这些事件注册<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>文本管理器上的接口。  
  
## <a name="see-also"></a>请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)   
 [编辑器功能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
