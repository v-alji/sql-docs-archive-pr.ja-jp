---
title: XML データ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML [SQL Server]
- XML [SQL Server], about XML
ms.assetid: 6a1793c9-9856-485c-aac5-88fda62f61a8
author: rothja
ms.author: jroth
ms.openlocfilehash: 48ddec1de8492c86aecfd80ea960c4a01673c24f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633007"
---
# <a name="xml-data-sql-server"></a><span data-ttu-id="4a557-102">XML データ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4a557-102">XML Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4a557-103">は、半構造化されたデータを管理する多機能アプリケーションを開発するための強力なプラットフォームを提供します。</span><span class="sxs-lookup"><span data-stu-id="4a557-103">provides a powerful platform for developing rich applications for semi-structured data management.</span></span> <span data-ttu-id="4a557-104">XML のサポートは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのコンポーネントに統合されており、次の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="4a557-104">Support for XML is integrated into all the components in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and includes the following:</span></span>  
  
-   <span data-ttu-id="4a557-105">`xml` データ型です。</span><span class="sxs-lookup"><span data-stu-id="4a557-105">The `xml` data type.</span></span> <span data-ttu-id="4a557-106">XML 値は XML スキーマ コレクションに従って型指定できる `xml` データ型の列にネイティブに保存できます。また、型指定しない状態でも保存できます。</span><span class="sxs-lookup"><span data-stu-id="4a557-106">XML values can be stored natively in an `xml` data type column that can be typed according to a collection of XML schemas, or left untyped.</span></span> <span data-ttu-id="4a557-107">XML 列のインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4a557-107">You can index the XML column.</span></span>  
  
-   <span data-ttu-id="4a557-108">`xml` 型の列や変数に格納されている XML データに対して XQuery クエリを指定する機能</span><span class="sxs-lookup"><span data-stu-id="4a557-108">The ability to specify an XQuery query against XML data stored in columns and variables of the `xml` type.</span></span>  
  
-   <span data-ttu-id="4a557-109">OPENROWSET で XML データを一括読み込みできる拡張機能。</span><span class="sxs-lookup"><span data-stu-id="4a557-109">Enhancements to OPENROWSET to allow bulk loading of XML data.</span></span>  
  
-   <span data-ttu-id="4a557-110">XML 形式のリレーショナル データを取得する FOR XML 句。</span><span class="sxs-lookup"><span data-stu-id="4a557-110">The FOR XML clause, to retrieve relational data in XML format.</span></span>  
  
-   <span data-ttu-id="4a557-111">リレーショナル形式の XML データを取得する OPENXML 関数。</span><span class="sxs-lookup"><span data-stu-id="4a557-111">The OPENXML function, to retrieve XML data in relational format.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a557-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4a557-112">In This Section</span></span>  
 [<span data-ttu-id="4a557-113">XML データ型と列 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a557-113">XML Data Type and Columns &#40;SQL Server&#41;</span></span>](xml-data-type-and-columns-sql-server.md)  
 [<span data-ttu-id="4a557-114">XML インデックス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a557-114">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
 [<span data-ttu-id="4a557-115">XML スキーマ コレクション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a557-115">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
 [<span data-ttu-id="4a557-116">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a557-116">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
 [<span data-ttu-id="4a557-117">OPENXML &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4a557-117">OPENXML &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openxml-transact-sql)  
  
## <a name="related-content"></a><span data-ttu-id="4a557-118">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="4a557-118">Related Content</span></span>  
 [<span data-ttu-id="4a557-119">XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a557-119">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
 [<span data-ttu-id="4a557-120">XQuery 言語リファレンス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a557-120">XQuery Language Reference &#40;SQL Server&#41;</span></span>](/sql/xquery/xquery-language-reference-sql-server)  
  
