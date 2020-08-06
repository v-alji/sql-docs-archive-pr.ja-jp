---
title: ローカル管理用のネイティブ モードのレポート サーバー (SSRS) の構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- UAC
- installing Reporting Services
- Windows Vista
- Localhost
- windows server 2008
- Vista
ms.assetid: 312c6bb8-b3f7-4142-a55f-c69ee15bbf52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad53f293ef825a382d9e39b58527a36ef291687a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642569"
---
# <a name="configure-a-native-mode-report-server-for-local-administration-ssrs"></a><span data-ttu-id="dc2cd-102">ローカル管理用のネイティブ モードのレポート サーバー (SSRS) の構成</span><span class="sxs-lookup"><span data-stu-id="dc2cd-102">Configure a Native Mode Report Server for Local Administration (SSRS)</span></span>
  <span data-ttu-id="dc2cd-103">レポート サーバー インスタンスをローカルに管理しようとする場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーを次のオペレーティング システムのいずれかに配置するには、追加の構成手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-103">Deploying a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server on one of the following operating systems requires more configuration steps if you want to administer the report server instance locally.</span></span> <span data-ttu-id="dc2cd-104">このトピックでは、レポート サーバーをローカル管理用に構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-104">This topic explains how to configure the report server for local administration.</span></span> <span data-ttu-id="dc2cd-105">レポートサーバーをまだインストールしていない場合、または構成していない場合は、[インストールウィザードから SQL Server 2014 をインストール](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)し、 [Reporting Services ネイティブモードのレポートサーバーを](manage-a-reporting-services-native-mode-report-server.md)セットアップ&#41;&#40;します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-105">If you have not yet installed or configured the report server, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) and [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="dc2cd-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード</span><span class="sxs-lookup"><span data-stu-id="dc2cd-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
-   [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)]  
  
-   [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]  
  
-   [!INCLUDE[win8](../../includes/win8-md.md)]  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
 <span data-ttu-id="dc2cd-107">記載されているオペレーティング システムによって権限が制限されるため、ほとんどのアプリケーションは、ローカルの Administrators グループのメンバーが実行しても、標準ユーザー アカウントを使用しているかのように実行されます。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-107">Because the noted operating systems limit permissions, members of the local Administrators group run most applications as if they are using the Standard User account.</span></span>  
  
 <span data-ttu-id="dc2cd-108">これにより、システム全体のセキュリティが向上しますが、Reporting Services がローカル管理者のために作成するあらかじめ定義された組み込みのロールの割り当てを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-108">While this practice improves the overall security of your system, it prevents you from using the predefined, built-in role assignments that Reporting Services creates for local administrators.</span></span>  
  
-   [<span data-ttu-id="dc2cd-109">構成変更の概要</span><span class="sxs-lookup"><span data-stu-id="dc2cd-109">Overview of Configuration Changes</span></span>](#bkmk_configuraiton_overview)  
  
-   [<span data-ttu-id="dc2cd-110">ローカル レポート サーバーとレポート マネージャーの管理を構成するには</span><span class="sxs-lookup"><span data-stu-id="dc2cd-110">To Configure Local Report Server and Report Manager Administration</span></span>](#bkmk_configure_local_server)  
  
-   [<span data-ttu-id="dc2cd-111">ローカル レポート サーバー管理を行う目的で SQL Server Management Studio (SSMS) を構成するには</span><span class="sxs-lookup"><span data-stu-id="dc2cd-111">To Configure SQL Server Management Studio (SSMS) for local report server administration</span></span>](#bkmk_configure_ssms)  
  
-   [<span data-ttu-id="dc2cd-112">ローカル レポート サーバー管理を行う目的で SQL Server データ ツール BI (SSDT) を構成するには</span><span class="sxs-lookup"><span data-stu-id="dc2cd-112">To Configure SQL Server Data Tools BI (SSDT) to Publish to a Local Report Server</span></span>](#bkmk_configure_ssdt)  
  
-   [<span data-ttu-id="dc2cd-113">追加情報</span><span class="sxs-lookup"><span data-stu-id="dc2cd-113">Additional Information</span></span>](#bkmk_addiitonal_informaiton)  
  
##  <a name="overview-of-configuration-changes"></a><a name="bkmk_configuraiton_overview"></a> <span data-ttu-id="dc2cd-114">構成変更の概要</span><span class="sxs-lookup"><span data-stu-id="dc2cd-114">Overview of Configuration Changes</span></span>  
 <span data-ttu-id="dc2cd-115">以下に示す構成変更でサーバーを構成することにより、標準ユーザーの権限を使用してレポート サーバーのコンテンツや操作を管理できます。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-115">The following configuration changes configure the server so that you can use standard user permissions to manage report server content and operations:</span></span>  
  
-   <span data-ttu-id="dc2cd-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の URL を信頼済みサイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-116">Add [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs to trusted sites.</span></span> <span data-ttu-id="dc2cd-117">既定では、記載されているオペレーティング システムで動作している Internet Explorer は **保護モード**で実行されます。保護モードとは、同じコンピューターで実行されている高レベルのプロセスにブラウザーの要求が到達するのを防ぐ機能です。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-117">By default, Internet Explorer running on the listed operating systems runs in **Protected Mode**, a feature that blocks browser requests from reaching high-level processes that run on the same computer.</span></span> <span data-ttu-id="dc2cd-118">レポート サーバー アプリケーションを信頼済みサイトに追加することで、それらのアプリケーションに対して保護モードを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-118">You can disable protected mode for the report server applications by adding them as Trusted Sites.</span></span>  
  
-   <span data-ttu-id="dc2cd-119">Internet Explorer で **[管理者として実行]** 機能を使用しなくてもコンテンツや操作を管理できる権限をレポート サーバー管理者に与えるロールの割り当てを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-119">Create role assignments that grant you, the report server administrator, permission to manage content and operations without having to use the **Run as administrator** feature on Internet Explorer.</span></span> <span data-ttu-id="dc2cd-120">Windows ユーザー アカウントに対してロールの割り当てを作成することにより、Reporting Services が作成するあらかじめ定義された組み込みのロールの割り当てを置き換える明示的なロールの割り当てを使用して、コンテンツ マネージャーおよびシステム管理者の権限でレポート サーバーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-120">By creating role assignments for your Windows user account, you gain access to a report server with Content Manager and System Administrator permissions through explicit role assignments that replace the predefined, built-in role assignments that Reporting Services creates.</span></span>  
  
##  <a name="to-configure-local-report-server-and-report-manager-administration"></a><a name="bkmk_configure_local_server"></a><span data-ttu-id="dc2cd-121">ローカルレポートサーバーとレポートマネージャーの管理を構成するには</span><span class="sxs-lookup"><span data-stu-id="dc2cd-121">To Configure Local Report Server and Report Manager Administration</span></span>  
 <span data-ttu-id="dc2cd-122">ローカル レポート サーバーを参照しているときに、次のようなエラーが表示された場合は、このセクションの構成手順を完了してください。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-122">Complete the configuration steps in this section if you are browsing to a local report server and you see errors similar to the following:</span></span>  
  
-   <span data-ttu-id="dc2cd-123">ユーザー `'Domain\[user name]`' に必要なアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-123">User `'Domain\[user name]`' does not have required permissions.</span></span> <span data-ttu-id="dc2cd-124">適切なアクセス許可が付与されていることと、Windows ユーザー アカウント制御 (UAC) の制限に対処済みであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-124">Verify that sufficient permissions have been granted and Windows User Account Control (UAC) restrictions have been addressed.</span></span>  
  
###  <a name="trusted-site-settings-in-the-browser"></a><a name="bkmk_site_settings"></a><span data-ttu-id="dc2cd-125">ブラウザーでの信頼されたサイトの設定</span><span class="sxs-lookup"><span data-stu-id="dc2cd-125">Trusted Site Settings in the Browser</span></span>  
  
1.  <span data-ttu-id="dc2cd-126">[管理者として実行] の権限を使用してブラウザー ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-126">Open a browser window with Run as administrator permissions.</span></span> <span data-ttu-id="dc2cd-127">**[スタート]** メニューの **[すべてのプログラム]** をクリックし、 **[Internet Explorer]** を右クリックして **[管理者として実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-127">From the **Start** menu, click **All Programs**, right-click **Internet Explorer**, and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="dc2cd-128">**[許可]** をクリックして続行します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-128">Click **Allow** to continue.</span></span>  
  
3.  <span data-ttu-id="dc2cd-129">URL アドレスにレポート マネージャーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-129">In the URL address, enter the Report Manager URL.</span></span> <span data-ttu-id="dc2cd-130">手順については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[レポート マネージャー (SSRS ネイティブ モード)](../report-manager-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-130">For instructions, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="dc2cd-131">**[ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-131">Click **Tools**.</span></span>  
  
5.  <span data-ttu-id="dc2cd-132">**[インターネット オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-132">Click **Internet Options**.</span></span>  
  
6.  <span data-ttu-id="dc2cd-133">**[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-133">Click **Security**.</span></span>  
  
7.  <span data-ttu-id="dc2cd-134">**[信頼済みサイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-134">Click **Trusted Sites**.</span></span>  
  
8.  <span data-ttu-id="dc2cd-135">**[サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-135">Click **Sites**.</span></span>  
  
9. <span data-ttu-id="dc2cd-136">`http://<your-server-name>`を追加します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-136">Add `http://<your-server-name>`.</span></span>  
  
10. <span data-ttu-id="dc2cd-137">既定のサイトに HTTPS を使用していない場合は、 **[ゾーンのすべてのサイトにサーバー証明書 (https:) を必要とする]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-137">Clear the check box **Require server certification (https:) for all sites in this zone** if you are not using HTTPS for the default site.</span></span>  
  
11. <span data-ttu-id="dc2cd-138">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-138">Click **Add**.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-folder-settings"></a><a name="bkmk_configure_folder_settings"></a> <span data-ttu-id="dc2cd-139">レポート マネージャーのフォルダーの設定</span><span class="sxs-lookup"><span data-stu-id="dc2cd-139">Report Manager Folder Settings</span></span>  
  
1.  <span data-ttu-id="dc2cd-140">レポート マネージャーのホーム ページで、 **[フォルダー設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-140">In Report Manager, on the Home page, click **Folder Settings**.</span></span>  
  
2.  <span data-ttu-id="dc2cd-141">[フォルダー設定] ページの **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-141">In the Folder Settings page, click **Security**.</span></span>  
  
3.  <span data-ttu-id="dc2cd-142">**[新しいロールの割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-142">Click **New Role Assignment**.</span></span>  
  
4.  <span data-ttu-id="dc2cd-143">**[グループ名またはユーザー名]** フィールドに、 `<domain>\<user>`という形式で自分 (レポート サーバー管理者) の Windows ユーザー アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-143">In the **Group or user name** field, type your Windows user account in this format: `<domain>\<user>`.</span></span>  
  
5.  <span data-ttu-id="dc2cd-144">**[コンテンツ マネージャー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-144">Select **Content Manager**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-site-settings"></a><a name="bkmk_configure_site_settings"></a> <span data-ttu-id="dc2cd-145">レポート マネージャーのサイトの設定</span><span class="sxs-lookup"><span data-stu-id="dc2cd-145">Report Manager Site Settings</span></span>  
  
1.  <span data-ttu-id="dc2cd-146">管理者特権を使用してブラウザーを開き、レポート マネージャー ( `http://<server name>/reports`) を参照します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-146">Open your browser with administrative privileges and browse to report manager, `http://<server name>/reports`.</span></span>  
  
2.  <span data-ttu-id="dc2cd-147">ホーム ページの上隅にある **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-147">Click **Site Settings** in the upper corner of the Home page.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="dc2cd-148">**注:\*\*\*\*[サイトの設定]** オプションが表示されない場合は、ブラウザーを閉じて、管理者特権を使用してもう一度開き、レポート マネージャーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-148">**Note:** If you do not see the **Site Settings** option, close and reopen your browser and browse to report manager with administrative privileges.</span></span>  
  
3.  <span data-ttu-id="dc2cd-149">[**セキュリティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-149">Click **security**.</span></span>  
  
4.  <span data-ttu-id="dc2cd-150">**[新しいロールの割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-150">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="dc2cd-151">**[グループ名またはユーザー名]** フィールドに、 `<domain>\<user>`という形式で自分 (レポート サーバー管理者) の Windows ユーザー アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-151">In the **Group or user name** field, type your Windows user account in this format: `<domain>\<user>`.</span></span>  
  
6.  <span data-ttu-id="dc2cd-152">**[システム管理者]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-152">Select **System Administrator**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="dc2cd-153">レポート マネージャーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-153">Close Report Manager.</span></span>  
  
9. <span data-ttu-id="dc2cd-154">**[管理者として実行]** を使用せずに再び Internet Explorer でレポート マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-154">Re-open Report Manager in Internet Explorer, without using **Run as administrator**.</span></span>  
  
##  <a name="to-configure-sql-server-management-studio-ssms-for-local-report-server-administration"></a><a name="bkmk_configure_ssms"></a><span data-ttu-id="dc2cd-155">ローカルレポートサーバー管理用に SQL Server Management Studio (SSMS) を構成するには</span><span class="sxs-lookup"><span data-stu-id="dc2cd-155">To Configure SQL Server Management Studio (SSMS) for local report server administration</span></span>  
 <span data-ttu-id="dc2cd-156">既定では、管理者権限を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開始した場合以外は、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で使用できるレポート サーバー プロパティのいずれにもアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-156">By default, you cannot access all of the report server properties available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] unless you start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
 <span data-ttu-id="dc2cd-157">**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** ロール プロパティとロールの割り当てを構成して、高度なアクセス許可で [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を毎回起動する必要をなくすには、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-157">**To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** role properties and role assignments so you do not need to start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with elevated permissions each time:</span></span>  
  
-   <span data-ttu-id="dc2cd-158">**[スタート]** メニューの **[すべてのプログラム]** をクリックし、 **[SQL Server 2014]** をクリックし、 **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]** を右クリックして **[管理者として実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-158">From the **Start** menu, click **All Programs**, click **SQL Server 2014**, right-click **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**, and then click **Run as administrator**.</span></span>  
  
-   <span data-ttu-id="dc2cd-159">ローカル [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="dc2cd-159">Connect to your local [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server.</span></span>  
  
-   <span data-ttu-id="dc2cd-160">**[セキュリティ]** ノードで、 **[システム ロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-160">In the **Security** node, click **System Roles**.</span></span>  
  
-   <span data-ttu-id="dc2cd-161">**[システム管理者]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-161">Right-click **System Administrator** and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="dc2cd-162">**[システム ロールのプロパティ]** ページで、 **[レポート サーバーのプロパティを表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-162">In the **System Role Properties** page, select **View report server properties**.</span></span> <span data-ttu-id="dc2cd-163">システム管理者ロールを持つメンバーに割り当てる他のすべてのプロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-163">Select any other properties you want associated with members of the system administrators role.</span></span>  
  
-   <span data-ttu-id="dc2cd-164">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-164">Click **OK**.</span></span>  
  
-   <span data-ttu-id="dc2cd-165">[閉じる] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc2cd-165">Close [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]</span></span>  
  
-   <span data-ttu-id="dc2cd-166">システム ロール "システム管理者" にユーザーを追加するには、このトピックで既に登場した「 [レポート マネージャーのサイトの設定](#bkmk_configure_site_settings) 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-166">To add a user to the system role "system administrator", see the [Report Manager Site Settings](#bkmk_configure_site_settings) section earlier in this topic.</span></span>  
  
 <span data-ttu-id="dc2cd-167">これで、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を開くときに **[管理者として実行]** を明示的に選択しなくても、レポート サーバーのプロパティにアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-167">Now when you open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and do not explicitly select **Run as administrator** you have access to the report server properties.</span></span>  
  
##  <a name="to-configure-sql-server-data-tools-bi-ssdt-to-publish-to-a-local-report-server"></a><a name="bkmk_configure_ssdt"></a><span data-ttu-id="dc2cd-168">ローカルレポートサーバーにパブリッシュするように SQL Server Data Tools BI (SSDT) を構成するには</span><span class="sxs-lookup"><span data-stu-id="dc2cd-168">To Configure SQL Server Data Tools BI (SSDT) to Publish to a Local Report Server</span></span>  
 <span data-ttu-id="dc2cd-169">[!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] を、このトピックの最初のセクションに記載したオペレーティング システムのいずれかにインストールした状況で、SSDT を使用してローカルのネイティブ モード レポート サーバーを操作する場合は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を高度な権限で開くか、レポート サービス ロールを構成しない限り、権限エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-169">If you installed [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] on one of the operating systems listed in the first section of this topic, and you want SSDT to interact with a local Native mode report server, you will experiences permission errors unless you open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] with elevated permissions or configure reporting services roles.</span></span> <span data-ttu-id="dc2cd-170">たとえば、十分な権限がない場合には次のような問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-170">For example, if you do not have sufficient permissions, you experience issues similar to the following:</span></span>  
  
-   <span data-ttu-id="dc2cd-171">ローカル レポート サーバーにレポート アイテムを配置しようとすると、 **[エラー一覧]** ウィンドウに次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-171">When you attempt to deploy report items to the local report server, you see an error message similar to the following in the **Error List** window:</span></span>  
  
    -   <span data-ttu-id="dc2cd-172">ユーザー 'Domain\\<user name\>' には、この操作を行うのに必要な権限が与えられていません。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-172">The permissions granted to user 'Domain\\<user name\>' are insufficient for performing this operation.</span></span>  
  
 <span data-ttu-id="dc2cd-173">**SSDT を開くときに高度な権限を毎回使用するには:**</span><span class="sxs-lookup"><span data-stu-id="dc2cd-173">**To run with elevated permissions each time you open SSDT:**</span></span>  
  
1.  <span data-ttu-id="dc2cd-174">スタート画面で、「」と入力し、[ `sql server` **Visual Studio の SQL Server Data Tools**] を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-174">From the start screen, type `sql server` and then right-click **SQL Server Data Tools for Visual Studio**.</span></span> <span data-ttu-id="dc2cd-175">**[管理者として実行]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="dc2cd-175">Click **Run as administrator**</span></span>  
  
     <span data-ttu-id="dc2cd-176">**または**、それ以前のオペレーティング システムで次のように操作します。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-176">**Or**, on older operating systems:</span></span>  
  
     <span data-ttu-id="dc2cd-177">**[スタート]** メニューの **[すべてのプログラム]** をクリックし、 **[SQL Server 2014]** をクリックし、 **[SQL Server Data Tools]** を右クリックして **[管理者として実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-177">From the **Start** menu, click **All Programs**, click **SQL Server 2014**, right-click **SQL Server Data Tools**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="dc2cd-178">**[Continue]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-178">Click **Continue**.</span></span>  
  
3.  <span data-ttu-id="dc2cd-179">**[プログラムの実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-179">Click **Run Program**.</span></span>  
  
 <span data-ttu-id="dc2cd-180">これで、レポートやその他のアイテムをローカル レポート サーバーに配置できるようになります。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-180">You should now be able to deploy reports and other items to a local report server.</span></span>  
  
 <span data-ttu-id="dc2cd-181">**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ロール プロパティとロールの割り当てを構成して、高度な権限で SSDT を毎回起動する必要をなくすには、以下の手順を実行します。**</span><span class="sxs-lookup"><span data-stu-id="dc2cd-181">**To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] role assignments so you do not need to start SSDT with elevated permissions each time:**</span></span>  
  
-   <span data-ttu-id="dc2cd-182">このトピックの「 [レポート マネージャーのフォルダーの設定](#bkmk_configure_folder_settings) 」および「 [レポート マネージャーのサイトの設定](#bkmk_configure_site_settings) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-182">See the [Report Manager Folder Settings](#bkmk_configure_folder_settings) and [Report Manager Site Settings](#bkmk_configure_site_settings) sections earlier in this topic.</span></span>  
  
##  <a name="additional-information"></a><a name="bkmk_addiitonal_informaiton"></a><span data-ttu-id="dc2cd-183">追加情報</span><span class="sxs-lookup"><span data-stu-id="dc2cd-183">Additional Information</span></span>  
 <span data-ttu-id="dc2cd-184">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の管理に関連する追加の一般的な手順は、Windows ファイアウォールでポート 80 を開いてレポート サーバー コンピューターへのアクセスを許可することです。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-184">An additional and common configuration step related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] administration is to open port 80 in Windows Firewall to allow access to the report server computer.</span></span> <span data-ttu-id="dc2cd-185">手順については、「 [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc2cd-185">For instructions, see [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc2cd-186">参照</span><span class="sxs-lookup"><span data-stu-id="dc2cd-186">See Also</span></span>  
 [<span data-ttu-id="dc2cd-187">Reporting Services ネイティブ モードのレポート サーバーの管理</span><span class="sxs-lookup"><span data-stu-id="dc2cd-187">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
