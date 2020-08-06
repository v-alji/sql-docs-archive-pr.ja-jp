---
title: Web 同期用の IIS の構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- IIS server configuration [SQL Server replication]
- websync.log
- Web synchronization, IIS servers
ms.assetid: d651186e-c9ca-4864-a444-2cd6943b8e35
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 523c4fc30151acd3ee4df21f2fdaa2187e702870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634403"
---
# <a name="configure-iis-for-web-synchronization"></a><span data-ttu-id="b385b-102">Web 同期用の IIS の構成</span><span class="sxs-lookup"><span data-stu-id="b385b-102">Configure IIS for Web Synchronization</span></span>
  <span data-ttu-id="b385b-103">ここでは、マージ レプリケーション用に Web 同期を構成する 2 番目の手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="b385b-103">The procedures in this topic make up the second step in configuring Web synchronization for merge replication.</span></span> <span data-ttu-id="b385b-104">この手順は、Web 同期用にパブリケーションを有効にした後に実行します。</span><span class="sxs-lookup"><span data-stu-id="b385b-104">You perform this step after you enable a publication for Web synchronization.</span></span> <span data-ttu-id="b385b-105">構成プロセスの概要については、「 [[Web 同期の構成]](configure-web-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-105">For an overview of the configuration process, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span> <span data-ttu-id="b385b-106">ここでの手順を完了したら、続いて、Web 同期が使用されるようにサブスクリプションを構成する 3 番目の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-106">After you complete the procedures in this topic, continue to the third step, configuring a subscription to use Web synchronization.</span></span> <span data-ttu-id="b385b-107">3 番目の手順については、次のトピックで説明します。</span><span class="sxs-lookup"><span data-stu-id="b385b-107">This third step is described in the following topics:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="b385b-108">: [Web 同期が使用されるようにサブスクリプションを構成する方法 \(SQL Server Management Studio\)](https://msdn.microsoft.com/library/ms345214.aspx)</span><span class="sxs-lookup"><span data-stu-id="b385b-108">: [How to: Configure a Subscription to Use Web Synchronization \(SQL Server Management Studio\)](https://msdn.microsoft.com/library/ms345214.aspx)</span></span>  
  
-   <span data-ttu-id="b385b-109">レプリケーション [!INCLUDE[tsql](../../includes/tsql-md.md)] プログラミング: [Web 同期を使用するようにサブスクリプションを構成する方法 (レプリケーション Transact-SQL プログラミング)](https://msdn.microsoft.com/library/ms345206.aspx)</span><span class="sxs-lookup"><span data-stu-id="b385b-109">Replication [!INCLUDE[tsql](../../includes/tsql-md.md)] programming: [How to: Configure a Subscription to Use Web Synchronization (Replication Transact-SQL Programming)](https://msdn.microsoft.com/library/ms345206.aspx)</span></span>  
  
-   <span data-ttu-id="b385b-110">RMO: [Web 同期を使用するようにサブスクリプションを構成する方法 (RMO プログラミング)](https://msdn.microsoft.com/library/ms345207.aspx)</span><span class="sxs-lookup"><span data-stu-id="b385b-110">RMO: [How to: Configure a Subscription to Use Web Synchronization (RMO Programming)](https://msdn.microsoft.com/library/ms345207.aspx)</span></span>  
  
 <span data-ttu-id="b385b-111">Web 同期では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) を実行するコンピューターを使用して、プル サブスクリプションをマージ パブリケーションに同期します。</span><span class="sxs-lookup"><span data-stu-id="b385b-111">Web synchronization uses a computer that is running [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) to synchronize pull subscriptions to merge publications.</span></span> <span data-ttu-id="b385b-112">IIS バージョン 5.0、IIS バージョン 6.0、および IIS バージョン 7.0 がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b385b-112">IIS version 5.0, IIS version 6.0, and IIS version 7.0 are supported.</span></span> <span data-ttu-id="b385b-113">IIS 7.0 では、Web 同期の構成ウィザードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b385b-113">The Configure Web Synchronization Wizard is not supported on IIS version 7.0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b385b-114">アプリケーションで [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] 以降のバージョンのみが使用されることと、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の以前のバージョンが IIS サーバーにインストールされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-114">Make sure that your application uses only [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] or later versions, and that earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] are not installed on the IIS server.</span></span> <span data-ttu-id="b385b-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の以前のバージョンを使用するとエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-115">Earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] can cause errors.</span></span> <span data-ttu-id="b385b-116">たとえば、"Web 同期中のメッセージの形式が無効でした。</span><span class="sxs-lookup"><span data-stu-id="b385b-116">These include the following: "The format of a message during Web synchronization was invalid.</span></span> <span data-ttu-id="b385b-117">Web サーバーでレプリケーション コンポーネントが正しく構成されていることを確認してください。" というエラーなどです。</span><span class="sxs-lookup"><span data-stu-id="b385b-117">Ensure that replication components are properly configured at the Web server".</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b385b-118">WebSync と代替スナップショット フォルダーの場所を同時に使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b385b-118">Do not use both WebSync and alternate snapshot folder locations at the same time.</span></span>  
  
 <span data-ttu-id="b385b-119">Web 同期を使用するには、次の手順を完了して IIS を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-119">To use Web synchronization, you must configure IIS by completing the following steps.</span></span> <span data-ttu-id="b385b-120">ここでは、各手順を詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="b385b-120">Each step is described in detail in this topic.</span></span>  
  
1.  <span data-ttu-id="b385b-121">SSL (Secure Sockets Layer) を構成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-121">Configure Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="b385b-122">IIS とすべてのサブスクライバー間の通信には SSL が必要です。</span><span class="sxs-lookup"><span data-stu-id="b385b-122">SSL is required for communication between IIS and all Subscribers.</span></span>  
  
2.  <span data-ttu-id="b385b-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールウィザードを使用して、IIS を実行しているコンピューターに接続コンポーネントをインストール [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="b385b-123">Install [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connectivity components on the computer that is running IIS by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span> <span data-ttu-id="b385b-124">手順 3. で説明する Web 同期の構成ウィザードを使用する場合は、IIS を実行しているコンピューターに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] もインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-124">If you plan to use the Configure Web Synchronization Wizard that is mentioned in step 3, you must also install [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] on the computer that is running IIS.</span></span>  
  
3.  <span data-ttu-id="b385b-125">IIS を実行しているコンピューターを Web 同期用に構成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-125">Configure the computer that is running IIS for Web synchronization.</span></span> <span data-ttu-id="b385b-126">手動でコンピューターを構成するか、Web 同期の構成ウィザードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b385b-126">You can configure the computer manually or use the Configure Web Synchronization Wizard.</span></span> <span data-ttu-id="b385b-127">ウィザードを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b385b-127">We recommend that you use the wizard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b385b-128">IIS を実行しているコンピューターで、64 ビット バージョンの Windows を実行している場合は、以下のコマンドを実行して、ISAPI (インターネット サーバー API) アプリケーションを実行できるようにサーバーを適切に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-128">If the computer that is running IIS is running on a 64-bit version of Windows, you must run following command to make sure that the server is properly configured to run Internet Server API (ISAPI) applications.</span></span> <span data-ttu-id="b385b-129">詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-129">For more information, see the IIS documentation.</span></span>  
  
    ```  
    cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 1  
    ```  
  
4.  <span data-ttu-id="b385b-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーに適切な権限を設定します。</span><span class="sxs-lookup"><span data-stu-id="b385b-130">Set the appropriate permissions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener.</span></span>  
  
5.  <span data-ttu-id="b385b-131">診断モードで Web 同期を実行し、IIS を実行しているコンピューターへの接続をテストして、SSL 証明書が正しくインストールされることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-131">Run Web synchronization in diagnostic mode to test the connection to the computer that is running IIS and to make sure that the SSL certificate is properly installed.</span></span>  
  
## <a name="configuring-secure-sockets-layer"></a><span data-ttu-id="b385b-132">Secure Sockets Layer の構成</span><span class="sxs-lookup"><span data-stu-id="b385b-132">Configuring Secure Sockets Layer</span></span>  
 <span data-ttu-id="b385b-133">SSL を構成するには、IIS を実行しているコンピューターが使用する証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-133">To configure SSL, specify a certificate for the computer that is running IIS to use.</span></span> <span data-ttu-id="b385b-134">マージ レプリケーション用の Web 同期では、サーバー証明書のみがサポートされており、クライアント証明書はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b385b-134">Web synchronization for merge replication supports using server certificates but not client certificates.</span></span> <span data-ttu-id="b385b-135">配置用に IIS を構成するには、最初に証明機関 (CA) から証明書を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-135">To configure IIS for deployment, you must first obtain a certificate from a certification authority (CA).</span></span> <span data-ttu-id="b385b-136">証明機関とは、ユーザー、コンピューター、およびその他の証明機関に属する公開暗号化キーの正当性の証明および保証を行う機関のことです。</span><span class="sxs-lookup"><span data-stu-id="b385b-136">A certificate authority is an entity that is responsible for establishing and vouching for the authenticity of public encryption keys that belong to users, computers, or other certification authorities.</span></span> <span data-ttu-id="b385b-137">証明書の詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-137">For more information about certificates, see the IIS documentation.</span></span> <span data-ttu-id="b385b-138">証明書をインストールしたら、その証明書を Web 同期で使用する Web サイトと関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-138">After you install the certificate, you must associate the certificate with the Web site that is used by Web synchronization.</span></span>  
  
#### <a name="to-specify-a-certificate-for-deployment"></a><span data-ttu-id="b385b-139">配置用に証明書を指定するには</span><span class="sxs-lookup"><span data-stu-id="b385b-139">To specify a certificate for deployment</span></span>  
  
1.  <span data-ttu-id="b385b-140">IIS を実行しているコンピューターに管理者としてログオンします。</span><span class="sxs-lookup"><span data-stu-id="b385b-140">Log on to the computer that is running IIS as an administrator.</span></span>  
  
2.  <span data-ttu-id="b385b-141">**[インターネット インフォメーション サービス (IIS) マネージャー]** を起動します。</span><span class="sxs-lookup"><span data-stu-id="b385b-141">Start **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="b385b-142">**[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-142">Click **Start**, and then click **Run**.</span></span>  
  
    2.  <span data-ttu-id="b385b-143">[**名前**] ボックスに「 `inetmgr` 」と入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-143">In the **Open** box, type `inetmgr`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b385b-144">IIS 証明書ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="b385b-144">Run the IIS Certificate Wizard:</span></span>  
  
    1.  <span data-ttu-id="b385b-145">**インターネット インフォメーション サービス (IIS) マネージャー**で、 **[ローカル コンピューター]** ノードを展開し、 **[Web サイト]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b385b-145">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand the **Web Sites** folder.</span></span>  
  
    2.  <span data-ttu-id="b385b-146">**[既定の Web サイト]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-146">Right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="b385b-147">**[既定の Web サイトのプロパティ]** ダイアログ ボックスの **[ディレクトリ セキュリティ]** タブで、 **[サーバー証明書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-147">In the **Default Web Site Properties** dialog box, on the **Directory Security** tab, click **Server Certificate**.</span></span>  
  
    4.  <span data-ttu-id="b385b-148">Web サーバー証明書ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="b385b-148">Complete the Web Server Certificate Wizard.</span></span>  
  
4.  <span data-ttu-id="b385b-149">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-149">Click **OK**.</span></span>  
  
 <span data-ttu-id="b385b-150">CA からサーバー証明書を取得できない場合は、テスト用に証明書を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b385b-150">If you cannot obtain a server certificate from a CA, you can specify a certificate for testing.</span></span> <span data-ttu-id="b385b-151">テスト用に IIS 6.0 を構成するには、SelfSSL ユーティリティを使用して証明書をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b385b-151">To configure IIS 6.0 for testing, install a certificate by using the SelfSSL utility.</span></span> <span data-ttu-id="b385b-152">このユーティリティは、IIS 6.0 リソース キットで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b385b-152">This utility is available in the IIS 6.0 Resource Kit.</span></span> <span data-ttu-id="b385b-153">ツールは、 [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=5135)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="b385b-153">You can download the tools from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=5135).</span></span> <span data-ttu-id="b385b-154">IIS 5.0 の場合は、 [Microsoft ヘルプとサポート](https://go.microsoft.com/fwlink/?LinkId=46229)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-154">For IIS 5.0, go to [Microsoft Help and Support](https://go.microsoft.com/fwlink/?LinkId=46229).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b385b-155">Web サイトで SSL を使用できるようにするには、事前に証明書を Web サイトに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-155">A certificate must be associated with a Web site before that Web site can use SSL.</span></span> <span data-ttu-id="b385b-156">SelfSSL を使用すると、証明書が既定の Web サイトに自動的に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="b385b-156">SelfSSL automatically associates the certificate with the default Web site.</span></span> <span data-ttu-id="b385b-157">既に証明書を保有しているか、または後で CA から証明書をインストールする場合は、証明書を Web 同期で使用する Web サイトと明示的に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-157">If you already have a certificate or later install a certificate from a CA, you must explicitly associate that certificate with the Web site that is used by Web synchronization.</span></span> <span data-ttu-id="b385b-158">サブスクリプションの同期に使用する Web サイトに関連付けられた証明書が 1 つしか存在しないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-158">Make sure there is only one certificate associated with the Web site that is used to synchronize subscriptions.</span></span> <span data-ttu-id="b385b-159">複数の証明書が存在する場合、サブスクライバーは使用可能な最初の Web サイトを使用します。</span><span class="sxs-lookup"><span data-stu-id="b385b-159">If there are multiple certificates, the Subscriber will use the first available Web site.</span></span>  
  
#### <a name="to-specify-a-certificate-for-testing-in-iis-60"></a><span data-ttu-id="b385b-160">IIS 6.0 でテスト用に証明書を指定するには</span><span class="sxs-lookup"><span data-stu-id="b385b-160">To specify a certificate for testing in IIS 6.0</span></span>  
  
1.  <span data-ttu-id="b385b-161">IIS を実行しているコンピューターに管理者としてログオンします。</span><span class="sxs-lookup"><span data-stu-id="b385b-161">Log on to the computer that is running IIS as an administrator.</span></span>  
  
2.  <span data-ttu-id="b385b-162">SelfSSL をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="b385b-162">Download and install SelfSSL.</span></span> <span data-ttu-id="b385b-163">既定では、アプリケーションは、次のようにインストールされ \<*drive*> ます。</span><span class="sxs-lookup"><span data-stu-id="b385b-163">By default, the application is installed to \<*drive*>:\Program Files\IIS Resources\SelfSSL.</span></span> <span data-ttu-id="b385b-164">アプリケーションとドキュメントのショートカットは \<*drive*> 、\Documents および Settings\All Users\Start Menu\Programs\IIS resources/selfsslにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="b385b-164">Application and documentation shortcuts are copied to \<*drive*>:\Documents and Settings\All Users\Start Menu\Programs\IIS Resources\SelfSSL.</span></span>  
  
3.  <span data-ttu-id="b385b-165">SelfSSL を実行します。</span><span class="sxs-lookup"><span data-stu-id="b385b-165">Run SelfSSL:</span></span>  
  
    -   <span data-ttu-id="b385b-166">すべてのパラメーターに既定値を指定して SelfSSL を実行するには、アプリケーションのインストール ディレクトリに移動して、SelfSSL.exe をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-166">To run SelfSSL with default values for all parameters, locate the installation directory for the application, and then double-click SelfSSL.exe.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b385b-167">SelfSSL を使用してインストールした証明書の既定の有効期限は 7 日間です。</span><span class="sxs-lookup"><span data-stu-id="b385b-167">By default, the certificate that is installed by SelfSSL is valid for seven days.</span></span>  
  
    -   <span data-ttu-id="b385b-168">1 つ以上のパラメーターの値を指定するには、 **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-168">To specify values for one or more parameters: click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b385b-169">[**名前**] ボックスに「」と入力し、 `cmd` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-169">In the **Open** box, enter `cmd`, and then click **OK**.</span></span> <span data-ttu-id="b385b-170">SelfSSL のインストール ディレクトリに移動して「 `SelfSSL`」と入力し、1 つ以上のパラメーターの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b385b-170">Locate the SelfSSL installation directory, type `SelfSSL`, and then specify values for one or more parameters.</span></span> <span data-ttu-id="b385b-171">パラメーターの一覧を確認する場合は、「 `SelfSSL -?`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b385b-171">For a list of parameters, type `SelfSSL -?`.</span></span>  
  
## <a name="installing-connectivity-components-and-sql-server-management-studio"></a><span data-ttu-id="b385b-172">接続コンポーネントと SQL Server Management Studio のインストール</span><span class="sxs-lookup"><span data-stu-id="b385b-172">Installing Connectivity Components and SQL Server Management Studio</span></span>  
  
#### <a name="to-install-sql-server-connectivity-components-and-sql-server-management-studio"></a><span data-ttu-id="b385b-173">SQL Server 接続コンポーネントと SQL Server Management Studio をインストールするには</span><span class="sxs-lookup"><span data-stu-id="b385b-173">To install SQL Server connectivity components and SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b385b-174">IIS を実行しているコンピューターに管理者としてログオンします。</span><span class="sxs-lookup"><span data-stu-id="b385b-174">Log on as an administrator to the computer that is running IIS.</span></span>  
  
2.  <span data-ttu-id="b385b-175">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] インストール ディスクから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="b385b-175">From the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installation disk, start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span> <span data-ttu-id="b385b-176">このウィザードの使用の詳細については、「インストール[ウィザードから SQL Server 2014 をインストールする」 &#40;セットアップ&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-176">For more information about using this wizard, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
3.  <span data-ttu-id="b385b-177">**[機能の選択]** ページで、 **[クライアント ツール接続]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b385b-177">On the **Feature Selection** page, select **Client Tools Connectivity**.</span></span>  
  
4.  <span data-ttu-id="b385b-178">Web 同期の構成ウィザードを使用する場合は、 **[管理ツール - 基本]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b385b-178">If you plan to use the Configure Web Synchronization Wizard, select **Management Tools - Basic**.</span></span>  
  
5.  <span data-ttu-id="b385b-179">ウィザードを終了して、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="b385b-179">Complete the wizard, and then restart the computer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b385b-180">他のコンポーネントをインストールすることもできますが、Web 同期で必要なのは接続コンポーネントだけです。</span><span class="sxs-lookup"><span data-stu-id="b385b-180">You can install additional components, but only the connectivity components are required for Web synchronization.</span></span>  
  
## <a name="configuring-the-computer-that-is-running-iis-by-using-the-configure-web-synchronization-wizard"></a><span data-ttu-id="b385b-181">Web 同期の構成ウィザードを使用した、IIS を実行しているコンピューターの構成</span><span class="sxs-lookup"><span data-stu-id="b385b-181">Configuring the Computer That Is Running IIS by Using the Configure Web Synchronization Wizard</span></span>  
 <span data-ttu-id="b385b-182">Web 同期の構成ウィザードを使用して、IIS サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-182">Configure the IIS server by using the Configure Web Synchronization Wizard or manually.</span></span> <span data-ttu-id="b385b-183">このウィザードを使用することをお勧めしますが、次のセクションで手動での構成の手順も説明します。</span><span class="sxs-lookup"><span data-stu-id="b385b-183">We recommend using the wizard, but we also provide steps for manual configuration in the next section.</span></span> <span data-ttu-id="b385b-184">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] に付属する Web 同期ウィザードは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を実行中のパブリッシャーまたは [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]にアップグレードされたパブリッシャーで作成されたパブリケーションのみに使用できます。</span><span class="sxs-lookup"><span data-stu-id="b385b-184">The Web Synchronization Wizard that is available with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] can be used only for publications that were created on a Publisher that is running [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], or a Publisher that was upgraded to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="b385b-185">このウィザードは、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]のパブリケーションには使用できません。</span><span class="sxs-lookup"><span data-stu-id="b385b-185">The wizard cannot be used for publications on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="b385b-186">このウィザードは、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンおよび [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 以降のバージョンのサブスクリプションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b385b-186">The wizard can be used with subscriptions on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, and [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 and later versions.</span></span>  
  
 <span data-ttu-id="b385b-187">この構成の特徴は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b385b-187">The configuration has the following characteristics:</span></span>  
  
-   <span data-ttu-id="b385b-188">IIS で既定の Web サイトを使用します。</span><span class="sxs-lookup"><span data-stu-id="b385b-188">Uses the default Web site in IIS.</span></span> <span data-ttu-id="b385b-189">ただし、別の Web サイトを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b385b-189">However, you can use another Web site.</span></span> <span data-ttu-id="b385b-190">Web サイトを作成する方法の詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-190">For more information about how to create Web sites, see the IIS documentation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b385b-191">指定した Web サイトから Web 同期で使用するコンポーネントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b385b-191">The Web site that you specify provides access to the components that are used by Web synchronization.</span></span> <span data-ttu-id="b385b-192">Web サイトの構成を行わなければ、そのサイトで他のデータや Web ページにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b385b-192">The Web site does not provide access to other data or Web pages unless you configure the site to do so.</span></span>  
  
-   <span data-ttu-id="b385b-193">仮想ディレクトリおよびこのディレクトリに関連付けられた別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-193">Creates a virtual directory and its associated alias.</span></span> <span data-ttu-id="b385b-194">この別名は、Web 同期コンポーネントにアクセスするときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b385b-194">The alias is used when accessing the Web synchronization components.</span></span> <span data-ttu-id="b385b-195">たとえば、IIS のアドレスが `https://*server.domain.com*` である場合に、別名を "websync1" と指定すると、replisapi.dll コンポーネントにアクセスするアドレスは `https://*server.domain.com*/websync1/replisapi.dll` となります。</span><span class="sxs-lookup"><span data-stu-id="b385b-195">For example, if the IIS address is `https://*server.domain.com*` and you specify an alias of 'websync1', the address to access the replisapi.dll component is `https://*server.domain.com*/websync1/replisapi.dll`.</span></span>  
  
-   <span data-ttu-id="b385b-196">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="b385b-196">Uses Basic Authentication.</span></span> <span data-ttu-id="b385b-197">基本認証の使用をお勧めする理由は、基本認証では、Kerberos 委任を必要とすることなく、IIS と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーまたはディストリビューターを別々のコンピューターで実行すること (推奨の構成) が可能になるからです。</span><span class="sxs-lookup"><span data-stu-id="b385b-197">We recommend using Basic Authentication because Basic Authentication enables you to run IIS and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher/Distributor on separate computers (the recommended configuration) without requiring Kerberos delegation.</span></span> <span data-ttu-id="b385b-198">基本認証を使用した SSL では、ログインやパスワードなどすべてのデータが暗号化されて送信されます </span><span class="sxs-lookup"><span data-stu-id="b385b-198">Using SSL with Basic Authentication makes sure that logins, passwords, and all data are encrypted in transit.</span></span> <span data-ttu-id="b385b-199">(使用する認証の種類にかかわらず、SSL は必須です)。Web 同期のベストプラクティスの詳細については、「web 同期の[構成](configure-web-synchronization.md)」の「web 同期のセキュリティのベストプラクティス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-199">(SSL is required, regardless of the type of authentication that is used.) For more information about best practices for Web synchronization, see the section "Security Best Practices for Web Synchronization" in [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
#### <a name="to-configure-the-computer-that-is-running-iis-by-using-the-configure-web-synchronization-wizard"></a><span data-ttu-id="b385b-200">Web 同期の構成ウィザードを使用して IIS を実行しているコンピューターを構成するには</span><span class="sxs-lookup"><span data-stu-id="b385b-200">To configure the computer that is running IIS by using the Configure Web Synchronization Wizard</span></span>  
  
1.  <span data-ttu-id="b385b-201">IIS を実行しているコンピューターで、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動します。</span><span class="sxs-lookup"><span data-stu-id="b385b-201">On the computer that is running IIS, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b385b-202">パブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="b385b-202">Connect to the Publisher, and then expand the server node.</span></span>  
  
3.  <span data-ttu-id="b385b-203">**[ローカル パブリケーション]** フォルダーを展開し、パブリケーションを右クリックして、 **[Web 同期の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-203">Expand the **Local Publications** folder, right-click the publication, and then click **Configure Web Synchronization**.</span></span>  
  
4.  <span data-ttu-id="b385b-204">Web 同期の構成ウィザードの **[サブスクライバーの種類]** ページで、 **[SQL Server]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-204">In the Configure Web Synchronization Wizard, on the **Subscriber Type** page, select **SQL Server**.</span></span>  
  
5.  <span data-ttu-id="b385b-205">**[Web サーバー]** ページで以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b385b-205">On the **Web Server** page:</span></span>  
  
    1.  <span data-ttu-id="b385b-206">サブスクリプションを同期する IIS のインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="b385b-206">Select the instance of IIS that will synchronize subscriptions.</span></span>  
  
    2.  <span data-ttu-id="b385b-207">**[新しい仮想ディレクトリを作成する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-207">Select **Create a new virtual directory**.</span></span>  
  
    3.  <span data-ttu-id="b385b-208">ページの下のペインで IIS のインスタンスを展開してから、 **[Web サイト]** を展開して、 **[既定の Web サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-208">In the lower pane of the page, expand the instance of IIS, expand **Web Sites**, and then click **Default Web Site**.</span></span>  
  
6.  <span data-ttu-id="b385b-209">**[仮想ディレクトリ情報]** ページで以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b385b-209">On the **Virtual Directory Information** page:</span></span>  
  
    1.  <span data-ttu-id="b385b-210">**[別名]** ボックスに仮想ディレクトリの別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="b385b-210">In the **Alias** box, enter an alias for the virtual directory.</span></span>  
  
    2.  <span data-ttu-id="b385b-211">**[パス]** ボックスに、仮想ディレクトリのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="b385b-211">In the **Path** box, enter a path of the virtual directory.</span></span> <span data-ttu-id="b385b-212">たとえば、[エイリアス] ボックスに「」と入力した場合は、[ `websync1` **Alias** `C:\Inetpub\wwwroot\websync1` **パス**] ボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b385b-212">For example, if you entered `websync1` in the **Alias** box, enter `C:\Inetpub\wwwroot\websync1` in the **Path** box.</span></span> <span data-ttu-id="b385b-213">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-213">Click **Next**.</span></span>  
  
    3.  <span data-ttu-id="b385b-214">両方のダイアログ ボックスで **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-214">On both dialog boxes, click **Yes**.</span></span> <span data-ttu-id="b385b-215">これにより、新しいフォルダーを作成し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ISAPI (インターネット サーバー API) の DLL をコピーします。</span><span class="sxs-lookup"><span data-stu-id="b385b-215">This specifies that you want to create a new folder and that you want to copy the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Internet Server API (ISAPI) DLL.</span></span> <span data-ttu-id="b385b-216">.</span><span class="sxs-lookup"><span data-stu-id="b385b-216">.</span></span>  
  
7.  <span data-ttu-id="b385b-217">**[認証済みアクセス]** ページで以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b385b-217">On the **Authenticated Access** page:</span></span>  
  
    1.  <span data-ttu-id="b385b-218">**[統合 Windows 認証]** と **[Windows ドメイン サーバーでダイジェスト認証を使用する]** チェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-218">Make sure that **Integrated Windows authentication** and **Digest authentication for Windows domain servers** are cleared.</span></span>  
  
    2.  <span data-ttu-id="b385b-219">**[基本認証]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b385b-219">Select **Basic Authentication**.</span></span>  
  
    3.  <span data-ttu-id="b385b-220">**[既定のドメイン]** ボックスおよび **[領域]** ボックスに、IIS を実行しているコンピューターのドメインを入力します。</span><span class="sxs-lookup"><span data-stu-id="b385b-220">In the **Default Domain** and **Realm** boxes, enter the domain of the computer that is running IIS.</span></span>  
  
8.  <span data-ttu-id="b385b-221">**[ディレクトリ アクセス]** ページで以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b385b-221">On the **Directory Access** page:</span></span>  
  
    1.  <span data-ttu-id="b385b-222">**[追加]** をクリックし、 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、サブスクライバーが IIS への接続に使用するアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b385b-222">Click **Add**, and then in the **Select Users or Groups** dialog box, add the accounts under which Subscribers will make connections to IIS.</span></span> <span data-ttu-id="b385b-223">これらのアカウントは、サブスクリプションの新規作成ウィザードの **[Web サーバー情報]** ページで指定するか、 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)*@internet_login* パラメーターの値として指定します。</span><span class="sxs-lookup"><span data-stu-id="b385b-223">These are the accounts that you will specify on the **Web Server Information** page of the New Subscription Wizard or as the value for the [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)*@internet_login* parameter.</span></span>  
  
9. <span data-ttu-id="b385b-224">**[スナップショットの共有へのアクセス]** ページで、スナップショット共有を入力します。</span><span class="sxs-lookup"><span data-stu-id="b385b-224">On the **Snapshot Share Access** page, enter the snapshot share.</span></span> <span data-ttu-id="b385b-225">サブスクライバーがスナップショット ファイルにアクセスできるように、この共有に適切な権限を設定します。</span><span class="sxs-lookup"><span data-stu-id="b385b-225">The appropriate permissions are set on this share so that Subscribers can access the snapshot files.</span></span> <span data-ttu-id="b385b-226">共有の権限の詳細については、「[スナップショット フォルダーのセキュリティ保護](security/secure-the-snapshot-folder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-226">For more information about permissions for the share, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  
10. <span data-ttu-id="b385b-227">**[ウィザードの完了]** ページの **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-227">On the **Completing the Wizard** page, click **Finish**.</span></span>  
  
     <span data-ttu-id="b385b-228">IIS を実行しているリモート コンピューターの構成中に発生したネットワーク エラーなど、何らかの障害が発生した場合、完了済みの操作はすべてロールバックされ、残りの操作は中止されます。</span><span class="sxs-lookup"><span data-stu-id="b385b-228">If a failure occurs, such as a network error while trying to configure a remote computer that is running IIS, all completed actions are rolled back and all remaining actions are canceled.</span></span> <span data-ttu-id="b385b-229">完了済みの操作をロールバックできない場合、ウィザードの最後のページの状態は " **成功** " と表示され、完了済みのアクションはコミットされたままとなります。</span><span class="sxs-lookup"><span data-stu-id="b385b-229">If a completed action cannot be rolled back, the status in the final page of the wizard displays **Success** and the completed actions remain committed.</span></span>  
  
11. <span data-ttu-id="b385b-230">IIS を実行しているコンピューターで、64 ビット バージョンの Windows を実行している場合、replisapi.dll を適切なディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-230">If the computer that is running IIS is running on a 64-bit version of Windows, replisapi.dll must be copied to the appropriate directory:</span></span>  
  
    1.  <span data-ttu-id="b385b-231">**[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-231">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b385b-232">[**名前**] ボックスに「」と入力し、 `iisreset` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-232">In the **Open** box, enter `iisreset`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="b385b-233">IIS が停止して再起動したら、 [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi から手順 6b. で指定したディレクトリに replisapi.dll をコピーします。</span><span class="sxs-lookup"><span data-stu-id="b385b-233">After IIS stops and restarts, copy replisapi.dll from [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi to the directory that is specified in step 6b.</span></span>  
  
    3.  <span data-ttu-id="b385b-234">**[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-234">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b385b-235">[**名前**] ボックスに「」と入力し、 `cmd` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-235">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="b385b-236">手順 6b. で指定したディレクトリで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b385b-236">In the directory that you specified in step 6b, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
## <a name="manually-configuring-the-computer-that-is-running-iis"></a><span data-ttu-id="b385b-237">IIS を実行しているコンピューターの手動の構成</span><span class="sxs-lookup"><span data-stu-id="b385b-237">Manually Configuring the Computer That Is Running IIS</span></span>  
 <span data-ttu-id="b385b-238">IIS を実行しているコンピューターを手動で構成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーをインストールおよび構成し、IIS に接続するサブスクライバーの認証を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-238">To configure the computer that is running IIS manually, you must install and configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener, and then configure authorization for Subscribers that will connect to IIS.</span></span>  
  
#### <a name="to-install-and-configure-the-sql-server-replication-listener"></a><span data-ttu-id="b385b-239">SQL Server レプリケーション リスナーのインストールと構成を行うには</span><span class="sxs-lookup"><span data-stu-id="b385b-239">To install and configure the SQL Server Replication Listener</span></span>  
  
1.  <span data-ttu-id="b385b-240">IIS を実行しているコンピューターに、replisapi.dll を格納するファイル ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-240">Create a file directory on the computer that is running IIS to contain replisapi.dll.</span></span> <span data-ttu-id="b385b-241">ディレクトリはどこに作成してもかまいませんが、\<*drive*>:\Inetpub ディレクトリの下に作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b385b-241">You can create the directory wherever you want, but we recommend that you create the directory under the \<*drive*>:\Inetpub directory.</span></span> <span data-ttu-id="b385b-242">たとえば、ディレクトリ \<*drive*>:\Inetpub\SQLReplication\\ を作成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-242">For example, create the directory \<*drive*>:\Inetpub\SQLReplication\\.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b385b-243">FAT ファイル システム パーティションではなく NTFS ファイル システム パーティションにこのディレクトリを作成することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b385b-243">We strongly recommend that you create this directory on an NTFS file system partition instead of a FAT file system.</span></span> <span data-ttu-id="b385b-244">NTFS ファイル システムであれば、NTFS ファイル システムのファイル アクセス許可を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションにアクセスできるユーザーを厳密に制御することができます。</span><span class="sxs-lookup"><span data-stu-id="b385b-244">When you use the NTFS file system, you can use NTFS file system permissions to control precisely the users that can access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
2.  <span data-ttu-id="b385b-245">replisapi.dll を [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ ディレクトリから、手順 1. で作成したファイル ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b385b-245">Copy replisapi.dll from the directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ to the file directory that you created in step 1.</span></span>  
  
3.  <span data-ttu-id="b385b-246">次の手順に従って replisapi.dll を登録します。</span><span class="sxs-lookup"><span data-stu-id="b385b-246">Register replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="b385b-247">**[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-247">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b385b-248">[**名前**] ボックスに「」と入力し、 `cmd` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-248">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="b385b-249">手順 1. で作成したディレクトリで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b385b-249">In the directory that you created in step 1, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
4.  <span data-ttu-id="b385b-250">レプリケーション用の新しい Web サイトを作成するか、既存のサイトを使用します。</span><span class="sxs-lookup"><span data-stu-id="b385b-250">Create a new Web site for replication, or use an existing site.</span></span> <span data-ttu-id="b385b-251">Web サイトは、同期の際にレプリケーション コンポーネントからアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="b385b-251">The Web site will be accessed by replication components during synchronization.</span></span> <span data-ttu-id="b385b-252">Web サイトを作成する方法の詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-252">For more information about how to create Web sites, see the IIS documentation.</span></span>  
  
5.  <span data-ttu-id="b385b-253">IIS で仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-253">Create a virtual directory in IIS.</span></span> <span data-ttu-id="b385b-254">仮想ディレクトリは、手順 4. で作成した Web サイトの下に作成し、手順 1. で作成したディレクトリにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="b385b-254">The virtual directory should be created under the Web site that was created in step 4, and should be mapped to the directory that was created in step 1.</span></span> <span data-ttu-id="b385b-255">仮想ディレクトリを作成する方法の詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-255">For more information about how to create virtual directories, see the IIS documentation.</span></span> <span data-ttu-id="b385b-256">このディレクトリに割り当てる権限は、最小限にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b385b-256">We recommend that you be as restrictive as possible when you assign permissions to this directory.</span></span> <span data-ttu-id="b385b-257">**[読み取り]** 権限と **[ISAPI アプリケーションや CGI などを実行する]** 権限は選択する必要がありますが、 **[ASP などのスクリプトを実行する]**、 **[書き込み]**、および **[参照]** 権限は選択しなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="b385b-257">You must select **Read** and **Execute** permissions, but you can clear **Run scripts**, **Write**, and **Browse** permissions.</span></span>  
  
6.  <span data-ttu-id="b385b-258">replisapi.dll を実行できるように IIS を構成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-258">Configure IIS to enable replisapi.dll to execute.</span></span> <span data-ttu-id="b385b-259">手順 4. で割り当てた権限は、以前のバージョンの IIS では十分ですが、IIS バージョン 6.0 では ISAPI (インターネット サーバー API) 拡張を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-259">The permissions that are assigned in step 4 are sufficient for earlier versions of IIS; however, IIS version 6.0 requires Internet Server API (ISAPI) extensions to be enabled.</span></span> <span data-ttu-id="b385b-260">詳細については、IIS 6.0 のマニュアルの「ISAPI 拡張を構成する」および「動的コンテンツを有効および無効にする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-260">For more information, see "Configuring ISAPI Extensions" and "Enabling and Disabling Dynamic Content" in the IIS 6.0 documentation.</span></span>  
  
#### <a name="to-configure-iis-authentication"></a><span data-ttu-id="b385b-261">IIS 認証を構成するには</span><span class="sxs-lookup"><span data-stu-id="b385b-261">To configure IIS authentication</span></span>  
  
-   <span data-ttu-id="b385b-262">サブスクライバーが IIS に接続するには、サブスクライバーがリソースやプロセスにアクセスする前に、IIS がサブスクライバーを認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-262">When Subscribers connect to IIS, IIS must authenticate the Subscribers before they can access resources and processes.</span></span> <span data-ttu-id="b385b-263">IIS では、匿名認証、基本認証、統合認証の 3 種類の認証方式が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b385b-263">IIS offers three types of authentication: Anonymous, Basic, and Integrated.</span></span> <span data-ttu-id="b385b-264">認証は、Web サイト全体または作成した特定の仮想ディレクトリに適用することができます。</span><span class="sxs-lookup"><span data-stu-id="b385b-264">Authentication can be applied to the whole Web site or to the virtual directory that you created.</span></span>  
  
     <span data-ttu-id="b385b-265">基本認証と SSL を組み合わせて使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b385b-265">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="b385b-266">使用する認証の種類にかかわらず、SSL は必須です。</span><span class="sxs-lookup"><span data-stu-id="b385b-266">SSL is required, regardless of the type of authentication that is used.</span></span> <span data-ttu-id="b385b-267">認証を構成する方法の詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-267">For more information about how to configure authentication, see the IIS documentation.</span></span>  
  
## <a name="setting-permissions-for-the-sql-server-replication-listener"></a><span data-ttu-id="b385b-268">SQL Server レプリケーション リスナーの権限の設定</span><span class="sxs-lookup"><span data-stu-id="b385b-268">Setting Permissions for the SQL Server Replication Listener</span></span>  
 <span data-ttu-id="b385b-269">サブスクライバーが IIS を実行しているコンピューターに接続するときは、IIS の構成時に指定した認証の種類を使用して、サブスクライバーが認証されます。</span><span class="sxs-lookup"><span data-stu-id="b385b-269">When a Subscriber connects to the computer that is running IIS, the Subscriber is authenticated by using the type of authentication that was specified when you configured IIS.</span></span> <span data-ttu-id="b385b-270">IIS はサブスクライバーを認証した後、サブスクライバーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションを実行する権限があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-270">After IIS authenticates the Subscriber, IIS checks whether the Subscriber is authorized to invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="b385b-271">replisapi.dll の権限を設定して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションを実行できるユーザーを制御します。</span><span class="sxs-lookup"><span data-stu-id="b385b-271">You control the users that can invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication by setting permissions for replisapi.dll.</span></span> <span data-ttu-id="b385b-272">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションに許可なくアクセスされることがないように権限を正しく構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-272">Properly configuring permissions is necessary to prevent unauthorized access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
 <span data-ttu-id="b385b-273">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーの実行に使用するアカウントを最小の権限で構成するには、次の手順を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-273">To configure the minimum permissions for the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener runs, complete the following procedure.</span></span> <span data-ttu-id="b385b-274">手順は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] IIS 6.0 の実行に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b385b-274">The steps in the procedure apply to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] running IIS 6.0.</span></span>  
  
 <span data-ttu-id="b385b-275">次の手順の他に、PAL (パブリケーション アクセス リスト) に必要なログインが登録されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-275">In addition to performing the following steps, make sure that the required logins are in the publication access list (PAL).</span></span> <span data-ttu-id="b385b-276">PAL の詳細については、「[Secure the Publisher (パブリッシャーのセキュリティ保護)](security/secure-the-publisher.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-276">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
#### <a name="to-configure-the-account-and-permissions"></a><span data-ttu-id="b385b-277">アカウントと権限を構成するには</span><span class="sxs-lookup"><span data-stu-id="b385b-277">To configure the account and permissions</span></span>  
  
1.  <span data-ttu-id="b385b-278">IIS を実行しているコンピューターでローカル アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-278">Create a local account on the computer that is running IIS:</span></span>  
  
    1.  <span data-ttu-id="b385b-279">**マイコンピューター**を右クリックし、[**管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-279">Right-click **My Computer**, and then click **Manage**.</span></span>  
  
    2.  <span data-ttu-id="b385b-280">**[コンピューターの管理]** で、 **[ローカル ユーザーとグループ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b385b-280">In **Computer Management**, expand **Local Users and Groups**.</span></span>  
  
    3.  <span data-ttu-id="b385b-281">**[ユーザー]** を右クリックし、 **[新しいユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-281">Right-click **Users**, and then click **New User**.</span></span>  
  
    4.  <span data-ttu-id="b385b-282">ユーザー名と複雑なパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="b385b-282">Enter a user name and a strong password.</span></span>  
  
    5.  <span data-ttu-id="b385b-283">**[作成]** をクリックしてから、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-283">Click **Create**, and then click **Close**.</span></span>  
  
2.  <span data-ttu-id="b385b-284">アカウントを IIS_WPG グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="b385b-284">Add the account to the IIS_WPG group:</span></span>  
  
    1.  <span data-ttu-id="b385b-285">**[コンピューターの管理]** で、 **[ローカル ユーザーとグループ]** を展開し、 **[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-285">In **Computer Management**, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
    2.  <span data-ttu-id="b385b-286">**[IIS_WPG]** を右クリックし、 **[グループに追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-286">Right-click **IIS_WPG**, and then click **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="b385b-287">**[IIS_WPG のプロパティ]** ダイアログ ボックスで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-287">In the **IIS_WPG Properties** dialog box, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="b385b-288">**[ユーザー、コンピューター、またはグループの選択]** ダイアログ ボックスで、手順 1. で作成したアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b385b-288">In the **Select Users, Computers, or Groups** dialog box, add the account created in step 1.</span></span>  
  
    5.  <span data-ttu-id="b385b-289">**[場所を指定してください]** フィールドの名前が、ドメインではなくローカル コンピューターの名前であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-289">Make sure that the name in the **From this location** field is the name of the local computer instead of a domain.</span></span> <span data-ttu-id="b385b-290">ローカル コンピューターの名前でない場合は、 **[場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-290">If the name is not a local computer, click **Locations**.</span></span> <span data-ttu-id="b385b-291">**[場所]** ダイアログ ボックスで、ローカル コンピューターを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-291">In the **Locations** dialog box, elect the local computer, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="b385b-292">**[ユーザーの選択]** ダイアログ ボックスと **[IIS_WPG のプロパティ]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-292">In the **Select Users** dialog box and the **IIS_WPG Properties** dialog box, click **OK**.</span></span>  
  
3.  <span data-ttu-id="b385b-293">replisapi.dll が保存されているフォルダーに対する最小限の権限をアカウントに許可します。</span><span class="sxs-lookup"><span data-stu-id="b385b-293">Grant the minimum permissions on the folder that contains replisapi.dll to the account :</span></span>  
  
    1.  <span data-ttu-id="b385b-294">replisapi.dll のために作成したフォルダーに移動し、フォルダーを右クリックして、 **[共有とセキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-294">Locate the folder that you created for replisapi.dll, right-click the folder, and then click **Sharing and Security**.</span></span>  
  
    2.  <span data-ttu-id="b385b-295">**[セキュリティ]** タブで **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-295">On the **Security** tab, click **Add**.</span></span>  
  
    3.  <span data-ttu-id="b385b-296">**[ユーザー、コンピューター、またはグループの選択]** ダイアログ ボックスで、手順 1. で作成したアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b385b-296">In the **Select Users, Computers, or Groups** dialog box, add the account that you created in step 1.</span></span>  
  
    4.  <span data-ttu-id="b385b-297">**[場所を指定してください]** フィールドの名前が、ドメインではなくローカル コンピューターの名前であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-297">Make sure that the name in the **From this location** field is the name of the local computer instead of a domain.</span></span> <span data-ttu-id="b385b-298">ローカル コンピューターの名前でない場合は、 **[場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-298">If the name is not a local computer, click **Locations**.</span></span> <span data-ttu-id="b385b-299">**[場所]** ダイアログ ボックスで、ローカル コンピューターを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-299">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="b385b-300">アカウントには、**[読み取り]**、**[読み取りと実行]**、**[フォルダーの内容の一覧表示]** のみが許可されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-300">Make sure that the account is granted only **Read**, **Read & Execute**, and **List Folder Contents** permissions.</span></span>  
  
    6.  <span data-ttu-id="b385b-301">ディレクトリにアクセスする必要がないユーザーまたはグループを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-301">Select any users or groups that do not require access to the directory, and then click **Remove**.</span></span>  
  
    7.  <span data-ttu-id="b385b-302">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-302">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="b385b-303">**インターネット インフォメーション サービス (IIS) マネージャー**でアプリケーション プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="b385b-303">Create an application pool in **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="b385b-304">**[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-304">Click **Start**, and then click **Run**.</span></span>  
  
    2.  <span data-ttu-id="b385b-305">[**名前**] ボックスに「 `inetmgr` 」と入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-305">In the **Open** box, type `inetmgr`, and then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="b385b-306">**インターネット インフォメーション サービス (IIS) マネージャー**で、 **[ローカル コンピューター]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="b385b-306">In **Internet Information Services (IIS) Manager**, expand the **local computer** node.</span></span>  
  
    4.  <span data-ttu-id="b385b-307">**[アプリケーション プール]** を右クリックし、 **[新規作成]** をポイントしてから **[アプリケーション プール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-307">Right-click **Application Pools**, point to **New** and then click **Application Pool**.</span></span>  
  
    5.  <span data-ttu-id="b385b-308">**[アプリケーション プール ID]** フィールドにプールの名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-308">Enter a name for the pool in the **Application pool ID** field, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="b385b-309">アカウントとアプリケーション プールを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b385b-309">Associate the account with the application pool:</span></span>  
  
    1.  <span data-ttu-id="b385b-310">**インターネット インフォメーション サービス (IIS) マネージャー**で、 **[ローカル コンピューター]** ノードを展開し、 **[アプリケーション プール]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b385b-310">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand **Application Pools**.</span></span>  
  
    2.  <span data-ttu-id="b385b-311">作成したアプリケーション プールを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-311">Right-click the application pool that you created, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="b385b-312">[ \*\* \<ApplicationPoolName> プロパティ**] ダイアログボックスの [ **id** ] タブで、[**構成可能\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-312">In the **\<ApplicationPoolName> Properties** dialog box, on the **Identity** tab, click **Configurable**.</span></span>  
  
    4.  <span data-ttu-id="b385b-313">**[ユーザー名]** および **[パスワード]** フィールドに、手順 1. で作成したアカウントとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="b385b-313">In the **User name** and **password** fields, enter the account and password that were created in step 1.</span></span>  
  
    5.  <span data-ttu-id="b385b-314">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-314">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="b385b-315">Web 同期に使用する仮想ディレクトリにアプリケーション プールを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b385b-315">Associate the application pool with the virtual directory that is used for Web synchronization:</span></span>  
  
    1.  <span data-ttu-id="b385b-316">**インターネット インフォメーション サービス (IIS) マネージャー**で、 **[ローカル コンピューター]** ノードを展開し、 **[Web サイト]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b385b-316">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand **Web Sites**.</span></span>  
  
    2.  <span data-ttu-id="b385b-317">Web 同期に使用している Web サイトを展開し、Web 同期用に作成した仮想ディレクトリを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-317">Expand the Web site that you are using for Web synchronization, right-click the virtual directory that you created for Web synchronization, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="b385b-318">[ \*\* \<VirtualDirectoryName> プロパティ**] ダイアログボックスの [**仮想ディレクトリ**] タブで、手順 5. で作成したアプリケーションプールを [**アプリケーションプール\*\*] ボックスの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="b385b-318">On the **Virtual Directory** tab of the **\<VirtualDirectoryName> Properties** dialog box, from the **Application pool** drop-down list, select the application pool that was created in step 5.</span></span>  
  
    4.  <span data-ttu-id="b385b-319">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-319">Click **OK**.</span></span>  
  
## <a name="testing-the-connection-to-replisapidll"></a><span data-ttu-id="b385b-320">replisapi.dll への接続のテスト</span><span class="sxs-lookup"><span data-stu-id="b385b-320">Testing the Connection to replisapi.dll</span></span>  
 <span data-ttu-id="b385b-321">診断モードで Web 同期を実行すると、IIS を実行しているコンピューターへの接続をテストして、SSL (Secure Sockets Layer) 証明書が正しくインストールされているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b385b-321">Run Web synchronization in diagnostic mode to test the connection to the computer that is running IIS and to make sure that the Secure Sockets Layer (SSL) certificate is properly installed.</span></span> <span data-ttu-id="b385b-322">診断モードで Web 同期を実行するには、IIS を実行しているコンピューターの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-322">To run Web synchronization in diagnostic mode, you must be an administrator on the computer running IIS.</span></span>  
  
#### <a name="to-test-the-connection-to-replisapidll"></a><span data-ttu-id="b385b-323">replisapi.dll への接続をテストするには</span><span class="sxs-lookup"><span data-stu-id="b385b-323">To test the connection to replisapi.dll</span></span>  
  
1.  <span data-ttu-id="b385b-324">サブスクライバーの LAN (ローカル エリア ネットワーク) が正しく設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-324">Make sure that local area network (LAN) settings at the Subscriber are correct:</span></span>  
  
    1.  <span data-ttu-id="b385b-325">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer で、 **[ツール]** メニューの **[インターネット オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-325">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="b385b-326">**[接続]** タブで、 **[LAN の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-326">On the **Connections** tab, click **LAN Settings**.</span></span>  
  
    3.  <span data-ttu-id="b385b-327">LAN でプロキシ サーバーを使用していない場合は、 **[設定を自動的に検出する]** と **[LAN にプロキシ サーバーを使用する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="b385b-327">If a proxy server is not used on the LAN, clear **Automatically Detect Settings** and **Use a proxy server for your LAN**.</span></span>  
  
    4.  <span data-ttu-id="b385b-328">プロキシ サーバーを使用している場合は、 **[LAN にプロキシ サーバーを使用する]** と **[ローカル アドレスにはプロキシ サーバーを使用しない]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="b385b-328">If a proxy server is used, select **Use a proxy server for your LAN** and **Bypass proxy server for local addresses**.</span></span>  
  
    5.  <span data-ttu-id="b385b-329">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-329">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="b385b-330">サブスクライバー側の Internet Explorer から診断モードでサーバーに接続します。診断モードで接続するには、replisapi.dll のアドレスの後に「 `?diag` 」を追加します。</span><span class="sxs-lookup"><span data-stu-id="b385b-330">At the Subscriber, in Internet Explorer, connect to the server in diagnostic mode by appending `?diag` to the address for the replisapi.dll.</span></span> <span data-ttu-id="b385b-331">(例: `https://server.domain.com/directory/replisapi.dll?diag`)。</span><span class="sxs-lookup"><span data-stu-id="b385b-331">For example: `https://server.domain.com/directory/replisapi.dll?diag`.</span></span>  
  
3.  <span data-ttu-id="b385b-332">IIS に指定した証明書が Windows オペレーティング システムによって認識されない場合は、 **[セキュリティの警告]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b385b-332">If the certificate that you specified for IIS is not recognized by the Windows operating system, the **Security Alert** dialog box appears.</span></span> <span data-ttu-id="b385b-333">証明書がテスト用の証明書であるか、Windows が認識しない証明機関 (CA) によって発行されていると、この警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b385b-333">This alert might occur because the certificate is a test certificate or the certificate was issued by a certification authority (CA) that Windows does not recognize.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b385b-334">このダイアログ ボックスが表示されない場合は、アクセスしているサーバーの証明書が信頼された証明書としてサブスクライバーの証明書ストアに追加されていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="b385b-334">If this dialog box does not appear, make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="b385b-335">証明書のエクスポートの詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-335">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
    1.  <span data-ttu-id="b385b-336">**[セキュリティの警告]** ダイアログ ボックスで、 **[証明書の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-336">In the **Security Alert** dialog box, click **View Certificate**.</span></span>  
  
    2.  <span data-ttu-id="b385b-337">**[証明書]** ダイアログ ボックスの **[全般]** タブで、 **[証明書のインストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-337">In the **Certificate** dialog box, on the **General** tab, click **Install Certificate**.</span></span>  
  
    3.  <span data-ttu-id="b385b-338">証明書インポート ウィザードを実行します。このウィザードでは既定の値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="b385b-338">Complete the Certificate Import Wizard, accepting the defaults.</span></span>  
  
    4.  <span data-ttu-id="b385b-339">**[セキュリティの警告]** ダイアログ ボックスで、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-339">In the **Security Warning** dialog box, click **Yes**.</span></span>  
  
    5.  <span data-ttu-id="b385b-340">証明書のインポート ウィザードの確認ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-340">In the Certificate Import Wizard confirmation dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="b385b-341">**[証明書]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b385b-341">Close the **Certificate** dialog box.</span></span>  
  
    7.  <span data-ttu-id="b385b-342">**[セキュリティの警告]** ダイアログ ボックスで、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b385b-342">In the **Security Alert** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b385b-343">ユーザーの証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b385b-343">Certificates are installed for users.</span></span> <span data-ttu-id="b385b-344">IIS と同期するユーザーすべてに対してこの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-344">This process must be performed for each user that will synchronize with IIS.</span></span>  
  
4.  <span data-ttu-id="b385b-345">**[\<ServerName> に接続]** ダイアログ ボックスで、マージ エージェントが IIS サーバーへの接続に使用するログインとパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b385b-345">In the **Connect to \<ServerName>** dialog box, specify the login and password that the Merge Agent will use to connect to IIS.</span></span> <span data-ttu-id="b385b-346">これらの資格情報は、サブスクリプションの新規作成ウィザードで指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b385b-346">These credentials will also be specified in the New Subscription Wizard.</span></span>  
  
5.  <span data-ttu-id="b385b-347">**[SQL Web 同期診断情報]** と呼ばれる Internet Explorer のウィンドウで、ページの **[Status]** 列の値が **[SUCCESS]** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-347">In the Internet Explorer window called **SQL Websync diagnostic information**, verify that the value in each **Status** column on the page is **SUCCESS**.</span></span>  
  
6.  <span data-ttu-id="b385b-348">証明書がサブスクライバーに正しくインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b385b-348">Make sure that the certificate is installed correctly on the Subscriber:</span></span>  
  
    1.  <span data-ttu-id="b385b-349">Internet Explorer をいったん閉じてから、再度開きます。</span><span class="sxs-lookup"><span data-stu-id="b385b-349">Close and then reopen Internet Explorer.</span></span>  
  
    2.  <span data-ttu-id="b385b-350">サーバーに診断モードで接続します。</span><span class="sxs-lookup"><span data-stu-id="b385b-350">Connect to the server in diagnostic mode.</span></span> <span data-ttu-id="b385b-351">証明書が正しくインストールされている場合は、 **[セキュリティの警告]** ダイアログ ボックスが表示されません。</span><span class="sxs-lookup"><span data-stu-id="b385b-351">If the certificate is installed properly, the **Security Alert** dialog box will not appear.</span></span> <span data-ttu-id="b385b-352">ダイアログ ボックスが表示される場合は、マージ エージェントから IIS を実行しているコンピューターへの接続に失敗します。</span><span class="sxs-lookup"><span data-stu-id="b385b-352">If the dialog box appears, the Merge Agent will fail when it tries to connect to the computer that is running IIS.</span></span> <span data-ttu-id="b385b-353">アクセスしているサーバーの証明書が、信頼された証明書としてサブスクライバーの証明書ストアに追加されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b385b-353">You must make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="b385b-354">証明書のエクスポートの詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b385b-354">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b385b-355">参照</span><span class="sxs-lookup"><span data-stu-id="b385b-355">See Also</span></span>  
 <span data-ttu-id="b385b-356">[[Web 同期の構成]](configure-web-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="b385b-356">[Configure Web Synchronization](configure-web-synchronization.md)</span></span>  
  
  
