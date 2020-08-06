---
title: 階層メンバーのアクセス許可 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81716dbd0ad08b6e92a2edb8f1d142b46bf3d24d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642143"
---
# <a name="hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="f8433-102">階層メンバーの権限 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="f8433-102">Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="f8433-103">階層メンバーの権限はオプションであり、特定のメンバーに対するユーザーのアクセスを制限する場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="f8433-103">Hierarchy member permissions are optional and should be used only when you want a user to have limited access to specific members.</span></span> <span data-ttu-id="f8433-104">**[階層メンバー]** タブで権限を割り当てていなければ、ユーザーの権限は、 **[モデル]** タブで割り当てられた権限のみに基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="f8433-104">If you do not assign permissions on the **Hierarchy Members** tab, then the user's permissions are based solely on the permissions assigned on the **Models** tab.</span></span>  
  
 <span data-ttu-id="f8433-105">階層メンバーの権限は、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザーインターフェイス (UI) の [**ユーザー/グループの権限**] 機能領域の [**階層メンバー** ] タブで割り当てられます。これらのアクセス許可によって、ユーザーが UI の [**エクスプローラー** ] 機能領域でアクセスできるメンバーが決まります。</span><span class="sxs-lookup"><span data-stu-id="f8433-105">Hierarchy member permissions are assigned in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), in the **User and Group Permissions** functional area on the **Hierarchy Members** tab. These permissions determine which members a user can access in the **Explorer** functional area of the UI.</span></span>  
  
 <span data-ttu-id="f8433-106">**[階層メンバー]** タブでは、各階層がツリー構造として表されます。</span><span class="sxs-lookup"><span data-stu-id="f8433-106">On the **Hierarchy Members** tab, each hierarchy is represented as a tree structure.</span></span> <span data-ttu-id="f8433-107">ツリー内のノードに権限を割り当てると、下位レベルで権限が明示的に割り当てられていない限り、すべての子がその権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="f8433-107">When you assign permission to a node in the tree, all children inherit that permission unless permission is explicitly assigned at a lower level.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f8433-108">階層内のいずれかのノードに権限を割り当てると、同じレベル以上にある、それ以外のノード内のメンバーはすべて暗黙的に拒否されます。</span><span class="sxs-lookup"><span data-stu-id="f8433-108">When you assign permission to a node in a hierarchy, all members in other nodes at the same level or higher are implicitly denied.</span></span>  
  
 <span data-ttu-id="f8433-109">**[エクスプローラー]** では、メンバーが表示されるすべての領域にメンバー権限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f8433-109">In **Explorer**, the member permissions are applied everywhere the member is displayed.</span></span> <span data-ttu-id="f8433-110">たとえば、**読み取り**専用権限を持つメンバーは、属しているすべてのエンティティ、階層、およびコレクションで読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="f8433-110">For example, a member with **Read-only** permission is read-only in any entities, hierarchies, and collections to which it belongs.</span></span>  
  
 <span data-ttu-id="f8433-111">階層メンバーの権限は、それらを割り当てたモデル バージョンと、そのバージョンの以降のコピーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f8433-111">Hierarchy member permissions apply to the model version you assign them to, and to any future copies of the version.</span></span> <span data-ttu-id="f8433-112">割り当てたバージョンよりも前のバージョンには適用されません。</span><span class="sxs-lookup"><span data-stu-id="f8433-112">They do not apply to versions earlier than the one you assign them to.</span></span>  
  
|<span data-ttu-id="f8433-113">権限</span><span class="sxs-lookup"><span data-stu-id="f8433-113">Permission</span></span>|<span data-ttu-id="f8433-114">説明</span><span class="sxs-lookup"><span data-stu-id="f8433-114">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="f8433-115">**読み取り専用です。**</span><span class="sxs-lookup"><span data-stu-id="f8433-115">**Read-only**</span></span>|<span data-ttu-id="f8433-116">メンバーが表示されますが、ユーザーはメンバーを変更できません。</span><span class="sxs-lookup"><span data-stu-id="f8433-116">The members are displayed but the user cannot change them.</span></span> <span data-ttu-id="f8433-117">また、メンバーが属する明示的階層またはコレクションでメンバーを移動することもできません。</span><span class="sxs-lookup"><span data-stu-id="f8433-117">The user also cannot move the members in any explicit hierarchies or collections that the members belong to.</span></span><br /><br /> <span data-ttu-id="f8433-118">注:**読み取り**専用権限を**ルート**に割り当てた場合、**ルート**の下のメンバーは読み取り専用になります。ただし、明示的階層およびコレクションでは、ユーザーはメンバーを**ルート**に移動し、新しいメンバーを**ルート**に追加できます。</span><span class="sxs-lookup"><span data-stu-id="f8433-118">Note: If you assign **Read-only** permission to **Root**, the members under **Root** are read-only; however, in explicit hierarchies and collections, the user can move members to **Root** and can add new members to **Root**.</span></span>|  
|<span data-ttu-id="f8433-119">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="f8433-119">**Update**</span></span>|<span data-ttu-id="f8433-120">メンバーが表示され、ユーザーはメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="f8433-120">The members are displayed and the user can change them.</span></span> <span data-ttu-id="f8433-121">また、メンバーが属する明示的階層またはコレクションでメンバーを移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="f8433-121">The user can also move the members in any explicit hierarchies or collections the members belong to.</span></span>|  
|<span data-ttu-id="f8433-122">**Deny**</span><span class="sxs-lookup"><span data-stu-id="f8433-122">**Deny**</span></span>|<span data-ttu-id="f8433-123">メンバーが表示されません。</span><span class="sxs-lookup"><span data-stu-id="f8433-123">The members are not displayed.</span></span>|  
  
 <span data-ttu-id="f8433-124">**[階層メンバー]** タブでは、権限を割り当ててもすぐには有効になりません。</span><span class="sxs-lookup"><span data-stu-id="f8433-124">On the **Hierarchy Members** tab, the permissions you assign do not take effect immediately.</span></span> <span data-ttu-id="f8433-125">権限が適用される頻度は、 **データベースの System Settings テーブルの** [メンバーのセキュリティ処理間隔の設定] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の値に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="f8433-125">The frequency that the permissions are applied depends on the **Member security processing interval setting** in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="f8433-126">メンバー権限を直ちに適用するには、「 [メンバー権限を直ちに適用する (マスター データ サービス)](immediately-apply-member-permissions-master-data-services.md)に追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="f8433-126">You can apply member permissions immediately by following the steps in [Immediately Apply Member Permissions &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f8433-127">階層メンバーの権限は、再帰型階層、明示的なキャップを持つ派生階層、およびレベルを非表示にした階層に割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="f8433-127">You cannot assign hierarchy member permissions to recursive hierarchies, derived hierarchies with explicit caps, and derived hierarchies with hidden levels.</span></span>  
  
## <a name="possible-overlapping-permissions"></a><span data-ttu-id="f8433-128">重複の可能性がある権限</span><span class="sxs-lookup"><span data-stu-id="f8433-128">Possible Overlapping Permissions</span></span>  
 <span data-ttu-id="f8433-129">メンバーに権限を割り当てる際、権限の重複を解決することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8433-129">When assigning permission to members, you may have to resolve overlapping permissions.</span></span>  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a><span data-ttu-id="f8433-130">1 つのメンバーが複数の階層に属している場合</span><span class="sxs-lookup"><span data-stu-id="f8433-130">When a member belongs to multiple hierarchies</span></span>  
 <span data-ttu-id="f8433-131">複数の階層に同じメンバーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f8433-131">Two or more hierarchies can contain the same member.</span></span>  
  
-   <span data-ttu-id="f8433-132">ある階層ノードに**更新**権限が割り当てられていて、別の階層ノードが**読み取り**専用に割り当てられている場合、ノード内のメンバーは**読み取り**専用になります。</span><span class="sxs-lookup"><span data-stu-id="f8433-132">If one hierarchy node is assigned **Update** permission and another is assigned **Read-only**, then the members in the node are **Read-only**.</span></span>  
  
-   <span data-ttu-id="f8433-133">1つの階層ノードに**更新**権限または**読み取り専用**権限が割り当てられていて、別のノードに [**拒否**] が割り当てられている場合、ノード内のメンバーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="f8433-133">If one hierarchy node is assigned **Update** or **Read-only** permission and another node is assigned **Deny**, then the members in the node are not displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8433-134">参照</span><span class="sxs-lookup"><span data-stu-id="f8433-134">See Also</span></span>  
 <span data-ttu-id="f8433-135">[階層メンバーの権限を割り当てる &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f8433-135">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="f8433-136">[アクセス許可の決定方法 &#40;マスターデータサービス&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f8433-136">[How Permissions Are Determined &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md) </span></span>  
 <span data-ttu-id="f8433-137">[メンバー &#40;マスターデータサービス&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f8433-137">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 <span data-ttu-id="f8433-138">[階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f8433-138">[Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="f8433-139">メンバー権限を直ちに適用する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="f8433-139">Immediately Apply Member Permissions &#40;Master Data Services&#41;</span></span>](immediately-apply-member-permissions-master-data-services.md)  
  
  
