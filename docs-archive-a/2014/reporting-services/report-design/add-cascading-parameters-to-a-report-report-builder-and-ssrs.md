---
title: カスケード型パラメーターのレポートへの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a22eec3-57a7-478e-b6fc-102a9dbe0591
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5419d448b2fa9526224e1bccd80d5c195e2763d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712729"
---
# <a name="add-cascading-parameters-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="d0cf7-102">カスケード型パラメーターのレポートへの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d0cf7-102">Add Cascading Parameters to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d0cf7-103">カスケード型パラメーターを使用すると、大量のレポート データの管理が可能になります。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-103">Cascading parameters provide a way of managing large amounts of report data.</span></span> <span data-ttu-id="d0cf7-104">パラメーターの値の一覧が、別のパラメーターで選択された値によって決まるように、関連するパラメーターのセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-104">You can define a set of related parameters so that the list of values for one parameter depends on the value chosen in another parameter.</span></span> <span data-ttu-id="d0cf7-105">たとえば、最初のパラメーターが独立しており、製品カテゴリの一覧を表すとします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-105">For example, the first parameter is independent and might present a list of product categories.</span></span> <span data-ttu-id="d0cf7-106">ユーザーが任意のカテゴリを選択すると、2 番目のパラメーターは最初のパラメーターの値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-106">When the user selects a category, the second parameter is dependent on the value of the first parameter.</span></span> <span data-ttu-id="d0cf7-107">その値は、選択したカテゴリ内のサブカテゴリの一覧で更新されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-107">Its values are updated with a list of subcategories within the chosen category.</span></span> <span data-ttu-id="d0cf7-108">ユーザーがレポートを表示するとき、カテゴリ パラメーターとサブカテゴリ パラメーターの両方の値を使用して、レポート データにフィルターが適用されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-108">When the user views the report, the values for both the category and subcategory parameters are used to filter report data.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="d0cf7-109">カスケード型パラメーターを作成するには、まずデータセット クエリを定義し、必要な各カスケード型パラメーターにクエリ パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-109">To create cascading parameters, you define the dataset query first and include a query parameter for each cascading parameter that you need.</span></span> <span data-ttu-id="d0cf7-110">各カスケード型パラメーターについて、使用可能な値を提供する独立したデータセットを作成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-110">You must also create a separate dataset for each cascading parameter to provide available values.</span></span> <span data-ttu-id="d0cf7-111">詳細については、「[レポート パラメーターの値の追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-111">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
 <span data-ttu-id="d0cf7-112">一覧の後半にあるパラメーターのデータセット クエリには一覧の前半にある各パラメーターへの参照が含まれているため、カスケード型パラメーターでは順序が重要な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-112">Order is important for cascading parameters because the dataset query for a parameter later in the list includes a reference to each parameter that is earlier in the list.</span></span> <span data-ttu-id="d0cf7-113">実行時には、レポート データ ペインのパラメーターの順序によって、パラメーター クエリがレポート内で作成される順序が決まります。したがって、ユーザーが後続の各パラメーター値を選択する順序が決まります。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-113">At run time, the order of the parameters in the Report Data pane determines the order in which the parameter queries appear in the report, and therefore, the order in which a user chooses each successive parameter value.</span></span>  
  
 <span data-ttu-id="d0cf7-114">複数の値を使用したカスケード型パラメーターを作成する方法、および [すべて選択] 機能を含める方法の詳細については、「 [すべてのマルチバリューカスケードパラメータを選択する方法](https://go.microsoft.com/fwlink/?LinkId=184757)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-114">For information about creating cascading parameters with multiple values and including the Select All feature, see [How to have a Select All Multivalue Cascading Parameter](https://go.microsoft.com/fwlink/?LinkId=184757).</span></span>  
  
### <a name="to-create-the-main-dataset-with-a-query-that-includes-multiple-related-parameters"></a><span data-ttu-id="d0cf7-115">関連する複数のパラメーターを含むクエリを使用してメイン データセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="d0cf7-115">To create the main dataset with a query that includes multiple related parameters</span></span>  
  
1.  <span data-ttu-id="d0cf7-116">レポート データ ペインでデータ ソースを右クリックし、 **[データセットの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-116">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="d0cf7-117">**[名前]** ボックスに、データセットの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-117">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="d0cf7-118">**[データ ソース]** ボックスのデータ ソースの名前を選択するか、 **[新規]** をクリックして名前を作成します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-118">In **Data source**, choose the name of the data source or click **New** to create one.</span></span>  
  
4.  <span data-ttu-id="d0cf7-119">**[クエリの種類]** ボックスで、選択したデータ ソースにクエリの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-119">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="d0cf7-120">このトピックでは、クエリの種類として **[テキスト]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-120">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="d0cf7-121">**[クエリ]** ボックスに、このレポートにデータを取得するためのクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-121">In **Query**, type the query to use to retrieve data for this report.</span></span> <span data-ttu-id="d0cf7-122">クエリには次の要素が必要です。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-122">The query must include the following parts:</span></span>  
  
    1.  <span data-ttu-id="d0cf7-123">データ ソース フィールドの一覧。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-123">A list of data source fields.</span></span> <span data-ttu-id="d0cf7-124">たとえば [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、SELECT ステートメントは指定されたテーブルまたはビューのデータベース列名の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-124">For example, in a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, the SELECT statement specifies a list of database column names from a given table or view.</span></span>  
  
    2.  <span data-ttu-id="d0cf7-125">カスケード型パラメーターごとに 1 つのクエリ パラメーター。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-125">One query parameter for each cascading parameter.</span></span> <span data-ttu-id="d0cf7-126">クエリ パラメーターは、クエリに含める特定の値またはクエリから除外する特定の値を指定することによって、データ ソースから取得するデータを制限します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-126">A query parameter limits the data retrieved from the data source by specifying certain values to include or exclude from the query.</span></span> <span data-ttu-id="d0cf7-127">通常、クエリ パラメーターはクエリの制約句で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-127">Typically, query parameters occur in a restriction clause in the query.</span></span> <span data-ttu-id="d0cf7-128">たとえば [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT ステートメントでは、クエリ パラメーターは WHERE 句で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-128">For example, in a [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement, query parameters occur in the WHERE clause.</span></span> <span data-ttu-id="d0cf7-129">詳細については、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server オンライン ブック [にある](https://go.microsoft.com/fwlink/?linkid=120955)のマニュアルの「WHERE と HAVING を使ったフィルターによる行選択」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-129">For more information, see "Filtering Rows by Using WHERE and HAVING" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
6.  <span data-ttu-id="d0cf7-130">**[実行]** (**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-130">Click **Run** (**!**).</span></span> <span data-ttu-id="d0cf7-131">クエリ パラメーターを指定し、クエリを実行したら、クエリ パラメーターに対応するレポート パラメーターが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-131">After you include query parameters and then run the query, report parameters that correspond to the query parameters are automatically created.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0cf7-132">最初にクエリを実行したときのクエリ パラメーターの順序によって、クエリ パラメーターがレポート内で作成される順序が決まります。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-132">The order of query parameters the first time you run a query determines the order that they are created in the report.</span></span> <span data-ttu-id="d0cf7-133">順序を変更するには、「[レポート パラメーターの順序の変更 &#40;レポート ビルダーおよび SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-133">To change the order, see [Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="d0cf7-134">次に、独立したパラメーターの値を提供するデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-134">Next, you will create a dataset that provides the values for the independent parameter.</span></span>  
  
### <a name="to-create-a-dataset-to-provide-values-for-an-independent-parameter"></a><span data-ttu-id="d0cf7-135">独立したパラメーターの値を提供するデータセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="d0cf7-135">To create a dataset to provide values for an independent parameter</span></span>  
  
1.  <span data-ttu-id="d0cf7-136">レポート データ ペインでデータ ソースを右クリックし、 **[データセットの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-136">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="d0cf7-137">**[名前]** ボックスに、データセットの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-137">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="d0cf7-138">**[データ ソース]** ボックスに表示された名前が、手順 1. で選択したデータ ソースの名前であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-138">In **Data source**, verify the name is the name of the data source you chose in step 1.</span></span>  
  
4.  <span data-ttu-id="d0cf7-139">**[クエリの種類]** ボックスで、選択したデータ ソースにクエリの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-139">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="d0cf7-140">このトピックでは、クエリの種類として **[テキスト]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-140">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="d0cf7-141">**[クエリ]** ボックスに、このパラメーターに値を取得するためのクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-141">In **Query**, type the query to use to retrieve values for this parameter.</span></span> <span data-ttu-id="d0cf7-142">通常、独立したパラメーターのクエリにはクエリ パラメーターが含まれません。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-142">Queries for independent parameters typically do not contain query parameters.</span></span> <span data-ttu-id="d0cf7-143">たとえば、すべてのカテゴリの値を提供するパラメーターのクエリを作成するには、次のような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-143">For example, to create a query for a parameter that provides all category values, you might use a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement similar to the following:</span></span>  
  
    ```  
    SELECT DISTINCT <column name> FROM <table>  
    ```  
  
     <span data-ttu-id="d0cf7-144">SELECT DISTINCT コマンドは、指定したテーブルの指定した列から一意の各値を取得できるように、結果セットから重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-144">The SELECT DISTINCT command removes duplicate values from the result set so that you get each unique value from the specified column in the specified table.</span></span>  
  
     <span data-ttu-id="d0cf7-145">**[実行]** (**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-145">Click **Run** (**!**).</span></span> <span data-ttu-id="d0cf7-146">結果セットには、この最初のパラメーターに使用可能な値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-146">The result set shows the values that are available for this first parameter.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="d0cf7-147">次に、このデータセットを使用する最初のパラメーターのプロパティを設定して、実行時に使用可能な値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-147">Next, you will set the properties of the first parameter to use this dataset to populate its available values at run-time.</span></span>  
  
### <a name="to-set-available-values-for-a-report-parameter"></a><span data-ttu-id="d0cf7-148">レポート パラメーターに使用可能な値を設定するには</span><span class="sxs-lookup"><span data-stu-id="d0cf7-148">To set available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="d0cf7-149">レポート データ ペインでパラメーター フォルダーの最初のパラメーターを右クリックし、 **[パラメーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-149">In the Report Data pane, in the Parameters folder, right-click the first parameter, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="d0cf7-150">**[名前]** ボックスのパラメーターの名前が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-150">In **Name**, verify that the name of the parameter is correct.</span></span>  
  
3.  <span data-ttu-id="d0cf7-151">**[使用できる値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-151">Click **Available Values**.</span></span>  
  
4.  <span data-ttu-id="d0cf7-152">**[クエリから値を取得]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-152">Click **Get values from a query**.</span></span> <span data-ttu-id="d0cf7-153">3 つのフィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-153">Three fields appear.</span></span>  
  
5.  <span data-ttu-id="d0cf7-154">**[データセット]** ボックスのドロップダウン リストから、前の手順で作成したデータセットの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-154">In **Dataset**, from the drop-down list, click the name of the dataset you created in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="d0cf7-155">**[値]** フィールドで、パラメーター値を指定するフィールドの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-155">In **Value** field, click the name of the field that provides the parameter value.</span></span>  
  
7.  <span data-ttu-id="d0cf7-156">**[ラベル]** フィールドで、パラメーターのラベルを指定するフィールドの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-156">In **Label** field, click the name of the field that provides the parameter label.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="d0cf7-157">次に、従属パラメーターの値を提供するデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-157">Next, you will create a dataset that provides the values for a dependent parameter.</span></span>  
  
### <a name="to-create-a-dataset-to-provide-values-for-a-dependent-parameter"></a><span data-ttu-id="d0cf7-158">従属パラメーターの値を提供するデータセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="d0cf7-158">To create a dataset to provide values for a dependent parameter</span></span>  
  
1.  <span data-ttu-id="d0cf7-159">レポート データ ペインでデータ ソースを右クリックし、 **[データセットの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-159">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="d0cf7-160">**[名前]** ボックスに、データセットの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-160">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="d0cf7-161">**[データ ソース]** ボックスに表示された名前が、手順 1. で選択したデータ ソースの名前であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-161">In **Data source**, verify the name is the name of the data source you chose in step 1.</span></span>  
  
4.  <span data-ttu-id="d0cf7-162">**[クエリの種類]** ボックスで、選択したデータ ソースにクエリの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-162">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="d0cf7-163">このトピックでは、クエリの種類として **[テキスト]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-163">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="d0cf7-164">**[クエリ]** ボックスに、このパラメーターに値を取得するためのクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-164">In **Query**, type the query to use to retrieve values for this parameter.</span></span> <span data-ttu-id="d0cf7-165">通常、従属パラメーターのクエリには、このパラメーターが依存している各クエリ パラメーターが含められます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-165">Queries for dependent parameters typically include query parameters for each parameter that this parameter is dependent on.</span></span> <span data-ttu-id="d0cf7-166">たとえば、カテゴリ (独立したパラメーター) のすべてのサブカテゴリ (従属パラメーター) の値を提供するパラメーターのクエリを作成するには、次のような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-166">For example, to create a query for a parameter that provides all subcategory (dependent parameter) values for a category (independent parameter), you might use a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement similar to the following:</span></span>  
  
    ```  
    SELECT DISTINCT Subcategory FROM <table>   
    WHERE (Category = @Category)  
    ```  
  
     <span data-ttu-id="d0cf7-167">WHERE 句では、Category はからのフィールドの名前であり、 \<table> @Category はクエリパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-167">In the WHERE clause, Category is the name of a field from \<table> and @Category is a query parameter.</span></span> <span data-ttu-id="d0cf7-168">このステートメントを使用すると、@Category に指定したカテゴリのサブカテゴリの一覧が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-168">This statement produces a list of subcategories for the category specified in @Category.</span></span> <span data-ttu-id="d0cf7-169">この値は実行時に、ユーザーが同名のレポート パラメーターに選択した値を使用して入力されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-169">At run time, this value will be filled in with the value that the user chooses for the report parameter that has the same name.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="d0cf7-170">次に、このデータセットを使用する 2 番目のパラメーターのプロパティを設定して、実行時に使用可能な値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-170">Next, you will set the properties of the second parameter to use this dataset to populate its available values at run time.</span></span>  
  
### <a name="to-set-available-values-for-a-report-parameter"></a><span data-ttu-id="d0cf7-171">レポート パラメーターに使用可能な値を設定するには</span><span class="sxs-lookup"><span data-stu-id="d0cf7-171">To set available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="d0cf7-172">レポート データ ペインでパラメーター フォルダーの最初のパラメーターを右クリックし、 **[パラメーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-172">In the Report Data pane, in the Parameters folder, right-click the first parameter, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="d0cf7-173">**[名前]** ボックスのパラメーターの名前が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-173">In **Name**, verify that the name of the parameter is correct.</span></span>  
  
3.  <span data-ttu-id="d0cf7-174">**[使用できる値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-174">Click **Available Values**.</span></span>  
  
4.  <span data-ttu-id="d0cf7-175">**[クエリから値を取得]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-175">Click **Get values from a query**.</span></span>  
  
5.  <span data-ttu-id="d0cf7-176">**[データセット]** ボックスのドロップダウン リストから、前の手順で作成したデータセットの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-176">In **Dataset**, from the drop-down list, click the name of the dataset you created in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="d0cf7-177">**[値]** フィールドで、パラメーター値を指定するフィールドの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-177">In **Value** field, click the name of the field that provides the parameter value.</span></span>  
  
7.  <span data-ttu-id="d0cf7-178">**[ラベル]** フィールドで、パラメーターのラベルを指定するフィールドの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-178">In **Label** field, click the name of the field that provides the parameter label.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-cascading-parameters"></a><span data-ttu-id="d0cf7-179">カスケード型パラメーターをテストするには</span><span class="sxs-lookup"><span data-stu-id="d0cf7-179">To test the cascading parameters</span></span>  
  
1.  <span data-ttu-id="d0cf7-180">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-180">Click **Run**.</span></span>  
  
2.  <span data-ttu-id="d0cf7-181">最初の独立したパラメーターのドロップダウン リストから値を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-181">From the drop-down list for the first, independent parameter, choose a value.</span></span>  
  
     <span data-ttu-id="d0cf7-182">レポート プロセッサによって、次のパラメーターのデータセット クエリが実行され、最初のパラメーターに選択した値が渡されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-182">The report processor runs the dataset query for the next parameter and passes it the value you chose for the first parameter.</span></span> <span data-ttu-id="d0cf7-183">最初のパラメーターの値に基づいて、使用可能な値を使用して 2 番目のパラメーターのドロップダウン リストが入力されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-183">The drop-down list for the second parameter is populated with the available values based on the first parameter value.</span></span>  
  
3.  <span data-ttu-id="d0cf7-184">2 番目の従属パラメーターのドロップダウン リストから値を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-184">From the drop-down list for the second, dependent parameter, choose a value.</span></span>  
  
     <span data-ttu-id="d0cf7-185">選択肢を変更できるように、最後のパラメーターを選択した後、レポートは自動的に実行されません。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-185">The report does not run automatically after you choose the last parameter so that you can change your choice.</span></span>  
  
4.  <span data-ttu-id="d0cf7-186">**[レポートの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-186">Click **View Report**.</span></span> <span data-ttu-id="d0cf7-187">選択したパラメーターに基づいて、レポートの表示が更新されます。</span><span class="sxs-lookup"><span data-stu-id="d0cf7-187">The report updates the display based on the parameters you have chosen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0cf7-188">参照</span><span class="sxs-lookup"><span data-stu-id="d0cf7-188">See Also</span></span>  
 <span data-ttu-id="d0cf7-189">[レポートパラメーターの追加、変更、または削除 &#40;レポートビルダーと SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d0cf7-189">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d0cf7-190">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="d0cf7-190">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="d0cf7-191">[チュートリアル: レポートへのパラメーターの追加 &#40;レポートビルダー&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="d0cf7-191">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="d0cf7-192">[チュートリアル &#40;レポートビルダー&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="d0cf7-192">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="d0cf7-193">[データセットフィルター、データ領域フィルター、およびグループフィルターを追加 &#40;レポートビルダーと SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="d0cf7-193">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 [<span data-ttu-id="d0cf7-194">レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d0cf7-194">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
