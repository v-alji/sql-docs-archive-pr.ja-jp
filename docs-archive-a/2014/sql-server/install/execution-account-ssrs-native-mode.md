---
title: 実行アカウント (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.executionaccount.F1
ms.assetid: 440b5a09-5fd4-4c3a-b510-f3c33cbf1c82
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 10e158eb38b9d1f94257f48339bb63bae2d3b61b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643150"
---
# <a name="execution-account-ssrs-native-mode"></a><span data-ttu-id="3391b-102">実行アカウント (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="3391b-102">Execution Account (SSRS Native Mode)</span></span>
  <span data-ttu-id="3391b-103">このページを使用すると、自動処理に使用するアカウントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3391b-103">Use this page to configure an account to use for unattended processing.</span></span> <span data-ttu-id="3391b-104">このアカウントは、他に使用できる資格情報のソースがないという特殊な状況で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3391b-104">This account is used under special circumstances when other sources of credentials are not available:</span></span>  
  
-   <span data-ttu-id="3391b-105">資格情報を必要としないデータ ソースにレポート サーバーが接続する場合。</span><span class="sxs-lookup"><span data-stu-id="3391b-105">When the report server connects to a data source that does not require credentials.</span></span> <span data-ttu-id="3391b-106">資格情報を必要としないデータ ソースの例には、XML ドキュメントや一部のクライアント側データベース アプリケーションがあります。</span><span class="sxs-lookup"><span data-stu-id="3391b-106">Examples of data sources that might not require credentials include XML documents and some client-side database applications.</span></span>  
  
-   <span data-ttu-id="3391b-107">外部画像ファイルなど、レポートで参照されるリソースを、レポート サーバーが他のサーバーに接続して取得する場合。</span><span class="sxs-lookup"><span data-stu-id="3391b-107">When the report server connects to another server to retrieve external image files or other resources that are referenced in a report.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="3391b-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="3391b-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="3391b-109">このアカウントの設定は省略可能ですが、設定しないと、外部画像の使用や一部のデータ ソースへの接続が制限されます。</span><span class="sxs-lookup"><span data-stu-id="3391b-109">Setting this account is optional, but not setting it limits your use of external images and connections to some data sources.</span></span> <span data-ttu-id="3391b-110">外部画像ファイルを取得するとき、レポート サーバーでは匿名接続を確立できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3391b-110">When retrieving external image files, the report server checks to see if an anonymous connection can be made.</span></span> <span data-ttu-id="3391b-111">接続がパスワード保護されている場合、レポート サーバーでは自動レポート処理アカウントを使用してリモート サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="3391b-111">If the connection is password protected, the report server uses the unattended report processing account to connect to the remote server.</span></span> <span data-ttu-id="3391b-112">レポート サーバーでレポート用のデータを取得する際には、現在のユーザーの資格情報を借用するか、ユーザーに資格情報を入力するように要求するか、保存されている資格情報を使用するか、またはデータ ソース接続で資格情報の種類として **[なし]** が指定されている場合は自動処理アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3391b-112">When retrieving data for a report, the report server either impersonates the current user, prompts the user to provide credentials, uses stored credentials, or uses the unattended processing account if the data source connection specifies **None** as the credential type.</span></span> <span data-ttu-id="3391b-113">他のコンピューターに接続する際、レポート サーバーではそのサービス アカウントの資格情報の委任や借用を許可しないので、他の資格情報を使用できない場合は自動処理アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3391b-113">The report server does not allow its service account credentials to be delegated or impersonated when connecting to other computers, so it must use the unattended processing account if no other credentials are available.</span></span>  
  
 <span data-ttu-id="3391b-114">サービス アカウントの実行に使用するものとは別のアカウントを指定してください。</span><span class="sxs-lookup"><span data-stu-id="3391b-114">The account you specify should be different from the one used to run the service account.</span></span> <span data-ttu-id="3391b-115">指定したアカウントを構成すると、値は暗号化されて RSReportServer.config ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="3391b-115">If you configure this account, it is stored in the RSReportServer.config file as an encrypted value.</span></span> <span data-ttu-id="3391b-116">スケールアウト配置でレポート サーバーを実行している場合は、各レポート サーバーでこのアカウントを同じように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3391b-116">If you are running the report server in a scale-out deployment, you must configure this account the same way on each report server.</span></span>  
  
 <span data-ttu-id="3391b-117">任意の Windows ユーザー アカウントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3391b-117">You can use any Windows user account.</span></span> <span data-ttu-id="3391b-118">最適な結果を得るには、読み取り権限とネットワーク ログオン権限のあるアカウントを選択し、他のコンピューターへの接続がサポートされるようにします。</span><span class="sxs-lookup"><span data-stu-id="3391b-118">For best results, choose an account that has read permissions and network logon permissions to support connections to other computers.</span></span> <span data-ttu-id="3391b-119">アカウントには、レポートで使用する外部画像またはデータ ファイルに対する読み取り権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3391b-119">It must have read permissions on any external image or data file that you want to use in a report.</span></span> <span data-ttu-id="3391b-120">すべてのレポート データ ソースと外部画像がレポート サーバー コンピューターに格納されていない場合は、ローカル アカウントを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="3391b-120">Do not specify a local account unless all report data sources and external images are stored on the report server computer.</span></span> <span data-ttu-id="3391b-121">アカウントは自動レポート処理専用に使用してください。</span><span class="sxs-lookup"><span data-stu-id="3391b-121">Use the account only for unattended report processing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3391b-122">[!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] を使用しているときは、レポートで外部画像を参照していて、その画像ファイルにアクセスする権限が必要な場合のみ、このアカウントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3391b-122">If you are using [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] with Advanced Services, you only need to configure this account if you are referencing external images in a report and permission is required to access the image file.</span></span> <span data-ttu-id="3391b-123">SQL Server Express は、リモート サーバーへのデータ ソース接続をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3391b-123">SQL Server Express does not support a data source connection to a remote server.</span></span> <span data-ttu-id="3391b-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3391b-124">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
 <span data-ttu-id="3391b-125">このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、ナビゲーション ウィンドウで **[実行アカウント]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3391b-125">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and select **Execution Account** in the navigation pane.</span></span> <span data-ttu-id="3391b-126">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3391b-126">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3391b-127">Options</span><span class="sxs-lookup"><span data-stu-id="3391b-127">Options</span></span>  
 <span data-ttu-id="3391b-128">**[実行アカウントの指定]**</span><span class="sxs-lookup"><span data-stu-id="3391b-128">**Specify an execution account**</span></span>  
 <span data-ttu-id="3391b-129">アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="3391b-129">Select to specify an account.</span></span>  
  
 <span data-ttu-id="3391b-130">**アカウント**</span><span class="sxs-lookup"><span data-stu-id="3391b-130">**Account**</span></span>  
 <span data-ttu-id="3391b-131">Windows のドメイン ユーザー アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="3391b-131">Enter a Windows domain user account.</span></span> <span data-ttu-id="3391b-132">\* \<domain> \\<ユーザーアカウント \> \*の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="3391b-132">Use this format: *\<domain>\\<user account\>*.</span></span>  
  
 <span data-ttu-id="3391b-133">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="3391b-133">**Password**</span></span>  
 <span data-ttu-id="3391b-134">パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="3391b-134">Type the password.</span></span>  
  
 <span data-ttu-id="3391b-135">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="3391b-135">**Confirm password**</span></span>  
 <span data-ttu-id="3391b-136">パスワードを再入力します。</span><span class="sxs-lookup"><span data-stu-id="3391b-136">Retype the password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3391b-137">参照</span><span class="sxs-lookup"><span data-stu-id="3391b-137">See Also</span></span>  
 <span data-ttu-id="3391b-138">[Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3391b-138">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="3391b-139">[暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="3391b-139">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 [<span data-ttu-id="3391b-140">自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="3391b-140">Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
  
  
