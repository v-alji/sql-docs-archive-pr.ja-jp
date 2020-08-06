---
title: '[あいまい参照変換エディター] ([列] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9294022b52536940916a381d7b811437eaa5814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713306"
---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a><span data-ttu-id="c6054-102">[あいまい参照変換エディター] ([列] タブ)</span><span class="sxs-lookup"><span data-stu-id="c6054-102">Fuzzy Lookup Transformation Editor (Columns Tab)</span></span>
  <span data-ttu-id="c6054-103">**[あいまい参照変換エディター]** ダイアログ ボックスの **[列]** タブを使用すると、入力列および出力列のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="c6054-103">Use the **Columns** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set properties for input and output columns.</span></span>  
  
 <span data-ttu-id="c6054-104">あいまい参照変換の詳細については、「 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6054-104">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c6054-105">Options</span><span class="sxs-lookup"><span data-stu-id="c6054-105">Options</span></span>  
 <span data-ttu-id="c6054-106">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="c6054-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="c6054-107">入力列をドラッグして、使用できる参照列に接続します。</span><span class="sxs-lookup"><span data-stu-id="c6054-107">Drag input columns to connect them to available lookup columns.</span></span> <span data-ttu-id="c6054-108">これらの列は、サポートされているデータ型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6054-108">These columns must have matching, supported data types.</span></span> <span data-ttu-id="c6054-109">マッピングする行を選択して右クリックし、 [[リレーションシップの作成]](data-flow/transformations/create-relationships.md) ダイアログ ボックスでマッピングを編集します。</span><span class="sxs-lookup"><span data-stu-id="c6054-109">Select a mapping line and right-click to edit the mappings in the [Create Relationships](data-flow/transformations/create-relationships.md) dialog box.</span></span>  
  
 <span data-ttu-id="c6054-110">**名前**</span><span class="sxs-lookup"><span data-stu-id="c6054-110">**Name**</span></span>  
 <span data-ttu-id="c6054-111">使用可能な入力列の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6054-111">View the names of the available input columns.</span></span>  
  
 <span data-ttu-id="c6054-112">**[パススルー]**</span><span class="sxs-lookup"><span data-stu-id="c6054-112">**Pass Through**</span></span>  
 <span data-ttu-id="c6054-113">変換先の出力に入力列を含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6054-113">Specify whether to include the input columns in the output of the transformation.</span></span>  
  
 <span data-ttu-id="c6054-114">**使用できる参照列**</span><span class="sxs-lookup"><span data-stu-id="c6054-114">**Available Lookup Columns**</span></span>  
 <span data-ttu-id="c6054-115">チェック ボックスを使用して、あいまい参照操作を実行する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6054-115">Use the check boxes to select columns on which to perform fuzzy lookup operations.</span></span>  
  
 <span data-ttu-id="c6054-116">**参照列**</span><span class="sxs-lookup"><span data-stu-id="c6054-116">**Lookup Column**</span></span>  
 <span data-ttu-id="c6054-117">使用できる参照テーブル列の一覧から参照列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6054-117">Select lookup columns from the list of available reference table columns.</span></span> <span data-ttu-id="c6054-118">選択内容が **[使用できる参照列]** テーブルのチェック ボックスに反映されます。</span><span class="sxs-lookup"><span data-stu-id="c6054-118">Your selections are reflected in the check box selections in the **Available Lookup Columns** table.</span></span> <span data-ttu-id="c6054-119">**[使用できる参照列]** テーブルの列を選択すると、返される一致行ごとに参照テーブル列の値を含む出力列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c6054-119">Selecting a column in the **Available Lookup Columns** table creates an output column that contains the reference table column value for each matching row returned.</span></span>  
  
 <span data-ttu-id="c6054-120">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="c6054-120">**Output Alias**</span></span>  
 <span data-ttu-id="c6054-121">各参照列の出力の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="c6054-121">Type an alias for the output for each lookup column.</span></span> <span data-ttu-id="c6054-122">既定では、参照列の名前に数値のインデックス値が追加されます。一意のわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="c6054-122">The default is the name of the lookup column with a numeric index value appended; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6054-123">参照</span><span class="sxs-lookup"><span data-stu-id="c6054-123">See Also</span></span>  
 <span data-ttu-id="c6054-124">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c6054-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c6054-125">[[あいまい参照変換エディター] &#40;[参照テーブル] タブ&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="c6054-125">[Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 <span data-ttu-id="c6054-126">[[あいまい参照変換エディター] &#40;[詳細設定] タブ&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)</span><span class="sxs-lookup"><span data-stu-id="c6054-126">[Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)</span></span>  
  
  
