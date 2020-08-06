---
title: 警告 (データベースデザイナー) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.warnings.f1
ms.assetid: 13f58b4d-f345-4fbc-ae2d-b3c8290a797d
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf635460187fe56f4811de5090cada002ea8ca3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634649"
---
# <a name="warnings-database-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="e75d7-102">[警告] (データベース デザイナー) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="e75d7-102">Warnings (Database Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e75d7-103">**[警告]** タブを使用すると、ルールをグローバルに表示および消去したり、消去された警告の特定のインスタンスを表示して再度有効にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-103">Use the **Warnings** tab to view and dismiss rules globally, and to view and re-enable specific instances of dismissed warnings.</span></span> <span data-ttu-id="e75d7-104">**[警告]** タブには、 **[デザイン警告ルール]** および **[消去された警告]** という 2 つのグリッドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-104">The **Warnings** tab displays two grids: **Design Warning Rules** and **Dismissed Warnings**.</span></span>  
  
 <span data-ttu-id="e75d7-105">**[警告] タブを表示するには**</span><span class="sxs-lookup"><span data-stu-id="e75d7-105">**To display the Warnings tab**</span></span>  
  
1.  <span data-ttu-id="e75d7-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="e75d7-107">**ソリューション エクスプローラー**で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを右クリックし、 **[データベースの編集]** をクリックして、 **[警告]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e75d7-107">In **Solution Explorer**, right-click the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, click **Edit Database**, and then click the **Warnings** tab.</span></span>  
  
## <a name="design-warning-rules-grid"></a><span data-ttu-id="e75d7-108">[デザイン警告ルール] グリッド</span><span class="sxs-lookup"><span data-stu-id="e75d7-108">Design Warning Rules Grid</span></span>  
 <span data-ttu-id="e75d7-109">**[デザイン警告ルール]** グリッドには、すべてのデザイン警告ルールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-109">The **Design Warning Rules** grid displays all the design warning rules.</span></span> <span data-ttu-id="e75d7-110">このグリッドでは、データベースに有効なルールも制御します。</span><span class="sxs-lookup"><span data-stu-id="e75d7-110">This grid also controls which rules are enabled for the database.</span></span> <span data-ttu-id="e75d7-111">警告ルールを有効または無効にするには、そのチェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="e75d7-111">To enable or disable a warning rule, select or clear its check box.</span></span>  
  
 <span data-ttu-id="e75d7-112">**[デザイン警告ルール]** グリッドには、次の列があります。</span><span class="sxs-lookup"><span data-stu-id="e75d7-112">The **Design Warning Rules** grid has the following columns:</span></span>  
  
 <span data-ttu-id="e75d7-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="e75d7-113">**Description**</span></span>  
 <span data-ttu-id="e75d7-114">ルールの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-114">Displays the name of the rule.</span></span> <span data-ttu-id="e75d7-115">ルールはカテゴリ別にグループ化されています。</span><span class="sxs-lookup"><span data-stu-id="e75d7-115">Rules are grouped by category.</span></span>  
  
 <span data-ttu-id="e75d7-116">**重要度**</span><span class="sxs-lookup"><span data-stu-id="e75d7-116">**Importance**</span></span>  
 <span data-ttu-id="e75d7-117">ルールに割り当てられている重要度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-117">Displays the importance assigned to the rule.</span></span>  
  
 <span data-ttu-id="e75d7-118">**コメント**</span><span class="sxs-lookup"><span data-stu-id="e75d7-118">**Comments**</span></span>  
 <span data-ttu-id="e75d7-119">ユーザーは警告を消去する理由を説明するコメントを入力できます (省略可)。</span><span class="sxs-lookup"><span data-stu-id="e75d7-119">(Optional) Allows the user to type a comment that explains why you are dismissing the warning.</span></span>  
  
## <a name="dismissed-warnings-grid"></a><span data-ttu-id="e75d7-120">[消去された警告] グリッド</span><span class="sxs-lookup"><span data-stu-id="e75d7-120">Dismissed Warnings Grid</span></span>  
 <span data-ttu-id="e75d7-121">**[消去された警告]** グリッドには、発生した警告のうち、 **[エラー一覧]** から消去された特定の警告がすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-121">The **Dismissed Warnings** grid displays all specific warning occurrences that have been dismissed from the **Error List**.</span></span> <span data-ttu-id="e75d7-122">警告を再度有効にするには、グリッドで警告を選択し、 **[再有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e75d7-122">To re-enable a warning, select it in the grid, and then click **Re-enable**.</span></span>  
  
 <span data-ttu-id="e75d7-123">**[消去された警告]** グリッドには、次の列があります。</span><span class="sxs-lookup"><span data-stu-id="e75d7-123">The **Dismissed Warnings** grid has the following :</span></span>  
  
 <span data-ttu-id="e75d7-124">**Object**</span><span class="sxs-lookup"><span data-stu-id="e75d7-124">**Object**</span></span>  
 <span data-ttu-id="e75d7-125">オブジェクトの種類とオブジェクト名を表すアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-125">Displays an icon that represents the object type and the object name.</span></span>  
  
 <span data-ttu-id="e75d7-126">**Type**</span><span class="sxs-lookup"><span data-stu-id="e75d7-126">**Type**</span></span>  
 <span data-ttu-id="e75d7-127">オブジェクトの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-127">Displays the object type.</span></span>  
  
 <span data-ttu-id="e75d7-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="e75d7-128">**Description**</span></span>  
 <span data-ttu-id="e75d7-129">ルールの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-129">Displays the name of the rule.</span></span>  
  
 <span data-ttu-id="e75d7-130">**重要度**</span><span class="sxs-lookup"><span data-stu-id="e75d7-130">**Importance**</span></span>  
 <span data-ttu-id="e75d7-131">ルールに割り当てられている重要度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-131">Displays the importance assigned to the rule.</span></span>  
  
 <span data-ttu-id="e75d7-132">**コメント**</span><span class="sxs-lookup"><span data-stu-id="e75d7-132">**Comments**</span></span>  
 <span data-ttu-id="e75d7-133">警告が消去されるときに入力されたコメントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-133">Displays the comment that was entered when the warning was dismissed.</span></span> <span data-ttu-id="e75d7-134">ここでは、コメントを追加または変更できます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-134">You can add or modify a comment here.</span></span>  
  
 <span data-ttu-id="e75d7-135">**[再有効化]**</span><span class="sxs-lookup"><span data-stu-id="e75d7-135">**Re-enable**</span></span>  
 <span data-ttu-id="e75d7-136">選択した警告を再度有効にします。</span><span class="sxs-lookup"><span data-stu-id="e75d7-136">Re-enables the selected warnings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e75d7-137">オブジェクトに警告が含まれていても、オブジェクトが無効な状態であったり、プロジェクトから手動で削除されたりすると、一覧にある警告の横にエラー アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e75d7-137">If an object has a warning, but the object is in an invalid state or was manually removed from the project, an error icon appears next to the warning in the list.</span></span> <span data-ttu-id="e75d7-138">警告を消去するには、警告を選択し、 **[再有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e75d7-138">To dismiss the warning, select it and then click **Re-enable**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75d7-139">参照</span><span class="sxs-lookup"><span data-stu-id="e75d7-139">See Also</span></span>  
 <span data-ttu-id="e75d7-140">[[警告の消去] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e75d7-140">[Dismiss Warning Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e75d7-141">一般 &#40;データベースデザイナー&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="e75d7-141">General &#40;Database Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](general-database-designer-analysis-services-multidimensional-data.md)  
  
  
