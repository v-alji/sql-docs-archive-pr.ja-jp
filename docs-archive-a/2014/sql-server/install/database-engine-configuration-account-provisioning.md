---
title: データベースエンジンの構成-アカウントの準備 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 834b26bc-49de-4033-88d5-6aa7b1609720
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7885bdda72668ac96e90b0900772a4f56575d5fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631506"
---
# <a name="database-engine-configuration---account-provisioning"></a><span data-ttu-id="3ee8c-102">データベース エンジンの構成 - アカウントの準備</span><span class="sxs-lookup"><span data-stu-id="3ee8c-102">Database Engine Configuration - Account Provisioning</span></span>
  <span data-ttu-id="3ee8c-103">このページは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ モードを設定し、Windows ユーザーまたはグループを [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の管理者として追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-103">Use this page to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security mode, and to add Windows users or groups as administrators of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="considerations-for-running-sscurrent"></a><span data-ttu-id="3ee8c-104">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の実行に関する注意点</span><span class="sxs-lookup"><span data-stu-id="3ee8c-104">Considerations for Running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span></span>  
 <span data-ttu-id="3ee8c-105">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 **のログインとして** BUILTIN\Administrators [!INCLUDE[ssDE](../../includes/ssde-md.md)] グループが準備され、ローカル Administrators グループのメンバーは、管理者資格情報を使用してログインできました。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-105">On previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BUILTIN\Administrators** group was provisioned as a login in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and members of the local Administrators group could login using their Administrator credentials.</span></span> <span data-ttu-id="3ee8c-106">しかし、引き上げられたアクセス許可を使用するのはベスト プラクティスではありません。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-106">Using elevated permissions is not a best practice.</span></span> <span data-ttu-id="3ee8c-107">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 **BUILTIN\Administrators** グループはログインとして準備されていません。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-107">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] the **BUILTIN\Administrators** group is not provisioned as a login.</span></span> <span data-ttu-id="3ee8c-108">したがって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいインスタンスのインストール時に、管理ユーザーごとに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ログインを作成し、そのログインを sysadmin 固定サーバー ロールに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-108">As a result, you should create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for each administrative user, and add that login to the sysadmin fixed server role during installation of a new instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3ee8c-109">また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行に使用する Windows アカウントに対しても、同様の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-109">You should also do this for Windows accounts that are used to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent jobs.</span></span> <span data-ttu-id="3ee8c-110">それらのジョブには、レプリケーション エージェント ジョブも含まれます。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-110">These include replication agent jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ee8c-111">Options</span><span class="sxs-lookup"><span data-stu-id="3ee8c-111">Options</span></span>  
 <span data-ttu-id="3ee8c-112">**[セキュリティ モード]** : インストール用に Windows 認証または混合モード認証を選択します。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-112">**Security Mode** - Select Windows Authentication or Mixed Mode Authentication for your installation.</span></span>  
  
 <span data-ttu-id="3ee8c-113">**[Windows プリンシパルの準備]** : 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、Windows の Builtin\Administrator ローカル グループが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin サーバー ロールに配置されました。これは、Windows 管理者に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスへのアクセス許可を付与する効果的な方法でした。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-113">**Windows Principal Provisioning** - In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Windows Builtin\Administrator local group was placed into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin server role, effectively granting Windows administrators access to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3ee8c-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、Builtin\Administrator グループは sysadmin  サーバー ロールで提供されません。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-114">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the Builtin\Administrator group is not provisioned in the sysadmin server role.</span></span> <span data-ttu-id="3ee8c-115">代わりに、セットアップ時に新規インストール用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者を明示的に用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-115">Instead, you should explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ee8c-116">セットアップ時に新規インストール用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者を明示的に用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-116">You must explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span> <span data-ttu-id="3ee8c-117">セットアップは、この手順を完了するまで続行できません。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-117">Setup will not allow you to continue until you complete this step.</span></span>  
  
 <span data-ttu-id="3ee8c-118">**[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者の指定]**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの Windows プリンシパルを少なくとも 1 つ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-118">**Specify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrators** - You must specify at least one Windows principal for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3ee8c-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行しているアカウントを追加するには、**[現在のユーザー]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-119">To add the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup is running, click the **Current User** button.</span></span> <span data-ttu-id="3ee8c-120">システム管理者の一覧に対してアカウントを追加または削除するには、 **[追加]** または **[削除]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスについて管理者特権を持っているユーザー、グループ、またはコンピューターの一覧を編集します。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-120">To add or remove accounts from the list of system administrators, click **Add** or **Remove**, and then edit the list of users, groups, or computers that will have administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3ee8c-121">一覧の編集が完了したら、 **[OK]** をクリックし、構成ダイアログ ボックスで管理者の一覧を確認します。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-121">When you are finished editing the list, click **OK**, then verify the list of administrators in the configuration dialog.</span></span> <span data-ttu-id="3ee8c-122">一覧が完成したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-122">When the list is complete, click **Next**.</span></span>  
  
 <span data-ttu-id="3ee8c-123">混合モード認証を選択した場合は、組み込みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者 (SA) アカウントのログオン資格情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-123">If you select Mixed Mode Authentication, you must provide logon credentials for the builtin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (SA) account.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 <span data-ttu-id="3ee8c-124">**Windows 認証モード**</span><span class="sxs-lookup"><span data-stu-id="3ee8c-124">**Windows Authentication Mode**</span></span>  
 <span data-ttu-id="3ee8c-125">Windows ユーザー アカウントでユーザーが接続すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はオペレーティング システムの Windows プリンシパル トークンを使用してアカウント名とパスワードを検証します。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-125">When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validates the account name and password using the Windows principal token in the operating system.</span></span> <span data-ttu-id="3ee8c-126">これは既定の認証モードで、混合モードよりはるかに安全性に優れています。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-126">This is the default authentication mode, and is much more secure than Mixed Mode.</span></span> <span data-ttu-id="3ee8c-127">Windows 認証では、Kerberos セキュリティ プロトコルを利用し、強力なパスワードに対して複雑な検証を行うという点で、パスワード ポリシーが強化されています。また、アカウント ロックアウトの機能を提供し、パスワード有効期限にも対応しています。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-127">Windows Authentication utilizes Kerberos security protocol, provides password policy enforcement in terms of complexity validation for strong passwords, provides support for account lockout, and supports password expiration.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]<span data-ttu-id="3ee8c-128">sa パスワードを空白のままにしないでください。また、推測しやすいパスワードを設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-128">Never set a blank or weak sa password.</span></span>  
  
 <span data-ttu-id="3ee8c-129">**混合モード (Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証)**</span><span class="sxs-lookup"><span data-stu-id="3ee8c-129">**Mixed Mode (Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication)**</span></span>  
 <span data-ttu-id="3ee8c-130">Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用してユーザー接続を許可します。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-130">Allows users to connect by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="3ee8c-131">Windows ユーザー アカウントで接続するユーザーは、Windows によって検証される信頼関係接続を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-131">Users who connect through a Windows user account can use trusted connections that are validated by Windows.</span></span>  
  
 <span data-ttu-id="3ee8c-132">混合モード認証を選択する必要があり、レガシ アプリケーションに対応するために SQL ログインを使用する必要もある場合は、必ずすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントに強力なパスワードを設定してください。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-132">If you must choose Mixed Mode Authentication and you have a requirement for using SQL logins to accommodate legacy applications, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accounts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3ee8c-133">認証は旧バージョンとの互換性を維持するためだけに提供されます。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-133">Authentication is provided for backward compatibility only.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="3ee8c-134">**パスワードの入力**</span><span class="sxs-lookup"><span data-stu-id="3ee8c-134">**Enter Password**</span></span>  
 <span data-ttu-id="3ee8c-135">システム管理者 (sa) ログインを入力および確認します。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-135">Enter and confirm the system administrator (sa) login.</span></span> <span data-ttu-id="3ee8c-136">パスワードは侵入者に対する防御の最前線であるため、システムのセキュリティにとって強力なパスワードを設定することは不可欠です。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-136">Passwords are the first line of defense against intruders, so setting strong passwords is essential to the security of your system.</span></span> <span data-ttu-id="3ee8c-137">sa パスワードを空白のままにしないでください。また、推測しやすいパスワードを設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-137">Never set a blank or weak sa password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3ee8c-138">パスワードは、文字、記号、数字の組み合わせを含む 1 ～ 128 文字で指定できます。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-138">passwords can contain from 1 to 128 characters, including any combination of letters, symbols, and numbers.</span></span> <span data-ttu-id="3ee8c-139">混合モード認証を選択する場合、インストール ウィザードの次のページに進む前に、強力な sa パスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-139">If you choose Mixed Mode authentication, you must enter a strong sa password before you can continue to the next page of the Installation Wizard.</span></span>  
  
 <span data-ttu-id="3ee8c-140">**強力なパスワードのガイドライン**</span><span class="sxs-lookup"><span data-stu-id="3ee8c-140">**Strong Password Guidelines**</span></span>  
 <span data-ttu-id="3ee8c-141">強力なパスワードとは、他人によってたやすく推測されず、コンピューター プログラムを使用して簡単にはハッキングされないパスワードです。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-141">Strong passwords are not readily guessed by a person, and are not easily hacked using a computer program.</span></span> <span data-ttu-id="3ee8c-142">強力なパスワードでは、次のような禁止された条件または用語を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-142">Strong passwords cannot use prohibited conditions or terms, including:</span></span>  
  
-   <span data-ttu-id="3ee8c-143">空白または NULL 条件</span><span class="sxs-lookup"><span data-stu-id="3ee8c-143">A blank or NULL condition</span></span>  
  
-   <span data-ttu-id="3ee8c-144">"Password"</span><span class="sxs-lookup"><span data-stu-id="3ee8c-144">"Password"</span></span>  
  
-   <span data-ttu-id="3ee8c-145">"Admin"</span><span class="sxs-lookup"><span data-stu-id="3ee8c-145">"Admin"</span></span>  
  
-   <span data-ttu-id="3ee8c-146">"Administrator"</span><span class="sxs-lookup"><span data-stu-id="3ee8c-146">"Administrator"</span></span>  
  
-   <span data-ttu-id="3ee8c-147">"sa"</span><span class="sxs-lookup"><span data-stu-id="3ee8c-147">"sa"</span></span>  
  
-   <span data-ttu-id="3ee8c-148">"sysadmin"</span><span class="sxs-lookup"><span data-stu-id="3ee8c-148">"sysadmin"</span></span>  
  
 <span data-ttu-id="3ee8c-149">強力なパスワードには、インストール コンピューターに関連付けられた次のような用語を指定できません。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-149">A strong password cannot be the following terms associated with the installation computer:</span></span>  
  
-   <span data-ttu-id="3ee8c-150">現在、マシンにログオンしているユーザーの名前</span><span class="sxs-lookup"><span data-stu-id="3ee8c-150">The name of the user currently logged onto the machine.</span></span>  
  
-   <span data-ttu-id="3ee8c-151">コンピューター名</span><span class="sxs-lookup"><span data-stu-id="3ee8c-151">The computer name.</span></span>  
  
 <span data-ttu-id="3ee8c-152">強力なパスワードは、長さ 9 文字以上で、以下の 4 つの条件のうち 3 つ以上を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-152">A strong password must be more than 8 characters in length and satisfy at least three of the following four criteria:</span></span>  
  
-   <span data-ttu-id="3ee8c-153">大文字を含んでいる。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-153">It must contain uppercase letters.</span></span>  
  
-   <span data-ttu-id="3ee8c-154">小文字を含んでいる。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-154">It must contain lowercase letters.</span></span>  
  
-   <span data-ttu-id="3ee8c-155">数字を含んでいる。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-155">It must contain numbers.</span></span>  
  
-   <span data-ttu-id="3ee8c-156">#、%、^ など、英数字以外の文字を含んでいる。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-156">It must contain non-alphanumeric characters; for example, #, %, or ^.</span></span>  
  
 <span data-ttu-id="3ee8c-157">このページで入力するパスワードは、強力なパスワード ポリシーの要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-157">Passwords entered on this page must meet strong password policy requirements.</span></span> <span data-ttu-id="3ee8c-158">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用したオートメーションを使用している場合、必ず強力なパスワード ポリシーの要件を満たすパスワードを指定してください。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-158">If you have any automation that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, ensure that the password meets strong password policy requirements.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="3ee8c-159">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="3ee8c-159">Related Content</span></span>  
 <span data-ttu-id="3ee8c-160">Windows 認証と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のどちらを選択するかについて詳しくは、 **オンライン ブックの「** 認証モードの選択 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-160">For more information about choosing Windows Authentication vs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, see the topic **Choose an Authentication Mode** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="3ee8c-161">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]を実行するアカウントの選択の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「**Windows サービス アカウントと権限の構成**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ee8c-161">For more information about choosing an account to run the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see the topic **Configure Windows Service Accounts and Permissions** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee8c-162">参照</span><span class="sxs-lookup"><span data-stu-id="3ee8c-162">See Also</span></span>  
 [<span data-ttu-id="3ee8c-163">Windows サービス アカウントと権限の構成</span><span class="sxs-lookup"><span data-stu-id="3ee8c-163">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
