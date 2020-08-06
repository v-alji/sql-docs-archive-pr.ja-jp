---
title: '[複数フラットファイル接続マネージャーエディター] ([詳細設定] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.advanced.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: fc883131-c03d-4ab3-8220-b51cbe243a82
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fa09b6bb7f57ef0d420f6dbd5aed43cc8640e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632558"
---
# <a name="multiple-flat-files-connection-manager-editor-advanced-page"></a><span data-ttu-id="837f0-102">[複数フラット ファイル接続マネージャー エディター] ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="837f0-102">Multiple Flat Files Connection Manager Editor (Advanced Page)</span></span>
  <span data-ttu-id="837f0-103">**[複数フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、フラット ファイル接続マネージャーが接続するテキスト ファイルの各列のデータ型や区切り記号などのプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="837f0-103">Use the **Advanced** page of the **Multiple Flat Files Connection ManagerEditor** dialog box to set properties such as data type and delimiters of each column in the text files to which the flat file connection manager connects.</span></span>  
  
 <span data-ttu-id="837f0-104">既定では、文字列の列の長さは 50 文字です。</span><span class="sxs-lookup"><span data-stu-id="837f0-104">By default, the length of string columns is 50 characters.</span></span> <span data-ttu-id="837f0-105">サンプル データを評価し、これらの列の長さを自動的に変更して、データが切り捨てられたり、列の幅が広くなりすぎないようにできます。</span><span class="sxs-lookup"><span data-stu-id="837f0-105">You can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="837f0-106">また、変換先列と互換性を持つように他のメタデータも更新できます。</span><span class="sxs-lookup"><span data-stu-id="837f0-106">You can also update other metadata to enable compatibility with destination columns.</span></span> <span data-ttu-id="837f0-107">たとえば、整数データのみを含む列のデータ型を、DT_I2 などの数値データ型に変更するなどの操作を行えます。</span><span class="sxs-lookup"><span data-stu-id="837f0-107">For example, you might change the data type of a column that contains only integer data to a numeric data type, such as DT_I2.</span></span>  
  
 <span data-ttu-id="837f0-108">複数フラット ファイル接続マネージャーの詳細については、「 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="837f0-108">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="837f0-109">Options</span><span class="sxs-lookup"><span data-stu-id="837f0-109">Options</span></span>  
 <span data-ttu-id="837f0-110">**接続マネージャー名**</span><span class="sxs-lookup"><span data-stu-id="837f0-110">**Connection manager name**</span></span>  
 <span data-ttu-id="837f0-111">ワークフロー内の複数フラット ファイル接続マネージャーの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="837f0-111">Provide a unique name for the Multiple Flat Files connection manager in the workflow.</span></span> <span data-ttu-id="837f0-112">指定された名前は、 **デザイナーの** [接続マネージャー] [!INCLUDE[ssIS](../includes/ssis-md.md)] 領域内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-112">The name provided will be displayed within the **Connection Managers** area of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="837f0-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="837f0-113">**Description**</span></span>  
 <span data-ttu-id="837f0-114">接続マネージャーの説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="837f0-114">Describe the connection manager.</span></span> <span data-ttu-id="837f0-115">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続マネージャーの目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="837f0-115">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="837f0-116">**[各列のプロパティを構成します。]**</span><span class="sxs-lookup"><span data-stu-id="837f0-116">**Configure the properties of each column**</span></span>  
 <span data-ttu-id="837f0-117">左側のペインで列を選択すると、そのプロパティが右側のペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-117">Select a column in the left pane to view its properties in the right pane.</span></span> <span data-ttu-id="837f0-118">データ型プロパティの説明については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="837f0-118">See the following table for a description of data type properties.</span></span> <span data-ttu-id="837f0-119">いくつかのプロパティは、一部のフラット ファイル形式でのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="837f0-119">Some of the properties listed are configurable only for some flat file formats.</span></span>  
  
|<span data-ttu-id="837f0-120">プロパティ</span><span class="sxs-lookup"><span data-stu-id="837f0-120">Property</span></span>|<span data-ttu-id="837f0-121">説明</span><span class="sxs-lookup"><span data-stu-id="837f0-121">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="837f0-122">**[列の型]**</span><span class="sxs-lookup"><span data-stu-id="837f0-122">**ColumnType**</span></span>|<span data-ttu-id="837f0-123">列が区切り形式、固定幅形式、幅合わせしない形式のうちどれであるかを示します。</span><span class="sxs-lookup"><span data-stu-id="837f0-123">Denotes whether the column is delimited, fixed width, or ragged right.</span></span> <span data-ttu-id="837f0-124">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="837f0-124">This property is read-only.</span></span> <span data-ttu-id="837f0-125">幅合わせしないファイルとは、最後の列以外のすべての列が固定幅を持つファイルです。最後の列は、行区切り記号で終了します。</span><span class="sxs-lookup"><span data-stu-id="837f0-125">Ragged right files are files in which every column has a fixed width, except for the last column, which is terminated by the row delimiter.</span></span>|  
|<span data-ttu-id="837f0-126">**[出力列の幅]**</span><span class="sxs-lookup"><span data-stu-id="837f0-126">**OutputColumnWidth**</span></span>|<span data-ttu-id="837f0-127">格納する値をバイト数で指定します。Unicode ファイルの場合、これは文字数として表示されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-127">Specify a value to be stored as a count of bytes; for Unicode files, this will display as a count of characters.</span></span> <span data-ttu-id="837f0-128">データ フロー タスクでは、この値を使用してフラット ファイル ソースの出力列の幅を設定します。</span><span class="sxs-lookup"><span data-stu-id="837f0-128">In the Data Flow task, this value is used to set the output column width for the Flat File source.</span></span><br /><br /> <span data-ttu-id="837f0-129">注:オブジェクト モデルでは、このプロパティの名前は MaximumWidth です。</span><span class="sxs-lookup"><span data-stu-id="837f0-129">Note: In the object model, the name of this property is MaximumWidth.</span></span>|  
|<span data-ttu-id="837f0-130">**DataType**</span><span class="sxs-lookup"><span data-stu-id="837f0-130">**DataType**</span></span>|<span data-ttu-id="837f0-131">使用できるデータ型を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="837f0-131">Select from the list of available data types.</span></span> <span data-ttu-id="837f0-132">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="837f0-132">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>|  
|<span data-ttu-id="837f0-133">**[テキスト修飾子]**</span><span class="sxs-lookup"><span data-stu-id="837f0-133">**TextQualified**</span></span>|<span data-ttu-id="837f0-134">テキストデータがテキスト修飾子文字を使用して修飾されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="837f0-134">Indicate whether text data is qualified using a text qualifier character.</span></span> <span data-ttu-id="837f0-135">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="837f0-135">Valid values are:</span></span><br /><br /> <span data-ttu-id="837f0-136">**True**:フラット ファイルのテキスト データは修飾されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-136">**True**: Text data in the flat file is qualified.</span></span><br /><br /> <span data-ttu-id="837f0-137">**False**:フラット ファイルのテキスト データは修飾されません。</span><span class="sxs-lookup"><span data-stu-id="837f0-137">**False**: Text data in the flat file is not qualified.</span></span>|  
|<span data-ttu-id="837f0-138">**名前**</span><span class="sxs-lookup"><span data-stu-id="837f0-138">**Name**</span></span>|<span data-ttu-id="837f0-139">列名を指定します。</span><span class="sxs-lookup"><span data-stu-id="837f0-139">Provide a column name.</span></span> <span data-ttu-id="837f0-140">既定では列の番号になりますが、わかりやすい一意な名前を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="837f0-140">The default is a numbered list of columns; however, you can choose any unique, descriptive name.</span></span>|  
|<span data-ttu-id="837f0-141">**[データ スケール]**</span><span class="sxs-lookup"><span data-stu-id="837f0-141">**DataScale**</span></span>|<span data-ttu-id="837f0-142">数値データの小数点以下の精度を指定します。</span><span class="sxs-lookup"><span data-stu-id="837f0-142">Specify the scale of numeric data.</span></span> <span data-ttu-id="837f0-143">これは小数点以下の桁数を表します。</span><span class="sxs-lookup"><span data-stu-id="837f0-143">Scale refers to the number of decimal places.</span></span> <span data-ttu-id="837f0-144">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="837f0-144">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>|  
|<span data-ttu-id="837f0-145">**[列区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="837f0-145">**ColumnDelimiter**</span></span>|<span data-ttu-id="837f0-146">使用できる列区切り記号の一覧から、列区切り記号を選択します。</span><span class="sxs-lookup"><span data-stu-id="837f0-146">Select from the list of available column delimiters.</span></span> <span data-ttu-id="837f0-147">テキストに出現しないと思われる区切り記号を選択してください。</span><span class="sxs-lookup"><span data-stu-id="837f0-147">Choose delimiters that are not likely to occur in the text.</span></span> <span data-ttu-id="837f0-148">固定幅列の場合、この値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-148">This value is ignored for fixed-width columns.</span></span><br /><br /> <span data-ttu-id="837f0-149">**{CR}{LF}** - 列は、復帰と改行の組み合わせで区切られます</span><span class="sxs-lookup"><span data-stu-id="837f0-149">**{CR}{LF}** - columns are delimited by a carriage return-line feed combination</span></span><br /><br /> <span data-ttu-id="837f0-150">**{CR}** - 列は、復帰で区切られます</span><span class="sxs-lookup"><span data-stu-id="837f0-150">**{CR}** - columns are delimited by a carriage return</span></span><br /><br /> <span data-ttu-id="837f0-151">**{LF}** - 列は、改行で区切られます</span><span class="sxs-lookup"><span data-stu-id="837f0-151">**{LF}** - columns are delimited by a line feed</span></span><br /><br /> <span data-ttu-id="837f0-152">**Semicolon {;}** - 列は、セミコロンで区切られます</span><span class="sxs-lookup"><span data-stu-id="837f0-152">**Semicolon {;}** - columns are delimited by a semicolon</span></span><br /><br /> <span data-ttu-id="837f0-153">**Colon {:}** - 列は、コロンで区切られます</span><span class="sxs-lookup"><span data-stu-id="837f0-153">**Colon {:}** - columns are delimited by a colon</span></span><br /><br /> <span data-ttu-id="837f0-154">**Comma {,}** - 列は、コンマで区切られます</span><span class="sxs-lookup"><span data-stu-id="837f0-154">**Comma {,}** - columns are delimited by a comma</span></span><br /><br /> <span data-ttu-id="837f0-155">**Tab {t}** - 列は、タブで区切られます</span><span class="sxs-lookup"><span data-stu-id="837f0-155">**Tab {t}** - columns are delimited by a tab</span></span><br /><br /> <span data-ttu-id="837f0-156">**Vertical bar {&#124;}** - 列は、縦棒で区切られます</span><span class="sxs-lookup"><span data-stu-id="837f0-156">**Vertical bar {&#124;}** - columns are delimited by a vertical bar</span></span>|  
|<span data-ttu-id="837f0-157">**[データ精度]**</span><span class="sxs-lookup"><span data-stu-id="837f0-157">**DataPrecision**</span></span>|<span data-ttu-id="837f0-158">数値データの精度を指定します。</span><span class="sxs-lookup"><span data-stu-id="837f0-158">Specify the precision of numeric data.</span></span> <span data-ttu-id="837f0-159">精度とは、桁数です。</span><span class="sxs-lookup"><span data-stu-id="837f0-159">Precision refers to the number of digits.</span></span> <span data-ttu-id="837f0-160">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="837f0-160">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>|  
|<span data-ttu-id="837f0-161">**[入力列の幅]**</span><span class="sxs-lookup"><span data-stu-id="837f0-161">**InputColumnWidth**</span></span>|<span data-ttu-id="837f0-162">格納する値をバイト数で指定します。Unicode ファイルの場合、これは文字数として表示されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-162">Specify a value to be stored as a count of bytes; for Unicode files, this will display as a count of characters.</span></span> <span data-ttu-id="837f0-163">区切られた列の場合、この値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-163">This value is ignored for delimited columns.</span></span><br /><br /> <span data-ttu-id="837f0-164">**注** オブジェクト モデルでは、このプロパティの名前は ColumnWidth です。</span><span class="sxs-lookup"><span data-stu-id="837f0-164">**Note** In the object model, the name of this property is ColumnWidth.</span></span>|  
  
 <span data-ttu-id="837f0-165">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="837f0-165">**New**</span></span>  
 <span data-ttu-id="837f0-166">**[新規作成]** をクリックして新しい列を追加します。</span><span class="sxs-lookup"><span data-stu-id="837f0-166">Add a new column by clicking **New**.</span></span> <span data-ttu-id="837f0-167">既定では、 **[新規作成]** ボタンをクリックすると、新しい列がリストの末尾に追加されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-167">By default, the **New** button adds a new column at the end of the list.</span></span> <span data-ttu-id="837f0-168">さらにこのボタンのドロップダウン リストには、次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="837f0-168">The button also has the following options, available in the dropdown list.</span></span>  
  
|<span data-ttu-id="837f0-169">値</span><span class="sxs-lookup"><span data-stu-id="837f0-169">Value</span></span>|<span data-ttu-id="837f0-170">説明</span><span class="sxs-lookup"><span data-stu-id="837f0-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="837f0-171">**[列の追加]**</span><span class="sxs-lookup"><span data-stu-id="837f0-171">**Add Column**</span></span>|<span data-ttu-id="837f0-172">新しい列をリストの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="837f0-172">Add a new column at the end of the list.</span></span>|  
|<span data-ttu-id="837f0-173">**[前に挿入]**</span><span class="sxs-lookup"><span data-stu-id="837f0-173">**Insert Before**</span></span>|<span data-ttu-id="837f0-174">選択した列の前に新しい列を追加します。</span><span class="sxs-lookup"><span data-stu-id="837f0-174">Insert a new column before the selected column.</span></span>|  
|<span data-ttu-id="837f0-175">**[後に挿入]**</span><span class="sxs-lookup"><span data-stu-id="837f0-175">**Insert After**</span></span>|<span data-ttu-id="837f0-176">選択した列の後に新しい列を追加します。</span><span class="sxs-lookup"><span data-stu-id="837f0-176">Insert a new column after the selected column.</span></span>|  
  
 <span data-ttu-id="837f0-177">**削除**</span><span class="sxs-lookup"><span data-stu-id="837f0-177">**Delete**</span></span>  
 <span data-ttu-id="837f0-178">列を選択して **[削除]** をクリックすると、列が削除されます。</span><span class="sxs-lookup"><span data-stu-id="837f0-178">Select a column, and then remove it by clicking **Delete**.</span></span>  
  
 <span data-ttu-id="837f0-179">**[型の推測]**</span><span class="sxs-lookup"><span data-stu-id="837f0-179">**Suggest Types**</span></span>  
 <span data-ttu-id="837f0-180">**[列の型の推測]** ダイアログ ボックスを使用して、最初に選択されたファイルのサンプル データを評価し、各列のデータ型と長さの推測を取得します。</span><span class="sxs-lookup"><span data-stu-id="837f0-180">Use the **Suggest Column Types** dialog box to evaluate sample data in the first selected file and to obtain suggestions for the data type and length of each column.</span></span> <span data-ttu-id="837f0-181">詳細については、「 [[列の型の推測] ダイアログ ボックスの UI リファレンス](connection-manager/suggest-column-types-dialog-box-ui-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="837f0-181">For more information, see [Suggest Column Types Dialog Box UI Reference](connection-manager/suggest-column-types-dialog-box-ui-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837f0-182">参照</span><span class="sxs-lookup"><span data-stu-id="837f0-182">See Also</span></span>  
 <span data-ttu-id="837f0-183">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="837f0-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="837f0-184">[[複数フラットファイル接続マネージャーエディター &#40;全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="837f0-184">[Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="837f0-185">[[複数フラットファイル接続マネージャーエディター &#40;列] ページ&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="837f0-185">[Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="837f0-186">[[複数フラット ファイル接続マネージャー エディター] &#40;[プレビュー] ページ&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)</span><span class="sxs-lookup"><span data-stu-id="837f0-186">[Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)</span></span>  
  
  