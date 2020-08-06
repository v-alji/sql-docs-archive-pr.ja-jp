---
title: FOR XML 句の基本構文 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- BINARY BASE64 directive
- ROOT directive
- FOR XML clause, BINARY BASE64 directive
- FOR XML clause, syntax
- FOR XML clause, ROOT directive
ms.assetid: df19ecbf-d28e-4e9c-aaa3-700f8bbd3be4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc0410e7a54674673f64442d8a3cf9476d250033
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631705"
---
# <a name="basic-syntax-of-the-for-xml-clause"></a><span data-ttu-id="04169-102">FOR XML 句の基本構文</span><span class="sxs-lookup"><span data-stu-id="04169-102">Basic Syntax of the FOR XML Clause</span></span>
  <span data-ttu-id="04169-103">FOR XML モードには、RAW、AUTO、EXPLICIT、または PATH を使用できます。</span><span class="sxs-lookup"><span data-stu-id="04169-103">The FOR XML mode can be RAW, AUTO, EXPLICIT, or PATH.</span></span> <span data-ttu-id="04169-104">このモードにより、結果の XML の構造が決まります。</span><span class="sxs-lookup"><span data-stu-id="04169-104">It determines the shape of the resulting XML.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="04169-105">FOR XML オプションに対する XMLDATA ディレクティブは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="04169-105">The XMLDATA directive to the FOR XML option is deprecated.</span></span> <span data-ttu-id="04169-106">RAW モードと AUTO モードの場合は、XSD 世代を使用してください。</span><span class="sxs-lookup"><span data-stu-id="04169-106">Use XSD generation in the case of RAW and AUTO modes.</span></span> <span data-ttu-id="04169-107">EXPLICIT モードでは、XMLDATA ディレクティブに代わる機能はありません。</span><span class="sxs-lookup"><span data-stu-id="04169-107">There is no replacement for the XMLDATA directive in EXPLICT mode.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="04169-108">[FOR 句 (transact-sql)](/sql/t-sql/queries/select-for-clause-transact-sql)で説明されている基本的な構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="04169-108">Following is the basic syntax that is described in [FOR Clause (Transact-SQL)](/sql/t-sql/queries/select-for-clause-transact-sql):</span></span>  
  
```  
[ FOR { BROWSE | <XML> } ]  
<XML> ::=  
XML   
    {   
      { RAW [ ('ElementName') ] | AUTO }   
        [   
           <CommonDirectives>   
           [ , { XMLDATA | XMLSCHEMA [ ('TargetNameSpaceURI') ]} ]   
           [ , ELEMENTS [ XSINIL | ABSENT ]   
        ]  
      | EXPLICIT   
        [   
           <CommonDirectives>   
           [ , XMLDATA ]   
        ]  
      | PATH [ ('ElementName') ]   
        [   
           <CommonDirectives>   
           [ , ELEMENTS [ XSINIL | ABSENT ] ]  
        ]  
     }   
  
 <CommonDirectives> ::=   
   [ , BINARY BASE64 ]  
   [ , TYPE ]  
   [ , ROOT [ ('RootName') ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="04169-109">引数</span><span class="sxs-lookup"><span data-stu-id="04169-109">Arguments</span></span>  
 <span data-ttu-id="04169-110">RAW[('*ElementName*')]</span><span class="sxs-lookup"><span data-stu-id="04169-110">RAW[('*ElementName*')]</span></span>  
 <span data-ttu-id="04169-111">クエリの結果を取得し、結果セット内の各行を、要素タグとして汎用識別子 \<row /> を持つ XML 要素に変換します。</span><span class="sxs-lookup"><span data-stu-id="04169-111">Takes the query result and transforms each row in the result set into an XML element that has a generic identifier, \<row />, as the element tag.</span></span> <span data-ttu-id="04169-112">このディレクティブを使用するときは、必要に応じて、行要素の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="04169-112">You can optionally specify a name for the row element when you use this directive.</span></span> <span data-ttu-id="04169-113">結果の XML では、指定した *ElementName* が、行ごとに生成される行要素として使用されます。</span><span class="sxs-lookup"><span data-stu-id="04169-113">The resulting XML will use the specified *ElementName* as the row element generated for each row.</span></span> <span data-ttu-id="04169-114">詳細については、「 [FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-114">For more information, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="04169-115">AUTO</span><span class="sxs-lookup"><span data-stu-id="04169-115">AUTO</span></span>  
 <span data-ttu-id="04169-116">クエリの結果を単純な入れ子の XML ツリーで返します。</span><span class="sxs-lookup"><span data-stu-id="04169-116">Returns query results in a simple, nested XML tree.</span></span> <span data-ttu-id="04169-117">1 つ以上の列が SELECT 句にリストされている FROM 句の各テーブルは、XML 要素として表されます。</span><span class="sxs-lookup"><span data-stu-id="04169-117">Each table in the FROM clause for which at least one column is listed in the SELECT clause is represented as an XML element.</span></span> <span data-ttu-id="04169-118">SELECT 句に一覧されている列は、該当する要素属性にマップされます。</span><span class="sxs-lookup"><span data-stu-id="04169-118">The columns listed in the SELECT clause are mapped to the appropriate element attributes.</span></span> <span data-ttu-id="04169-119">詳細については、「 [FOR XML での AUTO モードの使用](use-auto-mode-with-for-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-119">For more information, see [Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="04169-120">EXPLICIT</span><span class="sxs-lookup"><span data-stu-id="04169-120">EXPLICIT</span></span>  
 <span data-ttu-id="04169-121">結果として得られる XML ツリーの形状を明示的に定義することを指定します。</span><span class="sxs-lookup"><span data-stu-id="04169-121">Specifies that the shape of the resulting XML tree is defined explicitly.</span></span> <span data-ttu-id="04169-122">このモードを使用する場合は、クエリを特殊な方法で記述することにより、目的の入れ子構造に関して追加情報を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04169-122">By using this mode, queries must be written in a particular way so additional information about the nesting you want is specified explicitly.</span></span> <span data-ttu-id="04169-123">詳細については、「 [FOR XML での EXPLICIT モードの使用](use-explicit-mode-with-for-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-123">For more information, see [Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="04169-124">PATH</span><span class="sxs-lookup"><span data-stu-id="04169-124">PATH</span></span>  
 <span data-ttu-id="04169-125">PATH モードを使用すると、要素と属性を組み合わせた使用が容易になり、入れ子構造を使用することで、複雑なプロパティも容易に表現できるようになります。</span><span class="sxs-lookup"><span data-stu-id="04169-125">Provides a simpler way to mix elements and attributes, and to introduce additional nesting for representing complex properties.</span></span> <span data-ttu-id="04169-126">FOR XML EXPLICIT モードのクエリを使用してこのような XML を行セットから作成することもできますが、煩雑になりかねない EXPLICIT モードのクエリに比べて PATH モードでは同じことを簡潔に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="04169-126">You can use FOR XML EXPLICIT mode queries to construct this kind of XML from a rowset, but the PATH mode provides a simpler alternative to the possibly cumbersome EXPLICIT mode queries.</span></span> <span data-ttu-id="04169-127">PATH モードに、入れ子の FOR XML クエリと、 **xml** 型のインスタンスを返す TYPE ディレクティブを組み合わせることで、簡潔なクエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="04169-127">PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.</span></span> <span data-ttu-id="04169-128">この方法により、EXPLICIT モードのクエリの大半を書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="04169-128">It provides an alternative to writing most EXPLICIT mode queries.</span></span> <span data-ttu-id="04169-129">既定で、PATH モードは結果セットの行ごとに \<row> 要素ラッパーを生成します。</span><span class="sxs-lookup"><span data-stu-id="04169-129">By default, PATH mode generates a \<row> element wrapper for each row in the result set.</span></span> <span data-ttu-id="04169-130">要素名は、必要に応じて指定できます。</span><span class="sxs-lookup"><span data-stu-id="04169-130">You can optionally specify an element name.</span></span> <span data-ttu-id="04169-131">要素名を指定すると、指定した名前が囲み要素名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="04169-131">If you do, the specified name is used as the wrapper element name.</span></span> <span data-ttu-id="04169-132">空の文字列 (FOR XML PATH ('')) を指定すると、囲み要素は生成されません。</span><span class="sxs-lookup"><span data-stu-id="04169-132">If you provide an empty string (FOR XML PATH ('')), no wrapper element is generated.</span></span> <span data-ttu-id="04169-133">詳細については、「 [FOR XML での PATH モードの使用](use-path-mode-with-for-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-133">For more information, see [Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="04169-134">XMLDATA</span><span class="sxs-lookup"><span data-stu-id="04169-134">XMLDATA</span></span>  
 <span data-ttu-id="04169-135">インライン XDR (XML-Data Reduced) スキーマが返されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="04169-135">Specifies that an inline XML-Data Reduced (XDR) schema should be returned.</span></span> <span data-ttu-id="04169-136">このスキーマは、ドキュメントの前にインライン スキーマとして付加されます。</span><span class="sxs-lookup"><span data-stu-id="04169-136">The schema is prepended to the document as an inline schema.</span></span> <span data-ttu-id="04169-137">作業用サンプルについては、「 [FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-137">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="04169-138">XMLSCHEMA</span><span class="sxs-lookup"><span data-stu-id="04169-138">XMLSCHEMA</span></span>  
 <span data-ttu-id="04169-139">インライン W3C XML スキーマ (XSD) を返します。</span><span class="sxs-lookup"><span data-stu-id="04169-139">Returns an inline W3C XML Schema (XSD).</span></span> <span data-ttu-id="04169-140">このディレクティブを指定する場合は、必要に応じて対象名前空間 URI を指定できます。</span><span class="sxs-lookup"><span data-stu-id="04169-140">You can optionally specify a target namespace URI when specifying this directive.</span></span> <span data-ttu-id="04169-141">これにより、スキーマで指定した名前空間が返されます。</span><span class="sxs-lookup"><span data-stu-id="04169-141">This returns the specified namespace in the schema.</span></span> <span data-ttu-id="04169-142">詳細については、「 [Generate an Inline XSD Schema](generate-an-inline-xsd-schema.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-142">For more information, see [Generate an Inline XSD Schema](generate-an-inline-xsd-schema.md).</span></span> <span data-ttu-id="04169-143">作業用サンプルについては、「 [FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-143">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="04169-144">ELEMENTS</span><span class="sxs-lookup"><span data-stu-id="04169-144">ELEMENTS</span></span>  
 <span data-ttu-id="04169-145">ELEMENTS オプションを指定すると、列が副要素として返されます。</span><span class="sxs-lookup"><span data-stu-id="04169-145">If the ELEMENTS option is specified, the columns are returned as subelements.</span></span> <span data-ttu-id="04169-146">指定していない場合は、XML 属性にマップされます。</span><span class="sxs-lookup"><span data-stu-id="04169-146">Otherwise, they are mapped to XML attributes.</span></span> <span data-ttu-id="04169-147">このオプションは、RAW、AUTO、および PATH の各モードでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="04169-147">This option is supported in RAW, AUTO, and PATH modes only.</span></span> <span data-ttu-id="04169-148">このディレクティブを使用する場合は、必要に応じて XSINIL または ABSENT を指定できます。</span><span class="sxs-lookup"><span data-stu-id="04169-148">You can optionally specify XSINIL or ABSENT when you use this directive.</span></span> <span data-ttu-id="04169-149">XSINIL は、NULL 列の値に対して、 **xsi:nil** 属性が True に設定された要素を作成することを指定します。</span><span class="sxs-lookup"><span data-stu-id="04169-149">XSINIL specifies that an element that has an **xsi:nil** attribute set to True be created for NULL column values.</span></span> <span data-ttu-id="04169-150">既定の状態や、ABSENT が ELEMENTS と共に指定されている場合は、NULL 値に対して要素は作成されません。</span><span class="sxs-lookup"><span data-stu-id="04169-150">By default or when ABSENT is specified together with ELEMENTS, no elements are created for NULL values.</span></span> <span data-ttu-id="04169-151">作業用サンプルについては、「 [FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md) 」 および 「 [FOR XML での AUTO モードの使用](use-auto-mode-with-for-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-151">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md) and [Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="04169-152">BINARY BASE64</span><span class="sxs-lookup"><span data-stu-id="04169-152">BINARY BASE64</span></span>  
 <span data-ttu-id="04169-153">BINARY Base64 オプションを指定した場合、クエリの返すバイナリ データは Base64 エンコード形式で表されます。</span><span class="sxs-lookup"><span data-stu-id="04169-153">If the BINARY Base64 option is specified, any binary data returned by the query is represented in base64-encoded format.</span></span> <span data-ttu-id="04169-154">RAW モードおよび EXPLICIT モードでバイナリ データを取得する場合は、このオプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04169-154">To retrieve binary data by using RAW and EXPLICIT mode, this option must be specified.</span></span> <span data-ttu-id="04169-155">AUTO モードでは、特に指定しない限りバイナリ データが参照として返されます。</span><span class="sxs-lookup"><span data-stu-id="04169-155">In AUTO mode, binary data is returned as a reference by default.</span></span> <span data-ttu-id="04169-156">作業用サンプルについては、「 [FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-156">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="04169-157">TYPE</span><span class="sxs-lookup"><span data-stu-id="04169-157">TYPE</span></span>  
 <span data-ttu-id="04169-158">クエリが結果を **xml** 型で返すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="04169-158">Specifies that the query returns the results as the **xml** type.</span></span> <span data-ttu-id="04169-159">詳細については、「 [FOR XML クエリの TYPE ディレクティブ](type-directive-in-for-xml-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04169-159">For more information, see [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md).</span></span>  
  
 <span data-ttu-id="04169-160">ROOT [('*RootName*')]</span><span class="sxs-lookup"><span data-stu-id="04169-160">ROOT [('*RootName*')]</span></span>  
 <span data-ttu-id="04169-161">結果の XML に、1 つの最上位要素が追加されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="04169-161">Specifies that a single, top-level element be added to the resulting XML.</span></span> <span data-ttu-id="04169-162">必要に応じて、生成するルート要素名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="04169-162">You can optionally specify the root element name to generate.</span></span> <span data-ttu-id="04169-163">既定値は "root" です。</span><span class="sxs-lookup"><span data-stu-id="04169-163">The default value is "root".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04169-164">参照</span><span class="sxs-lookup"><span data-stu-id="04169-164">See Also</span></span>  
 <span data-ttu-id="04169-165">[FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="04169-165">[Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="04169-166">[FOR XML での AUTO モードの使用](use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="04169-166">[Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="04169-167">[FOR XML での EXPLICIT モードの使用](use-explicit-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="04169-167">[Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="04169-168">[FOR XML での PATH モードの使用](use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="04169-168">[Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="04169-169">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="04169-169">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="04169-170">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="04169-170">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
