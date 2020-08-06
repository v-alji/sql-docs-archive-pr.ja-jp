---
title: '[リレーションシップの作成] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.createrelationships.f1
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a1095e193587ae7d416311031e5297a035ca37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633918"
---
# <a name="create-relationships"></a><span data-ttu-id="46cf9-102">[リレーションシップの作成]</span><span class="sxs-lookup"><span data-stu-id="46cf9-102">Create Relationships</span></span>
  <span data-ttu-id="46cf9-103">**[リレーションシップの作成]** ダイアログ ボックスを使用すると、[あいまい参照変換エディター]、[参照変換エディター]、および [用語参照変換エディター] で設定したソース列と参照テーブル列の間のマッピングを編集できます。</span><span class="sxs-lookup"><span data-stu-id="46cf9-103">Use the **Create Relationships** dialog box to edit mappings between the source columns and the lookup table columns that you configured in the Fuzzy Lookup Transformation Editor, the Lookup Transformation Editor, and the Term Lookup Transformation Editor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46cf9-104">**[リレーションシップの作成]** ダイアログ ボックスを [用語参照変換エディター] から開いた場合、 **[入力列]** と **[参照列]** の一覧のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="46cf9-104">The **Create Relationships** dialog box displays only the **Input Column** and **Lookup Column** lists when invoked from the Term Lookup Transformation Editor.</span></span>  
  
 <span data-ttu-id="46cf9-105">**[リレーションシップの作成]** ダイアログ ボックスを使用した変換の詳細については、「 [Fuzzy Lookup Transformation](lookup-transformation.md)」、「 [Lookup Transformation](lookup-transformation.md)」、および「 [Term Lookup Transformation](term-lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46cf9-105">To learn more about the transformations that use the **Create Relationships** dialog box, see [Fuzzy Lookup Transformation](lookup-transformation.md), [Lookup Transformation](lookup-transformation.md), and [Term Lookup Transformation](term-lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="46cf9-106">オプション</span><span class="sxs-lookup"><span data-stu-id="46cf9-106">Options</span></span>  
 <span data-ttu-id="46cf9-107">**入力列**</span><span class="sxs-lookup"><span data-stu-id="46cf9-107">**Input Column**</span></span>  
 <span data-ttu-id="46cf9-108">使用できる入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="46cf9-108">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="46cf9-109">**参照列**</span><span class="sxs-lookup"><span data-stu-id="46cf9-109">**Lookup Column**</span></span>  
 <span data-ttu-id="46cf9-110">使用できる参照列の一覧から列を選択します。</span><span class="sxs-lookup"><span data-stu-id="46cf9-110">Select from the list of available lookup columns.</span></span>  
  
 <span data-ttu-id="46cf9-111">**マッピングの種類**</span><span class="sxs-lookup"><span data-stu-id="46cf9-111">**Mapping Type**</span></span>  
 <span data-ttu-id="46cf9-112">あいまい一致と完全一致のどちらかを指定します。</span><span class="sxs-lookup"><span data-stu-id="46cf9-112">Select fuzzy or exact matching.</span></span>  
  
 <span data-ttu-id="46cf9-113">あいまい一致を使用するときには、すべての列にわたって行が十分に類似している場合に行が重複していると見なされます。</span><span class="sxs-lookup"><span data-stu-id="46cf9-113">When you use fuzzy matching, rows are considered duplicates if they are sufficiently similar across all columns that have a fuzzy match type.</span></span> <span data-ttu-id="46cf9-114">あいまい一致により得られる結果を改善するために、一部の列であいまい一致ではなく完全一致を使用するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="46cf9-114">To obtain better results from fuzzy matching, you can specify that some columns should use exact matching instead of fuzzy matching.</span></span> <span data-ttu-id="46cf9-115">たとえば、特定の列にエラーや矛盾がないことがわかっている場合は、その列に対して完全一致を指定できます。この列に同一の値が含まれている行のみ、重複している可能性があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="46cf9-115">For example, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column, so that only rows which contain identical values in this column are considered as possible duplicates.</span></span> <span data-ttu-id="46cf9-116">これにより、他の列におけるあいまい一致の正確性が高まります。</span><span class="sxs-lookup"><span data-stu-id="46cf9-116">This increases the accuracy of fuzzy matching on other columns.</span></span>  
  
 <span data-ttu-id="46cf9-117">**[比較フラグ]**</span><span class="sxs-lookup"><span data-stu-id="46cf9-117">**Comparison Flags**</span></span>  
 <span data-ttu-id="46cf9-118">文字列比較オプションについては、「 [文字列データの比較](../comparing-string-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46cf9-118">For information about the string comparison options, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="46cf9-119">**[最小類似]**</span><span class="sxs-lookup"><span data-stu-id="46cf9-119">**Minimum Similarity**</span></span>  
 <span data-ttu-id="46cf9-120">スライダーを使用して、類似のしきい値を列レベルで設定します。</span><span class="sxs-lookup"><span data-stu-id="46cf9-120">Set the similarity threshold at the column level by using the slider.</span></span> <span data-ttu-id="46cf9-121">参照元の値と参照先の値が一致すると見なされるためには、この値が 1 に近いほど高い類似性が要求されます。</span><span class="sxs-lookup"><span data-stu-id="46cf9-121">The closer the value is to 1, the more the lookup value must resemble the source value to qualify as a match.</span></span> <span data-ttu-id="46cf9-122">しきい値を増加させると候補レコードとして処理対象になる数が少なくなるため、一致処理の速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="46cf9-122">Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.</span></span>  
  
 <span data-ttu-id="46cf9-123">**[類似出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="46cf9-123">**Similarity Output Alias**</span></span>  
 <span data-ttu-id="46cf9-124">選択された列の類似スコアを格納する、新しい出力列に付ける名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="46cf9-124">Specify the name for a new output column that contains the similarity scores for the selected column.</span></span> <span data-ttu-id="46cf9-125">この値を空にした場合、出力列は作成されません。</span><span class="sxs-lookup"><span data-stu-id="46cf9-125">If you leave this value empty, the output column is not created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cf9-126">参照</span><span class="sxs-lookup"><span data-stu-id="46cf9-126">See Also</span></span>  
 <span data-ttu-id="46cf9-127">[Integration Services のエラーおよびメッセージのリファレンス](../../integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="46cf9-127">[Integration Services Error and Message Reference](../../integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="46cf9-128">[あいまい参照変換エディター &#40;[列] タブ&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md) </span><span class="sxs-lookup"><span data-stu-id="46cf9-128">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md) </span></span>  
 <span data-ttu-id="46cf9-129">[[参照変換エディター] &#40;[列] ページ&#41;](../../lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="46cf9-129">[Lookup Transformation Editor &#40;Columns Page&#41;](../../lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="46cf9-130">[用語参照変換エディター ([用語参照] タブ)](../../term-lookup-transformation-editor-term-lookup-tab.md)</span><span class="sxs-lookup"><span data-stu-id="46cf9-130">[Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;](../../term-lookup-transformation-editor-term-lookup-tab.md)</span></span>  
  
  
