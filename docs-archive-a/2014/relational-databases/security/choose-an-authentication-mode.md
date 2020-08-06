---
title: 認証モードの選択 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.ins.instwizard.authenticationmode.f1
helpviewer_keywords:
- sa account
- authentication modes
- trusted connection
- SQL Server Installation Wizard, Authentication Mode page
- choose authentication mode
- authentication [SQL Server], choosing a mode
- Windows authentication [SQL Server]
- mixed mode authentication
- mixed authentication mode
- SQL authentication mode
ms.assetid: ff7a6a48-3d38-4209-aa0f-7d6c0a8c64ef
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 973d1ef75512f44c5dd7bbff844b72525554082e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717678"
---
# <a name="choose-an-authentication-mode"></a><span data-ttu-id="94f18-102">認証モードの選択</span><span class="sxs-lookup"><span data-stu-id="94f18-102">Choose an Authentication Mode</span></span>
  <span data-ttu-id="94f18-103">セットアップ中に、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の認証モードを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-103">During setup, you must select an authentication mode for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="94f18-104">選択できるモードは、Windows 認証モードと混合モードの 2 つです。</span><span class="sxs-lookup"><span data-stu-id="94f18-104">There are two possible modes: Windows Authentication mode and mixed mode.</span></span> <span data-ttu-id="94f18-105">Windows 認証モードを選択すると、Windows 認証が有効になり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が無効になります。</span><span class="sxs-lookup"><span data-stu-id="94f18-105">Windows Authentication mode enables Windows Authentication and disables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="94f18-106">混合モードを選択すると、Windows 認証と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証の両方が有効になります。</span><span class="sxs-lookup"><span data-stu-id="94f18-106">Mixed mode enables both Windows Authentication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="94f18-107">Windows 認証は常に使用可能であり、無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="94f18-107">Windows Authentication is always available and cannot be disabled.</span></span>  
  
## <a name="configuring-the-authentication-mode"></a><span data-ttu-id="94f18-108">認証モードの構成</span><span class="sxs-lookup"><span data-stu-id="94f18-108">Configuring the Authentication Mode</span></span>  
 <span data-ttu-id="94f18-109">セットアップ中に混合モード認証を選択した場合は、sa という組み込みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者アカウントの強力なパスワードを入力して確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-109">If you select Mixed Mode Authentication during setup, you must provide and then confirm a strong password for the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named sa.</span></span> <span data-ttu-id="94f18-110">sa アカウントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="94f18-110">The sa account connects by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="94f18-111">セットアップ中に Windows 認証を選択した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証用に sa アカウントが作成されますが、無効になっています。</span><span class="sxs-lookup"><span data-stu-id="94f18-111">If you select Windows Authentication during setup, Setup creates the sa account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but it is disabled.</span></span> <span data-ttu-id="94f18-112">後で混合モード認証に変更し、sa アカウントを使用する場合に、アカウントを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-112">If you later change to Mixed Mode Authentication and you want to use the sa account, you must enable the account.</span></span> <span data-ttu-id="94f18-113">任意の Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントは、システム管理者として構成できます。</span><span class="sxs-lookup"><span data-stu-id="94f18-113">Any Windows or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account can be configured as a system administrator.</span></span> <span data-ttu-id="94f18-114">sa アカウントはよく知られているため、悪意のあるユーザーの攻撃対象となることが少なくありません。そのため、アプリケーションで必要とならない限り、sa アカウントを有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="94f18-114">Because the sa account is well known and often targeted by malicious users, do not enable the sa account unless your application requires it.</span></span> <span data-ttu-id="94f18-115">また、sa アカウントでは、パスワードを空白のままにしたり、推測しやすいパスワードを設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="94f18-115">Never set a blank or weak password for the sa account.</span></span> <span data-ttu-id="94f18-116">Windows 認証モードから混合モード認証に変更して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、「 [サーバーの認証モードの変更](../../database-engine/configure-windows/change-server-authentication-mode.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="94f18-116">To change from Windows Authentication mode to Mixed Mode Authentication and use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="connecting-through-windows-authentication"></a><span data-ttu-id="94f18-117">Windows 認証を使用した接続</span><span class="sxs-lookup"><span data-stu-id="94f18-117">Connecting Through Windows Authentication</span></span>  
 <span data-ttu-id="94f18-118">Windows ユーザー アカウントでユーザーが接続すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はオペレーティング システムの Windows プリンシパル トークンを使用してアカウント名とパスワードを検証します。</span><span class="sxs-lookup"><span data-stu-id="94f18-118">When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validates the account name and password using the Windows principal token in the operating system.</span></span> <span data-ttu-id="94f18-119">つまり、ユーザーの ID は Windows によって確認されます。</span><span class="sxs-lookup"><span data-stu-id="94f18-119">This means that the user identity is confirmed by Windows.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="94f18-120">では、パスワードが要求されず、ID の検証も行われません。</span><span class="sxs-lookup"><span data-stu-id="94f18-120">does not ask for the password, and does not perform the identity validation.</span></span> <span data-ttu-id="94f18-121">Windows 認証は、既定の認証モードであり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証よりもはるかに安全性に優れています。</span><span class="sxs-lookup"><span data-stu-id="94f18-121">Windows Authentication is the default authentication mode, and is much more secure than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="94f18-122">Windows 認証では、Kerberos セキュリティ プロトコルを利用し、強力なパスワードに対して複雑な検証を行うという点に関して、パスワード ポリシーが強化されています。また、アカウント ロックアウトの機能を提供し、パスワード有効期限にも対応しています。</span><span class="sxs-lookup"><span data-stu-id="94f18-122">Windows Authentication uses Kerberos security protocol, provides password policy enforcement with regard to complexity validation for strong passwords, provides support for account lockout, and supports password expiration.</span></span> <span data-ttu-id="94f18-123">Windows 認証を使用して行われた接続は、信頼関係接続と呼ばれることがあります。これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では Windows が提供する資格情報を信頼しているためです。</span><span class="sxs-lookup"><span data-stu-id="94f18-123">A connection made using Windows Authentication is sometimes called a trusted connection, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trusts the credentials provided by Windows.</span></span>  
  
 <span data-ttu-id="94f18-124">Windows 認証を使用することにより、Windows グループをドメイン レベルで作成できます。また、グループ全体に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログインを作成できます。</span><span class="sxs-lookup"><span data-stu-id="94f18-124">By using Windows Authentication, Windows groups can be created at the domain level, and a login can be created on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the entire group.</span></span> <span data-ttu-id="94f18-125">ドメイン レベルでアクセスを管理すると、アカウント管理を簡素化できます。</span><span class="sxs-lookup"><span data-stu-id="94f18-125">Managing access from at the domain level can simplify account administration.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="connecting-through-sql-server-authentication"></a><span data-ttu-id="94f18-126">SQL Server 認証を使用した接続</span><span class="sxs-lookup"><span data-stu-id="94f18-126">Connecting Through SQL Server Authentication</span></span>  
 <span data-ttu-id="94f18-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用すると、Windows ユーザー アカウントに基づかないログインが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に作成されます。</span><span class="sxs-lookup"><span data-stu-id="94f18-127">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, logins are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are not based on Windows user accounts.</span></span> <span data-ttu-id="94f18-128">ユーザー名とパスワードの両方が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して作成され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納されます。</span><span class="sxs-lookup"><span data-stu-id="94f18-128">Both the user name and the password are created by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="94f18-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続するユーザーは、接続するたびに資格情報 (ログインとパスワード) を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-129">Users connecting using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication must provide their credentials (login and password) every time that they connect.</span></span> <span data-ttu-id="94f18-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントに強力なパスワードを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-130">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accounts.</span></span> <span data-ttu-id="94f18-131">強力なパスワードのガイドラインについては、「 [強力なパスワード](strong-passwords.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94f18-131">For strong password guidelines, see [Strong Passwords](strong-passwords.md).</span></span>  
  
 <span data-ttu-id="94f18-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインでは、省略可能な 3 つのパスワード ポリシーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="94f18-132">Three optional password policies are available for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="94f18-133">[ユーザーは次回ログイン時にパスワードを変更する]</span><span class="sxs-lookup"><span data-stu-id="94f18-133">User must change password at next login</span></span>  
  
     <span data-ttu-id="94f18-134">ユーザーは、次回接続するときにパスワードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-134">Requires the user to change the password the next time that the user connects.</span></span> <span data-ttu-id="94f18-135">パスワードを変更する機能は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に用意されています。</span><span class="sxs-lookup"><span data-stu-id="94f18-135">The ability to change the password is provided by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="94f18-136">このオプションが使用されている場合、サード パーティのソフトウェア開発者はこの機能を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-136">Third-party software developers should provide this feature if this option is used.</span></span>  
  
-   <span data-ttu-id="94f18-137">[パスワードの期限を適用する]</span><span class="sxs-lookup"><span data-stu-id="94f18-137">Enforce password expiration</span></span>  
  
     <span data-ttu-id="94f18-138">コンピューターのパスワードの有効期限ポリシーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに適用されます。</span><span class="sxs-lookup"><span data-stu-id="94f18-138">The maximum password age policy of the computer is enforced for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="94f18-139">[パスワード ポリシーを適用する]</span><span class="sxs-lookup"><span data-stu-id="94f18-139">Enforce password policy</span></span>  
  
     <span data-ttu-id="94f18-140">コンピューターの Windows のパスワード ポリシーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに適用されます。</span><span class="sxs-lookup"><span data-stu-id="94f18-140">The Windows password policies of the computer are enforced for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="94f18-141">これには、パスワードの長さおよび複雑さが含まれます。</span><span class="sxs-lookup"><span data-stu-id="94f18-141">This includes password length and complexity.</span></span> <span data-ttu-id="94f18-142">この機能は、 `NetValidatePasswordPolicy` 以降のバージョンのみで使用できる [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] API に依存します。</span><span class="sxs-lookup"><span data-stu-id="94f18-142">This functionality depends on the `NetValidatePasswordPolicy` API, which is only available in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] and later versions.</span></span>  
  
#### <a name="to-determine-the-password-policies-of-the-local-computer"></a><span data-ttu-id="94f18-143">ローカル コンピューターのパスワード ポリシーを確認するには</span><span class="sxs-lookup"><span data-stu-id="94f18-143">To determine the password policies of the local computer</span></span>  
  
1.  <span data-ttu-id="94f18-144">**[スタート]** メニューの **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94f18-144">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="94f18-145">[**実行**] ダイアログボックスで、「」と入力し、 `secpol.msc` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94f18-145">In the **Run** dialog box, type `secpol.msc`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="94f18-146">**[ローカル セキュリティ設定]** アプリケーションで、 **[セキュリティの設定]** 、 **[アカウント ポリシー]** の順に展開して、 **[パスワードのポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94f18-146">In the **Local Security Settings** application, expand **Security Settings**, expand **Account Policies**, and then click **Password Policy**.</span></span>  
  
     <span data-ttu-id="94f18-147">結果ペインに、パスワードのポリシーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="94f18-147">The password policies are described in the results pane.</span></span>  
  
### <a name="disadvantages-of-sql-server-authentication"></a><span data-ttu-id="94f18-148">SQL Server 認証の欠点</span><span class="sxs-lookup"><span data-stu-id="94f18-148">Disadvantages of SQL Server Authentication</span></span>  
  
-   <span data-ttu-id="94f18-149">Windows のログインとパスワードを持っている Windows ドメイン ユーザーの場合、接続するために別の ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) ログインとパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-149">If a user is a Windows domain user who has a login and password for Windows, he must still provide another ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) login and password to connect.</span></span> <span data-ttu-id="94f18-150">多くのユーザーにとって、複数の名前とパスワードを把握しておくことは困難です。</span><span class="sxs-lookup"><span data-stu-id="94f18-150">Keeping track of multiple names and passwords is difficult for many users.</span></span> <span data-ttu-id="94f18-151">データベースに接続するたびに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の資格情報を入力する必要があるのは面倒な場合があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-151">Having to provide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credentials every time that one connects to the database can be annoying.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="94f18-152">認証では、Kerberos セキュリティ プロトコルを使用できません。</span><span class="sxs-lookup"><span data-stu-id="94f18-152">Authentication cannot use Kerberos security protocol.</span></span>  
  
-   <span data-ttu-id="94f18-153">Windows には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインで使用できない、追加のパスワード ポリシーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="94f18-153">Windows offers additional password policies that are not available for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="94f18-154">接続時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログインの暗号化されたパスワードをネットワーク上で渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f18-154">The encrypted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login password, must be passed over the network at the time of the connection.</span></span> <span data-ttu-id="94f18-155">自動的に接続する一部のアプリケーションでは、クライアントでパスワードが保存されます。</span><span class="sxs-lookup"><span data-stu-id="94f18-155">Some applications that connect automatically will store the password at the client.</span></span> <span data-ttu-id="94f18-156">これらは追加の攻撃ポイントとなります。</span><span class="sxs-lookup"><span data-stu-id="94f18-156">These are additional attack points.</span></span>  
  
### <a name="advantages-of-sql-server-authentication"></a><span data-ttu-id="94f18-157">SQL Server 認証の利点</span><span class="sxs-lookup"><span data-stu-id="94f18-157">Advantages of SQL Server Authentication</span></span>  
  
-   <span data-ttu-id="94f18-158">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、古いアプリケーションや、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を必要とする、サード パーティが提供するアプリケーションをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="94f18-158">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support older applications and applications provided by third parties that require [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
-   <span data-ttu-id="94f18-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、すべてのユーザーが Windows ドメインで認証されていない、オペレーティング システムが混在する環境をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="94f18-159">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support environments with mixed operating systems, where all users are not authenticated by a Windows domain.</span></span>  
  
-   <span data-ttu-id="94f18-160">ユーザーが不明または信頼されていないドメインから接続できる場合。</span><span class="sxs-lookup"><span data-stu-id="94f18-160">Allows users to connect from unknown or untrusted domains.</span></span> <span data-ttu-id="94f18-161">たとえば、既存の顧客が、割り当てられた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用して接続し、発注状況を確認するアプリケーションの場合です。</span><span class="sxs-lookup"><span data-stu-id="94f18-161">For instance, an application where established customers connect with assigned [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins to receive the status of their orders.</span></span>  
  
-   <span data-ttu-id="94f18-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ユーザーが独自の ID を作成する Web ベースのアプリケーションをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="94f18-162">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support Web-based applications where users create their own identities.</span></span>  
  
-   <span data-ttu-id="94f18-163">ソフトウェア開発者は、事前に設定された既知の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに基づいた、複雑な権限の階層を使用してアプリケーションを配布できます。</span><span class="sxs-lookup"><span data-stu-id="94f18-163">Allows software developers to distribute their applications by using a complex permission hierarchy based on known, preset [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="94f18-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされているコンピューターのローカル管理者の権限は制限されません。</span><span class="sxs-lookup"><span data-stu-id="94f18-164">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication does not limit the permissions of local administrators on the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f18-165">参照</span><span class="sxs-lookup"><span data-stu-id="94f18-165">See Also</span></span>  
 [<span data-ttu-id="94f18-166">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="94f18-166">Security Considerations for a SQL Server Installation</span></span>](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  