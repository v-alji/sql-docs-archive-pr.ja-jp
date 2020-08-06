---
title: '[候補キー プロファイル要求] のオプション (データ プロファイル タスク) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 8632dbc4-4394-4dc7-b19c-f9adeb21ba52
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86d7135059a315ad6504beb8e7a9408ef20e4fcc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633261"
---
# <a name="candidate-key-profile-request-options-data-profiling-task"></a><span data-ttu-id="55ca6-102">[候補キー プロファイル要求] のオプション (データ プロファイル タスク)</span><span class="sxs-lookup"><span data-stu-id="55ca6-102">Candidate Key Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="55ca6-103">**[プロファイル要求]** ページの **[要求プロパティ]** ペインを使用すると、要求ペインで選択した **[候補キー プロファイル要求]** のオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Candidate Key Profile Request** that is selected in the requests pane.</span></span> <span data-ttu-id="55ca6-104">候補キー プロファイルは、列または列のセットが、選択したテーブルのキーまたは近似キーであるかどうかを報告します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-104">A Candidate Key profile reports whether a column or set of columns is a key, or an approximate key, for the selected table.</span></span> <span data-ttu-id="55ca6-105">また、このプロファイルを使用すると、キーとなる可能性がある列の重複値などのデータの問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-105">This profile can also help you identify problems in your data such as duplicate values in a potential key column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55ca6-106">このトピックで説明するオプションは、 **[データ プロファイル タスク エディター]** の **[プロファイル要求]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-106">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="55ca6-107">エディターのこのページの詳細については、「[Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md)」(データ プロファイル タスク エディター &#40;[プロファイル要求] ページ&#41;)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca6-107">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="55ca6-108">データ プロファイル タスクの使用方法の詳細については、「 [データ プロファイル タスクのセットアップ](data-profiling-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca6-108">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="55ca6-109">Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「 [Data Profile Viewer](data-profile-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca6-109">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-selection-of-columns-for-the-keycolumns-property"></a><span data-ttu-id="55ca6-110">KeyColumns プロパティの列の選択について</span><span class="sxs-lookup"><span data-stu-id="55ca6-110">Understanding the Selection of Columns for the KeyColumns Property</span></span>  
 <span data-ttu-id="55ca6-111">各 **候補キー プロファイル要求** は、1 つまたは複数の列で構成される単一のキー候補のキーの強さを計算します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-111">Each **Candidate Key Profile Request** computes the key strength of a single key candidate that consists of a single column or of multiple columns:</span></span>  
  
-   <span data-ttu-id="55ca6-112">**[KeyColumns]** で列を 1 つだけ選択すると、その列のキーの強さが計算されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-112">When you select only one column in **KeyColumns**, the task computes the key strength of that one column.</span></span>  
  
-   <span data-ttu-id="55ca6-113">**[KeyColumns]** で複数の列を選択すると、選択したすべての列で構成される複合キーのキーの強さが計算されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-113">When you select multiple columns in **KeyColumns**, the task computes the key strength of the composite key that consists of all the selected columns.</span></span>  
  
-   <span data-ttu-id="55ca6-114">**[KeyColumns]** でワイルドカード文字 **[(\*)]** を選択すると、テーブルまたはビューの各列のキーの強さが計算されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-114">When you select the wildcard character, **(\*)**, in **KeyColumns**, the task computers the key strength of each column in the table or view.</span></span>  
  
 <span data-ttu-id="55ca6-115">たとえば、A 列、B 列、および C 列を含むサンプル テーブルについて考えてみます。 **[KeyColumns]** について次の選択を行います。</span><span class="sxs-lookup"><span data-stu-id="55ca6-115">For example, consider a sample table that contains columns A, B, and C. You make the following selections for **KeyColumns**:</span></span>  
  
-   <span data-ttu-id="55ca6-116">\*[KeyColumns] **で [(** )] と C 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-116">You select (\*) and column C in **KeyColumns**.</span></span> <span data-ttu-id="55ca6-117">タスクは、C 列のキーの強さを計算し、次に複合キー候補 (A 列と C 列の組み合わせと B 列と C 列の組み合わせ) のキーの強さを計算します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-117">The task computes the key strength of column C, and then of composite key candidates (A, C) and (B, C).</span></span>  
  
-   <span data-ttu-id="55ca6-118">\*[KeyColumns]\*で [( **)] と [(** )] を選択します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-118">You select (\*) and (\*) in **KeyColumns**.</span></span> <span data-ttu-id="55ca6-119">タスクは、A 列、B 列、および C 列のキーの強さを個別に計算し、次に複合キー候補 (A, B)、(A, C)、および (B, C) のキーの強さを計算します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-119">The task computes the key strength of individual columns A, B, and C, and then of composite key candidates (A, B), (A, C) and (B, C).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55ca6-120">[(\*)] を選択した場合、多数の計算が実行され、タスクのパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55ca6-120">If you select (\*), this option might result in a large number of computations and decrease the performance of the task.</span></span> <span data-ttu-id="55ca6-121">ただし、キーのしきい値を満たすサブセットをタスクが見つけた場合、その他の組み合わせは分析されません。</span><span class="sxs-lookup"><span data-stu-id="55ca6-121">However, if the task finds a subset that satisfies the threshold for a key, the task does not analyze additional combinations.</span></span> <span data-ttu-id="55ca6-122">たとえば、上記のサンプル テーブルで C 列がキーであるとタスクが判断した場合、複合キー候補の分析は続行されません。</span><span class="sxs-lookup"><span data-stu-id="55ca6-122">For example, in the sample table described above, if the task determines that column C is a key, the task does not continue to analyze the composite key candidates.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="55ca6-123">[要求プロパティ] のオプション</span><span class="sxs-lookup"><span data-stu-id="55ca6-123">Request Properties Options</span></span>  
 <span data-ttu-id="55ca6-124">**[要求プロパティ]** ペインに表示される **[候補キー プロファイル要求]** のオプション グループは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55ca6-124">For a **Candidate Key Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="55ca6-125">**[データ]** ( **[TableOrView]** オプション、 **[KeyColumns]** オプションなど)</span><span class="sxs-lookup"><span data-stu-id="55ca6-125">**Data**, which includes the **TableOrView** and **KeyColumns** options</span></span>  
  
-   <span data-ttu-id="55ca6-126">**全般**</span><span class="sxs-lookup"><span data-stu-id="55ca6-126">**General**</span></span>  
  
-   <span data-ttu-id="55ca6-127">**[オプション]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-127">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="55ca6-128">[データ] のオプション</span><span class="sxs-lookup"><span data-stu-id="55ca6-128">Data Options</span></span>  
 <span data-ttu-id="55ca6-129">**[ConnectionManager]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-129">**ConnectionManager**</span></span>  
 <span data-ttu-id="55ca6-130">プロファイル対象のテーブルまたはビューを含む [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-130">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="55ca6-131">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-131">**TableOrView**</span></span>  
 <span data-ttu-id="55ca6-132">プロファイル対象の既存のテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-132">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="55ca6-133">詳細については、このトピックの「[TableorView] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca6-133">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="55ca6-134">**[KeyColumns]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-134">**KeyColumns**</span></span>  
 <span data-ttu-id="55ca6-135">プロファイル対象の既存の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-135">Select the existing column or columns to be profiled.</span></span> <span data-ttu-id="55ca6-136">すべての列をプロファイルするには、 **[(\*)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-136">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="55ca6-137">詳細については、このトピックの「KeyColumns プロパティの列の選択について」と「[KeyColumns] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca6-137">For more information, see the sections, "Understanding the Selection of Columns for the KeyColumns Property" and "KeyColumns Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="55ca6-138">[TableOrView] のオプション</span><span class="sxs-lookup"><span data-stu-id="55ca6-138">TableOrView Options</span></span>  
 <span data-ttu-id="55ca6-139">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-139">**Schema**</span></span>  
 <span data-ttu-id="55ca6-140">選択したテーブルが属するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-140">Specify the schema to which the selected table belongs.</span></span> <span data-ttu-id="55ca6-141">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="55ca6-142">**Table**</span><span class="sxs-lookup"><span data-stu-id="55ca6-142">**Table**</span></span>  
 <span data-ttu-id="55ca6-143">選択したテーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-143">Displays the name of the selected table.</span></span> <span data-ttu-id="55ca6-144">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-144">This option is read-only.</span></span>  
  
#### <a name="keycolumns-options"></a><span data-ttu-id="55ca6-145">[KeyColumns] のオプション</span><span class="sxs-lookup"><span data-stu-id="55ca6-145">KeyColumns Options</span></span>  
 <span data-ttu-id="55ca6-146">次のオプションは、 **[KeyColumns]** で選択したプロファイル対象の各列および **[(\*)]** オプションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-146">The following options are presented for each column selected for profiling in **KeyColumns**, or for the **(\*)** option.</span></span>  
  
 <span data-ttu-id="55ca6-147">詳細については、このトピックの「KeyColumns プロパティの列の選択について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca6-147">For more information, see the section, "Understanding the Selection of Columns for the KeyColumns Property," earlier in this topic.</span></span>  
  
 <span data-ttu-id="55ca6-148">**[IsWildCard]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-148">**IsWildcard**</span></span>  
 <span data-ttu-id="55ca6-149">**[(\*)]** ワイルドカードが選択されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-149">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="55ca6-150">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは **[True]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-150">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="55ca6-151">個々の列をプロファイル対象として選択した場合、このオプションは **[False]** になります。</span><span class="sxs-lookup"><span data-stu-id="55ca6-151">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="55ca6-152">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-152">This option is read-only.</span></span>  
  
 <span data-ttu-id="55ca6-153">**[ColumnName]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-153">**ColumnName**</span></span>  
 <span data-ttu-id="55ca6-154">選択した列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-154">Displays the name of the selected column.</span></span> <span data-ttu-id="55ca6-155">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="55ca6-155">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="55ca6-156">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-156">This option is read-only.</span></span>  
  
 <span data-ttu-id="55ca6-157">**[StringCompareOptions]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-157">**StringCompareOptions**</span></span>  
 <span data-ttu-id="55ca6-158">文字列値を比較するためのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-158">Select options for comparing string values.</span></span> <span data-ttu-id="55ca6-159">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-159">This property has the options listed in the following table.</span></span> <span data-ttu-id="55ca6-160">このオプションの既定値は **[Default]** です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-160">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55ca6-161">**[ColumnName]** に **[(\*)]** ワイルドカードを使用する場合、**[CompareOptions]** は読み取り専用で、**[Default]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-161">When you use a **(\*)** wildcard for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="55ca6-162">値</span><span class="sxs-lookup"><span data-stu-id="55ca6-162">Value</span></span>|<span data-ttu-id="55ca6-163">説明</span><span class="sxs-lookup"><span data-stu-id="55ca6-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="55ca6-164">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-164">**Default**</span></span>|<span data-ttu-id="55ca6-165">ソース テーブル内の列の照合順序に基づいてデータを並べ替えて比較します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-165">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="55ca6-166">**[BinarySort]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-166">**BinarySort**</span></span>|<span data-ttu-id="55ca6-167">文字ごとに定義されているビット パターンに基づいてデータを並べ替えて比較します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-167">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="55ca6-168">バイナリ並べ替え順では、大文字と小文字が区別され、アクセントが区別されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-168">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="55ca6-169">また、バイナリは最速の並べ替え順です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-169">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="55ca6-170">**[DictionarySort]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-170">**DictionarySort**</span></span>|<span data-ttu-id="55ca6-171">関連する言語またはアルファベットの辞書で定義されている並べ替えおよび比較ルールに基づいてデータを並べ替えて比較します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-171">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="55ca6-172">**[DictionarySort]** を選択した場合は、次の表に示すオプションの任意の組み合わせも選択できます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-172">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="55ca6-173">既定では、これらの追加オプションは選択されていません。</span><span class="sxs-lookup"><span data-stu-id="55ca6-173">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="55ca6-174">値</span><span class="sxs-lookup"><span data-stu-id="55ca6-174">Value</span></span>|<span data-ttu-id="55ca6-175">説明</span><span class="sxs-lookup"><span data-stu-id="55ca6-175">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="55ca6-176">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="55ca6-176">**IgnoreCase**</span></span>|<span data-ttu-id="55ca6-177">比較時に、大文字と小文字を区別するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-177">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="55ca6-178">このオプションを設定した場合、文字列比較で大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="55ca6-178">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="55ca6-179">たとえば、"ABC" は "abc" と同一になります。</span><span class="sxs-lookup"><span data-stu-id="55ca6-179">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="55ca6-180">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="55ca6-180">**IgnoreNonSpace**</span></span>|<span data-ttu-id="55ca6-181">比較で、通常の文字と分音文字付きの文字を区別するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-181">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="55ca6-182">このオプションを設定した場合、比較で分音文字は無視されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-182">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="55ca6-183">たとえば、"&#xE5;" は "a" と同じ文字になります。</span><span class="sxs-lookup"><span data-stu-id="55ca6-183">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="55ca6-184">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="55ca6-184">**IgnoreKanaType**</span></span>|<span data-ttu-id="55ca6-185">日本語の比較で、2 種類のかな文字である、ひらがなとカタカナを区別するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-185">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="55ca6-186">このオプションを設定した場合、文字列比較でひらがなとカタカナは区別されません。</span><span class="sxs-lookup"><span data-stu-id="55ca6-186">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="55ca6-187">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="55ca6-187">**IgnoreWidth**</span></span>|<span data-ttu-id="55ca6-188">比較で、1 バイト文字と、それと同じ文字を表記した 2 バイト文字を区別するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-188">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="55ca6-189">このオプションを設定した場合、文字列比較で 1 バイト表記と 2 バイト表記は同一文字として扱われます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-189">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="55ca6-190">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="55ca6-190">General Options</span></span>  
 <span data-ttu-id="55ca6-191">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="55ca6-191">**RequestID**</span></span>  
 <span data-ttu-id="55ca6-192">このプロファイル要求を識別するわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-192">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="55ca6-193">通常、自動生成された値を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="55ca6-193">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="55ca6-194">オプション</span><span class="sxs-lookup"><span data-stu-id="55ca6-194">Options</span></span>  
 <span data-ttu-id="55ca6-195">**[ThresholdSetting]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-195">**ThresholdSetting**</span></span>  
 <span data-ttu-id="55ca6-196">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-196">This property has the options listed in the following table.</span></span> <span data-ttu-id="55ca6-197">このプロパティの既定値は **[Specified]** です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-197">The default value of this property is **Specified**.</span></span>  
  
|<span data-ttu-id="55ca6-198">値</span><span class="sxs-lookup"><span data-stu-id="55ca6-198">Value</span></span>|<span data-ttu-id="55ca6-199">説明</span><span class="sxs-lookup"><span data-stu-id="55ca6-199">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="55ca6-200">**なし**</span><span class="sxs-lookup"><span data-stu-id="55ca6-200">**None**</span></span>|<span data-ttu-id="55ca6-201">しきい値が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="55ca6-201">No threshold is specified.</span></span> <span data-ttu-id="55ca6-202">キーの強さは、その値に関係なく報告されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-202">The key strength is reported regardless of its value.</span></span>|  
|<span data-ttu-id="55ca6-203">**[Specified]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-203">**Specified**</span></span>|<span data-ttu-id="55ca6-204">しきい値は **[KeyStrengthThreshold]** で指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-204">A threshold is specified in **KeyStrengthThreshold**.</span></span> <span data-ttu-id="55ca6-205">キーの強さは、このしきい値より大きい場合にのみ報告されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-205">The key strength is reported only if it is greater than the threshold.</span></span>|  
|<span data-ttu-id="55ca6-206">**[Exact]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-206">**Exact**</span></span>|<span data-ttu-id="55ca6-207">しきい値が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="55ca6-207">No threshold is specified.</span></span> <span data-ttu-id="55ca6-208">キーの強さは、選択した列がキーに完全に一致している場合にのみ報告されます。</span><span class="sxs-lookup"><span data-stu-id="55ca6-208">The key strength is reported only if the selected columns are an exact key.</span></span>|  
  
 <span data-ttu-id="55ca6-209">**[KeyStrengthThreshold]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-209">**KeyStrengthThreshold**</span></span>  
 <span data-ttu-id="55ca6-210">0 ～ 1 の値を使用して、キーの強さが報告されるしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-210">Specify the threshold (by using a value between 0 and 1) above which the key strength should be reported.</span></span> <span data-ttu-id="55ca6-211">このプロパティの既定値は 0.95 です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-211">The default value of this property is 0.95.</span></span> <span data-ttu-id="55ca6-212">このオプションは、 **[KeyStrengthThresholdSetting]** で **[Specified]** が選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-212">This option is enabled only when **Specified** is selected as the **KeyStrengthThresholdSetting**.</span></span>  
  
 <span data-ttu-id="55ca6-213">**[MaxNumberOfViolations]**</span><span class="sxs-lookup"><span data-stu-id="55ca6-213">**MaxNumberOfViolations**</span></span>  
 <span data-ttu-id="55ca6-214">出力で報告する候補キー違反の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca6-214">Specify the maximum number of candidate key violations to report in the output.</span></span> <span data-ttu-id="55ca6-215">このプロパティの既定値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-215">The default value of this property is 100.</span></span> <span data-ttu-id="55ca6-216">このオプションは、 **[KeyStrengthThresholdSetting]** で **[Exact]** が選択されている場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="55ca6-216">This option is disabled when **Exact** is selected as the **KeyStrengthThresholdSetting**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ca6-217">参照</span><span class="sxs-lookup"><span data-stu-id="55ca6-217">See Also</span></span>  
 <span data-ttu-id="55ca6-218">[データ プロファイル タスク エディター ([全般] ページ)](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="55ca6-218">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="55ca6-219">単一テーブル クイック プロファイル フォーム &#40;データ プロファイル タスク&#41;</span><span class="sxs-lookup"><span data-stu-id="55ca6-219">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
