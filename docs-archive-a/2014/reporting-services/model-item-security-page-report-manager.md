---
title: '[モデルアイテムのセキュリティ] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.modelitemsecurity.f1
ms.assetid: 8c5b29ae-1f17-41f2-ab59-97899b8fb4fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 928572437990c7f7fe1117c086c65c939aa9c999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631639"
---
# <a name="model-item-security-page-report-manager"></a><span data-ttu-id="dc069-102">[モデル アイテムのセキュリティ] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="dc069-102">Model Item Security Page (Report Manager)</span></span>
  <span data-ttu-id="dc069-103">このページでは、特定のアイテムに対する読み取り専用権限の許可や取り消しを行うことにより、モデルの各部をセキュリティで保護できます。</span><span class="sxs-lookup"><span data-stu-id="dc069-103">Use this page to secure parts of a model by granting or revoking read-only permissions on particular items.</span></span> <span data-ttu-id="dc069-104">モデル アイテムのセキュリティは、実行時のアドホック データ探索や、レポート ビルダーでのレポート作成時に、パブリッシュされたモデルの各部分を使用できるかどうかに影響します。</span><span class="sxs-lookup"><span data-stu-id="dc069-104">Model item security affects ad hoc data exploration at run time and the ability to use parts of a published model when creating reports in Report Builder.</span></span> <span data-ttu-id="dc069-105">この機能を使用するには、コンテンツ マネージャーの権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="dc069-105">To use this feature, you must have Content Manager permissions.</span></span>  
  
 <span data-ttu-id="dc069-106">モデル アイテムのセキュリティは、レポート サーバーで処理されるモデルに適用され、モデル デザイナーで編集したりレポート デザイナーで使用する .smdl ファイルには影響しません。</span><span class="sxs-lookup"><span data-stu-id="dc069-106">Model item security is applied to a model that is processed on the report server and does not affect .smdl files that you edit in Model Designer or use in Report Designer.</span></span> <span data-ttu-id="dc069-107">また、モデル定義の変更権限を持ったユーザーには適用されません。</span><span class="sxs-lookup"><span data-stu-id="dc069-107">Furthermore, it has no effect on users who have permission to modify a model definition.</span></span> <span data-ttu-id="dc069-108">モデルに対してコンテンツ マネージャーまたはパブリッシャーの権限を持つユーザーは、モデル アイテムのセキュリティを適用しているかどうかに関係なく、モデルのすべての部分を表示できます。</span><span class="sxs-lookup"><span data-stu-id="dc069-108">Any user who has Content Manager or Publisher permissions on a model can see all parts of it, regardless of whether you apply model item security.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc069-109">モデル アイテムのセキュリティは、セキュリティ フィルターを使用して強化することができます。</span><span class="sxs-lookup"><span data-stu-id="dc069-109">Model items can be further secured through the use of security filters.</span></span>  
  
 <span data-ttu-id="dc069-110">モデル アイテムのセキュリティは、モデル内のエンティティ、フォルダー、および個々のフィールドに対して定義できます。</span><span class="sxs-lookup"><span data-stu-id="dc069-110">You can define model item security on entities, folders, and individual fields within a model.</span></span> <span data-ttu-id="dc069-111">モデルにはセキュリティ保護可能なアイテムが非常に多く含まれるため、権限の継承をモデルに組み込むことにより、比較的少数のロールの割り当てをとおして多数のアイテムをセキュリティ保護できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="dc069-111">Because a model presents such a large surface of securable items, permission inheritance is built into the model so that you can secure a large number of items through a relatively small number of role assignments.</span></span> <span data-ttu-id="dc069-112">権限の継承は以下のものに基づいています。</span><span class="sxs-lookup"><span data-stu-id="dc069-112">Permission inheritance is based on the following:</span></span>  
  
-   <span data-ttu-id="dc069-113">モデル</span><span class="sxs-lookup"><span data-stu-id="dc069-113">Model</span></span>  
  
-   <span data-ttu-id="dc069-114">ルート ノード</span><span class="sxs-lookup"><span data-stu-id="dc069-114">Root node</span></span>  
  
-   <span data-ttu-id="dc069-115">フォルダーまたはエンティティ</span><span class="sxs-lookup"><span data-stu-id="dc069-115">Folders or entities</span></span>  
  
-   <span data-ttu-id="dc069-116">フィールド</span><span class="sxs-lookup"><span data-stu-id="dc069-116">Fields</span></span>  
  
 <span data-ttu-id="dc069-117">モデル アイテムへのアクセス権は、最初、モデル自体に設定されたロールの割り当てから継承されます。</span><span class="sxs-lookup"><span data-stu-id="dc069-117">Initially, permission to access to model items is inherited through role assignments that are set on the model itself.</span></span> <span data-ttu-id="dc069-118">レポート マネージャーでフォルダー内のモデルを表示する権限を持つユーザーは、モデル内のすべてのアイテムを表示できます。</span><span class="sxs-lookup"><span data-stu-id="dc069-118">A user who has permission to view a model in a folder in Report Manager can view all of the items in the model.</span></span>  
  
 <span data-ttu-id="dc069-119">モデル アイテムのセキュリティを適用する場合、ルート ノードにロールの割り当てを少なくとも 1 つ作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc069-119">If you apply model item security, you must create at least one role assignment on the root node.</span></span> <span data-ttu-id="dc069-120">ルート ノードに対するこの最初のロールの割り当てが、継承される権限の新しいソースとなります。</span><span class="sxs-lookup"><span data-stu-id="dc069-120">This initial role assignment on the root node becomes the new source of inherited permissions.</span></span> <span data-ttu-id="dc069-121">ルート ノードに対するロールの割り当てが、モデル階層内のすべてのアイテムに自動的に継承されます。</span><span class="sxs-lookup"><span data-stu-id="dc069-121">The role assignment on the root node is automatically inherited by all items in the model hierarchy.</span></span>  
  
 <span data-ttu-id="dc069-122">データ探索の権限をさらにカスタマイズする場合は、フォルダーとエンティティに対する権限を変更できます。</span><span class="sxs-lookup"><span data-stu-id="dc069-122">To further customize permissions on data exploration, you can vary permissions on folders and entities.</span></span> <span data-ttu-id="dc069-123">最後に、個別のフィールドに対する権限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="dc069-123">Finally, you can set permissions on individual fields.</span></span>  
  
 <span data-ttu-id="dc069-124">ロールの割り当てを容易に保守できるようにするには、個別のフィールドではなく、フォルダーまたはエンティティに対してのみ権限を設定します。</span><span class="sxs-lookup"><span data-stu-id="dc069-124">To make role assignments easier to maintain, set permissions only on folders or entities rather than individual fields.</span></span> <span data-ttu-id="dc069-125">自分で作成したロールの割り当てを検索することはできません。</span><span class="sxs-lookup"><span data-stu-id="dc069-125">You cannot search for role assignments that you create.</span></span> <span data-ttu-id="dc069-126">特定のフィールドに対してセキュリティを設定した後でそのセキュリティ設定を更新する場合は、モデル名前空間内でクリックを繰り返して、セキュリティを設定したフィールドを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc069-126">If you set security on specific fields and you want to update the security settings later, you must click through the model namespace to find the fields you secured.</span></span>  
  
 <span data-ttu-id="dc069-127">まずルート ノードに対してロールの割り当てを作成し、次にエンティティとフォルダーに対して追加のロールの割り当てを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc069-127">To get started, create a role assignment on the root node and then create additional role assignments on entities and folders.</span></span> <span data-ttu-id="dc069-128">モデル アイテムのセキュリティを消去するには、 **[このモデルのモデル アイテムは個別にセキュリティで保護する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="dc069-128">To clear model item security, clear the check box for **Secure individual model items independently for this model**.</span></span> <span data-ttu-id="dc069-129">このチェック ボックスをオフにすると、モデルから継承された、初期状態の権限に戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc069-129">Clearing the check box reverts back to the initial permissions that are inherited from the model.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="dc069-130">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="dc069-130">Navigation</span></span>  
 <span data-ttu-id="dc069-131">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="dc069-131">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a><span data-ttu-id="dc069-132">レポートの [全般] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="dc069-132">To open the General properties page for a report</span></span>  
  
1.  <span data-ttu-id="dc069-133">レポート マネージャーを開き、モデル アイテムのセキュリティを構成するモデルを探します。</span><span class="sxs-lookup"><span data-stu-id="dc069-133">Open Report Manager, and locate the model for which you want to configure security for model items.</span></span>  
  
2.  <span data-ttu-id="dc069-134">モデルの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc069-134">Hover over the model, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="dc069-135">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc069-135">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="dc069-136">この操作により、モデルの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="dc069-136">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="dc069-137">**[モデル アイテムのセキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc069-137">Select the **Model Item Security** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dc069-138">Options</span><span class="sxs-lookup"><span data-stu-id="dc069-138">Options</span></span>  
 <span data-ttu-id="dc069-139">**[このモデルのモデル アイテムは個別にセキュリティで保護する]**</span><span class="sxs-lookup"><span data-stu-id="dc069-139">**Secure individual model items independently for this model**</span></span>  
 <span data-ttu-id="dc069-140">モデル アイテムのセキュリティを有効にする場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="dc069-140">Click this check box to enable model item security.</span></span>  
  
 <span data-ttu-id="dc069-141">**[モデルのモデル アイテムに個別にセキュリティを指定します。]**</span><span class="sxs-lookup"><span data-stu-id="dc069-141">**Specify security for individual model items in the mode**</span></span>  
 <span data-ttu-id="dc069-142">モデル内のすべてのアイテムを表示します。</span><span class="sxs-lookup"><span data-stu-id="dc069-142">Shows all of the items in a model.</span></span> <span data-ttu-id="dc069-143">モデルの名前空間内を移動して、セキュリティを設定するアイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc069-143">You can navigate the model namespace to select the item you want to secure.</span></span> <span data-ttu-id="dc069-144">一度に 1 つのアイテムのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="dc069-144">You can only select one item at a time.</span></span> <span data-ttu-id="dc069-145">最初にルート ノードに対してロールの割り当てを作成してから、他のエンティティやフォルダーに対する作成に進んでください。</span><span class="sxs-lookup"><span data-stu-id="dc069-145">Be sure to create the first role assignment on the root node before proceeding to other entities and folders.</span></span>  
  
 <span data-ttu-id="dc069-146">**[次の親アイテムから権限を継承する]**</span><span class="sxs-lookup"><span data-stu-id="dc069-146">**Inherit permissions from the parent item**</span></span>  
 <span data-ttu-id="dc069-147">親アイテムのセキュリティ設定を継承する場合は、このオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc069-147">Click this option to inherit the security settings of the parent item.</span></span>  
  
 <span data-ttu-id="dc069-148">**[次のユーザーとグループをセミコロンで区切って読み取り権限を割り当ててください]**</span><span class="sxs-lookup"><span data-stu-id="dc069-148">**Assign read permission to the following users and groups (semi-colon separated)**</span></span>  
 <span data-ttu-id="dc069-149">アクセス権を定義するユーザーまたはグループ アカウントを指定する場合は、このオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc069-149">Click this option to specify the user or group account for which you are defining access.</span></span> <span data-ttu-id="dc069-150">既定のセキュリティを使用している場合、ユーザーおよびグループ アカウントは Windows ドメイン アカウントです。</span><span class="sxs-lookup"><span data-stu-id="dc069-150">If you are using default security, the user and group accounts are Windows domain accounts.</span></span> <span data-ttu-id="dc069-151">アカウントは、 \* \<domain> \\<アカウント \> \*の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="dc069-151">Specify the accounts in this format: *\<domain>\\<account\>*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc069-152">参照</span><span class="sxs-lookup"><span data-stu-id="dc069-152">See Also</span></span>  
 [<span data-ttu-id="dc069-153">Management Studio のレポート サーバーの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="dc069-153">Report Server in Management Studio F1 Help</span></span>](tools/report-server-in-management-studio-f1-help.md)  
  
  
