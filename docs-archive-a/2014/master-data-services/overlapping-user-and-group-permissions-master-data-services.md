---
title: ユーザー アクセス許可とグループ アクセス許可の重複 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7044bf6260170cbc598719ec204ddb6f861f6301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714461"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a><span data-ttu-id="05739-102">ユーザー権限とグループ権限の重複 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="05739-102">Overlapping User and Group Permissions (Master Data Services)</span></span>
  <span data-ttu-id="05739-103">ユーザーの権限は、次の権限に基づきます。</span><span class="sxs-lookup"><span data-stu-id="05739-103">A user's permissions are based on:</span></span>  
  
-   <span data-ttu-id="05739-104">グループのメンバーシップの権限</span><span class="sxs-lookup"><span data-stu-id="05739-104">Permissions from group memberships.</span></span>  
  
-   <span data-ttu-id="05739-105">ユーザーに明示的に割り当てられた権限</span><span class="sxs-lookup"><span data-stu-id="05739-105">Permissions assigned explicitly to the user.</span></span>  
  
 <span data-ttu-id="05739-106">ユーザーが複数のグループのメンバーであり、それらのグループがマスター データ マネージャーへのアクセス権を持っている場合、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="05739-106">If a user is a member of multiple groups, and those groups have access to Master Data Manager, the following rules apply:</span></span>  
  
-   <span data-ttu-id="05739-107">**拒否** が他のどの権限をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="05739-107">**Deny** overrides all other permissions.</span></span>  
  
-   <span data-ttu-id="05739-108">**更新\*\*\*\*は読み取り専用に**上書きされます。</span><span class="sxs-lookup"><span data-stu-id="05739-108">**Update** overrides **Read-only**.</span></span>  
  
 <span data-ttu-id="05739-109">上記のルールは、 **[モデル]** タブと **[階層メンバー]** タブに適用されます。</span><span class="sxs-lookup"><span data-stu-id="05739-109">These rules apply to both the **Models** and **Hierarchy Members** tabs.</span></span> <span data-ttu-id="05739-110">権限は、各タブで解決された後で組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="05739-110">Permissions are resolved for each tab and then combined.</span></span> <span data-ttu-id="05739-111">詳細については、「 [権限の決定方法 (マスター データ サービス)](how-permissions-are-determined-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05739-111">For more information, see [How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05739-112">ユーザー権限とグループ権限の重複がどのように解決されているかは、ユーザー インターフェイスに表示できます。</span><span class="sxs-lookup"><span data-stu-id="05739-112">You can view the resolution of user and group overlapping permissions in the user interface.</span></span> <span data-ttu-id="05739-113">**[モデル]** タブと **[階層メンバー]** タブにはドロップダウン リストがあり、そこから **[有効]** をクリックして有効な権限を表示できます。</span><span class="sxs-lookup"><span data-stu-id="05739-113">Both the **Models** and **Hierarchy Members** tab have a drop-down list from which you can choose **Effective** to view effective permissions.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="05739-114">例 1</span><span class="sxs-lookup"><span data-stu-id="05739-114">Example 1</span></span>  
 <span data-ttu-id="05739-115">![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")</span><span class="sxs-lookup"><span data-stu-id="05739-115">![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")</span></span>  
  
 <span data-ttu-id="05739-116">ユーザーがグループ 1 とグループ 2 に属しています。</span><span class="sxs-lookup"><span data-stu-id="05739-116">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="05739-117">ユーザーには、Product エンティティに対する**読み取り**専用権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-117">The user has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="05739-118">グループ 1 には、Product エンティティに対する **更新** 権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-118">Group 1 has **Update** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="05739-119">グループ2には、Product エンティティに対する**読み取り**専用権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-119">Group 2 has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="05739-120">結果: ユーザーの有効な権限は、Product エンティティに対する **更新** 権限となります。</span><span class="sxs-lookup"><span data-stu-id="05739-120">Result: The user's effective permission is **Update** to the Product entity.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="05739-121">例 2</span><span class="sxs-lookup"><span data-stu-id="05739-121">Example 2</span></span>  
 <span data-ttu-id="05739-122">![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")</span><span class="sxs-lookup"><span data-stu-id="05739-122">![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")</span></span>  
  
 <span data-ttu-id="05739-123">ユーザーがグループ 1 とグループ 2 に属しています。</span><span class="sxs-lookup"><span data-stu-id="05739-123">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="05739-124">ユーザーには、Product エンティティに対する**読み取り**専用権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-124">The user has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="05739-125">グループ 1 には、Product エンティティに対する **更新** 権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-125">Group 1 has **Update** permission to Product entity.</span></span>  
  
 <span data-ttu-id="05739-126">グループ 2 には、Product エンティティに対する **拒否** 権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-126">Group 2 has **Deny** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="05739-127">結果: ユーザーの有効な権限は、Product エンティティに対する **拒否** 権限となります。</span><span class="sxs-lookup"><span data-stu-id="05739-127">Result: The user's effective permission is **Deny** to the Product entity.</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="05739-128">例 3</span><span class="sxs-lookup"><span data-stu-id="05739-128">Example 3</span></span>  
 <span data-ttu-id="05739-129">![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")</span><span class="sxs-lookup"><span data-stu-id="05739-129">![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")</span></span>  
  
 <span data-ttu-id="05739-130">ユーザーがグループ 1 とグループ 2 に属しています。</span><span class="sxs-lookup"><span data-stu-id="05739-130">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="05739-131">ユーザーには、階層ノードのメンバーのグループに対する **更新** 権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-131">The user has **Update** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="05739-132">グループ1には、階層ノードのメンバーのグループに対する**読み取り**専用権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-132">Group 1 has **Read-only** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="05739-133">グループ2には、階層ノードのメンバーのグループに対する**読み取り**専用権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="05739-133">Group 2 has **Read-only** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="05739-134">結果: ユーザーの有効な権限は、メンバーに対する **更新** 権限となります。</span><span class="sxs-lookup"><span data-stu-id="05739-134">Result: The user's effective permission is **Update** to the members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05739-135">参照</span><span class="sxs-lookup"><span data-stu-id="05739-135">See Also</span></span>  
 <span data-ttu-id="05739-136">[アクセス許可の決定方法 &#40;マスターデータサービス&#41;](how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="05739-136">[How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span></span>  
 [<span data-ttu-id="05739-137">モデル アクセス許可とメンバー アクセス許可の重複 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="05739-137">Overlapping Model and Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
