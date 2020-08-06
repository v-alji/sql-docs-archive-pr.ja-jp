---
title: レポートサーバー web サイトのクライアント証明書 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 563a64e695ef552a712a5678f56d38fdfbff619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640470"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a><span data-ttu-id="1c06c-102">レポート サーバー Web サイト上のクライアント証明書 (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="1c06c-102">Client certificates on the report server web site (Upgrade Advisor)</span></span>
  <span data-ttu-id="1c06c-103">アップグレード アドバイザーによって、レポート サーバー仮想ディレクトリまたはレポート マネージャー仮想ディレクトリをホストする IIS Web サイトで、1 つ以上のクライアント証明書が検出されました。</span><span class="sxs-lookup"><span data-stu-id="1c06c-103">Upgrade Advisor detected one or more client certificates on the IIS Web site that hosts the report server or Report Manager virtual directories.</span></span>  
  
||  
|-|  
|<span data-ttu-id="1c06c-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="1c06c-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="1c06c-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1c06c-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="1c06c-106">説明</span><span class="sxs-lookup"><span data-stu-id="1c06c-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="1c06c-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、ユーザーを認証するためのクライアント証明書の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1c06c-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not support the use of client certificates to authenticate users.</span></span> <span data-ttu-id="1c06c-108">アップグレードを続行できますが、クライアント証明書はアップグレード後のレポート サーバーで使用されません。</span><span class="sxs-lookup"><span data-stu-id="1c06c-108">Upgrade can continue, but client certificates will not be used by the upgraded report server.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="1c06c-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="1c06c-109">Corrective Action</span></span>  
 <span data-ttu-id="1c06c-110">クライアント証明書の認証要件に対処するには、ISA Server など個別のソリューションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c06c-110">You will have to use a separate solution such as ISA Server to ensure any client certificate authentication requirements are addressed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c06c-111">参照</span><span class="sxs-lookup"><span data-stu-id="1c06c-111">See Also</span></span>  
 [<span data-ttu-id="1c06c-112">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="1c06c-112">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
