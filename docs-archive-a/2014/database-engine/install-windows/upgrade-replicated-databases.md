---
title: レプリケートされたデータベースのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- merge replication database upgrades [SQL Server replication]
- replication [SQL Server], upgrading
- transactional replication, upgrading databases
- snapshot replication [SQL Server], upgrading databases
- upgrading replicated databases
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 326a94820876b40128428aac58e47c650ce122b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634603"
---
# <a name="upgrade-replicated-databases"></a><span data-ttu-id="d87f3-102">レプリケートされたデータベースのアップグレード</span><span class="sxs-lookup"><span data-stu-id="d87f3-102">Upgrade Replicated Databases</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="d87f3-103">では、レプリケートされたデータベースを以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からアップグレードすることができます。ノードのアップグレード中は、その他のノードでの操作を停止する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d87f3-103">supports upgrading replicated databases from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; it is not required to stop activity at other nodes while a node is being upgraded.</span></span> <span data-ttu-id="d87f3-104">トポロジでサポートされるバージョンに関して、以下の規則が守られていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d87f3-104">Ensure that you adhere to the rules regarding which versions are supported in a topology:</span></span>  
  
-   <span data-ttu-id="d87f3-105">ディストリビューターは、パブリッシャーのバージョン以上であればどのバージョンでも使用できます (多くの場合、ディストリビューターはパブリッシャーと同じインスタンスです)。</span><span class="sxs-lookup"><span data-stu-id="d87f3-105">A Distributor can be any version as long as it is greater than or equal to the Publisher version (in many cases the Distributor is the same instance as the Publisher).</span></span>  
  
-   <span data-ttu-id="d87f3-106">パブリッシャーは、ディストリビューターのバージョン以下であればどのバージョンでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-106">A Publisher can be any version as long as it less than or equal to the Distributor version.</span></span>  
  
-   <span data-ttu-id="d87f3-107">サブスクライバーのバージョンは、次のように、パブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d87f3-107">Subscriber version depends on the type of publication:</span></span>  
  
    -   <span data-ttu-id="d87f3-108">トランザクション パブリケーションのサブスクライバーは、2 つのパブリッシャー バージョンのうちどちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-108">A Subscriber to a transactional publication can be any version within two versions of the Publisher version.</span></span> <span data-ttu-id="d87f3-109">たとえば、実行中の [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] のパブリッシャーには [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のサブスクライバーを設定することができ、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のパブリッシャーには [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] のサブスクライバーを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-109">For example: a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Publisher running can have [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Subscribers; and a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Publisher can have [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Subscribers.</span></span>  
  
    -   <span data-ttu-id="d87f3-110">マージ パブリケーションのサブスクライバーは、パブリッシャーのバージョン以下であればどのバージョンでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-110">A Subscriber to a merge publication can be any version less than or equal to the Publisher version.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d87f3-111">このトピックは、セットアップ ヘルプ ドキュメントおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックで参照できます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-111">This topic is available in the Setup Help documentation and in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="d87f3-112">セットアップ ヘルプ ドキュメントで太字で表示されているトピック リンクは、オンライン ブックでのみ参照可能なトピックを示しています。</span><span class="sxs-lookup"><span data-stu-id="d87f3-112">Topic links that appear as bold text in the Setup Help documentation refer to topics that are only available in Books Online.</span></span>  
  
## <a name="run-the-log-reader-agent-for-transactional-replication-before-upgrade"></a><span data-ttu-id="d87f3-113">アップグレードの前にトランザクション レプリケーション用にログ リーダー エージェントを実行する方法</span><span class="sxs-lookup"><span data-stu-id="d87f3-113">Run the Log Reader Agent for Transactional Replication Before Upgrade</span></span>  
 <span data-ttu-id="d87f3-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードする前には、パブリッシュされたテーブルからコミットされたすべてのトランザクションが、ログ リーダー エージェントによって処理されているかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d87f3-114">Before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must make sure that all committed transactions from published tables have been processed by the Log Reader Agent.</span></span> <span data-ttu-id="d87f3-115">すべてのトランザクションが処理されたことを確認するには、トランザクション パブリケーションを含んだ各データベースに対して次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-115">To make sure that all transactions have been processed, perform the following steps for each database that contains transactional publications:</span></span>  
  
1.  <span data-ttu-id="d87f3-116">データベースのログ リーダー エージェントが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-116">Make sure that the Log Reader Agent is running for the database.</span></span> <span data-ttu-id="d87f3-117">既定では、エージェントは継続的に実行されています。</span><span class="sxs-lookup"><span data-stu-id="d87f3-117">By default, the agent runs continuously.</span></span>  
  
2.  <span data-ttu-id="d87f3-118">パブリッシュされたテーブル上のユーザー アクティビティを停止します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-118">Stop user activity on published tables.</span></span>  
  
3.  <span data-ttu-id="d87f3-119">トランザクションをディストリビューション データベースにコピーする時間をログ リーダー エージェントに与えてから、エージェントを停止します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-119">Allow time for the Log Reader Agent to copy transactions to the distribution database, and then stop the agent.</span></span>  
  
4.  <span data-ttu-id="d87f3-120">[sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) を実行し、すべてのトランザクションが処理されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-120">Execute [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) to verify that all transactions have been processed.</span></span> <span data-ttu-id="d87f3-121">この手順の結果セットを空にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d87f3-121">The result set from this procedure should be empty.</span></span>  
  
5.  <span data-ttu-id="d87f3-122">[sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) を実行し、sp_replcmds から接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-122">Execute [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) to close the connection from sp_replcmds.</span></span>  
  
6.  <span data-ttu-id="d87f3-123">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]へのサーバー アップグレードを実行します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-123">Perform the server upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
7.  <span data-ttu-id="d87f3-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントとログ リーダー エージェントがアップグレードの後に自動的に起動しない場合は、これらを再起動します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-124">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and the Log Reader Agent if they do not start automatically after the upgrade.</span></span>  
  
## <a name="run-agents-for-merge-replication-after-upgrade"></a><span data-ttu-id="d87f3-125">アップグレード後のマージ レプリケーション用エージェントの実行</span><span class="sxs-lookup"><span data-stu-id="d87f3-125">Run Agents for Merge Replication After Upgrade</span></span>  
 <span data-ttu-id="d87f3-126">アップグレード後は、マージ パブリケーションごとにスナップショット エージェントを実行し、サブスクリプションごとにマージ エージェントを実行して、レプリケーション メタデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-126">After upgrade, run the Snapshot Agent for each merge publication and the Merge Agent for each subscription to update replication metadata.</span></span> <span data-ttu-id="d87f3-127">サブスクリプションを再初期化する必要がないので、新しいスナップショットを適用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d87f3-127">You do not have to apply the new snapshot, because it is not necessary to reinitialize subscriptions.</span></span> <span data-ttu-id="d87f3-128">サブスクリプション メタデータは、アップグレード後に最初にマージ エージェントを実行したときに更新されます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-128">Subscription metadata is updated the first time the Merge Agent is run after upgrade.</span></span> <span data-ttu-id="d87f3-129">そのため、サブスクリプション データベースは、パブリッシャーのアップグレード中にオンライン状態でアクティブなままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-129">This means that the subscription database can remain online and active during the Publisher upgrade.</span></span>  
  
 <span data-ttu-id="d87f3-130">マージ レプリケーションでは、パブリケーション データベースおよびサブスクリプション データベース内の多数のシステム テーブルに、パブリケーション メタデータおよびサブスクリプション メタデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-130">Merge replication stores publication and subscription metadata in a number of system tables in the publication and subscription databases.</span></span> <span data-ttu-id="d87f3-131">スナップショット エージェントを実行すると、パブリケーション メタデータが更新され、マージ エージェントを実行すると、サブスクリプション メタデータが更新されます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-131">Running the Snapshot Agent updates publication metadata and running the Merge Agent updates subscription metadata.</span></span> <span data-ttu-id="d87f3-132">生成が必要なのはパブリケーション スナップショットのみです。</span><span class="sxs-lookup"><span data-stu-id="d87f3-132">It is only required to generate a publication snapshot.</span></span> <span data-ttu-id="d87f3-133">パラメーター化されたフィルターがマージ パブリケーションで使用される場合は、各パーティションにもスナップショットが必要です。</span><span class="sxs-lookup"><span data-stu-id="d87f3-133">If a merge publication uses parameterized filters, each partition also has a snapshot.</span></span> <span data-ttu-id="d87f3-134">これらのパーティション スナップショットを更新する必要はありません</span><span class="sxs-lookup"><span data-stu-id="d87f3-134">It is not necessary to update these partitioned snapshots.</span></span>  
  
 <span data-ttu-id="d87f3-135">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、レプリケーション モニター、またはコマンド ラインで各エージェントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-135">Run the agents from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Replication Monitor, or from the command line.</span></span> <span data-ttu-id="d87f3-136">スナップショット エージェントの実行の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d87f3-136">For more information about running the Snapshot Agent, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d87f3-137">初期スナップショットの作成および適用</span><span class="sxs-lookup"><span data-stu-id="d87f3-137">Create and Apply the Initial Snapshot</span></span>](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [<span data-ttu-id="d87f3-138">レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d87f3-138">Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="d87f3-139">初期スナップショットの作成および適用</span><span class="sxs-lookup"><span data-stu-id="d87f3-139">Create and Apply the Initial Snapshot</span></span>](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [<span data-ttu-id="d87f3-140">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="d87f3-140">Replication Agent Executables Concepts</span></span>](../../../2014/relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 <span data-ttu-id="d87f3-141">マージ エージェントの実行の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d87f3-141">For more information about running the Merge Agent, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d87f3-142">プル サブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="d87f3-142">Synchronize a Pull Subscription</span></span>](../../../2014/relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [<span data-ttu-id="d87f3-143">プッシュ サブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="d87f3-143">Synchronize a Push Subscription</span></span>](../../../2014/relational-databases/replication/synchronize-a-push-subscription.md)  
  
 <span data-ttu-id="d87f3-144">マージ レプリケーションを使用するトポロジで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアップグレードした後に、新しい機能を使用する場合は、すべてのパブリケーションのパブリケーション互換性レベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-144">After upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a topology that uses merge replication, change the publication compatibility level of any publications if you want to use new features.</span></span>  
  
## <a name="upgrading-to-standard-workgroup-or-express-editions"></a><span data-ttu-id="d87f3-145">Standard Edition、Workgroup Edition、または Express Edition へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="d87f3-145">Upgrading to Standard, Workgroup, or Express Editions</span></span>  
 <span data-ttu-id="d87f3-146">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のいずれかのエディションから別のエディションへアップグレードする前に、現在使用している機能がアップグレード先のエディションでサポートされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-146">Before upgrading from one edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to another, verify that the functionality you are currently using is supported in the edition to which you are upgrading.</span></span> <span data-ttu-id="d87f3-147">詳細については、「 [SQL Server 2014 の各エディションがサポートする機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」のレプリケーションに関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d87f3-147">For more information, see the section on Replication in [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="web-synchronization-for-merge-replication"></a><span data-ttu-id="d87f3-148">マージ レプリケーションの Web 同期</span><span class="sxs-lookup"><span data-stu-id="d87f3-148">Web Synchronization for Merge Replication</span></span>  
 <span data-ttu-id="d87f3-149">マージ レプリケーションの Web 同期オプションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナー (replisapi.dll) を、同期に使用するインターネット インフォメーション サービス (IIS) サーバーの仮想ディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d87f3-149">The Web synchronization option for merge replication requires that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (replisapi.dll) be copied to the virtual directory on the Internet Information Services (IIS) server used for synchronization.</span></span> <span data-ttu-id="d87f3-150">Web 同期を構成すると、Web 同期の構成ウィザードにより、ファイルが仮想ディレクトリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d87f3-150">When you configure Web synchronization, the file is copied to the virtual directory by the Configure Web Synchronization Wizard.</span></span> <span data-ttu-id="d87f3-151">IIS サーバーにインストールされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをアップグレードする場合、replisapi.dll を COM ディレクトリから IIS サーバーの仮想ディレクトリへ手動でコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d87f3-151">If you upgrade the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components installed on the IIS server, you must manually copy replisapi.dll from the COM directory to the virtual directory on the IIS server.</span></span> <span data-ttu-id="d87f3-152">Web 同期の構成の詳細については、「 [Web 同期の構成](../../../2014/relational-databases/replication/configure-web-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d87f3-152">For more information about configuring Web synchronization, see [Configure Web Synchronization](../../../2014/relational-databases/replication/configure-web-synchronization.md).</span></span>  
  
## <a name="restoring-a-replicated-database-from-an-earlier-version"></a><span data-ttu-id="d87f3-153">以前のバージョンからレプリケートされたデータベースの復元</span><span class="sxs-lookup"><span data-stu-id="d87f3-153">Restoring a Replicated Database from an Earlier Version</span></span>  
 <span data-ttu-id="d87f3-154">以前のバージョンからレプリケートされたデータベースのバックアップを復元するときにレプリケーション設定が保持されるようにするには、バックアップが作成されたサーバーおよびデータベースと同じ名前のサーバーおよびデータベースに復元します。</span><span class="sxs-lookup"><span data-stu-id="d87f3-154">To ensure replication settings are retained when restoring a backup of a replicated database from a previous version: restore to a server and database with the same names as the server and database at which the backup was taken.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d87f3-155">参照</span><span class="sxs-lookup"><span data-stu-id="d87f3-155">See Also</span></span>  
 <span data-ttu-id="d87f3-156">[レプリケーション管理に関する FAQ](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="d87f3-156">[Replication Administration FAQ](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="d87f3-157">[レプリケーションの下位互換性](../../../2014/relational-databases/replication/replication-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="d87f3-157">[Replication Backward Compatibility](../../../2014/relational-databases/replication/replication-backward-compatibility.md) </span></span>  
 <span data-ttu-id="d87f3-158">[サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="d87f3-158">[Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 [<span data-ttu-id="d87f3-159">SQL Server 2014 へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="d87f3-159">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
  
  
