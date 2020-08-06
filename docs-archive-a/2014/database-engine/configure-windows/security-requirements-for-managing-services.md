---
title: サービスの管理に関するセキュリティ要件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46a777858c01bf3057093d34b29b9a2093668e97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738749"
---
# <a name="security-requirements-for-managing-services"></a><span data-ttu-id="da375-102">サービスの管理に関するセキュリティ要件</span><span class="sxs-lookup"><span data-stu-id="da375-102">Security Requirements for Managing Services</span></span>
  <span data-ttu-id="da375-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを管理するには、SQL Server 構成マネージャーまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="da375-103">To manage the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Services, use either SQL Server Configuration Manager or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="da375-104">クラスター化されたサーバー上のサービスを管理するには、クラスター アドミニストレーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="da375-104">Manage the services on clustered servers with the Cluster Administrator.</span></span>  
  
 <span data-ttu-id="da375-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを管理し、サーバー構成オプションを設定するには、 **serveradmin** 固定サーバー ロールまたは **sysadmin** 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="da375-105">To manage the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service and set the server configuration options, you must be a member of the **serveradmin** fixed server role or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="da375-106">Windows の **Administrators** グループのメンバーは、サービスを開始および停止したり、Windows で提供されているサーバー オプションを構成したりできます。</span><span class="sxs-lookup"><span data-stu-id="da375-106">Members of the Windows **Administrators** group can start and stop services and configure the server options that Windows provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da375-107">適切に操作するには、サービスに使用するアカウントに、正しいドメイン、ファイル システム、およびレジストリ権限を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da375-107">To operate properly, the accounts used for the services must be configured with the correct domain, file system, and registry permissions.</span></span> <span data-ttu-id="da375-108">必要なアクセス許可については、「 [Windows サービス アカウントと権限の構成](configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da375-108">For information about the required permissions, see [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md).</span></span>  
  
## <a name="windows-management-instrumentation"></a><span data-ttu-id="da375-109">Windows Management Instrumentation (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="da375-109">Windows Management Instrumentation</span></span>  
 <span data-ttu-id="da375-110">SQL Server 構成マネージャーと [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、一部のサーバー プロパティの表示および変更に Windows Management Instrumentation (WMI) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="da375-110">SQL Server Configuration Manager and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] use Windows Management Instrumentation (WMI) to display and modify some of the server properties.</span></span> <span data-ttu-id="da375-111">サービスを管理し、サービスの状態を取得するには、ユーザーは WMI オブジェクトにアクセスする権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="da375-111">To manage services and obtain the status of the services, the user must have rights to access the WMI object.</span></span> <span data-ttu-id="da375-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、次のサーバー プロパティ ページで WMI が使用されています。</span><span class="sxs-lookup"><span data-stu-id="da375-112">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the following server property pages use WMI:</span></span>  
  
-   <span data-ttu-id="da375-113">サービスの自動開始</span><span class="sxs-lookup"><span data-stu-id="da375-113">Autostart Services</span></span>  
  
-   <span data-ttu-id="da375-114">起動時のパラメーター</span><span class="sxs-lookup"><span data-stu-id="da375-114">Startup Parameters</span></span>  
  
-   <span data-ttu-id="da375-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="da375-115">Security</span></span>  
  
-   <span data-ttu-id="da375-116">その他のサーバーの設定</span><span class="sxs-lookup"><span data-stu-id="da375-116">Misc Server Settings</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="da375-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="da375-117">Related Tasks</span></span>  
 [<span data-ttu-id="da375-118">SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成</span><span class="sxs-lookup"><span data-stu-id="da375-118">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a><span data-ttu-id="da375-119">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="da375-119">Related Content</span></span>  
 [<span data-ttu-id="da375-120">構成管理用の WMI プロバイダーの概念</span><span class="sxs-lookup"><span data-stu-id="da375-120">WMI Provider for Configuration Management Concepts</span></span>](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
