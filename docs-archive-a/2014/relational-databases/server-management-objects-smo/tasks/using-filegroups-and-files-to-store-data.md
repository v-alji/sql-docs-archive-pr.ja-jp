---
title: ファイルグループとファイルを使用したデータの格納 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- filegroups [SMO]
- storing data [SMO]
- files [SMO]
- files [SMO], about files
- storage [SMO]
ms.assetid: 7e2327ce-e1a6-4904-83d1-0944b24a7b43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 15ac5fd0c43c9b58432a774ae11aeb6500f0403b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644401"
---
# <a name="using-filegroups-and-files-to-store-data"></a><span data-ttu-id="734bf-102">ファイルとファイル グループを使用したデータの格納</span><span class="sxs-lookup"><span data-stu-id="734bf-102">Using Filegroups and Files to Store Data</span></span>
  <span data-ttu-id="734bf-103">データベース ファイルの格納には、データ ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="734bf-103">Data files are used to store database files.</span></span> <span data-ttu-id="734bf-104">データ ファイルは、ファイル グループに細分化されます。</span><span class="sxs-lookup"><span data-stu-id="734bf-104">The data files are subdivided into file groups.</span></span> <span data-ttu-id="734bf-105"><xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトには、<xref:Microsoft.SqlServer.Management.Smo.Database.FileGroups%2A> オブジェクトを参照する <xref:Microsoft.SqlServer.Management.Smo.FileGroupCollection> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="734bf-105">The <xref:Microsoft.SqlServer.Management.Smo.Database> object has a <xref:Microsoft.SqlServer.Management.Smo.Database.FileGroups%2A> property that references a <xref:Microsoft.SqlServer.Management.Smo.FileGroupCollection> object.</span></span> <span data-ttu-id="734bf-106">このコレクション内の各 <xref:Microsoft.SqlServer.Management.Smo.FileGroup> オブジェクトには、<xref:Microsoft.SqlServer.Management.Smo.FileGroup.Files%2A> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="734bf-106">Each <xref:Microsoft.SqlServer.Management.Smo.FileGroup> object in that collection has a <xref:Microsoft.SqlServer.Management.Smo.FileGroup.Files%2A> property.</span></span> <span data-ttu-id="734bf-107">このプロパティは、データベースに属するすべてのデータ ファイルが含まれる、<xref:Microsoft.SqlServer.Management.Smo.DataFileCollection> コレクションを参照します。</span><span class="sxs-lookup"><span data-stu-id="734bf-107">This property refers to a <xref:Microsoft.SqlServer.Management.Smo.DataFileCollection> collection that contains all the data files that belong to the database.</span></span> <span data-ttu-id="734bf-108">ファイル グループは主に、データベース オブジェクトの格納に使用されるファイルをグループ化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="734bf-108">A file group is principally used to group files together that are used to store a database object.</span></span> <span data-ttu-id="734bf-109">データベース オブジェクトを複数のファイルに分散する理由の 1 つは、これによってパフォーマンスを向上させることができるからです。パフォーマンスの向上は、ファイルを複数のディスク ドライブに格納されていれば特に期待できます。</span><span class="sxs-lookup"><span data-stu-id="734bf-109">One reason for spreading a database object over several files is that it can improve performance, especially if the files are stored on different disk drives.</span></span>  
  
 <span data-ttu-id="734bf-110">自動的に作成される各データベースには、"Primary" という名前のファイル グループと、データベースと同じ名前を持つデータ ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="734bf-110">Every database that is created automatically has a file group named "Primary" and a data file with the same name as the database.</span></span> <span data-ttu-id="734bf-111">コレクションにはファイルおよびグループを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="734bf-111">Additional files and groups can be added to the collections.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="734bf-112">例</span><span class="sxs-lookup"><span data-stu-id="734bf-112">Examples</span></span>  
 <span data-ttu-id="734bf-113">次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="734bf-113">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="734bf-114">詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="734bf-114">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-visual-basic"></a><span data-ttu-id="734bf-115">Visual Basic でファイル グループおよびデータ ファイルをデータベースに追加する</span><span class="sxs-lookup"><span data-stu-id="734bf-115">Adding FileGroups and DataFiles to a Database in Visual Basic</span></span>  
 <span data-ttu-id="734bf-116">プライマリ ファイル グループおよびデータ ファイルは、既定のプロパティ値を使用して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="734bf-116">The primary file group and data file are created automatically with default property values.</span></span> <span data-ttu-id="734bf-117">コード例では、使用できるいくつかのプロパティ値を指定しています。</span><span class="sxs-lookup"><span data-stu-id="734bf-117">The code example specifies some property values that you can use.</span></span> <span data-ttu-id="734bf-118">指定しなかった場合は、既定のプロパティ値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="734bf-118">Otherwise, the default property values are used.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBFileGroups1](SMO How to#SMO_VBFileGroups1)]  -->  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-visual-c"></a><span data-ttu-id="734bf-119">Visual C# でファイル グループおよびデータ ファイルをデータベースに追加する</span><span class="sxs-lookup"><span data-stu-id="734bf-119">Adding FileGroups and DataFiles to a Database in Visual C#</span></span>  
 <span data-ttu-id="734bf-120">プライマリ ファイル グループおよびデータ ファイルは、既定のプロパティ値を使用して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="734bf-120">The primary file group and data file are created automatically with default property values.</span></span> <span data-ttu-id="734bf-121">コード例では、使用できるいくつかのプロパティ値を指定しています。</span><span class="sxs-lookup"><span data-stu-id="734bf-121">The code example specifies some property values that you can use.</span></span> <span data-ttu-id="734bf-122">指定しなかった場合は、既定のプロパティ値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="734bf-122">Otherwise, the default property values are used.</span></span>  
  
```csharp
{  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a FileGroup object called SECONDARY on the database.   
            FileGroup fg1 = default(FileGroup);  
            fg1 = new FileGroup(db, "SECONDARY");  
            //Call the Create method to create the file group on the instance of SQL Server.   
            fg1.Create();  
            //Define a DataFile object on the file group and set the FileName property.   
            DataFile df1 = default(DataFile);  
            df1 = new DataFile(fg1, "datafile1");  
            df1.FileName = "c:\\Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\Data\\datafile2.ndf";  
            //Call the Create method to create the data file on the instance of SQL Server.   
            df1.Create();  
        }  
```  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-powershell"></a><span data-ttu-id="734bf-123">PowerShell でのファイル グループおよびデータ ファイルのデータベースへの追加</span><span class="sxs-lookup"><span data-stu-id="734bf-123">Adding FileGroups and DataFiles to a Database in PowerShell</span></span>  
 <span data-ttu-id="734bf-124">プライマリ ファイル グループおよびデータ ファイルは、既定のプロパティ値を使用して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="734bf-124">The primary file group and data file are created automatically with default property values.</span></span> <span data-ttu-id="734bf-125">コード例では、使用できるいくつかのプロパティ値を指定しています。</span><span class="sxs-lookup"><span data-stu-id="734bf-125">The code example specifies some property values that you can use.</span></span> <span data-ttu-id="734bf-126">指定しなかった場合は、既定のプロパティ値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="734bf-126">Otherwise, the default property values are used.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012.  
$db = get-item AdventureWorks2012  
  
#Create a new filegroup  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "SECONDARY"  
$fg1.Create()  
  
#Define a DataFile object on the file group and set the FileName property.   
$df1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.DataFile -argumentlist $fg1, "datafile1"  
  
#Make sure to have a directory created to hold the designated data file  
$df1.FileName = "c:\\TestData\\datafile2.ndf"  
  
#Call the Create method to create the data file on the instance of SQL Server.   
$df1.Create()  
```  
  
## <a name="creating-altering-and-removing-a-log-file-in-visual-basic"></a><span data-ttu-id="734bf-127">Visual Basic でのログ ファイルの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="734bf-127">Creating, Altering, and Removing a Log File in Visual Basic</span></span>  
 <span data-ttu-id="734bf-128">コード例では、<xref:Microsoft.SqlServer.Management.Smo.LogFile> オブジェクトを作成し、プロパティの 1 つを変更して、このオブジェクトをデータベースから削除しています。</span><span class="sxs-lookup"><span data-stu-id="734bf-128">The code example creates a <xref:Microsoft.SqlServer.Management.Smo.LogFile> object, changes one of the properties, and then removes it from the database.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBFileGroups3](SMO How to#SMO_VBFileGroups3)]  -->  
  
## <a name="creating-altering-and-removing-a-log-file-in-visual-c"></a><span data-ttu-id="734bf-129">Visual C# でのログ ファイルの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="734bf-129">Creating, Altering, and Removing a Log File in Visual C#</span></span>  
 <span data-ttu-id="734bf-130">コード例では、<xref:Microsoft.SqlServer.Management.Smo.LogFile> オブジェクトを作成し、プロパティの 1 つを変更して、このオブジェクトをデータベースから削除しています。</span><span class="sxs-lookup"><span data-stu-id="734bf-130">The code example creates a <xref:Microsoft.SqlServer.Management.Smo.LogFile> object, changes one of the properties, and then removes it from the database.</span></span>  
  
```csharp
//Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a LogFile object and set the database, name, and file name properties in the constructor.   
            LogFile lf1 = default(LogFile);  
            lf1 = new LogFile(db, "logfile1", "c:\\Program Files\\Microsoft SQL Server\\MSSQL.10_50.MSSQLSERVER\\MSSQL\\Data\\logfile1.ldf");  
            //Set the file growth to 6%.   
            lf1.GrowthType = FileGrowthType.Percent;  
            lf1.Growth = 6;  
            //Run the Create method to create the log file on the instance of SQL Server.   
            lf1.Create();  
            //Alter the growth percentage.
            lf1.Growth = 7;  
            lf1.Alter();  
            //Remove the log file.
            lf1.Drop();
```  
  
## <a name="creating-altering-and-removing-a-log-file-in-powershell"></a><span data-ttu-id="734bf-131">PowerShell でのログ ファイルの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="734bf-131">Creating, Altering, and Removing a Log File in PowerShell</span></span>  
 <span data-ttu-id="734bf-132">コード例では、<xref:Microsoft.SqlServer.Management.Smo.LogFile> オブジェクトを作成し、プロパティの 1 つを変更して、このオブジェクトをデータベースから削除しています。</span><span class="sxs-lookup"><span data-stu-id="734bf-132">The code example creates a <xref:Microsoft.SqlServer.Management.Smo.LogFile> object, changes one of the properties, and then removes it from the database.</span></span>  
  
```powershell
#Load the assembly containing the enums used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlEnum")  
  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012  
$db = get-item AdventureWorks2012  
  
#Create a filegroup  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Secondary"  
  
#Call the Create method to create the file group on the instance of SQL Server.   
$fg1.Create()  
  
#Define a LogFile object on the file group and set the FileName property.   
$lf1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LogFile -argumentlist $db, "LogFile2"  
  
#Set a location for it - make sure the directory exists  
$lf1.FileName = "logfile1", "c:\\Program Files\\Microsoft SQL Server\\MSSQL.10_50.MSSQLSERVER\\MSSQL\\Data\\logfile1.ldf"  
  
#Set file growth to 6%  
$lf1.GrowthType = [Microsoft.SqlServer.Management.Smo.FileGrowthType]::Percent  
$lf1.Growth = 6.0  
  
#Call the Create method to create the data file on the instance of SQL Server.   
$lf1.Create()  
  
#Alter a value and drop the log file  
$lf1.Growth = 7.0  
$lf1.Alter()  
$lf1.Drop()
```  
  
## <a name="see-also"></a><span data-ttu-id="734bf-133">参照</span><span class="sxs-lookup"><span data-stu-id="734bf-133">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.FileGroup>   
 [<span data-ttu-id="734bf-134">データベース ファイルとファイル グループ</span><span class="sxs-lookup"><span data-stu-id="734bf-134">Database Files and Filegroups</span></span>](../../databases/database-files-and-filegroups.md)  
