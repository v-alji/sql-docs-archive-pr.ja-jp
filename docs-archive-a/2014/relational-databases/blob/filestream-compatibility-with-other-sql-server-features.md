---
title: FILESTREAM と SQL Server のその他の機能との互換性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], other SQL Server features and
- FILESTREAM [SQL Server], limitations
ms.assetid: d2c145dc-d49a-4f5b-91e6-89a2b0adb4f3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53bb99ea094261fd96f2a821dfaa5203e9796d8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631098"
---
# <a name="filestream-compatibility-with-other-sql-server-features"></a><span data-ttu-id="47f68-102">FILESTREAM と SQL Server のその他の機能との互換性</span><span class="sxs-lookup"><span data-stu-id="47f68-102">FILESTREAM Compatibility with Other SQL Server Features</span></span>
  <span data-ttu-id="47f68-103">ここでは、FILESTREAM データがファイル システムに存在することに関連して、FILESTREAM を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の次の機能と共に使用する際の注意事項、ガイドライン、および制限事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="47f68-103">Because FILESTREAM data is in the file system, this topic provides some considerations, guidelines, and limitations for using FILESTREAM with the following features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="47f68-104">SQL Server Integration Services (SSIS)</span><span class="sxs-lookup"><span data-stu-id="47f68-104">SQL Server Integration Services (SSIS)</span></span>](#ssis)  
  
-   [<span data-ttu-id="47f68-105">分散クエリおよびリンク サーバー</span><span class="sxs-lookup"><span data-stu-id="47f68-105">Distributed Queries and Linked Servers</span></span>](#distqueries)  
  
-   [<span data-ttu-id="47f68-106">暗号化</span><span class="sxs-lookup"><span data-stu-id="47f68-106">Encryption</span></span>](#encryption)  
  
-   [<span data-ttu-id="47f68-107">データベース スナップショット</span><span class="sxs-lookup"><span data-stu-id="47f68-107">Database Snapshots</span></span>](#DatabaseSnapshot)  
  
-   [<span data-ttu-id="47f68-108">レプリケーション</span><span class="sxs-lookup"><span data-stu-id="47f68-108">Replication</span></span>](#Replication)  
  
-   [<span data-ttu-id="47f68-109">ログ配布</span><span class="sxs-lookup"><span data-stu-id="47f68-109">Log Shipping</span></span>](#LogShipping)  
  
-   [<span data-ttu-id="47f68-110">データベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="47f68-110">Database Mirroring</span></span>](#DatabaseMirroring)  
  
-   [<span data-ttu-id="47f68-111">フルテキスト インデックス作成</span><span class="sxs-lookup"><span data-stu-id="47f68-111">Full-Text Indexing</span></span>](#FullText)  
  
-   [<span data-ttu-id="47f68-112">フェールオーバー クラスタリング</span><span class="sxs-lookup"><span data-stu-id="47f68-112">Failover Clustering</span></span>](#FailoverClustering)  
  
-   [<span data-ttu-id="47f68-113">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="47f68-113">SQL Server Express</span></span>](#SQLServerExpress)  
  
-   [<span data-ttu-id="47f68-114">包含データベース</span><span class="sxs-lookup"><span data-stu-id="47f68-114">Contained Databases</span></span>](#contained)  
  
##  <a name="sql-server-integration-services-ssis"></a><a name="ssis"></a> <span data-ttu-id="47f68-115">SQL Server Integration Services (SSIS)</span><span class="sxs-lookup"><span data-stu-id="47f68-115">SQL Server Integration Services (SSIS)</span></span>  
 <span data-ttu-id="47f68-116">SQL Server Integration Services (SSIS) では、DT_IMAGE SSIS データ型を使用して、他の BLOB データと同様にデータ フローの FILESTREAM データを処理します。</span><span class="sxs-lookup"><span data-stu-id="47f68-116">SQL Server Integration Services (SSIS) handles FILESTREAM data in the data flow like any other BLOB data by using the DT_IMAGE SSIS data type.</span></span>  
  
 <span data-ttu-id="47f68-117">列インポート変換を使用すると、ファイル システムから FILESTREAM 列にファイルを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="47f68-117">You can use the Import Column transformation to load files from the file system into a FILESTREAM column.</span></span> <span data-ttu-id="47f68-118">また、列エクスポート変換を使用すると、FILESTREAM 列からファイル システム内の別の場所にファイルを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="47f68-118">You can also use the Export Column transformation to extract files from a FILESTREAM column to another location in the file system.</span></span>  
  
##  <a name="distributed-queries-and-linked-servers"></a><a name="distqueries"></a> <span data-ttu-id="47f68-119">分散クエリおよびリンク サーバー</span><span class="sxs-lookup"><span data-stu-id="47f68-119">Distributed Queries and Linked Servers</span></span>  
 <span data-ttu-id="47f68-120">FILESTREAM データは、データとして扱うことによって、分散クエリおよびリンクサーバーを使用して操作でき `varbinary(max)` ます。</span><span class="sxs-lookup"><span data-stu-id="47f68-120">You can work with FILESTREAM data through distributed queries and linked servers by treating it as `varbinary(max)` data.</span></span> <span data-ttu-id="47f68-121">4 部構成の名前を使用する分散クエリでは、FILESTREAM の **PathName()** 関数を使用することはできません。その名前がローカル サーバーを指し示す場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="47f68-121">You cannot use the FILESTREAM **PathName()** function in distributed queries that use a four-part name, even when the name refers to the local server.</span></span> <span data-ttu-id="47f68-122">ただし、 **OPENQUERY()** を使用するパススルー クエリの内側のクエリでは **PathName()** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="47f68-122">However you can use **PathName()** in the inner query of a pass-through query that uses **OPENQUERY()**.</span></span>  
  
##  <a name="encryption"></a><a name="encryption"></a> <span data-ttu-id="47f68-123">暗号化</span><span class="sxs-lookup"><span data-stu-id="47f68-123">Encryption</span></span>  
 <span data-ttu-id="47f68-124">FILESTREAM データは、透過的なデータ暗号化が有効になっている場合でも暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="47f68-124">FILESTREAM data is not encrypted even when transparent data encryption is enabled.</span></span>  
  
##  <a name="database-snapshots"></a><a name="DatabaseSnapshot"></a> <span data-ttu-id="47f68-125">データベース スナップショット</span><span class="sxs-lookup"><span data-stu-id="47f68-125">Database Snapshots</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="47f68-126">では、FILESTREAM ファイル グループの [データベース スナップショット](../databases/database-snapshots-sql-server.md) をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="47f68-126">does not support [database snapshots](../databases/database-snapshots-sql-server.md) for FILESTREAM filegroups.</span></span> <span data-ttu-id="47f68-127">CREATE DATABASE ON 句に FILESTREAM ファイル グループが含まれていると、ステートメントが失敗してエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="47f68-127">If a FILESTREAM filegroup is included in a CREATE DATABASE ON clause, the statement will fail and an error will be raised.</span></span>  
  
 <span data-ttu-id="47f68-128">FILESTREAM を使用している場合は、標準の (FILESTREAM ファイル グループではない) ファイル グループのデータベース スナップショットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="47f68-128">When you are using FILESTREAM, you can create database snapshots of standard (non-FILESTREAM) filegroups.</span></span> <span data-ttu-id="47f68-129">FILESTREAM ファイル グループは、それらのデータベース スナップショットに対してオフラインとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="47f68-129">The FILESTREAM filegroups are marked as offline for those database snapshots.</span></span>  
  
 <span data-ttu-id="47f68-130">データベース スナップショットの FILESTREAM テーブルに対して実行する SELECT ステートメントには、FILESTREAM 列を含めないようにする必要があります。FILESTREAM 列が含まれていると、次のエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="47f68-130">A SELECT statement that is executed on a FILESTREAM table in a database snapshot must not include a FILESTREAM column; otherwise, the following error message will be returned:</span></span>  
  
 `Could not continue scan with NOLOCK due to data movement.`  
  
##  <a name="replication"></a><a name="Replication"></a> <span data-ttu-id="47f68-131">Replication</span><span class="sxs-lookup"><span data-stu-id="47f68-131">Replication</span></span>  
 <span data-ttu-id="47f68-132">パブリッシャーで FILESTREAM 属性が有効になっている `varbinary(max)` 列は、FILESTREAM 属性を含めてサブスクライバーにレプリケートすることも、含めずにレプリケートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="47f68-132">A `varbinary(max)` column that has the FILESTREAM attribute enabled at the Publisher can be replicated to a Subscriber with or without the FILESTREAM attribute.</span></span> <span data-ttu-id="47f68-133">列をレプリケートする方法を指定するには、 **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスを使用するか、[sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) または [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) の @schema_option パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="47f68-133">To specify the way in which the column is replicated, use the **Article Properties - \<Article>** dialog box or the @schema_option parameter of [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) or [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="47f68-134">FILESTREAM 属性を持たない `varbinary(max)` 列にレプリケートされるデータは、このデータ型の制限 (2 GB) を超えないようにする必要があります。この制限を超えると実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="47f68-134">Data that is replicated to a `varbinary(max)` column that does not have the FILESTREAM attribute must not exceed the 2-GB limit for that data type; otherwise, a run-time error is generated.</span></span> <span data-ttu-id="47f68-135">指定したスキーマオプションに関係なく、サブスクライバーにデータをレプリケートしている場合を除き、FILESTREAM 属性をレプリケートすることをお勧めし [!INCLUDE[ssVersion2005](../../includes/ssversion2000-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="47f68-135">We recommend that you replicate the FILESTREAM attribute, unless you are replicating data to [!INCLUDE[ssVersion2005](../../includes/ssversion2000-md.md)] Subscribers is not supported, regardless of the schema option that is specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47f68-136">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] から [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] サブスクライバーにレプリケートできるデータ値の大きさは、最大 256 MB に制限されています。</span><span class="sxs-lookup"><span data-stu-id="47f68-136">Replicating large data values from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Subscribers is limited to a maximum of 256 MB data values.</span></span> <span data-ttu-id="47f68-137">詳細については、「 [最大容量仕様](https://go.microsoft.com/fwlink/?LinkId=103810)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47f68-137">For more information, see [Maximum Capacity Specifications](https://go.microsoft.com/fwlink/?LinkId=103810).</span></span>  
  
### <a name="considerations-for-transactional-replication"></a><span data-ttu-id="47f68-138">トランザクション レプリケーションに関する注意点</span><span class="sxs-lookup"><span data-stu-id="47f68-138">Considerations for Transactional Replication</span></span>  
 <span data-ttu-id="47f68-139">トランザクション レプリケーション用にパブリッシュされるテーブルで FILESTREAM 列を使用する場合は、次のことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="47f68-139">If you use FILESTREAM columns in tables that are published for transactional replication, note the following considerations:</span></span>  
  
-   <span data-ttu-id="47f68-140">FILESTREAM 属性を持つ列を含むテーブルがある場合は、[sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) の @sync_method プロパティに対して値 *database snapshot* および *database snapshot character* を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="47f68-140">If any tables include columns that have the FILESTREAM attribute, you cannot use values of *database snapshot* or *database snapshot character* for the @sync_method property of [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span>  
  
-   <span data-ttu-id="47f68-141">max text repl size オプションは、レプリケーション用にパブリッシュされる列に挿入できるデータの最大サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="47f68-141">The max text repl size option specifies the maximum amount of data that can be inserted into a column that is published for replication.</span></span> <span data-ttu-id="47f68-142">このオプションを使用すると、レプリケートされる FILESTREAM データのサイズを制御できます。</span><span class="sxs-lookup"><span data-stu-id="47f68-142">This option can be used to control the size of FILESTREAM data that is replicated.</span></span>  
  
-   <span data-ttu-id="47f68-143">FILESTREAM 属性をレプリケートするスキーマ オプションを指定しても、FILESTREAM で必要な `uniqueidentifier` 列をフィルターで除外したり、この列の UNIQUE 制約をレプリケートしないように指定したりすると、FILESTREAM 属性はレプリケートされません。</span><span class="sxs-lookup"><span data-stu-id="47f68-143">If you specify the schema option to replicate the FILESTREAM attribute, but you filter out the `uniqueidentifier` column that FILESTREAM requires or you specify not to replicate the UNIQUE constraint for the column, replication does not replicate the FILESTREAM attribute.</span></span> <span data-ttu-id="47f68-144">その列は、`varbinary(max)` 列としてのみレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="47f68-144">The column is replicated only as a `varbinary(max)` column.</span></span>  
  
### <a name="considerations-for-merge-replication"></a><span data-ttu-id="47f68-145">マージ レプリケーションに関する注意点</span><span class="sxs-lookup"><span data-stu-id="47f68-145">Considerations for Merge Replication</span></span>  
 <span data-ttu-id="47f68-146">マージ レプリケーション用にパブリッシュされるテーブルで FILESTREAM 列を使用する場合は、次のことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="47f68-146">If you use FILESTREAM columns in tables that are published for merge replication, note the following considerations:</span></span>  
  
-   <span data-ttu-id="47f68-147">マージ レプリケーションと FILESTREAM では、テーブルの各行を識別するために `uniqueidentifier` データ型の列が必要になります。</span><span class="sxs-lookup"><span data-stu-id="47f68-147">Both merge replication and FILESTREAM require a column of data type `uniqueidentifier` to identify each row in a table.</span></span> <span data-ttu-id="47f68-148">マージ レプリケーションでは、この列がテーブルに含まれていなければ自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="47f68-148">Merge replication automatically adds a column if the table does not have one.</span></span> <span data-ttu-id="47f68-149">またその列で、ROWGUIDCOL プロパティと、NEWID() または NEWSEQUENTIALID() の既定値が設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="47f68-149">Merge replication requires that the column have the ROWGUIDCOL property set and a default of NEWID() or NEWSEQUENTIALID().</span></span> <span data-ttu-id="47f68-150">FILESTREAM ではさらに、この列に対して UNIQUE 制約が定義されている必要もあります。</span><span class="sxs-lookup"><span data-stu-id="47f68-150">In addition to these requirements, FILESTREAM requires that a UNIQUE constraint be defined for the column.</span></span> <span data-ttu-id="47f68-151">これらの要件により、次のような結果になります。</span><span class="sxs-lookup"><span data-stu-id="47f68-151">These requirements have the following consequences:</span></span>  
  
    -   <span data-ttu-id="47f68-152">既にマージ レプリケーション用にパブリッシュされているテーブルに FILESTREAM 列を追加する場合は、`uniqueidentifier` 列に UNIQUE 制約があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="47f68-152">If you add a FILESTREAM column to a table that is already published for merge replication, make sure that the `uniqueidentifier` column has a UNIQUE constraint.</span></span> <span data-ttu-id="47f68-153">UNIQUE 制約がない場合は、パブリケーション データベースのテーブルに名前付き制約を追加します。</span><span class="sxs-lookup"><span data-stu-id="47f68-153">If it does not have a UNIQUE constraint, add a named constraint to the table in the publication database.</span></span> <span data-ttu-id="47f68-154">既定では、マージ レプリケーションによってこのスキーマ変更がパブリッシュされ、各サブスクリプション データベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="47f68-154">By default, merge replication will publish this schema change, and it will be applied to each subscription database.</span></span>  
  
         <span data-ttu-id="47f68-155">上の説明に従って手動で UNIQUE 制約を追加した場合は、マージ レプリケーションを削除する際に先に UNIQUE 制約を削除する必要があります。そうしないと、レプリケーションの削除に失敗します。</span><span class="sxs-lookup"><span data-stu-id="47f68-155">If you add a UNIQUE constraint manually as described and you want to remove merge replication, you must first remove the UNIQUE constraint; otherwise, replication removal will fail.</span></span>  
  
    -   <span data-ttu-id="47f68-156">NEWID() より NEWSEQUENTIALID() の方がパフォーマンスが高いため、マージ レプリケーションでは既定で NEWSEQUENTIALID() が使用されます。</span><span class="sxs-lookup"><span data-stu-id="47f68-156">By default, merge replication uses NEWSEQUENTIALID() because it can provide better performance than NEWID().</span></span> <span data-ttu-id="47f68-157">マージ レプリケーション用にパブリッシュされるテーブルに `uniqueidentifier` 列を追加する場合は、NEWSEQUENTIALID() を既定値として指定してください。</span><span class="sxs-lookup"><span data-stu-id="47f68-157">If you add a `uniqueidentifier` column to a table that will be published for merge replication, specify NEWSEQUENTIALID() as the default.</span></span>  
  
-   <span data-ttu-id="47f68-158">マージ レプリケーションには、ラージ オブジェクト型のレプリケーションを最適化する機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="47f68-158">Merge replication includes an optimization for replicating large object types.</span></span> <span data-ttu-id="47f68-159">この機能は、[sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) の @stream_blob_columns パラメーターによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="47f68-159">This optimization is controlled by the @stream_blob_columns parameter of [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="47f68-160">FILESTREAM 属性をレプリケートするスキーマ オプションを設定すると、@stream_blob_columns パラメーターの値が `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="47f68-160">If you set the schema option to replicate the FILESTREAM attribute, the @stream_blob_columns parameter value is set to `true`.</span></span> <span data-ttu-id="47f68-161">この値をオーバーライドするには、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="47f68-161">This optimization can be overridden by using [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="47f68-162">このストアド プロシージャを使用すると、@stream_blob_columns を `false` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="47f68-162">This stored procedure enables you to set @stream_blob_columns to `false`.</span></span> <span data-ttu-id="47f68-163">既にマージ レプリケーション用にパブリッシュされているテーブルに FILESTREAM 列を追加する場合は、sp_changemergearticle を使用してこのオプションを `true` に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="47f68-163">If you add a FILESTREAM column to a table that is already published for merge replication, we recommend that you set the option to `true` by using sp_changemergearticle.</span></span>  
  
-   <span data-ttu-id="47f68-164">アーティクルが作成された後に FILESTREAM のスキーマ オプションを有効にすると、FILESTREAM 列のデータが 2 GB を超えていて、レプリケーションの間に競合が発生した場合に、レプリケーションが失敗します。</span><span class="sxs-lookup"><span data-stu-id="47f68-164">Enabling the schema option for FILESTREAM after an article is created can cause replication to fail if the data in a FILESTREAM column exceeds 2 GB and there is a conflict during replication.</span></span> <span data-ttu-id="47f68-165">この状況が発生することが予想される場合は、いったんテーブル アーティクルを削除して、適切な FILESTREAM スキーマ オプションを有効にした状態で再作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="47f68-165">If you expect this situation to arise, it is recommended that you drop and re-create the table article with the appropriate FILESTREAM schema option enabled at creation time.</span></span>  
  
-   <span data-ttu-id="47f68-166">マージ レプリケーションでは、 [Web 同期](../replication/merge/merge-replication.md)を使用して FILESTREAM データを HTTPS 接続経由で同期させることができます。</span><span class="sxs-lookup"><span data-stu-id="47f68-166">Merge replication can synchronize FILESTREAM data over an HTTPS connection by using [Web Synchronization](../replication/merge/merge-replication.md).</span></span> <span data-ttu-id="47f68-167">その際には、データが Web 同期の制限 (50 MB) に収まっている必要があります。データがこの制限を超えていると、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="47f68-167">This data cannot exceed the 50 MB limit for Web Synchronization; otherwise, a run-time error is generated.</span></span>  
  
##  <a name="log-shipping"></a><a name="LogShipping"></a> <span data-ttu-id="47f68-168">ログ配布</span><span class="sxs-lookup"><span data-stu-id="47f68-168">Log Shipping</span></span>  
 <span data-ttu-id="47f68-169">[ログ配布](../../database-engine/log-shipping/about-log-shipping-sql-server.md) は FILESTREAM をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="47f68-169">[Log shipping](../../database-engine/log-shipping/about-log-shipping-sql-server.md) supports FILESTREAM.</span></span> <span data-ttu-id="47f68-170">プライマリ サーバーとセカンダリ サーバーの両方で [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降のバージョンが実行されていて、FILESTREAM が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="47f68-170">Both the primary and secondary servers must be running [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], or a later version, and have FILESTREAM enabled.</span></span>  
  
##  <a name="database-mirroring"></a><a name="DatabaseMirroring"></a> <span data-ttu-id="47f68-171">データベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="47f68-171">Database Mirroring</span></span>  
 <span data-ttu-id="47f68-172">データベース ミラーリングは FILESTREAM をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="47f68-172">Database mirroring does not support FILESTREAM.</span></span> <span data-ttu-id="47f68-173">プリンシパル サーバー上に FILESTREAM ファイル グループを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="47f68-173">A FILESTREAM filegroup cannot be created on the principal server.</span></span> <span data-ttu-id="47f68-174">FILESTREAM ファイル グループを含むデータベースに対してデータベース ミラーリングを構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="47f68-174">Database mirroring cannot be configured for a database that contains FILESTREAM filegroups.</span></span>  
  
##  <a name="full-text-indexing"></a><a name="FullText"></a> <span data-ttu-id="47f68-175">フルテキスト インデックス作成</span><span class="sxs-lookup"><span data-stu-id="47f68-175">Full-Text Indexing</span></span>  
 <span data-ttu-id="47f68-176">[フルテキストインデックス作成](../indexes/indexes.md)は、列と同じように FILESTREAM 列で動作し `varbinary(max)` ます。</span><span class="sxs-lookup"><span data-stu-id="47f68-176">[Full-text indexing](../indexes/indexes.md) works with a FILESTREAM column in the same way that it does with a `varbinary(max)` column.</span></span> <span data-ttu-id="47f68-177">FILESTREAM テーブルに、各 FILESTREAM BLOB のファイル名拡張子を含む列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="47f68-177">The FILESTREAM table must have a column that contains the file name extension for each FILESTREAM BLOB.</span></span> <span data-ttu-id="47f68-178">詳細については、「[フルテキスト検索でのクエリ](../search/query-with-full-text-search.md)」、「[検索用フィルターの構成と管理](../search/configure-and-manage-filters-for-search.md)」、および「[sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47f68-178">For more information, see [Query with Full-Text Search](../search/query-with-full-text-search.md), [Configure and Manage Filters for Search](../search/configure-and-manage-filters-for-search.md), and [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql).</span></span>  
  
 <span data-ttu-id="47f68-179">フルテキスト エンジンは、FILESTREAM BLOB の内容のインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="47f68-179">The full-text engine indexes the contents of the FILESTREAM BLOBs.</span></span> <span data-ttu-id="47f68-180">イメージなど、インデックスを作成しても役に立たないファイルもあります。</span><span class="sxs-lookup"><span data-stu-id="47f68-180">Indexing files such as images might not be useful.</span></span> <span data-ttu-id="47f68-181">FILESTREAM BLOB が更新されると、インデックスが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="47f68-181">When a FILESTREAM BLOB is updated it is reindexed.</span></span>  
  
##  <a name="failover-clustering"></a><a name="FailoverClustering"></a> <span data-ttu-id="47f68-182">フェールオーバー クラスタリング</span><span class="sxs-lookup"><span data-stu-id="47f68-182">Failover Clustering</span></span>  
 <span data-ttu-id="47f68-183">フェールオーバー クラスタリングでは、FILESTREAM ファイル グループが共有ディスク上に配置されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="47f68-183">For failover clustering, FILESTREAM filegroups must be put on a shared disk.</span></span> <span data-ttu-id="47f68-184">また、FILESTREAM インスタンスをホストするクラスターの各ノードで FILESTREAM が有効になっている必要もあります。</span><span class="sxs-lookup"><span data-stu-id="47f68-184">FILESTREAM must be enabled on each node in the cluster that will host the FILESTREAM instance.</span></span> <span data-ttu-id="47f68-185">詳細については、「 [フェールオーバー クラスターでの FILESTREAM の設定](set-up-filestream-on-a-failover-cluster.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47f68-185">For more information, see [Set Up FILESTREAM on a Failover Cluster](set-up-filestream-on-a-failover-cluster.md).</span></span>  
  
##  <a name="sql-server-express"></a><a name="SQLServerExpress"></a> <span data-ttu-id="47f68-186">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="47f68-186">SQL Server Express</span></span>  
 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] <span data-ttu-id="47f68-187">は FILESTREAM をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="47f68-187">supports FILESTREAM.</span></span> <span data-ttu-id="47f68-188">FILESTREAM データ コンテナーは 10 GB のデータベース サイズの制限に含まれません。</span><span class="sxs-lookup"><span data-stu-id="47f68-188">The 10-GB database size limit does not include the FILESTREAM data container.</span></span>  
  
##  <a name="contained-databases"></a><a name="contained"></a> <span data-ttu-id="47f68-189">包含データベース</span><span class="sxs-lookup"><span data-stu-id="47f68-189">Contained Databases</span></span>  
 <span data-ttu-id="47f68-190">FILESTREAM 機能では、データベースの外部での構成が一部必要となります。</span><span class="sxs-lookup"><span data-stu-id="47f68-190">The FILESTREAM feature requires some configuration outside of the database.</span></span> <span data-ttu-id="47f68-191">そのため、FILESTREAM または FileTable を使用するデータベースは完全包含ではありません。</span><span class="sxs-lookup"><span data-stu-id="47f68-191">Therefore a database that uses FILESTREAM or FileTable is not fully contained.</span></span>  
  
 <span data-ttu-id="47f68-192">包含データベースの特定の機能 (包含ユーザーなど) を使用する場合は、データベースの包含を PARTIAL に設定します。</span><span class="sxs-lookup"><span data-stu-id="47f68-192">You can set database containment to PARTIAL if you want to use certain features of contained databases, such as contained users.</span></span> <span data-ttu-id="47f68-193">ただし、この場合、一部のデータベース設定はデータベースに含まれないため、データベースを移動するときに自動的には移動されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="47f68-193">In this case, however, you must be aware that some of the database settings are not contained in the database and are not automatically moved when the database moves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f68-194">参照</span><span class="sxs-lookup"><span data-stu-id="47f68-194">See Also</span></span>  
 [<span data-ttu-id="47f68-195">バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="47f68-195">Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;</span></span>](binary-large-object-blob-data-sql-server.md)  
  
  