---
title: スキーマのキャッシュ (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e36711955fa28bafd3b0996b1a02f6cd71f3c4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644382"
---
# <a name="schema-caching-sqlxml-40"></a><span data-ttu-id="61962-102">スキーマのキャッシュ (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="61962-102">Schema Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="61962-103">Microsoft SQL Server 2000 Web Release 1、Microsoft SQLXML 2.0、SQLXML 3.0 の XML のサイド バイ サイド インストールで、次のレジストリ キーを使用すると、すべてのバージョンでスキーマのキャッシュを明示的に制御できます。</span><span class="sxs-lookup"><span data-stu-id="61962-103">With a side-by-side installation of XML for Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0, and SQLXML 3.0, you can explicitly control the schema caching in all versions by using the following registry keys:</span></span>  
  
 <span data-ttu-id="61962-104">Web Release 1:</span><span class="sxs-lookup"><span data-stu-id="61962-104">Web Release 1:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 <span data-ttu-id="61962-105">SQLXML 2.0:</span><span class="sxs-lookup"><span data-stu-id="61962-105">SQLXML 2.0:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 <span data-ttu-id="61962-106">SQLXML 3.0:</span><span class="sxs-lookup"><span data-stu-id="61962-106">SQLXML 3.0:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="61962-107">サイドバイサイドインストールの詳細については、「 [SQLXML 4.0 SP1 の新機能](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61962-107">For more information about side-by-side installation, see [What's New in SQLXML 4.0 SP1](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).</span></span>  
  
 <span data-ttu-id="61962-108">スキーマをキャッシュすると、XPath クエリのパフォーマンスが大きく向上します。</span><span class="sxs-lookup"><span data-stu-id="61962-108">Schema caching significantly improves the performance of an XPath query.</span></span> <span data-ttu-id="61962-109">マッピング スキーマに対して XPath クエリを実行すると、スキーマはメモリに格納され、必要なデータ構造がメモリ内で作成されます。</span><span class="sxs-lookup"><span data-stu-id="61962-109">When an XPath query is executed against a mapping schema, the schema is stored in memory, and the necessary data structures are built in memory.</span></span> <span data-ttu-id="61962-110">スキーマのキャッシュを設定している場合、スキーマはメモリに残るので、以降の XPath クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="61962-110">If schema caching is set, the schema remains in memory, thereby improving performance for subsequent XPath queries.</span></span>  
  
 <span data-ttu-id="61962-111">スキーマのキャッシュ サイズは、レジストリに上のキーを追加することで設定できます。</span><span class="sxs-lookup"><span data-stu-id="61962-111">You can set the schema cache size by adding the above key in the registry</span></span>  
  
 <span data-ttu-id="61962-112">スキーマ サイズは、使用可能なメモリ量と、使用しているスキーマ数に基づいて設定します。</span><span class="sxs-lookup"><span data-stu-id="61962-112">The schema size is set based on the available memory and the number of schemas you are using.</span></span> <span data-ttu-id="61962-113">既定の**Schemacachesize**サイズは31です。</span><span class="sxs-lookup"><span data-stu-id="61962-113">The default **SchemaCacheSize** size is 31.</span></span> <span data-ttu-id="61962-114">**Schemacachesize**を大きく設定すると、より多くのメモリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="61962-114">If you set **SchemaCacheSize** higher, more memory is used.</span></span> <span data-ttu-id="61962-115">スキーマのアクセスが遅い場合はキャッシュ サイズを増やし、メモリが少ない場合はキャッシュ サイズを減らします。</span><span class="sxs-lookup"><span data-stu-id="61962-115">Therefore, you can increase the cache size if schema access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="61962-116">パフォーマンス上の理由から、 **Schemacachesize**は、通常使用するマッピングスキーマの数より大きい値に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61962-116">For performance reasons, it is recommended that you set **SchemaCacheSize** higher than the number of mapping schemas you usually use.</span></span> <span data-ttu-id="61962-117">スキーマの数が増えるにつれて、 **Schemacachesize**がスキーマの数より少ない場合は、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="61962-117">As the number of schemas increase, if **SchemaCacheSize** is less than the number of schemas you have, the performance degrades.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="61962-118">スキーマへの変更は約 2 分経たないとキャッシュに反映されないため、開発時はスキーマをキャッシュしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61962-118">During development, it is recommended that you do not cache the schemas, because the changes to the schemas are not reflected in the cache for about two minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61962-119">参照</span><span class="sxs-lookup"><span data-stu-id="61962-119">See Also</span></span>  
 <span data-ttu-id="61962-120">[テンプレートのキャッシュ &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="61962-120">[Template Caching &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="61962-121">XSL キャッシュ &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="61962-121">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
  
  
