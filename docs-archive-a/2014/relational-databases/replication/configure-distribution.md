---
title: ディストリビューションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- remote Distributors [SQL Server replication]
- transactional replication, configuring distribution
- distribution databases [SQL Server replication], sizing
- Distributors [SQL Server replication], configuring
- distribution databases [SQL Server replication], about distribution databases
- distribution databases [SQL Server replication]
- merge replication [SQL Server replication], configuring distribution
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0378fe285ba57e1420b7e6bebf5e2e6fe13d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634401"
---
# <a name="configure-distribution"></a><span data-ttu-id="91f16-102">ディストリビューションの構成</span><span class="sxs-lookup"><span data-stu-id="91f16-102">Configure Distribution</span></span>
  <span data-ttu-id="91f16-103">ディストリビューターは、ディストリビューション データベースを含むサーバーです。ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションに対するトランザクションが格納されます。</span><span class="sxs-lookup"><span data-stu-id="91f16-103">The Distributor is a server that contains the distribution database, which stores metadata and history data for all types of replication and transactions for transactional replication.</span></span> <span data-ttu-id="91f16-104">レプリケーションを設定するには、ディストリビューターを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f16-104">To set up replication, you must configure a Distributor.</span></span> <span data-ttu-id="91f16-105">パブリッシャーはそれぞれ 1 つのディストリビューター インスタンスにしか割り当てることができませんが、複数のパブリッシャーで 1 つのディストリビューターを共有できます。</span><span class="sxs-lookup"><span data-stu-id="91f16-105">Each Publisher can be assigned to only a single Distributor instance, but multiple publishers can share a Distributor.</span></span> <span data-ttu-id="91f16-106">サーバーがディストリビューターとして指定されると、次のようなリソースが新たに消費されることになります。</span><span class="sxs-lookup"><span data-stu-id="91f16-106">The Distributor uses these additional resources on the server where it is located:</span></span>  
  
-   <span data-ttu-id="91f16-107">パブリケーションのスナップショット ファイルをディストリビューターに格納する場合 (通常の場合) は、そのためのディスク領域</span><span class="sxs-lookup"><span data-stu-id="91f16-107">Additional disk space if the snapshot files for the publication are stored on the Distributor (which they typically are).</span></span>  
  
-   <span data-ttu-id="91f16-108">ディストリビューション データベースを格納するためのディスク領域</span><span class="sxs-lookup"><span data-stu-id="91f16-108">Additional disk space to store the distribution database.</span></span>  
  
-   <span data-ttu-id="91f16-109">ディストリビューター上で実行されるプッシュ サブスクリプションのために、レプリケーション エージェントによって使用されるプロセッサ時間</span><span class="sxs-lookup"><span data-stu-id="91f16-109">Additional processor usage by replication agents for push subscriptions running on the Distributor.</span></span>  
  
 <span data-ttu-id="91f16-110">ディストリビューターとして指定するサーバーには、サーバー上でさまざまな機能を果たしながら、レプリケーションの処理を実行できるだけの十分なディスク容量とプロセッサ パワーが必要です。</span><span class="sxs-lookup"><span data-stu-id="91f16-110">The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server.</span></span> <span data-ttu-id="91f16-111">ディストリビューターを構成するには、以下の設定を行います。</span><span class="sxs-lookup"><span data-stu-id="91f16-111">When you configure the Distributor, you specify the following:</span></span>  
  
-   <span data-ttu-id="91f16-112">ディストリビューターを使用するすべてのパブリッシャーに対して既定で使用されるスナップショット フォルダー。</span><span class="sxs-lookup"><span data-stu-id="91f16-112">A snapshot folder, which is used, by default, for all Publishers that use this Distributor.</span></span> <span data-ttu-id="91f16-113">フォルダーが既に共有されていること、および適切な権限が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="91f16-113">Ensure that this folder is already shared and has the appropriate permissions set.</span></span> <span data-ttu-id="91f16-114">詳細については、「[Secure the Snapshot Folder](security/secure-the-snapshot-folder.md)」(スナップショット フォルダーのセキュリティ保護) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91f16-114">For more information, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  
-   <span data-ttu-id="91f16-115">ディストリビューション データベースの名前とファイルの場所。</span><span class="sxs-lookup"><span data-stu-id="91f16-115">A name and file locations for the distribution database.</span></span> <span data-ttu-id="91f16-116">ディストリビューション データベースの名前は、作成後には変更できません。</span><span class="sxs-lookup"><span data-stu-id="91f16-116">The distribution database cannot be renamed after it is created.</span></span> <span data-ttu-id="91f16-117">データベースで別の名前を使用するには、ディストリビューションを無効にして再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f16-117">To use a different name for the database, you must disable distribution and reconfigure it.</span></span>  
  
-   <span data-ttu-id="91f16-118">ディストリビューターの使用を許可するパブリッシャー。</span><span class="sxs-lookup"><span data-stu-id="91f16-118">Any Publishers authorized to use the Distributor.</span></span> <span data-ttu-id="91f16-119">ディストリビューターが実行されているインスタンス以外のパブリッシャーを指定する場合は、パブリッシャーがリモート ディストリビューターに接続するためのパスワードも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f16-119">If you specify Publishers other than the instance on which the Distributor runs, you must also specify a password for the connections the Publishers make to the remote Distributor.</span></span>  
  
 <span data-ttu-id="91f16-120">トランザクション レプリケーションでは、ディストリビューションの構成後に以下の作業を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="91f16-120">For transactional replication, after you configure distribution, we recommend that you:</span></span>  
  
-   <span data-ttu-id="91f16-121">ディストリビューション データベースのサイズを適切に設定する。</span><span class="sxs-lookup"><span data-stu-id="91f16-121">Size the distribution database appropriately.</span></span> <span data-ttu-id="91f16-122">システムの典型的な負荷でレプリケーションをテストし、コマンドを格納するために必要な領域を決定します。</span><span class="sxs-lookup"><span data-stu-id="91f16-122">Test replication with a typical load for your system to determine how much space is required to store commands.</span></span> <span data-ttu-id="91f16-123">データベースが頻繁に自動拡張しなくてもコマンドを格納できるだけの大きさを備えていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="91f16-123">Ensure the database is large enough to store commands without having to auto-grow frequently.</span></span> <span data-ttu-id="91f16-124">データベースのサイズの変更に関する詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f16-124">For more information about changing the size of a database, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="91f16-125">ディストリビューション データベースで " **sync with backup** " オプションを設定する。</span><span class="sxs-lookup"><span data-stu-id="91f16-125">Set the **sync with backup** option on the distribution database.</span></span> <span data-ttu-id="91f16-126">詳細については、「[スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)」と「[トランザクション レプリケーションの連携バックアップの有効化 &#40;レプリケーション Transact-SQL プログラミング&#41;](administration/enable-coordinated-backups-for-transactional-replication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91f16-126">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) and [Enable Coordinated Backups for Transactional Replication &#40;Replication Transact-SQL Programming&#41;](administration/enable-coordinated-backups-for-transactional-replication.md).</span></span>  
  
## <a name="local-and-remote-distributors"></a><span data-ttu-id="91f16-127">ローカル ディストリビューターとリモート ディストリビューター</span><span class="sxs-lookup"><span data-stu-id="91f16-127">Local and Remote Distributors</span></span>  
 <span data-ttu-id="91f16-128">既定では、ディストリビューターはパブリッシャーと同じサーバー (ローカル ディストリビューター) になりますが、別のサーバー (リモート ディストリビューター) にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="91f16-128">By default, the Distributor is the same server as the Publisher (a local Distributor), but it can also be a separate server from the Publisher (a remote Distributor).</span></span> <span data-ttu-id="91f16-129">一般に、リモート ディストリビューターは次のような場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="91f16-129">Typically, you would choose to use a remote Distributor if you want to:</span></span>  
  
-   <span data-ttu-id="91f16-130">処理を別のコンピューターにオフロードする場合 (たとえばパブリッシャーが OLTP サーバーである場合など、パブリッシャーに対するレプリケーションの影響を最小限に抑えたい場合)</span><span class="sxs-lookup"><span data-stu-id="91f16-130">Offload processing to another computer if you want minimal impact from replication on the Publisher (for example, if the Publisher is an OLTP server).</span></span>  
  
-   <span data-ttu-id="91f16-131">複数のパブリッシャーを集中管理する単一のディストリビューターを構成する場合</span><span class="sxs-lookup"><span data-stu-id="91f16-131">Configure a centralized Distributor for multiple Publishers.</span></span>  
  
 <span data-ttu-id="91f16-132">リモート ディストリビューターは、マージ レプリケーションよりトランザクション レプリケーションでよく使用されます。これには、次の 2 つの理由があります。</span><span class="sxs-lookup"><span data-stu-id="91f16-132">Remote Distributors are more common in transactional replication than they are in merge replication for two reasons:</span></span>  
  
-   <span data-ttu-id="91f16-133">トランザクション レプリケーションでは、レプリケートされたすべてのトランザクションの書き込みと読み取りがディストリビューション データベースに対して行われるため、ディストリビューターが果たす役割が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="91f16-133">The Distributor plays a larger role in transactional replication because all replicated transactions are written to and read from the distribution database.</span></span>  
  
-   <span data-ttu-id="91f16-134">マージ レプリケーション トポロジでは通常、プル サブスクリプションが使用されるため、ディストリビューターですべてのエージェントが実行されるのではなく、各サブスクライバーでエージェントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="91f16-134">Merge replication topologies typically use pull subscriptions, so agents run at each Subscriber, rather than all running at the Distributor.</span></span> <span data-ttu-id="91f16-135">詳細については、「[パブリケーションのサブスクライブ](subscribe-to-publications.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91f16-135">For more information, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="91f16-136">マージ レプリケーションでは、ほとんどの場合、ローカル ディストリビューターを使用します。</span><span class="sxs-lookup"><span data-stu-id="91f16-136">In most cases, you should use a local Distributor for merge replication.</span></span>  
  
 <span data-ttu-id="91f16-137">パブリッシングおよびディストリビューションを構成するには、「 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f16-137">To configure publishing and distribution, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  
  
 <span data-ttu-id="91f16-138">パブリッシャーとディストリビューターのプロパティを変更するには、「 [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f16-138">To modify Publisher and Distributor properties, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f16-139">参照</span><span class="sxs-lookup"><span data-stu-id="91f16-139">See Also</span></span>  
 <span data-ttu-id="91f16-140">[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="91f16-140">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="91f16-141">ディストリビューターのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="91f16-141">Secure the Distributor</span></span>](security/secure-the-distributor.md)  
  
  
