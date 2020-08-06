---
title: 全体結合変換を使用してデータをマージする | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- merging datasets [Integration Services]
- merging inputs [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e782a5770ab9936e4c5cc84da706a5472ecd4d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644055"
---
# <a name="merge-data-by-using-the-union-all-transformation"></a><span data-ttu-id="ffe13-102">全体結合変換を使用してデータをマージする</span><span class="sxs-lookup"><span data-stu-id="ffe13-102">Merge Data by Using the Union All Transformation</span></span>
  <span data-ttu-id="ffe13-103">全体結合変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 2 つのデータ ソースがあらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffe13-103">To add and configure a Union All transformation, the package must already include at least one Data Flow task and two data sources.</span></span>  
  
 <span data-ttu-id="ffe13-104">全体結合変換は、複数の入力を結合します。</span><span class="sxs-lookup"><span data-stu-id="ffe13-104">The Union All transformation combines multiple inputs.</span></span> <span data-ttu-id="ffe13-105">この変換に連結される最初の入力は参照入力であり、その後に連結される入力はセカンダリ入力と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ffe13-105">The first input that is connected to the transformation is the reference input, and the inputs connected subsequently are the secondary inputs.</span></span> <span data-ttu-id="ffe13-106">出力には、参照入力内の列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ffe13-106">The output includes the columns in the reference input.</span></span>  
  
### <a name="to-combine-inputs-in-a-data-flow"></a><span data-ttu-id="ffe13-107">データ フローの入力を結合するには</span><span class="sxs-lookup"><span data-stu-id="ffe13-107">To combine inputs in a data flow</span></span>  
  
1.  <span data-ttu-id="ffe13-108">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、ソリューション エクスプローラー内のパッケージをダブルクリックし、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでそのパッケージを開きます。次に、 **[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffe13-108">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], double-click the package in Solution Explorer to open the package in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, and then click the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="ffe13-109">**[ツールボックス]** で、全体結合変換を **[データ フロー]** タブのデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ffe13-109">From the **Toolbox**, drag the Union All transformation to the design surface of the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="ffe13-110">全体結合変換をデータ フローに連結します。連結するには、データ ソースまたは前の変換から全体結合変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ffe13-110">Connect the Union All transformation to the data flow by dragging a connector from the data source or a previous transformation to the Union All transformation.</span></span>  
  
4.  <span data-ttu-id="ffe13-111">全体結合変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffe13-111">Double-click the Union All transformation.</span></span>  
  
5.  <span data-ttu-id="ffe13-112">**[全体結合変換エディター]** で、入力の一覧の行をクリックして次に列を選択し、入力の列を **[出力列の名前]** 一覧にある列にマップします。</span><span class="sxs-lookup"><span data-stu-id="ffe13-112">In the **Union All Transformation Editor**, map a column from an input to a column in the **Output Column Name** list by clicking a row and then selecting a column in the input list.</span></span> <span data-ttu-id="ffe13-113">列のマッピングをスキップするには、入力の一覧で **[\<ignore>]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffe13-113">Select **\<ignore>** in the input list to skip mapping the column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ffe13-114">2 つの列の間のマッピングでは、列のメタデータが一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffe13-114">The mapping between two columns requires that the metadata of the columns match.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ffe13-115">参照列にマップされないセカンダリ入力の列は、出力では NULL 値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ffe13-115">Columns in a secondary input that are not mapped to reference columns are set to null values in the output.</span></span>  
  
6.  <span data-ttu-id="ffe13-116">必要に応じて、 **[出力列の名前]** 列で列の名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="ffe13-116">Optionally, modify the names of columns in the **Output Column Name** column.</span></span>  
  
7.  <span data-ttu-id="ffe13-117">各入力の列ごとに、手順 5. と 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="ffe13-117">Repeat steps 5 and 6 for each column in each input.</span></span>  
  
8.  <span data-ttu-id="ffe13-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffe13-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="ffe13-119">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffe13-119">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe13-120">参照</span><span class="sxs-lookup"><span data-stu-id="ffe13-120">See Also</span></span>  
 <span data-ttu-id="ffe13-121">[全体結合変換](union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="ffe13-121">[Union All Transformation](union-all-transformation.md) </span></span>  
 <span data-ttu-id="ffe13-122">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="ffe13-122">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="ffe13-123">[Integration Services のパス](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="ffe13-123">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="ffe13-124">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="ffe13-124">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
