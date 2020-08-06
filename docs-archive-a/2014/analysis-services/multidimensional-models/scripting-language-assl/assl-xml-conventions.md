---
title: ASSL XML 規則 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- whitespace [Analysis Services Scripting Language]
- trailing whitespace
- XSD data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- cardinality [Analysis Services Scripting Language]
- white space [Analysis Services Scripting Language]
- ASSL, XML conventions
- defaults [Analysis Services Scripting Language]
- leading whitespace
- Analysis Services Scripting Language, XML conventions
- XML [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
- inherited defaults [Analysis Services Scripting Language]
ms.assetid: bce4edad-4420-41ce-9672-8c00c5c0dec6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b70742b07fd6450b01cf205147a05f40c4b6121
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736972"
---
# <a name="assl-xml-conventions"></a><span data-ttu-id="ef03c-102">ASSL XML 規則</span><span class="sxs-lookup"><span data-stu-id="ef03c-102">ASSL XML Conventions</span></span>
  <span data-ttu-id="ef03c-103">Analysis Services スクリプト言語 (ASSL) はオブジェクトの階層を要素の型のセットとして表し、それぞれが含むことのできる子要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-103">Analysis Services Scripting Language (ASSL) represents the hierarchy of objects as a set of element types, each of which defines the child elements they can contain.</span></span>  
  
 <span data-ttu-id="ef03c-104">ASSL では、次の XML 規則を使用してオブジェクトの階層を表します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-104">To represent the object hierarchy, ASSL uses the following XML conventions:</span></span>  
  
-   <span data-ttu-id="ef03c-105">' Xml: lang ' などの標準 XML 属性を除き、すべてのオブジェクトとプロパティは要素として表されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-105">All objects and properties are represented as elements, except for standard XML attributes such as 'xml:lang'.</span></span>  
  
-   <span data-ttu-id="ef03c-106">要素名と列挙値はどちらも、アンダースコアを使用しない、Pascal 文字種の Microsoft .NET Framework 名前付け規則に従います。</span><span class="sxs-lookup"><span data-stu-id="ef03c-106">Both element names and enumeration values follow the Microsoft .NET Framework naming convention of Pascal casing with no underscores.</span></span>  
  
-   <span data-ttu-id="ef03c-107">すべての値の大文字と小文字の区別が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-107">The case of all values is preserved.</span></span> <span data-ttu-id="ef03c-108">列挙の値も大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-108">Values for enumerations are also case-sensitive.</span></span>  
  
 <span data-ttu-id="ef03c-109">これらの規則の他にも、Analysis Services はカーディナリティ、継承、空白文字、データ型、既定値などに関する一定の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="ef03c-109">In addition to this list of conventions, Analysis Services also follows certain conventions regarding cardinality, inheritance, whitespace, data types, and default values.</span></span>  
  
## <a name="cardinality"></a><span data-ttu-id="ef03c-110">カーディナリティ</span><span class="sxs-lookup"><span data-stu-id="ef03c-110">Cardinality</span></span>  
 <span data-ttu-id="ef03c-111">要素に 1 より大きいカーディナリティがある場合は、この要素をカプセル化する XML 要素のコレクションがあります。</span><span class="sxs-lookup"><span data-stu-id="ef03c-111">When an element has a cardinality that is greater than 1, there is an XML element collection that encapsulates this element.</span></span> <span data-ttu-id="ef03c-112">コレクションの名前は、コレクションに含まれている要素の複数形を使用します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-112">The name of collection uses the plural form of the elements contained in the collection.</span></span> <span data-ttu-id="ef03c-113">たとえば、次の XML フラグメントは `Dimensions` 要素内の `Database` コレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-113">For example, the following XML fragment represents the `Dimensions` collection within a `Database` element:</span></span>  
  
 `<Database>`  
  
 `...`  
  
 `<Dimensions>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `</Dimensions>`  
  
 `</Database>`  
  
 ``  
  
 <span data-ttu-id="ef03c-114">要素の順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="ef03c-114">The order in which elements appear is unimportant.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="ef03c-115">継承</span><span class="sxs-lookup"><span data-stu-id="ef03c-115">Inheritance</span></span>  
 <span data-ttu-id="ef03c-116">継承は、重複しているが大幅に異なるプロパティのセットを持つ、明確に区別されるオブジェクトがある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-116">Inheritance is used when there are distinct objects that have overlapping but significantly different sets of properties.</span></span> <span data-ttu-id="ef03c-117">このように重複しているが明確に区別されるオブジェクトの例として、仮想キューブ、リンク キューブ、および標準キューブがあります。</span><span class="sxs-lookup"><span data-stu-id="ef03c-117">Examples of such overlapping but distinct objects are virtual cubes, linked cubes, and regular cubes.</span></span> <span data-ttu-id="ef03c-118">重複しているが明確に区別されるオブジェクトの場合、Analysis Services では XML インスタンス名前空間の標準的な `type` 属性を使用して、継承を示します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-118">For overlapping but distinct object, Analysis Services uses the standard `type` attribute from the XML Instance Namespace to indicate the inheritance.</span></span> <span data-ttu-id="ef03c-119">たとえば、次の XML フラグメントは、`type` 要素が標準キューブまたは仮想キューブのどちらから継承するかを `Cube` 属性が識別する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ef03c-119">For example, the following XML fragment shows how the `type` attribute identifies whether a `Cube` element inherits from a regular cube or from a virtual cube:</span></span>  
  
 `<Cubes>`  
  
 `<Cube xsi:type="RegularCube">`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type="VirtualCube">`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 <span data-ttu-id="ef03c-120">継承は通常、複数の型に同じ名前のプロパティがある場合は使用されません。</span><span class="sxs-lookup"><span data-stu-id="ef03c-120">Inheritance is generally not used when multiple types have a property of the same name.</span></span> <span data-ttu-id="ef03c-121">たとえば、`Name` プロパティと `ID` プロパティは多くの要素に含まれますが、抽象型には昇格されていません。</span><span class="sxs-lookup"><span data-stu-id="ef03c-121">For example, the `Name` and `ID` properties appear on many elements, but these properties have not been promoted to an abstract type.</span></span>  
  
## <a name="whitespace"></a><span data-ttu-id="ef03c-122">空白文字</span><span class="sxs-lookup"><span data-stu-id="ef03c-122">Whitespace</span></span>  
 <span data-ttu-id="ef03c-123">要素値内の空白文字が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-123">Whitespace within an element value is preserved.</span></span> <span data-ttu-id="ef03c-124">ただし、先頭と末尾の空白文字は常に切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-124">However, leading and trailing whitespace is always trimmed.</span></span> <span data-ttu-id="ef03c-125">たとえば、次の要素には同じテキストがありますが、そのテキスト内の空白文字の数が異なるので、別の値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-125">For example, the following elements have the same text but differing amounts of whitespace within that text, and are therefore treated as if they have different values:</span></span>  
  
 `<Description>My text<Description>`  
  
 `<Description>My  text<Description>`  
  
 ``  
  
 <span data-ttu-id="ef03c-126">しかし、次の要素は先頭と末尾の空白文字のみが異なるので、同じ値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-126">However, the following elements vary only in leading and trailing whitespace, and are therefore treated as if they have equivalent values:</span></span>  
  
 `<Description>My text<Description>`  
  
 `<Description>  My text  <Description>`  
  
 ``  
  
## <a name="data-types"></a><span data-ttu-id="ef03c-127">データ型</span><span class="sxs-lookup"><span data-stu-id="ef03c-127">Data Types</span></span>  
 <span data-ttu-id="ef03c-128">Analysis Services では、次のように XML スキーマ定義言語 (XSD) の標準的なデータ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-128">Analysis Services uses the following standard XML Schema definition language (XSD) data types:</span></span>  
  
 `Int`  
 <span data-ttu-id="ef03c-129">-231 ~ 231-1 の範囲の整数値。</span><span class="sxs-lookup"><span data-stu-id="ef03c-129">An integer value in the range of -231 to 231 - 1.</span></span>  
  
 `Long`  
 <span data-ttu-id="ef03c-130">-263 ~ 263-1 の範囲の整数値。</span><span class="sxs-lookup"><span data-stu-id="ef03c-130">An integer value in range of -263 to 263 - 1.</span></span>  
  
 `String`  
 <span data-ttu-id="ef03c-131">次のグローバル ルールに従う文字列値。</span><span class="sxs-lookup"><span data-stu-id="ef03c-131">A string value that conforms to the following global rules:</span></span>  
  
-   <span data-ttu-id="ef03c-132">制御文字は除去されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-132">Control characters are stripped out.</span></span>  
  
-   <span data-ttu-id="ef03c-133">先頭と末尾の空白文字は切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-133">Leading and trailing white space is trimmed.</span></span>  
  
-   <span data-ttu-id="ef03c-134">内部の空白文字は保持されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-134">Internal white space is preserved.</span></span>  
  
 <span data-ttu-id="ef03c-135">`Name` プロパティと `ID` プロパティには、文字列要素の有効な文字に特別な制限があります。</span><span class="sxs-lookup"><span data-stu-id="ef03c-135">`Name` and `ID` properties have special limitations on valid characters in string elements.</span></span> <span data-ttu-id="ef03c-136">および規約の詳細について `Name` `ID` は、「 [assl オブジェクトとオブジェクトの特性](assl-objects-and-object-characteristics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef03c-136">For additional information about `Name` and `ID` conventions, see [ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md).</span></span>  
  
 `DateTime`  
 <span data-ttu-id="ef03c-137">`DateTime`.NET Framework からの構造体。</span><span class="sxs-lookup"><span data-stu-id="ef03c-137">A `DateTime` structure from the .NET Framework.</span></span> <span data-ttu-id="ef03c-138">`DateTime` の値を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ef03c-138">A `DateTime` value cannot be NULL.</span></span> <span data-ttu-id="ef03c-139">`DataTime` データ型がサポートしている下限の日付は 1601 年 1 月 1 日です。プログラマはこの日付を `DateTime.MinValue` として使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-139">The lowest date supported by the `DataTime` data type is January 1, 1601, which is available to programmers as `DateTime.MinValue`.</span></span> <span data-ttu-id="ef03c-140">サポートされている下限の日付は、`DateTime` の値が欠落していることを示します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-140">The lowest supported date indicates that a `DateTime` value is missing.</span></span>  
  
 `Boolean`  
 <span data-ttu-id="ef03c-141">{true, false} や {0, 1} のように値が 2 つだけの列挙。</span><span class="sxs-lookup"><span data-stu-id="ef03c-141">An enumeration with only two values, such as {true, false} or {0, 1}.</span></span>  
  
## <a name="default-values"></a><span data-ttu-id="ef03c-142">既定値</span><span class="sxs-lookup"><span data-stu-id="ef03c-142">Default Values</span></span>  
 <span data-ttu-id="ef03c-143">Analysis Services で使用される既定値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-143">Analysis Services uses the defaults listed in the following table.</span></span>  
  
|<span data-ttu-id="ef03c-144">XML データ型</span><span class="sxs-lookup"><span data-stu-id="ef03c-144">XML data type</span></span>|<span data-ttu-id="ef03c-145">既定値</span><span class="sxs-lookup"><span data-stu-id="ef03c-145">Default value</span></span>|  
|-------------------|-------------------|  
|`Boolean`|<span data-ttu-id="ef03c-146">誤り</span><span class="sxs-lookup"><span data-stu-id="ef03c-146">False</span></span>|  
|`String`|<span data-ttu-id="ef03c-147">"" (空の文字列)</span><span class="sxs-lookup"><span data-stu-id="ef03c-147">"" (empty string)</span></span>|  
|<span data-ttu-id="ef03c-148">`Integer` または `Long`</span><span class="sxs-lookup"><span data-stu-id="ef03c-148">`Integer` or `Long`</span></span>|<span data-ttu-id="ef03c-149">0 (ゼロ)</span><span class="sxs-lookup"><span data-stu-id="ef03c-149">0 (zero)</span></span>|  
|`Timestamp`|<span data-ttu-id="ef03c-150">12:00:00 AM、1/1/0001 (0 ティックを持つ .NET Framework に対応 `System.DateTime` )</span><span class="sxs-lookup"><span data-stu-id="ef03c-150">12:00:00 AM, 1/1/0001 (corresponding to a the .NET Frameworks `System.DateTime` with 0 ticks)</span></span>|  
  
 <span data-ttu-id="ef03c-151">要素が存在するが空の場合は、既定値ではなく NULL 文字列の値を含んでいるとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-151">An element that is present but empty is interpreted as having a value of a null string, not the default value.</span></span>  
  
### <a name="inherited-defaults"></a><span data-ttu-id="ef03c-152">継承された既定値</span><span class="sxs-lookup"><span data-stu-id="ef03c-152">Inherited Defaults</span></span>  
 <span data-ttu-id="ef03c-153">オブジェクトに指定されているプロパティには、子または子孫オブジェクトの同じプロパティに既定値を提供するものがあります。</span><span class="sxs-lookup"><span data-stu-id="ef03c-153">Some properties that are specified on an object provide default values for the same property on child or descendant objects.</span></span> <span data-ttu-id="ef03c-154">たとえば、`Cube.StorageMode` は `Partition.StorageMode` に既定値を提供します。</span><span class="sxs-lookup"><span data-stu-id="ef03c-154">For example, `Cube.StorageMode` provides the default value for `Partition.StorageMode`.</span></span> <span data-ttu-id="ef03c-155">Analysis Services で継承された既定値に適用されるルールは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ef03c-155">The rules that Analysis Services applies for inherited default values are as follows:</span></span>  
  
-   <span data-ttu-id="ef03c-156">子オブジェクトのプロパティが XML で NULL の場合、その値の既定値は継承された値になります。</span><span class="sxs-lookup"><span data-stu-id="ef03c-156">When the property for the child object is null in the XML, its value defaults to the inherited value.</span></span> <span data-ttu-id="ef03c-157">ただし、サーバーから値をクエリする場合は、XML 要素の NULL 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ef03c-157">However, if you query the value from the server, the server returns the null value of the XML element.</span></span>  
  
-   <span data-ttu-id="ef03c-158">子オブジェクトのプロパティが子オブジェクトで直接設定されたか、または継承されたかをプログラムで判断することはできません。</span><span class="sxs-lookup"><span data-stu-id="ef03c-158">It is not possible to determine programmatically whether the property of a child object has been set directly on the child object or inherited.</span></span>  
  
 <span data-ttu-id="ef03c-159">一部の要素には、要素が欠落しているときに適用される既定値が定義されています。</span><span class="sxs-lookup"><span data-stu-id="ef03c-159">Some elements have defined defaults that apply when the element is missing.</span></span> <span data-ttu-id="ef03c-160">たとえば、次の XML フラグメントで、一方の `Dimension` 要素には `Dimension` 要素が含まれ、もう一方の `Visible` 要素には含まれませんが、これらの `Dimension` 要素は同じものです。</span><span class="sxs-lookup"><span data-stu-id="ef03c-160">For example, the `Dimension` elements in the following XML fragment are equivalent even though one `Dimension` element contains a `Visible` element, but the other `Dimension` element does not.</span></span>  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 <span data-ttu-id="ef03c-161">継承された既定値の詳細については、「 [Assl オブジェクトとオブジェクトの特性](assl-objects-and-object-characteristics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef03c-161">For more information on inherited defaults, see [ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md).</span></span>  
  
  
