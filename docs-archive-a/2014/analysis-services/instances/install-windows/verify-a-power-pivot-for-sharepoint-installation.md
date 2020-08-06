---
title: PowerPivot for SharePoint のインストールを確認する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f45e1aa1d48dd5a50b7ce38dc364089d438f215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643008"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a><span data-ttu-id="61003-102">PowerPivot for SharePoint インストールの確認</span><span class="sxs-lookup"><span data-stu-id="61003-102">Verify a PowerPivot for SharePoint Installation</span></span>
  <span data-ttu-id="61003-103">SharePoint ファームにインストールした PowerPivot for SharePoint インスタンスは、SharePoint サーバーの全体管理から管理されます。</span><span class="sxs-lookup"><span data-stu-id="61003-103">A PowerPivot for SharePoint instance that you install in a SharePoint farm is administered through SharePoint Central Administration.</span></span> <span data-ttu-id="61003-104">PowerPivot のサーバー コンポーネントと機能が使用可能になっているかどうかは、少なくとも、サーバーの全体管理および SharePoint サイトのページを調べれば確認できます。</span><span class="sxs-lookup"><span data-stu-id="61003-104">At a minimum, you can check pages in Central Administration and on SharePoint sites to verify that PowerPivot server components and features are available.</span></span> <span data-ttu-id="61003-105">インストールを完全に確認するには、SharePoint にパブリッシュでき、ライブラリからアクセスできる PowerPivot ブックが必要になります。</span><span class="sxs-lookup"><span data-stu-id="61003-105">However, to fully verify an installation, you must have a PowerPivot workbook that you can publish to SharePoint and access from a library.</span></span> <span data-ttu-id="61003-106">テストの際には、既に PowerPivot データが含まれているサンプル ブックをパブリッシュし、それを使用して SharePoint 統合が正しく構成されているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="61003-106">For testing purposes, you can publish a sample workbook that already contains PowerPivot data and use it to confirm that SharePoint integration is correctly configured.</span></span>  
  
##  <a name="verify-central-administration-integration"></a><a name="verifyinstall"></a><span data-ttu-id="61003-107">サーバーの全体管理統合の確認</span><span class="sxs-lookup"><span data-stu-id="61003-107">Verify Central Administration Integration</span></span>  
 <span data-ttu-id="61003-108">PowerPivot のサーバーの全体管理との統合を確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="61003-108">To verify PowerPivot integration with Central Administration, do the following:</span></span>  
  
1.  <span data-ttu-id="61003-109">[スタート] メニューの [**すべてのプログラム**] をクリックし、[Microsoft Sharepoint 2010 製品] を開いて、[ **sharepoint 2010 サーバーの全体管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-109">On the Start menu, click **All Programs**, open Microsoft SharePoint 2010 Products, and click **SharePoint 2010 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="61003-110">ユーザー名とパスワードを入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-110">Enter your user name and password, and then click **OK**.</span></span>  
  
     <span data-ttu-id="61003-111">サーバーの全体管理を開くたびにユーザー名とパスワードを入力せずに済むように、ブラウザーの設定を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="61003-111">Optionally, you can modify browser settings to avoid having to enter a user name and password each time you open Central Administration.</span></span> <span data-ttu-id="61003-112">サーバーの全体管理を信頼済みサイトとして追加するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="61003-112">To add Central Administration as a trusted site, do the following.</span></span>  
  
    1.  <span data-ttu-id="61003-113">Internet Explorer で、[ツール] メニューの [**インターネットオプション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-113">In Internet Explorer, on the Tools menu, click **Internet options**.</span></span>  
  
    2.  <span data-ttu-id="61003-114">[セキュリティ] タブの **[セキュリティ設定を表示または変更するゾーンを選択してください。]** セクションで、[信頼済みサイト] をクリックし、[サイト] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-114">On the Security tab, in the **Select a zone to view or change security settings** section, click Trusted Sites, and then click Sites.</span></span>  
  
    3.  <span data-ttu-id="61003-115">**[このゾーンのサイトにはすべてサーバーの確認 (https:) を必要とする]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="61003-115">Clear the **Require server verification (https:) for all sites in this zone** checkbox.</span></span>  
  
    4.  <span data-ttu-id="61003-116">**[次の Web サイトをゾーンに追加する]** に、サイトの URL を入力し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-116">In **Add this Web site to the zone**, type the URL to your site, and then click **Add**.</span></span>  
  
    5.  <span data-ttu-id="61003-117">[**閉じる**] をクリックしてから [**OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-117">Click **Close**, and then click **OK**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="61003-118">SharePoint のインストールに関するドキュメントには、プロキシ サーバーのエラーを解決する手順や、更新プログラムをダウンロードしてインストールできるように Internet Explorer セキュリティ強化の構成を無効にする手順も示されています。</span><span class="sxs-lookup"><span data-stu-id="61003-118">SharePoint installation documentation includes additional instructions for working around proxy server errors and for disabling Internet Explorer Enhanced Security Configuration so that you can download and install updates.</span></span> <span data-ttu-id="61003-119">詳細については、Microsoft Web サイトの「 **SQL Server を使用する単一サーバーを展開する (SharePoint Server 2010)** 」の「 [追加のタスクの実行](https://go.microsoft.com/fwlink/?LinkId=177754) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61003-119">For more information, see the **Perform additional tasks** section in [Deploy a single server with SQL Server](https://go.microsoft.com/fwlink/?LinkId=177754) on the Microsoft web site.</span></span>  
  
3.  <span data-ttu-id="61003-120">サーバーの全体管理で、[システム設定] の **[ファーム機能の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-120">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
4.  <span data-ttu-id="61003-121">**[PowerPivot 統合機能]** が **[アクティブ]** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-121">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
5.  <span data-ttu-id="61003-122">サーバーの全体管理で、[システム設定] の [**サーバーのサービスの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-122">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
6.  <span data-ttu-id="61003-123">**SQL Server Analysis Services** と **SQL Server PowerPivot System サービス** が開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-123">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
7.  <span data-ttu-id="61003-124">サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-124">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
8.  <span data-ttu-id="61003-125">[**既定の Powerpivot サービスアプリケーション**] をクリックして、このアプリケーションの Powerpivot 管理ダッシュボードを開きます。</span><span class="sxs-lookup"><span data-stu-id="61003-125">Click **Default PowerPivot Service Application** to open PowerPivot Management Dashboard for this application.</span></span> <span data-ttu-id="61003-126">最初に使用するときは、ダッシュボードの読み込みに数分かかります。</span><span class="sxs-lookup"><span data-stu-id="61003-126">On first use, the dashboard takes several minutes to load.</span></span>  
  
     <span data-ttu-id="61003-127">または、[**既定の PowerPivot サービスアプリケーション**] の横にある空白部分をクリックして行を選択し、[**プロパティ**] をクリックして、このサービスアプリケーションの構成設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="61003-127">Alternatively, click the empty space next to **Default PowerPivot Service Application** to select the row, and click **Properties** to view the configuration settings for this service application.</span></span> <span data-ttu-id="61003-128">構成設定とアプリケーション プロパティの両方を修正して、サーバーの構成を変更できます。</span><span class="sxs-lookup"><span data-stu-id="61003-128">You can modify both configuration settings and application properties to change your server configuration.</span></span> <span data-ttu-id="61003-129">これらの設定の詳細については、「[サーバーの全体管理での PowerPivot サービスアプリケーションの作成と構成](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61003-129">For more information about these settings, see [Create and Configure a PowerPivot Service Application in Central Administration](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).</span></span>  
  
## <a name="verify-integration-at-the-site-level"></a><span data-ttu-id="61003-130">サイト レベルでの統合の確認</span><span class="sxs-lookup"><span data-stu-id="61003-130">Verify Integration at the Site Level</span></span>  
 <span data-ttu-id="61003-131">PowerPivot の SharePoint サイトとの統合を確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="61003-131">To verify PowerPivot integration with a SharePoint site, do the following:</span></span>  
  
1.  <span data-ttu-id="61003-132">ブラウザーで、作成した Web アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="61003-132">In a browser, open the Web application you created.</span></span> <span data-ttu-id="61003-133">既定値を使用した場合は、URL アドレスに http://を指定でき \<your computer name> ます。</span><span class="sxs-lookup"><span data-stu-id="61003-133">If you used default values, you can specify http://\<your computer name> in the URL address.</span></span>  
  
2.  <span data-ttu-id="61003-134">PowerPivot データ アクセス機能と PowerPivot データ処理機能がアプリケーションで使用可能になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-134">Verify that PowerPivot data access and processing features are available in the application.</span></span> <span data-ttu-id="61003-135">そのためには、PowerPivot によって提供されるライブラリ テンプレートがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-135">You can do this by verifying the presence of PowerPivot-provided library templates:</span></span>  
  
    1.  <span data-ttu-id="61003-136">[サイトの操作] の [**その他のオプション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-136">On Site Actions, click **More Options..**.</span></span>  
  
    2.  <span data-ttu-id="61003-137">ライブラリでは、[**データフィードライブラリ**] と [ **PowerPivot ギャラリー**] が表示されます。</span><span class="sxs-lookup"><span data-stu-id="61003-137">In Libraries, you should see **Data Feed Library** and **PowerPivot Gallery**.</span></span> <span data-ttu-id="61003-138">これらのライブラリ テンプレートは PowerPivot 機能によって提供されるものであり、PowerPivot 機能が正しく統合されている場合に [ライブラリ] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="61003-138">These library templates are provided by the PowerPivot feature and will be visible in the Libraries list if the feature is integrated correctly.</span></span>  
  
## <a name="verify-data-access-on-the-server"></a><span data-ttu-id="61003-139">サーバーでのデータ アクセスの確認</span><span class="sxs-lookup"><span data-stu-id="61003-139">Verify Data Access on the Server</span></span>  
 <span data-ttu-id="61003-140">サーバーで PowerPivot データ アクセスを確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="61003-140">To verify PowerPivot data access on the server, do the following:</span></span>  
  
1.  <span data-ttu-id="61003-141">Reporting Services のチュートリアルにある Picnic のデータ サンプルを[ダウンロード](https://go.microsoft.com/fwlink/?LinkID=219108) します。</span><span class="sxs-lookup"><span data-stu-id="61003-141">[Download](https://go.microsoft.com/fwlink/?LinkID=219108) the Picnic data sample that accompanies a Reporting Services tutorial.</span></span> <span data-ttu-id="61003-142">このダウンロードに含まれるサンプル ブックを使用して、PowerPivot データのアクセスを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-142">You will use the sample workbook in this download to verify PowerPivot data access.</span></span> <span data-ttu-id="61003-143">ファイルを解凍します。</span><span class="sxs-lookup"><span data-stu-id="61003-143">Extract the files.</span></span>  
  
2.  <span data-ttu-id="61003-144">Excel ブック (.xlsx) を Shared Documents にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="61003-144">Upload the Excel workbook (.xlsx) to Shared Documents.</span></span> <span data-ttu-id="61003-145">ブックに埋め込み PowerPivot データが含まれます。</span><span class="sxs-lookup"><span data-stu-id="61003-145">The workbook contains embedded PowerPivot data.</span></span>  
  
3.  <span data-ttu-id="61003-146">ドキュメントをクリックしてライブラリから開きます。</span><span class="sxs-lookup"><span data-stu-id="61003-146">Click on the document to open it from the library.</span></span>  
  
4.  <span data-ttu-id="61003-147">ブックの上部にあるスライサーまたはフィルターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-147">Click on a slicer or filter at the top of the workbook.</span></span> <span data-ttu-id="61003-148">このブックのスライサーは、月、色、および種類です。</span><span class="sxs-lookup"><span data-stu-id="61003-148">Month, color, and type are slicers in this workbook.</span></span> <span data-ttu-id="61003-149">スライサーをクリックすると PowerPivot クエリが開始され、サーバーが動作することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="61003-149">Clicking a slicer starts a PowerPivot query and proves that your server is operational.</span></span> <span data-ttu-id="61003-150">サーバーは PowerPivot データをバックグラウンドで読み込んで結果を返します。</span><span class="sxs-lookup"><span data-stu-id="61003-150">The server will load PowerPivot data in the background and return the results.</span></span>  
  
5.  <span data-ttu-id="61003-151">ライブラリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="61003-151">Go back to the library.</span></span> <span data-ttu-id="61003-152">ブックの右側にある下矢印を選択して、 **[Power View の起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-152">Select the down arrow to the right of the workbook, and then click **Launch Power View**.</span></span> <span data-ttu-id="61003-153">この手順により、Reporting Services で [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] 機能が動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-153">This step confirms that the [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] feature in Reporting Services is operational.</span></span> <span data-ttu-id="61003-154">Reporting Services をインストールしていない場合は、この手順は省略します。</span><span class="sxs-lookup"><span data-stu-id="61003-154">If you did not install Reporting Services, skip this step.</span></span>  
  
     <span data-ttu-id="61003-155">次の手順で、Management Studio のサーバーに接続して、データの読み込みとキャッシュが行われたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-155">In the next step, you will connect to the server in Management Studio to verify the data is loaded and cached.</span></span>  
  
6.  <span data-ttu-id="61003-156">[スタート] メニューの [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] プログラム グループから SQL Server Management Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="61003-156">Start SQL Server Management Studio from the [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] program group in the Start menu.</span></span> <span data-ttu-id="61003-157">このツールがサーバーにインストールされていない場合は、以降の手順はスキップし、最後の手順でキャッシュされたファイルがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-157">If this tool is not installed on your server, you can skip ahead to the last step to confirm the presence of cached files.</span></span>  
  
7.  <span data-ttu-id="61003-158">[サーバーの種類] で、[ **Analysis Services**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="61003-158">In Server Type, select **Analysis Services**.</span></span>  
  
8.  <span data-ttu-id="61003-159">[サーバー名] に「 \*\* \<server-name> \ powerpivot\*\*」と入力します。ここで、 **\<server-name>** は PowerPivot for SharePoint インストールされているコンピューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="61003-159">In Server Name, enter **\<server-name>\powerpivot**, where **\<server-name>** is the name of the computer that has the PowerPivot for SharePoint installation.</span></span>  
  
9. <span data-ttu-id="61003-160">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61003-160">Click **Connect**.</span></span> <span data-ttu-id="61003-161">これにより、Analysis Services サーバーが使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-161">This verifies that the Analysis Services server is available.</span></span>  
  
10. <span data-ttu-id="61003-162">オブジェクトエクスプローラーでは、[**データベース**] をクリックして、読み込まれている PowerPivot データファイルの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="61003-162">In Object Explorer, you can click **Databases** to view the list of PowerPivot data files that are loaded.</span></span>  
  
11. <span data-ttu-id="61003-163">コンピューターのファイル システムのフォルダーで、ファイルがディスクにキャッシュされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="61003-163">On the computer file system, check the following folder to determine whether files are cached to disk.</span></span> <span data-ttu-id="61003-164">キャッシュされたファイルが存在していれば、配置が機能していることの確認になります。</span><span class="sxs-lookup"><span data-stu-id="61003-164">The presence of cached files is further verification that your deployment is operational.</span></span> <span data-ttu-id="61003-165">ファイルキャッシュを表示するには、「」に進んでください \<drive> 。POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot サービスアプリケーションフォルダー。</span><span class="sxs-lookup"><span data-stu-id="61003-165">To view the file cache, go to the \<drive>:\Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot Service Application folder.</span></span> <span data-ttu-id="61003-166">キャッシュされた各データベースは、名前が一意になるように、GUID ベースの名前付け規則を使用してそれぞれのフォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="61003-166">Each cached database is stored in its own folder, using a GUID-based naming convention to ensure a unique name.</span></span>  
  
  
