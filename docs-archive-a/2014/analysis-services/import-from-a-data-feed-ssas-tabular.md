---
title: データフィードからのインポート (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0686e519-67c2-4f9b-8cd2-84a4871499ee
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7e5446effdcd01a3fe0eeb5dd14a1a61e97c417b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645238"
---
# <a name="import-from-a-data-feed-ssas-tabular"></a><span data-ttu-id="84b99-102">データ フィードからのインポート (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="84b99-102">Import from a Data Feed (SSAS Tabular)</span></span>
  <span data-ttu-id="84b99-103">データ フィードは、オンライン データ ソースから生成され、宛先のドキュメントやアプリケーションに送信される 1 つ以上の XML データ ストリームです。</span><span class="sxs-lookup"><span data-stu-id="84b99-103">Data feeds are one or more XML data streams that are generated from an online data source and streamed to a destination document or application.</span></span> <span data-ttu-id="84b99-104">テーブルのインポート ウィザードを使用して、データ フィードからモデルにデータをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-104">You can import data from a data feed into your model by using the Table Import Wizard.</span></span>  
  
 <span data-ttu-id="84b99-105">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="84b99-105">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="84b99-106">データ フィードからのインポートについて</span><span class="sxs-lookup"><span data-stu-id="84b99-106">Understanding import from a data feed</span></span>](#prereq)  
  
-   [<span data-ttu-id="84b99-107">Azure DataMarket データセットからのデータのインポート</span><span class="sxs-lookup"><span data-stu-id="84b99-107">Import data from an Azure DataMarket dataset</span></span>](#azure)  
  
-   [<span data-ttu-id="84b99-108">パブリックまたは企業データのソースからのデータ フィードのインポート</span><span class="sxs-lookup"><span data-stu-id="84b99-108">Import data feeds from public or corporate data sources</span></span>](#importdata)  
  
-   [<span data-ttu-id="84b99-109">SharePoint リストからのデータ フィードのインポート</span><span class="sxs-lookup"><span data-stu-id="84b99-109">Import data feeds from SharePoint lists</span></span>](#importlist)  
  
-   [<span data-ttu-id="84b99-110">Reporting Services レポートからのデータ フィードのインポート</span><span class="sxs-lookup"><span data-stu-id="84b99-110">Import data feeds from Reporting Services Reports</span></span>](#importreport)  
  
##  <a name="understanding-import-from-a-data-feed"></a><a name="prereq"></a><span data-ttu-id="84b99-111">データフィードからのインポートについて</span><span class="sxs-lookup"><span data-stu-id="84b99-111">Understanding import from a data feed</span></span>  
 <span data-ttu-id="84b99-112">次の種類のデータ フィードからテーブル モデルにデータをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-112">You can import data into a Tabular Model from the following types of data feeds:</span></span>  
  
 <span data-ttu-id="84b99-113">**Reporting Services レポート**</span><span class="sxs-lookup"><span data-stu-id="84b99-113">**Reporting Services Report**</span></span>  
 <span data-ttu-id="84b99-114">モデル内のデータ ソースとして SharePoint サイトまたはレポート サーバーにパブリッシュされた Reporting Services レポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-114">You can use a Reporting Services report that has been published to a SharePoint site or a report server as a data source in a model.</span></span> <span data-ttu-id="84b99-115">Reporting Services レポートからデータをインポートするときは、データ ソースとしてレポート定義 (.rdl) ファイルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84b99-115">When importing data from a Reporting Services Report, you must specify a report definition (.rdl) file as a data source.</span></span>  
  
 <span data-ttu-id="84b99-116">**Azure DataMarket データセット**</span><span class="sxs-lookup"><span data-stu-id="84b99-116">**Azure DataMarket Dataset**</span></span>  
 <span data-ttu-id="84b99-117">Azure DataMarket は、クラウド サービスとして情報の 1 つのマーケットプレースと配信チャネルを提供するサービスです。</span><span class="sxs-lookup"><span data-stu-id="84b99-117">Azure DataMarket is a service that provides a single marketplace and delivery channel for information as cloud services.</span></span> <span data-ttu-id="84b99-118">Azure DataMarket データセットでは、Windows ユーザー アカウントではなくアカウント キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="84b99-118">Azure DataMarket datasets require an account key instead of a Windows user account.</span></span>  
  
 <span data-ttu-id="84b99-119">**Atom フィード**</span><span class="sxs-lookup"><span data-stu-id="84b99-119">**Atom feeds**</span></span>  
 <span data-ttu-id="84b99-120">フィードは Atom フィードである必要があります。</span><span class="sxs-lookup"><span data-stu-id="84b99-120">The feed must be an Atom feed.</span></span> <span data-ttu-id="84b99-121">RSS フィードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="84b99-121">RSS feeds are not supported.</span></span> <span data-ttu-id="84b99-122">フィードが一般公開されているか、現在ログインしている Windows アカウントでそのフィードに接続するための権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="84b99-122">The feed must either be publicly available or you must have permission to connect to it under the Windows account with which you are currently logged in.</span></span>  
  
 <span data-ttu-id="84b99-123">インポート時に、データ フィードからのデータがモデルに 1 回追加されます。</span><span class="sxs-lookup"><span data-stu-id="84b99-123">Data from a data feed is added into a model once during import.</span></span> <span data-ttu-id="84b99-124">フィードから更新済みデータを取得するには、モデル デザイナーからデータを更新するか、Analysis Services の実稼動インスタンスに配置後にモデルのデータ更新スケジュールを構成するかします。</span><span class="sxs-lookup"><span data-stu-id="84b99-124">To get updated data from the feed, you can either refresh the data from the model designer, or configure a data refresh schedule for the model after it is deployed to a production instance of Analysis Services.</span></span> <span data-ttu-id="84b99-125">詳細については、「 [データの処理 (SSAS テーブル)](process-data-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84b99-125">For more information, see [Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md).</span></span>  
  
##  <a name="import-data-from-an-azure-datamarket-dataset"></a><a name="azure"></a><span data-ttu-id="84b99-126">Azure DataMarket データセットからのデータのインポート</span><span class="sxs-lookup"><span data-stu-id="84b99-126">Import data from an Azure DataMarket dataset</span></span>  
 <span data-ttu-id="84b99-127">モデル内のテーブルとして Azure DataMarket からデータをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-127">You can import data from an Azure DataMarket as a table in your model.</span></span>  
  
#### <a name="to-import-data-from-an-azure-datamarket-dataset"></a><span data-ttu-id="84b99-128">Azure DataMarket データセットからデータをインポートするには</span><span class="sxs-lookup"><span data-stu-id="84b99-128">To import data from an Azure DataMarket dataset</span></span>  
  
1.  <span data-ttu-id="84b99-129">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span> <span data-ttu-id="84b99-130">テーブルのインポート ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84b99-130">The Table Import Wizard opens.</span></span>  
  
2.  <span data-ttu-id="84b99-131">**[データ ソースへの接続]** ページの **[データ フィード]** で、 **[Azure DataMarket データセット]** をクリックしてから **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-131">On the **Connect to a Data Source** page, under **Data Feeds**, select **Azure DataMarket Dataset**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="84b99-132">**[表示名]** の **[Azure DataMarket データセットへの接続]** ページに、アクセスするフィードに付けるわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-132">On the **Connect to an Azure DataMarket dataset** page, in **Friendly Name**, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="84b99-133">複数のフィードまたはデータ ソースをインポートする場合、接続を表す名前を使用すると、接続の使用方法の識別に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="84b99-133">If you are importing multiple feeds or data sources, using descriptive names for the connection can help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="84b99-134">**[データ フィード URL]** にデータ フィードのアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-134">In **Data Feed URL**, type the address for the data feed.</span></span>  
  
5.  <span data-ttu-id="84b99-135">**[アカウント キー]** の **[セキュリティ設定]** にアカウント キーを入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-135">In **Security Settings**, in **Account Key**, type an account key.</span></span> <span data-ttu-id="84b99-136">アカウント キーは、Analysis Services が DataMarket サブスクリプションにアクセスするときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="84b99-136">Account keys are used by Analysis Services to access the DataMarket subscriptions.</span></span>  
  
6.  <span data-ttu-id="84b99-137">**[接続テスト]** をクリックして、フィードが使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="84b99-137">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="84b99-138">または、 **[詳細設定]** をクリックして、ベース URL またはサービス ドキュメント URL に、フィードを提供するクエリまたはサービス ドキュメントが含まれていることを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-138">Alternatively, you can also click **Advanced** to confirm that the Base URL or Service Document URL contains the query or service document that provides the feed.</span></span>  
  
7.  <span data-ttu-id="84b99-139">インポートを続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-139">Click **Next** to continue with the import.</span></span>  
  
8.  <span data-ttu-id="84b99-140">**[権限借用情報]** ページで、データを更新するときに Analysis Services がデータ ソースへの接続に使用する資格情報を指定し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-140">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span> <span data-ttu-id="84b99-141">これらの資格情報はアカウント キーとは異なります。</span><span class="sxs-lookup"><span data-stu-id="84b99-141">These credentials are different from the Account Key.</span></span>  
  
9. <span data-ttu-id="84b99-142">ウィザードの **[テーブルとビューの選択]** ページの **[表示名]** フィールドに、インポート後にこのデータを含むテーブルを識別するわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-142">In the **Select Tables and Views** page of the wizard, in the **Friendly Name** field, type a descriptive name that identifies the table that will contain this data after it is imported</span></span>  
  
10. <span data-ttu-id="84b99-143">**[プレビューとフィルター]** をクリックしてデータを確認し、列の選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="84b99-143">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="84b99-144">レポートのデータ フィードでインポートされる行を制限することはできませんが、チェック ボックスをオフにすることで列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-144">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="84b99-145">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-145">Click **OK**.</span></span>  
  
11. <span data-ttu-id="84b99-146">**[テーブルとビューの選択]** ページで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-146">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-public-or-corporate-data-sources"></a><a name="importdata"></a><span data-ttu-id="84b99-147">パブリックまたは企業のデータソースからデータフィードをインポートする</span><span class="sxs-lookup"><span data-stu-id="84b99-147">Import data feeds from public or corporate data sources</span></span>  
 <span data-ttu-id="84b99-148">パブリック フィードにアクセスするか、または専用または従来のデータベース システムから Atom フィードを生成するカスタム データ サービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-148">You can access public feeds or build custom data services that generate Atom feeds from proprietary or legacy database systems.</span></span>  
  
#### <a name="to-import-data-from-public-or-corporate-data-feeds"></a><span data-ttu-id="84b99-149">パブリックまたは企業データ フィードからデータをインポートするには</span><span class="sxs-lookup"><span data-stu-id="84b99-149">To import data from public or corporate data feeds</span></span>  
  
1.  <span data-ttu-id="84b99-150">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-150">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span> <span data-ttu-id="84b99-151">テーブルのインポート ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84b99-151">The Table Import Wizard opens.</span></span>  
  
2.  <span data-ttu-id="84b99-152">**[データ ソースへの接続]** ページの **[データ フィード]** で、 **[他のフィード]** をクリックしてから **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-152">On the **Connect to a Data Source** page, under **Data Feeds**, select **Other Feeds**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="84b99-153">**[データ フィードへの接続]** ページに、アクセスするフィードに付けるわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-153">On the **Connect to a Data Feed** page, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="84b99-154">複数のフィードまたはデータ ソースをインポートする場合、接続を表す名前を使用すると、接続の使用方法の識別に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="84b99-154">If you are importing multiple feeds or data sources, using descriptive names for the connection can help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="84b99-155">**[データ フィード URL]** にデータ フィードのアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-155">In **Data Feed URL**, type the address for the data feed.</span></span> <span data-ttu-id="84b99-156">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="84b99-156">Valid values include the following:</span></span>  
  
    1.  <span data-ttu-id="84b99-157">Atom データを含む XML ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="84b99-157">An XML document that contains the Atom data.</span></span> <span data-ttu-id="84b99-158">たとえば、次の URL は Open Government Data Initiative Web サイトのパブリック フィードを指します。</span><span class="sxs-lookup"><span data-stu-id="84b99-158">For example, the following URL points to a public feed on the Open Government Data Initiative web site:</span></span>  
  
        ```  
        http://ogdi.cloudapp.net/v1/dc/banklocations/  
        ```  
  
    2.  <span data-ttu-id="84b99-159">1 つ以上のフィードを指定する .atomsvc ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="84b99-159">An .atomsvc document that specifies one or more feeds.</span></span> <span data-ttu-id="84b99-160">.atomsvc ドキュメントは、1 つ以上のフィードを提供するサービスまたはアプリケーションを指します。</span><span class="sxs-lookup"><span data-stu-id="84b99-160">An .atomsvc document points to a service or application that provides one or more feeds.</span></span> <span data-ttu-id="84b99-161">各フィードは、結果セットを返すベース クエリとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="84b99-161">Each feed is specified as a base query that returns the result set.</span></span>  
  
         <span data-ttu-id="84b99-162">Web サーバー上の .atomsvc ドキュメントに対する URL アドレスを指定するか、またはコンピューター上の共有フォルダーまたはローカル フォルダーからファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="84b99-162">You can specify a URL address to an .atomsvc document that is on a web server or you can open the file from a shared or local folder on your computer.</span></span> <span data-ttu-id="84b99-163">Reporting Services レポートをエクスポートしている間にコンピューターに保存した .atomsvc ドキュメント、または SharePoint サイトに対して作成されたデータ フィード ライブラリ内の .atomsvc ドキュメントが存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84b99-163">You might have an .atomsvc document if you saved one to your computer while exporting a Reporting Services report, or you might have .atomsvc documents in a data feed library that someone created for your SharePoint site.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="84b99-164">URL アドレスまたは共有フォルダーを介してアクセスできる .atomsvc ドキュメントを指定することをお勧めします。これは、SharePoint へのブックのパブリッシュ後に、後でブックの自動データ更新を設定するオプションが提供されるためです。</span><span class="sxs-lookup"><span data-stu-id="84b99-164">Specifying an .atomsvc document that can be accessed through a URL address or shared folder is recommended because it gives you the option of configuring automatic data refresh for the workbook later, after the workbook is published to SharePoint.</span></span> <span data-ttu-id="84b99-165">コンピューター上のローカルな場所でない場所が指定されていれば、サーバーは、同じ URL アドレスまたはネットワーク フォルダーを再使用してデータを更新できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-165">The server can re-use the same URL address or network folder to refresh data if you specify a location that is not local to your computer.</span></span>  
  
5.  <span data-ttu-id="84b99-166">**[接続テスト]** をクリックして、フィードが使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="84b99-166">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="84b99-167">または、 **[詳細設定]** をクリックして、ベース URL またはサービス ドキュメント URL に、フィードを提供するクエリまたはサービス ドキュメントが含まれていることを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-167">Alternatively, you can also click **Advanced** to confirm that the Base URL or Service Document URL contains the query or service document that provides the feed.</span></span>  
  
6.  <span data-ttu-id="84b99-168">インポートを続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-168">Click **Next** to continue with the import.</span></span>  
  
7.  <span data-ttu-id="84b99-169">**[権限借用情報]** ページで、データを更新するときに Analysis Services がデータ ソースへの接続に使用する資格情報を指定し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-169">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="84b99-170">ウィザードの **[テーブルとビューの選択]** ページの **[表示名]** フィールドで、データ フィード コンテンツを、インポート後にこのデータが格納されるテーブルを表す名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="84b99-170">In the **Select Tables and Views** page of the wizard, in the **Friendly Name** field, replace Data Feed Content with a descriptive name that identifies the table that will contain this data after it is imported</span></span>  
  
9. <span data-ttu-id="84b99-171">**[プレビューとフィルター]** をクリックしてデータを確認し、列の選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="84b99-171">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="84b99-172">レポートのデータ フィードでインポートされる行を制限することはできませんが、チェック ボックスをオフにすることで列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-172">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="84b99-173">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-173">Click **OK**.</span></span>  
  
10. <span data-ttu-id="84b99-174">**[テーブルとビューの選択]** ページで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-174">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-sharepoint-lists"></a><a name="importlist"></a><span data-ttu-id="84b99-175">SharePoint リストからデータフィードをインポートする</span><span class="sxs-lookup"><span data-stu-id="84b99-175">Import data feeds from SharePoint lists</span></span>  
 <span data-ttu-id="84b99-176">(SharePoint) リボンに **[データ フィードとしてエクスポート]** ボタンを持つ SharePoint リストをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-176">You can import any SharePoint list that has an **Export as Data Feed** button on the (SharePoint) ribbon.</span></span> <span data-ttu-id="84b99-177">このボタンをクリックすると、リストをフィードとしてエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-177">You can click this button to export the list as a feed.</span></span>  
  
#### <a name="to-import-data-feeds-from-a-sharepoint-list"></a><span data-ttu-id="84b99-178">SharePoint リストからデータ フィードをインポートするには</span><span class="sxs-lookup"><span data-stu-id="84b99-178">To import data feeds from a SharePoint list</span></span>  
  
1.  <span data-ttu-id="84b99-179">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-179">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="84b99-180">**[データ ソースへの接続]** ページの **[データ フィード]** で、 **[他のデータ フィード]** をクリックしてから **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-180">On the **Connect to a Data Source** page, under **Data Feeds**, select **Other Data Feeds**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="84b99-181">**[データ フィードへの接続]** ページに、アクセスするフィードに付けるわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-181">On the **Connect to a Data Feed** page, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="84b99-182">複数のフィードまたはデータ ソースをインポートする場合、接続を表す名前を使用すると、接続の使用方法の識別に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="84b99-182">If you are importing multiple feeds or data sources, using descriptive names for the connection might help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="84b99-183">[データフィード URL] に、リストデータサービスへのアドレスを入力し \<server-name> ます。の部分は、実際の SharePoint サーバーの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="84b99-183">In Data Feed URL, type an address to the list data service, replacing \<server-name> with the actual name of your SharePoint server:</span></span>  
  
    ```  
    http://<server-name>/_vti_bin/listdata.svc  
    ```  
  
5.  <span data-ttu-id="84b99-184">**[接続テスト]** をクリックして、フィードが使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="84b99-184">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="84b99-185">または、 **[詳細設定]** をクリックして、サービス ドキュメント URL に、リスト データ サービスのアドレスが含まれていることを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-185">Alternatively, you can also click **Advanced** to confirm that the Service Document URL contains an address to the list data service.</span></span>  
  
6.  <span data-ttu-id="84b99-186">インポートを続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-186">Click **Next** to continue with the import.</span></span>  
  
7.  <span data-ttu-id="84b99-187">**[権限借用情報]** ページで、データを更新するときに Analysis Services がデータ ソースへの接続に使用する資格情報を指定し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-187">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="84b99-188">ウィザードの **[テーブルとビューの選択]** ページで、インポートするリストを選択します。</span><span class="sxs-lookup"><span data-stu-id="84b99-188">In the **Select Tables and Views** page of the wizard, select the lists you want to import.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84b99-189">列を含むリストのみをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-189">You can only import lists that contain columns.</span></span>  
  
9. <span data-ttu-id="84b99-190">**[プレビューとフィルター]** をクリックしてデータを確認し、列の選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="84b99-190">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="84b99-191">レポートのデータ フィードでインポートされる行を制限することはできませんが、チェック ボックスをオフにすることで列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-191">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="84b99-192">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-192">Click **OK**.</span></span>  
  
10. <span data-ttu-id="84b99-193">**[テーブルとビューの選択]** ページで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-193">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-reporting-services-reports"></a><a name="importreport"></a><span data-ttu-id="84b99-194">Reporting Services レポートからのデータフィードのインポート</span><span class="sxs-lookup"><span data-stu-id="84b99-194">Import data feeds from Reporting Services Reports</span></span>  
 <span data-ttu-id="84b99-195">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services を配置している場合は、Atom 表示拡張機能を使用して既存のレポートからデータ フィードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-195">If you have a deployment of [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services, you can use the Atom rendering extension to generate a data feed from an existing report.</span></span>  
  
#### <a name="to-import-report-data-from-a-published-reporting-services-report"></a><span data-ttu-id="84b99-196">パブリッシュされた Reporting Services レポートからレポート データをインポートするには</span><span class="sxs-lookup"><span data-stu-id="84b99-196">To import report data from a published Reporting Services report</span></span>  
  
1.  <span data-ttu-id="84b99-197">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-197">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="84b99-198">**[データ ソースへの接続]** ページの **[データ フィード]** で、 **[レポート]** をクリックしてから **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-198">On the **Connect to a Data Source** page, under **Data Feeds**, select **Report**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="84b99-199">[Microsoft SQL Server Reporting Services レポートへの接続] ページで、[接続の表示名] に、アクセスするフィードに付けるわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-199">On the Connect to a Microsoft SQL Server Reporting Services Report page, in Friendly Connection Name, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="84b99-200">複数のデータ ソースをインポートする場合、接続を表す名前を使用すると、接続の使用方法の識別に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="84b99-200">If you are importing multiple data sources, using descriptive names for the connection might help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="84b99-201">**[参照]** をクリックし、レポート サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="84b99-201">Click **Browse** and select a report server.</span></span>  
  
     <span data-ttu-id="84b99-202">特定のレポート サーバーに関するレポートを定期的に使用している場合は、 **[最近使ったサイトとサーバー]** にそのサーバーが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84b99-202">If you regularly use reports on a report server, the server might be listed in **Recent Sites and Servers**.</span></span> <span data-ttu-id="84b99-203">それ以外の場合は、レポート サーバーのアドレスを [名前] に入力し、 **[開く]** をクリックして、レポート サーバー サイトのフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="84b99-203">Otherwise, in Name, type an address to a report server and click **Open** to browse the folders on the report server site.</span></span> <span data-ttu-id="84b99-204">レポートサーバーのアドレスの例としては、http://があり \<computername> ます。</span><span class="sxs-lookup"><span data-stu-id="84b99-204">An example address for a report server might be http://\<computername>/reportserver.</span></span>  
  
5.  <span data-ttu-id="84b99-205">レポートを選択し、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-205">Select the report and click **Open**.</span></span> <span data-ttu-id="84b99-206">代わりに、 **[名前]** ボックスに完全パスとレポート名を含むレポートへのリンクを貼り付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="84b99-206">Alternatively, you can paste a link to the report, including the full path and report name, in the **Name** text box.</span></span> <span data-ttu-id="84b99-207">テーブルのインポート ウィザードによってレポートに接続され、プレビュー領域にそれが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84b99-207">The Table Import wizard connects to the report and renders it in the preview area.</span></span>  
  
     <span data-ttu-id="84b99-208">レポートでパラメーターが使用されている場合は、パラメーターを指定しないとレポート接続を作成できません。</span><span class="sxs-lookup"><span data-stu-id="84b99-208">If the report uses parameters, you must specify a parameter or you cannot create the report connection.</span></span> <span data-ttu-id="84b99-209">パラメーターを指定すると、そのパラメーター値に関連する行だけがデータ フィードでインポートされます。</span><span class="sxs-lookup"><span data-stu-id="84b99-209">When you do so, only the rows related to the parameter value are imported in the data feed.</span></span>  
  
    1.  <span data-ttu-id="84b99-210">レポートのリスト ボックスまたはコンボ ボックスを使用してパラメーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="84b99-210">Choose a parameter using the list box or combo box provided in the report.</span></span>  
  
    2.  <span data-ttu-id="84b99-211">**[レポートの表示]** をクリックしてデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="84b99-211">Click **View Report** to update the data.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="84b99-212">レポートを表示すると、選択したパラメーターがデータ フィードの定義と共に保存されます。</span><span class="sxs-lookup"><span data-stu-id="84b99-212">Viewing the report saves the parameters that you selected together with the data feed definition.</span></span>  
  
     <span data-ttu-id="84b99-213">必要に応じて **[詳細設定]** をクリックし、プロバイダー固有のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-213">Optionally, click **Advanced** to set provider-specific properties for the report.</span></span>  
  
6.  <span data-ttu-id="84b99-214">**[接続テスト]** をクリックして、レポートがデータ フィードとして使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="84b99-214">Click **Test Connection** to make sure the report is available as a data feed.</span></span> <span data-ttu-id="84b99-215">または、 **[詳細設定]** をクリックして、データ フィード接続を指定する埋め込み XML が **[Inline Service Document]** プロパティに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="84b99-215">Alternatively, you can also click **Advanced** to confirm that the **Inline Service Document** property contains embedded XML that specifies the data feed connection.</span></span>  
  
7.  <span data-ttu-id="84b99-216">インポートを続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-216">Click **Next** to continue with the import.</span></span>  
  
8.  <span data-ttu-id="84b99-217">**[権限借用情報]** ページで、データを更新するときに Analysis Services がデータ ソースへの接続に使用する資格情報を指定し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-217">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="84b99-218">ウィザードの **[テーブルとビューの選択]** ページで、データとしてインポートするレポート パーツの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="84b99-218">In the **Select Tables and Views** page of the wizard, select the check box next to the report parts that you want to import as data.</span></span>  
  
     <span data-ttu-id="84b99-219">レポートによっては、テーブル、一覧、グラフなど、複数のパーツが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="84b99-219">Some reports can contain multiple parts, including tables, lists, or graphs.</span></span>  
  
10. <span data-ttu-id="84b99-220">**[表示名]** ボックスに、データ フィードを保存するモデルのテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="84b99-220">In the **Friendly name** box, type the name of the table where you want the data feed to be saved in your model.</span></span>  
  
     <span data-ttu-id="84b99-221">名前が割り当てられていない場合、既定では Reporting Services のコントロールの名前 (Tablix1、Tablix2 など) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="84b99-221">The name of the Reporting Service control is used by default if no name has been assigned: for example, Tablix1, Tablix2.</span></span> <span data-ttu-id="84b99-222">インポートされたデータ フィードのソースを簡単に識別できるように、インポート時にこの名前を変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="84b99-222">We recommend that you change this name during import so that you can more easily identify the origin of the imported data feed.</span></span>  
  
11. <span data-ttu-id="84b99-223">**[プレビューとフィルター]** をクリックしてデータを確認し、列の選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="84b99-223">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="84b99-224">レポートのデータ フィードでインポートされる行を制限することはできませんが、チェック ボックスをオフにすることで列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="84b99-224">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="84b99-225">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-225">Click **OK**.</span></span>  
  
12. <span data-ttu-id="84b99-226">**[テーブルとビューの選択]** ページで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b99-226">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b99-227">参照</span><span class="sxs-lookup"><span data-stu-id="84b99-227">See Also</span></span>  
 <span data-ttu-id="84b99-228">[SSAS 表形式&#41;&#40;サポートされるデータソース](tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="84b99-228">[Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="84b99-229">[SSAS 表形式&#41;&#40;サポートされているデータ型](tabular-models/data-types-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="84b99-229">[Data Types Supported &#40;SSAS Tabular&#41;](tabular-models/data-types-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="84b99-230">[SSAS の &#40;の権限借用表形式&#41;](tabular-models/impersonation-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="84b99-230">[Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md) </span></span>  
 <span data-ttu-id="84b99-231">[SSAS 表形式&#41;&#40;データを処理する](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="84b99-231">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="84b99-232">データのインポート &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="84b99-232">Import Data &#40;SSAS Tabular&#41;</span></span>](import-data-ssas-tabular.md)  
  
  
