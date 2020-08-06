---
title: マイニングモデルのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb086f4a978ca96de8e6fc99f889f718247629af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643617"
---
# <a name="mining-model-properties"></a><span data-ttu-id="b8a6f-102">マイニング モデルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b8a6f-102">Mining Model Properties</span></span>
  <span data-ttu-id="b8a6f-103">マイニング モデルには、次の種類のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-103">Mining models have the following kinds of properties:</span></span>  
  
-   <span data-ttu-id="b8a6f-104">モデルによって使用されるデータのデータ型および内容を定義するマイニング構造から継承されたプロパティ。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-104">Properties that are inherited from the mining structure that define the data type and content type of the data used by the model;</span></span>  
  
-   <span data-ttu-id="b8a6f-105">カスタム パラメーターなど、マイニング モデルの作成に使用されるアルゴリズムに関連するプロパティ。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-105">Properties that are related to the algorithm used to create the mining model, including any customer parameters;</span></span>  
  
-   <span data-ttu-id="b8a6f-106">モデルのトレーニングに使用するモデルに対するフィルターを定義するプロパティ。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-106">Properties that define a filter on the model used to train the model.</span></span>  
  
 <span data-ttu-id="b8a6f-107">マイニング モデルのプロパティは、モデルを作成するときに最初に定義されます。ただし、アルゴリズム パラメーター、フィルター、および列の使用法のプロパティなど、ほとんどのプロパティは後で変更できます。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-107">The properties of a mining model are initially defined when you create the model; however, you can alter most properties later, including the algorithm parameters, filters, and column usage properties.</span></span> <span data-ttu-id="b8a6f-108">プロパティの変更には、データ マイニング デザイナーの **[マイニング モデル]** タブを使用するか、AMO または XMLA を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-108">You change properties by using the **Mining Models** tab of Data Mining Designer, or by using AMO or XMLA.</span></span>  
  
 <span data-ttu-id="b8a6f-109">モデルのいずれかのプロパティを変更した後は、モデルを再処理して、変更内容をモデルに反映させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-109">Whenever you change any property of a model, you must reprocess the model for the changes to be reflected in the model.</span></span> <span data-ttu-id="b8a6f-110">列の別名や説明の追加など、変更がメタデータのみに関連する場合でも、再処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-110">Reprocessing is required even if the change only involves metadata, such as adding a column alias or description.</span></span>  
  
## <a name="properties-of-models"></a><span data-ttu-id="b8a6f-111">モデルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b8a6f-111">Properties of Models</span></span>  
 <span data-ttu-id="b8a6f-112">次の表で、マイニング モデルに固有のプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-112">The following table describes the properties that are specific to mining models.</span></span> <span data-ttu-id="b8a6f-113">また、マイニング モデルの個々の列に設定できるプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-113">Additionally, there are properties that you can set on individual columns in the mining</span></span>  
  
|<span data-ttu-id="b8a6f-114">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b8a6f-114">Property</span></span>|<span data-ttu-id="b8a6f-115">説明</span><span class="sxs-lookup"><span data-stu-id="b8a6f-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b8a6f-116">**アルゴリズム**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-116">**Algorithm**</span></span>|<span data-ttu-id="b8a6f-117">マイニング モデルのアルゴリズムの種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-117">Sets the algorithm type for the mining model.</span></span>|  
|<span data-ttu-id="b8a6f-118">**AlgorithmParameters**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-118">**AlgorithmParameters**</span></span>|<span data-ttu-id="b8a6f-119">アルゴリズムの各種類で使用可能なアルゴリズム パラメーターの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-119">Sets values for algorithm parameters that are available for each algorithm type.</span></span>|  
|<span data-ttu-id="b8a6f-120">**Assert**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-120">**Filter**</span></span>|<span data-ttu-id="b8a6f-121">マイニング モデルのトレーニングとテストに使用するデータに適用するフィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-121">Sets a filter that is applied to the data that is used for training and testing the mining model.</span></span> <span data-ttu-id="b8a6f-122">フィルター定義はモデルと共に格納され、予測クエリの作成時やモデル精度のテスト時に必要に応じて使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-122">The filter definition is stored with the model and can be used optionally when you create prediction queries, or when you test the accuracy of the model.</span></span><br /><br /> <span data-ttu-id="b8a6f-123">モデルのトレーニング時には、モデルのフィルターは省略できません。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-123">The model filter is not optional when training the model.</span></span>|  
|<span data-ttu-id="b8a6f-124">**名前**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-124">**Name**</span></span>|<span data-ttu-id="b8a6f-125">マイニング モデルの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-125">Sets the name of the mining model.</span></span>|  
|<span data-ttu-id="b8a6f-126">**AllowDrillThrough**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-126">**AllowDrillThrough**</span></span>|<span data-ttu-id="b8a6f-127">マイニング モデルでドリルスルーを有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-127">Specifies whether drill through is enabled on the mining model.</span></span>|  
  
## <a name="properties-of-model-columns"></a><span data-ttu-id="b8a6f-128">モデル列のプロパティ</span><span class="sxs-lookup"><span data-stu-id="b8a6f-128">Properties of Model Columns</span></span>  
 <span data-ttu-id="b8a6f-129">マイニング モデルの各列に対して、次のデータ マイニング固有のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-129">You can set the following data mining-specific properties for each column in a mining model.</span></span> <span data-ttu-id="b8a6f-130">これらのプロパティには、マイニング構造内のマイニング モデルごとに異なる値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-130">You can set these properties to a different value for each mining model in a mining structure.</span></span>  
  
|<span data-ttu-id="b8a6f-131">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b8a6f-131">Property</span></span>|<span data-ttu-id="b8a6f-132">説明</span><span class="sxs-lookup"><span data-stu-id="b8a6f-132">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b8a6f-133">**説明**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-133">**Description**</span></span>|<span data-ttu-id="b8a6f-134">マイニング列の目的について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-134">Describes the purpose of the mining column.</span></span>|  
|<span data-ttu-id="b8a6f-135">**名前**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-135">**Name**</span></span>|<span data-ttu-id="b8a6f-136">マイニング モデル列の名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-136">Sets the name of the mining model column.</span></span> <span data-ttu-id="b8a6f-137">新しい名前を入力し、マイニング モデル列に別名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-137">You can type a new name, to provide an alias for the mining model column.</span></span>|  
|<span data-ttu-id="b8a6f-138">**ModelingFlags**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-138">**ModelingFlags**</span></span>|<span data-ttu-id="b8a6f-139">列に対してアルゴリズム固有のフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-139">Sets any algorithm-specific flags for the column.</span></span>|  
|<span data-ttu-id="b8a6f-140">**SourceColumnID**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-140">**SourceColumnID**</span></span>|<span data-ttu-id="b8a6f-141">モデル列の基になるマイニング構造列の名前を示します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-141">Indicates the name of the mining structure column on which the model column is based.</span></span><br /><br /> <span data-ttu-id="b8a6f-142">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-142">This property is read-only.</span></span>|  
|<span data-ttu-id="b8a6f-143">**使用方法**</span><span class="sxs-lookup"><span data-stu-id="b8a6f-143">**Usage**</span></span>|<span data-ttu-id="b8a6f-144">マイニング モデルによる列の使用方法を設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-144">Sets how the column will be used by the mining model.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8a6f-145">参照</span><span class="sxs-lookup"><span data-stu-id="b8a6f-145">See Also</span></span>  
 <span data-ttu-id="b8a6f-146">[マイニングモデル列](mining-model-columns.md) </span><span class="sxs-lookup"><span data-stu-id="b8a6f-146">[Mining Model Columns](mining-model-columns.md) </span></span>  
 <span data-ttu-id="b8a6f-147">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b8a6f-147">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b8a6f-148">[マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b8a6f-148">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="b8a6f-149">[マイニングモデルのプロパティの変更](change-the-properties-of-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="b8a6f-149">[Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md) </span></span>  
 <span data-ttu-id="b8a6f-150">[データマイニングツール](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b8a6f-150">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="b8a6f-151">[リレーショナルマイニング構造の作成](create-a-relational-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="b8a6f-151">[Create a Relational Mining Structure](create-a-relational-mining-structure.md) </span></span>  
 [<span data-ttu-id="b8a6f-152">モデル列の別名の作成</span><span class="sxs-lookup"><span data-stu-id="b8a6f-152">Create an Alias for a Model Column</span></span>](create-an-alias-for-a-model-column.md)  
  
  
