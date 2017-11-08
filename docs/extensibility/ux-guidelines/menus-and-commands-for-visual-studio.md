---
title: "菜单和 Visual studio 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# 菜单和 Visual studio 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## 命令用法  
  
### 概述  
 与 Microsoft Office，这是包含许多单独的产品套件，不同的是 Visual Studio 包含许多产品，每个有任何贡献全局 Visual Studio IDE 到他们的命令集。 IDE 通过筛选功能可供用户根据上下文管理数千个命令的复杂性。  
  
 更改用户的上下文 – 例如，从设计窗口切换到代码编辑窗口 – 功能无关的新上下文就会消失。 在同一时间，以及相关的动态信息，例如属性和工具箱选项的新功能曲面。 用户应该不会注意到可用的命令集的交换。 如果用户是很难或由命令出现或消失感到困惑，UI 设计需要调整。 用户的当前上下文始终在一个或多个方面，如中指出的 IDE 标题栏、 属性窗口或属性页对话框。  
  
 命令栏允许在用户界面的灵活性。 唯一命令结构固有的 Visual Studio 环境是在主菜单和主要的命令栏中，该值可同时进行自定义，甚至隐藏。 其他命令栏出现和消失基于应用程序的状态。 工具窗口和文档编辑器还可以包含在其窗口边界内嵌入的工具栏。  
  
#### 基本指南  
  
##### 使用现有共享的命令、 命令组和菜单只要有可能。  
 由于命令，将通常显示在上下文上，使用现有共享的菜单和命令组可确保命令结构将保持相对稳定之间上下文中的更改。 再次使用共享的命令和放置新命令接近相关共享命令还降低了 IDE 的复杂性，并创建更加友好的用户体验。 如果需要定义一个新的命令，请尝试将其放在现有的共享的命令组。 如果需要定义一个新的组，将其放置在接近相关的命令组的现有共享菜单中创建一个新的顶级菜单之前。  
  
##### 不要创建的每个命令的图标。  
 在创建命令图标之前，请细致思考。 应仅为命令创建图标的:  
  
-   显示在默认工具栏上。  
  
-   可能由用户添加到通过工具栏 **自定义...** 对话框。  
  
-   具有一个与其他 Microsoft 产品中相同的操作关联的图标。  
  
##### 限制添加键盘快捷方式  
 绝大多数用户使用所有可用的快捷方式的一小部分。 当有疑问时，没有将绑定功能的键盘快捷方式。 使用您的用户体验团队然后再添加新的快捷方式。  
  
##### 提供命令作为默认菜单放置位置。  
 请注意，您的命令将由其他自定义，并且相应地对它们进行设计。 隐藏的命令，没有此类内容。 所有 Visual Studio 命令出现在 **工具 \> 自定义** 对话框中，命令窗口中，自动完成、 **工具 \> 选项 \> 键盘** 对话框中和开发工具环境 \(DTE\)。 请确保为您的命令指定名称和.ctc 文件中的工具提示，以便用户可以轻松地找到它们。  
  
##### 不复制在嵌入式工具栏上的共享的命令。  
 它可用于将命令放在紧靠用户的关注领域。 若要这样做的一种方法是在工具窗口或文档的顶部编辑器创建嵌入式工具栏。 置于工具栏上的命令应特定于窗口内的内容区域。 不复制这些工具栏上的共享的命令。 例如，永远不会将放置在嵌入式工具栏上的"保存"图标。  
  
### 内容和命令的可见性  
 命令位于以下范围: **环境**, ，**层次结构**, ，和 **文档**。 为了使命令放置中的置信度知道每个作用域。  
  
 中的命令 **环境** 作用域建立主上下文和多个上下文之间共享。 它们将更改的可见性或排列的文档和工具窗口。 作用域列出了其中一些在环境中的命令 **新项目**, ，**连接到服务器**, ，**附加进程**, ，**剪切**, ，**副本**, ，**粘贴**, ，**查找**, ，**选项**, ，**自定义**, ，**新窗口**, ，和 **视图帮助**。  
  
 中的命令 **层次结构** 作用域管理层次结构中 Visual Studio 包括 **项目**, ，**团队**, ，和 **数据**。 它们与相关联的项目子上下文 – 例如， **调试**, ，**生成**, ，**测试**, ，**体系结构**, ，或 **分析**。 作用域列出了其中一些层次结构中的命令 **添加新项**, ，**新查询**, ，**项目设置**, ，**添加新数据源**, ，**启动性能向导**, ，和 **新关系图**。  
  
 中的命令 **文档** 内容的文档，如代码、 设计或工作项查询 \(WIQ\) 的作用域操作。 它们还作用于一个工具窗口的视图，或为特定于该工具窗口。 文档作用域命令的行为还本身层次结构中特定的如文件对象上 **从项目中删除**。 作用域列出了其中一些文档中的命令 **重构 \> 重命名**, ，**创建工作项的副本**, ，**全部展开**, ，**全部折叠**, ，和 **创建用户任务**。  
  
### 命令放置决策  
 一旦您已决定创建命令，您需要确定及其相应的位置以及是否创建键盘快捷方式。 请按照此决策路径来指定在何处放置命令的位置:  
  
 ![Command placement decision chart](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501\-a\_CommandPlacement")  
  
 **用于 Visual Studio 中的命令放置决策路径**  
  
### 在菜单中的命令放置  
  
#### 主菜单栏  
 主菜单栏应构成 UI 任何特定于上下文菜单中程序包的命令的标准位置。 主菜单栏与其他命令结构不同，因为在环境中使用它来控制哪些命令都可见。 所有其他命令栏只需禁用命令不在上下文中，它们放在一个菜单或工具栏上。  
  
 环境定义一组内置于主菜单栏的命令所共有跨整个 IDE 和任务的多个域。 这些命令是始终可见的而不考虑其中 Vspackage 加载到环境。 虽然 Vspackage 可以扩展此命令集，从每个产品和其命令的位置设置命令将为每个团队的责任。  
  
 Visual Studio 主菜单的结构可以分为以下几个菜单类别:  
  
##### 核心菜单  
  
-   文件  
  
-   Edit  
  
-   视图  
  
-   工具  
  
-   窗口  
  
-   帮助  
  
##### 特定于项目的菜单  
  
-   Project  
  
-   生成  
  
-   调试  
  
##### 特定于上下文菜单  
  
-   团队  
  
-   数据  
  
-   测试  
  
-   体系结构  
  
-   分析  
  
##### 特定于文档的菜单  
  
-   格式  
  
-   表  
  
##### 在设计时主菜单，请遵循这些规则:  
  
-   不能超过 25 个顶级项目在给定的上下文中  
  
-   菜单应该永远不会超过 600 像素高。  
  
-   旗舰版 SKU 和常规配置文件中，如评估多个上下文中的主菜单。  
  
-   飞出式菜单为可接受。  
  
-   飞出式菜单应包含至少三个项并不能超过七个。  
  
-   深层飞出式菜单应该只有一个级别 – 某些 Visual Studio 菜单项具有级联子菜单，但不是建议使用此模式。  
  
-   可以使用不超过 6 个分隔符。 分组应遵循与下图:  
  
     ![Guidelines for main menu grouping](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501\-b\_MainMenus")  
  
-   虽然不需要具有在图中的每个分组，但添加其他分组是受限制。  
  
-   每个分组应具有的两到七个菜单项。  
  
#### 主菜单中排序  
 然后再添加一个新的顶级项，请考虑将该命令放在现有的顶级菜单。 在添加新的顶级菜单时，请务必将其放在正确的位置。 确定是否特定于项目、 上下文或文档菜单。 保留的顶级菜单名称简洁并使用只有一个字。  
  
 核心菜单应该书挡其余的命令。 文件、 编辑和视图应始终在左侧，，工具窗口中，并且帮助应始终是右对齐。  
  
#### 上下文菜单  
 放置过多的上下文菜单中的功能会导致难以了解接口。 所有主要功能应该能通过主菜单栏。 命令放置应该与现有的命令，以避免重复命令进行对帐。 对于上下文菜单，外壳中定义应包括根据上下文菜单是否为解决方案、 项目节点或项目项的标准菜单组。  
  
 在设计时上下文菜单，遵循相同的规则与主菜单中，和此外:  
  
-   不能超过 25 个顶级菜单项目。  
  
-   飞出式菜单可接受，但必须不能超过同一级别\-\-不应使用级联浮出控件。  
  
-   可以使用不超过 6 个分隔符。  
  
### 在工具栏中的命令放置  
  
#### 常规工具栏  
 在设计和排列工具栏时，应遵循这些标准:  
  
-   不要使用多个谓词，每个按钮。 一个按钮 \= 一个操作。  
  
-   仅当它需要强化的标签，请使用图标旁边的文本。  
  
-   使用组合框中以独占方式为将在一个会话中多次打开的属性。 否则，公开的属性在其他位置。  
  
-   组合框的宽度应等于内框 \+ 30%的最长的项的宽度。 例如，如果最长的项为 200 像素，组合框应为 260 像素宽。  
  
-   限制使用分隔符。 使用下拉列表旁边分隔符是反模式，因为形状的下拉列表中本身可以充当直观分隔符。  
  
-   图标组应包含三到六个图标。  
  
-   如果限定符导致多个有用的命令，请使用存储的最后一个设置的拆分按钮:  
  
     ![Split buttons in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501\-c\_SplitButtons")  
  
     **拆分按钮的示例。 在左侧的六个命令可以改为放入一个按钮。**  
  
#### 特定于产品的工具栏  
 每个产品可以提供包含经常使用的默认工具栏和重要的命令，每个产品的默认工具栏上应显示第一次启动 Visual Studio 后安装该产品。  
  
 共享的命令组和菜单提供的 IDE，还应利用产品。 每个共享的命令组置于共享菜单旨在为用户有意义的方式组织相关的命令。 请务必利用此共享的命令结构，以便降低复杂性。  
  
#### 全局工具栏  
 全局工具栏所需适合在初始状态下一行右侧。 在创建新的全局工具栏时，请按照该工具栏类型的指导原则。  
  
 **常规工具栏指导原则:**  
  
-   每个工具栏公共控件 \(控制手柄，溢出\) 中有 24 个像素。  
  
-   每个工具栏按钮是 22 个像素宽包括填充。 使拆分按钮的图标将添加另一个 11 像素宽。  
  
-   允许跨工具栏命令的重复。  
  
 **特定于文档的工具栏** 显示特定文件类型处于活动状态时，并在不同的文件类型将变为活动状态时消失。  
  
-   特定于文档的工具栏不能具有超过 12 个按钮。  
  
-   工具栏上的总宽度不能超过 300 像素。  
  
-   每种文件类型可以具有一个嵌入式工具栏上或一个特定于文档的全局工具栏上，但不要同时使用两者。  
  
 **上下文特定工具栏** 时某些上下文显示设置，并倾向于长时间保持活动状态。  
  
-   适用于所有特定于上下文的工具栏的按钮限制为 18。  
  
-   如果上下文处于活动状态时，大多数用户不会一致地使用此工具栏命令，然后不将关联此工具栏的上下文。  
  
-   确保，在退出上下文时，工具栏将消失。 在启动时未出现任何这些工具栏应。  
  
 **没有上下文的工具栏** 永远不会自动显示。 显示这些监视器，仅当用户激活它们。 使低于 200 像素的最大宽度。  
  
### 常规组织和命令行程序定义的组  
 使用现有共享的命令、 命令组和菜单。 如果需要定义一个新的命令，请尝试将其放在现有的共享的命令组。 如果需要定义一个新的组，请尝试创建一个新的顶级菜单之前将其放置在现有共享菜单接近相关的命令组。 这将减少同时确保一致的命令放置在 IDE 中命令的复杂性。  
  
 共享 **格式** 菜单上，通常在设计器样式的文档窗口的上下文中显示在下图中所示:  
  
 ![Visual Studio Format menu with callouts](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501\-d\_FormatMenu")  
  
 **Visual Studio 中的菜单组**  
  
### 减少和重复使用的命令  
 命令，将通常显示在上下文中，以减少用户将看到在任意给定时间的命令数。 但是，您应重复使用现有共享的菜单和命令组，以确保命令结构保持相对稳定的上下文中的更改之间。  
  
 再次使用共享的命令和放置新命令接近相关共享命令降低了 IDE 的复杂性，并创建更加友好的用户体验。  
  
## 命名的命令  
  
### 命名约定  
 一致命令命名至关重要，以便用户可以查找并执行命令，通过使用命令行或绑定到的键盘快捷方式的不同而不同。 命令名称还帮助用户了解哪些命令可显示在工具栏上或级联或上下文菜单中时的目的。  
  
#### 命名命令时:  
  
-   构造文本，以便更易于本地化。 有关本地化文本的详细信息，请参阅 [Visual Studio 的全球通用性](http://msdn.microsoft.com/zh-cn/1cc35051-8126-441f-bea9-059245a47b1d)。  
  
-   为简洁。 命令应使用不超过三个单词。  
  
-   使用标题首字母大写的大小写作: 每个单词的第一个字母应首字母大写。 有关 Visual Studio 中的文本格式的详细信息，请参阅 [文本样式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。  
  
-   请考虑将在其中放置该命令。 是在顶级菜单或浮出控件? 例如，当浮出控件的顶级命令中的分组对齐命令应为"对齐"和飞出式命令应将"Left""右"、"中心，""两端对齐，"等。 这是多余命名飞出式命令"左对齐"或"对齐右对齐。"  
  
     ![Visual Studio Format menu](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502\-a\_FormatMenu")  
  
### 使用命令图标  
 适当使用图标配对使用命令中使用。 尽管将唯一的映像与命令相关联 hastens 用户能够识别该命令，但视觉混乱和效率低下可能出现图像过度使用。 下列规则帮助时决定是否要创建命令图标。  
  
#### 使用命令只有当图标:  
  
-   相同的命令都有一个中另一个重要的 Microsoft 产品，例如 Microsoft Office 应用程序与之关联的图标。  
  
-   该命令将放入默认工具栏。  
  
-   该命令是用户很容易将添加到工具栏使用专业命令 **"自定义..."** 对话框。  
  
## 访问键和快捷键  
  
### 概述  
 有两种类型的键盘键分配方案:  
  
-   **访问密钥** \(也称为加速器\) 允许在对话框 UI 中使用键盘访问通过菜单命令并向每个标签。 访问键是主要是为了可访问性、 分配给所有菜单和大多数对话框控件、 不打算要记住，只有当前窗口，会对影响和已经进行了本地化。  
  
-   **快捷键** 主要使用控制 \(Ctrl\) 和功能 \(Fn\) 按键顺序。 它们旨在更高级的用户和保持工作效率。 它们只分配给最常用的命令，并且在跳过主菜单时允许快速访问。 键盘快捷方式用于所存储，并且对于的原因，必须分配与配置文件方案一致。 快捷方式的关键方案可能会因配置有所不同。 用户可以自定义快捷键通过 **工具 \> 选项 \> 键盘**。  
  
### 分配访问键  
 访问键包含 Alt 加上字母数字键。 将访问键分配给每个菜单项无一例外。 按照 Windows 和通用约定，以便分配访问键。 例如，对于访问密钥 **文件 \> 新建** 应始终为 **Alt、 F、 N**。  
  
 不使用单一像素宽度字母 i \(以大写或小写\) 或小写字母 l，如并避免在使用下行字母 \(g、 j、 p、 q 和 y\) 的字符，原因是难以区分它们。  
  
 避免使用重复的键在可能的情况。 在重复是不可避免的情况下，菜单系统通过遍历使用密钥的所有命令处理冲突。 例如，对于"Number"命令在文件菜单重复"N"访问密钥下, 一个假想 **Alt、 F、 N** 将创建一个新文件和 **Alt、 F、 N 和 N** 将执行"Number"命令。  
  
### 分配快捷键  
 避免分配新的快捷键，因为它们不是需要为每条命令，税系统 \(和用户内存\) 如果过度使用。 数据从客户体验改善计划 \(CEIP\) 指示 Visual Studio 用户使用只有一小部分的集成的快捷方式。  
  
 在定义的快捷方式时，遵循以下规则:  
  
-   **使用控件 \(Ctrl\) 和功能 \(Fn\) 按键顺序。**  
  
-   **保留频繁使用的快捷方式。**维护的最受欢迎的快捷方式。  
  
-   **使编辑器快捷键容易键入。**将简单类型的快捷方式绑定到开发人员在编写代码时的最需要的命令。 例如， **Edit.InvokeSmartTag** 需要快速快捷键，如 Ctrl \+ 和不 Alt \+ Shift \+ F10。  
  
-   **尽可能一致地应用了主题快捷方式。**  
  
-   **遵循 Windows 准则，以确定哪个修改键来使用。**使用 Ctrl 键组合产生大规模的效果，例如，将应用于整个文档的命令的命令。 用于扩展或补充的操作的标准的快捷键的命令使用 Shift 键组合。 请勿使用 Ctrl \+ Alt 组合。  
  
-   **删除多余的快捷方式。**如果您有一个旧的特征，请考虑删除如果访问键提供对相同的命令的快速访问与极少被 \(少于 10 次从 CEIP 数据\) 或中等均值 \(少于 100 次从 CEIP 数据\) 使用的快捷方式。 例如: Alt、 H、 C 将会打开帮助\/内容。  
  
 不是一种以检查快捷可用性的简单方法。 如果您想要添加快捷方式，请按照下列步骤:  
  
1.  检查的列表 [Visual Studio 2013 快捷方式](http://visualstudioshortcuts.com/2013/) 以确定是否有相似的命令，以与您进行分组。  
  
2.  转到 **工具 \> 选项 \> 环境 \> 键盘** 和测试您的快捷方式。 检查每个键盘映射方案列出在"应用以下其他键盘映射方案"。 检查常规、 C\#、 VB 和 c \+ \+ 的配置文件，因为将这些共享唯一快捷方式。 您的快捷方式之后，方可未映射任何这些位置中。