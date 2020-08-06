---
title: 機能ルール (アップグレード) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 653b15db-a984-4b4b-b224-81b0285b099b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0527c1ba26fed86a6c1a3d3a2ea7c11b096474f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643144"
---
# <a name="feature-rules-upgrade"></a><span data-ttu-id="1c6bd-102">機能ルール (アップグレード)</span><span class="sxs-lookup"><span data-stu-id="1c6bd-102">Feature Rules (Upgrade)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1c6bd-103">セットアップによって、セットアップ操作が完了する前にコンピューターの構成が検証されます。</span><span class="sxs-lookup"><span data-stu-id="1c6bd-103">Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="1c6bd-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップの実行中に、システムは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール先であるコンピューターをスキャンし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の正常なセットアップ動作を妨げる可能性のある状態をチェックします。</span><span class="sxs-lookup"><span data-stu-id="1c6bd-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the system scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed and checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="1c6bd-105">セットアップがアップグレード ウィザードを起動する前に、各項目の状態が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1c6bd-105">Before Setup starts the upgrade wizard, it retrieves the status of each item.</span></span> <span data-ttu-id="1c6bd-106">次に、必要な条件と取得した結果を比較し、ブロックの問題解決に関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="1c6bd-106">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="1c6bd-107">システム構成チェッカーは、実行された各ルールの簡単な記述と、実行ステータスを含むレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="1c6bd-107">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="1c6bd-108">システム構成チェックのレポートは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="1c6bd-108">The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="1c6bd-109">セットアップ操作を実行する前に、次のトピックを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1c6bd-109">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="1c6bd-110">SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア</span><span class="sxs-lookup"><span data-stu-id="1c6bd-110">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="1c6bd-111">SQL Server 2014 の各エディションがサポートする機能</span><span class="sxs-lookup"><span data-stu-id="1c6bd-111">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="1c6bd-112">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="1c6bd-112">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="1c6bd-113">SQL Server のローカル言語版</span><span class="sxs-lookup"><span data-stu-id="1c6bd-113">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="1c6bd-114">その他の参考資料:</span><span class="sxs-lookup"><span data-stu-id="1c6bd-114">Other references:</span></span>  
  
1.  [<span data-ttu-id="1c6bd-115">サポートされているバージョンとエディションのアップグレード</span><span class="sxs-lookup"><span data-stu-id="1c6bd-115">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="1c6bd-116">フェールオーバー クラスタリングをインストールする前に</span><span class="sxs-lookup"><span data-stu-id="1c6bd-116">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c6bd-117">参照</span><span class="sxs-lookup"><span data-stu-id="1c6bd-117">See Also</span></span>  
 [<span data-ttu-id="1c6bd-118">インストール ルール</span><span class="sxs-lookup"><span data-stu-id="1c6bd-118">Install Rules</span></span>](../../../2014/sql-server/install/install-rules.md)  
  
  
