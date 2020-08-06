---
title: シーケンス番号 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sequence number object, overview
- sequence [Database Engine]
- autonumbers, sequences
- sequence numbers [SQL Server]
- sequence number object
ms.assetid: c900e30d-2fd3-4d5f-98ee-7832f37e79d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6c65b4df915a85cf0ec7c7c0c8c0ff9f6607ad96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741686"
---
# <a name="sequence-numbers"></a><span data-ttu-id="e64ce-102">シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="e64ce-102">Sequence Numbers</span></span>
  <span data-ttu-id="e64ce-103">シーケンスは、シーケンスが作成された仕様に従って数値のシーケンスを生成するユーザー定義のスキーマ バインド オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e64ce-103">A sequence is a user-defined schema-bound object that generates a sequence of numeric values according to the specification with which the sequence was created.</span></span> <span data-ttu-id="e64ce-104">数値のシーケンスは、定義された間隔で昇順または降順に生成され、要求に応じて繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-104">The sequence of numeric values is generated in an ascending or descending order at a defined interval and may cycle (repeat) as requested.</span></span> <span data-ttu-id="e64ce-105">ID 列とは異なり、シーケンスはテーブルには関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="e64ce-105">Sequences, unlike identity columns, are not associated with tables.</span></span> <span data-ttu-id="e64ce-106">アプリケーションは、シーケンス オブジェクトを参照して、次の値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e64ce-106">An application refers to a sequence object to receive its next value.</span></span> <span data-ttu-id="e64ce-107">シーケンスとテーブルの関係は、アプリケーションによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-107">The relationship between sequences and tables is controlled by the application.</span></span> <span data-ttu-id="e64ce-108">ユーザー アプリケーションは、シーケンス オブジェクトを参照し、複数の行およびテーブルにわたって値キーを調整できます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-108">User applications can reference a sequence object and coordinate the values keys across multiple rows and tables.</span></span>  
  
 <span data-ttu-id="e64ce-109">シーケンスは、テーブルとは別に、 **CREATE SEQUENCE** ステートメントを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-109">A sequence is created independently of the tables by using the **CREATE SEQUENCE** statement.</span></span> <span data-ttu-id="e64ce-110">オプションを使用することにより、増分、最大値、最小値、始点、自動再開機能、およびパフォーマンスを向上させるためのキャッシュ動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-110">Options enable you to control the increment, maximum and minimum values, starting point, automatic restarting capability, and caching to improve performance.</span></span> <span data-ttu-id="e64ce-111">オプションの詳細については、 [「CREATE SEQUENCE」](/sql/t-sql/statements/create-sequence-transact-sql)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e64ce-111">For information about the options, see [CREATE SEQUENCE](/sql/t-sql/statements/create-sequence-transact-sql).</span></span>  
  
 <span data-ttu-id="e64ce-112">行の挿入時に生成される ID 列値とは異なり、アプリケーションは、 [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) 関数を呼び出すことにより、行を挿入する前に次のシーケンス番号を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-112">Unlike identity column values, which are generated when rows are inserted, an application can obtain the next sequence number before inserting the row by calling the [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) function.</span></span> <span data-ttu-id="e64ce-113">番号がテーブルに挿入されない場合でも、シーケンス番号は、NEXT VALUE FOR が呼び出されたときに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-113">The sequence number is allocated when NEXT VALUE FOR is called even if the number is never inserted into a table.</span></span> <span data-ttu-id="e64ce-114">NEXT VALUE FOR 関数は、テーブル定義内の列の既定値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-114">The NEXT VALUE FOR function can be used as the default value for a column in a table definition.</span></span> <span data-ttu-id="e64ce-115">一度に複数のシーケンス番号の範囲を取得するには、 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-115">Use [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) to get a range of multiple sequence numbers at once.</span></span>  
  
 <span data-ttu-id="e64ce-116">シーケンスは、任意の整数データ型として定義できます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-116">A sequence can be defined as any integer data type.</span></span> <span data-ttu-id="e64ce-117">シーケンスのデータ型を指定しなかった場合、既定で `bigint` 型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-117">If the data type is not specified, a sequence defaults to `bigint`.</span></span>  
  
## <a name="using-sequences"></a><span data-ttu-id="e64ce-118">シーケンスの使用</span><span class="sxs-lookup"><span data-stu-id="e64ce-118">Using Sequences</span></span>  
 <span data-ttu-id="e64ce-119">シーケンスは、次のシナリオで ID 列の代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-119">Use sequences instead of identity columns in the following scenarios:</span></span>  
  
-   <span data-ttu-id="e64ce-120">テーブルへの挿入を行う前に、アプリケーションが数値を必要とする。</span><span class="sxs-lookup"><span data-stu-id="e64ce-120">The application requires a number before the insert into the table is made.</span></span>  
  
-   <span data-ttu-id="e64ce-121">アプリケーションが、複数のテーブル間またはテーブル内の複数の列間で、単一の番号シリーズを共有する必要がある。</span><span class="sxs-lookup"><span data-stu-id="e64ce-121">The application requires sharing a single series of numbers between multiple tables or multiple columns within a table.</span></span>  
  
-   <span data-ttu-id="e64ce-122">指定した番号に達したときに、アプリケーションが番号シリーズを再開する必要がある。</span><span class="sxs-lookup"><span data-stu-id="e64ce-122">The application must restart the number series when a specified number is reached.</span></span> <span data-ttu-id="e64ce-123">たとえば、1 ～ 10 の値を割り当てた後、アプリケーションは再び 1 ～ 10 の値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-123">For example, after assigning values 1 through 10, the application starts assigning values 1 through 10 again.</span></span>  
  
-   <span data-ttu-id="e64ce-124">アプリケーションが、シーケンス値を別のフィールドで並べ替える必要がある。</span><span class="sxs-lookup"><span data-stu-id="e64ce-124">The application requires sequence values to be sorted by another field.</span></span> <span data-ttu-id="e64ce-125">NEXT VALUE FOR 関数は、OVER 句を関数呼び出しに適用できます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-125">The NEXT VALUE FOR function can apply the OVER clause to the function call.</span></span> <span data-ttu-id="e64ce-126">OVER 句によって、返される値は OVER 句の ORDER BY 句の順で生成されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-126">The OVER clause guarantees that the values returned are generated in the order of the OVER clause's ORDER BY clause.</span></span>  
  
-   <span data-ttu-id="e64ce-127">アプリケーションが、同時に複数の番号を割り当てる必要がある。</span><span class="sxs-lookup"><span data-stu-id="e64ce-127">An application requires multiple numbers to be assigned at the same time.</span></span> <span data-ttu-id="e64ce-128">たとえば、アプリケーションで 5 つの連続する番号を予約する必要がある場合などです。</span><span class="sxs-lookup"><span data-stu-id="e64ce-128">For example, an application needs to reserve five sequential numbers.</span></span> <span data-ttu-id="e64ce-129">ID 値を要求したときに他のプロセスが番号を同時に発行していた場合、非連続的な ID 値が生成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e64ce-129">Requesting identity values could result in gaps in the series if other processes were simultaneously issued numbers.</span></span> <span data-ttu-id="e64ce-130">sp_sequence_get_range を呼び出すことにより、シーケンス内の番号を一度に取得できます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-130">Calling sp_sequence_get_range can retrieve several numbers in the sequence at once.</span></span>  
  
-   <span data-ttu-id="e64ce-131">増分値など、シーケンスの仕様を変更する必要がある。</span><span class="sxs-lookup"><span data-stu-id="e64ce-131">You need to change the specification of the sequence, such as the increment value.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="e64ce-132">制限事項</span><span class="sxs-lookup"><span data-stu-id="e64ce-132">Limitations</span></span>  
 <span data-ttu-id="e64ce-133">値を変更できない ID 列とは異なり、シーケンス値はテーブルへの挿入後に自動的に保護されません。</span><span class="sxs-lookup"><span data-stu-id="e64ce-133">Unlike identity columns, whose values cannot be changed, sequence values are not automatically protected after insertion into the table.</span></span> <span data-ttu-id="e64ce-134">シーケンス値が変更されるのを防止するには、テーブルで更新トリガーを使用して、変更をロールバックします。</span><span class="sxs-lookup"><span data-stu-id="e64ce-134">To prevent sequence values from being changed, use an update trigger on the table to roll back changes.</span></span>  
  
 <span data-ttu-id="e64ce-135">シーケンス値に対して、一意性は自動的には適用されません。</span><span class="sxs-lookup"><span data-stu-id="e64ce-135">Uniqueness is not automatically enforced for sequence values.</span></span> <span data-ttu-id="e64ce-136">シーケンス値を再利用する機能は仕様です。</span><span class="sxs-lookup"><span data-stu-id="e64ce-136">The ability to reuse sequence values is by design.</span></span> <span data-ttu-id="e64ce-137">テーブルのシーケンス値が一意の値になる必要がある場合は、列に一意なインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-137">If sequence values in a table are required to be unique, create a unique index on the column.</span></span> <span data-ttu-id="e64ce-138">テーブルのグループ全体でテーブルのシーケンス値が一意になる必要がある場合は、更新ステートメントやシーケンス番号の循環によって発生する重複を防ぐためのトリガーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-138">If sequence values in a table are required to be unique throughout a group of tables, create triggers to prevent duplicates caused by update statements or sequence number cycling.</span></span>  
  
 <span data-ttu-id="e64ce-139">シーケンス オブジェクトは、定義に従って番号を生成しますが、その番号がどのように使用されるかについては制御しません。</span><span class="sxs-lookup"><span data-stu-id="e64ce-139">The sequence object generates numbers according to its definition, but the sequence object does not control how the numbers are used.</span></span> <span data-ttu-id="e64ce-140">トランザクションがロールバックされたとき、シーケンス オブジェクトが複数のテーブルで共有されているとき、またはテーブルのシーケンス番号を使用することなくシーケンス番号が割り当てられたときは、非連続的なシーケンス番号がテーブルに挿入される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e64ce-140">Sequence numbers inserted into a table can have gaps when a transaction is rolled back, when a sequence object is shared by multiple tables, or when sequence numbers are allocated without using them in tables.</span></span> <span data-ttu-id="e64ce-141">CACHE オプションを使用してシーケンス番号を作成する際に予期しないシャットダウン (電源障害など) が発生すると、キャッシュ内のシーケンス番号が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e64ce-141">When created with the CACHE option, an unexpected shutdown, such as a power failure, can lose the sequence numbers in the cache.</span></span>  
  
 <span data-ttu-id="e64ce-142">1 つの [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメント内で同じシーケンス ジェネレーターを指定する `NEXT VALUE FOR` 関数のインスタンスが複数ある場合、これらすべてのインスタンスは、その [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントによって処理される特定の行について同じ値を返します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-142">If there are multiple instances of the `NEXT VALUE FOR` function specifying the same sequence generator within a single [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, all those instances return the same value for a given row processed by that [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="e64ce-143">この動作は、ANSI 標準と一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="e64ce-143">This behavior is consistent with the ANSI standard.</span></span>  
  
## <a name="typical-use"></a><span data-ttu-id="e64ce-144">一般的な用途</span><span class="sxs-lookup"><span data-stu-id="e64ce-144">Typical Use</span></span>  
 <span data-ttu-id="e64ce-145">-2,147,483,648 ～ 2,147,483,647 まで 1 ずつ増分される整数のシーケンス番号を作成するには、次のステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-145">To create an integer sequence number that increments by 1 from -2,147,483,648 to 2,147,483,647, use the following statement.</span></span>  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    INCREMENT BY 1 ;  
```  
  
 <span data-ttu-id="e64ce-146">ID 列のように 1 ～ 2,147,483,647 まで 1 ずつ増分される整数のシーケンス番号を作成するには、次のステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-146">To create an integer sequence number similar to an identity column that increments by 1 from 1 to 2,147,483,647, use the following statement.</span></span>  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
  
```  
  
## <a name="managing-sequences"></a><span data-ttu-id="e64ce-147">シーケンスの管理</span><span class="sxs-lookup"><span data-stu-id="e64ce-147">Managing Sequences</span></span>  
 <span data-ttu-id="e64ce-148">シーケンスの詳細については、「 [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e64ce-148">For information about sequences, query [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e64ce-149">例</span><span class="sxs-lookup"><span data-stu-id="e64ce-149">Examples</span></span>  
 <span data-ttu-id="e64ce-150">関連する例については、「[CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql)」、「[NEXT VALUE FOR &#40;Transact-SQL&#41;](/sql/t-sql/functions/next-value-for-transact-sql)」、および「[sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e64ce-150">There are additional examples in the topics [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql), [NEXT VALUE FOR &#40;Transact-SQL&#41;](/sql/t-sql/functions/next-value-for-transact-sql), and [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql).</span></span>  
  
### <a name="a-using-a-sequence-number-in-a-single-table"></a><span data-ttu-id="e64ce-151">A.</span><span class="sxs-lookup"><span data-stu-id="e64ce-151">A.</span></span> <span data-ttu-id="e64ce-152">1 つのテーブルでシーケンス番号を使用する</span><span class="sxs-lookup"><span data-stu-id="e64ce-152">Using a sequence number in a single table</span></span>  
 <span data-ttu-id="e64ce-153">次の例では、Test という名前のスキーマ、Orders という名前のテーブル、および CountBy1 という名前のシーケンスを作成した後、NEXT VALUE FOR 関数を使用してテーブルに行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-153">The following example creates a schema named Test, a table named Orders, and a sequence named CountBy1, and then inserts rows into the table using the NEXT VALUE FOR function.</span></span>  
  
```  
--Create the Test schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Orders  
    (OrderID int PRIMARY KEY,  
    Name varchar(20) NOT NULL,  
    Qty int NOT NULL);  
GO  
  
-- Create a sequence  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
-- Insert three records  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Tire', 2) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Seat', 1) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Brake', 1) ;  
GO  
  
-- View the table  
SELECT * FROM Test.Orders ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `OrderID  Name    Qty`  
  
 `1        Tire    2`  
  
 `2        Seat    1`  
  
 `3        Brake   1`  
  
### <a name="b-calling-next-value-for-before-inserting-a-row"></a><span data-ttu-id="e64ce-154">B.</span><span class="sxs-lookup"><span data-stu-id="e64ce-154">B.</span></span> <span data-ttu-id="e64ce-155">行を挿入する前に NEXT VALUE FOR を呼び出す</span><span class="sxs-lookup"><span data-stu-id="e64ce-155">Calling NEXT VALUE FOR before inserting a row</span></span>  
 <span data-ttu-id="e64ce-156">次の例では、例 A で作成した `Orders` テーブルを使用して、 `@nextID`という名前の変数を宣言します。次に、NEXT VALUE FOR 関数を使用して、この変数を、次に使用できるシーケンス番号に設定します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-156">Using the `Orders` table created in example A, the following example declares a variable named `@nextID`, and then uses the NEXT VALUE FOR function to set the variable to the next available sequence number.</span></span> <span data-ttu-id="e64ce-157">アプリケーションは、潜在的な注文の `OrderID` 番号を顧客に提示した後、注文を確認するなど、注文に関する処理を行うものと考えられます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-157">The application is presumed to do some processing of the order, such as providing the customer with the `OrderID` number of their potential order, and then validates the order.</span></span> <span data-ttu-id="e64ce-158">この処理にどれだけの時間がかかろうとも、またこの処理中に他の注文がいくつ追加されようとも、この接続によって元の番号は保持されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-158">No matter how long this processing might take, or how many other orders are added during the process, the original number is preserved for use by this connection.</span></span> <span data-ttu-id="e64ce-159">最後に、 `INSERT` ステートメントによって注文が `Orders` テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-159">Finally, the `INSERT` statement adds the order to the `Orders` table.</span></span>  
  
```  
DECLARE @NextID int ;  
SET @NextID = NEXT VALUE FOR Test.CountBy1;  
-- Some work happens  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (@NextID, 'Rim', 2) ;  
GO  
  
```  
  
### <a name="c-using-a-sequence-number-in-multiple-tables"></a><span data-ttu-id="e64ce-160">C.</span><span class="sxs-lookup"><span data-stu-id="e64ce-160">C.</span></span> <span data-ttu-id="e64ce-161">複数のテーブルでシーケンス番号を使用する</span><span class="sxs-lookup"><span data-stu-id="e64ce-161">Using a sequence number in multiple tables</span></span>  
 <span data-ttu-id="e64ce-162">次の例では、生産ラインの監視プロセスが、ワークショップ全体で発生するイベントの通知を受信すると仮定します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-162">This example assumes that a production-line monitoring process receives notification of events that occur throughout the workshop.</span></span> <span data-ttu-id="e64ce-163">各イベントは、単調に増加する一意な `EventID` 番号を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e64ce-163">Each event receives a unique and monotonically increasing `EventID` number.</span></span> <span data-ttu-id="e64ce-164">すべてのイベントは、同じ `EventID` シーケンス番号を使用します。したがって、すべてのイベントが集約されたレポートで、それぞれのイベントを一意に識別できます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-164">All events use the same `EventID` sequence number so that reports that combine all events can uniquely identify each event.</span></span> <span data-ttu-id="e64ce-165">ただし、イベント データは、イベントの種類に応じて、3 つの異なるテーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-165">However the event data is stored in three different tables, depending on the type of event.</span></span> <span data-ttu-id="e64ce-166">このコード例では、 `Audit`という名前のスキーマ、 `EventCounter`という名前のシーケンス、およびそれぞれが `EventCounter` シーケンスを既定値として使用する 3 つのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-166">The code example creates a schema named `Audit`, a sequence named `EventCounter`, and three tables which each use the `EventCounter` sequence as a default value.</span></span> <span data-ttu-id="e64ce-167">次に、3 つのテーブルに行を追加し、クエリを実行して結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-167">Then the example adds rows to the three tables and queries the results.</span></span>  
  
```  
CREATE SCHEMA Audit ;  
GO  
CREATE SEQUENCE Audit.EventCounter  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
CREATE TABLE Audit.ProcessEvents  
(  
    EventID int PRIMARY KEY CLUSTERED   
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EventCode nvarchar(5) NOT NULL,  
    Description nvarchar(300) NULL  
) ;  
GO  
  
CREATE TABLE Audit.ErrorEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NULL,  
    ErrorNumber int NOT NULL,  
    EventDesc nvarchar(256) NULL  
) ;  
GO  
  
CREATE TABLE Audit.StartStopEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NOT NULL,  
    StartOrStop bit NOT NULL  
) ;  
GO  
  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 0) ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (72, 0) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (2735,   
    'Clean room temperature 18 degrees C.') ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (18, 'Spin rate threashold exceeded.') ;  
INSERT Audit.ErrorEvents (EquipmentID, ErrorNumber, EventDesc)   
    VALUES (248, 82, 'Feeder jam') ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 1) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (1841, 'Central feed in bypass mode.') ;  
-- The following statement combines all events, though not all fields.  
SELECT EventID, EventTime, Description FROM Audit.ProcessEvents   
UNION SELECT EventID, EventTime, EventDesc FROM Audit.ErrorEvents   
UNION SELECT EventID, EventTime,   
CASE StartOrStop   
    WHEN 0 THEN 'Start'   
    ELSE 'Stop'  
END   
FROM Audit.StartStopEvents  
ORDER BY EventID ;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `EventID  EventTime                Description`  
  
 `1        2009-11-02 15:00:51.157  Start`  
  
 `2        2009-11-02 15:00:51.160  Start`  
  
 `3        2009-11-02 15:00:51.167  Clean room temperature 18 degrees C.`  
  
 `4        2009-11-02 15:00:51.167  Spin rate threshold exceeded.`  
  
 `5        2009-11-02 15:00:51.173  Feeder jam`  
  
 `6        2009-11-02 15:00:51.177  Stop`  
  
 `7        2009-11-02 15:00:51.180  Central feed in bypass mode.`  
  
### <a name="d-generating-repeating-sequence-numbers-in-a-result-set"></a><span data-ttu-id="e64ce-168">D.</span><span class="sxs-lookup"><span data-stu-id="e64ce-168">D.</span></span> <span data-ttu-id="e64ce-169">結果セットで循環するシーケンス番号を生成する</span><span class="sxs-lookup"><span data-stu-id="e64ce-169">Generating repeating sequence numbers in a result set</span></span>  
 <span data-ttu-id="e64ce-170">次の例は、シーケンス番号に関する 2 つの機能を示しています。これらは、サイクル処理の機能と、SELECT ステートメントで `NEXT VALUE FOR` を使用した機能です。</span><span class="sxs-lookup"><span data-stu-id="e64ce-170">The following example demonstrates two features of sequence numbers: cycling, and using `NEXT VALUE FOR` in a select statement.</span></span>  
  
```  
CREATE SEQUENCE CountBy5  
   AS tinyint  
    START WITH 1  
    INCREMENT BY 1  
    MINVALUE 1  
    MAXVALUE 5  
    CYCLE ;  
GO  
  
SELECT NEXT VALUE FOR CountBy5 AS SurveyGroup, Name FROM sys.objects ;  
GO  
```  
  
### <a name="e-generating-sequence-numbers-for-a-result-set-by-using-the-over-clause"></a><span data-ttu-id="e64ce-171">E.</span><span class="sxs-lookup"><span data-stu-id="e64ce-171">E.</span></span> <span data-ttu-id="e64ce-172">OVER 句を使用して結果セットのシーケンス番号を生成する</span><span class="sxs-lookup"><span data-stu-id="e64ce-172">Generating sequence numbers for a result set by using the OVER clause</span></span>  
 <span data-ttu-id="e64ce-173">次の例では、結果セットをシーケンス番号列に追加する前に、 `OVER` 句を使用して `Name` の順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-173">The following example uses the `OVER` clause to sort the result set by `Name` before it adds the sequence number column.</span></span>  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Samples ;  
GO  
  
CREATE SEQUENCE Samples.IDLabel  
    AS tinyint  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="f-resetting-the-sequence-number"></a><span data-ttu-id="e64ce-174">F.</span><span class="sxs-lookup"><span data-stu-id="e64ce-174">F.</span></span> <span data-ttu-id="e64ce-175">シーケンス番号をリセットする</span><span class="sxs-lookup"><span data-stu-id="e64ce-175">Resetting the sequence number</span></span>  
 <span data-ttu-id="e64ce-176">例 E では、`Samples.IDLabel` のシーケンス番号の最初の 79 個の番号が使用されました </span><span class="sxs-lookup"><span data-stu-id="e64ce-176">Example E consumed the first 79 of the `Samples.IDLabel` sequence numbers.</span></span> <span data-ttu-id="e64ce-177">( `AdventureWorks2012` のバージョンによっては結果の数が異なる場合があります)。次のコードを実行すると、後続の 79 個のシーケンス番号 (80 ～ 158) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-177">(Your version of `AdventureWorks2012` may return a different number of results.) Execute the following to consume the next 79 sequence numbers (80 though 158).</span></span>  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
 <span data-ttu-id="e64ce-178">次のステートメントを実行すると、`Samples.IDLabel` シーケンスが最初から開始されます。</span><span class="sxs-lookup"><span data-stu-id="e64ce-178">Execute the following statement to restart the `Samples.IDLabel` sequence.</span></span>  
  
```  
ALTER SEQUENCE Samples.IDLabel  
RESTART WITH 1 ;  
```  
  
 <span data-ttu-id="e64ce-179">再び SELECT ステートメントを実行して、 `Samples.IDLabel` シーケンス番号が 1 から開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-179">Execute the select statement again to verify that the `Samples.IDLabel` sequence restarted with number 1.</span></span>  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="g-changing-a-table-from-identity-to-sequence"></a><span data-ttu-id="e64ce-180">G.</span><span class="sxs-lookup"><span data-stu-id="e64ce-180">G.</span></span> <span data-ttu-id="e64ce-181">ID からシーケンスにテーブルを変更する</span><span class="sxs-lookup"><span data-stu-id="e64ce-181">Changing a table from identity to sequence</span></span>  
 <span data-ttu-id="e64ce-182">次の例では、1 つのスキーマと、サンプルの 3 つの行が含まれたテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-182">The following example creates a schema and table containing three rows for the example.</span></span> <span data-ttu-id="e64ce-183">次に、新しい列を追加し、古い列を削除します。</span><span class="sxs-lookup"><span data-stu-id="e64ce-183">Then the example adds a new column and drops the old column.</span></span>  
  
```  
-- Create a schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Department  
    (  
        DepartmentID smallint IDENTITY(1,1) NOT NULL,  
        Name nvarchar(100) NOT NULL,  
        GroupName nvarchar(100) NOT NULL  
    CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC)   
    ) ;  
GO  
  
-- Insert three rows into the table  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Engineering', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Tool Design', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Sales', 'Sales and Marketing');  
GO  
  
-- View the table that will be changed  
SELECT * FROM Test.Department ;  
GO  
  
-- End of portion creating a sample table  
--------------------------------------------------------  
-- Add the new column that does not have the IDENTITY property  
ALTER TABLE Test.Department   
    ADD DepartmentIDNew smallint NULL  
GO  
  
-- Copy values from the old column to the new column  
UPDATE Test.Department  
    SET DepartmentIDNew = DepartmentID ;  
GO  
  
-- Drop the primary key constraint on the old column  
ALTER TABLE Test.Department  
    DROP CONSTRAINT [PK_Department_DepartmentID];  
-- Drop the old column  
ALTER TABLE Test.Department  
    DROP COLUMN DepartmentID ;  
GO  
  
-- Rename the new column to the old columns name  
EXEC sp_rename 'Test.Department.DepartmentIDNew',   
    'DepartmentID', 'COLUMN';  
GO  
  
-- Change the new column to NOT NULL  
ALTER TABLE Test.Department  
    ALTER COLUMN DepartmentID smallint NOT NULL ;  
-- Add the unique primary key constraint  
ALTER TABLE Test.Department  
    ADD CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC) ;  
-- Get the highest current value from the DepartmentID column   
-- and create a sequence to use with the column. (Returns 3.)  
SELECT MAX(DepartmentID) FROM Test.Department ;  
-- Use the next desired value (4) as the START WITH VALUE;  
CREATE SEQUENCE Test.DeptSeq  
    AS smallint  
    START WITH 4  
    INCREMENT BY 1 ;  
GO  
  
-- Add a default value for the DepartmentID column  
ALTER TABLE Test.Department  
    ADD CONSTRAINT DefSequence DEFAULT (NEXT VALUE FOR Test.DeptSeq)   
        FOR DepartmentID;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;   
-- Test insert  
INSERT Test.Department (Name, GroupName)  
    VALUES ('Audit', 'Quality Assurance') ;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;  
GO  
  
```  
  
 <span data-ttu-id="e64ce-184">`SELECT *` を使用する [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、最初の列としてではなく最後の列として、新しい列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e64ce-184">[!INCLUDE[tsql](../../../includes/tsql-md.md)] statements that use `SELECT *` will receive the new column as the last column instead of the first column.</span></span> <span data-ttu-id="e64ce-185">この動作を許容できない場合は、新しいテーブルを作成してデータをそこに移動した後、新しいテーブルに対する権限を再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e64ce-185">If this is not acceptable, then you must create an entirely new table, move the data to it, and then recreate the permissions on the new table.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="e64ce-186">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e64ce-186">Related Content</span></span>  
 [<span data-ttu-id="e64ce-187">CREATE SEQUENCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e64ce-187">CREATE SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-sequence-transact-sql)  
  
 [<span data-ttu-id="e64ce-188">ALTER SEQUENCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e64ce-188">ALTER SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-sequence-transact-sql)  
  
 [<span data-ttu-id="e64ce-189">DROP SEQUENCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e64ce-189">DROP SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-sequence-transact-sql)  
  
 [<span data-ttu-id="e64ce-190">IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e64ce-190">IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql-identity-property)  
  
  
