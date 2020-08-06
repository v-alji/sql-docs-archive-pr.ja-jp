---
title: SQL Server データベースの警告のセットアップ (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 090eeda2c134857df18d083ce06d460214aa4dfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645567"
---
# <a name="set-up-a-sql-server-database-alert-windows"></a><span data-ttu-id="59fff-102">SQL Server データベースの警告のセットアップ (Windows)</span><span class="sxs-lookup"><span data-stu-id="59fff-102">Set Up a SQL Server Database Alert (Windows)</span></span>
  <span data-ttu-id="59fff-103">システム モニターを使用すると、システム モニター カウンターがしきい値に到達した場合に生成される警告を作成できます。</span><span class="sxs-lookup"><span data-stu-id="59fff-103">Using System Monitor, you can create an alert to be raised when a threshold value for a System Monitor counter has been reached.</span></span> <span data-ttu-id="59fff-104">システム モニターは、この警告に応答して、警告状況を処理するために記述されたカスタム アプリケーションなどのアプリケーションを起動できます。</span><span class="sxs-lookup"><span data-stu-id="59fff-104">In response to the alert, System Monitor can launch an application, such as a custom application written to handle the alert condition.</span></span> <span data-ttu-id="59fff-105">たとえば、デッドロックの数が特定の値を超えたときに生成される警告を作成できます。</span><span class="sxs-lookup"><span data-stu-id="59fff-105">For example, you can create an alert that is raised when the number of deadlocks exceeds a specific value.</span></span>  
  
 <span data-ttu-id="59fff-106">警告は、Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用して定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="59fff-106">Alerts also can be defined using Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="59fff-107">詳細については、「 [警告](../../ssms/agent/alerts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59fff-107">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
### <a name="to-set-up-a-sql-server-database-alert"></a><span data-ttu-id="59fff-108">SQL Server データベースの警告をセットアップするには</span><span class="sxs-lookup"><span data-stu-id="59fff-108">To set up a SQL Server database alert</span></span>  
  
1.  <span data-ttu-id="59fff-109">[パフォーマンス] ウィンドウのナビゲーション ツリーで、 **[パフォーマンス ログと警告]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="59fff-109">On the navigation tree of the Performance window, expand **Performance Logs and Alerts**.</span></span>  
  
2.  <span data-ttu-id="59fff-110">**[警告]** を右クリックし、 **[新しい警告の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59fff-110">Right-click **Alerts**, and then click **New Alert Settings**.</span></span>  
  
3.  <span data-ttu-id="59fff-111">**[新しい警告の設定]** ダイアログ ボックスで、新しい警告の名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59fff-111">In the **New Alert Settings** dialog box, type a name for the new alert, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="59fff-112">新しい警告のダイアログ ボックスの **[全般]** タブで、 **[コメント]** を追加し、 **[追加]** をクリックして警告にカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="59fff-112">On the **General** tab of the dialog box for the new alert, add a **Comment**, and click **Add** to add a counter to the alert.</span></span>  
  
     <span data-ttu-id="59fff-113">各警告には、少なくとも 1 つのカウンターを含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="59fff-113">All alerts must have at least one counter.</span></span>  
  
5.  <span data-ttu-id="59fff-114">[カウンターの追加] ダイアログ ボックスで、 **[パフォーマンス オブジェクト]** の一覧から SQL Server オブジェクトを選択し、 **[一覧からカウンターを選ぶ]** からカウンターを選択します。</span><span class="sxs-lookup"><span data-stu-id="59fff-114">In the Add Counters dialog box, select a SQL Server object from the **Performance Object** list, and then select a counter from the **Select counters from list**.</span></span>  
  
6.  <span data-ttu-id="59fff-115">警告にカウンターを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59fff-115">To add the counter to the alert, click **Add**.</span></span> <span data-ttu-id="59fff-116">カウンターの追加を続行するか、 **[閉じる]** をクリックして新しい警告のダイアログ ボックスに戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="59fff-116">You can continue to add counters, or you can click **Close** to return to the dialog box for the new alert.</span></span>  
  
7.  <span data-ttu-id="59fff-117">新しい警告のダイアログ ボックスで、 **[Alert when the value is (次の値になったら警告する)]** の一覧の **[Over (超過)]** または **[Under (以下)]** をクリックし、 **[Limit (制限値)]** にしきい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="59fff-117">In the new alert dialog box, click either **Over** or **Under**in the **Alert when the value is** list, and then enter a threshold value in **Limit**.</span></span>  
  
     <span data-ttu-id="59fff-118">警告は、カウンターの値がしきい値を超えたとき、またはしきい値以下になったときに生成されます。これは **[Over (超過)]** または **[Under (以下)]** のどちらをクリックしたかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="59fff-118">The alert is generated when the value for the counter is more than or less than the threshold value (depending on whether you clicked **Over** or **Under**).</span></span>  
  
8.  <span data-ttu-id="59fff-119">**[Sample data every (データのサンプル間隔)]** ボックスで、サンプリング周期を設定します。</span><span class="sxs-lookup"><span data-stu-id="59fff-119">In the **Sample data every** boxes, set the sampling frequency.</span></span>  
  
9. <span data-ttu-id="59fff-120">**[アクション]** タブで、警告がトリガーされたときに実行される操作を設定します。</span><span class="sxs-lookup"><span data-stu-id="59fff-120">On the **Action** tab, set actions to occur every time the alert is triggered.</span></span>  
  
10. <span data-ttu-id="59fff-121">**[スケジュール]** タブで、警告スキャンの開始と停止のスケジュールを設定します。</span><span class="sxs-lookup"><span data-stu-id="59fff-121">On the **Schedule** tab, set the start and stop schedule for the alert scan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59fff-122">参照</span><span class="sxs-lookup"><span data-stu-id="59fff-122">See Also</span></span>  
 [<span data-ttu-id="59fff-123">SQL Server データベース警告の作成</span><span class="sxs-lookup"><span data-stu-id="59fff-123">Create a SQL Server Database Alert</span></span>](../performance-monitor/create-a-sql-server-database-alert.md)  
  
  
