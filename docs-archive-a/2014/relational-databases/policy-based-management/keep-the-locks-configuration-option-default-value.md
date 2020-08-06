---
title: locks 構成オプションの既定値の保持 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a1d1dcf82d9cd0ef8ef2c15cb68ef78b53a8a54a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632427"
---
# <a name="keep-the-locks-configuration-option-default-value"></a><span data-ttu-id="3ec92-102">locks 構成オプションの既定値の保持</span><span class="sxs-lookup"><span data-stu-id="3ec92-102">Keep the Locks Configuration Option Default Value</span></span>
  <span data-ttu-id="3ec92-103">このルールでは、locks 構成オプションの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="3ec92-103">This rule checks the value of the locks configuration option.</span></span> <span data-ttu-id="3ec92-104">このオプションは、使用可能なロックの最大数を決定します。</span><span class="sxs-lookup"><span data-stu-id="3ec92-104">This option determines the maximum number of available locks.</span></span> <span data-ttu-id="3ec92-105">これにより、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] がロックに使用するメモリの量が制限されます。</span><span class="sxs-lookup"><span data-stu-id="3ec92-105">This limits how much memory the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses for locks.</span></span> <span data-ttu-id="3ec92-106">既定値である 0 の場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はシステム要件の変更に基づいてロック構造を動的に割り当てたり、割り当てを解除することができます。</span><span class="sxs-lookup"><span data-stu-id="3ec92-106">The default setting of 0 enables the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to allocate and deallocate lock structures dynamically based on changing system requirements.</span></span>  
  
 <span data-ttu-id="3ec92-107">locks が 0 でない場合、指定された値を超えるとバッチ ジョブが停止し、"ロック不足" のエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3ec92-107">If locks is nonzero, batch jobs will stop, and an "out of locks" error message will be generated, if the value specified is exceeded.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="3ec92-108">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="3ec92-108">Best Practices Recommendations</span></span>  
 <span data-ttu-id="3ec92-109">sp_configure システム ストアド プロシージャを使用して次のステートメントを実行することで、locks の値を既定の設定に変更してください。</span><span class="sxs-lookup"><span data-stu-id="3ec92-109">Use the sp_configure system stored procedure to change the value of locks to its default setting by using the following statement:</span></span>  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="3ec92-110">詳細情報</span><span class="sxs-lookup"><span data-stu-id="3ec92-110">For More Information</span></span>  
 [<span data-ttu-id="3ec92-111">locks サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="3ec92-111">Configure the locks Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [<span data-ttu-id="3ec92-112">sys.dm_tran_locks &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3ec92-112">sys.dm_tran_locks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
 [<span data-ttu-id="3ec92-113">sys.dm_os_wait_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3ec92-113">sys.dm_os_wait_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)  
  
 [<span data-ttu-id="3ec92-114">サポート技術情報の資料 271509</span><span class="sxs-lookup"><span data-stu-id="3ec92-114">Microsoft Knowledge Base article 271509</span></span>](https://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a><span data-ttu-id="3ec92-115">参照</span><span class="sxs-lookup"><span data-stu-id="3ec92-115">See Also</span></span>  
 [<span data-ttu-id="3ec92-116">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="3ec92-116">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
