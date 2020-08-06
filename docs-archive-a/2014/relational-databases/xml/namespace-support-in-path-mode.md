---
title: PATH モードでの名前空間のサポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: rothja
ms.author: jroth
ms.openlocfilehash: abd6cd1f5590bffcd841b07897c9685faed4726f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712833"
---
# <a name="namespace-support-in-path-mode"></a><span data-ttu-id="98aea-102">PATH モードでの名前空間のサポート</span><span class="sxs-lookup"><span data-stu-id="98aea-102">Namespace Support in PATH Mode</span></span>
  <span data-ttu-id="98aea-103">PATH モードでは、WITH NAMESPACES を使用することで名前空間がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="98aea-103">Namespace support in the PATH mode is provided by using WITH NAMESPACES.</span></span> <span data-ttu-id="98aea-104">たとえば、次のクエリは WITH NAMESPACES 構文を使用して、後続の SELECT ステートメントで使用できる名前空間 ("a:") を宣言する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="98aea-104">For example, the following query demonstrates the WITH NAMESPACES syntax to declare a namespace ("a:") that can then be used in the subsequent SELECT statement:</span></span>  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a><span data-ttu-id="98aea-105">例</span><span class="sxs-lookup"><span data-stu-id="98aea-105">Examples</span></span>  
 <span data-ttu-id="98aea-106">次のサンプルでは、PATH モードで SELECT クエリから XML を生成する例を示します。</span><span class="sxs-lookup"><span data-stu-id="98aea-106">These samples illustrate the use of PATH mode in generating XML from a SELECT query.</span></span> <span data-ttu-id="98aea-107">これらのクエリの多くは、ProductModel テーブルの Instructions 列に格納されている、自転車製造手順の XML ドキュメントに対して指定されています。</span><span class="sxs-lookup"><span data-stu-id="98aea-107">Many of these queries are specified against the bicycle manufacturing instructions XML documents that are stored in the Instructions column of the ProductModel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98aea-108">参照</span><span class="sxs-lookup"><span data-stu-id="98aea-108">See Also</span></span>  
 [<span data-ttu-id="98aea-109">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="98aea-109">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
