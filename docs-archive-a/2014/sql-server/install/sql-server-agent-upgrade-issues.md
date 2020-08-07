---
title: SQL Server エージェントのアップグレードに関する問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server Agent
- SQL Server Agent, upgrades
ms.assetid: 77e303ff-febd-4103-ae5d-6e5b85bc8009
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ac234a757510af5ebfac261ea6d3e7e57d2f426f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715969"
---
# <a name="sql-server-agent-upgrade-issues"></a><span data-ttu-id="d44e8-102">SQL Server エージェントのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="d44e8-102">SQL Server Agent Upgrade Issues</span></span>
  <span data-ttu-id="d44e8-103">アップグレードに影響する可能性がある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントに関する問題については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d44e8-103">The following topics describe the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent issues that might affect an upgrade.</span></span> <span data-ttu-id="d44e8-104">これらのトピックでは、これらの変更が各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境にもたらす影響を軽減するための措置についても説明します。</span><span class="sxs-lookup"><span data-stu-id="d44e8-104">The topics describe actions that you can take to help reduce the effect of these changes on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d44e8-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d44e8-105">In This Section</span></span>  
  
-   [<span data-ttu-id="d44e8-106">データベース メンテナンス プランが新しくなった</span><span class="sxs-lookup"><span data-stu-id="d44e8-106">Database maintenance plans superseded</span></span>](../../../2014/sql-server/install/database-maintenance-plans-superseded.md)  
  
-   [<span data-ttu-id="d44e8-107">sysadmin ユーザーのみがジョブ ステップのログ ファイルをファイル システムに書き込むことができる</span><span class="sxs-lookup"><span data-stu-id="d44e8-107">Only sysadmin users can write job step log files to the file system</span></span>](../../../2014/sql-server/install/only-sysadmin-users-can-write-job-step-log-files-to-the-file-system.md)  
  
-   [<span data-ttu-id="d44e8-108">xp_sqlagent_proxy_account 拡張ストアド プロシージャの代わりに新しいストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="d44e8-108">Replace usage of the xp_sqlagent_proxy_account extended stored procedure with new stored procedures</span></span>](../../../2014/sql-server/install/replace-xp-sqlagent-proxy-account-extended-sp-with-new-stored-procedures.md)  
  
-   [<span data-ttu-id="d44e8-109">SQL Server エージェントのログ配布ジョブ カテゴリが原因でアップグレードに失敗する</span><span class="sxs-lookup"><span data-stu-id="d44e8-109">SQL Server Agent log shipping job category causes upgrade to fail</span></span>](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)  
  
-   [<span data-ttu-id="d44e8-110">SQL Server エージェント サービスで SQL Server 認証を使用できない</span><span class="sxs-lookup"><span data-stu-id="d44e8-110">SQL Server Agent Service cannot use SQL Server Authentication</span></span>](../../../2014/sql-server/install/sql-server-agent-service-cannot-use-sql-server-authentication.md)  
  
-   [<span data-ttu-id="d44e8-111">SQL Server エージェントのジョブ ステップのトークン構文を更新する</span><span class="sxs-lookup"><span data-stu-id="d44e8-111">Update token syntax in SQL Server Agent job steps</span></span>](../../../2014/sql-server/install/update-token-syntax-in-sql-server-agent-job-steps.md)  
  
-   [<span data-ttu-id="d44e8-112">マスター サーバーをアップグレードする前にすべてのターゲット サーバーをアップグレードする</span><span class="sxs-lookup"><span data-stu-id="d44e8-112">Upgrade all target servers before upgrading the master server</span></span>](../../../2014/sql-server/install/upgrade-all-target-servers-before-upgrading-the-master-server.md)  
  
-   [<span data-ttu-id="d44e8-113">アップグレードすると SQL Server エージェント ユーザーのプロキシ アカウントが一時的な UpgradedProxyAccount に変更される</span><span class="sxs-lookup"><span data-stu-id="d44e8-113">Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount</span></span>](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)  
  
## <a name="see-also"></a><span data-ttu-id="d44e8-114">参照</span><span class="sxs-lookup"><span data-stu-id="d44e8-114">See Also</span></span>  
 <span data-ttu-id="d44e8-115">[SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="d44e8-115">[SQL Server 2014 Upgrade Advisor &#91;new&#93;](sql-server-2014-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="d44e8-116">アップグレードに関する問題の解決</span><span class="sxs-lookup"><span data-stu-id="d44e8-116">Resolving Upgrade Issues</span></span>](../../../2014/sql-server/install/resolving-upgrade-issues.md)  
  
  
