---
title: ディストリビューション エージェント セキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.DA.f1
helpviewer_keywords:
- Distribution Agent Security dialog box
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4342d44a221d9b816a95a283917f005eb018827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632381"
---
# <a name="distribution-agent-security"></a><span data-ttu-id="ace15-102">[ディストリビューション エージェント セキュリティ]</span><span class="sxs-lookup"><span data-stu-id="ace15-102">Distribution Agent Security</span></span>
  <span data-ttu-id="ace15-103">**[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスを使用すると、ディストリビューション エージェントを実行する Windows アカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ace15-103">The **Distribution Agent Security** dialog box allows you to specify the Windows account under which the Distribution Agent runs.</span></span> <span data-ttu-id="ace15-104">ディストリビューション エージェントは、プッシュ サブスクリプションのディストリビューターと、プル サブスクリプションのサブスクライバーで動作します。</span><span class="sxs-lookup"><span data-stu-id="ace15-104">The Distribution Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions.</span></span> <span data-ttu-id="ace15-105">エージェント プロセスはこのアカウントで実行されるため、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントは、 *プロセス アカウント*としても参照されます。</span><span class="sxs-lookup"><span data-stu-id="ace15-105">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span> <span data-ttu-id="ace15-106">ダイアログ ボックスで使用できる追加オプションは、次に示すアクセスの方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ace15-106">Additional options available in the dialog box depend on how you access it:</span></span>  
  
-   <span data-ttu-id="ace15-107">サブスクリプションの新規作成ウィザードからこのダイアログ ボックスにアクセスする場合、サブスクライバー (プッシュ サブスクリプション) またはディストリビューター (プル サブスクリプション) への接続を作成するディストリビューション エージェントのコンテキストを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ace15-107">If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Distribution Agent makes connections to the Subscriber (for push subscriptions) or the Distributor (for pull subscriptions).</span></span> <span data-ttu-id="ace15-108">接続は、Windows アカウントを借用して作成されるか、指定した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントのコンテキストで作成されます。</span><span class="sxs-lookup"><span data-stu-id="ace15-108">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
-   <span data-ttu-id="ace15-109">**[サブスクリプションのプロパティ]** ダイアログ ボックスからこのダイアログ ボックスにアクセスする場合、 **[サブスクライバー接続]** 行または **[ディストリビューター接続]** 行のプロパティ ボタン ( **[...]** ) をクリックして、ディストリビューション エージェントが接続を作成するコンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="ace15-109">If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Distribution Agent makes connections by clicking the properties button (**...**) in the **Subscriber Connection** or **Distributor Connection** row of that dialog box.</span></span> <span data-ttu-id="ace15-110">**[サブスクリプションのプロパティ]** ダイアログ ボックスへのアクセスの詳細については、「[プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)」および「[プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ace15-110">For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and how to: [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
 <span data-ttu-id="ace15-111">各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace15-111">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="ace15-112">アカウントとパスワードは、エージェントが実行されるまで検証されません。</span><span class="sxs-lookup"><span data-stu-id="ace15-112">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ace15-113">オプション</span><span class="sxs-lookup"><span data-stu-id="ace15-113">Options</span></span>  
 <span data-ttu-id="ace15-114">**Process Account**</span><span class="sxs-lookup"><span data-stu-id="ace15-114">**Process Account**</span></span>  
 <span data-ttu-id="ace15-115">ディストリビューション エージェントが実行される Windows アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="ace15-115">Enter a Windows account under which the Distribution Agent runs:</span></span>  
  
-   <span data-ttu-id="ace15-116">プッシュ サブスクリプションでは、アカウントには次のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="ace15-116">For push subscriptions, the account must:</span></span>  
  
    -   <span data-ttu-id="ace15-117">最低でも、ディストリビューション データベースで **db_owner** 固定データベース ロールのメンバーである。</span><span class="sxs-lookup"><span data-stu-id="ace15-117">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
    -   <span data-ttu-id="ace15-118">パブリケーション アクセス リスト (PAL) のメンバーになれる。</span><span class="sxs-lookup"><span data-stu-id="ace15-118">Be a member of the publication access list (PAL).</span></span>  
  
    -   <span data-ttu-id="ace15-119">スナップショット共有の読み取り権限を持っている。</span><span class="sxs-lookup"><span data-stu-id="ace15-119">Have read permissions on the snapshot share.</span></span>  
  
    -   <span data-ttu-id="ace15-120">サブスクリプションが非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーの場合、サブスクライバーの OLE DB プロバイダーのインストール ディレクトリへの読み取り権限を持つ。</span><span class="sxs-lookup"><span data-stu-id="ace15-120">Have read permissions on the install directory of the OLE DB provider for the Subscriber if the subscription is for a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber.</span></span>  
  
-   <span data-ttu-id="ace15-121">プル サブスクリプションでは、アカウントは少なくとも、サブスクリプション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace15-121">For pull subscriptions, the account must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
 <span data-ttu-id="ace15-122">接続を作成するときにプロセス アカウントを借用する場合、追加の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ace15-122">Additional permissions are required if the process account is impersonated when connections are made.</span></span> <span data-ttu-id="ace15-123">後述の **[ディストリビューターに接続]** と **[サブスクライバーに接続]** を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ace15-123">See the **Connect to the Distributor** and **Connect to the Subscriber** sections below.</span></span>  
  
 <span data-ttu-id="ace15-124">ディストリビューション エージェントは  **のインスタンスでは実行できないため、** [プロセス アカウント][!INCLUDE[msCoName](../../includes/msconame-md.md)] は、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] へのプル サブスクリプションには指定できません。</span><span class="sxs-lookup"><span data-stu-id="ace15-124">**Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Distribution Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
 <span data-ttu-id="ace15-125">**[パスワード]** と **[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="ace15-125">**Password** and **Confirm Password**</span></span>  
 <span data-ttu-id="ace15-126">Windows アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ace15-126">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="ace15-127">**[ディストリビューターに接続]**</span><span class="sxs-lookup"><span data-stu-id="ace15-127">**Connect to the Distributor**</span></span>  
 <span data-ttu-id="ace15-128">プッシュ サブスクリプションでは、ディストリビューターへの接続は常に **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="ace15-128">For push subscriptions, connections to the Distributor are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="ace15-129">プル サブスクリプションでは、ディストリビューション エージェントが、 **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアカウントを使用してディストリビューターへの接続を作成する必要があるかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="ace15-129">For pull subscriptions, select whether the Distribution Agent should make connections to the Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="ace15-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ace15-130">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ace15-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ace15-131">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="ace15-132">接続に使用する Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントには次のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="ace15-132">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must:</span></span>  
  
-   <span data-ttu-id="ace15-133">PAL のメンバーである。</span><span class="sxs-lookup"><span data-stu-id="ace15-133">Be a member of the PAL.</span></span>  
  
-   <span data-ttu-id="ace15-134">スナップショット共有の読み取り権限を持っている。</span><span class="sxs-lookup"><span data-stu-id="ace15-134">Have read permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="ace15-135">**[サブスクライバーに接続]**</span><span class="sxs-lookup"><span data-stu-id="ace15-135">**Connect to the Subscriber**</span></span>  
 <span data-ttu-id="ace15-136">プル サブスクリプションでは、サブスクライバーへの接続は常に **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="ace15-136">For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="ace15-137">プッシュ サブスクリプションでは、次のように、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーと非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーのオプションが異なります。</span><span class="sxs-lookup"><span data-stu-id="ace15-137">For push subscriptions, the options are different for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers and non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="ace15-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーでは、ディストリビューション エージェントが、 **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアカウントを使用してサブスクライバーへの接続を作成する必要があるかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="ace15-138">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers: select whether the Distribution Agent should make connections to the Subscriber by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="ace15-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ace15-139">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ace15-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ace15-140">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
     <span data-ttu-id="ace15-141">サブスクライバーへの接続に使用される Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントは、少なくとも、サブスクリプション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace15-141">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
-   <span data-ttu-id="ace15-142">非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーでは、ディストリビューション エージェントがサブスクライバーに接続するときに使用する必要のあるサブスクライバーでデータベース ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="ace15-142">For non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, specify the database login at the Subscriber that should be used when the Distribution Agent connects to the Subscriber.</span></span> <span data-ttu-id="ace15-143">ログインは、サブスクリプション データベースにオブジェクトを作成するための十分な権限を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace15-143">The login should have sufficient permissions to create objects in the subscription database.</span></span> <span data-ttu-id="ace15-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバの詳細については、「[SQL Server 以外のサブスクライバーのサブスクリプションの作成](create-a-subscription-for-a-non-sql-server-subscriber.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ace15-144">For more information about configuring non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, see [Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
 <span data-ttu-id="ace15-145">**[追加の接続オプション]**</span><span class="sxs-lookup"><span data-stu-id="ace15-145">**Additional connection options**</span></span>  
 <span data-ttu-id="ace15-146">非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーのみです。</span><span class="sxs-lookup"><span data-stu-id="ace15-146">Non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers only.</span></span> <span data-ttu-id="ace15-147">接続文字列の形式で、サブスクライバーの任意の接続オプションを指定します (Oracle では追加のオプションは不要)。</span><span class="sxs-lookup"><span data-stu-id="ace15-147">Specify any connection options for the Subscriber in the form of a connection string (Oracle does not require additional options).</span></span> <span data-ttu-id="ace15-148">各オプションはセミコロンで区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace15-148">Each option should be separated by a semi-colon.</span></span> <span data-ttu-id="ace15-149">次は、IBM DB2 接続文字列の例です (読みやすくするために改行されています)。</span><span class="sxs-lookup"><span data-stu-id="ace15-149">The following is an example of an IBM DB2 connection string (line breaks are for readability):</span></span>  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 <span data-ttu-id="ace15-150">文字列内のオプションの多くは、接続する DB2 サーバーに固有のものですが、 **Process Binary as Character** オプションは常に **False**に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace15-150">Most of the options in the string are specific to the DB2 server you are configuring, but the **Process Binary as Character** option should always be set to **False**.</span></span> <span data-ttu-id="ace15-151">サブスクリプション データベースを識別するため、 **Initial Catalog** オプションに値が必要です。</span><span class="sxs-lookup"><span data-stu-id="ace15-151">A value is required for the **Initial Catalog** option to identify the subscription database.</span></span> <span data-ttu-id="ace15-152">詳細については、「 [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ace15-152">For more information, see [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace15-153">参照</span><span class="sxs-lookup"><span data-stu-id="ace15-153">See Also</span></span>  
 <span data-ttu-id="ace15-154">[レプリケーションのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="ace15-154">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="ace15-155">[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="ace15-155">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="ace15-156">[レプリケーション エージェントの概要](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="ace15-156">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 <span data-ttu-id="ace15-157">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="ace15-157">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="ace15-158">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="ace15-158">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
