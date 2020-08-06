---
title: XML アップデートグラムを使用したデータの挿入 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- xsi:nil attribute
- unique values
- <after> block
- id attribute
- data insertions [SQLXML]
- nil attribute
- <before> block
- updg:guid attribute
- multiple record insertions
- returnid attribute
- updategrams [SQLXML], inserting data
- updg:at-identity attribute
- invalid characters [SQLXML]
- updg:returnid attribute
- updg:id attribute
- namespaces [SQLXML], updategrams
- IDENTITY-type column
- guid attribute
- record insertion [SQLXML]
- null values [SQLXML]
- at-identity attribute
- xml data type [SQL Server], SQLXML
ms.assetid: 4dc48762-bc12-43fb-b356-ea1b9c1e287e
author: rothja
ms.author: jroth
ms.openlocfilehash: a80f2cb157e59f30ebcbff5c14abba1003de9e40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716129"
---
# <a name="inserting-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="fd14c-102">XML アップデートグラムを使用した、データの挿入 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="fd14c-102">Inserting Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="fd14c-103">アップデートグラムは、レコードインスタンスがブロック内に存在する **\<after>** が、対応するブロックには存在しない場合に挿入操作を示し **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-103">An updategram indicates an insert operation when a record instance appears in the **\<after>** block but not in the corresponding **\<before>** block.</span></span> <span data-ttu-id="fd14c-104">この場合、アップデートグラムではブロック内のレコードがデータベースに挿入され **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-104">In this case, the updategram inserts the record in the **\<after>** block into the database.</span></span>  
  
 <span data-ttu-id="fd14c-105">挿入操作のアップデートグラムの形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fd14c-105">This is the updategram format for an insert operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   [<updg:before>  
   </updg:before>]  
    <updg:after [updg:returnid="x y ...] >  
       <ElementName [updg:id="value"]   
                   [updg:at-identity="x"]   
                   [updg:guid="y"]  
                   attribute="value"   
                   attribute="value"  
                   ...  
       />  
      [<ElementName .../>... ]  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
## <a name="before-block"></a><span data-ttu-id="fd14c-106">\<before>帯</span><span class="sxs-lookup"><span data-stu-id="fd14c-106">\<before> Block</span></span>  
 <span data-ttu-id="fd14c-107">**\<before>** 挿入操作では、ブロックを省略できます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-107">The **\<before>** block can be omitted for an insert operation.</span></span> <span data-ttu-id="fd14c-108">省略可能な `mapping-schema` 属性が指定されていない場合、 **\<ElementName>** アップデートグラムで指定したはデータベーステーブルにマップされ、子要素または属性はテーブル内の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-108">If the optional `mapping-schema` attribute is not specified, the **\<ElementName>** that is specified in the updategram maps to a database table and the child elements or attributes map to columns in the table.</span></span>  
  
## <a name="after-block"></a><span data-ttu-id="fd14c-109">\<after>帯</span><span class="sxs-lookup"><span data-stu-id="fd14c-109">\<after> Block</span></span>  
 <span data-ttu-id="fd14c-110">ブロック内の1つ以上のレコードを指定でき **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-110">You can specify one or more records in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="fd14c-111">ブロックで **\<after>** 特定の列の値が指定されていない場合、アップデートグラムでは、注釈付きスキーマに指定されている既定値 (スキーマが指定されている場合) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-111">If the **\<after>** block does not supply a value for a particular column, the updategram uses the default value that is specified in the annotated schema (if a schema has been specified).</span></span> <span data-ttu-id="fd14c-112">スキーマで列の既定値が指定されていない場合、アップデートグラムではこの列に明示的な値が指定されず、代わりに、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] この列に既定値 (指定されている場合) が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-112">If the schema does not specify a default value for the column, the updategram does not specify any explicit value to this column and, instead, assigns the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default value (if specified) to this column.</span></span> <span data-ttu-id="fd14c-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定値がなく、列で NULL 値が許容される場合、アップデートグラムでは列値に NULL が設定されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-113">If there is no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default value and the column accepts a NULL value, the updategram sets the column value to NULL.</span></span> <span data-ttu-id="fd14c-114">列に既定値がなく NULL 値が許容されない場合、コマンドは失敗し、アップデートグラムではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-114">If the column neither has a default value nor accepts a NULL value, the command fails and the updategram returns an error.</span></span> <span data-ttu-id="fd14c-115">`updg:returnid` 属性は省略可能です。この属性は、IDENTITY 型の列があるテーブルにレコードを追加するときに、システムによって生成される ID 値を返す場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-115">The optional `updg:returnid` attribute is used to return the identity value that is generated by the system when a record is added in a table with an IDENTITY-type column.</span></span>  
  
## <a name="updgid-attribute"></a><span data-ttu-id="fd14c-116">updg:id 属性</span><span class="sxs-lookup"><span data-stu-id="fd14c-116">updg:id Attribute</span></span>  
 <span data-ttu-id="fd14c-117">アップデートグラムでレコードのみを挿入する場合、アップデートグラムに `updg:id` 属性を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-117">If the updategram is inserting only records, the updategram does not require the `updg:id` attribute.</span></span> <span data-ttu-id="fd14c-118">の詳細について `updg:id` は、「 [XML アップデートグラムを使用したデータの更新 &#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-118">For more information about `updg:id`, see [Updating Data Using XML Updategrams &#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
## <a name="updgat-identity-attribute"></a><span data-ttu-id="fd14c-119">updg:at-identity 属性</span><span class="sxs-lookup"><span data-stu-id="fd14c-119">updg:at-identity Attribute</span></span>  
 <span data-ttu-id="fd14c-120">アップデートグラムで、IDENTITY 型列があるテーブルにレコードを挿入するときには、省略可能な `updg:at-identity` 属性を使用して、システムにより割り当てられた値をキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-120">When an updategram inserts a record in a table that has an IDENTITY-type column, the updategram can capture the system assigned value by using the optional `updg:at-identity` attribute.</span></span> <span data-ttu-id="fd14c-121">キャプチャした値は、後続のアップデートグラム操作で使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-121">The updategram can then use this value in subsequent operations.</span></span> <span data-ttu-id="fd14c-122">`updg:returnid` 属性を指定してアップデートグラムを実行すると、生成される ID 値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-122">Upon execution of the updategram, you can return the identity value that is generated by specifying the `updg:returnid` attribute.</span></span>  
  
## <a name="updgguid-attribute"></a><span data-ttu-id="fd14c-123">updg:guid 属性</span><span class="sxs-lookup"><span data-stu-id="fd14c-123">updg:guid Attribute</span></span>  
 <span data-ttu-id="fd14c-124">`updg:guid` 属性は省略可能です。この属性では、グローバル一意識別子が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-124">The `updg:guid` attribute is an optional attribute that generates a globally unique identifier.</span></span> <span data-ttu-id="fd14c-125">この値は、指定されているブロック全体のスコープ内に残り **\<sync>** ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-125">This value remains in scope for the entire **\<sync>** block in which it is specified.</span></span> <span data-ttu-id="fd14c-126">この値は、ブロック内の任意の場所で使用でき **\<sync>** ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-126">You can use this value anywhere in the **\<sync>** block.</span></span> <span data-ttu-id="fd14c-127">属性は、関数を呼び出して、 `NEWGUID()` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一意の識別子を生成します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-127">The attribute calls the `NEWGUID()`[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] function to generate the unique identifier.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fd14c-128">例</span><span class="sxs-lookup"><span data-stu-id="fd14c-128">Examples</span></span>  
 <span data-ttu-id="fd14c-129">次の例を使用して実際のサンプルを作成するには、 [SQLXML の例を実行するための要件](../../sqlxml/requirements-for-running-sqlxml-examples.md)を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-129">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
 <span data-ttu-id="fd14c-130">アップデートグラムの例を使用する前に、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-130">Before using the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="fd14c-131">ほとんどの例では、アップデートグラムでマッピング スキーマを指定せず、既定のマッピングを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-131">Most of the examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="fd14c-132">マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-132">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="fd14c-133">ほとんどの例では、[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-133">Most of the examples use the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="fd14c-134">すべての更新内容は、このデータベースのテーブルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-134">All the updates are applied to the tables in this database.</span></span>  
  
### <a name="a-inserting-a-record-by-using-an-updategram"></a><span data-ttu-id="fd14c-135">A.</span><span class="sxs-lookup"><span data-stu-id="fd14c-135">A.</span></span> <span data-ttu-id="fd14c-136">アップデートグラムを使用してレコードを挿入する</span><span class="sxs-lookup"><span data-stu-id="fd14c-136">Inserting a record by using an updategram</span></span>  
 <span data-ttu-id="fd14c-137">この属性中心のアップデートグラムでは、[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] データベース内の HumanResources.Employee テーブルにレコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-137">This attribute-centric updategram inserts a record in the HumanResources.Employee table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="fd14c-138">この例では、アップデートグラムでマッピングスキーマが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-138">In this example, the updategram does not specify a mapping schema.</span></span> <span data-ttu-id="fd14c-139">したがって、アップデートグラムでは既定のマッピングが使用されます。このマッピングでは、要素名はテーブル名にマップされ、属性または子要素はそのテーブル内の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-139">Therefore, the updategram uses default mapping, in which the element name maps to a table name and the attributes or child elements map to columns in that table.</span></span>  
  
 <span data-ttu-id="fd14c-140">HumanResources.Department テーブルに対する [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] スキーマでは、すべての列に 'not null' 制限が設定されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-140">The [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] schema for the HumanResources.Department table imposes a 'not null' restriction on all columns.</span></span> <span data-ttu-id="fd14c-141">したがって、アップデートグラムには、すべての列に指定する値を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-141">Therefore, the updategram must include values specified for all columns.</span></span> <span data-ttu-id="fd14c-142">DepartmentID は IDENTITY 型の列であり、</span><span class="sxs-lookup"><span data-stu-id="fd14c-142">The DepartmentID is an IDENTITY-type column.</span></span> <span data-ttu-id="fd14c-143">値は指定しません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-143">Therefore, no values are specified for it.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name="New Product Research"   
            GroupName="Research and Development"   
            ModifiedDate="2010-08-31"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="fd14c-144">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-144">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="fd14c-145">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-145">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-146">MyUpdategram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-146">Save the file as MyUpdategram.xml.</span></span>  
  
2.  <span data-ttu-id="fd14c-147">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-147">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fd14c-148">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-148">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="fd14c-149">要素中心のマッピングの場合、アップデートグラムは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-149">In an element-centric mapping, the updategram looks like this:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department>  
            <Name> New Product Research </Name>  
            <GroupName> Research and Development </GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-150">要素中心と属性中心の混合モードのアップデートグラムでは、次のアップデートグラムのように、要素に属性と副要素の両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-150">In a mixed-mode (element-centric and attribute-centric) updategram, an element can have both attributes and subelements, as shown in this updategram:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name=" New Product Research "   
            <GroupName>Research and Development</GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="b-inserting-multiple-records-by-using-an-updategram"></a><span data-ttu-id="fd14c-151">B.</span><span class="sxs-lookup"><span data-stu-id="fd14c-151">B.</span></span> <span data-ttu-id="fd14c-152">アップデートグラムを使用して複数のレコードを挿入する</span><span class="sxs-lookup"><span data-stu-id="fd14c-152">Inserting multiple records by using an updategram</span></span>  
 <span data-ttu-id="fd14c-153">このアップデートグラムでは、HumanResources.Shift テーブルに 2 つの新しい勤務時間レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-153">This updategram adds two new shift records to the HumanResources.Shift table.</span></span> <span data-ttu-id="fd14c-154">アップデートグラムでは、省略可能なブロックが指定されていません **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="fd14c-154">The updategram does not specify the optional **\<before>** block.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="fd14c-155">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-155">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="fd14c-156">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-156">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-157">Updategram-AddShifts.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-157">Save the file as Updategram-AddShifts.xml.</span></span>  
  
2.  <span data-ttu-id="fd14c-158">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-158">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fd14c-159">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-159">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="fd14c-160">この例の別のバージョンは、 **\<after>** 2 つの従業員を挿入するために1つのブロックではなく、2つの個別のブロックを使用するアップデートグラムです。</span><span class="sxs-lookup"><span data-stu-id="fd14c-160">Another version of this example is an updategram that uses two separate **\<after>** blocks instead of one block to insert the two employees.</span></span> <span data-ttu-id="fd14c-161">これは有効であり、次のようにエンコードできます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-161">This is valid and can be encoded as follows:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after >  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="c-working-with-valid-sql-server-characters-that-are-not-valid-in-xml"></a><span data-ttu-id="fd14c-162">C.</span><span class="sxs-lookup"><span data-stu-id="fd14c-162">C.</span></span> <span data-ttu-id="fd14c-163">SQL Server で有効で、XML では有効でない文字を処理する</span><span class="sxs-lookup"><span data-stu-id="fd14c-163">Working with valid SQL Server characters that are not valid in XML</span></span>  
 <span data-ttu-id="fd14c-164">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、テーブル名は、Northwind データベースの Order Details テーブルのようにスペースを含めて指定できます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-164">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], table names can include a space, such as the Order Details table in the Northwind database.</span></span> <span data-ttu-id="fd14c-165">ただし、有効な識別子である XML 文字では有効ではありませんが、有効な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] xml 識別子はエンコード値として ' __xHHHH ' を使用してエンコードできます \_ \_ 。ここで、HHHH は、最上位ビットから順に、文字の4桁の16進数の UCS 2 コードを表します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-165">However, this is not valid in XML characters that are valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiers but not valid XML identifiers can be encoded using '__xHHHH\_\_' as the encoding value, where HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd14c-166">この例では Northwind データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-166">This example uses the Northwind database.</span></span> <span data-ttu-id="fd14c-167">この[Microsoft Web サイト](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)からダウンロードできる SQL スクリプトを使用して、Northwind データベースをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-167">You can install the Northwind database by using an SQL script available for download from this [Microsoft Web site](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>  
  
 <span data-ttu-id="fd14c-168">要素名も、角かっこ ([ ]) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-168">Also, the element name must be enclosed within brackets ([ ]).</span></span> <span data-ttu-id="fd14c-169">文字 [および] は XML では有効でないため、それぞれを _x005B としてエンコードし、_x005D する必要があり \_ \_ ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-169">Because the characters [and] are not valid in XML, you must encode them as _x005B\_ and _x005D\_, respectively.</span></span> <span data-ttu-id="fd14c-170">マッピング スキーマを使用して、空白文字など有効でない文字を含まない要素名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-170">(If you use a mapping schema, you can provide element names that do not contain characters that are not valid, such as white spaces.</span></span> <span data-ttu-id="fd14c-171">この場合、マッピング スキーマで必要なマッピングが行われるので、これらの文字をエンコードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-171">The mapping schema does the necessary mapping; therefore, you do not need to encode for these characters).</span></span>  
  
 <span data-ttu-id="fd14c-172">次のアップデートグラムでは、Northwind データベースの Order Details テーブルにレコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-172">This updategram adds a record to the Order Details table in the Northwind database:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <_x005B_Order_x0020_Details_x005D_ OrderID="1"  
            ProductID="11"  
            UnitPrice="$1.0"  
            Quantity="1"  
            Discount="0.0" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-173">Order Details テーブル内の UnitPrice 列は `money` 型です。</span><span class="sxs-lookup"><span data-stu-id="fd14c-173">The UnitPrice column in the Order Details table is of the `money` type.</span></span> <span data-ttu-id="fd14c-174">`string` 型から `money` 型へ、適切な型変換を行うには、ドル記号 ($) を値の一部に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-174">To apply the appropriate type conversion (from a `string` type to a `money` type), the dollar sign character ($) must be added as part of the value.</span></span> <span data-ttu-id="fd14c-175">アップデートグラムでマッピング スキーマが指定されていない場合は、`string` 値の最初の文字が評価されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-175">If the updategram does not specify a mapping schema, the first character of the `string` value is evaluated.</span></span> <span data-ttu-id="fd14c-176">最初の文字がドル記号 ($) の場合、適切な変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-176">If the first character is a dollar sign ($), the appropriate conversion is applied.</span></span>  
  
 <span data-ttu-id="fd14c-177">アップデートグラムで指定したマッピング スキーマで、列が `dt:type="fixed.14.4"` または `sql:datatype="money"` として適切にマークされている場合は、ドル記号 ($) は必要なく、マッピングによって変換が処理されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-177">If the updategram is specified against a mapping schema where the column is appropriately marked as either `dt:type="fixed.14.4"` or `sql:datatype="money"`, the dollar sign ($) is not required and the conversion is handled by the mapping.</span></span> <span data-ttu-id="fd14c-178">適切な型変換が行われるようにするには、この方法が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-178">This is the recommended way to ensure that the appropriate type conversion occurs.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="fd14c-179">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-179">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="fd14c-180">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-180">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-181">UpdategramSpacesInTableName.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-181">Save the file as UpdategramSpacesInTableName.xml.</span></span>  
  
2.  <span data-ttu-id="fd14c-182">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-182">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fd14c-183">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-183">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="d-using-the-at-identity-attribute-to-retrieve-the-value-that-has-been-inserted-in-the-identity-type-column"></a><span data-ttu-id="fd14c-184">D.</span><span class="sxs-lookup"><span data-stu-id="fd14c-184">D.</span></span> <span data-ttu-id="fd14c-185">at-identity 属性を使用して、IDENTITY 型の列に挿入されている値を取得する</span><span class="sxs-lookup"><span data-stu-id="fd14c-185">Using the at-identity attribute to retrieve the value that has been inserted in the IDENTITY-type column</span></span>  
 <span data-ttu-id="fd14c-186">次のアップデートグラムでは、Sales.SalesOrderHeader テーブルと Sales.SalesOrderDetail テーブルに 1 つずつ、合計 2 つのレコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-186">The following updategram inserts two records: one in the Sales.SalesOrderHeader table and another in the Sales.SalesOrderDetail table.</span></span>  
  
 <span data-ttu-id="fd14c-187">このアップデートグラムでは、最初にレコードを Sales.SalesOrderHeader テーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-187">First, the updategram adds a record to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="fd14c-188">このテーブルで、SalesOrderID 列は IDENTITY 型の列です。</span><span class="sxs-lookup"><span data-stu-id="fd14c-188">In this table, the SalesOrderID column is an IDENTITY-type column.</span></span> <span data-ttu-id="fd14c-189">したがって、このレコードをテーブルに追加するとき、アップデートグラムでは割り当てられている SalesOrderID 値を `at-identity` 属性に "x" (プレースホルダー値) としてキャプチャし、</span><span class="sxs-lookup"><span data-stu-id="fd14c-189">Therefore, when you add this record to the table, the updategram uses the `at-identity` attribute to capture the assigned SalesOrderID value as "x" (a placeholder value).</span></span> <span data-ttu-id="fd14c-190">次に、この `at-identity` 変数を要素の SalesOrderID 属性の値として指定し \<Sales.SalesOrderDetail> ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-190">The updategam then specifies this `at-identity` variable as the value of SalesOrderID attribute in the \<Sales.SalesOrderDetail> element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
   <Sales.SalesOrderHeader updg:at-identity="x"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00001111-2222-3333-4444-556677889900"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
      <Sales.SalesOrderDetail SalesOrderID="x"  
                LineNumber="1"  
                OrderQty="1"  
                ProductID="776"  
                SpecialOfferID="1"  
                UnitPrice="2429.9928"  
                UnitPriceDiscount="0.00"  
                rowguid="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"  
                ModifiedDate="2001-07-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-191">`updg:at-identity` 属性により生成される ID 値を返す場合は、`updg:returnid` 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-191">If you want to return the identity value that is generated by the `updg:at-identity` attribute, you can use the `updg:returnid` attribute.</span></span> <span data-ttu-id="fd14c-192">次のアップデートグラムは、この ID 値を返すように変更されたものです。</span><span class="sxs-lookup"><span data-stu-id="fd14c-192">The following is a revised updategram that returns this identity value.</span></span> <span data-ttu-id="fd14c-193">例を少し複雑にするため、ここでは 2 つの注文レコードと 2 つの注文詳細レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-193">(This updategram adds two order records and two order detail records, just to make the example a little more complex.)</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync>  
  <updg:before>  
  </updg:before>  
  <updg:after updg:returnid="x y" >  
       <HumanResources.Shift updg:at-identity="x" Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift updg:at-identity="y" Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:after>  
 </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-194">アップデートグラムを実行すると、次のような結果が返されます。この結果には、生成された ID 値 (テーブル ID に使用される ShiftID 列の生成値) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-194">When the updategram is executed, it returns results similar to the following, which includes the identity value (the generated value of the ShiftID column used for table identity) that was generated:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">   
  <returnid>   
    <x>4</x>   
    <y>5</y>   
  </returnid>   
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="fd14c-195">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-195">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="fd14c-196">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-196">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-197">Updategram-returnId.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-197">Save the file as Updategram-returnId.xml.</span></span>  
  
2.  <span data-ttu-id="fd14c-198">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-198">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fd14c-199">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-199">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="e-using-the-updgguid-attribute-to-generate-a-unique-value"></a><span data-ttu-id="fd14c-200">E.</span><span class="sxs-lookup"><span data-stu-id="fd14c-200">E.</span></span> <span data-ttu-id="fd14c-201">updg:guid 属性を使用して一意な値を生成する</span><span class="sxs-lookup"><span data-stu-id="fd14c-201">Using the updg:guid attribute to generate a unique value</span></span>  
 <span data-ttu-id="fd14c-202">この例のアップデートグラムでは、Cust および CustOrder テーブルにレコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-202">In this example, the updategram inserts a record in the Cust and CustOrder tables.</span></span> <span data-ttu-id="fd14c-203">また、`updg:guid` 属性を使用して、CustomerID 属性に一意な値を生成します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-203">Also, the updategram generates a unique value for the CustomerID attribute by using the `updg:guid` attribute.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after updg:returnid="x" >  
      <Cust updg:guid="x" >  
         <CustID>x</CustID>  
         <LastName>Fuller</LastName>  
      </Cust>  
      <CustOrder>  
         <CustID>x</CustID>  
         <OrderID>1</OrderID>  
      </CustOrder>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-204">このアップデートグラムでは、`returnid` 属性を指定しています。</span><span class="sxs-lookup"><span data-stu-id="fd14c-204">The updategram specifies the `returnid` attribute.</span></span> <span data-ttu-id="fd14c-205">結果として、生成された GUID が返されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-205">As a result, the GUID that is generated is returned:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <returnid>  
    <x>7111BD1A-7F0B-4CEE-B411-260DADFEFA2A</x>   
  </returnid>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="fd14c-206">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-206">To test the updategram</span></span>  
  
1.  <span data-ttu-id="fd14c-207">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-207">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-208">Updategram-GenerateGuid.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-208">Save the file as Updategram-GenerateGuid.xml.</span></span>  
  
2.  <span data-ttu-id="fd14c-209">次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-209">Create these tables:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust (CustID uniqueidentifier, LastName varchar(20))  
    CREATE TABLE CustOrder (CustID uniqueidentifier, OrderID int)  
    ```  
  
3.  <span data-ttu-id="fd14c-210">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-210">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fd14c-211">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-211">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="f-specifying-a-schema-in-an-updategram"></a><span data-ttu-id="fd14c-212">F.</span><span class="sxs-lookup"><span data-stu-id="fd14c-212">F.</span></span> <span data-ttu-id="fd14c-213">アップデートグラムでスキーマを指定する</span><span class="sxs-lookup"><span data-stu-id="fd14c-213">Specifying a schema in an updategram</span></span>  
 <span data-ttu-id="fd14c-214">この例のアップデートグラムでは、レコードを次のテーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-214">The updategram in this example inserts a record into the following table:</span></span>  
  
```  
CustOrder(OrderID, EmployeeID, OrderType)  
```  
  
 <span data-ttu-id="fd14c-215">このアップデートグラムでは XSD スキーマを指定しています。アップデートグラム要素と属性に既定のマッピングはありません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-215">An XSD schema is specified in this updategram (that is, there is no default mapping of updategram elements and attributes).</span></span> <span data-ttu-id="fd14c-216">このスキーマでは、要素および属性からデータベース テーブルおよび列への必要なマッピングが提供されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-216">The schema provides the necessary mapping of the elements and attributes to the database tables and columns.</span></span>  
  
 <span data-ttu-id="fd14c-217">次のスキーマ (CustOrderSchema.xml) では、 **\<CustOrder>** **OrderID**属性と**EmployeeID**属性で構成される要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-217">The following schema (CustOrderSchema.xml) describes a **\<CustOrder>** element that consists of the **OrderID** and **EmployeeID** attributes.</span></span> <span data-ttu-id="fd14c-218">スキーマをさらに興味深いものにするため、 **EmployeeID**属性には既定値が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="fd14c-218">To make the schema more interesting, a default value is assigned to the **EmployeeID** attribute.</span></span> <span data-ttu-id="fd14c-219">アップデートグラムでは、属性の既定値は、アップデートグラムでその属性が指定されていない挿入操作のみに使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-219">An updategram uses an attribute's default value only for insert operations, and then only if the updategram does not specify that attribute.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="CustOrder" >  
   <xsd:complexType>  
        <xsd:attribute name="OrderID"     type="xsd:integer" />   
        <xsd:attribute name="EmployeeID"  type="xsd:integer" />  
        <xsd:attribute name="OrderType  " type="xsd:integer" default="1"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="fd14c-220">このアップデートグラムでは、CustOrder テーブルにレコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-220">This updategram inserts a record into the CustOrder table.</span></span> <span data-ttu-id="fd14c-221">このアップデートグラムでは OrderID および EmployeeID 属性の値のみを指定し、</span><span class="sxs-lookup"><span data-stu-id="fd14c-221">The updategram specifies only the OrderID and EmployeeID attribute values.</span></span> <span data-ttu-id="fd14c-222">OrderType 属性の値は指定しません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-222">It does not specify the OrderType attribute value.</span></span> <span data-ttu-id="fd14c-223">したがって、アップデートグラムでは、前のスキーマで指定されている EmployeeID 属性の既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-223">Therefore, the updategram uses the default value of the EmployeeID attribute that is specified in the preceding schema.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
             xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync mapping-schema='CustOrderSchema.xml'>  
<updg:after>  
       <CustOrder OrderID="98000" EmployeeID="1" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-224">マッピングスキーマを指定するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-224">For more examples of updategrams that specify a mapping schema, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="fd14c-225">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-225">To test the updategram</span></span>  
  
1.  <span data-ttu-id="fd14c-226">**Tempdb**データベースに次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-226">Create this table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE CustOrder(  
                     OrderID int,   
                     EmployeeID int,   
                     OrderType int)  
    ```  
  
2.  <span data-ttu-id="fd14c-227">上のスキーマをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-227">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-228">CustOrderSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-228">Save the file as CustOrderSchema.xml.</span></span>  
  
3.  <span data-ttu-id="fd14c-229">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-229">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-230">上の手順と同じフォルダーに CustOrderUpdategram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-230">Save the file as CustOrderUpdategram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="fd14c-231">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-231">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="fd14c-232">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-232">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="fd14c-233">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="fd14c-233">This is the equivalent XDR schema:</span></span>  
  
```  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
 <ElementType name="CustOrder" >  
    <AttributeType name="OrderID" />  
    <AttributeType name="EmployeeID" />  
    <AttributeType name="OrderType" default="1" />  
    <attribute type="OrderID"  />  
    <attribute type="EmployeeID" />  
    <attribute type="OrderType" />  
  </ElementType>  
</Schema>  
```  
  
### <a name="g-using-the-xsinil-attribute-to-insert-null-values-in-a-column"></a><span data-ttu-id="fd14c-234">G.</span><span class="sxs-lookup"><span data-stu-id="fd14c-234">G.</span></span> <span data-ttu-id="fd14c-235">xsi:nil 属性を使用して列に null 値を挿入する</span><span class="sxs-lookup"><span data-stu-id="fd14c-235">Using the xsi:nil attribute to insert null values in a column</span></span>  
 <span data-ttu-id="fd14c-236">テーブル内の列に null 値を挿入する場合は、アップデートグラム内の対応する要素に `xsi:nil` 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-236">If you want to insert a null value in the corresponding column in the table, you can specify the `xsi:nil` attribute on an element in an updategram.</span></span> <span data-ttu-id="fd14c-237">また、対応する XSD スキーマで、XSD `nillable` 属性も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-237">In the corresponding XSD schema, the XSD `nillable` attribute also must be specified.</span></span>  
  
 <span data-ttu-id="fd14c-238">たとえば、次の XSD スキーマを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-238">For example, consider this XSD schema:</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="Student" sql:relation="Students">  
  <xsd:complexType>  
    <xsd:all>  
      <xsd:element name="fname" sql:field="first_name"   
                                type="xsd:string"   
                                 nillable="true"/>  
    </xsd:all>  
    <xsd:attribute name="SID"   
                        sql:field="StudentID"  
                        type="xsd:ID"/>      
    <xsd:attribute name="lname"       
                        sql:field="last_name"  
                        type="xsd:string"/>  
    <xsd:attribute name="minitial"    
                        sql:field="middle_initial"   
                        type="xsd:string"/>  
    <xsd:attribute name="years"       
                         sql:field="no_of_years"  
                         type="xsd:integer"/>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="fd14c-239">XSD スキーマでは、要素に**nillable = "true"** が指定されて **\<fname>** います。</span><span class="sxs-lookup"><span data-stu-id="fd14c-239">The XSD schema specifies **nillable="true"** for the **\<fname>** element.</span></span> <span data-ttu-id="fd14c-240">このスキーマを使用するアップデートグラムは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fd14c-240">The following updategram uses this schema:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
      xmlns:updg="urn:schemas-microsoft-com:xml-updategram"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
<updg:sync mapping-schema='StudentSchema.xml'>  
  <updg:before/>  
  <updg:after>  
    <Student SID="S00004" lname="Elmaci" minitial="" years="2">  
      <fname xsi:nil="true">  
    </fname>  
    </Student>  
  </updg:after>  
</updg:sync>  
  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-241">アップデートグラムでは、 `xsi:nil` ブロック内の要素にを指定し **\<fname>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-241">The updategram specifies `xsi:nil` for the **\<fname>** element in the **\<after>** block.</span></span> <span data-ttu-id="fd14c-242">したがって、このアップデートグラムを実行すると、テーブルの first_name 列に NULL 値が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-242">Therefore, when this updategram is executed, a value of NULL is inserted for the first_name column in the table.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="fd14c-243">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-243">To test the updategram</span></span>  
  
1.  <span data-ttu-id="fd14c-244">次のテーブルを**tempdb**データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-244">Create the following table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Students (  
       StudentID char(6)NOT NULL ,  
       first_name varchar(50),  
       last_name varchar(50),  
       middle_initial char(1),  
       no_of_years int NULL)  
    GO  
    ```  
  
2.  <span data-ttu-id="fd14c-245">上のスキーマをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-245">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-246">StudentSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-246">Save the file as StudentSchema.xml.</span></span>  
  
3.  <span data-ttu-id="fd14c-247">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-247">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-248">上の手順の StudentSchema.xml と同じフォルダーに StudentUpdategram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-248">Save the file as StudentUpdategram.xml in the same folder used in previous step to save StudentSchema.xml.</span></span>  
  
4.  <span data-ttu-id="fd14c-249">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-249">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="fd14c-250">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-250">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="h-specifying-namespaces-in-an-updategram"></a><span data-ttu-id="fd14c-251">H.</span><span class="sxs-lookup"><span data-stu-id="fd14c-251">H.</span></span> <span data-ttu-id="fd14c-252">アップデートグラムで名前空間を指定する</span><span class="sxs-lookup"><span data-stu-id="fd14c-252">Specifying namespaces in an updategram</span></span>  
 <span data-ttu-id="fd14c-253">アップデートグラム内の要素で名前空間を宣言し、その名前空間に属する要素として、同じ要素を保持することができます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-253">In an updategram you can have elements that belong to a namespace declared in the same element in the updategram.</span></span> <span data-ttu-id="fd14c-254">この場合、対応するスキーマで同じ名前空間を宣言する必要があり、対象の名前空間に要素が属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-254">In this case, the corresponding schema must also declare the same namespace and the element must belong to that target namespace.</span></span>  
  
 <span data-ttu-id="fd14c-255">たとえば、次のアップデートグラム (UpdateGram-ElementHavingNamespace.xml) では、要素は **\<Order>** 要素で宣言された名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-255">For example, in the following updategram (UpdateGram-ElementHavingNamespace.xml), the **\<Order>** element belongs to a namespace declared in the element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema='XSD-ElementHavingNameSpace.xml'>  
    <updg:after>  
       <x:Order  xmlns:x="http://server/xyz/schemas/"  
             updg:at-identity="SalesOrderID"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00009999-8888-7777-6666-554433221100"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-256">この場合、このスキーマに示すように、スキーマでも名前空間を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-256">In this case, the schema must also declare the namespace as shown in this schema:</span></span>  
  
 <span data-ttu-id="fd14c-257">次のスキーマ (XSD-ElementHavingNamespace.xml) では、対応する要素と属性の宣言方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fd14c-257">The following schema (XSD-ElementHavingNamespace.xml) shows how the corresponding element and attributes must be declared.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns:dt="urn:schemas-microsoft-com:datatypes"   
     xmlns:sql="urn:schemas-microsoft-com:mapping-schema"    
     xmlns:x="http://server/xyz/schemas/"   
     targetNamespace="http://server/xyz/schemas/" >  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="x:Order_type"/>  
  <xsd:complexType name="Order_type">  
    <xsd:attribute name="SalesOrderID"  type="xsd:ID"/>  
    <xsd:attribute name="RevisionNumber" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OrderDate" type="xsd:dateTime"/>  
    <xsd:attribute name="DueDate" type="xsd:dateTime"/>  
    <xsd:attribute name="ShipDate" type="xsd:dateTime"/>  
    <xsd:attribute name="Status" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OnlineOrderFlag" type="xsd:boolean"/>  
    <xsd:attribute name="SalesOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="PurchaseOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="AccountNumber" type="xsd:string"/>  
    <xsd:attribute name="CustomerID" type="xsd:int"/>  
    <xsd:attribute name="ContactID" type="xsd:int"/>  
    <xsd:attribute name="SalesPersonID" type="xsd:int"/>  
    <xsd:attribute name="TerritoryID" type="xsd:int"/>  
    <xsd:attribute name="BillToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipMethodID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardApprovalCode" type="xsd:string"/>  
    <xsd:attribute name="CurrencyRateID" type="xsd:int"/>  
    <xsd:attribute name="SubTotal" type="xsd:decimal"/>  
    <xsd:attribute name="TaxAmt" type="xsd:decimal"/>  
    <xsd:attribute name="Freight" type="xsd:decimal"/>  
    <xsd:attribute name="TotalDue" type="xsd:decimal"/>  
    <xsd:attribute name="Comment" type="xsd:string"/>  
    <xsd:attribute name="rowguid" type="xsd:string"/>  
    <xsd:attribute name="ModifiedDate" type="xsd:dateTime"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="fd14c-258">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-258">To test the updategram</span></span>  
  
1.  <span data-ttu-id="fd14c-259">上のスキーマをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-259">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-260">XSD-ElementHavingNamespace.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-260">Save the file as XSD-ElementHavingNamespace.xml.</span></span>  
  
2.  <span data-ttu-id="fd14c-261">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-261">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-262">XSD-ElementHavingnamespace.xml と同じフォルダーに Updategram-ElementHavingNamespace.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-262">Save the file as Updategram-ElementHavingNamespace.xml in the same folder used to save XSD-ElementHavingnamespace.xml.</span></span>  
  
3.  <span data-ttu-id="fd14c-263">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-263">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="fd14c-264">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-264">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="i-inserting-data-into-an-xml-data-type-column"></a><span data-ttu-id="fd14c-265">I.</span><span class="sxs-lookup"><span data-stu-id="fd14c-265">I.</span></span> <span data-ttu-id="fd14c-266">XML データ型列にデータを挿入する</span><span class="sxs-lookup"><span data-stu-id="fd14c-266">Inserting data into an XML data type column</span></span>  
 <span data-ttu-id="fd14c-267">`xml` データ型は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入されました。</span><span class="sxs-lookup"><span data-stu-id="fd14c-267">The `xml` data type was introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="fd14c-268">アップデートグラムを使用して、`xml` データ型の列にデータを挿入したり、この列に格納されているデータを更新することができます。これには次の条件があります。</span><span class="sxs-lookup"><span data-stu-id="fd14c-268">You can use updategrams to insert and update data stored in `xml` data type columns with the following provisions:</span></span>  
  
-   <span data-ttu-id="fd14c-269">`xml` 列は、既存の行の識別に使用できません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-269">The `xml` column cannot be used for identifying an existing row.</span></span> <span data-ttu-id="fd14c-270">したがって、アップデートグラムの `updg:before` セクションに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-270">Therefore, it cannot be included in the `updg:before` section of an updategram.</span></span>  
  
-   <span data-ttu-id="fd14c-271">`xml` 列に挿入される XML フラグメントのスコープにある名前空間は保持されます。挿入されたフラグメントの最上位要素には、その名前空間宣言が追加されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-271">Namespaces that are in scope of the XML fragment inserted into the `xml` column will be preserved and their namespace declarations are added to the top element of the inserted fragment.</span></span>  
  
 <span data-ttu-id="fd14c-272">たとえば、次のアップデートグラム (SampleUpdateGram.xml) では、要素によって、 **\<Desc>** サンプルデータベースの Production>Productdescription テーブルの ProductDescription 列が更新され [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-272">For example, in the following updategram (SampleUpdateGram.xml), the **\<Desc>** element updates the ProductDescription column in the Production>productModel table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="fd14c-273">このアップデートグラムの結果として、ProductDescription 列の XML コンテンツが要素の XML コンテンツで更新され **\<Desc>** ます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-273">The result of this updategram is that the XML contents of the ProductDescription column are update with the XML contents of the **\<Desc>** element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
       <updg:before>  
<ProductModel ProductModelID="19">  
   <Name>Mountain-100</Name>  
</ProductModel>  
    </updg:before>  
    <updg:after>  
 <ProductModel>  
    <Name>Mountain-100</Name>  
    <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
        <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
              xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
              xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
              xmlns:html="http://www.w3.org/1999/xhtml"   
              xmlns="">  
  <p1:Summary>  
     <html:p>Insert Example</html:p>  
  </p1:Summary>  
  <p1:Manufacturer>  
    <p1:Name>AdventureWorks</p1:Name>  
    <p1:Copyright>2002</p1:Copyright>  
    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
  </p1:Manufacturer>  
  <p1:Features>These are the product highlights.   
    <wm:Warranty>  
       <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
       <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
    <wm:Maintenance>  
       <wm:NoOfYears>10 years</wm:NoOfYears>  
       <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
    </wm:Maintenance>  
    <wf:wheel>High performance wheels.</wf:wheel>  
    <wf:saddle>  
      <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle>  
    <wf:pedal>  
       <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal>  
    <wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter and wall-thickness required of a premium mountain frame. The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame>  
    <wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset>  
   </p1:Features>  
   <p1:Picture>  
      <p1:Angle>front</p1:Angle>  
      <p1:Size>small</p1:Size>  
      <p1:ProductPhotoID>118</p1:ProductPhotoID>  
   </p1:Picture>  
   <p1:Specifications> These are the product specifications.  
     <Material>Almuminum Alloy</Material>  
     <Color>Available in most colors</Color>  
     <ProductLine>Mountain bike</ProductLine>  
     <Style>Unisex</Style>  
     <RiderExperience>Advanced to Professional riders</RiderExperience>  
   </p1:Specifications>  
  </p1:ProductDescription>  
 </Desc>  
      </ProductModel>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="fd14c-274">このアップデートグラムでは、次の注釈付き XSD スキーマ (SampleSchema.xml) を参照しています。</span><span class="sxs-lookup"><span data-stu-id="fd14c-274">The updategram refers to the following annotated XSD schema (SampleSchema.xml).</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
     <xsd:complexType>  
       <xsd:sequence>  
          <xsd:element name="Name" type="xsd:string"></xsd:element>  
          <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
           <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="ProductDescription">  
                 <xsd:complexType>  
                   <xsd:sequence>  
                     <xsd:element name="Summary" type="xsd:anyType">  
                     </xsd:element>  
                   </xsd:sequence>  
                 </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>   
       </xsd:sequence>  
       <xsd:attribute name="ProductModelID" sql:field="ProductModelID"/>  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="fd14c-275">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="fd14c-275">To test the updategram</span></span>  
  
1.  <span data-ttu-id="fd14c-276">上のスキーマをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-276">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-277">XSD-SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-277">Save the file as XSD-SampleSchema.xml.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd14c-278">アップデートグラムでは既定のマッピングがサポートされるので、`xml` データ型の開始位置と終了位置を識別する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="fd14c-278">Because updategrams support default mapping, there is no way to identify the beginning and ending of the `xml` data type.</span></span> <span data-ttu-id="fd14c-279">つまり、`xml` データ型の列を含むテーブルを挿入または更新するときには、マッピング スキーマが必要です。</span><span class="sxs-lookup"><span data-stu-id="fd14c-279">This effectively means that a mapping schema is required when inserting or updating tables with `xml` data type columns.</span></span> <span data-ttu-id="fd14c-280">スキーマを指定しない場合、SQLXML では、テーブル内の列の 1 つが見つからないというエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="fd14c-280">When a schema is not provided, SQLXML returns an error indicating that one of the columns is missing from the table.</span></span>  
  
2.  <span data-ttu-id="fd14c-281">上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="fd14c-281">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="fd14c-282">SampleSchema.xml と同じフォルダーに SampleUpdategram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-282">Save the file as SampleUpdategram.xml in the same folder used to save SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="fd14c-283">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd14c-283">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="fd14c-284">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd14c-284">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd14c-285">参照</span><span class="sxs-lookup"><span data-stu-id="fd14c-285">See Also</span></span>  
 [<span data-ttu-id="fd14c-286">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="fd14c-286">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
