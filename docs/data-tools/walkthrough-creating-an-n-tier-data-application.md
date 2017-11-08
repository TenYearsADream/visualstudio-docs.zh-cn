---
title: "演练：创建 N 层数据应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "n 层应用程序, 创建"
  - "n 层应用程序, 演练"
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 48
caps.handback.revision: 48
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：创建 N 层数据应用程序
*“N 层”*数据应用程序是指用于访问数据且分为多个逻辑层（或*“多层”*）的应用程序。  通过将应用程序组件分离到相对独立的层中，可以提高应用程序的可维护性和可伸缩性。  该结构之所以具有这种优点，是因为它有利于采用可应用于单个层而无需重新设计整个解决方案的新技术。  N 层体系结构包括一个表示层、一个中间层和一个数据层。  中间层通常包括数据访问层、业务逻辑层和共享组件（例如身份验证和验证）。  数据层则包括关系数据库。  N 层应用程序通常将敏感信息存储在中间层的数据访问层中，目的是将它们与访问表示层的最终用户隔离。  有关详细信息，请参阅[N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)。  
  
 在 N 层应用程序中，分离各层的一种方法是为要包括在应用程序中的每一层创建相互独立的项目。  类型化数据集包含一个 `DataSet Project` 属性，该属性决定了生成的数据集和 `TableAdapter` 代码应归属到哪些项目中。  
  
 本演练演示如何使用**“数据集设计器”**将数据集和 `TableAdapter` 代码分离到相互独立的类库项目中。  分离数据集和 TableAdapter 代码后，你将创建 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)服务以调入数据访问层。  最后，你要创建一个 Windows 窗体应用程序并将其用作表示层。  该层将访问数据服务中的数据。  
  
 在本演练中，你将执行以下步骤：  
  
-   新建将包含多个项目的 N 层解决方案。  
  
-   将两个类库项目添加到 N 层解决方案中。  
  
-   使用**“数据源配置向导”**创建类型化数据集。  
  
-   将生成的 [TableAdapter](../Topic/TableAdapters.md) 和数据集代码分离到相互独立的项目中。  
  
-   创建 Windows Communication Foundation \(WCF\) 服务以调入数据访问层。  
  
-   在服务中创建函数以从数据访问层检索数据。  
  
-   创建 Windows 窗体应用程序来充当表示层。  
  
-   创建绑定到数据源的 Windows 窗体控件。  
  
-   编写代码以填充数据表。  
  
 ![链接到视频](~/data-tools/media/playvideo.gif "PlayVideo") 有关本主题的视频版本，请参阅[视频帮助：创建 N 层数据应用程序](http://go.microsoft.com/fwlink/?LinkId=115188)。  
  
## 系统必备  
 若要完成本演练，你需要：  
  
-   能够访问 Northwind 示例数据库。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建 N 层解决方案和用于保存数据集的类库 \(DataEntityTier\)  
 本演练的第一步是创建一个解决方案和两个类库项目。  第一个类库将保存数据集（生成的类型化 DataSet 类以及将保存应用程序数据的数据表）。  此项目将用作应用程序的数据实体层，它通常位于中间层内。  [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)用于创建初始数据集，并自动将代码分离到两个类库中。  
  
> [!NOTE]
>  请确保已正确命名项目和解决方案，然后再单击**“确定”**。  这样做可使你更轻松地完成本演练。  
  
#### 创建 N 层解决方案和 DataEntityTier 类库  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
    > [!NOTE]
    >  **“数据集设计器”**在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 C\# 项目中受支持。  请使用这些语言之一创建新项目。  
  
2.  在**“新建项目”**对话框的**“项目类型”**窗格中，单击**“Windows”**。  
  
3.  单击**“类库”**模板。  
  
4.  将项目命名为“DataEntityTier”。  
  
5.  将解决方案命名为“NTierWalkthrough”。  
  
6.  单击“确定”。  
  
     包含 DataEntityTier 项目的 NTierWalkthrough 解决方案即被创建并添加到**“解决方案资源管理器”**中。  
  
## 创建用于保存 TableAdapter 的类库 \(DataAccessTier\)  
 创建 DataEntityTier 项目后，下一步是创建另一个类库项目。  此项目将保存生成的 `TableAdapter`，它称为应用程序的*“数据访问层”*。  数据访问层包含连接到数据库所需的信息，通常位于中间层内。  
  
#### 创建用于 TableAdapter 的新类库  
  
1.  从**“文件”**菜单中，将新项目添加到 NTierWalkthrough 解决方案。  
  
2.  在**“新建项目”**对话框的**“模板”**窗格中，单击**“类库”**。  
  
3.  将该项目命名为 DataAccessTier，然后单击**“确定”**。  
  
     DataAccessTier 项目即被创建并添加到 NTierWalkthrough 解决方案中。  
  
## 创建数据集  
 下一步是创建类型化数据集。  通过单个项目中的数据集类（包括 DataTable 类）和 `TableAdapter` 类创建类型化数据集。  （所有类都将生成到单个文件中。）在将数据集和 `TableAdapter` 分离到不同的项目中时，移到另一个项目中的是数据集类，`TableAdapter` 类则留在原始项目中。  因此，应在最终包含 `TableAdapter` 的项目（DataAccessTier 项目）中创建数据集。  你将使用**“数据源配置向导”**创建数据集。  
  
> [!NOTE]
>  你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。  有关如何设置 Northwind 示例数据库的信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
#### 创建数据集  
  
1.  在**“解决方案资源管理器”**中单击 DataAccessTier。  
  
2.  在**“数据”**菜单上，单击**“显示数据源”**。  
  
3.  在**“数据源”**窗口中，单击**“添加新数据源”**以启动**“数据源配置向导”**。  
  
4.  在**“选择数据源类型”**页面上，单击**“数据库”**，然后单击**“下一步”**。  
  
5.  在**“选择你的数据连接”**页面上，执行以下操作之一：  
  
     如果下拉列表中包含到 Northwind 示例数据库的数据连接，请单击该连接。  
  
     \- 或 \-  
  
     单击**“新建连接”**以打开**“添加连接”**对话框。  
  
6.  如果数据库需要密码，请选择该选项以包括敏感数据，然后单击**“下一步”**。  
  
    > [!NOTE]
    >  如果选择了本地数据库文件（而不是连接至 SQL Server），系统可能会询问你是否将该文件添加到项目中。  请单击**“是”**，以便将该数据库文件添加到项目中。  
  
7.  在**“将连接字符串保存到应用程序配置文件中”**页上单击**“下一步”**。  
  
8.  在**“选择数据库对象”**页面上展开**“表”**节点。  
  
9. 单击**“Customers”**和**“Orders”**表的复选框，然后单击**“完成”**。  
  
     NorthwindDataSet 将会添加到 DataAccessTier 项目中并显示在**“数据源”**窗口内。  
  
## 将 TableAdapter 与数据集分离  
 创建数据集后，接着是要将生成的数据集类与 TableAdapter 分离。  通过将**“数据集项目”**属性设置为要用于存储分离出的数据集类的项目的名称，可以达到此目的。  
  
#### 将 TableAdapter 与数据集分离  
  
1.  在**“解决方案资源管理器”**中双击**“NorthwindDataSet.xsd”**，以在**“数据集设计器”**中打开该数据集。  
  
2.  单击设计器上的空白区域。  
  
3.  在**“属性”**窗口中查找**“数据集项目”**节点。  
  
4.  在**“数据集项目”**列表中，单击**“DataEntityTier”**。  
  
5.  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
 将数据集和 TableAdapter 分离到两个类库项目中。  最初包含整个数据集的项目 \(DataAccessTier\) 现在只包含 TableAdapter。  **“数据集项目”**属性中指定的项目 \(DataEntityTier\) 则包含类型化数据集：NorthwindDataSet.Dataset.Designer.vb（或 NorthwindDataSet.Dataset.Designer.cs）。  
  
> [!NOTE]
>  分离数据集与 TableAdapter（通过设置**“数据集项目”**属性）时，将不会自动移动项目中现有的数据集分部类。  你必须手动将它们移到数据集项目中。  
  
## 创建新的服务应用程序  
 由于本演练演示如何使用 WCF 服务访问数据访问层，因此需要创建一个新的 WCF 服务应用程序。  
  
#### 创建新的 WCF 服务应用程序  
  
1.  从**“文件”**菜单中，将新项目添加到 NTierWalkthrough 解决方案。  
  
2.  在**“新建项目”**对话框的**“项目类型”**窗格中，单击**“WCF”**。  在**“模板”**窗格中，单击**“WCF 服务库”**。  
  
3.  将该项目命名为 DataService，然后单击**“确定”**。  
  
     DataService 项目即被创建并添加到 NTierWalkthrough 解决方案中。  
  
## 在数据访问层中创建用于返回客户和订单数据的方法  
 数据服务需要调用数据访问层中的两个方法：GetCustomers 和 GetOrders。  这些方法将返回 Northwind 的 Customers 表和 Orders 表。  请在 DataAccessTier 项目中创建 GetCustomers 和 GetOrders 方法。  
  
#### 在数据访问层中创建返回 Customers 表的方法  
  
1.  在**“解决方案资源管理器”**中，双击 NorthwindDataset.xsd 以在[创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)中打开该数据集。  
  
2.  右键单击 CustomersTableAdapter，然后单击**“添加查询”**以打开 [TableAdapter 查询配置向导](../data-tools/editing-tableadapters.md)。  
  
3.  在**“选择命令类型”**页面上，保留**“使用 SQL 语句”**的默认值，然后单击**“下一步”**。  
  
4.  在**“选择查询类型”**页面上，保留**“SELECT \(返回行\)”**的默认值，然后单击**“下一步”**。  
  
5.  在**“指定 SQL SELECT 语句”**页面上，保留默认查询，然后单击**“下一步”**。  
  
6.  在**“选择要生成的方法”**页面上，为**“返回 DataTable”**部分的**“方法名称”**键入 GetCustomers。  
  
7.  单击**“完成”**。  
  
#### 在数据访问层中创建返回 Orders 表的方法  
  
1.  右键单击 OrdersTableAdapter，然后单击**“添加查询”**。  
  
2.  在**“选择命令类型”**页面上，保留**“使用 SQL 语句”**的默认值，然后单击**“下一步”**。  
  
3.  在**“选择查询类型”**页面上，保留**“SELECT \(返回行\)”**的默认值，然后单击**“下一步”**。  
  
4.  在**“指定 SQL SELECT 语句”**页面上，保留默认查询，然后单击**“下一步”**。  
  
5.  在**“选择要生成的方法”**页面上，为**“返回 DataTable”**部分的**“方法名称”**键入 GetOrders。  
  
6.  单击**“完成”**。  
  
7.  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
## 向数据服务中添加对数据实体和数据访问层的引用  
 由于数据服务需要数据集和 TableAdapter 中的信息，因此需要添加对 DataEntityTier 和 DataAccessTier 项目的引用。  
  
#### 添加对数据服务的引用  
  
1.  在**“解决方案资源管理器”**中右键单击 DataService，然后单击**“添加引用”**。  
  
2.  在**“添加引用”**对话框中单击**“项目”**选项卡。  
  
3.  同时选择**“DataAccessTier”**和**“DataEntityTier”**项目。  
  
4.  单击“确定”。  
  
## 向服务中添加函数以调用数据访问层中的 GetCustomers 和 GetOrders 方法  
 现在数据访问层包含返回数据的方法，接下来要在数据服务中创建调用这些方法的方法。  
  
> [!NOTE]
>  对于 C\# 项目，必须添加对 `System.Data.DataSetExtensions` 程序集的引用，才能编译下面的代码。  
  
#### 在数据服务中创建 GetCustomers 和 GetOrders 函数  
  
1.  在**“DataService”**项目中，双击 IService1.vb 或 IService1.cs。  
  
2.  在**“在此处添加服务操作”**注释下方添加以下代码：  
  
    ```vb#  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```c#  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
  
    ```  
  
3.  在 DataService 项目中，双击 Service1.vb（或 Service1.cs）。  
  
4.  将以下代码添加到 Service1 类中：  
  
    ```vb#  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```c#  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
  
    }  
    ```  
  
5.  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
## 创建表示层以显示数据服务中的数据  
 现在，解决方案中的数据服务已具有调入数据访问层的方法，接下来要创建另一个项目，以调入数据服务并将数据显示给用户。  对于本演练，创建一个 Windows 窗体应用程序；它将充当 N 层应用程序的表示层。  
  
#### 创建表示层项目  
  
1.  从**“文件”**菜单中，将新项目添加到 NTierWalkthrough 解决方案。  
  
2.  在**“新建项目”**对话框的**“项目类型”**窗格中，单击**“Windows”**。  在**“模板”**窗格中，单击**“Windows 窗体应用程序”**。  
  
3.  将该项目命名为 PresentationTier，然后单击**“确定”**。  
  
4.  PresentationTier 项目即被创建并添加到 NTierWalkthrough 解决方案中。  
  
## 将 PresentationTier 项目设置为启动项目  
 由于表示层是用于显示数据和进行数据交互的实际客户端应用程序，因此必须将 PresentationTier 项目设置为启动项目。  
  
#### 将新的表示层项目设置为启动项目  
  
-   在**“解决方案资源管理器”**中，右键单击**“PresentationTier”**，然后单击**“设为启动项目”**。  
  
## 添加对表示层的引用  
 客户端应用程序 PresentationTier 需要具有对数据服务的服务引用，才能访问服务中的方法。  另外，WCF 服务又需要具有对数据集的引用，才能启用类型共享。  而只有通过数据服务启用类型共享，表示层才能使用添加到数据集分部类中的代码。  由于数据表的行和列更改事件中通常添加有类似于验证的代码，因此可能需要从客户端访问此代码。  
  
#### 添加定义表示层的引用  
  
1.  在**“解决方案资源管理器”**中，右键单击 PresentationTier，然后单击**“添加引用”**。  
  
2.  在**“添加引用”**对话框中，单击**“项目”**选项卡。  
  
3.  选择**“DataEntityTier”**，然后单击**“确定”**。  
  
#### 添加对表示层的服务引用  
  
1.  在**“解决方案资源管理器”**中，右键单击 PresentationTier，然后单击**“添加服务引用”**。  
  
2.  在**“添加服务引用”**对话框中，单击**“发现”**。  
  
3.  选择**“Service1”**，然后单击**“确定”**。  
  
    > [!NOTE]
    >  如果当前计算机上存在多项服务，请选择你在本演练的前面部分中创建的服务（即包含 GetCustomers 和 GetOrders 方法的服务）。  
  
## 将 DataGridView 添加到窗体，以显示数据服务返回的数据  
 在添加对数据服务的服务引用后，将自动使用该服务返回的数据填充**“数据源”**窗口。  
  
#### 将两个数据绑定 DataGridView 添加到窗体中  
  
1.  在**“解决方案资源管理器”**中，选择 PresentationTier 项目。  
  
2.  在**“数据源”**窗口中，展开**“NorthwindDataSet”**，然后查找**“Customers”**节点。  
  
3.  将**“Customers”**节点拖到 Form1 上。  
  
4.  在**“数据源”**窗口中，展开**“Customers”**节点，然后查找相关的**“Orders”**节点（**“Orders”**节点嵌套在**“Customers”**节点中）。  
  
5.  将相关的**“Orders”**节点拖到 Form1 上。  
  
6.  通过双击窗体的空白区域，创建一个 `Form1_Load` 事件处理程序。  
  
7.  将以下代码添加到 `Form1_Load` 事件处理程序中。  
  
    ```vb#  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```c#  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
  
    ```  
  
## 增加服务所允许的最大消息大小  
 由于服务会返回 Customers 和 Orders 表中的数据，而 maxReceivedMessageSize 的默认值还不够大，无法容纳这些数据，因此必须予以增加。  对于本演练，将值更改为 6553600。  将在客户端上更改该值，此操作将自动更新服务引用。  
  
> [!NOTE]
>  较小的默认大小旨在降低遭受拒绝服务 \(DoS\) 攻击的可能性。  有关详细信息，请参阅<xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>。  
  
#### 增加 maxReceivedMessageSize 值  
  
1.  在**“解决方案资源管理器”**的 PresentationTier 项目中，双击 app.config 文件。  
  
2.  查找**“maxReceivedMessage”**大小特性，然后将该值更改为 `6553600`。  
  
## 测试应用程序  
 运行该应用程序。  它会从数据服务中检索数据，并将检索到的数据显示在窗体上。  
  
#### 测试应用程序  
  
1.  按 F5。  
  
2.  应用程序会从数据服务中检索 Customers 和 Orders 表的数据，并将检索到的数据显示在窗体上。  
  
## 后续步骤  
 根据应用程序的要求，在基于 Windows 的应用程序中保存相关数据后，可能还要执行一些步骤。  例如，你可以对此应用程序进行以下增强：  
  
-   将验证添加到数据集。  有关信息，请参阅[演练：向 N 层数据应用程序添加验证](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)。  
  
-   将其他方法添加到服务，以将数据更新回数据库。  
  
## 请参阅  
 [在 N 层应用程序中使用数据集](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [分层更新](../data-tools/hierarchical-update.md)   
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)