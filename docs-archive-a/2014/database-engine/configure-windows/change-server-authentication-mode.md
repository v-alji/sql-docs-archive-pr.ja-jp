---
title: サーバーの認証モードの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- authentication [SQL Server], changing modes
- server authentication mode [SQL Server]
- modifying server authentication mode
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8bda31ca7d0c5949173a9a3e5ea656c1757c04f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740453"
---
# <a name="change-server-authentication-mode"></a><span data-ttu-id="d9883-102">サーバーの認証モードの変更</span><span class="sxs-lookup"><span data-stu-id="d9883-102">Change Server Authentication Mode</span></span>
  <span data-ttu-id="d9883-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、サーバーの認証モードを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9883-103">This topic describes how to change the server authentication mode in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d9883-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] はインストール中に、 **[Windows 認証モード]** または **[SQL Server 認証モードと Windows 認証モード]** のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d9883-104">During installation, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] is set to either **Windows Authentication mode** or **SQL Server and Windows Authentication mode**.</span></span> <span data-ttu-id="d9883-105">インストール後は、認証モードをいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="d9883-105">After installation, you can change the authentication mode at any time.</span></span>  
  
 <span data-ttu-id="d9883-106">インストール中に **[Windows 認証モード]** を選択した場合、sa ログインは無効となり、パスワードはセットアップによって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d9883-106">If **Windows Authentication mode** is selected during installation, the sa login is disabled and a password is assigned by setup.</span></span> <span data-ttu-id="d9883-107">後で認証モードを **[SQL Server 認証モードと Windows 認証モード]** に変更しても、sa ログインは無効のままです。</span><span class="sxs-lookup"><span data-stu-id="d9883-107">If you later change authentication mode to **SQL Server and Windows Authentication mode**, the sa login remains disabled.</span></span> <span data-ttu-id="d9883-108">sa ログインを使用するには、ALTER LOGIN ステートメントを使用して、sa ログインを有効にし、新しいパスワードを割り当ててください。</span><span class="sxs-lookup"><span data-stu-id="d9883-108">To use the sa login, use the ALTER LOGIN statement to enable the sa login and assign a new password.</span></span> <span data-ttu-id="d9883-109">sa ログインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用しないとサーバーに接続できません。</span><span class="sxs-lookup"><span data-stu-id="d9883-109">The sa login can only connect to the server by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="d9883-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d9883-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d9883-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d9883-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d9883-112">Security</span><span class="sxs-lookup"><span data-stu-id="d9883-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d9883-113">**サーバーの認証モードを変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="d9883-113">**To change server authentication mode, using:**</span></span>  
  
     [<span data-ttu-id="d9883-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d9883-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d9883-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d9883-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d9883-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="d9883-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d9883-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d9883-117">Security</span></span>  
 <span data-ttu-id="d9883-118">sa アカウントは、よく知られた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントで、悪意のあるユーザーの攻撃対象となることが少なくありません。</span><span class="sxs-lookup"><span data-stu-id="d9883-118">The sa account is a well-known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account and it is often targeted by malicious users.</span></span> <span data-ttu-id="d9883-119">sa アカウントは、アプリケーションで必要とならない限り、有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="d9883-119">Do not enable the sa account unless your application requires it.</span></span> <span data-ttu-id="d9883-120">sa ログインには、複雑なパスワードを使用することが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="d9883-120">It is very important that you use a strong password for the sa login.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d9883-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d9883-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-security-authentication-mode"></a><span data-ttu-id="d9883-122">セキュリティ認証モードを変更するには</span><span class="sxs-lookup"><span data-stu-id="d9883-122">To change security authentication mode</span></span>  
  
1.  <span data-ttu-id="d9883-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9883-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, right-click the server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d9883-124">**[セキュリティ]** ページの **[サーバー認証]** で、新しいサーバーの認証モードを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9883-124">On the **Security** page, under **Server authentication**, select the new server authentication mode, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="d9883-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の再起動が必要であることを示す **のダイアログ ボックスで、** [OK] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9883-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dialog box, click **OK** to acknowledge the requirement to restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="d9883-126">オブジェクト エクスプローラーでサーバーを右クリックし、 **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9883-126">In Object Explorer, right-click your server, and then click **Restart**.</span></span> <span data-ttu-id="d9883-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントも再起動する必要があります (実行されている場合)。</span><span class="sxs-lookup"><span data-stu-id="d9883-127">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running, it must also be restarted.</span></span>  
  
#### <a name="to-enable-the-sa-login"></a><span data-ttu-id="d9883-128">sa ログインを有効にするには</span><span class="sxs-lookup"><span data-stu-id="d9883-128">To enable the sa login</span></span>  
  
1.  <span data-ttu-id="d9883-129">オブジェクトエクスプローラーで、[**セキュリティ**]、[ログイン] の順に展開し、を右クリックし `sa` て、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9883-129">In Object Explorer, expand **Security**, expand Logins, right-click `sa`, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d9883-130">**[全般]** ページで、ログインのパスワード作成と確認が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9883-130">On the **General** page, you might have to create and confirm a password for the  login.</span></span>  
  
3.  <span data-ttu-id="d9883-131">**[状態]** ページで、 **[ログイン]** の **[有効]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9883-131">On the **Status** page, in the **Login** section, click **Enabled**, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d9883-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d9883-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="d9883-133">**sa ログインを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="d9883-133">**To enable the sa login**</span></span>  
  
1.  <span data-ttu-id="d9883-134">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d9883-134">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d9883-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9883-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d9883-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9883-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d9883-137">次の例では、sa ログインを有効にし、新しいパスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="d9883-137">The following example enables the sa login and sets a new password.</span></span>  
  
    ```  
    ALTER LOGIN sa ENABLE ;  
    GO  
    ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
    GO  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d9883-138">参照</span><span class="sxs-lookup"><span data-stu-id="d9883-138">See Also</span></span>  
 <span data-ttu-id="d9883-139">[強力なパスワード](../../relational-databases/security/strong-passwords.md) </span><span class="sxs-lookup"><span data-stu-id="d9883-139">[Strong Passwords](../../relational-databases/security/strong-passwords.md) </span></span>  
 <span data-ttu-id="d9883-140">[SQL Server インストールのセキュリティに関する考慮事項](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="d9883-140">[Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="d9883-141">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9883-141">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 [<span data-ttu-id="d9883-142">システム管理者がロックアウトされた場合の SQL Server への接続</span><span class="sxs-lookup"><span data-stu-id="d9883-142">Connect to SQL Server When System Administrators Are Locked Out</span></span>](connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
  
