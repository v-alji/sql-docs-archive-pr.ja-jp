---
title: レポート実行の確認 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- auditing [Reporting Services]
- verifying report execution
- logs [Reporting Services], verifying report run
- report execution data [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services], verifying execution
- checking report execution
ms.assetid: 18a98f2f-6b40-454e-9b37-568ed1a96458
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c11c57f7c5f67b2557f5637ad10658abc9f80606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640577"
---
# <a name="verifying-a-report-run"></a><span data-ttu-id="128cb-102">レポート実行の確認</span><span class="sxs-lookup"><span data-stu-id="128cb-102">Verifying a Report Run</span></span>
  <span data-ttu-id="128cb-103">レポート処理の状態に関する情報を表示するには、ログ ファイルを使用するか、またはレポート マネージャーでレポートと共に表示される状態の情報を参照します。</span><span class="sxs-lookup"><span data-stu-id="128cb-103">To view information about the status of report processing, you can use log files or refer to status information that is displayed with the report in Report Manager.</span></span>  
  
## <a name="sources-of-report-execution-data"></a><span data-ttu-id="128cb-104">レポート実行のデータ ソース</span><span class="sxs-lookup"><span data-stu-id="128cb-104">Sources of Report Execution Data</span></span>  
 <span data-ttu-id="128cb-105">レポート実行ログには、レポート名、レポートを実行したユーザー名、レポート実行時間、レポートの配信に使用された配信拡張機能などの、レポート実行に関する包括的な情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="128cb-105">The report execution logs provide comprehensive information about report execution, including the name of the report, the name of the user who ran the report, report execution time, and the delivery extension used to distribute the report.</span></span> <span data-ttu-id="128cb-106">このデータを表示または分析するには、レポート実行ログをデータベース テーブルにコピーします。データベース テーブルでは、クエリの実行やレポートの作成を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="128cb-106">To view and analyze this data, you can copy the report execution log into database tables that are easy to query and report on.</span></span>  
  
 <span data-ttu-id="128cb-107">ログ ファイルには、レポート実行および他のサーバー操作に関する多くのエントリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="128cb-107">Log files contain many entries about report execution and other server activity.</span></span> <span data-ttu-id="128cb-108">ログ ファイルには非常に多くのデータが含まれるので、レポートの最終実行日時のみを確認する場合は、レポート マネージャーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="128cb-108">Because log files contain so much data, you may want to use Report Manager if you only want to verify when the report last ran.</span></span> <span data-ttu-id="128cb-109">さらに情報が必要な場合は、ログ ファイルを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="128cb-109">If you require additional information, you must view the log files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="128cb-110">レポート マネージャーでは、要求時に実行されるレポートの処理時間は表示されません。</span><span class="sxs-lookup"><span data-stu-id="128cb-110">Report Manager does not show the processing times of reports that run on demand.</span></span>  
  
 <span data-ttu-id="128cb-111">次の表では、さまざまな種類のレポートでの処理日時を表示する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="128cb-111">The following table describes how to view the processing date and time for various types of reports.</span></span>  
  
|<span data-ttu-id="128cb-112">レポートの種類</span><span class="sxs-lookup"><span data-stu-id="128cb-112">For this type of report</span></span>|<span data-ttu-id="128cb-113">日時情報の参照先</span><span class="sxs-lookup"><span data-stu-id="128cb-113">Date and time information is located here</span></span>|<span data-ttu-id="128cb-114">情報の表示に必要な操作</span><span class="sxs-lookup"><span data-stu-id="128cb-114">To view the information, do the following</span></span>|  
|-----------------------------|-----------------------------------------------|-----------------------------------------------|  
|<span data-ttu-id="128cb-115">レポート スナップショットとして実行するレポート</span><span class="sxs-lookup"><span data-stu-id="128cb-115">A report that runs as a report snapshot.</span></span>|<span data-ttu-id="128cb-116">[コンテンツ] ページにあります。</span><span class="sxs-lookup"><span data-stu-id="128cb-116">On the Contents page.</span></span> <span data-ttu-id="128cb-117">詳細については、「[[コンテンツ] ページ &#40;レポート マネージャー&#41;](../contents-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="128cb-117">For more information, see [Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md).</span></span>|<span data-ttu-id="128cb-118">1) レポートが含まれているフォルダーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="128cb-118">1) Locate the folder that contains the report.</span></span><br /><span data-ttu-id="128cb-119">2) フォルダーを詳細表示にします。</span><span class="sxs-lookup"><span data-stu-id="128cb-119">2) Set the folder in Details view.</span></span><br /><span data-ttu-id="128cb-120">3) 3) [**実行時**] 列の日付と時刻を確認します。</span><span class="sxs-lookup"><span data-stu-id="128cb-120">3) 3) Note the date and time in the **When Run** column.</span></span>|  
|<span data-ttu-id="128cb-121">レポート履歴のスナップショット</span><span class="sxs-lookup"><span data-stu-id="128cb-121">A snapshot in report history.</span></span>|<span data-ttu-id="128cb-122">[履歴] プロパティ ページにあります。</span><span class="sxs-lookup"><span data-stu-id="128cb-122">On the History Properties page.</span></span> <span data-ttu-id="128cb-123">詳細については、「[[スナップショット オプション] プロパティ ページ &#40;レポート マネージャー&#41;](../snapshot-options-properties-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="128cb-123">For more information, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../snapshot-options-properties-page-report-manager.md).</span></span>|<span data-ttu-id="128cb-124">1) レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="128cb-124">1) Open the report.</span></span><br /><span data-ttu-id="128cb-125">2) **[プロパティ]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="128cb-125">2) Click the **Properties** page.</span></span><br /><span data-ttu-id="128cb-126">3) **[履歴]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="128cb-126">3) Click the **History** tab.</span></span><br /><span data-ttu-id="128cb-127">4) **[実行時]** 列の日時を記録します。</span><span class="sxs-lookup"><span data-stu-id="128cb-127">4) Note the date and time in the **When Run** column.</span></span>|  
|<span data-ttu-id="128cb-128">キャッシュされたレポート</span><span class="sxs-lookup"><span data-stu-id="128cb-128">A cached report.</span></span>|<span data-ttu-id="128cb-129">キャッシュされたレポートの作成および更新に使用するスケジュールに含まれています。</span><span class="sxs-lookup"><span data-stu-id="128cb-129">In the schedule used to create and refresh the cached report.</span></span>|<span data-ttu-id="128cb-130">1) レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="128cb-130">1) Open the report.</span></span><br /><span data-ttu-id="128cb-131">2) **[プロパティ]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="128cb-131">2) Click the **Properties** page.</span></span><br /><span data-ttu-id="128cb-132">3) **[実行]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="128cb-132">3) Click the **Execution** tab.</span></span><br /><span data-ttu-id="128cb-133">4) スケジュールを開きます。</span><span class="sxs-lookup"><span data-stu-id="128cb-133">4) Open the schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="128cb-134">参照</span><span class="sxs-lookup"><span data-stu-id="128cb-134">See Also</span></span>  
 <span data-ttu-id="128cb-135">[Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="128cb-135">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 <span data-ttu-id="128cb-136">[レポート処理プロパティの設定](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="128cb-136">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="128cb-137">レポート マネージャー &#40;SSRS ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="128cb-137">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
