---
title: データのエクスポート (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: edae5b996c25a1b6053231ed2f69ef511b9fbfa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641039"
---
# <a name="exporting-data-master-data-services"></a><span data-ttu-id="e2381-102">データのエクスポート (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e2381-102">Exporting Data (Master Data Services)</span></span>
  <span data-ttu-id="e2381-103">サブスクリプション ビューを作成して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データをサブスクライブ システムにエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="e2381-103">You can export [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] data to subscribing systems by creating subscriptions views.</span></span> <span data-ttu-id="e2381-104">これにより、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースにパブリッシュされたデータを任意のサブスクライブ システムで表示できます。</span><span class="sxs-lookup"><span data-stu-id="e2381-104">Any subscribing system can then view the published data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="e2381-105">表示の詳細については、「[表示](../relational-databases/views/views.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2381-105">For more information about views, see [Views](../relational-databases/views/views.md).</span></span>  
  
## <a name="subscription-view-formats"></a><span data-ttu-id="e2381-106">サブスクリプション ビュー形式</span><span class="sxs-lookup"><span data-stu-id="e2381-106">Subscription View Formats</span></span>  
 <span data-ttu-id="e2381-107">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でビューを作成する場合は、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] によって提供される一連の標準ビュー形式から選択します。</span><span class="sxs-lookup"><span data-stu-id="e2381-107">When you create a view in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you choose from a set of standard view formats that [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] provides.</span></span> <span data-ttu-id="e2381-108">これらの形式を使用して、以下を表示するビューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e2381-108">You can use these formats to create views that show:</span></span>  
  
-   <span data-ttu-id="e2381-109">すべてのリーフ メンバーとその属性</span><span class="sxs-lookup"><span data-stu-id="e2381-109">All leaf members and their attributes.</span></span>  
  
-   <span data-ttu-id="e2381-110">すべての統合メンバーとその属性</span><span class="sxs-lookup"><span data-stu-id="e2381-110">All consolidated members and their attributes.</span></span>  
  
-   <span data-ttu-id="e2381-111">すべてのコレクションとその属性</span><span class="sxs-lookup"><span data-stu-id="e2381-111">All collections and their attributes.</span></span>  
  
-   <span data-ttu-id="e2381-112">コレクションに明示的に追加されたメンバー</span><span class="sxs-lookup"><span data-stu-id="e2381-112">The members explicitly added to a collection.</span></span>  
  
-   <span data-ttu-id="e2381-113">親子形式またはレベル形式の派生階層内のメンバー</span><span class="sxs-lookup"><span data-stu-id="e2381-113">The members in a derived hierarchy, in either a parent child or level format.</span></span>  
  
-   <span data-ttu-id="e2381-114">エンティティのすべての明示的階層内のメンバー (親子形式またはレベル形式)</span><span class="sxs-lookup"><span data-stu-id="e2381-114">The members in all explicit hierarchies for an entity, in either a parent child or level format.</span></span>  
  
## <a name="subscription-views-can-become-out-of-date"></a><span data-ttu-id="e2381-115">サブスクリプション ビューが古くなる可能性</span><span class="sxs-lookup"><span data-stu-id="e2381-115">Subscription Views Can Become Out-of-Date</span></span>  
 <span data-ttu-id="e2381-116">エンティティまたは階層のサブスクリプション ビューを作成後、関連付けられたモデル オブジェクトへの変更が自動的にビューに反映されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e2381-116">After you create a subscription view for an entity or hierarchy, changes to the associated model objects are not automatically reflected in the view.</span></span> <span data-ttu-id="e2381-117">モデル オブジェクトに対する変更を反映するには、必要に応じて [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] でサブスクリプション ビューを再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2381-117">You might need to regenerate a subscription view in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to reflect changes to model objects.</span></span> <span data-ttu-id="e2381-118">モデル オブジェクトが変更されると、 **[エクスポート]** ページの **[変更]** 列が **[True]** に更新されます。</span><span class="sxs-lookup"><span data-stu-id="e2381-118">The **Changed** column on the **Export** page is updated to **True** when model objects change.</span></span> <span data-ttu-id="e2381-119">**[True]** は、サブスクリプション ビューを編集して保存する必要があることを示します。この操作により、ビューが再生成されます。</span><span class="sxs-lookup"><span data-stu-id="e2381-119">**True** indicates that you should edit the subscription view and save it, which regenerates the view.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e2381-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e2381-120">Related Tasks</span></span>  
  
|<span data-ttu-id="e2381-121">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="e2381-121">Task Description</span></span>|<span data-ttu-id="e2381-122">トピック</span><span class="sxs-lookup"><span data-stu-id="e2381-122">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="e2381-123">マスター データのサブスクリプション ビューを作成する。</span><span class="sxs-lookup"><span data-stu-id="e2381-123">Create a subscription view of your master data.</span></span>|[<span data-ttu-id="e2381-124">サブスクリプションビュー &#40;マスターデータサービスを作成し&#41;</span><span class="sxs-lookup"><span data-stu-id="e2381-124">Create a Subscription View &#40;Master Data Services&#41;</span></span>](create-a-subscription-view-to-export-data-master-data-services.md)|  
|<span data-ttu-id="e2381-125">既存のサブスクリプション ビューを削除する。</span><span class="sxs-lookup"><span data-stu-id="e2381-125">Delete an existing subscription view.</span></span>|[<span data-ttu-id="e2381-126">サブスクリプション ビューを削除する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="e2381-126">Delete a Subscription View &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="e2381-127">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e2381-127">Related Content</span></span>  
  
-   [<span data-ttu-id="e2381-128">サブスクリプション ビュー形式 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="e2381-128">Subscription View Formats &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [<span data-ttu-id="e2381-129">ビュー</span><span class="sxs-lookup"><span data-stu-id="e2381-129">Views</span></span>](../relational-databases/views/views.md)  
  
  
