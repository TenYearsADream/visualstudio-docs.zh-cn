---
title: -Deploy (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0dac8564c06efd65b8db04e0aa0fae97a849e6cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421416"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

生成或重新生成后部署解决方案。 仅适用于托管代码项目。  
  
## <a name="syntax"></a>语法  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## <a name="arguments"></a>自变量  
 `SolnConfigName`  
 必需。 `SolutionName` 中指定了将用于生成解决方案的解决方案配置的名称。  
  
 `SolutionName`  
 必需。 解决方案文件的完整路径和名称。  
  
 /project `ProjName`  
 可选。 解决方案中项目文件的路径和名称。 可以输入从 `SolutionName` 文件夹到项目文件的相对路径、项目的显示名称或项目文件的完整路径和名称。  
  
 /projectconfig `ProjConfigName`  
 可选。 指定了生成命名的 `/project` 时要使用的项目生成配置的名称。  
  
## <a name="remarks"></a>备注  
 指定的项目必须是部署项目。 如果指定的项目不是部署项目，当传递已生成的项目进行部署时会失败并出现错误。  
  
 用双引号将含有空格的字符串引起来。  
  
 “命令”窗口或使用 `/out` 开关指定的任何日志文件中都可显示生成的摘要信息（包括错误）。  
  
## <a name="example"></a>示例  
 本示例使用 `MySolution` 的 `Release` 解决方案配置中的 `Release` 项目生成配置来部署 `CSharpConsoleApp` 项目。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## <a name="see-also"></a>请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
