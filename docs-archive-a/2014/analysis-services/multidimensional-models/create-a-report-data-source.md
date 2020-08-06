---
title: レポートデータソースを作成する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd6662c7-ffbe-479d-8944-3dc858340998
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9205eac497fc047b471f5b80becec36495474d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737045"
---
# <a name="create-a-report-data-source"></a><span data-ttu-id="2dab7-102">レポート データ ソースの作成</span><span class="sxs-lookup"><span data-stu-id="2dab7-102">Create a Report Data Source</span></span>
  <span data-ttu-id="2dab7-103">Power View が多次元モデルに接続するためには、共有レポート データ ソース定義 (.rsds ファイル) を SharePoint ライブラリに作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dab7-103">In order for Power View to connect to a multidimensional model, you must create a shared report data source definition, also known as an .rsds file, in a SharePoint library.</span></span> <span data-ttu-id="2dab7-104">.rsds ファイルは、多次元モデルへの接続に使用する Analysis Services サーバー インスタンスの名前、接続の種類、接続文字列、および資格情報の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-104">The .rsds file specifies the name of an Analysis Services server instance, connection type, connection string, and credentials used to connect to the multidimensional model.</span></span> <span data-ttu-id="2dab7-105">ユーザーが .rsds ファイルをクリックすると、新しい空白の Power View レポート (.rdlx ファイル) がブラウザーで開きます。</span><span class="sxs-lookup"><span data-stu-id="2dab7-105">When a user clicks on the .rsds, a new blank Power View report (an .rdlx file) opens in the browser.</span></span>  
  
 <span data-ttu-id="2dab7-106">.rsds 接続を作成するには、SQL Server 2012 (以降) Reporting Services および SharePoint 2010 または SharePoint 2013 の Reporting Services アドインがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dab7-106">In order to create an .rsds connection, you must have SQL Server 2012 (or later) Reporting Services and the Reporting Services add-in for SharePoint 2010 or SharePoint 2013 installed.</span></span>  
  
## <a name="create-a-report-data-source-rsds-connection-to-a-multidimensional-model"></a><span data-ttu-id="2dab7-107">多次元モデルへのレポート モデル ソース (.rsds) 接続を作成する</span><span class="sxs-lookup"><span data-stu-id="2dab7-107">Create a Report Data Source (.rsds) connection to a multidimensional model</span></span>  
 <span data-ttu-id="2dab7-108">開始する前に以下を調べます。</span><span class="sxs-lookup"><span data-stu-id="2dab7-108">Before you begin, you need to know:</span></span>  
  
-   <span data-ttu-id="2dab7-109">多次元モードで実行中の Analysis Services サーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="2dab7-109">The name of the Analysis Services server instance running in Multidimensional mode.</span></span>  
  
-   <span data-ttu-id="2dab7-110">接続先の多次元データベースの名前。</span><span class="sxs-lookup"><span data-stu-id="2dab7-110">The name of the multidimensional database you want to connect to.</span></span>  
  
-   <span data-ttu-id="2dab7-111">キューブの名前 (複数存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="2dab7-111">The name of the cube, if there is more than one.</span></span>  
  
-   <span data-ttu-id="2dab7-112">(オプション) パースペクティブ名。</span><span class="sxs-lookup"><span data-stu-id="2dab7-112">(Optional) Perspective name.</span></span>  
  
-   <span data-ttu-id="2dab7-113">(オプション) ロケール識別子</span><span class="sxs-lookup"><span data-stu-id="2dab7-113">(Optional) Locale Identifier.</span></span>  
  
#### <a name="to-create-a-shared-report-data-source-rsds-file-sharepoint-2010"></a><span data-ttu-id="2dab7-114">共有レポート データ ソース (.rsds) ファイルを作成するには (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="2dab7-114">To create a shared Report Data Source (.rsds) file (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="2dab7-115">ライブラリ リボンで、 **[ドキュメント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dab7-115">Click the **Documents** tab on the library ribbon.</span></span>  
  
2.  <span data-ttu-id="2dab7-116">[**新しいドキュメント**] [  >  **レポートデータソース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dab7-116">Click **New Document** > **Report Data Source**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2dab7-117">メニューに **[レポート データ ソース]** アイテムが表示されない場合は、このライブラリに対してレポート データ ソースのコンテンツ タイプが有効化されていません。</span><span class="sxs-lookup"><span data-stu-id="2dab7-117">If you do not see the **Report Data Source** item on the menu, the report data source content type has not been enabled for this library.</span></span> <span data-ttu-id="2dab7-118">詳細については、「 [SharePoint 統合モードでのレポートサーバーコンテンツタイプのライブラリへの追加 &#40;Reporting Services」&#41;](../../reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dab7-118">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
3.  <span data-ttu-id="2dab7-119">**[データ ソースのプロパティ]** ページの **[名前]** に、接続 .rsds ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-119">On the **Data Source Properties** page, in **Name**, type a name for the connection .rsds file.</span></span>  
  
4.  <span data-ttu-id="2dab7-120">**[データ ソースの種類]** で **[Power View 用 Microsoft BI セマンティック モデル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dab7-120">In **Data Source Type**, select **Microsoft BI Semantic Model for Power View**.</span></span>  
  
5.  <span data-ttu-id="2dab7-121">**[接続文字列]** で、Analysis Services サーバー名、データベース名、キューブ名、およびオプションの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-121">In **Connection String**, specify the Analysis Services server name, database name, cube name, and any optional settings.</span></span>  
  
     <span data-ttu-id="2dab7-122">接続文字列: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'`</span><span class="sxs-lookup"><span data-stu-id="2dab7-122">Connection String: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'`</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2dab7-123">複数のキューブがある場合は、キューブの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dab7-123">If there is more than one cube, you must specify a cube name.</span></span>  
  
     <span data-ttu-id="2dab7-124">(オプション) 特定のディメンションまたはメジャー グループのみがクライアントに表示されている場合、ユーザーに選択ビューを提供するパースペクティブをキューブに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2dab7-124">(Optional) Cubes can have perspectives that provide users a select view where only certain dimensions and/or measure groups are visible in the client.</span></span> <span data-ttu-id="2dab7-125">パースペクティブを指定するには、次のように、キューブのプロパティにパースペクティブ名を値として入力します。 `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<perspectivename>'`</span><span class="sxs-lookup"><span data-stu-id="2dab7-125">To specify a perspective, enter the perspective name as a value to the Cube property: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<perspectivename>'`</span></span>  
  
     <span data-ttu-id="2dab7-126">(オプション) キューブには、モデル内でさまざまな言語に指定されたメタデータとデータの翻訳を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2dab7-126">(Optional) Cubes can have metadata and data translations specified for various languages within the model.</span></span> <span data-ttu-id="2dab7-127">翻訳 (データとメタデータ) を表示するには、接続文字列に "Locale Identifier" プロパティを追加する必要があります。`Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'; Locale Identifier=<identifier number>`</span><span class="sxs-lookup"><span data-stu-id="2dab7-127">In order to see the translations (data and metadata) you need to add the "Locale Identifier" property to the connection string: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'; Locale Identifier=<identifier number>`</span></span>  
  
6.  <span data-ttu-id="2dab7-128">**[資格情報]** で、外部データ ソースにアクセスする際にレポート サーバーが資格情報を取得する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-128">In **Credentials**, specify how the report server obtains credentials to access the external data source.</span></span>  
  
    -   <span data-ttu-id="2dab7-129">レポートを開いたユーザーの資格情報を使用してデータにアクセスする場合は、 **[Windows 認証 (統合)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-129">Select **Windows authentication (integrated)** if you want to access the data using the credentials of the user who opened the report.</span></span> <span data-ttu-id="2dab7-130">SharePoint サイトまたはファームでフォーム認証を使用する場合や、信頼済みアカウントを使用してレポート サーバーに接続する場合は、このオプションを選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="2dab7-130">Do not select this option if the SharePoint site or farm uses forms authentication or connects to the report server through a trusted account.</span></span> <span data-ttu-id="2dab7-131">このレポートのサブスクリプションまたはデータ処理をスケジュールする場合は、このオプションを選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="2dab7-131">Do not select this option if you want to schedule subscription or data processing for this report.</span></span> <span data-ttu-id="2dab7-132">Kerberos 認証が有効なドメインに参加している場合、またはレポート サーバーと同一のコンピューターにデータ ソースがある場合に、このオプションは最適です。</span><span class="sxs-lookup"><span data-stu-id="2dab7-132">This option works best when Kerberos authentication is enabled for your domain, or when the data source is on the same computer as the report server.</span></span> <span data-ttu-id="2dab7-133">Kerberos 認証が無効になっている場合、Windows 資格情報は別のコンピューター 1 台にしか渡すことができません。</span><span class="sxs-lookup"><span data-stu-id="2dab7-133">If Kerberos authentication is not enabled, Windows credentials can only be passed to one other computer.</span></span> <span data-ttu-id="2dab7-134">つまり、外部データ ソースが別のコンピューターにあり、別の接続が必要な場合、意図したデータを取得できずにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-134">This means that if the external data source is on another computer, requiring an additional connection, you will get an error instead of the data you expect.</span></span>  
  
    -   <span data-ttu-id="2dab7-135">ユーザーがレポートを実行するたびに資格情報の入力を要求する場合は、 **[資格情報を要求する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dab7-135">Select **Prompt for credentials** if you want the user to enter his or her credentials each time he or she runs the report.</span></span> <span data-ttu-id="2dab7-136">このレポートのサブスクリプションまたはデータ処理をスケジュールする場合は、このオプションを選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="2dab7-136">Do not select this option if you want to schedule subscription or data processing for this report.</span></span>  
  
    -   <span data-ttu-id="2dab7-137">1 組の資格情報を使用してデータにアクセスする場合は、 **[保存された資格情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-137">Select **Stored credentials** if you want to access the data using a single set of credentials.</span></span> <span data-ttu-id="2dab7-138">資格情報は暗号化されてから保存されます。</span><span class="sxs-lookup"><span data-stu-id="2dab7-138">The credentials are encrypted before they are stored.</span></span> <span data-ttu-id="2dab7-139">保存されている資格情報の認証方法を指定するオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2dab7-139">You can select options that determine how the stored credentials are authenticated.</span></span> <span data-ttu-id="2dab7-140">保存された資格情報が Windows ユーザー アカウントに属する場合は、[データ ソースへの接続時に Windows 資格情報として使用する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dab7-140">Select Use as Windows credentials if the stored credentials belong to a Windows user account.</span></span> <span data-ttu-id="2dab7-141">データベース サーバーの実行コンテキストを設定する場合は、 **[実行コンテキストをこのアカウントに設定する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dab7-141">Select **Set execution context to this account** if you want to set the execution context on the database server.</span></span>  
  
    -   <span data-ttu-id="2dab7-142">接続文字列で資格情報を指定する場合や、最小特権アカウントを使用してレポートを実行する場合は、 **[資格情報は必要ありません]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dab7-142">Select **Credentials are not required** if you specify credentials in the connection string, or if you want to run the report using a least-privilege account.</span></span>  
  
7.  <span data-ttu-id="2dab7-143">**[接続テスト]** をクリックして検証します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-143">Click **Test Connection** to validate.</span></span>  
  
8.  <span data-ttu-id="2dab7-144">データ ソースをアクティブにする場合は、 **[このデータ ソースを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2dab7-144">Select **Enable this data source** if you want the data source to be active.</span></span> <span data-ttu-id="2dab7-145">データ ソースが構成されていてもアクティブでない場合は、ユーザーがレポートを作成しようとするとエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dab7-145">If the data source is configured but not active, users will receive an error message when they attempt to create a report.</span></span>  
  
  
