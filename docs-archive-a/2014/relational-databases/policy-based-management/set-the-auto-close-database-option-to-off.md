---
title: AUTO_CLOSE データベース オプションを OFF に設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: db6cf5a3f82c3493a8732958594743104fccc968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740846"
---
# <a name="set-the-auto_close-database-option-to-off"></a><span data-ttu-id="7b114-102">AUTO_CLOSE データベース オプションを OFF に設定</span><span class="sxs-lookup"><span data-stu-id="7b114-102">Set the AUTO_CLOSE Database Option to OFF</span></span>
  <span data-ttu-id="7b114-103">このルールは、AUTO_CLOSE オプションが OFF に設定されているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="7b114-103">This rule checks whether the AUTO_ CLOSE option is set OFF.</span></span> <span data-ttu-id="7b114-104">AUTO_CLOSE が ON に設定されると、頻繁にアクセスされるデータベースでパフォーマンスが低下する場合があります。これは、接続するたびにデータベースを開いたり閉じたりするオーバーヘッドが増加するためです。</span><span class="sxs-lookup"><span data-stu-id="7b114-104">When AUTO_CLOSE is set ON, this option can cause performance degradation on frequently accessed databases because of the increased overhead of opening and closing the database after each connection.</span></span> <span data-ttu-id="7b114-105">また、AUTO_CLOSE は、接続が終了するたびにプロシージャ キャッシュをフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="7b114-105">AUTO_CLOSE also flushes the procedure cache after each connection.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="7b114-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="7b114-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="7b114-107">頻繁にアクセスされるデータベースでは、AUTO_CLOSE オプションを OFF に設定してください。</span><span class="sxs-lookup"><span data-stu-id="7b114-107">If a database is accessed frequently, set the AUTO_CLOSE option to OFF for the database.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="7b114-108">詳細情報</span><span class="sxs-lookup"><span data-stu-id="7b114-108">For More Information</span></span>  
 [<span data-ttu-id="7b114-109">ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7b114-109">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a><span data-ttu-id="7b114-110">参照</span><span class="sxs-lookup"><span data-stu-id="7b114-110">See Also</span></span>  
 [<span data-ttu-id="7b114-111">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="7b114-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
