---
title: システム データベースの対称キー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 28e25ae3-d3dc-45ec-b316-f219512a1a47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 81c657ededc694ed87df99e0739ff74b1eb9e39b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644999"
---
# <a name="symmetric-keys-on-system-databases"></a><span data-ttu-id="85df6-102">システム データベースの対称キー</span><span class="sxs-lookup"><span data-stu-id="85df6-102">Symmetric Keys on System Databases</span></span>
  <span data-ttu-id="85df6-103">このルールでは、master、msdb、model、および tempdb の各データベースにあるユーザーが作成した対称キーについて確認します。</span><span class="sxs-lookup"><span data-stu-id="85df6-103">This rule checks for user-created symmetric keys in the master, msdb, model, and tempdb databases.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="85df6-104">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="85df6-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="85df6-105">システム データベースには対称キーを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="85df6-105">Do not create symmetric keys in the system databases.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="85df6-106">詳細情報</span><span class="sxs-lookup"><span data-stu-id="85df6-106">For More Information</span></span>  
 [<span data-ttu-id="85df6-107">暗号化アルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="85df6-107">Choose an Encryption Algorithm</span></span>](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a><span data-ttu-id="85df6-108">参照</span><span class="sxs-lookup"><span data-stu-id="85df6-108">See Also</span></span>  
 [<span data-ttu-id="85df6-109">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="85df6-109">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
