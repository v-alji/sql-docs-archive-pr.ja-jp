---
title: 変更データ キャプチャの有効化と無効化 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- change data capture [SQL Server], enabling databases
- change data capture [SQL Server], disabling databases
- change data capture [SQL Server], disabling tables
ms.assetid: b741894f-d267-4b10-adfe-cbc14aa6caeb
author: rothja
ms.author: jroth
ms.openlocfilehash: df0a2fd4a2c6ffb2de58d6b52360d1730d0fa7df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640825"
---
# <a name="enable-and-disable-change-data-capture-sql-server"></a><span data-ttu-id="8029f-102">変更データ キャプチャの有効化と無効化 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8029f-102">Enable and Disable Change Data Capture (SQL Server)</span></span>
  <span data-ttu-id="8029f-103">このトピックでは、データベースおよびテーブルに対して変更データ キャプチャを有効または無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8029f-103">This topic describes how to enable and disable change data capture for a database and a table.</span></span>  
  
## <a name="enable-change-data-capture-for-a-database"></a><span data-ttu-id="8029f-104">データベースでの変更データ キャプチャの有効化</span><span class="sxs-lookup"><span data-stu-id="8029f-104">Enable Change Data Capture for a Database</span></span>  
 <span data-ttu-id="8029f-105">個々のテーブルに対してキャプチャ インスタンスを作成する前に、`sysadmin` 固定サーバー ロールのメンバーがデータベースで変更データ キャプチャを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8029f-105">Before a capture instance can be created for individual tables, a member of the `sysadmin` fixed server role must first enable the database for change data capture.</span></span> <span data-ttu-id="8029f-106">これは、データベース コンテキストでストアド プロシージャ [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) を実行することにより行われます。</span><span class="sxs-lookup"><span data-stu-id="8029f-106">This is done by running the stored procedure [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) in the database context.</span></span> <span data-ttu-id="8029f-107">この機能がデータベースで既に有効にされているかどうかを確認するには、`is_cdc_enabled` カタログ ビューの `sys.databases` 列をクエリします。</span><span class="sxs-lookup"><span data-stu-id="8029f-107">To determine if a database is already enabled, query the `is_cdc_enabled` column in the `sys.databases` catalog view.</span></span>  
  
 <span data-ttu-id="8029f-108">データベースで変更データ キャプチャを有効にすると、`cdc` スキーマ、`cdc` ユーザー、メタデータ テーブル、およびほかのシステム オブジェクトがデータベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-108">When a database is enabled for change data capture, the `cdc` schema, `cdc` user, metadata tables, and other system objects are created for the database.</span></span> <span data-ttu-id="8029f-109">`cdc` スキーマには、変更データ キャプチャのメタデータ テーブルが含まれています。ソース テーブルで変更データ キャプチャを有効にした後には、変更データのリポジトリとして機能する個々の変更テーブルも含まれます。</span><span class="sxs-lookup"><span data-stu-id="8029f-109">The `cdc` schema contains the change data capture metadata tables and, after source tables are enabled for change data capture, the individual change tables serve as a repository for change data.</span></span> <span data-ttu-id="8029f-110">`cdc` スキーマには変更データのクエリの実行に使用する関連のシステム関数も含まれています。</span><span class="sxs-lookup"><span data-stu-id="8029f-110">The `cdc` schema also contains associated system functions used to query for change data.</span></span>  
  
 <span data-ttu-id="8029f-111">変更データ キャプチャでは、`cdc` スキーマと `cdc` ユーザーのある目的の使用がクエリされます</span><span class="sxs-lookup"><span data-stu-id="8029f-111">Change data capture requires exclusive use of the `cdc` schema and `cdc` user.</span></span> <span data-ttu-id="8029f-112">*cdc* という名前のスキーマやデータベース ユーザーが現在データベースに存在する場合は、そのスキーマやユーザーを削除するか、名前を変更しないと、そのデータベースで変更データ キャプチャを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8029f-112">If either a schema or a database user named *cdc* currently exists in a database, the database cannot be enabled for change data capture until the schema and or user are dropped or renamed.</span></span>  
  
 <span data-ttu-id="8029f-113">データベースの有効化の例については、データベースでの変更データ キャプチャの有効化のテンプレートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8029f-113">See the Enable Database for Change Data Capture template for an example of enabling a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8029f-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でこのテンプレートを見つけるには、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックし、 **[SQL Server テンプレート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8029f-114">To locate the templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], go to **View**, click **Template Explorer**, and then select **SQL Server Templates**.</span></span> <span data-ttu-id="8029f-115">**Change Data Capture** はサブフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="8029f-115">**Change Data Capture** is a sub-folder.</span></span> <span data-ttu-id="8029f-116">このトピックで参照したすべてのテンプレートは、このフォルダー内にあります。</span><span class="sxs-lookup"><span data-stu-id="8029f-116">Under this folder, you will find all the templates referenced in this topic.</span></span> <span data-ttu-id="8029f-117">**ツール バーには** [テンプレート エクスプローラー] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] アイコンもあります。</span><span class="sxs-lookup"><span data-stu-id="8029f-117">There is also a **Template Explorer** icon on the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar.</span></span>  
  
```sql  
-- ====  
-- Enable Database for CDC template   
-- ====  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_db  
GO  
```  
  
## <a name="disable-change-data-capture-for-a-database"></a><span data-ttu-id="8029f-118">データベースでの変更データ キャプチャの無効化</span><span class="sxs-lookup"><span data-stu-id="8029f-118">Disable Change Data Capture for a Database</span></span>  
 <span data-ttu-id="8029f-119">固定サーバーロールのメンバーは、 `sysadmin` ストアドプロシージャ[sys. sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql)を実行してデータベースコンテキストで transact-sql&#41;&#40;し、データベースの変更データキャプチャを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8029f-119">A member of the `sysadmin` fixed server role can run the stored procedure [sys.sp_cdc_disable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) in the database context to disable change data capture for a database.</span></span> <span data-ttu-id="8029f-120">データベースを無効にする前に個々のテーブルを無効にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8029f-120">It is not necessary to disable individual tables before you disable the database.</span></span> <span data-ttu-id="8029f-121">データベースを無効にすると、`cdc` ユーザー、スキーマ、および変更データ キャプチャ ジョブを含む関連するすべての変更データ キャプチャ メタデータが削除されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-121">Disabling the database removes all associated change data capture metadata, including the `cdc` user and schema and the change data capture jobs.</span></span> <span data-ttu-id="8029f-122">ただし、変更データ キャプチャによって作成されたゲーティング ロールは自動的には削除されないので、明示的に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8029f-122">However, any gating roles created by change data capture will not be removed automatically and must be explicitly deleted.</span></span> <span data-ttu-id="8029f-123">この機能がデータベースで有効にされているかどうかを確認するには、sys.databases カタログ ビューの `is_cdc_enabled` 列をクエリします。</span><span class="sxs-lookup"><span data-stu-id="8029f-123">To determine if a database is enabled, query the `is_cdc_enabled` column in the sys.databases catalog view.</span></span>  
  
 <span data-ttu-id="8029f-124">変更データ キャプチャが有効になっているデータベースを削除すると、変更データ キャプチャ ジョブも自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-124">If a change data capture enabled database is dropped, change data capture jobs are automatically removed.</span></span>  
  
 <span data-ttu-id="8029f-125">データベースの無効化の例については、データベースでの変更データ キャプチャの無効化のテンプレートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8029f-125">See the Disable Database for Change Data Capture template for an example of disabling a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8029f-126">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でこのテンプレートを見つけるには、 **[表示]** 、 **[テンプレート エクスプローラー]** 、 **[SQL Server テンプレート]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8029f-126">To locate the templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], go to **View**, click **Template Explorer**, and then click **SQL Server Templates**.</span></span> <span data-ttu-id="8029f-127">**Change Data Capture** は、このトピックで参照されるすべてのテンプレートを含んだサブフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="8029f-127">**Change Data Capture** is a sub-folder where you will find all the templates that are referenced in this topic.</span></span> <span data-ttu-id="8029f-128">**ツール バーには** [テンプレート エクスプローラー] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] アイコンもあります。</span><span class="sxs-lookup"><span data-stu-id="8029f-128">There is also a **Template Explorer** icon on the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar.</span></span>  
  
```sql  
-- =======  
-- Disable Database for Change Data Capture template   
-- =======  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_db  
GO  
```  
  
## <a name="enable-change-data-capture-for-a-table"></a><span data-ttu-id="8029f-129">テーブルでの変更データ キャプチャの有効化</span><span class="sxs-lookup"><span data-stu-id="8029f-129">Enable Change Data Capture for a Table</span></span>  
 <span data-ttu-id="8029f-130">データベースで変更データ キャプチャが有効にされると、`db_owner` 固定データベース ロールのメンバーはストアド プロシージャ `sys.sp_cdc_enable_table` を使用して個々のソース テーブルに対してキャプチャ インスタンスを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8029f-130">After a database has been enabled for change data capture, members of the `db_owner` fixed database role can create a capture instance for individual source tables by using the stored procedure `sys.sp_cdc_enable_table`.</span></span> <span data-ttu-id="8029f-131">ソース テーブルで変更データ キャプチャが既に有効にされているかどうかを確認するには、`sys.tables` カタログ ビューの is_tracked_by_cdc 列を調べます。</span><span class="sxs-lookup"><span data-stu-id="8029f-131">To determine whether a source table has already been enabled for change data capture, examine the is_tracked_by_cdc column in the `sys.tables` catalog view.</span></span>  
  
 <span data-ttu-id="8029f-132">キャプチャ インスタンスの作成時に、次のオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8029f-132">The following options can be specified when creating a capture instance:</span></span>  
  
 <span data-ttu-id="8029f-133">`Columns in the source table to be captured`.</span><span class="sxs-lookup"><span data-stu-id="8029f-133">`Columns in the source table to be captured`.</span></span>  
  
 <span data-ttu-id="8029f-134">既定では、ソース テーブルのすべての列がキャプチャ対象列として識別されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-134">By default, all of the columns in the source table are identified as captured columns.</span></span> <span data-ttu-id="8029f-135">プライバシーやパフォーマンス上の理由から、列のサブセットのみを追跡する必要がある場合は、パラメーターを使用して *@captured_column_list* 列のサブセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="8029f-135">If only a subset of columns need to be tracked, such as for privacy or performance reasons, use the *@captured_column_list* parameter to specify the subset of columns.</span></span>  
  
 `A filegroup to contain the change table.`  
  
 <span data-ttu-id="8029f-136">既定では、変更テーブルはデータベースの既定のファイル グループにあります。</span><span class="sxs-lookup"><span data-stu-id="8029f-136">By default, the change table is located in the default filegroup of the database.</span></span> <span data-ttu-id="8029f-137">個々の変更テーブルの配置を制御するデータベース所有者は、パラメーターを使用して、 *@filegroup_name* キャプチャインスタンスに関連付けられている変更テーブルに特定のファイルグループを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8029f-137">Database owners who want to control the placement of individual change tables can use the *@filegroup_name* parameter to specify a particular filegroup for the change table associated with the capture instance.</span></span> <span data-ttu-id="8029f-138">指定するファイル グループはあらかじめ存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8029f-138">The named filegroup must already exist.</span></span> <span data-ttu-id="8029f-139">通常、変更テーブルはソース テーブルとは別のファイル グループに配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8029f-139">Generally, it is recommended that change tables be placed in a filegroup separate from source tables.</span></span> <span data-ttu-id="8029f-140">`Enable a Table Specifying Filegroup Option`パラメーターの使用例については、テンプレートを参照してください *@filegroup_name* 。</span><span class="sxs-lookup"><span data-stu-id="8029f-140">See the `Enable a Table Specifying Filegroup Option` template for an example showing use of the *@filegroup_name* parameter.</span></span>  
  
```sql  
-- =========  
-- Enable a Table Specifying Filegroup Option Template  
-- =========  
USE MyDB  
GO  
  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@filegroup_name = N'MyDB_CT',  
@supports_net_changes = 1  
GO  
```  
  
 `A role for controlling access to a change table.`  
  
 <span data-ttu-id="8029f-141">名前付きのロールの目的は、変更データへのアクセスを制御することです。</span><span class="sxs-lookup"><span data-stu-id="8029f-141">The purpose of the named role is to control access to the change data.</span></span> <span data-ttu-id="8029f-142">指定されるロールは、既存の固定サーバー ロールの場合もデータベース ロールの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8029f-142">The specified role can be an existing fixed server role or a database role.</span></span> <span data-ttu-id="8029f-143">指定のロールが存在しない場合は、その名前のデータベース ロールが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-143">If the specified role does not already exist, a database role of that name is created automatically.</span></span> <span data-ttu-id="8029f-144">`sysadmin` ロールのメンバーと `db_owner` ロールのメンバーには、変更テーブルのデータへのフル アクセス権が与えられます。</span><span class="sxs-lookup"><span data-stu-id="8029f-144">Members of either the `sysadmin` or `db_owner` role have full access to the data in the change tables.</span></span> <span data-ttu-id="8029f-145">他のすべてのユーザーには、ソース テーブルのすべてのキャプチャ対象列に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8029f-145">All other users must have SELECT permission on all the captured columns of the source table.</span></span> <span data-ttu-id="8029f-146">さらに、ロールが指定されている場合、`sysadmin` ロールまたは `db_owner` ロールのいずれのメンバーでもないユーザーも、指定のロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8029f-146">In addition, when a role is specified, users who are not members of either the `sysadmin` or `db_owner` role must also be members of the specified role.</span></span>  
  
 <span data-ttu-id="8029f-147">ゲートロールを使用しない場合は、パラメーターを明示的に *@role_name* NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="8029f-147">If you do not want to use a gating role, explicitly set the *@role_name* parameter to NULL.</span></span> <span data-ttu-id="8029f-148">ゲーティング ロールなしでテーブルを有効にする例については、`Enable a Table Without Using a Gating Role` のテンプレートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8029f-148">See the `Enable a Table Without Using a Gating Role` template for an example of enabling a table without a gating role.</span></span>  
  
```sql  
-- =========  
-- Enable a Table Without Using a Gating Role template   
-- =========  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = NULL,  
@supports_net_changes = 1  
GO  
  
```  
  
 `A function to query for net changes.`  
  
 <span data-ttu-id="8029f-149">キャプチャ インスタンスには、定義した期間内に発生したすべての変更テーブル エントリを返すためのテーブル値関数が常に含まれています。</span><span class="sxs-lookup"><span data-stu-id="8029f-149">A capture instance will always include a table valued function for returning all change table entries that occurred within a defined interval.</span></span> <span data-ttu-id="8029f-150">この関数の名前は、"cdc.fn_cdc_get_all_changes_" の後ろにキャプチャ インスタンス名を付加したものです。</span><span class="sxs-lookup"><span data-stu-id="8029f-150">This function is named by appending the capture instance name to "cdc.fn_cdc_get_all_changes_".</span></span> <span data-ttu-id="8029f-151">詳細については、「[cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8029f-151">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="8029f-152">パラメーターが1に設定されている場合は *@supports_net_changes* 、キャプチャインスタンスに対しても net changes 関数が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-152">If the parameter *@supports_net_changes* is set to 1, a net changes function is also generated for the capture instance.</span></span> <span data-ttu-id="8029f-153">この関数では、呼び出しで指定した期間内に変更された各行についてそれぞれ 1 つの変更のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-153">This function returns only one change for each distinct row changed in the interval specified in the call.</span></span> <span data-ttu-id="8029f-154">詳細については、「[cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8029f-154">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="8029f-155">差分変更のクエリをサポートするには、行を一意に識別するための主キーまたは一意のインデックスがソース テーブルに必要です。</span><span class="sxs-lookup"><span data-stu-id="8029f-155">To support net changes queries, the source table must have a primary key or unique index to uniquely identify rows.</span></span> <span data-ttu-id="8029f-156">一意のインデックスを使用する場合は、パラメーターを使用してインデックスの名前を指定する必要があり *@index_name* ます。</span><span class="sxs-lookup"><span data-stu-id="8029f-156">If a unique index is used, the name of the index must be specified using the *@index_name* parameter.</span></span> <span data-ttu-id="8029f-157">主キーまたは一意のインデックスで定義した列は、キャプチャするソース列の一覧に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8029f-157">The columns defined in the primary key or unique index must be included in the list of source columns to be captured.</span></span>  
  
 <span data-ttu-id="8029f-158">両方のクエリ関数を使用したキャプチャ インスタンスの作成例については、`Enable a Table for All and Net Changes Queries`のテンプレートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8029f-158">See the `Enable a Table for All and Net Changes Queries` template for an example demonstrating the creation of a capture instance with both query functions.</span></span>  
  
```sql  
-- =============  
-- Enable a Table for All and Net Changes Queries template   
-- =============  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@supports_net_changes = 1  
GO  
```  
  
> [!NOTE]
>  <span data-ttu-id="8029f-159">既存の主キーを持つテーブルで変更データキャプチャが有効になっていて、 *@index_name* 別の一意のインデックスを識別するためにパラメーターが使用されていない場合、変更データキャプチャ機能では主キーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-159">If change data capture is enabled on a table with an existing primary key, and the *@index_name* parameter is not used to identify an alternative unique index, the change data capture feature will use the primary key.</span></span> <span data-ttu-id="8029f-160">その後は、テーブルの変更データ キャプチャを無効にしてからでなければ、主キーに変更を加えることはできません。</span><span class="sxs-lookup"><span data-stu-id="8029f-160">Subsequent changes to the primary key will not be allowed without first disabling change data capture for the table.</span></span> <span data-ttu-id="8029f-161">これは、変更データ キャプチャの構成時に差分変更のクエリのサポートが要求されたかどうかには関係ありません。</span><span class="sxs-lookup"><span data-stu-id="8029f-161">This is true regardless of whether support for net changes queries was requested when change data capture was configured.</span></span> <span data-ttu-id="8029f-162">変更データ キャプチャが有効化された時点でテーブルに主キーがない場合、その後追加された主キーは変更データ キャプチャでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-162">If there is no primary key on a table at the time it is enabled for change data capture, the subsequent addition of a primary key is ignored by change data capture.</span></span> <span data-ttu-id="8029f-163">変更データ キャプチャでは、テーブルで変更データ キャプチャが有効化された後で作成された主キーは使用しないので、キーおよびキー列は制限なく削除できます。</span><span class="sxs-lookup"><span data-stu-id="8029f-163">Because change data capture will not use a primary key that is created after the table was enabled, the key and key columns can be removed without restrictions.</span></span>  
  
## <a name="disable-change-data-capture-for-a-table"></a><span data-ttu-id="8029f-164">テーブルでの変更データ キャプチャの無効化</span><span class="sxs-lookup"><span data-stu-id="8029f-164">Disable Change Data Capture for a Table</span></span>  
 <span data-ttu-id="8029f-165">`db_owner` 固定データベース ロールのメンバーは、ストアド プロシージャ `sys.sp_cdc_disable_table` を使用して個々のソース テーブルのキャプチャ インスタンスを削除できます。</span><span class="sxs-lookup"><span data-stu-id="8029f-165">Members of the `db_owner` fixed database role can remove a capture instance for individual source tables by using the stored procedure `sys.sp_cdc_disable_table`.</span></span> <span data-ttu-id="8029f-166">ソース テーブルで変更データ キャプチャが現在有効にされているかどうかを確認するには、`is_tracked_by_cdc` カタログ ビューの `sys.tables` 列を調べます。</span><span class="sxs-lookup"><span data-stu-id="8029f-166">To determine whether a source table is currently enabled for change data capture, examine the `is_tracked_by_cdc` column in the `sys.tables` catalog view.</span></span> <span data-ttu-id="8029f-167">無効化の後、データベースに対して有効なテーブルがない場合は、変更データ キャプチャ ジョブも削除されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-167">If there are no tables enabled for the database after the disabling takes place, the change data capture jobs are also removed.</span></span>  
  
 <span data-ttu-id="8029f-168">変更データ キャプチャが有効になっているテーブルを削除すると、そのテーブルに関連する変更データ キャプチャ メタデータも自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="8029f-168">If a change data capture-enabled table is dropped, change data capture metadata that is associated with the table is automatically removed.</span></span>  
  
 <span data-ttu-id="8029f-169">テーブルの無効化の例については、テーブルでのキャプチャ インスタンスの無効化のテンプレートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8029f-169">See the Disable a Capture Instance for a Table template for an example of disabling a table.</span></span>  
  
```sql  
-- =====  
-- Disable a Capture Instance for a Table template   
-- =====  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@capture_instance = N'dbo_MyTable'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8029f-170">参照</span><span class="sxs-lookup"><span data-stu-id="8029f-170">See Also</span></span>  
 <span data-ttu-id="8029f-171">[データ変更の追跡 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8029f-171">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="8029f-172">[変更データ キャプチャについて &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8029f-172">[About Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span></span>  
 <span data-ttu-id="8029f-173">[変更データの処理 &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8029f-173">[Work with Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span></span>  
 [<span data-ttu-id="8029f-174">変更データ キャプチャの管理と監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8029f-174">Administer and Monitor Change Data Capture &#40;SQL Server&#41;</span></span>](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
