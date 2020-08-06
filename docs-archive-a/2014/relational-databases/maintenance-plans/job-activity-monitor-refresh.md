---
title: ジョブの利用状況モニターの更新 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f290825f8a776c954ef802b184f7600aea5dc9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640939"
---
# <a name="job-activity-monitor-refresh"></a><span data-ttu-id="ec6d8-102">ジョブの利用状況モニターの更新</span><span class="sxs-lookup"><span data-stu-id="ec6d8-102">Job Activity Monitor Refresh</span></span>
  <span data-ttu-id="ec6d8-103">**[更新の設定]** ダイアログ ボックスを使用すると、ジョブの利用状況モニターでサーバーの利用状況に関する新しい情報を取得する頻度を構成できます。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-103">Use the **Refresh Settings** dialog box to configure how often Job Activity Monitor obtains new information about server activity.</span></span> <span data-ttu-id="ec6d8-104">ジョブの利用状況モニターは、監視対象のサーバーに対してクエリを実行して、[ジョブの利用状況モニター] グリッドの情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-104">Job Activity Monitor must run queries on the monitored server to obtain information for the Job Activity Monitor grid.</span></span> <span data-ttu-id="ec6d8-105">自動更新の間隔を 30 秒未満に設定すると、これらのクエリを実行する時間がサーバーのパフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-105">When the auto-refresh interval is set to less than 30 seconds, the time used to run these queries can affect server performance.</span></span>  
  
 <span data-ttu-id="ec6d8-106">このダイアログを開くには、ジョブの利用状況モニターの **[状態]** セクションの **[更新の設定を表示します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-106">To open this dialog, click **View refresh settings**, in the **Status** section of Job Activity Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ec6d8-107">オプション</span><span class="sxs-lookup"><span data-stu-id="ec6d8-107">Options</span></span>  
 <span data-ttu-id="ec6d8-108">**[次の間隔で自動更新する]**</span><span class="sxs-lookup"><span data-stu-id="ec6d8-108">**Auto-refresh every**</span></span>  
 <span data-ttu-id="ec6d8-109">オンにすると、ジョブの利用状況モニターの情報の自動更新が有効になります。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-109">Check to initiate automatic refreshing of Activity Monitor information.</span></span> <span data-ttu-id="ec6d8-110">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-110">This is off by default.</span></span>  
  
 <span data-ttu-id="ec6d8-111">**seconds**</span><span class="sxs-lookup"><span data-stu-id="ec6d8-111">**seconds**</span></span>  
 <span data-ttu-id="ec6d8-112">自動更新の間隔 (秒数) です。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-112">The number of seconds between auto-refresh attempts.</span></span> <span data-ttu-id="ec6d8-113">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-113">Defaults to 60 seconds.</span></span> <span data-ttu-id="ec6d8-114">5 秒以下に設定した場合は、5 秒ごとに情報が更新されます。</span><span class="sxs-lookup"><span data-stu-id="ec6d8-114">Refreshes every 5 seconds when set to 5 or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec6d8-115">参照</span><span class="sxs-lookup"><span data-stu-id="ec6d8-115">See Also</span></span>  
 [<span data-ttu-id="ec6d8-116">ジョブの利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="ec6d8-116">Monitor Job Activity</span></span>](../../ssms/agent/monitor-job-activity.md)  
  
  
