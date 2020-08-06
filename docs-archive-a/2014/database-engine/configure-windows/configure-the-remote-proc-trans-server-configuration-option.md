---
title: remote proc trans サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote proc trans option
- distributed transactions [SQL Server], enforcing
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54fcaafa51eef33acb1ae8d1e2f36022840b76a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634626"
---
# <a name="configure-the-remote-proc-trans-server-configuration-option"></a><span data-ttu-id="73240-102">remote proc trans サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="73240-102">Configure the remote proc trans Server Configuration Option</span></span>
  <span data-ttu-id="73240-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote proc trans [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73240-103">This topic describes how to configure the **remote proc trans** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="73240-104">**remote proc trans** オプションは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) トランザクションによってサーバー間プロシージャの動作を保護する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="73240-104">The **remote proc trans** option helps protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span>  
  
 <span data-ttu-id="73240-105">**remote proc trans** の値を 1 に設定することで、トランザクションの ACID (原子性、一貫性、分離性、および持続性) プロパティを保護する、MS DTC によってコーディネートされる分散トランザクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="73240-105">Set the value of **remote proc trans** to 1 to provide an MS DTC-coordinated distributed transaction that protects the ACID (atomic, consistent, isolated, and durable) properties of transactions.</span></span> <span data-ttu-id="73240-106">このオプションを 1 に設定した後に開始したセッションは、この構成オプションの設定を既定値として継承します。</span><span class="sxs-lookup"><span data-stu-id="73240-106">Sessions begun after setting this option to 1 inherit the configuration setting as their default.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 <span data-ttu-id="73240-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="73240-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="73240-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="73240-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="73240-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="73240-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="73240-110">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="73240-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="73240-111">Security</span><span class="sxs-lookup"><span data-stu-id="73240-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="73240-112">**以下を使用して remote proc trans オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="73240-112">**To configure the remote proc trans option, using:**</span></span>  
  
     [<span data-ttu-id="73240-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="73240-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="73240-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="73240-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="73240-115">**補足情報:** [remote proc trans オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="73240-115">**Follow Up:**  [After you configure the remote proc trans option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="73240-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="73240-116">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="73240-117">前提条件</span><span class="sxs-lookup"><span data-stu-id="73240-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="73240-118">この値を設定するには、あらかじめリモート サーバー接続が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="73240-118">Remote server connections must be allowed before this value can be set.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="73240-119">推奨事項</span><span class="sxs-lookup"><span data-stu-id="73240-119">Recommendations</span></span>  
  
-   <span data-ttu-id="73240-120">このオプションは、リモート ストアド プロシージャを使用したアプリケーションにおいて以前のバージョンの [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との互換性を保つために用意されています。</span><span class="sxs-lookup"><span data-stu-id="73240-120">This option is provided for compatibility with earlier versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for applications that use remote stored procedures.</span></span> <span data-ttu-id="73240-121">リモート ストアド プロシージャを呼び出す代わりに、 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)を使用して定義されている、リンク サーバーを参照した分散クエリを使用してください。</span><span class="sxs-lookup"><span data-stu-id="73240-121">Instead of issuing remote stored procedure calls, use distributed queries that reference linked servers, which are defined by using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="73240-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="73240-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="73240-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="73240-123">Permissions</span></span>  
 <span data-ttu-id="73240-124">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="73240-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="73240-125">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="73240-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="73240-126">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="73240-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="73240-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="73240-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a><span data-ttu-id="73240-128">remote proc trans オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="73240-128">To configure the remote proc trans option</span></span>  
  
1.  <span data-ttu-id="73240-129">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73240-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="73240-130">**[接続]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="73240-130">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="73240-131">**[リモート サーバー接続]** の **[サーバー間通信で使用する分散トランザクションを要求する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="73240-131">Under **Remote server connections**, select the **Require Distributed Transactions for server to server communication** check box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="73240-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="73240-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a><span data-ttu-id="73240-133">remote proc trans オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="73240-133">To configure the remote proc trans option</span></span>  
  
1.  <span data-ttu-id="73240-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="73240-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="73240-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73240-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="73240-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73240-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="73240-137">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `remote proc trans` オプションの値を `1`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="73240-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote proc trans` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="73240-138">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73240-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-proc-trans-option"></a><a name="FollowUp"></a><span data-ttu-id="73240-139">補足情報: remote proc trans オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="73240-139">Follow Up: After you configure the remote proc trans option</span></span>  
 <span data-ttu-id="73240-140">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="73240-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73240-141">参照</span><span class="sxs-lookup"><span data-stu-id="73240-141">See Also</span></span>  
 <span data-ttu-id="73240-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73240-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="73240-143">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="73240-143">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="73240-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73240-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
