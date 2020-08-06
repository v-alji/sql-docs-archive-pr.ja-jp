---
title: MSSQLSERVER_1505 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1505 (Database Engine error)
ms.assetid: ef4df75d-0f36-4c8b-b36c-e427f65f91ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c152404cf2d3710bbe98b29da7a96d86f58859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714406"
---
# <a name="mssqlserver_1505"></a><span data-ttu-id="703c4-102">MSSQLSERVER_1505</span><span class="sxs-lookup"><span data-stu-id="703c4-102">MSSQLSERVER_1505</span></span>
    
## <a name="details"></a><span data-ttu-id="703c4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="703c4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="703c4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="703c4-104">Product Name</span></span>|<span data-ttu-id="703c4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="703c4-105">SQL Server</span></span>|  
|<span data-ttu-id="703c4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="703c4-106">Event ID</span></span>|<span data-ttu-id="703c4-107">1505</span><span class="sxs-lookup"><span data-stu-id="703c4-107">1505</span></span>|  
|<span data-ttu-id="703c4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="703c4-108">Event Source</span></span>|<span data-ttu-id="703c4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="703c4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="703c4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="703c4-110">Component</span></span>|<span data-ttu-id="703c4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="703c4-111">SQLEngine</span></span>|  
|<span data-ttu-id="703c4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="703c4-112">Symbolic Name</span></span>|<span data-ttu-id="703c4-113">DUP_KEY</span><span class="sxs-lookup"><span data-stu-id="703c4-113">DUP_KEY</span></span>|  
|<span data-ttu-id="703c4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="703c4-114">Message Text</span></span>|<span data-ttu-id="703c4-115">オブジェクト名 '%.\*ls' およびインデックス名 '%.\*ls' の重複キーが見つかったため、CREATE UNIQUE INDEX が終了しました。</span><span class="sxs-lookup"><span data-stu-id="703c4-115">CREATE UNIQUE INDEX terminated because a duplicate key was found for object name '%.\*ls' and index name '%.\*ls'.</span></span>  <span data-ttu-id="703c4-116">重複キーの値は %ls です。</span><span class="sxs-lookup"><span data-stu-id="703c4-116">The duplicate key value is %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="703c4-117">説明</span><span class="sxs-lookup"><span data-stu-id="703c4-117">Explanation</span></span>  
 <span data-ttu-id="703c4-118">このエラーは、一意インデックスを作成しようとしたときに、指定した値がテーブルの 1 つ以上の行に含まれている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="703c4-118">This error occurs when you attempt to create a unique index and more than one row in the table contains the specified duplicate value.</span></span> <span data-ttu-id="703c4-119">一意インデックスは、インデックスを作成して UNIQUE キーワードを指定した場合、または UNIQUE 制約を作成した場合に作成されます。</span><span class="sxs-lookup"><span data-stu-id="703c4-119">A unique index is created when you create an index and specify the UNIQUE keyword, or when you create a UNIQUE constraint.</span></span> <span data-ttu-id="703c4-120">インデックスまたは制約で定義された列の値が重複する行をテーブルに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="703c4-120">The table cannot contain any rows that have duplicate values in the columns defined in the index or constraint.</span></span>  
  
 <span data-ttu-id="703c4-121">次の **Employee** テーブルのデータについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="703c4-121">Consider the data in the following **Employee** table:</span></span>  
  
|<span data-ttu-id="703c4-122">LastName</span><span class="sxs-lookup"><span data-stu-id="703c4-122">LastName</span></span>|<span data-ttu-id="703c4-123">FirstName</span><span class="sxs-lookup"><span data-stu-id="703c4-123">FirstName</span></span>|<span data-ttu-id="703c4-124">JobTitle</span><span class="sxs-lookup"><span data-stu-id="703c4-124">JobTitle</span></span>|<span data-ttu-id="703c4-125">HireDate</span><span class="sxs-lookup"><span data-stu-id="703c4-125">HireDate</span></span>|  
|--------------|---------------|--------------|--------------|  
|<span data-ttu-id="703c4-126">Walters</span><span class="sxs-lookup"><span data-stu-id="703c4-126">Walters</span></span>|<span data-ttu-id="703c4-127">Rob</span><span class="sxs-lookup"><span data-stu-id="703c4-127">Rob</span></span>|<span data-ttu-id="703c4-128">上級ツール デザイナー</span><span class="sxs-lookup"><span data-stu-id="703c4-128">Senior Tool Designer</span></span>|<span data-ttu-id="703c4-129">2004-11-19</span><span class="sxs-lookup"><span data-stu-id="703c4-129">2004-11-19</span></span>|  
|<span data-ttu-id="703c4-130">Brown</span><span class="sxs-lookup"><span data-stu-id="703c4-130">Brown</span></span>|<span data-ttu-id="703c4-131">Kevin</span><span class="sxs-lookup"><span data-stu-id="703c4-131">Kevin</span></span>|<span data-ttu-id="703c4-132">マーケティング アシスタント</span><span class="sxs-lookup"><span data-stu-id="703c4-132">Marketing Assistant</span></span>|<span data-ttu-id="703c4-133">NULL</span><span class="sxs-lookup"><span data-stu-id="703c4-133">NULL</span></span>|  
|<span data-ttu-id="703c4-134">Brown</span><span class="sxs-lookup"><span data-stu-id="703c4-134">Brown</span></span>|<span data-ttu-id="703c4-135">Jo</span><span class="sxs-lookup"><span data-stu-id="703c4-135">Jo</span></span>|<span data-ttu-id="703c4-136">デザイン エンジニア</span><span class="sxs-lookup"><span data-stu-id="703c4-136">Design Engineer</span></span>|<span data-ttu-id="703c4-137">NULL</span><span class="sxs-lookup"><span data-stu-id="703c4-137">NULL</span></span>|  
|<span data-ttu-id="703c4-138">Walters</span><span class="sxs-lookup"><span data-stu-id="703c4-138">Walters</span></span>|<span data-ttu-id="703c4-139">Rob</span><span class="sxs-lookup"><span data-stu-id="703c4-139">Rob</span></span>|<span data-ttu-id="703c4-140">ツール デザイナー</span><span class="sxs-lookup"><span data-stu-id="703c4-140">Tool Designer</span></span>|<span data-ttu-id="703c4-141">2001-08-09</span><span class="sxs-lookup"><span data-stu-id="703c4-141">2001-08-09</span></span>|  
  
 <span data-ttu-id="703c4-142">**LastName** 列、または **LastName** 列と **FirstName** 列の組み合わせに対して一意インデックスを作成することはできません。これは行の値が重複しているためです。</span><span class="sxs-lookup"><span data-stu-id="703c4-142">A unique index can not be created on the column combinations **LastName** or **LastName**, **FirstName** because of duplicate values in the rows.</span></span>  
  
 <span data-ttu-id="703c4-143">よりわかりにくいのは、**HireDate** 列で一意性違反が発生する可能性があることです。</span><span class="sxs-lookup"><span data-stu-id="703c4-143">Less obvious is the potential for a uniqueness violation in the **HireDate** column.</span></span> <span data-ttu-id="703c4-144">インデックスの作成という目的では、NULL 値は同じ値と見なされます。</span><span class="sxs-lookup"><span data-stu-id="703c4-144">For indexing purposes, NULL values compare as equal.</span></span> <span data-ttu-id="703c4-145">したがって、複数行のキー値が NULL である場合は、一意インデックスまたは一意制約を作成できません。</span><span class="sxs-lookup"><span data-stu-id="703c4-145">Therefore, you cannot create a unique index or constraint if the key values are NULL in more than one row.</span></span> <span data-ttu-id="703c4-146">上記のデータの場合、**HireDate** 列、または **LastName** 列と **HireDate** 列の組み合わせに対して一意インデックスを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="703c4-146">Given the data above, a unique index cannot be created on the column combinations **HireDate** or **LastName**, **HireDate**.</span></span>  
  
 <span data-ttu-id="703c4-147">エラー メッセージ 1505 では、一意性制約に違反する最初の行が返されます。</span><span class="sxs-lookup"><span data-stu-id="703c4-147">Error message 1505 returns the first row that violates the uniqueness constraint.</span></span> <span data-ttu-id="703c4-148">これ以外にも重複行がテーブルに含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="703c4-148">There may be other duplicate rows in the table.</span></span> <span data-ttu-id="703c4-149">重複行をすべて検出するには、指定されたテーブルに対してクエリを実行し、GROUP BY 句と HAVING 句を使用して重複行を抽出します。</span><span class="sxs-lookup"><span data-stu-id="703c4-149">To find all duplicate rows, query the specified table and use the GROUP BY and HAVING clauses to report the duplicate rows.</span></span> <span data-ttu-id="703c4-150">たとえば、次のクエリを実行すると、姓と名が重複する **Employee** テーブル内の行が返されます。</span><span class="sxs-lookup"><span data-stu-id="703c4-150">For example, the following query returns the rows in the **Employee** table that have duplicate first and last names.</span></span>  
  
 <span data-ttu-id="703c4-151">Dbo から LastName、FirstName、count () を選択し \* ます。従業員グループ (LastName、FirstName HAVING count ( \* ) > 1)</span><span class="sxs-lookup"><span data-stu-id="703c4-151">SELECT LastName, FirstName, count(\*) FROM dbo.Employee GROUP BY LastName, FirstName HAVING count(\*) > 1;</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="703c4-152">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="703c4-152">User Action</span></span>  
 <span data-ttu-id="703c4-153">次の解決策について検討してください。</span><span class="sxs-lookup"><span data-stu-id="703c4-153">Consider the following solutions.</span></span>  
  
-   <span data-ttu-id="703c4-154">インデックス定義または制約定義の列を追加または削除し、一意の複合インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="703c4-154">Add or remove columns in the index or constraint definition to create a unique composite.</span></span> <span data-ttu-id="703c4-155">上記の例では、インデックス定義または制約定義に **MiddleName** 列を追加すると、重複に関する問題が解決される場合があります。</span><span class="sxs-lookup"><span data-stu-id="703c4-155">In the previous example, adding a **MiddleName** column to the index or constraint definition might resolve the duplication problem.</span></span>  
  
-   <span data-ttu-id="703c4-156">一意インデックスまたは一意制約の列を選択する場合は、NOT NULL と定義された列を選択します。</span><span class="sxs-lookup"><span data-stu-id="703c4-156">Select columns that are defined as NOT NULL when you choose columns for a unique index or constraint.</span></span> <span data-ttu-id="703c4-157">これにより、複数の行のキー値に NULL が含まれている場合に発生する一意性違反の可能性がなくなります。</span><span class="sxs-lookup"><span data-stu-id="703c4-157">This eliminates the possibility of a uniqueness violation caused when more than one row contains NULL in the key values.</span></span>  
  
-   <span data-ttu-id="703c4-158">重複値の原因がデータ エントリのエラーである場合は、そのデータを手動で修正してから、インデックスまたは制約を作成します。</span><span class="sxs-lookup"><span data-stu-id="703c4-158">If the duplicate values are the result of data entry errors, manually correct the data and then create the index or constraint.</span></span> <span data-ttu-id="703c4-159">テーブル内の重複行を削除する方法の詳細については、サポート技術情報の記事 139444「[テーブルから重複行を削除する方法](https://support.microsoft.com/kb/139444)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="703c4-159">For information about removing duplicate rows in a table, see Knowledge Base article 139444: [How to remove duplicate rows from a table in SQL Server](https://support.microsoft.com/kb/139444).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703c4-160">参照</span><span class="sxs-lookup"><span data-stu-id="703c4-160">See Also</span></span>  
 <span data-ttu-id="703c4-161">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="703c4-161">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="703c4-162">[一意のインデックスの作成](../indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="703c4-162">[Create Unique Indexes](../indexes/indexes.md) </span></span>  
 [<span data-ttu-id="703c4-163">UNIQUE 制約の作成</span><span class="sxs-lookup"><span data-stu-id="703c4-163">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)  
  
  
