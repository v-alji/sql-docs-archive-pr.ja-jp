---
title: 結果更新の規則 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- updating query results
- Query Designer [SQL Server], Results pane
- Results pane
ms.assetid: de131ef0-ccbd-446f-9400-b93c7b8fa537
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5cc6befc6571f29be95b176f8de6d7dcfaed9108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719340"
---
# <a name="rules-for-updating-results-visual-database-tools"></a><span data-ttu-id="bd624-102">結果更新の規則 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="bd624-102">Rules for Updating Results (Visual Database Tools)</span></span>
  <span data-ttu-id="bd624-103">多くの場合、 [結果ペイン](visual-database-tools.md)に表示されている結果セットは更新できます。</span><span class="sxs-lookup"><span data-stu-id="bd624-103">In many cases, you can update the result set displayed in the [Results Pane](visual-database-tools.md).</span></span> <span data-ttu-id="bd624-104">ただし、更新できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bd624-104">However, in some cases you cannot.</span></span>  
  
 <span data-ttu-id="bd624-105">結果を更新するには、通常、 [クエリおよびビュー デザイナー](query-and-view-designer-tools-visual-database-tools.md) がテーブル内の行を一意に識別するのに十分な情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="bd624-105">In general, in order to update results, the [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) must have sufficient information to uniquely identify the row in the table.</span></span> <span data-ttu-id="bd624-106">たとえば、クエリの出力リストに主キーが含まれている場合などが該当します。</span><span class="sxs-lookup"><span data-stu-id="bd624-106">An example is if the query includes a primary key in the output list.</span></span> <span data-ttu-id="bd624-107">さらに、データベースを更新するためのアクセス許可も必要です。</span><span class="sxs-lookup"><span data-stu-id="bd624-107">In addition, you must have sufficient permission to update the database.</span></span>  
  
 <span data-ttu-id="bd624-108">クエリがビューに基づいている場合は、更新できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bd624-108">If your query is based on a view, you might be able to update it.</span></span> <span data-ttu-id="bd624-109">この場合も同じガイドラインが適用されますが、ビュー自体に対してだけでなく、ビューの基になるテーブルにも適用される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="bd624-109">The same guidelines apply, except that they apply to the underlying tables in the view, not just to the view itself.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd624-110">クエリおよびビュー デザイナーは、ビューに基づく結果セットを更新できるかどうかを事前に判断できません。</span><span class="sxs-lookup"><span data-stu-id="bd624-110">The Query and View Designer cannot determine in advance whether you can update a result set based on a view.</span></span> <span data-ttu-id="bd624-111">このため、更新できない場合でも、すべてのビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd624-111">Therefore, it displays all views, even though you might not be able to update them.</span></span>  
  
 <span data-ttu-id="bd624-112">次の表は、結果ペインに表示されたクエリの結果を更新できる場合とできない場合の例をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="bd624-112">The following table summarizes specific instances in which you might and might not be able to update query results in the Results pane.</span></span> <span data-ttu-id="bd624-113">多くの場合、クエリの結果を更新できるかどうかは、使用しているデータベースによって決まります。</span><span class="sxs-lookup"><span data-stu-id="bd624-113">In many cases, the database you are using dictates whether you can update query results.</span></span>  
  
|<span data-ttu-id="bd624-114">クエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-114">Query</span></span>|<span data-ttu-id="bd624-115">結果更新の可/不可</span><span class="sxs-lookup"><span data-stu-id="bd624-115">Can results be updated?</span></span>|  
|-----------|-----------------------------|  
|<span data-ttu-id="bd624-116">出力リストに主キーを持つ、単一のテーブルに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-116">Query based on one table with primary key in the output list</span></span>|<span data-ttu-id="bd624-117">可 (下のリストを除く)。</span><span class="sxs-lookup"><span data-stu-id="bd624-117">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="bd624-118">一意のインデックスおよび主キーを持たないテーブルに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-118">Query based on a table with no unique index and without a primary key</span></span>|<span data-ttu-id="bd624-119">クエリとデータベースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="bd624-119">Depends on query and database.</span></span> <span data-ttu-id="bd624-120">データベースによっては、レコードを一意に識別するのに十分な情報があれば、クエリの結果を更新できます。</span><span class="sxs-lookup"><span data-stu-id="bd624-120">Some databases allow updates if sufficient information is available to uniquely identify records.</span></span>|  
|<span data-ttu-id="bd624-121">結合されていない複数のテーブルに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-121">Query based on multiple tables which are not joined</span></span>|<span data-ttu-id="bd624-122">いいえ。</span><span class="sxs-lookup"><span data-stu-id="bd624-122">No.</span></span>|  
|<span data-ttu-id="bd624-123">データベース内で読み取り専用に設定されているデータに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-123">Query based on data marked as read-only in the database</span></span>|<span data-ttu-id="bd624-124">いいえ。</span><span class="sxs-lookup"><span data-stu-id="bd624-124">No.</span></span>|  
|<span data-ttu-id="bd624-125">制約のない単一のテーブルを含むビューに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-125">Query based on a view that involves one table with no constraints</span></span>|<span data-ttu-id="bd624-126">可 (下のリストを除く)。</span><span class="sxs-lookup"><span data-stu-id="bd624-126">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="bd624-127">一対一リレーションシップで結合されているテーブルに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-127">Query based on tables joined with a one-to-one relationship</span></span>|<span data-ttu-id="bd624-128">可 (下のリストを除く)。</span><span class="sxs-lookup"><span data-stu-id="bd624-128">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="bd624-129">一対多リレーションシップで結合されているテーブルに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-129">Query based on tables joined with a one-to-many relationship</span></span>|<span data-ttu-id="bd624-130">通常は可。</span><span class="sxs-lookup"><span data-stu-id="bd624-130">Usually.</span></span>|  
|<span data-ttu-id="bd624-131">多対多リレーションシップを持つ 3 つ以上のテーブルに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-131">Query based on three or more tables in which there is a many-to-many relationship</span></span>|<span data-ttu-id="bd624-132">いいえ。</span><span class="sxs-lookup"><span data-stu-id="bd624-132">No.</span></span>|  
|<span data-ttu-id="bd624-133">更新権限を与えられていないテーブルに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-133">Query based on a table for which update permission is not granted</span></span>|<span data-ttu-id="bd624-134">削除は可。更新は不可。</span><span class="sxs-lookup"><span data-stu-id="bd624-134">Can delete but not update.</span></span>|  
|<span data-ttu-id="bd624-135">削除権限を与えられていないテーブルに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-135">Query based on a table for which delete permission is not granted</span></span>|<span data-ttu-id="bd624-136">更新は可。削除は不可。</span><span class="sxs-lookup"><span data-stu-id="bd624-136">Can update but not delete.</span></span>|  
|<span data-ttu-id="bd624-137">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-137">Aggregate query</span></span>|<span data-ttu-id="bd624-138">いいえ。</span><span class="sxs-lookup"><span data-stu-id="bd624-138">No.</span></span>|  
|<span data-ttu-id="bd624-139">合計または集約関数を含むサブクエリに基づくクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-139">Query based on a subquery that contains totals or aggregate functions</span></span>|<span data-ttu-id="bd624-140">いいえ。</span><span class="sxs-lookup"><span data-stu-id="bd624-140">No.</span></span>|  
|<span data-ttu-id="bd624-141">重複する行を排除する DISTINCT キーワードを含むクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-141">Query that includes the DISTINCT keyword to exclude duplicate rows</span></span>|<span data-ttu-id="bd624-142">いいえ。</span><span class="sxs-lookup"><span data-stu-id="bd624-142">No.</span></span>|  
|<span data-ttu-id="bd624-143">テーブルを返すユーザー定義関数が FROM 句に含まれるクエリ、および複数の SELECT ステートメントを含むユーザー定義関数を FROM 句に含むクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-143">Query whose FROM clause includes a user-defined function that returns a table and the user-defined function contains multiple select statements</span></span>|<span data-ttu-id="bd624-144">いいえ。</span><span class="sxs-lookup"><span data-stu-id="bd624-144">No.</span></span>|  
|<span data-ttu-id="bd624-145">インライン ユーザー定義関数を FROM 句に含むクエリ</span><span class="sxs-lookup"><span data-stu-id="bd624-145">Query whose FROM clause includes an inline user-defined function</span></span>|<span data-ttu-id="bd624-146">はい。</span><span class="sxs-lookup"><span data-stu-id="bd624-146">Yes.</span></span>|  
  
 <span data-ttu-id="bd624-147">また、クエリ結果で特定の列を更新できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bd624-147">In addition, you might not be able to update specific columns in the query results.</span></span> <span data-ttu-id="bd624-148">結果ペインで更新できない列の種類を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bd624-148">The following list summarizes specific types of columns that you cannot update in the Results pane.</span></span>  
  
-   <span data-ttu-id="bd624-149">式に基づく列</span><span class="sxs-lookup"><span data-stu-id="bd624-149">Columns based on expressions</span></span>  
  
-   <span data-ttu-id="bd624-150">スカラー ユーザー定義関数に基づく列</span><span class="sxs-lookup"><span data-stu-id="bd624-150">Columns based on scalar user-defined functions</span></span>  
  
-   <span data-ttu-id="bd624-151">他のユーザーにより削除された行または列</span><span class="sxs-lookup"><span data-stu-id="bd624-151">Rows or columns deleted by another user</span></span>  
  
-   <span data-ttu-id="bd624-152">他のユーザーによりロックされている行または列 (ただし、ロックされている行は、通常、ロックが解除されたと同時に更新できるようになります。)</span><span class="sxs-lookup"><span data-stu-id="bd624-152">Rows or columns locked by another user (locked rows can usually be updated as soon as they are unlocked)</span></span>  
  
-   <span data-ttu-id="bd624-153">タイムスタンプまたは BLOB 列</span><span class="sxs-lookup"><span data-stu-id="bd624-153">Timestamp or BLOB columns</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd624-154">参照</span><span class="sxs-lookup"><span data-stu-id="bd624-154">See Also</span></span>  
 [<span data-ttu-id="bd624-155">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="bd624-155">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
