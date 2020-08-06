---
title: ターゲット サーバーのクロックの同期 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e7150cd42699503ab22cdd89fb6206194bd64e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711565"
---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a><span data-ttu-id="e0137-102">ターゲット サーバーのクロックの同期 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e0137-102">Synchronize Target Server Clocks (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e0137-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のターゲット サーバーのクロックとマスター サーバーのクロックを同期する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0137-103">This topic describes how to synchronize target server clocks in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] with the master server clock by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e0137-104">これらのシステム クロックの同期をとると、ジョブのスケジュールを効果的に管理できます。</span><span class="sxs-lookup"><span data-stu-id="e0137-104">Synchronizing these system clocks supports your job schedules.</span></span>  
  
 <span data-ttu-id="e0137-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e0137-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e0137-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e0137-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e0137-107">Security</span><span class="sxs-lookup"><span data-stu-id="e0137-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e0137-108">**ターゲット サーバーのクロックを同期する方法:**</span><span class="sxs-lookup"><span data-stu-id="e0137-108">**To synchronize target server clocks, using:**</span></span>  
  
     [<span data-ttu-id="e0137-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e0137-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e0137-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e0137-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e0137-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="e0137-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e0137-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e0137-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e0137-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="e0137-113">Permissions</span></span>  
 <span data-ttu-id="e0137-114">**sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="e0137-114">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e0137-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e0137-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-synchronize-target-server-clocks"></a><span data-ttu-id="e0137-116">ターゲット サーバーのクロックを同期するには</span><span class="sxs-lookup"><span data-stu-id="e0137-116">To synchronize target server clocks</span></span>  
  
1.  <span data-ttu-id="e0137-117">**オブジェクト エクスプローラー**で、ターゲット サーバーのクロックとマスター サーバーのクロックを同期するサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="e0137-117">In **Object Explorer,** click the plus sign to expand the server where you want to synchronize the target server clocks with the master server clock.</span></span>  
  
2.  <span data-ttu-id="e0137-118">**[SQL Server エージェント]** を右クリックし、**[マルチ サーバーの管理]** をポイントして、**[ターゲット サーバーの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e0137-118">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and select **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="e0137-119">**[ターゲット サーバーの管理]** ダイアログ ボックスで **[命令を通知]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0137-119">In the **Manage Target Servers** dialog box, click **Post Instructions**.</span></span>  
  
4.  <span data-ttu-id="e0137-120">**[命令の種類]** ボックスの一覧で、 **[クロックの同期]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e0137-120">In the **Instruction type** list, select **Synchronize clocks**.</span></span>  
  
5.  <span data-ttu-id="e0137-121">**[受信者]** で、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e0137-121">Under **Recipients**, do one of the following:</span></span>  
  
    -   <span data-ttu-id="e0137-122">すべてのターゲット サーバーのクロックとマスター サーバーのクロックを同期するには、**[すべてのターゲット サーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0137-122">Click **All target servers** to synchronize all target server clocks with the master server clock.</span></span>  
  
    -   <span data-ttu-id="e0137-123">特定のサーバーのクロックを同期するには、**[特定のターゲット サーバー]** をクリックし、マスター サーバーのクロックと同期するターゲット サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e0137-123">Click **These target servers** to synchronize certain server clocks, and then select each target server whose clock you want to synchronize with the master server clock.</span></span>  
  
6.  <span data-ttu-id="e0137-124">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0137-124">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e0137-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e0137-125">Using Transact-SQL</span></span>  
  
#### <a name="to-synchronize-target-server-clocks"></a><span data-ttu-id="e0137-126">ターゲット サーバーのクロックを同期するには</span><span class="sxs-lookup"><span data-stu-id="e0137-126">To synchronize target server clocks</span></span>  
  
1.  <span data-ttu-id="e0137-127">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e0137-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e0137-128">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0137-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e0137-129">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0137-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
 <span data-ttu-id="e0137-130">詳細については、「 [sp_resync_targetserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0137-130">For more information, see [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql).</span></span>  
  
  
