---
title: 'レッスン 1: RDL スキーマ Visual Studio プロジェクトを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f420509c-51aa-4170-8c25-64c2954f4bb9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a8411e3f0458ccda8c291d5c86a4467bb051a263
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711206"
---
# <a name="lesson-1-create-the-rdl-schema-visual-studio-project"></a><span data-ttu-id="544e0-102">レッスン 1 : RDL スキーマ Visual Studio プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="544e0-102">Lesson 1: Create the RDL Schema Visual Studio Project</span></span>
  <span data-ttu-id="544e0-103">このチュートリアルでは、簡単なコンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="544e0-103">For this tutorial, you will create a simple console application.</span></span> <span data-ttu-id="544e0-104">このチュートリアルは、で開発することを前提としてい [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="544e0-104">This tutorial assumes you are developing in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="544e0-105">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services で実行されているレポート サーバー Web サービスにアクセスする場合は、"_SQLExpress" を "ReportServer" パスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="544e0-105">When accessing the Report Server Web service running on [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, you must append "_SQLExpress" to the "ReportServer" path.</span></span> <span data-ttu-id="544e0-106">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="544e0-106">For example:</span></span>  
>   
>  `http://myserver/reportserver_sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-create-the-web-service-proxy"></a><span data-ttu-id="544e0-107">Web サービス プロキシを作成するには</span><span class="sxs-lookup"><span data-stu-id="544e0-107">To create the web service proxy</span></span>  
  
1.  <span data-ttu-id="544e0-108">[**スタート**] メニューから、[**すべてのプログラム**]、[Microsoft Visual Studio]、[ **Visual Studio Tools**]、[ **Visual Studio 2010 コマンドプロンプト**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="544e0-108">From the **Start** menu, select **All Programs**, then Microsoft Visual Studio, then **Visual Studio Tools**, and then **Visual Studio 2010 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="544e0-109">C#: を使用している場合は、コマンド プロンプト ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="544e0-109">In the command prompt window, run the following command if you are using C#:</span></span>  
  
    ```  
    wsdl /language:CS /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="544e0-110">Visual Basic を使用している場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="544e0-110">If you are using Visual Basic, then run the following command:</span></span>  
  
    ```  
    wsdl /language:VB /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="544e0-111">このコマンドは .cs ファイルまたは .vb ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="544e0-111">This command generates a .cs or .vb file.</span></span> <span data-ttu-id="544e0-112">このファイルをアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="544e0-112">You will add this file to your application.</span></span>  
  
### <a name="to-create-a-console-application"></a><span data-ttu-id="544e0-113">コンソール アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="544e0-113">To create a console application</span></span>  
  
1.  <span data-ttu-id="544e0-114">[**ファイル**] メニューの [**新規作成**] をポイントし、[**プロジェクト**] をクリックして [**新しいプロジェクト**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="544e0-114">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="544e0-115">左側のウィンドウの [**インストールされたテンプレート**] で、[ **Visual Basic** ] または [ **Visual C#** ] ノードをクリックし、展開された一覧からプロジェクトの種類のカテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="544e0-115">In the left pane, under **Installed Templates**, click either **Visual Basic** or the **Visual C#** node, and select a category of project types from the expanded list.</span></span>  
  
3.  <span data-ttu-id="544e0-116">[**コンソールアプリケーション**] プロジェクトの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="544e0-116">Choose the **Console Application** project type.</span></span>  
  
4.  <span data-ttu-id="544e0-117">[**名前**] ボックスに、プロジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="544e0-117">In the **Name** box, enter a name for your project.</span></span> <span data-ttu-id="544e0-118">名前を入力 `SampleRDLSchema` します。</span><span class="sxs-lookup"><span data-stu-id="544e0-118">Type the name `SampleRDLSchema`.</span></span>  
  
5.  <span data-ttu-id="544e0-119">[**場所**] ボックスにプロジェクトを保存するパスを入力するか、[**参照**] をクリックしてフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="544e0-119">In the **Location** box, type the path where you want to save your project, or click **Browse** to navigate to the folder.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="544e0-120">ソリューションエクスプローラーに、プロジェクトの折りたたまれたビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="544e0-120">A collapsed view of your project appears in Solution Explorer.</span></span>  
  
7.  <span data-ttu-id="544e0-121">**[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="544e0-121">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
8.  <span data-ttu-id="544e0-122">生成した .cs ファイルまたは .vb ファイルの場所に移動し、ファイルを選択して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="544e0-122">Navigate to the location for the .cs or .vb file you generated, then select the file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="544e0-123">また、Web 参照が動作するように、<xref:System.Web.Services> 名前空間への参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="544e0-123">You will also need to add a reference to the <xref:System.Web.Services> namespace for your Web reference to work.</span></span>  
  
9. <span data-ttu-id="544e0-124">[プロジェクト] メニューの **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="544e0-124">On the Project menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="544e0-125">[**参照の追加**] ダイアログボックスの [ **.net** ] タブで、[ **system.web. Services**] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="544e0-125">In the **Add Reference** dialog box, in the **.NET** tab, select **System.Web.Services**, then click **OK**.</span></span>  
  
     <span data-ttu-id="544e0-126">レポートサーバー Web サービスに接続する方法の詳細については、「 [Web サービスと .NET Framework を使用したアプリケーションの構築](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="544e0-126">For more information about how to connect to the Report Server Web service, see [Building Applications Using the Web Service and the .NET Framework](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
10. <span data-ttu-id="544e0-127">ソリューションエクスプローラーで、プロジェクトノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="544e0-127">In Solution Explorer, expand the project node.</span></span> <span data-ttu-id="544e0-128">プロジェクトには、Program.cs ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] の場合は Module1.vb) という既定の名前のコード ファイルが追加されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="544e0-128">You will see a code file with the default name of Program.cs (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) has been added to your project.</span></span>  
  
11. <span data-ttu-id="544e0-129">Program.cs ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] の場合は Module1.vb) ファイルを開き、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="544e0-129">Open the Program.cs (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) file and replace the code with the following:</span></span>  
  
     <span data-ttu-id="544e0-130">次のコードは、読み込み、変更、保存の機能を実装するときに使用するメソッドの一部です。</span><span class="sxs-lookup"><span data-stu-id="544e0-130">The following code provides the method stubs we will use to implement the Load, Update and Save functionality.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using ReportService2010;  
  
    namespace SampleRDLSchema  
    {  
        class ReportUpdater  
        {  
            ReportingService2010 _reportService;  
  
            static void Main(string[] args)  
            {  
                ReportUpdater reportUpdater = new ReportUpdater();  
                reportUpdater.UpdateReport();  
            }  
  
            private void UpdateReport()  
            {  
                try  
                {  
                    // Set up the Report Service connection  
                    _reportService = new ReportingService2010();  
                    _reportService.Credentials =  
                        System.Net.CredentialCache.DefaultCredentials;  
                    _reportService.Url =  
                       "http://<Server Name>/reportserver/" +  
                                       "reportservice2010.asmx";  
  
                    // Call the methods to update a report definition  
                    LoadReportDefinition();  
                    UpdateReportDefinition();  
                    PublishReportDefinition();  
                }  
                catch (Exception ex)  
                {  
                    System.Console.WriteLine(ex.Message);  
                }  
            }  
  
            private void LoadReportDefinition()  
            {  
                //Lesson 3: Load a report definition from the report   
                //          catalog  
            }  
  
            private void UpdateReportDefinition()  
            {  
                //Lesson 4: Update the report definition using the    
                //          classes generated from the RDL Schema  
            }  
  
            private void PublishReportDefinition()  
            {  
                //Lesson 5: Publish the updated report definition back   
                //          to the report catalog  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports ReportService2010  
  
    Namespace SampleRDLSchema  
  
        Module ReportUpdater  
  
            Private m_reportService As ReportingService2010  
  
            Public Sub Main(ByVal args As String())  
  
                Try  
                    'Set up the Report Service connection  
                    m_reportService = New ReportingService2010  
                    m_reportService.Credentials = _  
                        System.Net.CredentialCache.DefaultCredentials  
                    m_reportService.Url = _  
                        "http:// <Server Name>/reportserver/" & _  
                               "reportservice2010.asmx"  
  
                    'Call the methods to update a report definition  
                    LoadReportDefinition()  
                    UpdateReportDefinition()  
                    PublishReportDefinition()  
                Catch ex As Exception  
                    System.Console.WriteLine(ex.Message)  
                End Try  
  
            End Sub  
  
            Private Sub LoadReportDefinition()  
                'Lesson 3: Load a report definition from the report   
                '          catalog  
            End Sub  
  
            Private Sub UpdateReportDefinition()  
                'Lesson 4: Update the report definition using the   
                '          classes generated from the RDL Schema  
            End Sub  
  
            Private Sub PublishReportDefinition()  
                'Lesson 5: Publish the updated report definition back   
                '          to the report catalog  
            End Sub  
  
        End Module  
  
    End Namespace   
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="544e0-131">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="544e0-131">Next Lesson</span></span>  
 <span data-ttu-id="544e0-132">次のレッスンでは、XML スキーマ定義ツール (Xsd.exe) を使用して RDL スキーマからクラスを生成し、プロジェクトに組み込みます。</span><span class="sxs-lookup"><span data-stu-id="544e0-132">In the next lesson, you will use the XML Schema Definition Tool (Xsd.exe) to generate classes from the RDL schema and include them in your project.</span></span> <span data-ttu-id="544e0-133">「[レッスン 2: Xsd ツールを使用して RDL スキーマからクラスを生成](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="544e0-133">See [Lesson 2: Generate Classes from the RDL Schema using the xsd Tool](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544e0-134">参照</span><span class="sxs-lookup"><span data-stu-id="544e0-134">See Also</span></span>  
 <span data-ttu-id="544e0-135">[RDL スキーマから生成されたクラスを使用したレポートの更新 SSRS チュートリアル &#40;&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="544e0-135">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="544e0-136">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="544e0-136">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
