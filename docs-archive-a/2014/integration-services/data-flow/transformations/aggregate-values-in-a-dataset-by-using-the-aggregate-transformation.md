---
title: 集計変換を使用してデータセットの値を集計する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregate transformation [Integration Services]
- aggregate values [Integration Services]
- datasets [Integration Services], aggregate values
ms.assetid: 01b81c0f-d5e0-483b-81b2-73800a6945ac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de918c6c2adf194d5808ccd1b64c77a94a52e357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712205"
---
# <a name="aggregate-values-in-a-dataset-by-using-the-aggregate-transformation"></a><span data-ttu-id="23346-102">集計変換を使用してデータセットの値を集計する</span><span class="sxs-lookup"><span data-stu-id="23346-102">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>
  <span data-ttu-id="23346-103">集計変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの変換元があらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="23346-103">To add and configure an Aggregate transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
### <a name="to-aggregate-values-in-a-dataset"></a><span data-ttu-id="23346-104">データセットの値を集計するには</span><span class="sxs-lookup"><span data-stu-id="23346-104">To aggregate values in a dataset</span></span>  
  
1.  <span data-ttu-id="23346-105">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="23346-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="23346-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="23346-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="23346-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、集計変換をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="23346-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Aggregate transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="23346-108">集計変換をデータ フローに連結します。連結するには、変換元または前の変換から集計変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="23346-108">Connect the Aggregate transformation to the data flow by dragging a connector from the source or the previous transformation to the Aggregate transformation.</span></span>  
  
5.  <span data-ttu-id="23346-109">集計変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="23346-109">Double-click the transformation.</span></span>  
  
6.  <span data-ttu-id="23346-110">**[集計変換エディター]** ダイアログ ボックスで、 **[集計]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="23346-110">In the **Aggregate Transformation Editor** dialog box, click the **Aggregations** tab.</span></span>  
  
7.  <span data-ttu-id="23346-111">**[使用できる入力列]** 一覧で、値を集計する列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="23346-111">In the **Available Input Columns** list, select the check box by the columns on which you want to aggregate values.</span></span> <span data-ttu-id="23346-112">選択した列が、テーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="23346-112">The selected columns appear in the table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23346-113">1 つの列を複数回選択して、複数の変換をその列に適用できます。</span><span class="sxs-lookup"><span data-stu-id="23346-113">You can select a column multiple times, applying multiple transformations to the column.</span></span> <span data-ttu-id="23346-114">集計を一意に識別するために、既定の名前に番号が追加され、列の出力が別名で保存されます。</span><span class="sxs-lookup"><span data-stu-id="23346-114">To uniquely identify aggregations, a number is appended to the default name of the output alias of the column.</span></span>  
  
8.  <span data-ttu-id="23346-115">必要に応じ、 **[出力の別名]** 列の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="23346-115">Optionally, modify the value in the **Output Alias** columns.</span></span>  
  
9. <span data-ttu-id="23346-116">既定の集計操作である **[グループ化]** を変更するには、 **[操作]** 一覧で別の操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="23346-116">To change the default aggregation operation, **Group by**, select a different operation in the **Operation** list.</span></span>  
  
10. <span data-ttu-id="23346-117">既定の比較を変更するには、 **[比較フラグ]** 列に示された各比較フラグを選択します。</span><span class="sxs-lookup"><span data-stu-id="23346-117">To change the default comparison, select the individual comparison flags listed in the **Comparison Flags** column.</span></span> <span data-ttu-id="23346-118">既定の比較では、大文字と小文字、ひらがなとカタカナ、非空白文字、および文字幅は無視されます。</span><span class="sxs-lookup"><span data-stu-id="23346-118">By default, a comparison ignores case, kana type, non-spacing characters, and character width.</span></span>  
  
11. <span data-ttu-id="23346-119">**[個別のカウント]** 集計では、必要に応じて、個別の値の正確な数を **[個別カウント キー数]** 列で指定するか、カウントの概数を **[個別カウント スケール]** 列で選択します。</span><span class="sxs-lookup"><span data-stu-id="23346-119">Optionally, for the **Count distinct** aggregation, specify an exact number of distinct values in the **Count Distinct Keys** column, or select an approximate count in the **Count Distinct Scale** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23346-120">個別の値を正確な数または概数で指定することにより、変換作業に適したメモリ量が事前に割り当てられるので、パフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="23346-120">Providing the number of distinct values, exact or approximate, optimizes performance, because the transformation can preallocate an appropriate amount of memory to do its work.</span></span>  
  
12. <span data-ttu-id="23346-121">必要に応じ、 **[詳細設定]** をクリックして集計変換出力の名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="23346-121">Optionally, click **Advanced** and update the name of the Aggregate transformation output.</span></span> <span data-ttu-id="23346-122">集計に操作が含まれている場合は、[キー `Group By` **スケール**] 列でグループ化キー値の概数を選択するか、[**キー** ] 列でグループ化キー値の正確な数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="23346-122">If the aggregations include a `Group By` operation, you can select an approximate count of grouping key values in the **Keys Scale** column or specify an exact number of grouping key values in the **Keys** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23346-123">個別の値を正確な数または概数で指定することにより、変換作業に適したメモリ量が事前に割り当てられるので、パフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="23346-123">Providing the number of distinct values, exact or approximate, optimizes performance, because the transformation can preallocate an appropriate amount of memory to do its work.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23346-124">**[キー スケール]** と **[キー]** オプションは、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="23346-124">The **Keys Scale** and **Keys** options are mutually exclusive.</span></span> <span data-ttu-id="23346-125">両方の列に値を入力した場合、 **[キー スケール]** と **[キー]** のうち、いずれか大きい方の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="23346-125">If you enter values in both columns, the larger value in either **Keys Scale** or **Keys** is used.</span></span>  
  
13. <span data-ttu-id="23346-126">必要に応じ、 **[詳細設定]** タブをクリックして、集計変換が実行するすべての操作を最適化する属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="23346-126">Optionally, click the **Advanced** tab and set the attributes that apply to optimizing all the operations that the Aggregate transformation performs.</span></span>  
  
14. <span data-ttu-id="23346-127">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23346-127">Click **OK**.</span></span>  
  
15. <span data-ttu-id="23346-128">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23346-128">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23346-129">参照</span><span class="sxs-lookup"><span data-stu-id="23346-129">See Also</span></span>  
 <span data-ttu-id="23346-130">[集計変換](aggregate-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="23346-130">[Aggregate Transformation](aggregate-transformation.md) </span></span>  
 <span data-ttu-id="23346-131">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="23346-131">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="23346-132">[Integration Services のパス](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="23346-132">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="23346-133">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="23346-133">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
