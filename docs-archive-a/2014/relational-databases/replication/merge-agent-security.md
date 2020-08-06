---
title: マージ エージェント セキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.MA.f1
helpviewer_keywords:
- Merge Agent Security dialog box
ms.assetid: 9b86171a-4381-4b39-869a-cdc161e7cd15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecbb044ca87ccfc74c5cb39a016667d15cf7a859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718057"
---
# <a name="merge-agent-security"></a><span data-ttu-id="7dcda-102">[マージ エージェント セキュリティ]</span><span class="sxs-lookup"><span data-stu-id="7dcda-102">Merge Agent Security</span></span>
  <span data-ttu-id="7dcda-103">**[マージ エージェント セキュリティ]** ダイアログ ボックスを使用すると、マージ エージェントの実行に使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7dcda-103">The **Merge Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Merge Agent runs.</span></span> <span data-ttu-id="7dcda-104">マージ エージェントは、プッシュ サブスクリプションの場合はディストリビューターで実行され、プル サブスクリプションの場合はサブスクライバーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="7dcda-104">The Merge Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions.</span></span> <span data-ttu-id="7dcda-105">エージェント プロセスがこのアカウントで実行されるため、Windows アカウントは *プロセス アカウント*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7dcda-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span> <span data-ttu-id="7dcda-106">ダイアログ ボックスで使用できる追加オプションは、次に示すアクセスの方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7dcda-106">Additional options available in the dialog box depend on how you access it:</span></span>  
  
-   <span data-ttu-id="7dcda-107">サブスクリプションの新規作成ウィザードからダイアログ ボックスを開いた場合は、マージ エージェントがプッシュ サブスクリプション用にサブスクライバーへの接続を作成するコンテキスト、またはプル サブスクリプション用にパブリッシャーおよびディストリビューターへの接続を作成するコンテキストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7dcda-107">If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Merge Agent makes connections to the Subscriber (for push subscriptions) or the Publisher and Distributor (for pull subscriptions).</span></span> <span data-ttu-id="7dcda-108">Windows アカウントを使用するか、指定した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントのコンテキストにより、接続を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7dcda-108">The connection can be made using the Windows account or under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
-   <span data-ttu-id="7dcda-109">**[サブスクリプションのプロパティ]** ダイアログ ボックスから開いた場合は、 **[サブスクライバー接続]** 行または **[パブリッシャー接続]** 行のプロパティ ボタン ( **[...]** ) をクリックして、マージ エージェントによる接続の作成のコンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="7dcda-109">If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Merge Agent makes connections by clicking the properties button (**...**) in the **Subscriber Connection** or **Publisher Connection** row of that dialog box.</span></span> <span data-ttu-id="7dcda-110">**[サブスクリプションのプロパティ]** ダイアログ ボックスへのアクセスの詳細については、「[プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)」および「[プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dcda-110">For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and how to: [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
 <span data-ttu-id="7dcda-111">各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dcda-111">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="7dcda-112">アカウントとパスワードは、エージェントが実行されるまで検証されません。</span><span class="sxs-lookup"><span data-stu-id="7dcda-112">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7dcda-113">オプション</span><span class="sxs-lookup"><span data-stu-id="7dcda-113">Options</span></span>  
 <span data-ttu-id="7dcda-114">**Process Account**</span><span class="sxs-lookup"><span data-stu-id="7dcda-114">**Process Account**</span></span>  
 <span data-ttu-id="7dcda-115">マージ エージェントの実行に使用する Windows アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="7dcda-115">Enter a Windows account under which the Merge Agent runs.</span></span>  
  
-   <span data-ttu-id="7dcda-116">プッシュ サブスクリプションでは、アカウントには次のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="7dcda-116">For push subscriptions, the account must:</span></span>  
  
    -   <span data-ttu-id="7dcda-117">最低でも、ディストリビューション データベースで **db_owner** 固定データベース ロールのメンバーである。</span><span class="sxs-lookup"><span data-stu-id="7dcda-117">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
    -   <span data-ttu-id="7dcda-118">PAL のメンバーである。</span><span class="sxs-lookup"><span data-stu-id="7dcda-118">Be a member of the PAL.</span></span>  
  
    -   <span data-ttu-id="7dcda-119">パブリケーション データベースのユーザーに関連付けられたログインである。</span><span class="sxs-lookup"><span data-stu-id="7dcda-119">Be a login associated with a user in the publication database.</span></span>  
  
    -   <span data-ttu-id="7dcda-120">スナップショット共有の読み取り権限を持っている。</span><span class="sxs-lookup"><span data-stu-id="7dcda-120">Have read permissions on the snapshot share.</span></span>  
  
-   <span data-ttu-id="7dcda-121">プル サブスクリプションでは、アカウントは少なくとも、サブスクリプション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dcda-121">For pull subscriptions, the account must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
 <span data-ttu-id="7dcda-122">接続を作成するときにプロセス アカウントを借用する場合、追加の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7dcda-122">Additional permissions are required if the process account is impersonated when connections are made.</span></span> <span data-ttu-id="7dcda-123">**[パブリッシャーおよびディストリビューターに接続]** および **[サブスクライバーに接続]** を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dcda-123">See the **Connect to the Publisher and Distributor** and **Connect to the Subscriber** sections below.</span></span>  
  
 <span data-ttu-id="7dcda-124">マージ エージェントは  **のインスタンスで動作しないので、** [プロセス アカウント][!INCLUDE[msCoName](../../includes/msconame-md.md)] は、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] に対するプル サブスクリプションに指定できません。</span><span class="sxs-lookup"><span data-stu-id="7dcda-124">**Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Merge Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
 <span data-ttu-id="7dcda-125">**[パスワード]** と **[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="7dcda-125">**Password** and **Confirm Password**</span></span>  
 <span data-ttu-id="7dcda-126">Windows アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7dcda-126">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="7dcda-127">**[パブリッシャーおよびディストリビューターに接続]**</span><span class="sxs-lookup"><span data-stu-id="7dcda-127">**Connect to the Publisher and Distributor**</span></span>  
 <span data-ttu-id="7dcda-128">プッシュ サブスクリプションの場合、パブリッシャーおよびディストリビューターへの接続は、常に **[プロセス アカウント]** テキスト ボックスで指定されたアカウントを借用することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="7dcda-128">For push subscriptions, connections to the Publisher and Distributor are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="7dcda-129">プル サブスクリプションの場合、マージ エージェントでパブリケーションおよびディストリビューターへの接続を作成するには、 **[プロセス アカウント]** テキスト ボックスで指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7dcda-129">For pull subscriptions, select whether the Merge Agent should make connections to the Publisher and Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="7dcda-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7dcda-130">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="7dcda-131">は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7dcda-131">recommends that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="7dcda-132">接続に使用する Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントには次のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="7dcda-132">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must:</span></span>  
  
-   <span data-ttu-id="7dcda-133">PAL のメンバーである。</span><span class="sxs-lookup"><span data-stu-id="7dcda-133">Be a member of the PAL.</span></span>  
  
-   <span data-ttu-id="7dcda-134">パブリケーション データベースのユーザーに関連付けられたログインである。</span><span class="sxs-lookup"><span data-stu-id="7dcda-134">Be a login associated with a user in the publication database.</span></span>  
  
-   <span data-ttu-id="7dcda-135">ディストリビューション データベースのユーザー (ゲスト ユーザーでも可) に関連付けられたログインである。</span><span class="sxs-lookup"><span data-stu-id="7dcda-135">Be a login associated with a user in the distribution database (the user can be the Guest user).</span></span>  
  
-   <span data-ttu-id="7dcda-136">スナップショット共有の読み取り権限を持っている。</span><span class="sxs-lookup"><span data-stu-id="7dcda-136">Have read permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="7dcda-137">**[サブスクライバーに接続]**</span><span class="sxs-lookup"><span data-stu-id="7dcda-137">**Connect to the Subscriber**</span></span>  
 <span data-ttu-id="7dcda-138">プル サブスクリプションでは、サブスクライバーへの接続は常に **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="7dcda-138">For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="7dcda-139">プッシュ サブスクリプションの場合、マージ エージェントでパブリケーションおよびディストリビューターへの接続を作成するには、 **[プロセス アカウント]** テキスト ボックスで指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7dcda-139">For push subscriptions, select whether the Merge Agent should make connections to the Publisher and Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="7dcda-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7dcda-140">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dcda-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7dcda-141">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="7dcda-142">サブスクライバーへの接続に使用される Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントは、少なくとも、サブスクリプション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dcda-142">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dcda-143">参照</span><span class="sxs-lookup"><span data-stu-id="7dcda-143">See Also</span></span>  
 <span data-ttu-id="7dcda-144">[レプリケーションのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="7dcda-144">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="7dcda-145">[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="7dcda-145">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="7dcda-146">[レプリケーション エージェントの概要](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="7dcda-146">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 <span data-ttu-id="7dcda-147">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="7dcda-147">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="7dcda-148">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="7dcda-148">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
