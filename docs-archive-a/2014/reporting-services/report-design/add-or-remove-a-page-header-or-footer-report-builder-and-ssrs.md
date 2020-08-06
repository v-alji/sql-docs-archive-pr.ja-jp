---
title: ページ ヘッダーまたはページ フッターの追加および削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 72988623-fee8-4a05-9f72-8fcb8e668576
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b29db3f72323c460360c872a0f60d13a808e3e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719592"
---
# <a name="add-or-remove-a-page-header-or-footer-report-builder-and-ssrs"></a><span data-ttu-id="311c3-102">ページ ヘッダーまたはページ フッターの追加および削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="311c3-102">Add or Remove a Page Header or Footer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="311c3-103">ページ ヘッダーまたはページ フッターには、静的テキスト、画像、線、四角形、および罫線を追加できます。</span><span class="sxs-lookup"><span data-stu-id="311c3-103">You can add static text, images, lines, rectangles, and borders to page headers or footers.</span></span> <span data-ttu-id="311c3-104">ヘッダーまたはフッターに変数または計算されたデータを使用する場合は、式およびデータバインド画像をテキスト ボックスに配置できます。</span><span class="sxs-lookup"><span data-stu-id="311c3-104">You can place expressions and data-bound images in a textbox if you want variable or computed data in a header or footer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="311c3-105">各表示拡張機能では、ページ ヘッダーとページ フッターの処理が異なります。</span><span class="sxs-lookup"><span data-stu-id="311c3-105">Each rendering extension processes page headers and footers differently.</span></span> <span data-ttu-id="311c3-106">詳細については、「[ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)」および「[Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="311c3-106">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) and [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-header-or-footer"></a><span data-ttu-id="311c3-107">ページ ヘッダーまたはページ フッターを追加するには</span><span class="sxs-lookup"><span data-stu-id="311c3-107">To add a page header or footer</span></span>  
  
1.  <span data-ttu-id="311c3-108">レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="311c3-108">Open a report.</span></span>  
  
2.  <span data-ttu-id="311c3-109">デザイン画面で、レポートを右クリックし、 **[挿入]** をポイントして、 **[ヘッダー]** または **[フッター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="311c3-109">On the design surface, right-click the report, point to **Insert**, and then click **Header** or **Footer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="311c3-110">**[ヘッダー]** オプションおよび **[フッター]** オプションが表示されるのは、ヘッダーまたはフッターがまだレポートに含まれていない場合のみです。</span><span class="sxs-lookup"><span data-stu-id="311c3-110">The **Header** and **Footer** options appear only when a header or footer is not already part of the report.</span></span>  
  
### <a name="to-configure-a-page-header-or-footer"></a><span data-ttu-id="311c3-111">ページ ヘッダーまたはページ フッターを構成するには</span><span class="sxs-lookup"><span data-stu-id="311c3-111">To configure a page header or footer</span></span>  
  
1.  <span data-ttu-id="311c3-112">デザイン画面で、ページ ヘッダーまたはページ フッターを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="311c3-112">On the design surface, right-click the page header or footer.</span></span>  
  
2.  <span data-ttu-id="311c3-113">**[挿入]** をポイントして、次のいずれかのアイテムをクリックし、そのアイテムをヘッダー領域またはフッター領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="311c3-113">Point to **Insert**, and then click one of the following items to add it to the header or footer area:</span></span>  
  
    -   <span data-ttu-id="311c3-114">**テキスト ボックス**</span><span class="sxs-lookup"><span data-stu-id="311c3-114">**Textbox**</span></span>  
  
    -   <span data-ttu-id="311c3-115">**線**</span><span class="sxs-lookup"><span data-stu-id="311c3-115">**Line**</span></span>  
  
    -   <span data-ttu-id="311c3-116">**四角形**</span><span class="sxs-lookup"><span data-stu-id="311c3-116">**Rectangle**</span></span>  
  
    -   <span data-ttu-id="311c3-117">**Image**</span><span class="sxs-lookup"><span data-stu-id="311c3-117">**Image**</span></span>  
  
3.  <span data-ttu-id="311c3-118">ページ ヘッダーを右クリックして **[ヘッダーのプロパティ]** をクリックし、罫線、背景画像、または色を追加したり、ヘッダーの幅を調整したりします。</span><span class="sxs-lookup"><span data-stu-id="311c3-118">Right-click the page header, and then click **Header Properties** to add borders, background images, or colors, or to adjust the width of the header.</span></span> <span data-ttu-id="311c3-119">次に、 **[OK]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="311c3-119">Then click **OK**.</span></span>  
  
4.  <span data-ttu-id="311c3-120">ページ フッターを右クリックして **[フッターのプロパティ]** をクリックし、罫線、背景画像、または色を追加したり、フッターの幅を調整したりします。</span><span class="sxs-lookup"><span data-stu-id="311c3-120">Right-click the page footer, and then click **Footer Properties** to add borders, background images, or colors, or to adjust the width of the footer.</span></span> <span data-ttu-id="311c3-121">次に、 **[OK]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="311c3-121">Then click **OK**.</span></span>  
  
### <a name="to-remove-a-page-header-or-footer"></a><span data-ttu-id="311c3-122">ページ ヘッダーまたはページ フッターを削除するには</span><span class="sxs-lookup"><span data-stu-id="311c3-122">To remove a page header or footer</span></span>  
  
1.  <span data-ttu-id="311c3-123">レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="311c3-123">Open a report.</span></span>  
  
2.  <span data-ttu-id="311c3-124">デザイン画面で、ページ ヘッダーまたはページ フッターを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="311c3-124">On the design surface, right-click the page header or footer, and then click **Delete**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="311c3-125">ページ ヘッダーまたはページ フッターを削除すると、レポートから消去されます。</span><span class="sxs-lookup"><span data-stu-id="311c3-125">When you remove a page header or footer, you delete it from the report.</span></span> <span data-ttu-id="311c3-126">それまでにページ ヘッダーまたはページ フッターに追加したアイテムは、後でページ ヘッダーまたはページ フッターを再び追加しても再表示されません。</span><span class="sxs-lookup"><span data-stu-id="311c3-126">Any items that you previously added to the page header or footer will not reappear if you subsequently add the header or footer again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311c3-127">参照</span><span class="sxs-lookup"><span data-stu-id="311c3-127">See Also</span></span>  
 [<span data-ttu-id="311c3-128">ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="311c3-128">Page Headers and Footers &#40;Report Builder and SSRS&#41;</span></span>](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
