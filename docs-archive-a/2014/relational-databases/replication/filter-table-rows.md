---
title: テーブル行のフィルター選択 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.filtertablerows.f1
ms.assetid: 005f5c71-0401-490e-8823-adc54a2e9675
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9adeb2501adfd37658ddf05aa9956d6c3922bb80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632354"
---
# <a name="filter-table-rows"></a><span data-ttu-id="b4e64-102">[テーブル行のフィルター選択]</span><span class="sxs-lookup"><span data-stu-id="b4e64-102">Filter Table Rows</span></span>
  <span data-ttu-id="b4e64-103">**[テーブル行のフィルター選択]** ページでは、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-103">The **Filter Table Rows** page allows you to:</span></span>  
  
-   <span data-ttu-id="b4e64-104">静的行フィルターをスナップショット パブリケーション、トランザクション パブリケーション、およびマージ パブリケーションのテーブル アーティクルに適用します。</span><span class="sxs-lookup"><span data-stu-id="b4e64-104">Apply static row filters to table articles in snapshot, transactional, and merge publications.</span></span>  
  
-   <span data-ttu-id="b4e64-105">パラメーター化された行フィルターをマージ パブリケーションのテーブル アーティクルに適用します。</span><span class="sxs-lookup"><span data-stu-id="b4e64-105">Apply parameterized row filters to table articles in merge publications.</span></span>  
  
-   <span data-ttu-id="b4e64-106">結合フィルターを使用して、マージ テーブル アーティクルのフィルターを関連テーブル アーティクルに拡張します。</span><span class="sxs-lookup"><span data-stu-id="b4e64-106">Use join filters to extend filters on merge table articles to related table articles.</span></span>  
  
 <span data-ttu-id="b4e64-107">フィルター オプションの詳細については、「[パブリッシュされたデータのフィルター選択](publish/filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4e64-107">For more information about filtering options, see [Filter Published Data](publish/filter-published-data.md).</span></span> <span data-ttu-id="b4e64-108">フィルター選択は、 **[パブリケーションのプロパティ]** ダイアログ ボックスの **[行のフィルター選択]** ページで変更することができます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-108">Filtering can be changed in the **Filter Rows** page of the **Publication Properties** dialog box.</span></span>  
  
 <span data-ttu-id="b4e64-109">アプリケーションのパフォーマンスを最大限にし、なおかつリモート コンピューターで必要とされる記憶容量を少なくする場合、または特定のデータの使用を特定のサブスクライバーに制限する場合には、必要なデータだけをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="b4e64-109">To maximize application performance and reduce the amount of remote storage required, or to restrict the availability of certain data to specific Subscribers, you should publish only the data required.</span></span> <span data-ttu-id="b4e64-110">パブリケーションには、フィルター済み、フィルターなしの双方のテーブルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-110">Your publication can include both unfiltered and filtered tables.</span></span> <span data-ttu-id="b4e64-111">たとえば、会社製品のすべてを収めたテーブル (フィルターなし) を含める一方で、行フィルターを使用して、特定の地域についてフィルター済みの顧客のテーブルを提供できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-111">For example, you could include the complete (unfiltered) table of company products and use row filters to provide a filtered table of customers for a specific region.</span></span> <span data-ttu-id="b4e64-112">パブリッシュされたデータをフィルター選択することによって、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="b4e64-112">By filtering published data, you can:</span></span>  
  
-   <span data-ttu-id="b4e64-113">ネットワーク上で送信するデータ量を最小限に抑えられる。</span><span class="sxs-lookup"><span data-stu-id="b4e64-113">Minimize the amount of data sent over the network.</span></span>  
  
-   <span data-ttu-id="b4e64-114">サブスクライバーで必要となる保存領域を削減できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-114">Reduce the amount of storage space required at the Subscriber.</span></span>  
  
-   <span data-ttu-id="b4e64-115">各サブスクライバーの要件に基づいてパブリケーションとアプリケーションをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-115">Customize publications and applications based on individual Subscriber requirements.</span></span>  
  
-   <span data-ttu-id="b4e64-116">サブスクライバーがデータを更新する場合に、異なるデータ パーティションを異なるサブスクライバーに送信できるので (2 つのサブスクライバーが同一のデータ値を更新することはない)、競合をなくす、または減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-116">Avoid or reduce conflicts if Subscribers are updating data, because different data partitions can be sent to different Subscribers (no two Subscribers will be updating the same data values).</span></span>  
  
-   <span data-ttu-id="b4e64-117">機密データの送信を回避できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-117">Avoid transmitting sensitive data.</span></span> <span data-ttu-id="b4e64-118">行フィルターと列フィルターを使用して、サブスクライバーによるデータへのアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-118">Row filters and column filters can be used to restrict a Subscriber's access to data.</span></span> <span data-ttu-id="b4e64-119">マージ レプリケーションにおいて HOST_NAME() を含むパラメーター化されたフィルターを使用する場合は、セキュリティ上の留意事項があります。</span><span class="sxs-lookup"><span data-stu-id="b4e64-119">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="b4e64-120">詳細については、「 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)」の「HOST_NAME() によるフィルター選択」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4e64-120">For more information, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="b4e64-121">フィルターには、レプリケーションで行の識別に使用される `rowguidcol` を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="b4e64-121">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="b4e64-122">既定では、これはマージ レプリケーションのセットアップ時に追加される列であり、 **rowguid**という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-122">By default this is the column added at the time you set up merge replication and is named **rowguid**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4e64-123">Options</span><span class="sxs-lookup"><span data-stu-id="b4e64-123">Options</span></span>  
 <span data-ttu-id="b4e64-124">**[フィルター選択されたテーブル]**</span><span class="sxs-lookup"><span data-stu-id="b4e64-124">**Filtered Tables**</span></span>  
 <span data-ttu-id="b4e64-125">このペインには、パブリケーションのテーブル アーティクルに追加したフィルターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-125">This pane is populated with filters as you add them to table articles in the publication.</span></span> <span data-ttu-id="b4e64-126">行フィルターが設定されているテーブルは、ペイン内で最上位レベルのノードとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-126">Tables with row filters are shown as top-level nodes in the pane.</span></span> <span data-ttu-id="b4e64-127">マージ パブリケーションの場合、結合フィルターを介してフィルター選択が拡張されているテーブルは、子ノードとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-127">For merge publications, tables to which filtering has been extended through a join filter are shown as child nodes.</span></span>  
  
 <span data-ttu-id="b4e64-128">**追加**</span><span class="sxs-lookup"><span data-stu-id="b4e64-128">**Add**</span></span>  
 <span data-ttu-id="b4e64-129">**[追加]** をクリックすると、テーブル アーティクルをフィルター選択するためのダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-129">Click **Add** to launch a dialog box that enables you to filter table articles.</span></span> <span data-ttu-id="b4e64-130">スナップショット パブリケーションまたはトランザクション パブリケーションに対して **[追加]** をクリックすると、ダイアログ ボックスが即座に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-130">Clicking **Add** for a snapshot or transactional publication launches a dialog box immediately.</span></span> <span data-ttu-id="b4e64-131">マージ パブリケーションのために **[追加]** をクリックすると、次の 3 つの選択肢が表示されます。 **[フィルターの追加]** 、 **[選択したフィルターを拡張するために結合を追加する]** 、 **[フィルターを自動的に生成]** 。</span><span class="sxs-lookup"><span data-stu-id="b4e64-131">Clicking **Add** for a merge publication displays three choices: **Add Filter**; **Add Join to Extend the Selected Filter**; **Automatically Generate Filters**.</span></span>  
  
-   <span data-ttu-id="b4e64-132">**[フィルターの追加]** をクリックすると、 **[フィルターの追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-132">Select **Add Filter** to launch the **Add Filter** dialog box.</span></span> <span data-ttu-id="b4e64-133">このダイアログ ボックスでは、行フィルターをテーブル アーティクルに適用できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-133">This dialog box allows you to apply row filters to a table article.</span></span> <span data-ttu-id="b4e64-134">たとえば、 **[フィルターの追加]** ダイアログ ボックスを使用して、顧客データ テーブルをサブスクライバーにレプリケートするときにフランスの顧客に関するデータだけを格納するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-134">In the **Add Filter** dialog box, you could, for example, specify that a table with customer data should only contain data on French customers when it is replicated to Subscribers.</span></span>  
  
-   <span data-ttu-id="b4e64-135">**[選択したフィルターを拡張するために結合を追加する]** をクリックすると、 **[結合の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-135">Select **Add Join to Extend the Selected Filter** to launch the **Add Join** dialog box.</span></span> <span data-ttu-id="b4e64-136">**[結合の追加]** ダイアログ ボックスでは、行フィルターを拡張して、行フィルターが設定されているテーブルに関連付けられているテーブル内のデータをフィルター選択するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-136">The **Add Join** dialog box allows you to extend a row filter so that it filters data in tables related to the table with the row filter.</span></span> <span data-ttu-id="b4e64-137">たとえば、フランスの顧客に関するデータだけを含むように顧客テーブルにフィルターが設定され、顧客注文のための関連テーブルがある場合は、2 つのテーブル間に結合を定義して、フランスの顧客からの注文だけが注文テーブルに含まれるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-137">For example, if a customer table is filtered so that it only contains data on French customers and there is a related table for customer orders, you can define a join between the two tables so that the orders table only includes orders from French customers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4e64-138">このオプションは、フィルター ペイン内で結合のベース テーブルを最初に選択している場合だけ利用できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-138">This option is available only if you first select the base table of the join in the filter pane.</span></span>  
  
-   <span data-ttu-id="b4e64-139">**[フィルターを自動的に生成]** をクリックすると、 **[フィルターの生成]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-139">Select **Automatically Generate Filters** to launch the **Generate Filters** dialog box.</span></span> <span data-ttu-id="b4e64-140">このダイアログ ボックスでは、マージ パブリケーション内の 1 つのテーブルに対して行フィルターを定義できます。この行フィルターは、レプリケーションによって、外部キー リレーションシップを介して関連付けられる他のテーブルに自動的に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-140">This dialog box allows you to define a row filter on one table in a merge publication that replication automatically extends to other tables that are related through foreign key relationships.</span></span> <span data-ttu-id="b4e64-141">たとえば、パブリケーションに、顧客テーブル、(顧客テーブルへの外部キーを含む) 注文テーブル、および (注文テーブルへの外部キーを含む) 受注明細テーブルの 3 つのテーブルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-141">For example, a publication could include three tables: a customer table, an orders table (with a foreign key to the customer table), and an order details table (with a foreign key to the orders table).</span></span> <span data-ttu-id="b4e64-142">顧客テーブルに行フィルターを定義すると、レプリケーションによってそれが他のテーブルに拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-142">Define a row filter on the customer table, and replication will extend it to the other tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4e64-143">レプリケーションによってフィルターを自動的に生成した場合、パブリケーションの既存のフィルターは削除されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-143">When filters are automatically generated by replication, any existing filters on the publication are deleted.</span></span> <span data-ttu-id="b4e64-144">自動生成したフィルターと手動で指定したフィルターの両方を含めるには、フィルターの生成を最初に行います。</span><span class="sxs-lookup"><span data-stu-id="b4e64-144">To include both filters generated automatically and ones specified manually, generate filters first.</span></span> <span data-ttu-id="b4e64-145">自動生成したフィルターは、1 つのパブリケーションにつき 1 セットしか指定できません。</span><span class="sxs-lookup"><span data-stu-id="b4e64-145">You can only specify one set of automatically generated filters for each publication.</span></span>  
  
 <span data-ttu-id="b4e64-146">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="b4e64-146">**Edit**</span></span>  
 <span data-ttu-id="b4e64-147">フィルター ペインで行フィルターまたは結合フィルターを選択し、 **[編集]** をクリックすると、 **[フィルターの編集]** ダイアログ ボックスまたは **[結合の編集]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-147">Select a row filter or join filter in the filter pane and click **Edit** to launch the **Edit Filter** or **Edit Join** dialog box.</span></span>  
  
 <span data-ttu-id="b4e64-148">**削除**</span><span class="sxs-lookup"><span data-stu-id="b4e64-148">**Delete**</span></span>  
 <span data-ttu-id="b4e64-149">フィルター ペインで行フィルターまたは結合フィルターを選択し、 **[削除]** をクリックすると、フィルターを削除できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-149">Select a row filter or join filter in the filter pane and click **Delete** to delete the filter.</span></span>  
  
 <span data-ttu-id="b4e64-150">**[テーブルの検索]**</span><span class="sxs-lookup"><span data-stu-id="b4e64-150">**Find Table**</span></span>  
 <span data-ttu-id="b4e64-151">結合フィルターを持つマージ パブリケーションのみです。</span><span class="sxs-lookup"><span data-stu-id="b4e64-151">Merge publications with join filters only.</span></span> <span data-ttu-id="b4e64-152">**[テーブルの検索]** をクリックすると、複雑なフィルター ツリー内でテーブルを検索できます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-152">Click **Find Table** to find a table in a complex filter tree.</span></span> <span data-ttu-id="b4e64-153">複雑なリレーションシップを持つデータベースでは、1 つのテーブルを複数のテーブルに結合できます。その場合、テーブルはフィルター ツリー内で複数の場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-153">In a database with complex relationships, a table can be joined to multiple tables, and therefore can appear in more than one place in the filter tree.</span></span>  
  
 <span data-ttu-id="b4e64-154">実際のテーブルはツリー内の 1 つの場所に表示されます。他の場所では、テーブルがショートカットによって表されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-154">The actual table appears in only one place in the tree, and in other places, the table is represented by a shortcut.</span></span> <span data-ttu-id="b4e64-155">テーブルのショートカットはテーブルの単なる参照であり、テーブルの子ノードを示すものではありません。</span><span class="sxs-lookup"><span data-stu-id="b4e64-155">A shortcut to a table is only a reference to the table; it does not show the child nodes of the table.</span></span> <span data-ttu-id="b4e64-156">ショートカット ノードはショートカット矢印付きで示されます。このノードを展開すると、 **[\<tablename> のテーブルを表示するには、[テーブルの検索] をクリックします]** というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-156">A shortcut node is marked with a shortcut arrow, and expanding that node shows the text **Click Find Table to see table for \<tablename>**.</span></span>  
  
 <span data-ttu-id="b4e64-157">ペインでショートカット ノードをクリックし、 **[テーブルの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4e64-157">Select a shortcut node in the pane and click **Find Table**.</span></span> <span data-ttu-id="b4e64-158">ペインが拡張され、テーブルが反転表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-158">The pane is expanded and the table is highlighted.</span></span> <span data-ttu-id="b4e64-159">ショートカット ノードを選択せずに **[テーブルの検索]** をクリックすると、 **[テーブルの検索]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-159">If you click **Find Table** without a shortcut node selected, a **Find Table** dialog box is launched.</span></span>  
  
 <span data-ttu-id="b4e64-160">**Assert**</span><span class="sxs-lookup"><span data-stu-id="b4e64-160">**Filter**</span></span>  
 <span data-ttu-id="b4e64-161">フィルター ペインで選択されたフィルターの [!INCLUDE[tsql](../../includes/tsql-md.md)] 定義を含みます。</span><span class="sxs-lookup"><span data-stu-id="b4e64-161">Contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] definition for the filter selected in the filter pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e64-162">参照</span><span class="sxs-lookup"><span data-stu-id="b4e64-162">See Also</span></span>  
 <span data-ttu-id="b4e64-163">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="b4e64-163">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="b4e64-164">[パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b4e64-164">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="b4e64-165">[パブリッシュされたデータのフィルター処理](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="b4e64-165">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="b4e64-166">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="b4e64-166">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="b4e64-167">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="b4e64-167">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="b4e64-168">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="b4e64-168">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  