---
title: レポートマネージャー URL (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ec43c91bb2d24bb96cc6541d93311ce6dd234ed4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642521"
---
# <a name="report-manager-url-ssrs-native-mode"></a><span data-ttu-id="25f98-102">レポート マネージャー URL (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="25f98-102">Report Manager URL (SSRS Native Mode)</span></span>
  <span data-ttu-id="25f98-103">[レポート マネージャー URL] ページを使用すると、レポート マネージャーへのアクセスに使用する URL を構成または変更できます。</span><span class="sxs-lookup"><span data-stu-id="25f98-103">Use the Report Manager URL page to configure or modify the URL used to access Report Manager.</span></span> <span data-ttu-id="25f98-104">既定では、レポート マネージャーの URL は、レポート サーバー Web サービスの URL のプレフィックス、IP アドレス、およびポートを継承します。</span><span class="sxs-lookup"><span data-stu-id="25f98-104">By default, the Report Manager URL inherits the prefix, IP address, and port of the Report Server Web service URL.</span></span> <span data-ttu-id="25f98-105">これは、レポート マネージャーが同じレポート サーバー サービス内で実行される Web サービスへのフロントエンド アクセスを提供するためです。</span><span class="sxs-lookup"><span data-stu-id="25f98-105">This is because Report Manager provides front-end access to the Web service that runs within the same Report Server service.</span></span> <span data-ttu-id="25f98-106">サービス アプリケーションを分離し、レポート マネージャーを使用して別のコンピューター上のレポート サーバー Web サービスにアクセスする場合は、RSReportServer.config ファイルを編集して、レポート マネージャーが別のインスタンスを指すようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f98-106">If you are isolating the service applications and using Report Manager to access a Report Server Web service on a different computer, you must edit RSReportServer.config file to point Report Manager to a different instance.</span></span> <span data-ttu-id="25f98-107">リモートレポートサーバーへのレポートマネージャー接続の構成の詳細については、「 [Reporting Services Configuration Manager &#40;ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25f98-107">For more information about configuring a Report Manager connection to a remote report server, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="25f98-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="25f98-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="25f98-109">SharePoint 統合モードで動作するようにレポート サーバーを構成する場合は、レポート マネージャー URL を作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="25f98-109">If you are configuring the report server to run in SharePoint integrated mode, do not create a Report Manager URL.</span></span> <span data-ttu-id="25f98-110">レポート マネージャーは、SharePoint 統合モードで動作するレポート サーバーではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="25f98-110">Report Manager is not supported on a report server that runs in SharePoint integrated mode.</span></span> <span data-ttu-id="25f98-111">レポート マネージャー用の URL が既に存在する場合は、SharePoint 統合モードで動作するようにレポート サーバーを構成すると、この URL が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="25f98-111">If a URL already exists for Report Manager, it will become unavailable after you configure the report server to run in SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="25f98-112">このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、ナビゲーション ウィンドウで **[レポート マネージャー URL]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25f98-112">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and click **Report Manager URL** in the navigation pane.</span></span> <span data-ttu-id="25f98-113">Configuration Manager を開始する方法の詳細については、「[ネイティブモード&#41;&#40;Reporting Services Configuration Manager ](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25f98-113">For more information about how to start the Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25f98-114">レポート マネージャーが有効でない場合、このページのオプションは設定できません。</span><span class="sxs-lookup"><span data-stu-id="25f98-114">If Report Manager is not enabled, you cannot set options on this page.</span></span> <span data-ttu-id="25f98-115">レポートマネージャーの有効化の詳細については、「[ネイティブモード&#41;&#40;Reporting Services Configuration Manager ](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25f98-115">For more information about enabling Report Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="25f98-116">Options</span><span class="sxs-lookup"><span data-stu-id="25f98-116">Options</span></span>  
 <span data-ttu-id="25f98-117">**仮想ディレクトリ**</span><span class="sxs-lookup"><span data-stu-id="25f98-117">**Virtual Directory**</span></span>  
 <span data-ttu-id="25f98-118">レポート マネージャーの仮想ディレクトリ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="25f98-118">Specifies the virtual directory name for Report Manager.</span></span> <span data-ttu-id="25f98-119">仮想ディレクトリ名は、同じコンピューター上のレポート マネージャー インスタンスごとに 1 つだけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="25f98-119">You can only have one virtual directory name for each Report Manager instance on the same computer.</span></span>  
  
 <span data-ttu-id="25f98-120">**URL**</span><span class="sxs-lookup"><span data-stu-id="25f98-120">**URLs**</span></span>  
 <span data-ttu-id="25f98-121">現在のレポート マネージャー インスタンスに対して定義されている URL が表示されます。</span><span class="sxs-lookup"><span data-stu-id="25f98-121">Displays the URL defined for the current Report Manager instance.</span></span>  
  
 <span data-ttu-id="25f98-122">**詳細**</span><span class="sxs-lookup"><span data-stu-id="25f98-122">**Advanced**</span></span>  
 <span data-ttu-id="25f98-123">現在のレポート マネージャー インスタンスに対して URL を追加します。</span><span class="sxs-lookup"><span data-stu-id="25f98-123">Add an additional URL for the current Report Manager instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f98-124">参照</span><span class="sxs-lookup"><span data-stu-id="25f98-124">See Also</span></span>  
 <span data-ttu-id="25f98-125">[SSRS Configuration Manager の URL &#40;構成&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="25f98-125">[Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="25f98-126">[構成ファイルの Url &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="25f98-126">[URLs in Configuration Files  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="25f98-127">レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="25f98-127">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
