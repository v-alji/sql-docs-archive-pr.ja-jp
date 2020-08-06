---
title: データ変換変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4b893f04dcca2dd2a1a5874b55c1c1c608aaeb12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742474"
---
# <a name="data-conversion-transformation-editor"></a><span data-ttu-id="fea97-102">データ変換変換エディター</span><span class="sxs-lookup"><span data-stu-id="fea97-102">Data Conversion Transformation Editor</span></span>
  <span data-ttu-id="fea97-103">**[データ変換変換エディター]** ダイアログ ボックスを使用すると、変換対象の列や列の変換先のデータ型を選択したり、変換属性を設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="fea97-103">Use the **Data Conversion Transformation Editor** dialog box to select the columns to convert, select the data type to which the column is converted, and set conversion attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fea97-104">データ `FastParse` 変換の変換の出力列のプロパティは、[**データ変換変換エディター**] では使用できませんが、**詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="fea97-104">The `FastParse` property of the output columns of the Data Conversion transformation is not available in the **Data Conversion Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="fea97-105">このプロパティの詳細については、「 [変換のカスタム プロパティ](data-flow/transformations/transformation-custom-properties.md)」の「データ変換の変換」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fea97-105">For more information on this property, see the Data Conversion Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="fea97-106">データ変換の変換の詳細については、「 [データ変換の変換](data-flow/transformations/data-conversion-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fea97-106">To learn more about the Data Conversion transformation, see [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fea97-107">Options</span><span class="sxs-lookup"><span data-stu-id="fea97-107">Options</span></span>  
 <span data-ttu-id="fea97-108">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="fea97-108">**Available Input Columns**</span></span>  
 <span data-ttu-id="fea97-109">変換対象の列のチェック ボックスを使用して選択します。</span><span class="sxs-lookup"><span data-stu-id="fea97-109">Select columns to convert by using the check boxes.</span></span> <span data-ttu-id="fea97-110">選択した列が入力列として下のテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="fea97-110">Your selections add input columns to the table below.</span></span>  
  
 <span data-ttu-id="fea97-111">**入力列**</span><span class="sxs-lookup"><span data-stu-id="fea97-111">**Input Column**</span></span>  
 <span data-ttu-id="fea97-112">使用できる入力列の一覧から変換対象の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="fea97-112">Select columns to convert from the list of available input columns.</span></span> <span data-ttu-id="fea97-113">上記のチェック ボックスに、選択内容が反映されます。</span><span class="sxs-lookup"><span data-stu-id="fea97-113">Your selections are reflected in the check box selections above.</span></span>  
  
 <span data-ttu-id="fea97-114">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="fea97-114">**Output Alias**</span></span>  
 <span data-ttu-id="fea97-115">それぞれの新しい列の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="fea97-115">Type an alias for each new column.</span></span> <span data-ttu-id="fea97-116">既定では、入力列の名前の後に "`Copy of`" が追加された別名になりますが、固有のわかりやすい名前を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="fea97-116">The default is `Copy of` followed by the input column name; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="fea97-117">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="fea97-117">**Data Type**</span></span>  
 <span data-ttu-id="fea97-118">一覧から利用可能なデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="fea97-118">Select an available data type from the list.</span></span> <span data-ttu-id="fea97-119">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fea97-119">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="fea97-120">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="fea97-120">**Length**</span></span>  
 <span data-ttu-id="fea97-121">文字列データの列の長さを設定します。</span><span class="sxs-lookup"><span data-stu-id="fea97-121">Set the column length for string data.</span></span>  
  
 <span data-ttu-id="fea97-122">**[精度]**</span><span class="sxs-lookup"><span data-stu-id="fea97-122">**Precision**</span></span>  
 <span data-ttu-id="fea97-123">数値データの有効桁数を設定します。</span><span class="sxs-lookup"><span data-stu-id="fea97-123">Set the precision for numeric data.</span></span>  
  
 <span data-ttu-id="fea97-124">**スケール**</span><span class="sxs-lookup"><span data-stu-id="fea97-124">**Scale**</span></span>  
 <span data-ttu-id="fea97-125">数値データの小数点以下桁数を設定します。</span><span class="sxs-lookup"><span data-stu-id="fea97-125">Set the scale for numeric data.</span></span>  
  
 <span data-ttu-id="fea97-126">**コード ページ**</span><span class="sxs-lookup"><span data-stu-id="fea97-126">**Code page**</span></span>  
 <span data-ttu-id="fea97-127">DT_STR 型の列に適したコード ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="fea97-127">Select the appropriate code page for columns of type DT_STR.</span></span>  
  
 <span data-ttu-id="fea97-128">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="fea97-128">**Configure error output**</span></span>  
 <span data-ttu-id="fea97-129">[[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスを使用して、エラーの処理方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="fea97-129">Specify how to handle row-level errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea97-130">参照</span><span class="sxs-lookup"><span data-stu-id="fea97-130">See Also</span></span>  
 <span data-ttu-id="fea97-131">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fea97-131">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="fea97-132">データ変換の変換を使用してデータを別のデータ型に変換する</span><span class="sxs-lookup"><span data-stu-id="fea97-132">Convert Data to a Different Data Type by Using the Data Conversion Transformation</span></span>](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
