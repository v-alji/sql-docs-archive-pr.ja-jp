---
title: エンタープライズ全体におけるジョブの管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 385435302b2e987c86afb17eaebf90e91bc93e56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634807"
---
# <a name="manage-jobs-across-an-enterprise"></a><span data-ttu-id="ecb33-102">エンタープライズ全体におけるジョブの管理</span><span class="sxs-lookup"><span data-stu-id="ecb33-102">Manage Jobs Across an Enterprise</span></span>
  <span data-ttu-id="ecb33-103">以外でマルチサーバージョブ定義を変更した場合は [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、対象サーバーが更新されたジョブを再度ダウンロードできるように、その変更をダウンロードリストに投稿する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecb33-103">If you make changes to multiserver job definitions outside [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must post the changes to the download list so that target servers can download the updated job again.</span></span> <span data-ttu-id="ecb33-104">ターゲット サーバーが最新のジョブ定義を確実に持つように、マルチサーバー ジョブを更新した後で INSERT 命令を次のように通知します。</span><span class="sxs-lookup"><span data-stu-id="ecb33-104">To ensure that target servers have current job definitions, post an INSERT instruction after you update the multiserver job, as follows:</span></span>  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="ecb33-105">マルチサーバー ジョブが変更されたことをターゲット サーバーに通知するには、次のいずれかのプロシージャを使用した後で前述のコマンドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecb33-105">To notify target servers that a multiserver job has been modified, you must invoke the preceding command after using any of the following procedures:</span></span>  
  
-   [<span data-ttu-id="ecb33-106">sp_add_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ecb33-106">sp_add_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="ecb33-107">sp_update_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ecb33-107">sp_update_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)  
  
-   [<span data-ttu-id="ecb33-108">sp_delete_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ecb33-108">sp_delete_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)  
  
-   [<span data-ttu-id="ecb33-109">sp_attach_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ecb33-109">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="ecb33-110">sp_detach_schedule &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="ecb33-110">sp_detach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql)  
  
    > [!NOTE]  
    >  <span data-ttu-id="ecb33-111">**sp_update_job** または **sp_delete_job** を呼び出した後で **sp_post_msx_operation**を呼び出す必要はありません。この 2 つのストアド プロシージャは、必要な変更をダウンロード一覧に自動的に通知するためです。</span><span class="sxs-lookup"><span data-stu-id="ecb33-111">It is not necessary to call **sp_post_msx_operation** after you call **sp_update_job** or **sp_delete_job**, because these stored procedures post the required changes to the download list automatically.</span></span>  
  
 <span data-ttu-id="ecb33-112">エンタープライズ全体でジョブを管理するための一般的なタスクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ecb33-112">The following are common tasks for managing jobs across an enterprise:</span></span>  
  
 <span data-ttu-id="ecb33-113">**ターゲット サーバーの状態を確認するには**</span><span class="sxs-lookup"><span data-stu-id="ecb33-113">**To check the status of a target server**</span></span>  
  
-   [<span data-ttu-id="ecb33-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ecb33-114">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)  
  
-   [<span data-ttu-id="ecb33-115">SQL Server 管理オブジェクト (SMO)</span><span class="sxs-lookup"><span data-stu-id="ecb33-115">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="ecb33-116">**ジョブのターゲット サーバーを変更するには**</span><span class="sxs-lookup"><span data-stu-id="ecb33-116">**To change the target servers for a job**</span></span>  
  
-   [<span data-ttu-id="ecb33-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ecb33-117">SQL Server Management Studio</span></span>](modify-the-target-servers-for-a-job.md)  
  
-   [<span data-ttu-id="ecb33-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ecb33-118">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
-   [<span data-ttu-id="ecb33-119">SQL Server 管理オブジェクト (SMO)</span><span class="sxs-lookup"><span data-stu-id="ecb33-119">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="ecb33-120">**ターゲット サーバーの場所を変更するには**</span><span class="sxs-lookup"><span data-stu-id="ecb33-120">**To change the location of a target server**</span></span>  
  
-   [<span data-ttu-id="ecb33-121">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ecb33-121">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="ecb33-122">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ecb33-122">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
-   [<span data-ttu-id="ecb33-123">SQL Server 管理オブジェクト (SMO)</span><span class="sxs-lookup"><span data-stu-id="ecb33-123">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="ecb33-124">**ターゲット サーバーのクロックを同期するには**</span><span class="sxs-lookup"><span data-stu-id="ecb33-124">**To synchronize target server clocks**</span></span>  
  
-   [<span data-ttu-id="ecb33-125">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ecb33-125">SQL Server Management Studio</span></span>](synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="ecb33-126">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ecb33-126">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)  
  
 <span data-ttu-id="ecb33-127">**ターゲット サーバーからマスター サーバーにポーリングさせるには**</span><span class="sxs-lookup"><span data-stu-id="ecb33-127">**To force a target server to poll the master server**</span></span>  
  
-   [<span data-ttu-id="ecb33-128">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ecb33-128">SQL Server Management Studio</span></span>](force-a-target-server-to-poll-the-master-server.md)  
  
-   [<span data-ttu-id="ecb33-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ecb33-129">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="ecb33-130">参照</span><span class="sxs-lookup"><span data-stu-id="ecb33-130">See Also</span></span>  
 [<span data-ttu-id="ecb33-131">イベントの管理</span><span class="sxs-lookup"><span data-stu-id="ecb33-131">Manage Events</span></span>](manage-events.md)  
  
  
