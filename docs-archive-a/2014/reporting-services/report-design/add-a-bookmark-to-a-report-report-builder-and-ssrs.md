---
title: レポートへのブックマークの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f130562e-5673-40e3-8e01-de7227a21d41
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fae543dd1b071ff38853637a3da57ffd2410c3a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739378"
---
# <a name="add-a-bookmark-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="c5d49-102">レポートへのブックマークの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c5d49-102">Add a Bookmark to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c5d49-103">カスタマイズされた目次を指定したり、レポートにカスタマイズされた内部ナビゲーション リンクを指定したりする場合は、レポートにブックマークおよびブックマーク リンクを追加します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-103">Add bookmarks and bookmark links to a report when you want to provide a customized table of contents or to provide customized internal navigation links in the report.</span></span> <span data-ttu-id="c5d49-104">通常、各テーブルやグラフ、テーブルやマトリックスに表示される固有のグループ値など、ユーザーが直接アクセスするレポート内の場所にブックマークを追加します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-104">Typically, you add bookmarks to locations in the report to which you want to direct users, such as to each table or chart or to the unique group values displayed in a table or matrix.</span></span> <span data-ttu-id="c5d49-105">ブックマークとして使用する独自の文字列を作成できます。また、グループの場合はブックマークをグループ式に設定できます。</span><span class="sxs-lookup"><span data-stu-id="c5d49-105">You can create your own strings to use as bookmarks, or, for groups, you can set the bookmark to the group expression.</span></span>  
  
 <span data-ttu-id="c5d49-106">ブックマークを作成すると、ユーザーがクリックして各ブックマークに移動できるレポート アイテムを追加できます。</span><span class="sxs-lookup"><span data-stu-id="c5d49-106">After you create bookmarks, you can add report items that the user can click to go to each bookmark.</span></span> <span data-ttu-id="c5d49-107">これらの項目は通常、テキスト ボックスまたはイメージです。</span><span class="sxs-lookup"><span data-stu-id="c5d49-107">These items are typically text boxes or images.</span></span>  
  
 <span data-ttu-id="c5d49-108">たとえば、レポートに色別にグループ化されたテーブルが表示される場合、グループ ヘッダーにグループ式に基づくブックマークを追加します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-108">For example, if your report displays a table grouped by color, you would add a bookmark based on the group expression to the group header.</span></span> <span data-ttu-id="c5d49-109">次に、色の値が表示されたレポートの先頭に単一のテキスト ボックスのあるテーブルを追加し、そのテキスト ボックスにブックマーク リンクを設定します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-109">Then you would add a table with a single text box at the beginning of the report that displayed the color values, and set the bookmark link on that text box.</span></span> <span data-ttu-id="c5d49-110">色をクリックすると、レポートはその色のグループ ヘッダー行が表示されるページにジャンプします。</span><span class="sxs-lookup"><span data-stu-id="c5d49-110">When you click the color, the report jumps to the page that displays the group header row for that color.</span></span>  
  
 <span data-ttu-id="c5d49-111">任意のレポート アイテムにブックマークを追加したり、グラフのテキスト ボックス、画像、計算系列など、 **Action** プロパティのある任意のアイテムへのブックマーク リンクを追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="c5d49-111">You can add a bookmark to any report item and add a bookmark link to any item that has an **Action** property, for example, a text box, an image, or a calculated series in a chart.</span></span> <span data-ttu-id="c5d49-112">詳細については、「[[アクション プロパティ] ダイアログ ボックス (レポート ビルダーおよび SSRS)](../action-properties-dialog-box-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5d49-112">For more information, see the [Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-bookmark"></a><span data-ttu-id="c5d49-113">ブックマークを追加するには</span><span class="sxs-lookup"><span data-stu-id="c5d49-113">To add a bookmark</span></span>  
  
1.  <span data-ttu-id="c5d49-114">レポート デザイン ビューで、ブックマークを追加するテキスト ボックス、画像、グラフ、または他のレポート アイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-114">In report design view, select the text box, image, chart, or other report item to which you want to add a bookmark.</span></span> <span data-ttu-id="c5d49-115">選択したアイテムのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5d49-115">The properties for the selected item appear in the Properties pane.</span></span>  
  
2.  <span data-ttu-id="c5d49-116">**[ブックマーク]** の隣のテキスト ボックスに、このブックマークのラベルとなる文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-116">In the text box next to **Bookmark**, type a string that is the label for this bookmark.</span></span> <span data-ttu-id="c5d49-117">たとえば、レポート内の画像のブックマークとして、「 **BikePhoto** 」と入力できます。</span><span class="sxs-lookup"><span data-stu-id="c5d49-117">For example, you could type **BikePhoto** as the bookmark for an image in your report.</span></span> <span data-ttu-id="c5d49-118">または、式 ( **[fx]** ) ボタンをクリックして **[式]** ダイアログ ボックスを開き、結果がラベルになる式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-118">Alternatively, click the Expression (**fx**) button to open the **Expression** dialog box to specify an expression that evaluates to a label.</span></span> <span data-ttu-id="c5d49-119">グループの場合、入力する式はグループ式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5d49-119">For a group, the expression you type should be the group expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c5d49-120">ブックマークには任意の文字列を使用できますが、レポート内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5d49-120">The bookmark can be any string, but it must be unique in the report.</span></span> <span data-ttu-id="c5d49-121">ブックマークが一意でない場合、そのブックマークへのリンクは、最初に一致したブックマークを参照します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-121">If the bookmark is not unique, a link to the bookmark finds the first matching bookmark.</span></span>  
  
### <a name="to-add-a-bookmark-link"></a><span data-ttu-id="c5d49-122">ブックマーク リンクを追加するには</span><span class="sxs-lookup"><span data-stu-id="c5d49-122">To add a bookmark link</span></span>  
  
1.  <span data-ttu-id="c5d49-123">[デザイン] ビューで、リンクを追加するテキスト ボックス、画像、またはグラフを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5d49-123">In Design view, right-click the text box, image, chart, to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c5d49-124">そのレポート アイテムの **[プロパティ]** ダイアログ ボックスで、 **[アクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5d49-124">In The **Properties** dialog box for that report item, click **Action**.</span></span>  
  
3.  <span data-ttu-id="c5d49-125">**[ブックマークに移動する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-125">Select **Go to bookmark**.</span></span> <span data-ttu-id="c5d49-126">このオプションのダイアログ ボックスに追加のセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5d49-126">An additional section appears in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="c5d49-127">**[ブックマークの選択]** ボックスで、ブックマークまたは結果がブックマークになる式を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-127">In the **Select bookmark** box, type or select a bookmark or an expression that evaluates to a bookmark.</span></span> <span data-ttu-id="c5d49-128">上記の例を使用してレポート内の画像へのリンクを作成するには、「 **BikePhoto** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-128">Using the previous example, type **BikePhoto** to create a link to the image in your report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="c5d49-129">(省略可) テキストがリンクのように自動的に書式設定されることはありません。</span><span class="sxs-lookup"><span data-stu-id="c5d49-129">(Optional) The text is not automatically formatted like a link.</span></span> <span data-ttu-id="c5d49-130">テキストでは、テキストの色と効果を変更してそのテキストがリンクであることを示すと便利です。</span><span class="sxs-lookup"><span data-stu-id="c5d49-130">For text, it is helpful to change the color and effect of the text to indicate that the text is a link.</span></span> <span data-ttu-id="c5d49-131">たとえば、リボンの [ホーム] タブの **[フォント]** セクションで、色を青に変更し、効果を下線に変更します。</span><span class="sxs-lookup"><span data-stu-id="c5d49-131">For example, change the color to blue and the effect to underline in the **Font** section in the Home tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="c5d49-132">リンクをテストするには、 **[実行]** をクリックしてレポートをプレビューし、リンクを設定したレポート アイテムをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5d49-132">To test the link, click **Run** to preview the report, and then click the report item that you set this link on..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d49-133">参照</span><span class="sxs-lookup"><span data-stu-id="c5d49-133">See Also</span></span>  
 <span data-ttu-id="c5d49-134">[対話的な並べ替え、ドキュメント マップ、およびリンク &#40;レポート ビルダーおよび SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5d49-134">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5d49-135">[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5d49-135">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c5d49-136">データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c5d49-136">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
