---
title: '[更新可能なサブスクリプション] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 447114152365e098420f46d4b7e880e8f2907864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714145"
---
# <a name="updatable-subscriptions"></a><span data-ttu-id="847c6-102">[更新可能なサブスクリプション]</span><span class="sxs-lookup"><span data-stu-id="847c6-102">Updatable Subscriptions</span></span>
  <span data-ttu-id="847c6-103">トランザクション レプリケーションの場合、レプリケートされたデータは読み取り専用として扱う必要がありますが、更新可能なサブスクリプションを使用することにより、レプリケートされたデータを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーで変更できます。</span><span class="sxs-lookup"><span data-stu-id="847c6-103">With transactional replication, replicated data should be treated as read-only; however, you can modify replicated data at a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber by using updatable subscriptions.</span></span> <span data-ttu-id="847c6-104">サブスクライバーでデータを変更する必要がある場合は、要件に応じて次のいずれかのオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="847c6-104">If you need to modify data at the Subscriber, choose one of the following options depending on your requirements.</span></span>  
  
|<span data-ttu-id="847c6-105">更新可能なサブスクリプション タイプ</span><span class="sxs-lookup"><span data-stu-id="847c6-105">Updatable Subscription Type</span></span>|<span data-ttu-id="847c6-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="847c6-106">Requirements</span></span>|  
|---------------------------------|------------------|  
|<span data-ttu-id="847c6-107">即時更新</span><span class="sxs-lookup"><span data-stu-id="847c6-107">Immediate Updating</span></span>|<span data-ttu-id="847c6-108">サブスクライバーのデータを更新するために、パブリッシャーとサブスクライバーを接続します。</span><span class="sxs-lookup"><span data-stu-id="847c6-108">Publisher and Subscriber must be connected to update data at the Subscriber.</span></span>|  
|<span data-ttu-id="847c6-109">キュー更新</span><span class="sxs-lookup"><span data-stu-id="847c6-109">Queued Updating</span></span>|<span data-ttu-id="847c6-110">サブスクライバーのデータを更新するために、パブリッシャーとサブスクライバーを接続する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="847c6-110">Publisher and Subscriber do not have to be connected to update data at the Subscriber.</span></span> <span data-ttu-id="847c6-111">更新をオフラインで実行し、後からパブリッシャーとサブスクライバーの間で同期させることができます。</span><span class="sxs-lookup"><span data-stu-id="847c6-111">Updates can be made while offline, and later synchronized between the Publisher and Subscriber.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="847c6-112">オプション</span><span class="sxs-lookup"><span data-stu-id="847c6-112">Options</span></span>  
 <span data-ttu-id="847c6-113">**[以下のサブスクライバーの変更内容をレプリケートします]**</span><span class="sxs-lookup"><span data-stu-id="847c6-113">**Replicate Subscriber changes**</span></span>  
 <span data-ttu-id="847c6-114">更新可能にする必要のある各サブスクライバーの **[レプリケート]** 列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="847c6-114">Select the check box in the **Replicate** column for each Subscriber that should be able to make updates.</span></span> <span data-ttu-id="847c6-115">これらの更新可能なサブスクライバーに対して、 **[パブリッシャーでのコミット]** 列のドロップダウン リスト ボックスから適切なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="847c6-115">For those Subscribers that can make updates, select the appropriate option from the drop-down list box in the **Commit at Publisher** column:</span></span>  
  
-   <span data-ttu-id="847c6-116">即時更新サブスクリプションに対して **[変更を同時にコミットする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="847c6-116">Select **Simultaneously commit changes** for an immediate updating subscription.</span></span>  
  
-   <span data-ttu-id="847c6-117">キュー更新サブスクリプションに対して **[変更をキューに登録し、可能な場合はコミット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="847c6-117">Select **Queue changes and commit when possible** for a queued updating subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="847c6-118">参照</span><span class="sxs-lookup"><span data-stu-id="847c6-118">See Also</span></span>  
 <span data-ttu-id="847c6-119">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="847c6-119">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="847c6-120">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="847c6-120">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="847c6-121">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="847c6-121">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="847c6-122">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="847c6-122">Updatable Subscriptions for Transactional Replication</span></span>](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
