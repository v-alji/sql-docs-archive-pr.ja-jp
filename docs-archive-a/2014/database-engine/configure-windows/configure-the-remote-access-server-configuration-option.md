---
title: remote access サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], stored procedure execution
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eef18ec48ede59544b13545e49dc105909cfac16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632691"
---
# <a name="configure-the-remote-access-server-configuration-option"></a><span data-ttu-id="a2061-102">remote access サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="a2061-102">Configure the remote access Server Configuration Option</span></span>
  <span data-ttu-id="a2061-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote access [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2061-103">This topic describes how to configure the **remote access** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a2061-104">**remote access** オプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが実行されているローカル サーバーまたはリモート サーバーからストアド プロシージャの実行を制御します。</span><span class="sxs-lookup"><span data-stu-id="a2061-104">The **remote access** option controls the execution of stored procedures from local or remote servers on which instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are running.</span></span> <span data-ttu-id="a2061-105">このオプションの既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="a2061-105">This default value for this option is 1.</span></span> <span data-ttu-id="a2061-106">この場合、リモート サーバーからローカル ストアド プロシージャを実行する権限、またはローカル サーバーからリモート ストアド プロシージャを実行する権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="a2061-106">This grants permission to run local stored procedures from remote servers or remote stored procedures from the local server.</span></span> <span data-ttu-id="a2061-107">リモート サーバーからローカル ストアド プロシージャを、ローカル サーバーからリモート ストアド プロシージャを実行できないようにするには、このオプションを 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="a2061-107">To prevent local stored procedures from being run from a remote server or remote stored procedures from being run on the local server, set the option to 0.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] <span data-ttu-id="a2061-108">代わりに [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a2061-108">Use [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="a2061-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a2061-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a2061-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a2061-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a2061-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2061-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a2061-112">Security</span><span class="sxs-lookup"><span data-stu-id="a2061-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a2061-113">**以下を使用して remote access オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="a2061-113">**To configure the remote access option, using:**</span></span>  
  
     [<span data-ttu-id="a2061-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2061-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a2061-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2061-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a2061-116">**補足情報:** [remote access オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a2061-116">**Follow Up:**  [After you configure the remote access option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a2061-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="a2061-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a2061-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2061-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a2061-119">**remote access** オプションは [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)を使用して追加されたサーバーにのみ適用でき、旧バージョンとの互換性のために用意されています。</span><span class="sxs-lookup"><span data-stu-id="a2061-119">The **remote access** option only applies to servers that are added by using [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), and is included for backward compatibility.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a2061-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a2061-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a2061-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="a2061-121">Permissions</span></span>  
 <span data-ttu-id="a2061-122">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="a2061-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="a2061-123">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2061-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="a2061-124">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="a2061-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a2061-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a2061-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-access-option"></a><span data-ttu-id="a2061-126">remote access オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="a2061-126">To configure the remote access option</span></span>  
  
1.  <span data-ttu-id="a2061-127">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2061-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a2061-128">**[接続]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2061-128">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="a2061-129">**[リモート サーバー接続]** で、 **[このサーバーへのリモート接続を許可する]** チェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="a2061-129">Under **Remote server connections**, select or clear the **Allow remote connections to this server** check box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a2061-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a2061-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-access-option"></a><span data-ttu-id="a2061-131">remote access オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="a2061-131">To configure the remote access option</span></span>  
  
1.  <span data-ttu-id="a2061-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="a2061-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a2061-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2061-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a2061-134">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2061-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a2061-135">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `remote access` オプションの値を `0`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2061-135">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote access` option to `0`.</span></span>  
  
```sql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="a2061-136">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2061-136">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-access-option"></a><a name="FollowUp"></a><span data-ttu-id="a2061-137">補足情報: remote access オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="a2061-137">Follow Up: After you configure the remote access option</span></span>  
 <span data-ttu-id="a2061-138">この設定は、SQL Server の再起動後に反映されます。</span><span class="sxs-lookup"><span data-stu-id="a2061-138">This setting does not take effect until you restart SQL Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2061-139">参照</span><span class="sxs-lookup"><span data-stu-id="a2061-139">See Also</span></span>  
 <span data-ttu-id="a2061-140">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a2061-140">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="a2061-141">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a2061-141">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="a2061-142">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a2061-142">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
