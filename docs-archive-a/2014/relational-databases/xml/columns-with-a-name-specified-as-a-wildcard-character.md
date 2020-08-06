---
title: 名前をワイルドカード文字で指定した列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b363baf8792628c2e17b1a695c19a6a338f4fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640799"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a><span data-ttu-id="35774-102">名前をワイルドカード文字で指定した列</span><span class="sxs-lookup"><span data-stu-id="35774-102">Columns with a Name Specified as a Wildcard Character</span></span>
  <span data-ttu-id="35774-103">列名にワイルドカード文字 (\*) を指定した場合は、列名が指定されていない場合のように、列の内容が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="35774-103">If the column name specified is a wildcard character (\*), the content of that column is inserted as if there is no column name specified.</span></span> <span data-ttu-id="35774-104">`xml` 型以外の列の場合は、次の例で示すように内容がテキスト ノードとして挿入されます。</span><span class="sxs-lookup"><span data-stu-id="35774-104">If this column is a non-`xml` type column, the column content is inserted as a text node, as shown in the following example:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 <span data-ttu-id="35774-105">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35774-105">This is the result:</span></span>  
  
 `<row EmpID="1">KenJS??nchez</row>`  
  
 <span data-ttu-id="35774-106">`xml` 型の列の場合、対応する XML ツリーが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="35774-106">If the column is of `xml` type, the corresponding XML tree is inserted.</span></span> <span data-ttu-id="35774-107">たとえば次のクエリでは、Instructions 列に対する XQuery が返す XML を格納する列名として "\*" を指定しています。</span><span class="sxs-lookup"><span data-stu-id="35774-107">For example, the following query specifies "\*" for the column name that contains the XML returned by the XQuery against the Instructions column.</span></span>  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 <span data-ttu-id="35774-108">結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="35774-108">This is the result.</span></span> <span data-ttu-id="35774-109">XQuery が返した XML は、囲み要素なしで挿入されます。</span><span class="sxs-lookup"><span data-stu-id="35774-109">The XML returned by XQuery is inserted without a wrapping element.</span></span>  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="35774-110">参照</span><span class="sxs-lookup"><span data-stu-id="35774-110">See Also</span></span>  
 [<span data-ttu-id="35774-111">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="35774-111">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
