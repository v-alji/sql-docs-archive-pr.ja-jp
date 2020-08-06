---
title: XML スキーマの使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- XML [SMO]
ms.assetid: 9d04de01-efeb-4b2d-8c28-3234bc7ff2f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a0e5c58bb05da7025651a4e55e29541d694ba1ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741677"
---
# <a name="using-xml-schemas"></a><span data-ttu-id="84f02-102">XML スキーマの使用方法</span><span class="sxs-lookup"><span data-stu-id="84f02-102">Using XML Schemas</span></span>
  <span data-ttu-id="84f02-103">SMO で使用できる XML プログラミングの機能は、XML データ型や XML 名前空間の提供、および XML データ型の列での簡易インデックス作成に限定されています。</span><span class="sxs-lookup"><span data-stu-id="84f02-103">XML programming in SMO is limited to providing XML data types, XML namespaces, and simple indexing on XML data type columns.</span></span>  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="84f02-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]XML ドキュメントインスタンスのネイティブストレージを提供します。</span><span class="sxs-lookup"><span data-stu-id="84f02-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides native storage for XML document instances.</span></span> <span data-ttu-id="84f02-105">XML スキーマを使用すると、複雑な XML データ型を定義することができます。これを使用して、XML ドキュメントを検証し、データの整合性を確保することができます。</span><span class="sxs-lookup"><span data-stu-id="84f02-105">XML schemas let you define complex XML data types, which can be used to validate XML documents to ensure data integrity.</span></span> <span data-ttu-id="84f02-106">XML スキーマは、<xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> オブジェクトで定義します。</span><span class="sxs-lookup"><span data-stu-id="84f02-106">The XML schema is defined in the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84f02-107">例</span><span class="sxs-lookup"><span data-stu-id="84f02-107">Example</span></span>  
 <span data-ttu-id="84f02-108">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84f02-108">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="84f02-109">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84f02-109">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-an-xml-schema-in-visual-basic"></a><span data-ttu-id="84f02-110">Visual Basic での XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="84f02-110">Creating an XML Schema in Visual Basic</span></span>  
 <span data-ttu-id="84f02-111">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> オブジェクトを使用して XML スキーマを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84f02-111">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="84f02-112">XML スキーマ コレクションを定義する <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> プロパティは、複数の二重引用符記号を格納しています。</span><span class="sxs-lookup"><span data-stu-id="84f02-112">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="84f02-113">これらは `chr(34)` 文字列に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="84f02-113">These are replaced by the `chr(34)` string.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBXMLSchema1](SMO How to#SMO_VBXMLSchema1)]  -->  
  
## <a name="creating-an-xml-schema-in-visual-c"></a><span data-ttu-id="84f02-114">Visual C# での XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="84f02-114">Creating an XML Schema in Visual C#</span></span>  
 <span data-ttu-id="84f02-115">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> オブジェクトを使用して XML スキーマを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84f02-115">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="84f02-116">XML スキーマ コレクションを定義する <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> プロパティは、複数の二重引用符記号を格納しています。</span><span class="sxs-lookup"><span data-stu-id="84f02-116">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="84f02-117">これらは `chr(34)` 文字列に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="84f02-117">These are replaced by the `chr(34)` string.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = default(Server);  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define an XmlSchemaCollection object by supplying the parent  
            // database and name arguments in the constructor.   
            XmlSchemaCollection xsc = default(XmlSchemaCollection);  
            xsc = new XmlSchemaCollection(db, "MySampleCollection");  
            xsc.Text = "<schema xmlns=" + Strings.Chr(34) + "http://www.w3.org/2001/XMLSchema" + Strings.Chr(34) + " xmlns:ns=" + Strings.Chr(34) + "http://ns" + Strings.Chr(34) + "><element name=" + Strings.Chr(34) + "e" + Strings.Chr(34) + " type=" + Strings.Chr(34) + "dateTime" + Strings.Chr(34) + "/></schema>";  
            //Create the XML schema collection on the instance of SQL Server.   
            xsc.Create();  
        }  
```  
  
## <a name="creating-an-xml-schema-in-powershell"></a><span data-ttu-id="84f02-118">PowerShell での XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="84f02-118">Creating an XML Schema in PowerShell</span></span>  
 <span data-ttu-id="84f02-119">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> オブジェクトを使用して XML スキーマを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84f02-119">This code example shows how to create an XML schema by using the <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection> object.</span></span> <span data-ttu-id="84f02-120">XML スキーマ コレクションを定義する <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> プロパティは、複数の二重引用符記号を格納しています。</span><span class="sxs-lookup"><span data-stu-id="84f02-120">The <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A> property, which defines the XML schema collection, contains several double quotation marks.</span></span> <span data-ttu-id="84f02-121">これらは `chr(34)` 文字列に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="84f02-121">These are replaced by the `chr(34)` string.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalHost  
$srv = Get-Item default  
  
#Reference the AdventureWorks database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a new schema collection  
$xsc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.XmlSchemaCollection `  
-argumentlist $db,"MySampleCollection"  
  
#Add the xml  
$dq = '"' # the double quote character  
$xsc.Text = "<schema xmlns=" + $dq + "http://www.w3.org/2001/XMLSchema" + $dq + `  
"  xmlns:ns=" + $dq + "http://ns" + $dq + "><element name=" + $dq + "e" + $dq +`  
 " type=" + $dq + "dateTime" + $dq + "/></schema>"  
  
#Create the XML schema collection on the instance of SQL Server.  
$xsc.Create()  
```  
