---
title: 下位互換性 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Surface Area Configuration Tool
- command prompt [SQL Server], discontinued parameters
- discontinued functionality [SQL Server]
- compatibility [SQL Server], discontinued features
- SAC tool
- compatibility [Analysis Services]
- compatibility [Integration Services]
- SQL Server, discontinued features
- compatibility [Replication]
- compatibility [SQL Server]
- previous versions [SQL Server], (See also backward compatibility)
- backward compatibility [SQL Server]
- compatibility [Reporting Services]
- earlier versions [SQL Server], (See also backward compatibility)
ms.assetid: 15d9117e-e2fa-4985-99ea-66a117c1e9fd
author: rothja
ms.author: jroth
ms.openlocfilehash: fd8be66efd648f5b6703a76855a549a9bd30f1e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645774"
---
# <a name="backward-compatibility"></a><span data-ttu-id="5f25e-102">Backward Compatibility</span><span class="sxs-lookup"><span data-stu-id="5f25e-102">Backward Compatibility</span></span>
  <span data-ttu-id="5f25e-103">次の各セクションでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントの旧バージョンとの互換性について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f25e-103">The following sections contain backward compatibility information for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="5f25e-104">この内容には、非推奨の機能、提供が中止された機能、重大な変更、および動作変更に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f25e-104">This content includes information about deprecated features, discontinued features, breaking changes, and behavior changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f25e-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5f25e-105">In This Section</span></span>  
  
|<span data-ttu-id="5f25e-106">トピック</span><span class="sxs-lookup"><span data-stu-id="5f25e-106">Topic</span></span>|<span data-ttu-id="5f25e-107">説明</span><span class="sxs-lookup"><span data-stu-id="5f25e-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5f25e-108">SQL Server の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="5f25e-108">SQL Server Backward Compatibility</span></span>](../../2014/getting-started/sql-server-backward-compatibility.md)|<span data-ttu-id="5f25e-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に加えられた変更について説明します。これらの変更に伴い、一部のアプリケーションは修正が必要になります。</span><span class="sxs-lookup"><span data-stu-id="5f25e-109">Contains topics that describe changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span> <span data-ttu-id="5f25e-110">このトピック領域に含まれる機能には、データ プログラミング、セキュリティ構成ツール、セットアップ、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス、およびその他の幅広い機能の変更が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5f25e-110">Features that are included in this topic area include data programmability, surface area configuration tools, Setup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services, and other broad functionality changes.</span></span>|  
|[<span data-ttu-id="5f25e-111">SQL Server データベース エンジンの旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="5f25e-111">SQL Server Database Engine Backward Compatibility</span></span>](../database-engine/sql-server-database-engine-backward-compatibility.md)|<span data-ttu-id="5f25e-112">[!INCLUDE[ssDE](../includes/ssde-md.md)] の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に加えられた変更について説明します。これらの変更に伴い、一部のアプリケーションは修正が必要になります。</span><span class="sxs-lookup"><span data-stu-id="5f25e-112">Contains topics that describe [!INCLUDE[ssDE](../includes/ssde-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span>|  
|[<span data-ttu-id="5f25e-113">Analysis Services の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="5f25e-113">Analysis Services Backward Compatibility</span></span>](../../2014/analysis-services/analysis-services-backward-compatibility.md)|<span data-ttu-id="5f25e-114">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に加えられた変更について説明します。これらの変更に伴い、一部のアプリケーションは修正が必要になります。</span><span class="sxs-lookup"><span data-stu-id="5f25e-114">Contains topics that describe [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span>|  
|[<span data-ttu-id="5f25e-115">Integration Services の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="5f25e-115">Integration Services Backward Compatibility</span></span>](../integration-services/integration-services-backward-compatibility.md)|<span data-ttu-id="5f25e-116">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に加えられた変更について説明します。これらの変更に伴い、場合によっては、既存のデータ変換サービス アプリケーションを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f25e-116">Describes [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing Data Transformation Services applications.</span></span>|  
|[<span data-ttu-id="5f25e-117">Reporting Services の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="5f25e-117">Reporting Services Backward Compatibility</span></span>](../reporting-services/reporting-services-backward-compatibility.md)|<span data-ttu-id="5f25e-118">[!INCLUDE[ssRS](../includes/ssrs.md)] の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に加えられた変更について説明します。これらの変更に伴い、場合によっては、既存の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ソリューションを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f25e-118">Contains topics that describe [!INCLUDE[ssRS](../includes/ssrs.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] solutions.</span></span>|  
|[<span data-ttu-id="5f25e-119">旧バージョンとの互換性 &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="5f25e-119">Backward Compatibility &#40;Master Data Services&#41;</span></span>](../master-data-services/backward-compatibility-master-data-services.md)|<span data-ttu-id="5f25e-120">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に加えられた変更について説明します。これらの変更に伴い、場合によっては、既存の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ソリューションを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f25e-120">Contains topics that describe [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] solutions.</span></span>|  
|[<span data-ttu-id="5f25e-121">レプリケーションの旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="5f25e-121">Replication Backward Compatibility</span></span>](../../2014/relational-databases/replication/replication-backward-compatibility.md)|<span data-ttu-id="5f25e-122">[!INCLUDE[ssDE](../includes/ssde-md.md)] の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に加えられた変更について説明します。これらの変更に伴い、場合によっては、既存のレプリケーション ソリューションを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f25e-122">Contains topics that describe [!INCLUDE[ssDE](../includes/ssde-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to existing Replication solutions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f25e-123">参照</span><span class="sxs-lookup"><span data-stu-id="5f25e-123">See Also</span></span>  
 <span data-ttu-id="5f25e-124">[SQL Server 2014 をインストールする](../database-engine/install-windows/install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5f25e-124">[Install SQL Server 2014](../database-engine/install-windows/install-sql-server.md) </span></span>  
 [<span data-ttu-id="5f25e-125">SQL Server 2014 へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="5f25e-125">Upgrade to SQL Server 2014</span></span>](../database-engine/install-windows/upgrade-sql-server.md)  
  
  
