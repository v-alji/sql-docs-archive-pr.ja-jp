---
title: ページ復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restorepage.general.f1
helpviewer_keywords:
- restoring pages [SQL Server]
- pages [SQL Server], restoring
- databases [SQL Server], damaged
- page restores [SQL Server]
- pages [SQL Server], damaged
- restoring [SQL Server], pages
ms.assetid: 07e40950-384e-4d84-9ac5-84da6dd27a91
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6fb008314b9cb156f1cc575bda71b6364eca6e3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714434"
---
# <a name="restore-pages-sql-server"></a><span data-ttu-id="2a5c0-102">ページ復元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2a5c0-102">Restore Pages (SQL Server)</span></span>
  <span data-ttu-id="2a5c0-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してページを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-103">This topic describes how to restore pages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2a5c0-104">ページ復元の目的は、データベース全体を復元することなく 1 つ以上の損傷したページを復元することです。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-104">The goal of a page restore is to restore one or more damaged pages without restoring the whole database.</span></span> <span data-ttu-id="2a5c0-105">通常、復元候補のページは、そのページにアクセスする際に発生したエラーによって、"問題あり" に設定されています。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-105">Typically, pages that are candidates for restore have been marked as "suspect" because of an error that is encountered when accessing the page.</span></span> <span data-ttu-id="2a5c0-106">問題ありに設定されているページは、 [msdb](/sql/relational-databases/system-tables/suspect-pages-transact-sql) データベースの **suspect_pages** テーブルで特定できます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-106">Suspect pages are identified in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="2a5c0-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2a5c0-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2a5c0-109">どのような場合にページ復元が役立つか</span><span class="sxs-lookup"><span data-stu-id="2a5c0-109">When is a Page Restore Useful?</span></span>](#WhenUseful)  
  
     [<span data-ttu-id="2a5c0-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2a5c0-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2a5c0-111">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="2a5c0-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="2a5c0-112">Security</span><span class="sxs-lookup"><span data-stu-id="2a5c0-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2a5c0-113">**ページを復元する方法:**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-113">**To restore pages, using:**</span></span>  
  
     [<span data-ttu-id="2a5c0-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2a5c0-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2a5c0-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2a5c0-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2a5c0-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="2a5c0-116">Before You Begin</span></span>  
  
###  <a name="when-is-a-page-restore-useful"></a><a name="WhenUseful"></a> <span data-ttu-id="2a5c0-117">どのような場合にページ復元が役立つか</span><span class="sxs-lookup"><span data-stu-id="2a5c0-117">When is a Page Restore Useful?</span></span>  
 <span data-ttu-id="2a5c0-118">ページ復元の目的は、損傷した個々のページを修復することです。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-118">A page restore is intended for repairing isolated damaged pages.</span></span> <span data-ttu-id="2a5c0-119">少数のページに関する復元と復旧は、ファイルの復元を行うより高速に実行でき、復元処理中にオフラインになるデータ量が少なくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-119">Restoring and recovering a few individual pages might be faster than a file restore, reducing the amount of data that is offline during a restore operation.</span></span> <span data-ttu-id="2a5c0-120">ただし、1 つのファイル内の多数のページを復元しなければならない場合は、ファイル全体を復元する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-120">However, if you have to restore more than a few pages in a file, it is generally more efficient to restore the whole file.</span></span> <span data-ttu-id="2a5c0-121">たとえば、デバイス上の多くのページが損傷している場合は、デバイスの故障が差し迫っていることを示している可能性があるので、できれば別の場所にファイルを復元し、デバイスを修復することを検討します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-121">For example, if lots of pages on a device indicate a pending device failure, consider restoring the file, possibly to another location, and repairing the device.</span></span>  
  
 <span data-ttu-id="2a5c0-122">また、すべてのページ エラーが復元を必要とするわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-122">Furthermore, not all page errors require a restore.</span></span> <span data-ttu-id="2a5c0-123">セカンダリ インデックスなど、キャッシュされたデータで発生する問題は、データを再計算することで解決される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-123">A problem can occur in cached data, such as a secondary index, that can be resolved by recalculating the data.</span></span> <span data-ttu-id="2a5c0-124">たとえば、データベース管理者がセカンダリ インデックスを削除して再構築した場合、破損したデータは修正されていますが、 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) テーブルにはそのことが記録されません。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-124">For example, if the database administrator drops a secondary index and rebuilds it, the corrupted data, although fixed, is not indicated as such in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2a5c0-125">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2a5c0-125">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2a5c0-126">ページの復元は、完全復旧モデルまたは一括ログ復旧モデルを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-126">Page restore applies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span> <span data-ttu-id="2a5c0-127">ページ復元は、読み取り/書き込みファイル グループでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-127">Page restore is supported only for read/write filegroups.</span></span>  
  
-   <span data-ttu-id="2a5c0-128">復元できるのはデータベース ページのみです。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-128">Only database pages can be restored.</span></span> <span data-ttu-id="2a5c0-129">ページ復元を使用して、次のものを復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-129">Page restore cannot be used to restore the following:</span></span>  
  
    -   <span data-ttu-id="2a5c0-130">[トランザクション ログ]</span><span class="sxs-lookup"><span data-stu-id="2a5c0-130">Transaction log</span></span>  
  
    -   <span data-ttu-id="2a5c0-131">アロケーション ページ:グローバル アロケーション マップ (GAM) ページ、共有グローバル アロケーション マップ (SGAM) ページ、およびページ空き容量 (PFS) ページ。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-131">Allocation pages: Global Allocation Map (GAM) pages, Shared Global Allocation Map (SGAM) pages, and Page Free Space (PFS) pages.</span></span>  
  
    -   <span data-ttu-id="2a5c0-132">すべてのデータ ファイルのページ 0 (ファイルのブート ページ)</span><span class="sxs-lookup"><span data-stu-id="2a5c0-132">Page 0 of all data files (the file boot page)</span></span>  
  
    -   <span data-ttu-id="2a5c0-133">ページ 1:9 (データベースのブート ページ)</span><span class="sxs-lookup"><span data-stu-id="2a5c0-133">Page 1:9 (the database boot page)</span></span>  
  
    -   <span data-ttu-id="2a5c0-134">フルテキスト カタログ</span><span class="sxs-lookup"><span data-stu-id="2a5c0-134">Full-text catalog</span></span>  
  
-   <span data-ttu-id="2a5c0-135">データベースで一括ログ復旧モデルを使用している場合、ページ復元には次の追加条件があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-135">For a database that uses the bulk-logged recovery model, page restore has the following additional conditions:</span></span>  
  
    -   <span data-ttu-id="2a5c0-136">オフライン データはログに記録されないため、ファイル グループまたはページのデータがオフラインであるときにバックアップを行うと、一括ログ データで問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-136">Backing up while filegroup or page data is offline is problematic for bulk-logged data, because the offline data is not recorded in the log.</span></span> <span data-ttu-id="2a5c0-137">オフライン ページが原因で、ログのバックアップが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-137">Any offline page can prevent backing up the log.</span></span> <span data-ttu-id="2a5c0-138">この場合、最新のバックアップへの復元を実行する場合よりもデータ損失の可能性が低い、DBCC REPAIR の使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-138">In this cases, consider using DBCC REPAIR, because this might cause less data loss than restoring to the most recent backup.</span></span>  
  
    -   <span data-ttu-id="2a5c0-139">一括ログ データベースのログ バックアップで不正なページが検出された場合は、WITH CONTINUE_AFTER_ERROR が指定されていないと失敗します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-139">If a log backup of a bulk-logged database encounters a bad page, it fails unless WITH CONTINUE_AFTER_ERROR is specified.</span></span>  
  
    -   <span data-ttu-id="2a5c0-140">ページ復元は、一般的に一括ログ復旧では使用できません。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-140">Page restore generally does not work with bulk-logged recovery.</span></span>  
  
         <span data-ttu-id="2a5c0-141">ページ復元の実行で推奨されるのは、データベースを完全復旧モデルに設定し、ログ バックアップを試行する方法です。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-141">A best practice for performing page restore is to set the database to the full recovery model, and try a log backup.</span></span> <span data-ttu-id="2a5c0-142">ログ バックアップが成功した場合は、ページ復元を開始できます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-142">If the log backup works, you can continue with the page restore.</span></span> <span data-ttu-id="2a5c0-143">ログ バックアップが失敗した場合は、前回のログ バックアップ以降の作業をあきらめるか、REPAIR_ALLOW_DATA_LOSS オプションを指定して DBCC を実行してみる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-143">If the log backup fails, you either have to lose work since the previous log backup or you have to try running DBCC must be run with the REPAIR_ALLOW_DATA_LOSS option.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2a5c0-144">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2a5c0-144">Recommendations</span></span>  
  
-   <span data-ttu-id="2a5c0-145">ページ復元のシナリオ:</span><span class="sxs-lookup"><span data-stu-id="2a5c0-145">Page restore scenarios:</span></span>  
  
     <span data-ttu-id="2a5c0-146">オフライン ページ復元</span><span class="sxs-lookup"><span data-stu-id="2a5c0-146">Offline page restore</span></span>  
     <span data-ttu-id="2a5c0-147">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションでは、データベースがオフラインのときにページ復元を実行できます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-147">All editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support restoring pages when the database is offline.</span></span> <span data-ttu-id="2a5c0-148">オフライン ページ復元では、損傷したページの復元中はデータベースがオフラインです。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-148">In an offline page restore, the database is offline while damaged pages are restored.</span></span> <span data-ttu-id="2a5c0-149">データベースは、復元シーケンスの最後にオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-149">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="2a5c0-150">オンライン ページ復元</span><span class="sxs-lookup"><span data-stu-id="2a5c0-150">Online page restore</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2a5c0-151">Enterprise Edition では、データベースがオフラインであるときにはオフライン復元が使用される一方、オンラインでのページ復元もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-151">Enterprise edition supports online page restores, though they use offline restore if the database is currently offline.</span></span> <span data-ttu-id="2a5c0-152">ほとんどの場合、ページを復元しているファイル グループを含むデータベースをオンラインにしたまま、損傷したページを復元できます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-152">In most cases, a damaged page can be restored while the database remains online, including the filegroup to which a page is being restored.</span></span> <span data-ttu-id="2a5c0-153">プライマリ ファイル グループがオンラインの場合、そのセカンダリ ファイル グループがオフラインでも、通常は、オンラインによるページ復元が実行されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-153">When the primary filegroup is online, even if one or more of its secondary filegroups are offline, page restores are usually performed online.</span></span> <span data-ttu-id="2a5c0-154">ただし、場合によっては、損傷したページをオフラインで復元することも必要です。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-154">Occasionally, however, a damaged page can require an offline restore.</span></span> <span data-ttu-id="2a5c0-155">たとえば、特定の重要なページが損傷したことが原因で、データベースを起動できない可能性がある場合などです。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-155">For example, damage to certain critical pages might prevent the database from starting.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="2a5c0-156">破損したページにデータベースの重要なメタデータが格納されている場合、オンラインでのページ復元を試行する際、メタデータに対する必要な更新処理に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-156">If damaged pages are storing critical database metadata, required updates to metadata might fail during an online page restore attempt.</span></span> <span data-ttu-id="2a5c0-157">この場合は、オフラインでのページ復元を実行できます。ただし、その場合はまず、RESTORE WITH NORECOVERY でトランザクション ログをバックアップして、 [ログ末尾のバックアップ](tail-log-backups-sql-server.md) を作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-157">In this case, you can perform an offline page restore, but first you must create a [tail log backup](tail-log-backups-sql-server.md) (by backing up the transaction log using RESTORE WITH NORECOVERY).</span></span>  
  
-   <span data-ttu-id="2a5c0-158">ページ復元では、ページ レベルのエラー報告 (ページ チェックサムを含む) および追跡の機能を活用することができます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-158">Page restore takes advantage of the improved page-level error reporting (including page checksums) and tracking.</span></span> <span data-ttu-id="2a5c0-159">チェックサムや破損した書き込みによって壊れていることが検出されたページ ( *損傷したページ*) は、ページ復元操作によって復元できます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-159">Pages that are detected as corrupted by check-summing or a torn write, *damaged pages*, can be restored by a page restore operation.</span></span> <span data-ttu-id="2a5c0-160">復元されるのは、明示的に指定したページのみです。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-160">Only explicitly specified pages are restored.</span></span> <span data-ttu-id="2a5c0-161">指定した各ページが、指定のデータ バックアップから取得されたページのコピーで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-161">Each specified page is replaced by the copy of that page from the specified data backup.</span></span>  
  
     <span data-ttu-id="2a5c0-162">それ以降、ログ バックアップを復元した場合、復元対象のページが少なくとも 1 つ存在するデータベース ファイルにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-162">When you restore the subsequent log backups, they are applied only to database files that contain at least one page that is being recovered.</span></span> <span data-ttu-id="2a5c0-163">また、最新の完全復元または差分復元にチェーンが途切れていないログ バックアップを適用し、ページを含むファイル グループに現在のログ ファイルの状態を反映する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-163">An unbroken chain of log backups must be applied to the last full or differential restore to bring the filegroup that contains the page forward to the current log file.</span></span> <span data-ttu-id="2a5c0-164">ファイル復元と同様に、ロールフォワード セットは 1 つのログ再実行パスで進められます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-164">As in a file restore, the roll forward set is advanced with a single log redo pass.</span></span> <span data-ttu-id="2a5c0-165">正常にページ復元を完了するには、データベースとの一貫性が保たれた状態になるようにページを復旧する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-165">For a page restore to succeed, the restored pages must be recovered to a state consistent with the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2a5c0-166">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2a5c0-166">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2a5c0-167">Permissions</span><span class="sxs-lookup"><span data-stu-id="2a5c0-167">Permissions</span></span>  
 <span data-ttu-id="2a5c0-168">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-168">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="2a5c0-169">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-169">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="2a5c0-170">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-170">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="2a5c0-171">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-171">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2a5c0-172">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2a5c0-172">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2a5c0-173">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、新たに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でのページ復元がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-173">Starting in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports page restores.</span></span>  
  
#### <a name="to-restore-pages"></a><span data-ttu-id="2a5c0-174">ページを復元するには</span><span class="sxs-lookup"><span data-stu-id="2a5c0-174">To restore pages</span></span>  
  
1.  <span data-ttu-id="2a5c0-175">適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーでサーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-175">Connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="2a5c0-176">**[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-176">Expand **Databases**.</span></span> <span data-ttu-id="2a5c0-177">復元するデータベースに応じて、ユーザー データベースを選択するか、 **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-177">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="2a5c0-178">データベースを右クリックし、 **[タスク]** 、 **[復元]** の順にポイントし、 **[ページ]** をクリックします。 **[ページの復元]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-178">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Page**, which opens the **Restore Page** dialog box.</span></span>  
  
     <span data-ttu-id="2a5c0-179">**復元**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-179">**Restore**</span></span>  
     <span data-ttu-id="2a5c0-180">このセクションでは、 **[データベースの復元]\([全般] ページ)** の [[復元先]](../../integration-services/general-page-of-integration-services-designers-options.md)と同じ機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-180">This section performs the same function as that of **Restore to** on the [Restore Database (General Page)](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
     <span data-ttu-id="2a5c0-181">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-181">**Database**</span></span>  
     <span data-ttu-id="2a5c0-182">復元するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-182">Specifies the database to restore.</span></span> <span data-ttu-id="2a5c0-183">新しいデータベースを入力するか、ドロップダウン リストから既存のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-183">You can enter a new database or select an existing database from the drop-down list.</span></span> <span data-ttu-id="2a5c0-184">このリストには、システム データベース **master** および **tempdb**を除いた、サーバー上のすべてのデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-184">The list includes all databases on the server, except the system databases **master** and **tempdb**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="2a5c0-185">パスワードで保護されたバックアップを復元するには、 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-185">To restore a password-protected backup, you must use the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="2a5c0-186">**[ログ末尾のバックアップ]**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-186">**Tail-Log backup**</span></span>  
     <span data-ttu-id="2a5c0-187">**[バックアップ デバイス]** に、データベースのログ末尾バックアップを保存するファイル名を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-187">Enter or select a file name in **Backup device** where there tail-log backup will be stored for the database.</span></span>  
  
     <span data-ttu-id="2a5c0-188">**バックアップ セット**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-188">**Backup Sets**</span></span>  
     <span data-ttu-id="2a5c0-189">このセクションには、復元に関連するバックアップ セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-189">This section displays the backup sets involved in the restoration.</span></span>  
  
    |<span data-ttu-id="2a5c0-190">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="2a5c0-190">Header</span></span>|<span data-ttu-id="2a5c0-191">値</span><span class="sxs-lookup"><span data-stu-id="2a5c0-191">Values</span></span>|  
    |------------|------------|  
    |<span data-ttu-id="2a5c0-192">**名前**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-192">**Name**</span></span>|<span data-ttu-id="2a5c0-193">バックアップ セットの名前です。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-193">The name of the backup set.</span></span>|  
    |<span data-ttu-id="2a5c0-194">**コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-194">**Component**</span></span>|<span data-ttu-id="2a5c0-195">バックアップされるコンポーネント: **[データベース]** 、 **[ファイル]** 、または **\<blank>** (トランザクション ログ用)。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-195">The backed-up component: **Database**, **File**, or **\<blank>** (for transaction logs).</span></span>|  
    |<span data-ttu-id="2a5c0-196">**Type**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-196">**Type**</span></span>|<span data-ttu-id="2a5c0-197">実行するバックアップの種類: **[完全]** 、 **[差分]** 、 **[トランザクション ログ]** 。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-197">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="2a5c0-198">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-198">**Server**</span></span>|<span data-ttu-id="2a5c0-199">バックアップ操作を実行した [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-199">The name of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="2a5c0-200">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-200">**Database**</span></span>|<span data-ttu-id="2a5c0-201">バックアップ操作に呼び出されるデータベース名です。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-201">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="2a5c0-202">**Position**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-202">**Position**</span></span>|<span data-ttu-id="2a5c0-203">ボリューム内でのバックアップ セットの位置。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-203">The position of the backup set in the volume.</span></span>|  
    |<span data-ttu-id="2a5c0-204">**最初の LSN**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-204">**First LSN**</span></span>|<span data-ttu-id="2a5c0-205">バックアップ セット内の最初のトランザクションのログ シーケンス番号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-205">The log sequence number (LSN) of the first transaction in the backup set.</span></span> <span data-ttu-id="2a5c0-206">ファイル バックアップの場合は空白。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-206">Blank for file backups.</span></span>|  
    |<span data-ttu-id="2a5c0-207">**最後の LSN**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-207">**Last LSN**</span></span>|<span data-ttu-id="2a5c0-208">バックアップ セット内の最後のトランザクションのログ シーケンス番号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-208">The log sequence number (LSN) of the last transaction in the backup set.</span></span> <span data-ttu-id="2a5c0-209">ファイル バックアップの場合は空白。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-209">Blank for file backups.</span></span>|  
    |<span data-ttu-id="2a5c0-210">**チェックポイントの LSN**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-210">**Checkpoint LSN**</span></span>|<span data-ttu-id="2a5c0-211">バックアップが作成された時点で最新のチェックポイントのログ シーケンス番号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-211">The log sequence number (LSN) of the most recent checkpoint at the time the backup was created.</span></span>|  
    |<span data-ttu-id="2a5c0-212">**全 LSN**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-212">**Full LSN**</span></span>|<span data-ttu-id="2a5c0-213">最新のデータベースの完全バックアップのログ シーケンス番号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-213">The log sequence number (LSN) of the most recent full database backup.</span></span>|  
    |<span data-ttu-id="2a5c0-214">**[開始日]**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-214">**Start Date**</span></span>|<span data-ttu-id="2a5c0-215">バックアップ操作が開始した日時で、クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-215">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="2a5c0-216">**完了日**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-216">**Finish Date**</span></span>|<span data-ttu-id="2a5c0-217">バックアップ操作が完了したときの日付と時刻。クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-217">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="2a5c0-218">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-218">**Size**</span></span>|<span data-ttu-id="2a5c0-219">バックアップ セットのサイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-219">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="2a5c0-220">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-220">**User Name**</span></span>|<span data-ttu-id="2a5c0-221">バックアップ操作を実行したユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-221">The name of the user who performed the backup operation.</span></span>|  
    |<span data-ttu-id="2a5c0-222">**[有効期限]**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-222">**Expiration**</span></span>|<span data-ttu-id="2a5c0-223">バックアップ セットの期限が切れる日付と時刻。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-223">The date and time the backup set expires.</span></span>|  
  
     <span data-ttu-id="2a5c0-224">**[確認]** をクリックして、ページ復元操作の実行に必要なバックアップ ファイルの整合性を確認します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-224">Click **Verify** to check the integrity of the backup files needed to perform the page restore operation.</span></span>  
  
4.  <span data-ttu-id="2a5c0-225">破損したページを識別するには、 **[データベース]** ボックスで適切なデータベースを選択した状態で、 **[データベース ページの確認]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-225">To identify corrupted pages, with the correct database selected in the **Database** box, click **Check Database Pages**.</span></span> <span data-ttu-id="2a5c0-226">この操作の実行には時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-226">This is a long running operation.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="2a5c0-227">破損していない特定のページを復元するには、 **[追加]** をクリックし、復元するページの **[ファイル ID]** と **[ページ ID]** を入力します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-227">To restore specific pages that are not corrupted, click **Add** and enter the **File ID** and **Page ID** of the pages to be restored.</span></span>  
  
5.  <span data-ttu-id="2a5c0-228">ページ グリッドを使用して、復元対象のページを特定します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-228">The pages grid is used to identify the pages to be restored.</span></span> <span data-ttu-id="2a5c0-229">最初、このグリッドには、 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) システム テーブルから取得されたデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-229">Initially, this grid is populated from the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) system table.</span></span> <span data-ttu-id="2a5c0-230">このグリッドにページを追加したりグリッドからページを削除したりするには、 **[追加]** または **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-230">To add or remove pages from the grid, click **Add** or **Remove**.</span></span> <span data-ttu-id="2a5c0-231">詳細については、「[suspect_pages テーブルの管理 &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-231">For more information, see [Manage the suspect_pages Table &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md).</span></span>  
  
6.  <span data-ttu-id="2a5c0-232">**[バックアップ セット]** グリッドに、既定の復元プランのバックアップ セットが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-232">The **Backup sets** grid lists the backup sets in the default restore plan.</span></span> <span data-ttu-id="2a5c0-233">必要に応じて **[確認]** をクリックし、バックアップが読み取り可能かどうか、また、バックアップ セットに不備がないかどうかを、実際には復元せずに確認します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-233">Optionally, click **Verify** to verify that the backups are readable and that the backup sets are complete, without restoring them.</span></span> <span data-ttu-id="2a5c0-234">詳細については、「[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-234">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
     <span data-ttu-id="2a5c0-235">**ページ**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-235">**Pages**</span></span>  
  
7.  <span data-ttu-id="2a5c0-236">ページ グリッドに一覧表示されたページを復元するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-236">To restore the pages listed in the pages grid, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2a5c0-237">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2a5c0-237">Using Transact-SQL</span></span>  
 <span data-ttu-id="2a5c0-238">RESTORE DATABASE ステートメントでページを指定するには、ページを含むファイルのファイル ID とページのページ ID が必要です。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-238">To specify a page in a RESTORE DATABASE statement, you need the file ID of the file containing the page and the page ID of the page.</span></span> <span data-ttu-id="2a5c0-239">必須の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-239">The required syntax is as follows:</span></span>  
  
 `RESTORE DATABASE <database_name>`  
  
 `PAGE = '<file: page> [ ,... n ] ' [ ,... n ]`  
  
 `FROM <backup_device> [ ,... n ]`  
  
 `WITH NORECOVERY`  
  
 <span data-ttu-id="2a5c0-240">PAGE オプションのパラメーターの詳細については、「[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-240">For more information about the parameters of the PAGE option, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span> <span data-ttu-id="2a5c0-241">RESTORE DATABASE の構文の詳細については、「[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-241">For more information about the RESTORE DATABASE syntax, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
#### <a name="to-restore-pages"></a><span data-ttu-id="2a5c0-242">ページを復元するには</span><span class="sxs-lookup"><span data-stu-id="2a5c0-242">To restore pages</span></span>  
  
1.  <span data-ttu-id="2a5c0-243">復元する損傷したページのページ ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-243">Obtain the page IDs of the damaged pages to be restored.</span></span> <span data-ttu-id="2a5c0-244">チェックサムまたは破損した書き込みのエラーによってページ ID が返され、ページを指定するために必要な情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-244">A checksum or torn write error returns page ID, providing the information required for specifying the pages.</span></span> <span data-ttu-id="2a5c0-245">損傷したページのページ ID を検索するには、次のいずれかのソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-245">To look up page ID of a damaged page, use any of the following sources.</span></span>  
  
    |<span data-ttu-id="2a5c0-246">ページ ID のソース</span><span class="sxs-lookup"><span data-stu-id="2a5c0-246">Source of page ID</span></span>|<span data-ttu-id="2a5c0-247">トピック</span><span class="sxs-lookup"><span data-stu-id="2a5c0-247">Topic</span></span>|  
    |-----------------------|-----------|  
    |<span data-ttu-id="2a5c0-248">**msdb..suspect_pages**</span><span class="sxs-lookup"><span data-stu-id="2a5c0-248">**msdb..suspect_pages**</span></span>|[<span data-ttu-id="2a5c0-249">suspect_pages テーブルの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a5c0-249">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](manage-the-suspect-pages-table-sql-server.md)|  
    |<span data-ttu-id="2a5c0-250">エラー ログ</span><span class="sxs-lookup"><span data-stu-id="2a5c0-250">Error log</span></span>|[<span data-ttu-id="2a5c0-251">SQL Server エラー ログの表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="2a5c0-251">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)|  
    |<span data-ttu-id="2a5c0-252">イベント トレース</span><span class="sxs-lookup"><span data-stu-id="2a5c0-252">Event traces</span></span>|[<span data-ttu-id="2a5c0-253">イベントの監視と応答</span><span class="sxs-lookup"><span data-stu-id="2a5c0-253">Monitor and Respond to Events</span></span>](../../ssms/agent/monitor-and-respond-to-events.md)|  
    |<span data-ttu-id="2a5c0-254">DBCC</span><span class="sxs-lookup"><span data-stu-id="2a5c0-254">DBCC</span></span>|[<span data-ttu-id="2a5c0-255">DBCC &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a5c0-255">DBCC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-transact-sql)|  
    |<span data-ttu-id="2a5c0-256">WMI プロバイダー</span><span class="sxs-lookup"><span data-stu-id="2a5c0-256">WMI provider</span></span>|[<span data-ttu-id="2a5c0-257">WMI Provider for Server Events の概念</span><span class="sxs-lookup"><span data-stu-id="2a5c0-257">WMI Provider for Server Events Concepts</span></span>](../wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)|  
  
2.  <span data-ttu-id="2a5c0-258">損傷したページが含まれている、データベースの完全バックアップ、ファイル バックアップ、またはファイル グループ バックアップを使用して、ページ復元を開始します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-258">Start a page restore with a full database, file, or filegroup backup that contains the page.</span></span> <span data-ttu-id="2a5c0-259">RESTORE DATABASE ステートメントで PAGE 句を使用して、復元する全ページのページ ID の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-259">In the RESTORE DATABASE statement, use the PAGE clause to list the page IDs of all of the pages to be restored.</span></span>  
  
3.  <span data-ttu-id="2a5c0-260">最新の差分バックアップを適用します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-260">Apply the most recent differentials .</span></span>  
  
4.  <span data-ttu-id="2a5c0-261">後続のログ バックアップを適用します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-261">Apply the subsequent log backups.</span></span>  
  
5.  <span data-ttu-id="2a5c0-262">復元されたページの最終 LSN を含むデータベースの新しいログ バックアップ (最後に復元されたページがオフラインになった時点までのログ バックアップ) を作成します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-262">Create a new log backup of the database that includes the final LSN of the restored pages, that is, the point at which the last restored page is taken offline.</span></span> <span data-ttu-id="2a5c0-263">この最終 LSN が、再実行ターゲット LSN になります。最終 LSN は、復元シーケンス内の最初の復元の一環として設定されます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-263">The final LSN, which is set as part of the first restore in the sequence, is the redo target LSN.</span></span> <span data-ttu-id="2a5c0-264">損傷したページを含むファイルのオンラインのロールフォワードは、再実行ターゲット LSN で停止することができます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-264">Online roll forward of the file containing the page is able to stop at the redo target LSN.</span></span> <span data-ttu-id="2a5c0-265">ファイルの現在の再実行ターゲット LSN は、**sys.master_files** の **redo_target_lsn** 列で確認できます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-265">To learn the current redo target LSN of a file, see the **redo_target_lsn** column of **sys.master_files**.</span></span> <span data-ttu-id="2a5c0-266">詳細については、「[sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-266">For more information, see [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql).</span></span>  
  
6.  <span data-ttu-id="2a5c0-267">新しいログ バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-267">Restore the new log backup.</span></span> <span data-ttu-id="2a5c0-268">この新しいログ バックアップを適用すると、ページ復元が完了し、ページが使用可能な状態になります。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-268">After this new log backup is applied, the page restore is completed and the pages are now usable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a5c0-269">この復元シーケンスは、ファイル復元シーケンスと似ています。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-269">This sequence is analogous to a file restore sequence.</span></span> <span data-ttu-id="2a5c0-270">実際、ページ復元とファイル復元は、どちらも同じ復元シーケンスで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-270">In fact, page restore and file restores can both be performed as part of the same sequence.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2a5c0-271">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2a5c0-271">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="2a5c0-272">次の例では、 `B` を指定して、ファイル `NORECOVERY`の 4 つの損傷したページを復元します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-272">The following example restores four damaged pages of file `B` with `NORECOVERY`.</span></span> <span data-ttu-id="2a5c0-273">次に、 `NORECOVERY`を使用して 2 つのログ バックアップを適用してから、 `RECOVERY`を使用してログ末尾のバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-273">Next, two log backups are applied with `NORECOVERY`, followed with the tail-log backup, which is restored with `RECOVERY`.</span></span> <span data-ttu-id="2a5c0-274">次の例では、オンライン復元を実行します。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-274">This example performs an online restore.</span></span> <span data-ttu-id="2a5c0-275">この例では、ファイル `B` のファイル ID が `1`で、損傷したページのページ ID は `57`、 `202`、 `916`、および `1016`です。</span><span class="sxs-lookup"><span data-stu-id="2a5c0-275">In the example, the file ID of file `B` is `1`, and the page IDs of the damaged pages are `57`, `202`, `916`, and `1016`.</span></span>  
  
```sql  
RESTORE DATABASE <database> PAGE='1:57, 1:202, 1:916, 1:1016'  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
RESTORE LOG <database> FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG <database> FROM <log_backup>   
   WITH NORECOVERY;   
BACKUP LOG <database> TO <new_log_backup>;   
RESTORE LOG <database> FROM <new_log_backup> WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a5c0-276">参照</span><span class="sxs-lookup"><span data-stu-id="2a5c0-276">See Also</span></span>  
 <span data-ttu-id="2a5c0-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2a5c0-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="2a5c0-278">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a5c0-278">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="2a5c0-279">[suspect_pages テーブルの管理 &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a5c0-279">[Manage the suspect_pages Table &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md) </span></span>  
 [<span data-ttu-id="2a5c0-280">SQL Server データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="2a5c0-280">Back Up and Restore of SQL Server Databases</span></span>](back-up-and-restore-of-sql-server-databases.md)  
  
  
