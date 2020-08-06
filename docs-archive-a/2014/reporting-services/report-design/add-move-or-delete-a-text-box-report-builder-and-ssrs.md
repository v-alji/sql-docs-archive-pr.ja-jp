---
title: テキスト ボックスの追加、移動、または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f042cf81-d933-4ac7-9287-c074a46bde98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cd85415fd2f0bac2a37b3fbda06795e10f351b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739349"
---
# <a name="add-move-or-delete-a-text-box-report-builder-and-ssrs"></a><span data-ttu-id="8e599-102">テキスト ボックスの追加、移動、または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="8e599-102">Add, Move, or Delete a Text Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8e599-103">テキスト ボックスはレポート内で最も一般的に使用されるレポート アイテムです。</span><span class="sxs-lookup"><span data-stu-id="8e599-103">Text boxes are the most commonly used report item in reports.</span></span> <span data-ttu-id="8e599-104">テキスト ボックスをレポート本文に追加して、タイトル、パラメーターの選択肢、組み込みフィールド、日付などの情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="8e599-104">You can add a text box to the report body to display information such as titles, parameter choices, built-in fields, and dates.</span></span>  
  
 <span data-ttu-id="8e599-105">テーブルやマトリックスのすべてのセルは、実際にはテキスト ボックスです。</span><span class="sxs-lookup"><span data-stu-id="8e599-105">Every cell in a table or matrix is really a text box.</span></span> <span data-ttu-id="8e599-106">テーブルおよびマトリックスと共にレポートに表示されるほとんどのレポート データは、レポートの各テキスト ボックスの内容を評価するレポート プロセッサの結果です。</span><span class="sxs-lookup"><span data-stu-id="8e599-106">Almost all report data displayed in a report with tables and matrices is the result of the report processor evaluating the contents of each text box in the report.</span></span> <span data-ttu-id="8e599-107">したがってセルは、データ領域の外部にあるその他のテキスト ボックスと同じように書式設定できます。</span><span class="sxs-lookup"><span data-stu-id="8e599-107">As such, you can format cells in the same way you would format other text boxes outside the data region.</span></span>  
  
 <span data-ttu-id="8e599-108">テキスト ボックスを一覧データ領域に追加するには、テキスト ボックスを追加してから一覧にドラッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e599-108">To add a text box to a list data region, you must first add the text box and then drag it into the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e599-109">テキスト ボックスをクリックすると、すぐにテキスト ボックスのテキストを編集できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="8e599-109">When you click a text box, you're immediately editing the text in the text box.</span></span> <span data-ttu-id="8e599-110">テキストではなくテキスト ボックスそのものを選択するには、<localizedText>Esc</localizedText> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="8e599-110">To select the text box itself, not the text in it, press ESC.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-text-box"></a><span data-ttu-id="8e599-111">テキスト ボックスを追加するには</span><span class="sxs-lookup"><span data-stu-id="8e599-111">To add a text box</span></span>  
  
1.  <span data-ttu-id="8e599-112">[デザイン] ビューの **[挿入]** タブで、 **[テキスト ボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e599-112">On the **Insert** tab in Design view, click **Text Box**.</span></span>  
  
2.  <span data-ttu-id="8e599-113">デザイン画面で、ボックスをクリックし、テキスト ボックスの目的のサイズにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8e599-113">On the design surface, click and then drag a box to the desired size of the text box.</span></span> <span data-ttu-id="8e599-114">または、デザイン画面をクリックして、既定のサイズのテキスト ボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e599-114">Alternatively, click the design surface to create a text box of default size.</span></span>  
  
### <a name="to-add-a-text-box-in-a-list"></a><span data-ttu-id="8e599-115">一覧にテキスト ボックスを追加するには</span><span class="sxs-lookup"><span data-stu-id="8e599-115">To add a text box in a list</span></span>  
  
1.  <span data-ttu-id="8e599-116">レポート デザイン ビューの **[挿入]** タブで、 **[一覧]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e599-116">On the **Insert** tab in report design view, click **List**.</span></span>  
  
2.  <span data-ttu-id="8e599-117">デザイン画面で、ボックスをクリックし、一覧の目的のサイズにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8e599-117">On the design surface, click and then drag a box to the desired size of the list.</span></span> <span data-ttu-id="8e599-118">または、デザイン画面をクリックして、既定のサイズの一覧を作成します。</span><span class="sxs-lookup"><span data-stu-id="8e599-118">Alternatively, click the design surface to create a list of default size.</span></span>  
  
3.  <span data-ttu-id="8e599-119">**[挿入]** タブの **[テキスト ボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e599-119">On the **Insert** tab, click **Text Box**.</span></span>  
  
4.  <span data-ttu-id="8e599-120">デザイン画面の手順 1. で追加した一覧内で、ボックスをクリックし、テキスト ボックスの目的のサイズにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8e599-120">On the design surface, click and then drag a box to the desired size of the text box inside the list you added in step 1.</span></span> <span data-ttu-id="8e599-121">または、デザイン画面の一覧の内部をクリックして、既定のサイズのテキスト ボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e599-121">Alternatively, click the design surface inside the list to create a text box of default size.</span></span>  
  
5.  <span data-ttu-id="8e599-122">テキスト ボックスが一覧内で正しく入れ子になっていることを確認するには、テキスト ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="8e599-122">To confirm the text box is correctly nested inside the list, select the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e599-123">テキスト ボックスの中をクリックして編集モードになった場合は、&lt;localizedText&gt;Esc&lt;/localizedText&gt; キーを押すとテキスト ボックスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8e599-123">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
6.  <span data-ttu-id="8e599-124">プロパティ ペインで、 **Parent** プロパティが一覧データ領域に自動的に追加された四角形であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e599-124">In the Properties pane, verify that the **Parent** property is the rectangle that was automatically added to the list data region.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e599-125">プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="8e599-125">If the Properties pane is not visible, check **Properties** on the **View** tab.</span></span>  
  
### <a name="to-move-a-text-box"></a><span data-ttu-id="8e599-126">テキスト ボックスを移動するには</span><span class="sxs-lookup"><span data-stu-id="8e599-126">To move a text box</span></span>  
  
1.  <span data-ttu-id="8e599-127">レポート デザイン ビューで、テキスト ボックス内の空白部分をクリックして、テキスト ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="8e599-127">In report design view, click any empty space within the text box to select the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e599-128">テキスト ボックスの中をクリックして編集モードになった場合は、&lt;localizedText&gt;Esc&lt;/localizedText&gt; キーを押すとテキスト ボックスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8e599-128">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
2.  <span data-ttu-id="8e599-129">テキスト ボックスのハンドルをクリックし、テキスト ボックスを新しい場所にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8e599-129">Click the text box handle and drag the text box to the new location.</span></span> <span data-ttu-id="8e599-130">または、方向キーを使用して、選択したテキスト ボックスを横方向または縦方向に移動できます。</span><span class="sxs-lookup"><span data-stu-id="8e599-130">Alternatively, you can use the arrow keys to move a selected text box horizontally or vertically.</span></span> <span data-ttu-id="8e599-131">デザイン画面でテキスト ボックスを細かく移動するには、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながら方向キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="8e599-131">To move the text box in smaller increments on the design surface, hold down CTRL plus the arrow keys.</span></span>  
  
### <a name="to-delete-a-text-box"></a><span data-ttu-id="8e599-132">テキスト ボックスを削除するには</span><span class="sxs-lookup"><span data-stu-id="8e599-132">To delete a text box</span></span>  
  
1.  <span data-ttu-id="8e599-133">レポート デザイン ビューで、テキスト ボックス内の空白部分を右クリックして選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e599-133">In report design view, right-click any empty space within the text box to select it, and then click **Delete**.</span></span> <span data-ttu-id="8e599-134">または、テキスト ボックス内の空白部分をクリックして、<localizedText>Del</localizedText> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="8e599-134">Alternatively, click any empty space within the text box, and then press DELETE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e599-135">テキスト ボックスの中をクリックして編集モードになった場合は、&lt;localizedText&gt;Esc&lt;/localizedText&gt; キーを押すとテキスト ボックスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8e599-135">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e599-136">参照</span><span class="sxs-lookup"><span data-stu-id="8e599-136">See Also</span></span>  
 <span data-ttu-id="8e599-137">[テキストボックス &#40;レポートビルダーおよび SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8e599-137">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8e599-138">[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8e599-138">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8e599-139">キーボード ショートカット (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="8e599-139">Keyboard Shortcuts &#40;Report Builder&#41;</span></span>](../report-builder/keyboard-shortcuts-report-builder.md)  
  
  
