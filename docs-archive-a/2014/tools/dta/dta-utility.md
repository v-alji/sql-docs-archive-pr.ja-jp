---
title: dta ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- physical design structures [SQL Server]
- command prompt utilities [SQL Server], dta
- dta utility
- tuning databases [SQL Server], Database Engine Tuning Advisor
- workloads [SQL Server], analyzing
- dta utility, about dta utility
- performance [SQL Server], Database Engine Tuning Advisor
- Database Engine Tuning Advisor [SQL Server], command prompt
- optimizing databases [SQL Server]
ms.assetid: a0b210ce-9b58-4709-80cb-9363b68a1f5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: f9cd5a904993f1044c1cbeff8e1cdfc07332da64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740614"
---
# <a name="dta-utility"></a><span data-ttu-id="715f6-102">dta ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="715f6-102">dta Utility</span></span>
  <span data-ttu-id="715f6-103">**dta** ユーティリティは、データベース エンジン チューニング アドバイザーのコマンド プロンプト バージョンです。</span><span class="sxs-lookup"><span data-stu-id="715f6-103">The **dta** utility is the command prompt version of Database Engine Tuning Advisor.</span></span> <span data-ttu-id="715f6-104">**dta** ユーティリティは、データベース エンジン チューニング アドバイザーの機能をアプリケーションとスクリプトで使用するために作成されました。</span><span class="sxs-lookup"><span data-stu-id="715f6-104">The **dta** utility is designed to allow you to use Database Engine Tuning Advisor functionality in applications and scripts.</span></span>  
  
 <span data-ttu-id="715f6-105">データベース エンジン チューニング アドバイザーと同様、 **dta** ユーティリティは、ワークロードを分析し、そのワークロードに対するサーバー パフォーマンスを向上するために推奨される物理デザイン構造を提示します。</span><span class="sxs-lookup"><span data-stu-id="715f6-105">Like Database Engine Tuning Advisor, the **dta** utility analyzes a workload and recommends physical design structures to improve server performance for that workload.</span></span> <span data-ttu-id="715f6-106">ワークロードには、プラン キャッシュ、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のトレース ファイルやトレース テーブル、または [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="715f6-106">The workload can be a plan cache, a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace file or table, or a [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="715f6-107">物理デザイン構造には、インデックス、インデックス付きビュー、およびパーティション分割が含まれます。</span><span class="sxs-lookup"><span data-stu-id="715f6-107">Physical design structures include indexes, indexed views, and partitioning.</span></span> <span data-ttu-id="715f6-108">ワークロードの分析後、 **dta** ユーティリティは、データベースの物理デザインに対する推奨設定を作成します。また、その推奨設定を実装するために必要なスクリプトを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="715f6-108">After analyzing a workload, the **dta** utility produces a recommendation for the physical design of databases and can generate the necessary script to implement the recommendation.</span></span> <span data-ttu-id="715f6-109">ワークロードは、 **-if** 引数または **-it** 引数を使用してコマンド プロンプトから指定できます。</span><span class="sxs-lookup"><span data-stu-id="715f6-109">Workloads can be specified from the command prompt with the **-if** or the **-it** argument.</span></span> <span data-ttu-id="715f6-110">**-ix** 引数を使用して、コマンド プロンプトから XML 入力ファイルを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="715f6-110">You can also specify an XML input file from the command prompt with the **-ix** argument.</span></span> <span data-ttu-id="715f6-111">その場合、ワークロードは XML 入力ファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-111">In that case, the workload is specified in the XML input file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="715f6-112">構文</span><span class="sxs-lookup"><span data-stu-id="715f6-112">Syntax</span></span>  
  
```  
  
      dta  
[ -? ] |  
[  
      [ -S server_name[ \instance ] ]  
      { { -U login_id [-P password ] } | -E  }  
      { -D database_name [ ,...n ] }  
      [ -ddatabase_name ]   
      [ -Tltable_list | -Tf table_list_file ]  
      { -if workload_file | -it workload_trace_table_name  |   
        -ip | -ipf }  
      { -ssession_name | -IDsession_ID }  
      [ -F ]  
      [ -of output_script_file_name ]  
      [ -oroutput_xml_report_file_name ]  
      [ -ox output_XML_file_name ]  
      [ -rl analysis_report_list [ ,...n ] ]  
      [ -ix input_XML_file_name ]  
      [ -A time_for_tuning_in_minutes ]  
      [ -nnumber_of_events ]  
      [ -m minimum_improvement ]  
      [ -fa physical_design_structures_to_add ]  
      [ -fi ]  
      [ -fppartitioning_strategy ]  
      [ -fk keep_existing_option ]  
      [ -fxdrop_only_mode ]  
      [ -B storage_size ]  
      [ -cmax_key_columns_in_index ]  
      [ -C max_columns_in_index ]  
      [ -e | -e tuning_log_name ]  
      [ -N online_option]  
      [ -q ]  
      [ -u ]  
      [ -x ]  
      [ -a ]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="715f6-113">引数</span><span class="sxs-lookup"><span data-stu-id="715f6-113">Arguments</span></span>  
 <span data-ttu-id="715f6-114">**-?**</span><span class="sxs-lookup"><span data-stu-id="715f6-114">**-?**</span></span>  
 <span data-ttu-id="715f6-115">使用方法に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="715f6-115">Displays usage information.</span></span>  
  
 <span data-ttu-id="715f6-116">**-A** _time_for_tuning_in_minutes_</span><span class="sxs-lookup"><span data-stu-id="715f6-116">**-A** _time_for_tuning_in_minutes_</span></span>  
 <span data-ttu-id="715f6-117">チューニングの制限時間を分単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-117">Specifies the tuning time limit in minutes.</span></span> <span data-ttu-id="715f6-118">**dta** は、指定された時間を使用してワークロードをチューニングし、推奨される物理デザインに変更するスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="715f6-118">**dta** uses the specified amount of time to tune the workload and generate a script with the recommended physical design changes.</span></span> <span data-ttu-id="715f6-119">既定では、 **dta** は、チューニング時間を 8 時間と想定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-119">By default **dta** assumes a tuning time of 8 hours.</span></span> <span data-ttu-id="715f6-120">0 を指定すると、チューニング時間を無制限になります。</span><span class="sxs-lookup"><span data-stu-id="715f6-120">Specifying 0allows unlimited tuning time.</span></span> <span data-ttu-id="715f6-121">**dta** では、制限時間に達する前にワークロード全体のチューニングを終了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-121">**dta** might finish tuning the entire workload before the time limit expires.</span></span> <span data-ttu-id="715f6-122">ワークロード全体を確実にチューニングするためには、チューニング時間を無制限に指定 (-A 0) することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="715f6-122">However, to make sure that the entire workload is tuned, we recommend that you specify unlimited tuning time (-A 0).</span></span>  
  
 <span data-ttu-id="715f6-123">**-a**</span><span class="sxs-lookup"><span data-stu-id="715f6-123">**-a**</span></span>  
 <span data-ttu-id="715f6-124">ワークロードをチューニングし、確認のプロンプトを表示せずに推奨設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="715f6-124">Tunes workload and applies the recommendation without prompting you.</span></span>  
  
 <span data-ttu-id="715f6-125">**-B** _storage_size_</span><span class="sxs-lookup"><span data-stu-id="715f6-125">**-B** _storage_size_</span></span>  
 <span data-ttu-id="715f6-126">推奨されるインデックスとパーティション分割で使用できる最大容量を MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-126">Specifies the maximum space in megabytes that can be consumed by the recommended index and partitioning.</span></span> <span data-ttu-id="715f6-127">複数のデータベースをチューニングする場合は、すべてのデータベースの推奨設定が容量計算の対象になります。</span><span class="sxs-lookup"><span data-stu-id="715f6-127">When multiple databases are tuned, recommendations for all databases are considered for the space calculation.</span></span> <span data-ttu-id="715f6-128">既定では、 **dta** は、次のストレージ サイズより小さいサイズを想定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-128">By default, **dta** assumes the smaller of the following storage sizes:</span></span>  
  
-   <span data-ttu-id="715f6-129">現在の生データ サイズの 3 倍。このサイズには、データベース内のテーブルのヒープとクラスター化インデックスの合計サイズが含まれます。</span><span class="sxs-lookup"><span data-stu-id="715f6-129">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables in the database.</span></span>  
  
-   <span data-ttu-id="715f6-130">アタッチ先のすべてのディスク ドライブの空き容量に生データのサイズを加算した値</span><span class="sxs-lookup"><span data-stu-id="715f6-130">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="715f6-131">既定の記憶領域サイズには、非クラスター化インデックスとインデックス付きビューは含まれません。</span><span class="sxs-lookup"><span data-stu-id="715f6-131">The default storage size does not include nonclustered indexes and indexed views.</span></span>  
  
 <span data-ttu-id="715f6-132">**-C** _max_columns_in_index_</span><span class="sxs-lookup"><span data-stu-id="715f6-132">**-C** _max_columns_in_index_</span></span>  
 <span data-ttu-id="715f6-133">**dta** が提示する、インデックス内に含まれる列の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-133">Specifies the maximum number of columns in indexes that **dta** proposes.</span></span> <span data-ttu-id="715f6-134">最大値は 1024 です。</span><span class="sxs-lookup"><span data-stu-id="715f6-134">The maximum value  is 1024.</span></span> <span data-ttu-id="715f6-135">既定では、この引数は 16 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="715f6-135">By default, this argument is set to 16.</span></span>  
  
 <span data-ttu-id="715f6-136">**-c** _max_key_columns_in_index_</span><span class="sxs-lookup"><span data-stu-id="715f6-136">**-c** _max_key_columns_in_index_</span></span>  
 <span data-ttu-id="715f6-137">**dta** が提示する、インデックス内に含まれるキー列の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-137">Specifies the maximum number of key columns in indexes that **dta** proposes.</span></span> <span data-ttu-id="715f6-138">既定値は 16 (許可される最大値) です。</span><span class="sxs-lookup"><span data-stu-id="715f6-138">The default value is 16, the maximum value allowed.</span></span> <span data-ttu-id="715f6-139">**dta** では、付加列を使用するインデックスの作成も考慮されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-139">**dta** also considers creating indexes with included columns.</span></span> <span data-ttu-id="715f6-140">付加列を使用するインデックス推奨設定は、この引数で指定される列数を超える場合があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-140">Indexes recommended with included columns may exceed the number of columns specified in this argument.</span></span>  
  
 <span data-ttu-id="715f6-141">**-D** _database_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-141">**-D** _database_name_</span></span>  
 <span data-ttu-id="715f6-142">チューニングする各データベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-142">Specifies the name of each database that is to be tuned.</span></span> <span data-ttu-id="715f6-143">最初のデータベースは既定のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="715f6-143">The first database is the default database.</span></span> <span data-ttu-id="715f6-144">データベース名をコンマで区切り、複数のデータベースを指定することができます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="715f6-144">You can specify multiple databases by separating the database names with commas, for example:</span></span>  
  
```  
dta -D database_name1, database_name2...  
```  
  
 <span data-ttu-id="715f6-145">または、各データベース名に対して **-D** 引数を使用することで、複数のデータベースを指定できます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="715f6-145">Alternatively, you can specify multiple databases by using the **-D** argument for each database name, for example:</span></span>  
  
```  
dta -D database_name1 -D database_name2... n  
```  
  
 <span data-ttu-id="715f6-146">**-D** 引数は必須です。</span><span class="sxs-lookup"><span data-stu-id="715f6-146">The **-D** argument is mandatory.</span></span> <span data-ttu-id="715f6-147">**-d** 引数が指定されていない場合、 **dta** は、ワークロードの最初の `USE database_name` 句で指定されるデータベースに最初に接続します。</span><span class="sxs-lookup"><span data-stu-id="715f6-147">If the **-d** argument has not been specified, **dta** initially connects to the database that is specified with the first `USE database_name` clause in the workload.</span></span> <span data-ttu-id="715f6-148">ワークロードに明示的な `USE database_name` 句がない場合、 **-d** 引数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-148">If there is not explicit `USE database_name` clause in the workload, you must use the **-d** argument.</span></span>  
  
 <span data-ttu-id="715f6-149">たとえば、明示的な `USE database_name` 句を含まないワークロードで、次のような **dta** コマンドを使用する場合、推奨設定は生成されません。</span><span class="sxs-lookup"><span data-stu-id="715f6-149">For example, if you have a workload that contains no explicit `USE database_name` clause, and you use the following **dta** command, a recommendation will not be generated:</span></span>  
  
```  
dta -D db_name1, db_name2...  
```  
  
 <span data-ttu-id="715f6-150">しかし、同じワークロードを使用して、 **-d** 引数を使用した次のような **dta** コマンドを使用すると、推奨設定が生成されます:</span><span class="sxs-lookup"><span data-stu-id="715f6-150">But if you use the same workload, and use the following **dta** command that uses the **-d** argument, a recommendation will be generated:</span></span>  
  
```  
dta -D db_name1, db_name2 -d db_name1  
```  
  
 <span data-ttu-id="715f6-151">**-d** _database_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-151">**-d** _database_name_</span></span>  
 <span data-ttu-id="715f6-152">ワークロードをチューニングするときに、 **dta** が最初に接続するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-152">Specifies the first database to which **dta** connects when tuning a workload.</span></span> <span data-ttu-id="715f6-153">この引数で指定できるデータベースは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="715f6-153">Only one database can be specified for this argument.</span></span> <span data-ttu-id="715f6-154">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="715f6-154">For example:</span></span>  
  
```  
dta -d AdventureWorks2012 ...  
```  
  
 <span data-ttu-id="715f6-155">複数のデータベース名を指定すると、 **dta** はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="715f6-155">If multiple database names are specified, then **dta** returns an error.</span></span> <span data-ttu-id="715f6-156">**-d** 引数は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="715f6-156">The **-d** argument is optional.</span></span>  
  
 <span data-ttu-id="715f6-157">XML 入力ファイルを使用する場合は、要素の下にある要素を使用して、 **dta**が最初に接続するデータベースを指定でき `DatabaseToConnect` `TuningOptions` ます。</span><span class="sxs-lookup"><span data-stu-id="715f6-157">If you are using an XML input file, you can specify the first database to which **dta** connects by using the `DatabaseToConnect` element that is located under the `TuningOptions` element.</span></span> <span data-ttu-id="715f6-158">詳細については、「 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-158">For more information, see [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
 <span data-ttu-id="715f6-159">データベースを 1 つだけチューニングする場合、 **-d** 引数は **sqlcmd** ユーティリティの **-d** 引数と同様の機能を提供しますが、USE *database_name* ステートメントは実行しません。</span><span class="sxs-lookup"><span data-stu-id="715f6-159">If you are tuning only one database, the **-d** argument provides functionality that is similar to the **-d** argument in the **sqlcmd** utility, but it does not execute the USE *database_name* statement.</span></span> <span data-ttu-id="715f6-160">詳細については、「 [sqlcmd Utility](../sqlcmd-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-160">For more information, see [sqlcmd Utility](../sqlcmd-utility.md).</span></span>  
  
 <span data-ttu-id="715f6-161">**-E**</span><span class="sxs-lookup"><span data-stu-id="715f6-161">**-E**</span></span>  
 <span data-ttu-id="715f6-162">パスワードを要求せずに、セキュリティ接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="715f6-162">Uses a trusted connection instead of requesting a password.</span></span> <span data-ttu-id="715f6-163">ログイン ID を指定する **-E** 引数または **-U** 引数のいずれかを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-163">Either the **-E** argument or the **-U** argument, which specifies a login ID, must be used.</span></span>  
  
 <span data-ttu-id="715f6-164">**-e** _tuning_log_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-164">**-e** _tuning_log_name_</span></span>  
 <span data-ttu-id="715f6-165">**dta** がチューニングできなかったイベントを記録するテーブル名またはファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-165">Specifies the name of the table or file where **dta** records events that it could not tune.</span></span> <span data-ttu-id="715f6-166">このテーブルは、チューニングが行われるサーバー上に作成されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-166">The table is created on the server where the tuning is performed.</span></span>  
  
 <span data-ttu-id="715f6-167">テーブルを使用する場合、 *[database_name].[owner_name].table_name*の形式で名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-167">If a table is used, specify its name in the format: *[database_name].[owner_name].table_name*.</span></span> <span data-ttu-id="715f6-168">次の表は、各パラメーターの既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="715f6-168">The following table shows the default values for each parameter:</span></span>  
  
|<span data-ttu-id="715f6-169">パラメーター</span><span class="sxs-lookup"><span data-stu-id="715f6-169">Parameter</span></span>|<span data-ttu-id="715f6-170">既定値</span><span class="sxs-lookup"><span data-stu-id="715f6-170">Default value</span></span>|  
|---------------|-------------------|  
|<span data-ttu-id="715f6-171">*database_name*</span><span class="sxs-lookup"><span data-stu-id="715f6-171">*database_name*</span></span>|<span data-ttu-id="715f6-172">*-D* オプションで指定された **database_name**</span><span class="sxs-lookup"><span data-stu-id="715f6-172">*database_name* specified with the **-D** option</span></span>|  
|<span data-ttu-id="715f6-173">*owner_name*</span><span class="sxs-lookup"><span data-stu-id="715f6-173">*owner_name*</span></span>|<span data-ttu-id="715f6-174">**dbo**</span><span class="sxs-lookup"><span data-stu-id="715f6-174">**dbo**</span></span><br /><br /> <span data-ttu-id="715f6-175">注: *owner_name*は**dbo**である必要があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-175">Note: *owner_name* must be **dbo**.</span></span> <span data-ttu-id="715f6-176">それ以外の値を指定すると、 **dta** の実行は失敗し、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-176">If any other value is specified, then **dta** execution fails and it returns an error.</span></span>|  
|<span data-ttu-id="715f6-177">*table_name*</span><span class="sxs-lookup"><span data-stu-id="715f6-177">*table_name*</span></span>|<span data-ttu-id="715f6-178">なし</span><span class="sxs-lookup"><span data-stu-id="715f6-178">None</span></span>|  
  
 <span data-ttu-id="715f6-179">ファイルを使用する場合、拡張子として .xml を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-179">If a file is used, specify .xml as its extension.</span></span> <span data-ttu-id="715f6-180">たとえば、TuningLog.xml です。</span><span class="sxs-lookup"><span data-stu-id="715f6-180">For example, TuningLog.xml.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="715f6-181">**dta** ユーティリティは、セッションを削除する際に、ユーザー指定のチューニング ログ テーブルの内容を削除しません。</span><span class="sxs-lookup"><span data-stu-id="715f6-181">The **dta** utility does not delete the contents of user-specified tuning log tables if the session is deleted.</span></span> <span data-ttu-id="715f6-182">大量のワークロードをチューニングするときは、テーブルをチューニング ログ専用にすることを推奨します。</span><span class="sxs-lookup"><span data-stu-id="715f6-182">When tuning very large workloads, we recommend that a table be specified for the tuning log.</span></span> <span data-ttu-id="715f6-183">大量のワークロードをチューニングすると、チューニング ログが大きくなり、テーブルが急速に消費され、セッションが削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-183">Since tuning large workloads can result in large tuning logs, the sessions can be deleted much faster when a table is used.</span></span>  
  
 <span data-ttu-id="715f6-184">**-F**</span><span class="sxs-lookup"><span data-stu-id="715f6-184">**-F**</span></span>  
 <span data-ttu-id="715f6-185">既存の出力ファイルの上書きを **dta** に許可します。</span><span class="sxs-lookup"><span data-stu-id="715f6-185">Permits **dta** to overwrite an existing output file.</span></span> <span data-ttu-id="715f6-186">同じ名前の出力ファイルが既に存在し、 **-F** が指定されていない場合、 **dta**はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="715f6-186">If an output file with the same name already exists and **-F** is not specified, **dta**returns an error.</span></span> <span data-ttu-id="715f6-187">**-F** と **-of**、 **-or**、または **-ox**を同時に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="715f6-187">You can use **-F** with **-of**, **-or**, or **-ox**.</span></span>  
  
 <span data-ttu-id="715f6-188">**-fa** _physical_design_structures_to_add_</span><span class="sxs-lookup"><span data-stu-id="715f6-188">**-fa** _physical_design_structures_to_add_</span></span>  
 <span data-ttu-id="715f6-189">**dta** が推奨設定に含む必要がある物理デザイン構造の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-189">Specifies what types of physical design structures **dta** should include in the recommendation.</span></span> <span data-ttu-id="715f6-190">次の表は、この引数で指定できる値の一覧と説明です。</span><span class="sxs-lookup"><span data-stu-id="715f6-190">The following table lists and describes the values that can be specified for this argument.</span></span> <span data-ttu-id="715f6-191">値が指定されていない場合、 **dta**は既定の **-fa**を使用し `IDX` ます。</span><span class="sxs-lookup"><span data-stu-id="715f6-191">When no value is specified, **dta** uses the default **-fa**`IDX`.</span></span>  
  
|<span data-ttu-id="715f6-192">値</span><span class="sxs-lookup"><span data-stu-id="715f6-192">Value</span></span>|<span data-ttu-id="715f6-193">説明</span><span class="sxs-lookup"><span data-stu-id="715f6-193">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="715f6-194">IDX_IV</span><span class="sxs-lookup"><span data-stu-id="715f6-194">IDX_IV</span></span>|<span data-ttu-id="715f6-195">インデックスおよびインデックス付きビュー。</span><span class="sxs-lookup"><span data-stu-id="715f6-195">Indexes and indexed views.</span></span>|  
|<span data-ttu-id="715f6-196">IDX</span><span class="sxs-lookup"><span data-stu-id="715f6-196">IDX</span></span>|<span data-ttu-id="715f6-197">インデックスのみ。</span><span class="sxs-lookup"><span data-stu-id="715f6-197">Indexes only.</span></span>|  
|<span data-ttu-id="715f6-198">IV</span><span class="sxs-lookup"><span data-stu-id="715f6-198">IV</span></span>|<span data-ttu-id="715f6-199">インデックス付きビューのみ。</span><span class="sxs-lookup"><span data-stu-id="715f6-199">Indexed views only.</span></span>|  
|<span data-ttu-id="715f6-200">NCL_IDX</span><span class="sxs-lookup"><span data-stu-id="715f6-200">NCL_IDX</span></span>|<span data-ttu-id="715f6-201">非クラスター化インデックスのみ。</span><span class="sxs-lookup"><span data-stu-id="715f6-201">Nonclustered indexes only.</span></span>|  
  
 <span data-ttu-id="715f6-202">**-fi**</span><span class="sxs-lookup"><span data-stu-id="715f6-202">**-fi**</span></span>  
 <span data-ttu-id="715f6-203">フィルター選択されたインデックスが新しい推奨設定用と見なされるように指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-203">Specifies that filtered indexes be considered for new recommendations.</span></span> <span data-ttu-id="715f6-204">詳細については、「 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-204">For more information, see [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).</span></span>  
  
 <span data-ttu-id="715f6-205">**-fk** _keep_existing_option_</span><span class="sxs-lookup"><span data-stu-id="715f6-205">**-fk** _keep_existing_option_</span></span>  
 <span data-ttu-id="715f6-206">推奨設定を生成する際に **dta** が保持する必要のある既存の物理デザイン構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-206">Specifies what existing physical design structures **dta** must retain when generating its recommendation.</span></span> <span data-ttu-id="715f6-207">次の表は、この引数で指定できる値の一覧と説明です。</span><span class="sxs-lookup"><span data-stu-id="715f6-207">The following table lists and describes the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="715f6-208">値</span><span class="sxs-lookup"><span data-stu-id="715f6-208">Value</span></span>|<span data-ttu-id="715f6-209">説明</span><span class="sxs-lookup"><span data-stu-id="715f6-209">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="715f6-210">NONE</span><span class="sxs-lookup"><span data-stu-id="715f6-210">NONE</span></span>|<span data-ttu-id="715f6-211">既存の構造なし</span><span class="sxs-lookup"><span data-stu-id="715f6-211">No existing structures</span></span>|  
|<span data-ttu-id="715f6-212">ALL</span><span class="sxs-lookup"><span data-stu-id="715f6-212">ALL</span></span>|<span data-ttu-id="715f6-213">既存のすべての構造</span><span class="sxs-lookup"><span data-stu-id="715f6-213">All existing structures</span></span>|  
|<span data-ttu-id="715f6-214">ALIGNED</span><span class="sxs-lookup"><span data-stu-id="715f6-214">ALIGNED</span></span>|<span data-ttu-id="715f6-215">パーティションで固定された構造をすべて保持します。</span><span class="sxs-lookup"><span data-stu-id="715f6-215">All partition-aligned structures.</span></span>|  
|<span data-ttu-id="715f6-216">CL_IDX</span><span class="sxs-lookup"><span data-stu-id="715f6-216">CL_IDX</span></span>|<span data-ttu-id="715f6-217">テーブル上にあるクラスター化されたすべてのインデックス</span><span class="sxs-lookup"><span data-stu-id="715f6-217">All clustered indexes on tables</span></span>|  
|<span data-ttu-id="715f6-218">IDX</span><span class="sxs-lookup"><span data-stu-id="715f6-218">IDX</span></span>|<span data-ttu-id="715f6-219">テーブル上にある、クラスター化されたすべてのインデックスおよびすべての非クラスター化インデックス</span><span class="sxs-lookup"><span data-stu-id="715f6-219">All clustered and nonclustered indexes on tables</span></span>|  
  
 <span data-ttu-id="715f6-220">**-fp** _partitioning_strategy_</span><span class="sxs-lookup"><span data-stu-id="715f6-220">**-fp** _partitioning_strategy_</span></span>  
 <span data-ttu-id="715f6-221">**dta** によって提示される新しい物理デザイン構造 (インデックスおよびインデックス付きビュー) をパーティション分割する必要があるかどうか、およびパーティション分割の方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-221">Specifies whether new physical design structures (indexes and indexed views) that **dta** proposes should be partitioned, and how they should be partitioned.</span></span> <span data-ttu-id="715f6-222">次の表は、この引数で指定できる値の一覧と説明です。</span><span class="sxs-lookup"><span data-stu-id="715f6-222">The following table lists and describes the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="715f6-223">値</span><span class="sxs-lookup"><span data-stu-id="715f6-223">Value</span></span>|<span data-ttu-id="715f6-224">説明</span><span class="sxs-lookup"><span data-stu-id="715f6-224">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="715f6-225">NONE</span><span class="sxs-lookup"><span data-stu-id="715f6-225">NONE</span></span>|<span data-ttu-id="715f6-226">パーティション分割しない。</span><span class="sxs-lookup"><span data-stu-id="715f6-226">No partitioning</span></span>|  
|<span data-ttu-id="715f6-227">FULL</span><span class="sxs-lookup"><span data-stu-id="715f6-227">FULL</span></span>|<span data-ttu-id="715f6-228">完全パーティション分割 (選択するとパフォーマンスが向上します)。</span><span class="sxs-lookup"><span data-stu-id="715f6-228">Full partitioning (choose to enhance performance)</span></span>|  
|<span data-ttu-id="715f6-229">ALIGNED</span><span class="sxs-lookup"><span data-stu-id="715f6-229">ALIGNED</span></span>|<span data-ttu-id="715f6-230">固定パーティション分割 (選択すると管理機能が強化されます)。</span><span class="sxs-lookup"><span data-stu-id="715f6-230">Aligned partitioning only (choose to enhance manageability)</span></span>|  
  
 <span data-ttu-id="715f6-231">ALIGNED は、 **dta** によって生成された推奨設定では、提示されるすべてのインデックスが、インデックス定義の基になるテーブルとまったく同じ方法でパーティション分割されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="715f6-231">ALIGNED means that in the recommendation generated by **dta** every proposed index is partitioned in exactly the same way as the underlying table for which the index is defined.</span></span> <span data-ttu-id="715f6-232">インデックス付きビューの非クラスター化インデックスは、インデックス付きビューに準じます。</span><span class="sxs-lookup"><span data-stu-id="715f6-232">Nonclustered indexes on an indexed view are aligned with the indexed view.</span></span> <span data-ttu-id="715f6-233">この引数で指定できる値は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="715f6-233">Only one value can be specified for this argument.</span></span> <span data-ttu-id="715f6-234">既定値は **-fp**です `NONE` 。</span><span class="sxs-lookup"><span data-stu-id="715f6-234">The default is **-fp**`NONE`.</span></span>  
  
 <span data-ttu-id="715f6-235">**-fx** _drop_only_mode_</span><span class="sxs-lookup"><span data-stu-id="715f6-235">**-fx** _drop_only_mode_</span></span>  
 <span data-ttu-id="715f6-236">**dta** が、既存の物理デザイン構造の削除のみを考慮することを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-236">Specifies that **dta** only considers dropping existing physical design structures.</span></span> <span data-ttu-id="715f6-237">新しい物理デザイン構造は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="715f6-237">No new physical design structures are considered.</span></span> <span data-ttu-id="715f6-238">このオプションを指定すると、 **dta** は既存の物理デザイン構造の有用性を評価し、その後、使用頻度の低い構造を削除する推奨設定を提示します。</span><span class="sxs-lookup"><span data-stu-id="715f6-238">When this option is specified, **dta** evaluates the usefulness of existing physical design structures and recommends dropping seldom used structures.</span></span> <span data-ttu-id="715f6-239">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="715f6-239">This argument takes no values.</span></span> <span data-ttu-id="715f6-240">この引数と **-fa**、 **-fp**、または **-fk ALL** 引数を同時に使用することはできません</span><span class="sxs-lookup"><span data-stu-id="715f6-240">It cannot be used with the **-fa**, **-fp**, or **-fk ALL** arguments</span></span>  
  
 <span data-ttu-id="715f6-241">**-ID** _session_ID_</span><span class="sxs-lookup"><span data-stu-id="715f6-241">**-ID** _session_ID_</span></span>  
 <span data-ttu-id="715f6-242">チューニング セッションの識別子を数値で指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-242">Specifies a numerical identifier for the tuning session.</span></span> <span data-ttu-id="715f6-243">指定しない場合、 **dta** は ID 番号を生成します。</span><span class="sxs-lookup"><span data-stu-id="715f6-243">If not specified, then **dta** generates an ID number.</span></span> <span data-ttu-id="715f6-244">この識別子を使用して、既存のチューニング セッションの情報を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="715f6-244">You can use this identifier to view information for existing tuning sessions.</span></span> <span data-ttu-id="715f6-245">**-ID**に値を指定しない場合は、セッション名を **-s**で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-245">If you do not specify a value for **-ID**, then a session name must be specified with **-s**.</span></span>  
  
 <span data-ttu-id="715f6-246">**-ip**</span><span class="sxs-lookup"><span data-stu-id="715f6-246">**-ip**</span></span>  
 <span data-ttu-id="715f6-247">プラン キャッシュをワークロードとして使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-247">Specifies that the plan cache be used as the workload.</span></span> <span data-ttu-id="715f6-248">明示的に選択したデータベースの上位 1,000 個のプラン キャッシュ イベントが分析されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-248">The top 1,000 plan cache events for explicitly selected databases are analyzed.</span></span> <span data-ttu-id="715f6-249">この値は **-n** オプションを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="715f6-249">This value can be changed using the **-n** option.</span></span>  
  
 <span data-ttu-id="715f6-250">**-ipf**</span><span class="sxs-lookup"><span data-stu-id="715f6-250">**-ipf**</span></span>  
 <span data-ttu-id="715f6-251">プラン キャッシュをワークロードとして使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-251">Specifies that the plan cache be used as the workload.</span></span> <span data-ttu-id="715f6-252">すべてのデータベースの上位 1,000 個のプラン キャッシュ イベントが分析されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-252">The top 1,000 plan cache events for all databases are analyzed.</span></span> <span data-ttu-id="715f6-253">この値は **-n** オプションを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="715f6-253">This value can be changed using the **-n** option.</span></span>  
  
 <span data-ttu-id="715f6-254">**-if** _workload_file_</span><span class="sxs-lookup"><span data-stu-id="715f6-254">**-if** _workload_file_</span></span>  
 <span data-ttu-id="715f6-255">チューニングの入力として使用するワークロード ファイルのパスとファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-255">Specifies the path and name of the workload file to use as input for tuning.</span></span> <span data-ttu-id="715f6-256">ファイルは、.trc (SQL Server Profiler トレース ファイル)、.sql (SQL ファイル)、.log ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] トレース ファイル) のいずれかの形式になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-256">The file must be in one of these formats: .trc (SQL Server Profiler trace file), .sql (SQL file), or .log ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace file).</span></span> <span data-ttu-id="715f6-257">ワークロード ファイル、またはワークロード テーブルを 1 つ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="715f6-257">Either one workload file or one workload table must be specified.</span></span>  
  
 <span data-ttu-id="715f6-258">**-it** _workload_trace_table_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-258">**-it** _workload_trace_table_name_</span></span>  
 <span data-ttu-id="715f6-259">チューニングのワークロード トレースを含むテーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-259">Specifies the name of a table containing the workload trace for tuning.</span></span> <span data-ttu-id="715f6-260">名前は *[database_name*] **.** [*owner_name*] **.** _table_name_の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-260">The name is specified in the format: [*database_name*]**.**[*owner_name*]**.**_table_name_.</span></span>  
  
 <span data-ttu-id="715f6-261">次の表は、各パラメーターの既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="715f6-261">The following table shows the default values for each:</span></span>  
  
|<span data-ttu-id="715f6-262">パラメーター</span><span class="sxs-lookup"><span data-stu-id="715f6-262">Parameter</span></span>|<span data-ttu-id="715f6-263">既定値</span><span class="sxs-lookup"><span data-stu-id="715f6-263">Default value</span></span>|  
|---------------|-------------------|  
|<span data-ttu-id="715f6-264">*database_name*</span><span class="sxs-lookup"><span data-stu-id="715f6-264">*database_name*</span></span>|<span data-ttu-id="715f6-265">*-D* オプションで指定された **database_name**。</span><span class="sxs-lookup"><span data-stu-id="715f6-265">*database_name* specified with **-D** option.</span></span>|  
|<span data-ttu-id="715f6-266">*owner_name*</span><span class="sxs-lookup"><span data-stu-id="715f6-266">*owner_name*</span></span>|<span data-ttu-id="715f6-267">**dbo**。</span><span class="sxs-lookup"><span data-stu-id="715f6-267">**dbo**.</span></span>|  
|<span data-ttu-id="715f6-268">*table_name*</span><span class="sxs-lookup"><span data-stu-id="715f6-268">*table_name*</span></span>|<span data-ttu-id="715f6-269">[なし] :</span><span class="sxs-lookup"><span data-stu-id="715f6-269">None.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="715f6-270">*owner_name* は必ず **dbo**としてください。</span><span class="sxs-lookup"><span data-stu-id="715f6-270">*owner_name* must be **dbo**.</span></span> <span data-ttu-id="715f6-271">それ以外の値を指定すると、 **dta** の実行は失敗し、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-271">If any other value is specified, execution of **dta** fails and an error is returned.</span></span> <span data-ttu-id="715f6-272">ワークロード ファイルまたはワークロード テーブルを 1 つ指定する必要があることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-272">Also note that either one workload table or one workload file must be specified.</span></span>  
  
 <span data-ttu-id="715f6-273">**-ix** _input_XML_file_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-273">**-ix** _input_XML_file_name_</span></span>  
 <span data-ttu-id="715f6-274">**dta** の入力情報を含む XML ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-274">Specifies the name of the XML file containing **dta** input information.</span></span> <span data-ttu-id="715f6-275">これは、DTASchema.xsd に従った有効な XML ドキュメントであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="715f6-275">This must be a valid XML document conforming to DTASchema.xsd.</span></span> <span data-ttu-id="715f6-276">チューニング オプションのコマンド プロンプトから指定した引数と競合する場合、この XML ファイルの対応する値がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="715f6-276">Conflicting arguments specified from the command prompt for tuning options override the corresponding value in this XML file.</span></span> <span data-ttu-id="715f6-277">唯一の例外は、ユーザー定義の構成が XML 入力ファイルに評価モードで入力されている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="715f6-277">The only exception is if a user-specified configuration is entered in the evaluate mode in the XML input file.</span></span> <span data-ttu-id="715f6-278">たとえば、XML 入力ファイルの **Configuration** 要素に構成が入力されており、**EvaluateConfiguration** 要素も同様にチューニング オプションの 1 つとして指定されている場合、XML 入力ファイルで指定されたチューニング オプションは、コマンド プロンプトから入力されるいずれのチューニング オプションをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="715f6-278">For example, if a configuration is entered in the **Configuration** element of the XML input file and the **EvaluateConfiguration** element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered from the command prompt.</span></span>  
  
 <span data-ttu-id="715f6-279">**-m** _minimum_improvement_</span><span class="sxs-lookup"><span data-stu-id="715f6-279">**-m** _minimum_improvement_</span></span>  
 <span data-ttu-id="715f6-280">推奨構成が満たす必要がある、最小向上率を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-280">Specifies the minimum percentage of improvement that the recommended configuration must satisfy.</span></span>  
  
 <span data-ttu-id="715f6-281">**-N** _online_option_</span><span class="sxs-lookup"><span data-stu-id="715f6-281">**-N** _online_option_</span></span>  
 <span data-ttu-id="715f6-282">物理デザイン構造をオンラインで作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-282">Specifies whether physical design structures are created online.</span></span> <span data-ttu-id="715f6-283">次の表は、この引数で指定できる値の一覧と説明です。</span><span class="sxs-lookup"><span data-stu-id="715f6-283">The following table lists and describes the values you can specify for this argument:</span></span>  
  
|<span data-ttu-id="715f6-284">値</span><span class="sxs-lookup"><span data-stu-id="715f6-284">Value</span></span>|<span data-ttu-id="715f6-285">説明</span><span class="sxs-lookup"><span data-stu-id="715f6-285">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="715f6-286">OFF</span><span class="sxs-lookup"><span data-stu-id="715f6-286">OFF</span></span>|<span data-ttu-id="715f6-287">推奨される物理デザイン構造をオンラインで作成しません。</span><span class="sxs-lookup"><span data-stu-id="715f6-287">No recommended physical design structures can be created online.</span></span>|  
|<span data-ttu-id="715f6-288">ON</span><span class="sxs-lookup"><span data-stu-id="715f6-288">ON</span></span>|<span data-ttu-id="715f6-289">推奨される物理デザイン構造をすべてオンラインで作成します。</span><span class="sxs-lookup"><span data-stu-id="715f6-289">All recommended physical design structures can be created online.</span></span>|  
|<span data-ttu-id="715f6-290">MIXED</span><span class="sxs-lookup"><span data-stu-id="715f6-290">MIXED</span></span>|<span data-ttu-id="715f6-291">データベース エンジン チューニング アドバイザーは、可能な場合にオンラインで作成できる物理デザイン構造を推奨します。</span><span class="sxs-lookup"><span data-stu-id="715f6-291">Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.</span></span>|  
  
 <span data-ttu-id="715f6-292">インデックスがオンラインで作成される場合、このオブジェクト定義には ONLINE = ON が追加されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-292">If indexes are created online, ONLINE = ON is appended to its object definition.</span></span>  
  
 <span data-ttu-id="715f6-293">**-n** _number_of_events_</span><span class="sxs-lookup"><span data-stu-id="715f6-293">**-n** _number_of_events_</span></span>  
 <span data-ttu-id="715f6-294">**dta** がチューニングする必要があるワークロード内のイベント数を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-294">Specifies the number of events in the workload that **dta** should tune.</span></span> <span data-ttu-id="715f6-295">この引数が指定され、ワークロードが実行時間の情報を含むトレース ファイルの場合、 **dta** は、実行時間の長いものから順にイベントをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="715f6-295">If this argument is specified and the workload is a trace file that contains duration information, then **dta** tunes events in decreasing order of duration.</span></span> <span data-ttu-id="715f6-296">この引数は、物理デザイン構造の 2 つの構成を比較する場合に利用できます。</span><span class="sxs-lookup"><span data-stu-id="715f6-296">This argument is useful to compare two configurations of physical design structures.</span></span> <span data-ttu-id="715f6-297">2 つの構成を比較するには、両方の構成でチューニングする同じイベント数を指定し、次に示すように両方のチューニング時間を無制限に指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-297">To compare two configurations, specify the same number of events to be tuned for both configurations and then specify an unlimited tuning time for both also as follows:</span></span>  
  
```  
dta -n number_of_events -A 0  
```  
  
 <span data-ttu-id="715f6-298">この場合、チューニング時間を無制限 (`-A 0`) に指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="715f6-298">In this case, it is important to specify an unlimited tuning time (`-A 0`).</span></span> <span data-ttu-id="715f6-299">無制限に指定しない場合、データベース エンジン チューニング アドバイザーでは、既定の 8 時間のチューニング時間が前提となります。</span><span class="sxs-lookup"><span data-stu-id="715f6-299">Otherwise, Database Engine Tuning Advisor assumes an 8 hour tuning time by default.</span></span>  
  
 <span data-ttu-id="715f6-300">**-of** _output_script_file_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-300">**-of** _output_script_file_name_</span></span>  
 <span data-ttu-id="715f6-301">**dta** が、指定したファイル名と出力先に推奨設定を [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトとして書き込むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-301">Specifies that **dta** writes the recommendation as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script to the file name and destination specified.</span></span>  
  
 <span data-ttu-id="715f6-302">このオプションと **-F** を同時に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="715f6-302">You can use **-F** with this option.</span></span> <span data-ttu-id="715f6-303">特に **-or** および **-ox**も使用している場合は、ファイル名が一意であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-303">Make sure that the file name is unique, especially if you are also using **-or** and **-ox**.</span></span>  
  
 <span data-ttu-id="715f6-304">**-or** _output_xml_report_file_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-304">**-or** _output_xml_report_file_name_</span></span>  
 <span data-ttu-id="715f6-305">**dta** が、XML 形式の出力レポートに推奨設定を書き込むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-305">Specifies that **dta** writes the recommendation to an output report in XML.</span></span> <span data-ttu-id="715f6-306">ファイル名を指定した場合、推奨設定はその出力先へ書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="715f6-306">If a file name is supplied, then the recommendations are written to that destination.</span></span> <span data-ttu-id="715f6-307">ファイル名を指定しない場合、 **dta** はセッション名を使用してファイル名を生成し、それを現在のディレクトリに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="715f6-307">Otherwise, **dta** uses the session name to generate the file name and writes it to the current directory.</span></span>  
  
 <span data-ttu-id="715f6-308">このオプションと **-F** を同時に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="715f6-308">You can use **-F** with this option.</span></span> <span data-ttu-id="715f6-309">特に **-of** および **-ox**も使用している場合は、ファイル名が一意であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-309">Make sure that the file name is unique, especially if you are also using **-of** and **-ox**.</span></span>  
  
 <span data-ttu-id="715f6-310">**-ox** _output_XML_file_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-310">**-ox** _output_XML_file_name_</span></span>  
 <span data-ttu-id="715f6-311">**dta** が、指定したファイル名と出力先に推奨設定を XML ファイルとして書き込むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-311">Specifies that **dta** writes the recommendation as an XML file to the file name and destination supplied.</span></span> <span data-ttu-id="715f6-312">データベース エンジン チューニング アドバイザーには、宛先ディレクトリへの書き込み権限があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-312">Ensure that Database Engine Tuning Advisor has permissions to write to the destination directory.</span></span>  
  
 <span data-ttu-id="715f6-313">このオプションと **-F** を同時に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="715f6-313">You can use **-F** with this option.</span></span> <span data-ttu-id="715f6-314">特に **-of** および **-or**も使用している場合は、ファイル名が一意であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-314">Make sure that the file name is unique, especially if you are also using **-of** and **-or**.</span></span>  
  
 <span data-ttu-id="715f6-315">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="715f6-315">**-P** _password_</span></span>  
 <span data-ttu-id="715f6-316">ログイン ID のパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-316">Specifies the password for the login ID.</span></span> <span data-ttu-id="715f6-317">このオプションを使用しない場合、 **dta** はパスワードの入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="715f6-317">If this option is not used, **dta** prompts for a password.</span></span>  
  
 <span data-ttu-id="715f6-318">**-q**</span><span class="sxs-lookup"><span data-stu-id="715f6-318">**-q**</span></span>  
 <span data-ttu-id="715f6-319">非表示モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-319">Sets quiet mode.</span></span> <span data-ttu-id="715f6-320">進行状況やヘッダー情報を含め、コンソールには情報が一切表示されません。</span><span class="sxs-lookup"><span data-stu-id="715f6-320">No information is written to the console, including progress and header information.</span></span>  
  
 <span data-ttu-id="715f6-321">**-rl** _analysis_report_list_</span><span class="sxs-lookup"><span data-stu-id="715f6-321">**-rl** _analysis_report_list_</span></span>  
 <span data-ttu-id="715f6-322">生成する分析レポートのリストを指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-322">Specifies the list of analysis reports to generate.</span></span> <span data-ttu-id="715f6-323">次の表は、この引数で指定できる値の一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="715f6-323">The following table lists the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="715f6-324">値</span><span class="sxs-lookup"><span data-stu-id="715f6-324">Value</span></span>|<span data-ttu-id="715f6-325">レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-325">Report</span></span>|  
|-----------|------------|  
|<span data-ttu-id="715f6-326">ALL</span><span class="sxs-lookup"><span data-stu-id="715f6-326">ALL</span></span>|<span data-ttu-id="715f6-327">すべての分析レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-327">All analysis reports</span></span>|  
|<span data-ttu-id="715f6-328">STMT_COST</span><span class="sxs-lookup"><span data-stu-id="715f6-328">STMT_COST</span></span>|<span data-ttu-id="715f6-329">ステートメント コスト レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-329">Statement cost report</span></span>|  
|<span data-ttu-id="715f6-330">EVT_FREQ</span><span class="sxs-lookup"><span data-stu-id="715f6-330">EVT_FREQ</span></span>|<span data-ttu-id="715f6-331">イベント頻度レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-331">Event frequency report</span></span>|  
|<span data-ttu-id="715f6-332">STMT_DET</span><span class="sxs-lookup"><span data-stu-id="715f6-332">STMT_DET</span></span>|<span data-ttu-id="715f6-333">ステートメントの詳細レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-333">Statement detail report</span></span>|  
|<span data-ttu-id="715f6-334">CUR_STMT_IDX</span><span class="sxs-lookup"><span data-stu-id="715f6-334">CUR_STMT_IDX</span></span>|<span data-ttu-id="715f6-335">ステートメントとインデックスのリレーション レポート (現在の構成)</span><span class="sxs-lookup"><span data-stu-id="715f6-335">Statement-index relations report (current configuration)</span></span>|  
|<span data-ttu-id="715f6-336">REC_STMT_IDX</span><span class="sxs-lookup"><span data-stu-id="715f6-336">REC_STMT_IDX</span></span>|<span data-ttu-id="715f6-337">ステートメントとインデックスのリレーション レポート (推奨構成)</span><span class="sxs-lookup"><span data-stu-id="715f6-337">Statement-index relations report (recommended configuration)</span></span>|  
|<span data-ttu-id="715f6-338">STMT_COSTRANGE</span><span class="sxs-lookup"><span data-stu-id="715f6-338">STMT_COSTRANGE</span></span>|<span data-ttu-id="715f6-339">ステートメント コスト範囲レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-339">Statement cost range report</span></span>|  
|<span data-ttu-id="715f6-340">CUR_IDX_USAGE</span><span class="sxs-lookup"><span data-stu-id="715f6-340">CUR_IDX_USAGE</span></span>|<span data-ttu-id="715f6-341">インデックス使用状況レポート (現在の構成)</span><span class="sxs-lookup"><span data-stu-id="715f6-341">Index usage report (current configuration)</span></span>|  
|<span data-ttu-id="715f6-342">REC_IDX_USAGE</span><span class="sxs-lookup"><span data-stu-id="715f6-342">REC_IDX_USAGE</span></span>|<span data-ttu-id="715f6-343">インデックス使用状況レポート (推奨構成)</span><span class="sxs-lookup"><span data-stu-id="715f6-343">Index usage report (recommended configuration)</span></span>|  
|<span data-ttu-id="715f6-344">CUR_IDX_DET</span><span class="sxs-lookup"><span data-stu-id="715f6-344">CUR_IDX_DET</span></span>|<span data-ttu-id="715f6-345">インデックスの詳細レポート (現在の構成)</span><span class="sxs-lookup"><span data-stu-id="715f6-345">Index detail report (current configuration)</span></span>|  
|<span data-ttu-id="715f6-346">REC_IDX_DET</span><span class="sxs-lookup"><span data-stu-id="715f6-346">REC_IDX_DET</span></span>|<span data-ttu-id="715f6-347">インデックスの詳細レポート (推奨構成)</span><span class="sxs-lookup"><span data-stu-id="715f6-347">Index detail report (recommended configuration)</span></span>|  
|<span data-ttu-id="715f6-348">VIW_TAB</span><span class="sxs-lookup"><span data-stu-id="715f6-348">VIW_TAB</span></span>|<span data-ttu-id="715f6-349">ビューとテーブルのリレーション レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-349">View-table relations report</span></span>|  
|<span data-ttu-id="715f6-350">WKLD_ANL</span><span class="sxs-lookup"><span data-stu-id="715f6-350">WKLD_ANL</span></span>|<span data-ttu-id="715f6-351">ワークロード分析レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-351">Workload analysis report</span></span>|  
|<span data-ttu-id="715f6-352">DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="715f6-352">DB_ACCESS</span></span>|<span data-ttu-id="715f6-353">データベース アクセス レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-353">Database access report</span></span>|  
|<span data-ttu-id="715f6-354">TAB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="715f6-354">TAB_ACCESS</span></span>|<span data-ttu-id="715f6-355">テーブルのアクセス レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-355">Table access report</span></span>|  
|<span data-ttu-id="715f6-356">COL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="715f6-356">COL_ACCESS</span></span>|<span data-ttu-id="715f6-357">列のアクセス レポート</span><span class="sxs-lookup"><span data-stu-id="715f6-357">Column access report</span></span>|  
  
 <span data-ttu-id="715f6-358">値をコンマで区切って複数のレポートを指定します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="715f6-358">Specify multiple reports by separating the values with commas, for example:</span></span>  
  
```  
... -rl EVT_FREQ, VIW_TAB, WKLD_ANL ...  
```  
  
 <span data-ttu-id="715f6-359">**-S** _server_name_[ *\instance*]</span><span class="sxs-lookup"><span data-stu-id="715f6-359">**-S** _server_name_[ *\instance*]</span></span>  
 <span data-ttu-id="715f6-360">接続先となる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンピューターとインスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-360">Specifies the name of the computer and instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect to.</span></span> <span data-ttu-id="715f6-361">*server_name* を指定しない場合、 **dta** はローカル コンピューター上にある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="715f6-361">If no *server_name* is specified, **dta** connects to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="715f6-362">名前付きインスタンスに接続する場合、またはネットワーク上のリモート コンピューターから **dta** を実行する場合、このオプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="715f6-362">This option is required when connecting to a named instance or when executing **dta** from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="715f6-363">**-s** _session_name_</span><span class="sxs-lookup"><span data-stu-id="715f6-363">**-s** _session_name_</span></span>  
 <span data-ttu-id="715f6-364">チューニング セッションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-364">Specifies the name of the tuning session.</span></span> <span data-ttu-id="715f6-365">**-ID** を指定しない場合、これは必須です。</span><span class="sxs-lookup"><span data-stu-id="715f6-365">This is required if **-ID** is not specified.</span></span>  
  
 <span data-ttu-id="715f6-366">**-Tf** _table_list_file_</span><span class="sxs-lookup"><span data-stu-id="715f6-366">**-Tf** _table_list_file_</span></span>  
 <span data-ttu-id="715f6-367">チューニングするテーブルの一覧が含まれているファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-367">Specifies the name of a file containing a list of tables to be tuned.</span></span> <span data-ttu-id="715f6-368">このファイル内では、各テーブルをそれぞれ行を変えて指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-368">Each table listed within the file should begin on a new line.</span></span> <span data-ttu-id="715f6-369">テーブル名は、 **AdventureWorks2012.HumanResources.Department**のように、3 つの部分から構成されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-369">Table names should be qualified with three-part naming, for example, **AdventureWorks2012.HumanResources.Department**.</span></span> <span data-ttu-id="715f6-370">必要に応じてテーブル スケーリング機能を呼び出すには、既存のテーブル名の後に、テーブル内の行の予測数を示す数字を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-370">Optionally, to invoke the table-scaling feature, the name of an existing table can be followed by a number indicating the projected number of rows in the table.</span></span> <span data-ttu-id="715f6-371">データベース エンジン チューニング アドバイザーでは、これらのテーブルを参照するワークロード内にあるステートメントのチューニングや評価を行うときに、行の予測数を考慮します。</span><span class="sxs-lookup"><span data-stu-id="715f6-371">Database Engine Tuning Advisor takes into consideration the projected number of rows while tuning or evaluating statements in the workload that reference these tables.</span></span> <span data-ttu-id="715f6-372">*number_of_rows* と *table_name*の間には 1 つ以上の空白がある場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-372">Note that there can be one or more spaces between the *number_of_rows* count and the *table_name*.</span></span>  
  
 <span data-ttu-id="715f6-373">次に、 *table_list_file*ファイルのフォーマットを示します。</span><span class="sxs-lookup"><span data-stu-id="715f6-373">This is the file format for *table_list_file*:</span></span>  
  
 <span data-ttu-id="715f6-374">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="715f6-374">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="715f6-375">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="715f6-375">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="715f6-376">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="715f6-376">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="715f6-377">この引数は、コマンド プロンプトでテーブルの一覧 ( **-Tl**) を入力する代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="715f6-377">This argument is an alternative to entering a table list at the command prompt (**-Tl**).</span></span> <span data-ttu-id="715f6-378">**-Tl**を使用する場合は、テーブルの一覧ファイル ( **-Tf**) を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="715f6-378">Do not use a table list file (**-Tf**) if you are using **-Tl**.</span></span> <span data-ttu-id="715f6-379">両方の引数を使用すると、 **dta** は失敗し、エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="715f6-379">If both arguments are used, **dta** fails and returns an error.</span></span>  
  
 <span data-ttu-id="715f6-380">**-Tf** 引数および **-Tl** 引数を省略した場合、指定されたデータベース内のすべてのユーザー テーブルをチューニングするものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="715f6-380">If the **-Tf** and **-Tl** arguments are omitted, all user tables in the specified databases are considered for tuning.</span></span>  
  
 <span data-ttu-id="715f6-381">**-Tl** _table_list_</span><span class="sxs-lookup"><span data-stu-id="715f6-381">**-Tl** _table_list_</span></span>  
 <span data-ttu-id="715f6-382">コマンド プロンプトでチューニングするテーブルの一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-382">Specifies at the command prompt a list of tables to be tuned.</span></span> <span data-ttu-id="715f6-383">テーブル名の間にコンマを挿入して区切ります。</span><span class="sxs-lookup"><span data-stu-id="715f6-383">Place commas between table names to separate them.</span></span> <span data-ttu-id="715f6-384">**-D** 引数で 1 つのデータベースのみを指定する場合、テーブル名をデータベース名で修飾する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="715f6-384">If only one database is specified with the **-D** argument, then table names do not need to be qualified with a database name.</span></span> <span data-ttu-id="715f6-385">それ以外の場合、各テーブルには *database_name.schema_name.table_name* の形式で、完全修飾名が必要となります。</span><span class="sxs-lookup"><span data-stu-id="715f6-385">Otherwise, the fully qualified name in the format: *database_name.schema_name.table_name* is required for each table.</span></span>  
  
 <span data-ttu-id="715f6-386">この引数は、テーブルの一覧ファイル ( **-Tf**) の代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="715f6-386">This argument is an alternative to using a table list file (**-Tf**).</span></span> <span data-ttu-id="715f6-387">**-Tl** と **-Tf** の両方を使用すると、 **dta** は失敗し、エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="715f6-387">If both **-Tl** and **-Tf** are used, **dta** fails and returns an error.</span></span>  
  
 <span data-ttu-id="715f6-388">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="715f6-388">**-U** _login_id_</span></span>  
 <span data-ttu-id="715f6-389">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への接続に使用されるログイン ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-389">Specifies the login ID used to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="715f6-390">**-u**</span><span class="sxs-lookup"><span data-stu-id="715f6-390">**-u**</span></span>  
 <span data-ttu-id="715f6-391">データベース エンジン チューニング アドバイザー GUI を起動します。</span><span class="sxs-lookup"><span data-stu-id="715f6-391">Launches the Database Engine Tuning Advisor GUI.</span></span> <span data-ttu-id="715f6-392">すべてのパラメーターは、ユーザー インターフェイスの初期設定として扱われます。</span><span class="sxs-lookup"><span data-stu-id="715f6-392">All parameters are treated as the initial settings for the user interface.</span></span>  
  
 <span data-ttu-id="715f6-393">**-x**</span><span class="sxs-lookup"><span data-stu-id="715f6-393">**-x**</span></span>  
 <span data-ttu-id="715f6-394">チューニング セッションを開始し、終了します。</span><span class="sxs-lookup"><span data-stu-id="715f6-394">Starts tuning session and exits.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="715f6-395">解説</span><span class="sxs-lookup"><span data-stu-id="715f6-395">Remarks</span></span>  
 <span data-ttu-id="715f6-396">Ctrl + C キーを 1 度押すと、チューニング セッションが停止し、 **dta** がこの時点までに完了した分析に基づいて、推奨設定が生成されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-396">Press CTRL+C once to stop the tuning session and generate recommendations based on the analysis **dta** has completed up to this point.</span></span> <span data-ttu-id="715f6-397">推奨設定を生成するかどうかの確認が要求されます。</span><span class="sxs-lookup"><span data-stu-id="715f6-397">You will be prompted to decide whether you want to generate recommendations or not.</span></span> <span data-ttu-id="715f6-398">Ctrl</localizedText> + <localizedText>C</localizedText> キーをもう一度押すと、推奨設定を生成せずにチューニング セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="715f6-398">Press CTRL+C again to stop the tuning session without generating recommendations.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="715f6-399">例</span><span class="sxs-lookup"><span data-stu-id="715f6-399">Examples</span></span>  
 <span data-ttu-id="715f6-400">**A.推奨設定で、インデックスとインデックス付きビューを含んだワークロードをチューニングする**</span><span class="sxs-lookup"><span data-stu-id="715f6-400">**A. Tune a workload that includes indexes and indexed views in its recommendation**</span></span>  
  
 <span data-ttu-id="715f6-401">次の例では、セキュリティで保護された接続 (`-E`) を使用して MyServer の **tpcd1G** データベースに接続し、ワークロードの分析と推奨設定の作成を行います。</span><span class="sxs-lookup"><span data-stu-id="715f6-401">This example uses a secure connection (`-E`) to connect to the **tpcd1G** database on MyServer to analyze a workload and create recommendations.</span></span> <span data-ttu-id="715f6-402">出力結果は script.sql という名前のスクリプト ファイルへ書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="715f6-402">It writes the output to a script file named script.sql.</span></span> <span data-ttu-id="715f6-403">script.sql が既に存在する場合は、 **引数が指定されているため、** dta `-F` はファイルを上書きします。</span><span class="sxs-lookup"><span data-stu-id="715f6-403">If script.sql already exists, then **dta** will overwrite the file because the `-F` argument has been specified.</span></span> <span data-ttu-id="715f6-404">チューニング セッションは、ワークロードの分析を完全に終了するように時間制限なしで実行されます (`-A 0`)。</span><span class="sxs-lookup"><span data-stu-id="715f6-404">The tuning session runs for an unlimited length of time to ensure a complete analysis of the workload (`-A 0`).</span></span> <span data-ttu-id="715f6-405">推奨設定の最小向上率は 5% を指定する必要があります (`-m 5`)。</span><span class="sxs-lookup"><span data-stu-id="715f6-405">The recommendation must provide a minimum improvement of 5% (`-m 5`).</span></span> <span data-ttu-id="715f6-406">**dta** では、最終的な推奨設定にインデックスおよびインデックス付きビューが含まれます (`-fa IDX_IV`)。</span><span class="sxs-lookup"><span data-stu-id="715f6-406">**dta** should include indexes and indexed views in its final recommendation (`-fa IDX_IV`).</span></span>  
  
```  
dta -S MyServer -E -D tpcd1G -if tpcd_22.sql -F -of script.sql -A 0 -m 5 -fa IDX_IV  
```  
  
 <span data-ttu-id="715f6-407">**B.ディスク使用量を制限する**</span><span class="sxs-lookup"><span data-stu-id="715f6-407">**B. Limit disk use**</span></span>  
  
 <span data-ttu-id="715f6-408">次の例では、生データと追加のインデックスを含むデータベースの合計サイズを 3 GB までに制限し (`-B 3000`)、出力先には d:\result_dir\script1.sql を指定しています。</span><span class="sxs-lookup"><span data-stu-id="715f6-408">This example limits the total database size, which includes the raw data and the additional indexes, to 3 gigabytes (GB) (`-B 3000`) and directs the output to d:\result_dir\script1.sql.</span></span> <span data-ttu-id="715f6-409">実行は、1 時間以内です (`-A 60`)。</span><span class="sxs-lookup"><span data-stu-id="715f6-409">It runs for no more than 1 hour (`-A 60`).</span></span>  
  
```  
dta -D tpcd1G -if tpcd_22.sql -B 3000 -of "d:\result_dir\script1.sql" -A 60  
```  
  
 <span data-ttu-id="715f6-410">**C.チューニングするクエリの数を制限する**</span><span class="sxs-lookup"><span data-stu-id="715f6-410">**C. Limit the number of tuned queries**</span></span>  
  
 <span data-ttu-id="715f6-411">次の例では、orders_wkld.sql ファイルから読み取るクエリの数を最大 10 に制限し (`-n 10`)、15 分間実行します (`-A 15`)。どちらを先に指定しても同じです。</span><span class="sxs-lookup"><span data-stu-id="715f6-411">This example limits the number of queries read from the file orders_wkld.sql to a maximum of 10 (`-n 10`) and runs for 15 minutes (`-A 15`), whichever comes first.</span></span> <span data-ttu-id="715f6-412">10 個のクエリすべてをチューニングするために、`-A 0` を使用してチューニング時間を無制限に指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-412">To make sure that all 10 queries are tuned, specify an unlimited tuning time with `-A 0`.</span></span> <span data-ttu-id="715f6-413">時間が重要な場合は、この例で示すように `-A` 引数でチューニングできる時間数を指定して、適切な制限時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-413">If time is important, specify an appropriate time limit by specifying the number of minutes that are available for tuning with the `-A` argument as shown in this example.</span></span>  
  
```  
dta -D orders -if orders_wkld.sql -of script.sql -A 15 -n 10  
```  
  
 <span data-ttu-id="715f6-414">**D.ファイル内に指定されている特定のテーブルをチューニングする**</span><span class="sxs-lookup"><span data-stu-id="715f6-414">**D. Tune specific tables listed in a file**</span></span>  
  
 <span data-ttu-id="715f6-415">次の例では、 *table_list_file* ( **-Tf** 引数) の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="715f6-415">This example demonstrates the use of *table_list_file* (the **-Tf** argument).</span></span> <span data-ttu-id="715f6-416">table_list.txt ファイルの内容は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="715f6-416">The contents of the file table_list.txt are as follows:</span></span>  
  
```  
AdventureWorks2012.Sales.Customer  100000  
AdventureWorks2012.Sales.Store  
AdventureWorks2012.Production.Product  2000000  
```  
  
 <span data-ttu-id="715f6-417">table_list.txt 内には、次の内容が指定されています。</span><span class="sxs-lookup"><span data-stu-id="715f6-417">The contents of table_list.txt specifies that:</span></span>  
  
-   <span data-ttu-id="715f6-418">データベース内にある **Customer**、 **Store**、および **Product** テーブルのみをチューニングの対象とする。</span><span class="sxs-lookup"><span data-stu-id="715f6-418">Only the **Customer**, **Store**, and **Product** tables in the database should be tuned.</span></span>  
  
-   <span data-ttu-id="715f6-419">**Customer** 、 **Product** テーブルの列数は、それぞれ 100,000 と 2,000,000 と想定する。</span><span class="sxs-lookup"><span data-stu-id="715f6-419">The number of rows in the **Customer** and **Product** tables are assumed to be 100,000 and 2,000,000, respectively.</span></span>  
  
-   <span data-ttu-id="715f6-420">**Store** の行数は、このテーブル内の現在の行数と同じと想定する。</span><span class="sxs-lookup"><span data-stu-id="715f6-420">The number of rows in **Store** are assumed to be the current number of rows in the table.</span></span>  
  
 <span data-ttu-id="715f6-421">*table_list_file*では、行数とテーブル名の間には 1 つ以上の空白がある場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="715f6-421">Note that there can be one or more spaces between the number of rows count and the preceding table name in the *table_list_file*.</span></span>  
  
 <span data-ttu-id="715f6-422">チューニング時間は 2 時間 (`-A 120`) で、出力は XML ファイルに書き込まれます (`-ox XMLTune.xml`)。</span><span class="sxs-lookup"><span data-stu-id="715f6-422">The tuning time is 2 hours (`-A 120`) and the output is written to an XML file (`-ox XMLTune.xml`).</span></span>  
  
```  
dta -D pubs -if pubs_wkld.sql -ox XMLTune.xml -A 120 -Tf table_list.txt  
```  
  
## <a name="see-also"></a><span data-ttu-id="715f6-423">参照</span><span class="sxs-lookup"><span data-stu-id="715f6-423">See Also</span></span>  
 <span data-ttu-id="715f6-424">[コマンドプロンプトユーティリティリファレンス &#40;データベースエンジン&#41;](../command-prompt-utility-reference-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="715f6-424">[Command Prompt Utility Reference &#40;Database Engine&#41;](../command-prompt-utility-reference-database-engine.md) </span></span>  
 [<span data-ttu-id="715f6-425">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="715f6-425">Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
