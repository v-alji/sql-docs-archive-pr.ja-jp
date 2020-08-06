---
title: '[複数フラットファイル接続マネージャーエディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.columns.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a7f4936f0722754b414076820eda7dcf2dc8dc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632553"
---
# <a name="multiple-flat-files-connection-manager-editor-columns-page"></a><span data-ttu-id="c8dfa-102">[複数フラット ファイル接続マネージャー エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="c8dfa-102">Multiple Flat Files Connection Manager Editor (Columns Page)</span></span>
  <span data-ttu-id="c8dfa-103">**[複数フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[列]** ノードを使用すると、行と列の情報を指定し、最初に選択したファイルをプレビューできます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-103">Use the **Columns** node of the **Multiple Flat Files Connection Manager Editor** dialog box to specify the row and column information, and to preview the first selected file.</span></span>  
  
 <span data-ttu-id="c8dfa-104">複数フラット ファイル接続マネージャーの詳細については、「 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-104">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="c8dfa-105">静的オプション</span><span class="sxs-lookup"><span data-stu-id="c8dfa-105">Static Options</span></span>  
 <span data-ttu-id="c8dfa-106">**接続マネージャー名**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-106">**Connection manager name**</span></span>  
 <span data-ttu-id="c8dfa-107">ワークフローにおける複数フラット ファイル接続の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-107">Provide a unique name for the Multiple Flat Files connection in the workflow.</span></span> <span data-ttu-id="c8dfa-108">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="c8dfa-109">**説明**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-109">**Description**</span></span>  
 <span data-ttu-id="c8dfa-110">接続の説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-110">Describe the connection.</span></span> <span data-ttu-id="c8dfa-111">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
## <a name="flat-file-format-dynamic-options"></a><span data-ttu-id="c8dfa-112">フラット ファイル形式の動的オプション</span><span class="sxs-lookup"><span data-stu-id="c8dfa-112">Flat File Format Dynamic Options</span></span>  
  
### <a name="format--delimited"></a><span data-ttu-id="c8dfa-113">[形式] = [区切り記号]</span><span class="sxs-lookup"><span data-stu-id="c8dfa-113">Format = Delimited</span></span>  
 <span data-ttu-id="c8dfa-114">**[行区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-114">**Row delimiter**</span></span>  
 <span data-ttu-id="c8dfa-115">使用できる行区切り記号の一覧から選択するか、区切り記号テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-115">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="c8dfa-116">値</span><span class="sxs-lookup"><span data-stu-id="c8dfa-116">Value</span></span>|<span data-ttu-id="c8dfa-117">説明</span><span class="sxs-lookup"><span data-stu-id="c8dfa-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c8dfa-118">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-118">**{CR}{LF}**</span></span>|<span data-ttu-id="c8dfa-119">行は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-119">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="c8dfa-120">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-120">**{CR}**</span></span>|<span data-ttu-id="c8dfa-121">行は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-121">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="c8dfa-122">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-122">**{LF}**</span></span>|<span data-ttu-id="c8dfa-123">行は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-123">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="c8dfa-124">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-124">**Semicolon {;}**</span></span>|<span data-ttu-id="c8dfa-125">行は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-125">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="c8dfa-126">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-126">**Colon {:}**</span></span>|<span data-ttu-id="c8dfa-127">行は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-127">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="c8dfa-128">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-128">**Comma {,}**</span></span>|<span data-ttu-id="c8dfa-129">行は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-129">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="c8dfa-130">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-130">**Tab {t}**</span></span>|<span data-ttu-id="c8dfa-131">行は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-131">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="c8dfa-132">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-132">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="c8dfa-133">行は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-133">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="c8dfa-134">**列区切り記号**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-134">**Column delimiter**</span></span>  
 <span data-ttu-id="c8dfa-135">使用できる列区切り記号の一覧から選択するか、区切り記号テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-135">Select from the list of available column delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="c8dfa-136">値</span><span class="sxs-lookup"><span data-stu-id="c8dfa-136">Value</span></span>|<span data-ttu-id="c8dfa-137">説明</span><span class="sxs-lookup"><span data-stu-id="c8dfa-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c8dfa-138">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-138">**{CR}{LF}**</span></span>|<span data-ttu-id="c8dfa-139">列は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-139">Columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="c8dfa-140">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-140">**{CR}**</span></span>|<span data-ttu-id="c8dfa-141">列は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-141">Columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="c8dfa-142">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-142">**{LF}**</span></span>|<span data-ttu-id="c8dfa-143">列は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-143">Columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="c8dfa-144">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-144">**Semicolon {;}**</span></span>|<span data-ttu-id="c8dfa-145">列は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-145">Columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="c8dfa-146">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-146">**Colon {:}**</span></span>|<span data-ttu-id="c8dfa-147">列は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-147">Columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="c8dfa-148">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-148">**Comma {,}**</span></span>|<span data-ttu-id="c8dfa-149">列は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-149">Columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="c8dfa-150">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-150">**Tab {t}**</span></span>|<span data-ttu-id="c8dfa-151">列は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-151">Columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="c8dfa-152">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-152">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="c8dfa-153">列は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-153">Columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="c8dfa-154">**[列のリセット]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-154">**Reset Columns**</span></span>  
 <span data-ttu-id="c8dfa-155">元の列以外のすべての列を削除するには、 **[列のリセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-155">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--fixed-width"></a><span data-ttu-id="c8dfa-156">[形式] = [固定幅]</span><span class="sxs-lookup"><span data-stu-id="c8dfa-156">Format = Fixed Width</span></span>  
 <span data-ttu-id="c8dfa-157">**フォント**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-157">**Font**</span></span>  
 <span data-ttu-id="c8dfa-158">プレビュー データの表示に使用するフォントを選択します。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-158">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="c8dfa-159">**[変換元データ列]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-159">**Source data columns**</span></span>  
 <span data-ttu-id="c8dfa-160">行の幅を調整するには、垂直行マーカーをスライドさせます。列の幅を調整するには、プレビュー ウィンドウの最上部のルーラーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-160">Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="c8dfa-161">**[行幅]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-161">**Row width**</span></span>  
 <span data-ttu-id="c8dfa-162">個々の列に対して区切り記号を追加する前に、行の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-162">Specify the length of the row before adding delimiters for individual columns.</span></span> <span data-ttu-id="c8dfa-163">または、プレビュー ウィンドウの垂直線をドラッグして行の終わりをマークします。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-163">Or, drag the vertical line in the preview window to mark the end of the row.</span></span> <span data-ttu-id="c8dfa-164">行幅値は自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-164">The row width value is automatically updated.</span></span>  
  
 <span data-ttu-id="c8dfa-165">**[列のリセット]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-165">**Reset Columns**</span></span>  
 <span data-ttu-id="c8dfa-166">元の列以外のすべての列を削除するには、 **[列のリセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-166">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--ragged-right"></a><span data-ttu-id="c8dfa-167">[形式] = [幅合わせしない]</span><span class="sxs-lookup"><span data-stu-id="c8dfa-167">Format = Ragged Right</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8dfa-168">幅合わせしない形式のファイルとは、最後の列を除くすべての列が固定幅のファイルです。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-168">Ragged right files are those in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="c8dfa-169">最後の列は、行区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-169">It is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="c8dfa-170">**フォント**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-170">**Font**</span></span>  
 <span data-ttu-id="c8dfa-171">プレビュー データの表示に使用するフォントを選択します。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-171">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="c8dfa-172">**[変換元データ列]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-172">**Source data columns**</span></span>  
 <span data-ttu-id="c8dfa-173">行の幅を調整するには、垂直行マーカーをスライドさせます。列の幅を調整するには、プレビュー ウィンドウの最上部のルーラーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-173">Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="c8dfa-174">**[行区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-174">**Row delimiter**</span></span>  
 <span data-ttu-id="c8dfa-175">使用できる行区切り記号の一覧から選択するか、区切り記号テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-175">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="c8dfa-176">値</span><span class="sxs-lookup"><span data-stu-id="c8dfa-176">Value</span></span>|<span data-ttu-id="c8dfa-177">説明</span><span class="sxs-lookup"><span data-stu-id="c8dfa-177">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c8dfa-178">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-178">**{CR}{LF}**</span></span>|<span data-ttu-id="c8dfa-179">行は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-179">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="c8dfa-180">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-180">**{CR}**</span></span>|<span data-ttu-id="c8dfa-181">行は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-181">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="c8dfa-182">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-182">**{LF}**</span></span>|<span data-ttu-id="c8dfa-183">行は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-183">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="c8dfa-184">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-184">**Semicolon {;}**</span></span>|<span data-ttu-id="c8dfa-185">行は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-185">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="c8dfa-186">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-186">**Colon {:}**</span></span>|<span data-ttu-id="c8dfa-187">行は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-187">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="c8dfa-188">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-188">**Comma {,}**</span></span>|<span data-ttu-id="c8dfa-189">行は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-189">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="c8dfa-190">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-190">**Tab {t}**</span></span>|<span data-ttu-id="c8dfa-191">行は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-191">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="c8dfa-192">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-192">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="c8dfa-193">行は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-193">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="c8dfa-194">**[列のリセット]**</span><span class="sxs-lookup"><span data-stu-id="c8dfa-194">**Reset Columns**</span></span>  
 <span data-ttu-id="c8dfa-195">元の列以外のすべての列を削除するには、 **[列のリセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8dfa-195">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8dfa-196">参照</span><span class="sxs-lookup"><span data-stu-id="c8dfa-196">See Also</span></span>  
 <span data-ttu-id="c8dfa-197">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c8dfa-197">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c8dfa-198">[[複数フラットファイル接続マネージャーエディター &#40;全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="c8dfa-198">[Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="c8dfa-199">[[複数フラットファイル接続マネージャーエディター &#40;[詳細設定] ページ&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="c8dfa-199">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="c8dfa-200">[[複数フラット ファイル接続マネージャー エディター] &#40;[プレビュー] ページ&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)</span><span class="sxs-lookup"><span data-stu-id="c8dfa-200">[Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)</span></span>  
  
  
