---
title: Data Profile Viewer F1 ヘルプ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dataprofileviewer.f1
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], viewer
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7003e1299938bd53a6d16a5597d4566ba5c46579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633233"
---
# <a name="data-profile-viewer-f1-help"></a><span data-ttu-id="0beb7-102">Data Profile Viewer の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="0beb7-102">Data Profile Viewer F1 Help</span></span>
  <span data-ttu-id="0beb7-103">Data Profile Viewer を使用すると、データ プロファイル タスクの出力を表示できます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-103">Use the Data Profile Viewer to view the output of the Data Profiling task.</span></span>  
  
 <span data-ttu-id="0beb7-104">Data Profile Viewer の使用方法の詳細については、「 [Data Profile Viewer](control-flow/data-profile-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0beb7-104">For more information about how to use the Data Profile Viewer, see [Data Profile Viewer](control-flow/data-profile-viewer.md).</span></span> <span data-ttu-id="0beb7-105">データ プロファイル タスクの使用方法の詳細については、「 [データ プロファイル タスクのセットアップ](control-flow/data-profiling-task.md)」を参照してください。データ プロファイル タスクを使用すると、Data Profile Viewer で分析するプロファイル出力を作成できます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-105">For more information about how to use the Data Profiling task, which creates the profile output that you analyze in the Data Profile Viewer, see [Setup of the Data Profiling Task](control-flow/data-profiling-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="0beb7-106">静的オプション</span><span class="sxs-lookup"><span data-stu-id="0beb7-106">Static Options</span></span>  
 <span data-ttu-id="0beb7-107">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-107">**Open**</span></span>  
 <span data-ttu-id="0beb7-108">データ プロファイル タスクの出力を含む保存済みファイルを参照する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0beb7-108">Click to browse for the saved file that contains the output of the Data Profiling task.</span></span>  
  
 <span data-ttu-id="0beb7-109">**[プロファイル]** ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-109">**Profiles** pane</span></span>  
 <span data-ttu-id="0beb7-110">出力に含まれるプロファイルを表示するには、 **[プロファイル]** ペインのツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0beb7-110">Expand the tree in the **Profiles** pane to see the profiles that are included in the output.</span></span> <span data-ttu-id="0beb7-111">プロファイルを選択し、そのプロファイルの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="0beb7-111">Select a profile to view the results for that profile.</span></span>  
  
 <span data-ttu-id="0beb7-112">**[メッセージ]** ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-112">**Message** pane</span></span>  
 <span data-ttu-id="0beb7-113">状態を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-113">Displays status messages.</span></span>  
  
 <span data-ttu-id="0beb7-114">**[ドリル ダウン]** ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-114">**Drilldown** pane</span></span>  
 <span data-ttu-id="0beb7-115">データ プロファイル タスクで使用されるデータ ソースが使用可能な場合は、出力の値と一致するデータの行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-115">Displays the rows of data that match a value in the output, if the data source that is used by the Data Profiling task is available.</span></span>  
  
 <span data-ttu-id="0beb7-116">たとえば、US State 列に対する列の値分布プロファイルの出力を表示している場合に、 **[詳細な値分布]** ペインに "WA" の行が含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="0beb7-116">For example, if you are viewing the output of a Column Value Distribution profile for a US State column, the **Detailed Value Distribution** pane might contain a row for "WA".</span></span> <span data-ttu-id="0beb7-117">**[詳細な値分布]** ペインでこの行をダブルクリックすると、State 列が "WA" であるデータの行が [ドリル ダウン] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-117">Double-click the row in the **Detailed Value Distribution** pane to see the rows of data where the value of the state column is "WA" in the drilldown pane.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="0beb7-118">動的オプション</span><span class="sxs-lookup"><span data-stu-id="0beb7-118">Dynamic Options</span></span>  
  
### <a name="profile-type--column-length-distribution-profile"></a><span data-ttu-id="0beb7-119">プロファイルの種類 = 列長分布プロファイル</span><span class="sxs-lookup"><span data-stu-id="0beb7-119">Profile Type = Column Length Distribution Profile</span></span>  
  
#### <a name="column-length-distribution-profile---column-pane"></a><span data-ttu-id="0beb7-120">列長分布プロファイル - \<column> ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-120">Column Length Distribution Profile - \<column> pane</span></span>  
 <span data-ttu-id="0beb7-121">**[最小の長さ]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-121">**Minimum Length**</span></span>  
 <span data-ttu-id="0beb7-122">この列の最小の長さが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-122">Displays the minimum length of values in this column.</span></span>  
  
 <span data-ttu-id="0beb7-123">**[最大の長さ]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-123">**Maximum Length**</span></span>  
 <span data-ttu-id="0beb7-124">この列の最大の長さが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-124">Displays the maximum length of values in this column.</span></span>  
  
 <span data-ttu-id="0beb7-125">**[先頭のスペースを無視する]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-125">**Ignore Leading Spaces**</span></span>  
 <span data-ttu-id="0beb7-126">`IgnoreLeadingSpaces` の値に True または False のいずれを使用してこのプロファイルが計算されたかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-126">Displays whether this profile was computed with an `IgnoreLeadingSpaces` value of True or False.</span></span> <span data-ttu-id="0beb7-127">このプロパティは、[データ プロファイル タスク エディター] の **[プロファイル要求]** ページで設定されています。</span><span class="sxs-lookup"><span data-stu-id="0beb7-127">This property was set on the **Profile Requests** page of the Data Profiling Task Editor.</span></span>  
  
 <span data-ttu-id="0beb7-128">**[末尾のスペースを無視する]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-128">**Ignore Trailing Spaces**</span></span>  
 <span data-ttu-id="0beb7-129">`IgnoreTrailingSpaces` の値に True または False のいずれを使用してこのプロファイルが計算されたかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-129">Displays whether this profile was computed with an `IgnoreTrailingSpaces` value of True or False.</span></span> <span data-ttu-id="0beb7-130">このプロパティは、[データ プロファイル タスク エディター] の **[プロファイル要求]** ページで設定されています。</span><span class="sxs-lookup"><span data-stu-id="0beb7-130">This property was set on the **Profile Requests** page of the Data Profiling Task Editor.</span></span>  
  
 <span data-ttu-id="0beb7-131">**行数**</span><span class="sxs-lookup"><span data-stu-id="0beb7-131">**Row Count**</span></span>  
 <span data-ttu-id="0beb7-132">テーブルまたはビューの行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-132">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="detailed-length-distribution-pane"></a><span data-ttu-id="0beb7-133">[詳細な長さ分布] ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-133">Detailed Length Distribution pane</span></span>  
 <span data-ttu-id="0beb7-134">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-134">**Length**</span></span>  
 <span data-ttu-id="0beb7-135">プロファイルされた列の列長が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-135">Displays the column lengths found in the profiled column.</span></span>  
  
 <span data-ttu-id="0beb7-136">**Count**</span><span class="sxs-lookup"><span data-stu-id="0beb7-136">**Count**</span></span>  
 <span data-ttu-id="0beb7-137">プロファイルされた列の値の長さが **[長さ]** 列に表示された長さである行の数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-137">Displays the number of rows in which the value of the profiled column has the length shown in the **Length** column.</span></span>  
  
 <span data-ttu-id="0beb7-138">**Percentage**</span><span class="sxs-lookup"><span data-stu-id="0beb7-138">**Percentage**</span></span>  
 <span data-ttu-id="0beb7-139">プロファイルされた列の値の長さが **[長さ]** 列に表示された長さである行の割合が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-139">Displays the percentage of rows in which the value of the profiled column has the length shown in the **Length** column.</span></span>  
  
### <a name="profile-type--column-null-ratio-profile"></a><span data-ttu-id="0beb7-140">プロファイルの種類 = 列の NULL 比プロファイル</span><span class="sxs-lookup"><span data-stu-id="0beb7-140">Profile Type = Column Null Ratio Profile</span></span>  
  
#### <a name="column-null-ratio-profile---column-pane"></a><span data-ttu-id="0beb7-141">列の NULL 比プロファイル - \<column> ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-141">Column Null Ratio Profile - \<column> pane</span></span>  
 <span data-ttu-id="0beb7-142">**[NULL カウント]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-142">**Null Count**</span></span>  
 <span data-ttu-id="0beb7-143">プロファイルされた列が NULL 値である行の数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-143">Displays the number of rows in which the profiled column has a null value.</span></span>  
  
 <span data-ttu-id="0beb7-144">**[NULL 比率]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-144">**Null Percentage**</span></span>  
 <span data-ttu-id="0beb7-145">プロファイルされた列が NULL 値である行の割合が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-145">Displays the percentage of rows in which the profiled column has a null value.</span></span>  
  
 <span data-ttu-id="0beb7-146">**行数**</span><span class="sxs-lookup"><span data-stu-id="0beb7-146">**Row Count**</span></span>  
 <span data-ttu-id="0beb7-147">テーブルまたはビューの行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-147">Displays the number of rows in the table or view.</span></span>  
  
### <a name="profile-type--column-pattern-profile"></a><span data-ttu-id="0beb7-148">プロファイルの種類 = 列パターン プロファイル</span><span class="sxs-lookup"><span data-stu-id="0beb7-148">Profile Type = Column Pattern Profile</span></span>  
  
#### <a name="column-pattern-profile---column-pane"></a><span data-ttu-id="0beb7-149">列パターン プロファイル - \<column> ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-149">Column Pattern Profile - \<column> pane</span></span>  
 <span data-ttu-id="0beb7-150">**行数**</span><span class="sxs-lookup"><span data-stu-id="0beb7-150">**Row Count**</span></span>  
 <span data-ttu-id="0beb7-151">テーブルまたはビューの行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-151">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="pattern-distribution-pane"></a><span data-ttu-id="0beb7-152">[パターン分布] ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-152">Pattern Distribution pane</span></span>  
 <span data-ttu-id="0beb7-153">**パターン**</span><span class="sxs-lookup"><span data-stu-id="0beb7-153">**Pattern**</span></span>  
 <span data-ttu-id="0beb7-154">プロファイルされた列について計算されたパターンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-154">Displays the patterns computed for the profiled column.</span></span>  
  
 <span data-ttu-id="0beb7-155">**Percentage**</span><span class="sxs-lookup"><span data-stu-id="0beb7-155">**Percentage**</span></span>  
 <span data-ttu-id="0beb7-156">**[パターン]** 列に表示されたパターンに一致する値を持つ行の割合が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-156">Displays the percentage of rows whose values match the pattern displayed in the **Pattern** column.</span></span>  
  
### <a name="profile-type--column-statistics-profile"></a><span data-ttu-id="0beb7-157">プロファイルの種類 = 列統計プロファイル</span><span class="sxs-lookup"><span data-stu-id="0beb7-157">Profile Type = Column Statistics Profile</span></span>  
  
#### <a name="column-statistics-profile---column-pane"></a><span data-ttu-id="0beb7-158">列統計プロファイル - \<column> ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-158">Column Statistics Profile - \<column> pane</span></span>  
 <span data-ttu-id="0beb7-159">**最小**</span><span class="sxs-lookup"><span data-stu-id="0beb7-159">**Minimum**</span></span>  
 <span data-ttu-id="0beb7-160">プロファイルされた列の最小値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-160">Displays the minimum value found in the profiled column.</span></span>  
  
 <span data-ttu-id="0beb7-161">**[最大]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-161">**Maximum**</span></span>  
 <span data-ttu-id="0beb7-162">プロファイルされた列の最大値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-162">Displays the maximum value found in the profiled column.</span></span>  
  
 <span data-ttu-id="0beb7-163">**Mean (平均値)**</span><span class="sxs-lookup"><span data-stu-id="0beb7-163">**Mean**</span></span>  
 <span data-ttu-id="0beb7-164">プロファイルされた列の値の平均が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-164">Displays the mean of the values found in the profiled column.</span></span>  
  
 <span data-ttu-id="0beb7-165">**Standard Deviation**</span><span class="sxs-lookup"><span data-stu-id="0beb7-165">**Standard Deviation**</span></span>  
 <span data-ttu-id="0beb7-166">プロファイルされた列の値の標準偏差が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-166">Displays the standard deviation of the values found in the profiled column.</span></span>  
  
### <a name="profile-type--column-value-distribution-profile"></a><span data-ttu-id="0beb7-167">プロファイルの種類 = 列の値分布プロファイル</span><span class="sxs-lookup"><span data-stu-id="0beb7-167">Profile Type = Column Value Distribution Profile</span></span>  
  
#### <a name="column-value-distribution-profile---column-pane"></a><span data-ttu-id="0beb7-168">列の値分布プロファイル - \<column> ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-168">Column Value Distribution Profile - \<column> pane</span></span>  
 <span data-ttu-id="0beb7-169">**[個別の値数]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-169">**Number of Distinct Values**</span></span>  
 <span data-ttu-id="0beb7-170">プロファイルされた列の個別の値数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-170">Displays the count of distinct values found in the profiled column.</span></span>  
  
 <span data-ttu-id="0beb7-171">**行数**</span><span class="sxs-lookup"><span data-stu-id="0beb7-171">**Row Count**</span></span>  
 <span data-ttu-id="0beb7-172">テーブルまたはビューの行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-172">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="detailed-value-distribution-pane"></a><span data-ttu-id="0beb7-173">[詳細な値分布] ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-173">Detailed Value Distribution pane</span></span>  
 <span data-ttu-id="0beb7-174">**Value**</span><span class="sxs-lookup"><span data-stu-id="0beb7-174">**Value**</span></span>  
 <span data-ttu-id="0beb7-175">プロファイルされた列の個別の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-175">Displays the distinct values found in the profiled column.</span></span>  
  
 <span data-ttu-id="0beb7-176">**Count**</span><span class="sxs-lookup"><span data-stu-id="0beb7-176">**Count**</span></span>  
 <span data-ttu-id="0beb7-177">プロファイルされた列の値が **[値]** 列に表示された値である行の数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-177">Displays the number of rows in which the profiled column has the value shown in the **Value** column.</span></span>  
  
 <span data-ttu-id="0beb7-178">**Percentage**</span><span class="sxs-lookup"><span data-stu-id="0beb7-178">**Percentage**</span></span>  
 <span data-ttu-id="0beb7-179">プロファイルされた列の値が **[値]** 列に表示された値である行の割合が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-179">Displays the percentage of rows in which the profiled column has the value shown in the **Value** column.</span></span>  
  
### <a name="profile-type--candidate-key-profile"></a><span data-ttu-id="0beb7-180">プロファイルの種類 = 候補キー プロファイル</span><span class="sxs-lookup"><span data-stu-id="0beb7-180">Profile Type = Candidate Key Profile</span></span>  
  
#### <a name="candidate-key-profile---table-pane"></a><span data-ttu-id="0beb7-181">候補キー プロファイル - \<table> ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-181">Candidate Key Profile - \<table> pane</span></span>  
 <span data-ttu-id="0beb7-182">**[キー列]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-182">**Key Columns**</span></span>  
 <span data-ttu-id="0beb7-183">プロファイル対象の候補キーとして選択した列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-183">Displays the columns that were selected for profiling as a candidate key.</span></span>  
  
 <span data-ttu-id="0beb7-184">**[キーの強さ]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-184">**Key Strength**</span></span>  
 <span data-ttu-id="0beb7-185">候補キーの列または列の組み合わせの強さがパーセンテージで表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-185">Displays the strength (as a percentage) of the candidate key column or combination of columns.</span></span> <span data-ttu-id="0beb7-186">キーの強さが 100% 未満である場合は、重複する値が存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="0beb7-186">A key strength of less than 100% indicates that duplicate values exist.</span></span>  
  
#### <a name="key-violations-pane"></a><span data-ttu-id="0beb7-187">[キー違反] ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-187">Key Violations pane</span></span>  
 <span data-ttu-id="0beb7-188">**\<column1>、\<column2> などです。**</span><span class="sxs-lookup"><span data-stu-id="0beb7-188">**\<column1>, \<column2>, etc.**</span></span>  
 <span data-ttu-id="0beb7-189">プロファイルされた列で見つかった重複する値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-189">Displays the duplicate values that were found in the profiled column.</span></span>  
  
 <span data-ttu-id="0beb7-190">**Count**</span><span class="sxs-lookup"><span data-stu-id="0beb7-190">**Count**</span></span>  
 <span data-ttu-id="0beb7-191">指定された列の値が最初の列に表示された値である行の数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-191">Displays the number of rows in which the specified column has the value shown in the first column.</span></span>  
  
### <a name="profile-type--functional-dependency-profile"></a><span data-ttu-id="0beb7-192">プロファイルの種類 = 機能依存プロファイル</span><span class="sxs-lookup"><span data-stu-id="0beb7-192">Profile Type = Functional Dependency Profile</span></span>  
  
#### <a name="functional-dependency-profile-pane"></a><span data-ttu-id="0beb7-193">[機能依存プロファイル] ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-193">Functional Dependency Profile pane</span></span>  
 <span data-ttu-id="0beb7-194">**[決定列]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-194">**Determinant Columns**</span></span>  
 <span data-ttu-id="0beb7-195">決定列として選択した列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-195">Displays the column or columns selected as the determinant column.</span></span> <span data-ttu-id="0beb7-196">米国郵便番号によって州が一意に決定される例の場合、郵便番号は決定列です。</span><span class="sxs-lookup"><span data-stu-id="0beb7-196">In the example where the same United States Zip Code should always have the same state, the Zip Code is the determinant column.</span></span>  
  
 <span data-ttu-id="0beb7-197">**[依存列]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-197">**Dependent Columns**</span></span>  
 <span data-ttu-id="0beb7-198">依存列として選択した列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-198">Displays the column or columns selected as the dependent column.</span></span> <span data-ttu-id="0beb7-199">米国郵便番号によって州が一意に決定される例の場合、州は依存列です。</span><span class="sxs-lookup"><span data-stu-id="0beb7-199">In the example where the same United States Zip Code should always have the same state, the state is the dependent column.</span></span>  
  
 <span data-ttu-id="0beb7-200">**[機能依存の強さ]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-200">**Functional Dependency Strength**</span></span>  
 <span data-ttu-id="0beb7-201">列間の機能依存の強さがパーセンテージで表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-201">Displays the strength (as a percentage) of the functional dependency between columns.</span></span> <span data-ttu-id="0beb7-202">キーの強さが 100% 未満である場合は、決定値によって依存値が決定されないケースがあることを示します。</span><span class="sxs-lookup"><span data-stu-id="0beb7-202">A key strength of less than 100% indicates that there are cases where the determinant value does not determine the dependent value.</span></span> <span data-ttu-id="0beb7-203">米国郵便番号によって州が一意に決定される例でキーの強さが 100% 未満である場合は、無効な値が州の列に含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="0beb7-203">In the example where the same United States Zip Code should always have the same state, this probably indicates some state values are not valid.</span></span>  
  
#### <a name="functional-dependency-violations-pane"></a><span data-ttu-id="0beb7-204">[機能依存違反] ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-204">Functional Dependency Violations pane</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0beb7-205">データに含まれるエラー値の割合が高いと、機能依存プロファイルの結果が予期しない結果になることがあります。</span><span class="sxs-lookup"><span data-stu-id="0beb7-205">A high percentage of erroneous values in the data could lead to unexpected results from a Functional Dependency profile.</span></span> <span data-ttu-id="0beb7-206">たとえば、"98052" という郵便番号の値に対応する州の値として "WI" という値が 90% の行に含まれている場合、</span><span class="sxs-lookup"><span data-stu-id="0beb7-206">For example, 90% of the rows have a State value of "WI" for a Postal Code value of "98052."</span></span> <span data-ttu-id="0beb7-207">機能依存プロファイルにより、正しい州の値である "WA" という値の行が違反として報告されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-207">The profile reports rows that contain the correct state value of "WA" as violations.</span></span>  
  
 **\<determinant column name>**  
 <span data-ttu-id="0beb7-208">違反が検出された機能依存の決定列または列の組み合わせの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-208">Displays the value of the determinant column or combination of columns in this instance of a functional dependency violation.</span></span>  
  
 **\<dependent column name>**  
 <span data-ttu-id="0beb7-209">違反が検出された機能依存の依存列の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-209">Displays the value of the dependent column in this instance of a functional dependency violation.</span></span>  
  
 <span data-ttu-id="0beb7-210">**サポート数 (Support Count)**</span><span class="sxs-lookup"><span data-stu-id="0beb7-210">**Support Count**</span></span>  
 <span data-ttu-id="0beb7-211">決定列の値によって依存列が決定される行の数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-211">Displays the number of rows in which the determinant column value determines the dependent column.</span></span>  
  
 <span data-ttu-id="0beb7-212">**[違反カウント]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-212">**Violation Count**</span></span>  
 <span data-ttu-id="0beb7-213">決定列の値によって依存列が決定されない行の数が表示されます</span><span class="sxs-lookup"><span data-stu-id="0beb7-213">Displays the number of rows in which the determinant column value does not determine the dependent column.</span></span> <span data-ttu-id="0beb7-214">(依存値が **\<dependent column name>** 列に表示された値である行)。</span><span class="sxs-lookup"><span data-stu-id="0beb7-214">(These are the rows where the dependent value is the value shown in the **\<dependent column name>** column.)</span></span>  
  
 <span data-ttu-id="0beb7-215">**サポート比率 (Support Percentage)**</span><span class="sxs-lookup"><span data-stu-id="0beb7-215">**Support Percentage**</span></span>  
 <span data-ttu-id="0beb7-216">決定列によって依存列が決定される行の割合が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-216">Displays the percentage of rows in which the determinant column determines the dependent column.</span></span>  
  
### <a name="profile-type--value-inclusion-profile"></a><span data-ttu-id="0beb7-217">プロファイルの種類 = 値包含プロファイル</span><span class="sxs-lookup"><span data-stu-id="0beb7-217">Profile Type = Value Inclusion Profile</span></span>  
  
#### <a name="value-inclusion-profile-pane"></a><span data-ttu-id="0beb7-218">[値包含プロファイル] ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-218">Value Inclusion Profile pane</span></span>  
 <span data-ttu-id="0beb7-219">**[サブセット側の列]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-219">**Subset Side Columns**</span></span>  
 <span data-ttu-id="0beb7-220">スーパーセット列の一部であるかどうかを判断するためにプロファイルされた列または列の組み合わせが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-220">Displays the column or combination of columns that were profiled to determine whether they are in the superset columns.</span></span>  
  
 <span data-ttu-id="0beb7-221">**[スーパーセット側の列]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-221">**Superset Side Columns**</span></span>  
 <span data-ttu-id="0beb7-222">サブセット列の値が含まれているかどうかを判断するためにプロファイルされた列または列の組み合わせが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-222">Displays the column or combination of columns that were profiled to determine whether they include the values in the subset columns.</span></span>  
  
 <span data-ttu-id="0beb7-223">**[包含の強さ]**</span><span class="sxs-lookup"><span data-stu-id="0beb7-223">**Inclusion Strength**</span></span>  
 <span data-ttu-id="0beb7-224">列間の重複の強さがパーセンテージで表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-224">Displays the strength (as a percentage) of the overlap between columns.</span></span> <span data-ttu-id="0beb7-225">キーの強さが 100% 未満である場合は、サブセットの値がスーパーセットの値の中に含まれていないケースがあることを示します。</span><span class="sxs-lookup"><span data-stu-id="0beb7-225">A key strength of less than 100% indicates that there are cases where the subset value is not found among the superset values.</span></span>  
  
#### <a name="inclusion-violations-pane"></a><span data-ttu-id="0beb7-226">[包含違反] ペイン</span><span class="sxs-lookup"><span data-stu-id="0beb7-226">Inclusion Violations pane</span></span>  
 <span data-ttu-id="0beb7-227">**\<column1>、\<column2> などです。**</span><span class="sxs-lookup"><span data-stu-id="0beb7-227">**\<column1>, \<column2>, etc.**</span></span>  
 <span data-ttu-id="0beb7-228">スーパーセット列に含まれていないサブセット列の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-228">Displays the values in the subset column or columns that were not found in the superset column or columns.</span></span>  
  
 <span data-ttu-id="0beb7-229">**Count**</span><span class="sxs-lookup"><span data-stu-id="0beb7-229">**Count**</span></span>  
 <span data-ttu-id="0beb7-230">指定された列の値が最初の列に表示された値である行の数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0beb7-230">Displays the number of rows in which the specified column has the value shown in the first column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0beb7-231">参照</span><span class="sxs-lookup"><span data-stu-id="0beb7-231">See Also</span></span>  
 <span data-ttu-id="0beb7-232">[Data Profile Viewer](control-flow/data-profile-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="0beb7-232">[Data Profile Viewer](control-flow/data-profile-viewer.md) </span></span>  
 [<span data-ttu-id="0beb7-233">データ プロファイル タスクとビューアー</span><span class="sxs-lookup"><span data-stu-id="0beb7-233">Data Profiling Task and Viewer</span></span>](control-flow/data-profiling-task-and-viewer.md)  
  
  
