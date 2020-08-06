---
title: '[ソースキューブディメンションの選択] (データマイニングウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectsourcecube.f1
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6295a5312b4501236e0ce8f5776fc43c0d014581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633345"
---
# <a name="select-the-source-cube-dimension-data-mining-wizard"></a><span data-ttu-id="3d992-102">[ソース キューブ ディメンションの選択] (データ マイニング ウィザード)</span><span class="sxs-lookup"><span data-stu-id="3d992-102">Select the Source Cube Dimension (Data Mining Wizard)</span></span>
  <span data-ttu-id="3d992-103">**[ソース キューブ ディメンションの選択]** ページを使用すると、分析する対象のケースを含んでいるキューブからディメンションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3d992-103">Use the **Select the Source Cube Dimension** page to select the dimension from the cube that contains the cases you want to analyze.</span></span> <span data-ttu-id="3d992-104">たとえば、人口統計に基づいて顧客の購入行動を分析するモデルを構築する場合は、Customer ディメンションを選択します。一般に、このディメンションには、顧客ごとに固有のレコードが含まれているほか、性別、居住地、所得など、人口統計の内訳を表す各種の属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3d992-104">For example, if you are building a model that analyzes the purchasing behavior of customers based on demographics, you would select the Customer dimension, which typically contains a unique record for each customer and various attributes that represent demographics, such as gender, location, or income.</span></span> <span data-ttu-id="3d992-105">ウィザードの後半では、このケース テーブルに関連したテーブルを追加できます。たとえば、顧客が購入した製品を表す、入れ子になったテーブルを追加することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3d992-105">Later in the wizard you will have the opportunity to add a table that is related to this case table: for example, you might add a nested table that shows which products the customer has purchased.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d992-106"> このページは、ウィザードの **[定義方法の選択]** ページで **[既存のキューブを使用する]** を選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d992-106">This page will appear only if you have selected **From existing cube** on the **Select the Definition Method** page of the wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3d992-107">Options</span><span class="sxs-lookup"><span data-stu-id="3d992-107">Options</span></span>  
 <span data-ttu-id="3d992-108">**[ソース キューブ ディメンションの選択]**</span><span class="sxs-lookup"><span data-stu-id="3d992-108">**Select a Source Cube Dimension**</span></span>  
 <span data-ttu-id="3d992-109">マイニング構造のソース データを提供するキューブのディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3d992-109">Select the dimension of the cube that will provide the source data for your mining structure.</span></span>  
  
## <a name="choosing-a-dimension"></a><span data-ttu-id="3d992-110">ディメンションの選択</span><span class="sxs-lookup"><span data-stu-id="3d992-110">Choosing a Dimension</span></span>  
 <span data-ttu-id="3d992-111">モデルに使用するディメンションは 1 つしか選択できません。したがって、キューブの構造を十分に理解し、目的のモデルに合った情報を提供するうえで最も適したディメンションを選ぶことが重要です。</span><span class="sxs-lookup"><span data-stu-id="3d992-111">Because you can select only one dimension for use in your model, it is important that you understand the cube structure and select the dimension that provides the best information for your model.</span></span> <span data-ttu-id="3d992-112">どのディメンションを使用すればよいか迷った場合は、ディメンション デザイナーを使用してキューブを参照し、そこに含まれているフィールドとデータを調べます。</span><span class="sxs-lookup"><span data-stu-id="3d992-112">If you are not sure which dimension to use, it might be helpful to browse the cube and review the fields and the data in them by using Dimension Designer.</span></span> <span data-ttu-id="3d992-113">詳細については、「[ディメンション デザイナーでのディメンション データの参照](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3d992-113">For more information, see [Browse Dimension Data in Dimension Designer](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md).</span></span>  
  
 <span data-ttu-id="3d992-114">ディメンション全般について詳しく理解するには、「[ディメンションの概要 (Analysis Services - 多次元データ)](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3d992-114">If you are unfamiliar with dimensions in general, see [Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="3d992-115">データ マイニングに役立つ属性やメジャーなど、1 つのディメンションに含まれる代表的な情報の種類については、「[ディメンション リレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3d992-115">For more information about the type of information that is typically contained in a single dimension, including attributes and measures that might be useful for data mining, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
 <span data-ttu-id="3d992-116">データ マイニング モデルを構築するために必要な属性が、選択したディメンションにない場合は、ディメンションに対する変更が必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="3d992-116">If the dimension that you choose does not contain all of the related attributes that you need to build the data mining model, you might need to modify the dimension.</span></span> <span data-ttu-id="3d992-117">詳細については、「 [データベース ディメンションの定義](multidimensional-models/define-database-dimensions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3d992-117">For more information, see [Define Database Dimensions](multidimensional-models/define-database-dimensions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d992-118">参照</span><span class="sxs-lookup"><span data-stu-id="3d992-118">See Also</span></span>  
 <span data-ttu-id="3d992-119">[データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3d992-119">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3d992-120">[データマイニング構造 &#40;データマイニングウィザードの作成&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3d992-120">[Create the Data Mining Structure &#40;Data Mining Wizard&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="3d992-121">[[ケースキー &#40;データマイニングウィザード] を選択し&#41;](select-the-case-key-data-mining-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="3d992-121">[Select the Case Key &#40;Data Mining Wizard&#41;](select-the-case-key-data-mining-wizard.md)</span></span>  
  
  
