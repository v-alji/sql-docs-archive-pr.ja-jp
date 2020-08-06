---
title: データベース スナップショットの作成 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], creating
ms.assetid: 187fbba3-c555-4030-9bdf-0f01994c5230
author: stevestein
ms.author: sstein
ms.openlocfilehash: bae68c2d507e1dd3809e76a9d842b765d72234e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742225"
---
# <a name="create-a-database-snapshot-transact-sql"></a><span data-ttu-id="1a9a2-102">データベース スナップショットの作成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a9a2-102">Create a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="1a9a2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース スナップショットを作成する唯一の方法は、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用することです。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-103">The only way to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshot is to use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="1a9a2-104">では、データベース スナップショットの作成はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-104">does not support the creation of database snapshots.</span></span>  
  
-   <span data-ttu-id="1a9a2-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1a9a2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1a9a2-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="1a9a2-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="1a9a2-107">Security</span><span class="sxs-lookup"><span data-stu-id="1a9a2-107">Security</span></span>](#Security)  
  
     [<span data-ttu-id="1a9a2-108">ベスト プラクティス:データベース スナップショットの名前付け</span><span class="sxs-lookup"><span data-stu-id="1a9a2-108">Best Practice: Naming Database Snapshots</span></span>](#Naming)  
  
-   <span data-ttu-id="1a9a2-109">[Transact-sql](#TsqlProcedure)を**使用してデータベーススナップショットを作成するに**は  </span><span class="sxs-lookup"><span data-stu-id="1a9a2-109">**To create a database snapshot, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1a9a2-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="1a9a2-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="1a9a2-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="1a9a2-111">Prerequisites</span></span>  
 <span data-ttu-id="1a9a2-112">任意の復旧モデルを使用できるソース データベースは、次の前提条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-112">The source database, which can use any recovery model, must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="1a9a2-113">サーバー インスタンスで、データベース スナップショットをサポートする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エディションが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-113">The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports database snapshot.</span></span> <span data-ttu-id="1a9a2-114">でのデータベーススナップショットのサポートの詳細につい [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-114">For information about support for database snapshots in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="1a9a2-115">ソース データベースは、データベース ミラーリング セッション内のミラー データベースである場合を除き、オンラインである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-115">The source database must be online, unless the database is a mirror database within a database mirroring session.</span></span>  
  
-   <span data-ttu-id="1a9a2-116">ミラー データベースにデータベース スナップショットを作成するには、データベースは "同期済み" の[ミラーリング状態](../../database-engine/database-mirroring/mirroring-states-sql-server.md)になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-116">To create a database snapshot on a mirror database, the database must be in the synchronized[mirroring state](../../database-engine/database-mirroring/mirroring-states-sql-server.md).</span></span>  
  
-   <span data-ttu-id="1a9a2-117">ソース データベースは、スケーラブルな共有データベースとして構成できません。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-117">The source database cannot be configured as a scalable shared database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1a9a2-118">その他の重要な考慮事項については、「 [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md)を使用することです。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-118">For information about other significant considerations, see [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1a9a2-119">推奨事項</span><span class="sxs-lookup"><span data-stu-id="1a9a2-119">Recommendations</span></span>  
 <span data-ttu-id="1a9a2-120">このセクションでは、次のベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-120">This section discusses the following best practices:</span></span>  
  
-   [<span data-ttu-id="1a9a2-121">ベスト プラクティス:データベース スナップショットの名前付け</span><span class="sxs-lookup"><span data-stu-id="1a9a2-121">Best Practice: Naming Database Snapshots</span></span>](#Naming)  
  
-   [<span data-ttu-id="1a9a2-122">ベスト プラクティス:データベース スナップショット数の制限</span><span class="sxs-lookup"><span data-stu-id="1a9a2-122">Best Practice: Limiting the Number of Database Snapshots</span></span>](#Limiting_Number)  
  
-   [<span data-ttu-id="1a9a2-123">ベスト プラクティス:データベース スナップショットへのクライアント接続</span><span class="sxs-lookup"><span data-stu-id="1a9a2-123">Best Practice: Client Connections to a Database Snapshot</span></span>](#Client_Connections)  
  
####  <a name="best-practice-naming-database-snapshots"></a><a name="Naming"></a> <span data-ttu-id="1a9a2-124">ベスト プラクティス:データベース スナップショットの名前付け</span><span class="sxs-lookup"><span data-stu-id="1a9a2-124">Best Practice: Naming Database Snapshots</span></span>  
 <span data-ttu-id="1a9a2-125">スナップショットを作成する前に、名前付けの方法を検討することが重要です。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-125">Before creating snapshots, it is important to consider how to name them.</span></span> <span data-ttu-id="1a9a2-126">各データベース スナップショットでは、一意のデータベース名が必要になります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-126">Each database snapshot requires a unique database name.</span></span> <span data-ttu-id="1a9a2-127">管理を容易にするために、次のようなデータベースを識別する情報を、スナップショット名に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-127">For administrative ease, the name of a snapshot can incorporate information that identifies the database, such as:</span></span>  
  
-   <span data-ttu-id="1a9a2-128">ソース データベースの名前。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-128">The name of the source database.</span></span>  
  
-   <span data-ttu-id="1a9a2-129">新しい名前がスナップショット用であるという指示</span><span class="sxs-lookup"><span data-stu-id="1a9a2-129">An indication that the new name is for a snapshot.</span></span>  
  
-   <span data-ttu-id="1a9a2-130">任意のデータベース上のシーケンシャル スナップショットを区別するための、スナップショットの作成日や作成時刻、シーケンス番号、日時などの他のいくつかの情報</span><span class="sxs-lookup"><span data-stu-id="1a9a2-130">The creation date and time of the snapshot, a sequence number, or some other information, such as time of day, to distinguish sequential snapshots on a given database.</span></span>  
  
 <span data-ttu-id="1a9a2-131">たとえば、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの一連のスナップショットについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-131">For example, consider a series of snapshots for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="1a9a2-132">24 時間形式のクロックに基づいて、午前 6 時から午後 6 時までの間に、</span><span class="sxs-lookup"><span data-stu-id="1a9a2-132">Three daily snapshots are created at 6-hour intervals between 6 A.M.</span></span> <span data-ttu-id="1a9a2-133">6 時間間隔で毎日 3 つのスナップショットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-133">and 6 P.M., based on a 24-hour clock.</span></span> <span data-ttu-id="1a9a2-134">毎日の各スナップショットは、24 時間保持された後削除され、同じ名前の新しいスナップショットに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-134">Each daily snapshot is kept for 24 hours before being dropped and replaced by a new snapshot of the same name.</span></span> <span data-ttu-id="1a9a2-135">各スナップショット名は、次のように時刻を示しますが、日付は示しません。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-135">Note that each snapshot name indicates the hour, but not the day:</span></span>  
  
```  
AdventureWorks_snapshot_0600  
AdventureWorks_snapshot_1200  
AdventureWorks_snapshot_1800  
```  
  
 <span data-ttu-id="1a9a2-136">しかし、毎日のスナップショットの作成時刻が日によって異なる場合、あまり明確でない名前付け規則が適している場合もあります。たとえば次のような名前にします。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-136">Alternatively, if the creation time of these daily snapshots varies from day to day, a less precise naming convention might be preferable, for example:</span></span>  
  
```  
AdventureWorks_snapshot_morning  
AdventureWorks_snapshot_noon  
AdventureWorks_snapshot_evening  
```  
  
####  <a name="best-practice-limiting-the-number-of-database-snapshots"></a><a name="Limiting_Number"></a> <span data-ttu-id="1a9a2-137">ベスト プラクティス:データベース スナップショット数の制限</span><span class="sxs-lookup"><span data-stu-id="1a9a2-137">Best Practice: Limiting the Number of Database Snapshots</span></span>  
 <span data-ttu-id="1a9a2-138">一連のスナップショットを長期にわたって作成することで、ソース データベースのシーケンシャルなスナップショットがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-138">Creating a series of snapshots over time captures sequential snapshots of the source database.</span></span> <span data-ttu-id="1a9a2-139">各スナップショットは、明示的に削除されるまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-139">Each snapshot persists until it is explicitly dropped.</span></span> <span data-ttu-id="1a9a2-140">元のページが更新されるにつれて、各スナップショットが継続的に拡張されるので、新しいスナップショットの作成後に古いスナップショットを削除するとディスク領域を節約できます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-140">Because each snapshot will continue to grow as original pages are updated, you may want to conserve disk space by deleting an older snapshot after creating a new snapshot.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a9a2-141">データベース スナップショットに戻す場合は、そのデータベースから他のすべてのスナップショットを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-141">If you want to revert to a database snapshot, you need to delete any other snapshots from that database.</span></span>  
  
####  <a name="best-practice-client-connections-to-a-database-snapshot"></a><a name="Client_Connections"></a> <span data-ttu-id="1a9a2-142">ベスト プラクティス:データベース スナップショットへのクライアント接続</span><span class="sxs-lookup"><span data-stu-id="1a9a2-142">Best Practice: Client Connections to a Database Snapshot</span></span>  
 <span data-ttu-id="1a9a2-143">データベース スナップショットを使用するには、クライアントはそのスナップショットを見つける場所を認識している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-143">To use a database snapshot, clients need to know where to find it.</span></span> <span data-ttu-id="1a9a2-144">ユーザーは、あるデータベース スナップショットが作成または削除されている間でも、他のデータベース スナップショットから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-144">Users can read from one database snapshot while another is being created or deleted.</span></span> <span data-ttu-id="1a9a2-145">ただし、既存のスナップショットを新しいスナップショットに置き換えるときに、クライアントを新しいスナップショットにリダイレクトする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-145">However, when you substitute a new snapshot for an existing one, you need to redirect clients to the new snapshot.</span></span> <span data-ttu-id="1a9a2-146">ユーザーは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、データベース スナップショットに手動で接続できます。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-146">Users can manually connect to a database snapshot by means of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1a9a2-147">ただし、実稼働環境をサポートするには、ユーザーが意識しないうちにレポート作成クライアントをデータベースの最新のデータベース スナップショットにリダイレクトするような、プログラム ソリューションを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-147">However, to support a production environment, you should create a programmatic solution that transparently directs report-writing clients to the latest database snapshot of the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1a9a2-148">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1a9a2-148">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1a9a2-149">Permissions</span><span class="sxs-lookup"><span data-stu-id="1a9a2-149">Permissions</span></span>  
 <span data-ttu-id="1a9a2-150">データベースを作成できるすべてのユーザーが、データベース スナップショットを作成できます。ただし、ミラー データベースのスナップショットを作成するには、 **sysadmin** 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-150">Any user who can create a database can create a database snapshot; however, to create a snapshot of a mirror database, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="how-to-create-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1a9a2-151">データベース スナップショットの作成方法 (Transact-SQL の使用)</span><span class="sxs-lookup"><span data-stu-id="1a9a2-151">How to Create a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="1a9a2-152">**データベース スナップショットを作成するには**</span><span class="sxs-lookup"><span data-stu-id="1a9a2-152">**To create a database snapshot**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a9a2-153">この手順の例については、このセクションの後半の「 [例 (Transact-SQL)](#TsqlExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-153">For an example of this procedure, see [Examples (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="1a9a2-154">ソース データベースの現在のサイズに基づいて、データベース スナップショットを格納するのに十分なディスク領域があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-154">Based on the current size of the source database, ensure that you have sufficient disk space to hold the database snapshot.</span></span> <span data-ttu-id="1a9a2-155">データベース スナップショットの最大サイズは、スナップショット作成時におけるソース データベースのサイズです。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-155">The maximum size of a database snapshot is the size of the source database at snapshot creation.</span></span> <span data-ttu-id="1a9a2-156">詳細については、「[データベース スナップショットのスパース ファイルのサイズを表示する方法 &#40;Transact-SQL&#41;](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-156">For more information, see [View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="1a9a2-157">AS SNAPSHOT OF 句を使用して、CREATE DATABASE ステートメントをファイルに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-157">Issue a CREATE DATABASE statement on the files using the AS SNAPSHOT OF clause.</span></span> <span data-ttu-id="1a9a2-158">スナップショットを作成するには、ソース データベースの各データベース ファイルの論理名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-158">Creating a snapshot requires specifying the logical name of every database file of the source database.</span></span> <span data-ttu-id="1a9a2-159">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-159">The syntax is as follows:</span></span>  
  
     <span data-ttu-id="1a9a2-160">CREATE DATABASE *database_snapshot_name*</span><span class="sxs-lookup"><span data-stu-id="1a9a2-160">CREATE DATABASE *database_snapshot_name*</span></span>  
  
     <span data-ttu-id="1a9a2-161">ON</span><span class="sxs-lookup"><span data-stu-id="1a9a2-161">ON</span></span>  
  
     <span data-ttu-id="1a9a2-162">(</span><span class="sxs-lookup"><span data-stu-id="1a9a2-162">(</span></span>  
  
     <span data-ttu-id="1a9a2-163">NAME =*logical_file_name*,</span><span class="sxs-lookup"><span data-stu-id="1a9a2-163">NAME =*logical_file_name*,</span></span>  
  
     <span data-ttu-id="1a9a2-164">FILENAME ='*os_file_name*'</span><span class="sxs-lookup"><span data-stu-id="1a9a2-164">FILENAME ='*os_file_name*'</span></span>  
  
     <span data-ttu-id="1a9a2-165">) [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1a9a2-165">) [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="1a9a2-166">AS SNAPSHOT OF *source_database_name*</span><span class="sxs-lookup"><span data-stu-id="1a9a2-166">AS SNAPSHOT OF *source_database_name*</span></span>  
  
     <span data-ttu-id="1a9a2-167">[;]</span><span class="sxs-lookup"><span data-stu-id="1a9a2-167">[;]</span></span>  
  
     <span data-ttu-id="1a9a2-168">*source_\*\*database_name* はソース データベース、*logical_file_name* はファイルを参照するときに SQL Server で使用される論理名、*os_file_name* はファイルを作成する際にオペレーティング システムが使用するパスとファイル名、*database_snapshot_name* はデータベースを戻す対象になるスナップショットの名前です。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-168">Where *source_\*\*database_name* is the source database, *logical_file_name i*s the logical name used in SQL Server when referencing the file, *os_file_name* is the path and file name used by the operating system when you create the file, and *database_snapshot_name* is the name of the snapshot to which you want to revert the database.</span></span> <span data-ttu-id="1a9a2-169">この構文の詳細については、「 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)を使用することです。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-169">For a full description of this syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a9a2-170">データベース スナップショットを作成する場合、ログ ファイル、オフラインのファイル、復元中のファイル、および機能していないファイルを CREATE DATABASE ステートメントで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-170">When you create a database snapshot, log files, offline files, restoring files, and defunct files are not allowed in the CREATE DATABASE statement.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1a9a2-171">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a9a2-171">Examples (Transact-SQL)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a9a2-172">この例で使用している拡張子 `.ss` は任意です。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-172">The `.ss` extension used in the examples is arbitrary.</span></span>  
  
 <span data-ttu-id="1a9a2-173">このセクションには、次の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-173">This section contains the following examples:</span></span>  
  
-   <span data-ttu-id="1a9a2-174">A.</span><span class="sxs-lookup"><span data-stu-id="1a9a2-174">A.</span></span> [<span data-ttu-id="1a9a2-175">AdventureWorks データベースのスナップショットを作成する</span><span class="sxs-lookup"><span data-stu-id="1a9a2-175">Creating a snapshot on the AdventureWorks database</span></span>](#Creating_on_AW)  
  
-   <span data-ttu-id="1a9a2-176">B.</span><span class="sxs-lookup"><span data-stu-id="1a9a2-176">B.</span></span> [<span data-ttu-id="1a9a2-177">Sales データベースのスナップショットを作成する</span><span class="sxs-lookup"><span data-stu-id="1a9a2-177">Creating a snapshot on the Sales database</span></span>](#Creating_on_Sales)  
  
####  <a name="a-creating-a-snapshot-on-the-adventureworks-database"></a><a name="Creating_on_AW"></a> <span data-ttu-id="1a9a2-178">A.</span><span class="sxs-lookup"><span data-stu-id="1a9a2-178">A.</span></span> <span data-ttu-id="1a9a2-179">AdventureWorks データベースのスナップショットを作成する</span><span class="sxs-lookup"><span data-stu-id="1a9a2-179">Creating a snapshot on the AdventureWorks database</span></span>  
 <span data-ttu-id="1a9a2-180">この例では、 `AdventureWorks` データベースのデータベース スナップショットを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-180">This example creates a database snapshot on the `AdventureWorks` database.</span></span> <span data-ttu-id="1a9a2-181">スナップショット名 `AdventureWorks_dbss_1800`と、そのスパース ファイルの名前 `AdventureWorks_data_1800.ss`は、作成時間が午後 6 時 (1,800 時間) であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-181">The snapshot name, `AdventureWorks_dbss_1800`, and the file name of its sparse file, `AdventureWorks_data_1800.ss`, indicate the creation time, 6 P.M (1800 hours).</span></span>  
  
```  
CREATE DATABASE AdventureWorks_dbss1800 ON  
( NAME = AdventureWorks_Data, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data\AdventureWorks_data_1800.ss' )  
AS SNAPSHOT OF AdventureWorks;  
GO  
```  
  
####  <a name="b-creating-a-snapshot-on-the-sales-database"></a><a name="Creating_on_Sales"></a> <span data-ttu-id="1a9a2-182">B.</span><span class="sxs-lookup"><span data-stu-id="1a9a2-182">B.</span></span> <span data-ttu-id="1a9a2-183">Sales データベースのスナップショットを作成する</span><span class="sxs-lookup"><span data-stu-id="1a9a2-183">Creating a snapshot on the Sales database</span></span>  
 <span data-ttu-id="1a9a2-184">この例では、 `sales_snapshot1200`データベースのデータベース スナップショット `Sales` を作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-184">This example creates a database snapshot, `sales_snapshot1200`, on the `Sales` database.</span></span> <span data-ttu-id="1a9a2-185">このデータベースは、「 [CREATE database &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」の例「ファイルグループを持つデータベースの作成」で作成されました。</span><span class="sxs-lookup"><span data-stu-id="1a9a2-185">This database was created in the example, "Creating a database that has filegroups," in [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
```  
--Creating sales_snapshot1200 as snapshot of the  
--Sales database:  
CREATE DATABASE sales_snapshot1200 ON  
( NAME = SPri1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri1dat_1200.ss'),  
( NAME = SPri2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri2dt_1200.ss'),  
( NAME = SGrp1Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\mssql\data\SG1Fi1dt_1200.ss'),  
( NAME = SGrp1Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG1Fi2dt_1200.ss'),  
( NAME = SGrp2Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi1dt_1200.ss'),  
( NAME = SGrp2Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi2dt_1200.ss')  
AS SNAPSHOT OF Sales;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1a9a2-186">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1a9a2-186">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1a9a2-187">データベース スナップショットの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1a9a2-187">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="1a9a2-188">データベースをデータベース スナップショットに戻す</span><span class="sxs-lookup"><span data-stu-id="1a9a2-188">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="1a9a2-189">データベース スナップショットの削除 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1a9a2-189">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="1a9a2-190">参照</span><span class="sxs-lookup"><span data-stu-id="1a9a2-190">See Also</span></span>  
 <span data-ttu-id="1a9a2-191">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1a9a2-191">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="1a9a2-192">Database Snapshots &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1a9a2-192">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
