---
title: AUTO_SHRINK データベース オプションを OFF に設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 42d79ed13a691c3d39a28e7ab35a740a9f613fac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740845"
---
# <a name="set-the-auto_shrink-database-option-to-off"></a><span data-ttu-id="6d07c-102">AUTO_SHRINK データベース オプションを OFF に設定</span><span class="sxs-lookup"><span data-stu-id="6d07c-102">Set the AUTO_SHRINK Database Option to OFF</span></span>
  <span data-ttu-id="6d07c-103">このルールでは、AUTO_SHRINK データベース オプションが OFF に設定されているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="6d07c-103">This rule checks whether the AUTO_SHRINK database option is set to OFF.</span></span> <span data-ttu-id="6d07c-104">データベースの圧縮と拡張により、物理的な断片化が発生することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="6d07c-104">Frequently shrinking and expanding a database can lead to physical fragmentation.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="6d07c-105">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="6d07c-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="6d07c-106">AUTO_SHRINK データベース オプションを OFF に設定します。</span><span class="sxs-lookup"><span data-stu-id="6d07c-106">Set the AUTO_SHRINK database option to OFF.</span></span> <span data-ttu-id="6d07c-107">再利用している領域が今後不要になることがわかっている場合は、データベースを手動で圧縮して領域を再利用できます。</span><span class="sxs-lookup"><span data-stu-id="6d07c-107">If you know that the space that you are reclaiming will not be needed in the future, you can reclaim the space by manually shrinking the database.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="6d07c-108">詳細情報</span><span class="sxs-lookup"><span data-stu-id="6d07c-108">For More Information</span></span>  
 <span data-ttu-id="6d07c-109">サポート技術情報の資料 [315512](https://go.microsoft.com/fwlink/?linkid=117750)</span><span class="sxs-lookup"><span data-stu-id="6d07c-109">Microsoft Knowledge Base article [315512](https://go.microsoft.com/fwlink/?linkid=117750)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d07c-110">参照</span><span class="sxs-lookup"><span data-stu-id="6d07c-110">See Also</span></span>  
 [<span data-ttu-id="6d07c-111">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="6d07c-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
