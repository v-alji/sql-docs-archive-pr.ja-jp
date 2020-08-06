---
title: IIS の旧バージョンとの互換性コンポーネントが検出されませんでした (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a5aad54a01b3840e121c6a63de0ea26f35921fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644789"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a><span data-ttu-id="d13f6-102">IIS の下位互換コンポーネントが検出されない (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="d13f6-102">IIS backward compatibility components were not detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="d13f6-103">新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL を作成するためにセットアップで使用する情報を提供する IIS コンポーネントと設定が、アップグレード アドバイザーで検出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="d13f6-103">Upgrade Advisor did not detect IIS components and settings that provide information used by Setup to create new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLS.</span></span>  
  
||  
|-|  
|<span data-ttu-id="d13f6-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="d13f6-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="d13f6-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d13f6-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d13f6-106">説明</span><span class="sxs-lookup"><span data-stu-id="d13f6-106">Description</span></span>  
 <span data-ttu-id="d13f6-107">IIS にはレポート サーバー仮想ディレクトリおよびレポート マネージャー仮想ディレクトリに関する情報を提供するコンポーネントが含まれており、これらのコンポーネントがレポート サーバー コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="d13f6-107">IIS includes components that provide information about the report server and Report Manager virtual directories, and those components are not installed on the report server computer.</span></span> <span data-ttu-id="d13f6-108">アップグレードを続行できますが、レポート サーバーまたはレポート マネージャーの URL は、アップグレードで再作成されません。</span><span class="sxs-lookup"><span data-stu-id="d13f6-108">Upgrade can continue, but URLs for the report server or Report Manager will not be recreated by upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d13f6-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="d13f6-109">Corrective Action</span></span>  
 <span data-ttu-id="d13f6-110">アップグレードの完了後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用してレポート サーバーまたはレポート マネージャーの URL を設定します。</span><span class="sxs-lookup"><span data-stu-id="d13f6-110">After upgrade finishes, use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to set the URLs for report server or Report Manager.</span></span> <span data-ttu-id="d13f6-111">IIS マネージャーを使用して、不要になった仮想ディレクトリを削除します。</span><span class="sxs-lookup"><span data-stu-id="d13f6-111">Use IIS Manager to remove the virtual directories you no longer need.</span></span>  
  
 <span data-ttu-id="d13f6-112">詳細については、オンラインブックの「 [SSRS Configuration Manager&#41;の URL &#40;構成](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)する」を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d13f6-112">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13f6-113">参照</span><span class="sxs-lookup"><span data-stu-id="d13f6-113">See Also</span></span>  
 [<span data-ttu-id="d13f6-114">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="d13f6-114">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
