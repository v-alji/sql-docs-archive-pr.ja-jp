---
title: XSINIL パラメーターを使用した NULL 値に対する要素の生成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 602de12b5aa9be8997fbd49a2f23e0b73444aac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743062"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a><span data-ttu-id="18364-102">XSINIL パラメーターを使用した NULL 値に対する要素の生成</span><span class="sxs-lookup"><span data-stu-id="18364-102">Generate Elements for NULL Values with the XSINIL Parameter</span></span>
  <span data-ttu-id="18364-103">**ELEMENTS** ディレクティブにより構成される XML では、各列の値が XML の要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="18364-103">The **ELEMENTS** directive constructs XML in which each column value maps to an element in the XML.</span></span> <span data-ttu-id="18364-104">列の値が NULL の場合、要素は追加されません。</span><span class="sxs-lookup"><span data-stu-id="18364-104">If the column value is NULL, no element is added.</span></span> <span data-ttu-id="18364-105">ELEMENTS ディレクティブでオプションの **XSINIL** パラメーターを指定すると、NULL 値に対しても要素を作成するように要求できます。</span><span class="sxs-lookup"><span data-stu-id="18364-105">By specifying the optional **XSINIL** parameter on the ELEMENTS directive, you can request that an element also be created for the NULL value.</span></span> <span data-ttu-id="18364-106">この場合、値が NULL の各列に対して、TRUE に設定された **xsi:nil** 属性を持つ要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="18364-106">In this case, an element that has the **xsi:nil** attribute set to TRUE is returned for each NULL column value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18364-107">参照</span><span class="sxs-lookup"><span data-stu-id="18364-107">See Also</span></span>  
 [<span data-ttu-id="18364-108">FOR XML での RAW モードの使用</span><span class="sxs-lookup"><span data-stu-id="18364-108">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
