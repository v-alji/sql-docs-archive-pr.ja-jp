---
title: マイニングモデルタスクと操作方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], models
- mining models [Analysis Services], how-to topics
ms.assetid: 7c2073e5-b40f-4bf8-aa51-021adb08e072
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3648e8e47cc1954eaf8bca1e3608e9abbdf82b02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643615"
---
# <a name="mining-model-tasks-and-how-tos"></a><span data-ttu-id="72ed4-102">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="72ed4-102">Mining Model Tasks and How-tos</span></span>
  <span data-ttu-id="72ed4-103">マイニング構造のマイニング モデルを管理および処理するには、 **のデータ マイニング デザイナーにある** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="72ed4-103">Use the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to manage and process mining models in a mining structure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72ed4-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="72ed4-104">In This Section</span></span>  
  
-   [<span data-ttu-id="72ed4-105">既存のマイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="72ed4-105">Add a Mining Model to an Existing Mining Structure</span></span>](add-a-mining-model-to-an-existing-mining-structure.md)  
  
-   [<span data-ttu-id="72ed4-106">マイニング構造からのマイニング モデルの削除</span><span class="sxs-lookup"><span data-stu-id="72ed4-106">Delete a Mining Model from a Mining Structure</span></span>](delete-a-mining-model-from-a-mining-structure.md)  
  
-   [<span data-ttu-id="72ed4-107">マイニング モデルからの列の除外</span><span class="sxs-lookup"><span data-stu-id="72ed4-107">Exclude a Column from a Mining Model</span></span>](exclude-a-column-from-a-mining-model.md)  
  
-   [<span data-ttu-id="72ed4-108">モデル列の別名の作成</span><span class="sxs-lookup"><span data-stu-id="72ed4-108">Create an Alias for a Model Column</span></span>](create-an-alias-for-a-model-column.md)  
  
-   [<span data-ttu-id="72ed4-109">マイニング モデルでの列の分離の変更</span><span class="sxs-lookup"><span data-stu-id="72ed4-109">Change the Discretization of a Column in a Mining Model</span></span>](change-the-discretization-of-a-column-in-a-mining-model.md)  
  
-   [<span data-ttu-id="72ed4-110">モデリング フラグの表示または変更 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="72ed4-110">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
-   [<span data-ttu-id="72ed4-111">モデルでリグレッサーとして使用する列の指定</span><span class="sxs-lookup"><span data-stu-id="72ed4-111">Specify a Column to Use as Regressor in a Model</span></span>](specify-a-column-to-use-as-regressor-in-a-model.md)  
  
-   [<span data-ttu-id="72ed4-112">マイニング モデルのプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="72ed4-112">Change the Properties of a Mining Model</span></span>](change-the-properties-of-a-mining-model.md)  
  
-   [<span data-ttu-id="72ed4-113">マイニング モデルへのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="72ed4-113">Apply a Filter to a Mining Model</span></span>](apply-a-filter-to-a-mining-model.md)  
  
-   [<span data-ttu-id="72ed4-114">マイニング モデルからのフィルターの削除</span><span class="sxs-lookup"><span data-stu-id="72ed4-114">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
-   [<span data-ttu-id="72ed4-115">マイニング モデルのドリルスルーの有効化</span><span class="sxs-lookup"><span data-stu-id="72ed4-115">Enable Drillthrough for a Mining Model</span></span>](enable-drillthrough-for-a-mining-model.md)  
  
-   [<span data-ttu-id="72ed4-116">アルゴリズム パラメーターの表示または変更</span><span class="sxs-lookup"><span data-stu-id="72ed4-116">View or Change Algorithm Parameters</span></span>](view-or-change-algorithm-parameters.md)  
  
-   [<span data-ttu-id="72ed4-117">マイニング モデルのコピーの作成</span><span class="sxs-lookup"><span data-stu-id="72ed4-117">Make a Copy of a Mining Model</span></span>](make-a-copy-of-a-mining-model.md)  
  
-   [<span data-ttu-id="72ed4-118">マイニング モデルの処理</span><span class="sxs-lookup"><span data-stu-id="72ed4-118">Process a Mining Model</span></span>](process-a-mining-model.md)  
  
-   [<span data-ttu-id="72ed4-119">データ マイニング ディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="72ed4-119">Create a Data Mining Dimension</span></span>](create-a-data-mining-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="72ed4-120">参照</span><span class="sxs-lookup"><span data-stu-id="72ed4-120">See Also</span></span>  
 <span data-ttu-id="72ed4-121">[マイニング構造のタスクと操作方法](mining-structure-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="72ed4-121">[Mining Structure Tasks and How-tos](mining-structure-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="72ed4-122">[マイニングモデル &#40;Analysis Services-データマイニング&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="72ed4-122">[Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="72ed4-123">データマイニングの概念</span><span class="sxs-lookup"><span data-stu-id="72ed4-123">Data Mining Concepts</span></span>](data-mining-concepts.md)  
  
  
