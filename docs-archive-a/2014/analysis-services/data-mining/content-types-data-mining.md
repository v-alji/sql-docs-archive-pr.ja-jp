---
title: コンテンツの種類 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], content types
- KEY SEQUENCE column
- content types [data mining]
- attributes [data mining]
- DISCRETIZED column
- CONTINUOUS column
- CYCLICAL column
- ORDERED column
- discretized columns [data mining]
- discrete columns [Analysis Services]
- DISCRETE column
- KEY column
- KEY TIME column
- continuous columns
- coding [Data Mining]
ms.assetid: 2dacd968-70e8-4993-88b6-a6d36024a4e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e3400d904bc857bc282bb1ad9220c1e01fe5a4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711165"
---
# <a name="content-types-data-mining"></a><span data-ttu-id="5fbdc-102">コンテンツの種類 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-102">Content Types (Data Mining)</span></span>
  <span data-ttu-id="5fbdc-103">では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] マイニング構造の列に対して物理データ型を定義できます。また、モデルで使用する場合は、列の論理コンテンツ型を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can define the both the physical data type for a column in a mining structure, and a logical content type for the column when used in a model,</span></span>  
  
 <span data-ttu-id="5fbdc-104">*データ型* により、マイニング モデルを作成するときにその列に含まれるデータをアルゴリズムでどのように処理するかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-104">The *data type* determines how algorithms process the data in those columns when you create mining models.</span></span> <span data-ttu-id="5fbdc-105">列のデータ型を定義することで、列に含まれるデータの型に関する情報と、データの処理方法がアルゴリズムに通知されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-105">Defining the data type of a column gives the algorithm information about the type of data in the columns, and how to process the data.</span></span> <span data-ttu-id="5fbdc-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の各データ型では、データ マイニング向けに 1 つまたは複数のコンテンツの種類がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-106">Each data type in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports one or more content types for data mining.</span></span>  
  
 <span data-ttu-id="5fbdc-107">*コンテンツの種類* は、列に含まれるコンテンツの動作を表します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-107">The *content type* describes the behavior of the content that the column contains.</span></span> <span data-ttu-id="5fbdc-108">たとえば、列のコンテンツが特定の間隔 (特定の曜日など) で繰り返される場合は、この列のコンテンツの種類を CYCLICAL として指定できます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-108">For example, if the content in a column repeats in a specific interval, such as days of the week, you can specify the content type of that column as cyclical.</span></span>  
  
 <span data-ttu-id="5fbdc-109">いくつかのアルゴリズムは、正しく機能するために特定のデータ型と特定のコンテンツの種類が必要です。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-109">Some algorithms require specific data types and specific content types to be able to function correctly.</span></span> <span data-ttu-id="5fbdc-110">たとえば、Microsoft Naive Bayes アルゴリズムでは、連続列を入力として使用したり、連続する値を予測したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-110">For example, the Microsoft Naive Bayes algorithm cannot use continuous columns as input, and cannot predict continuous values.</span></span> <span data-ttu-id="5fbdc-111">Key Sequence など、一部のコンテンツの種類は、特定のアルゴリズムでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-111">Some content types, such as Key Sequence, are used only by a specific algorithm.</span></span> <span data-ttu-id="5fbdc-112">アルゴリズムの一覧と、各アルゴリズムがサポートするコンテンツの種類については、「[データ マイニング アルゴリズム (Analysis Services - データ マイニング)](data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-112">For a list of the algorithms and the content types that each supports, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="5fbdc-113">次の一覧は、データ マイニングで使用されるコンテンツの種類について説明し、各種類をサポートするデータ型を示しています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-113">The following list describes the content types that are used in data mining, and identifies the data types that support each type.</span></span>  
  
## <a name="discrete"></a><span data-ttu-id="5fbdc-114">離散</span><span class="sxs-lookup"><span data-stu-id="5fbdc-114">Discrete</span></span>  
 <span data-ttu-id="5fbdc-115">*Discrete* は、有限の不連続な値が列に格納されることを示します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-115">*Discrete* means that the column contains a finite number of values with no continuum between values.</span></span> <span data-ttu-id="5fbdc-116">たとえば、Gender 列は、データが特定の数のカテゴリを表すという点で、典型的な不連続の属性列です。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-116">For example, a gender column is a typical discrete attribute column, in that the data represents a specific number of categories.</span></span>  
  
 <span data-ttu-id="5fbdc-117">不連続の属性列の値には、値が数値であっても順序の意味は含まれません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-117">The values in a discrete attribute column cannot imply ordering, even if the values are numeric.</span></span> <span data-ttu-id="5fbdc-118">さらに、不連続列に対して使用された値は、数値であっても小数部を計算することはできません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-118">Moreover, even if the values used for the discrete column are numeric, fractional values cannot be calculated.</span></span> <span data-ttu-id="5fbdc-119">市外局番コードは、不連続の数値データの好例です。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-119">Telephone area codes are a good example of discrete data that is numeric.</span></span>  
  
 <span data-ttu-id="5fbdc-120">コンテンツの種類 `Discrete` は、すべてのデータ マイニング データ型によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-120">The `Discrete` content type is supported by all data mining data types.</span></span>  
  
## <a name="continuous"></a><span data-ttu-id="5fbdc-121">継続的</span><span class="sxs-lookup"><span data-stu-id="5fbdc-121">Continuous</span></span>  
 <span data-ttu-id="5fbdc-122">*Continuous* は、この列に中間値が許可されるスケールの数値データを表す値が格納されることを表します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-122">*Continuous* means that the column contains values that represent numeric data on a scale that allows interim values.</span></span> <span data-ttu-id="5fbdc-123">有限の数えられるデータを表す不連続列とは異なり、連続列は無限の小数部が含まれる可能性のある計測可能な測定値を表します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-123">Unlike a discrete column, which represents finite, countable data, a continuous column represents scalable measurements, and it is possible for the data to contain an infinite number of fractional values.</span></span> <span data-ttu-id="5fbdc-124">連続した属性列の例としては気温の列があります。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-124">A column of temperatures is an example of a continuous attribute column.</span></span>  
  
 <span data-ttu-id="5fbdc-125">連続する数値データが列に含まれ、そのデータがどのように分布するかがわかっている場合は、期待される値の分布を指定することで、分析の精度を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-125">When a column contains continuous numeric data, and you know how the data should be distributed, you can potentially improve the accuracy of the analysis by specifying the expected distribution of values.</span></span> <span data-ttu-id="5fbdc-126">列の分布は、マイニング構造レベルで指定します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-126">You specify the column distribution at the level of the mining structure.</span></span> <span data-ttu-id="5fbdc-127">このため、設定はその構造に基づくすべてのモデルに適用されます。詳細については、「[列の分布 (データ マイニング)](column-distributions-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-127">Therefore, the setting applies to all models that are based on the structure, For more information, see [Column Distributions &#40;Data Mining&#41;](column-distributions-data-mining.md).</span></span>  
  
 <span data-ttu-id="5fbdc-128">コンテンツの種類 `Continuous` は、`Date`、`Double`、および `Long` の各データ型によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-128">The `Continuous` content type is supported by the following data types: `Date`, `Double`, and `Long`.</span></span>  
  
## <a name="discretized"></a><span data-ttu-id="5fbdc-129">Discretized</span><span class="sxs-lookup"><span data-stu-id="5fbdc-129">Discretized</span></span>  
 <span data-ttu-id="5fbdc-130">*分離* とは、連続した一連のデータの値をバケットに分割して、限定された数の可能な値を生成するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-130">*Discretization* is the process of putting values of a continuous set of data into buckets so that there are a limited number of possible values.</span></span> <span data-ttu-id="5fbdc-131">数値データだけを分離できます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-131">You can discretize only numeric data.</span></span>  
  
 <span data-ttu-id="5fbdc-132">つまり、コンテンツの種類が *discretized* であれば、連続列から派生した値のグループ (またはバケット) を表す値が列に含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-132">Thus, the *discretized* content type indicates that the column contains values that represent groups, or buckets, of values that are derived from a continuous column.</span></span> <span data-ttu-id="5fbdc-133">バケットは、順序付きの不連続の値として処理されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-133">The buckets are treated as ordered and discrete values.</span></span>  
  
 <span data-ttu-id="5fbdc-134">必要なバケットが得られるようにデータを手動で分離することも、SQL Server Analysis Services に用意されている分離メソッドを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-134">You can discretize your data manually, to ensure that you get the buckets you want, or you can use the discretization methods provided in SQL Server Analysis Services.</span></span> <span data-ttu-id="5fbdc-135">一部のアルゴリズムでは分離が自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-135">Some algorithms perform discretization automatically.</span></span> <span data-ttu-id="5fbdc-136">詳細については、「 [マイニング モデルでの列の分離の変更](change-the-discretization-of-a-column-in-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-136">For more information, see [Change the Discretization of a Column in a Mining Model](change-the-discretization-of-a-column-in-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="5fbdc-137">コンテンツの種類 `Discretized` は、`Date`、`Double`、`Long`、および `Text` の各データ型によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-137">The `Discretized` content type is supported by the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
## <a name="key"></a><span data-ttu-id="5fbdc-138">Key</span><span class="sxs-lookup"><span data-stu-id="5fbdc-138">Key</span></span>  
 <span data-ttu-id="5fbdc-139">コンテンツの種類 *key* は、この列が行を一意に識別することを表します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-139">The *key* content type means that the column uniquely identifies a row.</span></span> <span data-ttu-id="5fbdc-140">ケース テーブルの場合、通常、キー列は数値またはテキストの識別子です。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-140">In a case table, typically the key column is a numeric or text identifier.</span></span> <span data-ttu-id="5fbdc-141">コンテンツの種類を `key` に設定すると、分析には使用しない、レコードの追跡専用の列であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-141">You set the content type to `key` to indicate that the column should not be used for analysis, only for tracking records.</span></span>  
  
 <span data-ttu-id="5fbdc-142">入れ子になったテーブルにもキーはありますが、入れ子になったテーブルのキーは使い方が多少異なります。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-142">Nested tables also have keys, but the usage of the nested table key is a little different.</span></span> <span data-ttu-id="5fbdc-143">入れ子になったテーブルでコンテンツの種類を `key` に設定するのは、その列が分析する属性である場合です。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-143">You set the content type to `key` in a nested table if the column is the attribute that you want to analyze.</span></span> <span data-ttu-id="5fbdc-144">入れ子になったテーブルのキーの値は各ケースで一意である必要がありますが、ケースのセット全体では重複していてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-144">The values in the nested table key must be unique for each case but there can be duplicates across the entire set of cases.</span></span>  
  
 <span data-ttu-id="5fbdc-145">たとえば、顧客が購入する製品を分析する場合は、ケース テーブルの **CustomerID** 列のコンテンツの種類を key に設定し、入れ子になったテーブルの **PurchasedProducts** 列のコンテンツの種類も key に設定します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-145">For example, if you are analyzing the products that customers purchase, you would set content type to key for the **CustomerID** column in the case table, and set content type to key again for the **PurchasedProducts** column in the nested table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fbdc-146">入れ子になったテーブルを使用できるのは、Analysis Services のデータ ソース ビューとして定義されている外部データ ソースのデータを使用する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-146">Nested tables are available only if you use data from an external data source that has been defined as an Analysis services data source view.</span></span>  
  
 <span data-ttu-id="5fbdc-147">このコンテンツの種類は、`Date`、`Double`、`Long`、および `Text` の各データ型によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-147">This content type is supported by the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
## <a name="key-sequence"></a><span data-ttu-id="5fbdc-148">Key Sequence</span><span class="sxs-lookup"><span data-stu-id="5fbdc-148">Key Sequence</span></span>  
 <span data-ttu-id="5fbdc-149">コンテンツの種類 *key sequence* は、シーケンス クラスター モデルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-149">The *key sequence* content type can only be used in sequence clustering models.</span></span> <span data-ttu-id="5fbdc-150">コンテンツの種類を `key sequence` に設定すると、一連のイベントを表す値を格納する列であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-150">When you set content type to `key sequence`, it indicates that the column contains values that represent a sequence of events.</span></span> <span data-ttu-id="5fbdc-151">値は順序付けされていますが、互いに等間隔である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-151">The values are ordered, but do not have to be an equal distance apart.</span></span>  
  
 <span data-ttu-id="5fbdc-152">このコンテンツの種類は、`Double`、`Long`、`Text`、および `Date` の各データ型によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-152">This content type is supported by the following data types: `Double`, `Long`, `Text`, and `Date`.</span></span>  
  
## <a name="key-time"></a><span data-ttu-id="5fbdc-153">[キー時刻]</span><span class="sxs-lookup"><span data-stu-id="5fbdc-153">Key Time</span></span>  
 <span data-ttu-id="5fbdc-154">コンテンツの種類 *key time* は、時系列モデルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-154">The *key time* content type can only be used in time series models.</span></span> <span data-ttu-id="5fbdc-155">コンテンツの種類を `key time` に設定すると、値が順序付きであり時系列を表す値であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-155">When you set content type to `key time`, it indicates that the values are ordered and represent a time scale.</span></span>  
  
 <span data-ttu-id="5fbdc-156">このコンテンツの種類は、`Double`、`Long`、および `Date` の各データ型によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-156">This content type is supported by the following data types: `Double`, `Long`, and `Date`.</span></span>  
  
## <a name="table"></a><span data-ttu-id="5fbdc-157">テーブル</span><span class="sxs-lookup"><span data-stu-id="5fbdc-157">Table</span></span>  
 <span data-ttu-id="5fbdc-158">コンテンツの種類 *table* は、1 つ以上の列と 1 つ以上の行を持つ別のデータ テーブルが列に含まれることを示します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-158">The *table* content type indicates that the column contains another data table, with one or more columns and one or more rows.</span></span> <span data-ttu-id="5fbdc-159">ケース テーブルの特定の行では、この列に、すべて親ケース レコードに関係する複数の値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-159">For any particular row in the case table, this column can contain multiple values, all related to the parent case record.</span></span> <span data-ttu-id="5fbdc-160">たとえば、メインのケース テーブルに顧客の一覧が含まれている場合に、その顧客が過去に購入した製品の一覧から成る入れ子になったテーブルを含む **ProductsPurchased** 列や、顧客の関心の一覧から成る **Hobbies** 列など、入れ子になったテーブルを含む複数の列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-160">For example, if the main case table contains a listing of customers, you could have several columns that contain nested tables, such as a **ProductsPurchased** column, where the nested table lists products bought by this customer in the past, and a **Hobbies** column that lists the interests of the customer.</span></span>  
  
 <span data-ttu-id="5fbdc-161">この列のデータ型は常に `Table` です。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-161">The data type of this column is always `Table`.</span></span>  
  
## <a name="cyclical"></a><span data-ttu-id="5fbdc-162">Cyclical</span><span class="sxs-lookup"><span data-stu-id="5fbdc-162">Cyclical</span></span>  
 <span data-ttu-id="5fbdc-163">コンテンツの種類 *cyclical* は、循環的な順序付きセットを表す値が列に含まれることを示します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-163">The *cyclical* content type means that the column contains values that represent a cyclical ordered set.</span></span> <span data-ttu-id="5fbdc-164">たとえば、曜日 1 が曜日 7 の後に続くので、番号付きの曜日は循環的な順序付きセットです。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-164">For example, the numbered days of the week is a cyclical ordered set, because day number one follows day number seven.</span></span>  
  
 <span data-ttu-id="5fbdc-165">循環的な列は、コンテンツの種類としては順序付きかつ不連続と見なされます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-165">Cyclical columns are considered both ordered and discrete in terms of content type.</span></span>  
  
 <span data-ttu-id="5fbdc-166">このコンテンツの種類は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のすべてのデータ マイニング データ型によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-166">This content type is supported by all the data mining data types in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="5fbdc-167">ただし、多くのアルゴリズムは cyclical の値を不連続の値として扱い、特別な処理は行いません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-167">However, most algorithms treat cyclical values as discrete values and do not perform special processing.</span></span>  
  
## <a name="ordered"></a><span data-ttu-id="5fbdc-168">注文済み</span><span class="sxs-lookup"><span data-stu-id="5fbdc-168">Ordered</span></span>  
 <span data-ttu-id="5fbdc-169">コンテンツの種類 *Ordered* は、並びまたは順序を定義する値が列に含まれることを示します。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-169">The *Ordered* content type also indicates that the column contains values that define a sequence or order.</span></span> <span data-ttu-id="5fbdc-170">ただし、このコンテンツの種類で順序付けに使用される値は、他の値との距離や大きさの関係を表すわけではありません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-170">However, in this content type the values used for ordering do not imply any distance or magnitude relationship between values in the set.</span></span> <span data-ttu-id="5fbdc-171">たとえば、順序付き属性列に 1 ～ 5 というランクのスキル レベルに関する情報が含まれている場合、各スキル レベル間の距離に関する情報は示されません。つまり、5 というスキル レベルが 1 というスキル レベルより必ずしも 5 倍優れているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-171">For example, if an ordered attribute column contains information about skill levels in rank order from one to five, there is no implied information in the distance between skill levels; a skill level of five is not necessarily five times better than a skill level of one.</span></span>  
  
 <span data-ttu-id="5fbdc-172">順序付き属性列は、コンテンツの種類としては不連続と見なされます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-172">Ordered attribute columns are considered to be discrete in terms of content type.</span></span>  
  
 <span data-ttu-id="5fbdc-173">このコンテンツの種類は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のすべてのデータ マイニング データ型によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-173">This content type is supported by all the data mining data types in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="5fbdc-174">ただし、多くのアルゴリズムは ordered の値を不連続の値として扱い、特別な処理は行いません。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-174">However, however, most algorithms treat ordered values as discrete values and do not perform special processing.</span></span>  
  
## <a name="classified"></a><span data-ttu-id="5fbdc-175">分類済み</span><span class="sxs-lookup"><span data-stu-id="5fbdc-175">Classified</span></span>  
 <span data-ttu-id="5fbdc-176">すべてのモデルで共通して使用される上記のコンテンツの種類の他にも、分類済みの列を使用して、一部のデータ型に対してコンテンツの種類を定義できます。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-176">In addition to the preceding content types that are in common use with all models, for some data types you can use classified columns to define content types.</span></span> <span data-ttu-id="5fbdc-177">分類済みの列の詳細については、「[分類済みの列 (データ マイニング)](classified-columns-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-177">For more information about classified columns, see [Classified Columns &#40;Data Mining&#41;](classified-columns-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fbdc-178">参照</span><span class="sxs-lookup"><span data-stu-id="5fbdc-178">See Also</span></span>  
 <span data-ttu-id="5fbdc-179">[DMX&#41;&#40;コンテンツの種類](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="5fbdc-179">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="5fbdc-180">[データマイニング&#41;&#40;データ型](data-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5fbdc-180">[Data Types &#40;Data Mining&#41;](data-types-data-mining.md) </span></span>  
 <span data-ttu-id="5fbdc-181">[DMX&#41;&#40;データ型](/sql/dmx/data-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="5fbdc-181">[Data Types &#40;DMX&#41;](/sql/dmx/data-types-dmx) </span></span>  
 <span data-ttu-id="5fbdc-182">[マイニング構造のプロパティの変更](change-the-properties-of-a-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="5fbdc-182">[Change the Properties of a Mining Structure](change-the-properties-of-a-mining-structure.md) </span></span>  
 [<span data-ttu-id="5fbdc-183">マイニング構造列</span><span class="sxs-lookup"><span data-stu-id="5fbdc-183">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
