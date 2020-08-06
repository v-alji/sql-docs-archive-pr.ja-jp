---
title: '[すべてのサブスクリプションの検証] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27a7a4f5e5c3c303d5a1cbe257c0a0e9b531e824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643227"
---
# <a name="validate-all-subscriptions"></a><span data-ttu-id="e33f0-102">[すべてのサブスクリプションの検証]</span><span class="sxs-lookup"><span data-stu-id="e33f0-102">Validate All Subscriptions</span></span>
  <span data-ttu-id="e33f0-103">**[すべてのサブスクリプションの検証]** ダイアログ ボックスを使用すると、各サブスクリプションのマージ エージェントを次に実行するときに、マージ パブリケーションへのサブスクリプションをすべて検証するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="e33f0-103">Use the **Validate All Subscriptions** dialog box to specify that all subscriptions to a merge publication should be validated the next time the Merge Agent for each subscription runs.</span></span> <span data-ttu-id="e33f0-104">検証の結果はレプリケーション モニターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e33f0-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="e33f0-105">詳しくは、「 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e33f0-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="e33f0-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサブスクリプションを右クリックし、 **[サブスクリプションの検証]** をクリックすることでも、1 つのサブスクリプションを検証することができます。</span><span class="sxs-lookup"><span data-stu-id="e33f0-106">It is also possible to validate a single subscription by right-clicking a subscription in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and clicking **Validate Subscription**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e33f0-107">オプション</span><span class="sxs-lookup"><span data-stu-id="e33f0-107">Options</span></span>  
 <span data-ttu-id="e33f0-108">**[行数のみを確認する]**</span><span class="sxs-lookup"><span data-stu-id="e33f0-108">**Verify the row counts only**</span></span>  
 <span data-ttu-id="e33f0-109">選択すると、サブスクライバー側のテーブルとパブリッシャー側のテーブルの行数が同じかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e33f0-109">Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher.</span></span> <span data-ttu-id="e33f0-110">この方法では、行の内容が一致するかどうかは確認されません。</span><span class="sxs-lookup"><span data-stu-id="e33f0-110">This method does not validate that the content of the rows matches.</span></span> <span data-ttu-id="e33f0-111">行数の確認は、データに問題があるかどうかを調べる手軽な検証方法です。</span><span class="sxs-lookup"><span data-stu-id="e33f0-111">Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.</span></span>  
  
 <span data-ttu-id="e33f0-112">**[行数を確認し、行データを評価するためにチェックサムを比較する (すべてのサブスクライバーは SQL Server 2000 以降を実行しているサーバー)]**</span><span class="sxs-lookup"><span data-stu-id="e33f0-112">**Verify the row counts and compare checksums to verify the row data**</span></span>  
 <span data-ttu-id="e33f0-113">パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。</span><span class="sxs-lookup"><span data-stu-id="e33f0-113">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="e33f0-114">行数の検証で失敗となった場合、チェックサムは実行されません。</span><span class="sxs-lookup"><span data-stu-id="e33f0-114">If the row count fails, the checksum is not performed.</span></span> <span data-ttu-id="e33f0-115">このオプションは [!INCLUDE[ssEW](../../includes/ssew-md.md)]では無効です。</span><span class="sxs-lookup"><span data-stu-id="e33f0-115">This option is not valid for [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33f0-116">参照</span><span class="sxs-lookup"><span data-stu-id="e33f0-116">See Also</span></span>  
 [<span data-ttu-id="e33f0-117">レプリケートされたデータの検証</span><span class="sxs-lookup"><span data-stu-id="e33f0-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
