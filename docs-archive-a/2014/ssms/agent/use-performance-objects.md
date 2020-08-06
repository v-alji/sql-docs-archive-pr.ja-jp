---
title: パフォーマンス オブジェクトの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7c1fe3f4a7d9a5fec901f84d8e913e49a4dbd1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642493"
---
# <a name="use-performance-objects"></a><span data-ttu-id="1bc24-102">パフォーマンス オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="1bc24-102">Use Performance Objects</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1bc24-103">エージェントには、サービスの動作を監視するためのパフォーマンス オブジェクトとパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1bc24-103">Agent includes performance objects and counters to monitor how the service is performing.</span></span> <span data-ttu-id="1bc24-104">パフォーマンス オブジェクトを使用すると、パフォーマンス モニターや Windows ツールを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスのバックグラウンド動作を特定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1bc24-104">These performance objects allow you to use Performance Monitor, a Windows tool, to identify what the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is doing in the background.</span></span> <span data-ttu-id="1bc24-105">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスで現在実行されているアクティブなジョブの数を特定して、ブロックされたジョブを特定できます。</span><span class="sxs-lookup"><span data-stu-id="1bc24-105">For example, you can identify how many active jobs the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is currently running to identify those jobs that are blocked.</span></span>  
  
 <span data-ttu-id="1bc24-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスのパフォーマンス オブジェクトとパフォーマンス カウンターは、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスごとに存在します。</span><span class="sxs-lookup"><span data-stu-id="1bc24-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service performance objects and counters exist for each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is installed on a computer.</span></span> <span data-ttu-id="1bc24-107">パフォーマンス オブジェクトの名前は、各オブジェクトが表す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに従って付けられます。</span><span class="sxs-lookup"><span data-stu-id="1bc24-107">Performance objects are named according to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that each object represents.</span></span>  
  
 <span data-ttu-id="1bc24-108">次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスのパフォーマンス オブジェクトの命名形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="1bc24-108">The following table shows how the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service performance objects are named:</span></span>  
  
|<span data-ttu-id="1bc24-109">インスタンスの種類</span><span class="sxs-lookup"><span data-stu-id="1bc24-109">Instance type</span></span>|<span data-ttu-id="1bc24-110">オブジェクト名</span><span class="sxs-lookup"><span data-stu-id="1bc24-110">Object name</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="1bc24-111">Default</span><span class="sxs-lookup"><span data-stu-id="1bc24-111">Default</span></span>|<span data-ttu-id="1bc24-112">**SQLAgent:** *オブジェクト*:*カウンター*</span><span class="sxs-lookup"><span data-stu-id="1bc24-112">**SQLAgent:** *object*:*counter*</span></span>|  
|<span data-ttu-id="1bc24-113">named</span><span class="sxs-lookup"><span data-stu-id="1bc24-113">Named</span></span>|<span data-ttu-id="1bc24-114">**SQLAgent$**</span><span class="sxs-lookup"><span data-stu-id="1bc24-114">**SQLAgent$**</span></span><br /> <span data-ttu-id="1bc24-115">***instance_name* :** *オブジェクト*:*counter*</span><span class="sxs-lookup"><span data-stu-id="1bc24-115">***instance_name* :** *object*:*counter*</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1bc24-116">には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの次のパフォーマンス オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1bc24-116">includes the following performance objects for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
|<span data-ttu-id="1bc24-117">オブジェクト名</span><span class="sxs-lookup"><span data-stu-id="1bc24-117">Object name</span></span>|<span data-ttu-id="1bc24-118">説明</span><span class="sxs-lookup"><span data-stu-id="1bc24-118">Description</span></span>|  
|-----------------|-----------------|  
|[<span data-ttu-id="1bc24-119">SQLAgent:Jobs</span><span class="sxs-lookup"><span data-stu-id="1bc24-119">SQLAgent:Jobs</span></span>](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|<span data-ttu-id="1bc24-120">開始されたジョブ、成功率、および現在の状態に関するパフォーマンス情報</span><span class="sxs-lookup"><span data-stu-id="1bc24-120">Performance information about jobs that have been started, success rates, and current status</span></span>|  
|[<span data-ttu-id="1bc24-121">SQLAgent:JobSteps</span><span class="sxs-lookup"><span data-stu-id="1bc24-121">SQLAgent:JobSteps</span></span>](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|<span data-ttu-id="1bc24-122">ジョブ ステップに関する状態情報</span><span class="sxs-lookup"><span data-stu-id="1bc24-122">Status information about job steps</span></span>|  
|[<span data-ttu-id="1bc24-123">SQLAgent:Alerts</span><span class="sxs-lookup"><span data-stu-id="1bc24-123">SQLAgent:Alerts</span></span>](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|<span data-ttu-id="1bc24-124">警告と通知の数に関する情報</span><span class="sxs-lookup"><span data-stu-id="1bc24-124">Information about number of alerts and notifications</span></span>|  
|[<span data-ttu-id="1bc24-125">SQLAgent:Statistics</span><span class="sxs-lookup"><span data-stu-id="1bc24-125">SQLAgent:Statistics</span></span>](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|<span data-ttu-id="1bc24-126">パフォーマンスに関する一般的な情報</span><span class="sxs-lookup"><span data-stu-id="1bc24-126">General performance information</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bc24-127">参照</span><span class="sxs-lookup"><span data-stu-id="1bc24-127">See Also</span></span>  
 <span data-ttu-id="1bc24-128">[パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md) </span><span class="sxs-lookup"><span data-stu-id="1bc24-128">[Monitor and Tune for Performance](../../relational-databases/performance/monitor-and-tune-for-performance.md) </span></span>  
 [<span data-ttu-id="1bc24-129">システム モニターの起動 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="1bc24-129">Start System Monitor &#40;Windows&#41;</span></span>](../../relational-databases/performance/start-system-monitor-windows.md)  
  
  
