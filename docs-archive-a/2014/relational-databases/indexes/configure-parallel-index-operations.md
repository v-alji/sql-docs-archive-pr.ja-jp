---
title: 並列インデックス操作の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index parallel operations [SQL Server]
- processors [SQL Server], parallel index operations
- max degree of parallelism option
- MAXDOP index option, parallel index operations
- parallel index operations [SQL Server]
ms.assetid: 8ec8c71e-5fc1-443a-92da-136ee3fc7f88
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8831aadae15af03a05f4ab03cfe514e54566df1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631897"
---
# <a name="configure-parallel-index-operations"></a><span data-ttu-id="456eb-102">並列インデックス操作の構成</span><span class="sxs-lookup"><span data-stu-id="456eb-102">Configure Parallel Index Operations</span></span>
  <span data-ttu-id="456eb-103">このトピックでは、並列処理の最大限度に関する定義と、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してこの設定を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="456eb-103">This topic defines max degree of parallelism and explains how to modify this setting in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="456eb-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 以上を実行するマルチプロセッサ コンピューターでは、他のクエリと同様に、インデックスのステートメントがこのステートメントに関連付けられているスキャン操作、並べ替え操作、インデックス操作などの実行に、複数のプロセッサを使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="456eb-104">On multiprocessor computers that are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise or higher, index statements may use multiple processors to perform the scan, sort, and index operations associated with the index statement just like other queries do.</span></span> <span data-ttu-id="456eb-105">1 つのインデックス ステートメントの実行に使用されるプロセッサの数は、 [max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) 構成オプション、現在のワークロード、およびインデックス統計によって決まります。</span><span class="sxs-lookup"><span data-stu-id="456eb-105">The number of processors used to run a single index statement is determined by the [max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) configuration option, the current workload, and the index statistics.</span></span> <span data-ttu-id="456eb-106">max degree of parallelism オプションによって、並列プランの実行で使用するプロセッサの最大数が決まります。</span><span class="sxs-lookup"><span data-stu-id="456eb-106">The max degree of parallelism option determines the maximum number of processors to use in parallel plan execution.</span></span> <span data-ttu-id="456eb-107">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によりシステムがビジー状態であることが検出されると、ステートメントの実行が開始される前に、インデックス操作の並列処理の次数が自動的に削減されます。</span><span class="sxs-lookup"><span data-stu-id="456eb-107">If the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] detects that the system is busy, the degree of parallelism of the index operation is automatically reduced before statement execution starts.</span></span> <span data-ttu-id="456eb-108">[!INCLUDE[ssDE](../../includes/ssde-md.md)] では、パーティション分割されていないインデックスの先頭のキー列で個々の値の数が制限されている場合や、個々の値の頻度が大きく異なる場合に、並列処理の次数を減らすこともできます。</span><span class="sxs-lookup"><span data-stu-id="456eb-108">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can also reduce the degree of parallelism if the leading key column of a non-partitioned index has a limited number of distinct values or the frequency of each distinct value varies significantly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="456eb-109">並列インデックス操作は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="456eb-109">Parallel index operations are not available in every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition.</span></span> <span data-ttu-id="456eb-110">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="456eb-110">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="456eb-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="456eb-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="456eb-112">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="456eb-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="456eb-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="456eb-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="456eb-114">Security</span><span class="sxs-lookup"><span data-stu-id="456eb-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="456eb-115">**並列処理の最大限度を設定するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="456eb-115">**To set the max degree of parallelism, using:**</span></span>  
  
     [<span data-ttu-id="456eb-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="456eb-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="456eb-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="456eb-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="456eb-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="456eb-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="456eb-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="456eb-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="456eb-120">通常は、クエリ オプティマイザーによって使用されるプロセッサ数で、最適なパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="456eb-120">The number of processors that are used by the query optimizer typically provides optimal performance.</span></span> <span data-ttu-id="456eb-121">ただし、非常に大きなインデックスの作成、再構築、または削除などの操作ではリソースが集中的に消費されるので、インデックス操作中に、他のアプリケーションやデータベース操作でリソースが不足する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="456eb-121">However, operations such as creating, rebuilding, or dropping very large indexes are resource intensive and can cause insufficient resources for other applications and database operations for the duration of the index operation.</span></span> <span data-ttu-id="456eb-122">この問題が発生した場合は、インデックス操作に使用するプロセッサ数を制限することで、インデックス ステートメントの実行に使用される最大プロセッサ数を手動で構成できます。</span><span class="sxs-lookup"><span data-stu-id="456eb-122">When this problem occurs, you can manually configure the maximum number of processors that are used to run the index statement by limiting the number of processors to use for the index operation.</span></span>  
  
-   <span data-ttu-id="456eb-123">MAXDOP インデックス オプションは、このオプションを指定しているクエリに関してのみ、max degree of parallelism 構成オプションをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="456eb-123">The MAXDOP index option overrides the max degree of parallelism configuration option only for the query specifying this option.</span></span> <span data-ttu-id="456eb-124">次の表に、max degree of parallelism 構成オプションと MAXDOP インデックス オプションで指定できる有効な整数値を示します。</span><span class="sxs-lookup"><span data-stu-id="456eb-124">The following table lists the valid integer values that can be specified with the max degree of parallelism configuration option and the MAXDOP index option.</span></span>  
  
    |<span data-ttu-id="456eb-125">値</span><span class="sxs-lookup"><span data-stu-id="456eb-125">Value</span></span>|<span data-ttu-id="456eb-126">説明</span><span class="sxs-lookup"><span data-stu-id="456eb-126">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="456eb-127">0</span><span class="sxs-lookup"><span data-stu-id="456eb-127">0</span></span>|<span data-ttu-id="456eb-128">現在のシステム ワークロードに応じて、使用する CPU 数をサーバーが決定するように指定します。</span><span class="sxs-lookup"><span data-stu-id="456eb-128">Specifies that the server determines the number of CPUs that are used, depending on the current system workload.</span></span> <span data-ttu-id="456eb-129">この値は既定値であり、推奨の設定です。</span><span class="sxs-lookup"><span data-stu-id="456eb-129">This is the default value and recommended setting.</span></span>|  
    |<span data-ttu-id="456eb-130">1</span><span class="sxs-lookup"><span data-stu-id="456eb-130">1</span></span>|<span data-ttu-id="456eb-131">並列プラン生成を抑制します。</span><span class="sxs-lookup"><span data-stu-id="456eb-131">Suppresses parallel plan generation.</span></span> <span data-ttu-id="456eb-132">操作は順番に実行されます。</span><span class="sxs-lookup"><span data-stu-id="456eb-132">The operation will be executed serially.</span></span>|  
    |<span data-ttu-id="456eb-133">2 ～ 64</span><span class="sxs-lookup"><span data-stu-id="456eb-133">2-64</span></span>|<span data-ttu-id="456eb-134">プロセッサ数が指定値まで制限されます。</span><span class="sxs-lookup"><span data-stu-id="456eb-134">Limits the number of processors to the specified value.</span></span> <span data-ttu-id="456eb-135">現在のワークロードによっては、使用されるプロセッサ数が少なくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="456eb-135">Fewer processors may be used depending on the current workload.</span></span> <span data-ttu-id="456eb-136">使用できる CPU 数よりも大きな値を指定した場合は、実際に使用できる CPU 数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="456eb-136">If a value larger than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>|  
  
-   <span data-ttu-id="456eb-137">インデックスの並列実行と MAXDOP インデックス オプションは、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに適用されます。</span><span class="sxs-lookup"><span data-stu-id="456eb-137">Parallel index execution and the MAXDOP index option apply to the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    -   <span data-ttu-id="456eb-138">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="456eb-138">CREATE INDEX</span></span>  
  
    -   <span data-ttu-id="456eb-139">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="456eb-139">ALTER INDEX REBUILD</span></span>  
  
    -   <span data-ttu-id="456eb-140">DROP INDEX (このステートメントは、クラスター化インデックスのみに適用されます。)</span><span class="sxs-lookup"><span data-stu-id="456eb-140">DROP INDEX (This applies to clustered indexes only.)</span></span>  
  
    -   <span data-ttu-id="456eb-141">ALTER TABLE ADD (インデックス) CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="456eb-141">ALTER TABLE ADD (index) CONSTRAINT</span></span>  
  
    -   <span data-ttu-id="456eb-142">ALTER TABLE DROP (クラスター化インデックス) CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="456eb-142">ALTER TABLE DROP (clustered index) CONSTRAINT</span></span>  
  
-   <span data-ttu-id="456eb-143">ALTER INDEX REORGANIZE ステートメントには、MAXDOP インデックス オプションを指定できません。</span><span class="sxs-lookup"><span data-stu-id="456eb-143">The MAXDOP index option cannot be specified in the ALTER INDEX REORGANIZE statement.</span></span>  
  
-   <span data-ttu-id="456eb-144">クエリ オプティマイザーが構築操作に 2 次以上の並列処理を適用すると、並べ替えを必要とするパーティション インデックス操作に必要なメモリ容量がさらに大きくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="456eb-144">Memory requirements for partitioned index operations that require sorting can be greater if the query optimizer applies degrees of parallelism to the build operation.</span></span> <span data-ttu-id="456eb-145">並列処理の次数が高いと、必要なメモリ容量も大きくなります。</span><span class="sxs-lookup"><span data-stu-id="456eb-145">The higher the degrees of parallelism, the greater the memory requirement is.</span></span> <span data-ttu-id="456eb-146">詳細については、「 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="456eb-146">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="456eb-147">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="456eb-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="456eb-148">Permissions</span><span class="sxs-lookup"><span data-stu-id="456eb-148">Permissions</span></span>  
 <span data-ttu-id="456eb-149">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="456eb-149">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="456eb-150">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="456eb-150">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-index"></a><span data-ttu-id="456eb-151">インデックスに並列処理の最大限度を設定するには</span><span class="sxs-lookup"><span data-stu-id="456eb-151">To set max degree of parallelism on an index</span></span>  
  
1.  <span data-ttu-id="456eb-152">オブジェクト エクスプローラーで、インデックスの並列処理の最大限度を設定するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="456eb-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to set max degree of parallelism for an index.</span></span>  
  
2.  <span data-ttu-id="456eb-153">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="456eb-153">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="456eb-154">インデックスの並列処理の最大限度を設定するテーブルをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="456eb-154">Click the plus sign to expand the table on which you want to set max degree of parallelism for an index.</span></span>  
  
4.  <span data-ttu-id="456eb-155">**[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="456eb-155">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="456eb-156">並列処理の最大限度を設定するインデックスを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="456eb-156">Right-click the index for which you want to set the max degree of parallelism and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="456eb-157">**[ページの選択]** の **[オプション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="456eb-157">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="456eb-158">**[並列処理の最大限度]** を選択し、1 ～ 64 の範囲の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="456eb-158">Select **Maximum degree of parallelism**, and then enter some value between 1 and 64.</span></span>  
  
8.  <span data-ttu-id="456eb-159">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="456eb-159">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="456eb-160">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="456eb-160">Using Transact-SQL</span></span>  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-existing-index"></a><span data-ttu-id="456eb-161">既存のインデックスに並列処理の最大限度を設定するには</span><span class="sxs-lookup"><span data-stu-id="456eb-161">To set max degree of parallelism on an existing index</span></span>  
  
1.  <span data-ttu-id="456eb-162">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="456eb-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="456eb-163">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="456eb-163">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="456eb-164">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="456eb-164">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Alters the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table so that, if the server has eight or more processors, the Database Engine will limit the execution of the index operation to eight or fewer processors.  
    */  
    ALTER INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor  
    REBUILD WITH (MAXDOP=8);   
    GO  
    ```  
  
 <span data-ttu-id="456eb-165">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="456eb-165">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
#### <a name="set-max-degree-of-parallelism-on-a-new-index"></a><span data-ttu-id="456eb-166">新しいインデックスに並列処理の最大限度を設定する方法</span><span class="sxs-lookup"><span data-stu-id="456eb-166">Set max degree of parallelism on a new index</span></span>  
  
1.  <span data-ttu-id="456eb-167">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="456eb-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="456eb-168">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="456eb-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="456eb-169">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="456eb-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE INDEX IX_ProductVendor_NewVendorID   
    ON Purchasing.ProductVendor (BusinessEntityID)  
    WITH (MAXDOP=8);  
    GO  
    ```  
  
 <span data-ttu-id="456eb-170">詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="456eb-170">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
