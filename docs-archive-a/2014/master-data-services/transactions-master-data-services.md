---
title: トランザクション (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], about transactions
- transactions [Master Data Services]
ms.assetid: 4cd2fa6f-9c76-4b7a-ae18-d4e5fd2f03f5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c693b550e0c1adb8f5910d99c7125c85f41abb8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740105"
---
# <a name="transactions-master-data-services"></a><span data-ttu-id="ae86a-102">トランザクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ae86a-102">Transactions (Master Data Services)</span></span>
  <span data-ttu-id="ae86a-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、メンバーに対してアクションが行われるたびに、トランザクションが記録されます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a transaction is recorded each time action is taken on a member.</span></span> <span data-ttu-id="ae86a-104">すべてのユーザーがトランザクションを表示でき、管理者はトランザクションを破棄できます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-104">Transactions can be viewed by all users and reversed by administrators.</span></span> <span data-ttu-id="ae86a-105">日付、時刻、アクションを行ったユーザーが、その他の詳細と共にトランザクションによって表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-105">Transactions show the date, time, and user who took the action, along with other details.</span></span> <span data-ttu-id="ae86a-106">ユーザーは、トランザクションが行われた理由を示す注釈をトランザクションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-106">Users can add an annotation to a transaction, to indicate why a transaction took place.</span></span>  
  
## <a name="when-transaction-are-recorded"></a><span data-ttu-id="ae86a-107">トランザクションが記録されるタイミング</span><span class="sxs-lookup"><span data-stu-id="ae86a-107">When Transaction Are Recorded</span></span>  
 <span data-ttu-id="ae86a-108">トランザクションは、次のタイミングで記録されます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-108">Transactions are recorded when members:</span></span>  
  
-   <span data-ttu-id="ae86a-109">メンバーが作成、削除、または再アクティブ化されたとき。</span><span class="sxs-lookup"><span data-stu-id="ae86a-109">Are created, deleted, or reactivated.</span></span>  
  
-   <span data-ttu-id="ae86a-110">メンバーが属性値を変更したとき。</span><span class="sxs-lookup"><span data-stu-id="ae86a-110">Have attribute values changed.</span></span>  
  
-   <span data-ttu-id="ae86a-111">メンバーが階層内で移動されたとき。</span><span class="sxs-lookup"><span data-stu-id="ae86a-111">Are moved in a hierarchy.</span></span>  
  
 <span data-ttu-id="ae86a-112">ビジネス ルールによって属性値が変更された場合、トランザクションは記録されません。</span><span class="sxs-lookup"><span data-stu-id="ae86a-112">Transactions are not recorded when business rules change attribute values.</span></span>  
  
## <a name="view-and-manage-transactions"></a><span data-ttu-id="ae86a-113">トランザクションの表示および管理</span><span class="sxs-lookup"><span data-stu-id="ae86a-113">View and Manage Transactions</span></span>  
 <span data-ttu-id="ae86a-114">**[エクスプローラー]** 機能領域では、自分で作成したトランザクションを表示したり、自分で作成したトランザクションに注釈を設定 (コメントを追加) したりできます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-114">In the **Explorer** functional area, you can view and annotate (add comments to) the transactions that you made yourself.</span></span>  
  
 <span data-ttu-id="ae86a-115">**[バージョン管理]** 機能領域では、管理者は、アクセス権を持っているモデルに対する全ユーザーのトランザクションをすべて表示したり、それらのトランザクションを破棄したりできます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-115">In the **Version Management** functional area, administrators can view all transactions for all users for the models they have access to, and reverse any of these transactions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae86a-116">**[バージョン管理]** 機能領域で読み取り専用アクセス許可レベルが適用されていない限り、管理者は全ユーザーの全トランザクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-116">Administrators can view all transactions for all users as long as they don't have the read-only permission level applied in the **Version Management** functional area .</span></span> <span data-ttu-id="ae86a-117">たとえば、読み取り専用アクセス許可と更新アクセス許可レベルが管理者に設定されている場合、読み取り専用アクセス許可が更新アクセス許可よりも優先されるため、管理者は他のユーザーのトランザクションを表示できません。</span><span class="sxs-lookup"><span data-stu-id="ae86a-117">For example, if the read-only permission and update permission level is set for the administrator, the administrator will not be able to see other user transactions because the read-only permission will take precedence over the update permission.</span></span>

## <a name="system-settings"></a><span data-ttu-id="ae86a-118">システム設定</span><span class="sxs-lookup"><span data-stu-id="ae86a-118">System Settings</span></span>  
 <span data-ttu-id="ae86a-119">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] には、レコードがステージングされたときにトランザクションが記録されるかどうかに影響する設定があります。</span><span class="sxs-lookup"><span data-stu-id="ae86a-119">There is a setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affects whether or not transactions are recorded when records are staged.</span></span> <span data-ttu-id="ae86a-120">この設定は SQL Server 2008 R2 にのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="ae86a-120">This setting affects SQL Server 2008 R2 only.</span></span> <span data-ttu-id="ae86a-121">この設定は、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整するか、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの System Settings テーブルで直接調整することができます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-121">You can adjust this setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="ae86a-122">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae86a-122">For more information, see [System Settings &#40;Master Data Services&#41;](system-settings-master-data-services.md).</span></span>  
  
 <span data-ttu-id="ae86a-123">このバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]にデータをインポートする場合に、ストアド プロシージャを開始するときにトランザクションをログに記録するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-123">When importing data in this version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can specify whether or not to log transactions when initiating the stored procedure.</span></span> <span data-ttu-id="ae86a-124">詳細については、「[ステージング ストアド プロシージャ (マスター データ サービス)](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae86a-124">For more information, see [Staging Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).</span></span>  
  
## <a name="concurrency"></a><span data-ttu-id="ae86a-125">コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="ae86a-125">Concurrency</span></span>  
 <span data-ttu-id="ae86a-126">複数のエクスプローラー セッションで特定のエンティティの値が同時に表示される場合、同じ値を同時に編集している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ae86a-126">If a particular entity value is shown simultaneously in more than one Explorer session, concurrent edits to the same value are possible.</span></span> <span data-ttu-id="ae86a-127">同時編集は、MDS によって自動的に検出されません。</span><span class="sxs-lookup"><span data-stu-id="ae86a-127">Concurrent edits will not be detected automatically by MDS.</span></span> <span data-ttu-id="ae86a-128">これは、複数のユーザーが複数のセッション (たとえば、複数のコンピューター、複数のブラウザーのタブやウィンドウ、複数のユーザー アカウントなど) から Web ブラウザー内で MDS エクスプローラーを使用している場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="ae86a-128">This can occur when multiple users use the MDS Explorer in the Web browser from multiple sessions, for example from multiple computers, multiple browser tabs or windows, or multiple user accounts.</span></span>  
  
 <span data-ttu-id="ae86a-129">トランザクションが有効になっているにもかかわらず、複数のユーザーがエラーなく、同じエンティティの値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-129">More than one user can update the same entity values without error despite transactions being enabled.</span></span> <span data-ttu-id="ae86a-130">通常、時間順で最後に編集した値が優先されます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-130">Typically the last edit to the value in a sequence of time will take precedence.</span></span> <span data-ttu-id="ae86a-131">トランザクションの履歴で、重複する編集の競合を手動で観察することができ、管理者によって手動で取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="ae86a-131">The duplicate edit conflict can be manually observed in the transaction history and can be reversed manually by the administrator.</span></span> <span data-ttu-id="ae86a-132">トランザクションの履歴は、各セッションの問題の属性に対する **[以前の値]** と **[新しい値]** の個々のトランザクションを表示しますが、複数の **[新しい値]** が同一の古い値に対して存在しても、競合を自動的には解決しません。</span><span class="sxs-lookup"><span data-stu-id="ae86a-132">The transaction history will show the individual transactions for the **Prior value** and **New value** for the attribute in question from each session, but will not automatically resolve the conflict when multiple **New Values** exist for the same old value.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ae86a-133">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ae86a-133">Related Tasks</span></span>  
  
|<span data-ttu-id="ae86a-134">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="ae86a-134">Task Description</span></span>|<span data-ttu-id="ae86a-135">トピック</span><span class="sxs-lookup"><span data-stu-id="ae86a-135">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ae86a-136">トランザクションを破棄してアクションを元に戻す (管理者のみ)。</span><span class="sxs-lookup"><span data-stu-id="ae86a-136">Undo an action by reversing a transaction (administrators only).</span></span>|[<span data-ttu-id="ae86a-137">トランザクションを破棄する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ae86a-137">Reverse a Transaction &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="ae86a-138">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ae86a-138">Related Content</span></span>  
  
-   [<span data-ttu-id="ae86a-139">管理者 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ae86a-139">Administrators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/administrators-master-data-services.md)  
  
-   [<span data-ttu-id="ae86a-140">注釈 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ae86a-140">Annotations &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/annotations-master-data-services.md)  
  
  
