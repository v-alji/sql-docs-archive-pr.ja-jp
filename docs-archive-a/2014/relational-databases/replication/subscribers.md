---
title: '[サブスクライバー] | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c5281a53b755bc171cdf96e7856e38ee6a54a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634378"
---
# <a name="subscribers"></a><span data-ttu-id="d6716-102">[サブスクライバー]</span><span class="sxs-lookup"><span data-stu-id="d6716-102">Subscribers</span></span>
  <span data-ttu-id="d6716-103">選択した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリケーションへのサブスクリプションを受け取るサブスクライバーまたは以外のサブスクライバーを指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d6716-103">Specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers that will receive a subscription to the selected publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d6716-104">オプション</span><span class="sxs-lookup"><span data-stu-id="d6716-104">Options</span></span>  
 <span data-ttu-id="d6716-105">**[パブリッシャーのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="d6716-105">**Subscribers**</span></span>  
 <span data-ttu-id="d6716-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [パブリケーション][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページで選択したパブリケーションへのサブスクライバーとして、 **のデータ ソースまたは** 以外のデータ ソースを有効にするには、グリッド内の対応するチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d6716-106">Select the check box in the grid to enable the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source as a Subscriber to the publication chosen on the **Publication** page.</span></span> <span data-ttu-id="d6716-107">サブスクライバーが一覧にない場合、 **[サブスクライバーの追加]** または **[SQL Server サブスクライバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6716-107">If the Subscriber is not listed, click **Add Subscriber** or **Add SQL Server Subscriber**.</span></span>  
  
 <span data-ttu-id="d6716-108">**サブスクリプション データベース**</span><span class="sxs-lookup"><span data-stu-id="d6716-108">**Subscription database**</span></span>  
 <span data-ttu-id="d6716-109">この列で表示される情報と実行できる操作は、 **[サブスクライバー]** 列に表示されているサブスクライバーの種類によって変わります。</span><span class="sxs-lookup"><span data-stu-id="d6716-109">The information displayed in and actions available from this column depend on the type of Subscriber listed in the **Subscribers** column:</span></span>  
  
-   <span data-ttu-id="d6716-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーの場合、 **[サブスクリプション データベース]** の一覧からサブスクリプション データベースを選択するか、同じ一覧から **[新しいデータベース]** コマンドを選択して新しいデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6716-110">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, select a subscription database from the **Subscription Database** list or create a new database by selecting the **New database** command from the same list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6716-111">パブリッシャーをサブスクライバーとして有効にする場合、サブスクリプション データベースはパブリケーション データベースとは別にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6716-111">If you are enabling the Publisher as a Subscriber, the subscription database must be different from the publication database.</span></span>  
  
-   <span data-ttu-id="d6716-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーの場合、サブスクリプション データベースは表示されません。</span><span class="sxs-lookup"><span data-stu-id="d6716-112">For non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, the subscription database is not displayed.</span></span> <span data-ttu-id="d6716-113">**[SQL Server 以外のサブスクライバーの追加]** ダイアログ ボックスの **[データ ソース名]** フィールドで、データベースおよび他の接続情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6716-113">Specify the database, along with other connection information, in the **Data source name** field of the **Add Non-SQL Server** dialog box.</span></span> <span data-ttu-id="d6716-114">このダイアログ ボックスを開くには、 **[サブスクライバーの追加]** をクリックして **[SQL Server 以外のサブスクライバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6716-114">This dialog box is available by clicking **Add Subscriber** and then clicking **Add Non-SQL Server Subscriber**.</span></span>  
  
 <span data-ttu-id="d6716-115">**[サブスクライバーの追加]**</span><span class="sxs-lookup"><span data-stu-id="d6716-115">**Add Subscriber**</span></span>  
 <span data-ttu-id="d6716-116">サブスクライバーとして有効にできるサーバーの一覧に、サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="d6716-116">Add a server to the list of servers that can be enabled as Subscribers.</span></span> <span data-ttu-id="d6716-117">このボタンは、次に示す条件がすべて満たされた場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6716-117">This button is displayed when all of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="d6716-118">選択したパブリケーションが、サブスクリプションの更新をサポートしないスナップショット パブリケーションまたはトランザクション パブリケーションである。</span><span class="sxs-lookup"><span data-stu-id="d6716-118">The publication you selected is a snapshot or transactional publication that does not support updating subscriptions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6716-119">サブスクライブしているパブリケーションに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクリプションが含まれており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーにまだ対応していない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクリプションを追加できません。</span><span class="sxs-lookup"><span data-stu-id="d6716-119">If the publication you are subscribing to has [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subscriptions and the publication is not already enabled for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, you cannot add a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subscription.</span></span>  
  
-   <span data-ttu-id="d6716-120">サブスクリプションがプッシュ サブスクリプションである。</span><span class="sxs-lookup"><span data-stu-id="d6716-120">The subscription is a push subscription.</span></span>  
  
-   <span data-ttu-id="d6716-121">選択したパブリケーションのパブリッシャーが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンである。</span><span class="sxs-lookup"><span data-stu-id="d6716-121">The Publisher of the selected publication is [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later.</span></span>  
  
 <span data-ttu-id="d6716-122">**[サブスクライバーの追加]** をクリックすると、 **[SQL Server サブスクライバーの追加]** と **[SQL Server 以外のサブスクライバーの追加]** という 2 つの選択肢を持つメニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6716-122">Clicking **Add Subscriber** shows a menu with two choices: **Add SQL Server Subscriber** and **Add Non-SQL Server Subscriber**.</span></span> <span data-ttu-id="d6716-123">Oracle または IBM DB2 のサブスクライバーを追加するには、 **[SQL Server 以外のサブスクライバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6716-123">Click **Add Non-SQL Server Subscriber** to add an Oracle or IBM DB2 Subscriber.</span></span>  
  
 <span data-ttu-id="d6716-124">**[SQL Server サブスクライバーの追加]**</span><span class="sxs-lookup"><span data-stu-id="d6716-124">**Add SQL Server Subscriber**</span></span>  
 <span data-ttu-id="d6716-125">サブスクライバーとして有効にできるサーバーの一覧に、サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="d6716-125">Add a server to the list of servers that can be enabled as Subscribers.</span></span> <span data-ttu-id="d6716-126">このボタンは、次のいずれかの条件が満たされた場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6716-126">This button is displayed when one or more of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="d6716-127">選択したパブリケーションが、サブスクリプションの更新をサポートするマージ パブリケーション、スナップショット パブリケーション、またはトランザクション パブリケーションである。</span><span class="sxs-lookup"><span data-stu-id="d6716-127">The publication you selected is a merge publication, or a snapshot or transactional publication that supports updating subscriptions.</span></span>  
  
-   <span data-ttu-id="d6716-128">サブスクリプションがプル サブスクリプションである。</span><span class="sxs-lookup"><span data-stu-id="d6716-128">The subscription is a pull subscription.</span></span>  
  
-   <span data-ttu-id="d6716-129">選択したパブリケーションのパブリッシャーが、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]よりも古いバージョンである。</span><span class="sxs-lookup"><span data-stu-id="d6716-129">The Publisher of the selected publication is earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="d6716-130">古いバージョンの場合、このボタンは次の条件のいずれかが満たされた場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6716-130">For earlier versions, the button is displayed only if one or more of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="d6716-131">パブリッシャーの **sysadmin** 固定サーバー ロールのメンバーである。</span><span class="sxs-lookup"><span data-stu-id="d6716-131">You are a member of the **sysadmin** fixed server role at the Publisher.</span></span>  
  
    -   <span data-ttu-id="d6716-132">サブスクライバーが、 **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[サブスクライバー]** ページに追加されている。</span><span class="sxs-lookup"><span data-stu-id="d6716-132">The Subscriber has been added on the **Subscribers** page of the **Publisher Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="d6716-133">パブリケーションで匿名サブスクリプションが許可されている。</span><span class="sxs-lookup"><span data-stu-id="d6716-133">The publication allows anonymous subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6716-134">参照</span><span class="sxs-lookup"><span data-stu-id="d6716-134">See Also</span></span>  
 <span data-ttu-id="d6716-135">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="d6716-135">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="d6716-136">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="d6716-136">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="d6716-137">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="d6716-137">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="d6716-138">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="d6716-138">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
