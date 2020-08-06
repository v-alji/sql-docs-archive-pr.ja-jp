---
title: ReportViewer コントロールを使用した Reporting Services の統合 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 18e28dbf1557bf36106b454738d0c0bfc037f2a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631672"
---
# <a name="integrating-reporting-services-using-the-reportviewer-controls"></a><span data-ttu-id="d54b6-102">ReportViewer コントロールを使用した Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="d54b6-102">Integrating Reporting Services Using the ReportViewer Controls</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="d54b6-103">に [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] は、レポート表示機能をアプリケーションに統合するための2つの ReportViewer コントロールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d54b6-103">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] provides two ReportViewer controls for integrating report viewing functionality into your applications.</span></span> <span data-ttu-id="d54b6-104">Windows フォームベース アプリケーション用のバージョンと Web フォーム アプリケーション用のバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="d54b6-104">There is a version for Windows Forms-based applications and one for Web Forms applications.</span></span> <span data-ttu-id="d54b6-105">それぞれのコントロールは同様の機能を持っていますが、別々の環境を対象にして設計されています。</span><span class="sxs-lookup"><span data-stu-id="d54b6-105">Each control provides similar functionality but each is designed to target their individual environments.</span></span> <span data-ttu-id="d54b6-106">どちらのコントロールも、レポートサーバーに配置されたレポート (リモート処理モード) または [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がインストールされていないコンピューター (ローカル処理モード) にコピーされたレポートを処理できます。</span><span class="sxs-lookup"><span data-stu-id="d54b6-106">Both controls can process reports that have been deployed to a report server (remote processing mode) or have been copied to a computer where [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] has not been installed (local processing mode).</span></span>  
  
 <span data-ttu-id="d54b6-107">ReportViewer コントロールには、さまざまな画面の解像度を備えた各種デバイスに動的に適応するためのサポートは組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="d54b6-107">The ReportViewer control does not include built-in support for dynamically adapting to different devices with different screen resolutions.</span></span>  
  
## <a name="remote-processing-mode"></a><span data-ttu-id="d54b6-108">リモート処理モード</span><span class="sxs-lookup"><span data-stu-id="d54b6-108">Remote Processing Mode</span></span>  
 <span data-ttu-id="d54b6-109">リモート処理モードは、レポート サーバーに配置されたレポートの表示に推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="d54b6-109">Remote processing mode is the preferred method for viewing reports that have been deployed to a report server.</span></span> <span data-ttu-id="d54b6-110">リモート処理モードには、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="d54b6-110">Remote processing mode provides the following advantages:</span></span>  
  
-   <span data-ttu-id="d54b6-111">リモート処理では、レポート サーバーによってレポートの処理が行われるので、レポートを実行する最適なソリューションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d54b6-111">Remote processing provides an optimized solution for running reports because the report is processed by the report server.</span></span>  
  
-   <span data-ttu-id="d54b6-112">すべての処理はレポート サーバーで実行されるので、レポートの要求は、スケールアウト配置では複数のレポート サーバーで、スケール アップ シナリオでは複数のプロセッサを持つサーバーで処理できます。</span><span class="sxs-lookup"><span data-stu-id="d54b6-112">Because all processing is handled by the report server, a report request can be processed by multiple report servers in a scale-out deployment or a server that has multiple processors in a scale-up scenario.</span></span>  
  
 <span data-ttu-id="d54b6-113">また、リモート モードで実行されるレポートでは、すべての表示拡張機能やデータ拡張機能など、レポート サーバーの機能をすべて利用できます。</span><span class="sxs-lookup"><span data-stu-id="d54b6-113">In addition, reports run in remote mode can utilize the full functionality of the report server including all rendering and data extensions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d54b6-114">ReportViewer コントロールをリモート処理モードで実行しているときに使用可能な拡張機能の一覧は、レポート サーバーにインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のエディションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d54b6-114">The list of extensions available to the ReportViewer control when it is running in remote processing mode depends on the edition of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that is installed on the report server.</span></span>  
  
## <a name="local-processing-mode"></a><span data-ttu-id="d54b6-115">ローカル処理モード</span><span class="sxs-lookup"><span data-stu-id="d54b6-115">Local Processing Mode</span></span>  
 <span data-ttu-id="d54b6-116">ローカル処理モードでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がインストールされていない場合にレポートを表示するための別の方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d54b6-116">Local processing mode provides an alternative method for viewing and rendering reports when [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not installed.</span></span> <span data-ttu-id="d54b6-117">リモート処理とは異なり、コントロールで利用できる機能は、レポート サーバーによって提供される機能のサブセットに限られます。</span><span class="sxs-lookup"><span data-stu-id="d54b6-117">Unlike remote processing only a subset of the functionality provided by the report server is available in the control.</span></span> <span data-ttu-id="d54b6-118">ローカル処理モードでは、データ処理はコントロールによって処理されず、ホスト アプリケーションに実装されます。</span><span class="sxs-lookup"><span data-stu-id="d54b6-118">In local processing mode, data processing is not handled by the control but rather implemented by the hosting application.</span></span> <span data-ttu-id="d54b6-119">ただし、レポートの処理はコントロール自体で行われます。</span><span class="sxs-lookup"><span data-stu-id="d54b6-119">However report processing is handled by the control itself.</span></span> <span data-ttu-id="d54b6-120">ローカル処理モードでは、PDF、Excel、Word、および画像の表示拡張機能のみが使用可能です。</span><span class="sxs-lookup"><span data-stu-id="d54b6-120">In local processing mode, only the PDF, Excel, Word, and Image rendering extensions are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54b6-121">参照</span><span class="sxs-lookup"><span data-stu-id="d54b6-121">See Also</span></span>  
 <span data-ttu-id="d54b6-122">[アプリケーションへの Reporting Services の統合](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d54b6-122">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="d54b6-123">Visual Studio を使用して SSRS レポートを作成する (ブログ)</span><span class="sxs-lookup"><span data-stu-id="d54b6-123">Create SSRS Reports Using Visual Studio (Blog)</span></span>](https://jwcooney.com/2015/01/07/ssrs-basics-set-up-visual-studio-to-write-a-new-ssrs-report/)  
  
  
