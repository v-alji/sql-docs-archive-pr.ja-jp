---
title: 新しいプラン ガイドの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.designer.newplanguide.f1
helpviewer_keywords:
- creating plan guides
- plan guides [SQL Server]. creating
ms.assetid: e1ad78bb-4857-40ea-a0c6-dcf5c28aef2f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60ba31e2a63575a316db5befb397bea59c0ad1e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645578"
---
# <a name="create-a-new-plan-guide"></a><span data-ttu-id="001d2-102">新しいプラン ガイドの作成</span><span class="sxs-lookup"><span data-stu-id="001d2-102">Create a New Plan Guide</span></span>
  <span data-ttu-id="001d2-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してプラン ガイドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="001d2-103">You can create a plan guide in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="001d2-104">プラン ガイドは、クエリ ヒントまたは固定クエリ プランをクエリにアタッチすることにより、クエリの最適化を促します。</span><span class="sxs-lookup"><span data-stu-id="001d2-104">Plan guides influence query optimization by attaching query hints or a fixed query plan to them.</span></span> <span data-ttu-id="001d2-105">プラン ガイドでは、最適化する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントと、使用するクエリ ヒントを含む OPTION 句またはクエリの最適化に使用する特定のクエリ プランのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="001d2-105">In the plan guide, you specify the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that you want optimized and either an OPTION clause that contains the query hints you want to use or a specific query plan you want to use to optimize the query.</span></span> <span data-ttu-id="001d2-106">クエリが実行されると、クエリ オプティマイザーにより [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがプラン ガイドと照合され、実行時にクエリに OPTION 句がアタッチされるか、指定されたクエリ プランが使用されます。</span><span class="sxs-lookup"><span data-stu-id="001d2-106">When the query executes, the query optimizer matches the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide and either attaches the OPTION clause to the query at run time or uses the specified query plan.</span></span>  
  
 <span data-ttu-id="001d2-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="001d2-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="001d2-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="001d2-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="001d2-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="001d2-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="001d2-110">Security</span><span class="sxs-lookup"><span data-stu-id="001d2-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="001d2-111">**以下を使用してプラン ガイドを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="001d2-111">**To create a plan guide, using:**</span></span>  
  
     [<span data-ttu-id="001d2-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="001d2-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="001d2-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="001d2-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="001d2-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="001d2-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="001d2-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="001d2-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="001d2-116">sp_create_plan_guide の引数は、表示される順序で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="001d2-116">The arguments to sp_create_plan_guide must be provided in the order that is shown.</span></span> <span data-ttu-id="001d2-117">`sp_create_plan_guide` のパラメーターに値を指定する場合、パラメーター名はすべて明示的に指定するか、すべて指定しないかのいずれかにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="001d2-117">When you supply values for the parameters of `sp_create_plan_guide`, all parameter names must be specified explicitly, or none at all.</span></span> <span data-ttu-id="001d2-118">たとえば、`@name =` を指定する場合は、`@stmt =`、`@type =` なども指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="001d2-118">For example, if `@name =` is specified, then `@stmt =` , `@type =`, and so on, must also be specified.</span></span> <span data-ttu-id="001d2-119">同様に、`@name =` を省略してパラメーター値だけを指定する場合は、その他のパラメーター名も省略し、値だけを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="001d2-119">Likewise, if `@name =` is omitted and only the parameter value is provided, the remaining parameter names must also be omitted, and only their values provided.</span></span> <span data-ttu-id="001d2-120">引数の名前は、構文を理解しやすくするための説明目的のものです。</span><span class="sxs-lookup"><span data-stu-id="001d2-120">Argument names are for descriptive purposes only, to help understand the syntax.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="001d2-121">では、指定したパラメーター名と、その名前が使用されている位置にあるパラメーターの名前が一致しているかどうかは確認されません。</span><span class="sxs-lookup"><span data-stu-id="001d2-121">does not verify that the specified parameter name matches the name for the parameter in the position where the name is used.</span></span>  
  
-   <span data-ttu-id="001d2-122">同一のクエリとバッチまたはモジュールに対し、複数の OBJECT または SQL プラン ガイドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="001d2-122">You can create more than one OBJECT or SQL plan guide for the same query and batch or module.</span></span> <span data-ttu-id="001d2-123">ただし、有効にできるプラン ガイドは常に 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="001d2-123">However, only one plan guide can be enabled at any given time.</span></span>  
  
-   <span data-ttu-id="001d2-124">@module_or_batch 値で参照するストアド プロシージャ、関数、または DML トリガーが、WITH ENCRYPTION 句を指定するものであるか一時的なものである場合、この値に対して OBJECT 型のプラン ガイドは作成できません。</span><span class="sxs-lookup"><span data-stu-id="001d2-124">Plan guides of type OBJECT cannot be created for an @module_or_batch value that references a stored procedure, function, or DML trigger that specifies the WITH ENCRYPTION clause or that is temporary.</span></span>  
  
-   <span data-ttu-id="001d2-125">有効、無効にする場合のどちらでも、そのプラン ガイドで参照されている関数、ストアド プロシージャ、または DML トリガーを削除または変更しようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="001d2-125">Trying to drop or modify a function, stored procedure, or DML trigger that is referenced by a plan guide, either enabled or disabled, causes an error.</span></span> <span data-ttu-id="001d2-126">プラン ガイドで参照され、トリガーが定義されているテーブルを削除しようとする場合もエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="001d2-126">Trying to drop a table that has a trigger defined on it that is referenced by a plan guide also causes an error.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="001d2-127">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="001d2-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="001d2-128">Permissions</span><span class="sxs-lookup"><span data-stu-id="001d2-128">Permissions</span></span>  
 <span data-ttu-id="001d2-129">OBJECT 型のプラン ガイドを作成するには、参照先オブジェクトに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="001d2-129">To create a plan guide of type OBJECT, requires ALTER permission on the referenced object.</span></span> <span data-ttu-id="001d2-130">SQL または TEMPLATE タイプのプラン ガイドを作成するには、現在のデータベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="001d2-130">To create a plan guide of type SQL or TEMPLATE, requires ALTER permission on the current database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="001d2-131">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="001d2-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-plan-guide"></a><span data-ttu-id="001d2-132">プラン ガイドを作成するには</span><span class="sxs-lookup"><span data-stu-id="001d2-132">To create a plan guide</span></span>  
  
1.  <span data-ttu-id="001d2-133">プラス記号をクリックして、作成するプラン ガイドのあるデータベースを展開し、プラス記号をクリックして **[プログラミング]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="001d2-133">Click the plus sign to expand the database in which you want to create a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="001d2-134">[**プランガイド**] フォルダーを右クリックし、[**新しいプランガイド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="001d2-134">Right-click the **Plan Guides** folder and select **New Plan Guide...**.</span></span>  
  
3.  <span data-ttu-id="001d2-135">**[新しいプラン ガイド]** ダイアログ ボックスの **[名前]** ボックスに、プラン ガイドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="001d2-135">In the **New Plan Guide** dialog box, in the **Name** box, enter the name of the plan guide.</span></span>  
  
4.  <span data-ttu-id="001d2-136">**[ステートメント]** ボックスに、プラン ガイドの適用対象の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="001d2-136">In the **Statement** box, enter the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement against which the plan guide is to be applied.</span></span>  
  
5.  <span data-ttu-id="001d2-137">**[スコープの種類]** ボックスの一覧で、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが存在するエンティティの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="001d2-137">In the **Scope type** list, select the type of entity in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="001d2-138">これは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントとプラン ガイドを照合するコンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="001d2-138">This specifies the context for matching the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide.</span></span> <span data-ttu-id="001d2-139">選択できる値は、 **OBJECT**、 **SQL**、および **TEMPLATE**です。</span><span class="sxs-lookup"><span data-stu-id="001d2-139">Possible values are **OBJECT**, **SQL**, and **TEMPLATE**.</span></span>  
  
6.  <span data-ttu-id="001d2-140">**[スコープのバッチ]** ボックスに、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを含むバッチ テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="001d2-140">In the **Scope batch** box, enter the batch text in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="001d2-141">バッチ テキストには、USE\`\`*database* ステートメントを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="001d2-141">The batch text cannot include a USE\`\`*database* statement.</span></span> <span data-ttu-id="001d2-142">**[スコープのバッチ]** ボックスは、スコープの種類として **[SQL]** を選択した場合にのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="001d2-142">The **Scope batch** box is only available when **SQL** is selected as a scope type.</span></span> <span data-ttu-id="001d2-143">スコープの種類が SQL であるとき、[スコープのバッチ] ボックスに何も入力しなかった場合、バッチ テキストの値は、 **[ステートメント]** ボックスと同じ値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="001d2-143">If nothing is entered in the scope batch box when SQL is the scope type, then the value of the batch text is set to the same value as is in the **Statement** box.</span></span>  
  
7.  <span data-ttu-id="001d2-144">**[スコープのスキーマ名]** ボックスに、対象のオブジェクトを含んでいるスキーマの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="001d2-144">In the **Scope schema name** list, enter the name of the schema in which the object is contained.</span></span> <span data-ttu-id="001d2-145">**[スコープのスキーマ名]** ボックスは、スコープの種類として **[オブジェクト]** を選択した場合にのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="001d2-145">The **Scope schema name** box is only available when **Object** is selected as a scope type.</span></span>  
  
8.  <span data-ttu-id="001d2-146">**[スコープのオブジェクト名]** ボックスに、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを含む [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ、ユーザー定義スカラー関数、複数ステートメントのテーブル値関数、または DML トリガーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="001d2-146">In the **Scope object name** box, enter the name of the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, user-defined scalar function, multistatement table-valued function, or DML trigger in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="001d2-147">**[スコープのオブジェクト名]** ボックスは、スコープの種類として **[オブジェクト]** を選択した場合にのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="001d2-147">The **Scope object name** box is only available when **Object** is selected as a scope type.</span></span>  
  
9. <span data-ttu-id="001d2-148">**ステートメントに埋め込まれているすべてのパラメーターの名前とデータ型を** [パラメーター] [!INCLUDE[tsql](../../includes/tsql-md.md)] ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="001d2-148">In the **Parameters** box, enter the parameter name and data type of all parameters that are embedded in the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
     <span data-ttu-id="001d2-149">パラメーターは、次の条件のいずれかを満たす場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="001d2-149">Parameters apply only when either of the following is true:</span></span>  
  
    -   <span data-ttu-id="001d2-150">スコープの種類が **SQL** または **TEMPLATE**の場合。</span><span class="sxs-lookup"><span data-stu-id="001d2-150">The scope type is **SQL** or **TEMPLATE**.</span></span> <span data-ttu-id="001d2-151">**TEMPLATE**の場合、パラメーターを NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="001d2-151">If **TEMPLATE**, parameters must not be NULL.</span></span>  
  
    -   <span data-ttu-id="001d2-152">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが sp_executesql を使用して送信され、パラメーターの値が指定されている場合、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が内部でステートメントをパラメーター化した後に送信する場合。</span><span class="sxs-lookup"><span data-stu-id="001d2-152">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is submitted by using sp_executesql and a value for the parameter is specified, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internally submits a statement after parameterizing it.</span></span>  
  
10. <span data-ttu-id="001d2-153">**ステートメントに適用されるクエリ ヒントまたはクエリ プランを** [ヒント] [!INCLUDE[tsql](../../includes/tsql-md.md)] ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="001d2-153">In the **Hints** box, enter the query hints or query plan to be applied to the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="001d2-154">1 つまたは複数のクエリ ヒントを指定するには、有効な OPTION 句を入力します。</span><span class="sxs-lookup"><span data-stu-id="001d2-154">To specify one or more query hints, enter a valid OPTION clause.</span></span>  
  
11. <span data-ttu-id="001d2-155">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="001d2-155">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="001d2-156">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="001d2-156">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-plan-guide"></a><span data-ttu-id="001d2-157">プラン ガイドを作成するには</span><span class="sxs-lookup"><span data-stu-id="001d2-157">To create a plan guide</span></span>  
  
1.  <span data-ttu-id="001d2-158">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="001d2-158">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="001d2-159">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="001d2-159">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="001d2-160">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="001d2-160">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
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
  
    ```  
  
 <span data-ttu-id="001d2-161">詳細については、「[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="001d2-161">For more information, see [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql).</span></span>  
  
  
