---
title: 定義済みのレプリケーションの警告の構成 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server replication]
- predefined replication alerts [SQL Server replication]
ms.assetid: c0414147-7ffe-4f9a-908c-71c1b5201584
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa78a08757cc7bbe809c5e3a1808c9632b76763a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741897"
---
# <a name="configure-predefined-replication-alerts-sql-server-management-studio"></a><span data-ttu-id="2c6cc-102">定義済みのレプリケーションの警告の構成 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2c6cc-102">Configure Predefined Replication Alerts (SQL Server Management Studio)</span></span>
  <span data-ttu-id="2c6cc-103">レプリケーションには、以下の定義済みの警告が用意されています。これらは、レプリケーション イベントに応答するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-103">Replication offers the following predefined alerts, which can be configured to respond to replication events:</span></span>  
  
-   <span data-ttu-id="2c6cc-104">**レプリケーション: エージェントが成功しました**</span><span class="sxs-lookup"><span data-stu-id="2c6cc-104">**Replication: agent success**</span></span>    
-   <span data-ttu-id="2c6cc-105">**レプリケーション: エージェントが失敗しました**</span><span class="sxs-lookup"><span data-stu-id="2c6cc-105">**Replication: agent failure**</span></span>    
-   <span data-ttu-id="2c6cc-106">**レプリケーション: エージェントを再試行します**</span><span class="sxs-lookup"><span data-stu-id="2c6cc-106">**Replication: agent retry**</span></span>    
-   <span data-ttu-id="2c6cc-107">**レプリケーション: 有効期限の切れたサブスクリプションを削除しました**</span><span class="sxs-lookup"><span data-stu-id="2c6cc-107">**Replication: expired subscription dropped**</span></span>    
-   <span data-ttu-id="2c6cc-108">**レプリケーション:データ検証で問題が見つかった後、サブスクリプションが再初期化されました**</span><span class="sxs-lookup"><span data-stu-id="2c6cc-108">**Replication: Subscription reinitialized after validation failure**</span></span>    
-   <span data-ttu-id="2c6cc-109">**レプリケーション:サブスクライバーでデータ検証の問題が見つかりました**</span><span class="sxs-lookup"><span data-stu-id="2c6cc-109">**Replication: Subscriber has failed data validation**</span></span>    
-   <span data-ttu-id="2c6cc-110">**レプリケーション:サブスクライバーでデータ検証を正常に終了しました**</span><span class="sxs-lookup"><span data-stu-id="2c6cc-110">**Replication: Subscriber has passed data validation**</span></span>    
-   <span data-ttu-id="2c6cc-111">**レプリケーション: エージェントのカスタム シャットダウン**</span><span class="sxs-lookup"><span data-stu-id="2c6cc-111">**Replication: agent custom shutdown**</span></span>  
  
 <span data-ttu-id="2c6cc-112">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の **[警告]** フォルダー、またはレプリケーション モニターの **[警告]** タブからこれらの警告を構成できます。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-112">Configure these alerts from the **Alerts** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or the **Warnings** tab in Replication Monitor.</span></span> <span data-ttu-id="2c6cc-113">このタブへのアクセスの詳細については、「[レプリケーションモニターを使用して情報を表示し、タスクを実行する](../monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-113">For more information about accessing this tab, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="2c6cc-114">これらの警告に加え、レプリケーション モニターでは、ステータスおよびパフォーマンスに関連する一連の警告を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-114">In addition to these alerts, Replication Monitor provides a set of warnings and alerts related to status and performance.</span></span> <span data-ttu-id="2c6cc-115">詳細については、「[レプリケーションモニターの警告インフラストラクチャでのしきい値と警告の設定](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-115">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md) alerts infrastructure.</span></span> <span data-ttu-id="2c6cc-116">詳細については、「[ユーザー定義イベントの作成](../../../ssms/agent/create-a-user-defined-event.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-116">For more information, see [Create a User-Defined Event](../../../ssms/agent/create-a-user-defined-event.md).</span></span>  
  
### <a name="to-configure-a-predefined-replication-alert-in-management-studio"></a><span data-ttu-id="2c6cc-117">Management Studio で定義済みのレプリケーションの警告を構成するには</span><span class="sxs-lookup"><span data-stu-id="2c6cc-117">To configure a predefined replication alert in Management Studio</span></span>  
  
1.  <span data-ttu-id="2c6cc-118">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-118">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>    
2.  <span data-ttu-id="2c6cc-119">**[SQL Server エージェント]** フォルダーを展開して、 **[警告]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-119">Expand the **SQL Server Agent** folder, and then expand the **Alerts** folder.</span></span>    
3.  <span data-ttu-id="2c6cc-120">レプリケーションの警告を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-120">Right-click a replication alert, and then click **Properties**.</span></span>    
4.  <span data-ttu-id="2c6cc-121">**[\<AlertName> 警告のプロパティ]** ダイアログ ボックスでオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-121">Set options in the **\<AlertName> alert properties** dialog box:</span></span>    
    -   <span data-ttu-id="2c6cc-122">**[全般]** ページで **[有効化]** をクリックし、警告を適用するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-122">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>    
    -   <span data-ttu-id="2c6cc-123">**[応答]** ページで、電子メールを送信するかどうか、または、ジョブを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-123">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
         <span data-ttu-id="2c6cc-124">警告が、 **[レプリケーション:サブスクライバーでデータ検証の問題が見つかりました]** である場合、レプリケーションがこの警告に提供する応答ジョブを指定することができます。 **[ジョブの実行]** を選択し、参照ボタン ( **...** ) をクリックします。 **[ジョブの検索]** ダイアログ ボックスで、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-124">If the alert is **Replication: Subscriber has failed data validation**, you can specify the response job that replication provides for this alert: Select **Execute job**, and then click the browse button (**...**). In the **Locate Job** dialog box, click **Browse**.</span></span> <span data-ttu-id="2c6cc-125">**[オブジェクトの参照]** ダイアログ ボックスで、 **[データ検証で問題が見つかったサブスクリプションの再初期化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-125">In the **Browse for Objects** dialog box, select **Reinitialize subscriptions having data validation failures**.</span></span> <span data-ttu-id="2c6cc-126">両方の開いているダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-126">Click **OK** in both open dialog boxes.</span></span> <span data-ttu-id="2c6cc-127">ジョブを実行するとき、サブスクリプションを再初期化するストアド プロシージャへのリモート プロシージャ コール (RPC) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-127">When the job executes, it uses a remote procedure call (RPC) to a stored procedure that reinitializes the subscription.</span></span> <span data-ttu-id="2c6cc-128">パブリッシャーがリモート ディストリビューターを使用する場合、パブリッシャーでリモート サーバー ログインを定義して、ディストリビューターからパブリッシャーへの RPC を実行可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-128">If the Publisher uses a remote Distributor, you must define a remote server login at the Publisher, so that the RPC from the Distributor to the Publisher can be made.</span></span>   
    -   <span data-ttu-id="2c6cc-129">**[オプション]** ページで、応答のテキストをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-129">On the **Options** page, customize the text of the response.</span></span>    
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-configure-an-alert-for-a-threshold-in-replication-monitor"></a><span data-ttu-id="2c6cc-130">レプリケーション モニターでしきい値に対する警告を構成するには</span><span class="sxs-lookup"><span data-stu-id="2c6cc-130">To configure an alert for a threshold in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="2c6cc-131">**[警告]** タブで、 **[警告の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-131">On the **Warnings** tab click **Configure Alerts**.</span></span>    
2.  <span data-ttu-id="2c6cc-132">**[レプリケーションの警告の構成]** ダイアログ ボックスで警告を選択し、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-132">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>    
3.  <span data-ttu-id="2c6cc-133">**[\<AlertName> 警告のプロパティ]** ダイアログ ボックスでオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-133">Set options in the **\<AlertName> alert properties** dialog box:</span></span>    
    -   <span data-ttu-id="2c6cc-134">**[全般]** ページで **[有効化]** をクリックし、警告を適用するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-134">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>    
    -   <span data-ttu-id="2c6cc-135">**[応答]** ページで、電子メールを送信するかどうか、または、ジョブを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-135">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>    
         <span data-ttu-id="2c6cc-136">警告が、 **[レプリケーション:サブスクライバーでデータ検証の問題が見つかりました]** である場合、レプリケーションがこの警告に提供する応答ジョブを指定することができます。 **[ジョブの実行]** を選択し、参照ボタン ( **...** ) をクリックします。 **[ジョブの検索]** ダイアログ ボックスで、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-136">If the alert is **Replication: Subscriber has failed data validation**, you can specify the response job that replication provides for this alert: Select **Execute job**, and then click the browse button (**...**). In the **Locate Job** dialog box, click **Browse**.</span></span> <span data-ttu-id="2c6cc-137">**[オブジェクトの参照]** ダイアログ ボックスで、 **[データ検証で問題が見つかったサブスクリプションの再初期化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-137">In the **Browse for Objects** dialog box, select **Reinitialize subscriptions having data validation failures**.</span></span> <span data-ttu-id="2c6cc-138">両方の開いているダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-138">Click **OK** in both open dialog boxes.</span></span> <span data-ttu-id="2c6cc-139">ジョブを実行するとき、サブスクリプションを再初期化するストアド プロシージャへのリモート プロシージャ コール (RPC) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-139">When the job executes, it uses a remote procedure call (RPC) to a stored procedure that reinitializes the subscription.</span></span> <span data-ttu-id="2c6cc-140">パブリッシャーがリモート ディストリビューターを使用する場合、パブリッシャーでリモート サーバー ログインを定義して、ディストリビューターからパブリッシャーへの RPC を実行可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-140">If the Publisher uses a remote Distributor, you must define a remote server login at the Publisher, so that the RPC from the Distributor to the Publisher can be made.</span></span>   
    -   <span data-ttu-id="2c6cc-141">**[オプション]** ページで、応答のテキストをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-141">On the **Options** page, customize the text of the response.</span></span>    
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]    
5.  <span data-ttu-id="2c6cc-142">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6cc-142">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6cc-143">参照</span><span class="sxs-lookup"><span data-stu-id="2c6cc-143">See Also</span></span>  
 [<span data-ttu-id="2c6cc-144">レプリケーション エージェント イベントに対する警告の使用</span><span class="sxs-lookup"><span data-stu-id="2c6cc-144">Use Alerts for Replication Agent Events</span></span>](../agents/use-alerts-for-replication-agent-events.md)  
  
  
