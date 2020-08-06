---
title: フルテキスト カタログの作成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18efd79bc34beee94d4edc61e9165a986edba90b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645479"
---
# <a name="create-and-manage-full-text-catalogs"></a><span data-ttu-id="9de14-102">フルテキスト カタログの作成と管理</span><span class="sxs-lookup"><span data-stu-id="9de14-102">Create and Manage Full-Text Catalogs</span></span>
  <span data-ttu-id="9de14-103">フルテキスト カタログが、ファイル グループに属さない仮想オブジェクトとなりました。これは、フルテキスト インデックスのグループを指す論理的概念です。</span><span class="sxs-lookup"><span data-stu-id="9de14-103">A full-text catalog is a virtual object that does not belong to any filegroup; it is a logical concept that refers to a group of full-text indexes.</span></span>  
  
##  <a name="creating-a-full-text-catalog"></a><a name="creating"></a><span data-ttu-id="9de14-104">フルテキストカタログの作成</span><span class="sxs-lookup"><span data-stu-id="9de14-104">Creating a Full-Text Catalog</span></span>  
  
#### <a name="to-create-a-full-text-catalog"></a><span data-ttu-id="9de14-105">フルテキスト カタログを作成するには</span><span class="sxs-lookup"><span data-stu-id="9de14-105">To create a full-text catalog</span></span>  
  
1.  <span data-ttu-id="9de14-106">オブジェクト エクスプローラーで、サーバーを展開し、 **[データベース]** を展開して、フルテキスト カタログを作成する対象のデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="9de14-106">In Object Explorer, expand the server, expand **Databases**, and expand the database in which you want to create the full-text catalog.</span></span>  
  
2.  <span data-ttu-id="9de14-107">**[ストレージ]** を展開し、 **[フルテキスト カタログ]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="9de14-107">Expand **Storage**, and then right-click **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="9de14-108">**[新しいフルテキスト カタログ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9de14-108">Select **New Full-Text Catalog**.</span></span>  
  
4.  <span data-ttu-id="9de14-109">**[新しいフルテキスト カタログ]** ダイアログ ボックスで、再作成するカタログの情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="9de14-109">In the **New Full-Text Catalog** dialog box, specify the information for the catalog that you are re-creating.</span></span> <span data-ttu-id="9de14-110">詳細については、「[[新しいフルテキスト カタログ] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9de14-110">For more information, see [New Full-Text Catalog &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9de14-111">フルテキスト カタログ ID は、00005 から始まり、新しいカタログが作成されるたびに 1 ずつ増加します。</span><span class="sxs-lookup"><span data-stu-id="9de14-111">Full-text catalog IDs begin at 00005 and are incremented by one for each new catalog created.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
##  <a name="viewing-the-properties-of-a-full-text-catalog"></a><a name="props"></a><span data-ttu-id="9de14-112">フルテキストカタログのプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="9de14-112">Viewing the Properties of a Full-Text Catalog</span></span>  
 <span data-ttu-id="9de14-113">FULLTEXTCATALOGPROPERTY などの [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数は、フルテキスト インデックスに関連するさまざまなプロパティの値を取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9de14-113">[!INCLUDE[tsql](../../includes/tsql-md.md)] functions such as FULLTEXTCATALOGPROPERTY can be used to obtain the value of various properties related to full-text indexing.</span></span> <span data-ttu-id="9de14-114">この情報は、フルテキスト検索の管理およびトラブルシューティングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9de14-114">This information is useful for administering and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="9de14-115">次の表は、フルテキスト カタログに関連しているプロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="9de14-115">The following table lists the properties that are related to full-text catalogs.</span></span>  
  
|<span data-ttu-id="9de14-116">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9de14-116">Property</span></span>|<span data-ttu-id="9de14-117">説明</span><span class="sxs-lookup"><span data-stu-id="9de14-117">Description</span></span>|<span data-ttu-id="9de14-118">機能</span><span class="sxs-lookup"><span data-stu-id="9de14-118">Function</span></span>|  
|--------------|-----------------|--------------|  
|`AccentSensitivity`|<span data-ttu-id="9de14-119">アクセントの区別の設定。</span><span class="sxs-lookup"><span data-stu-id="9de14-119">Accent-sensitivity setting.</span></span>|[<span data-ttu-id="9de14-120">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="9de14-120">FULLTEXTCATALOGPROPERTY</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|  
|`ImportStatus`|<span data-ttu-id="9de14-121">フルテキスト カタログがインポートされているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9de14-121">Whether the full-text catalog is being imported.</span></span>|<span data-ttu-id="9de14-122">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="9de14-122">FULLTEXTCATALOGPROPERTY</span></span>|  
|`IndexSize`|<span data-ttu-id="9de14-123">フルテキスト カタログのサイズ (MB 単位)。</span><span class="sxs-lookup"><span data-stu-id="9de14-123">Size of the full-text catalog in megabytes (MB).</span></span>|<span data-ttu-id="9de14-124">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="9de14-124">FULLTEXTCATALOGPROPERTY</span></span>|  
|`ItemCount`|<span data-ttu-id="9de14-125">現在フルテキスト カタログ内にあるフルテキスト インデックス項目の数。</span><span class="sxs-lookup"><span data-stu-id="9de14-125">Number of full-text indexed items currently in the full-text catalog.</span></span>|<span data-ttu-id="9de14-126">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="9de14-126">FULLTEXTCATALOGPROPERTY</span></span>|  
|`MergeStatus`|<span data-ttu-id="9de14-127">マスター マージの実行状況を示します。</span><span class="sxs-lookup"><span data-stu-id="9de14-127">Whether a master merge is in progress.</span></span>|<span data-ttu-id="9de14-128">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="9de14-128">FULLTEXTCATALOGPROPERTY</span></span>|  
|`PopulateCompletionAge`|<span data-ttu-id="9de14-129">01/01/1990 00:00:00 から、最後のフルテキスト インデックス作成が完了した時刻までの時間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="9de14-129">Difference in seconds between the completion of the last full-text index population and 01/01/1990 00:00:00.</span></span>|<span data-ttu-id="9de14-130">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="9de14-130">FULLTEXTCATALOGPROPERTY</span></span>|  
|`PopulateStatus`|<span data-ttu-id="9de14-131">作成状態。</span><span class="sxs-lookup"><span data-stu-id="9de14-131">Populate status.</span></span><br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|<span data-ttu-id="9de14-132">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="9de14-132">FULLTEXTCATALOGPROPERTY</span></span>|  
|`UniqueKeyCount`|<span data-ttu-id="9de14-133">フルテキスト カタログ内にある一意のキーの数。</span><span class="sxs-lookup"><span data-stu-id="9de14-133">Number of unique keys in the full-text catalog.</span></span>|<span data-ttu-id="9de14-134">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="9de14-134">FULLTEXTCATALOGPROPERTY</span></span>|  
  
  
  
##  <a name="rebuilding-a-full-text-catalog"></a><a name="rebuildone"></a><span data-ttu-id="9de14-135">フルテキストカタログの再構築</span><span class="sxs-lookup"><span data-stu-id="9de14-135">Rebuilding a Full-Text Catalog</span></span>  
  
#### <a name="to-rebuild-a-full-text-catalog"></a><span data-ttu-id="9de14-136">フルテキスト カタログを再構築するには</span><span class="sxs-lookup"><span data-stu-id="9de14-136">To rebuild a full-text catalog</span></span>  
  
1.  <span data-ttu-id="9de14-137">オブジェクト エクスプローラーで、サーバーを展開し、 **[データベース]** を展開して、再構築するフルテキスト カタログが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="9de14-137">In Object Explorer, expand the server, expand **Databases**, and then expand the database that contains the full-text catalog that you want to rebuild.</span></span>  
  
2.  <span data-ttu-id="9de14-138">**[ストレージ]** を展開し、 **[フルテキスト カタログ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9de14-138">Expand **Storage**, and then expand **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="9de14-139">再構築するフルテキスト カタログの名前を右クリックし、 **[再構築]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9de14-139">Right-click the name of the full-text catalog that you want to rebuild, and select **Rebuild**.</span></span>  
  
4.  <span data-ttu-id="9de14-140">**"フルテキスト カタログを削除して再構築しますか?"** という確認メッセージが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9de14-140">To the question **Do you want to delete the full-text catalog and rebuild it?**, click **OK**.</span></span>  
  
5.  <span data-ttu-id="9de14-141">**[フルテキスト カタログの再構築]** ダイアログ ボックスで、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9de14-141">In the **Rebuild Full-Text Catalog** dialog box, click **Close**.</span></span>  
  
  
  
##  <a name="rebuilding-all-full-text-catalogs-for-a-database"></a><a name="rebuildall"></a><span data-ttu-id="9de14-142">データベースのすべてのフルテキストカタログの再構築</span><span class="sxs-lookup"><span data-stu-id="9de14-142">Rebuilding All Full-Text Catalogs for a Database</span></span>  
  
#### <a name="to-rebuild-the-full-text-catalogs-for-a-database"></a><span data-ttu-id="9de14-143">データベースのフルテキスト カタログを再構築するには</span><span class="sxs-lookup"><span data-stu-id="9de14-143">To rebuild the full-text catalogs for a database</span></span>  
  
1.  <span data-ttu-id="9de14-144">オブジェクト エクスプローラーで、サーバーを展開し、 **[データベース]** を展開して、再構築するフルテキスト カタログが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="9de14-144">In Object Explorer, expand the server, expand **Databases**, and then expand the database that contains the full-text catalogs that you want to rebuild.</span></span>  
  
2.  <span data-ttu-id="9de14-145">**[ストレージ]** を展開し、 **[フルテキスト カタログ]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="9de14-145">Expand **Storage**, and then right-click **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="9de14-146">**[すべて再構築]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9de14-146">Select **Rebuild All**.</span></span>  
  
4.  <span data-ttu-id="9de14-147">**[すべてのフルテキスト カタログを削除して再構築しますか?]** という確認メッセージが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9de14-147">To the question, **Do you want to delete all full-text catalogs and rebuild them?**, click **OK**.</span></span>  
  
5.  <span data-ttu-id="9de14-148">**[すべてのフルテキスト カタログの再構築]** ダイアログ ボックスで、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9de14-148">In the **Rebuild All Full-Text Catalogs** dialog box, click **Close**.</span></span>  
  
  
  
##  <a name="removing-a-full-text-catalog-from-a-database"></a><a name="removing"></a><span data-ttu-id="9de14-149">データベースからのフルテキストカタログの削除</span><span class="sxs-lookup"><span data-stu-id="9de14-149">Removing a Full-Text Catalog from a Database</span></span>  
  
#### <a name="to-remove-a-full-text-catalog-from-a-database"></a><span data-ttu-id="9de14-150">データベースからフルテキスト カタログを削除するには</span><span class="sxs-lookup"><span data-stu-id="9de14-150">To remove a full-text catalog from a database</span></span>  
  
1.  <span data-ttu-id="9de14-151">オブジェクト エクスプローラーで、サーバーを展開し、 **[データベース]** を展開して、削除するフルテキスト カタログを含むデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="9de14-151">In Object Explorer, expand the server, expand **Databases**, and expand the database that contains the full-text catalog you want to remove.</span></span>  
  
2.  <span data-ttu-id="9de14-152">**[ストレージ]** を展開し、 **[フルテキスト カタログ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9de14-152">Expand **Storage**, and expand **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="9de14-153">削除するフルテキスト カタログを右クリックし、 **[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9de14-153">Right-click the full-text catalog that you want to remove, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="9de14-154">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9de14-154">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="9de14-155">参照</span><span class="sxs-lookup"><span data-stu-id="9de14-155">See Also</span></span>  
 [<span data-ttu-id="9de14-156">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9de14-156">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  
