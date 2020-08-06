---
title: トランザクションパブリケーションに対する更新可能なサブスクリプションの作成 (Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e784216116bdb9ab308dff5fa998740b0fa459b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741789"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a><span data-ttu-id="cecc9-102">トランザクション パブリケーションに対して更新可能なサブスクリプションを作成する (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cecc9-102">Create an Updatable Subscription to a Transactional Publication (Management Studio)</span></span>

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
<span data-ttu-id="cecc9-103">トランザクション レプリケーションは、即時更新サブスクリプションまたはキュー更新サブスクリプションを使用して、サブスクライバーでの変更がパブリッシャーに反映されるようにします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-103">Transactional replication enables changes made at a Subscriber to be propagated back to the Publisher using either immediate or queued updating subscriptions.</span></span> <span data-ttu-id="cecc9-104">レプリケーション ストアド プロシージャを使用して、更新サブスクリプションをプログラムで作成できます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-104">You can create an updating subscription programmatically using replication stored procedures.</span></span>

<span data-ttu-id="cecc9-105">**サブスクリプションの新規作成ウィザード**の **[更新可能なサブスクリプション]** ページで、更新可能なサブスクリプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-105">Configure updatable subscriptions on the **Updatable Subscriptions** page of the **New Subscription Wizard**.</span></span> <span data-ttu-id="cecc9-106">このページは、更新可能なサブスクリプションに対してトランザクション パブリケーションを有効にした場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-106">This page is only available if you have enabled a transactional publication for updatable subscriptions.</span></span> <span data-ttu-id="cecc9-107">更新可能なサブスクリプションを有効にする方法については、「[トランザクション パブリケーションの更新サブスクリプションを有効にする方法](enable-updating-subscriptions-for-transactional-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-107">For more information about enabling updatable subscriptions, see [Enable Updating Subscriptions for Transactional Publications](enable-updating-subscriptions-for-transactional-publications.md).</span></span>   
  
## <a name="configure-an-updatable-subscription-from-the-publisher"></a><span data-ttu-id="cecc9-108">パブリッシャーから更新可能なサブスクリプションを構成する</span><span class="sxs-lookup"><span data-stu-id="cecc9-108">Configure an updatable subscription from the Publisher</span></span>  

1. <span data-ttu-id="cecc9-109">Microsoft SQL Server Management Studio でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-109">Connect to the Publisher in Microsoft SQL Server Management Studio, and then expand the server node.</span></span>
2. <span data-ttu-id="cecc9-110">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-110">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>
3. <span data-ttu-id="cecc9-111">更新サブスクリプションを有効にしたトランザクション パブリケーションを右クリックし、 **[新しいサブスクリプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-111">Right-click a transactional publication enabled for updating subscriptions, and then click **New Subscriptions**.</span></span>
4. <span data-ttu-id="cecc9-112">ウィザード内のページに従って、ディストリビューション エージェントが実行される場所など、サブスクリプションに対するオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-112">Follow pages in the wizard to specify options for the subscription, such as where the Distribution Agent should run.</span></span>
5. <span data-ttu-id="cecc9-113">**サブスクリプションの新規作成ウィザード**の **[更新可能なサブスクリプション]** ページで、 **[レプリケート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-113">On the **Updatable Subscriptions** page of the **New Subscription Wizard**, ensure **Replicate** is selected.</span></span>
6. <span data-ttu-id="cecc9-114">**[パブリッシャーでのコミット]** ボックスの一覧からオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-114">Select an option from the **Commit at Publisher** drop-down list:</span></span>

    *  <span data-ttu-id="cecc9-115">即時更新サブスクリプションを使用するには、 **[変更を同時にコミットする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-115">To use immediate updating subscriptions, select **Simultaneously commit changes**.</span></span> <span data-ttu-id="cecc9-116">このオプションを選択し、パブリケーションがキュー更新サブスクリプションを許可する場合 (パブリケーションの新規作成ウィザードを使用して作成されたパブリケーションの既定値)、サブスクリプション プロパティ **update_mode** は **failover** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-116">If you select this option, and the publication allows queued updating subscriptions (the default for publications created with the New Publication Wizard), the subscription property **update_mode** is set to **failover**.</span></span> <span data-ttu-id="cecc9-117">このモードでは、必要に応じて、後からキュー更新に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-117">This mode allows you to switch to queued updating later if necessary.</span></span>
    *  <span data-ttu-id="cecc9-118">キュー更新サブスクリプションを使用するには、 **[変更をキューに登録し、可能な場合はコミット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-118">To use queued updating subscriptions, select **Queue changes and commit when possible**.</span></span> <span data-ttu-id="cecc9-119">このオプションを選択し、パブリケーションが即時更新サブスクリプションを許可していて (パブリケーションの新規作成ウィザードを使用して作成されたパブリケーションの既定値)、サブスクライバーが SQL Server 2005 以降を実行している場合、サブスクリプション プロパティ **update_mode** は queued failover に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-119">If you select this option, and the publication allows immediate updating subscriptions (the default for publications created with the New Publication Wizard), and the Subscriber is running SQL Server 2005 or a later version, the subscription property **update_mode** is set to queued failover.</span></span> <span data-ttu-id="cecc9-120">このモードでは、必要に応じて、後から即時更新に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-120">This mode allows you to switch to immediate updating later if necessary.</span></span>

    <span data-ttu-id="cecc9-121">更新モードの切り替えの詳細については、「[Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)」(更新可能なトランザクション サブスクリプションの更新モードを切り替える) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-121">For information about switching update modes, see [Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>

7. <span data-ttu-id="cecc9-122">即時更新を使用するサブスクリプション、または **update_mode** を **queued failover** に設定したサブスクリプションに対して **[更新可能なサブスクリプション用のログイン]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-122">The **Login for Updatable Subscriptions** page is displayed for subscriptions that use immediate updating or have **update_mode** set to **queued failover**.</span></span> <span data-ttu-id="cecc9-123">**[更新可能なサブスクリプション用のログイン]** ページで、即時更新サブスクリプション用にパブリッシャーへの接続を作成するリンク サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-123">On the **Login for Updatable Subscriptions** page, specify a linked server over which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="cecc9-124">接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-124">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="cecc9-125">以下のオプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-125">Select one of the following options:</span></span>

    * <span data-ttu-id="cecc9-126">**[SQL Server 認証を使用して接続するリンク サーバーを作成する]** 。</span><span class="sxs-lookup"><span data-stu-id="cecc9-126">**Create a linked server that connects using SQL Server Authentication.**</span></span> <span data-ttu-id="cecc9-127">サブスクライバーとパブリッシャーの間でリモート サーバーまたはリンク サーバーを定義していない場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-127">Select this option if you have not defined a remote server or linked server between the Subscriber and the Publisher.</span></span> <span data-ttu-id="cecc9-128">レプリケーションによってリンク サーバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-128">Replication creates a linked server for you.</span></span> <span data-ttu-id="cecc9-129">指定するアカウントは、パブリッシャーに既に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-129">The account you specify must already exist at the Publisher.</span></span>
    * <span data-ttu-id="cecc9-130">**[定義済みのリンク サーバーまたはリモート サーバーを使用する]**</span><span class="sxs-lookup"><span data-stu-id="cecc9-130">**Use a linked server or remote server that you have already defined.**</span></span> <span data-ttu-id="cecc9-131">[sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)、[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)、SQL Server Management Studio、または他の方法を使用してサブスクライバ―とパブリッシャーの間にリモート サーバーまたはリンクされたサーバーを定義した場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-131">Select this option if you have defined a remote server or linked server between the Subscriber and the Publisher using [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio, or another method.</span></span>

    <span data-ttu-id="cecc9-132">リンクされたサーバー アカウントに必要な権限に関する詳細については、「[ここにサブスクリプションを入力](../security/secure-the-subscriber.md)」の「**Queued Updating Subscriptions**」(キューに入れられた更新サブスクリプション) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-132">For information about the permissions required by the linked server account, see the **Queued Updating Subscriptions** of [enter link description here](../security/secure-the-subscriber.md).</span></span>

8. <span data-ttu-id="cecc9-133">ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-133">Complete the wizard.</span></span>

## <a name="configure-an-updatable-subscription-from-the-subscriber"></a><span data-ttu-id="cecc9-134">サブスクライバーから更新可能なサブスクリプションを構成する</span><span class="sxs-lookup"><span data-stu-id="cecc9-134">Configure an updatable subscription from the Subscriber</span></span>


1. <span data-ttu-id="cecc9-135">SQL Server Management Studio でサブスクライバ―に接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-135">Connect to the Subscriber in SQL Server Management Studio, and then expand the server node.</span></span>
2. <span data-ttu-id="cecc9-136">**[レプリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-136">Expand the **Replication** folder.</span></span>
3. <span data-ttu-id="cecc9-137">**[ローカル サブスクリプション]** フォルダーを右クリックし、 **[新しいサブスクリプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-137">Right-click the **Local Subscriptions** folder, and then click **New Subscriptions**.</span></span>
4. <span data-ttu-id="cecc9-138">**サブスクリプションの新規作成ウィザード**の **[パブリケーション]** ページで、 **[パブリッシャー]** ボックスの一覧から **[<SQL Server パブリッシャーの検索>]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-138">On the **Publication** page of the **New Subscription Wizard**, select **Find SQL Server Publisher** from the **Publisher** drop-down list.</span></span>
5. <span data-ttu-id="cecc9-139">**[サーバーへの接続]** ダイアログ ボックスでパブリッシャーに接続します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-139">Connect to the Publisher in the **Connect to Server** dialog box.</span></span>
6. <span data-ttu-id="cecc9-140">**[パブリケーション]** ページで、更新サブスクリプションを有効にしたトランザクション パブリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-140">Select a transactional publication enabled for updating subscriptions on the **Publication** page.</span></span>
7. <span data-ttu-id="cecc9-141">ウィザード内のページに従って、ディストリビューション エージェントが実行される場所など、サブスクリプションに対するオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-141">Follow pages in the wizard to specify options for the subscription, such as where the Distribution Agent should run.</span></span>
8. <span data-ttu-id="cecc9-142">サブスクリプションの新規作成ウィザードの **[更新可能なサブスクリプション]** ページで、 **[レプリケート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-142">On the **Updatable Subscriptions** page of the New Subscription Wizard, ensure **Replicate** is selected.</span></span>
9. <span data-ttu-id="cecc9-143">**[パブリッシャーでのコミット]** ボックスの一覧からオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-143">Select an option from the **Commit at Publisher** drop-down list:</span></span>

    * <span data-ttu-id="cecc9-144">即時更新サブスクリプションを使用するには、 **[変更を同時にコミットする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-144">To use immediate updating subscriptions, select **Simultaneously commit changes**.</span></span> <span data-ttu-id="cecc9-145">このオプションを選択し、パブリケーションがキュー更新サブスクリプションを許可する場合 (パブリケーションの新規作成ウィザードを使用して作成されたパブリケーションの既定値)、サブスクリプション プロパティ **update_mode** は **failover** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-145">If you select this option, and the publication allows queued updating subscriptions (the default for publications created with the New Publication Wizard), the subscription property **update_mode** is set to **failover**.</span></span> <span data-ttu-id="cecc9-146">このモードでは、必要に応じて、後からキュー更新に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-146">This mode allows you to switch to queued updating later if necessary.</span></span>
    * <span data-ttu-id="cecc9-147">キュー更新サブスクリプションを使用するには、 **[変更をキューに登録し、可能な場合はコミット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-147">To use queued updating subscriptions, select **Queue changes and commit when possible**.</span></span> <span data-ttu-id="cecc9-148">このオプションを選択し、パブリケーションが即時更新サブスクリプションを許可していて (パブリケーションの新規作成ウィザードを使用して作成されたパブリケーションの既定値)、サブスクライバーが SQL Server 2005 以降を実行している場合、サブスクリプション プロパティ **update_mode** は queued **failover** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-148">If you select this option, and the publication allows immediate updating subscriptions (the default for publications created with the New Publication Wizard), and the Subscriber is running SQL Server 2005 or a later version, the subscription property **update_mode** is set to queued **failover**.</span></span> <span data-ttu-id="cecc9-149">このモードでは、必要に応じて、後から即時更新に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-149">This mode allows you to switch to immediate updating later if necessary.</span></span>

    <span data-ttu-id="cecc9-150">更新モードの切り替えの詳細については、「[Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)」(更新可能なトランザクション サブスクリプションの更新モードを切り替える) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-150">For information about switching update modes, see [Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>

10. <span data-ttu-id="cecc9-151">即時更新を使用するサブスクリプション、または **update_mode** を queued **failover** に設定したサブスクリプションに対して **[更新可能なサブスクリプション用のログイン]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-151">The **Login for Updatable Subscriptions** page is displayed for subscriptions that use immediate updating or have **update_mode** set to queued **failover**.</span></span> <span data-ttu-id="cecc9-152">**[更新可能なサブスクリプション用のログイン]** ページで、即時更新サブスクリプション用にパブリッシャーへの接続を作成するリンク サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-152">On the **Login for Updatable Subscriptions** page, specify a linked server over which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="cecc9-153">接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-153">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="cecc9-154">以下のオプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-154">Select one of the following options:</span></span>

    * <span data-ttu-id="cecc9-155">**[SQL Server 認証を使用して接続するリンク サーバーを作成する]** 。</span><span class="sxs-lookup"><span data-stu-id="cecc9-155">**Create a linked server that connects using SQL Server Authentication.**</span></span> <span data-ttu-id="cecc9-156">サブスクライバーとパブリッシャーの間でリモート サーバーまたはリンク サーバーを定義していない場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-156">Select this option if you have not defined a remote server or linked server between the Subscriber and the Publisher.</span></span> <span data-ttu-id="cecc9-157">レプリケーションによってリンク サーバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-157">Replication creates a linked server for you.</span></span> <span data-ttu-id="cecc9-158">指定するアカウントは、パブリッシャーに既に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-158">The account you specify must already exist at the Publisher.</span></span>
    * <span data-ttu-id="cecc9-159">**[定義済みのリンク サーバーまたはリモート サーバーを使用する]**</span><span class="sxs-lookup"><span data-stu-id="cecc9-159">**Use a linked server or remote server that you have already defined.**</span></span> <span data-ttu-id="cecc9-160">[sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)、[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)、SQL Server Management Studio、または他の方法を使用してサブスクライバ―とパブリッシャーの間にリモート サーバーまたはリンクされたサーバーを定義した場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-160">Select this option if you have defined a remote server or linked server between the Subscriber and the Publisher using [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio, or another method.</span></span>

    <span data-ttu-id="cecc9-161">リンクされたサーバー アカウントに必要な権限に関する詳細については、「[ここにサブスクリプションを入力](../security/secure-the-subscriber.md)」の「**Queued Updating Subscriptions**」(キューに入れられた更新サブスクリプション) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-161">For information about the permissions required by the linked server account, see the **Queued Updating Subscriptions** of [enter link description here](../security/secure-the-subscriber.md).</span></span>

11. <span data-ttu-id="cecc9-162">ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-162">Complete the wizard.</span></span>

## <a name="create-an-immediate-updating-pull-subscription"></a><span data-ttu-id="cecc9-163">即時更新プル サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="cecc9-163">Create an immediate updating pull subscription</span></span>

1. <span data-ttu-id="cecc9-164">パブリッシャーで、 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)を実行することにより、パブリケーションが即時更新サブスクリプションをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-164">At the Publisher, verify that the publication supports immediate updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="cecc9-165">結果セットの `allow_sync_tran` の値が `1`である場合、パブリケーションは即時更新サブスクリプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-165">If the value of `allow_sync_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="cecc9-166">結果セットの `allow_sync_tran` の値が `0`である場合は、即時更新サブスクリプションを有効にしてパブリケーションを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-166">If the value of `allow_sync_tran` in the result set is `0`, the publication must be recreated with immediate updating subscriptions enabled.</span></span>

2. <span data-ttu-id="cecc9-167">パブリッシャーで、 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)を実行することにより、パブリケーションがプル サブスクリプションをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-167">At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="cecc9-168">結果セットの `allow_pull` の値が `1`である場合、パブリケーションはプル サブスクリプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-168">If the value of `allow_pull` in the result set is `1`, the publication supports pull subscriptions.</span></span>
    * <span data-ttu-id="cecc9-169">`allow_pull` の値が `0`である場合、 [には](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)、 `allow_pull` には `@property` を指定して `true` sp_changepublication `@value`を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-169">If the value of `allow_pull` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_pull` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="cecc9-170">サブスクライバーで、 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-170">At the Subscriber, execute [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql).</span></span> <span data-ttu-id="cecc9-171">`@publisher` と `@publication`を指定し、 `@update_mode`に次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-171">Specify `@publisher` and `@publication`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="cecc9-172">`sync tran` - サブスクリプションの即時更新を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-172">`sync tran` - enables the subscription for immediate updating.</span></span>
    * <span data-ttu-id="cecc9-173">`failover` キュー更新をフェールオーバー オプションとするサブスクリプションの即時更新を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-173">`failover` - enables the subscription for immediate updating with queued updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="cecc9-174">`failover` では、パブリケーションでもキュー更新サブスクリプションが有効になっていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="cecc9-174">`failover` requires that the publication also be enabled for queued updating subscriptions.</span></span> 
 
4. <span data-ttu-id="cecc9-175">サブスクライバーで、 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-175">At the Subscriber, execute [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="cecc9-176">次の指定を行います。</span><span class="sxs-lookup"><span data-stu-id="cecc9-176">Specify the following:</span></span>

    * <span data-ttu-id="cecc9-177">`@publisher`、 `@publisher_db`、および `@publication` パラメーター。</span><span class="sxs-lookup"><span data-stu-id="cecc9-177">The `@publisher`, `@publisher_db`, and `@publication` parameters.</span></span> 
    * <span data-ttu-id="cecc9-178">`@job_login` および `@job_password`に、サブスクライバーでディストリビューション エージェントを実行するときに使用する Microsoft Windows 資格情報。</span><span class="sxs-lookup"><span data-stu-id="cecc9-178">The Microsoft Windows credentials under which the Distribution Agent at the Subscriber runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="cecc9-179">Windows 統合認証を使用して作成された接続では、常に、 `@job_login` および `@job_password`で指定された Windows 資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-179">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="cecc9-180">ディストリビューション エージェントは、常に Windows 統合認証を使用してサブスクライバーへのローカル接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-180">The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication.</span></span> <span data-ttu-id="cecc9-181">既定では、エージェントは Windows 統合認証を使用してディストリビューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-181">By default, the agent connects to the Distributor using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="cecc9-182">(省略可能) ディストリビューターに接続するときに SQL Server 認証を使用する必要がある場合、 `0` には `@distributor_security_mode` 、 `@distributor_login` と `@distributor_password`には Microsoft SQL Server ログイン情報の値。</span><span class="sxs-lookup"><span data-stu-id="cecc9-182">(Optional) A value of `0` for `@distributor_security_mode` and the Microsoft SQL Server login information for `@distributor_login` and `@distributor_password`, if you need to use SQL Server Authentication when connecting to the Distributor.</span></span> 
    * <span data-ttu-id="cecc9-183">このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。</span><span class="sxs-lookup"><span data-stu-id="cecc9-183">A schedule for the Distribution Agent job for this subscription.</span></span> 

5. <span data-ttu-id="cecc9-184">サブスクライバー側のサブスクリプション データベースに対して、 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-184">At the Subscriber on the subscription database, execute [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="cecc9-185">`@publisher`、 `@publication`、 `@publisher_db`のパブリケーション データベース名、および `@security_mode`の次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-185">Specify `@publisher`, `@publication`, the name of the publication database for `@publisher_db`, and one of the following values for `@security_mode`:</span></span> 

    * <span data-ttu-id="cecc9-186">`0` - パブリッシャーで更新を作成する場合に SQL Server 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-186">`0` - Use SQL Server Authentication when making updates at the Publisher.</span></span> <span data-ttu-id="cecc9-187">このオプションの場合、パブリッシャーで、 `@login` および `@password`に有効なログインを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-187">This option requires you to specify a valid login at the Publisher for `@login` and `@password`.</span></span>
    * <span data-ttu-id="cecc9-188">`1` - パブリッシャーへの接続時にサブスクライバーで変更するユーザーのセキュリティ コンテキストを使用します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-188">`1` - Use the security context of the user making changes at the Subscriber when connecting to the Publisher.</span></span> <span data-ttu-id="cecc9-189">このセキュリティ モードに関連する制限の詳細については、 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-189">See [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) for restrictions related to this security mode.</span></span>
    * <span data-ttu-id="cecc9-190">`2` - [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)を使って作成された、既存のユーザー定義リンク サーバー ログインを使用します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-190">`2` - Use an existing, user-defined linked server login created using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>

6. <span data-ttu-id="cecc9-191">パブリッシャーで、 [、](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 、 `@publication`、 `@subscriber`のプル値、 `@destination_db`の手順 3 で指定したものと同じ値を指定し、 `@subscription_type`sp_addsubscription `@update_mode`を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-191">At the publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) specifying `@publication`, `@subscriber`, `@destination_db`, a value of pull for `@subscription_type`, and the same value specified in step 3 for `@update_mode`.</span></span>

<span data-ttu-id="cecc9-192">これにより、パブリッシャーでプル サブスクリプションが登録されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-192">This registers the pull subscription at the Publisher.</span></span> 


## <a name="create-an-immediate-updating-push-subscription"></a><span data-ttu-id="cecc9-193">即時更新プッシュ サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="cecc9-193">Create an immediate updating push subscription</span></span> 

1. <span data-ttu-id="cecc9-194">パブリッシャーで、 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)を実行することにより、パブリケーションが即時更新サブスクリプションをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-194">At the Publisher, verify that the publication supports immediate updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="cecc9-195">結果セットの `allow_sync_tran` の値が `1`である場合、パブリケーションは即時更新サブスクリプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-195">If the value of `allow_sync_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="cecc9-196">結果セットの `allow_sync_tran` の値が `0`である場合は、即時更新サブスクリプションを有効にしてパブリケーションを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-196">If the value of `allow_sync_tran` in the result set is `0`, the publication must be recreated with immediate updating subscriptions enabled.</span></span>

2. <span data-ttu-id="cecc9-197">パブリッシャーで、 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)を実行することにより、パブリケーションがプッシュ サブスクリプションをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-197">At the Publisher, verify that the publication supports push subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="cecc9-198">結果セットの `allow_push` の値が `1`である場合、パブリケーションはプッシュ サブスクリプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-198">If the value of `allow_push` in the result set is `1`, the publication supports push subscriptions.</span></span>
    * <span data-ttu-id="cecc9-199">`allow_push` の値が `0`である場合、 [には](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)、 `allow_push` には `@property` を指定して `true` sp_changepublication `@value`を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-199">If the value of `allow_push` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_push` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="cecc9-200">パブリッシャーで、 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-200">At the Publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="cecc9-201">`@publication`、 `@subscriber`、 `@destination_db`を指定し、 `@update_mode`に次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-201">Specify `@publication`, `@subscriber`, `@destination_db`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="cecc9-202">`sync tran` - 即時更新のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-202">`sync tran` - enables support for immediate updating.</span></span>
    * <span data-ttu-id="cecc9-203">`failover` - キュー更新をフェールオーバー オプションとする即時更新のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-203">`failover` - enables support for immediate updating with queued updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="cecc9-204">`failover` では、パブリケーションでもキュー更新サブスクリプションが有効になっていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="cecc9-204">`failover` requires that the publication also be enabled for queued updating subscriptions.</span></span> 
 
4. <span data-ttu-id="cecc9-205">パブリッシャーで、 [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-205">At the Publisher, execute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="cecc9-206">次のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-206">Specify the following parameters:</span></span>

    * <span data-ttu-id="cecc9-207">`@subscriber`、 `@subscriber_db`、および `@publication`。</span><span class="sxs-lookup"><span data-stu-id="cecc9-207">`@subscriber`, `@subscriber_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="cecc9-208">`@job_login` および `@job_password`のディストリビューターでディストリビューション エージェントを実行する際に使用する Windows 資格情報。</span><span class="sxs-lookup"><span data-stu-id="cecc9-208">The Windows credentials under which the Distribution Agent at the Distributor runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="cecc9-209">Windows 統合認証を使用して作成された接続では、常に、 `@job_login` および `@job_password`で指定された Windows 資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-209">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="cecc9-210">ディストリビューション エージェントは、常に Windows 統合認証を使用してディストリビューターにローカル接続します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-210">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="cecc9-211">既定では、エージェントは Windows 統合認証を使用してサブスクライバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-211">By default, the agent will connect to the Subscriber using Windows Integrated Authentication.</span></span> 

    * <span data-ttu-id="cecc9-212">(省略可能) サブスクライバーに接続するときに SQL Server 認証を使用する必要がある場合、 `0` には `@subscriber_security_mode` 、 `@subscriber_login` と `@subscriber_password`には SQL Server ログイン情報の値。</span><span class="sxs-lookup"><span data-stu-id="cecc9-212">(Optional) A value of `0` for `@subscriber_security_mode` and the SQL Server login information for `@subscriber_login` and `@subscriber_password`, if you need to use SQL Server Authentication when connecting to the Subscriber.</span></span> 
    * <span data-ttu-id="cecc9-213">このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。</span><span class="sxs-lookup"><span data-stu-id="cecc9-213">A schedule for the Distribution Agent job for this subscription.</span></span>

5. <span data-ttu-id="cecc9-214">サブスクライバー側のサブスクリプション データベースに対して、 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-214">At the Subscriber on the subscription database, execute [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="cecc9-215">`@publisher`、 `@publication`、 `@publisher_db`のパブリケーション データベース名、および `@security_mode`の次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-215">Specify `@publisher`, `@publication`, the name of the publication database for `@publisher_db`, and one of the following values for `@security_mode`:</span></span> 

     * <span data-ttu-id="cecc9-216">`0` - パブリッシャーで更新を作成する場合に SQL Server 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-216">`0` - Use SQL Server Authentication when making updates at the Publisher.</span></span> <span data-ttu-id="cecc9-217">このオプションの場合、パブリッシャーで、 `@login` および `@password`に有効なログインを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-217">This option requires you to specify a valid login at the Publisher for `@login` and `@password`.</span></span>
     * <span data-ttu-id="cecc9-218">`1` - パブリッシャーへの接続時にサブスクライバーで変更するユーザーのセキュリティ コンテキストを使用します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-218">`1` - Use the security context of the user making changes at the Subscriber when connecting to the Publisher.</span></span> <span data-ttu-id="cecc9-219">このセキュリティ モードに関連する制限の詳細については、 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-219">See [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) for restrictions related to this security mode.</span></span>
     * <span data-ttu-id="cecc9-220">`2` - [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)を使って作成された、既存のユーザー定義リンク サーバー ログインを使用します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-220">`2` - Use an existing, user-defined linked server login created using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>


## <a name="create-a-queued-updating-pull-subscription"></a><span data-ttu-id="cecc9-221">キュー更新プル サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="cecc9-221">Create a queued updating pull subscription</span></span> ##

1. <span data-ttu-id="cecc9-222">パブリッシャーで、 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)を実行することにより、パブリケーションがキュー更新サブスクリプションをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-222">At the Publisher, verify that the publication supports queued updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="cecc9-223">結果セットの `allow_queued_tran` の値が `1`である場合、パブリケーションは即時更新サブスクリプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-223">If the value of `allow_queued_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="cecc9-224">結果セットの `allow_queued_tran` の値が `0`である場合は、キュー更新サブスクリプションを有効にしてパブリケーションを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-224">If the value of `allow_queued_tran` in the result set is `0`, the publication must be recreated with queued updating subscriptions enabled.</span></span>

2. <span data-ttu-id="cecc9-225">パブリッシャーで、 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)を実行することにより、パブリケーションがプル サブスクリプションをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-225">At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="cecc9-226">結果セットの `allow_pull` の値が `1`である場合、パブリケーションはプル サブスクリプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-226">If the value of `allow_pull` in the result set is `1`, the publication supports pull subscriptions.</span></span>
    * <span data-ttu-id="cecc9-227">`allow_pull` の値が `0`である場合、 [には](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)、 `allow_pull` には `@property` を指定して `true` sp_changepublication `@value`を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-227">If the value of `allow_pull` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_pull` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="cecc9-228">サブスクライバーで、 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-228">At the Subscriber, execute [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql).</span></span> <span data-ttu-id="cecc9-229">`@publisher` と `@publication`を指定し、 `@update_mode`に次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-229">Specify `@publisher` and `@publication`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="cecc9-230">`queued tran` - サブスクリプションのキュー更新を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-230">`queued tran` - enables the subscription for queued updating.</span></span>
    * <span data-ttu-id="cecc9-231">`queued failover` - 即時更新をフェールオーバー オプションとするキュー更新のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-231">`queued failover` - enables support for queued updating with immediate updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="cecc9-232">`queued failover` では、パブリケーションでも即時更新サブスクリプションが有効になっていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="cecc9-232">`queued failover` requires that the publication also be enabled for immediate updating subscriptions.</span></span> <span data-ttu-id="cecc9-233">即時更新へのフェールオーバーを行うために、 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) を使って、サブスクライバーでの変更をパブリッシャーにレプリケートするときに使用する資格情報を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-233">To fail over to immediate updating, you must use [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) to define the credentials under which changes at the Subscriber are replicated to the Publisher.</span></span>
 
4. <span data-ttu-id="cecc9-234">サブスクライバーで、 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-234">At the Subscriber, execute [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="cecc9-235">次のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-235">Specify the following parameters:</span></span>

    * <span data-ttu-id="cecc9-236">@publisher、 `@publisher_db`、および `@publication`。</span><span class="sxs-lookup"><span data-stu-id="cecc9-236">@publisher, `@publisher_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="cecc9-237">`@job_login` および `@job_password`に、サブスクライバーでディストリビューション エージェントを実行するときに使用する Windows 資格情報。</span><span class="sxs-lookup"><span data-stu-id="cecc9-237">The Windows credentials under which the Distribution Agent at the Subscriber runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="cecc9-238">Windows 統合認証を使用して作成された接続では、常に、 `@job_login` および `@job_password`で指定された Windows 資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-238">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="cecc9-239">ディストリビューション エージェントは、常に Windows 統合認証を使用してサブスクライバーへのローカル接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-239">The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication.</span></span> <span data-ttu-id="cecc9-240">既定では、エージェントは Windows 統合認証を使用してディストリビューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-240">By default, the agent connects to the Distributor using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="cecc9-241">(省略可能) ディストリビューターに接続するときに SQL Server 認証を使用する必要がある場合、 `0` には `@distributor_security_mode` 、 `@distributor_login` と `@distributor_password`には SQL Server ログイン情報の値。</span><span class="sxs-lookup"><span data-stu-id="cecc9-241">(Optional) A value of `0` for `@distributor_security_mode` and the SQL Server login information for `@distributor_login` and `@distributor_password`, if you need to use SQL Server Authentication when connecting to the Distributor.</span></span> 
    * <span data-ttu-id="cecc9-242">このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。</span><span class="sxs-lookup"><span data-stu-id="cecc9-242">A schedule for the Distribution Agent job for this subscription.</span></span>

5. <span data-ttu-id="cecc9-243">パブリッシャーで、 [、](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) 、 `@publication`、 `@subscriber`のプル値、 `@destination_db`の手順 3 で指定したものと同じ値を指定して `@subscription_type`sp_addsubscriber `@update_mode`を実行し、パブリッシャーにサブスクライバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-243">At the publisher, execute [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) to register the Subscriber at the Publisher, specifying `@publication`, `@subscriber`, `@destination_db`, a value of pull for `@subscription_type`, and the same value specified in step 3 for `@update_mode`.</span></span>

<span data-ttu-id="cecc9-244">これにより、パブリッシャーでプル サブスクリプションが登録されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-244">This registers the pull subscription at the Publisher.</span></span> 


## <a name="to-create-a-queued-updating-push-subscription"></a><span data-ttu-id="cecc9-245">キュー更新プッシュ サブスクリプションを作成するには</span><span class="sxs-lookup"><span data-stu-id="cecc9-245">To create a queued updating push subscription</span></span> ##

1. <span data-ttu-id="cecc9-246">パブリッシャーで、 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)を実行することにより、パブリケーションがキュー更新サブスクリプションをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-246">At the Publisher, verify that the publication supports queued updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="cecc9-247">結果セットの allow_queued_tran の値が 1 である場合、パブリケーションは即時更新サブスクリプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-247">If the value of allow_queued_tran in the result set is 1, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="cecc9-248">結果セットの allow_queued_tran の値が 0 である場合は、キュー更新サブスクリプションを有効にしてパブリケーションを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-248">If the value of allow_queued_tran in the result set is 0, the publication must be recreated with queued updating subscriptions enabled.</span></span> <span data-ttu-id="cecc9-249">詳細については、トランザクション パブリケーションの更新可能なサブスクリプションを有効化する方法 (レプリケーション Transact-SQL プログラミング) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-249">For more information, see How to: Enable Updating Subscriptions for Transactional Publications (Replication Transact-SQL Programming).</span></span>

2. <span data-ttu-id="cecc9-250">パブリッシャーで、 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)を実行することにより、パブリケーションがプッシュ サブスクリプションをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-250">At the Publisher, verify that the publication supports push subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="cecc9-251">結果セットの `allow_push` の値が `1`である場合、パブリケーションはプッシュ サブスクリプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-251">If the value of `allow_push` in the result set is `1`, the publication supports push subscriptions.</span></span>
    * <span data-ttu-id="cecc9-252">`allow_push` の値が `0`である場合、 [には allow_push、](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)には `@property` を指定して `true` sp_changepublication `@value`を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-252">If the value of `allow_push` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying allow_push for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="cecc9-253">パブリッシャーで、 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-253">At the Publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="cecc9-254">`@publication`、 `@subscriber`、 `@destination_db`を指定し、 `@update_mode`に次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-254">Specify `@publication`, `@subscriber`, `@destination_db`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="cecc9-255">`queued tran` - サブスクリプションのキュー更新を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-255">`queued tran` - enables the subscription for queued updating.</span></span>
    * <span data-ttu-id="cecc9-256">`queued failover` - 即時更新をフェールオーバー オプションとするキュー更新のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="cecc9-256">`queued failover` - enables support for queued updating with immediate updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="cecc9-257">queued failover オプションでは、パブリケーションでも即時更新サブスクリプションが有効になっていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="cecc9-257">The queued failover option requires that the publication also be enabled for immediate updating subscriptions.</span></span> <span data-ttu-id="cecc9-258">即時更新へのフェールオーバーを行うために、 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) を使って、サブスクライバーでの変更をパブリッシャーにレプリケートするときに使用する資格情報を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cecc9-258">To fail over to immediate updating, you must use [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) to define the credentials under which changes at the Subscriber are replicated to the Publisher.</span></span>

4. <span data-ttu-id="cecc9-259">パブリッシャーで、 [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-259">At the Publisher, execute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="cecc9-260">次のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-260">Specify the following parameters:</span></span>

    * <span data-ttu-id="cecc9-261">`@subscriber`、 `@subscriber_db`、および `@publication`。</span><span class="sxs-lookup"><span data-stu-id="cecc9-261">`@subscriber`, `@subscriber_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="cecc9-262">`@job_login` および `@job_password`のディストリビューターでディストリビューション エージェントを実行する際に使用する Windows 資格情報。</span><span class="sxs-lookup"><span data-stu-id="cecc9-262">The Windows credentials under which the Distribution Agent at the Distributor runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="cecc9-263">Windows 統合認証を使用して作成された接続では、常に、 `@job_login` および `@job_password`で指定された Windows 資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-263">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="cecc9-264">ディストリビューション エージェントは、常に Windows 統合認証を使用してディストリビューターにローカル接続します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-264">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="cecc9-265">既定では、エージェントは Windows 統合認証を使用してサブスクライバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-265">By default, the agent connects to the Subscriber using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="cecc9-266">(省略可能) サブスクライバーに接続するときに SQL Server 認証を使用する必要がある場合、 `0` には `@subscriber_security_mode` 、 `@subscriber_login` と `@subscriber_password`には SQL Server ログイン情報の値。</span><span class="sxs-lookup"><span data-stu-id="cecc9-266">(Optional) A value of `0` for `@subscriber_security_mode` and the SQL Server login information for `@subscriber_login` and `@subscriber_password`, if you need to use SQL Server Authentication when connecting to the Subscriber.</span></span> 
    * <span data-ttu-id="cecc9-267">このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。</span><span class="sxs-lookup"><span data-stu-id="cecc9-267">A schedule for the Distribution Agent job for this subscription.</span></span>


## <a name="example"></a><span data-ttu-id="cecc9-268">例</span><span class="sxs-lookup"><span data-stu-id="cecc9-268">Example</span></span> ##

<span data-ttu-id="cecc9-269">この例では、即時更新サブスクリプションをサポートするパブリケーションに対する即時更新プル サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-269">This example creates an immediate updating pull subscription to a publication that supports immediate updating subscriptions.</span></span> <span data-ttu-id="cecc9-270">ログインとパスワードの値は、実行時に sqlcmd スクリプト変数を使用して入力されます。</span><span class="sxs-lookup"><span data-stu-id="cecc9-270">Login and password values are supplied at runtime using sqlcmd scripting variables.</span></span>

> [!NOTE]  
>  <span data-ttu-id="cecc9-271">このスクリプトでは sqlcmd スクリプト変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-271">This script uses sqlcmd scripting variables.</span></span> <span data-ttu-id="cecc9-272">`$(MyVariable)`という形式です。</span><span class="sxs-lookup"><span data-stu-id="cecc9-272">They are in the form `$(MyVariable)`.</span></span> <span data-ttu-id="cecc9-273">コマンド ラインと SQL Server Management Studio でスクリプト変数を使用する方法については、「 **レプリケーション システム ストアド プロシージャの概念** 」トピックの「 [レプリケーション スクリプトの実行](../concepts/replication-system-stored-procedures-concepts.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-273">For information about how to use scripting variables on the command line and in SQL Server Management Studio, see the **Executing Replication Scripts** section in the topic [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md).</span></span>

```sql
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a><span data-ttu-id="cecc9-274">キュー更新の競合解決オプションの設定 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cecc9-274">Set Queued Updating Conflict Resolution Options (SQL Server Management Studio)</span></span>
  <span data-ttu-id="cecc9-275">**[パブリケーション プロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、キュー更新サブスクリプションをサポートするパブリケーションの競合解決オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-275">Set conflict resolution options for publications that support queued updating subscriptions on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="cecc9-276">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cecc9-276">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a><span data-ttu-id="cecc9-277">キュー更新の競合解決オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="cecc9-277">To set queued updating conflict resolution options</span></span>  
  
1.  <span data-ttu-id="cecc9-278">**[パブリケーション プロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、 **[競合の解決方法]** オプションに対して、次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="cecc9-278">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select one of the following values for the **Conflict resolution policy** option:</span></span>    
    -   <span data-ttu-id="cecc9-279">**[パブリッシャーの変更を保持します]**</span><span class="sxs-lookup"><span data-stu-id="cecc9-279">**Keep the Publisher change**</span></span>    
    -   <span data-ttu-id="cecc9-280">**[サブスクライバーの変更を保持します]**</span><span class="sxs-lookup"><span data-stu-id="cecc9-280">**Keep the Subscriber change**</span></span>    
    -   <span data-ttu-id="cecc9-281">**[サブスクリプションを再初期化します]**</span><span class="sxs-lookup"><span data-stu-id="cecc9-281">**Reinitialize the subscription**</span></span>    
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="see-also"></a><span data-ttu-id="cecc9-282">参照</span><span class="sxs-lookup"><span data-stu-id="cecc9-282">See Also</span></span> ##
 <span data-ttu-id="cecc9-283">[Create a Publication](create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="cecc9-283">[Create a Publication](create-a-publication.md) </span></span>  
 <span data-ttu-id="cecc9-284">[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="cecc9-284">[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md) </span></span>  
 [<span data-ttu-id="cecc9-285">sqlcmd でのスクリプト変数の使用</span><span class="sxs-lookup"><span data-stu-id="cecc9-285">Use sqlcmd with Scripting Variables</span></span>](../../scripting/sqlcmd-use-with-scripting-variables.md)   

  
