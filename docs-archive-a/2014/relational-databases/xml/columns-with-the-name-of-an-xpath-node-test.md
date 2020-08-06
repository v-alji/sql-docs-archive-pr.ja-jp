---
title: XPath ノード テストの名前が付いた列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6555815d97308bed6e70d9fedb9858fc3abe7685
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713941"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a><span data-ttu-id="89cbf-102">XPath ノード テストの名前が付いた列</span><span class="sxs-lookup"><span data-stu-id="89cbf-102">Columns with the Name of an XPath Node Test</span></span>
  <span data-ttu-id="89cbf-103">XPath ノード テストのいずれかが列名である場合、内容は次の表に示すようにマップされます。</span><span class="sxs-lookup"><span data-stu-id="89cbf-103">If the column name is one of the XPath node tests, the content is mapped as shown in the following table.</span></span> <span data-ttu-id="89cbf-104">列名がいずれかの XPath ノード テストであれば、対応するノードに内容がマップされます。</span><span class="sxs-lookup"><span data-stu-id="89cbf-104">When the column name is an XPath node test, the content is mapped to the corresponding node.</span></span> <span data-ttu-id="89cbf-105">列の SQL 型が `xml` の場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="89cbf-105">If the SQL type of the column is `xml`, an error is returned.</span></span>  
  
|<span data-ttu-id="89cbf-106">列名</span><span class="sxs-lookup"><span data-stu-id="89cbf-106">Column Name</span></span>|<span data-ttu-id="89cbf-107">動作</span><span class="sxs-lookup"><span data-stu-id="89cbf-107">Behavior</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="89cbf-108">text()</span><span class="sxs-lookup"><span data-stu-id="89cbf-108">text()</span></span>|<span data-ttu-id="89cbf-109">text() という名前の列では、列内の文字列値がテキスト ノードとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="89cbf-109">For a column with the name of text(), the string value in that column is added as a text node.</span></span>|  
|<span data-ttu-id="89cbf-110">comment()</span><span class="sxs-lookup"><span data-stu-id="89cbf-110">comment()</span></span>|<span data-ttu-id="89cbf-111">comment() という名前の列では、列内の文字列値が XML のコメントとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="89cbf-111">For a column with the name of comment(), the string value in that column is added as an XML comment.</span></span>|  
|<span data-ttu-id="89cbf-112">node()</span><span class="sxs-lookup"><span data-stu-id="89cbf-112">node()</span></span>|<span data-ttu-id="89cbf-113">node() という名前の列では、列名がワイルドカード文字 (\*) の場合と同じ結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="89cbf-113">For a column with the name of node(), the result is the same as it is when the column name is a wildcard character (\*).</span></span>|  
|<span data-ttu-id="89cbf-114">processing-instruction(name)</span><span class="sxs-lookup"><span data-stu-id="89cbf-114">processing-instruction(name)</span></span>|<span data-ttu-id="89cbf-115">処理命令を名前とする列では、列内の文字列値が、処理命令ターゲット名に対応する PI 値として追加されます。</span><span class="sxs-lookup"><span data-stu-id="89cbf-115">For a column with the name of a processing instruction, the string value in that column is added as the PI value for the processing instruction target name.</span></span>|  
  
 <span data-ttu-id="89cbf-116">次のクエリでは、列名としてノード テストを使用しています。</span><span class="sxs-lookup"><span data-stu-id="89cbf-116">The following query shows the use of the node tests as column names.</span></span> <span data-ttu-id="89cbf-117">結果の XML では、テキスト ノードとコメントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="89cbf-117">It adds text nodes and comments in the resulting XML.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 <span data-ttu-id="89cbf-118">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="89cbf-118">This is the result:</span></span>  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>S??nchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="89cbf-119">参照</span><span class="sxs-lookup"><span data-stu-id="89cbf-119">See Also</span></span>  
 [<span data-ttu-id="89cbf-120">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="89cbf-120">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
