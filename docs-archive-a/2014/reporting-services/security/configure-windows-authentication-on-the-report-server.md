---
title: レポート サーバーで Windows 認証を構成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [Reporting Services]
- Reporting Services, configuration
ms.assetid: 4de9c3dd-0ee7-49b3-88bb-209465ca9d86
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 879c036977f9a34528dbf38e42fa080e72617a14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715090"
---
# <a name="configure-windows-authentication-on-the-report-server"></a><span data-ttu-id="e8d4d-102">レポート サーバーで Windows 認証を構成する</span><span class="sxs-lookup"><span data-stu-id="e8d4d-102">Configure Windows Authentication on the Report Server</span></span>
  <span data-ttu-id="e8d4d-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、既定では、ネゴシエート認証または NTLM 認証を指定する要求を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-103">By default, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] accepts requests that specify Negotiate or NTLM authentication.</span></span> <span data-ttu-id="e8d4d-104">これらのセキュリティ プロバイダーを使用するクライアント アプリケーションおよびブラウザーが配置に含まれている場合は、追加の構成なしで既定値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-104">If your deployment includes client applications and browsers that use these security providers, you can use the default values without additional configuration.</span></span> <span data-ttu-id="e8d4d-105">Windows 統合セキュリティの別のセキュリティ プロバイダーを使用する場合 (たとえば Kerberos を直接使用する場合)、または既定値を変更した後に元の設定を復元する場合は、このトピックの情報を使用して、レポート サーバーで認証設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-105">If you want to use a different security provider for Windows integrated security (for example, if you want to use Kerberos directly), or if you modified the default values and want to restore the original settings, you can use the information in this topic to specify authentication settings on the report server.</span></span>  
  
 <span data-ttu-id="e8d4d-106">Windows 統合セキュリティを使用するには、レポート サーバーにアクセスする必要がある各ユーザーに、有効な Windows ローカル ユーザー アカウントまたはドメイン ユーザー アカウントを割り当てるか、そのユーザーを Windows ローカル グループ アカウントまたはドメイン グループ アカウントのメンバーにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-106">To use Windows integrated security, each user who requires access to a report server must have a valid Windows local or domain user account or be a member of a Windows local or domain group account.</span></span> <span data-ttu-id="e8d4d-107">信頼されている他のドメインのアカウントを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-107">You can include accounts from other domains as long as those domains are trusted.</span></span> <span data-ttu-id="e8d4d-108">このアカウントは、レポート サーバー コンピューターにアクセスできる必要があります。また、レポート サーバーの特定の操作を実行できるように、後でこのアカウントをロールに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-108">The accounts must have access to the report server computer, and must be subsequently assigned to roles in order to gain access to specific report server operations.</span></span>  
  
 <span data-ttu-id="e8d4d-109">次の追加要件も満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-109">The following additional requirements must also be met:</span></span>  
  
-   <span data-ttu-id="e8d4d-110">RSReportServer.config ファイルの `AuthenticationType` が、`RSWindowsNegotiate`、`RSWindowsKerberos`、または `RSWindowsNTLM` に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-110">The RSeportServer.config files must have `AuthenticationType` set to `RSWindowsNegotiate`, `RSWindowsKerberos`, or `RSWindowsNTLM`.</span></span> <span data-ttu-id="e8d4d-111">レポート サーバー サービス アカウントが NetworkService または LocalSystem である場合、RSReportServer.config ファイルには、既定で `RSWindowsNegotiate` 設定が含まれます。それ以外の場合は、`RSWindowsNTLM` 設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-111">By default, the RSReportServer.config file includes the `RSWindowsNegotiate` setting if the Report Server service account is either NetworkService or LocalSystem; otherwise, the `RSWindowsNTLM` setting is used.</span></span> <span data-ttu-id="e8d4d-112">Kerberos 認証のみを使用するアプリケーションがある場合は、`RSWindowsKerberos` を追加できます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-112">You can add `RSWindowsKerberos` if you have applications that only use Kerberos authentication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e8d4d-113">レポート サーバー サービスをドメイン ユーザー アカウントで実行するように構成し、かつそのアカウントのサービス プリンシパル名 (SPN) を登録していない場合は、`RSWindowsNegotiate` を使用すると Kerberos 認証エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-113">Using `RSWindowsNegotiate` will result in a Kerberos authentication error if you configured the Report Server service to run under a domain user account and you did not register a Service Principal Name (SPN) for the account.</span></span> <span data-ttu-id="e8d4d-114">詳細については、このトピックの「 [レポート サーバー接続時の Kerberos 認証エラーの解決](#proxyfirewallRSWindowsNegotiate) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-114">For more information, see [Resolving Kerberos Authentication Errors When Connecting to a report server](#proxyfirewallRSWindowsNegotiate) in this topic.</span></span>  
  
-   [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="e8d4d-115">で Windows 認証を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-115">must be configured for Windows Authentication.</span></span> <span data-ttu-id="e8d4d-116">既定では、レポートサーバー Web サービスおよびレポートマネージャーの Web.config ファイルに設定が含まれ \<authentication mode="Windows"> ます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-116">By default, the Web.config files for the Report Server Web service and Report Manager include the \<authentication mode="Windows"> setting.</span></span> <span data-ttu-id="e8d4d-117">をに変更すると \<authentication mode="Forms"> 、の Windows 認証 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は失敗します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-117">If you change it to \<authentication mode="Forms">, the Windows Authentication for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] will fail.</span></span>  
  
-   <span data-ttu-id="e8d4d-118">レポートサーバー Web サービスおよびレポートマネージャーの Web.config ファイルには、が必要 \<identity impersonate= "true" /> です。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-118">The Web.config files for the Report Server Web service and Report Manager must have \<identity impersonate= "true" />.</span></span>  
  
-   <span data-ttu-id="e8d4d-119">クライアント アプリケーションまたはブラウザーが、Windows 統合セキュリティをサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-119">The client application or browser must support Windows integrated security.</span></span>  
  
 <span data-ttu-id="e8d4d-120">レポート サーバーの認証設定を変更するには、RSReportServer.config ファイルの XML 要素と値を編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-120">To change the report server authentication settings, edit the XML elements and values in the RSReportServer.config file.</span></span> <span data-ttu-id="e8d4d-121">特定の組み合わせを実装するために、このトピックの例をコピーして貼り付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-121">You can copy and paste the examples in this topic to implement specific combinations.</span></span>  
  
 <span data-ttu-id="e8d4d-122">既定の設定は、すべてのクライアント コンピューターとサーバー コンピューターが同じドメインまたは信頼されているドメインにあり、かつレポート サーバーがイントラネット アクセス用に企業のファイアウォールの内側に配置されている場合に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-122">The default settings work best if all client and server computers are in the same domain or in a trusted domain and the report server is deployed for intranet access behind a corporate firewall.</span></span> <span data-ttu-id="e8d4d-123">Windows 資格情報を渡すには、ドメインが信頼されていて単一であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-123">Trusted and single domains are a requirement for passing Windows credentials.</span></span> <span data-ttu-id="e8d4d-124">サーバーで Kerberos Version 5 プロトコルを有効にした場合は、資格情報を複数回渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-124">Credentials can be passed more than one time if you enable the Kerberos version 5 protocol for your servers.</span></span> <span data-ttu-id="e8d4d-125">それ以外の場合は、資格情報をその有効期限が切れる前に 1 回だけ渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-125">Otherwise, credentials can be passed only one time before they expire.</span></span> <span data-ttu-id="e8d4d-126">複数のコンピューター接続に対する資格情報の構成の詳細については、「 [レポート データ ソースに関する資格情報と接続情報を指定する](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-126">For more information about configuring credentials for multiple computer connections, see [Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
 <span data-ttu-id="e8d4d-127">次に示す手順は、ネイティブ モードのレポート サーバーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-127">The following instructions are intended for a native mode report server.</span></span> <span data-ttu-id="e8d4d-128">レポート サーバーを SharePoint 統合モードで配置する場合は、Windows 統合セキュリティを指定する既定の認証設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-128">If the report server is deployed in SharePoint integrated mode, you must use the default authentication settings that specify Windows integrated security.</span></span> <span data-ttu-id="e8d4d-129">レポート サーバーでは、既定の Windows 認証拡張機能の内部機能を使用して、SharePoint 統合モードのレポート サーバーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-129">The report server uses internal features in the default Windows Authentication extension to support report servers in SharePoint integrated mode.</span></span>  
  
## <a name="extended-protection-for-authentication"></a><span data-ttu-id="e8d4d-130">認証の拡張保護 (Extended Protection for Authentication)</span><span class="sxs-lookup"><span data-stu-id="e8d4d-130">Extended Protection for Authentication</span></span>  
 <span data-ttu-id="e8d4d-131">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]以降では、認証の拡張保護がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-131">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], support for Extended Protection for Authentication is available.</span></span> <span data-ttu-id="e8d4d-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能により、認証の拡張保護に対するチャネル バインドとサービス バインドの使用がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-132">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication.</span></span> <span data-ttu-id="e8d4d-133">この [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能は、拡張保護がサポートされているオペレーティング システムで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-133">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features need to be used with an operating system that supports Extended Protection.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e8d4d-134">の拡張保護に対する構成は、RSReportServer.config ファイルの設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-134">configuration for extended protection is determined by settings in the RSReportServer.config file.</span></span> <span data-ttu-id="e8d4d-135">このファイルは、ファイルを編集するか WMI API を使用して更新できます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-135">The file can be updated by either editing the file or using WMI APIs.</span></span> <span data-ttu-id="e8d4d-136">詳細については、「 [Reporting Services での認証の拡張保護](extended-protection-for-authentication-with-reporting-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-136">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
### <a name="to-configure-a-report-server-to-use-windows-integrated-security"></a><span data-ttu-id="e8d4d-137">レポート サーバーを構成して Windows 統合セキュリティを使用するには</span><span class="sxs-lookup"><span data-stu-id="e8d4d-137">To configure a report server to use Windows integrated security</span></span>  
  
1.  <span data-ttu-id="e8d4d-138">テキスト エディターで RSReportServer.config を開きます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-138">Open RSReportServer.config in a text editor.</span></span>  
  
2.  <span data-ttu-id="e8d4d-139"><`Authentication`> を検索します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-139">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="e8d4d-140">次に示す XML 構造の中でニーズに最も合うものをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-140">Copy one of the following XML structures that best fits your needs.</span></span> <span data-ttu-id="e8d4d-141">`RSWindowsNegotiate`、`RSWindowsNTLM`、および `RSWindowsKerberos` は、任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-141">You can specify `RSWindowsNegotiate`, `RSWindowsNTLM`, and `RSWindowsKerberos` in any order.</span></span> <span data-ttu-id="e8d4d-142">個々の要求ではなく接続を認証する場合は、認証の永続化を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-142">You should enable authentication persistence if you want to authenticate the connection rather than each individual request.</span></span> <span data-ttu-id="e8d4d-143">認証の永続化を有効にすると、接続が続いている間は、認証を必要とするすべての要求が許可されます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-143">Under authentication persistence, all requests that require authentication will be allowed for the duration of the connection.</span></span>  
  
     <span data-ttu-id="e8d4d-144">1 番目の XML 構造は、レポート サーバー サービス アカウントが NetworkService または LocalSystem である場合の既定の構成です。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-144">The first XML structure is the default configuration when the Report Server service account is either NetworkService or LocalSystem:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     <span data-ttu-id="e8d4d-145">2 番目の XML 構造は、レポート サーバー サービス アカウントが NetworkService と LocalSystem のいずれにも該当しない場合の既定の構成です。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-145">The second XML structure is the default configuration when the Report Server service account is not NetworkService or LocalSystem:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    ```  
  
     \</Authentication>  
  
     <span data-ttu-id="e8d4d-146">3 番目の XML 構造は、Windows 統合セキュリティで使用されるすべてのセキュリティ パッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-146">The third XML structure specifies all of the security packages that are used in Windows integrated security:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
                 <RSWindowsKerberos />  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
     <span data-ttu-id="e8d4d-147">4 番目の XML 構造は、配置が Kerberos をサポートしていない場合、または Kerberos 認証エラーに対処する場合にのみ、NTLM を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-147">The fourth XML structure specifies NTLM only for deployments that do not support Kerberos or to work around Kerberos authentication errors:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
4.  <span data-ttu-id="e8d4d-148"><> の既存のエントリの上に貼り付け `Authentication` ます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-148">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="e8d4d-149">`Custom` の各種類と `RSWindows` は併用できないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-149">Note that you cannot use `Custom` with the `RSWindows` types.</span></span>  
  
5.  <span data-ttu-id="e8d4d-150">必要に応じて拡張保護の設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-150">Modify as appropriate the settings for extended protection.</span></span> <span data-ttu-id="e8d4d-151">既定では、拡張保護は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-151">Extended protection is disabled by default.</span></span>  <span data-ttu-id="e8d4d-152">これらのエントリが存在しない場合は、拡張保護がサポートされているバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] が現在のコンピューターで実行されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-152">If these entries are not present, the current computer may not be running a version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] which supports extended protection.</span></span> <span data-ttu-id="e8d4d-153">詳細については、「 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-153">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span></span>  
  
    ```  
          <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>  
          <RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
    ```  
  
6.  <span data-ttu-id="e8d4d-154">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-154">Save the file.</span></span>  
  
7.  <span data-ttu-id="e8d4d-155">スケールアウト配置を構成した場合は、配置内の他のレポート サーバーに対して上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-155">If you configured a scale-out deployment, repeat these steps for other report servers in the deployment.</span></span>  
  
8.  <span data-ttu-id="e8d4d-156">レポート サーバーを再起動して、現在開いているセッションを消去します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-156">Restart the report server to clear any sessions that are currently open.</span></span>  
  
##  <a name="resolving-kerberos-authentication-errors-when-connecting-to-a-report-server"></a><a name="proxyfirewallRSWindowsNegotiate"></a><span data-ttu-id="e8d4d-157">レポートサーバーへの接続時の Kerberos 認証エラーの解決</span><span class="sxs-lookup"><span data-stu-id="e8d4d-157">Resolving Kerberos Authentication Errors When Connecting to a Report Server</span></span>  
 <span data-ttu-id="e8d4d-158">ネゴシエート認証または Kerberos 認証が構成されているレポート サーバーでは、Kerberos 認証エラーが発生すると、レポート サーバーへのクライアント接続が失敗します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-158">On a report server that is configured for Negotiate or Kerberos authentication, a client connection to the report server will fail if there is a Kerberos authentication error.</span></span> <span data-ttu-id="e8d4d-159">Kerberos 認証エラーは、次の場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-159">Kerberos authentication errors are known to occur when:</span></span>  
  
-   <span data-ttu-id="e8d4d-160">サービス プリンシパル名 (SPN) を登録していない Windows ドメイン ユーザー アカウントでレポート サーバー サービスが実行されたとき。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-160">The Report Server service runs as a Windows domain user account and you did not register a Service Principal Name (SPN) for the account.</span></span>  
  
-   <span data-ttu-id="e8d4d-161">レポート サーバーが `RSWindowsNegotiate` 設定で構成されているとき。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-161">The report server is configured with the `RSWindowsNegotiate` setting.</span></span>  
  
-   <span data-ttu-id="e8d4d-162">ブラウザーがレポート サーバーに送信する要求の認証ヘッダーで、NTLM ではなく Kerberos が選択されたとき。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-162">The browser chooses Kerberos over NTLM in the authentication header in the request it sends to the report server.</span></span>  
  
 <span data-ttu-id="e8d4d-163">Kerberos のログ記録を有効にしていれば、エラーを検出できます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-163">You can detect the error if you enabled Kerberos logging.</span></span> <span data-ttu-id="e8d4d-164">資格情報の入力を複数回要求された後に空のブラウザー ウィンドウが表示された場合も、エラーが発生しています。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-164">Another symptom of the error is that you are prompted for credentials multiple times and then see an empty browser window.</span></span>  
  
 <span data-ttu-id="e8d4d-165"></> を構成ファイルから削除して接続を再試行することで、Kerberos 認証エラーが発生していることを確認でき `RSWindowsNegotiate` ます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-165">You can confirm that you are encountering a Kerberos authentication error by removing < `RSWindowsNegotiate` /> from your configuration file and reattempting the connection.</span></span>  
  
 <span data-ttu-id="e8d4d-166">問題を確認したら、次の方法で問題に対処できます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-166">After you confirm the problem, you can address it in the following ways:</span></span>  
  
-   <span data-ttu-id="e8d4d-167">ドメイン ユーザー アカウントでレポート サーバー サービスの SPN を登録します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-167">Register an SPN for the Report Server service under the domain user account.</span></span> <span data-ttu-id="e8d4d-168">詳細については、「[レポート サーバーのサービス プリンシパル名 &#40;SPN&#41; の登録](../report-server/register-a-service-principal-name-spn-for-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-168">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
-   <span data-ttu-id="e8d4d-169">ネットワーク サービスなどのビルトイン アカウントで実行されるように、サービス アカウントを変更します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-169">Change the service account to run under a built-in account such as Network Service.</span></span> <span data-ttu-id="e8d4d-170">ビルトイン アカウントは、HTTP SPN を Host SPN にマップします。これは、コンピューターをネットワークに追加するときに定義されます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-170">Built-in accounts map HTTP SPN to the Host SPN, which is defined when you join a computer to your network.</span></span> <span data-ttu-id="e8d4d-171">詳細については、「[サービス アカウントの構成 (SSRS 構成マネージャー)](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-171">For more information, see [Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).</span></span>  
  
-   <span data-ttu-id="e8d4d-172">NTLM を使用します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-172">Use NTLM.</span></span> <span data-ttu-id="e8d4d-173">NTLM は一般に、Kerberos 認証が失敗した場合に機能します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-173">NTLM will generally work in cases where Kerberos authentication fails.</span></span> <span data-ttu-id="e8d4d-174">NTLM を使用するには、RSReportServer.config ファイルから `RSWindowsNegotiate` を削除し、`RSWindowsNTLM` のみが指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-174">To use NTLM, remove `RSWindowsNegotiate` from the RSReportServer.config file and verify that only `RSWindowsNTLM` is specified.</span></span> <span data-ttu-id="e8d4d-175">この方法を選択すれば、SPN を定義していないドメイン ユーザー アカウントでも、引き続きレポート サーバー サービスに使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-175">If you choose this approach, you can continue to use a domain user account for the Report Server service even if you do not define an SPN for it.</span></span>  
  
#### <a name="logging-information"></a><span data-ttu-id="e8d4d-176">ログ記録情報</span><span class="sxs-lookup"><span data-stu-id="e8d4d-176">Logging information</span></span>  
 <span data-ttu-id="e8d4d-177">ログ情報に、Kerberos 関連の問題の解決に役立つものがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-177">There are several sources of logging information that can help resolve Kerberos related issues.</span></span>  
  
##### <a name="user-account-control-attribute"></a><span data-ttu-id="e8d4d-178">User-Account-Control 属性</span><span class="sxs-lookup"><span data-stu-id="e8d4d-178">User-Account-Control Attribute</span></span>  
 <span data-ttu-id="e8d4d-179">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アカウントに Active Directory の十分な属性セットがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-179">Determine if the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account has the sufficient attribute set in Active Directory.</span></span> <span data-ttu-id="e8d4d-180">Reporting Services サービスのトレース ログ ファイルで、ログに記録された UserAccountControl 属性の値を探します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-180">Review the reporting services service trace log file to find the value logged for the UserAccountControl attribute.</span></span> <span data-ttu-id="e8d4d-181">値は 10 進形式で記録されています。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-181">The value logged is in decimal form.</span></span> <span data-ttu-id="e8d4d-182">10 進値を 16 進形式に変換し、その値を User-Account-Control 属性が記述された MSDN のトピックで検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-182">You need to convert the decimal value to hexadecimal form and then find that value in the MSDN topic describing User-Account-Control Attribute.</span></span>  
  
-   <span data-ttu-id="e8d4d-183">Reporting Services サービスのトレース ログのエントリは、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-183">The reporting services service trace log entry will look similar to the following:</span></span>  
  
    ```  
    appdomainmanager!DefaultDomain!8f8!01/14/2010-14:42:28:: i INFO: The UserAccountControl value for the service account is 590336  
    ```  
  
-   <span data-ttu-id="e8d4d-184">10 進値を 16 進形式に変換する 1 つの方法として、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows の電卓を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-184">One option for converting the value Decimal value to hexadecimal form is to us the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Calculator.</span></span> <span data-ttu-id="e8d4d-185">Windows の電卓では、[10 進] オプションと [16 進] オプションを表示するいくつかのモードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-185">Windows Calculator supports several modes that show the 'Dec' option and 'Hex' options.</span></span> <span data-ttu-id="e8d4d-186">[10 進] オプションを選択し、ログ ファイルで見つけた 10 進値を貼り付けるか入力して、[16 進] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-186">Select the 'Dec' option, paste or type in the decimal value you found in the log file and then select the 'Hex' option.</span></span>  
  
-   <span data-ttu-id="e8d4d-187">次に、「 [User-Account-Control 属性](https://go.microsoft.com/fwlink/?LinkId=183366) 」を参照して、サービス アカウントの属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-187">Then refer to the topic [User-Account-Control Attribute](https://go.microsoft.com/fwlink/?LinkId=183366) to derive the attribute for the service account.</span></span>  
  
##### <a name="spns-configured-in-active-directory-for-the-reporting-services-service-account"></a><span data-ttu-id="e8d4d-188">Reporting Services サービス アカウントに対して Active Directory で構成された SPN</span><span class="sxs-lookup"><span data-stu-id="e8d4d-188">SPNs Configured in Active Directory for the Reporting Services service account.</span></span>  
 <span data-ttu-id="e8d4d-189">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスのトレース ログ ファイルに SPN が記録されるようにするために、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の拡張保護機能を一時的に有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-189">To log the SPNs in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service trace log file, you can enable the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Extended Protection feature temporarily.</span></span>  
  
-   <span data-ttu-id="e8d4d-190">構成ファイル `rsreportserver.config` を次のように設定して変更します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-190">Modify the configuration file `rsreportserver.config` by setting the following:</span></span>  
  
    ```  
    <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>   
    <RSWindowsExtendedProtectionScenario>Any</RSWindowsExtendedProtectionScenario>  
    ```  
  
-   <span data-ttu-id="e8d4d-191">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-191">Restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>

 <span data-ttu-id="e8d4d-192">拡張保護の使用を止める場合は、構成値を既定に戻し、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アカウントを再開します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-192">If you do not want continue using Extended Protection, then set the configuration values back to defaults and restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service account.</span></span>  
  
```  
<RSWindowsExtendedProtectionLevel>Off</RSWindowsExtendedProtectionLevel>  
<RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
```  
  
 <span data-ttu-id="e8d4d-193">詳細については、「」、「認証の拡張保護」を参照してください[Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="e8d4d-193">For more information see, [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span></span>  
  
#### <a name="how-the-browser-chooses-negotiated-kerberos-or-negotiated-ntlm"></a><span data-ttu-id="e8d4d-194">ネゴシエートされた Kerberos またはネゴシエートされた NTLM がブラウザーで選択されるしくみ</span><span class="sxs-lookup"><span data-stu-id="e8d4d-194">How the Browser Chooses Negotiated Kerberos or Negotiated NTLM</span></span>  
 <span data-ttu-id="e8d4d-195">Internet Explorer を使用してレポート サーバーに接続すると、認証ヘッダーでネゴシエートされた Kerberos または NTLM が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-195">When you use Internet Explorer to connect to the report server, it specifies either Negotiated Kerberos or NTLM on the authentication header.</span></span> <span data-ttu-id="e8d4d-196">次の場合は、Kerberos に代わって NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-196">NTLM is used instead of Kerberos when:</span></span>  
  
-   <span data-ttu-id="e8d4d-197">要求がローカル レポート サーバーに送信された場合。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-197">The request is sent to a local report server.</span></span>  
  
-   <span data-ttu-id="e8d4d-198">要求が、ホスト ヘッダーまたはサーバー名ではなく、レポート サーバー コンピューターの IP アドレスに送信された場合。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-198">The request is sent to an IP address of the report server computer rather than a host header or server name.</span></span>  
  
-   <span data-ttu-id="e8d4d-199">Kerberos 認証に使用されるポートがファイアウォール ソフトウェアでブロックされた場合。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-199">Firewall software blocks ports used for Kerberos authentication.</span></span>  
  
-   <span data-ttu-id="e8d4d-200">特定のサーバーのオペレーティング システムで Kerberos が有効になっていない場合。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-200">The operating system of a particular server does not have Kerberos enabled.</span></span>  
  
-   <span data-ttu-id="e8d4d-201">ドメインに含まれている古いバージョンの Windows クライアントおよびサーバー オペレーティング システムが、そのオペレーティング システムの新しいバージョンに組み込まれている Kerberos 認証機能をサポートしていない場合。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-201">The domain includes older versions of Windows client and server operating systems that do not support the Kerberos authentication feature built into newer versions of the operating system.</span></span>  
  
 <span data-ttu-id="e8d4d-202">さらに Internet Explorer では、URL、LAN、およびプロキシの設定内容に応じて、ネゴシエートされた Kerberos または NTLM が選択されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-202">In addition, Internet Explorer might choose either Negotiated Kerberos or NTLM depending on how you configured URL, LAN, and proxy settings.</span></span>  
  
###### <a name="report-server-url"></a><span data-ttu-id="e8d4d-203">レポート サーバーの URL</span><span class="sxs-lookup"><span data-stu-id="e8d4d-203">Report Server URL</span></span>  
 <span data-ttu-id="e8d4d-204">URL に完全修飾ドメイン名が含まれている場合、Internet Explorer は NTLM を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-204">If the URL includes a fully qualified domain name, Internet Explorer selects NTLM.</span></span> <span data-ttu-id="e8d4d-205">URL で localhost が指定されている場合も、Internet Explorer は NTLM を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-205">If the URL specifies localhost, Internet Explorer selects NTLM.</span></span> <span data-ttu-id="e8d4d-206">URL でコンピューターのネットワーク名が指定されている場合、Internet Explorer はネゴシエートを選択します。この認証は、レポート サーバー サービス アカウントに SPN が存在するかどうかによって成功または失敗します。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-206">If the URL specifies the network name of the computer, Internet Explorer selects Negotiate, which will succeed or fail depending on whether an SPN exists for the Report Server service account.</span></span>  
  
###### <a name="lan-and-proxy-settings-on-the-client"></a><span data-ttu-id="e8d4d-207">クライアントでの LAN とプロキシの設定</span><span class="sxs-lookup"><span data-stu-id="e8d4d-207">LAN and Proxy Settings on the Client</span></span>  
 <span data-ttu-id="e8d4d-208">Internet Explorer での LAN とプロキシの設定によって、NTLM が Kerberos の代わりに選択されるかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-208">LAN and proxy settings that you set in Internet Explorer can determine whether NTLM is chosen over Kerberos.</span></span> <span data-ttu-id="e8d4d-209">ただし、LAN とプロキシの設定は組織間で異なるため、Kerberos 認証エラーがどの設定に起因するかを正確に特定することは不可能です。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-209">However, because LAN and proxy settings vary across organizations, it is not possible to precisely determine the exact settings that contribute to Kerberos authentication errors.</span></span> <span data-ttu-id="e8d4d-210">たとえば所属する組織で、URL を、イントラネット URL から完全修飾ドメイン名 URL (インターネット接続経由で解決される URL) に変換するようなプロキシ設定が実施されているとします。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-210">For example, your organization might enforce proxy settings that transform URLs from intranet URLs to fully-qualified domain name URLs that resolve over Internet connections.</span></span> <span data-ttu-id="e8d4d-211">種類の異なる URL に種類の異なる認証プロバイダーが使用されると、失敗すると予想した接続が成功することがあります。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-211">If different authentication providers are used for different types of URLs, you might find that some connections succeed when you would have expected them to fail.</span></span>  
  
 <span data-ttu-id="e8d4d-212">認証の失敗が原因と考えられる接続エラーが発生した場合は、問題の原因を特定するために、LAN とプロキシの設定の組み合わせを変えてみてください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-212">If you encounter connection errors that you think are due to authentication failures, you can try different combinations of LAN and proxy settings to isolate the problem.</span></span> <span data-ttu-id="e8d4d-213">Internet Explorer では、LAN とプロキシの設定を **[ローカル エリア ネットワーク (LAN) の設定]** ダイアログ ボックスで行います。このダイアログ ボックスを開くには、 **[インターネット オプション]** の **[接続]** タブで **[LAN の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-213">In Internet Explorer, LAN and proxy settings are on the **Local Area Network (LAN) Settings** dialog box, which you open by clicking **LAN settings** on the **Connection** tab of **Internet Options**.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e8d4d-214">外部リソース</span><span class="sxs-lookup"><span data-stu-id="e8d4d-214">External resources</span></span>  
  
-   <span data-ttu-id="e8d4d-215">Kerberos とレポート サーバーの詳細については、 [SharePoint、Reporting Services、PerformancePoint Monitoring Server と Kerberos を使用したビジネス インテリジェンス ソリューションの展開](https://go.microsoft.com/fwlink/?LinkID=177751)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8d4d-215">For additional information regarding Kerberos and report servers, see [Deploying a Business Intelligence Solution Using SharePoint, Reporting Services, and PerformancePoint Monitoring Server with Kerberos.](https://go.microsoft.com/fwlink/?LinkID=177751)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d4d-216">参照</span><span class="sxs-lookup"><span data-stu-id="e8d4d-216">See Also</span></span>  
 <span data-ttu-id="e8d4d-217">[レポート サーバーでの認証](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8d4d-217">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="e8d4d-218">[ネイティブ モードのレポート サーバーに対する権限の許可](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8d4d-218">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="e8d4d-219">[RSReportServer 構成ファイル](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="e8d4d-219">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="e8d4d-220">[レポートサーバーで基本認証を構成する](configure-basic-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8d4d-220">[Configure Basic Authentication on the Report Server](configure-basic-authentication-on-the-report-server.md) </span></span>  
 <span data-ttu-id="e8d4d-221">[レポートサーバーでカスタム認証またはフォーム認証を構成する](configure-custom-or-forms-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8d4d-221">[Configure Custom or Forms Authentication on the Report Server](configure-custom-or-forms-authentication-on-the-report-server.md) </span></span>  
 [<span data-ttu-id="e8d4d-222">Reporting Services での認証の拡張保護</span><span class="sxs-lookup"><span data-stu-id="e8d4d-222">Extended Protection for Authentication with Reporting Services</span></span>](extended-protection-for-authentication-with-reporting-services.md)  
  
  
