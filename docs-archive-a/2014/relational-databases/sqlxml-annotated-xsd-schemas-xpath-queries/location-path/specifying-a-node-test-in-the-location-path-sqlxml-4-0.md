---
title: ロケーションパスでのノードテストの指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d8535154f4b481c8a47bfdb8b801e3136a1ef0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641549"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a><span data-ttu-id="22732-102">ロケーション パスでのノード テストの指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="22732-102">Specifying a Node Test in the Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="22732-103">ノード テストによって、ロケーション ステップで選択されるノードの型が決まります。</span><span class="sxs-lookup"><span data-stu-id="22732-103">A node test specifies the node type selected by the location step.</span></span> <span data-ttu-id="22732-104">すべての軸 (`child`、`parent`、`attribute`、または `self`) には主ノード型があります。</span><span class="sxs-lookup"><span data-stu-id="22732-104">Every axis (`child`, `parent`, `attribute`, or `self`) has a principal node type.</span></span> <span data-ttu-id="22732-105">軸の場合 `attribute` 、主ノード型は **\<attribute>** です。</span><span class="sxs-lookup"><span data-stu-id="22732-105">For the `attribute` axis, the principal node type is **\<attribute>**.</span></span> <span data-ttu-id="22732-106">`parent`、 `child` 、および軸の場合 `self` 、主ノード型は **\<element>** です。</span><span class="sxs-lookup"><span data-stu-id="22732-106">For the `parent`, `child`, and `self` axes, the principal node type is **\<element>**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22732-107">ワイルドカード (\*) のノード テスト (たとえば `child::*`) は、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="22732-107">The wildcard node test \* (for example, `child::*`) is not supported.</span></span>  
  
## <a name="node-test-example-1"></a><span data-ttu-id="22732-108">ノードテスト: 例1</span><span class="sxs-lookup"><span data-stu-id="22732-108">Node Test: Example 1</span></span>  
 <span data-ttu-id="22732-109">ロケーションパスは `child::Customer` 、 **\<Customer>** コンテキストノードの子要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="22732-109">The location path `child::Customer` selects **\<Customer>** element children of the context node.</span></span>  
  
 <span data-ttu-id="22732-110">この例では、`child` は軸で、`Customer` はノード テストです。</span><span class="sxs-lookup"><span data-stu-id="22732-110">In this example, `child` is the axis and `Customer` is the node test.</span></span> <span data-ttu-id="22732-111">軸の主ノード型 `child` は **\<element>** です。</span><span class="sxs-lookup"><span data-stu-id="22732-111">The principal node type for the `child` axis is **\<element>**.</span></span> <span data-ttu-id="22732-112">したがって、ノードがノードの場合、ノードテストは TRUE になり **\<Customer>** **\<element>** ます。</span><span class="sxs-lookup"><span data-stu-id="22732-112">Therefore, the node test is TRUE if the **\<Customer>** node is an **\<element>** node.</span></span> <span data-ttu-id="22732-113">コンテキストノードに子がない場合 **\<Customer>** は、空のノードセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="22732-113">If the context node has no **\<Customer>** children, an empty set of nodes is returned.</span></span>  
  
## <a name="node-test-example-2"></a><span data-ttu-id="22732-114">ノード テスト : 例 2</span><span class="sxs-lookup"><span data-stu-id="22732-114">Node Test: Example 2</span></span>  
 <span data-ttu-id="22732-115">ロケーションパスによって、 `attribute::CustomerID` コンテキストノードの**CustomerID**属性が選択されます。</span><span class="sxs-lookup"><span data-stu-id="22732-115">The location path `attribute::CustomerID` selects the **CustomerID** attribute of the context node.</span></span>  
  
 <span data-ttu-id="22732-116">この例で `attribute` は、は軸で、 `CustomerID` はノードテストです。</span><span class="sxs-lookup"><span data-stu-id="22732-116">In the example, `attribute` is the axis and `CustomerID` is the node test.</span></span> <span data-ttu-id="22732-117">軸の主ノード型 `attribute` は **\<attribute>** です。</span><span class="sxs-lookup"><span data-stu-id="22732-117">The principal node type of the `attribute` axis is **\<attribute>**.</span></span> <span data-ttu-id="22732-118">このため、 **CustomerID**がノードの場合、ノードテストは TRUE になり **\<attribute>** ます。</span><span class="sxs-lookup"><span data-stu-id="22732-118">Therefore, the node test is TRUE if **CustomerID** is an **\<attribute>** node.</span></span> <span data-ttu-id="22732-119">コンテキストノードに**CustomerID**がない場合は、空のノードセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="22732-119">If the context node has no **CustomerID**, an empty set of nodes is returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22732-120">この XPath の実装では、ロケーションステップがスキーマで宣言されていないまたは型を参照している場合、 **\<element>** **\<attribute>** エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="22732-120">In this implementation of XPath, if a location step refers to an **\<element>** or an **\<attribute>** type that is not declared in the schema, an error is generated.</span></span> <span data-ttu-id="22732-121">これは、空のノード セットを返す MSXML の XPath の実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="22732-121">This is different from the implementation of XPath in MSXML, which returns an empty node set.</span></span>  
  
## <a name="abbreviated-syntax-for-the-axes"></a><span data-ttu-id="22732-122">軸の省略構文</span><span class="sxs-lookup"><span data-stu-id="22732-122">Abbreviated Syntax for the Axes</span></span>  
 <span data-ttu-id="22732-123">ロケーション パスでは、次の省略構文がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="22732-123">The following abbreviated syntax for the location path is supported:</span></span>  
  
-   <span data-ttu-id="22732-124">`attribute::` は `@` で省略できます。</span><span class="sxs-lookup"><span data-stu-id="22732-124">`attribute::` can be abbreviated to `@`.</span></span>  
  
     <span data-ttu-id="22732-125">ロケーション パス `Customer[@CustomerID="ALFKI"]` は、`child::Customer[attribute::CustomerID="ALFKI"]` と同じです。</span><span class="sxs-lookup"><span data-stu-id="22732-125">The location path `Customer[@CustomerID="ALFKI"]` is the same as `child::Customer[attribute::CustomerID="ALFKI"]`.</span></span>  
  
-   <span data-ttu-id="22732-126">ロケーション ステップから `child::` を省略できます。</span><span class="sxs-lookup"><span data-stu-id="22732-126">`child::` can be omitted from a location step.</span></span>  
  
     <span data-ttu-id="22732-127">つまり、`child` は既定の軸です。</span><span class="sxs-lookup"><span data-stu-id="22732-127">Thus, `child` is the default axis.</span></span> <span data-ttu-id="22732-128">ロケーション パス `Customer/Order` は、`child::Customer/child::Order` と同じです。</span><span class="sxs-lookup"><span data-stu-id="22732-128">The location path `Customer/Order` is the same as `child::Customer/child::Order`.</span></span>  
  
-   <span data-ttu-id="22732-129">`self::node()` は 1 つのピリオド (.) で省略できます。また、`parent::node()` は 2 つのピリオド (..) で省略できます。</span><span class="sxs-lookup"><span data-stu-id="22732-129">`self::node()` can be abbreviated to one period (.), and `parent::node()` can be abbreviated to two periods (..).</span></span>  
  
  
