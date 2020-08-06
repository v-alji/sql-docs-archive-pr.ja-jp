---
title: プラン ガイド プロパティの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.planguideprop.general.f1
helpviewer_keywords:
- plan guides [SQL Server], view plan guide properties
- viewing plan guide properties
ms.assetid: 8c0d2f39-59c1-4168-a649-65473f6a771b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af29c66690a43f89106c1f77aca8c3a02eff2ba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715230"
---
# <a name="view-plan-guide-properties"></a><span data-ttu-id="ffaff-102">プラン ガイド プロパティの表示</span><span class="sxs-lookup"><span data-stu-id="ffaff-102">View Plan Guide Properties</span></span>
  <span data-ttu-id="ffaff-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のプラン ガイドのプロパティは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または  を使用して表示できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffaff-103">You can view the properties of plan guides in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="ffaff-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ffaff-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ffaff-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ffaff-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ffaff-106">Security</span><span class="sxs-lookup"><span data-stu-id="ffaff-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ffaff-107">**以下を使用してプラン ガイドのプロパティを表示するには:**</span><span class="sxs-lookup"><span data-stu-id="ffaff-107">**To view the properties of plan guides, using:**</span></span>  
  
     [<span data-ttu-id="ffaff-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ffaff-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ffaff-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ffaff-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ffaff-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="ffaff-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ffaff-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ffaff-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ffaff-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="ffaff-112">Permissions</span></span>  
 <span data-ttu-id="ffaff-113">カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-113">The visibility of the metadata in catalog views is limited to securables that either a user owns or on which the user has been granted some permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ffaff-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ffaff-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-a-plan-guide"></a><span data-ttu-id="ffaff-115">プラン ガイドのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="ffaff-115">To view the properties of a plan guide</span></span>  
  
1.  <span data-ttu-id="ffaff-116">プラス記号をクリックして、プロパティを表示するプラン ガイドのあるデータベースを展開し、プラス記号をクリックして **[プログラミング]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ffaff-116">Click the plus sign to expand the database in which you want to view the properties of a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="ffaff-117">プラス記号をクリックして **[プラン ガイド]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ffaff-117">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="ffaff-118">プロパティを表示するプラン ガイドを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffaff-118">Right-click the plan guide of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="ffaff-119">**[プラン ガイドのプロパティ]** ダイアログ ボックスに次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-119">The following properties show in the **Plan Guide Properties** dialog box.</span></span>  
  
     <span data-ttu-id="ffaff-120">**[ヒント]**</span><span class="sxs-lookup"><span data-stu-id="ffaff-120">**Hints**</span></span>  
     <span data-ttu-id="ffaff-121">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに適用されるクエリ ヒントまたはクエリ プランが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-121">Displays the query hints or query plan to be applied to the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="ffaff-122">クエリ プランがヒントとして指定されている場合は、そのプランの XML プラン表示出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-122">When a query plan is specified as a hint, the XML Showplan output for the plan is displayed.</span></span>  
  
     <span data-ttu-id="ffaff-123">**[無効化]**</span><span class="sxs-lookup"><span data-stu-id="ffaff-123">**Is disabled**</span></span>  
     <span data-ttu-id="ffaff-124">プラン ガイドの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-124">Displays the status of the plan guide.</span></span> <span data-ttu-id="ffaff-125">指定できる値は、 **[True]** および **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="ffaff-125">Possible values are **True** and **False**.</span></span>  
  
     <span data-ttu-id="ffaff-126">**名前**</span><span class="sxs-lookup"><span data-stu-id="ffaff-126">**Name**</span></span>  
     <span data-ttu-id="ffaff-127">プラン ガイドの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-127">Displays the name of the plan guide.</span></span>  
  
     <span data-ttu-id="ffaff-128">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="ffaff-128">**Parameters**</span></span>  
     <span data-ttu-id="ffaff-129">スコープの種類が SQL または TEMPLATE の場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに埋め込まれているすべてのパラメーターの名前とデータ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-129">When the scope type is SQL or TEMPLATE, displays the name and data type of all parameters that are embedded in the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
     <span data-ttu-id="ffaff-130">**[スコープ バッチ]**</span><span class="sxs-lookup"><span data-stu-id="ffaff-130">**Scope batch**</span></span>  
     <span data-ttu-id="ffaff-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを含むバッチ テキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-131">Displays the batch text in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span>  
  
     <span data-ttu-id="ffaff-132">**[スコープ オブジェクト名]**</span><span class="sxs-lookup"><span data-stu-id="ffaff-132">**Scope object name**</span></span>  
     <span data-ttu-id="ffaff-133">スコープの種類が OBJECT の場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを含む [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ、ユーザー定義スカラー関数、複数ステートメントのテーブル値関数、または DML トリガーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-133">When the scope type is OBJECT, displays the name of the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, user-defined scalar function, multistatement table-valued function, or DML trigger in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span>  
  
     <span data-ttu-id="ffaff-134">**[スコープ スキーマ名]**</span><span class="sxs-lookup"><span data-stu-id="ffaff-134">**Scope schema name**</span></span>  
     <span data-ttu-id="ffaff-135">スコープの種類が OBJECT の場合は、そのオブジェクトを含むスキーマの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-135">When the scope type is OBJECT, displays the name of the schema in which the object is contained.</span></span>  
  
     <span data-ttu-id="ffaff-136">**[スコープの種類]**</span><span class="sxs-lookup"><span data-stu-id="ffaff-136">**Scope type**</span></span>  
     <span data-ttu-id="ffaff-137">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを含むエンティティの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-137">Displays the type of entity in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="ffaff-138">これは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントとプラン ガイドを照合するコンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="ffaff-138">This specifies the context for matching the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide.</span></span> <span data-ttu-id="ffaff-139">選択できる値は、 **OBJECT**、 **SQL**、および **TEMPLATE**です。</span><span class="sxs-lookup"><span data-stu-id="ffaff-139">Possible values are **OBJECT**, **SQL**, and **TEMPLATE**.</span></span>  
  
     <span data-ttu-id="ffaff-140">**ステートメント**</span><span class="sxs-lookup"><span data-stu-id="ffaff-140">**Statement**</span></span>  
     <span data-ttu-id="ffaff-141">プラン ガイドの適用対象の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffaff-141">Displays the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement against which the plan guide is applied.</span></span>  
  
4.  <span data-ttu-id="ffaff-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffaff-142">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ffaff-143">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ffaff-143">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-properties-of-a-plan-guide"></a><span data-ttu-id="ffaff-144">プラン ガイドのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="ffaff-144">To view the properties of a plan guide</span></span>  
  
1.  <span data-ttu-id="ffaff-145">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ffaff-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ffaff-146">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffaff-146">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ffaff-147">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffaff-147">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- If a plan guide named "Guide1" already exists in the AdventureWorks2012 database, delete it.  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID(N'Guide1') IS NOT NULL  
       EXEC sp_control_plan_guide N'DROP', N'Guide1';  
    GO  
    -- creates a plan guide named Guide1 based on a SQL statement  
    EXEC sp_create_plan_guide   
        @name = N'Guide1',   
        @stmt = N'SELECT TOP 1 *   
                  FROM Sales.SalesOrderHeader   
                  ORDER BY OrderDate DESC',   
        @type = N'SQL',  
        @module_or_batch = NULL,   
        @params = NULL,   
        @hints = N'OPTION (MAXDOP 1)';  
    GO  
    -- Gets the name, created date, and all other relevant property information on the plan guide created above.   
    SELECT name AS plan_guide_name,  
       create_date,  
       query_text,  
       scope_type_desc,  
       OBJECT_NAME(scope_object_id) AS scope_object_name,  
       scope_batch,  
       parameters,  
       hints,  
       is_disabled  
    FROM sys.plan_guides  
    WHERE name = N'Guide1';  
    GO  
    ```  
  
 <span data-ttu-id="ffaff-148">詳細については、「[sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffaff-148">For more information, see [sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql).</span></span>  
  
  
