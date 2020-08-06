---
title: XPath クエリの実行 (SQLXMLOLEDB Provider) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- queries [SQLXML], SQLXMLOLEDB Provider
- Base Path property
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
ms.assetid: 19063222-dc9c-48ae-a55f-778103674a9e
author: rothja
ms.author: jroth
ms.openlocfilehash: 667bc8dfd95c37c0a10c0bc68f3007e7d04533e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716161"
---
# <a name="executing-xpath-queries-sqlxmloledb-provider"></a><span data-ttu-id="122ad-102">XPath クエリの実行 (SQLXMLOLEDB プロバイダー)</span><span class="sxs-lookup"><span data-stu-id="122ad-102">Executing XPath Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="122ad-103">この例では、次の SQLXMLOLEDB プロバイダー固有のプロパティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="122ad-103">This example illustrates the use of the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   `ClientSideXML`  
  
-   `Base Path`  
  
-   `Mapping Schema`  
  
 <span data-ttu-id="122ad-104">このサンプル ADO アプリケーションでは、XPath クエリ (root) を XSD マッピング スキーマ (MySchema.xml) に対して指定します。</span><span class="sxs-lookup"><span data-stu-id="122ad-104">In this sample ADO application, an XPath query (root) is specified against an XSD mapping schema (MySchema.xml).</span></span> <span data-ttu-id="122ad-105">スキーマには、 **\<Contacts>** **ContactID**、 **FirstName**、および**LastName**属性を持つ要素があります。</span><span class="sxs-lookup"><span data-stu-id="122ad-105">The schema has a **\<Contacts>** element with **ContactID**, **FirstName**, and **LastName** attributes.</span></span> <span data-ttu-id="122ad-106">このスキーマでは、既定のマッピングにより、要素名は同じ名前のテーブルに、単純型の属性は同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="122ad-106">In the schema, default mapping takes place: an element name maps to the table with the same name, and attributes of simple type map to the columns with the same names.</span></span>  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contacts'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name='Contacts' sql:relation='Person.Contact'>   
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="122ad-107">マッピングスキーマプロパティは、XPath クエリの実行対象となるマッピングスキーマを提供します。</span><span class="sxs-lookup"><span data-stu-id="122ad-107">The Mapping Schema property provides the mapping schema against which the XPath query is executed.</span></span> <span data-ttu-id="122ad-108">このマッピング スキーマには XSD または XDR スキーマを指定できます。</span><span class="sxs-lookup"><span data-stu-id="122ad-108">The mapping schema can be an XSD or XDR schema.</span></span> <span data-ttu-id="122ad-109">Base Path プロパティは、マッピングスキーマへのファイルパスを提供します。</span><span class="sxs-lookup"><span data-stu-id="122ad-109">The Base Path property provides the file path to the mapping schema.</span></span>  
  
 <span data-ttu-id="122ad-110">ClientSideXML プロパティは True に設定されています。</span><span class="sxs-lookup"><span data-stu-id="122ad-110">The ClientSideXML property is set to True.</span></span> <span data-ttu-id="122ad-111">つまり、XML ドキュメントはクライアントで生成されます。</span><span class="sxs-lookup"><span data-stu-id="122ad-111">Therefore, the XML document is generated on the client.</span></span>  
  
 <span data-ttu-id="122ad-112">このアプリケーションでは、XPath クエリを直接指定します。</span><span class="sxs-lookup"><span data-stu-id="122ad-112">In the application, an XPath query is specified directly.</span></span> <span data-ttu-id="122ad-113">したがって、XPath 言語 {ec2a4293-e898-11d2-b1b7-00c04f680c56} を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="122ad-113">Therefore, the XPath dialect {ec2a4293-e898-11d2-b1b7-00c04f680c56} must be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="122ad-114">コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="122ad-114">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="122ad-115">また、この例では、追加の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ネットワーククライアントソフトウェアをインストールする必要があるデータプロバイダーに対して Native Client (SQLNCLI11) を使用するように指定しています。</span><span class="sxs-lookup"><span data-stu-id="122ad-115">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="122ad-116">詳細については、「 [SQL Server Native Client のシステム要件](../../native-client/system-requirements-for-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="122ad-116">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security= SSPI;"  
  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
  
oTestCommand.CommandText = "root"  
oTestStream.Open  
oTestCommand.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\XPathDirect\"  
oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
oTestCommand.Properties("Output Encoding") = "utf-8"  
oTestCommand.Execute , , adExecuteStream  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
