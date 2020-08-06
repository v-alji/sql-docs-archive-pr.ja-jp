---
title: クエリプランの移行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dafd3a5f8a460bb08e63919c2cb853ad74dc2f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718686"
---
# <a name="migrate-query-plans"></a><span data-ttu-id="338e8-102">クエリ プランの移行</span><span class="sxs-lookup"><span data-stu-id="338e8-102">Migrate Query Plans</span></span>
  <span data-ttu-id="338e8-103">データベースを最新バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードすると、ほとんどの場合、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="338e8-103">In most cases, upgrading a database to the most recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will result in improved query performance.</span></span> <span data-ttu-id="338e8-104">ただし、慎重にパフォーマンス チューニングされたミッションクリティカルなクエリがある場合は、アップグレードする前に、各クエリのプラン ガイドを作成してこれらのクエリのクエリ プランを保存しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="338e8-104">However, if you have mission-critical queries that have been carefully tuned for performance, you may want to preserve the query plans for these queries before upgrading by creating a plan guide for each query.</span></span> <span data-ttu-id="338e8-105">アップグレード後に、効率性の劣るクエリ プランが 1 つ以上のクエリに対してクエリ オプティマイザーで選択される場合は、プラン ガイドを有効にし、強制的にアップグレード前のプランが使用されるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="338e8-105">If, after upgrading, the query optimizer chooses a less efficient plan for one or more of the queries, you can enable the plan guides and force the query optimizer to use the pre-upgrade plans.</span></span>  
  
 <span data-ttu-id="338e8-106">アップグレードする前にプラン ガイドを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="338e8-106">To create plan guides before upgrading follow these steps:</span></span>  
  
1.  <span data-ttu-id="338e8-107">[Sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)ストアドプロシージャを使用し、USE plan クエリヒントでクエリプランを指定することにより、各ミッションクリティカルなクエリの現在のプランを記録します。</span><span class="sxs-lookup"><span data-stu-id="338e8-107">Record the current plan for each mission critical query by using the [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) stored procedure and specifying the query plan in the USE PLAN query hint.</span></span>  
  
2.  <span data-ttu-id="338e8-108">プラン ガイドがクエリに適用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="338e8-108">Verify that the plan guide is applied to the query.</span></span>  
  
3.  <span data-ttu-id="338e8-109">データベースを最新のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="338e8-109">Upgrade the database to the newer version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="338e8-110">このクエリ プランは、アップグレードしたデータベースのプラン ガイドに保存され、アップグレード後に効率性の劣るプランが選択された場合のフォールバックとして機能します。</span><span class="sxs-lookup"><span data-stu-id="338e8-110">The plans are persisted in the upgraded database in the plan guides and serve as a fallback in case of plan regressions after the upgrade.</span></span>  
  
     <span data-ttu-id="338e8-111">アップグレード後にプラン ガイドを有効にしないようお勧めします。統計の更新により、新しいリリースに含まれる優れたプランや有益な再コンパイルを利用できなくなる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="338e8-111">We recommend that you not enable the plan guides after the upgrade because you might miss opportunities for better plans in the new release or beneficial recompiles due to updated statistics.</span></span>  
  
4.  <span data-ttu-id="338e8-112">アップグレード後に効率性の劣るプランが選択される場合は、すべてのプラン ガイドまたはその一部を有効にして新しいプランをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="338e8-112">If less efficient plans are chosen after the upgrade, activate all or a subset of the plan guides to override the new plans.</span></span>  
  
## <a name="example"></a><span data-ttu-id="338e8-113">例</span><span class="sxs-lookup"><span data-stu-id="338e8-113">Example</span></span>  
 <span data-ttu-id="338e8-114">次の例は、プラン ガイドを作成することにより、アップグレード前のプランを記録する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="338e8-114">The following example shows how to record a pre-upgrade plan for a query by creating a plan guide.</span></span>  
  
### <a name="step-1-collect-the-plan"></a><span data-ttu-id="338e8-115">手順 1: プランを収集する</span><span class="sxs-lookup"><span data-stu-id="338e8-115">Step 1: Collect the Plan</span></span>  
 <span data-ttu-id="338e8-116">プラン ガイドに記録するクエリ プランは XML 形式にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="338e8-116">The query plan recorded in the plan guide must be in XML format.</span></span> <span data-ttu-id="338e8-117">XML 形式のクエリ プランは、次の方法で生成できます。</span><span class="sxs-lookup"><span data-stu-id="338e8-117">XML-formatted query plans can be produced through the following ways:</span></span>  
  
-   [<span data-ttu-id="338e8-118">SET SHOWPLAN_XML</span><span class="sxs-lookup"><span data-stu-id="338e8-118">SET SHOWPLAN_XML</span></span>](/sql/t-sql/statements/set-showplan-xml-transact-sql)  
  
-   [<span data-ttu-id="338e8-119">SET STATISTICS XML</span><span class="sxs-lookup"><span data-stu-id="338e8-119">SET STATISTICS XML</span></span>](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
-   <span data-ttu-id="338e8-120">動的管理関数[dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql)の query_plan 列を照会しています。</span><span class="sxs-lookup"><span data-stu-id="338e8-120">Querying the query_plan column of the [sys.dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql) dynamic management function.</span></span>  
  
-   <span data-ttu-id="338e8-121">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [Showplan xml](../../relational-databases/event-classes/showplan-xml-event-class.md)、 [showplan xml Statistics PROFILE](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)、および[showplan xml For Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)イベントクラス。</span><span class="sxs-lookup"><span data-stu-id="338e8-121">The [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md), [Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md), and [Showplan XML For Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md) event classes.</span></span>  
  
 <span data-ttu-id="338e8-122">次の例では、動的管理ビューに対してクエリを実行することにより、`SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` ステートメントのクエリ プランを収集します。</span><span class="sxs-lookup"><span data-stu-id="338e8-122">The following example collects the query plan for the statement `SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` by querying dynamic management views.</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%';  
GO  
```  
  
### <a name="step-2-create-the-plan-guide-to-force-the-plan"></a><span data-ttu-id="338e8-123">手順 2: プラン ガイドを作成しプランを適用する</span><span class="sxs-lookup"><span data-stu-id="338e8-123">Step 2: Create the Plan Guide to Force the Plan</span></span>  
 <span data-ttu-id="338e8-124">プラン ガイドで (前述のいずれかの方法で取得した) XML 形式のクエリ プランを使用し、sp_create_plan_guide の OPTION 句に指定した USE PLAN クエリ ヒント内に、文字列リテラルとしてそのクエリ プランをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="338e8-124">Using the XML-formatted query plan (obtained by any of the methods previously described) in the plan guide, copy and paste the query plan as a string literal inside the USE PLAN query hint specified in the OPTION clause of sp_create_plan_guide.</span></span>  
  
 <span data-ttu-id="338e8-125">プラン ガイドを作成する前に、XML プラン自体に含まれている引用符 (') には引用符をもう 1 つ付けてエスケープします。</span><span class="sxs-lookup"><span data-stu-id="338e8-125">Within the XML plan itself, escape quotation marks (') that appear in the plan with a second quotation mark before creating the plan guide.</span></span> <span data-ttu-id="338e8-126">たとえば、`WHERE A.varchar = 'This is a string'` を含むプランの場合は、コードを `WHERE A.varchar = ''This is a string''` のように変更してエスケープする必要があります。</span><span class="sxs-lookup"><span data-stu-id="338e8-126">For example, a plan that contains `WHERE A.varchar = 'This is a string'` must be escaped by modifying the code to `WHERE A.varchar = ''This is a string''`.</span></span>  
  
 <span data-ttu-id="338e8-127">次の例では、手順 1 で収集したクエリ プランのプラン ガイドを作成し、クエリの XML プラン表示を `@hints` パラメーターに挿入します。</span><span class="sxs-lookup"><span data-stu-id="338e8-127">The following example creates a plan guide for the query plan collected in step 1 and inserts the XML Showplan for the query in the `@hints` parameter.</span></span> <span data-ttu-id="338e8-128">簡略にするため、この例には一部のプラン表示出力しか含まれていません。</span><span class="sxs-lookup"><span data-stu-id="338e8-128">For brevity, only partial Showplan output is included in the example.</span></span>  
  
```  
EXECUTE sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',  
@type = N'SQL',  
@module_or_batch = NULL,  
@params = NULL,  
@hints = N'OPTION(USE PLAN N''<ShowPlanXML xmlns=''''https://schemas.microsoft.com/sqlserver/2004/07/showplan''''   
    Version=''''0.5'''' Build=''''9.00.1116''''>  
    <BatchSequence><Batch><Statements><StmtSimple>  
    ...  
    </StmtSimple></Statements></Batch>  
    </BatchSequence></ShowPlanXML>'')';  
GO  
```  
  
### <a name="step-3-verify-that-the-plan-guide-is-applied-to-the-query"></a><span data-ttu-id="338e8-129">手順 3: プラン ガイドがクエリに適用されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="338e8-129">Step 3: Verify That the Plan Guide Is Applied to the Query</span></span>  
 <span data-ttu-id="338e8-130">クエリを再実行し、生成されたクエリ プランを調べます。</span><span class="sxs-lookup"><span data-stu-id="338e8-130">Run the query again and examine the query plan that is produced.</span></span> <span data-ttu-id="338e8-131">このプランがプラン ガイドで指定したプランに一致していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="338e8-131">You should see that the plan matches the one that you specified in the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="338e8-132">参照</span><span class="sxs-lookup"><span data-stu-id="338e8-132">See Also</span></span>  
 <span data-ttu-id="338e8-133">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="338e8-133">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="338e8-134">[クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="338e8-134">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="338e8-135">プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="338e8-135">Plan Guides</span></span>](../../relational-databases/performance/plan-guides.md)  
  
  
