---
title: Web 同期用の IIS 7 の構成 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- IIS 7 server configuration [SQL Server replication]
- Web synchronization, IIS 7 servers
ms.assetid: c201fe2c-0a76-44e5-a233-05e14cd224a6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 65b5aa1ea0d314a9675b1c1b90b688d2990e6d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646137"
---
# <a name="configure-iis-7-for-web-synchronization"></a><span data-ttu-id="158e4-102">Web 同期用の IIS 7 の構成</span><span class="sxs-lookup"><span data-stu-id="158e4-102">Configure IIS 7 for Web Synchronization</span></span>
  <span data-ttu-id="158e4-103">ここでは、マージ レプリケーションの Web 同期で使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) バージョン 7 以降を手動で構成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="158e4-103">The procedures in this topic will guide you through the process of manually configuring [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) version 7 and higher for use with Web synchronization for merge replication.</span></span> 
  
 <span data-ttu-id="158e4-104">IIS 7 の構成は、Web 同期を有効にするために必要な 3 つの手順のうちの最初の手順です。</span><span class="sxs-lookup"><span data-stu-id="158e4-104">Configuring IIS 7 is the first of three steps needed to enable Web synchronization.</span></span>  
  
 <span data-ttu-id="158e4-105">構成プロセス全体の概要については、「[Configure Web Synchronization (Web 同期の構成)](configure-web-synchronization.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="158e4-105">For an overview of the entire configuration process, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="158e4-106">アプリケーションで [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] 以降のバージョンのみが使用されることと、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の以前のバージョンが IIS サーバーにインストールされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-106">Make sure that your application uses only [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] or later versions, and that earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] are not installed on the IIS server.</span></span> <span data-ttu-id="158e4-107">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の以前のバージョンを使用すると、次のようなエラーが発生する可能性があります。"Web 同期中のメッセージの形式が無効でした。</span><span class="sxs-lookup"><span data-stu-id="158e4-107">Earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] can cause errors, such as: "The format of a message during Web synchronization was invalid.</span></span> <span data-ttu-id="158e4-108">Web サーバーでレプリケーション コンポーネントが正しく構成されていることを確認してください。" というエラーなどです。</span><span class="sxs-lookup"><span data-stu-id="158e4-108">Ensure that replication components are properly configured at the Web server."</span></span>  
  
 <span data-ttu-id="158e4-109">Web 同期を使用するには、以下の手順で IIS 7 を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-109">To use Web synchronization, you must configure IIS 7 by completing the following steps.</span></span> <span data-ttu-id="158e4-110">ここでは、各手順を詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="158e4-110">Each step is described in detail in this topic.</span></span>  
  
1.  <span data-ttu-id="158e4-111">IIS を実行しているコンピューターに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーをインストールして構成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-111">Install and configure the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener on the computer that is running IIS.</span></span>  
  
2.  <span data-ttu-id="158e4-112">SSL (Secure Sockets Layer) を構成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-112">Configure Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="158e4-113">IIS とすべてのサブスクライバー間の通信には SSL が必要です。</span><span class="sxs-lookup"><span data-stu-id="158e4-113">SSL is required for communication between IIS and all subscribers.</span></span>  
  
3.  <span data-ttu-id="158e4-114">IIS 認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-114">Configure IIS authentication.</span></span>  
  
4.  <span data-ttu-id="158e4-115">アカウントを構成し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーの権限を設定します。</span><span class="sxs-lookup"><span data-stu-id="158e4-115">Configure an account and set permissions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener.</span></span>  
  
## <a name="installing-the-sql-server-replication-listener"></a><span data-ttu-id="158e4-116">SQL Server レプリケーション リスナーのインストール</span><span class="sxs-lookup"><span data-stu-id="158e4-116">Installing the SQL Server Replication Listener</span></span>  

<span data-ttu-id="158e4-117">Web 同期は、バージョン 5.0 以降の IIS でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="158e4-117">Web synchronization is supported on IIS, beginning with version 5.0.</span></span> <span data-ttu-id="158e4-118">IIS バージョン 5 と 6 の Web 同期の構成ウィザードは、IIS バージョン 7.0 以降では使用できません。</span><span class="sxs-lookup"><span data-stu-id="158e4-118">The Configure Web Synchronization Wizard of IIS version 5 and 6, is not available with IIS version 7.0 and higher.</span></span> <span data-ttu-id="158e4-119">**SQL Server 2012 以降では、IIS サーバーで Web 同期コンポーネントを使用するには、レプリケーションとともに SQL Server をインストールする必要があります。これは無料の SQL Server Express edition で構いません。**</span><span class="sxs-lookup"><span data-stu-id="158e4-119">**Beginning with SQL Server 2012, to use the web sync component on IIS server, you should install SQL Server with replication. This can be the free SQL Server Express edition.**</span></span>
  
#### <a name="to-install-and-configure-the-sql-server-replication-listener"></a><span data-ttu-id="158e4-120">SQL Server レプリケーション リスナーのインストールと構成を行うには</span><span class="sxs-lookup"><span data-stu-id="158e4-120">To install and configure the SQL Server Replication Listener</span></span>  
  
1. <span data-ttu-id="158e4-121">SQL Server レプリケーションを IIS コンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="158e4-121">Install SQL Server replication on the IIS computer.</span></span>

2.  <span data-ttu-id="158e4-122">IIS を実行しているコンピューターに、replisapi.dll 用の新しいファイル ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-122">Create a new file directory for replisapi.dll on the computer that is running IIS.</span></span> <span data-ttu-id="158e4-123">ディレクトリはどこに作成してもかまいませんが、\<*drive*>:\Inetpub ディレクトリの下に作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="158e4-123">You can create the directory wherever you want, but we recommend that you create the directory under the \<*drive*>:\Inetpub directory.</span></span> <span data-ttu-id="158e4-124">たとえば、ディレクトリ \<*drive*>:\Inetpub\SQLReplication\\ を作成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-124">For example, create the directory \<*drive*>:\Inetpub\SQLReplication\\.</span></span>  
  
3.  <span data-ttu-id="158e4-125">replisapi.dll を [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ ディレクトリから、手順 1. で作成したファイル ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="158e4-125">Copy replisapi.dll from the directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ to the file directory that you created in step 1.</span></span>  
  
4.  <span data-ttu-id="158e4-126">次の手順に従って replisapi.dll を登録します。</span><span class="sxs-lookup"><span data-stu-id="158e4-126">Register replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="158e4-127">**[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-127">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="158e4-128">[**名前**] ボックスに「」と入力し、 `cmd` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-128">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="158e4-129">手順 1. で作成したディレクトリで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="158e4-129">In the directory created in step 1, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
5.  <span data-ttu-id="158e4-130">レプリケーション用の新しい Web サイトを作成するか、既存のサイトを使用します。</span><span class="sxs-lookup"><span data-stu-id="158e4-130">Create a new Web site for replication or use an existing site.</span></span> <span data-ttu-id="158e4-131">この Web サイトは、同期の際にレプリケーション コンポーネントからアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="158e4-131">This Web site will be accessed by replication components during synchronization.</span></span> <span data-ttu-id="158e4-132">ここでは、既定の Web サイトを使用すると仮定します。</span><span class="sxs-lookup"><span data-stu-id="158e4-132">Procedures in this topic will assume the Default Web Site.</span></span> <span data-ttu-id="158e4-133">Web サイトを作成する方法の詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="158e4-133">For more information about how to create Web sites, see the IIS documentation</span></span>  
  
6.  <span data-ttu-id="158e4-134">IIS で仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-134">Create a virtual directory in IIS.</span></span> <span data-ttu-id="158e4-135">仮想ディレクトリは、手順 4. で作成した Web サイトの下に作成し、手順 1. で作成したディレクトリにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="158e4-135">The virtual directory should be created under the Web site that you created in step 4 and map it to the directory created in step 1.</span></span> <span data-ttu-id="158e4-136">このディレクトリに割り当てる権限は最小限にしてください。</span><span class="sxs-lookup"><span data-stu-id="158e4-136">Be as restrictive as possible when you assign permissions to this directory.</span></span> <span data-ttu-id="158e4-137">少なくとも **[読み取り]** と **[実行]** の権限を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-137">You must select at least **Read** and **Execute** permissions.</span></span>  
  
    1.  <span data-ttu-id="158e4-138">**インターネット インフォメーション サービス (IIS) マネージャー**の **[接続]** ペインで **[既定の Web サイト]** を右クリックし、 **[仮想ディレクトリの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="158e4-138">In **Internet Information Services (IIS) Manager**, in the **Connections** pane, right-click **Default Web Site**, and then select **Add Virtual Directory**.</span></span>  
  
    2.  <span data-ttu-id="158e4-139">[**エイリアス**] に「」と入力し `SQLReplication` ます。</span><span class="sxs-lookup"><span data-stu-id="158e4-139">For **Alias**, enter `SQLReplication`.</span></span>  
  
    3.  <span data-ttu-id="158e4-140">**[物理パス]** に「 **\<drive>:\Inetpub\SQLReplication\\** 」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-140">For **Physical Path**, enter **\<drive>:\Inetpub\SQLReplication\\**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="158e4-141">replisapi.dll を実行できるように IIS を構成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-141">Configure IIS to enable replisapi.dll to execute.</span></span>  
  
    1.  <span data-ttu-id="158e4-142">**インターネット インフォメーション サービス (IIS) マネージャー**で、 **[既定の Web サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-142">In **Internet Information Services (IIS) Manager**, click **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="158e4-143">中央のペインで、 **[ハンドラー マッピング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-143">In the center pane, click **Handler Mappings**.</span></span>  
  
    3.  <span data-ttu-id="158e4-144">**[アクション]** ペインで、 **[モジュール マップの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-144">In the **Actions** pane, click **Add Module Mapping**.</span></span>  
  
    4.  <span data-ttu-id="158e4-145">[**要求**パス] に「」と入力し `replisapi.dll` ます。</span><span class="sxs-lookup"><span data-stu-id="158e4-145">For **Request** Path, enter `replisapi.dll`.</span></span>  
  
    5.  <span data-ttu-id="158e4-146">**[モジュール]** ボックスの一覧から **[IsapiModule]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="158e4-146">From the **Module** drop-down list, select **IsapiModule**.</span></span>  
  
    6.  <span data-ttu-id="158e4-147">**[実行可能ファイル]** に「 **\<drive>:\Inetpub\SQLReplication\replisapi.dll**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="158e4-147">For **Executable**, enter **\<drive>:\Inetpub\SQLReplication\replisapi.dll**.</span></span>  
  
    7.  <span data-ttu-id="158e4-148">**名前**には、`Replisapi`を入力します。</span><span class="sxs-lookup"><span data-stu-id="158e4-148">For **Name**, enter `Replisapi`.</span></span>  
  
    8.  <span data-ttu-id="158e4-149">**[要求の制限]** をクリックし、 **[アクセス]** タブをクリックして、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-149">Click the **Request Restrictions** button, click the **Access** tab, and then click **Execute**.</span></span>  
  
    9. <span data-ttu-id="158e4-150">**[OK]** をクリックして **[要求の制限]** ダイアログ ボックスを閉じ、もう一度 **[OK]** をクリックして **[モジュール マップの追加]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="158e4-150">Click **OK** to close the **Request Restrictions** dialog box, and then click **OK** again to close the **Add Module Mapping** dialog box.</span></span> <span data-ttu-id="158e4-151">ISAPI 拡張を許可するように求めるメッセージが表示されたら、 **[はい]** をクリックして ISAPI 拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="158e4-151">When you are prompted to allow the ISAPI extension, click **Yes** to add the extension.</span></span>  
  
    10. <span data-ttu-id="158e4-152">Replisapi.dll が **[有効]** のハンドラー マッピングの一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-152">Verify that Replisapi.dll is listed under the **Enabled** handler mappings.</span></span> <span data-ttu-id="158e4-153">**[無効]** の一覧に表示されている場合は、Replisapi のエントリを右クリックし、 **[機能のアクセス許可の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-153">If it is in the **Disabled** list, right-click the Replisapi entry and then click **Edit Feature Permissions**.</span></span> <span data-ttu-id="158e4-154">**[実行]** チェック ボックスをオンにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-154">Check the **Execute** box, and then click **OK**.</span></span>  
  
## <a name="configuring-iis-authentication"></a><span data-ttu-id="158e4-155">IIS 認証の構成</span><span class="sxs-lookup"><span data-stu-id="158e4-155">Configuring IIS Authentication</span></span>  
 <span data-ttu-id="158e4-156">サブスクライバーのコンピューターが IIS に接続するには、サブスクライバーがリソースやプロセスにアクセスする前に、IIS がサブスクライバーを認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-156">When subscriber computers connect to IIS, IIS must authenticate the subscribers before they can access resources and processes.</span></span> <span data-ttu-id="158e4-157">認証は、Web サイト全体または作成した特定の仮想ディレクトリに適用することができます。</span><span class="sxs-lookup"><span data-stu-id="158e4-157">Authentication can be applied to the whole Web site or to the virtual directory that you created.</span></span>  
  
 <span data-ttu-id="158e4-158">基本認証と SSL を組み合わせて使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="158e4-158">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="158e4-159">使用する認証の種類にかかわらず、SSL は必須です。</span><span class="sxs-lookup"><span data-stu-id="158e4-159">SSL is required, regardless of the type of authentication that is used.</span></span>  
  
 <span data-ttu-id="158e4-160">基本認証と SSL を組み合わせて使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="158e4-160">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="158e4-161">使用する認証の種類にかかわらず、SSL は必須です。</span><span class="sxs-lookup"><span data-stu-id="158e4-161">SSL is required, regardless of the type of authentication that is used.</span></span>  
  
#### <a name="to-configure-iis-authentication"></a><span data-ttu-id="158e4-162">IIS 認証を構成するには</span><span class="sxs-lookup"><span data-stu-id="158e4-162">To Configure IIS Authentication</span></span>  
  
1.  <span data-ttu-id="158e4-163">**インターネット インフォメーション サービス (IIS) マネージャー**で、 **[既定の Web サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-163">In **Internet Information Services (IIS) Manager**, click **Default Web Site**.</span></span>  
  
2.  <span data-ttu-id="158e4-164">中央のペインで、 **[認証]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-164">In the middle pane, double-click **Authentication**.</span></span>  
  
3.  <span data-ttu-id="158e4-165">[匿名認証] を右クリックし、[無効にする] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-165">Right-click Anonymous Authentication, and then choose Disable.</span></span>  
  
4.  <span data-ttu-id="158e4-166">[基本認証] を右クリックし、[有効にする] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-166">Right-click Basic Authentication, and then choose Enable.</span></span>  
  
## <a name="configuring-secure-sockets-layer"></a><span data-ttu-id="158e4-167">Secure Sockets Layer の構成</span><span class="sxs-lookup"><span data-stu-id="158e4-167">Configuring Secure Sockets Layer</span></span>  
 <span data-ttu-id="158e4-168">SSL を構成するには、IIS を実行しているコンピューターが使用する証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-168">To configure SSL, specify a certificate to be used by the computer running IIS.</span></span> <span data-ttu-id="158e4-169">マージ レプリケーション用の Web 同期では、サーバー証明書のみがサポートされており、クライアント証明書はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="158e4-169">Web synchronization for merge replication supports using server certificates, but not client certificates.</span></span> <span data-ttu-id="158e4-170">配置用に IIS を構成するには、最初に証明機関 (CA) から証明書を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-170">To configure IIS for deployment, you must first obtain a certificate from a certification authority (CA).</span></span> <span data-ttu-id="158e4-171">証明書の詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="158e4-171">For more information about certificates, see the IIS documentation.</span></span>  
  
 <span data-ttu-id="158e4-172">証明書をインストールしたら、その証明書を Web 同期で使用する Web サイトと関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-172">After you install the certificate, you must associate the certificate with the Web site that is used by Web synchronization.</span></span> <span data-ttu-id="158e4-173">開発やテストでは、自己署名証明書を指定できます。</span><span class="sxs-lookup"><span data-stu-id="158e4-173">For development and testing, you can specify a self-signed certificate.</span></span> <span data-ttu-id="158e4-174">この場合、IIS 7 で証明書を作成してコンピューターに登録できます。</span><span class="sxs-lookup"><span data-stu-id="158e4-174">IIS 7 can create a certificate for you and register it on your computer.</span></span>  
  
 <span data-ttu-id="158e4-175">ここで紹介する手順と運用環境に配置する場合の手順との違いは、運用環境や運用前テストの環境では、自己署名証明書ではなく、CA によって発行された証明書を使用することです。</span><span class="sxs-lookup"><span data-stu-id="158e4-175">The difference between deploying for production and the procedures given here is that in production and pre-production testing, you would use a certificate issued by a CA instead of a self-signed certificate.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="158e4-176">運用環境で自己署名証明書を使用することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="158e4-176">A self-signed certificate is not recommended for a production installation.</span></span> <span data-ttu-id="158e4-177">自己署名証明書は安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="158e4-177">Self-signed certificates are not secure.</span></span> <span data-ttu-id="158e4-178">自己署名証明書を使用するのは、開発およびテストのときだけにしてください。</span><span class="sxs-lookup"><span data-stu-id="158e4-178">Use self-signed certificates for development and testing only.</span></span>  
  
 <span data-ttu-id="158e4-179">SSL を構成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="158e4-179">To configure SSL, you will perform the following steps:</span></span>  
  
1.  <span data-ttu-id="158e4-180">SSL を要求し、クライアント証明書を無視するように Web サイトを構成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-180">Configure the Web site to require SSL and ignore client certificates.</span></span>  
  
2.  <span data-ttu-id="158e4-181">CA から証明書を取得するか、自己署名証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-181">Obtain a certificate from a CA or create a self-signed certificate.</span></span>  
  
3.  <span data-ttu-id="158e4-182">証明書をレプリケーション Web サイトにバインドします。</span><span class="sxs-lookup"><span data-stu-id="158e4-182">Bind the certificate to the replication Web site.</span></span>  
  
#### <a name="to-require-ssl-security-for-a-web-site"></a><span data-ttu-id="158e4-183">Web サイトの SSL セキュリティを要求するには</span><span class="sxs-lookup"><span data-stu-id="158e4-183">To require SSL security for a Web site</span></span>  
  
1.  <span data-ttu-id="158e4-184">**インターネット インフォメーション サービス (IIS) マネージャー**でローカル サーバーのノードを展開し、 **[既定の Web サイト]** (Web 同期サイトが既定の Web サイトと異なる場合は Web 同期サイト) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-184">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click the **Default Web Site** (or your Web synchronization site if it is different from the default Web site).</span></span>  
  
2.  <span data-ttu-id="158e4-185">中央のペインで、 **[SSL 設定]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-185">In the middle pane, double-click **SSL Settings**.</span></span>  
  
3.  <span data-ttu-id="158e4-186">**[SSL が必要]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="158e4-186">Check the **Require SSL** option.</span></span> <span data-ttu-id="158e4-187">**[クライアント証明書]** で、 **[無視]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-187">Under **Client certificates**, verify that the **Ignore** button is selected.</span></span>  
  
#### <a name="to-create-a-self-signed-certificate-for-testing"></a><span data-ttu-id="158e4-188">テスト用の自己署名証明書を作成するには</span><span class="sxs-lookup"><span data-stu-id="158e4-188">To create a self-signed certificate for testing</span></span>  
  
1.  <span data-ttu-id="158e4-189">**インターネット インフォメーション サービス (IIS) マネージャー**でローカル サーバーのノードをクリックし、中央のペインで **[サーバー証明書]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-189">In **Internet Information Services (IIS) Manager**, click the local server node, and then in the center pane, double-click on **Server Certificates**.</span></span>  
  
2.  <span data-ttu-id="158e4-190">**[アクション]** ペインで、 **[自己署名証明書の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-190">In the **Actions** pane, click **Create Self-Signed Certificate**.</span></span>  
  
3.  <span data-ttu-id="158e4-191">**[自己署名証明書の作成]** ダイアログ ボックスで、証明書の名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-191">In the **Create Self-Signed Certificate** dialog box, enter a name for the certificate, and then click **OK**.</span></span>  
  
###### <a name="to-bind-a-certificate-to-a-web-site"></a><span data-ttu-id="158e4-192">証明書を Web サイトにバインドするには</span><span class="sxs-lookup"><span data-stu-id="158e4-192">To bind a certificate to a Web site</span></span>  
  
1.  <span data-ttu-id="158e4-193">**[接続]** ペインで、 **[既定の Web サイト]** (Web 同期サイトが既定の Web サイトと異なる場合は Web 同期サイト) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-193">In the **Connections** pane, click the **Default Web Site** (or your Web synchronization site, if it is different from the default Web site).</span></span>  
  
2.  <span data-ttu-id="158e4-194">**[アクション]** ペインで **[バインド]** をクリックし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-194">In the **Actions** pane, click **Bindings**, and then click **Add**.</span></span> <span data-ttu-id="158e4-195">**[サイト バインドの追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="158e4-195">The **Add Site Binding** dialog box will appear.</span></span>  
  
3.  <span data-ttu-id="158e4-196">**[種類]** ボックスの一覧で、 **[https]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="158e4-196">From the **Type** drop-down list, select **https**.</span></span> <span data-ttu-id="158e4-197">**[IP アドレス]** と **[ポート]** は既定の設定のままにします。</span><span class="sxs-lookup"><span data-stu-id="158e4-197">Leave the default settings for **IP address** and **Port**.</span></span>  
  
4.  <span data-ttu-id="158e4-198">**[SSL 証明書]** ボックスの一覧で、「テスト用の自己署名証明書を作成するには」で作成した証明書を選択し、 **[OK]** をクリックし、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-198">From the **SSL certificate** drop-down list, select the certificate created in "To create a self-signed certificate for testing," click **OK**, and then click **Close**.</span></span>  
  
###### <a name="to-test-the-certificate"></a><span data-ttu-id="158e4-199">証明書をテストするには</span><span class="sxs-lookup"><span data-stu-id="158e4-199">To test the certificate</span></span>  
  
1.  <span data-ttu-id="158e4-200">**ternet formation Services (IIS) Manager**で、 **[既定の Web サイト].**</span><span class="sxs-lookup"><span data-stu-id="158e4-200">In **Internet Information Services (IIS) Manager**, click **Default Web Site.**</span></span>  
  
2.  <span data-ttu-id="158e4-201">**[アクション]** ペインで、 **[Browse \*:443(https)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-201">From the **Actions** pane, click **Browse \*:443(https)**.</span></span>  
  
3.  <span data-ttu-id="158e4-202">Internet Explorer が開き、"この Web サイトのセキュリティ証明書には問題があります" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="158e4-202">Internet Explorer will open and display a message that "There is a problem with this website's security certificate."</span></span> <span data-ttu-id="158e4-203">これは、関連付けられている証明書が既知の CA によって発行された証明書ではないために信頼できないことを通知する警告です。</span><span class="sxs-lookup"><span data-stu-id="158e4-203">This warning tells you that the associated certificate was not issued by a recognized CA and might not be trustworthy.</span></span> <span data-ttu-id="158e4-204">これは予期されたとおりの警告なので、 **[このサイトの閲覧を続行する (推奨されません)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-204">This is an expected warning, so click **Continue to this website (not recommended)**.</span></span>  
  
4.  <span data-ttu-id="158e4-205">**[localhost に接続]** ダイアログ ボックスが表示された場合は、ユーザー名とパスワードを入力して続行します。</span><span class="sxs-lookup"><span data-stu-id="158e4-205">If you are prompted to **Connect to localhost**, enter a user name and password to proceed.</span></span> <span data-ttu-id="158e4-206">これで、Web サイトの既定のページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="158e4-206">You should see the default page for the Web site.</span></span>  
  
## <a name="setting-permissions-for-the-sql-server-replication-listener"></a><span data-ttu-id="158e4-207">SQL Server レプリケーション リスナーの権限の設定</span><span class="sxs-lookup"><span data-stu-id="158e4-207">Setting Permissions for the SQL Server Replication Listener</span></span>  
 <span data-ttu-id="158e4-208">サブスクライバーのコンピューターが IIS を実行しているコンピューターに接続するときは、IIS の構成時に指定した認証の種類を使用して、サブスクライバーが認証されます。</span><span class="sxs-lookup"><span data-stu-id="158e4-208">When a subscriber computer connects to the computer running IIS, the subscriber is authenticated by using the type of authentication specified when you configured IIS.</span></span> <span data-ttu-id="158e4-209">IIS はサブスクライバーを認証した後、サブスクライバーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションを実行する権限があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-209">After IIS authenticates the subscriber, IIS checks whether the subscriber is authorized to invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="158e4-210">replisapi.dll の権限を設定して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションを実行できるユーザーを制御します。</span><span class="sxs-lookup"><span data-stu-id="158e4-210">You control the users that can invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication by setting permissions for replisapi.dll.</span></span> <span data-ttu-id="158e4-211">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションに許可なくアクセスされることがないように権限を正しく構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-211">Properly configuring permissions is necessary to prevent unauthorized access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
 <span data-ttu-id="158e4-212">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーの実行に使用するアカウントを最小の権限で構成するには、次の手順を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-212">To configure the minimum permissions for the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener runs, complete the following procedure.</span></span> <span data-ttu-id="158e4-213">以下の手順は、IIS 7.0 を実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008 に適用されます。</span><span class="sxs-lookup"><span data-stu-id="158e4-213">The steps in the following procedure apply to [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008 running IIS 7.0.</span></span>  
  
 <span data-ttu-id="158e4-214">次の手順の他に、PAL (パブリケーション アクセス リスト) に必要なログインが登録されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="158e4-214">In addition to performing the following steps, make sure that the required logins are in the publication access list (PAL).</span></span> <span data-ttu-id="158e4-215">PAL の詳細については、「[Secure the Publisher (パブリッシャーのセキュリティ保護)](security/secure-the-publisher.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="158e4-215">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
 <span data-ttu-id="158e4-216">**重要** ここで作成するアカウントは、同期の際にパブリッシャーとディストリビューターに接続するアカウントです。</span><span class="sxs-lookup"><span data-stu-id="158e4-216">**Important** The account created in this section is the account that will connect to the Publisher and Distributor during synchronization.</span></span> <span data-ttu-id="158e4-217">したがって、ディストリビューション サーバーとパブリケーション サーバーに SQL ログイン アカウントとして追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-217">This account must be added as a SQL Login account on the distribution and publication server.</span></span>  
  
 <span data-ttu-id="158e4-218">SQL Server レプリケーション リスナーに使用するアカウントには、「マージ エージェント セキュリティ」の「パブリッシャーまたはディストリビューターへの接続」で説明されている権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="158e4-218">The account used for the SQL Server Replication Listener must have permissions as described in the Merge Agent Security topic, in the "Connect to the Publisher or Distributor" section.</span></span>  
  
 <span data-ttu-id="158e4-219">このアカウントに必要な権限の概要を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="158e4-219">In summary, the account must:</span></span>  
  
-   <span data-ttu-id="158e4-220">パブリケーション アクセス リスト (PAL) のメンバーである。</span><span class="sxs-lookup"><span data-stu-id="158e4-220">Be a member of the Publication Access List (PAL).</span></span>  
  
-   <span data-ttu-id="158e4-221">パブリケーション データベースのユーザーに関連付けられたログインにマップされている。</span><span class="sxs-lookup"><span data-stu-id="158e4-221">Be mapped to a login associated with a user in the publication database.</span></span>  
  
-   <span data-ttu-id="158e4-222">ディストリビューション データベース内のユーザーに関連付けられているログインにマップされている。</span><span class="sxs-lookup"><span data-stu-id="158e4-222">Be mapped to a login associated with a user in the distribution database.</span></span>  
  
-   <span data-ttu-id="158e4-223">スナップショット共有の読み取り権限を持つ。</span><span class="sxs-lookup"><span data-stu-id="158e4-223">Have Read permissions on the snapshot share.</span></span>  
  
#### <a name="to-configure-the-account-and-permissions"></a><span data-ttu-id="158e4-224">アカウントと権限を構成するには</span><span class="sxs-lookup"><span data-stu-id="158e4-224">To configure the account and permissions</span></span>  
  
1.  <span data-ttu-id="158e4-225">IIS を実行しているコンピューターでローカル アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-225">Create a local account on the computer running IIS:</span></span>  
  
    1.  <span data-ttu-id="158e4-226">**サーバー マネージャー**を開きます。</span><span class="sxs-lookup"><span data-stu-id="158e4-226">Open **Server Manager**.</span></span> <span data-ttu-id="158e4-227">[スタート] ボタンをクリックし、 **[マイ コンピューター]** を右クリックして、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-227">From the Start menu, right-click **Computer**, and then click **Manage**.</span></span>  
  
    2.  <span data-ttu-id="158e4-228">**サーバー マネージャー**で、 **[構成]** を展開し、 **[ローカル ユーザーとグループ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="158e4-228">In **Server Manager**, expand **Configuration**, and then expand **Local Users and Groups**.</span></span>  
  
    3.  <span data-ttu-id="158e4-229">**[ユーザー]** を右クリックし、 **[新しいユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-229">Right-click **Users**, and then click **New User**.</span></span>  
  
    4.  <span data-ttu-id="158e4-230">ユーザー名と複雑なパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="158e4-230">Enter a user name and a strong password.</span></span> <span data-ttu-id="158e4-231">**[ユーザーは次回ログオン時にパスワードの変更が必要]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="158e4-231">Clear **User must change password at next logon**.</span></span>  
  
    5.  <span data-ttu-id="158e4-232">**[作成]** をクリックしてから、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-232">Click **Create**, and then click **Close**.</span></span>  
  
2.  <span data-ttu-id="158e4-233">アカウントを IIS_IUSRS グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="158e4-233">Add the account to the IIS_IUSRS group:</span></span>  
  
    1.  <span data-ttu-id="158e4-234">**サーバー マネージャー**で、 **[構成]** 、 **[ローカル ユーザーとグループ]** の順に展開し、 **[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-234">In **Server Manager**, expand **Configuration**, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
    2.  <span data-ttu-id="158e4-235">**[IIS_IUSRS]** を右クリックし、 **[グループに追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-235">Right-click **IIS_IUSRS**, and then click **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="158e4-236">**[IIS_IUSRS のプロパティ]** ダイアログ ボックスで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-236">In the **IIS_IUSRS Properties** dialog box, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="158e4-237">**[ユーザー、コンピューター、またはグループの選択]** ダイアログ ボックスで、手順 1. で作成したアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="158e4-237">In the **Select Users, Computers, or Groups** dialog box, add the account created in step 1.</span></span>  
  
    5.  <span data-ttu-id="158e4-238">**[場所を指定してください]** フィールドに、ドメインではなくローカル コンピューターの名前が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-238">Verify that **From this location** displays the name of the local computer (not a domain).</span></span> <span data-ttu-id="158e4-239">ローカル コンピューターの名前が表示されていない場合は、 **[場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-239">If this field does not display the local computer name, click **Locations**.</span></span> <span data-ttu-id="158e4-240">**[場所]** ダイアログ ボックスで、ローカル コンピューターを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-240">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="158e4-241">**[ユーザーの選択]** ダイアログ ボックスと **[IIS_IUSRS のプロパティ]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-241">In the **Select Users** dialog box and the **IIS_IUSRS Properties** dialog box, click**OK**.</span></span>  
  
3.  <span data-ttu-id="158e4-242">replisapi.dll が保存されているフォルダーに対する最小限の権限をアカウントに許可します。</span><span class="sxs-lookup"><span data-stu-id="158e4-242">Grant minimum account permissions on the folder that contains replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="158e4-243">Windows エクスプローラーで、replisapi.dll のために作成したフォルダーを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-243">In Windows Explorer, right-click the folder that you created for replisapi.dll, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="158e4-244">**[セキュリティ]** タブで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-244">On the **Security** tab, click **Edit**.</span></span>  
  
    3.  <span data-ttu-id="158e4-245">**[\<foldername> のアクセス許可]** ダイアログ ボックスで **[追加]** をクリックして、手順 1 で作成したアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="158e4-245">In the **Permissions for \<foldername>** dialog box, click **Add** to add the account that you created in step 1.</span></span>  
  
    4.  <span data-ttu-id="158e4-246">**[場所を指定してください]** フィールドに、ドメインではなくローカル コンピューターの名前が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-246">Verify that **From this location** displays the name of the local computer (not a domain).</span></span> <span data-ttu-id="158e4-247">ローカル コンピューターの名前が表示されていない場合は、 **[場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-247">If this field does not display the local computer name, click **Locations**.</span></span> <span data-ttu-id="158e4-248">**[場所]** ダイアログ ボックスで、ローカル コンピューターを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-248">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="158e4-249">アカウントには、 **[読み取り]** 、 **[読み取りと実行]** 、 **[フォルダーの内容の一覧表示]** のみが許可されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-249">Verify that the account is granted only **Read**, **Read & Execute**, and **List Folder Contents** permissions.</span></span>  
  
    6.  <span data-ttu-id="158e4-250">ディレクトリにアクセスする必要がないユーザーまたはグループを選択し、 **[削除]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-250">Select any users or groups that do not require access to the directory, click **Remove**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="158e4-251">**インターネット インフォメーション サービス (IIS) マネージャー**でアプリケーション プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="158e4-251">Create an application pool in **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="158e4-252">**インターネット インフォメーション サービス (IIS) マネージャー**の **[接続]** ペインで、ローカル サーバーのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="158e4-252">In **Internet Information Services (IIS) Manager**, in the **Connections** pane, expand the local server node.</span></span>  
  
    2.  <span data-ttu-id="158e4-253">**[アプリケーション プール]** を右クリックし、 **[アプリケーション プールの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-253">Right-click **Application Pools**, and then click **Add Application Pool**.</span></span>  
  
    3.  <span data-ttu-id="158e4-254">アプリケーション プールの名前を入力し、その他のフィールドは既定値のままにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-254">Enter a name for the application pool, leave the default values for the remaining fields, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="158e4-255">3 つ以上の同期クライアントが同時に実行される可能性がある場合は、Web ガーデンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="158e4-255">If you anticipate having more than two concurrent synchronization clients, you might want to create a web garden.</span></span> <span data-ttu-id="158e4-256">詳しくは、「[Configure Web Synchronization (Web 同期の構成)](configure-web-synchronization.md)」の「Creating a Web Garden (Web ガーデンの作成)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="158e4-256">For more information, see "Creating a Web Garden" in [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
5.  <span data-ttu-id="158e4-257">アカウントとアプリケーション プールを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="158e4-257">Associate the account with the application pool:</span></span>  
  
    1.  <span data-ttu-id="158e4-258">**インターネット インフォメーション サービス (IIS) マネージャー**で、ローカル サーバーのノードを展開し、 **[アプリケーション プール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-258">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click on **Application Pools**.</span></span>  
  
    2.  <span data-ttu-id="158e4-259">作成したアプリケーション プールを右クリックして、 **[アプリケーション プールの既定値の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-259">Right-click the application pool that you created, and then click **Set Application Pool Defaults**.</span></span>  
  
    3.  <span data-ttu-id="158e4-260">**[アプリケーション プールの既定値]** ダイアログ ボックスで、 **[プロセス モデル]** セクションが表示されるまでスクロールして、 **[ID]** フィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-260">In the **Application Pool Defaults** dialog box, scroll down to the **Process Model** section, and then click the **Identity** field.</span></span>  
  
    4.  <span data-ttu-id="158e4-261">**[ID]** 行の右側にある参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-261">Click the ellipsis button on the right side of the **Identity** row.</span></span>  
  
    5.  <span data-ttu-id="158e4-262">**[カスタム アカウント]** オプションをクリックし、 **[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-262">Click the **Custom Account** radio button, and then click **Set**.</span></span>  
  
    6.  <span data-ttu-id="158e4-263">**[ユーザー名]** および **[パスワード]** フィールドに、手順 1. で作成したアカウントとパスワードを入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-263">In the **User name** and **Password** fields, enter the account and password that were created in step 1, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="158e4-264">**[OK]** をクリックして **[アプリケーション プール ID]** ダイアログ ボックスを閉じ、もう一度 **[OK]** をクリックして **[アプリケーション プールの既定値]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="158e4-264">Click **OK** to close the **Application Pool Identity** dialog box, and then click **OK** again to close the **Application Pool Defaults**dialog box.</span></span>  
  
6.  <span data-ttu-id="158e4-265">アプリケーション プールとレプリケーション Web サイトを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="158e4-265">Associate the application pool with the replication Web site:</span></span>  
  
    1.  <span data-ttu-id="158e4-266">**インターネット インフォメーション サービス (IIS) マネージャー**でローカル サーバーのノードを展開し、 **[既定の Web サイト]** (Web 同期サイトが既定の Web サイトと異なる場合は Web 同期サイト) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-266">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click on the **Default Web Site** (or your Web synchronization site if it is different from the default Web site).</span></span>  
  
    2.  <span data-ttu-id="158e4-267">**[アクション]** ペインの **[Web サイトの管理]** で、 **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-267">In the **Actions** pane, under **Manage Web Site**, click **Advanced Settings**.</span></span>  
  
    3.  <span data-ttu-id="158e4-268">**[詳細設定]** ダイアログ ボックスで、 **[アプリケーション プール]** の右側にある参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-268">In the **Advanced Settings** dialog box, click on the ellipsis button to the right of **Application Pool**.</span></span>  
  
    4.  <span data-ttu-id="158e4-269">**[アプリケーション プール]** ボックスの一覧で、手順 4. で作成したアプリケーション プールを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-269">From the **Application pool** drop-down list, select the application pool you created in step 4, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="158e4-270">もう一度 **[OK]** をクリックして [詳細設定] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="158e4-270">Click **OK** again to close Advanced Settings.</span></span>  
  
## <a name="testing-the-connection-to-replisapidll"></a><span data-ttu-id="158e4-271">replisapi.dll への接続のテスト</span><span class="sxs-lookup"><span data-stu-id="158e4-271">Testing the Connection to replisapi.dll</span></span>  
 <span data-ttu-id="158e4-272">診断モードで Web 同期を実行すると、IIS を実行しているコンピューターへの接続をテストして、SSL (Secure Sockets Layer) 証明書が正しくインストールされているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="158e4-272">Run Web synchronization in diagnostic mode to test the connection to the computer running IIS and to make sure that the Secure Sockets Layer (SSL) certificate is properly installed.</span></span> <span data-ttu-id="158e4-273">診断モードで Web 同期を実行するには、IIS を実行しているコンピューターの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-273">To run Web synchronization in diagnostic mode, you must be an administrator on the computer running IIS.</span></span>  
  
#### <a name="to-test-the-connection-to-replisapidll"></a><span data-ttu-id="158e4-274">replisapi.dll への接続をテストするには</span><span class="sxs-lookup"><span data-stu-id="158e4-274">To test the connection to replisapi.dll</span></span>  
  
1.  <span data-ttu-id="158e4-275">サブスクライバーの LAN (ローカル エリア ネットワーク) が正しく設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-275">Make sure that local area network (LAN) settings at the Subscriber are correct:</span></span>  
  
    1.  <span data-ttu-id="158e4-276">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer で、 **[ツール]** メニューの **[インターネット オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-276">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="158e4-277">**[接続]** タブで、 **[LAN の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-277">On the **Connections** tab, click **LAN Settings**.</span></span>  
  
    3.  <span data-ttu-id="158e4-278">LAN でプロキシ サーバーを使用していない場合は、 **[設定を自動的に検出する]** と **[LAN にプロキシ サーバーを使用する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="158e4-278">If a proxy server is not used on the LAN, clear **Automatically Detect Settings** and **Use a proxy server for your LAN**.</span></span>  
  
    4.  <span data-ttu-id="158e4-279">プロキシ サーバーを使用している場合は、 **[LAN にプロキシ サーバーを使用する]** と **[ローカル アドレスにはプロキシ サーバーを使用しない]** チェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-279">If a proxy server is used, click **Use a proxy server for your LAN** and **Bypass proxy server for local addresses**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="158e4-280">サブスクライバー側の Internet Explorer から診断モードでサーバーに接続します。診断モードで接続するには、replisapi.dll のアドレスの後に「 `?diag` 」を追加します。</span><span class="sxs-lookup"><span data-stu-id="158e4-280">At the Subscriber, in Internet Explorer, connect to the server in diagnostic mode by appending `?diag` to the address for the replisapi.dll.</span></span> <span data-ttu-id="158e4-281">(例: `https://server.domain.com/directory/replisapi.dll?diag`)。</span><span class="sxs-lookup"><span data-stu-id="158e4-281">For example: `https://server.domain.com/directory/replisapi.dll?diag`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="158e4-282">上の例の **server.domain.com** は、IIS マネージャーの **[サーバー証明書]** セクションに表示される **[発行先]** の正確な名前に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-282">In the example above, **server.domain.com** should be replaced with the exact **Issued To** name listed under the **Server Certificates** section in IIS Manager.</span></span>  
  
3.  <span data-ttu-id="158e4-283">IIS に指定した証明書が Windows オペレーティング システムによって認識されない場合は、 **[セキュリティの警告]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="158e4-283">If the certificate that you specified for IIS is not recognized by the Windows operating system, the **Security Alert** dialog box appears.</span></span> <span data-ttu-id="158e4-284">証明書がテスト用の証明書であるか、Windows が認識しない証明機関 (CA) によって発行されていると、この警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="158e4-284">This alert might occur because the certificate is a test certificate or the certificate was issued by a certification authority (CA) that Windows does not recognize.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="158e4-285">このダイアログ ボックスが表示されない場合は、アクセスしているサーバーの証明書が信頼された証明書としてサブスクライバーの証明書ストアに追加されていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="158e4-285">If this dialog box does not appear, make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="158e4-286">証明書のエクスポートの詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="158e4-286">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
    1.  <span data-ttu-id="158e4-287">**[セキュリティの警告]** ダイアログ ボックスで、 **[証明書の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-287">In the **Security Alert** dialog box, click **View Certificate**.</span></span>  
  
    2.  <span data-ttu-id="158e4-288">**[証明書]** ダイアログ ボックスの **[全般]** タブで、 **[証明書のインストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-288">In the **Certificate** dialog box, on the **General** tab, click **Install Certificate**.</span></span>  
  
    3.  <span data-ttu-id="158e4-289">証明書インポート ウィザードを実行します。このウィザードでは既定の値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="158e4-289">Complete the Certificate Import Wizard, accepting the defaults.</span></span>  
  
    4.  <span data-ttu-id="158e4-290">**[セキュリティの警告]** ダイアログ ボックスで、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-290">In the **Security Warning** dialog box, click **Yes**.</span></span>  
  
    5.  <span data-ttu-id="158e4-291">証明書のインポート ウィザードの確認ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-291">In the Certificate Import Wizard confirmation dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="158e4-292">**[証明書]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="158e4-292">Close the **Certificate** dialog box.</span></span>  
  
    7.  <span data-ttu-id="158e4-293">**[セキュリティの警告]** ダイアログ ボックスで、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="158e4-293">In the **Security Alert** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="158e4-294">ユーザーの証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="158e4-294">Certificates are installed for users.</span></span> <span data-ttu-id="158e4-295">IIS と同期するユーザーすべてに対してこの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-295">This process must be performed for each user that will synchronize with IIS.</span></span>  
  
4.  <span data-ttu-id="158e4-296">**[\<ServerName> に接続]** ダイアログ ボックスで、マージ エージェントが IIS サーバーへの接続に使用するログインとパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="158e4-296">In the **Connect to \<ServerName>** dialog box, specify the login and password that the Merge Agent will use to connect to IIS.</span></span> <span data-ttu-id="158e4-297">これらの資格情報は、サブスクリプションの新規作成ウィザードで指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="158e4-297">These credentials will also be specified in the New Subscription Wizard.</span></span>  
  
5.  <span data-ttu-id="158e4-298">**[SQL Web 同期診断情報]** と呼ばれる Internet Explorer のウィンドウで、ページの **[Status]** 列の値が **[SUCCESS]** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-298">In the Internet Explorer window called **SQL Websync diagnostic information**, verify that the value in each **Status** column on the page is **SUCCESS**.</span></span>  
  
6.  <span data-ttu-id="158e4-299">証明書がサブスクライバーに正しくインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="158e4-299">Make sure that the certificate is installed correctly on the Subscriber:</span></span>  
  
    1.  <span data-ttu-id="158e4-300">Internet Explorer をいったん閉じてから、再度開きます。</span><span class="sxs-lookup"><span data-stu-id="158e4-300">Close and then reopen Internet Explorer.</span></span>  
  
    2.  <span data-ttu-id="158e4-301">サーバーに診断モードで接続します。</span><span class="sxs-lookup"><span data-stu-id="158e4-301">Connect to the server in diagnostic mode.</span></span> <span data-ttu-id="158e4-302">証明書が正しくインストールされている場合は、 **[セキュリティの警告]** ダイアログ ボックスが表示されません。</span><span class="sxs-lookup"><span data-stu-id="158e4-302">If the certificate is installed properly, the **Security Alert** dialog box will not appear.</span></span> <span data-ttu-id="158e4-303">ダイアログ ボックスが表示される場合は、マージ エージェントから IIS を実行しているコンピューターへの接続に失敗します。</span><span class="sxs-lookup"><span data-stu-id="158e4-303">If the dialog box appears, the Merge Agent will fail when it tries to connect to the computer that is running IIS.</span></span> <span data-ttu-id="158e4-304">アクセスしているサーバーの証明書が、信頼された証明書としてサブスクライバーの証明書ストアに追加されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="158e4-304">You must make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="158e4-305">証明書のエクスポートの詳細については、IIS のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="158e4-305">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158e4-306">参照</span><span class="sxs-lookup"><span data-stu-id="158e4-306">See Also</span></span>  
 <span data-ttu-id="158e4-307">[マージ レプリケーションの Web 同期](web-synchronization-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="158e4-307">[Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md) </span></span>  
 <span data-ttu-id="158e4-308">[[Web 同期の構成]](configure-web-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="158e4-308">[Configure Web Synchronization](configure-web-synchronization.md)</span></span>  
  
  
