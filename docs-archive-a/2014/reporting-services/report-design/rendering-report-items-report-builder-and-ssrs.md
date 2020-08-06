---
title: レポート アイテムのレンダリング (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 99ebb4dc-41cc-42ac-82dd-a2b0e31155a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4e0b1dabee096cfbaab53227926633f8d7a3697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640693"
---
# <a name="rendering-report-items-report-builder-and-ssrs"></a><span data-ttu-id="946a9-102">レポート アイテムのレンダリング (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="946a9-102">Rendering Report Items (Report Builder and SSRS)</span></span>
  <span data-ttu-id="946a9-103">レポート アイテムの数、サイズ、および位置は、レポート本文の改ページに影響します。</span><span class="sxs-lookup"><span data-stu-id="946a9-103">The number, size, and location of report items affect how the renderers paginate the report body.</span></span> <span data-ttu-id="946a9-104">以降、各種のレポート アイテムがどのようにレンダリングされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="946a9-104">Below is a description of how various report items are rendered.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="overlapping-report-items"></a><span data-ttu-id="946a9-105">重なり合うレポート アイテム</span><span class="sxs-lookup"><span data-stu-id="946a9-105">Overlapping Report Items</span></span>  
 <span data-ttu-id="946a9-106">HTML、MHTML、Word、Excel、プレビュー、およびレポート ビューアーでは、レポート アイテムの重なりがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="946a9-106">Overlapping report items are not supported in HTML, MHTML, Word, Excel, in Preview, or the Report Viewer.</span></span> <span data-ttu-id="946a9-107">重なり合うアイテムは移動されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-107">If overlapping items exist, they are moved.</span></span> <span data-ttu-id="946a9-108">重なり合うレポート アイテムには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-108">The following rules are applied to overlapping report items:</span></span>  
  
-   <span data-ttu-id="946a9-109">レポート アイテムの縦方向の重なりの方が大きい場合、重なり合ういずれかのアイテムが右方向に移動されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-109">If the vertical overlap of report items is greater, one of the overlapping items is moved to the right.</span></span> <span data-ttu-id="946a9-110">左端に最も近いアイテムは、元の位置に保たれます。</span><span class="sxs-lookup"><span data-stu-id="946a9-110">The left-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="946a9-111">レポート アイテムの横方向の重なりの方が大きい場合、重なり合ういずれかのアイテムが下方向に移動されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-111">If the horizontal overlap of report items is greater, one of the overlapping items is moved down.</span></span> <span data-ttu-id="946a9-112">上端に最も近いアイテムは、元の位置に保たれます。</span><span class="sxs-lookup"><span data-stu-id="946a9-112">The top-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="946a9-113">レポート アイテムの縦方向と横方向の重なりが等しい場合、重なり合ういずれかのアイテムが右方向に移動されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-113">If the vertical and horizontal overlap is equal, one of the overlapping items is moved to the right.</span></span> <span data-ttu-id="946a9-114">左端に最も近いアイテムは、元の位置に保たれます。</span><span class="sxs-lookup"><span data-stu-id="946a9-114">The left-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="946a9-115">重なりを修正するためにアイテムを移動する必要がある場合、隣接するレポート アイテムが下方向または右方向に移動されますが、その際、上または左にあるレポート アイテムとの最小間隔が維持されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-115">If an item must be moved to correct overlapping, adjacent report items move down and/or to the right to maintain a minimum amount of spacing between the item and the report items that end above it and/or to the left of it.</span></span> <span data-ttu-id="946a9-116">たとえば、2 つのレポート アイテムが縦に重なっているとき、その 2 インチ右側に、3 つ目のレポート アイテムが存在するとします。</span><span class="sxs-lookup"><span data-stu-id="946a9-116">For example, suppose two report items overlap vertically and a third report item is 2 inches to the right of them.</span></span> <span data-ttu-id="946a9-117">重なっているレポート アイテムが右に移動されるとき、3 つ目のレポート アイテムも、左側にあるレポート アイテムとの 2 インチの間隔を保ったまま右に移動されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-117">When the overlapping report item is moved to the right, the third report item moves to the right as well in order to maintain the 2 inches between itself and the report item to its left.</span></span>  
  
 <span data-ttu-id="946a9-118">印刷を含め、ハード改ページ形式では、レポート アイテムの重なりがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="946a9-118">Overlapping report items are supported in hard page-break formats, including print.</span></span>  
  
## <a name="visibility-and-report-items"></a><span data-ttu-id="946a9-119">可視性とレポート アイテム</span><span class="sxs-lookup"><span data-stu-id="946a9-119">Visibility and Report Items</span></span>  
 <span data-ttu-id="946a9-120">レポート アイテムの表示と非表示を既定の設定のままにすることもできますが、式を使用して、条件によって表示と非表示を切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="946a9-120">Report items can be hidden or displayed by default, or hidden or displayed conditionally using expressions.</span></span> <span data-ttu-id="946a9-121">必要に応じて、別のレポート アイテムをクリックすることによって、可視性を切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="946a9-121">Optionally, the visibility can be switched by clicking another report item.</span></span>  
  
 <span data-ttu-id="946a9-122">レポート アイテムのレンダリング時には、可視性に関して次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-122">The following visibility rules apply when rendering report items:</span></span>  
  
-   <span data-ttu-id="946a9-123">レポート アイテムとその内容が常に非表示である場合 (つまり、式によって非表示にされているわけでも、別のレポート アイテムのクリックによって表示/非表示を切り替えられるわけでもない場合)、そのレポート アイテムの右側または下に他のレポート アイテムがあっても、空いた領域を埋めるための移動は行われません。</span><span class="sxs-lookup"><span data-stu-id="946a9-123">If a report item and its contents are always hidden (it is not hidden based on an expression or its visibility cannot be switched by clicking another report item), then other report items to the right or below it do not move to fill the empty space.</span></span> <span data-ttu-id="946a9-124">たとえば、四角形とそこに含まれる画像が非表示になっている場合、その四角形のすぐ右にあるレポート アイテムは左側に移動されないので、一見、空いた領域が存在するように見えます。</span><span class="sxs-lookup"><span data-stu-id="946a9-124">For example, if a rectangle and the image contained within it are hidden, the report item that starts to the right of the rectangle does not move to the left to fill what appears to be empty space.</span></span> <span data-ttu-id="946a9-125">四角形によって占有される領域はそのまま維持されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-125">The space occupied by the rectangle is preserved.</span></span>  
  
-   <span data-ttu-id="946a9-126">レポート アイテムとその内容が条件によって非表示になっている場合 (つまり、式によって非表示にされているか、別のレポート アイテムのクリックによって非表示に切り替えられている場合)、アイテムが非表示のときにはそのレポート アイテムの右側または下にある他のレポート アイテムが左に移動され、空いた領域が埋められます。</span><span class="sxs-lookup"><span data-stu-id="946a9-126">If a report item and its contents are hidden conditionally (it is hidden based on an expression or its visibility is switched by clicking another report item), then report items to the right or below it move to the left to fill in the space when the item is hidden.</span></span>  
  
-   <span data-ttu-id="946a9-127">レポート アイテムとその内容の表示/非表示を、別のレポート アイテムのクリックによって切り替えることができる場合、最初に表示したときのみ、レポート アイテムとその内容が収まるように改ページが調整されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-127">If the visibility of a report item and its contents can be switched by clicking another report item, then pagination changes to accommodate the report item and its contents only when it is initially displayed.</span></span>  
  
## <a name="keeping-report-items-together-on-a-single-page"></a><span data-ttu-id="946a9-128">レポート アイテムをまとめて 1 ページに収める</span><span class="sxs-lookup"><span data-stu-id="946a9-128">Keeping Report Items Together on a Single Page</span></span>  
 <span data-ttu-id="946a9-129">グループとして維持したり 1 つにまとめるためのプロパティを暗黙的または明示的に設定することにより、レポート内の複数のレポート アイテムをまとめて 1 ページに収めることができます。</span><span class="sxs-lookup"><span data-stu-id="946a9-129">Many report items within a report can be kept together on a single page implicitly or explicitly by setting the keep with group or keep together properties.</span></span> <span data-ttu-id="946a9-130">レポート アイテムに論理改ページが含まれず、また、そのサイズが使用可能なページ領域よりも小さければ、レポート アイテムは常に同じページにレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="946a9-130">Report items are always rendered on the same page if the report item does not have any logical page breaks and is smaller in size than the usable page area.</span></span> <span data-ttu-id="946a9-131">レポート アイテム全体を本来あるべきページに収めることができない場合、そのレポート アイテムの前にハード改ページが挿入され、強制的に次のページに移動されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-131">If a report item does not fit completely on the page on which it would usually start, a hard page break is inserted before the report item, forcing it to the next page.</span></span> <span data-ttu-id="946a9-132">ソフト改ページ レンダラーの場合は、レポート アイテムが収まるようにページが拡大されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-132">For soft page-break renderers, the page grows to accommodate the report item.</span></span>  
  
 <span data-ttu-id="946a9-133">レポート アイテムが常に非表示になっている場合、アイテムを 1 つにまとめるための規則は無視されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-133">When the report item is always hidden, the rules for keeping items together are ignored.</span></span>  
  
 <span data-ttu-id="946a9-134">次のアイテムは常にひとまとまりで表示されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-134">The following items are always kept together:</span></span>  
  
-   <span data-ttu-id="946a9-135">画像。</span><span class="sxs-lookup"><span data-stu-id="946a9-135">Images.</span></span>  
  
-   <span data-ttu-id="946a9-136">線 :</span><span class="sxs-lookup"><span data-stu-id="946a9-136">Lines.</span></span>  
  
-   <span data-ttu-id="946a9-137">グラフ、ゲージ、およびマップ。</span><span class="sxs-lookup"><span data-stu-id="946a9-137">Charts, gauges, and maps.</span></span>  
  
-   <span data-ttu-id="946a9-138">グループとして維持するオプションを選択することによって、他のページに分けて出現するデータ領域の単一行。</span><span class="sxs-lookup"><span data-stu-id="946a9-138">A single row in a data region that appears separately on another page, by selecting the keep with group option.</span></span> <span data-ttu-id="946a9-139">この場合は、行が孤立しないよう、暗黙的に少なくとも 1 つのグループで単一行にまとめられます。</span><span class="sxs-lookup"><span data-stu-id="946a9-139">This will implicitly keep together the single row with at least one instance of the group so that the row is not orphaned.</span></span> <span data-ttu-id="946a9-140">このオプションは、データ領域またはグループに対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="946a9-140">You can set this option on a data region or a group.</span></span>  
  
-   <span data-ttu-id="946a9-141">データ領域のヘッダー領域。</span><span class="sxs-lookup"><span data-stu-id="946a9-141">Header area of a data region.</span></span>  
  
-   <span data-ttu-id="946a9-142">データ領域のヘッダー領域およびデータの先頭行。</span><span class="sxs-lookup"><span data-stu-id="946a9-142">Header area of a data region and the first row of data.</span></span>  
  
-   <span data-ttu-id="946a9-143">Tablix データ領域で表示と非表示の切り替えができるレポート アイテム。</span><span class="sxs-lookup"><span data-stu-id="946a9-143">Report items that can be toggled in a tablix data region.</span></span>  
  
### <a name="priority-order"></a><span data-ttu-id="946a9-144">優先順位</span><span class="sxs-lookup"><span data-stu-id="946a9-144">Priority Order</span></span>  
 <span data-ttu-id="946a9-145">ページ サイズの制限により、レポート アイテムを 1 つにまとめるための規則どうしが競合する場合があります。</span><span class="sxs-lookup"><span data-stu-id="946a9-145">Due to page size limitations, conflicts can arise between the rules for keeping report items together.</span></span> <span data-ttu-id="946a9-146">競合が生じた場合、レンダリング時のアイテムのまとまりを保つために、次の優先順位が使用されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-146">When conflicts occur, the following priority order is used to keep items together when rendering:</span></span>  
  
-   <span data-ttu-id="946a9-147">線、グラフ、および画像。</span><span class="sxs-lookup"><span data-stu-id="946a9-147">Lines, charts, and images.</span></span>  
  
-   <span data-ttu-id="946a9-148">ウィンドウおよび孤立したコントロール。</span><span class="sxs-lookup"><span data-stu-id="946a9-148">Widow and orphan control.</span></span>  
  
-   <span data-ttu-id="946a9-149">繰り返し表示される列ヘッダーおよび行ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="946a9-149">Repeated column headers and row headers.</span></span>  
  
     <span data-ttu-id="946a9-150">ヘッダーはフッターよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-150">Headers take precedence over footers.</span></span> <span data-ttu-id="946a9-151">繰り返し表示されるグループが入れ子になっている場合は、内側のグループの方が、外側のグループよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-151">Inner repeated groups have priority over outer groups.</span></span> <span data-ttu-id="946a9-152">`RepeatWith` プロパティが設定されたアイテムでは、対象となるデータ領域に近い方のアイテムが、遠い方のアイテムよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-152">Items where the `RepeatWith` property is set that are closer to the target data region have priority over items that are farther away from the data region.</span></span>  
  
-   <span data-ttu-id="946a9-153">明示的な KeepTogether プロパティがに設定された、テキストボックスや四角形などの小さなレポートアイテム `true` 。</span><span class="sxs-lookup"><span data-stu-id="946a9-153">Small report items, such as text boxes or rectangles, with an explicit KeepTogether property set to `true`.</span></span>  
  
-   <span data-ttu-id="946a9-154">明示的な KeepTogether プロパティがに設定された、サブレポートや最も内側でない tablix メンバーなど、大きなレポートアイテム `true` 。</span><span class="sxs-lookup"><span data-stu-id="946a9-154">Large report items, such as subreports or a non-innermost tablix member, with an explicit KeepTogether property set to `true`.</span></span>  
  
-   <span data-ttu-id="946a9-155">明示的な KeepTogether プロパティがに設定された Tablix データ領域 `true` 。</span><span class="sxs-lookup"><span data-stu-id="946a9-155">Tablix data regions with an explicit KeepTogether property set to `true`.</span></span>  
  
### <a name="subreports"></a><span data-ttu-id="946a9-156">サブレポート</span><span class="sxs-lookup"><span data-stu-id="946a9-156">Subreports</span></span>  
 <span data-ttu-id="946a9-157">サブレポートは、別途レポート (.rdl) ファイルに定義された他のレポートを含んだ四角形としてレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="946a9-157">A subreport renders as a rectangle that contains another report that is defined in a separate report .rdl file.</span></span> <span data-ttu-id="946a9-158">親レポートからアクセスできるようにするには、あらかじめサブレポート ファイルをレポート サーバーにパブリッシュしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="946a9-158">The subreport file must be published to a report server before it can be accessed by the parent report.</span></span>  
  
 <span data-ttu-id="946a9-159">サブレポートのレンダリングには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-159">The following rules apply when rendering subreports:</span></span>  
  
-   <span data-ttu-id="946a9-160">サブレポートは、そのサブレポートを定義している .rdl ファイルで定義された本文サイズまで拡大できます。</span><span class="sxs-lookup"><span data-stu-id="946a9-160">Subreports can grow to the size of the body defined in the .rdl file that defines the subreport.</span></span> <span data-ttu-id="946a9-161">たとえば、サブレポートの RDL で、サブレポートの本文が 5 インチ幅として定義されていた場合、親レポート内のサブレポートの幅は 5 インチになります。</span><span class="sxs-lookup"><span data-stu-id="946a9-161">For example, if the RDL for the subreport states that the subreport body is 5 inches wide, then the subreport will be 5 inches wide within the parent report.</span></span>  
  
-   <span data-ttu-id="946a9-162">サブレポートでは、列の設定が親レポートから継承されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-162">Subreports inherit column settings from the parent report.</span></span> <span data-ttu-id="946a9-163">元の RDL で定義されている列の設定は常に無視されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-163">Column settings that are defined in the original RDL are always ignored.</span></span>  
  
-   <span data-ttu-id="946a9-164">レンダリングされるのはサブレポートの本文だけです。</span><span class="sxs-lookup"><span data-stu-id="946a9-164">Only the body of the subreport is rendered.</span></span> <span data-ttu-id="946a9-165">サブレポートを親レポート内にレンダリングした場合、サブレポートの .rdl ファイルで定義されているヘッダー セクションとフッター セクションはレンダリングされません。</span><span class="sxs-lookup"><span data-stu-id="946a9-165">Header and footer sections that are defined in the subreport's .rdl file are not rendered when the subreport is rendered in the parent report.</span></span>  
  
-   <span data-ttu-id="946a9-166">サブレポートには、明示的な KeepTogether プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="946a9-166">Subreports have an explicit KeepTogether property.</span></span> <span data-ttu-id="946a9-167">`true` に設定した場合、サブレポート内のすべてのアイテムが、可能な限り 1 ページにまとめて表示されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-167">When it is set to `true`, all the items in the subreport are kept together on one page when possible.</span></span>  
  
-   <span data-ttu-id="946a9-168">実行できなかったサブレポートは、エラー メッセージを含んだテキスト ボックスとしてレポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-168">If a subreport cannot run, it is displayed in the report as a text box with an error message.</span></span> <span data-ttu-id="946a9-169">サブレポートに適用されたスタイル プロパティは、このテキスト ボックスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-169">The style properties applied to the subreport are applied to the text box instead.</span></span>  
  
-   <span data-ttu-id="946a9-170">サブレポートが改ページで区切られている場合、サブレポートを罫線で区切るかどうかは、 **[改ページの罫線を省略]** 設定によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="946a9-170">If the subreport is split by a page break, the **Omit border on page break** setting controls whether or not the borders on the subreport are closed or open.</span></span>  
  
 <span data-ttu-id="946a9-171">サブレポートの詳細については、「[サブレポート &#40;レポート ビルダーおよび SSRS&#41;](subreports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="946a9-171">For more information about subreports, see [Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946a9-172">参照</span><span class="sxs-lookup"><span data-stu-id="946a9-172">See Also</span></span>  
 <span data-ttu-id="946a9-173">[Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="946a9-173">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="946a9-174">[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="946a9-174">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="946a9-175">[さまざまなレポート表示拡張機能の対話機能 &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="946a9-175">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 [<span data-ttu-id="946a9-176">一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="946a9-176">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
