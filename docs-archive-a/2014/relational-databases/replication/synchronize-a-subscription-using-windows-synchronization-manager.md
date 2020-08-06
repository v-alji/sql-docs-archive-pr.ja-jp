---
title: Windows 同期マネージャーを使用したサブスクリプションの同期 (Windows 同期マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], Windows Synchronization Manager
- Windows Synchronization Manager
ms.assetid: 80f15dd6-e84d-4f96-9866-5b34ea531f1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bb31c344f91c68b04e03dd218f22b09bec44830b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716237"
---
# <a name="synchronize-a-subscription-using-windows-synchronization-manager-windows-synchronization-manager"></a><span data-ttu-id="6aa9a-102">Windows 同期マネージャーを使用したサブスクリプションの同期 (Windows 同期マネージャー)</span><span class="sxs-lookup"><span data-stu-id="6aa9a-102">Synchronize a Subscription Using Windows Synchronization Manager (Windows Synchronization Manager)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="6aa9a-103">Windows 同期マネージャーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が同期マネージャーと同じコンピューターで実行されている場合には、サブスクリプションを Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリケーションに同期させるためだけに使用できます (オフライン ファイルや Web ページを同期するためにも使用できます)。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-103">Windows Synchronization Manager can only be used to synchronize subscriptions to Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publications if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running on the same computer as Synchronization Manager (it can also be used to synchronize offline files and Web pages).</span></span> <span data-ttu-id="6aa9a-104">同期マネージャーを使用するには、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-104">To use Synchronization Manager:</span></span>  
  
1.  <span data-ttu-id="6aa9a-105">**[サブスクリプションのプロパティ - \<Subscriber>: \<SubscriptionDatabase>]** ダイアログ ボックスで、Windows 同期マネージャーを使用したプル サブスクリプションの同期を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-105">Enable the synchronization of pull subscriptions with Windows Synchronization Manager in the **Subscription Properties - \<Subscriber>: \<SubscriptionDatabase>** dialog box.</span></span> <span data-ttu-id="6aa9a-106">このダイアログ ボックスへのアクセスの詳細については、「[プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-106">For more information about accessing this dialog box, see [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
2.  <span data-ttu-id="6aa9a-107">Windows の **[スタート]** メニューから、同期マネージャーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-107">Access Synchronization Manager through the **Start** menu in Windows.</span></span>  
  
 <span data-ttu-id="6aa9a-108">同期マネージャーでは、マージ サブスクリプションでインタラクティブ競合回避モジュールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-108">Synchronization Manager allows you to use the Interactive Resolver for merge subscriptions.</span></span> <span data-ttu-id="6aa9a-109">一般に、同期の際に検出された競合は自動的に回避されますが、対話型の競合回避が有効になっていると、同期の際にユーザーが競合を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-109">Typically, conflicts detected during synchronization are resolved automatically, but if interactive resolution is enabled, conflicts can be resolved by a user during synchronization.</span></span> <span data-ttu-id="6aa9a-110">同期が Windows 同期マネージャーの外部で (スケジュールされた同期、または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] かレプリケーション モニターでの要求時同期として) 実行される場合、競合は、アーティクルに指定された競合回避モジュールに従って、ユーザーの介入なしに自動的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-110">If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Replication Monitor), conflicts are resolved automatically without user intervention, according to the resolver specified for the article.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aa9a-111">[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] および [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]以降では、Windows 同期マネージャーの 64 ビット版は 32 ビット サブスクリプションを検出することはできません。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-111">Beginning with [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] and [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)], 64-bit versions of the Windows Synchronization Manager cannot detect 32-bit subscriptions.</span></span>  
  
### <a name="to-enable-the-synchronization-of-pull-subscriptions-with-windows-synchronization-manager"></a><span data-ttu-id="6aa9a-112">Windows 同期マネージャーを使用したプル サブスクリプションの同期を有効化するには</span><span class="sxs-lookup"><span data-stu-id="6aa9a-112">To enable the synchronization of pull subscriptions with Windows Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="6aa9a-113">**[サブスクリプションのプロパティ - \<Subscriber>: \<SubscriptionDatabase>]** ダイアログ ボックスの **[全般]** ページで、 **[Windows 同期マネージャーを使用]** オプションの値として **[有効化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-113">On the **General** page of the **Subscription Properties - \<Subscriber>: \<SubscriptionDatabase>** dialog box, select a value of **Enable** for the **Use Windows Synchronization Manager** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-synchronize-a-pull-subscription-with-synchronization-manager"></a><span data-ttu-id="6aa9a-114">同期マネージャーを使用してプル サブスクリプションを同期するには</span><span class="sxs-lookup"><span data-stu-id="6aa9a-114">To synchronize a pull subscription with Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="6aa9a-115">次の方法のいずれかを使用して、同期マネージャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-115">Launch Synchronization Manager using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6aa9a-116">Internet Explorer で、 **[ツール]** メニューの **[同期]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-116">In Internet Explorer, click **Tools**, and then click **Synchronize**.</span></span>  
  
    -   <span data-ttu-id="6aa9a-117">**[スタート]** ボタンをクリックし、 **[プログラム]** または **[すべてのプログラム]** をポイントします。 **[アクセサリ]** をポイントし、 **[同期]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-117">Click **Start**, point to **Programs** or **All Programs**, point to **Accessories**, and then click **Synchronize**.</span></span>  
  
    -   <span data-ttu-id="6aa9a-118">**[スタート]** メニューの **[ファイル名を指定して実行]**</span><span class="sxs-lookup"><span data-stu-id="6aa9a-118">Click **Start**, and then click **Run.**</span></span> <span data-ttu-id="6aa9a-119">[ファイル名を選択して**実行**] ダイアログボックスで、[開く] フィールドに「」と入力し、 `mobsync.exe` [ **OK**] をクリックします。 **Open**</span><span class="sxs-lookup"><span data-stu-id="6aa9a-119">In the **Run** dialog box, type `mobsync.exe` in the **Open** field, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="6aa9a-120">**[同期する項目]** ダイアログ ボックスで、同期するサブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-120">In the **Items to Synchronize** dialog box, select the subscriptions to synchronize.</span></span> <span data-ttu-id="6aa9a-121">サブスクリプションは、そのコンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-121">Subscriptions are listed under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
3.  <span data-ttu-id="6aa9a-122">**[同期]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-122">Click **Synchronize**.</span></span>  
  
### <a name="to-reinitialize-a-pull-subscription-with-synchronization-manager"></a><span data-ttu-id="6aa9a-123">同期マネージャーを使用してプル サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="6aa9a-123">To reinitialize a pull subscription with Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="6aa9a-124">**[同期する項目]** ダイアログ ボックスでサブスクリプションを選択し、次に **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-124">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6aa9a-125">**[SQL Server サブスクリプション プロパティ]** ダイアログ ボックスで、 **[サブスクリプションの再初期化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-125">In the **SQL Server Subscription Properties** dialog box, click **Reinitialize Subscription**.</span></span>  
  
3.  <span data-ttu-id="6aa9a-126">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-126">Click **Yes**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="6aa9a-127">次回サブスクリプションを同期すると、既定では新しいスナップショットがサブスクリプション データベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-127">The next time the subscription is synchronized, by default a new snapshot is applied to the subscription database.</span></span> <span data-ttu-id="6aa9a-128">詳細については、「 [サブスクリプションの再初期化](reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-128">For more information, see [Reinitialize Subscriptions](reinitialize-subscriptions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aa9a-129">マージ レプリケーションでは、スナップショットを適用する前に、未処理の変更をパブリッシャーにアップロードすることができますが、このオプションは同期マネージャーでは利用できません。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-129">Merge replication allows any outstanding changes to be uploaded to the Publisher before the snapshot is applied, but this option is not available from Synchronization Manager.</span></span> <span data-ttu-id="6aa9a-130">変更をアップロードするには、サブスクリプションを再初期化する前に同期します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-130">To upload changes, synchronize the subscription before reinitializing it.</span></span>  
  
### <a name="to-set-properties-for-a-pull-subscription-in-synchronization-manager"></a><span data-ttu-id="6aa9a-131">同期マネージャーでプル サブスクリプションのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="6aa9a-131">To set properties for a pull subscription in Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="6aa9a-132">**[同期する項目]** ダイアログ ボックスでサブスクリプションを選択し、次に **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-132">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6aa9a-133">以下のタブのプロパティを参照および変更します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-133">View and modify properties on the following tabs:</span></span>  
  
    -   <span data-ttu-id="6aa9a-134">**[識別]**</span><span class="sxs-lookup"><span data-stu-id="6aa9a-134">**Identification**</span></span>  
  
    -   <span data-ttu-id="6aa9a-135">**[サブスクライバー ログイン]** 、 **[ディストリビューター ログイン]** 、および **[パブリッシャー ログイン]** (マージ レプリケーションの場合のみ)</span><span class="sxs-lookup"><span data-stu-id="6aa9a-135">**Subscriber Login**, **Distributor Login**, and **Publisher Login** (for merge replication only)</span></span>  
  
    -   <span data-ttu-id="6aa9a-136">**[Web サーバー情報]** (SQL Server 2005 以降を実行しているサブスクライバー上のマージ サブスクリプションの場合)</span><span class="sxs-lookup"><span data-stu-id="6aa9a-136">**Web Server Information** (for merge subscriptions on Subscribers running SQL Server 2005 or later)</span></span>  
  
    -   <span data-ttu-id="6aa9a-137">**その他**</span><span class="sxs-lookup"><span data-stu-id="6aa9a-137">**Other**</span></span>  
  
     <span data-ttu-id="6aa9a-138">すべての接続で Windows 認証を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-138">It is recommended to use Windows Authentication for all connections.</span></span> <span data-ttu-id="6aa9a-139">ディストリビューション エージェントおよびマージ エージェントで必要な権限については、「 [Replication Agent Security Model](security/replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-139">For information about the permissions required by the Distribution Agent and the Merge Agent, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-pull-subscription-from-synchronization-manager"></a><span data-ttu-id="6aa9a-140">同期マネージャーからプル サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="6aa9a-140">To remove a pull subscription from Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="6aa9a-141">**[同期する項目]** ダイアログ ボックスでサブスクリプションを選択し、次に **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-141">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6aa9a-142">**[SQL Server サブスクリプション プロパティ]** ダイアログ ボックスで、 **[サブスクリプションの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-142">In the **SQL Server Subscription Properties** dialog box, click **Remove Subscription**.</span></span>  
  
3.  <span data-ttu-id="6aa9a-143">**[サブスクリプションの削除]** ダイアログ ボックスで、オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-143">Select an option in the **Remove Subscription** dialog box.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-interactive-resolver"></a><span data-ttu-id="6aa9a-144">インタラクティブ競合回避モジュールを使用するには</span><span class="sxs-lookup"><span data-stu-id="6aa9a-144">To use the Interactive Resolver</span></span>  
  
1.  <span data-ttu-id="6aa9a-145">アーティクルおよびサブスクリプションで、対話型の競合回避を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-145">Enable the article and subscription to use interactive resolution.</span></span> <span data-ttu-id="6aa9a-146">詳細については、「[マージ アーティクルのインタラクティブな競合回避の指定](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-146">For more information, see [Specify Interactive Conflict Resolution for Merge Articles](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>
  
2.  <span data-ttu-id="6aa9a-147">対話型の競合回避が有効になっており、1 つ以上のアーティクルで競合があると、同期マネージャーでサブスクリプションの同期が開始された後、インタラクティブ競合回避モジュールが自動的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-147">After the subscription begins synchronizing in Synchronization Manager, the Interactive Resolver launches automatically if interactive conflict resolution is enabled and there are conflicts for one or more articles.</span></span> <span data-ttu-id="6aa9a-148">インタラクティブ競合回避モジュールは、一度に 1 つずつ、競合および (パブリケーションとサブスクリプションの作成時に指定した回避モジュールに基づく) 推奨の回避方法を表示します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-148">The Interactive Resolver displays conflicts one at a time, with a suggested resolution for each conflict (based on the resolver specified when the publication and subscription were created).</span></span>  
  
3.  <span data-ttu-id="6aa9a-149">必要に応じて、インタラクティブ競合回避モジュールに表示された任意の列を編集し、以下のボタンのいずれかをクリックして競合を回避します。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-149">Optionally edit any of the columns displayed in the Interactive Resolver, and then click one of the following buttons to resolve the conflict:</span></span>  
  
    -   <span data-ttu-id="6aa9a-150">**[推奨設定を優先]**</span><span class="sxs-lookup"><span data-stu-id="6aa9a-150">**Accept Suggested**</span></span>  
  
    -   <span data-ttu-id="6aa9a-151">**[パブリッシャーを優先]**</span><span class="sxs-lookup"><span data-stu-id="6aa9a-151">**Accept Publisher**</span></span>  
  
    -   <span data-ttu-id="6aa9a-152">**[サブスクライバーを優先]**</span><span class="sxs-lookup"><span data-stu-id="6aa9a-152">**Accept Subscriber**</span></span>  
  
    -   <span data-ttu-id="6aa9a-153">**[残りの競合を自動的に解決]** (それ以上入力を行わなくても、現在のすべての競合が回避されます)</span><span class="sxs-lookup"><span data-stu-id="6aa9a-153">**Resolve All Automatically** (all current conflicts are resolved without further input)</span></span>  
  
     <span data-ttu-id="6aa9a-154">選択した行がパブリッシャーやサブスクライバーに適用され、以降の同期の際にトポロジ内の他のノードに反映されます。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-154">The selected row is then applied to the Publisher and/or Subscriber; it is propagated to other nodes in the topology during subsequent synchronizations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aa9a-155">編集した内容は、回避を選択した行の一部でなければ適用されません。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-155">Edits are only applied if they are part of the row that is chosen for resolution.</span></span> <span data-ttu-id="6aa9a-156">たとえば、 **[パブリッシャー]** の下を編集し、 **[サブスクライバーを優先]** をクリックしても、編集内容は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="6aa9a-156">For example, if you make edits under **Publisher**, and then click **Accept Subscriber**, the edits are discarded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa9a-157">参照</span><span class="sxs-lookup"><span data-stu-id="6aa9a-157">See Also</span></span>  
 [<span data-ttu-id="6aa9a-158">Interactive Conflict Resolution</span><span class="sxs-lookup"><span data-stu-id="6aa9a-158">Interactive Conflict Resolution</span></span>](merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
