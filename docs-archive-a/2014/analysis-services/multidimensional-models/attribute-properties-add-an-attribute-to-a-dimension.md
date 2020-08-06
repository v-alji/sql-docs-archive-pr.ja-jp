---
title: ディメンションに属性を追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
author: minewiskan
ms.author: owend
ms.openlocfilehash: 776591e94deedc679592cfe36d53fb1fea4093d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645218"
---
# <a name="add-an--attribute-to-a-dimension"></a><span data-ttu-id="6c9a9-102">ディメンションへの属性の追加</span><span class="sxs-lookup"><span data-stu-id="6c9a9-102">Add an  Attribute to a Dimension</span></span>
  <span data-ttu-id="6c9a9-103">では、自動または手動で、属性をディメンションに追加でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-103">You can add an attribute to a dimension either automatically or manually in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6c9a9-104">属性を自動的に作成するには、 **のディメンション デザイナーの** [ディメンション構造] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、属性にマッピングする列を選択し、その列を **[データ ソース ビュー]** ペインから **[属性]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-104">To create an attribute automatically, on the **Dimension Structure** tab of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the column that you want to map to an attribute, and then drag that column from the **Data Source View** pane to the **Attributes** pane.</span></span> <span data-ttu-id="6c9a9-105">これにより、列にマッピングされる属性が作成され、列の名前と同じ名前が属性に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-105">This creates an attribute that is mapped to the column, and assigns the same name to the attribute as the name of the column.</span></span> <span data-ttu-id="6c9a9-106">その名前を使用している属性が既に存在する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では序数サフィックスを追加して、最初の重複する名前を "1" から始めます。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-106">If an attribute that uses that name already exists, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] adds an ordinal number suffix, starting with "1" for the first duplicate name.</span></span>  
  
 <span data-ttu-id="6c9a9-107">属性を手動で作成するには、 **[属性]** ペインをグリッド ビューに設定します。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-107">To create an attribute manually, set the **Attributes** pane to grid view.</span></span> <span data-ttu-id="6c9a9-108">グリッドの最後の行の [名前] 列で、項目をクリックし **\<new attribute>** ます。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-108">In the name column of the last row in the grid, click the **\<new attribute>** item.</span></span> <span data-ttu-id="6c9a9-109">新しい属性の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-109">Type a name for the new attribute.</span></span> <span data-ttu-id="6c9a9-110">これにより、列にマッピングされない、すべてのプロパティが既定に設定されている属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-110">This creates an attribute that is not mapped to a column and that has default settings for all its properties.</span></span> <span data-ttu-id="6c9a9-111">新しい属性の **KeyColumns** プロパティを構成して、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] の **[プロパティ]** ウィンドウでマッピングを設定できます。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-111">You can set the mapping in the **Properties** window of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] by configuring the **KeyColumns** property for the new attribute.</span></span>  
  
 <span data-ttu-id="6c9a9-112">詳細については、「 [新しい属性の自動定義](attribute-properties-define-a-new-attribute-automatically.md)」、「 [新しい属性の手動による定義](../define-a-new-attribute-manually.md)」、「 [名前列への属性のバインド](attribute-properties-bind-an-attribute-to-a-name-column.md)」、「 [属性の KeyColumns プロパティの変更](attribute-properties-modify-the-keycolumn-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-112">For more information, see [Define a New Attribute Automatically](attribute-properties-define-a-new-attribute-automatically.md), [Define a New Attribute Manually](../define-a-new-attribute-manually.md), [Bind an Attribute to a Name Column](attribute-properties-bind-an-attribute-to-a-name-column.md), and [Modify the KeyColumn Property of an Attribute](attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9a9-113">参照</span><span class="sxs-lookup"><span data-stu-id="6c9a9-113">See Also</span></span>  
 [<span data-ttu-id="6c9a9-114">ディメンションの属性のプロパティの参照</span><span class="sxs-lookup"><span data-stu-id="6c9a9-114">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
