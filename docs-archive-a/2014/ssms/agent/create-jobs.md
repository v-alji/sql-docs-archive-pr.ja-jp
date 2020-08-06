---
title: ジョブの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 706b9348eed5b190f99543a74e7019dc1bde5978
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715049"
---
# <a name="create-jobs"></a><span data-ttu-id="4ca01-102">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="4ca01-102">Create Jobs</span></span>
  <span data-ttu-id="4ca01-103">ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって順番に実行される一連の操作です。</span><span class="sxs-lookup"><span data-stu-id="4ca01-103">A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="4ca01-104">ジョブは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、コマンド プロンプト アプリケーション、Microsoft ActiveX スクリプト、Integration Services パッケージ、Analysis Services コマンドおよびクエリ、レプリケーション タスクの実行など、広範な操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4ca01-104">A job can perform a wide range of activities, including running [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, command prompt applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks.</span></span> <span data-ttu-id="4ca01-105">ジョブは、反復的なタスクやスケジュール可能なタスクを実行でき、警告を発生させてジョブのステータスをユーザーに自動的に通知できるので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の管理が非常に簡単になります。</span><span class="sxs-lookup"><span data-stu-id="4ca01-105">Jobs can run repetitive or schedulable tasks, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administration.</span></span>  
  
 <span data-ttu-id="4ca01-106">ジョブを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールか **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ca01-106">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="4ca01-107">ジョブの編集は、ジョブの所有者または **sysadmin** ロールのメンバーのみが行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4ca01-107">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="4ca01-108">**sysadmin** ロールのメンバーは、別のユーザーにジョブの所有権を割り当てることができ、そのユーザーはジョブの所有者とは無関係にジョブを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4ca01-108">Members of the **sysadmin** role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span> <span data-ttu-id="4ca01-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールの詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ca01-109">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="4ca01-110">ジョブは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスまたは企業全体の複数のインスタンスで実行するように記述できます。</span><span class="sxs-lookup"><span data-stu-id="4ca01-110">Jobs can be written to run on the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or on multiple instances across an enterprise.</span></span> <span data-ttu-id="4ca01-111">複数のサーバーでジョブを実行するには、最低 1 つのマスター サーバーと 1 つ以上のターゲット サーバーをセットアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ca01-111">To run jobs on multiple servers, you must set up at least one master server and one or more target servers.</span></span> <span data-ttu-id="4ca01-112">マスター サーバーとターゲット サーバーの詳細については、「[エンタープライズ全体の管理の自動化](automated-administration-across-an-enterprise.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ca01-112">For more information about master and target servers, see [Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md)</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4ca01-113">エージェントにより、ジョブとジョブ ステップの情報がジョブ履歴に記録されます。</span><span class="sxs-lookup"><span data-stu-id="4ca01-113">Agent records job and job step information in the job history.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4ca01-114">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="4ca01-114">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ca01-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="4ca01-115">**Description**</span></span>|<span data-ttu-id="4ca01-116">**トピック**</span><span class="sxs-lookup"><span data-stu-id="4ca01-116">**Topic**</span></span>|  
|<span data-ttu-id="4ca01-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ca01-117">Describes how to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="4ca01-118">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="4ca01-118">Create a Job</span></span>](create-a-job.md)|  
|<span data-ttu-id="4ca01-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブの所有権を他のユーザーに再割り当てする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ca01-119">Describes how to reassign ownership of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to another user.</span></span>|[<span data-ttu-id="4ca01-120">Give Others Ownership of a Job</span><span class="sxs-lookup"><span data-stu-id="4ca01-120">Give Others Ownership of a Job</span></span>](give-others-ownership-of-a-job.md)|  
|<span data-ttu-id="4ca01-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ履歴ログをセットアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ca01-121">Describes how to set up the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="4ca01-122">Set Up the Job History Log</span><span class="sxs-lookup"><span data-stu-id="4ca01-122">Set Up the Job History Log</span></span>](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="4ca01-123">参照</span><span class="sxs-lookup"><span data-stu-id="4ca01-123">See Also</span></span>  
 <span data-ttu-id="4ca01-124">[ジョブ ステップの管理](manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="4ca01-124">[Manage Job Steps](manage-job-steps.md) </span></span>  
 <span data-ttu-id="4ca01-125">[エンタープライズ全体の管理の自動化](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="4ca01-125">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 <span data-ttu-id="4ca01-126">[スケジュールを作成してジョブにアタッチする](create-and-attach-schedules-to-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="4ca01-126">[Create and Attach Schedules to Jobs](create-and-attach-schedules-to-jobs.md) </span></span>  
 <span data-ttu-id="4ca01-127">[ジョブの実行](run-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="4ca01-127">[Run Jobs](run-jobs.md) </span></span>  
 [<span data-ttu-id="4ca01-128">ジョブの表示または変更</span><span class="sxs-lookup"><span data-stu-id="4ca01-128">View or Modify Jobs</span></span>](view-or-modify-jobs.md)  
  
  
