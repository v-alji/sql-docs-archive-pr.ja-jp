---
title: マイニングモデルからの列の除外 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30affebc143184c6287858f60b5d4f5d089c322a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634731"
---
# <a name="exclude-a-column-from-a-mining-model"></a><span data-ttu-id="1af28-102">マイニング モデルからの列の除外</span><span class="sxs-lookup"><span data-stu-id="1af28-102">Exclude a Column from a Mining Model</span></span>
  <span data-ttu-id="1af28-103">新しいマイニング モデルを作成するとき、基となるマイニング構造に存在するすべての列を使用しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="1af28-103">When you create a new mining model, you may not want to use all the columns that exist in the mining structure on which the model is based.</span></span> <span data-ttu-id="1af28-104">たとえば、ドリルスルーのために顧客名列を追加したものの、モデル化には使用したくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="1af28-104">For example, you might have added a customer name column for drillthrough, but don't want to use it for modeling.</span></span> <span data-ttu-id="1af28-105">または、列の複数のコピーをそれぞれ異なる分離で作成して、各モデルで 1 つのコピーのみ使用し、残りは無視する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1af28-105">Or, you might decide to create multiple copies of a column with different discretizations, and use only one of the copies in each model, and ignore the rest.</span></span> <span data-ttu-id="1af28-106">複数の異なるモデルで入力列を選択的に追加して、追加した変数が出力列に与える影響を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="1af28-106">You could also selectively add input columns in several different models to see how the added variable affects the output column.</span></span>  
  
 <span data-ttu-id="1af28-107">列の組み合わせごとに新しいマイニング構造を作成する必要はありません。代わりに、特定のモデルで使用されていないことを示すフラグを列に設定できます。</span><span class="sxs-lookup"><span data-stu-id="1af28-107">You do not need to create a new mining structure for each combination of columns; instead, you can simply flag a column as not being used in a particular model.</span></span>  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a><span data-ttu-id="1af28-108">マイニング モデルから列を除外するには</span><span class="sxs-lookup"><span data-stu-id="1af28-108">To exclude a column from a mining model</span></span>  
  
1.  <span data-ttu-id="1af28-109">**のデータ マイニング デザイナーの** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブにある適切なマイニング モデルで、除外する列に対応するセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="1af28-109">In the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the cell that corresponds to the column you want to exclude, under the appropriate mining model.</span></span>  
  
2.  <span data-ttu-id="1af28-110">ドロップダウン リスト ボックスから **[無視]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1af28-110">Select **Ignore** from the drop-down list box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af28-111">参照</span><span class="sxs-lookup"><span data-stu-id="1af28-111">See Also</span></span>  
 [<span data-ttu-id="1af28-112">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="1af28-112">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
