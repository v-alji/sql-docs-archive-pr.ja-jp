---
title: PowerPivot データ更新 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f7d5ed5c2f8882cbc0c47a1c711748d26e0193c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641292"
---
# <a name="powerpivot-data-refresh"></a><span data-ttu-id="c28d4-102">PowerPivot のデータ更新</span><span class="sxs-lookup"><span data-stu-id="c28d4-102">PowerPivot Data Refresh</span></span>
  <span data-ttu-id="c28d4-103">PowerPivot データを含むブックを作成したら、最初にブックを作成するときに使用したソースから更新情報を取得するクエリまたはコマンドを再実行して、定期的にデータを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="c28d4-103">After you create a workbook that contains PowerPivot data, you might want to periodically refresh the data by rerunning a query or command to get updated information from the sources you used originally to create the workbook.</span></span> <span data-ttu-id="c28d4-104">このプロセスは `data refresh` と呼ばれます。データ更新は、[!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] で要求時に実行したり、SharePoint ファーム内のアプリケーション サーバーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロセスとして実行される定期的な操作として実行したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c28d4-104">This process is called `data refresh`, and you can refresh data on demand in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], or as a scheduled operation that runs as an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] process on an application server in a SharePoint farm.</span></span> <span data-ttu-id="c28d4-105">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c28d4-105">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c28d4-106">SharePoint 2010 での PowerPivot データ更新</span><span class="sxs-lookup"><span data-stu-id="c28d4-106">PowerPivot Data Refresh with SharePoint 2010</span></span>](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [<span data-ttu-id="c28d4-107">PowerPivot 自動データ更新アカウント &#40;PowerPivot for SharePoint を構成し&#41;</span><span class="sxs-lookup"><span data-stu-id="c28d4-107">Configure the PowerPivot Unattended Data Refresh Account &#40;PowerPivot for SharePoint&#41;</span></span>](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [<span data-ttu-id="c28d4-108">PowerPivot データ更新用の保存された資格情報を構成する &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="c28d4-108">Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [<span data-ttu-id="c28d4-109">データ更新 &#40;PowerPivot for SharePoint をスケジュールする&#41;</span><span class="sxs-lookup"><span data-stu-id="c28d4-109">Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [<span data-ttu-id="c28d4-110">データ更新履歴の表示 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="c28d4-110">View Data Refresh History &#40;PowerPivot for SharePoint&#41;</span></span>](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="c28d4-111">および SharePoint Server 2013 の Excel Services では、PowerPivot データ モデルのデータ更新に異なるアーキテクチャを使用しています。</span><span class="sxs-lookup"><span data-stu-id="c28d4-111">and SharePoint Server 2013 Excel Services use a different architecture for data refresh of PowerPivot data models.</span></span> <span data-ttu-id="c28d4-112">SharePoint 2013 でサポートされているアーキテクチャでは、PowerPivot データ モデルを読み込むための主要なコンポーネントとして Excel Services が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c28d4-112">The SharePoint 2013 supported architecture utilizes Excel Services as the primary component to load PowerPivot data models.</span></span> <span data-ttu-id="c28d4-113">以前に使用されていたデータ更新のアーキテクチャでは、データ モデルを読み込むために、SharePoint モードで PowerPivot System サービスおよび [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を実行しているサーバーが使用されていました。</span><span class="sxs-lookup"><span data-stu-id="c28d4-113">The previous data refresh architecture used relied on a server running PowerPivot System Service and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in SharePoint mode to load data models.</span></span> <span data-ttu-id="c28d4-114">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="c28d4-114">For more information, see the following:</span></span>  
> 
>  -   [<span data-ttu-id="c28d4-115">SharePoint 2013 での PowerPivot データ更新</span><span class="sxs-lookup"><span data-stu-id="c28d4-115">PowerPivot Data Refresh with SharePoint 2013</span></span>](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [<span data-ttu-id="c28d4-116">SharePoint 2013&#41;&#40;のブックのアップグレードと定期データ更新</span><span class="sxs-lookup"><span data-stu-id="c28d4-116">Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;</span></span>](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
