---
title: Edit and Continue (Visual C++)
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3fd223b0a5891bc28cdef18dcd64312812607422
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428457"
---
# <a name="edit-and-continue-visual-c"></a>Edit and Continue (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可以在 Visual C++ 项目中使用 Edit and Continue。 请参阅[支持的代码更改 (C++)](../debugger/supported-code-changes-cpp.md)，了解有关 Edit and Continue 的限制的信息。  
  
 从 Visual Studio 2015 Update 1 开始，你现在可以使用编辑并继续在 Windows 应用商店中C++应用和 DirectX 应用，因为它现在支持 **/ZI**编译器开关与 **/bigobj**切换。 您还可以使用与使用编译的二进制文件的编辑并继续 **/FASTLINK**切换。  
  
 Update 1 其他的改进功能包括一个新型可取消的等待对话框，以及文件不支持“编辑并继续”时发出的通知。 有关 Update 1 改进功能的详细信息，请参阅[改进C++编辑并继续在 Visual Studio 2015 Update 1 中](http://blogs.msdn.com/b/vcblog/archive/2015/11/30/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1.aspx)。  
  
 Visual Studio 2013 Update 3 中引入的编译器选项 [/Zo（增强优化调试）](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) 向 .pdb （符号） 文件中添加了其他信息，用于未使用 [/Od（禁用（调试））](http://msdn.microsoft.com/library/aafb762y.aspx)选项编译的二进制文件。  
  
 **/Zo** 禁用 Edit and Continue。 请参阅[如何：调试优化的代码](../debugger/how-to-debug-optimized-code.md)。  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> 启用或禁用“编辑并继续”  
 如果要对代码进行编辑而又不希望在当前调试会话过程中应用这些编辑，则可以禁用自动调用“编辑并继续”。 也可以重新启用“编辑并继续”的自动操作。  
  
1. 在 **“工具”** 菜单上，选择 **“选项”**。  
  
2. 在“选项”  对话框中，选择“调试”/“常规” 文件夹。  
  
3. 在“编辑并继续”  组中，选中或取消选中“启用本机编辑并继续”  复选框。  
  
   更改此设置将影响当前处理的所有项目。 更改此设置后，不必重新生成应用程序。 你甚至可以在调试时更改此设置。 如果从命令行或从生成文件生成应用程序但在 Visual Studio 环境中调试，则在设置了 **/ZI** 选项的情况下，仍可以使用“编辑并继续”。  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a> 如何显式应用代码更改  
 在 Visual C++ 中，“编辑并继续”可以以两种方法应用代码更改。 代码更改可在选择执行命令时隐式应用，也可使用 **“应用代码更改”** 命令显式应用。  
  
 当显式应用代码更改时，程序保持在中断模式下，不会执行。  
  
- 或者，使用“应用代码更改”命令则可以显式应用代码更改。  
  
## <a name="BKMK_How_to_stop_code_changes"></a> 如何停止代码更改  
 当“编辑并继续”处于应用代码更改的过程中时，您可以停止该操作。  
  
 要停止应用代码更改：  
  
- 在 **调试** 菜单中选择 **停止应用代码更改**。  
  
  该菜单项仅在应用代码更改时才可见。  
  
  如果选择了改选项，就不会进行任何代码更改。  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a> 如何重置执行点  
 在“编辑并继续”应用更改时，一些代码更改会使执行点移动到新的位置。 “编辑并继续”尽可能正确地放置执行点，但是并非所有情况下的结果都正确。  
  
 在 Visual C++ 中，当执行点发生更改时，会显示一个对话框来提示此情况。 在继续调试之前，应验证位置是否正确。 如果位置不正确，则使用**设置下一语句**命令。 有关详细信息，请参阅[设置下一个要执行的语句](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute)。  
  
## <a name="BKMK_How_to_work_with_stale_code"></a> 如何使用陈旧代码  
 在某些情况下，“编辑并继续”无法将代码更改立即应用于可执行文件，但如果您继续调试，则可能会在稍后应用代码更改。 当编辑某个调用当前函数的函数，或将多于 64 个字节的新变量添加到调用堆栈上的函数时，就会发生这种情况。  
  
 在这种情况下，调试器会继续执行原始代码，直至可以应用更改。 陈旧的代码在单独的源窗口中作为临时源文件窗口显示，并带有一个类似 `enc25.tmp`的标题。 编辑过的源继续在原始源窗口中显示。 当您尝试编辑陈旧的代码时，会显示一条警告信息。  
  
## <a name="see-also"></a>请参阅  
 [受支持的代码更改 (C++)](../debugger/supported-code-changes-cpp.md)
