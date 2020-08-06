---
title: '[フラットファイル接続マネージャーエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.general.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 77296024-5c1a-4f6a-9665-0b50d45d744c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 478c7bcf56e300b47af93862bf66409a3c94b5f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632613"
---
# <a name="flat-file-connection-manager-editor-general-page"></a><span data-ttu-id="71469-102">[フラット ファイル接続マネージャー エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="71469-102">Flat File Connection Manager Editor (General Page)</span></span>
  <span data-ttu-id="71469-103">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、ファイルおよびデータ形式を選択できます。</span><span class="sxs-lookup"><span data-stu-id="71469-103">Use the **General** page of the **Flat File Connection Manager Editor** dialog box to select a file and data format.</span></span> <span data-ttu-id="71469-104">フラット ファイル接続により、パッケージをテキスト ファイルに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="71469-104">A flat file connection enables a package to connect to a text file.</span></span>  
  
 <span data-ttu-id="71469-105">フラット ファイル接続マネージャーの詳細については、「 [Flat File Connection Manager](connection-manager/file-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71469-105">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="71469-106">Options</span><span class="sxs-lookup"><span data-stu-id="71469-106">Options</span></span>  
 <span data-ttu-id="71469-107">**接続マネージャー名**</span><span class="sxs-lookup"><span data-stu-id="71469-107">**Connection manager name**</span></span>  
 <span data-ttu-id="71469-108">ワークフローにおけるフラット ファイル接続の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="71469-108">Provide a unique name for the flat file connection in the workflow.</span></span> <span data-ttu-id="71469-109">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="71469-109">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="71469-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="71469-110">**Description**</span></span>  
 <span data-ttu-id="71469-111">接続の説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="71469-111">Describe the connection.</span></span> <span data-ttu-id="71469-112">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="71469-112">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="71469-113">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="71469-113">**File name**</span></span>  
 <span data-ttu-id="71469-114">フラット ファイル接続で使用するパスおよびファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="71469-114">Type the path and file name to use in the flat file connection.</span></span>  
  
 <span data-ttu-id="71469-115">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="71469-115">**Browse**</span></span>  
 <span data-ttu-id="71469-116">フラット ファイル接続で使用するファイル名を探します。</span><span class="sxs-lookup"><span data-stu-id="71469-116">Locate the file name to use in the flat file connection.</span></span>  
  
 <span data-ttu-id="71469-117">**ロケール**</span><span class="sxs-lookup"><span data-stu-id="71469-117">**Locale**</span></span>  
 <span data-ttu-id="71469-118">ロケールを指定して、順序付けおよび日時の形式に関する言語固有の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="71469-118">Specify the locale to provide language-specific information for ordering and for date and time formats.</span></span>  
  
 <span data-ttu-id="71469-119">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="71469-119">**Unicode**</span></span>  
 <span data-ttu-id="71469-120">Unicode を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="71469-120">Indicate whether to use Unicode.</span></span> <span data-ttu-id="71469-121">Unicode を使用する場合は、コード ページを指定できません。</span><span class="sxs-lookup"><span data-stu-id="71469-121">If you use Unicode, you cannot specify a code page.</span></span>  
  
 <span data-ttu-id="71469-122">**コード ページ**</span><span class="sxs-lookup"><span data-stu-id="71469-122">**Code page**</span></span>  
 <span data-ttu-id="71469-123">非 Unicode テキストのコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="71469-123">Specify the code page for non-Unicode text.</span></span>  
  
 <span data-ttu-id="71469-124">**形式**</span><span class="sxs-lookup"><span data-stu-id="71469-124">**Format**</span></span>  
 <span data-ttu-id="71469-125">区切り記号形式、固定幅形式、または幅合わせしない形式をファイルで使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="71469-125">Indicate whether the file uses delimited, fixed width, or ragged right formatting.</span></span>  
  
|<span data-ttu-id="71469-126">値</span><span class="sxs-lookup"><span data-stu-id="71469-126">Value</span></span>|<span data-ttu-id="71469-127">説明</span><span class="sxs-lookup"><span data-stu-id="71469-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71469-128">区切り記号</span><span class="sxs-lookup"><span data-stu-id="71469-128">Delimited</span></span>|<span data-ttu-id="71469-129">列は、 **[列]** ページで指定した区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-129">Columns are separated by delimiters, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="71469-130">固定幅ファイル</span><span class="sxs-lookup"><span data-stu-id="71469-130">Fixed width</span></span>|<span data-ttu-id="71469-131">列は固定幅を持ちます。</span><span class="sxs-lookup"><span data-stu-id="71469-131">Columns have a fixed width.</span></span>|  
|<span data-ttu-id="71469-132">[幅合わせしない]</span><span class="sxs-lookup"><span data-stu-id="71469-132">Ragged right</span></span>|<span data-ttu-id="71469-133">幅合わせしない形式のファイルとは、最後の列を除くすべての列が固定幅のファイルです。</span><span class="sxs-lookup"><span data-stu-id="71469-133">Ragged right files are files in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="71469-134">最後の列は、行区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-134">It is delimited by the row delimiter.</span></span>|  
  
 <span data-ttu-id="71469-135">**テキスト修飾子**</span><span class="sxs-lookup"><span data-stu-id="71469-135">**Text qualifier**</span></span>  
 <span data-ttu-id="71469-136">使用するテキスト修飾子を指定します。</span><span class="sxs-lookup"><span data-stu-id="71469-136">Specify the text qualifier to use.</span></span> <span data-ttu-id="71469-137">たとえば、テキスト フィールドを引用符で囲むことを指定できます。</span><span class="sxs-lookup"><span data-stu-id="71469-137">For example, you can specify that text fields are enclosed in quotation marks.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71469-138">テキスト修飾子を選択した後で、 **[なし]** オプションを再度選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="71469-138">After you select a text qualifier, you cannot re-select the **None** option.</span></span> <span data-ttu-id="71469-139">テキスト修飾子の選択を解除するには、「 **なし** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="71469-139">Type **None** to de-select the text qualifier.</span></span>  
  
 <span data-ttu-id="71469-140">**[ヘッダー行区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="71469-140">**Header row delimiter**</span></span>  
 <span data-ttu-id="71469-141">ヘッダー行の区切り記号の一覧から選択するか、区切り記号テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="71469-141">Select from the list of delimiters for header rows, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="71469-142">値</span><span class="sxs-lookup"><span data-stu-id="71469-142">Value</span></span>|<span data-ttu-id="71469-143">説明</span><span class="sxs-lookup"><span data-stu-id="71469-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71469-144">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="71469-144">**{CR}{LF}**</span></span>|<span data-ttu-id="71469-145">ヘッダー行は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-145">The header row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="71469-146">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="71469-146">**{CR}**</span></span>|<span data-ttu-id="71469-147">ヘッダー行は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-147">The header row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="71469-148">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="71469-148">**{LF}**</span></span>|<span data-ttu-id="71469-149">ヘッダー行は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-149">The header row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="71469-150">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="71469-150">**Semicolon {;}**</span></span>|<span data-ttu-id="71469-151">ヘッダー行は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-151">The header row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="71469-152">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="71469-152">**Colon {:}**</span></span>|<span data-ttu-id="71469-153">ヘッダー行は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-153">The header row is delimited by a colon.</span></span>|  
|<span data-ttu-id="71469-154">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="71469-154">**Comma {,}**</span></span>|<span data-ttu-id="71469-155">ヘッダー行は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-155">The header row is delimited by a comma.</span></span>|  
|<span data-ttu-id="71469-156">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="71469-156">**Tab {t}**</span></span>|<span data-ttu-id="71469-157">ヘッダー行は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-157">The header row is delimited by a tab.</span></span>|  
|<span data-ttu-id="71469-158">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="71469-158">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="71469-159">ヘッダー行は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="71469-159">The header row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="71469-160">**[スキップするヘッダー行数]**</span><span class="sxs-lookup"><span data-stu-id="71469-160">**Header rows to skip**</span></span>  
 <span data-ttu-id="71469-161">必要に応じて、スキップするヘッダー行数または初期データ行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="71469-161">Specify the number of header rows or initial data rows to skip, if any.</span></span>  
  
 <span data-ttu-id="71469-162">**[先頭データ行を列名として使用する]**</span><span class="sxs-lookup"><span data-stu-id="71469-162">**Column names in the first data row**</span></span>  
 <span data-ttu-id="71469-163">先頭データ行を列名として使用するか、ここに列名を指定するかを示します。</span><span class="sxs-lookup"><span data-stu-id="71469-163">Indicate whether to expect or provide column names in the first data row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71469-164">参照</span><span class="sxs-lookup"><span data-stu-id="71469-164">See Also</span></span>  
 <span data-ttu-id="71469-165">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="71469-165">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="71469-166">[[フラットファイル接続マネージャーエディター &#40;列] ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="71469-166">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="71469-167">[[フラットファイル接続マネージャーエディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="71469-167">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="71469-168">[[フラット ファイル接続マネージャー エディター] ([プレビュー] ページ)](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)</span><span class="sxs-lookup"><span data-stu-id="71469-168">[Flat File Connection Manager Editor &#40;Preview Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)</span></span>  
  
  
