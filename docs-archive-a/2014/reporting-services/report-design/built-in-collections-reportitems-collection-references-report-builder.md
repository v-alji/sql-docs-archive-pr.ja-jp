---
title: ReportItems コレクションの参照 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: edc0c75f-0530-4e6d-85aa-3385301bfd00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61c89002adafb030288535debfe72de061945640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711729"
---
# <a name="reportitems-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="e16b0-102">ReportItems コレクションの参照 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e16b0-102">ReportItems Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e16b0-103">組み込みコレクション `ReportItems` は、データ領域の行などのレポート アイテムのテキスト ボックスや、レポート デザイン画面上のテキスト ボックスのセットです。</span><span class="sxs-lookup"><span data-stu-id="e16b0-103">The `ReportItems` built-in collection is the set of text boxes from report items such as rows of a data region or text boxes on the report design surface.</span></span> <span data-ttu-id="e16b0-104">`ReportItems` コレクションには、ページ ヘッダー、ページ フッター、またはレポート本文の現在のスコープにあるテキスト ボックスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e16b0-104">The `ReportItems` collection includes text boxes that are in the current scope of a page header, page footer, or report body.</span></span> <span data-ttu-id="e16b0-105">このコレクションは、レポート プロセッサおよびレポート レンダラーによって実行時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="e16b0-105">This collection is determined at run time by the report processor and the report renderer.</span></span> <span data-ttu-id="e16b0-106">ユーザーがレポートのページを表示する際には、レポート プロセッサによってレポート データとレポート アイテムのレイアウト要素が連続的に結合されますが、これに伴って現在のスコープが変化します。</span><span class="sxs-lookup"><span data-stu-id="e16b0-106">The current scope changes as the report processor successively combines report data and the report item layout elements as the user views pages of a report.</span></span> <span data-ttu-id="e16b0-107">組み込みコレクション `ReportItems` を使用すると、各ページの最初のアイテムと最後のアイテムを表示する辞書形式のページ ヘッダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e16b0-107">You can use the `ReportItems` built-in collection to produce dictionary-style page headers that show the first and last items on each page.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-reportitems-value-property"></a><span data-ttu-id="e16b0-108">ReportItems の Value プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="e16b0-108">Using the ReportItems Value Property</span></span>  
 <span data-ttu-id="e16b0-109">`ReportItems` コレクション内のアイテムに設定されるプロパティは、Value だけです。</span><span class="sxs-lookup"><span data-stu-id="e16b0-109">Items within the `ReportItems` collection have only one property: Value.</span></span> <span data-ttu-id="e16b0-110">`ReportItems` アイテムの値を使用すると、レポート内の別のフィールドのデータを表示または計算できます。</span><span class="sxs-lookup"><span data-stu-id="e16b0-110">The value for a `ReportItems` item can be used to display or calculate data from another field in the report.</span></span> <span data-ttu-id="e16b0-111">現在のテキスト ボックスの値にアクセスするには、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] に組み込まれたグローバルの Me.Value を使用するか、単なる Value を使用します。</span><span class="sxs-lookup"><span data-stu-id="e16b0-111">To access the value of the current text box, you can use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] built-in global Me.Value or simply Value.</span></span> <span data-ttu-id="e16b0-112">First 関数や集計関数などのレポート関数では、完全修飾された構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="e16b0-112">In report functions such as First and aggregate functions, use the fully qualified syntax.</span></span>  
  
 <span data-ttu-id="e16b0-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e16b0-113">For example:</span></span>  
  
-   <span data-ttu-id="e16b0-114">テキスト ボックスで次の式を使用すると、`Textbox1` という名前の `ReportItem` テキスト ボックスの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e16b0-114">This expression, placed in a text box, displays the value of a `ReportItem` text box named `Textbox1`:</span></span>  
  
     `=ReportItems!Textbox1.Value`  
  
-   <span data-ttu-id="e16b0-115">この式を `ReportItem` テキストボックスの Color プロパティに配置すると、値が 0 > の場合、テキストが黒で表示されます。それ以外の場合は、値が赤で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e16b0-115">This expression, placed in a `ReportItem` text box Color property, displays the text in black when the value is > 0; otherwise, the value is displayed in red:</span></span>  
  
     `=IIF(Me.Value > 0,"Black","Red")`  
  
-   <span data-ttu-id="e16b0-116">ページ ヘッダーまたはページ フッターのテキスト ボックスで次の式を使用すると、表示レポートのページごとに、 `LastName`という名前のテキスト ボックスの最初の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e16b0-116">This expression, placed in a text box in the page header or page footer, displays the first value per page of the rendered report, for a text box named `LastName`:</span></span>  
  
     `=First(ReportItems("LastName").Value)`  
  
## <a name="dictionary-style-page-header-expressions"></a><span data-ttu-id="e16b0-117">辞書形式のページ ヘッダー式</span><span class="sxs-lookup"><span data-stu-id="e16b0-117">Dictionary-Style Page Header Expressions</span></span>  
 <span data-ttu-id="e16b0-118">そのページ上の最初の顧客と最後の顧客を表示するページ ヘッダーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e16b0-118">You can create a page header to display the first customer on the page and the last customer on the page.</span></span> <span data-ttu-id="e16b0-119">ページ ヘッダーのテキスト ボックスでは、式の中で組み込みコレクション `ReportItems` を 1 回しか参照できないため、最初の顧客名用 (`=First(ReportItems!textboxLastName.Value`) と最後の顧客名用 (`=Last(ReportItems!textboxLastName.Value`) に 2 つのテキスト ボックスをページ ヘッダーに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e16b0-119">Because a text box in the page header can only refer to the `ReportItems` built-in collection once in an expression, you need to add two text boxes to the page header: one for the first customer name (`=First(ReportItems!textboxLastName.Value`) and one for the last customer name (`=Last(ReportItems!textboxLastName.Value`).</span></span>  
  
 <span data-ttu-id="e16b0-120">ページ ヘッダー セクションやページ フッター セクションでは、`ReportItems` コレクションのメンバーとして使用できるのは、現在のページのテキスト ボックスのみです。</span><span class="sxs-lookup"><span data-stu-id="e16b0-120">In a page header or page footer section, only text boxes on the current page are available as a member of the `ReportItems` collection.</span></span> <span data-ttu-id="e16b0-121">たとえば、 `ReportItems!textboxLastName.Value` が、複数ページにわたるデータ領域の最初のページにしか表示されないテキスト ボックスを参照している場合、最初のページでは値が表示されますが、その他すべてのページでは **#Error** と表示され、式が記述したとおりに評価できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="e16b0-121">For example, if `ReportItems!textboxLastName.Value` refers to a text box that only appears on the first page for a multipage data region, you see a value for the first page, but all other pages display **#Error** to show the expression could not be evaluated as written.</span></span>  
  
## <a name="scope-for-the-reportitems-collection"></a><span data-ttu-id="e16b0-122">ReportItems コレクションのスコープ</span><span class="sxs-lookup"><span data-stu-id="e16b0-122">Scope for the ReportItems Collection</span></span>  
 <span data-ttu-id="e16b0-123">レポートが処理されると、レポート本文内またはデータ領域内の各テキスト ボックスは、そのデータセット、データ領域、およびグループの関連付けのコンテキストで評価されます。</span><span class="sxs-lookup"><span data-stu-id="e16b0-123">As the report is processed, each text box in the report body or in a data region is evaluated in the context of its dataset, data region, and group associations.</span></span> <span data-ttu-id="e16b0-124">`ReportItems` コレクションへの参照のスコープは、現在のスコープまたは現在のスコープより上位の場所です。</span><span class="sxs-lookup"><span data-stu-id="e16b0-124">The scope for a reference to the `ReportItems` collection is the current scope or any point higher than the current scope.</span></span>  
  
 <span data-ttu-id="e16b0-125">たとえば、親グループの行の中にあるテキスト ボックスには、子グループの行の中にあるテキスト ボックスの名前を参照する式を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="e16b0-125">For example, a text box in a row that is in a parent group must not contain an expression that refers to the name of a text box in a child group row.</span></span> <span data-ttu-id="e16b0-126">このような式は、子行のテキスト ボックスがスコープ外にあるため、レポート内の値に解決されません。</span><span class="sxs-lookup"><span data-stu-id="e16b0-126">Such an expression does not resolve to a value in the report because the child row text box is out of scope.</span></span> <span data-ttu-id="e16b0-127">詳細については、「 [集計関数リファレンス (レポート ビルダーおよび SSRS)](report-builder-functions-aggregate-functions-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e16b0-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16b0-128">参照</span><span class="sxs-lookup"><span data-stu-id="e16b0-128">See Also</span></span>  
 <span data-ttu-id="e16b0-129">[式で使用される組み込みコレクション (レポート ビルダーおよび SSRS)](built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e16b0-129">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span></span>  
 <span data-ttu-id="e16b0-130">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e16b0-130">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e16b0-131">[Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e16b0-131">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e16b0-132">データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e16b0-132">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
