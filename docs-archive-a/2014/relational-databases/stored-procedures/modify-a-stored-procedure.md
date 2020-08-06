---
title: ストアド プロシージャの変更 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying stored procedures
- editing stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: 13396239-6100-48ce-aa34-461358d99c92
author: stevestein
ms.author: sstein
ms.openlocfilehash: 906f0e06650da505094d18774ce86dab53d53f38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711806"
---
# <a name="modify-a-stored-procedure"></a><span data-ttu-id="240c1-102">ストアド プロシージャの変更</span><span class="sxs-lookup"><span data-stu-id="240c1-102">Modify a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-modify-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="240c1-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でストアド プロシージャを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="240c1-103">This topic describes how to modify a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="240c1-104">**作業を開始する準備:** [制限事項と制約事項](#Restrictions)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="240c1-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="240c1-105">**プロシージャを変更するには次を使用します:** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="240c1-105">**To alter a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="240c1-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="240c1-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="240c1-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="240c1-107">Limitations and Restrictions</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="240c1-108">ストアド プロシージャを CLR ストアド プロシージャに変更したり、その逆に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="240c1-108">stored procedures cannot be modified to be CLR stored procedures and vice versa.</span></span>  
  
 <span data-ttu-id="240c1-109">以前のプロシージャ定義が WITH ENCRYPTION または WITH RECOMPILE を使用して作成されている場合、これらのオプションは、ALTER PROCEDURE ステートメントに指定されるときだけ有効になります。</span><span class="sxs-lookup"><span data-stu-id="240c1-109">If the previous procedure definition was created using WITH ENCRYPTION or WITH RECOMPILE, these options are enabled only if they are included in the ALTER PROCEDURE statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="240c1-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="240c1-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="240c1-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="240c1-111">Permissions</span></span>  
 <span data-ttu-id="240c1-112">プロシージャに対する ALTER PROCEDURE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="240c1-112">Requires ALTER PROCEDURE permission on the procedure.</span></span>  
  
##  <a name="how-to-modify-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="240c1-113">ストアド プロシージャを変更する方法</span><span class="sxs-lookup"><span data-stu-id="240c1-113">How to Modify a Stored Procedure</span></span>  
 <span data-ttu-id="240c1-114">次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="240c1-114">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="240c1-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="240c1-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="240c1-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="240c1-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="240c1-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="240c1-117">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="240c1-118">**Management Studio でプロシージャを変更するには**</span><span class="sxs-lookup"><span data-stu-id="240c1-118">**To modify a procedure in Management Studio**</span></span>  
  
1.  <span data-ttu-id="240c1-119">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="240c1-119">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="240c1-120">**[データベース]** を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="240c1-120">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="240c1-121">**[ストアド プロシージャ]** を展開し、変更するプロシージャを右クリックして、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-121">Expand **Stored Procedures**, right-click the procedure to modify, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="240c1-122">ストアド プロシージャのテキストを変更します。</span><span class="sxs-lookup"><span data-stu-id="240c1-122">Modify the text of the stored procedure.</span></span>  
  
5.  <span data-ttu-id="240c1-123">構文をテストするには、 **[クエリ]** メニューの **[解析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-123">To test the syntax, on the **Query** menu, click **Parse**.</span></span>  
  
6.  <span data-ttu-id="240c1-124">変更をプロシージャの定義に保存するには、 **[クエリ]** メニューの **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-124">To save the modifications to the procedure definition, on the **Query** menu, click **Execute**.</span></span>  
  
7.  <span data-ttu-id="240c1-125">更新されたプロシージャの定義を [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトとして保存するには、 **[ファイル]** メニューの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-125">To save the updated procedure definition as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="240c1-126">ファイル名をそのまま使用するか、または別の名前を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-126">Accept the file name or replace it with a new name, and then click **Save**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="240c1-127">すべてのユーザー入力を検証します。</span><span class="sxs-lookup"><span data-stu-id="240c1-127">Validate all user input.</span></span> <span data-ttu-id="240c1-128">ユーザー入力は検証するまで連結しないでください。</span><span class="sxs-lookup"><span data-stu-id="240c1-128">Do not concatenate user input before you validate it.</span></span> <span data-ttu-id="240c1-129">検証していないユーザー入力から作成されたコマンドは、絶対に実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="240c1-129">Never execute a command constructed from unvalidated user input.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="240c1-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="240c1-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="240c1-131">**クエリ エディターでプロシージャを変更するには**</span><span class="sxs-lookup"><span data-stu-id="240c1-131">**To modify a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="240c1-132">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="240c1-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="240c1-133">**[データベース]** を展開し、プロシージャが属するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="240c1-133">Expand **Databases**, expand the database in which the procedure belongs.</span></span> <span data-ttu-id="240c1-134">または、ツール バーの利用可能なデータベースの一覧からデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="240c1-134">Or, from the tool bar, select the database from the list of available databases.</span></span> <span data-ttu-id="240c1-135">この例では [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="240c1-135">For this example, select the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
3.  <span data-ttu-id="240c1-136">**[ファイル]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-136">On the **File** menu, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="240c1-137">次の例をコピーし、クエリ エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="240c1-137">Copy and paste the following example into the query editor.</span></span> <span data-ttu-id="240c1-138">この例では、 `uspVendorAllInfo` データベース内のすべてのベンダーの名前と、そのベンダーの提供製品、信用格付け、およびベンダーが現時点で製品を提供できるかどうかを返す [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] プロシージャが作成されます。</span><span class="sxs-lookup"><span data-stu-id="240c1-138">The example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
    ```  
  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
5.  <span data-ttu-id="240c1-139">**[ファイル]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-139">On the **File** menu, click **New Query**.</span></span>  
  
6.  <span data-ttu-id="240c1-140">次の例をコピーし、クエリ エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="240c1-140">Copy and paste the following example into the query editor.</span></span> <span data-ttu-id="240c1-141">この例では、 `uspVendorAllInfo` プロシージャが変更されます。</span><span class="sxs-lookup"><span data-stu-id="240c1-141">The example modifies the `uspVendorAllInfo` procedure.</span></span> <span data-ttu-id="240c1-142">EXECUTE AS CALLER 句が削除され、指定した製品を供給するベンダーだけを返すようにプロシージャの本体が変更されます。</span><span class="sxs-lookup"><span data-stu-id="240c1-142">The EXECUTE AS CALLER clause is removed and the body of the procedure is modified to return only those vendors that supply the specified product.</span></span> <span data-ttu-id="240c1-143">ここでは、 `LEFT` 関数および `CASE` 関数を使用して、結果セットの表示をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="240c1-143">The `LEFT` and `CASE` functions customize the appearance of the result set.</span></span>  
  
    ```  
    ALTER PROCEDURE Purchasing.uspVendorAllInfo  
        @Product varchar(25)   
    AS  
        SET NOCOUNT ON;  
        SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
        'Rating' = CASE v.CreditRating   
            WHEN 1 THEN 'Superior'  
            WHEN 2 THEN 'Excellent'  
            WHEN 3 THEN 'Above average'  
            WHEN 4 THEN 'Average'  
            WHEN 5 THEN 'Below average'  
            ELSE 'No rating'  
            END  
        , Availability = CASE v.ActiveFlag  
            WHEN 1 THEN 'Yes'  
            ELSE 'No'  
            END  
        FROM Purchasing.Vendor AS v   
        INNER JOIN Purchasing.ProductVendor AS pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product AS p   
          ON pv.ProductID = p.ProductID   
        WHERE p.Name LIKE @Product  
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
7.  <span data-ttu-id="240c1-144">変更をプロシージャの定義に保存するには、 **[クエリ]** メニューの **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-144">To save the modifications to the procedure definition, on the **Query** menu, click **Execute**.</span></span>  
  
8.  <span data-ttu-id="240c1-145">更新されたプロシージャの定義を [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトとして保存するには、 **[ファイル]** メニューの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-145">To save the updated procedure definition as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="240c1-146">ファイル名をそのまま使用するか、または別の名前を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="240c1-146">Accept the file name or replace it with a new name, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="240c1-147">変更したストアド プロシージャを実行するには、次の例を実行します。</span><span class="sxs-lookup"><span data-stu-id="240c1-147">To run the modified stored procedure, execute the following example.</span></span>  
  
    ```  
    EXEC Purchasing.uspVendorAllInfo N'LL Crankarm';  
    GO  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="240c1-148">参照</span><span class="sxs-lookup"><span data-stu-id="240c1-148">See Also</span></span>  
 [<span data-ttu-id="240c1-149">ALTER PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="240c1-149">ALTER PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-procedure-transact-sql)  
  
  
