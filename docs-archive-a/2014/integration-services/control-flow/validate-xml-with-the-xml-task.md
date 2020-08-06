---
title: XML タスクを使った XML の検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- XML validation
- XML, validating
ms.assetid: 224fc025-c21f-4d43-aa9d-5ffac337f9b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 633a269f53c85353c956b33bff8fd3af518dad56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631162"
---
# <a name="validate-xml-with-the-xml-task"></a><span data-ttu-id="12f51-102">Validate XML with the XML Task</span><span class="sxs-lookup"><span data-stu-id="12f51-102">Validate XML with the XML Task</span></span>
  <span data-ttu-id="12f51-103">XML タスクの `ValidationDetails` プロパティを有効にして、XML ドキュメントを検証し、詳細なエラー出力を取得します。</span><span class="sxs-lookup"><span data-stu-id="12f51-103">Validate XML documents and get rich error output by enabling the `ValidationDetails` property of the XML Task.</span></span>

 <span data-ttu-id="12f51-104">次のスクリーン ショットは、 **XML タスク エディター** と、XML 検証で詳細なエラー出力を取得するのに必要な設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="12f51-104">The following screen shot shows the **XML Task Editor** with the settings required for XML validation with rich error output.</span></span>

 <span data-ttu-id="12f51-105">![XML タスク エディターの XML タスク プロパティ](../media/xmltaskproperties.jpg "XML タスク エディターの XML タスク プロパティ")</span><span class="sxs-lookup"><span data-stu-id="12f51-105">![XML task properties in the XML Task Editor](../media/xmltaskproperties.jpg "XML task properties in the XML Task Editor")</span></span>

 <span data-ttu-id="12f51-106">`ValidationDetails` プロパティが利用できるようになる前は、XML タスクによる XML 検証では、true や false のみの結果が返され、エラーやその場所に関する情報は返されませんでした。</span><span class="sxs-lookup"><span data-stu-id="12f51-106">Before the `ValidationDetails` property was available, XML validation by the XML Task returned only a true or false result, with no information about errors or their locations.</span></span> <span data-ttu-id="12f51-107">これで、を true に設定すると、 `ValidationDetails` 出力ファイルには、行番号と位置を含むすべてのエラーに関する詳細情報が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="12f51-107">Now, when you set `ValidationDetails` to true, the output file contains detailed information about every error including the line number and the position.</span></span> <span data-ttu-id="12f51-108">この情報を使って、XML ドキュメントのエラーを把握、特定、修正できます。</span><span class="sxs-lookup"><span data-stu-id="12f51-108">You can use this information to understand, locate, and fix errors in XML documents.</span></span>

 <span data-ttu-id="12f51-109">この XML 検証機能は、大きなサイズの XML ドキュメントや大量のエラーにも、簡単に規模を変更して対応できます。</span><span class="sxs-lookup"><span data-stu-id="12f51-109">The XML validation functionality scales easily for large XML documents and large numbers of errors.</span></span> <span data-ttu-id="12f51-110">出力ファイル自体が XML 形式なので、出力に対するクエリの実行と分析が可能です。</span><span class="sxs-lookup"><span data-stu-id="12f51-110">Since the output file itself is in XML format, you can query and analyze the output.</span></span> <span data-ttu-id="12f51-111">たとえば、出力に大量のエラーが含まれている場合、このトピックで説明する方法で [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用して、エラーをグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="12f51-111">For example, if the output contains a large number of errors, you can group the errors by using a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query, as described in this topic.</span></span>

> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="12f51-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]( [!INCLUDE[ssIS](../../includes/ssis-md.md)] ) では、 `ValidationDetails` [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 2 でプロパティが導入されました。</span><span class="sxs-lookup"><span data-stu-id="12f51-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) introduced the `ValidationDetails` property in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 2.</span></span> <span data-ttu-id="12f51-113">プロパティは [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 、および SQL Server 2016 でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="12f51-113">The property is also available in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] and in SQL Server 2016.</span></span>

## <a name="sample-output-for-xml-thats-valid"></a><span data-ttu-id="12f51-114">有効な XML のサンプル出力</span><span class="sxs-lookup"><span data-stu-id="12f51-114">Sample output for XML that's valid</span></span>
 <span data-ttu-id="12f51-115">有効な XML ファイルの検証結果が記載されたサンプル出力ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="12f51-115">Here is a sample output file with validation results for a valid XML file.</span></span>

```xml

<root xmlns:ns="https://schemas.microsoft.com/xmltools/2002/xmlvalidation">
    <metadata>
        <result>true</result>
        <errors>0</errors>
        <warnings>0</warnings>
        <startTime>2015-05-28T10:27:22.087</startTime>
        <endTime>2015-05-28T10:29:07.007</endTime>
        <xmlFile>d:\Temp\TestData.xml</xmlFile>
        <xsdFile>d:\Temp\TestSchema.xsd</xsdFile>
    </metadata>
    <messages />
</root>
```

## <a name="sample-output-for-xml-thats-not-valid"></a><span data-ttu-id="12f51-116">無効な XML のサンプル出力</span><span class="sxs-lookup"><span data-stu-id="12f51-116">Sample output for XML that's not valid</span></span>
 <span data-ttu-id="12f51-117">少数のエラーのある XML ファイルの検証結果が記載されたサンプル出力ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="12f51-117">Here is a sample output file with validation results for an XML file that contains a small number of errors.</span></span> <span data-ttu-id="12f51-118">\<error> 要素のテキストは、読みやすくするために折り返されています。</span><span class="sxs-lookup"><span data-stu-id="12f51-118">The text of the \<error> elements has been wrapped for readability.</span></span>

```xml

<root xmlns:ns="https://schemas.microsoft.com/xmltools/2002/xmlvalidation">
    <metadata>
        <result>false</result>
        <errors>2</errors>
        <warnings>0</warnings>
        <startTime>2015-05-28T10:45:09.538</startTime>
        <endTime>2015-05-28T10:45:09.558</endTime>
        <xmlFile>C:\Temp\TestData.xml</xmlFile>
        <xsdFile>C:\Temp\TestSchema.xsd</xsdFile>
    </metadata>
    <messages>
        <error line="5" position="26">The 'ApplicantRole' element is invalid - The value 'wer3' is invalid
    according to its datatype 'ApplicantRoleType' - The Enumeration constraint failed.</error>
        <error line="16" position="28">The 'Phone' element is invalid - The value 'we3056666666' is invalid
     according to its datatype 'phone' - The Pattern constraint failed.</error>
    </messages>
</root>
```

## <a name="analyze-xml-validation-output-with-a-transact-sql-query"></a><span data-ttu-id="12f51-119">XML 検証の出力を Transact-SQL クエリで分析する</span><span class="sxs-lookup"><span data-stu-id="12f51-119">Analyze XML validation output with a Transact-SQL query</span></span>
 <span data-ttu-id="12f51-120">XML 検証の出力に大量のエラーが含まれている場合、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に出力を読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="12f51-120">If the output of XML validation contains a large number of errors, you can use a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query to load the output in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="12f51-121">そのうえで、WHERE、GROUP BY、ORDER BY、JOINなどの T-SQL 言語の機能をフル活用して、エラー一覧を分析できます。</span><span class="sxs-lookup"><span data-stu-id="12f51-121">Then you can analyze the error list with all the capabilities of the T-SQL language including WHERE, GROUP BY, ORDER BY, JOIN, and so forth.</span></span>

```sql
DECLARE @xml XML;

SELECT @xml = XmlDoc   
FROM OPENROWSET (BULK N'C:\Temp\XMLValidation_2016-02-212T10-41-00.xml', SINGLE_BLOB) AS Tab(XmlDoc);

-- Query # 1, flat list of errors
-- convert to relational/rectangular
;WITH XMLNAMESPACES ('https://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS
(
SELECT col.value('@line','INT') AS line
     , col.value('@position','INT') AS position
     , col.value('.','VARCHAR(1024)') AS error
FROM @XML.nodes('/root/messages/error') AS tab(col)
)
SELECT * FROM rs;
-- WHERE error LIKE '%whatever_string%'

-- Query # 2, count of errors grouped by the error message
-- convert to relational/rectangular
;WITH XMLNAMESPACES ('https://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS
(
SELECT col.value('@line','INT') AS line
     , col.value('@position','INT') AS position
     , col.value('.','VARCHAR(1024)') AS error
FROM @XML.nodes('/root/messages/error') AS tab(col)
)
SELECT COALESCE(error,'Total # of errors:') AS [error], COUNT(*) AS [counter]
FROM rs
GROUP BY GROUPING SETS ((error), ())
ORDER BY 2 DESC, COALESCE(error, 'Z');

```

 <span data-ttu-id="12f51-122">次に示すのは、前に示したテキストの 2 つ目のサンプル クエリの結果を [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で表示した画面です。</span><span class="sxs-lookup"><span data-stu-id="12f51-122">Here is the result in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] of the second sample query shown in the preceding text.</span></span>

 <span data-ttu-id="12f51-123">![Management Studio で XML エラーをグループ化するクエリ](../media/queryforxmlerrors.jpg "Management Studio で XML エラーをグループ化するクエリ")</span><span class="sxs-lookup"><span data-stu-id="12f51-123">![Query to group XML errors in Management Studio](../media/queryforxmlerrors.jpg "Query to group XML errors in Management Studio")</span></span>

## <a name="see-also"></a><span data-ttu-id="12f51-124">参照</span><span class="sxs-lookup"><span data-stu-id="12f51-124">See Also</span></span>
 <span data-ttu-id="12f51-125">[ [Xml タスク](xml-task.md) [Xml タスクエディター] &#40;[全般] ページ&#41;](../xml-task-editor-general-page.md)</span><span class="sxs-lookup"><span data-stu-id="12f51-125">[XML Task](xml-task.md) [XML Task Editor &#40;General Page&#41;](../xml-task-editor-general-page.md)</span></span>


