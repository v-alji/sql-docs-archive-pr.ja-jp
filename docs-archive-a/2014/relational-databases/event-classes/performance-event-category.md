---
title: Performance イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b0c076a4132298797313ecbf0874d9d2d4e453cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642776"
---
# <a name="performance-event-category"></a><span data-ttu-id="23b1e-102">Performance イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="23b1e-102">Performance Event Category</span></span>
  <span data-ttu-id="23b1e-103">**Performance** イベント カテゴリを使用すると、 **Showplan** イベント クラス、および SQL DML (データ操作言語) の操作を実行したときに作成されるイベント クラスを監視できます。</span><span class="sxs-lookup"><span data-stu-id="23b1e-103">Use the **Performance** event category to monitor **Showplan** event classes and event classes that are produced from the execution of SQL data manipulation language (DML) operators.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23b1e-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="23b1e-104">In This Section</span></span>  
  
|<span data-ttu-id="23b1e-105">トピック</span><span class="sxs-lookup"><span data-stu-id="23b1e-105">Topic</span></span>|<span data-ttu-id="23b1e-106">説明</span><span class="sxs-lookup"><span data-stu-id="23b1e-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="23b1e-107">Auto Stats イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-107">Auto Stats Event Class</span></span>](auto-stats-event-class.md)|<span data-ttu-id="23b1e-108">インデックス統計および列統計の自動更新が実行されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-108">Indicates that an automatic updating of index and column statistics has occurred.</span></span>|  
|[<span data-ttu-id="23b1e-109">Degree of Parallelism &#40;7.0 Insert&#41; イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-109">Degree of Parallelism &#40;7.0 Insert&#41; Event Class</span></span>](degree-of-parallelism-7-0-insert-event-class.md)|<span data-ttu-id="23b1e-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、直列プランまたは並列プランのいずれかを使用して SELECT、INSERT、UPDATE、または DELETE ステートメントが実行されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-110">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has executed a SELECT, INSERT, UPDATE, or DELETE statement using either a serial or parallel plan.</span></span> <span data-ttu-id="23b1e-111">操作の実行に使用された CPU の数もレポートされます。</span><span class="sxs-lookup"><span data-stu-id="23b1e-111">The number of CPUs used to perform the operation is also reported.</span></span>|  
|[<span data-ttu-id="23b1e-112">Performance Statistics イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-112">Performance Statistics Event Class</span></span>](performance-statistics-event-class.md)|<span data-ttu-id="23b1e-113">実行中のクエリのパフォーマンスを監視します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-113">Monitors performance of the queries that are being executed.</span></span>|  
|[<span data-ttu-id="23b1e-114">Showplan All イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-114">Showplan All Event Class</span></span>](showplan-all-event-class.md)|<span data-ttu-id="23b1e-115">SQL ステートメント内の **Showplan** 操作を識別します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-115">Identifies **Showplan** operators within a SQL statement.</span></span>|  
|[<span data-ttu-id="23b1e-116">Showplan All for Query Compile イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-116">Showplan All for Query Compile Event Class</span></span>](showplan-all-for-query-compile-event-class.md)|<span data-ttu-id="23b1e-117">**Showplan** 操作のコンパイル時間データを表示します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-117">Displays compile time data for **Showplan** operators.</span></span>|  
|[<span data-ttu-id="23b1e-118">Showplan Statistics Profile イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-118">Showplan Statistics Profile Event Class</span></span>](showplan-statistics-profile-event-class.md)|<span data-ttu-id="23b1e-119">クエリの推定コストを表示します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-119">Displays the estimated cost of a query.</span></span>|  
|[<span data-ttu-id="23b1e-120">Showplan XML イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-120">Showplan XML Event Class</span></span>](showplan-xml-event-class.md)|<span data-ttu-id="23b1e-121">SQL ステートメント内の **Showplan** 操作を識別します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-121">Identifies the **Showplan** operators in a SQL statement.</span></span> <span data-ttu-id="23b1e-122">このイベント クラスには、各イベントが整形式の XML ドキュメントとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="23b1e-122">The event class stores each event as a well defined XML document.</span></span>|  
|[<span data-ttu-id="23b1e-123">Showplan XML for Query Compile イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-123">Showplan XML for Query Compile Event Class</span></span>](showplan-xml-for-query-compile-event-class.md)|<span data-ttu-id="23b1e-124">**Showplan** 操作のコンパイル時間データを XML 形式で表示します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-124">Displays compile time data for **Showplan** operators in XML format.</span></span>|  
|[<span data-ttu-id="23b1e-125">Showplan XML Statistics Profile イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-125">Showplan XML Statistics Profile Event Class</span></span>](showplan-xml-statistics-profile-event-class.md)|<span data-ttu-id="23b1e-126">SQL ステートメントに関連付けられた **Showplan** 操作を識別します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-126">Identifies the **Showplan** operators associated with a SQL statement.</span></span> <span data-ttu-id="23b1e-127">出力は XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="23b1e-127">The output is an XML document.</span></span>|  
|[<span data-ttu-id="23b1e-128">SQL:FullTextQuery イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-128">SQL:FullTextQuery Event Class</span></span>](sql-fulltextquery-event-class.md)|<span data-ttu-id="23b1e-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でフルテキスト クエリが実行されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-129">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has executed a full-text query.</span></span>|  
|[<span data-ttu-id="23b1e-130">Plan Guide Successful イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-130">Plan Guide Successful Event Class</span></span>](plan-guide-successful-event-class.md)|<span data-ttu-id="23b1e-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でプラン ガイドを含むクエリまたはバッチの実行プランが正常に生成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-131">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] successfully produced an execution plan for a query or batch that contained a plan guide.</span></span>|  
|[<span data-ttu-id="23b1e-132">Plan Guide Unsuccessful イベント クラス</span><span class="sxs-lookup"><span data-stu-id="23b1e-132">Plan Guide Unsuccessful Event Class</span></span>](plan-guide-unsuccessful-event-class.md)|<span data-ttu-id="23b1e-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でプラン ガイドを含むクエリまたはバッチの実行プランを生成できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="23b1e-133">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could not produce an execution plan for a query or batch that contained a plan guide.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23b1e-134">参照</span><span class="sxs-lookup"><span data-stu-id="23b1e-134">See Also</span></span>  
 [<span data-ttu-id="23b1e-135">拡張イベント</span><span class="sxs-lookup"><span data-stu-id="23b1e-135">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
