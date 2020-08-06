---
title: プリンシパルに対する権限の許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Grant permission to a principal
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4256d62bdeac2d79c51e5f3792c991e0e3b15096
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741734"
---
# <a name="grant-a-permission-to-a-principal"></a><span data-ttu-id="157ea-102">プリンシパルに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="157ea-102">Grant a Permission to a Principal</span></span>
  <span data-ttu-id="157ea-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[tsql](../../../includes/tsql-md.md)]でプリンシパルに権限を与える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="157ea-103">This topic describes how to grant permission to a principal in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="157ea-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="157ea-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="157ea-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="157ea-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="157ea-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="157ea-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="157ea-107">Security</span><span class="sxs-lookup"><span data-stu-id="157ea-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="157ea-108">**プリンシパルに権限を与える方法:**</span><span class="sxs-lookup"><span data-stu-id="157ea-108">**To grant permission to a principal, using:**</span></span>  
  
     [<span data-ttu-id="157ea-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="157ea-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="157ea-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="157ea-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="157ea-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="157ea-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="157ea-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="157ea-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="157ea-113">権限の管理を容易にする次のベスト プラクティスを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="157ea-113">Consider the following best practices that can make managing permissions easier.</span></span>  
  
-   <span data-ttu-id="157ea-114">個々のログインまたはユーザーではなく、ロールに権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="157ea-114">Grant permission to roles, instead of individual logins or users.</span></span> <span data-ttu-id="157ea-115">ユーザーが入れ替わった場合、そのユーザーをロールから削除し、新しいユーザーをロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="157ea-115">When one individual is replaced by another, remove the departing individual from the role and add the new individual to the role.</span></span> <span data-ttu-id="157ea-116">ロールに関連付けられている多くの権限が自動的に新しいユーザーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="157ea-116">The many permissions that might be associated with the role will automatically be available to the new individual.</span></span> <span data-ttu-id="157ea-117">組織内の複数のユーザーが同じ権限を必要とする場合は、それぞれの権限をロールに追加します。そうすることで、それぞれのユーザーに同じ権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="157ea-117">If several people in an organization require the same permissions, adding each of them to the role will grant them the same permissions.</span></span>  
  
-   <span data-ttu-id="157ea-118">類似するセキュリティ保護可能なリソース (テーブル、ビュー、およびプロシージャ) をスキーマによって所有されるように構成した後、スキーマに対して権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="157ea-118">Configure similar securables (tables, views, and procedures) to be owned by a schema, then grant permissions to the schema.</span></span> <span data-ttu-id="157ea-119">たとえば、給与スキーマは、さまざまなテーブル、ビュー、およびストアド プロシージャを所有できます。</span><span class="sxs-lookup"><span data-stu-id="157ea-119">For example, the payroll schema might own several tables, views, and stored procedures.</span></span> <span data-ttu-id="157ea-120">そのスキーマへのアクセスを許可することにより、給与の機能を実行するために必要なすべての権限を同時に与えることができます。</span><span class="sxs-lookup"><span data-stu-id="157ea-120">By granting access to the schema, all the necessary permissions to perform the payroll function can be granted at the same time.</span></span> <span data-ttu-id="157ea-121">権限を付与できるセキュリティ保護可能なリソースの詳細については、「 [Securables](../securables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="157ea-121">For more information about what securables can be granted permissions, see [Securables](../securables.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="157ea-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="157ea-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="157ea-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="157ea-123">Permissions</span></span>  
 <span data-ttu-id="157ea-124">権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。</span><span class="sxs-lookup"><span data-stu-id="157ea-124">The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION or a higher permission that implies the permission being granted.</span></span> <span data-ttu-id="157ea-125">**sysadmin** 固定サーバー ロールのメンバーは、すべての権限を許可できます。</span><span class="sxs-lookup"><span data-stu-id="157ea-125">Members of the **sysadmin** fixed server role can grant any permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="157ea-126">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="157ea-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-grant-permission-to-a-principal"></a><span data-ttu-id="157ea-127">プリンシパルに権限を与えるには</span><span class="sxs-lookup"><span data-stu-id="157ea-127">To grant permission to a principal</span></span>  
  
1.  <span data-ttu-id="157ea-128">オブジェクト エクスプローラーで、権限を与えるオブジェクトが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="157ea-128">In Object Explorer, expand the database that contains the object to which you want to grant permissions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="157ea-129">次の手順は、ストアド プロシージャに対する権限の付与方法を説明していますが、同様の手順で、テーブル、ビュー、関数、およびセキュリティ保護可能なリソースに対して権限を追加できます。</span><span class="sxs-lookup"><span data-stu-id="157ea-129">These steps deal specifically with granting permissions to a stored procedure, but you can use similar steps to add permissions to tables, views, functions, and assemblies, as well as other securables.</span></span> <span data-ttu-id="157ea-130">詳細については、「[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="157ea-130">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)</span></span>  
  
2.  <span data-ttu-id="157ea-131">**[プログラミング]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="157ea-131">Expand the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="157ea-132">**[ストアド プロシージャ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="157ea-132">Expand the **Stored Procedures** folder.</span></span>  
  
4.  <span data-ttu-id="157ea-133">ストアド プロシージャを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157ea-133">Right-click a stored procedure and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="157ea-134">[**ストアドプロシージャのプロパティ-**_stored_procedure_name_ ] ダイアログボックスの [ページの選択] で、[**権限**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="157ea-134">In the **Stored Procedure Properties -**_stored_procedure_name_ dialog box, under select a page, select **Permissions**.</span></span> <span data-ttu-id="157ea-135">このページを使用して、ユーザーまたはロールをストアド プロシージャに追加し、追加したユーザーまたはロールが所有する権限を指定します。</span><span class="sxs-lookup"><span data-stu-id="157ea-135">Use this page to add users or roles to the stored procedure and specify the permissions those users or roles have.</span></span>  
  
6.  <span data-ttu-id="157ea-136">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157ea-136">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="157ea-137">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="157ea-137">Using Transact-SQL</span></span>  
  
#### <a name="to-grant-permission-to-a-principal"></a><span data-ttu-id="157ea-138">プリンシパルに権限を与えるには</span><span class="sxs-lookup"><span data-stu-id="157ea-138">To grant permission to a principal</span></span>  
  
1.  <span data-ttu-id="157ea-139">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="157ea-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="157ea-140">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157ea-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="157ea-141">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157ea-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 <span data-ttu-id="157ea-142">詳細については、「[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)」と「[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="157ea-142">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) and [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157ea-143">参照</span><span class="sxs-lookup"><span data-stu-id="157ea-143">See Also</span></span>  
 [<span data-ttu-id="157ea-144">プリンシパル &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="157ea-144">Principals &#40;Database Engine&#41;</span></span>](principals-database-engine.md)  
  
  
