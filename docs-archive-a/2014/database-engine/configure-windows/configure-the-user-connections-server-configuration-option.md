---
title: user connections サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 12/02/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- simultaneous connections [SQL Server]
- user connections option [SQL Server]
- users [SQL Server], simultaneous connections
- maximum number of simultaneous user connections
- connections [SQL Server], simultaneous
ms.assetid: 53beee6e-59fe-4276-9abb-8f1cec2a3508
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68fbb4a17de131c128b5b1bb7cfb35a33b9d0037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632097"
---
# <a name="configure-the-user-connections-server-configuration-option"></a><span data-ttu-id="fb733-102">user connections サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="fb733-102">Configure the user connections Server Configuration Option</span></span>
  <span data-ttu-id="fb733-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] user connections [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb733-103">This topic describes how to set the **user connections** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fb733-104">**user connections** オプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスで許可される同時ユーザー接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="fb733-104">The **user connections** option specifies the maximum number of simultaneous user connections that are allowed on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fb733-105">許可される実際のユーザー接続数は、使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンと、使用しているアプリケーションおよびハードウェアの制限によって異なります。</span><span class="sxs-lookup"><span data-stu-id="fb733-105">The actual number of user connections allowed also depends on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you are using, and also the limits of your application or applications and hardware.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fb733-106">では、最大 32,767 個のユーザー接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="fb733-106">allows a maximum of 32,767 user connections.</span></span> <span data-ttu-id="fb733-107">**User Connections** はサーバー自身が構成する動的なオプションなので、ユーザー接続の最大数は必要に応じて自動的に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって最大許容範囲内で調整されます。</span><span class="sxs-lookup"><span data-stu-id="fb733-107">Because **user connections** is a dynamic (self-configuring) option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adjusts the maximum number of user connections automatically as needed, up to the maximum value allowable.</span></span> <span data-ttu-id="fb733-108">たとえば、10 人のユーザーがログインしている場合、10 個のユーザー接続オブジェクトが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="fb733-108">For example, if only 10 users are logged in, 10 user connection objects are allocated.</span></span> <span data-ttu-id="fb733-109">ほとんどの場合は、このオプションの値を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fb733-109">In most cases, you do not have to change the value for this option.</span></span> <span data-ttu-id="fb733-110">既定は 0 で、最大数 (32,767) のユーザー接続を許可することを示します。</span><span class="sxs-lookup"><span data-stu-id="fb733-110">The default is 0, which means that the maximum (32,767) user connections are allowed.</span></span>  
  
 <span data-ttu-id="fb733-111">システムで許可されるユーザー接続の最大数を決定するには、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用するか、または [sys.configuration](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) カタログ ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb733-111">To determine the maximum number of user connections that your system allows, you can execute [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) or query the [sys.configuration](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="fb733-112">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="fb733-112">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fb733-113">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="fb733-113">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fb733-114">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="fb733-114">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="fb733-115">Security</span><span class="sxs-lookup"><span data-stu-id="fb733-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fb733-116">**以下を使用して user connections オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="fb733-116">**To configure the user connections option, using:**</span></span>  
  
     [<span data-ttu-id="fb733-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fb733-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fb733-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fb733-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="fb733-119">**補足情報:** [user connections オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="fb733-119">**Follow Up:**  [After you configure the user connections option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fb733-120">はじめに</span><span class="sxs-lookup"><span data-stu-id="fb733-120">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="fb733-121">推奨事項</span><span class="sxs-lookup"><span data-stu-id="fb733-121">Recommendations</span></span>  
  
-   <span data-ttu-id="fb733-122">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="fb733-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="fb733-123">**User Connections** オプションを使用すると、コンカレント接続数が多すぎてサーバーが過負荷になるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="fb733-123">Using the **user connections** option helps avoid overloading the server with too many concurrent connections.</span></span> <span data-ttu-id="fb733-124">接続数は、システムやユーザーの必要条件に基づいて予測できます。</span><span class="sxs-lookup"><span data-stu-id="fb733-124">You can estimate the number of connections based on system and user requirements.</span></span> <span data-ttu-id="fb733-125">たとえば、ユーザー数が多いシステムの場合、通常はどのユーザーにも専用の接続が必要なわけではありません。</span><span class="sxs-lookup"><span data-stu-id="fb733-125">For example, on a system with many users, each user would not usually require a unique connection.</span></span> <span data-ttu-id="fb733-126">接続は、ユーザー間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="fb733-126">Connections can be shared among users.</span></span> <span data-ttu-id="fb733-127">OLE DB アプリケーションを実行しているユーザーの場合は、開いている接続オブジェクトごとに 1 つの接続が必要であり、ODBC (Open Database Connectivity) アプリケーションを実行しているユーザーの場合は、アプリケーション内のアクティブな接続ハンドルごとに 1 つの接続が必要です。また、DB-Library アプリケーションを実行しているユーザーの場合は、DB-Library の **dbopen** 関数を呼び出すプロセスが開始されるたびに 1 つの接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="fb733-127">Users running OLE DB applications need a connection for each open connection object, users running Open Database Connectivity (ODBC) applications need a connection for each active connection handle in the application, and users running DB-Library applications need one connection for each process started that calls the DB-Library **dbopen** function.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fb733-128">このオプションを使用する必要がある場合、値を大きくしすぎないでください。1 つ接続すると、その接続が使用中であるかどうかに関係なくオーバーヘッドが生じます。</span><span class="sxs-lookup"><span data-stu-id="fb733-128">If you must use this option, do not set the value too high, because each connection has overhead regardless of whether the connection is being used.</span></span> <span data-ttu-id="fb733-129">ユーザー接続の最大数を超えると、エラー メッセージが表示され、別の接続が使用可能になるまで接続できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fb733-129">If you exceed the maximum number of user connections, you receive an error message and are not able to connect until another connection becomes available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fb733-130">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fb733-130">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fb733-131">Permissions</span><span class="sxs-lookup"><span data-stu-id="fb733-131">Permissions</span></span>  
 <span data-ttu-id="fb733-132">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="fb733-132">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="fb733-133">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb733-133">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="fb733-134">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="fb733-134">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fb733-135">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="fb733-135">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-user-connections-option"></a><span data-ttu-id="fb733-136">user connections オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="fb733-136">To configure the user connections option</span></span>  
  
1.  <span data-ttu-id="fb733-137">オブジェクト エクスプローラーで、サーバーを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb733-137">In Object Explorer, right-click a server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="fb733-138">**[接続]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb733-138">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="fb733-139">**[接続]** の **[コンカレント接続の最大数]** ボックスで 0 から 32767 までの値を入力するか選択し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに同時に接続できるユーザーの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="fb733-139">Under **Connections**, in the **Max number of concurrent connections** box, type or select a value from 0 through 32767 to set the maximum number of users that are allowed to connect simultaneously to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="fb733-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="fb733-140">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fb733-141">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="fb733-141">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-user-connections-option"></a><span data-ttu-id="fb733-142">user connections オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="fb733-142">To configure the user connections option</span></span>  
  
1.  <span data-ttu-id="fb733-143">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="fb733-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fb733-144">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb733-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fb733-145">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb733-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="fb733-146">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `user connections` オプションの値を `325` ユーザーに設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fb733-146">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the value of the `user connections` option to `325` users.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'user connections', 325 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="fb733-147">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb733-147">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-user-connections-option"></a><a name="FollowUp"></a><span data-ttu-id="fb733-148">補足情報: user connections オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="fb733-148">Follow Up: After you configure the user connections option</span></span>  
 <span data-ttu-id="fb733-149">設定を有効にするには、サーバーを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb733-149">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb733-150">参照</span><span class="sxs-lookup"><span data-stu-id="fb733-150">See Also</span></span>  
 <span data-ttu-id="fb733-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fb733-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="fb733-152">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb733-152">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="fb733-153">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb733-153">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
