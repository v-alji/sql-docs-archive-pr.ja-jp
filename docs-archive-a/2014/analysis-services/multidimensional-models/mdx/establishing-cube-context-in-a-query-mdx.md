---
title: クエリでのキューブコンテキストの確立 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72ae6e19f879651feb47841d70b444e9f845c74e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711074"
---
# <a name="establishing-cube-context-in-a-query-mdx"></a><span data-ttu-id="6f92a-102">クエリ内のキューブ コンテキストの確立 (MDX)</span><span class="sxs-lookup"><span data-stu-id="6f92a-102">Establishing Cube Context in a Query (MDX)</span></span>
  <span data-ttu-id="6f92a-103">各 MDX クエリは、指定したキューブ コンテキスト内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="6f92a-103">Every MDX query runs within a specified cube context.</span></span> <span data-ttu-id="6f92a-104">このコンテキストは、クエリ内の式によって評価されるメンバーを定義します。</span><span class="sxs-lookup"><span data-stu-id="6f92a-104">This context defines the members that are evaluated by the expressions within the query.</span></span>  
  
 <span data-ttu-id="6f92a-105">SELECT ステートメントでは、FROM 句によってキューブ コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f92a-105">In the SELECT statement, the FROM clause determines the cube context.</span></span> <span data-ttu-id="6f92a-106">このコンテキストは、キューブ全体の場合もあれば、キューブの中にある 1 つのサブキューブの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6f92a-106">This context can be the whole cube or just a subcube from that cube.</span></span> <span data-ttu-id="6f92a-107">FROM 句によってキューブ コンテキストを指定してから、追加の関数によってそのコンテキストを拡大したり縮小したりすることも可能です。</span><span class="sxs-lookup"><span data-stu-id="6f92a-107">Having specified cube context through the FROM clause, you can use additional functions to expand or restrict that context.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f92a-108">SCOPE ステートメントと CALCULATE ステートメントによって、MDX スクリプト内のキューブ コンテキストを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="6f92a-108">The SCOPE and CALCULATE statements also let you manage cube context from within an MDX script.</span></span> <span data-ttu-id="6f92a-109">詳細については、「[MDX スクリプティングの基礎 (Analysis Services)](mdx-scripting-fundamentals-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f92a-109">For more information, see [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md).</span></span>  
  
## <a name="from-clause-syntax"></a><span data-ttu-id="6f92a-110">FROM 句の構文</span><span class="sxs-lookup"><span data-stu-id="6f92a-110">FROM Clause Syntax</span></span>  
 <span data-ttu-id="6f92a-111">FROM 句の構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6f92a-111">The following syntax describes the FROM clause:</span></span>  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 <span data-ttu-id="6f92a-112">この構文では、 `<SELECT subcube clause>` 句によって、SELECT ステートメントの実行対象にするキューブまたはサブキューブを記述します。</span><span class="sxs-lookup"><span data-stu-id="6f92a-112">In this syntax, notice that it is the `<SELECT subcube clause>` clause that describes the cube or subcube on which the SELECT statement is executed.</span></span>  
  
 <span data-ttu-id="6f92a-113">シンプルな例としては、FROM 句で Adventure Works サンプル キューブ全体を対象として指定する例があります。</span><span class="sxs-lookup"><span data-stu-id="6f92a-113">A simple example of a FROM clause would be one that runs against the entire Adventure Works sample cube.</span></span> <span data-ttu-id="6f92a-114">そのような FROM 句の形式は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6f92a-114">Such a FROM clause would have the following format:</span></span>  
  
```  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="6f92a-115">MDX の SELECT ステートメントで使用する FROM 句の詳細については、「[SELECT ステートメント (MDX)](/sql/mdx/mdx-data-manipulation-select)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f92a-115">For more information about the FROM clause in the MDX SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
## <a name="refining-the-context"></a><span data-ttu-id="6f92a-116">コンテキストの調整</span><span class="sxs-lookup"><span data-stu-id="6f92a-116">Refining the Context</span></span>  
 <span data-ttu-id="6f92a-117">FROM 句ではいずれか 1 つのキューブがキューブ コンテキストとなりますが、複数のキューブのデータを同時に操作できないわけではありません。</span><span class="sxs-lookup"><span data-stu-id="6f92a-117">Although the FROM clause specifies the cube context as within a single cube, this does not have to limit you from working with data from more than one cube at a time.</span></span>  
  
 <span data-ttu-id="6f92a-118">キューブ コンテキストの外部のキューブからデータを取得する場合は、MDX の [LookupCube](/sql/mdx/lookupcube-mdx) 関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6f92a-118">You can use the MDX [LookupCube](/sql/mdx/lookupcube-mdx) function to retrieve data from cubes outside the cube context.</span></span> <span data-ttu-id="6f92a-119">さらに、クエリの評価時にコンテキストを一時的に制限するために、 [Filter](/sql/mdx/filter-mdx) などの関数も用意されています。</span><span class="sxs-lookup"><span data-stu-id="6f92a-119">Additionally, functions such as the [Filter](/sql/mdx/filter-mdx) function, are available that allow temporary restriction of the context while evaluating the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f92a-120">参照</span><span class="sxs-lookup"><span data-stu-id="6f92a-120">See Also</span></span>  
 [<span data-ttu-id="6f92a-121">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f92a-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
