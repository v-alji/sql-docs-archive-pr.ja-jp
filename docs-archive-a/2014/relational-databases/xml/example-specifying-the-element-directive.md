---
title: 例:ELEMENT ディレクティブの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
ms.assetid: 80dd5d1f-fa90-4f97-a186-8fa3f460a7f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a03d1049fa9df23eff759634bcd74f88f842a8e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711782"
---
# <a name="example-specifying-the-element-directive"></a><span data-ttu-id="d351f-102">例:ELEMENT ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="d351f-102">Example: Specifying the ELEMENT Directive</span></span>
  <span data-ttu-id="d351f-103">この例では、次に示すように従業員情報を取得し、要素中心の XML を生成します。</span><span class="sxs-lookup"><span data-stu-id="d351f-103">This retrieves employee information and generates element-centric XML as shown in the following:</span></span>  
  
```  
<Employee EmpID=...>  
  <Name>  
    <FName>...</FName>  
    <LName>...</LName>  
  </Name>  
</Employee>  
```  
  
 <span data-ttu-id="d351f-104">クエリも似ていますが、列名に `ELEMENT` ディレクティブを指定する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="d351f-104">The query remains the same, except you add the `ELEMENT` directive in the column names.</span></span> <span data-ttu-id="d351f-105">そのため、<`Name`> 要素には、属性ではなく、<`FName`> 子要素と <`LName`> 子要素が追加されます。</span><span class="sxs-lookup"><span data-stu-id="d351f-105">Therefore, instead of attributes, the <`FName`> and <`LName`> element children are added to the <`Name`> element.</span></span> <span data-ttu-id="d351f-106">`Employee!1!EmpID` 列では `ELEMENT` ディレクティブが指定されていないので、`EmpID` は <`Employee`> 要素の属性として追加されます。</span><span class="sxs-lookup"><span data-stu-id="d351f-106">Because the `Employee!1!EmpID` column does not specify the `ELEMENT` directive, `EmpID` is added as the attribute of the <`Employee`> element.</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID as [Employee!1!EmpID],  
       NULL       as [Name!2!FName!ELEMENT],  
       NULL       as [Name!2!LName!ELEMENT]  
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
ORDER BY [Employee!1!EmpID],[Name!2!FName!ELEMENT]  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="d351f-107">次に結果の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="d351f-107">This is the partial result.</span></span>  
  
 `<Employee EmpID="1">`  
  
 `<Name>`  
  
 `<FName>Ken</FName>`  
  
 `<LName>S??nchez</LName>`  
  
 `</Name>`  
  
 `</Employee>`  
  
 `<Employee EmpID="2">`  
  
 `<Name>`  
  
 `<FName>Terri</FName>`  
  
 `<LName>Duffy</LName>`  
  
 `</Name>`  
  
 `</Employee>`  
  
 `...`  
  
## <a name="see-also"></a><span data-ttu-id="d351f-108">参照</span><span class="sxs-lookup"><span data-stu-id="d351f-108">See Also</span></span>  
 [<span data-ttu-id="d351f-109">FOR XML での EXPLICIT モードの使用</span><span class="sxs-lookup"><span data-stu-id="d351f-109">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
