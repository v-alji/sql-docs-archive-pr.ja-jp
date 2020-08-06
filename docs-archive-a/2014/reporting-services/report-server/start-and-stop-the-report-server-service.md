---
title: レポート サーバー サービスの開始と停止 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b751fd1a31830ffdc96cb296fa39d08e396c8c50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640591"
---
# <a name="start-and-stop-the-report-server-service"></a><span data-ttu-id="cabad-102">Start and Stop the Report Server Service</span><span class="sxs-lookup"><span data-stu-id="cabad-102">Start and Stop the Report Server Service</span></span>
  <span data-ttu-id="cabad-103">レポート サーバーは、レポート サーバー Web サービス、レポート マネージャー、およびバックグラウンド処理アプリケーションを含んだ Windows サービスとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="cabad-103">A report server is implemented as a Windows service that contains the Report Server Web service, Report Manager, and a background processing application.</span></span> <span data-ttu-id="cabad-104">レポート サーバーのなんらかの機能を使用するには、このサービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cabad-104">The service must be running if you want to use any report server functionality.</span></span> <span data-ttu-id="cabad-105">このサービスを停止すると、すべてのレポート サーバー処理が停止されます。</span><span class="sxs-lookup"><span data-stu-id="cabad-105">Stopping the service stops all report server operations.</span></span>  
  
 <span data-ttu-id="cabad-106">このサービスが停止している間は、スケジュール設定されたレポートやサブスクリプション処理 (つまり、サービスが実行されていれば、本来発生するはずの処理) に対する要求はキューに追加されます。</span><span class="sxs-lookup"><span data-stu-id="cabad-106">While the service is stopped, requests for scheduled report and subscription processing that would have occurred had the service been running are added to the queue.</span></span> <span data-ttu-id="cabad-107">これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するジョブによって、イベントが作成されるためです。</span><span class="sxs-lookup"><span data-stu-id="cabad-107">This is because jobs that are run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent create the events.</span></span> <span data-ttu-id="cabad-108">サービスの停止中に処理のバックログが蓄積されないようにする場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントも停止してください。</span><span class="sxs-lookup"><span data-stu-id="cabad-108">If you want to avoid a backlog of operations while the service is off, consider stopping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent as well.</span></span>  
  
 <span data-ttu-id="cabad-109">レポート サーバー サービスの開始および停止には、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツール、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows で提供されるサービス ツールなどさまざまなツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cabad-109">You can use a variety of tools to start or stop the Report Server service, including the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, and the Services tool provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span></span>  
  
 <span data-ttu-id="cabad-110">サービス アカウントの変更など、サービスの開始および停止以外の操作を行うには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cabad-110">If you are doing more than starting or stopping the service, such as changing the service account, you must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="cabad-111">他のツールでサービス アカウントを変更すると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストールが壊れる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cabad-111">Using other tools to change the service account can break your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span> <span data-ttu-id="cabad-112">詳細については、 [レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cabad-112">For more information, see [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="cabad-113">サービスを一時停止および再開することはできません。</span><span class="sxs-lookup"><span data-stu-id="cabad-113">You cannot pause and resume the service.</span></span> <span data-ttu-id="cabad-114">また、開始パラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="cabad-114">There are no start parameters.</span></span> <span data-ttu-id="cabad-115">明示的な依存関係はありませんが、レポート サーバー上のサブスクリプションまたはスケジュールされた操作をサポートする場合は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントも実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="cabad-115">Although there are no explicit dependencies, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running if you support any subscriptions or scheduled report operations on the report server.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-the-reporting-services-configuration-tool"></a><span data-ttu-id="cabad-116">Reporting Services 構成ツールを使用してサービスを開始または停止するには</span><span class="sxs-lookup"><span data-stu-id="cabad-116">To start or stop the service using the Reporting Services Configuration tool</span></span>  
  
1.  <span data-ttu-id="cabad-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動して、レポート サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="cabad-117">Start [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server.</span></span>  
  
2.  <span data-ttu-id="cabad-118">[レポート サーバーの状態] ページで、 **[停止]** または **[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cabad-118">On the Report Server Status page, click **Stop** or **Start**.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-services-in-administrative-tools"></a><span data-ttu-id="cabad-119">管理ツールの [サービス] を使用してサービスを開始または停止するには</span><span class="sxs-lookup"><span data-stu-id="cabad-119">To start or stop the service using Services in Administrative Tools</span></span>  
  
-   <span data-ttu-id="cabad-120">[管理ツール] の [サービス] を開きます。次に、 **[SQL Server Reporting Services (MSSQLSERVER)]** を右クリックし、 **[停止]** または **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cabad-120">In Administrative Tools, open Services, right-click **SQL Server Reporting Services (MSSQLSERVER)**, and click **Stop** or **Restart**.</span></span>  
  
 <span data-ttu-id="cabad-121">複数のインスタンスを実行しているか、レポート サーバーが名前付きインスタンスとして実行されている場合は、かっこ内のインスタンス名が、停止または再起動するレポート サーバー インスタンスに対応していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cabad-121">If you are running multiple instance or if the report server is running as a named instance, verify that the instance name in parentheses corresponds to the report server instance you want to stop or restart.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-sql-server-configuration-manager"></a><span data-ttu-id="cabad-122">SQL Server 構成マネージャーを使用してサービスを開始または停止するには</span><span class="sxs-lookup"><span data-stu-id="cabad-122">To start or stop the service using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="cabad-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="cabad-123">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
2.  <span data-ttu-id="cabad-124">[SQL Server のサービス] を選択し、 **[SQL Server Reporting Services]** を右クリックして、 **[停止]** または **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cabad-124">Select SQL Server Services, right-click **SQL Server Reporting Services**, and click **Stop** or **Restart**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cabad-125">参照</span><span class="sxs-lookup"><span data-stu-id="cabad-125">See Also</span></span>  
 [<span data-ttu-id="cabad-126">Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="cabad-126">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
