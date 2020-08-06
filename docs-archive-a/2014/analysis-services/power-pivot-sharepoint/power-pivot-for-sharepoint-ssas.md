---
title: PowerPivot for SharePoint (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58ebcf004224d21ab5b47aaee1e2e7e3ef2047ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641289"
---
# <a name="powerpivot-for-sharepoint-ssas"></a><span data-ttu-id="4d764-102">PowerPivot for SharePoint (SSAS)</span><span class="sxs-lookup"><span data-stu-id="4d764-102">PowerPivot for SharePoint (SSAS)</span></span>
  <span data-ttu-id="4d764-103">PowerPivot for SharePoint は、SharePoint モードで実行される [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーです。</span><span class="sxs-lookup"><span data-stu-id="4d764-103">PowerPivot for SharePoint is a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server running in SharePoint mode.</span></span> <span data-ttu-id="4d764-104">PowerPivot for SharePoint は、SharePoint ファーム内の PowerPivot データのサーバー ホスティングを実現します。</span><span class="sxs-lookup"><span data-stu-id="4d764-104">PowerPivot for SharePoint provides server hosting of PowerPivot data in a SharePoint farm.</span></span> <span data-ttu-id="4d764-105">PowerPivot データは、次のいずれかを使用して構築する分析データモデルです。</span><span class="sxs-lookup"><span data-stu-id="4d764-105">PowerPivot data is an analytical data model that you build using one of the following:</span></span>  
  
-   <span data-ttu-id="4d764-106">PowerPivot for Excel 2010 アドイン</span><span class="sxs-lookup"><span data-stu-id="4d764-106">The PowerPivot for Excel 2010 add-in</span></span>  
  
-   <span data-ttu-id="4d764-107">Excel 2013</span><span class="sxs-lookup"><span data-stu-id="4d764-107">Excel 2013</span></span>  
  
 <span data-ttu-id="4d764-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013 |[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010</span><span class="sxs-lookup"><span data-stu-id="4d764-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010</span></span>  
  
 <span data-ttu-id="4d764-109">そのデータをサーバーでホストするには、SharePoint、Excel Services、および PowerPivot for SharePoint のインストールが必要です。</span><span class="sxs-lookup"><span data-stu-id="4d764-109">Server hosting of that data requires SharePoint, Excel Services, and an installation of PowerPivot for SharePoint.</span></span> <span data-ttu-id="4d764-110">PowerPivot for SharePoint インスタンスにデータが読み込まれます。このデータは、PowerPivot データ更新機能を使用してスケジュール設定された間隔で更新できます。Excel 2010 ブックの場合はこの更新機能がサーバーで実行され、Excel 2013 ブックの場合は SharePoint 2013 Excel Services で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4d764-110">Data is loaded on PowerPivot for SharePoint instances where it can be refreshed at scheduled intervals using the PowerPivot data refresh capability that the server provides for Excel 2010 workbooks or that SharePoint 2013 Excel Services provides for Excel 2013 workbooks.</span></span>  
  
## <a name="powerpivot-for-sharepoint-2013"></a><span data-ttu-id="4d764-111">PowerPivot for SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="4d764-111">PowerPivot for SharePoint 2013</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="4d764-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]サポート [!INCLUDE[msCoName](../../includes/msconame-md.md)]SharePoint 2013 の Excel Services では、データモデルと Power View レポートを含む Excel ブックが使用さ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="4d764-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] supports [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 2013 Excel Services usage of Excel workbooks containing data models and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Power View reports.</span></span>  
  
 <span data-ttu-id="4d764-113">SharePoint 2013 の Excel Services には、ブラウザー上で PowerPivot ブックを操作できるようにするためのデータ モデル機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4d764-113">Excel Services in SharePoint 2013 includes data model functionality to enable interaction with a PowerPivot workbook in the browser.</span></span> <span data-ttu-id="4d764-114">ファームに PowerPivot for SharePoint 2013 アドインを配置する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4d764-114">You do not need to deploy the PowerPivot for SharePoint 2013 add-in into the farm.</span></span> <span data-ttu-id="4d764-115">必要な操作は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーを SharePoint モードでインストールし、Excel Services の **[データ モデルの設定]** でサーバーを登録するだけです。</span><span class="sxs-lookup"><span data-stu-id="4d764-115">You only need to install an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server in SharePoint mode and register the server within the Excel Services **Data Model** settings.</span></span>  
  
 <span data-ttu-id="4d764-116">PowerPivot for SharePoint 2013 アドインを配置すると、SharePoint ファームで追加の機能を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4d764-116">Deploying the PowerPivot for SharePoint 2013 add-in enables additional functionality and features in your SharePoint farm.</span></span> <span data-ttu-id="4d764-117">追加の機能には、PowerPivot ギャラリー、データ更新のスケジュール、および PowerPivot 管理ダッシュボードがあります。</span><span class="sxs-lookup"><span data-stu-id="4d764-117">The additional features include PowerPivot Gallery, Schedule Data Refresh, and the PowerPivot Management Dashboard.</span></span>  
  
 <span data-ttu-id="4d764-118">![SSAS PowerPivot モード 2 のサーバー配置](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot モード 2 のサーバー配置")</span><span class="sxs-lookup"><span data-stu-id="4d764-118">![SSAS PowerPivot Mode 2 Server Deployment](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot Mode 2 Server Deployment")</span></span>  
  
## <a name="powerpivot-for-sharepoint-2010"></a><span data-ttu-id="4d764-119">PowerPivot for SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="4d764-119">PowerPivot for SharePoint 2010</span></span>  
 <span data-ttu-id="4d764-120">PowerPivot for SharePoint 2010 は、SharePoint 2010 ファーム内の PowerPivot データのサーバー ホスティングを実現します。</span><span class="sxs-lookup"><span data-stu-id="4d764-120">PowerPivot for SharePoint 2010 provides server hosting of PowerPivot data in a SharePoint 2010 farm.</span></span> <span data-ttu-id="4d764-121">PowerPivot データは、PowerPivot for Excel アドインを使用して Excel で構築する分析データ モデルです。</span><span class="sxs-lookup"><span data-stu-id="4d764-121">PowerPivot data is an analytical data model that you build in Excel using the PowerPivot for Excel add-in.</span></span> <span data-ttu-id="4d764-122">そのデータをサーバーでホストするには、SharePoint 2010、Excel Services、および PowerPivot for SharePoint のインストールが必要です。</span><span class="sxs-lookup"><span data-stu-id="4d764-122">Server hosting of that data requires SharePoint 2010, Excel Services, and an installation of PowerPivot for SharePoint.</span></span> <span data-ttu-id="4d764-123">ファーム内の PowerPivot for SharePoint インスタンスにデータが読み込まれます。このデータは、サーバーに用意されている PowerPivot データ更新機能を使用して、スケジュール設定された間隔で更新できます。</span><span class="sxs-lookup"><span data-stu-id="4d764-123">Data is loaded on PowerPivot for SharePoint instances in the farm, where it can be refreshed at scheduled intervals using the PowerPivot data refresh capability that the server provides.</span></span>  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a><span data-ttu-id="4d764-124">PowerPivot for SharePoint 2010 のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="4d764-124">Components of PowerPivot for SharePoint 2010</span></span>  
 <span data-ttu-id="4d764-125">PowerPivot for SharePoint は、共有サービスとして実装されています。共有サービスとは、組み込みの機能とインフラストラクチャを使用して、PowerPivot サービス アプリケーションを管理、セキュリティ保護、および使用できることです。</span><span class="sxs-lookup"><span data-stu-id="4d764-125">PowerPivot for SharePoint is implemented as a shared service, which means that the built-in features and infrastructure can be used to administer, secure, and use a PowerPivot service application.</span></span> <span data-ttu-id="4d764-126">サーバーとデータベースの検出、リダイレクト、および接続の管理はすべて、ファーム レベルで管理されます。</span><span class="sxs-lookup"><span data-stu-id="4d764-126">Server and database discovery, redirection, and connection management is all managed at the farm level.</span></span> <span data-ttu-id="4d764-127">サーバーの全体管理には、サーバー ID、サーバーの状態、および構成プロパティの管理に使用するサービスへの管理インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4d764-127">Central Administration provides the administrative interface to the services used to manage server identity, server state, and configuration properties.</span></span>  
  
 <span data-ttu-id="4d764-128">PowerPivot for SharePoint の配置全体には、SharePoint ファーム内の Excel および Excel Services と統合されるクライアント コンポーネントおよびサーバー コンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4d764-128">A complete deployment of PowerPivot for SharePoint includes client and server components that integrate with Excel and Excel Services in a SharePoint farm.</span></span> <span data-ttu-id="4d764-129">Excel ブック内の PowerPivot データは Analysis Services データベースであり、データの読み込みとクエリには、Analysis Services xVelocity メモリ内分析エンジン (VertiPaq) が必要です。</span><span class="sxs-lookup"><span data-stu-id="4d764-129">The PowerPivot data inside an Excel workbook is an Analysis Services database that requires an Analysis Services xVelocity in-memory analytics engine (VertiPaq) to load and query the data.</span></span> <span data-ttu-id="4d764-130">クライアント ワークステーションでは、xVelocity エンジンは Excel 内でインプロセスとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="4d764-130">On a client workstation, the xVelocity engine runs in-process within Excel.</span></span> <span data-ttu-id="4d764-131">SharePoint ファームの Analysis Services は、アプリケーション サーバー上で実行され、関連サービスと組み合わされて、PowerPivot データに対する要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="4d764-131">On a SharePoint farm, Analysis Services runs on an application server where it is paired with related services that handle requests for PowerPivot data.</span></span> <span data-ttu-id="4d764-132">次の図は、PowerPivot クライアントとサーバー コンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="4d764-132">The following diagram illustrates PowerPivot client and server components:</span></span>  
  
 <span data-ttu-id="4d764-133">![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")</span><span class="sxs-lookup"><span data-stu-id="4d764-133">![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")</span></span>  
  
 <span data-ttu-id="4d764-134">PowerPivot Web サービスは Web アプリケーション サーバー上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4d764-134">PowerPivot Web service runs on a web application server.</span></span> <span data-ttu-id="4d764-135">Web アプリケーションからの要求は、ファーム内の PowerPivot System サービス インスタンスにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="4d764-135">It redirects requests from the web application to a PowerPivot System Service instance in the farm.</span></span>  
  
 <span data-ttu-id="4d764-136">PowerPivot System サービスは、Analysis Services サーバーへの読み込み要求を発行します。キャッシュを実行したり、使用されなくなった際やシステム リソースに競合が発生した際にデータをアンロードしたりして、既にメモリに読み込まれているデータへの継続的な接続を管理します。</span><span class="sxs-lookup"><span data-stu-id="4d764-136">PowerPivot System Service issues load requests to the Analysis Services server and manages ongoing connections to data that is already loaded in memory, caching or unloading data if it is no longer used or when there is contention for system resources.</span></span> <span data-ttu-id="4d764-137">ユーザー利用状況の追跡も行います。</span><span class="sxs-lookup"><span data-stu-id="4d764-137">It also tracks user activity.</span></span> <span data-ttu-id="4d764-138">サーバーの状態データやその他の使用状況データは収集されてレポートに表示され、システム パフォーマンスを示します。</span><span class="sxs-lookup"><span data-stu-id="4d764-138">Server health data and other usage data is gathered and presented in reports to indicate how well the system is performing.</span></span>  
  
 <span data-ttu-id="4d764-139">SharePoint 統合モードの Analysis Service サーバー インスタンスで、配置が完了します。</span><span class="sxs-lookup"><span data-stu-id="4d764-139">An Analysis Service server instance in SharePoint integrated mode completes the deployment.</span></span> <span data-ttu-id="4d764-140">データの読み込み、クエリ、アンロードを行います。</span><span class="sxs-lookup"><span data-stu-id="4d764-140">It loads, queries, and unloads data.</span></span> <span data-ttu-id="4d764-141">ブックに PowerPivot データ更新が構成されている場合、データの処理も行います。</span><span class="sxs-lookup"><span data-stu-id="4d764-141">It also processes data if the workbook is configured for PowerPivot data refresh.</span></span>  <span data-ttu-id="4d764-142">各インスタンスは、同じインストールに含まれるローカルの PowerPivot System サービスと緊密に連携します。</span><span class="sxs-lookup"><span data-stu-id="4d764-142">Each instance is tightly coupled with the local PowerPivot System Service that is part of the same installation.</span></span>  
  
##  <a name="in-this-section"></a><a name="bkmk_RelatedContent"></a> <span data-ttu-id="4d764-143">トピックの内容</span><span class="sxs-lookup"><span data-stu-id="4d764-143">In This Section</span></span>  
 [<span data-ttu-id="4d764-144">サーバーの全体管理での PowerPivot サーバーの管理と構成</span><span class="sxs-lookup"><span data-stu-id="4d764-144">PowerPivot Server Administration and Configuration in Central Administration</span></span>](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [<span data-ttu-id="4d764-145">Windows PowerShell を使用した PowerPivot の構成</span><span class="sxs-lookup"><span data-stu-id="4d764-145">PowerPivot Configuration using Windows PowerShell</span></span>](power-pivot-configuration-using-windows-powershell.md)  
  
 [<span data-ttu-id="4d764-146">PowerPivot Configuration Tools</span><span class="sxs-lookup"><span data-stu-id="4d764-146">PowerPivot Configuration Tools</span></span>](power-pivot-configuration-tools.md)  
  
 [<span data-ttu-id="4d764-147">PowerPivot の認証および承認</span><span class="sxs-lookup"><span data-stu-id="4d764-147">PowerPivot Authentication and Authorization</span></span>](power-pivot-authentication-and-authorization.md)  
  
 [<span data-ttu-id="4d764-148">PowerPivot の正常性ルール - 構成</span><span class="sxs-lookup"><span data-stu-id="4d764-148">PowerPivot Health Rules - Configure</span></span>](configure-power-pivot-health-rules.md)  
  
 [<span data-ttu-id="4d764-149">PowerPivot 管理ダッシュボードと使用状況データ</span><span class="sxs-lookup"><span data-stu-id="4d764-149">PowerPivot Management Dashboard and Usage Data</span></span>](power-pivot-management-dashboard-and-usage-data.md)  
  
 [<span data-ttu-id="4d764-150">PowerPivot ギャラリー</span><span class="sxs-lookup"><span data-stu-id="4d764-150">PowerPivot Gallery</span></span>](../../index.yml)  
  
 [<span data-ttu-id="4d764-151">PowerPivot データ アクセス</span><span class="sxs-lookup"><span data-stu-id="4d764-151">PowerPivot Data Access</span></span>](power-pivot-data-access.md)  
  
 [<span data-ttu-id="4d764-152">PowerPivot のデータ更新</span><span class="sxs-lookup"><span data-stu-id="4d764-152">PowerPivot Data Refresh</span></span>](power-pivot-data-refresh.md)  
  
 [<span data-ttu-id="4d764-153">PowerPivot データ フィード</span><span class="sxs-lookup"><span data-stu-id="4d764-153">PowerPivot Data Feeds</span></span>](power-pivot-data-feeds.md)  
  
 [<span data-ttu-id="4d764-154">PowerPivot BI セマンティックモデル接続 &#40;。 bism&#41;</span><span class="sxs-lookup"><span data-stu-id="4d764-154">PowerPivot BI Semantic Model Connection &#40;.bism&#41;</span></span>](power-pivot-bi-semantic-model-connection-bism.md)  
  
 <span data-ttu-id="4d764-155">**他のセクション**</span><span class="sxs-lookup"><span data-stu-id="4d764-155">**In other sections**</span></span>  
  
## <a name="additional-topics"></a><span data-ttu-id="4d764-156">関連トピック</span><span class="sxs-lookup"><span data-stu-id="4d764-156">Additional topics</span></span>  
 [<span data-ttu-id="4d764-157">PowerPivot for SharePoint のアップグレード</span><span class="sxs-lookup"><span data-stu-id="4d764-157">Upgrade PowerPivot for SharePoint</span></span>](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [<span data-ttu-id="4d764-158">PowerPivot for SharePoint 2013 のインストール</span><span class="sxs-lookup"><span data-stu-id="4d764-158">PowerPivot for SharePoint 2013 Installation</span></span>](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [<span data-ttu-id="4d764-159">PowerShell リファレンス (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="4d764-159">PowerShell Reference for PowerPivot for SharePoint</span></span>](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [<span data-ttu-id="4d764-160">SQL Server 2014 セルフサービスビジネスインテリジェンスのライセンストポロジとコストの例</span><span class="sxs-lookup"><span data-stu-id="4d764-160">Example License Topologies and Costs  for SQL Server 2014 Self-Service Business Intelligence</span></span>](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a><span data-ttu-id="4d764-161">参照</span><span class="sxs-lookup"><span data-stu-id="4d764-161">See Also</span></span>  
 <span data-ttu-id="4d764-162">[PowerPivot の計画と配置](https://go.microsoft.com/fwlink/?linkID=220972) </span><span class="sxs-lookup"><span data-stu-id="4d764-162">[PowerPivot Planning and Deployment](https://go.microsoft.com/fwlink/?linkID=220972) </span></span>  
 [<span data-ttu-id="4d764-163">PowerPivot for SharePoint の災害復旧</span><span class="sxs-lookup"><span data-stu-id="4d764-163">Disaster Recovery for PowerPivot for SharePoint</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
