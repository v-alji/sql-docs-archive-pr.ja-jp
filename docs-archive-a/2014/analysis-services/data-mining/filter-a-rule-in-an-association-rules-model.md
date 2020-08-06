---
title: アソシエーションルールモデルでルールをフィルター処理する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filtering rules [Analysis Services]
- Mining Model Viewer [Analysis Services], rules
- Rules Viewer
ms.assetid: 26cdba5b-5bf1-439e-80a3-8759774e918b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c904713acc6eaf132e7cb1195186165f21d971a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642414"
---
# <a name="filter-a-rule-in-an-association-rules-model"></a><span data-ttu-id="d8d53-102">アソシエーション ルール モデルのルールのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="d8d53-102">Filter a Rule in an Association Rules Model</span></span>
  <span data-ttu-id="d8d53-103">アソシエーション モデルでフィルターを使用して、結果を必要なアソシエーションだけに限定できます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-103">You can use filtering with association models to restrict the results to just the associations that interest you.</span></span> <span data-ttu-id="d8d53-104">たとえば、ルールをフィルター選択して、特定の製品を含むルールだけを表示できます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-104">For example, you might filter the rules to show only those that include a specific product.</span></span>  
  
 <span data-ttu-id="d8d53-105">データ マイニング デザイナーで、 **アソシエーション ルール ビューアーの** [ルール] [!INCLUDE[msCoName](../../includes/msconame-md.md)] タブのコントロールを使用して、表示されるルールをフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="d8d53-105">In Data Mining Designer, you use the controls on the **Rules** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer to filter the rules that are displayed.</span></span>  <span data-ttu-id="d8d53-106">モデルに対するクエリを作成して、特定の値が格納されているアイテムセットだけを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-106">You can also create a query on the model to see only itemset that contains a particular value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8d53-107">このオプションは、Microsoft アソシエーション アルゴリズムを使用して作成されたマイニング モデルに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-107">This option is available only for mining models that have been created by using the Microsoft Association Algorithm.</span></span>  
  
### <a name="filter-a-rule-in-an-association-model"></a><span data-ttu-id="d8d53-108">アソシエーション モデルのルールのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="d8d53-108">Filter a rule in an association model</span></span>  
  
1.  <span data-ttu-id="d8d53-109">**アソシエーション ルール ビューアー**を使用してマイニング モデルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-109">Open the mining model by using the **Association Rules Viewer**.</span></span> <span data-ttu-id="d8d53-110">SQL Server Management Studio でマイニング モデルを開くには、モデル名を右クリックして **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8d53-110">To do this in SQL Server Management Studio, right click the model name and select **Browse**.</span></span> <span data-ttu-id="d8d53-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でマイニング モデルを開くには、モデルを含むマイニング構造をダブルクリックし、 **データ マイニング デザイナー** の **[マイニング モデル ビューアー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8d53-111">To do this in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the mining structure that contains the model, and then click the **Mining Model Viewer** tab of **Data Mining Designer**.</span></span>  
  
2.  <span data-ttu-id="d8d53-112">**アソシエーション ルール ビューアー** の **[ルール]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8d53-112">Click the **Rules** tab of the **Association Rules Viewer**.</span></span>  
  
3.  <span data-ttu-id="d8d53-113">**[ルールのフィルター]** ボックスにルールの条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="d8d53-113">Type a rule condition into the **Filter Rule** box.</span></span> <span data-ttu-id="d8d53-114">たとえば、「Bike Stand」というルールの条件を入力すると、"Bike Stands" も返されます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-114">For example, a rule condition might be "Bike Stand", which also returns "Bike Stands".</span></span>  
  
     <span data-ttu-id="d8d53-115">**[ルールのフィルター]** テキスト ボックスでは、.NET 言語で定義されている正規表現を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-115">The **Filter Rule** text box supports regular expressions as defined by the .NET language.</span></span> <span data-ttu-id="d8d53-116">したがって、 `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`のような式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-116">Therefore, you can use expressions such as the following: `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`.</span></span> <span data-ttu-id="d8d53-117">この式は、Helmets と Fenders という単語が任意の順序で含まれる属性を含むすべてのアイテムセットを返します。</span><span class="sxs-lookup"><span data-stu-id="d8d53-117">This expression would return any itemsets that include attributes with the words Helmets and Fenders, in any order.</span></span>  
  
4.  <span data-ttu-id="d8d53-118">**[最小の確率]** では、確率の値を大きくすると表示されるルール数が減り、値を小さくすると表示されるルール数が増えます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-118">For **Minimum probability**, increase the value of probability to see fewer rules, or decrease the value to see more rules.</span></span>  
  
5.  <span data-ttu-id="d8d53-119">**[最小の重要度]** では、重要度の値を大きくすると表示されるルール数が減り、値を小さくすると表示されるルール数が増えます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-119">For **Minimum importance**, increase the value of importance to see fewer rules, or decrease the value to see more rules.</span></span>  
  
6.  <span data-ttu-id="d8d53-120">**[表示]** では、 **[属性の名前と値を表示]**、 **[属性名のみ表示]**、 **[属性値のみ表示]** のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d8d53-120">For **Show**, select one of the following options: **Show attribute name and value**, **Show attribute name only**, or **Show attribute value only**.</span></span>  
  
7.  <span data-ttu-id="d8d53-121">**[最大行数]** では、値を大きくすると指定した条件を満たすルールの総数が増え、値を小さくすると返されるルールの数が制限されます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-121">For **Maximum rows**, increase the value to increase the total number of rules that meet the specified conditions, or decrease the value to limit the number of rules returned.</span></span> <span data-ttu-id="d8d53-122">ルールは確率の順に並べられるので、確率または重要度に対して指定した条件を満たす余分なルールを除外できます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-122">Rules are ordered by probability, so you might eliminate additional rules that meet the specified conditions for probability or importance.</span></span>  
  
8.  <span data-ttu-id="d8d53-123">**[長い名前を表示する]** チェック ボックスをオンまたはオフにして、ルール名の表示方法を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-123">Select or deselect the **Show long name** check box to toggle the way that the rules names are displayed.</span></span>  
  
     <span data-ttu-id="d8d53-124">これでルールにフィルターが適用され、指定したアイテムを含むルールのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-124">The rules are now filtered to only display rules that contain the indicated item.</span></span> <span data-ttu-id="d8d53-125">フィルター条件は、ルール区切り記号 "->" の前または後の属性値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-125">The filter condition applies to attribute values either before or after the rule delimiter, "->".</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d8d53-126">ビューアーはマイニング モデルに対するクエリによって最初に作成されるルールの一覧をキャッシュしており、最大行数、確率、重要度、または長い名前の表示を設定することでクエリの条件を変更しない限り、この一覧は更新されません。</span><span class="sxs-lookup"><span data-stu-id="d8d53-126">The viewer caches the initial list of rules, based on a query to the mining model, and does not refresh the list of rules unless you change the conditions of the query by setting the maximum rows, the probability, importance, or the display of long names.</span></span> <span data-ttu-id="d8d53-127">したがって、条件を入力しても表示がすぐに更新されない場合は、 **[長い名前を表示する]** チェック ボックスをオンにしてからオフにすることで、強制的にビューアーのデータを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="d8d53-127">Therefore, if you type a condition and the display does not immediately refresh, you can force the viewer to refresh the data by selecting and then deselecting the **Show long names** check box.</span></span>  
  
### <a name="create-a-query-on-the-itemsets-in-an-association-model"></a><span data-ttu-id="d8d53-128">アソシエーション モデルのアイテムセットに対するクエリの作成</span><span class="sxs-lookup"><span data-stu-id="d8d53-128">Create a query on the itemsets in an association model</span></span>  
  
-   [<span data-ttu-id="d8d53-129">結合モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="d8d53-129">Association Model Query Examples</span></span>](association-model-query-examples.md)  
  
## <a name="see-also"></a><span data-ttu-id="d8d53-130">参照</span><span class="sxs-lookup"><span data-stu-id="d8d53-130">See Also</span></span>  
 <span data-ttu-id="d8d53-131">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="d8d53-131">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="d8d53-132">[Microsoft アソシエーションルールビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-association-rules-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="d8d53-132">[Browse a Model Using the Microsoft Association Rules Viewer](browse-a-model-using-the-microsoft-association-rules-viewer.md) </span></span>  
 [<span data-ttu-id="d8d53-133">レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="d8d53-133">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
