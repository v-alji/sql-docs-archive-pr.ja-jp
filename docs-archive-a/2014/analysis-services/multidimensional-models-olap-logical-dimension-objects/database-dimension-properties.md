---
title: データベースディメンションのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 504e190f4c513a8c999c4d7d7ab9eaabb83298c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642993"
---
# <a name="database-dimension-properties"></a><span data-ttu-id="a0932-102">データベース ディメンション プロパティ</span><span class="sxs-lookup"><span data-stu-id="a0932-102">Database Dimension Properties</span></span>
  <span data-ttu-id="a0932-103">で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ディメンションの特性は、さまざまなディメンションプロパティの設定およびディメンションに含まれる属性または階層に基づいて、ディメンションのメタデータによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0932-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the characteristics of a dimension are defined by the metadata for the dimension, based on the settings of various dimension properties, and on the attributes or hierarchies that are contained by the dimension.</span></span> <span data-ttu-id="a0932-104">次の表では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンション プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0932-104">The following table describes the dimension properties in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="a0932-105">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a0932-105">Property</span></span>|<span data-ttu-id="a0932-106">説明</span><span class="sxs-lookup"><span data-stu-id="a0932-106">Description</span></span>|  
|--------------|-----------------|  
|`AttributeAllMemberName`|<span data-ttu-id="a0932-107">ディメンションの属性の All メンバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-107">Specifies the name of the All member for attributes in a dimension.</span></span>|  
|`Collation`|<span data-ttu-id="a0932-108">ディメンションで使用する照合順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-108">Determines the collation used by the dimension.</span></span>|  
|`CurrentStorageMode`|<span data-ttu-id="a0932-109">ディメンションの現在のストレージ モードを格納します。</span><span class="sxs-lookup"><span data-stu-id="a0932-109">Contains the current storage mode for the dimension.</span></span>|  
|`DependsOnDimension`|<span data-ttu-id="a0932-110">ディメンションが別のディメンションに依存している場合は、その ID を格納します。</span><span class="sxs-lookup"><span data-stu-id="a0932-110">Contains the ID of another dimension on which the dimension depends, if any.</span></span>|  
|`Description`|<span data-ttu-id="a0932-111">ディメンションの説明を格納します。</span><span class="sxs-lookup"><span data-stu-id="a0932-111">Contains the description of the dimension.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="a0932-112">重複するキー、不明なキー、エラーの制限、エラー検出時のアクション、エラー ログ ファイル、および NULL キーを処理するための、構成可能なエラー処理設定です。</span><span class="sxs-lookup"><span data-stu-id="a0932-112">Configurable error handling settings for handling of duplicate keys, unknown keys, error limits, action upon error detection, error log file, and null key handling.</span></span>|  
|`ID`|<span data-ttu-id="a0932-113">ディメンションの一意識別子 (ID) を示します。</span><span class="sxs-lookup"><span data-stu-id="a0932-113">Contains the unique identifier (ID) of the dimension.</span></span>|  
|`Language`|<span data-ttu-id="a0932-114">ディメンションの既定の言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-114">Specifies the default language for the dimension.</span></span>|  
|`MdxMissingMemberMode`|<span data-ttu-id="a0932-115">欠落しているメンバーを多次元式 (MDX) ステートメントでどのように処理するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-115">Determines how missing members are handled for Multidimensional Expressions (MDX) statements.</span></span>|  
|`MiningModelID`|<span data-ttu-id="a0932-116">データ マイニング ディメンションが関連付けられているマイニング モデルの ID を保持します。</span><span class="sxs-lookup"><span data-stu-id="a0932-116">Contains the ID of the mining model with which the data mining dimension is associated.</span></span> <span data-ttu-id="a0932-117">このプロパティは、ディメンションがマイニング モデル ディメンションの場合にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="a0932-117">This property is applicable only if the dimension is a mining model dimension.</span></span>|  
|`Name`|<span data-ttu-id="a0932-118">ディメンションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-118">Specifies the name of the dimension.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="a0932-119">ディメンションのプロアクティブ キャッシュの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a0932-119">Defines the proactive cache settings for the dimension.</span></span>|  
|`ProcessingGroup`|<span data-ttu-id="a0932-120">処理グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-120">Specifies the processing group.</span></span> <span data-ttu-id="a0932-121">有効値は ByAttribute または ByTable です。</span><span class="sxs-lookup"><span data-stu-id="a0932-121">Values are ByAttribute or ByTable.</span></span> <span data-ttu-id="a0932-122">既定値は `ByAttribute`です。</span><span class="sxs-lookup"><span data-stu-id="a0932-122">Default is `ByAttribute`.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="a0932-123">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によるインデックス化および集計を処理中または処理後のどちらに行うかを示します。</span><span class="sxs-lookup"><span data-stu-id="a0932-123">Indicates whether [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should index and aggregate during or after processing.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="a0932-124">レイジー集計、インデックス作成、クラスター化など、バックグラウンド操作中のディメンション処理の優先度を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-124">Determines the processing priority of the dimension during background operations such as lazy aggregation, indexing, or clustering.</span></span>|  
|`Source`|<span data-ttu-id="a0932-125">ディメンションのバインド先のデータ ソース ビューを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-125">Identifies the data source view to which the dimension is bound.</span></span>|  
|`StorageMode`|<span data-ttu-id="a0932-126">ディメンションのストレージ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-126">Determines the storage mode for the dimension.</span></span>|  
|`Type`|<span data-ttu-id="a0932-127">ディメンションの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-127">Specifies the type of the dimension.</span></span>|  
|`UnknownMember`|<span data-ttu-id="a0932-128">不明なメンバーが表示されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a0932-128">Indicates whether the unknown member is visible.</span></span>|  
|`UnknownMemberName`|<span data-ttu-id="a0932-129">ディメンションの不明なメンバーのキャプションをディメンションの既定の言語で指定します。</span><span class="sxs-lookup"><span data-stu-id="a0932-129">Specifies the caption, in the default language of the dimension, for the unknown member of the dimension.</span></span>|  
|`WriteEnabled`|<span data-ttu-id="a0932-130">ディメンションの書き戻しを使用できるかどうかを示します (セキュリティ権限に依存)。</span><span class="sxs-lookup"><span data-stu-id="a0932-130">Indicates whether dimension writebacks are available (subject to security permissions).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a0932-131">Null 値やその他のデータの整合性の問題を処理するときの ErrorConfiguration プロパティと UnknownMember プロパティの値の設定の詳細については、「 [Analysis Services 2005 でのデータ整合性の問題の処理](https://go.microsoft.com/fwlink/?LinkId=81891)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0932-131">For more information about setting values for the ErrorConfiguration and UnknownMember properties when working with null values and other data integrity issues, see [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0932-132">参照</span><span class="sxs-lookup"><span data-stu-id="a0932-132">See Also</span></span>  
 <span data-ttu-id="a0932-133">[属性と属性階層](attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="a0932-133">[Attributes and Attribute Hierarchies](attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="a0932-134">[ユーザー階層](user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="a0932-134">[User Hierarchies](user-hierarchies.md) </span></span>  
 <span data-ttu-id="a0932-135">[ディメンションのリレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="a0932-135">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 [<span data-ttu-id="a0932-136">ディメンション &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="a0932-136">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  
