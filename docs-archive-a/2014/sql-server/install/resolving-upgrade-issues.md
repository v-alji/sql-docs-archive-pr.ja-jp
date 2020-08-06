---
title: アップグレードに関する問題の解決 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c00b08d40bc8c17013e6af19b5d11b0b7ad78c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645352"
---
# <a name="resolving-upgrade-issues"></a><span data-ttu-id="9ed7a-102">アップグレードに関する問題とその対処方法</span><span class="sxs-lookup"><span data-stu-id="9ed7a-102">Resolving Upgrade Issues</span></span>
  <span data-ttu-id="9ed7a-103">このセクションのトピックでは、アップグレードに関連する検出可能な問題と、検出できずアップグレードまたはアップグレード後の動作に影響することが考えられる問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ed7a-103">The topics in this section describe upgrade issues that can be detected as well as those that cannot be detected, but that might affect the upgrade or post-upgrade experience.</span></span> <span data-ttu-id="9ed7a-104">これらの問題は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントごとにまとめられています。</span><span class="sxs-lookup"><span data-stu-id="9ed7a-104">The issues are organized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ed7a-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9ed7a-105">In This Section</span></span>  
  
-   [<span data-ttu-id="9ed7a-106">アップグレードに関する最新の問題</span><span class="sxs-lookup"><span data-stu-id="9ed7a-106">Late-Breaking Upgrade Issues</span></span>](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [<span data-ttu-id="9ed7a-107">データベース エンジンのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="9ed7a-107">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [<span data-ttu-id="9ed7a-108">フルテキスト検索のアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="9ed7a-108">Full-Text Search Upgrade Issues</span></span>](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [<span data-ttu-id="9ed7a-109">レプリケーションのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="9ed7a-109">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [<span data-ttu-id="9ed7a-110">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="9ed7a-110">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [<span data-ttu-id="9ed7a-111">SQL Server エージェントのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="9ed7a-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a><span data-ttu-id="9ed7a-112">アップグレードを妨げる問題</span><span class="sxs-lookup"><span data-stu-id="9ed7a-112">Issues That Prevent Upgrading</span></span>  
 <span data-ttu-id="9ed7a-113">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の構成または設定が原因で、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードできなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ed7a-113">A few configurations or settings in a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can prevent you from upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9ed7a-114">のインストール時にセットアップでこれらの問題が検出された場合 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、セットアップによってアップグレードプロセスが停止され、アップグレードアドバイザーを実行して、ブロックの問題を修正するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="9ed7a-114">If Setup detects these issues when you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Setup stops the upgrade process and requests that you run Upgrade Advisor and fix any blocking issues.</span></span>  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 <span data-ttu-id="9ed7a-115">以下のタスクが[!INCLUDE[ssDE](../../includes/ssde-md.md)]のアップグレード レポートに表示された場合は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードする前に必要な操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ed7a-115">If the following tasks are listed on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] upgrade report, you must perform the required actions before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:</span></span>  
  
-   [<span data-ttu-id="9ed7a-116">データベース ID 32767 をデタッチする</span><span class="sxs-lookup"><span data-stu-id="9ed7a-116">Detach database ID 32767</span></span>](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [<span data-ttu-id="9ed7a-117">固定サーバー ロール名と一致するログイン名を変更する</span><span class="sxs-lookup"><span data-stu-id="9ed7a-117">Rename logins matching fixed server role names</span></span>](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [<span data-ttu-id="9ed7a-118">ユーザー sys の名前変更が必要</span><span class="sxs-lookup"><span data-stu-id="9ed7a-118">Rename user sys</span></span>](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [<span data-ttu-id="9ed7a-119">sp_rename を使用して重複するインデックス名を変更する</span><span class="sxs-lookup"><span data-stu-id="9ed7a-119">Use sp_rename to rename duplicate index name</span></span>](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ed7a-120">参照</span><span class="sxs-lookup"><span data-stu-id="9ed7a-120">See Also</span></span>  
 [<span data-ttu-id="9ed7a-121">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="9ed7a-121">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
