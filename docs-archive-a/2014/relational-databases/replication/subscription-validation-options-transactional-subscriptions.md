---
title: '[サブスクリプションの検証オプション] (トランザクション サブスクリプション) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 40a617dd1beff24f8f072f5d139bec7c1ca65f33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741754"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a><span data-ttu-id="7316e-102">[サブスクリプションの検証オプション]\(トランザクション サブスクリプション)</span><span class="sxs-lookup"><span data-stu-id="7316e-102">Subscription Validation Options (Transactional Subscriptions)</span></span>
  <span data-ttu-id="7316e-103">[**サブスクリプションの検証オプション**] ダイアログボックスを使用すると、検証で行数のみを使用するか、行数とバイナリチェックサムを使用するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7316e-103">Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only, or a row count and a binary checksum.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7316e-104">Options</span><span class="sxs-lookup"><span data-stu-id="7316e-104">Options</span></span>  
 <span data-ttu-id="7316e-105">**[サブスクライバーとパブリッシャーでレプリケートされたデータの行数が同じであることを確認します。]**</span><span class="sxs-lookup"><span data-stu-id="7316e-105">**Verify that the Subscriber has the same number of rows of replicated data as the Publisher**</span></span>  
 <span data-ttu-id="7316e-106">実行する行数の検証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="7316e-106">Select the type of row count validation to perform.</span></span> <span data-ttu-id="7316e-107">Oracle パブリケーションの場合、使用できるオプションは **[テーブルに直接クエリすることにより、実際の行数を計算する]** のみとなります。</span><span class="sxs-lookup"><span data-stu-id="7316e-107">For Oracle publications, the only available option is **Compute an actual row count by querying the tables directly**.</span></span>  
  
 <span data-ttu-id="7316e-108">**[行データを比較するためにチェックサムを比較する (この処理には時間がかかります)]**</span><span class="sxs-lookup"><span data-stu-id="7316e-108">**Compare checksums to verify row data**</span></span>  
 <span data-ttu-id="7316e-109">パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。</span><span class="sxs-lookup"><span data-stu-id="7316e-109">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="7316e-110">行数の検証で失敗となった場合、チェックサムは実行されません。</span><span class="sxs-lookup"><span data-stu-id="7316e-110">If the row count fails, the checksum is not performed.</span></span>  
  
 <span data-ttu-id="7316e-111">**[検証完了後にディストリビューション エージェントを停止する]**</span><span class="sxs-lookup"><span data-stu-id="7316e-111">**Stop the Distribution Agent after the validation has completed**</span></span>  
 <span data-ttu-id="7316e-112">既定では、ディストリビューション エージェントは継続的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="7316e-112">By default, the Distribution Agent runs continuously.</span></span> <span data-ttu-id="7316e-113">検証の実行後にエージェントを停止するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7316e-113">Select this option to stop the agent after validation is performed.</span></span> <span data-ttu-id="7316e-114">これにより、サブスクライバーへのデータのレプリケートを継続する前に、検証が成功したかどうかをチェックできます。</span><span class="sxs-lookup"><span data-stu-id="7316e-114">This allows you to check whether validation was successful before continuing to replicate data to the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7316e-115">参照</span><span class="sxs-lookup"><span data-stu-id="7316e-115">See Also</span></span>  
 <span data-ttu-id="7316e-116">[サブスクライバーでデータを検証する](validate-data-at-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="7316e-116">[Validate Data at the Subscriber](validate-data-at-the-subscriber.md) </span></span>  
 [<span data-ttu-id="7316e-117">レプリケートされたデータの検証</span><span class="sxs-lookup"><span data-stu-id="7316e-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
