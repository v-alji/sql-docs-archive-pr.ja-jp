---
title: アップグレード後にログ配布が実行されない |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b2af60743cb2cbf9bf455397fe052c4e81f5a06d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645365"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a><span data-ttu-id="ef76c-102">アップグレード後にログ配布が実行されない</span><span class="sxs-lookup"><span data-stu-id="ef76c-102">Log shipping will not run after upgrading</span></span>
  <span data-ttu-id="ef76c-103">アップグレード アドバイザーによって、ログ配布を使用していることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="ef76c-103">Upgrade Advisor has detected that you are using log shipping.</span></span> [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] <span data-ttu-id="ef76c-104">のログ配布は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のログ配布と互換性がなく、直接アップグレードできません。</span><span class="sxs-lookup"><span data-stu-id="ef76c-104">log shipping is incompatible with log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and cannot be upgraded directly.</span></span> <span data-ttu-id="ef76c-105">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードした後、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはストアド プロシージャを使用してログ配布を再構成します。</span><span class="sxs-lookup"><span data-stu-id="ef76c-105">After upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], reconfigure log shipping using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef76c-106">参照</span><span class="sxs-lookup"><span data-stu-id="ef76c-106">See Also</span></span>  
 <span data-ttu-id="ef76c-107">[SQL Server エージェントログ配布ジョブカテゴリによってアップグレードが失敗する](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span><span class="sxs-lookup"><span data-stu-id="ef76c-107">[SQL Server Agent log shipping job category causes upgrade to fail](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span></span>  
 <span data-ttu-id="ef76c-108">[アップグレードすると、SQL Server エージェントユーザープロキシアカウントが一時的な UpgradedProxyAccount に変更されます](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span><span class="sxs-lookup"><span data-stu-id="ef76c-108">[Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span></span>  
 <span data-ttu-id="ef76c-109">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ef76c-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ef76c-110">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="ef76c-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
