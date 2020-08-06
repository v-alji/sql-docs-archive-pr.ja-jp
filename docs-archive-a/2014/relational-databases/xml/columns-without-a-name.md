---
title: 名前のない列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: rothja
ms.author: jroth
ms.openlocfilehash: 43d1cbce816e4666e6dab52fdffe5850e65740e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713938"
---
# <a name="columns-without-a-name"></a><span data-ttu-id="0c9a2-102">名前のない列</span><span class="sxs-lookup"><span data-stu-id="0c9a2-102">Columns without a Name</span></span>
  <span data-ttu-id="0c9a2-103">名前のない列はインラインになります。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-103">Any column without a name will be inlined.</span></span> <span data-ttu-id="0c9a2-104">たとえば、計算列または入れ子になったスカラー クエリで列の別名を指定しないと、名前のない列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-104">For example, computed columns or nested scalar queries that do not specify column alias will generate columns without any name.</span></span> <span data-ttu-id="0c9a2-105">列が `xml` 型の場合、そのデータ型のインスタンスの内容が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-105">If the column is of `xml` type, the content of that data type instance is inserted.</span></span> <span data-ttu-id="0c9a2-106">それ以外の型の場合は、列の内容がテキスト ノードとして挿入されます。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-106">Otherwise, the column content is inserted as a text node.</span></span>  
  
```  
SELECT 2+2  
FOR XML PATH  
```  
  
 <span data-ttu-id="0c9a2-107">上のクエリは、次の XML を生成します。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-107">Produce this XML.</span></span> <span data-ttu-id="0c9a2-108">既定では、行セットの行ごとに 1 つの <`row`> 要素が、結果の XML に生成されます。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-108">By default, for each row in the rowset, a <`row`> element is generated in the resulting XML.</span></span> <span data-ttu-id="0c9a2-109">これは RAW モードと同じ動作です。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-109">This is the same as RAW mode.</span></span>  
  
 `<row>4</row>`  
  
 <span data-ttu-id="0c9a2-110">次のクエリは 3 列の行セットを返します。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-110">The following query returns a three-column rowset.</span></span> <span data-ttu-id="0c9a2-111">3 番目の名前がない列には、XML データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-111">The third column without a name has XML data.</span></span> <span data-ttu-id="0c9a2-112">PATH モードにより、xml 型のインスタンスが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-112">The PATH mode inserts an instance of the xml type.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 <span data-ttu-id="0c9a2-113">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0c9a2-113">This is the partial result:</span></span>  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location ...LocationID="10" ...></MI:Location>`  
  
 `<MI:Location ...LocationID="20" ...></MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="0c9a2-114">参照</span><span class="sxs-lookup"><span data-stu-id="0c9a2-114">See Also</span></span>  
 [<span data-ttu-id="0c9a2-115">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="0c9a2-115">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
