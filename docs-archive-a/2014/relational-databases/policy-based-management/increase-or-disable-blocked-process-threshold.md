---
title: blocked process threshold の増加または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a7a90aea3fa8fb4d9c423cea1ec6008b01cde883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632437"
---
# <a name="increase-or-disable-blocked-process-threshold"></a><span data-ttu-id="6d908-102">blocked process threshold の増加または無効化</span><span class="sxs-lookup"><span data-stu-id="6d908-102">Increase or Disable Blocked Process Threshold</span></span>
  <span data-ttu-id="6d908-103">このルールでは、blocked process threshold オプションが 0 (無効) に設定されているか、5 (秒) 以上の値に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6d908-103">This rules checks that the blocked process threshold option is set to 0 (disabled) or set to a value higher than or equal to 5 (seconds).</span></span> <span data-ttu-id="6d908-104">blocked process threshold オプションを 1 ～ 4 の値に設定すると、デッドロック モニターが絶えず実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6d908-104">Setting the blocked process threshold option to a value from 1 to 4 can cause the deadlock monitor to run constantly.</span></span> <span data-ttu-id="6d908-105">1 ～ 4 の値はトラブルシューティングでのみ使用し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービスの協力がない場合は長期間または実稼働環境で使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6d908-105">Values 1 to 4 should only be used for troubleshooting, and never long term or in a production environment without the assistance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="6d908-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="6d908-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="6d908-107">この問題を解決するには、blocked process threshold オプションを 5 (秒) 以上の値に設定するか、値を 0 に設定して blocked process threshold を無効にします。</span><span class="sxs-lookup"><span data-stu-id="6d908-107">To resolve this problem, set the blocked process threshold option to a value of 5 (seconds) or higher, or disable blocked process threshold by setting the value to 0.</span></span> <span data-ttu-id="6d908-108">blocked process threshold を `5` 秒に設定するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6d908-108">To set the blocked process threshold to a value of `5` seconds, execute the following statement:</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="6d908-109">詳細情報</span><span class="sxs-lookup"><span data-stu-id="6d908-109">For More Information</span></span>  
 [<span data-ttu-id="6d908-110">blocked process threshold サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="6d908-110">blocked process threshold Server Configuration Option</span></span>](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="6d908-111">参照</span><span class="sxs-lookup"><span data-stu-id="6d908-111">See Also</span></span>  
 [<span data-ttu-id="6d908-112">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="6d908-112">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
