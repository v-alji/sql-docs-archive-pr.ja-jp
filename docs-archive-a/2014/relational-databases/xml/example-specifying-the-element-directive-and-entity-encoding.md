---
title: '例 : ELEMENT ディレクティブとエンティティのエンコードを指定する | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ba4e419d31aa7c02cc2dc8f19a3350c233f042b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711793"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a><span data-ttu-id="b6d53-102">例:ELEMENT ディレクティブとエンティティのエンコードの指定</span><span class="sxs-lookup"><span data-stu-id="b6d53-102">Example: Specifying the ELEMENT Directive and Entity Encoding</span></span>
  <span data-ttu-id="b6d53-103">この例では、 **ELEMENT** ディレクティブと **XML** ディレクティブの違いを説明します。</span><span class="sxs-lookup"><span data-stu-id="b6d53-103">This example illustrates the difference between the **ELEMENT** and **XML** directives.</span></span> <span data-ttu-id="b6d53-104">**ELEMENT** ディレクティブを指定した場合はデータがエンティティとしてエンコードされますが、 **XML** ディレクティブを指定した場合はその処理が行われません。</span><span class="sxs-lookup"><span data-stu-id="b6d53-104">The **ELEMENT** directive entitizes the data, but the **XML** directive does not.</span></span> <span data-ttu-id="b6d53-105">このクエリでは、\<Summary> 要素に、`<Summary>This is summary description</Summary>` のように XML が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="b6d53-105">The \<Summary> element is assigned XML, `<Summary>This is summary description</Summary>`, in the query.</span></span>  
  
 <span data-ttu-id="b6d53-106">次のクエリについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="b6d53-106">Consider this query:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="b6d53-107">結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b6d53-107">This is the result.</span></span> <span data-ttu-id="b6d53-108">概要説明がエンティティとしてエンコードされています。</span><span class="sxs-lookup"><span data-stu-id="b6d53-108">The summary description is entitized in the result.</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="b6d53-109">ここで、 **のように、列名に** ELEMENT `Summary!2!SummaryDescription!XML`ディレクティブではなく **XML** ディレクティブを指定すると、概要情報のエンコード処理が行われません。</span><span class="sxs-lookup"><span data-stu-id="b6d53-109">Now, if you specify the **XML** directive in the column name, `Summary!2!SummaryDescription!XML`, instead of the **ELEMENT** directive, you will receive the summary description without entitization.</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="b6d53-110">次のクエリでは、静的な XML 値を割り当てる代わりに、 **xml** 型の **query()** メソッドを使用して、 **xml** 型の CatalogDescription 列から製品モデルの概要情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="b6d53-110">Instead of assigning a static XML value, the following query uses the **query()** method of the **xml** type to retrieve the product model summary description from the CatalogDescription column of **xml** type.</span></span> <span data-ttu-id="b6d53-111">この場合、結果は **xml** 型であることがわかっているので、エンコード処理が適用されません。</span><span class="sxs-lookup"><span data-stu-id="b6d53-111">Because the result is known to be of **xml** type, no entitization is applied.</span></span>  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6d53-112">参照</span><span class="sxs-lookup"><span data-stu-id="b6d53-112">See Also</span></span>  
 [<span data-ttu-id="b6d53-113">FOR XML での EXPLICIT モードの使用</span><span class="sxs-lookup"><span data-stu-id="b6d53-113">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
