---
title: 選択的 XML インデックス (SXI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 598ecdcd-084b-4032-81b2-eed6ae9f5d44
author: rothja
ms.author: jroth
ms.openlocfilehash: 37dd72c5de2892672dc9f63066075ab5e770d758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645416"
---
# <a name="selective-xml-indexes-sxi"></a><span data-ttu-id="bf1d7-102">選択的 XML インデックス (SXI)</span><span class="sxs-lookup"><span data-stu-id="bf1d7-102">Selective XML Indexes (SXI)</span></span>
  <span data-ttu-id="bf1d7-103">選択的 XML インデックスは、通常の XML インデックスに加えて使用できる、別の種類の XML インデックスです。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-103">Selective XML indexes are another type of XML index that is available to you in addition to ordinary XML indexes.</span></span> <span data-ttu-id="bf1d7-104">選択的 XML インデックス機能の目標を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-104">The goals of the selective XML index feature are the following:</span></span>  
  
-   <span data-ttu-id="bf1d7-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納された XML データに対するクエリのパフォーマンスを向上させる。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-105">To improve the performance of queries over XML data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="bf1d7-106">大規模な XML データのワークロードのより速いインデックス設定をサポートする。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-106">To support faster indexing of large XML data workloads.</span></span>  
  
-   <span data-ttu-id="bf1d7-107">XML インデックスのストレージ コストの削減によってスケーラビリティを向上させる。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-107">To improve scalability by reducing the storage costs of XML indexes.</span></span>  
  
 <span data-ttu-id="bf1d7-108">通常の XML インデックスの大きな限界は、XML ドキュメント全体にインデックスを設定することです。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-108">The main limitation with ordinary XML indexes is that they index the entire XML document.</span></span> <span data-ttu-id="bf1d7-109">このため、クエリのパフォーマンスの低下やインデックスのメンテナンス コストの増加などのさまざまな欠点が生じ、そのほとんどがインデックスのストレージ コストに関連しています。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-109">This leads to several significant drawbacks, such as decreased query performance and increased index maintenance cost, mostly related to the storage costs of the index.</span></span>  
  
 <span data-ttu-id="bf1d7-110">選択的 XML インデックス機能を使用して、XML ドキュメントの特定のパスをインデックスに昇格できます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-110">The selective XML index feature lets you promote only certain paths from the XML documents to index.</span></span> <span data-ttu-id="bf1d7-111">インデックスの作成時に、これらのパスが評価され、パスがポイントしているノードが細分化され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のリレーショナル テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-111">At index creation time, these paths are evaluated, and the nodes that they point to are shredded and stored inside a relational table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bf1d7-112">この機能は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Research と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 製品チームのコラボレーションによって開発された効率的なマッピング アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-112">This feature uses an efficient mapping algorithm developed by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Research in collaboration with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product team.</span></span> <span data-ttu-id="bf1d7-113">このアルゴリズムは、XML ノードを単一のリレーショナル テーブルにマップすることで、非常に高いパフォーマンスを実現しますが、ストレージ スペースは少ししか必要ありません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-113">This algorithm maps the XML nodes to a single relational table, and achieves exceptional performance while requiring only modest storage space.</span></span>  
  
 <span data-ttu-id="bf1d7-114">選択的 XML インデックス機能は、選択的 XML インデックスによってインデックス設定されているノードに対するセカンダリ選択的 XML インデックスもサポートします。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-114">The selective XML index feature also supports secondary selective XML indexes over nodes that have been indexed by a selective XML index.</span></span> <span data-ttu-id="bf1d7-115">これらのセカンダリ選択的インデックスは効率的であり、クエリのパフォーマンスがさらに向上します。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-115">These secondary selective indexes are efficient and further improve the performance of queries.</span></span>  
  
##  <a name="benefits-of-selective-xml-indexes"></a><a name="benefits"></a> <span data-ttu-id="bf1d7-116">選択的 XML インデックスの利点</span><span class="sxs-lookup"><span data-stu-id="bf1d7-116">Benefits of Selective XML Indexes</span></span>  
 <span data-ttu-id="bf1d7-117">選択的 XML インデックスには、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-117">Selective XML indexes provide the following benefits:</span></span>  
  
1.  <span data-ttu-id="bf1d7-118">一般的なクエリのロードでの XML データ型に対するクエリのパフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-118">Greatly improved query performance over the XML data type for typical query loads.</span></span>  
  
2.  <span data-ttu-id="bf1d7-119">通常の XML インデックスよりストレージ要件が小さくなります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-119">Reduced storage requirements compared to ordinary XML indexes.</span></span>  
  
3.  <span data-ttu-id="bf1d7-120">通常の XML インデックスより、インデックスのメンテナンス コストが削減されます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-120">Reduced index maintenance costs compared to ordinary XML indexes.</span></span>  
  
4.  <span data-ttu-id="bf1d7-121">選択的 XML インデックスを使用するためにアプリケーションを更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-121">No need to update applications to benefit from selective XML indexes.</span></span>  
  

  
##  <a name="selective-xml-indexes-and-primary-xml-indexes"></a><a name="compare"></a> <span data-ttu-id="bf1d7-122">選択的 XML インデックスとプライマリ XML インデックス</span><span class="sxs-lookup"><span data-stu-id="bf1d7-122">Selective XML Indexes and Primary XML Indexes</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bf1d7-123">ほとんどの場合、通常の XML インデックスではなく選択的 XML インデックスを作成すると、パフォーマンスが向上し、効率的な保管が可能になります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-123">Create a selective XML index instead of an ordinary XML index in most cases for better performance and more efficient storage.</span></span>  
  
 <span data-ttu-id="bf1d7-124">ただし、選択的 XML インデックスは、次の条件のいずれかに該当する場合はお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-124">However, a selective XML index is not recommended when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="bf1d7-125">大量のノード パスをマップする。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-125">You map a large number of node paths.</span></span>  
  
-   <span data-ttu-id="bf1d7-126">ドキュメント構造内の不明な要素または不明な位置にある要素のクエリをサポートする。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-126">You support queries for unknown elements or elements in an unknown location in the document structure.</span></span>  
  

  
##  <a name="simple-example-of-a-selective-xml-index"></a><a name="example"></a> <span data-ttu-id="bf1d7-127">選択的 XML インデックスの単純な例</span><span class="sxs-lookup"><span data-stu-id="bf1d7-127">Simple Example of a Selective XML Index</span></span>  
 <span data-ttu-id="bf1d7-128">次の XML フラグメントを、約 500,000 行ある表形式の XML ドキュメントと考えてください。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-128">Consider the following XML fragment as an XML document in a table of approximately 500,000 rows:</span></span>  
  
```xml  
<book>  
    <created>2004-03-01</created>   
    <authors>Various</authors>  
    <subjects>  
        <subject>English wit and humor -- Periodicals</subject>  
        <subject>AP</subject>   
    </subjects>  
    <title>Punch, or the London Charivari, Volume 156, April 2, 1919</title>  
    <id>etext11617</id>  
</book>  
```  
  
 <span data-ttu-id="bf1d7-129">この単純なスキーマのそれほど多くの行に対するプライマリ XML インデックスの作成には、長い時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-129">Creating a primary XML index over so many rows of this simple schema takes a long time.</span></span> <span data-ttu-id="bf1d7-130">このデータのクエリも、プライマリ XML インデックスが選択的インデックスをサポートしていないため、同じように時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-130">Querying this data also suffers from the fact that a primary XML index does not support selective indexing.</span></span>  
  
 <span data-ttu-id="bf1d7-131">`/book/title` パスと `/book/subjects` パスのデータのみをクエリする必要がある場合は、次の選択的 XML インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-131">If you only need to query this data over the `/book/title` path and the `/book/subjects` path, you can create the following selective XML index:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX SXI_index  
ON Tbl(xmlcol)  
FOR   
(  
    pathTitle = '/book/title/text()' AS XQUERY 'xs:string',   
    pathAuthors = '/book/authors' AS XQUERY 'node()',  
    pathId = '/book/id' AS SQL NVARCHAR(100)  
)  
```  
  
 <span data-ttu-id="bf1d7-132">上に示したステートメントは、選択的 XML インデックスを作成するときに使用する CREATE 構文の好例です。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-132">The preceding statement is a good example of the CREATE syntax that you use when you create a selective XML index.</span></span> <span data-ttu-id="bf1d7-133">この CREATE ステートメントでは、インデックスの名前を指定した後、インデックスを設定するテーブルと XML 列を識別します。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-133">In the CREATE statement, first you provide a name for the index and identify the table and the XML column to index.</span></span> <span data-ttu-id="bf1d7-134">その後、インデックスのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-134">Then you provide the paths to index.</span></span> <span data-ttu-id="bf1d7-135">パスには、次の 3 つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-135">A path has three parts:</span></span>  
  
1.  <span data-ttu-id="bf1d7-136">パスを一意に識別する名前。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-136">A name that uniquely identifies the path.</span></span>  
  
2.  <span data-ttu-id="bf1d7-137">パスを記述する XQuery 式。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-137">An XQuery expression that describes the path.</span></span>  
  
3.  <span data-ttu-id="bf1d7-138">省略可能な最適化ヒント。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-138">Optional optimization hints.</span></span>  
  
 <span data-ttu-id="bf1d7-139">これらの要素の詳細については、「 [関連タスク](#reltasks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-139">For more information about these elements, see [Related Tasks](#reltasks).</span></span>  
  

  
## <a name="supported-features-prerequisites-and-limitations"></a><span data-ttu-id="bf1d7-140">サポートされる機能、前提条件、および制限事項</span><span class="sxs-lookup"><span data-stu-id="bf1d7-140">Supported Features, Prerequisites, and Limitations</span></span>  
  
###  <a name="supported-xml-features"></a><a name="features"></a> <span data-ttu-id="bf1d7-141">サポートされる XML 機能</span><span class="sxs-lookup"><span data-stu-id="bf1d7-141">Supported XML Features</span></span>  
 <span data-ttu-id="bf1d7-142">選択的 XML インデックスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって exist()、value()、および nodes() メソッドの中でサポートされる XQuery をサポートします。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-142">Selective XML indexes support the XQuery supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inside the exist(), value() and nodes() methods.</span></span>  
  
-   <span data-ttu-id="bf1d7-143">exist()、value()、および nodes() メソッドでは、式全体を変換するための十分な情報が選択的 XML インデックスに含まれます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-143">For the exist(), value() and nodes() methods, selective XML indexes contain enough information to transform the entire expression.</span></span>  
  
-   <span data-ttu-id="bf1d7-144">query() メソッドと modify() メソッドでは、選択的 XML インデックスは、ノードのフィルター処理でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-144">For the query() and modify() methods, selective XML indexes may be used for node filtering only.</span></span>  
  
-   <span data-ttu-id="bf1d7-145">query() メソッドでは、選択的 XML インデックスを使用して結果を取得することはありません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-145">For the query() method, selective XML indexes are not used to retrieve results.</span></span>  
  
-   <span data-ttu-id="bf1d7-146">modify() メソッドでは、選択的 XML インデックスを使用して XML ドキュメントを更新することはありません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-146">For the modify() method, selective XML indexes are not used to update XML documents.</span></span>  
  

  
###  <a name="unsupported-xml-features"></a><a name="unsupported"></a> <span data-ttu-id="bf1d7-147">サポートされない XML 機能</span><span class="sxs-lookup"><span data-stu-id="bf1d7-147">Unsupported XML Features</span></span>  
 <span data-ttu-id="bf1d7-148">選択的 XML インデックスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の XML の実装でサポートされている次の機能はサポートしません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-148">Selective XML indexes do not support the following features that are supported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementation of XML:</span></span>  
  
-   <span data-ttu-id="bf1d7-149">complex XS 型 (union 型、sequence 型、および list 型) のノードに対するインデックス設定。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-149">Indexing of nodes with complex XS types: union types, sequence types, and list types.</span></span>  
  
-   <span data-ttu-id="bf1d7-150">バイナリ XS 型 (base64Binary や hexBinary など) のノードに対するインデックス設定。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-150">Indexing of nodes with binary XS types: for example, base64Binary and hexBinary.</span></span>  
  
-   <span data-ttu-id="bf1d7-151">末尾にワイルドカード文字 `*` を含む XPath 式を使用した、インデックスを設定するノードの指定。例: `/a/b/c/*`、`/a//b/*`、`/a/b/*:c`。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-151">Specifying the nodes to index with XPath expressions that contain the wildcard character `*` at the end: For example,  `/a/b/c/*`, `/a//b/*`, or `/a/b/*:c`.</span></span>  
  
-   <span data-ttu-id="bf1d7-152">子、属性、または子孫以外の軸に対するインデックスの設定。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-152">Indexing any axis other than child, attribute, or descendant.</span></span> <span data-ttu-id="bf1d7-153">`//<step>` は特殊なケースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-153">The `//<step>` case is allowed as a special case.</span></span>  
  
-   <span data-ttu-id="bf1d7-154">XML 処理命令とコメントに対するインデックスの設定。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-154">Indexing of XML processing instructions and comments.</span></span>  
  
-   <span data-ttu-id="bf1d7-155">id() 関数の使用によるノードの識別子の指定と取得。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-155">Specifying and retrieving the identifier for a node by using the id() function.</span></span>  
  

  
###  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="bf1d7-156">前提条件</span><span class="sxs-lookup"><span data-stu-id="bf1d7-156">Prerequisites</span></span>  
 <span data-ttu-id="bf1d7-157">ユーザー テーブルの XML 列に対して選択的 XML インデックスを作成する前に、次の前提条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-157">The following prerequisites must exist before you can create a selective XML index over an XML column in a user table:</span></span>  
  
-   <span data-ttu-id="bf1d7-158">クラスター化インデックスは、ユーザー テーブルの主キー上に存在する必要がある。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-158">A clustered index must exist on the primary key of the user table.</span></span>  
  
-   <span data-ttu-id="bf1d7-159">選択的 XML インデックスで使用する場合、ユーザー テーブルのプライマリ キーのサイズは 128 バイトに制限されます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-159">The primary key of the user table is limited to a size of 128 bytes when used with selective XML indexes.</span></span>  
  
-   <span data-ttu-id="bf1d7-160">選択的 XML インデックスで使用する場合、ユーザー テーブルのクラスター化キーのサイズは 15 バイトに制限されます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-160">The clustering key of the user table is limited to 15 columns when used with selective XML indexes.</span></span>  
  

  
###  <a name="limitations"></a><a name="limits"></a> <span data-ttu-id="bf1d7-161">制限事項</span><span class="sxs-lookup"><span data-stu-id="bf1d7-161">Limitations</span></span>  
 <span data-ttu-id="bf1d7-162">**一般的な要件と制限事項**</span><span class="sxs-lookup"><span data-stu-id="bf1d7-162">**General requirements and limitations**</span></span>  
  
-   <span data-ttu-id="bf1d7-163">各選択的 XML インデックスは、単一の XML 列にのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-163">Each selective XML index can only be created on a single XML column.</span></span>  
  
-   <span data-ttu-id="bf1d7-164">選択的 XML インデックスは、XML 以外の列には作成できません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-164">You cannot create a selective XML index on a non-XML column.</span></span>  
  
-   <span data-ttu-id="bf1d7-165">テーブルの各 XML 列には、選択的 XML インデックスを 1 つだけ作成できます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-165">Each XML column in a table can have only one selective XML index.</span></span>  
  
-   <span data-ttu-id="bf1d7-166">各テーブルには、最大 249 の選択的 XML インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-166">Each table can have up to 249 selective XML indexes.</span></span>  
  
 <span data-ttu-id="bf1d7-167">**サポートされるオブジェクトに関する制限事項**</span><span class="sxs-lookup"><span data-stu-id="bf1d7-167">**Limitations on supported objects**</span></span>  
  
 <span data-ttu-id="bf1d7-168">選択的 XML インデックスは、次のオブジェクトには作成できません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-168">You cannot create selective XML indexes on the following objects:</span></span>  
  
1.  <span data-ttu-id="bf1d7-169">ビューの XML 列。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-169">XML columns in a view.</span></span>  
  
2.  <span data-ttu-id="bf1d7-170">XML 列を含むテーブル値変数。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-170">Table-valued variable with XML columns.</span></span>  
  
3.  <span data-ttu-id="bf1d7-171">XML 型の変数。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-171">XML type variables.</span></span>  
  
4.  <span data-ttu-id="bf1d7-172">XML の計算列。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-172">Computed XML columns.</span></span>  
  
5.  <span data-ttu-id="bf1d7-173">ノードの入れ子の深さが 128 を超えている XML 列。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-173">XML columns with a depth of more than 128 nested nodes.</span></span>  
  
 <span data-ttu-id="bf1d7-174">**ストレージに関する制限事項**</span><span class="sxs-lookup"><span data-stu-id="bf1d7-174">**Limitations related to storage**</span></span>  
  
 <span data-ttu-id="bf1d7-175">インデックスに追加できる XML ドキュメントのノード数は有限です。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-175">There is a finite limit on the number of nodes from the XML document that can be added to the index.</span></span> <span data-ttu-id="bf1d7-176">選択的 XML インデックスは、XML ドキュメントを単一のリレーショナル テーブルにマップします。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-176">A selective XML index maps XML documents to a single relational table.</span></span> <span data-ttu-id="bf1d7-177">したがって、テーブルの特定の行には、1024 を超える NULL 以外の列が存在することはできません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-177">Therefore it cannot have more than 1024 non-null columns in any given row of the table.</span></span> <span data-ttu-id="bf1d7-178">さらに、選択的 XML インデックスはスパース列をストレージ用に使用するため、スパース列に関する制限事項の多くがこのインデックスにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-178">Furthermore, many of the limitations of sparse columns also apply to selective XML indexes, because the indexes use sparse columns for storage.</span></span>  
  
 <span data-ttu-id="bf1d7-179">特定の行でサポートされる NULL 以外の列の最大数は、列内のデータのサイズによって決まります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-179">The maximum number of non-null columns supported in any given row depends on the size of the data in the columns:</span></span>  
  
-   <span data-ttu-id="bf1d7-180">最良の場合、すべての列の型が **bit**のとき、1024 の NULL 以外の列がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-180">In the best case, 1024 non-null columns are supported when all columns are of type **bit**.</span></span>  
  
-   <span data-ttu-id="bf1d7-181">最悪の場合、すべての列が **varchar**型のラージ オブジェクトのとき、236 の NULL 以外の列のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-181">In the worst case, only 236 non-null columns are supported when all columns are large objects of type **varchar**.</span></span>  
  
 <span data-ttu-id="bf1d7-182">選択的 XML インデックスは、インデックスが設定されているすべてのノード パスに対して、内部的に 1 列から 4 列を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-182">Selective XML indexes use from one to four columns internally for every node path that is indexed.</span></span> <span data-ttu-id="bf1d7-183">インデックスを設定できるノードの総数は、インデックス付きパス内のデータの実際のサイズに応じて、60 から数千になります。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-183">The total number of nodes that can be indexed ranges from 60 to several hundred nodes, depending on the actual size of the data in the indexed paths.</span></span>  
  
-   <span data-ttu-id="bf1d7-184">最悪の場合、ノード パス定義内の `//` を使用して一部のノードまたはすべてのノードがマップされるとき、インデックス付きノードの最大数は 60 です。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-184">In the worst case, when some or all nodes are mapped using `//` in the node path definition, the maximum number of indexed nodes is 60.</span></span>  
  
-   <span data-ttu-id="bf1d7-185">最良の場合、ノード パス定義内の `//` を使用しないで一部のノードまたはすべてのノードがマップされるとき、インデックス付きノードの最大数は 200 です。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-185">In the best case, when nodes are mapped without using `//` in the node path definition, the maximum number of indexed nodes is 200.</span></span>  
  
 <span data-ttu-id="bf1d7-186">**選択的 XML インデックスは、インデックスの CREATE または ALTER 時に再構築されます。**</span><span class="sxs-lookup"><span data-stu-id="bf1d7-186">**Selective XML indexes are rebuilt when you CREATE or ALTER the index.**</span></span>  
  
 <span data-ttu-id="bf1d7-187">選択的 XML インデックスを CREATE または ALTER すると、シングル スレッドのオフライン モードで再構築されます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-187">When you CREATE or ALTER a selective XML index, it is rebuilt in a single-threaded, offline mode.</span></span> <span data-ttu-id="bf1d7-188">ALTER ステートメントの頻繁な使用は、インデックス付き XML ドキュメントに対するクエリのパフォーマンスに悪影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-188">Frequently ALTER statements negatively affect the performance of queries over the indexed XML documents.</span></span>  
  
 <span data-ttu-id="bf1d7-189">**その他の制限事項**</span><span class="sxs-lookup"><span data-stu-id="bf1d7-189">**Other limitations**</span></span>  
  
-   <span data-ttu-id="bf1d7-190">選択的 XML インデックスは、クエリ ヒントではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-190">Selective XML indexes are not supported in query hints.</span></span>  
  
-   <span data-ttu-id="bf1d7-191">選択的 XML インデックスとセカンダリ選択的 XML インデックスは、データベース チューニング アドバイザーではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-191">Selective XML indexes and secondary selective XML indexes are not supported in Database Tuning Advisor.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="bf1d7-192">関連タスク</span><span class="sxs-lookup"><span data-stu-id="bf1d7-192">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf1d7-193">**タスク**</span><span class="sxs-lookup"><span data-stu-id="bf1d7-193">**Task**</span></span>|<span data-ttu-id="bf1d7-194">**トピック**</span><span class="sxs-lookup"><span data-stu-id="bf1d7-194">**Topic**</span></span>|  
|<span data-ttu-id="bf1d7-195">選択的 XML インデックスを作成または変更するときに、インデックスを設定するノード パスと省略可能な最適化ヒントを指定する。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-195">Specify the node paths that you want to index and optional optimization hints when you create or alter a selective XML index.</span></span>|[<span data-ttu-id="bf1d7-196">選択的 XML インデックスのパスと最適化ヒントの指定</span><span class="sxs-lookup"><span data-stu-id="bf1d7-196">Specify Paths and Optimization Hints for Selective XML Indexes</span></span>](specify-paths-and-optimization-hints-for-selective-xml-indexes.md)|  
|<span data-ttu-id="bf1d7-197">選択的 XML インデックスを作成、変更、または削除する。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-197">Create, alter, or drop a selective XML index.</span></span>|[<span data-ttu-id="bf1d7-198">選択的 XML インデックスの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="bf1d7-198">Create, Alter, and Drop Selective XML Indexes</span></span>](create-alter-and-drop-selective-xml-indexes.md)|  
|<span data-ttu-id="bf1d7-199">セカンダリ選択的 XML インデックスを作成、変更、または削除する。</span><span class="sxs-lookup"><span data-stu-id="bf1d7-199">Create, alter, or drop a secondary selective XML index.</span></span>|[<span data-ttu-id="bf1d7-200">選択的セカンダリ XML インデックスの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="bf1d7-200">Create, Alter, and Drop Secondary Selective XML Indexes</span></span>](create-alter-and-drop-secondary-selective-xml-indexes.md)|  
  

  
  
