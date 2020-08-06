---
title: FORE_COLOR と BACK_COLOR の内容 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 748754ec3c90bb44392d7acb7de8f815be24086e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737044"
---
# <a name="fore_color-and-back_color-contents-mdx"></a><span data-ttu-id="4cf13-102">FORE_COLOR および BACK_COLOR の内容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="4cf13-102">FORE_COLOR and BACK_COLOR Contents (MDX)</span></span>
  <span data-ttu-id="4cf13-103">セル プロパティ `FORE_COLOR` および `BACK_COLOR` は、セルのテキストの色および背景色についての情報を Microsoft Windows オペレーティング システムの赤緑青 (RGB) 形式で格納します。</span><span class="sxs-lookup"><span data-stu-id="4cf13-103">The `FORE_COLOR` and `BACK_COLOR` cell properties store color information for the text and the background of a cell, respectively, in the Microsoft Windows operating system red-green-blue (RGB) format.</span></span>  
  
 <span data-ttu-id="4cf13-104">通常の RGB 色の有効範囲は 0 ～ 16,777,215 (&H00FFFFFF) です。</span><span class="sxs-lookup"><span data-stu-id="4cf13-104">The valid range for an ordinary RGB color is zero (0) to 16,777,215 (&H00FFFFFF).</span></span> <span data-ttu-id="4cf13-105">この範囲の高位バイトは常に 0 で、最も低いバイトから意味を成すバイトまでの下位 3 バイトによって、赤、緑、および青それぞれの量が決まります。</span><span class="sxs-lookup"><span data-stu-id="4cf13-105">The high byte of a number in this range always equals 0; the lower 3 bytes, from least to most significant byte, determine the amount of red, green, and blue, respectively.</span></span> <span data-ttu-id="4cf13-106">赤、緑、および青のコンポーネントは、それぞれ 0 ～ 255 (&HFF) までの数値で表されます。</span><span class="sxs-lookup"><span data-stu-id="4cf13-106">The red, green, and blue components are each represented by a number between 0 and 255 (&HFF).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf13-107">参照</span><span class="sxs-lookup"><span data-stu-id="4cf13-107">See Also</span></span>  
 [<span data-ttu-id="4cf13-108">セル プロパティの使用 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf13-108">Using Cell Properties &#40;MDX&#41;</span></span>](mdx-cell-properties-using-cell-properties.md)  
  
  
