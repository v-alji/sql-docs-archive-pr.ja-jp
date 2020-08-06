---
title: SQL Server エージェントの JobSteps オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3759303807714e2bb7f71f59e644bc485d36cfcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633798"
---
# <a name="sql-server-agent-jobsteps-object"></a><span data-ttu-id="c210d-102">SQL Server エージェントの JobSteps オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c210d-102">SQL Server Agent, JobSteps Object</span></span>
  <span data-ttu-id="c210d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **JobSteps** パフォーマンス オブジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップについての情報を報告するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c210d-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **JobSteps** performance object contains performance counters that report information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="c210d-104">次の表は、このオブジェクトに含まれているカウンターを示します。</span><span class="sxs-lookup"><span data-stu-id="c210d-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="c210d-105">次の表は、 **SQLAgent:JobSteps** カウンターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="c210d-105">The table below contains the **SQLAgent:JobSteps** counters.</span></span>  
  
|<span data-ttu-id="c210d-106">名前</span><span class="sxs-lookup"><span data-stu-id="c210d-106">Name</span></span>|<span data-ttu-id="c210d-107">説明</span><span class="sxs-lookup"><span data-stu-id="c210d-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="c210d-108">**Active steps**</span><span class="sxs-lookup"><span data-stu-id="c210d-108">**Active steps**</span></span>|<span data-ttu-id="c210d-109">このカウンターは、現在実行中のジョブ ステップの数を報告します。</span><span class="sxs-lookup"><span data-stu-id="c210d-109">This counter reports the number of job steps currently running.</span></span>|  
|<span data-ttu-id="c210d-110">**Queued steps**</span><span class="sxs-lookup"><span data-stu-id="c210d-110">**Queued steps**</span></span>|<span data-ttu-id="c210d-111">このカウンターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行する準備が整っているジョブ ステップで、まだ実行が開始されていないジョブ ステップの数を報告します。</span><span class="sxs-lookup"><span data-stu-id="c210d-111">This counter reports the number of job steps that are ready for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run, but which have not yet started running.</span></span>|  
|<span data-ttu-id="c210d-112">**Total Step Retries**</span><span class="sxs-lookup"><span data-stu-id="c210d-112">**Total step retries**</span></span>|<span data-ttu-id="c210d-113">このカウンターは、サーバーを前回再起動してから [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がジョブ ステップを再試行した合計回数を報告します。</span><span class="sxs-lookup"><span data-stu-id="c210d-113">This counter reports the total number of times that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has retried a job step since the last server restart.</span></span>|  
  
 <span data-ttu-id="c210d-114">オブジェクトの各カウンターには、次のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c210d-114">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="c210d-115">インスタンス</span><span class="sxs-lookup"><span data-stu-id="c210d-115">Instance</span></span>|<span data-ttu-id="c210d-116">説明</span><span class="sxs-lookup"><span data-stu-id="c210d-116">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="c210d-117">**_Total**</span><span class="sxs-lookup"><span data-stu-id="c210d-117">**_Total**</span></span>|<span data-ttu-id="c210d-118">すべてのジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-118">Information for all job steps.</span></span>|  
|<span data-ttu-id="c210d-119">**ActiveScripting**</span><span class="sxs-lookup"><span data-stu-id="c210d-119">**ActiveScripting**</span></span>|<span data-ttu-id="c210d-120">**ActiveScripting** サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-120">Information for job steps that use the **ActiveScripting** subsystem.</span></span>|  
|<span data-ttu-id="c210d-121">**ANALYSISCOMMAND**</span><span class="sxs-lookup"><span data-stu-id="c210d-121">**ANALYSISCOMMAND**</span></span>|<span data-ttu-id="c210d-122">ANALYSISCOMMAND サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-122">Information for job steps that use the ANALYSISCOMMAND subsystem.</span></span>|  
|<span data-ttu-id="c210d-123">**ANALYSISQUERY**</span><span class="sxs-lookup"><span data-stu-id="c210d-123">**ANALYSISQUERY**</span></span>|<span data-ttu-id="c210d-124">ANALYSISQUERY サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-124">Information for job steps that use the ANALYSISQUERY subsystem.</span></span>|  
|<span data-ttu-id="c210d-125">**CmdExec**</span><span class="sxs-lookup"><span data-stu-id="c210d-125">**CmdExec**</span></span>|<span data-ttu-id="c210d-126">**CmdExec** サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-126">Information for job steps that use the **CmdExec** subsystem.</span></span>|  
|<span data-ttu-id="c210d-127">**Distribution**</span><span class="sxs-lookup"><span data-stu-id="c210d-127">**Distribution**</span></span>|<span data-ttu-id="c210d-128">**Distribution** サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-128">Information for job steps that use the **Distribution** subsystem.</span></span>|  
|<span data-ttu-id="c210d-129">**Dts**</span><span class="sxs-lookup"><span data-stu-id="c210d-129">**Dts**</span></span>|<span data-ttu-id="c210d-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-130">Information for job steps that use the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] subsystem.</span></span>|  
|<span data-ttu-id="c210d-131">**LogReader**</span><span class="sxs-lookup"><span data-stu-id="c210d-131">**LogReader**</span></span>|<span data-ttu-id="c210d-132">**LogReader** サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-132">Information for job steps that use the **LogReader** subsystem.</span></span>|  
|<span data-ttu-id="c210d-133">**[マージ]**</span><span class="sxs-lookup"><span data-stu-id="c210d-133">**Merge**</span></span>|<span data-ttu-id="c210d-134">**Merge** サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-134">Information for job steps that use the **Merge** subsystem.</span></span>|  
|<span data-ttu-id="c210d-135">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="c210d-135">**PowerShell**</span></span>|<span data-ttu-id="c210d-136">**PowerShell** サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-136">Information for job steps that use the **PowerShell** subsystem.</span></span>|  
|<span data-ttu-id="c210d-137">**QueueReader**</span><span class="sxs-lookup"><span data-stu-id="c210d-137">**QueueReader**</span></span>|<span data-ttu-id="c210d-138">**QueueReader** サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-138">Information for job steps that use the **QueueReader** subsystem.</span></span>|  
|<span data-ttu-id="c210d-139">**スナップショット**</span><span class="sxs-lookup"><span data-stu-id="c210d-139">**Snapshot**</span></span>|<span data-ttu-id="c210d-140">**Snapshot** サブシステムを使用するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-140">Information for job steps that use the **Snapshot** subsystem.</span></span>|  
|<span data-ttu-id="c210d-141">**TSQL**</span><span class="sxs-lookup"><span data-stu-id="c210d-141">**TSQL**</span></span>|<span data-ttu-id="c210d-142">[!INCLUDE[tsql](../../includes/tsql-md.md)]を実行するジョブ ステップの情報です。</span><span class="sxs-lookup"><span data-stu-id="c210d-142">Information for job steps that execute [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c210d-143">参照</span><span class="sxs-lookup"><span data-stu-id="c210d-143">See Also</span></span>  
 <span data-ttu-id="c210d-144">[ジョブ ステップの管理](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="c210d-144">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 <span data-ttu-id="c210d-145">[パフォーマンス オブジェクトの使用](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="c210d-145">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="c210d-146">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="c210d-146">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
