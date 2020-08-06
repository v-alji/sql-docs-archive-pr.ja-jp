---
title: default language サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default language option
ms.assetid: c08c26d8-5a62-487e-a4ee-4c529e4f9287
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b0e62fef112dad2c6c307946bc720adf1f14d82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741253"
---
# <a name="configure-the-default-language-server-configuration-option"></a><span data-ttu-id="ef96a-102">default language サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="ef96a-102">Configure the default language Server Configuration Option</span></span>
  <span data-ttu-id="ef96a-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] default language [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef96a-103">This topic describes how to configure the **default language** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ef96a-104">**default language** は、新しく作成したすべてのログインで使用される既定の言語を指定するオプションです。</span><span class="sxs-lookup"><span data-stu-id="ef96a-104">The **default language** option specifies the default language for all newly created logins.</span></span> <span data-ttu-id="ef96a-105">既定の言語を設定するには、目的の言語の **langid** 値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ef96a-105">To set default language, specify the **langid** value of the language you want.</span></span> <span data-ttu-id="ef96a-106">**langid** 値は、 **sys.syslanguages** 互換性ビューをクエリすることによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="ef96a-106">The **langid** value can be obtained by querying the **sys.syslanguages** compatibility view.</span></span>  
  
 <span data-ttu-id="ef96a-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ef96a-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ef96a-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ef96a-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ef96a-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="ef96a-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ef96a-110">Security</span><span class="sxs-lookup"><span data-stu-id="ef96a-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ef96a-111">**以下を使用して default language オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="ef96a-111">**To configure the default language option, using:**</span></span>  
  
     [<span data-ttu-id="ef96a-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef96a-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ef96a-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef96a-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="ef96a-114">**補足情報:** [default language オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ef96a-114">**Follow Up:**  [After you configure the default language option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ef96a-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="ef96a-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ef96a-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ef96a-116">Recommendations</span></span>  
  
-   <span data-ttu-id="ef96a-117">ログインの既定の言語は、CREATE LOGIN または ALTER LOGIN でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="ef96a-117">The default language for a login can be overridden by using CREATE LOGIN or ALTER LOGIN.</span></span> <span data-ttu-id="ef96a-118">セッションの既定の言語が、Open Database Connectivity (ODBC) API または OLE DB API でセッションごとにオーバーライドされない限り、そのセッションのログインの言語になります。</span><span class="sxs-lookup"><span data-stu-id="ef96a-118">The default language for a session is the language for that session's login, unless overridden on a per-session basis by using the Open Database Connectivity (ODBC) or OLE DB APIs.</span></span> <span data-ttu-id="ef96a-119">**default language** オプションには、 [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) で定義されている言語 ID (0 ～ 32) しか設定できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef96a-119">Note that you can only set the **default language** option to a language ID defined in [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) (0-32).</span></span> <span data-ttu-id="ef96a-120">包含データベースを使用している場合、既定の言語をデータベースに対して設定するには CREATE DATABASE または ALTER DATABASE を使用し、包含データベース ユーザーに対して設定するには CREATE USER または ALTER USER を使用します。</span><span class="sxs-lookup"><span data-stu-id="ef96a-120">When you are using contained databases, a default language can be set for a database by using CREATE DATABASE or ALTER DATABASE, and for contained database users by using CREATE USER or ALTER USER.</span></span> <span data-ttu-id="ef96a-121">包含データベースにおける既定の言語を設定する際は、 **sys.syslanguages** に格納されている **langid**値、言語の名前、または言語の別名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef96a-121">Setting default languages in a contained database accepts **langid** value, the language name, or a language alias as listed in **sys.syslanguages**.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ef96a-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ef96a-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ef96a-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="ef96a-123">Permissions</span></span>  
 <span data-ttu-id="ef96a-124">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="ef96a-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="ef96a-125">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef96a-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="ef96a-126">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="ef96a-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ef96a-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ef96a-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-default-language-option"></a><span data-ttu-id="ef96a-128">default language オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="ef96a-128">To configure the default language option</span></span>  
  
1.  <span data-ttu-id="ef96a-129">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef96a-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ef96a-130">**[その他のサーバーの設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef96a-130">Click the **Misc server settings** node.</span></span>  
  
3.  <span data-ttu-id="ef96a-131">**[ユーザーの既定の言語]** ボックスで、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がシステム メッセージの表示に使用する言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef96a-131">In the **Default language for users** box, choose the language in which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should display system messages.</span></span>  
  
     <span data-ttu-id="ef96a-132">既定の言語は English (英語) です。</span><span class="sxs-lookup"><span data-stu-id="ef96a-132">The default language is English.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ef96a-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ef96a-133">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-default-language-option"></a><span data-ttu-id="ef96a-134">default language オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="ef96a-134">To configure the default language option</span></span>  
  
1.  <span data-ttu-id="ef96a-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="ef96a-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ef96a-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef96a-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ef96a-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef96a-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ef96a-138">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `default language` オプションをフランス語 (`2`) に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ef96a-138">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `default language` option to French (`2`).</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'default language', 2 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
 <span data-ttu-id="ef96a-139">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef96a-139">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-default-language-option"></a><a name="FollowUp"></a><span data-ttu-id="ef96a-140">補足情報: default language オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="ef96a-140">Follow Up: After you configure the default language option</span></span>  
 <span data-ttu-id="ef96a-141">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="ef96a-141">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef96a-142">参照</span><span class="sxs-lookup"><span data-stu-id="ef96a-142">See Also</span></span>  
 <span data-ttu-id="ef96a-143">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef96a-143">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="ef96a-144">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef96a-144">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 <span data-ttu-id="ef96a-145">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef96a-145">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="ef96a-146">[ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef96a-146">[ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql) </span></span>  
 <span data-ttu-id="ef96a-147">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef96a-147">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="ef96a-148">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef96a-148">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="ef96a-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef96a-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="ef96a-150">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ef96a-150">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="ef96a-151">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ef96a-151">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
