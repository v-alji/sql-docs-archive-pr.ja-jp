---
title: セルの更新 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c3d9a7c27533666c75102d9eac3b8311bfe4af6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738946"
---
# <a name="updating-cells-xmla"></a><span data-ttu-id="f4f55-102">セルの更新 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="f4f55-102">Updating Cells (XMLA)</span></span>
  <span data-ttu-id="f4f55-103">[UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla)コマンドを使用すると、キューブの書き戻しが有効になっているキューブ内の1つ以上のセルの値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f4f55-103">You can use the [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) command to change the value of one or more cells in a cube enabled for cube writeback.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="f4f55-104">更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] されるセルを含むパーティションごとに、更新された情報を個別の書き戻しテーブルに格納します。</span><span class="sxs-lookup"><span data-stu-id="f4f55-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stores the updated information in a separate writeback table for each partition that contains cells to be updated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4f55-105">`UpdateCells` コマンドは、キューブ書き戻し時の割り当てをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="f4f55-105">The `UpdateCells` command does not support allocations during cube writeback.</span></span> <span data-ttu-id="f4f55-106">割り当てられた書き戻しを使用するには、[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドを使用して多次元式 (MDX) の UPDATE ステートメントを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4f55-106">To use allocated writeback, you should use the [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command to send a Multidimensional Expressions (MDX) UPDATE statement.</span></span> <span data-ttu-id="f4f55-107">詳細については、「 [UPDATE CUBE ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4f55-107">For more information, see [UPDATE CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).</span></span>  
  
## <a name="specifying-cells"></a><span data-ttu-id="f4f55-108">セルの指定</span><span class="sxs-lookup"><span data-stu-id="f4f55-108">Specifying Cells</span></span>  
 <span data-ttu-id="f4f55-109">コマンドの[Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)プロパティには `UpdateCells` 、更新するセルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4f55-109">The [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) property of the `UpdateCells` command contains the cells to be updated.</span></span> <span data-ttu-id="f4f55-110">`Cell` プロパティ内の各セルは、セルの序数を使用して識別します。</span><span class="sxs-lookup"><span data-stu-id="f4f55-110">You identify each cell in the `Cell` property using that cell's ordinal number.</span></span> <span data-ttu-id="f4f55-111">概念的には、キューブが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] *p*次元配列であるかのように、キューブ内のセルに数値が付けられます。ここで、 *p*は軸の数です。</span><span class="sxs-lookup"><span data-stu-id="f4f55-111">Conceptually, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numbers cells in a cube as if the cube were a *p*-dimensional array, where *p* is the number of axes.</span></span> <span data-ttu-id="f4f55-112">セルは、行優先順で指定されます。</span><span class="sxs-lookup"><span data-stu-id="f4f55-112">Cells are addressed in row-major order.</span></span> <span data-ttu-id="f4f55-113">次の図は、セルの序数を計算するための公式を示しています。</span><span class="sxs-lookup"><span data-stu-id="f4f55-113">The following illustration shows the formula for calculating the ordinal number of a cell.</span></span>  
  
 <span data-ttu-id="f4f55-114">![セルの序数の位置を計算する式](../../analysis-services/dev-guide/media/cellordinalformula.gif "セルの序数の位置を計算する式")</span><span class="sxs-lookup"><span data-stu-id="f4f55-114">![Formula to calculate the cell ordinal position](../../analysis-services/dev-guide/media/cellordinalformula.gif "Formula to calculate the cell ordinal position")</span></span>  
  
 <span data-ttu-id="f4f55-115">セルの序数がわかれば、そのセルの目的の値を[セルプロパティの](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) [value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla)プロパティで示すことができます。</span><span class="sxs-lookup"><span data-stu-id="f4f55-115">Once you know a cell's ordinal number, you can indicate the intended value of the cell in the [Value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) property of the [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4f55-116">参照</span><span class="sxs-lookup"><span data-stu-id="f4f55-116">See Also</span></span>  
 <span data-ttu-id="f4f55-117">[XMLA&#41;&#40;の要素の更新](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="f4f55-117">[Update Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span></span>  
 [<span data-ttu-id="f4f55-118">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="f4f55-118">Developing with XMLA in Analysis Services</span></span>](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
