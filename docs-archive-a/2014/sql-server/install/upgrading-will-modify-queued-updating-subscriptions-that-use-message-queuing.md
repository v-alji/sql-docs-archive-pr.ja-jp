---
title: アップグレードすると、メッセージキューを使用するキュー更新サブスクリプションが変更されます。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d44cbad43d75634cbf8660110cc879522265c54d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742769"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a><span data-ttu-id="4bdb2-102">アップグレードすると、メッセージ キューを使用するキュー更新サブスクリプションが変更される</span><span class="sxs-lookup"><span data-stu-id="4bdb2-102">Upgrading will modify queued updating subscriptions that use Message Queuing</span></span>
  <span data-ttu-id="4bdb2-103">アップグレード アドバイザーによって、[!INCLUDE[msCoName](../../includes/msconame-md.md)] メッセージ キュー (MSMQ) を使用する 1 つ以上のキュー更新サブスクリプションが存在する可能性があることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-103">Upgrade Advisor detected that you might have one or more queued updating subscriptions that use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="4bdb2-104">レプリケーションでは、メッセージ キューがサポートされないため、キュー更新サブスクリプションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] キューを使用するように変更されます。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-104">Replication no longer supports Message Queuing; therefore, the subscriptions will be modified to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span>  
  
 <span data-ttu-id="4bdb2-105">**Sql**の値のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-105">Only a value of **sql** is allowed.</span></span> <span data-ttu-id="4bdb2-106">メッセージ キューを使用する既存のパブリケーションは、アップグレード時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] キューを使用するよう修正されます。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-106">Existing publications that use Message Queuing are modified during upgrade to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span> <span data-ttu-id="4bdb2-107">使用するアプリケーションがメッセージ キューによるキュー更新を必要とする場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] キューに対応するようにこれらのアプリケーションを記述し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-107">If you have applications that depend on queued updating using Message Queuing, these applications will have to be rewritten to accommodate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span> <span data-ttu-id="4bdb2-108">キュー更新サブスクリプションの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「トランザクション レプリケーションの更新可能なサブスクリプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-108">For more information about queued updating subscriptions, see "Updatable Subscriptions for Transactional Replication" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="4bdb2-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアップグレード中にメッセージ キュー サービスを実行していると、既存のメッセージ キュー サブスクリプション キューは削除されます。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-109">Upgrade will remove the existing Message Queuing subscription queues if the Message Queuing service is running while [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is being upgraded.</span></span>  
  
 <span data-ttu-id="4bdb2-110">メッセージ キュー サービスを実行していない場合は、アップグレード完了後にキューを手動で削除してください。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-110">If the Message Queuing service is not running, remove the queues manually after upgrade is complete.</span></span> <span data-ttu-id="4bdb2-111">キューの削除方法の詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bdb2-111">For more information about how to remove queues, see the Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdb2-112">参照</span><span class="sxs-lookup"><span data-stu-id="4bdb2-112">See Also</span></span>  
 [<span data-ttu-id="4bdb2-113">レプリケーションのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="4bdb2-113">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
