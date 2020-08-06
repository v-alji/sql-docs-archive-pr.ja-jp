---
title: ロケーションパスでの選択述語の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: rothja
ms.author: jroth
ms.openlocfilehash: d323558556fb05d350e48ea9218a8e9b8dc9b5c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641544"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a><span data-ttu-id="92ea0-102">ロケーション パスでの選択述語の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="92ea0-102">Specifying Selection Predicates in the Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="92ea0-103">述語は、SELECT ステートメントの WHERE 句と同様に、軸についてノード セットをフィルター選択するものです。</span><span class="sxs-lookup"><span data-stu-id="92ea0-103">A predicate filters a node-set with respect to an axis (similar to a WHERE clause in a SELECT statement).</span></span> <span data-ttu-id="92ea0-104">述語はかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-104">The predicate is specified between brackets.</span></span> <span data-ttu-id="92ea0-105">フィルター選択されたノード セットの各ノードに対し、ノードをコンテキスト ノード、ノード セット内のノード数をコンテキストのサイズとして、述語式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-105">For each node in the node-set to be filtered, the predicate expression is evaluated with that node as the context node, with the number of nodes in the node-set as context size.</span></span> <span data-ttu-id="92ea0-106">述語式が TRUE と評価された場合、そのノードは結果のノード セットに含められます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-106">If the predicate expression evaluates to TRUE for that node, the node is included in the resulting node-set.</span></span>  
  
 <span data-ttu-id="92ea0-107">XPath では、位置に基づくフィルター選択を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-107">XPath also allows position-based filtering.</span></span> <span data-ttu-id="92ea0-108">数値として評価される述語式を使用すると、その序数に対応するノードが選択されます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-108">A predicate expression evaluating to a number selects that ordinal node.</span></span> <span data-ttu-id="92ea0-109">たとえば、ロケーション パス `Customer[3]` では、3 番目の顧客が返されますが、</span><span class="sxs-lookup"><span data-stu-id="92ea0-109">For example, the location path `Customer[3]` returns the third customer.</span></span> <span data-ttu-id="92ea0-110">このような数値述語はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="92ea0-110">Such numeric predicates are not supported.</span></span> <span data-ttu-id="92ea0-111">サポートされているのは、ブール値の結果を返す述語式のみです。</span><span class="sxs-lookup"><span data-stu-id="92ea0-111">Only predicate expressions that return a Boolean result are supported.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92ea0-112">Xpath のこの XPath 実装と W3C 仕様の違いについては、「 [Xpath クエリの使用の概要 &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92ea0-112">For information about the limitations of this XPath implementation of XPath and the differences between it and the W3C specification, see [Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).</span></span>  
  
## <a name="selection-predicate-example-1"></a><span data-ttu-id="92ea0-113">選択述語: 例1</span><span class="sxs-lookup"><span data-stu-id="92ea0-113">Selection Predicate: Example 1</span></span>  
 <span data-ttu-id="92ea0-114">次の XPath 式 (ロケーションパス) は、現在のコンテキストノードから、 **\<Customer>** **CustomerID**属性が ALFKI の値がであるすべての子要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="92ea0-114">The following XPath expression (location path) selects from the current context node all the **\<Customer>** element children that have the **CustomerID** attribute with value of ALFKI:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 <span data-ttu-id="92ea0-115">この XPath クエリでは、`child` と `attribute` は軸名で、</span><span class="sxs-lookup"><span data-stu-id="92ea0-115">In this XPath query, `child` and `attribute` are axis names.</span></span> <span data-ttu-id="92ea0-116">`Customer`はノードテストです。がである場合は TRUE になり `Customer` **\<element node>** ます。これは、 **\<element>** が軸の主ノード型であるためです `child` 。</span><span class="sxs-lookup"><span data-stu-id="92ea0-116">`Customer` is the node test (TRUE if `Customer` is an **\<element node>**, because **\<element>** is the principal node type for the `child` axis).</span></span> <span data-ttu-id="92ea0-117">`attribute::CustomerID="ALFKI"` は述語です。</span><span class="sxs-lookup"><span data-stu-id="92ea0-117">`attribute::CustomerID="ALFKI"` is the predicate.</span></span> <span data-ttu-id="92ea0-118">述語では、 `attribute` は軸で、は `CustomerID` ノードテストです**CustomerID** **\<attribute>** 。は軸の主ノード型であるため、CustomerID がコンテキストノードの属性である場合は TRUE に `attribute` なります。</span><span class="sxs-lookup"><span data-stu-id="92ea0-118">In the predicate, `attribute` is the axis and `CustomerID` is the node test (TRUE if **CustomerID** is an attribute of the context node, because **\<attribute>** is the principal node type of `attribute` axis).</span></span>  
  
 <span data-ttu-id="92ea0-119">省略構文を使用した場合、XPath クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-119">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a><span data-ttu-id="92ea0-120">選択述語: 例2</span><span class="sxs-lookup"><span data-stu-id="92ea0-120">Selection Predicate: Example 2</span></span>  
 <span data-ttu-id="92ea0-121">次の XPath 式 (ロケーションパス) では、現在のコンテキストノードから、 **\<Order>** **salesorderid**属性を持つすべての孫が値1で選択されます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-121">The following XPath expression (location path) selects from the current context node all the **\<Order>** grandchildren that have the **SalesOrderID** attribute with the value 1:</span></span>  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 <span data-ttu-id="92ea0-122">この XPath 式では、`child` と `attribute` は軸名で、</span><span class="sxs-lookup"><span data-stu-id="92ea0-122">In this XPath expression, `child` and `attribute` are the axis names.</span></span> <span data-ttu-id="92ea0-123">`Customer`、`Order`、および `SalesOrderID` はノード テストです。</span><span class="sxs-lookup"><span data-stu-id="92ea0-123">`Customer`, `Order`, and `SalesOrderID` are the node tests.</span></span> <span data-ttu-id="92ea0-124">`attribute::OrderID="1"` は述語です。</span><span class="sxs-lookup"><span data-stu-id="92ea0-124">`attribute::OrderID="1"` is the predicate.</span></span>  
  
 <span data-ttu-id="92ea0-125">省略構文を使用した場合、XPath クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-125">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a><span data-ttu-id="92ea0-126">選択述語: 例3</span><span class="sxs-lookup"><span data-stu-id="92ea0-126">Selection Predicate: Example 3</span></span>  
 <span data-ttu-id="92ea0-127">次の XPath 式 (ロケーションパス) では、現在のコンテキストノードから、 **\<Customer>** 1 つまたは複数の子を持つすべての子が選択され **\<ContactName>** ます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-127">The following XPath expression (location path) selects from the current context node all the **\<Customer>** children that have one or more **\<ContactName>** children:</span></span>  
  
```  
child::Customer[child::ContactName]  
```  
  
 <span data-ttu-id="92ea0-128">この例では、が XML ドキュメント内の要素の子要素であることを前提としてい **\<ContactName>** **\<Customer>** ます。これは、注釈付き XSD スキーマでは*要素中心のマッピング*と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="92ea0-128">This example assumes that the **\<ContactName>** is a child element of the **\<Customer>** element in the XML document, which is referred to as *element-centric mapping* in an annotated XSD schema.</span></span>  
  
 <span data-ttu-id="92ea0-129">この XPath 式では、`child` が軸名で、</span><span class="sxs-lookup"><span data-stu-id="92ea0-129">In this XPath expression, `child` is the axis name.</span></span> <span data-ttu-id="92ea0-130">`Customer`はノードテストです `Customer` **\<element>** 。は軸の主ノード型であるため、がノードの場合は TRUE に **\<element>** `child` なります。</span><span class="sxs-lookup"><span data-stu-id="92ea0-130">`Customer` is the node test (TRUE if `Customer` is an **\<element>** node, because **\<element>** is the principal node type for `child` axis).</span></span> <span data-ttu-id="92ea0-131">`child::ContactName` は述語です。</span><span class="sxs-lookup"><span data-stu-id="92ea0-131">`child::ContactName` is the predicate.</span></span> <span data-ttu-id="92ea0-132">述語では、 `child` は軸で、は `ContactName` ノードテストです (がノードの場合は TRUE `ContactName` **\<element>** )。</span><span class="sxs-lookup"><span data-stu-id="92ea0-132">In the predicate, `child` is the axis and `ContactName` is the node test (TRUE if `ContactName` is an **\<element>** node).</span></span>  
  
 <span data-ttu-id="92ea0-133">この式は、 **\<Customer>** 子要素を持つコンテキストノードの子要素のみを返し **\<ContactName>** ます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-133">This expression returns only the **\<Customer>** element children of the context node that have **\<ContactName>** element children.</span></span>  
  
 <span data-ttu-id="92ea0-134">省略構文を使用した場合、XPath クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-134">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a><span data-ttu-id="92ea0-135">選択述語: 例4</span><span class="sxs-lookup"><span data-stu-id="92ea0-135">Selection Predicate: Example 4</span></span>  
 <span data-ttu-id="92ea0-136">次の XPath 式は、 **\<Customer>** 要素の子を持たないコンテキストノードの子要素を選択し **\<ContactName>** ます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-136">The following XPath expression selects **\<Customer>** element children of the context node that do not have **\<ContactName>** element children:</span></span>  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 <span data-ttu-id="92ea0-137">この例で **\<ContactName>** は、が XML ドキュメント内の要素の子要素であり、データベースでは [担当する] フィールドが必須ではないことを前提としてい **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-137">This example assumes that **\<ContactName>** is a child element of the **\<Customer>** element in the XML document, and the ContactName field is not required in the database.</span></span>  
  
 <span data-ttu-id="92ea0-138">この例では、`child` は軸で、</span><span class="sxs-lookup"><span data-stu-id="92ea0-138">In this example, `child` is the axis.</span></span> <span data-ttu-id="92ea0-139">`Customer`はノードテストです。がノードの場合は TRUE に `Customer` \<element> なります。</span><span class="sxs-lookup"><span data-stu-id="92ea0-139">`Customer` is the node test (TRUE if `Customer` is an \<element> node).</span></span> <span data-ttu-id="92ea0-140">`not(child::ContactName)` は述語です。</span><span class="sxs-lookup"><span data-stu-id="92ea0-140">`not(child::ContactName)` is the predicate.</span></span> <span data-ttu-id="92ea0-141">述語では、 `child` は軸で、は `ContactName` ノードテストです (がノードの場合は TRUE `ContactName` \<element> )。</span><span class="sxs-lookup"><span data-stu-id="92ea0-141">In the predicate, `child` is the axis and `ContactName` is the node test (TRUE if `ContactName` is an \<element> node).</span></span>  
  
 <span data-ttu-id="92ea0-142">省略構文を使用した場合、XPath クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-142">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a><span data-ttu-id="92ea0-143">選択述語: 例5</span><span class="sxs-lookup"><span data-stu-id="92ea0-143">Selection Predicate: Example 5</span></span>  
 <span data-ttu-id="92ea0-144">次の XPath 式は、現在のコンテキストノードから、 **\<Customer>** **CustomerID**属性を持つすべての子を選択します。</span><span class="sxs-lookup"><span data-stu-id="92ea0-144">The following XPath expression selects from the current context node all the **\<Customer>** children that have the **CustomerID** attribute:</span></span>  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 <span data-ttu-id="92ea0-145">この例では、は軸で、は `child` `Customer` ノードテストです ( `Customer` がノードの場合は TRUE \<element> )。</span><span class="sxs-lookup"><span data-stu-id="92ea0-145">In this example, `child` is the axis and `Customer` is node test (TRUE if `Customer` is an \<element> node).</span></span> <span data-ttu-id="92ea0-146">`attribute::CustomerID` は述語です。</span><span class="sxs-lookup"><span data-stu-id="92ea0-146">`attribute::CustomerID` is the predicate.</span></span> <span data-ttu-id="92ea0-147">述語では、 `attribute` は軸で、は `CustomerID` 述語です ( `CustomerID` がノードの場合は TRUE **\<attribute>** )。</span><span class="sxs-lookup"><span data-stu-id="92ea0-147">In the predicate, `attribute` is the axis and `CustomerID` is the predicate (TRUE if `CustomerID` is an **\<attribute>** node).</span></span>  
  
 <span data-ttu-id="92ea0-148">省略構文を使用した場合、XPath クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-148">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a><span data-ttu-id="92ea0-149">選択述語 : 例 6</span><span class="sxs-lookup"><span data-stu-id="92ea0-149">Selection Predicate: Example 6</span></span>  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="92ea0-150">SQLXML 4.0 では、次の例に示すように、述語にクロス積を含む XPath クエリがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="92ea0-150">SQLXML 4.0 includes support for XPath queries that contain a cross-product in the predicate, as shown in the following example:</span></span>  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 <span data-ttu-id="92ea0-151">このクエリでは、`Order` の `OrderDate` が任意の `ShipDate` の `Order` と等しいすべての顧客が選択されます。</span><span class="sxs-lookup"><span data-stu-id="92ea0-151">This query selects all customers with any `Order` for which the `OrderDate` equals the `ShipDate` of any `Order`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ea0-152">参照</span><span class="sxs-lookup"><span data-stu-id="92ea0-152">See Also</span></span>  
 <span data-ttu-id="92ea0-153">[注釈付き XSD スキーマの概要 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="92ea0-153">[Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="92ea0-154">クライアント側の XML 書式設定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="92ea0-154">Client-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](../../sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
