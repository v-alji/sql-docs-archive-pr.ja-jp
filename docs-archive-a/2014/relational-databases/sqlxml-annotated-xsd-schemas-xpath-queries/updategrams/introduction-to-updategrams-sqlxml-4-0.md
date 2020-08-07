---
title: アップデートグラムの概要 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- updategrams [SQLXML], mapping schema specifying
- namespaces [SQLXML]
- updategrams [SQLXML], about updategrams
- attribute-centric mapping
- invalid characters [SQLXML]
- element-centric mapping [SQLXML]
- mapping schema [SQLXML], updategrams
- namespaces [SQLXML], updategrams
- executing updategrams [SQLXML]
- implicit schema mapping
ms.assetid: cfe24e82-a645-4f93-ab16-39c21f90cce6
author: rothja
ms.author: jroth
ms.openlocfilehash: eb2f29d7f5d86d28254dacb9c55cceb9b4c72d8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716126"
---
# <a name="introduction-to-updategrams-sqlxml-40"></a><span data-ttu-id="5001d-102">アップデートグラムの概要 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="5001d-102">Introduction to Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="5001d-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アップデートグラムまたは OPENXML 関数を使用して、既存の XML ドキュメントからデータベースを変更 (挿入、更新、または削除) することができ [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-103">You can modify (insert, update, or delete) a database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from an existing XML document by using an updategram or the OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="5001d-104">OPENXML 関数は、既存の XML ドキュメントを断片化し、INSERT、UPDATE または DELETE ステートメントに渡すことができる行セットを提供することで、データベースを変更する関数です。</span><span class="sxs-lookup"><span data-stu-id="5001d-104">The OPENXML function modifies a database by shredding the existing XML document and providing a rowset that can be passed to an INSERT, UPDATE, or DELETE statement.</span></span> <span data-ttu-id="5001d-105">OPENXML を使用すると、データベース テーブルに対して操作を直接実行できます。</span><span class="sxs-lookup"><span data-stu-id="5001d-105">With OPENXML, operations are performed directly against the database tables.</span></span> <span data-ttu-id="5001d-106">したがって、ソースにテーブルなどの行セット プロバイダーがある場合は常に、OPENXML を使用するのが最適です。</span><span class="sxs-lookup"><span data-stu-id="5001d-106">Therefore, OPENXML is most appropriate wherever rowset providers, such as a table, can appear as a source.</span></span>  
  
 <span data-ttu-id="5001d-107">アップデートグラムを使用すると、OPENXML と同様にデータベースに対してデータを挿入、更新、または削除できます。ただし、アップデートグラムは注釈付き XSD (または XDR) スキーマにより提供される XML ビューに対して動作します。たとえば、更新はマッピング スキーマにより提供される XML ビューに適用されます。</span><span class="sxs-lookup"><span data-stu-id="5001d-107">Like OPENXML, an updategram allows you to insert, update, or delete data in the database; however, an updategram works against the XML views provided by the annotated XSD (or an XDR) schema; for example, the updates are applied to the XML view provided by the mapping schema.</span></span> <span data-ttu-id="5001d-108">マッピング スキーマには、XML 要素と属性を対応するデータベース テーブルと列にマップするための、必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5001d-108">The mapping schema, in turn, has the necessary information to map XML elements and attributes to the corresponding database tables and columns.</span></span> <span data-ttu-id="5001d-109">アップデートグラムでは、このマッピング情報を使用してデータベース テーブルと列が更新されます。</span><span class="sxs-lookup"><span data-stu-id="5001d-109">The updategram uses this mapping information to update the database tables and columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5001d-110">このドキュメントは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされるテンプレートとマッピング スキーマについて理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="5001d-110">This documentation assumes that you are familiar with templates and mapping schema support in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5001d-111">詳細については、「[注釈付き XSD スキーマの概要 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5001d-111">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="5001d-112">XDR を使用するレガシアプリケーションでは、 [SQLXML 4.0&#41;では、注釈付き Xdr スキーマ &#40;非推奨](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)とされています。</span><span class="sxs-lookup"><span data-stu-id="5001d-112">For legacy applications that use XDR, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="required-namespaces-in-the-updategram"></a><span data-ttu-id="5001d-113">アップデートグラムで必要な名前空間</span><span class="sxs-lookup"><span data-stu-id="5001d-113">Required Namespaces in the Updategram</span></span>  
 <span data-ttu-id="5001d-114">、、などのアップデートグラムのキーワードは、 **\<sync>** **\<before>** **\<after>** 名前空間に存在し `urn:schemas-microsoft-com:xml-updategram` ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-114">The keywords in an updategram, such as **\<sync>**, **\<before>**, and **\<after>**, exist in the `urn:schemas-microsoft-com:xml-updategram` namespace.</span></span> <span data-ttu-id="5001d-115">名前空間プレフィックスは、任意のものを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5001d-115">The namespace prefix that you use is arbitrary.</span></span> <span data-ttu-id="5001d-116">このドキュメントでは、`updg` 名前空間を表すものとして `updategram` プレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="5001d-116">In this documentation, the `updg` prefix denotes the `updategram` namespace.</span></span>  
  
## <a name="reviewing-syntax"></a><span data-ttu-id="5001d-117">構文の確認</span><span class="sxs-lookup"><span data-stu-id="5001d-117">Reviewing Syntax</span></span>  
 <span data-ttu-id="5001d-118">アップデートグラムは、、、およびの各ブロックを含むテンプレートで、 **\<sync>** **\<before>** **\<after>** アップデートグラムの構文を形成します。</span><span class="sxs-lookup"><span data-stu-id="5001d-118">An updategram is a template with **\<sync>**, **\<before>**, and **\<after>** blocks that form the syntax of the updategram.</span></span> <span data-ttu-id="5001d-119">次のコードは、最も単純な構文です。</span><span class="sxs-lookup"><span data-stu-id="5001d-119">The following code shows this syntax in its simplest form:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema= "AnnotatedSchemaFile.xml"] >  
    <updg:before>  
        ...  
    </updg:before>  
    <updg:after>  
        ...  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="5001d-120">次に、これらの各ブロックの役割について説明します。</span><span class="sxs-lookup"><span data-stu-id="5001d-120">The following definitions describe the role of each of these blocks:</span></span>  
  
 **\<before>**  
 <span data-ttu-id="5001d-121">レコード インスタンスの既存の状態 ("before 状態") を指定します。</span><span class="sxs-lookup"><span data-stu-id="5001d-121">Identifies the existing state (also called "the before state") of the record instance.</span></span>  
  
 **\<after>**  
 <span data-ttu-id="5001d-122">データの変更後の新しい状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="5001d-122">Identifies the new state to which data is to be changed.</span></span>  
  
 **\<sync>**  
 <span data-ttu-id="5001d-123">とブロックを格納し **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-123">Contains the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="5001d-124">**\<sync>** ブロックには、およびブロックのセットを複数含めることができ **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-124">A **\<sync>** block can contain more than one set of **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="5001d-125">ブロックとブロックのセットが複数ある場合は **\<before>** **\<after>** 、これらのブロック (空の場合でも) をペアとして指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5001d-125">If there is more than one set of **\<before>** and **\<after>** blocks, these blocks (even if they are empty) must be specified as pairs.</span></span> <span data-ttu-id="5001d-126">さらに、アップデートグラムには複数のブロックを含めることができ **\<sync>** ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-126">Furthermore, an updategram can have more than one **\<sync>** block.</span></span> <span data-ttu-id="5001d-127">各 **\<sync>** ブロックは1つのトランザクション単位です (つまり、ブロック内のすべての処理が完了しているか、何も実行されていないことを意味 **\<sync>** します)。</span><span class="sxs-lookup"><span data-stu-id="5001d-127">Each **\<sync>** block is one unit of transaction (which means that either everything in the **\<sync>** block is done or nothing is done).</span></span> <span data-ttu-id="5001d-128">アップデートグラムに複数のブロックを指定した場合 **\<sync>** 、1つのブロックでエラーが発生しても、他のブロックには **\<sync>** 影響しません **\<sync>** 。</span><span class="sxs-lookup"><span data-stu-id="5001d-128">If you specify multiple **\<sync>** blocks in an updategram, the failure of one **\<sync>** block does not affect the other **\<sync>** blocks.</span></span>  
  
 <span data-ttu-id="5001d-129">アップデートグラムでレコードインスタンスを削除、挿入、または更新するかどうかは、ブロックとブロックの内容によって異なり **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-129">Whether an updategram deletes, inserts, or updates a record instance depends on the contents of the **\<before>** and **\<after>** blocks:</span></span>  
  
-   <span data-ttu-id="5001d-130">レコードインスタンスがブロック内にのみ存在し、 **\<before>** 対応するインスタンスがブロック内に存在しない場合 **\<after>** 、アップデートグラムは削除操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5001d-130">If a record instance appears only in the **\<before>** block with no corresponding instance in the **\<after>** block, the updategram performs a delete operation.</span></span>  
  
-   <span data-ttu-id="5001d-131">レコードインスタンスがブロック内にのみ存在し、 **\<after>** 対応するインスタンスがブロック内に存在しない場合 **\<before>** は、挿入操作になります。</span><span class="sxs-lookup"><span data-stu-id="5001d-131">If a record instance appears only in the **\<after>** block with no corresponding instance in the **\<before>** block, it is an insert operation.</span></span>  
  
-   <span data-ttu-id="5001d-132">レコードインスタンスがブロック内に存在 **\<before>** し、対応するインスタンスがブロック内にある場合 **\<after>** は、更新操作です。</span><span class="sxs-lookup"><span data-stu-id="5001d-132">If a record instance appears in the **\<before>** block and has a corresponding instance in the **\<after>** block, it is an update operation.</span></span> <span data-ttu-id="5001d-133">この場合、アップデートグラムでは、レコードインスタンスがブロックに指定されている値に更新され **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-133">In this case, the updategram updates the record instance to the values that are specified in the **\<after>** block.</span></span>  
  
## <a name="specifying-a-mapping-schema-in-the-updategram"></a><span data-ttu-id="5001d-134">アップデートグラムでマッピングスキーマを指定する</span><span class="sxs-lookup"><span data-stu-id="5001d-134">Specifying a Mapping Schema in the Updategram</span></span>  
 <span data-ttu-id="5001d-135">アップデートグラムでは、暗黙的または明示的に、マッピング スキーマによって XML データを操作できます。つまり、マッピング スキーマを指定しても指定しなくてもアップデートグラムは動作します。マッピング スキーマは XSD と XDR の両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5001d-135">In an updategram, the XML abstraction that is provided by a mapping schema (both XSD and XDR schemas are supported) can be implicit or explicit (that is, an updategram can work with or without a specified mapping schema).</span></span> <span data-ttu-id="5001d-136">マッピングスキーマを指定しない場合、アップデートグラムでは、暗黙的なマッピング (既定のマッピング) が使用されます。このマッピングでは、ブロックまたはブロック内の各要素が **\<before>** **\<after>** テーブルにマップされ、各要素の子要素または属性がデータベース内の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="5001d-136">If you do not specify a mapping schema, the updategram assumes an implicit mapping (the default mapping), where each element in the **\<before>** block or **\<after>** block maps to a table and each element's child element or attribute maps to a column in the database.</span></span> <span data-ttu-id="5001d-137">マッピング スキーマを明示的に指定する場合、アップデートグラムの要素と属性は、マッピング スキーマ内の要素と属性に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5001d-137">If you explicitly specify a mapping schema, the elements and attributes in the updategram must match the elements and attributes in the mapping schema.</span></span>  
  
### <a name="implicit-default-mapping"></a><span data-ttu-id="5001d-138">暗黙的なマッピング (既定)</span><span class="sxs-lookup"><span data-stu-id="5001d-138">Implicit (default) Mapping</span></span>  
 <span data-ttu-id="5001d-139">単純な更新を実行するアップデートグラムではほとんどの場合、マッピング スキーマは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5001d-139">In most cases, an updategram that performs simple updates might not require a mapping schema.</span></span> <span data-ttu-id="5001d-140">この場合、アップデートグラムは既定のマッピング スキーマに従います。</span><span class="sxs-lookup"><span data-stu-id="5001d-140">In this case, the updategram relies on the default mapping schema.</span></span>  
  
 <span data-ttu-id="5001d-141">次のアップデート グラムは、暗黙的なマッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="5001d-141">The following updategram demonstrates implicit mapping.</span></span> <span data-ttu-id="5001d-142">この例では、アップデートグラムによって新しい顧客が Sales.Customer テーブルに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="5001d-142">In this example, the updategram inserts a new customer in the Sales.Customer table.</span></span> <span data-ttu-id="5001d-143">このアップデートグラムでは暗黙的なマッピングが使用されるため、 \<Sales.Customer> 要素は sales. customer テーブルにマップされ、CustomerID 属性と SalesPersonID 属性が sales. customer テーブル内の対応する列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="5001d-143">Because this updategram uses implicit mapping, the \<Sales.Customer> element maps to the Sales.Customer table, and the CustomerID and SalesPersonID attributes map to the corresponding columns in the Sales.Customer table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
</updg:before>  
<updg:after>  
    <Sales.Customer CustomerID="1" SalesPersonID="277" />  
    </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="explicit-mapping"></a><span data-ttu-id="5001d-144">明示的なマッピング</span><span class="sxs-lookup"><span data-stu-id="5001d-144">Explicit Mapping</span></span>  
 <span data-ttu-id="5001d-145">XSD または XDR のいずれかのマッピング スキーマを指定した場合、アップデートグラムではそのスキーマによって、更新するデータベース テーブルと列が決定されます。</span><span class="sxs-lookup"><span data-stu-id="5001d-145">If you specify a mapping schema (either XSD or XDR), the updategram uses the schema to determine the database tables and columns that are to be updated.</span></span>  
  
 <span data-ttu-id="5001d-146">アップデートグラムにおいて、マッピング スキーマで指定される親子リレーションシップに基づいて複数のテーブルにレコードを挿入するなど、複雑な更新を実行する場合は、`mapping-schema` 属性でマッピング スキーマを明示的に指定する必要があります。アップデートグラムはこの属性で指定されたマッピング スキーマに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="5001d-146">If the updategram performs a complex update (for example, inserting records in multiple tables on the basis of the parent-child relationship that is specified in the mapping schema), you must explicitly provide the mapping schema by using the `mapping-schema` attribute against which the updategram executes.</span></span>  
  
 <span data-ttu-id="5001d-147">アップデートグラムはテンプレートであり、アップデートグラム内でマッピング スキーマに指定するパスは、テンプレート ファイルの場所 (アップデートグラムが保存されている場所) に対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="5001d-147">Because an updategram is a template, the path specified for the mapping schema in the updategram is relative to the location of the template file (relative to where the updategram is stored).</span></span> <span data-ttu-id="5001d-148">詳細については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5001d-148">For more information, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="element-centric-and-attribute-centric-mapping-in-updategrams"></a><span data-ttu-id="5001d-149">アップデートグラムでの要素中心および属性中心のマッピング</span><span class="sxs-lookup"><span data-stu-id="5001d-149">Element-centric and Attribute-centric Mapping in Updategrams</span></span>  
 <span data-ttu-id="5001d-150">アップデートグラムでマッピング スキーマが指定されていないときに使用される既定のマッピングでは、アップデートグラムの要素がテーブルにマップされ、要素中心マッピングの場合は子要素、属性中心マッピングの場合は属性が、それぞれ列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="5001d-150">With default mapping (when the mapping schema is not specified in the updategram), the updategram elements map to tables and the  child elements (in the case of element-centric mapping) and the attributes (in the case of attribute-centric mapping) map to columns.</span></span>  
  
### <a name="element-centric-mapping"></a><span data-ttu-id="5001d-151">要素中心のマッピング</span><span class="sxs-lookup"><span data-stu-id="5001d-151">Element-centric Mapping</span></span>  
 <span data-ttu-id="5001d-152">要素中心のアップデートグラムでは、要素に、要素のプロパティを表す子要素を含めます。</span><span class="sxs-lookup"><span data-stu-id="5001d-152">In an element-centric updategram, an element contains child elements that denote the properties of the element.</span></span> <span data-ttu-id="5001d-153">たとえば、次のアップデートグラムを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5001d-153">As an example, refer to the following updategram.</span></span> <span data-ttu-id="5001d-154">**\<Person.Contact>** 要素には、 **\<FirstName>** **\<LastName>** 子要素と子要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5001d-154">The **\<Person.Contact>** element contains the **\<FirstName>** and **\<LastName>** child elements.</span></span> <span data-ttu-id="5001d-155">これらの子要素は、要素のプロパティです **\<Person.Contact>** 。</span><span class="sxs-lookup"><span data-stu-id="5001d-155">These child elements are properties of the **\<Person.Contact>** element.</span></span>  
  
 <span data-ttu-id="5001d-156">このアップデートグラムではマッピングスキーマが指定されていないため、このアップデートグラムでは暗黙的なマッピングを使用します。この場合、 **\<Person.Contact>** 要素は Person テーブルとその子要素にマップされ、FirstName 列と LastName 列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="5001d-156">Because this updategram does not specify a mapping schema, the updategram uses implicit mapping, where the **\<Person.Contact>** element maps to the Person.Contact table and its child elements map to the FirstName and LastName columns.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:after>  
    <Person.Contact>  
       <FirstName>Catherine</FirstName>  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="attribute-centric-mapping"></a><span data-ttu-id="5001d-157">属性中心のマッピング</span><span class="sxs-lookup"><span data-stu-id="5001d-157">Attribute-centric Mapping</span></span>  
 <span data-ttu-id="5001d-158">属性中心のマッピングでは、要素に属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="5001d-158">In an attribute-centric mapping, the elements have attributes.</span></span> <span data-ttu-id="5001d-159">たとえば、次のアップデートグラムでは属性中心のマッピングが使用されています。</span><span class="sxs-lookup"><span data-stu-id="5001d-159">The following updategram uses attribute-centric mapping.</span></span> <span data-ttu-id="5001d-160">この例では、 **\<Person.Contact>** 要素は**FirstName**属性と**LastName**属性で構成されています。</span><span class="sxs-lookup"><span data-stu-id="5001d-160">In this example, the **\<Person.Contact>** element consists of the **FirstName** and **LastName** attributes.</span></span> <span data-ttu-id="5001d-161">これらの属性は、要素のプロパティ **\<Person.Contact>** です。</span><span class="sxs-lookup"><span data-stu-id="5001d-161">These attributes are the properties of the **\<Person.Contact>** element.</span></span> <span data-ttu-id="5001d-162">前の例と同様に、このアップデートグラムではマッピングスキーマが指定されていないため、 **\<Person.Contact>** 要素を Person. Contact テーブルにマップし、要素の属性をテーブル内のそれぞれの列にマップするために、暗黙的なマッピングに依存しています。</span><span class="sxs-lookup"><span data-stu-id="5001d-162">As in the previous example, this updategram specifies no mapping schema, so it relies on implicit mapping to map the **\<Person.Contact>** element to the Person.Contact table and the element's attributes to the respective columns in the table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" LastName="Abel" />  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="using-both-element-centric-and-attribute-centric-mapping"></a><span data-ttu-id="5001d-163">要素中心と属性中心の両方のマッピングの使用</span><span class="sxs-lookup"><span data-stu-id="5001d-163">Using Both Element-centric and Attribute-centric Mapping</span></span>  
 <span data-ttu-id="5001d-164">次のアップデートグラムに示すように、要素中心と属性中心のマッピングは併用できます。</span><span class="sxs-lookup"><span data-stu-id="5001d-164">You can specify a mix of element-centric and attribute-centric mapping, as shown in the following updategram.</span></span> <span data-ttu-id="5001d-165">要素には **\<Person.Contact>** 属性と子要素の両方が含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5001d-165">Notice that the **\<Person.Contact>** element contains both an attribute and a child element.</span></span> <span data-ttu-id="5001d-166">また、このアップデートグラムは暗黙的なマッピングに従います。</span><span class="sxs-lookup"><span data-stu-id="5001d-166">Also, this updategram relies on implicit mapping.</span></span> <span data-ttu-id="5001d-167">このため、 **FirstName**属性と **\<LastName>** child 要素は、Person. Contact テーブルの対応する列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="5001d-167">Thus, the **FirstName** attribute and the **\<LastName>** child element map to corresponding columns in the Person.Contact table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" >  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="working-with-characters-valid-in-sql-server-but-not-valid-in-xml"></a><span data-ttu-id="5001d-168">SQL Server で有効であり、XML で有効でない文字の取り扱い</span><span class="sxs-lookup"><span data-stu-id="5001d-168">Working with Characters Valid in SQL Server but Not Valid in XML</span></span>  
 <span data-ttu-id="5001d-169">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、テーブル名に空白を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5001d-169">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], table names can include a space.</span></span> <span data-ttu-id="5001d-170">ただし、このようなテーブル名は XML では有効でありません。</span><span class="sxs-lookup"><span data-stu-id="5001d-170">However, this type of table name is not valid in XML.</span></span>  
  
 <span data-ttu-id="5001d-171">有効な識別子であるが有効な XML 識別子ではない文字をエンコードするには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] \_ \_ エンコード値として ' __xHHHH ' を使用します。ここで、HHHH は、最上位ビットから順に、文字の4桁の16進数の UCS 2 コードを表します。</span><span class="sxs-lookup"><span data-stu-id="5001d-171">To encode characters that are valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiers but are not valid XML identifiers, use '__xHHHH\_\_' as the encoding value, where HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span> <span data-ttu-id="5001d-172">このエンコード方式を使用すると、スペース文字は x0020 (スペース文字の4桁の16進コード) に置き換えられます。このため、のテーブル名 [Order Details] は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML で _x005B_Order_x0020_Details_x005D になり \_ ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-172">Using this encoding scheme, a space character gets replaced with x0020 (the four-digit hexadecimal code for a space character); thus, the table name [Order Details] in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] becomes _x005B_Order_x0020_Details_x005D\_ in XML.</span></span>  
  
 <span data-ttu-id="5001d-173">同様に、などの3つの要素で構成される要素名を指定する必要がある場合もあり \<[database].[owner].[table]> ます。</span><span class="sxs-lookup"><span data-stu-id="5001d-173">Similarly, you might need to specify three-part element names, such as \<[database].[owner].[table]>.</span></span> <span data-ttu-id="5001d-174">角かっこ文字 ([および]) は XML では無効であるため、これをとして指定する必要があります \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_> \_ 。 _x005B は左角かっこ ([) のエンコーディングで、_x005D \_ は右角かっこ (]) のエンコーディングです。</span><span class="sxs-lookup"><span data-stu-id="5001d-174">Because the bracket characters ([ and ]) are not valid in XML, you must specify this as \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_>, where _x005B\_ is the encoding for the left bracket ([) and _x005D\_ is the encoding for the right bracket (]).</span></span>  
  
## <a name="executing-updategrams"></a><span data-ttu-id="5001d-175">アップデートグラムの実行</span><span class="sxs-lookup"><span data-stu-id="5001d-175">Executing Updategrams</span></span>  
 <span data-ttu-id="5001d-176">アップデートグラムはテンプレートであり、テンプレートのすべての処理メカニズムが適用されます。</span><span class="sxs-lookup"><span data-stu-id="5001d-176">Because an updategram is a template, all the processing mechanisms of a template apply to the updategram.</span></span> <span data-ttu-id="5001d-177">SQLXML 4.0 では、アップデートグラムを次のいずれかの方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="5001d-177">For SQLXML 4.0, you can execute an updategram in either of the following ways:</span></span>  
  
-   <span data-ttu-id="5001d-178">ADO コマンドに含めて送信する。</span><span class="sxs-lookup"><span data-stu-id="5001d-178">By submitting it in an ADO command.</span></span>  
  
-   <span data-ttu-id="5001d-179">OLE DB コマンドとして送信する。</span><span class="sxs-lookup"><span data-stu-id="5001d-179">By submitting it as an OLE DB command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5001d-180">参照</span><span class="sxs-lookup"><span data-stu-id="5001d-180">See Also</span></span>  
 [<span data-ttu-id="5001d-181">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="5001d-181">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
