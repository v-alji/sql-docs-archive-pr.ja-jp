---
title: 'レッスン 1: レポート サーバー プロジェクトの作成 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a708e5114344e87edd620ef58bc50594a9b9ef8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742914"
---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a><span data-ttu-id="901f5-102">レッスン 1 : レポート サーバー プロジェクトの作成 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="901f5-102">Lesson 1: Creating a Report Server Project (Reporting Services)</span></span>
  <span data-ttu-id="901f5-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でレポートを作成するには、まずレポート サーバー プロジェクトを作成して、レポート定義ファイル (.rdl) やその他レポートに必要なリソース ファイルを格納できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="901f5-103">To create a report in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you must first create a report server project where you will save your report definition (.rdl) file and any other resource files that you need for your report.</span></span> <span data-ttu-id="901f5-104">次に、実際のレポート定義ファイルを作成し、レポートのデータ ソース、データセット、レイアウトを定義します。</span><span class="sxs-lookup"><span data-stu-id="901f5-104">Then you will create the actual report definition file, define a data source for your report, define a dataset, and define the report layout.</span></span> <span data-ttu-id="901f5-105">作成したレポートを実行すると、実際のデータが取得され、レイアウト定義に従って画面上に表示されるので、その状態からエクスポート、印刷、保存を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="901f5-105">When you run the report, the actual data is retrieved and combined with the layout, and then rendered on your screen, from where you can export it, print it, or save it.</span></span>  
  
 <span data-ttu-id="901f5-106">このレッスンでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]でレポート サーバー プロジェクトを作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="901f5-106">In this lesson, you will learn how to create a report server project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="901f5-107">レポート サーバー プロジェクトを使用して、レポート サーバーで実行するレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="901f5-107">A report server project is used to create reports that run on a report server.</span></span>  
  
### <a name="to-create-a-report-server-project"></a><span data-ttu-id="901f5-108">レポート サーバー プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="901f5-108">To create a report server project</span></span>  
  
1.  <span data-ttu-id="901f5-109">[**スタート**] をクリックし、[**すべてのプログラム**]、[] の順にポイントし [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] て、[ **SQL Server Data Tools**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-109">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], and then click **SQL Server Data Tools**.</span></span> <span data-ttu-id="901f5-110">初めてを開いた場合は、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 既定の環境設定の [**ビジネスインテリジェンスの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-110">If this is the first time you have opened [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Business Intelligence Settings** for the default environment settings.</span></span>  
  
2.  <span data-ttu-id="901f5-111">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="901f5-112">**[インストールされているテンプレート]** ボックスの一覧で、 **[ビジネス インテリジェンス プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-112">In the **Installed Templates** list, click **Business Intelligence**.</span></span>  
  
4.  <span data-ttu-id="901f5-113">[**レポートサーバープロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-113">Click **Report Server Project**.</span></span>  
  
5.  <span data-ttu-id="901f5-114">**[名前]** に「 **Tutorial**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="901f5-114">In **Name**, type **Tutorial**.</span></span>  
  
6.  <span data-ttu-id="901f5-115">**[OK]** をクリックしてプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="901f5-115">Click **OK** to create the project.</span></span>  
  
     <span data-ttu-id="901f5-116">Tutorial プロジェクトがソリューション エクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="901f5-116">The Tutorial project is displayed in Solution Explorer.</span></span>  
  
### <a name="to-create-a-new-report-definition-file"></a><span data-ttu-id="901f5-117">新しいレポート定義ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="901f5-117">To create a new report definition file</span></span>  
  
1.  <span data-ttu-id="901f5-118">ソリューションエクスプローラーで、[**レポート**] を右クリックして [**追加**] をポイントし、[**新しいアイテム**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-118">In Solution Explorer, right-click **Reports**, point to **Add**, and click **New Item**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="901f5-119">**[ソリューション エクスプローラー]** ウィンドウが表示されない場合は、 **[表示]** メニューの **[ソリューション エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-119">If the **Solution Explorer** window is not visible, from the **View** menu, click **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="901f5-120">[**新しい項目の追加**] ダイアログボックスの [**テンプレート**] の下にある [**レポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-120">In the **Add New Item** dialog box, under **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="901f5-121">**[名前]** に「 **Sales Orders.rdl** 」と入力して、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-121">In **Name**, type **Sales Orders.rdl** and then click **Add**.</span></span>  
  
     <span data-ttu-id="901f5-122">レポート デザイナーを開き、デザイン ビューで新しい .rdl ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="901f5-122">Report Designer opens and displays the new .rdl file in Design view.</span></span>  
  
 <span data-ttu-id="901f5-123">レポート デザイナーは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で実行される [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="901f5-123">Report Designer is a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] component that runs in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="901f5-124">**[デザイン]** ビューと **[プレビュー]** ビューの 2 つのビューがあります。</span><span class="sxs-lookup"><span data-stu-id="901f5-124">It has two views: **Design** and **Preview**.</span></span> <span data-ttu-id="901f5-125">ビューを変更するには該当するタブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="901f5-125">Click each tab to change views.</span></span>  
  
 <span data-ttu-id="901f5-126">**[レポート データ]** ペインでデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="901f5-126">You define your data in the **Report Data** pane.</span></span> <span data-ttu-id="901f5-127">**[デザイン]** ビューではレポートのレイアウトを定義します。</span><span class="sxs-lookup"><span data-stu-id="901f5-127">You define your report layout in **Design** view.</span></span> <span data-ttu-id="901f5-128">**[プレビュー]** ビューではレポートを実行して結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="901f5-128">You can run the report and see what it looks like in **Preview** view.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="901f5-129">次の作業</span><span class="sxs-lookup"><span data-stu-id="901f5-129">Next Task</span></span>  
 <span data-ttu-id="901f5-130">ここでは、"Tutorial" というレポート プロジェクトを作成し、このレポート プロジェクトにレポート定義ファイル (.rdl) を追加しました。</span><span class="sxs-lookup"><span data-stu-id="901f5-130">You have successfully created a report project called "Tutorial" and added a report definition (.rdl) file to the report project.</span></span> <span data-ttu-id="901f5-131">次に、レポートで使用するデータ ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="901f5-131">Next, you will specify a data source to use for the report.</span></span> <span data-ttu-id="901f5-132">「[レッスン 2: 接続情報の指定 &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="901f5-132">See [Lesson 2: Specifying Connection Information &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="901f5-133">参照</span><span class="sxs-lookup"><span data-stu-id="901f5-133">See Also</span></span>  
 [<span data-ttu-id="901f5-134">基本的なテーブル レポートの作成 (SSRS チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="901f5-134">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
