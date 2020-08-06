---
title: テーブルとインデックスのパーティション分割を使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- partitions [SMO]
- storing data [SMO]
- partitioned tables [SQL Server], SMO
- partitioned indexes [SQL Server], SMO
ms.assetid: 0e682d7e-86c3-4d73-950d-aa692d46cb62
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e05087f63da163b8fa339befae039eb5e7e8245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633789"
---
# <a name="using-table-and-index-partitioning"></a><span data-ttu-id="f2e26-102">テーブルおよびインデックスのパーティション分割の使用</span><span class="sxs-lookup"><span data-stu-id="f2e26-102">Using Table and Index Partitioning</span></span>
  <span data-ttu-id="f2e26-103">データは、 [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md)によって提供される格納アルゴリズムを使用して格納することができます。</span><span class="sxs-lookup"><span data-stu-id="f2e26-103">Data can be stored by using the storage algorithms provided by [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md).</span></span> <span data-ttu-id="f2e26-104">パーティション分割により、大規模なテーブルとインデックスの管理の可能性と拡張性が向上します。</span><span class="sxs-lookup"><span data-stu-id="f2e26-104">Partitioning can make large tables and indexes more manageable and scalable.</span></span>  
  
## <a name="index-and-table-partitioning"></a><span data-ttu-id="f2e26-105">インデックスとテーブルのパーティション分割</span><span class="sxs-lookup"><span data-stu-id="f2e26-105">Index and Table Partitioning</span></span>  
 <span data-ttu-id="f2e26-106">この機能によって、インデックス データおよびテーブル データを、パーティション内の複数のファイル グループに分散させることができます。</span><span class="sxs-lookup"><span data-stu-id="f2e26-106">The feature enables index and table data to be spread across multiple file groups in partitions.</span></span> <span data-ttu-id="f2e26-107">パーティション関数は、パーティション分割列と呼ばれる特定の列の値に基づいて、テーブルまたはインデックスの行を一連のパーティションにどのようにマップするかを定義します。</span><span class="sxs-lookup"><span data-stu-id="f2e26-107">A partition function defines how the rows of a table or index are mapped to a set of partitions based on the values of certain columns, referred to as partitioning columns.</span></span> <span data-ttu-id="f2e26-108">パーティション構成は、パーティション関数によって指定された各パーティションをファイル グループにマップします。</span><span class="sxs-lookup"><span data-stu-id="f2e26-108">A partition scheme maps each partition specified by the partition function to a file group.</span></span> <span data-ttu-id="f2e26-109">これにより、複数のファイル グループにまたがってテーブルを拡張できるような、したがって物理デバイスもまたがって拡張できるような、アーカイブ戦略を開発することができます。</span><span class="sxs-lookup"><span data-stu-id="f2e26-109">This lets you develop archiving strategies that enable tables to be scaled across file groups, and therefore physical devices.</span></span>  
  
 <span data-ttu-id="f2e26-110"><xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトには、実装されたパーティション関数を表す <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> オブジェクトのコレクション、およびファイル グループへのデータのマップ方法を記述する <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> オブジェクトのコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2e26-110">The <xref:Microsoft.SqlServer.Management.Smo.Database> object contains a collection of <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> objects that represent the implemented partition functions and a collection of <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> objects that describe how data is mapped to file groups.</span></span>  
  
 <span data-ttu-id="f2e26-111">各 <xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.Index> オブジェクトは、どのパーティション構成を使用するかを <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> プロパティで指定し、列を <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection> で指定します。</span><span class="sxs-lookup"><span data-stu-id="f2e26-111">Each <xref:Microsoft.SqlServer.Management.Smo.Table> and <xref:Microsoft.SqlServer.Management.Smo.Index> object specifies which partition scheme it uses in the <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> property and specifies the columns in the <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2e26-112">例</span><span class="sxs-lookup"><span data-stu-id="f2e26-112">Example</span></span>  
 <span data-ttu-id="f2e26-113">次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2e26-113">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="f2e26-114">詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2e26-114">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-basic"></a><span data-ttu-id="f2e26-115">Visual Basic でのテーブルのパーティション構成の設定</span><span class="sxs-lookup"><span data-stu-id="f2e26-115">Setting Up a Partition Scheme for a Table in Visual Basic</span></span>  
 <span data-ttu-id="f2e26-116">コード例では、 `TransactionHistory` サンプル データベース内の [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] テーブルに対してパーティション関数およびパーティション構成を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f2e26-116">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="f2e26-117">これらのパーティションは、古いレコードを `TransactionHistoryArchive` テーブルに分割する目的で、日付によって分割されます。</span><span class="sxs-lookup"><span data-stu-id="f2e26-117">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBPartition1](SMO How to#SMO_VBPartition1)]  -->  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-c"></a><span data-ttu-id="f2e26-118">Visual C# でのテーブルのパーティション構成の設定</span><span class="sxs-lookup"><span data-stu-id="f2e26-118">Setting Up a Partition Scheme for a Table in Visual C#</span></span>  
 <span data-ttu-id="f2e26-119">コード例では、 `TransactionHistory` サンプル データベース内の [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] テーブルに対してパーティション関数およびパーティション構成を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f2e26-119">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="f2e26-120">これらのパーティションは、古いレコードを `TransactionHistoryArchive` テーブルに分割する目的で、日付によって分割されます。</span><span class="sxs-lookup"><span data-stu-id="f2e26-120">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
```csharp
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Define and create three new file groups on the database.   
FileGroup fg2;   
fg2 = new FileGroup(db, "Second");   
fg2.Create();   
FileGroup fg3;   
fg3 = new FileGroup(db, "Third");   
fg3.Create();   
FileGroup fg4;   
fg4 = new FileGroup(db, "Fourth");   
fg4.Create();   
//Define a partition function by supplying the parent database and name arguments in the constructor.   
PartitionFunction pf;   
pf = new PartitionFunction(db, "TransHistPF");   
//Add a partition function parameter that specifies the function uses a DateTime range type.   
PartitionFunctionParameter pfp;   
pfp = new PartitionFunctionParameter(pf, DataType.DateTime);   
pf.PartitionFunctionParameters.Add(pfp);   
//Specify the three dates that divide the data into four partitions.   
object[] val;   
val = new object[] {"1/1/2003", "1/1/2004", "1/1/2005"};   
pf.RangeValues = val;   
//Create the partition function.   
pf.Create();   
//Define a partition scheme by supplying the parent database and name arguments in the constructor.   
PartitionScheme ps;   
ps = new PartitionScheme(db, "TransHistPS");   
//Specify the partition function and the filegroups required by the partition scheme.   
ps.PartitionFunction = "TransHistPF";   
ps.FileGroups.Add("PRIMARY");   
ps.FileGroups.Add("second");   
ps.FileGroups.Add("Third");   
ps.FileGroups.Add("Fourth");   
//Create the partition scheme.   
ps.Create();   
}   
```  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-powershell"></a><span data-ttu-id="f2e26-121">PowerShell でのテーブルのパーティション構成の設定</span><span class="sxs-lookup"><span data-stu-id="f2e26-121">Setting Up a Partition Scheme for a Table in PowerShell</span></span>  
 <span data-ttu-id="f2e26-122">コード例では、 `TransactionHistory` サンプル データベース内の [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] テーブルに対してパーティション関数およびパーティション構成を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f2e26-122">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="f2e26-123">これらのパーティションは、古いレコードを `TransactionHistoryArchive` テーブルに分割する目的で、日付によって分割されます。</span><span class="sxs-lookup"><span data-stu-id="f2e26-123">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
$db = $srv.Databases["AdventureWorks"]  
#Create four filegroups  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "First"  
$fg2 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Second"  
$fg3 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Third"  
$fg4 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Fourth"  
  
#Define a partition function by supplying the parent database and name arguments in the constructor.  
$pf =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunction -argumentlist $db, "TransHistPF"  
$T = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$T  
$T.GetType()  
#Add a partition function parameter that specifies the function uses a DateTime range type.  
$pfp =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunctionParameter -argumentlist $pf, $T  
  
#Specify the three dates that divide the data into four partitions.
#Create an array of type object to hold the partition data  
$val = "1/1/2003"."1/1/2004","1/1/2005"  
$pf.RangeValues = $val  
$pf  
#Create the partition function  
$pf.Create()  
  
#Create partition scheme  
$ps = New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionScheme -argumentlist $db, "TransHistPS"  
$ps.PartitionFunction = "TransHistPF"  
  
#add the filegroups to the scheme
$ps.FileGroups.Add("PRIMARY")  
$ps.FileGroups.Add("Second")  
$ps.FileGroups.Add("Third")  
$ps.FileGroups.Add("Fourth")  
  
#Create it at the server  
$ps.Create()  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2e26-124">参照</span><span class="sxs-lookup"><span data-stu-id="f2e26-124">See Also</span></span>  
 [<span data-ttu-id="f2e26-125">パーティション テーブルとパーティション インデックス</span><span class="sxs-lookup"><span data-stu-id="f2e26-125">Partitioned Tables and Indexes</span></span>](../../partitions/partitioned-tables-and-indexes.md)  
