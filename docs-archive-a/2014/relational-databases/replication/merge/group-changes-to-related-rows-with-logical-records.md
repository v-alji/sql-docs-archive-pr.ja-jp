---
title: 論理レコードによる関連行への変更のグループ化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ad76799c-4486-4b98-9705-005433041321
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 433e0edbe83d102e6002bd133f967f27a236f66e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630959"
---
# <a name="group-changes-to-related-rows-with-logical-records"></a><span data-ttu-id="e5d68-102">論理レコードによる関連行への変更のグループ化</span><span class="sxs-lookup"><span data-stu-id="e5d68-102">Group Changes to Related Rows with Logical Records</span></span>
  
> [!NOTE]
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]

 <span data-ttu-id="e5d68-103">マージ レプリケーションの既定の動作では、データの変更は行ごとに処理されます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-103">By default, merge replication processes data changes on a row-by-row basis.</span></span> <span data-ttu-id="e5d68-104">この動作は多くの場合に適切ですが、アプリケーションによっては、関連する行を 1 つの単位として処理することが必要です。</span><span class="sxs-lookup"><span data-stu-id="e5d68-104">In many circumstances this is appropriate, but for some applications, it is essential that related rows be processed as a unit.</span></span> <span data-ttu-id="e5d68-105">マージ レプリケーションの論理レコード機能を使用すると、異なるテーブルの関連する行の間にリレーションシップを定義し、それらの行を 1 つの単位として処理できます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-105">The logical records feature of merge replication allows you to define a relationship between related rows in different tables so that the rows are processed as a unit.</span></span>

> [!NOTE]
>  <span data-ttu-id="e5d68-106">論理レコード機能は、単独で使用することも、結合フィルターと組み合わせて使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-106">The logical records feature can be used alone or in conjunction with join filters.</span></span> <span data-ttu-id="e5d68-107">結合フィルターの詳細については、「 [Join Filters](join-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-107">For more information about join filters, see [Join Filters](join-filters.md).</span></span> <span data-ttu-id="e5d68-108">論理レコードを使用するには、パブリケーションの互換性レベルが少なくとも 90 RTM である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-108">To use logical records, the compatibility level of the publication must be at least 90RTM.</span></span>

 <span data-ttu-id="e5d68-109">以下の 3 つの関連テーブルについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-109">Consider these three related tables:</span></span>

 <span data-ttu-id="e5d68-110">![列名のみを持つ 3 つのテーブルの論理レコード](../media/logical-records-01.gif "列名のみを持つ 3 つのテーブルの論理レコード")</span><span class="sxs-lookup"><span data-stu-id="e5d68-110">![Three table logical record, with column names only](../media/logical-records-01.gif "Three table logical record, with column names only")</span></span>

 <span data-ttu-id="e5d68-111">**Customers** テーブルは、このリレーションシップの親テーブルであり、主キー列 **CustID**を持ちます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-111">The **Customers** table is the parent table in this relationship and has a primary key column **CustID**.</span></span> <span data-ttu-id="e5d68-112">**Orders** テーブルは、主キー列 **OrderID**を持ちます。また、 **Customers** テーブルの **CustID** 列を参照する **CustID** 列に、外部キー制約が設定されています。</span><span class="sxs-lookup"><span data-stu-id="e5d68-112">The **Orders** table has a primary key column **OrderID**, with a foreign key constraint on the **CustID** column that references the **CustID** column in the **Customers** table.</span></span> <span data-ttu-id="e5d68-113">同様に、 **OrderItems** テーブルは主キー列 **OrderItemID**を持ちます。また、 **Orders** テーブルの **OrderID** 列を参照する **OrderID** 列に、外部キー制約が設定されています。</span><span class="sxs-lookup"><span data-stu-id="e5d68-113">Similarly, the **OrderItems** table has a primary key column **OrderItemID**, with a foreign key constraint on the **OrderID** column that references the **OrderID** column in the **Orders** table.</span></span>

 <span data-ttu-id="e5d68-114">この例の論理レコードは、単一の **CustID** 値に関連付けられている **Orders** テーブルのすべての行と、 **Orders** テーブル内の行に関連付けられている **OrderItems** テーブルのすべての行で構成されます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-114">In this example, a logical record consists of all the rows in the **Orders** table that are related to a single **CustID** value and all of the rows in the **OrderItems** table that are related to those rows in the **Orders** table.</span></span> <span data-ttu-id="e5d68-115">次の図は、Customer2 の論理レコードに含まれる、3 つのテーブルのすべての行を示しています。</span><span class="sxs-lookup"><span data-stu-id="e5d68-115">This diagram shows all the rows in the three tables that are in the logical record for Customer2:</span></span>

 <span data-ttu-id="e5d68-116">![値を持つ 3 つのテーブルの論理レコード](../media/logical-records-02.gif "値を持つ 3 つのテーブルの論理レコード")</span><span class="sxs-lookup"><span data-stu-id="e5d68-116">![Three table logical record with values](../media/logical-records-02.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="e5d68-117">アーティクル間で論理レコード リレーションシップを定義するには、「 [マージテーブル記事間の論理レコード関係を定義する](../publish/define-a-logical-record-relationship-between-merge-table-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-117">To define a logical record relationship between articles, see [Define a Logical Record Relationship Between Merge Table Articles](../publish/define-a-logical-record-relationship-between-merge-table-articles.md).</span></span>

## <a name="benefits-of-logical-records"></a><span data-ttu-id="e5d68-118">論理レコードの利点</span><span class="sxs-lookup"><span data-stu-id="e5d68-118">Benefits of Logical Records</span></span>
 <span data-ttu-id="e5d68-119">論理レコード機能には、2 つの主な利点があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-119">The logical records feature has two primary benefits:</span></span>

-   <span data-ttu-id="e5d68-120">データ変更が 1 つの単位として適用されます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-120">Application of data changes as a unit.</span></span>

-   <span data-ttu-id="e5d68-121">競合の検出および解決が、複数のテーブルの複数の行で同時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-121">The detection and resolution of conflicts simultaneously on multiple rows from multiple tables.</span></span>

### <a name="the-application-of-changes-as-a-unit"></a><span data-ttu-id="e5d68-122">変更を 1 つの単位として適用</span><span class="sxs-lookup"><span data-stu-id="e5d68-122">The Application of Changes As a Unit</span></span>
 <span data-ttu-id="e5d68-123">論理レコードを使用している場合、マージ処理が接続の切断などで中断されると、関連するレプリケートされた変更の部分的に完了したセットは、ロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-123">If merge processing is interrupted, such as in the case of a dropped connection, the partially completed set of related replicated changes is rolled back if logical records are used.</span></span> <span data-ttu-id="e5d68-124">たとえば、サブスクライバーが **OrderID** = 6 で新しい注文を追加し、 **OrderItems** テーブルに **OrderID** = 6 用の新しい 2 つの行を **OrderItemID** = 10 および **OrderItemID** = 11 で追加したとします。</span><span class="sxs-lookup"><span data-stu-id="e5d68-124">For example, consider the case where a Subscriber adds a new order with **OrderID** = 6 and two new rows in the **OrderItems** table with **OrderItemID** = 10 and **OrderItemID** = 11 for **OrderID** = 6.</span></span>

 <span data-ttu-id="e5d68-125">![値を持つ 3 つのテーブルの論理レコード](../media/logical-records-04.gif "値を持つ 3 つのテーブルの論理レコード")</span><span class="sxs-lookup"><span data-stu-id="e5d68-125">![Three table logical record with values](../media/logical-records-04.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="e5d68-126">**OrderID** = 6 の **Orders** 行の処理を完了後、 **OrderItems** 10 および 11 の処理が完了するまでの間にレプリケーション処理が中断されると、論理レコードを使用していない場合、 **OrderID** = 6 の **OrderTotal** 値は、 **OrderItems** 行の **OrderAmount** 値の合計とは一致しません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-126">If the replication process is interrupted after the **Orders** row for **OrderID** = 6 is complete, but before the **OrderItems** 10 and 11 are completed, and logical records are not used, the **OrderTotal** value for **OrderID** = 6 will not be consistent with the sum of the **OrderAmount** values for the **OrderItems** rows.</span></span> <span data-ttu-id="e5d68-127">論理レコードを使用している場合、 **OrderID** = 6 の **Orders** 行は、関連する **OrderItems** の変更がレプリケートされるまで、コミットされません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-127">If logical records are used, the **Orders** row for **OrderID** = 6 is not committed until the related **OrderItems** changes are replicated.</span></span>

 <span data-ttu-id="e5d68-128">別のシナリオで、論理レコードを使用していて、だれかがマージ処理による変更の適用中にテーブルに対してクエリを実行した場合、そのユーザーには、変更がすべて完了するまで、部分的にレプリケートされた変更は表示されません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-128">In a different scenario, if logical records are used, and someone is querying tables when the merge process is applying changes, the user will not see the partially replicated changes until they are all complete.</span></span> <span data-ttu-id="e5d68-129">たとえば、レプリケーション処理で **OrderID** = 6 の Orders 行をアップロードしても、 **OrderItems** 行がレプリケートされる前にユーザーがテーブルに対してクエリを実行した場合、 **OrderTotal** 値は、 **OrderAmount** 値の合計とは一致しません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-129">For example, the replication process has uploaded the Orders row for **OrderID** = 6, but a user queries the tables before the replication process has replicated the **OrderItems** rows, the **OrderTotal** value would not be the same as the sum of the **OrderAmount** values.</span></span> <span data-ttu-id="e5d68-130">論理レコードを使用している場合、 **Orders** 行は、 **OrderItems** 行の処理が完了し、トランザクションが 1 つの単位としてコミットされるまで表示されません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-130">If logical records are used, the **Orders** row would not be visible until the **OrderItems** rows are complete and the transaction has been committed as a unit.</span></span>

### <a name="the-application-of-conflict-handling-to-more-than-one-table"></a><span data-ttu-id="e5d68-131">複数のテーブルへの競合処理の適用</span><span class="sxs-lookup"><span data-stu-id="e5d68-131">The Application of Conflict Handling to More Than One Table</span></span>
 <span data-ttu-id="e5d68-132">2 つのサブスクライバーが上記のデータセットを保持しているケースを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-132">Consider the case where two Subscribers have the data set above:</span></span>

-   <span data-ttu-id="e5d68-133">最初のサブスクライバーのユーザーは、 **OrderItemID** 5 の **OrderAmount** を 100 から 150 に変更し、 **OrderID** 3 の **OrderTotal** を 200 から 250 に変更します。</span><span class="sxs-lookup"><span data-stu-id="e5d68-133">A user at the first Subscriber changes the **OrderAmount** of **OrderItemID** 5 from 100 to 150 and the **OrderTotal** of **OrderID** 3 from 200 to 250.</span></span>

-   <span data-ttu-id="e5d68-134">2 番目のサブスクライバーのユーザーは、 **OrderItemID** 6 の **OrderAmount** を 25 から 125 に変更し、 **OrderID** 3 の **OrderTotal** を 200 から 300 に変更します。</span><span class="sxs-lookup"><span data-stu-id="e5d68-134">A user at the second Subscriber changes the **OrderAmount** of **OrderItemID** 6 from 25 to 125 and the **OrderTotal** of **OrderID** 3 from 200 to 300.</span></span>

 <span data-ttu-id="e5d68-135">これらの変更が論理レコードを使用せずにレプリケートされると、異なる **OrderTotal** の値が競合し、それらのうちのいずれかのみがレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-135">If these changes are replicated without using logical records, the different **OrderTotal** values would result in a conflict and only one of them would be replicated.</span></span> <span data-ttu-id="e5d68-136">しかし、 **OrderItems** テーブルの競合してない変更は、競合することなくレプリケートされます。結果として、最終的な **OrderTotal** 値は、 **OrderItems** 行との一貫性を持たない状態になります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-136">But the non-conflicting changes in the **OrderItems** table would be replicated without conflict, leaving the final **OrderTotal** values in an inconsistent state with respect to the **OrderItems** rows.</span></span> <span data-ttu-id="e5d68-137">このシナリオで論理レコードを使用した場合、 **Orders** テーブルの失われた変更に関連する **OrderItems** の変更もロールバックされ、最終的な **OrderTotal** 値は **OrderItems** 行の正確な集計になります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-137">If logical records are used in this scenario, the **OrderItems** change associated with the losing **Orders** table change would also be rolled back, and the final **OrderTotal** value would be an accurate summary of the **OrderItems** rows.</span></span>

 <span data-ttu-id="e5d68-138">論理レコードが使用される場合の競合の検出と解決に関する選択肢については、「[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md)」 (論理レコードの競合の検出および解決) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-138">For more information about options related to conflict detection and resolution with logical records, see [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>

## <a name="considerations-for-using-logical-records"></a><span data-ttu-id="e5d68-139">論理レコードの使用に関する注意点</span><span class="sxs-lookup"><span data-stu-id="e5d68-139">Considerations for Using Logical Records</span></span>
 <span data-ttu-id="e5d68-140">論理レコードを使用するときは、以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-140">Keep the following considerations in mind when using logical records.</span></span>

### <a name="general-considerations"></a><span data-ttu-id="e5d68-141">一般的な考慮事項</span><span class="sxs-lookup"><span data-stu-id="e5d68-141">General Considerations</span></span>

-   <span data-ttu-id="e5d68-142">論理レコード内のテーブルは可能な限り少なくすることをお勧めします。テーブル数は 5 つ以下にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5d68-142">It is recommended that you keep the number of tables in a logical record as low as possible; five tables or less is recommended.</span></span>

-   <span data-ttu-id="e5d68-143">論理レコードでは、次のデータ型の列は参照できません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-143">Logical records cannot reference columns with any of the following data types:</span></span>

    -   <span data-ttu-id="e5d68-144">`varchar(max)` および `nvarchar(max)`</span><span class="sxs-lookup"><span data-stu-id="e5d68-144">`varchar(max)` and `nvarchar(max)`</span></span>

    -   `varbinary(max)`

    -   <span data-ttu-id="e5d68-145">`text` および `ntext`</span><span class="sxs-lookup"><span data-stu-id="e5d68-145">`text` and `ntext`</span></span>

    -   `image`

    -   `XML`

    -   `UDT`

-   <span data-ttu-id="e5d68-146">パブリッシュされたテーブルの外部キーのリレーションシップを CASCADE オプションで定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-146">Foreign key relationships in published tables cannot be defined with the CASCADE option.</span></span> <span data-ttu-id="e5d68-147">詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)」および「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-147">For more information, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) and [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>

-   <span data-ttu-id="e5d68-148">論理リレーション句で使用されている列は更新できません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-148">You cannot update any columns that are used in the logical relation clause.</span></span>

-   <span data-ttu-id="e5d68-149">ビジネス ロジック ハンドラーまたはカスタム競合回避モジュールによるカスタム競合解決は、論理レコードに含まれているアーティクルについてはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-149">Custom conflict resolution with business logic handlers or custom resolvers is not supported for articles that are included in a logical record.</span></span>

-   <span data-ttu-id="e5d68-150">パラメーター化されたフィルターを含むパブリケーションで論理レコードが使用されている場合、各サブスクライバーをそのパーティションのスナップショットで初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-150">If logical records are used in a publication that includes parameterized filters, you must initialize each Subscriber with a snapshot for its partition.</span></span> <span data-ttu-id="e5d68-151">サブスクライバーを別の方法で初期化した場合、マージ エージェントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="e5d68-151">If you initialize a Subscriber with another method, the Merge Agent will fail.</span></span> <span data-ttu-id="e5d68-152">詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-152">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>

-   <span data-ttu-id="e5d68-153">論理レコードに関連する競合は、競合表示モジュールに表示されません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-153">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="e5d68-154">これらの競合に関する情報を表示するには、レプリケーション ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5d68-154">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="e5d68-155">詳細については、「[マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)](../view-conflict-information-for-merge-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-155">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>

### <a name="publication-settings"></a><span data-ttu-id="e5d68-156">パブリケーションの設定</span><span class="sxs-lookup"><span data-stu-id="e5d68-156">Publication Settings</span></span>

-   <span data-ttu-id="e5d68-157">パブリケーションの互換性レベルは 90 RTM 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-157">The publication must have a compatibility level of 90RTM or greater.</span></span> <span data-ttu-id="e5d68-158">詳細については、「[Replication Backward Compatibility](../replication-backward-compatibility.md)」 (レプリケーションの下位互換性) の「Publication Compatibility Level」(パブリケーションの互換性レベル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-158">For more information, see the "Publication Compatibility Level" section of [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>

-   <span data-ttu-id="e5d68-159">パブリケーションではネイティブ スナップショット モードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-159">The publication must use native snapshot mode.</span></span> <span data-ttu-id="e5d68-160">論理レコードをサポートしない [!INCLUDE[ssEW](../../../includes/ssew-md.md)]にレプリケートしている場合を除き、これが既定になります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-160">This is the default unless you are replicating to [!INCLUDE[ssEW](../../../includes/ssew-md.md)], which does not support logical records.</span></span>

-   <span data-ttu-id="e5d68-161">パブリケーションでは Web 同期は許可されません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-161">The publication cannot allow Web synchronization.</span></span> <span data-ttu-id="e5d68-162">Web 同期の詳細については、「 [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-162">For more information about Web synchronization, see [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md).</span></span>

-   <span data-ttu-id="e5d68-163">フィルター選択されたパブリケーションで論理レコードを使用するには</span><span class="sxs-lookup"><span data-stu-id="e5d68-163">In order to use logical records on a filtered publication:</span></span>

    -   <span data-ttu-id="e5d68-164">事前計算済みパーティションも使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-164">Precomputed partitions must also be used.</span></span> <span data-ttu-id="e5d68-165">事前計算済みパーティションの要件は、論理レコードにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-165">The requirements of precomputed partitions also apply to logical records.</span></span> <span data-ttu-id="e5d68-166">詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-166">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>

    -   <span data-ttu-id="e5d68-167">重複しないパラメーター化されたフィルターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-167">You cannot use nonoverlapping parameterized filters.</span></span> <span data-ttu-id="e5d68-168">詳細については、「 [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md)」の「[パーティションのオプション] の設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-168">For more information, see the "Setting 'partition options'" section of [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>

-   <span data-ttu-id="e5d68-169">パブリケーションで結合フィルターを使用する場合、論理レコード リレーションシップに含まれるすべての結合フィルターに対し、 **join unique key** プロパティを **true** に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-169">If the publication uses join filters, the **join unique key** property must be set to **true** for all join filters that are involved in logical record relationships.</span></span> <span data-ttu-id="e5d68-170">詳しくは、「 [Join Filters](join-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e5d68-170">For more information, see [Join Filters](join-filters.md).</span></span>

### <a name="relationships-between-tables"></a><span data-ttu-id="e5d68-171">テーブル間のリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="e5d68-171">Relationships Between Tables</span></span>

-   <span data-ttu-id="e5d68-172">論理レコードを介して関連付けられたテーブルは、主キーと外部キーのリレーションシップを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-172">Tables related through logical records must have a primary key-foreign key relationship.</span></span>

-   <span data-ttu-id="e5d68-173">NOT FOR REPLICATION オプションは外部キー制約には設定できません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-173">The NOT FOR REPLICATION option cannot be set for foreign key constraints.</span></span>

-   <span data-ttu-id="e5d68-174">子テーブルは親テーブルを 1 つだけ持つことができます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-174">Child tables can have only one parent table.</span></span>

     <span data-ttu-id="e5d68-175">たとえば、データベース追跡の Class と Students が、次のような設計になっているとします。</span><span class="sxs-lookup"><span data-stu-id="e5d68-175">For example, a database tracking classes and students might have a design similar to:</span></span>

     <span data-ttu-id="e5d68-176">![複数の親テーブルを持つ子テーブル](../media/logical-records-03.gif "複数の親テーブルを持つ子テーブル")</span><span class="sxs-lookup"><span data-stu-id="e5d68-176">![Child table with more than one parent table](../media/logical-records-03.gif "Child table with more than one parent table")</span></span>

     <span data-ttu-id="e5d68-177">論理レコードを使用して、このリレーションシップの 3 つのテーブルを表すことはできません。これは、 **ClassMembers** の行が単一の主キー行と関連付けられていないからです。</span><span class="sxs-lookup"><span data-stu-id="e5d68-177">You cannot use a logical record to represent the three tables in this relationship, because the rows in **ClassMembers** are not associated with a single primary key row.</span></span> <span data-ttu-id="e5d68-178">テーブル **Classes** および **ClassMembers** で論理レコードを形成することは可能であり、テーブル **ClassMembers** および **Students**で論理レコードを形成することも可能です。しかし、3 つのテーブルすべてで論理レコードを形成することはできません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-178">The tables **Classes** and **ClassMembers** could still form a logical record, as could the tables **ClassMembers** and **Students**, but not all three.</span></span>

-   <span data-ttu-id="e5d68-179">パブリケーションに循環結合フィルター リレーションシップを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-179">The publication cannot contain circular join filter relationships.</span></span>

     <span data-ttu-id="e5d68-180">**Customers**テーブル、 **Orders**テーブル、および **OrderItems**テーブルの例でいうと、 **Orders** テーブルに **OrderItems** テーブルを参照する外部キー制約もある場合、論理レコードは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e5d68-180">Using the example with the tables **Customers**, **Orders**, and **OrderItems**, you could not use logical records if the **Orders** table also had a foreign key constraint that referenced the **OrderItems** table.</span></span>

## <a name="performance-implications-of-logical-records"></a><span data-ttu-id="e5d68-181">論理レコードのパフォーマンスへの影響</span><span class="sxs-lookup"><span data-stu-id="e5d68-181">Performance implications of logical records</span></span>
 <span data-ttu-id="e5d68-182">論理レコード機能を使用すると、パフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-182">The logical record feature does come with a performance cost.</span></span> <span data-ttu-id="e5d68-183">論理レコードを使用しない場合、レプリケーション エージェントは特定のアーティクルに対するすべての変更を同時に処理できます。また、変更は行ごとに適用されるため、変更を適用するために必要なロックおよびトランザクション ログの要件は、最小限になります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-183">If logical records are not used, the replication agent can process all of the changes for a given article at the same time, and because the changes are applied in a row-by-row fashion, the locking and transaction log requirements necessary for applying the changes are minimal.</span></span>

 <span data-ttu-id="e5d68-184">論理レコードを使用する場合、マージ エージェントは各論理レコード全体に対する変更をまとめて処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d68-184">If logical records are used, the Merge Agent must process the changes for each entire logical record together.</span></span> <span data-ttu-id="e5d68-185">これにより、マージ エージェントが行をレプリケートするためにかかる時間に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="e5d68-185">This has an effect on the amount of time it takes the Merge Agent to replicate the rows.</span></span> <span data-ttu-id="e5d68-186">さらに、エージェントは各論理レコードに対して個別にトランザクションを開くため、ロックの要件が増大します。</span><span class="sxs-lookup"><span data-stu-id="e5d68-186">Additionally, because the agent opens a separate transaction for each logical record, locking requirements can increase.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5d68-187">参照</span><span class="sxs-lookup"><span data-stu-id="e5d68-187">See Also</span></span>
 [<span data-ttu-id="e5d68-188">マージ レプリケーションのアーティクル オプション</span><span class="sxs-lookup"><span data-stu-id="e5d68-188">Article Options for Merge Replication</span></span>](article-options-for-merge-replication.md)


