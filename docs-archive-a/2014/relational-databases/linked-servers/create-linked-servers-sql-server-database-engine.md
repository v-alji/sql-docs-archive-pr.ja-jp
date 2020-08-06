---
title: リンク サーバーの作成 (SQL Server データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.linkedserver.properties.general.f1
- sql12.swb.linkedserver.properties.security.f1
- sql12.swb.linkedserver.properties.provider.f1
- sql12.swb.linkedserver.properties.options.f1
helpviewer_keywords:
- linked servers [SQL Server], creating
ms.assetid: 3228065d-de8f-4ece-a9b1-e06d3dca9310
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b28468db1024a9789364e5b6e5c115cba71fa9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714354"
---
# <a name="create-linked-servers-sql-server-database-engine"></a><span data-ttu-id="b9434-102">リンク サーバーの作成 (SQL Server データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="b9434-102">Create Linked Servers (SQL Server Database Engine)</span></span>
  <span data-ttu-id="b9434-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してリンク サーバーを作成し、別の [!INCLUDE[tsql](../../includes/tsql-md.md)]からデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9434-103">This topic shows how to create a linked server and access data from another [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b9434-104">リンク サーバーを作成すると、複数のソースのデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-104">By creating a linked server,  you can work with data from multiple sources.</span></span> <span data-ttu-id="b9434-105">リンク サーバーは別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスである必要はありませんが、そのようにするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="b9434-105">The linked server does not have to be another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but that is a common scenario.</span></span>  
  
##  <a name="background"></a><a name="Background"></a> <span data-ttu-id="b9434-106">背景情報</span><span class="sxs-lookup"><span data-stu-id="b9434-106">Background</span></span>  
 <span data-ttu-id="b9434-107">リンク サーバーを使用すると、OLE DB データ ソースに対する異種の分散クエリの利用が可能になります。</span><span class="sxs-lookup"><span data-stu-id="b9434-107">A linked server allows for access to distributed, heterogeneous queries against OLE DB data sources.</span></span> <span data-ttu-id="b9434-108">リンク サーバーを作成すると、このサーバーに対して分散クエリを実行でき、クエリを使用して複数のデータ ソースのテーブルを結合できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-108">After a linked server is created, distributed queries can be run against this server, and queries can join tables from more than one data source.</span></span> <span data-ttu-id="b9434-109">リンク サーバーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスとして定義した場合は、リモート ストアド プロシージャを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-109">If the linked server is defined as an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], remote stored procedures can be executed.</span></span>  
  
 <span data-ttu-id="b9434-110">リンク サーバーの機能と必須の引数は大きく異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="b9434-110">The capabilities and required arguments of the linked server can vary significantly.</span></span> <span data-ttu-id="b9434-111">このトピックでは、一般的な例を紹介しますが、すべてのオプションについて説明しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="b9434-111">The examples in this topic provide a typical example but all options are not described.</span></span> <span data-ttu-id="b9434-112">詳細については、「 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)からデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9434-112">For more information, see [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b9434-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b9434-113">Security</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="b9434-114">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="b9434-114">Permissions</span></span>  
 <span data-ttu-id="b9434-115">ステートメントを使用する場合 [!INCLUDE[tsql](../../includes/tsql-md.md)] `ALTER ANY LINKED SERVER` は、サーバーに対する権限、または**setupadmin**固定サーバーロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="b9434-115">When using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, requires `ALTER ANY LINKED SERVER` permission on the server or membership in the **setupadmin** fixed server role.</span></span> <span data-ttu-id="b9434-116">を使用する場合 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] `CONTROL SERVER` は、 **sysadmin**固定サーバーロールの権限またはメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="b9434-116">When using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] requires `CONTROL SERVER` permission or membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="how-to-create-a-linked-server"></a><a name="Procedures"></a> <span data-ttu-id="b9434-117">リンク サーバーを作成する方法</span><span class="sxs-lookup"><span data-stu-id="b9434-117">How to Create a Linked Server</span></span>  
 <span data-ttu-id="b9434-118">次のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-118">You can use any of the following:</span></span>  
  
-   [<span data-ttu-id="b9434-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b9434-119">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="b9434-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b9434-120">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b9434-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b9434-121">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-linked-server-to-another-instance-of-sql-server-using-sql-server-management-studio"></a><span data-ttu-id="b9434-122">SQL Server Management Studio を使用して別の SQL Server インスタンスへのリンク サーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b9434-122">To create a linked server to another instance of SQL Server Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b9434-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、オブジェクト エクスプローラーを開きます。次に、 **[サーバー オブジェクト]** を展開し、 **[リンク サーバー]** を右クリックして、 **[新しいリンク サーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9434-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer, expand **Server Objects**, right-click **Linked Servers**, and then click **New Linked Server**.</span></span>  
  
2.  <span data-ttu-id="b9434-124">**[全般]** ページの **[リンク サーバー]** ボックスに、リンク先の **SQL Server** インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9434-124">On the **General** page, in the **Linked server** box, type the name of the instance of **SQL Server** that you area linking to.</span></span>  
  
     <span data-ttu-id="b9434-125">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="b9434-125">**SQL Server**</span></span>  
     <span data-ttu-id="b9434-126">リンク サーバーを [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-126">Identify the linked server as an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b9434-127">この方法で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リンク サーバーを定義する場合、 **[リンク サーバー]** にはサーバーのネットワーク名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-127">If you use this method of defining a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] linked server, the name specified in **Linked server** must be the network name of the server.</span></span> <span data-ttu-id="b9434-128">さらに、サーバーから取得されるテーブルは、リンク サーバーのログイン用に定義されている既定のデータベースから取得されます。</span><span class="sxs-lookup"><span data-stu-id="b9434-128">Also, any tables retrieved from the server are from the default database defined for the login on the linked server.</span></span>  
  
     <span data-ttu-id="b9434-129">**[その他のデータ ソース]**</span><span class="sxs-lookup"><span data-stu-id="b9434-129">**Other data source**</span></span>  
     <span data-ttu-id="b9434-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外の OLE DB サーバーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-130">Specify an OLE DB server type other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b9434-131">このオプションをクリックすると、その下にあるオプションを指定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b9434-131">Clicking this option activates the options below it.</span></span>  
  
     <span data-ttu-id="b9434-132">**プロバイダー**</span><span class="sxs-lookup"><span data-stu-id="b9434-132">**Provider**</span></span>  
     <span data-ttu-id="b9434-133">リスト ボックスから OLE DB データ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="b9434-133">Select an OLE DB data source from the list box.</span></span> <span data-ttu-id="b9434-134">OLE DB プロバイダーは、特定の PROGID を使用してレジストリに登録されます。</span><span class="sxs-lookup"><span data-stu-id="b9434-134">The OLE DB provider is registered with the given PROGID in the registry.</span></span>  
  
     <span data-ttu-id="b9434-135">**[製品名]**</span><span class="sxs-lookup"><span data-stu-id="b9434-135">**Product name**</span></span>  
     <span data-ttu-id="b9434-136">リンク サーバーとして追加する OLE DB データ ソースの製品名を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9434-136">Type the product name of the OLE DB data source to add as a linked server.</span></span>  
  
     <span data-ttu-id="b9434-137">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="b9434-137">**Data source**</span></span>  
     <span data-ttu-id="b9434-138">OLE DB プロバイダーで解釈されるデータ ソースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9434-138">Type the name of the data source as interpreted by the OLE DB provider.</span></span> <span data-ttu-id="b9434-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続する場合は、インスタンス名を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9434-139">If you are connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], provide the instance name.</span></span>  
  
     <span data-ttu-id="b9434-140">**[プロバイダー文字列]**</span><span class="sxs-lookup"><span data-stu-id="b9434-140">**Provider string**</span></span>  
     <span data-ttu-id="b9434-141">データ ソースに対応する OLE DB プロバイダーの一意なプログラム識別子 (PROGID) を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9434-141">Type the unique programmatic identifier (PROGID) of the OLE DB provider that corresponds to the data source.</span></span> <span data-ttu-id="b9434-142">有効なプロバイダー文字列の例については、「 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)からデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9434-142">For examples of valid provider strings, see [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
     <span data-ttu-id="b9434-143">**Location**</span><span class="sxs-lookup"><span data-stu-id="b9434-143">**Location**</span></span>  
     <span data-ttu-id="b9434-144">OLE DB プロバイダーで解釈されるデータベースの場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9434-144">Type the location of the database as interpreted by the OLE DB provider.</span></span>  
  
     <span data-ttu-id="b9434-145">**カタログ**</span><span class="sxs-lookup"><span data-stu-id="b9434-145">**Catalog**</span></span>  
     <span data-ttu-id="b9434-146">OLE DB プロバイダーへの接続を作成するときに使用するカタログの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9434-146">Type the name of the catalog to use when making a connection to the OLE DB provider.</span></span>  
  
     <span data-ttu-id="b9434-147">リンク サーバーに接続できるかどうかをテストするには、オブジェクト エクスプローラーでリンク サーバーを右クリックし、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9434-147">To test the ability to connect to a linked server, in Object Explorer, right-click the linked server and then click **Test Connection**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b9434-148">**SQL Server** インスタンスが既定のインスタンスの場合は、 **SQL Server**インスタンスをホストするコンピューターの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9434-148">If the instance of **SQL Server** is the default instance, enter the name of the computer that hosts the instance of **SQL Server**.</span></span> <span data-ttu-id="b9434-149">**SQL Server** が名前付きインスタンスの場合は、コンピューターの名前とインスタンスの名前を入力します (例: **Accounting\SQLExpress**)。</span><span class="sxs-lookup"><span data-stu-id="b9434-149">If the **SQL Server** is a named instance, enter the name of the computer and the name of the instance, such as **Accounting\SQLExpress**.</span></span>  
  
3.  <span data-ttu-id="b9434-150">**[サーバーの種類]** 領域で **[SQL Server]** をクリックし、リンク サーバーが別の **SQL Server** インスタンスであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-150">In the **Server type** area, select **SQL Server** to indicate that the linked server is another instance of **SQL Server**.</span></span>  
  
4.  <span data-ttu-id="b9434-151">**[セキュリティ]** ページで、元の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリンク サーバーに接続するときに使用するセキュリティ コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-151">On the **Security** page, specify the security context that will be used when the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to the linked server.</span></span> <span data-ttu-id="b9434-152">ユーザーがドメイン ログインを使用して接続するドメイン環境では、 **[ログインの現在のセキュリティ コンテキストを使用する]** を選択することが最適な場合が多くあります。</span><span class="sxs-lookup"><span data-stu-id="b9434-152">In a domain environment where users are connecting by using their domain logins, selecting **Be made using the login's current security context** is often the best choice.</span></span> <span data-ttu-id="b9434-153">ユーザーが **SQL Server** ログインを使用して元の **SQL Server** に接続する場合は、 **[このセキュリティ コンテキストを使用する]** をクリックして、リンク サーバーでの認証に必要な資格情報を指定することが最適です。</span><span class="sxs-lookup"><span data-stu-id="b9434-153">When users connect to the original **SQL Server** by using a **SQL Server** login, the best choice is often to select **By using this security context**, and then providing the necessary credentials to authenticate at the linked server.</span></span>  
  
     <span data-ttu-id="b9434-154">**[ローカル ログイン]**</span><span class="sxs-lookup"><span data-stu-id="b9434-154">**Local login**</span></span>  
     <span data-ttu-id="b9434-155">リンク サーバーに接続できるローカル ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-155">Specify the local login that can connect to the linked server.</span></span> <span data-ttu-id="b9434-156">ローカル ログインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログインまたは Windows 認証ログインのいずれかを使用するログインにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b9434-156">The local login can be either a login using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication or a Windows Authentication login.</span></span> <span data-ttu-id="b9434-157">この一覧を使用して、特定のログインへの接続を制限することも、一部のログインが別のログインとして接続できるように設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9434-157">Use this list to restrict the connection to specific logins, or to allow some logins to connect as a different login.</span></span>  
  
     <span data-ttu-id="b9434-158">**Impersonate**</span><span class="sxs-lookup"><span data-stu-id="b9434-158">**Impersonate**</span></span>  
     <span data-ttu-id="b9434-159">ローカル ログインからリンク サーバーにユーザー名とパスワードを渡します。</span><span class="sxs-lookup"><span data-stu-id="b9434-159">Pass the username and password from the local login to the linked server.</span></span> <span data-ttu-id="b9434-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証の場合、まったく同じ名前とパスワードを持つログインがリモート サーバーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-160">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, a login with the exact same name and password must exist on the remote server.</span></span> <span data-ttu-id="b9434-161">Windows ログインの場合、ログインがリンク サーバー上で有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-161">For Windows logins, the login must be a valid login on the linked server.</span></span>  
  
     <span data-ttu-id="b9434-162">権限借用を使用するには、委任の要件を満たすように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-162">To use impersonation, the configuration must meet the requirement for delegation.</span></span>  
  
     <span data-ttu-id="b9434-163">**[リモート ユーザー]**</span><span class="sxs-lookup"><span data-stu-id="b9434-163">**Remote User**</span></span>  
     <span data-ttu-id="b9434-164">リモート ユーザーを使用して、 **[ローカル ログイン]** で定義されないユーザーをマップします。</span><span class="sxs-lookup"><span data-stu-id="b9434-164">Use the remote user to map users not defined in **Local login**.</span></span> <span data-ttu-id="b9434-165">**リモート ユーザー** は、リモート サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログインである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-165">The **Remote User** must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login on the remote server.</span></span>  
  
     <span data-ttu-id="b9434-166">**[リモート パスワード]**</span><span class="sxs-lookup"><span data-stu-id="b9434-166">**Remote Password**</span></span>  
     <span data-ttu-id="b9434-167">リモート ユーザーのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-167">Specify the password of the Remote User.</span></span>  
  
     <span data-ttu-id="b9434-168">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="b9434-168">**Add**</span></span>  
     <span data-ttu-id="b9434-169">新しいローカル ログインを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9434-169">Add a new local login.</span></span>  
  
     <span data-ttu-id="b9434-170">**削除**</span><span class="sxs-lookup"><span data-stu-id="b9434-170">**Remove**</span></span>  
     <span data-ttu-id="b9434-171">既存のローカル ログインを削除します。</span><span class="sxs-lookup"><span data-stu-id="b9434-171">Remove an existing local login.</span></span>  
  
     <span data-ttu-id="b9434-172">**[接続を許可しない]**</span><span class="sxs-lookup"><span data-stu-id="b9434-172">**Not be made**</span></span>  
     <span data-ttu-id="b9434-173">一覧で定義されていないログインについて、接続を許可しないように指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-173">Specify that a connection will not be made for logins not defined in the list.</span></span>  
  
     <span data-ttu-id="b9434-174">**[セキュリティ コンテキストを使用しない]**</span><span class="sxs-lookup"><span data-stu-id="b9434-174">**Be made without using a security context**</span></span>  
     <span data-ttu-id="b9434-175">一覧で定義されていないログインについて、セキュリティ コンテキストを使用せずに接続を作成するように指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-175">Specify that a connection will be made without using a security context for logins not defined in the list.</span></span>  
  
     <span data-ttu-id="b9434-176">**[ログインの現在のセキュリティ コンテキストを使用する]**</span><span class="sxs-lookup"><span data-stu-id="b9434-176">**Be made using the login's current security context**</span></span>  
     <span data-ttu-id="b9434-177">一覧で定義されていないログインについて、ログインの現在のセキュリティ コンテキストを使用して接続を作成するように指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-177">Specify that a connection will be made using the current security context of the login for logins not defined in the list.</span></span> <span data-ttu-id="b9434-178">Windows 認証を使用してローカル サーバーに接続する場合は、リモート サーバーへの接続に Windows 資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9434-178">If connected to the local server using Windows Authentication, your windows credentials will be used to connect to the remote server.</span></span> <span data-ttu-id="b9434-179">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用してローカル サーバーに接続する場合は、リモート サーバーへの接続にログイン名とパスワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9434-179">If connected to the local server using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, login name and password will be used to connect to the remote server.</span></span> <span data-ttu-id="b9434-180">この場合、まったく同じ名前とパスワードを持つログインがリモート サーバーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-180">In this case a login with the exact same name and password must exist on the remote server.</span></span>  
  
     <span data-ttu-id="b9434-181">**[このセキュリティ コンテキストを使用する]**</span><span class="sxs-lookup"><span data-stu-id="b9434-181">**Be made using this security context**</span></span>  
     <span data-ttu-id="b9434-182">一覧で定義されていないログインについて、 **[リモート ログイン]** ボックスおよび **[パスワード]** ボックスで指定したログインとパスワードを使用して接続を作成するように指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-182">Specify that a connection will be made using the login and password specified in the **Remote login** and **With password** boxes for logins not defined in the list.</span></span> <span data-ttu-id="b9434-183">リモート ログインは、リモート サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログインである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-183">The remote login must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login on the remote server.</span></span>  
  
5.  <span data-ttu-id="b9434-184">必要に応じてサーバー オプションを表示または指定する場合は、 **[サーバー オプション]**  ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9434-184">Optionally, to view or specify server options, click the **Server Options**  page.</span></span>  
  
     <span data-ttu-id="b9434-185">**[照合順序互換]**</span><span class="sxs-lookup"><span data-stu-id="b9434-185">**Collation Compatible**</span></span>  
     <span data-ttu-id="b9434-186">リンク サーバーに対する分散クエリの実行に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="b9434-186">Affects Distributed Query execution against linked servers.</span></span> <span data-ttu-id="b9434-187">このオプションを true に設定した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、文字セットと照合順序 (並べ替え順) に関して、リンク サーバー内のすべての文字がローカル サーバーと互換性があると見なします。</span><span class="sxs-lookup"><span data-stu-id="b9434-187">If this option is set to true, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assumes that all characters in the linked server are compatible with the local server, with regard to character set and collation sequence (or sort order).</span></span> <span data-ttu-id="b9434-188">これにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からプロバイダーに文字を含む列の比較を送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b9434-188">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to send comparisons on character columns to the provider.</span></span> <span data-ttu-id="b9434-189">このオプションが設定されていない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では文字列を含む列の比較の評価は常にローカルで行われます。</span><span class="sxs-lookup"><span data-stu-id="b9434-189">If this option is not set, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] always evaluates comparisons on character columns locally.</span></span>  
  
     <span data-ttu-id="b9434-190">このオプションは、リンク サーバーに対応するデータ ソースがローカル サーバーと同じ文字セットと並べ替え順を持っていることが確認できている場合のみ設定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-190">This option should be set only if it is certain that the data source corresponding to the linked server has the same character set and sort order as the local server.</span></span>  
  
     <span data-ttu-id="b9434-191">**データアクセス**</span><span class="sxs-lookup"><span data-stu-id="b9434-191">**Data Access**</span></span>  
     <span data-ttu-id="b9434-192">分散クエリ アクセスに対してリンク サーバーを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="b9434-192">Enables and disables a linked server for distributed query access.</span></span>  
  
     <span data-ttu-id="b9434-193">**RPC**</span><span class="sxs-lookup"><span data-stu-id="b9434-193">**RPC**</span></span>  
     <span data-ttu-id="b9434-194">指定されたサーバーからの RPC を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b9434-194">Enables RPC from the specified server.</span></span>  
  
     <span data-ttu-id="b9434-195">**[RPC 出力]**</span><span class="sxs-lookup"><span data-stu-id="b9434-195">**RPC Out**</span></span>  
     <span data-ttu-id="b9434-196">指定されたサーバーへの RPC を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b9434-196">Enables RPC to the specified server.</span></span>  
  
     <span data-ttu-id="b9434-197">**[リモート照合順序を使用]**</span><span class="sxs-lookup"><span data-stu-id="b9434-197">**Use Remote Collation**</span></span>  
     <span data-ttu-id="b9434-198">リモート列とローカル サーバーのどちらの照合順序を使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-198">Determines whether the collation of a remote column or of a local server will be used.</span></span>  
  
     <span data-ttu-id="b9434-199">true の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースに対してはリモート列の照合順序を使用し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のデータ ソースに対しては [照合順序名] で指定した照合順序を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9434-199">If true, the collation of remote columns is used for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data sources, and the collation specified in collation name is used for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data sources.</span></span>  
  
     <span data-ttu-id="b9434-200">false の場合、分散クエリは常にローカル サーバーの既定の照合順序を使用します。[照合順序名] とリモート列の照合順序は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b9434-200">If false, distributed queries will always use the default collation of the local server, while collation name and the collation of remote columns are ignored.</span></span> <span data-ttu-id="b9434-201">既定値は false です。</span><span class="sxs-lookup"><span data-stu-id="b9434-201">The default is false.</span></span>  
  
     <span data-ttu-id="b9434-202">**[照合順序名]**</span><span class="sxs-lookup"><span data-stu-id="b9434-202">**Collation Name**</span></span>  
     <span data-ttu-id="b9434-203">[リモート照合順序を使用] が true、かつ、データ ソースが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースでない場合に、リモート データ ソースが使用する照合順序の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9434-203">Specifies the name of the collation used by the remote data source if use remote collation is true and the data source is not a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source.</span></span> <span data-ttu-id="b9434-204">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がサポートしている照合順序名のいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-204">The name must be one of the collations supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="b9434-205">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外の OLE DB データ ソースにアクセスし、その照合順序が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序のいずれかと一致する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="b9434-205">Use this option when accessing an OLE DB data source other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but whose collation matches one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span>  
  
     <span data-ttu-id="b9434-206">リンク サーバーは、そのサーバー内のすべての列で使用される単一の照合順序をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-206">The linked server must support a single collation to be used for all columns in that server.</span></span> <span data-ttu-id="b9434-207">リンク サーバーが、単一のデータ ソース内で複数の照合順序をサポートしている、またはリンク サーバーの照合順序が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序のいずれかと一致するかどうかが判断できない場合は、このオプションを設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="b9434-207">Do not set this option if the linked server supports multiple collations within a single data source, or if the linked server's collation cannot be determined to match one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span>  
  
     <span data-ttu-id="b9434-208">**接続のタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="b9434-208">**Connection Timeout**</span></span>  
     <span data-ttu-id="b9434-209">リンク サーバーに接続する場合のタイムアウト値です (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="b9434-209">Time-out value in seconds for connecting to a linked server.</span></span>  
  
     <span data-ttu-id="b9434-210">0 の場合は、 **sp_configure** の [remote login timeout](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md) オプションの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9434-210">If 0, use the **sp_configure** default [remote login timeout](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md) option value.</span></span>  
  
     <span data-ttu-id="b9434-211">**クエリのタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="b9434-211">**Query Timeout**</span></span>  
     <span data-ttu-id="b9434-212">リンク サーバーに対するクエリのタイムアウト値です (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="b9434-212">Time-out value in seconds for queries against a linked server.</span></span>  
  
     <span data-ttu-id="b9434-213">0 の場合は、 **sp_configure** の [remote query timeout](../../database-engine/configure-windows/configure-the-remote-query-timeout-server-configuration-option.md) オプションの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9434-213">If 0, use the **sp_configure** default [remote query timeout](../../database-engine/configure-windows/configure-the-remote-query-timeout-server-configuration-option.md) option value.</span></span>  
  
     <span data-ttu-id="b9434-214">**[分散トランザクションのプロモーションを有効化]**</span><span class="sxs-lookup"><span data-stu-id="b9434-214">**Enable Promotion of Distributed Transactions**</span></span>  
     <span data-ttu-id="b9434-215">このオプションを使用して、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) トランザクションにより、サーバー間のプロシージャのアクションを保護します。</span><span class="sxs-lookup"><span data-stu-id="b9434-215">Use this option to protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span> <span data-ttu-id="b9434-216">このオプションが TRUE の場合、リモート ストアド プロシージャを呼び出すと分散トランザクションが開始され、トランザクションは MS DTC に参加します。</span><span class="sxs-lookup"><span data-stu-id="b9434-216">When this option is TRUE, calling a remote stored procedure starts a distributed transaction and enlists the transaction with MS DTC.</span></span> <span data-ttu-id="b9434-217">詳細については、「 [sp_serveroption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)からデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9434-217">For more information, see [sp_serveroption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql).</span></span>  
  
6.  <span data-ttu-id="b9434-218">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9434-218">Click **OK**.</span></span>  
  
##### <a name="to-view-the-provider-options"></a><span data-ttu-id="b9434-219">プロバイダー オプションを表示するには</span><span class="sxs-lookup"><span data-stu-id="b9434-219">To view the provider options</span></span>  
  
-   <span data-ttu-id="b9434-220">プロバイダーを使用可能にするオプションを表示するには、 **プロバイダー オプション]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9434-220">To view the options that the provider makes available, click the **Providers Options** page.</span></span>  
  
     <span data-ttu-id="b9434-221">すべてのプロバイダーで同じオプションを使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b9434-221">All providers do not have the same options available.</span></span> <span data-ttu-id="b9434-222">たとえば、インデックスを利用できるデータ型と利用できないデータ型があります。</span><span class="sxs-lookup"><span data-stu-id="b9434-222">For example, some types of data have indexes available and some might not.</span></span> <span data-ttu-id="b9434-223">このダイアログ ボックスを使用することで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がプロバイダーの機能を認識できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-223">Use this dialog box to help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] understand the capabilities of the provider.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b9434-224">は一般的なデータ プロバイダーをインストールしますが、データを提供する製品が変わると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でインストールされたプロバイダーが最新機能をすべてサポートしているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b9434-224">installs some common data providers, however when the product providing the data changes, the provider installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not support all the newest features.</span></span> <span data-ttu-id="b9434-225">データを提供する製品の機能の詳細については、その製品のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9434-225">The best source of information about the capabilities of the product providing the data is the documentation for that product.</span></span>  
  
     <span data-ttu-id="b9434-226">**動的パラメーター**</span><span class="sxs-lookup"><span data-stu-id="b9434-226">**Dynamic parameter**</span></span>  
     <span data-ttu-id="b9434-227">プロバイダーが、パラメーター化クエリに "?" パラメーター マーカー構文を使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="b9434-227">Indicates that the provider allows '?' parameter marker syntax for parameterized queries.</span></span> <span data-ttu-id="b9434-228">このオプションは、プロバイダーが **ICommandWithParameters** インターフェイスをサポートしており、パラメーター化マーカーとして "?" をサポートしている場合にのみ設定してください。</span><span class="sxs-lookup"><span data-stu-id="b9434-228">Set this option only if the provider supports the **ICommandWithParameters** interface and supports a '?' as the parameter marker.</span></span> <span data-ttu-id="b9434-229">このオプションを設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はプロバイダーに対してパラメーター化クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-229">Setting this option allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute parameterized queries against the provider.</span></span> <span data-ttu-id="b9434-230">プロバイダーに対してパラメーター化クエリを実行できることにより、特定のクエリではパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="b9434-230">The ability to execute parameterized queries against the provider can result in better performance for certain queries.</span></span>  
  
     <span data-ttu-id="b9434-231">**[入れ子になったクエリ]**</span><span class="sxs-lookup"><span data-stu-id="b9434-231">**Nested queries**</span></span>  
     <span data-ttu-id="b9434-232">プロバイダーが、入れ子になった  `SELECT` ステートメントを FROM 句内で使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="b9434-232">Indicates that the provider allows nested  `SELECT` statements in the FROM clause.</span></span> <span data-ttu-id="b9434-233">このオプションを設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は SELECT ステートメントを FROM 句の中で入れ子にする必要のある特定のクエリをプロバイダーに委任できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-233">Setting this option allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to delegate certain queries to the provider that require nesting SELECT statements in the FROM clause.</span></span>  
  
     <span data-ttu-id="b9434-234">**[レベル 0 のみ]**</span><span class="sxs-lookup"><span data-stu-id="b9434-234">**Level zero only**</span></span>  
     <span data-ttu-id="b9434-235">プロバイダーに対して起動できるのはレベル 0 の OLE DB インターフェイスだけです。</span><span class="sxs-lookup"><span data-stu-id="b9434-235">Only level 0 OLE DB interfaces are invoked against the provider.</span></span>  
  
     <span data-ttu-id="b9434-236">**[InProcess 許可]**</span><span class="sxs-lookup"><span data-stu-id="b9434-236">**Allow inprocess**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b9434-237">で、インプロセス サーバーとしてプロバイダーのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-237">allows the provider to be instantiated as an in-process server.</span></span> <span data-ttu-id="b9434-238">このオプションを設定しない場合、既定の動作として、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス外でプロバイダーのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b9434-238">When this option is not set, the default behavior is to instantiate the provider outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="b9434-239">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセス外でプロバイダーのインスタンスが作成されると、プロバイダーでエラーが発生しても、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="b9434-239">Instantiating the provider outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process protects the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process from errors in the provider.</span></span> <span data-ttu-id="b9434-240">また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセス外でインスタンスが作成されたプロバイダーでは、長い列 (`text`、`ntext`、または `image`) を参照する更新や挿入はできません。</span><span class="sxs-lookup"><span data-stu-id="b9434-240">When the provider is instantiated outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process, updates or inserts referencing long columns (`text`, `ntext`, or `image`) are not allowed.</span></span>  
  
     <span data-ttu-id="b9434-241">**[トランザクション更新以外]**</span><span class="sxs-lookup"><span data-stu-id="b9434-241">**Non transacted updates**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b9434-242">で、 **ITransactionLocal** を利用できない場合でも更新を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9434-242">allows updates, even if **ITransactionLocal** is not available.</span></span> <span data-ttu-id="b9434-243">このオプションがオンの場合、プロバイダーはトランザクションをサポートしないので、プロバイダーに対する更新を回復することはできません。</span><span class="sxs-lookup"><span data-stu-id="b9434-243">If this option is enabled, updates against the provider are not recoverable, because the provider does not support transactions.</span></span>  
  
     <span data-ttu-id="b9434-244">**[アクセス パスとしてのインデックス]**</span><span class="sxs-lookup"><span data-stu-id="b9434-244">**Index as access path**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b9434-245">はプロバイダーのインデックスを使用してデータをフェッチしようとします。</span><span class="sxs-lookup"><span data-stu-id="b9434-245">attempts to use indexes of the provider to fetch data.</span></span> <span data-ttu-id="b9434-246">既定では、インデックスはメタデータにのみ使用され、開かれることはありません。</span><span class="sxs-lookup"><span data-stu-id="b9434-246">By default, indexes are used only for metadata and are never opened</span></span>  
  
     <span data-ttu-id="b9434-247">**[アドホック アクセス禁止]**</span><span class="sxs-lookup"><span data-stu-id="b9434-247">**Disallow ad hoc access**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b9434-248">では、OLE DB プロバイダーに対して OPENROWSET 関数と OPENDATASOURCE 関数を使用したアドホック アクセスは許可されません。</span><span class="sxs-lookup"><span data-stu-id="b9434-248">does not allow ad hoc access through the OPENROWSET and OPENDATASOURCE functions against the OLE DB provider.</span></span> <span data-ttu-id="b9434-249">このオプションを設定しない場合も、アドホック アクセスは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により禁止されます。</span><span class="sxs-lookup"><span data-stu-id="b9434-249">When this option is not set, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] also does not allow ad hoc access.</span></span>  
  
     <span data-ttu-id="b9434-250">**['Like' 演算子をサポートします]**</span><span class="sxs-lookup"><span data-stu-id="b9434-250">**Supports 'Like' operator**</span></span>  
     <span data-ttu-id="b9434-251">プロバイダーが LIKE キーワードを使用したクエリをサポートしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="b9434-251">Indicates that the provider supports queries using the LIKE key word.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b9434-252">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b9434-252">Using Transact-SQL</span></span>  
 <span data-ttu-id="b9434-253">[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してリンク サーバーを作成するには、[sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) ステートメント、[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) ステートメント、および [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9434-253">To create a linked server by using [!INCLUDE[tsql](../../includes/tsql-md.md)], use the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) and [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql) statements.</span></span>  
  
##### <a name="to-create-a-linked-server-to-another-instance-of-sql-server-using-transact-sql"></a><span data-ttu-id="b9434-254">Transact-SQL を使用して別の SQL Server インスタンスへのリンク サーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b9434-254">To create a linked server to another instance of SQL Server using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="b9434-255">クエリ エディターで、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを入力して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] という名前の `SRVR002\ACCTG`インスタンスにリンクします。</span><span class="sxs-lookup"><span data-stu-id="b9434-255">In Query Editor, enter the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command to link to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named `SRVR002\ACCTG`:</span></span>  
  
    ```sql  
    USE [master]  
    GO  
    EXEC master.dbo.sp_addlinkedserver   
        @server = N'SRVR002\ACCTG',   
        @srvproduct=N'SQL Server' ;  
    GO  
  
    ```  
  
2.  <span data-ttu-id="b9434-256">次のコードを実行して、リンク サーバーを使用しているログインのドメイン資格情報を使用するようにリンク サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="b9434-256">Execute the following code to configure the linked server to use the domain credentials of the login that is using the linked server.</span></span>  
  
    ```sql  
    EXEC master.dbo.sp_addlinkedsrvlogin   
        @rmtsrvname = N'SRVR002\ACCTG',   
        @locallogin = NULL ,   
        @useself = N'True' ;  
    GO  
  
    ```  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-linked-server"></a><a name="FollowUp"></a><span data-ttu-id="b9434-257">補足情報: リンクサーバーの作成後に実行する手順</span><span class="sxs-lookup"><span data-stu-id="b9434-257">Follow Up: Steps to take after you create a linked server</span></span>  
  
#### <a name="to-test-the-linked-server"></a><span data-ttu-id="b9434-258">リンク サーバーをテストするには</span><span class="sxs-lookup"><span data-stu-id="b9434-258">To test the linked server</span></span>  
  
-   <span data-ttu-id="b9434-259">次のコードを実行して、リンク サーバーへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="b9434-259">Execute the following code to test the connection to the linked server.</span></span> <span data-ttu-id="b9434-260">この例は、リンク サーバーにあるデータベースの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="b9434-260">This example the returns the names of the databases on the linked server.</span></span>  
  
    ```sql  
    SELECT name FROM [SRVR002\ACCTG].master.sys.databases ;  
    GO  
  
    ```  
  
#### <a name="writing-a-query-that-joins-tables-from-a-linked-server"></a><span data-ttu-id="b9434-261">リンク サーバーのテーブルを結合するクエリの記述</span><span class="sxs-lookup"><span data-stu-id="b9434-261">Writing a query that joins tables from a linked server</span></span>  
  
-   <span data-ttu-id="b9434-262">4 つの要素で構成される名前を使用して、リンク サーバー上のオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="b9434-262">Use four-part names to refer to an object on a linked server.</span></span> <span data-ttu-id="b9434-263">次のコードを実行して、ローカル サーバー上のすべてのログインとリンク サーバー上の対応するログインの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9434-263">Execute the following code to return a list of all logins on the local server and their matching logins on the linked server.</span></span>  
  
    ```sql  
    SELECT local.name AS LocalLogins, linked.name AS LinkedLogins  
    FROM master.sys.server_principals AS local  
    LEFT JOIN [SRVR002\ACCTG].master.sys.server_principals AS linked  
        ON local.name = linked.name ;  
    GO  
    ```  
  
     <span data-ttu-id="b9434-264">リンク サーバー ログインに対して NULL が返される場合は、リンク サーバー上にログインが存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="b9434-264">When NULL is returned for the linked server login it indicates that the login does not exist on the linked server.</span></span> <span data-ttu-id="b9434-265">リンク サーバーが別のセキュリティ コンテキストを渡すように構成されている場合、またはリンク サーバーが匿名接続を許可する場合を除き、これらのログインではリンク サーバーを使用できません。</span><span class="sxs-lookup"><span data-stu-id="b9434-265">These logins will not be able to use the linked server unless the linked server is configured to pass a different security context or the linked server accepts anonymous connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9434-266">参照</span><span class="sxs-lookup"><span data-stu-id="b9434-266">See Also</span></span>  
 <span data-ttu-id="b9434-267">[リンク サーバー &#40;データベース エンジン&#41;](linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="b9434-267">[Linked Servers &#40;Database Engine&#41;](linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="b9434-268">[sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b9434-268">[sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) </span></span>  
 [<span data-ttu-id="b9434-269">sp_serveroption &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b9434-269">sp_serveroption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
