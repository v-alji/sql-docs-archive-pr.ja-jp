---
title: 並べ替え変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttransformation.f1
helpviewer_keywords:
- Sort Transformation Editor
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f48c366f4337af29b03877f6bb20b804457a293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742350"
---
# <a name="sort-transformation-editor"></a><span data-ttu-id="ea1ef-102">並べ替え変換エディター</span><span class="sxs-lookup"><span data-stu-id="ea1ef-102">Sort Transformation Editor</span></span>
  <span data-ttu-id="ea1ef-103">**[並べ替え変換エディター]** ダイアログ ボックスを使用すると、並べ替える列を選択し、並べ替え順を設定して、重複する部分を削除するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-103">Use the **Sort Transformation Editor** dialog box to select the columns to sort, set the sort order, and specify whether duplicates are removed.</span></span>  
  
 <span data-ttu-id="ea1ef-104">並べ替え変換の詳細については、「 [Sort Transformation](data-flow/transformations/sort-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-104">To learn more about the Sort transformation, see [Sort Transformation](data-flow/transformations/sort-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ea1ef-105">Options</span><span class="sxs-lookup"><span data-stu-id="ea1ef-105">Options</span></span>  
 <span data-ttu-id="ea1ef-106">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="ea1ef-107">このチェック ボックスを使用して、並べ替える列を指定します。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-107">Using the check boxes, specify the columns to sort.</span></span>  
  
 <span data-ttu-id="ea1ef-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-108">**Name**</span></span>  
 <span data-ttu-id="ea1ef-109">使用できる各入力列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-109">View the name of each available input column.</span></span>  
  
 <span data-ttu-id="ea1ef-110">**パススルー**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-110">**Passthrough**</span></span>  
 <span data-ttu-id="ea1ef-111">並べ替えられる出力に列が含まれるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-111">Indicate whether to include the column in the sorted output.</span></span>  
  
 <span data-ttu-id="ea1ef-112">**入力列**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-112">**Input Column**</span></span>  
 <span data-ttu-id="ea1ef-113">各行に対して使用できる入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-113">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="ea1ef-114">選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-114">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="ea1ef-115">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-115">**Output Alias**</span></span>  
 <span data-ttu-id="ea1ef-116">各出力列の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-116">Type an alias for each output column.</span></span> <span data-ttu-id="ea1ef-117">既定は入力列の名前です。一意のわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-117">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="ea1ef-118">**[並べ替えの種類]**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-118">**Sort Type**</span></span>  
 <span data-ttu-id="ea1ef-119">昇順で並べ替えるか、降順で並べ替えるかを示します。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-119">Indicate whether to sort in ascending or descending order.</span></span>  
  
 <span data-ttu-id="ea1ef-120">**[並べ替え順序]**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-120">**Sort Order**</span></span>  
 <span data-ttu-id="ea1ef-121">列を並べ替える順序を示します。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-121">Indicate the order in which to sort columns.</span></span> <span data-ttu-id="ea1ef-122">各列に対して手動で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-122">This must be set manually for each column.</span></span>  
  
 <span data-ttu-id="ea1ef-123">**[比較フラグ]**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-123">**Comparison Flags**</span></span>  
 <span data-ttu-id="ea1ef-124">文字列比較オプションについては、「 [文字列データの比較](data-flow/comparing-string-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-124">For information about the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="ea1ef-125">**[重複した並べ替え値を含む行を削除する]**</span><span class="sxs-lookup"><span data-stu-id="ea1ef-125">**Remove rows with duplicate sort values**</span></span>  
 <span data-ttu-id="ea1ef-126">指定された文字列比較オプションに基づいて、重複した列を変換出力にコピーするか、すべての重複部分に対して 1 つのエントリを作成するかを示します。</span><span class="sxs-lookup"><span data-stu-id="ea1ef-126">Indicate whether the transformation copies duplicate rows to the transformation output, or creates a single entry for all duplicates, based on the specified string comparison options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1ef-127">参照</span><span class="sxs-lookup"><span data-stu-id="ea1ef-127">See Also</span></span>  
 [<span data-ttu-id="ea1ef-128">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="ea1ef-128">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
