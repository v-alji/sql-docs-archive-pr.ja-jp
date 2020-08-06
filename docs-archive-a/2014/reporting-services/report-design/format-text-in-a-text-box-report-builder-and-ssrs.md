---
title: テキスト ボックス内のテキストの書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df0794b5-96b0-4034-bd17-1be7f31e29db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 522bc420f77b2e5e9d2163c28d3d688b7c47883c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634843"
---
# <a name="format-text-in-a-text-box-report-builder-and-ssrs"></a><span data-ttu-id="0ce42-102">テキスト ボックス内のテキストの書式設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="0ce42-102">Format Text in a Text Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0ce42-103">テキスト ボックス内のテキストは、どの部分も個別に書式設定できます。また、1 つのテキスト ボックスに、プレースホルダー テキストと静的テキストを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-103">You can format any part of the text within a text box independently, and mix placeholder text and static text in one text box.</span></span> <span data-ttu-id="0ce42-104">複数の書式を混在させ、プレースホルダー テキストを追加できるこの機能により、文書の差し込みを行ったり、レポート内のテキストに使用するテンプレートを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-104">This ability to mix formats and add placeholder text enables you to create mail merges or templates for text in your report.</span></span> <span data-ttu-id="0ce42-105">プレースホルダーを使用することによって、あらゆる式を定義できるほか、それぞれの式に対して、個別に書式を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-105">Any expression can be defined and formatted separately using a placeholder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-combine-multiple-formats-in-a-text-box"></a><span data-ttu-id="0ce42-106">テキスト ボックスで複数の書式を混在させるには</span><span class="sxs-lookup"><span data-stu-id="0ce42-106">To combine multiple formats in a text box</span></span>  
  
1.  <span data-ttu-id="0ce42-107">**[挿入]** タブの **[テキスト ボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-107">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="0ce42-108">デザイン画面をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-108">Click the design surface, and then drag to create a box that is the size you want.</span></span>  
  
2.  <span data-ttu-id="0ce42-109">テキスト ボックス内で、書式設定の対象となるテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-109">Inside the text box, select the text you want to format.</span></span>  
  
3.  <span data-ttu-id="0ce42-110">選択したテキストを右クリックして、 **[テキストのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-110">Right-click the selected text, and click **Text Properties**.</span></span>  
  
4.  <span data-ttu-id="0ce42-111">書式設定オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-111">Set formatting options.</span></span> <span data-ttu-id="0ce42-112">たとえば、 **[全般]** タブには次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="0ce42-112">For example, on the **General** tab:</span></span>  
  
    -   <span data-ttu-id="0ce42-113">**[ツールヒント]** : テキスト、または結果がツールヒントになる式を入力します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-113">**Tooltip** Type text or an expression that evaluates to a ToolTip.</span></span> <span data-ttu-id="0ce42-114">ツールヒントは、ユーザーがレポートのアイテムの上にポインターを置いたときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-114">The ToolTip appears when the user pauses the pointer over the item in a report</span></span>  
  
    -   <span data-ttu-id="0ce42-115">**[マークアップの種類]** : 選択したテキストの表示方法を指定するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-115">**Markup type** Select an option to indicate how the selected text will be rendered:</span></span>  
  
         <span data-ttu-id="0ce42-116">**[テキスト形式]** : 選択したテキストを単純なテキストとして表示します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-116">**Plain Text** Display the selected text as simple text.</span></span> <span data-ttu-id="0ce42-117">HTML はリテラル テキストとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-117">HTML will be treated as literal text.</span></span>  
  
         <span data-ttu-id="0ce42-118">**[HTML]**  : 選択したテキストを HTML として表示します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-118">**HTML**  Display the selected text as HTML.</span></span> <span data-ttu-id="0ce42-119">プレースホルダーの式の値が有効な HTML タグを含んでいる場合、これらのタグは HTML として表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-119">If the expression value of the placeholder contains valid HTML tags, these tags will be rendered as HTML.</span></span> <span data-ttu-id="0ce42-120">詳細については、[「レポートへの HTML のインポート &#40;レポート ビルダーおよび SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ce42-120">For more information, see [Importing HTML into a Report &#40;Report Builder and SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
5.  <span data-ttu-id="0ce42-121">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-121">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="0ce42-122">書式設定の対象となるその他のテキストについても、手順 2. ～ 5. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-122">Repeat steps 2 through 5 for the remaining text you want to format.</span></span>  
  
### <a name="to-format-text-and-placeholders-differently-in-the-same-text-box"></a><span data-ttu-id="0ce42-123">同じテキスト ボックス内のテキストとプレースホルダーの書式を個別に設定するには</span><span class="sxs-lookup"><span data-stu-id="0ce42-123">To format text and placeholders differently in the same text box</span></span>  
  
1.  <span data-ttu-id="0ce42-124">**[挿入]** タブの **[一覧]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-124">On the **Insert** tab, click **List**.</span></span> <span data-ttu-id="0ce42-125">デザイン画面をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-125">Click the design surface, and then drag to create a box that is the size you want.</span></span> <span data-ttu-id="0ce42-126">**[データセットのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-126">The **Dataset Properties** dialog box opens.</span></span> <span data-ttu-id="0ce42-127">共有データセットまたはレポートに埋め込まれたデータセットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-127">You can use a shared dataset or a dataset embedded in your report.</span></span> <span data-ttu-id="0ce42-128">詳細については、「[[クエリ] ([データセットのプロパティ] ダイアログ ボックス) &#40;レポート ビルダー&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md)」または「[[クエリ] ([データセットのプロパティ] ダイアログ ボックス)](../dataset-properties-dialog-box-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ce42-128">For more information, click [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) or [Dataset Properties Dialog Box, Query](../dataset-properties-dialog-box-query.md).</span></span>  
  
2.  <span data-ttu-id="0ce42-129">**[挿入]** タブの **[テキスト ボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-129">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="0ce42-130">一覧内をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-130">Click in the list, and then drag to create a box that is the size you want.</span></span>  
  
3.  <span data-ttu-id="0ce42-131">テキスト ボックスのラベルを入力します。たとえば、「**My Field**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0ce42-131">Type a label in the text box - for example, **My Field**:.</span></span>  
  
4.  <span data-ttu-id="0ce42-132">データセットからテキスト ボックスにフィールドをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-132">Drag a field from your dataset into the text box.</span></span> <span data-ttu-id="0ce42-133">フィールドに対してプレースホルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0ce42-133">A placeholder is created for your field.</span></span>  
  
5.  <span data-ttu-id="0ce42-134">基本的な書式設定の場合は、プレースホルダー テキストを選択し、 **[ホーム]** タブの **[フォント]** グループにある書式設定オプションのいずれかをクリックします。たとえば、 **[太字]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-134">For basic formatting, select the placeholder text and then click one of the formatting options in the **Font** group on the **Home** tab. For example, click the **Bold** button.</span></span>  
  
     <span data-ttu-id="0ce42-135">詳細な書式設定オプションの場合は、プレースホルダー テキストを右クリックし、 **[プレースホルダー プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-135">For more formatting options, right-click the placeholder text, and then click **Placeholder Properties**.</span></span>  
  
6.  <span data-ttu-id="0ce42-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-136">Click **OK**.</span></span> <span data-ttu-id="0ce42-137">レポート デザイン ビューで、テキスト ボックスに "**My Field**: [*FieldName*]" と表示されます ( *FieldName* はフィールド名)。</span><span class="sxs-lookup"><span data-stu-id="0ce42-137">In report design view, the text box should contain "**My Field**: [*FieldName*]", where *FieldName* is the name of your field.</span></span>  
  
7.  <span data-ttu-id="0ce42-138">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ce42-138">Click **Run**.</span></span>  
  
 <span data-ttu-id="0ce42-139">一覧はフィールド内の値ごとに 1 回繰り返され、プレースホルダー *FieldName* がデータセット内のそのフィールドの値に置き換わります。</span><span class="sxs-lookup"><span data-stu-id="0ce42-139">The list repeats one time for every value in the field, and the *FieldName* placeholder is replaced each time by the value of that field in the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce42-140">参照</span><span class="sxs-lookup"><span data-stu-id="0ce42-140">See Also</span></span>  
 <span data-ttu-id="0ce42-141">[テキスト ボックス &#40;レポート ビルダーおよび SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ce42-141">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ce42-142">[テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ce42-142">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ce42-143">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ce42-143">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ce42-144">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ce42-144">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ce42-145">[レポートへの HTML の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ce42-145">[Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ce42-146">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ce42-146">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ce42-147">[数値と日付の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ce42-147">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ce42-148">[[全般] ([プレースホルダーのプロパティ] ダイアログ ボックス) &#40;レポート ビルダーおよび SSRS&#41;](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="0ce42-148">[Placeholder Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)</span></span>  
  
  
