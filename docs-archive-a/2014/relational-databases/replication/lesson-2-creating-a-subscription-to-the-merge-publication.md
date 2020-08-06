---
title: 'レッスン 2 : マージ パブリケーションへのサブスクリプションの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
author: rothja
ms.author: jroth
ms.openlocfilehash: 2ca4f9cdf9c40d80b428d65b4201be61c2ea3eae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642034"
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a><span data-ttu-id="9eed4-102">レッスン 2 : マージ パブリケーションへのサブスクリプションの作成</span><span class="sxs-lookup"><span data-stu-id="9eed4-102">Lesson 2: Creating a Subscription to the Merge Publication</span></span>
  <span data-ttu-id="9eed4-103">このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9eed4-103">In this lesson, you will create the subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9eed4-104">次に、サブスクリプション データベースに権限を設定し、新しいサブスクリプション用のフィルター選択データのスナップショットを手動で作成します。</span><span class="sxs-lookup"><span data-stu-id="9eed4-104">You will then set permissions on the subscription database and manually generate the filtered data snapshot for the new subscription.</span></span> <span data-ttu-id="9eed4-105">このレッスンを進めるには、前のレッスン「 [レッスン 1: マージ レプリケーションを使用したデータのパブリッシュ](lesson-1-publishing-data-using-merge-replication.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="9eed4-105">This lesson requires that you have completed the previous lesson, [Lesson 1: Publishing Data Using Merge Replication](lesson-1-publishing-data-using-merge-replication.md).</span></span>  
  
### <a name="to-create-the-subscription"></a><span data-ttu-id="9eed4-106">サブスクリプションを作成するには</span><span class="sxs-lookup"><span data-stu-id="9eed4-106">To create the subscription</span></span>  
  
1.  <span data-ttu-id="9eed4-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、サーバー ノード、 **[レプリケーション]** フォルダーの順に展開して、 **[ローカル サブスクリプション]** フォルダーを右クリックし、 **[新しいサブスクリプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-107">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, expand the **Replication** folder, right-click the **Local Subscriptions** folder, and then click **New Subscriptions**.</span></span>  
  
     <span data-ttu-id="9eed4-108">サブスクリプションの新規作成ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="9eed4-108">The New Subscription Wizard launches.</span></span>  
  
2.  <span data-ttu-id="9eed4-109">**[パブリケーション]** ページで、 **[パブリッシャー]** ボックスの一覧の **[SQL Server パブリッシャーの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-109">On the **Publication** page, click **Find SQL Server Publisher** in the **Publisher** list.</span></span>  
  
3.  <span data-ttu-id="9eed4-110">**[サーバーへの接続]** ダイアログ ボックスで、 **[サーバー名]** ボックスにパブリッシャー インスタンスの名前を入力し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-110">In the **Connect to Server** dialog box, enter the name of the Publisher instance in the **Server name** box, and click **Connect**.</span></span>  
  
4.  <span data-ttu-id="9eed4-111">**[AdvWorksSalesOrdersMerge]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-111">Click **AdvWorksSalesOrdersMerge**, and click **Next**.</span></span>  
  
5.  <span data-ttu-id="9eed4-112">[マージ エージェントの場所] ページで、 **[サブスクライバーで各エージェントを実行する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-112">On the Merge Agent Location page, click **Run each agent at its Subscriber**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="9eed4-113">[サブスクライバー] ページで、サブスクライバー サーバーのインスタンス名を選択し、**[サブスクリプション データベース]** の一覧で **[\<New Database>]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9eed4-113">On the Subscribers page, select the instance name of the Subscriber server, and under **Subscription Database**, select **\<New Database>** from the list.</span></span>  
  
7.  <span data-ttu-id="9eed4-114">**[新しいデータベース]** ダイアログ ボックスで、 **[データベース名]** ボックスに「 **SalesOrdersReplica** 」と入力し、 **[OK]** をクリックして **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-114">In the **New Database** dialog box, enter **SalesOrdersReplica** in the **Database name** box, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="9eed4-115">[マージエージェントセキュリティ] ページで、省略記号ボタン ([**..**.]) をクリックし、[ \<_Machine_Name> **プロセスアカウント**] ボックスに「_**\ repl_merge** 」と入力して、このアカウントのパスワードを入力し、[ **OK**]、[**次へ**] の順にクリックしてから、もう一度 [**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-115">On the Merge Agent Security page, click the ellipsis (**...**) button, enter \<_Machine_Name>_**\repl_merge** in the **Process account** box, supply the password for this account, click **OK**, click **Next**, and then click **Next** again.</span></span>  
  
9. <span data-ttu-id="9eed4-116">[サブスクリプションの初期化] ページで、**[次の場合に初期化]** ボックスの一覧から **[初回同期時]** を選択し、**[次へ]** をクリックし、**[次へ]** もう一度です。</span><span class="sxs-lookup"><span data-stu-id="9eed4-116">On the Initialize Subscriptions page, select **At first synchronization** from the **Initialize When** list, click **Next**, and then click **Next** again.</span></span>  
  
10. <span data-ttu-id="9eed4-117">[値の HOST_NAME] ページで、[ `adventure-works\pamela0` **HOST_NAME の値**] ボックスに値を入力し、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-117">On the HOST_NAME Values page, enter a value of `adventure-works\pamela0` in the **HOST_NAME Value** box, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="9eed4-118">もう一度 **[完了]** をクリックし、サブスクリプションが作成されたら **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-118">Click **Finish** again, and after the subscription is created, click **Close**.</span></span>  
  
### <a name="setting-database-permissions-at-the-subscriber"></a><span data-ttu-id="9eed4-119">サブスクライバー側のデータベース権限を設定するには</span><span class="sxs-lookup"><span data-stu-id="9eed4-119">Setting database permissions at the Subscriber</span></span>  
  
1.  <span data-ttu-id="9eed4-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、 **[データベース]**、 **[SalesOrdersReplica]**、 **[セキュリティ]** の順に展開して、 **[ユーザー]** を右クリックし、 **[新しいユーザー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9eed4-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Databases**, **SalesOrdersReplica**, and **Security**, right-click **Users**, and then select **New User**.</span></span>  
  
2.  <span data-ttu-id="9eed4-121">[**全般**] ページの [ \<_Machine_Name> _**ユーザー名**] ボックスに「 **\ repl_merge** 」と入力し、省略記号ボタン ([**..**.] \<_Machine_Name> ) を**Browse**_ クリックして、[参照]、[ **\ repl_merge**] の順にクリックし、[ **ok**] をクリックして [**名前の確認**] をクリックし、[ **ok**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-121">On the **General** page, enter \<_Machine_Name>_**\repl_merge** in the **User name** box, click the ellipsis (**...**) button, click **Browse**, select \<_Machine_Name>_**\repl_merge**, click **OK**, click **Check Names**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="9eed4-122">**[データベース ロールのメンバーシップ]** で **[db_owner]** を選択し、 **[OK]** をクリックしてユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9eed4-122">In **Database role membership**, select **db_owner**, and then click **OK** to create the user.</span></span>  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a><span data-ttu-id="9eed4-123">サブスクリプション用のフィルター選択データのスナップショットを作成するには</span><span class="sxs-lookup"><span data-stu-id="9eed4-123">To create the filtered data snapshot for the subscription</span></span>  
  
1.  <span data-ttu-id="9eed4-124">でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9eed4-124">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="9eed4-125">**[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksSalesOrdersMerge]** パブリケーションを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-125">In the **Local Publications** folder, right-click the **AdvWorksSalesOrdersMerge** publication, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="9eed4-126">**[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9eed4-126">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="9eed4-127">**[データ パーティション]** ページを選択して、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-127">Select the **Data Partitions** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="9eed4-128">[**データパーティションの追加**] ダイアログボックスで、 `adventure-works\pamela0` [ **HOST_NAME 値**] ボックスに「」と入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-128">In the **Add Data Partition** dialog box, type `adventure-works\pamela0` in the **HOST_NAME Value** box, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="9eed4-129">新しく追加したパーティションを選択して、 **[今すぐ選択したスナップショットを生成する]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9eed4-129">Select the newly added partition, click **Generate the selected snapshots now**, and then click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9eed4-130">次の手順</span><span class="sxs-lookup"><span data-stu-id="9eed4-130">Next Steps</span></span>  
 <span data-ttu-id="9eed4-131">ここでは、マージ パブリケーションへのサブスクリプションを作成し、新しいサブスクリプションのデータ パーティション用のフィルター選択スナップショットを生成して、サブスクリプション初期化時に使用できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="9eed4-131">You have successfully created a subscription to the merge publication and generated the filtered snapshot for the new subscription's data partition so that it will be available when the subscription is initialized.</span></span> <span data-ttu-id="9eed4-132">次は、サブスクリプション データベースのマージ エージェントに権限を付与します。さらに、マージ エージェントを実行して、同期の開始とサブスクリプションの初期化を行います。</span><span class="sxs-lookup"><span data-stu-id="9eed4-132">Next, you will grant rights to the Merge Agent on the subscription database and run the Merge Agent to start synchronization and initialize the subscription.</span></span> <span data-ttu-id="9eed4-133">「 [レッスン 3:マージ パブリケーションへのサブスクリプションの同期](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9eed4-133">See [Lesson 3: Synchronizing the Subscription to the Merge Publication](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eed4-134">参照</span><span class="sxs-lookup"><span data-stu-id="9eed4-134">See Also</span></span>  
 <span data-ttu-id="9eed4-135">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="9eed4-135">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="9eed4-136">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="9eed4-136">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="9eed4-137">パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット</span><span class="sxs-lookup"><span data-stu-id="9eed4-137">Snapshots for Merge Publications with Parameterized Filters</span></span>](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
