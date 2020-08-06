---
title: 並べ替え変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttrans.f1
helpviewer_keywords:
- Sort transformation
- descending sorts
- ascending sorts
- sorting data [Integration Services]
- multiple sorts
- duplicate data [Integration Services]
ms.assetid: 728c9351-84a8-4a89-be4d-d50d4adc04e0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7039d02b6cc55355c3b27e5694474df4666570ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642195"
---
# <a name="sort-transformation"></a><span data-ttu-id="708d9-102">並べ替え変換</span><span class="sxs-lookup"><span data-stu-id="708d9-102">Sort Transformation</span></span>
  <span data-ttu-id="708d9-103">並べ替え変換は、入力データを昇順または降順で並べ替え、並べ替えたデータを変換出力にコピーします。</span><span class="sxs-lookup"><span data-stu-id="708d9-103">The Sort transformation sorts input data in ascending or descending order and copies the sorted data to the transformation output.</span></span> <span data-ttu-id="708d9-104">入力には複数の並べ替えを適用できます。各並べ替えは、並べ替えの順序を決定する数値によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="708d9-104">You can apply multiple sorts to an input; each sort is identified by a numeral that determines the sort order.</span></span> <span data-ttu-id="708d9-105">順序の数値が最も小さい列が最初に並べ替えられ、順序の数値の大きさの順に列が並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="708d9-105">The column with the lowest number is sorted first, the sort column with the second lowest number is sorted next, and so on.</span></span> <span data-ttu-id="708d9-106">たとえば、 **CountryRegion** という名前の列の並べ替え順序が 1 で、 **City** という名前の列の並べ替え順序が 2 の場合、出力は、国または地域、次に都市の順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="708d9-106">For example, if a column named **CountryRegion** has a sort order of 1 and a column named **City** has a sort order of 2, the output is sorted by country/region and then by city.</span></span> <span data-ttu-id="708d9-107">正の値は昇順の並べ替えを表し、負の値は降順の並べ替えを表します。</span><span class="sxs-lookup"><span data-stu-id="708d9-107">A positive number denotes that the sort is ascending, and a negative number denotes that the sort is descending.</span></span> <span data-ttu-id="708d9-108">並べ替えを行わない列の並べ替え順序は 0 です。</span><span class="sxs-lookup"><span data-stu-id="708d9-108">Columns that are not sorted have a sort order of 0.</span></span> <span data-ttu-id="708d9-109">並べ替えを選択されていない列は、並べ替えられた列と共に、自動的に変換出力にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="708d9-109">Columns that are not selected for sorting are automatically copied to the transformation output together with the sorted columns.</span></span>  
  
 <span data-ttu-id="708d9-110">並べ替え変換には、比較オプションのセットが含まれており、変換による列の文字列データの処理方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="708d9-110">The Sort transformation includes a set of comparison options to define how the transformation handles the string data in a column.</span></span> <span data-ttu-id="708d9-111">詳しくは、「 [Comparing String Data](../comparing-string-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="708d9-111">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="708d9-112">並べ替え変換では、GUID は Transact-SQL で ORDER BY 句を使用したときと同じ順序では並べ替えられません。</span><span class="sxs-lookup"><span data-stu-id="708d9-112">The Sort transformation does not sort GUIDs in the same order as the ORDER BY clause does in Transact-SQL.</span></span> <span data-ttu-id="708d9-113">並べ替え変換では、0 ～ 9 で始まる GUID は A ～ F で始まる GUID の前に並べ替えられますが、ORDER BY 句では [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]での実装と同じく、並べ替え変換とは異なる順番で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="708d9-113">While the Sort transformation sorts GUIDs that start with 0-9 before GUIDs that start with A-F, the ORDER BY clause, as implemented in the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], sorts them differently.</span></span> <span data-ttu-id="708d9-114">詳細については、「[ORDER BY 句 (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="708d9-114">For more information, see [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).</span></span>  
  
 <span data-ttu-id="708d9-115">また、並べ替え変換では、並べ替えの実行時に重複する行を削除できます。</span><span class="sxs-lookup"><span data-stu-id="708d9-115">The Sort transformation can also remove duplicate rows as part of its sort.</span></span> <span data-ttu-id="708d9-116">重複する行とは、並べ替えキーの値が同じ行のことです。</span><span class="sxs-lookup"><span data-stu-id="708d9-116">Duplicate rows are rows with the same sort key values.</span></span> <span data-ttu-id="708d9-117">並べ替えキーの値は、使用する文字列比較オプションに基づいて生成されます。したがって、リテラル文字列が異なっていても、並べ替えキーの値は同じとなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="708d9-117">The sort key value is generated based on the string comparison options being used, which means that different literal strings may have the same sort key values.</span></span> <span data-ttu-id="708d9-118">並べ替え変換は、値は異なるが並べ替えキーが同じ入力列の行を、重複していると識別します。</span><span class="sxs-lookup"><span data-stu-id="708d9-118">The transformation identifies rows in the input columns that have different values but the same sort key as duplicates.</span></span>  
  
 <span data-ttu-id="708d9-119">並べ替え変換には、パッケージの読み込み時にプロパティ式で更新できる、`MaximumThreads` カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="708d9-119">The Sort transformation includes the `MaximumThreads` custom property that can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="708d9-120">詳細については、「[Integration Services &#40;SSIS&#41; の式](../../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="708d9-120">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="708d9-121">この変換は 1 つの入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="708d9-121">This transformation has one input and one output.</span></span> <span data-ttu-id="708d9-122">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="708d9-122">It does not support error outputs.</span></span>  
  
## <a name="configuration-of-the-sort-transformation"></a><span data-ttu-id="708d9-123">並べ替え変換の構成</span><span class="sxs-lookup"><span data-stu-id="708d9-123">Configuration of the Sort Transformation</span></span>  
 <span data-ttu-id="708d9-124">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="708d9-124">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="708d9-125">**[並べ替え変換エディター]** ダイアログ ボックスで設定できるプロパティについては、「 [並べ替え変換エディター](../../sort-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="708d9-125">For information about the properties that you can set in the **Sort Transformation Editor** dialog box, see [Sort Transformation Editor](../../sort-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="708d9-126">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="708d9-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="708d9-127">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="708d9-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="708d9-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="708d9-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="708d9-129">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="708d9-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="708d9-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="708d9-130">Related Tasks</span></span>  
 <span data-ttu-id="708d9-131">コンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="708d9-131">For more information about how to set properties of the component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="708d9-132">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="708d9-132">Related Content</span></span>  
 <span data-ttu-id="708d9-133">codeplex.com のサンプル「 [SortDeDuplicateDelimitedString カスタム SSIS コンポーネント](https://go.microsoft.com/fwlink/?LinkId=220821)」</span><span class="sxs-lookup"><span data-stu-id="708d9-133">Sample, [SortDeDuplicateDelimitedString Custom SSIS Component](https://go.microsoft.com/fwlink/?LinkId=220821), on codeplex.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708d9-134">参照</span><span class="sxs-lookup"><span data-stu-id="708d9-134">See Also</span></span>  
 <span data-ttu-id="708d9-135">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="708d9-135">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="708d9-136">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="708d9-136">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
