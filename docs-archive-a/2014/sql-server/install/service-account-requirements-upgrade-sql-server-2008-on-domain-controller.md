---
title: ドメインコントローラー上の SQL Server 2008 にアップグレードするためのサービスアカウントの要件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0680e09548e38760f6ac317fec63152486a4e5fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640415"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a><span data-ttu-id="c0fd5-102">ドメイン コントローラーで SQL Server 2008 へのアップグレードを実行するためのサービス アカウント要件</span><span class="sxs-lookup"><span data-stu-id="c0fd5-102">Service account requirements for upgrading to SQL Server 2008 on a domain controller</span></span>
  <span data-ttu-id="c0fd5-103">アップグレードアドバイザーによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドメインコントローラー上のネットワークサービスまたはローカルサービスアカウントで実行されているのインスタンスが検出されました [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c0fd5-103">Upgrade Advisor detected an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running under a Network Service or Local Service account on a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] domain controller.</span></span> <span data-ttu-id="c0fd5-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドメイン コントローラーに [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] がインストールされている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを Local Service アカウントまたは Network Service アカウントの特権を使用して実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="c0fd5-104">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] domain controller, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services cannot run under Local Service account or Network Service account privileges.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c0fd5-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c0fd5-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="c0fd5-106">修正措置</span><span class="sxs-lookup"><span data-stu-id="c0fd5-106">Corrective Action</span></span>  
 <span data-ttu-id="c0fd5-107">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントが Domain アカウントまたは Local System アカウントに割り当てられていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c0fd5-107">Make sure that all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts are assigned to either Domain accounts or Local System accounts.</span></span> <span data-ttu-id="c0fd5-108">このように変更してからアップグレードしないと、セットアップがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="c0fd5-108">Failure to make this change before upgrading will block Setup.</span></span> <span data-ttu-id="c0fd5-109">サービス アカウントの SQL ライター、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、および Active Directory Helper サービスは、Network Service アカウントにハードコードされていて変更できないため例外となります。</span><span class="sxs-lookup"><span data-stu-id="c0fd5-109">The service accounts SQL Writer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Active Directory Helper services are exceptions because they are hard-coded to the Network Service account and cannot be changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fd5-110">参照</span><span class="sxs-lookup"><span data-stu-id="c0fd5-110">See Also</span></span>  
 <span data-ttu-id="c0fd5-111">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c0fd5-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c0fd5-112">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="c0fd5-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
