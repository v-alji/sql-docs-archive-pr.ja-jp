---
title: サブスクリプションの再初期化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bf9c68f66a32d1a5ddcf08b845396f815385e83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741762"
---
# <a name="reinitialize-subscriptions"></a><span data-ttu-id="b9c43-102">サブスクリプションの再初期化</span><span class="sxs-lookup"><span data-stu-id="b9c43-102">Reinitialize Subscriptions</span></span>
  <span data-ttu-id="b9c43-103">サブスクリプションの再初期化では、1 つ以上のサブスクライバーに 1 つ以上のアーティクルの新しいスナップショットが適用されます。トランザクション レプリケーションとスナップショット レプリケーションでは個々のアーティクルを再初期化できますが、マージ レプリケーションではすべてのアーティクルを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9c43-103">Reinitializing a subscription involves applying a new snapshot of one or more articles to one or more Subscribers: transactional and snapshot replication allow individual articles to be reinitialized; merge replication requires all articles to be reinitialized.</span></span> <span data-ttu-id="b9c43-104">ピア ツー ピア トランザクション レプリケーション トポロジのノードは再初期化できません。</span><span class="sxs-lookup"><span data-stu-id="b9c43-104">Nodes in a peer-to-peer transactional replication topology cannot be reinitialized.</span></span> <span data-ttu-id="b9c43-105">ノードが新しいデータのコピーを確実に保持する必要がある場合は、そのノードでバックアップを復元してください。</span><span class="sxs-lookup"><span data-stu-id="b9c43-105">If you need to ensure a node has a new copy of the data, restore a backup at the node.</span></span> <span data-ttu-id="b9c43-106">再初期化は、以下の 2 つの場合に行われます。</span><span class="sxs-lookup"><span data-stu-id="b9c43-106">Reinitialization occurs for one of two reasons:</span></span>  
  
-   <span data-ttu-id="b9c43-107">サブスクリプションを再初期化するように明示的にマークした場合。</span><span class="sxs-lookup"><span data-stu-id="b9c43-107">You explicitly mark a subscription for reinitialization.</span></span>  
  
-   <span data-ttu-id="b9c43-108">プロパティの変更など、再初期化を必要とする操作を実行した場合。</span><span class="sxs-lookup"><span data-stu-id="b9c43-108">You perform an action, such as a property change, that requires a reinitialization.</span></span> <span data-ttu-id="b9c43-109">再初期化が必要な操作の詳細については、「[Change Publication and Article Properties](publish/change-publication-and-article-properties.md)」 (パブリケーションおよびアーティクルのプロパティの変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9c43-109">For more information about actions that require reinitialization, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="b9c43-110">いずれの場合も、ディストリビューション エージェントまたはマージ エージェントが次に実行されたときに、最新のスナップショットがサブスクライバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b9c43-110">In both cases, the most recent snapshot is applied to the Subscriber the next time the Distribution Agent or the Merge Agent runs.</span></span> <span data-ttu-id="b9c43-111">スナップショット レプリケーションとトランザクション レプリケーションの場合は、再初期化が行われると、サブスクライバーで行われた変更 (まだパブリッシャーと同期されていない変更) は新しいスナップショットの適用によって上書きされます。</span><span class="sxs-lookup"><span data-stu-id="b9c43-111">For snapshot and transactional replication, when reinitialization occurs, any changes made at the Subscriber, but not yet synchronized with the Publisher, are overwritten by the application of the new snapshot.</span></span>  
  
 <span data-ttu-id="b9c43-112">マージ レプリケーションの場合は、スナップショットを適用する前にすべてのデータ変更をサブスクライバーからアップロードするように選択することができます。</span><span class="sxs-lookup"><span data-stu-id="b9c43-112">For merge replication, you can choose to have all the data changes uploaded from the Subscriber before the snapshot is applied.</span></span> <span data-ttu-id="b9c43-113">スナップショットが再適用される前に、パブリッシャーの保留中のスキーマ変更がサブスクライバーに適用され、前回の同期以降にサブスクライバーで行われた更新がパブリッシャーに反映されます。</span><span class="sxs-lookup"><span data-stu-id="b9c43-113">Any pending schema changes from the Publisher are applied at the Subscriber, and then any updates that have been made at the Subscriber since the last synchronization are propagated to the Publisher before the snapshot is reapplied.</span></span> <span data-ttu-id="b9c43-114">この動作は、 **upload_first** プロパティと **automatic_reinitialization_policy** プロパティによって制御されます。詳細については、「 [Reinitialize a Subscription](reinitialize-a-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9c43-114">This behavior is controlled by the **upload_first** and **automatic_reinitialization_policy** properties; for more information, see [Reinitialize a Subscription](reinitialize-a-subscription.md).</span></span> <span data-ttu-id="b9c43-115">SQL Server Management Studio またはレプリケーション モニターを使用してサブスクリプションを再初期化するようにマークする場合は、 **[サブスクリプションの再初期化]** ダイアログ ボックスのオプションで、先に変更をアップロードするかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b9c43-115">If you mark a subscription for reinitialization using SQL Server Management Studio or Replication Monitor, you are given an option in the **Reinitialize Subscription(s)** dialog box to upload changes first.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b9c43-116">マージ パブリケーションのパラメーター化されたフィルターを追加、削除、変更する場合は、再初期化の際にサブスクライバーで保留中の変更をパブリッシャーにアップロードできません。</span><span class="sxs-lookup"><span data-stu-id="b9c43-116">If you add, drop, or change a parameterized filter in a merge publication, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="b9c43-117">保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。</span><span class="sxs-lookup"><span data-stu-id="b9c43-117">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
 <span data-ttu-id="b9c43-118">サブスクリプションを作成するとき、初期スナップショットをサブスクライバーに適用しないように指定した場合、作成されたサブスクリプションを再初期化するようにマークしても、スナップショットは適用されません。</span><span class="sxs-lookup"><span data-stu-id="b9c43-118">If, you specified that no initial snapshot was to be applied to the Subscriber when you created the subscription, and you then mark the subscription for reinitialization, a snapshot is not applied.</span></span> <span data-ttu-id="b9c43-119">詳細については、「 [スナップショットを使用しないトランザクション サブスクリプションの初期化](initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c43-119">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
 <span data-ttu-id="b9c43-120">**サブスクリプションを再初期化するには**</span><span class="sxs-lookup"><span data-stu-id="b9c43-120">**To reinitialize a subscription**</span></span>  
  
 <span data-ttu-id="b9c43-121">サブスクリプションのすべてのアーティクルを再初期化するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、ストアド プロシージャ、またはレプリケーション管理オブジェクト (RMO) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9c43-121">To reinitialize all articles in a subscription, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], stored procedures or Replication Management Objects (RMO).</span></span> <span data-ttu-id="b9c43-122">スナップショット パブリケーションおよびトランザクション パブリケーションの個々のアーティクルを再初期化するには、ストアド プロシージャを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9c43-122">To reinitialize individual articles in snapshot and transactional publications, you must use stored procedures.</span></span> <span data-ttu-id="b9c43-123">詳細については、「 [Reinitialize a Subscription](reinitialize-a-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b9c43-123">For more information, see [Reinitialize a Subscription](reinitialize-a-subscription.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c43-124">参照</span><span class="sxs-lookup"><span data-stu-id="b9c43-124">See Also</span></span>  
 <span data-ttu-id="b9c43-125">[サブスクリプションの初期化](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="b9c43-125">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="b9c43-126">サブスクリプションの有効期限と非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="b9c43-126">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
