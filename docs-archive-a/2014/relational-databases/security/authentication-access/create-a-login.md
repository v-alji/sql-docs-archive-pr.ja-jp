---
title: ログインの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.LOGIN.SERVERROLES.F1
- sql12.swb.login.databaseaccess.f1
- sql12.swb.login.general.f1
- sql12.swb.login.effectivepermissions.f1
- sql12.swb.login.status.f1
helpviewer_keywords:
- authentication [SQL Server], logins
- logins [SQL Server], creating
- creating logins with Management Studio
- Create login [SQL Server]
- SQL Server logins
ms.assetid: fb163e47-1546-4682-abaa-8c9494e9ddc7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e476880103a69ae016c6720f36e26ef884db6f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714058"
---
# <a name="create-a-login"></a><span data-ttu-id="45017-102">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="45017-102">Create a Login</span></span>
  <span data-ttu-id="45017-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、ログインを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45017-103">This topic describes how to create a login in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="45017-104">ログインとは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスに接続しようとしている人またはプロセスの ID を指します。</span><span class="sxs-lookup"><span data-stu-id="45017-104">A login is the identity of the person or process that is connecting to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="45017-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="45017-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="45017-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="45017-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="45017-107">背景</span><span class="sxs-lookup"><span data-stu-id="45017-107">Background</span></span>](#Background)  
  
     [<span data-ttu-id="45017-108">Security</span><span class="sxs-lookup"><span data-stu-id="45017-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="45017-109">**次のものを使用してログインを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="45017-109">**To create a login, using:**</span></span>  
  
     [<span data-ttu-id="45017-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="45017-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="45017-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="45017-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="45017-112">**補足情報:**  [ログインの作成後に実行する手順](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="45017-112">**Follow Up:**  [Steps to take after you create a login](#FollowUp)</span></span>  
  
##  <a name="background"></a><a name="Background"></a> <span data-ttu-id="45017-113">背景情報</span><span class="sxs-lookup"><span data-stu-id="45017-113">Background</span></span>  
 <span data-ttu-id="45017-114">ログインは、セキュリティ プリンシパル、またはセキュリティで保護されたシステムで認証できるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="45017-114">A login is a security principal, or an entity that can be authenticated by a secure system.</span></span> <span data-ttu-id="45017-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に接続するためには、ユーザーにログインが必要です。</span><span class="sxs-lookup"><span data-stu-id="45017-115">Users need a login to connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="45017-116">Windows プリンシパル (ドメイン ユーザーや Windows ドメイン グループなど) に基づいてログインを作成することも、Windows プリンシパルに基づかないログイン ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインなど) を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="45017-116">You can create a login based on a Windows principal (such as a domain user or a Windows domain group) or you can create a login that is not based on a Windows principal (such as an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45017-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用するためには、[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に混合モード認証が使用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="45017-117">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must use mixed mode authentication.</span></span> <span data-ttu-id="45017-118">詳細については、「 [認証モードの選択](../choose-an-authentication-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-118">For more information, see [Choose an Authentication Mode](../choose-an-authentication-mode.md).</span></span>  
  
 <span data-ttu-id="45017-119">セキュリティ プリンシパルとして、ログインには権限を許可することができます。</span><span class="sxs-lookup"><span data-stu-id="45017-119">As a security principal, permissions can be granted to logins.</span></span> <span data-ttu-id="45017-120">ログインのスコープは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]全体です。</span><span class="sxs-lookup"><span data-stu-id="45017-120">The scope of a login is the whole [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="45017-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンス上の特定のデータベースに接続するには、データベース ユーザーにログインをマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="45017-121">To connect to a specific database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a login must be mapped to a database user.</span></span> <span data-ttu-id="45017-122">データベース内の権限を許可したり拒否したりする際に、その対象となるのは、ログインではなく、データベース ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="45017-122">Permissions inside the database are granted and denied to the database user, not the login.</span></span> <span data-ttu-id="45017-123">ログインには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス全体をスコープとして持つ権限 (`CREATE ENDPOINT` 権限など) を許可することができます。</span><span class="sxs-lookup"><span data-stu-id="45017-123">Permissions that have the scope of the whole instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (for example, the `CREATE ENDPOINT` permission) can be granted to a login.</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="45017-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="45017-124">Security</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="45017-125">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="45017-125">Permissions</span></span>  
 <span data-ttu-id="45017-126">サーバーに対する `ALTER ANY LOGIN` または `ALTER LOGIN` 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="45017-126">Requires `ALTER ANY LOGIN` or `ALTER LOGIN` permission on the server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="45017-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="45017-127">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-sql-server-login"></a><span data-ttu-id="45017-128">SQL Server ログインを作成するには</span><span class="sxs-lookup"><span data-stu-id="45017-128">To create a SQL Server login</span></span>  
  
1.  <span data-ttu-id="45017-129">オブジェクト エクスプローラーで、新しいログインを作成するサーバー インスタンスのフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="45017-129">In Object Explorer, expand the folder of the server instance in which you want to create the new login.</span></span>  
  
2.  <span data-ttu-id="45017-130">**[セキュリティ]** フォルダーを右クリックし、 **[新規作成]** をポイントして、 **[ログイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-130">Right-click the **Security** folder, point to **New**, and select **Login...**.</span></span>  
  
3.  <span data-ttu-id="45017-131">**[ログイン - 新規作成]** ダイアログ ボックスの **[全般]** ページで、 **[ログイン名]** ボックスにユーザーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="45017-131">In the **Login - New** dialog box, on the **General** page, enter the name of a user in the **Login name** box.</span></span> <span data-ttu-id="45017-132">または、 **[検索]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="45017-132">Alternately, click **Search...** to open the **Select User or Group** dialog box.</span></span>  
  
     <span data-ttu-id="45017-133">**[検索]** をクリックした場合:</span><span class="sxs-lookup"><span data-stu-id="45017-133">If you click **Search...**:</span></span>  
  
    1.  <span data-ttu-id="45017-134">**[このオブジェクトの種類を選択してください]** で、 **[オブジェクトの種類]** をクリックして **[オブジェクトの種類]** ダイアログ ボックスを開き、 **[ビルトイン セキュリティ プリンシパル]** 、 **[グループ]** 、 **[ユーザー]** のいずれかまたはすべてを選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-134">Under **Select this object type**, click **Object Types...** to open the **Object Types** dialog box and select any or all of the following: **Built-in security principals**, **Groups**, and **Users**.</span></span> <span data-ttu-id="45017-135">**[ビルトイン セキュリティ プリンシパル]** と **[ユーザー]** が既定で選択されます。</span><span class="sxs-lookup"><span data-stu-id="45017-135">**Built-in security principals** and **Users** are selected by default.</span></span> <span data-ttu-id="45017-136">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-136">When finished, click **OK**.</span></span>  
  
    2.  <span data-ttu-id="45017-137">**[場所を指定してください]** で、 **[場所]** をクリックして **[場所]** ダイアログ ボックスを開き、使用可能なサーバー場所の 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-137">Under **From this location**, click **Locations...** to open the **Locations** dialog box and select one of the available server locations.</span></span> <span data-ttu-id="45017-138">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-138">When finished, click **OK**.</span></span>  
  
    3.  <span data-ttu-id="45017-139">**[選択するオブジェクト名を入力してください (例)]** で、検索するユーザー名またはグループ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="45017-139">Under **Enter the object name to select (examples)**, enter the user or group name that you want to find.</span></span> <span data-ttu-id="45017-140">詳細については、「 [[ユーザー、コンピューターまたはグループの選択] ダイアログ ボックス](https://technet.microsoft.com/library/cc771712.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-140">For more information, see [Select Users, Computers, or Groups Dialog Box](https://technet.microsoft.com/library/cc771712.aspx).</span></span>  
  
    4.  <span data-ttu-id="45017-141">詳細検索オプションを表示するには **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-141">Click **Advanced...** for more advanced search options.</span></span> <span data-ttu-id="45017-142">詳細については、「 [[ユーザー、コンピューターまたはグループの選択] ダイアログ ボックス - [詳細設定] ページ](https://technet.microsoft.com/library/cc733110.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-142">For more information, see [Select Users, Computers, or Groups Dialog Box - Advanced Page](https://technet.microsoft.com/library/cc733110.aspx).</span></span>  
  
    5.  <span data-ttu-id="45017-143">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-143">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="45017-144">Windows プリンシパル上に基づいてログインを作成するには、 **[Windows 認証]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-144">To create a login based on a Windows principal, select **Windows authentication**.</span></span> <span data-ttu-id="45017-145">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="45017-145">This is the default selection.</span></span>  
  
5.  <span data-ttu-id="45017-146">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに保存されるログインを作成するには、 **[SQL Server 認証]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-146">To create a login that is saved on a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, select **SQL Server authentication**.</span></span>  
  
    1.  <span data-ttu-id="45017-147">**[パスワード]** ボックスに、新しいユーザーのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="45017-147">In the **Password** box, enter a password for the new user.</span></span> <span data-ttu-id="45017-148">**[パスワードの確認]** ボックスに、パスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="45017-148">Enter that password again into the **Confirm Password** box.</span></span>  
  
    2.  <span data-ttu-id="45017-149">既存のパスワードを変更する場合は、 **[古いパスワードを指定する]** を選択し、古いパスワードを **[古いパスワード]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="45017-149">When changing an existing password, select **Specify old password**, and then type the old password in the **Old password** box.</span></span>  
  
    3.  <span data-ttu-id="45017-150">複雑さと施行のパスワード ポリシー オプションを適用するには、 **[パスワード ポリシーを適用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-150">To enforce password policy options for complexity and enforcement, select **Enforce password policy**.</span></span> <span data-ttu-id="45017-151">詳細については、「 [Password Policy](../password-policy.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="45017-151">For more information, see [Password Policy](../password-policy.md).</span></span> <span data-ttu-id="45017-152">**[SQL Server 認証]** が選択されている場合、これは既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="45017-152">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
    4.  <span data-ttu-id="45017-153">失効に関するパスワード ポリシー オプションを適用するには、 **[パスワードの期限を適用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-153">To enforce password policy options for expiration, select **Enforce password expiration**.</span></span> <span data-ttu-id="45017-154">このチェック ボックスをオンにする場合は、 **[パスワード ポリシーを適用する]** がオンになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="45017-154">**Enforce password policy** must be selected to enable this checkbox.</span></span> <span data-ttu-id="45017-155">**[SQL Server 認証]** が選択されている場合、これは既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="45017-155">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
    5.  <span data-ttu-id="45017-156">ユーザーにログインの初回使用後に新しいパスワードの作成を強制するには、 **[ユーザーは次回ログイン時にパスワードを変更する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-156">To force the user to create a new password after the first time the login is used, select **User must change password at next login**.</span></span> <span data-ttu-id="45017-157">このチェック ボックスをオンにする場合は、 **[パスワードの期限を適用する]** がオンになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="45017-157">**Enforce password expiration** must be selected to enable this checkbox.</span></span> <span data-ttu-id="45017-158">**[SQL Server 認証]** が選択されている場合、これは既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="45017-158">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
6.  <span data-ttu-id="45017-159">ログインをスタンドアロン セキュリティ証明書に関連付けるには、 **[証明書にマップ済み]** を選択し、一覧から既存の証明書の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-159">To associate the login with a stand-alone security certificate, select **Mapped to certificate** and then select the name of an existing certificate from the list.</span></span>  
  
7.  <span data-ttu-id="45017-160">ログインをスタンドアロン非対称キーに関連付けるには、 **[非対称キーにマップ済み]** を選択し、一覧から既存のキーの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-160">To associate the login with a stand-alone asymmetric key, select **Mapped to asymmetric key** to, and then select the name of an existing key from the list.</span></span>  
  
8.  <span data-ttu-id="45017-161">ログインをセキュリティ資格情報に関連付けるには、 **[資格情報にマップ済み]** チェック ボックスをオンにし、一覧から既存の資格情報を選択するか、 **[追加]** をクリックして新しい資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="45017-161">To associate the login with a security credential, select the **Mapped to Credential** check box, and then either select an existing credential from the list or click **Add** to create a new credential.</span></span> <span data-ttu-id="45017-162">ログインからセキュリティ資格情報へのマッピングを削除するには、 **[マップされた資格情報]** から資格情報を選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-162">To remove a mapping to a security credential from the login, select the credential from **Mapped Credentials** and click **Remove**.</span></span> <span data-ttu-id="45017-163">全般的な資格情報の詳細については、「[資格情報 &#40;データベース エンジン&#41;](credentials-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-163">For more information about credentials in general, see [Credentials &#40;Database Engine&#41;](credentials-database-engine.md).</span></span>  
  
9. <span data-ttu-id="45017-164">**[既定のデータベース]** の一覧から、ログインの既定のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-164">From the **Default database** list, select a default database for the login.</span></span> <span data-ttu-id="45017-165">**[マスター]** はこのオプションの既定値です。</span><span class="sxs-lookup"><span data-stu-id="45017-165">**Master** is the default for this option.</span></span>  
  
10. <span data-ttu-id="45017-166">**[既定の言語]** の一覧から、ログインの既定の言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-166">From the **Default language** list, select a default language for the login.</span></span>  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="45017-167">追加オプション</span><span class="sxs-lookup"><span data-stu-id="45017-167">Additional Options</span></span>  
 <span data-ttu-id="45017-168">**[ログイン - 新規作成]** ダイアログ ボックスでは、 **[サーバー ロール]** 、 **[ユーザー マッピング]** 、 **[セキュリティ保護可能なリソース]** 、 **[状態]** の 4 つの追加ページにもオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="45017-168">The **Login - New** dialog box also offers options on four additional pages: **Server Roles**, **User Mapping**, **Securables**, and **Status**.</span></span>  
  
### <a name="server-roles"></a><span data-ttu-id="45017-169">[サーバー ロール]</span><span class="sxs-lookup"><span data-stu-id="45017-169">Server Roles</span></span>  
 <span data-ttu-id="45017-170">**[サーバー ロール]** ページには、新しいログインに割り当てることができるすべての可能なロールが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="45017-170">The **Server Roles** page lists all possible roles that can be assigned to the new login.</span></span> <span data-ttu-id="45017-171">次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="45017-171">The following options are available:</span></span>  
  
 <span data-ttu-id="45017-172">**[bulkadmin]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-172">**bulkadmin** check box</span></span>  
 <span data-ttu-id="45017-173">**bulkadmin** 固定サーバー ロールのメンバーは、BULK INSERT ステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="45017-173">Members of the **bulkadmin** fixed server role can run the BULK INSERT statement.</span></span>  
  
 <span data-ttu-id="45017-174">**[dbcreator]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-174">**dbcreator** check box</span></span>  
 <span data-ttu-id="45017-175">**dbcreator** 固定サーバー ロールのメンバーは、任意のデータベースを作成、変更、削除、および復元できます。</span><span class="sxs-lookup"><span data-stu-id="45017-175">Members of the **dbcreator** fixed server role can create, alter, drop, and restore any database.</span></span>  
  
 <span data-ttu-id="45017-176">**[diskadmin]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-176">**diskadmin** check box</span></span>  
 <span data-ttu-id="45017-177">**diskadmin** 固定サーバー ロールのメンバーは、ディスク ファイルを管理できます。</span><span class="sxs-lookup"><span data-stu-id="45017-177">Members of the **diskadmin** fixed server role can manage disk files.</span></span>  
  
 <span data-ttu-id="45017-178">**[processadmin]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-178">**processadmin** check box</span></span>  
 <span data-ttu-id="45017-179">**processadmin** 固定サーバー ロールのメンバーは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスを実行しているプロセスを終了できます。</span><span class="sxs-lookup"><span data-stu-id="45017-179">Members of the **processadmin** fixed server role can terminate processes running in an instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="45017-180">**[public]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-180">**public** check box</span></span>  
 <span data-ttu-id="45017-181">すべて SQL Server ユーザー、グループ、およびロールは、既定で **public** 固定サーバー ロールに属します。</span><span class="sxs-lookup"><span data-stu-id="45017-181">All SQL Server users, groups, and roles belong to the **public** fixed server role by default.</span></span>  
  
 <span data-ttu-id="45017-182">**[securityadmin]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-182">**securityadmin** check box</span></span>  
 <span data-ttu-id="45017-183">**securityadmin** 固定サーバー ロールのメンバーは、ログインとログインのプロパティを管理します。</span><span class="sxs-lookup"><span data-stu-id="45017-183">Members of the **securityadmin** fixed server role manage logins and their properties.</span></span> <span data-ttu-id="45017-184">このメンバーは、サーバー レベルの権限を許可、拒否、および禁止できます。</span><span class="sxs-lookup"><span data-stu-id="45017-184">They can GRANT, DENY, and REVOKE server-level permissions.</span></span> <span data-ttu-id="45017-185">また、データベース レベルの権限も許可、拒否、および禁止できます。</span><span class="sxs-lookup"><span data-stu-id="45017-185">They can also GRANT, DENY, and REVOKE database-level permissions.</span></span> <span data-ttu-id="45017-186">また、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインのパスワードをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="45017-186">Additionally, they can reset passwords for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span>  
  
 <span data-ttu-id="45017-187">**[serveradmin]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-187">**serveradmin** check box</span></span>  
 <span data-ttu-id="45017-188">**serveradmin** 固定サーバー ロールのメンバーは、サーバー全体の構成オプションを変更したり、サーバーをシャットダウンしたりできます。</span><span class="sxs-lookup"><span data-stu-id="45017-188">Members of the **serveradmin** fixed server role can change server-wide configuration options and shut down the server.</span></span>  
  
 <span data-ttu-id="45017-189">**[setupadmin]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-189">**setupadmin** check box</span></span>  
 <span data-ttu-id="45017-190">**setupadmin** 固定サーバー ロールのメンバーは、リンク サーバーを追加および削除でき、一部のシステム ストアド プロシージャを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="45017-190">Members of the **setupadmin** fixed server role can add and remove linked servers, and they can execute some system stored procedures.</span></span>  
  
 <span data-ttu-id="45017-191">**[sysadmin]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="45017-191">**sysadmin** check box</span></span>  
 <span data-ttu-id="45017-192">**sysadmin** 固定サーバー ロールのメンバーは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]の任意の動作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="45017-192">Members of the **sysadmin** fixed server role can perform any activity in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
### <a name="user-mapping"></a><span data-ttu-id="45017-193">[ユーザー マッピング]</span><span class="sxs-lookup"><span data-stu-id="45017-193">User Mapping</span></span>  
 <span data-ttu-id="45017-194">**[ユーザー マッピング]** ページには、すべての可能なデータベースと、ログインに適用できるデータベースに対するデータベース ロール メンバーシップが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="45017-194">The **User Mapping** page lists all possible databases and the database role memberships on those databases that can be applied to the login.</span></span> <span data-ttu-id="45017-195">選択したデータベースによって、ログインに使用できるロールのメンバーシップが決まります。</span><span class="sxs-lookup"><span data-stu-id="45017-195">The databases selected determine the role memberships that are available for the login.</span></span> <span data-ttu-id="45017-196">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="45017-196">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="45017-197">**[このログインにマップされたユーザー]**</span><span class="sxs-lookup"><span data-stu-id="45017-197">**Users mapped to this login**</span></span>  
 <span data-ttu-id="45017-198">このログインでアクセスできるデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-198">Select the databases that this login can access.</span></span> <span data-ttu-id="45017-199">データベースを選択すると、 **[_database_name_ のデータベース ロール メンバーシップ]** ペインに有効なデータベース ロールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45017-199">When you select a database, its valid database roles are displayed in the **Database role membership for:** _database_name_ pane.</span></span>  
  
 <span data-ttu-id="45017-200">**Map**</span><span class="sxs-lookup"><span data-stu-id="45017-200">**Map**</span></span>  
 <span data-ttu-id="45017-201">下の一覧にあるデータベースへのアクセスを、ログインに許可します。</span><span class="sxs-lookup"><span data-stu-id="45017-201">Allow the login to access the databases listed below.</span></span>  
  
 <span data-ttu-id="45017-202">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="45017-202">**Database**</span></span>  
 <span data-ttu-id="45017-203">サーバーで利用できるデータベースを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="45017-203">Lists the databases available on the server.</span></span>  
  
 <span data-ttu-id="45017-204">**User**</span><span class="sxs-lookup"><span data-stu-id="45017-204">**User**</span></span>  
 <span data-ttu-id="45017-205">ログインにマップするデータベース ユーザーを指定します。</span><span class="sxs-lookup"><span data-stu-id="45017-205">Specify a database user to map to the login.</span></span> <span data-ttu-id="45017-206">既定では、データベース ユーザーの名前はログインと同じになります。</span><span class="sxs-lookup"><span data-stu-id="45017-206">By default, the database user has the same name as the login.</span></span>  
  
 <span data-ttu-id="45017-207">**[既定のスキーマ]**</span><span class="sxs-lookup"><span data-stu-id="45017-207">**Default Schema**</span></span>  
 <span data-ttu-id="45017-208">ユーザーの既定のスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="45017-208">Specifies the default schema of the user.</span></span> <span data-ttu-id="45017-209">ユーザーが最初に作成されるときの既定のスキーマは、 **dbo**です。</span><span class="sxs-lookup"><span data-stu-id="45017-209">When a user is first created, its default schema is **dbo**.</span></span> <span data-ttu-id="45017-210">存在しない既定のスキーマを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="45017-210">It is possible to specify a default schema that does not yet exist.</span></span> <span data-ttu-id="45017-211">Windows グループ、証明書、非対称キーにマップされるユーザーに対して既定のスキーマを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="45017-211">You cannot specify a default schema for a user that is mapped to a Windows group, a certificate, or an asymmetric key.</span></span>  
  
 <span data-ttu-id="45017-212">**[_database_name_ では guest アカウントが有効]**</span><span class="sxs-lookup"><span data-stu-id="45017-212">**Guest account enabled for:**  _database_name_</span></span>  
 <span data-ttu-id="45017-213">選択したデータベースで guest アカウントが有効かどうかを示す読み取り専用属性です。</span><span class="sxs-lookup"><span data-stu-id="45017-213">Read-only attribute indicating whether the Guest account is enabled on the selected database.</span></span> <span data-ttu-id="45017-214">guest アカウントを有効または無効にするには、guest アカウントの **[ログインのプロパティ]** ダイアログ ボックスの **[状態]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="45017-214">Use the **Status** page of the **Login Properties** dialog box of the Guest account to enable or disable the Guest account.</span></span>  
  
 <span data-ttu-id="45017-215">**[_database_name_ のデータベース ロール メンバーシップ]**</span><span class="sxs-lookup"><span data-stu-id="45017-215">**Database role membership for:**  _database_name_</span></span>  
 <span data-ttu-id="45017-216">指定されたデータベースにおけるユーザーのロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-216">Select the roles for the user in the specified database.</span></span> <span data-ttu-id="45017-217">どのデータベースでも、ユーザーはすべて **public** ロールのメンバーになり、削除できません。</span><span class="sxs-lookup"><span data-stu-id="45017-217">All users are members of the **public** role in every database and cannot be removed.</span></span> <span data-ttu-id="45017-218">データベース ロールの詳細については、「 [データベース レベルのロール](database-level-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-218">For more information about database roles, see [Database-Level Roles](database-level-roles.md).</span></span>  
  
### <a name="securables"></a><span data-ttu-id="45017-219">[セキュリティ保護可能なリソース]</span><span class="sxs-lookup"><span data-stu-id="45017-219">Securables</span></span>  
 <span data-ttu-id="45017-220">**[セキュリティ保護可能なリソース]** ページには、すべてのセキュリティ保護可能なリソースと、ログインに付与できる、セキュリティ保護可能なリソースに対する権限が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="45017-220">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span> <span data-ttu-id="45017-221">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="45017-221">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="45017-222">**上のグリッド**</span><span class="sxs-lookup"><span data-stu-id="45017-222">**Upper Grid**</span></span>  
 <span data-ttu-id="45017-223">権限を設定できるアイテムが 1 つ以上表示されます。</span><span class="sxs-lookup"><span data-stu-id="45017-223">Contains one or more items for which permissions can be set.</span></span> <span data-ttu-id="45017-224">上のグリッドに表示される列は、プリンシパルまたはセキュリティ保護可能なリソースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="45017-224">The columns that are displayed in the upper grid vary depending on the principal or securable.</span></span>  
  
 <span data-ttu-id="45017-225">アイテムを上のグリッドに追加するには:</span><span class="sxs-lookup"><span data-stu-id="45017-225">To add items to the upper grid:</span></span>  
  
1.  <span data-ttu-id="45017-226">**[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-226">Click **Search**.</span></span>  
  
2.  <span data-ttu-id="45017-227">[**オブジェクトの追加**] ダイアログボックスで、次のいずれかのオプションを選択します。 [特定の**オブジェクト...**]、[**種類のすべてのオブジェクト**]、または [**サーバー**_server_name_] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-227">In the **Add Objects** dialog box, select one of the following options: **Specific objects...**, **All objects of the types...**, or **The server**_server_name_.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="45017-228">\*\*[サーバー \*\*_server_name]_ を選択すると、そのサーバーのセキュリティ保護可能なすべてのオブジェクトが上のグリッドに自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="45017-228">Selecting **The server**_server_name_ automatically fills the upper grid with all of that servers' securable objects.</span></span>  
  
3.  <span data-ttu-id="45017-229">**[特定のオブジェクト]** を選択した場合:</span><span class="sxs-lookup"><span data-stu-id="45017-229">If you select **Specific objects...**:</span></span>  
  
    1.  <span data-ttu-id="45017-230">**[オブジェクトの選択]** ダイアログ ボックスの **[以下のオブジェクトの種類を選択]** で、 **[オブジェクトの種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-230">In the **Select Objects** dialog box, under **Select these object types**, click **Object Types...**.</span></span>  
  
    2.  <span data-ttu-id="45017-231">**[オブジェクトの種類を選択]** ダイアログ ボックスで、 **[エンドポイント]** 、 **[ログイン]** 、 **[サーバー]** 、 **[可用性グループ]** 、 **[サーバー ロール]** のいずれかまたはすべてをオブジェクトの種類として選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-231">In the **Select Object Types** dialog box, select any or all of the following object types: **Endpoints**, **Logins**, **Servers**, **Availability Groups**, and **Server roles**.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    3.  <span data-ttu-id="45017-232">**[選択するオブジェクト名を入力してください (例)]** で、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-232">Under **Enter the object names to select (examples)**, click **Browse...**.</span></span>  
  
    4.  <span data-ttu-id="45017-233">**[オブジェクトの参照]** ダイアログ ボックスで、 **[オブジェクトの種類を選択]** ダイアログ ボックスで選択した種類の使用可能なオブジェクトを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-233">In the **Browse for Objects** dialog box, select any of the available objects of the type that you selected in the **Select Object Types** dialog box, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="45017-234">**[オブジェクトの選択]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-234">In the **Select Objects** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="45017-235">**[オブジェクトの種類を選択]** ダイアログ ボックスで **[この種類のすべてのオブジェクト]** を選択した場合は、 **[エンドポイント]** 、 **[ログイン]** 、 **[サーバー]** 、 **[可用性グループ]** 、 **[サーバー ロール]** のいずれかまたはすべてをオブジェクトの種類として選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-235">If you select **All objects of the types...**, in the **Select Object Types** dialog box, select any or all of the following object types: **Endpoints**, **Logins**, **Servers**, **Availability Groups**, and **Server roles**.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="45017-236">**名前**</span><span class="sxs-lookup"><span data-stu-id="45017-236">**Name**</span></span>  
 <span data-ttu-id="45017-237">グリッドに追加される各プリンシパルまたはセキュリティ保護可能なリソースの名前です。</span><span class="sxs-lookup"><span data-stu-id="45017-237">The name of each principal or securable that is added to the grid.</span></span>  
  
 <span data-ttu-id="45017-238">**Type**</span><span class="sxs-lookup"><span data-stu-id="45017-238">**Type**</span></span>  
 <span data-ttu-id="45017-239">各アイテムの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="45017-239">Describes the type of each item.</span></span>  
  
 <span data-ttu-id="45017-240">**[明示的] タブ**</span><span class="sxs-lookup"><span data-stu-id="45017-240">**Explicit Tab**</span></span>  
 <span data-ttu-id="45017-241">上のグリッドで選択されているセキュリティ保護可能なリソースに適用できる権限が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45017-241">Lists the possible permissions for the securable that are selected in the upper grid.</span></span> <span data-ttu-id="45017-242">すべての明示的な権限に対してすべてのオプションを使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="45017-242">Not all options are available for all explicit permissions.</span></span>  
  
 <span data-ttu-id="45017-243">**アクセス許可**</span><span class="sxs-lookup"><span data-stu-id="45017-243">**Permissions**</span></span>  
 <span data-ttu-id="45017-244">権限の名前です。</span><span class="sxs-lookup"><span data-stu-id="45017-244">The name of the permission.</span></span>  
  
 <span data-ttu-id="45017-245">**Grantor**</span><span class="sxs-lookup"><span data-stu-id="45017-245">**Grantor**</span></span>  
 <span data-ttu-id="45017-246">権限を許可したプリンシパルです。</span><span class="sxs-lookup"><span data-stu-id="45017-246">The principal that granted the permission.</span></span>  
  
 <span data-ttu-id="45017-247">**Grant**</span><span class="sxs-lookup"><span data-stu-id="45017-247">**Grant**</span></span>  
 <span data-ttu-id="45017-248">この権限をログインに対して許可する場合はオンにします。</span><span class="sxs-lookup"><span data-stu-id="45017-248">Select to grant this permission to the login.</span></span> <span data-ttu-id="45017-249">この権限を取り消す場合はオフにします。</span><span class="sxs-lookup"><span data-stu-id="45017-249">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="45017-250">**[許可の有無]**</span><span class="sxs-lookup"><span data-stu-id="45017-250">**With Grant**</span></span>  
 <span data-ttu-id="45017-251">一覧表示された権限に対する WITH GRANT オプションの状態を反映します。</span><span class="sxs-lookup"><span data-stu-id="45017-251">Reflects the state of the WITH GRANT option for the listed permission.</span></span> <span data-ttu-id="45017-252">このボックスは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="45017-252">This box is read-only.</span></span> <span data-ttu-id="45017-253">この権限を適用するには、 [GRANT](/sql/t-sql/statements/grant-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="45017-253">To apply this permission, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="45017-254">**Deny**</span><span class="sxs-lookup"><span data-stu-id="45017-254">**Deny**</span></span>  
 <span data-ttu-id="45017-255">この権限をログインに対して拒否する場合はオンにします。</span><span class="sxs-lookup"><span data-stu-id="45017-255">Select to deny this permission to the login.</span></span> <span data-ttu-id="45017-256">この権限を取り消す場合はオフにします。</span><span class="sxs-lookup"><span data-stu-id="45017-256">Clear to revoke this permission.</span></span>  
  
### <a name="status"></a><span data-ttu-id="45017-257">Status</span><span class="sxs-lookup"><span data-stu-id="45017-257">Status</span></span>  
 <span data-ttu-id="45017-258">**[状態]** ページには、選択した [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインに対して構成できる認証オプションと承認オプションの一部が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45017-258">The **Status** page lists some of the authentication and authorization options that can be configured on the selected [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="45017-259">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="45017-259">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="45017-260">**[データベース エンジンに接続する権限]**</span><span class="sxs-lookup"><span data-stu-id="45017-260">**Permission to connect to database engine**</span></span>  
 <span data-ttu-id="45017-261">この設定を操作するときは、選択したログインを、セキュリティ保護可能なリソースに対する権限を許可または拒否できるプリンシパルと考えます。</span><span class="sxs-lookup"><span data-stu-id="45017-261">When you work with this setting, you should think of the selected login as a principal that can be granted or denied permission on a securable.</span></span>  
  
 <span data-ttu-id="45017-262">ログインに CONNECT SQL 権限を付与する場合は、 **[許可]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-262">Select **Grant** to grant CONNECT SQL permission to the login.</span></span> <span data-ttu-id="45017-263">ログインに CONNECT SQL 権限を与えない場合は、 **[拒否]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45017-263">Select **Deny** to deny CONNECT SQL to the login.</span></span>  
  
 <span data-ttu-id="45017-264">**Login**</span><span class="sxs-lookup"><span data-stu-id="45017-264">**Login**</span></span>  
 <span data-ttu-id="45017-265">この設定を操作するときは、選択したログインを、テーブル内のレコードと考えます。</span><span class="sxs-lookup"><span data-stu-id="45017-265">When you work with this setting, you should think of the selected login as a record in a table.</span></span> <span data-ttu-id="45017-266">ここに一覧表示される値を変更すると、それらの変更がレコードに適用されます。</span><span class="sxs-lookup"><span data-stu-id="45017-266">Changes to the values listed here will be applied to the record.</span></span>  
  
 <span data-ttu-id="45017-267">無効になっているログインも、レコードとして存在し続けます。</span><span class="sxs-lookup"><span data-stu-id="45017-267">A login that has been disabled continues to exist as a record.</span></span> <span data-ttu-id="45017-268">ただし、無効になっているログインから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に接続を試みても、そのログインは認証されません。</span><span class="sxs-lookup"><span data-stu-id="45017-268">But if it tries to connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the login will not be authenticated.</span></span>  
  
 <span data-ttu-id="45017-269">このオプションを選択して、このログインを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="45017-269">Select this option to enable or disable this login.</span></span> <span data-ttu-id="45017-270">このオプションは、ENABLE オプションまたは DISABLE オプションを指定した ALTER LOGIN ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="45017-270">This option uses the ALTER LOGIN statement with the either ENABLE or DISABLE option.</span></span>  
  
 <span data-ttu-id="45017-271">**SQL Server 認証**</span><span class="sxs-lookup"><span data-stu-id="45017-271">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="45017-272">**[ログインをロックアウトする]** チェック ボックスは、選択したログインから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用して接続する場合のみ使用できます。このチェック ボックスは、そのログインがロックアウトされていることを示します。この設定は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="45017-272">The check box **Login is locked out** is only available if the selected login connects using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication and the login has been locked out. This setting is read-only.</span></span> <span data-ttu-id="45017-273">ロックアウトされたログインのロックを解除するには、UNLOCK オプションを指定して ALTER LOGIN を実行します。</span><span class="sxs-lookup"><span data-stu-id="45017-273">To unlock a login that is locked out, execute ALTER LOGIN with the UNLOCK option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="45017-274">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="45017-274">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-login-using-windows-authentication"></a><span data-ttu-id="45017-275">Windows 認証を使用してログインを作成するには</span><span class="sxs-lookup"><span data-stu-id="45017-275">To create a login using Windows Authentication</span></span>  
  
1.  <span data-ttu-id="45017-276">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="45017-276">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="45017-277">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-277">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="45017-278">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-278">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Create a login for SQL Server by specifying a server name and a Windows domain account name.  
  
    CREATE LOGIN [<domainName>\<loginName>] FROM WINDOWS;  
    GO  
  
    ```  
  
#### <a name="to-create-a-login-using-sql-server-authentication"></a><span data-ttu-id="45017-279">SQL Server 認証を使用してログインを作成するには</span><span class="sxs-lookup"><span data-stu-id="45017-279">To create a login using SQL Server Authentication</span></span>  
  
1.  <span data-ttu-id="45017-280">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="45017-280">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="45017-281">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-281">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="45017-282">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45017-282">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the user "shcooper" for SQL Server using the security credential "RestrictedFaculty"   
    -- The user login starts with the password "Baz1nga," but that password must be changed after the first login.  
  
    CREATE LOGIN shcooper   
       WITH PASSWORD = 'Baz1nga' MUST_CHANGE,  
       CREDENTIAL = RestrictedFaculty;  
    GO  
  
    ```  
  
 <span data-ttu-id="45017-283">詳細については、「[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-283">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-login"></a><a name="FollowUp"></a><span data-ttu-id="45017-284">補足情報: ログインの作成後に実行する手順</span><span class="sxs-lookup"><span data-stu-id="45017-284">Follow Up: Steps to take after you create a login</span></span>  
 <span data-ttu-id="45017-285">ログインの作成が済むと、そのログインで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に接続できるようになりますが、実際の作業を行うための十分な権限があるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="45017-285">After creating a login, the login can connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], but does not necessarily have sufficient permission to perform any useful work.</span></span> <span data-ttu-id="45017-286">ログインに関して一般的に行われる操作について説明するトピックへのリンクを次に示します。</span><span class="sxs-lookup"><span data-stu-id="45017-286">The following list provides links to common login actions.</span></span>  
  
-   <span data-ttu-id="45017-287">ログインをロールに参加させるには、「 [ロールの追加](join-a-role.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-287">To have the login join a role, see [Join a Role](join-a-role.md).</span></span>  
  
-   <span data-ttu-id="45017-288">データベースの使用をログインに承認するには、「 [データベース ユーザーの作成](../authentication-access/create-a-database-user.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-288">To authorize a login to use a database, see [Create a Database User](../authentication-access/create-a-database-user.md).</span></span>  
  
-   <span data-ttu-id="45017-289">ログインに権限を付与するには、「 [プリンシパルに対する権限の許可](grant-a-permission-to-a-principal.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45017-289">To grant a permission to a login, see [Grant a Permission to a Principal](grant-a-permission-to-a-principal.md).</span></span>  
  
  
