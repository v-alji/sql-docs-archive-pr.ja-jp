---
title: 'レッスン 1 : レプリケーション用の Windows アカウントの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: rothja
ms.author: jroth
ms.openlocfilehash: 29f1008338b3ba728066ed611108477586a4c899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632324"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a><span data-ttu-id="5d353-102">レッスン 1 : レプリケーション用の Windows アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="5d353-102">Lesson 1: Creating Windows Accounts for Replication</span></span>
  <span data-ttu-id="5d353-103">このレッスンでは、レプリケーション エージェントを実行するための Windows アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d353-103">In this lesson, you will create Windows accounts to run replication agents.</span></span> <span data-ttu-id="5d353-104">また、次のエージェントを実行するための別の Windows アカウントをローカル サーバー上に作成します。</span><span class="sxs-lookup"><span data-stu-id="5d353-104">You will create a separate Windows account on the local server for the following agents:</span></span>  
  
|<span data-ttu-id="5d353-105">エージェント</span><span class="sxs-lookup"><span data-stu-id="5d353-105">Agent</span></span>|<span data-ttu-id="5d353-106">場所</span><span class="sxs-lookup"><span data-stu-id="5d353-106">Location</span></span>|<span data-ttu-id="5d353-107">アカウント名</span><span class="sxs-lookup"><span data-stu-id="5d353-107">Account name</span></span>|  
|-----------|--------------|------------------|  
|<span data-ttu-id="5d353-108">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="5d353-108">Snapshot Agent</span></span>|<span data-ttu-id="5d353-109">Publisher</span><span class="sxs-lookup"><span data-stu-id="5d353-109">Publisher</span></span>|<span data-ttu-id="5d353-110">\<*machine_name*>\ repl_snapshot</span><span class="sxs-lookup"><span data-stu-id="5d353-110">\<*machine_name*>\repl_snapshot</span></span>|  
|<span data-ttu-id="5d353-111">ログ リーダー エージェント (Log Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="5d353-111">Log Reader Agent</span></span>|<span data-ttu-id="5d353-112">Publisher</span><span class="sxs-lookup"><span data-stu-id="5d353-112">Publisher</span></span>|<span data-ttu-id="5d353-113">\<*machine_name*>\ repl_logreader</span><span class="sxs-lookup"><span data-stu-id="5d353-113">\<*machine_name*>\repl_logreader</span></span>|  
|<span data-ttu-id="5d353-114">ディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="5d353-114">Distribution Agent</span></span>|<span data-ttu-id="5d353-115">パブリッシャーおよびサブスクライバー</span><span class="sxs-lookup"><span data-stu-id="5d353-115">Publisher and Subscriber</span></span>|<span data-ttu-id="5d353-116">\<*machine_name*>\ repl_distribution</span><span class="sxs-lookup"><span data-stu-id="5d353-116">\<*machine_name*>\repl_distribution</span></span>|  
|<span data-ttu-id="5d353-117">[マージ エージェント]</span><span class="sxs-lookup"><span data-stu-id="5d353-117">Merge Agent</span></span>|<span data-ttu-id="5d353-118">パブリッシャーおよびサブスクライバー</span><span class="sxs-lookup"><span data-stu-id="5d353-118">Publisher and Subscriber</span></span>|<span data-ttu-id="5d353-119">\<*machine_name*>\ repl_merge</span><span class="sxs-lookup"><span data-stu-id="5d353-119">\<*machine_name*>\repl_merge</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="5d353-120">このレプリケーション チュートリアルでは、パブリッシャーとディストリビューターで同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有します。</span><span class="sxs-lookup"><span data-stu-id="5d353-120">In the replication tutorials, the Publisher and Distributor share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5d353-121">パブリッシャーとサブスクライバーが同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有することもできますが、これは必須条件ではありません。</span><span class="sxs-lookup"><span data-stu-id="5d353-121">The Publisher and Subscriber may share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but it is not a requirement.</span></span> <span data-ttu-id="5d353-122">パブリッシャーとサブスクライバーが同じインスタンスを共有している場合、サブスクライバー側でアカウントの作成に使用される手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5d353-122">If the Publisher and Subscriber share the same instance, the steps that are used to create accounts at the Subscriber are not required.</span></span>  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a><span data-ttu-id="5d353-123">パブリッシャー側でレプリケーション エージェントを実行するためのローカル Windows アカウントを作成するには</span><span class="sxs-lookup"><span data-stu-id="5d353-123">To create local Windows accounts for replication agents at the Publisher</span></span>  
  
1.  <span data-ttu-id="5d353-124">パブリッシャーで、コントロールパネルの [**管理ツール**] から [**コンピューターの管理**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="5d353-124">At the Publisher, open **Computer Management** from **Administrative Tools** in Control Panel.</span></span>  
  
2.  <span data-ttu-id="5d353-125">**[システム ツール]** の **[ローカル ユーザーとグループ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="5d353-125">In **System Tools**, expand **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="5d353-126">[**ユーザー** ] を右クリックし、[**新しいユーザー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d353-126">Right-click **Users** and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="5d353-127">[ `repl_snapshot` **ユーザー名**] ボックスに「」と入力し、パスワードおよびその他の関連情報を入力して、[**作成**] をクリックして repl_snapshot アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d353-127">Enter `repl_snapshot` in the **User name** box, provide the password and other relevant information, and then click **Create** to create the repl_snapshot account.</span></span>  
  
5.  <span data-ttu-id="5d353-128">同様に、repl_logreader、repl_distribution、repl_merge の各アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d353-128">Repeat the previous step to create the repl_logreader, repl_distribution, and repl_merge accounts.</span></span>  
  
6.  <span data-ttu-id="5d353-129">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d353-129">Click **Close**.</span></span>  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a><span data-ttu-id="5d353-130">サブスクライバー側でレプリケーション エージェントを実行するためのローカル Windows アカウントを作成するには</span><span class="sxs-lookup"><span data-stu-id="5d353-130">To create local Windows accounts for replication agents at the Subscriber</span></span>  
  
1.  <span data-ttu-id="5d353-131">サブスクライバーで、コントロールパネルの [**管理ツール**] から [**コンピューターの管理**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="5d353-131">At the Subscriber, open **Computer Management** from **Administrative Tools** in Control Panel.</span></span>  
  
2.  <span data-ttu-id="5d353-132">**[システム ツール]** の **[ローカル ユーザーとグループ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="5d353-132">In **System Tools**, expand **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="5d353-133">[**ユーザー** ] を右クリックし、[**新しいユーザー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d353-133">Right-click **Users** and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="5d353-134">[ `repl_distribution` **ユーザー名**] ボックスに「」と入力し、パスワードおよびその他の関連情報を入力して、[**作成**] をクリックして repl_distribution アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d353-134">Enter `repl_distribution` in the **User name** box, provide the password and other relevant information, and then click **Create** to create the repl_distribution account.</span></span>  
  
5.  <span data-ttu-id="5d353-135">同様にして、repl_merge アカウントも作成します。</span><span class="sxs-lookup"><span data-stu-id="5d353-135">Repeat the previous step to create the repl_merge account.</span></span>  
  
6.  <span data-ttu-id="5d353-136">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d353-136">Click **Close**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5d353-137">次の手順</span><span class="sxs-lookup"><span data-stu-id="5d353-137">Next Steps</span></span>  
 <span data-ttu-id="5d353-138">ここでは、レプリケーション エージェントを実行するための Windows アカウントを作成しました。</span><span class="sxs-lookup"><span data-stu-id="5d353-138">You have successfully created Windows accounts for replication agents.</span></span> <span data-ttu-id="5d353-139">次はスナップショット フォルダーを設定します。</span><span class="sxs-lookup"><span data-stu-id="5d353-139">Next, you will configure the snapshot folder.</span></span> <span data-ttu-id="5d353-140">「 [レッスン 2: スナップショット フォルダーの準備](lesson-2-preparing-the-snapshot-folder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d353-140">See [Lesson 2: Preparing the Snapshot Folder](lesson-2-preparing-the-snapshot-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d353-141">参照</span><span class="sxs-lookup"><span data-stu-id="5d353-141">See Also</span></span>  
 [<span data-ttu-id="5d353-142">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="5d353-142">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
