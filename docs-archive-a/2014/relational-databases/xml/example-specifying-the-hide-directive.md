---
title: '例: HIDE ディレクティブの指定 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- HIDE directive
ms.assetid: 87504d87-1cbd-412a-9041-47884b6efcec
author: rothja
ms.author: jroth
ms.openlocfilehash: 423ee36f679467c07a604b9754172f6e261971b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644357"
---
# <a name="example-specifying-the-hide-directive"></a><span data-ttu-id="a1ece-102">例: HIDE ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="a1ece-102">Example: Specifying the HIDE Directive</span></span>
  <span data-ttu-id="a1ece-103">この例では、 **HIDE** ディレクティブの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a1ece-103">This example illustrates the use of the **HIDE** directive.</span></span> <span data-ttu-id="a1ece-104">クエリから返されたユニバーサル テーブル内の行を並べ替える目的でクエリから属性を返し、最終的な結果の XML ドキュメントにはその属性を含めない場合に、このディレクティブが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a1ece-104">This directive is useful when you want the query to return an attribute for ordering the rows in the universal table that is returned by the query, but you do not want that attribute in the final resulting XML document.</span></span>  
  
 <span data-ttu-id="a1ece-105">このクエリでは、次の XML を生成します。</span><span class="sxs-lookup"><span data-stu-id="a1ece-105">This query constructs this XML:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
           <Summary> element from XML stored in CatalogDescription column  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="a1ece-106">このクエリでは、求める XML を生成しています。</span><span class="sxs-lookup"><span data-stu-id="a1ece-106">This query generates the XML you want.</span></span> <span data-ttu-id="a1ece-107">Tag 列に値 1 と 2 を持つ 2 つの列グループが識別されます。</span><span class="sxs-lookup"><span data-stu-id="a1ece-107">The query identifies two column groups having 1 and 2 as Tag values in the column names.</span></span>  
  
 <span data-ttu-id="a1ece-108">このクエリでは、xml データ型の [query()](/sql/t-sql/xml/query-method-xml-data-type) メソッド ( **xml** データ型) を使用し、 **xml** 型の CatalogDescription 列に対するクエリを実行して、概要情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a1ece-108">This query uses the [query() Method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) of the **xml** data type to query the CatalogDescription column of **xml** type in order to retrieve the summary description.</span></span> <span data-ttu-id="a1ece-109">また、このクエリでは、 [xml](/sql/t-sql/xml/value-method-xml-data-type) データ型の **value() メソッド (xml データ型)** を使用して、CatalogDescription 列から ProductModelID 値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a1ece-109">The query also uses the [value() Method (xml Data Type)](/sql/t-sql/xml/value-method-xml-data-type) of the **xml** data type to retrieve the ProductModelID value from the CatalogDescription column.</span></span> <span data-ttu-id="a1ece-110">この値は、結果の行セットを並べ替えるために必要ですが、結果の XML ドキュメントでは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a1ece-110">This value is not required in the resulting XML, but is required to sort the resulting rowset.</span></span> <span data-ttu-id="a1ece-111">そのため、列名 `[Summary!2!ProductModelID!HIDE]`には、 **HIDE** ディレクティブが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1ece-111">Therefore, the column name, `[Summary!2!ProductModelID!HIDE]`, includes the **HIDE** directive.</span></span> <span data-ttu-id="a1ece-112">この列が SELECT ステートメントに含まれていなければ、 `[ProductModel!1!ProdModelID]` xml `[Summary!2!SummaryDescription]` 型の **列と** 列で行セットを並べ替える必要がありますが、ORDER BY 句では **xml** 型を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a1ece-112">If this column is not included in the SELECT statement, you will have to sort the rowset by `[ProductModel!1!ProdModelID]` and `[Summary!2!SummaryDescription]` that is **xml** type and you cannot use the **xml** type column in ORDER BY.</span></span> <span data-ttu-id="a1ece-113">このため、 `[Summary!2!ProductModelID!HIDE]` 列を追加し、これを ORDER BY 句で指定しています。</span><span class="sxs-lookup"><span data-stu-id="a1ece-113">Therefore, the additional `[Summary!2!ProductModelID!HIDE]` column is added and is then specified in the ORDER BY clause.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID     as [ProductModel!1!ProdModelID],  
        Name               as [ProductModel!1!Name],  
        NULL               as [Summary!2!ProductModelID!hide],  
        NULL               as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
        CatalogDescription.value('  
         declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       (/PD:ProductDescription/@ProductModelID)[1]', 'int'),  
        CatalogDescription.query('  
         declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /pd:ProductDescription/pd:Summary')  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],[Summary!2!ProductModelID!hide]  
FOR XML EXPLICIT  
go  
```  
  
 <span data-ttu-id="a1ece-114">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a1ece-114">This is the result:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription" xmlns="">  
        <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike. Performance-enhancing options include the innovative HL Frame, super-smooth front suspension, and traction for all terrain. </p1:p>  
      </pd:Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1ece-115">参照</span><span class="sxs-lookup"><span data-stu-id="a1ece-115">See Also</span></span>  
 [<span data-ttu-id="a1ece-116">FOR XML での EXPLICIT モードの使用</span><span class="sxs-lookup"><span data-stu-id="a1ece-116">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
