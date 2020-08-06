---
title: リモート エラーの有効化 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- remote data source [Reporting Services]
- EnableRemoteError server property
ms.assetid: 5f05022b-d557-43e0-b50a-f5e2a1846b83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d2a7e7e0b38b38bf563dfc2a8cff65c897c5293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642539"
---
# <a name="enable-remote-errors-reporting-services"></a><span data-ttu-id="79019-102">リモート エラーの有効化 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="79019-102">Enable Remote Errors (Reporting Services)</span></span>
  <span data-ttu-id="79019-103">リモート サーバーで発生するエラー状態に関する追加情報が返されるように、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーのサーバー プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="79019-103">You can set server properties on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server to return additional information about error conditions that occur on remote servers.</span></span> <span data-ttu-id="79019-104">エラー メッセージに "このエラーの詳細を表示するには、ローカルのサーバー コンピューターでレポート サーバーを開くか、リモート エラーを有効にしてください。" と表示されている場合は、`EnableRemoteErrors` プロパティを設定すると、問題のトラブルシューティングに役立つ追加情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="79019-104">If an error message contains the text "For more information about this error, navigate to the report server on the local server machine, or enable remote errors", you can set the `EnableRemoteErrors` property to access additional information that can help you troubleshoot the problem.</span></span> <span data-ttu-id="79019-105">詳細については、 [オンライン ブックの「](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) レポート サーバーのシステム プロパティ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79019-105">For more information, see [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="79019-106">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="79019-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="79019-107">SharePoint モードのリモート エラーの有効化</span><span class="sxs-lookup"><span data-stu-id="79019-107">Enable Remote Errors for SharePoint Mode</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="79019-108">SQL Server Management Studio を使用したリモート エラーの有効化 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="79019-108">Enable remote errors through SQL Server Management Studio (Native Mode)</span></span>](#bkmk_mgtStudio)  
  
-   [<span data-ttu-id="79019-109">スクリプトを使用したリモート エラーの有効化 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="79019-109">Enable remote errors through script (Native Mode)</span></span>](#bkmk_script)  
  
-   [<span data-ttu-id="79019-110">ConfigurationInfo テーブルの変更 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="79019-110">Modifying the ConfigurationInfo table (Native Mode)</span></span>](#bkmk_ConfigurationInfo)  
  
##  <a name="enable-remote-errors-for-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="79019-111">SharePoint モードのリモート エラーの有効化</span><span class="sxs-lookup"><span data-stu-id="79019-111">Enable Remote Errors for SharePoint Mode</span></span>  
 <span data-ttu-id="79019-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードのリモート エラーを有効化する手順は 2 種類あります。</span><span class="sxs-lookup"><span data-stu-id="79019-112">There are two different procedures for enabling remote errors for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="79019-113">この手順は、レポート サーバーのアーキテクチャによって異なります。</span><span class="sxs-lookup"><span data-stu-id="79019-113">The procedure is different for the two different report server architectures.</span></span> <span data-ttu-id="79019-114">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] リリースで導入されたアーキテクチャに基づく新しい SharePoint サービスでは、各 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション用に構成できる設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="79019-114">The newer SharePoint service based architecture that was introduced in the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, utilizes a setting that can be configured for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="79019-115">旧式のアーキテクチャでは、単一のサイト レベル設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="79019-115">The older architecture utilizes a single site level setting.</span></span>  
  
#### <a name="enable-remote-errors-for-a-reporting-services-service-application"></a><span data-ttu-id="79019-116">Reporting Services サービス アプリケーションのリモート エラーの有効化</span><span class="sxs-lookup"><span data-stu-id="79019-116">Enable Remote errors for a Reporting Services Service Application</span></span>  
  
1.  <span data-ttu-id="79019-117">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] か、またはそれ以降バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を使用してインストールされた SharePoint モード レポート サーバーの場合は、サービス アプリケーション設定 **[リモート エラーを有効にする]** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="79019-117">For a SharePoint mode report server installed with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or a newer version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], enable the service application setting **Enable remote errors**.</span></span> <span data-ttu-id="79019-118">この設定は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションごとに構成できます。</span><span class="sxs-lookup"><span data-stu-id="79019-118">The setting can be configured for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
2.  <span data-ttu-id="79019-119">SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-119">In SharePoint Central Administration, click **Manage service applications** in the **Application Management** group.</span></span>  
  
3.  <span data-ttu-id="79019-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを探し、サービス アプリケーションの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-120">Find your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and click the name of your service application.</span></span>  
  
4.  <span data-ttu-id="79019-121">**[システム設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-121">Click **System Settings**.</span></span>  
  
5.  <span data-ttu-id="79019-122">**[セキュリティ]** セクションで **[リモート エラーを有効にする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-122">Click **Enable Remote Errors** in the **Security** section.</span></span>  
  
6.  <span data-ttu-id="79019-123">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-123">Click **OK**.</span></span>  
  
#### <a name="enable-remote-errors-for-a-sharepoint-site"></a><span data-ttu-id="79019-124">SharePoint サイトのリモート エラーの有効化</span><span class="sxs-lookup"><span data-stu-id="79019-124">Enable Remote Errors for a SharePoint Site</span></span>  
  
1.  <span data-ttu-id="79019-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] より前のバージョンの [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を使用してインストールされた SharePoint モード レポート サーバーの場合は、サイト設定 **[ローカル モードでのリモート エラーを有効にします]** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="79019-125">For a SharePoint mode report server installed with a version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prior to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], enable the site setting **Enable remote errors in local mode**.</span></span>  
  
2.  <span data-ttu-id="79019-126">**[サイトの操作]** で、変更するサイトの **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-126">In **Site Actions** click **Site Settings** for the site you want to modify.</span></span>  
  
3.  <span data-ttu-id="79019-127">**[Reporting Services]** グループで **[Reporting Services のサイト設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-127">Click **Reporting Services Site Settings** in the **Reporting Services** group.</span></span>  
  
4.  <span data-ttu-id="79019-128">**[ローカル モードでのリモート エラーを有効にします]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-128">Click **Enable remote errors in local mode**.</span></span>  
  
5.  <span data-ttu-id="79019-129">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="79019-129">Click **OK**</span></span>  
  
##  <a name="enable-remote-errors-through-sql-server-management-studio-native-mode"></a><a name="bkmk_mgtStudio"></a> <span data-ttu-id="79019-130">SQL Server Management Studio を使用したリモート エラーの有効化 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="79019-130">Enable remote errors through SQL Server Management Studio (Native Mode)</span></span>  
  
1.  <span data-ttu-id="79019-131">Management Studio を起動し、レポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="79019-131">Start Management Studio and connect to a report server instance.</span></span> <span data-ttu-id="79019-132">詳細については、 [オンライン ブックの「](../tools/connect-to-a-report-server-in-management-studio.md) Management Studio でレポート サーバーに接続する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79019-132">For more information, see [Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="79019-133">レポート サーバー ノードを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79019-133">Right-click the report server node, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="79019-134">**[詳細設定]** をクリックすると、プロパティ ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="79019-134">Click **Advanced** to open the properties page.</span></span> <span data-ttu-id="79019-135">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[サーバーのプロパティ &#40;[詳細設定] ページ&#41; - Reporting Services」](../tools/server-properties-advanced-page-reporting-services.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79019-135">For more information, see [Server Properties &#40;Advanced Page&#41; - Reporting Services](../tools/server-properties-advanced-page-reporting-services.md)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="79019-136">で `EnableRemoteErrors` 、を選択し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="79019-136">In `EnableRemoteErrors`, select `True`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="enable-remote-errors-through-script-native-mode"></a><a name="bkmk_script"></a> <span data-ttu-id="79019-137">スクリプトを使用したリモート エラーの有効化 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="79019-137">Enable remote errors through script (Native Mode)</span></span>  
  
1.  <span data-ttu-id="79019-138">テキスト ファイルを作成し、そのファイルに次のスクリプトをコピーします。</span><span class="sxs-lookup"><span data-stu-id="79019-138">Create a text file and copy the following script into the file.</span></span>  
  
    ```  
    Public Sub Main()  
      Dim P As New [Property]()  
      P.Name = "EnableRemoteErrors"  
      P.Value = True  
      Dim Properties(0) As [Property]  
      Properties(0) = P  
      Try  
        rs.SetSystemProperties(Properties)  
        Console.WriteLine("Remote errors enabled.")  
      Catch SE As SoapException  
        Console.WriteLine(SE.Detail.OuterXml)  
      End Try  
    End Sub  
    ```  
  
2.  <span data-ttu-id="79019-139">ファイルを EnableRemoteErrors.rss として保存します。</span><span class="sxs-lookup"><span data-stu-id="79019-139">Save the file as EnableRemoteErrors.rss.</span></span>  
  
3.  <span data-ttu-id="79019-140">**[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。「 **cmd**」と入力して **[OK]** をクリックすると、コマンド プロンプト ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="79019-140">Click **Start**, point to **Run**, type **cmd**, and click **OK** to open a command prompt window.</span></span>  
  
4.  <span data-ttu-id="79019-141">作成した .rss ファイルが保存されているディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="79019-141">Navigate to the directory that contains the .rss file you just created.</span></span>  
  
5.  <span data-ttu-id="79019-142">次のコマンド ラインを入力します。 *servername* は実際のサーバー名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="79019-142">Type the following command line, replacing *servername* with the actual name of your server:</span></span>  
  
    ```  
    rs -i EnableRemoteErrors.rss -s http://servername/ReportServer  
    ```  
  
6.  <span data-ttu-id="79019-143">詳細については、「[RS.exe ユーティリティ (SSRS)](../tools/rs-exe-utility-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79019-143">For more information, see [RS.exe Utility &#40;SSRS&#41;](../tools/rs-exe-utility-ssrs.md)</span></span>  
  
##  <a name="modifying-the-configurationinfo-table-native-mode"></a><a name="bkmk_ConfigurationInfo"></a> <span data-ttu-id="79019-144">ConfigurationInfo テーブルの変更 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="79019-144">Modifying the ConfigurationInfo table (Native Mode)</span></span>  
  
1.  > [!NOTE]  
    >  <span data-ttu-id="79019-145">レポートサーバーデータベースで**Configurationinfo**テーブルを編集してをに設定できます `EnableRemoteErrors` `True` が、レポートサーバーがアクティブに使用されている場合は、SQL Server Management Studio またはスクリプトを使用して設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79019-145">You can edit the **ConfigurationInfo** table in the report server database to set `EnableRemoteErrors` to `True`, but if the report server is actively used, you should use SQL Server Management Studio or script to modify the settings.</span></span> <span data-ttu-id="79019-146">データベース内で設定を変更した場合、変更は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスの再起動後に反映されます。</span><span class="sxs-lookup"><span data-stu-id="79019-146">If you modify the setting in the database, you need to restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service before the changes take effect.</span></span>  
  
  
