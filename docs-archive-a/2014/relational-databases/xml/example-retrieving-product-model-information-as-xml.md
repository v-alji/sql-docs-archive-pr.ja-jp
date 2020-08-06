---
title: 例:XML での製品モデル情報の取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
author: rothja
ms.author: jroth
ms.openlocfilehash: d580f53c4b5185a8b1b1467c75a08fc6929bdcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641537"
---
# <a name="example-retrieving-product-model-information-as-xml"></a><span data-ttu-id="96a7c-102">例:XML での製品モデル情報の取得</span><span class="sxs-lookup"><span data-stu-id="96a7c-102">Example: Retrieving Product Model Information as XML</span></span>
  <span data-ttu-id="96a7c-103">次の クエリでは、出力モデル情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="96a7c-103">The following query returns product model information.</span></span> <span data-ttu-id="96a7c-104">`RAW` モードは、 `FOR XML` 句で指定します。</span><span class="sxs-lookup"><span data-stu-id="96a7c-104">`RAW` mode is specified in the `FOR XML` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96a7c-105">例</span><span class="sxs-lookup"><span data-stu-id="96a7c-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 <span data-ttu-id="96a7c-106">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="96a7c-106">This is the partial result:</span></span>  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 <span data-ttu-id="96a7c-107">`ELEMENTS` ディレクティブを指定することにより、要素中心の XML を取得できます。</span><span class="sxs-lookup"><span data-stu-id="96a7c-107">You can retrieve element-centric XML by specifying the `ELEMENTS` directive.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 <span data-ttu-id="96a7c-108">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="96a7c-108">This is the result:</span></span>  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 <span data-ttu-id="96a7c-109">結果を `xml` 型で取得するために、必要に応じて `TYPE` ディレクティブを指定できます。</span><span class="sxs-lookup"><span data-stu-id="96a7c-109">You can optionally specify the `TYPE` directive to retrieve the results as `xml` type.</span></span> <span data-ttu-id="96a7c-110">`TYPE` ディレクティブを指定しても、結果の内容は変更されません。</span><span class="sxs-lookup"><span data-stu-id="96a7c-110">The `TYPE` directive does not change the content of the results.</span></span> <span data-ttu-id="96a7c-111">結果のデータ型のみが変更されます。</span><span class="sxs-lookup"><span data-stu-id="96a7c-111">Only the data type of the results is affected.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="96a7c-112">参照</span><span class="sxs-lookup"><span data-stu-id="96a7c-112">See Also</span></span>  
 [<span data-ttu-id="96a7c-113">FOR XML での RAW モードの使用</span><span class="sxs-lookup"><span data-stu-id="96a7c-113">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
