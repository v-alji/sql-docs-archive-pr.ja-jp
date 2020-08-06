---
title: ストアド プロシージャに対する権限の許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23ea130b9d2033128adc99413c053d66936e3ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641531"
---
# <a name="grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="1616d-102">ストアド プロシージャに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="1616d-102">Grant Permissions on a Stored Procedure</span></span>
  <span data-ttu-id="1616d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ストアド プロシージャに対する権限を許可する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1616d-103">This topic describes how to grant permissions on a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1616d-104">権限は、データベース内の既存のユーザー、データベース ロール、またはアプリケーション ロールに許可することができます。</span><span class="sxs-lookup"><span data-stu-id="1616d-104">Permissions can be granted to an existing user, database role, or application role in the database.</span></span>  
  
 <span data-ttu-id="1616d-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1616d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1616d-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1616d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1616d-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="1616d-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1616d-108">Security</span><span class="sxs-lookup"><span data-stu-id="1616d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1616d-109">**ストアド プロシージャに対する権限を許可するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="1616d-109">**To grant permissions on a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="1616d-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1616d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1616d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1616d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1616d-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="1616d-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1616d-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="1616d-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1616d-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、システム プロシージャやシステム関数に対する権限を許可することはできません。</span><span class="sxs-lookup"><span data-stu-id="1616d-114">You cannot use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to grant permissions on system procedures or system functions.</span></span> <span data-ttu-id="1616d-115">代わりに、 [GRANT (オブジェクト権限の許可)](/sql/t-sql/statements/grant-object-permissions-transact-sql) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="1616d-115">Use [GRANT Object Permissions](/sql/t-sql/statements/grant-object-permissions-transact-sql) instead.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1616d-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1616d-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1616d-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="1616d-117">Permissions</span></span>  
 <span data-ttu-id="1616d-118">権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1616d-118">The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION, or a higher permission that implies the permission being granted.</span></span> <span data-ttu-id="1616d-119">プロシージャが属しているスキーマに対する ALTER 権限、またはプロシージャに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="1616d-119">Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure.</span></span> <span data-ttu-id="1616d-120">詳細については、「 [GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)を使用して、ストアド プロシージャに対する権限を許可する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1616d-120">For more information, see [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1616d-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1616d-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="1616d-122">ストアド プロシージャに対して権限を許可するには</span><span class="sxs-lookup"><span data-stu-id="1616d-122">To grant permissions on a stored procedure</span></span>  
  
1.  <span data-ttu-id="1616d-123">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="1616d-123">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="1616d-124">**[データベース]** を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="1616d-124">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="1616d-125">**[ストアド プロシージャ]** を展開し、権限を許可するプロシージャを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1616d-125">Expand **Stored Procedures**, right-click the procedure to grant permissions on, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1616d-126">**[ストアド プロシージャのプロパティ]** で、 **[権限]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="1616d-126">From **Stored Procedure Properties**, select the **Permissions** page.</span></span>  
  
5.  <span data-ttu-id="1616d-127">ユーザー、データベース ロール、またはアプリケーション ロールに権限を許可するには、 **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1616d-127">To grant permissions to a user, database role, or application role, click **Search**.</span></span>  
  
6.  <span data-ttu-id="1616d-128">**[ユーザーまたはロールの選択]** で、 **[オブジェクトの種類]** をクリックして目的のユーザーやロールを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="1616d-128">In **Select Users or Roles**, click **Object Types** to add or clear the users and roles you want.</span></span>  
  
7.  <span data-ttu-id="1616d-129">**[参照]** をクリックしてユーザーまたはロールの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="1616d-129">Click **Browse** to display the list of users or roles.</span></span> <span data-ttu-id="1616d-130">権限を許可するユーザーまたはロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="1616d-130">Select the users or roles to whom permissions should be granted.</span></span>  
  
8.  <span data-ttu-id="1616d-131">**[明示的な権限]** グリッドで、指定したユーザーまたはロールに許可する権限を選択します。</span><span class="sxs-lookup"><span data-stu-id="1616d-131">In the **Explicit Permissions** grid, select the permissions to grant to the specified user or role.</span></span> <span data-ttu-id="1616d-132">すべてのアクセス許可の説明については、「[権限 &#40;データベース エンジン&#41;](../security/permissions-database-engine.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1616d-132">For a description of the permissions, see [Permissions &#40;Database Engine&#41;](../security/permissions-database-engine.md).</span></span>  
  
 <span data-ttu-id="1616d-133">**[許可]** を選択すると、指定した権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="1616d-133">Selecting **Grant** indicates the grantee will be given the specified permission.</span></span> <span data-ttu-id="1616d-134">**[許可の有無]** を選択すると、指定した権限をさらに他のプリンシパルにも許可できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1616d-134">Selecting **Grant With** indicates that the grantee will also be able to grant the specified permission to other principals.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1616d-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1616d-135">Using Transact-SQL</span></span>  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="1616d-136">ストアド プロシージャに対して権限を許可するには</span><span class="sxs-lookup"><span data-stu-id="1616d-136">To grant permissions on a stored procedure</span></span>  
  
1.  <span data-ttu-id="1616d-137">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="1616d-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1616d-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1616d-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1616d-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1616d-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1616d-140">この例では、ストアド プロシージャ `EXECUTE` に対する `HumanResources.uspUpdateEmployeeHireInfo` 権限を、アプリケーション ロール `Recruiting11`に対して許可します。</span><span class="sxs-lookup"><span data-stu-id="1616d-140">This example grants `EXECUTE` permission on the stored procedure `HumanResources.uspUpdateEmployeeHireInfo` to an application role named `Recruiting11`.</span></span>  
  
```sql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="1616d-141">参照</span><span class="sxs-lookup"><span data-stu-id="1616d-141">See Also</span></span>  
 <span data-ttu-id="1616d-142">[sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1616d-142">[sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) </span></span>  
 <span data-ttu-id="1616d-143">[GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1616d-143">[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span></span>  
 <span data-ttu-id="1616d-144">[ストアド プロシージャの作成](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="1616d-144">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="1616d-145">[ストアド プロシージャの変更](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="1616d-145">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="1616d-146">[ストアド プロシージャの削除](../stored-procedures/delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="1616d-146">[Delete a Stored Procedure](../stored-procedures/delete-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="1616d-147">ストアド プロシージャの名前の変更</span><span class="sxs-lookup"><span data-stu-id="1616d-147">Rename a Stored Procedure</span></span>](rename-a-stored-procedure.md)  
  
  
