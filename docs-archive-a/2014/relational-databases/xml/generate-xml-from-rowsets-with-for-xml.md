---
title: FOR XML を使用した行セットからの XML の生成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, generating XML from rowsets
ms.assetid: d061c0f1-3de9-4ad1-bbca-ce45d064b6c8
author: rothja
ms.author: jroth
ms.openlocfilehash: dcf9feb4dab9ad1149ab433c9d9b4999c96c1cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743058"
---
# <a name="generate-xml-from-rowsets-with-for-xml"></a><span data-ttu-id="86d90-102">FOR XML を使用した行セットからの XML の生成</span><span class="sxs-lookup"><span data-stu-id="86d90-102">Generate XML from Rowsets with FOR XML</span></span>
  <span data-ttu-id="86d90-103">新しい Type ディレクティブを使用して `xml` FOR XML を使用することにより、行**TYPE**セットからデータ型のインスタンスを生成できます。</span><span class="sxs-lookup"><span data-stu-id="86d90-103">You can generate an `xml` data type instance from a rowset by using FOR XML with the new **TYPE** directive.</span></span>  
  
 <span data-ttu-id="86d90-104">結果は、 `xml` データ型の列、変数、またはパラメーターに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="86d90-104">The result can be assigned to an `xml` data type column, variable, or parameter.</span></span> <span data-ttu-id="86d90-105">また、FOR XML を入れ子にして階層構造を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="86d90-105">Also, FOR XML can be nested to generate any hierarchical structure.</span></span> <span data-ttu-id="86d90-106">入れ子にした FOR XML は FOR XML EXPLICIT よりも記述が容易ですが、階層が深いとパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="86d90-106">This makes nested FOR XML much more convenient to write than FOR XML EXPLICIT, but it may not perform as well for deep hierarchies.</span></span> <span data-ttu-id="86d90-107">FOR XML には新しい PATH モードも導入されています。</span><span class="sxs-lookup"><span data-stu-id="86d90-107">FOR XML also introduces a new PATH mode.</span></span> <span data-ttu-id="86d90-108">この新しいモードで、列の値が現れる XML ツリーのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="86d90-108">This new mode specifies the path in the XML tree where a column's value appears.</span></span>  
  
 <span data-ttu-id="86d90-109">新しい **FOR XML TYPE** ディレクティブを使用すると、リレーショナル データの読み取り専用の XML ビューを SQL 構文で定義できます。</span><span class="sxs-lookup"><span data-stu-id="86d90-109">The new **FOR XML TYPE** directive can be used to define read-only XML views over relational data with SQL syntax.</span></span> <span data-ttu-id="86d90-110">このビューには、次の例で示すように SQL ステートメントおよびそれに埋め込まれた XQuery を使用してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="86d90-110">The view can be queried with SQL statements and embedded XQuery, as shown in the following example.</span></span> <span data-ttu-id="86d90-111">この SQL ビューをストアド プロシージャで参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="86d90-111">You can also refer to these SQL views in stored procedures.</span></span>  
  
## <a name="example-sql-view-returning-generated-xml-data-type"></a><span data-ttu-id="86d90-112">例: 生成された xml データ型を返す SQL ビュー</span><span class="sxs-lookup"><span data-stu-id="86d90-112">Example: SQL View Returning Generated xml Data Type</span></span>  
 <span data-ttu-id="86d90-113">次の SQL ビュー定義により、リレーショナル列 pk および XML 列から取得した著者氏名の XML ビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="86d90-113">The following SQL view definition creates an XML view over a relational column, pk, and book authors retrieved from an XML column:</span></span>  
  
```  
CREATE VIEW V (xmlVal) AS  
SELECT pk, xCol.query('/book/author')  
FROM   T  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="86d90-114">V ビューには、XML 型の単一の columnxmlVal を含む1行が含まれてい `.` ます。これは、通常のデータ型のインスタンスと同様にクエリを実行でき `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="86d90-114">The V view contains a single row with a single columnxmlVal of XML type`.` It can be queried like a regular `xml` data type instance.</span></span> <span data-ttu-id="86d90-115">たとえば、次のクエリは名が "David" の著者を返します。</span><span class="sxs-lookup"><span data-stu-id="86d90-115">For example, the following query returns the author whose first name is "David":</span></span>  
  
```  
SELECT xmlVal.query('//author[first-name = "David"]')  
FROM   V  
```  
  
 <span data-ttu-id="86d90-116">SQL ビュー定義は、注釈付きスキーマを使用して作成する XML ビューと似ている部分があります。</span><span class="sxs-lookup"><span data-stu-id="86d90-116">SQL view definitions are somewhat similar to XML views that are created by using annotated schemas.</span></span> <span data-ttu-id="86d90-117">しかし、両者には重大な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="86d90-117">However, there are important differences.</span></span> <span data-ttu-id="86d90-118">SQL ビュー定義は読み取り専用であり、埋め込みの XQuery で操作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86d90-118">The SQL view definition is read-only and must be manipulated with embedded XQuery.</span></span> <span data-ttu-id="86d90-119">XML ビューは、注釈付きスキーマを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="86d90-119">The XML views are created by using annotated schema.</span></span> <span data-ttu-id="86d90-120">また、SQL ビューが XQuery 式を適用する前に XML の結果を具体化するのに対し、XML ビューへの XPath クエリは基になるテーブルで SQL クエリを評価します。</span><span class="sxs-lookup"><span data-stu-id="86d90-120">Additionally, the SQL view materializes the XML result before applying the XQuery expression, while the XPath queries on XML views evaluate SQL queries on the underlying tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d90-121">参照</span><span class="sxs-lookup"><span data-stu-id="86d90-121">See Also</span></span>  
 [<span data-ttu-id="86d90-122">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="86d90-122">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
