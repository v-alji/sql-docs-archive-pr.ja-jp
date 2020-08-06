---
title: カスタムレポートアイテムがレポートサーバーで検出されました (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: feacf6aa6f233f85a67b43e7b72d3a50913991bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634227"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a><span data-ttu-id="8fb2f-102">カスタム レポート アイテムがレポート サーバーで検出された (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="8fb2f-102">Custom report items were detected on the report server (Upgrade Advisor)</span></span>
  <span data-ttu-id="8fb2f-103">以前のリリースの用に作成されたカスタムレポートアイテム [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、と互換性がありません [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8fb2f-103">Custom report items that were created for previous releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are not compatible with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8fb2f-104">アップグレードを続行できますが、そのカスタム レポート アイテムを使用するレポートは想定どおりに実行されません。</span><span class="sxs-lookup"><span data-stu-id="8fb2f-104">Upgrade can continue, but reports that use the custom report item will not run as expected.</span></span> <span data-ttu-id="8fb2f-105">アップグレード アドバイザーによって、カスタム レポート アイテムが検出されました。</span><span class="sxs-lookup"><span data-stu-id="8fb2f-105">Upgrade Advisor detected custom report items.</span></span> <span data-ttu-id="8fb2f-106">アップグレードを続行できますが、アップグレードの完了後、カスタム レポート アイテム ファイルを新しいインストール フォルダーに手動で移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8fb2f-106">Upgrade can continue, but you must manually move the custom report item files to the new installation folder after upgrade completes.</span></span>  
  
||  
|-|  
|<span data-ttu-id="8fb2f-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="8fb2f-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="8fb2f-108">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8fb2f-108">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="8fb2f-109">説明</span><span class="sxs-lookup"><span data-stu-id="8fb2f-109">Description</span></span>  
 <span data-ttu-id="8fb2f-110">アップグレード アドバイザーによって、構成ファイル内にカスタム [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 拡張設定が検出されました。これは、レポート用のカスタム アセンブリが 1 つ以上インストールに含まれていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="8fb2f-110">Upgrade Advisor detected custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extension settings in the configuration files, indicating that your installation includes one or more custom assemblies for reports.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="8fb2f-111">修正措置</span><span class="sxs-lookup"><span data-stu-id="8fb2f-111">Corrective Action</span></span>  
 <span data-ttu-id="8fb2f-112">アップグレードの完了後、カスタム レポート アイテム ファイルを新しいインストール フォルダーに手動で移動します。</span><span class="sxs-lookup"><span data-stu-id="8fb2f-112">After upgrade completes, manually move the custom report item files to the new installation folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb2f-113">参照</span><span class="sxs-lookup"><span data-stu-id="8fb2f-113">See Also</span></span>  
 [<span data-ttu-id="8fb2f-114">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="8fb2f-114">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
