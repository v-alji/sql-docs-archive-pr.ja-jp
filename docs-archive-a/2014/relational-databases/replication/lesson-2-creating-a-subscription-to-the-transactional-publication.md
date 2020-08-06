---
title: 'レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
author: rothja
ms.author: jroth
ms.openlocfilehash: dbf40fa259302dffdd6c0b8e8717b7c35b0cf92d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632323"
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a><span data-ttu-id="a7ded-102">レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成</span><span class="sxs-lookup"><span data-stu-id="a7ded-102">Lesson 2: Creating a Subscription to the Transactional Publication</span></span>
  <span data-ttu-id="a7ded-103">このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-103">In this lesson, you will create a subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a7ded-104">このレッスンを薦めるには、前のレッスンである「 [レッスン 1: トランザクション レプリケーションを使用したデータのパブリッシュ](lesson-1-publishing-data-using-transactional-replication.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7ded-104">This lesson requires that you have completed the previous lesson, [Lesson 1: Publishing Data Using Transactional Replication](lesson-1-publishing-data-using-transactional-replication.md).</span></span>  
  
### <a name="to-create-the-subscription"></a><span data-ttu-id="a7ded-105">サブスクリプションを作成するには</span><span class="sxs-lookup"><span data-stu-id="a7ded-105">To create the subscription</span></span>  
  
1.  <span data-ttu-id="a7ded-106">でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-106">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="a7ded-107">**[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksProductTrans]** パブリケーションを右クリックして、 **[新しいサブスクリプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-107">In the **Local Publications** folder, right-click the **AdvWorksProductTrans** publication, and then click **New Subscriptions**.</span></span>  
  
     <span data-ttu-id="a7ded-108">サブスクリプションの新規作成ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-108">The New Subscription Wizard launches.</span></span>  
  
3.  <span data-ttu-id="a7ded-109">[パブリケーション] ページで **[AdvWorksProductTrans]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-109">On the Publication page, select **AdvWorksProductTrans**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="a7ded-110">[ディストリビューション エージェントの場所] ページで、 **[ディストリビューターですべてのエージェントを実行する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-110">On the Distribution Agent Location page, select **Run all agents at the Distributor**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="a7ded-111">[サブスクライバー] ページにサブスクライバー インスタンスの名前が表示されない場合は、 **[サブスクライバーの追加]**、 **[SQL Server サブスクライバーの追加]** の順にクリックし、 **[サーバーの接続]** ダイアログ ボックスにサブスクライバー インスタンス名を入力して、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-111">On the Subscribers page, if the name of the Subscriber instance is not displayed, click **Add Subscriber**, click **Add SQL Server Subscriber**, enter the Subscriber instance name in the **Connect to Server** dialog box, and then click **Connect**.</span></span>  
  
6.  <span data-ttu-id="a7ded-112">[サブスクライバー] ページで、サブスクライバーサーバーのインスタンス名を選択し、 **\<New Database>** [**サブスクリプションデータベース**] で [] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-112">On the Subscribers page, select the instance name of the Subscriber server, and select **\<New Database>** under **Subscription Database**.</span></span>  
  
7.  <span data-ttu-id="a7ded-113">**[新しいデータベース]** ダイアログ ボックスで、 **[データベース名]** ボックスに「 **ProductReplica** 」と入力し、 **[OK]** をクリックして **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-113">On the **New Database** dialog box, enter **ProductReplica** in the **Database name** box, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="a7ded-114">[**ディストリビューションエージェントセキュリティ**] ダイアログボックスで、省略記号ボタン ([**..**.]) をクリックし、[ \<_Machine_Name> **プロセスアカウント**] ボックスに「_**\ repl_distribution** 」と入力します。このアカウントのパスワードを入力し、[ **OK**] をクリックして、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-114">In the **Distribution Agent Security** dialog box, click the ellipsis (**...**) button, enter \<_Machine_Name>_**\repl_distribution** in the **Process account** box, enter the password for this account, click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="a7ded-115">以降のページでは既定値をそのまま採用し、 **[完了]** をクリックしてウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-115">Click **Finish** to accept the default values on the remaining pages and complete the wizard.</span></span>  
  
### <a name="setting-database-permissions-at-the-subscriber"></a><span data-ttu-id="a7ded-116">サブスクライバー側のデータベース権限を設定するには</span><span class="sxs-lookup"><span data-stu-id="a7ded-116">Setting database permissions at the Subscriber</span></span>  
  
1.  <span data-ttu-id="a7ded-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続します。次に、 **[データベース]**、 **[ProductReplica]**、 **[セキュリティ]** の順に展開し、 **[ユーザー]** を右クリックして、 **[新しいユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-117">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Databases**, **ProductReplica**, and **Security**, right-click **Users**, and then select **New User**.</span></span>  
  
2.  <span data-ttu-id="a7ded-118">**[全般]** ページの **[ユーザーの種類]** ボックスの一覧の **[Windows ユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-118">On the **General** page, in the **User type** list, select **Windows user**.</span></span>  
  
3.  <span data-ttu-id="a7ded-119">[**ユーザー名**] ボックスを選択し、省略記号ボタン ([...]) をクリックします。 [**選択するオブジェクト名を入力**してください] ボックスに <Machine_Name>**\ repl_distribution**] を入力し、[**名前の確認**] をクリックして、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-119">Select the **User name** box and click the ellipsis (...) button, in the **Enter the object name to select** box type <Machine_Name>**\repl_distribution**, click **Check Names**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="a7ded-120">**[メンバーシップ]** ページの **[データベース ロールのメンバーシップ]** 領域で、 **[db_owner]** を選択し、 **[OK]** をクリックしてユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-120">On the **Membership** page, in **Database role membership** area, select **db_owner**, and then click **OK** to create the user.</span></span>  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a><span data-ttu-id="a7ded-121">サブスクリプションの同期状態を表示するには</span><span class="sxs-lookup"><span data-stu-id="a7ded-121">To view the synchronization status of the subscription</span></span>  
  
1.  <span data-ttu-id="a7ded-122">でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-122">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="a7ded-123">**[ローカル パブリケーション]** フォルダーで、 **AdvWorksProductTrans** パブリケーションを展開し、 **ProductReplica** データベースのサブスクリプションを右クリックして、 **[同期の状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7ded-123">In the **Local Publications** folder, expand the **AdvWorksProductTrans** publication, right-click the subscription in the **ProductReplica** database, and then click **View Synchronization Status**.</span></span>  
  
     <span data-ttu-id="a7ded-124">サブスクリプションの現在の同期状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7ded-124">The current synchronization status of the subscription is displayed.</span></span>  
  
3.  <span data-ttu-id="a7ded-125">**[AdvWorksProductTrans]** の下にサブスクリプションが表示されない場合は、F5 キーを押して一覧を更新します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-125">If the subscription is not visible under **AdvWorksProductTrans**, press F5 to refresh the list.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a7ded-126">次の手順</span><span class="sxs-lookup"><span data-stu-id="a7ded-126">Next Steps</span></span>  
 <span data-ttu-id="a7ded-127">ここでは、トランザクション パブリケーションへのサブスクリプションを作成しました。</span><span class="sxs-lookup"><span data-stu-id="a7ded-127">You have successfully created a subscription to the transactional publication.</span></span> <span data-ttu-id="a7ded-128">このサブスクリプションのディストリビューション エージェントは常時動作しているので、サブスクリプションの作成時に初期化も行われます。</span><span class="sxs-lookup"><span data-stu-id="a7ded-128">Because the Distribution Agent for this subscription runs continuously, the subscription is initialized when it is created.</span></span> <span data-ttu-id="a7ded-129">次は、トレーサー トークンを使って、変更内容がサブスクライバーにレプリケートされているかどうかを確認し、待機時間を決定します。</span><span class="sxs-lookup"><span data-stu-id="a7ded-129">Next, you will use tracer tokens to verify that changes are being replicated to the Subscriber and to determine latency.</span></span> <span data-ttu-id="a7ded-130">「 [レッスン 3: サブスクリプションの検証と待機時間の計測](lesson-3-validating-the-subscription-and-measuring-latency.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7ded-130">See [Lesson 3: Validating the Subscription and Measuring Latency](lesson-3-validating-the-subscription-and-measuring-latency.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ded-131">参照</span><span class="sxs-lookup"><span data-stu-id="a7ded-131">See Also</span></span>  
 <span data-ttu-id="a7ded-132">[Initialize a Subscription with a Snapshot (スナップショットを使用したサブスクリプションの初期化)](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="a7ded-132">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="a7ded-133">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="a7ded-133">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="a7ded-134">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="a7ded-134">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
