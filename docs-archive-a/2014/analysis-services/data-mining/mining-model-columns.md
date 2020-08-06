---
title: マイニングモデル列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f936f3f4e0b8f65326e9a6e84f75e6f4e82657f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715886"
---
# <a name="mining-model-columns"></a><span data-ttu-id="96c52-102">マイニング モデル列</span><span class="sxs-lookup"><span data-stu-id="96c52-102">Mining Model Columns</span></span>
  <span data-ttu-id="96c52-103">データ マイニング モデルは、マイニング構造によって表されるデータにマイニング モデル アルゴリズムを適用します。</span><span class="sxs-lookup"><span data-stu-id="96c52-103">A data mining model applies a mining model algorithm to the data that is represented by a mining structure.</span></span> <span data-ttu-id="96c52-104">マイニング構造と同様に、マイニング モデルには列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96c52-104">Like the mining structure, the mining model contains columns.</span></span> <span data-ttu-id="96c52-105">マイニング モデルはマイニング構造内に含まれ、マイニング構造によって定義されるプロパティのすべての値を継承します。</span><span class="sxs-lookup"><span data-stu-id="96c52-105">A mining model is contained within the mining structure, and inherits all the values of the properties that are defined by the mining structure.</span></span> <span data-ttu-id="96c52-106">マイニング モデルは、マイニング構造に含まれているすべての列またはその一部を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="96c52-106">The model can use all the columns that the mining structure contains or a subset of the columns.</span></span>  
  
 <span data-ttu-id="96c52-107">マイニング モデル列には、使用法とモデリング フラグという 2 つの追加情報を定義できます。</span><span class="sxs-lookup"><span data-stu-id="96c52-107">You can define two additional pieces of information on a mining model column: usage, and modeling flags.</span></span>  
  
-   <span data-ttu-id="96c52-108">**使用法** は、モデルで列がどのように使用されるかを定義するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="96c52-108">**Usage** is a property that defines how the model uses the column.</span></span> <span data-ttu-id="96c52-109">列は、入力列、キー列、または予測可能列として使用できます。</span><span class="sxs-lookup"><span data-stu-id="96c52-109">Columns can be used as input columns, key columns, or predictable columns.</span></span>  
  
-   <span data-ttu-id="96c52-110">**モデリング フラグ** では、アルゴリズムがより正確なモデルを作成できるように、ケース テーブルに定義されているデータに関する追加情報をアルゴリズムに提供します。</span><span class="sxs-lookup"><span data-stu-id="96c52-110">**Modeling flags** provide the algorithm with additional information about the data that is defined in the case table, so that the algorithm can build a more accurate model.</span></span> <span data-ttu-id="96c52-111">モデリング フラグは、データ マイニング拡張機能 (DMX) 言語を使用してプログラムで定義するか、または **の** データ マイニング デザイナー [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で定義できます。</span><span class="sxs-lookup"><span data-stu-id="96c52-111">You can define modeling flags programmatically by using the Data Mining Extensions (DMX) language, or in **Data Mining Designer** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="96c52-112">次に、マイニング モデル列で定義できるモデリング フラグを示します。</span><span class="sxs-lookup"><span data-stu-id="96c52-112">The following list describes the modeling flags that you can define on a mining model column.</span></span>  
  
 `MODEL_EXISTENCE_ONLY`  
 <span data-ttu-id="96c52-113">属性の存在が属性列の値よりも重要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="96c52-113">Indicates that the presence of the attribute is more important than the values that are in the attribute column.</span></span> <span data-ttu-id="96c52-114">たとえば、特定の顧客に関連付けられている発注品目の一覧が含まれたケース テーブルについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="96c52-114">For example, consider a case table that contains a list of order items that are associated with a particular customer.</span></span> <span data-ttu-id="96c52-115">テーブル データには、各発注品目の製品タイプ、ID、およびコストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="96c52-115">The table data includes the product type, ID, and cost of each item.</span></span> <span data-ttu-id="96c52-116">モデリングには、顧客が特定の発注品目を購入したという事実の方が、発注品目そのもののコストよりも重要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="96c52-116">For modeling purposes, the fact that the customer purchased a particular order item may be more important than the cost of the order item itself.</span></span> <span data-ttu-id="96c52-117">この場合は、コスト列を `MODEL_EXISTENCE_ONLY` として設定します。</span><span class="sxs-lookup"><span data-stu-id="96c52-117">In this case, the cost column should be marked as `MODEL_EXISTENCE_ONLY`.</span></span>  
  
 `REGRESSOR`  
 <span data-ttu-id="96c52-118">アルゴリズムが、指定した列を回帰アルゴリズムの回帰式に使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="96c52-118">Indicates that the algorithm can use the specified column in the regression formula of regression algorithms.</span></span> <span data-ttu-id="96c52-119">このフラグは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリーと [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ アルゴリズムでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="96c52-119">This flag is supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithms.</span></span>  
  
 <span data-ttu-id="96c52-120">使用法プロパティの設定と、DMX を使用したプログラムによるモデリング フラグの定義について詳しくは、「[CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96c52-120">For more information about setting the usage property and defining modeling flags programmatically with DMX, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span> <span data-ttu-id="96c52-121">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]での使用法プロパティの設定およびモデリング フラグの定義について詳しくは、「 [データ マイニング オブジェクトの移動](moving-data-mining-objects.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96c52-121">For more information about setting the usage property and defining modeling flags in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Moving Data Mining Objects](moving-data-mining-objects.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c52-122">参照</span><span class="sxs-lookup"><span data-stu-id="96c52-122">See Also</span></span>  
 <span data-ttu-id="96c52-123">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="96c52-123">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="96c52-124">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="96c52-124">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="96c52-125">[マイニングモデルのプロパティの変更](change-the-properties-of-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="96c52-125">[Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md) </span></span>  
 <span data-ttu-id="96c52-126">[マイニングモデルからの列の除外](exclude-a-column-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="96c52-126">[Exclude a Column from a Mining Model](exclude-a-column-from-a-mining-model.md) </span></span>  
 [<span data-ttu-id="96c52-127">マイニング構造列</span><span class="sxs-lookup"><span data-stu-id="96c52-127">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
