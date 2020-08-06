---
title: XML データへのビジネス ロジックの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 5bf8e9edc36e9c420faa92f2db1a92c311194e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634333"
---
# <a name="add-business-logic-to-xml-data"></a><span data-ttu-id="cc23e-102">XML データへのビジネス ロジックの追加</span><span class="sxs-lookup"><span data-stu-id="cc23e-102">Add Business Logic to XML Data</span></span>
  <span data-ttu-id="cc23e-103">XML データにはいくつかの方法でビジネス ロジックを追加できます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-103">Your business logic can be added to XML data in several ways:</span></span>  
  
-   <span data-ttu-id="cc23e-104">XML データの挿入や変更のときに領域固有の制約を強制する行制約または列制約を記述できます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-104">You can write row or column constraints to enforce domain-specific constraints during insertion and modification of XML data.</span></span>  
  
-   <span data-ttu-id="cc23e-105">列の値を挿入または更新したときに起動するトリガーを XML 列に記述できます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-105">You can write a trigger on the XML column that fires when you insert or update values in the column.</span></span> <span data-ttu-id="cc23e-106">トリガーには領域固有の検証規則を含めたり、トリガーを使用してプロパティ テーブルにデータを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-106">The trigger can contain domain-specific validation rules or populate property tables.</span></span>  
  
-   <span data-ttu-id="cc23e-107">データベース エンジンには、マネージド コードを実行する機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc23e-107">The Database Engine includes the ability execute managed code.</span></span> <span data-ttu-id="cc23e-108">この共通言語ランタイム (CLR) 統合を使用すると、XML 値を渡す関数をマネージド コードに記述し、System.Xml 名前空間の提供する XML 処理機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-108">You can use this common language runtime (CLR) integration to write functions in managed code to which you pass XML values, and use XML processing capabilities provided by the System.Xml namespace.</span></span> <span data-ttu-id="cc23e-109">たとえば、XML データに XSL 変換を適用する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="cc23e-109">An example is to apply XSL transformation to XML data.</span></span> <span data-ttu-id="cc23e-110">または、XML のシリアル化を解除して 1 つ以上のマネージド クラスにし、マネージド コードで操作することができます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-110">Alternatively, you can deserialize the XML into one or more managed classes and operate on them by using managed code.</span></span>  
  
-   <span data-ttu-id="cc23e-111">ビジネス ニーズに合わせて XML 列の処理を開始する Transact-SQL ストアド プロシージャや関数を記述できます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-111">You can write Transact-SQL stored procedures and functions that start the processing on the XML column for your business needs.</span></span>  
  
## <a name="example-applying-xsl-transformation"></a><span data-ttu-id="cc23e-112">例: XSL 変換の適用</span><span class="sxs-lookup"><span data-stu-id="cc23e-112">Example: Applying XSL Transformation</span></span>  
 <span data-ttu-id="cc23e-113">データ型のインスタンスとファイルに格納されている XSL 変換を受け取り、変換を XML データに適用して、変換後の XML を結果に返す CLR 関数**Transformxml ()** について考えてみ `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-113">Consider a CLR function **TransformXml()** that accepts an `xml` data type instance and an XSL transformation stored in a file, applies the transformation to the XML data, and then returns the transformed XML in the result.</span></span> <span data-ttu-id="cc23e-114">次に示すのは、C# で記述した関数の骨組みです。</span><span class="sxs-lookup"><span data-stu-id="cc23e-114">Following is a skeleton function that is written in C#:</span></span>  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 <span data-ttu-id="cc23e-115">アセンブリを登録し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] TransformXml() **に対応する** のユーザー定義関数 **SqlXslTransform()** を作成すると、次のクエリに示すように Transact-SQL からその関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-115">After the assembly is registered and a user-defined [!INCLUDE[tsql](../../includes/tsql-md.md)] function is created, **SqlXslTransform()** corresponding to **TransformXml()**, the function can be invoked from Transact-SQL as shown in the following query:</span></span>  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 <span data-ttu-id="cc23e-116">クエリの結果には、変換後の XML の行セットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc23e-116">The query result contains a rowset of the transformed XML.</span></span>  
  
 <span data-ttu-id="cc23e-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に CLR を統合することによって、XML データをテーブルに分解するかプロパティを昇格させてから、System.Xml 名前空間のマネージド クラスを使用して XML データにクエリを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cc23e-117">The CLR integration into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] expands the possibilities for decomposing XML data into tables or property promotion, and querying XML data by using managed classes in the System.Xml namespace.</span></span> <span data-ttu-id="cc23e-118">詳細については、「[XML データ &#40;SQL Server&#41;](xml-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc23e-118">For more information, see [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md).</span></span>  
  
  
