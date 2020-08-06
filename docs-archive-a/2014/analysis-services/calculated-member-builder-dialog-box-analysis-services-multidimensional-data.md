---
title: '[計算されるメンバービルダー] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.calculatedmemberbuilderdialog.f1
ms.assetid: 73b89a9f-f403-4ab8-99f7-e3ceb870c260
author: minewiskan
ms.author: owend
ms.openlocfilehash: 240e2f2471bf77c403119fd51278a975badc8358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633551"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="67b8d-102">[計算されるメンバー ビルダー] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="67b8d-102">Calculated Member Builder Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="67b8d-103">**の** [計算されるメンバー ビルダー] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用して、計算されるメンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="67b8d-103">Use the **Calculated Member Builder** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to build a calculated member.</span></span>  
  
## <a name="options"></a><span data-ttu-id="67b8d-104">Options</span><span class="sxs-lookup"><span data-stu-id="67b8d-104">Options</span></span>  
  
|<span data-ttu-id="67b8d-105">期間</span><span class="sxs-lookup"><span data-stu-id="67b8d-105">Term</span></span>|<span data-ttu-id="67b8d-106">定義</span><span class="sxs-lookup"><span data-stu-id="67b8d-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="67b8d-107">**名前**</span><span class="sxs-lookup"><span data-stu-id="67b8d-107">**Name**</span></span>|<span data-ttu-id="67b8d-108">計算されるメンバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="67b8d-108">Type the name of the calculated member.</span></span>|  
|<span data-ttu-id="67b8d-109">**親階層**</span><span class="sxs-lookup"><span data-stu-id="67b8d-109">**Parent Hierarchy**</span></span>|<span data-ttu-id="67b8d-110">計算されるメンバーを作成する階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="67b8d-110">Select the hierarchy in which to create the calculated member.</span></span>|  
|<span data-ttu-id="67b8d-111">**親メンバー**</span><span class="sxs-lookup"><span data-stu-id="67b8d-111">**Parent Member**</span></span>|<span data-ttu-id="67b8d-112">複数のレベルを含む親階層 (`Measures` ディメンション以外) を選択した場合は、このオプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="67b8d-112">This option is enabled if you select a parent hierarchy (other than the `Measures` dimension) that has more than one level.</span></span> <span data-ttu-id="67b8d-113">省略記号ボタン ([**..**.]) をクリックして、親メンバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="67b8d-113">Click the ellipsis (**...**) button to select a parent member.</span></span> <span data-ttu-id="67b8d-114">親メンバーによって、ディメンション構造内における計算されるメンバーの位置が決まります。</span><span class="sxs-lookup"><span data-stu-id="67b8d-114">The parent member determines the location of the calculated member in the dimension structure.</span></span>|  
|<span data-ttu-id="67b8d-115">**[式]**</span><span class="sxs-lookup"><span data-stu-id="67b8d-115">**Expression**</span></span>|<span data-ttu-id="67b8d-116">使用する MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="67b8d-116">Type the MDX expression that will be used.</span></span>|  
|<span data-ttu-id="67b8d-117">**確認事項**</span><span class="sxs-lookup"><span data-stu-id="67b8d-117">**Check**</span></span>|<span data-ttu-id="67b8d-118">**[式]** で定義された MDX 式をテストするには、 **[確認]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67b8d-118">Click **Check** to test the MDX expression defined in **Expression**.</span></span>|  
|<span data-ttu-id="67b8d-119">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="67b8d-119">**Metadata**</span></span>|<span data-ttu-id="67b8d-120">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [式] **で定義された MDX 式に含めることができる現在の**オブジェクトのメタデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="67b8d-120">Displays metadata for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object that can be included in the MDX expression defined in **Expression**.</span></span><br /><br /> <span data-ttu-id="67b8d-121">選択されたアイテムの MDX 構文をコピーするには、アイテムを右クリックし、 **[コピー]** を選択するか、選択したアイテムを **[式]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="67b8d-121">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy**, or by dragging the selected item to **Expression**.</span></span>|  
|<span data-ttu-id="67b8d-122">**関数**</span><span class="sxs-lookup"><span data-stu-id="67b8d-122">**Functions**</span></span>|<span data-ttu-id="67b8d-123">現在の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで使用可能な MDX 関数を表示します。</span><span class="sxs-lookup"><span data-stu-id="67b8d-123">Displays the available MDX functions for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="67b8d-124">一覧表示されたアイテムは、MDSCHEMA_FUNCTIONS スキーマ行セットから取得されます。</span><span class="sxs-lookup"><span data-stu-id="67b8d-124">The items listed are retrieved from the MDSCHEMA_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="67b8d-125">選択されたアイテムの MDX 構文をコピーするには、アイテムを右クリックし、 **[コピー]** を選択するか、選択したアイテムを **[式]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="67b8d-125">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy**, or by dragging the selected item to **Expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67b8d-126">参照</span><span class="sxs-lookup"><span data-stu-id="67b8d-126">See Also</span></span>  
 [<span data-ttu-id="67b8d-127">多次元式 &#40;MDX&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="67b8d-127">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
