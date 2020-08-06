---
title: サブスクリプション メソッドおよび配信メソッド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], delivering
- delivery [Reporting Services]
- methods [Reporting Services], subscription and delivery
- subscriptions [Reporting Services], about subscriptions
ms.assetid: a8637501-1817-4ccc-b07d-dd9ed5608805
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6ae92a6abd5c25b9ab1236a2b5b11429d210cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713817"
---
# <a name="subscription-and-delivery-methods"></a><span data-ttu-id="62ff5-102">サブスクリプション メソッドおよび配信メソッド</span><span class="sxs-lookup"><span data-stu-id="62ff5-102">Subscription and Delivery Methods</span></span>
  <span data-ttu-id="62ff5-103">これらのメソッドを使用して、カタログ アイテムのサブスクリプションと配信を作成および管理できます。</span><span class="sxs-lookup"><span data-stu-id="62ff5-103">You can use these methods to create and manage subscriptions and delivery of catalog items.</span></span>  
  
|<span data-ttu-id="62ff5-104">Method</span><span class="sxs-lookup"><span data-stu-id="62ff5-104">Method</span></span>|<span data-ttu-id="62ff5-105">アクション</span><span class="sxs-lookup"><span data-stu-id="62ff5-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>|<span data-ttu-id="62ff5-106">指定したアイテムのデータ ドリブン サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-106">Creates a data-driven subscription for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetDataDrivenSubscriptionProperties%2A>|<span data-ttu-id="62ff5-107">データ ドリブン サブスクリプションのプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-107">Returns the properties for a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateSubscription%2A>|<span data-ttu-id="62ff5-108">指定したアイテムのサブスクリプションをレポート サーバー データベースまたは SharePoint ライブラリに作成します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-108">Creates a subscription for the specified item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteSubscription%2A>|<span data-ttu-id="62ff5-109">サブスクリプションをレポート サーバー データベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-109">Deletes a subscription from the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSubscriptionProperties%2A>|<span data-ttu-id="62ff5-110">サブスクリプションのプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-110">Returns the properties of a subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListMySubscriptions%2A>|<span data-ttu-id="62ff5-111">指定したカタログ アイテムについて、レポート サーバーまたは SharePoint サイトの現在のユーザーによって作成されたサブスクリプションの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-111">Retrieves a list of subscriptions that have been created by the current user of the report server or SharePoint site for the given catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptions%2A>|<span data-ttu-id="62ff5-112">指定したアイテムに対して作成されているサブスクリプションの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-112">Retrieves a list of subscriptions that have been created for a given item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.PrepareQuery%2A>|<span data-ttu-id="62ff5-113">データ ドリブン サブスクリプションの配信クエリによって取得されたフィールドを含むデータセットを返します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-113">Returns a data set containing the fields retrieved by the delivery query for a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>|<span data-ttu-id="62ff5-114">データ ドリブン サブスクリプションのプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-114">Sets the values of properties of a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A>|<span data-ttu-id="62ff5-115">サブスクリプションのプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="62ff5-115">Sets the values of properties of a subscription.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62ff5-116">参照</span><span class="sxs-lookup"><span data-stu-id="62ff5-116">See Also</span></span>  
 <span data-ttu-id="62ff5-117">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="62ff5-117">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="62ff5-118">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="62ff5-118">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="62ff5-119">[レポート サーバー Web サービス メソッド](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="62ff5-119">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="62ff5-120">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="62ff5-120">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
