---
title: アソシエーションルールモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
author: minewiskan
ms.author: owend
ms.openlocfilehash: de5adbca264fff81b44424d865a2c8201a6fdfc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633555"
---
# <a name="browsing-an-association-rules-model"></a><span data-ttu-id="e603a-102">アソシエーション ルール モデルの参照</span><span class="sxs-lookup"><span data-stu-id="e603a-102">Browsing an Association Rules Model</span></span>
  <span data-ttu-id="e603a-103">**参照**を使用してアソシエーションモデルを開くと、のアソシエーションルールビューアーに似た対話型ビューアーにモデルが表示され [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e603a-103">When you open an association model using **Browse**, the model is displayed in an interactive viewer, similar to the Association Rules Viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  <span data-ttu-id="e603a-104">このビューアーを使用すると、相互に関連付けられたアイテムをひとめで確認できます。また、このビューアーには、予測または提案を行うために使用できるルールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-104">The viewer lets you see at a glance which items were correlated with each other, and displays rules that you can use for prediction or making recommendations.</span></span>  
  
##  <a name="explore-the-model"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="e603a-105">モデルの調査</span><span class="sxs-lookup"><span data-stu-id="e603a-105">Explore the Model</span></span>  
 <span data-ttu-id="e603a-106">アソシエーションルールアルゴリズムを使用して作成されたマイニングモデルを開くと、[ [!INCLUDE[msCoName](../includes/msconame-md.md)] **参照**] ウィンドウに次のビューが表示されます。各ビューは、モデルのさまざまな側面を調べることができるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e603a-106">When you open a mining model that was created using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm, the **Browse** window includes the following views, each designed to let you explore a different aspect of the model:</span></span>  
  
-   [<span data-ttu-id="e603a-107">アイテムセット</span><span class="sxs-lookup"><span data-stu-id="e603a-107">Itemsets</span></span>](#BKMK_Itemsets)  
  
-   [<span data-ttu-id="e603a-108">ルール</span><span class="sxs-lookup"><span data-stu-id="e603a-108">Rules</span></span>](#BKMK_Rules)  
  
-   [<span data-ttu-id="e603a-109">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="e603a-109">Dependency Net</span></span>](#BKMK_Dependency)  
  
 <span data-ttu-id="e603a-110">各タブの [**長い名前を表示する**] オプションをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="e603a-110">Take note of the option on each tab, **Show long name** .</span></span> <span data-ttu-id="e603a-111">このチェック ボックスをオンにすると、アイテムセットの元のテーブルを表示/非表示を切り替えたり、ルールまたはアイテムセットの名前の長さを変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e603a-111">By selecting this option, you can show or hide the table from which the itemset originates, and shorten or lengthen the name of the rule or itemset.</span></span> <span data-ttu-id="e603a-112">このオプションは、ケース データと属性データが異なるデータ ソースから取得されている場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e603a-112">This option is particularly useful when your case data and attribute data are from different data sources.</span></span>  
  
 <span data-ttu-id="e603a-113">アソシエーション モデルをテストするには、サンプル データ ブックの [関連付け] タブにあるサンプル データを使用し、すべて既定値のままでアソシエーション モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e603a-113">To experiment with an association model, you can use the sample data on the Associate tab of the sample data workbook, and build an association model using all the defaults.</span></span> <span data-ttu-id="e603a-114">また、買い物かご分析モデルを作成して、[**参照**] を使用して開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="e603a-114">You can also build a Shopping Basket Analysis model and open that using **Browse**.</span></span>  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a><span data-ttu-id="e603a-115">アイテムセット</span><span class="sxs-lookup"><span data-stu-id="e603a-115">Itemsets</span></span>  
 <span data-ttu-id="e603a-116">[**アイテムセット**] タブは、アソシエーションモデルの調査を開始するのに適した場所です。</span><span class="sxs-lookup"><span data-stu-id="e603a-116">The **Itemsets** tab is a good place to begin exploring an association model.</span></span> <span data-ttu-id="e603a-117">このタブには、モデルによって同時に検出される頻度の高いアイテムの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-117">This tab shows a list of the items that the model frequently found together.</span></span>  
  
 <span data-ttu-id="e603a-118">![アソシエーション モデルのアイテムの一覧](media/dm13-association-itemsets.gif "アソシエーション モデルのアイテムの一覧")</span><span class="sxs-lookup"><span data-stu-id="e603a-118">![List of items in an association model](media/dm13-association-itemsets.gif "List of items in an association model")</span></span>  
  
 <span data-ttu-id="e603a-119">アイテムセットの最も一般的な例は、買い物かごモデルにあります。買い物かごモデルでは、多くの顧客が同時に購入する製品の組み合わせやセットをアイテムセットで表します。</span><span class="sxs-lookup"><span data-stu-id="e603a-119">The most common example of itemsets is in a shopping basket model, where an itemset represents pairs or sets of products that lots of customers purchase at the same time.</span></span> <span data-ttu-id="e603a-120">ただし、アイテムをどのようにグループ化および並べ替えするかに応じて、アイテムセットには、顧客が一定期間に注文した一連の映画や、特定の場所で開催される傾向のあるイベントが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e603a-120">However, depending on how you group and order your items, the itemset might contain a sequence of movies that customers order over a period of time, or events that tend to occur in  a particular location.</span></span>  
  
 <span data-ttu-id="e603a-121">アイテムセットに含めることができる項目の数は 2 ~ 3 つ*ですが、* 多くの場合、モデルのアイテムセットの最大サイズとして設定されています。</span><span class="sxs-lookup"><span data-stu-id="e603a-121">An *itemset* can contain as few as one item to two, three, or however, many is set as the maximum itemset size for the model.</span></span> <span data-ttu-id="e603a-122">ビューアーには、アイテムセットの*サポート*、*確率*、および*サイズ*が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-122">For each itemset, the viewer displays the itemset  *support*,  *probability*, and *size*.</span></span> <span data-ttu-id="e603a-123">サポートと確率は、アソシエーション モデルで生成されたアイテムセットとルールに順位を付けるための主要な統計です。</span><span class="sxs-lookup"><span data-stu-id="e603a-123">Support and probability are the principal statistics used to rank the itemsets and rules generated by an association model.</span></span> <span data-ttu-id="e603a-124">これらの値は、重要度の計算と説明にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-124">These values are also used to calculate and describe their importance.</span></span>  
  
 <span data-ttu-id="e603a-125">**サポート**。</span><span class="sxs-lookup"><span data-stu-id="e603a-125">**Support**.</span></span> <span data-ttu-id="e603a-126">サポートは、このアイテムを含む入力データのケースまたは行の数を示します。</span><span class="sxs-lookup"><span data-stu-id="e603a-126">Support means the number of cases or rows of input data that have this item.</span></span> <span data-ttu-id="e603a-127">たとえば、アイテムセットにショッピングカートで見つかった2つのアイテムが含まれている場合、[**サポート**] 列の数値は、ソースデータでアイテムの組み合わせが何回発生したかを示します。</span><span class="sxs-lookup"><span data-stu-id="e603a-127">For example, if an itemset contains two items that are found in a shopping cart, the number in the **Support** column indicates how many times that combination of items occurred in the source data.</span></span>  
  
 <span data-ttu-id="e603a-128">**[サイズ]**。</span><span class="sxs-lookup"><span data-stu-id="e603a-128">**Size**.</span></span> <span data-ttu-id="e603a-129">アイテムセットのサイズを変更することで、アイテムセットの一覧の長さを制御できます。</span><span class="sxs-lookup"><span data-stu-id="e603a-129">By changing itemset size, you can control the length of the lists of itemsets.</span></span> <span data-ttu-id="e603a-130">一覧に単一の製品が表示されないようにするには、[アイテムセットの**最小サイズ**] オプションを2以上に変更します。</span><span class="sxs-lookup"><span data-stu-id="e603a-130">If you don't want to see single products in the list, change the option, **Minimum itemset size**, to 2 or more.</span></span>  <span data-ttu-id="e603a-131">アイテムセットの最小サイズを大きくして、表示するアイテムセットを制限すれば、より明確なパターンを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="e603a-131">Restricting the list by increasing the minimum size of itemsets lets you look for very specific patterns.</span></span> <span data-ttu-id="e603a-132">これは、膨大な量のデータを処理する場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e603a-132">This might be useful if you are working with a very large set of data.</span></span>  
  
 <span data-ttu-id="e603a-133">[**最小のサポート**] と [**最大行数**] の値を変更することで、タブに表示されるアイテムセットの数をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="e603a-133">You can filter the number of itemsets that are displayed in the tab by changing the **Minimum support** and **Maximum rows** values.</span></span> <span data-ttu-id="e603a-134">[**最小サポート**] の値を大きくすると、一覧に表示されるアイテムセットの数は少なくなりますが、アイテムセットは入力データ内のより一般的なものになります。</span><span class="sxs-lookup"><span data-stu-id="e603a-134">If you increase the **Minimum Support** value, the list will show fewer itemsets, but the itemsets will be the more common ones in the input data.</span></span> <span data-ttu-id="e603a-135">共通の問題が重要であるかどうかはもう1つの質問で、[**ルール**] タブを使用して調べることができます。</span><span class="sxs-lookup"><span data-stu-id="e603a-135">Whether common is the same as important is another question, which you can explore using the **Rules** tab.</span></span>  
  
 <span data-ttu-id="e603a-136">[**アイテムセット**] タブのサポート値またはその他のコントロールを変更しても、表示される項目のみが変更され、基になるモデルには影響しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e603a-136">Note that changing the support value or other controls on the **Itemsets** tab only changes the items that are displayed, and does not affect the underlying model.</span></span> <span data-ttu-id="e603a-137">生成するアイテムセットの数を減らすか、サイズを制限する場合は、[ `MINIMUM_SUPPORT` `MAXIMUM_SUPPORT` **アルゴリズムパラメーター** ] ダイアログボックスで使用できるパラメーターとを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e603a-137">If you want to generate fewer or more itemsets, or limit their size, you should use the parameters, `MINIMUM_SUPPORT` and `MAXIMUM_SUPPORT`, available in the **Algorithm Parameters** dialog box.</span></span>  
  
##### <a name="explore-the-itemsets-list"></a><span data-ttu-id="e603a-138">アイテムセットの一覧の調査</span><span class="sxs-lookup"><span data-stu-id="e603a-138">Explore the itemsets list</span></span>  
  
1.  <span data-ttu-id="e603a-139">[**サポート**] 列をクリックすると、サポートのレベルが最も高いものから順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="e603a-139">Click the **Support** column to sort by highest to lowest support.</span></span> <span data-ttu-id="e603a-140">これにより、顧客の購入頻度が最も高いものがわかります。</span><span class="sxs-lookup"><span data-stu-id="e603a-140">This will give you an idea of what customers are buying most often.</span></span>  
  
2.  <span data-ttu-id="e603a-141">目的の特定のアイテムセットに注目するには、[アイテムセットの**フィルター** ] ボックスにテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="e603a-141">To focus on a particular itemset of interest, out of the many thousand combinations possible, type some text in the **Filter Itemset** box.</span></span>  
  
     <span data-ttu-id="e603a-142">ここでは、「」と入力しました `Gloves` 。</span><span class="sxs-lookup"><span data-stu-id="e603a-142">Here we typed `Gloves`.</span></span> <span data-ttu-id="e603a-143">フィルターを適用すると、一覧が更新され、グローブを含むアイテムセットのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-143">When you apply the filter, the list is refreshed to show only itemsets containing gloves.</span></span> <span data-ttu-id="e603a-144">これにより、顧客がグローブとその他のアイテムを購入したトランザクションに注目することができます。</span><span class="sxs-lookup"><span data-stu-id="e603a-144">This lets you focus on the transactions where customers purchased gloves and some other item.</span></span>  
  
     <span data-ttu-id="e603a-145">**[アイテムセットのフィルター]** オプションでは、以前に使用したフィルターの一覧も表示されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-145">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
3.  <span data-ttu-id="e603a-146">[**最小のアイテム**セットのサイズ] の値を変更して、手袋のみを購入し、他のアイテムを含まない顧客を除外します。</span><span class="sxs-lookup"><span data-stu-id="e603a-146">Change the value of **Minimum itemset size** to filter out the customers who bought only gloves and no other items.</span></span>  
  
4.  <span data-ttu-id="e603a-147">属性の表示方法を制御するには、[**表示**] のドロップダウンリストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e603a-147">Click the dropdown list for the option **Show**, to control how the attributes are displayed:</span></span>  
  
    -   <span data-ttu-id="e603a-148">**[属性の名前と値を表示]**</span><span class="sxs-lookup"><span data-stu-id="e603a-148">**Show attribute name and value**</span></span>  
  
    -   <span data-ttu-id="e603a-149">**[属性値のみ表示]**</span><span class="sxs-lookup"><span data-stu-id="e603a-149">**Show attribute value only**</span></span>  
  
    -   <span data-ttu-id="e603a-150">**[属性名のみ表示]**</span><span class="sxs-lookup"><span data-stu-id="e603a-150">**Show attribute name only**</span></span>  
  
     <span data-ttu-id="e603a-151">名前がどのように変更されているかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e603a-151">Notice how the name changes.</span></span> <span data-ttu-id="e603a-152">複数の顧客が購入した製品の入れ子になったテーブルに基づいて作成されるマーケット バスケット モデルの場合、通常、属性名は製品名であり、一覧に製品が含まれていると "`Existing`" とマークされます (これは顧客がそのアイテムを購入したことを意味します)。</span><span class="sxs-lookup"><span data-stu-id="e603a-152">In the case of a market basket model, which is built on nested tables of products that were purchased by multiple customers, the attribute name is typically the product name, and the presence of the product in the list is marked as `Existing`, meaning that the customer did buy the item.</span></span>  
  
     <span data-ttu-id="e603a-153">"`Existing`" の反対は "`Missing`" で、データ マイニングで調査を行う際に非常に役立つ属性となります。</span><span class="sxs-lookup"><span data-stu-id="e603a-153">The opposite of `Existing` is `Missing`, which can be a very useful attribute to investigate in data mining.</span></span> <span data-ttu-id="e603a-154">たとえば、アイテム a + B が非常に人気であり、アイテム B を購入した顧客を検索する必要があるとします。これを行うには、予測クエリを使用して、一方のトランザクションだけを使用してトランザクションを取得し、その他の分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="e603a-154">For example, suppose the itemset A +B is so very popular that you wanted to find customers who purchased Item A but not item B. You could do this by using a prediction query and retrieving the transactions with one but not the other, and do some further analysis on those.</span></span> <span data-ttu-id="e603a-155">アソシエーションモデルに対する予測クエリの作成方法の詳細については、「SQL Server オンラインブックでの[アソシエーションモデルのクエリ例](data-mining/association-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e603a-155">For information about how to create prediction queries on association models, see [Association Model Query Examples](data-mining/association-model-query-examples.md) in SQL Server Books Online</span></span>  
  
5.  <span data-ttu-id="e603a-156">新しいフィルター条件を使用してアイテムセットの一覧を強制的に再表示するには、[**長い名前を表示**する] チェックボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="e603a-156">To force the list of itemsets to redisplay using your new filter criteria, you can select or clear the **Show long name** check box.</span></span>  
  
 [<span data-ttu-id="e603a-157">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="e603a-157">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a><span data-ttu-id="e603a-158">ロジック</span><span class="sxs-lookup"><span data-stu-id="e603a-158">Rules</span></span>  
 <span data-ttu-id="e603a-159">[**ルール**] タブには、アイテムセットとその相対値に関する情報が結合されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-159">The **Rules** tab combines information about the itemsets and their relative value.</span></span>  
  
 <span data-ttu-id="e603a-160">![アソシエーション モデルによって作成されたルールの一覧](media/dm13-association-rules.gif "アソシエーション モデルによって作成されたルールの一覧")</span><span class="sxs-lookup"><span data-stu-id="e603a-160">![List of rules created by an association model](media/dm13-association-rules.gif "List of rules created by an association model")</span></span>  
  
 <span data-ttu-id="e603a-161">*確率*は、対象となるアイテムの組み合わせを含むデータセット内のケースの割合を表します。</span><span class="sxs-lookup"><span data-stu-id="e603a-161">*Probability* represents the fraction of cases in the dataset that contain the targeted combination of items.</span></span> <span data-ttu-id="e603a-162">確率は、*信頼度*の統計的概念に似ており、ルールの結果が発生する可能性があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e603a-162">Probability is similar to the statistical concept of *confidence*, and gives you an indication of how likely the result of a rule is to occur.</span></span> <span data-ttu-id="e603a-163">このペインの [**最小確率**] の値を変更して、表示されるルールをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="e603a-163">You can change the value of **Minimum probability** in this pane to filter the rules that are displayed.</span></span>  
  
 <span data-ttu-id="e603a-164">最初に表示される**最小確率**の値は、モデルの作成時にアルゴリズムによって使用されたしきい値です。</span><span class="sxs-lookup"><span data-stu-id="e603a-164">The value for **Minimum probability** that you initially see is the threshold value that was used by the algorithm when building the model.</span></span> <span data-ttu-id="e603a-165">モデルが完成した後は、この値を小さくすることはできませんが、大きな確率の項目だけを表示するように増やすことはできます。</span><span class="sxs-lookup"><span data-stu-id="e603a-165">After the model is complete, you can't decrease this value, but you can increase it to show only the higher probability items.</span></span>  
  
 <span data-ttu-id="e603a-166">*重要度*は、ルールの有用性を測定するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e603a-166">*Importance* is designed to measure the usefulness of a rule.</span></span> <span data-ttu-id="e603a-167">ごく一般的なルールはいたるところで見られるため、情報の価値はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="e603a-167">A rule that is very common might be so ubiquitous that is has little information value.</span></span> <span data-ttu-id="e603a-168">重要度が高いほど、結果を予測する上で、そのルールの利用価値が高くなります。</span><span class="sxs-lookup"><span data-stu-id="e603a-168">The greater the importance, the more valuable the rule is for predicting the outcome.</span></span> <span data-ttu-id="e603a-169">[買い物かご分析 &#40;Table AnalysisTools For Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool では、重要度と品目の価格を組み合わせて、売上の面で最も重要なバンドルを特定できます。</span><span class="sxs-lookup"><span data-stu-id="e603a-169">In the [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool, importance can be combined with the price of items to determine the bundles that are potentially most valuable in terms of sales.</span></span>  
  
##### <a name="explore-the-rules-list"></a><span data-ttu-id="e603a-170">ルールの一覧の調査</span><span class="sxs-lookup"><span data-stu-id="e603a-170">Explore the rules list</span></span>  
  
1.  <span data-ttu-id="e603a-171">列見出し (**確率**、**重要度**、**ルール**) をクリックして、データがどのように変化するかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e603a-171">Try clicking the column headings - **Probability**, **Importance**, and **Rule** - to see how the data changes.</span></span>  
  
2.  <span data-ttu-id="e603a-172">[**ルールのフィルター** ] オプションを使用して、値を入力し、対象となるルールに注目します。</span><span class="sxs-lookup"><span data-stu-id="e603a-172">Use the **Filter Rule** option to type in values and focus on targeted rules.</span></span>  
  
     <span data-ttu-id="e603a-173">たとえば、顧客が手袋と共に購入される可能性があることを予測するすべてのルールを表示するには、テキストボックスに「グローブ」と入力し、ウィンドウを更新します。</span><span class="sxs-lookup"><span data-stu-id="e603a-173">For example, if you want to see all the rules that predict what customers are likely to purchase along with gloves, type "gloves" in the text box and refresh the pane.</span></span>  
  
     <span data-ttu-id="e603a-174">**[アイテムセットのフィルター]** オプションでは、以前に使用したフィルターの一覧も表示されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-174">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
3.  <span data-ttu-id="e603a-175">フィルター条件を使用してルールの一覧を強制的に再表示するには、[**長い名前を表示**する] チェックボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="e603a-175">To force the list of rules to redisplay using filter criteria, you can select or clear the **Show long name** check box.</span></span>  
  
4.  <span data-ttu-id="e603a-176">[**表示**] オプションを使用して、ルール名の表示方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="e603a-176">Use the option, **Show** to control the way that rule names are displayed.</span></span>  
  
5.  <span data-ttu-id="e603a-177">[**最大行数**] オプションの値を100に設定し、[ **Excel にコピー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e603a-177">Set the value for the **Maximum rows** option to 100, and then click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="e603a-178">この値を変更しても、モデル内のデータ量には影響しないことに注意してください。表示リストの行数を制御するだけです。</span><span class="sxs-lookup"><span data-stu-id="e603a-178">Note that changing this value doesn't have any effect on the amount of data in the model; it simply controls the number of rows in the display list.</span></span> <span data-ttu-id="e603a-179">このオプションは、非常に大規模なモデルを使用する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e603a-179">This option can be useful when working with very large models.</span></span>  
  
 [<span data-ttu-id="e603a-180">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="e603a-180">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="dependency-network"></a><a name="BKMK_Dependency"></a><span data-ttu-id="e603a-181">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="e603a-181">Dependency Network</span></span>  
 <span data-ttu-id="e603a-182">[**依存関係ネットワーク**] タブは、項目間の相関関係を視覚的にマップしたものです。</span><span class="sxs-lookup"><span data-stu-id="e603a-182">The **Dependency Network** tab is a visual map of the correlations among items.</span></span> <span data-ttu-id="e603a-183">グラフ内の各楕円 (*ノード*と呼ばれます) は、属性と値のペアを表します。たとえば、"Age = Existing" または "Age = 1-30" のようになります。</span><span class="sxs-lookup"><span data-stu-id="e603a-183">Each oval in the graph (referred to as a *node*) represents an attribute-value pair, such as "Vest = Existing" or "Age = 1-30".</span></span>  <span data-ttu-id="e603a-184">楕円 (*エッジ*と呼ばれます) を接続する線は、相関関係の種類を表します。</span><span class="sxs-lookup"><span data-stu-id="e603a-184">Each line connecting the ovals (referred to as an *edge*) represents a type of correlation.</span></span>  
  
 <span data-ttu-id="e603a-185">![アソシエーション モデルの依存関係ネットワーク グラフ](media/dm13-association-dependencynetwork.gif "アソシエーション モデルの依存関係ネットワーク グラフ")</span><span class="sxs-lookup"><span data-stu-id="e603a-185">![Dependency network graph for an association model](media/dm13-association-dependencynetwork.gif "Dependency network graph for an association model")</span></span>  
  
##### <a name="explore-the-dependency-network"></a><span data-ttu-id="e603a-186">依存関係ネットワークの調査</span><span class="sxs-lookup"><span data-stu-id="e603a-186">Explore the dependency network</span></span>  
  
1.  <span data-ttu-id="e603a-187">[**検索**] ボタンをクリックし、[**ノードの検索**] ダイアログボックスを使用して目的の項目を入力します。</span><span class="sxs-lookup"><span data-stu-id="e603a-187">Click the **Find** button and use the **Find Node** dialog box to type an item of interest.</span></span>  
  
     <span data-ttu-id="e603a-188">たとえば、「グローブ」と入力し、ウィンドウ内のグラフを最大化して、結果を簡単に確認できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e603a-188">For example, type "gloves" and then maximize the graph in the window so that you can easily see the results.</span></span>  
  
     <span data-ttu-id="e603a-189">そのアイテムを含むノードが強調表示されると同時に、ノードを指す矢印はアイテムを結ぶルールを表します。</span><span class="sxs-lookup"><span data-stu-id="e603a-189">The node that contains the item is highlighted, while the arrows pointing to the node represent a rule that connects the items.</span></span>  
  
     <span data-ttu-id="e603a-190">矢印の向きによって、ルールの方向が示されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-190">The direction of the arrow tells you the direction of the rule.</span></span> <span data-ttu-id="e603a-191">たとえば、手袋を購入した人が権利を購入する可能性がある場合、矢印は "手袋" ノードから始まり、"権利がある" ノードで終了します。</span><span class="sxs-lookup"><span data-stu-id="e603a-191">For example, if someone who buys gloves is also likely to buy a vest, the arrow will start from the "glove" node and terminate on the "vest" node.</span></span>  
  
     <span data-ttu-id="e603a-192">このルールに関する追加の統計情報を取得するには、[**ルール**] タブをクリックし、"> 既存のもの" という説明が付いたルールを探します。</span><span class="sxs-lookup"><span data-stu-id="e603a-192">To get additional statistics about this rule, you can click the **Rules** tab and look for a rule with the description, "Glove - Existing" -> "Vest - Existing.")</span></span>  
  
2.  <span data-ttu-id="e603a-193">ビューアーの左側にあるスライダーをクリックしてドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e603a-193">Click and drag the slider at the left of the viewer.</span></span>  
  
     <span data-ttu-id="e603a-194">このスライダーは、ルールの確率に対するフィルターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="e603a-194">The slider acts as a filter on the probability of the rules.</span></span> <span data-ttu-id="e603a-195">スライダーを小さく設定すると、強力なルールのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-195">Lowering the slider shows only the strongest rules.</span></span>  
  
3.  <span data-ttu-id="e603a-196">[ **Excel にコピー** ] をクリックして、現在のウィンドウのスナップショットを excel にコピーします。</span><span class="sxs-lookup"><span data-stu-id="e603a-196">Click **Copy to Excel** to copy a snapshot of the current window to Excel.</span></span>  
  
     <span data-ttu-id="e603a-197">Excel にコピーしたグラフを操作することはできません。対話型のネットワークグラフが必要な場合は、「 [Visio でのデータマイニングモデルの表示」 &#40;データマイニングアドイン&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e603a-197">You won't be able to work with the graph that you copy into Excel; if you need an interactive network graph, use the [Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).</span></span>  
  
 [<span data-ttu-id="e603a-198">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="e603a-198">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a><span data-ttu-id="e603a-199">アソシエーションモデルの詳細</span><span class="sxs-lookup"><span data-stu-id="e603a-199">More about Association Models</span></span>  
 <span data-ttu-id="e603a-200">**参照**機能を使用して、Microsoft アソシエーションルールアルゴリズムを使用して作成された任意のモデルを開いて探索することができます。</span><span class="sxs-lookup"><span data-stu-id="e603a-200">You can use the **Browse** feature to open and explore any model that was created using the Microsoft Association Rules algorithm.</span></span> <span data-ttu-id="e603a-201">これには、[買い物かご分析 &#40;Table AnalysisTools For Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)ツール、**テーブル分析ツール**リボン、またはで作成されたモデルが含まれ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e603a-201">This includes models built using the [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool, in the **Table Analysis Tools** ribbon, or in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e603a-202">買い物かご分析ツールを使用してアソシエーション ルール モデルを作成した場合、詳細設定オプションの多くは自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="e603a-202">If you create an association rules model using the Shopping Basket Analysis tool, many of the advanced options are configured automatically for you.</span></span>  
  
 <span data-ttu-id="e603a-203">高度なパラメーターを設定したり、最小の確率とサポートを変更したりするには、[excel [&#41;用のデータマイニングクライアント &#40;](associate-wizard-data-mining-client-for-excel.md) ] ウィザードを使用するか、または [ [&#40;構造へのモデルの追加] [Excel 用データマイニングアドイン&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)モデリング] オプションを使用して独自のモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e603a-203">If you want to set advanced parameters or alter minimum probability and support, use the [Associate Wizard &#40;Data Mining Client for Excel&#41;](associate-wizard-data-mining-client-for-excel.md) wizard, or build your own model using the [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) modeling option.</span></span>  
  
-   <span data-ttu-id="e603a-204">**アイテムセット:** モデルを作成するときに、MINIMUM_PROBABILITY パラメーターに値を割り当てることによって生成されるアイテムセットの数を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="e603a-204">**Itemsets:** When you create the model, you can also control the number of itemsets that are generated by assigning a value to the MINIMUM_PROBABILITY parameter.</span></span> <span data-ttu-id="e603a-205">このパラメーターは、[アルゴリズム パラメーター] ダイアログ ボックスで設定できます。</span><span class="sxs-lookup"><span data-stu-id="e603a-205">This parameter is available in the Algorithm Parameters dialog box.</span></span>  
  
-   <span data-ttu-id="e603a-206">**ルール:**[!INCLUDE[msCoName](../includes/msconame-md.md)]アソシエーションルールアルゴリズムでは、確率値を使用して、生成されるルールの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="e603a-206">**Rules:** The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm uses probability values to restrict the number of rules that are generated.</span></span> <span data-ttu-id="e603a-207">ルールの数を制御するには、`MINIMUM_PROBABILITY` パラメーターまたは `MINIMUM _IMPORTANCE` パラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="e603a-207">You can control the number of rules by setting the parameters, `MINIMUM_PROBABILITY` or `MINIMUM _IMPORTANCE`.</span></span>  
  
 <span data-ttu-id="e603a-208">詳細なパラメーターの構成の詳細については、「データマイニング[アルゴリズム &#40;SQL Server データマイニングアドイン&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e603a-208">For more information about configuring advanced parameters, see [Data Mining Algorithms &#40;SQL Server Data Mining Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e603a-209">参照</span><span class="sxs-lookup"><span data-stu-id="e603a-209">See Also</span></span>  
 [<span data-ttu-id="e603a-210">Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;</span><span class="sxs-lookup"><span data-stu-id="e603a-210">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
