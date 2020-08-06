---
title: プル サブスクリプションのプロパティの表示または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying subscriptions
- viewing replication properties
- modifying replication properties, pull subscriptions
- pull subscriptions [SQL Server replication], modifying
- subscriptions [SQL Server replication], pull
- pull subscriptions [SQL Server replication], properties
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b847a22d31bbf3ea7540c55339fe27531134125
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631762"
---
# <a name="view-and-modify-pull-subscription-properties"></a><span data-ttu-id="eb85d-102">プル サブスクリプションのプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="eb85d-102">View and Modify Pull Subscription Properties</span></span>
  <span data-ttu-id="eb85d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プル サブスクリプションのプロパティを表示および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-103">This topic describes how to view and modify pull subscription properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="eb85d-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="eb85d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eb85d-105">**プル サブスクリプションのプロパティを表示および変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="eb85d-105">**To view and modify pull subscription properties, using:**</span></span>  
  
     [<span data-ttu-id="eb85d-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb85d-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eb85d-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb85d-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="eb85d-108">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="eb85d-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eb85d-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="eb85d-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="eb85d-110">パブリッシャーまたはサブスクライバーからのプル サブスクリプションのプロパティは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] から利用できる **[サブスクリプションのプロパティ - \<Publisher>: \<PublicationDatabase>]** ダイアログ ボックスで表示します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-110">View pull subscription properties from the Publisher or the Subscriber in the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="eb85d-111">その他のプロパティはサブスクライバーから表示でき、サブスクライバーで変更できます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-111">More properties are visible from the Subscriber, and properties can be modified at the Subscriber.</span></span> <span data-ttu-id="eb85d-112">パブリッシャーからも、レプリケーション モニターの **[すべてのサブスクリプション]** タブでプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-112">You can also view properties from the Publisher on the **All Subscriptions** tab, which is available in Replication Monitor.</span></span> <span data-ttu-id="eb85d-113">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb85d-113">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-management-studio"></a><span data-ttu-id="eb85d-114">Management Studio でパブリッシャーからのプル サブスクリプション プロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-114">To view pull subscription properties from the Publisher in Management Studio</span></span>  
  
1.  <span data-ttu-id="eb85d-115">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="eb85d-116">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-116">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="eb85d-117">適切なパブリケーションを展開し、サブスクリプションを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-117">Expand the appropriate publication, right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="eb85d-118">プロパティを表示して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-118">View properties, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-pull-subscription-properties-from-the-subscriber-in-management-studio"></a><span data-ttu-id="eb85d-119">Management Studio でサブスクライバーからのプル サブスクリプション プロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-119">To view and modify pull subscription properties from the Subscriber in Management Studio</span></span>  
  
1.  <span data-ttu-id="eb85d-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-120">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="eb85d-121">**[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="eb85d-122">サブスクリプションを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-122">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="eb85d-123">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-123">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-replication-monitor"></a><span data-ttu-id="eb85d-124">レプリケーション モニターでパブリッシャーからのプル サブスクリプション プロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-124">To view pull subscription properties from the Publisher in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="eb85d-125">レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-125">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="eb85d-126">**[すべてのサブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-126">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="eb85d-127">サブスクリプションを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-127">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="eb85d-128">プロパティを表示して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-128">View properties, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eb85d-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="eb85d-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="eb85d-130">レプリケーション ストアド プロシージャを使用して、プル サブスクリプションを変更し、そのプロパティにプログラムからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-130">Pull subscriptions can be modified and their properties accessed programmatically using replication stored procedures.</span></span> <span data-ttu-id="eb85d-131">使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eb85d-131">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="eb85d-132">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-132">To view the properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="eb85d-133">サブスクライバーで、 [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-133">At the Subscriber, execute [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql).</span></span> <span data-ttu-id="eb85d-134">**@publisher**、、およびを指定し **@publisher_db** **@publication** ます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-134">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="eb85d-135">これにより、サブスクライバーのシステム テーブルに格納されている、サブスクリプションに関する情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-135">This returns information about the subscription that is stored in system tables at the Subscriber.</span></span>  
  
2.  <span data-ttu-id="eb85d-136">サブスクライバーで、 [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-136">At the Subscriber, execute [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql).</span></span> <span data-ttu-id="eb85d-137">**@publisher**、、 **@publisher_db** **@publication** 、およびに対して次のいずれかの値を指定し **@publication_type** ます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-137">Specify **@publisher**, **@publisher_db**, **@publication**, and one of the following values for **@publication_type**:</span></span>  
  
    -   <span data-ttu-id="eb85d-138">**0** - サブスクリプションがトランザクション パブリケーションに属します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-138">**0** - Subscription belongs to a transactional publication.</span></span>  
  
    -   <span data-ttu-id="eb85d-139">**1** - サブスクリプションがスナップショット パブリケーションに属します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-139">**1** - Subscription belongs to a snapshot publication.</span></span>  
  
3.  <span data-ttu-id="eb85d-140">パブリッシャーで、 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-140">At the Publisher, execute [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="eb85d-141">およびを指定し **@publication** **@subscriber** ます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-141">Specify **@publication** and **@subscriber**.</span></span>  
  
4.  <span data-ttu-id="eb85d-142">パブリッシャーで[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)を実行し、を指定 **@subscriber** します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-142">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span> <span data-ttu-id="eb85d-143">これにより、サブスクライバーに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-143">This displays information about the Subscriber.</span></span>  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="eb85d-144">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-144">To change the properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="eb85d-145">サブスクライバーで、、、を指定して[sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql)を実行します。この場合、 **@publisher** には **@publisher_db** **@publication** **0** (トランザクション) または**1** (snapshot) の値を、には変更するサブスクリプションプロパティを、には新しい値を指定し **@publication_type** **@property** **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-145">At the Subscriber, execute [sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql), specifying **@publisher**, **@publisher_db**, **@publication**, a value of either **0** (transactional) or **1** (snapshot) for **@publication_type**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
2.  <span data-ttu-id="eb85d-146">(省略可) サブスクライバー側のサブスクリプション データベースに対して、 [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-146">(Optional) At the Subscriber on the subscription database, execute [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql).</span></span> <span data-ttu-id="eb85d-147">にディストリビューションエージェントジョブの ID を指定 **@jobid** し、次のデータ変換サービス (DTS) パッケージのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-147">Specify the ID of the Distribution Agent job for **@jobid**, and the following Data Transformation Services (DTS) package properties:</span></span>  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     <span data-ttu-id="eb85d-148">これにより、サブスクリプションの DTS パッケージ プロパティが変更されます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-148">This changes the DTS package properties of a subscription.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb85d-149">ジョブ ID は、 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)を実行することで取得できます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-149">The job ID can be obtained by executing [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span>  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="eb85d-150">マージ パブリケーションに対するプル サブスクリプションのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-150">To view the properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="eb85d-151">サブスクライバーで、 [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-151">At the Subscriber, execute [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="eb85d-152">**@publisher**、、およびを指定し **@publisher_db** **@publication** ます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-152">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span>  
  
2.  <span data-ttu-id="eb85d-153">サブスクライバーで、 [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-153">At the Subscriber, execute [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql).</span></span> <span data-ttu-id="eb85d-154">**@publisher**、、 **@publisher_db** **@publication** 、およびの値を2に指定し **@publication_type** ます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-154">Specify **@publisher**, **@publisher_db**, **@publication**, and a value of 2 for **@publication_type**.</span></span>  
  
3.  <span data-ttu-id="eb85d-155">パブリッシャーで [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) を実行し、サブスクリプション情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-155">At the Publisher, execute [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) to display subscription information.</span></span> <span data-ttu-id="eb85d-156">特定のサブスクリプションに関する情報を返すには **@publication** 、、 **@subscriber** 、およびに**pull**の値を指定する必要があり **@subscription_type** ます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-156">To return information on a specific subscription, you must specify **@publication**, **@subscriber**, and a value of **pull** for **@subscription_type**.</span></span>  
  
4.  <span data-ttu-id="eb85d-157">パブリッシャーで[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)を実行し、を指定 **@subscriber** します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-157">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span> <span data-ttu-id="eb85d-158">これにより、サブスクライバーに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-158">This displays information about the Subscriber.</span></span>  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="eb85d-159">マージ パブリケーションに対するプル サブスクリプションのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-159">To change the properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="eb85d-160">サブスクライバーで、 [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-160">At the Subscriber, execute [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql).</span></span> <span data-ttu-id="eb85d-161">**@publication**、、 **@publisher** **@publisher_db** 、変更するサブスクリプションプロパティを、 **@property** および新しい値として指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-161">Specify **@publication**, **@publisher**, **@publisher_db**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="eb85d-162">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="eb85d-162">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="eb85d-163">プル サブスクリプションのプロパティを表示または変更する際に使用する RMO のクラスは、プル サブスクリプションがサブスクライブされるパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eb85d-163">The RMO classes you use to view or modify pull subscription properties depend on the type of publication to which the pull subscription is subscribed.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="eb85d-164">スナップショット パブリケーションまたはトランザクション パブリケーションのプル サブスクリプションのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-164">To view or modify properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="eb85d-165"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-165">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="eb85d-166"><xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-166">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class.</span></span>  
  
3.  <span data-ttu-id="eb85d-167"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-167">Set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="eb85d-168">手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-168">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="eb85d-169"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-169">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="eb85d-170">このメソッドから `false` が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションがサーバー上に存在していません。</span><span class="sxs-lookup"><span data-stu-id="eb85d-170">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.</span></span>  
  
6.  <span data-ttu-id="eb85d-171">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> の設定可能なプロパティに新しい値を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-171">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="eb85d-172">(省略可) 新しい設定を表示するには、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> メソッドを呼び出して、アーティクルのプロパティを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-172">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the article.</span></span>  
  
8.  <span data-ttu-id="eb85d-173">すべての接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-173">Close all connections.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="eb85d-174">マージ パブリケーションのプル サブスクリプションのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="eb85d-174">To view or modify properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="eb85d-175"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-175">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="eb85d-176"><xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-176">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class.</span></span>  
  
3.  <span data-ttu-id="eb85d-177"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-177">Set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="eb85d-178">手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-178">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="eb85d-179"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="eb85d-180">このメソッドから `false` が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションがサーバー上に存在していません。</span><span class="sxs-lookup"><span data-stu-id="eb85d-180">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.</span></span>  
  
6.  <span data-ttu-id="eb85d-181">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> の設定可能なプロパティに新しい値を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eb85d-181">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="eb85d-182">(省略可) 新しい設定を表示するには、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> メソッドを呼び出して、アーティクルのプロパティを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="eb85d-182">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the article.</span></span>  
  
8.  <span data-ttu-id="eb85d-183">すべての接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="eb85d-183">Close all connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb85d-184">参照</span><span class="sxs-lookup"><span data-stu-id="eb85d-184">See Also</span></span>  
 <span data-ttu-id="eb85d-185">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="eb85d-185">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="eb85d-186">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="eb85d-186">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="eb85d-187">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="eb85d-187">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
