---
title: イメージの準備ルール |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 609a7c06-9527-4ef5-8e75-0c44e1958c5a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8c9c09e6e9abb3ee3e17d4942cb8e518f5d551a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643675"
---
# <a name="prepare-image-rules"></a><span data-ttu-id="4f9f3-102">イメージの準備ルール</span><span class="sxs-lookup"><span data-stu-id="4f9f3-102">Prepare Image Rules</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4f9f3-103">セットアップによって、セットアップ操作が完了する前にコンピューターの構成が検証されます。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-103">Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="4f9f3-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップの実行中、システム構成チェッカー (SCC) は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール先コンピューターをスキャンします。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the System Configuration Checker (SCC) scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed.</span></span> <span data-ttu-id="4f9f3-105">SCC は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ操作の成功を妨げる条件がないかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-105">The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="4f9f3-106">セットアップでウィザードが起動する前に、SCC は各項目の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-106">Before Setup starts the wizard, the SCC retrieves the status of each item.</span></span> <span data-ttu-id="4f9f3-107">次に、必要な条件と取得した結果を比較し、ブロックの問題解決に関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-107">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="4f9f3-108">システム構成チェッカーは、実行された各ルールの簡単な記述と、実行ステータスを含むレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-108">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="4f9f3-109">システム構成チェックのレポートは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-109">The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="4f9f3-110">セットアップ操作を実行する前に、次のトピックを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-110">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="4f9f3-111">SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア</span><span class="sxs-lookup"><span data-stu-id="4f9f3-111">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="4f9f3-112">SQL Server 2014 の各エディションがサポートする機能</span><span class="sxs-lookup"><span data-stu-id="4f9f3-112">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="4f9f3-113">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="4f9f3-113">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="4f9f3-114">SQL Server のローカル言語版</span><span class="sxs-lookup"><span data-stu-id="4f9f3-114">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="4f9f3-115">その他の参考資料:</span><span class="sxs-lookup"><span data-stu-id="4f9f3-115">Other references:</span></span>  
  
1.  [<span data-ttu-id="4f9f3-116">サポートされているバージョンとエディションのアップグレード</span><span class="sxs-lookup"><span data-stu-id="4f9f3-116">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="4f9f3-117">フェールオーバー クラスタリングをインストールする前に</span><span class="sxs-lookup"><span data-stu-id="4f9f3-117">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
  
