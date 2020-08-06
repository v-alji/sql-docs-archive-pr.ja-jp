---
title: Integration Services サービス (SSIS サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, about Integration Services service
- SQL Server Integration Services service
- service [Integration Services],about Integration Services service
- service [Integration Services]
- SQL Server Integration Services, service
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04b24f0f0d54009c50654904d606a208504f229c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742390"
---
# <a name="integration-services-service-ssis-service"></a><span data-ttu-id="ed55e-102">Integration Services サービス (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="ed55e-102">Integration Services Service (SSIS Service)</span></span>
  <span data-ttu-id="ed55e-103">このセクションのトピックでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ed55e-103">The topics in this section discuss the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="ed55e-104">Integration Service パッケージの作成、保存、および実行には、このサービスは不要です。</span><span class="sxs-lookup"><span data-stu-id="ed55e-104">This service is not required to create, save, and run Integration Services packages.</span></span> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="ed55e-105">以前のリリースの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] との互換性を維持するために、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]サービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ed55e-105">supports the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ed55e-106">以降、では [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] `SSISDB` [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクト配置モデルを使用してサーバーに配置したプロジェクトのオブジェクト、設定、および操作データがデータベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ed55e-106">Starting in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores objects, settings, and operational data in the `SSISDB` database for projects that you've deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model.</span></span> <span data-ttu-id="ed55e-107">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データベース エンジンのインスタンスである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーは、データベースをホストします。</span><span class="sxs-lookup"><span data-stu-id="ed55e-107">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, which is an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine, hosts the database.</span></span> <span data-ttu-id="ed55e-108">データベースの詳細については、「 [SSIS カタログ](../catalog/ssis-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed55e-108">For more information about the database, see [SSIS Catalog](../catalog/ssis-catalog.md).</span></span> <span data-ttu-id="ed55e-109">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーへのプロジェクトの配置の詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../deploy-projects-to-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed55e-109">For more information about deploying projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
## <a name="management-capabilities"></a><span data-ttu-id="ed55e-110">管理機能</span><span class="sxs-lookup"><span data-stu-id="ed55e-110">Management Capabilities</span></span>  
 <span data-ttu-id="ed55e-111">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="ed55e-111">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is a Windows service for managing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="ed55e-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed55e-112">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is available only in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ed55e-113">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスを実行すると、以下の管理機能が使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed55e-113">Running the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service provides the following management capabilities:</span></span>  
  
-   <span data-ttu-id="ed55e-114">リモートまたはローカルに格納されたパッケージの開始</span><span class="sxs-lookup"><span data-stu-id="ed55e-114">Starting remote and locally stored packages</span></span>  
  
-   <span data-ttu-id="ed55e-115">リモートまたはローカルで実行中のパッケージの停止</span><span class="sxs-lookup"><span data-stu-id="ed55e-115">Stopping remote and locally running packages</span></span>  
  
-   <span data-ttu-id="ed55e-116">リモートまたはローカルで実行中のパッケージの監視</span><span class="sxs-lookup"><span data-stu-id="ed55e-116">Monitoring remote and locally running packages</span></span>  
  
-   <span data-ttu-id="ed55e-117">パッケージのインポートおよびエクスポート</span><span class="sxs-lookup"><span data-stu-id="ed55e-117">Importing and exporting packages</span></span>  
  
-   <span data-ttu-id="ed55e-118">パッケージ ストレージの管理</span><span class="sxs-lookup"><span data-stu-id="ed55e-118">Managing package storage</span></span>  
  
-   <span data-ttu-id="ed55e-119">ストレージ フォルダーのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="ed55e-119">Customizing storage folders</span></span>  
  
-   <span data-ttu-id="ed55e-120">サービス停止時の実行中のパッケージの停止</span><span class="sxs-lookup"><span data-stu-id="ed55e-120">Stopping running packages when the service is stopped</span></span>  
  
-   <span data-ttu-id="ed55e-121">Windows のイベント ログの表示</span><span class="sxs-lookup"><span data-stu-id="ed55e-121">Viewing the Windows Event log</span></span>  
  
-   <span data-ttu-id="ed55e-122">複数の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="ed55e-122">Connecting to multiple [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] servers</span></span>  
  
## <a name="startup-type-for-integration-services-service"></a><span data-ttu-id="ed55e-123">Integration Services サービスのスタートアップの種類</span><span class="sxs-lookup"><span data-stu-id="ed55e-123">Startup Type for Integration Services Service</span></span>  
 <span data-ttu-id="ed55e-124">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネントのインストール時にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ed55e-124">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is installed when you install the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ed55e-125">既定では、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが起動され、スタートアップの種類が自動に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ed55e-125">By default, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is started and the startup type of the service is set to automatic.</span></span> <span data-ttu-id="ed55e-126">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストアに格納されているパッケージを監視するには、サービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed55e-126">The service must be running to monitor the packages that are stored in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store.</span></span> <span data-ttu-id="ed55e-127">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストアは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内の msdb データベース、またはファイル システム内の指定されたフォルダーのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="ed55e-127">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store can be either the msdb database in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the designated folders in the file system.</span></span>  
  
 <span data-ttu-id="ed55e-128">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの設計と実行だけを行う場合は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ed55e-128">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is not required if you only want to design and execute [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="ed55e-129">ただし、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してパッケージを一覧表示し、監視する場合はサービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="ed55e-129">However, the service is required to list and monitor packages using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ed55e-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ed55e-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ed55e-131">Integration Services サービスのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="ed55e-131">Set the Properties of the Integration Services Service</span></span>](../set-the-properties-of-the-integration-services-service.md)  
  
-   [<span data-ttu-id="ed55e-132">Integration Services サービスのイベントを表示する</span><span class="sxs-lookup"><span data-stu-id="ed55e-132">View Events for the Integration Services Service</span></span>](../view-events-for-the-integration-services-service.md)  
  
  
