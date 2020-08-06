---
title: MDX の基本的なクエリ (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], SELECT statement
- queries [MDX], about queries
- cellsets [MDX]
- SELECT statement [MDX]
- cubes [Analysis Services], SELECT statement
ms.assetid: 4fa5a95a-fec9-4584-875c-dbf030c53e82
author: minewiskan
ms.author: owend
ms.openlocfilehash: b6b1a70753abe8e477bd1e522a37f4513cc12a52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643576"
---
# <a name="the-basic-mdx-query-mdx"></a><span data-ttu-id="21dbb-102">MDX の基本的なクエリ (MDX)</span><span class="sxs-lookup"><span data-stu-id="21dbb-102">The Basic MDX Query (MDX)</span></span>
  <span data-ttu-id="21dbb-103">基本的な多次元式 (MDX) クエリは SELECT ステートメントであり、MDX で最も頻繁に使用されるクエリです。</span><span class="sxs-lookup"><span data-stu-id="21dbb-103">The basic Multidimensional Expressions (MDX) query is the SELECT statement-the most frequently used query in MDX.</span></span> <span data-ttu-id="21dbb-104">MDX の SELECT ステートメントで結果セットを指定する方法や、SELECT ステートメントの構文と、SELECT ステートメントによる簡単なクエリ作成を学習すれば、MDX を使用して多次元データに対するクエリを実行する方法を理解できます。</span><span class="sxs-lookup"><span data-stu-id="21dbb-104">By understanding how an MDX SELECT statement must specify a result set, what the syntax of the SELECT statement is, and how to create a simple query using the SELECT statement, you will have a solid understanding of how to use MDX to query multidimensional data.</span></span>  
  
## <a name="specifying-a-result-set"></a><span data-ttu-id="21dbb-105">結果セットの指定</span><span class="sxs-lookup"><span data-stu-id="21dbb-105">Specifying a Result Set</span></span>  
 <span data-ttu-id="21dbb-106">MDX の SELECT ステートメントでは、キューブから返された多次元データのサブセットを格納した結果セットが指定されます。</span><span class="sxs-lookup"><span data-stu-id="21dbb-106">In MDX, the SELECT statement specifies a result set that contains a subset of multidimensional data that has been returned from a cube.</span></span> <span data-ttu-id="21dbb-107">結果セットを指定するには、MDX クエリに次の情報を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="21dbb-107">To specify a result set, an MDX query must contain the following information:</span></span>  
  
-   <span data-ttu-id="21dbb-108">結果セットに含める軸の数。</span><span class="sxs-lookup"><span data-stu-id="21dbb-108">The number of axes that you want the result set to contain.</span></span> <span data-ttu-id="21dbb-109">MDX クエリでは、軸を 128 個まで指定できます。</span><span class="sxs-lookup"><span data-stu-id="21dbb-109">You can specify up to 128 axes in an MDX query.</span></span>  
  
-   <span data-ttu-id="21dbb-110">MDX クエリの各軸に含めるメンバーまたは組のセット。</span><span class="sxs-lookup"><span data-stu-id="21dbb-110">The set of members or tuples to include on each axis of the MDX query.</span></span>  
  
-   <span data-ttu-id="21dbb-111">MDX クエリのコンテキストを設定するキューブの名前。</span><span class="sxs-lookup"><span data-stu-id="21dbb-111">The name of the cube that sets the context of the MDX query.</span></span>  
  
-   <span data-ttu-id="21dbb-112">スライサー軸に含めるメンバーまたは組のセット。</span><span class="sxs-lookup"><span data-stu-id="21dbb-112">The set of members or tuples to include on the slicer axis.</span></span> <span data-ttu-id="21dbb-113">スライサー軸とクエリ軸の詳細については、「[クエリ軸とスライサー軸によるクエリの制限 (MDX)](mdx-query-and-slicer-axes-restricting-the-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21dbb-113">For more information about slicer and query axes, see[Restricting the Query with Query and Slicer Axes &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md).</span></span>  
  
 <span data-ttu-id="21dbb-114">MDX の SELECT ステートメントでは、クエリ軸、クエリ対象のキューブ、スライサー軸をそれぞれ指定するために以下の句を使用します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-114">To identify the query axes, the cube that will be queried, and the slicer axis, the MDX SELECT statement uses the following clauses:</span></span>  
  
-   <span data-ttu-id="21dbb-115">SELECT 句。MDX の SELECT ステートメントのクエリ軸を指定します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-115">A SELECT clause that determines the query axes of an MDX SELECT statement.</span></span> <span data-ttu-id="21dbb-116">SELECT 句でクエリ軸を作成する方法の詳細については、「[クエリ軸の内容の指定(MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21dbb-116">For more information about the construction of query axes in a SELECT clause, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
-   <span data-ttu-id="21dbb-117">FROM 句。クエリ対象のキューブを指定します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-117">A FROM clause that determines which cube will be queried.</span></span> <span data-ttu-id="21dbb-118">FROM 句の詳細については、「 [SELECT ステートメント (MDX)](/sql/mdx/mdx-data-manipulation-select)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21dbb-118">For more information about the FROM clause, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
-   <span data-ttu-id="21dbb-119">省略可能な WHERE 句。スライサー軸で使用するメンバーまたは組を指定して、返されるデータを限定します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-119">An optional WHERE clause that determines which members or tuples to use on the slicer axis to restrict the data returned.</span></span> <span data-ttu-id="21dbb-120">WHERE 句でスライサー軸を作成する方法の詳細については、「[スライサー軸の内容の指定 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21dbb-120">For more information about the construction of a slicer axis in a WHERE clause, see [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21dbb-121">SELECT ステートメントの各種の句の詳細については、「 [SELECT ステートメント (MDX)](/sql/mdx/mdx-data-manipulation-select)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21dbb-121">For more detailed information about the various clauses of the SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
## <a name="select-statement-syntax"></a><span data-ttu-id="21dbb-122">SELECT ステートメントの構文</span><span class="sxs-lookup"><span data-stu-id="21dbb-122">SELECT Statement Syntax</span></span>  
 <span data-ttu-id="21dbb-123">SELECT 句、FROM 句、WHERE 句を使用した基本的な SELECT ステートメントの構文を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-123">The following syntax shows a basic SELECT statement that includes the use of the SELECT, FROM, and WHERE clauses:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause>   
    [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
```  
  
 <span data-ttu-id="21dbb-124">MDX の SELECT ステートメントでは、WITH キーワードを使用する構文、軸またはスライサー軸に含める計算されたメンバーを作成するための MDX 関数を使用する構文、クエリの一部として特定のセル プロパティの値を返すための構文など、省略可能な構文をいくつかサポートしています。</span><span class="sxs-lookup"><span data-stu-id="21dbb-124">The MDX SELECT statement supports optional syntax, such as the WITH keyword, the use of MDX functions to create calculated members for inclusion in an axis or slicer axis, and the ability to return the values of specific cell properties as part of the query.</span></span> <span data-ttu-id="21dbb-125">MDX の SELECT ステートメントの詳細については、「 [SELECT ステートメント (MDX)](/sql/mdx/mdx-data-manipulation-select)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21dbb-125">For more information about the MDX SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
### <a name="comparing-the-syntax-of-the-mdx-select-statement-to-sql"></a><span data-ttu-id="21dbb-126">MDX の SELECT ステートメントと SQL の構文の比較</span><span class="sxs-lookup"><span data-stu-id="21dbb-126">Comparing the Syntax of the MDX SELECT Statement to SQL</span></span>  
 <span data-ttu-id="21dbb-127">MDX の SELECT ステートメントの構文形式は、SQL の構文とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="21dbb-127">The syntax format for the MDX SELECT statement is similar to that of SQL syntax.</span></span> <span data-ttu-id="21dbb-128">ただし、次のような基本的な違いもいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="21dbb-128">However, there are several fundamental differences:</span></span>  
  
-   <span data-ttu-id="21dbb-129">MDX 構文では、組またはメンバーを中かっこ ({および} 文字) で囲んで、セットを区別します。メンバー、組、およびセットの構文の詳細については、「 [MDX&#41;&#40;メンバー、組、およびセットの操作](working-with-members-tuples-and-sets-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21dbb-129">MDX syntax distinguishes sets by surrounding tuples or members with braces (the { and } characters.) For more information about member, tuple, and set syntax, see [Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).</span></span>  
  
-   <span data-ttu-id="21dbb-130">MDX クエリでは、SELECT ステートメントにクエリ軸を 0 個、1 個、2 個、または最大で 128 個まで指定できます。</span><span class="sxs-lookup"><span data-stu-id="21dbb-130">MDX queries can have 0, 1, 2 or up to 128 query axes in the SELECT statement.</span></span> <span data-ttu-id="21dbb-131">各軸は、まったく同じ動作をします。SQL の場合は、クエリの行と列とで、動作に大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="21dbb-131">Each axis behaves in exactly the same way, unlike SQL where there are significant differences between how the rows and the columns of a query behave.</span></span>  
  
-   <span data-ttu-id="21dbb-132">MDX クエリで使用するデータ ソースは、SQL クエリと同様に、FROM 句によって指定します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-132">As with an SQL query, the FROM clause names the source of the data for the MDX query.</span></span> <span data-ttu-id="21dbb-133">ただし、MDX の FROM 句では 1 つのキューブしか指定できません。</span><span class="sxs-lookup"><span data-stu-id="21dbb-133">However, the MDX FROM clause is restricted to a single cube.</span></span> <span data-ttu-id="21dbb-134">他のキューブの情報は、LookupCube 関数を使用して値ごとに取得できます。</span><span class="sxs-lookup"><span data-stu-id="21dbb-134">Information from other cubes can be retrieved on a value-by-value basis by using the LookupCube function.</span></span>  
  
-   <span data-ttu-id="21dbb-135">MDX クエリでは、WHERE 句はスライサー軸を指定します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-135">The WHERE clause describes the slicer axis in an MDX query.</span></span> <span data-ttu-id="21dbb-136">クエリ内の見えない追加の軸のように作用し、結果セット内のセルに表示される値をスライスします。SQL の WHERE 句とは異なり、クエリの行軸に何が表示されるかに関して直接影響することはありません。</span><span class="sxs-lookup"><span data-stu-id="21dbb-136">It acts as something like an invisible, extra axis in the query, slicing the values that appear in the cells in the result set; unlike the SQL WHERE clause it does not directly affect what appears on the rows axis of the query.</span></span> <span data-ttu-id="21dbb-137">SQL の WHERE 句の機能は、FILTER 関数などの他の MDX 関数を使って実現できます。</span><span class="sxs-lookup"><span data-stu-id="21dbb-137">The functionality of the SQL WHERE clause is available through other MDX functions such as the FILTER function.</span></span>  
  
## <a name="select-statement-example"></a><span data-ttu-id="21dbb-138">SELECT ステートメントの例</span><span class="sxs-lookup"><span data-stu-id="21dbb-138">SELECT Statement Example</span></span>  
 <span data-ttu-id="21dbb-139">SELECT ステートメントを使用した基本的な MDX クエリの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-139">The following example shows a basic MDX query that uses the SELECT statement.</span></span> <span data-ttu-id="21dbb-140">このクエリは、Southwest という販売地域の 2002 年と 2003 年の売上と税額を格納した結果セットを返します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-140">This query returns a result set that contains the 2002 and 2003 sales and tax amounts for the Southwest sales territories.</span></span>  
  
```  
SELECT  
    { [Measures].[Sales Amount],   
        [Measures].[Tax Amount] } ON COLUMNS,  
    { [Date].[Fiscal].[Fiscal Year].&[2002],   
        [Date].[Fiscal].[Fiscal Year].&[2003] } ON ROWS  
FROM [Adventure Works]  
WHERE ( [Sales Territory].[Southwest] )  
```  
  
 <span data-ttu-id="21dbb-141">このクエリでは、結果セットの情報を次のように定義しています。</span><span class="sxs-lookup"><span data-stu-id="21dbb-141">In this example, the query defines the following result set information:</span></span>  
  
-   <span data-ttu-id="21dbb-142">SELECT 句によって、Measures ディメンションの Sales Amount メンバーと Tax Amount メンバー、Date ディメンションの 2002 メンバーと 2003 メンバーをクエリ軸に設定しています。</span><span class="sxs-lookup"><span data-stu-id="21dbb-142">The SELECT clause sets the query axes as the Sales Amount and Tax Amount members of the Measures dimension, and the 2002 and 2003 members of the Date dimension.</span></span>  
  
-   <span data-ttu-id="21dbb-143">FROM 句によって、Adventure Works キューブをデータ ソースに指定しています。</span><span class="sxs-lookup"><span data-stu-id="21dbb-143">The FROM clause indicates that the data source is the Adventure Works cube.</span></span>  
  
-   <span data-ttu-id="21dbb-144">WHERE 句によって、Sales Territory ディメンションの Southwest メンバーをスライサー軸として定義しています。</span><span class="sxs-lookup"><span data-stu-id="21dbb-144">The WHERE clause defines the slicer axis as the Southwest member of the Sales Territory dimension.</span></span>  
  
 <span data-ttu-id="21dbb-145">このクエリでは、軸の別名として COLUMNS と ROWS を使用しています。</span><span class="sxs-lookup"><span data-stu-id="21dbb-145">Notice that the query example also uses the COLUMNS and ROWS axis aliases.</span></span> <span data-ttu-id="21dbb-146">別名の代わりに、これらの軸の位置を示す序数を使用することも可能です。</span><span class="sxs-lookup"><span data-stu-id="21dbb-146">The ordinal positions for these axes could also have been used.</span></span> <span data-ttu-id="21dbb-147">それぞれの軸の位置を示す序数を使用して MDX クエリを記述する例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="21dbb-147">The following example shows how the MDX query could have been written to use the ordinal position of each axis:</span></span>  
  
```  
SELECT  
    { [Measures].[Sales Amount],   
        [Measures].[Tax Amount] } ON 0,  
    { [Date].[Fiscal].[Fiscal Year].&[2002],   
        [Date].[Fiscal].[Fiscal Year].&[2003] } ON 1  
FROM [Adventure Works]  
WHERE ( [Sales Territory].[Southwest] )  
```  
  
 <span data-ttu-id="21dbb-148">詳細な例については、「[クエリ軸の内容の指定 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」および「[スライサー軸の内容の指定 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21dbb-148">For more detailed examples, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)and [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21dbb-149">参照</span><span class="sxs-lookup"><span data-stu-id="21dbb-149">See Also</span></span>  
 <span data-ttu-id="21dbb-150">[MDX &#40;Analysis Services の主な概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="21dbb-150">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 [<span data-ttu-id="21dbb-151">SELECT ステートメント &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="21dbb-151">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
