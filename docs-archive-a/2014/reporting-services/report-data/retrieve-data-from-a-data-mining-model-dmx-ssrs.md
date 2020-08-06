---
title: データ マイニング モデル (DMX) からデータを取得する (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- retrieving report data
- datasets [Reporting Services], with DMX queries
- datasets [Reporting Services], Analysis Services
- queries [Reporting Services], data mining prediction
ms.assetid: d9cd3624-1594-4707-8887-55437dd7e07c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a59184524967a9bfe772e41890afc3b900cc9e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738016"
---
# <a name="retrieve-data-from-a-data-mining-model-dmx-ssrs"></a><span data-ttu-id="628a6-102">データ マイニング モデル (DMX) からデータを取得する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="628a6-102">Retrieve Data from a Data Mining Model (DMX) (SSRS)</span></span>
  <span data-ttu-id="628a6-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ マイニング モデルのデータをレポートで使用するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースと 1 つ以上のレポート データセットを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="628a6-103">To use data from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data mining model in your report, you must define a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source and one or more report datasets.</span></span> <span data-ttu-id="628a6-104">データ ソース定義を作成する場合、クライアント コンピューターからデータ ソースにアクセスできるように接続文字列と資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="628a6-104">When you create the data source definition, you must specify a connection string and credentials so that you can access the data source from your client computer.</span></span>  
  
 <span data-ttu-id="628a6-105">単一のレポートで使用するように埋め込みデータ ソースの定義を作成することも、複数のレポートで使用できる共有データ ソースの定義を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="628a6-105">You can create an embedded data source definition for use by a single report or a shared data source definition that can be used by multiple reports.</span></span> <span data-ttu-id="628a6-106">このトピックでは、埋め込みデータ ソースを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="628a6-106">The procedures in this topic describe how to create an embedded data source.</span></span> <span data-ttu-id="628a6-107">共有データ ソースの詳細については、「[埋め込みデータ接続/データ ソースおよび共有データ接続/データ ソース (レポート ビルダーおよび SSRS)](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)」および「[共有データ ソースを作成、変更、および削除する (SSRS)](create-modify-and-delete-shared-data-sources-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="628a6-107">For more information about shared data sources, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) and [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
 <span data-ttu-id="628a6-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースを作成したら、1 つ以上のデータセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="628a6-108">After you create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, you can create one or more datasets.</span></span> <span data-ttu-id="628a6-109">データセットごとに、データ マイニング予測式 (DMX) クエリ デザイナーを使用して、フィールド コレクションを指定する DMX クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="628a6-109">For each dataset, you use a Data Mining Prediction Expression (DMX) query designer to create a DMX query that specifies the field collection.</span></span> <span data-ttu-id="628a6-110">詳細については、「 [Analysis Services の DMX クエリ デザイナーのユーザー インターフェイス](analysis-services-dmx-query-designer-user-interface.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="628a6-110">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).</span></span>  
  
 <span data-ttu-id="628a6-111">データセットを作成すると、そのデータセットの名前がデータ ソースの下のノードとしてレポート データ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="628a6-111">After you create a dataset, the name of the dataset appears in the Report Data pane as a node under its data source.</span></span>  
  
 <span data-ttu-id="628a6-112">レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="628a6-112">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
### <a name="to-create-an-embedded-microsoft-sql-server-analysis-services-data-source"></a><span data-ttu-id="628a6-113">埋め込み Microsoft SQL Server Analysis Services データ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="628a6-113">To create an embedded Microsoft SQL Server Analysis Services data source</span></span>  
  
1.  <span data-ttu-id="628a6-114">ツール バーのレポート データ ペインで、 **[新規作成]** 、 **[データ ソース]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="628a6-114">On the toolbar in the Report Data pane, click **New**, and then click **Data Source**.</span></span>  
  
2.  <span data-ttu-id="628a6-115">**[データ ソースのプロパティ]** ダイアログ ボックスの **[名前]** ボックスに名前を入力するか、既定の名前をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="628a6-115">In the **Data Source Properties** dialog box, type a name in the **Name** text box, or accept the default name.</span></span>  
  
3.  <span data-ttu-id="628a6-116">**[埋め込み接続]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="628a6-116">Verify that **Embedded connection** is selected.</span></span>  
  
4.  <span data-ttu-id="628a6-117">**[種類]** ボックスで、 **[Microsoft SQL Server Analysis Services]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="628a6-117">From the **Type** drop-down list, select **Microsoft SQL Server Analysis Services**.</span></span>  
  
5.  <span data-ttu-id="628a6-118">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースに使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="628a6-118">Specify a connection string that works with your [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span>  
  
     <span data-ttu-id="628a6-119">データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="628a6-119">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="628a6-120">ローカル クライアント上のサンプル [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] データベースを指定する接続文字列の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="628a6-120">The following connection string example specifies the sample [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] database on the local client.</span></span>  
  
    ```  
    Data Source=localhost;Initial Catalog=AdventureWorksDW2012  
    ```  
  
6.  <span data-ttu-id="628a6-121">**[資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628a6-121">Click **Credentials**.</span></span>  
  
     <span data-ttu-id="628a6-122">データ ソースへの接続に使用する資格情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="628a6-122">Set the credentials to use to connect to the data source.</span></span> <span data-ttu-id="628a6-123">詳細については、「 [レポート データ ソースに関する資格情報と接続情報を指定する](../../integration-services/connection-manager/data-sources.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="628a6-123">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="628a6-124">データ ソース接続をテストするには、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628a6-124">To test the data source connection, click **Edit**.</span></span> <span data-ttu-id="628a6-125">**[接続プロパティ]** ダイアログ ボックスで、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628a6-125">In the **Connection Properties** dialog box, click **Test Connection**.</span></span> <span data-ttu-id="628a6-126">テストが成功すると "接続テストに成功しました。" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="628a6-126">If the test is successful, you will see the information message "Test connection succeeded."</span></span> <span data-ttu-id="628a6-127">テストが失敗すると、その原因に関する詳しい情報を記載した警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="628a6-127">If the test fails, you will see a warning message with more information about why the test was not successful.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="628a6-128">データ ソースがレポート データ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="628a6-128">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-create-a-dataset-for-a-microsoft-sql-server-analysis-services"></a><span data-ttu-id="628a6-129">Microsoft SQL Server Analysis Services のデータセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="628a6-129">To create a dataset for a Microsoft SQL Server Analysis Services</span></span>  
  
1.  <span data-ttu-id="628a6-130">**[レポート データ]** ペインで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースに接続するデータ ソースの名前を右クリックし、 **[データセットの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628a6-130">In the **Report Data** pane, right-click the name of the data source that connects to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="628a6-131">**[データセットのプロパティ]** ダイアログ ボックスで、 **[名前]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="628a6-131">In the **Dataset Properties** dialog box, type a name in the **Name** text box.</span></span>  
  
3.  <span data-ttu-id="628a6-132">**[データ ソース]** ボックスに表示された名前が、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースに接続するデータ ソースの名前であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="628a6-132">In the **Data source box**, verify that the name is the name of a data source that connects to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span>  
  
4.  <span data-ttu-id="628a6-133">**[クエリ デザイナー]** をクリックしてグラフィカル クエリ デザイナーを開き、クエリを対話形式で作成します。</span><span class="sxs-lookup"><span data-stu-id="628a6-133">Click **Query Designer** to open the graphical query designer to build a query interactively.</span></span> <span data-ttu-id="628a6-134">クエリ デザイナーが MDX モードで開いた場合は、ツール バーの **[コマンドの種類 DMX]** (![DMX クエリ言語ビューに変更](../media/rsqdicon-commandtypedmx.gif "DMX クエリ言語ビューへの変更")) をクリックして、データ マイニング クエリ デザイナーに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="628a6-134">If the query designer opens in MDX mode, click **Command Type DMX** (![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")) on the toolbar to switch to the data mining query designer.</span></span> <span data-ttu-id="628a6-135">詳細については、「 [Analysis Services の DMX クエリ デザイナーのユーザー インターフェイス](analysis-services-dmx-query-designer-user-interface.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="628a6-135">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).</span></span>  
  
     <span data-ttu-id="628a6-136">代わりに、既存の DMX クエリを別のレポートからインポートするには、 **[インポート]** をクリックし、DMX クエリを使用して .rdl ファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="628a6-136">Alternatively, to import an existing DMX query from another report, click **Import**, and then navigate to the .rdl file with the DMX query.</span></span> <span data-ttu-id="628a6-137">.dmx ファイルからクエリをインポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="628a6-137">Importing a query from an .dmx file is not supported.</span></span>  
  
5.  <span data-ttu-id="628a6-138">クエリを作成して実行した後、サンプルの結果を表示するには **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628a6-138">After you create and run your query to see sample results, click **OK**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="628a6-139">データセットとそのフィールド コレクションがレポート データ ペインのデータ ソース ノードの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="628a6-139">The dataset and its field collection appear in the Report Data pane under the data source node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="628a6-140">参照</span><span class="sxs-lookup"><span data-stu-id="628a6-140">See Also</span></span>  
 <span data-ttu-id="628a6-141">[DMX のための Analysis Services の接続の種類 &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="628a6-141">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="628a6-142">[Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="628a6-142">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="628a6-143">[データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="628a6-143">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="628a6-144">レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="628a6-144">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
