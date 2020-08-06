---
title: '[フラットファイル接続マネージャーエディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.columns.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 40ce7537-abd0-4973-97fd-6ccb90fddfa0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6ce579f73922d2eaa2c48e98a98f52cd5836f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632611"
---
# <a name="flat-file-connection-manager-editor-columns-page"></a><span data-ttu-id="1b374-102">[フラット ファイル接続マネージャー エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="1b374-102">Flat File Connection Manager Editor (Columns Page)</span></span>
  <span data-ttu-id="1b374-103">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[列]** ページを使用すると、行および列情報を指定したり、ファイルをプレビューしたりできます。</span><span class="sxs-lookup"><span data-stu-id="1b374-103">Use the **Columns** page of the **Flat File Connection Manager Editor** dialog box to specify the row and column information, and to preview the file.</span></span>  
  
 <span data-ttu-id="1b374-104">フラット ファイル接続マネージャーの詳細については、「 [Flat File Connection Manager](connection-manager/file-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b374-104">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="1b374-105">静的オプション</span><span class="sxs-lookup"><span data-stu-id="1b374-105">Static Options</span></span>  
 <span data-ttu-id="1b374-106">**接続マネージャー名**</span><span class="sxs-lookup"><span data-stu-id="1b374-106">**Connection manager name**</span></span>  
 <span data-ttu-id="1b374-107">ワークフローにおけるフラット ファイル接続マネージャーの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b374-107">Provide a unique name for the Flat File connection in the workflow.</span></span> <span data-ttu-id="1b374-108">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b374-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="1b374-109">**説明**</span><span class="sxs-lookup"><span data-stu-id="1b374-109">**Description**</span></span>  
 <span data-ttu-id="1b374-110">接続の説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="1b374-110">Describe the connection.</span></span> <span data-ttu-id="1b374-111">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1b374-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
## <a name="flat-file-format-dynamic-options"></a><span data-ttu-id="1b374-112">フラット ファイル形式の動的オプション</span><span class="sxs-lookup"><span data-stu-id="1b374-112">Flat File Format Dynamic Options</span></span>  
  
### <a name="format--delimited"></a><span data-ttu-id="1b374-113">[形式] = [区切り記号]</span><span class="sxs-lookup"><span data-stu-id="1b374-113">Format = Delimited</span></span>  
 <span data-ttu-id="1b374-114">**[行区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="1b374-114">**Row delimiter**</span></span>  
 <span data-ttu-id="1b374-115">使用できる行区切り記号の一覧から選択するか、区切り記号テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="1b374-115">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="1b374-116">値</span><span class="sxs-lookup"><span data-stu-id="1b374-116">Value</span></span>|<span data-ttu-id="1b374-117">説明</span><span class="sxs-lookup"><span data-stu-id="1b374-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b374-118">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="1b374-118">**{CR}{LF}**</span></span>|<span data-ttu-id="1b374-119">行は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-119">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="1b374-120">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="1b374-120">**{CR}**</span></span>|<span data-ttu-id="1b374-121">行は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-121">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="1b374-122">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="1b374-122">**{LF}**</span></span>|<span data-ttu-id="1b374-123">行は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-123">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="1b374-124">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-124">**Semicolon {;}**</span></span>|<span data-ttu-id="1b374-125">行は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-125">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="1b374-126">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-126">**Colon {:}**</span></span>|<span data-ttu-id="1b374-127">行は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-127">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="1b374-128">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-128">**Comma {,}**</span></span>|<span data-ttu-id="1b374-129">行は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-129">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="1b374-130">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-130">**Tab {t}**</span></span>|<span data-ttu-id="1b374-131">行は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-131">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="1b374-132">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-132">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="1b374-133">行は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-133">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="1b374-134">**列区切り記号**</span><span class="sxs-lookup"><span data-stu-id="1b374-134">**Column delimiter**</span></span>  
 <span data-ttu-id="1b374-135">使用できる列区切り記号の一覧から選択するか、区切り記号テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="1b374-135">Select from the list of available column delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="1b374-136">値</span><span class="sxs-lookup"><span data-stu-id="1b374-136">Value</span></span>|<span data-ttu-id="1b374-137">説明</span><span class="sxs-lookup"><span data-stu-id="1b374-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b374-138">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="1b374-138">**{CR}{LF}**</span></span>|<span data-ttu-id="1b374-139">列は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-139">Columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="1b374-140">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="1b374-140">**{CR}**</span></span>|<span data-ttu-id="1b374-141">列は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-141">Columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="1b374-142">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="1b374-142">**{LF}**</span></span>|<span data-ttu-id="1b374-143">列は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-143">Columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="1b374-144">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-144">**Semicolon {;}**</span></span>|<span data-ttu-id="1b374-145">列は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-145">Columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="1b374-146">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-146">**Colon {:}**</span></span>|<span data-ttu-id="1b374-147">列は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-147">Columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="1b374-148">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-148">**Comma {,}**</span></span>|<span data-ttu-id="1b374-149">列は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-149">Columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="1b374-150">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-150">**Tab {t}**</span></span>|<span data-ttu-id="1b374-151">列は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-151">Columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="1b374-152">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-152">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="1b374-153">列は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-153">Columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="1b374-154">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="1b374-154">**Refresh**</span></span>  
 <span data-ttu-id="1b374-155">スキップする区切り記号を変更したときの効果を表示するには、 **[最新の情報に更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b374-155">View the effect of changing the delimiters to skip by clicking **Refresh**.</span></span> <span data-ttu-id="1b374-156">このボタンは、他の接続オプションを変更した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b374-156">This button only becomes visible after you have changed other connection options.</span></span>  
  
 <span data-ttu-id="1b374-157">**[プレビュー]**</span><span class="sxs-lookup"><span data-stu-id="1b374-157">**Preview rows**</span></span>  
 <span data-ttu-id="1b374-158">フラット ファイル内のサンプル データを、選択されたオプションに基づいて列と行に分割して表示します。</span><span class="sxs-lookup"><span data-stu-id="1b374-158">View sample data in the flat file, divided into columns and rows by using the options selected.</span></span>  
  
 <span data-ttu-id="1b374-159">**[列のリセット]**</span><span class="sxs-lookup"><span data-stu-id="1b374-159">**Reset Columns**</span></span>  
 <span data-ttu-id="1b374-160">元の列以外のすべての列を削除するには、 **[列のリセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b374-160">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--fixed-width"></a><span data-ttu-id="1b374-161">[形式] = [固定幅]</span><span class="sxs-lookup"><span data-stu-id="1b374-161">Format = Fixed Width</span></span>  
 <span data-ttu-id="1b374-162">**フォント**</span><span class="sxs-lookup"><span data-stu-id="1b374-162">**Font**</span></span>  
 <span data-ttu-id="1b374-163">プレビュー データの表示に使用するフォントを選択します。</span><span class="sxs-lookup"><span data-stu-id="1b374-163">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="1b374-164">**[変換元データ列]**</span><span class="sxs-lookup"><span data-stu-id="1b374-164">**Source data columns**</span></span>  
 <span data-ttu-id="1b374-165">行の幅を調整するには、赤い垂直行マーカーをスライドさせます。列の幅を調整するには、プレビュー ウィンドウの最上部のルーラーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b374-165">Adjust the width of the row by sliding the vertical red row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="1b374-166">**[行幅]**</span><span class="sxs-lookup"><span data-stu-id="1b374-166">**Row width**</span></span>  
 <span data-ttu-id="1b374-167">個々の列に対して区切り記号を追加する前に、行の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="1b374-167">Specify the length of the row before adding delimiters for individual columns.</span></span> <span data-ttu-id="1b374-168">または、プレビュー ウィンドウの赤い垂直線をドラッグして行の終わりをマークします。</span><span class="sxs-lookup"><span data-stu-id="1b374-168">Or, drag the vertical red line in the preview window to mark the end of the row.</span></span> <span data-ttu-id="1b374-169">行幅値は自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="1b374-169">The row width value is automatically updated.</span></span>  
  
 <span data-ttu-id="1b374-170">**[列のリセット]**</span><span class="sxs-lookup"><span data-stu-id="1b374-170">**Reset Columns**</span></span>  
 <span data-ttu-id="1b374-171">元の列以外のすべての列を削除するには、 **[列のリセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b374-171">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--ragged-right"></a><span data-ttu-id="1b374-172">[形式] = [幅合わせしない]</span><span class="sxs-lookup"><span data-stu-id="1b374-172">Format = Ragged Right</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b374-173">幅合わせしない形式のファイルとは、最後の列を除くすべての列が固定幅のファイルです。</span><span class="sxs-lookup"><span data-stu-id="1b374-173">Ragged right files are files in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="1b374-174">最後の列は、行区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-174">It is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="1b374-175">**フォント**</span><span class="sxs-lookup"><span data-stu-id="1b374-175">**Font**</span></span>  
 <span data-ttu-id="1b374-176">プレビュー データの表示に使用するフォントを選択します。</span><span class="sxs-lookup"><span data-stu-id="1b374-176">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="1b374-177">**[変換元データ列]**</span><span class="sxs-lookup"><span data-stu-id="1b374-177">**Source data columns**</span></span>  
 <span data-ttu-id="1b374-178">行の幅を調整するには、赤い垂直行マーカーをスライドさせます。列の幅を調整するには、プレビュー ウィンドウの最上部のルーラーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b374-178">Adjust the width of the row by sliding the vertical red row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="1b374-179">**[行区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="1b374-179">**Row delimiter**</span></span>  
 <span data-ttu-id="1b374-180">使用できる行区切り記号の一覧から選択するか、区切り記号テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="1b374-180">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="1b374-181">値</span><span class="sxs-lookup"><span data-stu-id="1b374-181">Value</span></span>|<span data-ttu-id="1b374-182">説明</span><span class="sxs-lookup"><span data-stu-id="1b374-182">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b374-183">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="1b374-183">**{CR}{LF}**</span></span>|<span data-ttu-id="1b374-184">行は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-184">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="1b374-185">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="1b374-185">**{CR}**</span></span>|<span data-ttu-id="1b374-186">行は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-186">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="1b374-187">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="1b374-187">**{LF}**</span></span>|<span data-ttu-id="1b374-188">行は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-188">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="1b374-189">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-189">**Semicolon {;}**</span></span>|<span data-ttu-id="1b374-190">行は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-190">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="1b374-191">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-191">**Colon {:}**</span></span>|<span data-ttu-id="1b374-192">行は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-192">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="1b374-193">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-193">**Comma {,}**</span></span>|<span data-ttu-id="1b374-194">行は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-194">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="1b374-195">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-195">**Tab {t}**</span></span>|<span data-ttu-id="1b374-196">行は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-196">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="1b374-197">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="1b374-197">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="1b374-198">行は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b374-198">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="1b374-199">**[列のリセット]**</span><span class="sxs-lookup"><span data-stu-id="1b374-199">**Reset Columns**</span></span>  
 <span data-ttu-id="1b374-200">元の列以外のすべての列を削除するには、 **[列のリセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b374-200">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b374-201">参照</span><span class="sxs-lookup"><span data-stu-id="1b374-201">See Also</span></span>  
 <span data-ttu-id="1b374-202">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1b374-202">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1b374-203">[[フラットファイル接続マネージャーエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="1b374-203">[Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="1b374-204">[[フラットファイル接続マネージャーエディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="1b374-204">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="1b374-205">[[フラット ファイル接続マネージャー エディター] ([プレビュー] ページ)](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)</span><span class="sxs-lookup"><span data-stu-id="1b374-205">[Flat File Connection Manager Editor &#40;Preview Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)</span></span>  
  
  
