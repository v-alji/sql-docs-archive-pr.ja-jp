---
title: SQL Server エージェントの Alerts オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9aa6fa871730af8cf129b3ea6b0aa4f1853d7e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633808"
---
# <a name="sql-server-agent-alerts-object"></a><span data-ttu-id="59256-102">SQL Server エージェントの Alerts オブジェクト</span><span class="sxs-lookup"><span data-stu-id="59256-102">SQL Server Agent, Alerts Object</span></span>
  <span data-ttu-id="59256-103">SQL Server エージェントの **Alerts** パフォーマンス オブジェクトには、SQL Server エージェントの警告に関する情報を報告するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="59256-103">The SQL Server Agent **Alerts** performance object contains performance counters that report information about SQL Server Agent alerts.</span></span> <span data-ttu-id="59256-104">次の表は、このオブジェクトに含まれているカウンターを示します。</span><span class="sxs-lookup"><span data-stu-id="59256-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="59256-105">次の表では、 **SQLAgent:Alerts** オブジェクトのカウンターを示します。</span><span class="sxs-lookup"><span data-stu-id="59256-105">The table below contains the **SQLAgent:Alerts** counters.</span></span>  
  
|<span data-ttu-id="59256-106">名前</span><span class="sxs-lookup"><span data-stu-id="59256-106">Name</span></span>|<span data-ttu-id="59256-107">説明</span><span class="sxs-lookup"><span data-stu-id="59256-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="59256-108">**Activated alerts**</span><span class="sxs-lookup"><span data-stu-id="59256-108">**Activated alerts**</span></span>|<span data-ttu-id="59256-109">最後に SQL Server エージェントが再起動されてから SQL Server エージェントによってアクティブ化された警告の合計数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="59256-109">This counter reports the total number of alerts that SQL Server Agent has activated since the last time that SQL Server Agent restarted.</span></span>|  
|<span data-ttu-id="59256-110">**Alerts activated/minute**</span><span class="sxs-lookup"><span data-stu-id="59256-110">**Alerts activated/minute**</span></span>|<span data-ttu-id="59256-111">1 分間に SQL Server エージェントによってアクティブ化された警告の数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="59256-111">This counter reports the number of alerts that SQL Server Agent activated within the last minute.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="59256-112">この SQL Server エージェント オブジェクトを使用するには、ユーザーが **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="59256-112">To use this SQL Server Agent object, users must be a member of the **sysadmin** fixed server role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59256-113">参照</span><span class="sxs-lookup"><span data-stu-id="59256-113">See Also</span></span>  
 <span data-ttu-id="59256-114">[Alerts](../../ssms/agent/alerts.md) </span><span class="sxs-lookup"><span data-stu-id="59256-114">[Alerts](../../ssms/agent/alerts.md) </span></span>  
 <span data-ttu-id="59256-115">[パフォーマンス オブジェクトの使用](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="59256-115">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="59256-116">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="59256-116">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
