---
title: '[アーティクル] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.articles.f1
ms.assetid: 7c743dc6-6c6d-4c92-b711-842e1b0b273e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91336314a9538633af7c528d756d8461f7e8fe13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741866"
---
# <a name="articles"></a><span data-ttu-id="2f70b-102">[アーティクル]</span><span class="sxs-lookup"><span data-stu-id="2f70b-102">Articles</span></span>
  <span data-ttu-id="2f70b-103">**[アーティクル]** ページでは、パブリケーションにアーティクルとして含めるデータベース オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f70b-103">On the **Articles** page, you specify which database objects to include as articles in the publication.</span></span> <span data-ttu-id="2f70b-104">1 つまたは複数の他のデータベース オブジェクトに依存するデータベース オブジェクトをパブリッシュする場合、参照されているオブジェクトをすべてパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f70b-104">If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects.</span></span> <span data-ttu-id="2f70b-105">たとえば、テーブルに依存しているビューをパブリッシュする場合は、そのテーブルもパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f70b-105">For example, if you publish a view that depends on a table, you must publish the table also.</span></span>  
  
 <span data-ttu-id="2f70b-106">パブリッシュできないオブジェクトの横には赤いアイコンが表示され、ウィザード ページの一番下の情報パネルに説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f70b-106">Objects that cannot be published have a red icon next to them, with an explanation in the information panel at the bottom of the wizard page.</span></span> <span data-ttu-id="2f70b-107">パブリッシュできないオブジェクトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2f70b-107">The following objects cannot be published:</span></span>  
  
-   <span data-ttu-id="2f70b-108">暗号化されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2f70b-108">Encrypted objects.</span></span>  
  
-   <span data-ttu-id="2f70b-109">主キーを持たないテーブル。これは、トランザクション パブリケーションにパブリッシュできません。</span><span class="sxs-lookup"><span data-stu-id="2f70b-109">Tables without primary keys cannot be published in transactional publications.</span></span>  
  
-   <span data-ttu-id="2f70b-110">テーブルは、キュー更新サブスクリプションが有効なマージ パブリケーションおよびトランザクション パブリケーションの両方でパブリッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2f70b-110">Tables cannot be published in both a merge publication and a transactional publication enabled for queued updating subscriptions.</span></span> <span data-ttu-id="2f70b-111">複数のパブリケーションでのアーティクルのパブリッシュの詳細については、「[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)」の「複数のパブリケーションでのテーブルのパブリッシュ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f70b-111">For more information about publishing an article in more than one publication, see the "Publishing Tables in More Than One Publication" section in [Publish Data and Database Objects](publish/publish-data-and-database-objects.md).</span></span>  
  
## <a name="oracle-publishers"></a><span data-ttu-id="2f70b-112">Oracle パブリッシャー</span><span class="sxs-lookup"><span data-stu-id="2f70b-112">Oracle Publishers</span></span>  
 <span data-ttu-id="2f70b-113">Oracle パブリッシャーについては、他にも次のような注意点があります。</span><span class="sxs-lookup"><span data-stu-id="2f70b-113">There are additional considerations for Oracle Publishers:</span></span>  
  
-   <span data-ttu-id="2f70b-114">Oracle からパブリッシュできるオブジェクトの一覧については、「 [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f70b-114">For a list of objects that can be published from Oracle, see [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span></span> <span data-ttu-id="2f70b-115">パブリッシュできないオブジェクトは表示されません。</span><span class="sxs-lookup"><span data-stu-id="2f70b-115">Objects that cannot be published are not displayed.</span></span>  
  
-   <span data-ttu-id="2f70b-116">パブリッシュできるデータ型の一覧については、「 [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f70b-116">For a list of data types that can be published, see [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span></span> <span data-ttu-id="2f70b-117">パブリッシュできないデータ型の列は表示されません。</span><span class="sxs-lookup"><span data-stu-id="2f70b-117">Columns with data types that cannot be published are not displayed.</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="2f70b-118">列フィルター</span><span class="sxs-lookup"><span data-stu-id="2f70b-118">Column Filters</span></span>  
 <span data-ttu-id="2f70b-119">このページで列をフィルターするには、 **[パブリッシュするオブジェクト]** ペインでテーブルを展開し、必要な列のみを選択します (このウィザードの **[テーブル行のフィルター選択]** ページで行をフィルターできます)。</span><span class="sxs-lookup"><span data-stu-id="2f70b-119">Filter columns on this page by expanding a table in the **Objects to publish** pane and then selecting only the columns required (rows can be filtered in the **Filter Table Rows** page of this wizard).</span></span> <span data-ttu-id="2f70b-120">列のフィルターが役に立つのには、セキュリティ (機密データのレプリケートの防止) やパフォーマンス (大規模な BLOB 列のレプリケーションの回避など) を含む複数の理由があります。</span><span class="sxs-lookup"><span data-stu-id="2f70b-120">Filtering columns is useful for a number of reasons, including security (preventing sensitive data from being replicated) and performance (avoiding replication of large binary large object (BLOB) columns, for example).</span></span> <span data-ttu-id="2f70b-121">フィルター処理できない列の種類の一覧を含む、列のフィルターの詳細については、「[パブリッシュされたデータのフィルター選択](publish/filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f70b-121">For more information about column filtering, including a list of column types that cannot be filtered, see [Filter Published Data](publish/filter-published-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2f70b-122">Options</span><span class="sxs-lookup"><span data-stu-id="2f70b-122">Options</span></span>  
 <span data-ttu-id="2f70b-123">**[パブリッシュするオブジェクト]** ペインでは、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2f70b-123">The **Objects to publish** pane allows you to:</span></span>  
  
-   <span data-ttu-id="2f70b-124">レプリケーションが可能なすべてのオブジェクトを表示する。</span><span class="sxs-lookup"><span data-stu-id="2f70b-124">View all objects available for replication.</span></span>  
  
-   <span data-ttu-id="2f70b-125">オブジェクトの横にあるチェック ボックスをオンにすることで、オブジェクトをパブリケーションに含めます。</span><span class="sxs-lookup"><span data-stu-id="2f70b-125">Include an object in a publication by selecting the check box next to that object.</span></span>  
  
-   <span data-ttu-id="2f70b-126">オブジェクトの種類 ( **[テーブル]** など) の横にあるチェック ボックスをオンにして、特定の型 (テーブルなど) のオブジェクトすべてをパブリケーションに含める。</span><span class="sxs-lookup"><span data-stu-id="2f70b-126">Include all objects of a particular type (such as a table) in the publication by selecting the check box next to that object type (such as **Tables**).</span></span>  
  
-   <span data-ttu-id="2f70b-127">テーブル ノードを展開してテーブル内の列を表示する。</span><span class="sxs-lookup"><span data-stu-id="2f70b-127">Expand table nodes to see the columns in the table.</span></span>  
  
-   <span data-ttu-id="2f70b-128">列の横にあるチェック ボックスをオフにすることで、パブリケーションのテーブル列をフィルターで除外します。</span><span class="sxs-lookup"><span data-stu-id="2f70b-128">Filter table columns out of a publication by clearing the check box next to the column.</span></span>  
  
-   <span data-ttu-id="2f70b-129">ペイン内でオブジェクトを右クリックし、そのオブジェクトに対するコマンドのメニューを表示する。</span><span class="sxs-lookup"><span data-stu-id="2f70b-129">Right-click an object in the pane to see a menu of commands for that object.</span></span>  
  
 <span data-ttu-id="2f70b-130">**[アーティクルのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="2f70b-130">**Article Properties**</span></span>  
 <span data-ttu-id="2f70b-131">**[アーティクルのプロパティ]** をクリックし、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2f70b-131">Click **Article Properties**, and then click one of the following:</span></span>  
  
-   <span data-ttu-id="2f70b-132">**[反転表示された \<ObjectType> アーティクルのプロパティを設定]** をクリックして、 **[アーティクルのプロパティ - \<ObjectName>]** ダイアログ ボックスを表示します。このダイアログ ボックスで行われたプロパティの変更は、 **[アーティクル]** ページのオブジェクト ペインで反転表示されたオブジェクトだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2f70b-132">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
-   <span data-ttu-id="2f70b-133">**[すべての\<ObjectType> アーティクルのプロパティを設定]** をクリックして、 **[すべての \<ObjectType> アーティクルのプロパティ]** ダイアログ ボックスを表示します。このダイアログ ボックスで行われたプロパティの変更は、パブリケーション用に選択されていないオブジェクトも含めた、 **[アーティクル]** ページのオブジェクト ペインにあるこの種類のすべてのオブジェクトに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2f70b-133">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f70b-134">**[すべての \<ObjectType> アーティクルのプロパティ]** ダイアログ ボックスで行われたプロパティの変更は、 **[アーティクルのプロパティ - \<ObjectName>]** ダイアログ ボックスで以前行われたものをすべてオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="2f70b-134">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="2f70b-135">たとえば、あるオブジェクトの種類のすべてのアーティクルに対して複数の既定を設定し、かつそれぞれのオブジェクトに対してプロパティを設定する場合には、最初にすべてのアーティクルに対する既定を設定します。</span><span class="sxs-lookup"><span data-stu-id="2f70b-135">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="2f70b-136">次に、それぞれのオブジェクトに対してプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2f70b-136">Then set the properties for the individual objects.</span></span>  
  
 <span data-ttu-id="2f70b-137">**[反転表示されたテーブルはダウンロードのみである]**</span><span class="sxs-lookup"><span data-stu-id="2f70b-137">**Highlighted table is download-only**</span></span>  
 <span data-ttu-id="2f70b-138">マージ レプリケーションのみです。</span><span class="sxs-lookup"><span data-stu-id="2f70b-138">Merge replication only.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="2f70b-139">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="2f70b-139">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="2f70b-140">クライアント サブスクリプションを使用している場合、サブスクライバーでの変更を許可しないように指定するときに選択します。</span><span class="sxs-lookup"><span data-stu-id="2f70b-140">Select to specify that changes are disallowed at the Subscriber if a client subscription is used.</span></span> <span data-ttu-id="2f70b-141">ダウンロード専用アーティクルはサブスクライバーで更新されないため、追跡メタデータがサブスクライバーに送信されることはありません。</span><span class="sxs-lookup"><span data-stu-id="2f70b-141">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="2f70b-142">これによってサブスクライバーの記憶域が節約されると共に、特に低速なネットワーク接続ではパフォーマンスの向上にもつながります。</span><span class="sxs-lookup"><span data-stu-id="2f70b-142">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span> <span data-ttu-id="2f70b-143">このオプションは、 **[アーティクルのプロパティ]** ダイアログ ボックスの **[同期の方向]** オプションの **[サブスクライバーへのダウンロードのみを実行し、サブスクライバーの変更を禁止する]** の値に対応します。</span><span class="sxs-lookup"><span data-stu-id="2f70b-143">This option corresponds to a value of **Download-only to Subscriber, prohibit Subscriber changes** for the option **Synchronization direction** in the **Article Properties** dialog box.</span></span> <span data-ttu-id="2f70b-144">詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](merge/optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f70b-144">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="2f70b-145">**[チェック ボックスがオンのオブジェクトのみ一覧に表示する]**</span><span class="sxs-lookup"><span data-stu-id="2f70b-145">**Show only checked objects in the list**</span></span>  
 <span data-ttu-id="2f70b-146">オブジェクト ペインで選択されたアーティクルのみを表示する場合に、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2f70b-146">Select this check box to show only those articles that are selected in the object pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f70b-147">参照</span><span class="sxs-lookup"><span data-stu-id="2f70b-147">See Also</span></span>  
 <span data-ttu-id="2f70b-148">[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="2f70b-148">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="2f70b-149">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="2f70b-149">[Create a Publication](publish/create-a-publication.md) </span></span>  
 [<span data-ttu-id="2f70b-150">パブリケーション プロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="2f70b-150">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)  
  
  
