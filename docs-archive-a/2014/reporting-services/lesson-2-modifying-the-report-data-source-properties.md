---
title: 'レッスン 2: レポート データ ソースのプロパティの変更 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c962b0ff-ce8a-4742-8262-dc730901afcf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05e56a58ce28ee1e1e450d3af012cbd1ffe668ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632983"
---
# <a name="lesson-2-modifying-the-report-data-source-properties"></a><span data-ttu-id="5619f-102">レッスン 2: レポート データ ソースのプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="5619f-102">Lesson 2: Modifying the Report Data Source Properties</span></span>
  <span data-ttu-id="5619f-103">このレッスンでは、受信者に配信されるレポートを、レポート マネージャーを使って選択します。</span><span class="sxs-lookup"><span data-stu-id="5619f-103">In this lesson, you will use Report Manager to select a report that will be delivered to recipients.</span></span> <span data-ttu-id="5619f-104">ここで定義するデータ ドリブン サブスクリプションによって、チュートリアル「 **基本的なテーブル レポートの作成 (SSRS チュートリアル)** 」で作成されたレポート [基本的なテーブル レポートの作成 (SSRS チュートリアル)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)が配信されます。</span><span class="sxs-lookup"><span data-stu-id="5619f-104">The data-driven subscription that you will define will distribute the **Sales Order** report created in the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md).</span></span> <span data-ttu-id="5619f-105">この後の手順では、レポートがデータの取得に使用するデータ ソースの接続情報を変更します。</span><span class="sxs-lookup"><span data-stu-id="5619f-105">In the steps that follow, you will modify the data source connection information used by the report to get data.</span></span> <span data-ttu-id="5619f-106">データ ドリブン サブスクリプションを介して配信できるのは、 **保存されている資格情報** を使用してレポート データ ソースにアクセスするレポートのみです。</span><span class="sxs-lookup"><span data-stu-id="5619f-106">Only reports that use **stored credentials** to access a report data source can be distributed through a data-driven subscription.</span></span> <span data-ttu-id="5619f-107">保存されている資格情報は、レポートの自動処理に必要となります。</span><span class="sxs-lookup"><span data-stu-id="5619f-107">Stored credentials are necessary for unattended report processing.</span></span>

 <span data-ttu-id="5619f-108">また、データセットとレポートを変更し、パラメーターを使用して `[Order]` のレポートをフィルター処理します。これによってサブスクリプションが特定の注文と表示形式で、レポートのさまざまなインスタンスを出力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5619f-108">You will also modify the dataset and report to use a parameter to filter the report on the `[Order]` so the subscription can output different instances of the report for specific orders and rendering formats.</span></span>

 <span data-ttu-id="5619f-109">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="5619f-109">**In this topic:**</span></span>

-   [<span data-ttu-id="5619f-110">データ ソースのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="5619f-110">To Modify the Data Source Properties</span></span>](#bkmk_modify_datasource)

-   [<span data-ttu-id="5619f-111">AdventureWorksDataset を変更するには</span><span class="sxs-lookup"><span data-stu-id="5619f-111">To Modify the AdventureWorksDataset</span></span>](#bkmk_modify_dataset)

-   [<span data-ttu-id="5619f-112">レポートパラメーターを追加してレポートを再パブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="5619f-112">To Add a Report Parameter and Republish the Report</span></span>](#bkmk_add_reportparameter)

-   [<span data-ttu-id="5619f-113">レポートを再配置するには</span><span class="sxs-lookup"><span data-stu-id="5619f-113">To Re-deploy the Report</span></span>](#bkmk_redeploy)

##  <a name="to-modify-the-data-source-properties"></a><a name="bkmk_modify_datasource"></a><span data-ttu-id="5619f-114">データソースのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="5619f-114">To Modify the Data Source Properties</span></span>

1.  <span data-ttu-id="5619f-115">管理者特権を使用して[SSRS ネイティブモード&#41;&#40;レポートマネージャー](../../2014/reporting-services/report-manager-ssrs-native-mode.md)を開始します。たとえば、Internet Explorer のアイコンを右クリックし、[**管理者として実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-115">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) with administrator privileges, for example, right-click the icon for Internet Explorer and click **Run as administrator**.</span></span>

2.  <span data-ttu-id="5619f-116">**Sales Orders** レポートを含むフォルダーを参照して、ショートカット メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-116">Browse to the folder containing the **Sales Orders** report and in the context menu of the report, click **Manage**.</span></span>

     <span data-ttu-id="5619f-117">![レポート ショートカット メニューを開いて管理を選択](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "レポート ショートカット メニューを開いて管理を選択")</span><span class="sxs-lookup"><span data-stu-id="5619f-117">![Open the report context menu and select manage](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "Open the report context menu and select manage")</span></span>

3.  <span data-ttu-id="5619f-118">**[データ ソース]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-118">Click the **Data Sources** tab.</span></span>

4.  <span data-ttu-id="5619f-119">**[接続の種類]** で **[Microsoft SQL Server]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5619f-119">For **Connection Type**, select **Microsoft SQL Server**.</span></span>

5.  <span data-ttu-id="5619f-120">カスタム データ ソースの接続文字列は次のようになります。この文字列は、サンプル データベースがローカルのデータベース サーバーに存在することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="5619f-120">The custom data source connection string will be the following and it assumes that the sample database is on a local database server:</span></span>

    ```
    Data source=localhost; initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="5619f-121">**[レポート サーバーに保存され、セキュリティで保護された資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-121">Click **Credentials stored securely in the report server**.</span></span>

7.  <span data-ttu-id="5619f-122">ユーザー名とパスワードを入力します。ユーザー名は、 *domain\user*の形式で入力してください。</span><span class="sxs-lookup"><span data-stu-id="5619f-122">Type your user name (use the format *domain\user*) and password.</span></span> <span data-ttu-id="5619f-123">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースにアクセスする権限がない場合は、このデータベースへの権限があるログイン情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="5619f-123">If you do not have permission to access the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database, specify a login that does.</span></span>

8.  <span data-ttu-id="5619f-124">**[データ ソースへの接続時に Windows 資格情報として使用する]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-124">Click **Use as windows credentials when connecting to the data source**, and then click **OK**.</span></span> <span data-ttu-id="5619f-125">ドメイン アカウントを使用していない場合 ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインを使用している場合など) は、このチェック ボックスをオンにしないでください。</span><span class="sxs-lookup"><span data-stu-id="5619f-125">If you are not using a domain account (for example, if you are using a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login), do not click this checkbox.</span></span>

9. <span data-ttu-id="5619f-126">**[接続テスト]** をクリックして、データ ソースに接続できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5619f-126">Click **Test Connection** to verify you can connect to the data source.</span></span>

10. <span data-ttu-id="5619f-127">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-127">Click **Apply**.</span></span>

11. <span data-ttu-id="5619f-128">レポートを表示し、指定した資格情報を使用してレポートが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5619f-128">View the report to verify that the report runs with the credentials you specified.</span></span> <span data-ttu-id="5619f-129">レポートを表示するには、[**表示**] タブをクリックします。レポートが開いたら、従業員名を選択し、[**レポートの表示**] ボタンをクリックしてレポートを表示する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5619f-129">To view the report, click the **View** tab. Note that once the report is open, you must select an Employee name and then click the **View Report** button to view the report.</span></span>

##  <a name="to-modify-the-adventureworksdataset"></a><a name="bkmk_modify_dataset"></a><span data-ttu-id="5619f-130">AdventureWorksDataset を変更するには</span><span class="sxs-lookup"><span data-stu-id="5619f-130">To Modify the AdventureWorksDataset</span></span>

1.  <span data-ttu-id="5619f-131">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で Sales Orders レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="5619f-131">Open the Sales Orders report in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]</span></span>

2.  <span data-ttu-id="5619f-132">データセット `AdventureWorksDataset` を右クリックし、 **[データセットのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-132">Right-click the dataset `AdventureWorksDataset` and click **Dataset Properties**.</span></span>

3.  <span data-ttu-id="5619f-133">`WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` ステートメントを `Group By` ステートメントの前に追加します。</span><span class="sxs-lookup"><span data-stu-id="5619f-133">Add the statement `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` before the `Group By` statement.</span></span> <span data-ttu-id="5619f-134">完全なクエリ構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5619f-134">The full query syntax is the following:</span></span>

    ```
    SELECT soh.OrderDate AS Date, soh.SalesOrderNumber AS [Order], pps.Name AS Subcat, pp.Name AS Product, SUM(sd.OrderQty) AS Qty, SUM(sd.LineTotal)  AS LineTotal
    FROM Sales.SalesPerson AS sp INNER JOIN
      Sales.SalesOrderHeader AS soh ON sp.BusinessEntityID = soh.SalesPersonID INNER JOIN
       Sales.SalesOrderDetail AS sd ON sd.SalesOrderID = soh.SalesOrderID INNER JOIN
       Production.Product AS pp ON sd.ProductID = pp.ProductID
    INNER JOIN
       Production.ProductSubcategory AS pps ON pp.ProductSubcategoryID = pps.ProductSubcategoryID 
    INNER JOIN
        Production.ProductCategory AS ppc ON ppc.ProductCategoryID = pps.ProductCategoryID

    WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)

    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name, soh.SalesPersonID
    HAVING (ppc.Name = 'Clothing')
    ```

4.  <span data-ttu-id="5619f-135">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="5619f-135">Click **OK**</span></span>

##  <a name="to-add-a-report-parameter-and-republish-the-report"></a><a name="bkmk_add_reportparameter"></a><span data-ttu-id="5619f-136">レポートパラメーターを追加してレポートを再パブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="5619f-136">To Add a Report Parameter and Republish the Report</span></span>

1.  <span data-ttu-id="5619f-137">**レポート データ** ペインで、 **[新規作成]** をクリックし、 **[パラメーター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-137">In the **Report Data** pane click **New** and then click **Parameter...**</span></span>

2.  <span data-ttu-id="5619f-138">**[名前]** に「 `OrderNumber`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5619f-138">In **Name**, type `OrderNumber`.</span></span>

3.  <span data-ttu-id="5619f-139">**[プロンプト]** で、「 `OrderNumber`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5619f-139">In **Prompt**, type `OrderNumber`.</span></span>

4.  <span data-ttu-id="5619f-140">**[空白の値 (" " ) を許可]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5619f-140">Select **Allow blank value ("")**.</span></span>

5.  <span data-ttu-id="5619f-141">**[NULL 値を許可]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5619f-141">Select **Allow null value**.</span></span>

6.  <span data-ttu-id="5619f-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-142">Click **OK**.</span></span> <span data-ttu-id="5619f-143">次の図のように、パラメーターが **レポート データ ペイン** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5619f-143">The parameter will be added to the **Report Data pane** and it will look like the following image:</span></span>

     <span data-ttu-id="5619f-144">![新しいパラメーターをレポート データ ペインに追加](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "新しいパラメーターをレポート データ ペインに追加")</span><span class="sxs-lookup"><span data-stu-id="5619f-144">![The new parameter is added to the Report Data pane](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "The new parameter is added to the Report Data pane")</span></span>

7.  <span data-ttu-id="5619f-145">**[プレビュー]** タブをクリックしてレポートを実行します。レポート最上部のパラメーター入力ボックスに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5619f-145">Click the **Preview** tab to run the report.Note the parameter input box at the top of the report.</span></span> <span data-ttu-id="5619f-146">次のいずれかを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5619f-146">You can either:</span></span>

    -   <span data-ttu-id="5619f-147">[レポートの表示] をクリックして、パラメーターを使用しない完全なレポートを表示する。</span><span class="sxs-lookup"><span data-stu-id="5619f-147">Click View Report to see the full report without using a parameter.</span></span>

    -   <span data-ttu-id="5619f-148">Null オプションの選択を解除して注文番号を入力する。たとえば「so71949」と入力すると、レポートに注文が 1 つだけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="5619f-148">Unselect the Null option and type an order number, for example so71949 to view only the one order in the report.</span></span>

         <span data-ttu-id="5619f-149">![パラメーター領域を表示するレポート ビューアー](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "パラメーター領域を表示するレポート ビューアー")</span><span class="sxs-lookup"><span data-stu-id="5619f-149">![Report viewer with parameter area visible](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "Report viewer with parameter area visible")</span></span>

8.  <span data-ttu-id="5619f-150">レポートを再配置して、このレッスンで適用した変更を、次のレッスンのサブスクリプション構成で利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5619f-150">Re-deploy the report so the subscription configuration in the next lesson can utilize the changes you made in this lesson.</span></span> <span data-ttu-id="5619f-151">テーブルチュートリアルで使用されるプロジェクトプロパティの詳細については、「[レッスン 6: グループと合計 &#40;Reporting Services&#41;の追加](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)」の「レポートをレポートサーバーにパブリッシュするには (オプション)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5619f-151">For more information on the project properties used in the table tutorial, see section 'To Publish the Report to the Report Server (Optional)' of [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>

##  <a name="to-re-deploy-the-report"></a><a name="bkmk_redeploy"></a><span data-ttu-id="5619f-152">レポートを再配置するには</span><span class="sxs-lookup"><span data-stu-id="5619f-152">To Re-deploy the Report</span></span>

1.  <span data-ttu-id="5619f-153">レポートを再配置して、このレッスンで適用した変更を、次のレッスンのサブスクリプション構成で利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5619f-153">Re-deploy the report so the subscription configuration in the next lesson can utilize the changes you made in this lesson.</span></span> <span data-ttu-id="5619f-154">テーブルチュートリアルで使用されるプロジェクトプロパティの詳細については、「[レッスン 6: グループと合計 &#40;Reporting Services&#41;の追加](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)」の「レポートをレポートサーバーにパブリッシュするには (オプション)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5619f-154">For more information on the project properties used in the table tutorial, see section 'To Publish the Report to the Report Server (Optional)' of [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>

2.  <span data-ttu-id="5619f-155">ツール バーの **[ビルド]** をクリックし、 **[Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5619f-155">On the toolbar click **Build** and then click **Deploy tutorial**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5619f-156">次の手順</span><span class="sxs-lookup"><span data-stu-id="5619f-156">Next Steps</span></span>
 <span data-ttu-id="5619f-157">保存されている資格情報を使用してデータを取得するレポートを構成しました。</span><span class="sxs-lookup"><span data-stu-id="5619f-157">You successfully configured the report to get data using stored credentials.</span></span> <span data-ttu-id="5619f-158">次に、レポート マネージャーの [データ ドリブン サブスクリプション] ページを使用してサブスクリプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5619f-158">Next, you specify the subscription using the Data-Driven Subscription pages in Report Manager.</span></span> <span data-ttu-id="5619f-159">「 [レッスン 3: データ ドリブン サブスクリプションの定義](../reporting-services/lesson-3-defining-a-data-driven-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5619f-159">See [Lesson 3: Defining a Data-Driven Subscription](../reporting-services/lesson-3-defining-a-data-driven-subscription.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5619f-160">参照</span><span class="sxs-lookup"><span data-stu-id="5619f-160">See Also</span></span>
 <span data-ttu-id="5619f-161">[レポートデータソースの管理](report-data/manage-report-data-sources.md)[レポートデータソースの資格情報と接続情報の指定](report-data/specify-credential-and-connection-information-for-report-data-sources.md)[データドリブンサブスクリプションの作成 &#40;Ssrs チュートリアル&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) [基本的なテーブルレポートの作成 &#40;ssrs チュートリアル&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="5619f-161">[Manage Report Data Sources](report-data/manage-report-data-sources.md) [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)</span></span>


