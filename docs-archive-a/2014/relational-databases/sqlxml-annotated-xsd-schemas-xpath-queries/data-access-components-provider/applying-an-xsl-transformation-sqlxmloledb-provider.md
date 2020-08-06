---
title: XSL 変換の適用 (SQLXMLOLEDB Provider) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fbb427a95d9f2308bf65724758a4a1563b42575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641999"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a><span data-ttu-id="1eb14-102">XSL 変換の適用 (SQLXMLOLEDB プロバイダー)</span><span class="sxs-lookup"><span data-stu-id="1eb14-102">Applying an XSL Transformation (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="1eb14-103">このサンプル ADO アプリケーションでは、SQL クエリが実行され、結果に XSL 変換が適用されます。</span><span class="sxs-lookup"><span data-stu-id="1eb14-103">In this sample ADO application, an SQL query is executed, and an XSL transformation is applied to the result.</span></span> <span data-ttu-id="1eb14-104">ClientSideXML プロパティを True に設定すると、クライアント側で行セットの処理が強制されます。</span><span class="sxs-lookup"><span data-stu-id="1eb14-104">Setting the ClientSideXML property to True enforces the processing of the rowset on the client side.</span></span> <span data-ttu-id="1eb14-105">SQL クエリをテンプレートで指定する場合は、テンプレート実行時にコマンド言語を指定する必要があるため、コマンド言語 {5d531cb2-e6ed-11d2-b252-00c04f681b71} を設定します。</span><span class="sxs-lookup"><span data-stu-id="1eb14-105">The command dialect is set to {5d531cb2-e6ed-11d2-b252-00c04f681b71}, because the SQL query is specified in a template and this dialect must be specified when executing a template.</span></span> <span data-ttu-id="1eb14-106">Xsl プロパティは、変換の適用に使用する XSL ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="1eb14-106">The xsl property specifies the XSL file to use to apply the transformation.</span></span> <span data-ttu-id="1eb14-107">[基本パスプロパティの値は、XSL ファイルを検索するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1eb14-107">The value of Base Path property is used to search for the XSL file.</span></span> <span data-ttu-id="1eb14-108">Xsl プロパティの値にパスを指定した場合、パスは、[ベースパス] プロパティで指定したパスに対する相対パスになります。</span><span class="sxs-lookup"><span data-stu-id="1eb14-108">If you specify a path in the value of the xsl property, the path is relative to the path that is specified in the Base Path property.</span></span>  
  
 <span data-ttu-id="1eb14-109">この例では、次の SQLXMLOLEDB プロバイダー固有のプロパティについて、使用法を示します。</span><span class="sxs-lookup"><span data-stu-id="1eb14-109">This example shows how to use the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="1eb14-110">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="1eb14-110">ClientSideXML</span></span>  
  
-   <span data-ttu-id="1eb14-111">xsl</span><span class="sxs-lookup"><span data-stu-id="1eb14-111">xsl</span></span>  
  
 <span data-ttu-id="1eb14-112">このクライアント側の ADO サンプル アプリケーションでは、SQL クエリで構成される XML テンプレートがサーバーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="1eb14-112">In this client-side ADO sample application, an XML template that consists of an SQL query is executed on the server.</span></span>  
  
 <span data-ttu-id="1eb14-113">ClientSideXML プロパティが True に設定されているため、FOR XML 句を指定せずに SELECT ステートメントがサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="1eb14-113">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="1eb14-114">サーバーではクエリが実行され、クライアントに行セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="1eb14-114">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="1eb14-115">次に、クライアントは、行セットに FOR XML 変換を適用し、XML ドキュメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="1eb14-115">The client then applies the FOR XML transformation to the rowset and produces the XML document.</span></span>  
  
 <span data-ttu-id="1eb14-116">Xsl プロパティは、アプリケーションで指定されています。そのため、クライアントで生成された XML ドキュメントに XSL 変換が適用され、結果は2列のテーブルになります。</span><span class="sxs-lookup"><span data-stu-id="1eb14-116">The xsl property is specified in the application; therefore, the XSL transformation is applied to the XML document that is generated on the client, and the result is a two-column table.</span></span>  
  
 <span data-ttu-id="1eb14-117">テンプレートコマンドを実行するには、XML テンプレート言語 ({5d531cb2-e6ed-11d2-b252-00c04f681b71}) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eb14-117">To execute the template command, the XML template dialect - {5d531cb2-e6ed-11d2-b252-00c04f681b71} - must be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1eb14-118">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eb14-118">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="1eb14-119">また、この例ではデータ プロバイダーとして [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用するよう指定していますが、これには追加ネットワーク クライアントがインストールされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="1eb14-119">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="1eb14-120">詳細については、「 [SQL Server Native Client のシステム要件](../../native-client/system-requirements-for-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1eb14-120">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 <span data-ttu-id="1eb14-121">次は XSL テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="1eb14-121">The XSL template follows.</span></span> <span data-ttu-id="1eb14-122">この XSL テンプレートを適用すると、2 列のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1eb14-122">The result of applying this XSL template is a two-column table.</span></span>  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  
