---
title: レプリケーションの種類 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5576331004eca44bc32dbde8f430284f75e6eb70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717804"
---
# <a name="types-of-replication"></a><span data-ttu-id="88178-102">レプリケーションの種類</span><span class="sxs-lookup"><span data-stu-id="88178-102">Types of Replication</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="88178-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、以下の種類のレプリケーションを分散型アプリケーションで利用できます。</span><span class="sxs-lookup"><span data-stu-id="88178-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following types of replication for use in distributed applications:</span></span>  
  
-   <span data-ttu-id="88178-104">トランザクション レプリケーション。</span><span class="sxs-lookup"><span data-stu-id="88178-104">Transactional replication.</span></span> <span data-ttu-id="88178-105">詳細については、「 [Transactional Replication](transactional/transactional-replication.md)」 (トランザクション レプリケーション) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88178-105">For more information, see [Transactional Replication](transactional/transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="88178-106">マージ レプリケーション。</span><span class="sxs-lookup"><span data-stu-id="88178-106">Merge replication.</span></span> <span data-ttu-id="88178-107">詳細については、「[Merge Replication](merge/merge-replication.md)」 (マージ レプリケーション) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="88178-107">For more information, see [Merge Replication](merge/merge-replication.md).</span></span>  
  
-   <span data-ttu-id="88178-108">スナップショット レプリケーション。</span><span class="sxs-lookup"><span data-stu-id="88178-108">Snapshot replication.</span></span> <span data-ttu-id="88178-109">詳細については、「[Snapshot Replication](snapshot-replication.md)」 (スナップショット レプリケーション) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="88178-109">For more information, see [Snapshot Replication](snapshot-replication.md).</span></span>  
  
 <span data-ttu-id="88178-110">アプリケーションで使用するレプリケーションの種類は、物理的なレプリケーション環境、レプリケートするデータの種類と量、データをサブスクライバーで更新するかどうかなどの、さまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="88178-110">The type of replication you choose for an application depends on many factors, including the physical replication environment, the type and quantity of data to be replicated, and whether the data is updated at the Subscriber.</span></span> <span data-ttu-id="88178-111">物理環境には、レプリケーションに関係するコンピューターの数と場所、これらのコンピューターがクライアント (ワークステーション、ラップトップ、またはハンドヘルド デバイス) なのかサーバーなのか、などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="88178-111">The physical environment includes the number and location of computers involved in replication and whether these computers are clients (workstations, laptops, or handheld devices) or servers.</span></span>  
  
 <span data-ttu-id="88178-112">どの種類のレプリケーションも、通常、パブリッシュされたオブジェクトをパブリッシャーとサブスクライバー間で初期同期することから始まります。</span><span class="sxs-lookup"><span data-stu-id="88178-112">Each type of replication typically begins with an initial synchronization of the published objects between the Publisher and Subscribers.</span></span> <span data-ttu-id="88178-113">初期同期は、 *スナップショット*を使用したレプリケーションで実行できます。スナップショットは、パブリケーションで指定されたすべてのオブジェクトおよびデータのコピーです。</span><span class="sxs-lookup"><span data-stu-id="88178-113">This initial synchronization can be performed by replication with a *snapshot*, which is a copy of all of the objects and data specified by a publication.</span></span> <span data-ttu-id="88178-114">作成されたスナップショットはサブスクライバーに配信されます。</span><span class="sxs-lookup"><span data-stu-id="88178-114">After the snapshot is created, it is delivered to the Subscribers.</span></span> <span data-ttu-id="88178-115">アプリケーションによっては、スナップショット レプリケーションのみで十分なこともあります。</span><span class="sxs-lookup"><span data-stu-id="88178-115">For some applications, snapshot replication is all that is required.</span></span> <span data-ttu-id="88178-116">スナップショット レプリケーションだけでは不十分なアプリケーションでは、その後行われたデータ変更が、一定期間にわたって増分としてサブスクライバーに渡されることが重要です。</span><span class="sxs-lookup"><span data-stu-id="88178-116">For other types of applications, it is important that subsequent data changes flow to the Subscriber incrementally over time.</span></span> <span data-ttu-id="88178-117">また、アプリケーションによっては、サブスクライバーからパブリッシャーに変更を送り返す必要もあります。</span><span class="sxs-lookup"><span data-stu-id="88178-117">Some applications also require that changes flow from the Subscriber back to the Publisher.</span></span> <span data-ttu-id="88178-118">トランザクション レプリケーションおよびマージ レプリケーションには、このような種類のアプリケーション用のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="88178-118">Transactional replication and merge replication provide options for these types of applications.</span></span>  
  
 <span data-ttu-id="88178-119">スナップショット レプリケーションでは、データの変更は追跡されず、スナップショットが適用されるたびに、既存のデータがすべて上書きされます。</span><span class="sxs-lookup"><span data-stu-id="88178-119">Data changes are not tracked for snapshot replication; each time a snapshot is applied, it completely overwrites the existing data.</span></span> <span data-ttu-id="88178-120">トランザクション レプリケーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] トランザクション ログを使用して変更が追跡され、マージ レプリケーションでは、トリガーとメタデータ テーブルを使用して変更が追跡されます。</span><span class="sxs-lookup"><span data-stu-id="88178-120">Transactional replication tracks changes through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction log, and merge replication tracks changes through triggers and metadata tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88178-121">参照</span><span class="sxs-lookup"><span data-stu-id="88178-121">See Also</span></span>  
 [<span data-ttu-id="88178-122">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="88178-122">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
