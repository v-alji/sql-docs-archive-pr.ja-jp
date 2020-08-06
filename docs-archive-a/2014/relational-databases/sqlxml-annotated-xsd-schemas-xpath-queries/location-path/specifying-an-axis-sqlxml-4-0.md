---
title: 軸の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e43281fe31d323a7eea19e749b80b59458752b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641547"
---
# <a name="specifying-an-axis-sqlxml-40"></a><span data-ttu-id="a807e-102">軸の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a807e-102">Specifying an Axis (SQLXML 4.0)</span></span>
    
-   <span data-ttu-id="a807e-103">軸によって、ロケーション ステップで選択されるノードと、コンテキスト ノードの間のツリー リレーションシップが指定されます。</span><span class="sxs-lookup"><span data-stu-id="a807e-103">The axis specifies the tree relationship between the nodes selected by the location step and the context node.</span></span> <span data-ttu-id="a807e-104">`child` 軸がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a807e-104">The following axes are supported:  `child`</span></span>  
  
     <span data-ttu-id="a807e-105">コンテキスト ノードの子を含みます。</span><span class="sxs-lookup"><span data-stu-id="a807e-105">Contains the child of the context node.</span></span>  
  
     <span data-ttu-id="a807e-106">次の XPath 式 (ロケーションパス) では、現在のコンテキストノードからすべての子が選択され **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="a807e-106">The following XPath expression (location path) selects from the current context node all the **\<Customer>** children:</span></span>  
  
    ```  
    child::Customer  
    ```  
  
     <span data-ttu-id="a807e-107">この XPath クエリでは、`child` は軸で、</span><span class="sxs-lookup"><span data-stu-id="a807e-107">In the following XPath query, `child` is the axis.</span></span> <span data-ttu-id="a807e-108">`Customer` はノード テストです。</span><span class="sxs-lookup"><span data-stu-id="a807e-108">`Customer` is the node test.</span></span>  
  
-   `parent`  
  
     <span data-ttu-id="a807e-109">コンテキスト ノードの親を含みます。</span><span class="sxs-lookup"><span data-stu-id="a807e-109">Contains the parent of the context node.</span></span>  
  
     <span data-ttu-id="a807e-110">次の XPath 式は、子のすべての親を選択し **\<Customer>** **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="a807e-110">The following XPath expression selects all the **\<Customer>** parents of the **\<Order>** children:</span></span>  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     <span data-ttu-id="a807e-111">これは、`child::Customer` を指定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="a807e-111">This is the same as specifying `child::Customer`.</span></span> <span data-ttu-id="a807e-112">この XPath クエリでは、`child` と `parent` は軸で、</span><span class="sxs-lookup"><span data-stu-id="a807e-112">In this XPath query, `child` and `parent` are the axes.</span></span> <span data-ttu-id="a807e-113">`Customer` と `Order` はノード テストです。</span><span class="sxs-lookup"><span data-stu-id="a807e-113">`Customer` and `Order` are the node tests.</span></span>  
  
-   `attribute`  
  
     <span data-ttu-id="a807e-114">コンテキスト ノードの属性を含みます。</span><span class="sxs-lookup"><span data-stu-id="a807e-114">Contains the attribute of the context node.</span></span>  
  
     <span data-ttu-id="a807e-115">次の XPath 式では、コンテキストノードの**CustomerID**属性が選択されます。</span><span class="sxs-lookup"><span data-stu-id="a807e-115">The following XPath expression selects the **CustomerID** attribute of the context node:</span></span>  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     <span data-ttu-id="a807e-116">コンテキスト ノードそのものを含みます。</span><span class="sxs-lookup"><span data-stu-id="a807e-116">Contains the context node itself.</span></span>  
  
     <span data-ttu-id="a807e-117">次の XPath 式は、ノードの場合、現在のノードを選択し **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="a807e-117">The following XPath expression selects the current node if it is the **\<Order>** node:</span></span>  
  
    ```  
    self::Order  
    ```  
  
     <span data-ttu-id="a807e-118">この XPath クエリでは、`self` は軸で、`Order` はノード テストです。</span><span class="sxs-lookup"><span data-stu-id="a807e-118">In this XPath query, `self` is the axis and `Order` is the node test.</span></span>  
  
  
