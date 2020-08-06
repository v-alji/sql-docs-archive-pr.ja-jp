---
title: リソース ガバナーの分類子関数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, classifier function
- user-defined functions [SQL Server], classifier function
- classifier function [SQL Server]
- classifier function [SQL Server], overview
ms.assetid: 64c25012-7068-476f-afa2-0b4f3adde9a4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69b6fd10ac0adc6f76925e0d41f110b917111466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715146"
---
# <a name="resource-governor-classifier-function"></a><span data-ttu-id="7a96a-102">リソース ガバナーの分類子関数</span><span class="sxs-lookup"><span data-stu-id="7a96a-102">Resource Governor Classifier Function</span></span>
  <span data-ttu-id="7a96a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソース ガバナーの分類プロセスにより、着信セッションがセッションの特性に基づいてワークロード グループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource governor classification process assigns incoming sessions to a workload group based on the characteristics of the session.</span></span> <span data-ttu-id="7a96a-104">分類ロジックは、分類子関数と呼ばれるユーザー定義関数を記述することで調整できます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-104">You can tailor the classification logic by writing a user-defined function, called a classifier function.</span></span>  
  
## <a name="classification"></a><span data-ttu-id="7a96a-105">分類</span><span class="sxs-lookup"><span data-stu-id="7a96a-105">Classification</span></span>  
 <span data-ttu-id="7a96a-106">リソース ガバナーでは、着信セッションの分類がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-106">Resource Governor supports the classification of incoming sessions.</span></span> <span data-ttu-id="7a96a-107">分類は、関数に含まれているユーザーが記述した一連の基準に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-107">Classification is based on a set of user-written criteria contained in a function.</span></span> <span data-ttu-id="7a96a-108">この関数ロジックの結果を使用して、リソース ガバナーは、セッションを既存のワークロード グループに分類します。</span><span class="sxs-lookup"><span data-stu-id="7a96a-108">The results of the function logic enable Resource Governor to classify sessions into existing workload groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a96a-109">内部ワークロード グループには、内部だけで使用される要求が格納されます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-109">The internal workload group is populated with requests that are for internal use only.</span></span> <span data-ttu-id="7a96a-110">要求のルーティングに使用される基準は変更できません。また、要求を内部ワークロード グループに分類することもできません。</span><span class="sxs-lookup"><span data-stu-id="7a96a-110">You cannot change the criteria used for routing these requests and you cannot classify requests into the internal workload group.</span></span>  
  
 <span data-ttu-id="7a96a-111">着信セッションをワークロード グループに割り当てるロジックを含んだスカラー関数を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-111">You can write a scalar function that contains the logic that is used to assign incoming sessions to a workload group.</span></span> <span data-ttu-id="7a96a-112">この関数を使用する前に、次の操作を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a96a-112">Before you can use this function, you must complete the following actions:</span></span>  
  
-   <span data-ttu-id="7a96a-113">ALTER RESOURCE GOVERNOR ステートメントを使用して、関数を作成し、登録します。</span><span class="sxs-lookup"><span data-stu-id="7a96a-113">Create and register the function using the ALTER RESOURCE GOVERNOR statement.</span></span> <span data-ttu-id="7a96a-114">詳細については、「[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a96a-114">For more information, see [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql).</span></span>  
  
-   <span data-ttu-id="7a96a-115">RECONFIGURE パラメーターを指定した ALTER RESOURCE GOVERNOR ステートメントを使用して、リソース ガバナーの構成を更新します。</span><span class="sxs-lookup"><span data-stu-id="7a96a-115">Update the Resource Governor configuration using the ALTER RESOURCE GOVERNOR statement with the RECONFIGURE parameter.</span></span>  
  
 <span data-ttu-id="7a96a-116">関数を作成して構成の変更を適用すると、この関数から返されたワークロード グループ名がリソース ガバナーの分類で使用されて、適切なワークロード グループに新しい要求が送信されます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-116">After you create the function and apply the configuration changes, the Resource Governor classifier will use the workload group name returned by the function to send a new request to the appropriate workload group.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7a96a-117">分類関数が指定のログイン タイムアウトまでに完了せずに、クライアント セッションがタイムアウトになることがあります。</span><span class="sxs-lookup"><span data-stu-id="7a96a-117">The client session may time out if the classification function does not complete within the specified time-out for the login.</span></span> <span data-ttu-id="7a96a-118">ログイン タイムアウトはクライアントのプロパティであるため、サーバーはタイムアウトを認識しません。分類関数の実行時間が長いと、孤立した接続がサーバーに長時間残される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a96a-118">Login time-out is a client property and as such, the server is unaware of a time-out. A long-running classifier function can leave the server with orphaned connections for long periods.</span></span> <span data-ttu-id="7a96a-119">接続がタイムアウトになる前に実行が完了する分類関数を作成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="7a96a-119">It is important that you create classifier functions that finish executing before a connection time-out.</span></span>  
  
 <span data-ttu-id="7a96a-120">ユーザー定義関数の特性と動作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7a96a-120">The user-defined function has the following characteristics and behaviors:</span></span>  
  
-   <span data-ttu-id="7a96a-121">ユーザー定義関数は、接続プールが有効になっている場合でも、新しいセッションすべてに対して評価されます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-121">The user-defined function is evaluated for every new session, even when connection pooling is enabled.</span></span>  
  
-   <span data-ttu-id="7a96a-122">ユーザー定義関数は、セッションにワークロード グループ コンテキストを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-122">The user-defined function gives workload group context for the session.</span></span> <span data-ttu-id="7a96a-123">グループのメンバーシップが確定すると、セッションがその有効期間にわたってワークロード グループにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-123">After group membership is determined, the session is bound to the workload group for the lifetime of the session.</span></span>  
  
-   <span data-ttu-id="7a96a-124">ユーザー定義関数が NULL、既定値、または存在しないグループの名前を返した場合は、セッションに既定のワークロード グループ コンテキストが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-124">If the user-defined function returns NULL, default, or the name of non-existent group the session is given the default workload group context.</span></span> <span data-ttu-id="7a96a-125">関数が何らかの理由で失敗した場合も、セッションに既定のコンテキストが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-125">The session is also given the default context if the function fails for any reason.</span></span>  
  
-   <span data-ttu-id="7a96a-126">ユーザー定義関数は、サーバー スコープ (master データベース) で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a96a-126">The function should be defined with server scope (master database).</span></span>  
  
-   <span data-ttu-id="7a96a-127">ユーザー定義の分類関数の指定は、ALTER RESOURCE GOVERNOR RECONFIGURE を実行するまで有効となりません。</span><span class="sxs-lookup"><span data-stu-id="7a96a-127">The classifier user-defined function designation only takes effect after ALTER RESOURCE GOVERNOR RECONFIGURE is executed.</span></span>  
  
-   <span data-ttu-id="7a96a-128">分類子として指定できるのは、一度に 1 つのユーザー定義関数だけです。</span><span class="sxs-lookup"><span data-stu-id="7a96a-128">Only one user-defined function can be designated as a classifier at a time.</span></span>  
  
-   <span data-ttu-id="7a96a-129">ユーザー定義の分類関数は、分類子の状態が削除されない限り、削除または変更できません。</span><span class="sxs-lookup"><span data-stu-id="7a96a-129">The classifier user-defined function cannot be dropped or altered unless its classifier status is removed.</span></span>  
  
-   <span data-ttu-id="7a96a-130">ユーザー定義の分類関数がない場合は、すべてのセッションが既定のグループに分類されます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-130">In the absence of a classifier user-defined function, all sessions are classified into the default group.</span></span>  
  
-   <span data-ttu-id="7a96a-131">分類関数から返されたワークロード グループは、スキーマ バインド制限の対象外です。</span><span class="sxs-lookup"><span data-stu-id="7a96a-131">The workload group returned by the classifier function is outside the scope of the schema-binding restriction.</span></span> <span data-ttu-id="7a96a-132">たとえば、テーブルを削除することはできませんが、ワークロード グループは削除できます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-132">For example, you cannot drop a table, but you can drop a workload group.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7a96a-133">サーバー上で専用管理者接続 (DAC) を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7a96a-133">We recommend enabling the Dedicated Administrator Connection (DAC) on the server.</span></span> <span data-ttu-id="7a96a-134">DAC は、リソース ガバナーの分類の対象ではなく、分類関数の監視とトラブルシューティングに使用できます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-134">The DAC is not subject to Resource Governor classification and can be used to monitor and troubleshoot a classifier function.</span></span> <span data-ttu-id="7a96a-135">詳細については、「 [データベース管理者用の診断接続](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a96a-135">For more information, see [Diagnostic Connection for Database Administrators](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span> <span data-ttu-id="7a96a-136">トラブルシューティングに DAC を使用できない場合は、システムをシングル ユーザー モードで再起動します。</span><span class="sxs-lookup"><span data-stu-id="7a96a-136">If a DAC is not available for troubleshooting, the other option is to restart the system in single user mode.</span></span> <span data-ttu-id="7a96a-137">シングル ユーザー モードは分類の対象となりませんが、実行中のリソース ガバナーによる分類をこのモードで診断することはできません。</span><span class="sxs-lookup"><span data-stu-id="7a96a-137">Although single user mode is not subject to classification, it does not give you the ability to diagnose Resource Governor classification while it is running.</span></span>  
  
### <a name="classification-process"></a><span data-ttu-id="7a96a-138">分類処理</span><span class="sxs-lookup"><span data-stu-id="7a96a-138">Classification Process</span></span>  
 <span data-ttu-id="7a96a-139">リソース ガバナーのコンテキストでは、セッションのログイン プロセスが次の手順で実行されます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-139">In the context of Resource Governor, the login process for a session consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="7a96a-140">ログイン認証</span><span class="sxs-lookup"><span data-stu-id="7a96a-140">Login authentication</span></span>  
  
2.  <span data-ttu-id="7a96a-141">LOGON トリガー実行</span><span class="sxs-lookup"><span data-stu-id="7a96a-141">LOGON trigger execution</span></span>  
  
3.  <span data-ttu-id="7a96a-142">分類</span><span class="sxs-lookup"><span data-stu-id="7a96a-142">Classification</span></span>  
  
 <span data-ttu-id="7a96a-143">分類が開始されると、リソース ガバナーは分類子関数を実行し、関数から返された値を使用して適切なワークロード グループに要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="7a96a-143">When classification starts, Resource Governor executes the classifier function and uses the value returned by the function to send requests to the appropriate workload group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a96a-144">分類関数および LOGON トリガーの実行に関する情報は、 [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) および [sys.dm_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql)」で公開されます。</span><span class="sxs-lookup"><span data-stu-id="7a96a-144">Information about the execution of the classifier function and LOGON triggers is exposed in [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) and [sys.dm_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql).</span></span>  
  
## <a name="classification-function-tasks"></a><span data-ttu-id="7a96a-145">分類関数のタスク</span><span class="sxs-lookup"><span data-stu-id="7a96a-145">Classification Function Tasks</span></span>  
  
|<span data-ttu-id="7a96a-146">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="7a96a-146">Task Description</span></span>|<span data-ttu-id="7a96a-147">トピック</span><span class="sxs-lookup"><span data-stu-id="7a96a-147">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="7a96a-148">ユーザー定義の分類子関数を作成およびテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a96a-148">Describes how to create and test a classifier user-defined function.</span></span>|[<span data-ttu-id="7a96a-149">ユーザー定義の分類子関数の作成とテスト</span><span class="sxs-lookup"><span data-stu-id="7a96a-149">Create and Test a Classifier User-Defined Function</span></span>](create-and-test-a-classifier-user-defined-function.md)|  
  
## <a name="see-also"></a><span data-ttu-id="7a96a-150">参照</span><span class="sxs-lookup"><span data-stu-id="7a96a-150">See Also</span></span>  
 <span data-ttu-id="7a96a-151">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="7a96a-151">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="7a96a-152">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="7a96a-152">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="7a96a-153">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="7a96a-153">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="7a96a-154">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="7a96a-154">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="7a96a-155">[テンプレートを使用してリソース ガバナーを構成する](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="7a96a-155">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 [<span data-ttu-id="7a96a-156">リソース ガバナー プロパティの表示</span><span class="sxs-lookup"><span data-stu-id="7a96a-156">View Resource Governor Properties</span></span>](view-resource-governor-properties.md)  
  
  
