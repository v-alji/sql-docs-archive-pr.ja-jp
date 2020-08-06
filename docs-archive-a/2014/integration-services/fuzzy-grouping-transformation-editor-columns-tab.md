---
title: '[あいまいグループ化変換エディター] ([列] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.columns.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 24f4539f-2a9f-4acd-acc7-06228a07f7df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d3aef9c30a81760b7f09378a8ecd66fee0dac62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713309"
---
# <a name="fuzzy-grouping-transformation-editor-columns-tab"></a><span data-ttu-id="02e80-102">[あいまいグループ化変換エディター] ([列] タブ)</span><span class="sxs-lookup"><span data-stu-id="02e80-102">Fuzzy Grouping Transformation Editor (Columns Tab)</span></span>
  <span data-ttu-id="02e80-103">**[あいまいグループ化変換エディター]** ダイアログ ボックスの **[列]** タブを使用すると、重複する値を持つ行をグループ化するための列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="02e80-103">Use the **Columns** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify the columns used to group rows with duplicate values.</span></span>  
  
 <span data-ttu-id="02e80-104">あいまいグループ化変換の詳細については、「 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02e80-104">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="02e80-105">Options</span><span class="sxs-lookup"><span data-stu-id="02e80-105">Options</span></span>  
 <span data-ttu-id="02e80-106">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="02e80-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="02e80-107">重複する値を持つ行をグループ化するために使用する入力列を、この一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="02e80-107">Select from this list the input columns used to group rows with duplicate values.</span></span>  
  
 <span data-ttu-id="02e80-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="02e80-108">**Name**</span></span>  
 <span data-ttu-id="02e80-109">使用できる入力列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="02e80-109">View the names of available input columns.</span></span>  
  
 <span data-ttu-id="02e80-110">**[パススルー]**</span><span class="sxs-lookup"><span data-stu-id="02e80-110">**Pass Through**</span></span>  
 <span data-ttu-id="02e80-111">入力列を変換の出力に含めるかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="02e80-111">Select whether to include the input column in the output of the transformation.</span></span> <span data-ttu-id="02e80-112">グループ化に使用されるすべての列は、自動的に出力にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="02e80-112">All columns used for grouping are automatically copied to the output.</span></span> <span data-ttu-id="02e80-113">この列を選択することによって、追加の列を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="02e80-113">You can include additional columns by checking this column.</span></span>  
  
 <span data-ttu-id="02e80-114">**入力列**</span><span class="sxs-lookup"><span data-stu-id="02e80-114">**Input Column**</span></span>  
 <span data-ttu-id="02e80-115">**[使用できる入力列]** の一覧で選択されている入力列の 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="02e80-115">Select one of the input columns selected earlier in the **Available Input Columns** list.</span></span>  
  
 <span data-ttu-id="02e80-116">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="02e80-116">**Output Alias**</span></span>  
 <span data-ttu-id="02e80-117">対応する出力列に付けるわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="02e80-117">Enter a descriptive name for the corresponding output column.</span></span> <span data-ttu-id="02e80-118">既定では、出力列名は入力列名と同じになります。</span><span class="sxs-lookup"><span data-stu-id="02e80-118">By default, the output column name is the same as the input column name.</span></span>  
  
 <span data-ttu-id="02e80-119">**[グループ出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="02e80-119">**Group Output Alias**</span></span>  
 <span data-ttu-id="02e80-120">グループ化された重複の標準の値を含む列に付けるわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="02e80-120">Enter a descriptive name for the column that will contain the canonical value for the grouped duplicates.</span></span> <span data-ttu-id="02e80-121">この出力列の既定の名前は、入力列名に _clean を付けた名前です。</span><span class="sxs-lookup"><span data-stu-id="02e80-121">The default name of this output column is the input column name with _clean appended.</span></span>  
  
 <span data-ttu-id="02e80-122">**[一致の種類]**</span><span class="sxs-lookup"><span data-stu-id="02e80-122">**Match Type**</span></span>  
 <span data-ttu-id="02e80-123">あいまい一致と完全一致のどちらかを指定します。</span><span class="sxs-lookup"><span data-stu-id="02e80-123">Select fuzzy or exact matching.</span></span> <span data-ttu-id="02e80-124">あいまい一致の場合、行は、すべての列にわたって行が十分に類似している場合に重複していると見なされます。</span><span class="sxs-lookup"><span data-stu-id="02e80-124">Rows are considered duplicates if they are sufficiently similar across all columns with a fuzzy match type.</span></span> <span data-ttu-id="02e80-125">さらに、特定の列に対して完全一致を指定した場合、完全一致列内で同一の値を含む行だけが、重複の可能性があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="02e80-125">If you also specify exact matching on certain columns, only rows that contain identical values in the exact matching columns are considered as possible duplicates.</span></span> <span data-ttu-id="02e80-126">したがって、特定の列にエラーや矛盾がないことがわかっている場合は、その列に対して完全一致を指定して、他の列でのあいまい一致の精度を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="02e80-126">Therefore, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column to increase the accuracy of the fuzzy matching on other columns.</span></span>  
  
 <span data-ttu-id="02e80-127">**[最小類似]**</span><span class="sxs-lookup"><span data-stu-id="02e80-127">**Minimum Similarity**</span></span>  
 <span data-ttu-id="02e80-128">スライダーを使用して、類似のしきい値を結合レベルで設定します。</span><span class="sxs-lookup"><span data-stu-id="02e80-128">Set the similarity threshold at the join level by using the slider.</span></span> <span data-ttu-id="02e80-129">値を 1 に近づけるほど、参照元の値と参照先の値との類似性が高くなければ一致しないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="02e80-129">The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match.</span></span> <span data-ttu-id="02e80-130">しきい値を大きくすると、照合の対象となるレコードが少なくなるため、照合の速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="02e80-130">Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.</span></span>  
  
 <span data-ttu-id="02e80-131">**[類似出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="02e80-131">**Similarity Output Alias**</span></span>  
 <span data-ttu-id="02e80-132">選択された結合の類似スコアを格納する、新しい出力列に付ける名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="02e80-132">Specify the name for a new output column that contains the similarity scores for the selected join.</span></span> <span data-ttu-id="02e80-133">この値を空にした場合、出力列は作成されません。</span><span class="sxs-lookup"><span data-stu-id="02e80-133">If you leave this value empty, the output column is not created.</span></span>  
  
 <span data-ttu-id="02e80-134">**[数字]**</span><span class="sxs-lookup"><span data-stu-id="02e80-134">**Numerals**</span></span>  
 <span data-ttu-id="02e80-135">列データを比較する際の先頭および末尾の数字の有意性を指定します。</span><span class="sxs-lookup"><span data-stu-id="02e80-135">Specify the significance of leading and trailing numerals in comparing the column data.</span></span> <span data-ttu-id="02e80-136">たとえば、先頭の数字が有意である場合、"123 Main Street" は "456 Main Street" と同じグループとは見なされません。</span><span class="sxs-lookup"><span data-stu-id="02e80-136">For example, if leading numerals are significant, "123 Main Street" will not be grouped with "456 Main Street."</span></span>  
  
|<span data-ttu-id="02e80-137">値</span><span class="sxs-lookup"><span data-stu-id="02e80-137">Value</span></span>|<span data-ttu-id="02e80-138">説明</span><span class="sxs-lookup"><span data-stu-id="02e80-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02e80-139">**どちらもオフ**</span><span class="sxs-lookup"><span data-stu-id="02e80-139">**Neither**</span></span>|<span data-ttu-id="02e80-140">先頭および末尾の数字は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="02e80-140">Leading and trailing numerals are not significant.</span></span>|  
|<span data-ttu-id="02e80-141">**最高**</span><span class="sxs-lookup"><span data-stu-id="02e80-141">**Leading**</span></span>|<span data-ttu-id="02e80-142">先頭の数字のみが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="02e80-142">Only leading numerals are significant.</span></span>|  
|<span data-ttu-id="02e80-143">**[Trailing]**</span><span class="sxs-lookup"><span data-stu-id="02e80-143">**Trailing**</span></span>|<span data-ttu-id="02e80-144">末尾の数字のみが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="02e80-144">Only trailing numerals are significant.</span></span>|  
|<span data-ttu-id="02e80-145">**[Leading and Trailing]**</span><span class="sxs-lookup"><span data-stu-id="02e80-145">**LeadingAndTrailing**</span></span>|<span data-ttu-id="02e80-146">先頭および末尾の両方の数字が考慮されます。</span><span class="sxs-lookup"><span data-stu-id="02e80-146">Both leading and trailing numerals are significant.</span></span>|  
  
 <span data-ttu-id="02e80-147">**[比較フラグ]**</span><span class="sxs-lookup"><span data-stu-id="02e80-147">**Comparison Flags**</span></span>  
 <span data-ttu-id="02e80-148">文字列比較オプションについては、「 [文字列データの比較](data-flow/comparing-string-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02e80-148">For information about the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e80-149">参照</span><span class="sxs-lookup"><span data-stu-id="02e80-149">See Also</span></span>  
 <span data-ttu-id="02e80-150">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="02e80-150">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="02e80-151">あいまいグループ化変換を使用して類似のデータ行を識別する</span><span class="sxs-lookup"><span data-stu-id="02e80-151">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
