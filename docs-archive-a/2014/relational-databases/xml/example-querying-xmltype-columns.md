---
title: '例: XML 型の列のクエリ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, querying XML example
ms.assetid: d9f3710d-7a2e-4abe-9c02-3e3c0df4d620
author: rothja
ms.author: jroth
ms.openlocfilehash: 0eedfa5a5a265f3715a76a6ca80d489bbec199bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631686"
---
# <a name="example-querying-xmltype-columns"></a><span data-ttu-id="ba95c-102">例: XML 型の列のクエリ</span><span class="sxs-lookup"><span data-stu-id="ba95c-102">Example: Querying XMLType Columns</span></span>
  <span data-ttu-id="ba95c-103">次のクエリには、`xml` 型の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ba95c-103">The following query includes columns of `xml` type.</span></span> <span data-ttu-id="ba95c-104">クエリでは、`xml` 型の `Instructions` 列から、製品モデル ID、名前、および最初の場所での製造手順を取得しています。</span><span class="sxs-lookup"><span data-stu-id="ba95c-104">The query retrieves product model ID, name, and manufacturing steps at the first location from the `Instructions` column of the `xml` type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba95c-105">例</span><span class="sxs-lookup"><span data-stu-id="ba95c-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
')   
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
GO  
```  
  
 <span data-ttu-id="ba95c-106">次に結果を示します。</span><span class="sxs-lookup"><span data-stu-id="ba95c-106">The following is the result.</span></span> <span data-ttu-id="ba95c-107">テーブルには、一部の製品モデルの製造手順だけが格納されます。</span><span class="sxs-lookup"><span data-stu-id="ba95c-107">Note that the table stores manufacturing instructions for only some product models.</span></span> <span data-ttu-id="ba95c-108">製造手順は、結果内の <`ProductModelData`> 要素のサブ要素として返されます。</span><span class="sxs-lookup"><span data-stu-id="ba95c-108">The manufacturing steps are returned as subelements of the <`ProductModelData`> element in the result.</span></span>  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
    <MI:step> ... </MI:step>  
    <MI:step> ... </MI:step>  
 </ProductModelData>  
```  
  
 <span data-ttu-id="ba95c-109">次の `SELECT` ステートメントで指定されているように、XQuery から返される XML に対して列名をクエリで指定した場合、製造手順は指定した名前の要素でラップされます。</span><span class="sxs-lookup"><span data-stu-id="ba95c-109">If the query specifies a column name for the XML returned by the XQuery, as specified in the following `SELECT` statement, the manufacturing steps are wrapped in the element that has the specified name.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
go  
```  
  
 <span data-ttu-id="ba95c-110">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ba95c-110">This is the result:</span></span>  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
  <ManuSteps>  
    <MI:step ... </MI:step>  
    <MI:step ... </MI:step>  
  </ManuSteps>  
</ProductModelData>  
```  
  
 <span data-ttu-id="ba95c-111">次のクエリでは、 `ELEMENTS` ディレクティブが指定されています。</span><span class="sxs-lookup"><span data-stu-id="ba95c-111">The following query specifies the `ELEMENTS` directive.</span></span> <span data-ttu-id="ba95c-112">したがって、返される結果は要素中心になります。</span><span class="sxs-lookup"><span data-stu-id="ba95c-112">Therefore, the result returned is element-centric.</span></span> <span data-ttu-id="ba95c-113">`XSINIL` オプションを `ELEMENTS` ディレクティブと共に指定すると、行セット内の対応する列が NULL であっても、<`ManuSteps`> 要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="ba95c-113">The `XSINIL` option specified with the `ELEMENTS` directive returns the <`ManuSteps`> elements, even if the corresponding column in the rowset is NULL.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData'), root('MyRoot'), ELEMENTS XSINIL  
go  
```  
  
 <span data-ttu-id="ba95c-114">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ba95c-114">This is the result:</span></span>  
  
```  
<MyRoot xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   ...  
  <ProductModelData>  
    <ProductModelID>6</ProductModelID>  
    <Name>HL Road Frame</Name>  
    <ManuSteps xsi:nil="true" />  
  </ProductModelData>  
  <ProductModelData>  
    <ProductModelID>7</ProductModelID>  
    <Name>HL Touring Frame</Name>  
    <ManuSteps>  
      <MI:step ... </MI:step>  
      <MI:step ...</MI:step>  
       ...  
    </ManuSteps>  
  </ProductModelData>  
</MyRoot>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba95c-115">参照</span><span class="sxs-lookup"><span data-stu-id="ba95c-115">See Also</span></span>  
 [<span data-ttu-id="ba95c-116">FOR XML での RAW モードの使用</span><span class="sxs-lookup"><span data-stu-id="ba95c-116">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
