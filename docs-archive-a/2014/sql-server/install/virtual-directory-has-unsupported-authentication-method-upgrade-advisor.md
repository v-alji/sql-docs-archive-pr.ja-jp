---
title: 仮想ディレクトリにサポートされていない認証方法がある (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67b1c027b8ed020f65fdea7c093f6d5454f02c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640369"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a><span data-ttu-id="d33b6-102">仮想ディレクトリにサポートされていない認証方法がある (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="d33b6-102">Virtual directory has unsupported authentication method (Upgrade Advisor)</span></span>
  <span data-ttu-id="d33b6-103">アップグレード アドバイザーによって、レポート マネージャー仮想ディレクトリまたはレポート サーバー仮想ディレクトリで、サポートされていない認証方法が検出されました。</span><span class="sxs-lookup"><span data-stu-id="d33b6-103">Upgrade Advisor detected an unsupported authentication method on the Report Manager or report server virtual directory.</span></span> <span data-ttu-id="d33b6-104">アップグレードでサポートされていない認証方法には、匿名、ダイジェスト、および .NET Passport があります。</span><span class="sxs-lookup"><span data-stu-id="d33b6-104">Authentication methods that are not supported by upgrade include Anonymous, Digest, and .NET Passport.</span></span>  
  
||  
|-|  
|<span data-ttu-id="d33b6-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="d33b6-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="d33b6-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d33b6-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d33b6-107">説明</span><span class="sxs-lookup"><span data-stu-id="d33b6-107">Description</span></span>  
 <span data-ttu-id="d33b6-108">セットアップでは、次のいずれかの認証方法を使用する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールをアップグレードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d33b6-108">Setup cannot upgrade a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation that uses one of the following authentication methods</span></span>  
  
-   <span data-ttu-id="d33b6-109">匿名</span><span class="sxs-lookup"><span data-stu-id="d33b6-109">Anonymous</span></span>  
  
-   <span data-ttu-id="d33b6-110">ダイジェスト</span><span class="sxs-lookup"><span data-stu-id="d33b6-110">Digest</span></span>  
  
-   <span data-ttu-id="d33b6-111">.NET Passport</span><span class="sxs-lookup"><span data-stu-id="d33b6-111">.NET Passport</span></span>  
  
 <span data-ttu-id="d33b6-112">続行するには、インターネット インフォメーション サービス (IIS) の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 仮想ディレクトリに指定されている認証方法を変更するか、インストールを移行します。</span><span class="sxs-lookup"><span data-stu-id="d33b6-112">To continue, you can either modify the Authentication method that is specified for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] virtual directories in Internet Information Services (IIS), or you can migrate your installation.</span></span> <span data-ttu-id="d33b6-113">インストールの移行の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d33b6-113">For more information about migrating your installation, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d33b6-114">修正措置</span><span class="sxs-lookup"><span data-stu-id="d33b6-114">Corrective Action</span></span>  
 <span data-ttu-id="d33b6-115">アップグレードを続行するには、ReportServer および Reports の各仮想ディレクトリに対する IIS の認証方法を変更します。</span><span class="sxs-lookup"><span data-stu-id="d33b6-115">To continue with upgrade, modify the Authentication method in IIS for the ReportServer and Reports virtual directories.</span></span> <span data-ttu-id="d33b6-116">IIS の認証方法を変更する方法については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d33b6-116">For more information about modifying Authentication methods in IIS, see the IIS documentation.</span></span> <span data-ttu-id="d33b6-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 仮想ディレクトリに対する認証方法を変更した後、アップグレード アドバイザーを再実行して、アップグレードに関する問題がその他にないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d33b6-117">After you modify the Authentication method for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] virtual directories, re-run Upgrade Advisor to confirm that there are no other upgrade issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33b6-118">参照</span><span class="sxs-lookup"><span data-stu-id="d33b6-118">See Also</span></span>  
 [<span data-ttu-id="d33b6-119">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="d33b6-119">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
