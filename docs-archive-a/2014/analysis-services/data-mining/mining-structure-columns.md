---
title: マイニング構造列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], columns
- data sources [Analysis Services], mining structure columns
- columns [data mining], mining structure columns
ms.assetid: 20cbf433-70d1-4b61-a462-41a8435b27b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0caebfaef9b80be2d8fb5586a061dcccd31981f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643607"
---
# <a name="mining-structure-columns"></a><span data-ttu-id="9840d-102">マイニング構造列</span><span class="sxs-lookup"><span data-stu-id="9840d-102">Mining Structure Columns</span></span>
  <span data-ttu-id="9840d-103">マイニング構造を作成するときは、外部データの列を選択し、データをどのようにモデリングに使用するかを指定して、マイニング構造の列を定義します。</span><span class="sxs-lookup"><span data-stu-id="9840d-103">You define the columns in a mining structure when you create the mining structure, by choosing columns of external data and then specifying how the data is to be used for modeling.</span></span> <span data-ttu-id="9840d-104">したがって、マイニング構造列は、単なるデータ ソースのデータのコピーではなく、マイニング モデルでソースのデータがどのように使用するかを定義するものです。</span><span class="sxs-lookup"><span data-stu-id="9840d-104">Therefore, mining structure columns are more than copies of data from a data source: they define how the data from the source is to be used by the mining model.</span></span> <span data-ttu-id="9840d-105">データの分離方法を決定するプロパティ (データ値の分布を記述するプロパティ) を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="9840d-105">You can assign properties that determine how the data is discretized, properties that describe how the data values are distributed</span></span>  
  
 <span data-ttu-id="9840d-106">マイニング構造列は、柔軟性と拡張性を併せ持つように設計されています。これは、マイニング モデルの作成に使用する各アルゴリズムによって、構造内のさまざまな列を使用してデータが解釈される場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="9840d-106">Mining structure columns are designed to be flexible and extensible, because each algorithm that you use to build a mining model may use different columns from the structure to interpret the data.</span></span> <span data-ttu-id="9840d-107">モデルごとに 1 つずつデータ セットを用意する代わりに、1 つのマイニング構造を使用し、そこに含まれる列を使用して各モデルのデータをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="9840d-107">Rather than have one set of data for each model, you can use a single mining structure and use the columns in it to customize the data for each model.</span></span>  
  
## <a name="defining-mining-structure-columns"></a><span data-ttu-id="9840d-108">マイニング構造列の定義</span><span class="sxs-lookup"><span data-stu-id="9840d-108">Defining Mining Structure Columns</span></span>  
 <span data-ttu-id="9840d-109">構造列を定義する基本データ型およびコンテンツの種類は、構造を作成するために使用するデータ ソースから派生します。</span><span class="sxs-lookup"><span data-stu-id="9840d-109">The basic data types and content types that define structure columns are derived from the data source that you use to create the structure.</span></span> <span data-ttu-id="9840d-110">これらの設定はマイニング構造内で変更でき、モデリング フラグの設定や連続した列の分布の設定も行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9840d-110">You can change these settings within the mining structure, and you can also set modeling flags and set the distribution for continuous columns.</span></span>  
  
 <span data-ttu-id="9840d-111">マイニング構造列の定義には、次の情報を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9840d-111">The definition of a mining structure column must contain the following information:</span></span>  
  
-   <span data-ttu-id="9840d-112">**ID**: 列の一意の名前。通常は名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="9840d-112">**ID**: The unique name of the column, often the same as the name.</span></span> <span data-ttu-id="9840d-113">マイニング構造の作成後、名前は変更することができますが、ID は変更できません。</span><span class="sxs-lookup"><span data-stu-id="9840d-113">This cannot be changed after you create the mining structure, whereas the name can be changed.</span></span>  
  
-   <span data-ttu-id="9840d-114">**名前**: 列の名前または別名。</span><span class="sxs-lookup"><span data-stu-id="9840d-114">**Name**: A name or alias for the column.</span></span>  
  
-   <span data-ttu-id="9840d-115">**コンテンツ**: データが不連続であるか連続であるかを表す列挙体。</span><span class="sxs-lookup"><span data-stu-id="9840d-115">**Content**: An enumeration that describes whether the data is discrete or continuous.</span></span>  
  
-   <span data-ttu-id="9840d-116">**型**: 一般的なデータ型を示す列挙体。</span><span class="sxs-lookup"><span data-stu-id="9840d-116">**Type**: An enumeration that indicates the general data type.</span></span>  
  
-   <span data-ttu-id="9840d-117">**分布**: 予想される値の分布を示す列挙体。</span><span class="sxs-lookup"><span data-stu-id="9840d-117">**Distribution**: An enumeration that describes the expected distribution of values.</span></span> <span data-ttu-id="9840d-118">分布は列が連続している場合に含まれます。</span><span class="sxs-lookup"><span data-stu-id="9840d-118">A distribution is included if the column is continuous.</span></span>  
  
-   <span data-ttu-id="9840d-119">**モデリング フラグ**: 不足値などの処理方法を示す列挙体。</span><span class="sxs-lookup"><span data-stu-id="9840d-119">**Modeling flags**: An enumeration that indicates how to handle missing values and so forth.</span></span> <span data-ttu-id="9840d-120">モデリング フラグはマイニング モデルに対して定義することもできますが、モデル フラグは構造列に使用されるフラグとは異なります。</span><span class="sxs-lookup"><span data-stu-id="9840d-120">Modeling flags can also be defined on the mining model, but the model flags are different than the flags used on structure columns.</span></span>  
  
-   <span data-ttu-id="9840d-121">**バインド**: ソース データを指定するプロパティ。</span><span class="sxs-lookup"><span data-stu-id="9840d-121">**Bindings**: Properties that specify the source data.</span></span>  
  
 <span data-ttu-id="9840d-122">サードパーティのアルゴリズムには、マイニング構造列で定義できるカスタム プロパティが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9840d-122">Third-party algorithms may also include custom properties that can be defined on the mining structure column.</span></span>  
  
 <span data-ttu-id="9840d-123">データ マイニング構造とデータ マイニング モデル オブジェクトの詳細については、「 [マイニング構造 (Analysis Services - データ マイニング)](mining-structures-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9840d-123">For more information about the data mining structure and the data mining model, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="9840d-124">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="9840d-124">Related Content</span></span>  
 <span data-ttu-id="9840d-125">マイニング構造列を定義および使用する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9840d-125">See the following topics for more information about how to define and use mining structure columns.</span></span>  
  
|<span data-ttu-id="9840d-126">トピック</span><span class="sxs-lookup"><span data-stu-id="9840d-126">Topic</span></span>|<span data-ttu-id="9840d-127">リンク</span><span class="sxs-lookup"><span data-stu-id="9840d-127">Links</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="9840d-128">マイニング構造列の定義に使用できるデータ型について説明します。</span><span class="sxs-lookup"><span data-stu-id="9840d-128">Describes the data types that you can use to define a mining structure column.</span></span>|[<span data-ttu-id="9840d-129">データ型 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9840d-129">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)|  
|<span data-ttu-id="9840d-130">マイニング構造列に含まれるデータのそれぞれの型に対して使用できるコンテンツの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="9840d-130">Describes the content types that are available for each type of data that is contained in a mining structure column.</span></span> <span data-ttu-id="9840d-131">コンテンツの種類はデータ型に依存します。</span><span class="sxs-lookup"><span data-stu-id="9840d-131">Content types are dependent on data type.</span></span> <span data-ttu-id="9840d-132">コンテンツの種類はモデル レベルで割り当てられ、モデルで列データを使用する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="9840d-132">The content type is assigned at the model level, and determines how the column data is used by the model.</span></span>|[<span data-ttu-id="9840d-133">コンテンツの種類 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9840d-133">Content Types &#40;Data Mining&#41;</span></span>](content-types-data-mining.md)|  
|<span data-ttu-id="9840d-134">入れ子になったテーブルの概念を紹介し、入れ子になったテーブルをマイニング構造列としてデータ ソースに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9840d-134">Introduces the concept of nested tables, and explains how nested tables can be added to the data source as mining structure columns.</span></span>|[<span data-ttu-id="9840d-135">分類済みの列 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9840d-135">Classified Columns &#40;Data Mining&#41;</span></span>](classified-columns-data-mining.md)|  
|<span data-ttu-id="9840d-136">予想される列の値の分布を指定するためにマイニング構造列に設定できる分布プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9840d-136">Lists and explains the distribution properties that you can set on a mining structure column to specify the expected distribution of values in the column.</span></span>|[<span data-ttu-id="9840d-137">列の分布 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9840d-137">Column Distributions &#40;Data Mining&#41;</span></span>](column-distributions-data-mining.md)|  
|<span data-ttu-id="9840d-138">分離 (*ビン分割*と呼ばれることもあります) の概念について説明し、連続する数値データを分離するために Analysis Services に用意されている方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9840d-138">Explains the concept of discretization (sometimes referred to as *binning*) and describes the methods that Analysis Services provides for discretizing continuous numeric data.</span></span>|[<span data-ttu-id="9840d-139">分離メソッド (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9840d-139">Discretization Methods &#40;Data Mining&#41;</span></span>](discretization-methods-data-mining.md)|  
|<span data-ttu-id="9840d-140">マイニング構造列に設定できるモデリング フラグについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9840d-140">Describes the modeling flags that you can set on a mining structure column.</span></span>|[<span data-ttu-id="9840d-141">モデリング フラグ (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9840d-141">Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|  
|<span data-ttu-id="9840d-142">マイニング構造列どうしを関連付けるために使用できる特殊な列である分類済みの列について説明します。</span><span class="sxs-lookup"><span data-stu-id="9840d-142">Describes classified columns, which are a special type of column that you can use to relate one mining structure column to another.</span></span>|[<span data-ttu-id="9840d-143">分類済みの列 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9840d-143">Classified Columns &#40;Data Mining&#41;</span></span>](classified-columns-data-mining.md)|  
|<span data-ttu-id="9840d-144">マイニング構造列を追加および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9840d-144">Learn to add and modify mining structure columns.</span></span>|[<span data-ttu-id="9840d-145">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="9840d-145">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)|  
  
## <a name="see-also"></a><span data-ttu-id="9840d-146">参照</span><span class="sxs-lookup"><span data-stu-id="9840d-146">See Also</span></span>  
 <span data-ttu-id="9840d-147">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9840d-147">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="9840d-148">マイニング モデル列</span><span class="sxs-lookup"><span data-stu-id="9840d-148">Mining Model Columns</span></span>](mining-model-columns.md)  
  
  
