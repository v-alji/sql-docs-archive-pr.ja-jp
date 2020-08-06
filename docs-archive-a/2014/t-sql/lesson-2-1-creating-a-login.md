---
title: ログインの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating a login
ms.assetid: a2512310-bdb6-41dc-858a-e866b2b58afc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 400a57693fbea10270a51f5735a19b9639112ce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737356"
---
# <a name="creating-a-login"></a><span data-ttu-id="2d05e-102">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="2d05e-102">Creating a Login</span></span>
  <span data-ttu-id="2d05e-103">[!INCLUDE[ssDE](../includes/ssde-md.md)]にアクセスするには、ユーザーのログインが必要です。</span><span class="sxs-lookup"><span data-stu-id="2d05e-103">To access the [!INCLUDE[ssDE](../includes/ssde-md.md)], users require a login.</span></span> <span data-ttu-id="2d05e-104">ログインは、ユーザーの ID を Windows のアカウントまたは Windows グループのメンバーとして表すか、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のみに存在する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ログインを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2d05e-104">The login can represent the user's identity as a Windows account or as a member of a Windows group, or the login can be a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login that exists only in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d05e-105">できるだけ Windows 認証を使用してください。</span><span class="sxs-lookup"><span data-stu-id="2d05e-105">Whenever possible you should use Windows Authentication.</span></span>  
  
 <span data-ttu-id="2d05e-106">既定では、コンピューターの管理者には [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]へのフル アクセス権が与えられます。</span><span class="sxs-lookup"><span data-stu-id="2d05e-106">By default, administrators on your computer have full access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d05e-107">このレッスンでは、これより特権の少ないユーザーが必要なので、コンピューターに新しいローカルの Windows 認証アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d05e-107">For this lesson, we want to have a less privileged user; therefore, you will create a new local Windows Authentication account on your computer.</span></span> <span data-ttu-id="2d05e-108">そのためには、コンピューターの管理者であることが条件となります。</span><span class="sxs-lookup"><span data-stu-id="2d05e-108">To do this, you must be an administrator on your computer.</span></span> <span data-ttu-id="2d05e-109">その後、この新しいユーザーに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]へのアクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="2d05e-109">Then you will grant that new user access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-create-a-new-windows-account"></a><span data-ttu-id="2d05e-110">新しい Windows アカウントを作成するには</span><span class="sxs-lookup"><span data-stu-id="2d05e-110">To create a new Windows account</span></span>  
  
1.  <span data-ttu-id="2d05e-111">[**スタート**] をクリックし、[**実行**] をクリックします。 [**名前**] ボックスに「」と入力し、 `%SystemRoot%\system32\compmgmt.msc /s` [OK] をクリックして [コンピューターの管理 **]** プログラムを開きます。</span><span class="sxs-lookup"><span data-stu-id="2d05e-111">Click **Start**, click **Run**, in the **Open** box, type `%SystemRoot%\system32\compmgmt.msc /s`, and then click **OK** to open the Computer Management program.</span></span>  
  
2.  <span data-ttu-id="2d05e-112">[ **システム ツール**] の [ **ローカル ユーザーとグループ**] を展開し、[ **ユーザー**] を右クリックして、[ **新しいユーザー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d05e-112">Under **System Tools**, expand **Local Users and Groups**, right-click **Users**, and then click **New User**.</span></span>  
  
3.  <span data-ttu-id="2d05e-113">[ **ユーザー名** ] ボックスに、「 **Mary**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2d05e-113">In the **User name** box type **Mary**.</span></span>  
  
4.  <span data-ttu-id="2d05e-114">[ **パスワード** ] および [ **パスワードの確認入力** ] ボックスに強力なパスワードを入力し、[ **作成** ] をクリックして、新しいローカルの Windows ユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d05e-114">In the **Password** and **Confirm password** box, type a strong password, and then click **Create** to create a new local Windows user.</span></span>  
  
### <a name="to-create-a-login"></a><span data-ttu-id="2d05e-115">ログインを作成するには</span><span class="sxs-lookup"><span data-stu-id="2d05e-115">To create a login</span></span>  
  
1.  <span data-ttu-id="2d05e-116">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のクエリ エディター ウィンドウで、次のコードを入力して実行します。 `computer_name` は自分のコンピューター名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2d05e-116">In a Query Editor window of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], type and execute the following code replacing `computer_name` with the name of your computer.</span></span> <span data-ttu-id="2d05e-117">`FROM WINDOWS` は Windows がユーザーを認証することを示します。</span><span class="sxs-lookup"><span data-stu-id="2d05e-117">`FROM WINDOWS` indicates that Windows will authenticate the user.</span></span> <span data-ttu-id="2d05e-118">オプションの `DEFAULT_DATABASE` 引数は、接続文字列で別のデータベースを指定しない限り、 `Mary` を `TestData` データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="2d05e-118">The optional `DEFAULT_DATABASE` argument connects `Mary` to the `TestData` database, unless her connection string indicates another database.</span></span> <span data-ttu-id="2d05e-119">このステートメントでは、セミコロンが [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントのオプションの終了文字として使用されています。</span><span class="sxs-lookup"><span data-stu-id="2d05e-119">This statement introduces the semicolon as an optional termination for a [!INCLUDE[tsql](../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    CREATE LOGIN [computer_name\Mary]  
        FROM WINDOWS  
        WITH DEFAULT_DATABASE = [TestData];  
    GO  
    ```  
  
     <span data-ttu-id="2d05e-120">これでユーザー名 `Mary`が承認され、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のこのインスタンスへのアクセスがコンピューターによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="2d05e-120">This authorizes a user name `Mary`, authenticated by your computer, to access this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d05e-121">コンピューターに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスが複数ある場合は、 `Mary` がアクセスする各インスタンスでログインを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d05e-121">If there is more than one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the computer, you must create the login on each instance that `Mary` must access.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2d05e-122">`Mary` はドメインのアカウントではないため、このユーザー名はこのコンピューターでしか認証できません。</span><span class="sxs-lookup"><span data-stu-id="2d05e-122">Because `Mary` is not a domain account, this user name can only be authenticated on this computer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2d05e-123">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="2d05e-123">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2d05e-124">データベースへのアクセス権の付与</span><span class="sxs-lookup"><span data-stu-id="2d05e-124">Granting Access to a Database</span></span>](lesson-2-2-granting-access-to-a-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d05e-125">参照</span><span class="sxs-lookup"><span data-stu-id="2d05e-125">See Also</span></span>  
 <span data-ttu-id="2d05e-126">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2d05e-126">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 [<span data-ttu-id="2d05e-127">認証モードの選択</span><span class="sxs-lookup"><span data-stu-id="2d05e-127">Choose an Authentication Mode</span></span>](../relational-databases/security/choose-an-authentication-mode.md)  
  
  
