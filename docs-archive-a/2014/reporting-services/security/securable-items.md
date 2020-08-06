---
title: セキュリティ保護可能なアイテム | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- securable items [Reporting Services]
- roles [Reporting Services], securable items
- security [Reporting Services], securable items listed
- role-based security [Reporting Services], securable items
ms.assetid: 27f58d4c-5c7b-4947-af5b-0f1fa60faf5f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f2f9fa5108831cb6c469710a71439bf3cfb6194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643698"
---
# <a name="securable-items"></a><span data-ttu-id="d02ee-102">セキュリティ保護可能なアイテム</span><span class="sxs-lookup"><span data-stu-id="d02ee-102">Securable Items</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d02ee-103">では、レポート サーバーに保存されているアイテムへのアクセス制御に、ロールベースのセキュリティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-103">uses role-based security to control access to items that are stored on a report server.</span></span> <span data-ttu-id="d02ee-104">レポート サーバーへのユーザー アクセスを許可する場合は、通常次の場所でロールの割り当てのペアを作成します。</span><span class="sxs-lookup"><span data-stu-id="d02ee-104">When you grant a user access to a report server, you typically do so by creating a pair of role assignments:</span></span>  
  
-   <span data-ttu-id="d02ee-105">サイト レベル</span><span class="sxs-lookup"><span data-stu-id="d02ee-105">At the site level</span></span>  
  
-   <span data-ttu-id="d02ee-106">[ホーム] (レポート サーバーのフォルダー階層のルート ノード)</span><span class="sxs-lookup"><span data-stu-id="d02ee-106">On Home, which is the root node of the report server folder hierarchy</span></span>  
  
 <span data-ttu-id="d02ee-107">セキュリティは、レポート サーバーのフォルダー階層内で継承されます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-107">Security is inherited within the report server folder hierarchy.</span></span> <span data-ttu-id="d02ee-108">サイト レベルと [ホーム] フォルダーでロールの割り当てを作成すると、レポート サーバーのすべてのアイテムおよび操作に拡張される権限の継承が設定されます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-108">Creating role assignments at the site level and on the Home folder sets permission inheritance that extends to all items and operations on a report server.</span></span>  
  
 <span data-ttu-id="d02ee-109">個別のアイテムにセキュリティを定義することで、権限の継承をオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-109">You can override permission inheritance by defining security for individual items.</span></span> <span data-ttu-id="d02ee-110">個別に保護できるのは、次のアイテムです。</span><span class="sxs-lookup"><span data-stu-id="d02ee-110">Items that you can secure individually include:</span></span>  
  
-   <span data-ttu-id="d02ee-111">Folders</span><span class="sxs-lookup"><span data-stu-id="d02ee-111">Folders</span></span>  
  
-   <span data-ttu-id="d02ee-112">Reports</span><span class="sxs-lookup"><span data-stu-id="d02ee-112">Reports</span></span>  
  
-   <span data-ttu-id="d02ee-113">レポート モデル</span><span class="sxs-lookup"><span data-stu-id="d02ee-113">Report models</span></span>  
  
-   <span data-ttu-id="d02ee-114">リソース</span><span class="sxs-lookup"><span data-stu-id="d02ee-114">Resources</span></span>  
  
-   <span data-ttu-id="d02ee-115">共有データ ソース</span><span class="sxs-lookup"><span data-stu-id="d02ee-115">Shared data sources</span></span>  
  
-   <span data-ttu-id="d02ee-116">共有データセット</span><span class="sxs-lookup"><span data-stu-id="d02ee-116">Shared datasets</span></span>  
  
 <span data-ttu-id="d02ee-117">スケジュールやサブスクリプションなどのその他の構成要素は、明示的にセキュリティ保護されません。</span><span class="sxs-lookup"><span data-stu-id="d02ee-117">Other constructs, such as schedules and subscriptions, are not explicitly secured.</span></span> <span data-ttu-id="d02ee-118">スケジュールとサブスクリプションは、レポートのセキュリティの中で運用されます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-118">Schedules and subscriptions operate within the security of a report.</span></span>  
  
## <a name="item-descriptions"></a><span data-ttu-id="d02ee-119">アイテムの説明</span><span class="sxs-lookup"><span data-stu-id="d02ee-119">Item Descriptions</span></span>  
 <span data-ttu-id="d02ee-120">セキュリティ保護可能なアイテムの一覧と、その特性の説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d02ee-120">The following table lists securable items and describes their characteristics.</span></span>  
  
|<span data-ttu-id="d02ee-121">アイテム</span><span class="sxs-lookup"><span data-stu-id="d02ee-121">Item</span></span>|<span data-ttu-id="d02ee-122">特性</span><span class="sxs-lookup"><span data-stu-id="d02ee-122">Characteristics</span></span>|  
|----------|---------------------|  
|<span data-ttu-id="d02ee-123">Folders</span><span class="sxs-lookup"><span data-stu-id="d02ee-123">Folders</span></span>|<span data-ttu-id="d02ee-124">フォルダーのセキュリティは、フォルダー自体と内部のアイテムに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-124">Folder security applies to the folder itself and the items it contains.</span></span> <span data-ttu-id="d02ee-125">[ホーム] フォルダーは、フォルダー階層のルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="d02ee-125">The Home folder is the root node of the folder hierarchy.</span></span> <span data-ttu-id="d02ee-126">このフォルダーに対して設定したセキュリティは、そのフォルダー階層にあるすべての下位フォルダー、レポート、リソース、および共有データ ソースに対するセキュリティの初期設定になります。</span><span class="sxs-lookup"><span data-stu-id="d02ee-126">Security that you set for this folder establishes the initial security settings for all subordinate folders, reports, resources, and shared data sources in the folder hierarchy.</span></span> <span data-ttu-id="d02ee-127">詳細については、「 [フォルダーをセキュリティで保護する](secure-folders.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d02ee-127">For more information, see [Secure Folders](secure-folders.md).</span></span><br /><br /> <span data-ttu-id="d02ee-128">[個人用レポート] は特別な用途を持つフォルダーで、専用のロールに基づく黙示的なロールの割り当てによってセキュリティで保護されています。</span><span class="sxs-lookup"><span data-stu-id="d02ee-128">My Reports is a special-purpose folder that is secured through an implied role assignment based on a dedicated role.</span></span> <span data-ttu-id="d02ee-129">詳細については、「 [個人用レポートをセキュリティで保護する](secure-my-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d02ee-129">For more information, see [Secure My Reports](secure-my-reports.md).</span></span>|  
|<span data-ttu-id="d02ee-130">Reports</span><span class="sxs-lookup"><span data-stu-id="d02ee-130">Reports</span></span>|<span data-ttu-id="d02ee-131">レポートおよびリンク レポートをセキュリティで保護して、ユーザーが実行できるアクションの範囲 (指定したレポートのプロパティを変更するなど) を制御することができます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-131">Reports and linked reports can be secured to control the range of actions that users can perform, such as changing the properties of a given report.</span></span><br /><br /> <span data-ttu-id="d02ee-132">レポート履歴は、履歴に含まれているレポートによりセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-132">Report history is secured through the report that contains the history.</span></span> <span data-ttu-id="d02ee-133">レポート履歴のスナップショットを個別にセキュリティで保護することはできません。</span><span class="sxs-lookup"><span data-stu-id="d02ee-133">You cannot secure individual snapshots within report history.</span></span><br /><br /> <span data-ttu-id="d02ee-134">レポートのセキュリティの詳細については、「 [レポートとリソースの保護](secure-reports-and-resources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d02ee-134">For more information about report security, see [Secure Reports and Resources](secure-reports-and-resources.md).</span></span>|  
|<span data-ttu-id="d02ee-135">レポート モデル</span><span class="sxs-lookup"><span data-stu-id="d02ee-135">Report models</span></span>|<span data-ttu-id="d02ee-136">レポート モデル全体またはその一部に対してロールの割り当てを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-136">You can specify role assignment on all or part of a report model.</span></span> <span data-ttu-id="d02ee-137">レポート モデルは非常に広範囲にわたることがあるため、そのような場合は、機密データに関連するモデル アイテムのみをセキュリティで保護できます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-137">Because report models can be quite extensive, you might want to secure the model items that map to confidential data.</span></span>|  
|<span data-ttu-id="d02ee-138">リソース</span><span class="sxs-lookup"><span data-stu-id="d02ee-138">Resources</span></span>|<span data-ttu-id="d02ee-139">リソースをセキュリティで保護して、リソース自体とプロパティへのアクセスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-139">Resources can be secured to control access to the resource itself and its properties.</span></span><br /><br /> <span data-ttu-id="d02ee-140">スタンドアロン リソースのみ、独立したアイテムとしてセキュリティで保護できます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-140">Only stand-alone resources can be secured as separate items.</span></span> <span data-ttu-id="d02ee-141">レポートに埋め込まれているリソースは、レポートと別にセキュリティで保護できません。</span><span class="sxs-lookup"><span data-stu-id="d02ee-141">Resources that are embedded within a report cannot be secured separately from that report.</span></span><br /><br /> <span data-ttu-id="d02ee-142">レポートのセキュリティの詳細については、「 [レポートとリソースの保護](secure-reports-and-resources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d02ee-142">For more information about resource security, see [Secure Reports and Resources](secure-reports-and-resources.md).</span></span>|  
|<span data-ttu-id="d02ee-143">共有データ ソース</span><span class="sxs-lookup"><span data-stu-id="d02ee-143">Shared data sources</span></span>|<span data-ttu-id="d02ee-144">共有データ ソースをセキュリティで保護して、共有データ ソース アイテムおよびそのプロパティ ページへのアクセスを制限することができます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-144">Shared data sources can be secured to limit access to the item and its property pages.</span></span> <span data-ttu-id="d02ee-145">詳細については、「 [Secure Shared Data Source Items](secure-shared-data-source-items.md)」(共有データ ソース アイテムをセキュリティで保護する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d02ee-145">For more information, see [Secure Shared Data Source Items](secure-shared-data-source-items.md).</span></span>|  
|<span data-ttu-id="d02ee-146">共有データセット</span><span class="sxs-lookup"><span data-stu-id="d02ee-146">Shared datasets</span></span>|<span data-ttu-id="d02ee-147">共有データセットをセキュリティで保護し、ユーザーが実行できるアクションの範囲 (定義の表示や変更、特定の共有データセットのプロパティの変更など) を制御できます。</span><span class="sxs-lookup"><span data-stu-id="d02ee-147">Shared datasets can be secured to control the range of actions that users can perform, such as viewing or changing the definition, or changing the properties of a given shared dataset.</span></span><br /><br /> <span data-ttu-id="d02ee-148">詳細については、「 [共有データセット アイテムをセキュリティで保護する](secure-shared-dataset-items.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d02ee-148">For more information, see [Secure Shared Dataset Items](secure-shared-dataset-items.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d02ee-149">参照</span><span class="sxs-lookup"><span data-stu-id="d02ee-149">See Also</span></span>  
 <span data-ttu-id="d02ee-150">[ネイティブ モードのレポート サーバーに対する権限の許可](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="d02ee-150">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="d02ee-151">[ロールを作成、削除、または変更する (Management Studio)](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="d02ee-151">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="d02ee-152">[レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="d02ee-152">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 [<span data-ttu-id="d02ee-153">ロールの割り当てを変更または削除する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="d02ee-153">Modify or Delete a Role Assignment &#40;Report Manager&#41;</span></span>](role-assignments-modify-or-delete.md)  
  
  
