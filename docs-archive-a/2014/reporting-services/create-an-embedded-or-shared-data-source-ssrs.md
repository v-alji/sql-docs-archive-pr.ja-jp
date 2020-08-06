---
title: 埋め込みデータソースまたは共有データソースを作成する (SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], creating
ms.assetid: b111a8d0-a60d-4c8b-b00a-51644b19c34b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52c5263859ad16ed725065bce4998d08bddaf5f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719688"
---
# <a name="create-an-embedded-or-shared-data-source-ssrs"></a><span data-ttu-id="0bdb1-102">埋め込みデータ ソースまたは共有データ ソースを作成する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="0bdb1-102">Create an Embedded or Shared Data Source (SSRS)</span></span>
  <span data-ttu-id="0bdb1-103">レポートのデータ ソースは名前と接続情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-103">A report data source specifies a name and connection information.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="0bdb1-104">は、"埋め込み" と "共有" の 2 種類のデータ ソースをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-104">supports two types of data sources: embedded and shared.</span></span> <span data-ttu-id="0bdb1-105">埋め込みデータ ソースは、レポート定義内で定義され、そのレポートでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-105">An embedded data source is defined in a report definition and used only by that report.</span></span> <span data-ttu-id="0bdb1-106">共有データ ソースは、個別のアイテムとして定義され、複数のレポートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-106">A shared data source is defined as a separate item and can be used by multiple reports.</span></span> <span data-ttu-id="0bdb1-107">詳細については、「[埋め込みデータ接続または共有データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-107">For more information, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="0bdb1-108">レポート ビルダーで、レポート サーバーまたは SharePoint サイト上の保存先を参照してデータ ソースを選択するか、または埋め込みデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-108">In Report Builder, you browse to the report server or SharePoint site and select data sources or create embedded data sources.</span></span> <span data-ttu-id="0bdb1-109">共有データ ソースをレポート ビルダーで作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-109">You cannot create shared data sources in Report Builder.</span></span>  
  
 <span data-ttu-id="0bdb1-110">レポート デザイナーでは、共有データ ソースも埋め込みデータ ソースも作成できます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-110">In Report Designer, you can create shared or embedded data sources.</span></span> <span data-ttu-id="0bdb1-111">レポートデータペインからデータソース参照の作成を開始し、[**新規**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-111">From the Report Data pane, begin to create a data source reference, and then select the **New** option.</span></span> <span data-ttu-id="0bdb1-112">データ ソースの参照を作成すると、ソリューション エクスプローラーの [共有データ ソース] フォルダーに新しい共有データ ソースが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-112">After you create the data source reference, a new shared data source will automatically be added to Solution Explorer under the Shared Data Sources folder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="0bdb1-113">レポート サーバー上または SharePoint サイト上で共有データ ソースを直接作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-113">You can also create shared data sources directly on a report server or SharePoint site.</span></span> <span data-ttu-id="0bdb1-114">詳細については、「[共有データソースを作成、削除、または変更する &#40;レポートマネージャー&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) 」または「 [SharePoint 統合モードで Reporting Services &#40;共有データソースを作成および管理](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) or [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
### <a name="to-create-an-embedded-or-shared-data-source"></a><span data-ttu-id="0bdb1-115">埋め込みデータ ソースまたは共有データ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="0bdb1-115">To create an embedded or shared data source</span></span>  
  
1.  <span data-ttu-id="0bdb1-116">レポートデータペインのツールバーで、[**新規作成**] をクリックし、[**データソース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-116">On the toolbar in the Report Data pane, click **New** and then click **Data Source**.</span></span> <span data-ttu-id="0bdb1-117">**[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-117">The **Data Source Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0bdb1-118">レポート データ ペインが表示されていない場合は、 **[表示]** メニューの **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-118">If the Report Data pane is not visible, click **Report Data** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="0bdb1-119">**[名前]** ボックスにデータ ソースの名前を入力するか、既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-119">In the **Name** text box, type a name for the data source or accept the default.</span></span> <span data-ttu-id="0bdb1-120">データ ソース名は、レポートの内部で使用されます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-120">The data source name is used internally within the report.</span></span> <span data-ttu-id="0bdb1-121">判別がつきやすいように、データ ソース名には、接続文字列に指定するデータベース名を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-121">For clarity, we recommend that the name of the data source contain the name of the database specified in the connection string.</span></span>  
  
3.  <span data-ttu-id="0bdb1-122">埋め込みデータソースの場合は、[**埋め込み接続**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-122">For an embedded data source, verify that **Embedded connection** is selected.</span></span>  
  
    1.  <span data-ttu-id="0bdb1-123">**[種類]** ボックスの一覧から、データ ソースの種類 ( **[Microsoft SQL Server]** や **[OLE DB]** など) を選択します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-123">From the **Type** drop-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.</span></span>  
  
    2.  <span data-ttu-id="0bdb1-124">次の選択肢の 1 つを使用して、接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-124">Specify a connection string using one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="0bdb1-125">**[接続文字列]** ボックスに接続文字列を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-125">Type the connection string directly in the **Connection string** text box.</span></span> <span data-ttu-id="0bdb1-126">接続文字列の例の一覧については、「[レポートビルダーのデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)」または「データ[接続、データソース、Reporting Services の接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-126">For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) or [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
    -   <span data-ttu-id="0bdb1-127">式 (**[fx]** ) ボタンをクリックして、接続文字列を評価する式を作成します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-127">Click the expression (**fx)** button to create an expression that evaluates to a connection string.</span></span> <span data-ttu-id="0bdb1-128">**[式]** ダイアログ ボックスで、式ペインに式を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-128">In the **Expression** dialog box, type the expression in the Expression pane.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
    -   <span data-ttu-id="0bdb1-129">**[編集]** をクリックして、手順 2 で選択したデータ ソースの種類の **[接続のプロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-129">Click **Edit** to open the **Connection Properties** dialog box for the data source type you chose in step 2.</span></span>  
  
         <span data-ttu-id="0bdb1-130">データ ソースの種類に合わせて **[接続のプロパティ]** ダイアログ ボックスのフィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-130">Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type.</span></span> <span data-ttu-id="0bdb1-131">接続のプロパティには、データ ソースの種類、データ ソースの名前、および使用する資格情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-131">Connection properties include the type of data source, the name of the data source, and the credentials to use.</span></span> <span data-ttu-id="0bdb1-132">このダイアログ ボックスで値を指定した後、 **[接続テスト]** をクリックして、データ ソースが使用可能であること、および指定した資格情報が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-132">After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct.</span></span> <span data-ttu-id="0bdb1-133">特定のデータ ソースの種類の詳細については、「[外部データ ソースのデータを追加する (SSRS)](report-data/add-data-from-external-data-sources-ssrs.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-133">For more information about specific data source types, see topics in [Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="0bdb1-134">共有データソースの場合は、[**共有データソース参照を使用**する] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-134">For a shared data source, verify that **Use shared data source reference** is selected.</span></span>  
  
    1.  <span data-ttu-id="0bdb1-135">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-135">Click **New**.</span></span> <span data-ttu-id="0bdb1-136">**[共有データ ソース]** のプロパティ ダイアログ ボックスで、手順 2. および 3. を実行して新規データ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-136">In the **Shared Data Source** properties dialog box, follow steps 2 and 3 to create a new data source.</span></span>  
  
    2.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
         <span data-ttu-id="0bdb1-137">ソリューション エクスプローラーの [共有データ ソース] フォルダーに、新しい共有データ ソースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-137">The new shared data source appears in the Shared Data Sources folder in Solution Explorer.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="0bdb1-138">データ ソースがレポート データ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-138">The data source appears in the Report Data pane.</span></span> <span data-ttu-id="0bdb1-139">レポート データ ペイン内の共有データ ソースは、そのデータ ソースの定義を参照しています。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-139">In the Report Data pane, a shared data source points to the data source definition.</span></span> <span data-ttu-id="0bdb1-140">レポート ビルダーでは、データ ソースの定義は、レポート サーバー上または SharePoint サイト上に存在します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-140">In Report Builder, the data source definition is on a report server or SharePoint site.</span></span> <span data-ttu-id="0bdb1-141">レポート デザイナーでは、ソリューション エクスプローラーの [共有データ ソース] フォルダーにあるファイルがデータ ソースの定義です。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-141">In Report Designer, the data source definition is a file in Solution Explorer under the Shared Data Sources folder.</span></span>  
  
### <a name="to-import-an-existing-data-source-in-report-designer"></a><span data-ttu-id="0bdb1-142">レポート デザイナーで既存のデータ ソースをインポートするには</span><span class="sxs-lookup"><span data-stu-id="0bdb1-142">To import an existing data source in Report Designer</span></span>  
  
1.  <span data-ttu-id="0bdb1-143">ソリューション エクスプローラーで、レポート サーバー プロジェクトの **[共有データ ソース]** フォルダーを右クリックして、 **[既存項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-143">In Solution Explorer, right-click the **Shared Data Sources** folder in the report server project, and then click **Add Existing Item**.</span></span> <span data-ttu-id="0bdb1-144">**[既存項目の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-144">The **Add Existing Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="0bdb1-145">既存のレポート定義共有データ ソース (rds) ファイルを参照して、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-145">Navigate to an existing Report Definition Shared data source (rds) file and then click **Open**.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-convert-an-embedded-data-source-to-a-shared-data-source-in-report-designer"></a><span data-ttu-id="0bdb1-146">レポート デザイナーで埋め込みデータ ソースを共有データ ソースに変換するには</span><span class="sxs-lookup"><span data-stu-id="0bdb1-146">To convert an embedded data source to a shared data source in Report Designer</span></span>  
  
-   <span data-ttu-id="0bdb1-147">レポートデータペインでデータソースを右クリックし、[**共有データソースに変換**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-147">In the Report Data pane, right-click the data source and then click **Convert to Shared Data Source**.</span></span>  
  
### <a name="to-convert-a-shared-data-source-to-an-embedded-data-source-in-report-builder"></a><span data-ttu-id="0bdb1-148">レポート ビルダーで共有データ ソースを埋め込みデータ ソースに変換するには</span><span class="sxs-lookup"><span data-stu-id="0bdb1-148">To convert a shared data source to an embedded data source in Report Builder</span></span>  
  
-   <span data-ttu-id="0bdb1-149">レポートデータペインで、データソースを右クリックし、[**データソースのプロパティ**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-149">In the Report Data pane, right-click the data source and open **Data Source Properties**.</span></span>  
  
-   <span data-ttu-id="0bdb1-150">[**埋め込み接続**] をクリックし、前の手順で説明したように、埋め込みデータソースの作成を完了します。</span><span class="sxs-lookup"><span data-stu-id="0bdb1-150">Click **Embedded Connection** and finish creating the embedded data source as described in an earlier procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bdb1-151">参照</span><span class="sxs-lookup"><span data-stu-id="0bdb1-151">See Also</span></span>  
 <span data-ttu-id="0bdb1-152">[Reporting Services データソースへの資格情報の格納](report-data/store-credentials-in-a-reporting-services-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb1-152">[Store Credentials in a Reporting Services Data Source](report-data/store-credentials-in-a-reporting-services-data-source.md) </span></span>  
 <span data-ttu-id="0bdb1-153">[埋め込みデータ接続または共有データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb1-153">[Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0bdb1-154">[埋め込みデータソースから共有 &#40;レポートビルダーと SSRS に変換&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb1-154">[Convert a Data Source from Embedded to Shared &#40;Report Builder and SSRS&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0bdb1-155">[レポートまたはモデルの共有データソースへのバインド &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb1-155">[Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span></span>  
 <span data-ttu-id="0bdb1-156">[レポート &#40;レポートマネージャーのデータソースプロパティの構成&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb1-156">[Configure Data Source Properties for a Report  &#40;Report Manager&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md) </span></span>  
 [<span data-ttu-id="0bdb1-157">Reporting Services でサポートされるデータ ソース (SSRS)</span><span class="sxs-lookup"><span data-stu-id="0bdb1-157">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
