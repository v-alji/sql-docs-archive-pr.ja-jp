---
title: 電子メール配信用にレポートサーバーを構成する (SSRS Configuration Manager) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], distributing
- report servers [Reporting Services], e-mail delivery
- remote SMTP service [Reporting Services]
- distributing reports [Reporting Services], e-mail
- CDO
- Collaboration Data Objects
- SMTP settings [Reporting Services]
- e-mail [Reporting Services]
- sending reports
- mail [Reporting Services]
- local SMTP service [Reporting Services]
ms.assetid: b838f970-d11a-4239-b164-8d11f4581d83
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3122dbbb5debc90afa73ca0f8ab0d8e23d38a0ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642526"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a><span data-ttu-id="72d4b-102">電子メール配信用にレポート サーバーを構成する (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="72d4b-102">Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)</span></span>


  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="72d4b-103">には電子メール配信拡張機能があり、電子メールを使用してレポートを配布できます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-103">includes an e-mail delivery extension so that you can distribute reports through e-mail.</span></span> <span data-ttu-id="72d4b-104">電子メール サブスクリプションをどのように定義するかに応じて、配信は、通知、リンク、添付ファイル、または埋め込みレポートから構成されます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-104">Depending on how you define the e-mail subscription, a delivery might consist of a notification, link, attachment, or embedded report.</span></span> <span data-ttu-id="72d4b-105">電子メール配信拡張機能は、既存のメール サーバー テクノロジと連携して動作します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-105">The e-mail delivery extension works with your existing mail server technology.</span></span> <span data-ttu-id="72d4b-106">メール サーバーは、SMTP サーバーまたはフォワーダーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-106">The mail server must be an SMTP server or forwarder.</span></span> <span data-ttu-id="72d4b-107">レポート サーバーは、オペレーティング システムに用意されている Collaboration Data Objects (CDO) ライブラリ (cdosys.dll) を通じて SMTP サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-107">The report server connects to an SMTP server through Collaboration Data Objects (CDO) libraries (cdosys.dll) that are provided by the operating system.</span></span>  
  
 <span data-ttu-id="72d4b-108">既定では、レポート サーバーの電子メール配信拡張機能は構成されていません。</span><span class="sxs-lookup"><span data-stu-id="72d4b-108">The report server e-mail delivery extension is not configured by default.</span></span> <span data-ttu-id="72d4b-109">Reporting Services 構成マネージャーを使用して、この拡張機能の最低限の構成を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-109">You must use the Reporting Services Configuration Manager to minimally configure the extension.</span></span> <span data-ttu-id="72d4b-110">詳細なプロパティを設定するには、 `RSReportServer.config` ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-110">To set advanced properties, you must edit the `RSReportServer.config` file.</span></span> <span data-ttu-id="72d4b-111">この拡張機能を使用するようにレポート サーバーを構成できない場合は、代わりに共有フォルダーにレポートを配信できます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-111">If you cannot configure the report server to use this extension, you can deliver reports to a shared folder instead.</span></span> <span data-ttu-id="72d4b-112">詳細については、「 [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72d4b-112">For more information, see [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] <span data-ttu-id="72d4b-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード</span><span class="sxs-lookup"><span data-stu-id="72d4b-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 
  
##  <a name="configuration-requirements"></a><a name="bkmk_configuration_requirements"></a><span data-ttu-id="72d4b-114">構成の要件</span><span class="sxs-lookup"><span data-stu-id="72d4b-114">Configuration Requirements</span></span>  
  
-   <span data-ttu-id="72d4b-115">レポート サーバーの電子メール配信は Collaboration Data Objects (CDO) に実装されており、ローカルまたはリモートの簡易メール転送プロトコル (SMTP) サーバーまたは SMTP フォワーダーを必要とします。</span><span class="sxs-lookup"><span data-stu-id="72d4b-115">Report server e-mail delivery is implemented on Collaboration Data Objects (CDO) and requires a local or remote Simple Mail Transfer Protocol (SMTP) server or SMTP forwarder.</span></span> <span data-ttu-id="72d4b-116">SMTP は、一部の Windows オペレーティング システムではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="72d4b-116">SMTP is not supported on all Windows operating systems.</span></span> <span data-ttu-id="72d4b-117">Itanium ベース エディションの Windows Server 2008 を使用している場合、SMTP はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="72d4b-117">If you are using the Itanium-based edition of Windows Server 2008, SMTP is not supported.</span></span> <span data-ttu-id="72d4b-118">CDO によって提供される構成オプションの詳細については、MSDN の「 [CoClass の構成](https://go.microsoft.com/fwlink/?LinkId=98237) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72d4b-118">For more information about configuration options provided through CDO, see [Configuration CoClass](https://go.microsoft.com/fwlink/?LinkId=98237) on MSDN.</span></span>  
  
-   <span data-ttu-id="72d4b-119">レポート サーバー サービス アカウントには、メールを送信する SMTP サーバーに対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="72d4b-119">The Report Server service account must have permission on the SMTP server to send mail.</span></span>  
  
-   <span data-ttu-id="72d4b-120">電子メール配信拡張機能では、電子メール添付ファイルに UTF-8 エンコードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-120">The e-mail delivery extension uses UTF-8 encoding in e-mail attachments.</span></span> <span data-ttu-id="72d4b-121">エンコードを変更することはできません。HTML 表示拡張機能では UTF-8 だけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-121">You cannot modify the encoding; the HTML rendering extension only supports UTF-8.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72d4b-122">既定の電子メール配信拡張機能では、送信するメール メッセージのデジタル署名および暗号化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="72d4b-122">The default e-mail delivery extension does not provide support for digitally signing or encrypting outgoing mail messages.</span></span>  
  
 
  
##  <a name="configuring-a-report-server-for-local-or-remote-smtp-service"></a><a name="bkmk_configure_for_local_or_remote_SMTP"></a><span data-ttu-id="72d4b-123">ローカルまたはリモートの SMTP サービス用のレポートサーバーの構成</span><span class="sxs-lookup"><span data-stu-id="72d4b-123">Configuring a Report Server for Local or Remote SMTP Service</span></span>  
 <span data-ttu-id="72d4b-124">ローカルの SMTP サービス、あるいはリモートの SMTP サーバーまたは SMTP フォワーダーを使用して、電子メール配信をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-124">You can use a local SMTP service or a remote SMTP server or forwarder to support e-mail delivery.</span></span> <span data-ttu-id="72d4b-125">既存のリモート SMTP サーバーにアクセスできる場合は、リモート SMTP サーバーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="72d4b-125">If you have access to an existing remote SMTP server, you should consider using it.</span></span> <span data-ttu-id="72d4b-126">使用できる SMTP サーバーがない場合、または後でコンピューター接続の障害が原因と考えられるレポート配信エラーが発生した場合は、ローカル SMTP サービスを使用するように切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-126">If there is no SMTP server available or if you subsequently encounter report delivery errors that can be attributed to computer connection failures, you should switch to using a local SMTP service.</span></span> <span data-ttu-id="72d4b-127">ローカル サービスまたはリモート サービス用にレポート サーバーを構成する方法の詳細については、このトピックでさらに説明します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-127">Details about how to configure a report server for local or remote service are provided further on in this topic.</span></span>  
  
  
  
##  <a name="setting-configuration-options-for-e-mail-delivery"></a><a name="bkmk_setting_email_delivery"></a><span data-ttu-id="72d4b-128">電子メール配信の構成オプションの設定</span><span class="sxs-lookup"><span data-stu-id="72d4b-128">Setting Configuration Options for E-Mail Delivery</span></span>  
 <span data-ttu-id="72d4b-129">レポート サーバーの電子メール配信を使用するには、先に、使用する SMTP サーバーに関する情報を提供する構成値を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-129">Before you can use Report Server e-mail delivery, you must set configuration values that provide information about which SMTP server to use.</span></span>  
  
 <span data-ttu-id="72d4b-130">電子メール配信用にレポート サーバーを構成するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="72d4b-130">To configure a report server for e-mail delivery, do the following:</span></span>  
  
-   <span data-ttu-id="72d4b-131">SMTP サーバーと、電子メールを送信する権限のあるユーザー アカウントを指定するだけの場合は、Reporting Services 構成マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-131">Use the Reporting Services Configuration Manager if you are specifying just an SMTP server and a user account that has permission to send e-mail.</span></span> <span data-ttu-id="72d4b-132">これらは、レポート サーバーの電子メール配信拡張機能を構成するために最低限必要な設定です。</span><span class="sxs-lookup"><span data-stu-id="72d4b-132">These are the minimum settings that are required for configuring the Report Server e-mail delivery extension.</span></span> <span data-ttu-id="72d4b-133">詳細については、「[電子メールの設定-Configuration Manager &#40;SSRS ネイティブモード&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) 」、および「 [Reporting Services での電子メール配信](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72d4b-133">For more information, see [E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) and [E-Mail Delivery in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="72d4b-134">(省略可能) テキスト エディターを使用して、RSreportserver.config ファイルで追加の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-134">(Optionally) Use a text editor to specify additional settings in the RSreportserver.config file.</span></span> <span data-ttu-id="72d4b-135">このファイルには、レポート サーバーの電子メール配信の構成設定がすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="72d4b-135">This file contains all of the configuration settings for Report Server e-mail delivery.</span></span> <span data-ttu-id="72d4b-136">ローカル SMTP サーバーを使用する場合や、電子メールの配信を特定のホストに限定する場合は、これらのファイルで追加の設定を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-136">Specifying additional settings in these files is required if you are using a local SMTP server or if you are restricting e-mail delivery to specific hosts.</span></span> <span data-ttu-id="72d4b-137">構成ファイルの検索と変更の詳細については、SQL Server オンラインブックの「 [Reporting Services 構成ファイル &#40;RSreportserver.config&#41;の変更](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72d4b-137">For more information about finding and modifying configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72d4b-138">レポート サーバーの電子メール設定は CDO に基づいています。</span><span class="sxs-lookup"><span data-stu-id="72d4b-138">Report server e-mail settings are based on CDO.</span></span> <span data-ttu-id="72d4b-139">特定の設定に関する詳細については、CDO の製品マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="72d4b-139">If you want more detail about specific settings, you can refer to the CDO production documentation.</span></span>  
  

  
##  <a name="example-report-server-e-mail-configuration"></a><a name="bkmk_example_config_file"></a><span data-ttu-id="72d4b-140">レポートサーバーの電子メール構成の例</span><span class="sxs-lookup"><span data-stu-id="72d4b-140">Example Report Server E-Mail Configuration</span></span>  
 <span data-ttu-id="72d4b-141">次の例は、リモート SMTP サーバーに対する RSreportserver.config ファイルでの設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="72d4b-141">The following example illustrates the settings in the RSreportserver.config file for a remote SMTP server.</span></span> <span data-ttu-id="72d4b-142">設定に関する説明と有効な値については、 [ssNoVersion](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) オンライン ブックの「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onlオンライン ブックの「e or the CDO product documentation.</span><span class="sxs-lookup"><span data-stu-id="72d4b-142">To read about the setting descriptions and valid values, see [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or the CDO product documentation.</span></span>  
  
```  
<RSEmailDPConfiguration>  
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>  
     <SMTPServerPort></SMTPServerPort>  
     <SMTPAccountName></SMTPAccountName>  
     <SMTPConnectionTimeout></SMTPConnectionTimeout>  
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>  
     <SMTPUseSSL></SMTPUseSSL>  
     <SendUsing>2</SendUsing>  
     <SMTPAuthenticate></SMTPAuthenticate>  
     <From>my-rs-email-account@Adventure-Works.com</From>  
     <EmbeddedRenderFormats>  
          <RenderingExtension>MHTML</RenderingExtension>  
     </EmbeddedRenderFormats>  
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>  
     <ExcludedRenderFormats>  
          <RenderingExtension>HTMLOWC</RenderingExtension>  
          <RenderingExtension>NULL</RenderingExtension>  
     </ExcludedRenderFormats>  
     <SendEmailToUserAlias>True</SendEmailToUserAlias>  
     <DefaultHostName></DefaultHostName>  
     <PermittedHosts>  
          <HostName>Adventure-Works.com</HostName>  
          <HostName>hotmail.com</HostName>  
     </PermittedHosts>  
</RSEmailDPConfiguration>  
```  
  

  
##  <a name="configuration-options-for-setting-the-to-field-in-a-message"></a><a name="bkmk_setting_TO_field"></a><span data-ttu-id="72d4b-143">メッセージの [宛先] フィールドを設定するための構成オプション</span><span class="sxs-lookup"><span data-stu-id="72d4b-143">Configuration Options for Setting the To: Field in a Message</span></span>  
 <span data-ttu-id="72d4b-144">**個々のサブスクリプションの管理**タスクによって付与されるアクセス許可に従って作成されたユーザー定義サブスクリプションには、ドメインユーザーアカウントに基づく事前設定されたユーザー名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-144">User-defined subscriptions that are created according to the permissions granted by the **Manage individual subscriptions** task contain a pre-set user name that is based on the domain user account.</span></span> <span data-ttu-id="72d4b-145">ユーザーがサブスクリプションを作成すると、 **[宛先]** フィールドの受信者名は、サブスクリプションの作成者のドメイン ユーザー アカウントを使用して自動的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-145">When the user creates the subscription, the recipient name in the **To:** field is self-addressed using the domain user account of the person creating the subscription.</span></span>  
  
 <span data-ttu-id="72d4b-146">使用している SMTP サーバーまたはフォワーダーで、ドメイン ユーザー アカウントとは別の電子メール アカウントを利用している場合、SMTP サーバーからそのユーザーにレポートの配信が試行されたときに配信が失敗します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-146">If you are using an SMTP server or forwarder that uses e-mail accounts that are different from the domain user account, the report delivery will fail when the SMTP server tries to deliver the report to that user.</span></span>  
  
 <span data-ttu-id="72d4b-147">この問題に対処するには、ユーザーが [ **宛先** ] フィールドに名前を入力できるように構成設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-147">To workaround this issue, you can modify configuration settings that allow users to enter a name in the **To:** field:</span></span>  
  
1.  <span data-ttu-id="72d4b-148">テキスト エディターで RSReportServer.config を開きます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-148">Open RSReportServer.config with a text editor.</span></span>  
  
2.  <span data-ttu-id="72d4b-149">`SendEmailToUserAlias` を `False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-149">Set `SendEmailToUserAlias` to `False`.</span></span>  
  
3.  <span data-ttu-id="72d4b-150">`DefaultHostName` を SMTP サーバーまたはフォワーダーのドメイン ネーム システム (DNS) 名または IP アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-150">Set `DefaultHostName` to the Domain Name System (DNS) name or IP address of the SMTP server or forwarder.</span></span>  
  
4.  <span data-ttu-id="72d4b-151">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-151">Save the file.</span></span>  
  
  
  
##  <a name="configuration-options-for-remote-smtp-service"></a><a name="bkmk_options_remote_SMTP"></a><span data-ttu-id="72d4b-152">リモート SMTP サービスの構成オプション</span><span class="sxs-lookup"><span data-stu-id="72d4b-152">Configuration Options for Remote SMTP Service</span></span>  
 <span data-ttu-id="72d4b-153">レポート サーバーと SMTP サーバーまたはフォワーダーの間の接続は、次の構成設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-153">The connection between the report server and an SMTP server or forwarder is determined by the following configuration settings:</span></span>  
  
-   <span data-ttu-id="72d4b-154">`SendUsing` メッセージを送信する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-154">`SendUsing` specifies a method for sending messages.</span></span> <span data-ttu-id="72d4b-155">ネットワーク SMTP サービスまたはローカル SMTP サービスのピックアップ ディレクトリを選択できます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-155">You can choose between a network SMTP service or a local SMTP service pickup directory.</span></span> <span data-ttu-id="72d4b-156">リモート SMTP サービスを使用するには、RSReportServer.config ファイルでこの値を **2** に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-156">To use a remote SMTP service, this value must be set to **2** in the RSReportServer.config file.</span></span>  
  
-   <span data-ttu-id="72d4b-157">`SMTPServer` リモート SMTP サーバーまたはフォワーダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-157">`SMTPServer` specifies the remote SMTP server or forwarder.</span></span> <span data-ttu-id="72d4b-158">リモート SMTP サーバーまたはフォワーダーを使用している場合には、この値は必須です。</span><span class="sxs-lookup"><span data-stu-id="72d4b-158">This value is a required value if you are using a remote SMTP server or forwarder.</span></span>  
  
-   <span data-ttu-id="72d4b-159">`From` メール メッセージの **[送信者]** 行に使用する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-159">`From` sets the value that appears in the **From:** line of an e-mail message.</span></span> <span data-ttu-id="72d4b-160">リモート SMTP サーバーまたはフォワーダーを使用している場合には、この値は必須です。</span><span class="sxs-lookup"><span data-stu-id="72d4b-160">This value is a required value if you are using a remote SMTP server or forwarder.</span></span>  
  
 <span data-ttu-id="72d4b-161">リモート SMTP サービスで使用する他の値としては、次のものがあります (既定値を変更するのでない限り、これらの値をオーバーライドする必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="72d4b-161">Other values that are used for remote SMTP service include the following (note that you do not need to specify these values unless you want to override the default values).</span></span>  
  
-   <span data-ttu-id="72d4b-162">**SMTPServerPort** は、ポート 25 に構成します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-162">**SMTPServerPort** is configured for port 25.</span></span>  
  
-   <span data-ttu-id="72d4b-163">**SMTPAuthenticate** では、レポート サーバーがリモート SMTP サーバーに接続する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-163">**SMTPAuthenticate** specifies how the report server connects to the remote SMTP server.</span></span> <span data-ttu-id="72d4b-164">既定値は 0 (認証なし) です。</span><span class="sxs-lookup"><span data-stu-id="72d4b-164">The default value is 0 (or no authentication).</span></span> <span data-ttu-id="72d4b-165">この場合、接続は匿名アクセスをとおして行われます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-165">In this case, the connection is made through Anonymous access.</span></span> <span data-ttu-id="72d4b-166">ドメインの構成によっては、レポート サーバーと SMTP サーバーが同じドメインのメンバーであることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-166">Depending on your domain configuration, the report server and the SMTP server may need to be members of the same domain.</span></span>  
  
     <span data-ttu-id="72d4b-167">制限付きの配信リスト (たとえば、認証されたアカウントからの着信メッセージだけを受け付ける配信リスト) に電子メールを送信するには、 **SMTPAuthenticate** を **2**に設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-167">To send e-mail to restricted distribution lists (for example, distribution lists that accept incoming messages only from authenticated accounts), set **SMTPAuthenticate** to **2**.</span></span>  
  

  
##  <a name="configuration-options-for-local-smtp-service"></a><a name="bkmk_options_local_SMTP"></a><span data-ttu-id="72d4b-168">ローカル SMTP サービスの構成オプション</span><span class="sxs-lookup"><span data-stu-id="72d4b-168">Configuration Options for Local SMTP Service</span></span>  
 <span data-ttu-id="72d4b-169">レポート サーバー電子メール配信のテストまたはトラブルシューティングを行う場合は、ローカル SMTP サービスの構成が役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-169">Configuring a local SMTP service is useful if you are testing or troubleshooting report server e-mail delivery.</span></span> <span data-ttu-id="72d4b-170">既定ではローカル SMTP サービスは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="72d4b-170">The local SMTP service is not enabled by default.</span></span> <span data-ttu-id="72d4b-171">有効にする方法については、「[電子メール配信用にレポートサーバーを構成する (ssrs Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 」および「[電子メールの設定-Configuration Manager &#40;SSRS ネイティブモード&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72d4b-171">For instructions on how to enable it, see [Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="72d4b-172">レポート サーバーとローカル SMTP サーバーまたはフォワーダーの間の接続は、次の構成設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="72d4b-172">The connection between the report server and a local SMTP server or forwarder is determined by the following configuration settings:</span></span>  
  
-   <span data-ttu-id="72d4b-173">`SendUsing` は **1** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-173">`SendUsing` is set to **1**.</span></span>  
  
-   <span data-ttu-id="72d4b-174">**SMTPServerPickupDirectory** には、ローカル ドライブのフォルダーを設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-174">**SMTPServerPickupDirectory** is set to a folder on the local drive.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="72d4b-175">ローカル SMTP サーバーを使用している場合は、を設定しないようにしてください `SMTPServer` 。</span><span class="sxs-lookup"><span data-stu-id="72d4b-175">Be sure that you do not set `SMTPServer` if you are using a local SMTP server.</span></span>  
  
-   <span data-ttu-id="72d4b-176">`From` メール メッセージの **[送信者]** 行に使用する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-176">`From` sets the value that appears in the **From:** line of an e-mail message.</span></span> <span data-ttu-id="72d4b-177">この値は必須です。</span><span class="sxs-lookup"><span data-stu-id="72d4b-177">This value is required.</span></span>  
  
 
  
##  <a name="to-configure-report-server-e-mail-using-the-reporting-services-configuration-manager"></a><a name="bkmk_use_configuration_manager"></a><span data-ttu-id="72d4b-178">Reporting Services Configuration Manager を使用してレポートサーバーの電子メールを構成するには</span><span class="sxs-lookup"><span data-stu-id="72d4b-178">To configure report server e-mail using the Reporting Services Configuration Manager</span></span>  
  
1.  <span data-ttu-id="72d4b-179">レポート サーバー Windows サービスが SMTP サーバー上で `Send As` 権限を保持していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-179">Verify that the Report Server Windows service has `Send As` permissions on the SMTP server.</span></span>  
  
2.  <span data-ttu-id="72d4b-180">Reporting Services 構成マネージャーを起動して、レポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-180">Start the Reporting Services Configuration Manager and connect to the report server instance.</span></span>  
  
3.  <span data-ttu-id="72d4b-181">[電子メールの設定] ページで、SMTP サーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-181">On the Email Settings page, enter the name of the SMTP server.</span></span> <span data-ttu-id="72d4b-182">この値は、IP アドレス、企業イントラネット上のコンピューターの UNC 名、または完全修飾ドメイン名にすることができます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-182">This value can be an IP address, a UNC name of a computer on your corporate intranet, or a fully qualified domain name.</span></span>  
  
4.  <span data-ttu-id="72d4b-183">**[送信者アドレス]** で、SMTP サーバーから電子メールを送信する権限を保持しているアカウントの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-183">In **Sender Address**, enter the name an account that has permission to send e-mail from the SMTP server.</span></span>  
  
5.  <span data-ttu-id="72d4b-184">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="72d4b-184">Click **Apply**.</span></span>  
  

  
##  <a name="to-configure-a-remote-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_remote_SMTP"></a><span data-ttu-id="72d4b-185">リモート SMTP サービスをレポートサーバー用に構成するには</span><span class="sxs-lookup"><span data-stu-id="72d4b-185">To configure a remote SMTP Service for the report server</span></span>  
  
1.  <span data-ttu-id="72d4b-186">レポート サーバー Windows サービスが SMTP サーバー上で `Send As` 権限を保持していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-186">Verify that the Report Server Windows service has `Send As` permissions on the SMTP server.</span></span>  
  
2.  <span data-ttu-id="72d4b-187">テキスト エディターで RSReportServer.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-187">Open the RSReportServer.config file in a text editor.</span></span>  
  
3.  <span data-ttu-id="72d4b-188"><`UrlRoot`> がレポートサーバーの URL アドレスに設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-188">Verify that <`UrlRoot`> is set to the report server URL address.</span></span> <span data-ttu-id="72d4b-189">この値はレポート サーバーを構成するときに設定されるため、既に設定されているはずです。</span><span class="sxs-lookup"><span data-stu-id="72d4b-189">This value is set when you configure the report server and it should be filled in already.</span></span> <span data-ttu-id="72d4b-190">設定されていない場合は、レポート サーバーの URL アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-190">If it is not set, type the report server URL address.</span></span>  
  
4.  <span data-ttu-id="72d4b-191">[配信] セクションで、[<> を見つけ `ReportServerEmail` ます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-191">In the Delivery section, find <`ReportServerEmail`>.</span></span>  
  
5.  <span data-ttu-id="72d4b-192">[<`SMTPServer`> で、SMTP サーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-192">In <`SMTPServer`>, type the name of the SMTP server.</span></span> <span data-ttu-id="72d4b-193">この値は、IP アドレス、企業イントラネット上のコンピューターの UNC 名、または完全修飾ドメイン名にすることができます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-193">This value can be an IP address, a UNC name of a computer on your corporate intranet, or a fully qualified domain name.</span></span>  
  
6.  <span data-ttu-id="72d4b-194"><`SendUsing`> が2に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-194">Verify that <`SendUsing`> is set to 2.</span></span> <span data-ttu-id="72d4b-195">別の値に設定されている場合、レポート サーバーはリモート SMTP サービスを使用するように構成されていません。</span><span class="sxs-lookup"><span data-stu-id="72d4b-195">If it is set another value, the report server is not configured to use a remote SMTP service.</span></span>  
  
7.  <span data-ttu-id="72d4b-196">[<`From`>] に、SMTP サーバーから電子メールを送信する権限を持つアカウントの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-196">In <`From`>, type the name an account that has permission to send e-mail from the SMTP server.</span></span>  
  
8.  <span data-ttu-id="72d4b-197">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-197">Save the file.</span></span>  
  
     <span data-ttu-id="72d4b-198">レポート サーバーは新しい設定を自動的に使用します。サービスを再起動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="72d4b-198">The report server will use the new settings automatically; you do not need to restart the service.</span></span> <span data-ttu-id="72d4b-199">追加の SMTP 設定を指定し、レポート サーバー電子メール配信で SMTP サーバーを使用する方法をさらに細かく構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-199">You can specify additional SMTP settings to further configure how the SMTP server is used for report server e-mail delivery.</span></span> <span data-ttu-id="72d4b-200">詳しくは、「 [ssNoVersion](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 」および「 [ssNoVersion](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) オンライン ブックの「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onlオンライン ブックの「e.</span><span class="sxs-lookup"><span data-stu-id="72d4b-200">For more information, see [Configuring a Report Server for E-Mail Delivery](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  

  
##  <a name="to-configure-a-local-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_local_SMTP"></a><span data-ttu-id="72d4b-201">レポートサーバーのローカル SMTP サービスを構成するには</span><span class="sxs-lookup"><span data-stu-id="72d4b-201">To configure a local SMTP Service for the report server</span></span>  
  
1.  <span data-ttu-id="72d4b-202">コントロール パネルで、**[プログラムの追加と削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="72d4b-202">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="72d4b-203">**[Windows コンポーネントの追加と削除]** をクリックして、Windows コンポーネント ウィザードを開始します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-203">Click **Add/Remove Windows Components** to start the Windows Component Wizard.</span></span>  
  
3.  <span data-ttu-id="72d4b-204">**[アプリケーション サーバー]** を選択し、 **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="72d4b-204">Select **Application Server** and click **Details**.</span></span>  
  
4.  <span data-ttu-id="72d4b-205">**[インターネット インフォメーション サービス (IIS)]** を選択し、 **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="72d4b-205">Select **Internet Information Services (IIS)** and click **Details**.</span></span>  
  
5.  <span data-ttu-id="72d4b-206">**[SMTP サービス]** チェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="72d4b-206">Select the **SMTP Service** checkbox and click **OK**.</span></span>  
  
6.  <span data-ttu-id="72d4b-207">Windows コンポーネント ウィザードの **[次へ]** をクリックし、</span><span class="sxs-lookup"><span data-stu-id="72d4b-207">On the Windows Component Wizard, click **Next**.</span></span> <span data-ttu-id="72d4b-208">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="72d4b-208">Click **Finish**.</span></span>  
  
7.  <span data-ttu-id="72d4b-209">**[サービス]** コンソールでサービスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-209">Verify that the service is running in the **Services** console.</span></span>  
  
8.  <span data-ttu-id="72d4b-210">テキストエディターで**RSReportServer.config**ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="72d4b-210">Open the **RSReportServer.config** file in a text editor.</span></span>  
  
9. <span data-ttu-id="72d4b-211">`<UrlRoot>` がレポート サーバーの URL アドレスに設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-211">Verify that `<UrlRoot>` is set to the report server URL address.</span></span> <span data-ttu-id="72d4b-212">この値はレポート サーバーを構成するときに設定されるため、既に設定されているはずです。</span><span class="sxs-lookup"><span data-stu-id="72d4b-212">This value is set when you configure the report server and it should be filled in already.</span></span> <span data-ttu-id="72d4b-213">設定されていない場合は、レポート サーバーの URL アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-213">If it is not set, type the report server URL address.</span></span>  
  
10. <span data-ttu-id="72d4b-214">Delivery セクションで、`<ReportServerEmail>.` を検索します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-214">In the Delivery section, find `<ReportServerEmail>.`</span></span>  
  
11. <span data-ttu-id="72d4b-215">`<SMTPServer>`内で、この設定の値をすべて消去します。タグは削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="72d4b-215">In `<SMTPServer>`, clear any values for this setting, but do not delete the tags.</span></span>  
  
12. <span data-ttu-id="72d4b-216">`<SendUsing>` を 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-216">Set `<SendUsing>` to 1.</span></span> <span data-ttu-id="72d4b-217">1 以外の値に設定されている場合、レポート サーバーはローカル SMTP サービスを使用するように構成されていません。</span><span class="sxs-lookup"><span data-stu-id="72d4b-217">If it is set another value, the report server is not configured to use a local SMTP service.</span></span>  
  
13. <span data-ttu-id="72d4b-218">`<SMTPServerPickupDirectory>` に、ローカル ドライブ上のフォルダーを設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-218">Set `<SMTPServerPickupDirectory>` to a folder on the local drive.</span></span>  
  
14. <span data-ttu-id="72d4b-219">`<From>` に、SMTP サーバーから電子メールを送信する権限を保持しているアカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-219">Set `<From>` to an account that has permission to send e-mail from the SMTP server.</span></span>  
  
15. <span data-ttu-id="72d4b-220">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="72d4b-220">Save the file.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="72d4b-221">参照</span><span class="sxs-lookup"><span data-stu-id="72d4b-221">See Also</span></span>  
 [<span data-ttu-id="72d4b-222">Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="72d4b-222">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
