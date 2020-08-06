---
title: '例: CDATA ディレクティブの指定 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- CDATA directive
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
author: rothja
ms.author: jroth
ms.openlocfilehash: 9b4f949ae1e9f309a13906efe44b329db2e47ec1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711798"
---
# <a name="example-specifying-the-cdata-directive"></a><span data-ttu-id="51972-102">例:CDATA ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="51972-102">Example: Specifying the CDATA Directive</span></span>
  <span data-ttu-id="51972-103">**CDATA**ディレクティブが指定されている場合、含まれているデータはエンティティとしてエンコードされず、CDATA セクションに配置されます。</span><span class="sxs-lookup"><span data-stu-id="51972-103">If the directive is set to **CDATA**, the contained data is not entity encoded, but is put in the CDATA section.</span></span> <span data-ttu-id="51972-104">**CDATA** 属性は、無名でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="51972-104">The **CDATA** attributes must be nameless.</span></span>  
  
 <span data-ttu-id="51972-105">次のクエリでは、製品モデルの概要説明を CDATA セクションに配置しています。</span><span class="sxs-lookup"><span data-stu-id="51972-105">The following query wraps the product model summary description in a CDATA section.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="51972-106">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51972-106">This is the result:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51972-107">参照</span><span class="sxs-lookup"><span data-stu-id="51972-107">See Also</span></span>  
 [<span data-ttu-id="51972-108">FOR XML での EXPLICIT モードの使用</span><span class="sxs-lookup"><span data-stu-id="51972-108">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
