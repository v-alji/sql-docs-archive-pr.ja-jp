---
title: スクリプト | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- dependencies [SMO]
- scripts [SMO]
ms.assetid: 13a35511-3987-426b-a3b7-3b2e83900dc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf46798597de021976cefa943a17500e773f9274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716173"
---
# <a name="scripting"></a><span data-ttu-id="a2a05-102">スクリプト</span><span class="sxs-lookup"><span data-stu-id="a2a05-102">Scripting</span></span>
  <span data-ttu-id="a2a05-103">SMO でのスクリプティングは、<xref:Microsoft.SqlServer.Management.Smo.Scripter> オブジェクトおよびその子オブジェクトによって、または個々のオブジェクトの `Script` メソッドによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-103">Scripting in SMO is controlled by the <xref:Microsoft.SqlServer.Management.Smo.Scripter> object and its child objects, or the `Script` method on individual objects.</span></span> <span data-ttu-id="a2a05-104">オブジェクトは、 <xref:Microsoft.SqlServer.Management.Smo.Scripter> のインスタンス上のオブジェクトに対する依存関係からのマッピングを制御し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-104">The <xref:Microsoft.SqlServer.Management.Smo.Scripter> object controls the mapping out of dependency relationships for objects on an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a2a05-105"><xref:Microsoft.SqlServer.Management.Smo.Scripter> オブジェクト、およびその子オブジェクトを使用する高度なスクリプティング プロセスには、次の 3 つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="a2a05-105">Advanced scripting by using the <xref:Microsoft.SqlServer.Management.Smo.Scripter> object and its child objects is a three phase process:</span></span>  
  
1.  <span data-ttu-id="a2a05-106">探索</span><span class="sxs-lookup"><span data-stu-id="a2a05-106">Discovery</span></span>  
  
2.  <span data-ttu-id="a2a05-107">リスト生成</span><span class="sxs-lookup"><span data-stu-id="a2a05-107">List generation</span></span>  
  
3.  <span data-ttu-id="a2a05-108">スクリプト生成</span><span class="sxs-lookup"><span data-stu-id="a2a05-108">Script generation</span></span>  
  
 <span data-ttu-id="a2a05-109">検索フェーズでは、<xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> オブジェクトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-109">The discovery phase uses the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> object.</span></span> <span data-ttu-id="a2a05-110">オブジェクトの URN リストが指定されている場合、<xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> メソッドは、URN リスト内のオブジェクトに対応する <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="a2a05-110">Given an URN list of objects, the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> object returns a <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> object for the objects in the URN list.</span></span> <span data-ttu-id="a2a05-111">ブール型の*Fparents*パラメーターを使用して、指定したオブジェクトの親または子を検出するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="a2a05-111">The Boolean *fParents* parameter is used to select whether the parents or the children of the specified object are to be discovered.</span></span> <span data-ttu-id="a2a05-112">依存関係ツリーはこの段階で変更することができます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-112">The dependency tree can be modified at this stage.</span></span>  
  
 <span data-ttu-id="a2a05-113">リスト生成フェーズでは、このツリーが渡され、結果リストが返されます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-113">In the list generation phase, the tree is passed in and the resulting list is returned.</span></span> <span data-ttu-id="a2a05-114">このオブジェクト リストは記述順であり、変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-114">This object list is in scripting order and can be manipulated.</span></span>  
  
 <span data-ttu-id="a2a05-115">リスト生成フェーズでは、<xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> メソッドを使用して <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> を返します。</span><span class="sxs-lookup"><span data-stu-id="a2a05-115">The list generation phases use the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> method to return a <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>.</span></span> <span data-ttu-id="a2a05-116"><xref:Microsoft.SqlServer.Management.Smo.DependencyTree> はこの段階で変更することができます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-116">The <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> can be modified at this stage.</span></span>  
  
 <span data-ttu-id="a2a05-117">3 番目の最後のフェーズでは、指定されたリストとスクリプティング オプションを使用してスクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-117">In the third and final phase, a script is generated with the specified list and scripting options.</span></span> <span data-ttu-id="a2a05-118">結果は <xref:System.Collections.Specialized.StringCollection> システム オブジェクトとして返されます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-118">The result is returned as a <xref:System.Collections.Specialized.StringCollection> system object.</span></span> <span data-ttu-id="a2a05-119">このフェーズで、<xref:Microsoft.SqlServer.Management.Smo.DependencyTree> オブジェクトの Items コレクションおよび <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> や <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A> などのプロパティから、依存オブジェクト名が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="a2a05-119">In this phase the dependent object names are then extracted from the Items collection of the <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> object and properties such as <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> and <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2a05-120">例</span><span class="sxs-lookup"><span data-stu-id="a2a05-120">Example</span></span>  
 <span data-ttu-id="a2a05-121">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2a05-121">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="a2a05-122">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2a05-122">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
 <span data-ttu-id="a2a05-123">このコード例には、System.Collections.Specialized 名前空間の `Imports` ステートメントが必要です。</span><span class="sxs-lookup"><span data-stu-id="a2a05-123">This code example requires an `Imports` statement for the System.Collections.Specialized namespace.</span></span> <span data-ttu-id="a2a05-124">アプリケーションの宣言の前、かつ他の Imports ステートメントの後に、次のステートメントを挿入します。</span><span class="sxs-lookup"><span data-stu-id="a2a05-124">Insert this with the other Imports statements, before any declarations in the application.</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
Imports System.Collections.Specialized  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-basic"></a><span data-ttu-id="a2a05-125">Visual Basic でデータベースの依存関係のスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="a2a05-125">Scripting Out the Dependencies for a Database in Visual Basic</span></span>  
 <span data-ttu-id="a2a05-126">このコード例では、依存関係を検出する方法と、リストを反復処理して結果を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2a05-126">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
  
Public Class A  
   Public Shared Sub Main()  
      ' database name  
      Dim dbName As [String] = "AdventureWorksLT2012"   ' database name  
  
      ' Connect to the local, default instance of SQL Server.   
      Dim srv As New Server()  
  
      ' Reference the database.    
      Dim db As Database = srv.Databases(dbName)  
  
      ' Define a Scripter object and set the required scripting options.   
      Dim scrp As New Scripter(srv)  
      scrp.Options.ScriptDrops = False  
      scrp.Options.WithDependencies = True  
      scrp.Options.Indexes = True   ' To include indexes  
      scrp.Options.DriAllConstraints = True   ' to include referential constraints in the script  
  
      ' Iterate through the tables in database and script each one. Display the script.  
      For Each tb As Table In db.Tables  
         ' check if the table is not a system table  
         If tb.IsSystemObject = False Then  
            Console.WriteLine("-- Scripting for table " + tb.Name)  
  
            ' Generating script for table tb  
            Dim sc As System.Collections.Specialized.StringCollection = scrp.Script(New Urn() {tb.Urn})  
            For Each st As String In sc  
               Console.WriteLine(st)  
            Next  
            Console.WriteLine("--")  
         End If  
      Next  
   End Sub  
End Class  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-c"></a><span data-ttu-id="a2a05-127">Visual C# でデータベースの依存関係のスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="a2a05-127">Scripting Out the Dependencies for a Database in Visual C#</span></span>  
 <span data-ttu-id="a2a05-128">このコード例では、依存関係を検出する方法と、リストを反復処理して結果を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2a05-128">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
  
public class A {  
   public static void Main() {   
      String dbName = "AdventureWorksLT2012"; // database name  
  
      // Connect to the local, default instance of SQL Server.   
      Server srv = new Server();  
  
      // Reference the database.    
      Database db = srv.Databases[dbName];  
  
      // Define a Scripter object and set the required scripting options.   
      Scripter scrp = new Scripter(srv);  
      scrp.Options.ScriptDrops = false;  
      scrp.Options.WithDependencies = true;  
      scrp.Options.Indexes = true;   // To include indexes  
      scrp.Options.DriAllConstraints = true;   // to include referential constraints in the script  
  
      // Iterate through the tables in database and script each one. Display the script.     
      foreach (Table tb in db.Tables) {   
         // check if the table is not a system table  
         if (tb.IsSystemObject == false) {  
            Console.WriteLine("-- Scripting for table " + tb.Name);  
  
            // Generating script for table tb  
            System.Collections.Specialized.StringCollection sc = scrp.Script(new Urn[]{tb.Urn});  
            foreach (string st in sc) {  
               Console.WriteLine(st);  
            }  
            Console.WriteLine("--");  
         }  
      }   
   }  
}  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-powershell"></a><span data-ttu-id="a2a05-129">PowerShell でデータベースの依存関係のスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="a2a05-129">Scripting Out the Dependencies for a Database in PowerShell</span></span>  
 <span data-ttu-id="a2a05-130">このコード例では、依存関係を検出する方法と、リストを反復処理して結果を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2a05-130">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
# Create a Scripter object and set the required scripting options.  
$scrp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Scripter -ArgumentList (Get-Item .)  
$scrp.Options.ScriptDrops = $false  
$scrp.Options.WithDependencies = $true  
$scrp.Options.IncludeIfNotExists = $true  
  
# Set the path context to the tables in AdventureWorks2012.  
CD Databases\AdventureWorks2012\Tables  
  
foreach ($Item in Get-ChildItem)  
 {    
 $scrp.Script($Item)  
 }  
```  
