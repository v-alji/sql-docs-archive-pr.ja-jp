---
title: '[列長分布プロファイル要求] のオプション (データ プロファイル タスク) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 1a4de41f-f38d-40ea-ba1b-6c0ef67ea52a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c0ebb6f1e0a6df2c0e47311f7b8217c5ce6f2df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640199"
---
# <a name="column-length-distribution-profile-request-options-data-profiling-task"></a><span data-ttu-id="8c0dc-102">[列長分布プロファイル要求] のオプション (データ プロファイル タスク)</span><span class="sxs-lookup"><span data-stu-id="8c0dc-102">Column Length Distribution Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="8c0dc-103">**[プロファイル要求]** ページの **[要求プロパティ]** ペインを使用すると、要求ペインで選択した **[列長分布プロファイル要求]** のオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Length Distribution Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="8c0dc-104">列長分布プロファイルは、選択された列に含まれる文字列値の長さごとに、その長さと、テーブル内におけるその長さの行の比率を報告します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-104">A Column Length Distribution profile reports all the distinct lengths of string values in the selected column and the percentage of rows in the table that each length represents.</span></span> <span data-ttu-id="8c0dc-105">このプロファイルを使用すると、無効な値などのデータの問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-105">This profile can help you identify problems in your data such as invalid values.</span></span> <span data-ttu-id="8c0dc-106">たとえば、2 文字の米国州コードの列をプロファイルし、3 文字以上の値を検出できます。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-106">For example, you profile a column of two-character United States state codes and discover values longer than two characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c0dc-107">このトピックで説明するオプションは、 **[データ プロファイル タスク エディター]** の **[プロファイル要求]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="8c0dc-108">エディターのこのページの詳細については、「[Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md)」(データ プロファイル タスク エディター &#40;[プロファイル要求] ページ&#41;)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="8c0dc-109">データ プロファイル タスクの使用方法の詳細については、「 [データ プロファイル タスクのセットアップ](data-profiling-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="8c0dc-110">Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「 [Data Profile Viewer](data-profile-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="8c0dc-111">[要求プロパティ] のオプション</span><span class="sxs-lookup"><span data-stu-id="8c0dc-111">Request Properties Options</span></span>  
 <span data-ttu-id="8c0dc-112">**[要求プロパティ]** ペインに表示される **[列長分布プロファイル要求]** のオプション グループは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-112">For a **Column Length Distribution Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="8c0dc-113">**[データ]** ( **[TableOrView]** オプション、 **[Column]** オプションなど)</span><span class="sxs-lookup"><span data-stu-id="8c0dc-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="8c0dc-114">**全般**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-114">**General**</span></span>  
  
-   <span data-ttu-id="8c0dc-115">**[オプション]**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-115">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="8c0dc-116">[データ] のオプション</span><span class="sxs-lookup"><span data-stu-id="8c0dc-116">Data Options</span></span>  
 <span data-ttu-id="8c0dc-117">**[ConnectionManager]**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-117">**ConnectionManager**</span></span>  
 <span data-ttu-id="8c0dc-118">プロファイル対象のテーブルまたはビューを含む [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-118">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="8c0dc-119">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-119">**TableOrView**</span></span>  
 <span data-ttu-id="8c0dc-120">プロファイル対象の列を含む既存のテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-120">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="8c0dc-121">詳細については、このトピックの「[TableorView] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-121">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="8c0dc-122">**列**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-122">**Column**</span></span>  
 <span data-ttu-id="8c0dc-123">プロファイル対象の既存の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-123">Select the existing column to be profiled.</span></span> <span data-ttu-id="8c0dc-124">すべての列をプロファイルするには、 **[(\*)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-124">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="8c0dc-125">詳細については、このトピックの「[列] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-125">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="8c0dc-126">[TableOrView] のオプション</span><span class="sxs-lookup"><span data-stu-id="8c0dc-126">TableOrView Options</span></span>  
 <span data-ttu-id="8c0dc-127">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-127">**Schema**</span></span>  
 <span data-ttu-id="8c0dc-128">選択したテーブルが属するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-128">Specify the schema to which the selected table belongs.</span></span> <span data-ttu-id="8c0dc-129">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-129">This option is read-only.</span></span>  
  
 <span data-ttu-id="8c0dc-130">**Table**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-130">**Table**</span></span>  
 <span data-ttu-id="8c0dc-131">選択したテーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-131">Displays the name of the selected table.</span></span> <span data-ttu-id="8c0dc-132">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-132">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="8c0dc-133">[列] のオプション</span><span class="sxs-lookup"><span data-stu-id="8c0dc-133">Column Options</span></span>  
 <span data-ttu-id="8c0dc-134">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-134">**IsWildCard**</span></span>  
 <span data-ttu-id="8c0dc-135">**[(\*)]** ワイルドカードが選択されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-135">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="8c0dc-136">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは **[True]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-136">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="8c0dc-137">個々の列をプロファイル対象として選択した場合、このオプションは **[False]** になります。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-137">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="8c0dc-138">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-138">This option is read-only.</span></span>  
  
 <span data-ttu-id="8c0dc-139">**[ColumnName]**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-139">**ColumnName**</span></span>  
 <span data-ttu-id="8c0dc-140">選択した列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-140">Displays the name of the selected column.</span></span> <span data-ttu-id="8c0dc-141">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-141">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="8c0dc-142">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-142">This option is read-only.</span></span>  
  
 <span data-ttu-id="8c0dc-143">**[StringCompareOptions]**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-143">**StringCompareOptions**</span></span>  
 <span data-ttu-id="8c0dc-144">このオプションは、列長分布プロファイルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-144">This option does not apply to the Column Length Distribution Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="8c0dc-145">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="8c0dc-145">General Options</span></span>  
 <span data-ttu-id="8c0dc-146">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-146">**RequestID**</span></span>  
 <span data-ttu-id="8c0dc-147">このプロファイル要求を識別するわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-147">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="8c0dc-148">通常、自動生成された値を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-148">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="8c0dc-149">オプション</span><span class="sxs-lookup"><span data-stu-id="8c0dc-149">Options</span></span>  
 <span data-ttu-id="8c0dc-150">**[IgnoreLeadingSpaces]**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-150">**IgnoreLeadingSpaces**</span></span>  
 <span data-ttu-id="8c0dc-151">プロファイルが文字列値を比較する際に、先頭の空白を無視するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-151">Indicate whether to ignore leading spaces when the profile compares string values.</span></span> <span data-ttu-id="8c0dc-152">このオプションの既定値は **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-152">The default value of this option is **False**.</span></span>  
  
 <span data-ttu-id="8c0dc-153">**[IgnoreTrailingSpaces]**</span><span class="sxs-lookup"><span data-stu-id="8c0dc-153">**IgnoreTrailingSpaces**</span></span>  
 <span data-ttu-id="8c0dc-154">プロファイルが文字列値を比較する際に、末尾の空白を無視するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-154">Indicate whether to ignore trailing spaces when the profile compares string values.</span></span> <span data-ttu-id="8c0dc-155">このオプションの既定値は **[true]** です。</span><span class="sxs-lookup"><span data-stu-id="8c0dc-155">The default value of this option is **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0dc-156">参照</span><span class="sxs-lookup"><span data-stu-id="8c0dc-156">See Also</span></span>  
 <span data-ttu-id="8c0dc-157">[データ プロファイル タスク エディター ([全般] ページ)](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="8c0dc-157">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="8c0dc-158">単一テーブル クイック プロファイル フォーム &#40;データ プロファイル タスク&#41;</span><span class="sxs-lookup"><span data-stu-id="8c0dc-158">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
