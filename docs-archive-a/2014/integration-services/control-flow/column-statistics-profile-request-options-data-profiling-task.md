---
title: '[列統計プロファイル要求] のオプション (データ プロファイル タスク) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 87205984-507a-49f3-b27c-36a0075c234d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce5c062a12e38d147f3cef95ea09b4c80f7c256
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640194"
---
# <a name="column-statistics-profile-request-options-data-profiling-task"></a><span data-ttu-id="4f515-102">[列統計プロファイル要求] のオプション (データ プロファイル タスク)</span><span class="sxs-lookup"><span data-stu-id="4f515-102">Column Statistics Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="4f515-103">**[プロファイル要求]** ページの **[要求プロパティ]** ペインを使用すると、要求ペインで選択した **[列統計プロファイル要求]** のオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="4f515-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Statistics Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="4f515-104">列統計プロファイルは、数値列の最小値、最大値、平均値、標準偏差、列の最小値、最大値などの統計を報告し `datetime` ます。</span><span class="sxs-lookup"><span data-stu-id="4f515-104">A Column Statistics profile reports statistics such as minimum, maximum, average, and standard deviation for numeric columns, and minimum and maximum for `datetime` columns.</span></span> <span data-ttu-id="4f515-105">このプロファイルを使用すると、無効な日付などのデータの問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="4f515-105">This profile can help you identify problems in your data such as invalid dates.</span></span> <span data-ttu-id="4f515-106">たとえば、履歴の日付の列をプロファイルし、将来の日付の最大値を検出できます。</span><span class="sxs-lookup"><span data-stu-id="4f515-106">For example, you profile a column of historical dates and discover a maximum date that is in the future.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f515-107">このトピックで説明するオプションは、 **[データ プロファイル タスク エディター]** の **[プロファイル要求]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f515-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="4f515-108">エディターのこのページの詳細については、「[Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md)」(データ プロファイル タスク エディター &#40;[プロファイル要求] ページ&#41;)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f515-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="4f515-109">データ プロファイル タスクの使用方法の詳細については、「 [データ プロファイル タスクのセットアップ](data-profiling-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f515-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="4f515-110">Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「 [Data Profile Viewer](data-profile-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f515-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="4f515-111">[要求プロパティ] のオプション</span><span class="sxs-lookup"><span data-stu-id="4f515-111">Request Properties Options</span></span>  
 <span data-ttu-id="4f515-112">**[要求プロパティ]** ペインに表示される **[列統計プロファイル要求]** のオプション グループは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4f515-112">For a **Column Statistics Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="4f515-113">**[データ]** ( **[TableOrView]** オプション、 **[Column]** オプションなど)</span><span class="sxs-lookup"><span data-stu-id="4f515-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="4f515-114">**全般**</span><span class="sxs-lookup"><span data-stu-id="4f515-114">**General**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="4f515-115">[データ] のオプション</span><span class="sxs-lookup"><span data-stu-id="4f515-115">Data Options</span></span>  
 <span data-ttu-id="4f515-116">**[ConnectionManager]**</span><span class="sxs-lookup"><span data-stu-id="4f515-116">**ConnectionManager**</span></span>  
 <span data-ttu-id="4f515-117">プロファイル対象のテーブルまたはビューを含む [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f515-117">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="4f515-118">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="4f515-118">**TableOrView**</span></span>  
 <span data-ttu-id="4f515-119">プロファイル対象の列を含む既存のテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f515-119">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="4f515-120">詳細については、このトピックの「[TableorView] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f515-120">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="4f515-121">**列**</span><span class="sxs-lookup"><span data-stu-id="4f515-121">**Column**</span></span>  
 <span data-ttu-id="4f515-122">プロファイル対象の既存の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f515-122">Select the existing column to be profiled.</span></span> <span data-ttu-id="4f515-123">すべての列をプロファイルするには、 **[(\*)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f515-123">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="4f515-124">詳細については、このトピックの「[列] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f515-124">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="4f515-125">[TableOrView] のオプション</span><span class="sxs-lookup"><span data-stu-id="4f515-125">TableOrView Options</span></span>  
 <span data-ttu-id="4f515-126">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="4f515-126">**Schema**</span></span>  
 <span data-ttu-id="4f515-127">選択したテーブルが属するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f515-127">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="4f515-128">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="4f515-128">This option is read-only.</span></span>  
  
 <span data-ttu-id="4f515-129">**Table**</span><span class="sxs-lookup"><span data-stu-id="4f515-129">**Table**</span></span>  
 <span data-ttu-id="4f515-130">選択したテーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="4f515-130">Displays the name of the selected table.</span></span> <span data-ttu-id="4f515-131">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="4f515-131">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="4f515-132">[列] のオプション</span><span class="sxs-lookup"><span data-stu-id="4f515-132">Column Options</span></span>  
 <span data-ttu-id="4f515-133">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="4f515-133">**IsWildCard**</span></span>  
 <span data-ttu-id="4f515-134">**[(\*)]** ワイルドカードが選択されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4f515-134">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="4f515-135">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは **[True]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4f515-135">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="4f515-136">個々の列をプロファイル対象として選択した場合、このオプションは **[False]** になります。</span><span class="sxs-lookup"><span data-stu-id="4f515-136">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="4f515-137">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="4f515-137">This option is read-only.</span></span>  
  
 <span data-ttu-id="4f515-138">**[ColumnName]**</span><span class="sxs-lookup"><span data-stu-id="4f515-138">**ColumnName**</span></span>  
 <span data-ttu-id="4f515-139">選択した列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="4f515-139">Displays the name of the selected column.</span></span> <span data-ttu-id="4f515-140">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="4f515-140">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="4f515-141">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="4f515-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="4f515-142">**[StringCompareOptions]**</span><span class="sxs-lookup"><span data-stu-id="4f515-142">**StringCompareOptions**</span></span>  
 <span data-ttu-id="4f515-143">このオプションは、列統計プロファイルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="4f515-143">This option does not apply to the Column Statistics Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="4f515-144">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="4f515-144">General Options</span></span>  
 <span data-ttu-id="4f515-145">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="4f515-145">**RequestID**</span></span>  
 <span data-ttu-id="4f515-146">このプロファイル要求を識別するわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4f515-146">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="4f515-147">通常、自動生成された値を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4f515-147">Typically, you do not have to change the autogenerated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f515-148">参照</span><span class="sxs-lookup"><span data-stu-id="4f515-148">See Also</span></span>  
 <span data-ttu-id="4f515-149">[データ プロファイル タスク エディター ([全般] ページ)](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="4f515-149">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="4f515-150">単一テーブル クイック プロファイル フォーム &#40;データ プロファイル タスク&#41;</span><span class="sxs-lookup"><span data-stu-id="4f515-150">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
