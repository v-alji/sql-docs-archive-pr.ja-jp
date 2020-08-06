---
title: 'Sql: max depth | を使用した再帰リレーションシップの深さの指定Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- max-depth annotation
- XPath queries [SQLXML], recursive relationships
- depth in recursive relationships [SQLXML]
- annotated XSD schemas, recursive relationships
- relationships [SQLXML], recursive relationships
- self joins
- recursive relationships [SQLXML]
- recursion [SQLXML]
- sql:max-depth
- recursive joins [SQLXML]
ms.assetid: 0ffdd57d-dc30-44d9-a8a0-f21cadedb327
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e3ccb2de9c7b2ac8f8702b52aa990d755620e46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642007"
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a><span data-ttu-id="f636d-102">sql:max-depth を使用した、再帰リレーションシップの深さの指定</span><span class="sxs-lookup"><span data-stu-id="f636d-102">Specifying Depth in Recursive Relationships by Using sql:max-depth</span></span>
  <span data-ttu-id="f636d-103">リレーショナル データベースでは、テーブルのリレーションシップにそのテーブル自身が含まれることを、再帰リレーションシップと呼びます。</span><span class="sxs-lookup"><span data-stu-id="f636d-103">In relational databases, when a table is involved in a relationship with itself, it is called a recursive relationship.</span></span> <span data-ttu-id="f636d-104">たとえば、監督者と被監督者のリレーションシップでは、従業員の記録を格納するテーブルのリレーションシップに、そのテーブル自身が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f636d-104">For example, in a supervisor-supervisee relationship, a table storing employee records is involved in a relationship with itself.</span></span> <span data-ttu-id="f636d-105">この場合、従業員テーブルはリレーションシップの 1 つの側では監督者となり、別の側では被監督者となります。</span><span class="sxs-lookup"><span data-stu-id="f636d-105">In this case, the employees table plays a role of supervisor on one side of the relationship, and the same table plays a role of supervisee on the other side.</span></span>  
  
 <span data-ttu-id="f636d-106">マッピング スキーマには、要素とその先祖が同じ型の再帰リレーションシップを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f636d-106">Mapping schemas can include recursive relationships where an element and its ancestor are of the same type.</span></span>  
  
## <a name="example-a"></a><span data-ttu-id="f636d-107">例 A</span><span class="sxs-lookup"><span data-stu-id="f636d-107">Example A</span></span>  
 <span data-ttu-id="f636d-108">次のテーブルを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="f636d-108">Consider the following table:</span></span>  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 <span data-ttu-id="f636d-109">このテーブルでは、ReportsTo 列にマネージャーの従業員 ID が格納されています。</span><span class="sxs-lookup"><span data-stu-id="f636d-109">In this table, the ReportsTo column stores the employee ID of the manager.</span></span>  
  
 <span data-ttu-id="f636d-110">ここで従業員の XML 階層を生成して、次のサンプル XML フラグメントに示すように、マネージャーである従業員を階層の一番上に、マネージャーに報告を行う従業員をそれに対応する階層に表示したいとします。</span><span class="sxs-lookup"><span data-stu-id="f636d-110">Assume that you want to generate an XML hierarchy of employees in which the manager employee is at the top of the hierarchy, and in which the employees that report to that manager appear in the corresponding hierarchy as shown in the following sample XML fragment.</span></span> <span data-ttu-id="f636d-111">このフラグメントが示すのは、employee 1 の*再帰ツリー*です。</span><span class="sxs-lookup"><span data-stu-id="f636d-111">What this fragment shows is the *recursive tree* for employee 1.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
     <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
     <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
        <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
          <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
...  
...  
</root>  
```  
  
 <span data-ttu-id="f636d-112">このフラグメントでは、従業員 5 が従業員 4、従業員 4 が従業員 3 に、従業員 3 と 2 は従業員 1 に報告を行います。</span><span class="sxs-lookup"><span data-stu-id="f636d-112">In this fragment, employee 5 reports to employee 4, employee 4 reports to employee 3, and employees 3 and 2 reports to employee 1.</span></span>  
  
 <span data-ttu-id="f636d-113">この結果を生成するには、次の XSD スキーマを使用して、これに対する XPath クエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f636d-113">To produce this result, you can use the following XSD schema and specify an XPath query against it.</span></span> <span data-ttu-id="f636d-114">このスキーマは、 **\<Emp>** user.employeetype 型の要素を記述します。これは、 **\<Emp>** 同じ型の user.employeetype の子要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="f636d-114">The schema describes an **\<Emp>** element of type EmployeeType, consisting of an **\<Emp>** child element of the same type, EmployeeType.</span></span> <span data-ttu-id="f636d-115">これは、要素とその先祖が同じ型の再帰リレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="f636d-115">This is a recursive relationship (the element and its ancestor are of the same type).</span></span> <span data-ttu-id="f636d-116">さらに、スキーマでは、を使用して、 **\<sql:relationship>** スーパーバイザーと被監督者の間の親子リレーションシップを記述します。</span><span class="sxs-lookup"><span data-stu-id="f636d-116">In addition, the schema uses a **\<sql:relationship>** to describe the parent-child relationship between the supervisor and supervisee.</span></span> <span data-ttu-id="f636d-117">この **\<sql:relationship>** 場合、Emp は親と子の両方のテーブルであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f636d-117">Note that in this **\<sql:relationship>**, Emp is both the parent and the child table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="6" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="f636d-118">このリレーションシップは再帰的なので、何らかの方法でスキーマ内の再帰の深さを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f636d-118">Because the relationship is recursive, you need some way to specify the depth of recursion in the schema.</span></span> <span data-ttu-id="f636d-119">指定しない場合、結果は無限再帰となり、従業員から次の従業員へと無限に報告を行うことになります。</span><span class="sxs-lookup"><span data-stu-id="f636d-119">Otherwise, the result will be an endless recursion (employee reporting to employee reporting to employee, and so on).</span></span> <span data-ttu-id="f636d-120">`sql:max-depth` 注釈を使用すと、再帰の深さを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f636d-120">The `sql:max-depth` annotation allows you to specify how deep in the recursion to go.</span></span> <span data-ttu-id="f636d-121">この例の場合、`sql:max-depth` の値を指定するには、その企業の管理階層の深さを知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f636d-121">In this particular example, to specify a value for `sql:max-depth`, you must know how deep the management hierarchy goes in the company.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f636d-122">このスキーマでは `sql:limit-field` 注釈が指定されていますが、`sql:limit-value` 注釈は指定されていません。</span><span class="sxs-lookup"><span data-stu-id="f636d-122">The schema specifies the `sql:limit-field` annotation, but does not specify the `sql:limit-value` annotation.</span></span> <span data-ttu-id="f636d-123">これにより、結果として生成される階層の一番上のノードは、だれにも報告しない従業員だけになります </span><span class="sxs-lookup"><span data-stu-id="f636d-123">This limits the top node in the resulting hierarchy to only those employees who do not report to anyone.</span></span> <span data-ttu-id="f636d-124">(ReportsTo は NULL です)。を指定 `sql:limit-field` しないと `sql:limit-value` (既定値は NULL になります)、注釈はこれを実現します。</span><span class="sxs-lookup"><span data-stu-id="f636d-124">(ReportsTo is NULL.) Specifying `sql:limit-field` and not specifying `sql:limit-value` (which defaults to NULL) annotation accomplishes this.</span></span> <span data-ttu-id="f636d-125">結果の XML に、可能な報告ツリー (テーブル内の各従業員の報告ツリー) をすべて含める場合は、スキーマから `sql:limit-field` 注釈を削除します。</span><span class="sxs-lookup"><span data-stu-id="f636d-125">If you want the resulting XML to include every possible reporting tree (the reporting tree for every employee in the table), remove the `sql:limit-field` annotation from the schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f636d-126">次の手順では、tempdb データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="f636d-126">The following procedure uses the tempdb database.</span></span>  
  
#### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="f636d-127">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="f636d-127">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="f636d-128">仮想ルートが示す tempdb データベースに、Emp という名前のサンプル テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f636d-128">Create a sample table called Emp in the tempdb database to which the virtual root points.</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Emp (  
           EmployeeID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    ```  
  
2.  <span data-ttu-id="f636d-129">次のサンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="f636d-129">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Emp values (1, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Emp values (2, 'Andrew', 'Fuller',1)  
    INSERT INTO Emp values (3, 'Janet', 'Leverling',1)  
    INSERT INTO Emp values (4, 'Margaret', 'Peacock',3)  
    INSERT INTO Emp values (5, 'Steven', 'Devolio',4)  
    INSERT INTO Emp values (6, 'Nancy', 'Buchanan',5)  
    INSERT INTO Emp values (7, 'Michael', 'Suyama',6)  
    ```  
  
3.  <span data-ttu-id="f636d-130">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="f636d-130">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="f636d-131">maxDepth.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="f636d-131">Save the file as maxDepth.xml.</span></span>  
  
4.  <span data-ttu-id="f636d-132">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="f636d-132">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="f636d-133">maxDepth.xml を保存したディレクトリに maxDepthT.xml としてファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="f636d-133">Save the file as maxDepthT.xml in the same directory where you saved maxDepth.xml.</span></span> <span data-ttu-id="f636d-134">このテンプレートのクエリでは、Emp テーブル内のすべての従業員が返されます。</span><span class="sxs-lookup"><span data-stu-id="f636d-134">The query in the template returns all the employees in the Emp table.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="maxDepth.xml">  
        /Emp  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="f636d-135">マッピング スキーマ (maxDepth.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="f636d-135">The directory path specified for the mapping schema (maxDepth.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="f636d-136">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f636d-136">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\maxDepth.xml"  
    ```  
  
5.  <span data-ttu-id="f636d-137">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="f636d-137">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="f636d-138">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f636d-138">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="f636d-139">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f636d-139">This is the result:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
    <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
      <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
        <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
          <Emp FirstName="Nancy" EmployeeID="6" LastName="Buchanan">  
            <Emp FirstName="Michael" EmployeeID="7" LastName="Suyama" />   
          </Emp>  
        </Emp>  
      </Emp>  
    </Emp>  
  </Emp>  
</root>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f636d-140">結果の階層の深さを変更するには、スキーマの `sql:max-depth` 注釈の値を変更し、それぞれの変更の後にもう一度テンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="f636d-140">To produce different depths of hierarchies in the result, change the value of the `sql:max-depth` annotation in the schema and execute the template again after each change.</span></span>  
  
 <span data-ttu-id="f636d-141">前のスキーマでは、すべての **\<Emp>** 要素がまったく同じ属性のセット (**EmployeeID**、 **FirstName**、および**LastName**) を持っていました。</span><span class="sxs-lookup"><span data-stu-id="f636d-141">In the previous schema, all the **\<Emp>** elements had exactly the same set of attributes (**EmployeeID**, **FirstName**, and **LastName**).</span></span> <span data-ttu-id="f636d-142">次のスキーマは、マネージャーに報告するすべての要素に対して追加の**ReportsTo**属性を返すように若干変更されてい **\<Emp>** ます。</span><span class="sxs-lookup"><span data-stu-id="f636d-142">The following schema has been slightly modified to return an additional **ReportsTo** attribute for all the **\<Emp>** elements that report to a manager.</span></span>  
  
 <span data-ttu-id="f636d-143">たとえば、次の XML フラグメントでは、従業員 1 の部下が示されています。</span><span class="sxs-lookup"><span data-stu-id="f636d-143">For example, this XML fragment shows the subordinates of employee 1:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
<Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2"   
       ReportsTo="1" LastName="Fuller" />   
  <Emp FirstName="Janet" EmployeeID="3"   
       ReportsTo="1" LastName="Leverling">  
...  
...  
```  
  
 <span data-ttu-id="f636d-144">変更後のスキーマは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f636d-144">This is the revised schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:documentation>  
      Customer-Order-Order Details Schema  
      Copyright 2000 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"  
                  parent-key="EmployeeID"  
                  child="Emp"  
                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
                   type="EmpType"   
                   sql:relation="Emp"   
                   sql:key-fields="EmployeeID"   
                   sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmpType">  
    <xsd:sequence>  
       <xsd:element name="Emp"   
                    type="EmpType"   
                    sql:relation="Emp"   
                    sql:key-fields="EmployeeID"  
                    sql:relationship="SupervisorSupervisee"  
                    sql:max-depth="6"/>  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:int" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
    <xsd:attribute name="ReportsTo" type="xsd:int" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
## <a name="sqlmax-depth-annotation"></a><span data-ttu-id="f636d-145">sql:max-depth 注釈</span><span class="sxs-lookup"><span data-stu-id="f636d-145">sql:max-depth Annotation</span></span>  
 <span data-ttu-id="f636d-146">再帰リレーションシップで構成されるスキーマでは、スキーマ内に再帰の深さを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f636d-146">In a schema consisting of recursive relationships, the depth of recursion must be explicitly specified in the schema.</span></span> <span data-ttu-id="f636d-147">これは、対応する FOR XML EXPLICIT クエリを正常に作成し、要求された結果を返すために必要です。</span><span class="sxs-lookup"><span data-stu-id="f636d-147">This is required to successfully produce the corresponding FOR XML EXPLICIT query that returns the requested results.</span></span>  
  
 <span data-ttu-id="f636d-148">スキーマで記述されている再帰リレーションシップの再帰の深さを指定するには、スキーマで `sql:max-depth` 注釈を使用します。</span><span class="sxs-lookup"><span data-stu-id="f636d-148">Use the `sql:max-depth` annotation in the schema to specify the depth of recursion in a recursive relationship that is described in the schema.</span></span> <span data-ttu-id="f636d-149">`sql:max-depth` 注釈の値は、再帰の回数を示す正の整数値 (1 ～ 50) です。値 1 を指定した場合は、`sql:max-depth` 注釈が指定されている要素で再帰が停止します。値 2 を指定した場合は、`sql:max-depth` が指定されている要素の次のレベルで再帰が停止します。このように、指定した値に応じたレベルで再帰が停止します。</span><span class="sxs-lookup"><span data-stu-id="f636d-149">The value of the `sql:max-depth` annotation is a positive integer (1 to 50) that indicates the number of recursions:  A value of 1 stops the recursion at the element for which the `sql:max-depth` annotation is specified; a value of 2 stops the recursion at the next level from the element at which `sql:max-depth` is specified; and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f636d-150">基になる実装では、マッピングスキーマに対して指定された XPath クエリは、SELECT...FOR XML EXPLICIT クエリ。</span><span class="sxs-lookup"><span data-stu-id="f636d-150">In the underlying implementation, an XPath query that is specified against a mapping schema is converted to a SELECT ... FOR XML EXPLICIT query.</span></span> <span data-ttu-id="f636d-151">このクエリでは、再帰に有限の深さを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f636d-151">This query requires you to specify a finite depth of recursion.</span></span> <span data-ttu-id="f636d-152">`sql:max-depth` に指定する値が大きいほど、生成される FOR XML EXPLICIT クエリは大きくなります。</span><span class="sxs-lookup"><span data-stu-id="f636d-152">The higher the value that you specify for `sql:max-depth`, the larger the FOR XML EXPLICIT query that is generated.</span></span> <span data-ttu-id="f636d-153">これによって、取得に時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="f636d-153">This might slow the retrieval time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f636d-154">アップデートグラムと XML 一括読み込みでは、max-depth 注釈は無視されます。</span><span class="sxs-lookup"><span data-stu-id="f636d-154">Updategrams and XML Bulk Load ignore the max-depth annotation.</span></span> <span data-ttu-id="f636d-155">つまり、再帰更新や再帰挿入は、max-depth に指定されている値に関係なく行われます。</span><span class="sxs-lookup"><span data-stu-id="f636d-155">This means, recursive updates or insertions will happen regardless of what value you specify for max-depth.</span></span>  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a><span data-ttu-id="f636d-156">複合要素での sql:max-depth の指定</span><span class="sxs-lookup"><span data-stu-id="f636d-156">Specifying sql:max-depth on Complex Elements</span></span>  
 <span data-ttu-id="f636d-157">`sql:max-depth` 注釈は、複合コンテンツを含む要素にも指定できます。</span><span class="sxs-lookup"><span data-stu-id="f636d-157">The `sql:max-depth` annotation can be specified on any complex content element.</span></span>  
  
### <a name="recursive-elements"></a><span data-ttu-id="f636d-158">再帰要素</span><span class="sxs-lookup"><span data-stu-id="f636d-158">Recursive Elements</span></span>  
 <span data-ttu-id="f636d-159">`sql:max-depth` を再帰リレーションシップの親要素と子要素の両方で指定した場合は、親で指定した `sql:max-depth` 注釈が優先されます。</span><span class="sxs-lookup"><span data-stu-id="f636d-159">If `sql:max-depth` is specified on both the parent element and the child element in a recursive relationship, the `sql:max-depth` annotation specified on the parent takes precedence.</span></span> <span data-ttu-id="f636d-160">たとえば次のスキーマでは、親と子の両方の従業員要素に `sql:max-depth` 注釈が指定されています。</span><span class="sxs-lookup"><span data-stu-id="f636d-160">For example, in the following schema, the `sql:max-depth` annotation is specified on both the parent and the child employee elements.</span></span> <span data-ttu-id="f636d-161">この場合、 `sql:max-depth=4` 親要素で指定された **\<Emp>** (スーパーバイザーの役割を果たす) が優先されます。</span><span class="sxs-lookup"><span data-stu-id="f636d-161">In this case, `sql:max-depth=4`, specified on the **\<Emp>** parent element (playing a role of supervisor), takes precedence.</span></span> <span data-ttu-id="f636d-162">`sql:max-depth`子要素で指定された **\<Emp>** (被監督者の役割を果たす) は無視されます。</span><span class="sxs-lookup"><span data-stu-id="f636d-162">The `sql:max-depth` specified on the child **\<Emp>** element (playing a role of supervisee) is ignored.</span></span>  
  
#### <a name="example-b"></a><span data-ttu-id="f636d-163">例 B</span><span class="sxs-lookup"><span data-stu-id="f636d-163">Example B</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo"   
                          sql:max-depth="3" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="2" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="f636d-164">このスキーマをテストするには、このトピックの「サンプル A」に記載されている手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f636d-164">To test this schema, follow the steps provided for Sample A, earlier in this topic.</span></span>  
  
### <a name="nonrecursive-elements"></a><span data-ttu-id="f636d-165">非再帰要素</span><span class="sxs-lookup"><span data-stu-id="f636d-165">Nonrecursive Elements</span></span>  
 <span data-ttu-id="f636d-166">再帰のないスキーマ内の要素に `sql:max-depth` 注釈が指定されている場合、その注釈は無視されます。</span><span class="sxs-lookup"><span data-stu-id="f636d-166">If the `sql:max-depth` annotation is specified on an element in the schema that does not cause any recursion, it is ignored.</span></span> <span data-ttu-id="f636d-167">次のスキーマでは、 **\<Emp>** 要素は子要素で構成されます。子要素は子要素を **\<Constant>** 持ち **\<Emp>** ます。</span><span class="sxs-lookup"><span data-stu-id="f636d-167">In the following schema, an **\<Emp>** element consists of a **\<Constant>** child element, which, in turn, has an **\<Emp>** child element.</span></span>  
  
 <span data-ttu-id="f636d-168">このスキーマでは、 `sql:max-depth` **\<Constant>** **\<Emp>** 親要素と子要素の間に再帰がないため、要素で指定されている注釈は無視され **\<Constant>** ます。</span><span class="sxs-lookup"><span data-stu-id="f636d-168">In this schema, the `sql:max-depth` annotation specified on the **\<Constant>** element is ignored because there is no recursion between the **\<Emp>** parent and the **\<Constant>** child element.</span></span> <span data-ttu-id="f636d-169">ただし、先祖と子の間には再帰があり **\<Emp>** **\<Emp>** ます。</span><span class="sxs-lookup"><span data-stu-id="f636d-169">But there is recursion between the **\<Emp>** ancestor and the **\<Emp>** child.</span></span> <span data-ttu-id="f636d-170">このスキーマでは先祖と子の両方に `sql:max-depth` 注釈が指定されています。</span><span class="sxs-lookup"><span data-stu-id="f636d-170">The schema specifies the `sql:max-depth` annotation on both.</span></span> <span data-ttu-id="f636d-171">そのため、 `sql:max-depth` 先祖 (スーパーバイザーロール内) に指定されている注釈が優先され **\<Emp>** ます。</span><span class="sxs-lookup"><span data-stu-id="f636d-171">Therefore, the `sql:max-depth` annotation that is specified on the ancestor (**\<Emp>** in the supervisor role) takes precedence.</span></span>  
  
#### <a name="example-c"></a><span data-ttu-id="f636d-172">例 C</span><span class="sxs-lookup"><span data-stu-id="f636d-172">Example C</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"   
                  child="Emp"   
                  parent-key="EmployeeID"   
                  child-key="ReportsTo"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
               sql:relation="Emp"   
               type="EmpType"  
               sql:limit-field="ReportsTo"  
               sql:max-depth="1" />  
    <xsd:complexType name="EmpType" >  
      <xsd:sequence>  
       <xsd:element name="Constant"   
                    sql:is-constant="1"   
                    sql:max-depth="20" >  
         <xsd:complexType >  
           <xsd:sequence>  
            <xsd:element name="Emp"   
                         sql:relation="Emp" type="EmpType"  
                         sql:relationship="SupervisorSupervisee"   
                         sql:max-depth="3" />  
         </xsd:sequence>  
         </xsd:complexType>  
         </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="EmployeeID" type="xsd:int" />  
    </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="f636d-173">このスキーマをテストするには、このトピックの例 A の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="f636d-173">To test this schema, follow the steps provided for Example A, earlier in this topic.</span></span>  
  
## <a name="complex-types-derived-by-restriction"></a><span data-ttu-id="f636d-174">制限により派生する複合型</span><span class="sxs-lookup"><span data-stu-id="f636d-174">Complex Types Derived by Restriction</span></span>  
 <span data-ttu-id="f636d-175">による複合型の派生がある場合 **\<restriction>** 、対応する基本複合型の要素で注釈を指定することはできません `sql:max-depth` 。</span><span class="sxs-lookup"><span data-stu-id="f636d-175">If you have a complex type derivation by **\<restriction>**, elements of the corresponding base complex type cannot specify the `sql:max-depth` annotation.</span></span> <span data-ttu-id="f636d-176">このような場合は、派生した型の要素に `sql:max-depth` 注釈を追加できます。</span><span class="sxs-lookup"><span data-stu-id="f636d-176">In these cases, the `sql:max-depth` annotation can be added to the element of the derived type.</span></span>  
  
 <span data-ttu-id="f636d-177">一方、によって複合型を派生させる場合は、 **\<extension>** 対応する基本複合型の要素で注釈を指定でき `sql:max-depth` ます。</span><span class="sxs-lookup"><span data-stu-id="f636d-177">On the other hand, if you have a complex type derivation by **\<extension>**, the elements of the corresponding base complex type can specify the `sql:max-depth` annotation.</span></span>  
  
 <span data-ttu-id="f636d-178">たとえば、次の XSD スキーマでは、基本型に `sql:max-depth` 注釈が指定されているのでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f636d-178">For example, the following XSD schema generates an error because the `sql:max-depth` annotation is specified on the base type.</span></span> <span data-ttu-id="f636d-179">この注釈は、別の型から派生した型ではサポートされていません **\<restriction>** 。</span><span class="sxs-lookup"><span data-stu-id="f636d-179">This annotation is not supported on a type that is derived by **\<restriction>** from another type.</span></span> <span data-ttu-id="f636d-180">この問題を解決するには、スキーマを変更し、派生した型の要素に `sql:max-depth` 注釈を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f636d-180">To fix this problem, you must change the schema and specify the `sql:max-depth` annotation on element in the derived type.</span></span>  
  
#### <a name="example-d"></a><span data-ttu-id="f636d-181">例 D</span><span class="sxs-lookup"><span data-stu-id="f636d-181">Example D</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:complexType name="CustomerBaseType">   
    <xsd:sequence>  
       <xsd:element name="CID" msdata:field="CustomerID" />  
       <xsd:element name="CompanyName"/>  
       <xsd:element name="Customers" msdata:max-depth="3">  
         <xsd:annotation>  
           <xsd:appinfo>  
             <msdata:relationship  
                     parent="Customers"  
                     parent-key="CustomerID"  
                     child-key="CustomerID"  
                     child="Customers" />  
           </xsd:appinfo>  
         </xsd:annotation>  
       </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  <xsd:element name="Customers" type="CustomerType"/>  
  <xsd:complexType name="CustomerType">  
    <xsd:complexContent>  
       <xsd:restriction base="CustomerBaseType">  
          <xsd:sequence>  
            <xsd:element name="CID"   
                         type="xsd:string"/>  
            <xsd:element name="CompanyName"   
                         type="xsd:string"  
                         msdata:field="CName" />  
            <xsd:element name="Customers"   
                         type="CustomerType" />  
          </xsd:sequence>  
       </xsd:restriction>  
    </xsd:complexContent>  
  </xsd:complexType>  
</xsd:schema>   
```  
  
 <span data-ttu-id="f636d-182">このスキーマでは、`sql:max-depth` 複合型に `CustomerBaseType` が指定されています。</span><span class="sxs-lookup"><span data-stu-id="f636d-182">In the schema, `sql:max-depth` is specified on a `CustomerBaseType` complex type.</span></span> <span data-ttu-id="f636d-183">スキーマでは **\<Customer>** 、から派生した型の要素も指定し `CustomerType` `CustomerBaseType` ます。</span><span class="sxs-lookup"><span data-stu-id="f636d-183">The schema also specifies a **\<Customer>** element of type `CustomerType`, which is derived from `CustomerBaseType`.</span></span> <span data-ttu-id="f636d-184">このようなスキーマで指定される XPath クエリでは、制限の基本型で定義されている要素に `sql:max-depth` がサポートされていないので、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f636d-184">An XPath query specified on such a schema will generate an error, because `sql:max-depth` is not supported on an element that is defined in a restriction base type.</span></span>  
  
## <a name="schemas-with-a-deep-hierarchy"></a><span data-ttu-id="f636d-185">深い階層のスキーマ</span><span class="sxs-lookup"><span data-stu-id="f636d-185">Schemas with a Deep Hierarchy</span></span>  
 <span data-ttu-id="f636d-186">要素に子要素が含まれ、その子要素にさらに別の子要素が含まれるというような深い階層のスキーマの場合は、</span><span class="sxs-lookup"><span data-stu-id="f636d-186">You might have a schema that includes a deep hierarchy in which an element contains a child element, which in turn contains another child element, and so on.</span></span> <span data-ttu-id="f636d-187">指定されている `sql:max-depth` 注釈によって生成される XML ドキュメントで、階層が 500 レベルを超えた場合はエラーが返されます。ここでは、最上位要素をレベル 1、その子をレベル 2 と数えます。</span><span class="sxs-lookup"><span data-stu-id="f636d-187">If the `sql:max-depth` annotation specified in such a schema generates an XML document that includes a hierarchy of more than 500 levels (with top-level element at level 1, its child at level 2, and so on), an error is returned.</span></span>  
  
  
