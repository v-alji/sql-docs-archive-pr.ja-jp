---
title: XPath クエリを含むテンプレートの実行 (SQLXMLOLEDB Provider) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing template files
- Base Path property
- templates [SQLXML], XPath queries
- XPath queries [SQLXML], templates
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
- XML templates [SQLXML]
ms.assetid: 7368c188-607e-459e-8254-8f23352dfa01
author: rothja
ms.author: jroth
ms.openlocfilehash: b3d31c95fe5d4fb1b7dc9a8d039a56b41cdd7349
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716158"
---
# <a name="executing-templates-that-contain-xpath-queries-sqlxmloledb-provider"></a><span data-ttu-id="f069c-102">XPath クエリを含むテンプレートの実行 (SQLXMLOLEDB プロバイダー)</span><span class="sxs-lookup"><span data-stu-id="f069c-102">Executing Templates That Contain XPath Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="f069c-103">この例では、次の SQLXMLOLEDB プロバイダー固有のプロパティについて、使用法を示します。</span><span class="sxs-lookup"><span data-stu-id="f069c-103">This example shows how to use the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="f069c-104">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="f069c-104">ClientSideXML</span></span>  
  
-   <span data-ttu-id="f069c-105">基本パス</span><span class="sxs-lookup"><span data-stu-id="f069c-105">Base Path</span></span>  
  
-   <span data-ttu-id="f069c-106">マッピング スキーマ</span><span class="sxs-lookup"><span data-stu-id="f069c-106">Mapping Schema</span></span>  
  
 <span data-ttu-id="f069c-107">このサンプル ADO アプリケーションでは、XPath クエリ (ルート) で構成される XML テンプレートが XSD マッピングスキーマ (MySchema.xml) に対して指定されています。これについては、「 [Xpath クエリ &#40;SQLXMLOLEDB Provider&#41;を実行](executing-xpath-queries-sqlxmloledb-provider.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f069c-107">In this sample ADO application, an XML template that consists of an XPath query (root) is specified against the XSD mapping schema (MySchema.xml) that is described in [Executing XPath Queries &#40;SQLXMLOLEDB Provider&#41;](executing-xpath-queries-sqlxmloledb-provider.md).</span></span>  
  
 <span data-ttu-id="f069c-108">マッピングスキーマプロパティは、XPath クエリの実行対象となる XSD マッピングスキーマを提供します。</span><span class="sxs-lookup"><span data-stu-id="f069c-108">The Mapping Schema property provides the XSD mapping schema against which the XPath query is executed.</span></span> <span data-ttu-id="f069c-109">Base Path プロパティは、マッピングスキーマへのファイルパスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f069c-109">The Base Path property provides the file path to the mapping schema.</span></span>  
  
 <span data-ttu-id="f069c-110">ClientSideXML プロパティは True に設定されています。</span><span class="sxs-lookup"><span data-stu-id="f069c-110">The ClientSideXML property is set to True.</span></span> <span data-ttu-id="f069c-111">つまり、XML ドキュメントはクライアントで生成されます。</span><span class="sxs-lookup"><span data-stu-id="f069c-111">Therefore, the XML document is generated on the client.</span></span>  
  
 <span data-ttu-id="f069c-112">このアプリケーションでは、XPath クエリを直接指定します。</span><span class="sxs-lookup"><span data-stu-id="f069c-112">In the application, an XPath query is specified directly.</span></span> <span data-ttu-id="f069c-113">したがって、言語 {5d531cb2-e6ed-11d2-b252-00c04f681b71} を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f069c-113">Therefore, the dialect {5d531cb2-e6ed-11d2-b252-00c04f681b71} must be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f069c-114">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f069c-114">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="f069c-115">また、この例では、追加の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ネットワーククライアントソフトウェアをインストールする必要があるデータプロバイダーに対して Native Client (SQLNCLI11) を使用するように指定しています。</span><span class="sxs-lookup"><span data-stu-id="f069c-115">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="f069c-116">詳細については、「 [SQL Server Native Client のシステム要件](../../native-client/system-requirements-for-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f069c-116">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub Main()  
  
   Dim oTestStream As New ADODB.Stream  
   Dim oTestConnection As New ADODB.Connection  
   Dim oTestCommand As New ADODB.Command  
  
   oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
  
   oTestCommand.ActiveConnection = oTestConnection  
   oTestCommand.Properties("ClientSideXML") = "False"  
  
   oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:xpath-query mapping-schema='mySchema.xml' > " & _  
        "   root " & _  
        "   </sql:xpath-query> " & _  
        " </ROOT> "  
   oTestStream.Open  
   ' You need the dialect if you are executing a template.  
   oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
   oTestCommand.Properties("Output Stream").Value = oTestStream  
   oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\TemplateWithXPath\"  
   oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
   oTestCommand.Properties("Output Encoding") = "utf-8"  
   oTestCommand.Execute , , adExecuteStream  
   oTestStream.Position = 0  
   oTestStream.Charset = "utf-8"  
   Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
  
Sub Form_Load()  
   Main  
End Sub  
```  
  
 <span data-ttu-id="f069c-117">スキーマは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f069c-117">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contact'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  
  <xsd:element name='Contact' sql:relation='Person.Contact'>  
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
  
