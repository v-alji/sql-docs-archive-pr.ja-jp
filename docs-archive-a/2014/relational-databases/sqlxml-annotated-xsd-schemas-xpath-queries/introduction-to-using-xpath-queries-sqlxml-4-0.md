---
title: XPath クエリの使用の概要 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
author: rothja
ms.author: jroth
ms.openlocfilehash: dd173f16ee0e97dac1c45039f75022bbf2dc0782
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631766"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a><span data-ttu-id="93857-102">XPath クエリの使用について (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="93857-102">Introduction to Using XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="93857-103">XML パス言語 (XPath) クエリは、URL の一部として、またはテンプレート内で指定できます。</span><span class="sxs-lookup"><span data-stu-id="93857-103">An XML Path Language (XPath) query can be specified as part of a URL or within a template.</span></span> <span data-ttu-id="93857-104">この結果のフラグメントの構造はマッピング スキーマによって決定され、値はデータベースから取得されます。</span><span class="sxs-lookup"><span data-stu-id="93857-104">The mapping schema determines the structure of this resulting fragment, and the values are retrieved from the database.</span></span> <span data-ttu-id="93857-105">このプロセスは、CREATE VIEW ステートメントを使用してビューを作成し、そのビューに対して SQL クエリを記述するのと概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="93857-105">This process is conceptually similar to creating views using the CREATE VIEW statement and writing SQL queries against them.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93857-106">SQLXML 4.0 の XPath クエリを理解するには、XML ビューと、それに関連するテンプレートやマッピング スキーマなどの概念について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="93857-106">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="93857-107">詳細については、「 [&#40;SQLXML 4.0&#41;の注釈付き XSD スキーマの概要](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)」および「WORLD WIDE WEB コンソーシアム (W3C) で定義されている XPath 標準」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93857-107">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md), and the XPath standard defined by the World Wide Web Consortium (W3C).</span></span>  
  
 <span data-ttu-id="93857-108">XML ドキュメントは、要素ノード、属性ノード、テキスト ノードなどのノードで構成されます。</span><span class="sxs-lookup"><span data-stu-id="93857-108">An XML document consists of nodes such as an element node, attribute node, text node, and so on.</span></span> <span data-ttu-id="93857-109">たとえば、次の XML ドキュメントを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="93857-109">For example, consider this XML document:</span></span>  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 <span data-ttu-id="93857-110">このドキュメントで **\<Customer>** は、が要素ノード、 **cid**が属性ノード、 **"Important"** がテキストノードです。</span><span class="sxs-lookup"><span data-stu-id="93857-110">In this document, **\<Customer>** is an element node, **cid** is an attribute node, and **"Important"** is a text node.</span></span>  
  
 <span data-ttu-id="93857-111">XPath は、XML ドキュメントからノード セットを選択するときに使用できるグラフ ナビゲーション言語です。</span><span class="sxs-lookup"><span data-stu-id="93857-111">XPath is a graph navigation language used to select a set of nodes from an XML document.</span></span> <span data-ttu-id="93857-112">XPath の各演算子では、前の XPath 演算子によって選択されたノード セットに基づいて、ノード セットを選択します。</span><span class="sxs-lookup"><span data-stu-id="93857-112">Each XPath operator selects a node-set based on a node-set selected by a previous XPath operator.</span></span> <span data-ttu-id="93857-113">たとえば、ノードのセットがある場合、 **\<Customer>** XPath は **\<Order>** **date**属性値が **"7/14/1999"** であるすべてのノードを選択できます。</span><span class="sxs-lookup"><span data-stu-id="93857-113">For example, given a set of **\<Customer>** nodes, XPath can select all **\<Order>** nodes with the **date** attribute value of **"7/14/1999"**.</span></span> <span data-ttu-id="93857-114">結果のノード セットには、注文日が 1999 年 7 月 14 日となっているすべての注文が含まれます。</span><span class="sxs-lookup"><span data-stu-id="93857-114">The resulting node-set contains all the orders with order date 7/14/1999.</span></span>  
  
 <span data-ttu-id="93857-115">XPath 言語は W3C (World Wide Web Consortium) によって標準のナビゲーション言語として定義されています。</span><span class="sxs-lookup"><span data-stu-id="93857-115">The XPath language is defined by the World Wide Web Consortium (W3C) as a standard navigation language.</span></span> <span data-ttu-id="93857-116">SQLXML 4.0 は、W3C XPath 仕様のサブセットを実装します。このサブセットは、にあり http://www.w3.org/TR/1999/PR-xpath-19991008.html ます。</span><span class="sxs-lookup"><span data-stu-id="93857-116">SQLXML 4.0 implements a subset of the W3C XPath specification, which is located at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="93857-117">次に、W3C XPath 実装と SQLXML 4.0 実装の主な違いを示します。</span><span class="sxs-lookup"><span data-stu-id="93857-117">The following are key differences between the W3C XPath implementation and the SQLXML 4.0 implementation.</span></span>  
  
-   <span data-ttu-id="93857-118">**ルート クエリ**</span><span class="sxs-lookup"><span data-stu-id="93857-118">**Root queries**</span></span>  
  
     <span data-ttu-id="93857-119">SQLXML 4.0 では、ルート クエリ (/) はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="93857-119">SQLXML 4.0 does not support the root query (/).</span></span> <span data-ttu-id="93857-120">すべての XPath クエリは、スキーマの最上位レベルから開始する必要があり **\<ElementType>** ます。</span><span class="sxs-lookup"><span data-stu-id="93857-120">Every XPath query must begin at a top-level **\<ElementType>** in the schema.</span></span>  
  
-   <span data-ttu-id="93857-121">**エラーの報告**</span><span class="sxs-lookup"><span data-stu-id="93857-121">**Reporting errors**</span></span>  
  
     <span data-ttu-id="93857-122">W3C XPath 仕様では、エラー状態は定義されていません。</span><span class="sxs-lookup"><span data-stu-id="93857-122">The W3C XPath specification defines no error conditions.</span></span> <span data-ttu-id="93857-123">ノードの選択に失敗した XPath クエリでは、空のノード セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="93857-123">XPath queries that fail to select any nodes return an empty node-set.</span></span> <span data-ttu-id="93857-124">SQLXML 4.0 では、さまざまな種類のエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="93857-124">In SQLXML 4.0, a query can return many types of error messages.</span></span>  
  
-   <span data-ttu-id="93857-125">**ドキュメント順**</span><span class="sxs-lookup"><span data-stu-id="93857-125">**Document order**</span></span>  
  
     <span data-ttu-id="93857-126">SQL XML 4.0 では、ドキュメント序数が必ずしも決まっていません。</span><span class="sxs-lookup"><span data-stu-id="93857-126">In SQLXML 4.0, document order is not always determined.</span></span> <span data-ttu-id="93857-127">このため、`following` などのドキュメント序数を使用する数値型の述語や軸は実装されていません。</span><span class="sxs-lookup"><span data-stu-id="93857-127">Therefore, numeric predicates and axes that use document order (such as `following`) are not implemented.</span></span>  
  
     <span data-ttu-id="93857-128">ドキュメント序数がないため、ノードの文字列値は、ノードが単一行の単一列にマップされる場合にのみ評価できます。</span><span class="sxs-lookup"><span data-stu-id="93857-128">The lack of document order also means that the string value of a node can be evaluated only when that node maps to a single column in a single row.</span></span> <span data-ttu-id="93857-129">子要素を含む要素や IDREFS または NMTOKENS ノードは、文字列に変換できません。</span><span class="sxs-lookup"><span data-stu-id="93857-129">An element with child elements or an IDREFS or NMTOKENS node cannot be converted to string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="93857-130">場合によっては、`key-fields` 注釈、または `relationship` 注釈のキーから、決定的なドキュメント序数が得られますが、</span><span class="sxs-lookup"><span data-stu-id="93857-130">In some cases, the `key-fields` annotation or keys from the `relationship` annotation can result in a deterministic document order.</span></span> <span data-ttu-id="93857-131">ただし、これはこれらの注釈を主に使用することではありません。詳細については、「 [sql: キーフィールドを使用したキー列の識別 &#40;sqlxml 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) 」と「 [sql:&#41;4.0 &#40;Relationship を使用したリレーションシップの指定](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93857-131">However, this is not the primary use of these annotations For more information, see [Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) and [Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="93857-132">**データ型**</span><span class="sxs-lookup"><span data-stu-id="93857-132">**Data types**</span></span>  
  
     <span data-ttu-id="93857-133">SQLXML 4.0 には、XPath の `string`、`number`、および `boolean` 型の実装に関して制限があります。</span><span class="sxs-lookup"><span data-stu-id="93857-133">SQLXML 4.0 has limitations in implementing the XPath `string`, `number`, and `boolean` data types.</span></span> <span data-ttu-id="93857-134">詳細については、「 [XPath データ型 &#40;SQLXML 4.0&#41;](xpath-data-types-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93857-134">For more information, see [XPath Data Types &#40;SQLXML 4.0&#41;](xpath-data-types-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="93857-135">**クロス積クエリ**</span><span class="sxs-lookup"><span data-stu-id="93857-135">**Cross-product queries**</span></span>  
  
     <span data-ttu-id="93857-136">SQLXML 4.0 では、`Customers[Order/@OrderDate=Order/@ShipDate]` などのクロス積 XPath クエリはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="93857-136">SQLXML 4.0 does not support cross-product XPath queries, such as `Customers[Order/@OrderDate=Order/@ShipDate]`.</span></span> <span data-ttu-id="93857-137">このクエリでは、任意の Order の OrderDate が任意の Order の ShipDate と等しいすべての Customer が選択されます。</span><span class="sxs-lookup"><span data-stu-id="93857-137">This query selects all Customers with any Order for which the OrderDate equals the ShipDate of any Order.</span></span>  
  
     <span data-ttu-id="93857-138">ただし、SQLXML 4.0 では、`Customer[Order[@OrderDate=@ShippedDate]]` などのクエリはサポートされます。このクエリでは、任意の Order の OrderDate とその ShipDate が等しいすべての Customer が選択されます。</span><span class="sxs-lookup"><span data-stu-id="93857-138">However, SQLXML 4.0 does support queries such as `Customer[Order[@OrderDate=@ShippedDate]]`, which selects Customers with any Order for which the OrderDate equals its ShipDate.</span></span>  
  
-   <span data-ttu-id="93857-139">**エラー処理とセキュリティ**</span><span class="sxs-lookup"><span data-stu-id="93857-139">**Error handling and security**</span></span>  
  
     <span data-ttu-id="93857-140">使用されるスキーマと XPath クエリ式によっては、一定の条件下において、[!INCLUDE[tsql](../../includes/tsql-md.md)] エラーがユーザーに表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="93857-140">Depending on the schema and XPath query expression that are used, [!INCLUDE[tsql](../../includes/tsql-md.md)] errors could be exposed to users under certain conditions.</span></span>  
  
 <span data-ttu-id="93857-141">以下に示す表では、この分野に関する SQLXML 4.0 の XPath クエリの実装と W3C 仕様の違いを詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="93857-141">The tables in the following sections provide details about how the implementation of XPath queries in SQLXML 4.0 differs from the W3C specification in these areas.</span></span>  
  
## <a name="supported-functionality"></a><span data-ttu-id="93857-142">サポートされる機能</span><span class="sxs-lookup"><span data-stu-id="93857-142">Supported Functionality</span></span>  
 <span data-ttu-id="93857-143">次の表は、SQLXML 4.0 で実装されている XPath 言語の機能です。</span><span class="sxs-lookup"><span data-stu-id="93857-143">The following table shows the features of the XPath language that are implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="93857-144">特徴量</span><span class="sxs-lookup"><span data-stu-id="93857-144">Feature</span></span>|<span data-ttu-id="93857-145">Item</span><span class="sxs-lookup"><span data-stu-id="93857-145">Item</span></span>|<span data-ttu-id="93857-146">サンプル クエリへのリンク</span><span class="sxs-lookup"><span data-stu-id="93857-146">Link to sample queries</span></span>|  
|-------------|----------|----------------------------|  
|<span data-ttu-id="93857-147">軸</span><span class="sxs-lookup"><span data-stu-id="93857-147">Axes</span></span>|<span data-ttu-id="93857-148">`attribute`、`child`、`parent`、`self` 軸</span><span class="sxs-lookup"><span data-stu-id="93857-148">`attribute`, `child`, `parent`, and `self` axes</span></span>|[<span data-ttu-id="93857-149">XPath クエリでの軸の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="93857-149">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="93857-150">連続する述語や入れ子になった述語など、ブール値を使用する述語</span><span class="sxs-lookup"><span data-stu-id="93857-150">Boolean-valued predicates including successive and nested predicates</span></span>||[<span data-ttu-id="93857-151">XPath クエリでの算術演算子の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="93857-151">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="93857-152">すべての関係演算子</span><span class="sxs-lookup"><span data-stu-id="93857-152">All relational operators</span></span>|<span data-ttu-id="93857-153">=、! =、<、 \<=, > 、>=</span><span class="sxs-lookup"><span data-stu-id="93857-153">=, !=, <, \<=, >, >=</span></span>|[<span data-ttu-id="93857-154">XPath クエリでの関係演算子の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="93857-154">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="93857-155">算術演算子</span><span class="sxs-lookup"><span data-stu-id="93857-155">Arithmetic operators</span></span>|<span data-ttu-id="93857-156">+、-、\*、div</span><span class="sxs-lookup"><span data-stu-id="93857-156">+, -, \*, div</span></span>|[<span data-ttu-id="93857-157">XPath クエリでの算術演算子の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="93857-157">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="93857-158">明示的な変換関数</span><span class="sxs-lookup"><span data-stu-id="93857-158">Explicit conversion functions</span></span>|<span data-ttu-id="93857-159">`number()`, `string()`, `Boolean()`</span><span class="sxs-lookup"><span data-stu-id="93857-159">`number()`, `string()`, `Boolean()`</span></span>|[<span data-ttu-id="93857-160">XPath クエリでの明示的な変換関数の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="93857-160">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="93857-161">ブール演算子</span><span class="sxs-lookup"><span data-stu-id="93857-161">Boolean operators</span></span>|<span data-ttu-id="93857-162">AND、OR</span><span class="sxs-lookup"><span data-stu-id="93857-162">AND, OR</span></span>|[<span data-ttu-id="93857-163">XPath クエリでのブール演算子の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="93857-163">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="93857-164">Boolean 関数群</span><span class="sxs-lookup"><span data-stu-id="93857-164">Boolean functions</span></span>|<span data-ttu-id="93857-165">`true()`, `false()`, `not()`</span><span class="sxs-lookup"><span data-stu-id="93857-165">`true()`, `false()`, `not()`</span></span>|[<span data-ttu-id="93857-166">XPath クエリでのブール関数の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="93857-166">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="93857-167">XPath 変数</span><span class="sxs-lookup"><span data-stu-id="93857-167">XPath variables</span></span>||[<span data-ttu-id="93857-168">XPath クエリでの XPath 変数の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="93857-168">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a><span data-ttu-id="93857-169">サポートされていない機能</span><span class="sxs-lookup"><span data-stu-id="93857-169">Unsupported Functionality</span></span>  
 <span data-ttu-id="93857-170">次の表は、SQLXML 4.0 で実装されていない XPath 言語の機能です。</span><span class="sxs-lookup"><span data-stu-id="93857-170">The following table shows the features of the XPath language that are not implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="93857-171">特徴量</span><span class="sxs-lookup"><span data-stu-id="93857-171">Feature</span></span>|<span data-ttu-id="93857-172">Item</span><span class="sxs-lookup"><span data-stu-id="93857-172">Item</span></span>|  
|-------------|----------|  
|<span data-ttu-id="93857-173">軸</span><span class="sxs-lookup"><span data-stu-id="93857-173">Axes</span></span>|<span data-ttu-id="93857-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="93857-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="93857-175">数値を使用する述語</span><span class="sxs-lookup"><span data-stu-id="93857-175">Numeric-valued predicates</span></span>||  
|<span data-ttu-id="93857-176">算術演算子</span><span class="sxs-lookup"><span data-stu-id="93857-176">Arithmetic operators</span></span>|<span data-ttu-id="93857-177">mod</span><span class="sxs-lookup"><span data-stu-id="93857-177">mod</span></span>|  
|<span data-ttu-id="93857-178">ノード関数</span><span class="sxs-lookup"><span data-stu-id="93857-178">Node functions</span></span>|<span data-ttu-id="93857-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="93857-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="93857-180">文字列関数</span><span class="sxs-lookup"><span data-stu-id="93857-180">String functions</span></span>|<span data-ttu-id="93857-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span><span class="sxs-lookup"><span data-stu-id="93857-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span></span>|  
|<span data-ttu-id="93857-182">Boolean 関数群</span><span class="sxs-lookup"><span data-stu-id="93857-182">Boolean functions</span></span>|`lang()`|  
|<span data-ttu-id="93857-183">数値関数</span><span class="sxs-lookup"><span data-stu-id="93857-183">Numeric functions</span></span>|<span data-ttu-id="93857-184">`sum()`, `floor()`, `ceiling()`, `round()`</span><span class="sxs-lookup"><span data-stu-id="93857-184">`sum()`, `floor()`, `ceiling()`, `round()`</span></span>|  
|<span data-ttu-id="93857-185">Union 演算子</span><span class="sxs-lookup"><span data-stu-id="93857-185">Union operator</span></span>|<span data-ttu-id="93857-186">&#124;</span><span class="sxs-lookup"><span data-stu-id="93857-186">&#124;</span></span>|  
  
 <span data-ttu-id="93857-187">テンプレートに XPath クエリを指定する場合には、次の動作に注意してください。</span><span class="sxs-lookup"><span data-stu-id="93857-187">When you specify XPath queries in a template, note the following behavior:</span></span>  
  
-   <span data-ttu-id="93857-188">XPath には、XML で特別な意味を持つ < や & などの文字を含めることができます (およびテンプレートは XML ドキュメントです)。</span><span class="sxs-lookup"><span data-stu-id="93857-188">XPath can contain characters such as < or & that have special meanings in XML (and template is an XML document).</span></span> <span data-ttu-id="93857-189">XML & エンコードを使用してこれらの文字をエスケープするか、URL に XPath を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93857-189">You must escape these characters using XML &-encoding, or specify the XPath in the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93857-190">参照</span><span class="sxs-lookup"><span data-stu-id="93857-190">See Also</span></span>  
 [<span data-ttu-id="93857-191">SQLXML 4.0 での XPath クエリの使用</span><span class="sxs-lookup"><span data-stu-id="93857-191">Using XPath Queries in SQLXML 4.0</span></span>](using-xpath-queries-in-sqlxml-4-0.md)  
  
  
