---
title: ジョブのターゲット サーバーの変更 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 246a5bb59a681a70734cc8cabef4f724cda1b52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634794"
---
# <a name="modify-the-target-servers-for-a-job"></a><span data-ttu-id="b047d-102">Modify the Target Servers for a Job</span><span class="sxs-lookup"><span data-stu-id="b047d-102">Modify the Target Servers for a Job</span></span>
  <span data-ttu-id="b047d-103"> このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエージェント ジョブのターゲット サーバーを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b047d-103">This topic describes how to change the target servers for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b047d-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b047d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b047d-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b047d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b047d-106">Security</span><span class="sxs-lookup"><span data-stu-id="b047d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b047d-107">**ジョブのターゲット サーバーを変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="b047d-107">**To modify the target servers for a job, using:**</span></span>  
  
     [<span data-ttu-id="b047d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b047d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b047d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b047d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b047d-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="b047d-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b047d-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b047d-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b047d-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="b047d-112">Permissions</span></span>  
 <span data-ttu-id="b047d-113">既定では、sysadmin 固定サーバー ロールのメンバーは、このストアド プロシージャを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b047d-113">By default, members of the sysadmin fixed server role can execute this stored procedure.</span></span> <span data-ttu-id="b047d-114">他のユーザーには、msdb データベースにおける次のいずれかの SQL Server エージェント固定データベース ロールが許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b047d-114">Other users must be granted one of the following SQL Server Agent fixed database roles in the msdb database:</span></span>  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  <span data-ttu-id="b047d-115">SQLAgentOperatorRole</span><span class="sxs-lookup"><span data-stu-id="b047d-115">SQLAgentOperatorRole</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b047d-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b047d-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a><span data-ttu-id="b047d-117">ジョブのターゲット サーバーを変更するには</span><span class="sxs-lookup"><span data-stu-id="b047d-117">To modify the target servers for a job</span></span>  
  
1.  <span data-ttu-id="b047d-118">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="b047d-118">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b047d-119">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、ジョブを右クリックします。次に、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b047d-119">Expand **SQL Server Agent**, expand **Jobs**, right-click a job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b047d-120">**[ジョブのプロパティ]** ダイアログ ボックスで **[対象サーバー]** ページをクリックし、 **[ローカル サーバーを対象とする]** または **[複数のサーバーを対象とする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b047d-120">In the **Job Properties** dialog, select the **Targets**page, and click **Target local server**, or **Target multiple servers**.</span></span>  
  
     <span data-ttu-id="b047d-121">**[複数のサーバーを対象とする]** を選択した場合は、サーバー名の左にあるチェック ボックスをオンにして、それらのサーバーがジョブの対象になるように設定します。</span><span class="sxs-lookup"><span data-stu-id="b047d-121">If you choose **Target multiple servers**, designate the servers that will be targets for the job by checking the box to the left of the server name.</span></span> <span data-ttu-id="b047d-122">ジョブの対象としないサーバーのチェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b047d-122">Verify that the check boxes for servers that will not be targets of the job are unchecked.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b047d-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b047d-123">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a><span data-ttu-id="b047d-124">ジョブのターゲット サーバーを変更するには</span><span class="sxs-lookup"><span data-stu-id="b047d-124">To modify the target servers for a job</span></span>  
  
1.  <span data-ttu-id="b047d-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="b047d-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b047d-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b047d-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b047d-127">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b047d-127">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b047d-128">この例では、マルチサーバー ジョブの Weekly Sales Backups をサーバー SEATTLE2 に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b047d-128">This example assigns the multiserver job Weekly Sales Backups to the server SEATTLE2.</span></span>  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 <span data-ttu-id="b047d-129">詳細については、「 [sp_add_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b047d-129">For more information, see [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b047d-130">参照</span><span class="sxs-lookup"><span data-stu-id="b047d-130">See Also</span></span>  
 [<span data-ttu-id="b047d-131">エンタープライズ全体の管理の自動化</span><span class="sxs-lookup"><span data-stu-id="b047d-131">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
