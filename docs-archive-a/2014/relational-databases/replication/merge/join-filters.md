---
title: 結合フィルター | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- publications [SQL Server replication], join filters
- merge replication join filters [SQL Server replication]
- join filters
ms.assetid: dd78fd8f-56e3-4582-9abd-6bc25c91e075
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b97e7d7b53e6a3fdb242d1272e013bbd45f0ed17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630948"
---
# <a name="join-filters"></a><span data-ttu-id="eb6b7-102">結合フィルター</span><span class="sxs-lookup"><span data-stu-id="eb6b7-102">Join Filters</span></span>
  <span data-ttu-id="eb6b7-103">結合フィルターを使用すると、パブリケーションにおける関連するテーブルのフィルター方法に基づいて、テーブルにフィルターを適用できます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-103">A join filter allows a table to be filtered based on how a related table in the publication is filtered.</span></span> <span data-ttu-id="eb6b7-104">通常、親テーブルにはパラメーター化されたフィルターが使用されます。そのため、テーブル間の結合を定義する場合とほぼ同じ方法で 1 つ以上の結合フィルターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-104">Typically a parent table is filtered using a parameterized filter; then one or more join filters are defined in much the same way that you define a join between tables.</span></span> <span data-ttu-id="eb6b7-105">結合フィルターは、結合フィルター句に一致した場合のみ関連テーブルのデータがレプリケートされるように、パラメーター化されたフィルターを拡張します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-105">The join filters extend the parameterized filter so that the data in the related tables is only replicated if it matches the join filter clause.</span></span>  
  
 <span data-ttu-id="eb6b7-106">通常、結合フィルターは適用先のテーブルに定義されている主キー/外部キーのリレーションシップに従いますが、これに厳密に限定されてはいません。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-106">Join filters typically follow the primary key/foreign key relationships defined for the tables to which they are applied, but they are not limited strictly to primary key/foreign key relationships.</span></span> <span data-ttu-id="eb6b7-107">結合フィルターには、2 つのテーブルの関連データを比較するためのあらゆるロジックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-107">The join filter can be based on any logic that compares related data in two tables.</span></span>  
  
 <span data-ttu-id="eb6b7-108">[!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] サンプル データベースの次のテーブルを検討してみましょう。これらのテーブルは主キーと外部キーのリレーションシップによって関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-108">Consider the following tables in the [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] sample database, which are related through primary key to foreign key relationships:</span></span>  
  
-   <span data-ttu-id="eb6b7-109">**HumanResources.Employee**</span><span class="sxs-lookup"><span data-stu-id="eb6b7-109">**HumanResources.Employee**</span></span>  
  
-   <span data-ttu-id="eb6b7-110">**Sales.SalesOrderHeader**</span><span class="sxs-lookup"><span data-stu-id="eb6b7-110">**Sales.SalesOrderHeader**</span></span>  
  
-   <span data-ttu-id="eb6b7-111">**Sales.SalesOrderDetail**</span><span class="sxs-lookup"><span data-stu-id="eb6b7-111">**Sales.SalesOrderDetail**</span></span>  
  
 <span data-ttu-id="eb6b7-112">これらのテーブルは、移動営業部門を支援するアプリケーションで利用できます。ただし、 **HumanResources.Employee** テーブルの各営業担当者が担当顧客の注文に関連するデータのみを受け取れるように、これらのテーブルをフィルター選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-112">These tables could be used in an application to support a mobile sales force, but they must be filtered so that each sales person in the **HumanResources.Employee** table receives only the data relevant to their customers' orders.</span></span>  
  
 <span data-ttu-id="eb6b7-113">最初に、親テーブルに対してパラメーター化されたフィルターを定義します。この例では、 **HumanResources.Employee** が親テーブルになります。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-113">The first step is to define a parameterized filter on the parent table, which in this example is the **HumanResources.Employee** table.</span></span> <span data-ttu-id="eb6b7-114">このテーブルには **LoginID**列が含まれており、この列には各従業員のログインが *domain\login*形式で格納されています。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-114">This table includes the column **LoginID**, which contains the login for each employee in the form *domain\login*.</span></span> <span data-ttu-id="eb6b7-115">このテーブルにフィルターを適用して各従業員が関連データのみを受け取れるようにするには、パラメーター化されたフィルター句を次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-115">To filter this table so that each employee receives only the data related to them, specify a parameterized filter clause of:</span></span>  
  
```  
LoginID = SUSER_SNAME()  
```  
  
 <span data-ttu-id="eb6b7-116">このフィルターを指定すると、各従業員のサブスクリプションには、当該従業員に関連する **HumanResources.Employee** テーブルのデータのみ (この例では単一の行) が格納されます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-116">This filter ensures that each employee's subscription only contains data from the **HumanResources.Employee** table that is relevant to that employee (which in this case is a single row).</span></span> <span data-ttu-id="eb6b7-117">詳しくは、「 [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-117">For more information, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="eb6b7-118">次の手順で、このフィルターを各関連テーブルに拡張します。フィルターの拡張に使用する構文は、2 つのテーブルの結合の指定に使用する構文とほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-118">The next step is to extend this filter to each of the related tables, using syntax similar to that used to specify a join between two tables.</span></span> <span data-ttu-id="eb6b7-119">最初の結合フィルター句を次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-119">The first join filter clause is:</span></span>  
  
```  
Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
```  
  
 <span data-ttu-id="eb6b7-120">この指定により、各営業担当者に関連する注文データのみがサブスクリプションに格納されます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-120">This ensures the subscription contains only the order data relevant to each sales person.</span></span> <span data-ttu-id="eb6b7-121">2 つ目の結合フィルター句を次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-121">The second join filter clause is:</span></span>  
  
```  
SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
```  
  
 <span data-ttu-id="eb6b7-122">この指定により、各営業担当者の注文データに関連する詳細データのみがサブスクリプションに格納されます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-122">This ensures the subscription contains only the detail data related to the order data for each sales person.</span></span> <span data-ttu-id="eb6b7-123">この例では、各ポイントで単一のテーブルが結合されていますが、複数のテーブルを結合することもできます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-123">This example shows a single table being joined at each point; it is also possible to join more than one table at each point.</span></span>  
  
 <span data-ttu-id="eb6b7-124">結合フィルターはパブリケーションの新規作成ウィザードと **[パブリケーションのプロパティ]** ダイアログ ボックスで 1 つずつ追加したり、プログラムを使用して追加することができます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-124">Join filters can be added one at a time through the New Publication Wizard and the **Publication Properties** dialog box, or they can be added programmatically.</span></span> <span data-ttu-id="eb6b7-125">パブリケーションの新規作成ウィザードを使用して結合フィルターを自動的に生成することもできます。このウィザードでテーブルの行フィルターを指定すると、すべての関連テーブルに対して結合フィルターが適用されます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-125">They can also be generated automatically through the New Publication Wizard: you specify a row filter for a table and join filters are applied to all related tables.</span></span> <span data-ttu-id="eb6b7-126">詳細については、「[マージ アーティクル間の結合フィルターの定義および変更](../publish/define-and-modify-a-join-filter-between-merge-articles.md)」、「[Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](../publish/automatically-generate-join-filters-between-merge-articles.md)」 (マージ アーティクル間の一連の結合フィルターを自動的に生成する &#40;SQL Server Management Studio&#41;)、および「[Define an Article](../publish/define-an-article.md)」 (アーティクルの定義) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-126">For more information, see [Define and Modify a Join Filter Between Merge Articles](../publish/define-and-modify-a-join-filter-between-merge-articles.md), [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](../publish/automatically-generate-join-filters-between-merge-articles.md), and [Define an Article](../publish/define-an-article.md).</span></span>  
  
## <a name="optimizing-join-filter-performance"></a><span data-ttu-id="eb6b7-127">結合フィルターのパフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="eb6b7-127">Optimizing Join Filter Performance</span></span>  
 <span data-ttu-id="eb6b7-128">次のガイドラインに従うことにより、結合フィルターのパフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-128">Join filter performance can be optimized by following these guidelines:</span></span>  
  
-   <span data-ttu-id="eb6b7-129">結合フィルター階層のテーブル数を制限します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-129">Limit the number of tables in the join filter hierarchy.</span></span>  
  
     <span data-ttu-id="eb6b7-130">結合フィルターを適用できるテーブル数に制限はありませんが、多数のテーブルにフィルターを適用すると、マージ処理中のパフォーマンスに大きく影響します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-130">Join Filters can involve an unlimited number of tables, but filters with a large number of tables can significantly impact performance during merge processing.</span></span> <span data-ttu-id="eb6b7-131">テーブルが 5 つ以上の結合フィルターを生成する場合は、小さなテーブル、変更されないテーブル、プライマリ参照テーブルはフィルター選択しないという別の解決策を検討してください。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-131">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="eb6b7-132">結合フィルターは、サブスクリプション間でパーティション分割する必要のあるテーブル間でのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-132">Use join filters only between tables that must be partitioned among subscriptions.</span></span>  
  
-   <span data-ttu-id="eb6b7-133">必要に応じて **join unique key** オプションを **True** に設定します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-133">Set the **join unique key** option to **True** where appropriate.</span></span>  
  
     <span data-ttu-id="eb6b7-134">親テーブルの結合列が一意の場合、特別なパフォーマンスの最適化機能をマージ処理で利用できます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-134">The merge process has special performance optimizations available if the joined column in the parent is unique.</span></span> <span data-ttu-id="eb6b7-135">一意な列に基づいて結合条件が指定されている場合、結合フィルターの **join unique key** オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-135">If the join condition is based on a unique column, set the **join unique key** option for the join filter.</span></span> <span data-ttu-id="eb6b7-136">このオプション設定の詳細については、前のセクションに示されている操作方法のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-136">For information about setting this option, see the how-to topics listed in the previous section.</span></span>  
  
-   <span data-ttu-id="eb6b7-137">結合フィルターで参照される列にインデックスが作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-137">Ensure that the columns referenced in join filters are indexed.</span></span>  
  
     <span data-ttu-id="eb6b7-138">結合フィルターで参照される列にインデックスを作成すると、レプリケーションのフィルター処理がより効率的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-138">If the columns referenced in the filter are indexed, replication can process the filters more efficiently.</span></span>  
  
-   <span data-ttu-id="eb6b7-139">結合フィルターと同様の処理をする行フィルターは作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-139">Do not create row filters that mimic join filters.</span></span>  
  
     <span data-ttu-id="eb6b7-140">WHERE 句にサブクエリを使用すると、結合フィルターと同様の処理の行フィルターを次のように作成できます。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-140">It is possible to create row filters that mimic join filters by using a subquery in a WHERE clause, such as:</span></span>  
  
    ```  
    WHERE Customer.SalesPersonID IN (SELECT EmployeeID FROM Employee WHERE LoginID = SUSER_SNAME())   
    ```  
  
     <span data-ttu-id="eb6b7-141">上記のようなロジックを使用する場合、サブクエリではなく結合フィルターを使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-141">It is strongly recommended that all such logic be expressed in a join filter rather than a subquery.</span></span> <span data-ttu-id="eb6b7-142">アプリケーションでサブクエリを使用する行フィルターが必要な場合は、サブクエリが参照するデータが変更されない読み取り専用データであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="eb6b7-142">If your application requires a row filter to use a subsquery, ensure that the subquery only references lookup data that does not change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6b7-143">参照</span><span class="sxs-lookup"><span data-stu-id="eb6b7-143">See Also</span></span>  
 <span data-ttu-id="eb6b7-144">[マージ レプリケーション用にパブリッシュされたデータのフィルター処理](filter-published-data-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="eb6b7-144">[Filter Published Data for Merge Replication](filter-published-data-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="eb6b7-145">パラメーター化された行フィルター</span><span class="sxs-lookup"><span data-stu-id="eb6b7-145">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  
