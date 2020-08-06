---
title: ストアド プロシージャの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- removing stored procedures
- stored procedures [SQL Server], deleting
- deleting stored procedures
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 418e68d4bb7c6ba6632767a554aea72e85726840
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644361"
---
# <a name="delete-a-stored-procedure"></a><span data-ttu-id="6bef6-102">ストアド プロシージャの削除</span><span class="sxs-lookup"><span data-stu-id="6bef6-102">Delete a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-delete-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="6bef6-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でストアド プロシージャを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-103">This topic describes how to delete a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="6bef6-104">**作業を開始する準備:** [制限事項と制約事項](#Restrictions)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="6bef6-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="6bef6-105">**プロシージャを削除するには次を使用します:** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="6bef6-105">**To delete a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6bef6-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="6bef6-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6bef6-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6bef6-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="6bef6-108">プロシージャを削除すると、依存オブジェクトとスクリプトを更新してプロシージャの削除を反映しない限り、そのオブジェクトとスクリプトが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6bef6-108">Deleting a procedure can cause dependent objects and scripts to fail when the objects and scripts are not updated to reflect the removal of the procedure.</span></span> <span data-ttu-id="6bef6-109">ただし、名前とパラメーターが同じである新しいプロシージャを作成し、削除したプロシージャと置き換えた場合、そのプロシージャを参照する他のオブジェクトは正常に処理されます。</span><span class="sxs-lookup"><span data-stu-id="6bef6-109">However, if a new procedure of the same name and the same parameters is created to replace the one that was deleted, other objects that reference it will still process successfully.</span></span> <span data-ttu-id="6bef6-110">詳細については、「 [ストアド プロシージャの依存関係の表示](view-the-dependencies-of-a-stored-procedure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bef6-110">For more information, see [View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6bef6-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6bef6-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6bef6-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="6bef6-112">Permissions</span></span>  
 <span data-ttu-id="6bef6-113">プロシージャが属しているスキーマに対する ALTER 権限、またはプロシージャに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6bef6-113">Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure.</span></span>  
  
##  <a name="how-to-delete-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="6bef6-114">ストアド プロシージャを削除する方法</span><span class="sxs-lookup"><span data-stu-id="6bef6-114">How to Delete a Stored Procedure</span></span>  
 <span data-ttu-id="6bef6-115">次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-115">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="6bef6-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6bef6-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="6bef6-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6bef6-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6bef6-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6bef6-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6bef6-119">**オブジェクト エクスプローラーでプロシージャを削除するには**</span><span class="sxs-lookup"><span data-stu-id="6bef6-119">**To delete a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="6bef6-120">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-120">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="6bef6-121">**[データベース]** を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-121">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="6bef6-122">**[ストアド プロシージャ]** を展開し、削除するプロシージャを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bef6-122">Expand **Stored Procedures**, right-click the procedure to remove, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="6bef6-123">プロシージャに依存するオブジェクトを表示するには、 **[依存関係の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bef6-123">To view objects that depend on the procedure, click **Show Dependencies**.</span></span>  
  
5.  <span data-ttu-id="6bef6-124">適切なプロシージャが選択されていることを確認して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bef6-124">Confirm the correct procedure is selected, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="6bef6-125">任意の依存オブジェクトおよびスクリプトからプロシージャへの参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-125">Remove references to the procedure from any dependent objects and scripts.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6bef6-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6bef6-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="6bef6-127">**クエリ エディターでプロシージャを削除するには**</span><span class="sxs-lookup"><span data-stu-id="6bef6-127">**To delete a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="6bef6-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="6bef6-129">**[データベース]** を展開し、プロシージャが属するデータベースを展開するか、ツール バーの利用可能なデータベースの一覧からデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-129">Expand **Databases**, expand the database in which the procedure belongs, or, from the tool bar, select the database from the list of available databases.</span></span>  
  
3.  <span data-ttu-id="6bef6-130">[ファイル] メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bef6-130">On the File menu, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="6bef6-131">現在のデータベースから削除するストアド プロシージャの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-131">Obtain the name of stored procedure to remove in the current database.</span></span> <span data-ttu-id="6bef6-132">オブジェクト エクスプローラーから、 **[プログラミング]** を展開し、 **[ストアド プロシージャ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-132">From Object Explorer, expand **Programmability** and then expand **Stored Procedures**.</span></span> <span data-ttu-id="6bef6-133">または、クエリ エディターで次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-133">Alternatively, in the query editor, run the following statement.</span></span>  
  
    ```sql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  <span data-ttu-id="6bef6-134">次の例をコピーしてクエリ エディターに貼り付け、現在のデータベースから削除するストアド プロシージャの名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-134">Copy and paste the following example into the query editor and insert a stored procedure name to delete from the current database.</span></span>  
  
    ```sql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  <span data-ttu-id="6bef6-135">任意の依存オブジェクトおよびスクリプトからプロシージャへの参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="6bef6-135">Remove references to the procedure from any dependent objects and scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bef6-136">参照</span><span class="sxs-lookup"><span data-stu-id="6bef6-136">See Also</span></span>  
 <span data-ttu-id="6bef6-137">[ストアド プロシージャの作成](create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6bef6-137">[Create a Stored Procedure](create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="6bef6-138">[ストアド プロシージャの変更](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6bef6-138">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="6bef6-139">[ストアド プロシージャの名前の変更](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6bef6-139">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="6bef6-140">[ストアド プロシージャの定義の表示](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6bef6-140">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="6bef6-141">[ストアド プロシージャの依存関係の表示](view-the-dependencies-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6bef6-141">[View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="6bef6-142">DROP PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6bef6-142">DROP PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
