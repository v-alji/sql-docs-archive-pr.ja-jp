---
title: CLR パラメーターデータのマッピング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
author: rothja
ms.author: jroth
ms.openlocfilehash: 7025c5180eac793534961af63df9ac701c95c03f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742278"
---
# <a name="mapping-clr-parameter-data"></a><span data-ttu-id="0fcf1-102">CLR パラメーター データのマッピング</span><span class="sxs-lookup"><span data-stu-id="0fcf1-102">Mapping CLR Parameter Data</span></span>
  <span data-ttu-id="0fcf1-103">次の表は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型、名前空間のの共通言語ランタイム (CLR) に相当するデータ型、および .NET Framework 内のネイティブ CLR に相当するものを示して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `System.Data.SqlTypes` [!INCLUDE[msCoName](../../includes/msconame-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-103">The following table lists [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, their equivalents in the common language runtime (CLR) for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the `System.Data.SqlTypes` namespace, and their native CLR equivalents in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="0fcf1-104">**SQL Server のデータ型**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-104">**SQL Server data type**</span></span>|<span data-ttu-id="0fcf1-105">型 (System.Data.SqlTypes または Microsoft.SqlServer.Types)</span><span class="sxs-lookup"><span data-stu-id="0fcf1-105">Type (in System.Data.SqlTypes or Microsoft.SqlServer.Types)</span></span>|<span data-ttu-id="0fcf1-106">**CLR データ型 (.NET Framework)**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-106">**CLR data type (.NET Framework)**</span></span>|  
|`bigint`|`SqlInt64`|<span data-ttu-id="0fcf1-107">**Int64、Nullable\<Int64>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-107">**Int64, Nullable\<Int64>**</span></span>|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|<span data-ttu-id="0fcf1-108">**ブール型、Null 値を許容\<Boolean>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-108">**Boolean, Nullable\<Boolean>**</span></span>|  
|`char`|<span data-ttu-id="0fcf1-109">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-109">None</span></span>|<span data-ttu-id="0fcf1-110">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-110">None</span></span>|  
|`cursor`|<span data-ttu-id="0fcf1-111">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-111">None</span></span>|<span data-ttu-id="0fcf1-112">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-112">None</span></span>|  
|`date`|`SqlDateTime`|<span data-ttu-id="0fcf1-113">**DateTime、Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-113">**DateTime, Nullable\<DateTime>**</span></span>|  
|`datetime`|`SqlDateTime`|<span data-ttu-id="0fcf1-114">**DateTime、Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-114">**DateTime, Nullable\<DateTime>**</span></span>|  
|`datetime2`|<span data-ttu-id="0fcf1-115">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-115">None</span></span>|<span data-ttu-id="0fcf1-116">**DateTime、Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-116">**DateTime, Nullable\<DateTime>**</span></span>|  
|`DATETIMEOFFSET`|`None`|<span data-ttu-id="0fcf1-117">**DateTimeOffset、Nullable\<DateTimeOffset>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-117">**DateTimeOffset, Nullable\<DateTimeOffset>**</span></span>|  
|`decimal`|`SqlDecimal`|<span data-ttu-id="0fcf1-118">**Decimal、Nullable\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-118">**Decimal, Nullable\<Decimal>**</span></span>|  
|`float`|`SqlDouble`|<span data-ttu-id="0fcf1-119">**Double、Nullable\<Double>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-119">**Double, Nullable\<Double>**</span></span>|  
|`geography`|`SqlGeography`<br /><br /> <span data-ttu-id="0fcf1-120">`SqlGeography`は Microsoft.SqlServer.Types.dll で定義され、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=53164)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-120">`SqlGeography` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="0fcf1-121">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-121">None</span></span>|  
|`geometry`|`SqlGeometry`<br /><br /> <span data-ttu-id="0fcf1-122">`SqlGeometry`は Microsoft.SqlServer.Types.dll で定義され、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=53164)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-122">`SqlGeometry` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="0fcf1-123">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-123">None</span></span>|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> <span data-ttu-id="0fcf1-124">`SqlHierarchyId`は Microsoft.SqlServer.Types.dll で定義され、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=53164)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-124">`SqlHierarchyId` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="0fcf1-125">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-125">None</span></span>|  
|`image`|<span data-ttu-id="0fcf1-126">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-126">None</span></span>|<span data-ttu-id="0fcf1-127">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-127">None</span></span>|  
|`int`|`SqlInt32`|<span data-ttu-id="0fcf1-128">**Int32、Nullable\<Int32>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-128">**Int32, Nullable\<Int32>**</span></span>|  
|`money`|`SqlMoney`|<span data-ttu-id="0fcf1-129">**Decimal、Nullable\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-129">**Decimal, Nullable\<Decimal>**</span></span>|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|<span data-ttu-id="0fcf1-130">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-130">None</span></span>|<span data-ttu-id="0fcf1-131">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-131">None</span></span>|  
|`numeric`|`SqlDecimal`|<span data-ttu-id="0fcf1-132">**Decimal、Nullable\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-132">**Decimal, Nullable\<Decimal>**</span></span>|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> <span data-ttu-id="0fcf1-133">`SQLChars` はデータの転送とアクセスに適しています。また、`SQLString` は文字列操作に適しています。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-133">`SQLChars` is a better match for data transfer and access, and `SQLString` is a better match for performing String operations.</span></span>|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|<span data-ttu-id="0fcf1-134">**Char、String、Char []、Nullable\<char>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-134">**Char, String, Char[], Nullable\<char>**</span></span>|  
|`real`|<span data-ttu-id="0fcf1-135">`SqlSingle`(`SqlSingle` の範囲内。ただし `real` より大きい)</span><span class="sxs-lookup"><span data-stu-id="0fcf1-135">`SqlSingle` (the range of `SqlSingle`, however, is larger than `real`)</span></span>|<span data-ttu-id="0fcf1-136">**Single、Nullable\<Single>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-136">**Single, Nullable\<Single>**</span></span>|  
|`rowversion`|<span data-ttu-id="0fcf1-137">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-137">None</span></span>|`Byte[]`|  
|`smallint`|`SqlInt16`|<span data-ttu-id="0fcf1-138">**Int16、Nullable\<Int16>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-138">**Int16, Nullable\<Int16>**</span></span>|  
|`smallmoney`|`SqlMoney`|<span data-ttu-id="0fcf1-139">**Decimal、Nullable\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-139">**Decimal, Nullable\<Decimal>**</span></span>|  
|`sql_variant`|<span data-ttu-id="0fcf1-140">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-140">None</span></span>|`Object`|  
|`table`|<span data-ttu-id="0fcf1-141">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-141">None</span></span>|<span data-ttu-id="0fcf1-142">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-142">None</span></span>|  
|`text`|<span data-ttu-id="0fcf1-143">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-143">None</span></span>|<span data-ttu-id="0fcf1-144">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-144">None</span></span>|  
|`time`|<span data-ttu-id="0fcf1-145">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-145">None</span></span>|<span data-ttu-id="0fcf1-146">**TimeSpan、Nullable\<TimeSpan>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-146">**TimeSpan, Nullable\<TimeSpan>**</span></span>|  
|`timestamp`|<span data-ttu-id="0fcf1-147">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-147">None</span></span>|<span data-ttu-id="0fcf1-148">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-148">None</span></span>|  
|`tinyint`|`SqlByte`|<span data-ttu-id="0fcf1-149">**Byte、Nullable\<Byte>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-149">**Byte, Nullable\<Byte>**</span></span>|  
|`uniqueidentifier`|`SqlGuid`|<span data-ttu-id="0fcf1-150">**Guid、Nullable\<Guid>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-150">**Guid, Nullable\<Guid>**</span></span>|  
|`User-defined type(UDT)`|<span data-ttu-id="0fcf1-151">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-151">None</span></span>|<span data-ttu-id="0fcf1-152">同じアセンブリまたは依存アセンブリ内のユーザー定義型にバインドされている同じクラス</span><span class="sxs-lookup"><span data-stu-id="0fcf1-152">The same class that is bound to the user-defined type in the same assembly or a dependent assembly.</span></span>|  
|<span data-ttu-id="0fcf1-153">**varbinary**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-153">**varbinary**</span></span>|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|<span data-ttu-id="0fcf1-154">**byte、Byte []、Nullable\<byte>**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-154">**byte, Byte[], Nullable\<byte>**</span></span>|  
|`varchar`|<span data-ttu-id="0fcf1-155">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-155">None</span></span>|<span data-ttu-id="0fcf1-156">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-156">None</span></span>|  
|`xml`|`SqlXml`|<span data-ttu-id="0fcf1-157">なし</span><span class="sxs-lookup"><span data-stu-id="0fcf1-157">None</span></span>|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a><span data-ttu-id="0fcf1-158">out パラメーターによるデータ型の自動変換</span><span class="sxs-lookup"><span data-stu-id="0fcf1-158">Automatic Data Type Conversion with Out Parameters</span></span>  
 <span data-ttu-id="0fcf1-159">CLR メソッドでは、入力パラメーターを `out` 修飾子 (Microsoft Visual C#) または `<Out()> ByRef` (Microsoft Visual Basic) でマークすることにより、呼び出し側のコードまたはプログラムに情報を返すことができます。`System.Data.SqlTypes` 名前空間での入力パラメーターが CLR データ型で、呼び出し側のプログラムがこれと同等な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を入力パラメーターとして指定する場合、CLR メソッドがデータ型を返すと、自動的に型の変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-159">A CLR method can return information to the calling code or program by marking an input parameter with the `out` modifier (Microsoft Visual C#) or `<Out()> ByRef` (Microsoft Visual Basic) If the input parameter is a CLR data type in the `System.Data.SqlTypes` namespace, and the calling program specifies its equivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type as the input parameter, a type conversion occurs automatically when the CLR method returns the data type.</span></span>  
  
 <span data-ttu-id="0fcf1-160">たとえば、次の CLR ストアド プロシージャには、`SqlInt32` (C#) または `out` (Visual Basic) でマークされている `<Out()> ByRef` CLR データ型の入力パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-160">For example, the following CLR stored procedure has an input parameter of `SqlInt32` CLR data type that is marked with `out` (C#) or `<Out()> ByRef` (Visual Basic):</span></span>  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 <span data-ttu-id="0fcf1-161">データベースでアセンブリがビルドおよび作成された後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、OUTPUT パラメーターとして `int` の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定する、次の Transact-SQL によりストアド プロシージャが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-161">After the assembly is built and created in the database, the stored procedure is created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the following Transact-SQL, which specifies a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of `int` as an OUTPUT parameter:</span></span>  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 <span data-ttu-id="0fcf1-162">CLR ストアド プロシージャが呼び出されると、`SqlInt32` データ型は自動的に `int` データ型に変換され、呼び出し側のプログラムに返されます。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-162">When the CLR stored procedure is called, the `SqlInt32` data type is automatically converted to an `int` data type, and returned to the calling program.</span></span>  
  
 <span data-ttu-id="0fcf1-163">ただし、out パラメーターにより自動的にすべての CLR データ型を同等な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-163">Not all CLR data types can be automatically converted to their equivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types through an out parameter, however.</span></span> <span data-ttu-id="0fcf1-164">次の表に、これらの例外を示します。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-164">The following table lists these exceptions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0fcf1-165">**CLR データ型 (SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-165">**CLR data type (SQL Server)**</span></span>|<span data-ttu-id="0fcf1-166">**SQL Server のデータ型**</span><span class="sxs-lookup"><span data-stu-id="0fcf1-166">**SQL Server data type**</span></span>|  
|`Decimal`|<span data-ttu-id="0fcf1-167">smallmoney</span><span class="sxs-lookup"><span data-stu-id="0fcf1-167">smallmoney</span></span>|  
|`SqlMoney`|<span data-ttu-id="0fcf1-168">smallmoney</span><span class="sxs-lookup"><span data-stu-id="0fcf1-168">smallmoney</span></span>|  
|`Decimal`|<span data-ttu-id="0fcf1-169">money</span><span class="sxs-lookup"><span data-stu-id="0fcf1-169">money</span></span>|  
|`DateTime`|<span data-ttu-id="0fcf1-170">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="0fcf1-170">smalldatetime</span></span>|  
|`SQLDateTime`|<span data-ttu-id="0fcf1-171">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="0fcf1-171">smalldatetime</span></span>|  
  
## <a name="change-history"></a><span data-ttu-id="0fcf1-172">変更履歴</span><span class="sxs-lookup"><span data-stu-id="0fcf1-172">Change History</span></span>  
  
|<span data-ttu-id="0fcf1-173">変更内容</span><span class="sxs-lookup"><span data-stu-id="0fcf1-173">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="0fcf1-174">マッピング テーブルに `SqlGeography` 型、`SqlGeometry` 型、および `SqlHierarchyId` 型を追加しました。</span><span class="sxs-lookup"><span data-stu-id="0fcf1-174">Added `SqlGeography`, `SqlGeometry`, and `SqlHierarchyId` types to the mapping table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fcf1-175">参照</span><span class="sxs-lookup"><span data-stu-id="0fcf1-175">See Also</span></span>  
 [<span data-ttu-id="0fcf1-176">.NET Framework での SQL Server データ型</span><span class="sxs-lookup"><span data-stu-id="0fcf1-176">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
