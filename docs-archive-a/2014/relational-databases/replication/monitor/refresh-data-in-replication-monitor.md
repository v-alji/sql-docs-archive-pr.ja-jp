---
title: レプリケーション モニターのデータの更新 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f097dea21b06540293e9b60b7de9315323b4168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741830"
---
# <a name="refresh-data-in-replication-monitor"></a><span data-ttu-id="9f72e-102">レプリケーション モニターのデータの更新</span><span class="sxs-lookup"><span data-stu-id="9f72e-102">Refresh Data in Replication Monitor</span></span>
  <span data-ttu-id="9f72e-103">レプリケーション モニターでは、メイン ウィンドウと詳細ウィンドウ (メイン ウィンドウから起動するウィンドウ) を自動または手動で最新の情報に更新できます。</span><span class="sxs-lookup"><span data-stu-id="9f72e-103">In Replication Monitor, the main window and detail windows (those windows launched from the main window) can be refreshed automatically or manually.</span></span> <span data-ttu-id="9f72e-104">ウィンドウを手動で最新の情報に更新する場合は、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9f72e-104">To refresh a window manually, press F5.</span></span> <span data-ttu-id="9f72e-105">既定では、メイン ウィンドウは 5 秒ごとに自動で最新の情報に更新されます。この更新頻度は、パブリッシャーごとにカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="9f72e-105">By default, the main window is refreshed automatically every five seconds; the rate can be customized for each Publisher.</span></span>  
  
 <span data-ttu-id="9f72e-106">レプリケーション モニターに表示されるデータはキャッシュからクエリされます。キャッシュとレプリケーション モニターの更新の関係に関する詳細については、「[キャッシュ、更新、およびレプリケーション モニターのパフォーマンス](caching-refresh-and-replication-monitor-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f72e-106">The data displayed in Replication Monitor is queried from a cache; for information about the relationship between the cache and refreshing Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span> <span data-ttu-id="9f72e-107">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f72e-107">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a><span data-ttu-id="9f72e-108">レプリケーション モニターの更新オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="9f72e-108">To set refresh options for Replication Monitor</span></span>  
  
1.  <span data-ttu-id="9f72e-109">パブリケーション モニターの左ペインでパブリッシャーを右クリックしてから、 **[パブリッシャーの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f72e-109">Right-click a Publisher in the left pane of Replication Monitor, and then click **Publisher Settings**.</span></span>  
  
2.  <span data-ttu-id="9f72e-110">**[パブリッシャーの設定]** ダイアログ ボックスで、 **[自動更新]** または **[更新頻度]** オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="9f72e-110">In the **Publisher Settings** dialog box, set the **Auto refresh** and **Refresh rate** options.</span></span> <span data-ttu-id="9f72e-111">**[自動更新]** 設定は、レプリケーション モニターのメイン ウィンドウに影響します。</span><span class="sxs-lookup"><span data-stu-id="9f72e-111">The **Auto refresh** setting affects the main window in Replication Monitor.</span></span> <span data-ttu-id="9f72e-112">**[更新頻度]** 設定は、自動更新に設定されているすべての詳細ウィンドウにも影響します (この設定の変更に影響を受けるのは、変更後に開かれた詳細ウィンドウのみです)。</span><span class="sxs-lookup"><span data-stu-id="9f72e-112">The **Refresh rate** setting also affects any detail windows that are set to refresh automatically (changes to the setting only affect the detail windows opened after the change).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a><span data-ttu-id="9f72e-113">詳細ウィンドウを自動更新するように指定するには</span><span class="sxs-lookup"><span data-stu-id="9f72e-113">To specify that a detail window should automatically refresh</span></span>  
  
1.  <span data-ttu-id="9f72e-114">レプリケーション モニターで詳細ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="9f72e-114">Open a detail window in Replication Monitor.</span></span> <span data-ttu-id="9f72e-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9f72e-115">For example:</span></span>  
  
    1.  <span data-ttu-id="9f72e-116">左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f72e-116">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
    2.  <span data-ttu-id="9f72e-117">**[すべてのサブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f72e-117">Click the **All Subscriptions** tab.</span></span>  
  
    3.  <span data-ttu-id="9f72e-118">サブスクリプションを右クリックし、 **[詳細表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f72e-118">Right-click a subscription, and then click **View Details**.</span></span>  
  
2.  <span data-ttu-id="9f72e-119">**[サブスクリプション \<SubscriptionName> の詳細]** ウィンドウで、 **[アクション]** をクリックし、 **[自動更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f72e-119">In the **Subscription \<SubscriptionName>** detail window, click **Action**, and then click **Auto Refresh**.</span></span> <span data-ttu-id="9f72e-120">更新頻度は、 **[パブリッシャーの設定]** ダイアログ ボックスの **[更新頻度]** 設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="9f72e-120">The refresh rate is determined by the **Refresh rate** setting in the **Publisher Settings** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f72e-121">参照</span><span class="sxs-lookup"><span data-stu-id="9f72e-121">See Also</span></span>  
 [<span data-ttu-id="9f72e-122">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="9f72e-122">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
