---
title: 'レッスン 1 : マージ レプリケーションを使用したデータのパブリッシュ | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: c3c6e0b6-54cd-4b7d-8efb-2cefe14fcd7f
author: rothja
ms.author: jroth
ms.openlocfilehash: ba1d8829d84c02d1436013af80de4bf0979049e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721369"
---
# <a name="lesson-1-publishing-data-using-merge-replication"></a><span data-ttu-id="5a0ba-102">レッスン 1 : マージ レプリケーションを使用したデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="5a0ba-102">Lesson 1: Publishing Data Using Merge Replication</span></span>
  <span data-ttu-id="5a0ba-103"> このレッスンでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してマージ パブリケーションを作成し、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの **Employee** テーブル、**SalesOrderHeader** テーブル、および **SalesOrderDetail** テーブルのサブセットをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-103">In this lesson, you will create a merge publication using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to publish a subset of the **Employee**, **SalesOrderHeader**, and **SalesOrderDetail** tables in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="5a0ba-104">ここでは、パラメーター化された行フィルターを使ってこれらのテーブルをフィルター処理し、サブスクリプションごとに一意のデータ部分が含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-104">These tables are filtered with parameterized row filters so that each subscription contains a unique partition of the data.</span></span> <span data-ttu-id="5a0ba-105">また、マージ エージェントにより使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインをパブリケーション アクセス リスト (PAL) に追加します。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-105">You will also add the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Merge Agent to the publication access list (PAL).</span></span> <span data-ttu-id="5a0ba-106">このチュートリアルを学習するには、前のチュートリアル「 [レプリケーションに備えたサーバーの準備](tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-106">This tutorial requires that you have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="5a0ba-107">パブリケーションを作成し、アーティクルを定義するには</span><span class="sxs-lookup"><span data-stu-id="5a0ba-107">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="5a0ba-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-108">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="5a0ba-109">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** を右クリックして、 **[新しいパブリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-109">Expand the **Replication** folder, right-click **Local Publications**, and click **New Publication**.</span></span>  
  
     <span data-ttu-id="5a0ba-110">パブリケーションの新規作成ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-110">The Publication Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="5a0ba-111">[パブリケーション データベース] ページで [ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-111">On the Publication Database page, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="5a0ba-112">[パブリケーションの種類] ページで、 **[マージ パブリケーション]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-112">On the Publication Type page, select **Merge publication**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="5a0ba-113">[サブスクライバーの種類] ページで、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のみが選択されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-113">On the Subscriber Types page, ensure that only [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later is selected, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="5a0ba-114">[アーティクル] ページで、 **[テーブル]** ノードを展開して **[SalesOrderHeader]** および **[SalesOrderDetail]** を選択します。次に **[Employee]** を展開し、 **[EmployeeID]** または **[LoginID]** を選択して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-114">On the Articles page, expand the **Tables** node, select **SalesOrderHeader** and **SalesOrderDetail**, then expand **Employee**, select **EmployeeID** or **LoginID**, and then click **Next**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="5a0ba-115">その他の必要な列が自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-115">Additional required columns are automatically selected.</span></span> <span data-ttu-id="5a0ba-116">自動的に選択された列のいずれかを選択すると、 **[パブリッシュするオブジェクト]** の一覧の下に、その列が必要な理由についての説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-116">Select any of  the automatically selected columns and view the note below the **Objects to publish** list for an explanation why the column is required.</span></span>  
  
7.  <span data-ttu-id="5a0ba-117">[テーブル行のフィルター選択] ページで、 **[追加]** をクリックして **[フィルターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-117">On the Filter Table Rows page, click **Add** and then click **Add Filter**.</span></span>  
  
8.  <span data-ttu-id="5a0ba-118">**[フィルターの追加]** ダイアログ ボックスの **[フィルターを適用するテーブルを選択します。]** で **[Employee (HumanResources)]** を選択します。 **[LoginID]** 列をクリックして、右矢印をクリックし、フィルター選択クエリの WHERE 句にこの列を追加します。WHERE 句を次のように修正します。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-118">In the **Add Filter** dialog box, select **Employee (HumanResources)** in **Select the table to filter**, click the **LoginID** column, click the right arrow to add the column to the WHERE clause of the filter query, and modify the WHERE clause as follows:</span></span>  
  
    ```  
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
9. <span data-ttu-id="5a0ba-119">**[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-119">Click **A row from this table will go to only one subscription**, and click **OK**.</span></span>  
  
10. <span data-ttu-id="5a0ba-120">**[テーブル行のフィルター選択]** ページで、 **[Employee (Human Resources)]**、 **[追加]** の順にクリックし、 **[選択したフィルターを拡張するために結合を追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-120">On the **Filter Table Rows** page, click **Employee (Human Resources)**, click **Add,** and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
11. <span data-ttu-id="5a0ba-121">**[結合の追加]** ダイアログ ボックスで、 **[結合テーブル]** の下の **[Sales.SalesOrderHeader]** をクリックして、 **[JOIN ステートメントを手動で作成する]** をクリックし、JOIN ステートメントを次のように完成させます。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-121">In the **Add Join** dialog box, select **Sales.SalesOrderHeader** under **Joined table**, click **Write the join statement manually**, and complete the join statement as follows:</span></span>  
  
    ```  
    ON Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
    ```  
  
12. <span data-ttu-id="5a0ba-122">**[結合オプションを指定します]** で、 **[一意キー]** を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-122">In **Specify join options**, select **Unique key**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="5a0ba-123">[テーブル行のフィルター選択] ページで、 **[SalesOrderHeader]**、 **[追加]** の順にクリックし、 **[選択したフィルターを拡張するために結合を追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-123">On the Filter Table Rows page, click **SalesOrderHeader**, click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
14. <span data-ttu-id="5a0ba-124">**[結合の追加]** ダイアログ ボックスで、 **[結合テーブル]** の下の **[Sales.SalesOrderDetail]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-124">In the **Add Join** dialog box, select **Sales.SalesOrderDetail** under **Joined table**.</span></span>  
  
15. <span data-ttu-id="5a0ba-125">**[JOIN ステートメントを手動で作成する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-125">Click **Write the join statement manually**.</span></span>  
  
16. <span data-ttu-id="5a0ba-126">**[フィルター選択されたテーブルの列]** で、 **[BusinessEntityID]** を選択し、矢印ボタンをクリックして列名を JOIN ステートメントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-126">In **Filtered table columns**, select **BusinessEntityID**, then click the arrow button to copy the column name to the loin statement.</span></span>  
  
17. <span data-ttu-id="5a0ba-127">**[JOIN ステートメント]** ボックスで、次のように JOIN ステートメントを完成させます。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-127">In the **Join statement** box, complete the join statement as follows:</span></span>  
  
    ```  
    ON Employee.BusinessEntityID = SalesOrderHeader.SalesPersonID  
    ```  
  
18. <span data-ttu-id="5a0ba-128">**[結合オプションを指定します]** で、 **[一意キー]** を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-128">In **Specify join options**, select **Unique key**, and then click **OK**.</span></span>  
  
19. <span data-ttu-id="5a0ba-129">**[テーブル行のフィルター選択]** ページで、 **[SalesOrderHeader (Sales)]**、 **[追加]** の順にクリックし、 **[選択したフィルターを拡張するために結合を追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-129">On the **Filter Table Rows** page, click **SalesOrderHeader (Sales)**, click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
20. <span data-ttu-id="5a0ba-130">**[結合の追加]** ダイアログボックスで、 **[結合テーブル]** の下の **[Sales.SalesOrderDetail]** をクリックして **[OK]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-130">In the **Add Join** dialog box, select **Sales.SalesOrderDetail** under **Joined table**, click **OK**, and then click **Next**.</span></span>  
  
21. <span data-ttu-id="5a0ba-131">**[スナップショットをすぐに作成する]** を選択し、 **[以下のスケジュールでスナップショット エージェントを実行する]** をオフにして、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-131">Select **Create a snapshot immediately**, clear **Schedule the snapshot agent to run at the following times**, and click **Next**.</span></span>  
  
22. <span data-ttu-id="5a0ba-132">[エージェントセキュリティ] ページで、[**セキュリティ設定**] をクリックし、[ \<_Machine_Name> **プロセスアカウント**] ボックスに「_**\ repl_snapshot** 」と入力して、このアカウントのパスワードを入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-132">On the Agent Security page, click **Security Settings**, type \<_Machine_Name>_**\repl_snapshot** in the **Process account** box, supply the password for this account, and then click **OK**.</span></span> <span data-ttu-id="5a0ba-133">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-133">Click **Finish**.</span></span>  
  
23. <span data-ttu-id="5a0ba-134">[ウィザードの完了] ページで、 **[パブリケーション名]** ボックスに「 **AdvWorksSalesOrdersMerge** 」と入力し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-134">On the Complete the Wizard page, enter **AdvWorksSalesOrdersMerge** in the **Publication name** box and click **Finish**.</span></span>  
  
24. <span data-ttu-id="5a0ba-135">パブリケーションが作成されたら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-135">After the publication is created, click **Close**.</span></span>  
  
### <a name="to-view-the-status-of-snapshot-generation"></a><span data-ttu-id="5a0ba-136">スナップショット生成の状態を表示するには</span><span class="sxs-lookup"><span data-stu-id="5a0ba-136">To view the status of snapshot generation</span></span>  
  
1.  <span data-ttu-id="5a0ba-137">でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-137">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="5a0ba-138">[ローカル パブリケーション] フォルダーを展開し、 **[AdvWorksSalesOrdersMerge]** を右クリックして、 **[スナップショット エージェントの状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-138">In the Local Publications folder, right-click **AdvWorksSalesOrdersMerge**, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="5a0ba-139">パブリケーションのスナップショット エージェントの現在の状態が表示されるので、</span><span class="sxs-lookup"><span data-stu-id="5a0ba-139">The current status of the Snapshot Agent job for the publication is displayed.</span></span> <span data-ttu-id="5a0ba-140">スナップショット ジョブが正常に終了していることを確認してから次のレッスンに進みます。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-140">Ensure that the snapshot job has succeeded before you continue to the next lesson.</span></span>  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a><span data-ttu-id="5a0ba-141">マージ エージェントのログインを PAL に追加するには</span><span class="sxs-lookup"><span data-stu-id="5a0ba-141">To add the Merge Agent login to the PAL</span></span>  
  
1.  <span data-ttu-id="5a0ba-142">でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-142">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="5a0ba-143">[ローカル パブリケーション] フォルダーを展開し、 **[AdvWorksSalesOrdersMerge]** パブリケーションを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-143">In the Local Publications folder, right-click **AdvWorksSalesOrdersMerge**, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="5a0ba-144">**[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-144">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="5a0ba-145">**[パブリケーション アクセス リスト]** ページを選択して、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-145">Select the **Publication Access List** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="5a0ba-146">[パブリケーション アクセスの追加] ダイアログ ボックスで、_<コンピューター名>_**\repl_merge** を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-146">In the Add Publication Access dialog box, select _<Machine_Name>_**\repl_merge** and click **OK**.</span></span> <span data-ttu-id="5a0ba-147">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-147">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5a0ba-148">次の手順</span><span class="sxs-lookup"><span data-stu-id="5a0ba-148">Next Steps</span></span>  
 <span data-ttu-id="5a0ba-149">ここでは、マージ パブリケーションを作成しました。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-149">You have successfully created the merge publication.</span></span> <span data-ttu-id="5a0ba-150">次は、このパブリケーションをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-150">Next, you will subscribe to this publication.</span></span> <span data-ttu-id="5a0ba-151">「 [レッスン 2: マージ パブリケーションへのサブスクリプションの作成](lesson-2-creating-a-subscription-to-the-merge-publication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-151">See [Lesson 2: Creating a Subscription to the Merge Publication](lesson-2-creating-a-subscription-to-the-merge-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a0ba-152">参照</span><span class="sxs-lookup"><span data-stu-id="5a0ba-152">See Also</span></span>  
 <span data-ttu-id="5a0ba-153">[パブリッシュされたデータのフィルター処理](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="5a0ba-153">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="5a0ba-154">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="5a0ba-154">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="5a0ba-155">アーティクルの定義</span><span class="sxs-lookup"><span data-stu-id="5a0ba-155">Define an Article</span></span>](publish/define-an-article.md)  
  
  
