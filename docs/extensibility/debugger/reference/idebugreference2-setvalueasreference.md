---
title: "IDebugReference2::SetValueAsReference |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e295ad3fd09a8b5dbaa17cdd6f10f3cb8a9ff1b9
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
设置从另一个引用的引用的值。 留待将来使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>参数  
 `rgpArgs`  
 [in]数组[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)对象用于确定如何设置引用值。  
  
 `dwArgCount`  
 [in]数组中引用的数目。  
  
 `pValue`  
 [in][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)要根据其设置的属性值的对象。  
  
 `dwTimeout`  
 [in]以毫秒为单位，从此方法返回前等待的最长时间。 使用`INFINITE`无限期等待。  
  
## <a name="return-value"></a>返回值  
 始终返回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)