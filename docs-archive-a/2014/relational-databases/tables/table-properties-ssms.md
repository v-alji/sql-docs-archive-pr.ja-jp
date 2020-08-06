---
title: テーブルのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.tableproperties.storage.f1
- sql12.SWB.SELECTCOLUMNS.F1
- sql12.swb.tableproperties.filetable.f1
- sql12.swb.tableproperties.general.f1
- sql12.swb.tableproperties.changetracking.f1
ms.assetid: ad8a2fd4-f092-4c0f-be85-54ce8b9d725a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 037e56649d3473e3fe09b9533bcc96b4729870d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641530"
---
# <a name="table-properties"></a><span data-ttu-id="38212-102">テーブルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="38212-102">Table Properties</span></span>
  <span data-ttu-id="38212-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の [テーブルのプロパティ] ダイアログ ボックスに表示されるテーブルのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="38212-103">This topic describes the table properties that are displayed in the Table Properties dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="38212-104">これらのプロパティの表示方法の詳細については、「 [テーブル定義の表示](view-the-table-definition.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38212-104">For more information about how to display these properties, see [View the Table Definition](view-the-table-definition.md).</span></span>  
  
 <span data-ttu-id="38212-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="38212-105">**In This Topic**</span></span>  
  
1.  <span data-ttu-id="38212-106">[[全般] ページ](#GeneralPage)</span><span class="sxs-lookup"><span data-stu-id="38212-106">[General Page](#GeneralPage)</span></span>  
  
2.  <span data-ttu-id="38212-107">[[変更の追跡] ページ](#ChangeTracking)</span><span class="sxs-lookup"><span data-stu-id="38212-107">[Change Tracking Page](#ChangeTracking)</span></span>  
  
3.  <span data-ttu-id="38212-108">[[FileTable] ページ](#FileTable)</span><span class="sxs-lookup"><span data-stu-id="38212-108">[File Table Page](#FileTable)</span></span>  
  
4.  <span data-ttu-id="38212-109">[[ストレージ] ページ](#Storage)</span><span class="sxs-lookup"><span data-stu-id="38212-109">[Storage Page](#Storage)</span></span>  
  
##  <a name="general-page"></a><a name="GeneralPage"></a> <span data-ttu-id="38212-110">[全般] ページ</span><span class="sxs-lookup"><span data-stu-id="38212-110">General Page</span></span>  
 <span data-ttu-id="38212-111">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="38212-111">**Database**</span></span>  
 <span data-ttu-id="38212-112">このテーブルを含むデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="38212-112">The name of the database containing this table.</span></span>  
  
 <span data-ttu-id="38212-113">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="38212-113">**Server**</span></span>  
 <span data-ttu-id="38212-114">現在のサーバー インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="38212-114">The name of the current server instance.</span></span>  
  
 <span data-ttu-id="38212-115">**User**</span><span class="sxs-lookup"><span data-stu-id="38212-115">**User**</span></span>  
 <span data-ttu-id="38212-116">この接続のユーザーの名前です。</span><span class="sxs-lookup"><span data-stu-id="38212-116">The name of the user of this connection.</span></span>  
  
 <span data-ttu-id="38212-117">**[作成日]**</span><span class="sxs-lookup"><span data-stu-id="38212-117">**Created Date**</span></span>  
 <span data-ttu-id="38212-118">テーブルが作成された日付と時刻です。</span><span class="sxs-lookup"><span data-stu-id="38212-118">The date and time that the table was created.</span></span>  
  
 <span data-ttu-id="38212-119">**Name**</span><span class="sxs-lookup"><span data-stu-id="38212-119">**Name**</span></span>  
 <span data-ttu-id="38212-120">テーブルの名前。</span><span class="sxs-lookup"><span data-stu-id="38212-120">The name of the table.</span></span>  
  
 <span data-ttu-id="38212-121">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="38212-121">**Schema**</span></span>  
 <span data-ttu-id="38212-122">テーブルを所有するスキーマです。</span><span class="sxs-lookup"><span data-stu-id="38212-122">The schema that owns the table.</span></span>  
  
 <span data-ttu-id="38212-123">**[システム オブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="38212-123">**System object**</span></span>  
 <span data-ttu-id="38212-124">このテーブルが、内部情報を格納するために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用されるシステム テーブルであることを示します。</span><span class="sxs-lookup"><span data-stu-id="38212-124">Indicates this table is a system table, used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to contain internal information.</span></span> <span data-ttu-id="38212-125">システム テーブルを直接変更したり参照したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="38212-125">Users should not directly change or reference system tables.</span></span>  
  
 <span data-ttu-id="38212-126">**[ANSI NULL]**</span><span class="sxs-lookup"><span data-stu-id="38212-126">**ANSI NULLs**</span></span>  
 <span data-ttu-id="38212-127">オブジェクトが、ANSI NULL オプションが ON に設定されて作成されたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="38212-127">Indicates if the object was created with the ANSI NULLs option set to ON.</span></span> <span data-ttu-id="38212-128">詳細については、「[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38212-128">For more information, see [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)</span></span>  
  
 <span data-ttu-id="38212-129">**[引用符で囲まれた識別子]**</span><span class="sxs-lookup"><span data-stu-id="38212-129">**Quoted identifier**</span></span>  
 <span data-ttu-id="38212-130">オブジェクトが、引用符で囲まれた識別子オプションが ON に設定されて作成されたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="38212-130">Indicates if the object was created with the quoted identifier option set to ON.</span></span> <span data-ttu-id="38212-131">詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38212-131">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)</span></span>  
  
 <span data-ttu-id="38212-132">**[ロックのエスカレーション]**</span><span class="sxs-lookup"><span data-stu-id="38212-132">**Lock Escalation**</span></span>  
 <span data-ttu-id="38212-133">テーブルのロック エスカレーションの粒度を示します。</span><span class="sxs-lookup"><span data-stu-id="38212-133">Indicates the lock escalation granularity of the table.</span></span> <span data-ttu-id="38212-134">データベース エンジンのロックの詳細については、「 [SQL Server トランザクションのロックおよび行のバージョン管理ガイド](https://msdn.microsoft.com/library/jj856598.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38212-134">For more information about locking in the Database Engine, see [SQL Server Transaction Locking and Row Versioning Guide](https://msdn.microsoft.com/library/jj856598.aspx).</span></span> <span data-ttu-id="38212-135">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="38212-135">Possible values are:</span></span>  
  
 <span data-ttu-id="38212-136">AUTO</span><span class="sxs-lookup"><span data-stu-id="38212-136">AUTO</span></span>  
 <span data-ttu-id="38212-137">このオプションを使用すると、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] は、テーブル スキーマに適したロック エスカレーションの粒度を選択します。</span><span class="sxs-lookup"><span data-stu-id="38212-137">This option allows the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to select the lock escalation granularity that is appropriate for the table schema.</span></span>  
  
-   <span data-ttu-id="38212-138">テーブルがパーティション分割されている場合は、ロック エスカレーションをヒープまたは B ツリー (HoBT) 粒度に設定できます。</span><span class="sxs-lookup"><span data-stu-id="38212-138">If the table is partitioned, lock escalation will be allowed to the heap or B-tree (HoBT) granularity.</span></span> <span data-ttu-id="38212-139">ロックは HoBT レベルにエスカレートされると、後で TABLE 粒度にエスカレートされません。</span><span class="sxs-lookup"><span data-stu-id="38212-139">After the lock is escalated to the HoBT level, the lock will not be escalated later to TABLE granularity.</span></span>  
  
-   <span data-ttu-id="38212-140">テーブルがパーティション分割されていない場合は、ロック エスカレーションは TABLE 粒度に設定されます。</span><span class="sxs-lookup"><span data-stu-id="38212-140">If the table is not partitioned, the lock escalation will be done to the TABLE granularity.</span></span>  
  
 <span data-ttu-id="38212-141">TABLE</span><span class="sxs-lookup"><span data-stu-id="38212-141">TABLE</span></span>  
 <span data-ttu-id="38212-142">テーブルがパーティション分割されているかどうかに関係なく、ロック エスカレーションはテーブルレベルの粒度で行われます。</span><span class="sxs-lookup"><span data-stu-id="38212-142">Lock escalation will be done at table-level granularity regardless of whether the table is partitioned or not partitioned.</span></span> <span data-ttu-id="38212-143">TABLE は既定値です。</span><span class="sxs-lookup"><span data-stu-id="38212-143">TABLE is the default value.</span></span>  
  
 <span data-ttu-id="38212-144">DISABLE</span><span class="sxs-lookup"><span data-stu-id="38212-144">DISABLE</span></span>  
 <span data-ttu-id="38212-145">ほとんどの場合でロック エスカレーションを禁止します。</span><span class="sxs-lookup"><span data-stu-id="38212-145">Prevents lock escalation in most cases.</span></span> <span data-ttu-id="38212-146">テーブルレベルのロックは完全には禁止されません。</span><span class="sxs-lookup"><span data-stu-id="38212-146">Table-level locks are not completely disallowed.</span></span> <span data-ttu-id="38212-147">たとえば、SERIALIZABLE 分離レベルでクラスター化インデックスがないテーブルをスキャンしている場合は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] でテーブル ロックを実行して、データの整合性を保護します。</span><span class="sxs-lookup"><span data-stu-id="38212-147">For example, when you are scanning a table that has no clustered index under the serializable isolation level, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must take a table lock to protect data integrity.</span></span>  
  
 <span data-ttu-id="38212-148">**[レプリケートされるテーブル]**</span><span class="sxs-lookup"><span data-stu-id="38212-148">**Table is replicated**</span></span>  
 <span data-ttu-id="38212-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションによってテーブルがいつ別のデータベースにレプリケートされるかを示します。</span><span class="sxs-lookup"><span data-stu-id="38212-149">Indicates when the table is replicated to another database using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="38212-150">指定できる値は `True` または `False` です。</span><span class="sxs-lookup"><span data-stu-id="38212-150">Possible values are `True` or `False`.</span></span>  
  
##  <a name="change-tracking-page"></a><a name="ChangeTracking"></a><span data-ttu-id="38212-151">Change Tracking ページ</span><span class="sxs-lookup"><span data-stu-id="38212-151">Change Tracking Page</span></span>  
 <span data-ttu-id="38212-152">**変更の追跡**</span><span class="sxs-lookup"><span data-stu-id="38212-152">**Change Tracking**</span></span>  
 <span data-ttu-id="38212-153">テーブルに対する変更の追跡が有効かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="38212-153">Indicates whether change tracking is enabled for the table.</span></span> <span data-ttu-id="38212-154">既定値は `False` です。</span><span class="sxs-lookup"><span data-stu-id="38212-154">The default value is `False`.</span></span>  
  
 <span data-ttu-id="38212-155">このオプションは、データベースに対して変更の追跡が有効になっている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="38212-155">This option is available only when change tracking is enabled for the database.</span></span>  
  
 <span data-ttu-id="38212-156">変更の追跡を有効にするには、テーブルに主キーが必要です。また、テーブルを変更する権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="38212-156">To enable change tracking, the table must have a primary key, and you must have permission to modify the table.</span></span> <span data-ttu-id="38212-157">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)を使用して変更の追跡を構成できます。</span><span class="sxs-lookup"><span data-stu-id="38212-157">You can configure change tracking by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="38212-158">**[更新された追跡列]**</span><span class="sxs-lookup"><span data-stu-id="38212-158">**Track Columns Updated**</span></span>  
 <span data-ttu-id="38212-159">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] が更新された列を追跡するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="38212-159">Indicates whether the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] tracks which columns were updated.</span></span>  
  
 <span data-ttu-id="38212-160">変更の追跡の詳細については、「[変更の追跡について &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38212-160">For more information about Change Tracking, see [About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).</span></span>  
  
##  <a name="filetable-page"></a><a name="FileTable"></a><span data-ttu-id="38212-161">[FileTable] ページ</span><span class="sxs-lookup"><span data-stu-id="38212-161">FileTable Page</span></span>  
 <span data-ttu-id="38212-162">FileTable に関連するテーブルのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="38212-162">Displays properties of the table related to FileTables.</span></span> <span data-ttu-id="38212-163">詳細については、「[FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38212-163">For more information, see [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).</span></span>  
  
 <span data-ttu-id="38212-164">**[FileTable の名前列の照合順序]**</span><span class="sxs-lookup"><span data-stu-id="38212-164">**FileTable name column collation**</span></span>  
 <span data-ttu-id="38212-165">FileTable の **Name** 列に適用される照合順序。</span><span class="sxs-lookup"><span data-stu-id="38212-165">The collation that is applied to the **Name** column in a FileTable.</span></span> <span data-ttu-id="38212-166">**Name** 列には、ファイルとディレクトリの名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="38212-166">The **Name** column contains file and directory names.</span></span>  
  
 <span data-ttu-id="38212-167">**[FileTable のディレクトリ名]**</span><span class="sxs-lookup"><span data-stu-id="38212-167">**FileTable directory name**</span></span>  
 <span data-ttu-id="38212-168">FileTable のルート フォルダー。</span><span class="sxs-lookup"><span data-stu-id="38212-168">The root folder for the FileTable.</span></span>  
  
 <span data-ttu-id="38212-169">**FileTable の名前空間の有効化**</span><span class="sxs-lookup"><span data-stu-id="38212-169">**FileTable namespace enabled**</span></span>  
 <span data-ttu-id="38212-170">`True` の場合、この値はテーブルが FileTable であることを示します。</span><span class="sxs-lookup"><span data-stu-id="38212-170">When `True`, this value indicates that the table is a FileTable.</span></span> <span data-ttu-id="38212-171">この値を `False` に変更すると、FileTable が通常のユーザー テーブルに変更されます。</span><span class="sxs-lookup"><span data-stu-id="38212-171">If you change this value to `False`, you are changing the FileTable to an ordinary user table.</span></span> <span data-ttu-id="38212-172">後でテーブルを FileTable に戻す場合は、変換時に FileTable 一貫性チェックを行い、テーブルに問題がないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38212-172">If you later want to change the table back to a FileTable, the table will have to pass a FileTable consistency check before the conversion succeeds.</span></span>  
  
##  <a name="storage-page"></a><a name="Storage"></a> <span data-ttu-id="38212-173">[ストレージ] ページ</span><span class="sxs-lookup"><span data-stu-id="38212-173">Storage Page</span></span>  
 <span data-ttu-id="38212-174">選択されているテーブルのストレージに関連するプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="38212-174">Displays the storage related properties of the selected table.</span></span>  
  
### <a name="compression"></a><span data-ttu-id="38212-175">圧縮</span><span class="sxs-lookup"><span data-stu-id="38212-175">Compression</span></span>  
 <span data-ttu-id="38212-176">**[圧縮の種類]**</span><span class="sxs-lookup"><span data-stu-id="38212-176">**Compression type**</span></span>  
 <span data-ttu-id="38212-177">テーブルの圧縮の種類。</span><span class="sxs-lookup"><span data-stu-id="38212-177">The compression type of the table.</span></span> <span data-ttu-id="38212-178">このプロパティは、パーティション分割されていないテーブルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="38212-178">This property is only available for tables that are not partitioned.</span></span> <span data-ttu-id="38212-179">詳細については、「 [Data Compression](../data-compression/data-compression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38212-179">For more information, see [Data Compression](../data-compression/data-compression.md).</span></span>  
  
 <span data-ttu-id="38212-180">**[ページの圧縮を使用したパーティション]**</span><span class="sxs-lookup"><span data-stu-id="38212-180">**Partitions using page compression**</span></span>  
 <span data-ttu-id="38212-181">ページの圧縮を使用しているパーティション番号。</span><span class="sxs-lookup"><span data-stu-id="38212-181">The partition numbers that are using page compression.</span></span> <span data-ttu-id="38212-182">このプロパティは、パーティション分割されているテーブルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="38212-182">This property is only available for partitioned tables.</span></span>  
  
 <span data-ttu-id="38212-183">**[圧縮されていないパーティション]**</span><span class="sxs-lookup"><span data-stu-id="38212-183">**Partitions not compressed**</span></span>  
 <span data-ttu-id="38212-184">圧縮されていないパーティション番号。</span><span class="sxs-lookup"><span data-stu-id="38212-184">The partition numbers that are not compressed.</span></span> <span data-ttu-id="38212-185">このプロパティは、パーティション分割されているテーブルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="38212-185">This property is only available for partitioned tables.</span></span>  
  
 <span data-ttu-id="38212-186">**[行の圧縮を使用したパーティション]**</span><span class="sxs-lookup"><span data-stu-id="38212-186">**Partitions using row compression**</span></span>  
 <span data-ttu-id="38212-187">行の圧縮を使用しているパーティション番号。</span><span class="sxs-lookup"><span data-stu-id="38212-187">The partition numbers that are using row compression.</span></span> <span data-ttu-id="38212-188">このプロパティは、パーティション分割されているテーブルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="38212-188">This property is only available for partitioned tables.</span></span>  
  
### <a name="filegroup"></a><span data-ttu-id="38212-189">[ファイル グループ]</span><span class="sxs-lookup"><span data-stu-id="38212-189">Filegroup</span></span>  
 <span data-ttu-id="38212-190">**[テキスト ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="38212-190">**Text filegroup**</span></span>  
 <span data-ttu-id="38212-191">テーブルのテキスト データを含むファイル グループの名前です。</span><span class="sxs-lookup"><span data-stu-id="38212-191">The name of the filegroup that contains the text data for the table.</span></span>  
  
 <span data-ttu-id="38212-192">**[ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="38212-192">**Filegroup**</span></span>  
 <span data-ttu-id="38212-193">このテーブルを含むファイル グループの名前。</span><span class="sxs-lookup"><span data-stu-id="38212-193">The name of the filegroup that contains the table.</span></span>  
  
 <span data-ttu-id="38212-194">**[パーティション分割されるテーブル]**</span><span class="sxs-lookup"><span data-stu-id="38212-194">**Table is partitioned**</span></span>  
 <span data-ttu-id="38212-195">設定可能な値は `True` および `False` です。</span><span class="sxs-lookup"><span data-stu-id="38212-195">Possible values are `True` and `False`.</span></span>  
  
 <span data-ttu-id="38212-196">**[Filestream ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="38212-196">**Filestream filegroup**</span></span>  
 <span data-ttu-id="38212-197">テーブルが FILESTREAM 属性がある `varbinary(max)` 列を持つ場合は、FILESTREAM データ ファイル グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="38212-197">Specify the name of the FILESTREAM data filegroup if the table has a `varbinary(max)` column that has the FILESTREAM attribute.</span></span> <span data-ttu-id="38212-198">既定値は、既定の FILESTREAM データ ファイル グループです。</span><span class="sxs-lookup"><span data-stu-id="38212-198">The default value is the default FILESTREAM data filegroup.</span></span>  
  
 <span data-ttu-id="38212-199">テーブルに FILESTREAM データが含まれていない場合、フィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="38212-199">If the table does not contain FILESTREAM data, the field is blank.</span></span>  
  
### <a name="general"></a><span data-ttu-id="38212-200">全般</span><span class="sxs-lookup"><span data-stu-id="38212-200">General</span></span>  
 <span data-ttu-id="38212-201">**[VarDecimal ストレージ形式が有効]**</span><span class="sxs-lookup"><span data-stu-id="38212-201">**Vardecimal storage format is enabled**</span></span>  
 <span data-ttu-id="38212-202">`True`の場合、この読み取り専用の値 `decimal` は、および `numeric` データ型が vardecimal ストレージ形式を使用して格納されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="38212-202">When `True`, this read-only value indicates that `decimal` and `numeric` data types are stored by using the vardecimal storage format.</span></span> <span data-ttu-id="38212-203">このオプションを変更するには、 `vardecimal storage format` [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="38212-203">To change this option, use the `vardecimal storage format` option of [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql).</span></span> <span data-ttu-id="38212-204">Vardecimal ストレージ形式は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="38212-204">Vardecimal storage format is deprecated.</span></span> <span data-ttu-id="38212-205">代わりに行の圧縮を使用してください。</span><span class="sxs-lookup"><span data-stu-id="38212-205">Use ROW compression instead.</span></span>  
  
 <span data-ttu-id="38212-206">**[インデックス領域]**</span><span class="sxs-lookup"><span data-stu-id="38212-206">**Index space**</span></span>  
 <span data-ttu-id="38212-207">インデックスがテーブル内で占有する領域の容量をメガバイト単位で表示します。</span><span class="sxs-lookup"><span data-stu-id="38212-207">The amount of space in megabytes that the indexes occupy in the table.</span></span> <span data-ttu-id="38212-208">この値には、テーブルの XML インデックスの領域使用状況は含まれません。</span><span class="sxs-lookup"><span data-stu-id="38212-208">This value does not include XML index space usage for the table.</span></span> <span data-ttu-id="38212-209">テーブルに XML インデックスが含まれている場合は、代わりに [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="38212-209">If XML indexes belong to the table, use [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="38212-210">**行数**</span><span class="sxs-lookup"><span data-stu-id="38212-210">**Row count**</span></span>  
 <span data-ttu-id="38212-211">表の行数。</span><span class="sxs-lookup"><span data-stu-id="38212-211">The number of rows in the table.</span></span>  
  
 <span data-ttu-id="38212-212">**[データ領域]**</span><span class="sxs-lookup"><span data-stu-id="38212-212">**Data space**</span></span>  
 <span data-ttu-id="38212-213">データがテーブル内で占有する領域の容量をメガバイト単位で表示します。</span><span class="sxs-lookup"><span data-stu-id="38212-213">The amount of space in megabytes that the data occupies in the table.</span></span>  
  
### <a name="partitioning"></a><span data-ttu-id="38212-214">パーティション分割</span><span class="sxs-lookup"><span data-stu-id="38212-214">Partitioning</span></span>  
 <span data-ttu-id="38212-215">このセクションは、テーブルがパーティション分割されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="38212-215">This section is only available if the table is partitioned.</span></span> <span data-ttu-id="38212-216">詳細については、「 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38212-216">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="38212-217">**[パーティション列]**</span><span class="sxs-lookup"><span data-stu-id="38212-217">**Partition column**</span></span>  
 <span data-ttu-id="38212-218">テーブルがパーティション分割される列の名前。</span><span class="sxs-lookup"><span data-stu-id="38212-218">The name of the column on which the table is partitioned.</span></span>  
  
 <span data-ttu-id="38212-219">**[パーティション構成]**</span><span class="sxs-lookup"><span data-stu-id="38212-219">**Partition scheme**</span></span>  
 <span data-ttu-id="38212-220">テーブルがパーティション分割されている場合のパーティション構成の名前。</span><span class="sxs-lookup"><span data-stu-id="38212-220">Name of the partition scheme if the table is partitioned.</span></span> <span data-ttu-id="38212-221">テーブルがパーティション分割されていない場合、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="38212-221">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="38212-222">**パーティションの数**</span><span class="sxs-lookup"><span data-stu-id="38212-222">**Number of partitions**</span></span>  
 <span data-ttu-id="38212-223">テーブルのパーティション数です。</span><span class="sxs-lookup"><span data-stu-id="38212-223">The number of partitions in the table.</span></span>  
  
 <span data-ttu-id="38212-224">**FILESTREAM パーティション構成**</span><span class="sxs-lookup"><span data-stu-id="38212-224">**FILESTREAM partition scheme**</span></span>  
 <span data-ttu-id="38212-225">テーブルがパーティション分割されている場合の FILESTREAM パーティション構成の名前。</span><span class="sxs-lookup"><span data-stu-id="38212-225">The name of the FILESTREAM partition scheme if the table is partitioned.</span></span> <span data-ttu-id="38212-226">テーブルがパーティション分割されていない場合、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="38212-226">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="38212-227">FILESTREAM パーティション構成は、 **[パーティション構成]** オプションで指定した構成と対称である必要があります。</span><span class="sxs-lookup"><span data-stu-id="38212-227">The FILESTREAM partition scheme must be symmetric to the scheme that is specified in the **Partition scheme** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38212-228">参照</span><span class="sxs-lookup"><span data-stu-id="38212-228">See Also</span></span>  
 <span data-ttu-id="38212-229">[テーブル定義を表示する](view-the-table-definition.md) </span><span class="sxs-lookup"><span data-stu-id="38212-229">[View the Table Definition](view-the-table-definition.md) </span></span>  
 [<span data-ttu-id="38212-230">列の変更 &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="38212-230">Modify Columns &#40;Database Engine&#41;</span></span>](../tables/modify-columns-database-engine.md)  
  
  
