---
title: ジョブの実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1925b3113db8d7c57ac4344958c0247763cfd1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631463"
---
# <a name="implement-jobs"></a><span data-ttu-id="bb821-102">ジョブの実装</span><span class="sxs-lookup"><span data-stu-id="bb821-102">Implement Jobs</span></span>
  <span data-ttu-id="bb821-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを使用すると、定型的な管理作業を自動化して定期的に実行し、管理を効率化できます。</span><span class="sxs-lookup"><span data-stu-id="bb821-103">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to automate routine administrative tasks and run them on a recurring basis, making administration more efficient.</span></span>  
  
 <span data-ttu-id="bb821-104">ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって順番に実行される一連の操作です。</span><span class="sxs-lookup"><span data-stu-id="bb821-104">A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="bb821-105">ジョブで実行できる操作は多岐にわたり、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、コマンド ライン アプリケーション、Microsoft ActiveX スクリプト、Integration Services パッケージ、Analysis Services のコマンドおよびクエリ、レプリケーション タスクなどを実行できます。</span><span class="sxs-lookup"><span data-stu-id="bb821-105">A job can perform a wide range of activities, including running [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, command-line applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks.</span></span> <span data-ttu-id="bb821-106">ジョブでは、繰り返し行う作業や、スケジュールに設定できる作業を実行できます。また、警告を生成してジョブの状態をユーザーに自動的に通知できるので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の管理を大幅に簡素化できます。</span><span class="sxs-lookup"><span data-stu-id="bb821-106">Jobs can run repetitive tasks or those that can be scheduled, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administration.</span></span>  
  
 <span data-ttu-id="bb821-107">ジョブは手動で実行することも、スケジュールや警告に応じて実行されるように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb821-107">You can run a job manually, or you can configure it to run according to a schedule or in response to alerts.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bb821-108">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bb821-108">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb821-109">**説明**</span><span class="sxs-lookup"><span data-stu-id="bb821-109">**Description**</span></span>|<span data-ttu-id="bb821-110">**トピック**</span><span class="sxs-lookup"><span data-stu-id="bb821-110">**Topic**</span></span>|  
|<span data-ttu-id="bb821-111">ジョブの作成と所有権の割り当てについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bb821-111">Contains information about creating jobs and assigning ownership.</span></span>|[<span data-ttu-id="bb821-112">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="bb821-112">Create Jobs</span></span>](create-jobs.md)|  
|<span data-ttu-id="bb821-113">ジョブをカテゴリごとに編成するための情報を記載しています。</span><span class="sxs-lookup"><span data-stu-id="bb821-113">Contains information about organizing jobs into categories.</span></span>|[<span data-ttu-id="bb821-114">ジョブの整理</span><span class="sxs-lookup"><span data-stu-id="bb821-114">Organize Jobs</span></span>](organize-jobs.md)|  
|<span data-ttu-id="bb821-115">ユーザーが作成できるさまざまな種類のジョブ ステップおよびそれらの管理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb821-115">Contains information about the different kinds of job steps you can create and how to manage them.</span></span>|[<span data-ttu-id="bb821-116">ジョブ ステップの管理</span><span class="sxs-lookup"><span data-stu-id="bb821-116">Manage Job Steps</span></span>](manage-job-steps.md)|  
|<span data-ttu-id="bb821-117">ジョブの実行開始時刻および実行頻度を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb821-117">Contains information about how to define when jobs start running and how often they should run.</span></span>|[<span data-ttu-id="bb821-118">スケジュールの作成とジョブへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="bb821-118">Create and Attach Schedules to Jobs</span></span>](create-and-attach-schedules-to-jobs.md)|  
|<span data-ttu-id="bb821-119">(スケジュールを設定せずに) ジョブを手動で実行するための情報を記載しています。</span><span class="sxs-lookup"><span data-stu-id="bb821-119">Contains information about manually running jobs (without a schedule).</span></span>|[<span data-ttu-id="bb821-120">ジョブの実行</span><span class="sxs-lookup"><span data-stu-id="bb821-120">Run Jobs</span></span>](run-jobs.md)|  
|<span data-ttu-id="bb821-121">ジョブに応答できるように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb821-121">Contains information about how you can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to respond to jobs.</span></span> <span data-ttu-id="bb821-122">たとえば、ジョブが完了したら管理者に通知するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="bb821-122">For example, you can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to notify administrators when jobs are finished.</span></span>|[<span data-ttu-id="bb821-123">ジョブ応答の指定</span><span class="sxs-lookup"><span data-stu-id="bb821-123">Specify Job Responses</span></span>](specify-job-responses.md)|  
|<span data-ttu-id="bb821-124">既存のジョブおよびその実行履歴を参照する方法と、既存のジョブを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb821-124">Contains information about how to view existing jobs, their history once executes, and how to modify them.</span></span>|[<span data-ttu-id="bb821-125">ジョブの表示または変更</span><span class="sxs-lookup"><span data-stu-id="bb821-125">View or Modify Jobs</span></span>](view-or-modify-jobs.md)|  
|<span data-ttu-id="bb821-126">ジョブを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb821-126">Contains information about how to delete jobs.</span></span>|[<span data-ttu-id="bb821-127">ジョブの削除</span><span class="sxs-lookup"><span data-stu-id="bb821-127">Delete Jobs</span></span>](delete-jobs.md)|  
  
## <a name="see-also"></a><span data-ttu-id="bb821-128">参照</span><span class="sxs-lookup"><span data-stu-id="bb821-128">See Also</span></span>  
 [<span data-ttu-id="bb821-129">SQL Server エージェントのセキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="bb821-129">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
