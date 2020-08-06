---
title: XSL キャッシュ (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
author: rothja
ms.author: jroth
ms.openlocfilehash: e41f247c34c1b40bedfdf6924a45afe5f63735b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716165"
---
# <a name="xsl-caching-sqlxml-40"></a><span data-ttu-id="6556f-102">XSL のキャッシュ (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6556f-102">XSL Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="6556f-103">XSL スタイル シートをキャッシュすると、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="6556f-103">Caching XSL style sheets improves performance.</span></span> <span data-ttu-id="6556f-104">XSL のキャッシュを ON に設定している場合、XSL スタイル シートは初回実行時にメモリに残るので、以降の処理でパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="6556f-104">Upon its first execution, an XSL style sheet remains in memory if XSL caching is set to ON; this improves performance for subsequent processing.</span></span> <span data-ttu-id="6556f-105">既定の設定は ON です。</span><span class="sxs-lookup"><span data-stu-id="6556f-105">The default setting is ON.</span></span>  
  
 <span data-ttu-id="6556f-106">XSL のキャッシュ サイズは、レジストリに次のキーを追加することで設定できます。</span><span class="sxs-lookup"><span data-stu-id="6556f-106">You can set the XSL cache size by adding the following key in the registry:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="6556f-107">XSL のキャッシュ サイズは、使用できるメモリと使用している XSL スタイル シートの数に基づいて設定します。</span><span class="sxs-lookup"><span data-stu-id="6556f-107">The XSL cache size should be set on the basis of the available memory and the number of XSL style sheets you are using.</span></span> <span data-ttu-id="6556f-108">**XSLCacheSize**の既定値は31です。</span><span class="sxs-lookup"><span data-stu-id="6556f-108">The default of **XSLCacheSize** size is 31.</span></span> <span data-ttu-id="6556f-109">XSL のアクセスが遅い場合はキャッシュ サイズを増やし、メモリが少ない場合はキャッシュ サイズを減らします。</span><span class="sxs-lookup"><span data-stu-id="6556f-109">You can increase the cache size if XSL access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="6556f-110">パフォーマンスを向上させるために、通常使用する XSL スタイルシートの数よりも大きい**XSLCacheSize**を設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6556f-110">For better performance, it is recommended that you set **XSLCacheSize** higher than the number of XSL style sheets you usually use.</span></span> <span data-ttu-id="6556f-111">**XSLCacheSize**が使用している xsl スタイルシートの数より小さい場合、xsl スタイルシートの数が増えるとパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="6556f-111">If **XSLCacheSize** is less than the number of XSL style sheets you have, the performance degrades as the number of XSL style sheets increases.</span></span> <span data-ttu-id="6556f-112">**XSLCacheSize**は最大128に設定できます。</span><span class="sxs-lookup"><span data-stu-id="6556f-112">The **XSLCacheSize** can be set to a maximum of 128.</span></span>  
  
 <span data-ttu-id="6556f-113">キャッシュされた XSL スタイル シートが使用されるときには、毎回 XSL ファイルの変更回数がチェックされ、更新が必要かどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="6556f-113">Every time the cached XSL style sheet is used, the modification time of the XSL file is checked to determine whether it needs to be refreshed.</span></span> <span data-ttu-id="6556f-114">これは、ディスク コピーがキャッシュ コピーより新しいためです。</span><span class="sxs-lookup"><span data-stu-id="6556f-114">This is because the disk copy is newer than the cache copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6556f-115">参照</span><span class="sxs-lookup"><span data-stu-id="6556f-115">See Also</span></span>  
 <span data-ttu-id="6556f-116">[テンプレートのキャッシュ &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="6556f-116">[Template Caching &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="6556f-117">スキーマキャッシュ &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6556f-117">Schema Caching &#40;SQLXML 4.0&#41;</span></span>](schema-caching-sqlxml-4-0.md)  
  
  
