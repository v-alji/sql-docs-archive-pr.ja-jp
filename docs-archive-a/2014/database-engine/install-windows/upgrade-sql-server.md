---
title: SQL Server 2014 | にアップグレードします。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
ms.assetid: 5064e35b-b70d-4a0b-a9e9-fff04162f9d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 857bbd6d7269b7675653b11a9d7c0acd07927f62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714566"
---
# <a name="upgrade-to-sql-server-2014"></a><span data-ttu-id="a49ce-102">SQL Server 2014 へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-102">Upgrade to SQL Server 2014</span></span>
  <span data-ttu-id="a49ce-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のインスタンスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="a49ce-103">You can upgrade instances of, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a49ce-104">セットアップを実行してにアップグレードする前に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [SQL Server 2014 アップグレード技術ガイド](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf)(PDF ダウンロード) を確認し、このセクションのアップグレードプロセスに関するトピックを確認し、 [SQL Server 2014 のリリースノート](https://go.microsoft.com/fwlink/?LinkID=296445)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a49ce-104">Before running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], check out the [SQL Server 2014 Upgrade Technical Guide](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf) (PDF download), review the topics about the upgrade process in this section, and read the [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a49ce-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a49ce-105">In This Section</span></span>  
 <span data-ttu-id="a49ce-106">このセクションでは、以下のトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a49ce-106">This section contains the following topics:</span></span>  
  
-   [<span data-ttu-id="a49ce-107">サポートされているバージョンとエディションのアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-107">Supported Version and Edition Upgrades</span></span>](supported-version-and-edition-upgrades.md)  
  
-   [<span data-ttu-id="a49ce-108">アップグレード アドバイザーを使用したアップグレードの準備</span><span class="sxs-lookup"><span data-stu-id="a49ce-108">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
-   [<span data-ttu-id="a49ce-109">分散再生ユーティリティを使用したアップグレードの準備</span><span class="sxs-lookup"><span data-stu-id="a49ce-109">Use the Distributed Replay Utility to Prepare for Upgrades</span></span>](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)  
  
-   [<span data-ttu-id="a49ce-110">Analysis Services のアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-110">Upgrade Analysis Services</span></span>](upgrade-analysis-services.md)  
  
-   [<span data-ttu-id="a49ce-111">データベース エンジンのアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-111">Upgrade Database Engine</span></span>](upgrade-database-engine.md)  
  
-   [<span data-ttu-id="a49ce-112">Data Quality Services のアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-112">Upgrade Data Quality Services</span></span>](upgrade-data-quality-services.md)  
  
-   [<span data-ttu-id="a49ce-113">Integration Services のアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-113">Upgrade Integration Services</span></span>](../../integration-services/install-windows/upgrade-integration-services.md)  
  
-   [<span data-ttu-id="a49ce-114">マスター データ サービスのアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-114">Upgrade Master Data Services</span></span>](upgrade-master-data-services.md)  
  
-   [<span data-ttu-id="a49ce-115">PowerPivot for SharePoint のアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-115">Upgrade PowerPivot for SharePoint</span></span>](upgrade-power-pivot-for-sharepoint.md)  
  
-   [<span data-ttu-id="a49ce-116">レプリケートされたデータベースのアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-116">Upgrade Replicated Databases</span></span>](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
-   [<span data-ttu-id="a49ce-117">Reporting Services のアップグレードと移行</span><span class="sxs-lookup"><span data-stu-id="a49ce-117">Upgrade and Migrate Reporting Services</span></span>](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
  
-   [<span data-ttu-id="a49ce-118">SQL Server 管理ツールのアップグレード</span><span class="sxs-lookup"><span data-stu-id="a49ce-118">Upgrade SQL Server Management Tools</span></span>](upgrade-sql-server-management-tools.md)  
  
-   [<span data-ttu-id="a49ce-119">アップグレード方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="a49ce-119">Upgrade How-to Topics</span></span>](../../../2014/sql-server/install/upgrade-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="a49ce-120">参照</span><span class="sxs-lookup"><span data-stu-id="a49ce-120">See Also</span></span>  
 <span data-ttu-id="a49ce-121">[データベース エンジンのアップグレード](upgrade-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="a49ce-121">[Upgrade Database Engine](upgrade-database-engine.md) </span></span>  
 <span data-ttu-id="a49ce-122">[Analysis Services のアップグレード](upgrade-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="a49ce-122">[Upgrade Analysis Services](upgrade-analysis-services.md) </span></span>  
 <span data-ttu-id="a49ce-123">[Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="a49ce-123">[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span></span>  
 <span data-ttu-id="a49ce-124">[Integration Services のアップグレード](../../integration-services/install-windows/upgrade-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="a49ce-124">[Upgrade Integration Services](../../integration-services/install-windows/upgrade-integration-services.md) </span></span>  
 <span data-ttu-id="a49ce-125">[レプリケートされたデータベースのアップグレード](../../database-engine/install-windows/upgrade-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="a49ce-125">[Upgrade Replicated Databases](../../database-engine/install-windows/upgrade-replicated-databases.md) </span></span>  
 <span data-ttu-id="a49ce-126">[マスター データ サービスのアップグレード](upgrade-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a49ce-126">[Upgrade Master Data Services](upgrade-master-data-services.md) </span></span>  
 <span data-ttu-id="a49ce-127">[SQL Server 2012 ベストプラクティスアナライザー](https://www.microsoft.com/download/details.aspx?id=29302) </span><span class="sxs-lookup"><span data-stu-id="a49ce-127">[SQL Server 2012 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=29302) </span></span>  
 <span data-ttu-id="a49ce-128">[SQL Server 2008 R2 ベスト プラクティス アナライザー](https://www.microsoft.com/download/details.aspx?id=436) </span><span class="sxs-lookup"><span data-stu-id="a49ce-128">[SQL Server 2008 R2 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=436) </span></span>  
 [<span data-ttu-id="a49ce-129">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="a49ce-129">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
