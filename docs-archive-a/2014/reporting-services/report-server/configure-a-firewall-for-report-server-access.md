---
title: レポート サーバー アクセスに対するファイアウォールの構成 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b578c980522d24f5a24a73fdfd080ec425335aac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642570"
---
# <a name="configure-a-firewall-for-report-server-access"></a><span data-ttu-id="2c1ec-102">レポート サーバー アクセスに対するファイアウォールの構成</span><span class="sxs-lookup"><span data-stu-id="2c1ec-102">Configure a Firewall for Report Server Access</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="2c1ec-103">レポート サーバー アプリケーションとパブリッシュされたレポートには、IP アドレス、ポート、および仮想ディレクトリを指定した URL を通じてアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-103">Report server applications and published reports are accessed through URLs that specify an IP address, port, and virtual directory.</span></span> <span data-ttu-id="2c1ec-104">Windows ファイアウォールが有効になっている場合、レポート サーバーで使用するように構成されているポートは閉じられる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-104">If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed.</span></span> <span data-ttu-id="2c1ec-105">ポートが閉じていると、レポートの要求後に空白の Web ページが表示されたり、リモートのクライアント コンピューターからレポート マネージャーを開こうとしたときに空白のページが表示されたりします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-105">Indications that a port might be closed are the appearance of a blank Web page after requesting a report, or a blank page when you attempt to open Report Manager from a remote client computer.</span></span>  
  
 <span data-ttu-id="2c1ec-106">ポートを開くには、レポート サーバー コンピューターで Windows ファイアウォール ユーティリティを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-106">To open a port, you must use the Windows Firewall utility on the report server computer.</span></span> <span data-ttu-id="2c1ec-107">ポートは Reporting Services によって自動的に開かれないので、この手順を手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-107">Reporting Services will not open ports for you; you must perform this step manually.</span></span>  
  
 <span data-ttu-id="2c1ec-108">既定では、レポート サーバーはポート 80 で HTTP 要求をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-108">By default, the report server listens for HTTP requests on port 80.</span></span> <span data-ttu-id="2c1ec-109">このため、以下に示す手順ではそのポートを指定しています。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-109">As such, the following instructions include steps that specify that port.</span></span> <span data-ttu-id="2c1ec-110">別のポートを使用するようにレポート サーバーの URL を構成している場合は、以下に示す手順を実行するときにそのポート番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-110">If you configured the report server URLs to use a different port, you must specify that port number when following the instructions below.</span></span>  
  
 <span data-ttu-id="2c1ec-111">外部コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リレーショナル データベースにアクセスする場合、またはレポート サーバー データベースが外部の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに置かれている場合は、外部コンピューターのポート 1433 および 1434 を開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-111">If you are accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational databases on external computers, or if the report server database is on an external [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, you must open port 1433 and 1434 on the external computer.</span></span> <span data-ttu-id="2c1ec-112">Windows ファイアウォールの詳細については、 [オンライン ブックの「](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-112">For more information, see [Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="2c1ec-113">Windows ファイアウォールの既定の設定に関する詳細と、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に影響する TCP ポートの説明については、 [オンライン ブックの「](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) SQL Server のアクセスを許可するための Windows ファイアウォールの構成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-113">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2c1ec-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="2c1ec-114">Prerequisites</span></span>  
 <span data-ttu-id="2c1ec-115">次の手順では、既にサービス アカウントを構成し、レポート サーバー データベースを作成し、レポート サーバー Web サービスとレポート マネージャーの URL を構成していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-115">These instructions assume that you already configured the service account, created the report server database, and configured URLs for the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="2c1ec-116">詳細については、「 [Reporting Services ネイティブ モードのレポート サーバーの管理](manage-a-reporting-services-native-mode-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-116">For more information, see [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="2c1ec-117">また、ローカル レポート サーバー インスタンスへのローカル Web ブラウザー接続を通じてレポート サーバーにアクセスできることを確認しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-117">You should also have verified that the report server is accessible over a local Web browser connection to the local report server instance.</span></span> <span data-ttu-id="2c1ec-118">この手順によって、作業環境が整っているかどうかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-118">This step establishes that you have a working installation.</span></span> <span data-ttu-id="2c1ec-119">ポートを開く前に、環境が正しく構成されているかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-119">You should verify that the installation is configured correctly before you begin opening ports.</span></span> <span data-ttu-id="2c1ec-120">Windows Server でこの手順を完了するには、レポート サーバー サイトを [信頼済みサイト] に追加しておくことも必要です。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-120">To complete this step on  Windows Server, you must have also added the report server site to Trusted Sites.</span></span> <span data-ttu-id="2c1ec-121">詳細については、「 [ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-121">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="opening-ports-in-windows-firewall"></a><span data-ttu-id="2c1ec-122">Windows ファイアウォールでポートを開く</span><span class="sxs-lookup"><span data-stu-id="2c1ec-122">Opening Ports in Windows Firewall</span></span>  
 <span data-ttu-id="2c1ec-123">Windows ファイアウォールのバージョンによって手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-123">There are separate instructions for different versions of Windows Firewall.</span></span>  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a><span data-ttu-id="2c1ec-124">Windows 7、Windows Server 2008 R2、Windows Server 2012 および 2012 R2 でポート 80 を開くには</span><span class="sxs-lookup"><span data-stu-id="2c1ec-124">To open port 80 on Windows 7, Windows Server 2008 R2, Windows Server 2012 and 2012 R2</span></span>  
  
1.  <span data-ttu-id="2c1ec-125">**[スタート]** メニューの **[コントロール パネル]** をクリックし、 **[システムとセキュリティ]**、 **[Windows ファイアウォール]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-125">From the **Start** menu, click **Control Panel**, click **System and Security**, and then click **Windows Firewall**.</span></span> <span data-ttu-id="2c1ec-126">コントロール パネルの表示方法が [カテゴリ] 以外の場合は、単に **[Windows ファイアウォール]** を選択するだけでかまいません。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-126">Control Panel is not configured for 'Category' view, you only need to select **Windows Firewall.**</span></span>  
  
2.  <span data-ttu-id="2c1ec-127">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-127">Click **Advanced Settings**.</span></span>  
  
3.  <span data-ttu-id="2c1ec-128">**[受信の規則]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-128">Click **Inbound Rules.**</span></span>  
  
4.  <span data-ttu-id="2c1ec-129">**[操作]** ウィンドウで **[新しい規則]** をクリックします **。**</span><span class="sxs-lookup"><span data-stu-id="2c1ec-129">Click **New Rule** in the **Actions** window **.**</span></span>  
  
5.  <span data-ttu-id="2c1ec-130">**[ポート]** の **[規則の種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-130">Click **Rule Type** of **Port.**</span></span>  
  
6.  <span data-ttu-id="2c1ec-131">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-131">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="2c1ec-132">**[プロトコルおよびポート]** ページで、 **[TCP]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-132">On the **Protocol and Ports** page click **TCP**.</span></span>  
  
8.  <span data-ttu-id="2c1ec-133">**[特定のローカル ポート]** を選択し、「 **80**」という値を入力します。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-133">Select **Specific Local Ports** and type a value of **80**.</span></span>  
  
9. <span data-ttu-id="2c1ec-134">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-134">Click **Next**.</span></span>  
  
10. <span data-ttu-id="2c1ec-135">**[操作]** ページで、 **[接続を許可する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-135">On the **Action** page click **Allow the connection**.</span></span>  
  
11. <span data-ttu-id="2c1ec-136">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-136">Click **Next**.</span></span>  
  
12. <span data-ttu-id="2c1ec-137">**[プロファイル]** ページで、実際の環境に合った適切なオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-137">On the **Profile** page click the appropriate options for your environment.</span></span>  
  
13. <span data-ttu-id="2c1ec-138">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-138">Click **Next**.</span></span>  
  
14. <span data-ttu-id="2c1ec-139">**[名前]** ページで、「**ReportServer (TCP on port 80)**」という名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-139">On the **Name** page enter a name of**ReportServer (TCP on port 80)**</span></span>  
  
15. <span data-ttu-id="2c1ec-140">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-140">Click **Finish**.</span></span>  
  
16. <span data-ttu-id="2c1ec-141">コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-141">Restart the computer.</span></span>  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a><span data-ttu-id="2c1ec-142">Windows Vista または Windows Server 2008 でポート 80 を開くには</span><span class="sxs-lookup"><span data-stu-id="2c1ec-142">To open port 80 on Windows Vista or Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="2c1ec-143">[**スタート**] ボタンをクリックし、[**コントロールパネル**]、[**セキュリティ**]、[ **Windows ファイアウォール**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-143">From the **Start** menu, click **Control Panel**, click **Security**, and then click **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="2c1ec-144">**[Windows ファイアウォールによるプログラムの許可]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-144">Click **Allow a program through Windows Firewall**.</span></span>  
  
3.  <span data-ttu-id="2c1ec-145">**[Continue]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-145">Click **Continue**.</span></span>  
  
4.  <span data-ttu-id="2c1ec-146">[例外] タブで、[**ポートの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-146">On the Exceptions tab, click **Add Port**.</span></span>  
  
5.  <span data-ttu-id="2c1ec-147">[名前] に「 **ReportServer (ポート80の TCP)**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-147">In Name, type **ReportServer (TCP on port 80)**.</span></span>  
  
6.  <span data-ttu-id="2c1ec-148">[ポート番号] に「 **80**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-148">In Port number, type **80**.</span></span>  
  
7.  <span data-ttu-id="2c1ec-149">**TCP**が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-149">Verify that **TCP** is selected.</span></span>  
  
8.  <span data-ttu-id="2c1ec-150">[**スコープの変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-150">Click **Change Scope**.</span></span>  
  
9. <span data-ttu-id="2c1ec-151">[**ネットワーク (サブネット) のみ**] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-151">Click **My network (subnet) only**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="2c1ec-152">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-152">Click **OK** to close the dialog box.</span></span>  
  
11. <span data-ttu-id="2c1ec-153">コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-153">Restart the computer.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2c1ec-154">次の手順</span><span class="sxs-lookup"><span data-stu-id="2c1ec-154">Next Steps</span></span>  
 <span data-ttu-id="2c1ec-155">ポートを開いた後、リモート ユーザーがそのポートでレポート サーバーにアクセスできるかどうかを確認する前に、ホームに対するロールとサイト レベルのロールの割り当てを行って、レポート サーバーへのアクセスをユーザーに許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-155">After you open the port and before you confirm whether remote users can access the report server on the port that you open, you must grant user access to the report server through role assignments on Home and at the site level.</span></span> <span data-ttu-id="2c1ec-156">ユーザーに十分な権限がない場合は、ポートを正しく開くことができてもレポート サーバーへの接続に失敗します。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-156">You can open a port correctly and still have report server connections fail if users do not have sufficient permissions.</span></span> <span data-ttu-id="2c1ec-157">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[レポート サーバーへのユーザー アクセスを許可する &#40;レポート マネージャー&#41;](../security/grant-user-access-to-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-157">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../security/grant-user-access-to-a-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="2c1ec-158">別のコンピューターでレポート マネージャーを起動することによって、ポートが正しく開かれているかどうかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-158">You can also verify that the port is opened correctly by starting Report Manager on a different computer.</span></span> <span data-ttu-id="2c1ec-159">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c1ec-159">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1ec-160">参照</span><span class="sxs-lookup"><span data-stu-id="2c1ec-160">See Also</span></span>  
 <span data-ttu-id="2c1ec-161">[レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2c1ec-161">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="2c1ec-162">[レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2c1ec-162">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="2c1ec-163">[SSRS Configuration Manager &#40;レポートサーバーデータベースを作成&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2c1ec-163">[Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="2c1ec-164">[レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2c1ec-164">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="2c1ec-165">Reporting Services ネイティブ モードのレポート サーバーの管理</span><span class="sxs-lookup"><span data-stu-id="2c1ec-165">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
