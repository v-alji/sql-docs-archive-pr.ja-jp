---
title: 'レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce20f4ed8863ede34c8709d2b77bf032e7d14a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713033"
---
# <a name="lesson-1-publishing-data-using-transactional-replication"></a><span data-ttu-id="b6d74-102">レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="b6d74-102">Lesson 1: Publishing Data Using Transactional Replication</span></span>
  <span data-ttu-id="b6d74-103"> このレッスンでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してトランザクション パブリケーションを作成し、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの **Product** テーブルからフィルター選択したサブセットをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-103">In this lesson, you will create a transactional publication using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to publish a filtered subset of the **Product** table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="b6d74-104">また、ディストリビューション エージェントにより使用される SQL Server ログインをパブリケーション アクセス リスト (PAL) に追加します。</span><span class="sxs-lookup"><span data-stu-id="b6d74-104">You will also add the SQL Server login used by the Distribution Agent to the publication access list (PAL).</span></span> <span data-ttu-id="b6d74-105">このチュートリアルを行うには、前のチュートリアル「 [レプリケーションに備えたサーバーの準備](tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6d74-105">Before starting this tutorial, you should have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="b6d74-106">パブリケーションを作成し、アーティクルを定義するには</span><span class="sxs-lookup"><span data-stu-id="b6d74-106">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="b6d74-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="b6d74-107">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="b6d74-108">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを右クリックして、 **[新しいパブリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-108">Expand the **Replication** folder, right-click the **Local Publications** folder, and click **New Publication**.</span></span>  
  
     <span data-ttu-id="b6d74-109">パブリケーションの新規作成ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="b6d74-109">The Publication Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="b6d74-110">[パブリケーション データベース] ページで [ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-110">On the Publication Database page, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="b6d74-111">[パブリケーションの種類] ページで **[トランザクション パブリケーション]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-111">On the Publication Type page, select **Transactional publication**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="b6d74-112">[アーティクル] ページで、 **[テーブル]** ノードを展開して **[Product]** チェック ボックスをオンにします。次に、 **[Product]** を展開して、 **[ListPrice]** チェック ボックスと **[StandardCost]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-112">On the Articles page, expand the **Tables** node, select the **Product** check box, then expand **Product** and clear the **ListPrice** and **StandardCost** check boxes.</span></span> <span data-ttu-id="b6d74-113">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-113">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="b6d74-114">[テーブル行のフィルター選択] ページで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-114">On the Filter Table Rows page, click **Add**.</span></span>  
  
7.  <span data-ttu-id="b6d74-115">**[フィルターの追加]** ダイアログ ボックスで **[SafetyStockLevel]** 列をクリックし、右矢印をクリックして、フィルター選択クエリの Filter ステートメントの WHERE 句にこの列を追加します。さらに、WHERE 句を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="b6d74-115">In the **Add Filter** dialog box, click the **SafetyStockLevel** column, click the right arrow to add the column to the Filter statement WHERE clause of the filter query, and modify the WHERE clause as follows:</span></span>  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  <span data-ttu-id="b6d74-116">[**OK**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-116">Click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="b6d74-117">**[スナップショットをすぐに作成し、サブスクリプションを初期化できるようにそのスナップショットを保持する]** チェック ボックスをオンにして、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-117">Select the **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** check box, and click **Next**.</span></span>  
  
10. <span data-ttu-id="b6d74-118">[エージェント セキュリティ] ページで、 **[スナップショット エージェントのセキュリティ設定を使用する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-118">On the Agent Security page, clear **Use the security settings from the Snapshot Agent** check box.</span></span>  
  
11. <span data-ttu-id="b6d74-119">スナップショットエージェントの [**セキュリティの設定**] をクリックし、[ \<_Machine_Name> **プロセスアカウント**] ボックスに「_**\ repl_snapshot** 」と入力して、このアカウントのパスワードを入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-119">Click **Security Settings** for the Snapshot Agent, enter \<_Machine_Name>_**\repl_snapshot** in the **Process account** box, supply the password for this account, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="b6d74-120">同様に、ログ リーダー エージェントのプロセス アカウントとして repl_logreader を設定し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-120">Repeat the previous step to set repl_logreader as the process account for the Log Reader Agent, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="b6d74-121">[ウィザードの完了] ページで、 **[パブリケーション名]** ボックスに「 **AdvWorksProductTrans** 」と入力し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-121">On the Complete the Wizard page, type **AdvWorksProductTrans** in the **Publication name** box, and click **Finish**.</span></span>  
  
14. <span data-ttu-id="b6d74-122">パブリケーションが作成されたら、 **[閉じる]** をクリックしてウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b6d74-122">After the publication is created, click **Close** to complete the wizard.</span></span>  
  
### <a name="to-view-the-status-of-snapshot-generation"></a><span data-ttu-id="b6d74-123">スナップショット生成の状態を表示するには</span><span class="sxs-lookup"><span data-stu-id="b6d74-123">To view the status of snapshot generation</span></span>  
  
1.  <span data-ttu-id="b6d74-124">でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b6d74-124">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="b6d74-125">**[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksProductTrans]** を右クリックして、 **[スナップショット エージェントの状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-125">In the **Local Publications** folder, right-click **AdvWorksProductTrans**, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="b6d74-126">パブリケーションのスナップショット エージェントの現在の状態が表示されるので、</span><span class="sxs-lookup"><span data-stu-id="b6d74-126">The current status of the Snapshot Agent job for the publication is displayed.</span></span> <span data-ttu-id="b6d74-127">スナップショット ジョブが正常に終了していることを確認してから次のレッスンに進みます。</span><span class="sxs-lookup"><span data-stu-id="b6d74-127">Verify that the snapshot job has succeeded before you continue to the next lesson.</span></span>  
  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a><span data-ttu-id="b6d74-128">ディストリビューション エージェントのログインを PAL に追加するには</span><span class="sxs-lookup"><span data-stu-id="b6d74-128">To add the Distribution Agent login to the PAL</span></span>  
  
1.  <span data-ttu-id="b6d74-129">でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b6d74-129">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="b6d74-130">**[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksProductTrans]** パブリケーションを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-130">In the **Local Publications** folder, right-click **AdvWorksProductTrans**, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="b6d74-131">**[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d74-131">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="b6d74-132">**[パブリケーション アクセス リスト]** ページを選択して、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-132">Select the **Publication Access List** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="b6d74-133">**[パブリケーション アクセスの追加]** ダイアログ ボックスで、_<コンピューター名>_**\repl_distribution** を選択して **[OK]** をクリックし、</span><span class="sxs-lookup"><span data-stu-id="b6d74-133">\In the **Add Publication Access** dialog box, select _<Machine_Name>_**\repl_distribution** and click **OK**.</span></span> <span data-ttu-id="b6d74-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-134">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b6d74-135">次の手順</span><span class="sxs-lookup"><span data-stu-id="b6d74-135">Next Steps</span></span>  
 <span data-ttu-id="b6d74-136">ここでは、トランザクション パブリケーションを作成しました。</span><span class="sxs-lookup"><span data-stu-id="b6d74-136">You have successfully created the transactional publication.</span></span> <span data-ttu-id="b6d74-137">次は、このパブリケーションをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="b6d74-137">Next, you will subscribe to this publication.</span></span> <span data-ttu-id="b6d74-138">「 [レッスン 2: トランザクション パブリケーションへのサブスクリプションの作成](lesson-2-creating-a-subscription-to-the-transactional-publication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6d74-138">See [Lesson 2: Creating a Subscription to the Transactional Publication](lesson-2-creating-a-subscription-to-the-transactional-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d74-139">参照</span><span class="sxs-lookup"><span data-stu-id="b6d74-139">See Also</span></span>  
 <span data-ttu-id="b6d74-140">[パブリッシュされたデータのフィルター処理](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="b6d74-140">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="b6d74-141">[Define an Article](publish/define-an-article.md) </span><span class="sxs-lookup"><span data-stu-id="b6d74-141">[Define an Article](publish/define-an-article.md) </span></span>  
 [<span data-ttu-id="b6d74-142">スナップショットの作成および適用</span><span class="sxs-lookup"><span data-stu-id="b6d74-142">Create and Apply the Snapshot</span></span>](create-and-apply-the-snapshot.md)  
  
  
