---
title: 'SQL Server: User Settable オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- User Settable object
- SQLServer:User Settable
ms.assetid: 633de3ef-533c-4f0c-9c7b-c105129d8e94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7243ab4767c8de93dccf4556f136a94b47554d3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713070"
---
# <a name="sql-server-user-settable-object"></a><span data-ttu-id="035cf-102">SQL Server: User Settable オブジェクト</span><span class="sxs-lookup"><span data-stu-id="035cf-102">SQL Server, User Settable Object</span></span>
  <span data-ttu-id="035cf-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **User Settable** オブジェクトを使用すると、カスタムのカウンター インスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="035cf-103">The **User Settable** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows you to create custom counter instances.</span></span> <span data-ttu-id="035cf-104">カスタムのカウンター インスタンスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのユーザー独自のコンポーネントなど、既存のカウンターでは監視されないサーバーの特性を監視するために使用します。たとえば、ログに記録された顧客注文数や製品在庫数などを監視できます。</span><span class="sxs-lookup"><span data-stu-id="035cf-104">Use custom counter instances to monitor aspects of the server not monitored by existing counters, such as components unique to your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database (for example, the number of customer orders logged or the product inventory).</span></span>  
  
 <span data-ttu-id="035cf-105">**User Settable** オブジェクトには、**ユーザー カウンター 1** から **ユーザー カウンター 10** まで、クエリ カウンターの 10 個のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="035cf-105">The **User Settable** object contains 10 instances of the query counter: **User counter 1** through **User counter 10**.</span></span> <span data-ttu-id="035cf-106">これらのカウンターは、 **sp_user_counter1** から **sp_user_counter10** までの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャに対応します。</span><span class="sxs-lookup"><span data-stu-id="035cf-106">These counters map to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures **sp_user_counter1** through **sp_user_counter10**.</span></span> <span data-ttu-id="035cf-107">ユーザー アプリケーションからこれらのストアド プロシージャが実行されると、ストアド プロシージャによって設定された値がシステム モニターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="035cf-107">As these stored procedures are executed by user applications, the values set by the stored procedures are displayed in System Monitor.</span></span> <span data-ttu-id="035cf-108">1 つのカウンターは、1 日に発生した特定製品の注文件数を数えるストアド プロシージャなど、任意の整数値を 1 つ監視できます。</span><span class="sxs-lookup"><span data-stu-id="035cf-108">A counter can monitor any single integer value (for example, a stored procedure that counts how many orders for a particular product have occurred in one day).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="035cf-109">ユーザー カウンターのストアド プロシージャは、システム モニターから自動的にポーリングされることはありません。</span><span class="sxs-lookup"><span data-stu-id="035cf-109">The user counter stored procedures are not polled automatically by System Monitor.</span></span> <span data-ttu-id="035cf-110">カウンター値を更新するには、ユーザー アプリケーションから明示的にストアド プロシージャを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="035cf-110">They must be explicitly executed by a user application for the counter values to be updated.</span></span> <span data-ttu-id="035cf-111">カウンター値を自動的に更新するには、トリガーを使用します。</span><span class="sxs-lookup"><span data-stu-id="035cf-111">Use a trigger to update the value of the counter automatically.</span></span> <span data-ttu-id="035cf-112">たとえば、テーブルの行数を監視するカウンターを作成するには、テーブルに対する INSERT と DELETE のトリガーを作成し、 `SELECT COUNT(*) FROM table`というステートメントが実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="035cf-112">For example, to create a counter that monitors the number of rows in a table, create an INSERT and DELETE trigger on the table that executes the following statement: `SELECT COUNT(*) FROM table`.</span></span> <span data-ttu-id="035cf-113">テーブルに対する INSERT 操作か DELETE 操作が発生するとトリガーが起動され、システム モニター カウンターが自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="035cf-113">Whenever the trigger is fired because of an INSERT or DELETE operation occurring on the table, the System Monitor counter is automatically updated.</span></span>  
  
 <span data-ttu-id="035cf-114">次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **User Settable** オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="035cf-114">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **User Settable** object.</span></span>  
  
|<span data-ttu-id="035cf-115">SQL Server User Settable カウンター</span><span class="sxs-lookup"><span data-stu-id="035cf-115">SQL Server User Settable counters</span></span>|<span data-ttu-id="035cf-116">説明</span><span class="sxs-lookup"><span data-stu-id="035cf-116">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="035cf-117">**クエリ**</span><span class="sxs-lookup"><span data-stu-id="035cf-117">**Query**</span></span>|<span data-ttu-id="035cf-118">**User Settable** オブジェクトには、Query カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="035cf-118">The **User Settable** object contains the query counter.</span></span> <span data-ttu-id="035cf-119">ユーザーは、クエリ オブジェクト内の **ユーザー カウンター** を構成します。</span><span class="sxs-lookup"><span data-stu-id="035cf-119">Users configure the **User counters** within the query object.</span></span>|  
  
 <span data-ttu-id="035cf-120">次の表では、 **Query** カウンターの **インスタンス** について説明します。</span><span class="sxs-lookup"><span data-stu-id="035cf-120">This table describes the **instances** of the **Query** counter.</span></span>  
  
|<span data-ttu-id="035cf-121">Query カウンターのインスタンス</span><span class="sxs-lookup"><span data-stu-id="035cf-121">Query counter instances</span></span>|<span data-ttu-id="035cf-122">説明</span><span class="sxs-lookup"><span data-stu-id="035cf-122">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="035cf-123">**ユーザー カウンター 1**</span><span class="sxs-lookup"><span data-stu-id="035cf-123">**User counter 1**</span></span>|<span data-ttu-id="035cf-124">**sp_user_counter1**を使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="035cf-124">Defined using **sp_user_counter1**.</span></span>|  
|<span data-ttu-id="035cf-125">**ユーザー カウンター 2**</span><span class="sxs-lookup"><span data-stu-id="035cf-125">**User counter 2**</span></span>|<span data-ttu-id="035cf-126">**sp_user_counter2**を使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="035cf-126">Defined using **sp_user_counter2**.</span></span>|  
|<span data-ttu-id="035cf-127">**ユーザー カウンター 3**</span><span class="sxs-lookup"><span data-stu-id="035cf-127">**User counter 3**</span></span>|<span data-ttu-id="035cf-128">**sp_user_counter3**を使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="035cf-128">Defined using **sp_user_counter3**.</span></span>|  
|<span data-ttu-id="035cf-129">...</span><span class="sxs-lookup"><span data-stu-id="035cf-129">...</span></span>||  
|<span data-ttu-id="035cf-130">**ユーザー カウンター 10**</span><span class="sxs-lookup"><span data-stu-id="035cf-130">**User counter 10**</span></span>|<span data-ttu-id="035cf-131">**sp_user_counter10**を使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="035cf-131">Defined using **sp_user_counter10**.</span></span>|  
  
 <span data-ttu-id="035cf-132">ユーザー カウンターのストアド プロシージャを使用するには、カウンターの新しい値を示す 1 つの整数パラメーターを指定して、独自のアプリケーションからそのストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="035cf-132">To make use of the user counter stored procedures, execute them from your own application with a single integer parameter representing the new value for the counter.</span></span> <span data-ttu-id="035cf-133">たとえば、 **ユーザー カウンター 1** の値を 10 に設定するには、次の Transact-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="035cf-133">For example, to set **User counter 1** to the value 10, execute this Transact-SQL statement:</span></span>  
  
```  
EXECUTE sp_user_counter1 10  
```  
  
 <span data-ttu-id="035cf-134">ユーザー カウンターのストアド プロシージャは、独自のストアド プロシージャなど他のストアド プロシージャを呼び出せる場所なら、どこからでも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="035cf-134">The user counter stored procedures can be called from anywhere other stored procedures can be called, such as your own stored procedures.</span></span> <span data-ttu-id="035cf-135">たとえば、次のストアド プロシージャを作成して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動されてから行われた接続と接続試行の数を数えることができます。</span><span class="sxs-lookup"><span data-stu-id="035cf-135">For example, you can create the following stored procedure to count the number of connections and attempted connections since an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] was started:</span></span>  
  
```  
DROP PROC My_Proc  
GO  
CREATE PROC My_Proc  
AS   
   EXECUTE sp_user_counter1 @@CONNECTIONS  
GO  
```  
  
 <span data-ttu-id="035cf-136">@@CONNECTIONS 関数は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動されてから行われた接続または接続試行の数を返します。</span><span class="sxs-lookup"><span data-stu-id="035cf-136">The @@CONNECTIONS function returns the number of connections or attempted connections since an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] started.</span></span> <span data-ttu-id="035cf-137">返された値が、パラメーターとして **sp_user_counter1** ストアド プロシージャに渡されます。</span><span class="sxs-lookup"><span data-stu-id="035cf-137">This value is passed to the **sp_user_counter1** stored procedure as the parameter.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="035cf-138">ユーザー カウンターのストアド プロシージャで定義するクエリは、できるだけ単純なものにしてください。</span><span class="sxs-lookup"><span data-stu-id="035cf-138">Make the queries defined in the user counter stored procedures as simple as possible.</span></span> <span data-ttu-id="035cf-139">大量の並べ替え操作やハッシュ操作を実行するクエリや大量の I/O を実行するクエリは、メモリを集中的に消費するので、パフォーマンスに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="035cf-139">Memory-intensive queries that perform substantial sort or hash operations or queries that perform large amounts of I/O are expensive to execute and can impact performance.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="035cf-140">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="035cf-140">Permissions</span></span>  
 <span data-ttu-id="035cf-141">**sp_user_counter** はすべてのユーザーが使用できますが、任意のクエリ カウンターに制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="035cf-141">**sp_user_counter** is available for all users but can be restricted for any query counter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035cf-142">参照</span><span class="sxs-lookup"><span data-stu-id="035cf-142">See Also</span></span>  
 [<span data-ttu-id="035cf-143">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="035cf-143">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
