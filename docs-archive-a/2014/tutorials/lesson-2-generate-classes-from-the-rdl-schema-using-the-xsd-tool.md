---
title: 'レッスン 2: xsd ツールを使用して RDL スキーマからクラスを生成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2c5db118ad8f94afc72cea44b9a2489f2b4fd7f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719089"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a><span data-ttu-id="ba7c4-102">レッスン 2 : xsd ツールを使用して RDL スキーマからクラスを作成</span><span class="sxs-lookup"><span data-stu-id="ba7c4-102">Lesson 2: Generate Classes from the RDL Schema using the xsd Tool</span></span>
  <span data-ttu-id="ba7c4-103">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトを作成したら、次はレポート定義スキーマのローカル コピーを取得して、XML スキーマ定義ツール (Xsd.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-103">After you have created your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project, the next step is to retrieve a local copy of the report definition schema and run the XML Schema Definition Tool (Xsd.exe).</span></span>  
  
### <a name="to-generate-the-rdl-classes"></a><span data-ttu-id="ba7c4-104">RDL クラスを生成するには</span><span class="sxs-lookup"><span data-stu-id="ba7c4-104">To generate the RDL classes</span></span>  
  
1.  <span data-ttu-id="ba7c4-105">Internet Explorer のインスタンス [!INCLUDE[msCoName](../includes/msconame-md.md)] (または同等の Web ブラウザー) を開き、次の URL に移動します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-105">Open an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (or equivalent Web browser) and navigate to the following URL:</span></span>  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  <span data-ttu-id="ba7c4-106">RDL スキーマがブラウザーで開かれたら、[**ファイル**] メニューに移動し、[名前を付け**て保存**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-106">Once the RDL schema has been opened in the browser, browse to the **File** menu, and select **Save As**.</span></span>  
  
3.  <span data-ttu-id="ba7c4-107">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトを作成した場所に移動して、スキーマをファイル名 ReportDefinition.xsd として保存します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-107">Browse to the location where you created your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project and save the schema with the file name ReportDefinition.xsd.</span></span>  
  
4.  <span data-ttu-id="ba7c4-108">ファイルが保存されたら、コマンドプロンプトのインスタンスを開き [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-108">After the file has been saved, open an instance of the [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] command prompt.</span></span> <span data-ttu-id="ba7c4-109">コマンドプロンプトのインスタンスを開くには、[スタート] ボタンをクリックし、[**すべてのプログラム**]、[ **Microsoft Visual Studio 2010**]、[ **Visual Studio Tools**の順にポイントし、[ **Visual Studio コマンドプロンプト (2010)**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-109">To open an instance of the command prompt, click the Start menu, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools** and click **Visual Studio Command Prompt (2010)**.</span></span>  
  
5.  <span data-ttu-id="ba7c4-110">現在のパスを、ReportDefinition.xsd ファイルを保存した場所に変更します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-110">Change the current path to the location where you saved the ReportDefinition.xsd file:</span></span>  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  <span data-ttu-id="ba7c4-111">次のコマンドを使用して、RDL スキーマのクラスを含む ReportDefinition.cs ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-111">Generate the ReportDefinition.cs file that contains the classes for the RDL schema with the following command:</span></span>  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     <span data-ttu-id="ba7c4-112">ReportDefinition.vb ファイルを生成するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-112">To generate a ReportDefinition.vb file use this command:</span></span>  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  <span data-ttu-id="ba7c4-113">プロジェクトに ReportDefinition.xsd を追加します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-113">Add ReportDefinition.xsd your project.</span></span> <span data-ttu-id="ba7c4-114">[**プロジェクト**] メニューの [**既存項目の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-114">From the **Project** menu, click **Add Existing Item**.</span></span> <span data-ttu-id="ba7c4-115">ReportDefinition .xsd ファイルの場所を参照し、[ReportDefinition. xsd] を選択して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-115">Browse to the location of the ReportDefinition.xsd file, select ReportDefinition.xsd, and click **Add**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba7c4-116">プロジェクトに ReportDefinition .xsd ファイルを追加すると、ReportDefinition.cs (.vb) ファイルが存在しないことが**ソリューションエクスプローラー**わかります。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-116">After you have added the ReportDefinition.xsd file to the project you will notice in **Solution Explorer** that the ReportDefinition.cs (.vb) file is not there.</span></span> <span data-ttu-id="ba7c4-117">ファイルを表示するには、ReportDefinition.xsd ファイルの横にある展開/折りたたみのボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-117">To display the file, click the expand/collapse button next to the ReportDefinition.xsd file.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="ba7c4-118">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="ba7c4-118">Next Lesson</span></span>  
 <span data-ttu-id="ba7c4-119">次のレッスンでは、RDL スキーマから生成したクラスを使って、レポート サーバーからレポート定義を読み込むコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-119">In the next lesson, you will write code to load a report definition from a report server using the classes you generated from the RDL schema.</span></span> <span data-ttu-id="ba7c4-120">「[レッスン 3: レポートサーバーからレポート定義を読み込む](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba7c4-120">See [Lesson 3: Load a Report Definition from the Report Server](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba7c4-121">参照</span><span class="sxs-lookup"><span data-stu-id="ba7c4-121">See Also</span></span>  
 <span data-ttu-id="ba7c4-122">[RDL スキーマから生成されたクラスを使用したレポートの更新 SSRS チュートリアル &#40;&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="ba7c4-122">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="ba7c4-123">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ba7c4-123">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
