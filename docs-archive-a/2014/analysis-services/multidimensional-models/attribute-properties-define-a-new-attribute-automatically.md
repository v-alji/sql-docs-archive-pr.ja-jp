---
title: 新しい属性を自動的に定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40f9ae1f00dd0a6520c6d1b06111864fba02e8f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741449"
---
# <a name="define-a-new-attribute-automatically"></a><span data-ttu-id="00635-102">新しい属性の自動定義</span><span class="sxs-lookup"><span data-stu-id="00635-102">Define a New Attribute Automatically</span></span>
  <span data-ttu-id="00635-103">ディメンション デザイナーでは、ドラッグ アンド ドロップ編集を使用して、ディメンションに新しい属性を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="00635-103">You can create a new attribute in a dimension by using drag-and-drop editing in the Dimension Designer.</span></span>  
  
### <a name="to-create-a-new-attribute-automatically"></a><span data-ttu-id="00635-104">新しい属性を自動的に作成するには</span><span class="sxs-lookup"><span data-stu-id="00635-104">To create a new attribute automatically</span></span>  
  
1.  <span data-ttu-id="00635-105">ディメンション デザイナーで、属性を作成するディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="00635-105">In Dimension Designer, open the dimension in which you want to create the attribute.</span></span>  
  
2.  <span data-ttu-id="00635-106">**[ディメンション構造]** タブの **[データ ソース ビュー]** ペインで、属性をバインドするテーブルの列を選択し、その列を **[属性]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="00635-106">On the **Dimension Structure** tab, in the **Data Source View** pane, in the table to which you want to bind the attribute, select the column, and then drag the column to the **Attributes** pane.</span></span>  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="00635-107">バインド先の列と同じ名前の新しい属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="00635-107">creates the new attribute that has the same name as the column to which it is bound.</span></span> <span data-ttu-id="00635-108">同じ列を使用する複数の属性がある場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、属性名に番号が追加されます。</span><span class="sxs-lookup"><span data-stu-id="00635-108">If there are multiple attributes that use the same column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] appends a number to the attribute name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00635-109">参照</span><span class="sxs-lookup"><span data-stu-id="00635-109">See Also</span></span>  
 <span data-ttu-id="00635-110">[多次元モデル内のディメンション](dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="00635-110">[Dimensions in Multidimensional Models](dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="00635-111">ディメンションの属性のプロパティの参照</span><span class="sxs-lookup"><span data-stu-id="00635-111">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
