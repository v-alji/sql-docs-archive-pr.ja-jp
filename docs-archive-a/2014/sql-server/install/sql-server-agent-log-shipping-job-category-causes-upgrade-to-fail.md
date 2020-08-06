---
title: SQL Server エージェントログ配布ジョブカテゴリによってアップグレードが失敗するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2f5947e8fc8d459388fe35d86c75666e25b5d907
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742778"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a><span data-ttu-id="913a2-102">SQL Server エージェントのログ配布ジョブ カテゴリが原因でアップグレードに失敗する</span><span class="sxs-lookup"><span data-stu-id="913a2-102">SQL Server Agent log shipping job category causes upgrade to fail</span></span>
  <span data-ttu-id="913a2-103">"ログ配布" という名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ カテゴリがある場合、アップグレード プロセスは失敗します。</span><span class="sxs-lookup"><span data-stu-id="913a2-103">The upgrade process will fail if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job category named Log Shipping exists.</span></span>  
  
## <a name="component"></a><span data-ttu-id="913a2-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="913a2-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="913a2-105">エージェント</span><span class="sxs-lookup"><span data-stu-id="913a2-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="913a2-106">説明</span><span class="sxs-lookup"><span data-stu-id="913a2-106">Description</span></span>  
 <span data-ttu-id="913a2-107">"ログ配布" という名前のシステム ジョブ カテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="913a2-107">There is a system job category named Log Shipping.</span></span> <span data-ttu-id="913a2-108">アップグレード対象のインストールにユーザーが作成した "ログ配布" という名前のジョブ カテゴリが含まれている場合、アップグレードする前にそのジョブ カテゴリの名前を変更する必要があります。名前を変更しないと、アップグレード プロセスは失敗します。</span><span class="sxs-lookup"><span data-stu-id="913a2-108">If an installation that is being upgraded already contains a user-created job category named Log Shipping, you must rename the job category before you upgrade; otherwise, the upgrade process will fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913a2-109">参照</span><span class="sxs-lookup"><span data-stu-id="913a2-109">See Also</span></span>  
 <span data-ttu-id="913a2-110">[アップグレード後にログ配布が実行されない](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md) </span><span class="sxs-lookup"><span data-stu-id="913a2-110">[Log shipping will not run after upgrading](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md) </span></span>  
 <span data-ttu-id="913a2-111">[アップグレードすると、SQL Server エージェントユーザープロキシアカウントが一時的な UpgradedProxyAccount に変更されます](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span><span class="sxs-lookup"><span data-stu-id="913a2-111">[Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span></span>  
 [<span data-ttu-id="913a2-112">SQL Server エージェントのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="913a2-112">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
