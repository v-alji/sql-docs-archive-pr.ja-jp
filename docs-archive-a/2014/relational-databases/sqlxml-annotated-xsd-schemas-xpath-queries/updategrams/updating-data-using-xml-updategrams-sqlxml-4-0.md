---
title: XML アップデートグラムを使用したデータの更新 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREF type attribute [SQLXML]
- before attribute
- <sync> block
- <after> block
- id attribute
- <before> block
- updg:after attribute
- mapping-schema attribute
- IDREFS type attribute [SQLXML]
- updg:id attribute
- multiple record updates
- after attribute
- updategrams [SQLXML], updating data
- updg:before attribute
- record updates [SQLXML]
ms.assetid: 90ef8a33-5ae3-4984-8259-608d2f1d727f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b019478868b61f293eda824d9b302099728dec4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642700"
---
# <a name="updating-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="b8e3f-102">XML アップデートグラムを使用した、データの更新 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="b8e3f-102">Updating Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="b8e3f-103">既存のデータを更新する場合は、ブロックとブロックの両方を指定する必要があり **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-103">When you update existing data, you must specify both the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="b8e3f-104">およびブロックで指定された要素は、 **\<before>** **\<after>** 必要な変更を記述します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-104">The elements specified in the **\<before>** and **\<after>** blocks describe the desired change.</span></span> <span data-ttu-id="b8e3f-105">アップデートグラムでは、ブロックに指定されている要素を使用して、 **\<before>** データベース内の既存のレコードを識別します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-105">The updategram uses the element(s) that are specified in the **\<before>** block to identify the existing record(s) in the database.</span></span> <span data-ttu-id="b8e3f-106">ブロック内の対応する要素は、 **\<after>** 更新操作の実行後にレコードがどのように表示されるかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-106">The corresponding element(s) in the **\<after>** block indicate how the records should look after executing the update operation.</span></span> <span data-ttu-id="b8e3f-107">この情報から、アップデートグラムでは、ブロックと一致する SQL ステートメントが作成され **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-107">From this information, the updategram creates an SQL statement that matches the **\<after>** block.</span></span> <span data-ttu-id="b8e3f-108">そのステートメントによってデータベースが更新されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-108">The updategram then uses this statement to update the database.</span></span>  
  
 <span data-ttu-id="b8e3f-109">更新操作のアップデートグラムの形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-109">This is the updategram format for an update operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
      <ElementName [updg:id="value"] .../>  
      [<ElementName [updg:id="value"] .../> ... ]  
   </updg:before>  
   <updg:after>  
      <ElementName [updg:id="value"] ... />  
      [<ElementName [updg:id="value"] .../> ...]  
   </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 `<updg:before>`  
 <span data-ttu-id="b8e3f-110">ブロック内の要素は、 **\<before>** データベーステーブル内の既存のレコードを識別します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-110">The elements in the **\<before>** block identify existing records in the database tables.</span></span>  
  
 `<updg:after>`  
 <span data-ttu-id="b8e3f-111">ブロック内の要素は、 **\<after>** ブロックに指定されたレコードが **\<before>** 更新プログラムが適用された後にどのように表示されるかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-111">The elements in the **\<after>** block describe how the records specified in the **\<before>** block should look after the updates are applied.</span></span>  
  
 <span data-ttu-id="b8e3f-112">`mapping-schema` 属性では、アップデートグラムで使用するマッピング スキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-112">The `mapping-schema` attribute identifies the mapping schema to be used by the updategram.</span></span> <span data-ttu-id="b8e3f-113">アップデートグラムでマッピングスキーマを指定する場合は、およびブロックで指定された要素名と属性名 **\<before>** **\<after>** が、スキーマ内の名前と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-113">If the updategram specifies a mapping schema, the element and attribute names specified in the **\<before>** and **\<after>** blocks must match the names in the schema.</span></span> <span data-ttu-id="b8e3f-114">マッピング スキーマでは、これらの要素または属性の名前がデータベース テーブルと列の名前にマップされます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-114">The mapping schema maps these element or attribute names to the database table and column names.</span></span>  
  
 <span data-ttu-id="b8e3f-115">アップデートグラムにスキーマを指定しない場合は、アップデートグラムで既定のマッピングが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-115">If an updategram does not specify a schema, the updategam uses default mapping.</span></span> <span data-ttu-id="b8e3f-116">既定のマッピングでは、 **\<ElementName>** アップデートグラムで指定したがデータベーステーブルにマップされ、子要素または属性がデータベース列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-116">In default mapping, the **\<ElementName>** specified in the updategram maps to the database table and the child elements or attributes map to the database columns.</span></span>  
  
 <span data-ttu-id="b8e3f-117">ブロック内の要素は **\<before>** 、データベース内の1つのテーブル行にのみ一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-117">An element in the **\<before>** block must match with only one table row in the database.</span></span> <span data-ttu-id="b8e3f-118">要素が複数のテーブル行に一致するか、テーブル行と一致しない場合、アップデートグラムはエラーを返し、ブロック全体を取り消し **\<sync>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-118">If the element either matches multiple table rows or does not match any table row, the updategram returns an error and cancels the entire **\<sync>** block.</span></span>  
  
 <span data-ttu-id="b8e3f-119">アップデートグラムには、複数のブロックを含めることができ **\<sync>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-119">An updategram can include multiple **\<sync>** blocks.</span></span> <span data-ttu-id="b8e3f-120">各 **\<sync>** ブロックはトランザクションとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-120">Each **\<sync>** block is treated as a transaction.</span></span> <span data-ttu-id="b8e3f-121">各 **\<sync>** ブロックには、複数のおよびブロックを含めることができ **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-121">Each **\<sync>** block can have multiple **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="b8e3f-122">たとえば、既存の2つのレコードを更新する場合は、 **\<before>** **\<after>** 更新するレコードごとに1つずつ、2つのペアを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-122">For example, if you are updating two of the existing records, you could specify two **\<before>** and **\<after>** pairs, one for each record being updated.</span></span>  
  
## <a name="using-the-updgid-attribute"></a><span data-ttu-id="b8e3f-123">updg:id 属性の使用</span><span class="sxs-lookup"><span data-stu-id="b8e3f-123">Using the updg:id Attribute</span></span>  
 <span data-ttu-id="b8e3f-124">およびブロックに複数の要素が指定されている場合は、 **\<before>** **\<after>** 属性を使用して、 `updg:id` ブロックおよびブロック内の行をマークし **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-124">When multiple elements are specified in the **\<before>** and **\<after>** blocks, use the `updg:id` attribute to mark rows in the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="b8e3f-125">処理ロジックでは、この情報を使用して、ブロック内のどのレコードがブロック内のどのレコードであるかを判断し **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-125">The processing logic uses this information to determine what record in the **\<before>** block pairs with what record in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="b8e3f-126">次のいずれかに該当する場合、`updg:id` 属性は必ずしも必要ではありません (ただし使用が推奨されます)。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-126">The `updg:id` attribute is not necessary (although recommended) if either of the following exists:</span></span>  
  
-   <span data-ttu-id="b8e3f-127">指定したマッピング スキーマの要素に `sql:key-fields` 属性がある。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-127">The elements in the specified mapping schema have the `sql:key-fields` attribute defined on them.</span></span>  
  
-   <span data-ttu-id="b8e3f-128">アップデートグラムのキー フィールドに特定の値が 1 つ以上提供されている。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-128">There is one or more specific value supplied for the key field(s) in the updategram.</span></span>  
  
 <span data-ttu-id="b8e3f-129">いずれかに該当する場合、アップデートグラムでは、で指定されたキー列を使用 `sql:key-fields` **\<before>** して、ブロックとブロックの要素をペアにし **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-129">If either is the case, the updategram uses the key columns that are specified in the `sql:key-fields` to pair the elements in the **\<before>** and **\<after>** blocks.</span></span>  
  
 <span data-ttu-id="b8e3f-130">マッピング スキーマで `sql:key-fields` によりキー列が指定されていない場合、またはアップデートグラムでキー列の値を更新する場合は、`updg:id` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-130">If the mapping schema does not identify key columns (by using `sql:key-fields`) or if the updategram is updating a key column value, you must specify `updg:id`.</span></span>  
  
 <span data-ttu-id="b8e3f-131">およびブロックで識別されるレコードは、 **\<before>** **\<after>** 同じ順序である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-131">The records that are identified in the **\<before>** and **\<after>** blocks do not have to be in the same order.</span></span> <span data-ttu-id="b8e3f-132">`updg:id`属性は、およびブロックで指定されている要素間の関連付けを強制し **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-132">The `updg:id` attribute forces the association between the elements that are specified in the **\<before>** and **\<after>** blocks.</span></span>  
  
 <span data-ttu-id="b8e3f-133">ブロック内に1つの要素を指定し、 **\<before>** ブロック内に対応する要素を1つだけ指定した場合 **\<after>** 、を使用する `updg:id` 必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-133">If you specify one element in the **\<before>** block and only one corresponding element in the **\<after>** block, using `updg:id` is not necessary.</span></span> <span data-ttu-id="b8e3f-134">ただし、あいまいになるのを避けるため、この場合も `updg:id` を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-134">However, it is recommended that you specify `updg:id` anyway to avoid ambiguity.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b8e3f-135">例</span><span class="sxs-lookup"><span data-stu-id="b8e3f-135">Examples</span></span>  
 <span data-ttu-id="b8e3f-136">アップデートグラムの例を使用する前に、次のことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-136">Before you use the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="b8e3f-137">ほとんどの例では、アップデートグラムでマッピング スキーマを指定せず、既定のマッピングを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-137">Most of the examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="b8e3f-138">マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-138">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="b8e3f-139">ほとんどの例では、AdventureWorks サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-139">Most of the examples use the AdventureWorks sample database.</span></span> <span data-ttu-id="b8e3f-140">すべての更新内容は、このデータベースのテーブルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-140">All the updates are applied to the tables in this database.</span></span> <span data-ttu-id="b8e3f-141">AdventureWorks データベースは復元できます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-141">You can restore the AdventureWorks database.</span></span>  
  
### <a name="a-updating-a-record"></a><span data-ttu-id="b8e3f-142">A.</span><span class="sxs-lookup"><span data-stu-id="b8e3f-142">A.</span></span> <span data-ttu-id="b8e3f-143">レコードを更新する</span><span class="sxs-lookup"><span data-stu-id="b8e3f-143">Updating a record</span></span>  
 <span data-ttu-id="b8e3f-144">次のアップデートグラムでは、AdventureWorks データベースの Person.Contact テーブルで、従業員の姓を Fuller に更新します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-144">The following updategram updates the employee last name to Fuller in the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="b8e3f-145">アップデートグラムにマッピング スキーマは指定しないので、既定のマッピングが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-145">The updategram does not specify any mapping schema; therefore, the updategram uses default mapping.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact LastName="Abel-Achong" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b8e3f-146">ブロックに記述されているレコードは、 **\<before>** データベース内の現在のレコードを表します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-146">The record described in the **\<before>** block represents the current record in the database.</span></span> <span data-ttu-id="b8e3f-147">アップデートグラムでは、ブロックで指定されたすべての列の値を使用して **\<before>** 、レコードを検索します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-147">The updategram uses all of the column values specified in the **\<before>** block to search for the record.</span></span> <span data-ttu-id="b8e3f-148">このアップデートグラムでは、 **\<before>** ブロックは ContactID 列のみを提供します。そのため、アップデートグラムでは、値のみを使用してレコードが検索されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-148">In this updategram, the **\<before>** block provides only the ContactID column; therefore, the updategram uses only the value to search for the record.</span></span> <span data-ttu-id="b8e3f-149">仮に、このブロックに LastName 値を追加した場合は、検索に ContactID と LastName の両方の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-149">If you were to add the LastName value to this block, the updategram would use both the ContactID and LastName values to search.</span></span>  
  
 <span data-ttu-id="b8e3f-150">このアップデートグラムでは、 **\<after>** 変更されている唯一の値であるため、block は LastName 列の値のみを提供します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-150">In this updategram, the **\<after>** block provides only the LastName column value because this is the only value that is being changed.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b8e3f-151">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="b8e3f-151">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b8e3f-152">上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="b8e3f-152">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="b8e3f-153">UpdateLastName.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-153">Save the file as UpdateLastName.xml.</span></span>  
  
2.  <span data-ttu-id="b8e3f-154">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-154">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b8e3f-155">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-155">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="b-updating-multiple-records-by-using-the-updgid-attribute"></a><span data-ttu-id="b8e3f-156">B.</span><span class="sxs-lookup"><span data-stu-id="b8e3f-156">B.</span></span> <span data-ttu-id="b8e3f-157">updg:id 属性を使用して複数のレコードを更新する</span><span class="sxs-lookup"><span data-stu-id="b8e3f-157">Updating multiple records by using the updg:id attribute</span></span>  
 <span data-ttu-id="b8e3f-158">この例では、アップデートグラムで、AdventureWorks データベースの HumanResources.Shift テーブルに次の 2 つの更新操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-158">In this example, the updategram performs two updates on the HumanResources.Shift table in the AdventureWorks database:</span></span>  
  
-   <span data-ttu-id="b8e3f-159">7:00AM から始まる勤務時間の名前を "Day" から "Early Morning" に変更する。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-159">It changes the name of the original day shift that starts at 7:00AM from "Day" to "Early Morning".</span></span>  
  
-   <span data-ttu-id="b8e3f-160">10:00AM から始まる、"Late Morning" という名前の新しい勤務時間を挿入する。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-160">It inserts a new shift named "Late Morning" that starts at 10:00AM.</span></span>  
  
 <span data-ttu-id="b8e3f-161">アップデートグラムでは、属性によって、 `updg:id` ブロックとブロックの要素間の関連付けが作成され **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-161">In the updategram, the `updg:id` attribute creates associations between elements in the **\<before>** and **\<after>** blocks.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift updg:id="x" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift updg:id="y" Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
      <HumanResources.Shift updg:id="x" Name="Early Morning" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b8e3f-162">属性が、ブロック `updg:id` 内の要素の最初のインスタンスとブロック \<HumanResources.Shift> 内の **\<before>** 要素の2番目のインスタンスとのペアになっていることに注目 \<HumanResources.Shift> して **\<after>** ください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-162">Notice how the `updg:id` attribute pairs the first instance of the \<HumanResources.Shift> element in the **\<before>** block with the second instance of the \<HumanResources.Shift> element in the **\<after>** block.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b8e3f-163">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="b8e3f-163">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b8e3f-164">上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="b8e3f-164">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="b8e3f-165">UpdateMultipleRecords.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-165">Save the file as UpdateMultipleRecords.xml.</span></span>  
  
2.  <span data-ttu-id="b8e3f-166">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-166">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b8e3f-167">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-167">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="c-specifying-multiple-before-and-after-blocks"></a><span data-ttu-id="b8e3f-168">C.</span><span class="sxs-lookup"><span data-stu-id="b8e3f-168">C.</span></span> <span data-ttu-id="b8e3f-169">複数 \<before> のブロックとブロックの指定 \<after></span><span class="sxs-lookup"><span data-stu-id="b8e3f-169">Specifying multiple \<before> and \<after> blocks</span></span>  
 <span data-ttu-id="b8e3f-170">あいまいさを避けるために、複数のおよびブロックのペアを使用して、例 B でアップデートグラムを記述でき **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-170">To avoid ambiguity, you can write the updategram in Example B by using multiple **\<before>** and **\<after>** block pairs.</span></span> <span data-ttu-id="b8e3f-171">**\<before>** とのペアを指定する **\<after>** ことは、少なくとも混乱を最小限に抑えて複数の更新プログラムを指定する方法の1つです。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-171">Specifying **\<before>** and **\<after>** pairs is one way of specifying multiple updates with a minimum of confusion.</span></span> <span data-ttu-id="b8e3f-172">また、との各ブロックが1つの要素のみを指定している場合は、 **\<before>** 属性を **\<after>** 使用する必要はありません `updg:id` 。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-172">Also, if each of the **\<before>** and **\<after>** blocks specify at most one element, you do not have to use the `updg:id` attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8e3f-173">ペアを形成するには、 **\<after>** タグが対応するタグの直後にある必要があり **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-173">To form a pair, the **\<after>** tag must immediately follow its corresponding **\<before>** tag.</span></span>  
  
 <span data-ttu-id="b8e3f-174">次のアップデートグラムでは、最初のとのペアによって、 **\<before>** **\<after>** 日シフトのシフト名が更新されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-174">In the following updategram, the first **\<before>** and **\<after>** pair updates the shift name for the day shift.</span></span> <span data-ttu-id="b8e3f-175">2 番目の組によって新しい勤務時間のレコードが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-175">The second pair inserts a new shift record.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Early Morning" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b8e3f-176">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="b8e3f-176">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b8e3f-177">上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="b8e3f-177">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="b8e3f-178">UpdateMultipleBeforeAfter.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-178">Save the file as UpdateMultipleBeforeAfter.xml.</span></span>  
  
2.  <span data-ttu-id="b8e3f-179">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-179">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b8e3f-180">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-180">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="d-specifying-multiple-sync-blocks"></a><span data-ttu-id="b8e3f-181">D.</span><span class="sxs-lookup"><span data-stu-id="b8e3f-181">D.</span></span> <span data-ttu-id="b8e3f-182">複数の \<sync> ブロックの指定</span><span class="sxs-lookup"><span data-stu-id="b8e3f-182">Specifying multiple \<sync> blocks</span></span>  
 <span data-ttu-id="b8e3f-183">アップデートグラムでは、複数のブロックを指定でき **\<sync>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-183">You can specify multiple **\<sync>** blocks in an updategram.</span></span> <span data-ttu-id="b8e3f-184">指定された各 **\<sync>** ブロックは、独立したトランザクションです。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-184">Each **\<sync>** block that is specified is an independent transaction.</span></span>  
  
 <span data-ttu-id="b8e3f-185">次のアップデートグラムでは、最初の **\<sync>** ブロックが Sales. Customer テーブルのレコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-185">In the following updategram, the first **\<sync>** block updates a record in the Sales.Customer table.</span></span> <span data-ttu-id="b8e3f-186">簡素化するため、アップデートグラムでは ID 値 (CustomerID) と更新する値 (SalesPersonID) の 2 つの必要な値だけを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-186">For the sake of simplicity, the updategram specifies only the required column values; the identity value (CustomerID) and the value being updated (SalesPersonID).</span></span>  
  
 <span data-ttu-id="b8e3f-187">2番目のブロックは、 **\<sync>** SalesOrderHeader テーブルに2つのレコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-187">The second **\<sync>** block adds two records to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="b8e3f-188">このテーブルで、SalesOrderID は IDENTITY 型の列です。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-188">For this table, SalesOrderID is an IDENTITY-type column.</span></span> <span data-ttu-id="b8e3f-189">そのため、アップデートグラムでは、各要素の SalesOrderID の値が指定されていません \<Sales.SalesOrderHeader> 。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-189">Therefore, the updategram does not specify the value of SalesOrderID in each of the \<Sales.SalesOrderHeader> elements.</span></span>  
  
 <span data-ttu-id="b8e3f-190">複数のブロックを指定する **\<sync>** と便利です。これは、2つ目の **\<sync>** ブロック (トランザクション) が SalesOrderHeader テーブルにレコードを追加できなかった場合でも、最初の **\<sync>** ブロックが sales. customer テーブルの customer レコードを更新する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-190">Specifying multiple **\<sync>** blocks is useful because if the second **\<sync>** block (a transaction) fails to add records to Sales.SalesOrderHeader table, the first **\<sync>** block can still update the customer record in the Sales.Customer table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
      <Sales.Customer CustomerID="1" SalesPersonID="280" />  
    </updg:before>  
    <updg:after>  
      <Sales.Customer CustomerID="1" SalesPersonID="283" />  
    </updg:after>  
  </updg:sync>  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
   <Sales.SalesOrderHeader   
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="01010101-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-08 00:00:00.000" />  
   <Sales.SalesOrderHeader  
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="1000.0000"  
             TaxAmt="0.0000"  
             Freight="0.0000"  
             rowguid="10101010-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-09 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b8e3f-191">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="b8e3f-191">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b8e3f-192">上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="b8e3f-192">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="b8e3f-193">UpdateMultipleSyncs.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-193">Save the file as UpdateMultipleSyncs.xml.</span></span>  
  
2.  <span data-ttu-id="b8e3f-194">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-194">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b8e3f-195">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-195">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="e-using-a-mapping-schema"></a><span data-ttu-id="b8e3f-196">E.</span><span class="sxs-lookup"><span data-stu-id="b8e3f-196">E.</span></span> <span data-ttu-id="b8e3f-197">マッピング スキーマを使用する</span><span class="sxs-lookup"><span data-stu-id="b8e3f-197">Using a mapping schema</span></span>  
 <span data-ttu-id="b8e3f-198">この例では、アップデートグラムで `mapping-schema` を使用してマッピング スキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-198">In this example, the updategram specifies a mapping schema by using the `mapping-schema` attribute.</span></span> <span data-ttu-id="b8e3f-199">ここでは既定のマッピングはなく、アップデートグラム内の要素および属性と、データベースのテーブルおよび列の間の必要なマッピングはマッピング スキーマによって指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-199">(There is no default mapping; that is, the mapping schema provides the necessary mapping of elements and attributes in the updategram to the database tables and columns.)</span></span>  
  
 <span data-ttu-id="b8e3f-200">アップデートグラムで指定する要素と属性は、マッピング スキーマ内の要素と属性を参照します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-200">The elements and attributes specified in the updategram refer to the elements and attributes in the mapping schema.</span></span>  
  
 <span data-ttu-id="b8e3f-201">次の XSD マッピングスキーマには **\<Customer>** 、 **\<Order>** データベースの **\<OD>** sales. Customer、SalesOrderHeader、および SalesOrderDetail テーブルにマップされる、、およびの各要素があります。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-201">The following XSD mapping schema has **\<Customer>**, **\<Order>**, and **\<OD>** elements that map to the Sales.Customer, Sales.SalesOrderHeader, and Sales.SalesOrderDetail tables in the database.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustomerOrder"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustomerOrder" >  
           <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OD"   
                             sql:relation="Sales.SalesOrderDetail"  
                             sql:relationship="OrderOD" >  
                 <xsd:complexType>  
                  <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                  <xsd:attribute name="ProductID" type="xsd:integer" />  
                  <xsd:attribute name="UnitPrice" type="xsd:decimal" />  
                  <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  <xsd:attribute name="UnitPriceDiscount" type="xsd:decimal" />   
                 </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
           </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="b8e3f-202">このマッピング スキーマ (UpdategramMappingSchema.xml) を次のアップデートグラムで指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-202">This mapping schema (UpdategramMappingSchema.xml) is specified in the following updategram.</span></span> <span data-ttu-id="b8e3f-203">このアップデートグラムでは、Sales.SalesOrderDetail テーブルの特定の注文アイテムに、注文明細アイテムを追加します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-203">The updategram adds an order detail item in the Sales.SalesOrderDetail table for a specific order.</span></span> <span data-ttu-id="b8e3f-204">このアップデートグラムには、入れ子になった要素 (要素の内側に入れ子になった要素) が含まれ **\<OD>** **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-204">The updategram includes nested elements: an **\<OD>** element nested inside an **\<Order>** element.</span></span> <span data-ttu-id="b8e3f-205">これら 2 つの要素の主キーと外部キーのリレーションシップは、マッピング スキーマで指定されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-205">The primary key/foreign key relationship between these two elements is specified in the mapping schema.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="UpdategramMappingSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43659" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43659" >  
          <OD ProductID="776" UnitPrice="2329.0000"  
              OrderQty="2" UnitPriceDiscount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b8e3f-206">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="b8e3f-206">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b8e3f-207">上のマッピング スキーマをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="b8e3f-207">Copy the mapping schema above and paste it into a text file.</span></span> <span data-ttu-id="b8e3f-208">UpdategramMappingSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-208">Save the file as UpdategramMappingSchema.xml.</span></span>  
  
2.  <span data-ttu-id="b8e3f-209">上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="b8e3f-209">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="b8e3f-210">マッピング スキーマ (UpdategramMappingSchema.xml) と同じフォルダーに UpdateWithMappingSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-210">Save the file as UpdateWithMappingSchema.xml in the same folder as was used to save the mapping schema (UpdategramMappingSchema.xml).</span></span>  
  
3.  <span data-ttu-id="b8e3f-211">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-211">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b8e3f-212">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-212">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="b8e3f-213">マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-213">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
### <a name="f-using-a-mapping-schema-with-idrefs-attributes"></a><span data-ttu-id="b8e3f-214">F.</span><span class="sxs-lookup"><span data-stu-id="b8e3f-214">F.</span></span> <span data-ttu-id="b8e3f-215">マッピング スキーマを IDREFS 属性と共に使用する</span><span class="sxs-lookup"><span data-stu-id="b8e3f-215">Using a mapping schema with IDREFS attributes</span></span>  
 <span data-ttu-id="b8e3f-216">この例では、アップデートグラムでマッピング スキーマ内の IDREFS 属性を使用して、複数のテーブルのレコードを更新する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-216">This example illustrates how updategrams use the IDREFS attributes in the mapping schema to update records in multiple tables.</span></span> <span data-ttu-id="b8e3f-217">この例では、データベースは次のテーブルから構成されるものとします。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-217">For this example, assume that the database consists of the following tables:</span></span>  
  
-   <span data-ttu-id="b8e3f-218">Student (StudentID、LastName)</span><span class="sxs-lookup"><span data-stu-id="b8e3f-218">Student(StudentID, LastName)</span></span>  
  
-   <span data-ttu-id="b8e3f-219">Course (CourseID、CourseName)</span><span class="sxs-lookup"><span data-stu-id="b8e3f-219">Course(CourseID, CourseName)</span></span>  
  
-   <span data-ttu-id="b8e3f-220">Enrollment (StudentID、CourseID)</span><span class="sxs-lookup"><span data-stu-id="b8e3f-220">Enrollment(StudentID, CourseID)</span></span>  
  
 <span data-ttu-id="b8e3f-221">学生 (Student) は複数の講座 (Course) に登録できるので、Course には複数の Student を含めることができます。3 番目のテーブル Enrollment は、この M:N リレーションシップを表すために必要です。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-221">Because a student can enroll in many courses and a course can have many students, the third table, the Enrollment table, is required to represent this M:N relationship.</span></span>  
  
 <span data-ttu-id="b8e3f-222">次の XSD マッピングスキーマでは、、、およびの各要素を使用して、テーブルの XML ビューを提供し **\<Student>** **\<Course>** **\<Enrollment>** ます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-222">The following XSD mapping schema provides an XML view of the tables by using the **\<Student>**, **\<Course>**, and **\<Enrollment>** elements.</span></span> <span data-ttu-id="b8e3f-223">マッピングスキーマ内の**IDREFS**属性は、これらの要素間のリレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-223">The **IDREFS** attributes in the mapping schema specify the relationship between these elements.</span></span> <span data-ttu-id="b8e3f-224">要素の**StudentIDList**属性 **\<Course>** は、登録テーブルの StudentID 列を参照する**IDREFS**型の属性です。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-224">The **StudentIDList** attribute on the **\<Course>** element is an **IDREFS** type attribute that refers to the StudentID column in the Enrollment table.</span></span> <span data-ttu-id="b8e3f-225">同様に、要素の**EnrolledIn**属性 **\<Student>** は**IDREFS**型の属性であり、登録テーブルの CourseID 列を参照します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-225">Likewise, the **EnrolledIn** attribute on the **\<Student>** element is an **IDREFS** type attribute that refers to the CourseID column in the Enrollment table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="StudentEnrollment"  
          parent="Student"  
          parent-key="StudentID"  
          child="Enrollment"  
          child-key="StudentID" />  
  
    <sql:relationship name="CourseEnrollment"  
          parent="Course"  
          parent-key="CourseID"  
          child="Enrollment"  
          child-key="CourseID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Course" sql:relation="Course"   
                             sql:key-fields="CourseID" >  
    <xsd:complexType>  
    <xsd:attribute name="CourseID"  type="xsd:string" />   
    <xsd:attribute name="CourseName"   type="xsd:string" />   
    <xsd:attribute name="StudentIDList" sql:relation="Enrollment"  
                 sql:field="StudentID"  
                 sql:relationship="CourseEnrollment"   
                                     type="xsd:IDREFS" />  
  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name="Student" sql:relation="Student" >  
    <xsd:complexType>  
    <xsd:attribute name="StudentID"  type="xsd:string" />   
    <xsd:attribute name="LastName"   type="xsd:string" />   
    <xsd:attribute name="EnrolledIn" sql:relation="Enrollment"  
                 sql:field="CourseID"  
                 sql:relationship="StudentEnrollment"   
                                     type="xsd:IDREFS" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="b8e3f-226">アップデートグラムでこのスキーマを指定して Course テーブルにレコードを挿入すると、Course テーブルには常に新しい講座レコードが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-226">Whenever you specify this schema in an updategram and insert a record in the Course table, the updategram inserts a new course record in the Course table.</span></span> <span data-ttu-id="b8e3f-227">StudentIDList 属性に 1 つ以上の新しい学生 ID を指定すると、アップデートグラムでは Enrollment テーブルにも新しい学生ごとのレコードが挿入され、</span><span class="sxs-lookup"><span data-stu-id="b8e3f-227">If you specify one or more new student IDs for the StudentIDList attribute, the updategram also inserts a record in the Enrollment table for the each new student.</span></span> <span data-ttu-id="b8e3f-228">重複した値が追加されていないことが Enrollment テーブルで確認されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-228">The updategram ensures that no duplicates are added to the Enrollment table.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b8e3f-229">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="b8e3f-229">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b8e3f-230">仮想ルートに指定したデータベースに、これらのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-230">Create these tables in the database that is specified in the virtual root:</span></span>  
  
    ```  
    CREATE TABLE Student(StudentID varchar(10) primary key,   
                         LastName varchar(25))  
    CREATE TABLE Course(CourseID varchar(10) primary key,   
                        CourseName varchar(25))  
    CREATE TABLE Enrollment(StudentID varchar(10)   
                                      references Student(StudentID),  
                           CourseID varchar(10)   
                                      references Course(CourseID))  
    ```  
  
2.  <span data-ttu-id="b8e3f-231">次のサンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-231">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Student VALUES ('S1','Davoli')  
    INSERT INTO Student VALUES ('S2','Fuller')  
  
    INSERT INTO Course VALUES  ('CS101', 'C Programming')  
    INSERT INTO Course VALUES  ('CS102', 'Understanding XML')  
  
    INSERT INTO Enrollment VALUES ('S1', 'CS101')  
    INSERT INTO Enrollment VALUES ('S1', 'CS102')  
    ```  
  
3.  <span data-ttu-id="b8e3f-232">上のマッピング スキーマをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="b8e3f-232">Copy the mapping schema above and paste it into a text file.</span></span> <span data-ttu-id="b8e3f-233">SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-233">Save the file as SampleSchema.xml.</span></span>  
  
4.  <span data-ttu-id="b8e3f-234">上の手順のマッピング スキーマと同じフォルダーに、アップデートグラム (SampleUpdategram) を保存します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-234">Save the updategram (SampleUpdategram) in the same folder used to save the mapping schema in the previous step.</span></span> <span data-ttu-id="b8e3f-235">このアップデートグラムでは、講座 CS102 から StudentID="1" の学生を削除します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-235">(This updategram drops a student with StudentID="1" from the CS102 course.)</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
5.  <span data-ttu-id="b8e3f-236">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-236">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b8e3f-237">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-237">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
6.  <span data-ttu-id="b8e3f-238">上の手順の説明どおり、次のアップデートグラムを保存して実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-238">Save and execute the following updategram as described in the previous steps.</span></span> <span data-ttu-id="b8e3f-239">このアップデートグラムでは、Enrollment テーブルにレコードを追加し、講義 CS102 に StudentID="1" の学生をもう一度追加します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-239">The updategram adds the student with StudentID="1" back into the CS102 course by adding a record in the Enrollment table.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
7.  <span data-ttu-id="b8e3f-240">前の手順の説明どおり、次のアップデートグラムを保存して実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-240">Save and execute this next updategram as described in the previous steps.</span></span> <span data-ttu-id="b8e3f-241">このアップデートグラムでは、新しい学生を 3 人追加し、講座 CS101 に登録します。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-241">This updategram inserts three new students and enrolls them in the CS101 course.</span></span> <span data-ttu-id="b8e3f-242">ここでもまた、IDREFS リレーションシップによって、Enrollment テーブルにレコードが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-242">Again, the IDREFS relationship inserts records in the Enrollment table.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
           <Course updg:id="y" CourseID="CS101"   
                               CourseName="C Programming" />  
        </updg:before>  
        <updg:after >  
           <Student updg:id="x1" StudentID="S3" LastName="Leverling" />  
           <Student updg:id="x2" StudentID="S4" LastName="Pecock" />  
           <Student updg:id="x3" StudentID="S5" LastName="Buchanan" />  
           <Course updg:id="y" CourseID="CS101"  
                               CourseName="C Programming"  
                               StudentIDList="S3 S4 S5" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
 <span data-ttu-id="b8e3f-243">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-243">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ElementType name="Enrollment" sql:relation="Enrollment" sql:key-fields="StudentID CourseID">  
    <AttributeType name="StudentID" dt:type="id" />  
    <AttributeType name="CourseID" dt:type="id" />  
  
    <attribute type="StudentID" />  
    <attribute type="CourseID" />  
  </ElementType>  
  <ElementType name="Course" sql:relation="Course" sql:key-fields="CourseID">  
    <AttributeType name="CourseID" dt:type="id" />  
    <AttributeType name="CourseName" />  
  
    <attribute type="CourseID" />  
    <attribute type="CourseName" />  
  
    <AttributeType name="StudentIDList" dt:type="idrefs" />  
    <attribute type="StudentIDList" sql:relation="Enrollment" sql:field="StudentID" >  
        <sql:relationship  
                key-relation="Course"  
                key="CourseID"  
                foreign-relation="Enrollment"  
                foreign-key="CourseID" />  
    </attribute>  
  
  </ElementType>  
  <ElementType name="Student" sql:relation="Student">  
    <AttributeType name="StudentID" dt:type="id" />  
     <AttributeType name="LastName" />  
  
    <attribute type="StudentID" />  
    <attribute type="LastName" />  
  
    <AttributeType name="EnrolledIn" dt:type="idrefs" />  
    <attribute type="EnrolledIn" sql:relation="Enrollment" sql:field="CourseID" >  
        <sql:relationship  
                key-relation="Student"  
                key="StudentID"  
                foreign-relation="Enrollment"  
                foreign-key="StudentID" />  
    </attribute>  
  
    <element type="Enrollment" sql:relation="Enrollment" >  
        <sql:relationship key-relation="Student"  
                          key="StudentID"  
                          foreign-relation="Enrollment"  
                          foreign-key="StudentID" />  
    </element>  
  </ElementType>  
  
</Schema>  
```  
  
 <span data-ttu-id="b8e3f-244">マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e3f-244">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e3f-245">参照</span><span class="sxs-lookup"><span data-stu-id="b8e3f-245">See Also</span></span>  
 [<span data-ttu-id="b8e3f-246">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="b8e3f-246">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
