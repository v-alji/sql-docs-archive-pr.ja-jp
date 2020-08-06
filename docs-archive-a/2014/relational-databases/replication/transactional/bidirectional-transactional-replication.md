---
title: 双方向トランザクション レプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57b18dde2e7134e0ba9eb6a9b2e8f5357d171a55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641598"
---
# <a name="bidirectional-transactional-replication"></a><span data-ttu-id="18390-102">双方向トランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="18390-102">Bidirectional Transactional Replication</span></span>
  <span data-ttu-id="18390-103">双方向トランザクション レプリケーションとは、トランザクション レプリケーションの中でも特に、2 台のサーバーが互いに変更内容を交換し合うことのできるトポロジのことです。各サーバーはデータをパブリッシュすると共に、同じデータを含んだパブリケーションをもう一方のサーバーからサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="18390-103">Bidirectional transactional replication is a specific transactional replication topology that allows two servers to exchange changes with each other: each server publishes data and then subscribes to a publication with the same data from the other server.</span></span> <span data-ttu-id="18390-104">**@loopback_detection** [Sp_addsubscription &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)のパラメーターは TRUE に設定されています。これにより、変更がサブスクライバーにのみ送信され、変更がパブリッシャーに送信されることはありません。</span><span class="sxs-lookup"><span data-stu-id="18390-104">The **@loopback_detection** parameter of [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) is set to TRUE to ensure that changes are only sent to the Subscriber and do not result in the change being sent back to the Publisher.</span></span>  
  
 <span data-ttu-id="18390-105">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降では、ピア ツー ピア トランザクション レプリケーションでもこのトポロジがサポートされますが、双方向レプリケーションを使用するとパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="18390-105">In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions, this topology is also supported by peer-to-peer transactional replication, but bidirectional replication can provide improved performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18390-106">参照</span><span class="sxs-lookup"><span data-stu-id="18390-106">See Also</span></span>  
 [<span data-ttu-id="18390-107">ピア ツー ピア トランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="18390-107">Peer-to-Peer Transactional Replication</span></span>](peer-to-peer-transactional-replication.md)  
  
  
