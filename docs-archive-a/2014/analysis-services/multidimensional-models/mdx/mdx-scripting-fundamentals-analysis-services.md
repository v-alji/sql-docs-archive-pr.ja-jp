---
title: MDX スクリプティングの基礎 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2f7638339d8fc366ee384d453f6df683f3bd41f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643574"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a><span data-ttu-id="b9391-102">MDX スクリプティングの基礎 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b9391-102">MDX Scripting Fundamentals (Analysis Services)</span></span>
  <span data-ttu-id="b9391-103">では [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、多次元式 (mdx) スクリプトは、キューブに計算を設定する1つ以上の mdx 式またはステートメントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b9391-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script is made up of one or more MDX expressions or statements that populate a cube with calculations.</span></span>  
  
 <span data-ttu-id="b9391-104">MDX スクリプトはキューブの計算プロセスを定義します。</span><span class="sxs-lookup"><span data-stu-id="b9391-104">An MDX script defines the calculation process for a cube.</span></span> <span data-ttu-id="b9391-105">また、MDX スクリプト自体がキューブの一部分だと考えることもできます。</span><span class="sxs-lookup"><span data-stu-id="b9391-105">An MDX script is also considered part of the cube itself.</span></span> <span data-ttu-id="b9391-106">したがって、キューブに関連した MDX スクリプトの内容を変更すると、即座にキューブの計算プロセスが変更されることになります。</span><span class="sxs-lookup"><span data-stu-id="b9391-106">Therefore, changing an MDX script associated with a cube immediately changes the calculation process for the cube.</span></span>  
  
 <span data-ttu-id="b9391-107">MDX スクリプトを生成するには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でキューブ デザイナーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9391-107">To create MDX scripts, you can use Cube Designer in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b9391-108">詳細については、「 [割り当てとその他のスクリプト コマンドの定義](../define-assignments-and-other-script-commands.md) 」および「 [Microsoft SQL Server 2005 の MDX スクリプトの紹介](https://go.microsoft.com/fwlink/?LinkId=81892)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9391-108">For more information, see [Define Assignments and Other Script Commands](../define-assignments-and-other-script-commands.md) and [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).</span></span>  
  
 <span data-ttu-id="b9391-109">MDX クエリおよび計算に関するパフォーマンス問題については、「 [SQL Server Analysis Services パフォーマンス ガイド](https://go.microsoft.com/fwlink/p/?LinkId=399050)」の MDX 最適化のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9391-109">For performance issues related to MDX queries and calculations, see the MDX optimization section in the [SQL Server Analysis Services Performance Guide](https://go.microsoft.com/fwlink/p/?LinkId=399050).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9391-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b9391-110">In This Section</span></span>  
  
|<span data-ttu-id="b9391-111">トピック</span><span class="sxs-lookup"><span data-stu-id="b9391-111">Topic</span></span>|<span data-ttu-id="b9391-112">説明</span><span class="sxs-lookup"><span data-stu-id="b9391-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b9391-113">基本的な MDX スクリプト &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="b9391-113">The Basic MDX Script &#40;MDX&#41;</span></span>](the-basic-mdx-script-mdx.md)|<span data-ttu-id="b9391-114">MDX スクリプトの基礎を詳しく説明します。各キューブに付属している既定の MDX スクリプトについて、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のキューブ内で MDX スクリプトが一般的にどのように機能するかについての説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9391-114">Details the basic MDX script, including the default MDX script provided in each cube, and how MDX scripts generally function within a cube in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="b9391-115">スコープとコンテキストの管理 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="b9391-115">Managing Scope and Context &#40;MDX&#41;</span></span>](managing-scope-and-context-mdx.md)|<span data-ttu-id="b9391-116">MDX スクリプト内でコンテキストとスコープを管理するために [CALCULATE](/sql/mdx/mdx-scripting-calculate) ステートメント、 [SCOPE](/sql/mdx/mdx-scripting-scope) ステートメント、および [This](/sql/mdx/this-mdx) 関数を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9391-116">Describes how to use the [CALCULATE](/sql/mdx/mdx-scripting-calculate) statement, the [SCOPE](/sql/mdx/mdx-scripting-scope) statement, and the [This](/sql/mdx/this-mdx) function to manage context and scope within an MDX script.</span></span>|  
|[<span data-ttu-id="b9391-117">変数とパラメーターの使用 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="b9391-117">Using Variables and Parameters &#40;MDX&#41;</span></span>](using-variables-and-parameters-mdx.md)|<span data-ttu-id="b9391-118">MDX スクリプト内で変数やパラメーターを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9391-118">Describes how to use variables and parameters in an MDX script.</span></span>|  
|[<span data-ttu-id="b9391-119">エラー処理 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="b9391-119">Error Handling &#40;MDX&#41;</span></span>](error-handling-mdx.md)|<span data-ttu-id="b9391-120">MDX スクリプト内でのエラー処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9391-120">Explains error handling within an MDX script.</span></span>|  
|[<span data-ttu-id="b9391-121">サポートされる MDX &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="b9391-121">Supported MDX &#40;MDX&#41;</span></span>](supported-mdx-mdx.md)|<span data-ttu-id="b9391-122">MDX スクリプト内でサポートされる MDX 演算子、ステートメント、関数の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="b9391-122">Provides a list of supported MDX operators, statements, and functions within an MDX script.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9391-123">参照</span><span class="sxs-lookup"><span data-stu-id="b9391-123">See Also</span></span>  
 [<span data-ttu-id="b9391-124">MDX 言語リファレンス &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="b9391-124">MDX Language Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-language-reference-mdx)  
  
  
