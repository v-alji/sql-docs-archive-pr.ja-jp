---
title: MSSQLSERVER_1204 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7ca03c19552b88e391d2de053193a70531571ece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640043"
---
# <a name="mssqlserver_1204"></a><span data-ttu-id="8a0f3-102">MSSQLSERVER_1204</span><span class="sxs-lookup"><span data-stu-id="8a0f3-102">MSSQLSERVER_1204</span></span>
    
## <a name="details"></a><span data-ttu-id="8a0f3-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8a0f3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a0f3-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8a0f3-104">Product Name</span></span>|<span data-ttu-id="8a0f3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8a0f3-105">SQL Server</span></span>|  
|<span data-ttu-id="8a0f3-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8a0f3-106">Event ID</span></span>|<span data-ttu-id="8a0f3-107">1204</span><span class="sxs-lookup"><span data-stu-id="8a0f3-107">1204</span></span>|  
|<span data-ttu-id="8a0f3-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8a0f3-108">Event Source</span></span>|<span data-ttu-id="8a0f3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8a0f3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8a0f3-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8a0f3-110">Component</span></span>|<span data-ttu-id="8a0f3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8a0f3-111">SQLEngine</span></span>|  
|<span data-ttu-id="8a0f3-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8a0f3-112">Symbolic Name</span></span>|<span data-ttu-id="8a0f3-113">LK_OUTOF</span><span class="sxs-lookup"><span data-stu-id="8a0f3-113">LK_OUTOF</span></span>|  
|<span data-ttu-id="8a0f3-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8a0f3-114">Message Text</span></span>|<span data-ttu-id="8a0f3-115">この時点では、SQL Server データベース エンジンのインスタンスは LOCK リソースを取得できません。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-115">The instance of the SQL Server Database Engine cannot obtain a LOCK resource at this time.</span></span> <span data-ttu-id="8a0f3-116">アクティブなユーザーが少ないときにステートメントを再実行してください。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-116">Rerun your statement when there are fewer active users.</span></span> <span data-ttu-id="8a0f3-117">データベース管理者に依頼して、このインスタンスのロックとメモリの構成を確認するか、実行時間の長いトランザクションを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-117">Ask the database administrator to check the lock and memory configuration for this instance, or to check for long-running transactions.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8a0f3-118">説明</span><span class="sxs-lookup"><span data-stu-id="8a0f3-118">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8a0f3-119">が、ロック リソースを獲得できません。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-119">cannot obtain a lock resource.</span></span> <span data-ttu-id="8a0f3-120">このエラーは次のいずれかが原因で生じている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-120">This can be caused by either of the following reasons:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8a0f3-121">が、オペレーティング システムからのメモリをこれ以上割り当てることができない。他のプロセスによってメモリが使用されているか、**max server memory** オプションが構成された状態でサーバーが動作していることが原因です。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-121">cannot allocate more memory from the operating system, either because other processes are using it, or because the server is operating with the **max server memory** option configured.</span></span>  
  
-   <span data-ttu-id="8a0f3-122">ロック マネージャーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できるメモリのうち最大 60% までしか使用できない。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-122">The lock manager will not use more than 60 percent of the memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a0f3-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8a0f3-123">User Action</span></span>  
 <span data-ttu-id="8a0f3-124">SQL Server が十分なメモリを割り当てられないようであれば、次の操作を行ってみます。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-124">If you suspect that SQL Server cannot allocate sufficient memory, try the following:</span></span>  
  
-   <span data-ttu-id="8a0f3-125">SQL Server 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションを停止するか、別のサーバーで実行することを検討します。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-125">If applications besides SQL Server are consuming resources, try stopping these applications or consider running them on a separate server.</span></span> <span data-ttu-id="8a0f3-126">これにより、他のプロセスからメモリが解放され、SQL Server で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-126">This will remove release memory from other processes for SQL Server.</span></span>  
  
-   <span data-ttu-id="8a0f3-127">max server memory を構成した場合は、設定値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-127">If you have configured max server memory, increase max server memory setting.</span></span>  
  
 <span data-ttu-id="8a0f3-128">使用可能なメモリの最大量がロック マネージャーによって使用されたと考えられる場合は、ロックの大半を取得しているトランザクションを見つけて中止します。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-128">If you suspect that the lock manager has used the maximum amount of available memory identify the transaction that is holding the most locks and terminate it.</span></span> <span data-ttu-id="8a0f3-129">次のスクリプトは、ロックの大半を取得しているトランザクションを見つけるために使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-129">The following script will identify the transaction with the most locks:</span></span>  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
 <span data-ttu-id="8a0f3-130">最も値が大きいセッション ID を見つけ、KILL コマンドでそのセッションを中止します。</span><span class="sxs-lookup"><span data-stu-id="8a0f3-130">Take the highest session id, and terminate it using the KILL command.</span></span>  
  
  
