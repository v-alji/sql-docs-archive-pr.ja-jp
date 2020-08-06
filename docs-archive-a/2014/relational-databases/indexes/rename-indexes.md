---
title: インデックスの名前変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- renaming indexes
- index names [SQL Server]
- indexes [SQL Server], renaming
ms.assetid: d3d612a1-ea1b-4d99-85d2-0a2ad54f4b0e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 184d6e20f7857c5ea3535e77e21a0630ffc7b678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645051"
---
# <a name="rename-indexes"></a><span data-ttu-id="829e7-102">インデックスの名前変更</span><span class="sxs-lookup"><span data-stu-id="829e7-102">Rename Indexes</span></span>
  <span data-ttu-id="829e7-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のインデックスの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="829e7-103">This topic describes how to rename an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="829e7-104">インデックスの名前を変更すると、現在のインデックス名が指定した新しい名前に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="829e7-104">Renaming an index replaces the current index name with the new name that you provide.</span></span> <span data-ttu-id="829e7-105">指定する名前は、テーブルやビュー内で一意になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="829e7-105">The specified name must be unique within the table or view.</span></span> <span data-ttu-id="829e7-106">たとえば、2 つのテーブルにそれぞれ **XPK_1**という名前のインデックスを含めることはできますが、同じテーブルに **XPK_1**という名前のインデックスを 2 つ含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="829e7-106">For example, two tables can have an index named **XPK_1**, but the same table cannot have two indexes named **XPK_1**.</span></span> <span data-ttu-id="829e7-107">無効になっている既存のインデックスと同じ名前のインデックスを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="829e7-107">You cannot create an index with the same name as an existing disabled index.</span></span> <span data-ttu-id="829e7-108">インデックス名を変更しても、インデックスは再構築されません。</span><span class="sxs-lookup"><span data-stu-id="829e7-108">Renaming an index does not cause the index to be rebuilt.</span></span>  
  
 <span data-ttu-id="829e7-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="829e7-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="829e7-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="829e7-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="829e7-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="829e7-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="829e7-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="829e7-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="829e7-113">**以下を使用してインデックスの名前を変更するには:**</span><span class="sxs-lookup"><span data-stu-id="829e7-113">**To rename an index, using:**</span></span>  
  
     [<span data-ttu-id="829e7-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="829e7-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="829e7-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="829e7-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="829e7-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="829e7-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="829e7-117">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="829e7-117">Limitations and Restrictions</span></span>  
 <span data-ttu-id="829e7-118">テーブルに PRIMARY KEY 制約または UNIQUE 制約を作成すると、制約と同じ名前のインデックスが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="829e7-118">When you create a PRIMARY KEY or UNIQUE constraint on a table, an index with the same name as the constraint is automatically created for the table.</span></span> <span data-ttu-id="829e7-119">インデックス名はテーブル内で一意になる必要があるので、そのテーブルに既存の PRIMARY KEY 制約または UNIQUE 制約と同じ名前のインデックスを作成したり、同じ名前を付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="829e7-119">Because index names must be unique within the table, you cannot create or rename an index to have the same name as an existing PRIMARY KEY or UNIQUE constraint on the table.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="829e7-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="829e7-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="829e7-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="829e7-121">Permissions</span></span>  
 <span data-ttu-id="829e7-122">インデックスに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="829e7-122">Requires ALTER permission on the index.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="829e7-123">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="829e7-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-an-index-by-using-the-table-designer"></a><span data-ttu-id="829e7-124">テーブル デザイナーを使用してインデックスの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="829e7-124">To rename an index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="829e7-125">オブジェクト エクスプローラーで、インデックスの名前を変更するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="829e7-125">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rename an index.</span></span>  
  
2.  <span data-ttu-id="829e7-126">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="829e7-126">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="829e7-127">インデックスの名前を変更するテーブルを右クリックし、 **[デザイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="829e7-127">Right-click the table on which you want to rename an index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="829e7-128">**[テーブル デザイナー]** メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="829e7-128">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="829e7-129">**[選択された主/一意キーまたはインデックス]** ボックスで、名前の変更対象のインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="829e7-129">Select the index you want to rename in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
6.  <span data-ttu-id="829e7-130">グリッド内の **[名前]** をクリックし、テキスト ボックスに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="829e7-130">In the grid, click **Name** and type a new name into the text box.</span></span>  
  
7.  <span data-ttu-id="829e7-131">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="829e7-131">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="829e7-132">**ファイル** メニューの **テーブル名**_の保存_をクリックします。</span><span class="sxs-lookup"><span data-stu-id="829e7-132">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="to-rename-an-index-by-using-object-explorer"></a><span data-ttu-id="829e7-133">オブジェクト エクスプローラーを使用してインデックスの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="829e7-133">To rename an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="829e7-134">オブジェクト エクスプローラーで、インデックスの名前を変更するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="829e7-134">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rename an index.</span></span>  
  
2.  <span data-ttu-id="829e7-135">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="829e7-135">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="829e7-136">プラス記号をクリックして、インデックスの名前を変更するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="829e7-136">Click the plus sign to expand the table on which you want to rename an index.</span></span>  
  
4.  <span data-ttu-id="829e7-137">プラス記号をクリックして **[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="829e7-137">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="829e7-138">名前を変更するインデックスを右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="829e7-138">Right-click the index you want to rename and select **Rename**.</span></span>  
  
6.  <span data-ttu-id="829e7-139">新しいインデックス名を入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="829e7-139">Type the index's new name and press Enter.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="829e7-140">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="829e7-140">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-an-index"></a><span data-ttu-id="829e7-141">インデックスの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="829e7-141">To rename an index</span></span>  
  
1.  <span data-ttu-id="829e7-142">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="829e7-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="829e7-143">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="829e7-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="829e7-144">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="829e7-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Renames the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table to IX_VendorID.   
  
    EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';   
    GO  
    ```  
  
 <span data-ttu-id="829e7-145">詳細については、「[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="829e7-145">For more information, see  [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
