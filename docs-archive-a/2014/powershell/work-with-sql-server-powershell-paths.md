---
title: SQL Server PowerShell パスの操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f31d8e2c-8d59-4fee-ac2a-324668e54262
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d2647251eb1c8843d4ab7a95d2c439e47f5bb6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715453"
---
# <a name="work-with-sql-server-powershell-paths"></a><span data-ttu-id="53920-102">SQL Server PowerShell パスの操作</span><span class="sxs-lookup"><span data-stu-id="53920-102">Work With SQL Server PowerShell Paths</span></span>
  <span data-ttu-id="53920-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] プロバイダーのパスでノードに移動した後、ノードに関連付けられている [!INCLUDE[ssDE](../includes/ssde-md.md)] 管理オブジェクトのメソッドとプロパティを使用して、作業を実行したり、情報を取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="53920-103">After you have navigated to a node in a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can perform work or retrieve information by using the methods and properties from the [!INCLUDE[ssDE](../includes/ssde-md.md)] management object associated with the node.</span></span>  
  
1.  [<span data-ttu-id="53920-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="53920-104">Before You Begin</span></span>](#BeforeYouBegin)  
  
2.  <span data-ttu-id="53920-105">**パス ノードに関する作業:**  [メソッドとプロパティの一覧表示](#ListPropMeth)、 [メソッドとプロパティの使用](#UsePropMeth)</span><span class="sxs-lookup"><span data-stu-id="53920-105">**To work on a path node:**  [Listing Methods and Properties](#ListPropMeth), [Using Methods and Properties](#UsePropMeth)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="53920-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="53920-106">Before You Begin</span></span>  
 <span data-ttu-id="53920-107">[!INCLUDE[ssDE](../includes/ssde-md.md)] プロバイダーのパスでノードに移動した後、2 種類の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="53920-107">After you have navigated to a node in a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can perform two types of actions:</span></span>  
  
-   <span data-ttu-id="53920-108">**Rename-Item**など、ノードを操作する Windows PowerShell コマンドレットを実行できます。</span><span class="sxs-lookup"><span data-stu-id="53920-108">You can run Windows PowerShell cmdlets that operate on nodes, such as **Rename-Item**.</span></span>  
  
-   <span data-ttu-id="53920-109">関連付けられた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理オブジェクト モデル (SMO など) のメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="53920-109">You can call the methods from the associated [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] management object model, such as SMO.</span></span> <span data-ttu-id="53920-110">たとえば、パスで <xref:Microsoft.SqlServer.Management.Smo.Database> ノードに移動すると、 クラスのメソッドとプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="53920-110">For example, if you navigate to the Databases node in a path, you can use the methods and properties of the <xref:Microsoft.SqlServer.Management.Smo.Database> class.</span></span>  
  
 <span data-ttu-id="53920-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーは、 [!INCLUDE[ssDE](../includes/ssde-md.md)]のインスタンスのオブジェクトを管理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="53920-111">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider is used to manage the objects in an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="53920-112">データベース内のデータの処理には使用されません。</span><span class="sxs-lookup"><span data-stu-id="53920-112">It is not used to work with the data in databases.</span></span> <span data-ttu-id="53920-113">テーブルまたはビューに移動した場合に、プロバイダーを使用してデータの選択、挿入、更新、または削除を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="53920-113">If you have navigated to a table or view, you cannot use the provider to select, insert, update, or delete data.</span></span> <span data-ttu-id="53920-114">テーブルおよびビューのデータを Windows PowerShell 環境からクエリまたは変更するには、 **Invoke-Sqlcmd** コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="53920-114">Use the **Invoke-Sqlcmd** cmdlet to query or change data in tables and views from the Windows PowerShell environment.</span></span> <span data-ttu-id="53920-115">詳細については、「 [Invoke-Sqlcmd コマンドレット](../database-engine/invoke-sqlcmd-cmdlet.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53920-115">For more information, see [Invoke-Sqlcmd cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md).</span></span>  
  
##  <a name="listing-methods-and-properties"></a><a name="ListPropMeth"></a><span data-ttu-id="53920-116">メソッドとプロパティの一覧表示</span><span class="sxs-lookup"><span data-stu-id="53920-116">Listing Methods and Properties</span></span>
  
 <span data-ttu-id="53920-117">特定のオブジェクトまたはオブジェクト クラスで使用できるメソッドとプロパティを表示するには、 **Get-Member** コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="53920-117">To view the methods and properties available for specific objects or object classes, use the **Get-Member** cmdlet.</span></span>  
  
### <a name="examples-listing-methods-and-properties"></a><span data-ttu-id="53920-118">例: メソッドとプロパティの一覧表示</span><span class="sxs-lookup"><span data-stu-id="53920-118">Examples: Listing Methods and Properties</span></span>  
 <span data-ttu-id="53920-119">次の例では、Windows PowerShell 変数に SMO <xref:Microsoft.SqlServer.Management.Smo.Database> クラスを設定し、メソッドとプロパティを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="53920-119">This example sets a Windows PowerShell variable to the SMO <xref:Microsoft.SqlServer.Management.Smo.Database> class and lists the methods and properties:</span></span>  
  
```powershell
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar | Get-Member -Type Methods  
$MyDBVar | Get-Member -Type Properties  
```  
  
 <span data-ttu-id="53920-120">また、 **Get-Member** を使用して、Windows PowerShell パスの終了ノードに関連付けられているメソッドとプロパティを一覧表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="53920-120">You can also use **Get-Member** to list the methods and properties that are associated with the end node of a Windows PowerShell path.</span></span>  
  
 <span data-ttu-id="53920-121">次の例では、SQLSERVER: パスで Databases ノードに移動し、コレクションのプロパティを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="53920-121">This example navigates to the Databases node in a SQLSERVER: path and lists the collection properties:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-Item . | Get-Member -Type Properties  
```  
  
 <span data-ttu-id="53920-122">次の例では、SQLSERVER: パスで AdventureWorks2012 ノードに移動し、オブジェクトのプロパティを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="53920-122">This example navigates to the AdventureWorks2012 node in a SQLSERVER: path and lists the object properties:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
Get-Item . | Get-Member -Type Properties  
```  
  
##  <a name="using-smo-methods-and-properties"></a><a name="UsePropMeth"></a><span data-ttu-id="53920-123">SMO のメソッドとプロパティの使用</span><span class="sxs-lookup"><span data-stu-id="53920-123">Using SMO Methods and Properties</span></span>  
  
 <span data-ttu-id="53920-124">[!INCLUDE[ssDE](../includes/ssde-md.md)] プロバイダー パスからオブジェクトの操作を実行するには、SMO メソッドとプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="53920-124">To perform work on objects from a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can use SMO methods and properties.</span></span>  
  
### <a name="examples-using-methods-and-properties"></a><span data-ttu-id="53920-125">例: メソッドとプロパティの使用</span><span class="sxs-lookup"><span data-stu-id="53920-125">Examples: Using Methods and Properties</span></span>  
 <span data-ttu-id="53920-126">次の例では、SMO の **Schema** プロパティを使用して、AdventureWorks2012 の Sales スキーマからテーブルの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="53920-126">This example uses the SMO **Schema** property to get a list of the tables from the Sales schema in AdventureWorks2012:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Tables  
Get-ChildItem | Where {$_.Schema -eq "Sales"}  
```  
  
 <span data-ttu-id="53920-127">この例では、SMO の**script**メソッドを使用して、 `CREATE VIEW` AdventureWorks2012 でビューを再作成するために必要なステートメントを含むスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="53920-127">This example uses the SMO **Script** method to generate a script that contains the `CREATE VIEW` statements you must have to re-create the views in AdventureWorks2012:</span></span>  
  
```powershell
Remove-Item C:\PowerShell\CreateViews.sql  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Views  
foreach ($Item in Get-ChildItem) { $Item.Script() | Out-File -Filepath C:\PowerShell\CreateViews.sql -append }  
```  
  
 <span data-ttu-id="53920-128">次の例では、SMO の **Create** メソッドを使用してデータベースを作成し、 **State** プロパティを使用してデータベースが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="53920-128">This example uses the SMO **Create** method to create a database, and then uses the **State** property to show whether the database exists:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar.Parent = (Get-Item ..)  
$MyDBVar.Name = "NewDB"  
$MyDBVar.Create()  
$MyDBVar.State  
```  
  
## <a name="see-also"></a><span data-ttu-id="53920-129">参照</span><span class="sxs-lookup"><span data-stu-id="53920-129">See Also</span></span>  
 <span data-ttu-id="53920-130">[SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="53920-130">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="53920-131">[SQL Server PowerShell パスの移動](navigate-sql-server-powershell-paths.md) </span><span class="sxs-lookup"><span data-stu-id="53920-131">[Navigate SQL Server PowerShell Paths](navigate-sql-server-powershell-paths.md) </span></span>  
 <span data-ttu-id="53920-132">[Urn を SQL Server プロバイダーのパスに変換する](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span><span class="sxs-lookup"><span data-stu-id="53920-132">[Convert URNs to SQL Server Provider Paths](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span></span>  
 [<span data-ttu-id="53920-133">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="53920-133">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
