---
title: 条件分割変換を使用してデータセットを分割する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2efbc3973db1ab1b6b61f6de879e451319b50e49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644052"
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a><span data-ttu-id="c725e-102">条件分割変換を使用してデータセットを分割する</span><span class="sxs-lookup"><span data-stu-id="c725e-102">Split a Dataset by Using the Conditional Split Transformation</span></span>
  <span data-ttu-id="c725e-103">条件分割変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの変換元があらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c725e-103">To add and configure a Conditional Split transformation, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-conditionally-split-a-dataset"></a><span data-ttu-id="c725e-104">データセットを条件に応じて分割するには</span><span class="sxs-lookup"><span data-stu-id="c725e-104">To conditionally split a dataset</span></span>  
  
1.  <span data-ttu-id="c725e-105">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c725e-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="c725e-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="c725e-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c725e-107">**[データ フロー]** タブをクリックし、 **[ツールボックス]** で、条件分割変換をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c725e-107">Click the **Data Flow** tab, and, from the **Toolbox**, drag the Conditional Split transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="c725e-108">条件分割変換をデータ フローに連結します。連結するには、データ ソースまたは前の変換から条件分割変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c725e-108">Connect the Conditional Split transformation to the data flow by dragging the connector from the data source or the previous transformation to the Conditional Split transformation.</span></span>  
  
5.  <span data-ttu-id="c725e-109">条件分割変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c725e-109">Double-click the Conditional Split transformation.</span></span>  
  
6.  <span data-ttu-id="c725e-110">**[条件分割変換エディター]** で、変数、列、関数、および演算子を、グリッドの **[条件]** 列にドラッグし、条件として使用する式を構築します。</span><span class="sxs-lookup"><span data-stu-id="c725e-110">In the **Conditional Split Transformation Editor**, build the expressions to use as conditions by dragging variables, columns, functions, and operators to the **Condition** column in the grid.</span></span> <span data-ttu-id="c725e-111">**[条件]** 列には、式を直接入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="c725e-111">Or, you can type the expression in the **Condition** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c725e-112">1 つの変数または列を、複数の式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c725e-112">A variable or column can be used in multiple expressions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c725e-113">式が有効でない場合、式のテキストは強調表示され、列のツールヒントにエラーの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c725e-113">If the expression is not valid, the expression text is highlighted and a ToolTip on the column describes the errors.</span></span>  
  
7.  <span data-ttu-id="c725e-114">必要に応じ、 **[出力名]** 列の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="c725e-114">Optionally, modify the values in the **Output Name** column.</span></span> <span data-ttu-id="c725e-115">既定の名前は、Case 1、Case 2 などとなります。</span><span class="sxs-lookup"><span data-stu-id="c725e-115">The default names are Case 1, Case 2, and so forth.</span></span>  
  
8.  <span data-ttu-id="c725e-116">条件が評価される順序を変更するには、上矢印または下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c725e-116">To modify the sequence in which the conditions are evaluated, click the up arrow or down arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c725e-117">該当する可能性が最も高い条件を、一覧の先頭に配置します。</span><span class="sxs-lookup"><span data-stu-id="c725e-117">Place the conditions that are most likely to be encountered at the top of the list.</span></span>  
  
9. <span data-ttu-id="c725e-118">必要に応じて、どの条件にも一致しないデータ行の、既定の出力名を変更します。</span><span class="sxs-lookup"><span data-stu-id="c725e-118">Optionally, modify the name of the default output for data rows that do not match any condition.</span></span>  
  
10. <span data-ttu-id="c725e-119">エラー出力を構成するには、 **[エラー出力の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c725e-119">To configure an error output, click **Configure Error Output**.</span></span> <span data-ttu-id="c725e-120">詳細については、「 [データ フロー コンポーネントでエラー出力を構成する](../../configure-an-error-output-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c725e-120">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="c725e-121">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c725e-121">Click **OK**.</span></span>  
  
12. <span data-ttu-id="c725e-122">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c725e-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c725e-123">参照</span><span class="sxs-lookup"><span data-stu-id="c725e-123">See Also</span></span>  
 <span data-ttu-id="c725e-124">[Conditional Split Transformation](conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="c725e-124">[Conditional Split Transformation](conditional-split-transformation.md) </span></span>  
 <span data-ttu-id="c725e-125">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="c725e-125">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="c725e-126">[Integration Services のパス](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="c725e-126">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="c725e-127">[Integration Services のデータ型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="c725e-127">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 <span data-ttu-id="c725e-128">[データ フロー タスク](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="c725e-128">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="c725e-129">Integration Services &#40;SSIS&#41; 式</span><span class="sxs-lookup"><span data-stu-id="c725e-129">Integration Services &#40;SSIS&#41; Expressions</span></span>](../../expressions/integration-services-ssis-expressions.md)  
  
  
