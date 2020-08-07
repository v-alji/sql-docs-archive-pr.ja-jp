---
title: 名前空間を使用した XPath クエリの実行 (SQLXMLOLEDB Provider) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- namespaces property
- queries [SQLXML], SQLXMLOLEDB Provider
- XPath queries [SQLXML], namespaces
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- namespaces [SQLXML], XPath queries
ms.assetid: 024a4b7d-435d-47ba-9e80-2c2f640108f5
author: rothja
ms.author: jroth
ms.openlocfilehash: ff692b49a4c32c14655af3a9eb07071dc60ba2a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716150"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxmloledb-provider"></a><span data-ttu-id="01d7a-102">名前空間を使用した、XPath クエリの実行 (SQLXMLOLEDB Provider)</span><span class="sxs-lookup"><span data-stu-id="01d7a-102">Executing XPath Queries with Namespaces (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="01d7a-103">XPath クエリには名前空間を使用できます。</span><span class="sxs-lookup"><span data-stu-id="01d7a-103">XPath queries can include namespaces.</span></span> <span data-ttu-id="01d7a-104">スキーマ要素が名前空間で限定されている (対象の名前空間を含んでいる) 場合、そのスキーマに対する XPath クエリでは、この名前空間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01d7a-104">If the schema elements are namespace qualified (that is, if they include a target namespace), XPath queries against the schema must specify this namespace.</span></span>  
  
 <span data-ttu-id="01d7a-105">SQLXML 4.0 ではワイルドカード文字 (\*) の使用がサポートされないため、XPath クエリは、名前空間プレフィックスを使用して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01d7a-105">Because using the wildcard character (\*) is not supported in SQLXML 4.0, you must specify the XPath query by using a namespace prefix.</span></span> <span data-ttu-id="01d7a-106">このプレフィックスを解決するには、名前空間プロパティを使用して名前空間のバインドを指定します。</span><span class="sxs-lookup"><span data-stu-id="01d7a-106">To resolve this prefix, use the namespaces property to specify the namespace binding.</span></span>  
  
 <span data-ttu-id="01d7a-107">次の例では、XPath クエリは、ワイルドカード文字 ( \* ) およびローカル名 () および名前空間 uri () の xpath 関数を使用して名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="01d7a-107">In the following example, the XPath query specifies namespaces by using the wildcard character (\*) and the local-name() and namespace-uri() XPath functions.</span></span> <span data-ttu-id="01d7a-108">この XPath クエリは、ローカル名がで、名前空間 URI がであるすべての要素を返し `Contact` `urn:myschema:Contacts` ます。</span><span class="sxs-lookup"><span data-stu-id="01d7a-108">This XPath query returns all the elements where the local name is `Contact` and the namespace URI is `urn:myschema:Contacts`.</span></span>  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 <span data-ttu-id="01d7a-109">SQLXML 4.0 では、この XPath クエリを名前空間プレフィックスと共に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01d7a-109">In SQLXML 4.0, this XPath query must be specified with a namespace prefix.</span></span> <span data-ttu-id="01d7a-110">たとえば、`x:Contact` と指定します。ここで、`x` は名前空間プレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="01d7a-110">An example is `x:Contact`, where `x` is the namespace prefix.</span></span> <span data-ttu-id="01d7a-111">次の XSD スキーマについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="01d7a-111">Consider the following XSD schema:</span></span>  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 <span data-ttu-id="01d7a-112">このスキーマでは対象の名前空間が定義されているため、このスキーマに対して "Employee" などの XPath クエリを実行するときには、クエリに名前空間を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="01d7a-112">Because this schema defines the target namespace, an XPath query (such as "Employee") against the schema must include the namespace.</span></span>  
  
 <span data-ttu-id="01d7a-113">これは、上の XSD スキーマに対して XPath クエリ (x:Employee) を実行する [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic アプリケーションのサンプルです。</span><span class="sxs-lookup"><span data-stu-id="01d7a-113">This is a sample [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application that executes an XPath query (x:Employee) against the preceding XSD schema.</span></span> <span data-ttu-id="01d7a-114">プレフィックスを解決するには、名前空間のプロパティを使用して名前空間のバインドを指定します。</span><span class="sxs-lookup"><span data-stu-id="01d7a-114">To resolve the prefix, the namespace binding is specified by using the namespaces property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01d7a-115">コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="01d7a-115">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="01d7a-116">また、この例ではデータ プロバイダーとして [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) を使用するよう指定していますが、これには追加ネットワーク クライアントがインストールされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="01d7a-116">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider, which requires additional network client software to be installed.</span></span> <span data-ttu-id="01d7a-117">詳細については、「 [SQL Server Native Client のシステム要件](../../native-client/system-requirements-for-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01d7a-117">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Private Sub Form_Load()  
    Dim con As New ADODB.Connection  
    Dim cmd As New ADODB.Command  
    Dim stm As New ADODB.Stream  
    con.Open "provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
    Set cmd.ActiveConnection = con  
    stm.Open  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    cmd.Properties("Mapping schema") = "C:\DirectoryPath\con-ex.xml"  
    cmd.Properties("namespaces") = "xmlns:x='urn:myschema:Contacts'"  
    '  Debug.Print "Set Command Dialect to DBGUID_XPATH"  
    cmd.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
    cmd.CommandText = "x:Contact"  
    cmd.Execute , , adExecuteStream   
    stm.Position = 0  
    Debug.Print stm.ReadText(adReadAll)  
End Sub  
```  
  
### <a name="to-test-this-application"></a><span data-ttu-id="01d7a-118">このアプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="01d7a-118">To test this application</span></span>  
  
1.  <span data-ttu-id="01d7a-119">サンプルの XSD スキーマをフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="01d7a-119">Save the sample XSD schema in a folder.</span></span>  
  
2.  <span data-ttu-id="01d7a-120">Visual Basic 実行可能プロジェクトを作成し、プロジェクト内にコードをコピーして、</span><span class="sxs-lookup"><span data-stu-id="01d7a-120">Create a Visual Basic executable project, and copy the code into it.</span></span> <span data-ttu-id="01d7a-121">指定されたディレクトリ パスを適切に変更します。</span><span class="sxs-lookup"><span data-stu-id="01d7a-121">Change the specified directory path as appropriate.</span></span>  
  
3.  <span data-ttu-id="01d7a-122">次のプロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="01d7a-122">Add the following project reference:</span></span>  
  
    ```  
    "Microsoft ActiveX Data Objects 2.8 Library"  
    ```  
  
4.  <span data-ttu-id="01d7a-123">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="01d7a-123">Execute the application.</span></span>  
  
 <span data-ttu-id="01d7a-124">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01d7a-124">This is the partial result:</span></span>  
  
```  
<y0:Employee xmlns:y0="urn:myschema:Contacts"   
             LName="Achong" CID="1" FName="Gustavo"/>  
<y0:Employee xmlns:y0="urn:myschema:Employees"   
             LName="Abel" CID="2" FName="Catherine"/>  
```  
  
 <span data-ttu-id="01d7a-125">XML ドキュメント内に生成されるプレフィックスはその都度変わりますが、マップされる名前空間は同じです。</span><span class="sxs-lookup"><span data-stu-id="01d7a-125">The prefixes that are generated in the XML document are arbitrary, but they map to the same namespace.</span></span>  
  
  
