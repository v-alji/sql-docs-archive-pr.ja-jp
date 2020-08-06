---
title: テーブルの作成 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d84a4da6a10fbcbae311fe1bf738c03b85a4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646093"
---
# <a name="create-tables-database-engine"></a><span data-ttu-id="622be-102">テーブルの作成 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="622be-102">Create Tables (Database Engine)</span></span>
  <span data-ttu-id="622be-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して新しいテーブルを作成して名前を付け、それを既存のデータベースに追加できます。</span><span class="sxs-lookup"><span data-stu-id="622be-103">You can create a new table, name it, and add it to an existing database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>

> [!NOTE]
>  <span data-ttu-id="622be-104">SQL Azure データベースに接続している場合、[新しいテーブル] オプションを選択すると、テーブルの作成テンプレート スクリプトが実行されます。</span><span class="sxs-lookup"><span data-stu-id="622be-104">If you are connected to a SQL Azure database, the new table option launches a create table template script.</span></span> <span data-ttu-id="622be-105">パラメーターを編集してから、このスクリプトを実行して新しいテーブルを作成してください。</span><span class="sxs-lookup"><span data-stu-id="622be-105">Edit the parameters, then run the script to create a new table.</span></span> <span data-ttu-id="622be-106">詳細については、「 [SQL Azure の概要](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622be-106">For more information, see [SQL Azure Overview](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx).</span></span>

 <span data-ttu-id="622be-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="622be-107">**In This Topic**</span></span>

-   <span data-ttu-id="622be-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="622be-108">**Before you begin:**</span></span>

     [<span data-ttu-id="622be-109">Security</span><span class="sxs-lookup"><span data-stu-id="622be-109">Security</span></span>](#Security)

-   <span data-ttu-id="622be-110">**テーブルを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="622be-110">**To create a table, using:**</span></span>

     [<span data-ttu-id="622be-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="622be-111">SQL Server Management Studio</span></span>](#SSMSProcedure)

     [<span data-ttu-id="622be-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="622be-112">Transact-SQL</span></span>](#TsqlProcedure)

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="622be-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="622be-113">Before You Begin</span></span>

###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="622be-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="622be-114">Security</span></span>

####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="622be-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="622be-115">Permissions</span></span>
 <span data-ttu-id="622be-116">データベースの CREATE TABLE 権限と、テーブルを作成するスキーマの ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="622be-116">Requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>

 <span data-ttu-id="622be-117">CREATE TABLE ステートメント内の列を CLR ユーザー定義型として定義する場合は、その型の所有権か、その型に対する REFERENCES 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="622be-117">If any columns in the CREATE TABLE statement are defined as a CLR user-defined type, either ownership of the type or REFERENCES permission on it is required.</span></span>

 <span data-ttu-id="622be-118">CREATE TABLE ステートメント内の列に XML スキーマ コレクションが関連付けられている場合は、その XML スキーマ コレクションの所有権か、そのスキーマ コレクションに対する REFERENCES 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="622be-118">If any columns in the CREATE TABLE statement have an XML schema collection associated with them, either ownership of the XML schema collection or REFERENCES permission on it is required.</span></span>

##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="622be-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="622be-119">Using SQL Server Management Studio</span></span>

#### <a name="to-create-a-table-with-table-designer"></a><span data-ttu-id="622be-120">テーブル デザイナーでテーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="622be-120">To create a table with Table Designer</span></span>

1.  <span data-ttu-id="622be-121">**オブジェクト エクスプローラー**で、変更するデータベースを含む [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="622be-121">In **Object Explorer**, connect to the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] that contains the database to be modified.</span></span>

2.  <span data-ttu-id="622be-122">**オブジェクト エクスプローラー**で、 **[データベース]** ノードを展開し、新しいテーブルを格納するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="622be-122">In **Object Explorer**, expand the **Databases** node and then expand the database that will contain the new table.</span></span>

3.  <span data-ttu-id="622be-123">オブジェクト エクスプローラーで、データベースの **[テーブル]** ノードを右クリックし、 **[新しいテーブル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="622be-123">In Object Explorer, right-click the **Tables** node of your database and then click **New Table**.</span></span>

4.  <span data-ttu-id="622be-124">次の図に示すように、列名を入力し、データ型を選択した後、各列で null 値を許可するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="622be-124">Type column names, choose data types, and choose whether to allow nulls for each column as shown in the following illustration.</span></span>

     <span data-ttu-id="622be-125">![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")</span><span class="sxs-lookup"><span data-stu-id="622be-125">![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")</span></span>

5.  <span data-ttu-id="622be-126">他のプロパティ (ID 列または計算列の値など) を指定するには、列をクリックし、列のプロパティ タブで適切なプロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="622be-126">To specify more properties for a column, such as identity or computed column values, click the column and in the column properties tab, choose the appropriate properties.</span></span> <span data-ttu-id="622be-127">列のプロパティの詳細については、「[テーブル列のプロパティ &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622be-127">For more information about column properties, see [Table Column Properties &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md).</span></span>

6.  <span data-ttu-id="622be-128">列を主キーとして指定するには、列を右クリックし、 **[主キーの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="622be-128">To specify a column as a primary key, right-click the column and select **Set Primary Key**.</span></span> <span data-ttu-id="622be-129">詳細については、「 [Create Primary Keys](../tables/create-primary-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622be-129">For more information, see [Create Primary Keys](../tables/create-primary-keys.md).</span></span>

7.  <span data-ttu-id="622be-130">外部キーのリレーションシップ、CHECK 制約、またはインデックスを作成するには、テーブル デザイナー ペイン内で右クリックし、次の図に示すように、一覧からオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="622be-130">To create foreign key relationships, check constraints, or indexes, right-click in the Table Designer pane and select an object from the list as shown in the following illustration.</span></span>

     <span data-ttu-id="622be-131">![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")</span><span class="sxs-lookup"><span data-stu-id="622be-131">![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")</span></span>

     <span data-ttu-id="622be-132">これらのオブジェクトの詳細については、「 [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md)」、「 [Create Check Constraints](../tables/create-check-constraints.md) 」、および「 [Indexes](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622be-132">For more information about these objects, see [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md), [Create Check Constraints](../tables/create-check-constraints.md) and [Indexes](../indexes/indexes.md).</span></span>

8.  <span data-ttu-id="622be-133">既定では、テーブルは **dbo** スキーマに含まれています。</span><span class="sxs-lookup"><span data-stu-id="622be-133">By default, the table is contained in the **dbo** schema.</span></span> <span data-ttu-id="622be-134">テーブルに対して別のスキーマを指定するには、テーブル デザイナー ペイン内で右クリックし、次の図に示すように、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="622be-134">To specify a different schema for the table, right-click in the Table Designer pane and select **Properties** as shown in the following illustration.</span></span> <span data-ttu-id="622be-135">**[スキーマ]** ボックスの一覧で、適切なスキーマを選択します。</span><span class="sxs-lookup"><span data-stu-id="622be-135">From the **Schema** drop-down list, select the appropriate schema.</span></span>

     <span data-ttu-id="622be-136">![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")</span><span class="sxs-lookup"><span data-stu-id="622be-136">![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")</span></span>

     <span data-ttu-id="622be-137">スキーマの詳細については、「 [Create a Database Schema](../security/authentication-access/create-a-database-schema.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622be-137">For more information about schemas, see [Create a Database Schema](../security/authentication-access/create-a-database-schema.md).</span></span>

9. <span data-ttu-id="622be-138">[**ファイル**] メニューの [ **Save** *テーブル名*の保存] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="622be-138">From the **File** menu, choose **Save** *table name*.</span></span>

10. <span data-ttu-id="622be-139">**[名前の選択]** ダイアログ ボックスで、テーブルの名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="622be-139">In the **Choose Name** dialog box, type a name for the table and click **OK**.</span></span>

11. <span data-ttu-id="622be-140">新しいテーブルを表示するには、 **オブジェクト エクスプローラー**で、 **[テーブル]** ノードを展開し、 **F5** キーを押してオブジェクトの一覧を更新します。</span><span class="sxs-lookup"><span data-stu-id="622be-140">To view the new table, in **Object Explorer**, expand the **Tables** node and press **F5** to refresh the list of objects.</span></span> <span data-ttu-id="622be-141">新しいテーブルがテーブルの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="622be-141">The new table is displayed in the list of tables.</span></span>

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="622be-142">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="622be-142">Using Transact-SQL</span></span>

#### <a name="to-create-a-table-in-the-query-editor"></a><span data-ttu-id="622be-143">クエリ エディターでテーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="622be-143">To create a table in the Query Editor</span></span>

1.  <span data-ttu-id="622be-144">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="622be-144">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>

2.  <span data-ttu-id="622be-145">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="622be-145">On the Standard bar, click **New Query**.</span></span>

3.  <span data-ttu-id="622be-146">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="622be-146">Copy and paste the following example into the query window and click **Execute**.</span></span>

    ```
    CREATE TABLE dbo.PurchaseOrderDetail
    (
        PurchaseOrderID int NOT NULL
        ,LineNumber smallint NOT NULL
        ,ProductID int NULL
        ,UnitPrice money NULL
        ,OrderQty smallint NULL
        ,ReceivedQty float NULL
        ,RejectedQty float NULL
        ,DueDate datetime NULL
    );
    ```

 <span data-ttu-id="622be-147">詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622be-147">For more examples, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>


