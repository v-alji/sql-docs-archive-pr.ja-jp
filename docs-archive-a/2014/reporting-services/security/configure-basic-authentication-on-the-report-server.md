---
title: レポート サーバーで基本認証を構成する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- Basic authentication
ms.assetid: 8faf2938-b71b-4e61-a172-46da2209ff55
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07f860a67e02c3eb29c5af4f480d3817c55c507f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633724"
---
# <a name="configure-basic-authentication-on-the-report-server"></a><span data-ttu-id="77f45-102">レポート サーバーで基本認証を構成する</span><span class="sxs-lookup"><span data-stu-id="77f45-102">Configure Basic Authentication on the Report Server</span></span>
  <span data-ttu-id="77f45-103">Reporting Services は、既定では、ネゴシエート認証および NTLM 認証を指定する要求を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="77f45-103">By default, Reporting Services accepts requests that specify Negotiate and NTLM authentication.</span></span> <span data-ttu-id="77f45-104">基本認証を使用するクライアント アプリケーションやブラウザーが配置に含まれる場合は、サポートされる種類の一覧に基本認証を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77f45-104">If your deployment includes client applications or browsers that use Basic authentication, you must add Basic authentication to the list of supported types.</span></span> <span data-ttu-id="77f45-105">また、レポート ビルダーを使用する場合は、レポート ビルダーのファイルへの匿名アクセスを有効にする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="77f45-105">In addition, if you want to use Report Builder, you must enable Anonymous access to the Report Builder files.</span></span>  
  
 <span data-ttu-id="77f45-106">レポート サーバーで基本認証を構成するには、RSReportServer.config ファイルの XML 要素と値を編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77f45-106">To configure Basic authentication on the report server, you edit XML elements and values in the RSReportServer.config file.</span></span> <span data-ttu-id="77f45-107">既定値を置き換える際に、このトピックの例をコピーして貼り付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="77f45-107">You can copy and paste the examples in this topic to replace the default values.</span></span>  
  
 <span data-ttu-id="77f45-108">基本認証を有効にする前に、セキュリティ インフラストラクチャで基本認証がサポートされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="77f45-108">Before you enable Basic authentication, verify that your security infrastructure supports it.</span></span> <span data-ttu-id="77f45-109">基本認証では、レポート サーバー Web サービスがローカル セキュリティ機関に資格情報を渡します。</span><span class="sxs-lookup"><span data-stu-id="77f45-109">Under Basic authentication, the Report Server Web service will pass credentials to the local security authority.</span></span> <span data-ttu-id="77f45-110">資格情報でローカル ユーザー アカウントが指定されていた場合は、ユーザーはレポート サーバー コンピューター上のローカル セキュリティ機関によって認証されて、ローカル リソースに対して有効なセキュリティ トークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="77f45-110">If the credentials specify a local user account, the user is authenticated by the local security authority on the report server computer and the user will get a security token that is valid for local resources.</span></span> <span data-ttu-id="77f45-111">ドメイン ユーザー アカウントの資格情報は、ドメイン コントローラーに転送されて認証されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-111">Credentials for domain user accounts are forwarded to and authenticated by a domain controller.</span></span> <span data-ttu-id="77f45-112">この場合は、認証が完了すると、ネットワーク リソースに対して有効なチケットが渡されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-112">The resulting ticket is valid for network resources.</span></span>  
  
 <span data-ttu-id="77f45-113">資格情報がネットワークのドメイン コントローラーに転送される間に傍受されるリスクを軽減するには、チャネルの暗号化 (Secure Sockets Layer (SSL) など) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77f45-113">Channel encryption, such as Secure Sockets Layer (SSL), is required if you want to mitigate the risk of having credentials intercepted while in transit to a domain controller in your network.</span></span> <span data-ttu-id="77f45-114">基本認証のみを使用した場合、ユーザー名はクリア テキストで転送され、パスワードは Base64 エンコード形式で転送されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-114">By itself, Basic authentication transmits the user name in clear text and the password in base-64 encoding.</span></span> <span data-ttu-id="77f45-115">チャネルの暗号化を追加すると、パケットが読み取り不可能になります。</span><span class="sxs-lookup"><span data-stu-id="77f45-115">Adding channel encryption makes the packet unreadable.</span></span> <span data-ttu-id="77f45-116">詳細については、「 [ネイティブ モードのレポート サーバーでの SSL 接続の構成](configure-ssl-connections-on-a-native-mode-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77f45-116">For more information, see [Configure SSL Connections on a Native Mode Report Server](configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="77f45-117">基本認証を有効にすると、レポートにデータを提供する外部データ ソースへの接続のプロパティをユーザーが設定するときに **[Windows 統合セキュリティ]** オプションを選択できなくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="77f45-117">After you enable Basic authentication, be aware that users cannot select the **Windows integrated security** option when setting connection properties to an external data source that provides data to a report.</span></span> <span data-ttu-id="77f45-118">このオプションは、データ ソース プロパティ ページでグレー表示されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-118">The option will be grayed out in the data source property pages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77f45-119">次に示す手順は、ネイティブ モードのレポート サーバーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="77f45-119">The following instructions are intended for a native mode report server.</span></span> <span data-ttu-id="77f45-120">レポート サーバーを SharePoint 統合モードで配置する場合は、Windows 統合セキュリティを指定する既定の認証設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77f45-120">If the report server is deployed in SharePoint integrated mode, you must use the default authentication settings that specify Windows integrated security.</span></span> <span data-ttu-id="77f45-121">レポート サーバーでは、既定の Windows 認証拡張機能の内部機能を使用して、SharePoint 統合モードのレポート サーバーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="77f45-121">The report server uses internal features in the default Windows Authentication extension to support report server in SharePoint integrated mode.</span></span>  
  
### <a name="to-configure-a-report-server-to-use-basic-authentication"></a><span data-ttu-id="77f45-122">レポート サーバーを構成して基本認証を使用するには</span><span class="sxs-lookup"><span data-stu-id="77f45-122">To configure a report server to use Basic authentication</span></span>  
  
1.  <span data-ttu-id="77f45-123">テキスト エディターで RSReportServer.config を開きます。</span><span class="sxs-lookup"><span data-stu-id="77f45-123">Open RSReportServer.config in a text editor.</span></span>  
  
     <span data-ttu-id="77f45-124">ファイルは\* \<drive> 次\*の場所にあります。MSSQLSERVER\Reporting Services\reportserver</span><span class="sxs-lookup"><span data-stu-id="77f45-124">The file is located at *\<drive>:* \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer.</span></span>  
  
2.  <span data-ttu-id="77f45-125"><`Authentication`> を検索します。</span><span class="sxs-lookup"><span data-stu-id="77f45-125">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="77f45-126">次に示す XML 構造の中でニーズに最も合うものをコピーします。</span><span class="sxs-lookup"><span data-stu-id="77f45-126">Copy one of the following XML structures that best fits your needs.</span></span> <span data-ttu-id="77f45-127">最初の XML 構造には、次のセクションで説明するすべての要素を指定するためのプレースホルダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="77f45-127">The first XML structure provides placeholders for specifying all of the elements, which are described in the next section:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsBasic>  
                       <LogonMethod>3</LogonMethod>  
                       <Realm></Realm>  
                       <DefaultDomain></DefaultDomain>  
                 </RSWindowsBasic>  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     <span data-ttu-id="77f45-128">既定値を使用する場合は、次に示す最小限の要素構造をコピーしてください。</span><span class="sxs-lookup"><span data-stu-id="77f45-128">If you are using default values, you can copy the minimum element structure:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsBasic/>  
          </AuthenticationTypes>  
    ```  
  
4.  <span data-ttu-id="77f45-129"><> の既存のエントリの上に貼り付け `Authentication` ます。</span><span class="sxs-lookup"><span data-stu-id="77f45-129">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="77f45-130">複数の認証の種類を使用する場合は、`RSWindowsBasic` 要素を追加するだけにして、`RSWindowsNegotiate`、`RSWindowsNTLM`、および `RSWindowsKerberos` の各エントリは削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="77f45-130">If you are using multiple authentication types, add just the `RSWindowsBasic` element but do not delete the entries for `RSWindowsNegotiate`, `RSWindowsNTLM`, or `RSWindowsKerberos`.</span></span>  
  
     <span data-ttu-id="77f45-131">Safari ブラウザーをサポートする場合は、複数の認証の種類を使用できるようにレポート サーバーを構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="77f45-131">To support the Safari browser, you cannot configure the report server to use multiple authentication types.</span></span> <span data-ttu-id="77f45-132">`RSWindowsBasic` のみを指定して、その他のエントリを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77f45-132">You must specify only `RSWindowsBasic` and delete the other entries.</span></span>  
  
     <span data-ttu-id="77f45-133">`Custom` は他の認証の種類と併用できないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="77f45-133">Note that you cannot use `Custom` with other authentication types.</span></span>  
  
5.  <span data-ttu-id="77f45-134"><`Realm`> または <> の空の値 `DefaultDomain` を、使用している環境に対して有効な値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="77f45-134">Replace empty values for <`Realm`> or <`DefaultDomain`> with values that are valid for your environment.</span></span>  
  
6.  <span data-ttu-id="77f45-135">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="77f45-135">Save the file.</span></span>  
  
7.  <span data-ttu-id="77f45-136">スケールアウト配置を構成した場合は、配置内の他のレポート サーバーに対して上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="77f45-136">If you configured a scale-out deployment, repeat these steps for other report servers in the deployment.</span></span>  
  
8.  <span data-ttu-id="77f45-137">レポート サーバーを再起動して、現在開いているセッションを消去します。</span><span class="sxs-lookup"><span data-stu-id="77f45-137">Restart the report server to clear any sessions that are currently open.</span></span>  
  
## <a name="rswindowsbasic-reference"></a><span data-ttu-id="77f45-138">RSWindowsBasic リファレンス</span><span class="sxs-lookup"><span data-stu-id="77f45-138">RSWindowsBasic Reference</span></span>  
 <span data-ttu-id="77f45-139">基本認証を構成するときには次の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="77f45-139">The following elements can be specified when configuring Basic authentication.</span></span>  
  
|<span data-ttu-id="77f45-140">要素</span><span class="sxs-lookup"><span data-stu-id="77f45-140">Element</span></span>|<span data-ttu-id="77f45-141">必須</span><span class="sxs-lookup"><span data-stu-id="77f45-141">Required</span></span>|<span data-ttu-id="77f45-142">有効な値</span><span class="sxs-lookup"><span data-stu-id="77f45-142">Valid Values</span></span>|  
|-------------|--------------|------------------|  
|<span data-ttu-id="77f45-143">LogonMethod</span><span class="sxs-lookup"><span data-stu-id="77f45-143">LogonMethod</span></span>|<span data-ttu-id="77f45-144">はい</span><span class="sxs-lookup"><span data-stu-id="77f45-144">Yes</span></span><br /><br /> <span data-ttu-id="77f45-145">値を指定しない場合は 3 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-145">If you do not specify a value, 3 will be used.</span></span>|<span data-ttu-id="77f45-146">`2`= ネットワークログオン。プレーンテキストパスワードを認証する高パフォーマンスサーバーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="77f45-146">`2` = Network logon, intended for high performance servers to authenticate plain text passwords.</span></span><br /><br /> <span data-ttu-id="77f45-147">`3` = クリア テキスト ログオン。各 HTTP 要求と一緒に送信される認証パッケージにログオン資格情報が保持されます。これにより、ネットワーク内の他のサーバーに接続する際に、サーバーがユーザーの権限を借用できます。</span><span class="sxs-lookup"><span data-stu-id="77f45-147">`3` = Cleartext logon, which preserves logon credentials in the authentication package that is sent with each HTTP request, allowing the server to impersonate the user when connecting to other servers in the network.</span></span> <span data-ttu-id="77f45-148">(既定)</span><span class="sxs-lookup"><span data-stu-id="77f45-148">(Default)</span></span><br /><br /> <span data-ttu-id="77f45-149">注:値 0 (対話型ログオン) と値 1 (バッチ ログオン) は、[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="77f45-149">Note: Values 0 (for interactive logon) and 1 (for batch logon) are not supported in [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].</span></span>|  
|<span data-ttu-id="77f45-150">Realm</span><span class="sxs-lookup"><span data-stu-id="77f45-150">Realm</span></span>|<span data-ttu-id="77f45-151">省略可能</span><span class="sxs-lookup"><span data-stu-id="77f45-151">Optional</span></span>|<span data-ttu-id="77f45-152">組織内の保護されたリソースへのアクセスを制御するための承認機能や認証機能を含んだリソース パーティションを指定します。</span><span class="sxs-lookup"><span data-stu-id="77f45-152">Specifies a resource partition that includes authorization and authentication features used to control access to protected resources in your organization.</span></span>|  
|<span data-ttu-id="77f45-153">DefaultDomain</span><span class="sxs-lookup"><span data-stu-id="77f45-153">DefaultDomain</span></span>|<span data-ttu-id="77f45-154">省略可能</span><span class="sxs-lookup"><span data-stu-id="77f45-154">Optional</span></span>|<span data-ttu-id="77f45-155">サーバーがユーザーを認証する際のドメインを指定します。</span><span class="sxs-lookup"><span data-stu-id="77f45-155">Specifies the domain used by the server to authenticate the user.</span></span> <span data-ttu-id="77f45-156">この値はオプションです。ただし、省略した場合、レポート サーバーでは、コンピューター名がドメインとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-156">This value is optional, but if you omit it the report server will use the computer name as the domain.</span></span> <span data-ttu-id="77f45-157">コンピューターがドメインのメンバーになっている場合は、そのドメインが既定のドメインです。</span><span class="sxs-lookup"><span data-stu-id="77f45-157">If the computer is a member of domain, that domain is the default domain.</span></span> <span data-ttu-id="77f45-158">レポート サーバーをドメイン コントローラーにインストールした場合、そのコンピューターによって制御されるドメインを指定します。</span><span class="sxs-lookup"><span data-stu-id="77f45-158">If you installed the report server on a domain controller, the domain used is the one controlled by the computer.</span></span>|  
  
## <a name="enabling-anonymous-access-to-report-builder-application-files"></a><span data-ttu-id="77f45-159">レポート ビルダー アプリケーション ファイルへの匿名アクセスの有効化</span><span class="sxs-lookup"><span data-stu-id="77f45-159">Enabling Anonymous Access to Report Builder Application Files</span></span>  
 <span data-ttu-id="77f45-160">レポート ビルダーは、ClickOnce テクノロジを使用して、アプリケーション ファイルをクライアント コンピューターにダウンロードおよびインストールします。</span><span class="sxs-lookup"><span data-stu-id="77f45-160">Report Builder uses ClickOnce technology to download and install application files on the client computer.</span></span> <span data-ttu-id="77f45-161">クライアント コンピューターでレポート ビルダーを起動すると、ClickOnce アプリケーション ランチャーがレポート サーバー コンピューター上の追加のアプリケーション ファイルを要求します。</span><span class="sxs-lookup"><span data-stu-id="77f45-161">When it starts on the client computer, the ClickOnce application launcher will make a request for additional application files on the report server computer.</span></span> <span data-ttu-id="77f45-162">レポート サーバーが基本認証用に構成されている場合、ClickOnce アプリケーション ランチャーは基本認証をサポートしていないため、認証チェックが失敗します。</span><span class="sxs-lookup"><span data-stu-id="77f45-162">If the report server is configured for Basic authentication, the ClickOnce application launcher will fail the authentication check because it does not support Basic authentication.</span></span>  
  
 <span data-ttu-id="77f45-163">この問題を回避するには、レポート ビルダーのプログラム ファイルへの匿名アクセスを構成します。</span><span class="sxs-lookup"><span data-stu-id="77f45-163">To work around this issue, you can configure Anonymous access to the Report Builder program files.</span></span> <span data-ttu-id="77f45-164">これにより、ClickOnce がファイルを取得するときに認証チェックを省略できるようになります。</span><span class="sxs-lookup"><span data-stu-id="77f45-164">Doing so allows ClickOnce to bypass the authentication check when retrieving its files.</span></span> <span data-ttu-id="77f45-165">匿名アクセスを有効にするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="77f45-165">Enable Anonymous access by doing the following:</span></span>  
  
-   <span data-ttu-id="77f45-166">レポート サーバーが基本認証用に構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="77f45-166">Verify that the report server is configured for Basic authentication.</span></span>  
  
-   <span data-ttu-id="77f45-167">ReportBuilder フォルダーの下に bin フォルダーを作成し、そのフォルダーに 4 つのアセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="77f45-167">Create a bin folder under ReportBuilder and copy four assemblies to the folder.</span></span>  
  
-   <span data-ttu-id="77f45-168">RSReportServer.config に `IsReportBuilderAnonymousAccessEnabled` 要素を追加して、`True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="77f45-168">Add the `IsReportBuilderAnonymousAccessEnabled` element to the RSReportServer.config and set it to `True`.</span></span> <span data-ttu-id="77f45-169">ファイルを保存すると、レポート ビルダーへの新しいエンドポイントがレポート サーバーによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-169">After you save the file, the report server creates a new endpoint to Report Builder.</span></span> <span data-ttu-id="77f45-170">このエンドポイントは、プログラム ファイルにアクセスするために内部で使用されるものであり、コードで使用できるプログラマティック インターフェイスはありません。</span><span class="sxs-lookup"><span data-stu-id="77f45-170">The endpoint is used internally to access program files and does not have a programmatic interface that you can use in code.</span></span> <span data-ttu-id="77f45-171">別のエンドポイントを使用することにより、レポート サーバー サービス プロセス境界内の独自のアプリケーション ドメインでレポート ビルダーを実行することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="77f45-171">Having a separate endpoint allows Report Builder to run in its own application domain within the Report Server service process boundary.</span></span>  
  
-   <span data-ttu-id="77f45-172">必要に応じて最小特権のアカウントを指定して、レポート サーバーとは別のセキュリティ コンテキストで要求を処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="77f45-172">Optionally, you can specify a least-privilege account to process requests under a security context that is different from the report server.</span></span> <span data-ttu-id="77f45-173">このアカウントは、レポート サーバー上のレポート ビルダー ファイルにアクセスするための匿名アカウントになります。</span><span class="sxs-lookup"><span data-stu-id="77f45-173">This account becomes the anonymous account for accessing Report Builder files on a report server.</span></span> <span data-ttu-id="77f45-174">このアカウントによって ASP.NET ワーカー プロセスのスレッドの ID が設定され、</span><span class="sxs-lookup"><span data-stu-id="77f45-174">The account sets the identity of the thread in the ASP.NET worker process.</span></span> <span data-ttu-id="77f45-175">そのスレッドで実行される要求は認証チェックなしでレポート サーバーに渡されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-175">Requests that run in that thread are passed to the report server without an authentication check.</span></span> <span data-ttu-id="77f45-176">このアカウントは \<machine> インターネットインフォメーションサービス (IIS) の IUSR_ アカウントに相当します。これは、匿名アクセスと偽装が有効になっている場合に ASP.NET ワーカープロセスのセキュリティコンテキストを設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-176">This account is equivalent to the IUSR_\<machine> account in Internet Information Services (IIS), which is used to set the security context for ASP.NET worker processes when Anonymous access and impersonation are enabled.</span></span> <span data-ttu-id="77f45-177">アカウントを指定するには、レポート ビルダーの Web.config ファイルにそのアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="77f45-177">To specify the account, you add it to a Report Builder Web.config file.</span></span>  
  
 <span data-ttu-id="77f45-178">レポート ビルダーのプログラム ファイルへの匿名アクセスを有効にする場合は、レポート サーバーが基本認証用に構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="77f45-178">The report server must be configured for Basic authentication if you want to enable Anonymous access to the Report Builder program files.</span></span> <span data-ttu-id="77f45-179">レポート サーバーが基本認証用に構成されていない場合、匿名アクセスを有効にしようとするとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="77f45-179">If the report server is not configured for Basic authentication, you will get an error when you attempt to enable Anonymous access.</span></span>  
  
 <span data-ttu-id="77f45-180">レポート ビルダーと認証の問題の詳細については、「[レポート ビルダーへのアクセスの構成](../report-server/configure-report-builder-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77f45-180">For more information about authentication issues and Report Builder, see [Configure Report Builder Access](../report-server/configure-report-builder-access.md).</span></span>  
  
#### <a name="to-configure-report-builder-access-on-a-report-server-configured-for-basic-authentication"></a><span data-ttu-id="77f45-181">基本認証用に構成されたレポート サーバーでレポート ビルダーへのアクセスを構成するには</span><span class="sxs-lookup"><span data-stu-id="77f45-181">To configure Report Builder access on a report server configured for Basic authentication</span></span>  
  
1.  <span data-ttu-id="77f45-182">RSReportServer.config ファイルの認証設定をチェックして、レポート サーバーが基本認証用に構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="77f45-182">Verify the report server is configured for Basic authentication by checking the authentication settings in the RSReportServer.config file.</span></span>  
  
2.  <span data-ttu-id="77f45-183">ReportBuilder フォルダーの下に BIN フォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="77f45-183">Create a BIN folder under the ReportBuilder folder.</span></span> <span data-ttu-id="77f45-184">既定では、このフォルダーは \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder にあります。</span><span class="sxs-lookup"><span data-stu-id="77f45-184">By default, this folder is located at \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder.</span></span>  
  
3.  <span data-ttu-id="77f45-185">ReportServer\Bin フォルダーから ReportBuilder\BIN フォルダーに次のアセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="77f45-185">Copy the following assemblies from the ReportServer\Bin folder to the ReportBuilder\BIN folder:</span></span>  
  
     <span data-ttu-id="77f45-186">Microsoft.ReportingServices.Diagnostics.dll</span><span class="sxs-lookup"><span data-stu-id="77f45-186">Microsoft.ReportingServices.Diagnostics.dll</span></span>  
  
     <span data-ttu-id="77f45-187">Microsoft.ReportingServices.Interfaces.dll</span><span class="sxs-lookup"><span data-stu-id="77f45-187">Microsoft.ReportingServices.Interfaces.dll</span></span>  
  
     <span data-ttu-id="77f45-188">ReportingServicesAppDomainManager.dll</span><span class="sxs-lookup"><span data-stu-id="77f45-188">ReportingServicesAppDomainManager.dll</span></span>  
  
     <span data-ttu-id="77f45-189">RSHttpRuntime.dll</span><span class="sxs-lookup"><span data-stu-id="77f45-189">RSHttpRuntime.dll</span></span>  
  
4.  <span data-ttu-id="77f45-190">必要に応じて、レポート ビルダーの要求を匿名アカウントで処理するための Web.config ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="77f45-190">Optionally, create a Web.config file to process Report Builder requests under an Anonymous account:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
    <system.web>  
    <authentication mode="Windows" />    
    <identity impersonate="true " userName="username" password="password"/>  
    </system.web>  
    </configuration>  
    ```  
  
     <span data-ttu-id="77f45-191">Web.config ファイルを含める場合は、認証モードを `Windows` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77f45-191">Authentication mode must be set to `Windows` if you include a Web.config file.</span></span>  
  
     <span data-ttu-id="77f45-192">`Identity impersonate` には、`True` または `False` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="77f45-192">`Identity impersonate` can be `True` or `False`.</span></span>  
  
    -   <span data-ttu-id="77f45-193">ASP.NET がセキュリティ トークンを読み取らないようにする場合は、`False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="77f45-193">Set it to `False` if you do not want ASP.NET to read the security token.</span></span> <span data-ttu-id="77f45-194">この場合、要求はレポート サーバー サービスのセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="77f45-194">The request will run in the security context of the Report Server service.</span></span>  
  
    -   <span data-ttu-id="77f45-195">ASP.NET がホスト層からセキュリティ トークンを読み取るようにする場合は、`True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="77f45-195">Set it to `True` if you want ASP.NET to read the security token from the host layer.</span></span> <span data-ttu-id="77f45-196">`True` に設定した場合は、`userName` と `password` を指定して匿名アカウントを指定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="77f45-196">If you set it to `True`, you must also specify `userName` and `password` to designate an Anonymous account.</span></span> <span data-ttu-id="77f45-197">指定する資格情報により、要求が発行されるセキュリティ コンテキストが決まります。</span><span class="sxs-lookup"><span data-stu-id="77f45-197">The credentials you specify will determine the security context under which the request is issued.</span></span>  
  
5.  <span data-ttu-id="77f45-198">Web.config ファイルを ReportBuilder\bin フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="77f45-198">Save the Web.config file to the ReportBuilder\bin folder.</span></span>  
  
6.  <span data-ttu-id="77f45-199">RSReportServer.config ファイルを開き、Services セクションで `IsReportManagerEnabled` を見つけて、その下に次の設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="77f45-199">Open RSReportServer.config file, in the Services section, find `IsReportManagerEnabled` and add the following setting below it:</span></span>  
  
    ```  
    <IsReportBuilderAnonymousAccessEnabled>True</IsReportBuilderAnonymousAccessEnabled>  
    ```  
  
7.  <span data-ttu-id="77f45-200">RSReportServer.config ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="77f45-200">Save RSReportServer.config and close the file.</span></span>  
  
8.  <span data-ttu-id="77f45-201">レポート サーバーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="77f45-201">Restart the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f45-202">参照</span><span class="sxs-lookup"><span data-stu-id="77f45-202">See Also</span></span>  
 <span data-ttu-id="77f45-203">[レポート サーバー アプリケーションのアプリケーション ドメイン](../report-server/application-domains-for-report-server-applications.md) </span><span class="sxs-lookup"><span data-stu-id="77f45-203">[Application Domains for Report Server Applications](../report-server/application-domains-for-report-server-applications.md) </span></span>  
 [<span data-ttu-id="77f45-204">Reporting Services のセキュリティと保護</span><span class="sxs-lookup"><span data-stu-id="77f45-204">Reporting Services Security and Protection</span></span>](reporting-services-security-and-protection.md)  
  
  
