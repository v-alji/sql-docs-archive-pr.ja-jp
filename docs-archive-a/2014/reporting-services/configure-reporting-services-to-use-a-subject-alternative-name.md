---
title: サブジェクト代替名を使用するように Reporting Services を構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ce458f9f-4b4f-4a58-aa75-9a90dda1e622
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0312d2d1fff8f854eb2ffb8d0dad2563212ee23b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739540"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a><span data-ttu-id="4dfe3-102">サブジェクト代替名を使用するように Reporting Services を構成する</span><span class="sxs-lookup"><span data-stu-id="4dfe3-102">Configure Reporting Services to Use a Subject Alternative Name</span></span>
  <span data-ttu-id="4dfe3-103">このトピックでは、rsreportserver.config ファイルを変更し、Netsh.exe ツールを使用することによって、サブジェクト代替名 (SAN) を使用するように [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-103">This topic explains how to configure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) to use a subject alternative name (SAN) by modifying the rsreportserver.config file and using the Netsh.exe tool.</span></span>

||
|-|
|<span data-ttu-id="4dfe3-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ネイティブ モード</span><span class="sxs-lookup"><span data-stu-id="4dfe3-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Native mode</span></span>|

 <span data-ttu-id="4dfe3-105">この手順は、レポート サービスの URL および Web サービス URL に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-105">The instructions apply to the Reporting Service URL as well as a Web Service URL.</span></span>

 <span data-ttu-id="4dfe3-106">SAN を使用するには、SSL 証明書がサーバーに登録され、署名され、秘密キーを保持している必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-106">To use a SAN, the SSL certificate must be registered on the server, signed, and have the private key.</span></span> <span data-ttu-id="4dfe3-107">自己署名証明書は使用できません</span><span class="sxs-lookup"><span data-stu-id="4dfe3-107">You cannot use a self-signed certificate</span></span>

 <span data-ttu-id="4dfe3-108">SSL 証明書を使用するように、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の URL を構成できます。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-108">URLs in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] can be configured to use an SSL certificate.</span></span> <span data-ttu-id="4dfe3-109">通常、証明書にはサブジェクト名のみが記載されているため、SSL (Secure Sockets Layer) セッションに対して許可される URL は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-109">A certificate normally has just a subject name, which allows only one URL for an SSL (Secure Sockets Layer) session.</span></span> <span data-ttu-id="4dfe3-110">SAN は、SSL サービスがリッスンでき、多数の URL 対して有効化され、SSL ポートを他のアプリケーションと共有できるようにするための証明書の追加フィールドです。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-110">The SAN is an additional field in the certificate that allows an SSL service to listen and be valid for many URLs, and to share the SSL port with other applications.</span></span> <span data-ttu-id="4dfe3-111">SAN は、www.s2.com のようになります。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-111">The SAN looks something like the following: www.s2.com.</span></span>

 <span data-ttu-id="4dfe3-112">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のSSL 設定の詳細については、「 [ネイティブ モードのレポート サーバーでの SSL 接続の構成](security/configure-ssl-connections-on-a-native-mode-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-112">For more information about SSL settings for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Configure SSL Connections on a Native Mode Report Server](security/configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>

### <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a><span data-ttu-id="4dfe3-113">サブジェクト代替名を Web サービス URL に使用するように SSRS を構成します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-113">Configure SSRS to use a subject alternative name for Web Service URL</span></span>

1.  <span data-ttu-id="4dfe3-114">Reporting Services 構成マネージャーを開始します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-114">Start Reporting Services Configuration Manager.</span></span>

     <span data-ttu-id="4dfe3-115">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>

2.  <span data-ttu-id="4dfe3-116">**[Web サービス URL]** ページで、SSL ポートおよび SSL 証明書を選択します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-116">On the **Web Service URL** page, select an SSL port and SSL Certificate.</span></span>

     <span data-ttu-id="4dfe3-117">![Reporting Services 構成マネージャー](media/reportingservices-configurationmanager.png "Reporting Services 構成マネージャー")</span><span class="sxs-lookup"><span data-stu-id="4dfe3-117">![Reporting Services Configuration Manager](media/reportingservices-configurationmanager.png "Reporting Services Configuration Manager")</span></span>

     <span data-ttu-id="4dfe3-118">構成マネージャーは、ポート用に SSL 証明書を登録します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-118">The configuration manager registers the SSL certificate for the port.</span></span>

3.  <span data-ttu-id="4dfe3-119">rsreportserver.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-119">Open the rsreportserver.config file.</span></span>

     <span data-ttu-id="4dfe3-120">SSRS ネイティブ モードの場合、ファイルは、既定では、次のフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-120">For SSRS Native mode, the file is located by default in the following folder.</span></span>

    ```
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer
    ```

4.  <span data-ttu-id="4dfe3-121">レポート サーバー Web サービス アプリケーションの URL セクションをコピーします。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-121">Copy the URL section for the Report Server Web Service application.</span></span>

     <span data-ttu-id="4dfe3-122">たとえば、元の URL セクションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-122">For example, the following is the original URL section.</span></span>

    ```
        <URL>
         <UrlString>https://localhost:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

     <span data-ttu-id="4dfe3-123">変更後の URL セクションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-123">The following is the modified URL section.</span></span>

    ```
    <URL>
         <UrlString>https://www.s1.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>
        <URL>
         <UrlString>https://www.s2.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

5.  <span data-ttu-id="4dfe3-124">rsreportserver.config ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-124">Save the rsreportserver.config file.</span></span>

6.  <span data-ttu-id="4dfe3-125">管理者としてコマンド プロンプトを起動し、Netsh.exe ツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-125">Start a command prompt as an administrator, and run the Netsh.exe tool.</span></span>

    ```
    C:\windows\system32\netsh
    ```

7.  <span data-ttu-id="4dfe3-126">次のように入力して、http コンテキストに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-126">Switch to the http context by typing the following.</span></span>

    ```
    Netsh>http
    ```

8.  <span data-ttu-id="4dfe3-127">次のように入力して、既存の urlacl を表示します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-127">Show the existing urlacls by typing the following.</span></span>

    ```
    Netsh http>show urlacl
    ```

     <span data-ttu-id="4dfe3-128">次のようなエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-128">An entry such as the following appears.</span></span>

    ```
    Reserved URL            : https:// www.s1.com:443/ReportServer/
        User: NT SERVICE\ReportServer
            Listen: Yes
            Delegate: No
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)
    ```

     <span data-ttu-id="4dfe3-129">urlacl は、予約された URL の DACL (任意のアクセス制御リスト) です。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-129">An urlacl is a DACL (Discretionary Access Control List) for a reserved URL.</span></span>

9. <span data-ttu-id="4dfe3-130">次のように入力して、既存のエントリと同じユーザーおよび SDDL を持つ、サブジェクト代替名の新しいエントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-130">Create a new entry for the subject alternative name, with the same user and SDDL as the existing entry, by typing the following.</span></span>

    ```
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer  
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)

    ```

10. <span data-ttu-id="4dfe3-131">Reporting Services 構成マネージャーの **[レポート サーバーの状態]** ページで、 **[停止]** をクリックしてから **[開始]** をクリックし、レポート サーバーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="4dfe3-131">On the **Report Server Status** page of the Reporting Services Configuration Manager, Click **Stop** and then click **Start** to restart the report server.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dfe3-132">参照</span><span class="sxs-lookup"><span data-stu-id="4dfe3-132">See Also</span></span>
 <span data-ttu-id="4dfe3-133">[Rsreportserver 構成ファイル](report-server/rsreportserver-config-configuration-file.md) [Reporting Services Configuration Manager &#40;ネイティブモード&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Reporting Services 構成ファイルを変更する &#40;、](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) [レポートサーバーの url RSreportserver.config SSRS&#41;を構成](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)&#40;</span><span class="sxs-lookup"><span data-stu-id="4dfe3-133">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)</span></span>


