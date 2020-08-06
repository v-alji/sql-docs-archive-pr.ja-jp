---
title: XML アップデートグラムを使用したデータの削除 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: rothja
ms.author: jroth
ms.openlocfilehash: d941005c71dc33dd8c4f5c5cc15f645cd0e68177
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643733"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="dc52c-102">XML アップデートグラムを使用した、データの削除 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="dc52c-102">Deleting Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="dc52c-103">アップデートグラムでは、ブロック内にレコードインスタンスが存在し、対応するレコードがブロック内にない場合の削除操作を示し **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="dc52c-103">An updategram indicates a delete operation when a record instance appears in the **\<before>** block with no corresponding records in the **\<after>** block.</span></span> <span data-ttu-id="dc52c-104">この場合、アップデートグラムではブロック内のレコードがデータベースから削除され **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="dc52c-104">In this case, the updategram deletes the record in the **\<before>** block from the database.</span></span>  
  
 <span data-ttu-id="dc52c-105">削除操作のアップデートグラムの形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dc52c-105">This is the updategram format for a delete operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="dc52c-106">**\<after>** アップデートグラムが削除操作のみを実行している場合は、タグを省略できます。</span><span class="sxs-lookup"><span data-stu-id="dc52c-106">You can omit the **\<after>** tag if the updategram is performing only a delete operation.</span></span> <span data-ttu-id="dc52c-107">省略可能な属性を指定しない場合 `mapping-schema` 、 **\<ElementName>** アップデートグラムで指定したはデータベーステーブルにマップされ、子要素または属性はテーブル内の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="dc52c-107">If you do not specify the optional `mapping-schema` attribute, the **\<ElementName>** specified in the updategram maps to a database table and the child elements or attributes map to columns in the table.</span></span>  
  
 <span data-ttu-id="dc52c-108">アップデートグラムで指定した要素が、テーブル内の複数の行に一致するか、いずれの行とも一致しない場合、アップデートグラムではエラーが返され、ブロック全体がキャンセルされ **\<sync>** ます。</span><span class="sxs-lookup"><span data-stu-id="dc52c-108">If an element specified in the updategram either matches more than one row in the table or does not match any row, the updategram returns an error and cancels the entire **\<sync>** block.</span></span> <span data-ttu-id="dc52c-109">アップデートグラム内の要素で削除できるのは、一度に 1 つのレコードだけです。</span><span class="sxs-lookup"><span data-stu-id="dc52c-109">Only one record at a time can be deleted by an element in the updategram.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dc52c-110">例</span><span class="sxs-lookup"><span data-stu-id="dc52c-110">Examples</span></span>  
 <span data-ttu-id="dc52c-111">この例では、アップデートグラムでマッピング スキーマを指定せず、既定のマッピングを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc52c-111">Examples in this section use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="dc52c-112">マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc52c-112">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="dc52c-113">次の例を使用して実際のサンプルを作成するには、 [SQLXML の例を実行するための要件](../../sqlxml/requirements-for-running-sqlxml-examples.md)を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc52c-113">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a><span data-ttu-id="dc52c-114">A.</span><span class="sxs-lookup"><span data-stu-id="dc52c-114">A.</span></span> <span data-ttu-id="dc52c-115">アップデートグラムを使用してレコードを削除する</span><span class="sxs-lookup"><span data-stu-id="dc52c-115">Deleting a record by using an updategram</span></span>  
 <span data-ttu-id="dc52c-116">次のアップデートグラムでは、HumanResources.Shift テーブルから 2 つのレコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="dc52c-116">The following updategrams deletes two records from the HumanResources.Shift table.</span></span>  
  
 <span data-ttu-id="dc52c-117">この例のアップデートグラムでは、マッピング スキーマを指定しません。</span><span class="sxs-lookup"><span data-stu-id="dc52c-117">In these examples, the updategram does not specify a mapping schema.</span></span> <span data-ttu-id="dc52c-118">したがって、アップデートグラムでは既定のマッピングが使用されます。このマッピングでは、要素名はテーブル名にマップされ、属性または副要素は列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="dc52c-118">Therefore, the updategram uses default mapping, in which the element name maps to table name and the attributes or subelements map to columns.</span></span>  
  
 <span data-ttu-id="dc52c-119">この最初のアップデートグラムは属性中心で、ブロック内の2つのシフト (日、夜、夜) を識別し **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="dc52c-119">This first updategram is attribute-centric and identifies two shifts (Day-Evening and Evening-Night) in the **\<before>** block.</span></span> <span data-ttu-id="dc52c-120">ブロック内に対応するレコードがないため **\<after>** 、これは削除操作です。</span><span class="sxs-lookup"><span data-stu-id="dc52c-120">Because there is no corresponding record in the **\<after>** block, this is a delete operation.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="dc52c-121">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="dc52c-121">To test the updategram</span></span>  
  
1.  <span data-ttu-id="dc52c-122">「 [XML アップデートグラムを使用してデータを挿入する](inserting-data-using-xml-updategrams-sqlxml-4-0.md)」の例 B (「アップデートグラムを使用して複数のレコードを挿入する」) を実行します。 &#40;SQLXML 4.0&#41;。</span><span class="sxs-lookup"><span data-stu-id="dc52c-122">Complete example B ("Inserting multiple records by using an updategram") in [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
2.  <span data-ttu-id="dc52c-123">上のアップデートグラムをメモ帳にコピーして、「 [XML アップデートグラムを使用したデータの挿入](inserting-data-using-xml-updategrams-sqlxml-4-0.md)」の「アップデートグラムを使用して複数のレコードを挿入する」で使用したのと同じフォルダーに Updategram-RemoveShifts.xml として保存します。 &#40;SQLXML 4.0&#41;。</span><span class="sxs-lookup"><span data-stu-id="dc52c-123">Copy the updategram above to Notepad and save it as Updategram-RemoveShifts.xml in the same folder as was used to complete ("Inserting multiple records by using an updategram") in [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
3.  <span data-ttu-id="dc52c-124">SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="dc52c-124">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="dc52c-125">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc52c-125">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc52c-126">参照</span><span class="sxs-lookup"><span data-stu-id="dc52c-126">See Also</span></span>  
 [<span data-ttu-id="dc52c-127">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="dc52c-127">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
