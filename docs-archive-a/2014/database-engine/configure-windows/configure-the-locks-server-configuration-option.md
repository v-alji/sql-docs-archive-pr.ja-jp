---
title: locks サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- locks option [SQL Server]
ms.assetid: b0cf0f86-7652-4574-a9fb-908e10d03973
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e45f4cc539be585966eb0beb30d4938b504c3419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741249"
---
# <a name="configure-the-locks-server-configuration-option"></a><span data-ttu-id="d59d2-102">locks サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="d59d2-102">Configure the locks Server Configuration Option</span></span>
  <span data-ttu-id="d59d2-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] locks [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d59d2-103">This topic describes how to configure the **locks** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d59d2-104">**locks** オプションは、使用できるロックの最大数を設定することによって、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] がそのために使用するメモリの量を制限します。</span><span class="sxs-lookup"><span data-stu-id="d59d2-104">The **locks** option sets the maximum number of available locks, thereby limiting the amount of memory the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses for them.</span></span> <span data-ttu-id="d59d2-105">既定値は 0 です。0 の場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はシステム要件の変更に基づいてロック構造を動的に割り当てたり、割り当てを解除したりできます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-105">The default setting is 0, which allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to allocate and deallocate lock structures dynamically, based on changing system requirements.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="d59d2-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d59d2-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d59d2-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d59d2-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d59d2-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="d59d2-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d59d2-109">Security</span><span class="sxs-lookup"><span data-stu-id="d59d2-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d59d2-110">**以下を使用して locks オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="d59d2-110">**To configure the locks option, using:**</span></span>  
  
     [<span data-ttu-id="d59d2-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d59d2-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d59d2-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d59d2-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d59d2-113">**補足情報:** [locks オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d59d2-113">**Follow Up:**  [After you configure the locks option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d59d2-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="d59d2-114">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d59d2-115">推奨事項</span><span class="sxs-lookup"><span data-stu-id="d59d2-115">Recommendations</span></span>  
  
-   <span data-ttu-id="d59d2-116">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d59d2-116">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="d59d2-117">**locks** を 0 に設定してサーバーを起動すると、ロック マネージャーは 2,500 個のロック構造の初期プール用に [!INCLUDE[ssDE](../../includes/ssde-md.md)] から十分なメモリを取得します。</span><span class="sxs-lookup"><span data-stu-id="d59d2-117">When the server is started with **locks** set to 0, the lock manager acquires sufficient memory from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for an initial pool of 2,500 lock structures.</span></span> <span data-ttu-id="d59d2-118">ロック プールがなくなると、プール用のメモリが追加取得されます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-118">As the lock pool is exhausted, additional memory is acquired for the pool.</span></span>  
  
     <span data-ttu-id="d59d2-119">通常、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のメモリ プールから取得できるメモリよりも多くのメモリがロック プールに必要であり、より多くのコンピューター メモリが使用できる ( **max server memory** のしきい値に達していない) 場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はメモリを動的に割り当ててロック要求に応じます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-119">Generally, if more memory is required for the lock pool than is available in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] memory pool, and more computer memory is available (the **max server memory** threshold has not been reached), the [!INCLUDE[ssDE](../../includes/ssde-md.md)] allocates memory dynamically to satisfy the request for locks.</span></span> <span data-ttu-id="d59d2-120">ただし、そのメモリを割り当てることによって、オペレーティング システム レベルでページングが発生する場合、たとえば、別のアプリケーションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスと同じコンピューター上で実行されていて、そのメモリを使用している場合は、ロック用に割り当てを増やすことはできません。</span><span class="sxs-lookup"><span data-stu-id="d59d2-120">However, if allocating that memory would cause paging at the operating system level (for example, if another application is running on the same computer as an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and using that memory), more lock space is not allocated.</span></span> <span data-ttu-id="d59d2-121">動的なロック プールは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]に割り当てられたメモリのうち最大 60% まで取得できます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-121">The dynamic lock pool does not acquire more than 60 percent of the memory allocated to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="d59d2-122">ロック プールが [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスによって取得されたメモリの 60% に達した場合、またはコンピューターで使用できるメモリがなくなった場合、さらにロック要求があるとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d59d2-122">After the lock pool has reached 60 percent of the memory acquired by an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or no more memory is available on the computer, further requests for locks generate an error.</span></span>  
  
     <span data-ttu-id="d59d2-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が動的にロックを割り当てるように構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d59d2-123">Allowing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use locks dynamically is the recommended configuration.</span></span> <span data-ttu-id="d59d2-124">ただし、**locks** を設定し、ロック リソースを動的に割り当てる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能をオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-124">However, you can set **locks** and override the ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to allocate lock resources dynamically.</span></span> <span data-ttu-id="d59d2-125">**locks** が 0 以外の値に設定されている場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は **locks**に指定された値よりも多くのロックを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="d59d2-125">When **locks** is set to a value other than 0, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] cannot allocate more locks than the value specified in **locks**.</span></span> <span data-ttu-id="d59d2-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に使用可能なロック数を超えたことを示すメッセージが表示された場合は、この値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="d59d2-126">Increase this value if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] displays a message that you have exceeded the number of available locks.</span></span> <span data-ttu-id="d59d2-127">各ロックはそれぞれ 96 バイトのメモリを消費するため、この値を大きくした場合、状況によってはサーバー専用のメモリも増やす必要があります。</span><span class="sxs-lookup"><span data-stu-id="d59d2-127">Because each lock consumes memory (96 bytes per lock), increasing this value can require increasing the amount of memory dedicated to the server.</span></span>  
  
-   <span data-ttu-id="d59d2-128">**locks** オプションも、ロックのエスカレートがいつ行われるかに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-128">The **locks** option also affects when lock escalation occurs.</span></span> <span data-ttu-id="d59d2-129">**locks** を 0 に設定すると、現在のロック構造で使用されるメモリが [!INCLUDE[ssDE](../../includes/ssde-md.md)] のメモリ プールの 40% に達したときに、ロックのエスカレートが行われます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-129">When **locks** is set to 0, lock escalation occurs when the memory used by the current lock structures reaches 40 percent of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] memory pool.</span></span> <span data-ttu-id="d59d2-130">**locks** が 0 に設定されていない場合は、ロック数が **locks**に指定された値の 40% に達したときに、ロックのエスカレートが行われます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-130">When **locks** is not set to 0, lock escalation occurs when the number of locks reaches 40 percent of the value specified for **locks**.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d59d2-131">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d59d2-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d59d2-132">Permissions</span><span class="sxs-lookup"><span data-stu-id="d59d2-132">Permissions</span></span>  
 <span data-ttu-id="d59d2-133">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="d59d2-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="d59d2-134">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d59d2-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="d59d2-135">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="d59d2-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d59d2-136">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d59d2-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-locks-option"></a><span data-ttu-id="d59d2-137">locks オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="d59d2-137">To configure the locks option</span></span>  
  
1.  <span data-ttu-id="d59d2-138">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d59d2-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="d59d2-139">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d59d2-139">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="d59d2-140">**[並列処理]** で、 **locks** オプションの目的の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d59d2-140">Under **Parallelism**, type the desired value for the **locks** option.</span></span>  
  
     <span data-ttu-id="d59d2-141">**locks** オプションは、使用可能なロックの最大数を設定して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってロックに使用されるメモリの量を制限するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d59d2-141">Use the **locks** option to set the maximum number of available locks, thereby limiting the amount of memory [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses for them.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d59d2-142">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d59d2-142">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-locks-option"></a><span data-ttu-id="d59d2-143">locks オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="d59d2-143">To configure the locks option</span></span>  
  
1.  <span data-ttu-id="d59d2-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="d59d2-144">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d59d2-145">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d59d2-145">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d59d2-146">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d59d2-146">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d59d2-147">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `locks` オプションの値を設定する方法を示します。使用できるロックの数をユーザー全体で `20000`に設定します。</span><span class="sxs-lookup"><span data-stu-id="d59d2-147">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `locks` option to set the number of locks available for all users to `20000`.</span></span>  
  
```sql  
Use AdventureWorks2012 ;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'locks', 20000;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="d59d2-148">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d59d2-148">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-locks-option"></a><a name="FollowUp"></a><span data-ttu-id="d59d2-149">補足情報: locks オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="d59d2-149">Follow Up: After you configure the locks option</span></span>  
 <span data-ttu-id="d59d2-150">設定を有効にするには、サーバーを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d59d2-150">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59d2-151">参照</span><span class="sxs-lookup"><span data-stu-id="d59d2-151">See Also</span></span>  
 <span data-ttu-id="d59d2-152">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d59d2-152">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="d59d2-153">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d59d2-153">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="d59d2-154">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d59d2-154">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
