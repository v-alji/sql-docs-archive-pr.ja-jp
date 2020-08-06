---
title: '[列の値分布プロファイル要求] のオプション (データ プロファイル タスク) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: c1e5f5de-04f5-4d00-a9f0-55817186bdf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bba231bf46600d9608e1a55ad3a084534fec75e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640186"
---
# <a name="column-value-distribution-profile-request-options-data-profiling-task"></a><span data-ttu-id="60c77-102">[列の値分布プロファイル要求] のオプション (データ プロファイル タスク)</span><span class="sxs-lookup"><span data-stu-id="60c77-102">Column Value Distribution Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="60c77-103">**[プロファイル要求]** ページの **[要求プロパティ]** ペインを使用すると、要求ペインで選択した **[列の値分布プロファイル要求]** のオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="60c77-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Value Distribution Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="60c77-104">列の値分布プロファイルは、選択された列に含まれるすべての異なる値と、それぞれの値が表す行のテーブル内での比率を報告します。</span><span class="sxs-lookup"><span data-stu-id="60c77-104">A Column Value Distribution profile reports all the distinct values in the selected column and the percentage of rows in the table that each value represents.</span></span> <span data-ttu-id="60c77-105">また、テーブル内の指定された比率を超えている行の値も報告できます。</span><span class="sxs-lookup"><span data-stu-id="60c77-105">The profile can also report values that represent more than a specified percentage of rows in the table.</span></span> <span data-ttu-id="60c77-106">このプロファイルを使用すると、列に含まれる個別の値の数が正しくないなどのデータの問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="60c77-106">This profile can help you identify problems in your data such as an incorrect number of distinct values in a column.</span></span> <span data-ttu-id="60c77-107">たとえば、米国の州の列をプロファイルし、50 個を超える個別の値を検出できます。</span><span class="sxs-lookup"><span data-stu-id="60c77-107">For example, you profile a United States state column and discover more than 50 distinct values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60c77-108">このトピックで説明するオプションは、 **[データ プロファイル タスク エディター]** の **[プロファイル要求]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="60c77-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="60c77-109">エディターのこのページの詳細については、「[Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md)」(データ プロファイル タスク エディター &#40;[プロファイル要求] ページ&#41;)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c77-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="60c77-110">データ プロファイル タスクの使用方法の詳細については、「 [データ プロファイル タスクのセットアップ](data-profiling-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c77-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="60c77-111">Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「 [Data Profile Viewer](data-profile-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c77-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="60c77-112">[要求プロパティ] のオプション</span><span class="sxs-lookup"><span data-stu-id="60c77-112">Request Properties Options</span></span>  
 <span data-ttu-id="60c77-113">**[要求プロパティ]** ペインに表示される **[列の値分布プロファイル要求]** のオプション グループは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="60c77-113">For a **Column Value Distribution Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="60c77-114">**[データ]** ( **[TableOrView]** オプション、 **[Column]** オプションなど)</span><span class="sxs-lookup"><span data-stu-id="60c77-114">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="60c77-115">**全般**</span><span class="sxs-lookup"><span data-stu-id="60c77-115">**General**</span></span>  
  
-   <span data-ttu-id="60c77-116">**[オプション]**</span><span class="sxs-lookup"><span data-stu-id="60c77-116">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="60c77-117">[データ] のオプション</span><span class="sxs-lookup"><span data-stu-id="60c77-117">Data Options</span></span>  
 <span data-ttu-id="60c77-118">**[ConnectionManager]**</span><span class="sxs-lookup"><span data-stu-id="60c77-118">**ConnectionManager**</span></span>  
 <span data-ttu-id="60c77-119">プロファイル対象のテーブルまたはビューを含む [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="60c77-119">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="60c77-120">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="60c77-120">**TableOrView**</span></span>  
 <span data-ttu-id="60c77-121">プロファイル対象の列を含む既存のテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="60c77-121">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="60c77-122">詳細については、このトピックの「[TableorView] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c77-122">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="60c77-123">**列**</span><span class="sxs-lookup"><span data-stu-id="60c77-123">**Column**</span></span>  
 <span data-ttu-id="60c77-124">プロファイル対象の既存の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="60c77-124">Select the existing column to be profiled.</span></span> <span data-ttu-id="60c77-125">すべての列をプロファイルするには、 **[(\*)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60c77-125">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="60c77-126">詳細については、このトピックの「[列] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c77-126">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="60c77-127">[TableOrView] のオプション</span><span class="sxs-lookup"><span data-stu-id="60c77-127">TableOrView Options</span></span>  
 <span data-ttu-id="60c77-128">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="60c77-128">**Schema**</span></span>  
 <span data-ttu-id="60c77-129">選択したテーブルが属するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="60c77-129">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="60c77-130">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="60c77-130">This option is read-only.</span></span>  
  
 <span data-ttu-id="60c77-131">**Table**</span><span class="sxs-lookup"><span data-stu-id="60c77-131">**Table**</span></span>  
 <span data-ttu-id="60c77-132">選択したテーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="60c77-132">Displays the name of the selected table.</span></span> <span data-ttu-id="60c77-133">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="60c77-133">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="60c77-134">[列] のオプション</span><span class="sxs-lookup"><span data-stu-id="60c77-134">Column Options</span></span>  
 <span data-ttu-id="60c77-135">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="60c77-135">**IsWildCard**</span></span>  
 <span data-ttu-id="60c77-136">**[(\*)]** ワイルドカードが選択されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="60c77-136">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="60c77-137">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは **[True]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="60c77-137">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="60c77-138">個々の列をプロファイル対象として選択した場合、このオプションは **[False]** になります。</span><span class="sxs-lookup"><span data-stu-id="60c77-138">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="60c77-139">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="60c77-139">This option is read-only.</span></span>  
  
 <span data-ttu-id="60c77-140">**[ColumnName]**</span><span class="sxs-lookup"><span data-stu-id="60c77-140">**ColumnName**</span></span>  
 <span data-ttu-id="60c77-141">選択した列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="60c77-141">Displays the name of the selected column.</span></span> <span data-ttu-id="60c77-142">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="60c77-142">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="60c77-143">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="60c77-143">This option is read-only.</span></span>  
  
 <span data-ttu-id="60c77-144">**[StringCompareOptions]**</span><span class="sxs-lookup"><span data-stu-id="60c77-144">**StringCompareOptions**</span></span>  
 <span data-ttu-id="60c77-145">文字列値を比較するためのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="60c77-145">Select options for comparing string values.</span></span> <span data-ttu-id="60c77-146">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="60c77-146">This property has the options listed in the following table.</span></span> <span data-ttu-id="60c77-147">このオプションの既定値は **[Default]** です。</span><span class="sxs-lookup"><span data-stu-id="60c77-147">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60c77-148">**[ColumnName]** に **[(\*)]** ワイルドカードを使用する場合、**[CompareOptions]** は読み取り専用で、**[Default]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="60c77-148">If the **(\*)** wildcard is used for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="60c77-149">値</span><span class="sxs-lookup"><span data-stu-id="60c77-149">Value</span></span>|<span data-ttu-id="60c77-150">説明</span><span class="sxs-lookup"><span data-stu-id="60c77-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="60c77-151">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="60c77-151">**Default**</span></span>|<span data-ttu-id="60c77-152">ソース テーブル内の列の照合順序に基づいてデータを並べ替えて比較します。</span><span class="sxs-lookup"><span data-stu-id="60c77-152">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="60c77-153">**[BinarySort]**</span><span class="sxs-lookup"><span data-stu-id="60c77-153">**BinarySort**</span></span>|<span data-ttu-id="60c77-154">文字ごとに定義されているビット パターンに基づいてデータを並べ替えて比較します。</span><span class="sxs-lookup"><span data-stu-id="60c77-154">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="60c77-155">バイナリ並べ替え順では、大文字と小文字が区別され、アクセントが区別されます。</span><span class="sxs-lookup"><span data-stu-id="60c77-155">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="60c77-156">また、バイナリは最速の並べ替え順です。</span><span class="sxs-lookup"><span data-stu-id="60c77-156">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="60c77-157">**[DictionarySort]**</span><span class="sxs-lookup"><span data-stu-id="60c77-157">**DictionarySort**</span></span>|<span data-ttu-id="60c77-158">関連する言語またはアルファベットの辞書で定義されている並べ替えおよび比較ルールに基づいてデータを並べ替えて比較します。</span><span class="sxs-lookup"><span data-stu-id="60c77-158">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="60c77-159">**[DictionarySort]** を選択した場合は、次の表に示すオプションの任意の組み合わせも選択できます。</span><span class="sxs-lookup"><span data-stu-id="60c77-159">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="60c77-160">既定では、これらの追加オプションは選択されていません。</span><span class="sxs-lookup"><span data-stu-id="60c77-160">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="60c77-161">値</span><span class="sxs-lookup"><span data-stu-id="60c77-161">Value</span></span>|<span data-ttu-id="60c77-162">説明</span><span class="sxs-lookup"><span data-stu-id="60c77-162">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="60c77-163">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="60c77-163">**IgnoreCase**</span></span>|<span data-ttu-id="60c77-164">比較時に、大文字と小文字を区別するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="60c77-164">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="60c77-165">このオプションを設定した場合、文字列比較で大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="60c77-165">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="60c77-166">たとえば、"ABC" は "abc" と同一になります。</span><span class="sxs-lookup"><span data-stu-id="60c77-166">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="60c77-167">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="60c77-167">**IgnoreNonSpace**</span></span>|<span data-ttu-id="60c77-168">比較で、通常の文字と分音文字付きの文字を区別するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="60c77-168">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="60c77-169">このオプションを設定した場合、比較で分音文字は無視されます。</span><span class="sxs-lookup"><span data-stu-id="60c77-169">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="60c77-170">たとえば、"&#xE5;" は "a" と同じ文字になります。</span><span class="sxs-lookup"><span data-stu-id="60c77-170">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="60c77-171">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="60c77-171">**IgnoreKanaType**</span></span>|<span data-ttu-id="60c77-172">日本語の比較で、2 種類のかな文字である、ひらがなとカタカナを区別するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="60c77-172">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="60c77-173">このオプションを設定した場合、文字列比較でひらがなとカタカナは区別されません。</span><span class="sxs-lookup"><span data-stu-id="60c77-173">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="60c77-174">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="60c77-174">**IgnoreWidth**</span></span>|<span data-ttu-id="60c77-175">比較で、1 バイト文字と、それと同じ文字を表記した 2 バイト文字を区別するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="60c77-175">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="60c77-176">このオプションを設定した場合、文字列比較で 1 バイト表記と 2 バイト表記は同一文字として扱われます。</span><span class="sxs-lookup"><span data-stu-id="60c77-176">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="60c77-177">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="60c77-177">General Options</span></span>  
 <span data-ttu-id="60c77-178">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="60c77-178">**RequestID**</span></span>  
 <span data-ttu-id="60c77-179">このプロファイル要求を識別するわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="60c77-179">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="60c77-180">通常、自動生成された値を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="60c77-180">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="60c77-181">オプション</span><span class="sxs-lookup"><span data-stu-id="60c77-181">Options</span></span>  
 <span data-ttu-id="60c77-182">**[ValueDistributionOption]**</span><span class="sxs-lookup"><span data-stu-id="60c77-182">**ValueDistributionOption**</span></span>  
 <span data-ttu-id="60c77-183">すべての列の値の分布を計算するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="60c77-183">Specify whether to compute the distribution for all column values.</span></span> <span data-ttu-id="60c77-184">このオプションの既定値は **[FrequentValues]** です。</span><span class="sxs-lookup"><span data-stu-id="60c77-184">The default value of this option is **FrequentValues**.</span></span>  
  
|<span data-ttu-id="60c77-185">値</span><span class="sxs-lookup"><span data-stu-id="60c77-185">Value</span></span>|<span data-ttu-id="60c77-186">説明</span><span class="sxs-lookup"><span data-stu-id="60c77-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="60c77-187">**[AllValues]**</span><span class="sxs-lookup"><span data-stu-id="60c77-187">**AllValues**</span></span>|<span data-ttu-id="60c77-188">すべての列の値の分布が計算されます。</span><span class="sxs-lookup"><span data-stu-id="60c77-188">The distribution is computed for all column values.</span></span>|  
|<span data-ttu-id="60c77-189">**[FrequentValues]**</span><span class="sxs-lookup"><span data-stu-id="60c77-189">**FrequentValues**</span></span>|<span data-ttu-id="60c77-190">**[FrequentValueThreshold]** で指定した最小値を頻繁に超える値の分布のみが計算されます。</span><span class="sxs-lookup"><span data-stu-id="60c77-190">The distribution is computed only for values whose frequency exceeds the minimum value specified in **FrequentValueThreshold**.</span></span> <span data-ttu-id="60c77-191">**[FrequentValueThreshold]** を満たさない値は出力レポートから除外されます。</span><span class="sxs-lookup"><span data-stu-id="60c77-191">Values that do not meet the **FrequentValueThreshold** are excluded from the output report.</span></span>|  
  
 <span data-ttu-id="60c77-192">**[FrequentValueThreshold]**</span><span class="sxs-lookup"><span data-stu-id="60c77-192">**FrequentValueThreshold**</span></span>  
 <span data-ttu-id="60c77-193">0 ～ 1 の値を使用して、列の値が報告されるしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="60c77-193">Specify the threshold (by using a value between 0 and 1) above which the column value should be reported.</span></span> <span data-ttu-id="60c77-194">**[ValueDistributionOption]** で **[AllValues]** を選択した場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="60c77-194">This option is disabled when you select **AllValues** as the **ValueDistributionOption**.</span></span> <span data-ttu-id="60c77-195">このオプションの既定値は 0.001 です。</span><span class="sxs-lookup"><span data-stu-id="60c77-195">The default value of this option is 0.001.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c77-196">参照</span><span class="sxs-lookup"><span data-stu-id="60c77-196">See Also</span></span>  
 <span data-ttu-id="60c77-197">[データ プロファイル タスク エディター ([全般] ページ)](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="60c77-197">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="60c77-198">単一テーブル クイック プロファイル フォーム &#40;データ プロファイル タスク&#41;</span><span class="sxs-lookup"><span data-stu-id="60c77-198">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
