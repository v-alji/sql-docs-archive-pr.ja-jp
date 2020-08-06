---
title: ジョブの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
author: stevestein
ms.author: sstein
ms.openlocfilehash: f66387a1334f91c29b8edddad293d76064430b39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737458"
---
# <a name="delete-jobs"></a><span data-ttu-id="bfb0a-102">ジョブの削除</span><span class="sxs-lookup"><span data-stu-id="bfb0a-102">Delete Jobs</span></span>
  <span data-ttu-id="bfb0a-103">ジョブとは、SQL Server エージェントによって順番に実行される一連の操作です。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-103">A job is a specified series of operations performed sequentially by SQL Server Agent.</span></span> <span data-ttu-id="bfb0a-104">既定では、ジョブは実行の終了時に削除されません。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-104">By default, jobs are not deleted when execution finishes.</span></span> <span data-ttu-id="bfb0a-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブは、ジョブの成否にかかわらず削除できます。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-105">You can delete one or more [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs regardless of success or failure of the job.</span></span> <span data-ttu-id="bfb0a-106">ジョブの成功時、失敗時、または完了時に自動的にそのジョブが削除されるように [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-106">You can also configure [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.</span></span>  
  
 <span data-ttu-id="bfb0a-107">既定では、 **sysadmin**固定サーバーロールのメンバーは、 [sp_delete_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)システムストアドプロシージャを実行して、ジョブを削除できます。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-107">By default, members of the **sysadmin** fixed server role can execute the [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql) system stored procedure to delete a job.</span></span> <span data-ttu-id="bfb0a-108">他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-108">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="bfb0a-109">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="bfb0a-109">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="bfb0a-110">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="bfb0a-110">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="bfb0a-111">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="bfb0a-111">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="bfb0a-112">これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-112">For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="bfb0a-113">**sp_delete_job** を実行して任意のジョブを削除できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-113">Members of the **sysadmin** fixed server role can execute **sp_delete_job** to delete any job.</span></span> <span data-ttu-id="bfb0a-114">**sysadmin** 固定サーバー ロールのメンバーでないユーザーは、自分が所有するジョブのみを削除できます。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-114">A user that is not a member of the **sysadmin** fixed server role can only delete jobs owned by that user.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bfb0a-115">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bfb0a-115">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bfb0a-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="bfb0a-116">**Description**</span></span>|<span data-ttu-id="bfb0a-117">**トピック**</span><span class="sxs-lookup"><span data-stu-id="bfb0a-117">**Topic**</span></span>|  
|<span data-ttu-id="bfb0a-118">1 つまたは複数の [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-118">Describes how to delete one or more [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="bfb0a-119">1 つまたは複数のジョブの削除</span><span class="sxs-lookup"><span data-stu-id="bfb0a-119">Delete One or More Jobs</span></span>](delete-one-or-more-jobs.md)|  
|<span data-ttu-id="bfb0a-120">ジョブの成功時、失敗時、または完了時に自動的にそのジョブが削除されるように [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bfb0a-120">Describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.</span></span>|[<span data-ttu-id="bfb0a-121">Automatically Delete a Job</span><span class="sxs-lookup"><span data-stu-id="bfb0a-121">Automatically Delete a Job</span></span>](automatically-delete-a-job.md)|  
  
  
