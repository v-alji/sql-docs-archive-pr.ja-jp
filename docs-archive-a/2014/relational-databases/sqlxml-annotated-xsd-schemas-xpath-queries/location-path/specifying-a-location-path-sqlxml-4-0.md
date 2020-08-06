---
title: ロケーションパスの指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dfa1717afe55c1599ccaba4b5d044c6e5a20e84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641551"
---
# <a name="specifying-a-location-path-sqlxml-40"></a><span data-ttu-id="df927-102">ロケーション パスの指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="df927-102">Specifying a Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="df927-103">XPath クエリは式の形式で指定され、</span><span class="sxs-lookup"><span data-stu-id="df927-103">XPath queries are specified in the form of an expression.</span></span> <span data-ttu-id="df927-104">式の種類にはさまざまなものがあります。</span><span class="sxs-lookup"><span data-stu-id="df927-104">There are various kinds of expressions.</span></span> <span data-ttu-id="df927-105">ロケーション パスは、コンテキスト ノードに相対的なノードのセットを選択する式です。</span><span class="sxs-lookup"><span data-stu-id="df927-105">A location path is an expression that selects a set of nodes relative to the context node.</span></span> <span data-ttu-id="df927-106">ロケーション パスを評価すると、結果はノード セットになります。</span><span class="sxs-lookup"><span data-stu-id="df927-106">The result of evaluating a location path is a node-set.</span></span>  
  
## <a name="types-of-location-paths"></a><span data-ttu-id="df927-107">ロケーション パスの種類</span><span class="sxs-lookup"><span data-stu-id="df927-107">Types of Location Paths</span></span>  
 <span data-ttu-id="df927-108">ロケーション パスは、次のいずれかの形式で指定できます。</span><span class="sxs-lookup"><span data-stu-id="df927-108">A location path can take either of these forms:</span></span>  
  
-   <span data-ttu-id="df927-109">**絶対ロケーション パス**</span><span class="sxs-lookup"><span data-stu-id="df927-109">**Absolute location path**</span></span>  
  
     <span data-ttu-id="df927-110">絶対ロケーション パスは、ドキュメントのルート ノードから開始します。</span><span class="sxs-lookup"><span data-stu-id="df927-110">An absolute location path starts at the root node of the document.</span></span> <span data-ttu-id="df927-111">構成要素はスラッシュ記号 (/) で、その後に相対ロケーション パスを続けることもできます。</span><span class="sxs-lookup"><span data-stu-id="df927-111">It consists of a slash mark (/) optionally followed by a relative location path.</span></span> <span data-ttu-id="df927-112">スラッシュ記号 (/) によって、ドキュメントのルート ノードが選択されます。</span><span class="sxs-lookup"><span data-stu-id="df927-112">The slash mark (/) selects the root node of the document.</span></span>  
  
-   <span data-ttu-id="df927-113">**相対ロケーション パス**</span><span class="sxs-lookup"><span data-stu-id="df927-113">**Relative location path**</span></span>  
  
     <span data-ttu-id="df927-114">相対ロケーション パスは、ドキュメントのコンテキスト ノードから開始します。</span><span class="sxs-lookup"><span data-stu-id="df927-114">A relative location path starts at the context node in the document.</span></span> <span data-ttu-id="df927-115">構成要素は連続する 1 つ以上のロケーション ステップで、区切りにはスラッシュ記号 (/) を使用します。</span><span class="sxs-lookup"><span data-stu-id="df927-115">A location path consists of a sequence of one or more location steps separated by a slash mark (/).</span></span> <span data-ttu-id="df927-116">各ステップで、コンテキスト ノードに対して相対的なノードのセットが選択されます。</span><span class="sxs-lookup"><span data-stu-id="df927-116">Each step selects a set of nodes relative to the context node.</span></span> <span data-ttu-id="df927-117">最初のステップでは、コンテキスト ノードに対して相対的なノードのセットが選択され、</span><span class="sxs-lookup"><span data-stu-id="df927-117">The initial sequence of steps selects a set of nodes relative to a context node.</span></span> <span data-ttu-id="df927-118">そのセットの各ノードが次のステップのコンテキスト ノードとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="df927-118">Each node in that set is used as a context node for the following step.</span></span> <span data-ttu-id="df927-119">そのステップで指定されたノードのセットは結合されます。</span><span class="sxs-lookup"><span data-stu-id="df927-119">The sets of nodes identified by that step are joined.</span></span> <span data-ttu-id="df927-120">たとえば、 **child:: Order/child:: OrderDetail**は、 **\<OrderDetail>** **\<Order>** コンテキストノードの子要素の子要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="df927-120">For example, **child::Order/child::OrderDetail** selects the **\<OrderDetail>** element children of the **\<Order>** element children of the context node.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="df927-121">SQLXML 4.0 における XPath の実装では、XPath が明示的に絶対として指定されていない場合でも、各 XPath クエリはルート コンテキストから開始します。</span><span class="sxs-lookup"><span data-stu-id="df927-121">In the SQLXML 4.0 implementation of XPath, every XPath query begins at the root context, even if the XPath is not explicitly absolute.</span></span> <span data-ttu-id="df927-122">たとえば、"Customer" で開始する XPath クエリは "/Customer" として扱われます。</span><span class="sxs-lookup"><span data-stu-id="df927-122">For example, an XPath query beginning with "Customer" is treated as "/Customer".</span></span> <span data-ttu-id="df927-123">XPath クエリの**customer [Order]** では、顧客はルートコンテキストから開始しますが、注文は顧客のコンテキストで開始されます。</span><span class="sxs-lookup"><span data-stu-id="df927-123">In the XPath query **Customer[Order]**, Customer begins at the root context, but Order begins at the Customer context.</span></span> <span data-ttu-id="df927-124">詳細については、「 [XPath クエリの使用の概要 &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df927-124">For more information, see [Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).</span></span>  
  
## <a name="location-steps"></a><span data-ttu-id="df927-125">ロケーション ステップ</span><span class="sxs-lookup"><span data-stu-id="df927-125">Location Steps</span></span>  
 <span data-ttu-id="df927-126">ロケーション パス (絶対または相対) は、次の 3 つの部分から成るロケーション ステップで構成されます。</span><span class="sxs-lookup"><span data-stu-id="df927-126">A location path (absolute or relative) is composed of location steps that contain three parts:</span></span>  
  
-   <span data-ttu-id="df927-127">**軸**</span><span class="sxs-lookup"><span data-stu-id="df927-127">**Axis**</span></span>  
  
     <span data-ttu-id="df927-128">軸によって、ロケーション ステップで選択されるノードと、コンテキスト ノードの間のツリー リレーションシップが指定されます。</span><span class="sxs-lookup"><span data-stu-id="df927-128">The axis specifies the tree relationship between the nodes selected by the location step and the context node.</span></span> <span data-ttu-id="df927-129">サポートされる軸は、`parent`、`child`、`attribute`、および `self` 軸です。</span><span class="sxs-lookup"><span data-stu-id="df927-129">The `parent`, `child`, `attribute`, and `self` axes are supported.</span></span> <span data-ttu-id="df927-130">ロケーション パスに `child` 軸を指定した場合、クエリで選択されるすべてのノードはコンテキスト ノードの子です。</span><span class="sxs-lookup"><span data-stu-id="df927-130">If a `child` axis is specified in the location path, all the nodes selected by the query are the children of the context node.</span></span> <span data-ttu-id="df927-131">`parent` 軸を指定した場合、選択されるノードはコンテキスト ノードの親ノードです。</span><span class="sxs-lookup"><span data-stu-id="df927-131">If a `parent` axis is specified, the node selected is the parent node of the context node.</span></span> <span data-ttu-id="df927-132">`attribute` 軸を指定した場合、選択されるノードはコンテキスト ノードの属性です。</span><span class="sxs-lookup"><span data-stu-id="df927-132">If an `attribute` axis is specified, the nodes selected are the attributes of the context node.</span></span>  
  
-   <span data-ttu-id="df927-133">**ノードテスト**</span><span class="sxs-lookup"><span data-stu-id="df927-133">**Node test**</span></span>  
  
     <span data-ttu-id="df927-134">ノード テストによって、ロケーション ステップで選択されるノードの型が決まります。</span><span class="sxs-lookup"><span data-stu-id="df927-134">A node test specifies the node type selected by the location step.</span></span> <span data-ttu-id="df927-135">すべての軸 (`child`、`parent`、`attribute`、および `self`) には主ノード型があります。</span><span class="sxs-lookup"><span data-stu-id="df927-135">Every axis (`child`, `parent`, `attribute`, and `self`) has a principal node type.</span></span> <span data-ttu-id="df927-136">軸の場合 `attribute` 、主ノード型は **\<attribute>** です。</span><span class="sxs-lookup"><span data-stu-id="df927-136">For the `attribute` axis, the principal node type is **\<attribute>**.</span></span> <span data-ttu-id="df927-137">`parent`、 `child` 、および軸の場合 `self` 、主ノード型は **\<element>** です。</span><span class="sxs-lookup"><span data-stu-id="df927-137">For the `parent`, `child`, and `self` axes, the principal node type is **\<element>**.</span></span>  
  
     <span data-ttu-id="df927-138">たとえば、ロケーションパスで**child:: Customer**を指定すると、 **\<Customer>** コンテキストノードの子要素が選択されます。</span><span class="sxs-lookup"><span data-stu-id="df927-138">For example, if the location path specifies **child::Customer**, the **\<Customer>** element children of the context node are selected.</span></span> <span data-ttu-id="df927-139">軸は `child` **\<element>** 主ノード型であるため、customer がノードの場合、ノードテスト CUSTOMER は TRUE になり **\<element>** ます。</span><span class="sxs-lookup"><span data-stu-id="df927-139">Because the `child` axis has **\<element>** as its principal node type, the node test, Customer, is TRUE if Customer is an **\<element>** node.</span></span>  
  
-   <span data-ttu-id="df927-140">**選択述語 (0 以上)**</span><span class="sxs-lookup"><span data-stu-id="df927-140">**Selection predicates (zero or more)**</span></span>  
  
     <span data-ttu-id="df927-141">述語では、軸に関してノード セットをフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="df927-141">A predicate filters a node-set with respect to an axis.</span></span> <span data-ttu-id="df927-142">XPath 式内に選択述語を指定するときには、SELECT ステートメント内に WHERE 句を指定するときのように、</span><span class="sxs-lookup"><span data-stu-id="df927-142">Specifying selection predicates in an XPath expression is similar to specifying a WHERE clause in a SELECT statement.</span></span> <span data-ttu-id="df927-143">述語はかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="df927-143">The predicate is specified between brackets.</span></span> <span data-ttu-id="df927-144">選択述語に指定したテストを適用すると、そのノード テストによって返されたノードがフィルター選択されます。</span><span class="sxs-lookup"><span data-stu-id="df927-144">Applying the test specified in the selection predicates filters the nodes returned by the node test.</span></span> <span data-ttu-id="df927-145">フィルター選択されたノード セットの各ノードに対し、ノードをコンテキスト ノード、ノード セット内のノード数をコンテキストのサイズとして、述語式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="df927-145">For each node in the node-set to be filtered, the predicate expression is evaluated with that node as the context node, with the number of nodes in the node-set as context size.</span></span> <span data-ttu-id="df927-146">述語式が TRUE と評価された場合、そのノードは結果のノード セットに含められます。</span><span class="sxs-lookup"><span data-stu-id="df927-146">If the predicate expression evaluates to TRUE for that node, the node is included in the resulting node-set.</span></span>  
  
     <span data-ttu-id="df927-147">ロケーション ステップの構文では、軸名とノード テストを 2 つのコロン (::) で区切り、その後に式をそれぞれ角かっこで囲んで指定します。式は指定しなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="df927-147">The syntax for a location step is the axis name and node test separated by two colons (::), followed by zero or more expressions, each in square brackets.</span></span> <span data-ttu-id="df927-148">たとえば、XPath 式 (ロケーションパス) に**child:: Customer [ @CustomerID = ' ALFKI ']** と指定すると、 **\<Customer>** コンテキストノードの子要素がすべて選択されます。</span><span class="sxs-lookup"><span data-stu-id="df927-148">For example, the XPath expression (location path) **child::Customer[@CustomerID='ALFKI']** selects all the **\<Customer>** element children of the context node.</span></span> <span data-ttu-id="df927-149">次に、述語内のテストがノードセットに適用されます。これに **\<Customer>** より、 **CustomerID**属性の属性値が ' ALFKI ' の要素ノードのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="df927-149">Then the test in the predicate is applied to the node-set, which returns only the **\<Customer>** element nodes with attribute value 'ALFKI' for its **CustomerID** attribute.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df927-150">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="df927-150">In This Section</span></span>  
 [<span data-ttu-id="df927-151">&#40;SQLXML 4.0&#41;の軸の指定</span><span class="sxs-lookup"><span data-stu-id="df927-151">Specifying an Axis &#40;SQLXML 4.0&#41;</span></span>](specifying-an-axis-sqlxml-4-0.md)  
 <span data-ttu-id="df927-152">軸を指定する例を示します。</span><span class="sxs-lookup"><span data-stu-id="df927-152">Provides examples of specifying an axis.</span></span>  
  
 [<span data-ttu-id="df927-153">Location パスでのノードテストの指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="df927-153">Specifying a Node Test in the Location Path &#40;SQLXML 4.0&#41;</span></span>](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="df927-154">ノード テストを指定する例を示します。</span><span class="sxs-lookup"><span data-stu-id="df927-154">Provides examples of specifying a node test.</span></span>  
  
 [<span data-ttu-id="df927-155">Location パスでの選択述語の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="df927-155">Specifying Selection Predicates in the Location Path &#40;SQLXML 4.0&#41;</span></span>](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="df927-156">選択述語を指定する例を示します。</span><span class="sxs-lookup"><span data-stu-id="df927-156">Provides examples of specifying selection predicates.</span></span>  
  
  
