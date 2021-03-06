---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e69435a319a9730af846a912cb3f90a12d4ac8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945778"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

比较两个文件。 差异将在特殊 Visual Studio 窗口中显示。

## <a name="syntax"></a>语法

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>自变量

- SourceFile

  必需。 要比较的第一个文件的完整路径和名称。

- TargetFile

  必需。 要比较的第二个文件的完整路径和文件名。

- SourceDisplayName

  可选。 第一个文件的显示名称。

- TargetDisplayName

  可选。 第二个文件的显示名称。

## <a name="remarks"></a>备注

如果 IDE 实例已打开，文件比较会出现在当前 IDE 中的选项卡内。

## <a name="example"></a>示例

第一个示例比较两个文件，而不更改它们的显示名称。 第二个示例比较文件，但更改这两个文件的显示名称。 第三个示例和第四个示例比较两个文件，但仅向第一个文件或第二个文件应用别名。

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>请参阅

- [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)
