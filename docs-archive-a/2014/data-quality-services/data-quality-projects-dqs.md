---
title: データ品質プロジェクト (DQS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a43fc9c0-19b6-414a-8661-4c7c55e0c03e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 471d528144b6687ffa3aeedb82cf479817c4edc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633324"
---
# <a name="data-quality-projects-dqs"></a><span data-ttu-id="01f14-102">データ品質プロジェクト (DQS)</span><span class="sxs-lookup"><span data-stu-id="01f14-102">Data Quality Projects (DQS)</span></span>
  <span data-ttu-id="01f14-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のデータ品質プロジェクトは、ナレッジ ベースを使用してソース データの品質を改善する手段になります。 *データ クレンジング* アクティビティおよび *データ照合* アクティビティを実行して、その結果データを SQL Server データベースや .csv ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="01f14-103">A data quality project in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) is a means of using a knowledge base to improve the quality of your source data by performing *data cleansing* and *data matching* activities, and then exporting the resultant data to a SQL Server database or a .csv file.</span></span> <span data-ttu-id="01f14-104">データ品質プロジェクトをクレンジング プロジェクトまたは照合プロジェクトとして作成し、それぞれのアクティビティを実行できます。</span><span class="sxs-lookup"><span data-stu-id="01f14-104">You can create a data quality project as a cleansing project or a matching project to perform respective activities.</span></span> <span data-ttu-id="01f14-105">データ クレンジングと照合のナレッジは同じナレッジ ベースに組み込むことができるため、クレンジング プロジェクトと照合プロジェクトは同じナレッジ ベースを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="01f14-105">Cleansing and matching projects can be run using the same knowledge base, because knowledge for data cleansing and matching can be built into the same knowledge base.</span></span>  
  
 <span data-ttu-id="01f14-106">データ品質プロジェクトには次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="01f14-106">A data quality project has the following benefits:</span></span>  
  
-   <span data-ttu-id="01f14-107">DQS ナレッジ ベースのナレッジを使用してソース データのデータ クレンジングを実行できます。</span><span class="sxs-lookup"><span data-stu-id="01f14-107">Enables you to perform data cleansing on your source data by using the knowledge in a DQS knowledge base.</span></span>  
  
-   <span data-ttu-id="01f14-108">ナレッジ ベースの照合ポリシーを使用してソース データのデータ照合を実行できます。</span><span class="sxs-lookup"><span data-stu-id="01f14-108">Enables you to perform data matching on your source data by using the matching policy in a knowledge base.</span></span>  
  
-   <span data-ttu-id="01f14-109">クレンジング アクティビティや照合アクティビティの実施をガイドするウィザードが提供されているほか、データを必要により SQL Server データベースや .csv ファイルにエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="01f14-109">Provides a wizard to guide you through the cleansing and matching activities, and export the data as per your selection to a SQL Server database or to a .csv file.</span></span> <span data-ttu-id="01f14-110">データ スチュワードはデータ品質プロジェクトを使用して、コンピューター支援型の、またはインタクラティブなクレンジングやデータ照合手順を実行および制御できます。</span><span class="sxs-lookup"><span data-stu-id="01f14-110">The data steward can use the data quality project to run and control the computer-assisted/interactive cleansing and data matching steps.</span></span>  
  
##  <a name="data-quality-project-cleansing-activity"></a><a name="Cleansing"></a><span data-ttu-id="01f14-111">データ品質プロジェクト: クレンジングアクティビティ</span><span class="sxs-lookup"><span data-stu-id="01f14-111">Data Quality Project: Cleansing Activity</span></span>  
 <span data-ttu-id="01f14-112">クレンジング データ品質プロジェクトでは、ナレッジ ベースに基づいてソース データのクレンジングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="01f14-112">A cleansing data quality project enables you to cleanse your source data based on a knowledge base.</span></span> <span data-ttu-id="01f14-113">DQS のデータ クレンジング アクティビティは、2 段階のプロセスから成ります。</span><span class="sxs-lookup"><span data-stu-id="01f14-113">The data cleansing activity in DQS is a two-step process:</span></span>  
  
1.  <span data-ttu-id="01f14-114">*コンピューター支援型の* データ クレンジング プロセス。ナレッジ ベース内のナレッジと照らし合わせてソース データを分析し、変更を提示します。</span><span class="sxs-lookup"><span data-stu-id="01f14-114">A *computer-assisted* data cleansing process that analyzes source data against the knowledge in the knowledge base, and proposes changes.</span></span> <span data-ttu-id="01f14-115">処理後のデータは DQS によって分類 (提案、新規、無効、修正済み、および修正) されたうえでユーザーに表示され、さらに処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="01f14-115">The processed data is categorized (suggested, new, invalid, corrected, and correct) by DQS, and displayed to the user for further processing.</span></span>  
  
2.  <span data-ttu-id="01f14-116">*インタラクティブな* クレンジング プロセス。データ スチュワードがコンピューター支援型のデータ クレンジング プロセスによって提案されたデータを承認、拒否、または変更します。</span><span class="sxs-lookup"><span data-stu-id="01f14-116">An *interactive* cleansing process that enables the data steward to approve, reject, or modify the data proposed by the computer-assisted data cleansing process.</span></span>  
  
 <span data-ttu-id="01f14-117">データ品質プロジェクトのクレンジング アクティビティの詳細については、「 [Data Cleansing](../../2014/data-quality-services/data-cleansing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01f14-117">For detailed information about the cleansing activity in a data quality project, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
##  <a name="data-quality-project-matching-activity"></a><a name="Matching"></a> <span data-ttu-id="01f14-118">データ品質プロジェクト: 照合アクティビティ</span><span class="sxs-lookup"><span data-stu-id="01f14-118">Data Quality Project: Matching Activity</span></span>  
 <span data-ttu-id="01f14-119">データ品質プロジェクトの照合では、ナレッジ ベース内の照合ポリシーに基づいて照合アクティビティを実行します。完全一致やあいまい一致を特定することによってデータの重複を防ぎ、重複データをユーザーが削除できます。</span><span class="sxs-lookup"><span data-stu-id="01f14-119">A matching data quality project enables you to perform matching activity based on matching policy in a knowledge base to prevent data duplication by identifying exact and approximate matches, and thereby enabling you to remove duplicate data.</span></span> <span data-ttu-id="01f14-120">データをクレンジングしてから照合を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="01f14-120">It is recommended that you cleanse your data before running matching on it.</span></span> <span data-ttu-id="01f14-121">そのためには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="01f14-121">To do so:</span></span>  
  
1.  <span data-ttu-id="01f14-122">データ品質プロジェクトを作成し、 **[クレンジング]** アクティビティを選択してソース データのデータ クレンジング アクティビティを完了し、その後 SQL Server データベースのテーブルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="01f14-122">Create a data quality project, select the **Cleansing** activity, complete the data cleansing activity on your source data, and then export it to a table in a SQL Server database.</span></span>  
  
2.  <span data-ttu-id="01f14-123">照合ポリシーを含んだナレッジ ベースを使用して別のデータ品質プロジェクトを作成し、 **[照合]** アクティビティを選択し、手順 1. でクレンジングしたデータをエクスポートしたデータベースとテーブルを **[マップ]** ページで選択します。</span><span class="sxs-lookup"><span data-stu-id="01f14-123">Create another data quality project by using a knowledge base that contains a matching policy, select the **Matching** activity, and then in the **Map** page, select the database and the table where you exported the cleansed data in step 1.</span></span>  
  
3.  <span data-ttu-id="01f14-124">クレンジングされたデータに対して照合アクティビティを完了させます。</span><span class="sxs-lookup"><span data-stu-id="01f14-124">Complete the matching activity on the cleansed data.</span></span>  
  
 <span data-ttu-id="01f14-125">データ品質プロジェクトの照合アクティビティの詳細については、「 [Data Matching](../../2014/data-quality-services/data-matching.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01f14-125">For detailed information about the matching activity in a data quality project, see [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
##  <a name="data-profiling-and-notifications"></a><a name="ProfilingNotification"></a> <span data-ttu-id="01f14-126">データ プロファイルと通知</span><span class="sxs-lookup"><span data-stu-id="01f14-126">Data Profiling and Notifications</span></span>  
 <span data-ttu-id="01f14-127">データ品質プロジェクトでクレンジングおよび照合アクティビティを実行しながら、DQS で処理中のデータに関する統計と情報をリアルタイムに表示できます。</span><span class="sxs-lookup"><span data-stu-id="01f14-127">While running the cleansing and matching activities in a data quality project, you can see real-time statistics and information about the data that is being processed by DQS.</span></span> <span data-ttu-id="01f14-128">クレンジングおよび照合プロセスの有効性を評価したり、データ クレンジングまたは照合によりデータ品質がどの程度向上したかを計測したりするのに、データ プロファイルが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="01f14-128">Data profiling helps you assess the effectiveness of the cleansing and matching processes, and you can potentially determine the extent to which data cleansing or matching helped improve the data quality.</span></span> <span data-ttu-id="01f14-129">DQS プロファイルでは、 *完全性* (データがどの程度存在するか) と *正確性* (データがどの程度意図されたとおりに使用できるか) の 2 つのデータ品質ディメンションを提供します。</span><span class="sxs-lookup"><span data-stu-id="01f14-129">DQS profiling provides two data-quality dimensions: *completeness* (the extent to which data is present) and *accuracy* (the extent to which data can be used for its intended use).</span></span> <span data-ttu-id="01f14-130">さらに、データ プロファイル情報に基づいて、データ クレンジングおよびデータ照合操作を向上させるために取ることができるアクションをユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="01f14-130">Further, based on the data profiling information, notifications are displayed to the user on the actions that can be taken to enhance the data cleansing and data matching operations.</span></span> <span data-ttu-id="01f14-131">データ プロファイルと通知の詳細については、「 [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01f14-131">For detailed information about data profiling and notifications, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="01f14-132">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="01f14-132">Related Tasks</span></span>  
  
|<span data-ttu-id="01f14-133">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="01f14-133">Task Description</span></span>|<span data-ttu-id="01f14-134">トピック</span><span class="sxs-lookup"><span data-stu-id="01f14-134">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="01f14-135">データ品質プロジェクトの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="01f14-135">Describes how to create a data quality project.</span></span>|[<span data-ttu-id="01f14-136">データ品質プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="01f14-136">Create a Data Quality Project</span></span>](../../2014/data-quality-services/create-a-data-quality-project.md)|  
|<span data-ttu-id="01f14-137">データ品質プロジェクトの管理方法 (開く、ロック解除、名前の変更、および削除) について説明します。</span><span class="sxs-lookup"><span data-stu-id="01f14-137">Describes how to manage (open, unlock, rename, and delete) a data quality project.</span></span>|[<span data-ttu-id="01f14-138">データ品質プロジェクト&#41; を管理 &#40;開いてロックを解除する、名前を変更する、削除する</span><span class="sxs-lookup"><span data-stu-id="01f14-138">Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project</span></span>](../../2014/data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)|  
|<span data-ttu-id="01f14-139">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]で Integration Services プロジェクトを開く方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="01f14-139">Describes how to open an Integration Services project in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>|[<span data-ttu-id="01f14-140">Data Quality Client で Integration Services プロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="01f14-140">Open Integration Services Projects in Data Quality Client</span></span>](../../2014/data-quality-services/open-integration-services-projects-in-data-quality-client.md)|  
  
## <a name="see-also"></a><span data-ttu-id="01f14-141">参照</span><span class="sxs-lookup"><span data-stu-id="01f14-141">See Also</span></span>  
 [<span data-ttu-id="01f14-142">DQS のナレッジ ベースとドメイン</span><span class="sxs-lookup"><span data-stu-id="01f14-142">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
