---
title: 変更の追跡の管理 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tracking data changes [SQL Server]
- change tracking [SQL Server], overhead
- change tracking [SQL Server]
- change tracking [SQL Server], managing
ms.assetid: 94a8d361-e897-4d6d-9a8f-1bb652e7a850
author: rothja
ms.author: jroth
ms.openlocfilehash: 36409f2ce256325da1c9849e5bec7e7ce114cf25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640822"
---
# <a name="manage-change-tracking-sql-server"></a><span data-ttu-id="62c01-102">変更の追跡の管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="62c01-102">Manage Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="62c01-103">このトピックでは、変更の追跡を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="62c01-103">This topic describes how to manage change tracking.</span></span> <span data-ttu-id="62c01-104">また、セキュリティを構成する方法、および変更の追跡を使用する場合のストレージとパフォーマンスへの影響を判断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="62c01-104">It also describes how to configure security and determine the effects on storage and performance when change tracking is used.</span></span>  
  
## <a name="managing-change-tracking"></a><span data-ttu-id="62c01-105">変更の追跡の管理</span><span class="sxs-lookup"><span data-stu-id="62c01-105">Managing Change Tracking</span></span>  
 <span data-ttu-id="62c01-106">ここでは、変更の追跡の管理に関連するカタログ ビュー、権限、および設定の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="62c01-106">The following sections list catalog views, permissions, and settings that are relevant for managing change tracking.</span></span>  
  
### <a name="catalog-views"></a><span data-ttu-id="62c01-107">カタログ ビュー</span><span class="sxs-lookup"><span data-stu-id="62c01-107">Catalog Views</span></span>  
 <span data-ttu-id="62c01-108">変更の追跡が有効になっているテーブルおよびデータベースを確認するには、次のカタログ ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="62c01-108">To determine which tables and databases have change tracking enabled, you can use the following catalog views:</span></span>  
  
-   [<span data-ttu-id="62c01-109">sys.change_tracking_databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="62c01-109">sys.change_tracking_databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases)  
  
-   [<span data-ttu-id="62c01-110">sys.change_tracking_tables &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="62c01-110">sys.change_tracking_tables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables)  
  
 <span data-ttu-id="62c01-111">また、 [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) カタログ ビューには、ユーザー テーブルの変更の追跡を有効にしたときに作成された内部テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-111">Also, the [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) catalog view lists the internal tables that are created when change tracking is enabled for a user table.</span></span>  
  
### <a name="security"></a><span data-ttu-id="62c01-112">Security</span><span class="sxs-lookup"><span data-stu-id="62c01-112">Security</span></span>  
 <span data-ttu-id="62c01-113">[変更追跡関数](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql)を使用して変更追跡情報にアクセスするには、プリンシパルに次の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="62c01-113">To access change tracking information by using the [change tracking functions](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql), the principal must have the following permissions:</span></span>  
  
-   <span data-ttu-id="62c01-114">少なくともクエリ対象テーブルへの変更の追跡対象テーブルの主キー列に対する SELECT 権限。</span><span class="sxs-lookup"><span data-stu-id="62c01-114">SELECT permission on at least the primary key columns on the change-tracked table to the table that is being queried.</span></span>  
  
-   <span data-ttu-id="62c01-115">変更が取得されるテーブルに対する VIEW CHANGE TRACKING 権限。</span><span class="sxs-lookup"><span data-stu-id="62c01-115">VIEW CHANGE TRACKING permission on the table for which changes are being obtained.</span></span> <span data-ttu-id="62c01-116">VIEW CHANGE TRACKING 権限は、次の理由のため必要です。</span><span class="sxs-lookup"><span data-stu-id="62c01-116">The VIEW CHANGE TRACKING permission is required for the following reasons:</span></span>  
  
    -   <span data-ttu-id="62c01-117">変更追跡レコードには、削除された行に関する情報 (特に削除された行の主キー値) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="62c01-117">Change tracking records include information about rows that have been deleted, specifically the primary key values of the rows that have been deleted.</span></span> <span data-ttu-id="62c01-118">機密データが削除された後の変更の追跡対象テーブルに対する SELECT 権限がプリンシパルに付与されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="62c01-118">A principal could have been granted SELECT permission for a change tracked table after some sensitive data had been deleted.</span></span> <span data-ttu-id="62c01-119">この場合、そのプリンシパルが変更の追跡を使用して、削除済みの情報にアクセスできることは望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="62c01-119">In this case, you would not want that principal to be able to access that deleted information by using change tracking.</span></span>  
  
    -   <span data-ttu-id="62c01-120">変更追跡情報には、更新操作によってどの列が変更されたかという情報が格納される場合があります。</span><span class="sxs-lookup"><span data-stu-id="62c01-120">Change tracking information can store information about which columns have been changed by update operations.</span></span> <span data-ttu-id="62c01-121">プリンシパルは、機密情報を含む列に対する権限を拒否されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="62c01-121">A principal could be denied permission to a column that contains sensitive information.</span></span> <span data-ttu-id="62c01-122">ただし、変更追跡情報は参照できるので、列の値が更新されたことは確認できますが、列の値を確認することはできません。</span><span class="sxs-lookup"><span data-stu-id="62c01-122">However, because change tracking information is available, a principal can determine that a column value has been updated, but the principal cannot determine the value of the column.</span></span>  
  
## <a name="understanding-change-tracking-overhead"></a><span data-ttu-id="62c01-123">変更の追跡のオーバーヘッドについて</span><span class="sxs-lookup"><span data-stu-id="62c01-123">Understanding Change Tracking Overhead</span></span>  
 <span data-ttu-id="62c01-124">テーブルの変更の追跡を有効にすると、一部の管理操作が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="62c01-124">When change tracking is enabled for a table, some administration operations are affected.</span></span> <span data-ttu-id="62c01-125">次の表に、考慮する必要がある操作と影響を示します。</span><span class="sxs-lookup"><span data-stu-id="62c01-125">The following table lists the operations and the effects you should consider.</span></span>  
  
|<span data-ttu-id="62c01-126">操作</span><span class="sxs-lookup"><span data-stu-id="62c01-126">Operation</span></span>|<span data-ttu-id="62c01-127">変更の追跡が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="62c01-127">When change tracking is enabled</span></span>|  
|---------------|-------------------------------------|  
|<span data-ttu-id="62c01-128">DROP TABLE</span><span class="sxs-lookup"><span data-stu-id="62c01-128">DROP TABLE</span></span>|<span data-ttu-id="62c01-129">削除するテーブルのすべての変更追跡情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-129">All change tracking information for the dropped table is removed.</span></span>|  
|<span data-ttu-id="62c01-130">ALTER TABLE DROP CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="62c01-130">ALTER TABLE DROP CONSTRAINT</span></span>|<span data-ttu-id="62c01-131">PRIMARY KEY 制約を削除しようとすると失敗します。</span><span class="sxs-lookup"><span data-stu-id="62c01-131">An attempt to drop the PRIMARY KEY constraint will fail.</span></span> <span data-ttu-id="62c01-132">PRIMARY KEY 制約を削除する前に、変更の追跡を無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="62c01-132">Change tracking must be disabled before a PRIMARY KEY constraint can be dropped.</span></span>|  
|<span data-ttu-id="62c01-133">ALTER TABLE DROP COLUMN</span><span class="sxs-lookup"><span data-stu-id="62c01-133">ALTER TABLE DROP COLUMN</span></span>|<span data-ttu-id="62c01-134">削除する列が主キーの一部である場合、変更の追跡に関係なく列は削除できません。</span><span class="sxs-lookup"><span data-stu-id="62c01-134">If a column that is being dropped is part of the primary key, dropping the column is not allowed, regardless of change tracking.</span></span><br /><br /> <span data-ttu-id="62c01-135">削除する列が主キーの一部ではない場合、列の削除は成功します。</span><span class="sxs-lookup"><span data-stu-id="62c01-135">If the column that is being dropped is not part of the primary key, dropping the column succeeds.</span></span> <span data-ttu-id="62c01-136">ただし、このデータの同期を実行しているアプリケーションへの影響についてまず理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="62c01-136">However, the effect on any application that is synchronizing this data should be understood first.</span></span> <span data-ttu-id="62c01-137">テーブルで列の変更の追跡が有効になっている場合、削除した列がまだ変更追跡情報の一部として返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="62c01-137">If column change tracking is enabled for the table, the dropped column might still be returned as part of the change tracking information.</span></span> <span data-ttu-id="62c01-138">削除した列の処理は、アプリケーションで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="62c01-138">It is the responsibility of the application to handle the dropped column.</span></span>|  
|<span data-ttu-id="62c01-139">ALTER TABLE ADD COLUMN</span><span class="sxs-lookup"><span data-stu-id="62c01-139">ALTER TABLE ADD COLUMN</span></span>|<span data-ttu-id="62c01-140">変更の追跡対象のテーブルに新しい列を追加する場合、その列の追加は追跡されません。</span><span class="sxs-lookup"><span data-stu-id="62c01-140">If a new column is added to the change tracked table, the addition of the column is not tracked.</span></span> <span data-ttu-id="62c01-141">新しい列に加えられた更新および変更のみが追跡されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-141">Only the updates and changes that are made to the new column are tracked.</span></span>|  
|<span data-ttu-id="62c01-142">ALTER TABLE ALTER COLUMN</span><span class="sxs-lookup"><span data-stu-id="62c01-142">ALTER TABLE ALTER COLUMN</span></span>|<span data-ttu-id="62c01-143">主キー列以外の列のデータ型の変更は追跡されません。</span><span class="sxs-lookup"><span data-stu-id="62c01-143">Data type changes of a non-primary key columns are not tracked.</span></span>|  
|<span data-ttu-id="62c01-144">ALTER TABLE SWITCH</span><span class="sxs-lookup"><span data-stu-id="62c01-144">ALTER TABLE SWITCH</span></span>|<span data-ttu-id="62c01-145">いずれかまたは両方のテーブルで変更の追跡が有効になっている場合、パーティションの切り替えは失敗します。</span><span class="sxs-lookup"><span data-stu-id="62c01-145">Switching a partition fails if one or both of the tables has change tracking enabled.</span></span>|  
|<span data-ttu-id="62c01-146">DROP INDEX または ALTER INDEX DISABLE</span><span class="sxs-lookup"><span data-stu-id="62c01-146">DROP INDEX, or ALTER INDEX DISABLE</span></span>|<span data-ttu-id="62c01-147">主キーを設定するインデックスは削除または無効化できません。</span><span class="sxs-lookup"><span data-stu-id="62c01-147">The index that enforces the primary key cannot be dropped or disabled.</span></span>|  
|<span data-ttu-id="62c01-148">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="62c01-148">TRUNCATE TABLE</span></span>|<span data-ttu-id="62c01-149">テーブルの切り捨ては、変更の追跡が有効になっているテーブルに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="62c01-149">Truncating a table can be performed on a table that has change tracking enabled.</span></span> <span data-ttu-id="62c01-150">ただし、この操作によって削除される行は追跡されず、有効な最小バージョンが更新されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-150">However, the rows that are deleted by the operation are not tracked, and the minimum valid version is updated.</span></span> <span data-ttu-id="62c01-151">アプリケーションがそのバージョンをチェックすると、バージョンが古すぎるため再初期化が必要であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-151">When an application checks its version, the check indicates that the version is too old and a reinitialization is required.</span></span> <span data-ttu-id="62c01-152">これは、テーブルの変更の追跡を無効にして再度有効にした場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="62c01-152">This is the same as change tracking being disabled, and then reenabled for the table.</span></span>|  
  
 <span data-ttu-id="62c01-153">変更の追跡を使用すると、DML 操作の一部として格納される変更追跡情報が原因で、DML 操作のオーバーヘッドが多少増加します。</span><span class="sxs-lookup"><span data-stu-id="62c01-153">Using change tracking does add some overhead to DML operations because of the change tracking information that is being stored as part of the operation.</span></span>  
  
### <a name="effects-on-dml"></a><span data-ttu-id="62c01-154">DML への影響</span><span class="sxs-lookup"><span data-stu-id="62c01-154">Effects on DML</span></span>  
 <span data-ttu-id="62c01-155">変更の追跡は、DML 操作のパフォーマンスのオーバーヘッドを最小限に抑えるように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="62c01-155">Change tracking has been optimized to minimize the performance overhead on DML operations.</span></span> <span data-ttu-id="62c01-156">テーブルに対する変更の追跡の使用に関連するパフォーマンスのオーバーヘッドの増加は、テーブルにインデックスを作成して維持する必要がある場合に発生するオーバーヘッドに似ています。</span><span class="sxs-lookup"><span data-stu-id="62c01-156">The incremental performance overhead that is associated with using change tracking on a table is similar to the overhead incurred when an index is created for a table and needs to be maintained.</span></span>  
  
 <span data-ttu-id="62c01-157">DML 操作で変更された行ごとに、行が内部変更追跡テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-157">For each row that is changed by a DML operation, a row is added to the internal change tracking table.</span></span> <span data-ttu-id="62c01-158">DML 操作に関連するこの影響は、次のようなさまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="62c01-158">The effect of this relative to the DML operation depends on various factors, such as the following:</span></span>  
  
-   <span data-ttu-id="62c01-159">主キー列の数</span><span class="sxs-lookup"><span data-stu-id="62c01-159">The number of primary key columns</span></span>  
  
-   <span data-ttu-id="62c01-160">ユーザー テーブル行で変更されるデータの量</span><span class="sxs-lookup"><span data-stu-id="62c01-160">The amount of data that is being changed in the user table row</span></span>  
  
-   <span data-ttu-id="62c01-161">トランザクションで実行される操作の数</span><span class="sxs-lookup"><span data-stu-id="62c01-161">The number of operations that are being performed in a transaction</span></span>  
  
 <span data-ttu-id="62c01-162">スナップショット分離を使用している場合も、変更の追跡が有効になっているかどうかに関係なく、すべての DML 操作のパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="62c01-162">Snapshot isolation, if used, also has an effect on performance for all DML operations, whether change tracking is enabled or not.</span></span>  
  
### <a name="effects-on-storage"></a><span data-ttu-id="62c01-163">ストレージへの影響</span><span class="sxs-lookup"><span data-stu-id="62c01-163">Effects on Storage</span></span>  
 <span data-ttu-id="62c01-164">変更追跡データは、次の種類の内部テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-164">Change tracking data is stored in the following types of internal tables:</span></span>  
  
-   <span data-ttu-id="62c01-165">内部変更テーブル</span><span class="sxs-lookup"><span data-stu-id="62c01-165">Internal change table</span></span>  
  
     <span data-ttu-id="62c01-166">変更の追跡が有効になっているユーザー テーブルごとに 1 つずつ内部変更テーブルがあります。</span><span class="sxs-lookup"><span data-stu-id="62c01-166">There is one internal change table for each user table that has change tracking enabled.</span></span>  
  
-   <span data-ttu-id="62c01-167">内部トランザクション テーブル</span><span class="sxs-lookup"><span data-stu-id="62c01-167">Internal transaction table</span></span>  
  
     <span data-ttu-id="62c01-168">データベースごとに 1 つずつ内部トランザクション テーブルがあります。</span><span class="sxs-lookup"><span data-stu-id="62c01-168">There is one internal transaction table for the database.</span></span>  
  
 <span data-ttu-id="62c01-169">これらの内部テーブルは、ストレージ要件に次のような影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="62c01-169">These internal tables affect storage requirements in the following ways:</span></span>  
  
-   <span data-ttu-id="62c01-170">ユーザー テーブル内の各行が変更されるごとに、行が内部変更テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-170">For each change to each row in the user table, a row is added to the internal change table.</span></span> <span data-ttu-id="62c01-171">この行によって、一定のわずかなオーバーヘッドおよび主キー列のサイズと同じ可変のオーバーヘッドが生じます。</span><span class="sxs-lookup"><span data-stu-id="62c01-171">This row has a small fixed overhead plus a variable overhead equal to the size of the primary key columns.</span></span> <span data-ttu-id="62c01-172">この行には、アプリケーションによって設定されるオプションのコンテキスト情報が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="62c01-172">The row can contain optional context information set by an application.</span></span> <span data-ttu-id="62c01-173">また、列の追跡が有効になっている場合、列が変更されるごとに追跡テーブルで 4 バイトが必要になります。</span><span class="sxs-lookup"><span data-stu-id="62c01-173">And, if column tracking is enabled, each changed column requires 4 bytes in the tracking table.</span></span>  
  
-   <span data-ttu-id="62c01-174">トランザクションがコミットされるごとに、行が内部トランザクション テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="62c01-174">For each committed transaction, a row is added to an internal transaction table.</span></span>  
  
 <span data-ttu-id="62c01-175">その他の内部テーブルと同様に、変更追跡テーブルに使用される領域は、 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) ストアド プロシージャを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="62c01-175">As with other internal tables, you can determine the space used for the change tracking tables by using the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) stored procedure.</span></span> <span data-ttu-id="62c01-176">内部テーブルの名前は、次の例に示すように、 [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) カタログ ビューを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="62c01-176">The names of the internal tables can be obtained by using the [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) catalog view, as shown in the following example.</span></span>  
  
```sql  
sp_spaceused 'sys.change_tracking_309576141'  
sp_spaceused 'sys.syscommittab'  
```  
  
## <a name="see-also"></a><span data-ttu-id="62c01-177">参照</span><span class="sxs-lookup"><span data-stu-id="62c01-177">See Also</span></span>  
 <span data-ttu-id="62c01-178">[データ変更の追跡 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="62c01-178">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="62c01-179">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="62c01-179">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="62c01-180">[[データベースのプロパティ] &#40;[変更の追跡] ページ&#41;](../databases/database-properties-changetracking-page.md) </span><span class="sxs-lookup"><span data-stu-id="62c01-180">[Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) </span></span>  
 <span data-ttu-id="62c01-181">[ALTER DATABASE SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="62c01-181">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="62c01-182">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span><span class="sxs-lookup"><span data-stu-id="62c01-182">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span></span>  
 <span data-ttu-id="62c01-183">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span><span class="sxs-lookup"><span data-stu-id="62c01-183">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span></span>  
 <span data-ttu-id="62c01-184">[データ変更の追跡 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="62c01-184">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="62c01-185">[変更の追跡について &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="62c01-185">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 [<span data-ttu-id="62c01-186">変更データの処理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="62c01-186">Work with Change Data &#40;SQL Server&#41;</span></span>](work-with-change-data-sql-server.md)  
  
  
