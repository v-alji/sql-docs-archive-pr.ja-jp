---
title: ターゲット サーバーのポーリング間隔の設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36517f60a99a1a844f6d14d489587eef1de9cb13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742733"
---
# <a name="set-the-polling-interval-for-target-servers"></a><span data-ttu-id="5b6da-102">ターゲット サーバーのポーリング間隔の設定</span><span class="sxs-lookup"><span data-stu-id="5b6da-102">Set the Polling Interval for Target Servers</span></span>
  <span data-ttu-id="5b6da-103">このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがマスターから対象サーバーに情報を更新する頻度を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b6da-103">This topic describes how to set the frequency that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent refreshes information from the master to the target servers.</span></span> <span data-ttu-id="5b6da-104">ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行される特定の一連の処理のことです。</span><span class="sxs-lookup"><span data-stu-id="5b6da-104">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> <span data-ttu-id="5b6da-105">マルチサーバー ジョブとは、1 つ以上のターゲット サーバーでマスター サーバーにより実行されるジョブです。</span><span class="sxs-lookup"><span data-stu-id="5b6da-105">A multiserver job is a job that a master server runs on one or more target servers.</span></span>  
  
-   <span data-ttu-id="5b6da-106">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="5b6da-106">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="5b6da-107">**ターゲット サーバーのポーリング間隔を設定するために使用するもの:**  [SQL Server Management Studio](#SSMS)、[Transact-SQL](#TSQL)</span><span class="sxs-lookup"><span data-stu-id="5b6da-107">**To set the polling interval for target servers, using:**  [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5b6da-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="5b6da-108">Before You Begin</span></span>  
 <span data-ttu-id="5b6da-109">各ターゲット サーバーは、同じジョブのインスタンスを同時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="5b6da-109">Each target server can run one instance of the same job at the same time.</span></span> <span data-ttu-id="5b6da-110">各ターゲット サーバーからマスター サーバーに定期的にポーリングし、そのターゲット サーバーに割り当てられた新しいジョブのコピーをダウンロードした後、切断します。</span><span class="sxs-lookup"><span data-stu-id="5b6da-110">Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects.</span></span> <span data-ttu-id="5b6da-111">ダウンロードされたジョブはターゲット サーバーでローカルに実行され、マスター サーバーに再接続してジョブ結果状態をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="5b6da-111">The target server runs the job locally and then reconnects to the master server to upload the job outcome status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b6da-112">ターゲット サーバーがジョブの状態をアップロードするときにマスター サーバーにアクセスできない場合、そのジョブの状態はマスター サーバーがアクセスできるようになるまでスプールされます。</span><span class="sxs-lookup"><span data-stu-id="5b6da-112">If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5b6da-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5b6da-113">Security</span></span>  
 <span data-ttu-id="5b6da-114">詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 」および「 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b6da-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="5b6da-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="5b6da-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="5b6da-116">**ターゲット サーバーのポーリング間隔を設定するには**</span><span class="sxs-lookup"><span data-stu-id="5b6da-116">**To set the polling interval for target servers**</span></span>  
  
1.  <span data-ttu-id="5b6da-117">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="5b6da-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5b6da-118">**[SQL Server エージェント]** を右クリックし、**[マルチ サーバーの管理]** をポイントして、**[ターゲット サーバーの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b6da-118">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="5b6da-119">**[ターゲット サーバーの状態]** タブで、**[命令を通知]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b6da-119">On the **Target Server Status** tab, click **Post Instructions**.</span></span>  
  
4.  <span data-ttu-id="5b6da-120">**[命令の種類]** ボックスの一覧で、 **[ポーリング間隔の設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5b6da-120">In the **Instruction type** list, select **Set polling interval**.</span></span>  
  
5.  <span data-ttu-id="5b6da-121">**[ポーリング間隔]** ボックスに、ターゲット サーバーがマスター サーバーをポーリングするまでの経過時間 (秒単位) を、10 から 28,800 までの範囲で入力します。</span><span class="sxs-lookup"><span data-stu-id="5b6da-121">In the **Polling interval** box, enter the number of seconds from 10 through 28,800 that must pass before the target server polls the master server.</span></span>  
  
6.  <span data-ttu-id="5b6da-122">**[受信者]** で、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="5b6da-122">Under **Recipients**, do one of the following:</span></span>  
  
    1.  <span data-ttu-id="5b6da-123">すべてのターゲット サーバーで同じポーリング間隔を共有する場合は、 **[すべてのターゲット サーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b6da-123">Click **All target servers** if all target servers share the same polling interval.</span></span>  
  
    2.  <span data-ttu-id="5b6da-124">すべてのターゲット サーバーで同じポーリング間隔を共有しない場合は、**[特定のターゲット サーバー]** をクリックし、このポーリング間隔を使用するターゲット サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="5b6da-124">Click **These target servers** if not all target servers share the same polling interval, and then select each target server that will use this polling interval.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="5b6da-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="5b6da-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="5b6da-126">**ターゲット サーバーのポーリング間隔を設定するには**</span><span class="sxs-lookup"><span data-stu-id="5b6da-126">**To set the polling interval for target servers**</span></span>  
  
1.  <span data-ttu-id="5b6da-127">オブジェクト エクスプローラーで、データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="5b6da-127">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5b6da-128">ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b6da-128">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5b6da-129">クエリウィンドウで、 [sp_post_msx_operation &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)システムストアドプロシージャを使用して、対象サーバーのポーリング間隔を設定します。</span><span class="sxs-lookup"><span data-stu-id="5b6da-129">In the query window, use the [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) system stored procedure to set the polling interval for target servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6da-130">参照</span><span class="sxs-lookup"><span data-stu-id="5b6da-130">See Also</span></span>  
 [<span data-ttu-id="5b6da-131">dbo.sysdownloadlist &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="5b6da-131">dbo.sysdownloadlist &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysdownloadlist-transact-sql)  
  
  
