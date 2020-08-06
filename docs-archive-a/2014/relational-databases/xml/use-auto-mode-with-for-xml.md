---
title: FOR XML での AUTO モードの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, AUTO mode
- ELEMENTS option
- FOR XML AUTO mode
- AUTO FOR XML mode
ms.assetid: 7140d656-1d42-4f01-a533-5251429f4450
author: rothja
ms.author: jroth
ms.openlocfilehash: 232cc046667c6d31cb9657a7abdc862204507d23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641526"
---
# <a name="use-auto-mode-with-for-xml"></a><span data-ttu-id="c4590-102">FOR XML での AUTO モードの使用</span><span class="sxs-lookup"><span data-stu-id="c4590-102">Use AUTO Mode with FOR XML</span></span>
  <span data-ttu-id="c4590-103">「 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)」で説明したように、AUTO モードを使用すると、入れ子構造の XML 要素としてクエリ結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-103">As described in [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md), AUTO mode returns query results as nested XML elements.</span></span> <span data-ttu-id="c4590-104">AUTO モードでは、クエリ結果から生成される XML の構造はあまり制御されません。</span><span class="sxs-lookup"><span data-stu-id="c4590-104">This does not provide much control over the shape of the XML generated from a query result.</span></span> <span data-ttu-id="c4590-105">AUTO モードのクエリは、単純な階層を生成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c4590-105">The AUTO mode queries are useful if you want to generate simple hierarchies.</span></span> <span data-ttu-id="c4590-106">ただし、 [FOR XML での EXPLICIT モードの使用](use-explicit-mode-with-for-xml.md) や [FOR XML での PATH モードの使用](use-path-mode-with-for-xml.md) により、クエリ結果から XML の構造を決定するときに、より厳密な制御や高い柔軟性を実現できます。</span><span class="sxs-lookup"><span data-stu-id="c4590-106">However, [Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) and [Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) provide more control and flexibility in deciding the shape of the XML from a query result.</span></span>  
  
 <span data-ttu-id="c4590-107">FROM 句の各テーブルは XML 要素として表され、そのうち少なくとも 1 列が SELECT 句のリストに含められます。</span><span class="sxs-lookup"><span data-stu-id="c4590-107">Each table in the FROM clause, from which at least one column is listed in the SELECT clause, is represented as an XML element.</span></span> <span data-ttu-id="c4590-108">FOR XML 句で省略可能な ELEMENTS オプションを指定すると、SELECT 句のリストに含められる列は属性またはサブ要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c4590-108">The columns listed in the SELECT clause are mapped to attributes or subelements, if the optional ELEMENTS option is specified in the FOR XML clause.</span></span>  
  
 <span data-ttu-id="c4590-109">生成される XML 内の要素が入れ子になった XML 階層は、SELECT 句で指定されている列で識別されるテーブルの順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="c4590-109">The XML hierarchy, nesting of the elements, in the resulting XML is based on the order of tables identified by the columns specified in the SELECT clause.</span></span> <span data-ttu-id="c4590-110">そのため、SELECT 句で列名を指定する順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="c4590-110">Therefore, the order in which column names are specified in the SELECT clause is significant.</span></span> <span data-ttu-id="c4590-111">先頭、つまり識別された左端のテーブルにより、生成される XML ドキュメント内の最上位要素が形成されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-111">The first, leftmost table that is identified forms the top element in the resulting XML document.</span></span> <span data-ttu-id="c4590-112">SELECT ステートメント内の列で識別された左から 2 番目のテーブルにより、最上位要素内のサブ要素が形成されます。以降についても同様です。</span><span class="sxs-lookup"><span data-stu-id="c4590-112">The second leftmost table, identified by columns in the SELECT statement, forms a subelement within the top element, and so on.</span></span>  
  
 <span data-ttu-id="c4590-113">SELECT 句のリストに含まれている列名が、SELECT 句でそれ以前に指定した列によって既に識別されたテーブルに含まれている場合、その列は、階層の新しいレベルを開くのではなく、既に作成されている要素の属性として追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-113">If a column name listed in the SELECT clause is from a table that is already identified by a previously specified column in the SELECT clause, the column is added as an attribute of the element already created, instead of opening a new level of hierarchy.</span></span> <span data-ttu-id="c4590-114">ELEMENTS オプションを指定している場合は、その列が属性として追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-114">If the ELEMENTS option is specified, the column is added as an attribute.</span></span>  
  
 <span data-ttu-id="c4590-115">たとえば、次のクエリを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="c4590-115">For example, execute this query:</span></span>  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO  
```  
  
 <span data-ttu-id="c4590-116">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c4590-116">This is the partial result:</span></span>  
  
```  
<Cust CustomerID="1" CustomerType="S">  
  <OrderHeader CustomerID="1" SalesOrderID="43860" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="44501" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="45283" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="46042" Status="5" />  
</Cust>  
...  
```  
  
 <span data-ttu-id="c4590-117">SELECT 句では、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c4590-117">Note the following in the SELECT clause:</span></span>  
  
-   <span data-ttu-id="c4590-118">CustomerID は Cust テーブルを参照します。</span><span class="sxs-lookup"><span data-stu-id="c4590-118">The CustomerID references the Cust table.</span></span> <span data-ttu-id="c4590-119">そのため、<`Cust`> 要素が作成され、CustomerID がその要素の属性として追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-119">Therefore, a <`Cust`> element is created and CustomerID is added as its attribute.</span></span>  
  
-   <span data-ttu-id="c4590-120">次に、OrderHeader.CustomerID、OrderHeader.SaleOrderID、および OrderHeader.Status の 3 列が、OrderHeader テーブルを参照します。</span><span class="sxs-lookup"><span data-stu-id="c4590-120">Next, three columns, OrderHeader.CustomerID, OrderHeader.SaleOrderID, and OrderHeader.Status, reference the OrderHeader table.</span></span> <span data-ttu-id="c4590-121">そのため、<`OrderHeader`> 要素が <`Cust`> 要素のサブ要素として追加され、OrderHeader テーブルを参照する 3 列が <`OrderHeader`> の属性として追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-121">Therefore, an <`OrderHeader`> element is added as a subelement of the <`Cust`> element and the three columns are added as attributes of <`OrderHeader`>.</span></span>  
  
-   <span data-ttu-id="c4590-122">次に、Cust.CustomerType 列が、Cust.CustomerID 列で既に識別された Cust テーブルを再び参照します。</span><span class="sxs-lookup"><span data-stu-id="c4590-122">Next, the Cust.CustomerType column again references the Cust table that was already identified by the Cust.CustomerID column.</span></span> <span data-ttu-id="c4590-123">このため、新しい要素は作成されません。</span><span class="sxs-lookup"><span data-stu-id="c4590-123">Therefore, no new element is created.</span></span> <span data-ttu-id="c4590-124">この場合、以前作成した <`Cust`> 要素に CustomerType 属性が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-124">Instead, the CustomerType attribute is added to the <`Cust`> element that was previously created.</span></span>  
  
-   <span data-ttu-id="c4590-125">クエリでは、テーブル名の別名が指定されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-125">The query specifies aliases for the table names.</span></span> <span data-ttu-id="c4590-126">これらの別名は、対応する要素名として示されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-126">These aliases appear as corresponding element names.</span></span>  
  
-   <span data-ttu-id="c4590-127">1 つの親のすべての子をグループ化するには、ORDER BY を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4590-127">ORDER BY is required to group all children under one parent.</span></span>  
  
 <span data-ttu-id="c4590-128">次のクエリは、SELECT 句で OrderHeader テーブルの列が指定されてから Cust テーブルの列が指定されている点を除いて、上記のクエリと同様です。</span><span class="sxs-lookup"><span data-stu-id="c4590-128">This query is similar to the previous one, except the SELECT clause specifies columns in the OrderHeader table before the columns in the Cust table.</span></span> <span data-ttu-id="c4590-129">そのため、最初の <`OrderHeader`> 要素が作成されてから、その要素に <`Cust`> 子要素が追加されています。</span><span class="sxs-lookup"><span data-stu-id="c4590-129">Therefore, first <`OrderHeader`> element is created and then the <`Cust`> child element is added to it.</span></span>  
  
```  
select OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerID,   
       Cust.CustomerType  
from Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
where Cust.CustomerID = OrderHeader.CustomerID  
for xml auto  
```  
  
 <span data-ttu-id="c4590-130">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c4590-130">This is the partial result:</span></span>  
  
```  
<OrderHeader CustomerID="1" SalesOrderID="43860" Status="5">  
  <Cust CustomerID="1" CustomerType="S" />  
</OrderHeader>  
...  
```  
  
 <span data-ttu-id="c4590-131">FOR XML 句に ELEMENTS オプションを追加すると、要素中心の XML が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-131">If the ELEMENTS option is added in the FOR XML clause, element-centric XML is returned.</span></span>  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO, ELEMENTS  
```  
  
 <span data-ttu-id="c4590-132">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c4590-132">This is the partial result:</span></span>  
  
```  
<Cust>  
  <CustomerID>1</CustomerID>  
  <CustomerType>S</CustomerType>  
  <OrderHeader>  
    <CustomerID>1</CustomerID>  
    <SalesOrderID>43860</SalesOrderID>  
    <Status>5</Status>  
  </OrderHeader>  
   ...  
</Cust>  
...  
```  
  
 <span data-ttu-id="c4590-133">このクエリでは、\<Cust> 要素の作成時に CustomerID の値が行ごとに比較されます。これは、CustomerID がテーブルの主キーであるためです。</span><span class="sxs-lookup"><span data-stu-id="c4590-133">In this query, the CustomerID values are compared from one row to the next in creating the \<Cust> elements, because CustomerID is the primary key of the table.</span></span> <span data-ttu-id="c4590-134">CustomerID がテーブルの主キーとして識別されない場合、列のすべての値 (このクエリでは CustomerID、CustomerType) が行ごとに比較されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-134">If CustomerID is not identified as the primary key for the table, all the column values (CustomerID, CustomerType in this query) are compared from one row to the next.</span></span> <span data-ttu-id="c4590-135">値が異なる場合は、新しい \<Cust> 要素が XML に追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-135">If the values differ, a new \<Cust> element is added to the XML.</span></span>  
  
 <span data-ttu-id="c4590-136">これらの列の値を比較するとき、比較するいずれかの列が **text**型、 **ntext**型、 **image**型、または **xml**型の場合は、FOR XML では値が同じ場合でも値が異なると想定され比較されません。</span><span class="sxs-lookup"><span data-stu-id="c4590-136">When comparing these column values, if any of the columns to be compared are of type **text**, **ntext**, **image**, or **xml**, FOR XML assumes that the values are different and not compared, even though they may be the same.</span></span> <span data-ttu-id="c4590-137">これは、ラージ オブジェクトの比較がサポートされていないためです。</span><span class="sxs-lookup"><span data-stu-id="c4590-137">This is because comparing large objects is not supported.</span></span> <span data-ttu-id="c4590-138">選択した行ごとに、要素が結果に追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-138">Elements are added to the result for each row selected.</span></span> <span data-ttu-id="c4590-139">**(n)varchar(max)** 型および **varbinary(max)** 型の列は比較されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c4590-139">Note that columns of **(n)varchar(max)** and **varbinary(max)** are compared.</span></span>  
  
 <span data-ttu-id="c4590-140">集計列や計算列の場合と同様に、SELECT 句内の列を FROM 句内で識別されるいずれかのテーブルと関連付けることができない場合、その列がリストに見つかった時点で最も深い入れ子レベルの XML ドキュメントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-140">When a column in the SELECT clause cannot be associated with any of the tables identified in the FROM clause, as in the case of an aggregate column or computed column, the column is added in the XML document in the deepest nesting level in place when it is encountered in the list.</span></span> <span data-ttu-id="c4590-141">このような列が SELECT 句内の最初の列の場合は、最上位の要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-141">If such a column appears as the first column in the SELECT clause, the column is added to the top element.</span></span>  
  
 <span data-ttu-id="c4590-142">SELECT 句にアスタリスク (\*) ワイルドカード文字を指定すると、クエリ エンジンから行が返される順序に基づいて上記の説明と同じ方法で入れ子が決定されます。</span><span class="sxs-lookup"><span data-stu-id="c4590-142">If the asterisk (\*) wildcard character is specified in the SELECT clause, the nesting is determined in the same way as previously described, based on the order that the rows are returned by the query engine.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4590-143">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c4590-143">In This Section</span></span>  
 <span data-ttu-id="c4590-144">次のトピックでは、AUTO モードの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4590-144">The following topics provide more information about AUTO mode:</span></span>  
  
-   [<span data-ttu-id="c4590-145">BINARY BASE64 オプションの使用</span><span class="sxs-lookup"><span data-stu-id="c4590-145">Use the BINARY BASE64 Option</span></span>](use-the-binary-base64-option.md)  
  
-   [<span data-ttu-id="c4590-146">返される XML を構造化する際の AUTO モード ヒューリスティック</span><span class="sxs-lookup"><span data-stu-id="c4590-146">AUTO Mode Heuristics in Shaping Returned XML</span></span>](auto-mode-heuristics-in-shaping-returned-xml.md)  
  
-   [<span data-ttu-id="c4590-147">例: AUTO モードの使用</span><span class="sxs-lookup"><span data-stu-id="c4590-147">Examples: Using AUTO Mode</span></span>](examples-using-auto-mode.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4590-148">参照</span><span class="sxs-lookup"><span data-stu-id="c4590-148">See Also</span></span>  
 <span data-ttu-id="c4590-149">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4590-149">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="c4590-150">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c4590-150">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
