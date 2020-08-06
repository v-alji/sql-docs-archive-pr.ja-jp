---
title: サーバー プロパティの表示または変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- viewing server properties
- server properties [SQL Server]
- displaying server properties
- servers [SQL Server], viewing
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 415d4e2d1aaa3166ae4df2dea53b34e064544e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713470"
---
# <a name="view-or-change-server-properties-sql-server"></a><span data-ttu-id="1275a-102">サーバー プロパティの表示または変更 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1275a-102">View or Change Server Properties (SQL Server)</span></span>
  <span data-ttu-id="1275a-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または SQL Server 構成マネージャーを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]のインスタンスのプロパティを表示または変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1275a-103">This topic describes how to view or change the properties of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Configuration Manager.</span></span>  
  
 <span data-ttu-id="1275a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1275a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1275a-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1275a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1275a-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="1275a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1275a-107">Security</span><span class="sxs-lookup"><span data-stu-id="1275a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1275a-108">**サーバーのプロパティを表示または変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="1275a-108">**To view or change server properties, using:**</span></span>  
  
     [<span data-ttu-id="1275a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1275a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1275a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1275a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="1275a-111">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="1275a-111">SQL Server Configuration Manager</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="1275a-112">**フォロー アップ:**  [サーバーのプロパティを変更した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1275a-112">**Follow Up:**  [After you change server properties](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1275a-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="1275a-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1275a-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="1275a-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1275a-115">sp_configure を使用する場合は、構成オプションを設定した後、RECONFIGURE または RECONFIGURE WITH OVERRIDE のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1275a-115">When using sp_configure, you must run either RECONFIGURE or RECONFIGURE WITH OVERRIDE after setting a configuration option.</span></span> <span data-ttu-id="1275a-116">通常、RECONFIGURE WITH OVERRIDE ステートメントは、十分注意して使用する必要がある構成オプション用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="1275a-116">The RECONFIGURE WITH OVERRIDE statement is usually reserved for configuration options that should be used with extreme caution.</span></span> <span data-ttu-id="1275a-117">ただし、RECONFIGURE WITH OVERRIDE はどの構成オプションでも機能します。また、RECONFIGURE WITH OVERRIDE を RECONFIGURE の代わりに使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1275a-117">However, RECONFIGURE WITH OVERRIDE works for all configuration options, and you can use it in place of RECONFIGURE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1275a-118">RECONFIGURE はトランザクション内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="1275a-118">RECONFIGURE executes within a transaction.</span></span> <span data-ttu-id="1275a-119">再構成オプションのいずれかが失敗した場合、すべての再構成操作が無効になります。</span><span class="sxs-lookup"><span data-stu-id="1275a-119">If any of the reconfigure operations fail, none of the reconfigure operations will take effect.</span></span>  
  
-   <span data-ttu-id="1275a-120">一部のプロパティ ページには、Windows Management Instrumentation (WMI) から取得した情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1275a-120">Some property pages present information obtained via Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="1275a-121">これらのページを表示するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を実行しているコンピューターに WMI をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1275a-121">To display those pages, WMI must be installed on the computer running [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1275a-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1275a-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1275a-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="1275a-123">Permissions</span></span>  
 <span data-ttu-id="1275a-124">詳細については、「 [サーバー レベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1275a-124">For more information, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>  
  
 <span data-ttu-id="1275a-125">`sp_configure`既定では、パラメーターを指定しない、または最初のパラメーターだけを指定して、の実行権限をすべてのユーザーに付与します。</span><span class="sxs-lookup"><span data-stu-id="1275a-125">Execute permissions on `sp_configure` with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="1275a-126">両方のパラメーターを使用してを実行し、 `sp_configure` 構成オプションを変更するか、または再構成ステートメントを実行するには、ALTER SETTINGS サーバーレベルのアクセス許可がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1275a-126">To execute `sp_configure` with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="1275a-127">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="1275a-127">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1275a-128">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1275a-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="1275a-129">サーバーのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="1275a-129">To view or change server properties</span></span>  
  
1.  <span data-ttu-id="1275a-130">オブジェクト エクスプローラーでサーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-130">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1275a-131">**[サーバーのプロパティ]** ダイアログ ボックスで、ページをクリックし、そのページに関するサーバーの情報を表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="1275a-131">In the **Server Properties** dialog box, click a page to view or change server information about that page.</span></span> <span data-ttu-id="1275a-132">いくつかのプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="1275a-132">Some properties are read-only.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1275a-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1275a-133">Using Transact-SQL</span></span>  
  
#### <a name="to-view-server-properties-by-using-the-serverproperty-built-in-function"></a><span data-ttu-id="1275a-134">SERVERPROPERTY 組み込み関数を使用してサーバーのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="1275a-134">To view server properties by using the SERVERPROPERTY built-in function</span></span>  
  
1.  <span data-ttu-id="1275a-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="1275a-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1275a-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1275a-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1275a-138">次の例では、 [ステートメント内で](/sql/t-sql/functions/serverproperty-transact-sql) SERVERPROPERTY `SELECT` 組み込み関数を使用することによって、現在のサーバーに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="1275a-138">This example uses the [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) built-in function in a `SELECT` statement to return information about the current server.</span></span> <span data-ttu-id="1275a-139">このシナリオは、Windows ベースのサーバー上に複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがインストールされており、クライアントの現在の接続で使用しているインスタンスと同じインスタンスに対して別の接続を開く必要がある場合に効果的です。</span><span class="sxs-lookup"><span data-stu-id="1275a-139">This scenario is useful when there are multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on a Windows-based server, and the client must open another connection to the same instance that is used by the current connection.</span></span>  
  
    ```sql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysservers-catalog-view"></a><span data-ttu-id="1275a-140">sys.servers カタログ ビューを使用してサーバーのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="1275a-140">To view server properties by using the sys.servers catalog view</span></span>  
  
1.  <span data-ttu-id="1275a-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="1275a-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1275a-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1275a-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1275a-144">この例では、 [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) カタログ ビューをクエリして現在のサーバーの名前 (`name`) と ID (`server_id`)、およびリンク サーバーに接続するための OLE DB プロバイダーの名前 (`provider`) が返されます。</span><span class="sxs-lookup"><span data-stu-id="1275a-144">This example queries the [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) catalog view to return the name (`name`) and ID (`server_id`) of the current server, and the name of the OLE DB provider (`provider`) for connecting to a linked server.</span></span>  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysconfigurations-catalog-view"></a><span data-ttu-id="1275a-145">sys.configurations カタログ ビューを使用してサーバーのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="1275a-145">To view server properties by using the sys.configurations catalog view</span></span>  
  
1.  <span data-ttu-id="1275a-146">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="1275a-146">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1275a-147">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-147">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1275a-148">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-148">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1275a-149">この例では、 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) カタログ ビューをクエリして、現在のサーバー上の各サーバーの構成オプションに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="1275a-149">This example queries the [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view to return information about each server configuration option on the current server.</span></span> <span data-ttu-id="1275a-150">この例では、オプションの名前 (`name`) と説明 (`description`)、およびこのオプションが詳細オプションに含まれているかどうか (`is_advanced`) が返されます。</span><span class="sxs-lookup"><span data-stu-id="1275a-150">The example returns the name (`name`) and description (`description`) of the option and whether the option is an advanced option (`is_advanced`).</span></span>  
  
    ```sql
    USE AdventureWorks2012;
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;
    GO
    ```  
  
#### <a name="to-change-a-server-property-by-using-sp_configure"></a><span data-ttu-id="1275a-151">sp_configure を使用して、サーバーのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="1275a-151">To change a server property by using sp_configure</span></span>  
  
1.  <span data-ttu-id="1275a-152">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="1275a-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1275a-153">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1275a-154">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-154">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1275a-155">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、サーバーのプロパティを変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1275a-155">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to change a server property.</span></span> <span data-ttu-id="1275a-156">この例では、 `fill factor` オプションの値を `100`に変更します。</span><span class="sxs-lookup"><span data-stu-id="1275a-156">The example changes the value of the `fill factor` option to `100`.</span></span> <span data-ttu-id="1275a-157">変更を有効にするには、サーバーを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1275a-157">The server must be restarted before the change can take effect.</span></span>  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="1275a-158">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1275a-158">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="1275a-159">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="1275a-159">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="1275a-160">いくつかのサーバー プロパティは、SQL Server 構成マネージャーを使用して表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="1275a-160">Some server properties can be viewed or changed by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="1275a-161">たとえば、SQL Server のインスタンスのバージョンおよびエディションを表示したり、エラー ログ ファイルの格納場所を変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="1275a-161">For example, you can view the version and edition of the instance of SQL Server, or change the location where error log files are stored.</span></span> <span data-ttu-id="1275a-162">これらのプロパティは、 [サーバー関連の動的管理ビューおよび関数](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)をクエリして表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="1275a-162">These properties can also be viewed by querying the [Server-Related Dynamic Management Views and Functions](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql).</span></span>  
  
#### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="1275a-163">サーバーのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="1275a-163">To view or change server properties</span></span>  
  
1.  <span data-ttu-id="1275a-164">**[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-164">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="1275a-165">**SQL Server 構成マネージャー**で **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-165">In **SQL Server Configuration Manager**, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="1275a-166">詳細ペインで **[SQL Server (\<***instancename***>)]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-166">In the details pane, right-click **SQL Server (\<***instancename***>)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1275a-167">**[SQL Server (\<***instancename***>) のプロパティ]** ダイアログ ボックスの **[サービス]** タブまたは **[詳細設定]** タブで、サーバーのプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1275a-167">In the **SQL Server (\<***instancename***>) Properties** dialog box, change the server properties on the **Service** tab or the **Advanced** tab, and then click **OK**.</span></span>  
  
##  <a name="follow-up-after-you-change-server-properties"></a><a name="FollowUp"></a><span data-ttu-id="1275a-168">補足情報: サーバーのプロパティを変更した後</span><span class="sxs-lookup"><span data-stu-id="1275a-168">Follow Up: After you change server properties</span></span>  
 <span data-ttu-id="1275a-169">いくつかのプロパティでは、変更を有効にするためにサーバーを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1275a-169">For some properties, the server might have to be restarted before the change can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1275a-170">参照</span><span class="sxs-lookup"><span data-stu-id="1275a-170">See Also</span></span>  
 <span data-ttu-id="1275a-171">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1275a-171">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="1275a-172">[SET ステートメント &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1275a-172">[SET Statements &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span></span>  
 <span data-ttu-id="1275a-173">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1275a-173">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="1275a-174">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1275a-174">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="1275a-175">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1275a-175">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="1275a-176">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1275a-176">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="1275a-177">[SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1275a-177">[Configure WMI to Show Server Status in SQL Server Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md) </span></span>  
 <span data-ttu-id="1275a-178">[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1275a-178">[SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="1275a-179">[構成関数 &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1275a-179">[Configuration Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql) </span></span>  
 [<span data-ttu-id="1275a-180">サーバー関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1275a-180">Server-Related Dynamic Management Views and Functions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)  
