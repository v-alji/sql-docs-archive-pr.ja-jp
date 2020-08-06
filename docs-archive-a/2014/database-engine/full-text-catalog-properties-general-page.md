---
title: '[フルテキストカタログのプロパティ] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
author: rothja
ms.author: jroth
ms.openlocfilehash: 483601c53db6c8a806ea8c53f771fd4f2608293b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740302"
---
# <a name="full-text-catalog-properties-general-page"></a><span data-ttu-id="ec1c2-102">[フルテキスト カタログのプロパティ] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="ec1c2-102">Full-Text Catalog Properties (General Page)</span></span>
  <span data-ttu-id="ec1c2-103">ここでは、 **[フルテキスト カタログのプロパティ]** ダイアログ ボックスの **[全般]** ページに表示されるオプションと機能を示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-103">This section shows the options and functions available on the **General** page of the **Full-Text Catalog Properties** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec1c2-104">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] データベースでは、フルテキスト カタログは、フルテキスト インデックスのグループを指す論理的概念です。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-104">For [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] databases, a full-text catalog is a logical concept that refers to a group of full-text indexes.</span></span> <span data-ttu-id="ec1c2-105">フルテキスト カタログは、ファイル グループに属さない仮想オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-105">The full-text catalog is a virtual object that does not belong to any filegroup.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ec1c2-106">Options</span><span class="sxs-lookup"><span data-stu-id="ec1c2-106">Options</span></span>  
  
### <a name="properties"></a><span data-ttu-id="ec1c2-107">Properties</span><span class="sxs-lookup"><span data-stu-id="ec1c2-107">Properties</span></span>  
 <span data-ttu-id="ec1c2-108">**[既定のカタログ]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-108">**Default Catalog**</span></span>  
 <span data-ttu-id="ec1c2-109">カタログがデータベースの既定のカタログかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-109">Displays whether the catalog is the default catalog for the database.</span></span>  
  
 <span data-ttu-id="ec1c2-110">**[作成の状態]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-110">**Population Status**</span></span>  
 <span data-ttu-id="ec1c2-111">カタログの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-111">Indicates the status of the catalog.</span></span> <span data-ttu-id="ec1c2-112">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-112">Possible values are:</span></span>  
  
-   <span data-ttu-id="ec1c2-113">**アイドル**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-113">**Idle**</span></span>  
  
-   <span data-ttu-id="ec1c2-114">**[クロール中]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-114">**Crawl in Progress**</span></span>  
  
-   <span data-ttu-id="ec1c2-115">**一時停止**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-115">**Paused**</span></span>  
  
-   <span data-ttu-id="ec1c2-116">**Throttled**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-116">**Throttled**</span></span>  
  
-   <span data-ttu-id="ec1c2-117">**際**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-117">**Recovering**</span></span>  
  
-   <span data-ttu-id="ec1c2-118">**シャットダウン**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-118">**Shutdown**</span></span>  
  
-   <span data-ttu-id="ec1c2-119">**[カタログを増分作成しています]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-119">**Incremental population in progress**</span></span>  
  
-   <span data-ttu-id="ec1c2-120">**[カタログ作成の最後のステップを実行しています]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-120">**Building index**</span></span>  
  
-   <span data-ttu-id="ec1c2-121">**ディスクが完全に一時停止しています**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-121">**Disk is full-Paused**</span></span>  
  
-   <span data-ttu-id="ec1c2-122">**Change tracking**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-122">**Change tracking**</span></span>  
  
 <span data-ttu-id="ec1c2-123">**項目数**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-123">**Item Count**</span></span>  
 <span data-ttu-id="ec1c2-124">カタログ内のフルテキスト項目の数を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-124">Displays the number of full-text items in the catalog.</span></span>  
  
 <span data-ttu-id="ec1c2-125">**[カタログ サイズ]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-125">**Catalog Size**</span></span>  
 <span data-ttu-id="ec1c2-126">フルテキスト カタログのサイズ (MB) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-126">Displays the size, in megabytes, of the full-text catalog.</span></span>  
  
 <span data-ttu-id="ec1c2-127">**名前**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-127">**Name**</span></span>  
 <span data-ttu-id="ec1c2-128">フルテキスト カタログの名前です。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-128">The name of the full-text catalog.</span></span>  
  
 <span data-ttu-id="ec1c2-129">**[アクセントを区別する]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-129">**Accent Sensitive**</span></span>  
 <span data-ttu-id="ec1c2-130">チルダ ( **~** )、アキュートアクセント記号 (**́**)、ウムラウト (**ィ**) などの、カタログが分音記号によって区別されるかどうかを表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-130">View or modify whether the catalog is sensitive to diacritical marks, such as a tilde (**~**), acute accent mark (**´**), or umlaut (**¨**).</span></span> <span data-ttu-id="ec1c2-131">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-131">Valid values are:</span></span>  
  
-   <span data-ttu-id="ec1c2-132">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-132">**No**</span></span>  
  
-   <span data-ttu-id="ec1c2-133">**はい**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-133">**Yes**</span></span>  
  
-   <span data-ttu-id="ec1c2-134">分音記号の詳細につい[ては、「」](https://www.merriam-webster.com/dictionary/diacritic)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-134">For information about diacritical marks, see [Diacritic](https://www.merriam-webster.com/dictionary/diacritic) in the Merriam-Webster dictionary.</span></span>  
  
 <span data-ttu-id="ec1c2-135">**[最終作成日付]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-135">**Last Population Date**</span></span>  
 <span data-ttu-id="ec1c2-136">そのカタログの最後に作成された日付を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-136">Displays the date the catalog was last populated.</span></span>  
  
 <span data-ttu-id="ec1c2-137">**所有者**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-137">**Owner**</span></span>  
 <span data-ttu-id="ec1c2-138">フルテキスト カタログの所有者です。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-138">The owner of the full-text catalog.</span></span>  
  
 <span data-ttu-id="ec1c2-139">**[一意なキー数]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-139">**Unique Key Count**</span></span>  
 <span data-ttu-id="ec1c2-140">このカタログの中でフルテキスト インデックスを構成している一意な文字列の個数です。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-140">The number of unique words that make up the full-text index for the catalog.</span></span>  
  
### <a name="catalog-action"></a><span data-ttu-id="ec1c2-141">カタログ アクション</span><span class="sxs-lookup"><span data-stu-id="ec1c2-141">Catalog Action</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec1c2-142">**なし**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-142">**None**</span></span>|<span data-ttu-id="ec1c2-143">**[カタログを最適化する]**、 **[カタログを再構築する]**、または **[カタログを再作成する]** の操作を実行しません。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-143">Does not perform **Optimize catalog**, **Rebuild catalog**, or **Repopulate catalog** operations.</span></span>|  
|<span data-ttu-id="ec1c2-144">**[カタログを最適化する]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-144">**Optimize catalog**</span></span>|<span data-ttu-id="ec1c2-145">カタログの使用効率を最適化し、クエリ パフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-145">Optimizes the space utilization of the catalog and improves query performance.</span></span> <span data-ttu-id="ec1c2-146">また、検索結果の関連順位の正確さを向上させます。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-146">It also improves the accuracy of relevance ranking of search results.</span></span><br /><br /> <span data-ttu-id="ec1c2-147">このアクションでは、ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-147">This action executes ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE.</span></span>|  
|<span data-ttu-id="ec1c2-148">**[カタログを再構築する]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-148">**Rebuild catalog**</span></span>|<span data-ttu-id="ec1c2-149">フルテキスト カタログを削除して再構築します。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-149">Deletes and rebuilds the full-text catalog.</span></span> <span data-ttu-id="ec1c2-150">アクセントの区別など基本的なカタログ プロパティが変更された場合は、この操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-150">This operation must be performed if a fundamental catalog property is changed, such as accent sensitivity.</span></span><br /><br /> <span data-ttu-id="ec1c2-151">再構築を成功させるために、フルテキスト カタログが存在するファイル グループは、オンラインで読み書きできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-151">For the rebuild to succeed, the filegroup the full-text catalog resides in must be online or read-writeable.</span></span> <span data-ttu-id="ec1c2-152">再構築の後で、フルテキスト インデックスは再作成されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-152">After the rebuild, the full-text index will be repopulated.</span></span><br /><br /> <span data-ttu-id="ec1c2-153">このアクションでは、ALTER FULLTEXT CATALOG *catalog_name* REBUILD が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-153">This action executes ALTER FULLTEXT CATALOG *catalog_name* REBUILD.</span></span>|  
|<span data-ttu-id="ec1c2-154">**[カタログを再作成する]**</span><span class="sxs-lookup"><span data-stu-id="ec1c2-154">**Repopulate catalog**</span></span>|<span data-ttu-id="ec1c2-155">データへの最新の変更によりカタログを更新します。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-155">Updates the catalog with recent changes to the data.</span></span> <span data-ttu-id="ec1c2-156">このオプションは、カタログ ダウンタイムを必要とします。</span><span class="sxs-lookup"><span data-stu-id="ec1c2-156">This option does require catalog downtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec1c2-157">参照</span><span class="sxs-lookup"><span data-stu-id="ec1c2-157">See Also</span></span>  
 [<span data-ttu-id="ec1c2-158">フルテキスト インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="ec1c2-158">Populate Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
  
