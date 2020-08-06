---
title: '例: 従業員情報の取得 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT mode
ms.assetid: 63cd6569-2600-485b-92b4-1f6ba09db219
author: rothja
ms.author: jroth
ms.openlocfilehash: ae4578aedb7dbcc63388d5ef797e3a0bf5d8c306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641529"
---
# <a name="example-retrieving-employee-information"></a><span data-ttu-id="ea9ad-102">例:従業員情報の取得</span><span class="sxs-lookup"><span data-stu-id="ea9ad-102">Example: Retrieving Employee Information</span></span>
  <span data-ttu-id="ea9ad-103">この例では、各従業員の従業員 ID と名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-103">This example retrieves an employee ID and employee name for each employee.</span></span> <span data-ttu-id="ea9ad-104">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの場合、employeeID は Employee テーブルの BusinessEntityID 列から取得できます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-104">In the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, the employeeID can be obtained from the BusinessEntityID column in the Employee table.</span></span> <span data-ttu-id="ea9ad-105">従業員名は、Person テーブルから取得できます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-105">Employee names can be obtained from the Person table.</span></span> <span data-ttu-id="ea9ad-106">これらのテーブルを結合する際には、BusinessEntityID 列を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-106">The BusinessEntityID column can be used to join the tables.</span></span>  
  
 <span data-ttu-id="ea9ad-107">FOR XML EXPLICIT 変換で、次に示す XML を生成するとします。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-107">Assume that you want FOR XML EXPLICIT transformation to generate XML as shown in the following:</span></span>  
  
```  
<Employee EmpID="1" >  
  <Name FName="Ken" LName="S??nchez" />  
</Employee>  
...  
```  
  
 <span data-ttu-id="ea9ad-108">階層は 2 レベルなので、 `SELECT` クエリを 2 つ記述して、UNION ALL を適用します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-108">Because there are two levels in the hierarchy, you would write two `SELECT` queries and apply UNION ALL.</span></span> <span data-ttu-id="ea9ad-109"><`Employee`> 要素とその属性の値を取得する 1 つ目のクエリを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-109">This is the first query that retrieves values for the <`Employee`> element and its attributes.</span></span> <span data-ttu-id="ea9ad-110"><`Employee`> 要素は最上位要素なので、このクエリでは、この要素の `1` 列に値 `Tag` を割り当て、`Parent` 列には NULL を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-110">The query assigns `1` as `Tag` value for the <`Employee`> element and NULL as `Parent`, because it is the top-level element.</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID AS [Employee!1!EmpID],  
       NULL       as [Name!2!FName],  
       NULL       as [Name!2!LName]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID;  
```  
  
 <span data-ttu-id="ea9ad-111">2 つ目のクエリを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-111">This is the second query.</span></span> <span data-ttu-id="ea9ad-112">このクエリでは、<`Name`> 要素の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-112">It retrieves values for the <`Name`> element.</span></span> <span data-ttu-id="ea9ad-113"><`2`> 要素の `Tag` 列に値 `Name` を割り当て、`1` 列には値 `Parent` を割り当てて、親要素が <`Employee`> であることを示します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-113">It assigns `2` as `Tag` value for the <`Name`> element and `1` as `Parent` tag value identifying <`Employee`> as the parent.</span></span>  
  
```  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID;  
```  
  
 <span data-ttu-id="ea9ad-114">`UNION AL`を使用してこれらのクエリを結合し、 `FOR XML EXPLICIT`を適用して、必要な `ORDER BY` 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-114">You combine these queries with `UNION AL`L, apply `FOR XML EXPLICIT`, and specify the required `ORDER BY` clause.</span></span> <span data-ttu-id="ea9ad-115">行セットは、まず `BusinessEntityID` で並べ替え、次に name で並べ替えます。このように並べ替えると、name に NULL が設定されている行が先に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-115">You must sort the rowset first by `BusinessEntityID` and then by name so that the NULL values in the name appear first.</span></span> <span data-ttu-id="ea9ad-116">FOR XML 句を指定せずに次のクエリを実行すると、ユニバーサル テーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-116">By executing the following query without the FOR XML clause, you can see the universal table generated.</span></span>  
  
 <span data-ttu-id="ea9ad-117">最終的なクエリは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-117">This is the final query:</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID as [Employee!1!EmpID],  
       NULL       as [Name!2!FName],  
       NULL       as [Name!2!LName]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
ORDER BY [Employee!1!EmpID],[Name!2!FName]  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="ea9ad-118">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-118">This is the partial result:</span></span>  
  
 `<Employee EmpID="1">`  
  
 `<Name FName="Ken" LName="S??nchez" />`  
  
 `</Employee>`  
  
 `<Employee EmpID="2">`  
  
 `<Name FName="Terri" LName="Duffy" />`  
  
 `</Employee>`  
  
 `...`  
  
 <span data-ttu-id="ea9ad-119">1 つ目の `SELECT` では、結果の行セット内の列名を指定しています。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-119">The first `SELECT` specifies names for columns in the resulting rowset.</span></span> <span data-ttu-id="ea9ad-120">この名前により、2 つの列グループが形成されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-120">These names form two column groups.</span></span> <span data-ttu-id="ea9ad-121">`Tag` 列の値が `1` のグループでは、 `Employee` が要素であり、 `EmpID` が属性であると識別されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-121">The group that has `Tag` value `1` in the column name identifies `Employee` as an element and `EmpID` as the attribute.</span></span> <span data-ttu-id="ea9ad-122">`Tag` 列の値が `2` のグループでは、<`Name`> が要素であり、`FName` と `LName` が属性であると識別されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-122">The other column group has `Tag` value `2` in the column and identifies <`Name`> as the element and `FName` and `LName` as the attributes.</span></span>  
  
 <span data-ttu-id="ea9ad-123">次の表に、このクエリを実行した結果として生成される行セットの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-123">The following table shows the partial rowset generated by the query:</span></span>  
  
 `Tag Parent  Employee!1!EmpID Name!2!FName Name!2!LName`  
  
 `--- ------  ---------------- ------------ ------------`  
  
 `1   NULL    1                NULL         NULL`  
  
 `2   1       1                Ken          S??nchez`  
  
 `1   NULL    2                NULL         NULL`  
  
 `2   1       2                Terri        Duffy`  
  
 `1   NULL    3                NULL         NULL`  
  
 `2   1       3                Roberto      Tamburello`  
  
 `...`  
  
 <span data-ttu-id="ea9ad-124">結果の XML ツリーを生成する際、ユニバーサル テーブル内の行は、次のように処理されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-124">This is how the rows in the universal table are processed to produce the resulting XML tree:</span></span>  
  
 <span data-ttu-id="ea9ad-125">1 行目の `Tag` 列の値は `1`です。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-125">The first row identifies `Tag` value `1`.</span></span> <span data-ttu-id="ea9ad-126">これにより、 `Tag` 列に値 `1` が割り当てられた列グループとして `Employee!1!EmpID`が識別されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-126">Therefore, the column group that has the `Tag` value `1` is identified, `Employee!1!EmpID`.</span></span> <span data-ttu-id="ea9ad-127">この列では、 `Employee` は要素名として識別されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-127">This column identifies `Employee` as the element name.</span></span> <span data-ttu-id="ea9ad-128">その後、`EmpID` 属性を持つ <`Employee`> 要素が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-128">An <`Employee`> element is then created that has `EmpID` attributes.</span></span> <span data-ttu-id="ea9ad-129">これらの属性には、対応する列の値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-129">Corresponding column values are assigned to these attributes.</span></span>  
  
 <span data-ttu-id="ea9ad-130">2 行目の `Tag` 列の値は `2`です。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-130">The second row has the `Tag` value `2`.</span></span> <span data-ttu-id="ea9ad-131">これにより、 `Tag` 列に値 `2` が割り当てられた列グループとして `Name!2!FName`、 `Name!2!LName`が識別されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-131">Therefore, the column group that has the `Tag` value `2` in the column name, `Name!2!FName`, `Name!2!LName`, is identified.</span></span> <span data-ttu-id="ea9ad-132">これらの列では、 `Name` が要素名として識別されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-132">These column names identify `Name` as element name.</span></span> <span data-ttu-id="ea9ad-133"><`Name`> 要素の作成時には、`FName` 属性と `LName` 属性が識別されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-133">A <`Name`> element is created that has `FName` and `LName` attributes.</span></span> <span data-ttu-id="ea9ad-134">これらの属性には、対応する列の値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-134">Corresponding column values are then assigned to these attributes.</span></span> <span data-ttu-id="ea9ad-135">この行の `1` 列には値 `Parent`が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-135">This row identifies `1` as `Parent`.</span></span> <span data-ttu-id="ea9ad-136">したがって、この要素は、1 行目の <`Employee`> 要素に子要素として追加されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-136">This element child is added to the previous <`Employee`> element.</span></span>  
  
 <span data-ttu-id="ea9ad-137">この処理が、行セット内の残りの行に対して繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-137">This process is repeated for rest of the rows in the rowset.</span></span> <span data-ttu-id="ea9ad-138">FOR XML EXPLICIT で行セットを順に処理して、必要な XML を生成できるようにするには、ユニバーサル テーブル内の行の並び順が重要になります。</span><span class="sxs-lookup"><span data-stu-id="ea9ad-138">Note the importance of ordering the rows in the universal table so that FOR XML EXPLICIT can process the rowset in order and generate the XML you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea9ad-139">参照</span><span class="sxs-lookup"><span data-stu-id="ea9ad-139">See Also</span></span>  
 [<span data-ttu-id="ea9ad-140">FOR XML での EXPLICIT モードの使用</span><span class="sxs-lookup"><span data-stu-id="ea9ad-140">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
