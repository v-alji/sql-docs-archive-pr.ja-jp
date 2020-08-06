---
title: データ変換の変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57b1f70c070cdf81dc0bc899ed365d048db26cc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632029"
---
# <a name="data-conversion-transformation"></a><span data-ttu-id="e0286-102">データ変換の変換</span><span class="sxs-lookup"><span data-stu-id="e0286-102">Data Conversion Transformation</span></span>
  <span data-ttu-id="e0286-103">データ変換の変換は、入力列のデータを別のデータ型に変換し、新しい出力列にコピーします。</span><span class="sxs-lookup"><span data-stu-id="e0286-103">The Data Conversion transformation converts the data in an input column to a different data type and then copies it to a new output column.</span></span> <span data-ttu-id="e0286-104">たとえば、パッケージで複数の変換元のデータを抽出し、この変換を使用して、列を変換先のデータ ストアで要求されるデータ型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="e0286-104">For example, a package can extract data from multiple sources, and then use this transformation to convert columns to the data type required by the destination data store.</span></span> <span data-ttu-id="e0286-105">1 つの入力列に複数の変換を適用できます。</span><span class="sxs-lookup"><span data-stu-id="e0286-105">You can apply multiple conversions to a single input column.</span></span>  
  
 <span data-ttu-id="e0286-106">この変換を使用すると、パッケージで次の種類のデータ変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e0286-106">Using this transformation, a package can perform the following types of data conversions:</span></span>  
  
-   <span data-ttu-id="e0286-107">データ型を変更します。</span><span class="sxs-lookup"><span data-stu-id="e0286-107">Change the data type.</span></span> <span data-ttu-id="e0286-108">詳細については、「 [Integration Services Data Types](../integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0286-108">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e0286-109">date データ型または datetime データ型にデータを変換する場合、ロケール設定で別の形式が指定されている場合でも、出力列の日付は ISO 形式になります。</span><span class="sxs-lookup"><span data-stu-id="e0286-109">If you are converting data to a date or a datetime data type, the date in the output column is in the ISO format, although the locale preference may specify a different format.</span></span>  
  
-   <span data-ttu-id="e0286-110">文字列データの列の長さ、および数値データの有効桁数と小数点以下桁数を設定します。</span><span class="sxs-lookup"><span data-stu-id="e0286-110">Set the column length of string data and the precision and scale on numeric data.</span></span> <span data-ttu-id="e0286-111">詳しくは、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e0286-111">For more information, see [Precision, Scale, and Length &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).</span></span>  
  
-   <span data-ttu-id="e0286-112">コード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0286-112">Specify a code page.</span></span> <span data-ttu-id="e0286-113">詳しくは、「 [Comparing String Data](../comparing-string-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e0286-113">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e0286-114">文字列データ型の 2 つの列間でコピーを行う場合、それらの列のコード ページは同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0286-114">When copying between columns with a string data type, the two columns must use the same code page.</span></span>  
  
 <span data-ttu-id="e0286-115">文字列データの出力列の長さが、対応する入力列の長さよりも短い場合、出力データは切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="e0286-115">If the length of an output column of string data is shorter than the length of its corresponding input column, the output data is truncated.</span></span> <span data-ttu-id="e0286-116">詳細については、「 [データのエラー処理](../error-handling-in-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0286-116">For more information, see [Error Handling in Data](../error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="e0286-117">この変換は、1 つの入力、1 つの出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="e0286-117">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e0286-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e0286-118">Related Tasks</span></span>  
 <span data-ttu-id="e0286-119">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="e0286-119">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="e0286-120">SSIS デザイナーでデータ変換の変換を使用する方法については、「 [データ変換の変換を使用してデータを別のデータ型に変換する](data-conversion-transformation.md) 」および「 [[データ変換変換エディター]](../../data-conversion-transformation-editor.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e0286-120">For information about using the Data Conversion Transformation in the SSIS Designer, see [Convert Data to a Different Data Type by Using the Data Conversion Transformation](data-conversion-transformation.md) and [Data Conversion Transformation Editor](../../data-conversion-transformation-editor.md).</span></span> <span data-ttu-id="e0286-121">プログラムによるこの変換のプロパティの設定については、「 [共通プロパティ](../../common-properties.md) 」および「 [変換のカスタム プロパティ](transformation-custom-properties.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e0286-121">For information about setting properties of this transformation programmatically, see [Common Properties](../../common-properties.md) and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="e0286-122">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e0286-122">Related Content</span></span>  
 <span data-ttu-id="e0286-123">blogs.msdn.com のブログ「 [SSIS 2008 のデータ型の変換手法間のパフォーマンス比較](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035)」</span><span class="sxs-lookup"><span data-stu-id="e0286-123">Blog entry, [Performance Comparison between Data Type Conversion Techniques in SSIS 2008](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0286-124">参照</span><span class="sxs-lookup"><span data-stu-id="e0286-124">See Also</span></span>  
 <span data-ttu-id="e0286-125">[高速解析](../../fast-parse.md) </span><span class="sxs-lookup"><span data-stu-id="e0286-125">[Fast Parse](../../fast-parse.md) </span></span>  
 <span data-ttu-id="e0286-126">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e0286-126">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="e0286-127">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="e0286-127">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
