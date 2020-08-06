---
title: テンプレートのキャッシュ (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: rothja
ms.author: jroth
ms.openlocfilehash: b2ea8a539086ada1b15abbb9cff4f838af45818c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640842"
---
# <a name="template-caching-sqlxml-40"></a><span data-ttu-id="a1d4b-102">テンプレートのキャッシュ (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a1d4b-102">Template Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="a1d4b-103">テンプレートをキャッシュすると、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-103">Template caching significantly improves performance.</span></span> <span data-ttu-id="a1d4b-104">テンプレートのキャッシュを設定している場合、テンプレートは初回実行時にメモリに残るので、</span><span class="sxs-lookup"><span data-stu-id="a1d4b-104">If template caching is set, the template remains in memory upon its first execution.</span></span> <span data-ttu-id="a1d4b-105">以降のテンプレート実行でパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-105">This improves the performance for the subsequent execution of the template.</span></span>  
  
 <span data-ttu-id="a1d4b-106">テンプレートのキャッシュ サイズは、レジストリに次のキーを追加することで設定できます。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-106">You can set the template cache size by adding the following key in the registry:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="a1d4b-107">テンプレートのサイズは、使用できるメモリと使用しているテンプレートの数に基づいて設定します。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-107">The template size should be set on the basis of the available memory and the number of templates you are using.</span></span> <span data-ttu-id="a1d4b-108">**TemplateCacheSize**の既定値は31です。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-108">The default of **TemplateCacheSize** size is 31.</span></span> <span data-ttu-id="a1d4b-109">テンプレートのアクセスが遅い場合はキャッシュ サイズを増やし、メモリが少ない場合はキャッシュ サイズを減らします。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-109">You can increase the cache size if template access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="a1d4b-110">パフォーマンスを向上させるために、通常使用するテンプレートの数より**TemplateCacheSize**を設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-110">For better performance, it is recommended that you set **TemplateCacheSize** higher than the number of templates you usually use.</span></span> <span data-ttu-id="a1d4b-111">**TemlateCacheSize**がテンプレートの数より少ない場合、テンプレートの数が増えるにつれてパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-111">If **TemlateCacheSize** is less than the number of templates you have, performance degrades as the number of templates increase.</span></span> <span data-ttu-id="a1d4b-112">**TemplateCacheSize**は最大128に設定できます。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-112">The **TemplateCacheSize** can be set to a maximum of 128.</span></span>  
  
 <span data-ttu-id="a1d4b-113">キャッシュされたテンプレートが使用されるときには、毎回テンプレート ファイルの変更回数がチェックされ、更新が必要がどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-113">Every time a cached template is used, the modification time of the template file is checked to see whether it needs to be refreshed.</span></span> <span data-ttu-id="a1d4b-114">これは、ディスク コピーがキャッシュ コピーより新しいためです。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-114">This is because the disk copy is newer than the cache copy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1d4b-115">テンプレートのパラメーターとコマンド プロパティはキャッシュされません。</span><span class="sxs-lookup"><span data-stu-id="a1d4b-115">Template parameters and command properties are not cached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d4b-116">参照</span><span class="sxs-lookup"><span data-stu-id="a1d4b-116">See Also</span></span>  
 <span data-ttu-id="a1d4b-117">[スキーマキャッシュ &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="a1d4b-117">[Schema Caching &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="a1d4b-118">XSL キャッシュ &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a1d4b-118">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
  
  
