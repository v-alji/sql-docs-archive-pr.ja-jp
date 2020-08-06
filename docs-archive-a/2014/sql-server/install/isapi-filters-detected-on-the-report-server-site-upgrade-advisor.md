---
title: レポートサーバーサイトで検出された ISAPI フィルター (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bff1834ddf1b8f90787a47a8fd58a240d2b715d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740717"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a><span data-ttu-id="41cef-102">ISAPI フィルターがレポート サーバー サイトで検出された (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="41cef-102">ISAPI filters detected on the report server site (Upgrade Advisor)</span></span>
  <span data-ttu-id="41cef-103">アップグレード アドバイザーによって、レポート サーバー仮想ディレクトリおよびレポート マネージャー仮想ディレクトリをホストする Web サイトで 1 つ以上の ISAPI フィルターが検出されました。</span><span class="sxs-lookup"><span data-stu-id="41cef-103">Upgrade Advisor detected one or more ISAPI filters on the Web site that hosts the report server and Report Manager virtual directories.</span></span> <span data-ttu-id="41cef-104">ISAPI フィルターは、ではサポートされていません [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="41cef-104">ISAPI filters are not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
||  
|-|  
|<span data-ttu-id="41cef-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]な.</span><span class="sxs-lookup"><span data-stu-id="41cef-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native .</span></span>|  
  
## <a name="component"></a><span data-ttu-id="41cef-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="41cef-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="41cef-107">説明</span><span class="sxs-lookup"><span data-stu-id="41cef-107">Description</span></span>  
 <span data-ttu-id="41cef-108">アップグレードする前に、Web サイトの ISAPI フィルターが [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションで使用されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="41cef-108">Before upgrading, verify whether the ISAPI filters on the Web site are used by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications.</span></span> <span data-ttu-id="41cef-109">ISAPI フィルターが必要でない場合、レポート サーバーをアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="41cef-109">If you do not require the ISAPI filter, you can upgrade the report server.</span></span> <span data-ttu-id="41cef-110">セットアップでは、既定の URL が作成され、IIS で実行される ISAPI フィルターはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="41cef-110">Setup will create the default URLs, without support for the ISAPI filter that runs in IIS.</span></span> <span data-ttu-id="41cef-111">ISAPI フィルターが必要な場合は、ISAPI フィルターをホストする別の方法 (ISA Server の使用や、IIS での ISAPI フィルターのホストの継続など) を把握してからアップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="41cef-111">If you require the ISAPI filter, do not upgrade until you find an alternative way of hosting the ISAPI filter (for example, using ISA Server or continuing to host the ISAPI filter in IIS).</span></span> <span data-ttu-id="41cef-112">レポート サーバーでは、シナリオによっては、ISAPI フィルターの代わりとして ASP.NET HTTPModules がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="41cef-112">The report server supports ASP.NET HTTPModules as a replacement for ISAPI filters in certain scenarios.</span></span> <span data-ttu-id="41cef-113">詳細については、MSDN で ASP.NET のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="41cef-113">For more information, see the ASP.NET documentation on MSDN.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="41cef-114">修正措置</span><span class="sxs-lookup"><span data-stu-id="41cef-114">Corrective Action</span></span>  
 <span data-ttu-id="41cef-115">配置に必要な ISAPI フィルターをホストするための個別のソリューションを評価し、使用します。</span><span class="sxs-lookup"><span data-stu-id="41cef-115">Evaluate and use a separate solution for hosting ISAPI filters required by your deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41cef-116">参照</span><span class="sxs-lookup"><span data-stu-id="41cef-116">See Also</span></span>  
 [<span data-ttu-id="41cef-117">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="41cef-117">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
