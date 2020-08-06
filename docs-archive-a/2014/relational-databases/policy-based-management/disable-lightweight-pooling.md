---
title: 簡易プーリングの無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13b9ccba0a3a5805dab2eec1d04cc161e6dbd6ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741910"
---
# <a name="disable-lightweight-pooling"></a><span data-ttu-id="97c83-102">簡易プーリングの無効化</span><span class="sxs-lookup"><span data-stu-id="97c83-102">Disable Lightweight Pooling</span></span>
  <span data-ttu-id="97c83-103">このルールでは、サーバーで簡易プーリングが無効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="97c83-103">This rule checks that lightweight pooling is disabled on the server.</span></span> <span data-ttu-id="97c83-104">簡易プーリングを 1 に設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はファイバー モード スケジューリングに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="97c83-104">Setting lightweightpooling to 1 causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to switch to fiber mode scheduling.</span></span> <span data-ttu-id="97c83-105">ファイバー モードは、UMS ワーカーのコンテキスト切り替えがパフォーマンスの重大なボトルネックになる状況を対象としています。</span><span class="sxs-lookup"><span data-stu-id="97c83-105">Fiber mode is intended for certain situations in which the context switching of the UMS workers is the important bottleneck in performance.</span></span> <span data-ttu-id="97c83-106">この状況はまれであるため、一般的なシステムのパフォーマンスやスケーラビリティがファイバー モードで向上することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="97c83-106">Because this is rare, fiber mode seldom improves performance or scalability on the typical system.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="97c83-107">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="97c83-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="97c83-108">簡易プーリング オプションは、十分なテストを行い、他のパフォーマンス チューニングのすべての機会が評価された後、使用環境においてコンテキストの切り替えが既知の問題である場合にのみ有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="97c83-108">The lightweightpooling option should only be enabled after thorough testing, after all other performance tuning opportunities are evaluated, and when context switching is a known issue in your environment.</span></span>  
  
 <span data-ttu-id="97c83-109">ルーチン処理にファイバー モード スケジューリングを使用することはお勧めしません。これは、コンテキストの切り替えがもたらす本来の利点が損なわれることでパフォーマンスが低下する場合があるためと、スレッド ローカル ストレージ (TLS) やスレッド所有オブジェクト (Win32 カーネル オブジェクトの一種であるミューテックスなど) を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部のコンポーネントがファイバー モードでは正常に機能しない場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="97c83-109">We recommend that you do not use fiber mode scheduling for routine operation because it can decrease performance by preventing the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that use Thread Local Storage (TLS) or thread-owned objects, such as mutexes (a kind of Win32 kernel object), cannot function correctly in fiber mode</span></span>  
  
 <span data-ttu-id="97c83-110">簡易プーリングを削除するには、次のステートメントを実行し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="97c83-110">To remove lightweight pooling, execute the following statement, and then restart the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweightpooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="97c83-111">詳細情報</span><span class="sxs-lookup"><span data-stu-id="97c83-111">For More Information</span></span>  
 [<span data-ttu-id="97c83-112">lightweight pooling サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="97c83-112">lightweight pooling Server Configuration Option</span></span>](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="97c83-113">参照</span><span class="sxs-lookup"><span data-stu-id="97c83-113">See Also</span></span>  
 [<span data-ttu-id="97c83-114">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="97c83-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
