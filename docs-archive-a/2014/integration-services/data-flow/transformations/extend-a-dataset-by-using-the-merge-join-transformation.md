---
title: マージ結合変換を使用してデータセットを拡張する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Merge Join transformation
- datasets [Integration Services], joining
- datasets [Integration Services], extending
- joining datasets [Integration Services]
ms.assetid: 9e512c3c-f89b-45f3-8281-cdb8f35a2b1f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a387c4ad840eb739d36023be9323c063dcb9a68e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633237"
---
# <a name="extend-a-dataset-by-using-the-merge-join-transformation"></a><span data-ttu-id="7c4f0-102">マージ結合変換を使用してデータセットを拡張する</span><span class="sxs-lookup"><span data-stu-id="7c4f0-102">Extend a Dataset by Using the Merge Join Transformation</span></span>
  <span data-ttu-id="7c4f0-103">マージ結合変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと、マージ結合変換への入力を提供する 2 つのデータ フロー コンポーネントがあらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-103">To add and configure a Merge Join transformation, the package must already include at least one Data Flow task and two data flow components that provide inputs to the Merge Join transformation.</span></span>  
  
 <span data-ttu-id="7c4f0-104">マージ結合変換には、2 つの並べ替え済み入力が必要です。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-104">The Merge Join transformation requires two sorted inputs.</span></span> <span data-ttu-id="7c4f0-105">詳細については、「 [マージ変換およびマージ結合変換用にデータを並べ替える](sort-data-for-the-merge-and-merge-join-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-105">For more information, see [Sort Data for the Merge and Merge Join Transformations](sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
### <a name="to-extend-a-dataset"></a><span data-ttu-id="7c4f0-106">データセットを拡張するには</span><span class="sxs-lookup"><span data-stu-id="7c4f0-106">To extend a dataset</span></span>  
  
1.  <span data-ttu-id="7c4f0-107">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-107">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="7c4f0-108">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="7c4f0-109">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、マージ結合変換をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-109">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Merge Join transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="7c4f0-110">マージ結合変換をデータ フローに連結します。連結するには、データ ソースまたは直前の変換からマージ結合変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-110">Connect the Merge Join transformation to the data flow by dragging the connector from a data source or a previous transformation to the Merge Join transformation.</span></span>  
  
5.  <span data-ttu-id="7c4f0-111">マージ結合変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-111">Double-click the Merge Join transformation.</span></span>  
  
6.  <span data-ttu-id="7c4f0-112">**[マージ結合変換エディター]** ダイアログ ボックスで、 **[結合の種類]** ボックスの一覧から使用する結合の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-112">In the **Merge Join Transformation Editor** dialog box, select the type of join to use in the **Join type** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7c4f0-113">**[左外部結合]** を選択した場合、 **[入力の入れ替え]** をクリックして入力を切り替え、左外部結合を右外部結合に変換できます。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-113">If you select the **Left outer join** type, you can click **Swap Inputs** to switch the inputs and convert the left outer join to a right outer join.</span></span>  
  
7.  <span data-ttu-id="7c4f0-114">左辺の入力内の列を、右辺の入力内の列にドラッグし、結合列を指定します。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-114">Drag columns in the left input to columns in the right input to specify the join columns.</span></span> <span data-ttu-id="7c4f0-115">列の名前が同じ場合、 **[結合キー]** チェック ボックスをオンにすると、マージ結合変換は自動的に結合を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-115">If the columns have the same name, you can select the **Join Key** check box and the Merge Join transformation automatically creates the join.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7c4f0-116">並べ替えの位置が同じ列のみの結合を作成できます。この場合、並べ替えの位置によって指定された順序で結合を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-116">You can create joins only between columns that have the same sort position, and the joins must be created in the order specified by the sort position.</span></span> <span data-ttu-id="7c4f0-117">順序が正しくない結合を作成しようとすると、 **[マージ結合変換エディター]** で、スキップした並べ替えの位置に対して、追加の結合を作成するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-117">If you attempt to create the joins out of order, the **Merge Join Transformation Editor** prompts you to create additional joins for the skipped sort order positions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7c4f0-118">既定では、出力は結合列に基づいて並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-118">By default, the output is sorted on the join columns.</span></span>  
  
8.  <span data-ttu-id="7c4f0-119">左辺の入力および右辺の入力で、出力に追加して含める列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-119">In the left and right inputs, select the check boxes of additional columns to include in the output.</span></span> <span data-ttu-id="7c4f0-120">結合列は、既定で含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-120">Join columns are included by default.</span></span>  
  
9. <span data-ttu-id="7c4f0-121">必要に応じて、 **[出力の別名]** 列で出力列の名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-121">Optionally, update the names of output columns in the **Output Alias** column.</span></span>  
  
10. <span data-ttu-id="7c4f0-122">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-122">Click **OK**.</span></span>  
  
11. <span data-ttu-id="7c4f0-123">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7c4f0-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4f0-124">参照</span><span class="sxs-lookup"><span data-stu-id="7c4f0-124">See Also</span></span>  
 <span data-ttu-id="7c4f0-125">[マージ結合変換](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="7c4f0-125">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="7c4f0-126">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="7c4f0-126">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="7c4f0-127">[Integration Services のパス](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="7c4f0-127">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="7c4f0-128">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="7c4f0-128">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
