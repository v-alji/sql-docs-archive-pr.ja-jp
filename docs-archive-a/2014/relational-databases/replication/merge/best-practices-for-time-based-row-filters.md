---
title: 時間ベースの行フィルターの推奨事項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- best practices
ms.assetid: 773c5c62-fd44-44ab-9c6b-4257dbf8ffdb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccaafe71d4137fd4b31eec412c1e35595861bdd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630960"
---
# <a name="best-practices-for-time-based-row-filters"></a><span data-ttu-id="e96ba-102">時間ベースの行フィルターの推奨事項</span><span class="sxs-lookup"><span data-stu-id="e96ba-102">Best Practices for Time-Based Row Filters</span></span>
  <span data-ttu-id="e96ba-103">アプリケーションのユーザーは、テーブルに対して時間ベースのデータ サブセットを要求することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="e96ba-103">Users of applications often require a time-based subset of data from a table.</span></span> <span data-ttu-id="e96ba-104">たとえば、販売員が先週の注文データを必要としたり、イベント プランナーが次週のイベントのデータを必要とする場合などです。</span><span class="sxs-lookup"><span data-stu-id="e96ba-104">For instance, a salesperson might require data for orders in the last week, or an event planner might require data for events in the upcoming week.</span></span> <span data-ttu-id="e96ba-105">多くの場合、アプリケーションでは、`GETDATE()` 関数を含むクエリを使用して、この処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="e96ba-105">In many cases, applications use queries containing the `GETDATE()` function to accomplish this.</span></span> <span data-ttu-id="e96ba-106">次の行フィルター ステートメントについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="e96ba-106">Consider the following row filter statement:</span></span>  
  
```  
WHERE SalesPersonID = CONVERT(INT,HOST_NAME()) AND OrderDate >= (GETDATE()-6)  
```  
  
 <span data-ttu-id="e96ba-107">このタイプのフィルターを使用すると、マージ エージェントの実行時には、2 つの処理 (このフィルターに適合する行をサブスクライバーにレプリケートする処理と、このフィルターに適合しない行をサブスクライバー側でクリーンアップする処理) が常に発生すると推測するのが普通です</span><span class="sxs-lookup"><span data-stu-id="e96ba-107">With a filter of this type, it is usually assumed that two things always occur when the Merge Agent runs: rows that satisfy this filter are replicated to Subscribers; and rows that no longer satisfy this filter are cleaned up at Subscribers.</span></span> <span data-ttu-id="e96ba-108">(でのフィルター処理の詳細につい `HOST_NAME()` ては、「[パラメーター化](parameterized-filters-parameterized-row-filters.md)された行フィルター」を参照してください)。ただし、マージレプリケーションでは、そのデータに対して行フィルターを定義する方法に関係なく、前回の同期以降に変更されたデータのみをレプリケートおよびクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="e96ba-108">(For more information about filtering with `HOST_NAME()`, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).) However, merge replication only replicates and cleans up data that has changed since the last synchronization, regardless of how you define a row filter for that data.</span></span>  
  
 <span data-ttu-id="e96ba-109">マージ レプリケーションで行を処理するには、行内のデータが行フィルターに適合していて、前回の同期以降にデータが変更されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e96ba-109">For merge replication to process a row, the data in the row must satisfy the row filter, and it must have changed since the last synchronization.</span></span> <span data-ttu-id="e96ba-110">**SalesOrderHeader** テーブルでは、行が挿入されると **OrderDate** が入力されます。</span><span class="sxs-lookup"><span data-stu-id="e96ba-110">In the case of the **SalesOrderHeader** table, **OrderDate** is entered when a row is inserted.</span></span> <span data-ttu-id="e96ba-111">挿入はデータ変更なので、行は、期待どおりにサブスクライバーにレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="e96ba-111">Rows are replicated to the Subscriber as expected because the insert is a data change.</span></span> <span data-ttu-id="e96ba-112">ただし、フィルターに適合しなくなった行 (7 日前以前の注文の行) がサブスクライバー側にある場合、他のなんらかの理由で更新されていない限り、その行はサブスクライバーから削除されません。</span><span class="sxs-lookup"><span data-stu-id="e96ba-112">However, if there are rows at the Subscriber that no longer satisfy the filter (they are for orders older than seven days), they are not removed from the Subscriber unless they were updated for some other reason.</span></span>  
  
 <span data-ttu-id="e96ba-113">イベント プランナーの事例では、このようなフィルター処理に伴う問題がさらに強く浮き彫りになります。</span><span class="sxs-lookup"><span data-stu-id="e96ba-113">The case of the event planner further highlights the issue with this type of filtering.</span></span> <span data-ttu-id="e96ba-114">**Events** テーブルに対する次のフィルターについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="e96ba-114">Consider the following filter for an **Events** table:</span></span>  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND EventDate <= (GETDATE()+6)  
```  
  
 <span data-ttu-id="e96ba-115">イベントを格納しているテーブルでは、イベント当日のかなり前に挿入が行われることがあります。</span><span class="sxs-lookup"><span data-stu-id="e96ba-115">For a table that contains events, inserts might be made well ahead of the event date.</span></span> <span data-ttu-id="e96ba-116">次週のイベントの挿入が 1 か月前に行われ、別の理由で行が更新されなかった場合、行フィルターに適合していても、行はサブスクライバーにレプリケートされません。</span><span class="sxs-lookup"><span data-stu-id="e96ba-116">If the insert for an event in the coming week was made a month ago and the row was not updated for another reason, the row is not replicated to the Subscriber even if it satisfies the row filter.</span></span>  
  
 <span data-ttu-id="e96ba-117">また、パブリケーションの構成方法によって、マージ レプリケーションがフィルターを評価するタイミングはさまざまです。</span><span class="sxs-lookup"><span data-stu-id="e96ba-117">In addition, depending on how the publication is configured, merge replication evaluates filters at different times:</span></span>  
  
-   <span data-ttu-id="e96ba-118">パブリケーションが事前計算済みパーティションを使用している場合 (既定)、行の挿入時および更新時に、フィルターが評価されます。</span><span class="sxs-lookup"><span data-stu-id="e96ba-118">If a publication uses precomputed partitions (the default), filters are evaluated when a row is inserted or updated.</span></span>  
  
-   <span data-ttu-id="e96ba-119">パブリケーションが事前計算済みパーティションを使用していない場合、マージ エージェントの実行時に、フィルターが評価されます。</span><span class="sxs-lookup"><span data-stu-id="e96ba-119">If the publication does not use precomputed partitions, filters are evaluated when the Merge Agent runs.</span></span>  
  
 <span data-ttu-id="e96ba-120">事前計算済みパーティションの詳細については、[事前計算済みパーティションによるパラメーター化されたフィルター パフォーマンスの最適化](parameterized-filters-optimize-for-precomputed-partitions.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e96ba-120">For more information about precomputed partitions, see [Optimize Parameterized Filter Performance with Precomputed Partitions](parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="e96ba-121">フィルターが評価されるタイミングは、どのデータがフィルターに適合するかということに影響します。</span><span class="sxs-lookup"><span data-stu-id="e96ba-121">The time at which the filter is evaluated affects what data satisfies the filter.</span></span> <span data-ttu-id="e96ba-122">たとえば、パブリケーション側で事前計算済みパーティションが使用されており、2 日ごとにデータを同期する場合、販売員のデータのサブセットには、予期した日付よりも最高 2 日分古い行が含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e96ba-122">For example, if a publication uses precomputed partitions, and you synchronize data every two days, the subset of data for the salesperson could include rows up to two days older than expected.</span></span>  
  
## <a name="recommendations-for-using-time-based-row-filters"></a><span data-ttu-id="e96ba-123">時間ベースの行フィルターを使用するための推奨事項</span><span class="sxs-lookup"><span data-stu-id="e96ba-123">Recommendations for Using Time-Based Row Filters</span></span>  
 <span data-ttu-id="e96ba-124">次に示す方法は、時間に基づいてフィルター処理を行う際の強力でわかりやすいアプローチです。</span><span class="sxs-lookup"><span data-stu-id="e96ba-124">The following method provides a robust and straightforward approach to filtering based on time:</span></span>  
  
-   <span data-ttu-id="e96ba-125">テーブルに、データ型 `bit` の列を追加する。</span><span class="sxs-lookup"><span data-stu-id="e96ba-125">Add a column to the table of data type `bit`.</span></span> <span data-ttu-id="e96ba-126">この列は、行をレプリケートするかどうかを示すために使用します。</span><span class="sxs-lookup"><span data-stu-id="e96ba-126">This column is used to indicate whether a row should be replicated.</span></span>  
  
-   <span data-ttu-id="e96ba-127">時間ベースの列ではなく新しい列を参照する行フィルターを使用する。</span><span class="sxs-lookup"><span data-stu-id="e96ba-127">Use a row filter that references the new column rather than a time-based column.</span></span>  
  
-   <span data-ttu-id="e96ba-128">スケジュールでマージ エージェントが実行される前に列を更新する SQL Server エージェント ジョブ (または別のメカニズムでスケジュールされたジョブ) を作成する。</span><span class="sxs-lookup"><span data-stu-id="e96ba-128">Create a SQL Server Agent job (or a job scheduled through another mechanism) that updates the column before the Merge Agent is scheduled to run.</span></span>  
  
 <span data-ttu-id="e96ba-129">この方法を使用すると、`GETDATE()` などの時間ベースの方法を使用した場合の欠点を補い、パーティションに対してフィルターが評価されるタイミングを決める問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="e96ba-129">This approach addresses the shortcomings of using `GETDATE()` or another time-based method and avoids the problem of having to determine when filters are evaluated for partitions.</span></span> <span data-ttu-id="e96ba-130">**Events** テーブルの次の例を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="e96ba-130">Consider the following example of an **Events** table:</span></span>  
  
|<span data-ttu-id="e96ba-131">**EventID**</span><span class="sxs-lookup"><span data-stu-id="e96ba-131">**EventID**</span></span>|<span data-ttu-id="e96ba-132">**EventName**</span><span class="sxs-lookup"><span data-stu-id="e96ba-132">**EventName**</span></span>|<span data-ttu-id="e96ba-133">**EventCoordID**</span><span class="sxs-lookup"><span data-stu-id="e96ba-133">**EventCoordID**</span></span>|<span data-ttu-id="e96ba-134">**EventDate**</span><span class="sxs-lookup"><span data-stu-id="e96ba-134">**EventDate**</span></span>|<span data-ttu-id="e96ba-135">**[レプリケート]**</span><span class="sxs-lookup"><span data-stu-id="e96ba-135">**Replicate**</span></span>|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|<span data-ttu-id="e96ba-136">1</span><span class="sxs-lookup"><span data-stu-id="e96ba-136">1</span></span>|<span data-ttu-id="e96ba-137">Reception</span><span class="sxs-lookup"><span data-stu-id="e96ba-137">Reception</span></span>|<span data-ttu-id="e96ba-138">112</span><span class="sxs-lookup"><span data-stu-id="e96ba-138">112</span></span>|<span data-ttu-id="e96ba-139">2006-10-04</span><span class="sxs-lookup"><span data-stu-id="e96ba-139">2006-10-04</span></span>|<span data-ttu-id="e96ba-140">1</span><span class="sxs-lookup"><span data-stu-id="e96ba-140">1</span></span>|  
|<span data-ttu-id="e96ba-141">2</span><span class="sxs-lookup"><span data-stu-id="e96ba-141">2</span></span>|<span data-ttu-id="e96ba-142">夕食</span><span class="sxs-lookup"><span data-stu-id="e96ba-142">Dinner</span></span>|<span data-ttu-id="e96ba-143">112</span><span class="sxs-lookup"><span data-stu-id="e96ba-143">112</span></span>|<span data-ttu-id="e96ba-144">2006-10-10</span><span class="sxs-lookup"><span data-stu-id="e96ba-144">2006-10-10</span></span>|<span data-ttu-id="e96ba-145">0</span><span class="sxs-lookup"><span data-stu-id="e96ba-145">0</span></span>|  
|<span data-ttu-id="e96ba-146">3</span><span class="sxs-lookup"><span data-stu-id="e96ba-146">3</span></span>|<span data-ttu-id="e96ba-147">Party</span><span class="sxs-lookup"><span data-stu-id="e96ba-147">Party</span></span>|<span data-ttu-id="e96ba-148">112</span><span class="sxs-lookup"><span data-stu-id="e96ba-148">112</span></span>|<span data-ttu-id="e96ba-149">2006-10-11</span><span class="sxs-lookup"><span data-stu-id="e96ba-149">2006-10-11</span></span>|<span data-ttu-id="e96ba-150">0</span><span class="sxs-lookup"><span data-stu-id="e96ba-150">0</span></span>|  
|<span data-ttu-id="e96ba-151">4</span><span class="sxs-lookup"><span data-stu-id="e96ba-151">4</span></span>|<span data-ttu-id="e96ba-152">Wedding</span><span class="sxs-lookup"><span data-stu-id="e96ba-152">Wedding</span></span>|<span data-ttu-id="e96ba-153">112</span><span class="sxs-lookup"><span data-stu-id="e96ba-153">112</span></span>|<span data-ttu-id="e96ba-154">2006-10-12</span><span class="sxs-lookup"><span data-stu-id="e96ba-154">2006-10-12</span></span>|<span data-ttu-id="e96ba-155">0</span><span class="sxs-lookup"><span data-stu-id="e96ba-155">0</span></span>|  
  
 <span data-ttu-id="e96ba-156">このテーブルの行フィルターは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e96ba-156">The row filter for this table would then look like this:</span></span>  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND Replicate = 1  
```  
  
 <span data-ttu-id="e96ba-157">SQL Server エージェント ジョブは、各マージ エージェントを実行する前に、次のような [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e96ba-157">The SQL Server Agent job could execute [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements similar to the following before each Merge Agent run:</span></span>  
  
```  
UPDATE Events SET Replicate = 0 WHERE Replicate = 1  
GO  
UPDATE Events SET Replicate = 1 WHERE EventDate <= GETDATE()+6  
GO  
```  
  
 <span data-ttu-id="e96ba-158">1 行目では、 **Replicate** 列を **0**に再設定しています。2 行目では、今後 7 日以内に発生するイベントの列を **1** に設定しています。</span><span class="sxs-lookup"><span data-stu-id="e96ba-158">The first line resets the **Replicate** column to **0**, and the second line sets the column to **1** for events that occur in the next seven days.</span></span> <span data-ttu-id="e96ba-159">この [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントが 2006 年 10 月 7 日に実行されると、テーブルが次のように更新されます。</span><span class="sxs-lookup"><span data-stu-id="e96ba-159">If this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement runs on 10/07/2006, the table is updated to:</span></span>  
  
|<span data-ttu-id="e96ba-160">**EventID**</span><span class="sxs-lookup"><span data-stu-id="e96ba-160">**EventID**</span></span>|<span data-ttu-id="e96ba-161">**EventName**</span><span class="sxs-lookup"><span data-stu-id="e96ba-161">**EventName**</span></span>|<span data-ttu-id="e96ba-162">**EventCoordID**</span><span class="sxs-lookup"><span data-stu-id="e96ba-162">**EventCoordID**</span></span>|<span data-ttu-id="e96ba-163">**EventDate**</span><span class="sxs-lookup"><span data-stu-id="e96ba-163">**EventDate**</span></span>|<span data-ttu-id="e96ba-164">**[レプリケート]**</span><span class="sxs-lookup"><span data-stu-id="e96ba-164">**Replicate**</span></span>|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|<span data-ttu-id="e96ba-165">1</span><span class="sxs-lookup"><span data-stu-id="e96ba-165">1</span></span>|<span data-ttu-id="e96ba-166">Reception</span><span class="sxs-lookup"><span data-stu-id="e96ba-166">Reception</span></span>|<span data-ttu-id="e96ba-167">112</span><span class="sxs-lookup"><span data-stu-id="e96ba-167">112</span></span>|<span data-ttu-id="e96ba-168">2006-10-04</span><span class="sxs-lookup"><span data-stu-id="e96ba-168">2006-10-04</span></span>|<span data-ttu-id="e96ba-169">0</span><span class="sxs-lookup"><span data-stu-id="e96ba-169">0</span></span>|  
|<span data-ttu-id="e96ba-170">2</span><span class="sxs-lookup"><span data-stu-id="e96ba-170">2</span></span>|<span data-ttu-id="e96ba-171">夕食</span><span class="sxs-lookup"><span data-stu-id="e96ba-171">Dinner</span></span>|<span data-ttu-id="e96ba-172">112</span><span class="sxs-lookup"><span data-stu-id="e96ba-172">112</span></span>|<span data-ttu-id="e96ba-173">2006-10-10</span><span class="sxs-lookup"><span data-stu-id="e96ba-173">2006-10-10</span></span>|<span data-ttu-id="e96ba-174">1</span><span class="sxs-lookup"><span data-stu-id="e96ba-174">1</span></span>|  
|<span data-ttu-id="e96ba-175">3</span><span class="sxs-lookup"><span data-stu-id="e96ba-175">3</span></span>|<span data-ttu-id="e96ba-176">Party</span><span class="sxs-lookup"><span data-stu-id="e96ba-176">Party</span></span>|<span data-ttu-id="e96ba-177">112</span><span class="sxs-lookup"><span data-stu-id="e96ba-177">112</span></span>|<span data-ttu-id="e96ba-178">2006-10-11</span><span class="sxs-lookup"><span data-stu-id="e96ba-178">2006-10-11</span></span>|<span data-ttu-id="e96ba-179">1</span><span class="sxs-lookup"><span data-stu-id="e96ba-179">1</span></span>|  
|<span data-ttu-id="e96ba-180">4</span><span class="sxs-lookup"><span data-stu-id="e96ba-180">4</span></span>|<span data-ttu-id="e96ba-181">Wedding</span><span class="sxs-lookup"><span data-stu-id="e96ba-181">Wedding</span></span>|<span data-ttu-id="e96ba-182">112</span><span class="sxs-lookup"><span data-stu-id="e96ba-182">112</span></span>|<span data-ttu-id="e96ba-183">2006-10-12</span><span class="sxs-lookup"><span data-stu-id="e96ba-183">2006-10-12</span></span>|<span data-ttu-id="e96ba-184">1</span><span class="sxs-lookup"><span data-stu-id="e96ba-184">1</span></span>|  
  
 <span data-ttu-id="e96ba-185">次週のイベントは、レプリケート準備済みとしてフラグが付けられています。</span><span class="sxs-lookup"><span data-stu-id="e96ba-185">The events for the next week are now flagged as being ready to replicate.</span></span> <span data-ttu-id="e96ba-186">イベント コーディネーター 112 が使用するサブスクリプションでマージ エージェントが次に実行されると、1 行目以外の行がサブスクライバーにダウンロードされ、1 行目がサブスクライバーから削除されます。</span><span class="sxs-lookup"><span data-stu-id="e96ba-186">The next time the Merge Agent runs for the subscription that event coordinator 112 uses, rows 2, 3, and 4 will be downloaded to the Subscriber and row 1 will be removed from the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e96ba-187">参照</span><span class="sxs-lookup"><span data-stu-id="e96ba-187">See Also</span></span>  
 <span data-ttu-id="e96ba-188">[GETDATE (Transact-SQL)](/sql/t-sql/functions/getdate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e96ba-188">[GETDATE &#40;Transact-SQL&#41;](/sql/t-sql/functions/getdate-transact-sql) </span></span>  
 <span data-ttu-id="e96ba-189">[ジョブの実装](../../../ssms/agent/implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="e96ba-189">[Implement Jobs](../../../ssms/agent/implement-jobs.md) </span></span>  
 [<span data-ttu-id="e96ba-190">パラメーター化された行フィルター</span><span class="sxs-lookup"><span data-stu-id="e96ba-190">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  
