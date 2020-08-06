---
title: レポート サーバー Web サービスのメソッド | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 37d0031ebfb4ec6d31da6aad9a8842c0623cb75b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632887"
---
# <a name="report-server-web-service-methods"></a><span data-ttu-id="b9c47-102">レポート サーバー Web サービスのメソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-102">Report Server Web Service Methods</span></span>
  <span data-ttu-id="b9c47-103">レポート サーバー Web サービスには、コンポーネントの機能に基づいた、複数のカテゴリのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9c47-103">The Report Server Web services include several categories of methods that are based on component features.</span></span> <span data-ttu-id="b9c47-104">これらのメソッドは、Web サービスのいくつかのエンドポイントを介して (レポート管理用に 3 つ、レポート実行用に 1 つ)、<xref:ReportService2010.ReportingService2010> クラスおよび <xref:ReportExecution2005.ReportExecutionService> クラスのメンバーとして提供されます。</span><span class="sxs-lookup"><span data-stu-id="b9c47-104">These methods are provided through several Web service endpoints (three for report management and one for report execution) which are exposed as members of the <xref:ReportService2010.ReportingService2010> and <xref:ReportExecution2005.ReportExecutionService> classes.</span></span> <span data-ttu-id="b9c47-105">これらのクラスは、SDK に含まれている wsdl.exe などのプロキシクラスツールを使用して生成でき [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b9c47-105">These classes can be generated through a proxy class tool such as wsdl.exe, which is included with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.</span></span> <span data-ttu-id="b9c47-106">Report Server Web サービスと [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の詳細については、「[Web サービスと、.NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9c47-106">For more information about the Report Server Web services and the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], see [Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
## <a name="endpoints-and-methods"></a><span data-ttu-id="b9c47-107">エンドポイントおよびメソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-107">Endpoints and Methods</span></span>  
 <span data-ttu-id="b9c47-108">次の表に、レポート サーバー Web サービスのエンドポイントと、<xref:ReportService2010.ReportingService2010> エンドポイントにより提供されるメソッドのカテゴリを示します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-108">The following table lists the endpoints of the Report Server Web service, and the categories of methods provided by the <xref:ReportService2010.ReportingService2010> endpoint.</span></span> <span data-ttu-id="b9c47-109">他のエンドポイントで利用可能なメソッドの詳細については、「[テクニカル リファレンス (SSRS)](../../technical-reference-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9c47-109">For information on the methods available in the other endpoints, see [Technical Reference &#40;SSRS&#41;](../../technical-reference-ssrs.md).</span></span>  
  
|<span data-ttu-id="b9c47-110">トピック</span><span class="sxs-lookup"><span data-stu-id="b9c47-110">Topic</span></span>|<span data-ttu-id="b9c47-111">説明</span><span class="sxs-lookup"><span data-stu-id="b9c47-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b9c47-112">レポート サーバー Web サービスのエンドポイント</span><span class="sxs-lookup"><span data-stu-id="b9c47-112">Report Server Web Service Endpoints</span></span>](report-server-web-service-endpoints.md)|<span data-ttu-id="b9c47-113">レポート サーバー Web サービスの管理用エンドポイントと実行用エンドポイントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-113">Describes the management and execution endpoints of the Report Server Web service.</span></span>|  
|[<span data-ttu-id="b9c47-114">レポート サーバー名前空間管理メソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-114">Report Server Namespace Management Methods</span></span>](report-server-namespace-management-methods.md)|<span data-ttu-id="b9c47-115">レポート サーバー データベースの管理に使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-115">Describes methods that you can use to manage the report server database.</span></span> <span data-ttu-id="b9c47-116">フォルダーとリソースの管理、アイテム プロパティの設定を行えます。</span><span class="sxs-lookup"><span data-stu-id="b9c47-116">Specifically you can manage folders and resources and set item properties.</span></span>|  
|[<span data-ttu-id="b9c47-117">承認方法</span><span class="sxs-lookup"><span data-stu-id="b9c47-117">Authorization Methods</span></span>](authorization-methods.md)|<span data-ttu-id="b9c47-118">タスク、ロール、およびポリシーの管理に使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-118">Describes methods that you can use to manage tasks, roles, and policies.</span></span>|  
|[<span data-ttu-id="b9c47-119">データ ソースと接続のメソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-119">Data Sources and Connection Methods</span></span>](data-sources-and-connection-methods.md)|<span data-ttu-id="b9c47-120">レポートのデータ ソース接続や資格情報の設定および管理に使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-120">Describes methods that you can use to set and manage data source connection and credential information for reports.</span></span>|  
|[<span data-ttu-id="b9c47-121">レポート パラメーターのメソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-121">Report Parameters Methods</span></span>](report-parameters-methods.md)|<span data-ttu-id="b9c47-122">レポートのパラメーターを設定および取得するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-122">Describes methods that you can use to set and retrieve parameters for reports.</span></span>|  
|[<span data-ttu-id="b9c47-123">モデルのメソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-123">Model Methods</span></span>](../report-server-web-service.md)|<span data-ttu-id="b9c47-124">モデルの管理に使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-124">Describes methods that you can use to manage models.</span></span>|  
|[<span data-ttu-id="b9c47-125">Rendering メソッドと Execution メソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-125">Rendering and Execution Methods</span></span>](rendering-and-execution-methods.md)|<span data-ttu-id="b9c47-126">レポートの実行、表示、およびキャッシュを管理するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-126">Describes methods that you can use to manage report execution, rendering, and caching.</span></span>|  
|[<span data-ttu-id="b9c47-127">レポート履歴メソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-127">Report History Methods</span></span>](report-history-methods.md)|<span data-ttu-id="b9c47-128">レポート履歴スナップショットを作成および管理するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-128">Describes methods that you can use to create and manage report history snapshots.</span></span>|  
|[<span data-ttu-id="b9c47-129">メソッドのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="b9c47-129">Scheduling Methods</span></span>](scheduling-methods.md)|<span data-ttu-id="b9c47-130">レポート サーバーが使用する共有スケジュールとキャッシュ更新計画を作成および管理するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-130">Describes methods that you can use to create and manage shared schedules and cache refresh plans that are used by the report server.</span></span>|  
|[<span data-ttu-id="b9c47-131">サブスクリプション メソッドおよび配信メソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-131">Subscription and Delivery Methods</span></span>](subscription-and-delivery-methods.md)|<span data-ttu-id="b9c47-132">サブスクリプションとレポート配信を作成および管理するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-132">Describes methods that you can use to create and manage subscriptions and report delivery.</span></span>|  
|[<span data-ttu-id="b9c47-133">リンク レポートのメソッド</span><span class="sxs-lookup"><span data-stu-id="b9c47-133">Linked Reports Methods</span></span>](linked-reports-methods.md)|<span data-ttu-id="b9c47-134">リンク レポートを作成および管理するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9c47-134">Describes methods that you can use to create and manage linked reports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9c47-135">参照</span><span class="sxs-lookup"><span data-stu-id="b9c47-135">See Also</span></span>  
 <span data-ttu-id="b9c47-136">[SOAP API へのアクセス](../accessing-the-soap-api.md) </span><span class="sxs-lookup"><span data-stu-id="b9c47-136">[Accessing the SOAP API](../accessing-the-soap-api.md) </span></span>  
 <span data-ttu-id="b9c47-137">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="b9c47-137">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="b9c47-138">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="b9c47-138">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="b9c47-139">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b9c47-139">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
