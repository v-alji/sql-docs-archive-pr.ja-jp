---
title: サブスクリプション、未配布のコマンド (トランザクションサブスクリプション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bbd82b4f4855c99076404d8b621edca11a7e1e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715185"
---
# <a name="subscription-undistributed-commands-transactional-subscription-sql-server-2005-and-later"></a><span data-ttu-id="db86d-102">サブスクリプション、[未配布のコマンド] (トランザクション サブスクリプション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="db86d-102">Subscription, Undistributed Commands (Transactional Subscription, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="db86d-103">**[未配布のコマンド]** タブには、ディストリビューション データベース内のコマンドで、選択したサブスクライバーにまだ配布されていないコマンドの数や、これらのコマンドを配布するのに要すると推定される時間についての情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="db86d-103">The **Undistributed Commands** tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands.</span></span> <span data-ttu-id="db86d-104">ディストリビューション データベース内のコマンドを表示する方法については、「[sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db86d-104">For information about viewing the commands in the distribution database, see [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="db86d-105">Options</span><span class="sxs-lookup"><span data-stu-id="db86d-105">Options</span></span>  
 <span data-ttu-id="db86d-106">**[このサブスクライバーへの適用を待機しているディストリビューション データベース内のコマンド数]**</span><span class="sxs-lookup"><span data-stu-id="db86d-106">**Number of commands in the distribution database waiting to be applied to this Subscriber**</span></span>  
 <span data-ttu-id="db86d-107">ディストリビューション データベース内のコマンドで、選択したサブスクライバーにまだ配布されていないコマンドの数を示します。</span><span class="sxs-lookup"><span data-stu-id="db86d-107">The number of commands in the distribution database that have not been delivered to the selected Subscriber.</span></span> <span data-ttu-id="db86d-108">コマンドは、1 つの Transact-SQL データ操作言語 (DML) ステートメントまたは 1 つのデータ定義言語 (DDL) ステートメントから構成されます。</span><span class="sxs-lookup"><span data-stu-id="db86d-108">A command consists of one Transact-SQL data manipulation language (DML) statement or one data definition language (DDL) statement.</span></span>  
  
 <span data-ttu-id="db86d-109">**[以前のパフォーマンスに基づく、これらのコマンドの適用にかかる推定時間]**</span><span class="sxs-lookup"><span data-stu-id="db86d-109">**Estimated time to apply these commands, based on past performance**</span></span>  
 <span data-ttu-id="db86d-110">コマンドをサブスクライバーに配布するのに要すると推定される時間を示します。</span><span class="sxs-lookup"><span data-stu-id="db86d-110">The estimated amount of time to deliver commands to the Subscriber.</span></span> <span data-ttu-id="db86d-111">スナップショットを生成してサブスクライバーに適用するのに必要な時間よりもこの値が大きい場合は、サブスクライバーの再初期化を検討してください。</span><span class="sxs-lookup"><span data-stu-id="db86d-111">If this value is greater than the amount of time required to generate and apply a snapshot to the Subscriber, consider reinitializing the Subscriber.</span></span> <span data-ttu-id="db86d-112">詳細については、「 [サブスクリプションの再初期化](reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db86d-112">For more information, see [Reinitialize Subscriptions](reinitialize-subscriptions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db86d-113">参照</span><span class="sxs-lookup"><span data-stu-id="db86d-113">See Also</span></span>  
 <span data-ttu-id="db86d-114">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="db86d-114">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="db86d-115">[レプリケーションモニターを使用したパフォーマンスの監視](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="db86d-115">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 [<span data-ttu-id="db86d-116">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="db86d-116">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
