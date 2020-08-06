---
title: '[列パターン プロファイル要求] のオプション (データ プロファイル タスク) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 9ccb8fc5-f65e-41a2-9511-7fa55586eb8b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9293d19baaee95cee77b075447dcfe1061d20bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640187"
---
# <a name="column-pattern-profile-request-options-data-profiling-task"></a><span data-ttu-id="57f88-102">[列パターン プロファイル要求] のオプション (データ プロファイル タスク)</span><span class="sxs-lookup"><span data-stu-id="57f88-102">Column Pattern Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="57f88-103">**[プロファイル要求]** ページの **[要求プロパティ]** ペインを使用すると、要求ペインで選択した **[列パターン プロファイル要求]** のオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="57f88-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Pattern Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="57f88-104">列パターン プロファイルは、文字列型の列に含まれる指定された比率の値に対応する一連の正規表現を報告します。</span><span class="sxs-lookup"><span data-stu-id="57f88-104">A Column Pattern profile reports a set of regular expressions that cover the specified percentage of values in a string column.</span></span> <span data-ttu-id="57f88-105">このプロファイルを使用すると、無効な文字列などのデータの問題を特定できます。また、このプロファイルには、新しい値を検証するために将来使用できる正規表現も提示されます。</span><span class="sxs-lookup"><span data-stu-id="57f88-105">This profile can help you identify problems in your data, such as invalid strings, and can suggest regular expressions that can be used in the future to validate new values.</span></span> <span data-ttu-id="57f88-106">たとえば、米国郵便番号列のパターン プロファイルでは、\d{5}-\d{4}、\d{5}、および \d{9} という正規表現が生成されます。</span><span class="sxs-lookup"><span data-stu-id="57f88-106">For example, a pattern profile of a column of United States Zip Codes might produce the regular expressions \d{5}-\d{4}, \d{5}, and \d{9}.</span></span> <span data-ttu-id="57f88-107">その他の正規表現が示された場合、データに無効な値または形式が正しくない値が含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57f88-107">If you see other regular expressions, your data likely contains values that are invalid or in an incorrect format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57f88-108">このトピックで説明するオプションは、 **[データ プロファイル タスク エディター]** の **[プロファイル要求]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="57f88-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="57f88-109">エディターのこのページの詳細については、「[Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md)」(データ プロファイル タスク エディター &#40;[プロファイル要求] ページ&#41;)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="57f88-110">データ プロファイル タスクの使用方法の詳細については、「 [データ プロファイル タスクのセットアップ](data-profiling-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="57f88-111">Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「 [Data Profile Viewer](data-profile-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-use-of-delimiters-and-symbols"></a><span data-ttu-id="57f88-112">区切り記号と記号の使用方法について</span><span class="sxs-lookup"><span data-stu-id="57f88-112">Understanding the Use of Delimiters and Symbols</span></span>  
 <span data-ttu-id="57f88-113">データ プロファイル タスクは、 **列パターン プロファイル要求**のパターンを計算する前にデータをトークン化します。</span><span class="sxs-lookup"><span data-stu-id="57f88-113">Before computing the patterns for a **Column Pattern Profile Request**, the Data Profiling Task tokenizes the data.</span></span> <span data-ttu-id="57f88-114">つまり、データ プロファイル タスクは、文字列値をトークンと呼ばれる小さな単位に分割します。</span><span class="sxs-lookup"><span data-stu-id="57f88-114">That is, the task separates the string values into smaller units known as tokens.</span></span> <span data-ttu-id="57f88-115">データ プロファイル タスクは、 **Delimiters** プロパティおよび **Symbols** プロパティで指定された区切り記号と記号に基づいて文字列をトークンに分割します。</span><span class="sxs-lookup"><span data-stu-id="57f88-115">The task separates strings into tokens based on the delimiters and symbols that you specify for the **Delimiters** and **Symbols** properties:</span></span>  
  
-   <span data-ttu-id="57f88-116">**Delimiters** 既定では、区切り記号の一覧には、空白文字、水平タブ文字 (\t)、改行文字 (\n)、および復帰文字 (\r) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="57f88-116">**Delimiters** By default, the list of delimiters contains the following characters: space, horizontal tab (\t), new line (\n), and carriage return (\r).</span></span> <span data-ttu-id="57f88-117">追加の区切り記号を指定できますが、既定の区切り記号を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="57f88-117">You can specify additional delimiters, but you cannot remove the default delimiters.</span></span>  
  
-   <span data-ttu-id="57f88-118">**シンボル**既定では、**記号**の一覧には次の文字が含まれています: `,.;:-"'` ~ =&/@!?() <> [] {} | # \* ^% `. For example, if the symbols are "` ()-' "の値" (425) 123-4567 "は、[" ("," 425 ",") "," 123 ","-"," 4567 ",") "] としてトークン化されます。</span><span class="sxs-lookup"><span data-stu-id="57f88-118">**Symbols** By default, the list of **Symbols** contains the following characters: `,.;:-"'`~=&/@!?()<>[]{}|#\*^%`. For example, if the symbols are "`()-\`", the value "(425) 123-4567" is tokenized as ["(", "425", ")", "123", "-", "4567", ")"].</span></span>  
  
 <span data-ttu-id="57f88-119">1 つの文字を区切り記号と記号の両方に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="57f88-119">A character cannot be both a delimiter and a symbol.</span></span>  
  
 <span data-ttu-id="57f88-120">区切り記号はすべて、トークン化処理の一部として 1 つの空白文字に正規化されます。一方、記号はそのまま保持されます。</span><span class="sxs-lookup"><span data-stu-id="57f88-120">All delimiters are normalized to a single space as part of the tokenizing process, while symbols are retained.</span></span>  
  
## <a name="understanding-the-use-of-the-tag-table"></a><span data-ttu-id="57f88-121">タグ テーブルの使用方法について</span><span class="sxs-lookup"><span data-stu-id="57f88-121">Understanding the Use of the Tag Table</span></span>  
 <span data-ttu-id="57f88-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース内に作成した特別なテーブルにタグと関連用語を保存することで、1 つのタグを持つ関連トークンを必要に応じてグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="57f88-122">You can optionally group related tokens with a single tag by storing tags and the related terms in a special table that you create in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="57f88-123">タグ テーブルには、"Tag" および "Term" という名前の 2 つの文字列型の列が必要です。</span><span class="sxs-lookup"><span data-stu-id="57f88-123">The tag table must have two string columns, one named "Tag" and the other named "Term".</span></span> <span data-ttu-id="57f88-124">これらの列には、`char` 型、`nchar` 型、`varchar` 型、または `nvarchar` 型を指定できます。ただし、`text` 型と `ntext` 型は指定できません。</span><span class="sxs-lookup"><span data-stu-id="57f88-124">These columns can be of type `char`, `nchar`, `varchar`, or `nvarchar`, but not `text` or `ntext`.</span></span> <span data-ttu-id="57f88-125">1 つのテーブルで複数のタグと対応する用語を結合できます。</span><span class="sxs-lookup"><span data-stu-id="57f88-125">You can combine multiple tags and the corresponding terms in a single table.</span></span> <span data-ttu-id="57f88-126">1 つの列パターン プロファイル要求で使用できるタグ テーブルは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="57f88-126">A Column Pattern Profile Request can use only one tag table.</span></span> <span data-ttu-id="57f88-127">タグ テーブルには個別の [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="57f88-127">You can use a separate [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to the tag table.</span></span> <span data-ttu-id="57f88-128">そのため、タグ テーブルは、ソース データとは異なるデータベースまたはサーバーに格納できます。</span><span class="sxs-lookup"><span data-stu-id="57f88-128">Therefore, the tag table can be located in a different database or on a different server than the source data.</span></span>  
  
 <span data-ttu-id="57f88-129">たとえば、住所に含まれる可能性がある "East"、"West"、"North"、および "South" という値を、"Direction" という 1 つのタグでグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="57f88-129">For example, you could group the values "East", "West", "North", and "South" that might appear in street addresses by using the single tag, "Direction".</span></span> <span data-ttu-id="57f88-130">次の表に、このようなタグ テーブルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="57f88-130">The following table is an example of such a tag table.</span></span>  
  
|<span data-ttu-id="57f88-131">タグ</span><span class="sxs-lookup"><span data-stu-id="57f88-131">Tag</span></span>|<span data-ttu-id="57f88-132">期間</span><span class="sxs-lookup"><span data-stu-id="57f88-132">Term</span></span>|  
|---------|----------|  
|<span data-ttu-id="57f88-133">Direction</span><span class="sxs-lookup"><span data-stu-id="57f88-133">Direction</span></span>|<span data-ttu-id="57f88-134">East</span><span class="sxs-lookup"><span data-stu-id="57f88-134">East</span></span>|  
|<span data-ttu-id="57f88-135">Direction</span><span class="sxs-lookup"><span data-stu-id="57f88-135">Direction</span></span>|<span data-ttu-id="57f88-136">West</span><span class="sxs-lookup"><span data-stu-id="57f88-136">West</span></span>|  
|<span data-ttu-id="57f88-137">Direction</span><span class="sxs-lookup"><span data-stu-id="57f88-137">Direction</span></span>|<span data-ttu-id="57f88-138">North</span><span class="sxs-lookup"><span data-stu-id="57f88-138">North</span></span>|  
|<span data-ttu-id="57f88-139">Direction</span><span class="sxs-lookup"><span data-stu-id="57f88-139">Direction</span></span>|<span data-ttu-id="57f88-140">South</span><span class="sxs-lookup"><span data-stu-id="57f88-140">South</span></span>|  
  
 <span data-ttu-id="57f88-141">別のタグを使用して、住所の "通り" の概念を表すさまざまな単語をグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="57f88-141">You could use another tag to group the different words that express the notion of a "street" in street addresses:</span></span>  
  
|<span data-ttu-id="57f88-142">タグ</span><span class="sxs-lookup"><span data-stu-id="57f88-142">Tag</span></span>|<span data-ttu-id="57f88-143">期間</span><span class="sxs-lookup"><span data-stu-id="57f88-143">Term</span></span>|  
|---------|----------|  
|<span data-ttu-id="57f88-144">Street</span><span class="sxs-lookup"><span data-stu-id="57f88-144">Street</span></span>|<span data-ttu-id="57f88-145">Street</span><span class="sxs-lookup"><span data-stu-id="57f88-145">Street</span></span>|  
|<span data-ttu-id="57f88-146">Street</span><span class="sxs-lookup"><span data-stu-id="57f88-146">Street</span></span>|<span data-ttu-id="57f88-147">Avenue</span><span class="sxs-lookup"><span data-stu-id="57f88-147">Avenue</span></span>|  
|<span data-ttu-id="57f88-148">Street</span><span class="sxs-lookup"><span data-stu-id="57f88-148">Street</span></span>|<span data-ttu-id="57f88-149">場所</span><span class="sxs-lookup"><span data-stu-id="57f88-149">Place</span></span>|  
|<span data-ttu-id="57f88-150">Street</span><span class="sxs-lookup"><span data-stu-id="57f88-150">Street</span></span>|<span data-ttu-id="57f88-151">方法</span><span class="sxs-lookup"><span data-stu-id="57f88-151">Way</span></span>|  
  
 <span data-ttu-id="57f88-152">これらのタグの組み合わせに基づいて生成される住所のパターンは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="57f88-152">Based on this combination of tags, the resulting pattern for a street address might resemble the following pattern:</span></span>  
  
 `\d+\ LookupTag=Direction \d+\p{L}+\ LookupTag=Street`  
  
> [!NOTE]  
>  <span data-ttu-id="57f88-153">タグ テーブルを使用すると、データ プロファイル タスクのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="57f88-153">Using a tag table decreases the performance of the Data Profiling task.</span></span> <span data-ttu-id="57f88-154">使用するタグは 10 個以内にし、また用語は 1 つのタグにつき 100 個以内にしてください。</span><span class="sxs-lookup"><span data-stu-id="57f88-154">Do not use more than 10 tags or more than 100 terms per tag.</span></span>  
  
 <span data-ttu-id="57f88-155">同じ用語を複数のタグに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="57f88-155">The same term can belong to more than one tag.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="57f88-156">[要求プロパティ] のオプション</span><span class="sxs-lookup"><span data-stu-id="57f88-156">Request Properties Options</span></span>  
 <span data-ttu-id="57f88-157">**[要求プロパティ]** ペインに表示される **[列パターン プロファイル要求]** のオプション グループは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="57f88-157">For a **Column Pattern Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="57f88-158">**[データ]**( **[TableOrView]** オプション、 **[Column]** オプションなど)</span><span class="sxs-lookup"><span data-stu-id="57f88-158">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="57f88-159">**全般**</span><span class="sxs-lookup"><span data-stu-id="57f88-159">**General**</span></span>  
  
-   <span data-ttu-id="57f88-160">**Options**</span><span class="sxs-lookup"><span data-stu-id="57f88-160">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="57f88-161">[データ] のオプション</span><span class="sxs-lookup"><span data-stu-id="57f88-161">Data Options</span></span>  
 <span data-ttu-id="57f88-162">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="57f88-162">**ConnectionManager**</span></span>  
 <span data-ttu-id="57f88-163">プロファイル対象のテーブルまたはビューを含む [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="57f88-163">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="57f88-164">**[Tableorview]**</span><span class="sxs-lookup"><span data-stu-id="57f88-164">**TableOrView**</span></span>  
 <span data-ttu-id="57f88-165">プロファイル対象の列を含む既存のテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="57f88-165">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="57f88-166">詳細については、このトピックの「[TableorView] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-166">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="57f88-167">**列**</span><span class="sxs-lookup"><span data-stu-id="57f88-167">**Column**</span></span>  
 <span data-ttu-id="57f88-168">プロファイル対象の既存の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="57f88-168">Select the existing column to be profiled.</span></span> <span data-ttu-id="57f88-169">すべての列をプロファイルするには、[ **( \* )** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57f88-169">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="57f88-170">詳細については、このトピックの「[列] のオプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-170">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="57f88-171">[TableOrView] のオプション</span><span class="sxs-lookup"><span data-stu-id="57f88-171">TableOrView Options</span></span>  
 <span data-ttu-id="57f88-172">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="57f88-172">**Schema**</span></span>  
 <span data-ttu-id="57f88-173">選択したテーブルが属するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="57f88-173">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="57f88-174">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="57f88-174">This option is read-only.</span></span>  
  
 <span data-ttu-id="57f88-175">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="57f88-175">**Table**</span></span>  
 <span data-ttu-id="57f88-176">選択したテーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="57f88-176">Displays the name of the selected table.</span></span> <span data-ttu-id="57f88-177">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="57f88-177">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="57f88-178">[列] のオプション</span><span class="sxs-lookup"><span data-stu-id="57f88-178">Column Options</span></span>  
 <span data-ttu-id="57f88-179">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="57f88-179">**IsWildCard**</span></span>  
 <span data-ttu-id="57f88-180">**( \* )** ワイルドカードが選択されているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="57f88-180">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="57f88-181">**[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは **[True]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="57f88-181">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="57f88-182">個々の列をプロファイル対象として選択した場合、このオプションは **[False]** になります。</span><span class="sxs-lookup"><span data-stu-id="57f88-182">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="57f88-183">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="57f88-183">This option is read-only.</span></span>  
  
 <span data-ttu-id="57f88-184">**[ColumnName]**</span><span class="sxs-lookup"><span data-stu-id="57f88-184">**ColumnName**</span></span>  
 <span data-ttu-id="57f88-185">選択した列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="57f88-185">Displays the name of the selected column.</span></span> <span data-ttu-id="57f88-186">**( \* )** を選択してすべての列をプロファイルする場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="57f88-186">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="57f88-187">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="57f88-187">This option is read-only.</span></span>  
  
 <span data-ttu-id="57f88-188">**[StringCompareOptions]**</span><span class="sxs-lookup"><span data-stu-id="57f88-188">**StringCompareOptions**</span></span>  
 <span data-ttu-id="57f88-189">このオプションは、列パターン プロファイルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="57f88-189">This option does not apply to the Column Pattern Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="57f88-190">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="57f88-190">General Options</span></span>  
 <span data-ttu-id="57f88-191">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="57f88-191">**RequestID**</span></span>  
 <span data-ttu-id="57f88-192">このプロファイル要求を識別するわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="57f88-192">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="57f88-193">通常、自動生成された値を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="57f88-193">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="57f88-194">Options</span><span class="sxs-lookup"><span data-stu-id="57f88-194">Options</span></span>  
 <span data-ttu-id="57f88-195">**[MaxNumberOfPatterns]**</span><span class="sxs-lookup"><span data-stu-id="57f88-195">**MaxNumberOfPatterns**</span></span>  
 <span data-ttu-id="57f88-196">プロファイルで計算するパターンの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="57f88-196">Specify the maximum number of patterns that you want the profile to compute.</span></span> <span data-ttu-id="57f88-197">このオプションの既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="57f88-197">The default value of this option is 10.</span></span> <span data-ttu-id="57f88-198">最大値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="57f88-198">The maximum value is 100.</span></span>  
  
 <span data-ttu-id="57f88-199">**[PercentageDataCoverageDesired]**</span><span class="sxs-lookup"><span data-stu-id="57f88-199">**PercentageDataCoverageDesired**</span></span>  
 <span data-ttu-id="57f88-200">計算されたパターンでカバーするデータの割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="57f88-200">Specify the percentage of the data that you want the computed patterns to cover.</span></span> <span data-ttu-id="57f88-201">このオプションの既定値は 95 (%) です。</span><span class="sxs-lookup"><span data-stu-id="57f88-201">The default value of this option is 95 (percent).</span></span>  
  
 <span data-ttu-id="57f88-202">**CaseSensitive**</span><span class="sxs-lookup"><span data-stu-id="57f88-202">**CaseSensitive**</span></span>  
 <span data-ttu-id="57f88-203">パターンで大文字と小文字を区別するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="57f88-203">Indicate whether the patterns should be case-sensitive.</span></span> <span data-ttu-id="57f88-204">このオプションの既定値は **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="57f88-204">The default value of this option is **False**.</span></span>  
  
 <span data-ttu-id="57f88-205">**区切り記号**</span><span class="sxs-lookup"><span data-stu-id="57f88-205">**Delimiters**</span></span>  
 <span data-ttu-id="57f88-206">テキストをトークン化するときに、単語間の空白文字と同等のものとして処理する文字の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="57f88-206">List the characters that should be treated as the equivalent of spaces between words when tokenizing text.</span></span> <span data-ttu-id="57f88-207">既定では、 **[Delimiters]** の一覧には、空白文字、水平タブ文字 (\t)、改行文字 (\n)、および復帰文字 (\r) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="57f88-207">By default, the list of **Delimiters** contains the following characters: the space, horizontal tab (\t), new line (\n), and carriage return (\r).</span></span> <span data-ttu-id="57f88-208">追加の区切り記号を指定できますが、既定の区切り記号を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="57f88-208">You can specify additional delimiters, but you cannot remove the default delimiters.</span></span>  
  
 <span data-ttu-id="57f88-209">詳細については、このトピックの「区切り記号と記号の使用方法について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-209">For more information, see "Understanding the Use of Delimiters and Symbols" earlier in this topic.</span></span>  
  
 <span data-ttu-id="57f88-210">**文字**</span><span class="sxs-lookup"><span data-stu-id="57f88-210">**Symbols**</span></span>  
 <span data-ttu-id="57f88-211">パターンの一部として保持する記号の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="57f88-211">List the symbols that should be retained as part of patterns.</span></span> <span data-ttu-id="57f88-212">記号の例として、日付を表す "/"、時刻を表す ":"、電子メール アドレスを表す "@" などがあります。</span><span class="sxs-lookup"><span data-stu-id="57f88-212">Examples might include "/" for dates, ":" for times, and "@" for e-mail addresses.</span></span> <span data-ttu-id="57f88-213">既定では、**記号**の一覧には次の文字が含まれています: `,.;:-"'` ~ =&/@!?() <> [] {} | # \* ^% ' です。</span><span class="sxs-lookup"><span data-stu-id="57f88-213">By default, the list of **Symbols** contains the following characters: `,.;:-"'`~=&/@!?()<>[]{}|#\*^%\`.</span></span>  
  
 <span data-ttu-id="57f88-214">詳細については、このトピックの「区切り記号と記号の使用方法について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-214">For more information, see "Understanding the Use of Delimiters and Symbols" earlier in this topic.</span></span>  
  
 <span data-ttu-id="57f88-215">**[TagTableConnectionManager]**</span><span class="sxs-lookup"><span data-stu-id="57f88-215">**TagTableConnectionManager**</span></span>  
 <span data-ttu-id="57f88-216">タグ テーブルを含む [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="57f88-216">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the tag table.</span></span>  
  
 <span data-ttu-id="57f88-217">詳細については、このトピックの「タグ テーブルの使用方法について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-217">For more information, see "Understanding the Use of the Tag Table" earlier in this topic.</span></span>  
  
 <span data-ttu-id="57f88-218">**[TagTableName]**</span><span class="sxs-lookup"><span data-stu-id="57f88-218">**TagTableName**</span></span>  
 <span data-ttu-id="57f88-219">"Tag" および "Term" という名前の 2 つの文字列型の列を持つ既存のタグ テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="57f88-219">Select the existing tag table, which must have two string columns named Tag and Term.</span></span>  
  
 <span data-ttu-id="57f88-220">詳細については、このトピックの「タグ テーブルの使用方法について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f88-220">For more information, see "Understanding the Use of the Tag Table" earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f88-221">参照</span><span class="sxs-lookup"><span data-stu-id="57f88-221">See Also</span></span>  
 <span data-ttu-id="57f88-222">[[データプロファイルタスクエディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="57f88-222">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="57f88-223">単一テーブル クイック プロファイル フォーム &#40;データ プロファイル タスク&#41;</span><span class="sxs-lookup"><span data-stu-id="57f88-223">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
