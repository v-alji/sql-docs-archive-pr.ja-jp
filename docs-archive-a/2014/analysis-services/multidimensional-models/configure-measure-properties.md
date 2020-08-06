---
title: メジャーのプロパティの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- additivity [Analysis Services]
- ID property
- ErrorConfiguration property
- AggregateFunction property
- DisplayFolder property
- IgnoreUnrelatedDimensions property
- FormatString property
- Description property
- semiadditive
- properties [Analysis Services], measure groups
- aggregate functions [Analysis Services]
- DataType property
- ProcessingMode property
- MeasureExpression property
- AggregationPrefix property
- Visible property
- properties [Analysis Services], measures
- StorageLocation property
- StorageMode property
- formats [Analysis Services], measures
- Source property
- aggregations [Analysis Services], measures
- measures [Analysis Services], properties
- nonadditive [Analysis Services]
- Name property
- measures [Analysis Services], display formats
- ProcessingPriority property
- measure groups [Analysis Services], properties
- Type property
- ProactiveCaching property
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ca291a5181fdb3f7a88845431d61ffd7a1034eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737110"
---
# <a name="configure-measure-properties"></a><span data-ttu-id="5ba26-102">メジャーのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="5ba26-102">Configure Measure Properties</span></span>
  <span data-ttu-id="5ba26-103">メジャーには、メジャーの動作を定義し、メジャーがユーザーに表示される方法を制御できるプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="5ba26-103">Measures have properties that enable you to define how the measures function and to control how the measures appear to users.</span></span>  
  
 <span data-ttu-id="5ba26-104">キューブまたはメジャーを作成または編集する際、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="5ba26-104">You can set properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] when creating or editing a cube or measure.</span></span> <span data-ttu-id="5ba26-105">また、MDX または AMO を使用してプログラムで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5ba26-105">You can also set them programmatically, using MDX or AMO.</span></span> <span data-ttu-id="5ba26-106">詳細については、「[多次元モデル内のメジャーおよびメジャー グループの作成](create-measures-and-measure-groups-in-multidimensional-models.md)」、「[CREATE MEMBER ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member)」、または「[AMO OLAP 基本オブジェクトのプログラミング](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ba26-106">See [Create Measures and Measure Groups in Multidimensional Models](create-measures-and-measure-groups-in-multidimensional-models.md) or [CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) or [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects) for details.</span></span>  
  
## <a name="measure-properties"></a><span data-ttu-id="5ba26-107">メジャーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="5ba26-107">Measure Properties</span></span>  
 <span data-ttu-id="5ba26-108">プロパティがメジャー レベルでオーバーライドされない限り、メジャーはメンバーになっているメジャー グループから特定のプロパティを継承します。</span><span class="sxs-lookup"><span data-stu-id="5ba26-108">Measures inherit certain properties from the measure group of which they are a member, unless those properties are overridden at the measure level.</span></span> <span data-ttu-id="5ba26-109">メジャーのプロパティは、メジャーの集計方法、データ型、表示名、メジャーの表示フォルダー、書式設定文字列、メジャーの式、基になるソース列、およびユーザーに対する表示や非表示を決定します。</span><span class="sxs-lookup"><span data-stu-id="5ba26-109">Measure properties determine how a measure is aggregated, its data type, the name that is displayed to the user, the display folder in which the measure will appear, its format string, any measure expression, the underlying source column, and its visibility to users.</span></span>  
  
|<span data-ttu-id="5ba26-110">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5ba26-110">Property</span></span>|<span data-ttu-id="5ba26-111">定義</span><span class="sxs-lookup"><span data-stu-id="5ba26-111">Definition</span></span>|  
|--------------|----------------|  
|`AggregateFunction`|<span data-ttu-id="5ba26-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="5ba26-112">Required.</span></span> <span data-ttu-id="5ba26-113">メジャーの集計方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="5ba26-113">Determines how measures are aggregated.</span></span> <span data-ttu-id="5ba26-114">`Sum` は既定の集計です。</span><span class="sxs-lookup"><span data-stu-id="5ba26-114">`Sum` is the default aggregation.</span></span> <span data-ttu-id="5ba26-115">各関数の詳しい説明については、「 [集計関数の使用](use-aggregate-functions.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ba26-115">For more information, see [Use Aggregate Functions](use-aggregate-functions.md) for a description of each function.</span></span>|  
|`DataType`|<span data-ttu-id="5ba26-116">必須。</span><span class="sxs-lookup"><span data-stu-id="5ba26-116">Required.</span></span> <span data-ttu-id="5ba26-117">メジャーのバインド先である、基になるファクト テーブル列のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ba26-117">Specifies the data type of the column in the underlying fact table to which the measure is bound.</span></span> <span data-ttu-id="5ba26-118">既定では、この値は基になる列から継承されます。</span><span class="sxs-lookup"><span data-stu-id="5ba26-118">This value is inherited from the source column by default.</span></span>|  
|`Description`|<span data-ttu-id="5ba26-119">メジャーの説明を指定します。クライアント アプリケーションに表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5ba26-119">Provides a description of the measure, which may be exposed in client applications.</span></span>|  
|`DisplayFolder`|<span data-ttu-id="5ba26-120">ユーザーがキューブに接続するとメジャーが表示されるフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="5ba26-120">Specifies the folder in which the measure will appear when users connect to the cube.</span></span> <span data-ttu-id="5ba26-121">キューブに多くのメジャーがある場合、表示フォルダーを使用すると、メジャーを分類して表示を見やすく改善できます。</span><span class="sxs-lookup"><span data-stu-id="5ba26-121">When a cube has many measures, you can use display folders to categorize the measures and improve the user browsing experience.</span></span>|  
|`FormatString`|<span data-ttu-id="5ba26-122">メジャーの `FormatString` プロパティを使用すると、メジャー値の表示に使用する形式を選択できます。</span><span class="sxs-lookup"><span data-stu-id="5ba26-122">You can select the format that is used to display measure values to users by using the `FormatString` property of the measure.</span></span><br /><br /> <span data-ttu-id="5ba26-123">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に表示形式の一覧が用意されていますが、一覧にはない追加形式を複数指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ba26-123">Although a list of display formats is provided in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can specify many additional formats that are not in the list.</span></span> <span data-ttu-id="5ba26-124">Microsoft Visual Basic で有効な名前付き形式またはユーザー定義形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ba26-124">You can specify any named or user-defined format that is valid in Microsoft Visual Basic.</span></span>|  
|`ID`|<span data-ttu-id="5ba26-125">必須。</span><span class="sxs-lookup"><span data-stu-id="5ba26-125">Required.</span></span> <span data-ttu-id="5ba26-126">メジャーの一意識別子 (ID) です。</span><span class="sxs-lookup"><span data-stu-id="5ba26-126">Displays the unique identifier (ID) of the measure.</span></span> <span data-ttu-id="5ba26-127">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="5ba26-127">This property is read-only.</span></span>|  
|`MeasureExpression`|<span data-ttu-id="5ba26-128">メジャーの値を定義する、制約付きの MDX 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ba26-128">Specifies a constrained MDX expression defining the value of the measure.</span></span> <span data-ttu-id="5ba26-129">式は、集計前にリーフ レベルで評価され、値の重み付けができるようになります。</span><span class="sxs-lookup"><span data-stu-id="5ba26-129">The expression is evaluated at the leaf level before being aggregated, and allows for weighting of a value.</span></span> <span data-ttu-id="5ba26-130">たとえば、売上高が為替レートで重み付けされる通貨の換算などです。</span><span class="sxs-lookup"><span data-stu-id="5ba26-130">For example, in currency conversion where a sales amount is weighted by the exchange rate.</span></span>|  
|`Name`|<span data-ttu-id="5ba26-131">必須。</span><span class="sxs-lookup"><span data-stu-id="5ba26-131">Required.</span></span> <span data-ttu-id="5ba26-132">メジャーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ba26-132">Specifies the name of the measure.</span></span>|  
|`Source`|<span data-ttu-id="5ba26-133">必須。</span><span class="sxs-lookup"><span data-stu-id="5ba26-133">Required.</span></span> <span data-ttu-id="5ba26-134">メジャーがバインドされるデータ ソース ビューの列を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ba26-134">Specifies the column in the data source view to which the measure is bound.</span></span> <span data-ttu-id="5ba26-135">詳細については、「[データ ソースとバインド &#40;SSAS 多次元&#41;](data-sources-and-bindings-ssas-multidimensional.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ba26-135">See [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](data-sources-and-bindings-ssas-multidimensional.md).</span></span>|  
|`Visible`|<span data-ttu-id="5ba26-136">クライアント アプリケーションでメジャーの表示/非表示を決定します。</span><span class="sxs-lookup"><span data-stu-id="5ba26-136">Determines the visibility of the measure in client applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ba26-137">参照</span><span class="sxs-lookup"><span data-stu-id="5ba26-137">See Also</span></span>  
 <span data-ttu-id="5ba26-138">[メジャーグループのプロパティの構成](configure-measure-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5ba26-138">[Configure Measure Group Properties](configure-measure-group-properties.md) </span></span>  
 [<span data-ttu-id="5ba26-139">メジャーの変更</span><span class="sxs-lookup"><span data-stu-id="5ba26-139">Modifying Measures</span></span>](../lesson-3-1-modifying-measures.md)  
  
  
