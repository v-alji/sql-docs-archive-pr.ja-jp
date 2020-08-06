---
title: 例:&lt;row&gt; 要素の名前を変更する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: rothja
ms.author: jroth
ms.openlocfilehash: 39375fa125f451f21d936b3a6897b93928fa2f02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631685"
---
# <a name="example-renaming-the-ltrowgt-element"></a><span data-ttu-id="af53b-102">例:&lt;row&gt; 要素の名前を変更する</span><span class="sxs-lookup"><span data-stu-id="af53b-102">Example: Renaming the &lt;row&gt; Element</span></span>
  <span data-ttu-id="af53b-103">結果セットの各行では、RAW モードによって `<row>`要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="af53b-103">For each row in the result set, the RAW mode generates an element `<row>`.</span></span> <span data-ttu-id="af53b-104">次のクエリに示すように、必要に応じて、RAW モードへの省略可能な引数を指定することにより、この要素に別の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="af53b-104">You can optionally specify another name for this element by specifying an optional argument to the RAW mode, as shown in this query.</span></span> <span data-ttu-id="af53b-105">クエリでは、行セットの行ごとに <`ProductModel`> 要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="af53b-105">The query returns a <`ProductModel`> element for each row in the rowset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af53b-106">例</span><span class="sxs-lookup"><span data-stu-id="af53b-106">Example</span></span>  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 <span data-ttu-id="af53b-107">結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="af53b-107">This is the result.</span></span> <span data-ttu-id="af53b-108">`ELEMENTS` ディレクティブがクエリに追加されたので、結果は要素中心になります。</span><span class="sxs-lookup"><span data-stu-id="af53b-108">Because the `ELEMENTS` directive is added in the query, the result is element-centric.</span></span>  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a><span data-ttu-id="af53b-109">参照</span><span class="sxs-lookup"><span data-stu-id="af53b-109">See Also</span></span>  
 [<span data-ttu-id="af53b-110">FOR XML での RAW モードの使用</span><span class="sxs-lookup"><span data-stu-id="af53b-110">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
