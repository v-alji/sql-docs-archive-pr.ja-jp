---
title: SharePoint サイト上のレポートサーバーアイテムに対する権限の設定 (Reporting Services SharePoint 統合モード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
ms.assetid: 2467c657-a3bf-4ec3-a88c-8877df19823d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f38497843ca99342f13952153d7fed957564e006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713758"
---
# <a name="set-permissions-for-report-server-items-on-a-sharepoint-site-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="eeef0-102">サイト上のレポート サーバー アイテムに対する権限の設定 (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="eeef0-102">Set Permissions for Report Server Items on a SharePoint Site (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="eeef0-103">既定のセキュリティ設定では必要なレベルのアクセスが提供されない場合は、新しい権限レベルを作成して、特定のレポート サーバー アイテムまたは処理に対するアクセスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-103">If default security settings do not provide the level of access that you require, you can create new permission levels to provide access to specific report server items or operations.</span></span> <span data-ttu-id="eeef0-104">カスタム セキュリティ設定は、アクセスを特定のレポートに制限する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="eeef0-104">Custom security settings can be useful if you want to restrict access to a particular report.</span></span>  
  
 <span data-ttu-id="eeef0-105">権限レベルおよびグループを作成できるのはサイト所有者だけです。</span><span class="sxs-lookup"><span data-stu-id="eeef0-105">You must be a site owner to create permission levels and groups.</span></span> <span data-ttu-id="eeef0-106">権限レベルは、サイト全体でグローバルに使用されます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-106">Permission levels are used globally throughout a site.</span></span> <span data-ttu-id="eeef0-107">新しい権限レベルを作成した場合、他のサイト所有者もその権限レベルを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eeef0-107">If you create a new permission level, it will be available to other site owners.</span></span>  
  
 <span data-ttu-id="eeef0-108">ほとんどの権限は、親サイトから継承されます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-108">Most permissions are inherited from a parent site.</span></span> <span data-ttu-id="eeef0-109">特定のライブラリまたはアイテムに権限を割り当てた場合は、権限の継承が無効になるので、サイト階層のその分岐に関する権限管理に追加のオーバーヘッドが生じます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-109">If you assign permissions on a specific library or item, you break permission inheritance and incur additional overhead in how manage permissions for that branch of your site hierarchy.</span></span>  
  
 <span data-ttu-id="eeef0-110">権限は、レポート定義 (.rdl)、モデル (.smdl)、および共有データ ソース (.rsds) ファイルに対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-110">You can set permissions on report definition (.rdl), model (.smdl), and shared data source (.rsds) files.</span></span> <span data-ttu-id="eeef0-111">同一のアイテムについて、継承された権限とそのアイテムに対して管理する権限を組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="eeef0-111">You cannot combine inherited and managed permissions on the same item.</span></span> <span data-ttu-id="eeef0-112">権限を直接管理することを選択した場合、継承された権限は現在のアイテムに対して無効になります。</span><span class="sxs-lookup"><span data-stu-id="eeef0-112">If you choose to manage permissions directly, inherited permissions will have no effect on the current item.</span></span> <span data-ttu-id="eeef0-113">後で権限の継承を再開する場合、 **[アクション]** メニューの **[権限の継承]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eeef0-113">If you want to resume permission inheritance later, you can select **Inherit Permissions** on the **Actions** menu.</span></span>  
  
 <span data-ttu-id="eeef0-114">モデル内のエンティティおよびパースペクティブに対する権限を設定するには、モデルに対するフル コントロール レベルの権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eeef0-114">To set permissions on entities and perspectives in a model, you must have Full Control level of permission for the model.</span></span> <span data-ttu-id="eeef0-115">フル コントロールには、サイト所有者とフル コントロール レベルの権限を持つ他の SharePoint グループに与えられるサイト レベルの権限である "権限の管理" が含まれます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-115">Full Control includes "Manage Permissions", which is a site level permission that is granted to site owners and other SharePoint groups who have Full Control level of permission.</span></span> <span data-ttu-id="eeef0-116">特定のユーザーがモデル アイテム セキュリティを設定できるようにするには、権限の継承を無効にした後で、高度な権限 (たとえばフル コントロール) をモデル ファイル上のユーザーまたはグループに許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eeef0-116">If you want to offer specific users the ability to set model item security, you must break permission inheritance and grant elevated permissions (such as Full Control) to the user or group on the model file.</span></span> <span data-ttu-id="eeef0-117">アイテム (たとえばライブラリ内のファイル) に対するフル コントロールを許可した場合、権限のスコープはそのアイテムであり、親や同じライブラリ内の他のアイテムには及びません。</span><span class="sxs-lookup"><span data-stu-id="eeef0-117">When you grant Full Control on an item such as a file in the library, the permissions are scoped to that item and do not extend to the parent or to other items within the same library.</span></span> <span data-ttu-id="eeef0-118">モデルに対する権限の管理権限が与えられたユーザーは、SharePoint サイトまたはモデル デザイナーを介して、設定されたモデル アイテム セキュリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-118">After the user has Manage Permissions permission on the model, he or she can use set model item security via the SharePoint site or Model Designer.</span></span>  
  
### <a name="to-set-permissions-on-an-individual-report-model-or-data-source"></a><span data-ttu-id="eeef0-119">レポート、モデル、またはデータ ソースに対して個別に権限を設定するには</span><span class="sxs-lookup"><span data-stu-id="eeef0-119">To set permissions on an individual report, model, or data source</span></span>  
  
1.  <span data-ttu-id="eeef0-120">まだライブラリが開いていない場合は、サイド リンク バーでライブラリの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-120">If the library is not already open, click its name on the Quick Launch.</span></span> <span data-ttu-id="eeef0-121">ライブラリの名前が表示されていない場合は、 **[すべてのサイト コンテンツの表示]** をクリックし、ライブラリの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-121">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="eeef0-122">レポート、レポート モデル、または共有データ ソース ファイルをポイントします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-122">Point to the report, report model, or shared data source file.</span></span>  
  
3.  <span data-ttu-id="eeef0-123">下矢印をクリックし、メニューの **[権限の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-123">Click the down arrow, and on the menu, click **Manage Permissions**.</span></span>  
  
4.  <span data-ttu-id="eeef0-124">**[アクション]** メニューの **[権限の編集]** をクリックし、 **[OK]** をクリックして操作を確定します。</span><span class="sxs-lookup"><span data-stu-id="eeef0-124">On the **Actions** menu, click **Edit Permissions**, and then click **OK** to confirm the action.</span></span>  
  
5.  <span data-ttu-id="eeef0-125">そのファイルを使用する権限がないユーザーまたはグループに権限を与えるには、 **[新規作成]** をクリックし、 **[ユーザーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-125">To give permissions to a user or group that does not yet have permissions to use the file, click **New**, and then click **Add Users**.</span></span>  
  
6.  <span data-ttu-id="eeef0-126">既存のユーザーまたはグループの権限を削除または変更するには、まずユーザーまたはグループの横にあるチェック ボックスをオンにします。次に、 **[アクション]** をクリックし、 **[ユーザー権限の削除]** または **[ユーザー権限の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-126">To remove or modify permissions for an existing user or group, click the check box next to the user or group, click **Actions**, and then click **Remove User Permissions** or **Edit User Permissions**.</span></span>  
  
### <a name="to-set-permissions-that-enable-model-item-security"></a><span data-ttu-id="eeef0-127">モデル アイテム セキュリティを有効にする権限を設定するには</span><span class="sxs-lookup"><span data-stu-id="eeef0-127">To set permissions that enable model item security</span></span>  
  
1.  <span data-ttu-id="eeef0-128">サイトに対する "権限の管理権限" を持つアカウントを使用して、SharePoint サイトにログインします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-128">Log in to the SharePoint site using an account that has Manage Permissions permission on the site.</span></span>  
  
2.  <span data-ttu-id="eeef0-129">モデルが格納されているライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-129">Open the library that contains the model.</span></span>  
  
3.  <span data-ttu-id="eeef0-130">モデルをポイントします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-130">Point to the model.</span></span>  
  
4.  <span data-ttu-id="eeef0-131">モデルの横にある下矢印をクリックし、 **[権限の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-131">Click the down arrow next to the model, and click **Manage Permissions**.</span></span>  
  
5.  <span data-ttu-id="eeef0-132">**[アクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-132">Click **Actions**.</span></span>  
  
6.  <span data-ttu-id="eeef0-133">**[権限を編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-133">Click **Edit Permissions**.</span></span> <span data-ttu-id="eeef0-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-134">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="eeef0-135">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-135">Click **New**.</span></span>  
  
8.  <span data-ttu-id="eeef0-136">**[ユーザーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-136">Click **Add Users**.</span></span>  
  
9. <span data-ttu-id="eeef0-137">[ユーザー/グループ] で、ユーザー アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="eeef0-137">In Users/Groups, enter the user account.</span></span>  
  
10. <span data-ttu-id="eeef0-138">**[ユーザーへの権限の直接付与]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eeef0-138">Select **Give users permission directly**.</span></span>  
  
11. <span data-ttu-id="eeef0-139">**[フル コントロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-139">Click **Full Control**.</span></span>  
  
12. <span data-ttu-id="eeef0-140">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eeef0-140">Click **OK**.</span></span> <span data-ttu-id="eeef0-141">特定のモデルの権限の管理権限が与えられたユーザーは、モデルを開いて、モデル内の権限を編集できます。</span><span class="sxs-lookup"><span data-stu-id="eeef0-141">Once a user has the ability to manage permissions for a specific model, he or she can open the model to edit permissions within the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeef0-142">参照</span><span class="sxs-lookup"><span data-stu-id="eeef0-142">See Also</span></span>  
 <span data-ttu-id="eeef0-143">[レポート サーバー アイテムに対して Windows SharePoint Services の組み込みのセキュリティを使用する](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="eeef0-143">[Use Built-in Security in Windows SharePoint Services for Report Server Items](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md) </span></span>  
 <span data-ttu-id="eeef0-144">[SharePoint Web アプリケーションのレポート サーバー操作に対するアクセス許可を設定する](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span><span class="sxs-lookup"><span data-stu-id="eeef0-144">[Set Permissions for Report Server Operations in a SharePoint Web Application](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span></span>  
 <span data-ttu-id="eeef0-145">[SQL Server Reporting Services と SharePoint グループの役割とタスクの比較とアクセス許可](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="eeef0-145">[Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span></span>  
 <span data-ttu-id="eeef0-146">[レポート サーバー アイテムの SharePoint サイトおよびリスト権限のリファレンス](sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="eeef0-146">[SharePoint Site and List Permission Reference for Report Server Items](sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span></span>  
 [<span data-ttu-id="eeef0-147">SharePoint サイトのレポート サーバー アイテムに対する権限の付与</span><span class="sxs-lookup"><span data-stu-id="eeef0-147">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
