---
title: 階層データ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [SQL Server], tables to support
- hierarchyid [Database Engine], concepts
- hierarchical tables [Database Engine]
- SqlHierarchyId
- hierarchyid [Database Engine]
- hierarchical queries [SQL Server], using hierarchyid data type
ms.assetid: 19aefa9a-fbc2-4b22-92cf-67b8bb01671c
author: rothja
ms.author: jroth
ms.openlocfilehash: 351a5a4aa6bc1655b8da5fced3e51385dd498bdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639962"
---
# <a name="hierarchical-data-sql-server"></a><span data-ttu-id="98bf6-102">階層データ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="98bf6-102">Hierarchical Data (SQL Server)</span></span>
  <span data-ttu-id="98bf6-103">組み込み `hierarchyid` データ型を使用すると、階層データの格納とクエリが容易になります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-103">The built-in `hierarchyid` data type makes it easier to store and query hierarchical data.</span></span> <span data-ttu-id="98bf6-104">`hierarchyid`は、最も一般的な階層データであるツリーを表すために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="98bf6-104">`hierarchyid` is optimized for representing trees, which are the most common type of hierarchical data.</span></span>  
  
 <span data-ttu-id="98bf6-105">階層データは、階層リレーションシップで相互に関連付けられたデータ アイテムのセットとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-105">Hierarchical data is defined as a set of data items that are related to each other by hierarchical relationships.</span></span> <span data-ttu-id="98bf6-106">あるデータ アイテムが別のアイテムの親となる場合は、そこに階層リレーションシップが存在します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-106">Hierarchical relationships exist where one item of data is the parent of another item.</span></span> <span data-ttu-id="98bf6-107">データベースに一般的に格納される階層データの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-107">Examples of the hierarchical data that is commonly stored in databases include the following:</span></span>  
  
-   <span data-ttu-id="98bf6-108">組織構造</span><span class="sxs-lookup"><span data-stu-id="98bf6-108">An organizational structure</span></span>  
  
-   <span data-ttu-id="98bf6-109">ファイル システム</span><span class="sxs-lookup"><span data-stu-id="98bf6-109">A file system</span></span>  
  
-   <span data-ttu-id="98bf6-110">プロジェクト内のタスクのセット</span><span class="sxs-lookup"><span data-stu-id="98bf6-110">A set of tasks in a project</span></span>  
  
-   <span data-ttu-id="98bf6-111">言語の用語の分類</span><span class="sxs-lookup"><span data-stu-id="98bf6-111">A taxonomy of language terms</span></span>  
  
-   <span data-ttu-id="98bf6-112">Web ページ間のリンクのグラフ</span><span class="sxs-lookup"><span data-stu-id="98bf6-112">A graph of links between Web pages</span></span>  
  
 <span data-ttu-id="98bf6-113">階層構造を持つテーブルを作成したり、別の場所に格納されているデータの階層構造を表したりするには、 [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) を使用します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-113">Use [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) as a data type to create tables with a hierarchical structure, or to describe the hierarchical structure of data that is stored in another location.</span></span> <span data-ttu-id="98bf6-114">階層データのクエリや管理を実行するには、 [!INCLUDE[tsql](../includes/tsql-md.md)] の [hierarchyid 関数](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) を使用します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-114">Use the [hierarchyid functions](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) in [!INCLUDE[tsql](../includes/tsql-md.md)] to query and manage hierarchical data.</span></span>  
  
##  <a name="key-properties-of-hierarchyid"></a><a name="keyprops"></a> <span data-ttu-id="98bf6-115">hierarchyid の主要な特性</span><span class="sxs-lookup"><span data-stu-id="98bf6-115">Key Properties of hierarchyid</span></span>  
 <span data-ttu-id="98bf6-116">データ型の値は、 `hierarchyid` ツリー階層内の位置を表します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-116">A value of the `hierarchyid` data type represents a position in a tree hierarchy.</span></span> <span data-ttu-id="98bf6-117">`hierarchyid` の値には、以下の特性があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-117">Values for `hierarchyid` have the following properties:</span></span>  
  
-   <span data-ttu-id="98bf6-118">非常にコンパクト</span><span class="sxs-lookup"><span data-stu-id="98bf6-118">Extremely compact</span></span>  
  
     <span data-ttu-id="98bf6-119">*n* 個のノードを持つツリー内の、1 つのノードを表すために必要な平均ビット数は、平均ファンアウト (ノードあたりの子の平均数) によって決まります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-119">The average number of bits that are required to represent a node in a tree with *n* nodes depends on the average fanout (the average number of children of a node).</span></span> <span data-ttu-id="98bf6-120">ファンアウトが小さい場合 (0 ～ 7)、サイズは約 6\*logA*n* ビットです (A は平均ファンアウト)。</span><span class="sxs-lookup"><span data-stu-id="98bf6-120">For small fanouts, (0-7) the size is about 6\*logA*n* bits, where A is the average fanout.</span></span> <span data-ttu-id="98bf6-121">平均ファンアウトが 6 レベルで、100,000 人から成る組織階層の場合、1 つのノードには約 38 ビットが必要です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-121">A node in an organizational hierarchy of 100,000 people with an average fanout of 6 levels takes about 38 bits.</span></span> <span data-ttu-id="98bf6-122">格納時には、これが 40 ビット (5 バイト) に切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-122">This is rounded up to 40 bits, or 5 bytes, for storage.</span></span>  
  
-   <span data-ttu-id="98bf6-123">深さ優先順で比較</span><span class="sxs-lookup"><span data-stu-id="98bf6-123">Comparison is in depth-first order</span></span>  
  
     <span data-ttu-id="98bf6-124">A と b の2つの値を指定した場合 `hierarchyid` 、 **<b**は、ツリーの深さ優先走査で b の前に来ることを意味します**a** 。 **b**</span><span class="sxs-lookup"><span data-stu-id="98bf6-124">Given two `hierarchyid` values **a** and **b**, **a<b** means a comes before b in a depth-first traversal of the tree.</span></span> <span data-ttu-id="98bf6-125">`hierarchyid` データ型のインデックスは深さ優先順であり、深さ優先検査で近接するノードどうしは、相互に近接して格納されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-125">Indexes on `hierarchyid` data types are in depth-first order, and nodes close to each other in a depth-first traversal are stored near each other.</span></span> <span data-ttu-id="98bf6-126">たとえば、あるレコードの子は、そのレコードに隣接して格納されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-126">For example, the children of a record are stored adjacent to that record.</span></span>  
  
-   <span data-ttu-id="98bf6-127">任意の挿入および削除のサポート</span><span class="sxs-lookup"><span data-stu-id="98bf6-127">Support for arbitrary insertions and deletions</span></span>  
  
     <span data-ttu-id="98bf6-128">[GetDescendant](/sql/t-sql/data-types/getdescendant-database-engine) メソッドを使用すると、指定したノードの右側や左側、または任意の 2 つの兄弟間に、いつでも兄弟を生成できます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-128">By using the [GetDescendant](/sql/t-sql/data-types/getdescendant-database-engine) method, it is always possible to generate a sibling to the right of any given node, to the left of any given node, or between any two siblings.</span></span> <span data-ttu-id="98bf6-129">階層に対して任意の数のノードを挿入または削除しても、比較の特性は維持されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-129">The comparison property is maintained when an arbitrary number of nodes is inserted or deleted from the hierarchy.</span></span> <span data-ttu-id="98bf6-130">ほとんどの挿入や削除では、コンパクトさも維持されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-130">Most insertions and deletions preserve the compactness property.</span></span> <span data-ttu-id="98bf6-131">ただし、2 ノード間に挿入した場合は、hierarchyid 値のコンパクトさがやや失われます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-131">However, insertions between two nodes will produce hierarchyid values with a slightly less compact representation.</span></span>  
  
  
##  <a name="limitations-of-hierarchyid"></a><a name="limits"></a> <span data-ttu-id="98bf6-132">hierarchyid の制限事項</span><span class="sxs-lookup"><span data-stu-id="98bf6-132">Limitations of hierarchyid</span></span>  
 <span data-ttu-id="98bf6-133">`hierarchyid`データ型には次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-133">The `hierarchyid` data type has the following limitations:</span></span>  
  
-   <span data-ttu-id="98bf6-134">`hierarchyid` 型の列が自動的にツリーを表すことはありません。</span><span class="sxs-lookup"><span data-stu-id="98bf6-134">A column of type `hierarchyid` does not automatically represent a tree.</span></span> <span data-ttu-id="98bf6-135">行と行の間に必要なリレーションシップが反映されるよう、`hierarchyid` 値を生成して割り当てるのは、アプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-135">It is up to the application to generate and assign `hierarchyid` values in such a way that the desired relationship between rows is reflected in the values.</span></span> <span data-ttu-id="98bf6-136">アプリケーションによっては、別のテーブルに定義されている階層内の位置を示す `hierarchyid` 型の列を持つ場合もあります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-136">Some applications might have a column of type `hierarchyid` that indicates the location in a hierarchy defined in another table.</span></span>  
  
-   <span data-ttu-id="98bf6-137">ph x="1" /&gt; 値の生成と割り当てにおいて、コンカレンシーを管理するのはアプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-137">It is up to the application to manage concurrency in generating and assigning `hierarchyid` values.</span></span> <span data-ttu-id="98bf6-138">アプリケーションで一意キー制約を使用したり、独自のロジックで一意性を適用したりしない限り、列内の `hierarchyid` 値の一意性は保証されません。</span><span class="sxs-lookup"><span data-stu-id="98bf6-138">There is no guarantee that `hierarchyid` values in a column are unique unless the application uses a unique key constraint or enforces uniqueness itself through its own logic.</span></span>  
  
-   <span data-ttu-id="98bf6-139">`hierarchyid` 値で表される階層リレーションシップは、外部キー リレーションシップとは適用方法が異なります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-139">Hierarchical relationships represented by `hierarchyid` values are not enforced like a foreign key relationship.</span></span> <span data-ttu-id="98bf6-140">階層リレーションシップでは、A に子 B があるとき、A だけを削除し、存在しないレコードに対するリレーションシップを B が引き続き保持することも可能であり、これが適切な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-140">It is possible and sometimes appropriate to have a hierarchical relationship where A has a child B, and then A is deleted leaving B with a relationship to a nonexistent record.</span></span> <span data-ttu-id="98bf6-141">この動作を許容しない場合は、親を削除する前に、アプリケーションで子孫に対するクエリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-141">If this behavior is unacceptable, the application must query for descendants before deleting parents.</span></span>  
  
  
##  <a name="when-to-use-alternatives-to-hierarchyid"></a><a name="alternatives"></a> <span data-ttu-id="98bf6-142">hierarchyid に代わる方法を使用する場合</span><span class="sxs-lookup"><span data-stu-id="98bf6-142">When to Use Alternatives to hierarchyid</span></span>  
 <span data-ttu-id="98bf6-143">`hierarchyid` を使用せずに階層データを表すためには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-143">Two alternatives to `hierarchyid` for representing hierarchical data are:</span></span>  
  
-   <span data-ttu-id="98bf6-144">親/子</span><span class="sxs-lookup"><span data-stu-id="98bf6-144">Parent/Child</span></span>  
  
-   <span data-ttu-id="98bf6-145">XML</span><span class="sxs-lookup"><span data-stu-id="98bf6-145">XML</span></span>  
  
 <span data-ttu-id="98bf6-146">通常、これらの方法よりも `hierarchyid` の方が優れています。</span><span class="sxs-lookup"><span data-stu-id="98bf6-146">`hierarchyid` is generally superior to these alternatives.</span></span> <span data-ttu-id="98bf6-147">しかし、次のような状況では、これらの代替方法を使用した方がよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-147">However, there are specific situations detailed below where the alternatives are likely superior.</span></span>  
  
### <a name="parentchild"></a><span data-ttu-id="98bf6-148">親/子</span><span class="sxs-lookup"><span data-stu-id="98bf6-148">Parent/Child</span></span>  
 <span data-ttu-id="98bf6-149">親/子の方法を使用すると、各行に親への参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-149">When using the Parent/Child approach, each row contains a reference to the parent.</span></span> <span data-ttu-id="98bf6-150">次のテーブルでは、親/子リレーションシップにある親と子の行を含めるための、一般的なテーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-150">The following table defines a typical table used to contain the parent and the child rows in a Parent/Child relationship:</span></span>  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE TABLE ParentChildOrg  
   (  
    BusinessEntityID int PRIMARY KEY,  
    ManagerId int REFERENCES ParentChildOrg(BusinessEntityID),  
    EmployeeName nvarchar(50)   
   ) ;  
GO  
```  
  
 <span data-ttu-id="98bf6-151">一般的な操作に関する親/子と `hierarchyid` の比較</span><span class="sxs-lookup"><span data-stu-id="98bf6-151">Comparing Parent/Child and `hierarchyid` for Common Operations</span></span>  
  
-   <span data-ttu-id="98bf6-152">サブツリーのクエリは、`hierarchyid` を使用した方がはるかに高速です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-152">Subtree queries are significantly faster with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="98bf6-153">直接の子孫のクエリは、`hierarchyid` を使用するとわずかに遅くなります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-153">Direct descendant queries are slightly slower with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="98bf6-154">非リーフ ノードの移動は、`hierarchyid` を使用すると遅くなります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-154">Moving non-leaf nodes is slower with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="98bf6-155">非リーフ ノードを挿入する場合、およびリーフ ノードを挿入または移動する場合も、`hierarchyid` を使用する場合と同様に複雑になります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-155">Inserting non-leaf nodes and inserting or moving leaf nodes has the same complexity with `hierarchyid`.</span></span>  
  
 <span data-ttu-id="98bf6-156">次の条件に当てはまるときは、親/子を使用した方がよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-156">Parent/Child might be superior when the following conditions exist:</span></span>  
  
-   <span data-ttu-id="98bf6-157">キーのサイズが非常に重要なとき。</span><span class="sxs-lookup"><span data-stu-id="98bf6-157">The size of the key is critical.</span></span> <span data-ttu-id="98bf6-158">同じノード数に対して、`hierarchyid` 値が整数系 (`smallint`、`int`、`bigint`) の値以上であるとき。</span><span class="sxs-lookup"><span data-stu-id="98bf6-158">For the same number of nodes, a `hierarchyid` value is equal to or larger than an integer-family (`smallint`, `int`, `bigint`) value.</span></span> <span data-ttu-id="98bf6-159">これが、ごくまれに親/子を使用する場合の唯一の理由です。親/子構造の使用時に必要な共通テーブル式よりも、`hierarchyid` の方が、I/O の局所性と CPU の複雑さにおいてはるかに優れているためです。</span><span class="sxs-lookup"><span data-stu-id="98bf6-159">This is only a reason to use Parent/Child in rare cases, because `hierarchyid` has significantly better locality of I/O and CPU complexity than the common table expressions required when you are using a Parent/Child structure.</span></span>  
  
-   <span data-ttu-id="98bf6-160">階層の複数セクションにわたるクエリをめったに実行しないとき。</span><span class="sxs-lookup"><span data-stu-id="98bf6-160">Queries rarely query across sections of the hierarchy.</span></span> <span data-ttu-id="98bf6-161">つまり、通常のクエリが、階層内の単一ポイントのみを対象とするとき。</span><span class="sxs-lookup"><span data-stu-id="98bf6-161">In other words, queries usually address only a single point in the hierarchy.</span></span> <span data-ttu-id="98bf6-162">このようなケースでは、同じ場所への配置は重要でありません。</span><span class="sxs-lookup"><span data-stu-id="98bf6-162">In these cases co-location is not important.</span></span> <span data-ttu-id="98bf6-163">たとえば、個々の従業員の給与処理のみに組織テーブルを使用する場合、親/子の方が優れています。</span><span class="sxs-lookup"><span data-stu-id="98bf6-163">For example, Parent/Child is superior when the organization table is only used to process payroll for individual employees.</span></span>  
  
-   <span data-ttu-id="98bf6-164">非リーフ サブツリーが頻繁に移動し、かつパフォーマンスが非常に重要なとき。</span><span class="sxs-lookup"><span data-stu-id="98bf6-164">Non-leaf subtrees move frequently and performance is very important.</span></span> <span data-ttu-id="98bf6-165">親/子表現では、階層内の行の場所を変更すると、1 行のみが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-165">In a parent/child representation changing the location of a row in a hierarchy affects a single row.</span></span> <span data-ttu-id="98bf6-166">使用状況の行の場所を変更すると、 `hierarchyid` *n*行が影響を受けます。 *n*は移動されるサブツリー内のノード数です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-166">Changing the location of a row in a `hierarchyid` usage affects *n* rows, where *n* is number of nodes in the sub-tree being moved.</span></span>  
  
     <span data-ttu-id="98bf6-167">非リーフ サブツリーが頻繁に移動し、かつパフォーマンスが重要だが、ほとんどの移動が正しく定義された階層レベルで行われるときは、上位レベルと下位レベルを 2 つの階層に分割することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="98bf6-167">If the non-leaf subtrees move frequently and performance is important, but most of the moves are at a well-defined level of the hierarchy, consider splitting the higher and lower levels into two hierarchies.</span></span> <span data-ttu-id="98bf6-168">こうすると、すべての移動が上位階層のリーフ レベルになります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-168">This makes all moves into leaf-levels of the higher hierarchy.</span></span> <span data-ttu-id="98bf6-169">たとえば、サービスによってホストされている Web サイトの階層があるとします。</span><span class="sxs-lookup"><span data-stu-id="98bf6-169">For instance, consider a hierarchy of Web sites hosted by a service.</span></span> <span data-ttu-id="98bf6-170">サイトには、階層状に配置された多くのページが含まれています。</span><span class="sxs-lookup"><span data-stu-id="98bf6-170">Sites contain many pages arranged in a hierarchical manner.</span></span> <span data-ttu-id="98bf6-171">ホストされているサイトは、サイト階層内の他の場所に移動される可能性がありますが、下位ページの配置が変更されることはまれです。</span><span class="sxs-lookup"><span data-stu-id="98bf6-171">Hosted sites might be moved to other locations in the site hierarchy, but the subordinate pages are rarely re-arranged.</span></span> <span data-ttu-id="98bf6-172">これは、次のように表すことができます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-172">This could be represented via:</span></span>  
  
    ```  
    CREATE TABLE HostedSites   
       (  
        SiteId hierarchyid, PageId hierarchyid  
       ) ;  
    GO  
    ```  
  
  
### <a name="xml"></a><span data-ttu-id="98bf6-173">XML</span><span class="sxs-lookup"><span data-stu-id="98bf6-173">XML</span></span>  
 <span data-ttu-id="98bf6-174">XML ドキュメントはツリーです。このため、XML データ型の 1 つのインスタンスで、完全な階層を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-174">An XML document is a tree, and therefore a single XML data type instance can represent a complete hierarchy.</span></span> <span data-ttu-id="98bf6-175">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で XML インデックスを作成する際は、階層内の位置を表す `hierarchyid` 値が内部で使用されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-175">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] when an XML index is created, `hierarchyid` values are used internally to represent the position in the hierarchy.</span></span>  
  
 <span data-ttu-id="98bf6-176">次のすべての条件に当てはまるときは、XML データ型を使用した方がよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-176">Using XML data type can be superior when all the following are true:</span></span>  
  
-   <span data-ttu-id="98bf6-177">完全な階層が常に格納および取得されるとき。</span><span class="sxs-lookup"><span data-stu-id="98bf6-177">The complete hierarchy is always stored and retrieved.</span></span>  
  
-   <span data-ttu-id="98bf6-178">アプリケーションによって XML 形式でデータが消費されるとき。</span><span class="sxs-lookup"><span data-stu-id="98bf6-178">The data is consumed in XML format by the application.</span></span>  
  
-   <span data-ttu-id="98bf6-179">述語検索が非常に限られており、かつパフォーマンスが重要でないとき。</span><span class="sxs-lookup"><span data-stu-id="98bf6-179">Predicate searches are extremely limited and not performance critical.</span></span>  
  
 <span data-ttu-id="98bf6-180">たとえば、アプリケーションで複数の組織を追跡し、完全な組織階層を常に格納および取得し、かつ単一の組織に対するクエリを実行しないときには、次の形式のテーブルが効果的な場合があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-180">For example, if an application tracks multiple organizations, always stores and retrieves the complete organizational hierarchy, and does not query into a single organization, a table of the following form might make sense:</span></span>  
  
```  
CREATE TABLE XMLOrg   
    (  
    Orgid int,  
    Orgdata xml  
    ) ;  
GO  
```  
  
  
##  <a name="indexing-strategies-for-hierarchical-data"></a><a name="indexing"></a> <span data-ttu-id="98bf6-181">階層データのインデックス作成方法</span><span class="sxs-lookup"><span data-stu-id="98bf6-181">Indexing Strategies for Hierarchical Data</span></span>  
 <span data-ttu-id="98bf6-182">階層データのインデックスを作成する方法には、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-182">There are two strategies for indexing hierarchical data:</span></span>  
  
-   <span data-ttu-id="98bf6-183">**深さ優先**</span><span class="sxs-lookup"><span data-stu-id="98bf6-183">**Depth-first**</span></span>  
  
     <span data-ttu-id="98bf6-184">深さ優先のインデックスで、サブツリー内の行が相互に近接して格納されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-184">A depth-first index stores the rows in a subtree near each other.</span></span> <span data-ttu-id="98bf6-185">たとえば、ある管理者の管理責任下にあるすべての従業員が、管理者のレコードの近くに格納されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-185">For example, all employees that report through a manager are stored near their managers' record.</span></span>  
  
     <span data-ttu-id="98bf6-186">深さ優先のインデックスでは、ノードのサブツリー内のすべてのノードが同じ場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-186">In a depth-first index, all nodes in the subtree of a node are co-located.</span></span> <span data-ttu-id="98bf6-187">このため、"このフォルダーとそのサブフォルダーにあるファイルをすべて検索する" など、サブツリーに関するクエリに応答するには、深さ優先インデックスが効率的です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-187">Depth-first indexes are therefore efficient for answering queries about subtrees, such as "Find all files in this folder and its subfolders".</span></span>  
  
-   <span data-ttu-id="98bf6-188">**幅優先**</span><span class="sxs-lookup"><span data-stu-id="98bf6-188">**Breadth-first**</span></span>  
  
     <span data-ttu-id="98bf6-189">幅優先の場合、階層の各レベルの行が一緒に格納されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-189">A breadth-first stores the rows each level of the hierarchy together.</span></span> <span data-ttu-id="98bf6-190">たとえば、同一の管理者に直属する従業員のレコードが、相互に近接して格納されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-190">For example, the records of employees who directly report to the same manager are stored near each other.</span></span>  
  
     <span data-ttu-id="98bf6-191">幅優先のインデックスでは、ノードの直接の子すべてが同じ場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-191">In a breadth-first index all direct children of a node are co-located.</span></span> <span data-ttu-id="98bf6-192">このため、"この管理者に直属するすべての従業員を検索する" など、直下の子に関するクエリに応答するには、幅優先インデックスが効率的です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-192">Breadth-first indexes are therefore efficient for answering queries about immediate children, such as "Find all employees who report directly to this manager".</span></span>  
  
 <span data-ttu-id="98bf6-193">深さ優先、幅優先、またはこれらの両方を使用するか、また、どちらをクラスター化キーとするか (該当する場合) は、上記の種類のクエリの相対的重要度と、SELECT 操作と DML 操作の相対的重要度によって決まります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-193">Whether to have depth-first, breadth-first, or both, and which to make the clustering key (if any), depends on the relative importance of the above types of queries, and the relative importance of SELECT vs. DML operations.</span></span> <span data-ttu-id="98bf6-194">インデックス作成方法の詳細な例については、「 [チュートリアル : hierarchyid データ型の使用](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98bf6-194">For a detailed example of indexing strategies, see [Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md).</span></span>  
  
  
### <a name="creating-indexes"></a><span data-ttu-id="98bf6-195">インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="98bf6-195">Creating Indexes</span></span>  
 <span data-ttu-id="98bf6-196">幅優先順を作成するには、GetLevel() メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-196">The GetLevel() method can be used to create a breadth first ordering.</span></span> <span data-ttu-id="98bf6-197">次の例では、幅優先と深さ優先の両方のインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-197">In the following example, both breadth-first and depth-first indexes are created:</span></span>  
  
```wmimof  
USE AdventureWorks2012 ;   
GO  
  
CREATE TABLE Organization  
   (  
    BusinessEntityID hierarchyid,  
    OrgLevel as BusinessEntityID.GetLevel(),   
    EmployeeName nvarchar(50) NOT NULL  
   ) ;  
GO  
  
CREATE CLUSTERED INDEX Org_Breadth_First   
ON Organization(OrgLevel,BusinessEntityID) ;  
GO  
  
CREATE UNIQUE INDEX Org_Depth_First   
ON Organization(BusinessEntityID) ;  
GO  
```  
  
  
## <a name="examples"></a><span data-ttu-id="98bf6-198">例</span><span class="sxs-lookup"><span data-stu-id="98bf6-198">Examples</span></span>  
  
### <a name="simple-example"></a><span data-ttu-id="98bf6-199">簡単な例</span><span class="sxs-lookup"><span data-stu-id="98bf6-199">Simple Example</span></span>  
 <span data-ttu-id="98bf6-200">作業を簡単に開始できるよう意図的に簡潔化された例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-200">The following example is intentionally simplistic to help you get started.</span></span> <span data-ttu-id="98bf6-201">最初に、geography データを保持するテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-201">First create a table to hold some geography data.</span></span>  
  
```  
CREATE TABLE SimpleDemo  
(Level hierarchyid NOT NULL,  
Location nvarchar(30) NOT NULL,  
LocationType nvarchar(9) NULL);  
```  
  
 <span data-ttu-id="98bf6-202">次に、いくつかの大陸、国、州、および都市のデータを挿入します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-202">Now insert data for some continents, countries, states, and cities.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES   
('/1/', 'Europe', 'Continent'),  
('/2/', 'South America', 'Continent'),  
('/1/1/', 'France', 'Country'),  
('/1/1/1/', 'Paris', 'City'),  
('/1/2/1/', 'Madrid', 'City'),  
('/1/2/', 'Spain', 'Country'),  
('/3/', 'Antarctica', 'Continent'),  
('/2/1/', 'Brazil', 'Country'),  
('/2/1/1/', 'Brasilia', 'City'),  
('/2/1/2/', 'Bahia', 'State'),  
('/2/1/2/1/', 'Salvador', 'City'),  
('/3/1/', 'McMurdo Station', 'City');  
```  
  
 <span data-ttu-id="98bf6-203">Level データを理解しやすいテキスト値に変換する列を追加するデータを選択します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-203">Select the data, adding a column that converts the Level data into a text value that is easy to understand.</span></span> <span data-ttu-id="98bf6-204">また、このクエリは、`hierarchyid` データ型で結果を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-204">This query also orders the result by the `hierarchyid` data type.</span></span>  
  
```  
SELECT CAST(Level AS nvarchar(100)) AS [Converted Level], *   
FROM SimpleDemo ORDER BY Level;  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
```  
Converted Level  Level     Location         LocationType  
/1/              0x58      Europe           Continent  
/1/1/            0x5AC0    France           Country  
/1/1/1/          0x5AD6    Paris            City  
/1/2/            0x5B40    Spain            Country  
/1/2/1/          0x5B56    Madrid           City  
/2/              0x68      South America    Continent  
/2/1/            0x6AC0    Brazil           Country  
/2/1/1/          0x6AD6    Brasilia         City  
/2/1/2/          0x6ADA    Bahia            State  
/2/1/2/1/        0x6ADAB0  Salvador         City  
/3/              0x78      Antarctica       Continent  
/3/1/            0x7AC0    McMurdo Station  City  
```  
  
 <span data-ttu-id="98bf6-205">内部に矛盾があるが、階層の構造は有効であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="98bf6-205">Notice that the hierarchy is has a valid structure, even though it is not internally consistent.</span></span> <span data-ttu-id="98bf6-206">州は Bahia だけです。</span><span class="sxs-lookup"><span data-stu-id="98bf6-206">Bahia is the only state.</span></span> <span data-ttu-id="98bf6-207">これは、都市 Brasilia のピアとして階層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-207">It appears in the hierarchy as a peer of the city Brasilia.</span></span> <span data-ttu-id="98bf6-208">同様に、McMurdo Station に親の国はありません。</span><span class="sxs-lookup"><span data-stu-id="98bf6-208">Similarly, McMurdo Station does not have a parent country.</span></span> <span data-ttu-id="98bf6-209">ユーザーは、この階層がそれぞれの用途に適しているかどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-209">Users must decide if this type of hierarchy is appropriate for their use.</span></span>  
  
 <span data-ttu-id="98bf6-210">別の行を追加し、結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-210">Add another row and select the results.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES ('/1/3/1/', 'Kyoto', 'City'), ('/1/3/1/', 'London', 'City');  
SELECT CAST(Level AS nvarchar(100)) AS [Converted Level], * FROM SimpleDemo ORDER BY Level;  
```  
  
 <span data-ttu-id="98bf6-211">これにより、考えられる問題が示されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-211">This demonstrates more possible problems.</span></span> <span data-ttu-id="98bf6-212">Kyoto は、親レベル `/1/3/1/` がなくても、レベル `/1/3/`として挿入できます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-212">Kyoto can be inserted as level `/1/3/1/` even though there is no parent level `/1/3/`.</span></span> <span data-ttu-id="98bf6-213">London と Kyoto の両方に同じ値の `hierarchyid` があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-213">And both London and Kyoto have the same value for the `hierarchyid`.</span></span> <span data-ttu-id="98bf6-214">ここでもユーザーはこの階層がそれぞれの用途に適しているかどうかを判断して、それぞれの用途に適していない値をブロックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-214">Again, users must decide if this type of hierarchy is appropriate for their use, and block values that are invalid for their usage.</span></span>  
  
 <span data-ttu-id="98bf6-215">また、このテーブルは、階層 `'/'`の上部を使用していません。</span><span class="sxs-lookup"><span data-stu-id="98bf6-215">Also, this table did not use the top of the hierarchy `'/'`.</span></span> <span data-ttu-id="98bf6-216">すべての大陸に共通する親が存在しないため、省略されています。</span><span class="sxs-lookup"><span data-stu-id="98bf6-216">It was omitted because there is no common parent of all the continents.</span></span> <span data-ttu-id="98bf6-217">地球を追加することで 1 を追加できます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-217">You can add one by adding the whole planet.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES ('/', 'Earth', 'Planet');  
```  
  
##  <a name="related-tasks"></a><a name="tasks"></a> <span data-ttu-id="98bf6-218">関連タスク</span><span class="sxs-lookup"><span data-stu-id="98bf6-218">Related Tasks</span></span>  
  
###  <a name="migrating-from-parentchild-to-hierarchyid"></a><a name="migrating"></a> <span data-ttu-id="98bf6-219">親/子から hierarchyid への移行</span><span class="sxs-lookup"><span data-stu-id="98bf6-219">Migrating from Parent/Child to hierarchyid</span></span>  
 <span data-ttu-id="98bf6-220">現在、ほとんどのツリーは親/子を使用して表されます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-220">Most trees are represented using Parent/Child.</span></span> <span data-ttu-id="98bf6-221">を使用して親/子構造からテーブルに移行する最も簡単 `hierarchyid` な方法は、一時列または一時テーブルを使用して、階層の各レベルのノード数を追跡することです。</span><span class="sxs-lookup"><span data-stu-id="98bf6-221">The easiest way to migrate from a Parent/Child structure to a table using `hierarchyid` is to use a temporary column or a temporary table to keep track of the number of nodes at each level of the hierarchy.</span></span> <span data-ttu-id="98bf6-222">親/子テーブルの移行例については、「 [チュートリアル : hierarchyid データ型の使用](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md)」のレッスン 1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98bf6-222">For an example of migrating a Parent/Child table, see lesson 1 of [Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md).</span></span>  
  
  
###  <a name="managing-a-tree-using-hierarchyid"></a><a name="BKMK_ManagingTrees"></a> <span data-ttu-id="98bf6-223">hierarchyid を使用したツリーの管理</span><span class="sxs-lookup"><span data-stu-id="98bf6-223">Managing a Tree Using hierarchyid</span></span>  
 <span data-ttu-id="98bf6-224">必ずしも `hierarchyid` 列がツリーを表すとは限りませんが、アプリケーションでは簡単に表すようにできます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-224">Although a `hierarchyid` column does not necessarily represent a tree, an application can easily ensure that it does.</span></span>  
  
-   <span data-ttu-id="98bf6-225">新しい値を生成する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="98bf6-225">When generating new values, do one of the following:</span></span>  
  
    -   <span data-ttu-id="98bf6-226">親行の最後の子の番号を追跡します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-226">Keep track of the last child number in the parent row.</span></span>  
  
    -   <span data-ttu-id="98bf6-227">最後の子を計算します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-227">Compute the last child.</span></span> <span data-ttu-id="98bf6-228">効率的に計算するには、幅優先のインデックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-228">Doing this efficiently requires a breadth-first index.</span></span>  
  
-   <span data-ttu-id="98bf6-229">列の一意のインデックスを作成することで (たとえばクラスター化キーの一部として)、一意性を適用します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-229">Enforce uniqueness by creating a unique index on the column, perhaps as part of a clustering key.</span></span> <span data-ttu-id="98bf6-230">一意の値が挿入されるようにするには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="98bf6-230">To ensure that unique values are inserted, do one of the following:</span></span>  
  
    -   <span data-ttu-id="98bf6-231">一意キー違反エラーを検出して、再試行します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-231">Detect unique key violation failures and retry.</span></span>  
  
    -   <span data-ttu-id="98bf6-232">それぞれの新しい子ノードの一意性を特定し、シリアル化可能なトランザクションの一部として挿入します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-232">Determine the uniqueness of each new child node, and insert it as part of a serializable transaction.</span></span>  
  
  
#### <a name="example-using-error-detection"></a><span data-ttu-id="98bf6-233">エラー検出の使用例</span><span class="sxs-lookup"><span data-stu-id="98bf6-233">Example Using Error Detection</span></span>  
 <span data-ttu-id="98bf6-234">次の例のサンプル コードは、新しい子 **EmployeeId** 値を計算してキー違反を検出し、 **INS_EMP** マーカーに戻って新しい行の **EmployeeId** 値を再計算します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-234">In the following example, the sample code computes the new child **EmployeeId** value, and then detects any key violation and returns to **INS_EMP** marker to recompute the **EmployeeId** value for the new row:</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE TABLE Org_T1  
   (  
    EmployeeId hierarchyid PRIMARY KEY,  
    OrgLevel AS EmployeeId.GetLevel(),  
    EmployeeName nvarchar(50)   
   ) ;  
GO  
  
CREATE INDEX Org_BreadthFirst ON Org_T1(OrgLevel, EmployeeId)  
GO  
  
CREATE PROCEDURE AddEmp(@mgrid hierarchyid, @EmpName nvarchar(50) )   
AS  
BEGIN  
    DECLARE @last_child hierarchyid  
INS_EMP:   
    SELECT @last_child = MAX(EmployeeId) FROM Org_T1   
    WHERE EmployeeId.GetAncestor(1) = @mgrid  
INSERT Org_T1 (EmployeeId, EmployeeName)  
SELECT @mgrid.GetDescendant(@last_child, NULL), @EmpName   
-- On error, return to INS_EMP to recompute @last_child  
IF @@error <> 0 GOTO INS_EMP   
END ;  
GO  
```  
  
  
#### <a name="example-using-a-serializable-transaction"></a><span data-ttu-id="98bf6-235">シリアル化可能なトランザクションの使用例</span><span class="sxs-lookup"><span data-stu-id="98bf6-235">Example Using a Serializable Transaction</span></span>  
 <span data-ttu-id="98bf6-236">**Org_BreadthFirst** インデックスによって、**@last_child** が範囲シークを使用するかどうかを判断できるようになります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-236">The **Org_BreadthFirst** index ensures that determining **@last_child** uses a range seek.</span></span> <span data-ttu-id="98bf6-237">アプリケーションで確認する必要がある他のエラーケースに加えて、挿入後の重複キー違反は、同じ id を持つ複数の従業員を追加しようとしたため、再計算する必要があることを示し **@last_child** ます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-237">In addition to other error cases an application might want to check, a duplicate key violation after the insert indicates an attempt to add multiple employees with the same id, and therefore **@last_child** must be recomputed.</span></span> <span data-ttu-id="98bf6-238">次のコードは、シリアル化可能なトランザクションと幅優先のインデックスを使用して、新しいノード値を計算します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-238">The following code uses a serializable transaction and a breadth-first index to compute the new node value:</span></span>  
  
```  
CREATE TABLE Org_T2  
    (  
    EmployeeId hierarchyid PRIMARY KEY,  
    LastChild hierarchyid,   
    EmployeeName nvarchar(50)   
    ) ;  
GO  
  
CREATE PROCEDURE AddEmp(@mgrid hierarchyid, @EmpName nvarchar(50))   
AS  
BEGIN  
DECLARE @last_child hierarchyid  
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
BEGIN TRANSACTION   
  
UPDATE Org_T2   
SET @last_child = LastChild = EmployeeId.GetDescendant(LastChild,NULL)  
WHERE EmployeeId = @mgrid  
INSERT Org_T2 (EmployeeId, EmployeeName)   
    VALUES(@last_child, @EmpName)  
COMMIT  
END ;  
```  
  
 <span data-ttu-id="98bf6-239">次のコードは、テーブルに 3 つの行を挿入して、その結果を返します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-239">The following code populates the table with three rows and returns the results:</span></span>  
  
```  
INSERT Org_T2 (EmployeeId, EmployeeName)   
    VALUES(hierarchyid::GetRoot(), 'David') ;  
GO  
AddEmp 0x , 'Sariya'  
GO  
AddEmp 0x58 , 'Mary'  
GO  
SELECT * FROM Org_T2  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
```  
EmployeeId LastChild EmployeeName  
---------- --------- ------------  
0x        0x58       David  
0x58      0x5AC0     Sariya  
0x5AC0    NULL       Mary  
```  
  
  
###  <a name="enforcing-a-tree"></a><a name="BKMK_EnforcingTrees"></a> <span data-ttu-id="98bf6-240">ツリーの強制</span><span class="sxs-lookup"><span data-stu-id="98bf6-240">Enforcing a tree</span></span>  
 <span data-ttu-id="98bf6-241">上記の例では、アプリケーションでツリーが保持されるようにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="98bf6-241">The above examples illustrate how an application can ensure that a tree is maintained.</span></span> <span data-ttu-id="98bf6-242">制約を使用してツリーを強制するには、主キー ID を参照する外部キー制約を使用して、各ノードの親を定義する計算列を作成します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-242">To enforce a tree by using constraints, a computed column that defines the parent of each node can be created with a foreign key constraint back to the primary key id.</span></span>  
  
```  
CREATE TABLE Org_T3  
(  
   EmployeeId hierarchyid PRIMARY KEY,  
   ParentId AS EmployeeId.GetAncestor(1) PERSISTED    
      REFERENCES Org_T3(EmployeeId),  
   LastChild hierarchyid,   
   EmployeeName nvarchar(50)  
)  
GO  
```  
  
 <span data-ttu-id="98bf6-243">リレーションシップを適用するこの方法は、階層ツリーを保持するための信頼がないコードにテーブルへの直接 DML アクセス権がある場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="98bf6-243">This method of enforcing a relationship is preferred when code that is not trusted to maintain the hierarchical tree has direct DML access to the table.</span></span> <span data-ttu-id="98bf6-244">ただし、このメソッドでは、すべての DML 操作で制約をチェックする必要があるため、パフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="98bf6-244">However this method might reduce performance because the constraint must be checked on every DML operation.</span></span>  
  
  
###  <a name="finding-ancestors-by-using-the-clr"></a><a name="findclr"></a> <span data-ttu-id="98bf6-245">CLR を使用した先祖の検索</span><span class="sxs-lookup"><span data-stu-id="98bf6-245">Finding Ancestors by Using the CLR</span></span>  
 <span data-ttu-id="98bf6-246">階層内の 2 つのノードに関連する一般的な操作は、最下位の共通の先祖を見つけることです。</span><span class="sxs-lookup"><span data-stu-id="98bf6-246">A common operation involving two nodes in a hierarchy is to find the lowest common ancestor.</span></span> <span data-ttu-id="98bf6-247">この [!INCLUDE[tsql](../includes/tsql-md.md)] 型は両方で使用可能であるため、または CLR で書き込むことができ `hierarchyid` ます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-247">This can be written in either [!INCLUDE[tsql](../includes/tsql-md.md)] or CLR, because the `hierarchyid` type is available in both.</span></span> <span data-ttu-id="98bf6-248">パフォーマンスが向上するため、CLR の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="98bf6-248">CLR is recommended because performance will be faster.</span></span>  
  
 <span data-ttu-id="98bf6-249">次の CLR コードを使用すると、先祖を一覧表示し、最下位の共通の先祖を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-249">Use the following CLR code to list ancestors and to find the lowest common ancestor:</span></span>  
  
```  
using System;  
using System.Collections;  
using System.Text;  
using Microsoft.SqlServer.Server;  
using Microsoft.SqlServer.Types;  
  
public partial class HierarchyId_Operations  
{  
    [SqlFunction(FillRowMethodName = "FillRow_ListAncestors")]  
    public static IEnumerable ListAncestors(SqlHierarchyId h)  
    {  
        while (!h.IsNull)  
        {  
            yield return (h);  
            h = h.GetAncestor(1);  
        }  
    }  
    public static void FillRow_ListAncestors(Object obj, out SqlHierarchyId ancestor)  
    {  
        ancestor = (SqlHierarchyId)obj;  
    }  
  
    public static HierarchyId CommonAncestor(SqlHierarchyId h1, HierarchyId h2)  
    {  
        while (!h1.IsDescendant(h2))  
            h1 = h1.GetAncestor(1);  
  
        return h1;  
    }  
}  
```  
  
 <span data-ttu-id="98bf6-250">以下の [!INCLUDE[tsql](../includes/tsql-md.md)] の例で **ListAncestor** メソッドおよび **CommonAncestor** メソッドを使用するには、DLL をビルドし、次のようなコードを実行して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の **HierarchyId_Operations** アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bf6-250">To use the **ListAncestor** and **CommonAncestor** methods in the following [!INCLUDE[tsql](../includes/tsql-md.md)] examples, build the DLL and create the **HierarchyId_Operations** assembly in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by executing code similar to the following:</span></span>  
  
```  
CREATE ASSEMBLY HierarchyId_Operations   
FROM '<path to DLL>\ListAncestors.dll'  
GO  
```  
  
  
###  <a name="listing-ancestors"></a><a name="ancestors"></a> <span data-ttu-id="98bf6-251">先祖の一覧表示</span><span class="sxs-lookup"><span data-stu-id="98bf6-251">Listing Ancestors</span></span>  
 <span data-ttu-id="98bf6-252">ノードの先祖のリストの作成は、組織内での位置を表示するなどの一般的な操作です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-252">Creating a list of ancestors of a node is a common operation, for instance to show position in an organization.</span></span> <span data-ttu-id="98bf6-253">これを実行するには、上で定義した **HierarchyId_Operations** クラスを使用して、テーブル値関数を使用するのが 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-253">One way of doing this is by using a table-valued-function using the **HierarchyId_Operations** class defined above:</span></span>  
  
 <span data-ttu-id="98bf6-254">[!INCLUDE[tsql](../includes/tsql-md.md)]の使用</span><span class="sxs-lookup"><span data-stu-id="98bf6-254">Using [!INCLUDE[tsql](../includes/tsql-md.md)]:</span></span>  
  
```  
CREATE FUNCTION ListAncestors (@node hierarchyid)  
RETURNS TABLE (node hierarchyid)  
AS  
EXTERNAL NAME HierarchyId_Operations.HierarchyId_Operations.ListAncestors  
GO  
```  
  
 <span data-ttu-id="98bf6-255">使用例</span><span class="sxs-lookup"><span data-stu-id="98bf6-255">Example of usage:</span></span>  
  
```  
DECLARE @h hierarchyid  
SELECT @h = OrgNode   
FROM HumanResources.EmployeeDemo    
WHERE LoginID = 'adventure-works\janice0' -- /1/1/5/2/  
  
SELECT LoginID, OrgNode.ToString() AS LogicalNode  
FROM HumanResources.EmployeeDemo AS ED  
JOIN ListAncestors(@h) AS A   
   ON ED.OrgNode = A.Node  
GO  
```  
  
  
###  <a name="finding-the-lowest-common-ancestor"></a><a name="lowestcommon"></a> <span data-ttu-id="98bf6-256">最下位の共通の先祖の検索</span><span class="sxs-lookup"><span data-stu-id="98bf6-256">Finding the Lowest Common Ancestor</span></span>  
 <span data-ttu-id="98bf6-257">上で定義した **HierarchyId_Operations** クラスを使用して、次の [!INCLUDE[tsql](../includes/tsql-md.md)] 関数を作成し、階層内の 2 つのノードに関連する最下位の共通の先祖を見つけます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-257">Using the **HierarchyId_Operations** class defined above, create the following [!INCLUDE[tsql](../includes/tsql-md.md)] function to find the lowest common ancestor involving two nodes in a hierarchy:</span></span>  
  
```  
CREATE FUNCTION CommonAncestor (@node1 hierarchyid, @node2 hierarchyid)  
RETURNS hierarchyid  
AS  
EXTERNAL NAME HierarchyId_Operations.HierarchyId_Operations.CommonAncestor  
GO  
```  
  
 <span data-ttu-id="98bf6-258">使用例</span><span class="sxs-lookup"><span data-stu-id="98bf6-258">Example of usage:</span></span>  
  
```  
DECLARE @h1 hierarchyid, @h2 hierarchyid  
  
SELECT @h1 = OrgNode   
FROM  HumanResources.EmployeeDemo   
WHERE LoginID = 'adventure-works\jossef0' -- Node is /1/1/3/  
  
SELECT @h2 = OrgNode   
FROM HumanResources.EmployeeDemo    
WHERE LoginID = 'adventure-works\janice0' -- Node is /1/1/5/2/  
  
SELECT OrgNode.ToString() AS LogicalNode, LoginID   
FROM HumanResources.EmployeeDemo    
WHERE OrgNode = dbo.CommonAncestor(@h1, @h2) ;  
```  
  
 <span data-ttu-id="98bf6-259">結果ノードは /1/1/</span><span class="sxs-lookup"><span data-stu-id="98bf6-259">The resultant node is /1/1/</span></span>  
  
  
###  <a name="moving-subtrees"></a><a name="BKMK_MovingSubtrees"></a> <span data-ttu-id="98bf6-260">サブツリーの移動</span><span class="sxs-lookup"><span data-stu-id="98bf6-260">Moving Subtrees</span></span>  
 <span data-ttu-id="98bf6-261">もう 1 つの一般的な操作は、サブツリーの移動です。</span><span class="sxs-lookup"><span data-stu-id="98bf6-261">Another common operation is moving subtrees.</span></span> <span data-ttu-id="98bf6-262">次の手順では、のサブツリーを取得 **@oldMgr** し、それをのサブツリー (を含む) にし **@oldMgr** **@newMgr** ます。</span><span class="sxs-lookup"><span data-stu-id="98bf6-262">The procedure below takes the subtree of **@oldMgr** and makes it (including **@oldMgr**) a subtree of **@newMgr**.</span></span>  
  
```  
CREATE PROCEDURE MoveOrg(@oldMgr nvarchar(256), @newMgr nvarchar(256) )  
AS  
BEGIN  
DECLARE @nold hierarchyid, @nnew hierarchyid  
SELECT @nold = OrgNode FROM HumanResources.EmployeeDemo WHERE LoginID = @oldMgr ;  
  
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
BEGIN TRANSACTION  
SELECT @nnew = OrgNode FROM HumanResources.EmployeeDemo WHERE LoginID = @newMgr ;  
  
SELECT @nnew = @nnew.GetDescendant(max(OrgNode), NULL)   
FROM HumanResources.EmployeeDemo WHERE OrgNode.GetAncestor(1)=@nnew ;  
  
UPDATE HumanResources.EmployeeDemo    
SET OrgNode = OrgNode.GetReparentedValue(@nold, @nnew)  
WHERE OrgNode.IsDescendantOf(@nold) = 1 ;  
  
COMMIT TRANSACTION  
END ;  
GO  
```  
  
  
## <a name="see-also"></a><span data-ttu-id="98bf6-263">参照</span><span class="sxs-lookup"><span data-stu-id="98bf6-263">See Also</span></span>  
 <span data-ttu-id="98bf6-264">[hierarchyid データ型メソッド リファレンス](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span><span class="sxs-lookup"><span data-stu-id="98bf6-264">[hierarchyid Data Type Method Reference](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span></span>  
 <span data-ttu-id="98bf6-265">[チュートリアル : hierarchyid データ型の使用](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="98bf6-265">[Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md) </span></span>  
 [<span data-ttu-id="98bf6-266">hierarchyid &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="98bf6-266">hierarchyid &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/hierarchyid-data-type-method-reference)  
  
  
