---
title: レプリケーション モニターのパブリッシャーの追加および削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, adding and removing Publishers
ms.assetid: fa36c4b4-bfa5-494e-92e3-07a02d7332c3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 16c2876b55541e347e4e638132f36ad33932abb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741841"
---
# <a name="add-and-remove-publishers-from-replication-monitor"></a><span data-ttu-id="d6af5-102">レプリケーション モニターのパブリッシャーの追加および削除</span><span class="sxs-lookup"><span data-stu-id="d6af5-102">Add and Remove Publishers from Replication Monitor</span></span>
  <span data-ttu-id="d6af5-103">パブリッシャーになっているサーバーからレプリケーション モニターを起動すると、そのサーバーは自動的にモニターに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-103">The server from which you launch Replication Monitor is automatically added to the monitor if it is a Publisher.</span></span> <span data-ttu-id="d6af5-104">その他のパブリッシャーを追加するには、 **[パブリッシャーの追加]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-104">Additional Publishers can be added through the **Add Publisher** dialog box.</span></span> <span data-ttu-id="d6af5-105">追加したパブリッシャーは、モニターの左ペインのグループの中に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-105">After adding a Publisher, it is displayed in a group in the left pane of the monitor.</span></span> <span data-ttu-id="d6af5-106">既定で **[マイ パブリッシャー]** グループが含まれていますが、新しいグループを作成して、1 つ以上のレプリケーション トポロジを管理できます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-106">The **My Publishers** group is included by default, but you can create new groups to manage one or more replication topologies.</span></span> <span data-ttu-id="d6af5-107">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6af5-107">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
### <a name="to-add-a-sql-server-publisher"></a><span data-ttu-id="d6af5-108">SQL Server パブリッシャーを追加するには</span><span class="sxs-lookup"><span data-stu-id="d6af5-108">To add a SQL Server Publisher</span></span>  
  
1.  <span data-ttu-id="d6af5-109">左ペインで **[レプリケーション モニター]** ノードまたはパブリッシャー グループのノードを右クリックし、 **[パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-109">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="d6af5-110">**[パブリッシャーの追加]** ダイアログ ボックスで、 **[追加]** をクリックし、 **[SQL Server パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-110">In the **Add Publisher** dialog box, click **Add**, and then click **Add SQL Server Publisher**.</span></span>  
  
3.  <span data-ttu-id="d6af5-111">**[サーバーへの接続]** ダイアログ ボックスで、パブリッシャーの名前を入力し、認証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-111">In the **Connect to Server** dialog box, enter the name of the Publisher, and then select the authentication type.</span></span> <span data-ttu-id="d6af5-112">**[SQL Server 認証]** を選択した場合は、ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-112">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="d6af5-113">指定した資格情報はレプリケーション モニターによって保存され、今後このサーバーに接続するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-113">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="d6af5-114">指定する Windows アカウントまたは SQL Server ログインは、固定サーバーロール **sysadmin** またはディストリビューション データベースの固定データベース ロール **replmonitor** のメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6af5-114">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="d6af5-115">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-115">Click **Connect**.</span></span> <span data-ttu-id="d6af5-116">パブリッシャーがリモート ディストリビューターを使用している場合は、ディストリビューターに接続するための **[サーバーへの接続]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-116">If the Publisher uses a remote Distributor, you will be prompted to connect to the Distributor in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="d6af5-117">指定した資格情報はレプリケーション モニターによって保存され、今後このサーバーに接続するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-117">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="d6af5-118">指定する Windows アカウントまたは SQL Server ログインは、固定サーバーロール **sysadmin** またはディストリビューション データベースの固定データベース ロール **replmonitor** のメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6af5-118">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
5.  <span data-ttu-id="d6af5-119">パブリッシャーとディストリビューターの名前が、 **[次のパブリッシャーの監視を開始します]** グリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-119">The name of the Publisher and Distributor are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span>  
  
6.  <span data-ttu-id="d6af5-120">パブリッシャーに対して更新や接続のオプションを指定するには、グリッドでパブリッシャーを選択し、必要に応じてオプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-120">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="d6af5-121">更新オプションの詳細については、「 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6af5-121">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="d6af5-122">レプリケーション モニターでパブリッシャーを表示するグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-122">Select the group under which the Publisher should be displayed in Replication Monitor.</span></span> <span data-ttu-id="d6af5-123">新しいグループを作成するには、 **[新しいグループ]** をクリックし、グループ名を入力します。次に、 **[このパブリッシャーを次のグループに表示する]** ボックスの一覧でそのグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-123">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-add-an-oracle-publisher"></a><span data-ttu-id="d6af5-124">Oracle パブリッシャーを追加するには</span><span class="sxs-lookup"><span data-stu-id="d6af5-124">To add an Oracle Publisher</span></span>  
  
1.  <span data-ttu-id="d6af5-125">左ペインで **[レプリケーション モニター]** ノードまたはパブリッシャー グループのノードを右クリックし、 **[パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-125">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="d6af5-126">**[パブリッシャーの追加]** ダイアログ ボックスで、 **[追加]** をクリックし、 **[Oracle パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-126">In the **Add Publisher** dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span>  
  
3.  <span data-ttu-id="d6af5-127">**[サーバーへの接続]** ダイアログ ボックスで、Oracle パブリッシャーに関連付けられている [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターの名前を入力し、認証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-127">In the **Connect to Server** dialog box, enter the name of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor associated with the Oracle Publisher, and then select the authentication type.</span></span> <span data-ttu-id="d6af5-128">**[SQL Server 認証]** を選択した場合は、ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-128">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="d6af5-129">指定した資格情報はレプリケーション モニターによって保存され、今後このサーバーに接続するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-129">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="d6af5-130">指定する Windows アカウントまたは SQL Server ログインは、固定サーバーロール **sysadmin** またはディストリビューション データベースの固定データベース ロール **replmonitor** のメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6af5-130">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="d6af5-131">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-131">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="d6af5-132">パブリッシャーとディストリビューターの名前が、 **[次のパブリッシャーの監視を開始します]** グリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-132">The name of the Publisher and Distributor are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span>  
  
6.  <span data-ttu-id="d6af5-133">パブリッシャーに対して更新や接続のオプションを指定するには、グリッドでパブリッシャーを選択し、必要に応じてオプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-133">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="d6af5-134">更新オプションの詳細については、「 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6af5-134">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="d6af5-135">レプリケーション モニターでパブリッシャーを表示するグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-135">Select the group under which the Publisher should be displayed in Replication Monitor.</span></span> <span data-ttu-id="d6af5-136">新しいグループを作成するには、 **[新しいグループ]** をクリックし、グループ名を入力します。次に、 **[このパブリッシャーを次のグループに表示する]** ボックスの一覧でそのグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-136">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-add-one-or-more-publishers-that-use-the-same-distributor"></a><span data-ttu-id="d6af5-137">同じディストリビューターを使用する 1 つ以上のパブリッシャーを追加するには</span><span class="sxs-lookup"><span data-stu-id="d6af5-137">To add one or more Publishers that use the same Distributor</span></span>  
  
1.  <span data-ttu-id="d6af5-138">左ペインで **[レプリケーション モニター]** ノードまたはパブリッシャー グループのノードを右クリックし、 **[パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-138">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="d6af5-139">**[パブリッシャーの追加]** ダイアログ ボックスで、 **[追加]** をクリックし、 **[ディストリビューターを指定し、そのパブリッシャーを追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-139">In the **Add Publisher** dialog box, click **Add**, and then click **Specify a Distributor and Add Its Publishers**.</span></span>  
  
3.  <span data-ttu-id="d6af5-140">**[サーバーへの接続]** ダイアログ ボックスで、ディストリビューターの名前を入力し、認証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-140">In the **Connect to Server** dialog box, enter the name of the Distributor, and then select the authentication type.</span></span> <span data-ttu-id="d6af5-141">**[SQL Server 認証]** を選択した場合は、ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-141">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="d6af5-142">指定した資格情報はレプリケーション モニターによって保存され、今後このサーバーに接続するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-142">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="d6af5-143">指定する Windows アカウントまたは SQL Server ログインは、固定サーバーロール **sysadmin** またはディストリビューション データベースの固定データベース ロール **replmonitor** のメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6af5-143">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="d6af5-144">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-144">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="d6af5-145">ディストリビューターと各パブリッシャーの名前が、 **[次のパブリッシャーの監視を開始します]** グリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6af5-145">The name of the Distributor and each Publisher are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span> <span data-ttu-id="d6af5-146">既にレプリケーション モニターに追加されているパブリッシャーはグリッドに表示されません。</span><span class="sxs-lookup"><span data-stu-id="d6af5-146">If a Publisher has already been added to Replication Monitor, it does not appear in the grid.</span></span>  
  
6.  <span data-ttu-id="d6af5-147">パブリッシャーに対して更新や接続のオプションを指定するには、グリッドでパブリッシャーを選択し、必要に応じてオプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-147">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="d6af5-148">更新オプションの詳細については、「 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6af5-148">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="d6af5-149">レプリケーション モニターでパブリッシャーを表示するグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-149">Select the group under which Publishers should be displayed in Replication Monitor.</span></span> <span data-ttu-id="d6af5-150">新しいグループを作成するには、 **[新しいグループ]** をクリックし、グループ名を入力します。次に、 **[このパブリッシャーを次のグループに表示する]** ボックスの一覧でそのグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-150">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-modify-settings-for-the-publisher-and-publisher-groups"></a><span data-ttu-id="d6af5-151">パブリッシャーおよびパブリッシャー グループの設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="d6af5-151">To modify settings for the Publisher and Publisher Groups</span></span>  
  
1.  <span data-ttu-id="d6af5-152">左ペインでパブリッシャーを右クリックし、 **[パブリッシャーの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-152">Right-click a Publisher in the left pane, and then click **Publisher Settings**.</span></span>  
  
2.  <span data-ttu-id="d6af5-153">**[パブリッシャーの設定]** ダイアログ ボックスで設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-153">Make any changes in the **Publisher Settings** dialog box:</span></span>  
  
    -   <span data-ttu-id="d6af5-154">レプリケーション モニターがサーバーに接続するときに使用する資格情報を変更するには、 **[パブリッシャー接続]** または **[ディストリビューター接続]** をクリックし、 **[サーバーへの接続]** ダイアログ ボックスに資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-154">To change the credentials that Replication Monitor uses to connect to a server, click **Publisher Connection** or **Distributor Connection**, and then enter credentials in the **Connect to Server** dialog box.</span></span>  
  
    -   <span data-ttu-id="d6af5-155">パブリッシャーを別のグループに移動するには、 **[次のパブリッシャーの監視を開始します]** グリッドでパブリッシャーを選択し、 **[このパブリッシャーを次のグループに表示する]** ボックスの一覧で新しいグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-155">To move a Publisher from one group to another, select the Publisher in the **Start monitoring the following Publisher(s)** grid, and then select the new group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-publisher-from-replication-monitor"></a><span data-ttu-id="d6af5-156">レプリケーション モニターからパブリッシャーを削除するには</span><span class="sxs-lookup"><span data-stu-id="d6af5-156">To remove a Publisher from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="d6af5-157">左ペインでパブリッシャーを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-157">Right-click a Publisher in the left pane.</span></span>  
  
2.  <span data-ttu-id="d6af5-158">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-158">Click **Remove**.</span></span>  
  
### <a name="to-add-a-publisher-group-to-replication-monitor"></a><span data-ttu-id="d6af5-159">レプリケーション モニターにパブリッシャー グループを追加するには</span><span class="sxs-lookup"><span data-stu-id="d6af5-159">To add a Publisher group to Replication Monitor</span></span>  
  
1.  <span data-ttu-id="d6af5-160">パブリッシャー グループは、パブリッシャーを追加するとき、またはパブリッシャーの設定を変更するときにしか作成できません。</span><span class="sxs-lookup"><span data-stu-id="d6af5-160">Publisher groups can be created only when adding a Publisher or modifying settings for a Publisher.</span></span> <span data-ttu-id="d6af5-161">詳細については、パブリッシャーを追加する手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6af5-161">See the how to procedures on adding a Publisher for more information.</span></span>  
  
### <a name="to-remove-a-publisher-group-from-replication-monitor"></a><span data-ttu-id="d6af5-162">レプリケーション モニターからパブリッシャー グループを削除するには</span><span class="sxs-lookup"><span data-stu-id="d6af5-162">To remove a Publisher group from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="d6af5-163">すべてのパブリッシャーを別のグループに移動するか、レプリケーション モニターから削除します。</span><span class="sxs-lookup"><span data-stu-id="d6af5-163">Move all Publishers to a different group or remove them from Replication Monitor.</span></span> <span data-ttu-id="d6af5-164">詳細については、このトピックの上記の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6af5-164">For more information, see previous procedures in this topic.</span></span>  
  
2.  <span data-ttu-id="d6af5-165">パブリッシャー グループを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6af5-165">Right-click the Publisher group, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6af5-166">参照</span><span class="sxs-lookup"><span data-stu-id="d6af5-166">See Also</span></span>  
 <span data-ttu-id="d6af5-167">[[ディストリビューションの構成]](../configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="d6af5-167">[Configure Distribution](../configure-distribution.md) </span></span>  
 [<span data-ttu-id="d6af5-168">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="d6af5-168">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
