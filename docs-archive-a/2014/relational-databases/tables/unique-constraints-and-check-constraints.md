---
title: UNIQUE 制約と CHECK 制約 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], Visual Database Tools
- Visual Database Tools [SQL Server], constraints
ms.assetid: 637098af-2567-48f8-90f4-b41df059833e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 205e4ae3d6f89f10a933bf357d1eeda458852584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711805"
---
# <a name="unique-constraints-and-check-constraints"></a><span data-ttu-id="71742-102">UNIQUE 制約と CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="71742-102">Unique Constraints and Check Constraints</span></span>
  <span data-ttu-id="71742-103">UNIQUE 制約と CHECK 制約は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内のデータに整合性を適用するために使用できる 2 種類の制約です。</span><span class="sxs-lookup"><span data-stu-id="71742-103">UNIQUE constraints and CHECK constraints are two types of constraints that can be used to enforce data integrity in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="71742-104">これらは重要なデータベース オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="71742-104">These are important database objects.</span></span>  
  
 <span data-ttu-id="71742-105">このトピックの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="71742-105">This topic contains the following sections.</span></span>  
  
 [<span data-ttu-id="71742-106">UNIQUE 制約</span><span class="sxs-lookup"><span data-stu-id="71742-106">UNIQUE Constraints</span></span>](#Unique)  
  
 [<span data-ttu-id="71742-107">CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="71742-107">CHECK Constraints</span></span>](#Check)  
  
 [<span data-ttu-id="71742-108">関連タスク</span><span class="sxs-lookup"><span data-stu-id="71742-108">Related Tasks</span></span>](#Tasks)  
  
##  <a name="unique-constraints"></a><a name="Unique"></a> <span data-ttu-id="71742-109">UNIQUE 制約</span><span class="sxs-lookup"><span data-stu-id="71742-109">UNIQUE Constraints</span></span>  
 <span data-ttu-id="71742-110">制約とは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によって適用される規則です。</span><span class="sxs-lookup"><span data-stu-id="71742-110">Constraints are rules that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] enforces for you.</span></span> <span data-ttu-id="71742-111">たとえば、UNIQUE 制約を使用して、主キーに関係しない特定の列に重複した値が入力されないようにできます。</span><span class="sxs-lookup"><span data-stu-id="71742-111">For example, you can use UNIQUE constraints to make sure that no duplicate values are entered in specific columns that do not participate in a primary key.</span></span> <span data-ttu-id="71742-112">UNIQUE 制約も PRIMARY KEY 制約も一意性を設定しますが、主キーではない列または列セットに一意性を設定する場合は、PRIMARY KEY 制約ではなく UNIQUE 制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="71742-112">Although both a UNIQUE constraint and a PRIMARY KEY constraint enforce uniqueness, use a UNIQUE constraint instead of a PRIMARY KEY constraint when you want to enforce the uniqueness of a column, or combination of columns, that is not the primary key.</span></span>  
  
 <span data-ttu-id="71742-113">PRIMARY KEY 制約とは異なり、UNIQUE 制約は NULL 値を許容できます。</span><span class="sxs-lookup"><span data-stu-id="71742-113">Unlike PRIMARY KEY constraints, UNIQUE constraints allow for the value NULL.</span></span> <span data-ttu-id="71742-114">ただし、UNIQUE 制約が適用される他の値と同様に、NULL 値も 1 列に 1 つしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="71742-114">However, as with any value participating in a UNIQUE constraint, only one null value is allowed per column.</span></span> <span data-ttu-id="71742-115">UNIQUE 制約は FOREIGN KEY 制約から参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="71742-115">A UNIQUE constraint can be referenced by a FOREIGN KEY constraint.</span></span>  
  
 <span data-ttu-id="71742-116">既定では、テーブルの既存の列に UNIQUE 制約を追加すると、すべての値が一意であることを確認するために、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] により列の既存のデータが調べられます。</span><span class="sxs-lookup"><span data-stu-id="71742-116">When a UNIQUE constraint is added to an existing column or columns in the table, by default, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] examines the existing data in the columns to make sure all values are unique.</span></span> <span data-ttu-id="71742-117">重複した値を含む列に UNIQUE 制約を追加すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によりエラーが返され、制約は追加されません。</span><span class="sxs-lookup"><span data-stu-id="71742-117">If a UNIQUE constraint is added to a column that has duplicated values, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] returns an error and does not add the constraint.</span></span>  
  
 <span data-ttu-id="71742-118">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、UNIQUE 制約による一意性の要件を強制する UNIQUE インデックスを自動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="71742-118">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] automatically creates a UNIQUE index to enforce the uniqueness requirement of the UNIQUE constraint.</span></span> <span data-ttu-id="71742-119">このため、重複した行を挿入しようとすると、UNIQUE 制約に違反していることを示すエラー メッセージが [!INCLUDE[ssDE](../../includes/ssde-md.md)] により返され、テーブルには行が追加されません。</span><span class="sxs-lookup"><span data-stu-id="71742-119">Therefore, if an attempt to insert a duplicate row is made, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] returns an error message that states the UNIQUE constraint has been violated and does not add the row to the table.</span></span> <span data-ttu-id="71742-120">クラスター化インデックスが明示的に指定されていない限り、UNIQUE 制約を強制する一意の非クラスター化インデックスが既定で作成されます。</span><span class="sxs-lookup"><span data-stu-id="71742-120">Unless a clustered index is explicitly specified, a unique, nonclustered index is created by default to enforce the UNIQUE constraint.</span></span>  
  
##  <a name="check-constraints"></a><a name="Check"></a> <span data-ttu-id="71742-121">CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="71742-121">CHECK Constraints</span></span>  
 <span data-ttu-id="71742-122">CHECK 制約は、1 つ以上の列に格納できる値を制限することによってドメインの整合性を強制します。</span><span class="sxs-lookup"><span data-stu-id="71742-122">CHECK constraints enforce domain integrity by limiting the values that are accepted by one or more columns.</span></span> <span data-ttu-id="71742-123">論理演算子に基づいて TRUE または FALSE を返す論理 (ブール) 式を使って CHECK 制約を作成できます。</span><span class="sxs-lookup"><span data-stu-id="71742-123">You can create a CHECK constraint with any logical (Boolean) expression that returns TRUE or FALSE based on the logical operators.</span></span> <span data-ttu-id="71742-124">たとえば、 **salary** 列の値の範囲は、$15,000 ～ $100,000 のデータのみを許容する CHECK 制約を作成することにより制限できます。</span><span class="sxs-lookup"><span data-stu-id="71742-124">For example, the range of values for a **salary** column can be limited by creating a CHECK constraint that allows for only data that ranges from $15,000 through $100,000.</span></span> <span data-ttu-id="71742-125">これにより、この一定の給与範囲を超える給与を入力できなくなります。</span><span class="sxs-lookup"><span data-stu-id="71742-125">This prevents salaries from being entered beyond the regular salary range.</span></span> <span data-ttu-id="71742-126">論理式は、 `salary >= 15000 AND salary <= 100000`になります。</span><span class="sxs-lookup"><span data-stu-id="71742-126">The logical expression would be the following: `salary >= 15000 AND salary <= 100000`.</span></span>  
  
 <span data-ttu-id="71742-127">複数の CHECK 制約を 1 つの列に適用できます。</span><span class="sxs-lookup"><span data-stu-id="71742-127">You can apply multiple CHECK constraints to a single column.</span></span> <span data-ttu-id="71742-128">テーブル レベルで CHECK 制約を作成すると、1 つの CHECK 制約を複数の列に適用できます。</span><span class="sxs-lookup"><span data-stu-id="71742-128">You can also apply a single CHECK constraint to multiple columns by creating it at the table level.</span></span> <span data-ttu-id="71742-129">たとえば、複数列の CHECK 制約を使用して、 **country_region** 列の値が **USA** であるいずれかの行の **state** 列に 2 文字の値が格納されているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="71742-129">For example, a multiple-column CHECK constraint could be used to confirm that any row with a **country_region** column value of **USA** also has a two-character value in the **state** column.</span></span> <span data-ttu-id="71742-130">これにより、1 か所で複数の条件をチェックできるようになります。</span><span class="sxs-lookup"><span data-stu-id="71742-130">This allows for multiple conditions to be checked in one location.</span></span>  
  
 <span data-ttu-id="71742-131">CHECK 制約は、列に格納される値を制御するという点では FOREIGN KEY 制約に似ています。</span><span class="sxs-lookup"><span data-stu-id="71742-131">CHECK constraints are similar to FOREIGN KEY constraints in that they control the values that are put in a column.</span></span> <span data-ttu-id="71742-132">異なる点は、有効な値を決定する方法です。FOREIGN KEY 制約では別のテーブルから有効な値の一覧が取得されますが、CHECK 制約では論理式によって有効な値が決定されます。</span><span class="sxs-lookup"><span data-stu-id="71742-132">The difference is in how they determine which values are valid: FOREIGN KEY constraints obtain the list of valid values from another table, while CHECK constraints determine the valid values from a logical expression.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="71742-133">暗黙的または明示的なデータ型の変換が含まれる制約により、特定の操作が失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="71742-133">Constraints that include implicit or explicit data type conversion may cause certain operations to fail.</span></span> <span data-ttu-id="71742-134">たとえば、パーティションの切り替え元のテーブルに定義された制約により、ALTER TABLE...SWITCH 操作が失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="71742-134">For example, such constraints defined on tables that are sources of partition switching may cause an ALTER TABLE...SWITCH operation to fail.</span></span> <span data-ttu-id="71742-135">制約の定義ではデータ型を変換しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="71742-135">Avoid data type conversion in constraint definitions.</span></span>  
  
### <a name="limitations-of-check-constraints"></a><span data-ttu-id="71742-136">CHECK 制約の制限事項</span><span class="sxs-lookup"><span data-stu-id="71742-136">Limitations of CHECK Constraints</span></span>  
 <span data-ttu-id="71742-137">CHECK 制約は、FALSE と評価された値を拒否します。</span><span class="sxs-lookup"><span data-stu-id="71742-137">CHECK constraints reject values that evaluate to FALSE.</span></span> <span data-ttu-id="71742-138">NULL 値は UNKNOWN と評価されるので、式に NULL 値が含まれていると制約がオーバーライドされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="71742-138">Because null values evaluate to UNKNOWN, their presence in expressions may override a constraint.</span></span> <span data-ttu-id="71742-139">たとえば、列 MyColumn に制約を設定し、 `int` MyColumn **MyColumn**に値 10 **MyColumn** (**MyColumn = 10**) のみを含めることを指定するとします。</span><span class="sxs-lookup"><span data-stu-id="71742-139">For example, suppose you place a constraint on an `int` column **MyColumn** specifying that **MyColumn** can contain only the value 10 (**MyColumn=10**).</span></span> <span data-ttu-id="71742-140">**MyColumn**に値 NULL を挿入すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によって NULL が追加され、エラーは返されません。</span><span class="sxs-lookup"><span data-stu-id="71742-140">If you insert the value NULL into **MyColumn**, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] inserts NULL and does not return an error.</span></span>  
  
 <span data-ttu-id="71742-141">CHECK 制約は、チェックしている条件がテーブルのすべての行に対して FALSE でない場合、TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="71742-141">A CHECK constraint returns TRUE when the condition it is checking is not FALSE for any row in the table.</span></span> <span data-ttu-id="71742-142">CHECK 制約は行レベルで機能します。</span><span class="sxs-lookup"><span data-stu-id="71742-142">A CHECK constraint works at the row level.</span></span> <span data-ttu-id="71742-143">作成したばかりのテーブルに行が含まれていない場合、このテーブルに適用された CHECK 制約は有効であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="71742-143">If a table that has just been created does not have any rows, any CHECK constraint on this table is considered valid.</span></span> <span data-ttu-id="71742-144">この場合、次の例に示すような予期しない結果が生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="71742-144">This situation can produce unexpected results, as in the following example.</span></span>  
  
```  
CREATE TABLE CheckTbl (col1 int, col2 int);  
GO  
CREATE FUNCTION CheckFnctn()  
RETURNS int  
AS   
BEGIN  
   DECLARE @retval int  
   SELECT @retval = COUNT(*) FROM CheckTbl  
   RETURN @retval  
END;  
GO  
ALTER TABLE CheckTbl  
ADD CONSTRAINT chkRowCount CHECK (dbo.CheckFnctn() >= 1 );  
GO  
```  
  
 <span data-ttu-id="71742-145">追加する `CHECK` 制約では、テーブル `CheckTbl`に 1 行以上の行が格納されていなければならないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="71742-145">The `CHECK` constraint being added specifies that there must be at least one row in table `CheckTbl`.</span></span> <span data-ttu-id="71742-146">ただし、テーブルにはこの制約の条件をチェックする行が存在しないので、ALTER TABLE ステートメントは成功します。</span><span class="sxs-lookup"><span data-stu-id="71742-146">However, because there are no rows in the table against which to check the condition of this constraint, the ALTER TABLE statement succeeds.</span></span>  
  
 <span data-ttu-id="71742-147">CHECK 制約では、DELETE ステートメントの実行中は検証されません。</span><span class="sxs-lookup"><span data-stu-id="71742-147">CHECK constraints are not validated during DELETE statements.</span></span> <span data-ttu-id="71742-148">そのため、特定の種類の CHECK 制約が適用されたテーブルで DELETE ステートメントを実行すると、予期しない結果が生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="71742-148">Therefore, executing DELETE statements on tables with certain types of check constraints may produce unexpected results.</span></span> <span data-ttu-id="71742-149">たとえば、テーブル `CheckTbl`で次のステートメントを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="71742-149">For example, consider the following statements executed on table `CheckTbl`.</span></span>  
  
```  
INSERT INTO CheckTbl VALUES (10, 10);  
GO  
DELETE CheckTbl WHERE col1 = 10;  
```  
  
 <span data-ttu-id="71742-150">`CHECK` 制約では、テーブル `CheckTbl` に `1` 行以上が格納されていなければならないことを指定していますが、`DELETE` ステートメントは成功します。</span><span class="sxs-lookup"><span data-stu-id="71742-150">The `DELETE` statement succeeds, even though the `CHECK` constraint specifies that table `CheckTbl` must have at least `1` row.</span></span>  
  
##  <a name="related-tasks"></a><a name="Tasks"></a> <span data-ttu-id="71742-151">関連タスク</span><span class="sxs-lookup"><span data-stu-id="71742-151">Related Tasks</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71742-152">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71742-152">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="71742-153">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="71742-153">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="71742-154">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="71742-154">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
|<span data-ttu-id="71742-155">タスク</span><span class="sxs-lookup"><span data-stu-id="71742-155">Task</span></span>|<span data-ttu-id="71742-156">トピック</span><span class="sxs-lookup"><span data-stu-id="71742-156">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="71742-157">UNIQUE 制約の作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71742-157">Describes how to create a unique constraint.</span></span>|[<span data-ttu-id="71742-158">UNIQUE 制約の作成</span><span class="sxs-lookup"><span data-stu-id="71742-158">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)|  
|<span data-ttu-id="71742-159">UNIQUE 制約の変更方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71742-159">Describes how to modify a unique constraint.</span></span>|[<span data-ttu-id="71742-160">UNIQUE 制約の変更</span><span class="sxs-lookup"><span data-stu-id="71742-160">Modify Unique Constraints</span></span>](../tables/modify-unique-constraints.md)|  
|<span data-ttu-id="71742-161">UNIQUE 制約の削除方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71742-161">Describes how to delete a unique constraint.</span></span>|[<span data-ttu-id="71742-162">UNIQUE 制約の削除</span><span class="sxs-lookup"><span data-stu-id="71742-162">Delete Unique Constraints</span></span>](../tables/delete-unique-constraints.md)|  
|<span data-ttu-id="71742-163">レプリケーション エージェントによってテーブルのデータが挿入または更新された場合に CHECK 制約を無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71742-163">Describes how to disable a check constraint when a replication agent inserts or updates data in your table.</span></span>|[<span data-ttu-id="71742-164">レプリケーションの CHECK 制約の無効化</span><span class="sxs-lookup"><span data-stu-id="71742-164">Disable Check Constraints for Replication</span></span>](../tables/disable-check-constraints-for-replication.md)|  
|<span data-ttu-id="71742-165">テーブルに対してデータの追加、更新、または削除を行う際に、CHECK 制約を無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71742-165">Describes how to disable a check constraint when data is added to, updated in, or deleted from a table.</span></span>|[<span data-ttu-id="71742-166">INSERT ステートメントまたは UPDATE ステートメントによる CHECK 制約の無効化</span><span class="sxs-lookup"><span data-stu-id="71742-166">Disable Check Constraints with INSERT and UPDATE Statements</span></span>](../tables/disable-check-constraints-with-insert-and-update-statements.md)|  
|<span data-ttu-id="71742-167">制約式を変更するか、または特定条件の制約を有効または無効にするオプションを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71742-167">Describes how to change the constraint expression or the options that enable or disable the constraint for specific conditions.</span></span>|[<span data-ttu-id="71742-168">CHECK 制約の変更</span><span class="sxs-lookup"><span data-stu-id="71742-168">Modify Check Constraints</span></span>](../tables/modify-check-constraints.md)|  
|<span data-ttu-id="71742-169">CHECK 制約の削除方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71742-169">Describes how to delete a check constraint.</span></span>|[<span data-ttu-id="71742-170">CHECK 制約の削除</span><span class="sxs-lookup"><span data-stu-id="71742-170">Delete Check Constraints</span></span>](../tables/delete-check-constraints.md)|  
|<span data-ttu-id="71742-171">CHECK 制約のプロパティを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71742-171">Describes how to view the properties of a check constraint.</span></span>|[<span data-ttu-id="71742-172">UNIQUE 制約と CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="71742-172">Unique Constraints and Check Constraints</span></span>](../tables/unique-constraints-and-check-constraints.md)|  
  
  
