---
title: フラットファイルへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connflatfile.f1
ms.assetid: a365991e-eded-4cd8-89c0-0daf6d658d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6bee3c8f7f4b255e6985e8d783365bc8a47599e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633482"
---
# <a name="connect-to-a-flat-file-ssas"></a><span data-ttu-id="15289-102">[フラット ファイルへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="15289-102">Connect to a Flat File (SSAS)</span></span>
  <span data-ttu-id="15289-103">**テーブルのインポート ウィザード** のこのページを使用すると、フラット ファイル (.txt)、タブ区切りファイル (.tab)、またはコンマ区切りファイル (.csv) に接続できます。</span><span class="sxs-lookup"><span data-stu-id="15289-103">This page of the **Table Import Wizard** enables you to connect to a flat file (.txt), tab-separated file (.tab), or a comma-separated file (.csv).</span></span> <span data-ttu-id="15289-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15289-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="15289-105">フラット ファイルに接続するには、ACE プロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="15289-105">To connect to a flat file, you must have the ACE provider installed on your computer.</span></span> <span data-ttu-id="15289-106">詳細については、「[サポートされているデータ ソース &#40;SSAS テーブル&#41;](tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15289-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15289-107">このページでファイルを選択する際には、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="15289-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="15289-108">ただし、[権限借用情報] ページで指定されたユーザーに、選択したファイルの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="15289-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="15289-109">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="15289-109">UI element list</span></span>  
 <span data-ttu-id="15289-110">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="15289-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="15289-111">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="15289-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="15289-112">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="15289-112">This is a required field.</span></span>  
  
 <span data-ttu-id="15289-113">**ファイル パス**</span><span class="sxs-lookup"><span data-stu-id="15289-113">**File Path**</span></span>  
 <span data-ttu-id="15289-114">ファイルの完全なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15289-114">Specify a full path for the file.</span></span>  
  
 <span data-ttu-id="15289-115">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="15289-115">**Browse**</span></span>  
 <span data-ttu-id="15289-116">使用可能なファイルがある場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="15289-116">Navigate to a location where a file is available.</span></span>  
  
 <span data-ttu-id="15289-117">**列区切り記号**</span><span class="sxs-lookup"><span data-stu-id="15289-117">**Column Separator**</span></span>  
 <span data-ttu-id="15289-118">使用できる列区切り記号の一覧から、列区切り記号を選択します。</span><span class="sxs-lookup"><span data-stu-id="15289-118">Select from a list of available column separators.</span></span> <span data-ttu-id="15289-119">テキストに出現しないと思われる区切り記号を選択してください。</span><span class="sxs-lookup"><span data-stu-id="15289-119">Choose a separator that is not likely to occur in the text.</span></span>  
  
|<span data-ttu-id="15289-120">値</span><span class="sxs-lookup"><span data-stu-id="15289-120">Value</span></span>|<span data-ttu-id="15289-121">説明</span><span class="sxs-lookup"><span data-stu-id="15289-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15289-122">タブ (t)</span><span class="sxs-lookup"><span data-stu-id="15289-122">Tab (t)</span></span>|<span data-ttu-id="15289-123">列はタブ文字で区切られます。</span><span class="sxs-lookup"><span data-stu-id="15289-123">Columns are separated by a tab (t).</span></span>|  
|<span data-ttu-id="15289-124">コンマ (,)</span><span class="sxs-lookup"><span data-stu-id="15289-124">Comma (,)</span></span>|<span data-ttu-id="15289-125">列はコンマ (,) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="15289-125">Columns are separated by a comma (,).</span></span>|  
|<span data-ttu-id="15289-126">セミコロン (;)</span><span class="sxs-lookup"><span data-stu-id="15289-126">Semicolon (;)</span></span>|<span data-ttu-id="15289-127">列はセミコロン (;) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="15289-127">Columns are separated by a semicolon (;).</span></span>|  
|<span data-ttu-id="15289-128">スペース ( )</span><span class="sxs-lookup"><span data-stu-id="15289-128">Space ( )</span></span>|<span data-ttu-id="15289-129">列はスペース ( ) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="15289-129">Columns are separated by a space ( ).</span></span>|  
|<span data-ttu-id="15289-130">コロン (:)</span><span class="sxs-lookup"><span data-stu-id="15289-130">Colon (:)</span></span>|<span data-ttu-id="15289-131">列はコロン (:) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="15289-131">Columns are separated by a colon (:).</span></span>|  
|<span data-ttu-id="15289-132">縦棒 (&#124;)</span><span class="sxs-lookup"><span data-stu-id="15289-132">Vertical Bar (&#124;)</span></span>|<span data-ttu-id="15289-133">列は縦棒 (&#124;) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="15289-133">Columns are separated by a vertical bar (&#124;).</span></span>|  
  
 <span data-ttu-id="15289-134">**詳細**</span><span class="sxs-lookup"><span data-stu-id="15289-134">**Advanced**</span></span>  
 <span data-ttu-id="15289-135">フラット ファイルのエンコーディング オプションとロケール オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="15289-135">Specify the encoding and locale options for the flat file.</span></span>  
  
 <span data-ttu-id="15289-136">**[先頭の行を列見出しとして使用する]**</span><span class="sxs-lookup"><span data-stu-id="15289-136">**Use first row as column headers**</span></span>  
 <span data-ttu-id="15289-137">先頭のデータ行を目的のテーブルの列見出しとして使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="15289-137">Specify whether to use the first data row as the column headers of the destination table.</span></span>  
  
 <span data-ttu-id="15289-138">**データのプレビュー**</span><span class="sxs-lookup"><span data-stu-id="15289-138">**Data preview**</span></span>  
 <span data-ttu-id="15289-139">選択されたファイルのデータをプレビューし、以下のオプションを使用してデータ インポートを変更します。</span><span class="sxs-lookup"><span data-stu-id="15289-139">Preview the data in the selected file, and use the following options to modify the data import.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15289-140">このプレビューには、ファイル内の最初の 50 行のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="15289-140">Only the first 50 rows in the file are displayed in this preview.</span></span>  
  
|<span data-ttu-id="15289-141">オプション</span><span class="sxs-lookup"><span data-stu-id="15289-141">Option</span></span>|<span data-ttu-id="15289-142">説明</span><span class="sxs-lookup"><span data-stu-id="15289-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="15289-143">**列ヘッダーのチェック ボックス**</span><span class="sxs-lookup"><span data-stu-id="15289-143">**Checkbox in the column header**</span></span>|<span data-ttu-id="15289-144">列をデータ インポートの対象にする場合は、チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="15289-144">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="15289-145">列をデータ インポートの対象から除外する場合は、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="15289-145">Clear the checkbox to remove the column from the data import.</span></span>|  
|<span data-ttu-id="15289-146">**列ヘッダーの下矢印ボタン**</span><span class="sxs-lookup"><span data-stu-id="15289-146">**Down-arrow button in the column header**</span></span>|<span data-ttu-id="15289-147">列内のデータを並べ替えてフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="15289-147">Sort and filter data in the column.</span></span>|  
  
 <span data-ttu-id="15289-148">**[行フィルターのクリア]**</span><span class="sxs-lookup"><span data-stu-id="15289-148">**Clear Row Filters**</span></span>  
 <span data-ttu-id="15289-149">列のデータに適用されているすべてのフィルターを削除します。</span><span class="sxs-lookup"><span data-stu-id="15289-149">Remove all filters that were applied to the data in the columns.</span></span>  
  
  
