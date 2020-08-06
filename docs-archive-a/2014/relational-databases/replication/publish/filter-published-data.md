---
title: パブリッシュされたデータのフィルター選択 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication]
- filters [SQL Server replication], about filtering
- filtering [SQL Server replication]
- static row filters
- transactional replication, filtering published data
- replication [SQL Server], filtering published data
- filtering published data [SQL Server replication]
- snapshot replication [SQL Server], filtering published data
- column filters [SQL Server replication]
ms.assetid: 8a914947-72dc-4119-b631-b39c8070c71b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 525e90cecbc4cd6ee817b8fd07748abaf651b524
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633067"
---
# <a name="filter-published-data"></a><span data-ttu-id="08718-102">パブリッシュされたデータのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="08718-102">Filter Published Data</span></span>
  <span data-ttu-id="08718-103">テーブル アーティクルをフィルター選択すると、パブリッシュされるデータのパーティションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="08718-103">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="08718-104">パブリッシュされたデータをフィルター選択することによって、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="08718-104">By filtering published data, you can:</span></span>  
  
-   <span data-ttu-id="08718-105">ネットワーク上で送信するデータ量を最小限に抑えられる。</span><span class="sxs-lookup"><span data-stu-id="08718-105">Minimize the amount of data sent over the network.</span></span>  
  
-   <span data-ttu-id="08718-106">サブスクライバーで必要となる保存領域を削減できます。</span><span class="sxs-lookup"><span data-stu-id="08718-106">Reduce the amount of storage space required at the Subscriber.</span></span>  
  
-   <span data-ttu-id="08718-107">各サブスクライバーの要件に基づいてパブリケーションとアプリケーションをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="08718-107">Customize publications and applications based on individual Subscriber requirements.</span></span>  
  
-   <span data-ttu-id="08718-108">サブスクライバーがデータを更新する場合に、異なるデータ パーティションを異なるサブスクライバーに送信できるので (2 つのサブスクライバーが同一のデータ値を更新することはない)、競合をなくす、または減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="08718-108">Avoid or reduce conflicts if Subscribers are updating data, because different data partitions can be sent to different Subscribers (no two Subscribers will be updating the same data values).</span></span>  
  
-   <span data-ttu-id="08718-109">機密データの送信を回避できます。</span><span class="sxs-lookup"><span data-stu-id="08718-109">Avoid transmitting sensitive data.</span></span> <span data-ttu-id="08718-110">行フィルターと列フィルターを使用して、サブスクライバーによるデータへのアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="08718-110">Row filters and column filters can be used to restrict a Subscriber's access to data.</span></span> <span data-ttu-id="08718-111">マージ レプリケーションにおいて HOST_NAME() を含むパラメーター化されたフィルターを使用する場合は、セキュリティ上の留意事項があります。</span><span class="sxs-lookup"><span data-stu-id="08718-111">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="08718-112">詳細については、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」の「HOST_NAME() によるフィルター選択」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08718-112">For more information, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="08718-113">レプリケーションでは、4 種類のフィルターが利用できます。</span><span class="sxs-lookup"><span data-stu-id="08718-113">Replication offers four types of filters:</span></span>  
  
-   <span data-ttu-id="08718-114">静的行フィルター。すべての種類のレプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="08718-114">Static row filters, which are available with all types of replication.</span></span>  
  
     <span data-ttu-id="08718-115">静的行フィルターを使用して、パブリッシュする行のサブセットを選択できます。</span><span class="sxs-lookup"><span data-stu-id="08718-115">Using static row filters, you can choose a subset of rows to be published.</span></span> <span data-ttu-id="08718-116">フィルター選択されたパブリケーションに対するすべてのサブスクライバーは、フィルター選択されたテーブルの同じ行のサブセットを受信します。</span><span class="sxs-lookup"><span data-stu-id="08718-116">All Subscribers to a filtered publication receive the same subset of rows for the filtered table.</span></span> <span data-ttu-id="08718-117">詳細については、このトピックの「静的行フィルター」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08718-117">For more information, see the section "Static Row Filters" in this topic.</span></span>  
  
-   <span data-ttu-id="08718-118">列フィルター。すべての種類のレプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="08718-118">Column filters, which are available with all types of replication.</span></span>  
  
     <span data-ttu-id="08718-119">列フィルターを使用して、パブリッシュする列のサブセットを選択できます。</span><span class="sxs-lookup"><span data-stu-id="08718-119">Using column filters, you can choose a subset of columns to be published.</span></span> <span data-ttu-id="08718-120">詳細については、このトピックの「列フィルター」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08718-120">For more information, see the section "Column Filters" in this topic.</span></span>  
  
-   <span data-ttu-id="08718-121">パラメーター化された行フィルター。マージ レプリケーションでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="08718-121">Parameterized row filters, which are available only with merge replication.</span></span>  
  
     <span data-ttu-id="08718-122">パラメーター化された行フィルターを使用して、パブリッシュする行のサブセットを選択できます。</span><span class="sxs-lookup"><span data-stu-id="08718-122">Using parameterized row filters, you can choose a subset of rows to be published.</span></span> <span data-ttu-id="08718-123">すべてのサブスクライバーに同じ行のサブセットを送信する静的フィルターと異なり、パラメーター化された行フィルターは、サブスクライバーにより提供されたデータの値を使用し、サブスクライバーにそれぞれ別の行のサブセットを送信します。</span><span class="sxs-lookup"><span data-stu-id="08718-123">Unlike static filters that send the same subset of rows to every Subscriber, parameterized row filters use a data value supplied by the Subscriber to send Subscribers different subsets of rows.</span></span> <span data-ttu-id="08718-124">詳しくは、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08718-124">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="08718-125">結合フィルター。マージ レプリケーションでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="08718-125">Join filters, which are available only with merge replication.</span></span>  
  
     <span data-ttu-id="08718-126">結合フィルターを使用して、1 つのパブリッシュされたテーブルから別のパブリッシュされたテーブルに行フィルターを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="08718-126">Using join filters, you can extend a row filter from one published table to another.</span></span> <span data-ttu-id="08718-127">詳しくは、「 [Join Filters](../merge/join-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08718-127">For more information, see [Join Filters](../merge/join-filters.md).</span></span>  
  
## <a name="static-row-filters"></a><span data-ttu-id="08718-128">静的行フィルター</span><span class="sxs-lookup"><span data-stu-id="08718-128">Static Row Filters</span></span>  
 <span data-ttu-id="08718-129">次の図は、行 2、3、および 6 のみがパブリケーションに含まれるようにフィルター選択される、パブリッシュされたテーブルを示します。</span><span class="sxs-lookup"><span data-stu-id="08718-129">The following illustration shows a published table that is filtered so that only rows 2, 3, and 6 are included in the publication.</span></span>  
  
 <span data-ttu-id="08718-130">![行のフィルタリング](../media/repl-16.gif "行のフィルター選択")</span><span class="sxs-lookup"><span data-stu-id="08718-130">![Row filtering](../media/repl-16.gif "Row filtering")</span></span>  
  
 <span data-ttu-id="08718-131">静的行フィルターは、WHERE 句を使用してパブリッシュするのに適したデータを選択します。WHERE 句の最後の部分を指定してください。</span><span class="sxs-lookup"><span data-stu-id="08718-131">A static row filter uses a WHERE clause to select the appropriate data to be published; you specify the final part of the WHERE clause.</span></span> <span data-ttu-id="08718-132">Adventure Works サンプル データベースの **Product テーブル** を考えます。ここには、列 **ProductLine**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08718-132">Consider the **Product Table** in the Adventure Works sample database, which contains the column **ProductLine**.</span></span> <span data-ttu-id="08718-133">マウンテン バイクに関連した製品についてのデータがある行のみをパブリッシュするには、 `ProductLine = 'M'`を指定します。</span><span class="sxs-lookup"><span data-stu-id="08718-133">To publish only the rows with data on products related to mountain bikes, specify `ProductLine = 'M'`.</span></span>  
  
 <span data-ttu-id="08718-134">静的行フィルターにより、各パブリケーションに対するデータセットは 1 つのみとなります。</span><span class="sxs-lookup"><span data-stu-id="08718-134">A static row filter results in a single set of data for each publication.</span></span> <span data-ttu-id="08718-135">前の例では、すべてのサブスクライバーは、マウンテン バイクに関連する製品についてのデータがある行のみを受信します。</span><span class="sxs-lookup"><span data-stu-id="08718-135">In the previous example, all Subscribers would receive only the rows with data on products related to mountain bikes.</span></span> <span data-ttu-id="08718-136">別のサブスクライバーがロード バイクに関連する製品についてのデータがある行のみを必要としている場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="08718-136">If you have another Subscriber that requires only the rows with data on products related to road bikes:</span></span>  
  
-   <span data-ttu-id="08718-137">スナップショット レプリケーションまたはトランザクション レプリケーションにより、別のパブリケーションを作成し、両方のパブリケーションにテーブルを含めることができます (そのパブリケーションのアーティクルに対するフィルター句で、 `ProductLine = 'R')`を指定します)。</span><span class="sxs-lookup"><span data-stu-id="08718-137">With snapshot or transactional replication, you can create another publication and include the table in both publications (in the filter clause for the article in that publication, specify `ProductLine = 'R')`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08718-138">トランザクション パブリケーションの行フィルターは、オーバーヘッドを大幅に増やす原因となる場合があります。パブリッシュされたテーブルのログ行ごとにアーティクルのフィルター句を評価して、ログ行をレプリケートする必要があるかどうかを判断するからです。</span><span class="sxs-lookup"><span data-stu-id="08718-138">Row filters in transactional publications can add significant overhead because the article filter clause is evaluated for each log row written for a published table, to determine whether the row should be replicated.</span></span> <span data-ttu-id="08718-139">各レプリケーション ノードが全データの読み込みをサポートできる場合、および、データセット全体がそれほど大きくない場合には、トランザクション パブリケーションの行フィルターは避けてください。</span><span class="sxs-lookup"><span data-stu-id="08718-139">Row filters in transactional publications should be avoided if each replication node can support the full data load, and the overall data set is reasonably small.</span></span>  
  
-   <span data-ttu-id="08718-140">マージ レプリケーションでは、静的行フィルターで複数のパブリケーションを作成するのではなく、パラメーター化された行フィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="08718-140">With merge replication, use parameterized row filters rather than creating multiple publications with static row filters.</span></span> <span data-ttu-id="08718-141">詳しくは、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08718-141">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="08718-142">静的行フィルターを定義または変更するには、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08718-142">To define or modify a static row filter, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="08718-143">列フィルター</span><span class="sxs-lookup"><span data-stu-id="08718-143">Column Filters</span></span>  
 <span data-ttu-id="08718-144">次の図は、列 C をフィルター選択により除外するパブリケーションを示します。</span><span class="sxs-lookup"><span data-stu-id="08718-144">The following illustration shows a publication that filters out column C.</span></span>  
  
 <span data-ttu-id="08718-145">![列のフィルター選択](../media/repl-17.gif "列のフィルター選択")</span><span class="sxs-lookup"><span data-stu-id="08718-145">![Column filtering](../media/repl-17.gif "Column filtering")</span></span>  
  
 <span data-ttu-id="08718-146">以下に示すように、行フィルターと列フィルターを組み合わせることも可能です。</span><span class="sxs-lookup"><span data-stu-id="08718-146">You can also use row and column filtering together, as illustrated here.</span></span>  
  
 <span data-ttu-id="08718-147">![行と列のフィルター選択](../media/repl-18.gif "行と列のフィルター選択")</span><span class="sxs-lookup"><span data-stu-id="08718-147">![Row and column filtering](../media/repl-18.gif "Row and column filtering")</span></span>  
  
 <span data-ttu-id="08718-148">パブリケーションが作成されたら、列のフィルター選択を使用して、既存のパブリケーションからは列を削除してパブリッシャーのテーブルの列を保持することもできますし、パブリケーションに既存の列を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="08718-148">After a publication is created, you can use column filtering to drop a column from an existing publication, but retain the column in the table at the Publisher, and also to include an existing column in the publication.</span></span> <span data-ttu-id="08718-149">新しい列をテーブルに追加し、それをパブリッシュされたアーティクルに追加するなど、その他の変更の場合は、スキーマ変更のレプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="08718-149">For other changes, such as adding a new column to a table and then adding it to the published article, use schema change replication.</span></span> <span data-ttu-id="08718-150">詳細については、「[パブリケーション データベースでのスキーマの変更](make-schema-changes-on-publication-databases.md)」の "列の追加" と "列の削除" を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08718-150">For more information, see the "Adding Columns" and "Dropping Columns" sections in the topic [Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md).</span></span>  
  
 <span data-ttu-id="08718-151">次の表に一覧表示した列の型は、特定の種類のパブリケーションからはフィルター選択により除外することができません。</span><span class="sxs-lookup"><span data-stu-id="08718-151">The types of columns listed in the following table cannot be filtered out of certain types of publications.</span></span>  
  
|<span data-ttu-id="08718-152">列の型</span><span class="sxs-lookup"><span data-stu-id="08718-152">Column type</span></span>|<span data-ttu-id="08718-153">パブリケーションの種類とオプション</span><span class="sxs-lookup"><span data-stu-id="08718-153">Type of publication and options</span></span>|  
|-----------------|-------------------------------------|  
|<span data-ttu-id="08718-154">主キー列</span><span class="sxs-lookup"><span data-stu-id="08718-154">Primary key column</span></span>|<span data-ttu-id="08718-155">主キー列は、トランザクション パブリケーションのすべてのテーブルで必要です。</span><span class="sxs-lookup"><span data-stu-id="08718-155">Primary key columns are required for all tables in transactional publications.</span></span> <span data-ttu-id="08718-156">マージ パブリケーションのテーブルでは、主キーは必要ではありませんが、主キー列が存在する場合、これをフィルター選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="08718-156">Primary keys are not required for tables in merge publications, but if a primary key column is present, it cannot be filtered.</span></span>|  
|<span data-ttu-id="08718-157">外部キー列</span><span class="sxs-lookup"><span data-stu-id="08718-157">Foreign key column</span></span>|<span data-ttu-id="08718-158">パブリケーションの新規作成ウィザードを使用して作成されたすべてのパブリケーション。</span><span class="sxs-lookup"><span data-stu-id="08718-158">All publications created using the New Publication wizard.</span></span> <span data-ttu-id="08718-159">外部キー列は、Transact-SQL ストアド プロシージャを使用して、フィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="08718-159">You can filter foreign key columns using Transact-SQL stored procedures.</span></span> <span data-ttu-id="08718-160">詳細については、「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08718-160">For more information, [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>|  
|<span data-ttu-id="08718-161">**rowguid** 列</span><span class="sxs-lookup"><span data-stu-id="08718-161">The **rowguid** column</span></span>|<span data-ttu-id="08718-162">マージパブリケーション<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08718-162">Merge publications<sup>1</sup></span></span>|  
|<span data-ttu-id="08718-163">**msrepl_tran_version** 列</span><span class="sxs-lookup"><span data-stu-id="08718-163">The **msrepl_tran_version** column</span></span>|<span data-ttu-id="08718-164">更新可能なサブスクリプションを有効にしたスナップショットまたはトランザクション パブリケーション</span><span class="sxs-lookup"><span data-stu-id="08718-164">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="08718-165">NULL を許容せず、既定値または IDENTITY プロパティが設定されていない列</span><span class="sxs-lookup"><span data-stu-id="08718-165">Columns that do not allow NULL and do not have default values or the IDENTITY property set.</span></span>|<span data-ttu-id="08718-166">更新可能なサブスクリプションを有効にしたスナップショットまたはトランザクション パブリケーション</span><span class="sxs-lookup"><span data-stu-id="08718-166">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="08718-167">一意の制約またはインデックスのある列</span><span class="sxs-lookup"><span data-stu-id="08718-167">Columns with unique constraints or indexes</span></span>|<span data-ttu-id="08718-168">更新可能なサブスクリプションを有効にしたスナップショットまたはトランザクション パブリケーション</span><span class="sxs-lookup"><span data-stu-id="08718-168">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="08718-169">SQL Server 7.0 マージ パブリケーションのすべての列</span><span class="sxs-lookup"><span data-stu-id="08718-169">All columns in a SQL Server 7.0 merge publication</span></span>|<span data-ttu-id="08718-170">SQL Server 7.0 マージ パブリケーションでは、列はフィルター選択できません。</span><span class="sxs-lookup"><span data-stu-id="08718-170">Columns cannot be filtered in SQL Server 7.0 merge publications.</span></span>|  
|<span data-ttu-id="08718-171">Timestamp</span><span class="sxs-lookup"><span data-stu-id="08718-171">Timestamp</span></span>|<span data-ttu-id="08718-172">更新可能なサブスクリプションを許可する SQL Server 7.0 のスナップショットまたはトランザクション パブリケーション</span><span class="sxs-lookup"><span data-stu-id="08718-172">SQL Server 7.0 snapshot or transactional publications that allow updatable subscriptions</span></span>|  
  
 <span data-ttu-id="08718-173"><sup>1</sup>マージパブリケーションでテーブルをパブリッシュしていて、そのテーブルにプロパティが設定されたデータ型の列が既に含まれている場合 `uniqueidentifier` `ROWGUIDCOL` 、レプリケーションでは、 **rowguid**という名前の追加列を作成するのではなく、この列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="08718-173"><sup>1</sup> If you are publishing a table in a merge publication and that table already contains a column of data type `uniqueidentifier` with the `ROWGUIDCOL` property set, replication can use this column instead of creating an additional column named **rowguid**.</span></span> <span data-ttu-id="08718-174">この場合、この既存の列をパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="08718-174">In this case, the existing column must be published.</span></span>  
  
 <span data-ttu-id="08718-175">列フィルターを定義または変更するには、「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」の「HOST_NAME() によるフィルター選択」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08718-175">To define or modify a column filter, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
## <a name="filtering-considerations"></a><span data-ttu-id="08718-176">フィルター選択に関する注意点</span><span class="sxs-lookup"><span data-stu-id="08718-176">Filtering Considerations</span></span>  
 <span data-ttu-id="08718-177">データをフィルター選択するときは、以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="08718-177">Keep the following considerations in mind when filtering data:</span></span>  
  
-   <span data-ttu-id="08718-178">行フィルターで参照されるすべての列は、パブリケーションに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="08718-178">All columns referenced in row filters must be included in the publication.</span></span> <span data-ttu-id="08718-179">つまり、行フィルターで使用される列を除外する列フィルターを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="08718-179">In other words, you cannot use a column filter to exclude a column that is used in a row filter.</span></span>  
  
-   <span data-ttu-id="08718-180">サブスクリプションを初期化した後でフィルターを追加、または変更する場合は、サブスクリプションは再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08718-180">If a filter is added or changed after subscriptions have been initialized, the subscriptions must be reinitialized.</span></span>  
  
-   <span data-ttu-id="08718-181">フィルターで使用される列に許容される最大バイト数は、マージ パブリケーションでは、アーティクルにつき 1,024 バイト、トランザクション パブリケーションでは、アーティクルにつき 8,000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="08718-181">The maximum number of bytes allowed for a column used in a filter is 1024 for an article in a merge publication and 8000 for an article in a transactional publication.</span></span>  
  
-   <span data-ttu-id="08718-182">次のデータ型を持つ列は、行フィルターまたは結合フィルターで参照できません。</span><span class="sxs-lookup"><span data-stu-id="08718-182">Columns with the following data types cannot be referenced in row filters or join filters:</span></span>  
  
    -   `varchar(max) and nvarchar(max)`  
  
    -   `varbinary(max)`  
  
    -   `text and ntext`  
  
    -   `image`  
  
    -   `XML`  
  
    -   `UDT`  
  
-   <span data-ttu-id="08718-183">トランザクション レプリケーションでは、インデックス付きビューをビューまたはテーブルとしてレプリケートできます。</span><span class="sxs-lookup"><span data-stu-id="08718-183">Transactional replication allows you to replicate an indexed view as a view or as a table.</span></span> <span data-ttu-id="08718-184">このビューをテーブルとしてレプリケートする場合、テーブルから列をフィルター選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="08718-184">If you replicate the view as a table, you cannot filter columns from the table.</span></span>  
  
 <span data-ttu-id="08718-185">行フィルターは、データベース間で動作するようには設計されていません。</span><span class="sxs-lookup"><span data-stu-id="08718-185">Row filters are not designed to work across databases.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="08718-186">では、(フィルターが実行される) `sp_replcmds` の実行が意図的にデータベース所有者 (`dbo`) に制限されています。</span><span class="sxs-lookup"><span data-stu-id="08718-186">intentionally restricts the execution of `sp_replcmds` (which filters execute under) to the database owner (`dbo`).</span></span> <span data-ttu-id="08718-187">`dbo` には、データベース間の権限がありません。</span><span class="sxs-lookup"><span data-stu-id="08718-187">The `dbo` does not have cross database privileges.</span></span> <span data-ttu-id="08718-188">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] に CDC (Change Data Capture) が追加されたことで、`sp_replcmds` のロジックは、ユーザーが戻って照会できる情報を変更追跡テーブルに設定します。</span><span class="sxs-lookup"><span data-stu-id="08718-188">With the addition of CDC (Change Data Capture) in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] the `sp_replcmds` logic populates the change tracking tables with information that the user can return to and query.</span></span> <span data-ttu-id="08718-189">セキュリティ上の理由により、はこの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ロジックの実行を制限し、悪意が `dbo` この実行パスに対応できないようにします。</span><span class="sxs-lookup"><span data-stu-id="08718-189">For security reasons, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restricts the execution of this logic so that a malicious `dbo` can't highjack this execution path.</span></span> <span data-ttu-id="08718-190">たとえば、悪意のある `dbo` が CDC テーブルのトリガーを追加すると、その後、`sp_replcmds` を呼び出すユーザーのコンテキスト (この場合はログ リーダー エージェント) でテーブルが実行されます。</span><span class="sxs-lookup"><span data-stu-id="08718-190">For example, a malicious `dbo` could add triggers on CDC tables which would then get executed under the context of the user calling `sp_replcmds`, in this case the logreader agent.</span></span>  <span data-ttu-id="08718-191">エージェントを実行しているアカウントの権限が高い場合、悪意のある `dbo` は自身の特権を引き上げます。</span><span class="sxs-lookup"><span data-stu-id="08718-191">If the account the agent is running under has higher privilege the malicious `dbo` could escalate his privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08718-192">参照</span><span class="sxs-lookup"><span data-stu-id="08718-192">See Also</span></span>  
 [<span data-ttu-id="08718-193">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="08718-193">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
