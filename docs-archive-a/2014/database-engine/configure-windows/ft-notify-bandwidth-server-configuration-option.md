---
title: ft notify bandwidth サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dc5839f699d55edf86c5e3e3f0eb001089a0a5dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738755"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a><span data-ttu-id="2b46e-102">ft notify bandwidth サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="2b46e-102">ft notify bandwidth Server Configuration Option</span></span>
  <span data-ttu-id="2b46e-103">**ft notify bandwidth** オプションは、小規模メモリ バッファーのプールの最大サイズを指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="2b46e-103">Use the **ft notify bandwidth** option to specify the size to which the pool of small memory buffers can grow.</span></span> <span data-ttu-id="2b46e-104">小規模メモリ バッファーのサイズは 64 KB です。</span><span class="sxs-lookup"><span data-stu-id="2b46e-104">Small memory buffers are 64 kilobytes (KB) in size.</span></span> <span data-ttu-id="2b46e-105">*max* パラメーターの値によって、小規模バッファー プールでフルテキスト メモリ マネージャーが保持する必要があるバッファーの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="2b46e-105">The *max* parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a small buffer pool.</span></span> <span data-ttu-id="2b46e-106">`max`値が0の場合、小さいバッファープールに格納できるバッファー数に上限はありません。</span><span class="sxs-lookup"><span data-stu-id="2b46e-106">If the `max` value is zero, then there is no upper limit to the number of buffers that can be in a small buffer pool.</span></span>  
  
 <span data-ttu-id="2b46e-107">**min** パラメーターによって、小規模メモリ バッファーのプールで保持する必要があるメモリ バッファーの最少数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="2b46e-107">The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of small memory buffers.</span></span> <span data-ttu-id="2b46e-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ マネージャーからの要求時に、余分なバッファー プールがすべて解放されますが、このバッファーの最少数は保持されます。</span><span class="sxs-lookup"><span data-stu-id="2b46e-108">Upon request from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained.</span></span> <span data-ttu-id="2b46e-109">ただし、 **min** の値にゼロ (0) が指定されている場合は、すべてのメモリ バッファーが解放されます。</span><span class="sxs-lookup"><span data-stu-id="2b46e-109">If, however, the **min** value specified is zero, then all memory buffers are released.</span></span>  
  
 <span data-ttu-id="2b46e-110">特定の状況では、その時点で割り当てられるバッファーの数が **min** パラメーターによって指定された値よりも少なくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="2b46e-110">Under certain circumstances the number of buffers currently allocated is less than the value specified by the **min** parameter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b46e-111">参照</span><span class="sxs-lookup"><span data-stu-id="2b46e-111">See Also</span></span>  
 <span data-ttu-id="2b46e-112">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2b46e-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="2b46e-113">[ft crawl bandwidth サーバー構成オプション](ft-crawl-bandwidth-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="2b46e-113">[ft crawl bandwidth Server Configuration Option](ft-crawl-bandwidth-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="2b46e-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2b46e-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
