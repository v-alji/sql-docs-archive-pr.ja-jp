---
title: サブスクリプションの検証 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.subscriptions.f1
helpviewer_keywords:
- Validate Subscriptions dialog box
ms.assetid: 0ca39a35-f22c-46c5-82a4-342e34bf5d1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a61e8b5417bf8312998b5051c47545b705b44c00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630887"
---
# <a name="validate-subscriptions"></a><span data-ttu-id="d668f-102">[サブスクリプションの検証]</span><span class="sxs-lookup"><span data-stu-id="d668f-102">Validate Subscriptions</span></span>
  <span data-ttu-id="d668f-103">**[サブスクリプションの検証]** ダイアログ ボックスを使用すると、各サブスクリプションのディストリビューション エージェントを次に実行するときに、トランザクション パブリケーションに対するサブスクリプションを検証するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="d668f-103">Use the **Validate Subscriptions** dialog box to specify that subscriptions to a transactional publication should be validated the next time the Distribution Agent for each subscription runs.</span></span> <span data-ttu-id="d668f-104">検証の結果はレプリケーション モニターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d668f-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="d668f-105">詳しくは、「 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d668f-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d668f-106">オプション</span><span class="sxs-lookup"><span data-stu-id="d668f-106">Options</span></span>  
 <span data-ttu-id="d668f-107">**[すべての SQL Server サブスクリプションを検証する]**</span><span class="sxs-lookup"><span data-stu-id="d668f-107">**Validate all SQL Server subscriptions**</span></span>  
 <span data-ttu-id="d668f-108">選択すると、このパブリケーションに対するすべての SQL Server サブスクリプションのデータが検証されます。</span><span class="sxs-lookup"><span data-stu-id="d668f-108">Select to validate data for all SQL Server subscriptions to this publication.</span></span>  
  
 <span data-ttu-id="d668f-109">**[以下のサブスクリプションを検証する]**</span><span class="sxs-lookup"><span data-stu-id="d668f-109">**Validate the following subscriptions**</span></span>  
 <span data-ttu-id="d668f-110">すべてのサブスクリプションを検証しない場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="d668f-110">Select if you do not want to validate all subscriptions.</span></span> <span data-ttu-id="d668f-111">検証するサブスクリプションを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="d668f-111">Select from the list the subscriptions you want to validate.</span></span>  
  
 <span data-ttu-id="d668f-112">**[検証オプション]**</span><span class="sxs-lookup"><span data-stu-id="d668f-112">**Validation Options**</span></span>  
 <span data-ttu-id="d668f-113">クリックすると、 **[サブスクリプションの検証オプション]** ダイアログ ボックスが開き、行数の検証とバイナリ チェックサムの検証のどちらを使用するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d668f-113">Click to access the **Subscription Validation Options** dialog box, which allows you to specify whether to use row count validation or binary checksum validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d668f-114">参照</span><span class="sxs-lookup"><span data-stu-id="d668f-114">See Also</span></span>  
 [<span data-ttu-id="d668f-115">レプリケートされたデータの検証</span><span class="sxs-lookup"><span data-stu-id="d668f-115">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
