---
title: データ圧縮 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- page compression [Database Engine]
- indexes [SQL Server], compressed
- compressed indexes [SQL Server]
- storage compression [Database Engine]
- tables [SQL Server], compressed
- storage [SQL Server], compressed
- compression [SQL Server]
- row compression [Database Engine]
- compression [SQL Server], about compressed tables and indexes
- data compression [Database Engine]
- compressed tables [SQL Server]
ms.assetid: 5f33e686-e115-4687-bd39-a00c48646513
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 48c4b11963d8e05ff7787ce9200329daf2e899ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643971"
---
# <a name="data-compression"></a><span data-ttu-id="57346-102">データ圧縮</span><span class="sxs-lookup"><span data-stu-id="57346-102">Data Compression</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="57346-103">では、行ストア インデックスおよびテーブルのための行およびページの圧縮がサポートされます。また、列ストアと、列ストアおよびインデックスのための列ストアの保存用圧縮もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="57346-103">supports row and page compression for rowstore tables and indexes, and supports columnstore and columnstore archival compression for columnstore tables and indexes.</span></span>  
  
 <span data-ttu-id="57346-104">行ストア テーブルおよびインデックスについては、データベースのサイズを小さくするためにデータ圧縮機能を使用してください。</span><span class="sxs-lookup"><span data-stu-id="57346-104">For rowstore tables and indexes, use the data compression feature to help reduce the size of the database.</span></span> <span data-ttu-id="57346-105">領域を削減するだけでなく、データ圧縮を使用すると、データを格納するページ数が少なくなり、クエリがディスクから読み取る必要のあるページが少なくなるため、大量の I/O が発生する作業のパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="57346-105">In addition to saving space, data compression can help improve performance of I/O intensive workloads because the data is stored in fewer pages and queries need to read fewer pages from disk.</span></span> <span data-ttu-id="57346-106">ただし、アプリケーションとの間でデータが交換される間は、データの圧縮と圧縮解除のためデータベース サーバーで追加の CPU リソースが必要になります。</span><span class="sxs-lookup"><span data-stu-id="57346-106">However, extra CPU resources are required on the database server to compress and decompress the data, while data is exchanged with the application.</span></span> <span data-ttu-id="57346-107">次のデータベース オブジェクトで行とページの圧縮を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="57346-107">You can configure row and page compression on the following database objects:</span></span>  
  
-   <span data-ttu-id="57346-108">ヒープとして格納されているテーブル全体。</span><span class="sxs-lookup"><span data-stu-id="57346-108">A whole table that is stored as a heap.</span></span>  
  
-   <span data-ttu-id="57346-109">クラスター化インデックスとして格納されているテーブル全体。</span><span class="sxs-lookup"><span data-stu-id="57346-109">A whole table that is stored as a clustered index.</span></span>  
  
-   <span data-ttu-id="57346-110">非クラスター化インデックス全体。</span><span class="sxs-lookup"><span data-stu-id="57346-110">A whole nonclustered index.</span></span>  
  
-   <span data-ttu-id="57346-111">インデックス付きビュー全体。</span><span class="sxs-lookup"><span data-stu-id="57346-111">A whole indexed view.</span></span>  
  
-   <span data-ttu-id="57346-112">パーティション分割されているテーブルおよびインデックスの場合、パーティションごとに圧縮オプションを構成することができ、オブジェクトの各パーティションを同じ圧縮設定にする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="57346-112">For partitioned tables and indexes, you can configure the compression option for each partition, and the various partitions of an object do not have to have the same compression setting.</span></span>  
  
 <span data-ttu-id="57346-113">列ストア テーブルおよびインデックスの場合、すべての列ストア テーブルおよびインデックスで列ストア圧縮が使用されます。これはユーザーが構成できません。</span><span class="sxs-lookup"><span data-stu-id="57346-113">For columnstore tables and indexes, all columnstore tables and indexes always use columnstore compression and this is not user configurable.</span></span> <span data-ttu-id="57346-114">データを格納および取得できる CPU リソースと時間に余裕がある場合にデータ サイズをさらに小さくするには、列ストアの保存用圧縮を使用します。</span><span class="sxs-lookup"><span data-stu-id="57346-114">Use columnstore archival compression to further reduce the data size for situations when you can afford extra time and CPU resources to store and retrieve the data.</span></span>  <span data-ttu-id="57346-115">次のデータベース オブジェクトで列ストアの保存用圧縮を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="57346-115">You can configure columnstore archival compression on the following database objects:</span></span>  
  
-   <span data-ttu-id="57346-116">列ストア テーブル全体またはクラスター化列ストア インデックス全体。</span><span class="sxs-lookup"><span data-stu-id="57346-116">A whole columnstore table or a whole clustered columnstore index.</span></span>  <span data-ttu-id="57346-117">列ストア テーブルはクラスター化列ストア インデックスとして格納されるため、どちらの方法を使っても同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="57346-117">Since a columnstore table is stored as a clustered columnstore index, both approaches have the same results.</span></span>  
  
-   <span data-ttu-id="57346-118">非クラスター化列ストア インデックス全体。</span><span class="sxs-lookup"><span data-stu-id="57346-118">A whole nonclustered columnstore index.</span></span>  
  
-   <span data-ttu-id="57346-119">パーティション分割されている列ストア テーブルおよび列ストア インデックスの場合、パーティションごとに保存用圧縮オプションを構成することができ、オブジェクトの各パーティションを同じ保存用圧縮設定にする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="57346-119">For partitioned columnstore tables and columnstore indexes, you can configure the archival compression option for each partition, and the various partitions do not have to have the same archival compression setting.</span></span>  
  
## <a name="considerations-for-when-you-use-row-and-page-compression"></a><span data-ttu-id="57346-120">行とページの圧縮の使用に関する注意点</span><span class="sxs-lookup"><span data-stu-id="57346-120">Considerations for When You Use Row and Page Compression</span></span>  
 <span data-ttu-id="57346-121">行とページの圧縮を使用する際は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="57346-121">When you use row and page compression, be aware the following considerations:</span></span>  
  
-   <span data-ttu-id="57346-122">データの圧縮に関する詳細情報は、Service Pack または今後のリリースで予告なしに変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="57346-122">The details of data compression are subject to change without notice in service packs or subsequent releases.</span></span>  
  
-   <span data-ttu-id="57346-123">圧縮は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディッションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="57346-123">Compression is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="57346-124">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="57346-124">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="57346-125">圧縮は、システム テーブルには使用できません。</span><span class="sxs-lookup"><span data-stu-id="57346-125">Compression is not available for system tables.</span></span>  
  
-   <span data-ttu-id="57346-126">圧縮を使用すると、ページに格納できる行数が増えますが、テーブルまたはインデックスの最大行サイズは変更されません。</span><span class="sxs-lookup"><span data-stu-id="57346-126">Compression can allow more rows to be stored on a page, but does not change the maximum row size of a table or index.</span></span>  
  
-   <span data-ttu-id="57346-127">最大行サイズに圧縮のオーバーヘッドを加えると最大行サイズが 8,060 バイトを超える場合、テーブルで圧縮を有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="57346-127">A table cannot be enabled for compression when the maximum row size plus the compression overhead exceeds the maximum row size of 8060 bytes.</span></span> <span data-ttu-id="57346-128">たとえば、c1 および c2 という列を含むテーブルは、 `char(8000)` `char(53)` 圧縮のオーバーヘッドが増加するため、圧縮できません。</span><span class="sxs-lookup"><span data-stu-id="57346-128">For example, a table that has the columns c1`char(8000)` and c2`char(53)` cannot be compressed because of the additional compression overhead.</span></span> <span data-ttu-id="57346-129">vardecimal ストレージ形式を使用する場合は、この形式が有効になると行サイズのチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="57346-129">When the vardecimal storage format is used, the row-size check is performed when the format is enabled.</span></span> <span data-ttu-id="57346-130">行とページの圧縮の場合は、オブジェクトが最初に圧縮されるときに行サイズのチェックが実行され、各行が挿入または変更されるときにもチェックされます。</span><span class="sxs-lookup"><span data-stu-id="57346-130">For row and page compression, the row-size check is performed when the object is initially compressed, and then checked as each row is inserted or modified.</span></span> <span data-ttu-id="57346-131">圧縮では、次の 2 つのルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="57346-131">Compression enforces the following two rules:</span></span>  
  
    -   <span data-ttu-id="57346-132">固定長の型に対する更新が常に成功する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57346-132">An update to a fixed-length type must always succeed.</span></span>  
  
    -   <span data-ttu-id="57346-133">データ圧縮の無効化が常に成功する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57346-133">Disabling data compression must always succeed.</span></span> <span data-ttu-id="57346-134">圧縮された行がページに収まる場合 (行のサイズが 8,060 バイト未満の場合) でも、圧縮されていないときの行に収まらない更新は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって回避されます。</span><span class="sxs-lookup"><span data-stu-id="57346-134">Even if the compressed row fits on the page, which means that it is less than 8060 bytes; [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prevents updates that would not fit on the row when it is uncompressed.</span></span>  
  
-   <span data-ttu-id="57346-135">パーティションの一覧を指定する場合は、個々のパーティションの圧縮の種類を ROW、PAGE、または NONE に設定できます。</span><span class="sxs-lookup"><span data-stu-id="57346-135">When a list of partitions is specified, the compression type can be set to ROW, PAGE, or NONE on individual partitions.</span></span> <span data-ttu-id="57346-136">パーティションの一覧を指定しない場合は、すべてのパーティションがステートメントで指定されたデータ圧縮プロパティを使用して設定されます。</span><span class="sxs-lookup"><span data-stu-id="57346-136">If the list of partitions is not specified, all partitions are set with the data compression property that is specified in the statement.</span></span> <span data-ttu-id="57346-137">特に指定しない限り、データ圧縮はテーブルまたはインデックスの作成時に NONE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="57346-137">When a table or index is created, data compression is set to NONE unless otherwise specified.</span></span> <span data-ttu-id="57346-138">特に指定しない限り、既存の圧縮はテーブルの変更時にも保持されます。</span><span class="sxs-lookup"><span data-stu-id="57346-138">When a table is modified, the existing compression is preserved unless otherwise specified.</span></span>  
  
-   <span data-ttu-id="57346-139">範囲外の一連のパーティションまたは単独のパーティションを指定すると、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="57346-139">If you specify a list of partitions or a partition that is out of range, an error will be generated.</span></span>  
  
-   <span data-ttu-id="57346-140">テーブルの圧縮プロパティは非クラスター化インデックスに継承されません。</span><span class="sxs-lookup"><span data-stu-id="57346-140">Nonclustered indexes do not inherit the compression property of the table.</span></span> <span data-ttu-id="57346-141">インデックスを圧縮するには、インデックスの圧縮プロパティを明示的に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57346-141">To compress indexes, you must explicitly set the compression property of the indexes.</span></span> <span data-ttu-id="57346-142">既定では、インデックスの圧縮設定はインデックスの作成時に NONE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="57346-142">By default, the compression setting for indexes will set to NONE when the index is created.</span></span>  
  
-   <span data-ttu-id="57346-143">ヒープにクラスター化インデックスを作成する場合、圧縮状態を特に指定しない限り、ヒープの圧縮状態がクラスター化インデックスに継承されます。</span><span class="sxs-lookup"><span data-stu-id="57346-143">When a clustered index is created on a heap, the clustered index inherits the compression state of the heap unless an alternative compression state is specified.</span></span>  
  
-   <span data-ttu-id="57346-144">ヒープがページ レベルの圧縮用に構成されている場合、ページでは、次の方法によるページ レベルの圧縮のみが受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="57346-144">When a heap is configured for page-level compression, pages receive page-level compression only in the following ways:</span></span>  
  
    -   <span data-ttu-id="57346-145">データは一括最適化を有効にして一括インポートされます。</span><span class="sxs-lookup"><span data-stu-id="57346-145">Data is bulk imported with bulk optimizations enabled.</span></span>  
  
    -   <span data-ttu-id="57346-146">INSERT INTO ...WITH (TABLOCK) 構文とテーブルに非クラスター化インデックスはありません。</span><span class="sxs-lookup"><span data-stu-id="57346-146">Data is inserted using INSERT INTO ... WITH (TABLOCK) syntax and the table does not have a nonclustered index.</span></span>  
  
    -   <span data-ttu-id="57346-147">PAGE 圧縮オプションを指定して ALTER TABLE ...REBUILD ステートメントを実行し、テーブルを再構築する方法</span><span class="sxs-lookup"><span data-stu-id="57346-147">A table is rebuilt by executing the ALTER TABLE ... REBUILD statement with the PAGE compression option.</span></span>  
  
-   <span data-ttu-id="57346-148">DML 操作の一部としてヒープに割り当てられた新しいページでは、ヒープが再構築されるまで PAGE 圧縮は使用されません。</span><span class="sxs-lookup"><span data-stu-id="57346-148">New pages allocated in a heap as part of DML operations will not use PAGE compression until the heap is rebuilt.</span></span> <span data-ttu-id="57346-149">圧縮を解除してから再適用するか、クラスター化インデックスを作成してから削除することで、ヒープを再構築します。</span><span class="sxs-lookup"><span data-stu-id="57346-149">Rebuild the heap by removing and reapplying compression, or by creating and removing a clustered index.</span></span>  
  
-   <span data-ttu-id="57346-150">ヒープの圧縮設定を変更するには、テーブルのすべての非クラスター化インデックスを再構築して、ヒープ内の新しい行位置へのポインターを持つようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57346-150">Changing the compression setting of a heap requires all nonclustered indexes on the table to be rebuilt so that they have pointers to the new row locations in the heap.</span></span>  
  
-   <span data-ttu-id="57346-151">ROW または PAGE 圧縮はオンラインまたはオフラインで有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="57346-151">You can enable or disable ROW or PAGE compression online or offline.</span></span> <span data-ttu-id="57346-152">オンライン操作の場合、ヒープに対する圧縮の有効化はシングル スレッドです。</span><span class="sxs-lookup"><span data-stu-id="57346-152">Enabling compression on a heap is single threaded for an online operation.</span></span>  
  
-   <span data-ttu-id="57346-153">行またはページの圧縮を有効または無効にするために必要なディスク空き容量は、インデックスを作成または再構築するために必要なディスク空き容量と同じです。</span><span class="sxs-lookup"><span data-stu-id="57346-153">The disk space requirements for enabling or disabling row or page compression are the same as for creating or rebuilding an index.</span></span> <span data-ttu-id="57346-154">パーティション データの場合は、一度に 1 つのパーティションの圧縮を有効または無効にすることによって必要な空き容量を削減できます。</span><span class="sxs-lookup"><span data-stu-id="57346-154">For partitioned data, you can reduce the space that is required by enabling or disabling compression for one partition at a time.</span></span>  
  
-   <span data-ttu-id="57346-155">パーティション テーブルのパーティションの圧縮状態を調べるには、sys.partitions カタログ ビューの data_compression 列に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="57346-155">To determine the compression state of partitions in a partitioned table, query the data_compression column of the sys.partitions catalog view.</span></span>  
  
-   <span data-ttu-id="57346-156">インデックスを圧縮する場合、行とページの両方の圧縮を使用してリーフ レベルのページを圧縮できます。</span><span class="sxs-lookup"><span data-stu-id="57346-156">When you are compressing indexes, leaf-level pages can be compressed with both row and page compression.</span></span> <span data-ttu-id="57346-157">リーフ レベル以外のページでは、ページの圧縮は受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="57346-157">Non-leaf-level pages do not receive page compression.</span></span>  
  
-   <span data-ttu-id="57346-158">大きな値のデータ型は、そのサイズが原因で、通常の行データとは別に特殊な目的のページに格納される場合があります。</span><span class="sxs-lookup"><span data-stu-id="57346-158">Because of their size, large-value data types are sometimes stored separately from the normal row data on special purpose pages.</span></span> <span data-ttu-id="57346-159">データ圧縮は、別個に格納されているデータには使用できません。</span><span class="sxs-lookup"><span data-stu-id="57346-159">Data compression is not available for the data that is stored separately.</span></span>  
  
-   <span data-ttu-id="57346-160">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で vardecimal ストレージ形式を実装したテーブルは、アップグレード時にもその設定を保持します。</span><span class="sxs-lookup"><span data-stu-id="57346-160">Tables which implemented the vardecimal storage format in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] will retain that setting when upgraded.</span></span> <span data-ttu-id="57346-161">vardecimal ストレージ形式を使用するテーブルに行の圧縮を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="57346-161">You can apply row compression to a table that has the vardecimal storage format.</span></span> <span data-ttu-id="57346-162">ただし、行の圧縮は vardecimal ストレージ形式のスーパーセットなので、vardecimal ストレージ形式を保持する理由はありません。</span><span class="sxs-lookup"><span data-stu-id="57346-162">However, because row compression is a superset of the vardecimal storage format, there is no reason to retain the vardecimal storage format.</span></span> <span data-ttu-id="57346-163">vardecimal ストレージ形式と行の圧縮を組み合わせても、10 進値の圧縮は追加されません。</span><span class="sxs-lookup"><span data-stu-id="57346-163">Decimal values gain no additional compression when you combine the vardecimal storage format with row compression.</span></span> <span data-ttu-id="57346-164">vardecimal ストレージ形式を使用するテーブルにページの圧縮を適用することができます。ただし、vardecimal ストレージ形式の列の圧縮が追加される可能性は低くなります。</span><span class="sxs-lookup"><span data-stu-id="57346-164">You can apply page compression to a table that has the vardecimal storage format; however, the vardecimal storage format columns probably will not achieve additional compression.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="57346-165">は vardecimal ストレージ形式をサポートしていますが、行レベルの圧縮で同じ目的が果たされるので、vardecimal ストレージ形式は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="57346-165">supports the vardecimal storage format; however, because row-level compression achieves the same goals, the vardecimal storage format is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="using-columnstore-and-columnstore-archive-compression"></a><span data-ttu-id="57346-166">列ストアおよび列ストアの保存用圧縮の使用</span><span class="sxs-lookup"><span data-stu-id="57346-166">Using Columnstore and Columnstore Archive Compression</span></span>  
  
||  
|-|  
|<span data-ttu-id="57346-167">**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](https://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。</span><span class="sxs-lookup"><span data-stu-id="57346-167">**Applies to**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] through [current version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).</span></span>|  
  
### <a name="basics"></a><span data-ttu-id="57346-168">基本</span><span class="sxs-lookup"><span data-stu-id="57346-168">Basics</span></span>  
 <span data-ttu-id="57346-169">列ストア テーブルおよび列ストア インデックスは常に列ストア圧縮を使用して格納されます。</span><span class="sxs-lookup"><span data-stu-id="57346-169">Columnstore tables and indexes are always stored with columnstore compression.</span></span> <span data-ttu-id="57346-170">保存用圧縮と呼ばれる追加の圧縮機能を構成するによって、列ストアのデータ サイズをさらに小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="57346-170">You can further reduce the size of columnstore data by configuring an additional compression called archival compression.</span></span>  <span data-ttu-id="57346-171">保存用圧縮を使用するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でデータに対して Microsoft Xpress 圧縮アルゴリズムを実行します。</span><span class="sxs-lookup"><span data-stu-id="57346-171">To perform archival compression, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs the Microsoft XPRESS compression algorithm on the data.</span></span> <span data-ttu-id="57346-172">次の種類のデータ圧縮を使用して、保存用圧縮を追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="57346-172">Add or remove archival compression by using the following data compression types:</span></span>  
  
-   <span data-ttu-id="57346-173">保存用圧縮で列ストア データを圧縮するには、`COLUMNSTORE_ARCHIVE` データ圧縮を使用します。</span><span class="sxs-lookup"><span data-stu-id="57346-173">Use `COLUMNSTORE_ARCHIVE` data compression to compress columnstore data with archival compression.</span></span>  
  
-   <span data-ttu-id="57346-174">保存用圧縮を解凍するには、 **COLUMNSTORE** データ圧縮を使用します。</span><span class="sxs-lookup"><span data-stu-id="57346-174">Use **COLUMNSTORE** data compression to decompress archival compression.</span></span> <span data-ttu-id="57346-175">この結果として生成されるデータは、引き続き列データの圧縮を使用して圧縮できます。</span><span class="sxs-lookup"><span data-stu-id="57346-175">This resulting data will continue to be compressed with columnstore compression.</span></span>  
  
 <span data-ttu-id="57346-176">保存用圧縮を追加するには、REBUILD オプションと DATA COMPRESSION = COLUMNSTORE を指定して [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) または [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="57346-176">To add archival compression, use [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with the REBUILD option and DATA COMPRESSION = COLUMNSTORE.</span></span>  
  
 <span data-ttu-id="57346-177">例 :</span><span class="sxs-lookup"><span data-stu-id="57346-177">Examples:</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE ON PARTITIONS (2,4)) ;  
  
```  
  
 <span data-ttu-id="57346-178">保存用圧縮を削除して、データを列ストア圧縮に復元するには、REBUILD オプションと DATA COMPRESSION = COLUMNSTORE を指定して [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) または [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="57346-178">To remove archival compression and restore the data to columnstore compression, use [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with the REBUILD option and DATA COMPRESSION = COLUMNSTORE.</span></span>  
  
 <span data-ttu-id="57346-179">例 :</span><span class="sxs-lookup"><span data-stu-id="57346-179">Examples:</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE ON PARTITIONS (2,4) ) ;  
  
```  
  
 <span data-ttu-id="57346-180">次の例では、データ圧縮をあるパーティションの列ストアに設定し、列ストアの圧縮を別のパーティションに設定しています。</span><span class="sxs-lookup"><span data-stu-id="57346-180">This next example sets the data compression to columnstore on some partitions, and to columnstore archival on other partitions.</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (  
    DATA_COMPRESSION =  COLUMNSTORE ON PARTITIONS (4,5),  
    DATA COMPRESSION = COLUMNSTORE_ARCHIVE ON PARTITIONS (1,2,3)  
) ;  
```  
  
### <a name="performance"></a><span data-ttu-id="57346-181">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="57346-181">Performance</span></span>  
 <span data-ttu-id="57346-182">保存用圧縮を使用して列ストア インデックスを圧縮すると、列ストア インデックスに保存用圧縮がない場合に比べて実行速度が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="57346-182">Compressing columnstore indexes with archival compression will cause the index to perform slower than columnstore indexes that do not have the archival compression.</span></span>  <span data-ttu-id="57346-183">保存用圧縮は、データを圧縮および取得する時間と CPU リソースに余裕がある場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="57346-183">Use archival compression only when you can afford to use extra time and CPU resources to compress and retrieve the data.</span></span>  
  
 <span data-ttu-id="57346-184">パフォーマンスは低下しますがストレージが少なくてすむため、頻繁にアクセスしないデータには便利です。</span><span class="sxs-lookup"><span data-stu-id="57346-184">The benefit of slower performance is reduced storage which is useful for data that is not frequently accessed.</span></span> <span data-ttu-id="57346-185">たとえば、各月のデータ用のパーティションがある場合、ほとんどアクティビティは最新の月のデータに対して実行されるため、古い月のデータをアーカイブして必要なストレージを削減できます。</span><span class="sxs-lookup"><span data-stu-id="57346-185">For example, if you have a partition for each month of data, and most of your activity is for the most recent months, you could archive older months to reduce the storage requirements.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="57346-186">Metadata</span><span class="sxs-lookup"><span data-stu-id="57346-186">Metadata</span></span>  
 <span data-ttu-id="57346-187">次のシステム ビューには、クラスター化インデックスのデータ圧縮に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="57346-187">The following system views contain information about data compression for clustered indexes:</span></span>  
  
-   <span data-ttu-id="57346-188">[&#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) -列と列には、 `type` `type_desc` クラスター化列ストアと非クラスター化列ストアが含まれます。</span><span class="sxs-lookup"><span data-stu-id="57346-188">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) - The `type` and `type_desc` columns include CLUSTERED COLUMNSTORE and NONCLUSTERED COLUMNSTORE.</span></span>  
  
-   <span data-ttu-id="57346-189">[ [transact-sql&#41;のパーティション &#40;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) ]-列と列には、列 `data_compression` `data_compression_desc` ストアと COLUMNSTORE_ARCHIVE が含まれます。</span><span class="sxs-lookup"><span data-stu-id="57346-189">[sys.partitions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) - The `data_compression` and `data_compression_desc` columns include COLUMNSTORE and COLUMNSTORE_ARCHIVE.</span></span>  
  
 <span data-ttu-id="57346-190">プロシージャ [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) は、列ストア インデックスに適用されません。</span><span class="sxs-lookup"><span data-stu-id="57346-190">The procedure [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) does not apply to columnstore indexes.</span></span>  
  
## <a name="how-compression-affects-partitioned-tables-and-indexes"></a><span data-ttu-id="57346-191">パーティション テーブルとパーティション インデックスへの圧縮の影響</span><span class="sxs-lookup"><span data-stu-id="57346-191">How Compression Affects Partitioned Tables and Indexes</span></span>  
 <span data-ttu-id="57346-192">パーティション テーブルとパーティション インデックスでデータ圧縮を使用する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="57346-192">When you use data compression with partitioned tables and indexes, be aware of the following considerations:</span></span>  
  
-   <span data-ttu-id="57346-193">ALTER PARTITION ステートメントを使用してパーティションを分割すると、両方のパーティションに元のパーティションのデータ圧縮属性が継承されます。</span><span class="sxs-lookup"><span data-stu-id="57346-193">When partitions are split by using the ALTER PARTITION statement, both partitions inherit the data compression attribute of the original partition.</span></span>  
  
-   <span data-ttu-id="57346-194">2 つのパーティションをマージすると、結果として得られるパーティションにマージ先パーティションのデータ圧縮属性が継承されます。</span><span class="sxs-lookup"><span data-stu-id="57346-194">When two partitions are merged, the resultant partition inherits the data compression attribute of the destination partition.</span></span>  
  
-   <span data-ttu-id="57346-195">パーティションを切り替えるには、パーティションのデータ圧縮プロパティがテーブルの圧縮プロパティと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57346-195">To switch a partition, the data compression property of the partition must match the compression property of the table.</span></span>  
  
-   <span data-ttu-id="57346-196">パーティション テーブルまたはパーティション インデックスの圧縮の変更に使用できる構文には、次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="57346-196">There are two syntax variations that you can use to modify the compression of a partitioned table or index:</span></span>  
  
    -   <span data-ttu-id="57346-197">次の構文では、参照されているパーティションのみが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="57346-197">The following syntax rebuilds only the referenced partition:</span></span>  
  
        ```  
        ALTER TABLE <table_name>   
        REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  <option>)  
        ```  
  
    -   <span data-ttu-id="57346-198">次の構文では、参照されていないパーティションの既存の圧縮設定を使用して、テーブル全体が再構築されます。</span><span class="sxs-lookup"><span data-stu-id="57346-198">The following syntax rebuilds the whole table by using the existing compression setting for any partitions that are not referenced:</span></span>  
  
        ```  
        ALTER TABLE <table_name>   
        REBUILD PARTITION = ALL   
        WITH (DATA_COMPRESSION = PAGE ON PARTITIONS(<range>),  
        ... )  
        ```  
  
     <span data-ttu-id="57346-199">パーティション インデックスの場合は、ALTER INDEX を使用して同じ原則に従います。</span><span class="sxs-lookup"><span data-stu-id="57346-199">Partitioned indexes follow the same principle using ALTER INDEX.</span></span>  
  
-   <span data-ttu-id="57346-200">クラスター化インデックスを削除する場合、パーティション構成を変更しない限り、対応するヒープ パーティションでデータ圧縮設定が維持されます。</span><span class="sxs-lookup"><span data-stu-id="57346-200">When a clustered index is dropped, the corresponding heap partitions retain their data compression setting unless the partitioning scheme is modified.</span></span> <span data-ttu-id="57346-201">パーティション構成を変更すると、すべてのパーティションが圧縮されていない状態に再構築されます。</span><span class="sxs-lookup"><span data-stu-id="57346-201">If the partitioning scheme is changed, all partitions are rebuilt to an uncompressed state.</span></span> <span data-ttu-id="57346-202">クラスター化インデックスを削除し、パーティション構成を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="57346-202">To drop a clustered index and change the partitioning scheme requires the following steps:</span></span>  
  
     1. <span data-ttu-id="57346-203">クラスター化インデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="57346-203">Drop the clustered index.</span></span>  
  
     2. <span data-ttu-id="57346-204">圧縮オプションを指定する ALTER TABLE ...REBUILD ... オプションを使用して、テーブルを変更します。</span><span class="sxs-lookup"><span data-stu-id="57346-204">Modify the table by using the ALTER TABLE ... REBUILD ... option that specifies the compression option.</span></span>  
  
     <span data-ttu-id="57346-205">OFFLINE でクラスター化インデックスを削除すると、クラスター化インデックスの上位レベルだけが削除されます。そのため、操作はとても高速です。</span><span class="sxs-lookup"><span data-stu-id="57346-205">To drop a clustered index OFFLINE is a very fast operation, because only the upper levels of clustered indexes are removed.</span></span> <span data-ttu-id="57346-206">ONLINE でクラスター化インデックスを削除すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、ヒープが手順 1. で 1 回、手順 2. で 1 回の計 2 回再構築されます。</span><span class="sxs-lookup"><span data-stu-id="57346-206">When a clustered index is dropped ONLINE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must rebuild the heap two times, once for step 1 and once for step 2.</span></span>  
  
## <a name="how-compression-affects-replication"></a><span data-ttu-id="57346-207">レプリケーションへの圧縮の影響</span><span class="sxs-lookup"><span data-stu-id="57346-207">How Compression Affects Replication</span></span>  
 <span data-ttu-id="57346-208">レプリケーションでデータ圧縮を使用する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="57346-208">When you are using data compression with replication, be aware of the following considerations:</span></span>  
  
-   <span data-ttu-id="57346-209">スナップショット エージェントで最初のスキーマ スクリプトが生成されるときに、新しいスキーマでは、テーブルとインデックスの両方に同じ圧縮設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="57346-209">When the Snapshot Agent generates the initial schema script, the new schema will use the same compression settings for both the table and its indexes.</span></span> <span data-ttu-id="57346-210">圧縮をテーブルのみで有効にし、インデックスで無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="57346-210">Compression cannot be enabled on just the table and not the index.</span></span>  
  
-   <span data-ttu-id="57346-211">トランザクション レプリケーションの場合、アーティクル スキーマ オプションによって、スクリプトを作成する必要がある依存オブジェクトおよびプロパティが特定されます。</span><span class="sxs-lookup"><span data-stu-id="57346-211">For transactional replication the article schema option determines what dependent objects and properties have to be scripted.</span></span> <span data-ttu-id="57346-212">詳細については、「 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57346-212">For more information, see [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span>  
  
     <span data-ttu-id="57346-213">ディストリビューション エージェントでは、スクリプトの適用時に下位のサブスクライバーのチェックが行われません。</span><span class="sxs-lookup"><span data-stu-id="57346-213">The Distribution Agent does not check for down-level Subscribers when it applies scripts.</span></span> <span data-ttu-id="57346-214">圧縮のレプリケーションが選択されている場合、下位のサブスクライバーに対するテーブルの作成は失敗します。</span><span class="sxs-lookup"><span data-stu-id="57346-214">If the replication of compression is selected, creating the table on down-level Subscribers will fail.</span></span> <span data-ttu-id="57346-215">混合トポロジの場合は、圧縮のレプリケーションを有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="57346-215">In the case of a mixed topology, do not enable the replication of compression.</span></span>  
  
-   <span data-ttu-id="57346-216">マージ レプリケーションの場合、パブリケーションの互換性レベルがスキーマ オプションをオーバーライドし、この互換性レベルによってスクリプトが作成されるスキーマ オブジェクトが特定されます。</span><span class="sxs-lookup"><span data-stu-id="57346-216">For merge replication, publication compatibility level overrides the schema options and determines the schema objects that will be scripted.</span></span>  
  
     <span data-ttu-id="57346-217">混合トポロジの場合、新しい圧縮オプションをサポートする必要がないときは、パブリケーションの互換性レベルを下位のサブスクライバー バージョンに設定してください。</span><span class="sxs-lookup"><span data-stu-id="57346-217">In the case of a mixed topology, if it is not required to support the new compression options, the publication compatibility level should be set to the down-level Subscriber version.</span></span> <span data-ttu-id="57346-218">サポートする必要があるときは、テーブルをサブスクライバーに作成してから圧縮してください。</span><span class="sxs-lookup"><span data-stu-id="57346-218">If it is required, compress tables on the Subscriber after they have been created.</span></span>  
  
 <span data-ttu-id="57346-219">次の表に、レプリケーション時に圧縮を制御するレプリケーション設定を示します。</span><span class="sxs-lookup"><span data-stu-id="57346-219">The following table shows replication settings that control compression during replication.</span></span>  
  
|<span data-ttu-id="57346-220">ユーザーの目的</span><span class="sxs-lookup"><span data-stu-id="57346-220">User intent</span></span>|<span data-ttu-id="57346-221">テーブルまたはインデックスのパーティション構成のレプリケート</span><span class="sxs-lookup"><span data-stu-id="57346-221">Replicate partition scheme for a table or index</span></span>|<span data-ttu-id="57346-222">圧縮設定のレプリケート</span><span class="sxs-lookup"><span data-stu-id="57346-222">Replicate compression settings</span></span>|<span data-ttu-id="57346-223">スクリプト作成の動作</span><span class="sxs-lookup"><span data-stu-id="57346-223">Scripting behavior</span></span>|  
|-----------------|-----------------------------------------------------|------------------------------------|------------------------|  
|<span data-ttu-id="57346-224">パーティション構成をレプリケートしてパーティションのサブスクライバーで圧縮を有効にする。</span><span class="sxs-lookup"><span data-stu-id="57346-224">To replicate the partition scheme and enable compression on the Subscriber on the partition.</span></span>|<span data-ttu-id="57346-225">True</span><span class="sxs-lookup"><span data-stu-id="57346-225">True</span></span>|<span data-ttu-id="57346-226">True</span><span class="sxs-lookup"><span data-stu-id="57346-226">True</span></span>|<span data-ttu-id="57346-227">パーティション構成と圧縮設定の両方のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="57346-227">Scripts both the partition scheme and the compression settings.</span></span>|  
|<span data-ttu-id="57346-228">パーティション構成をレプリケートするがサブスクライバーでデータ圧縮は実行しない。</span><span class="sxs-lookup"><span data-stu-id="57346-228">To replicate the partition scheme but not compress the data on the Subscriber.</span></span>|<span data-ttu-id="57346-229">正しい</span><span class="sxs-lookup"><span data-stu-id="57346-229">True</span></span>|<span data-ttu-id="57346-230">False</span><span class="sxs-lookup"><span data-stu-id="57346-230">False</span></span>|<span data-ttu-id="57346-231">パーティション構成のスクリプトは作成しますが、パーティションの圧縮設定のスクリプトは作成しません。</span><span class="sxs-lookup"><span data-stu-id="57346-231">Scripts out the partition scheme but not the compression settings for the partition.</span></span>|  
|<span data-ttu-id="57346-232">パーティション構成をレプリケートせず、サブスクライバーでデータ圧縮も実行しない。</span><span class="sxs-lookup"><span data-stu-id="57346-232">To not replicate the partition scheme and not compress the data on the Subscriber.</span></span>|<span data-ttu-id="57346-233">False</span><span class="sxs-lookup"><span data-stu-id="57346-233">False</span></span>|<span data-ttu-id="57346-234">False</span><span class="sxs-lookup"><span data-stu-id="57346-234">False</span></span>|<span data-ttu-id="57346-235">パーティションと圧縮設定のスクリプトを作成しません。</span><span class="sxs-lookup"><span data-stu-id="57346-235">Does not script partition or compression settings.</span></span>|  
|<span data-ttu-id="57346-236">パブリッシャーですべてのパーティションが圧縮される場合はサブスクライバーでテーブルを圧縮するが、パーティション構成はレプリケートしない。</span><span class="sxs-lookup"><span data-stu-id="57346-236">To compress the table on the Subscriber if all the partitions are compressed on the Publisher, but not replicate the partition scheme.</span></span>|<span data-ttu-id="57346-237">False</span><span class="sxs-lookup"><span data-stu-id="57346-237">False</span></span>|<span data-ttu-id="57346-238">True</span><span class="sxs-lookup"><span data-stu-id="57346-238">True</span></span>|<span data-ttu-id="57346-239">すべてのパーティションで圧縮が有効になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57346-239">Checks if all the partitions are enabled for compression.</span></span><br /><br /> <span data-ttu-id="57346-240">テーブル レベルで圧縮のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="57346-240">Scripts out compression at the table level.</span></span>|  
  
## <a name="how-compression-affects-other-sql-server-components"></a><span data-ttu-id="57346-241">他の SQL Server コンポーネントへの圧縮の影響</span><span class="sxs-lookup"><span data-stu-id="57346-241">How Compression Affects Other SQL Server Components</span></span>  
 <span data-ttu-id="57346-242">圧縮はストレージ エンジンで行われるので、他のほとんどの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントには、データは圧縮されていない状態で提供されます。</span><span class="sxs-lookup"><span data-stu-id="57346-242">Compression occurs in the storage engine and the data is presented to most of the other components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in an uncompressed state.</span></span> <span data-ttu-id="57346-243">このため、他のコンポーネントに対する圧縮の影響は、次のように制限されます。</span><span class="sxs-lookup"><span data-stu-id="57346-243">This limits the effects of compression on the other components to the following:</span></span>  
  
-   <span data-ttu-id="57346-244">一括インポート操作と一括エクスポート操作</span><span class="sxs-lookup"><span data-stu-id="57346-244">Bulk import and export operations</span></span>  
  
     <span data-ttu-id="57346-245">データをエクスポートする場合、データはネイティブ形式であっても圧縮されていない行形式で出力されます。</span><span class="sxs-lookup"><span data-stu-id="57346-245">When data is exported, even in native format, the data is output in the uncompressed row format.</span></span> <span data-ttu-id="57346-246">この結果、エクスポートされたデータ ファイルのサイズがソース データより大幅に大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57346-246">This can cause the size of exported data file to be significantly larger than the source data.</span></span>  
  
     <span data-ttu-id="57346-247">データをインポートする場合、インポート先のテーブルで圧縮が有効になっているときは、データはストレージ エンジンによって圧縮された行形式に変換されます。</span><span class="sxs-lookup"><span data-stu-id="57346-247">When data is imported, if the target table has been enabled for compression, the data is converted by the storage engine into compressed row format.</span></span> <span data-ttu-id="57346-248">この結果、圧縮されていないテーブルにデータをインポートする場合と比較して、CPU 使用率が上昇する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57346-248">This can cause increased CPU usage compared to when data is imported into an uncompressed table.</span></span>  
  
     <span data-ttu-id="57346-249">ページの圧縮を使用するヒープにデータを一括インポートする場合、一括インポート操作では、データの挿入時にページの圧縮を使用したデータ圧縮が試行されます。</span><span class="sxs-lookup"><span data-stu-id="57346-249">When data is bulk imported into a heap with page compression, the bulk import operation will try to compress the data with page compression when the data is inserted.</span></span>  
  
-   <span data-ttu-id="57346-250">圧縮はバックアップと復元には影響しません。</span><span class="sxs-lookup"><span data-stu-id="57346-250">Compression does not affect backup and restore.</span></span>  
  
-   <span data-ttu-id="57346-251">圧縮はログ配布には影響しません。</span><span class="sxs-lookup"><span data-stu-id="57346-251">Compression does not affect log shipping.</span></span>  
  
-   <span data-ttu-id="57346-252">データ圧縮は、スパース列と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="57346-252">Data compression is incompatible with sparse columns.</span></span> <span data-ttu-id="57346-253">したがって、スパース列を含むテーブルを圧縮したり、スパース列を圧縮されたテーブルに追加したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="57346-253">Therefore, tables containing sparse columns cannot be compressed nor can sparse columns be added to a compressed table.</span></span>  
  
-   <span data-ttu-id="57346-254">圧縮を有効にすると、クエリ プランが変更される可能性があります。データの格納に使用されるページ数とページあたりの行数が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="57346-254">Enabling compression can cause query plans to change because the data is stored using a different number of pages and number of rows per page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57346-255">参照</span><span class="sxs-lookup"><span data-stu-id="57346-255">See Also</span></span>  
 <span data-ttu-id="57346-256">[行の圧縮の実装](row-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="57346-256">[Row Compression Implementation](row-compression-implementation.md) </span></span>  
 <span data-ttu-id="57346-257">[ページの圧縮の実装](page-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="57346-257">[Page Compression Implementation](page-compression-implementation.md) </span></span>  
 <span data-ttu-id="57346-258">[Unicode 圧縮の実装](unicode-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="57346-258">[Unicode Compression Implementation](unicode-compression-implementation.md) </span></span>  
 <span data-ttu-id="57346-259">[CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57346-259">[CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql) </span></span>  
 <span data-ttu-id="57346-260">[CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57346-260">[CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-function-transact-sql) </span></span>  
 <span data-ttu-id="57346-261">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57346-261">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="57346-262">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57346-262">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="57346-263">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57346-263">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="57346-264">ALTER INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="57346-264">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
  
