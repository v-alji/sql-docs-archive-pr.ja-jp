---
title: 文字列の余白 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3985fd1b2f29260e2313a761797d2528f5d0e328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716465"
---
# <a name="string-padding-ssis"></a><span data-ttu-id="c4cc5-102">文字列の余白 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="c4cc5-102">String Padding (SSIS)</span></span>
  <span data-ttu-id="c4cc5-103">式エバリュエーターは、文字列の先頭および末尾にスペースが含まれているかどうかをチェックしません。また、文字列を比較する前に、比較文字列の長さが同じになるように文字列を埋め込む処理も行いません。</span><span class="sxs-lookup"><span data-stu-id="c4cc5-103">The expression evaluator does not check if a string contains leading and trailing spaces, and it does not pad strings to make them the same length before it compares them.</span></span> <span data-ttu-id="c4cc5-104">式に文字列の余白が必要な場合、+ 演算子を使用して列の値と空白の文字列を連結できます。</span><span class="sxs-lookup"><span data-stu-id="c4cc5-104">If expressions requires string padding, you can use the + operator to concatenate column values and blank strings.</span></span> <span data-ttu-id="c4cc5-105">詳細については、「[+ &#40;連結&#41; &#40;SSIS 式&#41;](concatenate-ssis-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4cc5-105">For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="c4cc5-106">これに対し、スペースを削除する場合、式エバリュエーターで用意されている LTRIM、RTRIM、および TRIM 関数を使用して、先頭または末尾のスペース、またはその両方を削除できます。</span><span class="sxs-lookup"><span data-stu-id="c4cc5-106">On the other hand, if you want to remove spaces, the expression evaluator provides the LTRIM, RTRIM, and TRIM functions, which remove leading or trailing spaces, or both.</span></span> <span data-ttu-id="c4cc5-107">詳細については、「[LTRIM &#40;SSIS 式&#41;](trim-ssis-expression.md)」、「[RTRIM &#40;SSIS 式&#41;](rtrim-ssis-expression.md)」、および「[TRIM &#40;SSIS 式&#41;](trim-ssis-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4cc5-107">For more information, see [LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md), [RTRIM &#40;SSIS Expression&#41;](rtrim-ssis-expression.md), and [TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4cc5-108">LEN 関数は、先頭と末尾の空白を含めてカウントします。</span><span class="sxs-lookup"><span data-stu-id="c4cc5-108">The LEN function includes leading and trailing blanks in its count.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="c4cc5-109">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="c4cc5-109">Related Content</span></span>  
 <span data-ttu-id="c4cc5-110">pragmaticworks.com の技術記事「 [SSIS 式チート シート](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
)」</span><span class="sxs-lookup"><span data-stu-id="c4cc5-110">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
), on pragmaticworks.com</span></span>  
  
  
