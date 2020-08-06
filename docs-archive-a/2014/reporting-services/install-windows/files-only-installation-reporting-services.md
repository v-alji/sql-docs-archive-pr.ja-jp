---
title: ファイルのみのインストール (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ec5c595dce3e292d37117453ccbbc6d19f8b87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716109"
---
# <a name="files-only-installation-reporting-services"></a><span data-ttu-id="57faa-102">ファイルのみのインストール (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="57faa-102">Files-Only Installation (Reporting Services)</span></span>
  <span data-ttu-id="57faa-103">*ファイルのみのインストール* とは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール形態の 1 つです。このインストールでは、セットアップで、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] プログラム ファイルのフォルダー構造の作成、ディスクへのファイルのコピー、ローカル コンピューターへのレポート サーバー サービスの登録、サービス アカウントの構成、サービス アカウントへのファイル権限の付与、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI プロバイダーの登録を行います。</span><span class="sxs-lookup"><span data-stu-id="57faa-103">*Files-only installation* refers to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation where Setup creates the folder structure for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] program files, copies the files to disk, registers the Report Server service on the local computer, configures the service account, grants files permissions to the service account, and registers the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI provider.</span></span>  
  
 <span data-ttu-id="57faa-104">ファイルのみのインストールに含まれる [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能は、レポート サーバー サービス (レポート サーバー Web サービス、バックグラウンド処理アプリケーション、およびレポート マネージャーをホストします)、レポート ビルダー、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツール、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コマンド ライン ユーティリティ (rsconfig.exe、rskeymgmt.exe、および rs.exe) です。</span><span class="sxs-lookup"><span data-stu-id="57faa-104">A files-only installation includes the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features: Report Server service (which hosts the Report Server Web service, background processing application, and Report Manager), Report Builder, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] command line utilities (rsconfig.exe, rskeymgmt.exe and rs.exe).</span></span> <span data-ttu-id="57faa-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] や [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] などの共有機能は含まれません。これらの機能をインストールする場合は、別のアイテムとして指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57faa-105">It does not apply to shared features such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which must be specified as separate items if you want to install them.</span></span>  
  
 <span data-ttu-id="57faa-106">他のインストール モードとは異なり、ファイルのみのモードでインストールされたレポート サーバーは、セットアップの終了時点ではまだ使用できません。</span><span class="sxs-lookup"><span data-stu-id="57faa-106">In contrast with other installation modes, a report server that is installed in files-only mode is not operational when Setup is finished.</span></span> <span data-ttu-id="57faa-107">[Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) を使用してレポート サーバーをオンラインにするには、追加の構成が必要です。</span><span class="sxs-lookup"><span data-stu-id="57faa-107">Additional configuration will be required to bring the report server online by using the [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="when-to-select-files-only-installation-mode"></a><span data-ttu-id="57faa-108">ファイルのみのインストール モードを選択する場合</span><span class="sxs-lookup"><span data-stu-id="57faa-108">When to Select Files-Only Installation Mode</span></span>  
 <span data-ttu-id="57faa-109">次のような場合、ファイルのみのインストールを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57faa-109">A files-only installation must be performed when:</span></span>  
  
-   <span data-ttu-id="57faa-110">リモートのレポート サーバー データベースにレポート サーバーを接続する場合。</span><span class="sxs-lookup"><span data-stu-id="57faa-110">You want to connect the report server to a remote report server database.</span></span>  
  
-   <span data-ttu-id="57faa-111">レポート サーバーを名前付きインスタンスとしてインストールする場合。</span><span class="sxs-lookup"><span data-stu-id="57faa-111">You want to install the report server as a named instance.</span></span>  
  
-   <span data-ttu-id="57faa-112">カスタムの設定や機能の使用が配置要件に含まれており、サーバー構成のタイミングと方法を完全に制御する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="57faa-112">You have deployment requirements that include using custom settings or functionality, and you want full control over when and how the server is configured.</span></span>  
  
-   <span data-ttu-id="57faa-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を含む [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]フェールオーバー クラスターをインストールする場合。</span><span class="sxs-lookup"><span data-stu-id="57faa-113">Installing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster that includes [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="how-to-perform-a-files-only-installation"></a><span data-ttu-id="57faa-114">ファイルのみのインストールを実行する方法</span><span class="sxs-lookup"><span data-stu-id="57faa-114">How to Perform a Files-Only Installation</span></span>  
 <span data-ttu-id="57faa-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、ファイルのみのインストールが既定値です。</span><span class="sxs-lookup"><span data-stu-id="57faa-115">Files-only installation is the default for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="57faa-116">ファイルのみのインストールを、コマンド ラインまたはインストール ウィザードで指定できます。</span><span class="sxs-lookup"><span data-stu-id="57faa-116">You can specify a files-only installation through the command line or in the Installation wizard.</span></span> <span data-ttu-id="57faa-117">手順については次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="57faa-117">The following topics provide step-by-step instructions:</span></span>  
  
-   <span data-ttu-id="57faa-118">[インストールウィザード &#40;セットアップ&#41;から SQL Server 2014 をインストール](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)します。</span><span class="sxs-lookup"><span data-stu-id="57faa-118">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
-   <span data-ttu-id="57faa-119">[コマンドプロンプトから SQL Server 2014 をインストール](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)します。</span><span class="sxs-lookup"><span data-stu-id="57faa-119">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
#### <a name="example-command-line-script"></a><span data-ttu-id="57faa-120">コマンド ライン スクリプトの例</span><span class="sxs-lookup"><span data-stu-id="57faa-120">Example Command Line Script</span></span>  
 <span data-ttu-id="57faa-121">わかりやすくするため、この例では /RSINSTALLMODE ="FilesOnlyMode" を指定しています。</span><span class="sxs-lookup"><span data-stu-id="57faa-121">For clarity, the example includes /RSINSTALLMODE="FilesOnlyMode".</span></span> <span data-ttu-id="57faa-122">実際には、ファイルのみのモードが既定値であるため、これを省略してもファイルのみのモードでインストールされます。</span><span class="sxs-lookup"><span data-stu-id="57faa-122">However, because files-only mode is the default, you can omit this and still get a files-only mode installation.</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a><span data-ttu-id="57faa-123">インストール ウィザード</span><span class="sxs-lookup"><span data-stu-id="57faa-123">Installation Wizard</span></span>  
 <span data-ttu-id="57faa-124">[機能の選択] ページで [ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ] を選択すると、[ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成] ページでインストール モードを指定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="57faa-124">When you select [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in the Feature Selection page, Setup provides a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page that enables you to specify the installation mode.</span></span> <span data-ttu-id="57faa-125">ファイルのみのインストールを指定するには、 **[構成] ページで** [レポート サーバーを構成せずにインストールする] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57faa-125">To specify a files-only installation, select **Install but do not configure the report server** on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57faa-126">参照</span><span class="sxs-lookup"><span data-stu-id="57faa-126">See Also</span></span>  
 <span data-ttu-id="57faa-127">[Reporting Services のインストール状態の検証](verify-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="57faa-127">[Verify a Reporting Services Installation](verify-a-reporting-services-installation.md) </span></span>  
 <span data-ttu-id="57faa-128">[レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="57faa-128">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="57faa-129">[レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="57faa-129">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="57faa-130">[SSRS Configuration Manager &#40;レポートサーバーデータベース接続の構成&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="57faa-130">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="57faa-131">[Sharepoint モードのインストール Reporting Services sharepoint 2010 および SharePoint 2013&#41;&#40;](install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="57faa-131">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="57faa-132">[Reporting Services ネイティブ モードのレポート サーバーのインストール](install-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="57faa-132">[Install Reporting Services Native Mode Report Server](install-reporting-services-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="57faa-133">Reporting Services ツール</span><span class="sxs-lookup"><span data-stu-id="57faa-133">Reporting Services Tools</span></span>](../tools/reporting-services-tools.md)  
  
  
