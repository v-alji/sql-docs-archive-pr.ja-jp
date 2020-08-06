---
title: Web サービス プロキシの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, proxies
- proxies [Reporting Services]
- XML Web service [Reporting Services], proxies
- Web service [Reporting Services], proxies
- Web references [Reporting Services]
ms.assetid: b1217843-8d3d-49f3-a0d2-d35b0db5b2df
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d080b96fa29e906c044561a684d58275af9f61e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713818"
---
# <a name="creating-the-web-service-proxy"></a><span data-ttu-id="d626a-102">Web サービス プロキシの作成</span><span class="sxs-lookup"><span data-stu-id="d626a-102">Creating the Web Service Proxy</span></span>
  <span data-ttu-id="d626a-103">クライアントと Web サービスは、SOAP メッセージを使用して通信できます。SOAP メッセージは、入力パラメーターと出力パラメーターを XML としてカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="d626a-103">A client and a Web service can communicate using SOAP messages, which encapsulate the input and output parameters as XML.</span></span> <span data-ttu-id="d626a-104">プロキシ クラスは、パラメーターを XML 要素にマップした後、ネットワークを介して SOAP メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="d626a-104">A proxy class maps parameters to XML elements and then sends the SOAP messages over a network.</span></span> <span data-ttu-id="d626a-105">この方法では、プロキシ クラスによって、SOAP レベルで Web サービスと通信する必要がなくなり、SOAP および Web サービスのプロキシをサポートするあらゆる開発環境で Web サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d626a-105">In this way, the proxy class frees you from having to communicate with the Web service at the SOAP level and allows you to invoke Web service methods in any development environment that supports SOAP and Web service proxies.</span></span>  
  
 <span data-ttu-id="d626a-106">を使用して開発プロジェクトにプロキシクラスを追加するには、の WSDL ツールを使用する方法 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] と、で Web 参照を追加する [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 方法の2つがあります。</span><span class="sxs-lookup"><span data-stu-id="d626a-106">There are two ways to add a proxy class to your development project using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: with the WSDL tool in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], and by adding a Web reference in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="d626a-107">ここでは、これらの方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="d626a-107">The following sections discuss this subject in further detail.</span></span>  
  
## <a name="adding-the-proxy-using-the-wsdl-tool"></a><span data-ttu-id="d626a-108">WSDL ツールを使用したプロキシの追加</span><span class="sxs-lookup"><span data-stu-id="d626a-108">Adding the Proxy Using the WSDL Tool</span></span>  
 <span data-ttu-id="d626a-109">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK には、Web サービス記述言語ツール (Wsdl.exe) が含まれています。これにより、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 開発環境で使用する Web サービス プロキシを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d626a-109">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK includes the Web Services Description Language tool (Wsdl.exe), which enables you to generate a Web service proxy for use in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] development environment.</span></span> <span data-ttu-id="d626a-110">Web サービスをサポートする言語 (現在は C# と) でクライアントプロキシを作成する最も一般的な方法 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] は、WSDL ツールを使用することです。</span><span class="sxs-lookup"><span data-stu-id="d626a-110">The most common way to create a client proxy in languages that support Web services (currently C# and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) is to use the WSDL tool.</span></span>  
  
 <span data-ttu-id="d626a-111">**Wsdl.exe を使用してプロキシ クラスをプロジェクトに追加するには**</span><span class="sxs-lookup"><span data-stu-id="d626a-111">**To add a proxy class to your project using Wsdl.exe**</span></span>  
  
1.  <span data-ttu-id="d626a-112">コマンド プロンプトから、Wsdl.exe を使用してプロキシ クラスを作成します。最低限レポート サーバー Web サービスへの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="d626a-112">From a command prompt, use Wsdl.exe to create a proxy class, specifying (at a minimum) the URL to the Report Server Web service.</span></span>  
  
     <span data-ttu-id="d626a-113">たとえば、次のコマンド プロンプト ステートメントは、レポート サーバー Web サービスの管理用エンドポイントの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="d626a-113">For example, the following command prompt statement specifies a URL for the management endpoint of the Report Server Web service:</span></span>  
  
    ```  
    wsdl /language:CS /n:"Microsoft.SqlServer.ReportingServices2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="d626a-114">WSDL ツールは、プロキシ生成用のコマンド プロンプト引数の数値を受け付けます。</span><span class="sxs-lookup"><span data-stu-id="d626a-114">The WSDL tool accepts a number of command-prompt arguments for generating a proxy.</span></span> <span data-ttu-id="d626a-115">前の例は C# 言語、プロキシに使用する推奨名前空間 (Web サービス エンドポイントを複数使用する場合に名前の衝突を避けるため) を指定し、ReportingService2010.cs という名前の C# ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="d626a-115">The preceding example specifies the language C#, a suggested namespace to use in the proxy (to prevent name collision if using more than one Web service endpoint), and generates a C# file called ReportingService2010.cs.</span></span> <span data-ttu-id="d626a-116">この例で [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] を指定した場合は、ReportingService2010.vb という名前のプロキシ ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d626a-116">If the example had specified [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], the example would have generated a proxy file with the name ReportingService2010.vb.</span></span> <span data-ttu-id="d626a-117">このファイルは、コマンド実行元のディレクトリに作成されます。</span><span class="sxs-lookup"><span data-stu-id="d626a-117">This file is created in the directory from which you run the command.</span></span>  
  
2.  <span data-ttu-id="d626a-118">プロキシ クラスをアセンブリ ファイル (拡張子 .dll) にコンパイルし、それをプロジェクトで参照するか、またはプロキシ クラスをプロジェクト アイテムとして追加します。</span><span class="sxs-lookup"><span data-stu-id="d626a-118">Compile the proxy class into an assembly file (with the extension .dll) and reference it in your project, or add the class as a project item.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d626a-119">プロキシ クラスをプロジェクトに手動で追加する場合は、System.Web.Services.dll への参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d626a-119">When you add a proxy class to your project manually, you need to add a reference to System.Web.Services.dll.</span></span> <span data-ttu-id="d626a-120">Visual Studio .NET で Web 参照を使用してプロキシを追加する場合は、参照が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d626a-120">If you add the proxy using a Web reference in Visual Studio .NET, the reference is automatically created for you.</span></span> <span data-ttu-id="d626a-121">詳細については、この後の「Visual Studio で Web 参照を使用するプロキシの追加」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d626a-121">For more information, see "Adding the Proxy Using a Web Reference in Visual Studio" later in this topic.</span></span>  
  
     <span data-ttu-id="d626a-122">プロキシ クラスをアイテムとしてプロジェクトに追加した後、関連付けられたファイルがソリューション エクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d626a-122">After you add the proxy class as an item to your project, the associated file appears in Solution Explorer.</span></span>  
  
3.  <span data-ttu-id="d626a-123">プログラムによってサービスを呼び出すには、プロキシ クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d626a-123">To call the service programmatically, create an instance of the proxy class.</span></span>  
  
     <span data-ttu-id="d626a-124">次のコード例は、プロジェクトに <xref:ReportService2010.ReportingService2010> プロキシ クラスのインスタンスを作成する場合の構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="d626a-124">The following code example shows the syntax for creating an instance of the <xref:ReportService2010.ReportingService2010> proxy class in a project:</span></span>  
  
```vb  
Dim service As New ReportingService2010()  
```  
  
```csharp  
ReportingService2010 service = new ReportingService2010();  
  
```  
  
 <span data-ttu-id="d626a-125">完全な構文を含む Wsdl.exe ツールの詳細については、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK ドキュメントの「Web サービス記述言語ツール」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d626a-125">For more information about the Wsdl.exe tool, including its full syntax, see "Web Services Description Language Tool" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span> <span data-ttu-id="d626a-126">Web サービス プロキシの詳しい説明は、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK ドキュメントの「XML Web サービス プロキシの作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d626a-126">For a full explanation of Web service proxies, see "Creating an XML Web Service Proxy" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="adding-the-proxy-using-a-web-reference-in-visual-studio"></a><span data-ttu-id="d626a-127">Visual Studio で Web 参照を使用するプロキシの追加</span><span class="sxs-lookup"><span data-stu-id="d626a-127">Adding the Proxy Using a Web Reference in Visual Studio</span></span>  
 <span data-ttu-id="d626a-128">Web 参照によって、プロジェクトで 1 つ以上の Web サービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d626a-128">A Web reference enables a project to consume one or more Web services.</span></span> [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] <span data-ttu-id="d626a-129">では、ユーザーが次の簡単な手順に従うことによって、Web サービスの参照をプロジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="d626a-129">enables users to add Web service references to projects by following a few simple steps.</span></span>  
  
 <span data-ttu-id="d626a-130">**Web 参照をプロジェクトに追加するには**</span><span class="sxs-lookup"><span data-stu-id="d626a-130">**To add a Web reference to a project**</span></span>  
  
1.  <span data-ttu-id="d626a-131">**ソリューション エクスプローラー**で、Web サービスを使用するプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d626a-131">In **Solution Explorer**, select the project that will consume the Web service.</span></span>  
  
2.  <span data-ttu-id="d626a-132">**[プロジェクト]** メニューの **[Web 参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d626a-132">On the **Project** menu, click **Add Web Reference**.</span></span>  
  
     <span data-ttu-id="d626a-133">**[Web 参照の追加]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="d626a-133">The **Add Web Reference** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="d626a-134">**[URL]** フィールドに、レポート サーバー Web サービスへの完全なパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d626a-134">In the **URL** field, enter the complete path to the Report Server Web service.</span></span>  
  
     <span data-ttu-id="d626a-135">レポート サーバー Web サービスのレポート実行エンドポイントの単純な URL は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d626a-135">A simplified URL for the report execution endpoint of the Report Server Web service might look like this:</span></span>  
  
    ```  
    http://<Server Name>/reportserver/reportexecution2005.asmx  
    ```  
  
     <span data-ttu-id="d626a-136">URL には、レポート サーバー Web サービスを配置するドメイン、Web サービスを格納するフォルダー名、および Web サービスの検出ファイル名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d626a-136">The URL contains the domain in which the Report Server Web service is deployed, the name of the folder containing the service, and the name of the discovery file for the service.</span></span> <span data-ttu-id="d626a-137">各種 URL 要素の完全な説明については、「[SOAP API へのアクセス](../accessing-the-soap-api.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d626a-137">For a complete description of the different URL elements, see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
     <span data-ttu-id="d626a-138">Web サービスによって提供されるメソッドとプロパティの説明が、左側のブラウザー ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d626a-138">A description of the methods and properties provided by the Web service appears in the Browser pane on the left.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d626a-139">レポート サーバー Web サービスに関連付けられたアイテムの詳細については、「[レポート サーバー Web サービス メソッド](../methods/report-server-web-service-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d626a-139">For more information about the items associated with the Report Server Web service, see [Report Server Web Service Methods](../methods/report-server-web-service-methods.md).</span></span>  
  
4.  <span data-ttu-id="d626a-140">プロジェクトでレポート サーバー Web サービスを使用できること、およびレポート サーバーにアクセスするための適切な権限を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d626a-140">Verify that your project can use the Report Server Web service, and that you have appropriate permission to access the report server.</span></span>  
  
5.  <span data-ttu-id="d626a-141">**[Web 参照名]** フィールドに、プログラムによってレポート サーバー Web サービスにアクセスする場合にコードで使用する名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d626a-141">In the **Web reference name** field, enter a name that you will use in your code to access the Report Server Web service programmatically.</span></span>  
  
6.  <span data-ttu-id="d626a-142">**[参照の追加]** を選択し、アプリケーションで Web サービスへの参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="d626a-142">Select the **Add Reference** button to create a reference in your application to the Web service.</span></span>  
  
     <span data-ttu-id="d626a-143">アクティブなプロジェクトの [Web 参照] ノードの下にある **[ソリューション エクスプローラー]** に、新しい参照が **[Web 参照名]** フィールドに指定した名前で表示されます。</span><span class="sxs-lookup"><span data-stu-id="d626a-143">The new reference appears in **Solution Explorer** under the Web References node for the active project, named as specified in the **Web reference name** field.</span></span>  
  
7.  <span data-ttu-id="d626a-144">**[ソリューション エクスプローラー]** で、[Web 参照] フォルダーを展開し、プロジェクトのアイテムで使用できる Web 参照クラスの名前空間をメモします。</span><span class="sxs-lookup"><span data-stu-id="d626a-144">In **Solution Explorer**, expand the Web References folder to note the namespace for the Web reference classes that are available to the items in your project.</span></span>  
  
     <span data-ttu-id="d626a-145">Web 参照をプロジェクトに追加した後、関連付けられたファイルが **[ソリューション エクスプローラー]** の [Web 参照] フォルダー内にあるフォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d626a-145">After adding a Web reference to your project, the associated files are displayed in a folder within the Web References folder of **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="d626a-146">Web 参照を追加した後に、次の構文を使用してプロキシ クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d626a-146">After you add the Web reference, use the following syntax to create an instance of the proxy class:</span></span>  
  
```vb  
Dim rs As New myNamespace.myReferenceName.ReportExecutionService()  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
myNamespace.myReferenceName.ReportExecutionService rs = new myNamespace.myReferenceName.ReportExecutionService();  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
```  
  
 <span data-ttu-id="d626a-147">**using** ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では **Import**) ディレクティブをレポート サーバー Web サービス参照に追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="d626a-147">You can also add a **using** (**Import** in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) directive to the Report Server Web service reference.</span></span> <span data-ttu-id="d626a-148">このディレクティブを使用すると、型を名前空間で完全修飾する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="d626a-148">If you use this directive, you do not need to fully qualify the types in the namespace.</span></span> <span data-ttu-id="d626a-149">このためには、次のコードをファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="d626a-149">To do this, add the following code to your file:</span></span>  
  
```vb  
Import myNamespace.myReferenceName  
```  
  
```csharp  
using myNamespace.myReferenceName;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d626a-150">参照</span><span class="sxs-lookup"><span data-stu-id="d626a-150">See Also</span></span>  
 <span data-ttu-id="d626a-151">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="d626a-151">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="d626a-152">[Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="d626a-152">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="d626a-153">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d626a-153">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
