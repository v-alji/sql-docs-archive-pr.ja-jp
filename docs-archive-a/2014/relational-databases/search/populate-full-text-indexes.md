---
title: フルテキスト インデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- index populations [full-text search]
- incremental populations [full-text search]
- populations [full-text search]
- full-text search [SQL Server], populations
- crawls [full-text search]
- automatic full-text index updates
- change tracking-based populations [full-text search]
- manual updates [full-text search]
- manual populations [full-text search]
- auto populations [full-text search]
- full-text indexes [SQL Server], key column
- full populations [full-text search]
- full-text indexes [SQL Server], populations
ms.assetid: 76767b20-ef55-49ce-8dc4-e77cb8ff618a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9ab93a3514fa260c8c3836da85c767da3c3051a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643750"
---
# <a name="populate-full-text-indexes"></a><span data-ttu-id="b34f9-102">フルテキスト インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="b34f9-102">Populate Full-Text Indexes</span></span>
  <span data-ttu-id="b34f9-103">フルテキスト インデックスの作成と保持では、 *作成* (または *クロール*) と呼ばれるプロセスを使用してインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-103">Creating and maintaining a full-text index involves populating the index by using a process called a *population* (also known as a *crawl*).</span></span>  
  
##  <a name="types-of-population"></a><a name="types"></a><span data-ttu-id="b34f9-104">作成の種類</span><span class="sxs-lookup"><span data-stu-id="b34f9-104">Types of Population</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b34f9-105">では、完全作成、変更の追跡に基づく自動または手動の作成、およびタイムスタンプに基づく増分作成の種類がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b34f9-105">supports the following types of population: full population, change tracking-based automatic or manual population, and incremental timestamp-based population.</span></span>  
  
### <a name="full-population"></a><span data-ttu-id="b34f9-106">すべてのカタログの作成</span><span class="sxs-lookup"><span data-stu-id="b34f9-106">Full Population</span></span>  
 <span data-ttu-id="b34f9-107">すべてのカタログの作成では、テーブルまたはインデックス付きビューのすべての行に対してインデックス エントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-107">During a full population, index entries are built for all the rows of a table or indexed view.</span></span> <span data-ttu-id="b34f9-108">フルテキスト インデックスのすべてのカタログの作成では、ベース テーブルまたはインデックス付きビューのすべての行に対してインデックス エントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-108">A full population of a full-text index, builds index entries for all the rows of the base table or indexed view.</span></span>  
  
 <span data-ttu-id="b34f9-109">既定では、新しいフルテキスト インデックスが作成されると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってすぐにそのカタログが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] populates a new full-text index fully as soon as it is created.</span></span> <span data-ttu-id="b34f9-110">ただし、すべてのカタログの作成では大量のリソースが消費される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b34f9-110">However, a full population can consume a significant amount of resources.</span></span> <span data-ttu-id="b34f9-111">このため、ピーク期間にフルテキスト インデックスを作成する場合は、すべてのカタログの作成をオフピーク時間まで遅らせることが推奨されています (特にフルテキスト インデックスのベース テーブルが大きい場合)。</span><span class="sxs-lookup"><span data-stu-id="b34f9-111">Therefore, when creating a full-text index during peak periods, it is often a best practice to delay the full population until an off-peak time, particularly if the base table of an full-text index is large.</span></span> <span data-ttu-id="b34f9-112">ただし、インデックスが属するフルテキスト カタログは、そのすべてのフルテキスト インデックスのカタログが作成されるまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="b34f9-112">However, the full-text catalog to which the index belongs is not usable until all of its full-text indexes are populated.</span></span> <span data-ttu-id="b34f9-113">フルテキスト インデックスを作成する際に直ちにカタログを作成しない場合は、CREATE FULLTEXT INDEX ステートメントで CHANGE_TRACKING OFF および NO POPULATION 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-113">To create a full-text index without populating it immediately, specify the CHANGE_TRACKING OFF, NO POPULATION clause in the CREATE FULLTEXT INDEX statement.</span></span> <span data-ttu-id="b34f9-114">CHANGE_TRACKING MANUAL を指定すると、Full-Text Engine はステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-114">If you specify CHANGE_TRACKING MANUAL, the Full-Text Engine uses statement.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b34f9-115">では、[完全作成の開始] または [増分作成の開始] 句を使用して ALTER フルテキストインデックスステートメントを実行するまで、新しいフルテキストインデックスは設定されません。</span><span class="sxs-lookup"><span data-stu-id="b34f9-115">will not populate the new full-text index until you execute an ALTER FULLTEXT INDEX statement using the START FULL POPULATION or START INCREMENTAL POPULATION clause.</span></span> <span data-ttu-id="b34f9-116">詳細については、このトピックの後半の例「A.</span><span class="sxs-lookup"><span data-stu-id="b34f9-116">For more information, see examples "A.</span></span> <span data-ttu-id="b34f9-117">完全作成を実行せずにフルテキスト インデックスを作成する」および「B.</span><span class="sxs-lookup"><span data-stu-id="b34f9-117">Creating a full-text index without running a full population" and "B.</span></span> <span data-ttu-id="b34f9-118">テーブルで完全作成を実行する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b34f9-118">Running a full population on table," later in this topic.</span></span>  
  

  
### <a name="change-tracking-based-population"></a><span data-ttu-id="b34f9-119">変更の追跡に基づくカタログ作成</span><span class="sxs-lookup"><span data-stu-id="b34f9-119">Change Tracking-Based Population</span></span>  
 <span data-ttu-id="b34f9-120">必要に応じて、変更の追跡を使用して、完全作成が最初に実行された後のフルテキスト インデックスを保持することができます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-120">Optionally, you can use change tracking to maintain a full-text index after its initial full population.</span></span> <span data-ttu-id="b34f9-121">変更の追跡には若干のオーバーヘッドが伴います。これは、前回のカタログ作成以降にベース テーブルに対して行われた変更を追跡するテーブルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で保持されるためです。</span><span class="sxs-lookup"><span data-stu-id="b34f9-121">There is a small overhead associated with change tracking because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintains a table in which it tracks changes to the base table since the last population.</span></span> <span data-ttu-id="b34f9-122">変更の追跡を使用すると、ベース テーブルまたはインデックス付きビューで更新、削除、または挿入によって変更された行の記録が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で保持されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-122">When change tracking is used, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintains a record of the rows in the base table or indexed view that have been modified by updates, deletes, or inserts.</span></span> <span data-ttu-id="b34f9-123">WRITETEXT および UPDATETEXT によるデータの変更は、フルテキスト インデックスには反映されず、変更の監視でも取得されません。</span><span class="sxs-lookup"><span data-stu-id="b34f9-123">Data changes through WRITETEXT and UPDATETEXT are not reflected in the full-text index, and are not picked up with change tracking.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b34f9-124">`timestamp` 列を含んでいるテーブルには、増分作成を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-124">For tables containing a `timestamp` column, you can use incremental populations.</span></span>  
  
 <span data-ttu-id="b34f9-125">インデックス作成時に変更の追跡を有効にすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で新しいフルテキスト インデックスが作成された直後にそのインデックスですべてのカタログの作成が実行されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-125">When change tracking is enabled during index creation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fully populates the new full-text index immediately after it is created.</span></span> <span data-ttu-id="b34f9-126">それ以降は、変更が追跡されてフルテキスト インデックスに反映されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-126">Thereafter, changes are tracked and propagated to the full-text index.</span></span> <span data-ttu-id="b34f9-127">変更の追跡には、自動 (CHANGE_TRACKING AUTO オプション) と手動 (CHANGE_TRACKING MANUAL オプション) の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="b34f9-127">There are two types of change tracking, automatic (CHANGE_TRACKING AUTO option) and manual (CHANGE_TRACKING MANUAL option).</span></span> <span data-ttu-id="b34f9-128">既定では自動で変更が追跡されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-128">Automatic change tracking is the default behavior.</span></span>  
  
 <span data-ttu-id="b34f9-129">変更の追跡の種類によって、フルテキスト インデックスのカタログ作成方法が次のように決まります。</span><span class="sxs-lookup"><span data-stu-id="b34f9-129">The type of change tracking determines how the full-text index is populated, as follows:</span></span>  
  
-   <span data-ttu-id="b34f9-130">自動でのカタログ作成</span><span class="sxs-lookup"><span data-stu-id="b34f9-130">Automatic population</span></span>  
  
     <span data-ttu-id="b34f9-131">既定では、または CHANGE_TRACKING AUTO を指定すると、Full-Text Engine によってフルテキスト インデックスに自動的にカタログが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-131">By default, or if you specify CHANGE_TRACKING AUTO, the Full-Text Engine uses automatic population on the full-text index.</span></span> <span data-ttu-id="b34f9-132">すべてのカタログの作成が最初に実行された後に、ベース テーブルでデータが変更されると変更が追跡され、追跡された変更が自動的に反映されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-132">After the initial full population completes, changes are tracked as data is modified in the base table, and the tracked changes are propagated automatically.</span></span> <span data-ttu-id="b34f9-133">ただし、フルテキスト インデックスはバックグラウンドで更新されるため、変更が直ちにインデックスに反映されないこともあります。</span><span class="sxs-lookup"><span data-stu-id="b34f9-133">The full-text index is updated in the background, however, so propagated changes might not be reflected immediately in the index.</span></span>  
  
     <span data-ttu-id="b34f9-134">**自動でのカタログ作成を指定して変更の追跡を設定するには**</span><span class="sxs-lookup"><span data-stu-id="b34f9-134">**To set up tracking changes with automatic population**</span></span>  
  
    -   <span data-ttu-id="b34f9-135">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="b34f9-135">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING AUTO</span></span>  
  
    -   <span data-ttu-id="b34f9-136">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="b34f9-136">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING AUTO</span></span>  
  
     <span data-ttu-id="b34f9-137">詳細については、このトピックの後半の例「E.</span><span class="sxs-lookup"><span data-stu-id="b34f9-137">For more information, see example "E.</span></span> <span data-ttu-id="b34f9-138">自動で変更が追跡されるようにフルテキスト インデックスを変更する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b34f9-138">Altering a full-text index to use automatic change tracking," later in this topic.</span></span>  
  
-   <span data-ttu-id="b34f9-139">手動でのカタログ作成</span><span class="sxs-lookup"><span data-stu-id="b34f9-139">Manual population</span></span>  
  
     <span data-ttu-id="b34f9-140">CHANGE_TRACKING MANUAL を指定すると、Full-Text Engine ではフルテキスト インデックスに対して手動作成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-140">If you specify CHANGE_TRACKING MANUAL, the Full-Text Engine uses manual population on the full-text index.</span></span> <span data-ttu-id="b34f9-141">完全作成が最初に実行された後に、ベース テーブルでデータが変更されると変更が追跡されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-141">After the initial full population completes, changes are tracked as data is modified in the base table.</span></span> <span data-ttu-id="b34f9-142">ただしその変更は、ALTER FULLTEXT INDEX ...START UPDATE POPULATION ステートメントを実行するまで反映されません。</span><span class="sxs-lookup"><span data-stu-id="b34f9-142">However, they are not propagated to the full-text index until you execute an ALTER FULLTEXT INDEX ... START UPDATE POPULATION statement.</span></span> <span data-ttu-id="b34f9-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用すると、この [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを定期的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-143">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to call this [!INCLUDE[tsql](../../includes/tsql-md.md)] statement periodically.</span></span>  
  
     <span data-ttu-id="b34f9-144">**手動でのカタログ作成を指定して変更の追跡を開始するには**</span><span class="sxs-lookup"><span data-stu-id="b34f9-144">**To start tracking changes with manual population**</span></span>  
  
    -   <span data-ttu-id="b34f9-145">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING MANUAL</span><span class="sxs-lookup"><span data-stu-id="b34f9-145">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING MANUAL</span></span>  
  
    -   <span data-ttu-id="b34f9-146">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING MANUAL</span><span class="sxs-lookup"><span data-stu-id="b34f9-146">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING MANUAL</span></span>  
  
     <span data-ttu-id="b34f9-147">詳細については、このトピックの後半の例「C.</span><span class="sxs-lookup"><span data-stu-id="b34f9-147">For more information, see examples "C.</span></span> <span data-ttu-id="b34f9-148">手動で変更を追跡するようにフルテキスト インデックスを作成する」および「D.</span><span class="sxs-lookup"><span data-stu-id="b34f9-148">Creating a full-text index with manual change tracking" and "D.</span></span> <span data-ttu-id="b34f9-149">手動でのカタログ作成を実行する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b34f9-149">Running a manual population," later in this topic.</span></span>  
  
 <span data-ttu-id="b34f9-150">**変更の追跡を無効にするには**</span><span class="sxs-lookup"><span data-stu-id="b34f9-150">**To turn off change tracking**</span></span>  
  
-   <span data-ttu-id="b34f9-151">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="b34f9-151">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING OFF</span></span>  
  
-   <span data-ttu-id="b34f9-152">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="b34f9-152">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING OFF</span></span>  
  

  
### <a name="incremental-timestamp-based-population"></a><span data-ttu-id="b34f9-153">タイムスタンプに基づく増分作成</span><span class="sxs-lookup"><span data-stu-id="b34f9-153">Incremental Timestamp-Based Population</span></span>  
 <span data-ttu-id="b34f9-154">増分作成は、フルテキスト インデックスに手動でカタログを作成するためのもう 1 つのメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="b34f9-154">An incremental population is an alternative mechanism for manually populating a full-text index.</span></span> <span data-ttu-id="b34f9-155">増分作成は、CHANGE_TRACKING が MANUAL または OFF に設定されているフルテキスト インデックスに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-155">You can run an incremental population for a full-text index that has CHANGE_TRACKING set to MANUAL or OFF.</span></span> <span data-ttu-id="b34f9-156">フルテキスト インデックスの最初のカタログ作成が増分作成の場合、すべての行にインデックスが付けられるため、完全作成と同じになります。</span><span class="sxs-lookup"><span data-stu-id="b34f9-156">If the first population on a full-text index is an incremental population, it indexes all rows, making it equivalent to a full population.</span></span>  
  
 <span data-ttu-id="b34f9-157">増分作成では、インデックスが設定されたテーブルに `timestamp` データ型の列が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b34f9-157">The requirement for incremental population is that the indexed table must have a column of the `timestamp` data type.</span></span> <span data-ttu-id="b34f9-158">`timestamp` 型の列が存在しない場合には、増分作成を実行できません。</span><span class="sxs-lookup"><span data-stu-id="b34f9-158">If a `timestamp` column does not exist, incremental population cannot be performed.</span></span> <span data-ttu-id="b34f9-159">`timestamp` 型の列を含んでいないテーブルで増分作成を要求すると、完全作成が実行されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-159">A request for incremental population on a table without a `timestamp` column results in a full population operation.</span></span> <span data-ttu-id="b34f9-160">また、前回のカタログ作成後にテーブルのフルテキスト インデックスに影響するようなメタデータの変更があった場合、増分作成の要求はすべてのカタログの作成として実行されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-160">Also, if any metadata that affects the full-text index for the table has changed since the last population, incremental population requests are implemented as full populations.</span></span> <span data-ttu-id="b34f9-161">これには、列、インデックス、またはフルテキスト インデックスの定義を変更したことによるメタデータの変更が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-161">This includes metadata changes caused by altering any column, index, or full-text index definitions.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b34f9-162">では、`timestamp` 列を使用して前回の作成後に変更された行が識別されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-162">uses the `timestamp` column to identify rows that have changed since the last population.</span></span> <span data-ttu-id="b34f9-163">増分作成では、前回のカタログ作成後、または作成中に追加、削除、または変更された行のフルテキスト インデックスが更新されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-163">The incremental population then updates the full-text index for rows added, deleted, or modified after the last population, or while the last population was in progress.</span></span> <span data-ttu-id="b34f9-164">テーブルで大量の挿入が行われた場合は、手動でのカタログ作成よりも増分作成を使用した方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="b34f9-164">If a table experiences a high volume of inserts, using incremental population can be more efficient that using manual population.</span></span>  
  
 <span data-ttu-id="b34f9-165">作成が終わると、Full-Text Engine は新しい `timestamp` 型の値を記録します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-165">At the end of a population, the Full-Text Engine records a new `timestamp` value.</span></span> <span data-ttu-id="b34f9-166">この値は、SQL Gatherer が検出した `timestamp` 型の最大値です。</span><span class="sxs-lookup"><span data-stu-id="b34f9-166">This value is the largest `timestamp` value that SQL Gatherer has encountered.</span></span> <span data-ttu-id="b34f9-167">今後、増分作成を開始するときには、この値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-167">This value will be used when a subsequent incremental population starts.</span></span>  
  
 <span data-ttu-id="b34f9-168">増分作成を実行するには、START INCREMENTAL POPULATION 句を指定して ALTER FULLTEXT INDEX ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-168">To run an incremental population, execute an ALTER FULLTEXT INDEX statement using the START INCREMENTAL POPULATION clause.</span></span>  
  

  
##  <a name="examples-of-populating-full-text-indexes"></a><a name="examples"></a><span data-ttu-id="b34f9-169">フルテキストインデックスの作成の例</span><span class="sxs-lookup"><span data-stu-id="b34f9-169">Examples of Populating Full-Text Indexes</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b34f9-170">このセクションの例では、 `Production.Document` サンプル データベースの `HumanResources.JobCandidate` テーブルまたは `AdventureWorks` テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-170">The examples in this section use the `Production.Document` or `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
### <a name="a-creating-a-full-text-index-without-running-a-full-population"></a><span data-ttu-id="b34f9-171">A.</span><span class="sxs-lookup"><span data-stu-id="b34f9-171">A.</span></span> <span data-ttu-id="b34f9-172">完全作成を実行せずにフルテキスト インデックスを作成する</span><span class="sxs-lookup"><span data-stu-id="b34f9-172">Creating a full-text index without running a full population</span></span>  
 <span data-ttu-id="b34f9-173">次の例では、 `Production.Document` サンプル データベースの `AdventureWorks` テーブルにフルテキスト インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-173">The following example creates a full-text index on the `Production.Document` table of the `AdventureWorks` sample database.</span></span> <span data-ttu-id="b34f9-174">この例では、WITH CHANGE_TRACKING OFF, NO POPULATION を使用して、最初の完全作成を遅らせます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-174">This example uses WITH CHANGE_TRACKING OFF, NO POPULATION to delay the initial full population.</span></span>  
  
```  
CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
CREATE FULLTEXT CATALOG AW_Production_FTCat;  
CREATE FULLTEXT INDEX ON Production.Document  
(  
    Document                         --Full-text index column name   
        TYPE COLUMN FileExtension    --Name of column that contains file type information  
        Language 1033                 --1033 is LCID for the English language  
)  
    KEY INDEX ui_ukDoc  
    ON AW_Production_FTCat  
    WITH CHANGE_TRACKING OFF, NO POPULATION;  
GO  
  
```  
  
### <a name="b-running-a-full-population-on-table"></a><span data-ttu-id="b34f9-175">B.</span><span class="sxs-lookup"><span data-stu-id="b34f9-175">B.</span></span> <span data-ttu-id="b34f9-176">テーブルで完全作成を実行する</span><span class="sxs-lookup"><span data-stu-id="b34f9-176">Running a full population on table</span></span>  
 <span data-ttu-id="b34f9-177">次の例では、 `Production.Document` サンプル データベースの `AdventureWorks` テーブルで完全作成を実行します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-177">The following example runs a full population on the `Production.Document` table of the `AdventureWorks` sample database.</span></span>  
  
```  
ALTER FULLTEXT INDEX ON Production.Document  
   START FULL POPULATION;  
```  
  
### <a name="c-creating-a-full-text-index-with-manual-change-tracking"></a><span data-ttu-id="b34f9-178">C.</span><span class="sxs-lookup"><span data-stu-id="b34f9-178">C.</span></span> <span data-ttu-id="b34f9-179">手動での変更の追跡によってフルテキスト インデックスを作成する</span><span class="sxs-lookup"><span data-stu-id="b34f9-179">Creating a full-text index with manual change tracking</span></span>  
 <span data-ttu-id="b34f9-180">次の例では、 `HumanResources.JobCandidate` サンプル データベースの `AdventureWorks` テーブルで、手動でのカタログ作成を指定した変更の追跡を使用するフルテキスト インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-180">The following example creates a full-text index that will use change tracking with manual population on the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE UNIQUE INDEX ui_ukJobCand ON HumanResources.JobCandidate(JobCandidateID);  
CREATE FULLTEXT CATALOG ft AS DEFAULT;  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume)   
   KEY INDEX ui_ukJobCand   
   WITH CHANGE_TRACKING=MANUAL;  
GO  
```  
  
### <a name="d-running-a-manual-population"></a><span data-ttu-id="b34f9-181">D.</span><span class="sxs-lookup"><span data-stu-id="b34f9-181">D.</span></span> <span data-ttu-id="b34f9-182">手動作成を実行する</span><span class="sxs-lookup"><span data-stu-id="b34f9-182">Running a manual population</span></span>  
 <span data-ttu-id="b34f9-183">次の例では、 `HumanResources.JobCandidate` サンプル データベースの `AdventureWorks` テーブルで、変更が追跡されるフルテキスト インデックスに対して手動でのカタログ作成を実行します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-183">The following example runs a manual population on the change-tracked full-text index of the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate START UPDATE POPULATION;  
GO  
```  
  
### <a name="e-altering-a-full-text-index-to-use-automatic-change-tracking"></a><span data-ttu-id="b34f9-184">E.</span><span class="sxs-lookup"><span data-stu-id="b34f9-184">E.</span></span> <span data-ttu-id="b34f9-185">自動の変更の追跡を使用するようにフルテキスト インデックスを変更する</span><span class="sxs-lookup"><span data-stu-id="b34f9-185">Altering a full-text index to use automatic change tracking</span></span>  
 <span data-ttu-id="b34f9-186">次の例では、 `HumanResources.JobCandidate` サンプル データベースの `AdventureWorks` テーブルで、自動作成に変更の追跡を使用するようにフルテキスト インデックスを変更します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-186">The following example changes the full-text index of the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database to use change tracking with automatic population.</span></span>  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate SET CHANGE_TRACKING AUTO;  
GO   
```  
  

  
##  <a name="creating-or-changing-a-schedule-for-incremental-population"></a><a name="create"></a><span data-ttu-id="b34f9-187">増分作成のスケジュールの作成または変更</span><span class="sxs-lookup"><span data-stu-id="b34f9-187">Creating or Changing a Schedule for Incremental Population</span></span>  
  
#### <a name="to-create-or-change-a-schedule-for-incremental-population-in-management-studio"></a><span data-ttu-id="b34f9-188">Management Studio で増分作成のスケジュールを作成または変更するには</span><span class="sxs-lookup"><span data-stu-id="b34f9-188">To create or change a schedule for incremental population in Management Studio</span></span>  
  
1.  <span data-ttu-id="b34f9-189">オブジェクト エクスプローラーで、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-189">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="b34f9-190">**[データベース]** を展開し、フルテキスト インデックスを含むデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-190">Expand **Databases**, and then expand the database that contains the full-text index.</span></span>  
  
3.  <span data-ttu-id="b34f9-191">**[テーブル]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-191">Expand **Tables**.</span></span>  
  
 <span data-ttu-id="b34f9-192">フルテキスト インデックスが定義されているテーブルを右クリックし、 **[フルテキスト インデックス]** コンテキスト メニューの **[フルテキスト インデックス]** をクリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b34f9-192">Right-click the table on which the full-text index is defined, select **Full-Text index**, and on the **Full-Text index** context menu, click **Properties**.</span></span> <span data-ttu-id="b34f9-193">**[フルテキスト インデックスのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-193">This opens the **Full-text index Properties** dialog box.</span></span>  
  
1.  <span data-ttu-id="b34f9-194">[**ページの選択**] ペインで、[スケジュール] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-194">In the **Select a page** pane, select Schedules.</span></span>  
  
     <span data-ttu-id="b34f9-195">このページでは、フルテキスト インデックスのベース テーブルまたはインデックス付きビューの増分作成を開始する SQL Server エージェント ジョブのスケジュールを作成または管理できます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-195">Use this page to create or manage schedules for a SQL Server Agent job that starts an incremental table population on the base table or indexed view of the full-text index.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b34f9-196">ベース テーブルまたはビューに `timestamp` データ型の列が含まれていない場合は、完全作成が実行されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-196">If the base table or view does not contain a column of the `timestamp` data type, a full population is performed.</span></span>  
  
     <span data-ttu-id="b34f9-197">次のようなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="b34f9-197">The options are as follows:</span></span>  
  
    -   <span data-ttu-id="b34f9-198">新しいスケジュールを作成するには、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b34f9-198">To create a new schedule, click **New**.</span></span>  
  
         <span data-ttu-id="b34f9-199">スケジュールを作成できる **[新しいフルテキスト インデックス テーブルのスケジュール]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-199">This opens the **New Full-Text Indexing Table Schedule** dialog box, where you can create a schedule.</span></span> <span data-ttu-id="b34f9-200">スケジュールを保存するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b34f9-200">To save the schedule, click **OK**.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="b34f9-201">*[フルテキスト インデックスのプロパティ]* ダイアログ ボックスを閉じると、新しいスケジュールが SQL Server エージェント ジョブ (*database_name*. **table_name** でテーブルの増分作成を開始) に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-201">A SQL Server Agent job (Start Incremental Table Population on *database_name*.*table_name*) is associated with a new schedule after you exit the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="b34f9-202">フルテキスト インデックスのスケジュールを複数作成した場合は、すべてのスケジュールで同じジョブが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-202">If you create multiple schedules for the full-text index, they all use the same job.</span></span>  
  
    -   <span data-ttu-id="b34f9-203">スケジュールを変更するには、スケジュールを選択して **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b34f9-203">To change a schedule, select it and click **Edit**.</span></span>  
  
         <span data-ttu-id="b34f9-204">スケジュールを変更できる **[新しいフルテキスト インデックス テーブルのスケジュール]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-204">This opens the **New Full-Text Indexing Table Schedule** dialog box, where you can modify the schedule.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b34f9-205">ジョブの変更については、「 [ジョブの変更](../../ssms/agent/modify-a-job.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b34f9-205">For information about modifying a job, see [Modify a Job](../../ssms/agent/modify-a-job.md).</span></span>  
  
    -   <span data-ttu-id="b34f9-206">スケジュールを削除するには、スケジュールを選択して **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b34f9-206">To remove a schedule, select it and click **Delete**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  

  
##  <a name="troubleshooting-errors-in-a-full-text-population-crawl"></a><a name="crawl"></a><span data-ttu-id="b34f9-207">フルテキスト作成 (クロール) で発生したエラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b34f9-207">Troubleshooting Errors in a Full-Text Population (Crawl)</span></span>  
 <span data-ttu-id="b34f9-208">クロール時にエラーが発生すると、フルテキスト検索クロール ログ記録機能によってクロール ログが作成および保持されます。このログはプレーンテキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="b34f9-208">When an error occurs during a crawl, the Full-Text Search crawl logging facility creates and maintains a crawl log, which is a plain text file.</span></span> <span data-ttu-id="b34f9-209">各クロール ログは特定のフルテキスト カタログに対応します。</span><span class="sxs-lookup"><span data-stu-id="b34f9-209">Each crawl log corresponds to a particular full-text catalog.</span></span> <span data-ttu-id="b34f9-210">既定では、特定のインスタンス (この場合は最初のインスタンス) のクロール ログは %ProgramFiles%\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="b34f9-210">By default crawl logs for a given instance, in this case, the first instance, are located in %ProgramFiles%\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG folder.</span></span> <span data-ttu-id="b34f9-211">クロール ログは次のような規則に従って命名されます。</span><span class="sxs-lookup"><span data-stu-id="b34f9-211">The crawl log file follows the following naming scheme:</span></span>  
  
 <span data-ttu-id="b34f9-212">SQLFT \<DatabaseID> \<FullTextCatalogID> 。ログ [ \<n> ]</span><span class="sxs-lookup"><span data-stu-id="b34f9-212">SQLFT\<DatabaseID>\<FullTextCatalogID>.LOG[\<n>]</span></span>  
  
 <`DatabaseID`>  
 <span data-ttu-id="b34f9-213">データベースの ID です。</span><span class="sxs-lookup"><span data-stu-id="b34f9-213">The ID of a database.</span></span><span data-ttu-id="b34f9-214"> <`dbid`> は、0で始まる5桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="b34f9-214"> <`dbid`> is a five digit number with leading zeros.</span></span>  
  
 <`FullTextCatalogID`>  
 <span data-ttu-id="b34f9-215">フルテキスト カタログ ID です。</span><span class="sxs-lookup"><span data-stu-id="b34f9-215">Full-text catalog ID.</span></span><span data-ttu-id="b34f9-216"> <`catid`> は、0で始まる5桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="b34f9-216"> <`catid`> is a five digit number with leading zeros.</span></span>  
  
 <`n`>  
 <span data-ttu-id="b34f9-217">同じフルテキスト カタログに 1 つ以上のクロール ログが存在することを示す整数です。</span><span class="sxs-lookup"><span data-stu-id="b34f9-217">Is an integer that indicates one or more crawl logs of the same full-text catalog exist.</span></span>  
  
 <span data-ttu-id="b34f9-218">たとえば、SQLFT0000500008.2 はデータベース ID が 5 で、フルテキスト カタログ ID が 8 のクロール ログ ファイルです。</span><span class="sxs-lookup"><span data-stu-id="b34f9-218">For example, SQLFT0000500008.2 is the crawl log file for a database with database ID = 5, and full-text catalog ID = 8.</span></span> <span data-ttu-id="b34f9-219">ファイル名の最後の 2 は、このデータベースとカタログのペアに 2 つのクロール ログ ファイルが存在することを示しています。</span><span class="sxs-lookup"><span data-stu-id="b34f9-219">The 2 at the end of the file name indicates that there are two crawl log files for this database/catalog pair.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="b34f9-220">参照</span><span class="sxs-lookup"><span data-stu-id="b34f9-220">See Also</span></span>  
 <span data-ttu-id="b34f9-221">[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b34f9-221">[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) </span></span>  
 <span data-ttu-id="b34f9-222">[フルテキスト検索の概要](get-started-with-full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="b34f9-222">[Get Started with Full-Text Search](get-started-with-full-text-search.md) </span></span>  
 <span data-ttu-id="b34f9-223">[フルテキスト インデックスの作成と管理](create-and-manage-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="b34f9-223">[Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) </span></span>  
 <span data-ttu-id="b34f9-224">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b34f9-224">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 [<span data-ttu-id="b34f9-225">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b34f9-225">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
