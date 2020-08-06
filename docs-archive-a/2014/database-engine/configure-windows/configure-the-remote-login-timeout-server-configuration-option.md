---
title: remote login timeout サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote login timeout option
ms.assetid: 077adebe-0e3f-42a5-a75e-5e6d04847e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58b3405f9b0e51bd43edcaa31e84c8ebbcc48547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632688"
---
# <a name="configure-the-remote-login-timeout-server-configuration-option"></a><span data-ttu-id="6fb50-102">remote login timeout サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="6fb50-102">Configure the remote login timeout Server Configuration Option</span></span>
  <span data-ttu-id="6fb50-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote login timeout [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6fb50-103">This topic describes how to configure the **remote login timeout** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6fb50-104">**remote login timeout** オプションでは、リモート ログインを要求した後の最大待機時間を秒数で指定します。リモート ログインを要求した後の最大待機時間を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="6fb50-104">The **remote login timeout** option specifies the number of seconds to wait before returning from a failed attempt to log in to a remote server.</span></span> <span data-ttu-id="6fb50-105">たとえば、リモート サーバーにログインを試みたときに、そのサーバーがダウンしている場合、 **remote login timeout** を設定してあれば、コンピューターによってログイン試行が中止されるまで無制限に待つ必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="6fb50-105">For example, if you are trying to log in to a remote server and that server is down, **remote login timeout** helps make sure that you do not have to wait indefinitely before your computer stops trying to log in.</span></span> <span data-ttu-id="6fb50-106">このオプションの既定値は 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="6fb50-106">The default value for this option is 10 seconds.</span></span> <span data-ttu-id="6fb50-107">0 に設定すると、待ち時間は無制限になります。</span><span class="sxs-lookup"><span data-stu-id="6fb50-107">A value of 0 allows for an infinite wait.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6fb50-108">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]では、このオプションの既定値は 20 秒です。</span><span class="sxs-lookup"><span data-stu-id="6fb50-108">The default value for this option is 20 seconds in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="6fb50-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6fb50-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6fb50-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="6fb50-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6fb50-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6fb50-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6fb50-112">Security</span><span class="sxs-lookup"><span data-stu-id="6fb50-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6fb50-113">**以下を使用して remote login timeout オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="6fb50-113">**To configure the remote login timeout option, using:**</span></span>  
  
     [<span data-ttu-id="6fb50-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6fb50-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6fb50-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6fb50-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="6fb50-116">**補足情報:** [remote login timeout オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="6fb50-116">**Follow Up:**  [After you configure the remote login timeout option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6fb50-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="6fb50-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6fb50-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6fb50-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6fb50-119">**remote login timeout** オプションは、異種クエリ用に確立された OLE DB プロバイダーへの接続に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6fb50-119">The **remote login timeout** option affects connections to OLE DB providers made for heterogeneous queries.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6fb50-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6fb50-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6fb50-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="6fb50-121">Permissions</span></span>  
 <span data-ttu-id="6fb50-122">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="6fb50-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="6fb50-123">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fb50-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="6fb50-124">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="6fb50-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6fb50-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6fb50-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a><span data-ttu-id="6fb50-126">remote login timeout オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="6fb50-126">To configure the remote login timeout option</span></span>  
  
1.  <span data-ttu-id="6fb50-127">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fb50-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="6fb50-128">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fb50-128">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="6fb50-129">**[ネットワーク]** の **[リモート ログイン タイムアウト]** ボックスで値を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fb50-129">Under **Network**, select a value for the **Remote Login Timeout** box.</span></span>  
  
     <span data-ttu-id="6fb50-130">**remote login timeout** オプションを使用して、リモート ログインを要求した後の最大待機時間を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="6fb50-130">Use the **remote login timeout** option to specify the number of seconds to wait before returning from a failed remote login attempt.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6fb50-131">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6fb50-131">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a><span data-ttu-id="6fb50-132">remote login timeout オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="6fb50-132">To configure the remote login timeout option</span></span>  
  
1.  <span data-ttu-id="6fb50-133">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="6fb50-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6fb50-134">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fb50-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6fb50-135">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fb50-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6fb50-136">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `remote login timeout` オプションの値を `35` 秒に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6fb50-136">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote login timeout` option to `35` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote login timeout', 35 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="6fb50-137">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fb50-137">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-login-timeout-option"></a><a name="FollowUp"></a><span data-ttu-id="6fb50-138">補足情報: remote login timeout オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="6fb50-138">Follow Up: After you configure the remote login timeout option</span></span>  
 <span data-ttu-id="6fb50-139">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="6fb50-139">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb50-140">参照</span><span class="sxs-lookup"><span data-stu-id="6fb50-140">See Also</span></span>  
 <span data-ttu-id="6fb50-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6fb50-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="6fb50-142">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6fb50-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="6fb50-143">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6fb50-143">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
