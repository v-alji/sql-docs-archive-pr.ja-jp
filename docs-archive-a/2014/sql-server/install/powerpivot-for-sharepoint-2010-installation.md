---
title: PowerPivot for SharePoint 2010 のインストール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 8d47dde7-c941-4280-a934-e2fe3f9a938f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ba04dfdc69b1c510a800c062586e45f8873c8e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643678"
---
# <a name="powerpivot-for-sharepoint-2010-installation"></a><span data-ttu-id="71892-102">PowerPivot for SharePoint 2010 のインストール</span><span class="sxs-lookup"><span data-stu-id="71892-102">PowerPivot for SharePoint 2010 Installation</span></span>
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] <span data-ttu-id="71892-103">は、SharePoint にパブリッシュする [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックのクエリ処理と管理を行う、サーバー コンポーネントのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="71892-103">is a collection of server components that provide query processing and management control over [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks that you publish to SharePoint.</span></span> <span data-ttu-id="71892-104">サービスには、Analysis Services エンジンと [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="71892-104">Services include the Analysis Services engine and [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71892-105">[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] および SharePoint Server 2013 のインストールについては、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71892-105">For information regarding [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] and installation with SharePoint Server 2013, see the following:</span></span>  
>   
>  -   <span data-ttu-id="71892-106">「 [SQL Server サービスのインストールの概要](../../../2014/sql-server/install/overview-of-sql-server-servicing-installation.md)」の「SQL SERVER 2012 SP1」セクション。</span><span class="sxs-lookup"><span data-stu-id="71892-106">The "SQL Server 2012 SP1" section of [Overview of SQL Server Servicing Installation](../../../2014/sql-server/install/overview-of-sql-server-servicing-installation.md).</span></span>  
  
 <span data-ttu-id="71892-107">Analysis Services は、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含む Excel ブックにサーバー側の処理を提供します。</span><span class="sxs-lookup"><span data-stu-id="71892-107">Analysis Services provides server-side processing for Excel workbooks that contain [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data.</span></span> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="71892-108">System サービスは Analysis Services と連動して、SharePoint 統合、負荷分散、および接続管理を追加します。</span><span class="sxs-lookup"><span data-stu-id="71892-108">System Service works alongside Analysis Services, adding SharePoint integration, load balancing and connection management.</span></span> [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]<span data-ttu-id="71892-109">では、大規模なデータ処理機能と Excel が提供するデータレンダリングサービスを組み合わせることで、Excel Services を拡張します。</span><span class="sxs-lookup"><span data-stu-id="71892-109">extends Excel Services by pairing its large scale data processing capability with the data rendering services that Excel provides.</span></span>  
  
 <span data-ttu-id="71892-110">をインストールするに [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] は、のインストールメディアを使用し [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="71892-110">To install [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], use the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]installation media.</span></span>  
  
 <span data-ttu-id="71892-111">高度な配置シナリオの手順については、「[配置のチェックリスト: Reporting Services、Power View、および PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)と[配置のチェックリスト: PowerPivot サーバーを SharePoint 2010 ファームに追加することによるスケールアウト](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71892-111">For instructions on advanced deployment scenarios, see [Deployment Checklist: Reporting Services, Power View, and PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) and [Deployment Checklist: Scale-out by adding PowerPivot Servers to a SharePoint 2010 farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71892-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="71892-112">In This Section</span></span>  
 [<span data-ttu-id="71892-113">PowerPivot for SharePoint 2010 をインストールする</span><span class="sxs-lookup"><span data-stu-id="71892-113">Install PowerPivot for SharePoint 2010</span></span>](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)  
  
 [<span data-ttu-id="71892-114">SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール</span><span class="sxs-lookup"><span data-stu-id="71892-114">Install the Analysis Services OLE DB Provider on SharePoint Servers</span></span>](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 [<span data-ttu-id="71892-115">サーバーの全体管理を実行している Web フロントエンド サーバーに ADOMD.NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="71892-115">Install ADOMD.NET on Web Front-End Servers Running Central Administration</span></span>](../../../2014/sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)  
  
 [<span data-ttu-id="71892-116">SharePoint リストのデータ フィードのエクスポートをサポートする ADO.NET Data Services のインストール</span><span class="sxs-lookup"><span data-stu-id="71892-116">Install ADO.NET Data Services to support data feed exports of SharePoint lists</span></span>](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md)  
  
 [<span data-ttu-id="71892-117">コマンド プロンプトからの PowerPivot のインストール</span><span class="sxs-lookup"><span data-stu-id="71892-117">Install PowerPivot from the Command Prompt</span></span>](../../../2014/sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
 [<span data-ttu-id="71892-118">PowerPivot for SharePoint のアンインストール</span><span class="sxs-lookup"><span data-stu-id="71892-118">Uninstall PowerPivot for SharePoint</span></span>](../../../2014/sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
 [<span data-ttu-id="71892-119">PowerPivot for SharePoint の修復</span><span class="sxs-lookup"><span data-stu-id="71892-119">Repair PowerPivot for SharePoint</span></span>](../../../2014/sql-server/install/repair-powerpivot-for-sharepoint.md)  
  
 [<span data-ttu-id="71892-120">初期構成 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="71892-120">Initial Configuration &#40;PowerPivot for SharePoint&#41;</span></span>](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
## <a name="see-also"></a><span data-ttu-id="71892-121">参照</span><span class="sxs-lookup"><span data-stu-id="71892-121">See Also</span></span>  
 [<span data-ttu-id="71892-122">サーバーの全体管理での PowerPivot サーバーの管理と構成</span><span class="sxs-lookup"><span data-stu-id="71892-122">PowerPivot Server Administration and Configuration in Central Administration</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)  
  
  
