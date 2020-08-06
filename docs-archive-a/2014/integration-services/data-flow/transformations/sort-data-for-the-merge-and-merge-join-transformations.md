---
title: マージ変換およびマージ結合変換用にデータを並べ替える | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bb4e91ad84c6baa52e1d7fb4b0104d835b7e4cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712178"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a><span data-ttu-id="d0a52-102">マージ変換およびマージ結合変換用にデータを並べ替える</span><span class="sxs-lookup"><span data-stu-id="d0a52-102">Sort Data for the Merge and Merge Join Transformations</span></span>
  <span data-ttu-id="d0a52-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]のマージ変換およびマージ結合変換では、入力データが並べ替えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-103">In [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], the Merge and Merge Join transformations require sorted data for their inputs.</span></span> <span data-ttu-id="d0a52-104">入力データは物理的に並べ替える必要があります。さらに、変換元の出力および出力列、または上流の変換の出力および出力列に対して、並べ替えオプションを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-104">The input data must be sorted physically, and sort options must be set on the outputs and the output columns in the source or in the upstream transformation.</span></span> <span data-ttu-id="d0a52-105">並べ替えオプションでデータの並べ替えを設定していても、実際にデータの並べ替えが行われない場合、マージ操作やマージ結合操作で予測できない結果が発生します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-105">If the sort options indicate that the data is sorted, but the data is not actually sorted, the results of the merge or merge join operation are unpredictable.</span></span>  
  
## <a name="sorting-the-data"></a><span data-ttu-id="d0a52-106">データを並べ替える</span><span class="sxs-lookup"><span data-stu-id="d0a52-106">Sorting the Data</span></span>  
 <span data-ttu-id="d0a52-107">データを並べ替えるには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-107">You can sort this data by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="d0a52-108">変換元で、データの読み込みに使用されるステートメントで ORDER BY 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-108">In the source, use an ORDER BY clause in the statement that is used to load the data.</span></span>  
  
-   <span data-ttu-id="d0a52-109">データ フローで、マージ変換またはマージ結合変換の前に並べ替え変換を挿入します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-109">In the data flow, insert a Sort transformation before the Merge or Merge Join transformation.</span></span>  
  
 <span data-ttu-id="d0a52-110">データが文字列データの場合、マージ変換およびマージ結合変換では、文字列値が Windows 照合順序を使用して並べ替えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-110">If the data is string data, both the Merge and Merge Join transformations expect the string values to have been sorted by using Windows collation.</span></span> <span data-ttu-id="d0a52-111">Windows 照合順序を使用して並べ替えた文字列値を、マージ変換およびマージ結合変換に指定するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-111">To provide string values to the Merge and Merge Join transformations that are sorted by using Windows collation, use the following procedure.</span></span>  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a><span data-ttu-id="d0a52-112">Windows 照合順序を使用して並べ替えた文字列値を指定するには</span><span class="sxs-lookup"><span data-stu-id="d0a52-112">To provide string values that are sorted by using Windows collation</span></span>  
  
-   <span data-ttu-id="d0a52-113">並べ替え変換を使用して、データを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-113">Use a Sort transformation to sort the data.</span></span>  
  
     <span data-ttu-id="d0a52-114">並べ替え変換では Windows 照合順序を使用して文字列値を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-114">The Sort transformation uses Windows collation to sort string values.</span></span>  
  
     <span data-ttu-id="d0a52-115">または</span><span class="sxs-lookup"><span data-stu-id="d0a52-115">-or-</span></span>  
  
-   <span data-ttu-id="d0a52-116">Transact-SQL の CAST 演算子を使用して最初に `varchar` 値を `nvarchar` 値にキャストし、次に Transact-SQL ORDER BY 句を使用してデータを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-116">Use the Transact-SQL CAST operator to first cast `varchar` values to `nvarchar` values, and then use the Transact-SQL ORDER BY clause to sort the data.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d0a52-117">ORDER BY 句では文字列値の並べ替えに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 照合順序を使用するため、ORDER BY 句のみを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d0a52-117">You cannot use the ORDER BY clause alone because the ORDER BY clause uses a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] collation to sort string values.</span></span> <span data-ttu-id="d0a52-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 照合順序を使用すると、Windows 照合順序とは異なる並べ替え順序になる場合があります。この場合、マージ変換またはマージ結合変換で予期しない結果になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-118">The use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] collation might result in a different sort order than Windows collation, which can cause the Merge or Merge Join transformation to produce unexpected results.</span></span>  
  
## <a name="setting-sort-options-on-the-data"></a><span data-ttu-id="d0a52-119">データに対する並べ替えオプションの設定</span><span class="sxs-lookup"><span data-stu-id="d0a52-119">Setting Sort Options on the Data</span></span>  
 <span data-ttu-id="d0a52-120">マージ変換およびマージ結合変換にデータを提供する変換元または上流の変換に対して、設定する必要のある重要な並べ替えプロパティが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-120">There are two important sort properties that must be set for the source or upstream transformation that supplies data to the Merge and Merge Join transformations:</span></span>  
  
-   <span data-ttu-id="d0a52-121">データが並べ替えられているかどうかを示す、出力の `IsSorted` プロパティ。</span><span class="sxs-lookup"><span data-stu-id="d0a52-121">The `IsSorted` property of the output that indicates whether the data has been sorted.</span></span> <span data-ttu-id="d0a52-122">このプロパティは `True` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-122">This property must be set to `True`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d0a52-123">`IsSorted` プロパティの値を `True` に設定しても、データは並べ替えられません。</span><span class="sxs-lookup"><span data-stu-id="d0a52-123">Setting the value of the `IsSorted` property to `True` does not sort the data.</span></span> <span data-ttu-id="d0a52-124">このプロパティでは、データが既に並べ替えられている下流コンポーネントにヒントのみを提供します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-124">This property only provides a hint to downstream components that the data has been previously sorted.</span></span>  
  
-   <span data-ttu-id="d0a52-125">列を並べ替えるかどうか、並べ替える場合はその列の並べ替え順、および複数の列の並べ替えの順序を示す、出力列の `SortKeyPosition` プロパティ。</span><span class="sxs-lookup"><span data-stu-id="d0a52-125">The `SortKeyPosition` property of output columns that indicates whether a column is sorted, the column's sort order, and the sequence in which multiple columns are sorted.</span></span> <span data-ttu-id="d0a52-126">このプロパティは、並べ替えられるデータの各列に対して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-126">This property must be set for each column of sorted data.</span></span>  
  
 <span data-ttu-id="d0a52-127">並べ替え変換を使用してデータを並べ替える場合、並べ替え変換によって、これらの両方のプロパティが、マージ変換またはマージ結合変換の必要に応じて設定されます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-127">If you use a Sort transformation to sort the data, the Sort transformation sets both of these properties as required by the Merge or Merge Join transformation.</span></span> <span data-ttu-id="d0a52-128">つまり、並べ替え変換によって、その出力の `IsSorted` プロパティが `True` に設定され、その出力列の `SortKeyPosition` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-128">That is, the Sort transformation sets the `IsSorted` property of its output to `True`, and sets the `SortKeyPosition` properties of its output columns.</span></span>  
  
 <span data-ttu-id="d0a52-129">ただし、データの並べ替えに並べ替え変換を使用しない場合は、変換元または上流の変換でこれらの並べ替えプロパティを手動で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-129">However, if you do not use a Sort transformation to sort the data, you must set these sort properties manually on the source or the upstream transformation.</span></span> <span data-ttu-id="d0a52-130">変換元または上流の変換で並べ替えプロパティを手動で設定するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-130">To manually set the sort properties on the source or upstream transformation, use the following procedure.</span></span>  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a><span data-ttu-id="d0a52-131">変換元コンポーネントまたは変換コンポーネントの並べ替え属性を手動で設定するには</span><span class="sxs-lookup"><span data-stu-id="d0a52-131">To manually set sort attributes on a source or transformation component</span></span>  
  
1.  <span data-ttu-id="d0a52-132">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-132">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="d0a52-133">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-133">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="d0a52-134">**[データ フロー]** タブで、適切な変換元または上流の変換を見つけるか、 **[ツールボックス]** からデザイン画面に、変換元または上流の変換をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d0a52-134">On the **Data Flow** tab, locate the appropriate source or upstream transformation, or drag it from the **Toolbox** to the design surface.</span></span>  
  
4.  <span data-ttu-id="d0a52-135">コンポーネントを右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0a52-135">Right-click the component and click **Show Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="d0a52-136">**[入力プロパティと出力プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0a52-136">Click the **Input and Output Properties** tab.</span></span>  
  
6.  <span data-ttu-id="d0a52-137">[ \*\* \<component name> 出力\*\*] をクリックし、 `IsSorted` プロパティをに設定し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-137">Click **\<component name> Output**, and set the `IsSorted` property to `True`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0a52-138">出力の `IsSorted` プロパティを手動で `True` に設定したにもかかわらず、データが並べ替えられない場合、パッケージの実行時に、下流の結合変換またはマージ結合変換で、データの欠落、または不良データの比較が生じている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-138">If you manually set the `IsSorted` property of the output to `True` and the data is not sorted, there might be missing data or bad data comparisons in the downstream Merge or Merge Join transformation when you run the package.</span></span>  
  
7.  <span data-ttu-id="d0a52-139">**[出力列]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-139">Expand **Output Columns**.</span></span>  
  
8.  <span data-ttu-id="d0a52-140">並べ替えを指定する列をクリックし、次のガイドラインに従って、その列の `SortKeyPosition` プロパティを 0 以外の整数値に設定します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-140">Click the column that you want to indicate is sorted and set its `SortKeyPosition` property to a nonzero integer value by following these guidelines:</span></span>  
  
    -   <span data-ttu-id="d0a52-141">整数値は、1 から始まって 1 ずつ増加する連続した数字を表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0a52-141">The integer value must represent a numeric sequence, starting with 1 and incremented by 1.</span></span>  
  
    -   <span data-ttu-id="d0a52-142">正の整数値は、昇順の並べ替え順序を示します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-142">A positive integer value indicates an ascending sort order.</span></span>  
  
    -   <span data-ttu-id="d0a52-143">負の整数値は、降順の並べ替え順序を示します</span><span class="sxs-lookup"><span data-stu-id="d0a52-143">A negative integer value indicates a descending sort order.</span></span> <span data-ttu-id="d0a52-144">(負の数値が設定されると、その数値の絶対値によって、並べ替え順での列の位置が決まります)。</span><span class="sxs-lookup"><span data-stu-id="d0a52-144">(If set to a negative number, the absolute value of the number determines the column's position in the sort sequence.)</span></span>  
  
    -   <span data-ttu-id="d0a52-145">既定値は 0 で、その列が並べ替えられないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-145">The default value of 0 indicates that the column is not sorted.</span></span> <span data-ttu-id="d0a52-146">並べ替えに加えない出力列では、値を 0 のままにします。</span><span class="sxs-lookup"><span data-stu-id="d0a52-146">Leave the value of 0 for output columns that do not participate in the sort.</span></span>  
  
     <span data-ttu-id="d0a52-147">`SortKeyPosition` プロパティの設定方法の例として、データを変換元に読み込む、次の Transact-SQL ステートメントについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="d0a52-147">As an example of how to set the `SortKeyPosition` property, consider the following Transact-SQL statement that loads data in a source:</span></span>  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     <span data-ttu-id="d0a52-148">このステートメントでは、列ごとに `SortKeyPosition` プロパティを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-148">For this statement, you would set the `SortKeyPosition` property for each column as follows:</span></span>  
  
    -   <span data-ttu-id="d0a52-149">ColumnA の `SortKeyPosition` プロパティを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-149">Set the `SortKeyPosition` property of ColumnA to 1.</span></span> <span data-ttu-id="d0a52-150">これは、ColumnA が最初に並べ替えられる列で、並べ替えが昇順で行われることを示します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-150">This indicates that ColumnA is the first column to be sorted and is sorted in ascending order.</span></span>  
  
    -   <span data-ttu-id="d0a52-151">ColumnB の `SortKeyPosition` プロパティを -2 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-151">Set the `SortKeyPosition` property of ColumnB to -2.</span></span> <span data-ttu-id="d0a52-152">これは、ColumnB が 2 番目に並べ替えられる列で、並べ替えが降順で行われることを示します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-152">This indicates that ColumnB is the second column to be sorted and is sorted in descending order</span></span>  
  
    -   <span data-ttu-id="d0a52-153">ColumnC の `SortKeyPosition` プロパティを 3 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-153">Set the `SortKeyPosition` property of ColumnC to 3.</span></span> <span data-ttu-id="d0a52-154">これは、ColumnC が 3 番目に並べ替えられる列で、並べ替えが昇順で行われることを示します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-154">This indicates that ColumnC is the third column to be sorted and is sorted in ascending order.</span></span>  
  
9. <span data-ttu-id="d0a52-155">並べ替える列ごとに、手順 8. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d0a52-155">Repeat step 8 for each sorted column.</span></span>  
  
10. <span data-ttu-id="d0a52-156">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0a52-156">Click **OK**.</span></span>  
  
11. <span data-ttu-id="d0a52-157">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0a52-157">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a52-158">参照</span><span class="sxs-lookup"><span data-stu-id="d0a52-158">See Also</span></span>  
 <span data-ttu-id="d0a52-159">[マージ変換](merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="d0a52-159">[Merge Transformation](merge-transformation.md) </span></span>  
 <span data-ttu-id="d0a52-160">[マージ結合変換](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="d0a52-160">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="d0a52-161">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="d0a52-161">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="d0a52-162">[Integration Services のパス](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="d0a52-162">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="d0a52-163">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="d0a52-163">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
