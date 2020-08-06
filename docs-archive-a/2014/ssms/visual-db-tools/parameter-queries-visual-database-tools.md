---
title: パラメーター クエリ (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- parameter queries [SQL Server]
ms.assetid: 4897c41a-324a-47b8-a30b-cbc9e9e19a8b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f6fd94ef180a34ae91d52c213092898612dc77d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642457"
---
# <a name="parameter-queries-visual-database-tools"></a><span data-ttu-id="90192-102">パラメーター クエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="90192-102">Parameter Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="90192-103">値を変えるだけで、繰り返し利用できるクエリを作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="90192-103">In some cases you want to create a query that you can use many times, but with a different value each time.</span></span> <span data-ttu-id="90192-104">たとえば、ある著者によって書かれたすべての `title_ids` を検索するクエリを頻繁に実行するような場合です。</span><span class="sxs-lookup"><span data-stu-id="90192-104">For example, you might frequently run a query to find all the `title_ids` written by one author.</span></span> <span data-ttu-id="90192-105">著者の ID または名前を変更するだけで、要求のたびに同じクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="90192-105">You could run the same query for each request, except that the author's ID or name would be different each time.</span></span>  
  
 <span data-ttu-id="90192-106">値を変更できるクエリを作成するには、クエリでパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="90192-106">To create a query that can have different values at different times, you use parameters in the query.</span></span> <span data-ttu-id="90192-107">パラメーターとは、クエリの実行時に与えられる値のプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="90192-107">A parameter is a placeholder for a value that is supplied when the query runs.</span></span> <span data-ttu-id="90192-108">パラメーターを含む SQL ステートメントの例を次に示します。"?" は、著者の ID を表すパラメーターを示します。</span><span class="sxs-lookup"><span data-stu-id="90192-108">An SQL statement with a parameter might look like the following, where "?" represents the parameter for the author's ID:</span></span>  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
## <a name="where-you-can-use-parameters"></a><span data-ttu-id="90192-109">パラメーターの使用例</span><span class="sxs-lookup"><span data-stu-id="90192-109">Where You Can Use Parameters</span></span>  
 <span data-ttu-id="90192-110">パラメーターは、リテラル値 (文字列または数値) のプレースホルダーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="90192-110">You can use parameters as placeholders for literal values - for either text or numeric values.</span></span> <span data-ttu-id="90192-111">最も一般的には、パラメーターは個別の行またはグループに対する検索条件のプレースホルダーとして、つまり SQL ステートメントの WHERE 句または HAVING 句内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="90192-111">Most commonly, parameters are used as placeholders in search conditions for individual rows or for groups (that is, in the WHERE or HAVING clauses of an SQL statement).</span></span>  
  
 <span data-ttu-id="90192-112">式の中でプレースホルダーとしてパラメーターを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="90192-112">You can use parameters as placeholders in expressions.</span></span> <span data-ttu-id="90192-113">たとえば、クエリを実行するたびに異なる割引き値を指定して、割引き価格を計算できます。</span><span class="sxs-lookup"><span data-stu-id="90192-113">For example, you might want to calculate discounted prices by supplying a different discount value each time you run a query.</span></span> <span data-ttu-id="90192-114">この計算は、次の式で行います。</span><span class="sxs-lookup"><span data-stu-id="90192-114">To do so, you could specify the following expression:</span></span>  
  
```  
(price * ?)  
```  
  
## <a name="specifying-unnamed-and-named-parameters"></a><span data-ttu-id="90192-115">無名パラメーターと名前付きパラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="90192-115">Specifying Unnamed and Named Parameters</span></span>  
 <span data-ttu-id="90192-116">指定できるパラメーターは、無名パラメーターと名前付きパラメーターの 2 種類です。</span><span class="sxs-lookup"><span data-stu-id="90192-116">You can specify two types of parameters: unnamed and named.</span></span> <span data-ttu-id="90192-117">無名パラメーターは疑問符 (?) です。リテラル値の入力を要求する、またはリテラル値を代入するクエリ内の任意の位置に挿入できます。</span><span class="sxs-lookup"><span data-stu-id="90192-117">An unnamed parameter is a question mark (?) that you put anywhere in the query that you want to prompt for or substitute a literal value.</span></span> <span data-ttu-id="90192-118">たとえば、無名パラメーターを使って `titleauthor` テーブルで著者の ID を検索する場合は、 [SQL ペイン](visual-database-tools.md) に次のようなステートメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="90192-118">For example, if you use an unnamed parameter to search for an author's id in the `titleauthor` table, the resulting statement in the [SQL Pane](visual-database-tools.md) might look like this:</span></span>  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
 <span data-ttu-id="90192-119">[クエリおよびビュー デザイナー](query-and-view-designer-tools-visual-database-tools.md)でこのクエリを実行すると、 [[クエリ パラメーター] ダイアログ ボックス](query-parameters-dialog-box-visual-database-tools.md) にパラメーター名として "?" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="90192-119">When you run the query in the [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md), the [Query Parameters Dialog Box](query-parameters-dialog-box-visual-database-tools.md) appears with "?" as the name of the parameter.</span></span>  
  
 <span data-ttu-id="90192-120">パラメーターに名前を割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="90192-120">Alternatively, you can assign a name to a parameter.</span></span> <span data-ttu-id="90192-121">名前付きパラメーターは、クエリに複数のパラメーターがある場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="90192-121">Named parameters are particularly useful if you have multiple parameters in a query.</span></span> <span data-ttu-id="90192-122">たとえば、名前付きパラメーターを使って `authors` テーブルで著者の姓名を検索する場合は、SQL ペインに次のようなステートメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="90192-122">For example, if you use named parameters to search for an author's first and last names in the `authors` table, the resulting statement in the SQL pane might look like this:</span></span>  
  
```  
SELECT au_id  
FROM authors  
WHERE au_fname = %first name% AND  
      au_lname = %last name%  
```  
  
> [!TIP]  
>  <span data-ttu-id="90192-123">名前付きパラメーター クエリを作成する前に、プレフィックスとサフィックスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90192-123">You must define prefix and suffix characters before creating a named parameter query.</span></span>  
  
 <span data-ttu-id="90192-124">クエリおよびビュー デザイナーでこのクエリを実行すると、 [[クエリ パラメーター] ダイアログ ボックス](query-parameters-dialog-box-visual-database-tools.md) に名前付きパラメーターのリストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90192-124">When you run the query in the Query and View Designer, the [Query Parameters Dialog Box](query-parameters-dialog-box-visual-database-tools.md) appears with a list of named parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90192-125">参照</span><span class="sxs-lookup"><span data-stu-id="90192-125">See Also</span></span>  
 <span data-ttu-id="90192-126">[Visual Database Tools &#40;パラメーターを使用したクエリ&#41;](query-with-parameters-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="90192-126">[Query with Parameters &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md) </span></span>  
 <span data-ttu-id="90192-127">[Visual Database Tools &#40;サポートされているクエリの種類&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="90192-127">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="90192-128">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="90192-128">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
