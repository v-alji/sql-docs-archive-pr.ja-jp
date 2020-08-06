---
title: レポートのキャッシュ (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e359e6c7a40b267979137ef2b3a285667a6fdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642572"
---
# <a name="cache-a-report-report-manager"></a><span data-ttu-id="3b5c1-102">レポートのキャッシュ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="3b5c1-102">Cache a Report (Report Manager)</span></span>
  <span data-ttu-id="3b5c1-103">パフォーマンスを向上させる方法の 1 つに、レポートのキャッシュ プロパティを構成するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-103">One way to improve performance is to configure caching properties for a report.</span></span> <span data-ttu-id="3b5c1-104">レポートをキャッシュに格納した場合、表示されたレポートのコピーが短時間、保存されます。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-104">When a report is cached, a copy of the rendered report is saved for a short period of time.</span></span> <span data-ttu-id="3b5c1-105">レポートを要求した 1 人目のユーザーは、すべての処理が完了しないとレポートを閲覧できませんが、</span><span class="sxs-lookup"><span data-stu-id="3b5c1-105">The first user who requests the report must wait for all processing to complete before viewing the report.</span></span> <span data-ttu-id="3b5c1-106">それ以降、同じレポートを要求したユーザーは、キャッシュの保持時間内であれば、処理が既に完了しているため、すぐにレポートを閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-106">Subsequent users who request the report within the caching period can view it right away because processing has already occurred.</span></span>  
  
 <span data-ttu-id="3b5c1-107">キャッシュできるレポートの種類には制限があります。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-107">There are restrictions on the types of reports that you can cache.</span></span> <span data-ttu-id="3b5c1-108">たとえば、レポート出力がユーザー ID によって異なる場合や、レポートを要求したユーザーのセキュリティ トークンを使ってデータが取得される場合、レポートをキャッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-108">For example, a report cannot be cached if report output varies based on the user identity or if data is retrieved using the security token of the user who requests the report.</span></span> <span data-ttu-id="3b5c1-109">詳細については、「 [レポートのキャッシュ (SSRS)](caching-reports-ssrs.md)でキャッシュを事前に読み込む唯一の方法でした。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-109">For more information, see [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a><span data-ttu-id="3b5c1-110">キャッシュされたレポートの有効期限をスケジュールするには</span><span class="sxs-lookup"><span data-stu-id="3b5c1-110">To schedule the expiration of a cached report</span></span>  
  
1.  <span data-ttu-id="3b5c1-111">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-111">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="3b5c1-112">レポート マネージャーで **[コンテンツ]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-112">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="3b5c1-113">キャッシュ プロパティを設定するレポートに移動し、アイテムの上にマウス ポインターを移動して、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-113">Navigate to the report for which you want to set caching properties, hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="3b5c1-114">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-114">In the drop-down menu, click **Manage**.</span></span>  
  
4.  <span data-ttu-id="3b5c1-115">左フレームの **[処理オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-115">In the left frame, click the **Processing Options**.</span></span>  
  
5.  <span data-ttu-id="3b5c1-116">このページで、 **[常に最新データを使用して、このレポートを実行する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-116">On the page, select **Always run this report with the most recent data**.</span></span>  
  
6.  <span data-ttu-id="3b5c1-117">次の 2 つのキャッシュ オプションのいずれかを選択し、以下のように有効期限を構成します。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-117">Select one of the following two cache options and configure expiration as follows:</span></span>  
  
    -   <span data-ttu-id="3b5c1-118">キャッシュされたコピーが、特定の期間が過ぎた後で有効期限が切れるように構成するには、 **レポートの一時コピーをキャッシュします。レポートのコピーの有効期限は数分後に切れます**。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-118">To configure a cached copy to expire after a particular time period, click **Cache a temporary copy of the report. Expire copy of report after a number of minutes**.</span></span> <span data-ttu-id="3b5c1-119">レポートの有効期限を分単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-119">Type the number of minutes for report expiration.</span></span>  
  
    -   <span data-ttu-id="3b5c1-120">キャッシュされたコピーが、スケジュールに基づいて有効期限が切れるように構成するには、 **[レポートの一時コピーをキャッシュします。次のスケジュールでレポートのコピーの有効期限は切れます。]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-120">To configure a cached copy to expire on a schedule, click **Cache a temporary copy of the report. Expire copy of report on the following schedule.**</span></span> <span data-ttu-id="3b5c1-121">**[構成]** をクリックするか、レポートの有効期限を制御する共有スケジュールを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-121">Click **Configure**, or select a shared schedule to control report expiration</span></span>  
  
7.  <span data-ttu-id="3b5c1-122">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b5c1-122">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5c1-123">参照</span><span class="sxs-lookup"><span data-stu-id="3b5c1-123">See Also</span></span>  
 <span data-ttu-id="3b5c1-124">[レポート処理プロパティの設定](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3b5c1-124">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="3b5c1-125">レポートのキャッシュ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="3b5c1-125">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
  
  
