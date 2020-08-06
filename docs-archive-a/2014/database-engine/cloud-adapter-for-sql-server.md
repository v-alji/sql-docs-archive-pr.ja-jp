---
title: SQL Server | のクラウドアダプターMicrosoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cloud adapter
- Deploy to Azure
ms.assetid: 82ed0d0f-952d-4d49-aa36-3855a3ca9877
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5716435bb1db494bdabeb45ed366c1783926989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642326"
---
# <a name="cloud-adapter-for-sql-server"></a><span data-ttu-id="35829-102">SQL Server のクラウド アダプター</span><span class="sxs-lookup"><span data-stu-id="35829-102">Cloud Adapter for SQL Server</span></span>
  <span data-ttu-id="35829-103">クラウドアダプターサービスは、Azure VM でのプロビジョニングの一部として作成され [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="35829-103">The Cloud Adapter service is created as part of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provisioning on an Azure VM.</span></span> <span data-ttu-id="35829-104">クラウド アダプター サービスは、最初の実行時に自己署名 SSL 証明書を生成し、 **Local System** アカウントとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="35829-104">The Cloud Adapter service generates a self-signed SSL certificate as part of its first run, and then runs as a **Local System** account.</span></span> <span data-ttu-id="35829-105">その際に、自身を構成するために使用される構成ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="35829-105">It generates a configuration file that is used to configure itself.</span></span> <span data-ttu-id="35829-106">また、クラウド アダプターでは、既定のポート 11435 での着信 TCP 接続を許可する Windows ファイアウォール ルールも作成されます。</span><span class="sxs-lookup"><span data-stu-id="35829-106">The Cloud Adapter also creates a Windows Firewall rule to allow its incoming TCP connections at default port 11435.</span></span>  
  
 <span data-ttu-id="35829-107">クラウド アダプターは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の内部設置型インスタンスからメッセージを受信するステートレスな同期サービスです。</span><span class="sxs-lookup"><span data-stu-id="35829-107">The Cloud Adapter is a stateless, synchronous service that receives messages from the on-premise instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="35829-108">クラウド アダプター サービスが停止すると、リモート アクセス クラウド アダプターが停止され、SSL 証明書のバインドが解除され、Windows ファイアウォールのルールが無効になります。</span><span class="sxs-lookup"><span data-stu-id="35829-108">When the Cloud Adapter service is stopped, it stops the remote access Cloud Adapter, unbinds the SSL certificate, and disables the Windows Firewall rule.</span></span>  
  
## <a name="cloud-adapter-requirements"></a><span data-ttu-id="35829-109">クラウド アダプターの要件</span><span class="sxs-lookup"><span data-stu-id="35829-109">Cloud Adapter Requirements</span></span>  
 <span data-ttu-id="35829-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に対してクラウド アダプターをインストールして有効にし、実行するには、次の要件が必要です。</span><span class="sxs-lookup"><span data-stu-id="35829-110">Note the following requirements to install, enable, and run the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="35829-111">クラウド アダプターは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="35829-111">Cloud Adapter is supported with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 and higher.</span></span> <span data-ttu-id="35829-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクラウド アダプターは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 に対応する SQL 管理オブジェクトを必要とします。</span><span class="sxs-lookup"><span data-stu-id="35829-112">On [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012, the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requires SQL Management Objects for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012.</span></span>  
  
-   <span data-ttu-id="35829-113">クラウド アダプター Web サービスは **ローカル システム** アカウントとして実行され、タスクを実行する前にクライアントの資格情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="35829-113">Cloud Adapter web service runs as a **Local System** account and verifies client credentials before executing any task.</span></span> <span data-ttu-id="35829-114">クライアントによって指定された資格情報は、リモートコンピューターのローカル**管理者**グループのメンバーである使用アカウントに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="35829-114">Credentials supplied by the client must belong to the use account that is a member of the local **Administrators** group on the remote machine.</span></span>  
  
-   <span data-ttu-id="35829-115">クラウド アダプターでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="35829-115">Cloud Adapter supports only [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
-   <span data-ttu-id="35829-116">クラウド アダプターは、ローカル コンピューター上のコマンドを実行するために sa アカウントではなく仮想マシンのローカル管理者アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="35829-116">Cloud Adapter uses VM local administrator account to execute commands on the local machine, not an sa account.</span></span>  
  
-   <span data-ttu-id="35829-117">クラウド アダプターは TCP/IP をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="35829-117">Cloud Adapter listens on TCP/IP.</span></span> <span data-ttu-id="35829-118">既定のポートは 11435 です。</span><span class="sxs-lookup"><span data-stu-id="35829-118">The default port is 11435.</span></span>  
  
-   <span data-ttu-id="35829-119">クラウド アダプターは Windows ファイアウォール ルールを作成および変更する権限を必要とします。</span><span class="sxs-lookup"><span data-stu-id="35829-119">Cloud Adapter must have permissions to create and modify Windows Firewall rules.</span></span>  
  
## <a name="cloud-adapter-configuration-settings"></a><span data-ttu-id="35829-120">クラウド アダプター構成の設定</span><span class="sxs-lookup"><span data-stu-id="35829-120">Cloud Adapter Configuration Settings</span></span>  
 <span data-ttu-id="35829-121">クラウド アダプターの設定を変更するには、クラウド アダプターの構成の詳細を使用します。</span><span class="sxs-lookup"><span data-stu-id="35829-121">Use the following Cloud Adapter configuration details to modify settings for a Cloud Adapter.</span></span>  
  
-   <span data-ttu-id="35829-122">**構成ファイルの既定のパス**-C:\PROGRAM "SQL \" \ "</span><span class="sxs-lookup"><span data-stu-id="35829-122">**Default path for the configuration file** - C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter\</span></span>  
  
-   <span data-ttu-id="35829-123">**構成ファイルのパラメーター** -</span><span class="sxs-lookup"><span data-stu-id="35829-123">**Configuration file parameters** -</span></span>  
  
    -   \<configuration>  
  
        -   \<appSettings>  
  
            -   \<add key="WebServicePort" value="" />  
  
            -   \<add key="WebServiceCertificate" value="GUID" />  
  
            -   \<add key="ExposeExceptionDetails" value="true" />  
  
        -   \</appSettings>  
  
    -   \</configuration>  
  
-   <span data-ttu-id="35829-124">**証明書の詳細**-証明書の値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="35829-124">**Certificate details** - The certificate has the following values:</span></span>  
  
    -   <span data-ttu-id="35829-125">Subject-"CN = CloudAdapter \<VMName> , dc = SQL Server, dc = Microsoft"</span><span class="sxs-lookup"><span data-stu-id="35829-125">Subject - "CN=CloudAdapter\<VMName>, DC=SQL Server, DC=Microsoft"</span></span>  
  
    -   <span data-ttu-id="35829-126">証明書ではサーバー認証 EKU のみを有効にします。</span><span class="sxs-lookup"><span data-stu-id="35829-126">The certificate should have only Server Authentication EKU enabled.</span></span>  
  
    -   <span data-ttu-id="35829-127">証明書キーの長さは 2,048 です。</span><span class="sxs-lookup"><span data-stu-id="35829-127">The certificate key length is 2048.</span></span>  
  
 <span data-ttu-id="35829-128">**構成ファイルの値**:</span><span class="sxs-lookup"><span data-stu-id="35829-128">**Configuration file values**:</span></span>  
  
|<span data-ttu-id="35829-129">設定</span><span class="sxs-lookup"><span data-stu-id="35829-129">Setting</span></span>|<span data-ttu-id="35829-130">値</span><span class="sxs-lookup"><span data-stu-id="35829-130">Values</span></span>|<span data-ttu-id="35829-131">Default</span><span class="sxs-lookup"><span data-stu-id="35829-131">Default</span></span>|<span data-ttu-id="35829-132">説明</span><span class="sxs-lookup"><span data-stu-id="35829-132">Comments</span></span>|  
|-------------|------------|-------------|--------------|  
|<span data-ttu-id="35829-133">WebServicePort</span><span class="sxs-lookup"><span data-stu-id="35829-133">WebServicePort</span></span>|<span data-ttu-id="35829-134">1-65535</span><span class="sxs-lookup"><span data-stu-id="35829-134">1-65535</span></span>|<span data-ttu-id="35829-135">11435</span><span class="sxs-lookup"><span data-stu-id="35829-135">11435</span></span>|<span data-ttu-id="35829-136">指定しない場合、11435 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="35829-136">If not specified, use 11435.</span></span>|  
|<span data-ttu-id="35829-137">WebServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="35829-137">WebServiceCertificate</span></span>|<span data-ttu-id="35829-138">Thumbprint</span><span class="sxs-lookup"><span data-stu-id="35829-138">Thumbprint</span></span>|<span data-ttu-id="35829-139">Empty</span><span class="sxs-lookup"><span data-stu-id="35829-139">Empty</span></span>|<span data-ttu-id="35829-140">空の場合、新しい自己署名証明書が生成されます。</span><span class="sxs-lookup"><span data-stu-id="35829-140">If empty, a new self-signed certificate is generated.</span></span>|  
|<span data-ttu-id="35829-141">ExposeExceptionDetails</span><span class="sxs-lookup"><span data-stu-id="35829-141">ExposeExceptionDetails</span></span>|<span data-ttu-id="35829-142">真/偽</span><span class="sxs-lookup"><span data-stu-id="35829-142">True/False</span></span>|<span data-ttu-id="35829-143">誤り</span><span class="sxs-lookup"><span data-stu-id="35829-143">False</span></span>||  
  
## <a name="cloud-adapter-troubleshooting"></a><span data-ttu-id="35829-144">クラウド アダプターのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="35829-144">Cloud Adapter Troubleshooting</span></span>  
 <span data-ttu-id="35829-145">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のクラウド アダプターのトラブルシューティングを行うには、次の情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="35829-145">Use the following information to troubleshoot the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="35829-146">**エラー処理とログ記録**-エラーと状態メッセージがアプリケーションイベントログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="35829-146">**Error handling and logging** - Errors and status messages are written to the Application Event Log.</span></span>  
  
-   <span data-ttu-id="35829-147">**トレース、イベント**: すべてのイベントがアプリケーションイベントログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="35829-147">**Tracing, Events** - All events are written to the Application Event Log.</span></span>  
  
-   <span data-ttu-id="35829-148">**コントロール、構成**: C:\Program の SQL server にある構成ファイルを使用し \\ ます。</span><span class="sxs-lookup"><span data-stu-id="35829-148">**Control, configuration** - Use the configuration file located in:  C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter\\.</span></span>  
  
|<span data-ttu-id="35829-149">エラー</span><span class="sxs-lookup"><span data-stu-id="35829-149">Error</span></span>|<span data-ttu-id="35829-150">エラー ID</span><span class="sxs-lookup"><span data-stu-id="35829-150">Error ID</span></span>|<span data-ttu-id="35829-151">原因</span><span class="sxs-lookup"><span data-stu-id="35829-151">Cause</span></span>|<span data-ttu-id="35829-152">解像度</span><span class="sxs-lookup"><span data-stu-id="35829-152">Resolution</span></span>|  
|-----------|--------------|-----------|----------------|  
|<span data-ttu-id="35829-153">証明書ストアに証明書を追加中に例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="35829-153">There was an exception while adding the certificate to the certificate store.</span></span> <span data-ttu-id="35829-154">{例外テキスト}。</span><span class="sxs-lookup"><span data-stu-id="35829-154">{Exception text}.</span></span>|<span data-ttu-id="35829-155">45560</span><span class="sxs-lookup"><span data-stu-id="35829-155">45560</span></span>|<span data-ttu-id="35829-156">コンピューター証明書ストアのアクセス許可</span><span class="sxs-lookup"><span data-stu-id="35829-156">Machine certificate store permissions</span></span>|<span data-ttu-id="35829-157">クラウドアダプターサービスに、コンピューター証明書ストアに証明書を追加するためのアクセス許可があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="35829-157">Ensure that the Cloud Adapter service has permissions to add certificates to the machine certificate store.</span></span>|  
|<span data-ttu-id="35829-158">ポート {ポート番号} と証明書 {サムプリント} の SSL バインドを構成しようとして例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="35829-158">There was an exception while trying to configure the SSL binding for port {Port number} and certificate {Thumbprint}.</span></span> <span data-ttu-id="35829-159">{例外}。</span><span class="sxs-lookup"><span data-stu-id="35829-159">{Exception}.</span></span>|<span data-ttu-id="35829-160">45561</span><span class="sxs-lookup"><span data-stu-id="35829-160">45561</span></span>|<span data-ttu-id="35829-161">他のアプリケーションが既にポートを使用しているか、証明書をバインドされています。</span><span class="sxs-lookup"><span data-stu-id="35829-161">Another application has already used the port or bound a certificate to it.</span></span>|<span data-ttu-id="35829-162">既存のバインドを削除するか、または構成ファイルのクラウド アダプターのポートを変更します。</span><span class="sxs-lookup"><span data-stu-id="35829-162">Remove existing bindings or change Cloud Adapter port in the configuration file.</span></span>|  
|<span data-ttu-id="35829-163">証明書ストアで SSL 証明書 [{サムプリント}] が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="35829-163">Failed to find SSL certificate [{Thumbprint}] in the certificate store.</span></span>|<span data-ttu-id="35829-164">45564</span><span class="sxs-lookup"><span data-stu-id="35829-164">45564</span></span>|<span data-ttu-id="35829-165">証明書のサムプリントが構成ファイルにありますが、そのサービスのための個人証明書ストアに証明書が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="35829-165">Certificate thumbprint is in the configuration file, but personal certificate store for the service does not contain certificate.</span></span><br /><br /> <span data-ttu-id="35829-166">権限が不足しています。</span><span class="sxs-lookup"><span data-stu-id="35829-166">Insufficient permissions.</span></span>|<span data-ttu-id="35829-167">サービスの個人証明書ストアに証明書を置きます。</span><span class="sxs-lookup"><span data-stu-id="35829-167">Make sure the certificate is in the personal certificate store for the service.</span></span><br /><br /> <span data-ttu-id="35829-168">サービスに、ストアへの適切な権限があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="35829-168">Make sure the service has correct permissions for the store.</span></span>|  
|<span data-ttu-id="35829-169">Web サービスを開始できませんでした。</span><span class="sxs-lookup"><span data-stu-id="35829-169">Failed to start the web service.</span></span> <span data-ttu-id="35829-170">{例外テキスト}。</span><span class="sxs-lookup"><span data-stu-id="35829-170">{Exception text}.</span></span>|<span data-ttu-id="35829-171">45570</span><span class="sxs-lookup"><span data-stu-id="35829-171">45570</span></span>|<span data-ttu-id="35829-172">例外で説明されています。</span><span class="sxs-lookup"><span data-stu-id="35829-172">Described in the exception.</span></span>|<span data-ttu-id="35829-173">ExposeExceptionDetails を有効にし、例外の拡張情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="35829-173">Enable ExposeExceptionDetails and use extended information from the exception.</span></span>|  
|<span data-ttu-id="35829-174">証明書 [{サムプリント}] の有効期限が切れています。</span><span class="sxs-lookup"><span data-stu-id="35829-174">Certificate [{Thumbprint}] has expired.</span></span>|<span data-ttu-id="35829-175">45565</span><span class="sxs-lookup"><span data-stu-id="35829-175">45565</span></span>|<span data-ttu-id="35829-176">構成ファイルから参照される期限切れの証明書。</span><span class="sxs-lookup"><span data-stu-id="35829-176">Expired certificate referenced from the configuration file.</span></span>|<span data-ttu-id="35829-177">有効な証明書を追加し、サムプリントを使用して構成ファイルを更新します。</span><span class="sxs-lookup"><span data-stu-id="35829-177">Add a valid certificate and update the configuration file with its thumbprint.</span></span>|  
|<span data-ttu-id="35829-178">Web サービスエラー: {0} 。</span><span class="sxs-lookup"><span data-stu-id="35829-178">Web service error: {0}.</span></span>|<span data-ttu-id="35829-179">45571</span><span class="sxs-lookup"><span data-stu-id="35829-179">45571</span></span>|<span data-ttu-id="35829-180">例外で説明されています。</span><span class="sxs-lookup"><span data-stu-id="35829-180">Described in the exception.</span></span>|<span data-ttu-id="35829-181">ExposeExceptionDetails を有効にし、例外の拡張情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="35829-181">Enable ExposeExceptionDetails and use extended information from the exception.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35829-182">参照</span><span class="sxs-lookup"><span data-stu-id="35829-182">See Also</span></span>  
 [<span data-ttu-id="35829-183">Microsoft Azure Virtual Machine の SQL Server データベースの配置</span><span class="sxs-lookup"><span data-stu-id="35829-183">Deploy a SQL Server Database to a Microsoft Azure Virtual Machine</span></span>](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)  
  
  
