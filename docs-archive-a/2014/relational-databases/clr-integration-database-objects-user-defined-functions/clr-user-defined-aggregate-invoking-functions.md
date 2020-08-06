---
title: CLR ユーザー定義集計関数の呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- aggregate functions [CLR integration]
- invoking user-defined aggregate functions
- user-defined functions [CLR integration]
ms.assetid: 5a188b50-7170-4069-acad-5de5c915f65d
author: rothja
ms.author: jroth
ms.openlocfilehash: 74e92563e01d0065c40619f3208aaf74691496c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641694"
---
# <a name="invoking-clr-user-defined-aggregate-functions"></a><span data-ttu-id="2d252-102">CLR ユーザー定義集計関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="2d252-102">Invoking CLR User-Defined Aggregate Functions</span></span>
  <span data-ttu-id="2d252-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] の SELECT ステートメントでは、CLR (共通言語ランタイム) ユーザー定義集計を呼び出すことができます。CLR ユーザー定義集計には、システム集計関数に適用されるすべての規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2d252-103">In [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statements, you can invoke common language runtime (CLR) user-defined aggregates, subject to all the rules that apply to system aggregate functions.</span></span>  
  
 <span data-ttu-id="2d252-104">さらに、次の規則も適用されます。</span><span class="sxs-lookup"><span data-stu-id="2d252-104">The following additional rules apply:</span></span>  
  
-   <span data-ttu-id="2d252-105">現在のユーザーは、ユーザー定義集計に `EXECUTE` 権限を所持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d252-105">The current user must have `EXECUTE` permission on the user-defined aggregate.</span></span>  
  
-   <span data-ttu-id="2d252-106">ユーザー定義集計は、2つの部分で構成される名前を使用して、 *schema_name udagg_name*の形式で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d252-106">User-defined aggregates must be invoked using a two-part name in the form of *schema_name.udagg_name*.</span></span>  
  
-   <span data-ttu-id="2d252-107">ユーザー定義集計の引数の型は、ステートメントで定義されているように、一致しているか、集計の*input_type*に暗黙的に変換可能である必要があり `CREATE AGGREGATE` ます。</span><span class="sxs-lookup"><span data-stu-id="2d252-107">The argument type of the user-defined aggregate must match or be implicitly convertible to the *input_type* of the aggregate, as defined in the `CREATE AGGREGATE` statement.</span></span>  
  
-   <span data-ttu-id="2d252-108">ユーザー定義集計の戻り値の型は、ステートメントの*return_type*と一致している必要があり `CREATE AGGREGATE` ます。</span><span class="sxs-lookup"><span data-stu-id="2d252-108">The return type of the user-defined aggregate must match the *return_type* in the `CREATE AGGREGATE` statement.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="2d252-109">例 1</span><span class="sxs-lookup"><span data-stu-id="2d252-109">Example 1</span></span>  
 <span data-ttu-id="2d252-110">次の例は、テーブルの列から取得した一連の文字列値を連結するユーザー定義集計関数を示します。</span><span class="sxs-lookup"><span data-stu-id="2d252-110">The following is an example of a user-defined aggregate function that concatenates a set of string values taken from a column in a table:</span></span>  
  
 <span data-ttu-id="2d252-111">[C#]</span><span class="sxs-lookup"><span data-stu-id="2d252-111">[C#]</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
using System.IO;  
using System.Text;  
  
[Serializable]  
[SqlUserDefinedAggregate(  
    Format.UserDefined, //use clr serialization to serialize the intermediate result  
    IsInvariantToNulls = true, //optimizer property  
    IsInvariantToDuplicates = false, //optimizer property  
    IsInvariantToOrder = false, //optimizer property  
    MaxByteSize = 8000) //maximum size in bytes of persisted value  
]  
public class Concatenate : IBinarySerialize  
{  
    /// <summary>  
    /// The variable that holds the intermediate result of the concatenation  
    /// </summary>  
    private StringBuilder intermediateResult;  
  
    /// <summary>  
    /// Initialize the internal data structures  
    /// </summary>  
    public void Init()  
    {  
        this.intermediateResult = new StringBuilder();  
    }  
  
    /// <summary>  
    /// Accumulate the next value, not if the value is null  
    /// </summary>  
    /// <param name="value"></param>  
    public void Accumulate(SqlString value)  
    {  
        if (value.IsNull)  
        {  
            return;  
        }  
  
        this.intermediateResult.Append(value.Value).Append(',');  
    }  
  
    /// <summary>  
    /// Merge the partially computed aggregate with this aggregate.  
    /// </summary>  
    /// <param name="other"></param>  
    public void Merge(Concatenate other)  
    {  
        this.intermediateResult.Append(other.intermediateResult);  
    }  
  
    /// <summary>  
    /// Called at the end of aggregation, to return the results of the aggregation.  
    /// </summary>  
    /// <returns></returns>  
    public SqlString Terminate()  
    {  
        string output = string.Empty;  
        //delete the trailing comma, if any  
        if (this.intermediateResult != null  
            && this.intermediateResult.Length > 0)  
        {  
            output = this.intermediateResult.ToString(0, this.intermediateResult.Length - 1);  
        }  
  
        return new SqlString(output);  
    }  
  
    public void Read(BinaryReader r)  
    {  
        intermediateResult = new StringBuilder(r.ReadString());  
    }  
  
    public void Write(BinaryWriter w)  
    {  
        w.Write(this.intermediateResult.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="2d252-112">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="2d252-112">[Visual Basic]</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.IO  
Imports System.Text  
  
<Serializable(), SqlUserDefinedAggregate(Format.UserDefined, IsInvariantToNulls:=True, IsInvariantToDuplicates:=False, IsInvariantToOrder:=False, MaxByteSize:=8000)> _  
Public Class Concatenate  
    Implements IBinarySerialize  
  
    ''' <summary>  
    ''' The variable that holds the intermediate result of the concatenation  
    ''' </summary>  
    Private intermediateResult As StringBuilder  
  
    ''' <summary>  
    ''' Initialize the internal data structures  
    ''' </summary>  
    Public Sub Init()  
        Me.intermediateResult = New StringBuilder()  
    End Sub  
  
    ''' <summary>  
    ''' Accumulate the next value, not if the value is null  
    ''' </summary>  
    ''' <param name="value"></param>  
    Public Sub Accumulate(ByVal value As SqlString)  
        If value.IsNull Then  
            Return  
        End If  
  
        Me.intermediateResult.Append(value.Value).Append(","c)  
    End Sub  
    ''' <summary>  
    ''' Merge the partially computed aggregate with this aggregate.  
    ''' </summary>  
    ''' <param name="other"></param>  
    Public Sub Merge(ByVal other As Concatenate)  
        Me.intermediateResult.Append(other.intermediateResult)  
    End Sub  
  
    ''' <summary>  
    ''' Called at the end of aggregation, to return the results of the aggregation.  
    ''' </summary>  
    ''' <returns></returns>  
    Public Function Terminate() As SqlString  
        Dim output As String = String.Empty  
  
        'delete the trailing comma, if any  
        If Not (Me.intermediateResult Is Nothing) AndAlso Me.intermediateResult.Length > 0 Then  
            output = Me.intermediateResult.ToString(0, Me.intermediateResult.Length - 1)  
        End If  
  
        Return New SqlString(output)  
    End Function  
  
    Public Sub Read(ByVal r As BinaryReader) Implements IBinarySerialize.Read  
        intermediateResult = New StringBuilder(r.ReadString())  
    End Sub  
  
    Public Sub Write(ByVal w As BinaryWriter) Implements IBinarySerialize.Write  
        w.Write(Me.intermediateResult.ToString())  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="2d252-113">コードをコンパイルして**MyAgg.dll**にすると、次のようにの集計をに登録でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2d252-113">Once you compile the code into **MyAgg.dll**, you can register the aggregate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as follows:</span></span>  
  
```  
CREATE ASSEMBLY MyAgg FROM 'C:\MyAgg.dll';  
GO  
CREATE AGGREGATE MyAgg (@input nvarchar(200)) RETURNS nvarchar(max)  
EXTERNAL NAME MyAgg.Concatenate;  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2d252-114">スカラー値関数など、/clr:pure コンパイラ オプションを指定してコンパイルした Visual C++ のデータベース オブジェクトは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では実行できません。</span><span class="sxs-lookup"><span data-stu-id="2d252-114">Visual C++ database objects, such as scalar-valued functions, that have been compiled with the /clr:pure compiler option are not supported for execution in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2d252-115">多くの集計について言えることですが、ロジックの大半は `Accumulate` メソッドに含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d252-115">As with most aggregates, the bulk of the logic is in the `Accumulate` method.</span></span> <span data-ttu-id="2d252-116">この例では、`Accumulate` メソッドにパラメーターとして渡される文字列は、`StringBuilder` メソッドで初期化された `Init` オブジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2d252-116">Here, the string that is passed in as a parameter to the `Accumulate` method is appended to the `StringBuilder` object that was initialized in the `Init` method.</span></span> <span data-ttu-id="2d252-117">以前にも `Accumulate` メソッドを呼び出しているとすると、`StringBuilder` オブジェクトには、渡された文字列が追加される前に、コンマが追加されます。</span><span class="sxs-lookup"><span data-stu-id="2d252-117">Assuming that this is not the first time the `Accumulate` method has been called, a comma is also appended to the `StringBuilder` prior to appending the passed-in string.</span></span> <span data-ttu-id="2d252-118">計算タスクの最後では、`Terminate` オブジェクトを文字列として返す `StringBuilder` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2d252-118">At the conclusion of the computational tasks, the `Terminate` method is called, which returns the `StringBuilder` as a string.</span></span>  
  
 <span data-ttu-id="2d252-119">たとえば、次のスキーマを持つテーブルについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="2d252-119">For example, consider a table with the following schema:</span></span>  
  
```  
CREATE TABLE BookAuthors  
(  
   BookID   int       NOT NULL,  
   AuthorName    nvarchar(200) NOT NULL  
);  
```  
  
 <span data-ttu-id="2d252-120">このテーブルに次の行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="2d252-120">Then insert the following rows:</span></span>  
  
```  
INSERT BookAuthors VALUES(1, 'Johnson'),(2, 'Taylor'),(3, 'Steven'),(2, 'Mayler'),(3, 'Roberts'),(3, 'Michaels');  
```  
  
 <span data-ttu-id="2d252-121">次のクエリを実行すると、以下のような結果になります。</span><span class="sxs-lookup"><span data-stu-id="2d252-121">The following query would then produce the following result:</span></span>  
  
```  
SELECT BookID, dbo.MyAgg(AuthorName)  
FROM BookAuthors  
GROUP BY BookID;  
```  
  
|<span data-ttu-id="2d252-122">BookID</span><span class="sxs-lookup"><span data-stu-id="2d252-122">BookID</span></span>|<span data-ttu-id="2d252-123">AuthorName</span><span class="sxs-lookup"><span data-stu-id="2d252-123">Author Names</span></span>|  
|------------|------------------|  
|<span data-ttu-id="2d252-124">1</span><span class="sxs-lookup"><span data-stu-id="2d252-124">1</span></span>|<span data-ttu-id="2d252-125">Johnson</span><span class="sxs-lookup"><span data-stu-id="2d252-125">Johnson</span></span>|  
|<span data-ttu-id="2d252-126">2</span><span class="sxs-lookup"><span data-stu-id="2d252-126">2</span></span>|<span data-ttu-id="2d252-127">Taylor, Mayler</span><span class="sxs-lookup"><span data-stu-id="2d252-127">Taylor, Mayler</span></span>|  
|<span data-ttu-id="2d252-128">3</span><span class="sxs-lookup"><span data-stu-id="2d252-128">3</span></span>|<span data-ttu-id="2d252-129">Roberts, Michaels, Steven</span><span class="sxs-lookup"><span data-stu-id="2d252-129">Roberts, Michaels, Steven</span></span>|  
  
## <a name="example-2"></a><span data-ttu-id="2d252-130">例 2</span><span class="sxs-lookup"><span data-stu-id="2d252-130">Example 2</span></span>  
 <span data-ttu-id="2d252-131">次の例では、`Accumulate` メソッドに 2 つのパラメーターを持つ集計を示します。</span><span class="sxs-lookup"><span data-stu-id="2d252-131">The following sample shows an aggregate that has two parameters on the `Accumulate` method.</span></span>  
  
 <span data-ttu-id="2d252-132">[C#]</span><span class="sxs-lookup"><span data-stu-id="2d252-132">[C#]</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
[Serializable]  
[SqlUserDefinedAggregate(  
    Format.Native,  
    IsInvariantToDuplicates = false,  
    IsInvariantToNulls = true,  
    IsInvariantToOrder = true,  
    IsNullIfEmpty = true,  
    Name = "WeightedAvg")]  
public struct WeightedAvg  
{  
    /// <summary>  
    /// The variable that holds the intermediate sum of all values multiplied by their weight  
    /// </summary>  
    private long sum;  
  
    /// <summary>  
    /// The variable that holds the intermediate sum of all weights  
    /// </summary>  
    private int count;  
  
    /// <summary>  
    /// Initialize the internal data structures  
    /// </summary>  
    public void Init()  
    {  
        sum = 0;  
        count = 0;  
    }  
  
    /// <summary>  
    /// Accumulate the next value, not if the value is null  
    /// </summary>  
    /// <param name="Value">Next value to be aggregated</param>  
    /// <param name="Weight">The weight of the value passed to Value parameter</param>  
    public void Accumulate(SqlInt32 Value, SqlInt32 Weight)  
    {  
        if (!Value.IsNull && !Weight.IsNull)  
        {  
            sum += (long)Value * (long)Weight;  
            count += (int)Weight;  
        }  
    }  
  
    /// <summary>  
    /// Merge the partially computed aggregate with this aggregate  
    /// </summary>  
    /// <param name="Group">The other partial results to be merged</param>  
    public void Merge(WeightedAvg Group)  
    {  
        sum += Group.sum;  
        count += Group.count;  
    }  
  
    /// <summary>  
    /// Called at the end of aggregation, to return the results of the aggregation.  
    /// </summary>  
    /// <returns>The weighted average of all inputed values</returns>  
    public SqlInt32 Terminate()  
    {  
        if (count > 0)  
        {  
            int value = (int)(sum / count);  
            return new SqlInt32(value);  
        }  
        else  
        {  
            return SqlInt32.Null;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2d252-133">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="2d252-133">[Visual Basic]</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> _  
<Serializable(), SqlUserDefinedAggregate(Format.Native, _  
IsInvariantToDuplicates:=False, _  
IsInvariantToNulls:=True, _  
IsInvariantToOrder:=True, _  
IsNullIfEmpty:=True, _  
Name:="WeightedAvg")> _  
Public Class WeightedAvg  
  
    ''' <summary>  
    ''' The variable that holds the intermediate sum of all values multiplied by their weight  
    ''' </summary>  
    Private sum As Long  
  
    ''' <summary>  
    ''' The variable that holds the intermediate sum of all weights  
    ''' </summary>  
    Private count As Integer  
  
    ''' <summary>  
    ''' The variable that holds the intermediate sum of all weights  
    ''' </summary>  
    Public Sub Init()  
        sum = 0  
        count = 0  
    End Sub  
  
    ''' <summary>  
    ''' Accumulate the next value, not if the value is null  
    ''' </summary>  
    ''' <param name="Value">Next value to be aggregated</param>  
    ''' <param name="Weight">The weight of the value passed to Value parameter</param>  
    Public Sub Accumulate(ByVal Value As SqlInt32, ByVal Weight As SqlInt32)  
        If Not Value.IsNull AndAlso Not Weight.IsNull Then  
            sum += CType(Value, Long) * CType(Weight, Long)  
            count += CType(Weight, Integer)  
        End If  
    End Sub  
  
    ''' <summary>  
    ''' Merge the partially computed aggregate with this aggregate.  
    ''' </summary>  
    ''' <param name="Group">The other partial results to be merged</param>  
    Public Sub Merge(ByVal Group As WeightedAvg)  
        sum = Group.sum  
        count = Group.count  
    End Sub  
  
    ''' <summary>  
    ''' Called at the end of aggregation, to return the results of the aggregation.  
    ''' </summary>  
    ''' <returns>The weighted average of all inputed values</returns>  
    Public Function Terminate() As SqlInt32  
        If count > 0 Then  
            ''                        int value = (int)(sum / count);  
            ''          return new SqlInt32(value);  
            Dim value As Integer = CType(sum / count, Integer)  
            Return New SqlInt32(value)  
        Else  
            Return SqlInt32.Null  
        End If  
    End Function  
End Class  
```  
  
 <span data-ttu-id="2d252-134">C# または Visual Basic のソース コードをコンパイルした後、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] を実行します。</span><span class="sxs-lookup"><span data-stu-id="2d252-134">After you compile the C# or Visual Basic source code, run the following [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  <span data-ttu-id="2d252-135">このスクリプトでは、C ドライブのルート ディレクトリにある WghtAvg.dll という名前の DLL を想定しています。</span><span class="sxs-lookup"><span data-stu-id="2d252-135">This script assumes that the DLL is called WghtAvg.dll and is in the root directory of your C drive.</span></span>  <span data-ttu-id="2d252-136">また、データベース名は test です。</span><span class="sxs-lookup"><span data-stu-id="2d252-136">A database called test is also assumed.</span></span>  
  
```  
use test;  
go  
  
-- sp_configure 'clr enabled', 1;  
-- go  
  
--- RECONFIGURE WITH OVERRIDE;  
-- go  
  
IF EXISTS (SELECT name FROM systypes WHERE name = 'MyTableType')  
   DROP TYPE MyTableType;  
go  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'WeightedAvg')  
   DROP AGGREGATE WeightedAvg;  
go  
  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'MyClrCode')  
   DROP ASSEMBLY MyClrCode;  
go  
  
CREATE ASSEMBLY MyClrCode FROM 'C:\WghtAvg.dll';  
GO  
  
CREATE AGGREGATE WeightedAvg (@value int, @weight int) RETURNS int  
EXTERNAL NAME MyClrCode.WeightedAvg;  
go  
  
CREATE TYPE MyTableType AS table (ItemValue int, ItemWeight int);  
go  
  
DECLARE @myTable AS MyTableType;  
  
INSERT INTO @myTable VALUES(1, 4), (6, 1);  
  
SELECT dbo.WeightedAvg(ItemValue, ItemWeight) FROM @myTable;  
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d252-137">参照</span><span class="sxs-lookup"><span data-stu-id="2d252-137">See Also</span></span>  
 [<span data-ttu-id="2d252-138">CLR ユーザー定義集計</span><span class="sxs-lookup"><span data-stu-id="2d252-138">CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates.md)  
  
  
