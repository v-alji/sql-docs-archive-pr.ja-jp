---
title: ユーザー定義型のコーディング |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e88c4d8162e5c7c921f5c5062f5b3c23df40a2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633175"
---
# <a name="coding-user-defined-types"></a><span data-ttu-id="e8b92-102">ユーザー定義型のコーディング</span><span class="sxs-lookup"><span data-stu-id="e8b92-102">Coding User-Defined Types</span></span>
  <span data-ttu-id="e8b92-103">ユーザー定義型 (UDT) の定義をコーディングする際は、形式やシリアル化のオプションを選択するだけでなく、UDT をクラスと構造体のどちらで実装するかによって、さまざまな機能を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-103">When coding your user-defined type (UDT) definition, you must implement various features, depending on whether you are implementing the UDT as a class or a structure, as well as on the format and serialization options you have chosen.</span></span>  
  
 <span data-ttu-id="e8b92-104">このセクションの例では、`Point` UDT を `struct` (Visual Basic では `Structure`) として実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-104">The example in this section illustrates implementing a `Point` UDT as a `struct` (or `Structure` in Visual Basic).</span></span> <span data-ttu-id="e8b92-105">`Point` UDT は、プロパティ プロシージャとして実装される X 座標と Y 座標から構成されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-105">The `Point` UDT consists of X and Y coordinates implemented as property procedures.</span></span>  
  
 <span data-ttu-id="e8b92-106">UDT の定義に必要な名前空間を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-106">The following namespaces are required when defining a UDT:</span></span>  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 <span data-ttu-id="e8b92-107">`Microsoft.SqlServer.Server` 名前空間には、UDT のさまざまな属性に必要なオブジェクトが含まれています。また、`System.Data.SqlTypes` 名前空間には、アセンブリに使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ データ型を表すクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e8b92-107">The `Microsoft.SqlServer.Server` namespace contains the objects required for various attributes of your UDT, and the `System.Data.SqlTypes` namespace contains the classes that represent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types available to the assembly.</span></span> <span data-ttu-id="e8b92-108">それ以外にもアセンブリが正しく機能するために必要な名前空間が存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-108">There may of course be additional namespaces that your assembly requires in order to function correctly.</span></span> <span data-ttu-id="e8b92-109">`Point` UDT は、文字列用の `System.Text` 名前空間も使用します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-109">The `Point` UDT also uses the `System.Text` namespace for working with strings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8b92-110">`/clr:pure` を指定してコンパイルした Visual C++ のデータベース オブジェクト (UDT など) は実行できません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-110">Visual C++ database objects, such as UDTs, compiled with `/clr:pure` are not supported for execution.</span></span>  
  
## <a name="specifying-attributes"></a><span data-ttu-id="e8b92-111">属性の指定</span><span class="sxs-lookup"><span data-stu-id="e8b92-111">Specifying Attributes</span></span>  
 <span data-ttu-id="e8b92-112">UDT のストレージ表現を構築し、クライアントに UDT を値として転送するためにシリアル化を使用する方法は、属性で決まります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-112">Attributes determine how serialization is used to construct the storage representation of UDTs and to transmit UDTs by value to the client.</span></span>  
  
 <span data-ttu-id="e8b92-113">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` は必須です。</span><span class="sxs-lookup"><span data-stu-id="e8b92-113">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` is required.</span></span> <span data-ttu-id="e8b92-114">`Serializable` 属性は省略できます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-114">The `Serializable` attribute is optional.</span></span> <span data-ttu-id="e8b92-115">また、`Microsoft.SqlServer.Server.SqlFacetAttribute` を指定して、UDT の戻り値の型に関する情報を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-115">You can also specify the `Microsoft.SqlServer.Server.SqlFacetAttribute` to provide information about the return type of a UDT.</span></span> <span data-ttu-id="e8b92-116">詳細については、「[CLR ルーチンのカスタム属性](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8b92-116">For more information, see [Custom Attributes for CLR Routines](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).</span></span>  
  
### <a name="point-udt-attributes"></a><span data-ttu-id="e8b92-117">Point UDT の属性</span><span class="sxs-lookup"><span data-stu-id="e8b92-117">Point UDT Attributes</span></span>  
 <span data-ttu-id="e8b92-118">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` の `Point` UDT のストレージ形式は `Native` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-118">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` sets the storage format for the `Point` UDT to `Native`.</span></span> <span data-ttu-id="e8b92-119">`IsByteOrdered` は `true` に設定します。これにより、SQL Server の比較結果がマネージド コードの比較結果と等しくなります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-119">`IsByteOrdered` is set to `true`, which guarantees that the results of comparisons are the same in SQL Server as if the same comparison had taken place in managed code.</span></span> <span data-ttu-id="e8b92-120">さらに、この UDT に `System.Data.SqlTypes.INullable` インターフェイスを実装し、NULL に対応できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e8b92-120">The UDT implements the `System.Data.SqlTypes.INullable` interface to make the UDT null aware.</span></span>  
  
 <span data-ttu-id="e8b92-121">次のコードに `Point` UDT の属性を示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-121">The following code fragment shows the attributes for the `Point` UDT.</span></span>  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a><span data-ttu-id="e8b92-122">NULL 値の許容属性の実装</span><span class="sxs-lookup"><span data-stu-id="e8b92-122">Implementing Nullability</span></span>  
 <span data-ttu-id="e8b92-123">アセンブリの属性を正しく指定することに加えて、UDT で NULL 値の許容属性をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-123">In addition to specifying the attributes for your assemblies correctly, your UDT must also support nullability.</span></span> <span data-ttu-id="e8b92-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込まれる UDT は NULL 値に対応していますが、UDT に NULL 値を認識させるには、UDT に `System.Data.SqlTypes.INullable` インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-124">UDTs loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are null-aware, but in order for the UDT to recognize a null value, the UDT must implement the `System.Data.SqlTypes.INullable` interface.</span></span>  
  
 <span data-ttu-id="e8b92-125">CLR コード内から値が NULL かどうかを判断するのに必要な `IsNull` というプロパティを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-125">You must create a property named `IsNull`, which is needed to determine whether a value is null from within CLR code.</span></span> <span data-ttu-id="e8b92-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では UDT が NULL インスタンスであることを検出すると、通常の NULL 値処理メソッドを使用して UDT を保存します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finds a null instance of a UDT, the UDT is persisted using normal null-handling methods.</span></span> <span data-ttu-id="e8b92-127">そのため、サーバーが NULL の UDT の不要なシリアル化やシリアル化解除に時間を費やしたり、NULL の UDT を格納して領域を無駄にすることはありません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-127">The server does not waste time serializing or deserializing the UDT if it does not have to, and it does not waste space to store a null UDT.</span></span> <span data-ttu-id="e8b92-128">この NULL に関するチェックは CLR から UDT が渡されるたびに実行されます。つまり、[!INCLUDE[tsql](../../includes/tsql-md.md)] の IS NULL コンストラクトを使用して NULL UDT のチェックを実行すると、必ず成功することを意味します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-128">This check for nulls is performed every time a UDT is brought over from the CLR, which means that using the [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL construct to check for null UDTs should always work.</span></span> <span data-ttu-id="e8b92-129">また、`IsNull` プロパティは、インスタンスが NULL かどうかをテストするためにサーバーでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-129">The `IsNull` property is also used by the server to test whether an instance is null.</span></span> <span data-ttu-id="e8b92-130">UDT が NULL であることを判断できれば、サーバーはネイティブの NULL 処理を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-130">Once the server determines that the UDT is null, it can use its native null handling.</span></span>  
  
 <span data-ttu-id="e8b92-131">`get()` の `IsNull` メソッドは決して特殊なケースではありません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-131">The `get()` method of `IsNull` is not special-cased in any way.</span></span> <span data-ttu-id="e8b92-132">`Point` の `@p` 変数が `Null` の場合、`@p.IsNull` は既定で、"1" ではなく "NULL" と評価されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-132">If a `Point` variable `@p` is `Null`, then `@p.IsNull` will, by default, evaluate to "NULL", not "1".</span></span> <span data-ttu-id="e8b92-133">これは、`SqlMethod(OnNullCall)` メソッドの `IsNull get()` 属性が既定で False であるためです。</span><span class="sxs-lookup"><span data-stu-id="e8b92-133">This is because the `SqlMethod(OnNullCall)` attribute of the `IsNull get()` method defaults to false.</span></span> <span data-ttu-id="e8b92-134">オブジェクトが `Null` であるため、プロパティを要求したときには、オブジェクトがシリアル化解除されることもメソッドが呼び出されることもなく、既定値の "NULL" が返されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-134">Because the object is `Null`, when the property is requested the object is not deserialized, the method is not called, and a default value of "NULL" is returned.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e8b92-135">例</span><span class="sxs-lookup"><span data-stu-id="e8b92-135">Example</span></span>  
 <span data-ttu-id="e8b92-136">次の例では、プライベート変数の `is_Null` に、UDT のインスタンスが NULL かどうかに関する状態が格納されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-136">In the following example, the `is_Null` variable is private and holds the state of null for the instance of the UDT.</span></span> <span data-ttu-id="e8b92-137">コードを作成する際は、`is_Null` の値を適切な状態に保つように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-137">Your code must maintain an appropriate value for `is_Null`.</span></span> <span data-ttu-id="e8b92-138">また、UDT の NULL 値のインスタンスを返す `Null` という静的プロパティを UDT に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-138">The UDT must also have a static property named `Null` that returns a null value instance of the UDT.</span></span> <span data-ttu-id="e8b92-139">これにより、データベース内の UDT のインスタンスが実際に NULL の場合に、UDT から NULL 値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-139">This allows the UDT to return a null value if the instance is indeed null in the database.</span></span>  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a><span data-ttu-id="e8b92-140">IS NULL と IsNull</span><span class="sxs-lookup"><span data-stu-id="e8b92-140">IS NULL vs. IsNull</span></span>  
 <span data-ttu-id="e8b92-141">Points(id int, location Point) というスキーマ (`Point` は CLR UDT) を含むテーブルと次のクエリを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-141">Consider a table that contains the schema Points(id int, location Point), where `Point` is a CLR UDT, and the following queries:</span></span>  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 <span data-ttu-id="e8b92-142">これらのクエリは、location が `Null` ではない Points の ID を返します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-142">Both queries return the IDs of points with non-`Null` locations.</span></span> <span data-ttu-id="e8b92-143">クエリ 1 では、通常の Null 処理が使用されるため、UDT のシリアル化解除は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-143">In Query 1, normal null-handling is used, and there no deserialization of UDTs is required.</span></span> <span data-ttu-id="e8b92-144">一方、クエリ 2 では、`Null` プロパティの値を取得するために、`IsNull` でないオブジェクトをすべてシリアル化解除し、CLR を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-144">Query 2, on the other hand, has to deserialize each non-`Null` object and call into the CLR to obtain the value of the `IsNull` property.</span></span> <span data-ttu-id="e8b92-145">`IS NULL` を使用する方が明らかにパフォーマンスがよく、UDT の `IsNull` プロパティを [!INCLUDE[tsql](../../includes/tsql-md.md)] コードから読み取らなければならない理由はまったくありません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-145">Clearly, using `IS NULL` will exhibit better performance and there should never be a reason to read the `IsNull` property of a UDT from [!INCLUDE[tsql](../../includes/tsql-md.md)] code.</span></span>  
  
 <span data-ttu-id="e8b92-146">では、何のために `IsNull` プロパティを使用するのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e8b92-146">So, what is the use of the `IsNull` property?</span></span> <span data-ttu-id="e8b92-147">1 つ目の理由は、値が `Null` かどうかを CLR コード内から判断するために必要だということです。</span><span class="sxs-lookup"><span data-stu-id="e8b92-147">First, it is needed to determine whether a value is `Null` from within CLR code.</span></span> <span data-ttu-id="e8b92-148">2 つ目の理由は、インスタンスが `Null` かどうかをテストするための手段として、サーバーがこのプロパティを使用するためです。</span><span class="sxs-lookup"><span data-stu-id="e8b92-148">Second, the server needs a way to test whether an instance is `Null`, so this property is used by the server.</span></span> <span data-ttu-id="e8b92-149">インスタンスが `Null` であることを判断できれば、サーバーはネイティブの NULL 処理を使用してこのインスタンスを処理できます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-149">After it determines it is `Null`, then it can use its native null handling to handle it.</span></span>  
  
## <a name="implementing-the-parse-method"></a><span data-ttu-id="e8b92-150">Parse メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="e8b92-150">Implementing the Parse Method</span></span>  
 <span data-ttu-id="e8b92-151">`Parse` メソッドと `ToString` メソッドを使用すると、UDT を文字列形式に変換したり、文字列形式から別の形式に変換できます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-151">The `Parse` and `ToString` methods allow for conversions to and from string representations of the UDT.</span></span> <span data-ttu-id="e8b92-152">`Parse` メソッドでは、文字列を UDT に変換できます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-152">The `Parse` method allows a string to be converted into a UDT.</span></span> <span data-ttu-id="e8b92-153">このメソッドは `static` (Visual Basic では `Shared`) メソッドとして宣言され、`System.Data.SqlTypes.SqlString` 型のパラメーターを受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-153">It must be declared as `static` (or `Shared` in Visual Basic), and take a parameter of type `System.Data.SqlTypes.SqlString`.</span></span>  
  
 <span data-ttu-id="e8b92-154">次のコードでは、`Parse` UDT の `Point` メソッドを実装します。このメソッドでは、X 座標と Y 座標を分離します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-154">The following code implements the `Parse` method for the `Point` UDT, which separates out the X and Y coordinates.</span></span> <span data-ttu-id="e8b92-155">`Parse` メソッドには `System.Data.SqlTypes.SqlString` 型の引数が 1 つあり、X と Y の値はコンマ区切りの文字列として提供されることを想定します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-155">The `Parse` method has a single argument of type `System.Data.SqlTypes.SqlString`, and assumes that X and Y values are supplied as a comma-delimited string.</span></span> <span data-ttu-id="e8b92-156">`Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` 属性を `false` に設定すると、Point の NULL インスタンスから `Parse` メソッドが呼び出されなくなります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-156">Setting the `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` attribute to `false` prevents the `Parse` method from being called from a null instance of Point.</span></span>  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a><span data-ttu-id="e8b92-157">ToString メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="e8b92-157">Implementing the ToString Method</span></span>  
 <span data-ttu-id="e8b92-158">`ToString` メソッドでは、`Point` UDT が文字列値に変換されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-158">The `ToString` method converts the `Point` UDT to a string value.</span></span> <span data-ttu-id="e8b92-159">この場合は、`Point` 型の NULL インスタンスには文字列 "NULL" が返されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-159">In this case, the string "NULL" is returned for a Null instance of the `Point` type.</span></span> <span data-ttu-id="e8b92-160">`ToString` メソッドでは、`Parse` を使用して `System.Text.StringBuilder` メソッドと逆の操作を行い、X 座標と Y 座標の値から構成されるコンマ区切りの `System.String` を返します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-160">The `ToString` method reverses the `Parse` method by using a `System.Text.StringBuilder` to return a comma-delimited `System.String` consisting of the X and Y coordinate values.</span></span> <span data-ttu-id="e8b92-161">**Invokeifreceiverisnull**の既定値は false であるため、の null インスタンスのチェック `Point` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-161">Because **InvokeIfReceiverIsNull** defaults to false, the check for a null instance of `Point` is unnecessary.</span></span>  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a><span data-ttu-id="e8b92-162">UDT プロパティの公開</span><span class="sxs-lookup"><span data-stu-id="e8b92-162">Exposing UDT Properties</span></span>  
 <span data-ttu-id="e8b92-163">`Point` UDT は、`System.Int32` 型のパブリックの読み書きプロパティとして実装される X 座標と Y 座標を公開します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-163">The `Point` UDT exposes X and Y coordinates that are implemented as public read-write properties of type `System.Int32`.</span></span>  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a><span data-ttu-id="e8b92-164">UDT 値の検証</span><span class="sxs-lookup"><span data-stu-id="e8b92-164">Validating UDT Values</span></span>  
 <span data-ttu-id="e8b92-165">UDT データの使用時は、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]により、バイナリ値が自動的に UDT 値に変換されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-165">When working with UDT data, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatically converts binary values to UDT values.</span></span> <span data-ttu-id="e8b92-166">この変換処理では、値がその UDT のシリアル化形式に適しているかどうかがチェックされ、値を正しくシリアル化解除できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e8b92-166">This conversion process involves checking that values are appropriate for the serialization format of the type and ensuring that the value can be deserialized correctly.</span></span> <span data-ttu-id="e8b92-167">これにより、値はバイナリ形式に再変換できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-167">This ensures that the value can be converted back to binary form.</span></span> <span data-ttu-id="e8b92-168">また、バイト順の UDT の場合は、結果のバイナリ値が必ず元のバイナリ値と一致するようになります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-168">In the case of byte-ordered UDTs, this also ensures that the resulting binary value matches the original binary value.</span></span> <span data-ttu-id="e8b92-169">これにより、無効な値がデータベース内に存在する危険性が回避されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-169">This prevents invalid values from being persisted in the database.</span></span> <span data-ttu-id="e8b92-170">それでも、このレベルのチェックでは不十分である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-170">In some cases, this level of checking may be inadequate.</span></span> <span data-ttu-id="e8b92-171">UDT 値を一定の範囲内に制限する必要があるときは、さらに検証が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-171">Additional validation may be required when UDT values are required to be in an expected domain or range.</span></span> <span data-ttu-id="e8b92-172">たとえば、日付を実装する UDT の日の値は、特定の有効範囲内の正の数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-172">For example, a UDT that implements a date might require the day value to be a positive number that falls within a certain range of valid values.</span></span>  
  
 <span data-ttu-id="e8b92-173">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` の `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` プロパティを使用すると、データを UDT に割り当てる場合および UDT に変換する場合にサーバーで実行される検証メソッドを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-173">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` allows you to supply the name of a validation method that the server runs when data is assigned to a UDT or converted to a UDT.</span></span> <span data-ttu-id="e8b92-174">また `ValidationMethodName` は、bcp ユーティリティ、BULK INSERT、DBCC CHECKDB、DBCC CHECKFILEGROUP、DBCC CHECKTABLE、分散クエリ、表形式のデータ ストリーム (TDS) リモート プロシージャ コール (RPC) などの操作の実行中にも呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-174">`ValidationMethodName` is also called during the running of the bcp utility, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, distributed query, and tabular data stream (TDS) remote procedure call (RPC) operations.</span></span> <span data-ttu-id="e8b92-175">`ValidationMethodName` の既定値は NULL です。これは、検証メソッドが指定されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-175">The default value for `ValidationMethodName` is null, indicating that there is no validation method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e8b92-176">例</span><span class="sxs-lookup"><span data-stu-id="e8b92-176">Example</span></span>  
 <span data-ttu-id="e8b92-177">次のコードでは、`Point` の `ValidationMethodName` を指定する `ValidatePoint` クラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-177">The following code fragment shows the declaration for the `Point` class, which specifies a `ValidationMethodName` of `ValidatePoint`.</span></span>  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 <span data-ttu-id="e8b92-178">検証メソッドを指定する場合は、次のコードに示すようなシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="e8b92-178">If a validation method is specified, it must have a signature that looks like the following code fragment.</span></span>  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 <span data-ttu-id="e8b92-179">検証メソッドには任意のスコープを設定でき、値が有効な場合は `true` を返し、それ以外の場合は `false` を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-179">The validation method can have any scope and should return `true` if the value is valid, and `false` otherwise.</span></span> <span data-ttu-id="e8b92-180">このメソッドから `false` が返されるか例外がスローされると、その値は無効な値と見なされ、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-180">If the method returns `false` or throws an exception, the value is treated as not valid and an error is raised.</span></span>  
  
 <span data-ttu-id="e8b92-181">次のコード例では、0 以上の値のみが X 座標および Y 座標として許可されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-181">In the example below, the code allows only values of zero or greater the X and Y coordinates.</span></span>  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a><span data-ttu-id="e8b92-182">検証メソッドの制限事項</span><span class="sxs-lookup"><span data-stu-id="e8b92-182">Validation Method Limitations</span></span>  
 <span data-ttu-id="e8b92-183">サーバーから検証メソッドが呼び出されるのは、サーバーで変換が実行されるときです。個別のプロパティを設定したり [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT ステートメントを使用してデータを挿入するときには呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-183">The server calls the validation method when the server is performing conversions, not when data is inserted by setting individual properties or when data is inserted using a [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT statement.</span></span>  
  
 <span data-ttu-id="e8b92-184">`Parse`すべての状況で検証メソッドを実行する場合は、プロパティ setter およびメソッドから明示的に検証メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-184">You must explicitly call the validation method from property setters and the `Parse` method if you want the validation method to execute in all situations.</span></span> <span data-ttu-id="e8b92-185">この呼び出しは必須ではなく、場合によっては不適切な呼び出しになることもあります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-185">This is not a requirement, and in some cases may not even be desirable.</span></span>  
  
### <a name="parse-validation-example"></a><span data-ttu-id="e8b92-186">Parse による検証の例</span><span class="sxs-lookup"><span data-stu-id="e8b92-186">Parse Validation Example</span></span>  
 <span data-ttu-id="e8b92-187">クラスでメソッドが呼び出されるようにするには、 `ValidatePoint` `Point` `Parse` メソッドと、X 座標と Y 座標の値を設定するプロパティプロシージャからメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-187">To ensure that the `ValidatePoint` method is invoked in the `Point` class, you must call it from the `Parse` method and from the property procedures that set the X and Y coordinate values.</span></span> <span data-ttu-id="e8b92-188">次のコードフラグメントは、関数から検証メソッドを呼び出す方法を示して `ValidatePoint` `Parse` います。</span><span class="sxs-lookup"><span data-stu-id="e8b92-188">The following code fragment shows how to call the `ValidatePoint` validation method from the `Parse` function.</span></span>  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a><span data-ttu-id="e8b92-189">Property による検証の例</span><span class="sxs-lookup"><span data-stu-id="e8b92-189">Property Validation Example</span></span>  
 <span data-ttu-id="e8b92-190">次のコードフラグメントは、 `ValidatePoint` X 座標と Y 座標を設定するプロパティプロシージャから検証メソッドを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e8b92-190">The following code fragment shows how to call the `ValidatePoint` validation method from the property procedures that set the X and Y coordinates.</span></span>  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a><span data-ttu-id="e8b92-191">UDT メソッドのコーディング</span><span class="sxs-lookup"><span data-stu-id="e8b92-191">Coding UDT Methods</span></span>  
 <span data-ttu-id="e8b92-192">UDT メソッドをコーディングする際は、使用するアルゴリズムが時間の経過と共に変化する可能性があるかどうかを考慮します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-192">When coding UDT methods, consider whether the algorithm used could possibly change over time.</span></span> <span data-ttu-id="e8b92-193">変化する可能性がある場合は、UDT で使用するメソッド用に独立したクラスを作成することを検討します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-193">If so, you may want to consider creating a separate class for the methods your UDT uses.</span></span> <span data-ttu-id="e8b92-194">アルゴリズムが変化したら、新しいコードになったクラスを再コンパイルし、UDT に影響を与えることなくそのアセンブリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-194">If the algorithm changes, you can recompile the class with the new code and load the assembly into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without affecting the UDT.</span></span> <span data-ttu-id="e8b92-195">多くの場合、UDT は [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY ステートメントを使用して再読み込みできますが、既存のデータとの間に問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-195">In many cases UDTs can be reloaded using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement, but that could potentially cause problems with existing data.</span></span> <span data-ttu-id="e8b92-196">たとえば、 `Currency` **AdventureWorks**サンプルデータベースに含まれている UDT は、 **convertcurrency**関数を使用して、別のクラスに実装されている通貨値を変換します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-196">For example, the `Currency` UDT included with the **AdventureWorks** sample database uses a **ConvertCurrency** function to convert currency values, which is implemented in a separate class.</span></span> <span data-ttu-id="e8b92-197">変換アルゴリズムが今後どう変化するかは予測できず、新しい機能が必要になる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-197">It is possible that conversion algorithms may change in unpredictable ways in the future, or that new functionality may be required.</span></span> <span data-ttu-id="e8b92-198">**Convertcurrency**関数を `Currency` UDT 実装から分離することで、将来の変更を計画するときの柔軟性が向上します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-198">Separating the **ConvertCurrency** function from the `Currency` UDT implementation provides greater flexibility when planning for future changes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e8b92-199">例</span><span class="sxs-lookup"><span data-stu-id="e8b92-199">Example</span></span>  
 <span data-ttu-id="e8b92-200">この `Point` クラスには、distance、 **DistanceFrom** **、** **DistanceFromXY**の3つの単純なメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e8b92-200">The `Point` class contains three simple methods for calculating distance: **Distance**, **DistanceFrom** and **DistanceFromXY**.</span></span> <span data-ttu-id="e8b92-201">各メソッドから返されるのは、`double` から 0 までの距離、指定した地点から `Point` までの距離、および指定した X 座標と Y 座標から `Point` までの距離を示す `Point` 型の値です。</span><span class="sxs-lookup"><span data-stu-id="e8b92-201">Each returns a `double` calculating the distance from `Point` to zero, the distance from a specified point to `Point`, and the distance from specified X and Y coordinates to `Point`.</span></span> <span data-ttu-id="e8b92-202">**Distance**と**DistanceFrom**はそれぞれ**DistanceFromXY**を呼び出し、メソッドごとに異なる引数を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-202">**Distance** and **DistanceFrom** each call **DistanceFromXY**, and demonstrate how to use different arguments for each method.</span></span>  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a><span data-ttu-id="e8b92-203">SqlMethod 属性の使用</span><span class="sxs-lookup"><span data-stu-id="e8b92-203">Using SqlMethod Attributes</span></span>  
 <span data-ttu-id="e8b92-204">`Microsoft.SqlServer.Server.SqlMethodAttribute` クラスにはカスタム属性が用意されています。このカスタム属性を使用して、決定性を示したり、NULL で呼び出したときの動作を指定したり、メソッドがミューテーターかどうかを指定するためにメソッド定義にマークを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-204">The `Microsoft.SqlServer.Server.SqlMethodAttribute` class provides custom attributes that can be used to mark method definitions in order to specify determinism, on null call behavior, and to specify whether a method is a mutator.</span></span> <span data-ttu-id="e8b92-205">これらのプロパティは既定値に設定されるので、既定値以外の値を設定する場合のみカスタム属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-205">Default values for these properties are assumed, and the custom attribute is only used when a non-default value is needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8b92-206">`SqlMethodAttribute` クラスは `SqlFunctionAttribute` クラスを継承するので、`SqlMethodAttribute` は `FillRowMethodName` フィールドと `TableDefinition` フィールドを `SqlFunctionAttribute` から継承します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-206">The `SqlMethodAttribute` class inherits from the `SqlFunctionAttribute` class, so `SqlMethodAttribute` inherits the `FillRowMethodName` and `TableDefinition` fields from `SqlFunctionAttribute`.</span></span> <span data-ttu-id="e8b92-207">これは、一見テーブル値メソッドを記述できることを示していますが、この場合には該当しません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-207">This implies that it is possible to write a table-valued method, which is not the case.</span></span> <span data-ttu-id="e8b92-208">メソッドはコンパイルされ、アセンブリが配置されますが、実行時に戻り値の型に関するエラーが `IEnumerable` 発生します。これは、アセンブリ ' ' のクラス ' ' のメソッド、プロパティ、またはフィールド ' \<name> ' に \<class> \<assembly> 無効な戻り値の型が含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-208">The method compiles and the assembly deploys, but an error about the `IEnumerable` return type is raised at runtime with the following message: "Method, property, or field '\<name>' in class '\<class>' in assembly '\<assembly>' has invalid return type."</span></span>  
  
 <span data-ttu-id="e8b92-209">次の表では、UDT メソッドで使用できる `Microsoft.SqlServer.Server.SqlMethodAttribute` の関連プロパティについて説明し、それらの既定値を示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-209">The following table describes some of the relevant `Microsoft.SqlServer.Server.SqlMethodAttribute` properties that can be used in UDT methods, and lists their default values.</span></span>  
  
 <span data-ttu-id="e8b92-210">DataAccess</span><span class="sxs-lookup"><span data-stu-id="e8b92-210">DataAccess</span></span>  
 <span data-ttu-id="e8b92-211">関数から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに格納されているユーザー データにアクセスする必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-211">Indicates whether the function involves access to user data stored in the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e8b92-212">既定値は `DataAccessKind`.`None` です。</span><span class="sxs-lookup"><span data-stu-id="e8b92-212">Default is `DataAccessKind`.`None`.</span></span>  
  
 <span data-ttu-id="e8b92-213">IsDeterministic</span><span class="sxs-lookup"><span data-stu-id="e8b92-213">IsDeterministic</span></span>  
 <span data-ttu-id="e8b92-214">入力値とデータベースの状態が同じであれば、関数から同じ値が出力されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-214">Indicates whether the function produces the same output values given the same input values and the same database state.</span></span> <span data-ttu-id="e8b92-215">既定値は `false`です。</span><span class="sxs-lookup"><span data-stu-id="e8b92-215">Default is `false`.</span></span>  
  
 <span data-ttu-id="e8b92-216">IsMutator</span><span class="sxs-lookup"><span data-stu-id="e8b92-216">IsMutator</span></span>  
 <span data-ttu-id="e8b92-217">メソッドにより UDT インスタンスの状態が変化するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-217">Indicates whether the method causes a state change in the UDT instance.</span></span> <span data-ttu-id="e8b92-218">既定値は `false`です。</span><span class="sxs-lookup"><span data-stu-id="e8b92-218">Default is `false`.</span></span>  
  
 <span data-ttu-id="e8b92-219">IsPrecise</span><span class="sxs-lookup"><span data-stu-id="e8b92-219">IsPrecise</span></span>  
 <span data-ttu-id="e8b92-220">浮動小数点演算など、厳密な結果が算出されない計算が関数に含まれているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-220">Indicates whether the function involves imprecise computations, such as floating point operations.</span></span> <span data-ttu-id="e8b92-221">既定値は `false`です。</span><span class="sxs-lookup"><span data-stu-id="e8b92-221">Default is `false`.</span></span>  
  
 <span data-ttu-id="e8b92-222">OnNullCall</span><span class="sxs-lookup"><span data-stu-id="e8b92-222">OnNullCall</span></span>  
 <span data-ttu-id="e8b92-223">入力引数に NULL 参照が指定されたときにメソッドが呼び出されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-223">Indicates whether the method is called when null reference input arguments are specified.</span></span> <span data-ttu-id="e8b92-224">既定値は `true`です。</span><span class="sxs-lookup"><span data-stu-id="e8b92-224">Default is `true`.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e8b92-225">例</span><span class="sxs-lookup"><span data-stu-id="e8b92-225">Example</span></span>  
 <span data-ttu-id="e8b92-226">`Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` プロパティを使用すると、UDT インスタンスの状態の変化を許可するようにメソッドをマークできます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-226">The `Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` property allows you to mark a method that allows a change in the state of an instance of a UDT.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="e8b92-227">では、1 つの UPDATE ステートメントの SET 句に 2 つの UDT プロパティを設定できません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-227">does not allow you to set two UDT properties in the SET clause of one UPDATE statement.</span></span> <span data-ttu-id="e8b92-228">ただし、2 つのメンバーを変更するミューテーターとしてメソッドをマークすることはできます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-228">However, you can have a method marked as a mutator that changes the two members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8b92-229">ミューテーター メソッドはクエリ内では使用できません。</span><span class="sxs-lookup"><span data-stu-id="e8b92-229">Mutator methods are not allowed in queries.</span></span> <span data-ttu-id="e8b92-230">代入ステートメントかデータ変更ステートメントでのみ、これらのメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-230">They can be called only in assignment statements or data modification statements.</span></span> <span data-ttu-id="e8b92-231">ミューテーターとしてマークされたメソッドが戻り値を返さない `void` (Visual Basic では `Sub`) の場合、CREATE TYPE はエラーで失敗します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-231">If a method marked as mutator does not return `void` (or is not a `Sub` in Visual Basic), CREATE TYPE fails with an error.</span></span>  
  
 <span data-ttu-id="e8b92-232">次のステートメントでは、`Triangles` メソッドを含む `Rotate` UDT が存在するものとします。</span><span class="sxs-lookup"><span data-stu-id="e8b92-232">The following statement assumes the existence of a `Triangles` UDT that has a `Rotate` method.</span></span> <span data-ttu-id="e8b92-233">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] 更新ステートメントでは、`Rotate` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-233">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] update statement invokes the `Rotate` method:</span></span>  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 <span data-ttu-id="e8b92-234">`Rotate` メソッドは、`SqlMethod` が `IsMutator` に設定された `true` 属性で修飾されています。これにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はこのメソッドをミューテーター メソッドとしてマークできます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-234">The `Rotate` method is decorated with the `SqlMethod` attribute setting `IsMutator` to `true` so that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can mark the method as a mutator method.</span></span> <span data-ttu-id="e8b92-235">また、このコードでは `OnNullCall` を `false` に設定しています。これは、いずれかの入力パラメーターが NULL 参照の場合に、メソッドから NULL 参照 (Visual Basic では `Nothing`) が返されることをサーバーに示しています。</span><span class="sxs-lookup"><span data-stu-id="e8b92-235">The code also sets `OnNullCall` to `false`, which indicates to the server that the method returns a null reference (`Nothing` in Visual Basic) if any of the input parameters are null references.</span></span>  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a><span data-ttu-id="e8b92-236">ユーザー定義形式による UDT の実装</span><span class="sxs-lookup"><span data-stu-id="e8b92-236">Implementing a UDT with a User-Defined Format</span></span>  
 <span data-ttu-id="e8b92-237">ユーザー定義形式を使用して UDT を実装する際は、`Read` メソッドと `Write` メソッドを実装する必要があります。これらのメソッドは、UDT データのシリアル化とシリアル化解除を処理する Microsoft.SqlServer.Server.IBinarySerialize インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-237">When implementing a UDT with a user-defined format, you must implement `Read` and `Write` methods that implement the Microsoft.SqlServer.Server.IBinarySerialize interface to handle serializing and deserializing UDT data.</span></span> <span data-ttu-id="e8b92-238">また、`MaxByteSize` の `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` プロパティも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-238">You must also specify the `MaxByteSize` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.</span></span>  
  
### <a name="the-currency-udt"></a><span data-ttu-id="e8b92-239">Currency UDT</span><span class="sxs-lookup"><span data-stu-id="e8b92-239">The Currency UDT</span></span>  
 <span data-ttu-id="e8b92-240">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以降、`Currency` UDT は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] と共にインストールできる CLR サンプルに同梱されています。</span><span class="sxs-lookup"><span data-stu-id="e8b92-240">The `Currency` UDT is included with the CLR samples that can be installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="e8b92-241">`Currency` UDT では、特定のカルチャの通貨システムでの金額の処理がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-241">The `Currency` UDT supports handling amounts of money in the monetary system of a particular culture.</span></span> <span data-ttu-id="e8b92-242">定義するフィールドは 2 つあります。`string` 型の `CultureInfo` フィールドでは、通貨の発行カルチャ (en-us など) を指定します。`decimal` 型の `CurrencyValue` フィールドでは金額を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-242">You must define two fields: a `string` for `CultureInfo`, which specifies who issued the currency (en-us, for example) and a `decimal` for `CurrencyValue`, the amount of money.</span></span>  
  
 <span data-ttu-id="e8b92-243">`Currency` UDT がサーバーでの比較に使用されることはありませんが、この UDT には、1 つのメソッド `System.IComparable` を公開する `System.IComparable.CompareTo` インターフェイスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-243">Although it is not used by the server for performing comparisons, the `Currency` UDT implements the `System.IComparable` interface, which exposes a single method, `System.IComparable.CompareTo`.</span></span> <span data-ttu-id="e8b92-244">このインターフェイスは、クライアント側でカルチャ内の通貨値を正しく比較したり並べ替えたりする場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-244">This is used on the client side in situations where it is desirable to accurately compare or order currency values within cultures.</span></span>  
  
 <span data-ttu-id="e8b92-245">CLR で実行されているコードでは、カルチャが通貨値とは別に比較されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-245">Code running in the CLR compares the culture separately from the currency value.</span></span> <span data-ttu-id="e8b92-246">[!INCLUDE[tsql](../../includes/tsql-md.md)] コードでは、次の操作により比較結果が決まります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-246">For [!INCLUDE[tsql](../../includes/tsql-md.md)] code, the following actions determine the comparison:</span></span>  
  
1.  <span data-ttu-id="e8b92-247">`IsByteOrdered` 属性を true に設定します。これは、ディスク上に保存されたバイナリ表現を使用して比較を行うように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に指示します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-247">Set the `IsByteOrdered` attribute to true, which tells [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use the persisted binary representation on disk for comparisons.</span></span>  
  
2.  <span data-ttu-id="e8b92-248">`Write` UDT に `Currency` メソッドを使用して、この UDT をディスクに保存する形式と、その情報に基づいて [!INCLUDE[tsql](../../includes/tsql-md.md)] 演算で UDT 値を比較し順序付ける方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-248">Use the `Write` method for the `Currency` UDT to determine how the UDT is persisted on disk and therefore how UDT values are compared and ordered for [!INCLUDE[tsql](../../includes/tsql-md.md)] operations.</span></span>  
  
3.  <span data-ttu-id="e8b92-249">次のバイナリ形式を使用して `Currency` UDT を保存します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-249">Save the `Currency` UDT using the following binary format:</span></span>  
  
    1.  <span data-ttu-id="e8b92-250">0 バイト目から 19 バイト目までは UTF-16 エンコードされた文字列としてカルチャを保存します。右側の不足バイトには NULL 文字が埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-250">Save the culture as a UTF-16 encoded string for bytes 0-19 with padding to the right with null characters.</span></span>  
  
    2.  <span data-ttu-id="e8b92-251">20 バイト目以降を使用して、通貨の 10 進値を保存します。</span><span class="sxs-lookup"><span data-stu-id="e8b92-251">Use bytes 20 and above to contain the decimal value of the currency.</span></span>  
  
 <span data-ttu-id="e8b92-252">NULL 文字を埋め込む目的は、カルチャと通貨値を完全に分離することです。これにより、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードで UDT が比較されるとき、カルチャ バイトどうし、通貨バイト値どうしが比較されるようになります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-252">The purpose of the padding is to ensure that the culture is completely separated from the currency value, so that when one UDT is compared against another in [!INCLUDE[tsql](../../includes/tsql-md.md)] code, culture bytes are compared against culture bytes, and currency byte values are compared against currency byte values.</span></span>  
  
 <span data-ttu-id="e8b92-253">UDT の完全なコードリストについては `Currency` 、 [SQL Server データベースエンジンのサンプル](https://msftengprodsamples.codeplex.com/)で CLR サンプルをインストールする方法に関する説明に従ってください。</span><span class="sxs-lookup"><span data-stu-id="e8b92-253">For the complete code listing for the `Currency` UDT, follow the directions for installing the CLR samples in [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).</span></span>  
  
### <a name="currency-attributes"></a><span data-ttu-id="e8b92-254">Currency の属性</span><span class="sxs-lookup"><span data-stu-id="e8b92-254">Currency Attributes</span></span>  
 <span data-ttu-id="e8b92-255">`Currency` UDT には、次の属性が定義されます。</span><span class="sxs-lookup"><span data-stu-id="e8b92-255">The `Currency` UDT is defined with the following attributes.</span></span>  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a><span data-ttu-id="e8b92-256">IBinarySerialize を備えた Read メソッドと Write メソッドの作成</span><span class="sxs-lookup"><span data-stu-id="e8b92-256">Creating Read and Write Methods with IBinarySerialize</span></span>  
 <span data-ttu-id="e8b92-257">`UserDefined` シリアル化形式を選択した場合は、`IBinarySerialize` インターフェイスを実装し、独自の `Read` メソッドと `Write` メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b92-257">When you choose `UserDefined` serialization format, you also must implement the `IBinarySerialize` interface and create your own `Read` and `Write` methods.</span></span> <span data-ttu-id="e8b92-258">次の `Currency` UDT のプロシージャでは、`System.IO.BinaryReader` と `System.IO.BinaryWriter` を使用して UDT に対する読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="e8b92-258">The following procedures from the `Currency` UDT use the `System.IO.BinaryReader` and `System.IO.BinaryWriter` to read from and write to the UDT.</span></span>  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 <span data-ttu-id="e8b92-259">UDT の完全なコードリストについ `Currency` ては、「 [SQL Server データベースエンジンサンプル](https://msftengprodsamples.codeplex.com/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8b92-259">For the complete code listing for the `Currency` UDT, see [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b92-260">参照</span><span class="sxs-lookup"><span data-stu-id="e8b92-260">See Also</span></span>  
 [<span data-ttu-id="e8b92-261">ユーザー定義型の作成</span><span class="sxs-lookup"><span data-stu-id="e8b92-261">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
  
