---
title: インメモリ OLTP をデモンストレーションする AdventureWorks の拡張機能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0186b7f2-cead-4203-8360-b6890f37cde8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73a87751aa6cd4734f81b60cdd87a62939ba4ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740315"
---
# <a name="extensions-to-adventureworks-to-demonstrate-in-memory-oltp"></a><span data-ttu-id="6447b-102">インメモリ OLTP を実証する AdventureWorks の拡張</span><span class="sxs-lookup"><span data-stu-id="6447b-102">Extensions to AdventureWorks to Demonstrate In-Memory OLTP</span></span>
    
## <a name="overview"></a><span data-ttu-id="6447b-103">概要</span><span class="sxs-lookup"><span data-stu-id="6447b-103">Overview</span></span>  
 <span data-ttu-id="6447b-104">このサンプルでは、 [!INCLUDE[hek_2](../includes/hek-2-md.md)] に含まれている [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]の新機能を紹介します。</span><span class="sxs-lookup"><span data-stu-id="6447b-104">This sample showcases the new [!INCLUDE[hek_2](../includes/hek-2-md.md)] feature, which is part of [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="6447b-105">このサンプルで取り上げるのは、新しいメモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャです。また、 [!INCLUDE[hek_2](../includes/hek-2-md.md)]のパフォーマンス上の利点も示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-105">It shows the new memory-optimized tables and natively-compiled stored procedures, and can be used to demonstrate performance benefits of [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6447b-106">SQL Server 2016 のこのトピックを表示するには、「 [メモリ内 OLTP を実証する AdventureWorks の拡張](https://msdn.microsoft.com/library/mt465764.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6447b-106">To view this topic for SQL Server 2016, see [Extensions to AdventureWorks to Demonstrate In-Memory OLTP](https://msdn.microsoft.com/library/mt465764.aspx)</span></span>  
  
 <span data-ttu-id="6447b-107">このサンプルは、AdventureWorks データベースの 5 つのテーブルをメモリ最適化テーブルに移行します。販売注文処理のデモ ワークロードも含まれています。</span><span class="sxs-lookup"><span data-stu-id="6447b-107">The sample migrates 5 tables in the AdventureWorks database to memory-optimized, and it includes a demo workload for sales order processing.</span></span> <span data-ttu-id="6447b-108">このデモ ワークロードを使用して、サーバーで [!INCLUDE[hek_2](../includes/hek-2-md.md)] を使用するパフォーマンス上の利点を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-108">You can use this demo workload to see the performance benefit of using [!INCLUDE[hek_2](../includes/hek-2-md.md)] on your server.</span></span>  
  
 <span data-ttu-id="6447b-109">サンプルの説明では、テーブルを [!INCLUDE[hek_2](../includes/hek-2-md.md)] に移行することによって生じるトレードオフについて触れ、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]のメモリ最適化テーブルでは (まだ) サポートされていない機能について記載しています。</span><span class="sxs-lookup"><span data-stu-id="6447b-109">In the description of the sample we discuss the tradeoffs that were made in migrating the tables to [!INCLUDE[hek_2](../includes/hek-2-md.md)] to account for the features that are not (yet) supported for memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="6447b-110">このサンプルのドキュメントは、次の内容で構成されています。</span><span class="sxs-lookup"><span data-stu-id="6447b-110">The documentation of this sample is structured as follows:</span></span>  
  
-   <span data-ttu-id="6447b-111">サンプルをインストールしてデモ ワークロードを実行するための[前提条件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="6447b-111">[Prerequisites](#Prerequisites) for installing the sample and running the demo workload</span></span>  
  
-   <span data-ttu-id="6447b-112">[AdventureWorksに基づくインメモリOLTPサンプルのインストール](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)する手順</span><span class="sxs-lookup"><span data-stu-id="6447b-112">Instructions for [Installing the In-Memory OLTP sample based on AdventureWorks](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)</span></span>  
  
-   <span data-ttu-id="6447b-113">[サンプルテーブルおよびプロシージャの説明](#Descriptionofthesampletablesandprocedures)-サンプルによって adventureworks に追加されたテーブルとプロシージャの説明 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 、および一部の adventureworks テーブルをメモリ最適化に移行する際の考慮事項についても説明します。</span><span class="sxs-lookup"><span data-stu-id="6447b-113">[Description of the sample tables and procedures](#Descriptionofthesampletablesandprocedures) - this includes descriptions of the tables and procedures added to AdventureWorks by the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample, as well as considerations for migrating some of the original AdventureWorks tables to memory-optimized</span></span>  
  
-   <span data-ttu-id="6447b-114">[デモワークロードを使用してパフォーマンス測定](#PerformanceMeasurementsusingtheDemoWorkload)を実行する手順-これには、ostress をインストールして実行する手順、ワークロードを実行するために使用するツール、およびデモワークロード自体を実行する手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6447b-114">Instructions for performing [Performance Measurements using the Demo Workload](#PerformanceMeasurementsusingtheDemoWorkload) - this includes instructions for installing and running ostress, a tool using for driving the workload, as well as running the demo workload itself</span></span>  
  
-   [<span data-ttu-id="6447b-115">サンプルにおけるメモリおよびディスク領域の使用率</span><span class="sxs-lookup"><span data-stu-id="6447b-115">Memory and Disk Space Utilization in the Sample</span></span>](#MemoryandDiskSpaceUtilizationintheSample)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6447b-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="6447b-116">Prerequisites</span></span>  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<span data-ttu-id="6447b-117">RTM-評価版、Developer edition、または Enterprise edition</span><span class="sxs-lookup"><span data-stu-id="6447b-117">RTM - Evaluation, Developer, or Enterprise edition</span></span>  
  
-   <span data-ttu-id="6447b-118">運用環境と仕様が似ているサーバー (パフォーマンス テスト用)。</span><span class="sxs-lookup"><span data-stu-id="6447b-118">For performance testing, a server with specifications similar to your production environment.</span></span> <span data-ttu-id="6447b-119">このサンプルでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に使用できるメモリが 16 GB 以上必要です。</span><span class="sxs-lookup"><span data-stu-id="6447b-119">For this particular sample you should have at least 16GB of memory available to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6447b-120">のハードウェアに関する一般的なガイドラインについ [!INCLUDE[hek_2](../includes/hek-2-md.md)] ては、次のブログ投稿を参照してください。[https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/](https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/)</span><span class="sxs-lookup"><span data-stu-id="6447b-120">For general guidelines on hardware for [!INCLUDE[hek_2](../includes/hek-2-md.md)], see the following blog post:[https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/](https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/)</span></span>  
  
##  <a name="installing-the-hek_2-sample-based-on-adventureworks"></a><a name="InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks"></a><span data-ttu-id="6447b-121">[!INCLUDE[hek_2](../includes/hek-2-md.md)]AdventureWorks に基づくサンプルのインストール</span><span class="sxs-lookup"><span data-stu-id="6447b-121">Installing the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample based on AdventureWorks</span></span>  
 <span data-ttu-id="6447b-122">サンプルをインストールするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-122">Follow these steps to install the sample:</span></span>  
  
1.  <span data-ttu-id="6447b-123">AdventureWorks2014 データベースの完全バックアップのアーカイブをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="6447b-123">Download the archive for the full backup of the AdventureWorks2014 database:</span></span>  
  
    1.  <span data-ttu-id="6447b-124">次のものを開き [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661) ます。</span><span class="sxs-lookup"><span data-stu-id="6447b-124">Open the following: [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661).</span></span>  
  
    2.  <span data-ttu-id="6447b-125">メッセージが表示されたら、ファイルをローカル フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="6447b-125">When prompted to save the file to a local folder.</span></span>  
  
2.  <span data-ttu-id="6447b-126">**AdventureWorks2014.bak** ファイルを C:\temp などのローカル フォルダーに解凍します。</span><span class="sxs-lookup"><span data-stu-id="6447b-126">Extract the **AdventureWorks2014.bak** file to a local folder, for example 'c:\temp'.</span></span>  
  
3.  <span data-ttu-id="6447b-127">[!INCLUDE[tsql](../includes/tsql-md.md)] または [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用して、データベース バックアップを復元します</span><span class="sxs-lookup"><span data-stu-id="6447b-127">Restore the database backup using [!INCLUDE[tsql](../includes/tsql-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="6447b-128">データ ファイルの対象フォルダーおよびファイル名を特定します。次に例を示します</span><span class="sxs-lookup"><span data-stu-id="6447b-128">Identify the target folder and filename for the data file, for example</span></span>  
  
         <span data-ttu-id="6447b-129">'h:\DATA\AdventureWorks2014_Data.mdf'</span><span class="sxs-lookup"><span data-stu-id="6447b-129">'h:\DATA\AdventureWorks2014_Data.mdf'</span></span>  
  
    2.  <span data-ttu-id="6447b-130">ログ ファイルの対象フォルダーおよびファイル名を特定します。次に例を示します</span><span class="sxs-lookup"><span data-stu-id="6447b-130">Identify the target folder and filename for the log file, for example</span></span>  
  
         <span data-ttu-id="6447b-131">'i:\DATA\AdventureWorks2014_log.ldf'</span><span class="sxs-lookup"><span data-stu-id="6447b-131">'i:\DATA\AdventureWorks2014_log.ldf'</span></span>  
  
        1.  <span data-ttu-id="6447b-132">ログ ファイルは、データ ファイルとは異なるドライブに配置します。最大限のパフォーマンスを実現するために、SSD、PCIe ストレージなど、待機時間の少ないドライブに配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6447b-132">The log file should be placed on a different drive than the data file, ideally a low latency drive such as an SSD or PCIe storage, for maximum performance.</span></span>  
  
     <span data-ttu-id="6447b-133">T-SQL スクリプトの例:</span><span class="sxs-lookup"><span data-stu-id="6447b-133">Example T-SQL script:</span></span>  
  
    ```  
    RESTORE DATABASE [AdventureWorks2014]   
      FROM DISK = N'C:\temp\AdventureWorks2014.bak'   
        WITH FILE = 1,    
      MOVE N'AdventureWorks2014_Data' TO N'h:\DATA\AdventureWorks2014_Data.mdf',    
      MOVE N'AdventureWorks2014_Log' TO N'i:\DATA\AdventureWorks2014_log.ldf'  
     GO  
    ```  
  
4.  <span data-ttu-id="6447b-134">データベース所有者を変更して、サーバーにログインします。それには、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のクエリ ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-134">Change the database owner to a login on your server, by running the following command in the query window of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:</span></span>  
  
    ```  
    ALTER AUTHORIZATION ON DATABASE::AdventureWorks2014 TO [<NewLogin>]  
    ```  
  
5.  <span data-ttu-id="6447b-135">サンプルスクリプト ' [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] rtm [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample. sql ' を[SQL Server 2014 RTM のインメモリ OLTP サンプル](https://go.microsoft.com/fwlink/?LinkID=396372)からローカルフォルダーにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="6447b-135">Download the sample script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql' from [SQL Server 2014 RTM In-Memory OLTP Sample](https://go.microsoft.com/fwlink/?LinkID=396372) to a local folder.</span></span>  
  
6.  <span data-ttu-id="6447b-136">スクリプト ' RTM Sample. sql ' の変数 ' checkpoint_files_location ' の値を更新して、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] チェックポイントファイルのターゲットの場所をポイントし [!INCLUDE[hek_2](../includes/hek-2-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6447b-136">Update the value for the variable 'checkpoint_files_location' in the script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql', to point to the target location for the [!INCLUDE[hek_2](../includes/hek-2-md.md)] checkpoint files.</span></span> <span data-ttu-id="6447b-137">チェックポイント ファイルは、シーケンシャル IO パフォーマンスに優れたドライブに配置します。</span><span class="sxs-lookup"><span data-stu-id="6447b-137">The checkpoint files should be placed on a drive with good sequential IO performance.</span></span>  
  
     <span data-ttu-id="6447b-138">AdventureWorks2014 データベースを指すように変数 'database_name' の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="6447b-138">Update the value for the variable 'database_name' to point to the AdventureWorks2014 database.</span></span>  
  
    1.  <span data-ttu-id="6447b-139">\'パス名の一部として円記号 (\) を含めるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6447b-139">Be sure to include the backslash '\' as part of the path name</span></span>  
  
    2.  <span data-ttu-id="6447b-140">例:</span><span class="sxs-lookup"><span data-stu-id="6447b-140">Example:</span></span>  
  
        ```  
        :setvar checkpoint_files_location "d:\DBData\"  
        ...  
        :setvar database_name "AdventureWorks2014"  
        ```  
  
7.  <span data-ttu-id="6447b-141">サンプル スクリプトを、以下の 2 つのいずれかの方法で実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-141">Execute the sample script, in one of two ways:</span></span>  
  
    1.  <span data-ttu-id="6447b-142">sqlcmd コマンド ライン ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-142">Using the sqlcmd command-line utility.</span></span> <span data-ttu-id="6447b-143">たとえば、スクリプトが含まれるフォルダーで、コマンド ライン プロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-143">For example, for example by running the following command from the command-line prompt in the folder containing the script:</span></span>  
  
        ```  
        sqlcmd -S . -E -i "ssSQL14 RTM hek_2 Sample.sql"  
        ```  
  
    2.  <span data-ttu-id="6447b-144">Management Studio を使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-144">Using Management Studio:</span></span>  
  
        1.  <span data-ttu-id="6447b-145">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] クエリウィンドウで "RTM Sample .sql" スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="6447b-145">Open the script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql' in a query window</span></span>  
  
        2.  <span data-ttu-id="6447b-146">AdventureWorks2014 データベースが含まれているターゲット サーバーに接続します</span><span class="sxs-lookup"><span data-stu-id="6447b-146">Connect to the target server that contains the database AdventureWorks2014</span></span>  
  
        3.  <span data-ttu-id="6447b-147">SQLCMD モードを有効にするには、[クエリ-> SQLCMD モード] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6447b-147">Enable SQLCMD Mode, by clicking on 'Query -> SQLCMD Mode'</span></span>  
  
        4.  <span data-ttu-id="6447b-148">[実行] ボタンをクリックしてスクリプトを実行します</span><span class="sxs-lookup"><span data-stu-id="6447b-148">Click the button 'Execute' to run the script</span></span>  
  
##  <a name="description-of-the-sample-tables-and-procedures"></a><a name="Descriptionofthesampletablesandprocedures"></a> <span data-ttu-id="6447b-149">サンプル テーブルおよびプロシージャの説明</span><span class="sxs-lookup"><span data-stu-id="6447b-149">Description of the sample tables and procedures</span></span>  
 <span data-ttu-id="6447b-150">サンプルでは、AdventureWorks の既存のテーブルに基づいて、製品および販売注文ごとに新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6447b-150">The sample creates new tables for products and sales orders, based on existing tables in AdventureWorks.</span></span> <span data-ttu-id="6447b-151">新しいテーブルのスキーマは既存のテーブルと似ていますが、以下に示すように、異なる点がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="6447b-151">The schema of the new tables is similar to the existing tables, with a few differences, as explained below.</span></span>  
  
 <span data-ttu-id="6447b-152">新しいメモリ最適化テーブルには、"_inmem" というサフィックスが付いています。</span><span class="sxs-lookup"><span data-stu-id="6447b-152">The new memory-optimized tables carry the suffix '_inmem'.</span></span> <span data-ttu-id="6447b-153">また、サンプルにはこれに対応するテーブルも含まれており、このテーブルには "_ondisk" というサフィックスが付いています。これらのテーブルを使用することで、システム上のメモリ最適化テーブルのパフォーマンスと、ディスク ベース テーブルのパフォーマンスを一対一で比較できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-153">The sample also includes corresponding tables carrying the suffix '_ondisk' - these tables can be used to make a one-to-one comparison between the performance of memory-optimized tables and disk-based tables on your system..</span></span>  
  
 <span data-ttu-id="6447b-154">パフォーマンスを比較するためにワークロードで使用されるメモリ最適化テーブルには完全持続性が適用され、その動作は完全にログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-154">Note that the memory-optimized tables used in the workload for performance comparison are fully durable and fully logged.</span></span> <span data-ttu-id="6447b-155">パフォーマンス向上を実現するために、持続性や信頼性が犠牲になることはありません。</span><span class="sxs-lookup"><span data-stu-id="6447b-155">They do not sacrifice durability or reliability to attain the performance gain.</span></span>  
  
 <span data-ttu-id="6447b-156">このサンプルの対象ワークロードは販売注文処理のワークロードです。また、製品および割引に関する情報も考慮します。</span><span class="sxs-lookup"><span data-stu-id="6447b-156">The target workload for this sample is sales order processing, where we consider also information about products and discounts.</span></span> <span data-ttu-id="6447b-157">このため、使用するのは、SalesOrderHeader、SalesOrderDetail、Product、SpecialOffer、SpecialOfferProduct の 5 つのテーブルです。</span><span class="sxs-lookup"><span data-stu-id="6447b-157">To this end, the table SalesOrderHeader, SalesOrderDetail, Product, SpecialOffer, and SpecialOfferProduct.</span></span>  
  
 <span data-ttu-id="6447b-158">2 つの新しいストアド プロシージャ、Sales.usp_InsertSalesOrder_inmem と Sales.usp_UpdateSalesOrderShipInfo_inmem は、販売注文を挿入し、指定された販売注文の出荷情報を更新するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-158">Two new stored procedures, Sales.usp_InsertSalesOrder_inmem and Sales.usp_UpdateSalesOrderShipInfo_inmem, are used to insert sales orders and to update the shipping information of a given sales order.</span></span>  
  
 <span data-ttu-id="6447b-159">新しいスキーマ "Demo" には、デモ ワークロードを実行するためのヘルパー テーブルとストアド プロシージャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6447b-159">The new schema 'Demo' contains helper tables and stored procedures to execute a demo workload.</span></span>  
  
 <span data-ttu-id="6447b-160">具体的には、 [!INCLUDE[hek_2](../includes/hek-2-md.md)] サンプルでは、次のオブジェクトが AdventureWorks に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-160">Concretely, the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample adds the following objects to AdventureWorks:</span></span>  
  
### <a name="tables-added-by-the-sample"></a><span data-ttu-id="6447b-161">サンプルによって追加されるテーブル</span><span class="sxs-lookup"><span data-stu-id="6447b-161">Tables added by the sample</span></span>  
  
#### <a name="the-new-tables"></a><span data-ttu-id="6447b-162">新しいテーブル</span><span class="sxs-lookup"><span data-stu-id="6447b-162">The New Tables</span></span>  
 <span data-ttu-id="6447b-163">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-163">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="6447b-164">販売注文に関するヘッダー情報。</span><span class="sxs-lookup"><span data-stu-id="6447b-164">Header information about sales orders.</span></span> <span data-ttu-id="6447b-165">このテーブルでは、各販売注文が 1 つの行に対応します。</span><span class="sxs-lookup"><span data-stu-id="6447b-165">Each sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="6447b-166">Sales.SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-166">Sales.SalesOrderDetail_inmem</span></span>  
  
-   <span data-ttu-id="6447b-167">販売注文の詳細。</span><span class="sxs-lookup"><span data-stu-id="6447b-167">Details of sales orders.</span></span> <span data-ttu-id="6447b-168">このテーブルでは、販売注文の各品目が 1 つの行に対応します。</span><span class="sxs-lookup"><span data-stu-id="6447b-168">Each line item of a sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="6447b-169">Sales.SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-169">Sales.SpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="6447b-170">特価品情報。各特価品に関連付けられた値引き率が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6447b-170">Information about special offers, including the discount percentage associated with each special offer.</span></span>  
  
 <span data-ttu-id="6447b-171">Sales.SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-171">Sales.SpecialOfferProduct_inmem</span></span>  
  
-   <span data-ttu-id="6447b-172">特価品と製品の間の参照テーブル。</span><span class="sxs-lookup"><span data-stu-id="6447b-172">Reference table between special offers and products.</span></span> <span data-ttu-id="6447b-173">各特価品が、0 個以上の製品を特徴付けることができます。また、0 個以上の特価品で、各製品を特徴付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="6447b-173">Each special offer can feature zero or more products, and each product can be featured in zero or more special offers.</span></span>  
  
 <span data-ttu-id="6447b-174">Production.Product_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-174">Production.Product_inmem</span></span>  
  
-   <span data-ttu-id="6447b-175">製品に関する情報 (表示価格を含む)。</span><span class="sxs-lookup"><span data-stu-id="6447b-175">Information about products, including their list price.</span></span>  
  
 <span data-ttu-id="6447b-176">Demo.DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="6447b-176">Demo.DemoSalesOrderDetailSeed</span></span>  
  
-   <span data-ttu-id="6447b-177">サンプル販売注文を作成するためにデモ ワークロードで使用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-177">Used in the demo workload to construct sample sales orders.</span></span>  
  
 <span data-ttu-id="6447b-178">ディスク ベース テーブルのバリエーション:</span><span class="sxs-lookup"><span data-stu-id="6447b-178">Disk-based variations of the tables:</span></span>  
  
-   <span data-ttu-id="6447b-179">Sales.SalesOrderHeader_ondisk</span><span class="sxs-lookup"><span data-stu-id="6447b-179">Sales.SalesOrderHeader_ondisk</span></span>  
  
-   <span data-ttu-id="6447b-180">Sales.SalesOrderDetail_ondisk</span><span class="sxs-lookup"><span data-stu-id="6447b-180">Sales.SalesOrderDetail_ondisk</span></span>  
  
-   <span data-ttu-id="6447b-181">Sales.SpecialOffer_ondisk</span><span class="sxs-lookup"><span data-stu-id="6447b-181">Sales.SpecialOffer_ondisk</span></span>  
  
-   <span data-ttu-id="6447b-182">Sales.SpecialOfferProduct_ondisk</span><span class="sxs-lookup"><span data-stu-id="6447b-182">Sales.SpecialOfferProduct_ondisk</span></span>  
  
-   <span data-ttu-id="6447b-183">Production.Product_ondisk</span><span class="sxs-lookup"><span data-stu-id="6447b-183">Production.Product_ondisk</span></span>  
  
#### <a name="differences-between-original-disk-based-and-the-and-new-memory-optimized-tables"></a><span data-ttu-id="6447b-184">元のディスク ベース テーブルと新しいメモリ最適化テーブルの違い</span><span class="sxs-lookup"><span data-stu-id="6447b-184">Differences between original disk-based and the and new memory-optimized tables</span></span>  
 <span data-ttu-id="6447b-185">このサンプルで提供されている新しいテーブルでは、その大部分で、元のテーブルと同じ列および同じデータ型が使用されています。</span><span class="sxs-lookup"><span data-stu-id="6447b-185">For the most part, the new tables introduced by this sample use the same columns and the same data types as the original tables.</span></span> <span data-ttu-id="6447b-186">しかし、違う点もいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="6447b-186">However, there are a few differences.</span></span> <span data-ttu-id="6447b-187">ここでは、その違いと、こうした変更の妥当性について説明します。</span><span class="sxs-lookup"><span data-stu-id="6447b-187">We list the differences below, along with a rationale for the changes.</span></span>  
  
 <span data-ttu-id="6447b-188">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-188">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="6447b-189">*既定の制約* はメモリ最適化テーブルでサポートされ、そのほとんどがそのまま移行されています。</span><span class="sxs-lookup"><span data-stu-id="6447b-189">*Default constraints* are supported for memory-optimized tables, and most default constraints we migrated as is.</span></span> <span data-ttu-id="6447b-190">ただし、元の Sales.SalesOrderHeader テーブルには、現在の日付を取得する既定の制約が 2 つあります。OrderDate 列の制約と ModifiedDate 列の制約です。</span><span class="sxs-lookup"><span data-stu-id="6447b-190">However, the original table Sales.SalesOrderHeader contains two default constraints that retrieve the current date, for the columns OrderDate and ModifiedDate.</span></span> <span data-ttu-id="6447b-191">コンカレンシーが多くスループットが高い注文処理ワークロードでは、グローバル リソースが競合ポイントになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6447b-191">In a high throughput order processing workload with a lot of concurrency, any global resource can become a point of contention.</span></span> <span data-ttu-id="6447b-192">たとえば、このようなグローバル リソースにはシステム時刻があります。販売注文を挿入する [!INCLUDE[hek_2](../includes/hek-2-md.md)] ワークロードを実行しているとき、特に、販売注文ヘッダーおよび販売注文の詳細に含まれる複数の列に対して、システム時刻を取得する必要がある場合は、このシステム時刻がボトルネックになることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="6447b-192">System time is such a global resource, and we have observed that it can become a bottleneck when running an [!INCLUDE[hek_2](../includes/hek-2-md.md)] workload that inserts sales orders, in particular if the system time needs to be retrieved for multiple columns in the sales order header, as well as the sales order details.</span></span> <span data-ttu-id="6447b-193">このサンプルでは、挿入された販売注文ごとに 1 度だけシステム時刻を取得することで問題に対処します。そして、ストアド プロシージャ Sales.usp_InsertSalesOrder_inmem で、SalesOrderHeader_inmem と SalesOrderDetail_inmem にある datetime 列に対して、その値を使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-193">The problem is addressed in this sample by retrieving the system time only once for each sales order that is inserted, and use that value for the datetime columns in SalesOrderHeader_inmem and SalesOrderDetail_inmem, in the stored procedure Sales.usp_InsertSalesOrder_inmem.</span></span>  
  
-   <span data-ttu-id="6447b-194">*エイリアス UDT* - 元のテーブルでは、2 つのエイリアス ユーザー定義データ型 (UDT) が使用されます。1 つは dbo.OrderNumber で、これは PurchaseOrderNumber 列に対して使用されます。もう 1 つは dbo.AccountNumber で、AccountNumber 列に対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-194">*Alias UDTs* - The original table uses two alias user-defined data types (UDTs) dbo.OrderNumber and dbo.AccountNumber, for the columns PurchaseOrderNumber and AccountNumber, respectively.</span></span> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="6447b-195">では、メモリ最適化テーブルに対してエイリアス UDT がサポートされていません。したがって、新しいテーブルでは、システム データ型 nvarchar(25) と nvarchar(15) が個別に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-195">does not support alias UDT for memory-optimized tables, thus the new tables use system data types nvarchar(25) and nvarchar(15), respectively.</span></span>  
  
-   <span data-ttu-id="6447b-196">*インデックス キーの NULL 値を許容する列* - 元のテーブルでは、SalesPersonID 列は NULL 値を許容しますが、新しいテーブルのこの列では NULL 値が許容されず、既定の制約として値 -1 が設定されています。</span><span class="sxs-lookup"><span data-stu-id="6447b-196">*Nullable columns in index keys* - In the original table, the column SalesPersonID is nullable, while in the new tables the column is not nullable and has a default constraint with value (-1).</span></span> <span data-ttu-id="6447b-197">これは、メモリ最適化テーブルのインデックスでは、インデックス キーに NULL 値を許容する列を使用できないためです。この場合は、-1 が NULL のサロゲートです。</span><span class="sxs-lookup"><span data-stu-id="6447b-197">This is because indexes on memory-optimized tables cannot have nullable columns in the index key; -1 is a surrogate for NULL in this case.</span></span>  
  
-   <span data-ttu-id="6447b-198">*計算列* - [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] のメモリ最適化テーブルでは計算列がサポートされていないため、計算列である SalesOrderNumber および TotalDue は省略されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-198">*Computed columns* - The computed columns SalesOrderNumber and TotalDue are omitted, as [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] does not support computed columns in memory-optimized tables.</span></span> <span data-ttu-id="6447b-199">新しい Sales.vSalesOrderHeader_extended_inmem ビューには、SalesOrderNumber 列と TotalDue 列が反映されています。</span><span class="sxs-lookup"><span data-stu-id="6447b-199">The new view Sales.vSalesOrderHeader_extended_inmem reflects the columns SalesOrderNumber and TotalDue.</span></span> <span data-ttu-id="6447b-200">したがって、これらの列が必要な場合は、このビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-200">Therefore, you can use this view if these columns are needed.</span></span>  
  
-   <span data-ttu-id="6447b-201">"外部キー制約"\*\* は、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]のメモリ最適化テーブルではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6447b-201">*Foreign key constraints* are not supported for memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="6447b-202">また、SalesOrderHeader_inmem はサンプル ワークロードのホット テーブルであり、外部キー制約には、すべての DML 操作に対して追加の処理が必要です。これは、このテーブルには、この制約で参照される他のすべてのテーブル内の参照が必要だからです。</span><span class="sxs-lookup"><span data-stu-id="6447b-202">In addition, SalesOrderHeader_inmem is a hot table in the example workload, and foreign keys constraints require additional processing for all DML operations, as it requires lookups in all the other tables referenced in these constraints.</span></span> <span data-ttu-id="6447b-203">したがって、アプリによって参照整合性が確保されているものと見なされ、行の挿入時には参照整合性は検証されません。</span><span class="sxs-lookup"><span data-stu-id="6447b-203">Therefore, the assumption is that the app ensures referential integrity, and referential integrity is not validated when rows are inserted.</span></span> <span data-ttu-id="6447b-204">このテーブルのデータの参照整合性は、ストアド プロシージャ dbo.usp_ValidateIntegrity を使用して、次のスクリプトで確認できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-204">Referential integrity for the data in this table can be verified using the stored procedure dbo.usp_ValidateIntegrity, using the following script:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="6447b-205">"CHECK 制約"\*\* は、SQL Server 2014 のメモリ最適化テーブルではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6447b-205">*Check constraints* are not supported for memory-optimized tables in SQ Server 2014.</span></span> <span data-ttu-id="6447b-206">ドメインの整合性は、次のスクリプトを使用して、参照整合性と共に検証されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-206">Domain integrity is validated along with referential integrity using this script:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="6447b-207">*Rowguid* - rowguid 列は省略されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-207">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="6447b-208">uniqueidentifier はメモリ最適化テーブルでサポートされますが、ROWGUIDCOL オプションは [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6447b-208">While uniqueidentifier is support for memory-optimized tables, the option ROWGUIDCOL is not supported in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="6447b-209">この種類の列は、通常、マージ レプリケーション、または filestream 列を持つテーブルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-209">Columns of this kind are typically used for either merge replication or tables that have filestream columns.</span></span> <span data-ttu-id="6447b-210">このサンプルには、どちらも含まれていません。</span><span class="sxs-lookup"><span data-stu-id="6447b-210">This sample includes neither.</span></span>  
  
 <span data-ttu-id="6447b-211">Sales.SalesOrderDetail</span><span class="sxs-lookup"><span data-stu-id="6447b-211">Sales.SalesOrderDetail</span></span>  
  
-   <span data-ttu-id="6447b-212">"*既定の制約*" - SalesOrderHeader と同様、システムの日付/時刻を必要とする既定の制約は移行されません。現在のシステムの日付/時刻の挿入は、販売注文を挿入するストアド プロシージャによる初回挿入時に行われます。</span><span class="sxs-lookup"><span data-stu-id="6447b-212">*Default constraints* - similar to SalesOrderHeader, the default constraint requiring the system date/time is not migrated, instead the stored procedure inserting sales orders takes care of inserting the current system date/time on first insert.</span></span>  
  
-   <span data-ttu-id="6447b-213">"*計算列*" - [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] のメモリ最適化テーブルでは計算列がサポートされていないため、計算列である LineTotal は計算列としては移行されませんでした。</span><span class="sxs-lookup"><span data-stu-id="6447b-213">*Computed columns* - the computed column LineTotal was not migrated as computed columns are not supported with memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="6447b-214">この列にアクセスするには、Sales.vSalesOrderDetail_extended_inmem ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-214">To access this column use the view Sales.vSalesOrderDetail_extended_inmem.</span></span>  
  
-   <span data-ttu-id="6447b-215">*Rowguid* - rowguid 列は省略されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-215">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="6447b-216">詳細については、SalesOrderHeader テーブルの説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-216">For details see the description for the table SalesOrderHeader.</span></span>  
  
-   <span data-ttu-id="6447b-217">"CHECK" \*\* 制約および "外部キー" \*\* 制約については、SalesOrderHeader の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-217">For *check* and *foreign key* constraints see the description of SalesOrderHeader.</span></span> <span data-ttu-id="6447b-218">次のスクリプトを使用すると、このテーブルのドメインと参照整合性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-218">The following script can be used to verify domain and referential integrity for this table:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
 <span data-ttu-id="6447b-219">Production.Product</span><span class="sxs-lookup"><span data-stu-id="6447b-219">Production.Product</span></span>  
  
-   <span data-ttu-id="6447b-220">"*エイリアス UDT*" - 元のテーブルでは、ユーザー定義データ型 dbo.Flag が使用されます。これは、システム データ型 bit と同じです。</span><span class="sxs-lookup"><span data-stu-id="6447b-220">*Alias UDTs* - the original table uses the user-defined data type dbo.Flag, which is equivalent to the system data type bit.</span></span> <span data-ttu-id="6447b-221">移行したテーブルでは、代わりに bit データ型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-221">The migrated table uses the bit data type instead.</span></span>  
  
-   <span data-ttu-id="6447b-222">*BIN2 collation* -列名と productnumber は、インデックスキーに含まれます。したがって、では BIN2 照合順序を持つ必要があり [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6447b-222">*BIN2 collation* - The columns Name and ProductNumber are included in index keys, and must thus have BIN2 collations in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="6447b-223">ここでは、アプリケーションが、照合順序の詳細 (大文字と小文字を区別など) に依存しないものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="6447b-223">Here, the assumption is that the app does not rely on collation specifics, like case insensitivity.</span></span>  
  
-   <span data-ttu-id="6447b-224">*Rowguid* - rowguid 列は省略されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-224">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="6447b-225">詳細については、SalesOrderHeader テーブルの説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-225">For details see the description for the table SalesOrderHeader.</span></span>  
  
-   <span data-ttu-id="6447b-226">"UNIQUE 制約"\*\*, \*\* 、および "外部キー制約" \*\* are accounted for in two ways: the stored procedures Product.usp_InsertProduct_inmem 、および "外部キー制約" Product.usp_DeleteProduct_inmem can be used to insert 、および "外部キー制約" delete products; these procedures validate domain 、および "外部キー制約" referential integrity, 、および "外部キー制約" will fail if integrity is violated.</span><span class="sxs-lookup"><span data-stu-id="6447b-226">*Unique*, *Check* and *Foreign Key constraints* are accounted for in two ways: the stored procedures Product.usp_InsertProduct_inmem and Product.usp_DeleteProduct_inmem can be used to insert and delete products; these procedures validate domain and referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="6447b-227">次のスクリプトを使用して、ドメインと参照整合性をそのままの状態で検証することもできます。</span><span class="sxs-lookup"><span data-stu-id="6447b-227">In addition, the follow script can be used to validate domain and referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Production.Product')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
    -   <span data-ttu-id="6447b-228">ストアド プロシージャ usp_InsertProduct_inmem および usp_DeleteProduct_inmem では、移行したテーブル間の外部キーのみが考慮されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-228">Note that the store procedures usp_InsertProduct_inmem and usp_DeleteProduct_inmem consider only foreign keys between the migrated tables.</span></span> <span data-ttu-id="6447b-229">他の ProductModel テーブル、ProductSubcategory テーブル、および UnitMeasure テーブルへの参照は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="6447b-229">References to other tables ProductModel, ProductSubcategory, and UnitMeasure are not considered.</span></span>  
  
 <span data-ttu-id="6447b-230">Sales.SpecialOffer</span><span class="sxs-lookup"><span data-stu-id="6447b-230">Sales.SpecialOffer</span></span>  
  
-   <span data-ttu-id="6447b-231">"CHECK 制約"\*\* と "外部キー制約" \*\* are accounted for in two ways: the stored procedures Sales.usp_InsertSpecialOffer_inmem と "外部キー制約" Sales.usp_DeleteSpecialOffer_inmem can be used to insert と "外部キー制約" delete special offers; these procedures validate domain と "外部キー制約" referential integrity, と "外部キー制約" will fail if integrity is violated.</span><span class="sxs-lookup"><span data-stu-id="6447b-231">*Check* and *Foreign Key constraints* are accounted for in two ways: the stored procedures Sales.usp_InsertSpecialOffer_inmem and Sales.usp_DeleteSpecialOffer_inmem can be used to insert and delete special offers; these procedures validate domain and referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="6447b-232">次のスクリプトを使用して、ドメインと参照整合性をそのままの状態で検証することもできます。</span><span class="sxs-lookup"><span data-stu-id="6447b-232">In addition, the follow script can be used to validate domain and referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SpecialOffer_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="6447b-233">*Rowguid* - rowguid 列は省略されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-233">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="6447b-234">詳細については、SalesOrderHeader テーブルの説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-234">For details see the description for the table SalesOrderHeader.</span></span>  
  
 <span data-ttu-id="6447b-235">Sales.SpecialOfferProduct</span><span class="sxs-lookup"><span data-stu-id="6447b-235">Sales.SpecialOfferProduct</span></span>  
  
-   <span data-ttu-id="6447b-236">"外部キー制約"\*\* は、2 つの方法で説明されます。ストアド プロシージャ Sales.usp_InsertSpecialOfferProduct_inmem を使用すると、特価品と製品の関係を挿入できます。このプロシージャは参照整合性を検証し、整合性に違反すると失敗します。</span><span class="sxs-lookup"><span data-stu-id="6447b-236">*Foreign Key constraints* are accounted for in two ways: the stored procedure Sales.usp_InsertSpecialOfferProduct_inmem can be used to insert relationships between special offers and products; this procedures validates referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="6447b-237">次のスクリプトを使用して、参照整合性をそのままの状態で検証することもできます。</span><span class="sxs-lookup"><span data-stu-id="6447b-237">In addition, the follow script can be used to validate referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SpecialOfferProduct_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="6447b-238">*Rowguid* - rowguid 列は省略されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-238">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="6447b-239">詳細については、SalesOrderHeader テーブルの説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-239">For details see the description for the table SalesOrderHeader.</span></span>  
  
#### <a name="considerations-for-indexes-on-memory-optimized-tables"></a><span data-ttu-id="6447b-240">メモリ最適化テーブルのインデックスに関する注意点</span><span class="sxs-lookup"><span data-stu-id="6447b-240">Considerations for indexes on memory-optimized tables</span></span>  
 <span data-ttu-id="6447b-241">メモリ最適化テーブルのベースライン インデックスは、非クラスター化インデックスです。このインデックスでは、ポイント参照 (等値述語に対するインデックスのシーク)、範囲スキャン (非等値述語に対するインデックスのシーク)、フル インデックス スキャン、および並べ替えられたスキャンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6447b-241">The baseline index for memory-optimized tables is the NONCLUSTERED index, which supports point lookups (index seek on equality predicate), range scans (index seek in inequality predicate), full index scans, and ordered scans.</span></span> <span data-ttu-id="6447b-242">また、インデックス キーの先頭列での検索もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6447b-242">In addition, NONCLUSTERED indexes support searching on leading columns of the index key.</span></span> <span data-ttu-id="6447b-243">実際、メモリ最適化された非クラスター化インデックスでは、ディスク ベースの非クラスター化インデックスでサポートされる操作が、後方スキャンを除き、すべてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6447b-243">In fact memory-optimized NONCLUSTERED indexes support all the operations supported by disk-based NONCLUSTERED indexes, with the only exception being backward scans.</span></span> <span data-ttu-id="6447b-244">したがって、非クラスター化インデックスは、インデックスとしては安全な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="6447b-244">Therefore, using NONCLUSTERED indexes is a safe choice for your indexes.</span></span>  
  
 <span data-ttu-id="6447b-245">ハッシュ インデックスを使用すると、ワークロードをさらに最適化できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-245">HASH indexes are can be used to further optimize the workload.</span></span> <span data-ttu-id="6447b-246">これは、特にポイント参照と行挿入に合わせて最適化されています。</span><span class="sxs-lookup"><span data-stu-id="6447b-246">They are particularly optimized for point lookups and row inserts.</span></span> <span data-ttu-id="6447b-247">ただし、範囲スキャン、並べ替えられたスキャン、または先頭のインデックス キー列での検索がサポートされていないことを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6447b-247">However, one must consider that they do not support range scans, ordered scans, or search on leading index key columns.</span></span> <span data-ttu-id="6447b-248">したがって、このインデックスを使用するときは注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="6447b-248">Therefore, care needs to be taken when using these indexes.</span></span> <span data-ttu-id="6447b-249">また、作成時に bucket_count を指定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="6447b-249">In addition, it is necessary to specify the bucket_count at create time.</span></span> <span data-ttu-id="6447b-250">一般的にはインデックス キー値の数の 1 ～ 2 倍に設定しますが、多めに設定しても通常は問題ありません。</span><span class="sxs-lookup"><span data-stu-id="6447b-250">It should usually be set at between one and two times the number of index key values, but overestimating is usually not a problem.</span></span>  
  
 <span data-ttu-id="6447b-251">詳細については、オンライン ブックの [インデックスのガイドライン](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) 、および [適切な bucket_count の選択](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx)に関するガイドラインをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6447b-251">See Books Online for more details about [index guidelines](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) and guidelines for [choosing the right bucket_count](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="6447b-252">移行したテーブルのインデックスは、販売注文処理のデモ ワークロードに合わせて調整されています。</span><span class="sxs-lookup"><span data-stu-id="6447b-252">The indexes on the migrated tables have been tuned for the demo sales order processing workload.</span></span> <span data-ttu-id="6447b-253">ワークロードは、Sales.SalesOrderHeader_inmem テーブルおよび Sales.SalesOrderDetail_inmem テーブルの挿入とポイント参照のほか、Production.Product_inmem テーブルおよび Sales.SpecialOffer_inmem テーブルの主キー列のポイント参照にも依存します。</span><span class="sxs-lookup"><span data-stu-id="6447b-253">The workload relies on inserts and point lookups in the tables Sales.SalesOrderHeader_inmem and Sales.SalesOrderDetail_inmem, and it also relies on point lookups on the primary key columns in the tables Production.Product_inmem and Sales.SpecialOffer_inmem.</span></span>  
  
 <span data-ttu-id="6447b-254">Sales.SalesOrderHeader_inmem には 3 つのインデックスがあります。このインデックスは、パフォーマンス上の理由から、また、並べ替えられたスキャンと範囲スキャンがワークロードに不要であることから、すべてハッシュ インデックスです。</span><span class="sxs-lookup"><span data-stu-id="6447b-254">Sales.SalesOrderHeader_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="6447b-255">(SalesOrderID) のハッシュ インデックス: 予測される販売注文数は 1,000 万であるため、bucket_count は 1,000 万です (1,600 万まで切り上げ)</span><span class="sxs-lookup"><span data-stu-id="6447b-255">HASH index on (SalesOrderID): bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="6447b-256">(SalesPersonID) のハッシュ インデックス: bucket_count は 100 万です。</span><span class="sxs-lookup"><span data-stu-id="6447b-256">HASH index on (SalesPersonID): bucket_count is 1 million.</span></span> <span data-ttu-id="6447b-257">提供されたデータ セットに含まれる販売員は多くありませんが、これにより将来の成長に対応できます。さらに、bucket_count のサイズが超過しても、ポイント参照のパフォーマンスが低下することはありません。</span><span class="sxs-lookup"><span data-stu-id="6447b-257">The data set provided does not have a lot of sales persons, but this allows for future growth, plus you don't pay a performance penalty for point lookups if the bucket_count is oversized.</span></span>  
  
-   <span data-ttu-id="6447b-258">(CustomerID) のハッシュ インデックス: bucket_count は 100 万です。</span><span class="sxs-lookup"><span data-stu-id="6447b-258">HASH index on (CustomerID): bucket_count is 1 million.</span></span> <span data-ttu-id="6447b-259">提供されたデータ セットに含まれる顧客は多くありませんが、これにより将来の成長に対応できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-259">The data set provided does not have a lot of customers, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="6447b-260">Sales.SalesOrderDetail_inmem には 3 つのインデックスがあります。このインデックスは、パフォーマンス上の理由から、また、並べ替えられたスキャンと範囲スキャンがワークロードに不要であることから、すべてハッシュ インデックスです。</span><span class="sxs-lookup"><span data-stu-id="6447b-260">Sales.SalesOrderDetail_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="6447b-261">(SalesOrderID、SalesOrderDetailID) のハッシュ インデックス: これは主キー インデックスです。(SalesOrderID、SalesOrderDetailID) での参照頻度が低くなりますが、このキーのハッシュ インデックスを使用すると行挿入の速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="6447b-261">HASH index on (SalesOrderID, SalesOrderDetailID): this is the primary key index, and even though lookups on (SalesOrderID, SalesOrderDetailID) will be infrequent, using a hash index for the key speeds up row inserts.</span></span> <span data-ttu-id="6447b-262">bucket_count は 5,000 万です (6,700 万まで切り上げ)。つまり、予測される販売注文数は 1,000 万で、各注文の平均品目数が 5 品目になるように調整されます</span><span class="sxs-lookup"><span data-stu-id="6447b-262">The bucket_count is sized at 50 million (rounded up to 67 million): the expected number of sales orders is 10 million, and this is sized to have an average of 5 items per order</span></span>  
  
-   <span data-ttu-id="6447b-263">(SalesOrderID) のハッシュ インデックス: 販売注文による参照が頻繁に行われます。1 つの注文に対応するすべての品目を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6447b-263">HASH index on (SalesOrderID): lookups by sales order are frequent: you will want to find all the line items corresponding to a single order.</span></span>  <span data-ttu-id="6447b-264">予測される販売注文数は 1,000 万であるため、bucket_count は 1,000 万です (1,600 万まで切り上げ)</span><span class="sxs-lookup"><span data-stu-id="6447b-264">bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="6447b-265">(ProductID) のハッシュ インデックス: bucket_count は 100 万です。</span><span class="sxs-lookup"><span data-stu-id="6447b-265">HASH index on (ProductID): bucket_count is 1 million.</span></span> <span data-ttu-id="6447b-266">提供されたデータ セットに含まれる製品は多くありませんが、これにより将来の成長に対応できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-266">The data set provided does not have a lot of product, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="6447b-267">Production.Product_inmem には 3 つのインデックスがあります</span><span class="sxs-lookup"><span data-stu-id="6447b-267">Production.Product_inmem has three indexes</span></span>  
  
-   <span data-ttu-id="6447b-268">(ProductID) のハッシュ インデックス: ProductID での参照はデモ ワークロードのクリティカル パスに含まれるため、これはハッシュ インデックスです</span><span class="sxs-lookup"><span data-stu-id="6447b-268">HASH index on (ProductID): lookups on ProductID are in the critical path for the demo workload, therefore this is a hash index</span></span>  
  
-   <span data-ttu-id="6447b-269">(Name) の非クラスター化インデックス: これにより、製品名に対して、並べ替えられたスキャンを実行できます</span><span class="sxs-lookup"><span data-stu-id="6447b-269">NONCLUSTERED index on (Name): this will allow ordered scans of product names</span></span>  
  
-   <span data-ttu-id="6447b-270">(ProductNumber) の非クラスター化インデックス: これにより、製品番号に対して、並べ替えられたスキャンを実行できます</span><span class="sxs-lookup"><span data-stu-id="6447b-270">NONCLUSTERED index on (ProductNumber): this will allow ordered scans of product numbers</span></span>  
  
 <span data-ttu-id="6447b-271">Sales.SpecialOffer_inmem の (SpecialOfferID) には、ハッシュ インデックスが 1 つあります。特価品のポイント参照は、デモ ワークロードでは重要です。</span><span class="sxs-lookup"><span data-stu-id="6447b-271">Sales.SpecialOffer_inmem has one HASH index on (SpecialOfferID): point lookups of special offers are in the critical part of the demo workload.</span></span> <span data-ttu-id="6447b-272">bucket_count は 100 万です。これにより、将来の成長に対応できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-272">The bucket_count is sized at 1 million to allow for future growth.</span></span>  
  
 <span data-ttu-id="6447b-273">Sales.SpecialOfferProduct_inmem は、デモ ワークロードでは参照されません。したがって、このテーブルでは、ハッシュ インデックスを使用してワークロードを最適化する必要はありません。(SpecialOfferID、ProductID) および (ProductID) のインデックスは非クラスター化インデックスです。</span><span class="sxs-lookup"><span data-stu-id="6447b-273">Sales.SpecialOfferProduct_inmem is not referenced in the demo workload, and thus there is no apparent need to use hash indexes on this table to optimize the workload - the indexes on (SpecialOfferID, ProductID) and (ProductID) are NONCLUSTERED.</span></span>  
  
 <span data-ttu-id="6447b-274">上記で挙げた bucket_count の中にはサイズ超過しているものがありますが、SalesOrderHeader_inmem と SalesOrderDetail_inmem のインデックスの bucket_count は違います。つまり、これらの bucket_count のサイズは、1,000 万個の販売注文を対象にしています。</span><span class="sxs-lookup"><span data-stu-id="6447b-274">Notice that in the above some of the bucket_counts are over-sized, but not the bucket_counts for the indexes on SalesOrderHeader_inmem and SalesOrderDetail_inmem: they are sized for just 10 million sales orders.</span></span> <span data-ttu-id="6447b-275">その目的は、使用できるメモリ容量が少ないシステムにサンプルをインストールできるようにすることですが、この場合、メモリ不足になるとデモ ワークロードは失敗します。</span><span class="sxs-lookup"><span data-stu-id="6447b-275">This was done to allow installing the sample on systems with low memory availability, although in those cases the demo workload will fail with out-of-memory.</span></span> <span data-ttu-id="6447b-276">1,000 万を超える販売注文を適切に処理する必要がある場合は、必要に応じてバケット数を増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="6447b-276">If you do want to scale well beyond 10 million sales orders, feel free to increase the bucket counts accordingly.</span></span>  
  
#### <a name="considerations-for-memory-utilization"></a><span data-ttu-id="6447b-277">メモリ使用率に関する注意点</span><span class="sxs-lookup"><span data-stu-id="6447b-277">Considerations for memory utilization</span></span>  
 <span data-ttu-id="6447b-278">デモ ワークロードの実行前および実行後のサンプル データベースのメモリ使用について、セクション「 [メモリ最適化テーブルのメモリ使用率](#Memoryutilizationforthememory-optimizedtables)」で説明しています。</span><span class="sxs-lookup"><span data-stu-id="6447b-278">Memory utilization in the sample database, both before and after running the demo workload, is discussed in the Section [Memory utilization for the memory-optimized tables](#Memoryutilizationforthememory-optimizedtables).</span></span>  
  
### <a name="stored-procedures-added-by-the-sample"></a><span data-ttu-id="6447b-279">サンプルによって追加されたストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="6447b-279">Stored Procedures added by the sample</span></span>  
 <span data-ttu-id="6447b-280">販売注文を挿入するストアド プロシージャと、出荷情報の詳細を更新するストアド プロシージャの 2 つの主要ストアド プロシージャを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-280">The two key stored procedures for inserting sales order and updating shipping details are as follows:</span></span>  
  
-   <span data-ttu-id="6447b-281">Sales.usp_InsertSalesOrder_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-281">Sales.usp_InsertSalesOrder_inmem</span></span>  
  
    -   <span data-ttu-id="6447b-282">新しい販売注文をデータベースに挿入し、その販売注文の SalesOrderID を出力します。</span><span class="sxs-lookup"><span data-stu-id="6447b-282">Inserts a new sales order in the database and outputs the SalesOrderID for that sales order.</span></span> <span data-ttu-id="6447b-283">入力パラメーターとして、販売注文ヘッダーの詳細と注文の品目を取得します。</span><span class="sxs-lookup"><span data-stu-id="6447b-283">As input parameters it takes details for the sales order header, as well as the line items in the order.</span></span>  
  
    -   <span data-ttu-id="6447b-284">出力パラメーター:</span><span class="sxs-lookup"><span data-stu-id="6447b-284">Output parameter:</span></span>  
  
        -   <span data-ttu-id="6447b-285">@SalesOrderID int - 挿入された販売注文の SalesOrderID</span><span class="sxs-lookup"><span data-stu-id="6447b-285">@SalesOrderID int - the SalesOrderID for the sales order that was just inserted</span></span>  
  
    -   <span data-ttu-id="6447b-286">入力パラメーター (必須):</span><span class="sxs-lookup"><span data-stu-id="6447b-286">Input parameters (required):</span></span>  
  
        -   <span data-ttu-id="6447b-287">@DueDate datetime2</span><span class="sxs-lookup"><span data-stu-id="6447b-287">@DueDate datetime2</span></span>  
  
        -   <span data-ttu-id="6447b-288">@CustomerID int</span><span class="sxs-lookup"><span data-stu-id="6447b-288">@CustomerID int</span></span>  
  
        -   <span data-ttu-id="6447b-289">@BillToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="6447b-289">@BillToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="6447b-290">@ShipToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="6447b-290">@ShipToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="6447b-291">@ShipMethodID [int]</span><span class="sxs-lookup"><span data-stu-id="6447b-291">@ShipMethodID [int]</span></span>  
  
        -   <span data-ttu-id="6447b-292">@SalesOrderDetails Sales.SalesOrderDetailType_inmem - 注文の品目が含まれる TVP</span><span class="sxs-lookup"><span data-stu-id="6447b-292">@SalesOrderDetails Sales.SalesOrderDetailType_inmem - TVP that contains the line items of the order</span></span>  
  
    -   <span data-ttu-id="6447b-293">入力パラメーター (省略可能):</span><span class="sxs-lookup"><span data-stu-id="6447b-293">Input parameters (optional):</span></span>  
  
        -   <span data-ttu-id="6447b-294">@Status [tinyint]</span><span class="sxs-lookup"><span data-stu-id="6447b-294">@Status [tinyint]</span></span>  
  
        -   <span data-ttu-id="6447b-295">@OnlineOrderFlag [bit]</span><span class="sxs-lookup"><span data-stu-id="6447b-295">@OnlineOrderFlag [bit]</span></span>  
  
        -   <span data-ttu-id="6447b-296">@PurchaseOrderNumber [nvarchar](25\)</span><span class="sxs-lookup"><span data-stu-id="6447b-296">@PurchaseOrderNumber [nvarchar](25\)</span></span>  
  
        -   <span data-ttu-id="6447b-297">@AccountNumber [nvarchar](15\)</span><span class="sxs-lookup"><span data-stu-id="6447b-297">@AccountNumber [nvarchar](15\)</span></span>  
  
        -   <span data-ttu-id="6447b-298">@SalesPersonID [int]</span><span class="sxs-lookup"><span data-stu-id="6447b-298">@SalesPersonID [int]</span></span>  
  
        -   <span data-ttu-id="6447b-299">@TerritoryID [int]</span><span class="sxs-lookup"><span data-stu-id="6447b-299">@TerritoryID [int]</span></span>  
  
        -   <span data-ttu-id="6447b-300">@CreditCardID [int]</span><span class="sxs-lookup"><span data-stu-id="6447b-300">@CreditCardID [int]</span></span>  
  
        -   <span data-ttu-id="6447b-301">@CreditCardApprovalCode [varchar](15\)</span><span class="sxs-lookup"><span data-stu-id="6447b-301">@CreditCardApprovalCode [varchar](15\)</span></span>  
  
        -   <span data-ttu-id="6447b-302">@CurrencyRateID [int]</span><span class="sxs-lookup"><span data-stu-id="6447b-302">@CurrencyRateID [int]</span></span>  
  
        -   <span data-ttu-id="6447b-303">@Comment nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="6447b-303">@Comment nvarchar(128)</span></span>  
  
-   <span data-ttu-id="6447b-304">Sales.usp_UpdateSalesOrderShipInfo_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-304">Sales.usp_UpdateSalesOrderShipInfo_inmem</span></span>  
  
    -   <span data-ttu-id="6447b-305">指定された販売注文の出荷情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="6447b-305">Update the shipping information for a given sales order.</span></span> <span data-ttu-id="6447b-306">これにより、販売注文のすべての品目の出荷情報も更新されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-306">This will also update the shipping information for all line items of the sales order.</span></span>  
  
    -   <span data-ttu-id="6447b-307">これはネイティブ コンパイル ストアド プロシージャ Sales.usp_UpdateSalesOrderShipInfo_native のラッパー プロシージャで、再試行ロジックを備えており、同じ注文を更新する同時実行トランザクションとの間で発生する可能性のある (予期しない) 競合を処理します。</span><span class="sxs-lookup"><span data-stu-id="6447b-307">This is a wrapper procedure for the natively compiled stored procedures Sales.usp_UpdateSalesOrderShipInfo_native with retry logic to deal with (unexpected) potential conflicts with concurrent transactions updating the same order.</span></span> <span data-ttu-id="6447b-308">再試行ロジックの詳細については、オンライン ブックの [こちら](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx)のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-308">For more information about retry logic see the Books Online topic [here](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx).</span></span>  
  
-   <span data-ttu-id="6447b-309">Sales.usp_UpdateSalesOrderShipInfo_native</span><span class="sxs-lookup"><span data-stu-id="6447b-309">Sales.usp_UpdateSalesOrderShipInfo_native</span></span>  
  
    -   <span data-ttu-id="6447b-310">これは、出荷情報に対する更新を実際に処理するネイティブ コンパイル ストアド プロシージャで、</span><span class="sxs-lookup"><span data-stu-id="6447b-310">This is the natively compiled stored procedure that actually processes the update to the shipping information.</span></span> <span data-ttu-id="6447b-311">ラッパー ストアド プロシージャ Sales.usp_UpdateSalesOrderShipInfo_inmem から呼び出される手段です。</span><span class="sxs-lookup"><span data-stu-id="6447b-311">It is means to be called from the wrapper stored procedure Sales.usp_UpdateSalesOrderShipInfo_inmem.</span></span> <span data-ttu-id="6447b-312">クライアントがエラーに対処できる場合、再試行ロジックを実装すると、ラッパー ストアド プロシージャを使用せずに、このプロシージャを直接呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6447b-312">If the client can deal with failures and implements retry logic, you can call this procedure directly, rather than using the wrapper stored procedure.</span></span>  
  
 <span data-ttu-id="6447b-313">次のストアド プロシージャは、デモ ワークロードに対して使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-313">The following stored procedure is used for the demo workload.</span></span>  
  
-   <span data-ttu-id="6447b-314">Demo.usp_DemoReset</span><span class="sxs-lookup"><span data-stu-id="6447b-314">Demo.usp_DemoReset</span></span>  
  
    -   <span data-ttu-id="6447b-315">SalesOrderHeader テーブルおよび SalesOrderDetail テーブルを空にして、再作成することで、デモをリセットします。</span><span class="sxs-lookup"><span data-stu-id="6447b-315">Resets the demo by emptying and reseeding the SalesOrderHeader and SalesOrderDetail tables.</span></span>  
  
 <span data-ttu-id="6447b-316">次のストアド プロシージャは、ドメインと参照整合性を確保しながら、メモリ最適化テーブルへの挿入や、テーブルからの削除を行うときに使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-316">The following stored procedures are used for inserting in and deleting from memory-optimized tables while guaranteeing domain and referential integrity.</span></span>  
  
-   <span data-ttu-id="6447b-317">Production.usp_InsertProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-317">Production.usp_InsertProduct_inmem</span></span>  
  
-   <span data-ttu-id="6447b-318">Production.usp_DeleteProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-318">Production.usp_DeleteProduct_inmem</span></span>  
  
-   <span data-ttu-id="6447b-319">Sales.usp_InsertSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-319">Sales.usp_InsertSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="6447b-320">Sales.usp_DeleteSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-320">Sales.usp_DeleteSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="6447b-321">Sales.usp_InsertSpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-321">Sales.usp_InsertSpecialOfferProduct_inmem</span></span>  
  
 <span data-ttu-id="6447b-322">最後に、ドメインと参照整合性を確認するときに使用するストアド プロシージャを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-322">Finally the following stored procedure is used to verify domain and referential integrity.</span></span>  
  
1.  <span data-ttu-id="6447b-323">dbo.usp_ValidateIntegrity</span><span class="sxs-lookup"><span data-stu-id="6447b-323">dbo.usp_ValidateIntegrity</span></span>  
  
    -   <span data-ttu-id="6447b-324">省略可能なパラメーター: @object_id - 整合性を検証するオブジェクトの ID</span><span class="sxs-lookup"><span data-stu-id="6447b-324">Optional parameter: @object_id - ID of the object to validate integrity for</span></span>  
  
    -   <span data-ttu-id="6447b-325">このプロシージャは、検証する必要がある整合性規則に関して、dbo.DomainIntegrity テーブル、dbo.ReferentialIntegrity テーブル、および dbo.UniqueIntegrity テーブルに依存しています。サンプルでは、AdventureWorks データベースの元のテーブルに対して存在する CHECK 制約、外部キー制約、および UNIQUE 制約に基づいて、これらのテーブルにデータが入力されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-325">This procedure relies on the tables dbo.DomainIntegrity, dbo.ReferentialIntegrity, and dbo.UniqueIntegrity for the integrity rules that need to be verified - the sample populates these tables based on the check, foreign key, and unique constraints that exist for the original tables in the AdventureWorks database.</span></span>  
  
    -   <span data-ttu-id="6447b-326">これはヘルパー プロシージャ dbo.usp_GenerateCKCheck、dbo.usp_GenerateFKCheck、および dbo.GenerateUQCheck を使用して、整合性チェックの実行に必要な T-SQL を生成します。</span><span class="sxs-lookup"><span data-stu-id="6447b-326">It relies on the helper procedures dbo.usp_GenerateCKCheck, dbo.usp_GenerateFKCheck, and dbo.GenerateUQCheck to generate the T-SQL needed for performing the integrity checks.</span></span>  
  
##  <a name="performance-measurements-using-the-demo-workload"></a><a name="PerformanceMeasurementsusingtheDemoWorkload"></a> <span data-ttu-id="6447b-327">デモ ワークロードを使用したパフォーマンス測定</span><span class="sxs-lookup"><span data-stu-id="6447b-327">Performance Measurements using the Demo Workload</span></span>  
 <span data-ttu-id="6447b-328">ostress は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] の CSS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サポート チームによって開発されたコマンド ライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="6447b-328">Ostress is a command-line tool that was developed by the [!INCLUDE[msCoName](../includes/msconame-md.md)] CSS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] support team.</span></span> <span data-ttu-id="6447b-329">このツールを使用すると、クエリやストアド プロシージャを並列実行できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-329">This tool can be used to execute queries or run stored procedures in parallel.</span></span> <span data-ttu-id="6447b-330">指定された T-SQL ステートメントが並列実行されるようにスレッドの数を構成できるほか、そのスレッドでステートメントを実行する回数を指定できます。ostress はスレッドをスピン アップし、すべてのスレッド内のステートメントを並列実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-330">You can configure the number of threads to run a given T-SQL statement in parallel, and you can specify how many times the statement should be executed on this thread; ostress will spin up the threads and execute the statement on all threads in parallel.</span></span> <span data-ttu-id="6447b-331">すべてのスレッドに対する実行が完了したら、その実行が完了するまでの所要時間を報告します。</span><span class="sxs-lookup"><span data-stu-id="6447b-331">After execution finishes for all threads, ostress will report the time taken for all threads to finish execution.</span></span>  
  
### <a name="installing-ostress"></a><span data-ttu-id="6447b-332">ostress のインストール</span><span class="sxs-lookup"><span data-stu-id="6447b-332">Installing ostress</span></span>  
 <span data-ttu-id="6447b-333">ostress は、RML ユーティリティの一部としてインストールされます。ostress のスタンドアロン インストールはありません。</span><span class="sxs-lookup"><span data-stu-id="6447b-333">Ostress is installed as part of the RML Utilities; there is no standalone installation for ostress.</span></span>  
  
 <span data-ttu-id="6447b-334">インストール手順:</span><span class="sxs-lookup"><span data-stu-id="6447b-334">Installation steps:</span></span>  
  
1.  <span data-ttu-id="6447b-335">次のページから RML ユーティリティの x64 インストールパッケージをダウンロードして実行します。[https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx](https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx)</span><span class="sxs-lookup"><span data-stu-id="6447b-335">Download and run the x64 installation package for the RML utilities from the following page: [https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx](https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx)</span></span>  
  
2.  <span data-ttu-id="6447b-336">特定のファイルが使用中であることを通知するダイアログ ボックスが表示された場合は、[続行] をクリックします</span><span class="sxs-lookup"><span data-stu-id="6447b-336">If there is a dialog box saying certain files are in use, click 'Continue'</span></span>  
  
### <a name="running-ostress"></a><span data-ttu-id="6447b-337">ostress の実行</span><span class="sxs-lookup"><span data-stu-id="6447b-337">Running ostress</span></span>  
 <span data-ttu-id="6447b-338">ostress は、コマンド ライン プロンプトから実行されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-338">Ostress is run from the command-line prompt.</span></span> <span data-ttu-id="6447b-339">最も便利なのは、RML ユーティリティの一部としてインストールされている "RML Cmd Prompt" から実行する方法です。</span><span class="sxs-lookup"><span data-stu-id="6447b-339">It is most convenient to run the tool from the "RML Cmd Prompt", which is installed as part of the RML Utilities.</span></span>  
  
 <span data-ttu-id="6447b-340">RML Cmd Prompt を開くには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6447b-340">To open the RML Cmd Prompt follow these instructions:</span></span>  
  
 <span data-ttu-id="6447b-341">Windows Server 2012 [R2] および Windows 8/8.1 で、Windows キーをクリックして [スタート] メニューを開き、「rml」と入力します。</span><span class="sxs-lookup"><span data-stu-id="6447b-341">In Windows Server 2012 [R2] and in Windows 8 and 8.1, open the start menu by clicking the Windows key, and type 'rml'.</span></span> <span data-ttu-id="6447b-342">検索結果の一覧に表示される [RML Cmd Prompt] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6447b-342">Click on "RML Cmd Prompt", which will be in the list of search results.</span></span>  
  
 <span data-ttu-id="6447b-343">コマンド プロンプトが、RML ユーティリティのインストール フォルダーにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6447b-343">Ensure that the command prompt is located in the RML Utilities installation folder.</span></span> <span data-ttu-id="6447b-344">例:</span><span class="sxs-lookup"><span data-stu-id="6447b-344">For example:</span></span>  
  
 ![](../../2014/database-engine/media/SQLServer2014RTMIn-MemoryOLTP01.jpg)  
  
 <span data-ttu-id="6447b-345">コマンド ライン オプションを指定せずに ostress.exe を実行すると、ostress のコマンド ライン オプションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-345">The command-line options for ostress can be seen when simply running ostress.exe without any command-line options.</span></span> <span data-ttu-id="6447b-346">このサンプルで ostress を実行するときに使用できる主なオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-346">The main options to consider for running ostress with this sample are:</span></span>  
  
-   <span data-ttu-id="6447b-347">-S 接続先の [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前</span><span class="sxs-lookup"><span data-stu-id="6447b-347">-S name of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to connect to</span></span>  
  
-   <span data-ttu-id="6447b-348">-E Windows 認証を使用して接続します (既定)。認証を使用する場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーザー名と-P オプションを使用して、ユーザー名とパスワードをそれぞれ指定します。</span><span class="sxs-lookup"><span data-stu-id="6447b-348">-E use Windows authentication to connect (default); if you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentication, use the options -U and -P to specify the username and password, respectively</span></span>  
  
-   <span data-ttu-id="6447b-349">-d データベースの名前。この例では AdventureWorks2014</span><span class="sxs-lookup"><span data-stu-id="6447b-349">-d name of the database, for this example AdventureWorks2014</span></span>  
  
-   <span data-ttu-id="6447b-350">-Q 実行される T-SQL ステートメント</span><span class="sxs-lookup"><span data-stu-id="6447b-350">-Q the T-SQL statement to be executed</span></span>  
  
-   <span data-ttu-id="6447b-351">-n 各入力ファイル/クエリを処理する接続の数</span><span class="sxs-lookup"><span data-stu-id="6447b-351">-n number of connections processing each input file/query</span></span>  
  
-   <span data-ttu-id="6447b-352">-r 各入力ファイル/クエリを実行するために接続ごとに繰り返される数</span><span class="sxs-lookup"><span data-stu-id="6447b-352">-r the number of iterations for each connection to execute each input file/query</span></span>  
  
### <a name="demo-workload"></a><span data-ttu-id="6447b-353">デモ ワークロード</span><span class="sxs-lookup"><span data-stu-id="6447b-353">Demo Workload</span></span>  
 <span data-ttu-id="6447b-354">デモ ワークロードで使用する主なストアド プロシージャは Sales.usp_InsertSalesOrder_inmem/ondisk です。</span><span class="sxs-lookup"><span data-stu-id="6447b-354">The main stored procedure used in the demo workload is Sales.usp_InsertSalesOrder_inmem/ondisk.</span></span> <span data-ttu-id="6447b-355">以下のスクリプトでは、サンプル データを使用してテーブル値パラメーター (TVP) を生成し、5 つの品目が含まれる販売注文を挿入するプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6447b-355">The script in the below constructs a table-valued parameter (TVP) with sample data, and calls the procedure to insert a sales order with 5 line items.</span></span>  
  
 <span data-ttu-id="6447b-356">ostress ツールは、ストアド プロシージャ呼び出しを並列実行し、販売注文を同時に挿入するクライアントをシミュレートする際に使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-356">The ostress tool is used to execute the stored procedure calls in parallel, to simulate clients inserting sales orders concurrently.</span></span>  
  
 <span data-ttu-id="6447b-357">負荷をかけた Demo.usp_DemoReset の実行が完了するたびに、デモをリセットしてください。</span><span class="sxs-lookup"><span data-stu-id="6447b-357">Reset the demo after each stress run executing Demo.usp_DemoReset.</span></span> <span data-ttu-id="6447b-358">このプロシージャにより、メモリ最適化テーブルの行とディスク ベース テーブルが削除され、データベース チェックポイントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-358">This procedure deletes the rows in the memory-optimized tables, truncates the disk-based tables, and executes a database checkpoint.</span></span>  
  
 <span data-ttu-id="6447b-359">次のスクリプトは同時に実行され、販売注文処理のワークロードをシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="6447b-359">The following script is executed concurrently to simulate a sales order processing workload:</span></span>  
  
```  
DECLARE   
      @i int = 0,   
      @od Sales.SalesOrderDetailType_inmem,   
      @SalesOrderID int,   
      @DueDate datetime2 = sysdatetime(),   
      @CustomerID int = rand() * 8000,   
      @BillToAddressID int = rand() * 10000,   
      @ShipToAddressID int = rand() * 10000,   
      @ShipMethodID int = (rand() * 5) + 1;   
  
INSERT INTO @od   
SELECT OrderQty, ProductID, SpecialOfferID   
FROM Demo.DemoSalesOrderDetailSeed   
WHERE OrderID= cast((rand()*106) + 1 as int);   
  
WHILE (@i < 20)   
BEGIN;   
      EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od;   
      SET @i += 1   
END  
  
```  
  
 <span data-ttu-id="6447b-360">このスクリプトでは、作成された各サンプル注文が、WHILE ループで実行された 20 個のストアド プロシージャによって 20 回挿入されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-360">With this script, each sample order that is constructed is inserted 20 times, through 20 stored procedures executed in a WHILE loop.</span></span> <span data-ttu-id="6447b-361">ループを使うことで、サンプル注文がデータベースを使用して作成されるという事実を説明します。</span><span class="sxs-lookup"><span data-stu-id="6447b-361">The loop is used to account for the fact that the database is used to construct the sample order.</span></span> <span data-ttu-id="6447b-362">一般的な運用環境では、中間層アプリケーションが、挿入する販売注文を作成します。</span><span class="sxs-lookup"><span data-stu-id="6447b-362">In typical production environments, the mid-tier application will construct the sales order to be inserted.</span></span>  
  
 <span data-ttu-id="6447b-363">前のスクリプトでは、メモリ最適化テーブルに販売注文が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-363">The above script inserts sales orders into memory-optimized tables.</span></span> <span data-ttu-id="6447b-364">ディスク ベース テーブルに販売注文を挿入するスクリプトを取得するには、2 つある "_inmem" を "_ondisk" に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6447b-364">The script to insert sales orders into disk-based tables is derived by replacing the two occurrences of '_inmem' with '_ondisk'.</span></span>  
  
 <span data-ttu-id="6447b-365">ostress ツールを使って、複数のコンカレント接続を使用してスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-365">We will use the ostress tool to execute the scripts using several concurrent connections.</span></span> <span data-ttu-id="6447b-366">"-n" パラメーターで接続数を制御し、"r" パラメーターで各接続のスクリプト実行回数を制御します。</span><span class="sxs-lookup"><span data-stu-id="6447b-366">We will use the parameter '-n' to control the number of connections, and the parameter 'r' to control how many times the script is executed on each connection.</span></span>  
  
#### <a name="functional-validation-of-the-workload"></a><span data-ttu-id="6447b-367">ワークロードの機能検証</span><span class="sxs-lookup"><span data-stu-id="6447b-367">Functional Validation of the Workload</span></span>  
 <span data-ttu-id="6447b-368">すべてが正しく動作することを確認するために、10個の同時接続と5回の反復処理を使用してサンプルテストを開始し、合計 10 \* 5 \* 20 = 1000 の販売注文を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6447b-368">To verify everything works, we will start with a sample test, using 10 concurrent connects and 5 iterations, inserting a total of 10 \* 5 \* 20 = 1000 sales order.</span></span>  
  
 <span data-ttu-id="6447b-369">次のコマンドでは、既定のインスタンスがローカル コンピューターで使用されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="6447b-369">With the below command we assume using the default instance on the local machine.</span></span> <span data-ttu-id="6447b-370">名前付きインスタンスまたはリモート サーバーを使用している場合は、- S パラメーターを使用してサーバー名を適宜変更します。</span><span class="sxs-lookup"><span data-stu-id="6447b-370">If you are using a named instance or using a remote server, change the server name accordingly, using the parameter -S.</span></span>  
  
 <span data-ttu-id="6447b-371">RML Cmd Prompt で次のコマンドを使用して、1000 個の販売注文をメモリ最適化テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="6447b-371">Insert 1000 sales orders in memory-optimized tables use the following command in the RML Cmd Prompt:</span></span>  
  
 <span data-ttu-id="6447b-372">[コピー] をクリックしてコマンドをコピーし、RML ユーティリティのコマンド プロンプトに貼り付けてください。</span><span class="sxs-lookup"><span data-stu-id="6447b-372">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n10 -r5 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="6447b-373">すべてが適切に機能していると、コマンド ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6447b-373">If everything works as expected, your command window will look similar to the following.</span></span> <span data-ttu-id="6447b-374">エラー メッセージはありません。</span><span class="sxs-lookup"><span data-stu-id="6447b-374">Error messages are not expected.</span></span>  
  
 ![](../../2014/database-engine/media/SQLServer2014RTMIn-MemoryOLTP02.jpg)  
  
 <span data-ttu-id="6447b-375">また、ワークロードが、ディスク ベーステーブルに対して適切に機能していることも検証します。それには、RML Cmd Prompt で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-375">Validate that also the workload functions as expected for disk-based tables by running the following command in the RML Cmd Prompt:</span></span>  
  
 <span data-ttu-id="6447b-376">[コピー] をクリックしてコマンドをコピーし、RML ユーティリティのコマンド プロンプトに貼り付けてください。</span><span class="sxs-lookup"><span data-stu-id="6447b-376">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n10 -r5 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
#### <a name="running-the-workload"></a><span data-ttu-id="6447b-377">ワークロードの実行</span><span class="sxs-lookup"><span data-stu-id="6447b-377">Running the Workload</span></span>  
 <span data-ttu-id="6447b-378">拡張性をテストするために、100 個の接続を使用して、1,000 万個の販売注文を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6447b-378">To test at scale we insert 10 million sales orders, using 100 connections.</span></span> <span data-ttu-id="6447b-379">このテストは、適度なサーバー (たとえば、8 個の物理コアと 16 個の論理コア) と、ログ用の基本 SSD ストレージで問題なく実行されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-379">This test performs reasonably on a modest server (e.g., 8 physical, 16 logical cores), and basic SSD storage for the log.</span></span> <span data-ttu-id="6447b-380">ご利用のハードウェアでテストを正常に実行できない場合は、「[実行速度の遅いテストのトラブルシューティング](#Troubleshootingslow-runningtests)」セクションをご覧ください。このテストのストレス レベルを下げるには、"-n" パラメーターを変更して接続数を減らします。</span><span class="sxs-lookup"><span data-stu-id="6447b-380">If the test does not perform well on your hardware, take look at the Section [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).If you want to reduce the level of stress for this test, lower the number of connections by changing the parameter '-n'.</span></span> <span data-ttu-id="6447b-381">たとえば、接続数を 40 に下げるには、"-n100" パラメーターを "-n40" に変更します。</span><span class="sxs-lookup"><span data-stu-id="6447b-381">For example to lower the connection count to 40, change the parameter '-n100' to '-n40'.</span></span>  
  
 <span data-ttu-id="6447b-382">ワークロードのパフォーマンス評価基準として、ワークロードの実行後に ostress.exe によって報告された経過時間を使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-382">As a performance measure for the workload we use the elapsed time as reported by ostress.exe after running the workload.</span></span>  
  
##### <a name="memory-optimized-tables"></a><span data-ttu-id="6447b-383">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="6447b-383">Memory-optimized tables</span></span>  
 <span data-ttu-id="6447b-384">まず、メモリ最適化テーブルでワークロードを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-384">We will start by running the workload on memory-optimized tables.</span></span> <span data-ttu-id="6447b-385">次のコマンドは、100 個のスレッドを開きます。このスレッドそれぞれが、5,000 個の繰り返しに対して実行されており、</span><span class="sxs-lookup"><span data-stu-id="6447b-385">The following command opens 100 threads, each running for 5,000 iterations.</span></span>  <span data-ttu-id="6447b-386">各繰り返しによって、20 個の販売注文が個別のトランザクションに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-386">Each iteration inserts 20 sales orders in separate transactions.</span></span> <span data-ttu-id="6447b-387">1 つの繰り返しにつき 20 個の挿入があり、挿入するデータがデータベースを使用して生成されるという事実を補います。</span><span class="sxs-lookup"><span data-stu-id="6447b-387">There are 20 inserts per iteration to compensate for the fact that the database is used to generate the data to be inserted.</span></span> <span data-ttu-id="6447b-388">この結果、販売注文の挿入の合計は "20 × 5,000 \* 100 = 10,000,000" 個になります。</span><span class="sxs-lookup"><span data-stu-id="6447b-388">This yield a total of 20 \* 5,000 \* 100 = 10,000,000 sales order inserts.</span></span>  
  
 <span data-ttu-id="6447b-389">RML Cmd Prompt を開いて、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-389">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="6447b-390">[コピー] をクリックしてコマンドをコピーし、RML ユーティリティのコマンド プロンプトに貼り付けてください。</span><span class="sxs-lookup"><span data-stu-id="6447b-390">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="6447b-391">合計 8 個の物理 (16 個の論理) コアを備えたテスト サーバーでの所要時間は 2 分 5 秒でした。</span><span class="sxs-lookup"><span data-stu-id="6447b-391">On one test server with a total number of 8 physical (16 logical) cores, this took 2 minutes and 5 seconds.</span></span> <span data-ttu-id="6447b-392">合計 24 個の物理 (48 個の論理) コアを備えた 2 台目のテスト サーバーでの所要時間は 1 分 0 秒でした。</span><span class="sxs-lookup"><span data-stu-id="6447b-392">On a second test server with 24 physical (48 logical) cores, this took 1 minute and 0 seconds.</span></span>  
  
 <span data-ttu-id="6447b-393">ワークロードの実行中、タスク マネージャーなどを使用して、CPU の使用率を確認します。</span><span class="sxs-lookup"><span data-stu-id="6447b-393">Observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="6447b-394">CPU 使用率が 100% に近いことがわかります。</span><span class="sxs-lookup"><span data-stu-id="6447b-394">You will see that CPU utilization is close to 100%.</span></span> <span data-ttu-id="6447b-395">そうでない場合は、ログ IO がボトルネックになっています。「 [実行速度の遅いテストのトラブルシューティング](#Troubleshootingslow-runningtests)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-395">If this is not the case, you have a log IO bottleneck see also [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).</span></span>  
  
##### <a name="disk-based-tables"></a><span data-ttu-id="6447b-396">ディスク ベース テーブル</span><span class="sxs-lookup"><span data-stu-id="6447b-396">Disk-based tables</span></span>  
 <span data-ttu-id="6447b-397">次のコマンドは、ディスク ベース テーブルでワークロードを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-397">The following command will run the workload on disk-based tables.</span></span> <span data-ttu-id="6447b-398">このワークロードの実行には時間がかかる場合があり、その主な原因はシステム内のラッチ競合です。</span><span class="sxs-lookup"><span data-stu-id="6447b-398">Note that this workload may take a while to execute, which is largely due to latch contention in the system.</span></span> <span data-ttu-id="6447b-399">メモリ最適化テーブルはラッチ フリーであるため、この問題は発生しません。</span><span class="sxs-lookup"><span data-stu-id="6447b-399">Memory-optimized table are latch-free and thus do not suffer from this problem.</span></span>  
  
 <span data-ttu-id="6447b-400">RML Cmd Prompt を開いて、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-400">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="6447b-401">[コピー] をクリックしてコマンドをコピーし、RML ユーティリティのコマンド プロンプトに貼り付けてください。</span><span class="sxs-lookup"><span data-stu-id="6447b-401">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="6447b-402">合計 8 個の物理 (16 個の論理) コアを備えたテスト サーバーでの所要時間は 41 分 25 秒でした。</span><span class="sxs-lookup"><span data-stu-id="6447b-402">On one test server with a total number of 8 physical (16 logical) cores, this took 41 minutes and 25 seconds.</span></span> <span data-ttu-id="6447b-403">合計 24 個の物理 (48 個の論理) コアを備えた 2 台目のテスト サーバーでの所要時間は 52 分 16 秒でした。</span><span class="sxs-lookup"><span data-stu-id="6447b-403">On a second test server with 24 physical (48 logical) cores, this took 52 minutes and 16 seconds.</span></span>  
  
 <span data-ttu-id="6447b-404">ディスク ベース テーブルを使用していると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では CPU をフルに活用できません。これが主な要因となり、このテストでは、メモリ最適化テーブルとディスク ベース テーブルのパフォーマンスに差が生じました。</span><span class="sxs-lookup"><span data-stu-id="6447b-404">The main factor in the performance difference between memory-optimized tables and disk-based tables in this test is the fact that when using disk-based tables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot not fully utilize the CPU.</span></span> <span data-ttu-id="6447b-405">CPU をフル活用できない原因はラッチ競合です。同時実行トランザクションは同じデータ ページに書き込もうとしますが、ラッチにより、一度に 1 つのトランザクションしかページに書き込むことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="6447b-405">The reason is latch contention: concurrent transactions are attempting to write to the same data page; latches are used to ensure only one transaction at a time can write to a page.</span></span> <span data-ttu-id="6447b-406">[!INCLUDE[hek_2](../includes/hek-2-md.md)] エンジンはラッチ フリーで、データ行はページ単位で整理されていません。</span><span class="sxs-lookup"><span data-stu-id="6447b-406">The [!INCLUDE[hek_2](../includes/hek-2-md.md)] engine is latch-free, and data rows are not organized in pages.</span></span> <span data-ttu-id="6447b-407">このため、同時実行トランザクションでは、互いの挿入がブロックされることはないため、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が CPU を完全に利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6447b-407">Thus, concurrent transactions do not block each other's inserts, thus enabling [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to fully utilize the CPU.</span></span>  
  
 <span data-ttu-id="6447b-408">ワークロードの実行中、タスク マネージャーなどを使用して、CPU の使用率を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-408">You can observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="6447b-409">ディスク ベース テーブルの CPU 使用率が、100% からはかけ離れていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6447b-409">You will see with disk-based tables the CPU utilization is far from 100%.</span></span> <span data-ttu-id="6447b-410">16 個の論理プロセッサを備えたテスト構成では、使用率は 24% 前後で推移します。</span><span class="sxs-lookup"><span data-stu-id="6447b-410">On a test configuration with 16 logical processors, the utilization would hover around 24%.</span></span>  
  
 <span data-ttu-id="6447b-411">必要に応じて、パフォーマンス モニターを使用して、パフォーマンス カウンター "\SQL Server:Latches\Latch Waits/sec" で 1 秒あたりのラッチ待機数を表示できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-411">Optionally, you can view the number of latch waits per second using Performance Monitor, with the performance counter '\SQL Server:Latches\Latch Waits/sec'.</span></span>  
  
#### <a name="resetting-the-demo"></a><span data-ttu-id="6447b-412">デモのリセット</span><span class="sxs-lookup"><span data-stu-id="6447b-412">Resetting the demo</span></span>  
 <span data-ttu-id="6447b-413">デモをリセットするには、RML Cmd Prompt を開いて、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-413">To reset the demo, open the RML Cmd Prompt, and execute the following command:</span></span>  
  
```  
ostress.exe -S. -E -dAdventureWorks2014 -Q"EXEC Demo.usp_DemoReset"  
```  
  
 <span data-ttu-id="6447b-414">ハードウェアによっては、この実行に数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="6447b-414">Depending on the hardware this may take a few minutes to run.</span></span>  
  
 <span data-ttu-id="6447b-415">デモの実行が完了するたびに、リセットすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6447b-415">We recommend a reset after every demo run.</span></span> <span data-ttu-id="6447b-416">このワークロードは挿入のみであるため、実行のたびに多くのメモリを消費します。このため、メモリ不足が発生しないようにリセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="6447b-416">Because this workload is insert-only, each run will consume more memory, and thus a reset is required to prevent running out of memory.</span></span> <span data-ttu-id="6447b-417">実行後に消費されるメモリ量について、セクション「 [ワークロード実行後のメモリ使用率](#Memoryutilizationafterrunningtheworkload)」で説明しています。</span><span class="sxs-lookup"><span data-stu-id="6447b-417">The amount of memory consumed after a run is discussed in Section [Memory utilization after running the workload](#Memoryutilizationafterrunningtheworkload).</span></span>  
  
###  <a name="troubleshooting-slow-running-tests"></a><a name="Troubleshootingslow-runningtests"></a> <span data-ttu-id="6447b-418">実行速度の遅いテストのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6447b-418">Troubleshooting slow-running tests</span></span>  
 <span data-ttu-id="6447b-419">テスト結果は、通常、ハードウェアと、テスト実行で使用されたコンカレンシーのレベルによって変わります。</span><span class="sxs-lookup"><span data-stu-id="6447b-419">Test results will typically vary with hardware, and also the level of concurrency used in the test run.</span></span> <span data-ttu-id="6447b-420">期待した結果を得られない場合に確認することをいくつか次に示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-420">A couple of things to look for if the results are not as expected:</span></span>  
  
-   <span data-ttu-id="6447b-421">同時実行トランザクションの数: 1 つのスレッドでワークロードを実行すると、 [!INCLUDE[hek_2](../includes/hek-2-md.md)] によるパフォーマンス向上が 2 倍に満たない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6447b-421">Number of concurrent transactions: When running the workload on a single thread, performance gain with [!INCLUDE[hek_2](../includes/hek-2-md.md)] will likely be less than 2X.</span></span> <span data-ttu-id="6447b-422">高レベルのコンカレンシーがある場合、唯一大きな問題になるのがラッチ競合です。</span><span class="sxs-lookup"><span data-stu-id="6447b-422">Latch contention is only a big problem if there is a high level of concurrency.</span></span>  
  
-   <span data-ttu-id="6447b-423">ph x="1" /&gt; で使用できるコアが少ない: つまり、低レベルのコンカレンシーがシステムに存在することになります。これは、SQL で使用できるコアの数しか、トランザクションをコンカレンシーできないからです。</span><span class="sxs-lookup"><span data-stu-id="6447b-423">Low number of cores available to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]: This means there will be a low level of concurrency in the system, as there can only be as many concurrently executing transactions as there are cores available to SQL.</span></span>  
  
    -   <span data-ttu-id="6447b-424">現象: ディスク ベース テーブルでワークロードを実行しているときに CPU 使用率が高い場合、競合の数はそれほど多くありません。これは、コンカレンシーが不足していることを示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-424">Symptom: if the CPU utilization is high when running the workload on disk-based tables, this means there is not a lot of contention, pointing to a lack of concurrency.</span></span>  
  
-   <span data-ttu-id="6447b-425">ログ ドライブの速度:ログ ドライブが、システム内のトランザクション スループット レベルに対応できない場合、ワークロードはログ IO でボトルネックになります。</span><span class="sxs-lookup"><span data-stu-id="6447b-425">Speed of the log drive: If the log drive cannot keep up with the level of transaction throughput in the system, the workload becomes bottlenecked on log IO.</span></span> <span data-ttu-id="6447b-426">[!INCLUDE[hek_2](../includes/hek-2-md.md)]でのログ記録は効率的ですが、ログ IO がボトルネックになっていると、パフォーマンス向上の可能性は限られます。</span><span class="sxs-lookup"><span data-stu-id="6447b-426">Although logging is more efficient with [!INCLUDE[hek_2](../includes/hek-2-md.md)], if log IO is a bottleneck, the potential performance gain is limited.</span></span>  
  
    -   <span data-ttu-id="6447b-427">現象: メモリ最適化テーブルでワークロードを実行しているとき、CPU 使用率が 100% からかけ離れている場合、または、その変動が激しい場合は、ログ IO ボトルネックが存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6447b-427">Symptom: if the CPU utilization is not close to 100% or is very spiky when running the workload on memory-optimized tables, it is possible there is a log IO bottleneck.</span></span> <span data-ttu-id="6447b-428">これを確認するには、リソース モニターを開き、ログ ドライブのキュー長を確認します。</span><span class="sxs-lookup"><span data-stu-id="6447b-428">This can be confirmed by opening Resource Monitor and looking at the queue length for the log drive.</span></span>  
  
##  <a name="memory-and-disk-space-utilization-in-the-sample"></a><a name="MemoryandDiskSpaceUtilizationintheSample"></a> <span data-ttu-id="6447b-429">サンプルにおけるメモリおよびディスク領域の使用率</span><span class="sxs-lookup"><span data-stu-id="6447b-429">Memory and Disk Space Utilization in the Sample</span></span>  
 <span data-ttu-id="6447b-430">ここでは、サンプル データベースのメモリおよびディスク領域の使用率に関して期待すべき事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="6447b-430">In the below we describe what to expect in terms of memory and disk space utilization for the sample database.</span></span> <span data-ttu-id="6447b-431">また、16 個の論理コアを備えたテスト サーバーでの結果も示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-431">We also show the results we have seen in on a test server with 16 logical cores.</span></span>  
  
###  <a name="memory-utilization-for-the-memory-optimized-tables"></a><a name="Memoryutilizationforthememory-optimizedtables"></a> <span data-ttu-id="6447b-432">メモリ最適化テーブルのメモリ使用率</span><span class="sxs-lookup"><span data-stu-id="6447b-432">Memory utilization for the memory-optimized tables</span></span>  
  
#### <a name="overall-utilization-of-the-database"></a><span data-ttu-id="6447b-433">データベースの全体的な使用率</span><span class="sxs-lookup"><span data-stu-id="6447b-433">Overall utilization of the database</span></span>  
 <span data-ttu-id="6447b-434">次のクエリを使用すると、システムの [!INCLUDE[hek_2](../includes/hek-2-md.md)] の合計メモリ使用率を取得できます。</span><span class="sxs-lookup"><span data-stu-id="6447b-434">The following query can be used to obtain the total memory utilization for [!INCLUDE[hek_2](../includes/hek-2-md.md)] in the system.</span></span>  
  
```  
SELECT type  
   , name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
 <span data-ttu-id="6447b-435">データベースが作成された後のスナップショット:</span><span class="sxs-lookup"><span data-stu-id="6447b-435">Snapshot after the database has just been created:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="6447b-436">**type**</span><span class="sxs-lookup"><span data-stu-id="6447b-436">**type**</span></span>|<span data-ttu-id="6447b-437">**name**</span><span class="sxs-lookup"><span data-stu-id="6447b-437">**name**</span></span>|<span data-ttu-id="6447b-438">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-438">**pages_MB**</span></span>|  
|<span data-ttu-id="6447b-439">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-439">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-440">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-440">Default</span></span>|<span data-ttu-id="6447b-441">94</span><span class="sxs-lookup"><span data-stu-id="6447b-441">94</span></span>|  
|<span data-ttu-id="6447b-442">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-442">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-443">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="6447b-443">DB_ID_5</span></span>|<span data-ttu-id="6447b-444">877</span><span class="sxs-lookup"><span data-stu-id="6447b-444">877</span></span>|  
|<span data-ttu-id="6447b-445">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-445">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-446">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-446">Default</span></span>|<span data-ttu-id="6447b-447">0</span><span class="sxs-lookup"><span data-stu-id="6447b-447">0</span></span>|  
|<span data-ttu-id="6447b-448">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-448">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-449">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-449">Default</span></span>|<span data-ttu-id="6447b-450">0</span><span class="sxs-lookup"><span data-stu-id="6447b-450">0</span></span>|  
  
 <span data-ttu-id="6447b-451">既定のメモリ クラークは比較的小さく、システム全体のメモリ構造が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6447b-451">The default memory clerks contain system-wide memory structures and are relatively small.</span></span> <span data-ttu-id="6447b-452">ユーザー データベースのメモリ クラーク (この場合は ID 5 のデータベース) は約 900 MB です。</span><span class="sxs-lookup"><span data-stu-id="6447b-452">The memory clerk for the user database, in this case database with ID 5, is about 900MB.</span></span>  
  
#### <a name="memory-utilization-per-table"></a><span data-ttu-id="6447b-453">テーブルごとのメモリ使用率</span><span class="sxs-lookup"><span data-stu-id="6447b-453">Memory utilization per table</span></span>  
 <span data-ttu-id="6447b-454">次のクエリを使用すると、個別のテーブルとそのインデックスのメモリ使用率にドリル ダウンできます。</span><span class="sxs-lookup"><span data-stu-id="6447b-454">The following query can be used to drill down into the memory utilization of the individual tables and their indexes:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
 <span data-ttu-id="6447b-455">サンプルの新しいインストールに対するこのクエリの結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-455">The following shows the results of this query for a fresh installation of the sample:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="6447b-456">**テーブル名**</span><span class="sxs-lookup"><span data-stu-id="6447b-456">**Table Name**</span></span>|<span data-ttu-id="6447b-457">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="6447b-457">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="6447b-458">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="6447b-458">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="6447b-459">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-459">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="6447b-460">64</span><span class="sxs-lookup"><span data-stu-id="6447b-460">64</span></span>|<span data-ttu-id="6447b-461">3840</span><span class="sxs-lookup"><span data-stu-id="6447b-461">3840</span></span>|  
|<span data-ttu-id="6447b-462">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="6447b-462">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="6447b-463">1984</span><span class="sxs-lookup"><span data-stu-id="6447b-463">1984</span></span>|<span data-ttu-id="6447b-464">5504</span><span class="sxs-lookup"><span data-stu-id="6447b-464">5504</span></span>|  
|<span data-ttu-id="6447b-465">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-465">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="6447b-466">15316</span><span class="sxs-lookup"><span data-stu-id="6447b-466">15316</span></span>|<span data-ttu-id="6447b-467">663552</span><span class="sxs-lookup"><span data-stu-id="6447b-467">663552</span></span>|  
|<span data-ttu-id="6447b-468">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="6447b-468">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="6447b-469">64</span><span class="sxs-lookup"><span data-stu-id="6447b-469">64</span></span>|<span data-ttu-id="6447b-470">10432</span><span class="sxs-lookup"><span data-stu-id="6447b-470">10432</span></span>|  
|<span data-ttu-id="6447b-471">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-471">SpecialOffer_inmem</span></span>|<span data-ttu-id="6447b-472">3</span><span class="sxs-lookup"><span data-stu-id="6447b-472">3</span></span>|<span data-ttu-id="6447b-473">8192</span><span class="sxs-lookup"><span data-stu-id="6447b-473">8192</span></span>|  
|<span data-ttu-id="6447b-474">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-474">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="6447b-475">7168</span><span class="sxs-lookup"><span data-stu-id="6447b-475">7168</span></span>|<span data-ttu-id="6447b-476">147456</span><span class="sxs-lookup"><span data-stu-id="6447b-476">147456</span></span>|  
|<span data-ttu-id="6447b-477">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-477">Product_inmem</span></span>|<span data-ttu-id="6447b-478">124</span><span class="sxs-lookup"><span data-stu-id="6447b-478">124</span></span>|<span data-ttu-id="6447b-479">12352</span><span class="sxs-lookup"><span data-stu-id="6447b-479">12352</span></span>|  
  
 <span data-ttu-id="6447b-480">テーブルがかなり小さいことがわかります。SalesOrderHeader_inmem は約 7 MB、SalesOrderDetail_inmem は約 15 MB です。</span><span class="sxs-lookup"><span data-stu-id="6447b-480">As you can see the tables are fairly small: SalesOrderHeader_inmem is about 7MB, and SalesOrderDetail_inmem is about 15MB in size.</span></span>  
  
 <span data-ttu-id="6447b-481">ここで印象的なのは、インデックスに割り当てられているメモリのサイズです (テーブル データのサイズと比較)。</span><span class="sxs-lookup"><span data-stu-id="6447b-481">What is striking here is the size of the memory allocated for indexes, compared to the size of the table data.</span></span> <span data-ttu-id="6447b-482">このサイズになるのは、サンプルのハッシュ インデックスが、大きなデータ サイズに合わせて事前にサイズ調整されているためです。</span><span class="sxs-lookup"><span data-stu-id="6447b-482">That is because the hash indexes in the sample are pre-sized for a larger data size.</span></span> <span data-ttu-id="6447b-483">ハッシュ インデックスのサイズは固定されているため、テーブルのデータのサイズに合わせて大きくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="6447b-483">Note that hash indexes have a fixed size, and thus their size will not grow with the size of data in the table.</span></span>  
  
####  <a name="memory-utilization-after-running-the-workload"></a><a name="Memoryutilizationafterrunningtheworkload"></a> <span data-ttu-id="6447b-484">ワークロード実行後のメモリ使用率</span><span class="sxs-lookup"><span data-stu-id="6447b-484">Memory utilization after running the workload</span></span>  
 <span data-ttu-id="6447b-485">1,000 万個の販売注文を挿入した後の全体的なメモリ使用率は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6447b-485">After insert 10 million sales orders, the all-up memory utilization looks similar to the following:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="6447b-486">**type**</span><span class="sxs-lookup"><span data-stu-id="6447b-486">**type**</span></span>|<span data-ttu-id="6447b-487">**name**</span><span class="sxs-lookup"><span data-stu-id="6447b-487">**name**</span></span>|<span data-ttu-id="6447b-488">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-488">**pages_MB**</span></span>|  
|<span data-ttu-id="6447b-489">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-489">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-490">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-490">Default</span></span>|<span data-ttu-id="6447b-491">146</span><span class="sxs-lookup"><span data-stu-id="6447b-491">146</span></span>|  
|<span data-ttu-id="6447b-492">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-492">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-493">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="6447b-493">DB_ID_5</span></span>|<span data-ttu-id="6447b-494">7374</span><span class="sxs-lookup"><span data-stu-id="6447b-494">7374</span></span>|  
|<span data-ttu-id="6447b-495">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-495">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-496">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-496">Default</span></span>|<span data-ttu-id="6447b-497">0</span><span class="sxs-lookup"><span data-stu-id="6447b-497">0</span></span>|  
|<span data-ttu-id="6447b-498">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-498">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-499">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-499">Default</span></span>|<span data-ttu-id="6447b-500">0</span><span class="sxs-lookup"><span data-stu-id="6447b-500">0</span></span>|  
  
 <span data-ttu-id="6447b-501">このように、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] がサンプル データベースのメモリ最適化テーブルおよびインデックスに対して使用しているビットは 8 GB を下回ります。</span><span class="sxs-lookup"><span data-stu-id="6447b-501">As you can see, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is using a bit under 8GB for the memory-optimized tables and indexes in the sample database.</span></span>  
  
 <span data-ttu-id="6447b-502">サンプルを 1 回実行した後のテーブルごとの詳細なメモリ使用量を確認します。</span><span class="sxs-lookup"><span data-stu-id="6447b-502">Looking at the detailed memory usage per table after one example run:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="6447b-503">**テーブル名**</span><span class="sxs-lookup"><span data-stu-id="6447b-503">**Table Name**</span></span>|<span data-ttu-id="6447b-504">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="6447b-504">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="6447b-505">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="6447b-505">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="6447b-506">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-506">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="6447b-507">5113761</span><span class="sxs-lookup"><span data-stu-id="6447b-507">5113761</span></span>|<span data-ttu-id="6447b-508">663552</span><span class="sxs-lookup"><span data-stu-id="6447b-508">663552</span></span>|  
|<span data-ttu-id="6447b-509">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="6447b-509">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="6447b-510">64</span><span class="sxs-lookup"><span data-stu-id="6447b-510">64</span></span>|<span data-ttu-id="6447b-511">10368</span><span class="sxs-lookup"><span data-stu-id="6447b-511">10368</span></span>|  
|<span data-ttu-id="6447b-512">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-512">SpecialOffer_inmem</span></span>|<span data-ttu-id="6447b-513">2</span><span class="sxs-lookup"><span data-stu-id="6447b-513">2</span></span>|<span data-ttu-id="6447b-514">8192</span><span class="sxs-lookup"><span data-stu-id="6447b-514">8192</span></span>|  
|<span data-ttu-id="6447b-515">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-515">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="6447b-516">1575679</span><span class="sxs-lookup"><span data-stu-id="6447b-516">1575679</span></span>|<span data-ttu-id="6447b-517">147456</span><span class="sxs-lookup"><span data-stu-id="6447b-517">147456</span></span>|  
|<span data-ttu-id="6447b-518">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-518">Product_inmem</span></span>|<span data-ttu-id="6447b-519">111</span><span class="sxs-lookup"><span data-stu-id="6447b-519">111</span></span>|<span data-ttu-id="6447b-520">12032</span><span class="sxs-lookup"><span data-stu-id="6447b-520">12032</span></span>|  
|<span data-ttu-id="6447b-521">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="6447b-521">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="6447b-522">64</span><span class="sxs-lookup"><span data-stu-id="6447b-522">64</span></span>|<span data-ttu-id="6447b-523">3712</span><span class="sxs-lookup"><span data-stu-id="6447b-523">3712</span></span>|  
|<span data-ttu-id="6447b-524">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="6447b-524">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="6447b-525">1984</span><span class="sxs-lookup"><span data-stu-id="6447b-525">1984</span></span>|<span data-ttu-id="6447b-526">5504</span><span class="sxs-lookup"><span data-stu-id="6447b-526">5504</span></span>|  
  
 <span data-ttu-id="6447b-527">データの合計サイズが約 6.5 GB であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6447b-527">We can see a total of about 6.5GB of data.</span></span> <span data-ttu-id="6447b-528">SalesOrderHeader_inmem テーブルと SalesOrderDetail_inmem テーブルのインデックスのサイズが、販売注文を挿入する前のインデックスのサイズと同じであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-528">Notice that the size of the indexes on the table SalesOrderHeader_inmem and SalesOrderDetail_inmem is the same as the size of the indexes before inserting the sales orders.</span></span> <span data-ttu-id="6447b-529">インデックスのサイズが変わらなかったのは、この両方のテーブルがハッシュ インデックスを使用しているからです。ハッシュ インデックスは静的です。</span><span class="sxs-lookup"><span data-stu-id="6447b-529">The index size did not change because both tables are using hash indexes, and hash indexes are static.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="6447b-530">デモのリセット後</span><span class="sxs-lookup"><span data-stu-id="6447b-530">After demo reset</span></span>  
 <span data-ttu-id="6447b-531">ストアド プロシージャ Demo.usp_DemoReset を使用すると、デモをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="6447b-531">The stored procedure Demo.usp_DemoReset can be used to reset the demo.</span></span> <span data-ttu-id="6447b-532">これにより SalesOrderHeader_inmem テーブルと SalesOrderDetail_inmem テーブルのデータが削除され、元の SalesOrderHeader テーブルと SalesOrderDetail テーブルからデータが再送信されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-532">It deletes the data in the tables SalesOrderHeader_inmem and SalesOrderDetail_inmem, and re-seeds the data from the original tables SalesOrderHeader and SalesOrderDetail.</span></span>  
  
 <span data-ttu-id="6447b-533">この時点でテーブルの行は削除されていますが、メモリはすぐに再利用されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="6447b-533">Now, even though the rows in the tables have been deleted, this does not mean that memory is reclaimed immediately.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="6447b-534">では、メモリは、メモリ最適化テーブルの削除された行から、必要に応じてバックグラウンドで再利用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-534">reclaims memory from deleted rows in memory-optimized tables in the background, as needed.</span></span> <span data-ttu-id="6447b-535">デモのリセット後すぐにこれがわかります。システムにトランザクション ワークロードがない場合、削除された行のメモリはまだ再利用されていません。</span><span class="sxs-lookup"><span data-stu-id="6447b-535">You will see that immediately after demo reset, with no transactional workload on the system, memory from deleted rows is not yet reclaimed:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="6447b-536">**type**</span><span class="sxs-lookup"><span data-stu-id="6447b-536">**type**</span></span>|<span data-ttu-id="6447b-537">**name**</span><span class="sxs-lookup"><span data-stu-id="6447b-537">**name**</span></span>|<span data-ttu-id="6447b-538">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-538">**pages_MB**</span></span>|  
|<span data-ttu-id="6447b-539">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-539">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-540">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-540">Default</span></span>|<span data-ttu-id="6447b-541">2261</span><span class="sxs-lookup"><span data-stu-id="6447b-541">2261</span></span>|  
|<span data-ttu-id="6447b-542">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-542">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-543">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="6447b-543">DB_ID_5</span></span>|<span data-ttu-id="6447b-544">7396</span><span class="sxs-lookup"><span data-stu-id="6447b-544">7396</span></span>|  
|<span data-ttu-id="6447b-545">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-545">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-546">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-546">Default</span></span>|<span data-ttu-id="6447b-547">0</span><span class="sxs-lookup"><span data-stu-id="6447b-547">0</span></span>|  
|<span data-ttu-id="6447b-548">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-548">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-549">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-549">Default</span></span>|<span data-ttu-id="6447b-550">0</span><span class="sxs-lookup"><span data-stu-id="6447b-550">0</span></span>|  
  
 <span data-ttu-id="6447b-551">これは想定されている動作です。メモリはトランザクション ワークロードの実行中に再利用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-551">This is expected: memory will be reclaimed when the transactional workload is running.</span></span>  
  
 <span data-ttu-id="6447b-552">2 回目のデモ ワークロードの実行を開始すると、前に削除された行がクリーンアップされるため、メモリ使用率は最初は減少します。</span><span class="sxs-lookup"><span data-stu-id="6447b-552">If you start a second run of the demo workload you will see the memory utilization decrease initially, as the previously deleted rows are cleaned up.</span></span> <span data-ttu-id="6447b-553">ある時点で、メモリ サイズは再び増加し、ワークロードが終了するまで増加し続けます。</span><span class="sxs-lookup"><span data-stu-id="6447b-553">At some point the memory size will increase again, until the workload finishes.</span></span> <span data-ttu-id="6447b-554">デモをリセットしてから 1,000 万行を挿入した後のメモリ使用率は、最初の実行後の使用率とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="6447b-554">After inserting 10 million rows after demo reset, the memory utilization will be very similar to the utilization after the first run.</span></span> <span data-ttu-id="6447b-555">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-555">For example:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="6447b-556">**type**</span><span class="sxs-lookup"><span data-stu-id="6447b-556">**type**</span></span>|<span data-ttu-id="6447b-557">**name**</span><span class="sxs-lookup"><span data-stu-id="6447b-557">**name**</span></span>|<span data-ttu-id="6447b-558">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-558">**pages_MB**</span></span>|  
|<span data-ttu-id="6447b-559">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-559">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-560">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-560">Default</span></span>|<span data-ttu-id="6447b-561">1863</span><span class="sxs-lookup"><span data-stu-id="6447b-561">1863</span></span>|  
|<span data-ttu-id="6447b-562">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-562">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-563">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="6447b-563">DB_ID_5</span></span>|<span data-ttu-id="6447b-564">7390</span><span class="sxs-lookup"><span data-stu-id="6447b-564">7390</span></span>|  
|<span data-ttu-id="6447b-565">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-565">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-566">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-566">Default</span></span>|<span data-ttu-id="6447b-567">0</span><span class="sxs-lookup"><span data-stu-id="6447b-567">0</span></span>|  
|<span data-ttu-id="6447b-568">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="6447b-568">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="6447b-569">Default</span><span class="sxs-lookup"><span data-stu-id="6447b-569">Default</span></span>|<span data-ttu-id="6447b-570">0</span><span class="sxs-lookup"><span data-stu-id="6447b-570">0</span></span>|  
  
### <a name="disk-utilization-for-memory-optimized-tables"></a><span data-ttu-id="6447b-571">メモリ最適化テーブルのディスク使用率</span><span class="sxs-lookup"><span data-stu-id="6447b-571">Disk utilization for memory-optimized tables</span></span>  
 <span data-ttu-id="6447b-572">特定の時点におけるデータベースのチェックポイント ファイルに対する、全体的なディスク上のサイズを確認するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-572">The overall on-disk size for the checkpoint files of a database at a given time can be found using the query:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
  
```  
  
#### <a name="initial-state"></a><span data-ttu-id="6447b-573">初期状態</span><span class="sxs-lookup"><span data-stu-id="6447b-573">Initial state</span></span>  
 <span data-ttu-id="6447b-574">サンプル ファイル グループとサンプル メモリ最適化テーブルの初回作成時に、チェックポイント ファイルがいくつか事前作成され、システムによってデータが入力されます。事前作成されるチェックポイント ファイルの数は、システム内の論理プロセッサの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="6447b-574">When the sample filegroup and sample memory-optimized tables are created initially, a number of checkpoint files are pre-created and the system starts filling the files - the number of checkpoint files pre-created depends on the number of logical processors in the system.</span></span> <span data-ttu-id="6447b-575">最初はサンプルがかなり小さいため、初回作成後の事前作成されたファイルはほとんど空です。</span><span class="sxs-lookup"><span data-stu-id="6447b-575">As the sample is initially very small, the pre-created files will be mostly empty after initial create.</span></span>  
  
 <span data-ttu-id="6447b-576">16 個の論理プロセッサを持つコンピューター上のサンプルに対する、最初のディスク上のサイズを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-576">The following shows the initial on-disk size for the sample on a machine with 16 logical processors:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="6447b-577">**On-disk size in MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-577">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="6447b-578">2312</span><span class="sxs-lookup"><span data-stu-id="6447b-578">2312</span></span>|  
  
 <span data-ttu-id="6447b-579">チェックポイント ファイルのディスク上のサイズ (2.3 GB) と実際のデータ サイズ (約 30 MB) に大きな違いがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6447b-579">As you can see, there is a big discrepancy between the on-disk size of the checkpoint files, which is 2.3GB, and the actual data size, which is closer to 30MB.</span></span>  
  
 <span data-ttu-id="6447b-580">ディスク領域の使用率の詳細を確認するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="6447b-580">Looking closer at where the disk-space utilization comes from, you can use the following query.</span></span> <span data-ttu-id="6447b-581">このクエリから返されるディスクのサイズは、5 (REQUIRED FOR BACKUP/HA)、6 (IN TRANSITION TO TOMBSTONE)、または 7 (TOMBSTONE) の状態のファイルに関するおおよそのサイズです。</span><span class="sxs-lookup"><span data-stu-id="6447b-581">The size on disk returned by this query is approximate for files with state in 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE), or 7 (TOMBSTONE).</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
 <span data-ttu-id="6447b-582">サンプルの初期状態については、このクエリ結果は、16 個の論理プロセッサを持つサーバーに対する結果と似ています。</span><span class="sxs-lookup"><span data-stu-id="6447b-582">For the initial state of the sample, the result will look something like for a server with 16 logical processors:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="6447b-583">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="6447b-583">**state_desc**</span></span>|<span data-ttu-id="6447b-584">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="6447b-584">**file_type_desc**</span></span>|<span data-ttu-id="6447b-585">**count**</span><span class="sxs-lookup"><span data-stu-id="6447b-585">**count**</span></span>|<span data-ttu-id="6447b-586">**on-disk size MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-586">**on-disk size MB**</span></span>|  
|<span data-ttu-id="6447b-587">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="6447b-587">PRECREATED</span></span>|<span data-ttu-id="6447b-588">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-588">DATA</span></span>|<span data-ttu-id="6447b-589">16</span><span class="sxs-lookup"><span data-stu-id="6447b-589">16</span></span>|<span data-ttu-id="6447b-590">2048</span><span class="sxs-lookup"><span data-stu-id="6447b-590">2048</span></span>|  
|<span data-ttu-id="6447b-591">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="6447b-591">PRECREATED</span></span>|<span data-ttu-id="6447b-592">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-592">DELTA</span></span>|<span data-ttu-id="6447b-593">16</span><span class="sxs-lookup"><span data-stu-id="6447b-593">16</span></span>|<span data-ttu-id="6447b-594">128</span><span class="sxs-lookup"><span data-stu-id="6447b-594">128</span></span>|  
|<span data-ttu-id="6447b-595">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="6447b-595">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="6447b-596">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-596">DATA</span></span>|<span data-ttu-id="6447b-597">1</span><span class="sxs-lookup"><span data-stu-id="6447b-597">1</span></span>|<span data-ttu-id="6447b-598">128</span><span class="sxs-lookup"><span data-stu-id="6447b-598">128</span></span>|  
|<span data-ttu-id="6447b-599">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="6447b-599">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="6447b-600">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-600">DELTA</span></span>|<span data-ttu-id="6447b-601">1</span><span class="sxs-lookup"><span data-stu-id="6447b-601">1</span></span>|<span data-ttu-id="6447b-602">8</span><span class="sxs-lookup"><span data-stu-id="6447b-602">8</span></span>|  
  
 <span data-ttu-id="6447b-603">領域のほとんどが、事前作成されたデータとデルタ ファイルによって使用されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6447b-603">As you can see, most of the space is used by precreated data and delta files.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="6447b-604">により、1 組のファイル ペア (データとデルタ) が論理プロセッサごとに事前作成されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-604">pre-created one pair of (data, delta) files per logical processor.</span></span> <span data-ttu-id="6447b-605">また、さらに効率よくデータを挿入できるように、データ ファイルは 128 MB に、デルタ ファイルは 8 MB に事前にサイズ調整されています。</span><span class="sxs-lookup"><span data-stu-id="6447b-605">In addition, data files are pre-sized at 128MB, and delta files at 8MB, in order to make inserting data into these files more efficient.</span></span>  
  
 <span data-ttu-id="6447b-606">メモリ最適化テーブルの実際のデータは、1 つのデータ ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="6447b-606">The actual data in the memory-optimized tables is in the single data file.</span></span>  
  
#### <a name="after-running-the-workload"></a><span data-ttu-id="6447b-607">ワークロードの実行後</span><span class="sxs-lookup"><span data-stu-id="6447b-607">After running the workload</span></span>  
 <span data-ttu-id="6447b-608">1,000 万個の販売注文を挿入するテストを 1 回実行すると、全体的なディスク上のサイズは次のようになります (16 コア テスト サーバーの場合)。</span><span class="sxs-lookup"><span data-stu-id="6447b-608">After a single test run that inserts 10 million sales orders, the overall on-disk size looks something like this (for a 16-core test server):</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="6447b-609">**On-disk size in MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-609">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="6447b-610">8828</span><span class="sxs-lookup"><span data-stu-id="6447b-610">8828</span></span>|  
  
 <span data-ttu-id="6447b-611">ディスク上のサイズは 9 GB に迫っています。これは、データのインメモリ サイズに近い数値です。</span><span class="sxs-lookup"><span data-stu-id="6447b-611">The on-disk size is close to 9GB, which comes close to the in-memory size of the data.</span></span>  
  
 <span data-ttu-id="6447b-612">さまざまな状態のチェックポイント ファイルのサイズを詳しく確認します。</span><span class="sxs-lookup"><span data-stu-id="6447b-612">Looking more closely at the sizes of the checkpoint files across the various states:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="6447b-613">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="6447b-613">**state_desc**</span></span>|<span data-ttu-id="6447b-614">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="6447b-614">**file_type_desc**</span></span>|<span data-ttu-id="6447b-615">**count**</span><span class="sxs-lookup"><span data-stu-id="6447b-615">**count**</span></span>|<span data-ttu-id="6447b-616">**on-disk size MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-616">**on-disk size MB**</span></span>|  
|<span data-ttu-id="6447b-617">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="6447b-617">PRECREATED</span></span>|<span data-ttu-id="6447b-618">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-618">DATA</span></span>|<span data-ttu-id="6447b-619">16</span><span class="sxs-lookup"><span data-stu-id="6447b-619">16</span></span>|<span data-ttu-id="6447b-620">2048</span><span class="sxs-lookup"><span data-stu-id="6447b-620">2048</span></span>|  
|<span data-ttu-id="6447b-621">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="6447b-621">PRECREATED</span></span>|<span data-ttu-id="6447b-622">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-622">DELTA</span></span>|<span data-ttu-id="6447b-623">16</span><span class="sxs-lookup"><span data-stu-id="6447b-623">16</span></span>|<span data-ttu-id="6447b-624">128</span><span class="sxs-lookup"><span data-stu-id="6447b-624">128</span></span>|  
|<span data-ttu-id="6447b-625">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="6447b-625">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="6447b-626">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-626">DATA</span></span>|<span data-ttu-id="6447b-627">1</span><span class="sxs-lookup"><span data-stu-id="6447b-627">1</span></span>|<span data-ttu-id="6447b-628">128</span><span class="sxs-lookup"><span data-stu-id="6447b-628">128</span></span>|  
|<span data-ttu-id="6447b-629">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="6447b-629">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="6447b-630">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-630">DELTA</span></span>|<span data-ttu-id="6447b-631">1</span><span class="sxs-lookup"><span data-stu-id="6447b-631">1</span></span>|<span data-ttu-id="6447b-632">8</span><span class="sxs-lookup"><span data-stu-id="6447b-632">8</span></span>|  
  
 <span data-ttu-id="6447b-633">事前作成された 16 組のファイル ペアはまだあり、チェックポイントが閉じているので、準備状態です。</span><span class="sxs-lookup"><span data-stu-id="6447b-633">We still have 16 pairs of pre-created files, ready to go as checkpoints are closed.</span></span>  
  
 <span data-ttu-id="6447b-634">1 組の作成中のファイル ペアは、現在のチェックポイントが閉じるまで使用されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-634">There is one pair under construction, which is used until the current checkpoint is closed.</span></span> <span data-ttu-id="6447b-635">これにより、アクティブなチェックポイント ファイルと共に、約 6.5 GB のディスク使用率が 6.5 GB のメモリ内のデータに対して提供されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-635">Along with the active checkpoint files this gives about 6.5GB of disk utilization for 6.5GB of data in memory.</span></span> <span data-ttu-id="6447b-636">インデックスはディスクに保存されないため、この場合、全体的なディスクのサイズはメモリのサイズよりも小さくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6447b-636">Recall that indexes are not persisted on disk, and thus the overall size on disk is smaller than the size in memory in this case.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="6447b-637">デモのリセット後</span><span class="sxs-lookup"><span data-stu-id="6447b-637">After demo reset</span></span>  
 <span data-ttu-id="6447b-638">システムにトランザクション ワークロードがなく、また、データベース チェックポイントもない場合は、デモをリセットしても、ディスク領域はすぐには再利用されません。</span><span class="sxs-lookup"><span data-stu-id="6447b-638">After demo reset, disk space is not reclaimed immediately if there is no transactional workload on the system, and there are not database checkpoints.</span></span> <span data-ttu-id="6447b-639">チェックポイント ファイルがさまざまな段階を経て最終的に破棄されるようにするには、複数のチェックポイントとログの切り捨てイベントが発生する必要があり、これによりチェックポイント ファイルのマージとガベージ コレクションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="6447b-639">For checkpoint files to be moved through their various stages and eventually be discarded, a number of checkpoints and log truncation events need to happen, to initiate merge of checkpoint files, as well as to initiate garbage collection.</span></span> <span data-ttu-id="6447b-640">システムにトランザクション ワークロードがある場合 (また、完全復旧モデルの使用時に、定期的なログ バックアップを取得する場合)、システムがアイドル状態でなければ、デモ シナリオで示すように、これらは自動的に発生します。</span><span class="sxs-lookup"><span data-stu-id="6447b-640">These will happen automatically if you have a transactional workload in the system [and take regular log backups, in case you are using the FULL recovery model], but not when the system is idle, as in a demo scenario.</span></span>  
  
 <span data-ttu-id="6447b-641">この例では、デモのリセット後、次のように表示される場合があります</span><span class="sxs-lookup"><span data-stu-id="6447b-641">In the example, after demo reset, you may see something like</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="6447b-642">**On-disk size in MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-642">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="6447b-643">11839</span><span class="sxs-lookup"><span data-stu-id="6447b-643">11839</span></span>|  
  
 <span data-ttu-id="6447b-644">ディスク サイズは 12 GB 近くあり、デモをリセットする前の 9 GB を大幅に上回っています。</span><span class="sxs-lookup"><span data-stu-id="6447b-644">At nearly 12GB, this is significantly more than the 9GB we had before the demo reset.</span></span> <span data-ttu-id="6447b-645">これは、一部のチェックポイント ファイルのマージが開始されたにもかかわらず、まだインストールされていないマージ ターゲットがあるためです。また、クリーン アップされていないマージ ソース ファイルの存在も原因となっています。これを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-645">This is because some checkpoint file merges have been started, but some of the merge targets have not yet been installed, and some of the merge source files have not yet been cleaned up, as can be seen from the following:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="6447b-646">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="6447b-646">**state_desc**</span></span>|<span data-ttu-id="6447b-647">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="6447b-647">**file_type_desc**</span></span>|<span data-ttu-id="6447b-648">**count**</span><span class="sxs-lookup"><span data-stu-id="6447b-648">**count**</span></span>|<span data-ttu-id="6447b-649">**on-disk size MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-649">**on-disk size MB**</span></span>|  
|<span data-ttu-id="6447b-650">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="6447b-650">PRECREATED</span></span>|<span data-ttu-id="6447b-651">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-651">DATA</span></span>|<span data-ttu-id="6447b-652">16</span><span class="sxs-lookup"><span data-stu-id="6447b-652">16</span></span>|<span data-ttu-id="6447b-653">2048</span><span class="sxs-lookup"><span data-stu-id="6447b-653">2048</span></span>|  
|<span data-ttu-id="6447b-654">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="6447b-654">PRECREATED</span></span>|<span data-ttu-id="6447b-655">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-655">DELTA</span></span>|<span data-ttu-id="6447b-656">16</span><span class="sxs-lookup"><span data-stu-id="6447b-656">16</span></span>|<span data-ttu-id="6447b-657">128</span><span class="sxs-lookup"><span data-stu-id="6447b-657">128</span></span>|  
|<span data-ttu-id="6447b-658">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="6447b-658">ACTIVE</span></span>|<span data-ttu-id="6447b-659">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-659">DATA</span></span>|<span data-ttu-id="6447b-660">38</span><span class="sxs-lookup"><span data-stu-id="6447b-660">38</span></span>|<span data-ttu-id="6447b-661">5152</span><span class="sxs-lookup"><span data-stu-id="6447b-661">5152</span></span>|  
|<span data-ttu-id="6447b-662">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="6447b-662">ACTIVE</span></span>|<span data-ttu-id="6447b-663">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-663">DELTA</span></span>|<span data-ttu-id="6447b-664">38</span><span class="sxs-lookup"><span data-stu-id="6447b-664">38</span></span>|<span data-ttu-id="6447b-665">1331</span><span class="sxs-lookup"><span data-stu-id="6447b-665">1331</span></span>|  
|<span data-ttu-id="6447b-666">MERGE TARGET</span><span class="sxs-lookup"><span data-stu-id="6447b-666">MERGE TARGET</span></span>|<span data-ttu-id="6447b-667">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-667">DATA</span></span>|<span data-ttu-id="6447b-668">7</span><span class="sxs-lookup"><span data-stu-id="6447b-668">7</span></span>|<span data-ttu-id="6447b-669">896</span><span class="sxs-lookup"><span data-stu-id="6447b-669">896</span></span>|  
|<span data-ttu-id="6447b-670">MERGE TARGET</span><span class="sxs-lookup"><span data-stu-id="6447b-670">MERGE TARGET</span></span>|<span data-ttu-id="6447b-671">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-671">DELTA</span></span>|<span data-ttu-id="6447b-672">7</span><span class="sxs-lookup"><span data-stu-id="6447b-672">7</span></span>|<span data-ttu-id="6447b-673">56</span><span class="sxs-lookup"><span data-stu-id="6447b-673">56</span></span>|  
|<span data-ttu-id="6447b-674">MERGED SOURCE</span><span class="sxs-lookup"><span data-stu-id="6447b-674">MERGED SOURCE</span></span>|<span data-ttu-id="6447b-675">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-675">DATA</span></span>|<span data-ttu-id="6447b-676">13</span><span class="sxs-lookup"><span data-stu-id="6447b-676">13</span></span>|<span data-ttu-id="6447b-677">1772</span><span class="sxs-lookup"><span data-stu-id="6447b-677">1772</span></span>|  
|<span data-ttu-id="6447b-678">MERGED SOURCE</span><span class="sxs-lookup"><span data-stu-id="6447b-678">MERGED SOURCE</span></span>|<span data-ttu-id="6447b-679">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-679">DELTA</span></span>|<span data-ttu-id="6447b-680">13</span><span class="sxs-lookup"><span data-stu-id="6447b-680">13</span></span>|<span data-ttu-id="6447b-681">455</span><span class="sxs-lookup"><span data-stu-id="6447b-681">455</span></span>|  
  
 <span data-ttu-id="6447b-682">トランザクション アクティビティがシステムで発生すると、マージ ターゲットがインストールされ、マージされたソースがクリーン アップされます。</span><span class="sxs-lookup"><span data-stu-id="6447b-682">Merge targets are installed and merged source are cleaned up as transactional activity happens in the system.</span></span>  
  
 <span data-ttu-id="6447b-683">2 回目のデモ ワークロードを実行してからデモをリセットし、1,000 万個の販売注文を挿入すると、最初のワークロードの実行中に作成されたファイルはクリーンアップされています。</span><span class="sxs-lookup"><span data-stu-id="6447b-683">After a second run of the demo workload, inserting 10 million sales orders after the demo reset, you will see that the files constructed during the first run of the workload have been cleaned up.</span></span> <span data-ttu-id="6447b-684">ワークロードの実行中に前のクエリを複数回実行した場合、チェックポイント ファイルはさまざまな段階を経て進行します。</span><span class="sxs-lookup"><span data-stu-id="6447b-684">If you run the above query several times while the workload is running, you can see the checkpoint files make their way through the various stages.</span></span>  
  
 <span data-ttu-id="6447b-685">2 回目のワークロードを実行してから 1,000 万個の販売注文を挿入した場合、そのディスク使用率は最初の実行後の使用率とよく似ています。ただし、システムはもともと動的であるため、必ずしも同じであるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="6447b-685">After the second run of the workload insert 10 million sales orders you will see disk utilization very similar to, though not necessarily the same as after the first run, as the system is dynamic in nature.</span></span> <span data-ttu-id="6447b-686">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6447b-686">For example:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="6447b-687">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="6447b-687">**state_desc**</span></span>|<span data-ttu-id="6447b-688">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="6447b-688">**file_type_desc**</span></span>|<span data-ttu-id="6447b-689">**count**</span><span class="sxs-lookup"><span data-stu-id="6447b-689">**count**</span></span>|<span data-ttu-id="6447b-690">**on-disk size MB**</span><span class="sxs-lookup"><span data-stu-id="6447b-690">**on-disk size MB**</span></span>|  
|<span data-ttu-id="6447b-691">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="6447b-691">PRECREATED</span></span>|<span data-ttu-id="6447b-692">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-692">DATA</span></span>|<span data-ttu-id="6447b-693">16</span><span class="sxs-lookup"><span data-stu-id="6447b-693">16</span></span>|<span data-ttu-id="6447b-694">2048</span><span class="sxs-lookup"><span data-stu-id="6447b-694">2048</span></span>|  
|<span data-ttu-id="6447b-695">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="6447b-695">PRECREATED</span></span>|<span data-ttu-id="6447b-696">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-696">DELTA</span></span>|<span data-ttu-id="6447b-697">16</span><span class="sxs-lookup"><span data-stu-id="6447b-697">16</span></span>|<span data-ttu-id="6447b-698">128</span><span class="sxs-lookup"><span data-stu-id="6447b-698">128</span></span>|  
|<span data-ttu-id="6447b-699">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="6447b-699">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="6447b-700">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-700">DATA</span></span>|<span data-ttu-id="6447b-701">2</span><span class="sxs-lookup"><span data-stu-id="6447b-701">2</span></span>|<span data-ttu-id="6447b-702">268</span><span class="sxs-lookup"><span data-stu-id="6447b-702">268</span></span>|  
|<span data-ttu-id="6447b-703">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="6447b-703">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="6447b-704">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-704">DELTA</span></span>|<span data-ttu-id="6447b-705">2</span><span class="sxs-lookup"><span data-stu-id="6447b-705">2</span></span>|<span data-ttu-id="6447b-706">16</span><span class="sxs-lookup"><span data-stu-id="6447b-706">16</span></span>|  
|<span data-ttu-id="6447b-707">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="6447b-707">ACTIVE</span></span>|<span data-ttu-id="6447b-708">DATA</span><span class="sxs-lookup"><span data-stu-id="6447b-708">DATA</span></span>|<span data-ttu-id="6447b-709">41</span><span class="sxs-lookup"><span data-stu-id="6447b-709">41</span></span>|<span data-ttu-id="6447b-710">5608</span><span class="sxs-lookup"><span data-stu-id="6447b-710">5608</span></span>|  
|<span data-ttu-id="6447b-711">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="6447b-711">ACTIVE</span></span>|<span data-ttu-id="6447b-712">DELTA</span><span class="sxs-lookup"><span data-stu-id="6447b-712">DELTA</span></span>|<span data-ttu-id="6447b-713">41</span><span class="sxs-lookup"><span data-stu-id="6447b-713">41</span></span>|<span data-ttu-id="6447b-714">328</span><span class="sxs-lookup"><span data-stu-id="6447b-714">328</span></span>|  
  
 <span data-ttu-id="6447b-715">この場合、"under construction" 状態のチェックポイント ファイルのペアが 2 組あります。これは、複数のファイル ペアが、おそらくワークロードにおける高レベルのコンカレンシーが原因で、"under construction" 状態に移行されたことを意味します。</span><span class="sxs-lookup"><span data-stu-id="6447b-715">In this case, there are two checkpoint file pairs in the 'under construction' state, which means multiple file pairs were moved to the 'under construction' state, likely due to the high level of concurrency in the workload.</span></span> <span data-ttu-id="6447b-716">一方、複数の同時実行スレッドには新しいファイル ペアが必要だったため、ペアの状態が "precreated" から "under construction" に移行されました。</span><span class="sxs-lookup"><span data-stu-id="6447b-716">Multiple concurrent threads required a new file pair at the same time, and thus moved a pair from 'precreated' to 'under construction'.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6447b-717">参照</span><span class="sxs-lookup"><span data-stu-id="6447b-717">See Also</span></span>  
 [<span data-ttu-id="6447b-718">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="6447b-718">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
