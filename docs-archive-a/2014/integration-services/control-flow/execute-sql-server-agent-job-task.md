---
title: SQL Server エージェント ジョブの実行タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d0c66eb7022312fa3ec3d161f63a9aee92b840f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641803"
---
# <a name="execute-sql-server-agent-job-task"></a><span data-ttu-id="3715e-102">SQL Server エージェント ジョブの実行タスク</span><span class="sxs-lookup"><span data-stu-id="3715e-102">Execute SQL Server Agent Job Task</span></span>
  <span data-ttu-id="3715e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを実行します。</span><span class="sxs-lookup"><span data-stu-id="3715e-103">The Execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job task runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3715e-104">エージェントは、SQL Server のインスタンスで定義されたジョブを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="3715e-104">Agent is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows service that runs jobs that have been defined in an instance of SQL Server.</span></span> <span data-ttu-id="3715e-105">ユーザーは、Transact-SQL ステートメントや ActiveX スクリプトの実行、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] やレプリケーションのメンテナンス タスクの実行、およびパッケージの実行を行うジョブを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3715e-105">You can create jobs that execute Transact-SQL statements and ActiveX scripts, perform [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and Replication maintenance tasks, or run packages.</span></span> <span data-ttu-id="3715e-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を監視し、警告を発するジョブを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3715e-106">You can also configure a job to monitor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and fire alerts.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3715e-107">エージェント ジョブは、通常、繰り返し実行するタスクの自動化に使用します。</span><span class="sxs-lookup"><span data-stu-id="3715e-107">Agent jobs are typically used to automate tasks that you perform repeatedly.</span></span> <span data-ttu-id="3715e-108">詳細については、 [「ジョブの実装」](../../ssms/agent/implement-jobs.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3715e-108">For more information, see [Implement Jobs](../../ssms/agent/implement-jobs.md).</span></span>  
  
 <span data-ttu-id="3715e-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行タスクを使用すると、パッケージは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントに関連する管理タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3715e-109">By using the Execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job task, a package can perform administrative tasks related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="3715e-110">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブでは、フォルダー内のパッケージの一覧を取得する **sp_enum_dtspackages** などのシステム ストアド プロシージャを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3715e-110">For example, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job can run a system stored procedure such as **sp_enum_dtspackages** to obtain a list of packages in a folder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3715e-111">ローカルまたはマルチサーバーの管理ジョブを自動的に実行できるようにするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3715e-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running before local or multiserver administrative jobs can run automatically.</span></span>  
  
 <span data-ttu-id="3715e-112">このタスクは、 **sp_start_job** システム プロシージャをカプセル化し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの名前を引数としてこのプロシージャに渡します。</span><span class="sxs-lookup"><span data-stu-id="3715e-112">This task encapsulates the **sp_start_job** system procedure and passes the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to the procedure as an argument.</span></span> <span data-ttu-id="3715e-113">詳細については、「[sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3715e-113">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a><span data-ttu-id="3715e-114">SQL Server エージェント ジョブの実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="3715e-114">Configuring the Execute SQL Server Agent Job Task</span></span>  
 <span data-ttu-id="3715e-115">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="3715e-115">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="3715e-116">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3715e-116">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="3715e-117">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3715e-117">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="3715e-118">[[SQL Server エージェント ジョブの実行タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="3715e-118">[Execute SQL Server Agent Job Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)</span></span>  
  
 <span data-ttu-id="3715e-119">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3715e-119">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="3715e-120">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="3715e-120">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
