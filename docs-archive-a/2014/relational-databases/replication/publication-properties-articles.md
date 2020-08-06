---
title: '[パブリケーションのプロパティ]、[アーティクル] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.articles.f1
ms.assetid: bdeea318-a153-44b8-9e51-9155f3bad18b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b88c54a6fc8c33193af7573ebd9b7c9931d8fbe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717834"
---
# <a name="publication-properties-articles"></a><span data-ttu-id="77189-102">[パブリケーションのプロパティ]、[アーティクル]</span><span class="sxs-lookup"><span data-stu-id="77189-102">Publication Properties, Articles</span></span>
  <span data-ttu-id="77189-103">**[パブリケーションのプロパティ]** ダイアログ ボックスの **[アーティクル]** ページには、パブリケーションに含まれるアーティクルの情報が表示されるため、これを使用すると、既存のパブリケーションに対してアーティクルを追加したり削除したりできます。また、アーティクルのプロパティや列のフィルターを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="77189-103">The **Articles** page of the **Publication Properties** dialog box: contains information about the articles contained in a publication; allows you to add articles to and drop articles from existing publications; and allows you to change article properties and column filtering.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77189-104">パブリケーションの作成後、プロパティの変更によっては新しいスナップショットが必要となります。</span><span class="sxs-lookup"><span data-stu-id="77189-104">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="77189-105">パブリケーションにサブスクリプションが含まれている場合、変更によっては、すべてのサブスクリプションを再初期化する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="77189-105">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="77189-106">詳細については、「[Change Publication and Article Properties](publish/change-publication-and-article-properties.md)」 (パブリケーションおよびアーティクルのプロパティの変更) と「[既存のパブリケーションでのアーティクルの追加および削除](publish/add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77189-106">For more information, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
 <span data-ttu-id="77189-107">1 つまたは複数の他のデータベース オブジェクトに依存するデータベース オブジェクトをパブリッシュする場合、参照されているオブジェクトをすべてパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="77189-107">If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects.</span></span> <span data-ttu-id="77189-108">たとえば、テーブルに依存しているビューをパブリッシュする場合は、そのテーブルもパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="77189-108">For example, if you publish a view that depends on a table, you must publish the table also.</span></span>  
  
 <span data-ttu-id="77189-109">パブリッシュできないオブジェクトの横には赤いアイコンが表示され、ウィザード ページの一番下の情報パネルに説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77189-109">Objects that cannot be published have a red icon next to them, with an explanation in the information panel at the bottom of the wizard page.</span></span> <span data-ttu-id="77189-110">パブリッシュできないオブジェクトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="77189-110">The following objects cannot be published:</span></span>  
  
-   <span data-ttu-id="77189-111">暗号化されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="77189-111">Encrypted objects.</span></span>  
  
-   <span data-ttu-id="77189-112">NULL 値が許可されている列を含むインデックス付きビュー。</span><span class="sxs-lookup"><span data-stu-id="77189-112">Indexed views containing columns that allow NULL.</span></span>  
  
-   <span data-ttu-id="77189-113">主キーを持たないテーブル。これは、トランザクション パブリケーションにパブリッシュできません。</span><span class="sxs-lookup"><span data-stu-id="77189-113">Tables without primary keys cannot be published in transactional publications.</span></span>  
  
-   <span data-ttu-id="77189-114">テーブルは、キュー更新サブスクリプションが有効なマージ パブリケーションおよびトランザクション パブリケーションの両方でパブリッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="77189-114">Tables cannot be published in both a merge publication and a transactional publication enabled for queued updating subscriptions.</span></span> <span data-ttu-id="77189-115">複数のパブリケーションでのアーティクルのパブリッシュの詳細については、「[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)」の「複数のパブリケーションでのテーブルのパブリッシュ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77189-115">For more information about publishing an article in more than one publication, see the "Publishing Tables in More Than One Publication" section in [Publish Data and Database Objects](publish/publish-data-and-database-objects.md).</span></span>  
  
## <a name="oracle-publishers"></a><span data-ttu-id="77189-116">Oracle パブリッシャー</span><span class="sxs-lookup"><span data-stu-id="77189-116">Oracle Publishers</span></span>  
 <span data-ttu-id="77189-117">Oracle パブリッシャーについては、他にも次のような注意点があります。</span><span class="sxs-lookup"><span data-stu-id="77189-117">There are additional considerations for Oracle Publishers:</span></span>  
  
-   <span data-ttu-id="77189-118">Oracle からパブリッシュできるオブジェクトの一覧については、「 [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77189-118">For a list of objects that can be published from Oracle, see [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span></span> <span data-ttu-id="77189-119">パブリッシュできないオブジェクトは表示されません。</span><span class="sxs-lookup"><span data-stu-id="77189-119">Objects that cannot be published are not displayed.</span></span>  
  
-   <span data-ttu-id="77189-120">パブリッシュできるデータ型の一覧については、「 [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77189-120">For a list of data types that can be published, see [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span></span> <span data-ttu-id="77189-121">パブリッシュできないデータ型の列は表示されません。</span><span class="sxs-lookup"><span data-stu-id="77189-121">Columns with data types that cannot be published are not displayed.</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="77189-122">列フィルター</span><span class="sxs-lookup"><span data-stu-id="77189-122">Column Filters</span></span>  
 <span data-ttu-id="77189-123">このページで列をフィルターするには、 **[パブリッシュするオブジェクト]** ペインでテーブルを展開し、必要な列のみを選択します (このウィザードの **[テーブル行のフィルター選択]** ページで行をフィルターできます)。</span><span class="sxs-lookup"><span data-stu-id="77189-123">Filter columns on this page by expanding a table in the **Objects to publish** pane and then selecting only the columns required (rows can be filtered in the **Filter Table Rows** page of this wizard).</span></span> <span data-ttu-id="77189-124">列のフィルターが役に立つのには、セキュリティ (機密データのレプリケートの防止) やパフォーマンス (大規模な BLOB 列のレプリケーションの回避など) を含む複数の理由があります。</span><span class="sxs-lookup"><span data-stu-id="77189-124">Filtering columns is useful for a number of reasons, including security (preventing sensitive data from being replicated) and performance (avoiding replication of large binary large object (BLOB) columns, for example).</span></span> <span data-ttu-id="77189-125">フィルター処理できない列の種類の一覧を含む、列のフィルターの詳細については、「[パブリッシュされたデータのフィルター選択](publish/filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77189-125">For more information about column filtering, including a list of column types that cannot be filtered, see [Filter Published Data](publish/filter-published-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="77189-126">Options</span><span class="sxs-lookup"><span data-stu-id="77189-126">Options</span></span>  
 <span data-ttu-id="77189-127">**[パブリッシュするオブジェクト]** ペインでは、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="77189-127">The **Objects to publish** pane allows you to:</span></span>  
  
-   <span data-ttu-id="77189-128">レプリケーションが可能なすべてのオブジェクトを表示する。</span><span class="sxs-lookup"><span data-stu-id="77189-128">View all objects available for replication.</span></span>  
  
-   <span data-ttu-id="77189-129">オブジェクトの横にあるチェック ボックスをオンにして、アーティクルをパブリケーションに追加する。</span><span class="sxs-lookup"><span data-stu-id="77189-129">Add an article to a publication by selecting the check box next to that object.</span></span>  
  
-   <span data-ttu-id="77189-130">オブジェクトの横にあるチェック ボックスをオフにして、パブリケーションからアーティクルを削除する。</span><span class="sxs-lookup"><span data-stu-id="77189-130">Drop an article from a publication by clearing the check box next to that object.</span></span> <span data-ttu-id="77189-131">アーティクルの削除の詳細については、「[既存のパブリケーションでのアーティクルの追加および削除](publish/add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77189-131">For information about when articles can be dropped, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
-   <span data-ttu-id="77189-132">オブジェクトの種類 ( **[テーブル]** など) の横にあるチェック ボックスをオンにして、特定の型 (テーブルなど) のオブジェクトすべてをパブリケーションに含める。</span><span class="sxs-lookup"><span data-stu-id="77189-132">Include all objects of a particular type (such as a table) in the publication by selecting the check box next to that object type (such as **Tables**).</span></span>  
  
-   <span data-ttu-id="77189-133">テーブル ノードを展開してテーブル内の列を表示する。</span><span class="sxs-lookup"><span data-stu-id="77189-133">Expand table nodes to see the columns in the table.</span></span>  
  
-   <span data-ttu-id="77189-134">列の横にあるチェック ボックスをオフにしてテーブル列をパブリケーションからフィルターする、またはチェック ボックスをオンにしてパブリッシュされていない列を含める。</span><span class="sxs-lookup"><span data-stu-id="77189-134">Filter table columns out of a publication by clearing the check box next to the column or include unpublished columns by selecting the check box.</span></span>  
  
-   <span data-ttu-id="77189-135">ペイン内でオブジェクトを右クリックし、そのオブジェクトに対するコマンドのメニューを表示する。</span><span class="sxs-lookup"><span data-stu-id="77189-135">Right-click an object in the pane to see a menu of commands for that object.</span></span>  
  
 <span data-ttu-id="77189-136">**[アーティクルのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="77189-136">**Article Properties**</span></span>  
 <span data-ttu-id="77189-137">**[アーティクルのプロパティ]** をクリックし、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="77189-137">Click **Article Properties** , and then click one of the following:</span></span>  
  
-   <span data-ttu-id="77189-138">**[反転表示された \<ObjectType> アーティクルのプロパティを設定]** をクリックし、 **[アーティクルのプロパティ - \<ObjectName>]** ダイアログ ボックスを表示します。このダイアログ ボックスで行われたプロパティの変更は、 **[アーティクル]** ページのオブジェクト ペインで反転表示されたオブジェクトだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="77189-138">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
-   <span data-ttu-id="77189-139">**[すべての\<ObjectType> アーティクルのプロパティを設定]** をクリックし、 **[すべての \<ObjectType> アーティクルのプロパティ]** ダイアログ ボックスを表示します。このダイアログ ボックスで行われたプロパティの変更は、パブリケーションが選択されていないオブジェクトも含めた、 **[アーティクル]** ページのオブジェクト ペインにあるこの種類のすべてのオブジェクトに適用されます。</span><span class="sxs-lookup"><span data-stu-id="77189-139">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77189-140">**[すべての \<ObjectType> アーティクルのプロパティ]** ダイアログ ボックスで行われたプロパティの変更は、 **[アーティクルのプロパティ - \<ObjectName>]** ダイアログ ボックスで以前行われたすべての変更をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="77189-140">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="77189-141">たとえば、あるオブジェクトの種類のすべてのアーティクルに対して複数の既定を設定し、かつそれぞれのオブジェクトに対してプロパティを設定する場合には、最初にすべてのアーティクルに対する既定を設定します。</span><span class="sxs-lookup"><span data-stu-id="77189-141">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="77189-142">次に、それぞれのオブジェクトに対してプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="77189-142">Then set the properties for the individual objects.</span></span>  
  
 <span data-ttu-id="77189-143">**[反転表示されたテーブルはダウンロードのみである]**</span><span class="sxs-lookup"><span data-stu-id="77189-143">**Highlighted table is download-only**</span></span>  
 <span data-ttu-id="77189-144">マージ レプリケーションのみです。</span><span class="sxs-lookup"><span data-stu-id="77189-144">Merge replication only.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="77189-145">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="77189-145">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="77189-146">クライアント サブスクリプションを使用している場合、サブスクライバーでの変更を許可しないように指定するときに選択します。</span><span class="sxs-lookup"><span data-stu-id="77189-146">Select to specify that changes are disallowed at the Subscriber if a client subscription is used.</span></span> <span data-ttu-id="77189-147">ダウンロード専用アーティクルはサブスクライバーで更新されないため、追跡メタデータがサブスクライバーに送信されることはありません。</span><span class="sxs-lookup"><span data-stu-id="77189-147">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="77189-148">これによってサブスクライバーの記憶域が節約されると共に、特に低速なネットワーク接続ではパフォーマンスの向上にもつながります。</span><span class="sxs-lookup"><span data-stu-id="77189-148">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span> <span data-ttu-id="77189-149">このオプションは、 **[アーティクルのプロパティ]** ダイアログ ボックスの **[同期の方向]** オプションの **[サブスクライバーへのダウンロードのみを実行し、サブスクライバーの変更を禁止する]** の値に対応します。</span><span class="sxs-lookup"><span data-stu-id="77189-149">This option corresponds to a value of **Download-only to Subscriber, prohibit Subscriber changes** for the option **Synchronization direction** in the **Article Properties** dialog box.</span></span> <span data-ttu-id="77189-150">詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](merge/optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77189-150">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="77189-151">**[チェック ボックスがオンのオブジェクトのみ一覧に表示する]**</span><span class="sxs-lookup"><span data-stu-id="77189-151">**Show only checked objects in the list**</span></span>  
 <span data-ttu-id="77189-152">オブジェクト ペインで選択されたアーティクルのみを表示する場合に、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="77189-152">Select this check box to show only those articles that are selected in the object pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77189-153">参照</span><span class="sxs-lookup"><span data-stu-id="77189-153">See Also</span></span>  
 <span data-ttu-id="77189-154">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="77189-154">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="77189-155">[パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="77189-155">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="77189-156">[初期スナップショットの作成および適用](create-and-apply-the-initial-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="77189-156">[Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) </span></span>  
 <span data-ttu-id="77189-157">[サブスクリプションの再初期化](reinitialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="77189-157">[Reinitialize a Subscription](reinitialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="77189-158">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="77189-158">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
