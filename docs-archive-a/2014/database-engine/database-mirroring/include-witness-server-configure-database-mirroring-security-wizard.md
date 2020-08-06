---
title: ミラーリング監視サーバーを含める (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 314d2205463436e2182b8d1a4cc0cc972213bd5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632656"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a><span data-ttu-id="a5897-102">[ミラーリング監視サーバーを含める] (データベース ミラーリング セキュリティ構成ウィザード)</span><span class="sxs-lookup"><span data-stu-id="a5897-102">Include Witness Server (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="a5897-103">このページを使用すると、データベース ミラーリング用に、このセキュリティ構成にミラーリング監視サーバーを含めるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a5897-103">Use this page to specify whether you want to include a witness server in this security configuration for database mirroring.</span></span>  
  
 <span data-ttu-id="a5897-104">**SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**</span><span class="sxs-lookup"><span data-stu-id="a5897-104">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="a5897-105">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a5897-105">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="a5897-106">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a5897-106">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="a5897-107">Options</span><span class="sxs-lookup"><span data-stu-id="a5897-107">Options</span></span>  
 <span data-ttu-id="a5897-108">**はい**</span><span class="sxs-lookup"><span data-stu-id="a5897-108">**Yes**</span></span>  
 <span data-ttu-id="a5897-109">ミラーリング監視サーバー インスタンスをセキュリティ構成に含めるには、これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5897-109">Click to include a witness server instance in the security configuration.</span></span> <span data-ttu-id="a5897-110">ミラーリング監視サーバーは、自動フェールオーバーを伴う高い安全性モード (プリンシパル サーバー インスタンスで障害が発生した場合に、ミラー サーバー インスタンスへ自動的に処理をフェールオーバーするモード) に必要です。</span><span class="sxs-lookup"><span data-stu-id="a5897-110">The witness is necessary for high-safety mode with automatic failover, which supports automatic failover to the mirror server instance if the principal server instance fails.</span></span>  
  
 <span data-ttu-id="a5897-111">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="a5897-111">**No**</span></span>  
 <span data-ttu-id="a5897-112">ミラーリング監視サーバーを使用せずにセキュリティを構成するには、これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5897-112">Click to configure security without a witness.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5897-113">参照</span><span class="sxs-lookup"><span data-stu-id="a5897-113">See Also</span></span>  
 <span data-ttu-id="a5897-114">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="a5897-114">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="a5897-115">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a5897-115">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="a5897-116">データベース ミラーリング監視サーバー</span><span class="sxs-lookup"><span data-stu-id="a5897-116">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
