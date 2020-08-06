---
title: サブスクリプションを検証する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 010b5b2e9778ccf37133b0a84796373c012290f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634376"
---
# <a name="validate-subscription"></a><span data-ttu-id="3c0dd-102">[サブスクリプションを検証する]</span><span class="sxs-lookup"><span data-stu-id="3c0dd-102">Validate Subscription</span></span>
  <span data-ttu-id="3c0dd-103">**[サブスクリプションを検証する]** ダイアログ ボックスを使用すると、サブスクリプションのマージ エージェントを次に実行するときに、マージ パブリケーションへのサブスクリプションを検証するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="3c0dd-103">Use the **Validate Subscription** dialog box to specify that a subscription to a merge publication should be validated the next time the Merge Agent for the subscription runs.</span></span> <span data-ttu-id="3c0dd-104">検証の結果はレプリケーション モニターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c0dd-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="3c0dd-105">詳しくは、「 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3c0dd-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="3c0dd-106">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でパブリケーションを右クリックし、 **[すべてのサブスクリプションの検証]** をクリックすると、マージ パブリケーションへのすべてのサブスクリプションを検証できます。</span><span class="sxs-lookup"><span data-stu-id="3c0dd-106">It is also possible to validate all subscriptions to a merge publication by right-clicking a publication in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and clicking **Validate All Subscriptions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c0dd-107">オプション</span><span class="sxs-lookup"><span data-stu-id="3c0dd-107">Options</span></span>  
 <span data-ttu-id="3c0dd-108">**[最後に検証を行った日付]**</span><span class="sxs-lookup"><span data-stu-id="3c0dd-108">**Date of the last attempted validation**</span></span>  
 <span data-ttu-id="3c0dd-109">検証が成功したかどうかに関係なく、サブスクリプションの検証を含むマージ エージェント セッションを最後に実行した日付です。</span><span class="sxs-lookup"><span data-stu-id="3c0dd-109">The date of the last Merge Agent session that included subscription validation, whether or not that validation was successful.</span></span>  
  
 <span data-ttu-id="3c0dd-110">**[最後に検証が正常終了した日付]**</span><span class="sxs-lookup"><span data-stu-id="3c0dd-110">**Date of the last successful validation**</span></span>  
 <span data-ttu-id="3c0dd-111">検証が正常終了したマージ エージェント セッションを最後に実行した日付です。</span><span class="sxs-lookup"><span data-stu-id="3c0dd-111">The date of the last Merge Agent session that included a successful subscription validation.</span></span>  
  
 <span data-ttu-id="3c0dd-112">**[このサブスクリプションを検証する]**</span><span class="sxs-lookup"><span data-stu-id="3c0dd-112">**Validate this subscription**</span></span>  
 <span data-ttu-id="3c0dd-113">選択すると、サブスクリプションを検証できます。</span><span class="sxs-lookup"><span data-stu-id="3c0dd-113">Select to validate the subscription.</span></span>  
  
 <span data-ttu-id="3c0dd-114">**[オプション]**</span><span class="sxs-lookup"><span data-stu-id="3c0dd-114">**Options**</span></span>  
 <span data-ttu-id="3c0dd-115">クリックすると、 **[サブスクリプションの検証オプション]** ダイアログ ボックスが開き、行数の検証とバイナリ チェックサムの検証のどちらを使用するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3c0dd-115">Click to access the **Subscription Validation Options** dialog box, which allows you to specify whether to use row count validation or binary checksum validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c0dd-116">参照</span><span class="sxs-lookup"><span data-stu-id="3c0dd-116">See Also</span></span>  
 [<span data-ttu-id="3c0dd-117">レプリケートされたデータの検証</span><span class="sxs-lookup"><span data-stu-id="3c0dd-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
