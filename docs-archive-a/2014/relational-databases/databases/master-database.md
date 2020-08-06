---
title: master データベース | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], about
- master database [SQL Server]
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac38453237ed6816c32ed974e8141c57c93ceb44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742166"
---
# <a name="master-database"></a><span data-ttu-id="9a466-102">master データベース</span><span class="sxs-lookup"><span data-stu-id="9a466-102">master Database</span></span>
  <span data-ttu-id="9a466-103">**master** データベースには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムのシステム レベルの情報がすべて記録されます。</span><span class="sxs-lookup"><span data-stu-id="9a466-103">The **master** database records all the system-level information for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system.</span></span> <span data-ttu-id="9a466-104">記録される情報には、ログオン アカウント、エンドポイント、リンク サーバー、システム構成設定など、インスタンス全体のメタデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9a466-104">This includes instance-wide metadata such as logon accounts, endpoints, linked servers, and system configuration settings.</span></span> <span data-ttu-id="9a466-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、システム オブジェクトが **master** データベースではなく、 [Resource データベース](resource-database.md)に格納されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9a466-105">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], system objects are no longer stored in the **master** database; instead, they are stored in the [Resource database](resource-database.md).</span></span> <span data-ttu-id="9a466-106">また、 **master** は、他のすべてのデータベースの存在、それらのデータベース ファイルの場所、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の初期化情報を記録するデータベースでもあります。</span><span class="sxs-lookup"><span data-stu-id="9a466-106">Also, **master** is the database that records the existence of all other databases and the location of those database files and records the initialization information for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9a466-107">したがって、 **master** データベースが使用できないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を開始できません。</span><span class="sxs-lookup"><span data-stu-id="9a466-107">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot start if the **master** database is unavailable.</span></span>  
  
## <a name="physical-properties-of-master"></a><span data-ttu-id="9a466-108">master データベースの物理プロパティ</span><span class="sxs-lookup"><span data-stu-id="9a466-108">Physical Properties of master</span></span>  
 <span data-ttu-id="9a466-109">\line 次の表は、 **master** のデータ ファイルとログ ファイルの初期構成値の一覧です。</span><span class="sxs-lookup"><span data-stu-id="9a466-109">The following table lists the initial configuration values of the **master** data and log files.</span></span> <span data-ttu-id="9a466-110">これらのファイルのサイズは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエディションによって多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9a466-110">The sizes of these files may vary slightly for different editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="9a466-111">ファイル</span><span class="sxs-lookup"><span data-stu-id="9a466-111">File</span></span>|<span data-ttu-id="9a466-112">論理名</span><span class="sxs-lookup"><span data-stu-id="9a466-112">Logical name</span></span>|<span data-ttu-id="9a466-113">物理名</span><span class="sxs-lookup"><span data-stu-id="9a466-113">Physical name</span></span>|<span data-ttu-id="9a466-114">ファイル拡張</span><span class="sxs-lookup"><span data-stu-id="9a466-114">File growth</span></span>|  
|----------|------------------|-------------------|-----------------|  
|<span data-ttu-id="9a466-115">プライマリ データ</span><span class="sxs-lookup"><span data-stu-id="9a466-115">Primary data</span></span>|<span data-ttu-id="9a466-116">master</span><span class="sxs-lookup"><span data-stu-id="9a466-116">master</span></span>|<span data-ttu-id="9a466-117">master.mdf</span><span class="sxs-lookup"><span data-stu-id="9a466-117">master.mdf</span></span>|<span data-ttu-id="9a466-118">ディスクがいっぱいになるまで 10% ずつ自動拡張</span><span class="sxs-lookup"><span data-stu-id="9a466-118">Autogrow by 10 percent until the disk is full.</span></span>|  
|<span data-ttu-id="9a466-119">ログ</span><span class="sxs-lookup"><span data-stu-id="9a466-119">Log</span></span>|<span data-ttu-id="9a466-120">mastlog</span><span class="sxs-lookup"><span data-stu-id="9a466-120">mastlog</span></span>|<span data-ttu-id="9a466-121">mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="9a466-121">mastlog.ldf</span></span>|<span data-ttu-id="9a466-122">最大 2 TB まで 10% ずつ自動拡張</span><span class="sxs-lookup"><span data-stu-id="9a466-122">Autogrow by 10 percent to a maximum of 2 terabytes.</span></span>|  
  
 <span data-ttu-id="9a466-123">**master** のデータ ファイルとログ ファイルの移動方法の詳細については、「 [システム データベースの移動](system-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a466-123">For information about how to move the **master** data and log files, see [Move System Databases](system-databases.md).</span></span>  
  
### <a name="database-options"></a><span data-ttu-id="9a466-124">データベース オプション</span><span class="sxs-lookup"><span data-stu-id="9a466-124">Database Options</span></span>  
 <span data-ttu-id="9a466-125">**master** データベースの各データベース オプションの既定値とそのオプションを変更できるかどうかを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9a466-125">The following table lists the default value for each database option in the **master** database and whether the option can be modified.</span></span> <span data-ttu-id="9a466-126">これらのオプションの現在の設定を表示するには、 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) カタログ ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a466-126">To view the current settings for these options, use the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
|<span data-ttu-id="9a466-127">データベース オプション</span><span class="sxs-lookup"><span data-stu-id="9a466-127">Database option</span></span>|<span data-ttu-id="9a466-128">既定値</span><span class="sxs-lookup"><span data-stu-id="9a466-128">Default value</span></span>|<span data-ttu-id="9a466-129">変更可否</span><span class="sxs-lookup"><span data-stu-id="9a466-129">Can be modified</span></span>|  
|---------------------|-------------------|---------------------|  
|<span data-ttu-id="9a466-130">ALLOW_SNAPSHOT_ISOLATION</span><span class="sxs-lookup"><span data-stu-id="9a466-130">ALLOW_SNAPSHOT_ISOLATION</span></span>|<span data-ttu-id="9a466-131">ON</span><span class="sxs-lookup"><span data-stu-id="9a466-131">ON</span></span>|<span data-ttu-id="9a466-132">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-132">No</span></span>|  
|<span data-ttu-id="9a466-133">ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a466-133">ANSI_NULL_DEFAULT</span></span>|<span data-ttu-id="9a466-134">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-134">OFF</span></span>|<span data-ttu-id="9a466-135">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-135">Yes</span></span>|  
|<span data-ttu-id="9a466-136">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="9a466-136">ANSI_NULLS</span></span>|<span data-ttu-id="9a466-137">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-137">OFF</span></span>|<span data-ttu-id="9a466-138">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-138">Yes</span></span>|  
|<span data-ttu-id="9a466-139">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="9a466-139">ANSI_PADDING</span></span>|<span data-ttu-id="9a466-140">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-140">OFF</span></span>|<span data-ttu-id="9a466-141">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-141">Yes</span></span>|  
|<span data-ttu-id="9a466-142">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="9a466-142">ANSI_WARNINGS</span></span>|<span data-ttu-id="9a466-143">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-143">OFF</span></span>|<span data-ttu-id="9a466-144">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-144">Yes</span></span>|  
|<span data-ttu-id="9a466-145">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="9a466-145">ARITHABORT</span></span>|<span data-ttu-id="9a466-146">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-146">OFF</span></span>|<span data-ttu-id="9a466-147">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-147">Yes</span></span>|  
|<span data-ttu-id="9a466-148">AUTO_CLOSE</span><span class="sxs-lookup"><span data-stu-id="9a466-148">AUTO_CLOSE</span></span>|<span data-ttu-id="9a466-149">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-149">OFF</span></span>|<span data-ttu-id="9a466-150">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-150">No</span></span>|  
|<span data-ttu-id="9a466-151">AUTO_CREATE_STATISTICS</span><span class="sxs-lookup"><span data-stu-id="9a466-151">AUTO_CREATE_STATISTICS</span></span>|<span data-ttu-id="9a466-152">ON</span><span class="sxs-lookup"><span data-stu-id="9a466-152">ON</span></span>|<span data-ttu-id="9a466-153">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-153">Yes</span></span>|  
|<span data-ttu-id="9a466-154">AUTO_SHRINK</span><span class="sxs-lookup"><span data-stu-id="9a466-154">AUTO_SHRINK</span></span>|<span data-ttu-id="9a466-155">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-155">OFF</span></span>|<span data-ttu-id="9a466-156">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-156">No</span></span>|  
|<span data-ttu-id="9a466-157">AUTO_UPDATE_STATISTICS</span><span class="sxs-lookup"><span data-stu-id="9a466-157">AUTO_UPDATE_STATISTICS</span></span>|<span data-ttu-id="9a466-158">ON</span><span class="sxs-lookup"><span data-stu-id="9a466-158">ON</span></span>|<span data-ttu-id="9a466-159">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-159">Yes</span></span>|  
|<span data-ttu-id="9a466-160">AUTO_UPDATE_STATISTICS_ASYNC</span><span class="sxs-lookup"><span data-stu-id="9a466-160">AUTO_UPDATE_STATISTICS_ASYNC</span></span>|<span data-ttu-id="9a466-161">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-161">OFF</span></span>|<span data-ttu-id="9a466-162">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-162">Yes</span></span>|  
|<span data-ttu-id="9a466-163">CHANGE_TRACKING</span><span class="sxs-lookup"><span data-stu-id="9a466-163">CHANGE_TRACKING</span></span>|<span data-ttu-id="9a466-164">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-164">OFF</span></span>|<span data-ttu-id="9a466-165">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-165">No</span></span>|  
|<span data-ttu-id="9a466-166">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="9a466-166">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="9a466-167">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-167">OFF</span></span>|<span data-ttu-id="9a466-168">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-168">Yes</span></span>|  
|<span data-ttu-id="9a466-169">CURSOR_CLOSE_ON_COMMIT</span><span class="sxs-lookup"><span data-stu-id="9a466-169">CURSOR_CLOSE_ON_COMMIT</span></span>|<span data-ttu-id="9a466-170">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-170">OFF</span></span>|<span data-ttu-id="9a466-171">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-171">Yes</span></span>|  
|<span data-ttu-id="9a466-172">CURSOR_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a466-172">CURSOR_DEFAULT</span></span>|<span data-ttu-id="9a466-173">GLOBAL</span><span class="sxs-lookup"><span data-stu-id="9a466-173">GLOBAL</span></span>|<span data-ttu-id="9a466-174">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-174">Yes</span></span>|  
|<span data-ttu-id="9a466-175">データベース可用性オプション</span><span class="sxs-lookup"><span data-stu-id="9a466-175">Database Availability Options</span></span>|<span data-ttu-id="9a466-176">ONLINE</span><span class="sxs-lookup"><span data-stu-id="9a466-176">ONLINE</span></span><br /><br /> <span data-ttu-id="9a466-177">MULTI_USER</span><span class="sxs-lookup"><span data-stu-id="9a466-177">MULTI_USER</span></span><br /><br /> <span data-ttu-id="9a466-178">READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="9a466-178">READ_WRITE</span></span>|<span data-ttu-id="9a466-179">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-179">No</span></span><br /><br /> <span data-ttu-id="9a466-180">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-180">No</span></span><br /><br /> <span data-ttu-id="9a466-181">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-181">No</span></span>|  
|<span data-ttu-id="9a466-182">DATE_CORRELATION_OPTIMIZATION</span><span class="sxs-lookup"><span data-stu-id="9a466-182">DATE_CORRELATION_OPTIMIZATION</span></span>|<span data-ttu-id="9a466-183">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-183">OFF</span></span>|<span data-ttu-id="9a466-184">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-184">Yes</span></span>|  
|<span data-ttu-id="9a466-185">DB_CHAINING</span><span class="sxs-lookup"><span data-stu-id="9a466-185">DB_CHAINING</span></span>|<span data-ttu-id="9a466-186">ON</span><span class="sxs-lookup"><span data-stu-id="9a466-186">ON</span></span>|<span data-ttu-id="9a466-187">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-187">No</span></span>|  
|<span data-ttu-id="9a466-188">ENCRYPTION</span><span class="sxs-lookup"><span data-stu-id="9a466-188">ENCRYPTION</span></span>|<span data-ttu-id="9a466-189">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-189">OFF</span></span>|<span data-ttu-id="9a466-190">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-190">No</span></span>|  
|<span data-ttu-id="9a466-191">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="9a466-191">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="9a466-192">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-192">OFF</span></span>|<span data-ttu-id="9a466-193">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-193">Yes</span></span>|  
|<span data-ttu-id="9a466-194">PAGE_VERIFY</span><span class="sxs-lookup"><span data-stu-id="9a466-194">PAGE_VERIFY</span></span>|<span data-ttu-id="9a466-195">CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="9a466-195">CHECKSUM</span></span>|<span data-ttu-id="9a466-196">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-196">Yes</span></span>|  
|<span data-ttu-id="9a466-197">PARAMETERIZATION</span><span class="sxs-lookup"><span data-stu-id="9a466-197">PARAMETERIZATION</span></span>|<span data-ttu-id="9a466-198">SIMPLE</span><span class="sxs-lookup"><span data-stu-id="9a466-198">SIMPLE</span></span>|<span data-ttu-id="9a466-199">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-199">Yes</span></span>|  
|<span data-ttu-id="9a466-200">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="9a466-200">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="9a466-201">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-201">OFF</span></span>|<span data-ttu-id="9a466-202">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-202">Yes</span></span>|  
|<span data-ttu-id="9a466-203">READ_COMMITTED_SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="9a466-203">READ_COMMITTED_SNAPSHOT</span></span>|<span data-ttu-id="9a466-204">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-204">OFF</span></span>|<span data-ttu-id="9a466-205">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-205">No</span></span>|  
|<span data-ttu-id="9a466-206">RECOVERY</span><span class="sxs-lookup"><span data-stu-id="9a466-206">RECOVERY</span></span>|<span data-ttu-id="9a466-207">SIMPLE</span><span class="sxs-lookup"><span data-stu-id="9a466-207">SIMPLE</span></span>|<span data-ttu-id="9a466-208">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-208">Yes</span></span>|  
|<span data-ttu-id="9a466-209">RECURSIVE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="9a466-209">RECURSIVE_TRIGGERS</span></span>|<span data-ttu-id="9a466-210">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-210">OFF</span></span>|<span data-ttu-id="9a466-211">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-211">Yes</span></span>|  
|<span data-ttu-id="9a466-212">Service Broker のオプション</span><span class="sxs-lookup"><span data-stu-id="9a466-212">Service Broker Options</span></span>|<span data-ttu-id="9a466-213">DISABLE_BROKER</span><span class="sxs-lookup"><span data-stu-id="9a466-213">DISABLE_BROKER</span></span>|<span data-ttu-id="9a466-214">いいえ</span><span class="sxs-lookup"><span data-stu-id="9a466-214">No</span></span>|  
|<span data-ttu-id="9a466-215">TRUSTWORTHY</span><span class="sxs-lookup"><span data-stu-id="9a466-215">TRUSTWORTHY</span></span>|<span data-ttu-id="9a466-216">OFF</span><span class="sxs-lookup"><span data-stu-id="9a466-216">OFF</span></span>|<span data-ttu-id="9a466-217">はい</span><span class="sxs-lookup"><span data-stu-id="9a466-217">Yes</span></span>|  
  
 <span data-ttu-id="9a466-218">これらのデータベース オプションの説明は、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a466-218">For a description of these database options, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="9a466-219">制限</span><span class="sxs-lookup"><span data-stu-id="9a466-219">Restrictions</span></span>  
 <span data-ttu-id="9a466-220">**master** データベースでは、次の操作は実行できません。</span><span class="sxs-lookup"><span data-stu-id="9a466-220">The following operations cannot be performed on the **master** database:</span></span>  
  
-   <span data-ttu-id="9a466-221">ファイルまたはファイル グループの追加。</span><span class="sxs-lookup"><span data-stu-id="9a466-221">Adding files or filegroups.</span></span>  
  
-   <span data-ttu-id="9a466-222">照合順序の変更。</span><span class="sxs-lookup"><span data-stu-id="9a466-222">Changing collation.</span></span> <span data-ttu-id="9a466-223">既定の照合順序はサーバーの照合順序です。</span><span class="sxs-lookup"><span data-stu-id="9a466-223">The default collation is the server collation.</span></span>  
  
-   <span data-ttu-id="9a466-224">データベース所有者の変更。</span><span class="sxs-lookup"><span data-stu-id="9a466-224">Changing the database owner.</span></span> <span data-ttu-id="9a466-225">**master** は **sa**が所有します。</span><span class="sxs-lookup"><span data-stu-id="9a466-225">**master** is owned by **sa**.</span></span>  
  
-   <span data-ttu-id="9a466-226">フルテキスト カタログまたはフルテキスト インデックスの作成。</span><span class="sxs-lookup"><span data-stu-id="9a466-226">Creating a full-text catalog or full-text index.</span></span>  
  
-   <span data-ttu-id="9a466-227">データベース内のシステム テーブルのトリガーの作成。</span><span class="sxs-lookup"><span data-stu-id="9a466-227">Creating triggers on system tables in the database.</span></span>  
  
-   <span data-ttu-id="9a466-228">データベースの削除。</span><span class="sxs-lookup"><span data-stu-id="9a466-228">Dropping the database.</span></span>  
  
-   <span data-ttu-id="9a466-229">データベースから**guest**ユーザーを削除しています。</span><span class="sxs-lookup"><span data-stu-id="9a466-229">Dropping the **guest** user from the database.</span></span>  
  
-   <span data-ttu-id="9a466-230">変更データ キャプチャの有効化。</span><span class="sxs-lookup"><span data-stu-id="9a466-230">Enabling change data capture.</span></span>  
  
-   <span data-ttu-id="9a466-231">データベース ミラーリングへの参加。</span><span class="sxs-lookup"><span data-stu-id="9a466-231">Participating in database mirroring.</span></span>  
  
-   <span data-ttu-id="9a466-232">プライマリ ファイル グループ、プライマリ データ ファイル、またはログ ファイルの削除。</span><span class="sxs-lookup"><span data-stu-id="9a466-232">Removing the primary filegroup, primary data file, or log file.</span></span>  
  
-   <span data-ttu-id="9a466-233">データベース名またはプライマリ ファイル グループ名の変更。</span><span class="sxs-lookup"><span data-stu-id="9a466-233">Renaming the database or primary filegroup.</span></span>  
  
-   <span data-ttu-id="9a466-234">データベースの OFFLINE への設定。</span><span class="sxs-lookup"><span data-stu-id="9a466-234">Setting the database to OFFLINE.</span></span>  
  
-   <span data-ttu-id="9a466-235">データベースまたはプライマリ ファイル グループの READ_ONLY への設定。</span><span class="sxs-lookup"><span data-stu-id="9a466-235">Setting the database or primary filegroup to READ_ONLY.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="9a466-236">Recommendations</span><span class="sxs-lookup"><span data-stu-id="9a466-236">Recommendations</span></span>  
 <span data-ttu-id="9a466-237">**master** データベースで作業を行っているときは、次の推奨設定を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="9a466-237">When you work with the **master** database, consider the following recommendations:</span></span>  
  
-   <span data-ttu-id="9a466-238">**master** データベースの現在のバックアップを、常に使用可能にする。</span><span class="sxs-lookup"><span data-stu-id="9a466-238">Always have a current backup of the **master** database available.</span></span>  
  
-   <span data-ttu-id="9a466-239">次の操作後には、できるだけ早く **master** データベースのバックアップを作成する。</span><span class="sxs-lookup"><span data-stu-id="9a466-239">Back up the **master** database as soon as possible after the following operations:</span></span>  
  
    -   <span data-ttu-id="9a466-240">データベースの作成、変更、または削除</span><span class="sxs-lookup"><span data-stu-id="9a466-240">Creating, modifying, or dropping any database</span></span>  
  
    -   <span data-ttu-id="9a466-241">サーバーまたはデータベースの構成値の変更</span><span class="sxs-lookup"><span data-stu-id="9a466-241">Changing server or database configuration values</span></span>  
  
    -   <span data-ttu-id="9a466-242">ログオン アカウントの変更または追加</span><span class="sxs-lookup"><span data-stu-id="9a466-242">Modifying or adding logon accounts</span></span>  
  
-   <span data-ttu-id="9a466-243">**master**にはユーザー オブジェクトを作成しない。</span><span class="sxs-lookup"><span data-stu-id="9a466-243">Do not create user objects in **master**.</span></span> <span data-ttu-id="9a466-244">ユーザー オブジェクトを作成すると、 **master** をより頻繁にバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a466-244">If you do, **master** must be backed up more frequently.</span></span>  
  
-   <span data-ttu-id="9a466-245">**master** データベースでは TRUSTWORTHY オプションを ON に設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="9a466-245">Do not set the TRUSTWORTHY option to ON for the **master** database.</span></span>  
  
## <a name="what-to-do-if-master-becomes-unusable"></a><span data-ttu-id="9a466-246">master が使用できない状態になった場合の対処方法</span><span class="sxs-lookup"><span data-stu-id="9a466-246">What to Do If master Becomes Unusable</span></span>  
 <span data-ttu-id="9a466-247">**master** が使用できない状態になった場合、このデータベースを次のいずれかの方法で使用できる状態に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="9a466-247">If **master** becomes unusable, you can return the database to a usable state in either of the following ways:</span></span>  
  
-   <span data-ttu-id="9a466-248">現在のデータベース バックアップから **master** を復元します。</span><span class="sxs-lookup"><span data-stu-id="9a466-248">Restore **master** from a current database backup.</span></span>  
  
     <span data-ttu-id="9a466-249">サーバー インスタンスを起動できる場合は、データベースの完全バックアップから **master** を復元できます。</span><span class="sxs-lookup"><span data-stu-id="9a466-249">If you can start the server instance, you should be able to restore **master** from a full database backup.</span></span> <span data-ttu-id="9a466-250">詳細については、「[master データベースの復元 &#40;Transact-SQL&#41;](../backup-restore/restore-the-master-database-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a466-250">For more information, see [Restore the master Database &#40;Transact-SQL&#41;](../backup-restore/restore-the-master-database-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="9a466-251">**master** を完全に再構築します。</span><span class="sxs-lookup"><span data-stu-id="9a466-251">Rebuild **master** completely.</span></span>  
  
     <span data-ttu-id="9a466-252">**master** に深刻な破損があり、それが原因で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を起動できない場合、 **master**を再構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a466-252">If severe damage to **master** prevents you from starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must rebuild **master**.</span></span> <span data-ttu-id="9a466-253">詳細については、「 [システム データベースの再構築](rebuild-system-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a466-253">For more information, see [Rebuild System Databases](rebuild-system-databases.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9a466-254">**master** を再構築すると、すべてのシステム データベースが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="9a466-254">Rebuilding **master** rebuilds all of the system databases.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="9a466-255">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="9a466-255">Related Content</span></span>  
 [<span data-ttu-id="9a466-256">システム データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="9a466-256">Rebuild System Databases</span></span>](rebuild-system-databases.md)  
  
 [<span data-ttu-id="9a466-257">システム データベース</span><span class="sxs-lookup"><span data-stu-id="9a466-257">System Databases</span></span>](system-databases.md)  
  
 [<span data-ttu-id="9a466-258">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9a466-258">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [<span data-ttu-id="9a466-259">sys.master_files &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9a466-259">sys.master_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [<span data-ttu-id="9a466-260">データベース ファイルの移動</span><span class="sxs-lookup"><span data-stu-id="9a466-260">Move Database Files</span></span>](move-database-files.md)  
  
  
