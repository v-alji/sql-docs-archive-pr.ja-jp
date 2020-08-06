---
title: ビューの作成、変更、および削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd8d75e413b1871ce4b8784f5087cb08ed08da73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644941"
---
# <a name="creating-altering-and-removing-views"></a><span data-ttu-id="d3f8c-102">ビューの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="d3f8c-102">Creating, Altering, and Removing Views</span></span>
  <span data-ttu-id="d3f8c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ビューは <xref:Microsoft.SqlServer.Management.Smo.View> オブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] views are represented by the <xref:Microsoft.SqlServer.Management.Smo.View> object.</span></span>  
  
 <span data-ttu-id="d3f8c-104"><xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.View> プロパティはビューを定義します。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-104">The <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.View> object defines the view.</span></span> <span data-ttu-id="d3f8c-105">これは、ビューを作成する [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT ステートメントと等価です。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-105">It is the equivalent of the [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT statement for creating a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3f8c-106">例</span><span class="sxs-lookup"><span data-stu-id="d3f8c-106">Example</span></span>  
 <span data-ttu-id="d3f8c-107">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="d3f8c-108">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a><span data-ttu-id="d3f8c-109">Visual Basic でのビューの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="d3f8c-109">Creating, Altering, and Removing a View in Visual Basic</span></span>  
 <span data-ttu-id="d3f8c-110">このコード例では、内部結合を使用して 2 つのテーブルのビューを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-110">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="d3f8c-111">このビューはテキスト モードを使用して作成されるため、<xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> プロパティが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-111">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBViews1](SMO How to#SMO_VBViews1)]  -->  
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a><span data-ttu-id="d3f8c-112">Visual C# でのビューの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="d3f8c-112">Creating, Altering, and Removing a View in Visual C#</span></span>  
 <span data-ttu-id="d3f8c-113">このコード例では、内部結合を使用して 2 つのテーブルのビューを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-113">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="d3f8c-114">このビューはテキスト モードを使用して作成されるため、<xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> プロパティが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-114">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
```csharp
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a><span data-ttu-id="d3f8c-115">PowerShell でのビューの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="d3f8c-115">Creating, Altering, and Removing a View in PowerShell</span></span>  
 <span data-ttu-id="d3f8c-116">このコード例では、内部結合を使用して 2 つのテーブルのビューを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-116">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="d3f8c-117">このビューはテキスト モードを使用して作成されるため、<xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> プロパティが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3f8c-117">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View -argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.
$myview.Create()  
  
# Remove the view
$myview.Drop();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3f8c-118">参照</span><span class="sxs-lookup"><span data-stu-id="d3f8c-118">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
