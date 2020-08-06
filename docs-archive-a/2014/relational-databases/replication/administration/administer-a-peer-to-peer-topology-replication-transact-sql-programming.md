---
title: ピア ツー ピア トポロジの管理 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, peer-to-peer replication
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a73af1c1f3a7196d87f77681ee9d62a3ef248a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634424"
---
# <a name="administer-a-peer-to-peer-topology-replication-transact-sql-programming"></a><span data-ttu-id="e214b-102">ピア ツー ピア トポロジの管理 (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="e214b-102">Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="e214b-103">ピア ツー ピア トポロジの管理は通常のトランザクション レプリケーション トポロジの管理と似ていますが、特別な考慮が必要な部分が数多くあります。</span><span class="sxs-lookup"><span data-stu-id="e214b-103">Administering a peer-to-peer topology is similar to administering a typical transactional replication topology, but there are a number of areas with special considerations.</span></span> <span data-ttu-id="e214b-104">ピア ツー ピア トポロジの管理が通常のトポロジ管理と最も異なる点は、ある種の変更を行うときにシステムを *停止*する必要があることです。</span><span class="sxs-lookup"><span data-stu-id="e214b-104">The principal difference in administering a peer-to-peer topology is that some changes require the system to be *quiesced*.</span></span> <span data-ttu-id="e214b-105">システムを停止するときには、すべてのノードでパブリッシュ済みテーブルの利用を停止し、各ノードが他のすべてのノードの変更を受け取っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e214b-105">Quiescing a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes.</span></span> <span data-ttu-id="e214b-106">詳細については、「[レプリケーション トポロジの停止 &#40;レプリケーション Transact-SQL プログラミング&#41;](quiesce-a-replication-topology-replication-transact-sql-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e214b-106">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e214b-107">ピア ツー ピア トポロジでは、ディストリビューターはプル サブスクライバーより前の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンを使用できません。</span><span class="sxs-lookup"><span data-stu-id="e214b-107">In a peer-to-peer topology, the distributor cannot be using an earlier version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] than a pull subscriber.</span></span>  
  
### <a name="to-add-an-article-to-an-existing-configuration"></a><span data-ttu-id="e214b-108">既存の構成にアーティクルを追加するには</span><span class="sxs-lookup"><span data-stu-id="e214b-108">To add an article to an existing configuration</span></span>  
  
1.  <span data-ttu-id="e214b-109">システムを停止します。</span><span class="sxs-lookup"><span data-stu-id="e214b-109">Quiesce the system.</span></span>  
  
2.  <span data-ttu-id="e214b-110">トポロジ内の各ノードでディストリビューション エージェントを停止します。</span><span class="sxs-lookup"><span data-stu-id="e214b-110">Stop the Distribution Agent at each node in the topology.</span></span> <span data-ttu-id="e214b-111">詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e214b-111">For more information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
3.  <span data-ttu-id="e214b-112">CREATE TABLE ステートメントを実行して、トポロジ内の各ノードに新しいテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="e214b-112">Execute the CREATE TABLE statement to add the new table at each node in the topology.</span></span>  
  
4.  <span data-ttu-id="e214b-113">[bcp ユーティリティ](../../../tools/bcp-utility.md)を使用して、全ノードの新しいテーブルにデータを一括コピーします。</span><span class="sxs-lookup"><span data-stu-id="e214b-113">Bulk copy the data for the new table manually at all nodes by using the [bcp utility](../../../tools/bcp-utility.md).</span></span>  
  
5.  <span data-ttu-id="e214b-114">[sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) を実行して、トポロジ内の各ノードに新しいアーティクルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e214b-114">Execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) to create the new article at each node in the topology.</span></span> <span data-ttu-id="e214b-115">詳しくは、「 [アーティクルを定義](../publish/define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e214b-115">For more information, see [Define an Article](../publish/define-an-article.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e214b-116">[sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) の実行後、レプリケーションによってトポロジ内のサブスクリプションにアーティクルが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e214b-116">After [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) is executed, replication automatically adds the article to the subscriptions in the topology.</span></span>  
  
6.  <span data-ttu-id="e214b-117">トポロジ内の各ノードでディストリビューション エージェントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="e214b-117">Restart the Distribution Agents at each node in the topology.</span></span>  
  
### <a name="to-make-schema-changes-to-a-publication-database"></a><span data-ttu-id="e214b-118">パブリケーション データベースのスキーマを変更するには</span><span class="sxs-lookup"><span data-stu-id="e214b-118">To make schema changes to a publication database</span></span>  
  
1.  <span data-ttu-id="e214b-119">システムを停止します。</span><span class="sxs-lookup"><span data-stu-id="e214b-119">Quiesce the system.</span></span>  
  
2.  <span data-ttu-id="e214b-120">データ定義言語 (DDL) ステートメントを実行して、パブリッシュ済みテーブルのスキーマを変更します。</span><span class="sxs-lookup"><span data-stu-id="e214b-120">Execute the data definition language (DDL) statements to modify the schema of published tables.</span></span> <span data-ttu-id="e214b-121">サポートされるスキーマ変更の詳細については、「[パブリケーション データベースでのスキーマの変更](../publish/make-schema-changes-on-publication-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e214b-121">For more information about supported schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
3.  <span data-ttu-id="e214b-122">パブリッシュ済みテーブルの利用を再開する前に、再びシステムを停止します。</span><span class="sxs-lookup"><span data-stu-id="e214b-122">Before you resume activity on published tables, quiesce the system again.</span></span> <span data-ttu-id="e214b-123">これにより、新しいデータ変更がレプリケートされる前に、すべてのノードでスキーマ変更が受け取られます。</span><span class="sxs-lookup"><span data-stu-id="e214b-123">This ensures that schema changes have been received by all nodes before any new data changes are replicated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e214b-124">例</span><span class="sxs-lookup"><span data-stu-id="e214b-124">Example</span></span>  
 <span data-ttu-id="e214b-125">次の例は、2 つのノードを持つ既存のピア ツー ピア レプリケーション トポロジに新しいテーブル アーティクルを追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e214b-125">The following example demonstrates how to add a new table article to an existing peer-to-peer replication topology that has two nodes.</span></span>  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createtables)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_cmdline)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createarticle)]  
  
## <a name="see-also"></a><span data-ttu-id="e214b-126">参照</span><span class="sxs-lookup"><span data-stu-id="e214b-126">See Also</span></span>  
 <span data-ttu-id="e214b-127">[レプリケーション管理に関する FAQ](frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="e214b-127">[Replication Administration FAQ](frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="e214b-128">[SQL Server データベースのバックアップと復元](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="e214b-128">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="e214b-129">ピア ツー ピア トランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="e214b-129">Peer-to-Peer Transactional Replication</span></span>](../transactional/peer-to-peer-transactional-replication.md)  
  
  
