---
title: Data Quality Client で Integration Services プロジェクトを開く | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd29bbba274535d6489eb8d188aa4f0150ed7c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634647"
---
# <a name="open-integration-services-projects-in-data-quality-client"></a><span data-ttu-id="9adb9-102">Data Quality Client で Integration Services プロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="9adb9-102">Open Integration Services Projects in Data Quality Client</span></span>
  <span data-ttu-id="9adb9-103">[!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] では、クレンジング プロジェクトをバッチ モードで実行できます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-103">The [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] enables you to run a cleansing project in batch mode.</span></span> <span data-ttu-id="9adb9-104">しかし、DQS のデータ品質プロジェクト内のクレンジング アクティビティの **[結果の管理と表示]** タブでクレンジング結果を確認するのと同様の方法で、Integration Services パッケージ内でクレンジング結果を確認したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="9adb9-104">However, at times you might want to review the cleansing results in an Integration Services package similar to how you can review the cleansing results in the **Manage and View Results** tab of a cleansing activity in a data quality project in DQS.</span></span> <span data-ttu-id="9adb9-105">DQS では、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] [プロジェクトを開く] **画面から他のデータ品質プロジェクトを開くのと同様に、** で Integration Services プロジェクトを開くことができ、Integration Services プロジェクト内のクレンジング結果について、インタラクティブなクレンジングを操作できます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-105">DQS enables you to open Integration Services projects in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] just like any other data quality project from the **Open project** screen, and have an interactive cleansing experience of the cleansing results in an Integration Services project.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9adb9-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="9adb9-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="9adb9-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9adb9-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9adb9-108">完了した Integration Services プロジェクトだけが **の** [プロジェクトを開く] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-108">Only completed Integration Services projects are available in the **Open project** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="9adb9-109">失敗したプロジェクトや実行中のプロジェクトは **[プロジェクトを開く]** 画面に表示されません。</span><span class="sxs-lookup"><span data-stu-id="9adb9-109">Failed or running projects are not available in the **Open project** screen.</span></span>  
  
-   <span data-ttu-id="9adb9-110">Integration Services プロジェクトは、**で、インタラクティブなクレンジング ステージとして (** [管理ビューと結果] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]タブで) 開きます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-110">Integration Services projects open at the interactive cleansing stage (**Manage View and Results** tab) in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="9adb9-111">**[最適化]** タブまたは **[マップ]** タブに移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="9adb9-111">You cannot go to the **Cleanse** or **Map** tabs.</span></span> <span data-ttu-id="9adb9-112">**[次へ]** をクリックして **[エクスポート]** タブにだけ移動できます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-112">You can only go to the **Export** tab by clicking **Next**.</span></span>  
  
-   <span data-ttu-id="9adb9-113">ロックされた Integration Services プロジェクトを [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]から削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="9adb9-113">You cannot delete a locked Integration Services project from [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="9adb9-114">削除するには先にロックを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9adb9-114">You must first unlock it to delete.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="9adb9-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="9adb9-115">Prerequisites</span></span>  
 <span data-ttu-id="9adb9-116">Integration Services プロジェクトを [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]に表示して開くためには、DQS クレンジング コンポーネントのパッケージを含む Integration Services プロジェクトの実行を正常に完了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9adb9-116">You must have successfully completed running an Integration Services project containing a package with a DQS Cleansing component to see and open it in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9adb9-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9adb9-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9adb9-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="9adb9-118">Permissions</span></span>  
 <span data-ttu-id="9adb9-119">Integration Services プロジェクトを開くためには、DQS_MAIN データベースに対する dqs_kb_editor または dqs_kb_operator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="9adb9-119">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to open an Integration Services project.</span></span>  
  
##  <a name="open-an-integration-services-project"></a><a name="Open"></a> <span data-ttu-id="9adb9-120">Integration Services プロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="9adb9-120">Open an Integration Services Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="9adb9-121">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="9adb9-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="9adb9-122">の [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ホーム画面で、[**データ品質プロジェクトを開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9adb9-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open Data Quality Project**.</span></span> <span data-ttu-id="9adb9-123">**[プロジェクトを開く]** 画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-123">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="9adb9-124">**[プロジェクトを開く]** 画面で、次のいずれかの方法で Integration Services プロジェクトを特定します。</span><span class="sxs-lookup"><span data-stu-id="9adb9-124">In the **Open project** screen, you can identify an Integration Services project in either of the following ways:</span></span>  
  
    1.  <span data-ttu-id="9adb9-125">**プロジェクト名**: Integration Services プロジェクトは、次の名前付け用語を使用して一覧表示されます: "PACKAGE. DQS Cleansing_ *\<DATE>\*\*\<TIME>* _ {GUID}。"</span><span class="sxs-lookup"><span data-stu-id="9adb9-125">**Project Name**: Integration Services projects are listed using the following naming terminology: "Package.DQS Cleansing_*\<DATE>\*\*\<TIME>*_{GUID}."</span></span> <span data-ttu-id="9adb9-126">同じパッケージを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で正常に実行するたびに、新しいプロジェクトが **[プロジェクトを開く]** 画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-126">Every time you successfully run the same package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], a new project is listed in the **Open project** screen.</span></span>  
  
    2.  <span data-ttu-id="9adb9-127">**[プロジェクトの種類]**: Integration Services プロジェクトはプロジェクトの種類が **[SSIS]** として **[プロジェクトを開く]** 画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-127">**Project Type**: Integration Services projects have **SSIS** as the project type in the **Open project** screen.</span></span>  
  
     <span data-ttu-id="9adb9-128">プロジェクトを選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9adb9-128">Select a project, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="9adb9-129">Integration Services プロジェクトが、インタラクティブなクレンジング ステージとして (**[管理ビューと結果]** タブで) 開きます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-129">The Integration Services project opens at the interactive cleansing stage (**Manage View and Results** tab).</span></span> <span data-ttu-id="9adb9-130">Integration Services プロジェクト内のデータに対してインタラクティブなクレンジングを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-130">You can perform an interactive cleansing on the data in the Integration Services project.</span></span> <span data-ttu-id="9adb9-131">**[結果の管理と表示]** タブについて詳しくは、「[DQS &#40;内部&#41; ナレッジを使用したデータのクレンジング](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)」の「[インタラクティブなクレンジング ステージ](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9adb9-131">For detailed information about the **Manage and View Results** tab, see [Interactive Cleansing Stage](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).</span></span>  
  
5.  <span data-ttu-id="9adb9-132">**[次へ]** をクリックして **[エクスポート]** タブに進みます。ここでは処理されたデータを、SQL Server データベースの新しいテーブル、.csv ファイル、または Excel ファイルにエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-132">Click **Next** to go to the **Export** tab where you can export the processed data to any of the following: a new table in the SQL Server database, a .csv file, or an Excel file.</span></span> <span data-ttu-id="9adb9-133">**[エクスポート]** タブについて詳しくは、「[DQS &#40;内部&#41; ナレッジを使用したデータのクレンジング](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)」の「[エクスポート ステージ](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9adb9-133">For detailed information about the **Export** tab, see [Export Stage](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)</span></span>  
  
6.  <span data-ttu-id="9adb9-134">データをエクスポートした後で **[完了]** をクリックして Integration Services プロジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9adb9-134">After exporting the data, click **Finish** to close the Integration Services project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9adb9-135">参照</span><span class="sxs-lookup"><span data-stu-id="9adb9-135">See Also</span></span>  
 <span data-ttu-id="9adb9-136">[DQS クレンジング変換](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="9adb9-136">[DQS Cleansing Transformation](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) </span></span>  
 [<span data-ttu-id="9adb9-137">Integration Services (SSIS) プロジェクト</span><span class="sxs-lookup"><span data-stu-id="9adb9-137">Integration Services &#40;SSIS&#41; Projects</span></span>](../integration-services/integration-services-ssis-projects-and-solutions.md)  
