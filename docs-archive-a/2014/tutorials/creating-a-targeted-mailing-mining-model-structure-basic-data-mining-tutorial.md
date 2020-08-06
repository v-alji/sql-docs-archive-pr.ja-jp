---
title: 絞り込みメールマイニングモデル構造の作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6a27f818b29120e40248044091c78205dad945bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719125"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a><span data-ttu-id="fea6a-102">絞り込みメール配信マイニング モデル構造の作成 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="fea6a-102">Creating a Targeted Mailing Mining Model Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="fea6a-103">絞り込みメール配信シナリオを作成するには、まず、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のデータ マイニング ウィザードを使用して、新しいマイニング構造とデシジョン ツリー マイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-103">The first step in creating a targeted mailing scenario is to use the Data Mining Wizard in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a new mining structure and decision tree mining model.</span></span>  
  
 <span data-ttu-id="fea6a-104">このタスクでは、新しいマイニング構造を設定し、デシジョンツリーアルゴリズムに基づいて初期マイニングモデルを追加し [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fea6a-104">In this task you will set up a new mining structure, and add an initial mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="fea6a-105">マイニング構造を作成するには、まずテーブルとビューを選択し、トレーニングに使用する列とテストに使用する列を特定します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-105">To create the structure, you will first select tables and views and then identify which columns will be used for training and which for testing.</span></span>  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a><span data-ttu-id="fea6a-106">絞り込みメール配信シナリオ用のマイニング構造を作成するには</span><span class="sxs-lookup"><span data-stu-id="fea6a-106">To create a mining structure for the targeted mailing scenario</span></span>  
  
1.  <span data-ttu-id="fea6a-107">ソリューションエクスプローラーで、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックして、データマイニングウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-107">In Solution Explorer, right-click **Mining Structures** and select **New Mining Structure** to start the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="fea6a-108">**[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-108">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="fea6a-109">[**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-109">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="fea6a-110">[**データマイニング構造の作成**] ページの [**使用するデータマイニング技法を指定**してください] で、[ **Microsoft デシジョンツリー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-110">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Decision Trees**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fea6a-111">データ マイニング アルゴリズムが見つからないという警告が発生する場合は、プロジェクトのプロパティが適切に構成されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fea6a-111">If you get a warning that no data mining algorithms can be found, the project properties might not be configured correctly.</span></span> <span data-ttu-id="fea6a-112">この警告は、プロジェクトが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーからデータ マイニング アルゴリズムの一覧を取得しようとして、サーバーが見つからない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-112">This warning occurs when the project attempts to retrieve a list of data mining algorithms from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and cannot find the server.</span></span> <span data-ttu-id="fea6a-113">既定で [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] は、は**localhost**をサーバーとして使用します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-113">By default, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] will use **localhost** as the server.</span></span> <span data-ttu-id="fea6a-114">別のインスタンスまたは名前付きインスタンスを使用している場合は、プロジェクトのプロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fea6a-114">If you are using a different instance, or a named instance, you must change the project properties.</span></span> <span data-ttu-id="fea6a-115">詳細については、「[基本的なデータマイニングチュートリアル&#41;&#40;Analysis Services プロジェクトの作成](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fea6a-115">For more information, see [Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).</span></span>  
  
5.  <span data-ttu-id="fea6a-116">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-116">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="fea6a-117">[**データソースビューの選択**] ページの [**使用できるデータソースビュー** ] ペインで、[**対象メーリング**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-117">On the **Select Data Source View** page, in the **Available data source views** pane, select **Targeted Mailing**.</span></span> <span data-ttu-id="fea6a-118">[**参照**] をクリックしてデータソースビュー内のテーブルを表示し、[**閉じる**] をクリックしてウィザードに戻ります。</span><span class="sxs-lookup"><span data-stu-id="fea6a-118">You can click **Browse** to view the tables in the data source view and then click **Close** to return to the wizard.</span></span>  
  
7.  <span data-ttu-id="fea6a-119">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-119">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="fea6a-120">[**テーブルの種類の指定**] ページで、[vTargetMail] の [**ケース**] 列のチェックボックスをオンにして、ケーステーブルとして使用し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-120">On the **Specify Table Types** page, select the check box in the **Case** column for vTargetMail to use it as the case table, and then click **Next**.</span></span> <span data-ttu-id="fea6a-121">ProspectiveBuyer テーブルは後でテストに使用するので、ここでは無視します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-121">You will use the ProspectiveBuyer table later for testing; ignore it for now.</span></span>  
  
9. <span data-ttu-id="fea6a-122">[**トレーニングデータの指定**] ページで、少なくとも1つの予測可能列、1つのキー列、およびモデルの1つの入力列を指定します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-122">On the **Specify the Training Data** page, you will identify at least one predictable column, one key column, and one input column for your model.</span></span> <span data-ttu-id="fea6a-123">[ **Bikebuyer** ] 行の [**予測可能**] 列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-123">Select the check box in the **Predictable** column in the **BikeBuyer** row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fea6a-124">ウィンドウの下部に表示される警告に注意してください。</span><span class="sxs-lookup"><span data-stu-id="fea6a-124">Notice the warning at the bottom of the window.</span></span> <span data-ttu-id="fea6a-125">少なくとも1つの**入力**と1つの**予測可能**列を選択するまで、次のページに移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="fea6a-125">You will not be able to navigate to the next page until you select at least one **Input** and one **Predictable** column.</span></span>  
  
10. <span data-ttu-id="fea6a-126">[**提案**] をクリックして [**関連列の提示**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="fea6a-126">Click **Suggest** to open the **Suggest Related Columns** dialog box.</span></span>  
  
     <span data-ttu-id="fea6a-127">少なくとも1つの予測可能な属性が選択されている場合は、[**提案**] ボタンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="fea6a-127">The **Suggest** button is enabled whenever at least one predictable attribute has been selected.</span></span> <span data-ttu-id="fea6a-128">[**関連列の提示**] ダイアログボックスには、予測可能列に最も密接に関連する列が一覧表示され、予測可能な属性との相関関係によって属性が並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="fea6a-128">The **Suggest Related Columns** dialog box lists the columns that are most closely related to the predictable column, and orders the attributes by their correlation with the predictable attribute.</span></span> <span data-ttu-id="fea6a-129">相関性の高い列 (信頼スコアが 95% を超えている場合) は、モデルに追加する対象として自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="fea6a-129">Columns with a significant correlation (confidence greater than 95%) are automatically selected to be included in the model.</span></span>  
  
     <span data-ttu-id="fea6a-130">提案を確認し、[**キャンセル**] をクリックして提案を無視します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-130">Review the suggestions, and then click **Cancel** toignore the suggestions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fea6a-131">[ **OK**] をクリックすると、一覧表示されたすべての候補がウィザードの入力列としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="fea6a-131">If you click **OK**, all listed suggestions will be marked as input columns in the wizard.</span></span> <span data-ttu-id="fea6a-132">提示内容の一部のみを使用する場合、値を手動で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fea6a-132">If you agree with only some of the suggestions, you must change the values manually.</span></span>  
  
11. <span data-ttu-id="fea6a-133">[**キー** ] 列のチェックボックスが [**顧客キー** ] 行で選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-133">Verify that the check box in the **Key** column is selected in the **CustomerKey** row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fea6a-134">データ ソース ビューのソース テーブルにキーが表示されていれば、その列がモデルのキーとして自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="fea6a-134">If the source table from the data source view indicates a key, the Data Mining Wizard automatically chooses that column as a key for the model.</span></span>  
  
12. <span data-ttu-id="fea6a-135">次の行の [**入力**] 列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-135">Select the check boxes in the **Input** column in the following rows.</span></span> <span data-ttu-id="fea6a-136">複数の列をオンにするには、セルの範囲を強調表示し、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながらチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-136">You can check multiple columns by highlighting a range of cells and pressing CTRL while selecting a check box.</span></span>  
  
    -   <span data-ttu-id="fea6a-137">**変更**</span><span class="sxs-lookup"><span data-stu-id="fea6a-137">**Age**</span></span>  
  
    -   <span data-ttu-id="fea6a-138">**CommuteDistance**</span><span class="sxs-lookup"><span data-stu-id="fea6a-138">**CommuteDistance**</span></span>  
  
    -   <span data-ttu-id="fea6a-139">**EnglishEducation**</span><span class="sxs-lookup"><span data-stu-id="fea6a-139">**EnglishEducation**</span></span>  
  
    -   <span data-ttu-id="fea6a-140">**EnglishOccupation**</span><span class="sxs-lookup"><span data-stu-id="fea6a-140">**EnglishOccupation**</span></span>  
  
    -   <span data-ttu-id="fea6a-141">**性別**</span><span class="sxs-lookup"><span data-stu-id="fea6a-141">**Gender**</span></span>  
  
    -   <span data-ttu-id="fea6a-142">**GeographyKey**</span><span class="sxs-lookup"><span data-stu-id="fea6a-142">**GeographyKey**</span></span>  
  
    -   <span data-ttu-id="fea6a-143">**HouseOwnerFlag**</span><span class="sxs-lookup"><span data-stu-id="fea6a-143">**HouseOwnerFlag**</span></span>  
  
    -   <span data-ttu-id="fea6a-144">**MaritalStatus**</span><span class="sxs-lookup"><span data-stu-id="fea6a-144">**MaritalStatus**</span></span>  
  
    -   <span data-ttu-id="fea6a-145">**NumberCarsOwned**</span><span class="sxs-lookup"><span data-stu-id="fea6a-145">**NumberCarsOwned**</span></span>  
  
    -   <span data-ttu-id="fea6a-146">**NumberChildrenAtHome**</span><span class="sxs-lookup"><span data-stu-id="fea6a-146">**NumberChildrenAtHome**</span></span>  
  
    -   <span data-ttu-id="fea6a-147">**リージョン**</span><span class="sxs-lookup"><span data-stu-id="fea6a-147">**Region**</span></span>  
  
    -   <span data-ttu-id="fea6a-148">**TotalChildren**</span><span class="sxs-lookup"><span data-stu-id="fea6a-148">**TotalChildren**</span></span>  
  
    -   <span data-ttu-id="fea6a-149">**YearlyIncome**</span><span class="sxs-lookup"><span data-stu-id="fea6a-149">**YearlyIncome**</span></span>  
  
13. <span data-ttu-id="fea6a-150">ページの左端の列で、次の行のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-150">On the far left column of the page, select the check boxes in the following rows.</span></span>  
  
    -   <span data-ttu-id="fea6a-151">**AddressLine1**</span><span class="sxs-lookup"><span data-stu-id="fea6a-151">**AddressLine1**</span></span>  
  
    -   <span data-ttu-id="fea6a-152">**AddressLine2**</span><span class="sxs-lookup"><span data-stu-id="fea6a-152">**AddressLine2**</span></span>  
  
    -   <span data-ttu-id="fea6a-153">**DateFirstPurchase**</span><span class="sxs-lookup"><span data-stu-id="fea6a-153">**DateFirstPurchase**</span></span>  
  
    -   <span data-ttu-id="fea6a-154">**EmailAddress**</span><span class="sxs-lookup"><span data-stu-id="fea6a-154">**EmailAddress**</span></span>  
  
    -   <span data-ttu-id="fea6a-155">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="fea6a-155">**FirstName**</span></span>  
  
    -   <span data-ttu-id="fea6a-156">**LastName**</span><span class="sxs-lookup"><span data-stu-id="fea6a-156">**LastName**</span></span>  
  
     <span data-ttu-id="fea6a-157">上記の行の左の列のみがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fea6a-157">Ensure that these rows have checks only in the left column.</span></span> <span data-ttu-id="fea6a-158">これらの列は構造に追加されますが、モデルには追加されません。</span><span class="sxs-lookup"><span data-stu-id="fea6a-158">These columns will be added to your structure but will not be included in the model.</span></span> <span data-ttu-id="fea6a-159">ただし、モデル作成後は、ドリルスルーやテストに使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fea6a-159">However, after the model is built, they will be available for drillthrough and testing.</span></span> <span data-ttu-id="fea6a-160">ドリルスルーの詳細については、「[データマイニング &#40;のドリルスルークエリ](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="fea6a-160">For more information about drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span></span>  
  
14. <span data-ttu-id="fea6a-161">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fea6a-161">Click **Next**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fea6a-162">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="fea6a-162">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fea6a-163">データ型とコンテンツの種類の指定 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="fea6a-163">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="fea6a-164">参照</span><span class="sxs-lookup"><span data-stu-id="fea6a-164">See Also</span></span>  
 <span data-ttu-id="fea6a-165">[データマイニングウィザード &#40;テーブルの種類の指定&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="fea6a-165">[Specify Table Types &#40;Data Mining Wizard&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="fea6a-166">[データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="fea6a-166">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="fea6a-167">Microsoft デシジョンツリーアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="fea6a-167">Microsoft Decision Trees Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
