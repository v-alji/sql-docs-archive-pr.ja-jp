---
title: サブスクリプション ビュー形式 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ff1e2566-ac8f-467d-a6d9-12c3f13879b9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da2fbc6f3f4c4f577f432cb048c6f392981baf3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645706"
---
# <a name="subscription-view-formats-master-data-services"></a><span data-ttu-id="240f0-102">サブスクリプション ビュー形式 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="240f0-102">Subscription View Formats (Master Data Services)</span></span>
  <span data-ttu-id="240f0-103">選択するエンティティまたは派生階層に基づいて、次の形式をサブスクリプション ビューで使用できます。</span><span class="sxs-lookup"><span data-stu-id="240f0-103">Based on the entity or derived hierarchy you select, the following formats are available for your subscription view.</span></span>  
  
## <a name="subscription-view-formats"></a><span data-ttu-id="240f0-104">サブスクリプション ビュー形式</span><span class="sxs-lookup"><span data-stu-id="240f0-104">Subscription View Formats</span></span>  
  
|<span data-ttu-id="240f0-105">名前</span><span class="sxs-lookup"><span data-stu-id="240f0-105">Name</span></span>|<span data-ttu-id="240f0-106">説明</span><span class="sxs-lookup"><span data-stu-id="240f0-106">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="240f0-107">**リーフ メンバー**</span><span class="sxs-lookup"><span data-stu-id="240f0-107">**Leaf Members**</span></span>|<span data-ttu-id="240f0-108">リーフ メンバーとそのメンバーに関連付けられた属性値を含みます。</span><span class="sxs-lookup"><span data-stu-id="240f0-108">Contains leaf members and their associated attribute values.</span></span>|  
|<span data-ttu-id="240f0-109">**統合メンバー**</span><span class="sxs-lookup"><span data-stu-id="240f0-109">**Consolidated Members**</span></span>|<span data-ttu-id="240f0-110">統合メンバーとそのメンバーに関連付けられた属性値を含みます。</span><span class="sxs-lookup"><span data-stu-id="240f0-110">Contains consolidated members and their associated attribute values.</span></span>|  
|<span data-ttu-id="240f0-111">**コレクション メンバーシップ**</span><span class="sxs-lookup"><span data-stu-id="240f0-111">**Collection Memberships**</span></span>|<span data-ttu-id="240f0-112">コレクションのリストとコレクションに関連付けられた属性値を含みます。</span><span class="sxs-lookup"><span data-stu-id="240f0-112">Contains a list of collections and their associated attribute values.</span></span>|  
|<span data-ttu-id="240f0-113">**コレクション**</span><span class="sxs-lookup"><span data-stu-id="240f0-113">**Collections**</span></span>|<span data-ttu-id="240f0-114">コレクションのリストと各コレクションのメンバーおよび重みの値と並べ替え順序を含みます。</span><span class="sxs-lookup"><span data-stu-id="240f0-114">Contains a list of collections and the members in each, along with weight values and sort order.</span></span>|  
|<span data-ttu-id="240f0-115">**明示的親子関係**</span><span class="sxs-lookup"><span data-stu-id="240f0-115">**Explicit Parent Child**</span></span>|<span data-ttu-id="240f0-116">エンティティの明示的階層構造を親子形式で含みます。</span><span class="sxs-lookup"><span data-stu-id="240f0-116">Contains explicit hierarchy structures for an entity in a parent child format.</span></span>|  
|<span data-ttu-id="240f0-117">**明示的レベル**</span><span class="sxs-lookup"><span data-stu-id="240f0-117">**Explicit Levels**</span></span>|<span data-ttu-id="240f0-118">エンティティの明示的階層構造をレベル形式で含みます。</span><span class="sxs-lookup"><span data-stu-id="240f0-118">Contains explicit hierarchy structures for an entity in level format.</span></span>|  
|<span data-ttu-id="240f0-119">**派生親子関係 (派生階層ビュー)**</span><span class="sxs-lookup"><span data-stu-id="240f0-119">**Derived Parent Child (Derived Hierarchy View)**</span></span>|<span data-ttu-id="240f0-120">派生階層構造を親子形式で含みます。</span><span class="sxs-lookup"><span data-stu-id="240f0-120">Contains a derived hierarchy structure in parent child format.</span></span>|  
|<span data-ttu-id="240f0-121">**派生レベル (派生階層ビュー)**</span><span class="sxs-lookup"><span data-stu-id="240f0-121">**Derived Levels (Derived Hierarchy View)**</span></span>|<span data-ttu-id="240f0-122">派生階層構造をレベル形式で含みます。</span><span class="sxs-lookup"><span data-stu-id="240f0-122">Contains a derived hierarchy structure in level format.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="240f0-123">参照</span><span class="sxs-lookup"><span data-stu-id="240f0-123">See Also</span></span>  
 <span data-ttu-id="240f0-124">[データのエクスポート &#40;マスターデータサービス&#41;](overview-exporting-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="240f0-124">[Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md) </span></span>  
 [<span data-ttu-id="240f0-125">サブスクリプションビュー &#40;マスターデータサービスを作成し&#41;</span><span class="sxs-lookup"><span data-stu-id="240f0-125">Create a Subscription View &#40;Master Data Services&#41;</span></span>](create-a-subscription-view-to-export-data-master-data-services.md)  
  
  
