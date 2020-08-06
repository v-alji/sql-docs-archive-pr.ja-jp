---
title: XPath データ型 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
author: rothja
ms.author: jroth
ms.openlocfilehash: 846fc5a17ac97d30b6f0ab65fee176ac459c20cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642696"
---
# <a name="xpath-data-types-sqlxml-40"></a><span data-ttu-id="8d6d2-102">XPath のデータ型 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-102">XPath Data Types (SQLXML 4.0)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="8d6d2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、XPath、および XML スキーマ (XSD) のデータ型は大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath, and XML Schema (XSD) have very different data types.</span></span> <span data-ttu-id="8d6d2-104">たとえば、XPath に整数や日付のデータ型はありませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と XSD にはこれらのデータ型が多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-104">For example, XPath does not have integer or date data types, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and XSD have many.</span></span> <span data-ttu-id="8d6d2-105">また、XSD では時間値の精度はナノ秒ですが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の精度は最大でも 1/300 秒です。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-105">XSD uses nanosecond precision for time values, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses at most 1/300-second precision.</span></span> <span data-ttu-id="8d6d2-106">このため、あるデータ型から別のデータ型へのマッピングが常に可能であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-106">Consequently, mapping one data type to another is not always possible.</span></span> <span data-ttu-id="8d6d2-107">データ型の XSD データ型へのマッピングの詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「[データ型の強制変換」と「sql: datatype 注釈 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-107">For more information about mapping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to XSD data types, see [Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="8d6d2-108">XPath には、`string`、`number`、および `boolean` の 3 つのデータ型があります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-108">XPath has three data types: `string`, `number`, and `boolean`.</span></span> <span data-ttu-id="8d6d2-109">`number` 型は、常に IEEE 754 倍精度浮動小数点数です。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-109">The `number` data type is always an IEEE 754 double-precision floating-point.</span></span> <span data-ttu-id="8d6d2-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `float(53)` データ型は、XPath に最も近いです `number` 。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`float(53)` data type is the closest to XPath `number`.</span></span> <span data-ttu-id="8d6d2-111">ただし、`float(53)` は正確には IEEE 754 ではありません。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-111">However, `float(53)` is not exactly IEEE 754.</span></span> <span data-ttu-id="8d6d2-112">たとえば、非数 (NaN) も無限大も使用されません。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-112">For example, neither NaN (Not-a-Number) nor infinity is used.</span></span> <span data-ttu-id="8d6d2-113">非数値文字列を `number` 型に変換し、0 での除算を試みると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-113">Attempting to convert a nonnumeric string to `number` and trying to divide by zero results in an error.</span></span>  
  
## <a name="xpath-conversions"></a><span data-ttu-id="8d6d2-114">XPath 変換</span><span class="sxs-lookup"><span data-stu-id="8d6d2-114">XPath Conversions</span></span>  
 <span data-ttu-id="8d6d2-115">`OrderDetail[@UnitPrice > "10.0"]` などの XPath クエリを使用する場合は、データ型の変換を暗黙的に行うか明示的に行うかによって、クエリの意味が微妙に変わります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-115">When you use an XPath query such as `OrderDetail[@UnitPrice > "10.0"]`, implicit and explicit data type conversions can change the meaning of the query in subtle ways.</span></span> <span data-ttu-id="8d6d2-116">このため、XPath データ型の実装方法について理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-116">Therefore, it is important to understand how XPath data types are implemented.</span></span> <span data-ttu-id="8d6d2-117">XPath 言語仕様である XML Path Language (XPath) バージョン 1.0 W3C 勧告では、1999年10月8日に、W3C Web サイトの「」を参照 http://www.w3.org/TR/1999/PR-xpath-19991008.html してください。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-117">The XPath language specification, XML Path Language (XPath) version 1.0 W3C Proposed Recommendation 8 October 1999, can be found at the W3C Web site at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="8d6d2-118">XPath の演算子は、次の 4 つのカテゴリに分けられます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-118">XPath operators are divided into four categories:</span></span>  
  
-   <span data-ttu-id="8d6d2-119">論理演算子 (and、or)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-119">Boolean operators (and, or)</span></span>  
  
-   <span data-ttu-id="8d6d2-120">関係演算子 ( \<, > 、 \<=, > =)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-120">Relational operators (\<, >, \<=, >=)</span></span>  
  
-   <span data-ttu-id="8d6d2-121">等価演算子 (=、!=)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-121">Equality operators (=, !=)</span></span>  
  
-   <span data-ttu-id="8d6d2-122">算術演算子 (+、-、\*、div、mod)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-122">Arithmetic operators (+, -, \*, div, mod)</span></span>  
  
 <span data-ttu-id="8d6d2-123">各カテゴリの演算子では、それぞれ異なる方法で各自のオペランドが変換されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-123">Each category of operator converts its operands differently.</span></span> <span data-ttu-id="8d6d2-124">XPath の演算子では、必要に応じて各自のオペランドが暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-124">XPath operators implicitly convert their operands if necessary.</span></span> <span data-ttu-id="8d6d2-125">算術演算子では、オペランドが `number` に変換され、数値が得られます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-125">Arithmetic operators convert their operands to `number`, and result in a number value.</span></span> <span data-ttu-id="8d6d2-126">論理演算子では、オペランドが `boolean` に変換され、ブール値が得られます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-126">Boolean operators convert their operands to `boolean`, and result in a Boolean value.</span></span> <span data-ttu-id="8d6d2-127">関係演算子と等価演算子では、ブール値が得られます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-127">Relational operators and equality operators result in a Boolean value.</span></span> <span data-ttu-id="8d6d2-128">ただし、次の表に示すように、オペランドの変換元のデータ型に応じて、それぞれ異なる変換規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-128">However, they have different conversion rules depending on the original data types of their operands, as shown in this table.</span></span>  
  
|<span data-ttu-id="8d6d2-129">オペランド</span><span class="sxs-lookup"><span data-stu-id="8d6d2-129">Operand</span></span>|<span data-ttu-id="8d6d2-130">関係演算子</span><span class="sxs-lookup"><span data-stu-id="8d6d2-130">Relational operator</span></span>|<span data-ttu-id="8d6d2-131">等値演算子</span><span class="sxs-lookup"><span data-stu-id="8d6d2-131">Equality operator</span></span>|  
|-------------|-------------------------|-----------------------|  
|<span data-ttu-id="8d6d2-132">両方のオペランドがノード セットの場合</span><span class="sxs-lookup"><span data-stu-id="8d6d2-132">Both operands are node-sets.</span></span>|<span data-ttu-id="8d6d2-133">それぞれのセットにノードが 1 つあり、それらの `string` 値を比較した結果が TRUE の場合に限り TRUE。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-133">TRUE if and only if there is a node in one set and a node in the second set such that the comparison of their `string` values is TRUE.</span></span>|<span data-ttu-id="8d6d2-134">同じ。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-134">Same.</span></span>|  
|<span data-ttu-id="8d6d2-135">一方がノード セットで、他方が `string` の場合</span><span class="sxs-lookup"><span data-stu-id="8d6d2-135">One is a node-set, the other a `string`.</span></span>|<span data-ttu-id="8d6d2-136">ノード セットにノードが 1 つあり、それを `number` に変換した値と、`string` を `number` に変換した値を比較した結果が TRUE である場合に限り TRUE。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-136">TRUE if and only if there is a node in the node-set such that when converted to `number`, the comparison of it with the `string` converted to `number` is TRUE.</span></span>|<span data-ttu-id="8d6d2-137">ノード セットにノードが 1 つあり、それを `string` に変換した値と、`string` を比較した結果が TRUE である場合に限り TRUE。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-137">TRUE if and only if there is a node in the node-set such that when converted to `string`, the comparison of it with the `string` is TRUE.</span></span>|  
|<span data-ttu-id="8d6d2-138">一方がノード セットで、他方が `number` の場合</span><span class="sxs-lookup"><span data-stu-id="8d6d2-138">One is a node-set, the other a `number`.</span></span>|<span data-ttu-id="8d6d2-139">ノード セットにノードが 1 つあり、それを `number` に変換した値と、`number` を比較した結果が TRUE である場合に限り TRUE。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-139">TRUE if and only if there is a node in the node-set such that when converted to `number`, the comparison of it with the `number` is TRUE.</span></span>|<span data-ttu-id="8d6d2-140">同じ。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-140">Same.</span></span>|  
|<span data-ttu-id="8d6d2-141">一方がノード セットで、他方が `boolean` の場合</span><span class="sxs-lookup"><span data-stu-id="8d6d2-141">One is a node-set, the other a `boolean`.</span></span>|<span data-ttu-id="8d6d2-142">ノード セットにノードが 1 つあり、それを `boolean` に変換し、その後 `number` に変換した値と、`boolean` を `number` に変換した値を比較した結果が TRUE である場合に限り TRUE。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-142">TRUE if and only if there is a node in the node-set such that when converted to `boolean` and then to `number`, the comparison of it with the `boolean` converted to `number` is TRUE.</span></span>|<span data-ttu-id="8d6d2-143">ノード セットにノードが 1 つあり、それを `boolean` に変換した値と、`boolean` を比較した結果が TRUE である場合に限り TRUE。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-143">TRUE if and only if there is a node in the node-set such that when converted to `boolean`, the comparison of it with the `boolean` is TRUE.</span></span>|  
|<span data-ttu-id="8d6d2-144">どちらもノード セットでない場合</span><span class="sxs-lookup"><span data-stu-id="8d6d2-144">Neither is a node-set.</span></span>|<span data-ttu-id="8d6d2-145">両方のオペランドを `number` に変換し比較。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-145">Convert both operands to `number` and then compare.</span></span>|<span data-ttu-id="8d6d2-146">両方のオペランドを共通のデータ型に変換し比較。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-146">Convert both operands to a common type and then compare.</span></span> <span data-ttu-id="8d6d2-147">いずれかが `boolean` の場合は `boolean` に変換し、いずれかが `number` の場合は `number` に変換します。それ以外の場合は `string` に変換します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-147">Convert to `boolean` if either is `boolean`, `number` if either is `number`; otherwise, convert to `string`.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="8d6d2-148">XPath の関係演算子ではオペランドが常に `number` に変換されるので、`string` の比較はできません。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-148">Because XPath relational operators always convert their operands to `number`, `string` comparisons are not possible.</span></span> <span data-ttu-id="8d6d2-149">日付の比較を含めるため、SQL Server 2000 では XPath の仕様が変更され、関係演算子で `string` と `string`、ノード セットと `string`、または文字列値ノード セットと文字列値ノード セットが比較される場合には、`string` ではなく `number` の比較が行われるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-149">To include date comparisons, SQL Server 2000 offers this variation to the XPath specification: When a relational operator compares a `string` to a `string`, a node-set to a `string`, or a string-valued node-set to a string-valued node-set, a `string` comparison (not a `number` comparison) is performed.</span></span>  
  
## <a name="node-set-conversions"></a><span data-ttu-id="8d6d2-150">ノード セット変換</span><span class="sxs-lookup"><span data-stu-id="8d6d2-150">Node-Set Conversions</span></span>  
 <span data-ttu-id="8d6d2-151">ノード セット変換は常に直感的なものとは限りません。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-151">Node-set conversions are not always intuitive.</span></span> <span data-ttu-id="8d6d2-152">ノード セットから `string` への変換では、セット内の先頭ノードの文字列値のみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-152">A node-set is converted to a `string` by taking the string value of only the first node in the set.</span></span> <span data-ttu-id="8d6d2-153">ノードセットは、に変換してからに変換することによってに変換され `number` `string` `string` `number` ます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-153">A node-set is converted to `number` by converting it to `string`, and then converting `string` to `number`.</span></span> <span data-ttu-id="8d6d2-154">ノード セットから `boolean` への変換では、その存在が検査されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-154">A node-set is converted to `boolean` by testing for its existence.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8d6d2-155">では、ノード セットで位置の選択は実行されません。たとえば、XPath クエリ `Customer[3]` は 3 番目の顧客を意味しますが、このような位置の選択は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-155">does not perform positional selection on node-sets: for example, the XPath query `Customer[3]` means the third customer; this type of positional selection is not supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8d6d2-156">したがって、XPath 仕様で説明されているような、ノード セットから `string`、またはノード セットから `number` への変換は実装されていません。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-156">Therefore, the node-set-to-`string` or node-set-to-`number` conversions as described by the XPath specification are not implemented.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8d6d2-157">では、XPath 仕様で "先頭" の意味で指定されているものが "任意" の意味として扱われます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-157">uses "any" semantics wherever the XPath specification specifies "first" semantics.</span></span> <span data-ttu-id="8d6d2-158">たとえば、W3C XPath 仕様に基づき、XPath クエリは、 `Order[OrderDetail/@UnitPrice > 10.0]` **UnitPrice**が10.0 より大きい最初の**orderdetail**を持つ注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-158">For example, based on the W3C XPath specification, the XPath query `Order[OrderDetail/@UnitPrice > 10.0]` selects those orders with the first **OrderDetail** that has a **UnitPrice** greater than 10.0.</span></span> <span data-ttu-id="8d6d2-159">では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、この XPath クエリは、 **UnitPrice**が10.0 より大きい**orderdetail**を持つ注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-159">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this XPath query selects those orders with any **OrderDetail** that has a **UnitPrice** greater than 10.0.</span></span>  
  
 <span data-ttu-id="8d6d2-160">`boolean` への変換では、存在検査が生成されます。このため、`Products[@Discontinued=true()]` という XPath クエリは、"Products.Discontinued = 1" という SQL 式ではなく、"Products.Discontinued is not null" という SQL 式と等価になります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-160">Conversion to `boolean` generates an existence test; therefore, the XPath query `Products[@Discontinued=true()]` is equivalent to the SQL expression "Products.Discontinued is not null", not the SQL expression "Products.Discontinued = 1".</span></span> <span data-ttu-id="8d6d2-161">"Products.Discontinued = 1" という SQL 式と等価なクエリを作成するには、最初にノード セットを `boolean` などの、`number` 以外の型に変換します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-161">To make the query equivalent to the latter SQL expression, first convert the node-set to a non-`boolean` type, such as `number`.</span></span> <span data-ttu-id="8d6d2-162">たとえば、「 `Products[number(@Discontinued) = true()]` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-162">For example, `Products[number(@Discontinued) = true()]`.</span></span>  
  
 <span data-ttu-id="8d6d2-163">大半の演算子は、ノード セット内の 1 つ以上のノードに対して TRUE であれば TRUE となるように定義されているので、これらの演算はノード セットが空の場合は常に FALSE となります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-163">Because most operators are defined to be TRUE if they are TRUE for any or one of the nodes in the node-set, these operations always evaluate to FALSE if the node-set is empty.</span></span> <span data-ttu-id="8d6d2-164">したがって、A が空の場合、`A = B` と `A != B` は両方とも FALSE になり、`not(A=B)` と `not(A!=B)` は TRUE になります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-164">Thus, if A is empty, both `A = B` and `A != B` are FALSE, and `not(A=B)` and `not(A!=B)` are TRUE.</span></span>  
  
 <span data-ttu-id="8d6d2-165">通常、列にマップされる属性や要素は、データベース内でその列の値が `null` でない場合に存在します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-165">Usually, an attribute or element that maps to a column exists if the value of that column in the database is not `null`.</span></span> <span data-ttu-id="8d6d2-166">行にマップされる要素は、子が存在する場合に存在します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-166">Elements that map to rows exist if any of their children exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d6d2-167">`is-constant` で注釈される要素は常に存在します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-167">Elements annotated with `is-constant` always exist.</span></span> <span data-ttu-id="8d6d2-168">したがって、XPath 述語を `is-constant` 要素に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-168">Consequently, XPath predicates cannot be used on `is-constant` elements.</span></span>  
  
 <span data-ttu-id="8d6d2-169">ノード セットが `string` または `number` に変換される場合、注釈付きスキーマにその XDR 型が指定されているかどうかが調べられ、見つかった場合はその型によって必要な変換が判別されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-169">When a node-set is converted to `string` or `number`, its XDR type (if any) is inspected in the annotated schema and that type is used to determine the conversion that is required.</span></span>  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a><span data-ttu-id="8d6d2-170">XDR データ型から XPath データ型へのマッピング</span><span class="sxs-lookup"><span data-stu-id="8d6d2-170">Mapping XDR Data Types to XPath Data Types</span></span>  
 <span data-ttu-id="8d6d2-171">ノードの XPath データ型は、次の表に示すように、スキーマ内の XDR データ型から派生します (この**ノードは、説明的な**目的で使用されます)。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-171">The XPath data type of a node is derived from the XDR data type in the schema, as shown in the following table (the node **EmployeeID** is used for illustrative purpose).</span></span>  
  
|<span data-ttu-id="8d6d2-172">XDR データ型</span><span class="sxs-lookup"><span data-stu-id="8d6d2-172">XDR data type</span></span>|<span data-ttu-id="8d6d2-173">同等の</span><span class="sxs-lookup"><span data-stu-id="8d6d2-173">Equivalent</span></span><br /><br /> <span data-ttu-id="8d6d2-174">XPath データ型</span><span class="sxs-lookup"><span data-stu-id="8d6d2-174">XPath data type</span></span>|<span data-ttu-id="8d6d2-175">使用される SQL Server 変換</span><span class="sxs-lookup"><span data-stu-id="8d6d2-175">SQL Server conversion used</span></span>|  
|-------------------|------------------------------------|--------------------------------|  
|<span data-ttu-id="8d6d2-176">Nonebin.base64bin.hex</span><span class="sxs-lookup"><span data-stu-id="8d6d2-176">Nonebin.base64bin.hex</span></span>|<span data-ttu-id="8d6d2-177">該当なし</span><span class="sxs-lookup"><span data-stu-id="8d6d2-177">N/A</span></span>|<span data-ttu-id="8d6d2-178">NoneEmployeeID</span><span class="sxs-lookup"><span data-stu-id="8d6d2-178">NoneEmployeeID</span></span>|  
|<span data-ttu-id="8d6d2-179">boolean</span><span class="sxs-lookup"><span data-stu-id="8d6d2-179">boolean</span></span>|<span data-ttu-id="8d6d2-180">boolean</span><span class="sxs-lookup"><span data-stu-id="8d6d2-180">boolean</span></span>|<span data-ttu-id="8d6d2-181">CONVERT(bit, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-181">CONVERT(bit, EmployeeID)</span></span>|  
|<span data-ttu-id="8d6d2-182">number、int、float,i1、i2、i4、i8、r4、r8ui1、ui2、ui4、ui8</span><span class="sxs-lookup"><span data-stu-id="8d6d2-182">number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8</span></span>|<span data-ttu-id="8d6d2-183">number</span><span class="sxs-lookup"><span data-stu-id="8d6d2-183">number</span></span>|<span data-ttu-id="8d6d2-184">CONVERT(float(53), EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-184">CONVERT(float(53), EmployeeID)</span></span>|  
|<span data-ttu-id="8d6d2-185">id、idref、idrefsentity、entities、enumerationnotation、nmtoken、nmtokens、chardate、Timedate、Time.tz、string、uri、uuid</span><span class="sxs-lookup"><span data-stu-id="8d6d2-185">id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid</span></span>|<span data-ttu-id="8d6d2-186">string</span><span class="sxs-lookup"><span data-stu-id="8d6d2-186">string</span></span>|<span data-ttu-id="8d6d2-187">CONVERT(nvarchar(4000), EmployeeID, 126)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-187">CONVERT(nvarchar(4000), EmployeeID, 126)</span></span>|  
|<span data-ttu-id="8d6d2-188">fixed14.4</span><span class="sxs-lookup"><span data-stu-id="8d6d2-188">fixed14.4</span></span>|<span data-ttu-id="8d6d2-189">N/A (XDR データ型 fixed14.4 に相当する XPath のデータ型はありません)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-189">N/A(There is no data type in XPath that is equivalent to the fixed14.4 XDR data type)</span></span>|<span data-ttu-id="8d6d2-190">CONVERT(money, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-190">CONVERT(money, EmployeeID)</span></span>|  
|<span data-ttu-id="8d6d2-191">date</span><span class="sxs-lookup"><span data-stu-id="8d6d2-191">date</span></span>|<span data-ttu-id="8d6d2-192">string</span><span class="sxs-lookup"><span data-stu-id="8d6d2-192">string</span></span>|<span data-ttu-id="8d6d2-193">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-193">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span></span>|  
|<span data-ttu-id="8d6d2-194">time</span><span class="sxs-lookup"><span data-stu-id="8d6d2-194">time</span></span><br /><br /> <span data-ttu-id="8d6d2-195">time.tz</span><span class="sxs-lookup"><span data-stu-id="8d6d2-195">time.tz</span></span>|<span data-ttu-id="8d6d2-196">string</span><span class="sxs-lookup"><span data-stu-id="8d6d2-196">string</span></span>|<span data-ttu-id="8d6d2-197">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-197">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span></span>|  
  
 <span data-ttu-id="8d6d2-198">日付と時刻の変換は、値がデータ型またはを使用してデータベースに格納されているかどうかにかかわらず機能するように設計されてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` `string` ます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-198">The date and time conversions are designed to work whether the value is stored in the database using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`datetime` data type or a `string`.</span></span> <span data-ttu-id="8d6d2-199">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` データ型はを使用せず、 `timezone` XML データ型よりも精度が低いことに注意して `time` ください。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-199">Note that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`datetime` data type does not use `timezone` and has a smaller precision than the XML `time` data type.</span></span> <span data-ttu-id="8d6d2-200">`timezone` 型または追加の有効桁数を含めるには、`string` 型を使って [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-200">To include the `timezone` data type or additional precision, store the data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a `string` type.</span></span>  
  
 <span data-ttu-id="8d6d2-201">ノードが XDR データ型から XPath データ型に変換される場合は、1 つの XPath データ型から別の XPath データ型へ、追加の変換が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-201">When a node is converted from its XDR data type to the XPath data type, additional conversion is sometimes necessary (from one XPath data type to another XPath data type).</span></span> <span data-ttu-id="8d6d2-202">たとえば、次の XPath クエリを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-202">For example, consider this XPath query:</span></span>  
  
```  
(@m + 3) = 4  
```  
  
 <span data-ttu-id="8d6d2-203">@mが `fixed14.4` xdr データ型の場合、xdr データ型から XPath データ型への変換は、以下を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-203">If @m is of the `fixed14.4` XDR data type, the conversion from XDR data type to XPath data type is accomplished using:</span></span>  
  
```  
CONVERT(money, m)  
```  
  
 <span data-ttu-id="8d6d2-204">この変換で、ノード `m` は `fixed14.4` から `money` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-204">In this conversion, the node `m` is converted from `fixed14.4` to `money`.</span></span> <span data-ttu-id="8d6d2-205">しかし、値 3 を加算するには追加の変換が必要になります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-205">However, adding the value of 3, requires additional conversion:</span></span>  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 <span data-ttu-id="8d6d2-206">この XPath 式は、次のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-206">The XPath expression is evaluated as:</span></span>  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 <span data-ttu-id="8d6d2-207">次の表に示すように、これは、リテラルや複合式など、他の XPath 式に適用される変換と同じです。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-207">As shown in the following table, this is the same conversion that is applied for other XPath expressions (such as literals or compound expressions).</span></span>  
  
||||||  
|-|-|-|-|-|  
||<span data-ttu-id="8d6d2-208">X が不明</span><span class="sxs-lookup"><span data-stu-id="8d6d2-208">X is unknown</span></span>|<span data-ttu-id="8d6d2-209">X が `string`</span><span class="sxs-lookup"><span data-stu-id="8d6d2-209">X is `string`</span></span>|<span data-ttu-id="8d6d2-210">X が `number`</span><span class="sxs-lookup"><span data-stu-id="8d6d2-210">X is `number`</span></span>|<span data-ttu-id="8d6d2-211">X が `boolean`</span><span class="sxs-lookup"><span data-stu-id="8d6d2-211">X is `boolean`</span></span>|  
|<span data-ttu-id="8d6d2-212">string(X)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-212">string(X)</span></span>|<span data-ttu-id="8d6d2-213">CONVERT (nvarchar(4000), X, 126)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-213">CONVERT (nvarchar(4000), X, 126)</span></span>|-|<span data-ttu-id="8d6d2-214">CONVERT (nvarchar(4000), X, 126)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-214">CONVERT (nvarchar(4000), X, 126)</span></span>|<span data-ttu-id="8d6d2-215">CASE WHEN X THEN N'true' ELSE N'false' END</span><span class="sxs-lookup"><span data-stu-id="8d6d2-215">CASE WHEN X THEN N'true' ELSE N'false' END</span></span>|  
|<span data-ttu-id="8d6d2-216">number(X)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-216">number(X)</span></span>|<span data-ttu-id="8d6d2-217">CONVERT (float(53), X)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-217">CONVERT (float(53), X)</span></span>|<span data-ttu-id="8d6d2-218">CONVERT (float(53), X)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-218">CONVERT (float(53), X)</span></span>|-|<span data-ttu-id="8d6d2-219">CASE WHEN X THEN 1 ELSE 0 END</span><span class="sxs-lookup"><span data-stu-id="8d6d2-219">CASE WHEN X THEN 1 ELSE 0 END</span></span>|  
|<span data-ttu-id="8d6d2-220">boolean(X)</span><span class="sxs-lookup"><span data-stu-id="8d6d2-220">boolean(X)</span></span>|-|<span data-ttu-id="8d6d2-221">LEN (X) > 0</span><span class="sxs-lookup"><span data-stu-id="8d6d2-221">LEN(X) > 0</span></span>|<span data-ttu-id="8d6d2-222">X != 0</span><span class="sxs-lookup"><span data-stu-id="8d6d2-222">X != 0</span></span>|-|  
  
## <a name="examples"></a><span data-ttu-id="8d6d2-223">例</span><span class="sxs-lookup"><span data-stu-id="8d6d2-223">Examples</span></span>  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a><span data-ttu-id="8d6d2-224">A.</span><span class="sxs-lookup"><span data-stu-id="8d6d2-224">A.</span></span> <span data-ttu-id="8d6d2-225">XPath クエリ内のデータ型を変換する</span><span class="sxs-lookup"><span data-stu-id="8d6d2-225">Convert a data type in an XPath query</span></span>  
 <span data-ttu-id="8d6d2-226">注釈付き XSD スキーマに対して指定された次の XPath クエリでは、 **EmployeeID**属性値が E-1 のすべての**Employee**ノードが選択されます。ここで、"e-" は、注釈を使用して指定されたプレフィックスです `sql:id-prefix` 。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-226">In the following XPath query specified against an annotated XSD schema, the query selects all **Employee** nodes with the **EmployeeID** attribute value of E-1, where "E-" is the prefix specified using the `sql:id-prefix` annotation.</span></span>  
  
 `Employee[@EmployeeID="E-1"]`  
  
 <span data-ttu-id="8d6d2-227">クエリ内の述語は、次の SQL 式と等価です。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-227">The predicate in the query is equivalent to the SQL expression:</span></span>  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 <span data-ttu-id="8d6d2-228">**Employeeid**は XSD スキーマのデータ型の値 (、、、など) の1つであるため `id` `idref` `idrefs` `nmtoken` `nmtokens` 、前**EmployeeID**に `string` 説明した変換規則を使用して、employeeid を XPath データ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-228">Because **EmployeeID** is one of the `id` (`idref`, `idrefs`, `nmtoken`, `nmtokens`, and so on) data type values in the XSD schema, **EmployeeID** is converted to the `string` XPath data type using the conversion rules described previously.</span></span>  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 <span data-ttu-id="8d6d2-229">文字列に "E-" プレフィックスが追加され、結果が `N'E-1'` と比較されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-229">The "E-" prefix is added to the string, and the result is then compared with `N'E-1'`.</span></span>  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a><span data-ttu-id="8d6d2-230">B.</span><span class="sxs-lookup"><span data-stu-id="8d6d2-230">B.</span></span> <span data-ttu-id="8d6d2-231">XPath クエリ内で複数のデータ型変換を実行する</span><span class="sxs-lookup"><span data-stu-id="8d6d2-231">Perform several data type conversions in an XPath query</span></span>  
 <span data-ttu-id="8d6d2-232">注釈付き XSD スキーマに対して指定される XPath クエリ `OrderDetail[@UnitPrice * @OrderQty > 98]` を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-232">Consider this XPath query specified against an annotated XSD schema: `OrderDetail[@UnitPrice * @OrderQty > 98]`</span></span>  
  
 <span data-ttu-id="8d6d2-233">この XPath クエリは、述語を満たすすべての要素を返し **\<OrderDetail>** `@UnitPrice * @OrderQty > 98` ます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-233">This XPath query returns all the **\<OrderDetail>** elements satisfying the predicate `@UnitPrice * @OrderQty > 98`.</span></span> <span data-ttu-id="8d6d2-234">注釈付きスキーマのデータ型で、 **UnitPrice**に注釈が付けられている場合 `fixed14.4` 、この述語は SQL 式に相当します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-234">If the **UnitPrice** is annotated with a `fixed14.4` data type in the annotated schema, this predicate is equivalent to the SQL expression:</span></span>  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 <span data-ttu-id="8d6d2-235">XPath クエリ内の値を変換するとき、最初の変換では、XDR データ型を XPath データ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-235">In converting the values in the XPath query, the first conversion converts the XDR data type to the XPath data type.</span></span> <span data-ttu-id="8d6d2-236">前の表で説明したように、 **UnitPrice**の XSD データ型はであり、 `fixed14.4` 最初に使用される変換です。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-236">Because the XSD data type of **UnitPrice** is `fixed14.4`, as described in the previous table, this is the first conversion that is used:</span></span>  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 <span data-ttu-id="8d6d2-237">算術演算子ではオペランドが `number` XPath データ型に変換されるので、1 つの XPath データ型から別の XPath データ型への追加変換が適用され、値は `float(53)` に変換されます。`float(53)` に近い XPath のデータ型は `number` です。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-237">Because the arithmetic operators convert their operands to the `number` XPath data type, the second conversion (from one XPath data type to another XPath data type) is applied in which the value is converted to `float(53)` (`float(53)` is close to the XPath `number` data type):</span></span>  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 <span data-ttu-id="8d6d2-238">**Orderqty**属性に XSD データ型が含まれていない場合、 **orderqty**は `number` 1 回の変換で XPath データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-238">Assuming the **OrderQty** attribute has no XSD data type, **OrderQty** is converted to a `number` XPath data type in a single conversion:</span></span>  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 <span data-ttu-id="8d6d2-239">同様に、値 98 は `number` XPath データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-239">Similarly, the value 98 is converted to the `number` XPath data type:</span></span>  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8d6d2-240">スキーマで使用されている XSD データ型がデータベース内の基になるデータ型と互換性がない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または XPath データ型の変換が不可能な場合は、に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] よってエラーが返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-240">If the XSD data type used in the schema is incompatible with the underlying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type in the database, or if an impossible XPath data type conversion is performed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may return an error.</span></span> <span data-ttu-id="8d6d2-241">たとえば、 **employeeid**属性に注釈が付いている場合、 `id-prefix` `Employee[@EmployeeID=1]` **employeeid**には注釈があり、 `id-prefix` に変換することはできないため、XPath ではエラーが生成され `number` ます。</span><span class="sxs-lookup"><span data-stu-id="8d6d2-241">For example, if the **EmployeeID** attribute is annotated with `id-prefix` annotation, the XPath `Employee[@EmployeeID=1]` generates an error, because **EmployeeID** has the `id-prefix` annotation and cannot be converted to `number`.</span></span>  
  
  
