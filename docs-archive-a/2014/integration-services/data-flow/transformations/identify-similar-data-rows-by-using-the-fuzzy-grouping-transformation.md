---
title: あいまいグループ化変換を使用して類似のデータ行を識別する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Fuzzy Grouping transformation
- match similar data [Integration Services]
- similar data rows [Integration Services]
- fuzzy matches
ms.assetid: ffcb41a6-e23d-49ea-8c32-ac980e3dc495
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4e6d49548c211b38a35d6f5f7efc3d50fec93588
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644068"
---
# <a name="identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation"></a><span data-ttu-id="57af7-102">あいまいグループ化変換を使用して類似のデータ行を識別する</span><span class="sxs-lookup"><span data-stu-id="57af7-102">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>
  <span data-ttu-id="57af7-103">あいまいグループ化変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの変換元があらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="57af7-103">To add and configure a Fuzzy Grouping transformation, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-implement-fuzzy-grouping-transformation-in-a-data-flow"></a><span data-ttu-id="57af7-104">データ フローにあいまいグループ化変換を実装するには</span><span class="sxs-lookup"><span data-stu-id="57af7-104">To implement Fuzzy Grouping transformation in a data flow</span></span>  
  
1.  <span data-ttu-id="57af7-105">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="57af7-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="57af7-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="57af7-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="57af7-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、あいまいグループ化変換をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="57af7-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Fuzzy Grouping transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="57af7-108">あいまいグループ化変換をデータ フローに連結します。連結するには、データ ソースまたは直前の変換からあいまいグループ化変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="57af7-108">Connect the Fuzzy Grouping transformation to the data flow by dragging the connector from the data source or a previous transformation to the Fuzzy Grouping transformation.</span></span>  
  
5.  <span data-ttu-id="57af7-109">あいまいグループ化変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="57af7-109">Double-click the Fuzzy Grouping transformation.</span></span>  
  
6.  <span data-ttu-id="57af7-110">**[あいまいグループ化変換エディター]** ダイアログ ボックスの **[接続マネージャー]** タブで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに接続する OLE DB 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="57af7-110">In the **Fuzzy Grouping Transformation Editor** dialog box, on the **Connection Manager** tab, select an OLE DB connection manager that connects to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57af7-111">この変換では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに接続し、一時テーブルおよびインデックスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57af7-111">The transformation requires a connection to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database to create temporary tables and indexes.</span></span>  
  
7.  <span data-ttu-id="57af7-112">**[列]** タブをクリックし、 **[使用できる入力列]** 一覧で、データセット内で類似の行を識別するために使用する入力列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="57af7-112">Click the **Columns** tab and, in the **Available Input Columns** list, select the check box of the input columns to use to identify similar rows in the dataset.</span></span>  
  
8.  <span data-ttu-id="57af7-113">**[パススルー]** 列のチェック ボックスをオンにし、変換出力に渡す入力列を指定します。</span><span class="sxs-lookup"><span data-stu-id="57af7-113">Select the check box in the **Pass Through** column to identify the input columns to pass through to the transformation output.</span></span> <span data-ttu-id="57af7-114">パススルー列は、重複する行の識別処理には含まれません。</span><span class="sxs-lookup"><span data-stu-id="57af7-114">Pass-through columns are not included in the process of identification of duplicate rows.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57af7-115">グループ化で使用される入力列は、自動的にパススルー列として選択されます。この入力列は、グループ化で使用されている間は選択解除できません。</span><span class="sxs-lookup"><span data-stu-id="57af7-115">Input columns that are used for grouping are automatically selected as pass-through columns, and they cannot be unselected while used for grouping.</span></span>  
  
9. <span data-ttu-id="57af7-116">必要に応じて、 **[出力の別名]** 列で出力列の名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="57af7-116">Optionally, update the names of output columns in the **Output Alias** column.</span></span>  
  
10. <span data-ttu-id="57af7-117">必要に応じて、 **[グループ出力の別名]** 列で、クリーンにした列の名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="57af7-117">Optionally, update the names of cleaned columns in the **Group OutputAlias** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57af7-118">列の既定の名前は、入力列の名前に "_clean" サフィックスが付いたものとなります。</span><span class="sxs-lookup"><span data-stu-id="57af7-118">The default names of columns are the names of the input columns with a "_clean" suffix.</span></span>  
  
11. <span data-ttu-id="57af7-119">必要に応じて、 **[一致の種類]** 列で、使用する一致の種類を更新します。</span><span class="sxs-lookup"><span data-stu-id="57af7-119">Optionally, update the type of match to use in the **Match Type** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57af7-120">少なくとも 1 列では、あいまい一致を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57af7-120">At least one column must use fuzzy matching.</span></span>  
  
12. <span data-ttu-id="57af7-121">**[最小類似]** 列で、最小の類似レベル列を指定します。</span><span class="sxs-lookup"><span data-stu-id="57af7-121">Specify the minimum similarity level columns in the **Minimum Similarity** column.</span></span> <span data-ttu-id="57af7-122">この値は、0 から 1 までの値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="57af7-122">The value must be between 0 and 1.</span></span> <span data-ttu-id="57af7-123">値が 1 に近づくほど、入力列内の値をグループ化するために必要な類似性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="57af7-123">The closer the value is to 1, the more similar the values in the input columns must be to form a group.</span></span> <span data-ttu-id="57af7-124">最小類似が 1 の場合は、完全一致であることを示します。</span><span class="sxs-lookup"><span data-stu-id="57af7-124">A minimum similarity of 1 indicates an exact match.</span></span>  
  
13. <span data-ttu-id="57af7-125">必要に応じて、 **[類似出力の別名]** 列で、類似列の名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="57af7-125">Optionally, update the names of similarity columns in the **Similarity Output Alias** column.</span></span>  
  
14. <span data-ttu-id="57af7-126">データ値の数値の処理を指定するには、 **[数字]** 列の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="57af7-126">To specify the handling of numbers in data values, update the values in the **Numerals** column.</span></span>  
  
15. <span data-ttu-id="57af7-127">変換による列内の文字列データの比較方法を指定するには、 **[比較フラグ]** 列内にある比較オプションの既定の選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="57af7-127">To specify how the transformation compares the string data in a column, modify the default selection of comparison options in the **Comparison Flags** column.</span></span>  
  
16. <span data-ttu-id="57af7-128">**[詳細設定]** タブをクリックすると、一意の行識別子 (_key_in)、重複の行識別子 (_key_out)、および類似値 (_score) の出力に、変換が追加する列の名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="57af7-128">Click the **Advanced** tab to modify the names of the columns that the transformation adds to the output for the unique row identifier (_key_in), the duplicate row identifier (_key_out), and the similarity value (_score).</span></span>  
  
17. <span data-ttu-id="57af7-129">必要に応じて、スライダー バーを移動して類似のしきい値を調整します。</span><span class="sxs-lookup"><span data-stu-id="57af7-129">Optionally, adjust the similarity threshold by moving the slider bar.</span></span>  
  
18. <span data-ttu-id="57af7-130">必要に応じて、データ内の区切り記号を無視するように、トークン区切り記号のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="57af7-130">Optionally, clear the token delimiter check boxes to ignore delimiters in the data.</span></span>  
  
19. <span data-ttu-id="57af7-131">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57af7-131">Click **OK**.</span></span>  
  
20. <span data-ttu-id="57af7-132">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57af7-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57af7-133">参照</span><span class="sxs-lookup"><span data-stu-id="57af7-133">See Also</span></span>  
 <span data-ttu-id="57af7-134">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="57af7-134">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) </span></span>  
 <span data-ttu-id="57af7-135">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="57af7-135">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="57af7-136">[Integration Services のパス](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="57af7-136">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="57af7-137">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="57af7-137">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
