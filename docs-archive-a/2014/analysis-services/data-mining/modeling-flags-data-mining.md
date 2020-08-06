---
title: モデリングフラグ (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- data types [data mining]
- REGRESSOR flag
- MODEL_EXISTENCE_ONLY flag
- REGRESSOR column
- columns [data mining], modeling flags
- NOT NULL modeling flag
- modeling flags [data mining]
- null values [Analysis Services]
- MODEL_EXISTENCE_ONLY column
- coding [Data Mining]
ms.assetid: 8826d5ce-9ba8-4490-981b-39690ace40a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f1c802f6503b84ff4f6879c18d3bffebb46d7ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712649"
---
# <a name="modeling-flags-data-mining"></a><span data-ttu-id="63fed-102">モデリング フラグ (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="63fed-102">Modeling Flags (Data Mining)</span></span>
  <span data-ttu-id="63fed-103">のモデリングフラグを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ケーステーブルで定義されているデータに関する追加情報をデータマイニングアルゴリズムに提供できます。</span><span class="sxs-lookup"><span data-stu-id="63fed-103">You can use modeling flags in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide additional information to a data mining algorithm about the data that is defined in a case table.</span></span> <span data-ttu-id="63fed-104">アルゴリズムは、この情報を使用して、より正確なデータ マイニング モデルを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="63fed-104">The algorithm can use this information to build a more accurate data mining model.</span></span>  
  
 <span data-ttu-id="63fed-105">マイニング構造のレベルで定義されるモデリング フラグもあれば、マイニング モデル列のレベルで定義されるモデリング フラグもあります。</span><span class="sxs-lookup"><span data-stu-id="63fed-105">Some modeling flags are defined at the level of the mining structure, whereas others are defined at the level of the mining model column.</span></span> <span data-ttu-id="63fed-106">たとえば、`NOT NULL` モデリング フラグはマイニング構造列で使用されます。</span><span class="sxs-lookup"><span data-stu-id="63fed-106">For example, the `NOT NULL` modeling flag is used with mining structure columns.</span></span> <span data-ttu-id="63fed-107">モデルの作成に使用するアルゴリズムに応じて、追加的なモデリング フラグをマイニング モデル列に定義することができます。</span><span class="sxs-lookup"><span data-stu-id="63fed-107">You can define additional modeling flags on the mining model columns, depending on the algorithm you use to create the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63fed-108">サードパーティ プラグインには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]であらかじめ定義されているフラグに加えて他のモデリング フラグがある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="63fed-108">Third-party plug-ins might have other modeling flags, in addition to those pre-defined by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="list-of-modeling-flags"></a><span data-ttu-id="63fed-109">モデリング フラグの一覧</span><span class="sxs-lookup"><span data-stu-id="63fed-109">List of Modeling Flags</span></span>  
 <span data-ttu-id="63fed-110">次の一覧に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でサポートされているモデリング フラグを示します。</span><span class="sxs-lookup"><span data-stu-id="63fed-110">The following list describes the modeling flags that are supported in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="63fed-111">特定のアルゴリズムでサポートされているモデリング フラグについては、モデルの作成に使用したアルゴリズムのテクニカル リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="63fed-111">For information about modeling flags that are supported by specific algorithms, see the technical reference topic for the algorithm that was used to create the model.</span></span>  
  
 `NOT NULL`  
 <span data-ttu-id="63fed-112">この属性列の値が NULL 値を含むことはないことを示します。</span><span class="sxs-lookup"><span data-stu-id="63fed-112">Indicates that the values for the attribute column should never contain a null value.</span></span> <span data-ttu-id="63fed-113">モデルの学習プロセス中に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がこの属性列に NULL 値を検出した場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="63fed-113">An error will result if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a null value for this attribute column during the model training process.</span></span>  
  
 <span data-ttu-id="63fed-114">**MODEL_EXISTENCE_ONLY**</span><span class="sxs-lookup"><span data-stu-id="63fed-114">**MODEL_EXISTENCE_ONLY**</span></span>  
 <span data-ttu-id="63fed-115">列が、`Missing` および `Existing` の 2 つの状態を持つ列として扱われることを示します。</span><span class="sxs-lookup"><span data-stu-id="63fed-115">Indicates that the column will be treated as having two states: `Missing` and `Existing`.</span></span> <span data-ttu-id="63fed-116">値が `NULL` の場合は Missing として扱われます。</span><span class="sxs-lookup"><span data-stu-id="63fed-116">If the value is `NULL`, it is treated as Missing.</span></span> <span data-ttu-id="63fed-117">MODEL_EXISTENCE_ONLY フラグは、予測可能な属性に適用され、ほとんどのアルゴリズムでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="63fed-117">The MODEL_EXISTENCE_ONLY flag is applied to the predictable attribute and is supported by most algorithms.</span></span>  
  
 <span data-ttu-id="63fed-118">実際、MODEL_EXISTENCE_ONLY フラグを `True` に設定すると、`Missing` と `Existing` の 2 つの状態だけが存在するように値の形式が変わります。</span><span class="sxs-lookup"><span data-stu-id="63fed-118">In effect, setting the MODEL_EXISTENCE_ONLY flag to `True` changes the representation of the values such that there are only two states: `Missing` and `Existing`.</span></span> <span data-ttu-id="63fed-119">Missing に該当しない状態はすべて単一の `Existing` 値に統合されます。</span><span class="sxs-lookup"><span data-stu-id="63fed-119">All the non-missing states are combined into a single `Existing` value.</span></span>  
  
 <span data-ttu-id="63fed-120">このモデリング フラグは、`NULL` 状態が暗黙的な意味を持ち、`NOT NULL` 状態の明示的な値はその列に値があるという事実ほど重要ではないような属性に使用されるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="63fed-120">A typical use for this modeling flag would be in attributes for which the `NULL` state has an implicit meaning, and the explicit value of the `NOT NULL` state might not be as important as the fact that the column has any value.</span></span> <span data-ttu-id="63fed-121">たとえば [DateContractSigned] 列は、契約書が署名されなかった場合には `NULL` に、署名された場合には `NOT NULL` になります。</span><span class="sxs-lookup"><span data-stu-id="63fed-121">For example, a [DateContractSigned] column might be `NULL` if a contract was never signed and `NOT NULL` if the contract was signed.</span></span> <span data-ttu-id="63fed-122">したがって、契約書が署名されるかどうかの予測を目的とするモデルでは、MODEL_EXISTENCE_ONLY フラグを使用して、`NOT NULL` のケースの正確な日付の値は無視して、契約書が `Missing` のケースと `Existing` のケースの区別のみを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="63fed-122">Therefore, if the purpose of the model is to predict whether a contract will be signed, you can use the MODEL_EXISTENCE_ONLY flag to ignore the exact date value in the `NOT NULL` cases and distinguish only between cases where a contract is `Missing` or `Existing`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63fed-123">Missing はアルゴリズムによって使用される特殊な状態であり、列のテキスト値の "Missing" とは異なります。</span><span class="sxs-lookup"><span data-stu-id="63fed-123">Missing is a special state used by the algorithm, and differs from the text value "Missing" in a column.</span></span> <span data-ttu-id="63fed-124">詳細については、「 [不足値 &#40;Analysis Services - データ マイニング&#41;](missing-values-analysis-services-data-mining.md)であらかじめ定義されているフラグに加えて他のモデリング フラグがある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="63fed-124">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
 `REGRESSOR`  
 <span data-ttu-id="63fed-125">列が処理中にリグレッサーとして使用される候補であることを示します。</span><span class="sxs-lookup"><span data-stu-id="63fed-125">Indicates that the column is a candidate for used as a regressor during processing.</span></span> <span data-ttu-id="63fed-126">このフラグは、マイニング モデル列で定義され、連続する数値データ型の列にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="63fed-126">This flag is defined on a mining model column, and can only be applied to columns that have a continuous numeric data type.</span></span> <span data-ttu-id="63fed-127">このフラグの使用の詳細については、このトピックの「 [REGRESSOR モデリング フラグの使用](#bkmk_UseRegressors)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63fed-127">For more information about the use of this flag, see the section in this topic, [Uses of the REGRESSOR Modeling Flag](#bkmk_UseRegressors).</span></span>  
  
## <a name="viewing-and-changing-modeling-flags"></a><span data-ttu-id="63fed-128">モデリング フラグの表示と変更</span><span class="sxs-lookup"><span data-stu-id="63fed-128">Viewing and Changing Modeling Flags</span></span>  
 <span data-ttu-id="63fed-129">マイニング構造列やマイニング モデル列に関連付けられているモデリング フラグは、その構造またはモデルのプロパティをデータ マイニング デザイナーで表示することによって確認できます。</span><span class="sxs-lookup"><span data-stu-id="63fed-129">You can view the modeling flags associated with a mining structure column or model column in Data Mining Designer by viewing the properties of the structure or model.</span></span>  
  
 <span data-ttu-id="63fed-130">現在のマイニング構造に適用されているモデリング フラグを確認するには、データ マイニングのスキーマ行セットに対するクエリを作成し、その構造列のみのモデリング フラグを取得します。たとえば、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="63fed-130">To determine which modeling flags have been applied to the current mining structure, you can create a query against the data mining schema rowset that returns the modeling flags for just the structure columns, by using a query like the following:</span></span>  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_STRUCTURE_COLUMNS  
WHERE STRUCTURE_NAME = '<structure name>'  
```  
  
 <span data-ttu-id="63fed-131">モデルに使用されるモデリング フラグは、データ マイニング デザイナーを使用し、関連する列のプロパティを編集することによって追加または変更できます。</span><span class="sxs-lookup"><span data-stu-id="63fed-131">You can add or change the modeling flags used in a model by using the Data Mining Designer and editing the properties of the associated columns.</span></span> <span data-ttu-id="63fed-132">このような変更を行った場合、該当する構造またはモデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63fed-132">Such changes require that the structure or model be reprocessed.</span></span>  
  
 <span data-ttu-id="63fed-133">新しいマイニング構造またはマイニング モデルでモデリング フラグを指定するには、DMX を使用するか、AMO スクリプトまたは XMLA スクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="63fed-133">You can specify modeling flags in a new mining structure or mining model by using DMX, or by using AMO or XMLA scripts.</span></span> <span data-ttu-id="63fed-134">ただし、DMX を使用して、既存のマイニング モデルやマイニング構造で使用されているモデリング フラグを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="63fed-134">However, you cannot change the modeling flags used in an existing mining model and structure by using DMX.</span></span> <span data-ttu-id="63fed-135">`ALTER MINING STRUCTURE....ADD MINING MODEL`構文を使用して新しいマイニング モデルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63fed-135">You must create a new mining model by using the syntax, `ALTER MINING STRUCTURE....ADD MINING MODEL`.</span></span>  
  
##  <a name="uses-of-the-regressor-modeling-flag"></a><a name="bkmk_UseRegressors"></a> <span data-ttu-id="63fed-136">REGRESSOR モデリング フラグの使用</span><span class="sxs-lookup"><span data-stu-id="63fed-136">Uses of the REGRESSOR Modeling Flag</span></span>  
 <span data-ttu-id="63fed-137">列に REGRESSOR モデリング フラグを設定すると、その列にリグレッサー候補が含まれていることがアルゴリズムに対して示されます。</span><span class="sxs-lookup"><span data-stu-id="63fed-137">When you set the REGRESSOR modeling flag on a column, you are indicating to the algorithm that the column contains potential regressors.</span></span> <span data-ttu-id="63fed-138">モデルで使用される実際のリグレッサーはアルゴリズムによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="63fed-138">The actual regressors that are used in the model are determined by the algorithm.</span></span> <span data-ttu-id="63fed-139">予測可能な属性をモデル化しないリグレッサー候補は破棄できます。</span><span class="sxs-lookup"><span data-stu-id="63fed-139">A potential regressor can be discarded if it does not model the predictable attribute.</span></span>  
  
 <span data-ttu-id="63fed-140">データ マイニング ウィザードを使用してモデルを作成すると、連続列である入力列のすべてにリグレッサー候補のフラグが付けられます。</span><span class="sxs-lookup"><span data-stu-id="63fed-140">When you build a model by using the Data Mining wizard, all continuous input columns are flagged as possible regressors.</span></span> <span data-ttu-id="63fed-141">したがって、REGRESSOR フラグを明示的に設定していない列がモデルでリグレッサーとして使用される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="63fed-141">Therefore, even if you do not explicitly set the REGRESSOR flag on a column, the column might be used as a regressor in the model.</span></span>  
  
 <span data-ttu-id="63fed-142">処理されたモデルで実際に使用されたリグレッサーを特定するには、マイニング モデルのスキーマ行セットに対してクエリを実行します。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="63fed-142">You can determine the regressors that were actually used in the processed model by performing a query against the schema rowset for the mining model, as shown in the following example:</span></span>  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_COLUMNS  
WHERE MODEL_NAME = '<model name>'  
```  
  
 <span data-ttu-id="63fed-143">**注** マイニング モデルを変更して、列のコンテンツの種類を連続から不連続に変更した場合は、マイニング列のフラグを手動で変更してからモデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63fed-143">**Note** If you modify a mining model and change the content type of a column from continuous to discrete, you must manually change the flag on the mining column and then reprocess the model.</span></span>  
  
### <a name="regressors-in-linear-regression-models"></a><span data-ttu-id="63fed-144">線形回帰モデルのリグレッサー</span><span class="sxs-lookup"><span data-stu-id="63fed-144">Regressors in Linear Regression Models</span></span>  
 <span data-ttu-id="63fed-145">線形回帰モデルは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムに基づいています。</span><span class="sxs-lookup"><span data-stu-id="63fed-145">Linear regression models are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="63fed-146">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを使用していない場合でも、連続属性の回帰を表すツリーやノードがデシジョン ツリー モデルに含まれることはあります。</span><span class="sxs-lookup"><span data-stu-id="63fed-146">Even if you do not use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, any decision tree model can contain a tree or nodes that represents a regression on a continuous attribute.</span></span>  
  
 <span data-ttu-id="63fed-147">したがって、これらのモデルについては、連続列がリグレッサーを表すことを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="63fed-147">Therefore, in these models you do not need to specify that a continuous column represents a regressor.</span></span> <span data-ttu-id="63fed-148">列に REGRESSOR フラグを設定しなくても、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムにより、データセットが意味のあるパターンを持つ領域に分割されます。</span><span class="sxs-lookup"><span data-stu-id="63fed-148">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm will partition the dataset into regions with meaningful patterns even if you do not set the REGRESSOR flag on the column.</span></span> <span data-ttu-id="63fed-149">違いは、このモデリング フラグを設定すると、ツリーのノードのパターンに合う以下の形式の回帰式をアルゴリズムが見つけようとするということです。</span><span class="sxs-lookup"><span data-stu-id="63fed-149">The difference is that when you set the modeling flag, the algorithm will try to find regression equations of the following form to fit the patterns in the nodes of  the tree.</span></span>  
  
 <span data-ttu-id="63fed-150">a\*C1 + b\*C2 + ...</span><span class="sxs-lookup"><span data-stu-id="63fed-150">a\*C1 + b\*C2 + ...</span></span>  
  
 <span data-ttu-id="63fed-151">その後、残差の合計が計算され、偏差が大きすぎる場合には、ツリーが強制的に分割されます。</span><span class="sxs-lookup"><span data-stu-id="63fed-151">Then, the sum of the residuals is calculated, and if the deviation is too great, a split is forced in the tree.</span></span>  
  
 <span data-ttu-id="63fed-152">たとえば、 **Income** を属性として使用して顧客の購入行動を予測する場合に、その列に REGRESSOR モデリング フラグを設定すると、アルゴリズムはまず、標準の回帰式を使用して **Income** の値を試します。</span><span class="sxs-lookup"><span data-stu-id="63fed-152">For example, if you are predicting customer purchasing behavior using **Income** as an attribute, and set the REGRESSOR modeling flag on the column, the algorithm would first try to fit the **Income** values by using a standard regression formula.</span></span> <span data-ttu-id="63fed-153">偏差が大きすぎる場合はその回帰式が放棄され、ツリーが他の属性で分割されます。</span><span class="sxs-lookup"><span data-stu-id="63fed-153">If the deviation is too great, the regression formula is abandoned and the tree would be split on some other attribute.</span></span> <span data-ttu-id="63fed-154">その後デシジョン ツリー アルゴリズムは、分割後の各分岐で、Income をリグレッサーとして使用できるかどうかを試します。</span><span class="sxs-lookup"><span data-stu-id="63fed-154">The decision tree algorithm would then try fit a regressor for income in each of the branches after the split.</span></span>  
  
 <span data-ttu-id="63fed-155">FORCE_REGRESSOR パラメーターを使用すると、アルゴリズムで特定のリグレッサーが使用されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="63fed-155">You can use the FORCE_REGRESSOR parameter to guarantee that the algorithm will use a particular regressor.</span></span> <span data-ttu-id="63fed-156">このパラメーターは、デシジョン ツリー アルゴリズムと線形回帰アルゴリズムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="63fed-156">This parameter can be used with the Decision Trees algorithm and Linear Regression algorithm.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="63fed-157">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="63fed-157">Related Tasks</span></span>  
 <span data-ttu-id="63fed-158">モデリング フラグの使用の詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="63fed-158">Use the following links to learn more about using modeling flags.</span></span>  
  
|<span data-ttu-id="63fed-159">タスク</span><span class="sxs-lookup"><span data-stu-id="63fed-159">Task</span></span>|<span data-ttu-id="63fed-160">トピック</span><span class="sxs-lookup"><span data-stu-id="63fed-160">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="63fed-161">データ マイニング デザイナーを使用してモデリング フラグを編集する</span><span class="sxs-lookup"><span data-stu-id="63fed-161">Edit modeling flags by using the Data Mining Designer</span></span>|[<span data-ttu-id="63fed-162">モデリング フラグの表示または変更 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="63fed-162">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|  
|<span data-ttu-id="63fed-163">適切なリグレッサーを推奨するためのヒントをアルゴリズムに対して指定する</span><span class="sxs-lookup"><span data-stu-id="63fed-163">Specify a hint to the algorithm to recommend likely regressors</span></span>|[<span data-ttu-id="63fed-164">モデルでリグレッサーとして使用する列の指定</span><span class="sxs-lookup"><span data-stu-id="63fed-164">Specify a Column to Use as Regressor in a Model</span></span>](specify-a-column-to-use-as-regressor-in-a-model.md)|  
|<span data-ttu-id="63fed-165">特定のアルゴリズムでサポートされているモデリング フラグを確認する (各アルゴリズムのリファレンス トピックの「モデリング フラグ」セクション)</span><span class="sxs-lookup"><span data-stu-id="63fed-165">See the modeling flags supported by specific algorithms (in the Modeling Flags section for each algorithm reference topic)</span></span>|[<span data-ttu-id="63fed-166">データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="63fed-166">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)|  
|<span data-ttu-id="63fed-167">マイニング構造列とそこに設定できるプロパティについて詳しく知る</span><span class="sxs-lookup"><span data-stu-id="63fed-167">Learn more about mining structure columns and the properties that you can set on them</span></span>|[<span data-ttu-id="63fed-168">マイニング構造列</span><span class="sxs-lookup"><span data-stu-id="63fed-168">Mining Structure Columns</span></span>](mining-structure-columns.md)|  
|<span data-ttu-id="63fed-169">モデル レベルで適用できるマイニング モデル列とモデリング フラグについて知る</span><span class="sxs-lookup"><span data-stu-id="63fed-169">Learn about mining model columns and modeling flags that can be applied at the model level</span></span>|[<span data-ttu-id="63fed-170">マイニング モデル列</span><span class="sxs-lookup"><span data-stu-id="63fed-170">Mining Model Columns</span></span>](mining-model-columns.md)|  
|<span data-ttu-id="63fed-171">モデリング フラグを DMX ステートメントで扱うための構文を確認する</span><span class="sxs-lookup"><span data-stu-id="63fed-171">See syntax for  working with modeling  flags in DMX statements</span></span>|[<span data-ttu-id="63fed-172">モデリング フラグ (DMX)</span><span class="sxs-lookup"><span data-stu-id="63fed-172">Modeling Flags &#40;DMX&#41;</span></span>](/sql/dmx/modeling-flags-dmx)|  
|<span data-ttu-id="63fed-173">不足値とその取り扱いの方法について知る</span><span class="sxs-lookup"><span data-stu-id="63fed-173">Understand missing values and how to work with  them</span></span>|[<span data-ttu-id="63fed-174">不足値 &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="63fed-174">Missing Values &#40;Analysis Services - Data Mining&#41;</span></span>](missing-values-analysis-services-data-mining.md)|  
|<span data-ttu-id="63fed-175">モデルと構造の管理および使用法のプロパティの設定について知る</span><span class="sxs-lookup"><span data-stu-id="63fed-175">Learn about managing models and structures and setting usage properties</span></span>|[<span data-ttu-id="63fed-176">データ マイニング オブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="63fed-176">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)|  
  
  
