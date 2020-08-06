---
title: モデルビューアーからのドリルスルーの使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e5e065ad-c688-4c2c-8c82-7f3038e04915
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97bf20023009ec0e245126644d9fd38537182b2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720390"
---
# <a name="use-drillthrough-from-the-model-viewers"></a><span data-ttu-id="20abb-102">モデル ビューアーからのドリルスルーの使用</span><span class="sxs-lookup"><span data-stu-id="20abb-102">Use Drillthrough from the Model Viewers</span></span>
  <span data-ttu-id="20abb-103">モデルの種類に応じて、データ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにある参照ビューアーのドリルスルーを使用して、マイニング モデルで使用されているケースを調べたり、マイニング構造の追加列を参照したりできます。</span><span class="sxs-lookup"><span data-stu-id="20abb-103">Depending on the model type, you can use drillthrough from the browse viewers on the **Mining Model Viewer** tab of Data Mining Designer to explore the cases used in the mining model or to see additional columns in the mining structure.</span></span> <span data-ttu-id="20abb-104">モデルのパターンは特定のケースに直接リンクできないため、多くのモデルの種類ではドリルスルーがサポートされませんが、次のモデルの種類ではドリルスルーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="20abb-104">Although many model types do not support drillthrough because the patterns in the model cannot be directly linked to specific cases, the following model types do support drillthrough.</span></span>  
  
 <span data-ttu-id="20abb-105">モデルでドリルスルーが有効になっている必要があり、適切な権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="20abb-105">Note that drillthrough must have been enabled on the model, and you must have the appropriate permissions.</span></span> <span data-ttu-id="20abb-106">モデルが以前に処理されたかどうか、またコンテンツがあるかどうかにかかわらず、ドリルスルー オプションはモデルが未処理状態の場合にも無効になることがあります。</span><span class="sxs-lookup"><span data-stu-id="20abb-106">The drillthrough option might also be disabled if the model is in an unprocessed state, regardless of whether the model was previously processed and has content.</span></span> <span data-ttu-id="20abb-107">ドリルスルーを使用してモデル ケース データを取得するには、構造とモデルのキャッシュが最新である必要があります。</span><span class="sxs-lookup"><span data-stu-id="20abb-107">To retrieve model case data by using drillthrough, the cache of the structure and model must be current.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-tree-viewer"></a><span data-ttu-id="20abb-108">Microsoft ツリー ビューアーでのドリルスルーの使用</span><span class="sxs-lookup"><span data-stu-id="20abb-108">Use drillthrough in the Microsoft Tree Viewer</span></span>  
  
1.  <span data-ttu-id="20abb-109">データ マイニング デザイナーで、デシジョン ツリー モデルを選択し、 **[モデルの参照]** を選択して **[Microsoft ツリー ビューアー]** にモデルを開きます。</span><span class="sxs-lookup"><span data-stu-id="20abb-109">In Data Mining Designer, select a decision trees model, and select **Browse Model** to open the model in the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="20abb-110">SQL Server Management Studio でモデルを右クリックし、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20abb-110">In SQL Server Management Studio, right-click the model, and select **Browse**</span></span>  
  
2.  <span data-ttu-id="20abb-111">ツリー グラフの任意のノードを右クリックし、 **[ドリルスルー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="20abb-111">Right-click any node in the tree graph, and select **Drill through**.</span></span>  
  
3.  <span data-ttu-id="20abb-112">**[モデル列のみ]** または **[モデル列および構造列]** のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20abb-112">Select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="20abb-113">権限がない場合は、オプションを利用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="20abb-113">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="20abb-114">**[ドリルスルー]** ダイアログ ボックスが開き、ケース データ、構造データ、またはその両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="20abb-114">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="20abb-115">ダイアログ ボックスのタイトル バーには、ドリルスルー クエリが実行されたノードを識別する説明も表示されます。</span><span class="sxs-lookup"><span data-stu-id="20abb-115">The title bar of the dialog box also contains a description that identifies the node from which the drillthrough query was executed.</span></span>  
  
5.  <span data-ttu-id="20abb-116">結果内の任意の場所を右クリックし、 **[すべてコピー]** をクリックして結果をクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="20abb-116">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-cluster-viewer"></a><span data-ttu-id="20abb-117">Microsoft クラスター ビューアーでのドリルスルーの使用</span><span class="sxs-lookup"><span data-stu-id="20abb-117">Use drillthrough in the Microsoft Cluster Viewer</span></span>  
  
1.  <span data-ttu-id="20abb-118">データ マイニング デザイナーで、クラスター モデルを選択し、 **[モデルの参照]** を選択して **[Microsoft クラスター ビューアー]** にモデルを開きます。</span><span class="sxs-lookup"><span data-stu-id="20abb-118">In Data Mining Designer, select a clustering model, and select **Browse Model** to open the model in the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="20abb-119">SQL Server Management Studio で、モデルを右クリックし、[**参照**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="20abb-119">In SQL Server Management Studio, right-click the model, and select **Browse**.</span></span>  
  
2.  <span data-ttu-id="20abb-120">**[クラスター]** タブで、任意のノードを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="20abb-120">On the **Cluster** tab, right-click any node.</span></span>  
  
3.  <span data-ttu-id="20abb-121">**[ドリルスルー]** を選択してから、 **[モデル列のみ]** または **[モデル列および構造列]** のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20abb-121">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="20abb-122">権限がない場合は、オプションを利用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="20abb-122">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="20abb-123">**[ドリルスルー]** ダイアログ ボックスが開き、ケース データ、構造データ、またはその両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="20abb-123">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="20abb-124">ダイアログ ボックスのタイトル バーには、ケースのクラスターを識別する説明も表示されます。</span><span class="sxs-lookup"><span data-stu-id="20abb-124">The title bar of the dialog box also contains a description that identifies the cluster for the cases.</span></span>  
  
5.  <span data-ttu-id="20abb-125">結果内の任意の場所を右クリックし、 **[すべてコピー]** をクリックして結果をクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="20abb-125">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-association-rules-viewer"></a><span data-ttu-id="20abb-126">Microsoft アソシエーション ルール ビューアーでのドリルスルーの使用</span><span class="sxs-lookup"><span data-stu-id="20abb-126">Use drillthrough in the Microsoft Association Rules Viewer</span></span>  
  
1.  <span data-ttu-id="20abb-127">データ マイニング デザイナーで、アソシエーション モデルを選択し、 **[モデルの参照]** を選択して **[Microsoft アソシエーション ルール ビューアー]** にモデルを開きます。</span><span class="sxs-lookup"><span data-stu-id="20abb-127">In Data Mining Designer, select an association model, and select **Browse Model** to open the model in the **Microsoft Association Rules Viewer**.</span></span> <span data-ttu-id="20abb-128">SQL Server Management Studio でモデルを右クリックし、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20abb-128">In SQL Server Management Studio, right-click the model, and select **Browse**</span></span>  
  
2.  <span data-ttu-id="20abb-129">**[ルール]** タブで、ルールを表す任意の行を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="20abb-129">On the **Rules** tab, right-click any row that represents a rule.</span></span> <span data-ttu-id="20abb-130">**[アイテムセット]** タブで、アイテムセットを含む任意の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20abb-130">On the **Itemsets** tab, click on any row that contains an itemset.</span></span>  
  
3.  <span data-ttu-id="20abb-131">**[ドリルスルー]** を選択してから、 **[モデル列のみ]** または **[モデル列および構造列]** のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20abb-131">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="20abb-132">権限がない場合は、オプションを利用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="20abb-132">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="20abb-133">**[ドリルスルー]** ダイアログ ボックスが開き、ケース データ、構造データ、またはその両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="20abb-133">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="20abb-134">ダイアログ ボックスのタイトル バーには、ルール名を識別する説明も表示されます。</span><span class="sxs-lookup"><span data-stu-id="20abb-134">The title bar of the dialog box also contains a description that identifies the rule name.</span></span>  
  
5.  <span data-ttu-id="20abb-135">結果内の任意の場所を右クリックし、 **[すべてコピー]** をクリックしてケースの結果全体をクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="20abb-135">Right-click anywhere in the results and select **Copy All** to save the complete case results to the Clipboard.</span></span> <span data-ttu-id="20abb-136">**[コピー]** を選択して、選択したケースのみコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="20abb-136">You can also select **Copy** to copy just the selected case.</span></span> <span data-ttu-id="20abb-137">モデルに入れ子になったテーブル列が含まれる場合は、入れ子になったテーブル列の名前のみ貼り付けられます。各ケースの入れ子になったテーブル列内のデータ値を取得するには、モデル コンテンツに対するクエリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20abb-137">If the model contains a nested table column, only the name of the nested table column is pasted; to retrieve the data values inside the nested table column for each case you must create a query on the model content.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-sequence-cluster-viewer"></a><span data-ttu-id="20abb-138">Microsoft シーケンス クラスター ビューアーでのドリルスルーの使用</span><span class="sxs-lookup"><span data-stu-id="20abb-138">Use drillthrough in the Microsoft Sequence Cluster Viewer</span></span>  
  
1.  <span data-ttu-id="20abb-139">データ マイニング デザイナーで、クラスター モデルを選択し、 **[モデルの参照]** を選択して **[Microsoft クラスター ビューアー]** にモデルを開きます。</span><span class="sxs-lookup"><span data-stu-id="20abb-139">In Data Mining Designer, select a clustering model, and select **Browse Model** to open the model in the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="20abb-140">SQL Server Management Studio で、モデルを右クリックし、[**参照**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="20abb-140">In SQL Server Management Studio, right-click the model, and select **Browse**.</span></span>  
  
2.  <span data-ttu-id="20abb-141">**[クラスター ダイアグラム]** タブで、クラスターを表す任意のノードを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="20abb-141">On the **Cluster Diagram tab**, right-click any node that represents a cluster.</span></span> <span data-ttu-id="20abb-142">**[クラスターのプロファイル]** タブから、クラスター プロファイル内またはモデルの母集団を表すクラスター内の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20abb-142">From the **Cluster Profiles** tab, click anywhere in a cluster profile or in the cluster representing the total model population.</span></span>  
  
3.  <span data-ttu-id="20abb-143">**[ドリルスルー]** を選択してから、 **[モデル列のみ]** または **[モデル列および構造列]** のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20abb-143">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="20abb-144">権限がない場合は、オプションを利用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="20abb-144">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="20abb-145">**[ドリルスルー]** ダイアログ ボックスが開き、ケース データ、構造データ、またはその両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="20abb-145">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="20abb-146">ダイアログ ボックスのタイトル バーには、ケースのクラスターを識別する説明も表示されます。</span><span class="sxs-lookup"><span data-stu-id="20abb-146">The title bar of the dialog box also contains a description that identifies the cluster for the cases.</span></span>  
  
5.  <span data-ttu-id="20abb-147">結果内の任意の場所を右クリックし、 **[すべてコピー]** をクリックして結果をクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="20abb-147">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span> <span data-ttu-id="20abb-148">モデルに入れ子になったテーブル列が含まれる場合は、入れ子になったテーブル列の名前のみ貼り付けられます。各ケースの入れ子になったテーブル列内のデータ値を取得するには、モデル コンテンツに対するクエリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20abb-148">If the model contains a nested table column, only the name of the nested table column is pasted; to retrieve the data values inside the nested table column for each case you must create a query on the model content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20abb-149">参照</span><span class="sxs-lookup"><span data-stu-id="20abb-149">See Also</span></span>  
 <span data-ttu-id="20abb-150">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="20abb-150">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="20abb-151">[マイニングモデルでのドリルスルー](drillthrough-on-mining-models.md) </span><span class="sxs-lookup"><span data-stu-id="20abb-151">[Drillthrough on Mining Models](drillthrough-on-mining-models.md) </span></span>  
 [<span data-ttu-id="20abb-152">マイニング構造でのドリルスルー</span><span class="sxs-lookup"><span data-stu-id="20abb-152">Drillthrough on Mining Structures</span></span>](drillthrough-on-mining-structures.md)  
  
  
