---
title: インストールルール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SCC
- System Configuration Check, Setup
helpviewer_keywords:
- System Configuration Check page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, System Configuration Check page
- SCC [SQL Server]
ms.assetid: 168c0445-5651-42fc-91f4-d9f27d9e2281
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3d9fe413174613cadc9277e5c7f21695a4021c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737579"
---
# <a name="install-rules"></a><span data-ttu-id="5fe82-102">インストール ルール</span><span class="sxs-lookup"><span data-stu-id="5fe82-102">Install Rules</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5fe82-103">セットアップによって、セットアップ操作が完了する前にコンピューターの構成が検証されます。</span><span class="sxs-lookup"><span data-stu-id="5fe82-103">Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="5fe82-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップの実行中、システム構成チェッカー (SCC) は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール先コンピューターをスキャンします。</span><span class="sxs-lookup"><span data-stu-id="5fe82-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the System Configuration Checker (SCC) scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed.</span></span> <span data-ttu-id="5fe82-105">SCC は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ操作の成功を妨げる条件がないかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="5fe82-105">The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="5fe82-106">セットアップで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードが起動する前に、SCC は各項目の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="5fe82-106">Before Setup starts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard, the SCC retrieves the status of each item.</span></span> <span data-ttu-id="5fe82-107">次に、必要な条件と取得した結果を比較し、ブロックの問題解決に関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5fe82-107">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="5fe82-108">システム構成チェッカーは、実行された各ルールの簡単な記述と、実行ステータスを含むレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="5fe82-108">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="5fe82-109">システム構成チェックのレポートは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="5fe82-109">The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="5fe82-110">セットアップ操作を実行する前に、次のトピックを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5fe82-110">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="5fe82-111">SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア</span><span class="sxs-lookup"><span data-stu-id="5fe82-111">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="5fe82-112">SQL Server 2014 の各エディションがサポートする機能</span><span class="sxs-lookup"><span data-stu-id="5fe82-112">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="5fe82-113">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="5fe82-113">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="5fe82-114">SQL Server のローカル言語版</span><span class="sxs-lookup"><span data-stu-id="5fe82-114">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="5fe82-115">その他の参考資料:</span><span class="sxs-lookup"><span data-stu-id="5fe82-115">Other references:</span></span>  
  
1.  [<span data-ttu-id="5fe82-116">サポートされているバージョンとエディションのアップグレード</span><span class="sxs-lookup"><span data-stu-id="5fe82-116">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="5fe82-117">フェールオーバー クラスタリングをインストールする前に</span><span class="sxs-lookup"><span data-stu-id="5fe82-117">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="additional-rule-topics"></a><span data-ttu-id="5fe82-118">その他のルール トピック</span><span class="sxs-lookup"><span data-stu-id="5fe82-118">Additional Rule topics</span></span>  
 <span data-ttu-id="5fe82-119">シナリオ固有のセットアップ ルールについては、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fe82-119">See the following topics for scenario-specific Setup rules:</span></span>  
  
-   [<span data-ttu-id="5fe82-120">インストール ルール</span><span class="sxs-lookup"><span data-stu-id="5fe82-120">Installation Rules</span></span>](../../../2014/sql-server/install/installation-rules.md)  
  
-   [<span data-ttu-id="5fe82-121">機能ルール &#40;アップグレード&#41;</span><span class="sxs-lookup"><span data-stu-id="5fe82-121">Feature Rules &#40;Upgrade&#41;</span></span>](../../../2014/sql-server/install/feature-rules-upgrade.md)  
  
-   [<span data-ttu-id="5fe82-122">エディションのアップグレード規則</span><span class="sxs-lookup"><span data-stu-id="5fe82-122">Edition Upgrade Rules</span></span>](../../../2014/sql-server/install/edition-upgrade-rules.md)  
  
-   [<span data-ttu-id="5fe82-123">アンインストール ルール</span><span class="sxs-lookup"><span data-stu-id="5fe82-123">Uninstallation rules</span></span>](../../../2014/sql-server/install/uninstallation-rules.md)  
  
-   [<span data-ttu-id="5fe82-124">イメージの準備ルール</span><span class="sxs-lookup"><span data-stu-id="5fe82-124">Prepare Image Rules</span></span>](../../../2014/sql-server/install/prepare-image-rules.md)  
  
-   [<span data-ttu-id="5fe82-125">イメージの完了ルール</span><span class="sxs-lookup"><span data-stu-id="5fe82-125">Complete Image Rules</span></span>](../../../2014/sql-server/install/complete-image-rules.md)  
  
  
