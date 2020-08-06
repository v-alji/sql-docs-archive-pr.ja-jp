---
title: マージ結合変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergejointransformation.f1
helpviewer_keywords:
- Merge Join Transformation Editor
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0d15d1233c2e0ff836e9dbd17459e56c48183f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642167"
---
# <a name="merge-join-transformation-editor"></a><span data-ttu-id="296de-102">マージ結合変換エディター</span><span class="sxs-lookup"><span data-stu-id="296de-102">Merge Join Transformation Editor</span></span>
  <span data-ttu-id="296de-103">**[マージ結合変換エディター]** ダイアログ ボックスを使用すると、結合の種類、結合列、および結合によって組み合わされた 2 つの入力をマージするための出力列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="296de-103">Use the **Merge Join Transformation Editor** dialog box to specify the join type, the join columns, and the output columns for merging two inputs combined by a join.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="296de-104">マージ結合変換では、入力データが並べ替えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="296de-104">The Merge Join Transformation requires sorted data for its inputs.</span></span> <span data-ttu-id="296de-105">この重要な要件の詳細については、「 [マージ変換およびマージ結合変換用にデータを並べ替える](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="296de-105">For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
 <span data-ttu-id="296de-106">マージ結合変換の詳細については、「 [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="296de-106">To learn more about the Merge Join transformation, see [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="296de-107">Options</span><span class="sxs-lookup"><span data-stu-id="296de-107">Options</span></span>  
 <span data-ttu-id="296de-108">**結合の種類**</span><span class="sxs-lookup"><span data-stu-id="296de-108">**Join type**</span></span>  
 <span data-ttu-id="296de-109">内部結合、左外部結合、または完全結合を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="296de-109">Specify whether you want to use an inner join, left outer join, or full join.</span></span>  
  
 <span data-ttu-id="296de-110">**[入力の入れ替え]**</span><span class="sxs-lookup"><span data-stu-id="296de-110">**Swap Inputs**</span></span>  
 <span data-ttu-id="296de-111">**[入力の入れ替え]** ボタンを使用して、入力間の順序を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="296de-111">Switch the order between inputs by using the **Swap Inputs** button.</span></span> <span data-ttu-id="296de-112">この選択は、左外部結合オプションで使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="296de-112">This selection may be useful with the Left outer join option.</span></span>  
  
 <span data-ttu-id="296de-113">**入力**</span><span class="sxs-lookup"><span data-stu-id="296de-113">**Input**</span></span>  
 <span data-ttu-id="296de-114">出力をマージする各列は、使用できる入力の一覧から最初に選択します。</span><span class="sxs-lookup"><span data-stu-id="296de-114">For each column that you want in the merged output, first select from the list of available inputs.</span></span>  
  
 <span data-ttu-id="296de-115">入力は 2 つの個別のテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="296de-115">Inputs are displayed in two separate tables.</span></span> <span data-ttu-id="296de-116">出力に含める列を選択します。</span><span class="sxs-lookup"><span data-stu-id="296de-116">Select columns to include in the output.</span></span> <span data-ttu-id="296de-117">テーブル間の結合を作成する列をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="296de-117">Drag columns to create a join between the tables.</span></span> <span data-ttu-id="296de-118">結合を削除するには、選択してから Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="296de-118">To delete a join, select it and then press the DELETE key.</span></span>  
  
 <span data-ttu-id="296de-119">**入力列**</span><span class="sxs-lookup"><span data-stu-id="296de-119">**Input Column**</span></span>  
 <span data-ttu-id="296de-120">選択した入力の使用できる列の一覧からマージする出力に含める列を選択します。</span><span class="sxs-lookup"><span data-stu-id="296de-120">Select a column to include in the merged output from the list of available columns on the selected input.</span></span>  
  
 <span data-ttu-id="296de-121">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="296de-121">**Output Alias**</span></span>  
 <span data-ttu-id="296de-122">各出力列の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="296de-122">Type an alias for each output column.</span></span> <span data-ttu-id="296de-123">既定は入力列の名前です。一意のわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="296de-123">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296de-124">参照</span><span class="sxs-lookup"><span data-stu-id="296de-124">See Also</span></span>  
 <span data-ttu-id="296de-125">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="296de-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="296de-126">[マージ変換およびマージ結合変換のデータの並べ替え](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="296de-126">[Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md) </span></span>  
 <span data-ttu-id="296de-127">[マージ結合変換を使用してデータセットを拡張する](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="296de-127">[Extend a Dataset by Using the Merge Join Transformation](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md) </span></span>  
 <span data-ttu-id="296de-128">[マージ変換](data-flow/transformations/merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="296de-128">[Merge Transformation](data-flow/transformations/merge-transformation.md) </span></span>  
 [<span data-ttu-id="296de-129">全体結合変換</span><span class="sxs-lookup"><span data-stu-id="296de-129">Union All Transformation</span></span>](data-flow/transformations/union-all-transformation.md)  
  
  
