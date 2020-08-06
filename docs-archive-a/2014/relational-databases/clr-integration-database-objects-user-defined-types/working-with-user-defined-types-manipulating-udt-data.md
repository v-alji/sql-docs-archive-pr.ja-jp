---
title: UDT データの操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- data deletions [CLR integration]
- data insertions [CLR integration]
- CONVERT function
- data updates [CLR integration]
- comparing data
- updating data [CLR integration]
- removing data
- IsByteOrdered property
- variables [CLR integration]
- data manipulation [CLR integration]
- user-defined types [CLR integration], data manipulation
- deleting data
- UDTs [CLR integration], data manipulation
- invoking UDT methods
- inserting data
ms.assetid: 51b1a5f2-7591-4e11-bfe2-d88e0836403f
author: rothja
ms.author: jroth
ms.openlocfilehash: 75810a2ffd92130e45025f742d43ba7917d73992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714426"
---
# <a name="manipulating-udt-data"></a><span data-ttu-id="48658-102">UDT データの操作</span><span class="sxs-lookup"><span data-stu-id="48658-102">Manipulating UDT Data</span></span>
  [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="48658-103">には、UDT (ユーザー定義型) 列のデータを変更する際に特別な INSERT、UPDATE、または DELETE ステートメント構文は用意されていません。</span><span class="sxs-lookup"><span data-stu-id="48658-103">provides no specialized syntax for INSERT, UPDATE, or DELETE statements when modifying data in user-defined type (UDT) columns.</span></span> <span data-ttu-id="48658-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] の CAST 関数または CONVERT 関数を使用して、ネイティブ データ型を UDT 型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="48658-104">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST or CONVERT functions are used to cast native data types to the UDT type.</span></span>  
  
## <a name="inserting-data-in-a-udt-column"></a><span data-ttu-id="48658-105">UDT 列へのデータの挿入</span><span class="sxs-lookup"><span data-stu-id="48658-105">Inserting Data in a UDT Column</span></span>  
 <span data-ttu-id="48658-106">次のステートメントでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 3 行のサンプルデータを**Points**テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="48658-106">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements insert three rows of sample data into the **Points** table.</span></span> <span data-ttu-id="48658-107">**Point**データ型は、UDT のプロパティとして公開される X および Y 整数値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="48658-107">The **Point** data type consists of X and Y integer values that are exposed as properties of the UDT.</span></span> <span data-ttu-id="48658-108">コンマ区切りの X 値と Y 値を**Point**型にキャストするには、cast 関数または CONVERT 関数のいずれかを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48658-108">You must use either the CAST or CONVERT function to cast the comma-delimited X and Y values to the **Point** type.</span></span> <span data-ttu-id="48658-109">最初の2つのステートメントでは、CONVERT 関数を使用して文字列値を**Point**型に変換し、3番目のステートメントで CAST 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="48658-109">The first two statements use the CONVERT function to convert a string value to the **Point** type, and the third statement uses the CAST function:</span></span>  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a><span data-ttu-id="48658-110">データの選択</span><span class="sxs-lookup"><span data-stu-id="48658-110">Selecting Data</span></span>  
 <span data-ttu-id="48658-111">次の SELECT ステートメントでは、UDT のバイナリ値を選択します。</span><span class="sxs-lookup"><span data-stu-id="48658-111">The following SELECT statement selects the binary value of the UDT.</span></span>  
  
```  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 <span data-ttu-id="48658-112">出力を判読可能な形式で表示するには、 `ToString` **Point** UDT のメソッドを呼び出します。これにより、値が文字列形式に変換されます。</span><span class="sxs-lookup"><span data-stu-id="48658-112">To see the output displayed in a readable format, call the `ToString` method of the **Point** UDT, which converts the value to its string representation.</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="48658-113">これにより、次の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="48658-113">This produces the following results.</span></span>  
  
```  
IDPointValue  
----------  
13,4  
21,5  
31,99  
```  
  
 <span data-ttu-id="48658-114">また、[!INCLUDE[tsql](../../includes/tsql-md.md)] の CAST 関数や CONVERT 関数を使用して、同じ結果を得ることもできます。</span><span class="sxs-lookup"><span data-stu-id="48658-114">You can also use the [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST and CONVERT functions to achieve the same results.</span></span>  
  
```  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="48658-115">**Point** UDT は、X 座標と Y 座標をプロパティとして公開します。これを個別に選択できます。</span><span class="sxs-lookup"><span data-stu-id="48658-115">The **Point** UDT exposes its X and Y coordinates as properties, which you can then select individually.</span></span> <span data-ttu-id="48658-116">次の、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、X 座標と Y 座標を個別に選択します。</span><span class="sxs-lookup"><span data-stu-id="48658-116">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement selects the X and Y coordinates separately:</span></span>  
  
```  
SELECT ID, PointValue.X AS xVal, PointValue.Y AS yVal   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="48658-117">X プロパティと Y プロパティから整数値が返され、結果セットに表示されます。</span><span class="sxs-lookup"><span data-stu-id="48658-117">The X and Y properties return an integer value, which is displayed in the result set.</span></span>  
  
```  
IDxValyVal  
----------  
134  
215  
3199  
```  
  
## <a name="working-with-variables"></a><span data-ttu-id="48658-118">変数を使用した作業</span><span class="sxs-lookup"><span data-stu-id="48658-118">Working with Variables</span></span>  
 <span data-ttu-id="48658-119">変数を使用するには、DECLARE ステートメントを使用して、UDT 型にその変数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="48658-119">You can work with variables using the DECLARE statement to assign a variable to a UDT type.</span></span> <span data-ttu-id="48658-120">次のステートメントでは、[!INCLUDE[tsql](../../includes/tsql-md.md)] の SET ステートメントを使用して値を代入し、変数に対して UDT の `ToString` メソッドを呼び出すことで結果を表示しています。</span><span class="sxs-lookup"><span data-stu-id="48658-120">The following statements assign a value using the [!INCLUDE[tsql](../../includes/tsql-md.md)] SET statement and display the results by calling the UDT's `ToString` method on the variable:</span></span>  
  
```  
DECLARE @PointValue Point;  
SET @PointValue = (SELECT PointValue FROM dbo.Points  
    WHERE ID = 2);  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 <span data-ttu-id="48658-121">結果セットには、次のように変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48658-121">The result set displays the variable value:</span></span>  
  
```  
PointValue  
----------  
-1,5  
```  
  
 <span data-ttu-id="48658-122">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、変数の代入で SET ステートメントの代わりに SELECT ステートメントを使用して、同じ結果を得ています。</span><span class="sxs-lookup"><span data-stu-id="48658-122">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements achieve the same result using SELECT rather than SET for the variable assignment:</span></span>  
  
```  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 <span data-ttu-id="48658-123">変数の代入に SELECT ステートメントを使用した場合と SET ステートメントを使用した場合には異なる点が 1 つあります。SELECT ステートメントでは 1 つのステートメントで複数の変数に代入できますが、SET 構文では、1 つ変数に代入するごとに 1 つの SET ステートメントが必要になります。</span><span class="sxs-lookup"><span data-stu-id="48658-123">The difference between using SELECT and SET for variable assignment is that SELECT allows you to assign multiple variables in one SELECT statement, whereas the SET syntax requires each variable assignment to have its own SET statement.</span></span>  
  
## <a name="comparing-data"></a><span data-ttu-id="48658-124">データの比較</span><span class="sxs-lookup"><span data-stu-id="48658-124">Comparing Data</span></span>  
 <span data-ttu-id="48658-125">クラスを定義する際に、`IsByteOrdered` プロパティに `true` を設定すると、比較演算子を使用して、UDT の値を比較できます。</span><span class="sxs-lookup"><span data-stu-id="48658-125">You can use comparison operators to compare values in your UDT if you have set the `IsByteOrdered` property to `true` when defining the class.</span></span> <span data-ttu-id="48658-126">詳細については、「[ユーザー定義型の作成](creating-user-defined-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48658-126">For more information, see [Creating a User-Defined Type](creating-user-defined-types.md).</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 <span data-ttu-id="48658-127">値自体が比較できる場合は、`IsByteOrdered` の設定に関係なく、UDT の内部値を比較できます。</span><span class="sxs-lookup"><span data-stu-id="48658-127">You can compare internal values of the UDT regardless of the `IsByteOrdered` setting if the values themselves are comparable.</span></span> <span data-ttu-id="48658-128">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、X の値が Y の値よりも大きい行を選択します。</span><span class="sxs-lookup"><span data-stu-id="48658-128">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement selects rows where X is greater than Y:</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 <span data-ttu-id="48658-129">また、一致する PointValue を検索する次のクエリのように、変数と比較演算子を組み合わせて使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="48658-129">You can also use comparison operators with variables, as shown in this query that searches for a matching PointValue.</span></span>  
  
```  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a><span data-ttu-id="48658-130">UDT メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="48658-130">Invoking UDT Methods</span></span>  
 <span data-ttu-id="48658-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] でも、UDT で定義されているメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="48658-131">You can also invoke methods that are defined in your UDT in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="48658-132">**Point**クラスには、、、およびの3つのメソッドが含まれてい `Distance` `DistanceFrom` `DistanceFromXY` ます。</span><span class="sxs-lookup"><span data-stu-id="48658-132">The **Point** class contains three methods, `Distance`, `DistanceFrom`, and `DistanceFromXY`.</span></span> <span data-ttu-id="48658-133">これら3つのメソッドを定義するコードの一覧については、「[ユーザー定義型のコーディング](creating-user-defined-types-coding.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48658-133">For the code listings defining these three methods, see [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
 <span data-ttu-id="48658-134">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、`PointValue.Distance` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="48658-134">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement calls the `PointValue.Distance` method:</span></span>  
  
```  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="48658-135">結果が列に表示され `Distance` ます。</span><span class="sxs-lookup"><span data-stu-id="48658-135">The results are displayed in the `Distance` column:</span></span>  
  
```  
IDXYDistance  
------------------------  
1345  
2155.09901951359278  
319999.0050503762308  
```  
  
 <span data-ttu-id="48658-136">`DistanceFrom`メソッドは**point**データ型の引数を受け取り、指定されたポイントから pointvalue までの距離を表示します。</span><span class="sxs-lookup"><span data-stu-id="48658-136">The `DistanceFrom` method takes an argument of **Point** data type, and displays the distance from the specified point to the PointValue:</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 <span data-ttu-id="48658-137">結果には、テーブルの行ごとに `DistanceFrom` メソッドの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48658-137">The results display the results of the `DistanceFrom` method for each row in the table:</span></span>  
  
```  
ID PntDistanceFromPoint  
---------------------  
13,495.0210502993942  
21,594  
31,990  
```  
  
 <span data-ttu-id="48658-138">`DistanceFromXY` メソッドでは、Points を引数として個別に受け取ります。</span><span class="sxs-lookup"><span data-stu-id="48658-138">The `DistanceFromXY` method takes the points individually as arguments:</span></span>  
  
```  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 <span data-ttu-id="48658-139">結果セットは、`DistanceFrom` メソッドの場合と同様になります。</span><span class="sxs-lookup"><span data-stu-id="48658-139">The result set is the same as the `DistanceFrom` method.</span></span>  
  
## <a name="updating-data-in-a-udt-column"></a><span data-ttu-id="48658-140">UDT 列のデータの更新</span><span class="sxs-lookup"><span data-stu-id="48658-140">Updating Data in a UDT Column</span></span>  
 <span data-ttu-id="48658-141">UDT 列のデータを更新するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] の UPDATE ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="48658-141">To update data in a UDT column, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE statement.</span></span> <span data-ttu-id="48658-142">また、UDT のメソッドを使用して、オブジェクトの状態を更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="48658-142">You can also use a method of the UDT to update the state of the object.</span></span> <span data-ttu-id="48658-143">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、テーブルの単一行を更新します。</span><span class="sxs-lookup"><span data-stu-id="48658-143">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement updates a single row in the table:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 <span data-ttu-id="48658-144">また、UDT の要素を個別に更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="48658-144">You can also update UDT elements separately.</span></span> <span data-ttu-id="48658-145">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、Y 座標の値のみを更新します。</span><span class="sxs-lookup"><span data-stu-id="48658-145">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement updates only the Y coordinate:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 <span data-ttu-id="48658-146">バイト順序を `true` に設定して UDT が定義されている場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] は WHERE 句でこの UDT 列を評価することができます。</span><span class="sxs-lookup"><span data-stu-id="48658-146">If the UDT has been defined with byte ordering set to `true`, [!INCLUDE[tsql](../../includes/tsql-md.md)] can evaluate the UDT column in a WHERE clause.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a><span data-ttu-id="48658-147">更新の制限事項</span><span class="sxs-lookup"><span data-stu-id="48658-147">Updating Limitations</span></span>  
 <span data-ttu-id="48658-148">[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、複数のプロパティを一度に更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="48658-148">You cannot update multiple properties at once using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="48658-149">たとえば、1 つの UPDATE ステートメントでは同じ列名を 2 回使用することができないため、次のステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="48658-149">For example, the following UPDATE statement fails with an error because you cannot use the same column name twice in one UDATE statement.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 <span data-ttu-id="48658-150">座標の値を個別に更新するには、Point UDT のアセンブリにミューテーター メソッドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48658-150">To update each point individually, you would need to create a mutator method in the Point UDT assembly.</span></span> <span data-ttu-id="48658-151">ミューテーター メソッドを作成すると、[!INCLUDE[tsql](../../includes/tsql-md.md)] の UPDATE ステートメントでミューテーター メソッドを呼び出して、オブジェクトを更新することができます。次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="48658-151">You can then invoke the mutator method to update the object in a [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE statement, as in the following:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a><span data-ttu-id="48658-152">UDT 列のデータの削除</span><span class="sxs-lookup"><span data-stu-id="48658-152">Deleting Data in a UDT Column</span></span>  
 <span data-ttu-id="48658-153">UDT のデータを削除するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] の DELETE ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="48658-153">To delete data in a UDT, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE statement.</span></span> <span data-ttu-id="48658-154">次のステートメントでは、WHERE 句で指定した条件に一致するテーブル内のすべての行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="48658-154">The following statement deletes all rows in the table that match the criteria specified in the WHERE clause.</span></span> <span data-ttu-id="48658-155">DELETE ステートメントで WHERE 句を省略すると、テーブル内のすべての行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="48658-155">If you omit the WHERE clause in a DELETE statement, all rows in the table will be deleted.</span></span>  
  
```  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 <span data-ttu-id="48658-156">UDT 列の値を削除し、それ以外の行の値については現状維持する場合は、UPDATE ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="48658-156">Use the UPDATE statement if you want to remove the values in a UDT column while leaving other row values intact.</span></span> <span data-ttu-id="48658-157">次の例では、PointValue に NULL を設定します。</span><span class="sxs-lookup"><span data-stu-id="48658-157">This example sets the PointValue to null.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a><span data-ttu-id="48658-158">参照</span><span class="sxs-lookup"><span data-stu-id="48658-158">See Also</span></span>  
 [<span data-ttu-id="48658-159">SQL Server でのユーザー定義型の使用</span><span class="sxs-lookup"><span data-stu-id="48658-159">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
  
  
