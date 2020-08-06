---
title: 列のデータ型の設定 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 34e2d508-7b64-4503-a4f0-c6c6ad5f8a44
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d747f96e836a683ccce3aca3c5e3349ca633210
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711053"
---
# <a name="set-the-data-type-of-a-column-ssas-tabular"></a><span data-ttu-id="13e31-102">列のデータ型の設定 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="13e31-102">Set the Data Type of a Column (SSAS Tabular)</span></span>
  <span data-ttu-id="13e31-103">モデルにデータをインポートするか、データを貼り付けると、モデル デザイナーによってデータ型の検出と適用が自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="13e31-103">When you import data or paste data into a model, the model designer will automatically detect and apply data types.</span></span> <span data-ttu-id="13e31-104">データをモデルに追加したら、列のデータ型を手動で変更してデータの格納方法を変更できます。</span><span class="sxs-lookup"><span data-stu-id="13e31-104">After you have added the data to the model, you can manually modify the data type of a column to change how data is stored.</span></span> <span data-ttu-id="13e31-105">代わりに、データの格納方法を変更せずに表示形式だけを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="13e31-105">If you just want to change the format of how the data is displayed without changing the way it is stored, you can do that instead.</span></span>  
  
### <a name="to-change-the-data-type-or-display-format-for-a-column"></a><span data-ttu-id="13e31-106">列のデータ型または表示形式を変更するには</span><span class="sxs-lookup"><span data-stu-id="13e31-106">To change the data type or display format for a column</span></span>  
  
1.  <span data-ttu-id="13e31-107">モデル デザイナーで、データ型または表示形式を変更する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="13e31-107">In the model designer, select the column for which you want to change the data type or display format.</span></span>  
  
2.  <span data-ttu-id="13e31-108">列の **[プロパティ]** ウィンドウで、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="13e31-108">In the column **Properties** window, do one of the following:</span></span>  
  
    -   <span data-ttu-id="13e31-109">**[データ形式]** プロパティで別のデータ形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="13e31-109">In the **Data Format** property, select a different data format.</span></span>  
  
    -   <span data-ttu-id="13e31-110">**[データ型]** プロパティで別のデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="13e31-110">In the **Data Type** property, select a different data type.</span></span>  
  
## <a name="considerations-when-changing-data-types"></a><span data-ttu-id="13e31-111">データ型を変更するときの注意事項</span><span class="sxs-lookup"><span data-stu-id="13e31-111">Considerations when Changing Data Types</span></span>  
 <span data-ttu-id="13e31-112">列のデータ型を変更したり、データ変換を選択したりするときに、以下のいずれかのエラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="13e31-112">Sometimes when you try to change the data type of a column or select a data conversion, one of the following errors might occur:</span></span>  
  
-   <span data-ttu-id="13e31-113">データ型を変更できませんでした</span><span class="sxs-lookup"><span data-stu-id="13e31-113">Failed to change data type</span></span>  
  
-   <span data-ttu-id="13e31-114">列のデータ型を変更できませんでした</span><span class="sxs-lookup"><span data-stu-id="13e31-114">Failed to change column data type</span></span>  
  
 <span data-ttu-id="13e31-115">これらのエラーは、そのデータ型が [データ型] ボックスにオプションとして表示される場合でも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13e31-115">These errors might occur even if the data type is available as an option in the Data Type dropdown list.</span></span> <span data-ttu-id="13e31-116">ここでは、これらのエラーの原因と修正方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13e31-116">This section explains the cause of these errors and how you can correct them.</span></span>  
  
### <a name="understanding-automatically-determined-data-types"></a><span data-ttu-id="13e31-117">自動的に決定されたデータ型について</span><span class="sxs-lookup"><span data-stu-id="13e31-117">Understanding Automatically Determined Data Types</span></span>  
 <span data-ttu-id="13e31-118">データをモデルに追加すると、モデル デザイナーによってデータ列がチェックされ、各列に格納されているデータ型が調べられます。</span><span class="sxs-lookup"><span data-stu-id="13e31-118">When you add data to a model, the model designer checks the columns of data to see what data types each column contains.</span></span> <span data-ttu-id="13e31-119">その列のデータが一貫している場合は、最も有効桁数の大きいデータ型が列に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="13e31-119">If the data in that column is consistent, is assigns the most precise data type to the column.</span></span>  
  
 <span data-ttu-id="13e31-120">ただし、各列で 1 つのデータ型しか使用できない Excel または別のソースからデータを追加した場合は、列内のすべての値に対応できるデータ型がモデル デザイナーによって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="13e31-120">However, if you add data from Excel or another source that does not enforce the use of a single data type within each column, the model designer will assign a data type that accommodates all values within the column.</span></span> <span data-ttu-id="13e31-121">そのため、整数、長整数、通貨など、データ型の異なる数値が同じ列に含まれている場合、モデル デザイナーは decimal データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="13e31-121">Therefore, if a column contains numbers of different types, such as integers, long numbers, and currency, the model designer will use a decimal data type.</span></span> <span data-ttu-id="13e31-122">また、同じ列に数値と文字列が混在している場合は、文字列データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="13e31-122">Alternatively, if a column mixes numbers and text, the model designer will use the text data type.</span></span> <span data-ttu-id="13e31-123">モデル デザイナーには、Excel で使用できる標準データ型のようなデータ型は用意されていません。</span><span class="sxs-lookup"><span data-stu-id="13e31-123">The model designer does not provide a data type similar to the General data type available in Excel.</span></span>  
  
 <span data-ttu-id="13e31-124">したがって、列に数値とテキスト値の両方が含まれている場合は、その列を数値データ型に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="13e31-124">Therefore, if a column contains both numbers and text values, you will not be able to convert the column to a numeric data type.</span></span>  
  
 <span data-ttu-id="13e31-125">Business Intelligence Semantic Model で使用できるデータ型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="13e31-125">The following data types are available in business intelligence semantic models:</span></span>  
  
|<span data-ttu-id="13e31-126">モデルのデータ型</span><span class="sxs-lookup"><span data-stu-id="13e31-126">Model data types</span></span>|  
|----------------------|  
|<span data-ttu-id="13e31-127">Text</span><span class="sxs-lookup"><span data-stu-id="13e31-127">Text</span></span><br /><br /> <span data-ttu-id="13e31-128">10 進数</span><span class="sxs-lookup"><span data-stu-id="13e31-128">Decimal Number</span></span><br /><br /> <span data-ttu-id="13e31-129">整数</span><span class="sxs-lookup"><span data-stu-id="13e31-129">Whole Number</span></span><br /><br /> <span data-ttu-id="13e31-130">Currency</span><span class="sxs-lookup"><span data-stu-id="13e31-130">Currency</span></span><br /><br /> <span data-ttu-id="13e31-131">TRUE または FALSE</span><span class="sxs-lookup"><span data-stu-id="13e31-131">TRUE/FALSE</span></span><br /><br /> <span data-ttu-id="13e31-132">Date</span><span class="sxs-lookup"><span data-stu-id="13e31-132">Date</span></span>|  
  
 <span data-ttu-id="13e31-133">インポートしたデータのデータ型が間違っていた場合や、目的のデータ型と違っていた場合は、次の選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="13e31-133">If you find that your data has a wrong data type, or at least a different one than you wanted, you have several options:</span></span>  
  
-   <span data-ttu-id="13e31-134">データを再インポートします。</span><span class="sxs-lookup"><span data-stu-id="13e31-134">You can re-import the data.</span></span> <span data-ttu-id="13e31-135">これを選択した場合は、データ ソースへの既存の接続を開いて列を再インポートします。</span><span class="sxs-lookup"><span data-stu-id="13e31-135">To do this, open the existing connection to the data source and re-import the column.</span></span> <span data-ttu-id="13e31-136">データ ソースの種類によっては、インポート中にフィルターを適用して、問題のある値を削除できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="13e31-136">Depending on the data source type, you might be able to apply a filter during import to remove problem values.</span></span>  
  
-   <span data-ttu-id="13e31-137">計算列に DAX 数式を作成して、目的のデータ型の新しい値を作成します。</span><span class="sxs-lookup"><span data-stu-id="13e31-137">You can create a DAX formula in a calculated column to create a new value of the desired data type.</span></span> <span data-ttu-id="13e31-138">たとえば、TRUNC 関数を使用して小数点数を整数に変換したり、情報関数と論理関数を組み合わせて値をテストして変換したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="13e31-138">For example, the TRUNC function can be used to change a decimal number to a whole integer, or you can combine information functions and logical functions to test and convert values.</span></span>  
  
### <a name="understanding-data-conversion"></a><span data-ttu-id="13e31-139">データ変換について</span><span class="sxs-lookup"><span data-stu-id="13e31-139">Understanding Data Conversion</span></span>  
 <span data-ttu-id="13e31-140">データ変換オプションを選択するとエラーが発生する場合は、選択した変換を列の現在のデータ型がサポートしていないことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="13e31-140">If an error occurs when you select a data conversion option, it might be that the current data type of the column does not support the selected conversion.</span></span> <span data-ttu-id="13e31-141">すべてのデータ型ですべての変換を使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="13e31-141">Not all conversions are allowed for all data types.</span></span> <span data-ttu-id="13e31-142">たとえば、列をブール型に変更できるのは、列の現在のデータ型が数値 (整数または小数) またはテキストの場合だけです。</span><span class="sxs-lookup"><span data-stu-id="13e31-142">For example, you can only change a column to a Boolean data type if the current data type of the column is either a number (whole or decimal) or text.</span></span> <span data-ttu-id="13e31-143">したがって、列のデータに適したデータ型を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13e31-143">Therefore, you must choose an appropriate data type for the data in the column.</span></span>  
  
 <span data-ttu-id="13e31-144">適切なデータ型を選択した後、モデル デザイナーによって、有効桁数の損失や切り捨ての可能性など、データの変更についての警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13e31-144">After you choose an appropriate data type, the model designer will warn you about possible changes to your data, such as loss of precision, or truncation.</span></span> <span data-ttu-id="13e31-145">[OK] をクリックして受け入れ、データを新しいデータ型に変更します。</span><span class="sxs-lookup"><span data-stu-id="13e31-145">Click OK to accept and change your data to the new data type.</span></span>  
  
 <span data-ttu-id="13e31-146">そのデータ型がサポートされていても、新しいデータ型の範囲でサポートされていない値が見つかった場合は、モデル デザイナーによって別のエラーが表示されます。この場合は、続行する前にデータ値を修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13e31-146">If the data type is supported, but the model designer finds values that are not supported within the new data type, you will get another error, and will need to correct the data values before proceeding.</span></span>  
  
 <span data-ttu-id="13e31-147">Business Intelligence Semantic Model で使用されるデータ型、それらのデータ型の暗黙的な変換、および数式でさまざまなデータ型を使用する方法の詳細については、 [サポートされているデータ型 (SSAS テーブル)](data-types-supported-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13e31-147">For detailed information about the data types used in business intelligence semantic models, how they are implicitly converted, and how different data types are used in formulas, see [Data Types Supported &#40;SSAS Tabular&#41;](data-types-supported-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e31-148">参照</span><span class="sxs-lookup"><span data-stu-id="13e31-148">See Also</span></span>  
 [<span data-ttu-id="13e31-149">サポートされているデータ型 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="13e31-149">Data Types Supported &#40;SSAS Tabular&#41;</span></span>](data-types-supported-ssas-tabular.md)  
  
  
