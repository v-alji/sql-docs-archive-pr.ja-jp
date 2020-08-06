---
title: プログラムによるローカル パッケージの読み込みと実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Integration Services packages, running
- events [Integration Services], capturing
- packages [Integration Services], running
- loading packages programmatically
- Visual Basic [Integration Services]
- running packages [Integration Services]
- programmatically load and run packages [SSIS]
ms.assetid: 2f9fc1a8-a001-4c54-8c64-63b443725422
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a29faf623c02fea4fd8722c235f595f0fe4492e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713234"
---
# <a name="loading-and-running-a-local-package-programmatically"></a><span data-ttu-id="6bd48-102">プログラムによるローカル パッケージの読み込みと実行</span><span class="sxs-lookup"><span data-stu-id="6bd48-102">Loading and Running a Local Package Programmatically</span></span>
  <span data-ttu-id="6bd48-103">「[パッケージの実行](../packages/run-integration-services-ssis-packages.md)」で説明されている方法を使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを必要に応じて実行したり、事前に定義した時刻に実行したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6bd48-103">You can run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages as needed or at predetermined times by using the methods described in [Running Packages](../packages/run-integration-services-ssis-packages.md).</span></span> <span data-ttu-id="6bd48-104">また、数行のコードを記述するだけで、Windows フォーム アプリケーション、コンソール アプリケーション、ASP.NET Web フォームや Web サービス、または Windows サービスなどのカスタム アプリケーションから、パッケージを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="6bd48-104">However, with only a few lines of code, you can also run a package from a custom application such as a Windows Forms application, a console application, an ASP.NET Web form or Web service, or a Windows service.</span></span>  
  
 <span data-ttu-id="6bd48-105">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="6bd48-105">This topic discusses:</span></span>  
  
-   <span data-ttu-id="6bd48-106">プログラムによるパッケージの読み込み</span><span class="sxs-lookup"><span data-stu-id="6bd48-106">Loading a package programmatically</span></span>  
  
-   <span data-ttu-id="6bd48-107">プログラムによるパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="6bd48-107">Running a package programmatically</span></span>  
  
 <span data-ttu-id="6bd48-108">このトピックでパッケージを読み込み、実行するために使用するすべてのメソッドには、`Microsoft.SqlServer.ManagedDTS` アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="6bd48-108">All of the methods used in this topic to load and run packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="6bd48-109">この参照を新しいプロジェクトに追加した後、`using` ステートメントまたは `Imports` ステートメントを使用して <xref:Microsoft.SqlServer.Dts.Runtime> 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="6bd48-109">After adding the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
## <a name="loading-a-package-programmatically"></a><span data-ttu-id="6bd48-110">プログラムによるパッケージの読み込み</span><span class="sxs-lookup"><span data-stu-id="6bd48-110">Loading a Package Programmatically</span></span>  
 <span data-ttu-id="6bd48-111">プログラムによってローカル コンピューターでパッケージを読み込むには、パッケージがローカルまたはリモートのどちらに保存されているかに関係なく、次のいずれかの方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bd48-111">To load a package programmatically on the local computer, whether the package is stored locally or remotely, call one of the following methods:</span></span>  
  
|<span data-ttu-id="6bd48-112">保存先</span><span class="sxs-lookup"><span data-stu-id="6bd48-112">Storage Location</span></span>|<span data-ttu-id="6bd48-113">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="6bd48-113">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6bd48-114">ファイル</span><span class="sxs-lookup"><span data-stu-id="6bd48-114">File</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>|  
|<span data-ttu-id="6bd48-115">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="6bd48-115">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6bd48-116">SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドは、"."、localhost、またはローカル サーバーのサーバー名のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6bd48-116">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store only support ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="6bd48-117">"(local)" は使用できません。</span><span class="sxs-lookup"><span data-stu-id="6bd48-117">You cannot use "(local)".</span></span>  
  
## <a name="running-a-package-programmatically"></a><span data-ttu-id="6bd48-118">プログラムによるパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="6bd48-118">Running a Package Programmatically</span></span>  
 <span data-ttu-id="6bd48-119">ローカル コンピューターでマネージド コードを使用して、パッケージを実行するカスタム アプリケーションを開発するには、次の方法が必要です。</span><span class="sxs-lookup"><span data-stu-id="6bd48-119">Developing a custom application in managed code that runs a package on the local computer requires the following approach.</span></span> <span data-ttu-id="6bd48-120">ここにまとめた手順は、後のサンプル コンソール アプリケーションで示します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-120">The steps summarized here are demonstrated in the sample console application that follows.</span></span>  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically"></a><span data-ttu-id="6bd48-121">プログラムによってローカル コンピューターでパッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="6bd48-121">To run a package on the local computer programmatically</span></span>  
  
1.  <span data-ttu-id="6bd48-122">Visual Studio 開発環境を起動し、任意の開発言語で、新しいアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-122">Start the Visual Studio development environment, and create a new application in your preferred development language.</span></span> <span data-ttu-id="6bd48-123">この例ではコンソール アプリケーションを使用しますが、Windows フォーム アプリケーション、ASP.NET Web フォームや Web サービス、または Windows サービスからパッケージを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="6bd48-123">This example uses a console application; however you can also run a package from a Windows Forms application, an ASP.NET Web form or Web service, or a Windows service.</span></span>  
  
2.  <span data-ttu-id="6bd48-124">**[プロジェクト]** メニューの **[参照の追加]** をクリックし、**Microsoft.SqlServer.ManagedDTS.dll** への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-124">On the **Project** menu, click **Add Reference** and add a reference to **Microsoft.SqlServer.ManagedDTS.dll**.</span></span> <span data-ttu-id="6bd48-125">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bd48-125">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="6bd48-126">Visual Basic `Imports` ステートメントまたは C# ステートメントを使用して、 `using` 名前空間をインポート**Microsoft.SqlServer.Dts.Runtime**します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-126">Use the Visual Basic `Imports` statement or the C# `using` statement to import the **Microsoft.SqlServer.Dts.Runtime** namespace.</span></span>  
  
4.  <span data-ttu-id="6bd48-127">メイン ルーチンに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-127">Add the following code in the main routine.</span></span> <span data-ttu-id="6bd48-128">完成したコンソール アプリケーションは、たとえば次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bd48-128">The completed console application should look like the following example.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6bd48-129">このサンプル コードは、<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> メソッドを使用してファイル システムからパッケージを読み込む方法を示していますが、</span><span class="sxs-lookup"><span data-stu-id="6bd48-129">The sample code demonstrates loading the package from the file system by using the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> method.</span></span> <span data-ttu-id="6bd48-130"><xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> メソッドを呼び出して MSDB データベースからパッケージを読み込んだり、<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> メソッドを呼び出して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ ストアからパッケージを読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="6bd48-130">However you can also load the package from the MSDB database by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> method, or from the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package store by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> method.</span></span>  
  
5.  <span data-ttu-id="6bd48-131">プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-131">Run the project.</span></span> <span data-ttu-id="6bd48-132">このサンプル コードでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサンプルと共にインストールされている CalculatedColumns サンプル パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-132">The sample code executes the CalculatedColumns sample package that is installed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="6bd48-133">パッケージの実行結果がコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bd48-133">The result of package execution is displayed in the console window.</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="6bd48-134">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="6bd48-134">Sample Code</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, Nothing)  
    pkgResults = pkg.Execute()  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, null);  
      pkgResults = pkg.Execute();  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="capturing-events-from-a-running-package"></a><span data-ttu-id="6bd48-135">実行中のパッケージからのイベントのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="6bd48-135">Capturing Events from a Running Package</span></span>  
 <span data-ttu-id="6bd48-136">上記のサンプルのようにプログラムを使用してパッケージを実行するときは、パッケージの実行時に発生するエラーやその他のイベントをキャプチャすることが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6bd48-136">When you run a package programmatically as shown in the preceding sample, you may also want to capture errors and other events that occur as the package executes.</span></span> <span data-ttu-id="6bd48-137">イベントのキャプチャは、<xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> クラスから継承するクラスを追加し、パッケージを読み込むときにそのクラスへの参照を渡すことによって行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6bd48-137">You can accomplish this by adding a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class, and by passing a reference to that class when you load the package.</span></span> <span data-ttu-id="6bd48-138">次の例では <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> イベントのみがキャプチャされますが、<xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> クラスによってキャプチャできるイベントは他にも多数あります。</span><span class="sxs-lookup"><span data-stu-id="6bd48-138">Although the following example captures only the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> event, there are many other events that the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class lets you capture.</span></span>  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically-and-capture-package-events"></a><span data-ttu-id="6bd48-139">プログラムによってローカル コンピューターでパッケージを実行し、パッケージ イベントをキャプチャするには</span><span class="sxs-lookup"><span data-stu-id="6bd48-139">To run a package on the local computer programmatically and capture package events</span></span>  
  
1.  <span data-ttu-id="6bd48-140">上記の例の手順を実行し、この例のプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-140">Follow the steps in the preceding example to create a project for this example.</span></span>  
  
2.  <span data-ttu-id="6bd48-141">メイン ルーチンに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-141">Add the following code in the main routine.</span></span> <span data-ttu-id="6bd48-142">完成したコンソール アプリケーションは、たとえば次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bd48-142">The completed console application should look like the following example.</span></span>  
  
3.  <span data-ttu-id="6bd48-143">プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-143">Run the project.</span></span> <span data-ttu-id="6bd48-144">このサンプル コードでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサンプルと共にインストールされている CalculatedColumns サンプル パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-144">The sample code executes the CalculatedColumns sample package that is installed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="6bd48-145">パッケージ実行結果は、発生したエラーと共にコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bd48-145">The result of package execution is displayed in the console window, along with any errors that occur.</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="6bd48-146">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="6bd48-146">Sample Code</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    Dim eventListener As New EventListener()  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, eventListener)  
    pkgResults = pkg.Execute(Nothing, Nothing, eventListener, Nothing, Nothing)  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
  
Class EventListener  
  Inherits DefaultEvents  
  
  Public Overrides Function OnError(ByVal source As Microsoft.SqlServer.Dts.Runtime.DtsObject, _  
    ByVal errorCode As Integer, ByVal subComponent As String, ByVal description As String, _  
    ByVal helpFile As String, ByVal helpContext As Integer, _  
    ByVal idofInterfaceWithError As String) As Boolean  
  
    ' Add application-specific diagnostics here.  
    Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description)  
    Return False  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppWithEventsCS  
{  
  class MyEventListener : DefaultEvents  
  {  
    public override bool OnError(DtsObject source, int errorCode, string subComponent,   
      string description, string helpFile, int helpContext, string idofInterfaceWithError)  
    {  
      // Add application-specific diagnostics here.  
      Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description);  
      return false;  
    }  
  }  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      MyEventListener eventListener = new MyEventListener();  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, eventListener);  
      pkgResults = pkg.Execute(null, null, eventListener, null, null);  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
<span data-ttu-id="6bd48-147">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="6bd48-147">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6bd48-148">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bd48-148">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6bd48-149">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="6bd48-149">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6bd48-150">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="6bd48-150">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd48-151">参照</span><span class="sxs-lookup"><span data-stu-id="6bd48-151">See Also</span></span>  
 <span data-ttu-id="6bd48-152">[ローカル実行とリモート実行の違いについて](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span><span class="sxs-lookup"><span data-stu-id="6bd48-152">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span></span>  
 <span data-ttu-id="6bd48-153">[プログラムによるリモートパッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="6bd48-153">[Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span></span>  
 [<span data-ttu-id="6bd48-154">ローカル パッケージの出力の読み込み</span><span class="sxs-lookup"><span data-stu-id="6bd48-154">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
