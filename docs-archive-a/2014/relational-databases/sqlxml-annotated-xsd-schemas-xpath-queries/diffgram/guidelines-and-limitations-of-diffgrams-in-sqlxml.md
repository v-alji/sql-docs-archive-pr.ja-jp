---
title: SQLXML における Diffgram のガイドラインと制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f2901f02f8b4a8fc7b77dcb6c1cb166cb6af6ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641564"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a><span data-ttu-id="22197-102">SQLXML における DiffGram のガイドラインと制限</span><span class="sxs-lookup"><span data-stu-id="22197-102">Guidelines and Limitations of DiffGrams in SQLXML</span></span>
  <span data-ttu-id="22197-103">SQLXML 4.0 で DiffGram を使用するときには、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="22197-103">Remember the following when using DiffGrams with SQLXML 4.0:</span></span>  
  
-   <span data-ttu-id="22197-104">ph x="1" /&gt; や image のようなバイナリ ラージ オブジェクト (BLOB) 型は、DiffGram の `<diffgr:before>` ブロックでは使用しないでください。使用すると、これらがコンカレンシー制御で使用され、</span><span class="sxs-lookup"><span data-stu-id="22197-104">Binary large object (BLOB) types like `text/ntext` and images should not be used in the `<diffgr:before>` block in when working with DiffGrams, because this will include them for use in concurrency control.</span></span> <span data-ttu-id="22197-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、BLOB 型の比較の制限によって問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22197-105">This can cause problems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="22197-106">たとえば、`text` データ型の列を比較するには WHERE 句で LIKE キーワードを使用しますが、データ サイズが 8 KB を超える BLOB 型の場合、この比較は失敗します。</span><span class="sxs-lookup"><span data-stu-id="22197-106">For example, the LIKE keyword is used in the WHERE clause for comparing between columns of the `text` data type; however, comparisons will fail in the case of BLOB types where the size of the data is greater than 8K.</span></span>  
  
-   <span data-ttu-id="22197-107">`ntext` データで特殊文字を使用すると、BLOB 型の比較の制限によって、SQLXML 4.0 で問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22197-107">Special characters in `ntext` data can cause problems with SQLXML 4.0 because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="22197-108">たとえば、DiffGram の `<diffgr:before>` ブロックに "[Serializable]" を使用すると、`ntext` 型列に対するコンカレンシー チェックで操作が失敗し、次の SQLOLEDB エラー説明が返されます。</span><span class="sxs-lookup"><span data-stu-id="22197-108">For example, the use of "[Serializable]" in the `<diffgr:before>` block of a DiffGram when used in concurrency checking of a column of `ntext` type will fail with the following SQLOLEDB error description:</span></span>  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
