---
title: プログラムを使用したパッケージ作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: e44bcc70-32d3-43e8-a84b-29aef819d5d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1159784fc95dd86d9d33c4354291cc7c52812982
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715654"
---
# <a name="creating-a-package-programmatically"></a><span data-ttu-id="35d99-102">プログラムを使用したパッケージ作成</span><span class="sxs-lookup"><span data-stu-id="35d99-102">Creating a Package Programmatically</span></span>
  <span data-ttu-id="35d99-103"><xref:Microsoft.SqlServer.Dts.Runtime.Package> オブジェクトは、[!INCLUDE[ssIS](../../includes/ssis-md.md)] プロジェクトによるソリューションで、他のすべてのオブジェクトの上位に位置するコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="35d99-103">The <xref:Microsoft.SqlServer.Dts.Runtime.Package> object is the top-level container for all other objects in an [!INCLUDE[ssIS](../../includes/ssis-md.md)] project solution.</span></span> <span data-ttu-id="35d99-104">パッケージは、トップレベルのコンテナーとして、最初に作成されるオブジェクトです。それ以降のオブジェクトはパッケージに追加され、パッケージのコンテキスト内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="35d99-104">As the top-level container, the package is the first object created, and subsequent objects are added to it, and then executed within the context of the package.</span></span> <span data-ttu-id="35d99-105">パッケージ自体は、データの移動または変換を行いません。</span><span class="sxs-lookup"><span data-stu-id="35d99-105">The package itself does not move or transform data.</span></span> <span data-ttu-id="35d99-106">パッケージは、格納しているタスクに依存して作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="35d99-106">The package relies on the tasks it contains to perform the work.</span></span> <span data-ttu-id="35d99-107">タスクは、パッケージが実行する作業のほとんどを実行し、パッケージの機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="35d99-107">Tasks perform most of the work performed by a package, and define the functionality of a package.</span></span> <span data-ttu-id="35d99-108">パッケージを作成して実行するには、わずか 3 行のコードを必要とするだけですが、さまざまなタスクおよび <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトをパッケージに追加して、機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="35d99-108">A package is created and executed with just three lines of code, but various tasks and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects are added to give additional functionality to your package.</span></span> <span data-ttu-id="35d99-109">このセクションでは、プログラムによってパッケージを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35d99-109">This section discusses how to programmatically create a package.</span></span> <span data-ttu-id="35d99-110">タスクまたは <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> の作成方法についての説明は行いません。</span><span class="sxs-lookup"><span data-stu-id="35d99-110">It does not provide information about how to create the tasks or the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.</span></span> <span data-ttu-id="35d99-111">これらについては、後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="35d99-111">These are covered in later sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35d99-112">例</span><span class="sxs-lookup"><span data-stu-id="35d99-112">Example</span></span>  
 <span data-ttu-id="35d99-113">Visual Studio IDE を使用してコードを記述するには、Microsoft.SqlServer.Dts.Runtime に対して `using` ステートメント (Visual Basic .NET では `Imports`) を作成するために、Microsoft.SqlServer.ManagedDTS.DLL を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35d99-113">To write code using the Visual Studio IDE, a reference to Microsoft.SqlServer.ManagedDTS.DLL is required in order to create a `using` statement (`Imports` in Visual Basic .NET) to the Microsoft.SqlServer.Dts.Runtime.</span></span> <span data-ttu-id="35d99-114">次のコード例では、空のパッケージを作成しています。</span><span class="sxs-lookup"><span data-stu-id="35d99-114">The following code sample demonstrates creating an empty package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package;  
      package = new Package();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package  
    package = New Package  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="35d99-115">サンプルをコンパイルして実行するには、Visual Studio で F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="35d99-115">To compile and run the sample, press F5 in Visual Studio.</span></span> <span data-ttu-id="35d99-116">C# コンパイラ **csc.exe** を使用してコードを作成し、コマンド プロンプトからコンパイルするには、次のコマンドおよびファイル参照を使用します。 *\<filename>* は .cs または .vb ファイルの名前に置き換えて、任意の *\<outputfilename>* を付けます。</span><span class="sxs-lookup"><span data-stu-id="35d99-116">To build the code using the C# compiler, **csc.exe**, at the command prompt to compile, use the following command and file references, replacing the *\<filename>* with the name of the .cs or .vb file, and giving it an *\<outputfilename>* of your choice.</span></span>  
  
 <span data-ttu-id="35d99-117">**csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span><span class="sxs-lookup"><span data-stu-id="35d99-117">**csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span></span>  
  
 <span data-ttu-id="35d99-118">Visual Basic .NET コンパイラ **vbc.exe** を使用してコードを作成し、コマンド プロンプトからコンパイルするには、次のコマンドおよびファイル参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="35d99-118">To build the code using the Visual Basic .NET compiler, **vbc.exe**, at the command prompt to compile, use the following command and file references.</span></span>  
  
 <span data-ttu-id="35d99-119">**vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span><span class="sxs-lookup"><span data-stu-id="35d99-119">**vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span></span>  
  
 <span data-ttu-id="35d99-120">また、ディスク上、ファイル システム、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に保存されている既存のパッケージを読み込むことにより、パッケージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="35d99-120">You can also create a package by loading an existing package that was saved on disk, in the file system, or to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="35d99-121">その場合、<xref:Microsoft.SqlServer.Dts.Runtime.Application> オブジェクトが最初に作成され、そのパッケージ オブジェクトが、オーバーロードされた次のアプリケーションのメソッドのいずれかによって設定される点が異なります。そのメソッドとは、フラット ファイル用の `LoadPackage`、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に保存されているパッケージ用の `LoadFromSQLServer`、またはファイル システムに保存されているパッケージ用の <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> です。</span><span class="sxs-lookup"><span data-stu-id="35d99-121">The difference is that the <xref:Microsoft.SqlServer.Dts.Runtime.Application> object is first created, and then the package object is filled by one of the Application's overloaded methods: `LoadPackage` for flat files, `LoadFromSQLServer` for packages saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> for packages saved to the file system.</span></span> <span data-ttu-id="35d99-122">次の例では、ディスクから既存のパッケージを読み込み、パッケージの複数のプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="35d99-122">The following example loads an existing package from disk, and then views several properties on the package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class ApplicationTests  
  {  
    static void Main(string[] args)  
    {  
      // The variable pkg points to the location of the  
      // ExecuteProcess package sample that was installed with  
      // the SSIS samples.  
      string pkg = @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx";  
  
      Application app = new Application();  
      Package p = app.LoadPackage(pkg, null);  
  
      // Now that the package is loaded, we can query on  
      // its properties.  
      int n = p.Configurations.Count;  
      DtsProperty p2 = p.Properties["VersionGUID"];  
      DTSProtectionLevel pl = p.ProtectionLevel;  
  
      Console.WriteLine("Number of configurations = " + n.ToString());  
      Console.WriteLine("VersionGUID = " + (string)p2.GetValue(p));  
      Console.WriteLine("ProtectionLevel = " + pl.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module ApplicationTests  
  
  Sub Main()  
  
    ' The variable pkg points to the location of the  
    ' ExecuteProcess package sample that was installed with  
    ' the SSIS samples.  
    Dim pkg As String = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx"  
  
    Dim app As Application = New Application()  
    Dim p As Package = app.LoadPackage(pkg, Nothing)  
  
    ' Now that the package is loaded, we can query on  
    ' its properties.  
    Dim n As Integer = p.Configurations.Count  
    Dim p2 As DtsProperty = p.Properties("VersionGUID")  
    Dim pl As DTSProtectionLevel = p.ProtectionLevel  
  
    Console.WriteLine("Number of configurations = " & n.ToString())  
    Console.WriteLine("VersionGUID = " & CType(p2.GetValue(p), String))  
    Console.WriteLine("ProtectionLevel = " & pl.ToString())  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="35d99-123">**サンプル出力:**</span><span class="sxs-lookup"><span data-stu-id="35d99-123">**Sample Output:**</span></span>  
  
 `Number of configurations = 2`  
  
 `VersionGUID = {09016682-89B8-4406-AAC9-AF1E527FF50F}`  
  
 `ProtectionLevel = DontSaveSensitive`  
  
## <a name="external-resources"></a><span data-ttu-id="35d99-124">外部リソース</span><span class="sxs-lookup"><span data-stu-id="35d99-124">External Resources</span></span>  
  
-   <span data-ttu-id="35d99-125">blogs.msdn.com のブログ「[API Sample - OleDB source and OleDB destination](https://go.microsoft.com/fwlink/?LinkId=220824)」(API サンプル – OleDB ソースと OleDB 変換先)</span><span class="sxs-lookup"><span data-stu-id="35d99-125">Blog entry, [API Sample - OleDB source and OleDB destination](https://go.microsoft.com/fwlink/?LinkId=220824), on blogs.msdn.com.</span></span>  
  
-   <span data-ttu-id="35d99-126">blogs.msdn.com のブログ「[EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223)」(EzAPI - SQL Server 2012 用の更新)</span><span class="sxs-lookup"><span data-stu-id="35d99-126">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="35d99-127">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="35d99-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="35d99-128">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="35d99-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="35d99-129">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="35d99-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="35d99-130">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="35d99-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d99-131">参照</span><span class="sxs-lookup"><span data-stu-id="35d99-131">See Also</span></span>  
 [<span data-ttu-id="35d99-132">プログラムによるタスクの追加</span><span class="sxs-lookup"><span data-stu-id="35d99-132">Adding Tasks Programmatically</span></span>](../building-packages-programmatically/adding-tasks-programmatically.md)  
  
  
