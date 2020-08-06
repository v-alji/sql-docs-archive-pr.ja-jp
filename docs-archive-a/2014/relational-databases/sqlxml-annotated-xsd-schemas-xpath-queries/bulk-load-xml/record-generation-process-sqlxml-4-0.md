---
title: レコード生成プロセス (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], record generation process
- node scopes [SQLXML]
- record subsets [SQLXML]
- scope [SQLXML]
- key ordering rules [SQLXML]
- record generation process for bulk loads [SQLXML]
- entering node scope [SQLXML]
- bulk load [SQLXML], record generation process
- leaving node scope [SQLXML]
- schema mapping [SQLXML]
ms.assetid: d8885bbe-6f15-4fb9-9684-ca7883cfe9ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 5734776864aecbda7adaf0b9b16180b5ebd55ce3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711818"
---
# <a name="record-generation-process-sqlxml-40"></a><span data-ttu-id="51240-102">レコードの生成処理 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="51240-102">Record Generation Process (SQLXML 4.0)</span></span>
  <span data-ttu-id="51240-103">XML 一括読み込みでは、XML 入力データが処理され、Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の適切なテーブルに格納するレコードが用意されます。</span><span class="sxs-lookup"><span data-stu-id="51240-103">XML Bulk Load processes the XML input data and prepares records for the appropriate tables in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="51240-104">XML 一括読み込みのロジックでは、新しいレコードを生成するタイミングと、レコードのフィールドにコピーする子要素および属性値が決定され、完成したレコードを挿入のため [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信するタイミングが判断されます。</span><span class="sxs-lookup"><span data-stu-id="51240-104">The logic in XML Bulk Load determines when to generate a new record, what child element or attribute values to copy into the fields of the record, and when the record is complete and ready to be sent to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="51240-105">XML 一括読み込みでは、すべての XML 入力データがメモリに読み込まれるわけではなく、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にデータが送信される前に完全なレコード セットが作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="51240-105">XML Bulk Load does not load the entire XML input data into memory, and does not produce complete record sets before sending data to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="51240-106">これは、XML 入力データが大きなドキュメントの場合に、ドキュメント全体をメモリに読み込むと時間がかかる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="51240-106">This is because XML input data can be a large document and loading the entire document in memory can be expensive.</span></span> <span data-ttu-id="51240-107">代わりに、XML 一括読み込みでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="51240-107">Instead, XML Bulk Load does the following:</span></span>  
  
1.  <span data-ttu-id="51240-108">マッピング スキーマを分析し、必要な実行プランを準備する。</span><span class="sxs-lookup"><span data-stu-id="51240-108">Analyzes the mapping schema and prepares the necessary execution plan.</span></span>  
  
2.  <span data-ttu-id="51240-109">実行プランを入力ストリームのデータに適用する。</span><span class="sxs-lookup"><span data-stu-id="51240-109">Applies the execution plan to the data in the input stream.</span></span>  
  
 <span data-ttu-id="51240-110">この順次処理では、決まった方法で XML 入力データを指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="51240-110">This sequential processing makes it important to provide the XML input data in a specific way.</span></span> <span data-ttu-id="51240-111">また、XML 一括読み込みでマッピング スキーマがどのように分析されるかと、レコード生成処理がどのように行われるかについて理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="51240-111">You must understand how XML Bulk Load analyzes the mapping schema and how the record generation process occurs.</span></span> <span data-ttu-id="51240-112">これらを理解しておくと、XML 一括読み込みに対し、必要な結果を生成するマッピング スキーマを指定できます。</span><span class="sxs-lookup"><span data-stu-id="51240-112">With this understanding, you can provide a mapping schema to XML Bulk Load that produces the results you want.</span></span>  
  
 <span data-ttu-id="51240-113">XML 一括読み込みでは、注釈により明示的に、または既定のマッピングにより暗黙的に行われる列とテーブルのマッピングを含む一般的なマッピング スキーマ注釈、および結合リレーションシップが処理されます。</span><span class="sxs-lookup"><span data-stu-id="51240-113">XML Bulk Load handles common mapping schema annotations, including column and table mappings (specified explicitly by using annotations or implicitly through the default mapping), and join relationships.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51240-114">注釈付き XSD または XDR マッピング スキーマについて理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="51240-114">It is assumed that you are familiar with annotated XSD or XDR mapping schemas.</span></span> <span data-ttu-id="51240-115">スキーマの詳細については、「sqlxml 4.0&#41;または[注釈付き XDR&#41;4.0 &#40;スキーマ](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md) [&#40;の注釈付き XSD スキーマの概要](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51240-115">For more information about schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) or [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="51240-116">レコード生成を理解するには、次の概念を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51240-116">Understanding record generation requires understanding the following concepts:</span></span>  
  
-   <span data-ttu-id="51240-117">ノードのスコープ</span><span class="sxs-lookup"><span data-stu-id="51240-117">Scope of a node</span></span>  
  
-   <span data-ttu-id="51240-118">レコード生成の規則</span><span class="sxs-lookup"><span data-stu-id="51240-118">Record Generation Rule</span></span>  
  
-   <span data-ttu-id="51240-119">レコードのサブセットとキーの順序付け規則</span><span class="sxs-lookup"><span data-stu-id="51240-119">Record subset and the Key Ordering Rule</span></span>  
  
-   <span data-ttu-id="51240-120">レコード生成の規則の例外</span><span class="sxs-lookup"><span data-stu-id="51240-120">Exceptions to the Record Generation Rule</span></span>  
  
## <a name="scope-of-a-node"></a><span data-ttu-id="51240-121">ノードのスコープ</span><span class="sxs-lookup"><span data-stu-id="51240-121">Scope of a Node</span></span>  
 <span data-ttu-id="51240-122">Xml ドキュメント内のノード (要素または属性) は、xml 一括読み込みで xml 入力データストリームで検出されたときに*スコープ内に*入ります。</span><span class="sxs-lookup"><span data-stu-id="51240-122">A node (an element or an attribute) in an XML document enters *into scope* when XML Bulk Load encounters it in the XML input data stream.</span></span> <span data-ttu-id="51240-123">要素ノードの場合、要素はその開始タグが現れた時点でスコープ内に入ります。</span><span class="sxs-lookup"><span data-stu-id="51240-123">For an element node, the start tag of the element brings the element in scope.</span></span> <span data-ttu-id="51240-124">属性ノードの場合、属性はその名前が現れた時点でスコープ内に入ります。</span><span class="sxs-lookup"><span data-stu-id="51240-124">For an attribute node, the attribute name brings the attribute in scope.</span></span>  
  
 <span data-ttu-id="51240-125">要素ノードの場合は終了タグ、属性ノードの場合は属性値の最後に達し、ノードのデータがなくなると、ノードはスコープ外に出ます。</span><span class="sxs-lookup"><span data-stu-id="51240-125">A node leaves scope when there is no more data for it: either at the end tag (in the case of an element node) or at the end of an attribute value (in the case of an attribute node).</span></span>  
  
## <a name="record-generation-rule"></a><span data-ttu-id="51240-126">レコード生成の規則</span><span class="sxs-lookup"><span data-stu-id="51240-126">Record Generation Rule</span></span>  
 <span data-ttu-id="51240-127">ノード (要素または属性) がスコープ内に入ると、そのノードからレコードを生成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="51240-127">When a node (element or attribute) enters into scope, there is a potential for generating a record from that node.</span></span> <span data-ttu-id="51240-128">レコードは、関連付けられたノードがスコープ内にある間、存在します。</span><span class="sxs-lookup"><span data-stu-id="51240-128">The record lives as long as the associated node is in scope.</span></span> <span data-ttu-id="51240-129">ノードがスコープ外に出ると、XML 一括読み込みでは生成されたレコードへのデータの格納が完了したと判断され、レコードが挿入のために [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。</span><span class="sxs-lookup"><span data-stu-id="51240-129">When the node goes out of scope, XML Bulk Load considers the generated record complete (with data) and sends it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="51240-130">たとえば、次の XSD スキーマ フラグメントを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="51240-130">For example, consider the following XSD schema fragment:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Customers" >  
   <xsd:complexType>  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
     <xsd:attribute name="CompanyName" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="51240-131">このスキーマでは、 **\<Customer>** **CustomerID**属性と**CompanyName**属性を持つ要素が指定されています。</span><span class="sxs-lookup"><span data-stu-id="51240-131">The schema specifies a **\<Customer>** element with **CustomerID** and **CompanyName** attributes.</span></span> <span data-ttu-id="51240-132">注釈は、 `sql:relation` **\<Customer>** 要素を Customers テーブルにマップします。</span><span class="sxs-lookup"><span data-stu-id="51240-132">The `sql:relation` annotation maps the **\<Customer>** element to the Customers table.</span></span>  
  
 <span data-ttu-id="51240-133">次の XML ドキュメントの一部を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="51240-133">Consider this fragment of an XML document:</span></span>  
  
```  
<Customer CustomerID="1" CompanyName="xyz" />  
<Customer CustomerID="2" CompanyName="abc" />  
...  
```  
  
 <span data-ttu-id="51240-134">XML 一括読み込みで、入力用に前の段落で説明したスキーマと XML データが指定された場合、ソース データのノード (要素と属性) は次のように処理されます。</span><span class="sxs-lookup"><span data-stu-id="51240-134">When XML Bulk Load is provided with the schema described in the preceding paragraphs and XML data as input, it processes the nodes (elements and attributes) in the source data as follows:</span></span>  
  
-   <span data-ttu-id="51240-135">最初の要素の開始タグによっ **\<Customer>** て、その要素がスコープ内に取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="51240-135">The start tag of the first **\<Customer>** element brings that element in scope.</span></span> <span data-ttu-id="51240-136">このノードは Customers テーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="51240-136">This node maps to the Customers table.</span></span> <span data-ttu-id="51240-137">したがって、XML 一括読み込みでは Customers テーブルのレコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="51240-137">Therefore, XML Bulk Load generates a record for the Customers table.</span></span>  
  
-   <span data-ttu-id="51240-138">スキーマでは、要素のすべての属性が **\<Customer>** Customers テーブルの列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="51240-138">In the schema, all attributes of the **\<Customer>** element map to columns of the Customers table.</span></span> <span data-ttu-id="51240-139">これらの属性がスコープ内に入ると、XML 一括読み込みでは、これらの値が親スコープで生成された顧客レコードにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="51240-139">As these attributes enter into scope, XML Bulk Load copies their values to the customer record that is already generated by the parent scope.</span></span>  
  
-   <span data-ttu-id="51240-140">XML 一括読み込みが要素の終了タグに達すると **\<Customer>** 、要素はスコープ外になります。</span><span class="sxs-lookup"><span data-stu-id="51240-140">When XML Bulk Load reaches the end tag for the **\<Customer>** element, the element goes out of scope.</span></span> <span data-ttu-id="51240-141">この時点で、XML 一括読み込みではレコードの準備が完了したと判断され、レコードが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。</span><span class="sxs-lookup"><span data-stu-id="51240-141">This causes XML Bulk Load to consider the record complete and send it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="51240-142">XML 一括読み込みでは、後続の各要素に対してこのプロセスを実行 **\<Customer>** します。</span><span class="sxs-lookup"><span data-stu-id="51240-142">XML Bulk Load follows this process for each subsequent **\<Customer>** element.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51240-143">このモデルでは、終了タグに達した (ノードがスコープ外に出た) ときにレコードが挿入されるため、レコードに関連付けるすべてのデータをノードのスコープ内に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51240-143">In this model, because a record is inserted when the end tag is reached (or the node is out of scope), you must define all of the data that is associated with the record within the scope of the node.</span></span>  
  
## <a name="record-subset-and-the-key-ordering-rule"></a><span data-ttu-id="51240-144">レコードのサブセットとキーの順序付け規則</span><span class="sxs-lookup"><span data-stu-id="51240-144">Record Subset and the Key Ordering Rule</span></span>  
 <span data-ttu-id="51240-145">`<sql:relationship>` を使用するマッピング スキーマを指定する場合、サブセットとは、リレーションシップの外部側で生成されたレコード セットを指します。</span><span class="sxs-lookup"><span data-stu-id="51240-145">When you specify a mapping schema that uses `<sql:relationship>`, the subset term refers to the set of records that is generated on the foreign side of the relationship.</span></span> <span data-ttu-id="51240-146">次の例では、CustOrder レコードが `<sql:relationship>` の外部側になります。</span><span class="sxs-lookup"><span data-stu-id="51240-146">In the following example, the CustOrder records are on the foreign side, `<sql:relationship>`.</span></span>  
  
 <span data-ttu-id="51240-147">たとえば、データベースに次のテーブルが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="51240-147">For example, suppose a database contains the following tables:</span></span>  
  
-   <span data-ttu-id="51240-148">Cust (CustomerID、CompanyName、City)</span><span class="sxs-lookup"><span data-stu-id="51240-148">Cust (CustomerID, CompanyName, City)</span></span>  
  
-   <span data-ttu-id="51240-149">CustOrder (CustomerID、OrderID)</span><span class="sxs-lookup"><span data-stu-id="51240-149">CustOrder (CustomerID, OrderID)</span></span>  
  
 <span data-ttu-id="51240-150">CustOrder テーブルの CustomerID は、Cust テーブルの CustomerID 主キーを参照する外部キーです。</span><span class="sxs-lookup"><span data-stu-id="51240-150">The CustomerID in the CustOrder table is a foreign key that refers to the CustomerID primary key in the Cust table.</span></span>  
  
 <span data-ttu-id="51240-151">ここで、次の注釈付き XSD スキーマで指定される XML ビューを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="51240-151">Now, consider the XML view as specified in the following annotated XSD schema.</span></span> <span data-ttu-id="51240-152">このスキーマでは、`<sql:relationship>` によって、Cust テーブルと CustOrder テーブルの間のリレーションシップが指定されています。</span><span class="sxs-lookup"><span data-stu-id="51240-152">This schema uses `<sql:relationship>` to specify the relationship between the Cust and CustOrder tables.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="51240-153">サンプル XML データと、実際のサンプルを作成する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="51240-153">The sample XML data and the steps to create a working sample are given below.</span></span>  
  
-   <span data-ttu-id="51240-154">**\<Customer>** Xml データファイル内の要素ノードがスコープ内に入ると、Xml 一括読み込みでは Cust テーブルのレコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="51240-154">When a **\<Customer>** element node in the XML data file enters into scope, XML Bulk Load generates a record for the Cust table.</span></span> <span data-ttu-id="51240-155">次に、XML 一括読み込みで、、、および子要素から必要な列値 (CustomerID、CompanyName、および City) がコピーされ、 **\<CustomerID>** **\<CompanyName>** これらの要素が **\<City>** スコープ内に入ります。</span><span class="sxs-lookup"><span data-stu-id="51240-155">XML Bulk Load then copies the necessary column values (CustomerID, CompanyName, and City) from the **\<CustomerID>**, **\<CompanyName>**, and the **\<City>** child elements as these elements enter into scope.</span></span>  
  
-   <span data-ttu-id="51240-156">**\<Order>** 要素ノードがスコープ内に入ると、XML 一括読み込みでは CustOrder テーブルのレコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="51240-156">When an **\<Order>** element node enters into scope, XML Bulk Load generates a record for the CustOrder table.</span></span> <span data-ttu-id="51240-157">XML 一括読み込みでは、 **OrderID**属性の値がこのレコードにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="51240-157">XML Bulk Load copies the value of the **OrderID** attribute to this record.</span></span> <span data-ttu-id="51240-158">CustomerID 列に必要な値は、 **\<CustomerID>** 要素の子要素から取得され **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="51240-158">The value required for the CustomerID column is obtained from the **\<CustomerID>** child element of the **\<Customer>** element.</span></span> <span data-ttu-id="51240-159">XML 一括読み込みでは、 `<sql:relationship>` 要素で**customerid**属性が指定されていない限り、で指定された情報を使用して、このレコードの customerid 外部キー値を取得し **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="51240-159">XML Bulk Load uses the information that is specified in `<sql:relationship>` to obtain the CustomerID foreign key value for this record, unless the **CustomerID** attribute was specified in the **\<Order>** element.</span></span> <span data-ttu-id="51240-160">一般的な規則としては、子要素で外部キー属性の値が明示的に指定されている場合、XML 一括読み込みではその値が使用され、指定された `<sql:relationship>` によって親要素から値が取得されることはありません。</span><span class="sxs-lookup"><span data-stu-id="51240-160">The general rule is that if the child element explicitly specifies a value for the foreign key attribute, XML Bulk Load uses that value and does not obtain the value from the parent element by using the specified `<sql:relationship>`.</span></span> <span data-ttu-id="51240-161">この **\<Order>** 要素ノードがスコープ外に出ると、XML 一括読み込みではレコードがに送信され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 後続のすべての **\<Order>** 要素ノードが同じ方法で処理されます。</span><span class="sxs-lookup"><span data-stu-id="51240-161">As this **\<Order>** element node goes out of scope, XML Bulk Load sends the record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and then processes all the subsequent **\<Order>** element nodes in the same manner.</span></span>  
  
-   <span data-ttu-id="51240-162">最後に、 **\<Customer>** 要素ノードがスコープ外に移動します。</span><span class="sxs-lookup"><span data-stu-id="51240-162">Finally, the **\<Customer>** element node goes out of scope.</span></span> <span data-ttu-id="51240-163">XML 一括読み込みで顧客レコードが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。</span><span class="sxs-lookup"><span data-stu-id="51240-163">At that time, XML Bulk Load sends the customer record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="51240-164">XML 一括読み込みでは、XML データ ストリームの後続の顧客すべてについて、この処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="51240-164">XML Bulk Load follows this process for all the subsequent customers in the XML data stream.</span></span>  
  
 <span data-ttu-id="51240-165">マッピング スキーマに関しては、次の 2 つの点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="51240-165">Here are two observations about the mapping schema:</span></span>  
  
-   <span data-ttu-id="51240-166">スキーマが "含有" 規則を満たす場合 (たとえば、顧客と注文に関連付けられているすべてのデータが、関連付けられているノードと要素ノードのスコープ内で定義されている場合 **\<Customer>** **\<Order>** )、一括読み込みは成功します。</span><span class="sxs-lookup"><span data-stu-id="51240-166">When the schema satisfies the "containment" rule (for example, all data that is associated with the customer and the order is defined within the scope of the associated **\<Customer>** and **\<Order>** element nodes), the bulk load succeeds.</span></span>  
  
-   <span data-ttu-id="51240-167">要素の記述では、 **\<Customer>** その子要素が適切な順序で指定されます。</span><span class="sxs-lookup"><span data-stu-id="51240-167">In describing the **\<Customer>** element, its child elements are specified in the appropriate order.</span></span> <span data-ttu-id="51240-168">この場合、子要素は **\<CustomerID>** 子要素の前に指定され **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="51240-168">In this case, the **\<CustomerID>** child element is specified before the **\<Order>** child element.</span></span> <span data-ttu-id="51240-169">つまり、入力 XML データファイルでは、要素が **\<CustomerID>** スコープ内に入るときに、要素値を外部キー値として使用でき **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="51240-169">This means that in the input XML data file, the **\<CustomerID>** element value is available as the foreign key value when the **\<Order>** element enters into scope.</span></span> <span data-ttu-id="51240-170">キー属性は最初に指定されます。これを "キーの順序付け規則" といいます。</span><span class="sxs-lookup"><span data-stu-id="51240-170">The key attributes are specified first; this is the "Key Ordering Rule."</span></span>  
  
     <span data-ttu-id="51240-171">子要素の後に子要素を指定した場合 **\<CustomerID>** **\<Order>** 、 **\<Order>** 要素がスコープ内に入るときに値は使用できません。</span><span class="sxs-lookup"><span data-stu-id="51240-171">If you specify the **\<CustomerID>** child element after the **\<Order>** child element, the value is not available when the **\<Order>** element enters into scope.</span></span> <span data-ttu-id="51240-172">**\</Order>** 終了タグが読み取られると、custorder テーブルのレコードは完了したと見なされ、custorder テーブルに挿入されます。このテーブルには、CustomerID 列に NULL 値が挿入されます。これは目的の結果ではありません。</span><span class="sxs-lookup"><span data-stu-id="51240-172">When the **\</Order>** end tag is then read, the record for CustOrder table is considered complete and is inserted in the CustOrder table with a NULL value for the CustomerID column, which is not the desired result.</span></span>  
  
#### <a name="to-create-a-working-sample"></a><span data-ttu-id="51240-173">実際のサンプルを作成するには</span><span class="sxs-lookup"><span data-stu-id="51240-173">To create a working sample</span></span>  
  
1.  <span data-ttu-id="51240-174">この例のスキーマを SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="51240-174">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="51240-175">次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="51240-175">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                 OrderID        int         PRIMARY KEY,  
                 CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
3.  <span data-ttu-id="51240-176">次のサンプル XML 入力データを SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="51240-176">Save the following sample XML input data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>   
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
        <City>LA</City>  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="51240-177">XML 一括読み込みを実行するには、次の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) の例 (BulkLoad.vbs) を保存し、実行します。</span><span class="sxs-lookup"><span data-stu-id="51240-177">To execute XML Bulk Load, save and execute the following [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example (BulkLoad.vbs):</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
## <a name="exceptions-to-the-record-generation-rule"></a><span data-ttu-id="51240-178">レコード生成の規則の例外</span><span class="sxs-lookup"><span data-stu-id="51240-178">Exceptions to the Record Generation Rule</span></span>  
 <span data-ttu-id="51240-179">XML 一括読み込みでは、IDREF または IDREFS 型のノードがスコープ内に入っても、ノードのレコードは生成されません。</span><span class="sxs-lookup"><span data-stu-id="51240-179">XML Bulk Load does not generate a record for a node when it enters into scope if that node is either an IDREF or IDREFS type.</span></span> <span data-ttu-id="51240-180">スキーマのどこかで、レコードを完全に記述するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="51240-180">You must make sure that a complete description of the record occurs at some place in the schema.</span></span> <span data-ttu-id="51240-181">IDREFS 型が無視されるのと同様に、`dt:type="nmtokens"` 注釈は無視されます。</span><span class="sxs-lookup"><span data-stu-id="51240-181">The `dt:type="nmtokens"` annotations are ignored just as the IDREFS type is ignored.</span></span>  
  
 <span data-ttu-id="51240-182">たとえば、要素と要素を記述する次の XSD スキーマについて考えてみ **\<Customer>** **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="51240-182">For example, consider the following XSD schema that describes **\<Customer>** and **\<Order>** elements.</span></span> <span data-ttu-id="51240-183">要素には、 **\<Customer>** IDREFS 型の**orderlist**属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="51240-183">The **\<Customer>** element includes an **OrderList** attribute of the IDREFS type.</span></span> <span data-ttu-id="51240-184">`<sql:relationship>` タグでは、顧客と注文リストの間の一対多のリレーションシップが指定されています。</span><span class="sxs-lookup"><span data-stu-id="51240-184">The `<sql:relationship>` tag specifies the one-to-many relationship between the customer and list of orders.</span></span>  
  
 <span data-ttu-id="51240-185">スキーマは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="51240-185">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
                 parent="Cust"  
                 parent-key="CustomerID"  
                 child="CustOrder"  
                 child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="CompanyName" type="xsd:string" />  
    <xsd:attribute name="City" type="xsd:string" />  
    <xsd:attribute name="OrderList"   
                       type="xsd:IDREFS"   
                       sql:relation="CustOrder"   
                       sql:field="OrderID"  
                       sql:relationship="CustCustOrder" >  
    </xsd:attribute>  
  </xsd:complexType>  
 </xsd:element>  
  
  <xsd:element name="Order" sql:relation="CustOrder" >  
   <xsd:complexType>  
    <xsd:attribute name="OrderID" type="xsd:string" />  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="OrderDate" type="xsd:date" />  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="51240-186">一括読み込みでは IDREFS 型のノードが無視されるため、 **Orderlist**属性ノードがスコープ内に入ってもレコードは生成されません。</span><span class="sxs-lookup"><span data-stu-id="51240-186">Because Bulk Load ignores the nodes of IDREFS type, there is no record generation when the **OrderList** attribute node enters into scope.</span></span> <span data-ttu-id="51240-187">このため、注文レコードを Orders テーブルに追加したい場合は、スキーマ内のどこかでこれらの注文を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51240-187">Therefore, if you want the order records added to the Orders table, you must describe those orders somewhere in the schema.</span></span> <span data-ttu-id="51240-188">このスキーマでは、要素を指定することで、 **\<Order>** XML 一括読み込みで Orders テーブルに注文レコードが追加されるようになります。</span><span class="sxs-lookup"><span data-stu-id="51240-188">In this schema, specifying the **\<Order>** element ensures that XML Bulk Load adds the order records to the Orders table.</span></span> <span data-ttu-id="51240-189">要素には、 **\<Order>** CustOrder テーブルのレコードを埋めるために必要なすべての属性が記述されています。</span><span class="sxs-lookup"><span data-stu-id="51240-189">The **\<Order>** element describes all the attributes that are required to fill the record for the CustOrder table.</span></span>  
  
 <span data-ttu-id="51240-190">要素の**CustomerID**と**OrderID**の値が要素の値と一致していることを確認する必要があり **\<Customer>** **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="51240-190">You must ensure that the **CustomerID** and **OrderID** values in the **\<Customer>** element match the values in the **\<Order>** element.</span></span> <span data-ttu-id="51240-191">参照の整合性は必ず維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51240-191">You are responsible for maintaining referential integrity.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="51240-192">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="51240-192">To test a working sample</span></span>  
  
1.  <span data-ttu-id="51240-193">次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="51240-193">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
                  CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
                  CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID),  
                  OrderDate      datetime DEFAULT '2000-01-01')  
    GO  
    ```  
  
2.  <span data-ttu-id="51240-194">この例のマッピング スキーマを SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="51240-194">Save the mapping schema provided in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="51240-195">次のサンプル XML データを SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="51240-195">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai" City="NY"  
                 OrderList="Ord1 Ord2" />  
      <Customers CustomerID="1112" CompanyName="Dont Know" City="LA"  
                 OrderList="Ord3 Ord4" />  
      <Order OrderID="Ord1" CustomerID="1111" OrderDate="1999-01-01" />  
      <Order OrderID="Ord2" CustomerID="1111" OrderDate="1999-02-01" />  
      <Order OrderID="Ord3" CustomerID="1112" OrderDate="1999-03-01" />  
      <Order OrderID="Ord4" CustomerID="1112" OrderDate="1999-04-01" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="51240-196">XML 一括読み込みを実行するには、次の VBScript の例 (SampleVB.vbs) を保存し実行します。</span><span class="sxs-lookup"><span data-stu-id="51240-196">To execute XML Bulk Load, save and execute this VBScript example (SampleVB.vbs):</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
