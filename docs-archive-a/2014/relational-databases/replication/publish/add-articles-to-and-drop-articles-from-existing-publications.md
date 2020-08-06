---
title: 既存のパブリケーションでのアーティクルの追加および削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- removing articles
- dropping articles
- adding articles
- administering replication, articles
- publications [SQL Server replication], adding and dropping articles
- articles [SQL Server replication], adding
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f72f15886e7105dde8d0e15dd0598a7474ed7e39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645525"
---
# <a name="add-articles-to-and-drop-articles-from-existing-publications"></a><span data-ttu-id="24c2c-102">既存のパブリケーションでのアーティクルの追加および削除</span><span class="sxs-lookup"><span data-stu-id="24c2c-102">Add Articles to and Drop Articles from Existing Publications</span></span>
  <span data-ttu-id="24c2c-103">パブリケーションを作成したら、アーティクルを追加および削除できます。</span><span class="sxs-lookup"><span data-stu-id="24c2c-103">After a publication is created, it is possible to add and drop articles.</span></span> <span data-ttu-id="24c2c-104">アーティクルはいつでも追加できますが、アーティクルを削除するために必要な操作は、レプリケーションの種類と、アーティクルを削除するタイミングによって異なります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-104">Articles can be added at any time, but the actions required for dropping articles depend on the type of replication and when the article is dropped.</span></span>  
  
## <a name="adding-articles"></a><span data-ttu-id="24c2c-105">アーティクルの追加</span><span class="sxs-lookup"><span data-stu-id="24c2c-105">Adding Articles</span></span>  
 <span data-ttu-id="24c2c-106">アーティクルを追加するには、アーティクルへのパブリケーションの追加、パブリケーションの新しいスナップショットの作成、サブスクリプションの同期による新しいアーティクルのスキーマとデータの適用を行います。</span><span class="sxs-lookup"><span data-stu-id="24c2c-106">Adding an article involves: adding the article to the publication; creating a new snapshot for the publication; synchronizing the subscription to apply the schema and data for the new article.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24c2c-107">マージ パブリケーションにアーティクルを追加する際に、その新しいアーティクルに既存のアーティクルが依存している場合は、[sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) および [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) の **\@processing_order** パラメーターを使用して、両方のアーティクルの処理順序を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-107">If you add an article to a merge publication and an existing article depends on the new article, you must specify a processing order for both articles using the **\@processing_order** parameter of [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) and [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="24c2c-108">たとえば、テーブルをパブリッシュし、テーブルが参照している関数はパブリッシュしない場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="24c2c-108">Consider the following scenario: you publish a table but you do not publish a function that the table references.</span></span> <span data-ttu-id="24c2c-109">この関数をパブリッシュしないと、サブスクライバー側でテーブルを作成できないとします。</span><span class="sxs-lookup"><span data-stu-id="24c2c-109">If you do not publish the function, the table cannot be created at the Subscriber.</span></span> <span data-ttu-id="24c2c-110">この場合は、この関数をパブリケーションに追加するときに、**sp_addmergearticle** の **\@processing_order** パラメーターに値 **1** を指定し、**sp_changemergearticle** の **\@processing_order** パラメーターに値 **2** を指定します。パラメーター **\@article** にはテーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="24c2c-110">When you add the function to the publication: specify a value of **1** for the **\@processing_order** parameter of **sp_addmergearticle**; and specify a value of **2** for the **\@processing_order** parameter of **sp_changemergearticle**, specifying the table name for the parameter **\@article**.</span></span> <span data-ttu-id="24c2c-111">この処理順序により、サブスクライバー側で関数に依存するテーブルを作成する前に、関数の作成が求められるようになります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-111">This processing order ensures that you create the function at the Subscriber before the table that depends on it.</span></span> <span data-ttu-id="24c2c-112">各アーティクルに使用する値は、関数の値がテーブルの値より小さければ、別の値でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="24c2c-112">You can use different numbers for each article, as long as the number for the function is lower than the number for the table.</span></span>  
  
1.  <span data-ttu-id="24c2c-113">次のいずれかの方法を使用して、1 つ以上のアーティクルを追加します。</span><span class="sxs-lookup"><span data-stu-id="24c2c-113">Add one or more articles through one of the following methods:</span></span>  
  
    -   [<span data-ttu-id="24c2c-114">パブリケーションでのアーティクルの追加または削除 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="24c2c-114">Add Articles to and Drop Articles from a Publication &#40;SQL Server Management Studio&#41;</span></span>](add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [<span data-ttu-id="24c2c-115">アーティクルの定義</span><span class="sxs-lookup"><span data-stu-id="24c2c-115">Define an Article</span></span>](define-an-article.md)  
  
2.  <span data-ttu-id="24c2c-116">パブリケーションにアーティクルを追加したら、パブリケーションの新しいスナップショット (およびパラメーター化されたフィルターを使用したマージ パブリケーションの場合は、すべてのパーティション) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-116">After adding an article to a publication, you must create a new snapshot for the publication (and all partitions if it is a merge publication with parameterized filters).</span></span> <span data-ttu-id="24c2c-117">その後、ディストリビューション エージェントまたはマージ エージェントによって、新しいアーティクルのスキーマおよびデータがサブスクライバーにコピーされます (パブリケーション全体が再初期化されるわけではありません)。</span><span class="sxs-lookup"><span data-stu-id="24c2c-117">The Distribution Agent or Merge Agent then copies the schema and data for the new article to the Subscriber (it does not reinitialize the entire publication).</span></span>  
  
    -   <span data-ttu-id="24c2c-118">新しいスナップショットを作成するには、「 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-118">To create a new snapshot, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
    -   <span data-ttu-id="24c2c-119">パラメーター化されたフィルターを使用してマージ パブリケーションに新しいスナップショットを作成するには、「[パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」 (パラメーター化されたフィルターを使用してマージ パブリケーションのスナップショットを作成する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-119">To create a new snapshot for a merge publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
3.  <span data-ttu-id="24c2c-120">スナップショットを作成したら、サブスクリプションを同期し、新しいアーティクルのスキーマおよびデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="24c2c-120">After the snapshot is created, synchronize the subscription to copy the schema and data for the new article.</span></span>  
  
    -   <span data-ttu-id="24c2c-121">プッシュ サブスクリプションを同期するには、「[Synchronize a Push Subscription](../synchronize-a-push-subscription.md)」 (プッシュ サブスクリプションの同期) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-121">To synchronize a push subscription, see [Synchronize a Push Subscription](../synchronize-a-push-subscription.md).</span></span>  
  
    -   <span data-ttu-id="24c2c-122">プル サブスクリプションを同期するには、「[Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md)」 (プル サブスクリプションの同期) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-122">To synchronize a pull subscription, see [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).</span></span>  
  
## <a name="dropping-articles"></a><span data-ttu-id="24c2c-123">アーティクルのドロップ</span><span class="sxs-lookup"><span data-stu-id="24c2c-123">Dropping Articles</span></span>  
 <span data-ttu-id="24c2c-124">アーティクルはパブリケーションからいつでも削除できます。ただし、次の動作について考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-124">Articles can be dropped from a publication at any time, but you must take into account the following behaviors:</span></span>  
  
-   <span data-ttu-id="24c2c-125">パブリケーションからアーティクルを削除しても、パブリケーション データベースからオブジェクトが削除されたり、サブスクリプション データベースから対応するオブジェクトが削除されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="24c2c-125">Dropping an article from a publication does not remove the object from the publication database or the corresponding object from the subscription database.</span></span> <span data-ttu-id="24c2c-126">必要に応じて、DROP \<Object> を使用し、これらのオブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="24c2c-126">Use DROP \<Object> to remove these objects if necessary.</span></span> <span data-ttu-id="24c2c-127">パブリッシュされた他のアーティクルに外部キー制約を通じて関連付けられているアーティクルを削除する場合は、手動で、またはオンデマンド スクリプトの実行により、サブスクライバーでテーブルを削除することをお勧めします。適切な DROP \<Object> ステートメントを含むスクリプトを指定してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-127">When you drop an article that is related to other published articles through foreign key constraints, we recommend that you drop the table at the Subscriber manually or by using on-demand script execution: specify a script that includes the appropriate DROP \<Object> statements.</span></span> <span data-ttu-id="24c2c-128">詳細については、「[同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング)](../execute-scripts-during-synchronization-replication-transact-sql-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-128">For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](../execute-scripts-during-synchronization-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="24c2c-129">互換性レベル 90RTM 以上のマージ パブリケーションの場合、アーティクルはいつでも削除できますが、新しいスナップショットが必要です。</span><span class="sxs-lookup"><span data-stu-id="24c2c-129">For merge publications with a compatibility level of 90RTM or higher, articles can be dropped at any time, but a new snapshot is required.</span></span> <span data-ttu-id="24c2c-130">追加として:</span><span class="sxs-lookup"><span data-stu-id="24c2c-130">Additionally:</span></span>  
  
    -   <span data-ttu-id="24c2c-131">アーティクルが結合フィルター リレーションシップまたは論理レコード リレーションシップの親アーティクルの場合、最初にリレーションシップの削除が必要ですが、これには再初期化が必要になります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-131">If an article is a parent article in a join filter or logical record relationship, the relationships must be dropped first, which requires reinitialization.</span></span>  
  
    -   <span data-ttu-id="24c2c-132">アーティクルにパブリケーションの最後のパラメーター化されたフィルターが含まれる場合、サブスクリプションを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-132">If an article has the last parameterized filter in a publication, subscriptions must be reinitialized.</span></span>  
  
-   <span data-ttu-id="24c2c-133">互換性レベルが 90RTM 未満のマージ パブリケーションの場合、アーティクルは特別な注意をせずに、サブスクリプションの初期同期の前に削除できます。</span><span class="sxs-lookup"><span data-stu-id="24c2c-133">For merge publications with a compatibility level lower than 90RTM, articles can be dropped with no special considerations prior to the initial synchronization of subscriptions.</span></span> <span data-ttu-id="24c2c-134">1 つ以上のサブスクリプションが同期された後にアーティクルが削除された場合、サブスクリプションの削除、再作成、および同期が必要です。</span><span class="sxs-lookup"><span data-stu-id="24c2c-134">If an article is dropped after one or more subscriptions is synchronized, the subscriptions must be dropped, re-created, and synchronized.</span></span>  
  
-   <span data-ttu-id="24c2c-135">スナップショット パブリケーションまたはトランザクション パブリケーションの場合、アーティクルはサブスクリプションを作成する前に、特別な事項を考慮せずに削除できます。</span><span class="sxs-lookup"><span data-stu-id="24c2c-135">For snapshot or transactional publications, articles can be dropped with no special considerations prior to subscriptions being created.</span></span> <span data-ttu-id="24c2c-136">1 つ以上のサブスクリプションが作成された後にアーティクルが削除された場合、サブスクリプションの削除、再作成、および同期が必要です。</span><span class="sxs-lookup"><span data-stu-id="24c2c-136">If an article is dropped after one or more subscriptions is created, the subscriptions must be dropped, recreated, and synchronized.</span></span> <span data-ttu-id="24c2c-137">サブスクリプションの削除の詳細については、「[パブリケーションのサブスクライブ](../subscribe-to-publications.md)」と「[sp_dropsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-137">For more information about dropping subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md) and [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="24c2c-138">**sp_dropsubscription** を使用すると、サブスクリプション全体ではなく、サブスクリプションの 1 つのアーティクルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="24c2c-138">**sp_dropsubscription** allows you to drop a single article from the subscription rather than the entire subscription.</span></span>  
  
1.  <span data-ttu-id="24c2c-139">パブリケーションからアーティクルを削除するには、アーティクルを削除し、パブリケーションの新しいスナップショットを作成します。</span><span class="sxs-lookup"><span data-stu-id="24c2c-139">Dropping an article from a publication involves dropping the article and creating a new snapshot for the publication.</span></span> <span data-ttu-id="24c2c-140">アーティクルを削除すると、現在のスナップショットは無効になります。したがって新しいスナップショットを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-140">Dropping an article invalidates the current snapshot; therefore a new snapshot must be created.</span></span>  
  
    -   <span data-ttu-id="24c2c-141">パブリケーションからアーティクルを削除するには、「[パブリケーションでのアーティクルの追加または削除 (SQL Server Management Studio)](add-articles-to-and-drop-articles-from-a-publication.md)」または「[Delete an Article](delete-an-article.md)」 (アーティクルの削除) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-141">To drop an article from a publication, see [Add Articles to and Drop Articles from a Publication &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) or [Delete an Article](delete-an-article.md).</span></span>  
  
2.  <span data-ttu-id="24c2c-142">パブリケーションからアーティクルを削除したら、パブリケーションの新しいスナップショット (およびパラメーター化されたフィルターを使用したマージ パブリケーションの場合は、すべてのパーティション) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-142">After dropping an article from a publication, you must create a new snapshot for the publication (and all partitions if it is a merge publication with parameterized filters).</span></span>  
  
    -   <span data-ttu-id="24c2c-143">新しいスナップショットを作成するには、「 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-143">To create a new snapshot, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
    -   <span data-ttu-id="24c2c-144">パラメーター化されたフィルターを使用してマージ パブリケーションに新しいスナップショットを作成するには、「[パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」 (パラメーター化されたフィルターを使用してマージ パブリケーションのスナップショットを作成する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-144">To create a new snapshot for a merge publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
 <span data-ttu-id="24c2c-145">前述のように、場合によっては、アーティクルを削除するために、サブスクリプションの削除、再作成、および同期が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="24c2c-145">As noted above, in some cases dropping an article requires subscriptions to be dropped, recreated, and then synchronized.</span></span> <span data-ttu-id="24c2c-146">詳細については、「[パブリケーションのサブスクライブ](../subscribe-to-publications.md)」と「[データの同期](../synchronize-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c2c-146">For more information, see [Subscribe to Publications](../subscribe-to-publications.md) and [Synchronize Data](../synchronize-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c2c-147">参照</span><span class="sxs-lookup"><span data-stu-id="24c2c-147">See Also</span></span>  
 <span data-ttu-id="24c2c-148">[データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="24c2c-148">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="24c2c-149">[サブスクリプションの再初期化](../reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="24c2c-149">[Reinitialize Subscriptions](../reinitialize-subscriptions.md) </span></span>  
 [<span data-ttu-id="24c2c-150">パブリケーション データベースでのスキーマの変更</span><span class="sxs-lookup"><span data-stu-id="24c2c-150">Make Schema Changes on Publication Databases</span></span>](make-schema-changes-on-publication-databases.md)  
  
  
