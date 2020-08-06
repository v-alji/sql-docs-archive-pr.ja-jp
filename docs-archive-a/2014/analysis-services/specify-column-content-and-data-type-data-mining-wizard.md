---
title: '[列のコンテンツおよびデータ型の指定] (データマイニングウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0634be64-4c38-4381-9b19-fe9a5889306c
author: minewiskan
ms.author: owend
ms.openlocfilehash: e22f46808877391376f721bcab55ea4fd9074186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639682"
---
# <a name="specify-column-content-and-data-type-data-mining-wizard"></a><span data-ttu-id="5440a-102">[列のコンテンツおよびデータ型の指定] (データ マイニング ウィザード)</span><span class="sxs-lookup"><span data-stu-id="5440a-102">Specify Column Content and Data Type (Data Mining Wizard)</span></span>
  <span data-ttu-id="5440a-103">**[列のコンテンツおよびデータ型の指定]** ページを使用すると、ウィザードの前のページで選択した各列に対し、使用法とデータ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5440a-103">Use the **Specify Column Content and Data Type** page to specify the usage and data type for each column that you selected on the previous page of the wizard.</span></span> <span data-ttu-id="5440a-104">列を無視するには、 **[戻る]** をクリックして **[トレーニング データの指定]** ページに戻り、すべてのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5440a-104">If you want to ignore the column, click **Back** to return to the page **Specify the Training Data**, and clear all checkboxes.</span></span>  
  
 <span data-ttu-id="5440a-105">列の使用法は、モデルにおけるデータの使用方法を表します。</span><span class="sxs-lookup"><span data-stu-id="5440a-105">The usage of a column indicates how the data will be used in the model.</span></span> <span data-ttu-id="5440a-106">シリーズを特定するキー、分析に使用する入力値、または予測する値として、列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5440a-106">A column can be used as a key to identify a series, as an input value to use in analysis, or as the value that you want to predict.</span></span> <span data-ttu-id="5440a-107">列は、予測と入力の両方に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5440a-107">Columns can be used for both prediction and input.</span></span>  
  
 <span data-ttu-id="5440a-108">データ型では、列に格納されるデータの型に関する追加の詳細と、そのデータがトレーニング中にどのように使用されるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-108">The data type specifies additional detail about the type of data that is contained in the column, and how the data will be used during training.</span></span> <span data-ttu-id="5440a-109">コンテンツの種類によっては特定のデータ型が必要とされることも、この逆の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5440a-109">Some content types require a specific data type, and vice versa.</span></span> <span data-ttu-id="5440a-110">マイニング モデルの作成時に使用するアルゴリズムによっては、特定のデータ型を指定する必要が生じる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5440a-110">You might also need to specify a particular data type depending on the algorithm that you use when you create a mining model.</span></span> <span data-ttu-id="5440a-111">マイニング モデルとマイニング構造におけるコンテンツの種類とデータ型については、「[コンテンツの種類 (データ マイニング)](data-mining/content-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5440a-111">For information about content types and data types in mining models and structures, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="5440a-112">**詳細:** [マイニング構造 &#40;Analysis Services - データ マイニング&#41;](data-mining/mining-structures-analysis-services-data-mining.md)、[マイニング モデル列](data-mining/mining-model-columns.md)、[データ マイニング ウィザード &#40;Analysis Services - データ マイニング&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[リレーショナル マイニング構造の作成](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="5440a-112">**For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Mining Model Columns](data-mining/mining-model-columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="5440a-113">Options</span><span class="sxs-lookup"><span data-stu-id="5440a-113">Options</span></span>  
 <span data-ttu-id="5440a-114">**[マイニング モデル構造]**</span><span class="sxs-lookup"><span data-stu-id="5440a-114">**Mining model structure**</span></span>  
 <span data-ttu-id="5440a-115">ウィザードの前のページで選択した、ビューおよび入れ子になったテーブルの列を表示します。</span><span class="sxs-lookup"><span data-stu-id="5440a-115">Displays the columns from the views and nested tables that you selected on the previous page of the wizard.</span></span>  
  
 <span data-ttu-id="5440a-116">**[列]**</span><span class="sxs-lookup"><span data-stu-id="5440a-116">**Columns**</span></span>  
 <span data-ttu-id="5440a-117">列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5440a-117">Lists the columns.</span></span>  
  
 <span data-ttu-id="5440a-118">**Content type**</span><span class="sxs-lookup"><span data-stu-id="5440a-118">**Content type**</span></span>  
 <span data-ttu-id="5440a-119">列のコンテンツの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-119">Specify the content type for the column.</span></span> <span data-ttu-id="5440a-120">ウィザードの前のページで列をキーとして指定した場合、使用できる値は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5440a-120">If you specified that the column is a key on the previous page of the wizard, the following values are available:</span></span>  
  
|<span data-ttu-id="5440a-121">オプション</span><span class="sxs-lookup"><span data-stu-id="5440a-121">Option</span></span>|<span data-ttu-id="5440a-122">説明</span><span class="sxs-lookup"><span data-stu-id="5440a-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5440a-123">Key</span><span class="sxs-lookup"><span data-stu-id="5440a-123">Key</span></span>|<span data-ttu-id="5440a-124">ケース シリーズの一意の識別子を列に格納することを指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-124">Specify that the column contains a unique identifier for the case series.</span></span>|  
|<span data-ttu-id="5440a-125">Key Sequence</span><span class="sxs-lookup"><span data-stu-id="5440a-125">Key Sequence</span></span>|<span data-ttu-id="5440a-126">シーケンス ID を列に格納することを指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-126">Specify that the column contains a sequence identifier.</span></span>|  
|<span data-ttu-id="5440a-127">[キー時刻]</span><span class="sxs-lookup"><span data-stu-id="5440a-127">Key Time</span></span>|<span data-ttu-id="5440a-128">日付またはタイム シリーズを識別するための、日付など、一意の連続する数値を列に格納することを指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-128">Specify that the column contains a date or other unique continuous number that is used to identify a date or time series.</span></span>|  
  
 <span data-ttu-id="5440a-129">列をキー以外の列として選択した場合、使用できる値は以下のとおりで、データ型に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="5440a-129">If you selected the column as a non-key column, the following values are available, depending on the data type:</span></span>  
  
|<span data-ttu-id="5440a-130">オプション</span><span class="sxs-lookup"><span data-stu-id="5440a-130">Option</span></span>|<span data-ttu-id="5440a-131">説明</span><span class="sxs-lookup"><span data-stu-id="5440a-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5440a-132">継続的</span><span class="sxs-lookup"><span data-stu-id="5440a-132">Continuous</span></span>|<span data-ttu-id="5440a-133">連続する数値を列に格納することを指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-133">Specify that the column contains continuous numeric values.</span></span>|  
|<span data-ttu-id="5440a-134">Discretized</span><span class="sxs-lookup"><span data-stu-id="5440a-134">Discretized</span></span>|<span data-ttu-id="5440a-135">分離された数値か、不連続値として処理可能な数値を列に格納することを指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-135">Specify that the column contains numeric values that either have been discretized, or can be treated as discrete values.</span></span>|  
|<span data-ttu-id="5440a-136">離散</span><span class="sxs-lookup"><span data-stu-id="5440a-136">Discrete</span></span>|<span data-ttu-id="5440a-137">テキストなど数値以外の値を列に格納することを指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-137">Specify that the column contains text or other nonnumeric values.</span></span>|  
  
 <span data-ttu-id="5440a-138">**データの種類**</span><span class="sxs-lookup"><span data-stu-id="5440a-138">**Data type**</span></span>  
 <span data-ttu-id="5440a-139">列のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="5440a-139">Specify the data type for the column.</span></span>  
  
 <span data-ttu-id="5440a-140">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5440a-140">The following values are available:</span></span>  
  
-   `Boolean`  
  
-   `Date`  
  
-   `Double`  
  
-   `Long`  
  
-   `Text`  
  
 <span data-ttu-id="5440a-141">**Detect**</span><span class="sxs-lookup"><span data-stu-id="5440a-141">**Detect**</span></span>  
 <span data-ttu-id="5440a-142">すべての数値列でデータのサンプルを分析します。</span><span class="sxs-lookup"><span data-stu-id="5440a-142">Analyze a sample of data in all numeric columns.</span></span> <span data-ttu-id="5440a-143">指定した **[コンテンツの種類]** 値を、推奨されるコンテンツの種類に置換します。</span><span class="sxs-lookup"><span data-stu-id="5440a-143">Replaces specified **Content Type** values with a recommended content type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5440a-144">参照</span><span class="sxs-lookup"><span data-stu-id="5440a-144">See Also</span></span>  
 <span data-ttu-id="5440a-145">[データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5440a-145">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="5440a-146">[データマイニングウィザード &#40;関連する列の提案&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="5440a-146">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="5440a-147">[データマイニングウィザード &#40;テーブルの種類の指定&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="5440a-147">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="5440a-148">列のコンテンツとデータ型 &#40;データマイニングウィザードを指定し&#41;</span><span class="sxs-lookup"><span data-stu-id="5440a-148">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
