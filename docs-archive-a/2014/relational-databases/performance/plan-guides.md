---
title: プラン ガイド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- SQL plan guides
- OPTIMIZE FOR query hint
- RECOMPILE query hint
- OBJECT plan guide
- plan guides [SQL Server], about plan guides
- OPTION clause
- plan guides [SQL Server]
- USE PLAN query hint
ms.assetid: bfc97632-c14c-4768-9dc5-a9c512f6b2bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c97682163313a56acb8521174fa8d4012a69b529
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642749"
---
# <a name="plan-guides"></a><span data-ttu-id="1b091-102">プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="1b091-102">Plan Guides</span></span>
  <span data-ttu-id="1b091-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の実際のクエリのテキストを直接変更することが不可能な場合や望ましくない場合に、プラン ガイドを使用してクエリのパフォーマンスを最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="1b091-103">Plan guides let you optimize the performance of queries when you cannot or do not want to directly change the text of the actual query in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1b091-104">プラン ガイドは、クエリ ヒントまたは固定クエリ プランをクエリにアタッチすることにより、クエリの最適化を促します。</span><span class="sxs-lookup"><span data-stu-id="1b091-104">Plan guides influence the optimization of queries by attaching query hints or a fixed query plan to them.</span></span> <span data-ttu-id="1b091-105">プラン ガイドは、サード パーティ ベンダーが提供するデータベース アプリケーションのクエリの小さなサブセットで、期待どおりのパフォーマンスが得られない場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="1b091-105">Plan guides can be useful when a small subset of queries in a database application provided by a third-party vendor are not performing as expected.</span></span> <span data-ttu-id="1b091-106">プラン ガイドでは、最適化する Transact-SQL ステートメントのほか、使用するクエリ ヒントを含む OPTION 句またはクエリの最適化に使用する特定のクエリ プランのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1b091-106">In the plan guide, you specify the Transact-SQL statement that you want optimized and either an OPTION clause that contains the query hints you want to use or a specific query plan you want to use to optimize the query.</span></span> <span data-ttu-id="1b091-107">クエリが実行されると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により Transact-SQL ステートメントがプラン ガイドと照合され、実行時にクエリに OPTION 句がアタッチされるか、指定されたクエリ プランが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-107">When the query executes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] matches the Transact-SQL statement to the plan guide and attaches the OPTION clause to the query at run time or uses the specified query plan.</span></span>  
  
 <span data-ttu-id="1b091-108">作成できるプラン ガイドの総数の上限は、使用可能なシステム リソースによって決まります。</span><span class="sxs-lookup"><span data-stu-id="1b091-108">The total number of plan guides you can create is limited only by available system resources.</span></span> <span data-ttu-id="1b091-109">ただし、プラン ガイドは、ミッションクリティカルなクエリのパフォーマンスの向上と安定化を図る目的にのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b091-109">Nevertheless, plan guides should be limited to mission-critical queries that are targeted for improved or stabilized performance.</span></span> <span data-ttu-id="1b091-110">プラン ガイドの使用により配置済みのアプリケーションのクエリ負荷の多くが影響を受けることがないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="1b091-110">Plan guides should not be used to influence most of the query load of a deployed application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b091-111">プラン ガイドは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1b091-111">Plan guides cannot be used in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1b091-112">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b091-112">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="1b091-113">プラン ガイドはどのエディションでも表示できます。</span><span class="sxs-lookup"><span data-stu-id="1b091-113">Plan guides are visible in any edition.</span></span> <span data-ttu-id="1b091-114">また、プラン ガイドを含むデータベースは、どのエディションに対してもアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="1b091-114">You can also attach a database that contains plan guides to any edition.</span></span> <span data-ttu-id="1b091-115">アップグレード済みのバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にデータベースを復元またはアタッチした場合、プラン ガイドはまったく影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="1b091-115">Plan guides remain intact when you restore or attach a database to an upgraded version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="types-of-plan-guides"></a><span data-ttu-id="1b091-116">プラン ガイドの種類</span><span class="sxs-lookup"><span data-stu-id="1b091-116">Types of Plan Guides</span></span>  
 <span data-ttu-id="1b091-117">次の種類のプラン ガイドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b091-117">The following types of plan guides can be created.</span></span>  
  
 <span data-ttu-id="1b091-118">OBJECT プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="1b091-118">OBJECT plan guide</span></span>  
 <span data-ttu-id="1b091-119">OBJECT プラン ガイドでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ、スカラー ユーザー定義関数、複数ステートメント テーブル値ユーザー定義関数、および DML トリガーのコンテキストで実行されるクエリが照合されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-119">An OBJECT plan guide matches queries that execute in the context of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures, scalar user-defined functions, multi-statement table-valued user-defined functions, and DML triggers.</span></span>  
  
 <span data-ttu-id="1b091-120">`@Country`_`region` パラメーターを受け取る次のストアド プロシージャが、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに対して配置されたデータベース アプリケーションに存在するとします。</span><span class="sxs-lookup"><span data-stu-id="1b091-120">Suppose the following stored procedure, which takes the `@Country`_`region` parameter, is in a database application that is deployed against the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
CREATE PROCEDURE Sales.GetSalesOrderByCountry (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h, Sales.Customer AS c,   
        Sales.SalesTerritory AS t  
    WHERE h.CustomerID = c.CustomerID  
        AND c.TerritoryID = t.TerritoryID  
        AND CountryRegionCode = @Country_region  
END;  
```  
  
 <span data-ttu-id="1b091-121">このストアド プロシージャは `@Country`_`region = N'AU'` (オーストラリア) 用にコンパイルおよび最適化されているものとします。</span><span class="sxs-lookup"><span data-stu-id="1b091-121">Assume that this stored procedure has been compiled and optimized for `@Country`_`region = N'AU'` (Australia).</span></span> <span data-ttu-id="1b091-122">ただし、オーストラリアでは比較的少数の販売注文しか発生していないため、多くの販売注文が発生している国のパラメーター値を使用してクエリを実行するとパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="1b091-122">However, because there are relatively few sales orders that originate from Australia, performance decreases when the query executes using parameter values of countries with more sales orders.</span></span> <span data-ttu-id="1b091-123">販売注文数が最も多いのは米国なので、 `@Country`\_`region = N'US'` 用に生成されたクエリ プランのパフォーマンスは、 `@Country`\_`region` パラメーターにどの値を使用しても低下しません。</span><span class="sxs-lookup"><span data-stu-id="1b091-123">Because the most sales orders originate in the United States, a query plan that is generated for `@Country`\_`region = N'US'` would likely perform better for all possible values of the `@Country`\_`region` parameter.</span></span>  
  
 <span data-ttu-id="1b091-124">ストアド プロシージャを変更して `OPTIMIZE FOR` クエリ ヒントをクエリに追加することで、この問題に対処できます。</span><span class="sxs-lookup"><span data-stu-id="1b091-124">You could address this problem by modifying the stored procedure to add the `OPTIMIZE FOR` query hint to the query.</span></span> <span data-ttu-id="1b091-125">ただし、ストアド プロシージャは配置済みアプリケーション内にあるので、アプリケーション コードを直接変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="1b091-125">However, because the stored procedure is in a deployed application, you cannot directly modify the application code.</span></span> <span data-ttu-id="1b091-126">代わりに、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに次のプラン ガイドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b091-126">Instead, you can create the following plan guide in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT *FROM Sales.SalesOrderHeader AS h,  
        Sales.Customer AS c,  
        Sales.SalesTerritory AS t  
        WHERE h.CustomerID = c.CustomerID   
            AND c.TerritoryID = t.TerritoryID  
            AND CountryRegionCode = @Country_region',  
@type = N'OBJECT',  
@module_or_batch = N'Sales.GetSalesOrderByCountry',  
@params = NULL,  
@hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
 <span data-ttu-id="1b091-127">`sp_create_plan_guide` ステートメントの指定したクエリが実行されると、そのクエリは最適化される前に変更され、 `OPTIMIZE FOR (@Country = N''US'')` 句が含められます。</span><span class="sxs-lookup"><span data-stu-id="1b091-127">When the query specified in the `sp_create_plan_guide` statement executes, the query is modified before optimization to include the `OPTIMIZE FOR (@Country = N''US'')` clause.</span></span>  
  
 <span data-ttu-id="1b091-128">SQL プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="1b091-128">SQL plan guide</span></span>  
 <span data-ttu-id="1b091-129">SQL プラン ガイドでは、データベース オブジェクトの一部ではないスタンドアロン [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントとスタンドアロン バッチのコンテキストで実行されるクエリが照合されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-129">An SQL plan guide matches queries that execute in the context of stand-alone [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and batches that are not part of a database object.</span></span> <span data-ttu-id="1b091-130">また、SQL ベースのプラン ガイドを使用して、指定した形式にパラメーター化されたクエリを照合することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b091-130">SQL-based plan guides can also be used to match queries that parameterize to a specified form.</span></span> <span data-ttu-id="1b091-131">SQL プラン ガイドは、スタンドアロン [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントとスタンドアロン バッチに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-131">SQL plan guides apply to stand-alone [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and batches.</span></span> <span data-ttu-id="1b091-132">これらのステートメントは、よく [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) システム ストアド プロシージャを使用してアプリケーションから送信されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-132">Frequently, these statements are submitted by an application by using the [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) system stored procedure.</span></span> <span data-ttu-id="1b091-133">たとえば、次のスタンドアロン バッチについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="1b091-133">For example, consider the following stand-alone batch:</span></span>  
  
```  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 <span data-ttu-id="1b091-134">このクエリに並列実行プランが生成されないようにするには、次のプラン ガイドを作成し、 `MAXDOP` パラメーターで `1` クエリ ヒントを `@hints` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1b091-134">To prevent a parallel execution plan from being generated on this query, create the following plan guide and set the `MAXDOP` query hint to `1` in the `@hints` parameter.</span></span>  
  
```  
sp_create_plan_guide   
@name = N'Guide2',   
@stmt = N'SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC',  
@type = N'SQL',  
@module_or_batch = NULL,   
@params = NULL,   
@hints = N'OPTION (MAXDOP 1)';  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1b091-135">`@module_or_batch` ステートメントの `@params` 引数と `sp_create_plan guide` 引数に指定する値は、実際のクエリで送信される、対応するテキストと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b091-135">The values that are supplied for the `@module_or_batch` and `@params` arguments of the `sp_create_plan guide` statement must match the corresponding text submitted in the actual query.</span></span> <span data-ttu-id="1b091-136">詳細については、「 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) ステートメントの [SQL Server Profiler を使用したプラン ガイドの作成とテスト](plan-guides.md)の実際のクエリのテキストを直接変更することが不可能な場合や望ましくない場合に、プラン ガイドを使用してクエリのパフォーマンスを最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="1b091-136">For more information, see [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) and [Use SQL Server Profiler to Create and Test Plan Guides](plan-guides.md).</span></span>  
  
 <span data-ttu-id="1b091-137">PARAMETERIZATION データベース オプションを FORCED に設定するか、またはクエリのクラスをパラメーター化するように指定して TEMPLATE プラン ガイドを作成すると、同じ形式にパラメーター化されるクエリに SQL プラン ガイドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b091-137">SQL plan guides can also be created on queries that parameterize to the same form when the PARAMETERIZATION database option is SET to FORCED, or when a TEMPLATE plan guide is created specifying that a parameterized class of queries.</span></span>  
  
 <span data-ttu-id="1b091-138">TEMPLATE プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="1b091-138">TEMPLATE plan guide</span></span>  
 <span data-ttu-id="1b091-139">TEMPLATE プラン ガイドでは、指定した形式にパラメーター化されたスタンドアロン クエリが照合されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-139">A TEMPLATE plan guide matches stand-alone queries that parameterize to a specified form.</span></span> <span data-ttu-id="1b091-140">これらのプラン ガイドは、クエリのクラスのデータベースの現在の PARAMETERIZATION データベース SET オプションをオーバーライドするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-140">These plan guides are used to override the current PARAMETERIZATION database SET option of a database for a class of queries.</span></span>  
  
 <span data-ttu-id="1b091-141">TEMPLATE プラン ガイドは、次のいずれかの状況で作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b091-141">You can create a TEMPLATE plan guide in either of the following situations:</span></span>  
  
-   <span data-ttu-id="1b091-142">PARAMETERIZATION データベース オプションを FORCED に設定したが、簡易パラメーター化のルールに従ってコンパイルするクエリがある場合。</span><span class="sxs-lookup"><span data-stu-id="1b091-142">The PARAMETERIZATION database option is SET to FORCED, but there are queries you want compiled according to the rules of simple parameterization.</span></span>  
  
-   <span data-ttu-id="1b091-143">PARAMETERIZATION データベース オプションを SIMPLE (既定値) に設定したが、特定のクラスのクエリについて強制パラメーター化が必要である場合。</span><span class="sxs-lookup"><span data-stu-id="1b091-143">The PARAMETERIZATION database option is SET to SIMPLE (the default setting), but you want forced parameterization to be tried on a class of queries.</span></span>  
  
## <a name="plan-guide-matching-requirements"></a><span data-ttu-id="1b091-144">プラン ガイドの照合要件</span><span class="sxs-lookup"><span data-stu-id="1b091-144">Plan Guide Matching Requirements</span></span>  
 <span data-ttu-id="1b091-145">プラン ガイドの範囲は、そのガイドが作成されているデータベースです。</span><span class="sxs-lookup"><span data-stu-id="1b091-145">Plan guides are scoped to the database in which they are created.</span></span> <span data-ttu-id="1b091-146">したがって、クエリの実行時に使用されているデータベース内に存在するプラン ガイドだけをクエリと照合できます。</span><span class="sxs-lookup"><span data-stu-id="1b091-146">Therefore, only plan guides that are in the database that is current when a query executes can be matched to the query.</span></span> <span data-ttu-id="1b091-147">たとえば、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] が現在のデータベースの場合に次のクエリを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="1b091-147">For example, if [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] is the current database and the following query executes:</span></span>  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 <span data-ttu-id="1b091-148">この場合、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内のプラン ガイドだけがこのクエリと照合されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-148">Only plan guides in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database are eligible to be matched to this query.</span></span> <span data-ttu-id="1b091-149">ただし、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] が現在のデータベースの場合に、次のステートメントを実行すると結果が異なります。</span><span class="sxs-lookup"><span data-stu-id="1b091-149">However, if [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] is the current database and the following statements are run:</span></span>  
  
 `USE DB1;`  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 <span data-ttu-id="1b091-150">この場合、 `DB1` のコンテキストでこのクエリが実行されているので、 `DB1`内のプラン ガイドがこのクエリと照合されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-150">Only plan guides in `DB1` are eligible to be matched to the query because the query is executing in the context of `DB1`.</span></span>  
  
 <span data-ttu-id="1b091-151">SQL ベースのプラン ガイドまたは TEMPLATE ベースのプラン ガイドでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、引数 @module_or_batch と引数 @params の値が文字単位で比較されてクエリと照合されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-151">For SQL- or TEMPLATE-based plan guides, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] matches the values for the @module_or_batch and @params arguments to a query by comparing the two values character by character.</span></span> <span data-ttu-id="1b091-152">つまり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で受け取られる実際のバッチ テキストと厳密に同じテキストを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b091-152">This means you must provide the text exactly as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] receives it in the actual batch.</span></span>  
  
 <span data-ttu-id="1b091-153">@type = 'SQL' で、@module_or_batch が NULL に設定されている場合、@module_or_batch の値は @stmt の値に設定されます。つまり、 *statement_text* の値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に送信するときと同一の形式で、同じ文字で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b091-153">When @type = 'SQL' and @module_or_batch is set to NULL, the value of @module_or_batch is set to the value of @stmt. This means that the value for *statement_text* must be provided in the identical format, character-for-character, as it is submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1b091-154">この適合を容易にするために内部変換は実行されません。</span><span class="sxs-lookup"><span data-stu-id="1b091-154">No internal conversion is performed to facilitate this match.</span></span>  
  
 <span data-ttu-id="1b091-155">通常の (SQL または OBJECT) プラン ガイドと TEMPLATE プラン ガイドの両方をステートメントに適用可能な場合、通常のプラン ガイドのみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-155">When both a regular (SQL or OBJECT) plan guide and a TEMPLATE plan guide can apply to a statement, only the regular plan guide will be used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b091-156">プラン ガイドの作成対象のステートメントを含むバッチには、USE *database* ステートメントを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="1b091-156">The batch that contains the statement on which you want to create a plan guide cannot contain a USE *database* statement.</span></span>  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a><span data-ttu-id="1b091-157">プラン キャッシュに対するプラン ガイドの効果</span><span class="sxs-lookup"><span data-stu-id="1b091-157">Plan Guide Effect on the Plan Cache</span></span>  
 <span data-ttu-id="1b091-158">モジュールにプラン ガイドを作成すると、そのモジュールのクエリ プランがプラン キャッシュから削除されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-158">Creating a plan guide on a module removes the query plan for that module from the plan cache.</span></span> <span data-ttu-id="1b091-159">バッチに OBJECT 型または SQL 型のプラン ガイドを作成すると、同じハッシュ値を持つバッチのクエリ プランが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-159">Creating a plan guide of type OBJECT or SQL on a batch removes the query plan for a batch that has the same hash value.</span></span> <span data-ttu-id="1b091-160">TEMPLATE 型のプラン ガイドを作成すると、単一ステートメントのバッチがデータベース内のプラン キャッシュからすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="1b091-160">Creating a plan guide of type TEMPLATE removes all single-statement batches from the plan cache within that database.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1b091-161">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1b091-161">Related Tasks</span></span>  
  
|<span data-ttu-id="1b091-162">タスク</span><span class="sxs-lookup"><span data-stu-id="1b091-162">Task</span></span>|<span data-ttu-id="1b091-163">トピック</span><span class="sxs-lookup"><span data-stu-id="1b091-163">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="1b091-164">プラン ガイドを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b091-164">Describes how to create a plan guide.</span></span>|[<span data-ttu-id="1b091-165">新しいプラン ガイドの作成</span><span class="sxs-lookup"><span data-stu-id="1b091-165">Create a New Plan Guide</span></span>](create-a-new-plan-guide.md)|  
|<span data-ttu-id="1b091-166">パラメーター化クエリ用のプラン ガイドを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b091-166">Describes how to create a plan guide for parameterized queries.</span></span>|[<span data-ttu-id="1b091-167">パラメーター化クエリのプラン ガイドの作成</span><span class="sxs-lookup"><span data-stu-id="1b091-167">Create a Plan Guide for Parameterized Queries</span></span>](create-a-plan-guide-for-parameterized-queries.md)|  
|<span data-ttu-id="1b091-168">プラン ガイドを使用してクエリのパラメーター化動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b091-168">Describes how to control query parameterization behavior by using plan guides.</span></span>|[<span data-ttu-id="1b091-169">プラン ガイドを使用したクエリのパラメーター化動作の指定</span><span class="sxs-lookup"><span data-stu-id="1b091-169">Specify Query Parameterization Behavior by Using Plan Guides</span></span>](specify-query-parameterization-behavior-by-using-plan-guides.md)|  
|<span data-ttu-id="1b091-170">プラン ガイドに固定クエリ プランを含める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b091-170">Describes how to include a fixed query plan in a plan guide.</span></span>|[<span data-ttu-id="1b091-171">プラン ガイドへの固定クエリ プランの適用</span><span class="sxs-lookup"><span data-stu-id="1b091-171">Apply a Fixed Query Plan to a Plan Guide</span></span>](apply-a-fixed-query-plan-to-a-plan-guide.md)|  
|<span data-ttu-id="1b091-172">プラン ガイドにクエリ ヒントを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b091-172">Describes how to specify query hints in a plan guide.</span></span>|[<span data-ttu-id="1b091-173">プラン ガイドへのクエリ ヒントのアタッチ</span><span class="sxs-lookup"><span data-stu-id="1b091-173">Attach Query Hints to a Plan Guide</span></span>](attach-query-hints-to-a-plan-guide.md)|  
|<span data-ttu-id="1b091-174">プラン ガイドのプロパティを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b091-174">Describes how to view plan guide properties.</span></span>|[<span data-ttu-id="1b091-175">プラン ガイド プロパティの表示</span><span class="sxs-lookup"><span data-stu-id="1b091-175">View Plan Guide Properties</span></span>](view-plan-guide-properties.md)|  
|<span data-ttu-id="1b091-176">プラン ガイドを作成およびテストするために SQL Server Profiler を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b091-176">Describes how to use SQL Server Profiler to create and test plan guides.</span></span>|[<span data-ttu-id="1b091-177">SQL Server Profiler を使用したプラン ガイドの作成とテスト</span><span class="sxs-lookup"><span data-stu-id="1b091-177">Use SQL Server Profiler to Create and Test Plan Guides</span></span>](plan-guides.md)|  
|<span data-ttu-id="1b091-178">プラン ガイドを検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b091-178">Describes how to validate plan guides.</span></span>|[<span data-ttu-id="1b091-179">アップグレード後のプラン ガイドの検証</span><span class="sxs-lookup"><span data-stu-id="1b091-179">Validate Plan Guides After Upgrade</span></span>](validate-plan-guides-after-upgrade.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1b091-180">参照</span><span class="sxs-lookup"><span data-stu-id="1b091-180">See Also</span></span>  
 <span data-ttu-id="1b091-181">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b091-181">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="1b091-182">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b091-182">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span></span>  
 <span data-ttu-id="1b091-183">[sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b091-183">[sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="1b091-184">[sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b091-184">[sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql) </span></span>  
 [<span data-ttu-id="1b091-185">sys.fn_validate_plan_guide &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1b091-185">sys.fn_validate_plan_guide &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql)  
  
  
