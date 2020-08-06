---
title: 資格情報の変更ウィザード (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0f2e84ec59f1241a10ce52e597920827f3afbc06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640489"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a><span data-ttu-id="450d4-102">資格情報の変更ウィザード (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="450d4-102">Change Credentials Wizard (SSRS Native Mode)</span></span>
  <span data-ttu-id="450d4-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャー ツールの資格情報の変更ウィザードを使用して、レポート サーバーがレポート サーバー データベースへの接続に使用するアカウントを再構成することができます。</span><span class="sxs-lookup"><span data-stu-id="450d4-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the Change Credentials Wizard to guide you through the steps of reconfiguring the account that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="450d4-104">資格情報を変更すると、構成マネージャーによって、レポート サーバーで使用中のレポート サーバー データベースのデータベース サーバー上のすべての権限とデータベース ログイン情報が更新されます。</span><span class="sxs-lookup"><span data-stu-id="450d4-104">When you change credentials, the Configuration Manager will update all permissions and database login information on the database server for the report server database that is actively used by the report server.</span></span>  
  
 <span data-ttu-id="450d4-105">このウィザードを起動するには、 **構成マネージャーの [データベース] ページにある** [資格情報の変更] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="450d4-105">To start the wizard, click **Change Credentials** on the Database page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="450d4-106">Configuration Manager を開始する方法については [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、「 [Reporting Services Configuration Manager &#40;ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="450d4-106">For instructions on how to start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="450d4-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="450d4-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
## <a name="options"></a><span data-ttu-id="450d4-108">Options</span><span class="sxs-lookup"><span data-stu-id="450d4-108">Options</span></span>  
 <span data-ttu-id="450d4-109">**データベースサーバー**</span><span class="sxs-lookup"><span data-stu-id="450d4-109">**Database Server**</span></span>  
 <span data-ttu-id="450d4-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] レポートサーバーデータベースを実行するインスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="450d4-110">Specifies the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance that runs the report server database.</span></span>  
  
 <span data-ttu-id="450d4-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスに接続するには、サーバーにログオンしてデータベース情報を更新するための権限がある資格情報を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="450d4-111">To connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, you must use credentials that have permission to log on to the server and update database information.</span></span> <span data-ttu-id="450d4-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーでは、現在の Windows 資格情報が使用されますが、ログイン権限またはデータベース権限がない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ログインを指定できます。</span><span class="sxs-lookup"><span data-stu-id="450d4-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager uses your current Windows credentials, but if you do not have a login or database permissions, you can specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span>  
  
 <span data-ttu-id="450d4-113">別の Windows 資格情報を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="450d4-113">You cannot specify different Windows credentials.</span></span> <span data-ttu-id="450d4-114">別の Windows ユーザーとして接続する場合は、ユーザーとしてログインし、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="450d4-114">If you want to connect as a different Windows user, login as that user and then start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="450d4-115">**資格情報**</span><span class="sxs-lookup"><span data-stu-id="450d4-115">**Credentials**</span></span>  
 <span data-ttu-id="450d4-116">レポート サーバーがレポート サーバー データベースへの接続に使用するアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="450d4-116">Specifies the account by which the report server connects to the report server database.</span></span> <span data-ttu-id="450d4-117">指定できる値は、レポート サーバー Web サービスのサービス アカウント、レポート サーバーのホストに使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで定義されている [!INCLUDE[ssDE](../../includes/ssde-md.md)] データベース ログイン、または Windows アカウントです。</span><span class="sxs-lookup"><span data-stu-id="450d4-117">Valid values include the service account of the Report Server Web service, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login defined on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance you are using to host the report server, or a Windows account.</span></span> <span data-ttu-id="450d4-118">Windows アカウントを使用している場合は、レポートサーバーとデータベースが同じコンピューター上に存在する場合はローカルアカウント (\* \<computername> \\<ユーザー名 \> *) を指定し、同じドメイン内の異なるコンピューターに存在する場合はドメインユーザーアカウント (* \<domain> \\<username \> \*) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="450d4-118">If you are using a Windows account, you can specify a local account (*\<computername>\\<username\>*) if the report server and the database are on the same computer, or a domain user account (*\<domain>\\<username\>*) if they are on different computers in the same domain.</span></span>  
  
 <span data-ttu-id="450d4-119">レポート サーバーはデータベース ログインを作成し、指定したアカウントにデータベース権限を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="450d4-119">The report server will create a database login and assign database permissions for the account you specify.</span></span>  
  
 <span data-ttu-id="450d4-120">レポート サーバーでは、アカウントの作成は行われません。</span><span class="sxs-lookup"><span data-stu-id="450d4-120">The report server does not create the account itself.</span></span> <span data-ttu-id="450d4-121">配置構成に対して有効な、既に存在するアカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="450d4-121">The account you specify must already exist and it must be valid for your deployment configuration.</span></span> <span data-ttu-id="450d4-122">特に、データベースがリモート コンピューター上にある環境で、Windows アカウントを使用する場合は、そのコンピューターへのログオン権限のあるアカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="450d4-122">Specifically, if the database is on a remote computer and you want to use a Windows account, you must specify an account that has log on permissions on that computer.</span></span>  
  
 <span data-ttu-id="450d4-123">コンピューターが別のドメインまたは信頼されていないドメイン内に存在する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ログインを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="450d4-123">If the computer is in a different or non-trusted domain, consider using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span> <span data-ttu-id="450d4-124">アカウントの選択の詳細については、「 [SSRS Configuration Manager&#41;&#40;レポートサーバーデータベース接続を構成](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="450d4-124">For more information about choosing an account, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="450d4-125">**要約**</span><span class="sxs-lookup"><span data-stu-id="450d4-125">**Summary**</span></span>  
 <span data-ttu-id="450d4-126">ウィザードを実行する前に、設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="450d4-126">Verify the settings before the wizard runs.</span></span>  
  
 <span data-ttu-id="450d4-127">**[続行して完了する]**</span><span class="sxs-lookup"><span data-stu-id="450d4-127">**Progress and Finish**</span></span>  
 <span data-ttu-id="450d4-128">各タスクの進行状況を監視します。</span><span class="sxs-lookup"><span data-stu-id="450d4-128">Monitor the progress of each task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="450d4-129">参照</span><span class="sxs-lookup"><span data-stu-id="450d4-129">See Also</span></span>  
 <span data-ttu-id="450d4-130">[データベース &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="450d4-130">[Database &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="450d4-131">[データベースの変更ウィザード &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="450d4-131">[Change Database Wizard &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="450d4-132">[SSRS Configuration Manager &#40;ネイティブモードのレポートサーバーデータベースを作成&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span><span class="sxs-lookup"><span data-stu-id="450d4-132">[Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span></span>  
 <span data-ttu-id="450d4-133">[Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="450d4-133">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="450d4-134">レポート サーバー データベース接続の構成 &#40;SSRS構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="450d4-134">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
