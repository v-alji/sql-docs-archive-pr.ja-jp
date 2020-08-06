---
title: 関連付けウィザード (Excel 用のデータマイニングクライアント) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nested tables, in association models
- association [data mining]
ms.assetid: 4db6462f-93c7-443f-8ff7-39474dc7029e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 73ce4bbedb710de1ded149a12f6f9b83f0b92a11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633635"
---
# <a name="associate-wizard-data-mining-client-for-excel"></a><span data-ttu-id="6df77-102">アソシエーション ウィザード (Excel 用データ マイニング クライアント)</span><span class="sxs-lookup"><span data-stu-id="6df77-102">Associate Wizard (Data Mining Client for Excel)</span></span>
  <span data-ttu-id="6df77-103">![[データ マイニング] リボンの関連付けウィザード](media/dmc-associate.gif "[データ マイニング] リボンの関連付けウィザード")</span><span class="sxs-lookup"><span data-stu-id="6df77-103">![Associate wizard in Data Mining ribbon](media/dmc-associate.gif "Associate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="6df77-104">関連付けウィザードでは、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション ルール アルゴリズムを使用してデータ マイニング モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6df77-104">The Associate wizard helps you create a data mining model using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm.</span></span> <span data-ttu-id="6df77-105">このようなマイニングモデルは、*推奨システム*を作成する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="6df77-105">Such mining models are particularly useful for creating *recommendation systems*.</span></span>  
  
 <span data-ttu-id="6df77-106">そのしくみは、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション ルール アルゴリズムで、トランザクションまたはイベントで構成されるデータセットをスキャンし、同時に出現する頻度の高い組み合わせを探します。</span><span class="sxs-lookup"><span data-stu-id="6df77-106">How it works is that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm scans a dataset comprised of transactions or events, and finds the combinations that frequently appear together.</span></span> <span data-ttu-id="6df77-107">数千の組み合わせがあり得ますが、アルゴリズムをカスタマイズして探す組み合わせの数を増減して、可能性の高い組み合わせだけを保持することができます。</span><span class="sxs-lookup"><span data-stu-id="6df77-107">There can be many thousand combinations, but the algorithm can be customized to find more or fewer, and to retain only the most probable combinations.</span></span>  
  
 <span data-ttu-id="6df77-108">アソシエーション分析は多くの問題に適用できます。</span><span class="sxs-lookup"><span data-stu-id="6df77-108">You can apply association analysis to many problems.</span></span> <span data-ttu-id="6df77-109">この方法の最も一般的な適用例は、同時に購入されることの多い製品を見つけるマーケット バスケット分析です。</span><span class="sxs-lookup"><span data-stu-id="6df77-109">The most popular application of this method is market basket analysis, which finds individual products that are often purchased together.</span></span> <span data-ttu-id="6df77-110">その情報を使用すると、顧客が既に購入したアイテムに基づいて、顧客に製品を推奨できます。</span><span class="sxs-lookup"><span data-stu-id="6df77-110">You can then use that information to recommend products to customers based on items they have already bought.</span></span>  
  
## <a name="using-the-associate-wizard"></a><span data-ttu-id="6df77-111">関連付けウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="6df77-111">Using the Associate Wizard</span></span>  
  
1.  <span data-ttu-id="6df77-112">[**データマイニング**] リボンで、[**関連付け**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6df77-112">In the **Data Mining** ribbon, click **Associate**.</span></span>  
  
2.  <span data-ttu-id="6df77-113">[**ソースデータの選択**] ページで、Excel テーブルまたはデータ範囲を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6df77-113">On the **Select Source Data** page, choose an Excel table or data range, and click **Next**.</span></span>  
  
     <span data-ttu-id="6df77-114">サンプル データ ブックの [関連付け] タブには、各トランザクションに複数の製品がある場合や分析する顧客ごとに複数の購入レコードがある場合などに、トランザクション データが通常どのように配置されるかを示す例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6df77-114">The sample data workbook contains an example, in the Associate tab, of how transaction data is typically arranged if, for example, you have multiple products in each transaction or multiple purchasing records per customer that you want to analyze.</span></span>  
  
     <span data-ttu-id="6df77-115">関連付けウィザードを使用して外部データを使用してアソシエーションモデルを作成する場合は、最初にデータを Excel に追加し、データを*フラット*化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df77-115">If you want to use external data to build an association model using the Associate wizard, you must add the data to Excel first, and *flatten* the data.</span></span> <span data-ttu-id="6df77-116">アソシエーションモデリング用のデータの準備の詳細については、SQL Server オンラインブックの「[入れ子になったテーブル &#40;Analysis Services データマイニング&#41;](data-mining/nested-tables-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df77-116">For more information about preparing data for association modeling, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md), in SQL Server Books Online.</span></span>  
  
3.  <span data-ttu-id="6df77-117">[**関連付け**] ページで、トランザクションを識別する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="6df77-117">On the **Association** page, choose the column that identifies the transaction.</span></span>  
  
     <span data-ttu-id="6df77-118">マーケット バスケット モデルの場合、この識別子は、モデル化する単位を表します。</span><span class="sxs-lookup"><span data-stu-id="6df77-118">For market basket models, this identifier represents the unit you want to model.</span></span> <span data-ttu-id="6df77-119">個々の顧客が一定期間内に購入したアイテムを分析する場合や、複数の顧客に関連する多くのトランザクションを分析する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6df77-119">Do you want to analyze items that individual customers have purchased over time, or do you want to analyze many transactions involving multiple customers?</span></span> <span data-ttu-id="6df77-120">前者の場合には、顧客 ID を選択し、後者の場合には、購買発注 ID または他のトランザクション ID を選択します。</span><span class="sxs-lookup"><span data-stu-id="6df77-120">In the first case, you would choose the customer ID; in the latter you would choose the purchase order or other transaction ID.</span></span>  
  
4.  <span data-ttu-id="6df77-121">[**項目**] で、アソシエーションを検索する必要がある項目が含まれている列を選択します。</span><span class="sxs-lookup"><span data-stu-id="6df77-121">For **Item**, select the column that contains the things among which you need to find associations.</span></span>  
  
     <span data-ttu-id="6df77-122">たとえば、マーケット バスケット モデルでは、製品フィールドを選択し、同時に購入されることの多い製品を分析します。</span><span class="sxs-lookup"><span data-stu-id="6df77-122">For example, in a market basket model, you would choose a products field, to analyze which products are often purchased together.</span></span> <span data-ttu-id="6df77-123">個別の製品が多すぎて効果的に相互に関連付けることができない場合は、製品カテゴリ フィールドまたは製品サブカテゴリ フィールドを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6df77-123">If there are too many individual products to correlate them effectively, you might choose a product category or subcategory field.</span></span>  
  
5.  <span data-ttu-id="6df77-124">[**しきい**値] では、モデルの出力を制御または影響を与える値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="6df77-124">In **Thresholds**, you can set values that control or affect the output of the model:</span></span>  
  
    -   <span data-ttu-id="6df77-125">**最小のサポート。**</span><span class="sxs-lookup"><span data-stu-id="6df77-125">**Minimum support.**</span></span> <span data-ttu-id="6df77-126">重要と見なす条件としてアイテムのグループの出現回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6df77-126">Specifies how many times a group of items must appear to be considered important.</span></span> <span data-ttu-id="6df77-127">このアルゴリズムでは、この条件を満たしていないアイテムの組み合わせが無視されます。</span><span class="sxs-lookup"><span data-stu-id="6df77-127">The algorithm will ignore any item combinations that do not meet this criterion.</span></span> <span data-ttu-id="6df77-128">たとえば、アイテムが全体で 10 回以上同時に出現するアイテムセットのみを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="6df77-128">For example, you might want to see only itemsets where the items appeared together at least 10 times overall.</span></span>  
  
    -   <span data-ttu-id="6df77-129">**ルールの最小確率**。</span><span class="sxs-lookup"><span data-stu-id="6df77-129">**Minimum rule probability**.</span></span> <span data-ttu-id="6df77-130">ルールを保存するのに必要な最小の確率値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6df77-130">Specifies the minimum probability value required for a rule to be saved.</span></span> <span data-ttu-id="6df77-131">すべての組み合わせを見つけるためにデータ セット全体が分析され、確率が計算されます。</span><span class="sxs-lookup"><span data-stu-id="6df77-131">The entire data set is analyzed to find all combinations, and then probability is calculated.</span></span> <span data-ttu-id="6df77-132">しきい値が低い場合は、緩い相関関係にあるアイテムのみが関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="6df77-132">If the threshold is low, the wizard may associate items that are only loosely correlated.</span></span> <span data-ttu-id="6df77-133">しきい値が高すぎると、サポートするデータが十分ではないために、いくつかのアソシエーションが除外される場合があります。</span><span class="sxs-lookup"><span data-stu-id="6df77-133">If the threshold is too high, some associations may be omitted because they do not have enough supporting data.</span></span>  
  
     <span data-ttu-id="6df77-134">一般に、これらの値を変更すると、次のような効果があります。</span><span class="sxs-lookup"><span data-stu-id="6df77-134">In general, changing these values has the following effects:</span></span>  
  
    -   <span data-ttu-id="6df77-135">サポートの値を小さくすると、検出される組み合わせの数が増加します。</span><span class="sxs-lookup"><span data-stu-id="6df77-135">As you lower the value for support, you increase the number of combinations that are found.</span></span>  
  
    -   <span data-ttu-id="6df77-136">最大のサポートを減らすと、頻繁に出現するためにほとんど意味を持たないアイテムが除外されます。</span><span class="sxs-lookup"><span data-stu-id="6df77-136">As you decrease the maximum support, you filter out items that occur so often that they have little meaning.</span></span>  
  
    -   <span data-ttu-id="6df77-137">ルールの確率を小さくすると、データ セット全体のコンテキストで重要と見なされる組み合わせのしきい値が低くなります。</span><span class="sxs-lookup"><span data-stu-id="6df77-137">As you lower the probability of a rule, you lower the requirements that a combination must meet to be considered important in the context of the total data set.</span></span>  
  
     <span data-ttu-id="6df77-138">**ヒント:** サポートと確率の組み合わせを変えて、複数のマイニングモデルを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6df77-138">**Tip:** It is a good idea to create multiple mining models using different combinations of support and probability.</span></span> <span data-ttu-id="6df77-139">各モデルで使用した設定を追跡するには、Excel 用のデータマイニングクライアントで使用できる**ドキュメントモデル**ウィザードを使用し、[**詳細**レポート] オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6df77-139">To track which settings you used for each model, you can use the **Document Model** wizard, available in the Data Mining Client for Excel, and use the **Detailed** report option.</span></span> <span data-ttu-id="6df77-140">詳細については、「 [Excel 用データマイニングアドイン &#40;マイニングモデルを文書化する&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df77-140">For more information, see [Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).</span></span>  
  
6.  <span data-ttu-id="6df77-141">必要に応じて、[**パラメーター** ] をクリックして、アルゴリズムパラメーターを変更し、マイニングモデルの動作をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="6df77-141">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the mining model.</span></span>  
  
     <span data-ttu-id="6df77-142">[アルゴリズム パラメーター] ダイアログ ボックスには、ウィザードで設定したすべてのパラメーターと、MAXIMUM_SUPPORT などの使用頻度の低いいくつかのパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6df77-142">The Algorithm Parameters dialog box includes all of the parameters you set in the wizard, plus a few that are less commonly used, such as MAXIMUM_SUPPORT.</span></span> <span data-ttu-id="6df77-143">これらのパラメーターの使用方法の詳細については、「 [Microsoft アソシエーションアルゴリズムテクニカルリファレンス](data-mining/microsoft-association-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df77-143">For information about how to use these parameters, see [Microsoft Association Algorithm Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
7.  <span data-ttu-id="6df77-144">[**完了**] ページで、データセットとモデルの一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6df77-144">On the **Finish** page, type a unique name for the data set and the model.</span></span>  
  
8.  <span data-ttu-id="6df77-145">[**オプション**] では、完了後にモデルを操作する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="6df77-145">In **Options**, you define how you want to work with the model after it is completed:</span></span>  
  
    -   <span data-ttu-id="6df77-146">[**参照**]。</span><span class="sxs-lookup"><span data-stu-id="6df77-146">**Browse**.</span></span>  <span data-ttu-id="6df77-147">モデルの準備ができると、ルール、アイテムセット、およびアソシエーションを示す依存関係ネットワーク グラフを表示するウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="6df77-147">When the model is ready, the wizard opens a window that displays the rules, the itemsets, and a dependency network graph that depicts associations.</span></span>  
  
         <span data-ttu-id="6df77-148">アソシエーションモデルビューアーでデータを解釈する方法の詳細については、「[アソシエーションルールモデルの参照](browsing-an-association-rules-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df77-148">For more information about how to interpret the data in the association model viewer, see [Browsing an Association Rules Model](browsing-an-association-rules-model.md).</span></span>  
  
    -   <span data-ttu-id="6df77-149">**ドリルスルーを有効に**します。</span><span class="sxs-lookup"><span data-stu-id="6df77-149">**Enable drillthrough**.</span></span> <span data-ttu-id="6df77-150">このチェック ボックスをオンにすると、モデルを通じて基になるデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6df77-150">Select this option to gain access to the underlying data, via the model.</span></span>  
  
         <span data-ttu-id="6df77-151">ドリルスルーは、特定のアイテムセットをクリックしてソース データを表示する場合などに便利です。</span><span class="sxs-lookup"><span data-stu-id="6df77-151">Drillthrough is useful, for example, if you want to click on a particular itemset and see the source data.</span></span>  
  
    -   <span data-ttu-id="6df77-152">**一時的なモデルを使用**します。</span><span class="sxs-lookup"><span data-stu-id="6df77-152">**Use temporary model**.</span></span> <span data-ttu-id="6df77-153">モデルがサーバーに保存されないようにする場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6df77-153">Select this option if you don't want the model saved on the server.</span></span> <span data-ttu-id="6df77-154">一時的なモデルは、Excel の終了時に削除されます。</span><span class="sxs-lookup"><span data-stu-id="6df77-154">Temporary models are deleted when you close Excel.</span></span>  
  
9. <span data-ttu-id="6df77-155">このウィザードは、すべての可能な組み合わせを分析し、アイテムセットとルールを含むレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="6df77-155">The wizard analyzes all possible combinations and creates a report that contains the itemsets and rules.</span></span>  
  
## <a name="more-about-association-models"></a><span data-ttu-id="6df77-156">アソシエーション モデルの詳細</span><span class="sxs-lookup"><span data-stu-id="6df77-156">More About Association Models</span></span>  
 <span data-ttu-id="6df77-157">[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション ルール アルゴリズムは、トレーニング データを調べて、トランザクション内で一緒に出現するアイテムを検索します。</span><span class="sxs-lookup"><span data-stu-id="6df77-157">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm examines the training data to find items that appear together in a transaction.</span></span> <span data-ttu-id="6df77-158">アイテムの各*グループは、アイテムセット*を構成します。</span><span class="sxs-lookup"><span data-stu-id="6df77-158">Each group of items constitutes an *itemset*.</span></span> <span data-ttu-id="6df77-159">次に、アルゴリズムは各アイテムセットの出現回数をカウントし、すべてのトランザクション間での各アイテムセットの相対的な重要度を計算します。</span><span class="sxs-lookup"><span data-stu-id="6df77-159">The algorithm then counts the number of times each itemset appears and calculates the relative importance of each itemset across all transactions.</span></span>  
  
 <span data-ttu-id="6df77-160">アルゴリズムは、アイテムセットに関するこの情報を使用して、アソシエーションの予測や提案に使用できるルールを生成します。</span><span class="sxs-lookup"><span data-stu-id="6df77-160">The algorithm uses this information about itemsets to generate rules that can be used to predict associations or make recommendations.</span></span> <span data-ttu-id="6df77-161">たとえば、"ユーザーが Author 1 の本および Author 2 の本を購入した場合、Author 3 の本も購入する可能性がある" というルールを生成します。</span><span class="sxs-lookup"><span data-stu-id="6df77-161">For example, a rule could be "if the user purchased a book by Author 1 and a book by Author 2, then it is likely that the user will also purchase a book by Author 3".</span></span> <span data-ttu-id="6df77-162">それぞれの提案に対して、アソシエーションの強さに基づいて確率が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6df77-162">Each recommendation is assigned a probability, based on the strength of the associations.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="6df77-163">必要条件</span><span class="sxs-lookup"><span data-stu-id="6df77-163">Requirements</span></span>  
 <span data-ttu-id="6df77-164">関連付けウィザードを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df77-164">To use the Associate wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="6df77-165">ソース データをトランザクション テーブルとして編成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df77-165">Your source data must be organized as a transaction table.</span></span> <span data-ttu-id="6df77-166">ソース データは、トランザクション識別子を含む列を 1 つ含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df77-166">The source data must contain one column that contains the transaction identifier.</span></span> <span data-ttu-id="6df77-167">この列は、アイテムの各グループを識別します。</span><span class="sxs-lookup"><span data-stu-id="6df77-167">This column identifies each group of items.</span></span> <span data-ttu-id="6df77-168">このトランザクション列は、2 番目のアイテム ID の列と 1 対他の関係にする必要があります。アイテム ID の列には、グループ内の個別のアイテムの名前または ID 番号が格納されています。</span><span class="sxs-lookup"><span data-stu-id="6df77-168">That transaction column must be in a one-to-many relationship with a second column, the item ID, which stores names or ID numbers for the individual items in the group.</span></span>  
  
 <span data-ttu-id="6df77-169">概念上の理解を簡単にするために、ショッピング カートの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="6df77-169">Conceptually, this might be easiest to understand by recalling the shopping cart example.</span></span> <span data-ttu-id="6df77-170">ショッピング カートに ID が割り当てられている場合は、ショッピング カート ID がトランザクションの識別子として機能します。</span><span class="sxs-lookup"><span data-stu-id="6df77-170">If the shopping cart is assigned an ID, the shopping cart ID serves as the identifier for the transaction.</span></span> <span data-ttu-id="6df77-171">ショッピング カート内の各アイテム (ジャガイモや牛乳など) は、そのトランザクションのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="6df77-171">Each item in the shopping cart, such as potatoes or milk, is a member of that transaction.</span></span> <span data-ttu-id="6df77-172">関連付けアルゴリズムは、トランザクション全体でアイテムを追跡して、1 つのトランザクションにジャガイモおよびミルクが出現する回数を判断するなどの作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6df77-172">The Associate algorithm can track items across transactions: for example, to determine how many times potatoes and milk appear within any single transaction.</span></span>  
  
 <span data-ttu-id="6df77-173">ソース データは、トランザクション識別子列によって並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df77-173">Your source data must be sorted by the transaction identifier column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df77-174">参照</span><span class="sxs-lookup"><span data-stu-id="6df77-174">See Also</span></span>  
 <span data-ttu-id="6df77-175">[データマイニングモデルの作成](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="6df77-175">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="6df77-176">[アソシエーションルールモデルの参照](browsing-an-association-rules-model.md) </span><span class="sxs-lookup"><span data-stu-id="6df77-176">[Browsing an Association Rules Model](browsing-an-association-rules-model.md) </span></span>  
 <span data-ttu-id="6df77-177">[買い物かご分析 &#40;テーブル AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="6df77-177">[Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) </span></span>  
 [<span data-ttu-id="6df77-178">依存関係ネットワークダイアグラムのチュートリアル &#40;データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="6df77-178">Dependency Network Diagram Walkthrough &#40;Data Mining Add-ins&#41;</span></span>](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
  