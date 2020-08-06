---
title: 入れ子になった AFTER トリガーは、トリガーの入れ子が OFF の場合でも起動されます。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f91c04e8d69880b451c1479e2907cd1910e8f9c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742817"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a><span data-ttu-id="84cc7-102">トリガーの入れ子がオフになっている場合でも、入れ子になった AFTER トリガーが起動される</span><span class="sxs-lookup"><span data-stu-id="84cc7-102">Nested AFTER trigger fires even when trigger nesting is OFF</span></span>
  <span data-ttu-id="84cc7-103">アップグレード アドバイザーによって、1 つ以上のテーブルで定義されている INSTEAD OF トリガー内に入れ子になった AFTER トリガーが検出されました。</span><span class="sxs-lookup"><span data-stu-id="84cc7-103">Upgrade Advisor detected an AFTER trigger nested inside an INSTEAD OF trigger that is defined on one or more tables.</span></span> <span data-ttu-id="84cc7-104">入れ子になった AFTER トリガーは、`nested triggers` サーバー構成オプションが 0 に設定されている場合でも起動されることがあります。</span><span class="sxs-lookup"><span data-stu-id="84cc7-104">Nested AFTER triggers may fire even when the `nested triggers` server configuration option is set to 0.</span></span>  
  
## <a name="component"></a><span data-ttu-id="84cc7-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="84cc7-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="84cc7-106">説明</span><span class="sxs-lookup"><span data-stu-id="84cc7-106">Description</span></span>  
 <span data-ttu-id="84cc7-107">INSTEAD OF トリガー内で入れ子になっている最初の AFTER トリガーは、 `nested triggers` サーバー構成オプションが0に設定されている場合でも起動されます。</span><span class="sxs-lookup"><span data-stu-id="84cc7-107">The first AFTER trigger nested inside an INSTEAD OF trigger fires even if the `nested triggers` server configuration option is set to 0.</span></span> <span data-ttu-id="84cc7-108">ただし、この設定では、後続の AFTER トリガーは起動されません。</span><span class="sxs-lookup"><span data-stu-id="84cc7-108">However, under this setting, subsequent AFTER triggers do not fire.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="84cc7-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="84cc7-109">Corrective Action</span></span>  
 <span data-ttu-id="84cc7-110">アプリケーションに入れ子になったトリガーがないかどうかを調査し、`nested triggers` サーバー構成オプションが 0 に設定されている場合の新しい動作に関して、アプリケーションがビジネス ルールに従っているかどうかを判断します。その後、適切な変更を加えてください。</span><span class="sxs-lookup"><span data-stu-id="84cc7-110">Review your applications for nested triggers to determine whether the applications still comply with your business rules with regard to this new behavior when the `nested triggers` server configuration option is set to 0, and then make appropriate modifications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cc7-111">参照</span><span class="sxs-lookup"><span data-stu-id="84cc7-111">See Also</span></span>  
 <span data-ttu-id="84cc7-112">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="84cc7-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="84cc7-113">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="84cc7-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
