---
title: ネットワーク パケット サイズは 8060 バイトを超えることはできない | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 01b500cbe65107767d73bc2901b6d5e028b94ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634458"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a><span data-ttu-id="59e24-102">ネットワーク パケット サイズは 8060 バイトを超えることはできない</span><span class="sxs-lookup"><span data-stu-id="59e24-102">Network Packet Size Should Not Exceed 8060 Bytes</span></span>
  <span data-ttu-id="59e24-103">sp_configure の 'network packet size' に指定された値またはログイン ユーザーのネットワーク パケット サイズが 8060 バイトを超えている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、異なるメモリ割り当て操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="59e24-103">If the value specified for sp_configure 'network packet size' or if the network packet size of any logged-in user is more than 8060 bytes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs different memory allocation operations.</span></span> <span data-ttu-id="59e24-104">これにより、バッファー プールに予約されていない、プロセスの仮想アドレス空間が増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="59e24-104">This can cause an increase in the process virtual address space that is not reserved for the buffer pool.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="59e24-105">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="59e24-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="59e24-106">ネットワーク パケット サイズが 8060 バイトを超えないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59e24-106">The network packet size should not exceed 8060 bytes.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="59e24-107">詳細情報</span><span class="sxs-lookup"><span data-stu-id="59e24-107">For More Information</span></span>  
 [<span data-ttu-id="59e24-108">サポート技術情報の資料 903002</span><span class="sxs-lookup"><span data-stu-id="59e24-108">Microsoft Knowledge Base article 903002</span></span>](https://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a><span data-ttu-id="59e24-109">参照</span><span class="sxs-lookup"><span data-stu-id="59e24-109">See Also</span></span>  
 [<span data-ttu-id="59e24-110">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="59e24-110">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
