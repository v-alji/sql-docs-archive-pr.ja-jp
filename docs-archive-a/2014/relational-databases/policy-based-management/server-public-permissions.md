---
title: サーバーのパブリック権限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7913c4715f47b8105b72b1c817dbe77e52d40539
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740857"
---
# <a name="server-public-permissions"></a><span data-ttu-id="e49d7-102">サーバーのパブリック権限</span><span class="sxs-lookup"><span data-stu-id="e49d7-102">Server public Permissions</span></span>
  <span data-ttu-id="e49d7-103">このルールでは、public サーバー ロールにサーバー権限があるかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="e49d7-103">This rule determines whether the public server role has server permissions.</span></span> <span data-ttu-id="e49d7-104">サーバー上で作成されたログインは、すべて public サーバー ロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="e49d7-104">Every login that is created on the server is a member of the public server role.</span></span> <span data-ttu-id="e49d7-105">この条件が満たされる場合、サーバー上のログインにはすべてサーバー権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="e49d7-105">If this condition is met, every login on the server will have server permissions.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="e49d7-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="e49d7-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="e49d7-107">public サーバー ロールにサーバー権限を付与しないでください。</span><span class="sxs-lookup"><span data-stu-id="e49d7-107">Do not grant server permissions to the server public role.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e49d7-108">セットアップが完了する**PUBLIC**と、 `CONNECT` **専用管理者接続**以外のすべてのエンドポイントに対する権限が PUBLIC ロールに付与されます。</span><span class="sxs-lookup"><span data-stu-id="e49d7-108">After setup completes the **PUBLIC** role has `CONNECT` permission on all the endpoints except the **Dedicated Admin Connection**.</span></span> <span data-ttu-id="e49d7-109">これは正常な動作です。通常は変更しないでください</span><span class="sxs-lookup"><span data-stu-id="e49d7-109">This is normal and should not be normally changed.</span></span> <span data-ttu-id="e49d7-110">(アクセスの制御には、新しいログインの作成時に自動的に付与される `CONNECT SQL` 権限が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="e49d7-110">(Access is controlled by using the `CONNECT SQL` permission which is automatically granted when new logins are created.)</span></span>  
  
### <a name="for-more-information"></a><span data-ttu-id="e49d7-111">詳細情報</span><span class="sxs-lookup"><span data-stu-id="e49d7-111">For more information</span></span>  
 [<span data-ttu-id="e49d7-112">SQL Server の保護</span><span class="sxs-lookup"><span data-stu-id="e49d7-112">Securing SQL Server</span></span>](../security/securing-sql-server.md)  
  
  
