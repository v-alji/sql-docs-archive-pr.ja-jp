---
title: '[トレーニングデータの指定] (データマイニングウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytrainingdata.f1
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87a802256d287a3e8e9e7fb65bbd91687cb71a4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643504"
---
# <a name="specify-the-training-data-data-mining-wizard"></a><span data-ttu-id="64342-102">[トレーニング データの指定] (データ マイニング ウィザード)</span><span class="sxs-lookup"><span data-stu-id="64342-102">Specify the Training Data (Data Mining Wizard)</span></span>
  <span data-ttu-id="64342-103">**[トレーニング データの指定]** ページを使用すると、マイニング構造に含める列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="64342-103">Use the **Specify the Training Data** page to identify which columns to include in the mining structure.</span></span> <span data-ttu-id="64342-104">構造に含める列をすべてのモデルで使用するとは限らない場合でも、それらの列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="64342-104">You can select columns to include in the structure even if you do not use them in all models.</span></span> <span data-ttu-id="64342-105">たとえば、マイニング モデルから列にドリルスルーする場合は、それらの列をモデルには含めずに構造に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="64342-105">For example, if you want to drill through to the columns from the mining model, you can include them in the structure but not in the model.</span></span>  
  
 <span data-ttu-id="64342-106">構造に含まれる各テーブルには、少なくとも 1 つのキー列が必要です。</span><span class="sxs-lookup"><span data-stu-id="64342-106">At least one key column is required for each table that is included in the structure.</span></span> <span data-ttu-id="64342-107">キーとして選択する列は、テーブルがケース テーブルか入れ子になったテーブルかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="64342-107">The column that you pick as the key depends on whether the table is a case table or a nested table.</span></span> <span data-ttu-id="64342-108">テーブルが入れ子になったテーブルである場合は、通常、キーは予測可能列でもあり、リレーショナル外部キーではありません。</span><span class="sxs-lookup"><span data-stu-id="64342-108">If the table is a nested table, the key is often also the predictable column, not the relational foreign key.</span></span> <span data-ttu-id="64342-109">入れ子になったキーについては、「[入れ子になったテーブル &#40;Analysis Services - データ マイニング&#41;](data-mining/nested-tables-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64342-109">To learn about nested keys, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64342-110">マイニング アルゴリズムごとに、異なるキーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="64342-110">Different mining algorithms use keys differently.</span></span> <span data-ttu-id="64342-111">各種のキーの詳細については、「[コンテンツの種類 &#40;データ マイニング&#41;](data-mining/content-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64342-111">To learn about the different kinds of keys, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="64342-112">**詳細:** [マイニング構造 &#40;Analysis Services - データ マイニング&#41;](data-mining/mining-structures-analysis-services-data-mining.md)、[マイニング モデル列](data-mining/mining-model-columns.md)、[データ マイニング ウィザード &#40;Analysis Services - データ マイニング&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[リレーショナル マイニング構造の作成](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="64342-112">**For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Mining Model Columns](data-mining/mining-model-columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="64342-113">Options</span><span class="sxs-lookup"><span data-stu-id="64342-113">Options</span></span>  
 <span data-ttu-id="64342-114">**テーブルまたは列**</span><span class="sxs-lookup"><span data-stu-id="64342-114">**Tables/Columns**</span></span>  
 <span data-ttu-id="64342-115">ウィザードの前のページで選択したテーブルおよび列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64342-115">Displays the tables and columns that you selected on the previous page of the wizard.</span></span>  
  
 **\<check box>**  
 <span data-ttu-id="64342-116">マイニング構造に含める列を選択します。</span><span class="sxs-lookup"><span data-stu-id="64342-116">Select the columns to include in the mining structure.</span></span>  
  
 <span data-ttu-id="64342-117">データ ソースに入れ子になったテーブルまたは複数のビューが含まれている場合は、列の一覧を展開して入れ子になったテーブルを表示します。</span><span class="sxs-lookup"><span data-stu-id="64342-117">If your data source includes nested tables or multiple views, expand the column list to view the nested tables.</span></span>  
  
 <span data-ttu-id="64342-118">**[キー]**</span><span class="sxs-lookup"><span data-stu-id="64342-118">**Key**</span></span>  
 <span data-ttu-id="64342-119">データの一意識別子として使用される列を選択します。</span><span class="sxs-lookup"><span data-stu-id="64342-119">Select to use the column as a unique identifier for the data.</span></span>  
  
 <span data-ttu-id="64342-120">ケース テーブルの場合、通常、キーは一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="64342-120">For a case table, the key is usually the unique identifier.</span></span>  
  
 <span data-ttu-id="64342-121">入れ子になったテーブルの場合は、 **[キー]** により、関連付けられているケースのコンテキスト内の行の識別子が指定されます。</span><span class="sxs-lookup"><span data-stu-id="64342-121">For nested table, the **Key** indicates the identifier of a row in the context of the associated case.</span></span>  
  
 <span data-ttu-id="64342-122">**入力**</span><span class="sxs-lookup"><span data-stu-id="64342-122">**Input**</span></span>  
 <span data-ttu-id="64342-123">推奨設定の作成時にこの列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="64342-123">Select to use the column in creating predictions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64342-124">この列を使用できるのは、マイニング モデルをマイニング構造と共に作成する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="64342-124">This column is only available when you are creating a mining model together with the mining structure.</span></span>  
  
 <span data-ttu-id="64342-125">**[予測可能]**</span><span class="sxs-lookup"><span data-stu-id="64342-125">**Predictable**</span></span>  
 <span data-ttu-id="64342-126">このテーブルまたは列が今後の追加入力に基づいて予測できるようにします。</span><span class="sxs-lookup"><span data-stu-id="64342-126">Select to enable the table or column to be predicted based on additional future input.</span></span>  
  
 <span data-ttu-id="64342-127">入れ子になったテーブルを予測可能として指定すると、入れ子になったテーブル全体が予測可能になります。</span><span class="sxs-lookup"><span data-stu-id="64342-127">If you also mark a nested table as predictable, the whole nested table becomes predictable.</span></span> <span data-ttu-id="64342-128">入れ子になったテーブル内で入力列または予測可能列として指定されている列がない場合、そのテーブルはマイニング構造に表示されても、モデル内では無視されます。</span><span class="sxs-lookup"><span data-stu-id="64342-128">If no columns in the nested table are marked as input or predictable, the nested table will appear in the mining structure, but will be ignored in the model.</span></span>  
  
 <span data-ttu-id="64342-129">**メモ** : この列を使用できるのは、マイニング モデルをマイニング構造と共に作成する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="64342-129">**Note** This column is only available when you are creating a mining model together with the mining structure.</span></span>  
  
 <span data-ttu-id="64342-130">**候補**</span><span class="sxs-lookup"><span data-stu-id="64342-130">**Suggest**</span></span>  
 <span data-ttu-id="64342-131">クリックすると、 **[関連列の提示]** ダイアログ ボックスが開きます。ここで、サンプル データに基づいて分析を実行し、選択した **[予測可能]** 列に対してエントロピに基づく最大のリレーションシップを持つ入力列を識別します。</span><span class="sxs-lookup"><span data-stu-id="64342-131">Click to open the **Suggest Related Columns** dialog box, which performs an analysis on a sample of data to identify input columns that show the greatest relationship to the selected **Predictable** column based on entropy.</span></span> <span data-ttu-id="64342-132">この分析は、OLAP ソースに基づく入れ子になったテーブル列またはマイニング構造にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="64342-132">This analysis also applies to nested table columns or mining structures that are based on OLAP sources.</span></span>  
  
 <span data-ttu-id="64342-133">**メモ** : この列を使用できるのは、マイニング モデルをマイニング構造と共に作成する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="64342-133">**Note** This column only available when you are creating a mining model together with the mining structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64342-134">参照</span><span class="sxs-lookup"><span data-stu-id="64342-134">See Also</span></span>  
 <span data-ttu-id="64342-135">[データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="64342-135">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="64342-136">[データマイニングウィザード &#40;関連する列の提案&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="64342-136">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="64342-137">[データマイニングウィザード &#40;テーブルの種類の指定&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="64342-137">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="64342-138">列のコンテンツとデータ型 &#40;データマイニングウィザードを指定し&#41;</span><span class="sxs-lookup"><span data-stu-id="64342-138">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
