---
title: 派生列変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntransformation.f1
helpviewer_keywords:
- Derived Column Transformation Editor
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41a0f0dcd253473f78f2f38426b5fbd3d2ac2812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644571"
---
# <a name="derived-column-transformation-editor"></a><span data-ttu-id="01a08-102">派生列変換エディター</span><span class="sxs-lookup"><span data-stu-id="01a08-102">Derived Column Transformation Editor</span></span>
  <span data-ttu-id="01a08-103">**[派生列変換エディター]** ダイアログ ボックスを使用すると、新しい列または置換列を作成する式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="01a08-103">Use the **Derived Column Transformation Editor** dialog box to create expressions that populate new or replacement columns.</span></span>  
  
 <span data-ttu-id="01a08-104">派生列変換の詳細については、「 [派生列変換](data-flow/transformations/derived-column-transformation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="01a08-104">To learn more about the Derived Column transformation, see [Derived Column Transformation](data-flow/transformations/derived-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="01a08-105">Options</span><span class="sxs-lookup"><span data-stu-id="01a08-105">Options</span></span>  
 <span data-ttu-id="01a08-106">**[変数] と [列]**</span><span class="sxs-lookup"><span data-stu-id="01a08-106">**Variables and Columns**</span></span>  
 <span data-ttu-id="01a08-107">使用可能な変数と列の一覧から、下のペインにある既存のテーブル行または一覧の下の新しい行へドラッグすることによって、変数または入力列を使用する式を作成します。</span><span class="sxs-lookup"><span data-stu-id="01a08-107">Build an expression that uses a variable or an input column by dragging the variable or column from the list of available variables and columns to an existing table row in the pane below, or to a new row at the bottom of the list.</span></span>  
  
 <span data-ttu-id="01a08-108">**[関数] と [演算子]**</span><span class="sxs-lookup"><span data-stu-id="01a08-108">**Functions and Operators**</span></span>  
 <span data-ttu-id="01a08-109">関数と演算子を一覧から下のペインにドラッグすることによって、入力データおよび直接出力データを評価する関数または演算子を使用する式を作成します。</span><span class="sxs-lookup"><span data-stu-id="01a08-109">Build an expression that uses a function or an operator to evaluate input data and direct output data by dragging functions and operators from the list to the pane below.</span></span>  
  
 <span data-ttu-id="01a08-110">**派生列名**</span><span class="sxs-lookup"><span data-stu-id="01a08-110">**Derived Column Name**</span></span>  
 <span data-ttu-id="01a08-111">派生列名を指定します。</span><span class="sxs-lookup"><span data-stu-id="01a08-111">Provide a derived column name.</span></span> <span data-ttu-id="01a08-112">既定は派生列の番号付けされた一覧ですが、一意のわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="01a08-112">The default is a numbered list of derived columns; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="01a08-113">**[派生列]**</span><span class="sxs-lookup"><span data-stu-id="01a08-113">**Derived Column**</span></span>  
 <span data-ttu-id="01a08-114">一覧から派生列を選択します。</span><span class="sxs-lookup"><span data-stu-id="01a08-114">Select a derived column from the list.</span></span> <span data-ttu-id="01a08-115">派生列を新しい出力列として追加するか、既存の列のデータを置き換えるかを選択します。</span><span class="sxs-lookup"><span data-stu-id="01a08-115">Choose whether to add the derived column as a new output column, or to replace the data in an existing column.</span></span>  
  
 <span data-ttu-id="01a08-116">**[式]**</span><span class="sxs-lookup"><span data-stu-id="01a08-116">**Expression**</span></span>  
 <span data-ttu-id="01a08-117">式を入力するか、前述の使用可能な列、変数、関数、および演算子の一覧からドラッグすることによって式を作成します。</span><span class="sxs-lookup"><span data-stu-id="01a08-117">Type an expression or build one by dragging from the previous list of available columns, variables, functions, and operators.</span></span>  
  
 <span data-ttu-id="01a08-118">このプロパティの値は、プロパティ式を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="01a08-118">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="01a08-119">**関連トピック**: [Integration Services &#40;SSIS&#41; の式](expressions/integration-services-ssis-expressions.md)、[ &#40;SSIS の式&#41;](expressions/operators-ssis-expression.md)、[ &#40;SSIS の式&#41;](expressions/functions-ssis-expression.md)</span><span class="sxs-lookup"><span data-stu-id="01a08-119">**Related topics**: [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Operators &#40;SSIS Expression&#41;](expressions/operators-ssis-expression.md), and [Functions &#40;SSIS Expression&#41;](expressions/functions-ssis-expression.md)</span></span>  
  
 <span data-ttu-id="01a08-120">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="01a08-120">**Data Type**</span></span>  
 <span data-ttu-id="01a08-121">新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって自動的に式が評価され、データ型が適切に設定されます。</span><span class="sxs-lookup"><span data-stu-id="01a08-121">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the data type appropriately.</span></span> <span data-ttu-id="01a08-122">この列の値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="01a08-122">The value of this column is read-only.</span></span> <span data-ttu-id="01a08-123">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01a08-123">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="01a08-124">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="01a08-124">**Length**</span></span>  
 <span data-ttu-id="01a08-125">新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって自動的に式が評価され、文字列データに対する列の長さが設定されます。</span><span class="sxs-lookup"><span data-stu-id="01a08-125">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the column length for string data.</span></span> <span data-ttu-id="01a08-126">この列の値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="01a08-126">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="01a08-127">**[精度]**</span><span class="sxs-lookup"><span data-stu-id="01a08-127">**Precision**</span></span>  
 <span data-ttu-id="01a08-128">新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって、データ型に基づく数値データの有効桁数が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="01a08-128">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the precision for numeric data based on the data type.</span></span> <span data-ttu-id="01a08-129">この列の値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="01a08-129">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="01a08-130">**スケール**</span><span class="sxs-lookup"><span data-stu-id="01a08-130">**Scale**</span></span>  
 <span data-ttu-id="01a08-131">新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって、データ型に基づく数値データの小数点以下桁数が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="01a08-131">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the scale for numeric data based on the data type.</span></span> <span data-ttu-id="01a08-132">この列の値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="01a08-132">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="01a08-133">**コードページ**</span><span class="sxs-lookup"><span data-stu-id="01a08-133">**Code Page**</span></span>  
 <span data-ttu-id="01a08-134">新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって、DT_STR データ型のコード ページが自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="01a08-134">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets code page for the DT_STR data type.</span></span> <span data-ttu-id="01a08-135">**[コード ページ]** は必要に応じて更新できます。</span><span class="sxs-lookup"><span data-stu-id="01a08-135">You can update **Code Page**.</span></span>  
  
 <span data-ttu-id="01a08-136">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="01a08-136">**Configure error output**</span></span>  
 <span data-ttu-id="01a08-137">[[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスを使用して、エラーの処理方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="01a08-137">Specify how to handle errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a08-138">参照</span><span class="sxs-lookup"><span data-stu-id="01a08-138">See Also</span></span>  
 <span data-ttu-id="01a08-139">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="01a08-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="01a08-140">派生列変換を使用して列の値を取得する</span><span class="sxs-lookup"><span data-stu-id="01a08-140">Derive Column Values by Using the Derived Column Transformation</span></span>](data-flow/transformations/derive-column-values-by-using-the-derived-column-transformation.md)  
  
  
