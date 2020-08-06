---
title: Reporting Services のプロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61f1f50ea7a49acc616a36a4eaf1d3d5fcdf269a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713785"
---
# <a name="reporting-services-properties"></a><span data-ttu-id="d56cd-102">Reporting Services のプロパティ</span><span class="sxs-lookup"><span data-stu-id="d56cd-102">Reporting Services Properties</span></span>
  <span data-ttu-id="d56cd-103">レポート サーバーは、レポート サーバーにグローバルなシステム プロパティのセット、およびレポート サーバー データベースに格納された個別のアイテムに関連付けられているアイテム プロパティのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="d56cd-103">The report server defines a set of system properties that are global to the report server and a set of item properties that are associated with an individual item stored in the report server database.</span></span> <span data-ttu-id="d56cd-104">レポート サーバーによって定義されたプロパティは削除できず、場合によっては読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="d56cd-104">Properties defined by the report server cannot be deleted, and in some cases they are read-only.</span></span> <span data-ttu-id="d56cd-105">アプリケーションでシステム プロパティとアイテム プロパティを拡張するには、ユーザー定義プロパティをシステム プロパティとアイテム プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="d56cd-105">An application can extend system properties and item properties by adding additional user-defined properties to the system and item properties.</span></span>  
  
 <span data-ttu-id="d56cd-106">次の Web サービスメソッドは、プロパティを取得して設定し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d56cd-106">The following Web service methods retrieve and set [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] properties.</span></span>  
  
|<span data-ttu-id="d56cd-107">Method</span><span class="sxs-lookup"><span data-stu-id="d56cd-107">Method</span></span>|<span data-ttu-id="d56cd-108">アクション</span><span class="sxs-lookup"><span data-stu-id="d56cd-108">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|<span data-ttu-id="d56cd-109">レポート サーバー データベースのアイテムに関する 1 つ以上のプロパティ値を返します。</span><span class="sxs-lookup"><span data-stu-id="d56cd-109">Returns the values of one or more properties on an item in the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|<span data-ttu-id="d56cd-110">1 つ以上のシステム プロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="d56cd-110">Returns one or more system properties.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|<span data-ttu-id="d56cd-111">レポート サーバー データベースのアイテムの 1 つ以上のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d56cd-111">Sets one or more properties of an item in the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|<span data-ttu-id="d56cd-112">1 つ以上のシステム プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d56cd-112">Sets one or more system properties.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="d56cd-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d56cd-113">In This Section</span></span>  
  
|<span data-ttu-id="d56cd-114">トピック</span><span class="sxs-lookup"><span data-stu-id="d56cd-114">Topic</span></span>|<span data-ttu-id="d56cd-115">説明</span><span class="sxs-lookup"><span data-stu-id="d56cd-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d56cd-116">レポート サーバー アイテムのプロパティ</span><span class="sxs-lookup"><span data-stu-id="d56cd-116">Report Server Item Properties</span></span>](reporting-services-properties-report-server-item-properties.md)|<span data-ttu-id="d56cd-117">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のアイテム固有のプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d56cd-117">Describes the item-specific properties in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="d56cd-118">レポート サーバーのシステム プロパティ</span><span class="sxs-lookup"><span data-stu-id="d56cd-118">Report Server System Properties</span></span>](reporting-services-properties-report-server-system-properties.md)|<span data-ttu-id="d56cd-119">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のシステム固有のプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d56cd-119">Describes the system-specific properties in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d56cd-120">参照</span><span class="sxs-lookup"><span data-stu-id="d56cd-120">See Also</span></span>  
 <span data-ttu-id="d56cd-121">[Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="d56cd-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="d56cd-122">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="d56cd-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="d56cd-123">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d56cd-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
