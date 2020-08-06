---
title: レポートサーバーデータベースが構成されていない (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 072e689da3f43222396f071e607214a2ec494749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631499"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a><span data-ttu-id="75b81-102">レポート サーバー データベースが構成されていない (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="75b81-102">Report server database is not configured (Upgrade Advisor)</span></span>
  <span data-ttu-id="75b81-103">レポート サーバーの構成が不完全であるためアップグレードがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="75b81-103">Upgrade is blocked due to an incomplete report server configuration.</span></span> <span data-ttu-id="75b81-104">レポート サーバー データベースが構成されていません。</span><span class="sxs-lookup"><span data-stu-id="75b81-104">The report server database is not configured.</span></span>  
  
||  
|-|  
|<span data-ttu-id="75b81-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="75b81-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="75b81-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="75b81-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="75b81-107">説明</span><span class="sxs-lookup"><span data-stu-id="75b81-107">Description</span></span>  
 <span data-ttu-id="75b81-108">セットアップでアップグレードできるのは、完全に構成されているレポート サーバー インスタンスだけです。</span><span class="sxs-lookup"><span data-stu-id="75b81-108">Setup can only upgrade a fully configured report server instance.</span></span> <span data-ttu-id="75b81-109">続行するには、レポートサーバーデータベースを構成するか、Microsoft Windows の**コントロールパネル**を使用してインストールからレポートサーバー機能を削除する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="75b81-109">To continue, you must either configure the report server database, or use Microsoft Windows **Control Panel** to remove the report server feature from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="75b81-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を削除すると、その他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをアップグレードできるようになります。</span><span class="sxs-lookup"><span data-stu-id="75b81-110">After you remove [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can upgrade other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="75b81-111">修正措置</span><span class="sxs-lookup"><span data-stu-id="75b81-111">Corrective Action</span></span>  
 <span data-ttu-id="75b81-112">レポート サーバー データベースを構成していない場合、レポート サーバーは使用できないので、アップグレード前に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75b81-112">If you did not configure the report server database, the report server is not operational and should be removed prior to upgrade.</span></span>  
  
 <span data-ttu-id="75b81-113">のアンインストールの詳細につい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ては、「 [Reporting Services 2012 のアンインストール](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75b81-113">For additional information on uninstalling [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , see [Uninstall Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)).</span></span> <span data-ttu-id="75b81-114">このトピックでは、特定のバージョンをアンインストールする方法について説明しています。アンインストールする手順は以前のバージョンでも同様です。</span><span class="sxs-lookup"><span data-stu-id="75b81-114">the topic describes how to uninstall a specific version and the procedures are similar for previous versions as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b81-115">参照</span><span class="sxs-lookup"><span data-stu-id="75b81-115">See Also</span></span>  
 [<span data-ttu-id="75b81-116">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="75b81-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
