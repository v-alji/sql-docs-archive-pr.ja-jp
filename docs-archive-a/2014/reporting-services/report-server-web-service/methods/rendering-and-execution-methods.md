---
title: Rendering メソッドと Execution メソッド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0bc793e9a18e993989563fd3526ff12272f775c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721075"
---
# <a name="rendering-and-execution-methods"></a><span data-ttu-id="e60df-102">Rendering メソッドと Execution メソッド</span><span class="sxs-lookup"><span data-stu-id="e60df-102">Rendering and Execution Methods</span></span>
  <span data-ttu-id="e60df-103">これらのメソッドを使用して、アイテムの実行とキャッシュ、およびレポートの表示を管理します。</span><span class="sxs-lookup"><span data-stu-id="e60df-103">You can use these methods to manage item execution and caching, and report rendering.</span></span>  
  
|<span data-ttu-id="e60df-104">Method</span><span class="sxs-lookup"><span data-stu-id="e60df-104">Method</span></span>|<span data-ttu-id="e60df-105">アクション</span><span class="sxs-lookup"><span data-stu-id="e60df-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|<span data-ttu-id="e60df-106">アイテムのキャッシュを無効にします。</span><span class="sxs-lookup"><span data-stu-id="e60df-106">Invalidates the cache for an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|<span data-ttu-id="e60df-107">アイテムのキャッシュ構成と、キャッシュされたコピーの有効期限がいつ切れるかを表す設定を返します。</span><span class="sxs-lookup"><span data-stu-id="e60df-107">Returns the cache configuration for an item and the settings that describe when the cached copy of the item expires.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|<span data-ttu-id="e60df-108">個々のアイテムの実行オプションおよび関連付けられている設定を返します。</span><span class="sxs-lookup"><span data-stu-id="e60df-108">Returns the execution option and associated settings for an individual item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|<span data-ttu-id="e60df-109">サポートされている実行設定の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="e60df-109">Returns a list of supported execution settings.</span></span>|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|<span data-ttu-id="e60df-110">指定されたレポートを処理し、指定された書式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="e60df-110">Processes the specified report and renders it in a specified format.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|<span data-ttu-id="e60df-111">アイテムをキャッシュ用に構成し、キャッシュ内のアイテムの有効期限を示す設定を提供します。</span><span class="sxs-lookup"><span data-stu-id="e60df-111">Configures an item to be cached and provides settings that specify when the cached copy of the item expires.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|<span data-ttu-id="e60df-112">指定したアイテムの実行オプションおよび関連付けられた実行プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="e60df-112">Sets execution options and associated execution properties for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|<span data-ttu-id="e60df-113">指定したアイテムのアイテム実行スナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="e60df-113">Generates an item execution snapshot for a specified item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e60df-114">参照</span><span class="sxs-lookup"><span data-stu-id="e60df-114">See Also</span></span>  
 <span data-ttu-id="e60df-115">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="e60df-115">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="e60df-116">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="e60df-116">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="e60df-117">[レポート サーバー Web サービス メソッド](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="e60df-117">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="e60df-118">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e60df-118">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
