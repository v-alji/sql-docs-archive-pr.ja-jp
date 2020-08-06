---
title: メジャーとメジャーグループ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- measure groups [Analysis Services]
- measures [Analysis Services], about measures
- OLAP objects [Analysis Services], measures
- aggregate functions [Analysis Services]
- granularity
- measure groups [Analysis Services], about measure groups
- measures [Analysis Services]
- aggregations [Analysis Services], measures
- fact tables [Analysis Services]
ms.assetid: 4f0122f9-c3a5-4172-ada3-5bc5f7b1cc9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: daac03573880328ffe2648343d5af45eb7b07801
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715785"
---
# <a name="measures-and-measure-groups"></a><span data-ttu-id="aabdd-102">メジャーおよびメジャー グループ</span><span class="sxs-lookup"><span data-stu-id="aabdd-102">Measures and Measure Groups</span></span>
  <span data-ttu-id="aabdd-103">キューブには、 *メジャー グループ* 内の *メジャー*、ビジネス ロジック、およびディメンションのコレクション (メジャーが提供する数値のデータを評価するためのコンテキストを指定する) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-103">A cube includes *measures* in *measure groups*, business logic, plus a collection of dimensions that give context for evaluating the numerical data that a measure provides.</span></span> <span data-ttu-id="aabdd-104">メジャーおよびメジャー グループはどちらも、キューブに不可欠なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="aabdd-104">Both measures and measure groups are an essential component of a cube.</span></span> <span data-ttu-id="aabdd-105">キューブは、それぞれが少なくとも 1 つないと存在できません。</span><span class="sxs-lookup"><span data-stu-id="aabdd-105">A cube cannot exist without at least one of each.</span></span>  
  
 <span data-ttu-id="aabdd-106">このトピックでは、 [メジャー](#bkmk_measure) と [メジャー グループ](#bkmk_mg)について説明します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-106">This topic describes [Measures](#bkmk_measure) and [Measure Groups](#bkmk_mg).</span></span> <span data-ttu-id="aabdd-107">また、メジャーおよびメジャー グループの作成と構成の手順にリンクされている次の表も含まれています。</span><span class="sxs-lookup"><span data-stu-id="aabdd-107">It also contains the following table, with links to procedural steps for creating and configuring measures and measure groups.</span></span>  
  
|<span data-ttu-id="aabdd-108">**リンク**</span><span class="sxs-lookup"><span data-stu-id="aabdd-108">**Link**</span></span>|<span data-ttu-id="aabdd-109">**説明**</span><span class="sxs-lookup"><span data-stu-id="aabdd-109">**Description**</span></span>|  
|--------------|---------------------|  
|[<span data-ttu-id="aabdd-110">多次元モデル内のメジャーおよびメジャー グループの作成</span><span class="sxs-lookup"><span data-stu-id="aabdd-110">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|<span data-ttu-id="aabdd-111">メジャーとメジャー グループを作成するためのいくつかのアプローチのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-111">Choose from one of several approaches for creating measures and measure groups.</span></span>|  
|[<span data-ttu-id="aabdd-112">メジャーのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="aabdd-112">Configure Measure Properties</span></span>](configure-measure-properties.md)|<span data-ttu-id="aabdd-113">キューブを開始するためにキューブ ウィザードを使用した場合、集計方法を変更し、データ形式を適用し、クライアント アプリケーションでのメジャーの表示/非表示を設定し、場合によっては値の集計前にデータを操作するためのメジャー式を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aabdd-113">If you used the Cube Wizard to start your cube, you might need to change the aggregation method, apply a data format, set the visibility of the measure in client applications, or possibly add a measure expression to manipulate the data before values are aggregated.</span></span>|  
|[<span data-ttu-id="aabdd-114">メジャー グループのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="aabdd-114">Configure Measure Group Properties</span></span>](configure-measure-group-properties.md)|<span data-ttu-id="aabdd-115">多次元モデルでは、メジャー グループはソースのデータ ウェアハウス内のファクト テーブルに相当します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-115">In a multidimensional model, a measure group equates to a fact table in the source data warehouse.</span></span> <span data-ttu-id="aabdd-116">メジャー グループでのプロパティにより、キャッシュの動作、記憶域、メジャー グループ レベルでまとめて動作する処理ディレクティブを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-116">Properties on a measure group allow you to specify caching behaviors, storage, and processing directives that operate collectively at the measure group level.</span></span> <span data-ttu-id="aabdd-117">パーティション構成の一部は、メジャー グループ オブジェクトに設定するプロパティによって決まります。</span><span class="sxs-lookup"><span data-stu-id="aabdd-117">Partition configuration is partly determined by the properties you set on measure group objects.</span></span>|  
|[<span data-ttu-id="aabdd-118">集計関数の使用</span><span class="sxs-lookup"><span data-stu-id="aabdd-118">Use Aggregate Functions</span></span>](use-aggregate-functions.md)|<span data-ttu-id="aabdd-119">メジャーに割り当てることのできる集計メソッドを理解してください。</span><span class="sxs-lookup"><span data-stu-id="aabdd-119">Understand the aggregation methods that can be assigned to a measure.</span></span>|  
|[<span data-ttu-id="aabdd-120">準加法の動作の定義</span><span class="sxs-lookup"><span data-stu-id="aabdd-120">Define Semiadditive Behavior</span></span>](define-semiadditive-behavior.md)|<span data-ttu-id="aabdd-121">準加法の動作は、一部のディメンションだけに有効な集計を表します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-121">Semiadditive behavior refers to aggregations that are valid for some dimensions but not others.</span></span> <span data-ttu-id="aabdd-122">一般的な例としては、銀行口座の残高があります。</span><span class="sxs-lookup"><span data-stu-id="aabdd-122">A common example is a bank account balance.</span></span> <span data-ttu-id="aabdd-123">時間は除外し、顧客と地域によって残高を集計したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="aabdd-123">You might want to aggregate balances by customer and region, but not time.</span></span> <span data-ttu-id="aabdd-124">たとえば、連続した日々にわたって、同じ口座から残高を加算することはしません。</span><span class="sxs-lookup"><span data-stu-id="aabdd-124">For example, you would not want to add balances from the same account over consecutive days.</span></span> <span data-ttu-id="aabdd-125">準加法の動作を定義するには、ビジネス インテリジェンスの追加ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-125">To define semiadditive behavior,   use the Add Business Intelligence Wizard.</span></span>|  
|[<span data-ttu-id="aabdd-126">リンクメジャーグループ</span><span class="sxs-lookup"><span data-stu-id="aabdd-126">Linked Measure Groups</span></span>](linked-measure-groups.md)|<span data-ttu-id="aabdd-127">同じデータベース内、または別の Analysis Services データベース内の他のキューブで、既存のメジャー グループの用途を変更します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-127">Repurpose an existing measure group in other cubes in the same database or in different Analysis Services databases.</span></span>|  
  
##  <a name="measures"></a><a name="bkmk_measure"></a><span data-ttu-id="aabdd-128">直径</span><span class="sxs-lookup"><span data-stu-id="aabdd-128">Measures</span></span>  
 <span data-ttu-id="aabdd-129">メジャーは、集計できる定量化可能なデータ (通常は数値データ) を含んでいる列を表します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-129">A measure represents a column that contains quantifiable data, usually numeric, that can be aggregated.</span></span> <span data-ttu-id="aabdd-130">メジャーは組織のアクティビティの何らかの側面を表すもので、通貨の用語 (売上、利益率、コストなど) で表現されるか、カウント (在庫レベル、従業員、顧客、または注文の数) として表現されるか、またはビジネス ロジックを組み込んだ、より複雑な計算として表現されます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-130">Measures represent some aspect of organizational activity, expressed in monetary terms (such as revenue, margins, or costs) or as counts (inventory levels, number of employees, customers, or orders), or as a more complex calculation that incorporates business logic.</span></span>  
  
 <span data-ttu-id="aabdd-131">すべてのキューブが少なくとも 1 つのメジャーを持っている必要があるものの、多くの場合、メジャーの数は数百に達します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-131">Every cube must have at least one measure, but most have many, sometimes numbering in the hundreds.</span></span> <span data-ttu-id="aabdd-132">構造的には、メジャーは多くの場合、メジャーの読み込みに使用される値を提供する列と共に、ファクト テーブル内のソース列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-132">Structurally, a measure is often mapped to a source column in a fact table, with the column providing the values used to load the measure.</span></span> <span data-ttu-id="aabdd-133">代わりに、MDX を使用してメジャーを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-133">Alternatively, you can also define a measure using MDX.</span></span>  
  
 <span data-ttu-id="aabdd-134">メジャーはコンテキスト依存であり、いずれかのディメンション メンバーがクエリに含まれることによって決定されるコンテキストで、数値データに対して動作します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-134">Measures are context-sensitive, operating on numeric data in a context that is determined by whichever dimension members happen to be included in the query.</span></span> <span data-ttu-id="aabdd-135">たとえば、**再販業者の売上**を計算するメジャーは演算子によって支えられ、 `Sum` クエリに含まれる各ディメンションメンバーの売上金額が加算されます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-135">For example, a measure that calculates **Reseller Sales** will be backed by a `Sum` operator, and it will add the sales amounts for each dimension member included in the query.</span></span> <span data-ttu-id="aabdd-136">クエリで個々の製品を指定するかどうか、カテゴリにロールアップするかどうか、また時間や場所によってスライスされるかに応じて、メジャーはクエリに含まれるディメンションに対して有効な操作を生成します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-136">Whether the query specifies individual products, rolls up to a category, or is sliced by time or geography, the measure should produce an operation that is valid for the dimensions included in the query.</span></span>  
  
 <span data-ttu-id="aabdd-137">この例では、 **Sales Territory** 階層に沿ったさまざまなレベルに **再販業者の売上** を集計します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-137">In this example **Reseller Sales** aggregates to various levels along the **Sales Territory** hierarchy.</span></span>  
  
 <span data-ttu-id="aabdd-138">![メジャーとディメンションが呼び出されたピボットテーブル](../media/ssas-keyconcepts-pivot1-measures-dimensions.png "メジャーとディメンションが呼び出されたピボットテーブル")</span><span class="sxs-lookup"><span data-stu-id="aabdd-138">![PivotTable with measures and dimensions called out](../media/ssas-keyconcepts-pivot1-measures-dimensions.png "PivotTable with measures and dimensions called out")</span></span>  
  
 <span data-ttu-id="aabdd-139">メジャーは、数値のソース データを含むファクト テーブルに、クエリで使用されているディメンション テーブルへのポインターも含まれているときに、有効な結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="aabdd-139">Measures produce valid results when the fact table that contains the numeric source data also contains pointers to dimension tables that are used in the query.</span></span> <span data-ttu-id="aabdd-140">Reseller Sales の例で説明すると、売り上げ高を格納する行ごとに製品テーブル、日付テーブル、または販売区域のテーブルへのポインターも格納されている場合には、それらのディメンションからのメンバーが含まれるクエリが正しく解決されます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-140">Using the Reseller Sales example, if each row storing a sales amount also stores a pointer to a product table, a date table, or a sales territory table, then queries that include members from those dimension will resolve correctly.</span></span>  
  
 <span data-ttu-id="aabdd-141">メジャーがクエリで使用されるディメンションに関連付けられていないと、どうなるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="aabdd-141">What happens if the measure is unrelated to the dimensions used in query?</span></span> <span data-ttu-id="aabdd-142">通常、Analysis Services は、既定のメジャーを表示し、値はすべてのメンバーで同じになります。</span><span class="sxs-lookup"><span data-stu-id="aabdd-142">Typically, Analysis Services will show the default measure, and the value will be the same for all members.</span></span> <span data-ttu-id="aabdd-143">この例では、オンライン カタログを使用して顧客によって行われる直販を測定する **Internet Sales**は、販売組織に関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="aabdd-143">In this example, **Internet Sales**, which measure direct sales placed by customers using the online catalog, has no relationship to the sales organization.</span></span>  
  
 <span data-ttu-id="aabdd-144">![繰り返すメジャーの値を表示するピボットテーブル](../media/ssas-unrelatedmeasure.PNG "繰り返すメジャーの値を表示するピボットテーブル")</span><span class="sxs-lookup"><span data-stu-id="aabdd-144">![Pivottable showing repeated measure values](../media/ssas-unrelatedmeasure.PNG "Pivottable showing repeated measure values")</span></span>  
  
 <span data-ttu-id="aabdd-145">クライアント アプリケーションでこれらの動作が発生する可能性を最小限に抑えるには、複数のキューブまたはパースペクティブを同じデータベース内で構築し、各キューブまたはパースペクティブに、関連するオブジェクトのみが含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="aabdd-145">To minimize the chances of encountering these behaviors in a client application, you could build multiple cubes or perspectives within the same database, and ensure that each cube or perspective contains only related objects.</span></span> <span data-ttu-id="aabdd-146">確認する必要がある関係は、(ファクト テーブルにマップする) メジャー グループと、ディメンションの間の関係です。</span><span class="sxs-lookup"><span data-stu-id="aabdd-146">The relationships you need to check are between the measure group (mapped to the fact table) and the dimensions.</span></span>  
  
##  <a name="measure-groups"></a><a name="bkmk_mg"></a><span data-ttu-id="aabdd-147">メジャーグループ</span><span class="sxs-lookup"><span data-stu-id="aabdd-147">Measure Groups</span></span>  
 <span data-ttu-id="aabdd-148">キューブでは、メジャーは基になるファクト テーブルによってメジャー グループにグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-148">In a cube, measures are grouped by their underlying fact tables into measure groups.</span></span> <span data-ttu-id="aabdd-149">メジャー グループは、ディメンションをメジャーに関連付けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-149">Measure groups are used to associate dimensions with measures.</span></span> <span data-ttu-id="aabdd-150">メジャー グループは、集計動作として個別のカウントを持っているメジャーにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-150">Measure groups are also used for measures that have distinct count as their aggregation behavior.</span></span> <span data-ttu-id="aabdd-151">各個別のカウント メジャーをそれぞれ独自のメジャー グループに配置すると、集計処理が最適化されます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-151">Placing each distinct count measure into its own measure group optimizes aggregation processing.</span></span>  
  
 <span data-ttu-id="aabdd-152">単純な <xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトは、グループ名、ストレージ モード、および処理モードなどの基本情報で構成されます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-152">A simple <xref:Microsoft.AnalysisServices.MeasureGroup> object is composed of basic information like the group name, storage mode, and processing mode.</span></span> <span data-ttu-id="aabdd-153">その構成要素として、メジャー、ディメンション、およびメジャー グループの構成を形成するパーティションも、それに含まれます。</span><span class="sxs-lookup"><span data-stu-id="aabdd-153">It also contains its constituent parts; the measures, dimensions, and partitions that form the composition of the measure group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aabdd-154">参照</span><span class="sxs-lookup"><span data-stu-id="aabdd-154">See Also</span></span>  
 <span data-ttu-id="aabdd-155">[多次元モデルのキューブ](cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="aabdd-155">[Cubes in Multidimensional Models](cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="aabdd-156">多次元モデル内のメジャーおよびメジャー グループの作成</span><span class="sxs-lookup"><span data-stu-id="aabdd-156">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)  
  
  