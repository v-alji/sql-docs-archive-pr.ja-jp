---
title: マイニング構造のソースキューブのフィルター処理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61409b4803f43d3ff2634daaba65a92bc343db36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633444"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a><span data-ttu-id="d1356-102">マイニング構造のソース キューブのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="d1356-102">Filter the Source Cube for a Mining Structure</span></span>
  <span data-ttu-id="d1356-103">多次元モデル (OLAP キューブ) のデータに基づくマイニング構造を作成する場合は、マイニング構造の基になっているキューブを*スライス*することができます。</span><span class="sxs-lookup"><span data-stu-id="d1356-103">When you create a mining structure that is based on data in a multidimensional model (an OLAP cube), you can *slice* the cube that the mining structure is based on.</span></span> <span data-ttu-id="d1356-104">スライスを行うことにより、マイニング モデルのトレーニングに使用するデータに対するフィルターの種類として、データのサブセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1356-104">Slicing lets you create subsets of data, as a kind of filter on the data that is used to train the mining model.</span></span>  
  
### <a name="to-slice-a-cube"></a><span data-ttu-id="d1356-105">キューブをスライスするには</span><span class="sxs-lookup"><span data-stu-id="d1356-105">To slice a cube</span></span>  
  
1.  <span data-ttu-id="d1356-106">のデータマイニングデザイナーで、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] [**マイニング構造**] タブまたは [**マイニングモデル**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1356-106">In Data Mining Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], select the **Mining Structure** tab or the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="d1356-107">[**マイニングモデル**] メニューの [**マイニング構造キューブスライスの定義**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1356-107">On the **Mining Model** menu, select **Define Mining Structure Cube Slice**.</span></span>  
  
     <span data-ttu-id="d1356-108">[**キューブのスライス**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1356-108">The **Slice Cube** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="d1356-109">[**キューブのスライス**] ダイアログボックスの [**ディメンション**] 列で、フィルター処理するディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1356-109">In the **Dimension** column of the **Slice Cube** dialog box, select the dimension that you want to filter.</span></span>  
  
4.  <span data-ttu-id="d1356-110">[**階層**] 列の一覧を使用して、階層のレベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1356-110">Select a level of a hierarchy, using the list in the **Hierarchy** column.</span></span>  
  
5.  <span data-ttu-id="d1356-111">フィルター条件の作成に使用する演算子を [**演算子**] 列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="d1356-111">Select an operator from the list in the **Operator** column, to use in building the filter condition.</span></span>  
  
6.  <span data-ttu-id="d1356-112">[**フィルター** ] 列のボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1356-112">Click the box in the **Filter** column.</span></span>  
  
     <span data-ttu-id="d1356-113">指定した階層レベルのメンバーをすべて含むダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1356-113">A dialog box opens that contains all the members at the specified level of the hierarchy.</span></span>  
  
7.  <span data-ttu-id="d1356-114">フィルター選択する 1 つまたは複数のメンバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1356-114">Select the member or members on which you want to filter.</span></span>  
  
8.  <span data-ttu-id="d1356-115">[メンバー] ダイアログボックスで [ **OK** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1356-115">Click **OK** in the member dialog box.</span></span>  
  
9. <span data-ttu-id="d1356-116">[**キューブのスライス**] ダイアログボックスで [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1356-116">Click **OK** in the **Slice Cube** dialog box.</span></span>  
  
     <span data-ttu-id="d1356-117">キューブ スライスの定義に従って、ソース キューブがフィルター選択されます。</span><span class="sxs-lookup"><span data-stu-id="d1356-117">The source cube is now filtered as defined by the cube slice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1356-118">参照</span><span class="sxs-lookup"><span data-stu-id="d1356-118">See Also</span></span>  
 <span data-ttu-id="d1356-119">[マイニング構造のタスクと操作方法](data-mining/mining-structure-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="d1356-119">[Mining Structure Tasks and How-tos](data-mining/mining-structure-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="d1356-120">新規の OLAP マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="d1356-120">Create a New OLAP Mining Structure</span></span>](data-mining/create-a-new-olap-mining-structure.md)  
  
  
