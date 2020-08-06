---
title: アップグレードすると、SQL Server エージェントユーザープロキシアカウントが一時的な UpgradedProxyAccount | に変更されます。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2bca80580a50f2acebed1b6fbea2dec1f6458dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631482"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a><span data-ttu-id="b786b-102">アップグレードすると SQL Server エージェント ユーザーのプロキシ アカウントが一時的な UpgradedProxyAccount に変更される</span><span class="sxs-lookup"><span data-stu-id="b786b-102">Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount</span></span>
  <span data-ttu-id="b786b-103">ログ配布を有効にしたデータベース メンテナンス プランは、アップグレード後に無効になります。</span><span class="sxs-lookup"><span data-stu-id="b786b-103">Database maintenance plans that have log shipping enabled will not be enabled after upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b786b-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b786b-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b786b-105">エージェント</span><span class="sxs-lookup"><span data-stu-id="b786b-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="b786b-106">説明</span><span class="sxs-lookup"><span data-stu-id="b786b-106">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b786b-107">には新しいログ配布関数のセットが用意されており、この関数はデータベース メンテナンス プランと直接的な互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="b786b-107">provides a new set of log shipping functions that are not directly compatible with database maintenance plans.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b786b-108">修正措置</span><span class="sxs-lookup"><span data-stu-id="b786b-108">Corrective Action</span></span>  
 <span data-ttu-id="b786b-109">ログ配布関数を含むデータベース メンテナンス プランを [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] で使用していた場合は、新しい関数を使用するようにログ配布を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b786b-109">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] users that have database maintenance plans that contain log shipping functions should configure log shipping by using the new functions.</span></span> <span data-ttu-id="b786b-110">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックで「ログ配布」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="b786b-110">For more information, search on "log shipping" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b786b-111">参照</span><span class="sxs-lookup"><span data-stu-id="b786b-111">See Also</span></span>  
 <span data-ttu-id="b786b-112">[SQL Server エージェントログ配布ジョブカテゴリによってアップグレードが失敗する](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span><span class="sxs-lookup"><span data-stu-id="b786b-112">[SQL Server Agent log shipping job category causes upgrade to fail](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span></span>  
 [<span data-ttu-id="b786b-113">アップグレード後にログ配布が実行されない</span><span class="sxs-lookup"><span data-stu-id="b786b-113">Log shipping will not run after upgrading</span></span>](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  
