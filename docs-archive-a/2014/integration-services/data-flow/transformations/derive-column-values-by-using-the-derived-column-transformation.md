---
title: 派生列変換を使用して列の値を取得する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- columns [Integration Services]
- derived columns
- columns [Integration Services], values
- Derived Column transformation
ms.assetid: 28b07746-fc6f-42b2-b741-9de6fac3f29c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 837ec552144697b40cf649bc0403edfe4dc57a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632025"
---
# <a name="derive-column-values-by-using-the-derived-column-transformation"></a><span data-ttu-id="ea6df-102">派生列変換を使用して列の値を取得する</span><span class="sxs-lookup"><span data-stu-id="ea6df-102">Derive Column Values by Using the Derived Column Transformation</span></span>
  <span data-ttu-id="ea6df-103">派生列変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの変換元があらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea6df-103">To add and configure a Derived Column transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
 <span data-ttu-id="ea6df-104">派生列変換では、式を使用して既存の値を更新したり、新しい列に値を追加したりします。</span><span class="sxs-lookup"><span data-stu-id="ea6df-104">The Derived Column transformation uses expressions to update the values of existing or to add values to new columns.</span></span> <span data-ttu-id="ea6df-105">新しい列に値を追加することを選択すると、 **[派生列変換エディター]** ダイアログ ボックスによって式が評価され、それに応じて列のメタデータが定義されます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-105">When you choose to add values to new columns, the **Derived Column Transformation Editor** dialog box evaluates the expression and defines the metadata of the columns accordingly.</span></span> <span data-ttu-id="ea6df-106">たとえば、2 つの列 (ぞれぞれデータ型が DT_WSTR で長さが 50) があり、式がこの 2 つの列の値の間にスペースを 1 つ入れて連結する場合、新しい列はデータ型が DT_WSTR で長さが 101 になります。</span><span class="sxs-lookup"><span data-stu-id="ea6df-106">For example, if an expression concatenates two columns-each with the DT_WSTR data type and a length of 50-with a space between the two column values, the new column has the DT_WSTR data type and a length of 101.</span></span> <span data-ttu-id="ea6df-107">新しい列のデータ型は更新することができます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-107">You can update the data type of new columns.</span></span> <span data-ttu-id="ea6df-108">唯一の要件は、挿入されたデータと互換性があるデータ型であることです。</span><span class="sxs-lookup"><span data-stu-id="ea6df-108">The only requirement is that data type be compatible with the inserted data.</span></span> <span data-ttu-id="ea6df-109">たとえば、整数データ型の列に日付の値を割り当てると、 **[派生列変換エディター]** ダイアログ ボックスによって検証エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-109">For example, the **Derived Column Transformation Editor** dialog box generates a validation error when you assign a date value to a column with an integer data type.</span></span> <span data-ttu-id="ea6df-110">選択したデータ型に応じて、列の長さ、有効桁数、小数点以下桁数、およびコード ページを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-110">Depending on the data type that you selected, you can specify the length, precision, scale, and code page of the column.</span></span>  
  
### <a name="to-derive-column-values"></a><span data-ttu-id="ea6df-111">列の値を取得するには</span><span class="sxs-lookup"><span data-stu-id="ea6df-111">To derive column values</span></span>  
  
1.  <span data-ttu-id="ea6df-112">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-112">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="ea6df-113">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-113">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="ea6df-114">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、派生列変換をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ea6df-114">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Derived Column transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="ea6df-115">派生列変換をデータ フローに連結します。連結するには、変換元または前の変換から派生列変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ea6df-115">Connect the Derived Column transformation to the data flow by dragging the connector from the source or the previous transformation to the Derived Column transformation.</span></span>  
  
5.  <span data-ttu-id="ea6df-116">派生列変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea6df-116">Double-click the Derived Column transformation.</span></span>  
  
6.  <span data-ttu-id="ea6df-117">**[派生列変換エディター]** ダイアログ ボックスで、変数、列、関数、および演算子を、グリッドの **[式]** 列にドラッグし、条件として使用する式を構築します。</span><span class="sxs-lookup"><span data-stu-id="ea6df-117">In the **Derived Column Transformation Editor** dialog box, build the expressions to use as conditions by dragging variables, columns, functions, and operators to the **Expression** column in the grid.</span></span> <span data-ttu-id="ea6df-118">**[式]** 列には、式を直接入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-118">Alternatively, you can type the expression in the **Expression** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea6df-119">式が有効でない場合、式のテキストは強調表示され、列のツールヒントにエラーの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-119">If the expression is not valid, the expression text is highlighted and a ToolTip on the column describes the errors.</span></span>  
  
7.  <span data-ttu-id="ea6df-120">**[派生列]** 一覧で、 **[\<add as new column>]** を選択して式の評価結果を新しい列に書き込みます。または、既存の列を選択し、評価結果で更新します。</span><span class="sxs-lookup"><span data-stu-id="ea6df-120">In the **Derived Column** list, select **\<add as new column>** to write the evaluation result of the expression to a new column, or select an existing column to update with the evaluation result.</span></span>  
  
     <span data-ttu-id="ea6df-121">新しい列を使用することを選択した場合は、 **[派生列変換エディター]** ダイアログ ボックスによって式が評価され、データ型、長さ、有効桁数、小数点以下桁数、およびコード ページに応じて列にデータ型が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ea6df-121">If you chose to use a new column, the **Derived Column Transformation Editor** dialog box evaluates the expression and assigns a data type to the column, depending on the data type, length, precisions, scale, and code page.</span></span>  
  
8.  <span data-ttu-id="ea6df-122">新しい列を使用する場合は、 **[データ型]** 一覧でデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea6df-122">If using a new column, select a data type in the **Data Type** list.</span></span> <span data-ttu-id="ea6df-123">選択したデータ型によっては、必要に応じて **[長さ]** 、 **[有効桁数]** 、 **[小数点以下桁数]** 、および **[コード ページ]** 列の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="ea6df-123">Depending on the selected data type, optionally update the values in the **Length**, **Precision**, **Scale**, and **Code Page** columns.</span></span> <span data-ttu-id="ea6df-124">既存の列のメタデータは変更できません。</span><span class="sxs-lookup"><span data-stu-id="ea6df-124">Metadata of existing columns cannot be changed.</span></span>  
  
9. <span data-ttu-id="ea6df-125">必要に応じ、 **[派生列名]** 列の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="ea6df-125">Optionally, modify the values in the **Derived Column Name** column.</span></span>  
  
10. <span data-ttu-id="ea6df-126">エラー出力を構成するには、 **[エラー出力の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea6df-126">To configure the error output, click **Configure Error Output**.</span></span> <span data-ttu-id="ea6df-127">詳細については、「 [データ フロー コンポーネントでエラー出力を構成する](../../configure-an-error-output-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6df-127">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="ea6df-128">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea6df-128">Click **OK**.</span></span>  
  
12. <span data-ttu-id="ea6df-129">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea6df-129">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea6df-130">参照</span><span class="sxs-lookup"><span data-stu-id="ea6df-130">See Also</span></span>  
 <span data-ttu-id="ea6df-131">[Derived Column Transformation](derived-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="ea6df-131">[Derived Column Transformation](derived-column-transformation.md) </span></span>  
 <span data-ttu-id="ea6df-132">[Integration Services のデータ型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ea6df-132">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 <span data-ttu-id="ea6df-133">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="ea6df-133">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="ea6df-134">[Integration Services のパス](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="ea6df-134">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="ea6df-135">[データ フロー タスク](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="ea6df-135">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="ea6df-136">Integration Services &#40;SSIS&#41; 式</span><span class="sxs-lookup"><span data-stu-id="ea6df-136">Integration Services &#40;SSIS&#41; Expressions</span></span>](../../expressions/integration-services-ssis-expressions.md)  
  
  
