---
title: 検出された IP アドレス制限 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2028e59e91d42bfdced2d18fa6ce129dfb108302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715974"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a><span data-ttu-id="cba2d-102">IP アドレス制限が検出された (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="cba2d-102">IP address restriction detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="cba2d-103">アップグレード アドバイザーによって、1 つ以上の IP アドレス制約が、レポート サーバー仮想ディレクトリまたはレポート マネージャー仮想ディレクトリをホストする IIS Web サイトで検出されました。</span><span class="sxs-lookup"><span data-stu-id="cba2d-103">Upgrade Advisor detected one or more IP address restrictions on the IIS Web site that hosts the report server or Report Manager virtual directories.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="cba2d-104">では、IP アドレス制約のネイティブ サポートは提供されません。</span><span class="sxs-lookup"><span data-stu-id="cba2d-104">does not provide native support for IP address restrictions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="cba2d-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]な.</span><span class="sxs-lookup"><span data-stu-id="cba2d-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="cba2d-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="cba2d-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="cba2d-107">説明</span><span class="sxs-lookup"><span data-stu-id="cba2d-107">Description</span></span>  
 <span data-ttu-id="cba2d-108">セットアップでは、アップグレード後のレポート サーバー用に作成された URL に IP アドレス制限を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="cba2d-108">Setup cannot define IP address restrictions on URLs created for an upgraded report server.</span></span> <span data-ttu-id="cba2d-109">アップグレードを続行できますが、IP アドレス制限は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL に対して定義されません。</span><span class="sxs-lookup"><span data-stu-id="cba2d-109">Upgrade can continue, but IP address restrictions will not be defined on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="cba2d-110">修正措置</span><span class="sxs-lookup"><span data-stu-id="cba2d-110">Corrective Action</span></span>  
 <span data-ttu-id="cba2d-111">アップグレード後、ISA Server、ファイアウォール ソフトウェア、または別のソリューションを使用して、レポート サーバーに対する特定の IP アドレスからの要求を許可または除外してください。</span><span class="sxs-lookup"><span data-stu-id="cba2d-111">After upgrade, use ISA Server, your firewall software, or another solution to allow or exclude requests from specific IP addresses to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba2d-112">参照</span><span class="sxs-lookup"><span data-stu-id="cba2d-112">See Also</span></span>  
 [<span data-ttu-id="cba2d-113">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="cba2d-113">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
