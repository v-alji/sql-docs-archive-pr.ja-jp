---
title: Reporting Services SharePoint モードの PowerShell コマンドレット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b20ad870fd8a9cd7f220eebb2b954d7a88a10c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742897"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a><span data-ttu-id="b9868-102">Reporting Services SharePoint モードの PowerShell コマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-102">PowerShell cmdlets for Reporting Services SharePoint Mode</span></span>
  <span data-ttu-id="b9868-103">Sharepoint モードをインストールすると [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 、sharepoint モードのレポートサーバーをサポートするために PowerShell コマンドレットがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b9868-103">When you install [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode, PowerShell cmdlets are installed to support report Servers in SharePoint mode.</span></span> <span data-ttu-id="b9868-104">コマンドレットは 3 つのカテゴリの機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b9868-104">The cmdlets cover three categories of functionality.</span></span>  
  
-   <span data-ttu-id="b9868-105">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共有サービスおよびプロキシのインストール。</span><span class="sxs-lookup"><span data-stu-id="b9868-105">Installation of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint shared service and proxy.</span></span>  
  
-   <span data-ttu-id="b9868-106">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションおよび関連付けられたプロキシのプロビジョニングと管理。</span><span class="sxs-lookup"><span data-stu-id="b9868-106">Provisioning and management of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications and associated proxies.</span></span>  
  
-   <span data-ttu-id="b9868-107">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能 (拡張機能や暗号化キーなど) の管理。</span><span class="sxs-lookup"><span data-stu-id="b9868-107">Management of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features, for example extensions and encryption keys.</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)]<span data-ttu-id="b9868-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="b9868-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint Mode</span></span>|  
  
 <span data-ttu-id="b9868-109">**このトピックの内容は次のとおりです。**</span><span class="sxs-lookup"><span data-stu-id="b9868-109">**This topic contains the following:**</span></span>  
  
-   [<span data-ttu-id="b9868-110">コマンドレットの概要</span><span class="sxs-lookup"><span data-stu-id="b9868-110">Cmdlet Summary</span></span>](#bkmk_cmdlet_sum)  
  
-   [<span data-ttu-id="b9868-111">共有サービスとプロキシ コマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-111">Shared Service and Proxy Cmdlets</span></span>](#bkmk_sharedservice_cmdlets)  
  
-   [<span data-ttu-id="b9868-112">サービスアプリケーションとプロキシコマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-112">Service Application and Proxy Cmdlets</span></span>](#bkmk_serviceapp_cmdlets)  
  
-   [<span data-ttu-id="b9868-113">Reporting Services カスタム機能コマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-113">Reporting Services Custom Functionality Cmdlets</span></span>](#bkmk_ssrsfeatures_cmdlets)  
  
-   [<span data-ttu-id="b9868-114">基本的なサンプル</span><span class="sxs-lookup"><span data-stu-id="b9868-114">Basic Samples</span></span>](#bkmk_basic_samples)  
  
-   [<span data-ttu-id="b9868-115">詳細なサンプル</span><span class="sxs-lookup"><span data-stu-id="b9868-115">Detailed Samples</span></span>](#bkmk_detailedsamples)  
  
    -   [<span data-ttu-id="b9868-116">Reporting Services サービスアプリケーションとプロキシを作成する</span><span class="sxs-lookup"><span data-stu-id="b9868-116">Create a Reporting Services service application and proxy</span></span>](#bkmk_example_create_service_application)  
  
    -   [<span data-ttu-id="b9868-117">Reporting Services 配信拡張機能の確認と更新</span><span class="sxs-lookup"><span data-stu-id="b9868-117">Review and update a Reporting Services delivery extension</span></span>](#bkmk_example_delivery_extension)  
  
    -   [<span data-ttu-id="b9868-118">Reporting Services アプリケーション データベースのプロパティ (データベース タイムアウトなど) の取得と設定</span><span class="sxs-lookup"><span data-stu-id="b9868-118">Get and set properties of the Reporting Servicea application database, for example database timeout</span></span>](#bkmk_example_db_properties)  
  
    -   [<span data-ttu-id="b9868-119">Reporting services データ拡張機能の一覧表示-SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="b9868-119">List reporting services data extensions - SharePoint mode</span></span>](#bkmk_example_list_data_extensions)  
  
    -   [<span data-ttu-id="b9868-120">サブスクリプションの所有者の変更と一覧表示</span><span class="sxs-lookup"><span data-stu-id="b9868-120">Change and list subscription owners</span></span>](#bkmk_change_subscription_owner)  
  
##  <a name="cmdlet-summary"></a><a name="bkmk_cmdlet_sum"></a><span data-ttu-id="b9868-121">コマンドレットの概要</span><span class="sxs-lookup"><span data-stu-id="b9868-121">Cmdlet Summary</span></span>  

 <span data-ttu-id="b9868-122">コマンドレットを実行するには、SharePoint 管理シェルを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9868-122">To run the cmdlets you need to open the SharePoint Management Shell.</span></span> <span data-ttu-id="b9868-123">Microsoft Windows に付属しているグラフィカル ユーザー インターフェイス エディター ( **Windows PowerShell Integrated Scripting Environment (ISE)**) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9868-123">You can also use the graphical user interface editor that is included with Microsoft Windows, **Windows PowerShell Integrated Scripting Environment (ISE)**.</span></span> <span data-ttu-id="b9868-124">詳細については、「 [Windows Server での Windows PowerShell の開始](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell)) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9868-124">For more information, see [Starting Windows PowerShell on Windows Server](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell).</span></span> <span data-ttu-id="b9868-125">次のコマンドレットの概要では、サービスアプリケーション "データベース" への参照は、サービスアプリケーションによって作成および使用されるすべてのデータベースを参照し [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b9868-125">In the following cmdlet summaries, the references to service application 'databases', refer to all of the databases created and used by a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="b9868-126">これには、構成、警告、および一時データベースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9868-126">This includes the configuration, alerting, and temp databases.</span></span>  

  
 <span data-ttu-id="b9868-127">PowerShell の例を入力すると、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9868-127">If you see an error message similar to the following when you type the PowerShell examples:</span></span>  
  
-   <span data-ttu-id="b9868-128">Install-SPRSService : 用語 'Install-SPRSService' は、</span><span class="sxs-lookup"><span data-stu-id="b9868-128">Install-SPRSService : The term 'Install-SPRSService' is not recognized as the</span></span>  
    <span data-ttu-id="b9868-129">コマンドレット、関数、スクリプト ファイル、または操作可能なプログラムの名前として認識されません。</span><span class="sxs-lookup"><span data-stu-id="b9868-129">name of a cmdlet, function, script file, or operable program.</span></span> <span data-ttu-id="b9868-130">名前が正しく記述されていることを確認し、パスが含まれている場合はそのパスが正しいことを確認してから、再試行してください。</span><span class="sxs-lookup"><span data-stu-id="b9868-130">Check the spelling of the name, or if a path was included, verify that the path is correct and try again.</span></span>  
  
 <span data-ttu-id="b9868-131">次のいずれかの問題が発生しています。</span><span class="sxs-lookup"><span data-stu-id="b9868-131">One of the following issues is occurring:</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="b9868-132">SharePoint モードがインストールされていないため、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] コマンドレットがインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="b9868-132">SharePoint mode is not installed and therefore the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlets are not installed.</span></span>  
  
-   <span data-ttu-id="b9868-133">SharePoint 管理シェルでなく、Windows PowerShell または Windows PowerShell ISE で PowerShell コマンドを実行しました。</span><span class="sxs-lookup"><span data-stu-id="b9868-133">You ran the PowerShell command in Windows PowerShell or Windows PowerShell ISE instead of the SharePoint Management Shell.</span></span> <span data-ttu-id="b9868-134">SharePoint 管理シェルを使用するか、次のコマンドで SharePoint スナップインを Windows PowerShell ウィンドウに追加します。</span><span class="sxs-lookup"><span data-stu-id="b9868-134">Use the SharePoint Management shell or add the SharePoint Snap-in to the Windows PowerShell window with the following command:</span></span>  
  
    ```powershell
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 <span data-ttu-id="b9868-135">詳細については、「 [Windows PowerShell を使用して SharePoint 2013 を管理する](https://technet.microsoft.com/library/ee806878.aspx)」 (を参照してください https://technet.microsoft.com/library/ee806878.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="b9868-135">For more information see [Use Windows PowerShell to administer SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) (https://technet.microsoft.com/library/ee806878.aspx).</span></span>  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a><span data-ttu-id="b9868-136">SharePoint 管理シェルを開いてコマンドレットを実行するには</span><span class="sxs-lookup"><span data-stu-id="b9868-136">To Open the SharePoint Management Shell and run cmdlets</span></span>  
  
1.  <span data-ttu-id="b9868-137">[**スタート**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9868-137">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="b9868-138">**[Microsoft SharePoint 製品]** グループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9868-138">Click the **Microsoft SharePoint Products** group.</span></span>  
  
3.  <span data-ttu-id="b9868-139">**[SharePoint 管理シェル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9868-139">Click the **SharePoint Management Shell**.</span></span>  
  
 <span data-ttu-id="b9868-140">コマンドレットのコマンド ライン ヘルプを表示するには、PowerShell のコマンド プロンプトで 'Get-Help' コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9868-140">To view command line help for a cmdlet use the PowerShell 'Get-Help' command at the PowerShell command prompt.</span></span> <span data-ttu-id="b9868-141">例:</span><span class="sxs-lookup"><span data-stu-id="b9868-141">For example:</span></span>  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="shared-service-and-proxy-cmdlets"></a><a name="bkmk_sharedservice_cmdlets"></a><span data-ttu-id="b9868-142">共有サービスとプロキシコマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-142">Shared Service and Proxy Cmdlets</span></span>  
 <span data-ttu-id="b9868-143">次の表に、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共有サービス用の PowerShell コマンドレットを示します。</span><span class="sxs-lookup"><span data-stu-id="b9868-143">The following table contains the PowerShell cmdlets for the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint shared service.</span></span>  
  
|<span data-ttu-id="b9868-144">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-144">Cmdlet</span></span>|<span data-ttu-id="b9868-145">説明</span><span class="sxs-lookup"><span data-stu-id="b9868-145">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b9868-146">Install-SPRSService</span><span class="sxs-lookup"><span data-stu-id="b9868-146">Install-SPRSService</span></span>|<span data-ttu-id="b9868-147">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 共有サービスをインストールして登録するか、アンインストールします。</span><span class="sxs-lookup"><span data-stu-id="b9868-147">Installs and registers, or uninstalls, the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] shared service.</span></span> <span data-ttu-id="b9868-148">この操作は、SharePoint モードの SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] がインストールされているコンピューター上でのみ行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b9868-148">This can be done only on the machine that has an installation of SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="b9868-149">インストールの場合は、以下の 2 つの操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="b9868-149">For installation, two operations occur:</span></span><br /><br /> <span data-ttu-id="b9868-150">1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービスがファームにインストールされていること。</span><span class="sxs-lookup"><span data-stu-id="b9868-150">1) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is installed in the farm.</span></span><br /><br /> <span data-ttu-id="b9868-151">2) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービスインスタンスが現在のコンピューターにインストールされていること。</span><span class="sxs-lookup"><span data-stu-id="b9868-151">2) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service instance is installed to the current machine.</span></span><br /><br /> <span data-ttu-id="b9868-152">アンインストールの場合は、以下の 2 つの操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="b9868-152">For Uninstallation, two operations occur:</span></span><br /><span data-ttu-id="b9868-153">1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービスは、現在のコンピューターからアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b9868-153">1) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is uninstalled from the current machine.</span></span><br /><span data-ttu-id="b9868-154">2) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービスがファームからアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b9868-154">2) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is uninstalled from the farm.</span></span><br /><br /> <br /><br /> <span data-ttu-id="b9868-155">メモ: [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービスがインストールされているファーム内に他のコンピューターが存在する場合や [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションがファーム内で引き続き実行されている場合は、警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9868-155">NOTE: If there are any other machines in the farm that have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service installed, or if there are still [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications running in the farm, a warning message is displayed.</span></span>|  
|<span data-ttu-id="b9868-156">Install-SPRSServiceProxy</span><span class="sxs-lookup"><span data-stu-id="b9868-156">Install-SPRSServiceProxy</span></span>|<span data-ttu-id="b9868-157">SharePoint ファーム内で Reporting Services サービス プロキシをインストールして登録するか、アンインストールします。</span><span class="sxs-lookup"><span data-stu-id="b9868-157">Installs and registers, or uninstalls, the Reporting Services service proxy in the SharePoint farm.</span></span>|  
|<span data-ttu-id="b9868-158">Get-SPRSProxyUrl</span><span class="sxs-lookup"><span data-stu-id="b9868-158">Get-SPRSProxyUrl</span></span>|<span data-ttu-id="b9868-159">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービスにアクセスするための URL を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9868-159">Gets the URL(s) for accessing the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="b9868-160">Get-SPRSServiceApplicationServers</span><span class="sxs-lookup"><span data-stu-id="b9868-160">Get-SPRSServiceApplicationServers</span></span>|<span data-ttu-id="b9868-161">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 共有サービスのインストールを含む、ローカル SharePoint ファーム内のすべてのサーバーを取得します。</span><span class="sxs-lookup"><span data-stu-id="b9868-161">Gets all servers in the local SharePoint farm that contain an installation of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] shared service.</span></span> <span data-ttu-id="b9868-162">このコマンドレットは、どのサーバーで共有サービスを実行していてアップグレードする必要があるかを調べる目的に適しており、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のアップグレードに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b9868-162">This cmdlet is useful for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] upgrades, to determine which servers run the shared service and therefore need to be upgraded.</span></span>|  
  
###  <a name="service-application-and-proxy-cmdlets"></a><a name="bkmk_serviceapp_cmdlets"></a> <span data-ttu-id="b9868-163">サービス アプリケーションとプロキシ コマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-163">Service Application and Proxy Cmdlets</span></span>  
 <span data-ttu-id="b9868-164">次の表には、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションとそれらに関連付けられたプロキシ用の PowerShell コマンドレットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9868-164">The following table contains the PowerShell cmdlets for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications and their associated proxies.</span></span>  
  
|<span data-ttu-id="b9868-165">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-165">cmdlet</span></span>|<span data-ttu-id="b9868-166">[説明]</span><span class="sxs-lookup"><span data-stu-id="b9868-166">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b9868-167">Get-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="b9868-167">Get-SPRSServiceApplication</span></span>|<span data-ttu-id="b9868-168">1 つ以上の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="b9868-168">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application objects.</span></span>|  
|<span data-ttu-id="b9868-169">New-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="b9868-169">New-SPRSServiceApplication</span></span>|<span data-ttu-id="b9868-170">新しい Reporting Services サービス アプリケーションと、それに関連付けられたデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9868-170">Create a new Reporting Services service application and associated databases.</span></span><br /><br /> <span data-ttu-id="b9868-171">LogonType パラメーター: レポート サーバーが、レポート サーバー データベースへのアクセスに SSRS Application Pool アカウントと SQL Server ログインのどちらを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9868-171">LogonType Parameter: Specifies if the report server uses the SSRS Application Pool account or a SQL Server login to access the report server database.</span></span> <span data-ttu-id="b9868-172">次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b9868-172">It can be one of the following:</span></span><br /><br /> <span data-ttu-id="b9868-173">0 Windows 認証</span><span class="sxs-lookup"><span data-stu-id="b9868-173">0 Windows Authentication</span></span><br /><br /> <span data-ttu-id="b9868-174">1 SQL Server</span><span class="sxs-lookup"><span data-stu-id="b9868-174">1 SQL Server</span></span><br /><br /> <span data-ttu-id="b9868-175">2 アプリケーション プール アカウント (既定)</span><span class="sxs-lookup"><span data-stu-id="b9868-175">2 Application Pool Account (default)</span></span>|  
|<span data-ttu-id="b9868-176">Remove-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="b9868-176">Remove-SPRSServiceApplication</span></span>|<span data-ttu-id="b9868-177">指定した Reporting Services サービス アプリケーションを削除します。</span><span class="sxs-lookup"><span data-stu-id="b9868-177">Removes the specified Reporting Services service application.</span></span> <span data-ttu-id="b9868-178">これを実行すると、関連付けられたデータベースも削除されます。</span><span class="sxs-lookup"><span data-stu-id="b9868-178">This will also remove the associated databases.</span></span>|  
|<span data-ttu-id="b9868-179">Set-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="b9868-179">Set-SPRSServiceApplication</span></span>|<span data-ttu-id="b9868-180">既存の Reporting Services サービス アプリケーションのプロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="b9868-180">Edits the properties of an existing Reporting Services service application.</span></span>|  
|<span data-ttu-id="b9868-181">New-SPRSServiceApplicationProxy</span><span class="sxs-lookup"><span data-stu-id="b9868-181">New-SPRSServiceApplicationProxy</span></span>|<span data-ttu-id="b9868-182">新しい Reporting Services サービス アプリケーション プロキシを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9868-182">Creates a new Reporting Services service application proxy.</span></span>|  
|<span data-ttu-id="b9868-183">Get-SPRSServiceApplicationProxy</span><span class="sxs-lookup"><span data-stu-id="b9868-183">Get-SPRSServiceApplicationProxy</span></span>|<span data-ttu-id="b9868-184">1 つ以上の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション プロキシを取得します。</span><span class="sxs-lookup"><span data-stu-id="b9868-184">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application proxies.</span></span>|  
|<span data-ttu-id="b9868-185">Dismount-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="b9868-185">Dismount-SPRSDatabase</span></span>|<span data-ttu-id="b9868-186">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション用のサービス アプリケーション データベースをマウント解除します。</span><span class="sxs-lookup"><span data-stu-id="b9868-186">Dismounts the service application databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="b9868-187">Remove-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="b9868-187">Remove-SPRSDatabase</span></span>|<span data-ttu-id="b9868-188">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション用のサービス アプリケーション データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="b9868-188">Remove the service application databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="b9868-189">Set-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="b9868-189">Set-SPRSDatabase</span></span>|<span data-ttu-id="b9868-190">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションに関連付けられたデータベースのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b9868-190">Sets the properties of the databases associated to a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="b9868-191">Mount-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="b9868-191">Mount-SPRSDatabase</span></span>|<span data-ttu-id="b9868-192">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション用のデータベースをマウントします。</span><span class="sxs-lookup"><span data-stu-id="b9868-192">Mounts databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="b9868-193">New-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="b9868-193">New-SPRSDatabase</span></span>|<span data-ttu-id="b9868-194">指定した [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション用の新しいサービス アプリケーション データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9868-194">Create new service application databases for the specified [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="b9868-195">Get-SPRSDatabaseCreationScript</span><span class="sxs-lookup"><span data-stu-id="b9868-195">Get-SPRSDatabaseCreationScript</span></span>|<span data-ttu-id="b9868-196">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション用に、データベース作成スクリプトを画面に出力します。</span><span class="sxs-lookup"><span data-stu-id="b9868-196">Outputs the database creation script to the screen for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="b9868-197">その後、SQL Server Management Studio でスクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9868-197">You can then run the script in SQL Server Management Studio.</span></span>|  
|<span data-ttu-id="b9868-198">Get-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="b9868-198">Get-SPRSDatabase</span></span>|<span data-ttu-id="b9868-199">1 つ以上の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション データベースを取得します。</span><span class="sxs-lookup"><span data-stu-id="b9868-199">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application databases.</span></span> <span data-ttu-id="b9868-200">Set-SPRSDatabase コマンドレットを使用して `querytimeout`などのプロパティを変更できるように、コマンドを使用してサービス アプリケーション データベースの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9868-200">Use the command to get the ID of service application database so you can use the Set-SPRSDatabase comdlet to modify properties, for example the `querytimeout`.</span></span> <span data-ttu-id="b9868-201">このトピックの例を参照してください。たとえば、データベースのタイムアウトなど、 [Reporting Servicea アプリケーションデータベースのプロパティを取得して設定](#bkmk_example_db_properties)します。</span><span class="sxs-lookup"><span data-stu-id="b9868-201">See the example in this topic, [Get and set properties of the Reporting Servicea application database, for example database timeout](#bkmk_example_db_properties).</span></span>|  
|<span data-ttu-id="b9868-202">Get-SPRSDatabaseRightsScript</span><span class="sxs-lookup"><span data-stu-id="b9868-202">Get-SPRSDatabaseRightsScript</span></span>|<span data-ttu-id="b9868-203">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション用に、データベース権限スクリプトを画面に出力します。</span><span class="sxs-lookup"><span data-stu-id="b9868-203">Outputs the database rights script to the screen for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="b9868-204">これを実行すると、対象のユーザーとデータベースの入力を求めるプロンプトが表示され、権限を変更するための Transact-SQL が返されます。</span><span class="sxs-lookup"><span data-stu-id="b9868-204">It will prompt for desired user and database then returns transact SQL you can run to modify permissions.</span></span> <span data-ttu-id="b9868-205">その後、SQL Server Management Studio でこのスクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9868-205">You can then run this script in SQL Server Management Studio.</span></span>|  
|<span data-ttu-id="b9868-206">Get-SPRSDatabaseUpgradeScript</span><span class="sxs-lookup"><span data-stu-id="b9868-206">Get-SPRSDatabaseUpgradeScript</span></span>|<span data-ttu-id="b9868-207">データベース アップグレード スクリプトを画面に出力します。</span><span class="sxs-lookup"><span data-stu-id="b9868-207">Outputs a database upgrade script to the screen.</span></span> <span data-ttu-id="b9868-208">このスクリプトは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション データベースを、現在の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] インストールのデータベース バージョンにアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="b9868-208">The script will upgrade [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application databases to the database version of the current [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installation.</span></span>|  
  
###  <a name="reporting-services-custom-functionality-cmdlets"></a><a name="bkmk_ssrsfeatures_cmdlets"></a><span data-ttu-id="b9868-209">カスタム機能のコマンドレットの Reporting Services</span><span class="sxs-lookup"><span data-stu-id="b9868-209">Reporting Services Custom Functionality Cmdlets</span></span>  
  
|<span data-ttu-id="b9868-210">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="b9868-210">Cmdlet</span></span>|<span data-ttu-id="b9868-211">説明</span><span class="sxs-lookup"><span data-stu-id="b9868-211">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b9868-212">Update-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="b9868-212">Update-SPRSEncryptionKey</span></span>|<span data-ttu-id="b9868-213">指定した Reporting Services サービス アプリケーションの暗号化キーを更新し、そのデータを再暗号化します。</span><span class="sxs-lookup"><span data-stu-id="b9868-213">Updates the encryption key for the specified Reporting Services service application and re-encrypts its data.</span></span>|  
|<span data-ttu-id="b9868-214">Restore-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="b9868-214">Restore-SPRSEncryptionKey</span></span>|<span data-ttu-id="b9868-215">以前にバックアップした、Reporting Services サービス アプリケーションの暗号化キーを復元します。</span><span class="sxs-lookup"><span data-stu-id="b9868-215">Restores a previously backed up encryption key for a Reporting Services service application.</span></span>|  
|<span data-ttu-id="b9868-216">Remove-SPRSEncryptedData</span><span class="sxs-lookup"><span data-stu-id="b9868-216">Remove-SPRSEncryptedData</span></span>|<span data-ttu-id="b9868-217">指定した Reporting Services サービス アプリケーションの暗号化されたデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="b9868-217">Delete the encrypted data for the specified Reporting Services service application.</span></span>|  
|<span data-ttu-id="b9868-218">Backup-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="b9868-218">Backup-SPRSEncryptionKey</span></span>|<span data-ttu-id="b9868-219">指定した Reporting Services サービス アプリケーションの暗号化キーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="b9868-219">Backs up the encryption key for the specified Reporting Services service application.</span></span>|  
|<span data-ttu-id="b9868-220">New-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="b9868-220">New-SPRSExtension</span></span>|<span data-ttu-id="b9868-221">新しい拡張機能を Reporting Services サービス アプリケーションに登録します。</span><span class="sxs-lookup"><span data-stu-id="b9868-221">Registers a new extension with a Reporting Services service application.</span></span>|  
|<span data-ttu-id="b9868-222">Set-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="b9868-222">Set-SPRSExtension</span></span>|<span data-ttu-id="b9868-223">既存の Reporting Services 拡張機能のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b9868-223">Sets the properties of an existing Reporting Services extension.</span></span>|  
|<span data-ttu-id="b9868-224">Remove-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="b9868-224">Remove-SPRSExtension</span></span>|<span data-ttu-id="b9868-225">Reporting Services サービス アプリケーションから拡張機能を削除します。</span><span class="sxs-lookup"><span data-stu-id="b9868-225">Removes an extension from a Reporting Services service application.</span></span>|  
|<span data-ttu-id="b9868-226">Get-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="b9868-226">Get-SPRSExtension</span></span>|<span data-ttu-id="b9868-227">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーション用の、1 つ以上の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 拡張機能を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9868-227">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] extensions for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span><br /><br /> <span data-ttu-id="b9868-228">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b9868-228">Valid values are:</span></span><br /><br /> <span data-ttu-id="b9868-229">**配信**</span><span class="sxs-lookup"><span data-stu-id="b9868-229">**Delivery**</span></span><br /><br /> <span data-ttu-id="b9868-230">**DeliveryUI**</span><span class="sxs-lookup"><span data-stu-id="b9868-230">**DeliveryUI**</span></span><br /><br /> <span data-ttu-id="b9868-231">**レンダリング**</span><span class="sxs-lookup"><span data-stu-id="b9868-231">**Render**</span></span><br /><br /> <span data-ttu-id="b9868-232">**データ**</span><span class="sxs-lookup"><span data-stu-id="b9868-232">**Data**</span></span><br /><br /> <span data-ttu-id="b9868-233">**Security**</span><span class="sxs-lookup"><span data-stu-id="b9868-233">**Security**</span></span><br /><br /> <span data-ttu-id="b9868-234">**認証**</span><span class="sxs-lookup"><span data-stu-id="b9868-234">**Authentication**</span></span><br /><br /> <span data-ttu-id="b9868-235">**EventProcessing**</span><span class="sxs-lookup"><span data-stu-id="b9868-235">**EventProcessing**</span></span><br /><br /> <span data-ttu-id="b9868-236">**ReportItems**</span><span class="sxs-lookup"><span data-stu-id="b9868-236">**ReportItems**</span></span><br /><br /> <span data-ttu-id="b9868-237">**Designer**</span><span class="sxs-lookup"><span data-stu-id="b9868-237">**Designer**</span></span><br /><br /> <span data-ttu-id="b9868-238">**ReportItemDesigner**</span><span class="sxs-lookup"><span data-stu-id="b9868-238">**ReportItemDesigner**</span></span><br /><br /> <span data-ttu-id="b9868-239">**ReportItemConverter**</span><span class="sxs-lookup"><span data-stu-id="b9868-239">**ReportItemConverter**</span></span><br /><br /> <span data-ttu-id="b9868-240">**ReportDefinitionCustomization**</span><span class="sxs-lookup"><span data-stu-id="b9868-240">**ReportDefinitionCustomization**</span></span>|  
|<span data-ttu-id="b9868-241">Get-SPRSSite</span><span class="sxs-lookup"><span data-stu-id="b9868-241">Get-SPRSSite</span></span>|<span data-ttu-id="b9868-242">"ReportingService" 機能が有効になっているかどうかに基づいて SharePoint サイトを取得します。</span><span class="sxs-lookup"><span data-stu-id="b9868-242">Gets the SharePoint sites based on whether the "ReportingService" feature is enabled.</span></span> <span data-ttu-id="b9868-243">既定では、"ReportingService" 機能が有効になっているサイトが返されます。</span><span class="sxs-lookup"><span data-stu-id="b9868-243">By default, sites that enable the "ReportingService" feature are returned.</span></span>|  
  
##  <a name="basic-samples"></a><a name="bkmk_basic_samples"></a><span data-ttu-id="b9868-244">基本的なサンプル</span><span class="sxs-lookup"><span data-stu-id="b9868-244">Basic Samples</span></span>  
 <span data-ttu-id="b9868-245">名前に 'SPRS' を含んでいるコマンドレットの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="b9868-245">Return a list of cmdlets that contain 'SPRS' in the name.</span></span> <span data-ttu-id="b9868-246">これは [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] コマンドレットの完全な一覧になります。</span><span class="sxs-lookup"><span data-stu-id="b9868-246">This will be the full list of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlets.</span></span>  
  
```powershell
Get-command -noun *SPRS*  
```  
  
 <span data-ttu-id="b9868-247">または、より詳細な情報を使用して、commandlist.txt という名前のテキスト ファイルにパイプします。</span><span class="sxs-lookup"><span data-stu-id="b9868-247">Or with a little more detail, piped to a text file named commandlist.txt</span></span>  
  
```powershell
Get-Command -Noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 <span data-ttu-id="b9868-248">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint サービスおよびサービス プロキシをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b9868-248">Install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint service and service proxy.</span></span>  
  
```powershell
Install-SPRSService  
```  
  
```powershell
Install-SPRSServiceProxy  
```  
  
 <span data-ttu-id="b9868-249">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="b9868-249">Start the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service</span></span>  
  
```powershell
Get-SPServiceInstance -all | where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 <span data-ttu-id="b9868-250">SharePoint 管理シェルから次のコマンドを入力すると、フィルター処理された行のリストがログ ファイルから返されます。</span><span class="sxs-lookup"><span data-stu-id="b9868-250">Type the following command from the SharePoint Management Shell to return a filtered list of rows from the a log file.</span></span> <span data-ttu-id="b9868-251">このコマンドを実行すると、"ssrscustomactionerror" を含む行がフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="b9868-251">The command will filter for lines that contain "ssrscustomactionerror".</span></span> <span data-ttu-id="b9868-252">この例では、rssharepoint.msi のインストール時に作成されたログ ファイルが検索対象となっています。</span><span class="sxs-lookup"><span data-stu-id="b9868-252">This example is looking at the log file created when the rssharepoint.msi was installed.</span></span>  
  
```powershell
Get-Content -Path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"  
```  
  
##  <a name="detailed-samples"></a><a name="bkmk_detailedsamples"></a><span data-ttu-id="b9868-253">詳細なサンプル</span><span class="sxs-lookup"><span data-stu-id="b9868-253">Detailed Samples</span></span>  
 <span data-ttu-id="b9868-254">次のサンプルに加えて、[手順1-4 の Windows powershell スクリプトに関する](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script)トピックの「Windows powershell スクリプト」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9868-254">In addition to the following samples, see the section "Windows PowerShell Script" in the topic [Windows PowerShell script for Steps 1-4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).</span></span>  
  
###  <a name="create-a-reporting-services-service-application-and-proxy"></a><a name="bkmk_example_create_service_application"></a><span data-ttu-id="b9868-255">Reporting Services サービスアプリケーションとプロキシを作成する</span><span class="sxs-lookup"><span data-stu-id="b9868-255">Create a Reporting Services service application and proxy</span></span>  
 <span data-ttu-id="b9868-256">このサンプル スクリプトは次のタスクを完了します。</span><span class="sxs-lookup"><span data-stu-id="b9868-256">This sample script completes the following tasks:</span></span>  
  
1.  <span data-ttu-id="b9868-257">Reporting Services サービス アプリケーションとプロキシを作成する。</span><span class="sxs-lookup"><span data-stu-id="b9868-257">Create a Reporting Services service application and proxy.</span></span> <span data-ttu-id="b9868-258">このスクリプトは、"My App Pool" というアプリケーション プールが既に存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b9868-258">The script assumes the application pool "My App Pool" already exists.</span></span>  
  
2.  <span data-ttu-id="b9868-259">作成したプロキシを既定のプロキシ グループに追加する。</span><span class="sxs-lookup"><span data-stu-id="b9868-259">Add the proxy to the default proxy group</span></span>  
  
3.  <span data-ttu-id="b9868-260">ポート 80 の Web アプリケーションのコンテンツ データベースに、サービス アプリケーション アクセス権を付与する。</span><span class="sxs-lookup"><span data-stu-id="b9868-260">Grant the service app access to the port 80 web app's content database.</span></span> <span data-ttu-id="b9868-261">このスクリプトは、サイト " http://sitename " が既に存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b9868-261">The script assumes site "http://sitename" already exists.</span></span>  
  
```powershell
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool "My App Pool"  
$serviceApp = New-SPRSServiceApplication "My RS Service App" -ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy -Name "My RS Service App Proxy" -ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application's content database.  
$webApp = Get-SPWebApplication "http://sitename"  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)
```  
  
###  <a name="review-and-update-a-reporting-services-delivery-extension"></a><a name="bkmk_example_delivery_extension"></a><span data-ttu-id="b9868-262">Reporting Services 配信拡張機能の確認と更新</span><span class="sxs-lookup"><span data-stu-id="b9868-262">Review and update a Reporting Services delivery extension</span></span>  
 <span data-ttu-id="b9868-263">次の PowerShell スクリプトの例では、 `My RS Service App`という名前のサービス アプリケーションについて、レポート サーバーの電子メール配信拡張機能の構成を更新します。</span><span class="sxs-lookup"><span data-stu-id="b9868-263">The following PowerShell script example, updates the configuration for the report server e-mail delivery extension for the service application named `My RS Service App`.</span></span> <span data-ttu-id="b9868-264">SMTP サーバー (`<email server name>`) と差出人の電子メール別名 (`<your FROM email address>`) の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="b9868-264">Update the values for the SMTP server (`<email server name>`) and the FROM email alias (`<your FROM email address>`).</span></span>  
  
```powershell
$app = Get-SPRSServiceApplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
$emailXml = [xml]$emailCfg
$emailXml.SelectSingleNode("//SMTPServer").InnerText = "<email server name>"  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 <span data-ttu-id="b9868-265">上の例で、サービス アプリケーションの正確な名前がわからない場合は、最初のステートメントを書き換えて、サービス アプリケーションを部分名検索に基づいて取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9868-265">In the above example if you did not know the exact name of the service application, you could rewrite the first statement to get the service application based on a search of the partial name.</span></span> <span data-ttu-id="b9868-266">例:</span><span class="sxs-lookup"><span data-stu-id="b9868-266">For example:</span></span>  
  
```powershell
$app = Get-SPRSServiceApplication | Where {$_.name -like " ssrs_testapp *"}  
```  
  
 <span data-ttu-id="b9868-267">次のスクリプトは、"Reporting Services Application" という名前のサービス アプリケーションについて、レポート サーバーの電子メール配信拡張機能の現在の構成値を返します。</span><span class="sxs-lookup"><span data-stu-id="b9868-267">The following script will return the current configuration values for the report server e-mail delivery extension for the service application named "Reporting Services Application".</span></span> <span data-ttu-id="b9868-268">最初のステップでは、"My RS Service App" という名前のサービス アプリケーションのオブジェクトに、変数 $app の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="b9868-268">The first step sets the value of the variable $app to the object of the service application that has a name of " My RS Service App "</span></span>  
  
 <span data-ttu-id="b9868-269">2 番目のステートメントは、変数 $app 内のサービス アプリケーション オブジェクト用の "レポート サーバー電子メール" 配信拡張機能を取得し、configurationXML を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9868-269">The second statement will Get the 'Report Server Email' delivery extension for the service application object in variable $app, and select the configurationXML</span></span>  
  
```powershell
$app = Get-SPRSServiceapplication -Name "Reporting Services Application"  
Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
 <span data-ttu-id="b9868-270">上の 2 つのステートメントを次のように書き直して 1 つのステートメントにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b9868-270">You can also rewrite the above two statements as one:</span></span>  
  
```powershell
Get-SPRSServiceApplication -Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="get-and-set-properties-of-the-reporting-servicea-application-database-for-example-database-timeout"></a><a name="bkmk_example_db_properties"></a><span data-ttu-id="b9868-271">Reporting Servicea アプリケーションデータベースのプロパティの取得と設定 (データベースのタイムアウトなど)</span><span class="sxs-lookup"><span data-stu-id="b9868-271">Get and set properties of the Reporting Servicea application database, for example database timeout</span></span>  
 <span data-ttu-id="b9868-272">次の例では、set コマンドに指定するデータベースの GUID (ID) を確認できるように、最初にデータベースとプロパティの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="b9868-272">The following example first returns a list of the databases and properties so you can determine the database guid (ID) that you then supply to the set command.</span></span> <span data-ttu-id="b9868-273">プロパティの一覧については、「 `Get-SPRSDatabase | format-list`」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9868-273">For a full list of the properties, use `Get-SPRSDatabase | format-list`.</span></span>  
  
```powershell
Get-SPRSDatabase | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance
```  
  
 <span data-ttu-id="b9868-274">出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b9868-274">The following is an example of the output.</span></span> <span data-ttu-id="b9868-275">変更するデータベースの ID を確認し、SET コマンドレットでその ID を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9868-275">Determine the ID for the database you want to modify and use the ID in the SET cmdlet.</span></span>  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```powershell
Set-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 <span data-ttu-id="b9868-276">値が設定されていることを確認するには、もう一度 GET コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="b9868-276">To verify the value is set, run the GET cmdlet again.</span></span>  
  
```powershell
Get-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="list-reporting-services-data-extensions---sharepoint-mode"></a><a name="bkmk_example_list_data_extensions"></a><span data-ttu-id="b9868-277">Reporting services データ拡張機能の一覧表示-SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="b9868-277">List reporting services data extensions - SharePoint mode</span></span>  
 <span data-ttu-id="b9868-278">次の例では、各 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションの間をループし、それぞれの現在のデータ拡張機能を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b9868-278">The following example loops through each [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application and lists the current data extensions for each.</span></span>  
  
```powershell
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType "Data" | select name, extensiontype | Format-Table -AutoSize  
}  
```  
  
 <span data-ttu-id="b9868-279">**出力例:**</span><span class="sxs-lookup"><span data-stu-id="b9868-279">**Example output:**</span></span>  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="change-and-list-subscription-owners"></a><a name="bkmk_change_subscription_owner"></a><span data-ttu-id="b9868-280">サブスクリプション所有者の変更と一覧表示</span><span class="sxs-lookup"><span data-stu-id="b9868-280">Change and list subscription owners</span></span>  
 <span data-ttu-id="b9868-281">「 [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9868-281">See [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9868-282">参照</span><span class="sxs-lookup"><span data-stu-id="b9868-282">See Also</span></span>  
 <span data-ttu-id="b9868-283">[PowerShell を使用して Reporting Services サブスクリプションの所有者を変更および一覧表示し、サブスクリプションを実行する](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="b9868-283">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md) </span></span>  
 <span data-ttu-id="b9868-284">[チェックリスト: PowerShell を使用して PowerPivot for SharePoint を確認する](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint) </span><span class="sxs-lookup"><span data-stu-id="b9868-284">[CheckList: Use PowerShell to Verify PowerPivot for SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint) </span></span>  
 [<span data-ttu-id="b9868-285">CodePlex SharePoint 管理 PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="b9868-285">CodePlex SharePoint Management PowerShell scripts</span></span>](https://sharepointpsscripts.codeplex.com/)   
