---
title: MSSQLSERVER_605 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 605 (Database Engine error)
ms.assetid: d8d3a22e-1ff8-48a4-891f-4c8619437e24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e196fba84af492b25e798629d3e808b1bf22857e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643845"
---
# <a name="mssqlserver_605"></a><span data-ttu-id="d53bc-102">MSSQLSERVER_605</span><span class="sxs-lookup"><span data-stu-id="d53bc-102">MSSQLSERVER_605</span></span>
    
## <a name="details"></a><span data-ttu-id="d53bc-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d53bc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d53bc-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d53bc-104">Product Name</span></span>|<span data-ttu-id="d53bc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d53bc-105">SQL Server</span></span>|  
|<span data-ttu-id="d53bc-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d53bc-106">Event ID</span></span>|<span data-ttu-id="d53bc-107">605</span><span class="sxs-lookup"><span data-stu-id="d53bc-107">605</span></span>|  
|<span data-ttu-id="d53bc-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d53bc-108">Event Source</span></span>|<span data-ttu-id="d53bc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d53bc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d53bc-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d53bc-110">Component</span></span>|<span data-ttu-id="d53bc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d53bc-111">SQLEngine</span></span>|  
|<span data-ttu-id="d53bc-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d53bc-112">Symbolic Name</span></span>|<span data-ttu-id="d53bc-113">WRONGPAGE</span><span class="sxs-lookup"><span data-stu-id="d53bc-113">WRONGPAGE</span></span>|  
|<span data-ttu-id="d53bc-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d53bc-114">Message Text</span></span>|<span data-ttu-id="d53bc-115">データベース %d の論理ページ %S_PGID のフェッチに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="d53bc-115">Attempt to fetch logical page %S_PGID in database %d failed.</span></span> <span data-ttu-id="d53bc-116">この論理ページは、アロケーション ユニット %I64d ではなく、%I64d に所属しています。</span><span class="sxs-lookup"><span data-stu-id="d53bc-116">It belongs to allocation unit %I64d not to %I64d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d53bc-117">説明</span><span class="sxs-lookup"><span data-stu-id="d53bc-117">Explanation</span></span>  
 <span data-ttu-id="d53bc-118">一般的に、このエラーは指定されたデータベース内のページまたはアロケーションの破損を意味しています。</span><span class="sxs-lookup"><span data-stu-id="d53bc-118">This error generally signifies page or allocation corruption in the specified database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d53bc-119">では、ページ リンケージをたどるか IAM (Index Allocation Map) を使用してテーブルに属するページを読み取る際に、破損が検出されます。</span><span class="sxs-lookup"><span data-stu-id="d53bc-119">detects corruption when reading pages belonging to a table either by following the page linkages or by using the Index Allocation Map (IAM).</span></span> <span data-ttu-id="d53bc-120">テーブルに割り当てられるすべてのページは、テーブルに関連付けられているいずれか 1 つのアロケーション ユニットに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d53bc-120">All pages allocated to a table must belong to one of the allocation units associated with the table.</span></span> <span data-ttu-id="d53bc-121">ページ ヘッダーに含まれるアロケーション ユニット ID が、テーブルに関連付けられているアロケーション ユニット ID と一致しない場合、この例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-121">If the allocation unit ID contained in the page header does not match an allocation unit ID associated with the table, this exception is raised.</span></span> <span data-ttu-id="d53bc-122">エラー メッセージの一覧で最初に示されるアロケーション ユニット ID はページ ヘッダー内の ID で、2 番目のアロケーション ユニットの値はテーブルに関連付けられている ID です。</span><span class="sxs-lookup"><span data-stu-id="d53bc-122">The first allocation unit ID listed in the error message is the ID present in the page header, and the second allocation unit value is the ID associated with the table.</span></span>  
  
 <span data-ttu-id="d53bc-123">**データ破損エラー**</span><span class="sxs-lookup"><span data-stu-id="d53bc-123">**Data Corruption Errors**</span></span>  
  
 <span data-ttu-id="d53bc-124">重大度レベル 21 は、データ破損の可能性を示しています。</span><span class="sxs-lookup"><span data-stu-id="d53bc-124">A severity level of 21 indicates potential data corruption.</span></span> <span data-ttu-id="d53bc-125">この原因としては、ページ チェーンの破損、IAM の破損、対象となるオブジェクトの [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) カタログ ビュー内に無効なエントリがあることなどが考えられます。</span><span class="sxs-lookup"><span data-stu-id="d53bc-125">Possible causes are a damaged page chain, a corrupt IAM, or an invalid entry in the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view for that object.</span></span> <span data-ttu-id="d53bc-126">これらのエラーは多くの場合、ハードウェア エラーやディスク デバイスのドライバー エラーによって発生します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-126">These errors are often caused by hardware or disk device driver failure.</span></span>  
  
 <span data-ttu-id="d53bc-127">**一時的なエラー**</span><span class="sxs-lookup"><span data-stu-id="d53bc-127">**Transient Errors**</span></span>  
  
 <span data-ttu-id="d53bc-128">重大度レベル 12 は、一時的なエラーの可能性を示しています。つまり、このエラーはキャッシュ内で発生するもので、ディスク上のデータの破損を示すものではありません。</span><span class="sxs-lookup"><span data-stu-id="d53bc-128">A severity level of 12 indicates a potential transient error; that is, it occurs in the cache and does not indicate damage to data on disk.</span></span> <span data-ttu-id="d53bc-129">一時的な 605 エラーは、以下の条件で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d53bc-129">Transient 605 errors can be caused by the following conditions:</span></span>  
  
-   <span data-ttu-id="d53bc-130">オペレーティング システムから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に、処理が途中であるにもかかわらず I/O 操作が完了したことが通知された場合。実際のデータの破損がない場合でも、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d53bc-130">The operating system prematurely notifies [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that an I/O operation has completed; the error message is displayed even though no actual data corruption exists.</span></span>  
  
 <span data-ttu-id="d53bc-131">オプティマイザー ヒント NOLOCK を使用してクエリを実行しているか、トランザクション分離レベルを READ UNCOMMITTED に設定している場合。</span><span class="sxs-lookup"><span data-stu-id="d53bc-131">Running a query with the Optimizer hint NOLOCK or setting the transaction isolation level to READ UNCOMMITTED.</span></span> <span data-ttu-id="d53bc-132">NOLOCK または READ UNCOMMITTED を使用するクエリで、別のユーザーによる移動または変更が実行中であるデータを読み取ろうとすると、605 エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-132">When a query that is using NOLOCK or READ UNCOMMITTED tries to read data that is being moved or changed by another user, a 605 error occurs.</span></span> <span data-ttu-id="d53bc-133">一時的な 605 エラーかどうかを確認するには、後でクエリを再実行してください。</span><span class="sxs-lookup"><span data-stu-id="d53bc-133">To verify that it is a transient 605 error, rerun the query later.</span></span> <span data-ttu-id="d53bc-134">詳細については、サポート技術情報 [235880](https://support.microsoft.com/kb/235880/en-us) の「SQL Server で、オプティマイザー ヒント NOLOCK を指定してクエリを実行したり、分離レベルを READ UNCOMMITTED に設定したりすると、エラー 605 が表示される」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d53bc-134">For more information, see this KB article [235880](https://support.microsoft.com/kb/235880/en-us): "You receive an "Error 605" error message when you run a query with the optimizer hint NOLOCK or you set the transaction isolation level to READ UNCOMMITTED in SQL Server."</span></span>  
  
 <span data-ttu-id="d53bc-135">一般的に、データ アクセス中にエラーが発生しても、後に続く DBCC CHECKDB 操作がエラーなしで完了した場合、605 エラーは一時的なエラーであったと考えられます。</span><span class="sxs-lookup"><span data-stu-id="d53bc-135">In general, if the error occurs during data access but subsequent DBCC CHECKDB operations complete without error, the 605 error was probably transient.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d53bc-136">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d53bc-136">User Action</span></span>  
 <span data-ttu-id="d53bc-137">605 エラーが一時的なエラーでない場合、問題は深刻です。次の作業を行って修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d53bc-137">If the 605 error is not transient, the problem is severe and must be corrected by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="d53bc-138">次のクエリを実行して、メッセージ内に指定されているアロケーション ユニットと関連付けられているテーブルを特定し、</span><span class="sxs-lookup"><span data-stu-id="d53bc-138">Identify the tables associated with the allocation units specified in the message by running the following query.</span></span> <span data-ttu-id="d53bc-139">`allocation_unit_id` をエラー メッセージ内に指定されているアロケーション ユニットと入れ替えます。</span><span class="sxs-lookup"><span data-stu-id="d53bc-139">Replace `allocation_unit_id` with the allocation units specified in the error message.</span></span>  
  
     <span data-ttu-id="d53bc-140">USE`database_name`;</span><span class="sxs-lookup"><span data-stu-id="d53bc-140">USE`database_name`;</span></span>  
  
     <span data-ttu-id="d53bc-141">GO</span><span class="sxs-lookup"><span data-stu-id="d53bc-141">GO</span></span>  
  
     <span data-ttu-id="d53bc-142">SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,</span><span class="sxs-lookup"><span data-stu-id="d53bc-142">SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,</span></span>  
  
     <span data-ttu-id="d53bc-143">au.type_desc AS allocation_type, au.data_pages, partition_number</span><span class="sxs-lookup"><span data-stu-id="d53bc-143">au.type_desc AS allocation_type, au.data_pages, partition_number</span></span>  
  
     <span data-ttu-id="d53bc-144">FROM sys.allocation_units AS au</span><span class="sxs-lookup"><span data-stu-id="d53bc-144">FROM sys.allocation_units AS au</span></span>  
  
     <span data-ttu-id="d53bc-145">JOIN sys.partitions AS p ON au.container_id = p.partition_id</span><span class="sxs-lookup"><span data-stu-id="d53bc-145">JOIN sys.partitions AS p ON au.container_id = p.partition_id</span></span>  
  
     <span data-ttu-id="d53bc-146">JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id</span><span class="sxs-lookup"><span data-stu-id="d53bc-146">JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id</span></span>  
  
     <span data-ttu-id="d53bc-147">WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`</span><span class="sxs-lookup"><span data-stu-id="d53bc-147">WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`</span></span>  
  
     <span data-ttu-id="d53bc-148">ORDER BY au.allocation_unit_id;</span><span class="sxs-lookup"><span data-stu-id="d53bc-148">ORDER BY au.allocation_unit_id;</span></span>  
  
     <span data-ttu-id="d53bc-149">GO</span><span class="sxs-lookup"><span data-stu-id="d53bc-149">GO</span></span>  
  
2.  <span data-ttu-id="d53bc-150">エラー メッセージ内に指定されている 2 番目のアロケーション ユニット ID と関連付けられているテーブルに対し、REPAIR 句なしで DBCC CHECKTABLE を実行します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-150">Execute DBCC CHECKTABLE without a REPAIR clause on the table associated with the second allocation unit ID specified in the error message.</span></span>  
  
3.  <span data-ttu-id="d53bc-151">データベース全体における破損の全範囲を調べるには、できるだけ早く REPAIR 句なしで DBCC CHECKDB を実行します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-151">Execute DBCC CHECKDB without a REPAIR clause as soon as possible to determine the full extent of the corruption in the entire database.</span></span>  
  
4.  <span data-ttu-id="d53bc-152">エラー ログで、605 エラーと共に頻繁に発生している他のエラーがないかどうかを確認し、Windows イベント ログで、システムまたはハードウェアに関連する問題がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-152">Check the error log for other errors that often accompany a 605 error and examine the Windows Event Log for any system or hardware related issues.</span></span> <span data-ttu-id="d53bc-153">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-153">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d53bc-154">問題がハードウェアに関連するものでない場合は、次のいずれかの作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-154">If the problem is not hardware related, perform one of the following tasks:</span></span>  
  
1.  <span data-ttu-id="d53bc-155">既知のクリーン バックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-155">Restore the database from a known clean backup.</span></span> <span data-ttu-id="d53bc-156">破損したページだけを復元するには、ページ復元バックアップ機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="d53bc-156">You can leverage the page restore backup feature to restore just the damaged pages.</span></span>  
  
2.  <span data-ttu-id="d53bc-157">破損修復の手順 3. で実行した DBCC CHECKDB 操作で推奨された REPAIR 句と共に、DBCC CHECKDB を実行します。</span><span class="sxs-lookup"><span data-stu-id="d53bc-157">Run DBCC CHECKDB with the REPAIR clause recommended by the DBCC CHECKDB operation performed in step 3 to repair the corruption.</span></span> <span data-ttu-id="d53bc-158">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d53bc-158">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span> <span data-ttu-id="d53bc-159">確認用に、DBCC CHECKDB からの出力を保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="d53bc-159">Have the output from DBCC CHECKDB available for review.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="d53bc-160">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d53bc-160">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d53bc-161">参照</span><span class="sxs-lookup"><span data-stu-id="d53bc-161">See Also</span></span>  
 [<span data-ttu-id="d53bc-162">DBCC CHECKTABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d53bc-162">DBCC CHECKTABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)  
  
  
