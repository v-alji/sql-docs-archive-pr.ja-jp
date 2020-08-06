---
title: MSSQLSERVER_137 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e0142cd53006609e9274972e4f5964132f5982c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643928"
---
# <a name="mssqlserver_137"></a><span data-ttu-id="eb261-102">MSSQLSERVER_137</span><span class="sxs-lookup"><span data-stu-id="eb261-102">MSSQLSERVER_137</span></span>
    
## <a name="details"></a><span data-ttu-id="eb261-103">詳細</span><span class="sxs-lookup"><span data-stu-id="eb261-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eb261-104">製品名</span><span class="sxs-lookup"><span data-stu-id="eb261-104">Product Name</span></span>|<span data-ttu-id="eb261-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="eb261-105">SQL Server</span></span>|  
|<span data-ttu-id="eb261-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="eb261-106">Event ID</span></span>|<span data-ttu-id="eb261-107">137</span><span class="sxs-lookup"><span data-stu-id="eb261-107">137</span></span>|  
|<span data-ttu-id="eb261-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="eb261-108">Event Source</span></span>|<span data-ttu-id="eb261-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="eb261-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="eb261-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="eb261-110">Component</span></span>|<span data-ttu-id="eb261-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="eb261-111">SQLEngine</span></span>|  
|<span data-ttu-id="eb261-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="eb261-112">Symbolic Name</span></span>|<span data-ttu-id="eb261-113">P_SCALAR_VAR_NOTFOUND</span><span class="sxs-lookup"><span data-stu-id="eb261-113">P_SCALAR_VAR_NOTFOUND</span></span>|  
|<span data-ttu-id="eb261-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="eb261-114">Message Text</span></span>|<span data-ttu-id="eb261-115">スカラー変数 "% \* ls" を宣言してください。</span><span class="sxs-lookup"><span data-stu-id="eb261-115">Must declare the scalar variable "%.\*ls".</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eb261-116">説明</span><span class="sxs-lookup"><span data-stu-id="eb261-116">Explanation</span></span>  
 <span data-ttu-id="eb261-117">このエラーは、SQL スクリプトで、変数を宣言する前にその変数を使用しようとした場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="eb261-117">This error occurs when a variable is used in a SQL script without first declaring the variable.</span></span> <span data-ttu-id="eb261-118">次の例で **@mycol** は、が宣言されていないため、SET ステートメントと SELECT ステートメントの両方に対してエラー137が返されます。</span><span class="sxs-lookup"><span data-stu-id="eb261-118">The following example returns error 137 for both the SET and SELECT statements because **@mycol** is not declared.</span></span>  
  
 <span data-ttu-id="eb261-119">SET @mycol = 'ContactName';</span><span class="sxs-lookup"><span data-stu-id="eb261-119">SET @mycol = 'ContactName';</span></span>  
  
 <span data-ttu-id="eb261-120">SELECT @mycol;</span><span class="sxs-lookup"><span data-stu-id="eb261-120">SELECT @mycol;</span></span>  
  
 <span data-ttu-id="eb261-121">このエラーのより複雑な原因の 1 つは、EXECUTE ステートメントの外部で宣言された変数を使用することです。</span><span class="sxs-lookup"><span data-stu-id="eb261-121">One of the more complicated causes of this error includes the use of a variable that is declared outside the EXECUTE statement.</span></span> <span data-ttu-id="eb261-122">たとえば、 **@mycol** select ステートメントで指定された変数は、select ステートメントに対してローカルであるため、EXECUTE ステートメントの外部にあります。</span><span class="sxs-lookup"><span data-stu-id="eb261-122">For example, the variable **@mycol** specified in the SELECT statement is local to the SELECT statement; thus it is outside the EXECUTE statement.</span></span>  
  
 <span data-ttu-id="eb261-123">USE AdventureWorks2012;</span><span class="sxs-lookup"><span data-stu-id="eb261-123">USE AdventureWorks2012;</span></span>  
  
 <span data-ttu-id="eb261-124">GO</span><span class="sxs-lookup"><span data-stu-id="eb261-124">GO</span></span>  
  
 <span data-ttu-id="eb261-125">DECLARE @mycol nvarchar(20);</span><span class="sxs-lookup"><span data-stu-id="eb261-125">DECLARE @mycol nvarchar(20);</span></span>  
  
 <span data-ttu-id="eb261-126">SET @mycol = 'Name';</span><span class="sxs-lookup"><span data-stu-id="eb261-126">SET @mycol = 'Name';</span></span>  
  
 <span data-ttu-id="eb261-127">EXECUTE ('SELECT @mycol FROM Production.Product;');</span><span class="sxs-lookup"><span data-stu-id="eb261-127">EXECUTE ('SELECT @mycol FROM Production.Product;');</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eb261-128">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="eb261-128">User Action</span></span>  
 <span data-ttu-id="eb261-129">SQL スクリプトで使用する変数がスクリプト内の別の場所で事前に宣言されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb261-129">Verify that any variables used in a SQL script are declared before being used elsewhere in the script.</span></span>  
  
 <span data-ttu-id="eb261-130">外部で宣言された EXECUTE ステートメント内の変数を参照しないようにスクリプトを修正します。</span><span class="sxs-lookup"><span data-stu-id="eb261-130">Rewrite the script so that it does not reference variables in the EXECUTE statement that are declared outside of it.</span></span> <span data-ttu-id="eb261-131">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="eb261-131">For example:</span></span>  
  
 <span data-ttu-id="eb261-132">USE AdventureWorks2012;</span><span class="sxs-lookup"><span data-stu-id="eb261-132">USE AdventureWorks2012;</span></span>  
  
 <span data-ttu-id="eb261-133">GO</span><span class="sxs-lookup"><span data-stu-id="eb261-133">GO</span></span>  
  
 <span data-ttu-id="eb261-134">DECLARE @mycol nvarchar(20) ;</span><span class="sxs-lookup"><span data-stu-id="eb261-134">DECLARE @mycol nvarchar(20) ;</span></span>  
  
 <span data-ttu-id="eb261-135">SET @mycol = 'Name';</span><span class="sxs-lookup"><span data-stu-id="eb261-135">SET @mycol = 'Name';</span></span>  
  
 <span data-ttu-id="eb261-136">EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;</span><span class="sxs-lookup"><span data-stu-id="eb261-136">EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb261-137">参照</span><span class="sxs-lookup"><span data-stu-id="eb261-137">See Also</span></span>  
 <span data-ttu-id="eb261-138">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb261-138">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span></span>  
 <span data-ttu-id="eb261-139">[SET ステートメント &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb261-139">[SET Statements &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span></span>  
 [<span data-ttu-id="eb261-140">DECLARE @local_variable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb261-140">DECLARE @local_variable &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
  
