---
title: フルテキスト検索の実装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- full-text search [SMO]
ms.assetid: 9ce9ad9c-f671-4760-90b5-e0c8ca051473
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8b797e2a38c9136c34b7058b539fca522e03229
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711838"
---
# <a name="implementing-full-text-search"></a><span data-ttu-id="98186-102">フルテキスト検索の実装</span><span class="sxs-lookup"><span data-stu-id="98186-102">Implementing Full-Text Search</span></span>
  <span data-ttu-id="98186-103">フルテキスト検索は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスごとに使用することができ、SMO では <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A> オブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="98186-103">Full-text search is available per instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and is represented in SMO by the <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A> object.</span></span> <span data-ttu-id="98186-104"><xref:Microsoft.SqlServer.Management.Smo.FullTextService> オブジェクトは、`Server` オブジェクトの下位に位置します。</span><span class="sxs-lookup"><span data-stu-id="98186-104">The <xref:Microsoft.SqlServer.Management.Smo.FullTextService> object resides under the `Server` object.</span></span> <span data-ttu-id="98186-105">このオブジェクトは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] フルテキスト検索サービスの構成オプションを管理するために使用します。</span><span class="sxs-lookup"><span data-stu-id="98186-105">It is used to manage the configuration options for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Full Text Search service.</span></span> <span data-ttu-id="98186-106"><xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> オブジェクトは <xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトに属し、データベースに対して定義されるフルテキスト カタログを表す <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> オブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="98186-106">The <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> object belongs to the <xref:Microsoft.SqlServer.Management.Smo.Database> object and it is a collection of <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> objects that represent full-text catalogs defined for the database.</span></span> <span data-ttu-id="98186-107">通常のインデックスとは異なり、フルテキスト インデックスは各テーブルに対して 1 つのみ定義されます。</span><span class="sxs-lookup"><span data-stu-id="98186-107">You can only have one full-text index defined for each table, unlike normal indexes.</span></span> <span data-ttu-id="98186-108">これは、<xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> オブジェクト内の <xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="98186-108">This is represented by a <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> object in the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
 <span data-ttu-id="98186-109">フルテキスト検索サービスを作成するには、データベースにフルテキスト カタログが定義されており、データベース内のいずれかのテーブルにフルテキスト検索インデックスが定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="98186-109">To create a full-text search service, you must have a full-text catalog defined on the database and a full-text search index defined on one of the tables in the database.</span></span>  
  
 <span data-ttu-id="98186-110">まず、<xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> コンストラクターを呼び出し、カタログ名を指定して、データベースにフルテキスト カタログを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-110">First, create a full-text catalog on the database by calling the <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> constructor and specifying the catalog name.</span></span> <span data-ttu-id="98186-111">次に、コンストラクターを呼び出し、フルテキスト インデックスを作成するテーブルを指定して、フルテキスト インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-111">Then, create the full-text index by calling the constructor and specifying the table on which it is to be created.</span></span> <span data-ttu-id="98186-112">次に、<xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> オブジェクトを使用して、テーブル内の列の名前を指定し、フルテキスト インデックスのインデックス列を追加します。</span><span class="sxs-lookup"><span data-stu-id="98186-112">You can then add index columns for the full-text index, by using the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> object and providing the name of the column within the table.</span></span> <span data-ttu-id="98186-113">次に、<xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> プロパティを、作成したカタログに設定します。</span><span class="sxs-lookup"><span data-stu-id="98186-113">Then, set the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> property to the catalog you have created.</span></span> <span data-ttu-id="98186-114">最後に、<xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> メソッドを呼び出して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにフルテキスト インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-114">Finally, call the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> method and create the full-text index on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="98186-115">例</span><span class="sxs-lookup"><span data-stu-id="98186-115">Example</span></span>  
 <span data-ttu-id="98186-116">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98186-116">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="98186-117">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98186-117">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-full-text-search-service-in-visual-basic"></a><span data-ttu-id="98186-118">Visual Basic でのフルテキスト検索サービスの作成</span><span class="sxs-lookup"><span data-stu-id="98186-118">Creating a Full-Text Search Service in Visual Basic</span></span>  
 <span data-ttu-id="98186-119">このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] サンプル データベースの `ProductCategory` テーブルに対してフルテキスト検索カタログを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-119">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="98186-120">次に、`ProductCategory` テーブル内の Name 列にフルテキスト検索インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-120">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="98186-121">フルテキスト検索インデックスを作成する列には、既に定義されている一意のインデックスが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98186-121">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.SqlEnum.dll   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      ' Connect to the local, default instance of SQL Server.  
      Dim srv As Server = Nothing  
      srv = New Server()  
  
      ' Reference the AdventureWorks database.  
      Dim db As Database = Nothing  
      db = srv.Databases("AdventureWorks")  
  
      ' Reference the ProductCategory table.  
      Dim tb As Table = Nothing  
      tb = db.Tables("ProductCategory", "Production")  
  
      ' Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      Dim ftc As FullTextCatalog = Nothing  
      ftc = New FullTextCatalog(db, "Test_Catalog")  
      ftc.IsDefault = True  
  
      ' Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create()  
  
      ' Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      Dim fti As FullTextIndex = Nothing  
      fti = New FullTextIndex(tb)  
  
      ' Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      Dim ftic As FullTextIndexColumn = Nothing  
      ftic = New FullTextIndexColumn(fti, "Name")  
  
      ' Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic)  
      fti.ChangeTracking = ChangeTracking.Automatic  
  
      ' Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
      ' Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog"  
  
      ' Create the Full Text Search index on the instance of SQL Server.  
      fti.Create()  
   End Sub  
End Class  
```  
  
## <a name="creating-a-full-text-search-service-in-visual-c"></a><span data-ttu-id="98186-122">Visual C# でのフルテキスト検索サービスの作成</span><span class="sxs-lookup"><span data-stu-id="98186-122">Creating a Full-Text Search Service in Visual C#</span></span>  
 <span data-ttu-id="98186-123">このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] サンプル データベースの `ProductCategory` テーブルに対してフルテキスト検索カタログを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-123">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="98186-124">次に、`ProductCategory` テーブル内の Name 列にフルテキスト検索インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-124">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="98186-125">フルテキスト検索インデックスを作成する列には、既に定義されている一意のインデックスが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98186-125">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.SqlEnum.dll   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.  
      Server srv = default(Server);  
      srv = new Server();  
  
      // Reference the AdventureWorks database.  
      Database db = default(Database);  
      db = srv.Databases ["AdventureWorks"];  
  
      // Reference the ProductCategory table.  
      Table tb = default(Table);  
      tb = db.Tables["ProductCategory", "Production"];  
  
      // Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      FullTextCatalog ftc = default(FullTextCatalog);  
      ftc = new FullTextCatalog(db, "Test_Catalog");  
      ftc.IsDefault = true;  
  
      // Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create();  
  
      // Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      FullTextIndex fti = default(FullTextIndex);  
      fti = new FullTextIndex(tb);  
  
      // Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      FullTextIndexColumn ftic = default(FullTextIndexColumn);  
      ftic = new FullTextIndexColumn(fti, "Name");  
  
      // Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic);  
      fti.ChangeTracking = ChangeTracking.Automatic;  
  
      // Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name";  
  
      // Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog";  
  
      // Create the Full Text Search index on the instance of SQL Server.  
      fti.Create();  
   }  
}  
```  
  
## <a name="creating-a-full-text-search-service-in-powershell"></a><span data-ttu-id="98186-126">PowerShell でのフルテキスト検索サービスの作成</span><span class="sxs-lookup"><span data-stu-id="98186-126">Creating a Full-Text Search Service in PowerShell</span></span>  
 <span data-ttu-id="98186-127">このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] サンプル データベースの `ProductCategory` テーブルに対してフルテキスト検索カタログを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-127">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="98186-128">次に、`ProductCategory` テーブル内の Name 列にフルテキスト検索インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="98186-128">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="98186-129">フルテキスト検索インデックスを作成する列には、既に定義されている一意のインデックスが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98186-129">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = Get-Item AdventureWorks2012  
  
CD AdventureWorks\tables  
  
#Get a reference to the table  
$tb = Get-Item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -ArgumentList $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -ArgumentList $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -ArgumentList $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
