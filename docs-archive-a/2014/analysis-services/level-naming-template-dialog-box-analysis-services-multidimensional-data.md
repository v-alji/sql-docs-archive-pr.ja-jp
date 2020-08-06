---
title: '[レベル名前付けテンプレート] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dd704e619e49f0dd1adb8fed8f1e743b61309af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743574"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="11d1f-102">[レベル名前付けテンプレート] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="11d1f-102">Level Naming Template Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="11d1f-103">**の** [レベル名前付けテンプレート] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、ディメンション内の親属性のレベル名前付けテンプレートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="11d1f-103">Use the **Level Naming Template** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to construct the level naming template for a parent attribute in a dimension.</span></span> <span data-ttu-id="11d1f-104">レベル名前付けテンプレートの詳細については、「[NamingTemplate 要素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11d1f-104">For more information about level naming templates, see [NamingTemplate Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl).</span></span> <span data-ttu-id="11d1f-105">[**レベル名前付けテンプレート**] ダイアログボックスを表示するには、**...** `NamingTemplate` **ディメンションデザイナー**の **[翻訳**] タブの [**翻訳の詳細**] ペインで、属性の翻訳の値の省略記号ボタン ([...]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11d1f-105">You can display the **Level Naming Template** dialog box by clicking the ellipsis button (**...**) on the `NamingTemplate` value of a translation for an attribute in the **Translation Details** pane on the **Translations** tab of **Dimension Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="11d1f-106">Options</span><span class="sxs-lookup"><span data-stu-id="11d1f-106">Options</span></span>  
  
|<span data-ttu-id="11d1f-107">期間</span><span class="sxs-lookup"><span data-stu-id="11d1f-107">Term</span></span>|<span data-ttu-id="11d1f-108">定義</span><span class="sxs-lookup"><span data-stu-id="11d1f-108">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="11d1f-109">**[レベル テンプレートの定義]**</span><span class="sxs-lookup"><span data-stu-id="11d1f-109">**Define the level template**</span></span>|<span data-ttu-id="11d1f-110">親属性のレベルの階層を設計するためのグリッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="11d1f-110">Displays a grid in which you can design the hierarchy of levels in the parent attribute.</span></span> <span data-ttu-id="11d1f-111">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="11d1f-111">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="11d1f-112">**Level**: **name**に指定された名前が使用されるレベルの序数位置を表示します。</span><span class="sxs-lookup"><span data-stu-id="11d1f-112">**Level**: Displays the ordinal position of the level for which the name specified in **Name** is used.</span></span> <span data-ttu-id="11d1f-113">レベルに新しい名前付けテンプレートを追加するには、 **[レベル]** のアスタリスク (\*) を含む行で **[名前]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="11d1f-113">To add a new naming template for a level, select **Name** on the row that contains an asterisk (\*) in **Level**.</span></span><br /><br /> <span data-ttu-id="11d1f-114">**名前**:**レベル**で示されるレベルに使用される名前付けテンプレートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="11d1f-114">**Name**: Contains the naming template used for the level indicated in **Level**.</span></span> <span data-ttu-id="11d1f-115">名前付けテンプレートのレベルの順位に対してプレースホルダーを追加するには、1 つのアスタリスク (\*) を追加します。</span><span class="sxs-lookup"><span data-stu-id="11d1f-115">To add a placeholder for the level ordinal position in the naming template, add a single asterisk (\*).</span></span> <span data-ttu-id="11d1f-116">名前付けテンプレートによって作成された名前の一部としてアスタリスクを追加するには、2つのアスタリスク () を追加し \* \* ます。</span><span class="sxs-lookup"><span data-stu-id="11d1f-116">To add an asterisk as part of the name created by the naming template, add two asterisks (\*\*).</span></span>|  
|<span data-ttu-id="11d1f-117">**すべてクリア**</span><span class="sxs-lookup"><span data-stu-id="11d1f-117">**Clear All**</span></span>|<span data-ttu-id="11d1f-118">クリックすると、 **[レベル テンプレートの定義]** の行がすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="11d1f-118">Select to remove all rows in **Define the level template**.</span></span>|  
|<span data-ttu-id="11d1f-119">**結果**</span><span class="sxs-lookup"><span data-stu-id="11d1f-119">**Result**</span></span>|<span data-ttu-id="11d1f-120">ダイアログ ボックスによって構築されたレベルの名前付けテンプレートを表示します。</span><span class="sxs-lookup"><span data-stu-id="11d1f-120">Displays the level naming template constructed by the dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11d1f-121">参照</span><span class="sxs-lookup"><span data-stu-id="11d1f-121">See Also</span></span>  
 <span data-ttu-id="11d1f-122">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="11d1f-122">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="11d1f-123">翻訳 &#40;ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="11d1f-123">Translations &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
