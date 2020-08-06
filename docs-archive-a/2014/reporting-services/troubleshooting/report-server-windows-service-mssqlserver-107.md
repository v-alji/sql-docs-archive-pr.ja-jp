---
title: レポート サーバー Windows サービス (MSSQLServer) 107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- MSSQLServer 107 error
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8651f98b47b698fbe3cfb6a152b9220a84ed7256
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639896"
---
# <a name="report-server-windows-service-mssqlserver-107"></a><span data-ttu-id="90bd5-102">レポート サーバー Windows サービス (MSSQLServer) 107</span><span class="sxs-lookup"><span data-stu-id="90bd5-102">Report Server Windows Service (MSSQLServer) 107</span></span>
    
## <a name="details"></a><span data-ttu-id="90bd5-103">詳細</span><span class="sxs-lookup"><span data-stu-id="90bd5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90bd5-104">製品名</span><span class="sxs-lookup"><span data-stu-id="90bd5-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="90bd5-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90bd5-105">Event ID</span></span>|<span data-ttu-id="90bd5-106">107</span><span class="sxs-lookup"><span data-stu-id="90bd5-106">107</span></span>|  
|<span data-ttu-id="90bd5-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="90bd5-107">Event Source</span></span>|<span data-ttu-id="90bd5-108">レポート サーバー Windows サービス</span><span class="sxs-lookup"><span data-stu-id="90bd5-108">Report Server Windows Service</span></span>|  
|<span data-ttu-id="90bd5-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="90bd5-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="90bd5-110">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="90bd5-110">Message Text</span></span>|<span data-ttu-id="90bd5-111">レポート サーバー Windows サービス (MSSQLSERVER) はレポート サーバー データベースに接続できません。</span><span class="sxs-lookup"><span data-stu-id="90bd5-111">Report Server Windows Service (MSSQLSERVER) cannot connect to the report server database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="90bd5-112">説明</span><span class="sxs-lookup"><span data-stu-id="90bd5-112">Explanation</span></span>  
 <span data-ttu-id="90bd5-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レポート サーバー サービスは、レポート サーバー データベースに接続できません。</span><span class="sxs-lookup"><span data-stu-id="90bd5-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server service cannot connect to the report server database.</span></span> <span data-ttu-id="90bd5-114">このエラーは、サービスの再起動中、レポート サーバー データベースへの接続を確立できない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="90bd5-114">This error occurs during a service restart if a connection to the report server database cannot be established.</span></span> <span data-ttu-id="90bd5-115">このエラーは、次のような状況で発生します。</span><span class="sxs-lookup"><span data-stu-id="90bd5-115">Conditions under which this error occurs include the following:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90bd5-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスが実行されていない場合。</span><span class="sxs-lookup"><span data-stu-id="90bd5-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] service is not running when the Report Server service starts.</span></span>  
  
-   <span data-ttu-id="90bd5-117">リモート接続または TCP/IP プロトコルが無効になっているため、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスへの接続に失敗する場合。</span><span class="sxs-lookup"><span data-stu-id="90bd5-117">The connection to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service fails because remote connections or the TCP/IP protocol is not enabled.</span></span>  
  
-   <span data-ttu-id="90bd5-118">レポート サーバー データベースが正しく構成されていない場合。</span><span class="sxs-lookup"><span data-stu-id="90bd5-118">The report server database is not configured correctly.</span></span>  
  
-   <span data-ttu-id="90bd5-119">サービス アカウントが正しく構成されていないか、レポート サーバー データベースに対する権限がアカウントにない場合。</span><span class="sxs-lookup"><span data-stu-id="90bd5-119">The service account is not configured correctly, or the account no longer has permissions on the report server database.</span></span> <span data-ttu-id="90bd5-120">この状況は、アカウントやレポート サーバー データベースの設定に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用しない場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="90bd5-120">This can occur if you do not use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to set up the account or the report server database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="90bd5-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="90bd5-121">User Action</span></span>  
 <span data-ttu-id="90bd5-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスが実行されていない場合はこのサービスを開始し、TCP/IP プロトコルでのリモート接続が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="90bd5-122">Start the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service if it is not running and check that remote connections are enabled for TCP/IP protocol.</span></span>  
  
 <span data-ttu-id="90bd5-123">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用して、レポート サーバー データベースとサービス アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="90bd5-123">Use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to configure the report server database and service account.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="90bd5-124">内部使用のみ</span><span class="sxs-lookup"><span data-stu-id="90bd5-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90bd5-125">参照</span><span class="sxs-lookup"><span data-stu-id="90bd5-125">See Also</span></span>  
 <span data-ttu-id="90bd5-126">[レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="90bd5-126">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="90bd5-127">[Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="90bd5-127">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 [<span data-ttu-id="90bd5-128">レポート サーバー サービスの開始と停止</span><span class="sxs-lookup"><span data-stu-id="90bd5-128">Start and Stop the Report Server Service</span></span>](../report-server/start-and-stop-the-report-server-service.md)  
  
  
