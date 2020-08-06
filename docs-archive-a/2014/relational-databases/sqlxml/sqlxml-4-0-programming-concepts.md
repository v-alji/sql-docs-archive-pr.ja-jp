---
title: SQLXML 4.0 プログラミング概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
- SQLXML
ms.assetid: 5a11cda2-b8a3-4453-848f-641afdaa7024
author: rothja
ms.author: jroth
ms.openlocfilehash: 90a383d2a12e073f262d24a94abe1b094509713c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642668"
---
# <a name="sqlxml-40-programming-concepts"></a><span data-ttu-id="fa28d-102">SQLXML 4.0 のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="fa28d-102">SQLXML 4.0 Programming Concepts</span></span>
  <span data-ttu-id="fa28d-103">クライアント側の XML 機能を追加し既存の機能を拡張するため、SQLXML 3.0 が Web リリースとして提供されました。この機能には、注釈付き XSD スキーマ、XML 一括読み込み、Web サービス (SOAP) サポート、アップデートグラムなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fa28d-103">SQLXML 3.0 was offered as a Web release to provide additional client-side XML functionality and enhancements to existing features, such as annotated XSD schemas, XML bulk load, Web services (SOAP) support, and updategrams.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="fa28d-104">では SQLXML 4.0 が導入され、SQLXML 3.0 と同じ機能に加えて、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] の新機能に対応するための追加の更新が提供されました。</span><span class="sxs-lookup"><span data-stu-id="fa28d-104">introduced SQLXML 4.0, which continues to deliver the same functionality as SQLXML 3.0 plus additional updates provided to accommodate new features introduced with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="fa28d-105">ここでは、SQLXML 4.0 に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-105">This section provides information about SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="fa28d-106">SQL Server で SQLXML がインストールされない</span><span class="sxs-lookup"><span data-stu-id="fa28d-106">SQLXML Is Not Installed in SQL Server</span></span>](sqlxml-is-not-installed-in-sql-server.md)  
 <span data-ttu-id="fa28d-107">SQLXML 4.0 をインストールする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-107">Describes how to install SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="fa28d-108">SQLXML 4.0 SP1 の新機能</span><span class="sxs-lookup"><span data-stu-id="fa28d-108">What's New in SQLXML 4.0 SP1</span></span>](what-s-new-in-sqlxml-4-0-sp1.md)  
 <span data-ttu-id="fa28d-109">SQLXML 4.0 での更新と機能拡張について説明し、このドキュメント内の関連項目へのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-109">Describes the updates and enhancements in SQLXML 4.0, and provides links to relevant topics in this documentation.</span></span>  
  
 [<span data-ttu-id="fa28d-110">ADO を使用した SQLXML 4.0 クエリの実行</span><span class="sxs-lookup"><span data-stu-id="fa28d-110">Using ADO to Execute SQLXML 4.0 Queries</span></span>](using-ado-to-execute-sqlxml-4-0-queries.md)  
 <span data-ttu-id="fa28d-111">SQLXML クエリに対する ADO の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-111">Describes how to use ADO for SQLXML queries.</span></span> <span data-ttu-id="fa28d-112">以前のバージョンに比べて SQLXML 4.0 では ADO がさらに重要になっています。</span><span class="sxs-lookup"><span data-stu-id="fa28d-112">ADO is more prominent in SQLXML 4.0 than in previous versions.</span></span>  
  
 [<span data-ttu-id="fa28d-113">SQLXML 4.0 での xml データ型のサポート</span><span class="sxs-lookup"><span data-stu-id="fa28d-113">xml Data Type Support in SQLXML 4.0</span></span>](xml-data-type-support-in-sqlxml-4-0.md)  
 <span data-ttu-id="fa28d-114">SQLXML 4.0 で追加された xml データ型のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-114">Describes the support for the xml data type that has been added for SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="fa28d-115">SQLXML の例を実行するための要件</span><span class="sxs-lookup"><span data-stu-id="fa28d-115">Requirements for Running SQLXML Examples</span></span>](requirements-for-running-sqlxml-examples.md)  
 <span data-ttu-id="fa28d-116">提供される SQLXML の例から実際のサンプルを作成するための要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-116">Describe the requirements for creating working samples from the SQLXML examples provided.</span></span>  
  
 [<span data-ttu-id="fa28d-117">SQLXML 4.0&#41;のクライアント側およびサーバー側の書式設定 &#40;</span><span class="sxs-lookup"><span data-stu-id="fa28d-117">Client-side and Server-side Formatting &#40;SQLXML 4.0&#41;</span></span>](formatting/client-side-and-server-side-formatting-sqlxml-4-0.md)  
 <span data-ttu-id="fa28d-118">クライアント側とサーバー側の書式設定について情報を提供し、これらを比較します。XML ドキュメントを構築する FOR XML コマンドに関する情報も提供します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-118">Provides information about and comparisons of client-side and server-side formatting, including the FOR XML command for constructing XML documents.</span></span>  
  
 [<span data-ttu-id="fa28d-119">SQLXML 4.0 における注釈付き XSD スキーマ</span><span class="sxs-lookup"><span data-stu-id="fa28d-119">Annotated XSD Schemas in SQLXML 4.0</span></span>](annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
 <span data-ttu-id="fa28d-120">SQLXML 4.0 での注釈付き XSD スキーマの使用について情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-120">Provides information about using annotated XSD schemas in SQLXML 4.0.</span></span> <span data-ttu-id="fa28d-121">レガシ アプリケーションで注釈付き XDR スキーマを使用する場合の情報も提供します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-121">Also provides information about annotated XDR schemas for use in legacy applications.</span></span>  
  
 [<span data-ttu-id="fa28d-122">SQLXML 4.0 での XPath クエリの使用</span><span class="sxs-lookup"><span data-stu-id="fa28d-122">Using XPath Queries in SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/using-xpath-queries-in-sqlxml-4-0.md)  
 <span data-ttu-id="fa28d-123">XPath 言語のサブセットを使用して、注釈付き XSD スキーマにより作成された XML ビューに対してクエリを実行する方法を説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-123">Describes how to use a subset of the XPath language to query the XML views created by an annotated XSD schema, and provides examples.</span></span>  
  
 [<span data-ttu-id="fa28d-124">SQLXML 4.0 での、アップデートグラムを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="fa28d-124">Using Updategrams to Modify Data in SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
 <span data-ttu-id="fa28d-125">XSD (または XDR) の注釈付きスキーマによって提供される XML ビューを操作し、データベース内のデータを変更するアップデートグラムについて、情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-125">Provides information about updategrams, which modify data in a database by working against the XML views provided by XSD (or XDR) annotated schemas.</span></span>  
  
 [<span data-ttu-id="fa28d-126">XML データの一括読み込みの実行 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa28d-126">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
 <span data-ttu-id="fa28d-127">SQLXML 4.0 で XML の一括読み込みを行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-127">Describes how to bulk load XML in SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="fa28d-128">SQLXML 4.0 のデータ アクセス コンポーネント</span><span class="sxs-lookup"><span data-stu-id="fa28d-128">SQLXML 4.0 Data Access Components</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/sqlxml-4-0-data-access-components-sqlxmloledb-provider.md)  
 <span data-ttu-id="fa28d-129">SQLXMLOLEDB プロバイダーについて説明し、その他の SQLXML 4.0 データ アクセス コンポーネントへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-129">Documents the SQLXMLOLEDB Provider and provides links to other SQLXML 4.0 data access components.</span></span>  
  
 [<span data-ttu-id="fa28d-130">SQLXML 4.0 の .NET Framework サポート</span><span class="sxs-lookup"><span data-stu-id="fa28d-130">SQLXML 4.0 .NET Framework Support</span></span>](../../database-engine/dev-guide/sqlxml-4-0-net-framework-support.md)  
 <span data-ttu-id="fa28d-131">.NET Framework に対する SQLXML 4.0 のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-131">Describes the SQLXML 4.0 support for the .NET Framework.</span></span>  
  
 [<span data-ttu-id="fa28d-132">SQLXML 4.0&#41;&#40;のテンプレート、XSL、およびスキーマのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="fa28d-132">Caching Templates, XSL, and Schemas &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/caching-templates-xsl-and-schemas-sqlxml-4-0.md)  
 <span data-ttu-id="fa28d-133">パフォーマンス向上のため SQLXML で提供されるキャッシュ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-133">Describes the caching functionality provided in SQLXML to improve performance.</span></span>  
  
 [<span data-ttu-id="fa28d-134">SQLXML 4.0 のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="fa28d-134">SQLXML 4.0 Security Considerations</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/security/sqlxml-4-0-security-considerations.md)  
 <span data-ttu-id="fa28d-135">SQLXML 4.0 に関連するセキュリティ問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-135">Discusses security issues relevant to SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="fa28d-136">SQLXML 4.0 のガイドラインと制限</span><span class="sxs-lookup"><span data-stu-id="fa28d-136">Guidelines and Limitations of SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/guidelines-and-limitations-of-sqlxml-4-0.md)  
 <span data-ttu-id="fa28d-137">SQLXML 4.0 で作業するときに注意すべき問題の一覧を提供します。</span><span class="sxs-lookup"><span data-stu-id="fa28d-137">Lists issues to remember when working with SQLXML 4.0.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa28d-138">参照</span><span class="sxs-lookup"><span data-stu-id="fa28d-138">See Also</span></span>  
 [<span data-ttu-id="fa28d-139">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fa28d-139">XML Data &#40;SQL Server&#41;</span></span>](../xml/xml-data-sql-server.md)  
  
  
