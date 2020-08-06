---
title: クエリ式と Uniform Resource Name | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- query expressions
- unique resource names
- URN
ms.assetid: e0d30dbe-7daf-47eb-8412-1b96792b6fb9
author: stevestein
ms.author: sstein
ms.openlocfilehash: db6e311dd7d8a824b0e2f22e538e15eefa9fd9ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640118"
---
# <a name="query-expressions-and-uniform-resource-names"></a><span data-ttu-id="4cbb9-102">クエリ式と Uniform Resource Name</span><span class="sxs-lookup"><span data-stu-id="4cbb9-102">Query Expressions and Uniform Resource Names</span></span>
  <span data-ttu-id="4cbb9-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) モデルおよび [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell スナップインでは、XPath 式に似た、2 種類の式文字列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object (SMO) models and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins use two types of expression strings that are similar to XPath expressions.</span></span> <span data-ttu-id="4cbb9-104">クエリ式は、オブジェクト モデル階層内の 1 つまたは複数のオブジェクトを列挙するための条件のセットを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-104">Query expressions are strings that specify a set of criteria used to enumerate one or more objects in an object model hierarchy.</span></span> <span data-ttu-id="4cbb9-105">URN (Uniform Resource Name) は、単一のオブジェクトを一意に識別する特定の種類のクエリ式文字列です。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-105">A Uniform Resource Name (URN) is a specific type of query expression string that uniquely identifies a single object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cbb9-106">構文</span><span class="sxs-lookup"><span data-stu-id="4cbb9-106">Syntax</span></span>  
  
```
      Object1  
      [<FilterExpression1>]/ ... /ObjectN[<FilterExpressionN>]<FilterExpression>::=  
<PropertyExpression> [and <PropertyExpression>][...n]  
  
<PropertyExpression>::=@BooleanPropertyName=true()  
 | @BooleanPropertyName=false()  
 | contains(@StringPropertyName, 'PatternString')  
  | @StringPropertyName='String'  
 | @DatePropertyName=datetime('DateString')  
 | is_null(@PropertyName)  
 | not(<PropertyExpression>)  
```  
  
## <a name="arguments"></a><span data-ttu-id="4cbb9-107">引数</span><span class="sxs-lookup"><span data-stu-id="4cbb9-107">Arguments</span></span>  
 <span data-ttu-id="4cbb9-108">*Object*</span><span class="sxs-lookup"><span data-stu-id="4cbb9-108">*Object*</span></span>  
 <span data-ttu-id="4cbb9-109">オブジェクトの種類を指定します。オブジェクトの種類は、式文字列のこのノードで表されます。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-109">Specifies the type of object that is represented at that node of the expression string.</span></span> <span data-ttu-id="4cbb9-110">各オブジェクトは、これらの SMO オブジェクト モデルの名前空間からのコレクション クラスを表します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-110">Each object represents a collection class from these SMO object model namespaces:</span></span>  
  
 <xref:Microsoft.SqlServer.Management.Smo>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Agent>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Mail>  
  
 <xref:Microsoft.SqlServer.Management.Dmf>  
  
 <xref:Microsoft.SqlServer.Management.Facets>  
  
 <xref:Microsoft.SqlServer.Management.RegisteredServers>  
  
 <xref:Microsoft.SqlServer.Management.Smo.RegSvrEnum>  
  
 <span data-ttu-id="4cbb9-111">たとえば、サーバーでは **ServerCollection** クラスを、データベースでは **DatabaseCollection** クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-111">For example, specify Server for the **ServerCollection** class, Database for the **DatabaseCollection** class.</span></span>  
  
 <span data-ttu-id="4cbb9-112">\@*PropertyName*</span><span class="sxs-lookup"><span data-stu-id="4cbb9-112">\@*PropertyName*</span></span>  
 <span data-ttu-id="4cbb9-113">*Object*に指定したオブジェクトと関連付けるクラスのいずれかのプロパティの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-113">Specifies the name of one of the properties of the class that is associated with the object specified in *Object*.</span></span> <span data-ttu-id="4cbb9-114">プロパティの名前の前に \@ 文字を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-114">The name of the property must be prefixed with the \@ character.</span></span> <span data-ttu-id="4cbb9-115">たとえば、 \@ **データベース**クラスプロパティ**IsAnsiNull**に IsAnsiNull を指定します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-115">For example, specify \@IsAnsiNull for the **Database** class property **IsAnsiNull**.</span></span>  
  
 <span data-ttu-id="4cbb9-116">\@*BooleanPropertyName*= true ()</span><span class="sxs-lookup"><span data-stu-id="4cbb9-116">\@*BooleanPropertyName*=true()</span></span>  
 <span data-ttu-id="4cbb9-117">指定したブール型のプロパティが TRUE に設定されているすべてのオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-117">Enumerates all objects where the specified Boolean property is set to TRUE.</span></span>  
  
 <span data-ttu-id="4cbb9-118">\@*BooleanPropertyName*= false ()</span><span class="sxs-lookup"><span data-stu-id="4cbb9-118">\@*BooleanPropertyName*=false()</span></span>  
 <span data-ttu-id="4cbb9-119">指定したブール型のプロパティが FALSE に設定されているすべてのオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-119">Enumerates all objects where the specified Boolean property is set to FALSE.</span></span>  
  
 <span data-ttu-id="4cbb9-120">contains ( \@ *stringpropertyname*, '*pattern string*')</span><span class="sxs-lookup"><span data-stu-id="4cbb9-120">contains(\@*StringPropertyName*, '*PatternString*')</span></span>  
 <span data-ttu-id="4cbb9-121">指定した文字列プロパティに '*PatternString*' に指定した文字のセットが 1 つ以上含まれるすべてのオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-121">Enumerates all objects where the specified string property contains at least one occurrence of the set of characters that is specified in '*PatternString*'.</span></span>  
  
 <span data-ttu-id="4cbb9-122">\@*Stringpropertyname*= '*pattern string*'</span><span class="sxs-lookup"><span data-stu-id="4cbb9-122">\@*StringPropertyName*='*PatternString*'</span></span>  
 <span data-ttu-id="4cbb9-123">指定した文字列プロパティの値が '*PatternString*' に指定した文字パターンとまったく同じであるすべてのオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-123">Enumerates all objects where the value of the specified string property is exactly the same as the character pattern that is specified in '*PatternString*'.</span></span>  
  
 <span data-ttu-id="4cbb9-124">\@*Datepropertyname*= datetime ('*datepropertyname*')</span><span class="sxs-lookup"><span data-stu-id="4cbb9-124">\@*DatePropertyName*= datetime('*DateString*')</span></span>  
 <span data-ttu-id="4cbb9-125">指定した日付プロパティの値が '*DateString*' に指定した日付と一致するすべてのオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-125">Enumerates all objects where the value of the specified date property matches the date that is specified in '*DateString*'.</span></span> <span data-ttu-id="4cbb9-126">*DateString* は、yyyy-mm-dd hh:mi:ss.mmm 形式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-126">*DateString* must follow the format yyyy-mm-dd hh:mi:ss.mmm</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4cbb9-127">yyyy</span><span class="sxs-lookup"><span data-stu-id="4cbb9-127">yyyy</span></span>|<span data-ttu-id="4cbb9-128">年を表す 4 桁の数字。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-128">Four digit year.</span></span>|  
|<span data-ttu-id="4cbb9-129">mm</span><span class="sxs-lookup"><span data-stu-id="4cbb9-129">mm</span></span>|<span data-ttu-id="4cbb9-130">月を表す 2 桁の数字 (01 ～ 12)。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-130">Two digit month (01 through 12).</span></span>|  
|<span data-ttu-id="4cbb9-131">dd</span><span class="sxs-lookup"><span data-stu-id="4cbb9-131">dd</span></span>|<span data-ttu-id="4cbb9-132">日を表す 2 桁の数字 (01 ～ 31)。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-132">Two digit date (01 through 31).</span></span>|  
|<span data-ttu-id="4cbb9-133">hh</span><span class="sxs-lookup"><span data-stu-id="4cbb9-133">hh</span></span>|<span data-ttu-id="4cbb9-134">時を 24 時間形式で表す 2 桁の数字 (01 ～ 23)。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-134">Two digit hour using a 24 hour clock (01 through 23).</span></span>|  
|<span data-ttu-id="4cbb9-135">mi</span><span class="sxs-lookup"><span data-stu-id="4cbb9-135">mi</span></span>|<span data-ttu-id="4cbb9-136">分を表す 2 桁の数字 (01 ～ 59)。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-136">Two digit minutes (01 through 59).</span></span>|  
|<span data-ttu-id="4cbb9-137">ss</span><span class="sxs-lookup"><span data-stu-id="4cbb9-137">ss</span></span>|<span data-ttu-id="4cbb9-138">秒を表す 2 桁の数字 (01 ～ 59)。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-138">Two digit seconds (01 through 59).</span></span>|  
|<span data-ttu-id="4cbb9-139">mmm</span><span class="sxs-lookup"><span data-stu-id="4cbb9-139">mmm</span></span>|<span data-ttu-id="4cbb9-140">ミリ秒数 (001 ～ 999)。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-140">Number of milliseconds (001 through 999).</span></span>|  
  
 <span data-ttu-id="4cbb9-141">この形式で指定された日付は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に格納されているすべての日付形式に対して評価できます。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-141">The dates that are specified in this format can be evaluated against any date format that is stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="4cbb9-142">is_null ( \@ *PropertyName*)</span><span class="sxs-lookup"><span data-stu-id="4cbb9-142">is_null(\@*PropertyName*)</span></span>  
 <span data-ttu-id="4cbb9-143">指定したプロパティの値が NULL であるすべてのオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-143">Enumerates all objects where the specified property has a value of NULL.</span></span>  
  
 <span data-ttu-id="4cbb9-144">not ( \<*PropertyExpression*> )</span><span class="sxs-lookup"><span data-stu-id="4cbb9-144">not(\<*PropertyExpression*>)</span></span>  
 <span data-ttu-id="4cbb9-145">*PropertyExpression*の評価値を否定して、 *PropertyExpression*に指定した条件に一致しないすべてのオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-145">Negates the evaluation value of the *PropertyExpression*, enumerating all objects that do not match the condition specified in *PropertyExpression*.</span></span> <span data-ttu-id="4cbb9-146">たとえば、not(contains(\@Name, 'xyz')) と指定した場合、名前に xyz という文字列が含まれないすべてのオブジェクトが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-146">For example, not(contains(\@Name, 'xyz')) enumerates all objects that do not have the string xyz in their names.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cbb9-147">解説</span><span class="sxs-lookup"><span data-stu-id="4cbb9-147">Remarks</span></span>  
 <span data-ttu-id="4cbb9-148">クエリ式は、SMO モデル階層のノードを列挙する文字列です。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-148">Query expressions are strings that enumerate the nodes in an SMO model hierarchy.</span></span> <span data-ttu-id="4cbb9-149">各ノードには、そのノードのどのオブジェクトを列挙するかを決定する条件を指定するためのフィルター式があります。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-149">Each node has a filter expression that specifies the criteria for determining which objects at that node are enumerated.</span></span> <span data-ttu-id="4cbb9-150">クエリ式は、XPath 式言語をモデル化したものです。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-150">Query expressions are modeled on the XPath expression language.</span></span> <span data-ttu-id="4cbb9-151">クエリ式は、XPath でサポートされる式の小さなサブセットを実装し、XPath には用意されていないいくつかの拡張を含みます。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-151">Query expressions implement a small subset of the expressions that are supported by XPath, and also have some extensions that are not found in XPath.</span></span> <span data-ttu-id="4cbb9-152">XPath 式は、XML ドキュメント内の 1 つまたは複数のタグを列挙するための条件のセットを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-152">XPath expressions are strings that specify a set of criteria that are used to enumerate one or more of the tags in an XML document.</span></span> <span data-ttu-id="4cbb9-153">XPath の詳細については、 [W3C XPath 言語の Web サイト](http://www.w3.org/TR/xpath20/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-153">For more information about XPath, see [W3C XPath Language](http://www.w3.org/TR/xpath20/).</span></span>  
  
 <span data-ttu-id="4cbb9-154">クエリ式は、Server オブジェクトへの絶対参照で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-154">Query expressions must start with an absolute reference to the Server object.</span></span> <span data-ttu-id="4cbb9-155">/ で始まる相対的な式は使用できません。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-155">Relative expressions with a leading / are not allowed.</span></span> <span data-ttu-id="4cbb9-156">クエリ式に指定するオブジェクトの順序は、関連付けられたオブジェクト モデルのコレクション オブジェクトの階層に従っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-156">The sequence of objects that are specified in a query expression must follow the hierarchy of collection objects in the associated object model.</span></span> <span data-ttu-id="4cbb9-157">たとえば、Microsoft.SqlServer.Management.Smo 名前空間のオブジェクトを参照するクエリ式は、Server ノードで開始し、続けて Database ノードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-157">For example, a query expression that references objects in the Microsoft.SqlServer.Management.Smo namespace must start with a Server node followed by a Database node, and so on.</span></span>  
  
 <span data-ttu-id="4cbb9-158">*\<FilterExpression>* がオブジェクトに対して指定されていない場合は、そのノードのすべてのオブジェクトが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-158">If a *\<FilterExpression>* is not specified for an object, all the objects at that node are enumerated.</span></span>  
  
## <a name="uniform-resource-names-urn"></a><span data-ttu-id="4cbb9-159">URN (Uniform Resource Name)</span><span class="sxs-lookup"><span data-stu-id="4cbb9-159">Uniform Resource Names (URN)</span></span>  
 <span data-ttu-id="4cbb9-160">URN は、クエリ式のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-160">URNs are a subset of query expressions.</span></span> <span data-ttu-id="4cbb9-161">それぞれの URN は、1 つのオブジェクトへの完全修飾参照を示します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-161">Each URN forms a fully-qualified reference to a single object.</span></span> <span data-ttu-id="4cbb9-162">一般的な URN では、Name プロパティを使用して、各ノードの単独のオブジェクトを識別します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-162">A typical URN uses the Name property to identify a single object at each node.</span></span> <span data-ttu-id="4cbb9-163">たとえば、次の URN は特定の列を参照します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-163">For example, this URN refers to a specific column:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[@Name='SalesPerson' and @Schema='Sales']/Column[@Name='SalesPersonID']  
```  
  
## <a name="examples"></a><span data-ttu-id="4cbb9-164">例</span><span class="sxs-lookup"><span data-stu-id="4cbb9-164">Examples</span></span>  
  
### <a name="a-enumerating-objects-using-false"></a><span data-ttu-id="4cbb9-165">A.</span><span class="sxs-lookup"><span data-stu-id="4cbb9-165">A.</span></span> <span data-ttu-id="4cbb9-166">false() を使用したオブジェクトの列挙</span><span class="sxs-lookup"><span data-stu-id="4cbb9-166">Enumerating objects using false()</span></span>  
 <span data-ttu-id="4cbb9-167">このクエリ式は、 **MyComputer** 上の既定のインスタンスにおいて **AutoClose**属性が false に設定されているすべてのデータベースを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-167">This query expression enumerates all the databases that have the **AutoClose** attribute set to false in the default instance on **MyComputer**.</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@AutoClose=false()]  
```  
  
### <a name="b-enumerating-objects-using-contains"></a><span data-ttu-id="4cbb9-168">B.</span><span class="sxs-lookup"><span data-stu-id="4cbb9-168">B.</span></span> <span data-ttu-id="4cbb9-169">contains を使用したオブジェクトの列挙</span><span class="sxs-lookup"><span data-stu-id="4cbb9-169">Enumerating objects using contains</span></span>  
 <span data-ttu-id="4cbb9-170">このクエリ式は、大文字と小文字が区別されない、名前に m という文字を含むすべてのデータベースを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-170">This query expression enumerates all the databases that are case-insensitive and have the character 'm' in their name.</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@CaseSensitive=false() and contains(@Name, 'm')]   
```  
  
### <a name="c-enumerating-objects-using-not"></a><span data-ttu-id="4cbb9-171">C.</span><span class="sxs-lookup"><span data-stu-id="4cbb9-171">C.</span></span> <span data-ttu-id="4cbb9-172">not を使用したオブジェクトの列挙</span><span class="sxs-lookup"><span data-stu-id="4cbb9-172">Enumerating objects using not</span></span>  
 <span data-ttu-id="4cbb9-173">このクエリ式は、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Production **スキーマに含まれていない、テーブル名に History という単語を含むすべての** テーブルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-173">This query expression enumerates all of [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] tables that are not in the **Production** schema and contain the word History in the table name:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[not(@Schema='Production') and contains(@Name, 'History')]  
```  
  
### <a name="d-not-supplying-a-filter-expression-for-the-final-node"></a><span data-ttu-id="4cbb9-174">D.</span><span class="sxs-lookup"><span data-stu-id="4cbb9-174">D.</span></span> <span data-ttu-id="4cbb9-175">最後のノードのフィルター式を省略した例</span><span class="sxs-lookup"><span data-stu-id="4cbb9-175">Not supplying a filter expression for the final node</span></span>  
 <span data-ttu-id="4cbb9-176">このクエリ式は、 **AdventureWorks2012.Sales.SalesPerson** テーブル内のすべての列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-176">This query expression enumerates all the columns in the **AdventureWorks2012.Sales.SalesPerson** table:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@Schema='Sales' and @Name='SalesPerson']/Columns  
```  
  
### <a name="e-enumerating-objects-using-datetime"></a><span data-ttu-id="4cbb9-177">E.</span><span class="sxs-lookup"><span data-stu-id="4cbb9-177">E.</span></span> <span data-ttu-id="4cbb9-178">datetime を使用したオブジェクトの列挙</span><span class="sxs-lookup"><span data-stu-id="4cbb9-178">Enumerating objects using datetime</span></span>  
 <span data-ttu-id="4cbb9-179">このクエリ式は、特定の時刻に [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースに作成されたすべてのテーブルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-179">This query expression enumerates all the tables that are created in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database at a specific time:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@CreateDate=datetime('2008-03-21 19:49:32.647')]  
```  
  
### <a name="f-enumerating-objects-using-is_null"></a><span data-ttu-id="4cbb9-180">F.</span><span class="sxs-lookup"><span data-stu-id="4cbb9-180">F.</span></span> <span data-ttu-id="4cbb9-181">is_null を使用したオブジェクトの列挙</span><span class="sxs-lookup"><span data-stu-id="4cbb9-181">Enumerating objects using is_null</span></span>  
 <span data-ttu-id="4cbb9-182">このクエリ式は、最終更新日プロパティの値が NULL ではない [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース内のすべてのテーブルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cbb9-182">This query expression enumerates all the tables in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database that do not have NULL for their date last modified property:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[Not(is_null(@DateLastModified))]  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cbb9-183">参照</span><span class="sxs-lookup"><span data-stu-id="4cbb9-183">See Also</span></span>  
 <span data-ttu-id="4cbb9-184">[呼び出し-Policの評価コマンドレット](../database-engine/invoke-policyevaluation-cmdlet.md) </span><span class="sxs-lookup"><span data-stu-id="4cbb9-184">[Invoke-PolicyEvaluation cmdlet](../database-engine/invoke-policyevaluation-cmdlet.md) </span></span>  
 [<span data-ttu-id="4cbb9-185">SQL Server Audit &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="4cbb9-185">SQL Server Audit &#40;Database Engine&#41;</span></span>](../relational-databases/security/auditing/sql-server-audit-database-engine.md)  
