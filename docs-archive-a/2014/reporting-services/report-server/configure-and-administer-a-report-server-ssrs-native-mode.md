---
title: レポート サーバーを構成および管理する (SSRS ネイティブ モード) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5164fd2f9170cb092a45394f64f06d7622253f2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642560"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a><span data-ttu-id="9cc89-102">レポート サーバーを構成および管理する (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="9cc89-102">Configure and Administer a Report Server (SSRS Native Mode)</span></span>
  <span data-ttu-id="9cc89-103">このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を構成するための方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-103">This topic summarizes the approaches that you can use to configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9cc89-104">また、特定のコンポーネント、機能、サーバー機能の構成方法について説明しているトピックへのリストも記載されています。</span><span class="sxs-lookup"><span data-stu-id="9cc89-104">It also includes a list of topics that explain how to configure specific components, features, or server capabilities.</span></span> <span data-ttu-id="9cc89-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]は次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="9cc89-105">To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="9cc89-106">Reporting Services 構成マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-106">Use the Reporting Services Configuration Manager.</span></span> <span data-ttu-id="9cc89-107">このセクションの多くのトピックでは、このツールを使用して特定の機能を構成する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="9cc89-107">Many of the topics in this section contain information about how to configure specific features through this tool.</span></span>  
  
-   <span data-ttu-id="9cc89-108">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して、サーバーのプロパティのカスタマイズ、個人用レポートの有効化、トレース ログの有効化、および、サイト全体に対する既定値の設定を行います。</span><span class="sxs-lookup"><span data-stu-id="9cc89-108">Use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to customize server properties, enable My Reports, enable trace logs, and set site-wide defaults.</span></span> <span data-ttu-id="9cc89-109">サイト設定の詳細については、Management Studio の「 [Reporting Services レポート サーバー &#40;ネイティブ モード&#41;](reporting-services-report-server-native-mode.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cc89-109">For more information about site settings, see [Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) for Management Studio.</span></span> <span data-ttu-id="9cc89-110">サーバーのプロパティをプログラムから設定するスクリプトを作成して実行できます。</span><span class="sxs-lookup"><span data-stu-id="9cc89-110">Note that you can create and run script that sets server properties programmatically.</span></span> <span data-ttu-id="9cc89-111">詳細については、「 [配置タスクおよび管理タスクのスクリプト作成](../tools/script-deployment-and-administrative-tasks.md) 」および「 [レポート サーバーのシステム プロパティ](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cc89-111">For more information, see [Script Deployment and Administrative Tasks](../tools/script-deployment-and-administrative-tasks.md) and [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md).</span></span>  
  
-   <span data-ttu-id="9cc89-112">レポート マネージャー使用して、レポート サーバーにアクセスするための権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="9cc89-112">Use Report Manager to grant permissions to access the report server.</span></span> <span data-ttu-id="9cc89-113">権限は、各ユーザーまたはグループ アカウントに対して定義したロールの割り当てを通じて付与されます。</span><span class="sxs-lookup"><span data-stu-id="9cc89-113">Permissions are conveyed through role assignments that you define for each user or group account.</span></span> <span data-ttu-id="9cc89-114">詳細については、「[ロールと権限 (Reporting Services)](../security/roles-and-permissions-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cc89-114">For more information, see [Roles and Permissions &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="9cc89-115">必要に応じて、構成ファイルを修正し、アプリケーションの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-115">Optionally, modify configuration files to change application settings.</span></span> <span data-ttu-id="9cc89-116">各ファイルの詳細およびそれらの修正のガイドラインについては、「 [Reporting Services 構成ファイル](reporting-services-configuration-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cc89-116">For more information about each file and guidelines for modifying them, see [Reporting Services Configuration Files](reporting-services-configuration-files.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9cc89-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9cc89-117">In This Section</span></span>  
 [<span data-ttu-id="9cc89-118">レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="9cc89-118">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 <span data-ttu-id="9cc89-119">レポート サーバーおよびレポート マネージャーへのアクセスに使用する URL の定義方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-119">Describes how to define the URLs used to access the report server and Report Manager.</span></span>  
  
 [<span data-ttu-id="9cc89-120">レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="9cc89-120">Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="9cc89-121">サービスのアカウントとパスワードを変更する方法の推奨事項と手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-121">Provides recommendations and steps on how to modify service account and password.</span></span>  
  
 [<span data-ttu-id="9cc89-122">レポート サーバー データベースの作成 &#40;SSRS構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="9cc89-122">Create a Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 <span data-ttu-id="9cc89-123">サーバーのメタデータやオブジェクトの格納に必要なレポート サーバー データベースを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-123">Describes how to create a report server database, required for storing server metadata and objects.</span></span>  
  
 [<span data-ttu-id="9cc89-124">レポート サーバー データベース接続の構成 &#40;SSRS構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="9cc89-124">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 <span data-ttu-id="9cc89-125">レポート サーバーからレポート サーバー データベースへの接続に使用する接続文字列を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-125">Describes how to modify the connection string used by the report server to connect to the report server database.</span></span>  
  
 [<span data-ttu-id="9cc89-126">SSRS Configuration Manager &#40;電子メール配信用にレポートサーバーを構成&#41;</span><span class="sxs-lookup"><span data-stu-id="9cc89-126">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 <span data-ttu-id="9cc89-127">電子メールによるレポートの配信をサポートするようにレポート サーバーを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-127">Describes how to configure a report server to support e-mail report distribution.</span></span>  
  
 [<span data-ttu-id="9cc89-128">自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="9cc89-128">Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="9cc89-129">自動実行モードでレポートを処理するようにユーザー アカウントを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cc89-129">Describes how to configure a user account to process reports in unattended mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc89-130">参照</span><span class="sxs-lookup"><span data-stu-id="9cc89-130">See Also</span></span>  
 <span data-ttu-id="9cc89-131">[レポートビルダーアクセスの構成](configure-report-builder-access.md) </span><span class="sxs-lookup"><span data-stu-id="9cc89-131">[Configure Report Builder Access](configure-report-builder-access.md) </span></span>  
 <span data-ttu-id="9cc89-132">[Reporting Services 構成ファイル](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="9cc89-132">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="9cc89-133">[Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="9cc89-133">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="9cc89-134">[Reporting Services のセキュリティと保護](../security/reporting-services-security-and-protection.md) </span><span class="sxs-lookup"><span data-stu-id="9cc89-134">[Reporting Services Security and Protection](../security/reporting-services-security-and-protection.md) </span></span>  
 [<span data-ttu-id="9cc89-135">Reporting Services レポート サーバー (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="9cc89-135">Reporting Services Report Server &#40;Native Mode&#41;</span></span>](reporting-services-report-server-native-mode.md)  
  
  
