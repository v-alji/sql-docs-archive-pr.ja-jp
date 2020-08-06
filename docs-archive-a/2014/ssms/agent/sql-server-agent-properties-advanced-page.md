---
title: SQL Server エージェントのプロパティ ([詳細設定] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8ec0d9d7fbd51f9350bf692588f90c292e54f4e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644276"
---
# <a name="sql-server-agent-properties-advanced-page"></a><span data-ttu-id="9239f-102">SQL Server エージェントのプロパティ ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="9239f-102">SQL Server Agent Properties (Advanced Page)</span></span>
  <span data-ttu-id="9239f-103">このページを使用すると、エージェントサービスの詳細プロパティを表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="9239f-103">Use this page to view and modify advanced properties of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9239f-104">Options</span><span class="sxs-lookup"><span data-stu-id="9239f-104">Options</span></span>  
 <span data-ttu-id="9239f-105">**[SQL Server イベントの転送]**</span><span class="sxs-lookup"><span data-stu-id="9239f-105">**SQL Server event forwarding**</span></span>  
 <span data-ttu-id="9239f-106">このカテゴリのオプションを使用して、イベントの転送をアクティブにしたり、構成したりします。</span><span class="sxs-lookup"><span data-stu-id="9239f-106">The options in this category activate and configure event forwarding.</span></span>  
  
 <span data-ttu-id="9239f-107">**[イベントを別のサーバーに転送する]**</span><span class="sxs-lookup"><span data-stu-id="9239f-107">**Forward events to a different server**</span></span>  
 <span data-ttu-id="9239f-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント イベントを別のサーバーに転送します。</span><span class="sxs-lookup"><span data-stu-id="9239f-108">Forwards [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events to a different server.</span></span>  
  
 <span data-ttu-id="9239f-109">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="9239f-109">**Server**</span></span>  
 <span data-ttu-id="9239f-110">イベントの転送先のサーバー名を選択します。</span><span class="sxs-lookup"><span data-stu-id="9239f-110">Select the name of the server to forward events to.</span></span>  
  
 <span data-ttu-id="9239f-111">**[未処理のイベント]**</span><span class="sxs-lookup"><span data-stu-id="9239f-111">**Unhandled events**</span></span>  
 <span data-ttu-id="9239f-112">未処理のイベントのみを指定のサーバーに転送します。</span><span class="sxs-lookup"><span data-stu-id="9239f-112">Forwards only unhandled events to the specified server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9239f-113">エージェントは、警告が返されないイベントのみを転送します。</span><span class="sxs-lookup"><span data-stu-id="9239f-113">Agent forwards only events that no alert responds to.</span></span>  
  
 <span data-ttu-id="9239f-114">**[すべてのイベント]**</span><span class="sxs-lookup"><span data-stu-id="9239f-114">**All events**</span></span>  
 <span data-ttu-id="9239f-115">すべてのイベントを転送します。</span><span class="sxs-lookup"><span data-stu-id="9239f-115">Forwards all events.</span></span> <span data-ttu-id="9239f-116">ローカル インスタンスの警告がイベントに応答した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはイベントの転送と警告の処理の両方を行います。</span><span class="sxs-lookup"><span data-stu-id="9239f-116">When an alert in the local instance responds to the event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent will both forward the event and process the alert.</span></span>  
  
 <span data-ttu-id="9239f-117">**[次のレベル以上のイベント発生時]**</span><span class="sxs-lookup"><span data-stu-id="9239f-117">**If event has severity at or above**</span></span>  
 <span data-ttu-id="9239f-118">指定された重大度レベル以上のイベントのみを転送します。</span><span class="sxs-lookup"><span data-stu-id="9239f-118">Forwards only events with a severity level at or above the level specified.</span></span>  
  
 <span data-ttu-id="9239f-119">**[CPU のアイドル状態]**</span><span class="sxs-lookup"><span data-stu-id="9239f-119">**Idle CPU Condition**</span></span>  
 <span data-ttu-id="9239f-120">このカテゴリのオプションは、CPU のアイドル スケジュールで実行がスケジュールされたジョブを、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するための条件を定義します。</span><span class="sxs-lookup"><span data-stu-id="9239f-120">The options in this category define the conditions under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs jobs scheduled to run on the Idle CPU schedule.</span></span>  
  
 <span data-ttu-id="9239f-121">**[CPU のアイドル状態を定義する]**</span><span class="sxs-lookup"><span data-stu-id="9239f-121">**Define idle CPU condition**</span></span>  
 <span data-ttu-id="9239f-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントにより CPU がアイドル状態であると見なされる条件を定義します。</span><span class="sxs-lookup"><span data-stu-id="9239f-122">Defines the conditions under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent considers the CPU to be idle.</span></span>  
  
 <span data-ttu-id="9239f-123">**[CPU の平均使用量が次の値以下になったとき]**</span><span class="sxs-lookup"><span data-stu-id="9239f-123">**Average CPU usage falls below**</span></span>  
 <span data-ttu-id="9239f-124">CPU がアイドル状態であると見なされる CPU の使用量の割合です。</span><span class="sxs-lookup"><span data-stu-id="9239f-124">Percentage of CPU usage below which the CPU is considered to be idle.</span></span>  
  
 <span data-ttu-id="9239f-125">**[かつ、この使用率以下で次の期間を経過]**</span><span class="sxs-lookup"><span data-stu-id="9239f-125">**And remains below this level for**</span></span>  
 <span data-ttu-id="9239f-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが CPU のアイドル スケジュールのジョブを実行する前に、CPU の平均使用量が指定されたレベルを下回っていなければならない時間です。</span><span class="sxs-lookup"><span data-stu-id="9239f-126">Amount of time that the average CPU must below the level specified before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs jobs on the Idle CPU schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9239f-127">参照</span><span class="sxs-lookup"><span data-stu-id="9239f-127">See Also</span></span>  
 <span data-ttu-id="9239f-128">[スケジュールを作成してジョブにアタッチする](create-and-attach-schedules-to-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="9239f-128">[Create and Attach Schedules to Jobs](create-and-attach-schedules-to-jobs.md) </span></span>  
 [<span data-ttu-id="9239f-129">イベントの管理</span><span class="sxs-lookup"><span data-stu-id="9239f-129">Manage Events</span></span>](manage-events.md)  
  
  
