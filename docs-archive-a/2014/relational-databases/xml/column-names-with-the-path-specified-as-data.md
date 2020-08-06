---
title: パスを data() として指定した列の名前 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: rothja
ms.author: jroth
ms.openlocfilehash: 61aa7f85c7ee2358ddcf99f81c87c1295fac8fb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631694"
---
# <a name="column-names-with-the-path-specified-as-data"></a><span data-ttu-id="b3bae-102">パスを data() として指定した列の名前</span><span class="sxs-lookup"><span data-stu-id="b3bae-102">Column Names with the Path Specified as data()</span></span>
  <span data-ttu-id="b3bae-103">列名として指定したパスが "data()" の場合、生成される XML では列の値がアトミック値として処理されます。</span><span class="sxs-lookup"><span data-stu-id="b3bae-103">If the path specified as column name is "data()", the value is treated as an atomic value in the generated XML.</span></span> <span data-ttu-id="b3bae-104">シリアル化時の後続アイテムもアトミック値である場合は、空白文字が XML に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b3bae-104">A space character is added to the XML if the next item in the serialization is also an atomic value.</span></span> <span data-ttu-id="b3bae-105">これはリスト状の要素値または属性値を作成する場合に有用です。</span><span class="sxs-lookup"><span data-stu-id="b3bae-105">This is useful when you are creating list typed element and attribute values.</span></span> <span data-ttu-id="b3bae-106">次のクエリでは、製品モデルの ID および名前と、そのモデルに含まれる製品のリストを取得します。</span><span class="sxs-lookup"><span data-stu-id="b3bae-106">The following query retrieves the product model ID, name, and list of products in that product model.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 <span data-ttu-id="b3bae-107">入れ子の内側の SELECT では、製品 ID のリストを取得しています。</span><span class="sxs-lookup"><span data-stu-id="b3bae-107">The nested SELECT retrieves a list of product IDs.</span></span> <span data-ttu-id="b3bae-108">製品 ID の列名が "data()" と指定されています。</span><span class="sxs-lookup"><span data-stu-id="b3bae-108">It specifies "data()" as the column name for product IDs.</span></span> <span data-ttu-id="b3bae-109">PATH モードでは空文字列が行の要素名に指定されるので、ここでは行要素は生成されません。</span><span class="sxs-lookup"><span data-stu-id="b3bae-109">Because PATH mode specifies an empty string for the row element name, there is no row element generated.</span></span> <span data-ttu-id="b3bae-110">代わりに、親の SELECT で指定した <`ProductModelData`> 行要素の ProductIDs 属性に設定された値が返されます。</span><span class="sxs-lookup"><span data-stu-id="b3bae-110">Instead, the values are returned as assigned to a ProductIDs attribute of the <`ProductModelData`> row element of the parent SELECT.</span></span> <span data-ttu-id="b3bae-111">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b3bae-111">This is the result:</span></span>  
  
 `<ProductModelData ProductModelID="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 888 889 890 891 892 893" />`  
  
## <a name="see-also"></a><span data-ttu-id="b3bae-112">参照</span><span class="sxs-lookup"><span data-stu-id="b3bae-112">See Also</span></span>  
 [<span data-ttu-id="b3bae-113">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="b3bae-113">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
