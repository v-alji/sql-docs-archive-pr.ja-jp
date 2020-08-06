---
title: テンプレート、XSL、およびスキーマのキャッシュ (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: rothja
ms.author: jroth
ms.openlocfilehash: 4df25909cf156957908abf0691964fd66a76343a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642000"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a><span data-ttu-id="27238-102">テンプレート、XSL、およびスキーマのキャッシュ (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="27238-102">Caching Templates, XSL, and Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="27238-103">パフォーマンス向上のため、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 ではテンプレート、XSL、およびスキーマのキャッシュがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="27238-103">To improve performance, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 supports caching templates, XSL, and schemas.</span></span>  
  
 <span data-ttu-id="27238-104">SQLXML 4.0 ではすべてのスキーマとテンプレート、および (http:// または ftp:// にあるファイルを除く) XSL ファイルをキャッシュでき、</span><span class="sxs-lookup"><span data-stu-id="27238-104">All schemas, templates, and XSL files (except the files from an http:// or ftp:// location) are cached.</span></span> <span data-ttu-id="27238-105">キャッシュされたファイルは処理が実行されている間メモリに残ります。</span><span class="sxs-lookup"><span data-stu-id="27238-105">The cached files remain in memory while the process is running.</span></span> <span data-ttu-id="27238-106">処理が終了すると、すべてのキャッシュは失われます。</span><span class="sxs-lookup"><span data-stu-id="27238-106">As the process exits, all the cache is lost.</span></span> <span data-ttu-id="27238-107">したがって、クエリごとに 1 つの処理を実行する場合は、キャッシュがそれほどメリットにならない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="27238-107">Therefore, if you run one process per query, the caching benefit may not be noticeable.</span></span>  
  
 <span data-ttu-id="27238-108">ここでは、キャッシュの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="27238-108">The topics in this section provide more information about caching.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27238-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="27238-109">In This Section</span></span>  
 [<span data-ttu-id="27238-110">テンプレートのキャッシュ &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="27238-110">Template Caching &#40;SQLXML 4.0&#41;</span></span>](template-caching-sqlxml-4-0.md)  
 <span data-ttu-id="27238-111">テンプレートのキャッシュ用のレジストリ キーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="27238-111">Describes and provides a registry key for template caching.</span></span>  
  
 [<span data-ttu-id="27238-112">XSL キャッシュ &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="27238-112">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
 <span data-ttu-id="27238-113">XSL のキャッシュ用のレジストリ キーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="27238-113">Describes and provides a registry key for XSL caching.</span></span>  
  
 [<span data-ttu-id="27238-114">スキーマキャッシュ &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="27238-114">Schema Caching &#40;SQLXML 4.0&#41;</span></span>](schema-caching-sqlxml-4-0.md)  
 <span data-ttu-id="27238-115">スキーマのキャッシュに関する SQLXML サイド バイ サイド インストールについて説明し、スキーマのキャッシュ用のレジストリ キーを提供します。</span><span class="sxs-lookup"><span data-stu-id="27238-115">Discusses SQLXML side-by-side installation issues related to schema caching, and provides registry keys for schema caching.</span></span>  
  
  
