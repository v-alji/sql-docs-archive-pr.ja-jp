---
title: Reporting Services の既定の配信拡張機能を変更する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], default delivery extension
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cc1b3af2a4fe3038b761d0b48030062da06d354e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719418"
---
# <a name="change-the-default-reporting-services-delivery-extension"></a><span data-ttu-id="ed87e-102">Reporting Services の既定の配信拡張機能を変更する</span><span class="sxs-lookup"><span data-stu-id="ed87e-102">Change the Default Reporting Services Delivery Extension</span></span>
  <span data-ttu-id="ed87e-103">サブスクリプション定義ページの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] [配信者] **リストに表示される既定の配信拡張機能は** の構成設定で変更できます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-103">You can modify [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration settings to change the default delivery extension that appears in the **Delivered by** list of a subscription definition page.</span></span> <span data-ttu-id="ed87e-104">たとえば、ユーザーが新しいサブスクリプションを作成したときに電子メール配信ではなくファイル共有配信が既定で選択されるように構成を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-104">For example you can modify the configuration so that when users create a new subscription, file share delivery is selected by default instead of e-mail delivery.</span></span> <span data-ttu-id="ed87e-105">また、ユーザー インターフェイスにおける配信拡張機能の表示順を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-105">You can also change the order the delivery extensions are listed in the user interface.</span></span>

 <span data-ttu-id="ed87e-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="ed87e-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ed87e-107">には、電子メールの配信拡張機能と Windows ファイル共有の配信拡張機能があります。</span><span class="sxs-lookup"><span data-stu-id="ed87e-107">includes E-mail and Windows File Share delivery are extensions.</span></span> <span data-ttu-id="ed87e-108">カスタム配信をサポートするため、独自の拡張機能またはサード パーティの拡張機能を配置している場合は、これら以外の配信拡張機能もレポート サーバーに含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed87e-108">Your report server might have additional delivery extensions if you have deployed custom or third-party extensions to support custom delivery.</span></span> <span data-ttu-id="ed87e-109">配信拡張機能を使用できるかどうかは、配信拡張機能がレポート サーバーに配置されているかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="ed87e-109">The availability of a delivery extension depends on whether it is deployed on a report server.</span></span>

## <a name="default-native-mode-report-server-configuration"></a><span data-ttu-id="ed87e-110">ネイティブ モードのレポート サーバーの既定の構成</span><span class="sxs-lookup"><span data-stu-id="ed87e-110">Default Native mode report server configuration</span></span>
 <span data-ttu-id="ed87e-111">レポート マネージャーの **[配信者]** リストの配信拡張機能は、 **RSReportServer.config** ファイルの配信拡張機能のエントリ順に基づいて表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-111">The order of a delivery extension appears in Report Manager in the **Delivered by** list is based on the order of the delivery extension entries in the **RSReportServer.config** file.</span></span> <span data-ttu-id="ed87e-112">たとえば次の画像を見ると、電子メールが一覧の先頭に表示され、既定で選択状態になっています。</span><span class="sxs-lookup"><span data-stu-id="ed87e-112">For example the following image shows e-mail first in the list and it is selected by default.</span></span>

 <span data-ttu-id="ed87e-113">![配信拡張機能の既定の一覧](../media/ssrs-default-delivery.png "配信拡張機能の既定の一覧")</span><span class="sxs-lookup"><span data-stu-id="ed87e-113">![default list of delivery extensions](../media/ssrs-default-delivery.png "default list of delivery extensions")</span></span>

 <span data-ttu-id="ed87e-114">以下に示すコードは、 **RSReportServer.config** の既定のセクションです。既定の配信拡張機能とレポート マネージャーにおける表示順がこのセクションで制御されます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-114">The following is the default section of **RSReportServer.config** that controls the default delivery extension and the order they are displayed in Report Manager.</span></span> <span data-ttu-id="ed87e-115">このファイルで電子メールが先に記述され、なおかつ既定として設定されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="ed87e-115">Note that email appears first in the file and it is set as the default.</span></span>

```xml
<DeliveryUI>
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
               <Configuration>
               <RSEmailDPConfiguration>
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
               </RSEmailDPConfiguration>
               </Configuration>
     </Extension>
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>
</DeliveryUI>
```

#### <a name="configure-file-share-delivery-as-the-default-delivery-extension-in-report-manager"></a><span data-ttu-id="ed87e-116">レポート マネージャーでファイル共有配信を既定の配信拡張機能として構成する</span><span class="sxs-lookup"><span data-stu-id="ed87e-116">Configure File Share Delivery as the default delivery extension in Report Manager</span></span>

1.  <span data-ttu-id="ed87e-117">ファイル共有配信が一覧の先頭に、既定の選択肢として表示されるように、この手順の各段階で構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="ed87e-117">The steps in this procedure modify the configuration so that file share delivery is listed as the first option in the UI and it is the default selection.</span></span>

     <span data-ttu-id="ed87e-118">テキスト エディターで RSReportServer.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-118">Open the RSReportServer.config file in a text editor.</span></span> <span data-ttu-id="ed87e-119">構成ファイルの詳細については、「 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed87e-119">For more information on the configuration file, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span> <span data-ttu-id="ed87e-120">以下の画像は、構成変更後の UI を示しています。</span><span class="sxs-lookup"><span data-stu-id="ed87e-120">After the configuration changes, the UI will look like the following image:</span></span>

     <span data-ttu-id="ed87e-121">![配信拡張機能の変更した一覧](../media/ssrs-modified-delivery.png "配信拡張機能の変更した一覧")</span><span class="sxs-lookup"><span data-stu-id="ed87e-121">![modified list of delivery extensions](../media/ssrs-modified-delivery.png "modified list of delivery extensions")</span></span>

2.  <span data-ttu-id="ed87e-122">DeliveryUI セクションを以下の例のように変更します。主な変更点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ed87e-122">Modify the DeliveryUI section to look like the following sample and note the key changes of:</span></span>

    1.  <span data-ttu-id="ed87e-123">FileShare 拡張機能を電子メール拡張機能の前に移動。</span><span class="sxs-lookup"><span data-stu-id="ed87e-123">The FileShare extension is before the email extension.</span></span> <span data-ttu-id="ed87e-124">レポート マネージャーにおける配信拡張機能の表示順が変更されます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-124">This will change the order the extensions are listed in Report Manager.</span></span>

    2.  <span data-ttu-id="ed87e-125">ファイル共有拡張機能に DefaultExtension タグ `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` と拡張機能の終了タグ `</Extension>`を追加。</span><span class="sxs-lookup"><span data-stu-id="ed87e-125">The File share extension contains DefaultExtension tag `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` and the extension end tag was added `</Extension>`.</span></span>

    3.  <span data-ttu-id="ed87e-126">既定としての電子メール拡張機能の構成を解除。</span><span class="sxs-lookup"><span data-stu-id="ed87e-126">The email extension is no longer configured as the default.</span></span> `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`

    ```
    <DeliveryUI>
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
         </Extension>
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>
         <Configuration>
              <RSEmailDPConfiguration>
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
              </RSEmailDPConfiguration>
         </Configuration>
         </Extension>
    </DeliveryUI>
    ```

3.  <span data-ttu-id="ed87e-127">構成ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ed87e-127">Save the configuration file.</span></span>

4.  <span data-ttu-id="ed87e-128">数分するとレポート サーバーに構成ファイルが再読み込みされ、新しい設定が反映されます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-128">Within a few minutes the report server will reload the configuration file and the new settings will take effect.</span></span> <span data-ttu-id="ed87e-129">構成ファイルを強制的に読み込ませるには、レポート サーバー サービスを再起動してください。</span><span class="sxs-lookup"><span data-stu-id="ed87e-129">You can restart the report server service to force the loading of the configuration file.</span></span>

     <span data-ttu-id="ed87e-130">構成が読み取られると、次のイベントが Windows イベント ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-130">The following event is written to the windows event log when the configuration is read.</span></span>

     <span data-ttu-id="ed87e-131">**イベント ID:** 109</span><span class="sxs-lookup"><span data-stu-id="ed87e-131">**Event ID:** 109</span></span>

     <span data-ttu-id="ed87e-132">**ソース:** Report Server Windows Service (インスタンス名)</span><span class="sxs-lookup"><span data-stu-id="ed87e-132">**Source:** Report Server Windows Service (instance name)</span></span>

     <span data-ttu-id="ed87e-133">RSReportServer.config ファイルが変更されました。</span><span class="sxs-lookup"><span data-stu-id="ed87e-133">The RSReportServer.config file has been modified</span></span>

## <a name="sharepoint-mode-report-servers"></a><span data-ttu-id="ed87e-134">SharePoint モードのレポート サーバー</span><span class="sxs-lookup"><span data-stu-id="ed87e-134">SharePoint mode report servers</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ed87e-135">SharePoint モードでは、拡張機能の情報が、RsrReportServer.config ファイルにではなく SharePoint Service アプリケーションのデータベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-135">SharePoint mode stores extensions information in the SharePoint service application databases and not in the RsrReportServer.config file.</span></span> <span data-ttu-id="ed87e-136">SharePoint モードの配信拡張機能の構成は PowerShell を使って変更することになります。</span><span class="sxs-lookup"><span data-stu-id="ed87e-136">In SharePoint mode, delivery extension configuration is modified using PowerShell.</span></span>

#### <a name="configure-the-default-delivery-extension"></a><span data-ttu-id="ed87e-137">既定の配信拡張機能の構成</span><span class="sxs-lookup"><span data-stu-id="ed87e-137">Configure the default delivery extension</span></span>

1.  <span data-ttu-id="ed87e-138">**[SharePoint 管理シェル]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="ed87e-138">Open the **SharePoint Management Shell**.</span></span>

2.  <span data-ttu-id="ed87e-139">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サービス アプリケーションの名前が既にわかっている場合、この手順は省略してかまいません。</span><span class="sxs-lookup"><span data-stu-id="ed87e-139">You can skip this step if you already know the name of your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="ed87e-140">次の PowerShell コマンドを使用して、SharePoint ファーム内の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サービス アプリケーションを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ed87e-140">Use the following PowerShell to list the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service applications in your SharePoint farm.</span></span>

    ```powershell
    Get-SPRSServiceApplication | Format-List *
    ```

3.  <span data-ttu-id="ed87e-141">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サービス アプリケーション "ssrsapp" に使用されている現在の既定の配信拡張機能を次の PowerShell コードで確認します。</span><span class="sxs-lookup"><span data-stu-id="ed87e-141">Run the following PowerShell to verify the current default delivery extension for the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service application "ssrsapp".</span></span>

    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -Like "ssrsapp*"};
    Get-SPRSExtension -Identity $app | Where {$_.ServerDirectivesXML -Like "<DefaultDelivery*"} | Format-List *
    ```

## <a name="see-also"></a><span data-ttu-id="ed87e-142">参照</span><span class="sxs-lookup"><span data-stu-id="ed87e-142">See Also</span></span>
 <span data-ttu-id="ed87e-143">[Rsreportserver 構成ファイル](../report-server/rsreportserver-config-configuration-file.md) [rsreportserver 構成ファイル](../report-server/rsreportserver-config-configuration-file.md)[ファイル共有配信 Reporting Services](file-share-delivery-in-reporting-services.md) [電子](e-mail-delivery-in-reporting-services.md)メール配信での電子メール配信で[は、SSRS Configuration Manager &#40;電子メール配信用にレポートサーバーを構成 Reporting Services&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)</span><span class="sxs-lookup"><span data-stu-id="ed87e-143">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md) [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)</span></span>
