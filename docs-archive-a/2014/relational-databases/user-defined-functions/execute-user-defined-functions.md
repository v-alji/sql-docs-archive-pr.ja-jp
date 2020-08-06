---
title: ユーザー定義関数の実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4446f3b3a132488fdac6e859f30abaca40a193d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646084"
---
# <a name="execute-user-defined-functions"></a><span data-ttu-id="a24c2-102">ユーザー定義関数の実行</span><span class="sxs-lookup"><span data-stu-id="a24c2-102">Execute User-defined Functions</span></span>
  <span data-ttu-id="a24c2-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してユーザー定義関数を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a24c2-103">You can execute a user defined function in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a24c2-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a24c2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a24c2-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a24c2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a24c2-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a24c2-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a24c2-107">Security</span><span class="sxs-lookup"><span data-stu-id="a24c2-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a24c2-108">**ユーザー定義関数を実行するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="a24c2-108">**To execute a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="a24c2-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a24c2-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a24c2-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="a24c2-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a24c2-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a24c2-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a24c2-112">Transact-SQL では、 *値* を使用するか、@*parameter_name*=*値.* を使用し、パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a24c2-112">In Transact-SQL, parameters can be supplied either by using *value* or by using @*parameter_name*=*value.*</span></span> <span data-ttu-id="a24c2-113">パラメーターは、トランザクションの一部ではないです。そのため、トランザクションが後でロールバックの値にパラメーターが変更された場合、パラメーター戻すことはできません前の値にします。</span><span class="sxs-lookup"><span data-stu-id="a24c2-113">A parameter is not part of a transaction; therefore, if a parameter is changed in a transaction that is later rolled back, the value of the parameter does not revert to its previous value.</span></span> <span data-ttu-id="a24c2-114">呼び出し元に返される値は常に、モジュールから戻る時点での値になります。</span><span class="sxs-lookup"><span data-stu-id="a24c2-114">The value returned to the caller is always the value at the time the module returns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a24c2-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a24c2-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a24c2-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="a24c2-116">Permissions</span></span>  
 <span data-ttu-id="a24c2-117">EXECUTE ステートメントの実行に権限は必要ありませんが、</span><span class="sxs-lookup"><span data-stu-id="a24c2-117">Permissions are not required to run the EXECUTE statement.</span></span> <span data-ttu-id="a24c2-118">EXECUTE 文字列内で参照されるセキュリティ保護可能なリソースに対しては権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a24c2-118">However, permissions are required on the securables that are referenced within the EXECUTE string.</span></span> <span data-ttu-id="a24c2-119">たとえば、この文字列に INSERT ステートメントが含まれている場合、EXECUTE ステートメントの呼び出し元は対象のテーブルに対する INSERT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a24c2-119">For example, if the string contains an INSERT statement, the caller of the EXECUTE statement must have INSERT permission on the target table.</span></span> <span data-ttu-id="a24c2-120">EXECUTE ステートメントは、モジュール内に含まれている場合でも、検出されるたびに権限が確認されます。</span><span class="sxs-lookup"><span data-stu-id="a24c2-120">Permissions are checked at the time EXECUTE statement is encountered, even if the EXECUTE statement is included within a module.</span></span> <span data-ttu-id="a24c2-121">詳細については、「 [EXECUTE &#40;transact-sql&#41;](/sql/t-sql/language-elements/execute-transact-sql) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a24c2-121">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a24c2-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a24c2-122">Using Transact-SQL</span></span>  
  
#### <a name="to-execute-a-user-defined-function"></a><span data-ttu-id="a24c2-123">ユーザー定義関数を実行するには</span><span class="sxs-lookup"><span data-stu-id="a24c2-123">To execute a user-defined function</span></span>  
  
1.  <span data-ttu-id="a24c2-124">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a24c2-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a24c2-125">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a24c2-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a24c2-126">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a24c2-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 <span data-ttu-id="a24c2-127">詳細については、「 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a24c2-127">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
  
