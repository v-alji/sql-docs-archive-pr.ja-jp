---
title: データベース (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bb8f1841e980279d6051e3393efdf06df238f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645383"
---
# <a name="database-ssrs-native-mode"></a><span data-ttu-id="e72fe-102">データベース (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="e72fe-102">Database (SSRS Native Mode)</span></span>
  <span data-ttu-id="e72fe-103">[データベース] ページを使用すると、1 つまたは複数のレポート サーバー インスタンスに対して内部記憶域を提供するレポート サーバー データベースの作成や構成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e72fe-103">Use the Database page to create and configure the report server databases that provide internal storage for one or more report server instances.</span></span> <span data-ttu-id="e72fe-104">リモートのレポート サーバー データベースが使用されるようにレポート サーバーを構成する場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してデータベースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e72fe-104">If you are configuring a report server to use a remote report server database, you must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to create the database.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="e72fe-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="e72fe-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="e72fe-106">レポート サーバー データベースの作成と接続の構成は複数の手順から成る作業です。</span><span class="sxs-lookup"><span data-stu-id="e72fe-106">Creating a report server database and configuring the connection is a multi-step process.</span></span> <span data-ttu-id="e72fe-107">このページには、タスクごとに各手順を示すウィザードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e72fe-107">To guide you through the steps, this page provides Wizards for each type of task.</span></span> <span data-ttu-id="e72fe-108">権限およびログインの作成または更新も行えます。</span><span class="sxs-lookup"><span data-stu-id="e72fe-108">Permissions and logins are created or updated for you.</span></span> <span data-ttu-id="e72fe-109">[進行状況] ページでは、各手順の状態を監視できます。</span><span class="sxs-lookup"><span data-stu-id="e72fe-109">You can monitor the status of each step in the Progress page.</span></span> <span data-ttu-id="e72fe-110">エラーが発生した場合は、そのエラーをクリックすることで、エラーの解決方法に関する情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e72fe-110">If an error occurs, you can click the error for information on how to resolve it.</span></span>  
  
 <span data-ttu-id="e72fe-111">レポート サーバー データベースでは、特定のサーバー モードをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e72fe-111">A report server database must support a specific server mode.</span></span> <span data-ttu-id="e72fe-112">既定のモードはネイティブ モードですが、SharePoint の製品またはテクノロジの大規模な配置でレポート サーバーを実行している場合は、SharePoint 統合モード用のレポート サーバー データベースを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e72fe-112">The default mode is native mode, but you can also create a report server database for SharePoint integrated mode if you are running a report server in a larger deployment of a SharePoint product or technology.</span></span> <span data-ttu-id="e72fe-113">詳細については、「[ネイティブ モードのレポート サーバー データベースの作成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e72fe-113">For more information, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
 <span data-ttu-id="e72fe-114">このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、ナビゲーション ウィンドウで **[データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e72fe-114">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and click **Database** in the navigation pane.</span></span> <span data-ttu-id="e72fe-115">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e72fe-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e72fe-116">Options</span><span class="sxs-lookup"><span data-stu-id="e72fe-116">Options</span></span>  
 <span data-ttu-id="e72fe-117">**SQL Server 名**</span><span class="sxs-lookup"><span data-stu-id="e72fe-117">**SQL Server Name**</span></span>  
 <span data-ttu-id="e72fe-118">[現在のレポート サーバー データベース] の **[SQL Server 名]** では、レポート サーバー データベースを実行する [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-118">In Current Report Server Database, **SQL Server Name** specifies the name of the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] that runs the report server database.</span></span> <span data-ttu-id="e72fe-119">ローカルまたはリモートのコンピューターの、既定または名前付きのインスタンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e72fe-119">You can use a default or named instance on a local or remote computer.</span></span>  
  
 <span data-ttu-id="e72fe-120">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="e72fe-120">**Database Name**</span></span>  
 <span data-ttu-id="e72fe-121">サーバー データを格納するレポート サーバー データベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-121">Specifies the name of the report server database that stores server data.</span></span>  
  
 <span data-ttu-id="e72fe-122">**[レポート サーバー モード]**</span><span class="sxs-lookup"><span data-stu-id="e72fe-122">**Report Server Mode**</span></span>  
 <span data-ttu-id="e72fe-123">レポート サーバー データベースでネイティブ モードと SharePoint 統合モードのどちらをサポートするかを示します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-123">Indicates whether the report server database supports native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="e72fe-124">詳細については、「[レポートサーバーの Reporting Services](../../../2014/reporting-services/reporting-services-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e72fe-124">For more information, see [Reporting Services Report Server](../../../2014/reporting-services/reporting-services-report-server.md).</span></span>  
  
 <span data-ttu-id="e72fe-125">**データベースの変更**</span><span class="sxs-lookup"><span data-stu-id="e72fe-125">**Change Database**</span></span>  
 <span data-ttu-id="e72fe-126">レポート サーバー データベースの作成または選択に必要なすべての手順を示すウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-126">Start a wizard that guides you through all of the steps required for creating or selecting a report server database.</span></span>  
  
 <span data-ttu-id="e72fe-127">**資格情報の種類**</span><span class="sxs-lookup"><span data-stu-id="e72fe-127">**Credential Type**</span></span>  
 <span data-ttu-id="e72fe-128">レポート サーバーがレポート サーバー データベースへの接続に使用する資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-128">Specifies credentials that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="e72fe-129">指定できる資格情報の種類には、サービス アカウント、Windows ドメイン ユーザー、Windows ローカル ユーザー、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ログインがあります。</span><span class="sxs-lookup"><span data-stu-id="e72fe-129">Credential types you can specify include the service account, a Windows domain user, Windows local user, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span> <span data-ttu-id="e72fe-130">資格情報の選択の詳細については、「 [SSRS Configuration Manager&#41;&#40;レポートサーバーデータベース接続の構成](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e72fe-130">For more information about selecting credentials, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="e72fe-131">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="e72fe-131">**User Name**</span></span>  
 <span data-ttu-id="e72fe-132">Windows 資格情報を使用している場合はドメイン ユーザー アカウントを指定し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資格情報を使用している場合は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-132">Specifies a domain user account if you are using Windows credentials, or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login if you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credentials.</span></span> <span data-ttu-id="e72fe-133">Windows 資格情報を使用している場合は、 \* \<domain> \\<アカウント \> \*の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-133">If you are using Windows credentials, specify them in this format: *\<domain>\\<account\>*.</span></span>  
  
 <span data-ttu-id="e72fe-134">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="e72fe-134">**Password**</span></span>  
 <span data-ttu-id="e72fe-135">アカウントのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-135">Specifies the password for the account.</span></span>  
  
 <span data-ttu-id="e72fe-136">**資格情報の変更**</span><span class="sxs-lookup"><span data-stu-id="e72fe-136">**Change Credentials**</span></span>  
 <span data-ttu-id="e72fe-137">別のアカウントを選択したり、レポート サーバー データベースへの接続に使用するアカウントのパスワードを更新するのに必要なすべての手順を示すウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="e72fe-137">Start a wizard that guides you through all of the steps required for selecting a different account or updating the password on the account that is used to connect to the report server database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e72fe-138">参照</span><span class="sxs-lookup"><span data-stu-id="e72fe-138">See Also</span></span>  
 <span data-ttu-id="e72fe-139">[SSRS Configuration Manager &#40;ネイティブモードのレポートサーバーデータベースを作成&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span><span class="sxs-lookup"><span data-stu-id="e72fe-139">[Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span></span>  
 <span data-ttu-id="e72fe-140">[Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e72fe-140">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="e72fe-141">[レポートサーバーデータベース &#40;SSRS ネイティブモード&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e72fe-141">[Report Server Database &#40;SSRS Native Mode&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="e72fe-142">レポート サーバー データベース接続の構成 &#40;SSRS構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="e72fe-142">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
