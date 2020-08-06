---
title: サポートされる MDX (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], statements
- MDX [Analysis Services], functions
ms.assetid: 308bc0b3-4fd6-4435-972b-5e40d9e3c99b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e8df6a2aa6da6b88a07a2abdef99d6ea03d8eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737027"
---
# <a name="supported-mdx-mdx"></a><span data-ttu-id="add6a-102">サポートされる MDX (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-102">Supported MDX (MDX)</span></span>
  <span data-ttu-id="add6a-103">多次元式 (MDX) スクリプト内では、以下のステートメントおよび関数がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="add6a-103">The following statements and functions are supported within Multidimensional Expressions (MDX) Script:</span></span>  
  
 [<span data-ttu-id="add6a-104">(コメント) (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-104">&#40;Comment&#41; &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="add6a-105">-- &#40;コメント&#41; &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="add6a-105">-- &#40;Comment&#41; &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="add6a-106">コメント &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="add6a-106">Comment &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="add6a-107">ALTER CUBE ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-107">ALTER CUBE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-alter-cube)  
  
> [!NOTE]  
>  <span data-ttu-id="add6a-108">MDX スクリプトでは、既定のメンバーの変更だけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="add6a-108">Only altering the default member is supported in MDX Scripting.</span></span>  
  
 [<span data-ttu-id="add6a-109">CALCULATE ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-109">CALCULATE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-calculate)  
  
 [<span data-ttu-id="add6a-110">CASE ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-110">CASE Statement &#40;MDX&#41;</span></span>](/sql/mdx/case-statement-mdx)  
  
 [<span data-ttu-id="add6a-111">CREATE CELL CALCULATION ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-111">CREATE CELL CALCULATION Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
 [<span data-ttu-id="add6a-112">CREATE MEMBER ステートメント &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="add6a-112">CREATE MEMBER Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-member)  
  
 [<span data-ttu-id="add6a-113">CREATE SET ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-113">CREATE SET Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-set)  
  
 [<span data-ttu-id="add6a-114">EXISTING キーワード (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-114">EXISTING Keyword &#40;MDX&#41;</span></span>](mdx-query-existing-keyword.md)  
  
 [<span data-ttu-id="add6a-115">FREEZE ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-115">FREEZE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-freeze)  
  
 [<span data-ttu-id="add6a-116">IF ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-116">IF Statement  &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-if)  
  
 [<span data-ttu-id="add6a-117">This (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-117">This &#40;MDX&#41;</span></span>](/sql/mdx/this-mdx)  
  
> [!NOTE]  
>  <span data-ttu-id="add6a-118">MDX では、セル プロパティ `BACK_COLOR`、`FORE_COLOR`、`FORMAT_STRING`、`FONT_FLAGS`、`FONT_NAME`、および `FONT_SIZE` への代入がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="add6a-118">MDX supports assignment to the following cell properties: `BACK_COLOR`, `FORE_COLOR`, `FORMAT_STRING`, `FONT_FLAGS`, `FONT_NAME`, and `FONT_SIZE`.</span></span> <span data-ttu-id="add6a-119">詳細については、[「セル プロパティの使用 (MDX)」](mdx-cell-properties-using-cell-properties.md) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="add6a-119">For more information, see [Using Cell Properties &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md).</span></span> <span data-ttu-id="add6a-120">MDX では、 `NON_EMPTY_BEHAVIOR` [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member)ステートメントのプロパティへの代入もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="add6a-120">MDX also supports assignment to the `NON_EMPTY_BEHAVIOR` property of the [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) statement.</span></span>  
  
 [<span data-ttu-id="add6a-121">SCOPE ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="add6a-121">SCOPE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-scope)  
  
## <a name="see-also"></a><span data-ttu-id="add6a-122">参照</span><span class="sxs-lookup"><span data-stu-id="add6a-122">See Also</span></span>  
 [<span data-ttu-id="add6a-123">基本的な MDX スクリプト &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="add6a-123">The Basic MDX Script &#40;MDX&#41;</span></span>](the-basic-mdx-script-mdx.md)  
  
  
