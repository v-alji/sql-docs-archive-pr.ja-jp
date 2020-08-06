---
title: 階層の作成と管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8dd30cd0-a831-4d25-b577-648d7f3c7fa6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bab3e09aadb4e0c857b9c1da3111e03e90f777e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634670"
---
# <a name="create-and-manage-hierarchies-ssas-tabular"></a><span data-ttu-id="5ddc0-102">階層の作成および管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="5ddc0-102">Create and Manage Hierarchies (SSAS Tabular)</span></span>
  <span data-ttu-id="5ddc0-103">階層の作成と管理はダイアグラム ビューのモデル デザイナーで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-103">Hierarchies can be created and managed in the model designer, in Diagram View.</span></span> <span data-ttu-id="5ddc0-104">モデル デザイナーをダイアグラム ビューに表示するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントして、 **[ダイアグラム ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-104">To view the model designer in Diagram View, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
 <span data-ttu-id="5ddc0-105">このトピックでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-105">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="5ddc0-106">階層を作成する</span><span class="sxs-lookup"><span data-stu-id="5ddc0-106">Create a Hierarchy</span></span>](#bkmk_create)  
  
-   [<span data-ttu-id="5ddc0-107">階層の編集</span><span class="sxs-lookup"><span data-stu-id="5ddc0-107">Edit a Hierarchy</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="5ddc0-108">階層の削除</span><span class="sxs-lookup"><span data-stu-id="5ddc0-108">Delete a Hierarchy</span></span>](#bkmk_delete)  
  
##  <a name="create-a-hierarchy"></a><a name="bkmk_create"></a> <span data-ttu-id="5ddc0-109">階層の作成</span><span class="sxs-lookup"><span data-stu-id="5ddc0-109">Create a Hierarchy</span></span>  
 <span data-ttu-id="5ddc0-110">列とテーブルのショートカット メニューを使用すると階層を作成できます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-110">You can create a hierarchy by using the columns and table context menu.</span></span> <span data-ttu-id="5ddc0-111">階層を作成すると、選択した列を子レベルに持つ新しい親レベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-111">When you create a hierarchy, a new parent level displays with selected columns as child levels.</span></span>  
  
#### <a name="to-create-a-hierarchy-from-the-context-menu"></a><span data-ttu-id="5ddc0-112">ショートカット メニューから階層を作成するには</span><span class="sxs-lookup"><span data-stu-id="5ddc0-112">To create a hierarchy from the context menu</span></span>  
  
1.  <span data-ttu-id="5ddc0-113">テーブル ウィンドウのモデル デザイナー (ダイアグラム ビュー) で、列を右クリックして **[階層の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-113">In the model designer (Diagram View), in a table window, right-click on a column, and then click **Create Hierarchy**.</span></span>  
  
     <span data-ttu-id="5ddc0-114">複数の列を選択するには、列を 1 つずつクリックし、右クリックしてショートカット メニューを開き、 **[階層の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-114">To select multiple columns, click each column, then right-click to open the context menu, and then click **Create Hierarchy**.</span></span>  
  
     <span data-ttu-id="5ddc0-115">テーブル ウィンドウの下部に親階層レベルが作成され、選択した列が階層の下に子レベルとしてコピーされます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-115">A parent hierarchy level is created at the bottom of the table window and the selected columns are copied under the hierarchy as child levels.</span></span>  
  
2.  <span data-ttu-id="5ddc0-116">階層の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-116">Type a name for the hierarchy.</span></span>  
  
 <span data-ttu-id="5ddc0-117">追加の列を階層の親レベルにドラッグすると、列がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-117">You can drag additional columns into your hierarchy's parent level, which copies the columns.</span></span> <span data-ttu-id="5ddc0-118">子レベルを階層内の目的の場所にドロップします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-118">Drop the child level to place it where you want it to appear in the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ddc0-119">1 つ以上の列と共に 1 つのメジャーを複数選択するか、または複数のテーブルから複数の列を選択した場合、ショートカット メニューの [階層の作成] コマンドは無効になります。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-119">The Create Hierarchy command is disabled in the context menu if you multi-select a measure along with one or more columns or you select columns from multiple tables.</span></span>  
  
##  <a name="edit-a-hierarchy"></a><a name="bkmk_edit"></a><span data-ttu-id="5ddc0-120">階層の編集</span><span class="sxs-lookup"><span data-stu-id="5ddc0-120">Edit a Hierarchy</span></span>  
 <span data-ttu-id="5ddc0-121">階層名の変更、子レベルの名前の変更、子レベルの順序の変更、子レベルとしての列の追加、階層内の子レベルの削除、子レベルの基になる名前 (列名) の表示、階層の親レベルと同名の子レベルの非表示を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-121">You can rename a hierarchy, rename a child level, change the order of the child levels, add additional columns as child levels, remove a child level from a hierarchy, show the source name of a child level (the column name), and hide a child level if it has the same name as the hierarchy parent level.</span></span>  
  
#### <a name="to-change-the-name-of-a-hierarchy-or-child-level"></a><span data-ttu-id="5ddc0-122">階層または子レベルの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="5ddc0-122">To change the name of a hierarchy or child level</span></span>  
  
1.  <span data-ttu-id="5ddc0-123">階層の親レベルまたは子レベルを右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-123">Right-click the hierarchy parent level or a child level, and the click **Rename**.</span></span>  
  
2.  <span data-ttu-id="5ddc0-124">新しい名前を入力するか、既存の名前を編集します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-124">Type a new name or edit the existing name.</span></span>  
  
#### <a name="to-change-the-order-of-a-child-level-in-a-hierarchy"></a><span data-ttu-id="5ddc0-125">階層内の子レベルの順序を変更するには</span><span class="sxs-lookup"><span data-stu-id="5ddc0-125">To change the order of a child level in a hierarchy</span></span>  
  
-   <span data-ttu-id="5ddc0-126">子レベルをクリックして、階層内の新しい場所にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-126">Click and drag a child level into a new position in the hierarchy.</span></span>  
  
-   <span data-ttu-id="5ddc0-127">または、階層内の子レベルを右クリックし、[上へ移動] をクリックして一覧内を上へ移動するか、[下へ移動] をクリックして下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-127">Or, right-click a child level of the hierarchy, and then click Move Up to move the level up in the list, or click Move Down to move the level down in the list.</span></span>  
  
-   <span data-ttu-id="5ddc0-128">または、子レベルをクリックして選択し、Alt キーを押しながら上方向キーを押して一覧内を上へ移動するか、Alt キーを押しながら下方向キーを押して下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-128">Or, click a child level to select it, and then press Alt + Up Arrow to move the level up, or press Alt+Down Arrow to move the level down in the list.</span></span>  
  
#### <a name="to-add-another-child-level-to-a-hierarchy"></a><span data-ttu-id="5ddc0-129">階層に他の子レベルを追加するには</span><span class="sxs-lookup"><span data-stu-id="5ddc0-129">To add another child level to a hierarchy</span></span>  
  
-   <span data-ttu-id="5ddc0-130">列をクリックして、親レベルまたは階層内の特定の場所にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-130">Click and drag a column onto the parent level or into a specific location of the hierarchy.</span></span> <span data-ttu-id="5ddc0-131">階層の子レベルとして列がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-131">The column is copied as a child level of the hierarchy.</span></span>  
  
-   <span data-ttu-id="5ddc0-132">または、列を右クリックして **[階層に追加]** をポイントし、階層をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-132">Or, right-click a column, point to **Add to Hierarchy**, and then click the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ddc0-133">非表示の列 (レポートで非表示の列) を子レベルとして階層に追加できます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-133">You can add a hidden column (a column that is hidden from reports) as a child level to the hierarchy.</span></span> <span data-ttu-id="5ddc0-134">子レベルは非表示になりません。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-134">The child level is not hidden.</span></span>  
  
#### <a name="to-remove-a-child-level-from-a-hierarchy"></a><span data-ttu-id="5ddc0-135">階層から子レベルを削除するには</span><span class="sxs-lookup"><span data-stu-id="5ddc0-135">To remove a child level from a hierarchy</span></span>  
  
-   <span data-ttu-id="5ddc0-136">子レベルを右クリックし、 **[階層から削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-136">Right-click a child level, and then click **Remove from Hierarchy**.</span></span>  
  
-   <span data-ttu-id="5ddc0-137">または、子レベルをクリックして **Del**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-137">Or, click a child level, and then press **Delete**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ddc0-138">階層の子レベルの名前を変更すると、コピー元の列とは同じ名前を共有しなくなります。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-138">If you rename a hierarchy child level, it no longer shares the same name as the column that it is copied from.</span></span> <span data-ttu-id="5ddc0-139">コピー元の列を表示するには、 **[基になる列の名前の表示]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-139">Use the **Show Source Name** command to see which column it was copied from.</span></span>  
  
#### <a name="to-show-a-source-name"></a><span data-ttu-id="5ddc0-140">基になる列の名前を表示するには</span><span class="sxs-lookup"><span data-stu-id="5ddc0-140">To show a source name</span></span>  
  
-   <span data-ttu-id="5ddc0-141">階層の子レベルを右クリックして、 **[基になる列の名前の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-141">Right-click a hierarchy child level, and then click **Show Source Name**.</span></span> <span data-ttu-id="5ddc0-142">コピー元の列の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-142">The name of the column that it was copied from appears.</span></span>  
  
##  <a name="delete-a-hierarchy"></a><a name="bkmk_delete"></a><span data-ttu-id="5ddc0-143">階層の削除</span><span class="sxs-lookup"><span data-stu-id="5ddc0-143">Delete a Hierarchy</span></span>  
  
#### <a name="to-delete-a-hierarchy-and-remove-its-child-levels"></a><span data-ttu-id="5ddc0-144">階層と子レベルを削除するには</span><span class="sxs-lookup"><span data-stu-id="5ddc0-144">To delete a hierarchy and remove its child levels</span></span>  
  
-   <span data-ttu-id="5ddc0-145">親階層レベルを右クリックして、[階層の削除] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-145">Right-click the parent hierarchy level, and then click Delete Hierarchy.</span></span>  
  
-   <span data-ttu-id="5ddc0-146">または、親階層レベルをクリックし、Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-146">Or, click the parent hierarchy level, and then press Delete.</span></span> <span data-ttu-id="5ddc0-147">これにより、すべての子レベルも削除されます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-147">This also removes all the child levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ddc0-148">参照</span><span class="sxs-lookup"><span data-stu-id="5ddc0-148">See Also</span></span>  
 <span data-ttu-id="5ddc0-149">[SSAS 表形式&#41;&#40;テーブルモデルデザイナー](../tabular-model-designer-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="5ddc0-149">[Tabular Model Designer &#40;SSAS Tabular&#41;](../tabular-model-designer-ssas-tabular.md) </span></span>  
 <span data-ttu-id="5ddc0-150">[SSAS テーブル&#41;&#40;階層](hierarchies-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="5ddc0-150">[Hierarchies &#40;SSAS Tabular&#41;](hierarchies-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="5ddc0-151">メジャー &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="5ddc0-151">Measures &#40;SSAS Tabular&#41;</span></span>](measures-ssas-tabular.md)  
  
  
