---
title: アップグレード後のプラン ガイドの検証 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18cc0f93ddec46025f659bcb9489bfff3ca846ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716262"
---
# <a name="validate-plan-guides-after-upgrade"></a><span data-ttu-id="68001-102">アップグレード後のプラン ガイドの検証</span><span class="sxs-lookup"><span data-stu-id="68001-102">Validate Plan Guides After Upgrade</span></span>
  <span data-ttu-id="68001-103">アプリケーションを新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のリリースにアップグレードした場合は、プラン ガイドの定義を再評価し、テストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68001-103">We recommend re-evaluating and testing plan guide definitions when you upgrade your application to a new release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="68001-104">新しいリリースでは、パフォーマンス チューニングの要件とプラン ガイドの照合動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="68001-104">Performance tuning requirements and plan guide matching behavior may change.</span></span> <span data-ttu-id="68001-105">無効なプラン ガイドが原因でクエリが失敗することはありませんが、そのプラン ガイドは使用されずにプランがコンパイルされるので、最適な選択ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="68001-105">Although an invalid plan guide will not cause a query to fail, the plan is compiled without using the plan guide and may not be the best choice.</span></span> <span data-ttu-id="68001-106">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にデータベースをアップグレードした後は、次の作業を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68001-106">After upgrading a database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="68001-107">既存のプラン ガイドを [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) 関数を使用して検証する。</span><span class="sxs-lookup"><span data-stu-id="68001-107">Validate existing plan guides by using the [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) function.</span></span>  
  
-   <span data-ttu-id="68001-108">拡張イベントで、プラン ガイドによって不適切に生成されたプランがないか、 [Plan Guide Unsuccessful](../event-classes/plan-guide-unsuccessful-event-class.md) イベントを使用して一定期間の間監視する。</span><span class="sxs-lookup"><span data-stu-id="68001-108">Use extended events to monitor for misguided plans for some period of time by using the [Plan Guide Unsuccessful](../event-classes/plan-guide-unsuccessful-event-class.md) event.</span></span>  
  
  
