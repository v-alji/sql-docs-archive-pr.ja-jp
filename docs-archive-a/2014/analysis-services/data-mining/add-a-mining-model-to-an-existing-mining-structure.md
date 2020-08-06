---
title: 既存のマイニング構造へのマイニングモデルの追加 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], adding
- mining structures [Analysis Services], mining models
- adding mining models
ms.assetid: fcf72300-0674-4e73-a826-9b8eeffefbb5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0afdf5f795303eaa8bb672aa80e68e0f1f891607
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643029"
---
# <a name="add-a-mining-model-to-an-existing-mining-structure"></a><span data-ttu-id="c9113-102">既存のマイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="c9113-102">Add a Mining Model to an Existing Mining Structure</span></span>
  <span data-ttu-id="c9113-103">初期モデルを追加した後、マイニング構造にマイニング モデルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="c9113-103">You can add more mining models to a mining structure, after you add the initial model.</span></span> <span data-ttu-id="c9113-104">各モデルには構造内に存在する列が含まれている必要がありますが、列の使用法はマイニング モデルごとにそれぞれ定義できます。</span><span class="sxs-lookup"><span data-stu-id="c9113-104">Each model must contain columns that exist in the structure, but you can define the usage of the columns differently for each mining model.</span></span> <span data-ttu-id="c9113-105">マイニング モデルの列を定義する方法の詳細については、「 [マイニング モデル列](mining-model-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9113-105">For more information about how to define mining models columns, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-add-a-mining-model-to-the-structure"></a><span data-ttu-id="c9113-106">構造にマイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="c9113-106">To add a mining model to the structure</span></span>  
  
1.  <span data-ttu-id="c9113-107">**の** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]メニュー項目から **[新しいマイニング モデル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c9113-107">From the **Mining Model** menu item in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select **New Mining Model**.</span></span>  
  
     <span data-ttu-id="c9113-108">**[新しいマイニング モデル]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9113-108">The **New Mining Model** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="c9113-109">**[モデル名]** で、新しいマイニング モデルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c9113-109">Under **Model name**, enter a name for the new mining model.</span></span>  
  
3.  <span data-ttu-id="c9113-110">**[アルゴリズム名]** で、マイニング モデルを作成するアルゴリズムを選択します。</span><span class="sxs-lookup"><span data-stu-id="c9113-110">Under **Algorithm name**, select the algorithm that the mining model will be built from.</span></span>  
  
4.  <span data-ttu-id="c9113-111">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c9113-111">Click **OK**.</span></span>  
  
 <span data-ttu-id="c9113-112">新しいマイニングモデルが [**マイニングモデル**] タブに表示されます。モデルでは、構造に存在する既定の列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9113-112">A new mining model appears in the **Mining Models** tab. The model uses the default columns that exist in the structure.</span></span> <span data-ttu-id="c9113-113">列を変更する方法については、「 [マイニング モデルのプロパティの変更](change-the-properties-of-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9113-113">For information about how to modify the columns, see [Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9113-114">参照</span><span class="sxs-lookup"><span data-stu-id="c9113-114">See Also</span></span>  
 [<span data-ttu-id="c9113-115">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="c9113-115">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
