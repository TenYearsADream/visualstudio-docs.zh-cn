---
title: “列出调用堆栈”命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 932dbc9e3971598748e462de92280ac7112f8c62
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665111"
---
# <a name="list-call-stack-command"></a>“列出调用堆栈”命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

显示当前调用堆栈。  
  
## <a name="syntax"></a>语法  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## <a name="arguments"></a>自变量  
 `index`  
 可选。 设置当前堆栈帧且不显示任何输出。  
  
## <a name="switches"></a>开关  
 每个开关都可以使用其完整形式或缩写形式来调用。  
  
 /Count:`number` [or] /C:`number`  
 可选。 要显示的调用堆栈的最大数量。 默认值为无限制。  
  
 /ShowTypes:`yes`|`no` [or] /T:`yes`|`no`  
 可选。 指定是否显示参数类型。 默认值是 `yes`。  
  
 /ShowNames:`yes``no` [or] /N:`yes``no`  
 可选。 指定是否显示参数名称。 默认值是 `yes`。  
  
 /ShowValues:`yes``no` [or] /V:`yes``no`  
 可选。 指定是否显示参数值。 默认值是 `yes`。  
  
 /ShowModule:`yes``no` [or] /M:`yes``no`  
 可选。 指定是否显示模块名称。 默认值是 `yes`。  
  
 /ShowLineOffset:`yes``no` [or] /#:`yes``no`  
 可选。 指定是否显示线偏移。 默认值是 `no`。  
  
 /ShowByteOffset:`yes``no` [or] /B:`yes``no`  
 可选。 指定是否显示字节偏移。 默认值是 `no`。  
  
 /ShowLanguage:`yes``no` [or] /L:`yes``no`  
 可选。 指定是否显示语言。 默认值是 `no`。  
  
 /IncludeCallsAcrossThreads:`yes``no` [or] /I:`yes`|`no`  
 可选。 指定是否包括对其他线程的调用或包括来自其他线程的调用。 默认值是 `no`。  
  
 /ShowExternalCode:`yes`|`no`  
 可选。 指定是否为调用堆栈显示“仅我的代码”。 “仅我的代码”关闭时，将显示所有非用户代码。 “仅我的代码”开启时，非用户代码在调用堆栈输出中显示为 `[external]`。  
  
 线程：`n`  
 可选。 显示线程 `n` 的调用堆栈。 如果没有指定线程，则显示当前线程的调用堆栈。  
  
## <a name="remarks"></a>备注  
 对参数或开关所做的更改将应用于对此命令的将来的调用。 如果发出 Debug.ListCallStackby 本身，则显示整个调用堆栈。 如果指定一个索引，例如，  
  
```  
Debug.ListCallStack 2  
```  
  
 则当前堆栈帧被设置为该帧（本例中为第二个帧）。  
  
 还可使用此命令的预定义别名 (kb) 编写此命令。 例如，可以输入  
  
```  
kb 2  
```  
  
 将当前堆栈帧设置为第二个帧。  
  
## <a name="example"></a>示例  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## <a name="see-also"></a>请参阅  
 [“列出反汇编”命令](../../ide/reference/list-disassembly-command.md)   
 [“列出线程”命令](../../ide/reference/list-threads-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找/命令”框](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
