---
title: 'レッスン 13: Excel で分析する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
ms.openlocfilehash: 129956ddc8e755d1f2b298a7ea36307d50f52344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631293"
---
# <a name="lesson-13-analyze-in-excel"></a><span data-ttu-id="055fc-102">レッスン 13:[Excel で分析]</span><span class="sxs-lookup"><span data-stu-id="055fc-102">Lesson 13: Analyze in Excel</span></span>
  <span data-ttu-id="055fc-103">このレッスンでは、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で "Excel で分析" 機能を使用して Microsoft Excel を開き、モデル ワークスペースへのデータ ソース接続を自動的に作成して、ワークシートにピボットテーブルを自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="055fc-103">In this lesson, you will use the Analyze in Excel feature in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to open Microsoft Excel, automatically create a data source connection to the model workspace, and automatically add a PivotTable to the worksheet.</span></span> <span data-ttu-id="055fc-104">Analyze in Excel 機能は､モデルをデプロイする前にモデル デザインの有効性を迅速かつ簡単にテストする手段を提供することを意図しています｡</span><span class="sxs-lookup"><span data-stu-id="055fc-104">The Analyze in Excel feature is meant to provide a quick and easy way to test the efficacy of your model design prior to deploying your model.</span></span> <span data-ttu-id="055fc-105">このレッスンでは、データの分析は行いません。</span><span class="sxs-lookup"><span data-stu-id="055fc-105">You will not perform any data analysis in this lesson.</span></span> <span data-ttu-id="055fc-106">このレッスンの目的はモデル作成者が､モデル デザインのテストに利用できるツールを慣れてもらうことにあります｡</span><span class="sxs-lookup"><span data-stu-id="055fc-106">The purpose of this lesson is to familiarize you, the model author, with the tools you can use to test your model design.</span></span> <span data-ttu-id="055fc-107">モデル作成者向けの "Excel で分析" 機能を使用する場合とは異なり、エンド ユーザーは Excel や [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] などのクライアント レポート アプリケーションを使用して、配置済みのモデル データへの接続と参照を行います。</span><span class="sxs-lookup"><span data-stu-id="055fc-107">Unlike using the Analyze in Excel feature, which is meant for model authors, end-users will use client reporting applications such as Excel or [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] to connect to and browse deployed model data.</span></span>  
  
 <span data-ttu-id="055fc-108">このレッスンを完了するには、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]と同じコンピューター上に Excel がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="055fc-108">In order to complete this lesson, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="055fc-109">詳細については、「[Excel で分析 (SSAS テーブル)](tabular-models/analyze-in-excel-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="055fc-109">To learn more, see [Analyze in Excel &#40;SSAS Tabular&#41;](tabular-models/analyze-in-excel-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="055fc-110">このレッスンの推定所要時間: **20 分**</span><span class="sxs-lookup"><span data-stu-id="055fc-110">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="055fc-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="055fc-111">Prerequisites</span></span>  
 <span data-ttu-id="055fc-112">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="055fc-112">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="055fc-113">このレッスンの実習を行う前に、前のレッスン「 [レッスン 11: パーティションの作成](lesson-10-create-partitions.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="055fc-113">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a><span data-ttu-id="055fc-114">Default および Internet Sales パースペクティブを使用して参照します｡</span><span class="sxs-lookup"><span data-stu-id="055fc-114">Browse using the Default and Internet Sales perspectives</span></span>  
 <span data-ttu-id="055fc-115">ここでは、すべてのモデル オブジェクトを含む既定のパースペクティブと「レッスン 8: パースペクティブの作成」で作成した Internet Sales パースペクティブの両方を使用してモデルを参照します。</span><span class="sxs-lookup"><span data-stu-id="055fc-115">In these first tasks, you will browse your model by using both the default perspective, which includes all model objects, and also by using the Internet Sales perspective you created in Lesson 8: Create Perspectives.</span></span> <span data-ttu-id="055fc-116">Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。</span><span class="sxs-lookup"><span data-stu-id="055fc-116">The Internet Sales perspective excludes the Customer table object.</span></span>  
  
#### <a name="to-browse-by-using-the-default-perspective"></a><span data-ttu-id="055fc-117">Default パースペクティブを使って参照する</span><span class="sxs-lookup"><span data-stu-id="055fc-117">To browse by using the Default perspective</span></span>  
  
1.  <span data-ttu-id="055fc-118">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="055fc-118">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="055fc-119">**[Analyze in Excel]** ダイアログ ボックスで **[OK]** をクリックします｡</span><span class="sxs-lookup"><span data-stu-id="055fc-119">In the **Analyze in Excel** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="055fc-120">新しいノートブックで Excel が開きます｡</span><span class="sxs-lookup"><span data-stu-id="055fc-120">Excel will open with a new workbook.</span></span> <span data-ttu-id="055fc-121">現在のユーザー アカウントを使用してデータ ソース接続が作成され、既定のパースペクティブを使用して表示可能なフィールドが定義されます。</span><span class="sxs-lookup"><span data-stu-id="055fc-121">A data source connection is created using the current user account and the Default perspective is used to define viewable fields.</span></span> <span data-ttu-id="055fc-122">ピボットテーブルがワークシートに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="055fc-122">A Pivot table is automatically added to the worksheet.</span></span>  
  
3.  <span data-ttu-id="055fc-123">Excel の [**ピボットテーブルのフィールドリスト**] に、 **Date**および**internet sales**メジャーが表示され、 **Customer**、 **date**、 **Geography**、 **product**、 **product Category**、 **product サブカテゴリ**、および**internet sales**の各テーブルにそれぞれの列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="055fc-123">In Excel, in the **PivotTable Field List**, notice the **Date** and **Internet Sales** measures appear, as well as the **Customer**, **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory**, and **Internet Sales** tables with all of their respective columns appear.</span></span>  
  
4.  <span data-ttu-id="055fc-124">ブックを保存せずに Excel を閉じます。</span><span class="sxs-lookup"><span data-stu-id="055fc-124">Close Excel without saving the workbook.</span></span>  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a><span data-ttu-id="055fc-125">Internet Sales パースペクティブを使って参照する</span><span class="sxs-lookup"><span data-stu-id="055fc-125">To browse by using the Internet Sales perspective</span></span>  
  
1.  <span data-ttu-id="055fc-126">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="055fc-126">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="055fc-127">**[Excel で分析]** ダイアログ ボックスの **[現在の Windows ユーザー]** を選択したままにして、 **[パースペクティブ]** ドロップダウン リストで **[Internet Sales]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="055fc-127">In the **Analyze in Excel** dialog box, leave **Current Windows User** selected, then in the **Perspective** drop-down listbox, select **Internet Sales**, and then click **OK**.</span></span> <span data-ttu-id="055fc-128">Excel が開きます。</span><span class="sxs-lookup"><span data-stu-id="055fc-128">Excel opens.</span></span>  
  
3.  <span data-ttu-id="055fc-129">Excel の **[ピボットテーブルのフィールドリスト]** で、フィールドリストから Customer テーブルが除外されます。</span><span class="sxs-lookup"><span data-stu-id="055fc-129">In Excel, in the **PivotTable Field List**, notice the Customer table is excluded from the field list.</span></span>  
  
## <a name="browse-using-roles"></a><span data-ttu-id="055fc-130">ロールを使用した参照</span><span class="sxs-lookup"><span data-stu-id="055fc-130">Browse Using Roles</span></span>  
 <span data-ttu-id="055fc-131">ロールはテーブル モデルに欠かせない要素です。</span><span class="sxs-lookup"><span data-stu-id="055fc-131">Roles are an integral part of any tabular model.</span></span> <span data-ttu-id="055fc-132">ユーザーがメンバーとして追加されているロールが少なくとも 1 つなければ、ユーザーはモデルを使用してデータにアクセスし、分析することができません。</span><span class="sxs-lookup"><span data-stu-id="055fc-132">Without at least one role, to which users are added as members, users will not be able to access and analyze data using your model.</span></span> <span data-ttu-id="055fc-133">"Excel で分析" 機能を利用して、定義したロールをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="055fc-133">The Analyze in Excel feature provides a way for you to test the roles you have defined.</span></span>  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a><span data-ttu-id="055fc-134">Internet Sales Manager ユーザー ロールを使用して参照するには</span><span class="sxs-lookup"><span data-stu-id="055fc-134">To browse by using the Internet Sales Manager user role</span></span>  
  
1.  <span data-ttu-id="055fc-135">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="055fc-135">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="055fc-136">**[Excel で分析]** ダイアログ ボックスの **[モデルへの接続に使用するユーザー名またはロールの指定]** で、 **[ロール]** を選択します。次にドロップダウン リストで **[Internet Sales Manager]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="055fc-136">In the **Analyze in Excel** dialog box, in **Specify the user name or role to use to connect to the model**, select **Role**, and then in the drop-down listbox, select **Internet Sales Manager**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="055fc-137">新しいノートブックで Excel が開きます｡</span><span class="sxs-lookup"><span data-stu-id="055fc-137">Excel will open with a new workbook.</span></span> <span data-ttu-id="055fc-138">ピボット テーブルが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="055fc-138">A Pivot table is automatically created.</span></span> <span data-ttu-id="055fc-139">[ピボット テーブル フィールド リスト] には、新しいモデルで使用できるすべてのデータ フィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="055fc-139">The Pivot Table Field List includes all of the data fields available in your new model.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="055fc-140">次の手順</span><span class="sxs-lookup"><span data-stu-id="055fc-140">Next Steps</span></span>  
 <span data-ttu-id="055fc-141">このチュートリアルを続行するには、次のレッスン「 [レッスン 14: 配置](lesson-13-deploy.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="055fc-141">To continue this tutorial, go to the next lesson: [Lesson 14: Deploy](lesson-13-deploy.md).</span></span>  
  
  
