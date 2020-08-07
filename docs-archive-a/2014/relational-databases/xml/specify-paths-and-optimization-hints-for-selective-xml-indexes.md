---
title: 選択的 XML インデックスのパスと最適化ヒントの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 486ee339-165b-4aeb-b760-d2ba023d7d0a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a9d683fe57d489fdb9922b53d2c5c6825835216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719737"
---
# <a name="specify-paths-and-optimization-hints-for-selective-xml-indexes"></a><span data-ttu-id="61b96-102">選択的 XML インデックスのパスと最適化ヒントの指定</span><span class="sxs-lookup"><span data-stu-id="61b96-102">Specify Paths and Optimization Hints for Selective XML Indexes</span></span>
  <span data-ttu-id="61b96-103">このトピックでは、選択的な XML インデックスを作成または変更するときに、インデックス設定用のインデックス ヒントと最適化ヒントへのノード パスを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="61b96-103">This topic describes how to specify node paths to index and optimization hints for indexing when you create or alter selective XML indexes.</span></span>  
  
 <span data-ttu-id="61b96-104">ノード パスと最適化ヒントは、次のいずれかのステートメントで同時に指定します。</span><span class="sxs-lookup"><span data-stu-id="61b96-104">You specify node paths and optimization hints at the same time in one of the following statements:</span></span>  
  
-   <span data-ttu-id="61b96-105">**CREATE** ステートメントの **FOR** 句の中。</span><span class="sxs-lookup"><span data-stu-id="61b96-105">In the **FOR** clause of a **CREATE** statement.</span></span> <span data-ttu-id="61b96-106">詳細については、「[CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61b96-106">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
-   <span data-ttu-id="61b96-107">**ALTER** ステートメントの **ADD** 句の中。</span><span class="sxs-lookup"><span data-stu-id="61b96-107">In the **ADD** clause of an **ALTER** statement.</span></span> <span data-ttu-id="61b96-108">詳細については、「[ALTER INDEX &#40;選択的 XML インデックス&#41;](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61b96-108">For more information, see [ALTER INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="61b96-109">選択的 XML インデックスの詳細については、「 [選択的 XML インデックス &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61b96-109">For more information about selective XML indexes, see [Selective XML Indexes &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md).</span></span>  
  
##  <a name="understanding-xquery-and-sql-server-types-in-untyped-xml"></a><a name="untyped"></a> <span data-ttu-id="61b96-110">型指定されていない XML での XQuery 型と SQL Server 型について</span><span class="sxs-lookup"><span data-stu-id="61b96-110">Understanding XQuery and SQL Server Types in Untyped XML</span></span>  
 <span data-ttu-id="61b96-111">選択的 XML インデックスは、XQuery 型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型という 2 つの型システムをサポートします。</span><span class="sxs-lookup"><span data-stu-id="61b96-111">Selective XML indexes support two type systems: XQuery types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="61b96-112">インデックスを設定するパスを使用して、XQuery 式、または XML データ型の value() メソッドの戻り値の型のいずれかと一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="61b96-112">The indexed path can be used either to match an XQuery expression, or to match the return type of the value() method of the XML data type.</span></span>  
  
-   <span data-ttu-id="61b96-113">インデックスを設定するパスに注釈が設定されていない場合、または XQUERY キーワードを使用して注釈が設定されている場合、パスは XQuery 式と一致します。</span><span class="sxs-lookup"><span data-stu-id="61b96-113">When a path to index is not annotated, or is annotated with the XQUERY keyword, the path matches an XQuery expression.</span></span> <span data-ttu-id="61b96-114">XQUERY 注釈付きノード パスには 2 種類のバリエーションがあります。</span><span class="sxs-lookup"><span data-stu-id="61b96-114">There are two variations for XQUERY-annotated node paths:</span></span>  
  
    -   <span data-ttu-id="61b96-115">XQUERY キーワードと XQuery データ型を指定しない場合は、既定のマッピングが使用されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-115">If you do not specify the XQUERY keyword and the XQuery data type, then default mappings are used.</span></span> <span data-ttu-id="61b96-116">通常、ストレージとパフォーマンスは最適ではありません。</span><span class="sxs-lookup"><span data-stu-id="61b96-116">Typically performance and storage are not optimal.</span></span>  
  
    -   <span data-ttu-id="61b96-117">XQUERY キーワード、XQuery データ型、および他の最適化ヒント (省略可能) を指定すると、パフォーマンスと効率を最大限に高めたストレージを実現できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-117">If you specify the XQUERY keyword and the XQuery data type, and optionally other optimization hints, then you can achieve the best possible performance and the most efficient possible storage.</span></span> <span data-ttu-id="61b96-118">ただし、キャストが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="61b96-118">However, a cast can fail.</span></span>  
  
-   <span data-ttu-id="61b96-119">インデックスを設定するパスに SQL キーワードによる注釈が設定されている場合、パスは XML データ型の value() メソッドの戻り値の型と一致します。</span><span class="sxs-lookup"><span data-stu-id="61b96-119">When a path to index is annotated with the SQL keyword, the path matches the return type of the value() method of the XML data type.</span></span> <span data-ttu-id="61b96-120">適切な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定します。これは value() メソッドから戻ることが想定される戻り値の型です。</span><span class="sxs-lookup"><span data-stu-id="61b96-120">Specify the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, which is the return type that you expect from the value() method.</span></span>  
  
 <span data-ttu-id="61b96-121">XQuery 式の XML 型システムと XML データ型の value() メソッドに適用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型システムには、多少の違いがあります。</span><span class="sxs-lookup"><span data-stu-id="61b96-121">There are subtle differences between the XQuery expressions XML type system and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type system applied to the value() method of the XML data type.</span></span> <span data-ttu-id="61b96-122">これらの違いを次に示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-122">These differences include the following:</span></span>  
  
-   <span data-ttu-id="61b96-123">XQuery 型システムは、末尾の空白を認識します。</span><span class="sxs-lookup"><span data-stu-id="61b96-123">The XQuery type system is aware of trailing spaces.</span></span> <span data-ttu-id="61b96-124">たとえば、文字列 "abc" と "abc " は、XQuery 型セマンティックでは等しくありませんが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれらの文字列は等しくなります。</span><span class="sxs-lookup"><span data-stu-id="61b96-124">For example, according to XQuery type semantics, the strings "abc" and "abc " are not equal, while in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] these strings are equal.</span></span>  
  
-   <span data-ttu-id="61b96-125">XQuery の浮動小数点データ型は、+/- ゼロと +/- 無限大という特殊な値をサポートします。</span><span class="sxs-lookup"><span data-stu-id="61b96-125">XQuery floating point data types support special values of +/- zero and +/- infinity.</span></span> <span data-ttu-id="61b96-126">これらの特殊な値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の浮動小数点データ型ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="61b96-126">These special values are not supported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] floating point data types.</span></span>  
  
### <a name="xquery-types-in-untyped-xml"></a><span data-ttu-id="61b96-127">型指定されていない XML での XQuery 型</span><span class="sxs-lookup"><span data-stu-id="61b96-127">XQuery Types in Untyped XML</span></span>  
  
-   <span data-ttu-id="61b96-128">XQuery 型は、すべての XML データ型の value() メソッドを含むすべてのメソッド内の XQuery 式と一致します。</span><span class="sxs-lookup"><span data-stu-id="61b96-128">XQuery types match XQuery expressions in all methods of the XML data type including the value() method.</span></span>  
  
-   <span data-ttu-id="61b96-129">XQuery 型は、次の最適化ヒントをサポートします: ()、SINGLETON、DATA TYPE、および MAXLENGTH。</span><span class="sxs-lookup"><span data-stu-id="61b96-129">XQuery types support these optimization hints: node(), SINGLETON, DATA TYPE, and MAXLENGTH.</span></span>  
  
 <span data-ttu-id="61b96-130">型指定されていない XML に対する XQuery 式では、2 つの操作モードから選択できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-130">For XQuery expressions over untyped XML, you can choose between two modes of operation:</span></span>  
  
-   <span data-ttu-id="61b96-131">**既定のマッピング モード**。</span><span class="sxs-lookup"><span data-stu-id="61b96-131">**Default mapping mode**.</span></span> <span data-ttu-id="61b96-132">このモードでは、選択的 XML インデックスの作成時にパスのみを指定します。</span><span class="sxs-lookup"><span data-stu-id="61b96-132">In this mode, you specify only the path when creating a selective XML index.</span></span>  
  
-   <span data-ttu-id="61b96-133">**ユーザー指定のマッピング モード**。</span><span class="sxs-lookup"><span data-stu-id="61b96-133">**User-specified mapping mode**.</span></span> <span data-ttu-id="61b96-134">このモードでは、パスと省略可能な最適化ヒントの両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="61b96-134">In this mode, you specify both the path and optional optimization hints.</span></span>  
  
 <span data-ttu-id="61b96-135">既定のマッピング モードは、常に安全で一般的なストレージ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="61b96-135">The default mapping mode uses a conservative storage option which is always safe and general.</span></span> <span data-ttu-id="61b96-136">任意の型の式と一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="61b96-136">It can match any expression type.</span></span> <span data-ttu-id="61b96-137">既定のマッピング モードの限界は、最適化されたパフォーマンスよりも小さくなります。これは、実行時に多数のキャストが必要であり、セカンダリ インデックスを使用できないためです。</span><span class="sxs-lookup"><span data-stu-id="61b96-137">A limitation of the default mapping mode is less than optimal performance, because an increased number of runtime casts are required, and secondary indexes are not available.</span></span>  
  
 <span data-ttu-id="61b96-138">既定のマッピングで作成される選択的 XML インデックスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-138">Here is an example of a selective XML index created with default mappings.</span></span> <span data-ttu-id="61b96-139">3 つのパスのすべてで、既定のノード型 (**xs:untypedAtomic**) とカーディナリティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-139">For all three paths, the default node type (**xs:untypedAtomic**) and cardinality are used.</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_UX_default  
ON Tbl(xmlcol)  
FOR  
(  
mypath01 =  '/a/b',  
mypath02 = '/a/b/c',  
mypath03 = '/a/b/d'  
)  
```  
  
 <span data-ttu-id="61b96-140">ユーザー指定のマッピング モードでは、ノードの型とカーディナリティを指定することで、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="61b96-140">The user-specified mapping mode lets you specify a type and cardinality for the node to obtain better performance.</span></span> <span data-ttu-id="61b96-141">ただし、このパフォーマンスの向上は、安全性の放棄 (キャストが失敗する可能性があります) と汎用性の放棄 (指定した型のみが選択的 XML インデックスと一致します) によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-141">However, this improved performance is achieved by giving up safety - because a cast can fail - and generality - because only the specified type is matched with the selective XML index.</span></span>  
  
 <span data-ttu-id="61b96-142">型指定されていない XML でサポートされる XQuery の型を次に示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-142">The XQuery types supported for untyped XML case are:</span></span>  
  
-   <span data-ttu-id="61b96-143">**xs:boolean**</span><span class="sxs-lookup"><span data-stu-id="61b96-143">**xs:boolean**</span></span>  
  
-   <span data-ttu-id="61b96-144">**xs:double**</span><span class="sxs-lookup"><span data-stu-id="61b96-144">**xs:double**</span></span>  
  
-   <span data-ttu-id="61b96-145">**xs:string**</span><span class="sxs-lookup"><span data-stu-id="61b96-145">**xs:string**</span></span>  
  
-   <span data-ttu-id="61b96-146">**xs:date**</span><span class="sxs-lookup"><span data-stu-id="61b96-146">**xs:date**</span></span>  
  
-   <span data-ttu-id="61b96-147">**xs:time**</span><span class="sxs-lookup"><span data-stu-id="61b96-147">**xs:time**</span></span>  
  
-   <span data-ttu-id="61b96-148">**xs:dateTime**</span><span class="sxs-lookup"><span data-stu-id="61b96-148">**xs:dateTime**</span></span>  
  
 <span data-ttu-id="61b96-149">型が指定されていない場合、ノードは **xs:untypedAtomic** データ型と見なされます。</span><span class="sxs-lookup"><span data-stu-id="61b96-149">If the type is not specified, the node is assumed to be of the **xs:untypedAtomic** data type.</span></span>  
  
 <span data-ttu-id="61b96-150">選択的 XML インデックスは、次に示す方法で最適化できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-150">You can optimize the selective XML index shown in the following manner:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_UX_optimized  
ON Tbl(xmlcol)  
FOR  
(  
mypath= '/a/b' as XQUERY 'node()',  
pathX = '/a/b/c' as XQUERY 'xs:double' SINGLETON,  
pathY = '/a/b/d' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
)  
-- mypath - Only the node value is needed; storage is saved.  
-- pathX - Performance is improved; secondary indexes are possible.  
-- pathY - Performance is improved; secondary indexes are possible; storage is saved.  
```  
  
### <a name="sql-server-types-in-untyped-xml"></a><span data-ttu-id="61b96-151">型指定されていない XML での SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="61b96-151">SQL Server Types in Untyped XML</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="61b96-152">型は、value() メソッドの戻り値の型と一致します。</span><span class="sxs-lookup"><span data-stu-id="61b96-152">types match the return value of the value() method.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="61b96-153">型は、次の最適化ヒントをサポートします: SINGLETON。</span><span class="sxs-lookup"><span data-stu-id="61b96-153">types support this optimization hint: SINGLETON.</span></span>  
  
 <span data-ttu-id="61b96-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型を返すパスでは、型を必ず指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61b96-154">Specifying a type is mandatory for paths that return [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="61b96-155">value() メソッドで使用するものと同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="61b96-155">Use the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type that you would use in the value() method.</span></span>  
  
 <span data-ttu-id="61b96-156">次のクエリを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="61b96-156">Consider the following query:</span></span>  
  
```sql  
SELECT T.record,  
    T.xmldata.value('(/a/b/d)[1]', 'NVARCHAR(200)')  
FROM myXMLTable T  
```  
  
 <span data-ttu-id="61b96-157">指定されたクエリは、NVARCHAR(200) データ型にパックされたパス `/a/b/d` の値を返すため、ノード用に指定するデータ型は明白です。</span><span class="sxs-lookup"><span data-stu-id="61b96-157">The specified query returns a value from the path `/a/b/d` packed into an NVARCHAR(200) data type, so the data type to specify for the node is obvious.</span></span> <span data-ttu-id="61b96-158">ただし、ノードのカーディナリティを型指定されていない XML で指定するスキーマはありません。</span><span class="sxs-lookup"><span data-stu-id="61b96-158">However there is no schema to specify the cardinality of the node in untyped XML.</span></span> <span data-ttu-id="61b96-159">ノード `d` を親ノード `b`の下に最大で 1 つ表示するには、次に示すように、SINGLETON 最適化ヒントを使用する XML インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="61b96-159">To specify that node `d` appears at most once under its parent node `b`, create a selective XML index that uses the SINGLETON optimization hint as follows:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_US  
ON Tbl(xmlcol)  
FOR  
(  
node1223 = '/a/b/d' as SQL NVARCHAR(200) SINGLETON  
)  
```  
  

  
##  <a name="understanding-selective-xml-index-support-for-typed-xml"></a><a name="typed"></a> <span data-ttu-id="61b96-160">型指定された XML に対する選択的 XML インデックスのサポートについて</span><span class="sxs-lookup"><span data-stu-id="61b96-160">Understanding Selective XML Index support for typed XML</span></span>  
 <span data-ttu-id="61b96-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の型指定された XML は、特定の XML ドキュメントに関連付けられたスキーマです。</span><span class="sxs-lookup"><span data-stu-id="61b96-161">Typed XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is a schema associated with a given XML document.</span></span> <span data-ttu-id="61b96-162">このスキーマは、ノードの全体的なドキュメントの構造と型を定義します。</span><span class="sxs-lookup"><span data-stu-id="61b96-162">The schema defines overall document structure and types of nodes.</span></span> <span data-ttu-id="61b96-163">スキーマが存在する場合、選択的 XML インデックスは、ユーザーがパスを昇格したときのスキーマ構造を適用することで、パスの XQUERY 型を指定する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="61b96-163">If a schema exists, Selective XML Index applies the schema structure when the user promotes paths, so there is no need to specify the XQUERY types for paths.</span></span>  
  
 <span data-ttu-id="61b96-164">選択的 XML インデックスは、次の XSD 型をサポートします。</span><span class="sxs-lookup"><span data-stu-id="61b96-164">Selective XML Index supports following XSD types:</span></span>  
  
-   <span data-ttu-id="61b96-165">**xs:anyUri**</span><span class="sxs-lookup"><span data-stu-id="61b96-165">**xs:anyUri**</span></span>  
  
-   <span data-ttu-id="61b96-166">**xs:boolean**</span><span class="sxs-lookup"><span data-stu-id="61b96-166">**xs:boolean**</span></span>  
  
-   <span data-ttu-id="61b96-167">**xs:date**</span><span class="sxs-lookup"><span data-stu-id="61b96-167">**xs:date**</span></span>  
  
-   <span data-ttu-id="61b96-168">**xs:dateTime**</span><span class="sxs-lookup"><span data-stu-id="61b96-168">**xs:dateTime**</span></span>  
  
-   <span data-ttu-id="61b96-169">**xs:day**</span><span class="sxs-lookup"><span data-stu-id="61b96-169">**xs:day**</span></span>  
  
-   <span data-ttu-id="61b96-170">**xs:decimal**</span><span class="sxs-lookup"><span data-stu-id="61b96-170">**xs:decimal**</span></span>  
  
-   <span data-ttu-id="61b96-171">**xs:double**</span><span class="sxs-lookup"><span data-stu-id="61b96-171">**xs:double**</span></span>  
  
-   <span data-ttu-id="61b96-172">**xs:float**</span><span class="sxs-lookup"><span data-stu-id="61b96-172">**xs:float**</span></span>  
  
-   <span data-ttu-id="61b96-173">**xs:int**</span><span class="sxs-lookup"><span data-stu-id="61b96-173">**xs:int**</span></span>  
  
-   <span data-ttu-id="61b96-174">**xs:integer**</span><span class="sxs-lookup"><span data-stu-id="61b96-174">**xs:integer**</span></span>  
  
-   <span data-ttu-id="61b96-175">**xs:language**</span><span class="sxs-lookup"><span data-stu-id="61b96-175">**xs:language**</span></span>  
  
-   <span data-ttu-id="61b96-176">**xs:long**</span><span class="sxs-lookup"><span data-stu-id="61b96-176">**xs:long**</span></span>  
  
-   <span data-ttu-id="61b96-177">**xs:name**</span><span class="sxs-lookup"><span data-stu-id="61b96-177">**xs:name**</span></span>  
  
-   <span data-ttu-id="61b96-178">**xs:NCName**</span><span class="sxs-lookup"><span data-stu-id="61b96-178">**xs:NCName**</span></span>  
  
-   <span data-ttu-id="61b96-179">**xs:negativeInteger**</span><span class="sxs-lookup"><span data-stu-id="61b96-179">**xs:negativeInteger**</span></span>  
  
-   <span data-ttu-id="61b96-180">**xs:nmtoken**</span><span class="sxs-lookup"><span data-stu-id="61b96-180">**xs:nmtoken**</span></span>  
  
-   <span data-ttu-id="61b96-181">**xs:nonNegativeInteger**</span><span class="sxs-lookup"><span data-stu-id="61b96-181">**xs:nonNegativeInteger**</span></span>  
  
-   <span data-ttu-id="61b96-182">**xs:nonPositiveInteger**</span><span class="sxs-lookup"><span data-stu-id="61b96-182">**xs:nonPositiveInteger**</span></span>  
  
-   <span data-ttu-id="61b96-183">**xs:positiveInteger**</span><span class="sxs-lookup"><span data-stu-id="61b96-183">**xs:positiveInteger**</span></span>  
  
-   <span data-ttu-id="61b96-184">**xs:qname**</span><span class="sxs-lookup"><span data-stu-id="61b96-184">**xs:qname**</span></span>  
  
-   <span data-ttu-id="61b96-185">**xs:short**</span><span class="sxs-lookup"><span data-stu-id="61b96-185">**xs:short**</span></span>  
  
-   <span data-ttu-id="61b96-186">**xs:string**</span><span class="sxs-lookup"><span data-stu-id="61b96-186">**xs:string**</span></span>  
  
-   <span data-ttu-id="61b96-187">**xs:time**</span><span class="sxs-lookup"><span data-stu-id="61b96-187">**xs:time**</span></span>  
  
-   <span data-ttu-id="61b96-188">**xs:token**</span><span class="sxs-lookup"><span data-stu-id="61b96-188">**xs:token**</span></span>  
  
-   <span data-ttu-id="61b96-189">**xs:unsignedByte**</span><span class="sxs-lookup"><span data-stu-id="61b96-189">**xs:unsignedByte**</span></span>  
  
-   <span data-ttu-id="61b96-190">**xs:unsignedInt**</span><span class="sxs-lookup"><span data-stu-id="61b96-190">**xs:unsignedInt**</span></span>  
  
-   <span data-ttu-id="61b96-191">**xs:unsignedLong**</span><span class="sxs-lookup"><span data-stu-id="61b96-191">**xs:unsignedLong**</span></span>  
  
-   <span data-ttu-id="61b96-192">**xs:unsignedShort**</span><span class="sxs-lookup"><span data-stu-id="61b96-192">**xs:unsignedShort**</span></span>  
  
 <span data-ttu-id="61b96-193">スキーマが関連付けられたドキュメントに対して選択的 XML インデックスを作成する場合は、インデックスの設定または変更時に XQUERY 型を指定すると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-193">When Selective XML Index is created over a document that has schema associated with it, specifying a XQUERY type at index creation or altering returns an error.</span></span> <span data-ttu-id="61b96-194">ユーザーは、パスの昇格部分で SQL 型の注釈を使用できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-194">The user can use SQL type annotations in the path promotion part.</span></span> <span data-ttu-id="61b96-195">SQL 型はスキーマに定義された XSD 型の有効な変換である必要があり、そうでない場合はエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="61b96-195">The SQL type must be a valid conversion from the XSD type defined in the schema, or an error is thrown.</span></span> <span data-ttu-id="61b96-196">日付型または時刻型を除いて、XSD に十分な表現が指定されたすべての SQL 型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="61b96-196">All SQL types that have adequate representation in XSD are supported, with an exception of date/time types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="61b96-197">選択的インデックスは、選択的 XML インデックスのパスの昇格に指定された型が、value() メソッドの戻り値の型と同じ場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-197">The selective index is used if the type specified in the Selective XML Index path promotion is the same as the value() method return value.</span></span>  
  
 <span data-ttu-id="61b96-198">型指定された XML ドキュメントで、次の最適化ヒントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-198">The following optimization hints can be used with typed XML documents:</span></span>  
  
-   <span data-ttu-id="61b96-199">node() 最適化ヒント。</span><span class="sxs-lookup"><span data-stu-id="61b96-199">node() optimization hint.</span></span>  
  
-   <span data-ttu-id="61b96-200">MAXLENGTH 最適化ヒントを xs:string 型と共に使用して、インデックス値を短縮できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-200">MAXLENGTH optimization hint can be used with xs:string types to shorten the indexed value.</span></span>  
  
 <span data-ttu-id="61b96-201">最適化ヒントの詳細については、「 [最適化ヒントの指定](#hints)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61b96-201">For more information about optimization hints, see [Specifying Optimization Hints](#hints).</span></span>  
  
##  <a name="specifying-paths"></a><a name="paths"></a> <span data-ttu-id="61b96-202">パスの指定</span><span class="sxs-lookup"><span data-stu-id="61b96-202">Specifying Paths</span></span>  
 <span data-ttu-id="61b96-203">選択的 XML インデックスを使用して、実行する予定のクエリに関連する格納された XML データから、ノードのサブセットにのみインデックスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-203">A selective XML index lets you index only a subset of nodes from the stored XML data that are relevant for the queries that you expect to run.</span></span> <span data-ttu-id="61b96-204">関連するノードのサブセットが XML ドキュメント内のノードの総数よりも大幅に少ない場合、選択的 XML インデックスには、関連するノードだけが格納されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-204">When the subset of relevant nodes is much smaller than the total number of nodes in the XML document, the selective XML index stores only the relevant nodes.</span></span> <span data-ttu-id="61b96-205">選択的 XML インデックスを有効利用するには、インデックスを設定する適切なノードのサブセットを識別します。</span><span class="sxs-lookup"><span data-stu-id="61b96-205">To benefit from a selective XML index, identify the correct subset of nodes to index.</span></span>  
  
### <a name="choosing-the-nodes-to-index"></a><span data-ttu-id="61b96-206">インデックスを設定するノードの選択</span><span class="sxs-lookup"><span data-stu-id="61b96-206">Choosing the nodes to index</span></span>  
 <span data-ttu-id="61b96-207">次の 2 つの単純な原則を使用して、選択的 XML インデックスに追加する適切なノードのサブセットを識別できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-207">You can use the following two simple principles to identify the correct subset of nodes to add to a selective XML index.</span></span>  
  
1.  <span data-ttu-id="61b96-208">**原則 1**: 特定の XQuery 式を評価するには、調べる必要があるすべてのノードにインデックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="61b96-208">**Principle 1**: To evaluate a given XQuery expression, index all nodes that you need to examine.</span></span>  
  
    -   <span data-ttu-id="61b96-209">その存在または値が XQuery 式で使用されるすべてのノードにインデックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="61b96-209">Index all nodes whose existence or value is used in the XQuery expression.</span></span>  
  
    -   <span data-ttu-id="61b96-210">XQuery 述語が適用される XQuery 式に含まれるすべてのノードにインデックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="61b96-210">Index all nodes in the XQuery expression on which XQuery predicates are applied.</span></span>  
  
     <span data-ttu-id="61b96-211">このトピックの [サンプル XML ドキュメント](#sample) に対する次の単純なクエリを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="61b96-211">Consider the following simple query over the [sample XML document](#sample) in this topic:</span></span>  
  
    ```sql  
    SELECT T.record FROM myXMLTable T  
    WHERE T.xmldata.exist('/a/b[./c = "43"]') = 1  
    ```  
  
     <span data-ttu-id="61b96-212">このクエリを満足させる XML インスタンスを返すため、選択的 XML インデックスは、すべての XML インスタンス内の次の 2 つのノードを調べます。</span><span class="sxs-lookup"><span data-stu-id="61b96-212">In order to return the XML instances that satisfy this query, a selective XML index needs to examine two nodes in every XML instance:</span></span>  
  
    -   <span data-ttu-id="61b96-213">ノード `c`。その値が XQuery 式で使用されているため。</span><span class="sxs-lookup"><span data-stu-id="61b96-213">Node `c`, because its value is used in the XQuery expression.</span></span>  
  
    -   <span data-ttu-id="61b96-214">ノード `b`。述語が、XQuery 式の中でノード`b` に適用されるため。</span><span class="sxs-lookup"><span data-stu-id="61b96-214">Node `b`, because a predicate is applied over node`b` in the XQuery expression.</span></span>  
  
2.  <span data-ttu-id="61b96-215">**原則 2**: 最大限のパフォーマンスを得るには、特定の XQuery 式を評価するために必要なすべてのノードにインデックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="61b96-215">**Principle 2**: For best performance, index all nodes that are required to evaluate a given XQuery expression.</span></span> <span data-ttu-id="61b96-216">ノードの一部にのみインデックスを設定した場合、選択的 XML インデックスは、インデックス付きノードのみを含むサブ式の評価を向上させます。</span><span class="sxs-lookup"><span data-stu-id="61b96-216">If you index only some of the nodes, then the selective XML index improves the evaluation of sub-expressions that include only indexed nodes.</span></span>  
  
 <span data-ttu-id="61b96-217">上に示した SELECT ステートメントのパフォーマンスを向上させるには、次に示す選択的 XML インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="61b96-217">To improve the performance of the SELECT statement shown above, you can create the following selective XML index:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX simple_sxi  
ON Tbl(xmlcol)  
FOR  
(  
    path123 =  '/a/b',  
    path124 =  '/a/b/c'  
)  
```  
  
### <a name="indexing-identical-paths"></a><span data-ttu-id="61b96-218">同一パスのインデックス設定</span><span class="sxs-lookup"><span data-stu-id="61b96-218">Indexing identical paths</span></span>  
 <span data-ttu-id="61b96-219">同一パスを異なる名前で同じデータ型として昇格させることはできません。</span><span class="sxs-lookup"><span data-stu-id="61b96-219">You cannot promote identical paths as the same data type under different path names.</span></span> <span data-ttu-id="61b96-220">たとえば、次のクエリでは、 `pathOne` と `pathTwo` が同じため、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="61b96-220">For example, the following query raises an error, because `pathOne` and `pathTwo` are identical:</span></span>  
  
```sql  
CREATE SELECTIVE INDEX test_simple_sxi ON T1(xmlCol)  
FOR  
(  
    pathOne = 'book/authors/authorID' AS XQUERY 'xs:string',  
    pathTwo = 'book/authors/authorID' AS XQUERY 'xs:string'  
)  
```  
  
 <span data-ttu-id="61b96-221">ただし、同一パスを異なる名前を持つ異なるデータ型として昇格させることはできます。</span><span class="sxs-lookup"><span data-stu-id="61b96-221">However, you can promote identical paths as different data types with different names.</span></span> <span data-ttu-id="61b96-222">たとえば、次のクエリはデータ型が異なるため、許容されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-222">For example, the following query is now acceptable, because the data types are different:</span></span>  
  
```sql  
CREATE SELECTIVE INDEX test_simple_sxi ON T1(xmlCol)  
FOR  
(  
    pathOne = 'book/authors/authorID' AS XQUERY 'xs:double',  
    pathTwo = 'book/authors/authorID' AS XQUERY 'xs:string'  
)  
```  
  
### <a name="examples"></a><span data-ttu-id="61b96-223">例</span><span class="sxs-lookup"><span data-stu-id="61b96-223">Examples</span></span>  
 <span data-ttu-id="61b96-224">異なる XQuery 型用のインデックスを設定するために適切なノードを選択するいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-224">Here are some additional examples of selecting the correct nodes to index for different XQuery types.</span></span>  
  
 <span data-ttu-id="61b96-225">**例 1**</span><span class="sxs-lookup"><span data-stu-id="61b96-225">**Example 1**</span></span>  
  
 <span data-ttu-id="61b96-226">次に示すのは、exist() メソッドを使用する単純な XQuery です。</span><span class="sxs-lookup"><span data-stu-id="61b96-226">Here is a simple XQuery that uses the exist() method:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b/c/d/e/h') = 1  
```  
  
 <span data-ttu-id="61b96-227">次の表に、このクエリで選択的 XML インデックスの使用を可能にするためにインデックスを設定する必要があるノードを示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-227">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="61b96-228">インデックスに含めるノード</span><span class="sxs-lookup"><span data-stu-id="61b96-228">Node to include in the index</span></span>|<span data-ttu-id="61b96-229">このノードにインデックスを設定する理由</span><span class="sxs-lookup"><span data-stu-id="61b96-229">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="61b96-230">**/a/b/c/d/e/h**</span><span class="sxs-lookup"><span data-stu-id="61b96-230">**/a/b/c/d/e/h**</span></span>|<span data-ttu-id="61b96-231">ノード `h` が exist() メソッドで評価される。</span><span class="sxs-lookup"><span data-stu-id="61b96-231">The existence of node `h` is evaluated in the exist() method.</span></span>|  
  
 <span data-ttu-id="61b96-232">**例 2**</span><span class="sxs-lookup"><span data-stu-id="61b96-232">**Example 2**</span></span>  
  
 <span data-ttu-id="61b96-233">次に示すのは、前の XQuery のより複雑なバリエーションです。ここでは述語が適用されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-233">Here is a more complex variation of the previous XQuery, with a predicate applied:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b/c/d/e[./f = "SQL"]') = 1  
```  
  
 <span data-ttu-id="61b96-234">次の表に、このクエリで選択的 XML インデックスの使用を可能にするためにインデックスを設定する必要があるノードを示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-234">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="61b96-235">インデックスに含めるノード</span><span class="sxs-lookup"><span data-stu-id="61b96-235">Node to include in the index</span></span>|<span data-ttu-id="61b96-236">このノードにインデックスを設定する理由</span><span class="sxs-lookup"><span data-stu-id="61b96-236">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="61b96-237">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="61b96-237">**/a/b/c/d/e**</span></span>|<span data-ttu-id="61b96-238">述語がノード `e`に適用される。</span><span class="sxs-lookup"><span data-stu-id="61b96-238">A predicate is applied over node `e`.</span></span>|  
|<span data-ttu-id="61b96-239">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="61b96-239">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="61b96-240">ノード `f` の値が述語内で評価される。</span><span class="sxs-lookup"><span data-stu-id="61b96-240">The value of node `f` is evaluated inside the predicate.</span></span>|  
  
 <span data-ttu-id="61b96-241">**例 3**</span><span class="sxs-lookup"><span data-stu-id="61b96-241">**Example 3**</span></span>  
  
 <span data-ttu-id="61b96-242">次に示すのは、value() 句を使用するさらに複雑なクエリです。</span><span class="sxs-lookup"><span data-stu-id="61b96-242">Here is a more complex query with a value() clause:</span></span>  
  
```sql  
SELECT T.record,  
    T.xmldata.value('(/a/b/c/d/e[./f = "SQL"]/g)[1]', 'nvarchar(100)')  
FROM myXMLTable T  
```  
  
 <span data-ttu-id="61b96-243">次の表に、このクエリで選択的 XML インデックスの使用を可能にするためにインデックスを設定する必要があるノードを示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-243">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="61b96-244">インデックスに含めるノード</span><span class="sxs-lookup"><span data-stu-id="61b96-244">Node to include in the index</span></span>|<span data-ttu-id="61b96-245">このノードにインデックスを設定する理由</span><span class="sxs-lookup"><span data-stu-id="61b96-245">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="61b96-246">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="61b96-246">**/a/b/c/d/e**</span></span>|<span data-ttu-id="61b96-247">述語がノード `e`に適用される。</span><span class="sxs-lookup"><span data-stu-id="61b96-247">A predicate is applied over node `e`.</span></span>|  
|<span data-ttu-id="61b96-248">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="61b96-248">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="61b96-249">ノード `f` の値が述語内で評価される。</span><span class="sxs-lookup"><span data-stu-id="61b96-249">The value of node `f` is evaluated inside the predicate.</span></span>|  
|<span data-ttu-id="61b96-250">**/a/b/c/d/e/g**</span><span class="sxs-lookup"><span data-stu-id="61b96-250">**/a/b/c/d/e/g**</span></span>|<span data-ttu-id="61b96-251">ノード `g` の値が value() メソッドによって返される。</span><span class="sxs-lookup"><span data-stu-id="61b96-251">The value of node `g` is returned by the value() method.</span></span>|  
  
 <span data-ttu-id="61b96-252">**例 4**</span><span class="sxs-lookup"><span data-stu-id="61b96-252">**Example 4**</span></span>  
  
 <span data-ttu-id="61b96-253">次に示すのは、exist() 句の中で FLWOR 句を使用するクエリです</span><span class="sxs-lookup"><span data-stu-id="61b96-253">Here is a query that uses a FLWOR clause inside an exist() clause.</span></span> <span data-ttu-id="61b96-254">(FLWOR という名前は、XQuery FLWOR 式を構成できる 5 つの句 (for、let、where、order by、および return) に由来します)。</span><span class="sxs-lookup"><span data-stu-id="61b96-254">(The name FLWOR comes from the five clauses that can make up an XQuery FLWOR expression: for, let, where, order by, and return.)</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('  
  For $x in /a/b/c/d/e  
  Where $x/f = "SQL"  
  Return $x/g  
') = 1  
```  
  
 <span data-ttu-id="61b96-255">次の表に、このクエリで選択的 XML インデックスの使用を可能にするためにインデックスを設定する必要があるノードを示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-255">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="61b96-256">インデックスに含めるノード</span><span class="sxs-lookup"><span data-stu-id="61b96-256">Node to include in the index</span></span>|<span data-ttu-id="61b96-257">このノードにインデックスを設定する理由</span><span class="sxs-lookup"><span data-stu-id="61b96-257">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="61b96-258">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="61b96-258">**/a/b/c/d/e**</span></span>|<span data-ttu-id="61b96-259">ノード `e` の存在が FLWOR 区の中で評価される。</span><span class="sxs-lookup"><span data-stu-id="61b96-259">The existence of node `e` is evaluated in the FLWOR clause.</span></span>|  
|<span data-ttu-id="61b96-260">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="61b96-260">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="61b96-261">ノード `f` の値が FLWOR 句の中で評価される。</span><span class="sxs-lookup"><span data-stu-id="61b96-261">The value of node `f` is evaluated in the FLWOR clause.</span></span>|  
|<span data-ttu-id="61b96-262">**/a/b/c/d/e/g**</span><span class="sxs-lookup"><span data-stu-id="61b96-262">**/a/b/c/d/e/g**</span></span>|<span data-ttu-id="61b96-263">ノード `g` の存在が exist() メソッドによって評価される。</span><span class="sxs-lookup"><span data-stu-id="61b96-263">The existence of node `g` is evaluated by the exist() method.</span></span>|  
  

  
##  <a name="specifying-optimization-hints"></a><a name="hints"></a> <span data-ttu-id="61b96-264">最適化ヒントの指定</span><span class="sxs-lookup"><span data-stu-id="61b96-264">Specifying Optimization Hints</span></span>  
 <span data-ttu-id="61b96-265">省略可能な最適化ヒントを使用して、選択的 XML インデックスによってインデックス設定されるノードのマッピングの詳細を指定できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-265">You can use optional optimization hints to specify additional mapping details for a node indexed by a selective XML index.</span></span> <span data-ttu-id="61b96-266">たとえば、ノードのデータ型とカーディナリティ、およびデータの構造に関する特定の情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-266">For example, you can specify the data type and cardinality of the node, and certain information about the structure of the data.</span></span> <span data-ttu-id="61b96-267">この追加情報により、マッピングに対するサポートが向上します。</span><span class="sxs-lookup"><span data-stu-id="61b96-267">This additional information supports better mapping.</span></span> <span data-ttu-id="61b96-268">さらに、パフォーマンスの向上またはストレージの節約、あるいはその両方が実現します。</span><span class="sxs-lookup"><span data-stu-id="61b96-268">It also results in improvements in performance or savings in storage, or both.</span></span>  
  
 <span data-ttu-id="61b96-269">最適化ヒントの使用は任意です。</span><span class="sxs-lookup"><span data-stu-id="61b96-269">The use of optimization hints is optional.</span></span> <span data-ttu-id="61b96-270">常に既定のマッピングをそのまま使用できます。これらは信頼できますが、最適化されたパフォーマンスとストレージを提供しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="61b96-270">You can always accept the default mappings, which are reliable but may not provide optimal performance and storage.</span></span>  
  
 <span data-ttu-id="61b96-271">一部の最適化ヒント (SINGLETON ヒントなど) には、データに対する制約があります。</span><span class="sxs-lookup"><span data-stu-id="61b96-271">Some optimization hints - for example, the SINGLETON hint - introduce constraints over your data.</span></span> <span data-ttu-id="61b96-272">場合によっては、これらの制約が満たされないとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="61b96-272">In some cases, errors may be raised when those constraints are not met.</span></span>  
  
### <a name="benefits-of-optimization-hints"></a><span data-ttu-id="61b96-273">最適化ヒントの利点</span><span class="sxs-lookup"><span data-stu-id="61b96-273">Benefits of Optimization Hints</span></span>  
 <span data-ttu-id="61b96-274">次の表に、より効率的なストレージまたはパフォーマンスの向上をサポートする最適化ヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-274">The following table identifies the optimization hints that support more efficient storage or improved performance.</span></span>  
  
|<span data-ttu-id="61b96-275">最適化ヒント</span><span class="sxs-lookup"><span data-stu-id="61b96-275">Optimization hint</span></span>|<span data-ttu-id="61b96-276">より効率的なストレージ</span><span class="sxs-lookup"><span data-stu-id="61b96-276">More efficient storage</span></span>|<span data-ttu-id="61b96-277">パフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="61b96-277">Improved performance</span></span>|  
|-----------------------|----------------------------|--------------------------|  
|<span data-ttu-id="61b96-278">**node()**</span><span class="sxs-lookup"><span data-stu-id="61b96-278">**node()**</span></span>|<span data-ttu-id="61b96-279">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-279">Yes</span></span>|<span data-ttu-id="61b96-280">いいえ</span><span class="sxs-lookup"><span data-stu-id="61b96-280">No</span></span>|  
|<span data-ttu-id="61b96-281">**SINGLETON**</span><span class="sxs-lookup"><span data-stu-id="61b96-281">**SINGLETON**</span></span>|<span data-ttu-id="61b96-282">いいえ</span><span class="sxs-lookup"><span data-stu-id="61b96-282">No</span></span>|<span data-ttu-id="61b96-283">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-283">Yes</span></span>|  
|<span data-ttu-id="61b96-284">**DATA TYPE**</span><span class="sxs-lookup"><span data-stu-id="61b96-284">**DATA TYPE**</span></span>|<span data-ttu-id="61b96-285">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-285">Yes</span></span>|<span data-ttu-id="61b96-286">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-286">Yes</span></span>|  
|<span data-ttu-id="61b96-287">**MAXLENGTH**</span><span class="sxs-lookup"><span data-stu-id="61b96-287">**MAXLENGTH**</span></span>|<span data-ttu-id="61b96-288">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-288">Yes</span></span>|<span data-ttu-id="61b96-289">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-289">Yes</span></span>|  
  
### <a name="optimization-hints-and-data-types"></a><span data-ttu-id="61b96-290">最適化ヒントとデータ型</span><span class="sxs-lookup"><span data-stu-id="61b96-290">Optimization Hints and Data Types</span></span>  
 <span data-ttu-id="61b96-291">ノードに XQuery データ型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型としてインデックスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-291">You can index nodes as XQuery data types or as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="61b96-292">次の表に、各データ型でサポートされる最適化ヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="61b96-292">The following table shows which optimization hints are supported with each data type.</span></span>  
  
|<span data-ttu-id="61b96-293">最適化ヒント</span><span class="sxs-lookup"><span data-stu-id="61b96-293">Optimization hint</span></span>|<span data-ttu-id="61b96-294">XQuery のデータ型</span><span class="sxs-lookup"><span data-stu-id="61b96-294">XQuery data types</span></span>|<span data-ttu-id="61b96-295">SQL データ型</span><span class="sxs-lookup"><span data-stu-id="61b96-295">SQL data types</span></span>|  
|-----------------------|-----------------------|--------------------|  
|<span data-ttu-id="61b96-296">**node()**</span><span class="sxs-lookup"><span data-stu-id="61b96-296">**node()**</span></span>|<span data-ttu-id="61b96-297">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-297">Yes</span></span>|<span data-ttu-id="61b96-298">いいえ</span><span class="sxs-lookup"><span data-stu-id="61b96-298">No</span></span>|  
|<span data-ttu-id="61b96-299">**SINGLETON**</span><span class="sxs-lookup"><span data-stu-id="61b96-299">**SINGLETON**</span></span>|<span data-ttu-id="61b96-300">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-300">Yes</span></span>|<span data-ttu-id="61b96-301">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-301">Yes</span></span>|  
|<span data-ttu-id="61b96-302">**DATA TYPE**</span><span class="sxs-lookup"><span data-stu-id="61b96-302">**DATA TYPE**</span></span>|<span data-ttu-id="61b96-303">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-303">Yes</span></span>|<span data-ttu-id="61b96-304">いいえ</span><span class="sxs-lookup"><span data-stu-id="61b96-304">No</span></span>|  
|<span data-ttu-id="61b96-305">**MAXLENGTH**</span><span class="sxs-lookup"><span data-stu-id="61b96-305">**MAXLENGTH**</span></span>|<span data-ttu-id="61b96-306">はい</span><span class="sxs-lookup"><span data-stu-id="61b96-306">Yes</span></span>|<span data-ttu-id="61b96-307">いいえ</span><span class="sxs-lookup"><span data-stu-id="61b96-307">No</span></span>|  
  
### <a name="node-optimization-hint"></a><span data-ttu-id="61b96-308">node() 最適化ヒント</span><span class="sxs-lookup"><span data-stu-id="61b96-308">node() optimization hint</span></span>  
 <span data-ttu-id="61b96-309">適用対象:XQuery のデータ型</span><span class="sxs-lookup"><span data-stu-id="61b96-309">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="61b96-310">node() 最適化ヒントを使用して、一般的なクエリではその値を評価する必要がないノードを指定できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-310">You can use the node() optimization to specify a node whose value is not required to evaluate the typical query.</span></span> <span data-ttu-id="61b96-311">このヒントは、通常のクエリがノードの存在のみを評価する必要があるときに必要なメモリ量が減少します</span><span class="sxs-lookup"><span data-stu-id="61b96-311">This hint reduces storage requirements when the typical query only has to evaluate the existence of the node.</span></span> <span data-ttu-id="61b96-312">(既定では、選択的 XML インデックスは、complex ノード型以外の昇格されたすべてのノードの値を格納します)。</span><span class="sxs-lookup"><span data-stu-id="61b96-312">(By default, a selective XML index stores the value for all promoted nodes, except complex node types.)</span></span>  
  
 <span data-ttu-id="61b96-313">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="61b96-313">Consider the following example:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b[./c=5]') = 1  
```  
  
 <span data-ttu-id="61b96-314">このクエリを選択的 XML インデックスを使用して評価するには、ノード `b` とノード `c`を昇格します。</span><span class="sxs-lookup"><span data-stu-id="61b96-314">To use a selective XML index to evaluate this query, promote nodes `b` and `c`.</span></span> <span data-ttu-id="61b96-315">ただし、ノード `b` の値は必要ないため、次の構文で node() ヒントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-315">However, since the value of node `b` is not required, you can use the node() hint with the following syntax:</span></span>  
  
 `/a/b/ as node()`  
  
 <span data-ttu-id="61b96-316">node() ヒントでインデックス設定されているノードの値がクエリで必要な場合、選択的 XML インデックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="61b96-316">If a query requires the value of a node that has been indexed with the node() hint, then the selective XML index cannot be used.</span></span>  
  
### <a name="singleton-optimization-hint"></a><span data-ttu-id="61b96-317">SINGLETON 最適化ヒント</span><span class="sxs-lookup"><span data-stu-id="61b96-317">SINGLETON optimization hint</span></span>  
 <span data-ttu-id="61b96-318">適用対象:XQuery データ型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型</span><span class="sxs-lookup"><span data-stu-id="61b96-318">Applies to: XQuery or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types</span></span>  
  
 <span data-ttu-id="61b96-319">SINGLETON 最適化ヒントは、ノードのカーディナリティを指定します。</span><span class="sxs-lookup"><span data-stu-id="61b96-319">The SINGLETON optimization hint specifies the cardinality of a node.</span></span> <span data-ttu-id="61b96-320">このヒントは、ノードが親または先祖の中で最大で 1 回出現することを事前に通知するため、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="61b96-320">This hint improves query performance since it is known in advance that a node appears at most one time within its parent or ancestor.</span></span>  
  
 <span data-ttu-id="61b96-321">このトピックの [サンプル XML ドキュメント](#sample) を参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="61b96-321">Consider the [sample XML document](#sample) in this topic.</span></span>  
  
 <span data-ttu-id="61b96-322">選択的 XML を使用してこのドキュメントのクエリを実行するには、ノード `d` が親の中で最大 1 回出現するため、そのノードに対して SINGLETON ヒントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-322">To use a selective XML index to query this document, you can specify the SINGLETON hint for node `d` since it appears at most one time within its parent.</span></span>  
  
 <span data-ttu-id="61b96-323">SINGLETON ヒントは指定されているが、ノードがその親または先祖の中で複数回出現した場合は、インデックスの作成時 (既存のデータの場合) またはクエリの実行時 (新規データの場合) にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="61b96-323">If the SINGLETON hint has been specified, but a node appears more than one time within its parent or ancestor, then an error is raised when you create the index (for existing data) or when you run a query (for new data).</span></span>  
  
### <a name="data-type-optimization-hint"></a><span data-ttu-id="61b96-324">DATA TYPE 最適化ヒント</span><span class="sxs-lookup"><span data-stu-id="61b96-324">DATA TYPE optimization hint</span></span>  
 <span data-ttu-id="61b96-325">適用対象:XQuery のデータ型</span><span class="sxs-lookup"><span data-stu-id="61b96-325">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="61b96-326">DATA TYPE 最適化ヒントを使用して、インデックス付きノードに対して XQuery データ型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-326">The DATA TYPE optimization hint lets you specify an XQuery or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the indexed node.</span></span> <span data-ttu-id="61b96-327">このデータ型は、選択的 XML インデックスのデータ テーブル内のインデックス付きノードに対応する列で使用されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-327">The data type is used for the column in the data table of the selective XML index that corresponds to the indexed node.</span></span>  
  
 <span data-ttu-id="61b96-328">既存の値の指定されたデータ型へのキャストが失敗した場合でも、インデックスへの挿入操作は失敗しません。ただし、インデックスのデータ テーブルには NULL 値が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="61b96-328">When casting an existing value to the specified data type fails, the insert operation (into the index) does not fail; however, a null value is inserted into the data table of the index.</span></span>  
  
### <a name="maxlength-optimization-hint"></a><span data-ttu-id="61b96-329">MAXLENGTH 最適化ヒント</span><span class="sxs-lookup"><span data-stu-id="61b96-329">MAXLENGTH optimization hint</span></span>  
 <span data-ttu-id="61b96-330">適用対象:XQuery のデータ型</span><span class="sxs-lookup"><span data-stu-id="61b96-330">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="61b96-331">MAXLENGTH 最適化ヒントを使用して、xs:string データの長さを制限できます。</span><span class="sxs-lookup"><span data-stu-id="61b96-331">The MAXLENGTH optimization hint lets you limit the length of xs:string data.</span></span> <span data-ttu-id="61b96-332">VARCHAR データ型または NVARCHAR データ型を指定するときに長さを指定するため、MAXLENGTH は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型には関連しません。</span><span class="sxs-lookup"><span data-stu-id="61b96-332">MAXLENGTH is not relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types since you specify the length when you specify the VARCHAR or NVARCHAR date types.</span></span>  
  
 <span data-ttu-id="61b96-333">既存の文字列が指定された MAXLENGTH よりも長い場合は、その値をインデックスに挿入する操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="61b96-333">When an existing string is longer than the specified MAXLENGTH, then inserting that value into the index fails.</span></span>  
  

  
##  <a name="sample-xml-document-for-examples"></a><a name="sample"></a> <span data-ttu-id="61b96-334">例で参照されるサンプル XML ドキュメント</span><span class="sxs-lookup"><span data-stu-id="61b96-334">Sample XML Document for Examples</span></span>  
 <span data-ttu-id="61b96-335">このトピックの例では、次に示すサンプル XML ドキュメントが参照されています。</span><span class="sxs-lookup"><span data-stu-id="61b96-335">The following sample XML document is referenced in the examples in this topic:</span></span>  
  
```xml  
<a>  
    <b>  
         <c atc="aa">10</c>  
         <c atc="bb">15</c>  
         <d atd1="dd" atd2="ddd">md </d>  
    </b>  
     <b>  
        <c></c>  
        <c atc="">117</c>  
     </b>  
</a>  
```  
  

  
## <a name="see-also"></a><span data-ttu-id="61b96-336">参照</span><span class="sxs-lookup"><span data-stu-id="61b96-336">See Also</span></span>  
 <span data-ttu-id="61b96-337">[選択的 XML インデックス &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md) </span><span class="sxs-lookup"><span data-stu-id="61b96-337">[Selective XML Indexes &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md) </span></span>  
 [<span data-ttu-id="61b96-338">選択的 XML インデックスの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="61b96-338">Create, Alter, and Drop Selective XML Indexes</span></span>](../xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  
