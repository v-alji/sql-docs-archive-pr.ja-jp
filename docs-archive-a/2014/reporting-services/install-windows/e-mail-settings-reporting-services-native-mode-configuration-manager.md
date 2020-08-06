---
title: 電子メールの設定-Configuration Manager (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c5f276f8d6566e052ee291118eb1d1c12fbddc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716118"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a><span data-ttu-id="eadad-102">電子メールの設定 - 構成マネージャー (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="eadad-102">E-mail Settings - Configuration Manager (SSRS Native Mode)</span></span>
  <span data-ttu-id="eadad-103">このページを使用すると、レポート サーバーからのレポート サーバー電子メール配信を有効にする簡易メール転送プロトコル (SMTP) の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="eadad-103">Use this page to specify Simple Mail Transport Protocol (SMTP) settings that enable report server e-mail delivery from the report server.</span></span> <span data-ttu-id="eadad-104">レポート サーバーの電子メール配信拡張機能により、電子メール サブスクリプションを通じてレポートやレポート処理通知を配信できます。</span><span class="sxs-lookup"><span data-stu-id="eadad-104">You can use the Report Server E-Mail delivery extension to distribute reports or report processing notifications through e-mail subscriptions.</span></span> <span data-ttu-id="eadad-105">レポート サーバーの電子メール配信拡張機能を使用するには、SMTP サーバーと、差出人フィールドに使用する電子メール アドレスが必要です。</span><span class="sxs-lookup"><span data-stu-id="eadad-105">The Report Server E-Mail delivery extension requires an SMTP server and an e-mail address to use in the From: field.</span></span>  
  
 <span data-ttu-id="eadad-106">その他の構成設定を使用することで、メール サーバーのホストを限定するための設定や表示拡張機能の使用などを含め、電子メール サブスクリプションを詳細にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="eadad-106">Additional configuration settings can be used to further customize e-mail subscriptions, including settings that restrict mail server hosts and rendering extension availability.</span></span> <span data-ttu-id="eadad-107">これらの設定は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーでは指定できません。</span><span class="sxs-lookup"><span data-stu-id="eadad-107">You cannot specify these settings in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="eadad-108">追加の設定を構成するには、RSReportServer.config ファイルを手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eadad-108">To configure the additional settings, you must manually edit the RSReportServer.config file.</span></span> <span data-ttu-id="eadad-109">詳細については、オンラインブックの「[電子メール配信用のレポートサーバーの構成 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 」および「 [Reporting Services 構成ファイル](../report-server/reporting-services-configuration-files.md)」を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eadad-109">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="eadad-110">このページを開くには、Reporting Services Configuration Manager を開始し、ナビゲーションウィンドウで [**電子メールの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eadad-110">To open this page, start the Reporting Services Configuration Manager and click **E-mail Settings** in the navigation pane.</span></span> <span data-ttu-id="eadad-111">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eadad-111">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="eadad-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="eadad-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
## <a name="options"></a><span data-ttu-id="eadad-113">Options</span><span class="sxs-lookup"><span data-stu-id="eadad-113">Options</span></span>  
 <span data-ttu-id="eadad-114">**送信者アドレス**</span><span class="sxs-lookup"><span data-stu-id="eadad-114">**Sender Address**</span></span>  
 <span data-ttu-id="eadad-115">生成される電子メールの送信者フィールドに使用する電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="eadad-115">Specifies the e-mail address to use in the From: field of a generated e-mail.</span></span> <span data-ttu-id="eadad-116">SMTP サーバーからメールを送信する権限のあるユーザー アカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eadad-116">You must specify a user account that has permission to send mail from the SMTP server.</span></span>  
  
 <span data-ttu-id="eadad-117">**[現在の SMTP 配信方法]**</span><span class="sxs-lookup"><span data-stu-id="eadad-117">**Current SMTP Delivery Method**</span></span>  
 <span data-ttu-id="eadad-118">レポート サーバー電子メールが SMTP サーバーによってルーティングされるように指定します。</span><span class="sxs-lookup"><span data-stu-id="eadad-118">Specifies that report server e-mail is routed through an SMTP server.</span></span> <span data-ttu-id="eadad-119">これは、Reporting Services 構成マネージャーで指定できる唯一の配信方法です。</span><span class="sxs-lookup"><span data-stu-id="eadad-119">This is the only delivery method that you can specify in the Reporting Services Configuration Manager.</span></span>  
  
 <span data-ttu-id="eadad-120">その他の配信方法には、ローカル SMTP サービス ピックアップ ディレクトリを使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="eadad-120">An alternative delivery method is to use a local SMTP service pickup directory.</span></span> <span data-ttu-id="eadad-121">ネットワーク SMTP サービスが使用できない場合、この配信方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="eadad-121">You can use this delivery method if a network SMTP service is not available.</span></span> <span data-ttu-id="eadad-122">ローカル SMTP サービス ピックアップ ディレクトリを指定するには、RSReportServer.config ファイルを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eadad-122">To specify a local SMTP service pickup directory, you must edit the RSReportServer.config file.</span></span> <span data-ttu-id="eadad-123">この構成ファイルを編集してローカル SMTP サービス ピックアップ ディレクトリを使用すると、Reporting Services 構成マネージャーの **[現在の配信方法]** オプションが *[ローカルのピックアップ ディレクトリに送ります]* に設定されて、この配信方法が構成ファイルで指定されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="eadad-123">If you edit the configuration file to use a local SMTP service pickup directory, the Reporting Services Configuration Manager sets the **Delivery method** option to *custom* to indicate that the delivery method is specified in the configuration file.</span></span>  
  
 <span data-ttu-id="eadad-124">構成ファイルでは、`SendUsing` 構成設定を使用して配信方法を設定します。</span><span class="sxs-lookup"><span data-stu-id="eadad-124">In the configuration file, the delivery method is set through the `SendUsing` configuration setting.</span></span> <span data-ttu-id="eadad-125">設定の指定の詳細については `SendUsing` 、「[電子メール配信用にレポートサーバーを構成する &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eadad-125">For more information about specifying the `SendUsing` setting, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="eadad-126">**SMTP サーバー**</span><span class="sxs-lookup"><span data-stu-id="eadad-126">**SMTP Server**</span></span>  
 <span data-ttu-id="eadad-127">使用する SMTP サーバーまたはゲートウェイを指定します。</span><span class="sxs-lookup"><span data-stu-id="eadad-127">Specify the SMTP server or gateway to use.</span></span> <span data-ttu-id="eadad-128">ローカル サーバーまたはネットワーク上の SMTP サーバーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="eadad-128">You can use a local server or an SMTP server on your network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eadad-129">参照</span><span class="sxs-lookup"><span data-stu-id="eadad-129">See Also</span></span>  
 <span data-ttu-id="eadad-130">[SSRS Configuration Manager &#40;電子メール配信用にレポートサーバーを構成&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="eadad-130">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="eadad-131">Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;</span><span class="sxs-lookup"><span data-stu-id="eadad-131">Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
