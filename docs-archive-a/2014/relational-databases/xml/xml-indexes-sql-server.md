---
title: XML インデックス (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- secondary indexes [XML in SQL Server]
- xml data type [SQL Server], indexes
- dropping indexes
- PATH index
- DROP_EXISTING clause
- XML [SQL Server], indexes
- primary indexes [XML in SQL Server]
- indexes [SQL Server], XML
- XML indexes [SQL Server], secondary
- BLOBs, XML indexes
- disabling indexes
- XML indexes [SQL Server], modifying
- XML indexes [SQL Server]
- XML indexes [SQL Server], primary
- modifying indexes
- XML indexes [SQL Server], dropping
- VALUE index
- XML indexes [SQL Server], xml data type
- PROPERTY index
- XML indexes [SQL Server], creating
ms.assetid: f5c9209d-b3f3-4543-b30b-01365a5e7333
author: rothja
ms.author: jroth
ms.openlocfilehash: bf9a33bc18790bf8821d778746a708f78bbb3d8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642638"
---
# <a name="xml-indexes-sql-server"></a><span data-ttu-id="a3eb0-102">XML インデックス (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a3eb0-102">XML Indexes (SQL Server)</span></span>
  <span data-ttu-id="a3eb0-103">`xml` データ型の列には XML インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-103">XML indexes can be created on `xml` data type columns.</span></span> <span data-ttu-id="a3eb0-104">列に保存されている XML インスタンスのすべてのタグ、値、およびパスにインデックスが設定されるので、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-104">They index all tags, values and paths over the XML instances in the column and benefit query performance.</span></span> <span data-ttu-id="a3eb0-105">次のような場合、XML インデックスの効果が得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-105">Your application may benefit from an XML index in the following situations:</span></span>  
  
-   <span data-ttu-id="a3eb0-106">ワークロードで XML 列へのクエリが頻繁に行われる場合。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-106">Queries on XML columns are common in your workload.</span></span> <span data-ttu-id="a3eb0-107">データ変更時の XML インデックスのメンテナンス コストを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-107">XML index maintenance cost during data modification must be considered.</span></span>  
  
-   <span data-ttu-id="a3eb0-108">XML 値が比較的大きいのに対し、取得する部分が比較的小さい場合。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-108">Your XML values are relatively large and the retrieved parts are relatively small.</span></span> <span data-ttu-id="a3eb0-109">インデックスを作成すると、実行時にデータ全体が解析されることを回避し、クエリ処理を効率化するためのインデックス参照を利用できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-109">Building the index avoids parsing the whole data at run time and benefits index lookups for efficient query processing.</span></span>  
  
 <span data-ttu-id="a3eb0-110">XML のインデックスは、次のカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-110">XML indexes fall into the following categories:</span></span>  
  
-   <span data-ttu-id="a3eb0-111">プライマリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-111">Primary XML index</span></span>  
  
-   <span data-ttu-id="a3eb0-112">セカンダリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-112">Secondary XML index</span></span>  
  
 <span data-ttu-id="a3eb0-113">`xml` 型の列の最初のインデックスは、プライマリ XML インデックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-113">The first index on the `xml` type column must be the primary XML index.</span></span> <span data-ttu-id="a3eb0-114">プライマリ XML インデックスを使用している場合は、PATH、VALUE、および PROPERTY という種類のセカンダリ XML インデックスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-114">Using the primary XML index, the following types of secondary indexes are supported: PATH, VALUE, and PROPERTY.</span></span> <span data-ttu-id="a3eb0-115">クエリの種類によって異なりますが、これらのセカンダリ XML インデックスを使用することで、クエリのパフォーマンス向上に役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-115">Depending on the type of queries, these secondary indexes might help improve query performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3eb0-116">XML インデックスを作成したり変更したりするには、`xml` データ型を操作できるようにデータベース オプションが正しく設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-116">You cannot create or modify an XML index unless the database options are set correctly for working with the `xml` data type.</span></span> <span data-ttu-id="a3eb0-117">詳細については、「 [XML 列でのフルテキスト検索の使用](use-full-text-search-with-xml-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-117">For more information, see [Use Full-Text Search with XML Columns](use-full-text-search-with-xml-columns.md).</span></span>  
  
 <span data-ttu-id="a3eb0-118">XML インスタンスは、BLOB (バイナリ ラージ オブジェクト) として `xml` 型の列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-118">XML instances are stored in `xml` type columns as large binary objects (BLOBs).</span></span> <span data-ttu-id="a3eb0-119">これらの XML インスタンスは大きくなる可能性がありますが、`xml` データ型インスタンスをバイナリ表記したものを最大 2 GB まで格納できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-119">These XML instances can be large, and the stored binary representation of `xml` data type instances can be up to 2 GB.</span></span> <span data-ttu-id="a3eb0-120">インデックスを設定しない場合、クエリを評価するためにこのようなバイナリ ラージ オブジェクトが実行時に細分化されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-120">Without an index, these binary large objects are shredded at run time to evaluate a query.</span></span> <span data-ttu-id="a3eb0-121">この細分化には時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-121">This shredding can be time-consuming.</span></span> <span data-ttu-id="a3eb0-122">たとえば、次のクエリについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-122">For example, consider the following query:</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.query('  
  /PD:ProductDescription/PD:Summary  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist ('/PD:ProductDescription/@ProductModelID[.="19"]') = 1  
```  
  
 <span data-ttu-id="a3eb0-123">`WHERE` 句の条件を満たす XML インスタンスを選択するために、テーブル `Production.ProductModel` の各行内の XML BLOB (バイナリ ラージ オブジェクト) が実行時に細分化されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-123">To select the XML instances that satisfy the condition in the `WHERE` clause, the XML binary large object (BLOB) in each row of table `Production.ProductModel` is shredded at run time.</span></span> <span data-ttu-id="a3eb0-124">次に、 `(/PD:ProductDescription/@ProductModelID[.="19"]`メソッドの式 `exist()` ) が評価されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-124">Then, the expression `(/PD:ProductDescription/@ProductModelID[.="19"]`) in the `exist()` method is evaluated.</span></span> <span data-ttu-id="a3eb0-125">このような実行時の細分化は、列に格納されたインスタンスのサイズや数によってはコストが高くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-125">This run-time shredding can be costly, depending on the size and number of instances stored in the column.</span></span>  
  
 <span data-ttu-id="a3eb0-126">使用しているアプリケーション環境で、XML BLOB (バイナリ ラージ オブジェクト) に対するクエリを頻繁に実行する場合は、`xml` 型の列のインデックスを設定することが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-126">If querying XML binary large objects (BLOBs) is common in your application environment, it helps to index the `xml` type columns.</span></span> <span data-ttu-id="a3eb0-127">ただし、データの変更時には、インデックスのメンテナンスに関するコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-127">However, there is a cost associated with maintaining the index during data modification.</span></span>  
  
## <a name="primary-xml-index"></a><span data-ttu-id="a3eb0-128">プライマリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-128">Primary XML Index</span></span>  
 <span data-ttu-id="a3eb0-129">プライマリ XML インデックスにより、XML 列に保存されている XML インスタンスのすべてのタグ、値、およびパスにインデックスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-129">The primary XML index indexes all tags, values, and paths within the XML instances in an XML column.</span></span> <span data-ttu-id="a3eb0-130">プライマリ XML インデックスを作成するには、XML 列があるテーブルの主キーにクラスター化インデックスが作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-130">To create a primary XML index, the table in which the XML column occurs must have a clustered index on the primary key of the table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a3eb0-131">この主キーを使用して、プライマリ XML インデックスの行を、XML 列を含むテーブルの行に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-131">uses this primary key to correlate rows in the primary XML index with rows in the table that contains the XML column.</span></span>  
  
 <span data-ttu-id="a3eb0-132">プライマリ XML インデックスは、`xml` データ型列内の XML BLOB の細分化された永続化表現です。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-132">The primary XML index is a shredded and persisted representation of the XML BLOBs in the `xml` data type column.</span></span> <span data-ttu-id="a3eb0-133">インデックスでは、列内の XML BLOB (バイナリ ラージ オブジェクト) ごとに、数行のデータ行が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-133">For each XML binary large object (BLOB) in the column, the index creates several rows of data.</span></span> <span data-ttu-id="a3eb0-134">インデックス内の行数は、XML バイナリ ラージ オブジェクトのノード数とほぼ等しくなります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-134">The number of rows in the index is approximately equal to the number of nodes in the XML binary large object.</span></span> <span data-ttu-id="a3eb0-135">クエリで完全な XML インスタンスを取得する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって XML 列からインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-135">When a query retrieves the full XML instance, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the instance from the XML column.</span></span> <span data-ttu-id="a3eb0-136">XML インスタンス内でクエリを実行するときはプライマリ XML インデックスが使用され、インデックス自体によってスカラー値または XML サブツリーが返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-136">Queries within XML instances use the primary XML index, and can return scalar values or XML subtrees by using the index itself.</span></span>  
  
 <span data-ttu-id="a3eb0-137">各行には、次のノード情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-137">Each row stores the following node information:</span></span>  
  
-   <span data-ttu-id="a3eb0-138">要素名、属性名などのタグ名。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-138">Tag name such as an element or attribute name.</span></span>  
  
-   <span data-ttu-id="a3eb0-139">ノード値。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-139">Node value.</span></span>  
  
-   <span data-ttu-id="a3eb0-140">要素ノード、属性ノード、テキスト ノードなどのノードの型。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-140">Node type such as an element node, attribute node, or text node.</span></span>  
  
-   <span data-ttu-id="a3eb0-141">ドキュメント内の表示順情報。内部ノード識別子によって表現されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-141">Document order information, represented by an internal node identifier.</span></span>  
  
-   <span data-ttu-id="a3eb0-142">各ノードから XML ツリーのルートまでのパス。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-142">Path from each node to the root of the XML tree.</span></span> <span data-ttu-id="a3eb0-143">クエリ内のパス式ではこの列を検索します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-143">This column is searched for path expressions in the query.</span></span>  
  
-   <span data-ttu-id="a3eb0-144">ベース テーブルの主キー。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-144">Primary key of the base table.</span></span> <span data-ttu-id="a3eb0-145">ベース テーブルとの逆結合のため、ベース テーブルの主キーがプライマリ XML インデックスにコピーされます。ベース テーブルの主キーの最大列数は 15 です。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-145">The primary key of the base table is duplicated in the primary XML index for a back join with the base table, and the maximum number of columns in the primary key of the base table is limited to 15.</span></span>  
  
 <span data-ttu-id="a3eb0-146">このノード情報は、指定されたクエリに対して XML の結果を評価し構築するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-146">This node information is used to evaluate and construct XML results for a specified query.</span></span> <span data-ttu-id="a3eb0-147">最適化のために、タグ名とノード型の情報は整数値でエンコードされるので、パス列でも同じエンコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-147">For optimization purposes, the tag name and the node type information are encoded as integer values, and the Path column uses the same encoding.</span></span> <span data-ttu-id="a3eb0-148">また、パスのサフィックスが既知の場合にのみパスを照合できるように、パスは逆の順序で格納されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-148">Also, paths are stored in reverse order to allow matching paths when only the path suffix is known.</span></span> <span data-ttu-id="a3eb0-149">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-149">For example:</span></span>  
  
-   <span data-ttu-id="a3eb0-150">`//ContactRecord/PhoneNumber` 最後の 2 つのロケーション ステップだけが既知です。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-150">`//ContactRecord/PhoneNumber` where only the last two steps are known</span></span>  
  
 <span data-ttu-id="a3eb0-151">OR</span><span class="sxs-lookup"><span data-stu-id="a3eb0-151">OR</span></span>  
  
-   <span data-ttu-id="a3eb0-152">`/Book/*/Title` 式の中間でワイルドカード文字 (`*`) が指定されています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-152">`/Book/*/Title` where the wildcard character (`*`) is specified in the middle of the expression.</span></span>  
  
 <span data-ttu-id="a3eb0-153">[xml データ型のメソッド](/sql/t-sql/xml/xml-data-type-methods) に関係するクエリの場合、クエリ プロセッサでプライマリ XML インデックスが使用され、スカラー値またはプライマリ インデックス自体の XML サブツリーのどちらかが返されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-153">The query processor uses the primary XML index for queries that involve [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) and returns either scalar values or the XML subtrees from the primary index itself.</span></span> <span data-ttu-id="a3eb0-154">(このプライマリ XML インデックスには XML インスタンスの再構築に必要なすべての情報が格納されています)。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-154">(This index stores all the necessary information to reconstruct the XML instance.)</span></span>  
  
 <span data-ttu-id="a3eb0-155">たとえば、次のクエリでは、テーブルの type 列に格納されている概要情報が返され `CatalogDescription``xml` `ProductModel` ます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-155">For example, the following query returns summary information stored in the `CatalogDescription``xml` type column in the `ProductModel` table.</span></span> <span data-ttu-id="a3eb0-156">このクエリでは、カタログの説明に <`Features`> の説明も含まれている製品モデルに限り <`Summary`> 情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-156">The query returns <`Summary`> information only for product models whose catalog description also stores the <`Features`> description.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")SELECT CatalogDescription.query('  /PD:ProductDescription/PD:Summary') as ResultFROM Production.ProductModelWHERE CatalogDescription.exist ('/PD:ProductDescription/PD:Features') = 1  
```  
  
 <span data-ttu-id="a3eb0-157">プライマリ XML インデックスでは、ベース テーブルの各 XML バイナリ ラージ オブジェクト インスタンスを細分化するのではなく、各 XML バイナリ ラージ オブジェクトに対応するインデックスの行が `exist()` メソッドで指定された式に対して順番に検索されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-157">With regard to the primary XML index, instead of shredding each XML binary large object instance in the base table, the rows in the index that correspond to each XML binary large object are searched sequentially for the expression specified in the `exist()` method.</span></span> <span data-ttu-id="a3eb0-158">インデックスのパス列にそのパスが見つかると、プライマリ XML インデックスから <`Summary`> 要素とそのサブツリーが共に取得され、`query()` メソッドの結果として XML バイナリ ラージ オブジェクトに変換されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-158">If the path is found in the Path column in the index, the <`Summary`> element together with its subtrees is retrieved from the primary XML index and converted into an XML binary large object as the result of the `query()` method.</span></span>  
  
 <span data-ttu-id="a3eb0-159">XML インスタンス全体を取得するときには、プライマリ XML インデックスが使用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-159">Note that the primary XML index is not used when retrieving a full XML instance.</span></span> <span data-ttu-id="a3eb0-160">たとえば、次のクエリでは、特定の製品モデルの製造手順を説明する XML インスタンス全体をテーブルから取得します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-160">For example, the following query retrieves from the table the whole XML instance that describes the manufacturing instructions for a specific product model.</span></span>  
  
```  
USE AdventureWorks2012;SELECT InstructionsFROM Production.ProductModel WHERE ProductModelID=7;  
```  
  
## <a name="secondary-xml-indexes"></a><span data-ttu-id="a3eb0-161">セカンダリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-161">Secondary XML Indexes</span></span>  
 <span data-ttu-id="a3eb0-162">検索のパフォーマンスを向上するために、セカンダリ XML インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-162">To enhance search performance, you can create secondary XML indexes.</span></span> <span data-ttu-id="a3eb0-163">セカンダリ XML インデックスを作成する前に、プライマリ XML インデックスが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-163">A primary XML index must first exist before you can create secondary indexes.</span></span> <span data-ttu-id="a3eb0-164">セカンダリ XML インデックスの種類を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-164">These are the types:</span></span>  
  
-   <span data-ttu-id="a3eb0-165">PATH セカンダリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-165">PATH secondary XML index</span></span>  
  
-   <span data-ttu-id="a3eb0-166">VALUE セカンダリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-166">VALUE secondary XML index</span></span>  
  
-   <span data-ttu-id="a3eb0-167">PROPERTY セカンダリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-167">PROPERTY secondary XML index</span></span>  
  
 <span data-ttu-id="a3eb0-168">次に、セカンダリ インデックスを 1 種類以上作成する場合のガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-168">Following are some guidelines for creating one or more secondary indexes:</span></span>  
  
-   <span data-ttu-id="a3eb0-169">ワークロードで XML 列にパス式が多用されている場合、PATH セカンダリ XML インデックスを作成するとワークロードを高速に処理できることがあります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-169">If your workload uses path expressions significantly on XML columns, the PATH secondary XML index is likely to speed up your workload.</span></span> <span data-ttu-id="a3eb0-170">一般的な例では、Transact-SQL の WHERE 句で XML 列に対し **exist()** メソッドが使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-170">The most common case is the use of the **exist()** method on XML columns in the WHERE clause of Transact-SQL.</span></span>  
  
-   <span data-ttu-id="a3eb0-171">パス式を使用して個々の XML インスタンスから複数の値を取得する場合、PROPERTY インデックスで各 XML インスタンス内のパスをクラスター化すると効果が得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-171">If your workload retrieves multiple values from individual XML instances by using path expressions, clustering paths within each XML instance in the PROPERTY index may be helpful.</span></span> <span data-ttu-id="a3eb0-172">このシナリオは、主キーの値がわかっていてオブジェクトのプロパティをフェッチするプロパティ バッグ シナリオで主に発生します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-172">This scenario typically occurs in a property bag scenario when properties of an object are fetched and its primary key value is known.</span></span>  
  
-   <span data-ttu-id="a3eb0-173">XML インスタンスの値を、要素名または属性名がわからないままクエリで取得する場合、VALUE インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-173">If your workload involves querying for values within XML instances without knowing the element or attribute names that contain those values, you may want to create the VALUE index.</span></span> <span data-ttu-id="a3eb0-174">//author[last-name="Howard"]\(\<author> 要素が階層のどのレベルにあってもよい) のように、descendant 軸を参照する場合がその典型です。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-174">This typically occurs with descendant axes lookups, such as //author[last-name="Howard"], where \<author> elements can occur at any level of the hierarchy.</span></span> <span data-ttu-id="a3eb0-175">また、ワイルドカードを使用するクエリ (いずれかの属性に値 "novel" が指定された \<book> 要素をクエリで検索する /book [@\* = "novel"] など) もこれに該当します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-175">It also occurs in wildcard queries, such as /book [@\* = "novel"], where the query looks for \<book> elements that have some attribute having the value "novel".</span></span>  
  
### <a name="path-secondary-xml-index"></a><span data-ttu-id="a3eb0-176">PATH セカンダリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-176">PATH Secondary XML Index</span></span>  
 <span data-ttu-id="a3eb0-177">クエリで `xml` 型列のパス式をよく指定している場合、PATH セカンダリ インデックスにより検索速度を向上できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-177">If your queries generally specify path expressions on `xml` type columns, a PATH secondary index may be able to speed up the search.</span></span> <span data-ttu-id="a3eb0-178">このトピックで既に説明したように、WHERE 句に **exist()** メソッドを指定するクエリを使用する場合には、プライマリ インデックスが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-178">As described earlier in this topic, the primary index is helpful when you have queries that specify **exist()** method in the WHERE clause.</span></span> <span data-ttu-id="a3eb0-179">PATH セカンダリ インデックスを追加することでも、そのようなクエリの検索パフォーマンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-179">If you add a PATH secondary index, you may also improve the search performance in such queries.</span></span>  
  
 <span data-ttu-id="a3eb0-180">プライマリ XML インデックスにより、XML バイナリ ラージ オブジェクトを実行時に細分化せずに済むようになりますが、パス式に基づくクエリのパフォーマンスが最適にならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-180">Although a primary XML index avoids having to shred the XML binary large objects at run time, it may not provide the best performance for queries based on path expressions.</span></span> <span data-ttu-id="a3eb0-181">XML バイナリ ラージ オブジェクトに対応するプライマリ XML インデックスのすべての行は大きな XML インスタンスに対して順番に検索されるので、検索速度が低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-181">Because all rows in the primary XML index corresponding to an XML binary large object are searched sequentially for large XML instances, the sequential search may be slow.</span></span> <span data-ttu-id="a3eb0-182">このような場合、プライマリ インデックスのパス値とノード値にセカンダリ インデックスを構築すると、インデックス検索の速度を大幅に向上できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-182">In this case, having a secondary index built on the path values and node values in the primary index can significantly speed up the index search.</span></span> <span data-ttu-id="a3eb0-183">PATH セカンダリ インデックスではパス値とノード値がキー列になり、パスの検索時により効率的にシークできるようになります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-183">In the PATH secondary index, the path and node values are key columns that allow for more efficient seeks when searching for paths.</span></span> <span data-ttu-id="a3eb0-184">クエリ オプティマイザーでは、次に示すような式に PATH インデックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-184">The query optimizer may use the PATH index for expressions such as those shown in the following:</span></span>  
  
-   <span data-ttu-id="a3eb0-185">`/root/Location` パスだけを指定しています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-185">`/root/Location` which specify only a path</span></span>  
  
 <span data-ttu-id="a3eb0-186">OR</span><span class="sxs-lookup"><span data-stu-id="a3eb0-186">OR</span></span>  
  
-   <span data-ttu-id="a3eb0-187">`/root/Location/@LocationID[.="10"]` パスとノード値の両方を指定しています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-187">`/root/Location/@LocationID[.="10"]` where both the path and the node value are specified.</span></span>  
  
 <span data-ttu-id="a3eb0-188">次のクエリでは、PATH インデックスが役立つケースを示します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-188">The following query shows where the PATH index is helpful:</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.query('  
  /PD:ProductDescription/PD:Summary  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist ('/PD:ProductDescription/@ProductModelID[.="19"]') = 1  
```  
  
 <span data-ttu-id="a3eb0-189">このクエリでは、 `/PD:ProductDescription/@ProductModelID` メソッド内のパス式 `"19"` と値 `exist()` が PATH インデックスのキー フィールドに対応しています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-189">In the query, the path expression `/PD:ProductDescription/@ProductModelID` and value `"19"` in the `exist()` method correspond to the key fields of the PATH index.</span></span> <span data-ttu-id="a3eb0-190">これにより、PATH インデックス内を直接シークできるようになり、プライマリ XML インデックスでパス値を順番に検索するよりも検索のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-190">This allows for direct seek in the PATH index and provides better search performance than the sequential search for path values in the primary index.</span></span>  
  
### <a name="value-secondary-xml-index"></a><span data-ttu-id="a3eb0-191">VALUE セカンダリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-191">VALUE Secondary XML Index</span></span>  
 <span data-ttu-id="a3eb0-192">`/Root/ProductDescription/@*[. = "Mountain Bike"]` や `//ProductDescription[@Name = "Mountain Bike"]`などのように、クエリが値に基づいており、パスが完全に指定されていない場合や、パスにワイルドカードが含まれている場合は、プライマリ XML インデックスのノード値にセカンダリ XML インデックスを構築すると、より迅速に結果を得られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-192">If queries are value based, for example, `/Root/ProductDescription/@*[. = "Mountain Bike"]` or `//ProductDescription[@Name = "Mountain Bike"]`, and the path is not fully specified or it includes a wildcard, you might obtain faster results by building a secondary XML index that is built on node values in the primary XML index.</span></span>  
  
 <span data-ttu-id="a3eb0-193">VALUE インデックスのキー列は、プライマリ XML インデックスの列 (ノード値とパス) です。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-193">The key columns of the VALUE index are (node value and path) of the primary XML index.</span></span> <span data-ttu-id="a3eb0-194">値を格納している要素名または属性名がわからない状態で XML インスタンスの値に対するクエリを実行する作業がワークロードに含まれている場合、VALUE インデックスが役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-194">If your workload involves querying for values from XML instances without knowing the element or attribute names that contain the values, a VALUE index may be useful.</span></span> <span data-ttu-id="a3eb0-195">たとえば、次の式は VALUE インデックスを使用すると効率的になります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-195">For example, the following expression will benefit from having a VALUE index:</span></span>  
  
-   <span data-ttu-id="a3eb0-196">`//author[LastName="someName"]`: <`LastName`> 要素の値はわかっていますが、親である <`author`> はどこにでも存在し得ます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-196">`//author[LastName="someName"]` where you know the value of the <`LastName`> element, but the <`author`> parent can occur anywhere.</span></span>  
  
-   <span data-ttu-id="a3eb0-197">`/book[@* = "someValue"]`: `"someValue"` という値の属性を持つ <`book`> 要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-197">`/book[@* = "someValue"]` where the query looks for the <`book`> element that has some attribute having the value `"someValue"`.</span></span>  
  
 <span data-ttu-id="a3eb0-198">次のクエリは、 `ContactID` テーブルから `Contact` を返します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-198">The following query returns `ContactID` from the `Contact` table.</span></span> <span data-ttu-id="a3eb0-199">句は、 `WHERE` 型の列の値を検索するフィルターを指定し `AdditionalContactInfo``xml` ます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-199">The `WHERE` clause specifies a filter that looks for values in the `AdditionalContactInfo``xml` type column.</span></span> <span data-ttu-id="a3eb0-200">連絡先 ID は、対応する追加の連絡先情報の XML バイナリ ラージ オブジェクトに特定の電話番号が含まれている場合にのみ返されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-200">The contact IDs are returned only if the corresponding additional contact information XML binary large object includes a specific telephone number.</span></span> <span data-ttu-id="a3eb0-201"><`telephoneNumber`> 要素は XML 内のどこにでも存在し得るので、パス式で descendent-or-self 軸を指定しています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-201">Because the <`telephoneNumber`> element may appear anywhere in the XML, the path expression specifies the descendent-or-self axis.</span></span>  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS CI,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.exist('//ACT:telephoneNumber/ACT:number[.="111-111-1111"]') = 1  
```  
  
 <span data-ttu-id="a3eb0-202">この場合、検索する <`number`> の値はわかっていますが、この値は <`telephoneNumber`> 要素の子として XML インスタンス内のどこにでも存在できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-202">In this situation, the search value for <`number`> is known, but it can appear anywhere in the XML instance as a child of the <`telephoneNumber`> element.</span></span> <span data-ttu-id="a3eb0-203">このようなクエリでは特定の値に基づいてインデックス参照を行うと、効率的になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-203">This kind of query might benefit from an index lookup based on a specific value.</span></span>  
  
### <a name="property-secondary-index"></a><span data-ttu-id="a3eb0-204">PROPERTY セカンダリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="a3eb0-204">PROPERTY Secondary Index</span></span>  
 <span data-ttu-id="a3eb0-205">個々の XML インスタンスから 1 つ以上の値を取得するクエリでは、PROPERTY インデックスを使用するとメリットが得られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-205">Queries that retrieve one or more values from individual XML instances might benefit from a PROPERTY index.</span></span> <span data-ttu-id="a3eb0-206">このシナリオは、型の**value ()** メソッドを使用してオブジェクトのプロパティを取得し、 `xml` オブジェクトの主キーの値がわかっている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-206">This scenario occurs when you retrieve object properties by using the **value()** method of the `xml` type and when the primary key value of the object is known.</span></span>  
  
 <span data-ttu-id="a3eb0-207">PROPERTY インデックスは、プライマリ XML インデックスの列 (PK、パス、およびノード値) について構築されます。PK はベース テーブルの主キーです。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-207">The PROPERTY index is built on columns (PK, Path and node value) of the primary XML index where PK is the primary key of the base table.</span></span>  
  
 <span data-ttu-id="a3eb0-208">たとえば、次のクエリでは、製品モデル `19`の `ProductModelID` 属性と `ProductModelName` 属性の値を `value()` メソッドを使用して取得しています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-208">For example, for product model `19`, the following query retrieves the `ProductModelID` and `ProductModelName` attribute values using the `value()` method.</span></span> <span data-ttu-id="a3eb0-209">プライマリ XML インデックスや他のセカンダリ XML インデックスではなく PROPERTY インデックスを使用すると、クエリをより迅速に実行できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-209">Instead of using the primary XML index or the other secondary XML indexes, the PROPERTY index may provide faster execution.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.value('(/PD:ProductDescription/@ProductModelID)[1]', 'int') as ModelID,  
       CatalogDescription.value('(/PD:ProductDescription/@ProductModelName)[1]', 'varchar(30)') as ModelName          
FROM Production.ProductModel     
WHERE ProductModelID = 19  
```  
  
 <span data-ttu-id="a3eb0-210">このトピックで後述する相違点を除いて、型の列に XML インデックスを作成 `xml` することは、非型列にインデックスを作成することと似てい `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-210">Except for the differences described later in this topic, creating an XML index on an`xml` type column is similar to creating an index on a non-`xml` type column.</span></span> <span data-ttu-id="a3eb0-211">XML インデックスの作成と管理には、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-211">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statements can be used to create and manage XML indexes:</span></span>  
  
-   [<span data-ttu-id="a3eb0-212">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3eb0-212">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [<span data-ttu-id="a3eb0-213">ALTER INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3eb0-213">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
-   [<span data-ttu-id="a3eb0-214">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3eb0-214">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
## <a name="getting-information-about-xml-indexes"></a><span data-ttu-id="a3eb0-215">XML インデックスに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="a3eb0-215">Getting Information about XML Indexes</span></span>  
 <span data-ttu-id="a3eb0-216">XML インデックス エントリは、カタログ ビュー sys.indexes にインデックスの "type" 3 として表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-216">XML index entries appear in the catalog view, sys.indexes, with the index "type" 3.</span></span> <span data-ttu-id="a3eb0-217">name 列には XML インデックスの名前が格納されています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-217">The name column contains the name of the XML index.</span></span>  
  
 <span data-ttu-id="a3eb0-218">XML インデックスはカタログ ビュー sys.xml_indexes にも記録されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-218">XML indexes are also recorded in the catalog view, sys.xml_indexes.</span></span> <span data-ttu-id="a3eb0-219">このビューには、sys.indexes のすべての列および XML インデックスに有用な特定の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-219">This contains all the columns of sys.indexes and some specific ones that are useful for XML indexes.</span></span> <span data-ttu-id="a3eb0-220">列 secondary_type に値 NULL がある場合はプライマリ XML インデックスであることを示します。セカンダリ XML インデックスの値 "P"、"R"、および "V" はそれぞれ PATH、PROPERTY、VALUE を示します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-220">The value NULL in the column, secondary_type, indicates a primary XML index; the values 'P', 'R' and 'V' stand for PATH, PROPERTY, and VALUE secondary XML indexes, respectively.</span></span>  
  
 <span data-ttu-id="a3eb0-221">XML インデックスによる領域の使用状況は、テーブル値関数 [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)でわかります。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-221">The space use of XML indexes can be found in the table-valued function [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span> <span data-ttu-id="a3eb0-222">この関数は、すべてのインデックスの種類について、占有しているディスク ページの数、バイト単位の平均行サイズ、レコードの数などの情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-222">It provides information, such as the number of disk pages occupied, average row size in bytes, and number of records, for all index types..</span></span> <span data-ttu-id="a3eb0-223">また、この情報には XML インデックスも含まれています。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-223">This also includes XML indexes.</span></span> <span data-ttu-id="a3eb0-224">この情報はデータベース パーティションごとに取得できます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-224">This information is available for each database partition.</span></span> <span data-ttu-id="a3eb0-225">どの XML インデックスにも同一の、ベース テーブルのパーティション構成とパーティション関数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3eb0-225">XML indexes use the same partitioning scheme and partitioning function of the base table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3eb0-226">参照</span><span class="sxs-lookup"><span data-stu-id="a3eb0-226">See Also</span></span>  
 <span data-ttu-id="a3eb0-227">[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a3eb0-227">[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) </span></span>  
 [<span data-ttu-id="a3eb0-228">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3eb0-228">XML Data &#40;SQL Server&#41;</span></span>](../xml/xml-data-sql-server.md)  
  
  
