---
title: テンプレートからの単一予測クエリの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton query predictions [DMX]
ms.assetid: e0a68ab0-bece-4d25-b464-47f1719302e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80e853875cce349dd8623fab3c30f1ad09bfbf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632791"
---
# <a name="create-a-singleton-prediction-query-from-a-template"></a><span data-ttu-id="99997-102">テンプレートからの単一予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="99997-102">Create a Singleton Prediction Query from a Template</span></span>
  <span data-ttu-id="99997-103">単一クエリは、予測に使用するモデルがあり、それを外部入力データセットにマップしたり、一括予測を行ったりしない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="99997-103">A singleton query is useful when you have a model that you want to use for prediction, but don't want to map it to an external input data set or make bulk predictions.</span></span> <span data-ttu-id="99997-104">単一クエリでは、モデルに 1 つまたは複数の値を提供し、予測される値を即時に参照できます。</span><span class="sxs-lookup"><span data-stu-id="99997-104">With a singleton query, you can provide a value or values to the model and instantly see the predicted value.</span></span>  
  
 <span data-ttu-id="99997-105">たとえば、次の DMX クエリは、メーリング対象モデル TM_Decision_Tree に対する単一クエリを表しています。</span><span class="sxs-lookup"><span data-stu-id="99997-105">For example, the following DMX query represents a singleton query against the targeted mailing model, TM_Decision_Tree.</span></span>  
  
```  
SELECT * FROM [TM_Decision_tree] ;  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 <span data-ttu-id="99997-106">次の手順では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でテンプレート エクスプローラーを使用してこのクエリを迅速に作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99997-106">The procedure that follows describes how to use the Template Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to quickly create this query.</span></span>  
  
### <a name="to-open-the-analysis-services-templates-in-sql-server-management-studio"></a><span data-ttu-id="99997-107">SQL Server Management Studio で Analysis Services テンプレートを開くには</span><span class="sxs-lookup"><span data-stu-id="99997-107">To open the Analysis Services templates in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="99997-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99997-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="99997-109">キューブ アイコンをクリックして、 **[分析サーバー]** テンプレートを開きます。</span><span class="sxs-lookup"><span data-stu-id="99997-109">Click the cube icon to open the **Analysis Server**templates.</span></span>  
  
### <a name="to-open-a-prediction-query-template"></a><span data-ttu-id="99997-110">予測クエリ テンプレートを開くには</span><span class="sxs-lookup"><span data-stu-id="99997-110">To open a prediction query template</span></span>  
  
1.  <span data-ttu-id="99997-111">**[テンプレート エクスプローラー]** の分析サーバー テンプレートの一覧から **[DMX]** を展開し、 **[予測クエリ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="99997-111">In **Template Explorer**, in the list of Analysis Server templates, expand **DMX**, and thenexpand **Prediction Queries**.</span></span>  
  
2.  <span data-ttu-id="99997-112">**[単一予測]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="99997-112">Double-click **Singleton Prediction**.</span></span>  
  
3.  <span data-ttu-id="99997-113">**[Analysis Services への接続]** ダイアログ ボックスで、クエリの対象であるマイニング モデルを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのあるサーバー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="99997-113">In the **Connect to Analysis Services** dialog box, type the name of the server that has the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining model to be queried.</span></span>  
  
4.  <span data-ttu-id="99997-114">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99997-114">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="99997-115">指定したデータベースでテンプレートが開き、データ マイニング関数と、データ マイニング構造および関連するモデルの一覧を示す、マイニング モデルのオブジェクト ブラウザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="99997-115">The template opens in the specified database, together with a mining model Object Browser that contains data mining functions and a list of data mining structures and related models.</span></span>  
  
### <a name="to-customize-the-singleton-query-template"></a><span data-ttu-id="99997-116">単一クエリ テンプレートをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="99997-116">To customize the singleton query template</span></span>  
  
1.  <span data-ttu-id="99997-117">テンプレートで、 **[使用できるデータベース]** ドロップダウン リストをクリックし、一覧から Analysis Services インスタンスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="99997-117">In the template, click the **Available Databases** drop-down list, and then select an instance of Analysis Service from the list.</span></span>  
  
2.  <span data-ttu-id="99997-118">**[マイニング モデル]** ボックスの一覧から、クエリの対象とするマイニング モデルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="99997-118">In the **Mining Model** list, select the mining model that you want to query.</span></span>  
  
     <span data-ttu-id="99997-119">マイニング モデルの列の一覧がオブジェクト ブラウザーの **[メタデータ]** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="99997-119">The list of columns in the mining model appears in the **Metadata** pane of the object browser.</span></span>  
  
3.  <span data-ttu-id="99997-120">**[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99997-120">On the **Query** menu, select **Specify Values for Template Parameters**.</span></span>  
  
4.  <span data-ttu-id="99997-121">**select list** 行に「\*」と入力するとすべての列が返され、列と式のコンマ区切りの一覧を入力すると特定の列が返されます。</span><span class="sxs-lookup"><span data-stu-id="99997-121">In the **select list** row, type \* to return all columns, or type a comma-delimited list of columns and expressions to return specific columns.</span></span>  
  
     <span data-ttu-id="99997-122">「\*」と入力すると、予測可能列と、手順 6. で新しい値を指定する列が返されます。</span><span class="sxs-lookup"><span data-stu-id="99997-122">If you type \*, the predictable column is returned, together with any columns for which you provide new values for in step 6.</span></span>  
  
     <span data-ttu-id="99997-123">このトピックの冒頭に示したサンプル コードでは、 **select list** 行を \* に設定していました。</span><span class="sxs-lookup"><span data-stu-id="99997-123">For the sample code shown at the start of this topic, the **select list** row was set to \*.</span></span>  
  
5.  <span data-ttu-id="99997-124">**mining model** 行には、 **オブジェクト エクスプローラー**に表示されるマイニング モデルの一覧からマイニング モデルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="99997-124">In the **mining model** row, type the name of the mining model from among the list of mining models that appear in **Object Explorer**.</span></span>  
  
     <span data-ttu-id="99997-125">このトピックの冒頭に示したサンプルコードでは、[**マイニングモデル**] 行にという名前が設定されて `TM_Decision_Tree` います。</span><span class="sxs-lookup"><span data-stu-id="99997-125">For the sample code shown at the start of this topic, the **mining model** row was set to the name, `TM_Decision_Tree`.</span></span>  
  
6.  <span data-ttu-id="99997-126">**value** 行には、予測を行う新しいデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="99997-126">In the **value** row, type the new data value for which you want to make a prediction.</span></span>  
  
     <span data-ttu-id="99997-127">このトピックの冒頭に示したサンプルコードでは、[**値**] 行をに設定して、 `2` 自宅の子供の数に基づいて自転車の購買行動を予測しました。</span><span class="sxs-lookup"><span data-stu-id="99997-127">For the sample code shown at the start of this topic, the **value** row was set to `2` to predict bike buying behavior based on the number of children at home.</span></span>  
  
7.  <span data-ttu-id="99997-128">**column** 行には、新しいデータをマップするマイニング モデルの列名を入力します。</span><span class="sxs-lookup"><span data-stu-id="99997-128">In the **column** row, type the name of the column in the mining model to which the new data should be mapped.</span></span>  
  
     <span data-ttu-id="99997-129">このトピックの冒頭に示したサンプルコードでは、**列**行はに設定されてい `Number Children at Home` ます。</span><span class="sxs-lookup"><span data-stu-id="99997-129">For the sample code shown at the start of this topic, the **column** row was set to `Number Children at Home`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="99997-130">**[テンプレート パラメーターの値の指定]** ダイアログ ボックスを使用する場合、列名を角かっこで囲む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="99997-130">When you use the **Specify Values for Template Parameters** dialog box, you do not have to add square brackets around the column name.</span></span> <span data-ttu-id="99997-131">角かっこは自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="99997-131">The brackets will automatically be added for you.</span></span>  
  
8.  <span data-ttu-id="99997-132">入力の**エイリアス**はのままにし `t` ます。</span><span class="sxs-lookup"><span data-stu-id="99997-132">Leave the **input alias** as `t`.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="99997-133">クエリのテキスト ペインで、コンマと省略記号の下に構文エラーを示す赤い波線がある箇所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="99997-133">In the query text pane, find the red squiggle under the comma and ellipsis that indicates a syntax error.</span></span> <span data-ttu-id="99997-134">省略記号を削除し、必要なクエリ条件を追加します。</span><span class="sxs-lookup"><span data-stu-id="99997-134">Delete the ellipsis, and add any additional query condition that you want.</span></span> <span data-ttu-id="99997-135">他の条件を追加しない場合はコンマを削除します。</span><span class="sxs-lookup"><span data-stu-id="99997-135">If you do not add any other conditions, delete the comma.</span></span>  
  
     <span data-ttu-id="99997-136">このトピックの冒頭に示したサンプル コードでは、追加のクエリ条件として `'45' as [Age]` を設定していました。</span><span class="sxs-lookup"><span data-stu-id="99997-136">For the sample code shown at the start of this topic, the additional query condition was set to `'45' as [Age]`.</span></span>  
  
11. <span data-ttu-id="99997-137">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99997-137">Click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99997-138">参照</span><span class="sxs-lookup"><span data-stu-id="99997-138">See Also</span></span>  
 [<span data-ttu-id="99997-139">予測の作成 &#40;基本的なデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="99997-139">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
  
