---
title: サーバーのポーリング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6370e53083d2cf818e8c8b09752d49e092755a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642499"
---
# <a name="poll-servers"></a><span data-ttu-id="5c00a-102">サーバーのポーリング</span><span class="sxs-lookup"><span data-stu-id="5c00a-102">Poll Servers</span></span>
  <span data-ttu-id="5c00a-103">マルチサーバー管理を実装している場合、ターゲット サーバーからマスター サーバーに定期的にアクセスし、既に実行したジョブの情報をアップロードして新しいジョブをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="5c00a-103">When multiserver administration is implemented, target servers periodically contact the master server to upload information on jobs that have been executed, and download new jobs.</span></span> <span data-ttu-id="5c00a-104">マスター サーバーにアクセスする処理は *サーバー ポーリング* と呼ばれ、定期的な *ポーリング間隔*で行われます。</span><span class="sxs-lookup"><span data-stu-id="5c00a-104">The process of contacting the master server is called *server polling,* which takes place at regular *polling intervals.*</span></span>  
  
## <a name="polling-intervals"></a><span data-ttu-id="5c00a-105">ポーリング間隔</span><span class="sxs-lookup"><span data-stu-id="5c00a-105">Polling Intervals</span></span>  
 <span data-ttu-id="5c00a-106">ターゲット サーバーからマスター サーバーに接続し、命令をダウンロードしてジョブの実行結果をアップロードする頻度をポーリング間隔 (既定値は 1 分) で制御します。</span><span class="sxs-lookup"><span data-stu-id="5c00a-106">The polling interval (one minute by default) controls how frequently the target server connects to the master server to download instructions and upload the results of job execution.</span></span>  
  
 <span data-ttu-id="5c00a-107">ターゲット サーバーからマスター サーバーにポーリングするとき、ターゲット サーバーに割り当てられる操作を **msdb** データベースの **sysdownloadlist** テーブルから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="5c00a-107">When a target server polls the master server, it reads the operations assigned to the target server from the **sysdownloadlist** table in the **msdb** database.</span></span> <span data-ttu-id="5c00a-108">読み取った操作により、マルチサーバー ジョブやターゲット サーバーのさまざまな動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="5c00a-108">These operations control multiserver jobs and various aspects of the behavior of a target server.</span></span> <span data-ttu-id="5c00a-109">操作の例には、ジョブの削除、ジョブの挿入、ジョブの開始、ターゲット サーバーのポーリング間隔の更新などがあります。</span><span class="sxs-lookup"><span data-stu-id="5c00a-109">Examples of operations include deleting a job, inserting a job, starting a job, and updating the polling interval of a target server.</span></span>  
  
 <span data-ttu-id="5c00a-110">操作は次のいずれかの方法で **sysdownloadlist** テーブルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5c00a-110">Operations are posted to the **sysdownloadlist** table in either of the following ways:</span></span>  
  
-   <span data-ttu-id="5c00a-111">**sp_post_msx_operation** ストアド プロシージャを使用して明示的に行います。</span><span class="sxs-lookup"><span data-stu-id="5c00a-111">Explicitly by using the **sp_post_msx_operation** stored procedure.</span></span>  
  
-   <span data-ttu-id="5c00a-112">他のジョブ ストアド プロシージャを使用して暗黙的に行います。</span><span class="sxs-lookup"><span data-stu-id="5c00a-112">Implicitly by using other job stored procedures.</span></span>  
  
 <span data-ttu-id="5c00a-113">ジョブ ストアド プロシージャを使用してマルチサーバー ジョブ スケジュールやジョブ ステップを変更する場合、または SQL-DMO (SQL 分散管理オブジェクト) を使用してマルチサーバー ジョブを制御する場合、マルチサーバー ジョブのステップやスケジュールを変更してから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5c00a-113">If you use job stored procedures to modify multiserver job schedules or job steps, or SQL Distributed Management Objects (SQL-DMO) to control multiserver jobs, issue the following command after modifying a multiserver job's steps or schedules:</span></span>  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="5c00a-114">このコマンドを実行すると、現在のジョブ定義がターゲット サーバーと同期されます。</span><span class="sxs-lookup"><span data-stu-id="5c00a-114">Issue this command keeps the target servers synchronized with the current job definition.</span></span>  
  
 <span data-ttu-id="5c00a-115">次の場合、操作を明示的に書き込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5c00a-115">You do not have to post operations explicitly if you use the following:</span></span>  
  
-   <span data-ttu-id="5c00a-116">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してマルチサーバー ジョブを制御する場合。</span><span class="sxs-lookup"><span data-stu-id="5c00a-116">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to control multiserver jobs.</span></span>  
  
-   <span data-ttu-id="5c00a-117">ジョブ スケジュールまたはジョブ ステップを変更しないジョブ ストアド プロシージャの場合。</span><span class="sxs-lookup"><span data-stu-id="5c00a-117">Job stored procedures that do not modify job schedules or job steps.</span></span>  
  
 <span data-ttu-id="5c00a-118">**ターゲット サーバーからマスター サーバーにポーリングさせるには**</span><span class="sxs-lookup"><span data-stu-id="5c00a-118">**To force a target server to poll the master server**</span></span>  
  
-   [<span data-ttu-id="5c00a-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5c00a-119">SQL Server Management Studio</span></span>](force-a-target-server-to-poll-the-master-server.md)  
  
-   [<span data-ttu-id="5c00a-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5c00a-120">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="5c00a-121">参照</span><span class="sxs-lookup"><span data-stu-id="5c00a-121">See Also</span></span>  
 [<span data-ttu-id="5c00a-122">イベントの管理</span><span class="sxs-lookup"><span data-stu-id="5c00a-122">Manage Events</span></span>](manage-events.md)  
  
  
