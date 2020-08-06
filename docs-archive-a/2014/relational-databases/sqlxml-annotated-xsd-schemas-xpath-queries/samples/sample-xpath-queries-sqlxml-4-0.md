---
title: XPath クエリのサンプル (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- examples [SQLXML], XPath
- sample applications [SQLXML]
- sample XPath queries [SQLXML]
- mapping schema [SQLXML], queries
- XPath queries [SQLXML], samples
ms.assetid: 1595c2d4-0e9c-4969-84c8-a793a32df57d
author: rothja
ms.author: jroth
ms.openlocfilehash: 08ed32433e9bed4cc1542d6700ad73dc96f3c2dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631750"
---
# <a name="sample-xpath-queries-sqlxml-40"></a><span data-ttu-id="e9137-102">XPath クエリの例 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e9137-102">Sample XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="e9137-103">ここでは、SQLXML 4.0 の XPath クエリの例を挙げます。</span><span class="sxs-lookup"><span data-stu-id="e9137-103">This section provides examples of XPath queries for SQLXML 4.0.</span></span> <span data-ttu-id="e9137-104">わかりやすくするため、サンプルの XPath クエリはテンプレート内に指定しています。このテンプレートは ADO を使用して実行します。</span><span class="sxs-lookup"><span data-stu-id="e9137-104">For illustration purposes, these example XPath queries are specified in a template executed using ADO.</span></span> <span data-ttu-id="e9137-105">これには、マッピング スキーマ ファイルを使用する必要がありますが、このファイルもここで SampleSchema1.xml として提供します。</span><span class="sxs-lookup"><span data-stu-id="e9137-105">Therefore, you must use a mapping schema file, SampleSchema1.xml, which is also provided in this section.</span></span> <span data-ttu-id="e9137-106">このファイルは、テンプレートと同じディレクトリに保存してください。</span><span class="sxs-lookup"><span data-stu-id="e9137-106">Save this file in the directory where your templates are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e9137-107">サンプルのクエリは、実行する XPath 操作の種類ごとにグループ化されています。</span><span class="sxs-lookup"><span data-stu-id="e9137-107">The sample queries in this section are grouped by the type of XPath operation that is performed by the query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9137-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e9137-108">In This Section</span></span>  
 [<span data-ttu-id="e9137-109">&#40;SQLXML 4.0&#41;の XPath の例の注釈付き XSD スキーマのサンプル</span><span class="sxs-lookup"><span data-stu-id="e9137-109">Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;</span></span>](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-110">このファイルは、ここで説明する XPath クエリのサンプルと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="e9137-110">Use this file with the XPath query examples provided in this section.</span></span>  
  
 [<span data-ttu-id="e9137-111">XPath クエリでの軸の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e9137-111">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-axes-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-112">XPath クエリで軸をどのように指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e9137-112">Illustrates how axes are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e9137-113">XPath クエリでのブール値述語の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e9137-113">Specifying Boolean-Valued Predicates in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-114">XPath クエリでブール値の述語をどのように指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e9137-114">Illustrates how Boolean-valued predicates are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e9137-115">XPath クエリでの関係演算子の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e9137-115">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-116">XPath クエリで関係演算子をどのように指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e9137-116">Illustrates how relational operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e9137-117">XPath クエリでの算術演算子の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e9137-117">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-118">XPath クエリで算術演算子をどのように指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e9137-118">Illustrates how arithmetic operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e9137-119">XPath クエリでの明示的な変換関数の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e9137-119">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-120">XPath クエリで明示的変換関数をどのように指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e9137-120">Illustrates how explicit conversion functions are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e9137-121">XPath クエリでのブール演算子の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e9137-121">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-122">XPath クエリで論理演算子をどのように指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e9137-122">Illustrates how Boolean operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e9137-123">XPath クエリでのブール関数の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e9137-123">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-124">XPath クエリで論理関数をどのように指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e9137-124">Illustrates how Boolean functions are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e9137-125">XPath クエリでの XPath 変数の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e9137-125">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e9137-126">XPath クエリで XPath 変数をどのように指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e9137-126">Illustrates how XPath variables are specified in XPath queries.</span></span>  
  
  
