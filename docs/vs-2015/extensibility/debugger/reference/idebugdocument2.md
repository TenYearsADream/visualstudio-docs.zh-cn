---
title: IDebugDocument2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d840039f6ec9c4dce16e8efe9d6dbb2d91cad5d8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47482942"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[IDebugDocument2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocument2)。  
  
此接口表示源文档。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者的说明  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 通常可实现此接口。 它需要提供的源代码和磁盘上不存在源时，调试引擎 (DE) 还可以实现此接口。  在这种情况下，还将实现 DE [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)并[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)接口，以及一些其他方法[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)并[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 上的方法`IDebugDocumentContext2`， `IDebugDisassemblyStream2`， `IDebugDocumentPosition2`，和`IDebugActivateDocumentEvent2`接口返回此接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugDocument2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|获取文档的名称中有几种形式之一。|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|获取文档的类标识符。|  
  
## <a name="remarks"></a>备注  
 仅当 DE 提供的源代码时，实现此接口。 例如，调试 HTML 页面上的脚本时，DE 提供的源代码由于下载或动态生成的源，并且不存在为磁盘文件。 传统的语言，如 c + +，进行调试时则不需要实现此接口。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>请参阅  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
