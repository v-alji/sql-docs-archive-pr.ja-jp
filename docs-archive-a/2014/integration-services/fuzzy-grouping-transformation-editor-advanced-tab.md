---
title: '[あいまいグループ化変換エディター] ([詳細設定] タブ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f5dd05eda56b4818914f659734eb3cdfb20c4d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633898"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a><span data-ttu-id="6102b-102">[あいまいグループ化変換エディター] ([詳細設定] タブ)</span><span class="sxs-lookup"><span data-stu-id="6102b-102">Fuzzy Grouping Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="6102b-103">**[あいまいグループ化変換エディター]** ダイアログ ボックスの **[詳細設定]** タブを使用すると、入力列と出力列の指定、類似性のしきい値の設定、区切り記号の定義ができます。</span><span class="sxs-lookup"><span data-stu-id="6102b-103">Use the **Advanced** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify input and output columns, set similarity thresholds, and define delimiters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6102b-104">`Exhaustive` `MaxMemoryUsage` あいまいグループ化変換のおよびプロパティは、[**あいまいグループ化変換エディター**] では使用できませんが、**詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="6102b-104">The `Exhaustive` and the `MaxMemoryUsage` properties of the Fuzzy Grouping transformation are not available in the **Fuzzy Grouping Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="6102b-105">これらのプロパティの詳細については、「 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)」の「あいまいグループ化変換」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6102b-105">For more information on these properties, see the Fuzzy Grouping Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="6102b-106">あいまいグループ化変換の詳細については、「 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6102b-106">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6102b-107">Options</span><span class="sxs-lookup"><span data-stu-id="6102b-107">Options</span></span>  
 <span data-ttu-id="6102b-108">**[入力キー列名]**</span><span class="sxs-lookup"><span data-stu-id="6102b-108">**Input key column name**</span></span>  
 <span data-ttu-id="6102b-109">各入力行の一意の識別子を含む、出力列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6102b-109">Specify the name of an output column that contains the unique identifier for each input row.</span></span> <span data-ttu-id="6102b-110">[`_key_in`] 列は各行を一意に識別する値を持ちます。</span><span class="sxs-lookup"><span data-stu-id="6102b-110">The `_key_in` column has a value that uniquely identifies each row.</span></span>  
  
 <span data-ttu-id="6102b-111">**[出力キー列名]**</span><span class="sxs-lookup"><span data-stu-id="6102b-111">**Output key column name**</span></span>  
 <span data-ttu-id="6102b-112">重複する行グループの正規行の一意識別子を含む、出力列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6102b-112">Specify the name of an output column that contains the unique identifier for the canonical row of a group of duplicate rows.</span></span> <span data-ttu-id="6102b-113">[`_key_out`] 列は、正規データ行の `_key_in` 値に対応します。</span><span class="sxs-lookup"><span data-stu-id="6102b-113">The `_key_out` column corresponds to the `_key_in` value of the canonical data row.</span></span>  
  
 <span data-ttu-id="6102b-114">**[類似性スコアの列名]**</span><span class="sxs-lookup"><span data-stu-id="6102b-114">**Similarity score column name**</span></span>  
 <span data-ttu-id="6102b-115">類似性スコアを含む列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6102b-115">Specify a name for the column that contains the similarity score.</span></span> <span data-ttu-id="6102b-116">類似性スコアは、正規行に対する入力行の類似性を示す、0 ～ 1 の間の値です。</span><span class="sxs-lookup"><span data-stu-id="6102b-116">The similarity score is a value between 0 and 1 that indicates the similarity of the input row to the canonical row.</span></span> <span data-ttu-id="6102b-117">スコアが 1 に近いほど、その行と正規行との類似性が高いことを示しています。</span><span class="sxs-lookup"><span data-stu-id="6102b-117">The closer the score is to 1, the more closely the row matches the canonical row.</span></span>  
  
 <span data-ttu-id="6102b-118">**[類似性のしきい値]**</span><span class="sxs-lookup"><span data-stu-id="6102b-118">**Similarity threshold**</span></span>  
 <span data-ttu-id="6102b-119">スライダーを使用して類似性のしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="6102b-119">Set the similarity threshold by using the slider.</span></span> <span data-ttu-id="6102b-120">しきい値が 1 に近づくと、より類似性が高い行どうしのみが重複として扱われるようになります。</span><span class="sxs-lookup"><span data-stu-id="6102b-120">The closer the threshold is to 1, the more the rows must resemble each other to qualify as duplicates.</span></span> <span data-ttu-id="6102b-121">しきい値を増加させると候補レコードとして処理対象になる数が少なくなるため、一致処理の速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="6102b-121">Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.</span></span>  
  
 <span data-ttu-id="6102b-122">**[トークン区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="6102b-122">**Token delimiters**</span></span>  
 <span data-ttu-id="6102b-123">変換により、トークンにするデータの区切り記号の既定のセットが提供されます。必要に応じて、一覧を編集して区切り記号の追加や削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6102b-123">The transformation provides a default set of delimiters for tokenizing data, but you can add or remove delimiters as needed by editing the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6102b-124">参照</span><span class="sxs-lookup"><span data-stu-id="6102b-124">See Also</span></span>  
 <span data-ttu-id="6102b-125">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6102b-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="6102b-126">あいまいグループ化変換を使用して類似のデータ行を識別する</span><span class="sxs-lookup"><span data-stu-id="6102b-126">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
