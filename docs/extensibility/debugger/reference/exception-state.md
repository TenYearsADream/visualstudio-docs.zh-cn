---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9c0c5ed3f4432deeb26e97ff21f6d89de9ee109
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720310"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
指定的异常状态。

## <a name="syntax"></a>语法

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="members"></a>成员
EXCEPTION_NONE 执行操作的异常处停止。

在第一个触发异常处停止 EXCEPTION_STOP_FIRST_CHANCE。 描述时的异常事件，此标志指示异常事件是最可能的异常事件。

在第二个触发异常处停止 EXCEPTION_STOP_SECOND_CHANCE。 描述异常事件时, 指示异常事件是第二个可能发生的异常事件。

在第一个激发用户模式异常处停止 EXCEPTION_STOP_USER_FIRST_CHANCE。 描述异常事件时, 指示异常事件是最可能的用户异常事件。

EXCEPTION_STOP_USER_UNCAUGHT 停止时的用户模式异常未被捕获。 描述异常事件时, 指示异常事件是未捕获的用户模式异常事件。

EXCEPTION_STOP_ALL 停止任何异常。 描述异常事件时，不使用。

EXCEPTION_CANNOT_BE_CONTINUED 时描述异常事件，指示该异常不能从继续执行。

EXCEPTION_CODE_SUPPORTED 指示异常具有支持它的代码。 用于显示异常

EXCEPTION_CODE_DISPLAY_IN_HEX 指示应以十六进制格式显示异常代码。 用于显示异常。

EXCEPTION_JUST_MY_CODE_SUPPORTED 指示的异常代码支持 JustMyCode。 用于显示异常。

EXCEPTION_MANAGED_DEBUG_ASSISTANT 指示托管的代码调试程序应处理异常。 如果未设置，默认调试器处理的异常。 这将传递到[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法而不用于[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)结构。

EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT 已过时，则不要使用。

EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT 已过时，则不要使用。

EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT 已过时，则不要使用。

EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT 已过时，则不要使用。

## <a name="remarks"></a>备注
用作`dwState`的成员[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)结构来指示的异常和有关它可以做什么的状态。

这些值也将传递给[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法以设置所有异常的状态。

可能会使用按位 OR 组合这些标志。

## <a name="requirements"></a>要求
标头： msdbg.h

命名空间:Microsoft.VisualStudio.Debugger.Interop

程序集：Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
