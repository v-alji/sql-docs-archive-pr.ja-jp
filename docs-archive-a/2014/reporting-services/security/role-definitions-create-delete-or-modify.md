---
title: ロールを作成、削除、または変更する (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- deleting roles
- removing roles
- roles [Reporting Services], definitions
- modifying roles
- roles [Reporting Services], deleting
- roles [Reporting Services], modifying
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 543bddda88e41af39d3200df4728716d46b3ae8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721062"
---
# <a name="create-delete-or-modify-a-role-management-studio"></a><span data-ttu-id="f2a65-102">ロールを作成、削除、または変更する (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f2a65-102">Create, Delete, or Modify a Role (Management Studio)</span></span>
  <span data-ttu-id="f2a65-103">Reporting Services には、レポート サーバーへのアクセス レベルをあらかじめ定義したロールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f2a65-103">Reporting Services provides predefined roles that define a level of access to a report server.</span></span> <span data-ttu-id="f2a65-104">レポート サーバーにアクセスする各ユーザーまたはグループは、実行できるタスクが定義されたロールを介して、レポート サーバーにアクセスすることになります。</span><span class="sxs-lookup"><span data-stu-id="f2a65-104">Each user or group who requires access to report server does so through a role that describes the tasks that can be performed.</span></span> <span data-ttu-id="f2a65-105">ロールは、レポート サーバー全体に対して定義されます。</span><span class="sxs-lookup"><span data-stu-id="f2a65-105">Roles are defined for the report server as a whole.</span></span> <span data-ttu-id="f2a65-106">レポート サーバーの特定の部分についてロール定義を変更したり、状況に依存するようなロールを指定したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f2a65-106">You cannot vary a role definition for specific parts of the report server, or specify that a role be used differently depending on the circumstances.</span></span>  
  
 <span data-ttu-id="f2a65-107">ロールを作成、変更、または削除するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-107">To create, modify, or delete roles, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f2a65-108">削除できるのは、使用されていないロールだけです。</span><span class="sxs-lookup"><span data-stu-id="f2a65-108">You can only delete roles that are not used.</span></span>  
  
 <span data-ttu-id="f2a65-109">作成したロールにユーザーおよびグループを割り当てるには、レポート マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-109">To assign users and groups to the roles that you create, use Report Manager.</span></span> <span data-ttu-id="f2a65-110">詳細については、「[レポートサーバーへのユーザーアクセスを許可する &#40;レポートマネージャー&#41;](grant-user-access-to-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2a65-110">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2a65-111">レポート サーバーが SharePoint 統合モード用に構成されている場合、統合先の SharePoint サイトに接続すると、レポート サーバーのコンテンツや操作へのアクセスを制御する権限レベルを閲覧および変更できます。</span><span class="sxs-lookup"><span data-stu-id="f2a65-111">If the report server is configured for SharePoint integrated mode, and you connected to the SharePoint site that the report server is integrated with, you can view and modify the permission levels that control access to report server content and operations.</span></span>  
  
### <a name="to-create-a-role-definition"></a><span data-ttu-id="f2a65-112">ロールの定義を作成するには</span><span class="sxs-lookup"><span data-stu-id="f2a65-112">To create a role definition</span></span>  
  
1.  <span data-ttu-id="f2a65-113">オブジェクト エクスプローラーで、レポート サーバーのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-113">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="f2a65-114">[セキュリティ] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-114">Expand the Security folder.</span></span>  
  
3.  <span data-ttu-id="f2a65-115">アイテムレベルのロールの定義を作成する場合は、 **[ロール]** を右クリックし、 **[新しいロール]** をポイントします。</span><span class="sxs-lookup"><span data-stu-id="f2a65-115">If you are creating an item-level role definition, right-click **Roles**, and point to **New Role**.</span></span>  
  
     <span data-ttu-id="f2a65-116">また、システム レベルのロールの定義を作成する場合は、 **[システム ロール]** を右クリックし、 **[新しいシステム ロール]** をポイントします。</span><span class="sxs-lookup"><span data-stu-id="f2a65-116">Or, if you are creating a system-level role definition, right-click **System Roles**, and point to **New System Role**.</span></span>  
  
4.  <span data-ttu-id="f2a65-117">ロールに対する一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-117">Type a unique name for the role.</span></span> <span data-ttu-id="f2a65-118">名前には、少なくとも 1 つの文字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2a65-118">A name must contain at least one character.</span></span> <span data-ttu-id="f2a65-119">スペースおよび記号を含めることもできますが、; ?</span><span class="sxs-lookup"><span data-stu-id="f2a65-119">It can also include spaces and certain symbols, but not the characters ; ?</span></span> <span data-ttu-id="f2a65-120">: \@ & = +、$/\* \< > |"または/です。</span><span class="sxs-lookup"><span data-stu-id="f2a65-120">: \@ & = + , $ / \* \< > | " or /.</span></span>  
  
5.  <span data-ttu-id="f2a65-121">必要に応じて、説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-121">Optionally type a description.</span></span> <span data-ttu-id="f2a65-122">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、この説明はこのページでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2a65-122">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] this description is visible only on this page.</span></span> <span data-ttu-id="f2a65-123">レポート マネージャーを使用してこのアイテムを表示するユーザーは、この説明をレポート マネージャーで参照できます。</span><span class="sxs-lookup"><span data-stu-id="f2a65-123">Users who view this item through Report Manager can see this description in that tool.</span></span>  
  
6.  <span data-ttu-id="f2a65-124">このロールのメンバーが実行できるタスクを選択します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-124">Select the tasks that members of this role can perform.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-or-modify-a-role-definition"></a><span data-ttu-id="f2a65-125">ロールの定義を削除または変更するには</span><span class="sxs-lookup"><span data-stu-id="f2a65-125">To delete or modify a role definition</span></span>  
  
1.  <span data-ttu-id="f2a65-126">オブジェクト エクスプローラーで、レポート サーバーのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-126">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="f2a65-127">[セキュリティ] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-127">Expand the Security folder.</span></span>  
  
3.  <span data-ttu-id="f2a65-128">アイテムレベルのロールの定義を削除または変更するには、[ロール] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-128">To delete or modify an item-level role definition, expand the Roles folder.</span></span> <span data-ttu-id="f2a65-129">以下のいずれかを行います。</span><span class="sxs-lookup"><span data-stu-id="f2a65-129">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="f2a65-130">ロールの定義を削除するには、アイテムを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2a65-130">To delete a role definition, right-click the item and click **Delete**.</span></span> <span data-ttu-id="f2a65-131">**[オブジェクトの削除]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2a65-131">The **Delete Object** dialog box is displayed.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  <span data-ttu-id="f2a65-132">ロールの定義を変更するには、アイテムを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2a65-132">To modify a role definition, right-click the item and click **Properties**.</span></span> <span data-ttu-id="f2a65-133">**[ユーザー ロールのプロパティ]** ダイアログ ボックスの [全般] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2a65-133">The General page of the **User Role Properties** dialog box is displayed.</span></span>  
  
         <span data-ttu-id="f2a65-134">このロールのメンバーが実行できるタスクを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2a65-134">Select the tasks that members of this role can perform, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="f2a65-135">システム レベルのロールの定義を削除または変更するには、 **[システム ロール]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-135">To delete or modify a system-level role definition, expand the **System Roles** folder.</span></span> <span data-ttu-id="f2a65-136">以下のいずれかを行います。</span><span class="sxs-lookup"><span data-stu-id="f2a65-136">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="f2a65-137">システム ロールの定義を削除するには、アイテムを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2a65-137">To delete a system role definition, right-click the item and click **Delete**.</span></span> <span data-ttu-id="f2a65-138">**[オブジェクトの削除]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2a65-138">The **Delete Object** dialog box is displayed.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  <span data-ttu-id="f2a65-139">システム ロールの定義を変更するには、アイテムを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2a65-139">To modify a system role definition, right-click the item and click **Properties**.</span></span> <span data-ttu-id="f2a65-140">**[システム ロールのプロパティ]** ダイアログ ボックスの [全般] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2a65-140">The General page of the **System Role Properties** dialog box is displayed.</span></span>  
  
         <span data-ttu-id="f2a65-141">このロールのメンバーが実行できるタスクを選択し、 **[OK]** をクリックして変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="f2a65-141">Select the tasks that members of this role can perform, and click **OK** to apply the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a65-142">参照</span><span class="sxs-lookup"><span data-stu-id="f2a65-142">See Also</span></span>  
 <span data-ttu-id="f2a65-143">[Management Studio でレポートサーバーに接続する](../tools/connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="f2a65-143">[Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="f2a65-144">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="f2a65-144">(create-and-manage-role-assignments.md)</span></span>   
 [<span data-ttu-id="f2a65-145">SQL Server Management Studio の Reporting Services &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f2a65-145">Reporting Services in SQL Server Management Studio &#40;SSRS&#41;</span></span>](../tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
  
