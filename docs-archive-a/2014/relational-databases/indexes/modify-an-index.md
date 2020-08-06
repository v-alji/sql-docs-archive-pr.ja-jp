---
title: インデックスの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], modifying
- modifying indexes
- index changes [SQL Server]
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af9293966afce8372f5b83a579418c546c82816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739967"
---
# <a name="modify-an-index"></a><span data-ttu-id="ede31-102">インデックスの変更</span><span class="sxs-lookup"><span data-stu-id="ede31-102">Modify an Index</span></span>
  <span data-ttu-id="ede31-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のインデックスを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ede31-103">This topic describes how to modify an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ede31-104">PRIMARY KEY 制約または UNIQUE 制約の結果として作成されたインデックスは、この方法を使用して変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="ede31-104">Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be modified by using this method.</span></span> <span data-ttu-id="ede31-105">このような場合には、制約を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ede31-105">Instead, the constraint must be modified.</span></span>  
  
 <span data-ttu-id="ede31-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ede31-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ede31-107">**インデックスを変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="ede31-107">**To modify an index, using:**</span></span>  
  
     [<span data-ttu-id="ede31-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ede31-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ede31-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ede31-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ede31-110">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ede31-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-an-index"></a><span data-ttu-id="ede31-111">インデックスを変更するには</span><span class="sxs-lookup"><span data-stu-id="ede31-111">To modify an index</span></span>  
  
1.  <span data-ttu-id="ede31-112">オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="ede31-112">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ede31-113">**[データベース]** を展開し、テーブルが属するデータベースを展開して、 **[テーブル]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="ede31-113">Expand **Databases**, expand the database in which the table belongs, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="ede31-114">インデックスが属するテーブルを展開し、 **[インデックス]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="ede31-114">Expand the table in which the index belongs and then expand **Indexes**.</span></span>  
  
4.  <span data-ttu-id="ede31-115">変更するインデックスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede31-115">Right-click the index that you want to modify and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="ede31-116">**[インデックスのプロパティ]** ダイアログ ボックスで、目的の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="ede31-116">In the **Index Properties** dialog box, make the desired changes.</span></span> <span data-ttu-id="ede31-117">たとえば、インデックス キーの列の追加や削除を行うことができます。また、インデックス オプションの設定も変更できます。</span><span class="sxs-lookup"><span data-stu-id="ede31-117">For example, you can add or remove a column from the index key, or change the setting of an index option.</span></span>  
  
#### <a name="to-modify-index-columns"></a><span data-ttu-id="ede31-118">インデックス列を変更するには</span><span class="sxs-lookup"><span data-stu-id="ede31-118">To modify index columns</span></span>  
  
1.  <span data-ttu-id="ede31-119">インデックス列の位置を追加、削除、または変更するには、 **[インデックスのプロパティ]** ダイアログ ボックスの **[全般]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede31-119">To add, remove, or change the position of an index column, select the **General** page from the **Index Properties** dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ede31-120">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ede31-120">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-an-index"></a><span data-ttu-id="ede31-121">インデックスを変更するには</span><span class="sxs-lookup"><span data-stu-id="ede31-121">To modify an index</span></span>  
  
1.  <span data-ttu-id="ede31-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="ede31-122">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ede31-123">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede31-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ede31-124">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede31-124">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ede31-125">次の例では、 `ProductID` オプションを使って、 `Production.WorkOrder` テーブルの `DROP_EXISTING` 列にある既存のインデックスを削除して再作成します。</span><span class="sxs-lookup"><span data-stu-id="ede31-125">This example drops and re-creates an existing index on the `ProductID` column of the `Production.WorkOrder` table by using the `DROP_EXISTING` option.</span></span> <span data-ttu-id="ede31-126">ここではオプション `FILLFACTOR` および `PAD_INDEX` も設定されています。</span><span class="sxs-lookup"><span data-stu-id="ede31-126">The options `FILLFACTOR` and `PAD_INDEX` are also set.</span></span>  
  
     [!code-sql[IndexDDL#CreateIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/createindex.sql#createindex4)]  
  
     <span data-ttu-id="ede31-127">次の例では、ALTER INDEX を使用して、 `AK_SalesOrderHeader_SalesOrderNumber`インデックスのいくつかのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="ede31-127">The following example uses ALTER INDEX to set several options on the index `AK_SalesOrderHeader_SalesOrderNumber`.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
#### <a name="to-modify-index-columns"></a><span data-ttu-id="ede31-128">インデックス列を変更するには</span><span class="sxs-lookup"><span data-stu-id="ede31-128">To modify index columns</span></span>  
  
1.  <span data-ttu-id="ede31-129">インデックス列の位置を追加、削除、または変更するには、インデックスを削除してから再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ede31-129">To add, remove, or change the position of an index column, you must drop and recreate the index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede31-130">参照</span><span class="sxs-lookup"><span data-stu-id="ede31-130">See Also</span></span>  
 <span data-ttu-id="ede31-131">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ede31-131">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="ede31-132">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ede31-132">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="ede31-133">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ede31-133">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span></span>  
 <span data-ttu-id="ede31-134">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ede31-134">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) </span></span>  
 <span data-ttu-id="ede31-135">[sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ede31-135">[sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql) </span></span>  
 <span data-ttu-id="ede31-136">[インデックス オプションの設定](set-index-options.md) </span><span class="sxs-lookup"><span data-stu-id="ede31-136">[Set Index Options](set-index-options.md) </span></span>  
 [<span data-ttu-id="ede31-137">インデックスの名前変更</span><span class="sxs-lookup"><span data-stu-id="ede31-137">Rename Indexes</span></span>](indexes.md)  
  
  
