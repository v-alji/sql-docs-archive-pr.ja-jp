---
title: XML データの一括読み込みの実行 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML]
- bulk load [SQLXML]
- data insertions [SQLXML]
- SQLXML, bulk loading
- XSD schemas [SQLXML], XML Bulk Load
- XDR schemas [SQLXML], XML Bulk Load
- inserting data
ms.assetid: 3708b493-322e-4f3c-9b27-441d0c0ee346
author: rothja
ms.author: jroth
ms.openlocfilehash: ec540ff082b02fa43b9abd9f294752073eb68d5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711822"
---
# <a name="performing-bulk-load-of-xml-data-sqlxml-40"></a><span data-ttu-id="f2274-102">XML データの一括読み込みの実行 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f2274-102">Performing Bulk Load of XML Data (SQLXML 4.0)</span></span>
  <span data-ttu-id="f2274-103">XML 一括読み込みはスタンドアロン COM オブジェクトであり、これを使用すると、半構造化された XML データを Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f2274-103">XML Bulk Load is a standalone COM object that allows you to load semistructured XML data into Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2274-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f2274-104">In This Section</span></span>  
 [<span data-ttu-id="f2274-105">XML 一括読み込みの概要 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f2274-105">Introduction to XML Bulk Load &#40;SQLXML 4.0&#41;</span></span>](introduction-to-xml-bulk-load-sqlxml-4-0.md)  
 <span data-ttu-id="f2274-106">XML 一括読み込みユーティリティで XML データの一括読み込みを実行する際の一般的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f2274-106">Provides general information about bulk loading XML data with the XML Bulk Load utility.</span></span> <span data-ttu-id="f2274-107">たとえば、XML データ ストリーミングや、トランザクション モードとトランザクション以外のモードでの一括読み込み操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2274-107">Topics include XML data streaming and transacted vs. nontransacted bulk load operations.</span></span>  
  
 [<span data-ttu-id="f2274-108">SQLXML 4.0&#41;&#40;レコード生成プロセス</span><span class="sxs-lookup"><span data-stu-id="f2274-108">Record Generation Process &#40;SQLXML 4.0&#41;</span></span>](record-generation-process-sqlxml-4-0.md)  
 <span data-ttu-id="f2274-109">XML 一括読み込みのレコードが生成されるプロセスと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2274-109">Describes the process and rules by which records are generated for XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="f2274-110">SQLXML 4.0 &#40;の注釈の解釈&#41;</span><span class="sxs-lookup"><span data-stu-id="f2274-110">Annotation Interpretation &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sqlxml-4-0.md)  
 <span data-ttu-id="f2274-111">XML 一括読み込みで XSD および XDR スキーマ内の注釈がどのように解釈されるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f2274-111">Describes how XML Bulk Load interprets annotations in XSD and XDR schemas.</span></span>  
  
 [<span data-ttu-id="f2274-112">SQL Server XML 一括読み込みオブジェクトモデル &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f2274-112">SQL Server XML Bulk Load Object Model &#40;SQLXML 4.0&#41;</span></span>](sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)  
 <span data-ttu-id="f2274-113">SQLXMLBulkLoad オブジェクトとそのメソッドとプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f2274-113">Describes the SQLXMLBulkLoad object and its methods and properties.</span></span>  
  
 [<span data-ttu-id="f2274-114">XML 一括読み込みの例 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f2274-114">XML Bulk Load Examples &#40;SQLXML 4.0&#41;</span></span>](xml-bulk-load-examples-sqlxml-4-0.md)  
 <span data-ttu-id="f2274-115">XML 一括読み込みを使用したコードの例を提供します。</span><span class="sxs-lookup"><span data-stu-id="f2274-115">Provides example code that uses XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="f2274-116">データ型と XML 一括読み込みの動作 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f2274-116">Data Types and XML Bulk Load Behavior &#40;SQLXML 4.0&#41;</span></span>](data-types-and-xml-bulk-load-behavior-sqlxml-4-0.md)  
 <span data-ttu-id="f2274-117">XSD と XDR での、さまざまな XML 一括読み込み動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2274-117">Describes XML Bulk Load Behavior with different types in XSD and XDR.</span></span>  
  
 [<span data-ttu-id="f2274-118">XML 一括読み込みのガイドラインと制限 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f2274-118">Guidelines and Limitations of XML Bulk Load &#40;SQLXML 4.0&#41;</span></span>](guidelines-and-limitations-of-xml-bulk-load-sqlxml-4-0.md)  
 <span data-ttu-id="f2274-119">XML 一括読み込みを扱うときに注意すべき問題をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="f2274-119">Lists some issues to be aware of when working with XML Bulk Load.</span></span>  
  
  
