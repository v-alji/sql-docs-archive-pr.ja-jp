---
title: '例 : ELEMENTS ディレクティブで XSINIL を指定する | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying XSINIL example
ms.assetid: 07c873ff-1f9d-480e-8536-862c39eb8249
author: rothja
ms.author: jroth
ms.openlocfilehash: 7817d2c72909ca66fb9fac10f8fcb32a759faf56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711781"
---
# <a name="example-specifying-xsinil-with-the-elements-directive"></a><span data-ttu-id="3aa42-102">例: ELEMENTS ディレクティブで XSINIL を指定する</span><span class="sxs-lookup"><span data-stu-id="3aa42-102">Example: Specifying XSINIL with the ELEMENTS Directive</span></span>
  <span data-ttu-id="3aa42-103">次のクエリでは、 `ELEMENTS` ディレクティブを指定し、クエリ結果から要素中心の XML を生成します。</span><span class="sxs-lookup"><span data-stu-id="3aa42-103">The following query specifies the `ELEMENTS` directive to generate element-centric XML from the query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aa42-104">例</span><span class="sxs-lookup"><span data-stu-id="3aa42-104">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 <span data-ttu-id="3aa42-105">次に結果の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="3aa42-105">This is the partial result.</span></span>  
  
```  
<row>  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
 <span data-ttu-id="3aa42-106">一部の製品では `Color` 列に NULL 値が含まれるので、その結果の XML では対応する <`Color`> 要素が生成されません。</span><span class="sxs-lookup"><span data-stu-id="3aa42-106">Because the `Color` column has null values for some products, the resulting XML will not generate the corresponding <`Color`> element.</span></span> <span data-ttu-id="3aa42-107">`XSINIL` と共に `ELEMENTS` ディレクティブを追加することにより、結果セット内の Color 列が NULL 値の行も <`Color`> 要素を生成できます。</span><span class="sxs-lookup"><span data-stu-id="3aa42-107">By adding the `XSINIL` directive with `ELEMENTS`, you can generate the <`Color`> element even for NULL color values in the result set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS XSINIL ;  
```  
  
 <span data-ttu-id="3aa42-108">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3aa42-108">This is the partial result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
  <Color xsi:nil="true" />  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3aa42-109">参照</span><span class="sxs-lookup"><span data-stu-id="3aa42-109">See Also</span></span>  
 [<span data-ttu-id="3aa42-110">FOR XML での RAW モードの使用</span><span class="sxs-lookup"><span data-stu-id="3aa42-110">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
