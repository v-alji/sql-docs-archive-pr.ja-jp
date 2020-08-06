---
title: PAGE_VERIFY データベース オプションを CHECKSUM に設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13296a976722390668b8ca6d901cf0dd080e5cc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740837"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a><span data-ttu-id="15eb4-102">PAGE_VERIFY データベース オプションを CHECKSUM に設定</span><span class="sxs-lookup"><span data-stu-id="15eb4-102">Set the PAGE_VERIFY Database Option to CHECKSUM</span></span>
  <span data-ttu-id="15eb4-103">このルールでは、PAGE_VERIFY データベース オプションが CHECKSUM に設定されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="15eb4-103">This rule checks whether PAGE_VERIFY database option is set to CHECKSUM.</span></span> <span data-ttu-id="15eb4-104">PAGE_VERIFY データベース オプションに対して CHECKSUM を有効にすると、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ではページをディスクに書き込む際に、ページ全体の内容のチェックサムを計算し、ページ ヘッダーに計算したチェックサムの値を格納します。</span><span class="sxs-lookup"><span data-stu-id="15eb4-104">When CHECKSUM is enabled for the PAGE_VERIFY database option, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calculates a checksum over the contents of the whole page, and stores the value in the page header when a page is written to disk.</span></span> <span data-ttu-id="15eb4-105">このページがディスクから読み取られるときに、チェックサムが再計算され、ページ ヘッダーに格納されているチェックサムの値と比較されます。</span><span class="sxs-lookup"><span data-stu-id="15eb4-105">When the page is read from disk, the checksum is recomputed and compared to the checksum value that is stored in the page header.</span></span> <span data-ttu-id="15eb4-106">これにより、高レベルなデータ ファイル整合性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="15eb4-106">This helps provide a high level of data-file integrity.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="15eb4-107">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="15eb4-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="15eb4-108">PAGE_VERIFY データベース オプションを CHECKSUM に設定します。</span><span class="sxs-lookup"><span data-stu-id="15eb4-108">Set the PAGE_VERIFY database option to CHECKSUM.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="15eb4-109">詳細情報</span><span class="sxs-lookup"><span data-stu-id="15eb4-109">For More Information</span></span>  
 [<span data-ttu-id="15eb4-110">ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15eb4-110">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
