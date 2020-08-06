---
title: 変更の追跡 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2d3b69057b02884f41a43aa9a009ab3db937ed25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716409"
---
# <a name="change-tracking-master-data-services"></a><span data-ttu-id="ad579-102">変更の追跡 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ad579-102">Change Tracking (Master Data Services)</span></span>
  <span data-ttu-id="ad579-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、変更の追跡グループを使用して、属性の値が変化したときにアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad579-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can use change tracking groups to take action when an attribute value changes.</span></span> <span data-ttu-id="ad579-104">新しい値がどうなるかわからないけれども、変更が発生した場合にそれを知りたいときに、変更の追跡を使用します。</span><span class="sxs-lookup"><span data-stu-id="ad579-104">Use change tracking when you don't know what the new value will be, but instead want to know if any change occurred.</span></span>  
  
## <a name="configuring-change-tracking"></a><span data-ttu-id="ad579-105">変更の追跡を構成する</span><span class="sxs-lookup"><span data-stu-id="ad579-105">Configuring Change Tracking</span></span>  
 <span data-ttu-id="ad579-106">変更の追跡を構成するには、変更の追跡グループに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="ad579-106">To configure change tracking, you add an attribute to a change tracking group.</span></span> <span data-ttu-id="ad579-107">グループは、1 つまたは複数の属性を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="ad579-107">The group can contain one or many attributes.</span></span> <span data-ttu-id="ad579-108">その後、ビジネス ルールを作成し、グループ内のいずれかの属性が変化したときに実行するアクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="ad579-108">Then, you create a business rule to define the action that is taken when any of the attributes in the group change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad579-109">変更の追跡のビジネス ルールでは、ステージング (インポートされた) データが変更されるものと想定します。</span><span class="sxs-lookup"><span data-stu-id="ad579-109">Change tracking business rules consider staged (imported) data to be changed.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ad579-110">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ad579-110">Related Tasks</span></span>  
  
|<span data-ttu-id="ad579-111">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="ad579-111">Task Description</span></span>|<span data-ttu-id="ad579-112">トピック</span><span class="sxs-lookup"><span data-stu-id="ad579-112">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ad579-113">変更の追跡グループに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="ad579-113">Add attributes to a change tracking group.</span></span>|[<span data-ttu-id="ad579-114">変更の追跡グループに属性を追加する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ad579-114">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="ad579-115">属性の変更に基づいてアクションを開始するビジネス ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="ad579-115">Create a business rule that initiates actions based on attribute changes.</span></span>|[<span data-ttu-id="ad579-116">属性値の変更に基づいてアクションを開始する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ad579-116">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="ad579-117">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ad579-117">Related Content</span></span>  
  
-   [<span data-ttu-id="ad579-118">検証 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ad579-118">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [<span data-ttu-id="ad579-119">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ad579-119">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="ad579-120">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ad579-120">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
