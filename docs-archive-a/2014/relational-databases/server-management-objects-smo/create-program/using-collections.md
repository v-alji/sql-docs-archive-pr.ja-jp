---
title: コレクションを使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: stevestein
ms.author: sstein
ms.openlocfilehash: 288f2110952a85d2aab610c0f1da40d433882400
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633013"
---
# <a name="using-collections"></a><span data-ttu-id="fabf6-102">コレクションの使用</span><span class="sxs-lookup"><span data-stu-id="fabf6-102">Using Collections</span></span>
  <span data-ttu-id="fabf6-103">コレクションとは、同じオブジェクト クラスから作成された、同じ親オブジェクトを持つオブジェクトのリストのことです。</span><span class="sxs-lookup"><span data-stu-id="fabf6-103">A collection is a list of objects that have been constructed from the same object class and that share the same parent object.</span></span> <span data-ttu-id="fabf6-104">コレクション オブジェクトには、Collection サフィックス付きのオブジェクトの種類の名前が必ず含まれています。</span><span class="sxs-lookup"><span data-stu-id="fabf6-104">The collection object always contains the name of the object type with the Collection suffix.</span></span> <span data-ttu-id="fabf6-105">たとえば、指定されたテーブル内の列にアクセスするには、<xref:Microsoft.SqlServer.Management.Smo.ColumnCollection> というオブジェクトの種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="fabf6-105">For example, to access the columns in a specified table, use the <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection> object type.</span></span> <span data-ttu-id="fabf6-106">これには、同じ <xref:Microsoft.SqlServer.Management.Smo.Column> オブジェクトに属するすべての <xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fabf6-106">It contains all the <xref:Microsoft.SqlServer.Management.Smo.Column> objects that belong to the same <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
 <span data-ttu-id="fabf6-107">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `For...Each` ステートメントまたは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] `foreach` ステートメントを使用して、コレクションの各メンバーを反復処理できます。</span><span class="sxs-lookup"><span data-stu-id="fabf6-107">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `For...Each` statement or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] `foreach` statement can be used to iterate through each member of the collection.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fabf6-108">例</span><span class="sxs-lookup"><span data-stu-id="fabf6-108">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a><span data-ttu-id="fabf6-109">Visual Basic でのコレクションを使用したオブジェクトの参照</span><span class="sxs-lookup"><span data-stu-id="fabf6-109">Referencing an Object by Using a Collection in Visual Basic</span></span>  
 <span data-ttu-id="fabf6-110">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A> プロパティ、<xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> プロパティ、および <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> プロパティを使用して、列プロパティを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fabf6-110">This code example shows how to set a column property by using the <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, and <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> properties.</span></span> <span data-ttu-id="fabf6-111">これらのプロパティはコレクションを表現しており、オブジェクトの名前を指定するパラメーターと共に使用すれば、特定のオブジェクトを識別するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="fabf6-111">These properties represent collections, which can be used to identify a particular object when they are used with a parameter that specifies the name of the object.</span></span> <span data-ttu-id="fabf6-112"><xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> コレクション オブジェクト プロパティには、名前とスキーマが必要です。</span><span class="sxs-lookup"><span data-stu-id="fabf6-112">The name and the schema are required for the <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> collection object property.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections1](SMO How to#SMO_VBCollections1)]  -->  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a><span data-ttu-id="fabf6-113">Visual C# でのコレクションを使用したオブジェクトの参照</span><span class="sxs-lookup"><span data-stu-id="fabf6-113">Referencing an Object by Using a Collection in Visual C#</span></span>  
 <span data-ttu-id="fabf6-114">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A> プロパティ、<xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> プロパティ、および <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> プロパティを使用して、列プロパティを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fabf6-114">This code example shows how to set a column property by using the <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, and <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> properties.</span></span> <span data-ttu-id="fabf6-115">これらのプロパティはコレクションを表現しており、オブジェクトの名前を指定するパラメーターと共に使用すれば、特定のオブジェクトを識別するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="fabf6-115">These properties represent collections, which can be used to identify a particular object when they are used with a parameter that specifies the name of the object.</span></span> <span data-ttu-id="fabf6-116"><xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> コレクション オブジェクト プロパティには、名前とスキーマが必要です。</span><span class="sxs-lookup"><span data-stu-id="fabf6-116">The name and the schema are required for the <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> collection object property.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a><span data-ttu-id="fabf6-117">Visual Basic でのコレクションのメンバーの反復処理</span><span class="sxs-lookup"><span data-stu-id="fabf6-117">Iterating Through the Members of a Collection in Visual Basic</span></span>  
 <span data-ttu-id="fabf6-118">このコード例では、<xref:Microsoft.AnalysisServices.Server.Databases%2A> コレクション プロパティを反復処理し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへのすべてのデータベース接続を表示します。</span><span class="sxs-lookup"><span data-stu-id="fabf6-118">This code example iterates through the <xref:Microsoft.AnalysisServices.Server.Databases%2A> collection property and displays all database connections to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections2](SMO How to#SMO_VBCollections2)]  -->  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a><span data-ttu-id="fabf6-119">Visual C# でのコレクションのメンバーの反復処理</span><span class="sxs-lookup"><span data-stu-id="fabf6-119">Iterating Through the Members of a Collection in Visual C#</span></span>  
 <span data-ttu-id="fabf6-120">このコード例では、<xref:Microsoft.AnalysisServices.Server.Databases%2A> コレクション プロパティを反復処理し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへのすべてのデータベース接続を表示します。</span><span class="sxs-lookup"><span data-stu-id="fabf6-120">This code example iterates through the <xref:Microsoft.AnalysisServices.Server.Databases%2A> collection property and displays all database connections to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
