---
title: クエリスコープの名前付きセットの作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6eccb4e20fca03079a04a0219b07f6411b80a433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714638"
---
# <a name="creating-query-scoped-named-sets-mdx"></a><span data-ttu-id="106cb-102">クエリ スコープの名前付きセットの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="106cb-102">Creating Query-Scoped Named Sets (MDX)</span></span>
  <span data-ttu-id="106cb-103">1 つの多次元式 (MDX) クエリでのみ名前付きセットが必要な場合は、WITH キーワードを使用してその名前付きセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="106cb-103">If a named set is only required for a single Multidimensional Expressions (MDX) query, you can define that named set by using the WITH keyword.</span></span> <span data-ttu-id="106cb-104">WITH キーワードを使用して作成した名前付きセットは、そのクエリの実行が終了した時点で存在しなくなります。</span><span class="sxs-lookup"><span data-stu-id="106cb-104">A named set that is created by using the WITH keyword no longer exists after the query has finished running.</span></span>  
  
 <span data-ttu-id="106cb-105">このトピックで説明するように、WITH キーワードの構文は非常に柔軟なので、名前付きセットを定義するための関数も使用できます。</span><span class="sxs-lookup"><span data-stu-id="106cb-105">As discussed in this topic, the syntax of the WITH keyword is quite flexible, even accommodating the use of functions to define the named set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="106cb-106">名前付きセットの詳細については、「[MDX での名前付きセットの作成 &#40;MDX&#41;](mdx-named-sets-building-named-sets.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="106cb-106">For more information about named sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
## <a name="with-keyword-syntax"></a><span data-ttu-id="106cb-107">WITH キーワードの構文</span><span class="sxs-lookup"><span data-stu-id="106cb-107">WITH Keyword Syntax</span></span>  
 <span data-ttu-id="106cb-108">MDX の SELECT ステートメントに WITH キーワードを追加するための構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="106cb-108">Use the following syntax to add the WITH keyword to a MDX SELECT statement:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
   ( SET Set_Identifier AS 'Set_Expression')  
  
```  
  
 <span data-ttu-id="106cb-109">WITH キーワードの構文で使用する `Set_Identifier` パラメーターには、名前付きセットの別名を指定します。</span><span class="sxs-lookup"><span data-stu-id="106cb-109">In the syntax for the WITH keyword, the `Set_Identifier` parameter contains the alias for the named set.</span></span> <span data-ttu-id="106cb-110">`Set_Expression` パラメーターには、名前付きセットの別名が参照するセット式を指定します。</span><span class="sxs-lookup"><span data-stu-id="106cb-110">The `Set_Expression` parameter contains the set expression to which the named set alias refers.</span></span>  
  
## <a name="with-keyword-example"></a><span data-ttu-id="106cb-111">WITH キーワードの例</span><span class="sxs-lookup"><span data-stu-id="106cb-111">WITH Keyword Example</span></span>  
 <span data-ttu-id="106cb-112">以下に示すのは、Microsoft SQL Server 2000 Analysis Services のサンプル データベース `FoodMart 2000` に登録されている Chardonnay ワインと Chablis ワインの売上数量を調べる MDX クエリです。</span><span class="sxs-lookup"><span data-stu-id="106cb-112">The following MDX query examines the unit sales of the various Chardonnay and Chablis wines in `FoodMart 2000`, the sample database for Microsoft SQL Server 2000 Analysis Services.</span></span> <span data-ttu-id="106cb-113">このクエリは、結果セットという観点からすれば非常にシンプルですが、クエリの管理という観点から見ると長すぎて扱いが厄介です。</span><span class="sxs-lookup"><span data-stu-id="106cb-113">This query, although fairly simple in terms of the result set, is lengthy and unwieldy when you have to maintenance such a query.</span></span>  
  
```  
SELECT  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]} ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
 <span data-ttu-id="106cb-114">この MDX クエリを管理しやすくするために、WITH キーワードを使用してこのクエリのための名前付きセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="106cb-114">To make the previous MDX query easier to maintain, you can create a named set for the query by using the WITH keyword.</span></span> <span data-ttu-id="106cb-115">以下に示すのは、WITH キーワードを使用して `[ChardonnayChablis]`という名前付きセットを作成し、その名前付きセットを使用して SELECT ステートメントを短くする方法を示したコードです。</span><span class="sxs-lookup"><span data-stu-id="106cb-115">The following code shows how to use the WITH keyword to create a named set, `[ChardonnayChablis]`, and how the named set makes the SELECT statement shorter and easier to maintain.</span></span>  
  
```  
WITH SET [ChardonnayChablis] AS  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]}  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
### <a name="using-functions-together-with-the-with-keyword"></a><span data-ttu-id="106cb-116">WITH キーワードで関数を使用する方法</span><span class="sxs-lookup"><span data-stu-id="106cb-116">Using Functions Together with the WITH Keyword</span></span>  
 <span data-ttu-id="106cb-117">名前付きセットの各メンバーを明示的に定義することもできますが、その場合はステートメントが長くなってしまうことがあります。</span><span class="sxs-lookup"><span data-stu-id="106cb-117">Although you can explicitly define each member of a named set, this approach can produce a lengthy statement.</span></span> <span data-ttu-id="106cb-118">名前付きセットの作成と管理を簡略化するために、MDX 関数を使用してメンバーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="106cb-118">To make the creation and maintenance of a named set easier, you can use MDX functions to define the members.</span></span>  
  
 <span data-ttu-id="106cb-119">たとえば、次に示す MDX クエリでは、 [Filter](/sql/mdx/filter-mdx)、 [CurrentMember](/sql/mdx/current-mdx)、 [Name](/sql/mdx/members-string-mdx) の各 MDX 関数と VBA の InStr 関数を使用して名前付きセット `[ChardonnayChablis]` を作成しています。</span><span class="sxs-lookup"><span data-stu-id="106cb-119">For example, the following MDX query example uses the [Filter](/sql/mdx/filter-mdx), [CurrentMember](/sql/mdx/current-mdx), and [Name](/sql/mdx/members-string-mdx) MDX functions and the InStr VBA function to create the `[ChardonnayChablis]` named set.</span></span> <span data-ttu-id="106cb-120">この名前付きセット `[ChardonnayChablis]` は、明示的に定義した上記の名前付きセットと同じです。</span><span class="sxs-lookup"><span data-stu-id="106cb-120">This version of the `[ChardonnayChablis]` named set is the same as the explicitly defined version shown previously in this topic.</span></span>  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="106cb-121">参照</span><span class="sxs-lookup"><span data-stu-id="106cb-121">See Also</span></span>  
 <span data-ttu-id="106cb-122">[SELECT ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="106cb-122">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 [<span data-ttu-id="106cb-123">セッション スコープの名前付きセットの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="106cb-123">Creating Session-Scoped Named Sets &#40;MDX&#41;</span></span>](mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  
