---
title: '[複数フラットファイル接続マネージャーエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.general.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: 00129d43-2772-413b-bdf8-ac5de81cf4a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f30a422794723f216d30e05f0750fb1e974e0920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736528"
---
# <a name="multiple-flat-files-connection-manager-editor-general-page"></a><span data-ttu-id="e8fe6-102">[複数フラット ファイル接続マネージャー エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="e8fe6-102">Multiple Flat Files Connection Manager Editor (General Page)</span></span>
  <span data-ttu-id="e8fe6-103">**[複数フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、同じデータ形式を持つファイルのグループを選択したり、そのデータ形式を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-103">Use the **General** page of the **Multiple Flat Files Connection Manager Editor** dialog box to select a group of files that have the same data format, and to specify their data format.</span></span> <span data-ttu-id="e8fe6-104">複数フラット ファイル接続は、パッケージが同じ形式のテキスト ファイルのグループに接続できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-104">A multiple flat files connection enables a package to connect to a group of text files that have the same format.</span></span>  
  
 <span data-ttu-id="e8fe6-105">複数フラット ファイル接続マネージャーの詳細については、「 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-105">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e8fe6-106">Options</span><span class="sxs-lookup"><span data-stu-id="e8fe6-106">Options</span></span>  
 <span data-ttu-id="e8fe6-107">**接続マネージャー名**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-107">**Connection manager name**</span></span>  
 <span data-ttu-id="e8fe6-108">ワークフローにおける複数フラット ファイル接続の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-108">Provide a unique name for the Multiple Flat Files connection in the workflow.</span></span> <span data-ttu-id="e8fe6-109">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-109">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="e8fe6-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-110">**Description**</span></span>  
 <span data-ttu-id="e8fe6-111">接続の説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-111">Describe the connection.</span></span> <span data-ttu-id="e8fe6-112">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-112">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="e8fe6-113">**ファイル名**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-113">**File names**</span></span>  
 <span data-ttu-id="e8fe6-114">複数フラット ファイル接続で使用するパスおよびファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-114">Type the path and file names to use in the Multiple Flat Files connection.</span></span> <span data-ttu-id="e8fe6-115">複数のファイルを指定するには、たとえば、"C:\\*.txt" のようにワイルドカード文字を使用するか、縦棒パイプ文字 (|) をファイル名の区切り文字として使用します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-115">You can specify multiple files by using wildcard characters, as in the example "C:\\*.txt", or by using the vertical pipe character (|) to separate multiple file names.</span></span> <span data-ttu-id="e8fe6-116">すべてのファイルのデータ形式が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-116">All files must have the same data format.</span></span>  
  
 <span data-ttu-id="e8fe6-117">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-117">**Browse**</span></span>  
 <span data-ttu-id="e8fe6-118">複数フラット ファイル接続で使用するファイルの名前を参照します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-118">Browse the file names to use in the Multiple Flat Files connection.</span></span> <span data-ttu-id="e8fe6-119">複数のファイルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-119">You can select multiple files.</span></span> <span data-ttu-id="e8fe6-120">すべてのファイルのデータ形式が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-120">All files must have the same data format.</span></span>  
  
 <span data-ttu-id="e8fe6-121">**ロケール**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-121">**Locale**</span></span>  
 <span data-ttu-id="e8fe6-122">場所を指定して、順序付けおよび日時の変換に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-122">Specify the location to provide information for ordering and for date and time conversion.</span></span>  
  
 <span data-ttu-id="e8fe6-123">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-123">**Unicode**</span></span>  
 <span data-ttu-id="e8fe6-124">Unicode を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-124">Indicate whether to use Unicode.</span></span> <span data-ttu-id="e8fe6-125">Unicode を使用する場合は、コード ページを指定できません。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-125">Using Unicode precludes specifying a code page.</span></span>  
  
 <span data-ttu-id="e8fe6-126">**コード ページ**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-126">**Code page**</span></span>  
 <span data-ttu-id="e8fe6-127">非 Unicode テキストのコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-127">Specify the code page for non-Unicode text.</span></span>  
  
 <span data-ttu-id="e8fe6-128">**形式**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-128">**Format**</span></span>  
 <span data-ttu-id="e8fe6-129">区切り形式、固定幅形式、または幅合わせしない形式を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-129">Indicate whether to use delimited, fixed width, or ragged right formatting.</span></span> <span data-ttu-id="e8fe6-130">すべてのファイルのデータ形式が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-130">All files must have the same data format.</span></span>  
  
|<span data-ttu-id="e8fe6-131">値</span><span class="sxs-lookup"><span data-stu-id="e8fe6-131">Value</span></span>|<span data-ttu-id="e8fe6-132">説明</span><span class="sxs-lookup"><span data-stu-id="e8fe6-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8fe6-133">区切り記号</span><span class="sxs-lookup"><span data-stu-id="e8fe6-133">Delimited</span></span>|<span data-ttu-id="e8fe6-134">列は、 **[列]** ページで指定した区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-134">Columns are separated by delimiters, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="e8fe6-135">固定幅ファイル</span><span class="sxs-lookup"><span data-stu-id="e8fe6-135">Fixed width</span></span>|<span data-ttu-id="e8fe6-136">列は、 **[列]** ページでマーカー ラインをドラッグして指定した幅に固定されます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-136">Columns have a fixed width, specified by dragging marker lines on the **Columns** page.</span></span>|  
|<span data-ttu-id="e8fe6-137">[幅合わせしない]</span><span class="sxs-lookup"><span data-stu-id="e8fe6-137">Ragged right</span></span>|<span data-ttu-id="e8fe6-138">幅合わせしないファイルとは、最後の列以外のすべての列が固定幅を持つファイルです。最後の列は、 **[列]** ページで指定した行区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-138">Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter, specified on the **Columns** page.</span></span>|  
  
 <span data-ttu-id="e8fe6-139">**テキスト修飾子**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-139">**Text qualifier**</span></span>  
 <span data-ttu-id="e8fe6-140">使用するテキスト修飾子を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-140">Specify the text qualifier to use.</span></span> <span data-ttu-id="e8fe6-141">たとえば、テキストを引用符で囲むように指定できます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-141">For example, you can specify to enclose text with quotation marks.</span></span>  
  
 <span data-ttu-id="e8fe6-142">**[ヘッダー行区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-142">**Header row delimiter**</span></span>  
 <span data-ttu-id="e8fe6-143">ヘッダー行の区切り記号の一覧から選択するか、区切り記号テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-143">Select from the list of delimiters for header rows, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="e8fe6-144">値</span><span class="sxs-lookup"><span data-stu-id="e8fe6-144">Value</span></span>|<span data-ttu-id="e8fe6-145">説明</span><span class="sxs-lookup"><span data-stu-id="e8fe6-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8fe6-146">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-146">**{CR}{LF}**</span></span>|<span data-ttu-id="e8fe6-147">ヘッダー行は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-147">The header row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="e8fe6-148">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-148">**{CR}**</span></span>|<span data-ttu-id="e8fe6-149">ヘッダー行は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-149">The header row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="e8fe6-150">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-150">**{LF}**</span></span>|<span data-ttu-id="e8fe6-151">ヘッダー行は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-151">The header row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="e8fe6-152">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-152">**Semicolon {;}**</span></span>|<span data-ttu-id="e8fe6-153">ヘッダー行は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-153">The header row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="e8fe6-154">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-154">**Colon {:}**</span></span>|<span data-ttu-id="e8fe6-155">ヘッダー行は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-155">The header row is delimited by a colon.</span></span>|  
|<span data-ttu-id="e8fe6-156">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-156">**Comma {,}**</span></span>|<span data-ttu-id="e8fe6-157">ヘッダー行は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-157">The header row is delimited by a comma.</span></span>|  
|<span data-ttu-id="e8fe6-158">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-158">**Tab {t}**</span></span>|<span data-ttu-id="e8fe6-159">ヘッダー行は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-159">The header row is delimited by a tab.</span></span>|  
|<span data-ttu-id="e8fe6-160">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-160">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="e8fe6-161">ヘッダー行は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-161">The header row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="e8fe6-162">**[スキップするヘッダー行数]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-162">**Header rows to skip**</span></span>  
 <span data-ttu-id="e8fe6-163">必要に応じて、スキップするヘッダー行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-163">Specify the number of header rows to skip, if any.</span></span>  
  
 <span data-ttu-id="e8fe6-164">**[先頭データ行を列名として使用する]**</span><span class="sxs-lookup"><span data-stu-id="e8fe6-164">**Column names in the first data row**</span></span>  
 <span data-ttu-id="e8fe6-165">先頭データ行を列名として使用するか、ここに列名を指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="e8fe6-165">Indicate whether to expect or provide column names in the first data row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8fe6-166">参照</span><span class="sxs-lookup"><span data-stu-id="e8fe6-166">See Also</span></span>  
 <span data-ttu-id="e8fe6-167">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e8fe6-167">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e8fe6-168">[[複数フラットファイル接続マネージャーエディター &#40;列] ページ&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e8fe6-168">[Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e8fe6-169">[[複数フラットファイル接続マネージャーエディター &#40;[詳細設定] ページ&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="e8fe6-169">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="e8fe6-170">[[複数フラット ファイル接続マネージャー エディター] &#40;[プレビュー] ページ&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)</span><span class="sxs-lookup"><span data-stu-id="e8fe6-170">[Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)</span></span>  
  
  
