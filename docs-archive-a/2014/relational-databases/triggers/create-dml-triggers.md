---
title: DML トリガーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], DML triggers
- deferred name resolution, DML triggers
- WITH ENCRYPTION clause
- IF UPDATE
- SET statement, DML triggers
- DML triggers, programming
- testing column changes
- results [SQL Server], DML triggers
ms.assetid: b2b52258-642b-462e-8e0f-18c09d2eccf4
author: rothja
ms.author: jroth
ms.openlocfilehash: f843513ba634bcb3479e373eb9ac978ab584588d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644899"
---
# <a name="create-dml-triggers"></a><span data-ttu-id="81db0-102">DML トリガーの作成</span><span class="sxs-lookup"><span data-stu-id="81db0-102">Create DML Triggers</span></span>
  <span data-ttu-id="81db0-103">このトピックでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の CREATE TRIGGER ステートメントを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] DML トリガーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="81db0-103">This topic describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] DML trigger by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER statement.</span></span>  
  
##  <a name="before-you-begin"></a><a name="Top"></a> <span data-ttu-id="81db0-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="81db0-104">Before You Begin</span></span>  
  
### <a name="limitations-and-restrictions"></a><span data-ttu-id="81db0-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="81db0-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="81db0-106">DML トリガーの作成に関する制限事項と制約事項の一覧については、「[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81db0-106">For a list of limitations and restrictions related to creating DML triggers, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="81db0-107">Permissions</span><span class="sxs-lookup"><span data-stu-id="81db0-107">Permissions</span></span>  
 <span data-ttu-id="81db0-108">トリガーを作成するテーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="81db0-108">Requires ALTER permission on the table or view on which the trigger is being created.</span></span>  
  
##  <a name="how-to-create-a-dml-trigger"></a><a name="Procedures"></a> <span data-ttu-id="81db0-109">DML トリガーの作成方法</span><span class="sxs-lookup"><span data-stu-id="81db0-109">How to Create a DML Trigger</span></span>  
 <span data-ttu-id="81db0-110">次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="81db0-110">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="81db0-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="81db0-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="81db0-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="81db0-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="81db0-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="81db0-113">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="81db0-114">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="81db0-114">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="81db0-115">**[データベース]** 、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース、 **[テーブル]** 、 **Purchasing.PurchaseOrderHeader**テーブルの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="81db0-115">Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, expand **Tables** and then expand the table **Purchasing.PurchaseOrderHeader**.</span></span>  
  
3.  <span data-ttu-id="81db0-116">**[トリガー]** を右クリックし、 **[新しいトリガー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81db0-116">Right-click **Triggers**, and then select **New Trigger**.</span></span>  
  
4.  <span data-ttu-id="81db0-117">**[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81db0-117">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span> <span data-ttu-id="81db0-118">または、Ctrl キーと Shift キーを押しながら M キーを押して、 **[テンプレート パラメーターの値の指定]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="81db0-118">Alternatively, you can press (Ctrl-Shift-M) to open the **Specify Values for Template Parameters** dialog box.</span></span>  
  
5.  <span data-ttu-id="81db0-119">**[テンプレート パラメーターの値の指定]** ダイアログ ボックスで、各パラメーターに次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="81db0-119">In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.</span></span>  
  
    |<span data-ttu-id="81db0-120">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81db0-120">Parameter</span></span>|<span data-ttu-id="81db0-121">値</span><span class="sxs-lookup"><span data-stu-id="81db0-121">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="81db0-122">Author</span><span class="sxs-lookup"><span data-stu-id="81db0-122">Author</span></span>|<span data-ttu-id="81db0-123">*名前*</span><span class="sxs-lookup"><span data-stu-id="81db0-123">*Your name*</span></span>|  
    |<span data-ttu-id="81db0-124">Create Date</span><span class="sxs-lookup"><span data-stu-id="81db0-124">Create Date</span></span>|<span data-ttu-id="81db0-125">*今日の日付*</span><span class="sxs-lookup"><span data-stu-id="81db0-125">*Today's date*</span></span>|  
    |<span data-ttu-id="81db0-126">説明</span><span class="sxs-lookup"><span data-stu-id="81db0-126">Description</span></span>|<span data-ttu-id="81db0-127">ベンダーへの新しい購買発注の挿入を許可する前に、ベンダーの信用格付けを確認します。</span><span class="sxs-lookup"><span data-stu-id="81db0-127">Checks the vendor credit rating before allowing a new purchase order with the vendor to be inserted.</span></span>|  
    |<span data-ttu-id="81db0-128">Schema_Name</span><span class="sxs-lookup"><span data-stu-id="81db0-128">Schema_Name</span></span>|<span data-ttu-id="81db0-129">購入</span><span class="sxs-lookup"><span data-stu-id="81db0-129">Purchasing</span></span>|  
    |<span data-ttu-id="81db0-130">Trigger_Name</span><span class="sxs-lookup"><span data-stu-id="81db0-130">Trigger_Name</span></span>|<span data-ttu-id="81db0-131">NewPODetail2</span><span class="sxs-lookup"><span data-stu-id="81db0-131">NewPODetail2</span></span>|  
    |<span data-ttu-id="81db0-132">Table_Name</span><span class="sxs-lookup"><span data-stu-id="81db0-132">Table_Name</span></span>|<span data-ttu-id="81db0-133">PurchaseOrderDetail</span><span class="sxs-lookup"><span data-stu-id="81db0-133">PurchaseOrderDetail</span></span>|  
    |<span data-ttu-id="81db0-134">Data_Modification_Statement</span><span class="sxs-lookup"><span data-stu-id="81db0-134">Data_Modification_Statement</span></span>|<span data-ttu-id="81db0-135">一覧から UPDATE と DELETE を削除します。</span><span class="sxs-lookup"><span data-stu-id="81db0-135">Remove UPDATE and DELETE from the list.</span></span>|  
  
6.  <span data-ttu-id="81db0-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81db0-136">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="81db0-137">**クエリ エディター**で、コメント `-- Insert statements for trigger here` を次のステートメントに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="81db0-137">In the **Query Editor**, replace the comment `-- Insert statements for trigger here` with the following statement:</span></span>  
  
    ```sql  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
  
8.  <span data-ttu-id="81db0-138">構文が有効であることを検証するには、 **[クエリ]** メニューの **[解析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81db0-138">To verify the syntax is valid, on the **Query** menu, click **Parse**.</span></span> <span data-ttu-id="81db0-139">エラー メッセージが返された場合は、ステートメントと上記の情報を比較し、必要に応じて修正してからこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="81db0-139">If an error message is returned, compare the statement with the information above and correct as needed and repeat this step.</span></span>  
  
9. <span data-ttu-id="81db0-140">DML トリガーを作成するには、 **[クエリ]** メニューの **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81db0-140">To create the DML trigger, from the **Query** menu, click **Execute**.</span></span> <span data-ttu-id="81db0-141">DML トリガーがデータベース内のオブジェクトとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="81db0-141">The DML trigger is created as an object in the database.</span></span>  
  
10. <span data-ttu-id="81db0-142">オブジェクト エクスプローラーにリストされた DML トリガーを確認するには、 **[トリガー]** を右クリックして **[更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="81db0-142">To see the DML trigger listed in Object Explorer, right-click **Triggers** and select **Refresh**.</span></span>  
  
 [<span data-ttu-id="81db0-143">はじめに</span><span class="sxs-lookup"><span data-stu-id="81db0-143">Before You Begin</span></span>](#Top)  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="81db0-144">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="81db0-144">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="81db0-145">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="81db0-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="81db0-146">**[ファイル]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81db0-146">From the **File** menu, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="81db0-147">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81db0-147">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="81db0-148">この例は、上と同じ DML トリガーを作成します。</span><span class="sxs-lookup"><span data-stu-id="81db0-148">This example creates the same stored DML trigger as above.</span></span>  
  
    ```sql
    -- Trigger valid for multirow and single row inserts  
    -- and optimal for single row inserts.  
    USE AdventureWorks2012;  
    GO  
    CREATE TRIGGER NewPODetail3  
    ON Purchasing.PurchaseOrderDetail  
    FOR INSERT AS  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
