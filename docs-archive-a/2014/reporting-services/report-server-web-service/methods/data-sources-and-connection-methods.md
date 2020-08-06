---
title: データ ソースと接続のメソッド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- data sources [Reporting Services], methods
ms.assetid: 50999b52-fc7c-4333-9fb0-d04c37a4c90f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29dd8dd1c002ab3b7d4594a4e25ec44bdb2cc8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721098"
---
# <a name="data-sources-and-connection-methods"></a><span data-ttu-id="baca5-102">データ ソースと接続のメソッド</span><span class="sxs-lookup"><span data-stu-id="baca5-102">Data Sources and Connection Methods</span></span>
  <span data-ttu-id="baca5-103">これらのメソッドを使用して、データ ソースの接続と資格情報を設定および管理できます。</span><span class="sxs-lookup"><span data-stu-id="baca5-103">You can use these methods to set and manage data source connections and credentials.</span></span>  
  
|<span data-ttu-id="baca5-104">Method</span><span class="sxs-lookup"><span data-stu-id="baca5-104">Method</span></span>|<span data-ttu-id="baca5-105">アクション</span><span class="sxs-lookup"><span data-stu-id="baca5-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataSource%2A>|<span data-ttu-id="baca5-106">レポート サーバー データベースまたは SharePoint ライブラリの新しいデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="baca5-106">Creates a new data source in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DisableDataSource%2A>|<span data-ttu-id="baca5-107">有効になっているデータ ソースを無効にします。</span><span class="sxs-lookup"><span data-stu-id="baca5-107">Disables a data source that is enabled.</span></span>|  
|<xref:ReportService2010.ReportingService2010.EnableDataSource%2A>|<span data-ttu-id="baca5-108">無効なデータ ソースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="baca5-108">Enables a data source that is disabled.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A>|<span data-ttu-id="baca5-109">データ ソースの内容を返します。</span><span class="sxs-lookup"><span data-stu-id="baca5-109">Returns the contents of a data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSourcePrompts%2A>|<span data-ttu-id="baca5-110">指定したアイテムのデータ ソース表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="baca5-110">Gets the data source prompts for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSources%2A>|<span data-ttu-id="baca5-111">カタログ内のアイテムのデータ ソースを返します。</span><span class="sxs-lookup"><span data-stu-id="baca5-111">Returns the data sources for an item in the catalog.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListDependentItems%2A>|<span data-ttu-id="baca5-112">指定したカタログ アイテムを参照するカタログ アイテムの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="baca5-112">Returns a list of catalog items that reference a specified catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptionsUsingDataSource%2A>|<span data-ttu-id="baca5-113">指定したデータ ソースに関連付けられたサブスクリプションの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="baca5-113">Returns a list of subscriptions that are associated with a given data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetDataSourceContents%2A>|<span data-ttu-id="baca5-114">データ ソースに関連付けられた接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="baca5-114">Sets the connection properties that are associated with a data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemDataSources%2A>|<span data-ttu-id="baca5-115">レポート サーバー データベースまたは SharePoint ライブラリのアイテムのデータ ソースを設定します。</span><span class="sxs-lookup"><span data-stu-id="baca5-115">Sets the data sources for an item in a report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.TestConnectForDataSourceDefinition%2A>|<span data-ttu-id="baca5-116">データ ソースへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="baca5-116">Tests the connection for a data source.</span></span> <span data-ttu-id="baca5-117">このメソッドは、データ ソースのテストを直接実行できます。</span><span class="sxs-lookup"><span data-stu-id="baca5-117">This method supports the direct testing of the data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.TestConnectForItemDataSource%2A>|<span data-ttu-id="baca5-118">データ ソースへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="baca5-118">Tests the connection for a data source.</span></span> <span data-ttu-id="baca5-119">このメソッドは、レポートまたはモデルで使用されるパブリッシュされたデータ ソースと、共有データ ソースのテストをサポートします。</span><span class="sxs-lookup"><span data-stu-id="baca5-119">This method supports the testing of published data sources that are used by reports or models and shared data sources.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="baca5-120">参照</span><span class="sxs-lookup"><span data-stu-id="baca5-120">See Also</span></span>  
 <span data-ttu-id="baca5-121">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="baca5-121">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="baca5-122">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="baca5-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="baca5-123">[レポート サーバー Web サービス メソッド](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="baca5-123">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="baca5-124">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="baca5-124">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
