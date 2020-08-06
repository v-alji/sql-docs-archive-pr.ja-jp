---
title: メソッドのスケジュール設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 735da4f22d523fd40dd031f55e203fa9a4204f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632886"
---
# <a name="scheduling-methods"></a><span data-ttu-id="77bfb-102">メソッドのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="77bfb-102">Scheduling Methods</span></span>
  <span data-ttu-id="77bfb-103">これらのメソッドを使用して、レポート サーバーが利用する、レポートの実行と配信のための共有スケジュールとキャッシュ更新計画を作成および管理できます。</span><span class="sxs-lookup"><span data-stu-id="77bfb-103">You can use these methods to create and manage shared schedules for report execution and delivery, and to cache refresh plans utilized by the report server.</span></span>  
  
|<span data-ttu-id="77bfb-104">Method</span><span class="sxs-lookup"><span data-stu-id="77bfb-104">Method</span></span>|<span data-ttu-id="77bfb-105">アクション</span><span class="sxs-lookup"><span data-stu-id="77bfb-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|<span data-ttu-id="77bfb-106">アイテムのキャッシュ更新プランを作成します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-106">Creates a cache refresh plan for an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|<span data-ttu-id="77bfb-107">新しい共有スケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-107">Creates a new shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|<span data-ttu-id="77bfb-108">キャッシュ更新プランを削除します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-108">Deletes a cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|<span data-ttu-id="77bfb-109">特定のスケジュール ID に基づいて共有スケジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-109">Deletes a shared schedule based on a specific schedule ID.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|<span data-ttu-id="77bfb-110">指定したキャッシュ更新プランのプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-110">Returns the properties of the specified cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|<span data-ttu-id="77bfb-111">共有スケジュールのプロパティ値を返します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-111">Returns the values of properties of a shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|<span data-ttu-id="77bfb-112">カタログ アイテムに関連付けられたキャッシュ更新プランの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-112">Returns a list of the cache refresh plans associated with a catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|<span data-ttu-id="77bfb-113">共有スケジュールに関連付けられたアイテムの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-113">Returns a list of items that are associated with a shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|<span data-ttu-id="77bfb-114">レポート サーバーまたは SharePoint サイトにおけるすべての共有スケジュールの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-114">Returns a list of all shared schedules at the report server or the SharePoint site.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|<span data-ttu-id="77bfb-115">サポートされているスケジュールの状態の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-115">Returns a list of supported schedule states.</span></span>|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|<span data-ttu-id="77bfb-116">指定したスケジュールの実行を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-116">Pauses the execution of a given schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|<span data-ttu-id="77bfb-117">一時停止している共有スケジュールを再開します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-117">Resumes a shared schedule that has been paused.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|<span data-ttu-id="77bfb-118">キャッシュ更新計画のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-118">Sets the properties of a cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|<span data-ttu-id="77bfb-119">共有スケジュールのプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="77bfb-119">Sets the value of properties of a shared schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77bfb-120">参照</span><span class="sxs-lookup"><span data-stu-id="77bfb-120">See Also</span></span>  
 <span data-ttu-id="77bfb-121">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="77bfb-121">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="77bfb-122">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="77bfb-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="77bfb-123">[レポート サーバー Web サービス メソッド](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="77bfb-123">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="77bfb-124">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="77bfb-124">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
