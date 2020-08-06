---
title: メタデータ表示の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- subcomponents visibility [SQL Server]
- metadata [SQL Server], visibility
- permissions [SQL Server], metadata access
- viewing metadata
- objects [SQL Server], metadata
- displaying metadata
- database metadata [SQL Server]
- metadata [SQL Server], permissions
ms.assetid: 50d2e015-05ae-4014-a1cd-4de7866ad651
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5198dc4ba4e81bc1d7a8dd2411da59da81596102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641570"
---
# <a name="metadata-visibility-configuration"></a><span data-ttu-id="e24b6-102">メタデータ表示の構成</span><span class="sxs-lookup"><span data-stu-id="e24b6-102">Metadata Visibility Configuration</span></span>
  <span data-ttu-id="e24b6-103">メタデータの表示は、ユーザーが所有するセキュリティ保護可能なリソース、またはそのユーザーが権限を許可されているセキュリティ保護可能なリソースに制限されています。</span><span class="sxs-lookup"><span data-stu-id="e24b6-103">The visibility of metadata is limited to securables that a user either owns or on which the user has been granted some permission.</span></span> <span data-ttu-id="e24b6-104">たとえば、次のクエリを実行すると、ユーザーがテーブル `myTable`に対する SELECT または INSERT 権限を許可されている場合は、1 行が返されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-104">For example, the following query returns a row if the user has been granted a permission such as SELECT or INSERT on the table `myTable`.</span></span>  
  
```  
SELECT name, object_id  
FROM sys.tables  
WHERE name = 'myTable';  
GO  
```  
  
 <span data-ttu-id="e24b6-105">ただし、ユーザーが `myTable`での権限を許可されていない場合は、空の結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-105">However, if the user does not have any permission on `myTable`, the query returns an empty result set.</span></span>  
  
## <a name="scope-and-impact-of-metadata-visibility-configuration"></a><span data-ttu-id="e24b6-106">メタデータ表示の構成のスコープと影響</span><span class="sxs-lookup"><span data-stu-id="e24b6-106">Scope and Impact of Metadata Visibility Configuration</span></span>  
 <span data-ttu-id="e24b6-107">メタデータ表示の構成は、次のセキュリティ保護可能なメタデータにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-107">Metadata visibility configuration only applies to the following securables.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e24b6-108">カタログ ビュー</span><span class="sxs-lookup"><span data-stu-id="e24b6-108">Catalog views</span></span>|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="e24b6-109">**sp_help** ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e24b6-109">**sp_help** stored procedures</span></span>|  
|<span data-ttu-id="e24b6-110">メタデータ公開組み込み関数</span><span class="sxs-lookup"><span data-stu-id="e24b6-110">Metadata exposing built-in functions</span></span>|<span data-ttu-id="e24b6-111">情報スキーマ ビュー</span><span class="sxs-lookup"><span data-stu-id="e24b6-111">Information schema views</span></span>|  
|<span data-ttu-id="e24b6-112">互換性ビュー</span><span class="sxs-lookup"><span data-stu-id="e24b6-112">Compatibility views</span></span>|<span data-ttu-id="e24b6-113">拡張プロパティ</span><span class="sxs-lookup"><span data-stu-id="e24b6-113">Extended properties</span></span>|  
  
 <span data-ttu-id="e24b6-114">メタデータ表示の構成は、次のセキュリティ保護可能なメタデータには適用されません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-114">Metadata visibility configuration does not apply to the following securables.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e24b6-115">ログ配布システム テーブル</span><span class="sxs-lookup"><span data-stu-id="e24b6-115">Log shipping system tables</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e24b6-116">エージェント システム テーブル</span><span class="sxs-lookup"><span data-stu-id="e24b6-116">Agent system tables</span></span>|  
|<span data-ttu-id="e24b6-117">データベース メンテナンス プラン システム テーブル</span><span class="sxs-lookup"><span data-stu-id="e24b6-117">Database maintenance plan system tables</span></span>|<span data-ttu-id="e24b6-118">バックアップ システム テーブル</span><span class="sxs-lookup"><span data-stu-id="e24b6-118">Backup system tables</span></span>|  
|<span data-ttu-id="e24b6-119">レプリケーション システム テーブル</span><span class="sxs-lookup"><span data-stu-id="e24b6-119">Replication system tables</span></span>|<span data-ttu-id="e24b6-120">レプリケーション ストアド プロシージャと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **sp_help** ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e24b6-120">Replication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **sp_help** stored procedures</span></span>|  
  
 <span data-ttu-id="e24b6-121">メタデータへのアクセスを制限すると、次のような影響があります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-121">Limited metadata accessibility means the following:</span></span>  
  
-   <span data-ttu-id="e24b6-122">メタデータへの **パブリック** なアクセスを前提とするアプリケーションは機能しません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-122">Applications that assume **public** metadata access will break.</span></span>  
  
-   <span data-ttu-id="e24b6-123">システム ビューへのクエリを実行しても、行のサブセットまたは空の結果セットしか返されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-123">Queries on system views might only return a subset of rows, or sometimes an empty result set.</span></span>  
  
-   <span data-ttu-id="e24b6-124">OBJECTPROPERTYEX などのメタデータ生成組み込み関数を実行すると、NULL 値が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-124">Metadata-emitting, built-in functions such as OBJECTPROPERTYEX may return NULL.</span></span>  
  
-   <span data-ttu-id="e24b6-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)] **sp_help** ストアド プロシージャを実行しても、行のサブセットまたは NULL 値しか返されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-125">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] **sp_help** stored procedures might return only a subset of rows, or NULL.</span></span>  
  
 <span data-ttu-id="e24b6-126">ストアド プロシージャやトリガーなどの SQL モジュールは、呼び出し元のセキュリティ コンテキストで実行されるので、メタデータへのアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-126">SQL modules, such as stored procedures and triggers, run under the security context of the caller and, therefore, have limited metadata accessibility.</span></span> <span data-ttu-id="e24b6-127">たとえば次のコードでは、ストアド プロシージャから、呼び出し元に権限のないテーブル `myTable` のメタデータへのアクセスが試行されると、空の結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-127">For example, in the following code, when the stored procedure tries to access metadata for the table `myTable` on which the caller has no rights, an empty result set is returned.</span></span> <span data-ttu-id="e24b6-128">以前のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では行が返されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-128">In earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a row is returned.</span></span>  
  
```  
CREATE PROCEDURE assumes_caller_can_access_metadata  
BEGIN  
SELECT name, id   
FROM sysobjects   
WHERE name = 'myTable';  
END;  
GO  
```  
  
 <span data-ttu-id="e24b6-129">呼び出し元でのメタデータの表示を可能にするには、呼び出し元にオブジェクト レベル、データベース レベル、サーバー レベルのいずれかの適切なスコープで VIEW DEFINITION 権限を許可できます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-129">To allow callers to view metadata, you can grant the callers VIEW DEFINITION permission at an appropriate scope: object level, database level or server level.</span></span> <span data-ttu-id="e24b6-130">したがって、上記の例では、呼び出し元に `myTable`に対する VIEW DEFINITION 権限が許可されていると、ストアド プロシージャから行が返されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-130">Therefore, in the previous example, if the caller has VIEW DEFINITION permission on `myTable`, the stored procedure returns a row.</span></span> <span data-ttu-id="e24b6-131">詳細については、「[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)」と「[GRANT &#40;データベースの権限の許可&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e24b6-131">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) and [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
 <span data-ttu-id="e24b6-132">また、ストアド プロシージャを所有者の資格情報で実行するように変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-132">You can also modify the stored procedure so that it executes under the credentials of the owner.</span></span> <span data-ttu-id="e24b6-133">プロシージャの所有者とテーブルの所有者が同じ場合は、所有権の継承が適用されます。したがって、プロシージャの所有者のセキュリティ コンテキストにより、 `myTable`のメタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-133">When the procedure owner and the table owner are the same owner, ownership chaining applies, and the security context of the procedure owner enables access to the metadata for `myTable`.</span></span> <span data-ttu-id="e24b6-134">このシナリオで次のコードを実行すると、メタデータの行が呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-134">Under this scenario, the following code returns a row of metadata to the caller.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e24b6-135">次の例で使用するのは、 [sys.sysobjects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 互換性ビューではなく [sys.objects](/sql/relational-databases/system-compatibility-views/sys-sysobjects-transact-sql) カタログ ビューです。</span><span class="sxs-lookup"><span data-stu-id="e24b6-135">The following example uses the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view instead of the [sys.sysobjects](/sql/relational-databases/system-compatibility-views/sys-sysobjects-transact-sql) compatibility view.</span></span>  
  
```  
CREATE PROCEDURE does_not_assume_caller_can_access_metadata  
WITH EXECUTE AS OWNER  
AS  
BEGIN  
SELECT name, id  
FROM sys.objects   
WHERE name = 'myTable'   
END;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e24b6-136">EXECUTE AS を使用すると、一時的に呼び出し元のセキュリティ コンテキストに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-136">You can use EXECUTE AS to temporarily switch to the security context of the caller.</span></span> <span data-ttu-id="e24b6-137">詳細については、「[EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e24b6-137">For more information, see [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql).</span></span>  
  
## <a name="benefits-and-limits-of-metadata-visibility-configuration"></a><span data-ttu-id="e24b6-138">メタデータ表示構成の利点と制限事項</span><span class="sxs-lookup"><span data-stu-id="e24b6-138">Benefits and Limits of Metadata Visibility Configuration</span></span>  
 <span data-ttu-id="e24b6-139">メタデータ表示の構成は、セキュリティ計画全体にとって重要な役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="e24b6-139">Metadata visibility configuration can play an important role in your overall security plan.</span></span> <span data-ttu-id="e24b6-140">ただし、上級ユーザーや事前に指定されたユーザーが一部のメタデータを強制的に公開できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-140">However, there are cases in which a skilled and determined user can force the disclosure of some metadata.</span></span> <span data-ttu-id="e24b6-141">メタデータの権限の配置は、数ある堅牢な防御策の 1 つとして行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e24b6-141">We recommend that you deploy metadata permissions as one of many defenses-in-depth.</span></span>  
  
 <span data-ttu-id="e24b6-142">理論上は、クエリで述語の評価の順序を操作することで、エラー メッセージ内にメタデータの生成を強制することも可能です。</span><span class="sxs-lookup"><span data-stu-id="e24b6-142">It is theoretically possible to force the emission of metadata in error messages by manipulating the order of predicate evaluation in queries.</span></span> <span data-ttu-id="e24b6-143">このような *試行錯誤による攻撃* は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に固有のものではありません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-143">The possibility of such *trial-and-error attacks* is not specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e24b6-144">関係代数で許可されている結合変換および相互変換に伴う場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-144">It is implied by the associative and commutative transformations permitted in relational algebra.</span></span> <span data-ttu-id="e24b6-145">このリスクは、エラー メッセージで返される情報を制限することで緩和できます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-145">You can mitigate this risk by limiting the information returned in error messages.</span></span> <span data-ttu-id="e24b6-146">この方法でメタデータの表示を制限するには、トレース フラグ 3625 を使用してサーバーを起動します。</span><span class="sxs-lookup"><span data-stu-id="e24b6-146">To further restrict the visibility of metadata in this way, you can start the server with trace flag 3625.</span></span> <span data-ttu-id="e24b6-147">このトレース フラグは、エラー メッセージで表示される情報の量を制限します。</span><span class="sxs-lookup"><span data-stu-id="e24b6-147">This trace flag limits the amount of information shown in error messages.</span></span> <span data-ttu-id="e24b6-148">そのため、この方法を使用することで、メタデータの公開が強制されることを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-148">In turn, this helps to prevent forced disclosures.</span></span> <span data-ttu-id="e24b6-149">その代わりに、エラー メッセージは簡潔になり、デバッグに使用するのは困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-149">The tradeoff is that error messages will be terse and might be difficult to use for debugging purposes.</span></span> <span data-ttu-id="e24b6-150">詳細については、「[データベース エンジン サービスのスタートアップ オプション](../../database-engine/configure-windows/database-engine-service-startup-options.md)」と「[トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e24b6-150">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md) and [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
 <span data-ttu-id="e24b6-151">次のメタデータは公開を強制されません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-151">The following metadata is not subject to forced disclosure:</span></span>  
  
-   <span data-ttu-id="e24b6-152">**sys.servers** の **provider_string**列に格納されている値。</span><span class="sxs-lookup"><span data-stu-id="e24b6-152">The value stored in the **provider_string** column of **sys.servers**.</span></span> <span data-ttu-id="e24b6-153">ALTER ANY LINKED SERVER 権限が許可されていないユーザーには、この列に NULL 値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-153">A user that does not have ALTER ANY LINKED SERVER permission will see a NULL value in this column.</span></span>  
  
-   <span data-ttu-id="e24b6-154">ストアド プロシージャやトリガーなどのユーザー定義オブジェクトのソース定義。</span><span class="sxs-lookup"><span data-stu-id="e24b6-154">Source definition of a user-defined object such as a stored procedure or trigger.</span></span> <span data-ttu-id="e24b6-155">ソース コードは、次のいずれかの条件を満たしている場合のみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-155">The source code is visible only when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="e24b6-156">ユーザーがオブジェクトに対する VIEW DEFINITION 権限を許可されている場合。</span><span class="sxs-lookup"><span data-stu-id="e24b6-156">The user has VIEW DEFINITION permission on the object.</span></span>  
  
    -   <span data-ttu-id="e24b6-157">ユーザーがオブジェクトに対する VIEW DEFINITION 権限を拒否されておらず、そのオブジェクトに対する CONTROL、ALTER、TAKE OWNERSHIP のいずれかの権限を許可されている場合。</span><span class="sxs-lookup"><span data-stu-id="e24b6-157">The user has not been denied VIEW DEFINITION permission on the object and has CONTROL, ALTER, or TAKE OWNERSHIP permission on the object.</span></span> <span data-ttu-id="e24b6-158">他のすべてのユーザーには NULL 値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-158">All other users will see NULL.</span></span>  
  
-   <span data-ttu-id="e24b6-159">次のカタログ ビューの定義列。</span><span class="sxs-lookup"><span data-stu-id="e24b6-159">The definition columns found in the following catalog views:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="e24b6-160">**sys.all_sql_modules**</span><span class="sxs-lookup"><span data-stu-id="e24b6-160">**sys.all_sql_modules**</span></span>|<span data-ttu-id="e24b6-161">**sys.sql_modules**</span><span class="sxs-lookup"><span data-stu-id="e24b6-161">**sys.sql_modules**</span></span>|  
    |<span data-ttu-id="e24b6-162">**sys.server_sql_modules**</span><span class="sxs-lookup"><span data-stu-id="e24b6-162">**sys.server_sql_modules**</span></span>|<span data-ttu-id="e24b6-163">**sys.check_constraints**</span><span class="sxs-lookup"><span data-stu-id="e24b6-163">**sys.check_constraints**</span></span>|  
    |<span data-ttu-id="e24b6-164">**sys.default_constraints**</span><span class="sxs-lookup"><span data-stu-id="e24b6-164">**sys.default_constraints**</span></span>|<span data-ttu-id="e24b6-165">**sys.computed_columns**</span><span class="sxs-lookup"><span data-stu-id="e24b6-165">**sys.computed_columns**</span></span>|  
    |<span data-ttu-id="e24b6-166">**sys.numbered_procedures**</span><span class="sxs-lookup"><span data-stu-id="e24b6-166">**sys.numbered_procedures**</span></span>||  
  
-   <span data-ttu-id="e24b6-167">**syscomments** 互換性ビューの **ctext** 列。</span><span class="sxs-lookup"><span data-stu-id="e24b6-167">The **ctext** column in the **syscomments** compatibility view.</span></span>  
  
-   <span data-ttu-id="e24b6-168">**sp_helptext** プロシージャの出力。</span><span class="sxs-lookup"><span data-stu-id="e24b6-168">The output of the **sp_helptext** procedure.</span></span>  
  
-   <span data-ttu-id="e24b6-169">情報スキーマ ビューの次の列。</span><span class="sxs-lookup"><span data-stu-id="e24b6-169">The following columns in the information schema views:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="e24b6-170">INFORMATION_SCHEMA.CHECK_CONSTRAINTS.CHECK_CLAUSE</span><span class="sxs-lookup"><span data-stu-id="e24b6-170">INFORMATION_SCHEMA.CHECK_CONSTRAINTS.CHECK_CLAUSE</span></span>|<span data-ttu-id="e24b6-171">INFORMATION_SCHEMA.COLUMNS.COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e24b6-171">INFORMATION_SCHEMA.COLUMNS.COLUMN_DEFAULT</span></span>|  
    |<span data-ttu-id="e24b6-172">INFORMATION_SCHEMA.DOMAINS.DOMAIN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e24b6-172">INFORMATION_SCHEMA.DOMAINS.DOMAIN_DEFAULT</span></span>|<span data-ttu-id="e24b6-173">INFORMATION_SCHEMA.ROUTINE_COLUMNS.COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e24b6-173">INFORMATION_SCHEMA.ROUTINE_COLUMNS.COLUMN_DEFAULT</span></span>|  
    |<span data-ttu-id="e24b6-174">INFORMATION_SCHEMA.ROUTINES.ROUTINE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e24b6-174">INFORMATION_SCHEMA.ROUTINES.ROUTINE_DEFINITION</span></span>|<span data-ttu-id="e24b6-175">INFORMATION_SCHEMA.VIEWS.VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e24b6-175">INFORMATION_SCHEMA.VIEWS.VIEW_DEFINITION</span></span>|  
  
-   <span data-ttu-id="e24b6-176">OBJECT_DEFINITION() 関数</span><span class="sxs-lookup"><span data-stu-id="e24b6-176">OBJECT_DEFINITION() function</span></span>  
  
-   <span data-ttu-id="e24b6-177">**sys.sql_logins**の password_hash 列に格納された値。</span><span class="sxs-lookup"><span data-stu-id="e24b6-177">The value stored in the password_hash column of **sys.sql_logins**.</span></span>  <span data-ttu-id="e24b6-178">CONTROL SERVER 権限が許可されていないユーザーには、この列に NULL 値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-178">A user that does not have CONTROL SERVER permission will see a NULL value in this column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e24b6-179">組み込みシステム プロシージャと組み込みシステム関数の SQL 定義は、 **sys.system_sql_modules** カタログ ビュー、 **sp_helptext** ストアド プロシージャ、および OBJECT_DEFINITION() 関数を使用すると公開されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-179">The SQL definitions of built-in system procedures and functions are publicly visible through the **sys.system_sql_modules** catalog view, the **sp_helptext** stored procedure, and the OBJECT_DEFINITION() function.</span></span>  
  
## <a name="general-principles-of-metadata-visibility"></a><span data-ttu-id="e24b6-180">メタデータ表示の一般原則</span><span class="sxs-lookup"><span data-stu-id="e24b6-180">General Principles of Metadata Visibility</span></span>  
 <span data-ttu-id="e24b6-181">次に、メタデータの表示に関して考慮する必要がある一般原則を示します。</span><span class="sxs-lookup"><span data-stu-id="e24b6-181">The following are some general principles to consider regarding metadata visibility:</span></span>  
  
-   <span data-ttu-id="e24b6-182">固定ロールの暗黙の権限</span><span class="sxs-lookup"><span data-stu-id="e24b6-182">Fixed roles implicit permissions</span></span>  
  
-   <span data-ttu-id="e24b6-183">権限のスコープ</span><span class="sxs-lookup"><span data-stu-id="e24b6-183">Scope of permissions</span></span>  
  
-   <span data-ttu-id="e24b6-184">DENY の優先</span><span class="sxs-lookup"><span data-stu-id="e24b6-184">Precedence of DENY</span></span>  
  
-   <span data-ttu-id="e24b6-185">サブコンポーネントのメタデータの表示</span><span class="sxs-lookup"><span data-stu-id="e24b6-185">Visibility of subcomponent metadata</span></span>  
  
### <a name="fixed-roles-and-implicit-permissions"></a><span data-ttu-id="e24b6-186">固定ロールと暗黙の権限</span><span class="sxs-lookup"><span data-stu-id="e24b6-186">Fixed Roles and Implicit Permissions</span></span>  
 <span data-ttu-id="e24b6-187">固定ロールでアクセスできるメタデータは、それらのメタデータに対応する暗黙の権限によって決まります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-187">Metadata that can be accessed by fixed roles depends upon their corresponding implicit permissions.</span></span>  
  
### <a name="scope-of-permissions"></a><span data-ttu-id="e24b6-188">権限のスコープ</span><span class="sxs-lookup"><span data-stu-id="e24b6-188">Scope of Permissions</span></span>  
 <span data-ttu-id="e24b6-189">あるスコープで権限が許可されていると、そのスコープのメタデータと、そのスコープに含まれるすべてのスコープのメタデータを表示できることになります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-189">Permissions at one scope imply the ability to see metadata at that scope and at all enclosed scopes.</span></span> <span data-ttu-id="e24b6-190">たとえば、あるスキーマに対する SELECT 権限が許可されると、そのスキーマに含まれるすべてのセキュリティ保護可能なメタデータに対する SELECT 権限がユーザーに許可されることになります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-190">For example, SELECT permission on a schema implies that the grantee has SELECT permission on all securables that are contained by that schema.</span></span> <span data-ttu-id="e24b6-191">したがって、あるスキーマに対する SELECT 権限を許可すると、ユーザーはそのスキーマと、スキーマ内のすべてのテーブル、ビュー、関数、プロシージャ、キュー、シノニム、型、および XML スキーマ コレクションのメタデータも表示できます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-191">The granting of SELECT permission on a schema therefore enables a user to see the metadata of the schema and also all tables, views, functions, procedures, queues, synonyms, types, and XML schema collections within it.</span></span> <span data-ttu-id="e24b6-192">スコープの詳細については、「[権限の階層 &#40;データベース エンジン&#41;](permissions-hierarchy-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e24b6-192">For more information about scopes, see [Permissions Hierarchy &#40;Database Engine&#41;](permissions-hierarchy-database-engine.md).</span></span>  
  
### <a name="precedence-of-deny"></a><span data-ttu-id="e24b6-193">DENY の優先</span><span class="sxs-lookup"><span data-stu-id="e24b6-193">Precedence of DENY</span></span>  
 <span data-ttu-id="e24b6-194">通常、DENY は他の権限よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-194">DENY typically takes precedence over other permissions.</span></span> <span data-ttu-id="e24b6-195">たとえば、データベース ユーザーがあるスキーマに対する EXECUTE 権限を許可されていても、そのスキーマ内にあるストアド プロシージャに対する EXECUTE 権限が拒否されている場合は、そのストアド プロシージャのメタデータを表示できません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-195">For example, if a database user is granted EXECUTE permission on a schema but has been denied EXECUTE permission on a stored procedure in that schema, the user cannot view the metadata for that stored procedure.</span></span>  
  
 <span data-ttu-id="e24b6-196">また、ユーザーがあるスキーマに対する EXECUTE 権限を拒否されている場合は、そのスキーマ内のストアド プロシージャに対して EXECUTE 権限を許可されていても、そのストアド プロシージャのメタデータを表示できません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-196">Additionally, if a user is denied EXECUTE permission on a schema but has been granted EXECUTE permission on a stored procedure in that schema, the user cannot view the metadata for that stored procedure.</span></span>  
  
 <span data-ttu-id="e24b6-197">もう 1 つの例として、ユーザーがあるストアド プロシージャに対する EXECUTE 権限を許可および拒否されている場合 (さまざまなロールのメンバーシップに属しているとこのような状況が生じます)、DENY が優先されるので、そのストアド プロシージャのメタデータを表示できません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-197">For another example, if a user has been granted and denied EXECUTE permission on a stored procedure, which is possible through your various role memberships, DENY takes precedence and the user cannot view the metadata of the stored procedure.</span></span>  
  
### <a name="visibility-of-subcomponent-metadata"></a><span data-ttu-id="e24b6-198">サブコンポーネントのメタデータの表示</span><span class="sxs-lookup"><span data-stu-id="e24b6-198">Visibility of Subcomponent Metadata</span></span>  
 <span data-ttu-id="e24b6-199">インデックス、CHECK 制約、トリガーなどのサブコンポーネントが表示されるかどうかは、そのサブコンポーネントの親に対する権限によって決まります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-199">The visibility of subcomponents, such as indexes, check constraints, and triggers is determined by permissions on the parent.</span></span> <span data-ttu-id="e24b6-200">これらのサブコンポーネントには、権限を許可できません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-200">These subcomponents do not have grantable permissions.</span></span> <span data-ttu-id="e24b6-201">たとえば、ユーザーがあるテーブルに対していくつかの権限を許可されていると、そのテーブル、列、インデックス、CHECK 制約、トリガー、およびその他のサブコンポーネントのメタデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-201">For example, if a user has been granted some permission on a table, the user can view the metadata for the tables, columns, indexes, check constraints, triggers, and other such subcomponents.</span></span>  
  
#### <a name="metadata-that-is-accessible-to-all-database-users"></a><span data-ttu-id="e24b6-202">すべてのデータベース ユーザーがアクセスできるメタデータ</span><span class="sxs-lookup"><span data-stu-id="e24b6-202">Metadata That Is Accessible to All Database Users</span></span>  
 <span data-ttu-id="e24b6-203">一部のメタデータは、特定のデータベースのすべてのユーザーがアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-203">Some metadata must be accessible to all users in a specific database.</span></span> <span data-ttu-id="e24b6-204">たとえば、ファイル グループには許可できる権限がないので、ファイル グループのメタデータを表示するための権限をユーザーに許可できません。</span><span class="sxs-lookup"><span data-stu-id="e24b6-204">For example, filegroups do not have conferrable permissions; therefore, a user cannot be granted permission to view the metadata of a filegroup.</span></span> <span data-ttu-id="e24b6-205">ただし、テーブルを作成できるすべてのユーザーは、ファイル グループのメタデータにアクセスして、CREATE TABLE ステートメントの ON *filegroup* 句または TEXTIMAGE_ON *filegroup* 句を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e24b6-205">However, any user that can create a table must be able to access filegroup metadata to use the ON *filegroup* or TEXTIMAGE_ON *filegroup* clauses of the CREATE TABLE statement.</span></span>  
  
 <span data-ttu-id="e24b6-206">DB_ID() 関数と DB_NAME() 関数で返されるメタデータは、すべてのユーザーが表示できます。</span><span class="sxs-lookup"><span data-stu-id="e24b6-206">The metadata that is returned by the DB_ID() and DB_NAME() functions is visible to all users.</span></span>  
  
 <span data-ttu-id="e24b6-207">次の表に、 **public** ロールで表示できるカタログ ビューを示します。</span><span class="sxs-lookup"><span data-stu-id="e24b6-207">The following table lists the catalog views that are visible to the **public** role.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e24b6-208">**sys.partition_functions**</span><span class="sxs-lookup"><span data-stu-id="e24b6-208">**sys.partition_functions**</span></span>|<span data-ttu-id="e24b6-209">**sys.partition_range_values**</span><span class="sxs-lookup"><span data-stu-id="e24b6-209">**sys.partition_range_values**</span></span>|  
|<span data-ttu-id="e24b6-210">**sys.partition_schemes**</span><span class="sxs-lookup"><span data-stu-id="e24b6-210">**sys.partition_schemes**</span></span>|<span data-ttu-id="e24b6-211">**sys.data_spaces**</span><span class="sxs-lookup"><span data-stu-id="e24b6-211">**sys.data_spaces**</span></span>|  
|<span data-ttu-id="e24b6-212">**sys.filegroups**</span><span class="sxs-lookup"><span data-stu-id="e24b6-212">**sys.filegroups**</span></span>|<span data-ttu-id="e24b6-213">**sys.destination_data_spaces**</span><span class="sxs-lookup"><span data-stu-id="e24b6-213">**sys.destination_data_spaces**</span></span>|  
|<span data-ttu-id="e24b6-214">**sys.database_files**</span><span class="sxs-lookup"><span data-stu-id="e24b6-214">**sys.database_files**</span></span>|<span data-ttu-id="e24b6-215">**sys.allocation_units**</span><span class="sxs-lookup"><span data-stu-id="e24b6-215">**sys.allocation_units**</span></span>|  
|<span data-ttu-id="e24b6-216">**sys.partitions**</span><span class="sxs-lookup"><span data-stu-id="e24b6-216">**sys.partitions**</span></span>|<span data-ttu-id="e24b6-217">**sys.messages**</span><span class="sxs-lookup"><span data-stu-id="e24b6-217">**sys.messages**</span></span>|  
|<span data-ttu-id="e24b6-218">**sys.schemas**</span><span class="sxs-lookup"><span data-stu-id="e24b6-218">**sys.schemas**</span></span>|<span data-ttu-id="e24b6-219">**sys.configurations**</span><span class="sxs-lookup"><span data-stu-id="e24b6-219">**sys.configurations**</span></span>|  
|<span data-ttu-id="e24b6-220">**sys.sql_dependencies**</span><span class="sxs-lookup"><span data-stu-id="e24b6-220">**sys.sql_dependencies**</span></span>|<span data-ttu-id="e24b6-221">**sys.type_assembly_usages**</span><span class="sxs-lookup"><span data-stu-id="e24b6-221">**sys.type_assembly_usages**</span></span>|  
|<span data-ttu-id="e24b6-222">**sys.parameter_type_usages**</span><span class="sxs-lookup"><span data-stu-id="e24b6-222">**sys.parameter_type_usages**</span></span>|<span data-ttu-id="e24b6-223">**sys.column_type_usages**</span><span class="sxs-lookup"><span data-stu-id="e24b6-223">**sys.column_type_usages**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e24b6-224">参照</span><span class="sxs-lookup"><span data-stu-id="e24b6-224">See Also</span></span>  
 <span data-ttu-id="e24b6-225">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e24b6-225">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="e24b6-226">[DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e24b6-226">[DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) </span></span>  
 <span data-ttu-id="e24b6-227">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e24b6-227">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 <span data-ttu-id="e24b6-228">[EXECUTE AS 句 &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e24b6-228">[EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql) </span></span>  
 <span data-ttu-id="e24b6-229">[カタログ ビュー &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e24b6-229">[Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span></span>  
 [<span data-ttu-id="e24b6-230">互換性ビュー &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e24b6-230">Compatibility Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql)  
  
  
