---
title: '[キューブディメンションの追加] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0de75c02c39b0690184f35f2b0b6a07d7ed9a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632801"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="c94bc-102">[キューブ ディメンションの追加] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="c94bc-102">Add Cube Dimension Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c94bc-103">**の** [キューブ ディメンションの追加] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、キューブにデータベース ディメンションへの参照を追加できます。</span><span class="sxs-lookup"><span data-stu-id="c94bc-103">Use the **Add Cube Dimension** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a reference to a database dimension to a cube.</span></span> <span data-ttu-id="c94bc-104">**[キューブ ディメンションの追加]** ダイアログ ボックスは、次のいずれかの操作で表示できます。</span><span class="sxs-lookup"><span data-stu-id="c94bc-104">You can display the **Add Cube Dimension** dialog box by doing one of the following:</span></span>  
  
-   <span data-ttu-id="c94bc-105">キューブ デザイナーの **[キューブ構造]** または **[ディメンションの使用法]** タブにある **[ツール バー]** ペインで、 **[キューブ ディメンションの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c94bc-105">Click **Add Cube Dimension** in the **Toolbar** pane on the **Cube Structure** or **Dimension Usage** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="c94bc-106">キューブ デザイナーの **[キューブ構造]** タブにある **[ディメンション]** ペインを右クリックして、ショートカット メニューの **[キューブ ディメンションの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c94bc-106">Right-click the **Dimensions** pane on the **Cube Structure** tab in Cube Designer and select **Add Cube Dimension** from the context menu.</span></span>  
  
-   <span data-ttu-id="c94bc-107">キューブ デザイナーの **[ディメンションの使用法]** タブにある **[グリッド]** ペインを右クリックして、ショートカット メニューの **[キューブ ディメンションの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c94bc-107">Right-click the **Grid** pane on the **Dimension Usage** tab in Cube Designer and select **Add Cube Dimension** from the context menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c94bc-108">各キューブ ディメンションには、メジャー グループに対するリレーションシップを 1 つのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="c94bc-108">Each cube dimension can have only one relationship to a measure group.</span></span> <span data-ttu-id="c94bc-109">しかし、データ ソース ビューで、キューブ ディメンションの基となるデータベース ディメンションが複数のリレーションシップによりメジャー グループに関連付けられている場合、複数のキューブ ディメンションを作成してキューブに追加できます。</span><span class="sxs-lookup"><span data-stu-id="c94bc-109">However, you can create more than one cube dimension and add it to the cube, if the database dimension on which the cube dimension is based is related to measure groups through more than one relationship in the data source view.</span></span> <span data-ttu-id="c94bc-110">このようなディメンションを多様ディメンションと呼び、一般的には時間ディメンションに使用されます。</span><span class="sxs-lookup"><span data-stu-id="c94bc-110">Such dimensions are referred to as role-playing dimensions and commonly occur with time dimensions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c94bc-111">Options</span><span class="sxs-lookup"><span data-stu-id="c94bc-111">Options</span></span>  
 <span data-ttu-id="c94bc-112">**[ディメンションの選択]**</span><span class="sxs-lookup"><span data-stu-id="c94bc-112">**Select dimension**</span></span>  
 <span data-ttu-id="c94bc-113">選択したキューブに追加されるキューブ ディメンションの基となる、既存のデータベース ディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c94bc-113">Select an existing database dimension to add a cube dimension based on it to the selected cube.</span></span> <span data-ttu-id="c94bc-114">同じデータベース ディメンションから、複数のキューブ ディメンションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="c94bc-114">Multiple cube dimensions can be defined from the same database dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c94bc-115">同じデータベース ディメンションに基づく複数のキューブ ディメンションがキューブに追加される場合、追加されるキューブ ディメンションは多様ディメンションと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c94bc-115">If more than one cube dimension based on the same database dimension is added to a cube, the additional cube dimensions are called role-playing dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94bc-116">参照</span><span class="sxs-lookup"><span data-stu-id="c94bc-116">See Also</span></span>  
 [<span data-ttu-id="c94bc-117">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="c94bc-117">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
