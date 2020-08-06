---
title: max full-text crawl range サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1dbd9e44518b6e849a06a76e21fc605172fd2ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712369"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a><span data-ttu-id="3b554-102">max full-text crawl range サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="3b554-102">max full-text crawl range Server Configuration Option</span></span>
  <span data-ttu-id="3b554-103">**max full-text crawl range** オプションは、CPU の使用率を最適化して、フル クロール中のクロールのパフォーマンスを向上させる場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="3b554-103">Use the **max full-text crawl range** option to optimize CPU utilization, which improves crawl performance during a full crawl.</span></span> <span data-ttu-id="3b554-104">このオプションを使用して、フル インデックス クロール中に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって使用されるパーティションの数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3b554-104">Using this option, you can specify the number of partitions that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should use during a full index crawl.</span></span> <span data-ttu-id="3b554-105">たとえば、CPU が多数あり、CPU の使用率が最適でない場合は、このオプションの最大値を大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="3b554-105">For example, if there are many CPUs and their utilization is not optimal, you can increase the maximum value of this option.</span></span> <span data-ttu-id="3b554-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このオプションだけでなく、テーブルの行数や CPU 数などの他の多くの要素によって、使用する実際のパーティション数を決定します。</span><span class="sxs-lookup"><span data-stu-id="3b554-106">In addition to this option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses a number of other factors, such as the number of rows in the table and the number of CPUs, to determine the actual number of partitions used.</span></span>  
  
 <span data-ttu-id="3b554-107">このオプションの既定値は 4 です。また、最小値は 1 で、最大値は 256 です。</span><span class="sxs-lookup"><span data-stu-id="3b554-107">The default value of this option is 4; the minimum value is 1, and the maximum value is 256.</span></span> <span data-ttu-id="3b554-108">このオプションを変更すると、変更後のクロールにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="3b554-108">Changes made to this option affect only subsequent crawls.</span></span> <span data-ttu-id="3b554-109">このオプションの設定を変更しても、処理中のクロールは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="3b554-109">Crawls in process will not be affected by a change in this option setting.</span></span>  
  
 <span data-ttu-id="3b554-110">**max full-text crawl range** オプションは拡張オプションです。</span><span class="sxs-lookup"><span data-stu-id="3b554-110">The **max full-text crawl range** option is an advanced option.</span></span> <span data-ttu-id="3b554-111">**sp_configure** システム ストアド プロシージャを使用して **max full-text crawl range** の設定を変更するには、 **show advanced options** を 1 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b554-111">If you are using the **sp_configure** system stored procedure to change the setting, you can change **max full-text crawl range** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="3b554-112">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="3b554-112">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b554-113">参照</span><span class="sxs-lookup"><span data-stu-id="3b554-113">See Also</span></span>  
 <span data-ttu-id="3b554-114">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3b554-114">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="3b554-115">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3b554-115">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="3b554-116">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b554-116">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
