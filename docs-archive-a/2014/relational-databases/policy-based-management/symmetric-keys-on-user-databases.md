---
title: ユーザー データベースの対称キー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ca0fb62ccb32ce244e1087281997dcd9929df89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634457"
---
# <a name="symmetric-keys-on-user-databases"></a><span data-ttu-id="b2f2e-102">ユーザー データベースの対称キー</span><span class="sxs-lookup"><span data-stu-id="b2f2e-102">Symmetric Keys on User Databases</span></span>
  <span data-ttu-id="b2f2e-103">このルールでは、長さが 128 バイト未満のキーが RC2 または RC4 暗号化アルゴリズムを使用していないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2f2e-103">This rule checks whether keys that have a length of less than 128 bytes do not use the RC2 or RC4 encryption algorithm.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="b2f2e-104">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="b2f2e-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="b2f2e-105">データ暗号化用の対称キーを作成する場合は、AES 128 ビット以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2f2e-105">Use AES 128 bit or larger to create symmetric keys for data encryption.</span></span> <span data-ttu-id="b2f2e-106">AES がオペレーティング システムでサポートされていない場合は、3DES を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2f2e-106">If AES is not supported by your operating system, use 3DES.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="b2f2e-107">詳細情報</span><span class="sxs-lookup"><span data-stu-id="b2f2e-107">For More Information</span></span>  
 [<span data-ttu-id="b2f2e-108">暗号化アルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="b2f2e-108">Choose an Encryption Algorithm</span></span>](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a><span data-ttu-id="b2f2e-109">参照</span><span class="sxs-lookup"><span data-stu-id="b2f2e-109">See Also</span></span>  
 [<span data-ttu-id="b2f2e-110">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="b2f2e-110">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
