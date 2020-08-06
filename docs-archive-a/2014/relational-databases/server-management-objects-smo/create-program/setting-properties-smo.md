---
title: プロパティの設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SMO [SQL Server], properties
- SQL Server Management Objects, properties
- properties [SMO]
ms.assetid: 342569ba-d2f7-44d2-8f3f-ae9c701c7f0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: de381f8e4e9dfe9f6590638742e988f866ccabdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719802"
---
# <a name="setting-properties"></a><span data-ttu-id="c1cb2-102">プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="c1cb2-102">Setting Properties</span></span>
  <span data-ttu-id="c1cb2-103">プロパティとは、オブジェクトに関する説明情報を格納する値のことです。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-103">Properties are values that store descriptive information about the object.</span></span> <span data-ttu-id="c1cb2-104">たとえば、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成オプションは、オブジェクトのプロパティによって表され <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-104">For example, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration options are represented by the <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> object's properties.</span></span> <span data-ttu-id="c1cb2-105">プロパティは、直接、またはプロパティ コレクションを使用して間接的にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-105">Properties can be accessed either directly or indirectly by using the property collection.</span></span> <span data-ttu-id="c1cb2-106">プロパティへの直接アクセス時には、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-106">Accessing properties directly uses the following syntax:</span></span>  
  
 `objInstance.PropertyName`  
  
 <span data-ttu-id="c1cb2-107">プロパティ値は、そのプロパティが読み取り/書き込みアクセスまたは読み取り専用アクセスのどちらであるかに応じて、変更または取得を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-107">A property value can be modified or retrieved depending on whether the property has read/write access or read-only access.</span></span> <span data-ttu-id="c1cb2-108">また、オブジェクトを作成する前に、特定のプロパティを設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-108">It is also necessary to set certain properties before an object can be created.</span></span> <span data-ttu-id="c1cb2-109">詳細については、SMO 参考資料で特定のオブジェクトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-109">For more information, see the SMO reference for the particular object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1cb2-110">子オブジェクトのコレクションは、オブジェクトのプロパティとして表現されます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-110">Collections of child objects appear as the property of an object.</span></span> <span data-ttu-id="c1cb2-111">たとえば、`Tables` コレクションは、`Server` オブジェクトのプロパティとなります。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-111">For example, the `Tables` collection is a property of a `Server` object.</span></span> <span data-ttu-id="c1cb2-112">詳しくは、「 [Using Collections](using-collections.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-112">For more information, see [Using Collections](using-collections.md).</span></span>  
  
 <span data-ttu-id="c1cb2-113">オブジェクトのプロパティは、Properties コレクションのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-113">The properties of an object are members of the Properties collection.</span></span> <span data-ttu-id="c1cb2-114">Properties コレクションを使用して、オブジェクトの各プロパティを反復処理することができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-114">The Properties collection can be used to iterate through every property of an object.</span></span>  
  
 <span data-ttu-id="c1cb2-115">次の理由によって、プロパティを使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-115">Sometimes a property is not available for the following reasons:</span></span>  
  
-   <span data-ttu-id="c1cb2-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の以前のバージョンで、新しい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]機能を表すプロパティにアクセスしようとするなど、サーバーのバージョンがプロパティをサポートしていない場合。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-116">The server version does not support the property, such as if you try to access a property that represents a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] feature on an older version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c1cb2-117">インストールされていない [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コンポーネントを表すプロパティにアクセスしようとするなど、サーバーがプロパティのデータを提供しない場合。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-117">The server does not provide data for the property, such as if you try to access a property that represents a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] component that is not installed.</span></span>  
  
 <span data-ttu-id="c1cb2-118"><xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> および <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> の SMO 例外をキャッチすることによって、これらの状況に対処することができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-118">You can handle these circumstances by catching the <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> and the <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> SMO exceptions.</span></span>  
  
## <a name="setting-default-initialization-fields"></a><span data-ttu-id="c1cb2-119">既定の初期化フィールドの設定</span><span class="sxs-lookup"><span data-stu-id="c1cb2-119">Setting Default Initialization Fields</span></span>  
 <span data-ttu-id="c1cb2-120">SMO は、オブジェクトの取得時に最適化を行います。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-120">SMO performs an optimization when retrieving objects.</span></span> <span data-ttu-id="c1cb2-121">最適化によって、次の状態の間で自動的にスケーリングを行うことによって読み込まれるプロパティ数を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-121">The optimization minimizes the number of properties loaded by automatically scaling between the following states:</span></span>  
  
1.  <span data-ttu-id="c1cb2-122">部分的読み込み。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-122">Partially loaded.</span></span> <span data-ttu-id="c1cb2-123">オブジェクトへの最初の参照時には、最少限のプロパティ (Name や Schema など) のみが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-123">When an object is first referenced it has a minimum of properties available (such as Name and Schema).</span></span>  
  
2.  <span data-ttu-id="c1cb2-124">完全読み込み。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-124">Fully loaded.</span></span> <span data-ttu-id="c1cb2-125">いずれかのプロパティが参照されたとき、すぐに読み込まれた残りのプロパティが初期化されて使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-125">When any property is referenced, the remaining properties that are quick to load, are initialized and are made available.</span></span>  
  
3.  <span data-ttu-id="c1cb2-126">大量のメモリを使用するプロパティ。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-126">Properties that use lots of memory.</span></span> <span data-ttu-id="c1cb2-127">これ以外の、多くのメモリを使用し、<xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> プロパティ値 (<xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A> など) の値が true であるプロパティは読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-127">The remaining unavailable properties use lots of memory and have an <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> property value of true (such as <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>).</span></span> <span data-ttu-id="c1cb2-128">これらのプロパティは、明示的に参照された場合にのみ読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-128">These properties are loaded only when specifically referenced.</span></span>  
  
 <span data-ttu-id="c1cb2-129">部分的に読み込まれた状態で提供されたプロパティだけでなく、それ以外のプロパティもアプリケーションによってフェッチされる場合、これらの追加のプロパティを取得するクエリが送信され、完全に読み込まれた状態にスケール アップされます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-129">If your application does fetch extra properties, besides the ones provided in the partially loaded state, it submits a query to retrieve these extra properties and scales up to the fully loaded state.</span></span> <span data-ttu-id="c1cb2-130">これにより、クライアントとサーバーの間に不要なトラフィックが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-130">This can cause unnecessary traffic between the client and server.</span></span> <span data-ttu-id="c1cb2-131"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> メソッドを呼び出すことにより、さらに最適化を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-131">More optimization can be achieved by calling the <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method.</span></span> <span data-ttu-id="c1cb2-132"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> メソッドを使用すると、オブジェクトの初期化時に読み込まれるプロパティを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-132">The <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method allows specification of the properties that are loaded when the object is initialized.</span></span>  
  
 <span data-ttu-id="c1cb2-133"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> メソッドでは、アプリケーションの残り部分に対して、またはリセットされるまでの、プロパティの読み込み動作を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-133">The <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method sets the property loading behavior for the rest of application or until it is reset.</span></span> <span data-ttu-id="c1cb2-134"><xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> メソッドを使用して、元の動作を保存し、必要に応じて復元することができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-134">You can save the original behavior by using the <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> method and restore it as required.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c1cb2-135">例</span><span class="sxs-lookup"><span data-stu-id="c1cb2-135">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="getting-and-setting-a-property-in-visual-basic"></a><span data-ttu-id="c1cb2-136">Visual Basic でのプロパティの取得および設定</span><span class="sxs-lookup"><span data-stu-id="c1cb2-136">Getting and Setting a Property in Visual Basic</span></span>  
 <span data-ttu-id="c1cb2-137">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Information> プロパティを取得する方法と、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> プロパティの <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 列挙型の `ExecuteSql` メンバーに設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-137">This code example shows how to get the <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Information> object and how to set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property to the `ExecuteSql` member of the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> enumerated type.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties1](SMO How to#SMO_VBProperties1)]  -->  
  
## <a name="getting-and-setting-a-property-in-visual-c"></a><span data-ttu-id="c1cb2-138">Visual C# でのプロパティの取得および設定</span><span class="sxs-lookup"><span data-stu-id="c1cb2-138">Getting and Setting a Property in Visual C#</span></span>  
 <span data-ttu-id="c1cb2-139">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Information> プロパティを取得する方法と、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> プロパティの <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 列挙型の `ExecuteSql` メンバーに設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-139">This code example shows how to get the <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Information> object and how to set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property to the `ExecuteSql` member of the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> enumerated type.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Get a property.   
Console.WriteLine(srv.Information.Version);   
//Set a property.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-basic"></a><span data-ttu-id="c1cb2-140">Visual Basic でのオブジェクト作成前のさまざまなプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="c1cb2-140">Setting Various Properties Before an Object is Created in Visual Basic</span></span>  
 <span data-ttu-id="c1cb2-141">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> オブジェクトを作成する前に、<xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Table> プロパティを直接設定する方法、および列の作成と追加を行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-141">This code example shows how to directly set the <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Table> object, and how to create and add columns before you create the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties2](SMO How to#SMO_VBProperties2)]  -->  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-c"></a><span data-ttu-id="c1cb2-142">Visual C# でのオブジェクト作成前のさまざまなプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="c1cb2-142">Setting Various Properties Before an Object is Created in Visual C#</span></span>  
 <span data-ttu-id="c1cb2-143">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> オブジェクトを作成する前に、<xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Table> プロパティを直接設定する方法、および列の作成と追加を行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-143">This code example shows how to directly set the <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Table> object, and how to create and add columns before you create the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Create a new table in the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
Table tb;   
//Specify the parent database, table schema, and the table name in the constructor.   
tb = new Table(db, "Test_Table", "HumanResources");   
//Add columns because the table requires columns before it can be created.   
Column c1;   
//Specify the parent table, the column name, and data type in the constructor.   
c1 = new Column(tb, "ID", DataType.Int);   
tb.Columns.Add(c1);   
c1.Nullable = false;   
c1.Identity = true;   
c1.IdentityIncrement = 1;   
c1.IdentitySeed = 0;   
Column c2;   
c2 = new Column(tb, "Name", DataType.NVarChar(100));   
c2.Nullable = false;   
tb.Columns.Add(c2);   
tb.AnsiNullsStatus = true;   
//Create the table on the instance of SQL Server.   
tb.Create();   
}  
```  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-basic"></a><span data-ttu-id="c1cb2-144">Visual Basic でのオブジェクトのすべてのプロパティの反復処理</span><span class="sxs-lookup"><span data-stu-id="c1cb2-144">Iterating Through All Properties of an Object in Visual Basic</span></span>  
 <span data-ttu-id="c1cb2-145">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> オブジェクトの `Properties` コレクションが反復処理され、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の出力画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-145">This code example iterates through the `Properties` collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object and displays them on the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Output screen.</span></span>  
  
 <span data-ttu-id="c1cb2-146">この例では、<xref:Microsoft.SqlServer.Management.Smo.Property> オブジェクトは [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] のキーワードでもあるため、角かっこで囲まれています。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-146">In the example, the <xref:Microsoft.SqlServer.Management.Smo.Property> object has been put in square parentheses because it is also a [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] keyword.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties3](SMO How to#SMO_VBProperties3)]  -->  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-c"></a><span data-ttu-id="c1cb2-147">Visual C# でのオブジェクトのすべてのプロパティの反復処理</span><span class="sxs-lookup"><span data-stu-id="c1cb2-147">Iterating Through All Properties of an Object in Visual C#</span></span>  
 <span data-ttu-id="c1cb2-148">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> オブジェクトの `Properties` コレクションが反復処理され、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の出力画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-148">This code example iterates through the `Properties` collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object and displays them on the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Output screen.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Set properties on the uspGetEmployeedManagers stored procedure on the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
StoredProcedure sp;   
sp = db.StoredProcedures("uspGetEmployeeManagers");   
sp.AnsiNullsStatus = false;   
sp.QuotedIdentifierStatus = false;   
//Iterate through the properties of the stored procedure and display.   
  Property p;   
  foreach ( p in sp.Properties) {   
    Console.WriteLine(p.Name + p.Value);   
  }   
}  
```  
  
## <a name="setting-default-initialization-fields-in-visual-basic"></a><span data-ttu-id="c1cb2-149">Visual Basic での既定の初期化フィールドの設定</span><span class="sxs-lookup"><span data-stu-id="c1cb2-149">Setting Default Initialization Fields in Visual Basic</span></span>  
 <span data-ttu-id="c1cb2-150">このコード例では、SMO プログラムで初期化されるオブジェクト プロパティの数を最小にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-150">This code example shows how to minimize the number of object properties initialized in an SMO program.</span></span> <span data-ttu-id="c1cb2-151"><xref:System.Collections.Specialized.StringCollection> オブジェクトを使用するには、`using System.Collections.Specialized` ステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-151">You have to include the `using System.Collections.Specialized`; statement to use the <xref:System.Collections.Specialized.StringCollection> object.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="c1cb2-152">を使用すれば、この最適化によって [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに送信されるステートメントの数を比較することができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-152">can be used to compare the number statements sent to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with this optimization.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaultInitFields1](SMO How to#SMO_VBDefaultInitFields1)]  -->  
  
## <a name="setting-default-initialization-fields-in-visual-c"></a><span data-ttu-id="c1cb2-153">Visual C# での既定の初期化フィールドの設定</span><span class="sxs-lookup"><span data-stu-id="c1cb2-153">Setting Default Initialization Fields in Visual C#</span></span>  
 <span data-ttu-id="c1cb2-154">このコード例では、SMO プログラムで初期化されるオブジェクト プロパティの数を最小にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-154">This code example shows how to minimize the number of object properties initialized in an SMO program.</span></span> <span data-ttu-id="c1cb2-155"><xref:System.Collections.Specialized.StringCollection> オブジェクトを使用するには、`using System.Collections.Specialized` ステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-155">You have to include the `using System.Collections.Specialized`; statement to use the <xref:System.Collections.Specialized.StringCollection> object.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="c1cb2-156">を使用すれば、この最適化によって [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに送信されるステートメントの数を比較することができます。</span><span class="sxs-lookup"><span data-stu-id="c1cb2-156">can be used to compare the number statements sent to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with this optimization.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Assign the Table object type to a System.Type object variable.   
Table tb;   
Type typ;   
tb = new Table();   
typ = tb.GetType;   
//Assign the current default initialization fields for the Table object type to a   
//StringCollection object variable.   
StringCollection sc;   
sc = srv.GetDefaultInitFields(typ);   
//Set the default initialization fields for the Table object type to the CreateDate property.   
srv.SetDefaultInitFields(typ, "CreateDate");   
//Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.   
   //Note that the improvement in performance can be viewed in SQL Server Profiler.   
foreach ( tb in db.Tables) {   
   Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate);   
}   
//Set the default initialization fields for the Table object type back to the original settings.   
srv.SetDefaultInitFields(typ, sc);   
}  
```  
  
  
