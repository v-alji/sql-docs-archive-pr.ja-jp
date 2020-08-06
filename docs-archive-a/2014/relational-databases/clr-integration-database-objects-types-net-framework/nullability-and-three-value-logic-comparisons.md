---
title: Null 値の許容と3つの値の論理比較 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b8000c1c28d5a1d3d129b6e8d01c4ab2fbbbc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742273"
---
# <a name="nullability-and-three-value-logic-comparisons"></a><span data-ttu-id="18d20-102">NULL 値の許容と 3 値論理比較</span><span class="sxs-lookup"><span data-stu-id="18d20-102">Nullability and Three-Value Logic Comparisons</span></span>
  <span data-ttu-id="18d20-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型に慣れているユーザーであれば、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の `System.Data.SqlTypes` 名前空間でもよく似たセマンティクスや有効桁数を使用していることがわかるはずです。</span><span class="sxs-lookup"><span data-stu-id="18d20-103">If you are familiar with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, you will find similar semantics and precision in the `System.Data.SqlTypes` namespace in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="18d20-104">ただし、いくつか違いもあります。このトピックでは、これらの違いの中から最も重要な点について説明します。</span><span class="sxs-lookup"><span data-stu-id="18d20-104">There are some differences, however, and this topic covers the most important of these differences.</span></span>  
  
## <a name="null-values"></a><span data-ttu-id="18d20-105">NULL 値</span><span class="sxs-lookup"><span data-stu-id="18d20-105">NULL Values</span></span>  
 <span data-ttu-id="18d20-106">CLR (共通言語ランタイム) のネイティブ データ型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の主な違いは、CLR データ型では NULL 値が許容されないのに対して、SQL Server データ型では完全な NULL セマンティクスが用意されているという点です。</span><span class="sxs-lookup"><span data-stu-id="18d20-106">A primary difference between native common language runtime (CLR) data types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types is that the former do not allow for NULL values, while the latter provide full NULL semantics.</span></span>  
  
 <span data-ttu-id="18d20-107">比較は NULL 値の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="18d20-107">Comparisons are affected by NULL values.</span></span> <span data-ttu-id="18d20-108">つまり、2 つの値 x と y を比較するときに、x または y が NULL の場合、一部の論理比較では true または false ではなく UNKNOWN 値に評価されます。</span><span class="sxs-lookup"><span data-stu-id="18d20-108">When comparing two values x and y, if either x or y is NULL, then some logical comparisons evaluate to an UNKNOWN value rather than true or false.</span></span>  
  
## <a name="sqlboolean-data-type"></a><span data-ttu-id="18d20-109">SqlBoolean データ型</span><span class="sxs-lookup"><span data-stu-id="18d20-109">SqlBoolean Data Type</span></span>  
 <span data-ttu-id="18d20-110">`System.Data.SqlTypes` 名前空間では、この 3 つの論理値を表す `SqlBoolean` 型が導入されます。</span><span class="sxs-lookup"><span data-stu-id="18d20-110">The `System.Data.SqlTypes` namespace introduces a `SqlBoolean` type to represent this 3-value logic.</span></span> <span data-ttu-id="18d20-111">`SqlTypes` 間の比較では、`SqlBoolean` 型の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="18d20-111">Comparisons between any `SqlTypes` return a `SqlBoolean` value type.</span></span> <span data-ttu-id="18d20-112">UNKNOWN 値は、`SqlBoolean` 型の NULL 値で表現されます。</span><span class="sxs-lookup"><span data-stu-id="18d20-112">The UNKNOWN value is represented by the null value of the `SqlBoolean` type.</span></span> <span data-ttu-id="18d20-113">`IsTrue` 型の値を確認するために、プロパティ `IsFalse`、`IsNull`、および `SqlBoolean` が用意されています。</span><span class="sxs-lookup"><span data-stu-id="18d20-113">The properties `IsTrue`, `IsFalse`, and `IsNull` are provided to check the value of a `SqlBoolean` type.</span></span>  
  
## <a name="operations-functions-and-null-values"></a><span data-ttu-id="18d20-114">演算、関数、および NULL 値</span><span class="sxs-lookup"><span data-stu-id="18d20-114">Operations, Functions, and NULL Values</span></span>  
 <span data-ttu-id="18d20-115">すべての算術演算子 (+、-、 \* 、/、%)、ビットごとの演算子 (~、&、|)、およびほとんどの関数は、のオペランドまたは引数のいずれかが null の場合に null を返し `SqlTypes` ます。</span><span class="sxs-lookup"><span data-stu-id="18d20-115">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, and |), and most functions return NULL if any of the operands or arguments of `SqlTypes` are NULL.</span></span> <span data-ttu-id="18d20-116">`IsNull` プロパティで返される値は、常に true または false です。</span><span class="sxs-lookup"><span data-stu-id="18d20-116">The `IsNull` property always returns a true or false value.</span></span>  
  
## <a name="precision"></a><span data-ttu-id="18d20-117">有効桁数</span><span class="sxs-lookup"><span data-stu-id="18d20-117">Precision</span></span>  
 <span data-ttu-id="18d20-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR の decimal データ型の最大値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の numeric データ型や decimal データ型の最大値とは異なります。</span><span class="sxs-lookup"><span data-stu-id="18d20-118">Decimal data types in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR have different maximum values than those of the numeric and decimal data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="18d20-119">また、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR の decimal データ型では、最大有効桁数が想定されます。</span><span class="sxs-lookup"><span data-stu-id="18d20-119">In addition, in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR decimal data types assume the maximum precision.</span></span> <span data-ttu-id="18d20-120">ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の CLR で、`SqlDecimal` の最大有効桁数、最大小数点以下桁数、およびセマンティクスは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の decimal データ型と同じです。</span><span class="sxs-lookup"><span data-stu-id="18d20-120">In the CLR for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], however, `SqlDecimal` provides the same maximum precision and scale, and the same semantics as the decimal data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="overflow-detection"></a><span data-ttu-id="18d20-121">オーバーフローの検出</span><span class="sxs-lookup"><span data-stu-id="18d20-121">Overflow Detection</span></span>  
 <span data-ttu-id="18d20-122">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR では、非常に大きな 2 つの数を加算しても例外がスローされないことがあります。</span><span class="sxs-lookup"><span data-stu-id="18d20-122">In the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR, the addition of two very large numbers may not throw an exception.</span></span> <span data-ttu-id="18d20-123">チェック演算子を使用しないと、負の整数に "回り込んだ" 結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="18d20-123">Instead, if no check operator has been used, the returned result may "wrap around" as a negative integer.</span></span> <span data-ttu-id="18d20-124">`System.Data.SqlTypes` では、すべてのオーバーフロー エラー、アンダーフロー エラー、および 0 除算エラーに対して例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="18d20-124">In `System.Data.SqlTypes`, exceptions are thrown for all overflow and underflow errors, and divide-by-zero errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d20-125">参照</span><span class="sxs-lookup"><span data-stu-id="18d20-125">See Also</span></span>  
 [<span data-ttu-id="18d20-126">.NET Framework での SQL Server データ型</span><span class="sxs-lookup"><span data-stu-id="18d20-126">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
