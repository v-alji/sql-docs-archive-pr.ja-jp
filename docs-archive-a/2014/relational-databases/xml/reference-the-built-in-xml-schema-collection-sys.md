---
title: 組み込みの XML スキーマ コレクション (sys) の参照 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- sys XML schema collections [SQL Server]
- schema collections [SQL Server], predefined
- predefined XML schema collections [SQL Server]
- XML schema collections [SQL Server], predefined
- built-in XML schema collections [SQL Server]
ms.assetid: 1e118303-5df0-4ee4-bd8d-14ced7544144
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fa30107e1746b33e3f9b8eb1cfa53d1f4d25fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713922"
---
# <a name="reference-the-built-in-xml-schema-collection-sys"></a><span data-ttu-id="77e59-102">組み込みの XML スキーマ コレクション (sys) の参照</span><span class="sxs-lookup"><span data-stu-id="77e59-102">Reference the Built-in XML Schema Collection (sys)</span></span>
  <span data-ttu-id="77e59-103">作成したどのデータベースでも、 **sys** リレーショナル スキーマに **sys** XML スキーマ コレクションが事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="77e59-103">Every database you create has a predefined **sys** XML schema collection in the **sys** relational schema.</span></span> <span data-ttu-id="77e59-104">各データベースはこれらの事前定義されたスキーマを保持します。また、これらのスキーマは、ユーザーが作成した他の XML スキーマ コレクションからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="77e59-104">It reserves these predefined schemas, and they can be accessed from any other user-created XML schema collection.</span></span> <span data-ttu-id="77e59-105">このような事前定義されたスキーマに使われているプレフィックスは、XQuery で意味があるものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="77e59-105">The prefixes used in these predefined schemas are meaningful in XQuery.</span></span> <span data-ttu-id="77e59-106">**xml** のみが、予約されているプレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="77e59-106">Only **xml** is a reserved prefix.</span></span>  
  
```  
xml = http://www.w3.org/XML/1998/namespace  
xs = http://www.w3.org/2001/XMLSchema  
xsi = http://www.w3.org/2001/XMLSchema-instance  
fn = http://www.w3.org/2004/07/xpath-functions  
sqltypes = https://schemas.microsoft.com/sqlserver/2004/sqltypes  
xdt = http://www.w3.org/2004/07/xpath-datatypes  
(no prefix) = urn:schemas-microsoft-com:xml-sql  
(no prefix) = https://schemas.microsoft.com/sqlserver/2004/SOAP  
```  
  
 <span data-ttu-id="77e59-107">**sqltypes** 名前空間には、ユーザーが作成したどの XML スキーマ コレクションからでも参照できるコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="77e59-107">Note that the **sqltypes** namespace contains components that can be referenced from any user-created XML schema collection.</span></span> <span data-ttu-id="77e59-108">**sqltypes** スキーマは、 [Microsoft Web サイト](https://go.microsoft.com/fwlink/?linkid=31850)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="77e59-108">You can download the **sqltypes** schema from this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=31850).</span></span> <span data-ttu-id="77e59-109">組み込みのコンポーネントには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="77e59-109">The built-in components include the following:</span></span>  
  
-   <span data-ttu-id="77e59-110">XSD 型</span><span class="sxs-lookup"><span data-stu-id="77e59-110">XSD types</span></span>  
  
-   <span data-ttu-id="77e59-111">XML 属性 **lang**、 **base**、および **space**</span><span class="sxs-lookup"><span data-stu-id="77e59-111">XML attributes **lang**, **base**, and **space**</span></span>  
  
-   <span data-ttu-id="77e59-112">**sqltypes** 名前空間のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="77e59-112">Components of the **sqltypes** namespace</span></span>  
  
 <span data-ttu-id="77e59-113">次のクエリは、ユーザーが作成した XML スキーマ コレクションから参照できる組み込みのコンポーネントを返します。</span><span class="sxs-lookup"><span data-stu-id="77e59-113">The following query returns built-in components that can be referenced from a user-created XML schema collection:</span></span>  
  
```  
SELECT C.name, N.name, C.symbol_space_desc from sys.xml_schema_components C join sys.xml_schema_namespaces N  
on ((C.xml_namespace_id = N.xml_namespace_id) AND (C.xml_collection_id = N.xml_collection_id))  
join sys.xml_schema_collections SC  
on SC.xml_collection_id = C.xml_collection_id  
where ((C.xml_collection_id = 1) AND (C.name is not null) AND (C.scoping_xml_component_id is null)   
AND (SC.schema_id = 4))  
GO  
```  
  
 <span data-ttu-id="77e59-114">次の例は、これらのコンポーネントをユーザー スキーマで参照する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="77e59-114">The following example shows how these components are referenced in a user schema.</span></span> <span data-ttu-id="77e59-115">`CREATE XML SCHEMA COLLECTION` は、 `varchar` 名前空間で定義されている `sqltypes` 型を参照する XML スキーマ コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="77e59-115">`CREATE XML SCHEMA COLLECTION` creates an XML schema collection that references the `varchar` type defined in the `sqltypes` namespace.</span></span> <span data-ttu-id="77e59-116">この例では、 `lang` 名前空間で定義されている `xml` 属性も参照します。</span><span class="sxs-lookup"><span data-stu-id="77e59-116">The example also references the `lang` attribute that is defined in the `xml` namespace.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema   
   xmlns="http://www.w3.org/2001/XMLSchema"   
   targetNamespace="myNS"  
   xmlns:ns="myNS"  
   xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes" >   
   <import namespace="http://www.w3.org/XML/1998/namespace"/>  
   <import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
   <element name="root">  
      <complexType>  
          <sequence>  
             <element name="a" type="string"/>  
             <element name="b" type="string"/>  
             <!-- varchar type is defined in the sys.sys collection and   
                  can be referenced in any user-defined schema -->  
             <element name="c" type="s:varchar"/>  
          </sequence>  
          <attribute name="att" type="int"/>  
          <!-- xml:lang attribute is defined in the sys.sys collection   
               and can be referenced in any user-defined schema -->  
          <attribute ref="xml:lang"/>  
      </complexType>  
    </element>  
 </schema>'  
GO  
 -- Cleanup  
DROP xml schema collection SC   
GO  
```  
  
 <span data-ttu-id="77e59-117">注意点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="77e59-117">You should note the following:</span></span>  
  
-   <span data-ttu-id="77e59-118">ユーザー定義の XML スキーマ コレクションで、これらの名前空間の XML スキーマを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="77e59-118">You cannot modify XML schemas with these namespaces in any user-defined XML schema collection.</span></span> <span data-ttu-id="77e59-119">たとえば、次の XML スキーマ コレクションは、保護されている `sqltypes` 名前空間にコンポーネントを追加しているため、失敗します。</span><span class="sxs-lookup"><span data-stu-id="77e59-119">For example, the following XML schema collection fails, because it is adding a component to the `sqltypes` protected namespace:</span></span>  
  
    ```  
    CREATE XML SCHEMA COLLECTION SC AS '  
    <schema xmlns="http://www.w3.org/2001/XMLSchema"   
    targetNamespace    
        ="https://schemas.microsoft.com/sqlserver/2004/sqltypes" >   
          <element name="root" type="string"/>  
    </schema>'  
    GO  
    ```  
  
-   <span data-ttu-id="77e59-120">`sys` XML スキーマ コレクションを `xml` 型の列、変数、またはパラメーターの型指定に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="77e59-120">You cannot use the `sys` XML schema collection to type `xml` columns, variables, or parameters.</span></span> <span data-ttu-id="77e59-121">たとえば、次のコードではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="77e59-121">For example, the following code returns an error:</span></span>  
  
    ```  
    DECLARE @x xml (sys.sys)  
    ```  
  
-   <span data-ttu-id="77e59-122">これらの組み込みスキーマのシリアル化は、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="77e59-122">Serialization of these built-in schemas is not supported.</span></span> <span data-ttu-id="77e59-123">たとえば、次のコードではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="77e59-123">For example, the following code returns an error:</span></span>  
  
    ```  
    SELECT XML_SCHEMA_NAMESPACE(N'sys',N'sys')  
    GO  
    ```  
  
 <span data-ttu-id="77e59-124">`varchar` 名前空間で定義されている `sqltypes` 型を使用する XML スキーマ コレクションを作成する別の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="77e59-124">The following code is another example in which you create an XML schema collection that uses the `varchar` type defined in the `sqltypes` namespace:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="myNS" xmlns:ns="myNS"  
        xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes">  
   <import     
     namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
      <simpleType name="myType">  
            <restriction base="s:varchar">  
                  <maxLength value="20"/>  
            </restriction>  
      </simpleType>  
      <element name="root" type="ns:myType"/>  
</schema>'  
go  
```  
  
 <span data-ttu-id="77e59-125">次の例に示すように、型指定した `XML` 変数を作成し、これに XML インスタンスを割り当て、<`root`> 要素の値の型が `varchar` 型であることを検証できます。</span><span class="sxs-lookup"><span data-stu-id="77e59-125">As shown in the following, you can create a typed `XML` variable, assign an XML instance to it, and verify that the value of the <`root`> element type is a `varchar` type.</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xmlns="myNS">My data</root>'  
SELECT @var.query('declare namespace sqltypes = "https://schemas.microsoft.com/sqlserver/2004/sqltypes";  
declare namespace ns="myNS";   
data(/ns:root[1]) instance of sqltypes:varchar?')  
GO  
```  
  
 <span data-ttu-id="77e59-126">`@var` 変数に関連付けられているスキーマに従うと、<`root`> 要素の値の型が **varchar** 型の派生型であるため、`instance of sqltypes:varchar?` 式は TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="77e59-126">The `instance of sqltypes:varchar?` expression returns TRUE, because the <`root`> element value is of a type derived from **varchar** according to the schema that is associated with the `@var` variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e59-127">参照</span><span class="sxs-lookup"><span data-stu-id="77e59-127">See Also</span></span>  
 [<span data-ttu-id="77e59-128">XML スキーマ コレクション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="77e59-128">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
