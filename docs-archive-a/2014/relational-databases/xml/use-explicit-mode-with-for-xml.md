---
title: FOR XML での EXPLICIT モードの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT FOR XML mode
- FOR XML clause, EXPLICIT mode
- FOR XML EXPLICIT mode
ms.assetid: 8b26e8ce-5465-4e7a-b237-98d0f4578ab1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e3db80333c74166301fcff7bb25edea4aca38a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639921"
---
# <a name="use-explicit-mode-with-for-xml"></a><span data-ttu-id="b5997-102">FOR XML での EXPLICIT モードの使用</span><span class="sxs-lookup"><span data-stu-id="b5997-102">Use EXPLICIT Mode with FOR XML</span></span>
  <span data-ttu-id="b5997-103">トピック「 [FOR XML を使用した XML の構築](../xml/for-xml-sql-server.md)」で説明されているように、RAW モードと AUTO モードでは、クエリ結果から生成される XML の構造を厳密に制御することはできません。</span><span class="sxs-lookup"><span data-stu-id="b5997-103">As described in the topic, [Constructing XML Using FOR XML](../xml/for-xml-sql-server.md), RAW and AUTO mode do not provide much control over the shape of the XML generated from a query result.</span></span> <span data-ttu-id="b5997-104">一方、EXPLICIT モードを使用すると、クエリ結果から生成される XML の構造を柔軟に制御することができます。</span><span class="sxs-lookup"><span data-stu-id="b5997-104">However, EXPLICIT mode provides the most flexibility in generating the XML you want from a query result.</span></span>  
  
 <span data-ttu-id="b5997-105">ただし、必要な XML に関する追加情報 (XML 内の入れ子構造など) をクエリの一部として明示的に指定するために、EXPLICIT モードのクエリを記述する際には特殊な記述方法が必要になります。</span><span class="sxs-lookup"><span data-stu-id="b5997-105">The EXPLICIT mode query must be written in a specific way so that the additional information about the required XML, such as expected nesting in the XML, is explicitly specified as part of the query.</span></span> <span data-ttu-id="b5997-106">このため、要求する XML によっては、EXPLICIT モードのクエリを記述する作業が複雑になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b5997-106">Depending on the XML you request, writing EXPLICIT mode queries can be cumbersome.</span></span> <span data-ttu-id="b5997-107">EXPLICIT モードのクエリを記述するよりも、 [PATH モード](../xml/use-path-mode-with-for-xml.md) で入れ子を使用する方が作業が容易になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b5997-107">You may find that [Using PATH Mode](../xml/use-path-mode-with-for-xml.md) with nesting is a simpler alternative to writing EXPLICIT mode queries.</span></span>  
  
 <span data-ttu-id="b5997-108">EXPLICIT モードでは、目的の XML をクエリによって記述するので、正しい形式で有効な XML が生成されるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5997-108">Because you describe the XML you want as part of the query in EXPLICIT mode, you must ensure that the generated XML is well formed and valid.</span></span>  
  
## <a name="rowset-processing-in-explicit-mode"></a><span data-ttu-id="b5997-109">EXPLICIT モードでの行セットの処理</span><span class="sxs-lookup"><span data-stu-id="b5997-109">Rowset Processing in EXPLICIT Mode</span></span>  
 <span data-ttu-id="b5997-110">EXPLICIT モードでは、クエリを実行した結果として生じた行セットが XML に変換されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-110">The EXPLICIT mode transforms the rowset that results from the query execution into an XML document.</span></span> <span data-ttu-id="b5997-111">EXPLICIT モードで XML ドキュメントを作成するには、特殊な形式の行セットが必要になります。</span><span class="sxs-lookup"><span data-stu-id="b5997-111">In order for EXPLICIT mode to produce the XML document, the rowset must have a specific format.</span></span> <span data-ttu-id="b5997-112">そのためには、XML を処理ロジックで生成できるように、決められた形式の行セット ( **ユニバーサル テーブル**) を生成できるような選択クエリを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5997-112">This requires that you write the SELECT query to produce the rowset, the **universal table**, with a specific format so the processing logic can then produce the XML you want.</span></span>  
  
 <span data-ttu-id="b5997-113">まず、クエリで次の 2 つのメタデータ列を生成します。</span><span class="sxs-lookup"><span data-stu-id="b5997-113">First, the query must produce the following two metadata columns:</span></span>  
  
-   <span data-ttu-id="b5997-114">1 列目は **Tag**という名前で、現在の要素のタグ番号 (整数型) を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5997-114">The first column must provide the tag number, integer type, of the current element, and the column name must be **Tag**.</span></span> <span data-ttu-id="b5997-115">行セットから構築される要素ごとに、一意のタグ番号をクエリが提供しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="b5997-115">Your query must provide a unique tag number for each element that will be constructed from the rowset.</span></span>  
  
-   <span data-ttu-id="b5997-116">2 列目は **Parent**という名前で、親要素のタグ番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5997-116">The second column must provide a tag number of the parent element, and this column name must be **Parent**.</span></span> <span data-ttu-id="b5997-117">これにより、Tag 列と Parent 列の階層情報が定義されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-117">In this way, the Tag and the Parent column provide hierarchy information.</span></span>  
  
 <span data-ttu-id="b5997-118">XML を生成する際には、これらのメタデータ列の値が、列名の情報と共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-118">These metadata column values, together with the information in the column names, are used to produce the XML you want.</span></span> <span data-ttu-id="b5997-119">列名は、特殊な方法でクエリ内に指定します。</span><span class="sxs-lookup"><span data-stu-id="b5997-119">Note that your query must provide column names in a specific way.</span></span> <span data-ttu-id="b5997-120">**Parent** 列の値が 0 または NULL であれば、その要素に親要素がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="b5997-120">Also note that a 0 or NULL in the **Parent** column indicates that the corresponding element has no parent.</span></span> <span data-ttu-id="b5997-121">このような要素は、最上位の要素として XML に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-121">The element is added to the XML as a top-level element.</span></span>  
  
 <span data-ttu-id="b5997-122">クエリで生成したユニバーサル テーブルが、どのように処理され、XML として生成されるか、例を検証しましょう。ここでは、次のユニバーサル テーブルを生成するクエリを記述したとします。</span><span class="sxs-lookup"><span data-stu-id="b5997-122">To understand how the universal table generated by a query is processed into generating XML result, assume that you have written a query that produces this universal table:</span></span>  
  
 <span data-ttu-id="b5997-123">![ユニバーサル テーブルのサンプル](../../database-engine/media/xmlutable.gif "ユニバーサル テーブルのサンプル")</span><span class="sxs-lookup"><span data-stu-id="b5997-123">![Sample universal table](../../database-engine/media/xmlutable.gif "Sample universal table")</span></span>  
  
 <span data-ttu-id="b5997-124">このユニバーサル テーブルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b5997-124">Note the following about this universal table:</span></span>  
  
-   <span data-ttu-id="b5997-125">最初の 2 列は **Tag** 列と **Parent** 列で、これらはメタデータ列です。</span><span class="sxs-lookup"><span data-stu-id="b5997-125">The first two columns are **Tag** and **Parent** and are meta columns.</span></span> <span data-ttu-id="b5997-126">これらの値は、階層を決定します。</span><span class="sxs-lookup"><span data-stu-id="b5997-126">These values determine the hierarchy.</span></span>  
  
-   <span data-ttu-id="b5997-127">列名は、このトピックの後半で説明するように、決められた方法で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5997-127">The column names are specified in a certain way, as described later in this topic.</span></span>  
  
-   <span data-ttu-id="b5997-128">このユニバーサル テーブルから XML を生成する際、このテーブルのデータは列方向に (列グループに) パーティション分割されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-128">In generating the XML from this universal table, the data in this table is partitioned vertically into column groups.</span></span> <span data-ttu-id="b5997-129">このグループ化は、 **Tag** 列の値と列名によって決まります。</span><span class="sxs-lookup"><span data-stu-id="b5997-129">The grouping is determined based on the **Tag** value and the column names.</span></span> <span data-ttu-id="b5997-130">XML の生成時には、各行ごとに 1 つの列グループが選択され、1 つの要素が構築されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-130">In constructing XML, the processing logic selects one group of columns for each row and constructs an element.</span></span> <span data-ttu-id="b5997-131">この処理は、この例では次のように行われます。</span><span class="sxs-lookup"><span data-stu-id="b5997-131">The following applies in this example:</span></span>  
  
    -   <span data-ttu-id="b5997-132">1 行目の **Tag** 列の値は 1 なので、同じタグ番号を列名に含んでいる **Customer!1!cid** 列と **Customer!1!name**列でグループが形成されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-132">For **Tag** column value 1 in the first row, the columns whose names include the same tag number, **Customer!1!cid** and **Customer!1!name**, form a group.</span></span> <span data-ttu-id="b5997-133">これらの列が行の処理に使用され、生成される要素の形式は <`Customer id=... name=...`> のようになります。</span><span class="sxs-lookup"><span data-stu-id="b5997-133">These columns are used in processing the row, and you may have noticed that the shape of the generated element is <`Customer id=... name=...`>.</span></span> <span data-ttu-id="b5997-134">列名の形式については、このトピックの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="b5997-134">Column name format is described later in this topic.</span></span>  
  
    -   <span data-ttu-id="b5997-135">**Tag** 列の値が 2 の行については、**Order!2!id** 列と **Order!2!date** 列でグループが形成され、<`Order id=... date=... /`> という形式の要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-135">For rows with **Tag** column value 2, columns **Order!2!id** and **Order!2!date** form a group that is then used in constructing elements, <`Order id=... date=... /`>.</span></span>  
  
    -   <span data-ttu-id="b5997-136">**Tag** 列の値が 3 の行については、 **OrderDetail!3!id!id** 列と **OrderDetail!3!pid!idref** 列でグループが形成されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-136">For rows with **Tag** column value 3, columns **OrderDetail!3!id!id** and **OrderDetail!3!pid!idref** form a group.</span></span> <span data-ttu-id="b5997-137">これらの列からは、<`OrderDetail id=... pid=...`> という形式の要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-137">Each of these rows generates an element, <`OrderDetail id=... pid=...`>, from these columns.</span></span>  
  
-   <span data-ttu-id="b5997-138">XML 階層の生成時、行は順番に処理されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-138">Note that in generating XML hierarchy, the rows are processed in order.</span></span> <span data-ttu-id="b5997-139">XML 階層は、次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-139">The XML hierarchy is determined as shown in the following:</span></span>  
  
    -   <span data-ttu-id="b5997-140">1 行目では、 **Tag** 列に値 1 が指定され、 **Parent** 列には NULL が指定されています。</span><span class="sxs-lookup"><span data-stu-id="b5997-140">The first row specifies **Tag** value 1 and **Parent** value NULL.</span></span> <span data-ttu-id="b5997-141">したがって、対応する <`Customer`> 要素は、XML の最上位要素として追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-141">Therefore, the corresponding element, <`Customer`> element, is added as a top-level element in the XML.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
        ```  
  
    -   <span data-ttu-id="b5997-142">2 行目では、 **Tag** 列に値 2、 **Parent** 列に値 1 が指定されています。</span><span class="sxs-lookup"><span data-stu-id="b5997-142">The second row identifies **Tag** value 2 and **Parent** value 1.</span></span> <span data-ttu-id="b5997-143">したがって、<`Customer`> 要素の子要素として、<`Order`> 要素が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-143">Therefore, the element, <`Order`> element, is added as a child of the <`Customer`> element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
        ```  
  
    -   <span data-ttu-id="b5997-144">次の 2 行では、 **Tag** 列に値 3、 **Parent** 列に値 2 が指定されています。</span><span class="sxs-lookup"><span data-stu-id="b5997-144">The next two rows identify **Tag** value 3 and **Parent** value 2.</span></span> <span data-ttu-id="b5997-145">したがって、<`Order`> 要素の子要素として、2 つの <`OrderDetail`> 要素が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-145">Therefore, the two elements, <`OrderDetail`> elements, are added as children of the <`Order`> element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
              <OrderDetail id="OD1" pid="P1"/>  
              <OrderDetail id="OD2" pid="P2"/>  
        ```  
  
    -   <span data-ttu-id="b5997-146">最後の行では、 **Tag** 列に値 2 が指定され、 **Parent** 列には値 1 が指定されています。</span><span class="sxs-lookup"><span data-stu-id="b5997-146">The last row identifies 2 as the **Tag** number and 1 as the **Parent** tag number.</span></span> <span data-ttu-id="b5997-147">したがって、<`Customer`> 親要素には、別の <`Order`> 子要素が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-147">Therefore, another <`Order`> element child is added to the <`Customer`> parent element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
              <OrderDetail id="OD1" pid="P1"/>  
              <OrderDetail id="OD2" pid="P2"/>  
           </Order>  
           <Order id="O2" date="3/29/1997">  
        </Customer>  
        ```  
  
 <span data-ttu-id="b5997-148">つまり、EXPLICIT モードでは、 **Tag** メタデータ列と **Parent** メタデータ列の値、各列名に提供されている情報、および列の正しい順序に基づいて、必要な XML を生成できるということになります。</span><span class="sxs-lookup"><span data-stu-id="b5997-148">To summarize, the values in the **Tag** and **Parent** meta columns, the information provided in the column names, and the correct ordering of the rows produce the XML you want when you use EXPLICIT mode.</span></span>  
  
### <a name="universal-table-row-ordering"></a><span data-ttu-id="b5997-149">ユニバーサル テーブルの行の順序</span><span class="sxs-lookup"><span data-stu-id="b5997-149">Universal Table Row Ordering</span></span>  
 <span data-ttu-id="b5997-150">XML の生成時、ユニバーサル テーブルの行は順番に処理されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-150">In constructing the XML, the rows in the universal table are processed in order.</span></span> <span data-ttu-id="b5997-151">そのため、親と関連付けられている適切な子インスタンスを取得するには、各親ノードの直後がその親の子ノードになるという順序で、行セットの行が並んでいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5997-151">Therefore, to retrieve the correct children instances associated with their parent, the rows in the rowset must be ordered so that each parent node is immediately followed by its children.</span></span>  
  
## <a name="specifying-column-names-in-a-universal-table"></a><span data-ttu-id="b5997-152">ユニバーサル テーブルでの列名の指定</span><span class="sxs-lookup"><span data-stu-id="b5997-152">Specifying Column Names in a Universal Table</span></span>  
 <span data-ttu-id="b5997-153">EXPLICIT モードのクエリを記述する際に、結果の行セットの列名は、この形式を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="b5997-153">When writing EXPLICIT mode queries, column names in the resulting rowset must be specified by using this format.</span></span> <span data-ttu-id="b5997-154">列名では、ディレクティブを使用して、要素と属性の名前や他の追加情報などを含めた変換情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5997-154">They provide transformation information including element and attribute names and other additional information, specified by using directives.</span></span>  
  
 <span data-ttu-id="b5997-155">次に一般的な形式を示します。</span><span class="sxs-lookup"><span data-stu-id="b5997-155">This is the general format:</span></span>  
  
```  
  
ElementName!TagNumber!AttributeName!Directive  
```  
  
 <span data-ttu-id="b5997-156">各部分の説明は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b5997-156">Following is the description of the parts of the format.</span></span>  
  
 <span data-ttu-id="b5997-157">*ElementName*</span><span class="sxs-lookup"><span data-stu-id="b5997-157">*ElementName*</span></span>  
 <span data-ttu-id="b5997-158">結果の要素の汎用識別子。</span><span class="sxs-lookup"><span data-stu-id="b5997-158">Is the resulting generic identifier of the element.</span></span> <span data-ttu-id="b5997-159">たとえば、*ElementName* として **Customers** が指定されている場合、\<Customers> 要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-159">For example, if **Customers** is specified as *ElementName*, the \<Customers> element is generated.</span></span>  
  
 <span data-ttu-id="b5997-160">*TagNumber*</span><span class="sxs-lookup"><span data-stu-id="b5997-160">*TagNumber*</span></span>  
 <span data-ttu-id="b5997-161">要素に割り当てられる一意なタグの値。</span><span class="sxs-lookup"><span data-stu-id="b5997-161">Is a unique tag value assigned to an element.</span></span> <span data-ttu-id="b5997-162">この値と **Tag** および **Parent**の 2 つのメタデータ列の組み合わせにより、生成される XML 内の要素の入れ子構造が決定されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-162">This value, with the help of the two metadata columns, **Tag** and **Parent**, determines the nesting of the elements in the resulting XML.</span></span>  
  
 <span data-ttu-id="b5997-163">*AttributeName*</span><span class="sxs-lookup"><span data-stu-id="b5997-163">*AttributeName*</span></span>  
 <span data-ttu-id="b5997-164">指定した *ElementName*要素に作成する属性の名前。</span><span class="sxs-lookup"><span data-stu-id="b5997-164">Provides the name of the attribute to construct in the specified *ElementName*.</span></span> <span data-ttu-id="b5997-165">これは、 *Directive* を指定しない場合の動作です。</span><span class="sxs-lookup"><span data-stu-id="b5997-165">This is the behavior if *Directive* is not specified.</span></span>  
  
 <span data-ttu-id="b5997-166">*Directive* に **xml**、 **cdata**、または **element**のいずれかが指定されている場合、この値は *ElementName*要素の子要素の構築に使用され、列値がその子要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-166">If *Directive* is specified and it is **xml**, **cdata**, or **element**, this value is used to construct an element child of *ElementName*, and the column value is added to it.</span></span>  
  
 <span data-ttu-id="b5997-167">*Directive*を指定した場合、 *AttributeName* は省略できます。</span><span class="sxs-lookup"><span data-stu-id="b5997-167">If you specify the *Directive*, the *AttributeName* can be empty.</span></span> <span data-ttu-id="b5997-168">たとえば、ElementName!TagNumber!!Directive という形式を指定したとします。</span><span class="sxs-lookup"><span data-stu-id="b5997-168">For example, ElementName!TagNumber!!Directive.</span></span> <span data-ttu-id="b5997-169">この場合、列値は、 *ElementName*に直接格納されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-169">In this case, the column value is directly contained by the *ElementName*.</span></span>  
  
 <span data-ttu-id="b5997-170">*Directive*</span><span class="sxs-lookup"><span data-stu-id="b5997-170">*Directive*</span></span>  
 <span data-ttu-id="b5997-171">*Directive* は、XML を生成するための追加情報を指定する場合に使用しますが、省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b5997-171">*Directive* is optional and you can use it to provide additional information for construction of the XML.</span></span> <span data-ttu-id="b5997-172">*Directive* には、2 つの目的があります。</span><span class="sxs-lookup"><span data-stu-id="b5997-172">*Directive* has two purposes.</span></span>  
  
 <span data-ttu-id="b5997-173">1 つ目の目的は、値を ID、IDREF、および IDREFS としてエンコードすることです。</span><span class="sxs-lookup"><span data-stu-id="b5997-173">One of the purposes is to encode values as ID, IDREF, and IDREFS.</span></span> <span data-ttu-id="b5997-174">それには、 **Directives**として、 **ID**、 **IDREF** 、および *IDREFS*キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5997-174">You can specify **ID**, **IDREF**, and **IDREFS** keywords as *Directives*.</span></span> <span data-ttu-id="b5997-175">これらのディレクティブを指定すると、属性の型が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="b5997-175">These directives overwrite the attribute types.</span></span> <span data-ttu-id="b5997-176">これにより、ドキュメント内でのリンクを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b5997-176">This allows you to create intra-document links.</span></span>  
  
 <span data-ttu-id="b5997-177">*Directive* を使用する 2 つ目の目的は、文字列データをどのように XML にマップするかを指定することです。</span><span class="sxs-lookup"><span data-stu-id="b5997-177">Also, you can use *Directive* to indicate how to map the string data to XML.</span></span> <span data-ttu-id="b5997-178">**Directive**としては、 **hide**、 **element、elementxsinil**、 **xml**、 **xmltext** 、 *cdata*の各キーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5997-178">The **hide**, **element, elementxsinil**, **xml**, **xmltext**, and **cdata** keywords can be used as the *Directive*.</span></span> <span data-ttu-id="b5997-179">**hide** ディレクティブを指定した場合は、ノードが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="b5997-179">The **hide** directive hides the node.</span></span> <span data-ttu-id="b5997-180">このディレクティブは、ノードを並べ替えるだけの目的で値を取得し、生成する XML にはその値を表示しない場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b5997-180">This is useful when you retrieve values only for sorting purposes, but you do not want them in the resulting XML.</span></span>  
  
 <span data-ttu-id="b5997-181">**element** ディレクティブを指定すると、属性ではなく子要素 (含まれる要素) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-181">The **element** directive generates a contained element instead of an attribute.</span></span> <span data-ttu-id="b5997-182">含まれる要素のデータは、エンティティとしてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="b5997-182">The contained data is encoded as an entity.</span></span> <span data-ttu-id="b5997-183">たとえば、文字 **<** は &lt;になります。</span><span class="sxs-lookup"><span data-stu-id="b5997-183">For example, the **<** character becomes &lt;.</span></span> <span data-ttu-id="b5997-184">列の値が NULL であれば、要素は生成されません。</span><span class="sxs-lookup"><span data-stu-id="b5997-184">For NULL column values, no element is generated.</span></span> <span data-ttu-id="b5997-185">列の値が NULL である場合にも要素を生成する場合は、 **elementxsinil** ディレクティブを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5997-185">If you want an element generated for null column values, you can specify the **elementxsinil** directive.</span></span> <span data-ttu-id="b5997-186">このディレクティブを指定すると、xsi:nil=TRUE 属性を持つ要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-186">This will generate an element that has the attribute xsi:nil=TRUE.</span></span>  
  
 <span data-ttu-id="b5997-187">**xml** ディレクティブは、 **element** ディレクティブと似ていますが、エンティティのエンコードが行われない点が異なります。</span><span class="sxs-lookup"><span data-stu-id="b5997-187">The **xml** directive is the same as an **element** directive, except that no entity encoding occurs.</span></span> <span data-ttu-id="b5997-188">また、 **element** ディレクティブは **ID**、 **IDREF**、または **IDREFS**と組み合わせて使用できますが、 **xml** ディレクティブは **hide**以外のディレクティブと組み合わせて使用することができない点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="b5997-188">Note that the **element** directive can be combined with **ID**, **IDREF**, or **IDREFS**, whereas the **xml** directive is not allowed with any other directive, except **hide**.</span></span>  
  
 <span data-ttu-id="b5997-189">**cdata** ディレクティブを使用した場合は、データが CDATA セクション内に取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="b5997-189">The **cdata** directive contains the data by wrapping it with a CDATA section.</span></span> <span data-ttu-id="b5997-190">CDATA セクションの内容については、エンティティのエンコードが行われません。</span><span class="sxs-lookup"><span data-stu-id="b5997-190">The content is not entity encoded.</span></span> <span data-ttu-id="b5997-191">元のデータ型は、 **varchar**、 **nvarchar**、 **text**、または **ntext**などのテキスト型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="b5997-191">The original data type must be a text type such as **varchar**, **nvarchar**, **text**, or **ntext**.</span></span> <span data-ttu-id="b5997-192">このディレクティブと組み合わせて使用できるのは、 **hide**ディレクティブだけです。</span><span class="sxs-lookup"><span data-stu-id="b5997-192">This directive can be used only with **hide**.</span></span> <span data-ttu-id="b5997-193">このディレクティブを使用する場合、 *AttributeName* は指定できません。</span><span class="sxs-lookup"><span data-stu-id="b5997-193">When this directive is used, *AttributeName* must not be specified.</span></span>  
  
 <span data-ttu-id="b5997-194">この 2 つのグループ間でディレクティブを組み合わせることは、ほとんどの場合に可能ですが、同じグループ内のディレクティブを組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="b5997-194">Combining directives between these two groups is allowed in most cases, but combining them among themselves is not allowed.</span></span>  
  
 <span data-ttu-id="b5997-195">*Directive* と *AttributeName* が指定されていない場合を考えます。たとえば、 **Customer!1**の場合、 **Customer!1!!element** のように **element**ディレクティブが暗黙的に指定され、列のデータが *ElementName*に格納されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-195">If the *Directive* and the *AttributeName* is not specified, for example, **Customer!1**, an **element** directive is implied, such as **Customer!1!!element**, and column data is contained in the *ElementName*.</span></span>  
  
 <span data-ttu-id="b5997-196">**xmltext** ディレクティブを指定すると、列の内容は 1 つのタグで囲まれ、ドキュメントの残りの部分に統合されます。</span><span class="sxs-lookup"><span data-stu-id="b5997-196">If the **xmltext** directive is specified, the column content is wrapped in a single tag that is integrated with the rest of the document.</span></span> <span data-ttu-id="b5997-197">このディレクティブは、OPENXML によって列に格納されている未使用のオーバーフロー XML データを収集する場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="b5997-197">This directive is useful in fetching overflow, unconsumed, XML data stored in a column by OPENXML.</span></span> <span data-ttu-id="b5997-198">詳細については、「[OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5997-198">For more information, see [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md).</span></span>  
  
 <span data-ttu-id="b5997-199">*AttributeName* を指定した場合、タグ名は指定した名前に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="b5997-199">If *AttributeName* is specified, the tag name is replaced by the specified name.</span></span> <span data-ttu-id="b5997-200">それ以外の場合、属性は囲み要素の現在の属性リストに追加され、内容は囲み要素の内容として先頭に追加されます。このとき、エンティティのエンコードは行われません。</span><span class="sxs-lookup"><span data-stu-id="b5997-200">Otherwise, the attribute is appended to the current list of attributes of the enclosing elements by putting the content at the beginning of the containment without entity encoding.</span></span> <span data-ttu-id="b5997-201">このディレクティブを指定する列は、 **varchar**、 **nvarchar**、 **char**、 **nchar**、 **text**、または **ntext**などのテキスト型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="b5997-201">The column with this directive must be a text type, such as **varchar**, **nvarchar**, **char**, **nchar**, **text**, or **ntext**.</span></span> <span data-ttu-id="b5997-202">このディレクティブと組み合わせて使用できるのは、 **hide**ディレクティブだけです。</span><span class="sxs-lookup"><span data-stu-id="b5997-202">This directive can be used only with **hide**.</span></span> <span data-ttu-id="b5997-203">このディレクティブは、列に格納されているオーバーフロー データを収集する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b5997-203">This directive is useful in fetching overflow data stored in a column.</span></span> <span data-ttu-id="b5997-204">内容が、正しい形式の XML でない場合は、動作が不確定な状態になります。</span><span class="sxs-lookup"><span data-stu-id="b5997-204">If the content is not a well-formed XML, the behavior is undefined.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5997-205">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b5997-205">In This Section</span></span>  
 <span data-ttu-id="b5997-206">次の例では、EXPLICIT モードの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b5997-206">The following examples illustrate the use of EXPLICIT mode.</span></span>  
  
-   [<span data-ttu-id="b5997-207">例: 従業員情報の取得</span><span class="sxs-lookup"><span data-stu-id="b5997-207">Example: Retrieving Employee Information</span></span>](../xml/example-retrieving-employee-information.md)  
  
-   [<span data-ttu-id="b5997-208">例: ELEMENT ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="b5997-208">Example: Specifying the ELEMENT Directive</span></span>](../xml/example-specifying-the-element-directive.md)  
  
-   [<span data-ttu-id="b5997-209">例: ELEMENTXSINIL ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="b5997-209">Example: Specifying the ELEMENTXSINIL Directive</span></span>](../xml/example-specifying-the-elementxsinil-directive.md)  
  
-   [<span data-ttu-id="b5997-210">例: EXPLICIT モードを使用した兄弟の構築</span><span class="sxs-lookup"><span data-stu-id="b5997-210">Example: Constructing Siblings with EXPLICIT Mode</span></span>](../xml/example-constructing-siblings-with-explicit-mode.md)  
  
-   [<span data-ttu-id="b5997-211">例: ID ディレクティブと IDREF ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="b5997-211">Example: Specifying the ID and IDREF Directives</span></span>](../xml/example-specifying-the-id-and-idref-directives.md)  
  
-   [<span data-ttu-id="b5997-212">例: ID ディレクティブと IDREFS ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="b5997-212">Example: Specifying the ID and IDREFS Directives</span></span>](../xml/example-specifying-the-id-and-idrefs-directives.md)  
  
-   [<span data-ttu-id="b5997-213">例: HIDE ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="b5997-213">Example: Specifying the HIDE Directive</span></span>](../xml/example-specifying-the-hide-directive.md)  
  
-   [<span data-ttu-id="b5997-214">例: ELEMENT ディレクティブとエンティティのエンコードの指定</span><span class="sxs-lookup"><span data-stu-id="b5997-214">Example: Specifying the ELEMENT Directive and Entity Encoding</span></span>](../xml/example-specifying-the-element-directive-and-entity-encoding.md)  
  
-   [<span data-ttu-id="b5997-215">例: CDATA ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="b5997-215">Example: Specifying the CDATA Directive</span></span>](../xml/example-specifying-the-cdata-directive.md)  
  
-   [<span data-ttu-id="b5997-216">例: XMLTEXT ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="b5997-216">Example: Specifying the XMLTEXT Directive</span></span>](../xml/example-specifying-the-xmltext-directive.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5997-217">参照</span><span class="sxs-lookup"><span data-stu-id="b5997-217">See Also</span></span>  
 <span data-ttu-id="b5997-218">[FOR XML での RAW モードの使用](../xml/use-raw-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b5997-218">[Use RAW Mode with FOR XML](../xml/use-raw-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="b5997-219">[FOR XML での AUTO モードの使用](../xml/use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b5997-219">[Use AUTO Mode with FOR XML](../xml/use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="b5997-220">[FOR XML での PATH モードの使用](../xml/use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b5997-220">[Use PATH Mode with FOR XML](../xml/use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="b5997-221">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5997-221">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="b5997-222">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b5997-222">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
