---
title: Reporting Services を使ったスクリプトの作成と PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7a8dc805351897c11202467ed8bcb0373ef77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641979"
---
# <a name="scripting-and-powershell-with-reporting-services"></a><span data-ttu-id="fd3da-102">Reporting Services を使ったスクリプトの作成と PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd3da-102">Scripting and PowerShell with Reporting Services</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fd3da-103">は、スクリプトによる開発および管理のさまざまなシナリオをサポートしています。スクリプトには、rs.exe コマンド ライン ユーティリティや SharePoint モードのレポート サーバー用の PowerShell コマンドレットを含むもの、またネイティブ モードと SharePoint モードの両方の PowerShell からの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] オブジェクト モデルを利用するものがあります。</span><span class="sxs-lookup"><span data-stu-id="fd3da-103">supports a wide range of development and management scenarios through script, including the rs.exe command line utility, PowerShell cmdlets for SharePoint mode report servers, and leveraging the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] object model from PowerShell for both Native and SharePoint mode.</span></span>

-   <span data-ttu-id="fd3da-104">管理者は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] でスクリプトを作成して、レポート サーバーのインストールを配置および管理する方法を自動化できます。</span><span class="sxs-lookup"><span data-stu-id="fd3da-104">Administrators can write script in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] to automate how they deploy and manage a report server installation.</span></span> <span data-ttu-id="fd3da-105">また、レポート サーバー データベースを作成、構成、および更新する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを生成し、実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd3da-105">Administrators can also generate and run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that create, configure, and update a report server database.</span></span> <span data-ttu-id="fd3da-106">さらに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でスクリプトの記録機能と再生機能を使用して、定期的なメンテナンス タスクを自動化することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd3da-106">Administrators can also use the record and playback script features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to automate routine maintenance tasks.</span></span>

-   <span data-ttu-id="fd3da-107">開発者は、スクリプトを含むカスタム アプリケーションを作成して、</span><span class="sxs-lookup"><span data-stu-id="fd3da-107">Developers can create custom applications that include script.</span></span> <span data-ttu-id="fd3da-108">レポート サーバー Web サービスを呼び出すスクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="fd3da-108">You can run script that makes calls to the Report Server Web service.</span></span> <span data-ttu-id="fd3da-109">マネージド コードで記述できるほとんどすべての操作は、スクリプトで記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd3da-109">Almost any operation that you can write in managed code can also be written in script.</span></span>

-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fd3da-110">は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET スクリプトを、RS.exe ユーティリティ (レポート サーバーで実行されるスクリプト ホスト) によって処理されるスクリプト言語としてサポートしています。</span><span class="sxs-lookup"><span data-stu-id="fd3da-110">supports [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET script as the script language that can be processed by the RS.exe utility, a script host that runs on the report server.</span></span>

## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a><span data-ttu-id="fd3da-111">Reporting Services SharePoint モードの PowerShell コマンドレットとサンプル</span><span class="sxs-lookup"><span data-stu-id="fd3da-111">Reporting Services SharePoint mode PowerShell cmdlets and samples</span></span>
 <span data-ttu-id="fd3da-112">![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")</span><span class="sxs-lookup"><span data-stu-id="fd3da-112">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fd3da-113">SharePoint モードには、レポート サーバー管理用の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] コマンドレットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fd3da-113">SharePoint mode includes [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] cmdlets for report server administration.</span></span>

-   <span data-ttu-id="fd3da-114">[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) には、以下の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fd3da-114">[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Includes the following examples:</span></span>

    -   <span data-ttu-id="fd3da-115">サービス アプリケーションとプロキシの作成</span><span class="sxs-lookup"><span data-stu-id="fd3da-115">Create a service application and proxy</span></span>

    -   <span data-ttu-id="fd3da-116">配信拡張機能の確認と更新</span><span class="sxs-lookup"><span data-stu-id="fd3da-116">Review and update a delivery extension</span></span>

    -   <span data-ttu-id="fd3da-117">Reporting Services アプリケーション データベースのプロパティの取得と設定 (たとえば、データベースのタイムアウト)</span><span class="sxs-lookup"><span data-stu-id="fd3da-117">Get and set Properties of the Reporting Service Application Database, for example database timeout</span></span>

    -   <span data-ttu-id="fd3da-118">データ拡張機能の一覧</span><span class="sxs-lookup"><span data-stu-id="fd3da-118">List Data Extensions</span></span>

## <a name="reporting-services-object-model-and-powershell-samples"></a><span data-ttu-id="fd3da-119">Reporting Services のオブジェクト モデルと Powershell サンプル</span><span class="sxs-lookup"><span data-stu-id="fd3da-119">Reporting Services Object model and Powershell samples</span></span>
 <span data-ttu-id="fd3da-120">![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")</span><span class="sxs-lookup"><span data-stu-id="fd3da-120">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

 <span data-ttu-id="fd3da-121">コア オブジェクト モデルを呼び出す PowerShell。ほとんどの場合、SharePoint モードとネイティブ モードにも有効です。たとえば、移行作業、サブスクリプション作業、SQL15 でのサブスクリプション作業の関連するサンプルなどです。</span><span class="sxs-lookup"><span data-stu-id="fd3da-121">PowerShell calling the core object model and for the most part valid for SharePoint and native mode, for example the migration work, subscription work, and more related samples for subscriptions work in SQL15.</span></span>

-   <span data-ttu-id="fd3da-122">[PowerShell を使用した Reporting Services サブスクリプション所有者の変更および一覧表示とサブスクリプションの実行](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="fd3da-122">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span></span>

-   <span data-ttu-id="fd3da-123">[PowerShell を使用したネイティブ モードのレポート サーバーを含む Azure VM の作成](https://msdn.microsoft.com/library/azure/dn449661.aspx)。</span><span class="sxs-lookup"><span data-stu-id="fd3da-123">[Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/library/azure/dn449661.aspx).</span></span>

-   <span data-ttu-id="fd3da-124">「[Reporting Services WMI プロバイダーへのアクセス](access-the-reporting-services-wmi-provider.md)」の「PowerShell を使用した WMI クラスへのアクセス」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd3da-124">See the section "Access the WMI classes using PowerShell" in [Access the Reporting Services WMI Provider](access-the-reporting-services-wmi-provider.md).</span></span>

-   <span data-ttu-id="fd3da-125">[PowerShell.scriptin を使用して SSRS を管理する方法](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/)</span><span class="sxs-lookup"><span data-stu-id="fd3da-125">[How to Administer SSRS using PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin</span></span>

## <a name="rsexe-scripting-samples"></a><span data-ttu-id="fd3da-126">RS.exe スクリプトのサンプル</span><span class="sxs-lookup"><span data-stu-id="fd3da-126">RS.exe scripting samples</span></span>

-   <span data-ttu-id="fd3da-127">[サンプル Reporting Services rs.exe レポートサーバー間でコンテンツを移行するためのスクリプト](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd3da-127">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>

-   <span data-ttu-id="fd3da-128">その他のスクリプト、アプリケーション、および拡張機能の例については、「 [SQL Server Reporting Services の製品例](https://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd3da-128">For additional script, application, and extension examples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>

## <a name="see-also"></a><span data-ttu-id="fd3da-129">参照</span><span class="sxs-lookup"><span data-stu-id="fd3da-129">See Also</span></span>
 <span data-ttu-id="fd3da-130">[RS.exe ユーティリティ &#40;SSRS&#41;](rs-exe-utility-ssrs.md) [スクリプトの配置と管理タスク](script-deployment-and-administrative-tasks.md)[スクリプトを使用した rs.exe ユーティリティと Web サービス](script-with-the-rs-exe-utility-and-the-web-service.md)</span><span class="sxs-lookup"><span data-stu-id="fd3da-130">[RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md) [Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) [Script with the rs.exe Utility and the Web Service](script-with-the-rs-exe-utility-and-the-web-service.md)</span></span>


