---
title: CPU のアイドル時間と期間の設定 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1660f6d70977b8f590a18adf952a6a19f32a26cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742737"
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a><span data-ttu-id="df659-102">CPU のアイドル時間と期間の設定 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="df659-102">Set CPU Idle Time and Duration (SQL Server Management Studio)</span></span>
  <span data-ttu-id="df659-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、サーバーの CPU アイドル状態を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="df659-103">This topic explains how to define the CPU idle condition for your server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="df659-104">CPU アイドルの定義は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがイベントに応答する方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="df659-104">The CPU idle definition influences how [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent responds to events.</span></span> <span data-ttu-id="df659-105">たとえば、CPU の平均使用率が 10% 未満になり、そのレベルで 10 分間経過したときを CPU アイドル状態であると定義するとします。</span><span class="sxs-lookup"><span data-stu-id="df659-105">For example, suppose that you define the CPU idle condition as when the average CPU usage falls below 10 percent and remains at this level for 10 minutes.</span></span> <span data-ttu-id="df659-106">この場合に、サーバーの CPU がアイドル状態になるたびにジョブが実行されるように定義していると、CPU 使用率が 10% 未満になり、その使用率のまま 10 分間経過したときにジョブが開始されます。</span><span class="sxs-lookup"><span data-stu-id="df659-106">Then if you have defined jobs to execute whenever the server CPU reaches an idle condition, the job will start when the CPU usage falls below 10 percent and remains at that level for 10 minutes.</span></span> <span data-ttu-id="df659-107">このジョブがサーバーのパフォーマンスに大きな影響を及ぼす場合、CPU アイドル状態をどのように定義するかが重要になります。</span><span class="sxs-lookup"><span data-stu-id="df659-107">If this is a job that significantly impacts the performance of your server, how you define the CPU idle condition is important.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="df659-108">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="df659-108">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a><span data-ttu-id="df659-109">CPU のアイドル時間と期間を設定するには</span><span class="sxs-lookup"><span data-stu-id="df659-109">To set CPU idle time and duration</span></span>  
  
1.  <span data-ttu-id="df659-110">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="df659-110">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="df659-111">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックして、 **[詳細設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="df659-111">Right-click **SQL Server Agent**, click **Properties**, and select the **Advanced** page.</span></span>  
  
3.  <span data-ttu-id="df659-112">**[CPU のアイドル状態]** で、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="df659-112">Under **Idle CPU condition**, do the following:</span></span>  
  
    -   <span data-ttu-id="df659-113">**[CPU のアイドル状態を定義する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="df659-113">Check **Define idle CPU condition.**</span></span>  
  
    -   <span data-ttu-id="df659-114">**[CPU の平均使用量が次の値以下になったとき]** ボックスで、比率を指定します (全 CPU 共通)。</span><span class="sxs-lookup"><span data-stu-id="df659-114">Specify a percentage for the **Average CPU usage falls below** (across all CPUs) box.</span></span> <span data-ttu-id="df659-115">これにより、CPU がその値を下回ったときにアイドル状態と見なす使用率が設定されます。</span><span class="sxs-lookup"><span data-stu-id="df659-115">This sets the usage level that the CPU must fall below before it is considered idle.</span></span>  
  
    -   <span data-ttu-id="df659-116">**[かつ、この使用率以下で次の期間を経過]** ボックスで、秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="df659-116">Specify a number of seconds for the **And remains below this level for** box.</span></span> <span data-ttu-id="df659-117">低い CPU 使用率のまま、ここで設定した秒数が経過すると、CPU がアイドル状態であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="df659-117">This sets the duration that the minimum CPU usage must remain at before it is considered idle.</span></span>  
  
  
