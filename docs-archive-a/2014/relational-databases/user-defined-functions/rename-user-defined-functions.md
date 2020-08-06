---
title: ユーザー定義関数名の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
ms.openlocfilehash: ec923be64cf7819c4018ebda71a472f58b29cf8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646081"
---
# <a name="rename-user-defined-functions"></a><span data-ttu-id="4520c-102">ユーザー定義関数名の変更</span><span class="sxs-lookup"><span data-stu-id="4520c-102">Rename User-defined Functions</span></span>
  <span data-ttu-id="4520c-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してユーザー定義関数の名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4520c-103">You can rename user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4520c-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4520c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4520c-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4520c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4520c-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4520c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4520c-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4520c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4520c-108">**ユーザー定義関数の名前を変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="4520c-108">**To rename user-defined functions, using:**</span></span>  
  
     [<span data-ttu-id="4520c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4520c-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4520c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4520c-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4520c-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="4520c-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4520c-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4520c-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4520c-113">関数名は、 [識別子](../databases/database-identifiers.md)の規則に従っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4520c-113">Function names must comply with the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="4520c-114">ユーザー定義関数の名前を変更しても、 **sys.sql_modules** カタログ ビューの定義列にある、対応するオブジェクトの名前は変更されません。</span><span class="sxs-lookup"><span data-stu-id="4520c-114">Renaming a user-defined function will not change the name of the corresponding object name in the definition column of the **sys.sql_modules** catalog view.</span></span> <span data-ttu-id="4520c-115">したがって、このオブジェクトの種類の名前を変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4520c-115">Therefore, we recommend that you do not rename this object type.</span></span> <span data-ttu-id="4520c-116">代わりに、ストアド プロシージャを削除して新しい名前で再作成してください。</span><span class="sxs-lookup"><span data-stu-id="4520c-116">Instead, drop and re-create the stored procedure with its new name.</span></span>  
  
-   <span data-ttu-id="4520c-117">ユーザー定義関数の名前または定義を変更すると、依存オブジェクトを更新してその関数に加えられた変更を反映しなければ、その依存オブジェクトが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4520c-117">Changing the name or definition of a user-defined function can cause dependent objects to fail when the objects are not updated to reflect the changes that have been made to the function.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4520c-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4520c-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4520c-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="4520c-119">Permissions</span></span>  
 <span data-ttu-id="4520c-120">関数を削除するには、関数が属するスキーマに対する ALTER 権限、または関数に対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4520c-120">To drop the function, requires either ALTER permission on the schema to which the function belongs or CONTROL permission on the function.</span></span> <span data-ttu-id="4520c-121">関数を再作成するには、データベースの CREATE FUNCTION 権限と、関数を作成するスキーマの ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4520c-121">To re-create the function, requires CREATE FUNCTION permission in the database and ALTER permission on the schema in which the function is being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4520c-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4520c-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-user-defined-functions"></a><span data-ttu-id="4520c-123">ユーザー定義関数の名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="4520c-123">To rename user-defined functions</span></span>  
  
1.  <span data-ttu-id="4520c-124">**オブジェクト エクスプローラー**で、名前を変更する関数が格納されているデータベースの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4520c-124">In **Object Explorer**, click the plus sign next to the database that contains the function you wish to rename and then</span></span>  
  
2.  <span data-ttu-id="4520c-125">**Programmability** フォルダーの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4520c-125">Click the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="4520c-126">名前変更する次の関数を含むフォルダーの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4520c-126">Click the plus sign next to the folder that contains the function you wish to rename:</span></span>  
  
    -   <span data-ttu-id="4520c-127">Table-valued Function</span><span class="sxs-lookup"><span data-stu-id="4520c-127">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="4520c-128">スカラー値関数</span><span class="sxs-lookup"><span data-stu-id="4520c-128">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="4520c-129">集計関数</span><span class="sxs-lookup"><span data-stu-id="4520c-129">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="4520c-130">名前を変更する関数を右クリックし、 **[名前の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4520c-130">Right-click the function you wish to rename and select **Rename**.</span></span>  
  
5.  <span data-ttu-id="4520c-131">関数の新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4520c-131">Enter the function's new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4520c-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4520c-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="4520c-133">**ユーザー定義関数の名前を変更するには**</span><span class="sxs-lookup"><span data-stu-id="4520c-133">**To rename user-defined functions**</span></span>  
  
 <span data-ttu-id="4520c-134">Transact-SQL ステートメントを使用して、このタスクを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="4520c-134">This task cannot be performed using Transact-SQL statements.</span></span> <span data-ttu-id="4520c-135">Transact-SQL を使用してユーザー定義関数の名前を変更するには、まず既存の関数を削除してから、新しい定義を使用して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4520c-135">To rename a user-defined function using Transact-SQL, you must first delete the existing function and then re-create it with the new name.</span></span> <span data-ttu-id="4520c-136">関数の古い名前を使用していたすべてのコードおよびアプリケーションが、新しい名前を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4520c-136">Ensure that all code and applications that used the function's old name now use the new name.</span></span>  
  
 <span data-ttu-id="4520c-137">詳細については、「[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)」および「[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4520c-137">For more information, see [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) and [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4520c-138">参照</span><span class="sxs-lookup"><span data-stu-id="4520c-138">See Also</span></span>  
 <span data-ttu-id="4520c-139">[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4520c-139">[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) </span></span>  
 [<span data-ttu-id="4520c-140">ユーザー定義関数の表示</span><span class="sxs-lookup"><span data-stu-id="4520c-140">View User-defined Functions</span></span>](user-defined-functions.md)  
  
  
