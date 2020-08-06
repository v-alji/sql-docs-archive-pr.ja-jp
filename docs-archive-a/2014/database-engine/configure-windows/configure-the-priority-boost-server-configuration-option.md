---
title: priority boost サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- priority boost option
ms.assetid: 765f1e83-dd52-44fb-b0c8-1078f213607b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f42d7d2022e07dcac3039557295dc70e4500583d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634629"
---
# <a name="configure-the-priority-boost-server-configuration-option"></a><span data-ttu-id="9ce0f-102">priority boost サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="9ce0f-102">Configure the priority boost Server Configuration Option</span></span>
  <span data-ttu-id="9ce0f-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] priority boost [!INCLUDE[tsql](../../includes/tsql-md.md)]構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-103">This topic describes how to configure the **priority boost** configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9ce0f-104">**priority boost** オプションは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 または Windows 2008 R2 のスケジューリングでの優先度を同じコンピューター上の他のプロセスよりも高くして、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行する必要があるかどうかを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-104">Use the **priority boost** option to specify whether [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should run at a higher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 or Windows 2008 R2 scheduling priority than other processes on the same computer.</span></span> <span data-ttu-id="9ce0f-105">このオプションを 1 に設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、Windows 2008 または Windows Server 2008 R2 のスケジューラで優先度ベース 13 で実行されます。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-105">If you set this option to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs at a priority base of 13 in the Windows 2008 or Windows Server 2008 R2 scheduler.</span></span> <span data-ttu-id="9ce0f-106">既定値は 0 (優先度ベース 7) です。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-106">The default is 0, which is a priority base of 7.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="9ce0f-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9ce0f-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9ce0f-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9ce0f-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9ce0f-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9ce0f-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9ce0f-110">Security</span><span class="sxs-lookup"><span data-stu-id="9ce0f-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9ce0f-111">**以下を使用して priority boost オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="9ce0f-111">**To configure the priority boost option, using:**</span></span>  
  
     [<span data-ttu-id="9ce0f-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9ce0f-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9ce0f-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9ce0f-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="9ce0f-114">**補足情報:** [priority boost オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="9ce0f-114">**Follow Up:**  [After you configure the priority boost option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9ce0f-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="9ce0f-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9ce0f-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9ce0f-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9ce0f-117">この優先度を高くしすぎると、オペレーティング システムやネットワーク機能の重要なリソースを奪うことになり、その結果、SQL Server のシャットダウン時に障害が発生する場合や、オペレーティング システムの他のタスクをサーバー上で実行できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-117">Raising the priority too high may drain resources from essential operating system and network functions, resulting in problems shutting down SQL Server or using other operating system tasks on the server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9ce0f-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9ce0f-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9ce0f-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="9ce0f-119">Permissions</span></span>  
 <span data-ttu-id="9ce0f-120">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-120">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="9ce0f-121">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-121">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="9ce0f-122">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-122">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9ce0f-123">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9ce0f-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-priority-boost-option"></a><span data-ttu-id="9ce0f-124">priority boost オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="9ce0f-124">To configure the priority boost option</span></span>  
  
1.  <span data-ttu-id="9ce0f-125">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-125">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="9ce0f-126">**[プロセッサ]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-126">Click the **Processors** node.</span></span>  
  
3.  <span data-ttu-id="9ce0f-127">**[スレッド]** の **[SQL Server の優先度を上げる]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-127">Under **Threads**, select the **Boost SQL Server priority** check box.</span></span>  
  
4.  <span data-ttu-id="9ce0f-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を停止して再起動します。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-128">Stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9ce0f-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9ce0f-129">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-priority-boost-option"></a><span data-ttu-id="9ce0f-130">priority boost オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="9ce0f-130">To configure the priority boost option</span></span>  
  
1.  <span data-ttu-id="9ce0f-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-131">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9ce0f-132">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-132">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9ce0f-133">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-133">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9ce0f-134">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `priority boost` オプションの値を `1`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-134">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `priority boost` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'priority boost', 1 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="9ce0f-135">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-135">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-priority-boost-option"></a><a name="FollowUp"></a><span data-ttu-id="9ce0f-136">補足情報: priority boost オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="9ce0f-136">Follow Up: After you configure the priority boost option</span></span>  
 <span data-ttu-id="9ce0f-137">設定を有効にするには、サーバーを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce0f-137">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce0f-138">参照</span><span class="sxs-lookup"><span data-stu-id="9ce0f-138">See Also</span></span>  
 <span data-ttu-id="9ce0f-139">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ce0f-139">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="9ce0f-140">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9ce0f-140">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="9ce0f-141">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce0f-141">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
