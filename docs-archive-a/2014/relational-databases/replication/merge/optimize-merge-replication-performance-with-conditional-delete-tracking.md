---
title: 条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
- articles [SQL Server replication], conditional delete tracking
ms.assetid: 58f120a3-ea3a-4e97-93f0-0eb4e580ecf2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46fc189d2a2e0ebf5ea44775585a69d52783a7e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630944"
---
# <a name="optimize-merge-replication-performance-with-conditional-delete-tracking"></a><span data-ttu-id="f2208-102">条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="f2208-102">Optimize Merge Replication Performance with Conditional Delete Tracking</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="f2208-103">マージ レプリケーションでは、1 つ以上のアーティクルに対する削除が、レプリケーション トリガーおよびシステム テーブルにより追跡されないように指定することができます。</span><span class="sxs-lookup"><span data-stu-id="f2208-103">With merge replication you can specify that deletes for one or more articles should not be tracked by replication triggers and system tables.</span></span> <span data-ttu-id="f2208-104">アーティクルに対してこのオプションを指定すると、削除は、パブリッシャーやサブスクライバーから追跡またはレプリケートされません。</span><span class="sxs-lookup"><span data-stu-id="f2208-104">If you specify this option for an article, deletes are not tracked or replicated from the Publisher or any Subscribers.</span></span> <span data-ttu-id="f2208-105">このオプションは、多くのアプリケーション シナリオをサポートしたり、削除のレプリケーションが不要または望ましくない場合にパフォーマンスの最適化を行うために利用できます。</span><span class="sxs-lookup"><span data-stu-id="f2208-105">This option is available to support a number of application scenarios and to provide a performance optimization for cases in which the replication of deletes is not necessary or desirable.</span></span> <span data-ttu-id="f2208-106">パフォーマンスは、削除のメタデータを格納しない、削除を同期中に列挙しない、削除をサブスクライバーにレプリケートせずサブスクライバーでも適用しない、という 3 つの方法により向上します。</span><span class="sxs-lookup"><span data-stu-id="f2208-106">Performance is enhanced in three ways: metadata for deletes is not stored; deletes are not enumerated during synchronization; deletes are not replicated to and applied at the Subscriber.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2208-107">ダウンロード専用アーティクルを使用するためには、90RTM 以上の互換性レベルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="f2208-107">To use download-only articles, the compatibility level of the publication must be at least 90RTM.</span></span>  
  
 <span data-ttu-id="f2208-108">オプションはパブリケーションを作成する際に指定できます。一部の削除をレプリケートし、バッチによる削除などその他の削除はレプリケートしないことがアプリケーションで必要な場合には、オプションのオン/オフを切り替えられます。</span><span class="sxs-lookup"><span data-stu-id="f2208-108">The option can be specified when a publication is created or it can be toggled on and off if an application requires that some deletes be replicated and that others not be replicated, such as batch deletes.</span></span> <span data-ttu-id="f2208-109">以下の例では、このオプションがどのようにアプリケーションで使用されるかを示します。</span><span class="sxs-lookup"><span data-stu-id="f2208-109">The following examples illustrate ways in which this option might be used in an application:</span></span>  
  
-   <span data-ttu-id="f2208-110">移動営業部門向けのアプリケーションには、通常、 **SalesOrderHeader**、 **SalesOrderDetail** 、および **Product**などのテーブルがあります。</span><span class="sxs-lookup"><span data-stu-id="f2208-110">An application for a mobile sales force typically has tables such as **SalesOrderHeader**, **SalesOrderDetail** and **Product**.</span></span> <span data-ttu-id="f2208-111">注文は、サブスクライバーで入力され、次にパブリッシャーにレプリケートされます。パブリッシャーは、頻繁にデータを注文確定システムに送ります。</span><span class="sxs-lookup"><span data-stu-id="f2208-111">Orders are entered at the Subscriber and then replicated to the Publisher, which often supplies data to an order fulfillment system.</span></span> <span data-ttu-id="f2208-112">モバイル ワーカーの多くは、記憶域が制限されたハンドヘルド デバイスを使用しています。パブリッシャーで注文を受けると、サブスクライバーではこれを削除できます。</span><span class="sxs-lookup"><span data-stu-id="f2208-112">Many mobile workers use handheld devices which have limited storage: after the order is received at the Publisher, it can be deleted at the Subscriber.</span></span> <span data-ttu-id="f2208-113">注文がシステム内ではまだアクティブであるため、削除はパブリッシャーに反映されません。</span><span class="sxs-lookup"><span data-stu-id="f2208-113">The delete is not propagated to the Publisher, because the order is still active in the system.</span></span>  
  
     <span data-ttu-id="f2208-114">このシナリオでは、 **SalesOrderHeader** および **SalesOrderDetail** テーブルに対して、削除は追跡されません。</span><span class="sxs-lookup"><span data-stu-id="f2208-114">In this scenario, deletes would not be tracked for the **SalesOrderHeader** and **SalesOrderDetail** tables.</span></span> <span data-ttu-id="f2208-115">**Product** テーブルについては、削除を追跡します。これは、パブリッシャーで製品が削除された場合、製品リストを最新に保つために削除をサブスクライバーに送信する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="f2208-115">Deletes would be tracked for the **Product** table, because if a product is deleted at the Publisher, the delete should be sent to the Subscriber to keep the product list up to date.</span></span>  
  
-   <span data-ttu-id="f2208-116">アプリケーションは、 **TransactionHistory**などのテーブルに履歴データを格納できます。テーブルでは、1 年を経過したレコードを定期的に削除します。</span><span class="sxs-lookup"><span data-stu-id="f2208-116">An application could store historical data in a table such as **TransactionHistory**, which is periodically purged of records older than a year.</span></span> <span data-ttu-id="f2208-117">サブスクライバーが今月のトランザクションのデータのみを受信するように、テーブルをフィルター選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="f2208-117">The table could be filtered such that Subscribers only receive data on transactions within the current month.</span></span> <span data-ttu-id="f2208-118">パブリッシャーで毎月バッチで行われる古いデータの削除は、サブスクライバーとは関係がありませんが、既定では、これらを追跡および列挙します。</span><span class="sxs-lookup"><span data-stu-id="f2208-118">Monthly batch deletes at the Publisher that purge older data are not relevant to Subscribers, but they would still be tracked and enumerated by default.</span></span>  
  
     <span data-ttu-id="f2208-119">このシナリオでは、バッチ処理が発生する前に、システムでの処理を停止し、アプリケーションで削除の追跡を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="f2208-119">In this scenario, before the batch processing occurred, activity could be stopped on the system, and the application could disable the tracking of deletes.</span></span> <span data-ttu-id="f2208-120">処理が完了したら、追跡を再度有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f2208-120">After the processing has finished, tracking could again be enabled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f2208-121">パブリッシャーで他の処理が継続している場合は、削除の追跡が無効の間に、サブスクライバーへの反映が必要な削除が発生しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2208-121">If other activity continues at the Publisher, you must ensure that deletes that should be propagated to Subscribers do not occur while delete tracking is disabled.</span></span>  
  
 <span data-ttu-id="f2208-122">**削除が追跡されないように指定するには**</span><span class="sxs-lookup"><span data-stu-id="f2208-122">**To specify that deletes should not be tracked**</span></span>  
  
-   <span data-ttu-id="f2208-123">レプリケーション [!INCLUDE[tsql](../../../includes/tsql-md.md)] プログラミング: [マージ アーティクルに対して削除を追跡しないように指定する &#40;レプリケーション Transact-SQL プログラミング&#41;](..//publish/specify-merge-replication-properties.md#tracking-deletes)</span><span class="sxs-lookup"><span data-stu-id="f2208-123">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming: [Specify That Deletes Should Not Be Tracked For Merge Articles &#40;Replication Transact-SQL Programming&#41;](..//publish/specify-merge-replication-properties.md#tracking-deletes)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2208-124">参照</span><span class="sxs-lookup"><span data-stu-id="f2208-124">See Also</span></span>  
 <span data-ttu-id="f2208-125">[マージレプリケーションのアーティクルオプション](article-options-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="f2208-125">[Article Options for Merge Replication](article-options-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="f2208-126">ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化</span><span class="sxs-lookup"><span data-stu-id="f2208-126">Optimize Merge Replication Performance with Download-Only Articles</span></span>](optimize-merge-replication-performance-with-download-only-articles.md)  
  
  
