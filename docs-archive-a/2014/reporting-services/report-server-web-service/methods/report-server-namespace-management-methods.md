---
title: レポート サーバー名前空間管理メソッド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], managing
- management methods [Reporting Services]
- methods [Reporting Services], about methods
- methods [Reporting Services]
ms.assetid: 2aa43ce9-f51e-408a-8ce0-b40d3dd62561
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b2dc38976406aaa0fa799e7a58ee340e5449d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713825"
---
# <a name="report-server-namespace-management-methods"></a><span data-ttu-id="2d313-102">レポート サーバー名前空間管理メソッド</span><span class="sxs-lookup"><span data-stu-id="2d313-102">Report Server Namespace Management Methods</span></span>
  <span data-ttu-id="2d313-103">レポート サーバー管理 Web サービスには、レポート サーバー データベースのレポート、フォルダー、およびリソースの管理に使用できるメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d313-103">The Report Server Management Web service contains methods that you can use to manage reports, folders, and resources in the report server database.</span></span>  
  
|<span data-ttu-id="2d313-104">Method</span><span class="sxs-lookup"><span data-stu-id="2d313-104">Method</span></span>|<span data-ttu-id="2d313-105">アクション</span><span class="sxs-lookup"><span data-stu-id="2d313-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CancelJob%2A>|<span data-ttu-id="2d313-106">ジョブの実行を取り消します。</span><span class="sxs-lookup"><span data-stu-id="2d313-106">Cancels execution of a job.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateFolder%2A>|<span data-ttu-id="2d313-107">レポート サーバー データベースまたは SharePoint ライブラリにフォルダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d313-107">Adds a folder to the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A>|<span data-ttu-id="2d313-108">レポート サーバー データベースまたは SharePoint ライブラリに新しいアイテムを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d313-108">Adds a new item to a report server database or SharePoint library.</span></span> <span data-ttu-id="2d313-109">このメソッドは、アイテムの種類 `Report`、`Model`、`Dataset`、`Component`、`Resource`、および `DataSource` に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2d313-109">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<span data-ttu-id="2d313-110">M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)</span><span class="sxs-lookup"><span data-stu-id="2d313-110">M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)</span></span>|<span data-ttu-id="2d313-111">新しいレポート編集セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d313-111">Creates a new report edit session.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteItem%2A>|<span data-ttu-id="2d313-112">レポート サーバー データベースまたは SharePoint ライブラリからアイテムを削除します。</span><span class="sxs-lookup"><span data-stu-id="2d313-112">Removes an item from the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.FindItems%2A>|<span data-ttu-id="2d313-113">指定した検索条件に一致する、レポート サーバー データベースまたは SharePoint ライブラリのアイテムを返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-113">Returns the items in the report server database or SharePoint library that match the specified search criteria.</span></span>|  
|<xref:ReportService2010.ReportingService2010.FireEvent%2A>|<span data-ttu-id="2d313-114">指定したパラメーターに基づいてイベントをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="2d313-114">Triggers an event based on the supplied parameters.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>|<span data-ttu-id="2d313-115">指定した拡張機能の設定の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-115">Returns a list of settings for a given extension.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemType%2A>|<span data-ttu-id="2d313-116">レポート サーバー データベースまたは SharePoint ライブラリにアイテムが存在する場合に、アイテムの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d313-116">Retrieves the type of an item in the report server database or SharePoint library, if the item exists.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|<span data-ttu-id="2d313-117">レポート サーバー データベースまたは SharePoint ライブラリのアイテムに関する 1 つ以上のプロパティ値を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-117">Returns the values of one or more properties on an item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDefinition%2A>|<span data-ttu-id="2d313-118">アイテムの定義またはコンテンツを取得します。</span><span class="sxs-lookup"><span data-stu-id="2d313-118">Retrieves the definition or content for an item.</span></span> <span data-ttu-id="2d313-119">このメソッドは、アイテムの種類 `Report`、`Model`、`Dataset`、`Component`、`Resource`、および `DataSource` に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2d313-119">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemReferences%2A>|<span data-ttu-id="2d313-120">アイテムに関連付けられたカタログ アイテム参照の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-120">Returns a list of catalog item references associated with an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetReportServerConfigInfo%2A>|<span data-ttu-id="2d313-121">接続しているレポート サーバー インスタンス、またはスケールアウト配置内のすべてのレポート サーバー インスタンスに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-121">Returns information on the connected report server instance or all the report server instances in a scale-out deployment.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|<span data-ttu-id="2d313-122">1 つ以上のシステム プロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-122">Returns one or more system properties.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListChildren%2A>|<span data-ttu-id="2d313-123">指定したフォルダーの子の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d313-123">Gets a list of children of a specified folder.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListDatabaseCredentialRetrievalOptions%2A>|<span data-ttu-id="2d313-124">サポートされている資格情報取得オプションの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-124">Returns a list of supported credential retrieval options.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListEvents%2A>|<span data-ttu-id="2d313-125">レポート サーバー構成ファイルに表示されるイベント拡張機能の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-125">Returns a list of event extensions as they appear in the report server configuration file.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobs%2A>|<span data-ttu-id="2d313-126">レポート サーバーで実行中のジョブの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-126">Returns a list of jobs running on the report server.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExtensions%2A>|<span data-ttu-id="2d313-127">指定した拡張機能の種類に対して構成された拡張機能の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-127">Returns a list of extensions that are configured for a given extension type.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExtensionTypes%2A>|<span data-ttu-id="2d313-128">サポートされている拡張機能の種類の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-128">Returns a list of supported extension types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListItemTypes%2A>|<span data-ttu-id="2d313-129">サポートされているカタログ アイテムの種類の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-129">Returns a list of supported catalog item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobActions%2A>|<span data-ttu-id="2d313-130">サポートされているジョブの操作の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-130">Returns a list of supported job actions.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobStates%2A>|<span data-ttu-id="2d313-131">サポートされているジョブの状態の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-131">Returns a list of supported job states.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobTypes%2A>|<span data-ttu-id="2d313-132">サポートされているジョブの種類の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-132">Returns a list of supported job types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListParents%2A>|<span data-ttu-id="2d313-133">指定したアイテムの親アイテムを取得します。</span><span class="sxs-lookup"><span data-stu-id="2d313-133">Retrieves parent items for the given item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSecurityScopes%2A>|<span data-ttu-id="2d313-134">サポートされているセキュリティ スコープの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="2d313-134">Returns a list of supported security scopes.</span></span>|  
|<xref:ReportService2010.ReportingService2010.Logoff%2A>|<span data-ttu-id="2d313-135">Web サービス要求を行っている現在のユーザーをログアウトします。</span><span class="sxs-lookup"><span data-stu-id="2d313-135">Logs out the current user making Web service requests.</span></span> <span data-ttu-id="2d313-136">このメソッドは、ネイティブ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="2d313-136">This method only applies to native mode.</span></span>|  
|<xref:ReportService2010.ReportingService2010.LogonUser%2A>|<span data-ttu-id="2d313-137">ユーザーのログオンを処理し、レポート サーバー Web サービスへのユーザーの要求を認証します。</span><span class="sxs-lookup"><span data-stu-id="2d313-137">Logs on a user and authenticates a user request to the Report Server Web service.</span></span> <span data-ttu-id="2d313-138">このメソッドは、ネイティブ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="2d313-138">This method only applies to native mode.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemReferences%2A>|<span data-ttu-id="2d313-139">アイテムに関連付けられたカタログ アイテムを設定します。</span><span class="sxs-lookup"><span data-stu-id="2d313-139">Sets the catalog items associated with an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.MoveItem%2A>|<span data-ttu-id="2d313-140">アイテムの移動や名前の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="2d313-140">Moves and/or renames an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|<span data-ttu-id="2d313-141">アイテムの 1 つ以上のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2d313-141">Sets one or more properties of an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemDefinition%2A>|<span data-ttu-id="2d313-142">指定したアイテムの定義またはコンテンツを設定します。</span><span class="sxs-lookup"><span data-stu-id="2d313-142">Sets the definition or content for a specified item.</span></span> <span data-ttu-id="2d313-143">このメソッドは、アイテムの種類 `Report`、`Model`、`Dataset`、`Component`、`Resource`、および `DataSource` に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2d313-143">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|<span data-ttu-id="2d313-144">レポート サーバーまたは SharePoint ファームの 1 つ以上のシステム プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2d313-144">Sets one or more system properties in the report server or SharePoint farm.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ValidateExtensionSettings%2A>|<span data-ttu-id="2d313-145">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 拡張機能の設定を検証します。</span><span class="sxs-lookup"><span data-stu-id="2d313-145">Validates [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d313-146">参照</span><span class="sxs-lookup"><span data-stu-id="2d313-146">See Also</span></span>  
 <span data-ttu-id="2d313-147">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="2d313-147">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="2d313-148">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="2d313-148">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="2d313-149">[レポート サーバー Web サービス メソッド](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="2d313-149">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="2d313-150">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="2d313-150">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
