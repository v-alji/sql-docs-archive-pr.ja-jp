---
title: データベース ユーザーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.GENERAL.F1
- sql12.swb.user.securables.f1
helpviewer_keywords:
- database users, creating
- creating users with Management Studio
- mapping users
- users [SQL Server], creating
- database user additions [SQL Server]
- database users, mapping
- CREATE USER [Management Studio]
- users [SQL Server], adding
- mapping database users
ms.assetid: 782798d3-9552-4514-9f58-e87be4b264e4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 97fc758c754f5fc8803e988d55147670fc3ff45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714062"
---
# <a name="create-a-database-user"></a><span data-ttu-id="a6ab2-102">データベース ユーザーの作成</span><span class="sxs-lookup"><span data-stu-id="a6ab2-102">Create a Database User</span></span>
  <span data-ttu-id="a6ab2-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、ログインにマップされるデータベース ユーザーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-103">This topic describes how to create a database user mapped to a login in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a6ab2-104">データベース ユーザーは、ログインの ID として、データベースへの接続時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-104">The database user is the identity of the login when it is connected to a database.</span></span> <span data-ttu-id="a6ab2-105">データベース ユーザーとログインには同じ名前を使用できますが、必ずしもその必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-105">The database user can use the same name as the login, but that is not required.</span></span> <span data-ttu-id="a6ab2-106">このトピックは、既存のログインが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-106">This topic assumes that a login already exists in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a6ab2-107">ログインの作成方法の詳細については、「[ログインの作成](create-a-login.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-107">For information about how to create a login, see [Create a Login](create-a-login.md).</span></span>  
  
 <span data-ttu-id="a6ab2-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a6ab2-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a6ab2-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a6ab2-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a6ab2-110">背景</span><span class="sxs-lookup"><span data-stu-id="a6ab2-110">Background</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a6ab2-111">Security</span><span class="sxs-lookup"><span data-stu-id="a6ab2-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a6ab2-112">**次のものを使用してデータベース ユーザーを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="a6ab2-112">**To create a database user, using:**</span></span>  
  
     [<span data-ttu-id="a6ab2-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6ab2-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a6ab2-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6ab2-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a6ab2-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="a6ab2-115">Before You Begin</span></span>  
  
###  <a name="background"></a><a name="Restrictions"></a> <span data-ttu-id="a6ab2-116">背景情報</span><span class="sxs-lookup"><span data-stu-id="a6ab2-116">Background</span></span>  
 <span data-ttu-id="a6ab2-117">ユーザーは、データベース レベルのセキュリティ プリンシパルです。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-117">A user is a database level security principal.</span></span> <span data-ttu-id="a6ab2-118">データベースに接続するためには、データベース ユーザーにログインをマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-118">Logins must be mapped to a database user to connect to a database.</span></span> <span data-ttu-id="a6ab2-119">異なるデータベースには、1 つのログインを異なるユーザーとしてマップすることができますが、各データベースでは 1 人のユーザーとしてのみマップできます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-119">A login can be mapped to different databases as different users but can only be mapped as one user in each database.</span></span> <span data-ttu-id="a6ab2-120">部分的包含データベースでは、ログインを持たないユーザーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-120">In a partially contained database, a user can be created that does not have a login.</span></span> <span data-ttu-id="a6ab2-121">包含データベース ユーザーの詳細については、「[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-121">For more information about contained database users, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span> <span data-ttu-id="a6ab2-122">データベースで guest ユーザーが有効になっている場合は、データベース ユーザーにマップされていないログインでも、guest ユーザーとしてそのデータベースにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-122">If the guest user in a database is enabled, a login that is not mapped to a database user can enter the database as the guest user.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a6ab2-123">guest ユーザーは無効にするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-123">The guest user is ordinarily disabled.</span></span> <span data-ttu-id="a6ab2-124">必要な場合を除き、guest ユーザーは有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-124">Do not enable the guest user unless it is necessary.</span></span>  
  
 <span data-ttu-id="a6ab2-125">セキュリティ プリンシパルとして、ユーザーには権限を許可することができます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-125">As a security principal, permissions can be granted to users.</span></span> <span data-ttu-id="a6ab2-126">ユーザーのスコープはデータベースです。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-126">The scope of a user is the database.</span></span> <span data-ttu-id="a6ab2-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンス上の特定のデータベースに接続するには、データベース ユーザーにログインをマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-127">To connect to a specific database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a login must be mapped to a database user.</span></span> <span data-ttu-id="a6ab2-128">データベース内の権限を許可したり拒否したりする際に、その対象となるのは、ログインではなく、データベース ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-128">Permissions inside the database are granted and denied to the database user, not the login.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a6ab2-129">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a6ab2-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a6ab2-130">Permissions</span><span class="sxs-lookup"><span data-stu-id="a6ab2-130">Permissions</span></span>  
 <span data-ttu-id="a6ab2-131">データベースに対する `ALTER ANY USER` 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-131">Requires `ALTER ANY USER` permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a6ab2-132">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a6ab2-132">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-database-user"></a><span data-ttu-id="a6ab2-133">データベース ユーザーを作成するには</span><span class="sxs-lookup"><span data-stu-id="a6ab2-133">To create a database user</span></span>  
  
1.  <span data-ttu-id="a6ab2-134">オブジェクト エクスプローラーで、 **[データベース]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-134">In Object Explorer, expand the **Databases** folder.</span></span>  
  
2.  <span data-ttu-id="a6ab2-135">新しいデータベース ユーザーを作成するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-135">Expand the database in which to create the new database user.</span></span>  
  
3.  <span data-ttu-id="a6ab2-136">**[セキュリティ]** フォルダーを右クリックし、 **[新規作成]** をポイントして、 **[ユーザー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-136">Right-click the **Security** folder, point to **New**, and select **User...**.</span></span>  
  
4.  <span data-ttu-id="a6ab2-137">[**データベースユーザー-新規作成**] ダイアログボックスの **[全般**] ページで、[**ユーザーの種類**] ボックスの一覧から [ユーザーの種類] ボックスの一覧から1つを選択します。 [ログインを使用し**た sql**ユーザー]、[**ログインを持たない sql ユーザー**]、**証明書にマップ**されたユーザー、**非対称キーにマップ\*\*\*\*されて**いるユーザー</span><span class="sxs-lookup"><span data-stu-id="a6ab2-137">In the **Database User - New** dialog box, on the **General** page, select one of the following user types from the **User type** list: **SQL user with login**, **SQL user without login**, **User mapped to a certificate**, **User mapped to an asymmetric key**, or **Windows user**.</span></span>  
  
5.  <span data-ttu-id="a6ab2-138">**[ユーザー名]** ボックスに、新しいユーザーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-138">In the **User name** box, enter a name for the new user.</span></span> <span data-ttu-id="a6ab2-139">**[ユーザーの種類]** で一覧から **[Windows ユーザー]** を選択した場合は、省略記号 **[...]** をクリックして、 **[ユーザーまたはグループの選択]** ダイアログ ボックスを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-139">If you have chosen **Windows user** from the **User type** list, you can also click the ellipsis **(...)** to open the **Select User or Group** dialog box.</span></span>  
  
6.  <span data-ttu-id="a6ab2-140">**[ログイン名]** ボックスにユーザーのログインを入力します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-140">In the **Login name** box, enter the login for the user.</span></span> <span data-ttu-id="a6ab2-141">または、省略記号 **[...]** をクリックして **[ログインの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-141">Alternately, click the ellipsis **(...)** to open the **Select Login** dialog box.</span></span> <span data-ttu-id="a6ab2-142">**[ログイン名]** は、 **[ユーザーの種類]** で一覧から **[ログインを持つ SQL ユーザー]** または **[Windows ユーザー]** を選択した場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-142">**Login name** is available if you select either **SQL user with login** or **Windows user** from the **User type** list.</span></span>  
  
7.  <span data-ttu-id="a6ab2-143">**[既定のスキーマ]** ボックスで、このユーザーが作成したオブジェクトを所有するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-143">In the **Default schema** box, specifies the schema that will own objects created by this user.</span></span> <span data-ttu-id="a6ab2-144">または、省略記号 **[...]** をクリックして **[スキーマの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-144">Alternately, click the ellipsis **(...)** to open the **Select Schema** dialog box.</span></span> <span data-ttu-id="a6ab2-145">**[既定のスキーマ]** は、 **[ユーザーの種類]** で一覧から **[ログインを持つ SQL ユーザー]** 、 **[ログインを持たない SQL ユーザー]** 、または **[Windows ユーザー]** を選択した場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-145">**Default schema** is available if you select either **SQL user with login**, **SQL user without login**, or **Windows user** from the **User type** list.</span></span>  
  
8.  <span data-ttu-id="a6ab2-146">**[証明書名]** ボックスに、データベース ユーザーに使用する証明書を入力します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-146">In the **Certificate name** box, enter the certificate to be used for the database user.</span></span> <span data-ttu-id="a6ab2-147">または、省略記号 **[...]** をクリックして **[証明書の選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-147">Alternately, click the ellipsis **(...)** to open the **Select Certificate** dialog box.</span></span> <span data-ttu-id="a6ab2-148">**[証明書名]** は、 **[ユーザーの種類]** で一覧から **[証明書にマップされたユーザー]** を選択した場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-148">**Certificate name** is available if you select **User mapped to a certificate** from the **User type** list.</span></span>  
  
9. <span data-ttu-id="a6ab2-149">**[非対称キー名]**  ボックスに、データベース ユーザーに使用するキーを入力します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-149">In the **Asymmetric key name**  box, enter the key to be used for the database user.</span></span> <span data-ttu-id="a6ab2-150">または、省略記号 **[...]** をクリックして **[非対称キーの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-150">Alternately, click the ellipsis **(...)** to open the **Select Asymmetric Key** dialog box.</span></span> <span data-ttu-id="a6ab2-151">**[非対称キー名]** は、 **[ユーザーの種類]** で一覧から **[非対称キーにマップされたユーザー]** を選択した場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-151">**Asymmetric key name** is available if you select **User mapped to an asymmetric key** from the **User type** list.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="a6ab2-152">追加オプション</span><span class="sxs-lookup"><span data-stu-id="a6ab2-152">Additional Options</span></span>  
 <span data-ttu-id="a6ab2-153">**[データベース ユーザー - 新規]** ダイアログ ボックスには、次の 4 つの追加ページで使用できるオプションも用意されています。 **[所有されているスキーマ]** 、 **[メンバーシップ]** 、 **[セキュリティ保護可能なリソース]** 、 **[拡張プロパティ]** です。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-153">The **Database User - New** dialog box also offers options on four additional pages: **Owned Schemas**, **Membership**, **Securables**, and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="a6ab2-154">**[所有されているスキーマ]** ページには、新しいデータベース ユーザーが所有できるすべてのスキーマが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-154">The **Owned Schemas** page lists all possible schemas that can be owned by the new database user.</span></span> <span data-ttu-id="a6ab2-155">データベース ユーザーのスキーマを追加または削除するには、 **[このユーザーが所有するスキーマ]** で、スキーマの横のチェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-155">To add schemas to or remove them from a database user, under **Schemas owned by this user**, select or clear the check boxes next to the schemas.</span></span>  
  
-   <span data-ttu-id="a6ab2-156">**[メンバーシップ]** ページには、新しいデータベース ユーザーが所有できるすべてのデータベース メンバーシップ ロールが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-156">The **Membership** page lists all possible database membership roles that can be owned by the new database user.</span></span> <span data-ttu-id="a6ab2-157">データベース ユーザーのロールを追加または削除するには、 **[データベース ロールのメンバーシップ]** で、ロールの横のチェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-157">To add roles to or remove them from a database user, under **Database role membership**, select or clear the check boxes next to the roles.</span></span>  
  
-   <span data-ttu-id="a6ab2-158">**[セキュリティ保護可能なリソース]** ページには、すべてのセキュリティ保護可能なリソースと、ログインに付与できる、セキュリティ保護可能なリソースに対する権限が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-158">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="a6ab2-159">**[拡張プロパティ]** ページでは、カスタム プロパティをデータベース ユーザーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-159">The **Extended properties** page allows you to add custom properties to database users.</span></span> <span data-ttu-id="a6ab2-160">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-160">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="a6ab2-161">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="a6ab2-161">**Database**</span></span>  
     <span data-ttu-id="a6ab2-162">選択しているデータベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-162">Displays the name of the selected database.</span></span> <span data-ttu-id="a6ab2-163">このフィールドは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-163">This field is read-only.</span></span>  
  
     <span data-ttu-id="a6ab2-164">**Collation**</span><span class="sxs-lookup"><span data-stu-id="a6ab2-164">**Collation**</span></span>  
     <span data-ttu-id="a6ab2-165">選択されているデータベースに使用する照合順序を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-165">Displays the collation used for the selected database.</span></span> <span data-ttu-id="a6ab2-166">このフィールドは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-166">This field is read-only.</span></span>  
  
     <span data-ttu-id="a6ab2-167">**Properties**</span><span class="sxs-lookup"><span data-stu-id="a6ab2-167">**Properties**</span></span>  
     <span data-ttu-id="a6ab2-168">オブジェクトの拡張プロパティを表示または指定します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-168">View or specify the extended properties for the object.</span></span> <span data-ttu-id="a6ab2-169">各拡張プロパティは、オブジェクトに関連付けられたメタデータの名前/値ペアで構成されています。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-169">Each extended property consists of a name/value pair of metadata associated with the object.</span></span>  
  
     <span data-ttu-id="a6ab2-170">**省略記号 (...)**</span><span class="sxs-lookup"><span data-stu-id="a6ab2-170">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="a6ab2-171">**[値]** の後ろにある省略記号 **[...]** をクリックすると、 **[拡張プロパティの値]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-171">Click the ellipsis **(...)** after **Value** to open the **Value for Extended Property** dialog box.</span></span> <span data-ttu-id="a6ab2-172">ここでは、より大きなテキスト ボックスを使用して拡張プロパティの値を入力または表示できます。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-172">Type or view the value of the extended property in this larger location.</span></span> <span data-ttu-id="a6ab2-173">詳細については、「 [拡張プロパティの値ダイアログ ボックス](../../databases/value-for-extended-property-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-173">For more information, see [Value for Extended Property Dialog Box](../../databases/value-for-extended-property-dialog-box.md).</span></span>  
  
     <span data-ttu-id="a6ab2-174">**削除**</span><span class="sxs-lookup"><span data-stu-id="a6ab2-174">**Delete**</span></span>  
     <span data-ttu-id="a6ab2-175">選択されている拡張プロパティを削除します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-175">Removes the selected extended property.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a6ab2-176">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a6ab2-176">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database-user"></a><span data-ttu-id="a6ab2-177">データベース ユーザーを作成するには</span><span class="sxs-lookup"><span data-stu-id="a6ab2-177">To create a database user</span></span>  
  
1.  <span data-ttu-id="a6ab2-178">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-178">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a6ab2-179">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-179">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a6ab2-180">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-180">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the login AbolrousHazem with password '340$Uuxwp7Mcxo7Khy'.  
    CREATE LOGIN AbolrousHazem   
        WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
    GO  
  
    -- Creates a database user for the login created above.  
    CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
    GO  
    ```  
  
 <span data-ttu-id="a6ab2-181">詳細については、「[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ab2-181">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ab2-182">参照</span><span class="sxs-lookup"><span data-stu-id="a6ab2-182">See Also</span></span>  
 [<span data-ttu-id="a6ab2-183">プリンシパル &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="a6ab2-183">Principals &#40;Database Engine&#41;</span></span>](principals-database-engine.md)  
  
  
