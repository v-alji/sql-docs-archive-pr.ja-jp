---
title: 改ページの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3846cd48-2787-47e9-b13b-7fc45a205f68
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55d6be3ae47827c5a8ff4a5b36e3ff2ce80e1034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631553"
---
# <a name="add-a-page-break-report-builder-and-ssrs"></a><span data-ttu-id="eba67-102">改ページの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="eba67-102">Add a Page Break (Report Builder and SSRS)</span></span>
  <span data-ttu-id="eba67-103">四角形、データ領域、またはデータ領域内のグループに改ページを追加して、各ページの情報量を制御することができます。</span><span class="sxs-lookup"><span data-stu-id="eba67-103">You can add a page break to rectangles, data regions, or groups within data regions to control the amount of information on each page.</span></span> <span data-ttu-id="eba67-104">改ページを追加すると、レポートを表示する際に各ページのアイテムのみを処理すればよいので、パブリッシュされたレポートのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="eba67-104">Adding page breaks can improve the performance of published reports because only the items on each page have to be processed as you view the report.</span></span> <span data-ttu-id="eba67-105">レポート全体が 1 ページで構成されている場合は、レポートを表示する前にすべてのアイテムを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eba67-105">When the whole report is a single page, all items must be processed before you can view the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-break-to-a-data-region"></a><span data-ttu-id="eba67-106">データ領域に改ページを追加するには</span><span class="sxs-lookup"><span data-stu-id="eba67-106">To add a page break to a data region</span></span>  
  
1.  <span data-ttu-id="eba67-107">デザイン画面で、データ領域のコーナー ハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eba67-107">On the design surface, right-click the corner handle of the data region and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="eba67-108">**[全般]** タブの **[改ページのオプション]** で、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="eba67-108">On the **General** tab, under **Page break options**, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="eba67-109">**[前に改ページを追加する]** :</span><span class="sxs-lookup"><span data-stu-id="eba67-109">**Add a page break before**.</span></span> <span data-ttu-id="eba67-110">テーブルの前に改ページを追加する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eba67-110">Select this option when you want to add a page break before the table.</span></span>  
  
    -   <span data-ttu-id="eba67-111">**[後に改ページを追加する]** :</span><span class="sxs-lookup"><span data-stu-id="eba67-111">**Add a page break after**.</span></span> <span data-ttu-id="eba67-112">テーブルの後に改ページを追加する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eba67-112">Select this option when you want to add a page break after the table.</span></span>  
  
    -   <span data-ttu-id="eba67-113">**[可能な場合は、テーブルを 1 ページに収める]** :</span><span class="sxs-lookup"><span data-stu-id="eba67-113">**Fit table on one page if possible**.</span></span> <span data-ttu-id="eba67-114">データを 1 ページに収める場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eba67-114">Select this option when you want the data to stay on one page.</span></span>  
  
### <a name="to-add-a-page-break-to-a-rectangle"></a><span data-ttu-id="eba67-115">四角形に改ページを追加するには</span><span class="sxs-lookup"><span data-stu-id="eba67-115">To add a page break to a rectangle</span></span>  
  
1.  <span data-ttu-id="eba67-116">デザイン画面で、改ページを追加する四角形を右クリックし、 **[四角形のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eba67-116">On the design surface, right-click the rectangle where you want to add a page break, and then click **Rectangle Properties**.</span></span>  
  
2.  <span data-ttu-id="eba67-117">**[全般]** タブの **[改ページのオプション]** で、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="eba67-117">On the **General** tab, under **Page break options**, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="eba67-118">**[前に改ページを追加する]** :</span><span class="sxs-lookup"><span data-stu-id="eba67-118">**Add a page break before**.</span></span> <span data-ttu-id="eba67-119">四角形の前に改ページを追加する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eba67-119">Select this option when you want to add a page break before the rectangle.</span></span>  
  
    -   <span data-ttu-id="eba67-120">**[後に改ページを追加する]** :</span><span class="sxs-lookup"><span data-stu-id="eba67-120">**Add a page break after**.</span></span> <span data-ttu-id="eba67-121">四角形の後に改ページを追加する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eba67-121">Select this option when you want to add a page break after the rectangle.</span></span>  
  
    -   <span data-ttu-id="eba67-122">**[改ページの罫線を省略する]** :</span><span class="sxs-lookup"><span data-stu-id="eba67-122">**Omit border on page break**.</span></span> <span data-ttu-id="eba67-123">改ページの罫線が不要な場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eba67-123">Select this option when you do not want a border on the page break.</span></span>  
  
    -   <span data-ttu-id="eba67-124">**[可能な場合は、コンテンツを 1 ページに収める]** :</span><span class="sxs-lookup"><span data-stu-id="eba67-124">**Keep contents together on a single page, if possible**.</span></span> <span data-ttu-id="eba67-125">四角形内のコンテンツを 1 ページに収める場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eba67-125">Select this option when you want contents inside the rectangle to stay on one page.</span></span>  
  
### <a name="to-add-a-page-break-to-a-row-group-in-a-table-matrix-or-list"></a><span data-ttu-id="eba67-126">テーブル、マトリックス、または一覧の行グループに改ページを追加するには</span><span class="sxs-lookup"><span data-stu-id="eba67-126">To add a page break to a row group in a table, matrix, or list</span></span>  
  
1.  <span data-ttu-id="eba67-127">グループ化ペインで、行グループを右クリックし、 **[グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eba67-127">In the Grouping pane, right-click a row group, and then click **Group Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eba67-128">列グループでは改ページは無視されます。</span><span class="sxs-lookup"><span data-stu-id="eba67-128">Page breaks are ignored on column groups.</span></span>  
  
2.  <span data-ttu-id="eba67-129">**[改ページ]** タブの **[グループの各インスタンスの間]** を選択し、テーブル内のグループの各インスタンスの間に改ページを追加します。</span><span class="sxs-lookup"><span data-stu-id="eba67-129">On the **Page Breaks** tab, select **Between each instance of a group** to add a page break between each instance of a group in the table.</span></span>  
  
3.  <span data-ttu-id="eba67-130">必要に応じて、 **[グループの先頭でも改ページする]** チェック ボックスまたは **[グループの末尾でも改ページする]** チェック ボックスをオンにし、テーブル内のグループの開始時または終了時に改ページが追加されるよう指定します。</span><span class="sxs-lookup"><span data-stu-id="eba67-130">Optionally, select **Also at the start of a group** or **Also at the end of a group** to specify that a page break be added when a group starts or ends in the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba67-131">参照</span><span class="sxs-lookup"><span data-stu-id="eba67-131">See Also</span></span>  
 <span data-ttu-id="eba67-132">[Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eba67-132">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eba67-133">[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eba67-133">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="eba67-134">ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="eba67-134">Page Headers and Footers &#40;Report Builder and SSRS&#41;</span></span>](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
