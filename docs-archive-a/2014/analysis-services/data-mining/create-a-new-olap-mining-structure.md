---
title: 新しい OLAP マイニング構造を作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], OLAP
- mining structures [Analysis Services], creating
- OLAP [Analysis Services], mining models
ms.assetid: 368f4273-a016-4748-bcb6-505a3e745af3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2851fe6180254b129471c442297c419fd594e123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711146"
---
# <a name="create-a-new-olap-mining-structure"></a><span data-ttu-id="e1463-102">新規の OLAP マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="e1463-102">Create a New OLAP Mining Structure</span></span>
  <span data-ttu-id="e1463-103">のデータマイニングウィザードを使用し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] て、多次元モデルのデータを使用するマイニング構造を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e1463-103">You can use the Data Mining Wizard in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create a mining structure that uses data from a multidimensional model.</span></span> <span data-ttu-id="e1463-104">OLAP キューブに基づくマイニング モデルでは、ファクト テーブルの列と値、ディメンション、およびメジャー グループを分析の属性として使用できます。</span><span class="sxs-lookup"><span data-stu-id="e1463-104">Mining models that are based on OLAP cubes can use the column and values in fact tables, dimensions, and measure groups as attributes for analysis.</span></span>  
  
### <a name="to-create-a-new-olap-mining-structure"></a><span data-ttu-id="e1463-105">新規の OLAP マイニング構造を作成するには</span><span class="sxs-lookup"><span data-stu-id="e1463-105">To create a new OLAP mining structure</span></span>  
  
1.  <span data-ttu-id="e1463-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、 **プロジェクトの** [マイニング構造] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] フォルダーを右クリックし、 **[新しいマイニング構造]** をクリックして、データ マイニング ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="e1463-106">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then click **New Mining Structure** to open the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="e1463-107">**[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="e1463-108">**[定義方法の選択]** ページで、 **[既存のキューブを使用する]** を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-108">On the **Select the Definition Method** page, select **From existing cube**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="e1463-109">[サポートされているデータ マイニング アルゴリズムの一覧を取得できません] というエラーが表示される場合は、 **[プロジェクトのプロパティ]** ダイアログ ボックスを開き、多次元モデルをサポートする Analysis Services インスタンスの名前を指定したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e1463-109">If you get an error with the message, Unable to retrieve a list of supported data mining algorithms, open the **Project Properties** dialog box and verify that you have specified the name of an Analysis Services instance that supports multidimensional models.</span></span> <span data-ttu-id="e1463-110">テーブル モデリングをサポートする [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスにマイニング モデルを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="e1463-110">You cannot create mining models on an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that supports tabular modeling.</span></span>  
  
4.  <span data-ttu-id="e1463-111">**[データ マイニング構造の作成]** ページで、マイニング構造のみを作成するか、マイニング構造および関連するマイニング モデルを 1 つ作成するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="e1463-111">On the **Create the Data Mining Structure** page, decide whether you will create a mining structure only, or a mining structure plus one related mining model.</span></span> <span data-ttu-id="e1463-112">一般には、必要な列を含めるよう求めるプロンプトが表示されるように、マイニング モデルを同時に作成する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="e1463-112">Generally it is easier to create a mining model at the same time, so that you can be prompted to include necessary columns.</span></span>  
  
     <span data-ttu-id="e1463-113">マイニング モデルを作成する場合は、使用するデータ マイニング アルゴリズムを選択して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-113">If you will create a mining model, select the data mining algorithm that you want to use, and then click **Next**.</span></span> <span data-ttu-id="e1463-114">アルゴリズムの選択方法の詳細については、「[データ マイニング アルゴリズム (Analysis Services - データ マイニング)](data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1463-114">For more information about how to choose an algorithm, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
5.  <span data-ttu-id="e1463-115">**[ソース キューブ ディメンションの選択]** ページの **[ソース キューブ ディメンションの選択]** で、ケース データの大半を含むディメンションを探します。</span><span class="sxs-lookup"><span data-stu-id="e1463-115">On the **Select the Source Cube Dimension** page, under **Select a Source Cube Dimension**, locate the dimension that contains the majority of your case data.</span></span>  
  
     <span data-ttu-id="e1463-116">たとえば、顧客グループを識別しようとしている場合は、Customer ディメンションを選択できます。複数の取引の購買を分析しようとしている場合は、Internet Sales Order Details ディメンションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="e1463-116">For example, if you are trying to identify customer groupings, you might choose the Customer dimension; if you are trying to analyze purchases across transactions, you might choose the Internet Sales Order Details dimension.</span></span> <span data-ttu-id="e1463-117">このディメンションのデータのみ使用するように制限はされませんが、分析で使用する重要属性を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1463-117">You are not restricted to using only the data in this dimension, but it should contain important attributes to use in analysis.</span></span>  
  
     <span data-ttu-id="e1463-118">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="e1463-119">**[ケース キーの選択]** ページの **[属性]** で、マイニング構造のキーにする属性を選択して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-119">On the **Select the Case Key** page, under **Attributes**, select the attribute that will be the key of the mining structure, and then click **Next**.</span></span>  
  
     <span data-ttu-id="e1463-120">通常、マイニング構造のキーとして使用する属性は、ディメンションのキーにもなり、事前に選択されます。</span><span class="sxs-lookup"><span data-stu-id="e1463-120">Typically the attribute that you use as key for the mining structure is also a key for the dimension and will be pre-selected.</span></span>  
  
7.  <span data-ttu-id="e1463-121">**[ケース レベル列の選択]** ページの **[関連する属性およびメジャー]** で、マイニング構造にケース データとして追加する値が格納された属性とメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-121">On the **Select Case Level Columns** page, under **Related Attributes and Measures**, select the attributes and measures that contain values you want to add to the mining structure as case data.</span></span> <span data-ttu-id="e1463-122">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-122">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="e1463-123">**[マイニング モデル列の使用法の指定]** ページの **[マイニング モデル構造]** で、最初に予測可能列を設定してから、入力として使用する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-123">On the **Specify Mining Model Column Usage** page, under **Mining model structure**, first set the predictable column, and then choose columns to use as inputs.</span></span>  
  
    -   <span data-ttu-id="e1463-124">一番左の列のチェック ボックスをオンにして、データをマイニング構造に含めます。</span><span class="sxs-lookup"><span data-stu-id="e1463-124">Select the checkbox in the leftmost column to include the data in the mining structure.</span></span> <span data-ttu-id="e1463-125">参照に使用する構造に列を含めることができますが、分析に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e1463-125">You can include columns in the structure that you will use for reference, but not use them for analysis.</span></span>  
  
    -   <span data-ttu-id="e1463-126">**[入力]** 列のチェック ボックスをオンにして、分析で属性を変数として使用します。</span><span class="sxs-lookup"><span data-stu-id="e1463-126">Select the checkbox in the **Input** column to use the attribute as a variable in analysis.</span></span>  
  
    -   <span data-ttu-id="e1463-127">予測可能な属性についてのみ、 **[予測]** 列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e1463-127">Select the checkbox in the **Predict** column only for predictable attributes.</span></span>  
  
     <span data-ttu-id="e1463-128">キーとして指定した列を入力または予測に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e1463-128">Note that columns you have designated as keys cannot be used for input or prediction.</span></span>  
  
     <span data-ttu-id="e1463-129">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-129">Click **Next**.</span></span>  
  
9. <span data-ttu-id="e1463-130">**[マイニング モデル列の使用法の指定]** ページの **[入れ子になっているテーブルの追加]** および **[入れ子になったテーブル]** を使用して、入れ子になったテーブルをマイニング構造に対して追加または削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="e1463-130">On the **Specify Mining Model Column Usage** page, you can also add and remove nested tables to the mining structure, using **Add Nested Tables** and **Nested Tables**.</span></span>  
  
     <span data-ttu-id="e1463-131">OLAP マイニング モデルでは、入れ子になったテーブルとは、ケース属性を表すディメンションとの間に一対多リレーションシップがあるキューブ内のデータの別のセットです。</span><span class="sxs-lookup"><span data-stu-id="e1463-131">In an OLAP mining model, a nested table is another set of data within the cube that has a one-to-many relationship with the dimension that represents the case attributes.</span></span> <span data-ttu-id="e1463-132">したがって、ダイアログ ボックスが開いたときに、ケース テーブルとして選択したディメンションに既に関連しているメジャー グループが事前に選択されています。</span><span class="sxs-lookup"><span data-stu-id="e1463-132">Therefore, when the dialog box opens, it pre-selects measure groups that are already related to the dimension you selected as the case table.</span></span> <span data-ttu-id="e1463-133">この時点で、分析に役立つ追加情報を格納している別のディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-133">At this point, you would choose a different dimension that contains additional information useful for analysis.</span></span>  
  
     <span data-ttu-id="e1463-134">たとえば、顧客を分析している場合は、[Customer] ディメンションをケース テーブルとして使用します。</span><span class="sxs-lookup"><span data-stu-id="e1463-134">For example, if you are analyzing customers, you would use the [Customer] dimension as the case table.</span></span> <span data-ttu-id="e1463-135">入れ子になったテーブルでは、購入を行うときに顧客が示した理由を追加できます。これは [Sales Reason] ディメンションに含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1463-135">For the nested table, you might add the reason customers cited when making a purchase, which is included in the [Sales Reason] dimension.</span></span>  
  
     <span data-ttu-id="e1463-136">入れ子になったデータを追加する場合は、次の 2 つの列を追加で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1463-136">If you add nested data, you must specify two additional columns:</span></span>  
  
    -   <span data-ttu-id="e1463-137">入れ子になったテーブルのキー: これは、 **[入れ子になったテーブル キーの選択]** ページで事前に選択されています。</span><span class="sxs-lookup"><span data-stu-id="e1463-137">The key of the nested table: This should be pre-selected on the page, **Select Nested Table Key**.</span></span>  
  
    -   <span data-ttu-id="e1463-138">分析に使用する属性: **[入れ子になったテーブル列の選択]** ページでは、入れ子になったテーブルの選択でメジャーと属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1463-138">The attributes or attributes to use for analysis: The page, **Select Nested Table Columns**, provides a list of measures and attributes in the nested table selection.</span></span>  
  
        -   <span data-ttu-id="e1463-139">モデルに含める属性ごとに、左の列のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e1463-139">For each attribute that you include in the model, check the box in the left column.</span></span>  
  
        -   <span data-ttu-id="e1463-140">属性を分析にのみ使用する場合は、 **[入力]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="e1463-140">If you want to use the attribute for analysis only, check **Input**.</span></span>  
  
        -   <span data-ttu-id="e1463-141">列をモデルの予測可能属性の 1 つとして含める場合は、 **[予測]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-141">If you want to include the column as one of the predictable attributes for the model, select **Predict**.</span></span>  
  
        -   <span data-ttu-id="e1463-142">構造に含め、入力または予測可能属性として指定しないアイテムは、`Ignore` フラグ付きで構造に追加されます。これは、データがモデルの作成時に処理され、分析には使用されず、ドリルスルーにのみ使用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e1463-142">Any item that you include in the structure but do not specify as an input or predictable attribute is added to the structure with the flag `Ignore`; this means that the data is processed when you build the model but is not used in analysis, and is available only for drillthrough.</span></span> <span data-ttu-id="e1463-143">これは、顧客名などの詳細を分析で使用しない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e1463-143">This can be handy if you want to include details such as customer names but don't want to use them in analysis.</span></span>  
  
     <span data-ttu-id="e1463-144">**[終了]** をクリックして、入れ子になったテーブルを処理するウィザードの部分を終了します。</span><span class="sxs-lookup"><span data-stu-id="e1463-144">Click **Finish** to close the part of the wizard that works with nested tables.</span></span> <span data-ttu-id="e1463-145">プロセスを繰り返して、複数の入れ子になった列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="e1463-145">You can repeat the process to add multiple nested columns.</span></span>  
  
10. <span data-ttu-id="e1463-146">**[列のコンテンツおよびデータ型の指定]** ページの **[マイニング モデル構造]** で、各列のコンテンツの種類とデータ型を設定します。</span><span class="sxs-lookup"><span data-stu-id="e1463-146">On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, set the content type and data type for each column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1463-147">OLAP マイニング モデルでは、 **[検出]** 機能を使用して、連続したデータと連続しないデータのどちらが列に含まれているかを自動的に検出することはできません。</span><span class="sxs-lookup"><span data-stu-id="e1463-147">OLAP mining models do not support using the **Detect** feature to automatically detect whether a column contains continuous or discrete data.</span></span>  
  
     <span data-ttu-id="e1463-148">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-148">Click **Next**.</span></span>  
  
11. <span data-ttu-id="e1463-149">**[ソース キューブのスライス]** ページでは、マイニング構造の作成に使用されるデータをフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="e1463-149">On the **Slice Source Cube** page, you can filter the data that is used to create the mining structure.</span></span>  
  
     <span data-ttu-id="e1463-150">キューブをスライスすると、モデルの作成に使用されるデータを制限できます。</span><span class="sxs-lookup"><span data-stu-id="e1463-150">Slicing the cube lets you restrict the data that is used to build the model.</span></span> <span data-ttu-id="e1463-151">たとえば、Geography 階層と以下のアイテムでスライスすることにより、地域ごとに異なるモデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e1463-151">For example, you could build separate models for each region by slicing on the Geography hierarchy and</span></span>  
  
    -   <span data-ttu-id="e1463-152">**ディメンション**: ドロップダウン リストから、関連するディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-152">**Dimension**: Choose a related dimension from the dropdown list.</span></span>  
  
    -   <span data-ttu-id="e1463-153">**階層**: フィルターを適用するディメンション階層のレベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-153">**Hierarchy**:  Select the level of the dimension hierarchy at which you want to apply the filter.</span></span> <span data-ttu-id="e1463-154">たとえば、[Geography] ディメンションでスライスする場合は、[Region Country Name] などの階層レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-154">For example, if you are slicing by the [Geography] dimension, you would choose a hierarchy level such as [Region Country Name] .</span></span>  
  
    -   <span data-ttu-id="e1463-155">**演算子**: 一覧から演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-155">**Operator**: Choose an operator from the list.</span></span>  
  
    -   <span data-ttu-id="e1463-156">**フィルター式**: フィルター条件として使用する値または式を入力するか、ドロップダウン リストを使用して、指定した階層レベルでメンバーの一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="e1463-156">**Filter Expression**: Type a value or expression to serve as the filter condition, or use the dropdown list to select a value from the list of members at the specified level of the hierarchy.</span></span>  
  
         <span data-ttu-id="e1463-157">たとえば、[Geography] をディメンションとして選択し、[Region Country Name] を階層レベルとして選択した場合、ドロップダウンリストには、フィルター条件として使用できるすべての有効な国/地域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1463-157">For example, if you selected [Geography] as the dimension and [Region Country Name] as the hierarchy level, the dropdown list contains all the valid countries/regions that you can use as a filter condition.</span></span> <span data-ttu-id="e1463-158">複数選択することができます。</span><span class="sxs-lookup"><span data-stu-id="e1463-158">You can make multiple selections.</span></span> <span data-ttu-id="e1463-159">その結果、マイニング構造内のデータは、これらの地域のキューブ データに制限されます。</span><span class="sxs-lookup"><span data-stu-id="e1463-159">As a result, the data in the mining structure will be limited to cube data from these geographical areas.</span></span>  
  
    -   <span data-ttu-id="e1463-160">**パラメーター**: このチェック ボックスは無視します。</span><span class="sxs-lookup"><span data-stu-id="e1463-160">**Parameters**: Ignore this check box.</span></span> <span data-ttu-id="e1463-161">このダイアログ ボックスでは複数のキューブ フィルター シナリオがサポートされ、このオプションはマイニング構造の作成に関係しません。</span><span class="sxs-lookup"><span data-stu-id="e1463-161">This dialog box supports multiple cube filtering scenarios and this option is not relevant to building a mining structure.</span></span>  
  
     <span data-ttu-id="e1463-162">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-162">Click **Next**.</span></span>  
  
12. <span data-ttu-id="e1463-163">**[トレーニング セットとテスト セットにデータを分割します]** ページで、テスト用に予約するマイニング構造データの割合を指定するか、テスト ケースの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1463-163">On the **Split data into training and testing sets** page, specify a percentage of the mining structure data to reserve for testing, or specify the maximum number of test cases.</span></span> <span data-ttu-id="e1463-164">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-164">Click **Next**.</span></span>  
  
     <span data-ttu-id="e1463-165">両方の値を指定した場合、それらの制限のうちの低い方が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1463-165">If you specify both values, the limits are combined to use whichever is lowest.</span></span>  
  
13. <span data-ttu-id="e1463-166">**[ウィザードの完了]** ページで、新しい OLAP マイニング構造と初期マイニング モデルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1463-166">On the **Completing the Wizard** page, provide a name for the new OLAP mining structure and the initial mining model.</span></span>  
  
14. <span data-ttu-id="e1463-167">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1463-167">Click **Finish**.</span></span>  
  
15. <span data-ttu-id="e1463-168">**[ウィザードの完了]** ページで、マイニング モデル ディメンションまたはマイニング モデル ディメンションを使用するキューブ、あるいはその両方を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e1463-168">On the **Completing the Wizard** page, you also have the option to create a mining model dimension and/or a cube using the mining model dimension.</span></span> <span data-ttu-id="e1463-169">これらのオプションは、次のアルゴリズムを使用して作成されるモデルに対してのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e1463-169">These options are supported only for models built using the following algorithms:</span></span>  
  
    -   <span data-ttu-id="e1463-170">Microsoft クラスタリング アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="e1463-170">Microsoft Clustering algorithm</span></span>  
  
    -   <span data-ttu-id="e1463-171">Microsoft デシジョン ツリー アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="e1463-171">Microsoft Decision Trees algorithm</span></span>  
  
    -   <span data-ttu-id="e1463-172">Microsoft アソシエーション ルール アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="e1463-172">Microsoft Association Rules algorithm</span></span>  
  
     <span data-ttu-id="e1463-173">**[マイニング モデル ディメンションを作成する]**: このチェック ボックスをオンにして、マイニング モデル ディメンションの種類名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1463-173">**Create mining model dimension**: Select this check box and provide a type name for the mining model dimension.</span></span> <span data-ttu-id="e1463-174">このオプションを使用すると、マイニング構造の作成に使用された元のキューブ内に新しいディメンションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e1463-174">When you use this option, a new dimension is created within the original cube that was used to build the mining structure.</span></span> <span data-ttu-id="e1463-175">このディメンションを使用してドリル ダウンし、さらに分析を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e1463-175">You can use this dimension to drill down and conduct further analysis.</span></span> <span data-ttu-id="e1463-176">ディメンションはキューブ内にあるため、ディメンションは自動的にケース データ ディメンションにマップされます。</span><span class="sxs-lookup"><span data-stu-id="e1463-176">Because the dimension is located within the cube, the dimension is automatically mapped to the case data dimension.</span></span>  
  
     <span data-ttu-id="e1463-177">**[マイニング モデル ディメンションを使用してキューブを作成する]**: このチェック ボックスをオンにし、新しいキューブの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1463-177">**Create cube using mining model dimension**: Select this check box, and provide a name for the new cube.</span></span> <span data-ttu-id="e1463-178">このオプションを使用する場合、構造の作成に使用された既存のディメンションと、モデルからの結果を格納する新しいデータ マイニング ディメンションを含む新しいキューブが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e1463-178">When you use this option, a new cube is created that contains both the existing dimensions that were used in building the structure, and the new data mining dimension that contains the results from the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1463-179">参照</span><span class="sxs-lookup"><span data-stu-id="e1463-179">See Also</span></span>  
 [<span data-ttu-id="e1463-180">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="e1463-180">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
