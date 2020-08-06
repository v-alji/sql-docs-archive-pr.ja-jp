---
title: 最初または最後のページでページヘッダーまたはページフッターを非表示にする (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f87ce79b-00d7-4458-a17e-e253a20f720d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60c8789fd098df7347e9cc0f583426478aee06e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711638"
---
# <a name="hide-a-page-header-or-footer-on-the-first-or-last-page-report-builder-and-ssrs"></a><span data-ttu-id="ffb5b-102">最初のページまたは最後のページでページ ヘッダーまたはページ フッターを非表示にする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ffb5b-102">Hide a Page Header or Footer on the First or Last Page (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ffb5b-103">レポートでは、各ページの上部と下部にそれぞれページ ヘッダーとページ フッターを配置できます。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-103">A report can contain a page header and page footer that run along the top and bottom of each page, respectively.</span></span> <span data-ttu-id="ffb5b-104">ヘッダーやフッターを追加した後で、レポートの最初と最後のページのヘッダーとフッターだけを非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-104">After you a add a header or footer, you can selectively hide it on the first and last pages of a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-a-page-header-on-the-first-or-last-page"></a><span data-ttu-id="ffb5b-105">最初と最後のページでページ ヘッダーを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="ffb5b-105">To hide a page header on the first or last page</span></span>  
  
1.  <span data-ttu-id="ffb5b-106">[デザイン] ビューでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-106">Open a report in Design view.</span></span>  
  
2.  <span data-ttu-id="ffb5b-107">ページ ヘッダーを右クリックし、 **[ヘッダーのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-107">Right-click the page header, and then click **Header Properties**.</span></span> <span data-ttu-id="ffb5b-108">**[レポート ヘッダーのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-108">The **Report Header Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ffb5b-109">**[このレポートのヘッダーを表示する]** がオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-109">Verify that **Display header for this report** is not selected.</span></span>  
  
4.  <span data-ttu-id="ffb5b-110">**[印刷オプション]** セクションで、各オプションのチェック ボックスをオフにし、レポートの最初と最後のページでフッターを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-110">In the **Print options** section, clear the check box for each option to hide the display on the first or last page of the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-hide-a-page-footer-on-the-first-or-last-page"></a><span data-ttu-id="ffb5b-111">最初と最後のページでページ フッターを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="ffb5b-111">To hide a page footer on the first or last page</span></span>  
  
1.  <span data-ttu-id="ffb5b-112">[デザイン] ビューでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-112">Open a report in Design view.</span></span>  
  
2.  <span data-ttu-id="ffb5b-113">ページ フッターを右クリックし、 **[フッターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-113">Right-click the page footer, and then click **Footer Properties**.</span></span> <span data-ttu-id="ffb5b-114">**[レポート フッターのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-114">The **Report Footer Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ffb5b-115">**[このレポートのフッターを表示する]** がオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-115">Verify that **Display footer for this report** is not selected.</span></span>  
  
4.  <span data-ttu-id="ffb5b-116">**[印刷オプション]** セクションで、各オプションのチェック ボックスをオフにし、レポートの最初と最後のページでフッターを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-116">In the **Print options** section, clear the check box for each option to hide the display on the first or last page of the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ffb5b-117">参照</span><span class="sxs-lookup"><span data-stu-id="ffb5b-117">See Also</span></span>  
 <span data-ttu-id="ffb5b-118">[ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ffb5b-118">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ffb5b-119">[Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ffb5b-119">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ffb5b-120">ページ ヘッダーまたはページ フッターの追加および削除 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ffb5b-120">Add or Remove a Page Header or Footer &#40;Report Builder and SSRS&#41;</span></span>](add-or-remove-a-page-header-or-footer-report-builder-and-ssrs.md)  
  
  
