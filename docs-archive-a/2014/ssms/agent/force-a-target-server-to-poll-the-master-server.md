---
title: ターゲット サーバーからのマスター サーバーのポーリングの強制 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: stevestein
ms.author: sstein
ms.openlocfilehash: b37bf19bfe8e8fb55c29c8d94c28a341d06df5da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631474"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a><span data-ttu-id="9248f-102">ターゲット サーバーからのマスター サーバーのポーリングの強制</span><span class="sxs-lookup"><span data-stu-id="9248f-102">Force a Target Server to Poll the Master Server</span></span>
  <span data-ttu-id="9248f-103">このトピックでは、ターゲット サーバーからマスター サーバーにポーリングさせる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9248f-103">This topic describes how to force a target server to poll the master server.</span></span> <span data-ttu-id="9248f-104">ターゲット サーバーは、マスター サーバーの登録済みサーバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9248f-104">The target server must be a registered server on the master server.</span></span>  
  
 <span data-ttu-id="9248f-105">ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行される特定の一連の処理のことです。</span><span class="sxs-lookup"><span data-stu-id="9248f-105">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> <span data-ttu-id="9248f-106">マルチサーバー ジョブとは、1 つ以上のターゲット サーバーでマスター サーバーにより実行されるジョブです。</span><span class="sxs-lookup"><span data-stu-id="9248f-106">A multiserver job is a job that a master server runs on one or more target servers.</span></span> <span data-ttu-id="9248f-107">各ターゲット サーバーは、同じジョブのインスタンスを同時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="9248f-107">Each target server can run one instance of the same job at the same time.</span></span> <span data-ttu-id="9248f-108">各ターゲット サーバーからマスター サーバーに定期的にポーリングし、そのターゲット サーバーに割り当てられた新しいジョブのコピーをダウンロードした後、切断します。</span><span class="sxs-lookup"><span data-stu-id="9248f-108">Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects.</span></span> <span data-ttu-id="9248f-109">ダウンロードされたジョブはターゲット サーバーでローカルに実行され、マスター サーバーに再接続してジョブ結果状態をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="9248f-109">The target server runs the job locally and then reconnects to the master server to upload the job outcome status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9248f-110">ターゲット サーバーがジョブの状態をアップロードするときにマスター サーバーにアクセスできない場合、そのジョブの状態はマスター サーバーがアクセスできるようになるまでスプールされます。</span><span class="sxs-lookup"><span data-stu-id="9248f-110">If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.</span></span>  
  
-   <span data-ttu-id="9248f-111">**作業を開始する準備:** [制限事項と制約事項](#Restrictions)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="9248f-111">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="9248f-112">**ターゲット サーバーからマスター サーバーにポーリングさせるために使用するもの:**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="9248f-112">**To force a target server to poll the master server, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9248f-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="9248f-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9248f-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9248f-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9248f-115">ターゲット サーバーは、マスター サーバーの登録済みサーバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9248f-115">The target server must be a registered server on the master server.</span></span> <span data-ttu-id="9248f-116">このトピックに説明されている手順は、マスター サーバーから実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9248f-116">You must run the instructions given in this topic from the master server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9248f-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9248f-117">Security</span></span>  
 <span data-ttu-id="9248f-118">詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 」および「 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9248f-118">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="9248f-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9248f-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9248f-120">**ターゲット サーバーからマスター サーバーにポーリングさせるには**</span><span class="sxs-lookup"><span data-stu-id="9248f-120">**To force a target server to poll the master server**</span></span>  
  
1.  <span data-ttu-id="9248f-121">**オブジェクト エクスプローラー**で、マスター サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9248f-121">In **Object Explorer**, expand the master server.</span></span>  
  
2.  <span data-ttu-id="9248f-122">**[SQL Server エージェント]** を右クリックし、**[マルチ サーバーの管理]** をポイントして、**[ターゲット サーバーの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9248f-122">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="9248f-123">ターゲット サーバーをクリックし、**[強制的にポーリング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9248f-123">Click a target server, and then click **Force Poll**.</span></span>  
  
  
