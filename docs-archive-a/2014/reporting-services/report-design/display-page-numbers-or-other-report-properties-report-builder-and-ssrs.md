---
title: ページ番号またはその他のレポート プロパティの表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efc3d5d5de11af1fcdfefc52ed12d5057ee12668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640699"
---
# <a name="display-page-numbers-or-other-report-properties-report-builder-and-ssrs"></a><span data-ttu-id="a877e-102">ページ番号またはその他のレポート プロパティの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a877e-102">Display Page Numbers or Other Report Properties (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a877e-103">レポートのページ ヘッダーまたはページ フッターにページ番号、レポート タイトル、ファイル名、およびその他のレポート プロパティを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="a877e-103">It's easy to add page numbers, a report title, file name, and other report properties to the page headers or footers of your report.</span></span> <span data-ttu-id="a877e-104">これらのプロパティは、レポート データ ペインの [組み込みフィールド] フォルダーのフィールドとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="a877e-104">These properties are stored as fields in the Built-in Fields folder in the Report Data pane:</span></span>  
  
-   <span data-ttu-id="a877e-105">[実行時間]</span><span class="sxs-lookup"><span data-stu-id="a877e-105">Execution time</span></span>  
  
-   <span data-ttu-id="a877e-106">ページ番号</span><span class="sxs-lookup"><span data-stu-id="a877e-106">Page number</span></span>  
  
-   <span data-ttu-id="a877e-107">[レポート フォルダー]</span><span class="sxs-lookup"><span data-stu-id="a877e-107">Report folder</span></span>  
  
-   <span data-ttu-id="a877e-108">レポート名</span><span class="sxs-lookup"><span data-stu-id="a877e-108">Report name</span></span>  
  
-   <span data-ttu-id="a877e-109">[レポート サーバー URL]</span><span class="sxs-lookup"><span data-stu-id="a877e-109">Report server URL</span></span>  
  
-   <span data-ttu-id="a877e-110">[総ページ数]</span><span class="sxs-lookup"><span data-stu-id="a877e-110">Total pages</span></span>  
  
-   <span data-ttu-id="a877e-111">User ID</span><span class="sxs-lookup"><span data-stu-id="a877e-111">User ID</span></span>  
  
-   <span data-ttu-id="a877e-112">言語</span><span class="sxs-lookup"><span data-stu-id="a877e-112">Language</span></span>  
  
 <span data-ttu-id="a877e-113">ページ番号については、番号の前に "ページ" という語を追加したり、</span><span class="sxs-lookup"><span data-stu-id="a877e-113">For a page number, you may want to add the word "Page" before the number.</span></span> <span data-ttu-id="a877e-114">総ページ数を表示したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a877e-114">You may also want to show the total number of pages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a877e-115">フッターに総ページ数を追加すると、レポートの実行時やプレビュー時にパフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="a877e-115">Adding the total number of pages to the footer may slow performance when you run or preview your report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-number-or-other-report-properties"></a><span data-ttu-id="a877e-116">ページ番号またはその他のレポート プロパティを追加するには</span><span class="sxs-lookup"><span data-stu-id="a877e-116">To add a page number or other report properties</span></span>  
  
1.  <span data-ttu-id="a877e-117">レポート データ ペインで [組み込みフィールド] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a877e-117">In the Report Data pane, expand the Built-in Fields folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a877e-118">[レポート データ] ペインが表示されていない場合は、[表示] タブの **[レポート データ]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="a877e-118">If you don't see the Report Data pane, on the View tab, check **Report Data**.</span></span>  
  
2.  <span data-ttu-id="a877e-119">**[ページ番号]** フィールドを、[レポート データ] ペインからレポート ヘッダーまたはレポート フッターにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a877e-119">Drag the **Page Number** field from the Report Data pane to the report header or footer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a877e-120">ページ フッターはレポートに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a877e-120">The page footer is added to the report automatically.</span></span> <span data-ttu-id="a877e-121">ページ ヘッダーを追加するには、 **[挿入]** タブで、 **[ヘッダー]** をクリックして **[ヘッダーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a877e-121">To add a page header, on the **Insert** tab, click **Header**, and then click **Add Header**.</span></span>  
    >   
    >  <span data-ttu-id="a877e-122">[&PageNumber] という単純な式が含まれているテキスト ボックスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="a877e-122">A text box that contains the simple expression [&PageNumber] is added.</span></span>  
  
### <a name="to-add-the-word-page-before-the-page-number"></a><span data-ttu-id="a877e-123">ページ番号の前に "ページ" という語を追加するには</span><span class="sxs-lookup"><span data-stu-id="a877e-123">To add the word "Page" before the page number</span></span>  
  
1.  <span data-ttu-id="a877e-124">[&PageNumber] が含まれているテキスト ボックスを右クリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a877e-124">Right-click the text box that contains [&PageNumber] and click **Expressions**.</span></span>  
  
     <span data-ttu-id="a877e-125">**[式の設定: 値]** テキスト ボックスに、=Globals!PageNumber という式が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a877e-125">The **Set Expression for: Value** text box contains the expression =Globals!PageNumber.</span></span>  
  
2.  <span data-ttu-id="a877e-126">= (等号) の後ろにカーソルを置き、「`"Page " &`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a877e-126">Place the cursor after the = sign and type `"Page " &`.</span></span>  
  
     <span data-ttu-id="a877e-127">式は、="ページ "&Globals!PageNumber となります。</span><span class="sxs-lookup"><span data-stu-id="a877e-127">The expression is now  ="Page "&Globals!PageNumber</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-total-number-of-pages-after-the-page-number"></a><span data-ttu-id="a877e-128">ページ番号の後ろに総ページ数を追加するには</span><span class="sxs-lookup"><span data-stu-id="a877e-128">To add total number of pages after the page number</span></span>  
  
1.  <span data-ttu-id="a877e-129">式が含まれているテキスト ボックスを右クリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a877e-129">Right click the text box with the expression and click **Expressions**.</span></span>  
  
2.  <span data-ttu-id="a877e-130">式の末尾に「 **&"/"&** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a877e-130">Type **&" of "&** at the end of the expression.</span></span>  
  
3.  <span data-ttu-id="a877e-131">[カテゴリ] ペインで、 **[組み込みフィールド]** を展開し、 **[TotalPages]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a877e-131">In the Category pane, expand **Built-in Fields** and double-click **TotalPages**.</span></span>  
  
     <span data-ttu-id="a877e-132">式は、="ページ "&Globals!PageNumber &"/"&Globals!TotalPages となります。</span><span class="sxs-lookup"><span data-stu-id="a877e-132">The expression is now ="Page "&Globals!PageNumber &" of "&Globals!TotalPages</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a877e-133">参照</span><span class="sxs-lookup"><span data-stu-id="a877e-133">See Also</span></span>  
 <span data-ttu-id="a877e-134">[ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a877e-134">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a877e-135">テキスト ボックス内のテキストの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a877e-135">Format Text in a Text Box &#40;Report Builder and SSRS&#41;</span></span>](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  
