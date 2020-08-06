---
title: 仮想ディレクトリが指定されていない (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e20c48d0bf58d28cb2894baa26c2e11db26fab96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640371"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a><span data-ttu-id="58382-102">仮想ディレクトリが指定されていない (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="58382-102">Virtual directories are unspecified (Upgrade Advisor)</span></span>
  <span data-ttu-id="58382-103">アップグレード アドバイザーで、レポート サーバー Web サービスまたはレポート マネージャーの仮想ディレクトリ設定が検出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="58382-103">Upgrade Advisor did not detect virtual directory settings for the Report Server Web service or Report Manager.</span></span> <span data-ttu-id="58382-104">アップグレードの完了後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してレポート サーバーの URL 予約を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58382-104">After upgrade completes, you must configure URL reservations for the report server by using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
||  
|-|  
|<span data-ttu-id="58382-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="58382-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="58382-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="58382-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="58382-107">説明</span><span class="sxs-lookup"><span data-stu-id="58382-107">Description</span></span>  
 <span data-ttu-id="58382-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールのアップグレードには、レポート サーバー Web サービスとレポート マネージャーの新しい URL の予約が含まれます。</span><span class="sxs-lookup"><span data-stu-id="58382-108">Upgrading a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation includes reserving new URLs for the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="58382-109">アップグレードするインスタンスのレポート サーバーまたはレポート マネージャーの仮想ディレクトリが、アップグレード アドバイザーによって検出されませんでした。そのため、アップグレード プロセスでは、アップグレード後のレポート サーバーの URL 予約を作成するための情報が不足しています。</span><span class="sxs-lookup"><span data-stu-id="58382-109">Upgrade Advisor did not detect virtual directories for the report server or Report Manager for the instance to be upgraded, and therefore the upgrade process has insufficient information to create URL reservations for the upgraded report server.</span></span> <span data-ttu-id="58382-110">アップグレードを続行できますが、レポート サーバー仮想ディレクトリまたはレポート マネージャー仮想ディレクトリは、アップグレード後のインストールでは未定義になります。</span><span class="sxs-lookup"><span data-stu-id="58382-110">Upgrade can continue, but the report server or Report Manager virtual directory will be undefined after the upgraded installation.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="58382-111">修正措置</span><span class="sxs-lookup"><span data-stu-id="58382-111">Corrective Action</span></span>  
 <span data-ttu-id="58382-112">アップグレードの完了後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、レポート サーバーおよびレポート マネージャーの URL を設定します。</span><span class="sxs-lookup"><span data-stu-id="58382-112">After upgrade finishes, use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to set the URLs for report server and Report Manager.</span></span> <span data-ttu-id="58382-113">IIS マネージャーを使用して、不要になった仮想ディレクトリをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="58382-113">Use IIS Manager to remove any virtual directories you no longer need.</span></span>  
  
 <span data-ttu-id="58382-114">詳細については、オンラインブックの「 [SSRS Configuration Manager&#41;の URL &#40;構成](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)する」を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="58382-114">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58382-115">参照</span><span class="sxs-lookup"><span data-stu-id="58382-115">See Also</span></span>  
 [<span data-ttu-id="58382-116">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="58382-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
