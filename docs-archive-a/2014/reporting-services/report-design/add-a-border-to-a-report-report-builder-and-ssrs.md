---
title: レポートへの罫線の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf4a0c2c117774a0f3b25ca0644796fd067bc971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739379"
---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="081d9-102">レポートへの罫線の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="081d9-102">Add a Border to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="081d9-103">線や四角形を追加せずに、ヘッダー、フッター、およびレポート本文自体に罫線を追加することで、レポートに罫線を追加できます。</span><span class="sxs-lookup"><span data-stu-id="081d9-103">You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.</span></span>  
  
 <span data-ttu-id="081d9-104">ページ ヘッダーとページ フッターに表示されるレポートの罫線を追加する場合は、レポートの最初と最後のページでヘッダーとフッターを非表示にしないでください。</span><span class="sxs-lookup"><span data-stu-id="081d9-104">If you add a report border that appears on the page header and footer, do not suppress the header and footer on the first and last pages of the report.</span></span> <span data-ttu-id="081d9-105">非表示にした場合、レポートの最初と最後のページの上部または下部で罫線が一部しか表示されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="081d9-105">If you do, the border may appear cut off at the top or bottom of the first and last pages of the report.</span></span> <span data-ttu-id="081d9-106">詳細については、「[ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="081d9-106">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-border-to-a-report"></a><span data-ttu-id="081d9-107">レポートに罫線を追加するには</span><span class="sxs-lookup"><span data-stu-id="081d9-107">To add a border to a report</span></span>  
  
1.  <span data-ttu-id="081d9-108">ヘッダー内のアイテムの外側で右クリックし、 **[ヘッダーのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="081d9-108">Right-click in the header outside any items in the header, and click **Header Properties**.</span></span> <span data-ttu-id="081d9-109">**[罫線]** タブで、左、上、右に、必要なスタイルを指定した罫線を追加します。</span><span class="sxs-lookup"><span data-stu-id="081d9-109">On the **Border** tab, add a left, top, and right border with the style you want.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="081d9-110">レポートでヘッダーを使用しない場合は、レポート本文の周りにのみ罫線を配置することも、[**挿入**] タブからヘッダーを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="081d9-110">If you do not use headers in your report, you can place borders around just the report body, or you can add headers from the **Insert** tab.</span></span>  
  
2.  <span data-ttu-id="081d9-111">デザイン画面のアイテムの外側の本文で右クリックし、 **[本文のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="081d9-111">Right-click in the body outside any items on the design surface, and click **Body Properties**.</span></span> <span data-ttu-id="081d9-112">**[罫線]** タブで、左および右に、必要なスタイルを指定した罫線を追加します。</span><span class="sxs-lookup"><span data-stu-id="081d9-112">On the **Border** tab, add a left and right border with the style you want.</span></span>  
  
3.  <span data-ttu-id="081d9-113">フッター内のアイテムの外側で右クリックし、 **[フッターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="081d9-113">Right-click in the footer outside any items in the footer, and click **Footer Properties**.</span></span> <span data-ttu-id="081d9-114">**[罫線]** タブで、左、下、右に、必要なスタイルを指定した罫線を追加します。</span><span class="sxs-lookup"><span data-stu-id="081d9-114">On the **Border** tab, add a left, bottom, and right border with the style you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081d9-115">参照</span><span class="sxs-lookup"><span data-stu-id="081d9-115">See Also</span></span>  
 [<span data-ttu-id="081d9-116">四角形と線 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="081d9-116">Rectangles and Lines &#40;Report Builder and SSRS&#41;</span></span>](rectangles-and-lines-report-builder-and-ssrs.md)  
  
  
