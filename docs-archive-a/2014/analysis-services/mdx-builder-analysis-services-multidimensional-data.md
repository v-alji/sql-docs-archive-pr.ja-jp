---
title: MDX ビルダー (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.mdxbuilderdialof.f1
helpviewer_keywords:
- MDX Builder dialog box
ms.assetid: fecbf093-65ea-4e1b-b637-f04876f1cb0f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 391f4abe953184470be60cca41d53ee20e965423
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641905"
---
# <a name="mdx-builder-analysis-services---multidimensional-data"></a><span data-ttu-id="ed705-102">MDX ビルダー (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="ed705-102">MDX Builder (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="ed705-103">**または** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [MDX ビルダー] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、多次元式 (MDX) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ed705-103">Use the **MDX Builder** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to build a Multidimensional Expressions (MDX) expression.</span></span> <span data-ttu-id="ed705-104">[ **Mdx ビルダー** ] ダイアログボックスを表示するには、[**キューブコンテンツの読み取りを許可**する] オプション、[セル**の内容**の読み取りを許可する] オプション、または**ロールデザイナー**の [**セルデータ**] ページの [**キューブコンテンツの読み取りと書き込み**を許可する] オプションの [ **mdx の編集**] をクリックします。**...**</span><span class="sxs-lookup"><span data-stu-id="ed705-104">You can display the **MDX Builder** dialog box by clicking the **Edit MDX** ellipsis button (**...**) for the **Allow reading of cube content** option, the **Allow reading of cell content contingent on cell security** option, or the **Allow reading and writing of cube content** option on the **Cell Data** page of **Role Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ed705-105">Options</span><span class="sxs-lookup"><span data-stu-id="ed705-105">Options</span></span>  
  
|<span data-ttu-id="ed705-106">期間</span><span class="sxs-lookup"><span data-stu-id="ed705-106">Term</span></span>|<span data-ttu-id="ed705-107">定義</span><span class="sxs-lookup"><span data-stu-id="ed705-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="ed705-108">**[式]**</span><span class="sxs-lookup"><span data-stu-id="ed705-108">**Expression**</span></span>|<span data-ttu-id="ed705-109">使用する MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="ed705-109">Type the MDX expression to be used.</span></span>|  
|<span data-ttu-id="ed705-110">**確認事項**</span><span class="sxs-lookup"><span data-stu-id="ed705-110">**Check**</span></span>|<span data-ttu-id="ed705-111">**[式]** で定義された MDX 式をテストするには、 **[確認]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed705-111">Click **Check** to test the MDX expression defined in **Expression**.</span></span>|  
|<span data-ttu-id="ed705-112">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="ed705-112">**Metadata**</span></span>|<span data-ttu-id="ed705-113">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [式] **で定義された MDX 式に含めることができる現在の**オブジェクトのメタデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="ed705-113">Displays metadata for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object that can be included in the MDX expression defined in **Expression**.</span></span><br /><br /> <span data-ttu-id="ed705-114">選択されたアイテムの MDX 構文をコピーするには、アイテムを右クリックし、ショートカット メニューから **[コピー]** を選択するか、選択したアイテムを **[式]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ed705-114">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy** from the context menu, or by dragging the selected item to **Expression**.</span></span>|  
|<span data-ttu-id="ed705-115">**関数**</span><span class="sxs-lookup"><span data-stu-id="ed705-115">**Functions**</span></span>|<span data-ttu-id="ed705-116">現在の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで使用可能な MDX 関数を表示します。</span><span class="sxs-lookup"><span data-stu-id="ed705-116">Displays available MDX functions for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="ed705-117">一覧表示されたアイテムは、MDSCHEMA_FUNCTIONS スキーマ行セットから取得されます。</span><span class="sxs-lookup"><span data-stu-id="ed705-117">The items listed are retrieved from the MDSCHEMA_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="ed705-118">選択されたアイテムの MDX 構文をコピーするには、アイテムを右クリックし、ショートカット メニューから **[コピー]** を選択するか、選択したアイテムを **[式]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ed705-118">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy** from the context menu, or by dragging the selected item to **Expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed705-119">参照</span><span class="sxs-lookup"><span data-stu-id="ed705-119">See Also</span></span>  
 <span data-ttu-id="ed705-120">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ed705-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="ed705-121">[セルデータ &#40;ロールデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](https://msdn.microsoft.com/library/ms177279(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="ed705-121">[Cell Data &#40;Role Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms177279(v=sql.120).aspx)</span></span>  
  
  
