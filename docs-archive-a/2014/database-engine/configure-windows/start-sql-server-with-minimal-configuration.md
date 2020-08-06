---
title: 最小構成での SQL Server の起動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c78fc10be584803b438b2cd125a77400ff369b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632090"
---
# <a name="start-sql-server-with-minimal-configuration"></a><span data-ttu-id="8e73b-102">最小構成での SQL Server の起動</span><span class="sxs-lookup"><span data-stu-id="8e73b-102">Start SQL Server with Minimal Configuration</span></span>
  <span data-ttu-id="8e73b-103">構成の問題があるためにサーバーを起動できない場合は、最小構成起動オプションを使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動できます。</span><span class="sxs-lookup"><span data-stu-id="8e73b-103">If you have configuration problems that prevent the server from starting, you can start an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the minimal configuration startup option.</span></span> <span data-ttu-id="8e73b-104">これが起動オプション **-f**です。</span><span class="sxs-lookup"><span data-stu-id="8e73b-104">This is the startup option **-f**.</span></span> <span data-ttu-id="8e73b-105">最小構成で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動すると、サーバーが自動的にシングル ユーザー モードに設定されます。</span><span class="sxs-lookup"><span data-stu-id="8e73b-105">Starting an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with minimal configuration automatically puts the server in single-user mode.</span></span>  
  
 <span data-ttu-id="8e73b-106">最小構成モードで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="8e73b-106">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode, note the following:</span></span>  
  
-   <span data-ttu-id="8e73b-107">1 人のユーザーのみが接続でき、CHECKPOINT プロセスは実行されません。</span><span class="sxs-lookup"><span data-stu-id="8e73b-107">Only a single user can connect, and the CHECKPOINT process is not executed.</span></span>  
  
-   <span data-ttu-id="8e73b-108">リモート アクセスと先行読み取りは無効になります。</span><span class="sxs-lookup"><span data-stu-id="8e73b-108">Remote access and read-ahead are disabled.</span></span>  
  
-   <span data-ttu-id="8e73b-109">起動ストアド プロシージャは実行されません。</span><span class="sxs-lookup"><span data-stu-id="8e73b-109">Startup stored procedures do not run.</span></span>  
  
 <span data-ttu-id="8e73b-110">最小構成でサーバーを起動後、適切なサーバー オプションの値を変更し、サーバーを停止してから再起動してください。</span><span class="sxs-lookup"><span data-stu-id="8e73b-110">After the server has been started with minimal configuration, you should change the appropriate server option value or values, stop, and then restart the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8e73b-111">**sqlcmd** ユーティリティと専用管理者接続 (DAC) を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="8e73b-111">Use the **sqlcmd** utility and the dedicated administrator connection (DAC) to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8e73b-112">一般的な接続を使用する場合は、最小構成モードで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する前に SQL Server エージェント サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="8e73b-112">If you use a typical connection, stop the SQL Server Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode.</span></span> <span data-ttu-id="8e73b-113">停止しないと、SQL Server エージェント サービスが接続を使用するため、接続がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="8e73b-113">Otherwise, the SQL Server Agent service uses the connection, thereby blocking it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e73b-114">参照</span><span class="sxs-lookup"><span data-stu-id="8e73b-114">See Also</span></span>  
 <span data-ttu-id="8e73b-115">[SQL Server エージェント サービスの開始、停止、または一時停止](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span><span class="sxs-lookup"><span data-stu-id="8e73b-115">[Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span></span>  
 <span data-ttu-id="8e73b-116">[データベース管理者用の診断接続](diagnostic-connection-for-database-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="8e73b-116">[Diagnostic Connection for Database Administrators](diagnostic-connection-for-database-administrators.md) </span></span>  
 <span data-ttu-id="8e73b-117">[sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="8e73b-117">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="8e73b-118">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8e73b-118">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="8e73b-119">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8e73b-119">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="8e73b-120">データベース エンジン サービスのスタートアップ オプション</span><span class="sxs-lookup"><span data-stu-id="8e73b-120">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
