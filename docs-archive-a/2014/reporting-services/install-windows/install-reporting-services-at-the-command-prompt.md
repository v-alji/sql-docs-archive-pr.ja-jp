---
title: Reporting Services SharePoint モードとネイティブモードのコマンドプロンプトのインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b2101c40c5136e89d4e30d9551187a2b63672da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711745"
---
# <a name="command-prompt-installation-of-reporting-services-sharepoint-mode-and-native-mode"></a><span data-ttu-id="0ddce-102">Reporting Services のコマンド プロンプト インストール (SharePoint モードとネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="0ddce-102">Command Prompt Installation of Reporting Services SharePoint Mode and Native Mode</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="0ddce-103">は、SQL Server セットアップ プログラムからのコマンド ライン インストールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0ddce-103">supports a command-line installation from the SQL Server setup program.</span></span> <span data-ttu-id="0ddce-104">このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]用のコマンド ラインからのインストール例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="0ddce-104">This topic contains several examples of command-line installations that are specific to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="0ddce-105">すべての SQL Server コンポーネントで使用できるコマンドラインオプションの詳細については、「 [Install SQL Server 2014 from The Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ddce-105">For a complete description of the command-line options available for all SQL Server components, see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span> <span data-ttu-id="0ddce-106">このトピックでは、SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインのコマンド ライン オプションについては説明していません。</span><span class="sxs-lookup"><span data-stu-id="0ddce-106">This topic does not describe command-line options for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span> <span data-ttu-id="0ddce-107">アドインのコマンド インストールについては、「 [rsSharePoint.msi インストール ファイルを使用したアドインのインストール](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0ddce-107">For information on command installation of the add-in, see [Install the add-in using the installation file rsSharePoint.msi](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint).</span></span>  
  
 <span data-ttu-id="0ddce-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード |[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード</span><span class="sxs-lookup"><span data-stu-id="0ddce-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>  
  
## <a name="rsinstallmode-native-mode"></a><span data-ttu-id="0ddce-109">RSINSTALLMODE (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="0ddce-109">RSINSTALLMODE (Native Mode)</span></span>  
 <span data-ttu-id="0ddce-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールするための主な入力設定は、 **/RSINSTALLMODE** の入力設定です。</span><span class="sxs-lookup"><span data-stu-id="0ddce-110">The primary input setting for installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is the **/RSINSTALLMODE** input setting.</span></span> <span data-ttu-id="0ddce-111">この設定には、 **DefaultNativeMode** および **FilesOnlyMode**という 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="0ddce-111">The setting has two options: **DefaultNativeMode** and **FilesOnlyMode**</span></span>  
  
 <span data-ttu-id="0ddce-112">インストールに SQL Server データベース エンジンが含まれている場合、既定の RSINSTALLMODE は DefaultNativeMode です。インストールに SQL Server データベース エンジンが含まれていない場合、既定の RSINSTALLMODE は FilesOnlyMode です。インストールに SQL Server データベース エンジンが含まれていない場合に DefaultNativeMode を選択すると、そのインストールでは自動的に RSINSTALLMODE が FilesOnlyMode に変更されます。</span><span class="sxs-lookup"><span data-stu-id="0ddce-112">If the installation includes the SQL Server Database engine, the default RSINSTALLMODE is DefaultNativeMode.If the installation does not include the SQL Server Database engine, the default RSINSTALLMODE is FilesOnlyMode.If you choose DefaultNativeMode but the installation does not include the SQL Server Database engine, the installation automatically changes the RSINSTALLMODE to FilesOnlyMode.</span></span> <span data-ttu-id="0ddce-113">入力設定の詳細については、「 [Install SQL Server 2014 from The Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ddce-113">For more information on the input settings, see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="rsshpinstallmode-sharepoint-mode"></a><span data-ttu-id="0ddce-114">RSSHPINSTALLMODE (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="0ddce-114">RSSHPINSTALLMODE (SharePoint Mode)</span></span>  
 <span data-ttu-id="0ddce-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を SharePoint モードでインストールするための入力設定は、 **/RSSHPINSTALLMODE**です。</span><span class="sxs-lookup"><span data-stu-id="0ddce-115">The input setting to install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode is **/RSSHPINSTALLMODE**.</span></span> <span data-ttu-id="0ddce-116">入力設定には 1 つのオプション SharePointFilesOnlyMode があります。</span><span class="sxs-lookup"><span data-stu-id="0ddce-116">The input setting has one option: SharePointFilesOnlyMode.</span></span> <span data-ttu-id="0ddce-117">このオプションにより、SharePoint モードに必要なすべてのファイルがインストールされますが、インストール後に構成が必要です。</span><span class="sxs-lookup"><span data-stu-id="0ddce-117">The option installs all the files needed for SharePoint mode but, configuration is required following installation.</span></span> <span data-ttu-id="0ddce-118">追加の構成の手順は、SharePoint サーバーの全体管理を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="0ddce-118">The additional configuration steps are completed using SharePoint Central Administration.</span></span> <span data-ttu-id="0ddce-119">詳細については、「 [sharepoint 2010 用 Reporting Services Sharepoint モードのインストール](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ddce-119">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>  
  
## <a name="examples-of-sharepoint-mode-installation"></a><span data-ttu-id="0ddce-120">SharePoint モード インストールの例</span><span class="sxs-lookup"><span data-stu-id="0ddce-120">Examples of SharePoint Mode Installation</span></span>  
 <span data-ttu-id="0ddce-121">次の例は、SQL Server のデータベース エンジン サービス、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、および SharePoint 用の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドイン (RS_SHPWFE) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="0ddce-121">The following example installs SQL Server the database engine service and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode as well as the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint (RS_SHPWFE).</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 <span data-ttu-id="0ddce-122">次の例は、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のみをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0ddce-122">The following example installs only [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="*****" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
 <span data-ttu-id="0ddce-123">次の例は、すべての SQL Server 機能 (ネイティブ モードと SharePoint モードの両方の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を含む) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="0ddce-123">The following example installs all of the SQL Server features, including both [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode and SharePoint mode.</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT, RS_SHP,RS_SHPWFE,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSSHPINSTALLMODE="SharePointFilesOnlyMode" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="examples-of-sharepoint-mode-upgrade"></a><span data-ttu-id="0ddce-124">SharePoint モード アップグレードの例</span><span class="sxs-lookup"><span data-stu-id="0ddce-124">Examples of SharePoint Mode Upgrade</span></span>  
 <span data-ttu-id="0ddce-125">次の例は、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="0ddce-125">The following example upgrades [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="0ddce-126">**RSUPGRADEPASSWORD** は、既存のレポート サーバー サービス アカウントのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="0ddce-126">**RSUPGRADEPASSWORD** is the password of the existing Report Server service account.</span></span> <span data-ttu-id="0ddce-127">RSUPGRADEPASSWORD は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アカウントがビルトイン アカウントである場合を除いて、アップグレード シナリオの必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="0ddce-127">RSUPGRADEPASSWORD is a required field in an upgrade scenario unless the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account is a built-in account.</span></span>  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[ACCOUNTPASSSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="******"  
```  
  
 <span data-ttu-id="0ddce-128">次の例を使用すると、SharePoint 共有サービス アーキテクチャに基づく SharePoint モードのインストールをアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="0ddce-128">The following example can be used to upgrade a SharePoint Mode installation that is based on the SharePoint shared service architecture.</span></span> <span data-ttu-id="0ddce-129">この例は ALLOWUPGRADEFORSSRSSHAREPOINTMODE スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="0ddce-129">The example uses switch ALLOWUPGRADEFORSSRSSHAREPOINTMODE.</span></span> <span data-ttu-id="0ddce-130">共有サービス アーキテクチャに基づいていない古いバージョンのアップグレードの場合、スイッチは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="0ddce-130">The switch is not needed for upgrading older versions that are not based on the shared service architecture:</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="****" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```  
  
## <a name="examples-of-native-mode-installation"></a><span data-ttu-id="0ddce-131">ネイティブ モード インストールの例</span><span class="sxs-lookup"><span data-stu-id="0ddce-131">Examples of Native Mode Installation</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ddce-132">参照</span><span class="sxs-lookup"><span data-stu-id="0ddce-132">See Also</span></span>  
 <span data-ttu-id="0ddce-133">[コマンドプロンプトから SQL Server 2014 をインストールする](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="0ddce-133">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="0ddce-134">[SysPrep パラメーター](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep) </span><span class="sxs-lookup"><span data-stu-id="0ddce-134">[SysPrep Parameters](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep) </span></span>  
 [<span data-ttu-id="0ddce-135">コマンド プロンプトからの PowerPivot のインストール</span><span class="sxs-lookup"><span data-stu-id="0ddce-135">Install PowerPivot from the Command Prompt</span></span>](../../sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
  
