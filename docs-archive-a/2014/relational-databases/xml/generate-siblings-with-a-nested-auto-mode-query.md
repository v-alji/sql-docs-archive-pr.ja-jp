---
title: 入れ子になった AUTO モードのクエリを使用した兄弟の生成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- queries [XML in SQL Server], nested AUTO mode
- nested AUTO mode query
ms.assetid: 748d9899-589d-4420-8048-1258e9e67c20
author: rothja
ms.author: jroth
ms.openlocfilehash: 20362942bdd0f7e7537433b664e5e63461ded499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743061"
---
# <a name="generate-siblings-with-a-nested-auto-mode-query"></a><span data-ttu-id="2fe67-102">入れ子になった AUTO モードのクエリを使用した兄弟の生成</span><span class="sxs-lookup"><span data-stu-id="2fe67-102">Generate Siblings with a Nested AUTO Mode Query</span></span>
  <span data-ttu-id="2fe67-103">次の例では、入れ子になった AUTO モードのクエリを使用して兄弟を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2fe67-103">The following example shows how to generate siblings by using a nested AUTO mode query.</span></span> <span data-ttu-id="2fe67-104">他の方法では、EXPLICIT モードを使用する以外に、このような XML を生成する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="2fe67-104">The only other way to generate such XML is to use the EXPLICIT mode.</span></span> <span data-ttu-id="2fe67-105">ただし、この方法は複雑になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2fe67-105">However, this can be cumbersome.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fe67-106">例</span><span class="sxs-lookup"><span data-stu-id="2fe67-106">Example</span></span>  
 <span data-ttu-id="2fe67-107">このクエリでは、販売注文情報を提供する XML が構築されます。</span><span class="sxs-lookup"><span data-stu-id="2fe67-107">This query constructs XML that provides sales order information.</span></span> <span data-ttu-id="2fe67-108">これには、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2fe67-108">This includes the following:</span></span>  
  
-   <span data-ttu-id="2fe67-109">販売注文ヘッダー情報、 `SalesOrderID`、 `SalesPersonID`、および `OrderDate`。</span><span class="sxs-lookup"><span data-stu-id="2fe67-109">Sales order header information, `SalesOrderID`, `SalesPersonID`, and `OrderDate`.</span></span> [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="2fe67-110">の `SalesOrderHeader` テーブルにこの情報が格納されています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-110">stores this information in the `SalesOrderHeader` table.</span></span>  
  
-   <span data-ttu-id="2fe67-111">販売注文明細情報。</span><span class="sxs-lookup"><span data-stu-id="2fe67-111">Sales order detail information.</span></span> <span data-ttu-id="2fe67-112">注文を受けた 1 つ以上の製品、単価、および受注数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2fe67-112">This includes one or more products ordered, the unit price, and the quantity ordered.</span></span> <span data-ttu-id="2fe67-113">この情報は `SalesOrderDetail` テーブルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-113">This information is stored in the `SalesOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="2fe67-114">販売員情報。</span><span class="sxs-lookup"><span data-stu-id="2fe67-114">Sales person information.</span></span> <span data-ttu-id="2fe67-115">これは注文を受けた販売員です。</span><span class="sxs-lookup"><span data-stu-id="2fe67-115">This is the salesperson who took the order.</span></span> <span data-ttu-id="2fe67-116">`SalesPerson` は、 `SalesPersonID`テーブルで提供されています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-116">The `SalesPerson` table provides the `SalesPersonID`.</span></span> <span data-ttu-id="2fe67-117">このクエリでは、販売員の名前を検索するために、このテーブルと `Employee` テーブルを結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fe67-117">For this query, you have to join this table to the `Employee` table to find the name of the sales person.</span></span>  
  
 <span data-ttu-id="2fe67-118">次に示す 2 つの異なる `SELECT` クエリは、やや形式の異なる XML を生成します。</span><span class="sxs-lookup"><span data-stu-id="2fe67-118">The two distinct `SELECT` queries that follow generate XML with a small difference in shape.</span></span>  
  
 <span data-ttu-id="2fe67-119">最初のクエリで生成される XML では、<`SalesPerson`> と <`SalesOrderHeader`> は <`SalesOrder`> の子の兄弟として示されます。</span><span class="sxs-lookup"><span data-stu-id="2fe67-119">The first query generates XML in which <`SalesPerson`> and <`SalesOrderHeader`> appear as sibling children of <`SalesOrder`>:</span></span>  
  
```  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID =   
                   SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
        FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
        for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As   
                     SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="2fe67-120">上のクエリで、最も外側の `SELECT` ステートメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2fe67-120">In the previous query, the outermost `SELECT` statement does the following:</span></span>  
  
-   <span data-ttu-id="2fe67-121">`SalesOrder` 句で指定された行セット `FROM` に対してクエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-121">Queries the rowset, `SalesOrder`, specified in the `FROM` clause.</span></span> <span data-ttu-id="2fe67-122">結果は、1 つ以上の <`SalesOrder`> 要素を含む XML になります。</span><span class="sxs-lookup"><span data-stu-id="2fe67-122">The result is an XML with one or more <`SalesOrder`> elements.</span></span>  
  
-   <span data-ttu-id="2fe67-123">`AUTO` モードと `TYPE` ディレクティブが指定されています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-123">Specifies `AUTO` mode and the `TYPE` directive.</span></span> <span data-ttu-id="2fe67-124">`AUTO`モードはクエリの結果を XML に変換し、 `TYPE` ディレクティブは結果を型として返し `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="2fe67-124">`AUTO` mode transforms the query result into XML, and the `TYPE` directive returns the result as `xml` type.</span></span>  
  
-   <span data-ttu-id="2fe67-125">2 つの `SELECT` ステートメントが含まれており、コンマで区切られ、入れ子構造になっています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-125">Includes two nested `SELECT` statements separated by a comma.</span></span> <span data-ttu-id="2fe67-126">入れ子の最初の `SELECT` ステートメントで、販売注文情報、ヘッダー、および明細を取得し、入れ子の 2 番目の `SELECT` ステートメントで販売員情報を取得しています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-126">The first nested `SELECT` retrieves sales order information, header and details, and the second nested `SELECT` statement retrieves salesperson information.</span></span>  
  
    -   <span data-ttu-id="2fe67-127">`SELECT` 、 `SalesOrderID`、および `SalesPersonID`自体を取得する `CustomerID` ステートメントには、販売注文明細情報を返す別の `SELECT ... FOR XML` ステートメント ( `AUTO` モードと `TYPE` ディレクティブを指定) が入れ子として含まれています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-127">The `SELECT` statement that retrieves `SalesOrderID`, `SalesPersonID`, and `CustomerID` itself includes another nested `SELECT ... FOR XML` statement (with `AUTO` mode and `TYPE` directive) that returns sales order detail information.</span></span>  
  
 <span data-ttu-id="2fe67-128">販売員情報を取得する `SELECT` ステートメントは、 `SalesPerson`句で作成された行セット `FROM` に対してクエリを行います。</span><span class="sxs-lookup"><span data-stu-id="2fe67-128">The `SELECT` statement that retrieves the sales person information queries a rowset, `SalesPerson`, created in the `FROM` clause.</span></span> <span data-ttu-id="2fe67-129">`FOR XML` クエリが機能するためには、 `FROM` 句で生成される匿名の行セットに名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fe67-129">For `FOR XML` queries to work, you must provide a name for the anonymous rowset generated in the `FROM` clause.</span></span> <span data-ttu-id="2fe67-130">ここで指定されている名前は `SalesPerson`です。</span><span class="sxs-lookup"><span data-stu-id="2fe67-130">In this case, the name provided is `SalesPerson`.</span></span>  
  
 <span data-ttu-id="2fe67-131">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2fe67-131">This is the partial result:</span></span>  
  
```  
<SalesOrder>  
  <Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  </Sales.SalesOrderHeader>  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</SalesOrder>  
...  
```  
  
 <span data-ttu-id="2fe67-132">次のクエリでは、同じ販売注文情報が生成されます。ただし、結果の XML では、<`SalesPerson`> は <`SalesOrderDetail`> の兄弟として示されます。</span><span class="sxs-lookup"><span data-stu-id="2fe67-132">The following query generates the same sales order information, except that in the resulting XML, the <`SalesPerson`> appears as a sibling of <`SalesOrderDetail`>:</span></span>  
  
```  
<SalesOrder>  
    <SalesOrderHeader ...>  
          <SalesOrderDetail .../>  
          <SalesOrderDetail .../>  
          ...  
          <SalesPerson .../>  
    </SalesOrderHeader>  
  
</SalesOrder>  
<SalesOrder>  
  ...  
</SalesOrder>  
```  
  
 <span data-ttu-id="2fe67-133">クエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2fe67-133">This is the query:</span></span>  
  
```  
SELECT SalesOrderID, SalesPersonID, CustomerID,  
             (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
              from Sales.SalesOrderDetail  
              WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
              FOR XML AUTO, TYPE),  
              (SELECT *   
               FROM  (SELECT SalesPersonID, EmployeeID  
                    FROM Sales.SalesPerson, HumanResources.Employee  
                    WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
               WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
         FOR XML AUTO, TYPE)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID=43659 or SalesOrderID=43660  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="2fe67-134">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2fe67-134">This is the result:</span></span>  
  
```  
<Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
<Sales.SalesOrderHeader SalesOrderID="43660" SalesPersonID="279" CustomerID="117">  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="762" OrderQty="1" UnitPrice="419.4589" />  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="758" OrderQty="1" UnitPrice="874.7940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
```  
  
 <span data-ttu-id="2fe67-135">`TYPE` ディレクティブによってクエリの結果が `xml` 型で返されるので、各種の `xml` データ型メソッドを使用して結果の XML にクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2fe67-135">Because the `TYPE` directive returns a query result as `xml` type, you can query the resulting XML by using various `xml` data type methods.</span></span> <span data-ttu-id="2fe67-136">詳細については、「 [xml データ型のメソッド](/sql/t-sql/xml/xml-data-type-methods)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fe67-136">For more information, see [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods).</span></span> <span data-ttu-id="2fe67-137">次のクエリでは、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="2fe67-137">In the following query, note the following:</span></span>  
  
-   <span data-ttu-id="2fe67-138">上記のクエリが `FROM` 句に追加されています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-138">The previous query is added in the `FROM` clause.</span></span> <span data-ttu-id="2fe67-139">クエリの結果はテーブルで返されます。</span><span class="sxs-lookup"><span data-stu-id="2fe67-139">The query result is returned as a table.</span></span> <span data-ttu-id="2fe67-140">追加された `XmlCol` 別名に注意してください。</span><span class="sxs-lookup"><span data-stu-id="2fe67-140">Note the `XmlCol` alias that is added.</span></span>  
  
-   <span data-ttu-id="2fe67-141">`SELECT` 句では、 `XmlCol` 句で返される `FROM` に対して XQuery を指定しています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-141">The `SELECT` clause specifies an XQuery against the `XmlCol` returned in the `FROM` clause.</span></span> <span data-ttu-id="2fe67-142">XQuery の指定では、`query()` データ型の `xml` メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="2fe67-142">The `query()` method of the `xml` data type is used in specifying the XQuery.</span></span> <span data-ttu-id="2fe67-143">詳細については、「[クエリ&#40;&#41; メソッド &#40;xml データ型&#41;](/sql/t-sql/xml/query-method-xml-data-type)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fe67-143">For more information, see [query&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/query-method-xml-data-type).</span></span>  
  
    ```  
    SELECT XmlCol.query('<Root> { /* } </Root>')  
    FROM (  
    SELECT SalesOrderID, SalesPersonID, CustomerID,  
                 (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
                  from Sales.SalesOrderDetail  
                  WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
                  FOR XML AUTO, TYPE),  
                  (SELECT *   
                   FROM  (SELECT SalesPersonID, EmployeeID  
                        FROM Sales.SalesPerson, HumanResources.Employee  
                        WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
                   WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
             FOR XML AUTO, TYPE)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesOrderID='43659' or SalesOrderID='43660'  
    FOR XML AUTO, TYPE ) as T(XmlCol)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2fe67-144">参照</span><span class="sxs-lookup"><span data-stu-id="2fe67-144">See Also</span></span>  
 [<span data-ttu-id="2fe67-145">入れ子になった FOR XML クエリの使用</span><span class="sxs-lookup"><span data-stu-id="2fe67-145">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
