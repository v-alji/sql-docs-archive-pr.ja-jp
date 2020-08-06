---
title: テーブルのデータの挿入と更新 (チュートリアル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserting and updating data
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0646019f166e1c2cc126a4cc7d2ed8f27a7bd2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642440"
---
# <a name="inserting-and-updating-data-in-a-table-tutorial"></a><span data-ttu-id="8bc2a-102">テーブルのデータの挿入と更新 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="8bc2a-102">Inserting and Updating Data in a Table (Tutorial)</span></span>
  <span data-ttu-id="8bc2a-103">**Products** テーブルを作成したので、INSERT ステートメントを使用してデータをテーブルに挿入する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-103">Now that you have created the **Products** table, you are ready to insert data into the table by using the INSERT statement.</span></span> <span data-ttu-id="8bc2a-104">データを挿入した後は、UPDATE ステートメントを使用して行の内容を変更します。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-104">After the data is inserted, you will change the content of a row by using an UPDATE statement.</span></span> <span data-ttu-id="8bc2a-105">更新を 1 つの行に制限するには、UPDATE ステートメントの WHERE 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-105">You will use the WHERE clause of the UPDATE statement to restrict the update to a single row.</span></span> <span data-ttu-id="8bc2a-106">4 つのステートメントによって、次のデータが入力されます。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-106">The four statements will enter the following data.</span></span>  
  
|<span data-ttu-id="8bc2a-107">ProductID</span><span class="sxs-lookup"><span data-stu-id="8bc2a-107">ProductID</span></span>|<span data-ttu-id="8bc2a-108">ProductName</span><span class="sxs-lookup"><span data-stu-id="8bc2a-108">ProductName</span></span>|<span data-ttu-id="8bc2a-109">Price</span><span class="sxs-lookup"><span data-stu-id="8bc2a-109">Price</span></span>|<span data-ttu-id="8bc2a-110">ProductDescription</span><span class="sxs-lookup"><span data-stu-id="8bc2a-110">ProductDescription</span></span>|  
|---------------|-----------------|-----------|------------------------|  
|<span data-ttu-id="8bc2a-111">1</span><span class="sxs-lookup"><span data-stu-id="8bc2a-111">1</span></span>|<span data-ttu-id="8bc2a-112">Clamp</span><span class="sxs-lookup"><span data-stu-id="8bc2a-112">Clamp</span></span>|<span data-ttu-id="8bc2a-113">12.48</span><span class="sxs-lookup"><span data-stu-id="8bc2a-113">12.48</span></span>|<span data-ttu-id="8bc2a-114">Workbench clamp</span><span class="sxs-lookup"><span data-stu-id="8bc2a-114">Workbench clamp</span></span>|  
|<span data-ttu-id="8bc2a-115">50</span><span class="sxs-lookup"><span data-stu-id="8bc2a-115">50</span></span>|<span data-ttu-id="8bc2a-116">Screwdriver</span><span class="sxs-lookup"><span data-stu-id="8bc2a-116">Screwdriver</span></span>|<span data-ttu-id="8bc2a-117">3.17</span><span class="sxs-lookup"><span data-stu-id="8bc2a-117">3.17</span></span>|<span data-ttu-id="8bc2a-118">Flat head</span><span class="sxs-lookup"><span data-stu-id="8bc2a-118">Flat head</span></span>|  
|<span data-ttu-id="8bc2a-119">75</span><span class="sxs-lookup"><span data-stu-id="8bc2a-119">75</span></span>|<span data-ttu-id="8bc2a-120">Tire Bar</span><span class="sxs-lookup"><span data-stu-id="8bc2a-120">Tire Bar</span></span>||<span data-ttu-id="8bc2a-121">Tool for changing tires</span><span class="sxs-lookup"><span data-stu-id="8bc2a-121">Tool for changing tires.</span></span>|  
|<span data-ttu-id="8bc2a-122">3000</span><span class="sxs-lookup"><span data-stu-id="8bc2a-122">3000</span></span>|<span data-ttu-id="8bc2a-123">3mm Bracket</span><span class="sxs-lookup"><span data-stu-id="8bc2a-123">3mm Bracket</span></span>|<span data-ttu-id="8bc2a-124">.52</span><span class="sxs-lookup"><span data-stu-id="8bc2a-124">.52</span></span>||  
  
 <span data-ttu-id="8bc2a-125">基本的な構文は、INSERT、テーブル名、列一覧、VALUES、および挿入する値の一覧です。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-125">The basic syntax is: INSERT, table name, column list, VALUES, and then a list of the values to be inserted.</span></span> <span data-ttu-id="8bc2a-126">行の先頭にある 2 つのハイフンは、その行がコメントであることを示します。この行のテキストはコンパイラによって無視されます。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-126">The two hyphens in front of a line indicate that the line is a comment and the text will be ignored by the compiler.</span></span> <span data-ttu-id="8bc2a-127">この場合、コメントは構文に許可されているバリエーションを記述します。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-127">In this case, the comment describes a permissible variation of the syntax.</span></span>  
  
### <a name="to-insert-data-into-a-table"></a><span data-ttu-id="8bc2a-128">データをテーブルに挿入するには</span><span class="sxs-lookup"><span data-stu-id="8bc2a-128">To insert data into a table</span></span>  
  
1.  <span data-ttu-id="8bc2a-129">次のステートメントを実行し、前のタスクで作成した `Products` テーブルに行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-129">Execute the following statement to insert a row into the `Products` table that was created in the previous task.</span></span> <span data-ttu-id="8bc2a-130">これは基本構文です。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-130">This is the basic syntax.</span></span>  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  <span data-ttu-id="8bc2a-131">次のステートメントは、フィールド一覧 (かっこ内) と値一覧の両方にある `ProductID` と `ProductName` の配置を交換することで、パラメーターの順序を変更する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-131">The following statement shows how you can change the order in which the parameters are provided by switching the placement of the `ProductID` and `ProductName` in both the field list (in parentheses) and in the values list.</span></span>  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  <span data-ttu-id="8bc2a-132">次のステートメントは、値が正しい順序で示されている限り、列の名前はオプションであることを示しています。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-132">The following statement demonstrates that the names of the columns are optional, as long as the values are listed in the correct order.</span></span> <span data-ttu-id="8bc2a-133">この構文は一般的ですが、他のユーザーがコードを理解しにくいため、推奨されません。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-133">This syntax is common but is not recommended because it might be harder for others to understand your code.</span></span> <span data-ttu-id="8bc2a-134">`NULL` が `Price` 列に指定されているのは、この製品の価格が不明ためです。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-134">`NULL` is specified for the `Price` column because the price for this product is not yet known.</span></span>  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  <span data-ttu-id="8bc2a-135">スキーマ名は、既定のスキーマ内のテーブルにアクセスし、変更している場合にはオプションです。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-135">The schema name is optional as long as you are accessing and changing a table in your default schema.</span></span> <span data-ttu-id="8bc2a-136">`ProductDescription` 列では NULL 値が許可されており、値が提供されていないため、 `ProductDescription` 列の名前と値はステートメントから完全に省略できます。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-136">Because the `ProductDescription` column allows null values and no value is being provided, the `ProductDescription` column name and value can be dropped from the statement completely.</span></span>  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### <a name="to-update-the-products-table"></a><span data-ttu-id="8bc2a-137">Products テーブルを更新するには</span><span class="sxs-lookup"><span data-stu-id="8bc2a-137">To update the products table</span></span>  
  
1.  <span data-ttu-id="8bc2a-138">次の `UPDATE` ステートメントを入力して実行し、2 番目の製品の `ProductName` を `Screwdriver`から `Flat Head Screwdriver`に変更します。</span><span class="sxs-lookup"><span data-stu-id="8bc2a-138">Type and execute the following `UPDATE` statement to change the `ProductName` of the second product from `Screwdriver`, to `Flat Head Screwdriver`.</span></span>  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8bc2a-139">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="8bc2a-139">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8bc2a-140">テーブルのデータの読み取り (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="8bc2a-140">Reading the Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-4-reading-the-data-in-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="8bc2a-141">参照</span><span class="sxs-lookup"><span data-stu-id="8bc2a-141">See Also</span></span>  
 <span data-ttu-id="8bc2a-142">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8bc2a-142">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 [<span data-ttu-id="8bc2a-143">UPDATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8bc2a-143">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
