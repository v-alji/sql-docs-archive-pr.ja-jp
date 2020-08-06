---
title: '[列の NULL 比プロファイル要求] のオプション (データ プロファイル タスク) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e47c09a9a19eae4aed21c0c518430bc19a45648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640197"
---
# <a name="column-null-ratio-profile-request-options-data-profiling-task"></a><span data-ttu-id="c95da-102">[列の NULL 比プロファイル要求] のオプション (データ プロファイル タスク)</span><span class="sxs-lookup"><span data-stu-id="c95da-102">Column Null Ratio Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="c95da-103">**[プロファイル要求]** ページの **[要求プロパティ]** ペインを使用すると、要求ペインで選択した **[列の NULL 比要求]** のオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="c95da-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Null Ratio Request** selected in the requests pane.</span></span> <span data-ttu-id="c95da-104">列の NULL 比プロファイルは、選択した列の NULL 値の比率を報告します。</span><span class="sxs-lookup"><span data-stu-id="c95da-104">A Column Null Ratio profile reports the percentage of null values in the selected column.</span></span> <span data-ttu-id="c95da-105">このプロファイルを使用すると、列の NULL 値の比率が予想外に高いなどのデータの問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="c95da-105">This profile can help you identify problems in your data such as an unexpectedly high ratio of null values in a column.</span></span> <span data-ttu-id="c95da-106">たとえば、列の NULL 比プロファイルを使用して郵便番号列をプロファイルすると、許容範囲を超える欠落した郵便番号の比率を検出できます。</span><span class="sxs-lookup"><span data-stu-id="c95da-106">For example, a Column Null Ratio profile can profile a ZIP Code/Postal Code column and discover an unacceptably high percentage of missing postal codes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c95da-107">このトピックで説明するオプションは、 **[データ プロファイル タスク エディター]** の **[プロファイル要求]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c95da-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="c95da-108">エディターのこのページの詳細については、「[Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md)」(データ プロファイル タスク エディター &#40;[プロファイル要求] ページ&#41;)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c95da-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="c95da-109">データ プロファイル タスクの使用方法の詳細については、「 [データ プロファイル タスクのセットアップ](data-profiling-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c95da-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="c95da-110">Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「 [Data Profile Viewer](data-profile-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c95da-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="c95da-111">[要求プロパティ] のオプション</span><span class="sxs-lookup"><span data-stu-id="c95da-111">Request Properties Options</span></span>  
 <span data-ttu-id="c95da-112">**[要求プロパティ]** ペインに表示される **[列の NULL 比要求]** のオプション グループは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c95da-112">For a **Column Null Ratio Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="c95da-113">**[データ]** ( **[TableOrView]** オプション、 **[Column]** オプションなど)</span><span class="sxs-lookup"><span data-stu-id="c95da-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="c95da-114">**全般**</span><span class="sxs-lookup"><span data-stu-id="c95da-114">**General**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="c95da-115">[データ] のオプション</span><span class="sxs-lookup"><span data-stu-id="c95da-115">Data Options</span></span>  
 <span data-ttu-id="c95da-116">**[ConnectionManager]**</span><span class="sxs-lookup"><span data-stu-id="c95da-116">**ConnectionManager**</span></span>  
 <span data-ttu-id="c95da-117">プロファイル対象のテーブルまたはビューを含む [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="c95da-117">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="c95da-118">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="c95da-118">**TableOrView**</span></span>  
 <span data-ttu-id="c95da-119">プロファイル対象の列を含む既存のテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="c95da-119">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="c95da-120">詳細については、このトピックの「[TableorView] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c95da-120">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="c95da-121">**列**</span><span class="sxs-lookup"><span data-stu-id="c95da-121">**Column**</span></span>  
 <span data-ttu-id="c95da-122">プロファイル対象の既存の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c95da-122">Select the existing column to be profiled.</span></span> <span data-ttu-id="c95da-123">すべての列をプロファイルするには、 **[(\*)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c95da-123">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="c95da-124">詳細については、このトピックの「[列] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c95da-124">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="c95da-125">[TableOrView] のオプション</span><span class="sxs-lookup"><span data-stu-id="c95da-125">TableOrView Options</span></span>  
 <span data-ttu-id="c95da-126">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="c95da-126">**Schema**</span></span>  
 <span data-ttu-id="c95da-127">選択したテーブルが属するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="c95da-127">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="c95da-128">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c95da-128">This option is read-only.</span></span>  
  
 <span data-ttu-id="c95da-129">**Table**</span><span class="sxs-lookup"><span data-stu-id="c95da-129">**Table**</span></span>  
 <span data-ttu-id="c95da-130">選択したテーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c95da-130">Displays the name of the selected table.</span></span> <span data-ttu-id="c95da-131">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c95da-131">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="c95da-132">[列] のオプション</span><span class="sxs-lookup"><span data-stu-id="c95da-132">Column Options</span></span>  
 <span data-ttu-id="c95da-133">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="c95da-133">**IsWildCard**</span></span>  
 <span data-ttu-id="c95da-134">**[(\*)]** ワイルドカードが選択されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c95da-134">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="c95da-135">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは **[True]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c95da-135">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="c95da-136">個々の列をプロファイル対象として選択した場合、このオプションは **[False]** になります。</span><span class="sxs-lookup"><span data-stu-id="c95da-136">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="c95da-137">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c95da-137">This option is read-only.</span></span>  
  
 <span data-ttu-id="c95da-138">**[ColumnName]**</span><span class="sxs-lookup"><span data-stu-id="c95da-138">**ColumnName**</span></span>  
 <span data-ttu-id="c95da-139">選択した列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c95da-139">Displays the name of the selected column.</span></span> <span data-ttu-id="c95da-140">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="c95da-140">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="c95da-141">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c95da-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="c95da-142">**[StringCompareOptions]**</span><span class="sxs-lookup"><span data-stu-id="c95da-142">**StringCompareOptions**</span></span>  
 <span data-ttu-id="c95da-143">このオプションは、列の NULL 比プロファイルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="c95da-143">This option does not apply to the Column Null Ratio Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="c95da-144">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="c95da-144">General Options</span></span>  
 <span data-ttu-id="c95da-145">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="c95da-145">**RequestID**</span></span>  
 <span data-ttu-id="c95da-146">このプロファイル要求を識別するわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c95da-146">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="c95da-147">通常、自動生成された値を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c95da-147">Typically, you do not have to change the autogenerated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95da-148">参照</span><span class="sxs-lookup"><span data-stu-id="c95da-148">See Also</span></span>  
 <span data-ttu-id="c95da-149">[データ プロファイル タスク エディター ([全般] ページ)](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="c95da-149">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="c95da-150">単一テーブル クイック プロファイル フォーム &#40;データ プロファイル タスク&#41;</span><span class="sxs-lookup"><span data-stu-id="c95da-150">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
