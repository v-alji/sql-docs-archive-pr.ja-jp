---
title: ft crawl bandwidth サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33821ff1fdbc4248c71906d8307a8164a7f64d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741238"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a><span data-ttu-id="22005-102">ft crawl bandwidth サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="22005-102">ft crawl bandwidth Server Configuration Option</span></span>
  <span data-ttu-id="22005-103">**ft crawl bandwidth** オプションを使用すると、大規模メモリ バッファーのプールを拡張するサイズを指定できます。</span><span class="sxs-lookup"><span data-stu-id="22005-103">Use the **ft crawl bandwidth** option to specify the size to which the pool of large memory buffers can grow.</span></span> <span data-ttu-id="22005-104">大規模メモリ バッファーのサイズは 4 MB です。</span><span class="sxs-lookup"><span data-stu-id="22005-104">Large memory buffers are 4 megabytes (MB) in size.</span></span> <span data-ttu-id="22005-105">**max** パラメーターの値によって、大規模バッファー プールでフルテキスト メモリ マネージャーが保持する必要があるバッファーの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="22005-105">The **max** parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a large buffer pool.</span></span> <span data-ttu-id="22005-106">**max** の値がゼロ (0) の場合、大規模バッファー プールで保持できるバッファー数に上限はありません。</span><span class="sxs-lookup"><span data-stu-id="22005-106">If the **max** value is zero, then there is no upper limit to the number of buffers that can be in a large buffer pool.</span></span>  
  
 <span data-ttu-id="22005-107">**min** パラメーターによって、大規模メモリ バッファーのプールで保持する必要があるメモリ バッファーの最少数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="22005-107">The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of large memory buffers.</span></span> <span data-ttu-id="22005-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ マネージャーからの要求時に、余分なバッファー プールがすべて解放されますが、このバッファーの最少数は保持されます。</span><span class="sxs-lookup"><span data-stu-id="22005-108">Upon request from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained.</span></span> <span data-ttu-id="22005-109">ただし、 **min** の値にゼロ (0) が指定されている場合は、すべてのメモリ バッファーが解放されます。</span><span class="sxs-lookup"><span data-stu-id="22005-109">If, however, the **min** value specified is zero, then all memory buffers are released.</span></span>  
  
 <span data-ttu-id="22005-110">特定の状況では、その時点で割り当てられるバッファーの数が **min** パラメーターによって指定された値よりも少なくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="22005-110">Under certain circumstances, the number of buffers currently allocated is less than the value specified by the **min** parameter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22005-111">参照</span><span class="sxs-lookup"><span data-stu-id="22005-111">See Also</span></span>  
 <span data-ttu-id="22005-112">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="22005-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="22005-113">[ft notify bandwidth サーバー構成オプション](ft-notify-bandwidth-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="22005-113">[ft notify bandwidth Server Configuration Option](ft-notify-bandwidth-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="22005-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22005-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
